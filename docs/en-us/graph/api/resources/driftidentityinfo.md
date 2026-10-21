<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/driftidentityinfo?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-10-17 -->

# driftIdentityInfo resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents an abstract base type for identity information in an access drift record. Derived types include [entraDriftIdentityInfo](https://learn.microsoft.com/en-us/graph/api/resources/entradriftidentityinfo?view=graph-rest-beta) and [localDriftIdentityInfo](https://learn.microsoft.com/en-us/graph/api/resources/localdriftidentityinfo?view=graph-rest-beta).

This object is returned in the **identities** relationship of [accessDriftDetail](https://learn.microsoft.com/en-us/graph/api/resources/accessdriftdetail?view=graph-rest-beta).

This is an abstract type.

## Methods

None.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| displayName | String | The display name of the identity. |
| identifier | String | The unique identifier for the identity within the drift record. |
| principalName | String | The principal name of the identity. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.driftIdentityInfo",
  "identifier": "String (identifier)",
  "principalName": "String",
  "displayName": "String"
}
```
