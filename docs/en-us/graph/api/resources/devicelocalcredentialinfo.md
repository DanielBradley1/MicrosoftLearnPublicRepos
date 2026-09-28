<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/devicelocalcredentialinfo?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-05-24 -->

# deviceLocalCredentialInfo resource type

Namespace: microsoft.graph

Represents local administrator credential information for all device objects in Azure Active Directory that are enabled with Local Admin Password Solution \(LAPS\).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List](https://learn.microsoft.com/en-us/graph/api/directory-list-devicelocalcredentials?view=graph-rest-1.0) | [deviceLocalCredentialInfo](https://learn.microsoft.com/en-us/graph/api/resources/devicelocalcredentialinfo?view=graph-rest-1.0) collection | Get a list of the [deviceLocalCredentials](https://learn.microsoft.com/en-us/graph/api/resources/devicelocalcredential?view=graph-rest-1.0) objects and their properties. |
| [Get](https://learn.microsoft.com/en-us/graph/api/devicelocalcredentialinfo-get?view=graph-rest-1.0) | [deviceLocalCredentialInfo](https://learn.microsoft.com/en-us/graph/api/resources/devicelocalcredentialinfo?view=graph-rest-1.0) | Retrieve the properties and relationships of a [deviceLocalCredentialInfo](https://learn.microsoft.com/en-us/graph/api/resources/devicelocalcredentialinfo?view=graph-rest-1.0) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| credentials | [deviceLocalCredential](https://learn.microsoft.com/en-us/graph/api/resources/devicelocalcredential?view=graph-rest-1.0) collection | The credentials of the device's local administrator account backed up to Azure Active Directory. |
| deviceName | String | Display name of the device that the local credentials are associated with. |
| id | String | ID of the device that the local credentials are associated with Key. This is same as **deviceId** in the [device](https://learn.microsoft.com/en-us/graph/api/resources/device?view=graph-rest-1.0) object. |
| lastBackupDateTime | DateTimeOffset | When the local administrator account credential was backed up to Azure Active Directory. |
| refreshDateTime | DateTimeOffset | When the local administrator account credential will be refreshed and backed up to Azure Active Directory. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.deviceLocalCredentialInfo",
  "id": "String (identifier)",
  "deviceName": "String",
  "lastBackupDateTime": "String (timestamp)",
  "refreshDateTime": "String (timestamp)",
  "credentials": [
    {
      "@odata.type": "microsoft.graph.deviceLocalCredential"
    }
  ]
}
```
