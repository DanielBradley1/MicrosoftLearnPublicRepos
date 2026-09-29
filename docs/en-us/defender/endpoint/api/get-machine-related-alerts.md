<!-- Source: https://learn.microsoft.com/en-us/defender-endpoint/api/get-machine-related-alerts -->
<!-- Sitemap-Last-Modified: 2025-12-11 -->

# Get machine related alerts API

## API description

Retrieves all [Alerts](https://learn.microsoft.com/en-us/defender-endpoint/api/alerts) related to a specific device.

## Limitations

- You can query on devices last updated according to your configured retention period.
- Rate limitations for this API are 100 calls per minute and 1500 calls per hour.

## Permissions

When obtaining a token using user credentials:

- The user needs to have at least the following role permission: 'View Data'. For more information about permissions, see: [Create and manage roles](https://learn.microsoft.com/en-us/defender-endpoint/user-roles).
- The user needs to have access to the device, based on device group settings. For more information about device group settings, see: [Create and manage device groups](https://learn.microsoft.com/en-us/defender-endpoint/machine-groups).

| Permission type | Permission | Permission display name |
| --- | --- | --- |
| Application | Alert.ReadWrite.All | 'Read and write all alerts' |
| Delegated \(work or school account\) | Alert.ReadWrite | 'Read and write alerts' |

## HTTP request

```http
GET /api/machines/{id}/alerts
```

## Request headers

| Name | Type | Description |
| --- | --- | --- |
| Authorization | String | Bearer {token}. **Required**. |

## Request body

Empty

## Response

If successful and device exists: 200 OK with list of [alert](https://learn.microsoft.com/en-us/defender-endpoint/api/alerts) entities in the body. If device was not found: 404 Not Found.
