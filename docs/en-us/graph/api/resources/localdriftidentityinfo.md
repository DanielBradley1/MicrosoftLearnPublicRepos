<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/localdriftidentityinfo?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-10-17 -->

# localDriftIdentityInfo resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents identity information from a local or external system in an access drift record.

This object can be returned in the **identities** relationship of [accessDriftDetail](https://learn.microsoft.com/en-us/graph/api/resources/accessdriftdetail?view=graph-rest-beta).

Inherits from [driftIdentityInfo](https://learn.microsoft.com/en-us/graph/api/resources/driftidentityinfo?view=graph-rest-beta).

## Methods

None.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| displayName | String | The display name of the identity. Inherited from [driftIdentityInfo](https://learn.microsoft.com/en-us/graph/api/resources/driftidentityinfo?view=graph-rest-beta). |
| identifier | String | The unique identifier for the identity. Inherited from [driftIdentityInfo](https://learn.microsoft.com/en-us/graph/api/resources/driftidentityinfo?view=graph-rest-beta). |
| principalName | String | The principal name of the identity. Inherited from [driftIdentityInfo](https://learn.microsoft.com/en-us/graph/api/resources/driftidentityinfo?view=graph-rest-beta). |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.localDriftIdentityInfo",
  "identifier": "String (identifier)",
  "principalName": "String",
  "displayName": "String"
}
```
