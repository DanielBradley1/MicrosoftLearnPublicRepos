<!-- Source: https://learn.microsoft.com/en-us/defender-endpoint/api/machine -->
<!-- Sitemap-Last-Modified: 2025-12-11 -->

# Machine resource type

Important

Some information in this article relates to a prereleased product which may be substantially modified before it's commercially released. Microsoft makes no warranties, expressed or implied, with respect to the information provided here.

## Properties

| Property | Type | Description |
| --- | --- | --- |
| id | String | [machine](https://learn.microsoft.com/en-us/defender-endpoint/api/machine) identity. |
| computerDnsName | String | [machine](https://learn.microsoft.com/en-us/defender-endpoint/api/machine) fully qualified name. |
| firstSeen | DateTimeOffset | First date and time where the [machine](https://learn.microsoft.com/en-us/defender-endpoint/api/machine) was observed by Microsoft Defender for Endpoint. |
| lastSeen | DateTimeOffset | Time and date of the last received full device report. A device typically sends a full report every 24 hours.  <br>NOTE: This property doesn't correspond to the last seen value in the UI. It pertains to the last device update. |
| osPlatform | String | Operating system platform. |
| onboardingstatus | String | Status of machine onboarding. Possible values are: `onboarded`, `CanBeOnboarded`, `Unsupported`, and `InsufficientInfo`. |
| osProcessor | String | Operating system processor. Use osArchitecture property instead. |
| version | String | Operating system Version. |
| osBuild | Nullable long | Operating system build number. |
| lastIpAddress | String | Last IP on local NIC on the [machine](https://learn.microsoft.com/en-us/defender-endpoint/api/machine). |
| lastExternalIpAddress | String | Last IP through which the [machine](https://learn.microsoft.com/en-us/defender-endpoint/api/machine) accessed the internet. |
| healthStatus | Enum | [machine](https://learn.microsoft.com/en-us/defender-endpoint/api/machine) health status. Possible values are: `Active`, `Inactive`, `ImpairedCommunication`, `NoSensorData`, `NoSensorDataImpairedCommunication`, and `Unknown`. |
| rbacGroupName | String | Machine group Name. |
| rbacGroupId | String | Machine group ID. |
| riskScore | Nullable Enum | Risk score as evaluated by Microsoft Defender for Endpoint. Possible values are: `None`, `Informational`, `Low`, `Medium`, and `High`. |
| aadDeviceId | Nullable representation Guid | Microsoft Entra Device ID \(when [machine](https://learn.microsoft.com/en-us/defender-endpoint/api/machine) is Microsoft Entra joined\). |
| machineTags | String collection | Set of [machine](https://learn.microsoft.com/en-us/defender-endpoint/api/machine) tags. |
| exposureLevel | Nullable Enum | Exposure level as evaluated by Microsoft Defender for Endpoint. Possible values are: `None`, `Low`, `Medium`, and `High`. |
| deviceValue | Nullable Enum | The [value of the device](https://learn.microsoft.com/en-us/defender-vulnerability-management/tvm-assign-device-value). Possible values are: `Normal`, `Low`, and `High`. |
| ipAddresses | IpAddress collection | Set of ***IpAddress*** objects. See [Get machines API](https://learn.microsoft.com/en-us/defender-endpoint/api/get-machines). |
| osArchitecture | String | Operating system architecture. Possible values are: `32-bit`, `64-bit`. Use this property instead of osProcessor. |
