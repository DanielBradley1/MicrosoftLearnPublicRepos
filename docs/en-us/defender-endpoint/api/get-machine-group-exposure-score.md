<!-- Source: https://learn.microsoft.com/en-us/defender-endpoint/api/get-machine-group-exposure-score -->
<!-- Sitemap-Last-Modified: 2025-11-24 -->

# List exposure score by device group

Important

Some information in this article relates to a prereleased product which may be substantially modified before it's commercially released. Microsoft makes no warranties, expressed or implied, with respect to the information provided here.

Retrieves the exposure score for each machine group.

## Permissions

One of the following permissions is required to call this API. To learn more, including how to choose permissions, see [Use Microsoft Defender for Endpoint APIs](https://learn.microsoft.com/en-us/defender-endpoint/api/apis-intro)

| Permission type | Permission | Permission display name |
| --- | --- | --- |
| Application | Score.Read.All | 'Read Threat and Vulnerability Management score' |
| Delegated \(work or school account\) | Score.Read | 'Read Threat and Vulnerability Management score' |

## HTTP request

```http
GET /api/exposureScore/ByMachineGroups
```

## Request headers

| Name | Type | Description |
| --- | --- | --- |
| Authorization | String | Bearer {token}.**Required**. |

## Request body

Empty

## Response

If successful, this method returns 200 OK, with a list of exposure score per device group data in the response body.

## Example

### Example request

Here is an example of the request.

```http
GET https://api.security.microsoft.com/api/exposureScore/ByMachineGroups
```

### Example response

Here is an example of the response.

```json
{
    "@odata.context": "https://api.security.microsoft.com/api/$metadata#ExposureScore",
    "value": [
        {
            "time": "2019-12-03T09:51:28.214338Z",
            "score": 41.38041766305988,
            "rbacGroupName": "GroupOne"
        },
        {
            "time": "2019-12-03T09:51:28.2143399Z",
            "score": 37.403726933165366,
            "rbacGroupName": "GroupTwo"
        }
        ...
    ]
}
```
