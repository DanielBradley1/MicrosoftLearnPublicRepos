<!-- Source: https://learn.microsoft.com/en-us/defender-endpoint/api/get-alert-info-by-id -->
<!-- Sitemap-Last-Modified: 2025-11-24 -->

# Get alert information by ID API

## API description

Retrieves specific [Alert](https://learn.microsoft.com/en-us/defender-endpoint/api/alerts) by its ID.

## Limitations

- You can get alerts last updated according to your configured retention period.
- Rate limitations for this API are 100 calls per minute and 1500 calls per hour.

## Permissions

When obtaining a token using user credentials:

- The user needs to have at least the following role permission: 'View Data'. For more information, see [Create and manage roles](https://learn.microsoft.com/en-us/defender-endpoint/user-roles).
- The user needs to have access to the device associated with the alert, based on device group settings. For more information, see [Create and manage device groups](https://learn.microsoft.com/en-us/defender-endpoint/machine-groups).

One of the following permissions is required to call this API. To learn more, including how to choose permissions, see [Use Microsoft Defender for Endpoint APIs](https://learn.microsoft.com/en-us/defender-endpoint/api/apis-intro).

| Permission type | Permission | Permission display name |
| --- | --- | --- |
| Application | Alert.ReadWrite.All | 'Read and write all alerts' |
| Delegated \(work or school account\) | Alert.ReadWrite | 'Read and write alerts' |

## HTTP request

```http
GET /api/alerts/{id}
```

## Request headers

| Name | Type | Description |
| --- | --- | --- |
| Authorization | String | Bearer {token}. **Required**. |

## Request body

Empty

## Response

If successful, this method returns 200 OK, and the [alert](https://learn.microsoft.com/en-us/defender-endpoint/api/alerts) entity in the response body. If an alert with the specified ID wasn't found - 404 Not Found.
