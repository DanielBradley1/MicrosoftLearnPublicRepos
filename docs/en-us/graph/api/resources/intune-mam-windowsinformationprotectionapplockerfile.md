<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-windowsinformationprotectionapplockerfile?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# windowsInformationProtectionAppLockerFile resource type

Namespace: microsoft.graph

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

Windows Information Protection AppLocker File

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List windowsInformationProtectionAppLockerFiles](https://learn.microsoft.com/en-us/graph/api/intune-mam-windowsinformationprotectionapplockerfile-list?view=graph-rest-1.0) | [windowsInformationProtectionAppLockerFile](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-windowsinformationprotectionapplockerfile?view=graph-rest-1.0) collection | List properties and relationships of the [windowsInformationProtectionAppLockerFile](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-windowsinformationprotectionapplockerfile?view=graph-rest-1.0) objects. |
| [Get windowsInformationProtectionAppLockerFile](https://learn.microsoft.com/en-us/graph/api/intune-mam-windowsinformationprotectionapplockerfile-get?view=graph-rest-1.0) | [windowsInformationProtectionAppLockerFile](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-windowsinformationprotectionapplockerfile?view=graph-rest-1.0) | Read properties and relationships of the [windowsInformationProtectionAppLockerFile](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-windowsinformationprotectionapplockerfile?view=graph-rest-1.0) object. |
| [Create windowsInformationProtectionAppLockerFile](https://learn.microsoft.com/en-us/graph/api/intune-mam-windowsinformationprotectionapplockerfile-create?view=graph-rest-1.0) | [windowsInformationProtectionAppLockerFile](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-windowsinformationprotectionapplockerfile?view=graph-rest-1.0) | Create a new [windowsInformationProtectionAppLockerFile](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-windowsinformationprotectionapplockerfile?view=graph-rest-1.0) object. |
| [Delete windowsInformationProtectionAppLockerFile](https://learn.microsoft.com/en-us/graph/api/intune-mam-windowsinformationprotectionapplockerfile-delete?view=graph-rest-1.0) | None | Deletes a [windowsInformationProtectionAppLockerFile](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-windowsinformationprotectionapplockerfile?view=graph-rest-1.0). |
| [Update windowsInformationProtectionAppLockerFile](https://learn.microsoft.com/en-us/graph/api/intune-mam-windowsinformationprotectionapplockerfile-update?view=graph-rest-1.0) | [windowsInformationProtectionAppLockerFile](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-windowsinformationprotectionapplockerfile?view=graph-rest-1.0) | Update the properties of a [windowsInformationProtectionAppLockerFile](https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-windowsinformationprotectionapplockerfile?view=graph-rest-1.0) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| displayName | String | The friendly name |
| fileHash | String | SHA256 hash of the file |
| file | Binary | File as a byte array |
| id | String | Key of the entity. |
| version | String | Version of the entity. |

## Relationships

None

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.windowsInformationProtectionAppLockerFile",
  "displayName": "String",
  "fileHash": "String",
  "file": "binary",
  "id": "String (identifier)",
  "version": "String"
}
```
