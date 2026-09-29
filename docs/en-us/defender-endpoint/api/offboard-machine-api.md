<!-- Source: https://learn.microsoft.com/en-us/defender-endpoint/api/offboard-machine-api -->
<!-- Sitemap-Last-Modified: 2026-08-12 -->

# Offboard machine API

## API description

Offboard device from Defender for Endpoint.

## Prerequisites

### Supported operating systems

| Operating system | Supported versions |
| --- | --- |
| Windows client | Windows 11 and Windows 10, version 1703 and later |
| Windows Server | Windows Server 2019 and later; Windows Server 2012 R2 and Windows Server 2016 when using the [new, unified agent for Defender for Endpoint](https://learn.microsoft.com/en-us/defender-endpoint/update-agent-mma-windows#upgrade-to-the-new-agent-for-defender-for-endpoint) |
| macOS | [macOS 14 and later](https://learn.microsoft.com/en-us/defender-endpoint/microsoft-defender-endpoint-releases#macos-releases) |
| Linux | [Supported Linux distributions](https://learn.microsoft.com/en-us/defender-endpoint/mde-linux-prerequisites#supported-linux-distributions) |

## Limitations

- Rate limitations for this API are 100 calls per minute and 1,500 calls per hour.
- On Windows devices, running the offboarding API only stops the sensor service. It doesn't remove the onboarding information from the registry like an offboarding script does.

## Permissions

Microsoft recommends that you use roles with the fewest permissions. This helps improve security for your organization. Global Administrator is a highly privileged role that should be limited to emergency scenarios when you can't use an existing role.

When obtaining a token using user credentials:

- The user must have an appropriate role assigned. For more information, see: [Permission options](https://learn.microsoft.com/en-us/defender-endpoint/user-roles#permission-options).
- The user must have access to the device, based on device group settings. For more information, see: [Create and manage device groups](https://learn.microsoft.com/en-us/defender-endpoint/machine-groups).

One of the following permissions is required to call this API. To learn more, including how to choose permissions, see [Use Defender for Endpoint APIs](https://learn.microsoft.com/en-us/defender-endpoint/api/apis-intro)

| Permission type | Permission | Permission display name |
| --- | --- | --- |
| Application | `Machine.Offboard` | `Offboard machine` |
| Delegated \(work or school account\) | `Machine.Offboard` | `Offboard machine` |

## HTTP request

```http
POST https://api.security.microsoft.com/api/machines/{id}/offboard
```

The machine ID can be found in the URL when you select the device. Generally, it's a 40 digit alphanumeric number that can be found in the URL.

## Request headers

| Name | Type | Description |
| --- | --- | --- |
| Authorization | String | Bearer {token}. **Required**. |
| Content-Type | string | application/json. **Required**. |

## Request body

In the request body, supply a JSON object with the following parameters:

| Parameter | Type | Description |
| --- | --- | --- |
| Comment | String | Comment to associate with the action. **Required**. |

## Response

If successful, this method returns `200 - Created response` code and [Machine Action](https://learn.microsoft.com/en-us/defender-endpoint/api/machineaction) in the response body.

## Example

### Request

Here's an example of the request. If there's no JSON comment added, it errors out with code `400`.

```http
POST https://api.security.microsoft.com/api/machines/1e5bc9d7e413ddd7902c2932e418702b84d0cc07/offboard
```

```json
{
  "Comment": "Offboard machine by automation"
}
```
