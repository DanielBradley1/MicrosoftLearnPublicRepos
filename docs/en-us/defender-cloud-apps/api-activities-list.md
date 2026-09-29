<!-- Source: https://learn.microsoft.com/en-us/defender-cloud-apps/api-activities-list -->
<!-- Sitemap-Last-Modified: 2025-03-13 -->

# List - Activities API

Run the GET or POST request to fetch a list of activities matching the specified filters.

## HTTP request

```rest
GET /api/v1/activities/
```

```rest
POST /api/v1/activities/
```

## Request BODY parameters

| Parameter | Description |
| --- | --- |
| filters | Filter objects with all the search filters for the request, for more details see [activity filters](https://learn.microsoft.com/en-us/defender-cloud-apps/api-activities#filters) |
| sortDirection | The sorting direction. Possible values are: `asc` and `desc` |
| sortField | Fields used to sort activities. Possible values are:<br><br><li> <strong>date</strong>: The date when then the activity happened </li><br><br><li> <strong>created</strong>: The <a href="https://learn.microsoft.com/en-us/defender-cloud-apps/api-introduction#timestamps" data-linktype="relative-path">timestamp</a> when the activity was saved</li> |
| skip | Skips the specified number of records |
| limit | Maximum number of records returned by the request |

## Example

### Request

Here's an example of the request.

```rest
curl -XPOST -H "Authorization:Token <your_token_key>" -H "Content-Type: application/json" "https://<tenant_id>.<tenant_region>.portal.cloudappsecurity.com/api/v1/activities/" -d '{
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
