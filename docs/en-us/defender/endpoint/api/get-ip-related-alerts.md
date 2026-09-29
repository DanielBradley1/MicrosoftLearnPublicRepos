<!-- Source: https://learn.microsoft.com/en-us/defender-endpoint/api/get-ip-related-alerts -->
<!-- Sitemap-Last-Modified: 2025-12-11 -->

# Get IP related alerts API

## API description

Retrieves a collection of alerts related to a given IP address.

## Limitations

Rate limitations for this API are 100 calls per minute and 1,500 calls per hour.

## Permissions

When obtaining a token using user credentials:

- The user needs to have at least the following role permission: `View Data`. For more information, see [Create and manage roles](https://learn.microsoft.com/en-us/defender-endpoint/user-roles) for more information.
- Response includes only alerts, associated with devices, that the user have access to, based on device group settings \(See [Create and manage device groups](https://learn.microsoft.com/en-us/defender-endpoint/machine-groups) for more information\)

One of the following permissions is required to call this API. To learn more, including how to choose permissions, see [Use Defender for Endpoint APIs](https://learn.microsoft.com/en-us/defender-endpoint/api/apis-intro).

| Permission type | Permission | Permission display name |
| --- | --- | --- |
| Application | Alert.Read.All | `Read all alerts` |
| Application | Alert.ReadWrite.All | `Read and write all alerts` |
| Delegated \(work or school account\) | Alert.Read | `Read alerts` |
| Delegated \(work or school account\) | Alert.ReadWrite | `Read and write alerts` |

## HTTP request

```http
GET /api/ips/{ip}/alerts
```

## Request headers

| Name | Type | Description |
| --- | --- | --- |
| Authorization | String | Bearer {token}. **Required**. |

## Request body

Empty

## Response

If successful and IP exists - 200 OK with list of [alert](https://learn.microsoft.com/en-us/defender-endpoint/api/alerts) entities in the body. If IP address is unknown but valid, it returns an empty set. If the IP address is invalid, it returns HTTP 400.

## Example

### Request

Here's an example of the request.

```http
GET https://api.security.microsoft.com/api/ips/10.209.67.177/alerts
```
