<!-- Source: https://learn.microsoft.com/en-us/defender-endpoint/api/get-device-secure-score -->
<!-- Sitemap-Last-Modified: 2025-11-24 -->

# Get device secure score

Retrieves your [Microsoft Secure Score for Devices](https://learn.microsoft.com/en-us/defender-vulnerability-management/tvm-microsoft-secure-score-devices). A higher Microsoft Secure Score for Devices means your endpoints are more resilient from cybersecurity threat attacks.

## Permissions

One of the following permissions is required to call this API. To learn more, including how to choose permissions, see [Use Microsoft Defender for Endpoint APIs](https://learn.microsoft.com/en-us/defender-endpoint/api/apis-intro) for details.

| Permission type | Permission | Permission display name |
| --- | --- | --- |
| Application | Score.Read.All | 'Read Threat and Vulnerability Management score' |
| Delegated \(work or school account\) | Score.Read | 'Read Threat and Vulnerability Management score' |

## HTTP request

```http
GET /api/configurationScore
```

## Request headers

| Name | Type | Description |
| --- | --- | --- |
| Authorization | String | Bearer {token}. **Required**. |

## Request body

Empty

## Response

If successful, this method returns 200 OK, with the device secure score data in the response body.

## Example

### Request example

Here is an example of the request.

```http
GET https://api.security.microsoft.com/api/configurationScore
```

### Response example

Here's an example of the shortned response list.

```json
{
    "@odata.context": "https://api.security.microsoft.com/api/$metadata#ConfigurationScore/$entity",
    "time": "2019-12-03T09:15:58.1665846Z",
    "score": 340
}
```
