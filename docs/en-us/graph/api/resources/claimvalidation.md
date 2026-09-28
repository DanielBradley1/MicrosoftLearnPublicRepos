<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/claimvalidation?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-05-01 -->

# claimValidation resource type

Namespace: microsoft.graph

Defines validation settings for claim processing in Verified ID profiles through the [verifiedIdProfileConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/verifiedidprofileconfiguration?view=graph-rest-1.0) object.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| customExtensionId | String | The identifier of a custom extension for claim validation. |
| isEnabled | Boolean | Indicates whether claim validation is enabled. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.claimValidation",
  "isEnabled": "Boolean",
  "customExtensionId": "String"
}
```
