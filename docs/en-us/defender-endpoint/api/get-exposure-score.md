<!-- Source: https://learn.microsoft.com/en-us/defender-endpoint/api/get-exposure-score -->
<!-- Sitemap-Last-Modified: 2025-11-24 -->

# Get exposure score

Important

Some information in this article relates to a prereleased product which may be substantially modified before it's commercially released. Microsoft makes no warranties, expressed or implied, with respect to the information provided here.

Retrieves the organizational exposure score.

## Permissions

One of the following permissions is required to call this API. To learn more, including how to choose permissions, see [Use Microsoft Defender for Endpoint APIs](https://learn.microsoft.com/en-us/defender-endpoint/api/apis-intro)

| Permission type | Permission | Permission display name |
| --- | --- | --- |
| Application | Score.Read.All | 'Read Threat and Vulnerability Management score' |
| Delegated \(work or school account\) | Score.Read | 'Read Threat and Vulnerability Management score' |

## HTTP request

```http
GET /api/exposureScore
```

## Request headers

| Name | Type | Description |
| --- | --- | --- |
| Authorization | String | Bearer {token}. **Required**. |

## Request body

Empty

## Response

If successful, this method returns 200 OK, with the exposure data in the response body.

## Example

### Request

Here is an example of the request.

```http
GET https://api.security.microsoft.com/api/exposureScore
```

### Response

Here's an example of a shortened response list.

```json
{
    "@odata.context": "https://api.security.microsoft.com/api/$metadata#ExposureScore/$entity",
    "time": "2019-12-03T07:23:53.280499Z",
    "score": 33.491554051195706
}
```
