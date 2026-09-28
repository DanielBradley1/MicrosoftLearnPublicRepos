<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/devicemetadata?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-07-01 -->

# deviceMetadata resource type

Namespace: microsoft.graph

Contains details about the device involved in a session, including type and OS specifications.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| deviceType | String | Optional. The general type of the device \(for example, "Managed", "Unmanaged"\). |
| operatingSystemSpecifications | [operatingSystemSpecifications](https://learn.microsoft.com/en-us/graph/api/resources/operatingsystemspecifications?view=graph-rest-1.0) | Details about the operating system platform and version. |
| ipAddress | String | The Internet Protocol \(IP\) address of the device. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.deviceMetadata",
  "deviceType": "String",
  "operatingSystemSpecifications": {
    "@odata.type": "microsoft.graph.operatingSystemSpecifications"
  },
  "ipAddress": "String"
}
```
