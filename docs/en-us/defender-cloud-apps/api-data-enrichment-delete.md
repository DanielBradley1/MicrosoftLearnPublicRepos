<!-- Source: https://learn.microsoft.com/en-us/defender-cloud-apps/api-data-enrichment-delete -->
<!-- Sitemap-Last-Modified: 2024-10-23 -->

# Delete IP address range - Data Enrichment API

Run the DELETE request to delete an IP address range.

## HTTP request

```rest
DELETE /api/v1/subnet/<ip_range_id>/
```

## Example

### Request

Here's an example of the request.

```rest
curl -X DELETE -H "Authorization:Token <your_token_key>" "https://<tenant_id>.<tenant_region>.portal.cloudappsecurity.com/api/v1/subnet/<ip_range_id>/"
```

If you run into any problems, we're here to help. To get assistance or support for your product issue, please [open a support ticket](https://learn.microsoft.com/en-us/defender-xdr/contact-defender-support).
