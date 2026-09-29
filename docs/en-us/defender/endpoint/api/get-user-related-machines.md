<!-- Source: https://learn.microsoft.com/en-us/defender-endpoint/api/get-user-related-machines -->
<!-- Sitemap-Last-Modified: 2025-11-24 -->

# Get user-related machines API

## API description

Retrieves a collection of devices related to a given user ID.

## Limitations

Rate limitations for this API are 100 calls per minute and 1,500 calls per hour.

## Permissions

When obtaining a token using user credentials:

- The user needs to have at least the following role permission: 'View Data'. For more information, see [Create and manage roles](https://learn.microsoft.com/en-us/defender-endpoint/user-roles).
- Response will include only devices that the user can access, based on device group settings. For more information, see [Create and manage device groups](https://learn.microsoft.com/en-us/defender-endpoint/machine-groups).

One of the following permissions is required to call this API. To learn more, including how to choose permissions, see [Use Microsoft Defender for Endpoint APIs](https://learn.microsoft.com/en-us/defender-endpoint/api/apis-intro)

| Permission type | Permission | Permission display name |
| --- | --- | --- |
| Application | Machine.ReadWrite.All | 'Read and write all machine information' |
| Delegated \(work or school account\) | Machine.ReadWrite | 'Read and write machine information' |

## HTTP request

```http
GET /api/users/{id}/machines
```

**The ID is not the full UPN, but only the user name. \(for example, to retrieve machines for user1@contoso.com use /api/users/user1/machines\)**

## Request headers

| Name | Type | Description |
| --- | --- | --- |
| Authorization | String | Bearer {token}. **Required**. |

## Request body

Empty

## Response

If successful and user exists - 200 OK with list of [machine](https://learn.microsoft.com/en-us/defender-endpoint/api/machine) entities in the body. If user doesn't exist - 200 OK with an empty set.

## Example

### Request

Here's an example of the request.

```http
GET https://api.security.microsoft.com/api/users/user1/machines
```
