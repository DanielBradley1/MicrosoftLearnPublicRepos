<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-windowsinformationprotectiondatarecoverycertificate?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# windowsInformationProtectionDataRecoveryCertificate resource type

Namespace: microsoft.graph

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

Windows Information Protection DataRecoveryCertificate

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| subjectName | String | Data recovery Certificate subject name |
| description | String | Data recovery Certificate description |
| expirationDateTime | DateTimeOffset | Data recovery Certificate expiration datetime |
| certificate | Binary | Data recovery Certificate |

## Relationships

None

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.windowsInformationProtectionDataRecoveryCertificate",
  "subjectName": "String",
  "description": "String",
  "expirationDateTime": "String (timestamp)",
  "certificate": "binary"
}
```
