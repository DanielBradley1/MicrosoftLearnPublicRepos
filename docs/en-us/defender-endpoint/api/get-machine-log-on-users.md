<!-- Source: https://learn.microsoft.com/en-us/defender-endpoint/api/get-machine-log-on-users -->
<!-- Sitemap-Last-Modified: 2025-12-11 -->

# Get machine logon users API

## API description

Retrieves a collection of logged on users on a specific device.

## Limitations

- You can query on alerts last updated according to your configured retention period.
- Rate limitations for this API are 100 calls per minute and 1500 calls per hour.

## Permissions

When obtaining a token using user credentials:

- The user needs to have at least the following role permission: 'View Data'. For more information, see: [Create and manage roles](https://learn.microsoft.com/en-us/defender-endpoint/user-roles).
- Response will include users only if the device is visible to the user, based on device group settings. For more information, see: [Create and manage device groups](https://learn.microsoft.com/en-us/defender-endpoint/machine-groups).

One of the following permissions is required to call this API. To learn more, including how to choose permissions, see [Use Microsoft Defender for Endpoint APIs](https://learn.microsoft.com/en-us/defender-endpoint/api/apis-intro)

| Permission type | Permission | Permission display name |
| --- | --- | --- |
| Application | User.Read.All | 'Read user profiles' |
| Delegated \(work or school account\) | User.Read.All | 'Read user profiles' |

## HTTP request

```http
GET /api/machines/{id}/logonusers
```

## Request headers

| Name | Type | Description |
| --- | --- | --- |
| Authorization | String | Bearer {token}. **Required**. |

## Request body

Empty

## Response

If successful and device exists - 200 OK with list of [user](https://learn.microsoft.com/en-us/defender-endpoint/api/user) entities in the body. If device wasn't found - 404 Not Found.

## Example

### Request

Here's an example of the request.

```http
GET https://api.security.microsoft.com/api/machines/1e5bc9d7e413ddd7902c2932e418702b84d0cc07/logonusers
```

### Response

Here's an example of the response.

```http
HTTP/1.1 200 OK
Content-type: application/json
{
    "@odata.context": "https://api.security.microsoft.com/api/$metadata#Users",
    "value": [
        {
            "id": "contoso\\user1",
            "accountName": "user1",
            "accountDomain": "contoso",
            "firstSeen": "2019-12-18T08:02:54Z",
            "lastSeen": "2020-01-06T08:01:48Z",
            "logonTypes": "Interactive",
            "isDomainAdmin": true,
            "isOnlyNetworkUser": false
        },
        ...
    ]
}
```
