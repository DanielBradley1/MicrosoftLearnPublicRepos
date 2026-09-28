<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/accesspackagesubject?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-06-24 -->

# accessPackageSubject resource type

Namespace: microsoft.graph

In [Microsoft Entra entitlement management](https://learn.microsoft.com/en-us/graph/api/resources/entitlementmanagement-overview?view=graph-rest-1.0), an access package subject is a user, service principal, or other entity that can be configured to request or be assigned an access package. It might represent a requestor from a connected organization who isn't yet in the tenant.

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [Get](https://learn.microsoft.com/en-us/graph/api/accesspackagesubject-get?view=graph-rest-1.0) | [accessPackageSubject](https://learn.microsoft.com/en-us/graph/api/resources/accesspackagesubject?view=graph-rest-1.0) | Get the properties of an **accessPackageSubject** object. |
| [Update](https://learn.microsoft.com/en-us/graph/api/accesspackagesubject-update?view=graph-rest-1.0) | None | Update the properties of an **accessPackageSubject** object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| displayName | String | The display name of the subject. |
| email | String | The email address of the subject. |
| id | String | This property shouldn't be used as a dependency, as it could change without notice. Instead, use the **objectId** property. |
| objectId | String | The object identifier of the subject. `null` if the subject isn't yet a user in the tenant. |
| onPremisesSecurityIdentifier | String | A string representation of the principal's security identifier, if known, or `null` if the subject doesn't have a security identifier. |
| principalName | String | The principal name, if known, of the subject. |
| subjectLifecycle | accessPackageSubjectLifecycle | The lifecycle of the subject user, if a guest. The possible values are: `notDefined`, `notGoverned`, `governed`, `unknownFutureValue`. |
| subjectType | accessPackageSubjectType | The resource type of the subject. The possible values are: `notSpecified`, `user`, `servicePrincipal`, `unknownFutureValue`. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| connectedOrganization | [connectedOrganization](https://learn.microsoft.com/en-us/graph/api/resources/connectedorganization?view=graph-rest-1.0) | The connected organization of the subject. Read-only. Nullable. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.accessPackageSubject",
  "displayName": "String",
  "email": "String",
  "id": "String (identifier)",
  "objectId": "String",
  "onPremisesSecurityIdentifier": "String",
  "principalName": "String",
  "subjectLifecycle": "String",
  "subjectType": "String"
}
```
