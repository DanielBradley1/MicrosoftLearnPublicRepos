<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-devicelogcollectionrequest?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-01-08 -->

# deviceLogCollectionRequest resource type

Namespace: microsoft.graph

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

Windows Log Collection request entity.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | The unique identifier |
| templateType | [deviceLogCollectionTemplateType](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-devicelogcollectiontemplatetype?view=graph-rest-1.0) | Indicates The template type that is sent with the collection request. defaule is Predefined. The possible values are: `predefined`, `unknownFutureValue`. |

## Relationships

None

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.deviceLogCollectionRequest",
  "id": "String (identifier)",
  "templateType": "String"
}
```
