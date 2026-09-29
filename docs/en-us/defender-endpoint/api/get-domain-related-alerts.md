<!-- Source: https://learn.microsoft.com/en-us/defender-endpoint/api/get-domain-related-alerts -->
<!-- Sitemap-Last-Modified: 2025-11-24 -->

# Get domain-related alerts API

## API description

Retrieves a collection of [Alerts](https://learn.microsoft.com/en-us/defender-endpoint/api/alerts) related to a given domain address.

## Limitations

- You can query on alerts last updated according to your configured retention period.
- Rate limitations for this API are 100 calls per minute and 1,500 calls per hour.

## Permissions

When obtaining a token using user credentials, the user needs to have at least the following role permission: `View Data`. For more information,see [Create and manage roles](https://learn.microsoft.com/en-us/defender-endpoint/user-roles).

A response includes only alerts, associated with devices, that the user has access to, based on device group settings. For more information,see [Create and manage device groups](https://learn.microsoft.com/en-us/defender-endpoint/machine-groups).

One of the following permissions is required to call this API. To learn more, including how to choose permissions, see [Use Microsoft Defender for Endpoint APIs](https://learn.microsoft.com/en-us/defender-endpoint/api/apis-intro)

| Permission type | Permission | Permission display name |
| --- | --- | --- |
| Application | Alert.ReadWrite.All | 'Read and write all alerts' |
| Delegated \(work or school account\) | Alert.ReadWrite | 'Read and write alerts' |

## HTTP request

```http
GET /api/domains/{domain}/alerts
```

## Request headers

| Header | Value |
| --- | --- |
| Authorization | String |

## Request body

Empty

## Response

If successful and domain exists - 200 OK with list of [alert](https://learn.microsoft.com/en-us/defender-endpoint/api/alerts) entities. If domain doesn't exist - 200 OK with an empty set.

## Example

### Request

Here's an example of the request.

```http
GET https://api.security.microsoft.com/api/domains/client.wns.windows.com/alerts
```
