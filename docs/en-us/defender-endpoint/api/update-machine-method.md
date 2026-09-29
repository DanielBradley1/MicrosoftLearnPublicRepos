<!-- Source: https://learn.microsoft.com/en-us/defender-endpoint/api/update-machine-method -->
<!-- Sitemap-Last-Modified: 2025-12-11 -->

# Update machine

## API description

Updates properties of existing [Machine](https://learn.microsoft.com/en-us/defender-endpoint/api/machine).

Updatable properties are: `machineTags` and `deviceValue`.

## Limitations

- You can update machines that are available in the API.
- Update machine only appends tags to the tag collection. If tags exist, they must be included in the tags collection in the body.
- Rate limitations for this API are 100 calls per minute and 1500 calls per hour.

## Permissions

When obtaining a token using user credentials:

- The user needs to have at least the following role permission: 'Alerts investigation'. For more information, see: [Create and manage roles](https://learn.microsoft.com/en-us/defender-endpoint/user-roles).
- The user needs to have access to the device associated with the alert, based on device group settings. For more information, see: [Create and manage device groups](https://learn.microsoft.com/en-us/defender-endpoint/machine-groups).

One of the following permissions is required to call this API. To learn more, including how to choose permissions, see: [Use Microsoft Defender for Endpoint APIs](https://learn.microsoft.com/en-us/defender-endpoint/api/apis-intro)

| Permission type | Permission | Permission display name |
| --- | --- | --- |
| Application | Machine.ReadWrite.All | 'Read and write machine information for all machines' |
| Delegated \(work or school account\) | Machine.ReadWrite | 'Read and write machine information' |

## HTTP request

```http
PATCH /api/machines/{machineId}
```

## Request headers

| Name | Type | Description |
| --- | --- | --- |
| Authorization | String | Bearer {token}. **Required**. |
| Content-Type | String | application/json. **Required**. |

## Request body

In the request body, supply the values for the relevant fields that should be updated.

Existing properties that aren't included in the request body will maintain their previous values or be recalculated based on changes to other property values.

For best performance, you shouldn't include existing values that haven't change.

| Property | Type | Description |
| --- | --- | --- |
| machineTags | String collection | Set of [machine](https://learn.microsoft.com/en-us/defender-endpoint/api/machine) tags. |
| deviceValue | Nullable Enum | The [value of the device](https://learn.microsoft.com/en-us/defender-vulnerability-management/tvm-assign-device-value). Possible values are: 'Normal', 'Low' and 'High'. |

## Response

If successful, this method returns 200 OK, and the [machine](https://learn.microsoft.com/en-us/defender-endpoint/api/machine) entity in the response body with the updated properties.

If machine tags collection in body doesn't contain existing machine tags - replaces all tags with the tags provided in the request body.

If machine with the specified ID wasn't found - 404 Not Found.

## Example

### Request

Here's an example of the request.

```http
PATCH https://api.security.microsoft.com/api/machines/{machineId}
```

```json
{
    "deviceValue": "Normal",
    "machineTags": [
                     "Demo Device",
                     "Generic User Machine - Attack Source",
                     "Windows 10" "Windows11",
                     "Windows Insider - Fast"
    ]
}
```
