<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/driftaccesspackageinfo?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-10-17 -->

# driftAccessPackageInfo resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents information about an access package associated with an access drift record.

This object is configured in the **accessPackage** property of [entraAccessDriftDetail](https://learn.microsoft.com/en-us/graph/api/resources/entraaccessdriftdetail?view=graph-rest-beta).

## Methods

None.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| displayName | String | The display name of the access package. |
| identifier | String | The unique identifier of the access package. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.driftAccessPackageInfo",
  "identifier": "String",
  "displayName": "String"
}
```
