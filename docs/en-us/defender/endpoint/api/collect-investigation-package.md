<!-- Source: https://learn.microsoft.com/en-us/defender-endpoint/api/collect-investigation-package -->
<!-- Sitemap-Last-Modified: 2025-11-24 -->

# Collect investigation package API

## API description

Collect investigation package from a device.

## Limitations

- Rate limitations for this API are 100 calls per minute and 1500 calls per hour.

## Permissions

When obtaining a token using user credentials:

- The user needs to have at least the following role permission: 'Alerts Investigation'. For more information, see: [Create and manage roles](https://learn.microsoft.com/en-us/defender-endpoint/user-roles)
- The user needs to have access to the device, based on device group settings. For more information, see: [Create and manage device groups](https://learn.microsoft.com/en-us/defender-endpoint/machine-groups)

One of the following permissions is required to call this API. To learn more, including how to choose permissions, see [Use Defender for Endpoint APIs](https://learn.microsoft.com/en-us/defender-endpoint/api/apis-intro)

| Permission type | Permission | Permission display name |
| --- | --- | --- |
| Application | Machine.CollectForensics | 'Collect forensics' |
| Delegated \(work or school account\) | Machine.CollectForensics | 'Collect forensics' |

## HTTP request

```http
POST https://api.security.microsoft.com/api/machines/{id}/collectInvestigationPackage
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

If successful, this method returns 201 - Created response code and [Machine Action](https://learn.microsoft.com/en-us/defender-endpoint/api/machineaction) in the response body. If a collection is already running, this returns 400 Bad Request.

## Example

### Request

Here is an example of the request.

```http
POST https://api.security.microsoft.com/api/machines/fb9ab6be3965095a09c057be7c90f0a2/collectInvestigationPackage
```

```json
{
  "Comment": "Collect forensics due to alert 1234"
}
```
