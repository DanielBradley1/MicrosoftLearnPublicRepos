<!-- Source: https://learn.microsoft.com/en-us/defender-endpoint/api/get-machine-by-id -->
<!-- Sitemap-Last-Modified: 2025-12-11 -->

# Get machine by ID API

## API description

Retrieves specific [Machine](https://learn.microsoft.com/en-us/defender-endpoint/api/machine) by its device ID or computer name.

## Limitations

- You can get devices last seen according to your configured retention policy.
- Rate limitations for this API are 100 calls per minute and 1500 calls per hour.

## Permissions

When obtaining a token using user credentials:

- The user needs to have at least the following role permission: 'View Data'. For more information, see: [Create and manage roles](https://learn.microsoft.com/en-us/defender-endpoint/user-roles).
- The user needs to have access to the device, based on device group settings. For more information, see: [Create and manage device groups](https://learn.microsoft.com/en-us/defender-endpoint/machine-groups).

One of the following permissions is required to call this API. To learn more, including how to choose permissions, see [Use Microsoft Defender for Endpoint APIs](https://learn.microsoft.com/en-us/defender-endpoint/api/apis-intro)

| Permission type | Permission | Permission display name |
| --- | --- | --- |
| Application | Machine.ReadWrite.All | 'Read and write all machine information' |
| Delegated \(work or school account\) | Machine.ReadWrite | 'Read and write machine information' |

## HTTP request

```http
GET /api/machines/{id}
```

## Request headers

| Name | Type | Description |
| --- | --- | --- |
| Authorization | String | Bearer {token}. **Required**. |

## Request body

Empty

## Response

If successful and device exists - 200 OK with the [machine](https://learn.microsoft.com/en-us/defender-endpoint/api/machine) entity in the body. If machine with the specified ID wasn't found - 404 Not Found.

## Example

### Request example

Here's an example of the request.

```http
GET https://api.security.microsoft.com/api/machines/1e5bc9d7e413ddd7902c2932e418702b84d0cc07
```

### Response example

Here's an example of the response.

```http
HTTP/1.1 200 OK
Content-type: application/json
{
    "@odata.context": "https://api.security.microsoft.com/api/$metadata#Machine",
    "id": "1e5bc9d7e413ddd7902c2932e418702b84d0cc07",
    "computerDnsName": "mymachine1.contoso.com",
    "firstSeen": "2018-08-02T14:55:03.7791856Z",
    "lastSeen": "2018-08-02T14:55:03.7791856Z",
    "osPlatform": "Windows10" "Windows11",
    "version": "1709",
    "osProcessor": "x64",
    "lastIpAddress": "172.17.230.209",
    "lastExternalIpAddress": "167.220.196.71",
    "osBuild": 18209,
    "healthStatus": "Active",
    "rbacGroupId": 140,
    "rbacGroupName": "The-A-Team",
    "riskScore": "Low",
    "exposureLevel": "Medium",
    "isAadJoined": true,
    "aadDeviceId": "80fe8ff8-2624-418e-9591-41f0491218f9",
    "machineTags": [ "test tag 1", "test tag 2" ]
}
```
