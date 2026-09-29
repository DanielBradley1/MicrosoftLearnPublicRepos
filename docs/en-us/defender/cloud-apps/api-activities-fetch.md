<!-- Source: https://learn.microsoft.com/en-us/defender-cloud-apps/api-activities-fetch -->
<!-- Sitemap-Last-Modified: 2025-11-05 -->

# Fetch - Activities API

Run the GET request to fetch the activity matching the specified primary key.

## HTTP request

```rest
GET /api/v1/activities/<pk>/
```

## Request URL parameters

| Parameter | Description |
| --- | --- |
| pk | The ID of the activity |

## Example

### Request

Here's an example of the request.

```rest
curl -XGET -H "Authorization:Token <your_token_key>" "https://<tenant_id>.<tenant_region>.portal.cloudappsecurity.com/api/v1/activities/<pk>/"
```

### Response

Returns the specified activity in JSON format.

```json
{
  // activity record
}
```

If you run into any problems, we're here to help. To get assistance or support for your product issue, [open a support ticket](https://learn.microsoft.com/en-us/defender-xdr/contact-defender-support).
