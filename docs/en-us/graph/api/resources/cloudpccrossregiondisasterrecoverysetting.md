<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/cloudpccrossregiondisasterrecoverysetting?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-12-10 -->

# cloudPcCrossRegionDisasterRecoverySetting resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents the settings for cross-region disaster recovery on a Cloud PC.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| disasterRecoveryNetworkSetting | [cloudPcDisasterRecoveryNetworkSetting](https://learn.microsoft.com/en-us/graph/api/resources/cloudpcdisasterrecoverynetworksetting?view=graph-rest-beta) | Indicates the network settings of the Cloud PC during a cross-region disaster recovery operation. |
| disasterRecoveryType | [cloudPcDisasterRecoveryType](#cloudpcdisasterrecoverytype-values) | Indicates the type of disaster recovery to perform when a disaster occurs on the user's Cloud PC. The possible values are: `notConfigured`, `crossRegion`, `premium`, `unknownFutureValue`. The default value is `notConfigured`. |
| maintainCrossRegionRestorePointEnabled | Boolean | Indicates whether Windows 365 maintain the cross-region disaster recovery function generated restore points. If `true`, the Windows 365 stored restore points; `false` indicates that Windows 365 doesn't generate or keep the restore point from the original Cloud PC. If a disaster occurs, the new Cloud PC can only be provisioned using the initial image. This limitation can result in the loss of some user data on the original Cloud PC. The default value is `false`. |
| userInitiatedDisasterRecoveryAllowed | Boolean | Indicates whether the client allows the end user to initiate a disaster recovery activation. `True` indicates that the client includes the option for the end user to activate Backup Cloud PC. When `false`, the end user doesn't have the option to activate disaster recovery. The default value is `false`. Currently, only premium disaster recovery is supported. |
| crossRegionDisasterRecoveryEnabled \(deprecated\) | Boolean | `True` if an end user is allowed to set up cross-region disaster recovery for Cloud PC; otherwise, `false`. The default value is `false`. This property is deprecated and will no longer be supported effective February 11, 2025. For scenarios where **crossRegionDisasterRecoveryEnabled** is `true`, set **disasterRecoveryType** to `crossRegion`. For scenarios where **crossRegionDisasterRecoveryEnabled** is `false`, set **disasterRecoveryType** to `notconfigured`. |

### cloudPcDisasterRecoveryType values

| Value | Description |
| :--- | :--- |
| notConfigured | Default. Indicates that the administrator didn't set up the Cloud PC disaster recovery functionality. |
| crossRegion | Indicates that the administrator set up the Cloud PC cross-region disaster recovery functionality. |
| premium | Indicates that the administrator set up the Cloud PC premium disaster recovery functionality. |
| unknownFutureValue | Evolvable enumeration sentinel value. Don't use. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.cloudPcCrossRegionDisasterRecoverySetting",
  "crossRegionDisasterRecoveryEnabled": "Boolean",
  "disasterRecoveryNetworkSetting": {"@odata.type": "microsoft.graph.cloudPcDisasterRecoveryNetworkSetting"},
  "disasterRecoveryType": "String",
  "maintainCrossRegionRestorePointEnabled": "Boolean",
  "userInitiatedDisasterRecoveryAllowed": "Boolean"
}
```
