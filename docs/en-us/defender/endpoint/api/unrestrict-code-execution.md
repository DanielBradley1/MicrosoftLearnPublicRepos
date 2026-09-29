<!-- Source: https://learn.microsoft.com/en-us/defender-endpoint/api/unrestrict-code-execution -->
<!-- Sitemap-Last-Modified: 2025-11-24 -->

# Remove app restriction API

## API description

Enable execution of any application on the device.

When isolating a device, only certain processes and destinations are allowed. Devices that are behind a full VPN tunnel won't be able to reach the Microsoft Defender for Endpoint cloud service after the device is isolated. We recommend using a split-tunneling VPN for Microsoft Defender for Endpoint and Microsoft Defender Antivirus cloud-based protection-related traffic.

## Limitations

Rate limitations for this API are 100 calls per minute and 1500 calls per hour.

## Prerequisites

### Supported operating systems

- Full isolation is available for devices on Windows 10, version 1703.
- Selective isolation is available for devices on Windows 10, version 1709 or later.

## Permissions

When obtaining a token using user credentials:

- The user needs to have at least the following role permission: 'Active remediation actions'. For more information, see: [Create and manage roles](https://learn.microsoft.com/en-us/defender-endpoint/user-roles)
- The user needs to have access to the device, based on device group settings. For more information, see: [Create and manage device groups](https://learn.microsoft.com/en-us/defender-endpoint/machine-groups)

One of the following permissions is required to call this API. To learn more, including how to choose permissions, see [Use Microsoft Defender for Endpoint APIs](https://learn.microsoft.com/en-us/defender-endpoint/api/apis-intro)

| Permission type | Permission | Permission display name |
| --- | --- | --- |
| Application | Machine.RestrictExecution | 'Restrict code execution' |
| Delegated \(work or school account\) | Machine.RestrictExecution | 'Restrict code execution' |

## HTTP request

```http
POST https://api.security.microsoft.com/api/machines/{id}/unrestrictCodeExecution
```

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

If successful, this method returns 201 - Created response code and [Machine Action](https://learn.microsoft.com/en-us/defender-endpoint/api/machineaction) in the response body.

If you send multiple API calls to remove app restrictions for the same device, it returns "pending machine action" or HTTP 400 with the message "Action is already in progress".

## Example

### Request

Here is an example of the request.

```http
POST https://api.security.microsoft.com/api/machines/1e5bc9d7e413ddd7902c2932e418702b84d0cc07/unrestrictCodeExecution
```

```json
{
  "Comment": "Unrestrict code execution since machine was cleaned and validated"
}
```
