<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-managementstate?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-10-11 -->

# managementState enum type

Namespace: microsoft.graph

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

Management state of device in Microsoft Intune.

## Members

| Member | Value | Description |
| :--- | :--- | :--- |
| managed | 0 | The device is under management |
| retirePending | 1 | A retire command is occuring on the device and in the process of unenrolling from management |
| retireFailed | 2 | Retire command failed on the device |
| wipePending | 3 | A wipe command is occuring on the device and in the process of unenrolling from management |
| wipeFailed | 4 | Wipe command failed on the device |
| unhealthy | 5 | The device is unhealthy. |
| deletePending | 6 | A delete command is occuring on the device |
| retireIssued | 7 | A retire command was issued for the device |
| wipeIssued | 8 | A wipe command was issued for the device |
| wipeCanceled | 9 | A wipe command for this device has been canceled |
| retireCanceled | 10 | A retire command for this device has been canceled |
| discovered | 11 | The device is discovered but not fully enrolled. |
| unknownFutureValue | 12 | Evolvable enumeration sentinel value. Do not use. |
