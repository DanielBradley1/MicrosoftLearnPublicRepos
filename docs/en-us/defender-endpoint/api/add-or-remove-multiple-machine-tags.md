<!-- Source: https://learn.microsoft.com/en-us/defender-endpoint/api/add-or-remove-multiple-machine-tags -->
<!-- Sitemap-Last-Modified: 2026-01-08 -->

# Add or remove a tag for multiple machines

## API description

Adds or removes a tag for the specified set of machines.

## Limitations

- You can post on machines last seen according to your configured retention period.
- Rate limitations for this API are 100 calls per minute and 1,500 calls per hour.
- We can add or remove a tag for up to 500 machines per API call.

## Permissions

When obtaining a token using user credentials:

- The user needs to have at least the following role permission: 'Manage security setting'. For more information, see: [Create and manage roles](https://learn.microsoft.com/en-us/defender-endpoint/user-roles).
- The user needs to have access to the machine, based on machine group settings. For more information, see: [Create and manage machine groups](https://learn.microsoft.com/en-us/defender-endpoint/machine-groups).

One of the following permissions is required to call this API. To learn more, including how to choose permissions, see [Use Defender for Endpoint APIs](https://learn.microsoft.com/en-us/defender-endpoint/api/apis-intro).

| Permission type | Permission | Permission display name |
| --- | --- | --- |
| Application | Machine.ReadWrite.All | 'Read and write all machine information' |
| Delegated \(work or school account\) | Machine.ReadWrite | 'Read and write machine information' |

## HTTP request

```http
POST https://api.security.microsoft.com/api/machines/AddOrRemoveTagForMultipleMachines
```

Tip

For better performance, instead of using api.security.microsoft.com, use a server closer to your geolocation:

- us.api.security.microsoft.com
- eu.api.security.microsoft.com
- uk.api.security.microsoft.com
- au.api.security.microsoft.com
- swa.api.security.microsoft.com
- ina.api.security.microsoft.com
- aea.api.security.microsoft.com

## Request headers

| Name | Type | Description |
| --- | --- | --- |
| Authorization | String | Bearer {token}. **Required**. |
| Content-Type | string | application/json. **Required**. |

## Request body

In the request body, supply a JSON object with the following parameters:

| Parameter | Type | Description |
| --- | --- | --- |
| Value | String | The tag name. **Required**. |
| Action | Enum | Add or Remove. Allowed values are: 'Add' or 'Remove'. **Required**. |
| MachineIds | List \(String\) | List of machine IDs to update. Required. |

## Response

If successful, this method returns 200 - Ok response code and the updated machines in the response body.

## Example Request

To remove machine tags, set the Action to 'Remove' instead of 'Add' in the request body.

Here's an example of a request that adds a tag to multiple machines.

```http
POST https://api.security.microsoft.com/api/machines/AddOrRemoveTagForMultipleMachines
```

```json
{
  "Value" : "Tag",
  "Action": "Add",
  "MachineIds": ["34e83ca3feea4dae2353006ba389262c033a025e",
  "2a398439b4975924e87a65943972bc702469b329",
  "a610c00c65fdf79960cc0077d9d8c569d23f09a5"]
}
```
