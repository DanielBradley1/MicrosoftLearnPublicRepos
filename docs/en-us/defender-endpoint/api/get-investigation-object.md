<!-- Source: https://learn.microsoft.com/en-us/defender-endpoint/api/get-investigation-object -->
<!-- Sitemap-Last-Modified: 2025-11-24 -->

# Get Investigation API

## API description

Retrieves specific [Investigation](https://learn.microsoft.com/en-us/defender-endpoint/api/investigation) by its ID.  
ID can be the investigation ID or the investigation triggering alert ID.

## Limitations

Rate limitations for this API are 100 calls per minute and 1500 calls per hour.

## Permissions

When obtaining a token using user credentials:

- The user needs to have at least the following role permission: 'View Data'. For more information, see [Create and manage roles](https://learn.microsoft.com/en-us/defender-endpoint/user-roles).

One of the following permissions is required to call this API. TFor more information on how to choose permissions, see [Use Microsoft Defender for Endpoint APIs](https://learn.microsoft.com/en-us/defender-endpoint/api/apis-intro)

| Permission type | Permission | Permission display name |
| --- | --- | --- |
| Application | Alert.ReadWrite.All | 'Read and write all alerts' |
| Delegated \(work or school account\) | Alert.ReadWrite | 'Read and write alerts' |

## HTTP request

```http
GET https://api.security.microsoft.com/api/investigations/{id}
```

## Request headers

| Name | Type | Description |
| --- | --- | --- |
| Authorization | String | Bearer {token}. **Required**. |

## Request body

Empty

## Response

If successful, this method returns 200, Ok response code with an [Investigations](https://learn.microsoft.com/en-us/defender-endpoint/api/investigation) entity.
