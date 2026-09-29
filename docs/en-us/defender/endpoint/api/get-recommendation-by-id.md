<!-- Source: https://learn.microsoft.com/en-us/defender-endpoint/api/get-recommendation-by-id -->
<!-- Sitemap-Last-Modified: 2025-11-24 -->

# Get recommendation by ID

Important

Some information in this article relates to a prereleased product which may be substantially modified before it's commercially released. Microsoft makes no warranties, expressed or implied, with respect to the information provided here.

Retrieves a security recommendation by its ID.

## Permissions

One of the following permissions is required to call this API. To learn more, including how to choose permissions, see [Use Microsoft Defender for Endpoint APIs](https://learn.microsoft.com/en-us/defender-endpoint/api/apis-intro) for details.

| Permission type | Permission | Permission display name |
| --- | --- | --- |
| Application | SecurityRecommendation.Read.All | 'Read Threat and Vulnerability Management security recommendation information' |
| Delegated \(work or school account\) | SecurityRecommendation.Read | 'Read Threat and Vulnerability Management security recommendation information' |

## HTTP request

```http
GET /api/recommendations/{id}
```

## Request headers

| Name | Type | Description |
| --- | --- | --- |
| Authorization | String | Bearer {token}. **Required**. |

## Request body

Empty

## Response

If successful, this method returns 200 OK with the security recommendations in the body.

## Example

### Request example

Here's an example of the request.

```http
GET https://api.security.microsoft.com/api/recommendations/va-_-google-_-chrome
```

### Response example

Here's an example of the response.

```json
{
    "@odata.context": "https://api.security.microsoft.com/api/$metadata#Recommendations/$entity",
    "id": "va-_-google-_-chrome",
    "productName": "chrome",
    "recommendationName": "Update Chrome",
    "weaknesses": 38,
    "vendor": "google",
    "recommendedVersion": "",
    "recommendationCategory": "Application",
    "subCategory": "",
    "severityScore": 0,
    "publicExploit": false,
    "activeAlert": false,
    "associatedThreats": [],
    "remediationType": "Update",
    "status": "Active",
    "configScoreImpact": 0,
    "exposureImpact": 3.9441860465116285,
    "totalMachineCount": 6,
    "exposedMachinesCount": 5,
    "nonProductivityImpactedAssets": 0,
    "relatedComponent": "Chrome",
    "tags": [
    "internetFacing"
    ],
    "exposedCriticalDevices": 116
}
```

## Related articles

- [Microsoft Defender Vulnerability Management](https://learn.microsoft.com/en-us/defender-vulnerability-management/defender-vulnerability-management)
- [Defender Vulnerability Management security recommendation](https://learn.microsoft.com/en-us/defender-vulnerability-management/tvm-security-recommendation)
