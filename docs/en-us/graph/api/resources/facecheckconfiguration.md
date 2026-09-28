<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/facecheckconfiguration?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-08-04 -->

# faceCheckConfiguration resource type

Namespace: microsoft.graph

Configuration for Face Check requirements in a [Verified ID Profile](https://learn.microsoft.com/en-us/graph/api/resources/verifiedidprofile?view=graph-rest-1.0).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| isEnabled | Boolean | Defines if Face Check is required. Currently must always be `true`. |
| sourcePhotoClaimName | String | Source of photo to validate Face Check against. Currently must always be `portrait`. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.faceCheckConfiguration",
  "isEnabled": "Boolean",
  "sourcePhotoClaimName": "String"
}
```
