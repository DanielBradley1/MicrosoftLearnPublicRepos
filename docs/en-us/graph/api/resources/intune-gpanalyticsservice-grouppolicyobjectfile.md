<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-gpanalyticsservice-grouppolicyobjectfile?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# groupPolicyObjectFile resource type

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

The Group Policy Object file uploaded by admin.

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List groupPolicyObjectFiles](https://learn.microsoft.com/en-us/graph/api/intune-gpanalyticsservice-grouppolicyobjectfile-list?view=graph-rest-beta) | [groupPolicyObjectFile](https://learn.microsoft.com/en-us/graph/api/resources/intune-gpanalyticsservice-grouppolicyobjectfile?view=graph-rest-beta) collection | List properties and relationships of the [groupPolicyObjectFile](https://learn.microsoft.com/en-us/graph/api/resources/intune-gpanalyticsservice-grouppolicyobjectfile?view=graph-rest-beta) objects. |
| [Get groupPolicyObjectFile](https://learn.microsoft.com/en-us/graph/api/intune-gpanalyticsservice-grouppolicyobjectfile-get?view=graph-rest-beta) | [groupPolicyObjectFile](https://learn.microsoft.com/en-us/graph/api/resources/intune-gpanalyticsservice-grouppolicyobjectfile?view=graph-rest-beta) | Read properties and relationships of the [groupPolicyObjectFile](https://learn.microsoft.com/en-us/graph/api/resources/intune-gpanalyticsservice-grouppolicyobjectfile?view=graph-rest-beta) object. |
| [Create groupPolicyObjectFile](https://learn.microsoft.com/en-us/graph/api/intune-gpanalyticsservice-grouppolicyobjectfile-create?view=graph-rest-beta) | [groupPolicyObjectFile](https://learn.microsoft.com/en-us/graph/api/resources/intune-gpanalyticsservice-grouppolicyobjectfile?view=graph-rest-beta) | Create a new [groupPolicyObjectFile](https://learn.microsoft.com/en-us/graph/api/resources/intune-gpanalyticsservice-grouppolicyobjectfile?view=graph-rest-beta) object. |
| [Delete groupPolicyObjectFile](https://learn.microsoft.com/en-us/graph/api/intune-gpanalyticsservice-grouppolicyobjectfile-delete?view=graph-rest-beta) | None | Deletes a [groupPolicyObjectFile](https://learn.microsoft.com/en-us/graph/api/resources/intune-gpanalyticsservice-grouppolicyobjectfile?view=graph-rest-beta). |
| [Update groupPolicyObjectFile](https://learn.microsoft.com/en-us/graph/api/intune-gpanalyticsservice-grouppolicyobjectfile-update?view=graph-rest-beta) | [groupPolicyObjectFile](https://learn.microsoft.com/en-us/graph/api/resources/intune-gpanalyticsservice-grouppolicyobjectfile?view=graph-rest-beta) | Update the properties of a [groupPolicyObjectFile](https://learn.microsoft.com/en-us/graph/api/resources/intune-gpanalyticsservice-grouppolicyobjectfile?view=graph-rest-beta) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String |  |
| groupPolicyObjectId | Guid | The Group Policy Object GUID from GPO Xml content |
| ouDistinguishedName | String | The distinguished name of the OU. |
| createdDateTime | DateTimeOffset | The date and time at which the GroupPolicy was first uploaded. |
| lastModifiedDateTime | DateTimeOffset | The date and time at which the GroupPolicyObjectFile was last modified. |
| content | String | The Group Policy Object file content. |
| roleScopeTagIds | String collection | The list of scope tags for the configuration. |

## Relationships

None

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.groupPolicyObjectFile",
  "id": "String (identifier)",
  "groupPolicyObjectId": "Guid",
  "ouDistinguishedName": "String",
  "createdDateTime": "String (timestamp)",
  "lastModifiedDateTime": "String (timestamp)",
  "content": "String",
  "roleScopeTagIds": [
    "String"
  ]
}
```
