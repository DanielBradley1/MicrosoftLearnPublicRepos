<!-- Source: https://learn.microsoft.com/en-us/defender-endpoint/api/get-file-related-alerts -->
<!-- Sitemap-Last-Modified: 2025-11-24 -->

# Get file-related alerts API

## API description

Retrieves a collection of alerts related to a given file hash.

## Limitations

- Rate limitations for this API are 100 calls per minute and 1500 calls per hour.
- Only SHA-1 Hash Function is supported \(not MD5 or SHA-256\).

## Permissions

When obtaining a token using user credentials:

- The user needs to have at least the following role permission: 'View Data'. For more information, see [Create and manage roles](https://learn.microsoft.com/en-us/defender-endpoint/user-roles).
- Response will include only alerts, associated with devices, that the user have access to, based on device group settings. For more information, see [Create and manage device groups](https://learn.microsoft.com/en-us/defender-endpoint/machine-groups).

One of the following permissions is required to call this API. To learn more, including how to choose permissions, see [Use Defender for Endpoint APIs](https://learn.microsoft.com/en-us/defender-endpoint/api/apis-intro)

| Permission type | Permission | Permission display name |
| --- | --- | --- |
| Application | Alert.ReadWrite.All | 'Read and write all alerts' |
| Delegated \(work or school account\) | Alert.ReadWrite | 'Read and write alerts' |

## HTTP request

```http
GET /api/files/{id}/alerts
```

## Request headers

| Name | Type | Description |
| --- | --- | --- |
| Authorization | String | Bearer {token}. **Required**. |

## Request body

Empty

## Response

If successful and file exists - 200 OK with list of [alert](https://learn.microsoft.com/en-us/defender-endpoint/api/alerts) entities in the body. If file doesn't exist - 200 OK with an empty set.

## Example

### Request

Here's an example of the request.

```http
GET https://api.security.microsoft.com/api/files/6532ec91d513acc05f43ee0aa3002599729fd3e1/alerts
```
