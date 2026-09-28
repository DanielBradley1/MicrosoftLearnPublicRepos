<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-unlock-windowsdefenderapplicationcontrolsupplementalpolicy?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-10-11 -->

# windowsDefenderApplicationControlSupplementalPolicy resource type

Namespace: microsoft.graph

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List windowsDefenderApplicationControlSupplementalPolicies](https://learn.microsoft.com/en-us/graph/api/intune-unlock-windowsdefenderapplicationcontrolsupplementalpolicy-list?view=graph-rest-1.0) | [windowsDefenderApplicationControlSupplementalPolicy](https://learn.microsoft.com/en-us/graph/api/resources/intune-unlock-windowsdefenderapplicationcontrolsupplementalpolicy?view=graph-rest-1.0) collection | List properties and relationships of the [windowsDefenderApplicationControlSupplementalPolicy](https://learn.microsoft.com/en-us/graph/api/resources/intune-unlock-windowsdefenderapplicationcontrolsupplementalpolicy?view=graph-rest-1.0) objects. |
| [Get windowsDefenderApplicationControlSupplementalPolicy](https://learn.microsoft.com/en-us/graph/api/intune-unlock-windowsdefenderapplicationcontrolsupplementalpolicy-get?view=graph-rest-1.0) | [windowsDefenderApplicationControlSupplementalPolicy](https://learn.microsoft.com/en-us/graph/api/resources/intune-unlock-windowsdefenderapplicationcontrolsupplementalpolicy?view=graph-rest-1.0) | Read properties and relationships of the [windowsDefenderApplicationControlSupplementalPolicy](https://learn.microsoft.com/en-us/graph/api/resources/intune-unlock-windowsdefenderapplicationcontrolsupplementalpolicy?view=graph-rest-1.0) object. |
| [Create windowsDefenderApplicationControlSupplementalPolicy](https://learn.microsoft.com/en-us/graph/api/intune-unlock-windowsdefenderapplicationcontrolsupplementalpolicy-create?view=graph-rest-1.0) | [windowsDefenderApplicationControlSupplementalPolicy](https://learn.microsoft.com/en-us/graph/api/resources/intune-unlock-windowsdefenderapplicationcontrolsupplementalpolicy?view=graph-rest-1.0) | Create a new [windowsDefenderApplicationControlSupplementalPolicy](https://learn.microsoft.com/en-us/graph/api/resources/intune-unlock-windowsdefenderapplicationcontrolsupplementalpolicy?view=graph-rest-1.0) object. |
| [Delete windowsDefenderApplicationControlSupplementalPolicy](https://learn.microsoft.com/en-us/graph/api/intune-unlock-windowsdefenderapplicationcontrolsupplementalpolicy-delete?view=graph-rest-1.0) | None | Deletes a [windowsDefenderApplicationControlSupplementalPolicy](https://learn.microsoft.com/en-us/graph/api/resources/intune-unlock-windowsdefenderapplicationcontrolsupplementalpolicy?view=graph-rest-1.0). |
| [Update windowsDefenderApplicationControlSupplementalPolicy](https://learn.microsoft.com/en-us/graph/api/intune-unlock-windowsdefenderapplicationcontrolsupplementalpolicy-update?view=graph-rest-1.0) | [windowsDefenderApplicationControlSupplementalPolicy](https://learn.microsoft.com/en-us/graph/api/resources/intune-unlock-windowsdefenderapplicationcontrolsupplementalpolicy?view=graph-rest-1.0) | Update the properties of a [windowsDefenderApplicationControlSupplementalPolicy](https://learn.microsoft.com/en-us/graph/api/resources/intune-unlock-windowsdefenderapplicationcontrolsupplementalpolicy?view=graph-rest-1.0) object. |
| [assign action](https://learn.microsoft.com/en-us/graph/api/intune-unlock-windowsdefenderapplicationcontrolsupplementalpolicy-assign?view=graph-rest-1.0) | None |  |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | The unique identifier of the Windows Defender Application Control Supplemental Policy. This id is assigned during creation of the policy. |
| displayName | String | The display name of the Windows Defender Application Control Supplemental Policy. |
| description | String | The description of the Windows Defender Application Control Supplemental Policy. |
| content | Binary | Indicates the content of the Windows Defender Application Control Supplemental Policy in byte array format. |
| contentFileName | String | Indicates the file name associated with the content of the Windows Defender Application Control Supplemental Policy. |
| version | String | Indicates the Windows Defender Application Control Supplemental Policy's version. |
| creationDateTime | DateTimeOffset | Indicates the created date and time when the Windows Defender Application Control Supplemental Policy was uploaded. |
| lastModifiedDateTime | DateTimeOffset | Indicates the last modified date and time of the Windows Defender Application Control Supplemental Policy. |
| roleScopeTagIds | String collection | List of Scope Tags for the Windows Defender Application Control Supplemental Policy entity. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| assignments | [windowsDefenderApplicationControlSupplementalPolicyAssignment](https://learn.microsoft.com/en-us/graph/api/resources/intune-unlock-windowsdefenderapplicationcontrolsupplementalpolicyassignment?view=graph-rest-1.0) collection | The associated group assignments for the Windows Defender Application Control Supplemental Policy. |

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.windowsDefenderApplicationControlSupplementalPolicy",
  "id": "String (identifier)",
  "displayName": "String",
  "description": "String",
  "content": "binary",
  "contentFileName": "String",
  "version": "String",
  "creationDateTime": "String (timestamp)",
  "lastModifiedDateTime": "String (timestamp)",
  "roleScopeTagIds": [
    "String"
  ]
}
```
