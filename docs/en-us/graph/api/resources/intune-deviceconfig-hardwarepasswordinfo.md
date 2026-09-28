<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-hardwarepasswordinfo?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# hardwarePasswordInfo resource type

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

Intune will provide customer the ability to configure hardware/bios settings on the enrolled windows 10 Azure Active Directory joined devices. Starting from June, 2024 \(Intune Release 2406\), this type will no longer be supported and will be marked as deprecated

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List hardwarePasswordInfos](https://learn.microsoft.com/en-us/graph/api/intune-deviceconfig-hardwarepasswordinfo-list?view=graph-rest-beta) | [hardwarePasswordInfo](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-hardwarepasswordinfo?view=graph-rest-beta) collection | List properties and relationships of the [hardwarePasswordInfo](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-hardwarepasswordinfo?view=graph-rest-beta) objects. |
| [Get hardwarePasswordInfo](https://learn.microsoft.com/en-us/graph/api/intune-deviceconfig-hardwarepasswordinfo-get?view=graph-rest-beta) | [hardwarePasswordInfo](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-hardwarepasswordinfo?view=graph-rest-beta) | Read properties and relationships of the [hardwarePasswordInfo](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-hardwarepasswordinfo?view=graph-rest-beta) object. |
| [Create hardwarePasswordInfo](https://learn.microsoft.com/en-us/graph/api/intune-deviceconfig-hardwarepasswordinfo-create?view=graph-rest-beta) | [hardwarePasswordInfo](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-hardwarepasswordinfo?view=graph-rest-beta) | Create a new [hardwarePasswordInfo](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-hardwarepasswordinfo?view=graph-rest-beta) object. |
| [Delete hardwarePasswordInfo](https://learn.microsoft.com/en-us/graph/api/intune-deviceconfig-hardwarepasswordinfo-delete?view=graph-rest-beta) | None | Deletes a [hardwarePasswordInfo](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-hardwarepasswordinfo?view=graph-rest-beta). |
| [Update hardwarePasswordInfo](https://learn.microsoft.com/en-us/graph/api/intune-deviceconfig-hardwarepasswordinfo-update?view=graph-rest-beta) | [hardwarePasswordInfo](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-hardwarepasswordinfo?view=graph-rest-beta) | Update the properties of a [hardwarePasswordInfo](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-hardwarepasswordinfo?view=graph-rest-beta) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | A unique string Id that is based on associated Intune Device Id. This property is read-only. |
| serialNumber | String | Associated device's serial number . This property is read-only. |
| currentPassword | String | Current device password. This property is read-only. |
| previousPasswords | String collection | List of previous device passwords. This property is read-only. |

## Relationships

None

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.hardwarePasswordInfo",
  "id": "String (identifier)",
  "serialNumber": "String",
  "currentPassword": "String",
  "previousPasswords": [
    "String"
  ]
}
```
