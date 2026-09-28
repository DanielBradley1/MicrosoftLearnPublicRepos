<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-gpanalyticsservice-grouppolicymigrationreport?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# groupPolicyMigrationReport resource type

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

The Group Policy migration report.

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List groupPolicyMigrationReports](https://learn.microsoft.com/en-us/graph/api/intune-gpanalyticsservice-grouppolicymigrationreport-list?view=graph-rest-beta) | [groupPolicyMigrationReport](https://learn.microsoft.com/en-us/graph/api/resources/intune-gpanalyticsservice-grouppolicymigrationreport?view=graph-rest-beta) collection | List properties and relationships of the [groupPolicyMigrationReport](https://learn.microsoft.com/en-us/graph/api/resources/intune-gpanalyticsservice-grouppolicymigrationreport?view=graph-rest-beta) objects. |
| [Get groupPolicyMigrationReport](https://learn.microsoft.com/en-us/graph/api/intune-gpanalyticsservice-grouppolicymigrationreport-get?view=graph-rest-beta) | [groupPolicyMigrationReport](https://learn.microsoft.com/en-us/graph/api/resources/intune-gpanalyticsservice-grouppolicymigrationreport?view=graph-rest-beta) | Read properties and relationships of the [groupPolicyMigrationReport](https://learn.microsoft.com/en-us/graph/api/resources/intune-gpanalyticsservice-grouppolicymigrationreport?view=graph-rest-beta) object. |
| [Create groupPolicyMigrationReport](https://learn.microsoft.com/en-us/graph/api/intune-gpanalyticsservice-grouppolicymigrationreport-create?view=graph-rest-beta) | [groupPolicyMigrationReport](https://learn.microsoft.com/en-us/graph/api/resources/intune-gpanalyticsservice-grouppolicymigrationreport?view=graph-rest-beta) | Create a new [groupPolicyMigrationReport](https://learn.microsoft.com/en-us/graph/api/resources/intune-gpanalyticsservice-grouppolicymigrationreport?view=graph-rest-beta) object. |
| [Delete groupPolicyMigrationReport](https://learn.microsoft.com/en-us/graph/api/intune-gpanalyticsservice-grouppolicymigrationreport-delete?view=graph-rest-beta) | None | Deletes a [groupPolicyMigrationReport](https://learn.microsoft.com/en-us/graph/api/resources/intune-gpanalyticsservice-grouppolicymigrationreport?view=graph-rest-beta). |
| [Update groupPolicyMigrationReport](https://learn.microsoft.com/en-us/graph/api/intune-gpanalyticsservice-grouppolicymigrationreport-update?view=graph-rest-beta) | [groupPolicyMigrationReport](https://learn.microsoft.com/en-us/graph/api/resources/intune-gpanalyticsservice-grouppolicymigrationreport?view=graph-rest-beta) | Update the properties of a [groupPolicyMigrationReport](https://learn.microsoft.com/en-us/graph/api/resources/intune-gpanalyticsservice-grouppolicymigrationreport?view=graph-rest-beta) object. |
| [createMigrationReport action](https://learn.microsoft.com/en-us/graph/api/intune-gpanalyticsservice-grouppolicymigrationreport-createmigrationreport?view=graph-rest-beta) | String |  |
| [updateScopeTags action](https://learn.microsoft.com/en-us/graph/api/intune-gpanalyticsservice-grouppolicymigrationreport-updatescopetags?view=graph-rest-beta) | String |  |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String |  |
| groupPolicyObjectId | Guid | The Group Policy Object GUID from GPO Xml content |
| displayName | String | The name of Group Policy Object from the GPO Xml Content |
| ouDistinguishedName | String | The distinguished name of the OU. |
| createdDateTime | DateTimeOffset | The date and time at which the GroupPolicyMigrationReport was created. |
| lastModifiedDateTime | DateTimeOffset | The date and time at which the GroupPolicyMigrationReport was last modified. |
| groupPolicyCreatedDateTime | DateTimeOffset | The date and time at which the GroupPolicyMigrationReport was created. |
| groupPolicyLastModifiedDateTime | DateTimeOffset | The date and time at which the GroupPolicyMigrationReport was last modified. |
| migrationReadiness | [groupPolicyMigrationReadiness](https://learn.microsoft.com/en-us/graph/api/resources/intune-gpanalyticsservice-grouppolicymigrationreadiness?view=graph-rest-beta) | The Intune coverage for the associated Group Policy Object file. Possible values are: `none`, `partial`, `complete`, `error`, `notApplicable`. |
| targetedInActiveDirectory | Boolean | The Targeted in AD property from GPO Xml Content |
| totalSettingsCount | Int32 | The total number of Group Policy Settings from GPO file. |
| supportedSettingsCount | Int32 | The number of Group Policy Settings supported by Intune. |
| supportedSettingsPercent | Int32 | The Percentage of Group Policy Settings supported by Intune. |
| roleScopeTagIds | String collection | The list of scope tags for the configuration. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| groupPolicySettingMappings | [groupPolicySettingMapping](https://learn.microsoft.com/en-us/graph/api/resources/intune-gpanalyticsservice-grouppolicysettingmapping?view=graph-rest-beta) collection | A list of group policy settings to MDM/Intune mappings. |
| unsupportedGroupPolicyExtensions | [unsupportedGroupPolicyExtension](https://learn.microsoft.com/en-us/graph/api/resources/intune-gpanalyticsservice-unsupportedgrouppolicyextension?view=graph-rest-beta) collection | A list of unsupported group policy extensions inside the Group Policy Object. |

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.groupPolicyMigrationReport",
  "id": "String (identifier)",
  "groupPolicyObjectId": "Guid",
  "displayName": "String",
  "ouDistinguishedName": "String",
  "createdDateTime": "String (timestamp)",
  "lastModifiedDateTime": "String (timestamp)",
  "groupPolicyCreatedDateTime": "String (timestamp)",
  "groupPolicyLastModifiedDateTime": "String (timestamp)",
  "migrationReadiness": "String",
  "targetedInActiveDirectory": true,
  "totalSettingsCount": 1024,
  "supportedSettingsCount": 1024,
  "supportedSettingsPercent": 1024,
  "roleScopeTagIds": [
    "String"
  ]
}
```
