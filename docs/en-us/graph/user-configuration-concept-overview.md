<!-- Source: https://learn.microsoft.com/en-us/graph/user-configuration-concept-overview -->
<!-- Sitemap-Last-Modified: 2026-06-03 -->

# Overview of the user configuration API in Microsoft Graph \(preview\)

The user configuration API in Microsoft Graph lets your application store and retrieve per-folder configuration data alongside the contents of an Exchange Online mailbox. A [userConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/userconfiguration?view=graph-rest-beta&preserve-view=true) object \(folder associated item, FAI\) is associated with a specific mail folder and identified by a key that's unique within that folder. Each object applies to a single folder rather than the whole mailbox. This scoping lets your app keep state close to the content it relates to.

The API gives your app full create, read, update, and delete control over **userConfiguration** objects, and supports multiple payload styles that let you store the format that best fits your scenario: arbitrary binary data, serialized XML, or strongly typed key-value pairs.

## Why integrate with the user configuration API?

### Store per-folder application state and settings

Many applications need a reliable place to keep settings or state that pertains to a specific mail folder. Examples include the last-synchronized item ID for an inbox synchronization tool, view preferences for a custom folder, or feature flags scoped to a folder. The user configuration API gives your app a dedicated, mailbox-resident storage location for this kind of data, so you don't have to maintain a separate external store.

### Persist app metadata alongside mailbox content

User configuration objects live inside the mailbox. As a result, the data sits close to the content it relates to, and the same access controls that protect the user's other mailbox content also protect this data. This storage pattern makes the API a good fit for app metadata that should remain tied to a specific folder.

### Choose the payload style that fits your data

The **userConfiguration** resource supports three payload properties, and you can pick the right shape for your scenario:

- Use **binaryData** for arbitrary binary content.
- Use **xmlData** for serialized XML.
- Use **structuredData** to store typed key-value pairs without serializing your own format. The [structuredDataEntry](https://learn.microsoft.com/en-us/graph/api/resources/structureddataentry?view=graph-rest-beta&preserve-view=true) and [structuredDataEntryTypedValue](https://learn.microsoft.com/en-us/graph/api/resources/structureddataentrytypedvalue?view=graph-rest-beta&preserve-view=true) complex types model the supported value types.

A single **userConfiguration** object can carry any combination of these properties. You can mix payload styles as your app evolves.

## API reference

Looking for the API reference for this service? See the [userConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/userconfiguration?view=graph-rest-beta&preserve-view=true) resource type and its supported methods.

## Next steps

- Explore the [userConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/userconfiguration?view=graph-rest-beta&preserve-view=true) resource type and its supported methods \(Create, Get, Update, Delete\).
- Try the user configuration API in [Graph Explorer](https://developer.microsoft.com/graph/graph-explorer).
