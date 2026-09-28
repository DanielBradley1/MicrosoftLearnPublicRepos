<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/cloudpcstatusdetails?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-06-21 -->

# cloudPcStatusDetails resource type \(deprecated\)

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents details about a Cloud PC status.

Note

This resource type is deprecated and will stop returning data on August 31, 2024. Use [cloudPcStatusDetail](https://learn.microsoft.com/en-us/graph/api/resources/cloudpcstatusdetail?view=graph-rest-beta) instead.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| additionalInformation | [keyValuePair](https://learn.microsoft.com/en-us/graph/api/resources/keyvaluepair?view=graph-rest-beta) collection | Any additional information about the Cloud PC status. |
| code | String | The code associated with the Cloud PC status. |
| message | String | The status message. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.cloudPcStatusDetails",
  "additionalInformation": [
    {
      "@odata.type": "microsoft.graph.keyValuePair"
    }
  ],
  "code": "String",
  "message": "String"
}
```
