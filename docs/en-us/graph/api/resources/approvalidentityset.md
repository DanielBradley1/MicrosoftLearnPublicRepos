<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/approvalidentityset?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-08-02 -->

# approvalIdentitySet resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents a keyed collection of [identity](https://learn.microsoft.com/en-us/graph/api/resources/identity?view=graph-rest-beta) resources that are associated with an approval item.

Inherits from [identitySet](https://learn.microsoft.com/en-us/graph/api/resources/identityset?view=graph-rest-beta).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| group | [identity](https://learn.microsoft.com/en-us/graph/api/resources/identity?view=graph-rest-beta) | The Microsoft Entra group associated with the approval item. |
| user | [identity](https://learn.microsoft.com/en-us/graph/api/resources/identity?view=graph-rest-beta) | The user associated with the approval item. Inherited from [identitySet](https://learn.microsoft.com/en-us/graph/api/resources/identityset?view=graph-rest-beta). |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.approvalIdentitySet",
  "user": {
    "@odata.type": "microsoft.graph.identity"
  },
  "group": {
    "@odata.type": "microsoft.graph.identity"
  }
}
```
