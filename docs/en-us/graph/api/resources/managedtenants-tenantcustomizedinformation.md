<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/managedtenants-tenantcustomizedinformation?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-05-24 -->

# tenantCustomizedInformation resource type

Namespace: microsoft.graph.managedTenants

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents customizable information for a managed tenant.

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List tenant customized information](https://learn.microsoft.com/en-us/graph/api/managedtenants-managedtenant-list-tenantscustomizedinformation?view=graph-rest-beta) | [microsoft.graph.managedTenants.tenantCustomizedInformation](https://learn.microsoft.com/en-us/graph/api/resources/managedtenants-tenantcustomizedinformation?view=graph-rest-beta) collection | Get a list of the [tenantCustomizedInformation](https://learn.microsoft.com/en-us/graph/api/resources/managedtenants-tenantcustomizedinformation?view=graph-rest-beta) objects and their properties. |
| [Get tenant customized information](https://learn.microsoft.com/en-us/graph/api/managedtenants-tenantcustomizedinformation-get?view=graph-rest-beta) | [microsoft.graph.managedTenants.tenantCustomizedInformation](https://learn.microsoft.com/en-us/graph/api/resources/managedtenants-tenantcustomizedinformation?view=graph-rest-beta) | Read the properties and relationships of a [tenantCustomizedInformation](https://learn.microsoft.com/en-us/graph/api/resources/managedtenants-tenantcustomizedinformation?view=graph-rest-beta) object. |
| [Update tenant customized information](https://learn.microsoft.com/en-us/graph/api/managedtenants-tenantcustomizedinformation-update?view=graph-rest-beta) | [microsoft.graph.managedTenants.tenantCustomizedInformation](https://learn.microsoft.com/en-us/graph/api/resources/managedtenants-tenantcustomizedinformation?view=graph-rest-beta) | Update the properties of a [tenantCustomizedInformation](https://learn.microsoft.com/en-us/graph/api/resources/managedtenants-tenantcustomizedinformation?view=graph-rest-beta) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| contacts | [microsoft.graph.managedTenants.tenantContactInformation](https://learn.microsoft.com/en-us/graph/api/resources/managedtenants-tenantcontactinformation?view=graph-rest-beta) collection | The collection of contacts for the managed tenant. Optional. |
| displayName | String | The display name for the managed tenant. Required. Read-only. |
| id | String | The Microsoft Entra tenant identifier for the managed tenant. Required. Read-only. |
| tenantId | String | The Microsoft Entra tenant identifier for the [managed tenant](https://learn.microsoft.com/en-us/graph/api/resources/managedtenants-tenant?view=graph-rest-beta). Optional. Read-only. |
| website | String | The website for the managed tenant. Required. |
| businessRelationship | String | Describes the relationship between the Managed Services Provider and the managed tenant; for example, Managed, Co-managed, Licensing. The maximum length is 250 characters. Optional. |
| complianceRequirements | String collection | Contains the compliance requirements for the customer tenant; for example, HIPPA, NIST, CMMC. The maximum length is 250 characters per compliance requirement. Optional. |
| managedServicesPlans | String collection | This is the Managed Services Plans for the customer tenant that the Managed Services Provider manages. The maximum length is 250 characters per managed service plan. Optional. |
| note | String | A field for the Managed Services Provider technician to input custom text to share notes between technicians within the Managed Service Providers. The maximum length is 5000 characters. Optional. |
| noteLastModifiedDateTime | DateTimeOffset | The date on which the note field of this entity was last modified. Optional. |
| partnerRelationshipManagerUserIds | String collection | The list of Entra user IDs for users in the Managed Services Provider that manage the relationship with the managed tenant. Optional. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
    {
      "id": "34298981-4fc8-4974-9486-c8909ed1521b",
      "tenantId": "34298981-4fc8-4974-9486-c8909ed1521b",
      "website": "https://www.fourthcoffee.com",
      "contacts": [
        {
          "name": "Sally",
          "email": "sally@fourthcoffee.com",
          "phone": "5558009731"
        },
        {
          "name": "Hector",
          "email": "hector@fourthcoffee.com",
          "phone": "5558009732"
        }
      ],
      "businessRelationship": "Managed",
      "complianceRequirements": [
        "NIST",
        "HIPPA"
      ],
      "managedServicesPlans": [
        "Microsoft Entra ID P1"
      ],
      "note": "This is a test note.",
      "noteLastModifiedDateTime": "2024-04-03 00:10:21.1989208",
      "partnerRelationshipManagerUserIds": [
        "3c23994c-711b-46f6-ab1e-0aeef19413f3"
      ]
    }
```
