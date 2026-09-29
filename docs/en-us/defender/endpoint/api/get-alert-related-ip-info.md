<!-- Source: https://learn.microsoft.com/en-us/defender-endpoint/api/get-alert-related-ip-info -->
<!-- Sitemap-Last-Modified: 2025-11-24 -->

# Get alert-related IPs' information API

## API description

Retrieves all IPs related to a specific alert.

## Limitations

- You can query on alerts last updated according to your configured retention period.
- Rate limitations for this API are 100 calls per minute and 1500 calls per hour.

## Permissions

When obtaining a token using user credentials:

- The user needs to have at least the following role permission: 'View Data'. For more information, see [Create and manage roles](https://learn.microsoft.com/en-us/defender-endpoint/user-roles)
- The user needs to have access to the device associated with the alert, based on device group settings. For more information, see [Create and manage device groups](https://learn.microsoft.com/en-us/defender-endpoint/machine-groups)

One of the following permissions is required to call this API. To learn more, including how to choose permissions, see [Use Microsoft Defender for Endpoint APIs](https://learn.microsoft.com/en-us/defender-endpoint/api/apis-intro)

| Permission type | Permission | Permission display name |
| --- | --- | --- |
| Application | Ip.Read.All | 'Read IP address profiles' |
| Delegated \(work or school account\) | Ip.Read.All | 'Read IP address profiles' |

## HTTP request

```http
GET /api/alerts/{id}/ips
```

## Request headers

| Name | Type | Description |
| --- | --- | --- |
| Authorization | String | Bearer {token}. **Required**. |

## Request body

Empty

## Response

If successful and alert and an IP exist - 200 OK. If alert not found - 404 Not Found.

## Example

### Request example

Here's an example of the request.

```http
GET https://api.security.microsoft.com/alerts/636688558380765161_2136280442/ips
```

### Response example

Here's an example of the response.

```json
{
    "@odata.context": "https://api.security.microsoft.com/$metadata#Ips",
    "value": [
                {
                    "id": "104.80.104.128"
                },
                {
                    "id": "23.203.232.228
                }
                ...
    ]
}
```
