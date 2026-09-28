<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/identityinfo?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-07-04 -->

# identityInfo resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents the identity information \(**sourceIdentity** and **targetIdentity** properties\) used in a [correlatedIdentity](https://learn.microsoft.com/en-us/graph/api/resources/correlatedidentity?view=graph-rest-beta) object in [identity correlation reports](https://learn.microsoft.com/en-us/graph/api/resources/identitycorrelation?view=graph-rest-beta). Contains the anchor property, matching property, identity type, and additional details for a source or target identity.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| anchor | [attributeInfo](https://learn.microsoft.com/en-us/graph/api/resources/attributeinfo?view=graph-rest-beta) | The anchor property that uniquely identifies the identity in its directory. |
| details | [detailsInfo](https://learn.microsoft.com/en-us/graph/api/resources/detailsinfo?view=graph-rest-beta) | Additional details about the identity. |
| identityType | String | The type of identity, such as `user`. |
| matchingProperty | [attributeInfo](https://learn.microsoft.com/en-us/graph/api/resources/attributeinfo?view=graph-rest-beta) | The property used to match identities across directories. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.identityInfo",
  "anchor": {
    "@odata.type": "microsoft.graph.attributeInfo",
    "name": "String",
    "value": "String"
  },
  "matchingProperty": {
    "@odata.type": "microsoft.graph.attributeInfo",
    "name": "String",
    "value": "String"
  },
  "identityType": "String",
  "details": {
    "@odata.type": "microsoft.graph.detailsInfo"
  }
}
```
