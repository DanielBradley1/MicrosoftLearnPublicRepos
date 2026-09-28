<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/security-impacteddeviceasset?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-06-20 -->

# impactedDeviceAsset resource type \(deprecated\)

Namespace: microsoft.graph.security

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Important

The **impactedDeviceAsset** resource type is deprecated and will be removed on 2026-10-01. Use [entityMapping](https://learn.microsoft.com/en-us/graph/api/resources/security-entitymapping?view=graph-rest-beta) and its derived types via `alertTemplate.entityMappings` instead. See the [custom detection rule](https://learn.microsoft.com/en-us/graph/api/resources/security-detectionrule?view=graph-rest-beta) topic for the new shape.

Represents a device that was identified in an alert triggered by a [custom detection rule](https://learn.microsoft.com/en-us/graph/api/resources/security-detectionrule?view=graph-rest-beta).

Inherits from [microsoft.graph.security.impactedAsset](https://learn.microsoft.com/en-us/graph/api/resources/security-impactedasset?view=graph-rest-beta).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| identifier | [microsoft.graph.security.deviceAssetIdentifier](https://learn.microsoft.com/en-us/graph/api/resources/enums-security?view=graph-rest-beta#deviceassetidentifier-values) | Unique identifier for the impacted device asset. The possible values are: `deviceId`, `deviceName`, `remoteDeviceName`, `targetDeviceName`, `destinationDeviceName`, `unknownFutureValue`. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.security.impactedDeviceAsset",
  "identifier": "String"
}
```
