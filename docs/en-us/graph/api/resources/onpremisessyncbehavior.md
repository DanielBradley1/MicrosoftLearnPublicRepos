<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/onpremisessyncbehavior?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-09-23 -->

# onPremisesSyncBehavior resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Indicates the synchronization settings for a directory object between the cloud and on-premises Active Directory for [group](https://learn.microsoft.com/en-us/graph/api/resources/group?view=graph-rest-beta), [user](https://learn.microsoft.com/en-us/graph/api/resources/user?view=graph-rest-beta), and [orgContact](https://learn.microsoft.com/en-us/graph/api/resources/orgcontact?view=graph-rest-beta) resources.

For more information, see [Convert Group Source of Authority to the cloud](https://learn.microsoft.com/en-us/entra/identity/hybrid/concept-source-of-authority-overview).

Inherits from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [Get](https://learn.microsoft.com/en-us/graph/api/onpremisessyncbehavior-get?view=graph-rest-beta) | [onPremisesSyncBehavior](https://learn.microsoft.com/en-us/graph/api/resources/onpremisessyncbehavior?view=graph-rest-beta) | Read the properties of an onPremisesSyncBehavior object. |
| [Update](https://learn.microsoft.com/en-us/graph/api/onpremisessyncbehavior-update?view=graph-rest-beta) | [onPremisesSyncBehavior](https://learn.microsoft.com/en-us/graph/api/resources/onpremisessyncbehavior?view=graph-rest-beta) | Update the properties of an onPremisesSyncBehavior object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | The object ID of the parent object. Read-only. Inherits from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta) |
| isCloudManaged | Boolean | Indicates the state of synchronization for an object between the cloud and on-premises Active Directory. If `true`, updates from on-premises Active Directory are blocked in the cloud; if `false`, updates from on-premises Active Directory are allowed in the cloud and the on-premises Active Directory can take over the object. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.onPremisesSyncBehavior",
  "id": "String (identifier)",
  "isCloudManaged": "Boolean"
}
```
