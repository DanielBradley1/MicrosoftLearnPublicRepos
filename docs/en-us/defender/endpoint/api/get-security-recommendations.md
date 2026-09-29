<!-- Source: https://learn.microsoft.com/en-us/defender-endpoint/api/get-security-recommendations -->
<!-- Sitemap-Last-Modified: 2025-12-11 -->

# Get security recommendations

Important

Some information in this article relates to a prereleased product which may be substantially modified before it's commercially released. Microsoft makes no warranties, expressed or implied, with respect to the information provided here.

Retrieves a collection of security recommendations related to a given device ID.

## Permissions

One of the following permissions is required to call this API. To learn more, including how to choose permissions, see [Use Microsoft Defender for Endpoint APIs](https://learn.microsoft.com/en-us/defender-endpoint/api/apis-intro)

| Permission type | Permission | Permission display name |
| --- | --- | --- |
| Application | SecurityRecommendation.Read.All | 'Read Threat and Vulnerability Management security recommendation information' |
| Delegated \(work or school account\) | SecurityRecommendation.Read | 'Read Threat and Vulnerability Management security recommendation information' |

## HTTP request

```http
GET /api/machines/{machineId}/recommendations
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

Here is an example of the request.

```http
GET https://api.security.microsoft.com/api/machines/ac233fa6208e1579620bf44207c4006ed7cc4501/recommendations
```

### Response example

Here is an example of the response.

```json
{
    "@odata.context": "https://api.security.microsoft.com/api/$metadata#Recommendations",
    "value": [
        {
            "id": "va-_-git-scm-_-git",
            "productName": "git",
            "recommendationName": "Update Git to version 2.24.1.2",
            "weaknesses": 3,
            "vendor": "git-scm",
            "recommendedVersion": "2.24.1.2",
            "recommendationCategory": "Application",
            "subCategory": "",
            "severityScore": 0,
            "publicExploit": false,
            "activeAlert": false,
            "associatedThreats": [],
            "remediationType": "Update",
            "status": "Active",
            "configScoreImpact": 0,
            "exposureImpact": 0,
            "totalMachineCount": 0,
            "exposedMachinesCount": 1,
            "nonProductivityImpactedAssets": 0,
            "relatedComponent": "Git"
        },
...
}
```
