<!-- Source: https://learn.microsoft.com/en-us/defender-cloud-apps/api-entities-fetch-tree -->
<!-- Sitemap-Last-Modified: 2024-10-23 -->

# Fetch entity tree - Entities API

Note

This request is not available for Microsoft 365 Cloud App Security.

Run the GET request to fetch all entities related to the entity matching the specified primary key. If the entity is a user, fetches all accounts associated with the user. If the entity is an account, fetches the entity's parent and siblings.

## HTTP request

```rest
GET /api/v1/entities/<pk>/retrieve_tree/
```

## Request URL parameters

| Parameter | Description |
| --- | --- |
| pk | The ID of the entity |

## Example

### Request

Here is an example of the request.

```rest
curl -XGET -H "Authorization:Token <your_token_key>" "https://<tenant_id>.<tenant_region>.portal.cloudappsecurity.com/api/v1/entities/<pk>/retrieve_tree/"
```

### Response

Returns the specified entity tree in JSON format.

```json
{
  // entity tree record
}
```

If you run into any problems, we're here to help. To get assistance or support for your product issue, please [open a support ticket](https://learn.microsoft.com/en-us/defender-xdr/contact-defender-support).
