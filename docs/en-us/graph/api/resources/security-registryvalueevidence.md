<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/security-registryvalueevidence?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-07-23 -->

# registryValueEvidence resource type

Namespace: microsoft.graph.security

A registry value that is reported in the alert as evidence.

Inherits from [alertEvidence](https://learn.microsoft.com/en-us/graph/api/resources/security-alertevidence?view=graph-rest-1.0).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| mdeDeviceId | String | A unique identifier assigned to a device by Microsoft Defender for Endpoint. |
| registryHive | String | Registry hive of the key that the recorded action was applied to. |
| registryKey | String | Registry key that the recorded action was applied to. |
| registryValue | String | Data of the registry value that the recorded action was applied to. |
| registryValueName | String | Name of the registry value that the recorded action was applied to. |
| registryValueType | String | Data type, such as binary or string, of the registry value that the recorded action was applied to. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.security.registryValueEvidence",
  "createdDateTime": "String (timestamp)",
  "verdict": "String",
  "remediationStatus": "String",
  "remediationStatusDetails": "String",
  "roles": [
    "String"
  ],
  "detailedRoles": [
    "String"
  ],
  "tags": [
    "String"
  ],
  "mdeDeviceId": "String",
  "registryKey": "String",
  "registryHive": "String",
  "registryValue": "String",
  "registryValueName": "String",
  "registryValueType": "String"
}
```
