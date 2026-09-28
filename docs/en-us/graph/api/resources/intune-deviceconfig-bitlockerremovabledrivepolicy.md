<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-bitlockerremovabledrivepolicy?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# bitLockerRemovableDrivePolicy resource type

Namespace: microsoft.graph

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

BitLocker Removable Drive Policies.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| encryptionMethod | [bitLockerEncryptionMethod](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-bitlockerencryptionmethod?view=graph-rest-1.0) | Select the encryption method for removable drives. The possible values are: `aesCbc128`, `aesCbc256`, `xtsAes128`, `xtsAes256`. |
| requireEncryptionForWriteAccess | Boolean | Indicates whether to block write access to devices configured in another organization. If requireEncryptionForWriteAccess is false, this value does not affect. |
| blockCrossOrganizationWriteAccess | Boolean | This policy setting determines whether BitLocker protection is required for removable data drives to be writable on a computer. |

## Relationships

None

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.bitLockerRemovableDrivePolicy",
  "encryptionMethod": "String",
  "requireEncryptionForWriteAccess": true,
  "blockCrossOrganizationWriteAccess": true
}
```
