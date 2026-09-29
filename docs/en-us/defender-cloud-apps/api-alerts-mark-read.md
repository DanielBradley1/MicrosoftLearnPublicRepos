<!-- Source: https://learn.microsoft.com/en-us/defender-cloud-apps/api-alerts-mark-read -->
<!-- Sitemap-Last-Modified: 2025-11-05 -->

# Mark as read - Alerts API

Run the POST request to mark the alert matching the specified primary key as read.

## HTTP request

```rest
POST /api/v1/alerts/<pk>/read/
```

## Request URL parameters

| Parameter | Description |
| --- | --- |
| pk | The ID of the alert |

## Example

### Request

Here's an example of the request.

```rest
curl -XPOST -H "Authorization:Token <your_token_key>" -H "Content-Type: application/json" "https://<tenant_id>.<tenant_region>.portal.cloudappsecurity.com/api/v1/alerts/<pk>/read/"
```

If you run into any problems, we're here to help. To get assistance or support for your product issue, please [open a support ticket](https://learn.microsoft.com/en-us/defender-xdr/contact-defender-support).
