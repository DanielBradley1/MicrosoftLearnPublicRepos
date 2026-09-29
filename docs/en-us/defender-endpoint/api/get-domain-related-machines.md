<!-- Source: https://learn.microsoft.com/en-us/defender-endpoint/api/get-domain-related-machines -->
<!-- Sitemap-Last-Modified: 2025-11-24 -->

# Get domain-related machines API

## API description

Retrieves a collection of [Machines](https://learn.microsoft.com/en-us/defender-endpoint/api/machine) that have communicated to or from a given domain address.

## Limitations

- You can query on devices last updated according to your configured retention period.
- Rate limitations for this API are 100 calls per minute and 1500 calls per hour.
- Responses are limited to 500 devices in results.

## Permissions

When obtaining a token using user credentials:

- The user must have at least the following role permission: `View Data`. For more information, see [Create and manage roles](https://learn.microsoft.com/en-us/defender-endpoint/user-roles).
- Responses include only devices that the user can access, based on device group settings. For more information, see [Create and manage device groups](https://learn.microsoft.com/en-us/defender-endpoint/machine-groups).

One of the following permissions is required to call this API. To learn more, including how to choose permissions, see [Use Microsoft Defender for Endpoint APIs](https://learn.microsoft.com/en-us/defender-endpoint/api/apis-intro)

| Permission type | Permission | Permission display name |
| --- | --- | --- |
| Application | `Machine.ReadWrite.All` | `Read and write all machine information` |
| Delegated \(work or school account\) | `Machine.ReadWrite` | `Read and write machine information` |

## HTTP request

```http
GET /api/domains/{domain}/machines
```

## Request headers

| Name | Type | Description |
| --- | --- | --- |
| Authorization | String | `Bearer {token}`.  <br>**Required**. |

## Request body

Empty

## Response

If successful, and the domain exists:

- 200 OK with list of [machine](https://learn.microsoft.com/en-us/defender-endpoint/api/machine) entities

If domain doesn't exist:

- 200 OK with an empty set

## Example

### Request

Here's an example of the request.

```http
GET https://api.security.microsoft.com/api/domains/api.security.microsoft.com/machines
```
