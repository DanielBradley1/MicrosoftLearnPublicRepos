<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-filteringprofile?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-05-24 -->

# filteringProfile resource type

Namespace: microsoft.graph.networkaccess

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Associates network access policies with Microsoft Entra ID Conditional Access policies, so that access policies can be applied to users and groups.

Inherits from [microsoft.graph.networkaccess.profile](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-profile?view=graph-rest-beta).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/networkaccess-filteringprofile-list?view=graph-rest-beta) | [microsoft.graph.networkaccess.filteringProfile](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-filteringprofile?view=graph-rest-beta) collection | Get a list of the [microsoft.graph.networkaccess.filteringProfile](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-filteringprofile?view=graph-rest-beta) objects and their properties. |
| [Get](https://learn.microsoft.com/en-us/graph/api/networkaccess-filteringprofile-get?view=graph-rest-beta) | [microsoft.graph.networkaccess.filteringProfile](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-filteringprofile?view=graph-rest-beta) | Get a [microsoft.graph.networkaccess.filteringProfile](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-filteringprofile?view=graph-rest-beta) object. |
| [Update](https://learn.microsoft.com/en-us/graph/api/networkaccess-filteringprofile-update?view=graph-rest-beta) | [microsoft.graph.networkaccess.filteringProfile](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-filteringprofile?view=graph-rest-beta) | Update the properties of a [microsoft.graph.networkaccess.filteringProfile](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-filteringprofile?view=graph-rest-beta) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| createdDateTime | DateTimeOffset | The date and time when the filteringProfile was created. |
| description | String | A description of the filtering profile. Inherited from [microsoft.graph.networkaccess.profile](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-profile?view=graph-rest-beta). |
| id | String | The distinct identifier that is assigned to a specific profile. Inherited from [microsoft.graph.entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta). |
| lastModifiedDateTime | DateTimeOffset | The date and time when a particular profile was last modified or updated. Inherited from [microsoft.graph.networkaccess.profile](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-profile?view=graph-rest-beta). |
| name | String | The name of the profile. Inherited from [microsoft.graph.networkaccess.profile](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-profile?view=graph-rest-beta). |
| priority | Int64 | The priority used to order the profile for processing within a list. |
| state | microsoft.graph.networkaccess.status | The profile state. Inherited from [microsoft.graph.networkaccess.profile](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-profile?view=graph-rest-beta). The possible values are: `enabled`, `disabled`. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| conditionalAccessPolicies | [microsoft.graph.networkaccess.conditionalAccessPolicy](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-conditionalaccesspolicy?view=graph-rest-beta) collection | A set of associated policies defined to regulate access to resources or systems based on specific conditions. Automatically expanded. |
| policies | [microsoft.graph.networkaccess.policyLink](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-policylink?view=graph-rest-beta) collection | The collection of policies that are linked to this filtering profile. Inherited from [microsoft.graph.networkaccess.profile](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-profile?view=graph-rest-beta). Supports `$expand`. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.networkaccess.filteringProfile",
  "id": "String (identifier)",
  "name": "String",
  "description": "String",
  "state": "String",
  "version": "String",
  "lastModifiedDateTime": "String (timestamp)",
  "priority": "Integer",
  "createdDateTime": "String (timestamp)"
}
```
