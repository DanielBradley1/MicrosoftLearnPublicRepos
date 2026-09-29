<!-- Source: https://learn.microsoft.com/en-us/defender-endpoint/api/find-machines-by-tag -->
<!-- Sitemap-Last-Modified: 2025-11-24 -->

# Find devices by tag API

## API description

Find [Machines](https://learn.microsoft.com/en-us/defender-endpoint/api/machine) by [Tag](https://learn.microsoft.com/en-us/defender-endpoint/machine-tags).

`startswith` query is supported.

## Limitations

Rate limitations for this API are 100 calls per minute and 1,500 calls per hour.

## Permissions

When obtaining a token using user credentials:

- Responses include only devices that the user have access to based on device group settings. For more information, see: [Create and manage device groups](https://learn.microsoft.com/en-us/defender-endpoint/machine-groups).
- The user needs to have at least the following role permission: 'View Data'. For more information, see: [Create and manage roles](https://learn.microsoft.com/en-us/defender-endpoint/user-roles)
- Responses include only devices that the user have access to based on device group settings. For more information, see: [Create and manage device groups](https://learn.microsoft.com/en-us/defender-endpoint/machine-groups).

The following permission is required to call this API. To learn more, including how to choose permissions, see [Use Microsoft Defender for Endpoint APIs](https://learn.microsoft.com/en-us/defender-endpoint/api/apis-intro)

| Permission type | Permission | Permission display name |
| --- | --- | --- |
| Application | Machine.ReadWrite.All | 'Read and write all machine information' |
| Delegated \(work or school account\) | Machine.ReadWrite | 'Read and write machine information' |

## HTTP request

```http
GET /api/machines/findbytag?tag={tag}&useStartsWithFilter={true/false}
```

## Request headers

| Name | Type | Description |
| --- | --- | --- |
| Authorization | String | Bearer {token}. **Required**. |

## Request URI parameters

| Name | Type | Description |
| --- | --- | --- |
| tag | String | The tag name. **Required**. |
| useStartsWithFilter | Boolean | When set to true, the search finds all devices with tag name that starts with the given tag in the query. Defaults to false. **Optional**. |

## Request body

Empty

## Response

If successful - 200 OK with list of the machines in the response body.

## Example

### Request

Here's an example of the request.

```http
GET https://api.security.microsoft.com/api/machines/findbytag?tag=testTag&useStartsWithFilter=true
```
