<!-- Source: https://learn.microsoft.com/en-us/defender-cloud-apps/api-files-list -->
<!-- Sitemap-Last-Modified: 2025-03-13 -->

# List - Files API

Note

- This API is not available for Microsoft 365 Cloud App Security.
- This endpoint might time out when filtering and paginating large collections.

Run the GET or POST request to fetch a list of files matching the specified filters.

## HTTP request

```rest
GET /api/v1/files/
```

```rest
POST /api/v1/files/
```

## Request BODY parameters

| Parameter | Description |
| --- | --- |
| filters | Filter objects with all the search filters for the request, for more details see [file filters](https://learn.microsoft.com/en-us/defender-cloud-apps/api-files#filters) |
| skip | Skips the specified number of records |
| limit | Maximum number of records returned by the request |

## Example

### Request

Here's an example of the request.

```rest
curl -XPOST -H "Authorization:Token <your_token_key>" -H "Content-Type: application/json" "https://<tenant_id>.<tenant_region>.portal.cloudappsecurity.com/api/v1/files/" -d '{
  "filters": {
    // some filters
  },
  "skip": 5,
  "limit": 10
  ...
}'
```

### Response

Returns a list of files in JSON format.

```json
{
  "total": 5 // approximate number of records
  "hasNext": true // whether there is more data to show or not.
  "data": [
    // returned records
  ]
}
```

If you run into any problems, we're here to help. To get assistance or support for your product issue, please [open a support ticket](https://learn.microsoft.com/en-us/defender-xdr/contact-defender-support).
