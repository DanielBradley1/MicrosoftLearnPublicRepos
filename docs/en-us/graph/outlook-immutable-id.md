<!-- Source: https://learn.microsoft.com/en-us/graph/outlook-immutable-id -->
<!-- Sitemap-Last-Modified: 2024-11-07 -->

# Obtain immutable identifiers for Outlook resources

Outlook items \(messages, events, contacts, tasks\) have an interesting behavior that you've probably either never noticed or has caused you significant frustration: their IDs change. It doesn't happen often, only if the item is moved, but it can cause real problems for apps that store IDs offline for later use. Immutable identifiers \(IDs\) enable your application to obtain an ID that doesn't change for the lifetime of the item.

Note

Immutable identifiers, like all identifiers in Microsoft Graph, are case-sensitive. Keep this in mind if you are comparing IDs.

## How it works

Immutable ID is an optional feature for Microsoft Graph. To opt in, your application needs to send an additional HTTP header in your API requests:

```http
Prefer: IdType="ImmutableId"
```

This header only applies to the request it is included with. If you want to always use immutable IDs, you must include this header with every API request.

## Lifetime of immutable IDs

An item's immutable ID won't change so long as the item stays in the same mailbox. That means that immutable ID will NOT change if the item is moved to a different folder in the mailbox. However, the immutable ID changes if:

- The user moves the item to an archive mailbox.
- The user exports the item \(to a PST, as an MSG file, etc.\) and re-imports it into their mailbox.

## Items that support immutable IDs

The following items support immutable IDs:

- [message resource type](https://learn.microsoft.com/en-us/graph/api/resources/message)
- [attachment resource type](https://learn.microsoft.com/en-us/graph/api/resources/attachment)
- [event resource type](https://learn.microsoft.com/en-us/graph/api/resources/event)
- [eventMessage resource type](https://learn.microsoft.com/en-us/graph/api/resources/eventmessage)
- [contact resource type](https://learn.microsoft.com/en-us/graph/api/resources/contact)
- [outlookTask resource type](https://learn.microsoft.com/en-us/graph/api/resources/outlooktask)

Container types \(mailFolder, calendar, etc.\) don't support immutable ID, but their regular IDs were already constant.

## Immutable ID with sending mail

You can use immutable IDs to find a message in the Sent Items folder after it has been sent, using the following steps:

1. [Create a draft message](https://learn.microsoft.com/en-us/graph/api/user-post-messages) using the `Prefer: IdType="ImmutableId"` header and save the `id` property of the message in the response.
2. [Send the message](https://learn.microsoft.com/en-us/graph/api/message-send) using the ID from the previous step.
3. [Get the message](https://learn.microsoft.com/en-us/graph/api/message-get) using the ID from the first step. This is the copy in Sent Items.

Note

Getting the message in Sent Items might not succeed immediately after sending the message. The copy of the message is not created until the message successfully sends, which might take time.

## Immutable ID with change notifications

You can request that Microsoft Graph send immutable IDs in change notifications by including the `Prefer: IdType="ImmutableId"` header when [creating a subscription](https://learn.microsoft.com/en-us/graph/api/subscription-post-subscriptions). Existing subscriptions created without the header continues to use the default ID format. In order to switch existing subscriptions to use immutable IDs, you must delete and recreate them using the header.

## Immutable ID with delta query

You can request that Microsoft Graph return immutable IDs in [delta query responses](https://learn.microsoft.com/en-us/graph/delta-query-overview) for supported resource types by including the `Prefer: IdType="ImmutableId"` header. The `@odata.nextLink` and `@odata.deltaLink` values returned by delta queries are compatible with both ID formats, so your application doesn't need to re-synchronize to take advantage of immutable ID. You can use the header to get immutable IDs going forward, and you can [update your app's storage](#updating-existing-data) separately.

## Updating existing data

If you've already got a database filled with thousands of regular IDs, you can migrate those IDs to immutable format using the [translateExchangeIds](https://learn.microsoft.com/en-us/graph/api/user-translateexchangeids) function. You can provide an array of up to 1000 IDs to be translated into a target format.

Note

You can also use `translateExchangeIds` to migrate Exchange Web Services applications to Microsoft Graph.

### Example

The following example translates a normal Microsoft Graph ID to an immutable Microsoft Graph ID.

#### Request

```http
POST https://graph.microsoft.com/v1.0/me/translateExchangeIds

{
  "inputIds" :
  [
    "AQMkAGM2…"
  ],
  "targetIdType" : "restImmutableEntryId",
  "sourceIdType" : "restId"
}
```

#### Response

```http
HTTP 200 OK

{
  "value": [
    {
      "targetId": "AAkALgAA...",
      "sourceId": "AQMkAGM2..."
    }
  ]
}
```
