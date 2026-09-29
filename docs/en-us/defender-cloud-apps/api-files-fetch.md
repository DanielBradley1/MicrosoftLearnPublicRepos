<!-- Source: https://learn.microsoft.com/en-us/defender-cloud-apps/api-files-fetch -->
<!-- Sitemap-Last-Modified: 2024-10-23 -->

# Fetch - Files API

Note

- This API is not available for Microsoft 365 Cloud App Security.

Run the GET request to fetch the file matching the specified primary key.

## HTTP request

```rest
GET /api/v1/files/<pk>/
```

## Request URL parameters

| Parameter | Description |
| --- | --- |
| pk | The ID of the file |

## Example

### Request

Here is an example of the request.

```rest
curl -XPOST -H "Authorization:Token <your_token_key>" "https://<tenant_id>.<tenant_region>.portal.cloudappsecurity.com/api/v1/files/<pk>/"
```

### Response

Returns the specified file.

If you run into any problems, we're here to help. To get assistance or support for your product issue, please [open a support ticket](https://learn.microsoft.com/en-us/defender-xdr/contact-defender-support).
