<!-- Source: https://learn.microsoft.com/en-us/defender-endpoint/api/run-av-scan -->
<!-- Sitemap-Last-Modified: 2026-06-02 -->

# Run antivirus scan API

## API description

Initiate Microsoft Defender Antivirus scan on a device.

A Microsoft Defender Antivirus scan can run alongside other antivirus solutions, whether Microsoft Defender Antivirus is the active antivirus solution or not. Microsoft Defender Antivirus can be in Passive mode. For more information, see [Microsoft Defender Antivirus compatibility](https://learn.microsoft.com/en-us/defender-endpoint/microsoft-defender-antivirus-compatibility).

## Limitations

Rate limitations for this API are 100 calls per minute and 1500 calls per hour.

## Prerequisites

### Supported operating systems

- Windows 10, version 1709 or later, and on Windows 11.
- Linux Servers. See [Supported Linux distributions](https://learn.microsoft.com/en-us/defender-endpoint/mde-linux-prerequisites#supported-linux-distributions)
- macOS. See [Prerequisites for Defender for Endpoint on macOS](https://learn.microsoft.com/en-us/defender-endpoint/microsoft-defender-endpoint-mac-prerequisites)

## Permissions

When obtaining a token using user credentials:

- The user needs to have at least the following role permission: 'Active remediation actions'. For more information, see: [Create and manage roles](https://learn.microsoft.com/en-us/defender-endpoint/user-roles).
- The user needs to have access to the device, based on device group settings. For more information, see [Create and manage device groups](https://learn.microsoft.com/en-us/defender-endpoint/machine-groups).

One of the following permissions is required to call this API. To learn more, including how to choose permissions, see [Use Microsoft Defender for Endpoint APIs](https://learn.microsoft.com/en-us/defender-endpoint/api/apis-intro)

| Permission type | Permission | Permission display name |
| --- | --- | --- |
| Application | Machine.Scan | 'Scan machine' |
| Delegated \(work or school account\) | Machine.Scan | 'Scan machine' |

## HTTP request

```http
POST https://api.security.microsoft.com/api/machines/{id}/runAntiVirusScan
```

## Request headers

| Name | Type | Description |
| --- | --- | --- |
| Authorization | String | Bearer {token}. **Required**. |
| Content-Type | string | application/json |

## Request body

In the request body, supply a JSON object with the following parameters:

| Parameter | Type | Description |
| --- | --- | --- |
| Comment | String | Comment to associate with the action. **Required**. |
| ScanType | String | Defines the type of the Scan. **Required**. |

**ScanType** controls the type of scan to perform and can be one of the following:

- **Quick**: Perform quick scan on the device
- **Full**: Perform full scan on the device

## Response

If successful, this method returns 201, Created response code and *MachineAction* object in the response body.

If you send multiple API calls to run an antivirus scan for the same device, it returns "pending machine action" or HTTP 400 with the message "Action is already in progress".

## Example

### Request

Here is an example of the request.

```http
POST https://api.security.microsoft.com/api/machines/1e5bc9d7e413ddd7902c2932e418702b84d0cc07/runAntiVirusScan
```

```json
{
  "Comment": "Check machine for viruses due to alert 3212",
  "ScanType": "Full"
}
```
