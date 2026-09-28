<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-onboarding-mobilethreatdefenseconnector?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-10-11 -->

# mobileThreatDefenseConnector resource type

Namespace: microsoft.graph

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

Entity which represents a connection to Mobile Threat Defense partner.

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List mobileThreatDefenseConnectors](https://learn.microsoft.com/en-us/graph/api/intune-onboarding-mobilethreatdefenseconnector-list?view=graph-rest-1.0) | [mobileThreatDefenseConnector](https://learn.microsoft.com/en-us/graph/api/resources/intune-onboarding-mobilethreatdefenseconnector?view=graph-rest-1.0) collection | List properties and relationships of the [mobileThreatDefenseConnector](https://learn.microsoft.com/en-us/graph/api/resources/intune-onboarding-mobilethreatdefenseconnector?view=graph-rest-1.0) objects. |
| [Get mobileThreatDefenseConnector](https://learn.microsoft.com/en-us/graph/api/intune-onboarding-mobilethreatdefenseconnector-get?view=graph-rest-1.0) | [mobileThreatDefenseConnector](https://learn.microsoft.com/en-us/graph/api/resources/intune-onboarding-mobilethreatdefenseconnector?view=graph-rest-1.0) | Read properties and relationships of the [mobileThreatDefenseConnector](https://learn.microsoft.com/en-us/graph/api/resources/intune-onboarding-mobilethreatdefenseconnector?view=graph-rest-1.0) object. |
| [Create mobileThreatDefenseConnector](https://learn.microsoft.com/en-us/graph/api/intune-onboarding-mobilethreatdefenseconnector-create?view=graph-rest-1.0) | [mobileThreatDefenseConnector](https://learn.microsoft.com/en-us/graph/api/resources/intune-onboarding-mobilethreatdefenseconnector?view=graph-rest-1.0) | Create a new [mobileThreatDefenseConnector](https://learn.microsoft.com/en-us/graph/api/resources/intune-onboarding-mobilethreatdefenseconnector?view=graph-rest-1.0) object. |
| [Delete mobileThreatDefenseConnector](https://learn.microsoft.com/en-us/graph/api/intune-onboarding-mobilethreatdefenseconnector-delete?view=graph-rest-1.0) | None | Deletes a [mobileThreatDefenseConnector](https://learn.microsoft.com/en-us/graph/api/resources/intune-onboarding-mobilethreatdefenseconnector?view=graph-rest-1.0). |
| [Update mobileThreatDefenseConnector](https://learn.microsoft.com/en-us/graph/api/intune-onboarding-mobilethreatdefenseconnector-update?view=graph-rest-1.0) | [mobileThreatDefenseConnector](https://learn.microsoft.com/en-us/graph/api/resources/intune-onboarding-mobilethreatdefenseconnector?view=graph-rest-1.0) | Update the properties of a [mobileThreatDefenseConnector](https://learn.microsoft.com/en-us/graph/api/resources/intune-onboarding-mobilethreatdefenseconnector?view=graph-rest-1.0) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String |  |
| lastHeartbeatDateTime | DateTimeOffset | DateTime of last Heartbeat recieved from the Mobile Threat Defense partner |
| partnerState | [mobileThreatPartnerTenantState](https://learn.microsoft.com/en-us/graph/api/resources/intune-onboarding-mobilethreatpartnertenantstate?view=graph-rest-1.0) | Mobile Threat Defense partner state for this account. The possible values are: `unavailable`, `available`, `enabled`, `unresponsive`, `notSetUp`, `error`, `unknownFutureValue`. |
| androidMobileApplicationManagementEnabled | Boolean | When TRUE, inidicates that data from the Mobile Threat Defense partner can be used during Mobile Application Management \(MAM\) evaluations for Android devices. When FALSE, inidicates that data from the Mobile Threat Defense partner should not be used during Mobile Application Management \(MAM\) evaluations for Android devices. Only one partner per platform may be enabled for Mobile Application Management \(MAM\) evaluation. Default value is FALSE. |
| iosMobileApplicationManagementEnabled | Boolean | When TRUE, inidicates that data from the Mobile Threat Defense partner can be used during Mobile Application Management \(MAM\) evaluations for iOS devices. When FALSE, inidicates that data from the Mobile Threat Defense partner should not be used during Mobile Application Management \(MAM\) evaluations for iOS devices. Only one partner per platform may be enabled for Mobile Application Management \(MAM\) evaluation. Default value is FALSE. |
| androidEnabled | Boolean | When TRUE, indicates that data from the Mobile Threat Defense partner will be used during compliance evaluations for Android devices. When FALSE, indicates that data from the Mobile Threat Defense partner will not be used during compliance evaluations for Android devices. Default value is FALSE. |
| iosEnabled | Boolean | When TRUE, indicates that data from the Mobile Threat Defense partner will be used during compliance evaluations for iOS devices. When FALSE, indicates that data from the Mobile Threat Defense partner will not be used during compliance evaluations for iOS devices. Default value is FALSE. |
| windowsEnabled | Boolean | When TRUE, indicates that data from the Mobile Threat Defense partner will be used during compliance evaluations for Windows. When FALSE, indicates that data from the Mobile Threat Defense partner will not be used during compliance evaluations for Windows. Default value is FALSE. |
| androidDeviceBlockedOnMissingPartnerData | Boolean | When TRUE, indicates that Intune must receive data from the Mobile Threat Defense partner prior to marking an Android device compliant. When FALSE, indicates that Intune may mark an Android device compliant before receiving data from the Mobile Threat Defense partner. |
| iosDeviceBlockedOnMissingPartnerData | Boolean | When TRUE, indicates that Intune must receive data from the Mobile Threat Defense partner prior to marking a device compliant. When FALSE, indicates that Intune may not recieve data from Mobile Threat Defense partner prior to making device compliant. Default value is FALSE. |
| windowsDeviceBlockedOnMissingPartnerData | Boolean | When TRUE, indicates that Intune must receive data from the data sync partner prior to marking a device compliant for Windows. When FALSE, indicates that Intune may mark a device compliant without receiving data from the data sync partner for Windows. Default value is FALSE. |
| partnerUnsupportedOsVersionBlocked | Boolean | When TRUE, indicates that Intune will mark devices noncompliant on enabled platforms that do not meet the minimum version requirements of the Mobile Threat Defense partner. When FALSE, indicates that Intune will not mark devices noncompliant on enabled platforms that do not meet the minimum version requirements of the Mobile Threat Defense partner. Default value is FALSE. |
| partnerUnresponsivenessThresholdInDays | Int32 | Indicates the number of days without receiving a heartbeat from a Mobile Threat Defense partner before the partner is marked as unresponsive. Intune will the ignore the data from this Mobile Threat Defense Partner for next compliance calculation. |
| allowPartnerToCollectIOSApplicationMetadata | Boolean | When TRUE, indicates the Mobile Threat Defense partner may collect metadata about installed applications from Intune for iOS devices. When FALSE, indicates the Mobile Threat Defense partner may not collect metadata about installed applications from Intune for iOS devices. Default value is FALSE. |
| allowPartnerToCollectIOSPersonalApplicationMetadata | Boolean | When TRUE, indicates the Mobile Threat Defense partner may collect metadata about personally installed applications from Intune for iOS devices. When FALSE, indicates the Mobile Threat Defense partner may not collect metadata about personally installed applications from Intune for iOS devices. Default value is FALSE. |
| microsoftDefenderForEndpointAttachEnabled | Boolean | When TRUE, inidicates that configuration profile management via Microsoft Defender for Endpoint is enabled. When FALSE, inidicates that configuration profile management via Microsoft Defender for Endpoint is disabled. Default value is FALSE. |

## Relationships

None

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.mobileThreatDefenseConnector",
  "id": "String (identifier)",
  "lastHeartbeatDateTime": "String (timestamp)",
  "partnerState": "String",
  "androidMobileApplicationManagementEnabled": true,
  "iosMobileApplicationManagementEnabled": true,
  "androidEnabled": true,
  "iosEnabled": true,
  "windowsEnabled": true,
  "androidDeviceBlockedOnMissingPartnerData": true,
  "iosDeviceBlockedOnMissingPartnerData": true,
  "windowsDeviceBlockedOnMissingPartnerData": true,
  "partnerUnsupportedOsVersionBlocked": true,
  "partnerUnresponsivenessThresholdInDays": 1024,
  "allowPartnerToCollectIOSApplicationMetadata": true,
  "allowPartnerToCollectIOSPersonalApplicationMetadata": true,
  "microsoftDefenderForEndpointAttachEnabled": true
}
```
