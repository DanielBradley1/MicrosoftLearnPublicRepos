<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/defaultsharinglink?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-05-04 -->

# defaultSharingLink resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents the default sharing link a user can create.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| defaultToExistingAccess | Boolean | Indicates whether the default link setting for this object is a direct URL rather than a sharing link. |
| role | sharingRole | The default sharing link role. The possible values are: `none`, `view`, `edit`, `manageList`, `review`, `restrictedView`, `submitOnly`, `unknownFutureValue`. |
| scope | sharingScope | The default sharing link scope. The possible values are: `anyone`, `organization`, `specificPeople`, `anonymous`, `users`, `unknownFutureValue`. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.defaultSharingLink",
  "role": "String",
  "scope": "String",
  "defaultToExistingAccess": "Boolean"
}
```
