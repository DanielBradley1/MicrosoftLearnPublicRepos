<!-- Source: https://learn.microsoft.com/en-us/defender-cloud-apps/api-entities-list -->
<!-- Sitemap-Last-Modified: 2025-03-13 -->

# List - Entities API

Note

This request is not available for Microsoft 365 Cloud App Security.

Run the GET or POST request to fetch a list of entities matching the specified filters.

## HTTP request

```rest
GET /api/v1/entities/
```

```rest
POST /api/v1/entities/
```

## Request BODY parameters

| Parameter | Description |
| --- | --- |
| filters | Filter objects with all the search filters for the request, for more details see [entity filters](https://learn.microsoft.com/en-us/defender-cloud-apps/api-entities#filters) |
| sortDirection | The sorting direction. Possible values are: `asc` and `desc` |
| sortField | Fields used to sort entities. Possible values are:  <br>- **date**: The date when then the entity was created  <br>- **severity**: The severity of the entity |
| skip | Skips the specified number of records |
| limit | Maximum number of records returned by the request |

## Example

### Request

Here's an example of the request.

```rest
curl -XPOST -H "Authorization:Token <your_token_key>" -H "Content-Type: application/json" "https://<tenant_id>.<tenant_region>.portal.cloudappsecurity.com/api/v1/entities/" -d '{
  "filters": {
    // some filters
  },
  "skip": 5,
  "limit": 10
  ...
}'
```

### Response

Returns a list of activities in JSON format.

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
