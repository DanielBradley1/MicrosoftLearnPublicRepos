<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/cloudpcstatusdetail?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-06-21 -->

# cloudPcStatusDetail resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Describes the extended detail of the Cloud PC status or action status, including code, message, and additional information.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| code | String | The error/warning code associated with the Cloud PC status. Example: `"code": "internalServerError"`. |
| message | String | The status message associated with error code. Example: `"message": "There was an internal server error. Please contact support xxx."`. |
| additionalInformation | [keyValuePair](https://learn.microsoft.com/en-us/graph/api/resources/keyvaluepair?view=graph-rest-beta) collection | More information about the Cloud PC status. For example, `"additionalInformation": ["{'@odata.type': 'microsoft.graph.keyValuePair','name': 'retriable','value': true }] "` |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.cloudPcStatusDetail",
  "code": "String",
  "message": "String",
  "additionalInformation": [
    {
      "@odata.type": "microsoft.graph.keyValuePair"
    }
  ]
}
```
