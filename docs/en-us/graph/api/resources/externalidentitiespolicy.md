<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/externalidentitiespolicy?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-05-24 -->

# externalIdentitiesPolicy resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents the tenant-wide policy that controls whether external users can leave the guest Microsoft Entra tenant via self-service controls. When permitted by the administrator, external users can leave the guest Microsoft Entra tenant through the **organizations** menu of the [My Account](https://myaccount.microsoft.com/) portal.

Inherits from [policyBase](https://learn.microsoft.com/en-us/graph/api/resources/policybase?view=graph-rest-beta).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [Get](https://learn.microsoft.com/en-us/graph/api/externalidentitiespolicy-get?view=graph-rest-beta) | [externalIdentitiesPolicy](https://learn.microsoft.com/en-us/graph/api/resources/externalidentitiespolicy?view=graph-rest-beta) | Read the properties and relationships of an [externalIdentitiesPolicy](https://learn.microsoft.com/en-us/graph/api/resources/externalidentitiespolicy?view=graph-rest-beta) object. |
| [Update](https://learn.microsoft.com/en-us/graph/api/externalidentitiespolicy-update?view=graph-rest-beta) | [externalIdentitiesPolicy](https://learn.microsoft.com/en-us/graph/api/resources/externalidentitiespolicy?view=graph-rest-beta) | Update the properties of an [externalIdentitiesPolicy](https://learn.microsoft.com/en-us/graph/api/resources/externalidentitiespolicy?view=graph-rest-beta) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| allowDeletedIdentitiesDataRemoval | Boolean | **Reserved for future use.** |
| allowExternalIdentitiesToLeave | Boolean | Defines whether external users can leave the guest tenant. If set to `false`, self-service controls are disabled, and the admin of the guest tenant must manually remove the external user from the guest tenant. When the external user leaves the tenant, their data in the guest tenant is first soft-deleted then permanently deleted in 30 days. |
| displayName | String | The policy name. Inherited from [policyBase](https://learn.microsoft.com/en-us/graph/api/resources/policybase?view=graph-rest-beta). |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.externalIdentitiesPolicy",
  "id": "String (identifier)",
  "description": "String",
  "displayName": "String",
  "allowExternalIdentitiesToLeave": "Boolean",
  "allowDeletedIdentitiesDataRemoval": "Boolean"
}
```

## Related content

- [Leave an organization as an external user](https://learn.microsoft.com/en-us/azure/active-directory/external-identities/leave-the-organization)
