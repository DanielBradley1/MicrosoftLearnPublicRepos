<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-softwareupdate-windowsqualityupdatepolicy?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# windowsQualityUpdatePolicy resource type

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

Windows Quality Update Policy

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List windowsQualityUpdatePolicies](https://learn.microsoft.com/en-us/graph/api/intune-softwareupdate-windowsqualityupdatepolicy-list?view=graph-rest-beta) | [windowsQualityUpdatePolicy](https://learn.microsoft.com/en-us/graph/api/resources/intune-softwareupdate-windowsqualityupdatepolicy?view=graph-rest-beta) collection | List properties and relationships of the [windowsQualityUpdatePolicy](https://learn.microsoft.com/en-us/graph/api/resources/intune-softwareupdate-windowsqualityupdatepolicy?view=graph-rest-beta) objects. |
| [Get windowsQualityUpdatePolicy](https://learn.microsoft.com/en-us/graph/api/intune-softwareupdate-windowsqualityupdatepolicy-get?view=graph-rest-beta) | [windowsQualityUpdatePolicy](https://learn.microsoft.com/en-us/graph/api/resources/intune-softwareupdate-windowsqualityupdatepolicy?view=graph-rest-beta) | Read properties and relationships of the [windowsQualityUpdatePolicy](https://learn.microsoft.com/en-us/graph/api/resources/intune-softwareupdate-windowsqualityupdatepolicy?view=graph-rest-beta) object. |
| [Create windowsQualityUpdatePolicy](https://learn.microsoft.com/en-us/graph/api/intune-softwareupdate-windowsqualityupdatepolicy-create?view=graph-rest-beta) | [windowsQualityUpdatePolicy](https://learn.microsoft.com/en-us/graph/api/resources/intune-softwareupdate-windowsqualityupdatepolicy?view=graph-rest-beta) | Create a new [windowsQualityUpdatePolicy](https://learn.microsoft.com/en-us/graph/api/resources/intune-softwareupdate-windowsqualityupdatepolicy?view=graph-rest-beta) object. |
| [Delete windowsQualityUpdatePolicy](https://learn.microsoft.com/en-us/graph/api/intune-softwareupdate-windowsqualityupdatepolicy-delete?view=graph-rest-beta) | None | Deletes a [windowsQualityUpdatePolicy](https://learn.microsoft.com/en-us/graph/api/resources/intune-softwareupdate-windowsqualityupdatepolicy?view=graph-rest-beta). |
| [Update windowsQualityUpdatePolicy](https://learn.microsoft.com/en-us/graph/api/intune-softwareupdate-windowsqualityupdatepolicy-update?view=graph-rest-beta) | [windowsQualityUpdatePolicy](https://learn.microsoft.com/en-us/graph/api/resources/intune-softwareupdate-windowsqualityupdatepolicy?view=graph-rest-beta) | Update the properties of a [windowsQualityUpdatePolicy](https://learn.microsoft.com/en-us/graph/api/resources/intune-softwareupdate-windowsqualityupdatepolicy?view=graph-rest-beta) object. |
| [assign action](https://learn.microsoft.com/en-us/graph/api/intune-softwareupdate-windowsqualityupdatepolicy-assign?view=graph-rest-beta) | None |  |
| [bulkAction action](https://learn.microsoft.com/en-us/graph/api/intune-softwareupdate-windowsqualityupdatepolicy-bulkaction?view=graph-rest-beta) | [bulkCatalogItemActionResult](https://learn.microsoft.com/en-us/graph/api/resources/intune-softwareupdate-bulkcatalogitemactionresult?view=graph-rest-beta) |  |
| [retrieveWindowsQualityUpdateCatalogItemDetails function](https://learn.microsoft.com/en-us/graph/api/intune-softwareupdate-windowsqualityupdatepolicy-retrievewindowsqualityupdatecatalogitemdetails?view=graph-rest-beta) | [windowsQualityUpdateCatalogItemPolicyDetail](https://learn.microsoft.com/en-us/graph/api/resources/intune-softwareupdate-windowsqualityupdatecatalogitempolicydetail?view=graph-rest-beta) collection |  |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | This id is assigned when creating the profile. Read-only |
| displayName | String | The display name for the policy. Max allowed length is 200 chars. |
| description | String | The description of the policy which is specified by the user. Max allowed length is 1500 chars. |
| createdDateTime | DateTimeOffset | Timestamp of when the profile was created. The value cannot be modified and is automatically populated when the profile is created. The Timestamp type represents date and time information using ISO 8601 format and is always in UTC time. Read-only |
| lastModifiedDateTime | DateTimeOffset | Timestamp of when the profile was modified. The value cannot be modified and is automatically populated when the profile is modified. The Timestamp type represents date and time information using ISO 8601 format and is always in UTC time. Read-only |
| roleScopeTagIds | String collection | List of the scope tag ids for this profile. |
| hotpatchEnabled | Boolean | Indicates if hotpatch is enabled for the tenants. When 'true', tenant can apply quality updates without rebooting their devices. When 'false', tenant devices will receive cold patch associated with Windows quality updates. |
| approvalSettings | [windowsQualityUpdateApprovalSetting](https://learn.microsoft.com/en-us/graph/api/resources/intune-softwareupdate-windowsqualityupdateapprovalsetting?view=graph-rest-beta) collection | The list of approval settings for this policy. The maximun number of approval settings supported for one policy is 6. The expected number of approval settings for one policy from UX is 4. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| assignments | [windowsQualityUpdatePolicyAssignment](https://learn.microsoft.com/en-us/graph/api/resources/intune-softwareupdate-windowsqualityupdatepolicyassignment?view=graph-rest-beta) collection | List of the groups this profile is assgined to. |

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.windowsQualityUpdatePolicy",
  "id": "String (identifier)",
  "displayName": "String",
  "description": "String",
  "createdDateTime": "String (timestamp)",
  "lastModifiedDateTime": "String (timestamp)",
  "roleScopeTagIds": [
    "String"
  ],
  "hotpatchEnabled": true,
  "approvalSettings": [
    {
      "@odata.type": "microsoft.graph.windowsQualityUpdateApprovalSetting",
      "windowsQualityUpdateCadence": "String",
      "windowsQualityUpdateCategory": "String",
      "approvalMethodType": "String",
      "deferredDeploymentInDay": 1024
    }
  ]
}
```
