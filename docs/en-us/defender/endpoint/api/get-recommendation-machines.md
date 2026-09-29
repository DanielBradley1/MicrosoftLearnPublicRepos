<!-- Source: https://learn.microsoft.com/en-us/defender-endpoint/api/get-recommendation-machines -->
<!-- Sitemap-Last-Modified: 2025-11-24 -->

# List devices by recommendation

Important

Some information in this article relates to a prereleased product which may be substantially modified before it's commercially released. Microsoft makes no warranties, expressed or implied, with respect to the information provided here.

Retrieves a list of devices associated with the security recommendation.

## Permissions

One of the following permissions is required to call this API. To learn more, including how to choose permissions, see [Use Microsoft Defender for Endpoint APIs](https://learn.microsoft.com/en-us/defender-endpoint/api/apis-intro) for details.

| Permission type | Permission | Permission display name |
| --- | --- | --- |
| Application | SecurityRecommendation.Read.All | 'Read Threat and Vulnerability Management security recommendation information' |
| Delegated \(work or school account\) | SecurityRecommendation.Read | 'Read Threat and Vulnerability Management security recommendation information' |

## HTTP request

```http
GET /api/recommendations/{id}/machineReferences
```

## Request headers

| Name | Type | Description |
| --- | --- | --- |
| Authorization | String | Bearer {token}. **Required**. |

## Request body

Empty

## Response

If successful, this method returns 200 OK with the list of devices associated with the security recommendation.

## Example

### Request example

Here is an example of the request.

```http
GET https://api.security.microsoft.com/api/recommendations/va-_-google-_-chrome/machineReferences
```

### Response example

Here is an example of the response.

```json
{
    "@odata.context": "https://api.security.microsoft.com/api/$metadata#MachineReferences",
    "value": [
        {
            "id": "e058770379bc199a9c179ce52a23e16fd44fd2ee",
            "computerDnsName": "niw_pc",
            "osPlatform": "Windows10" "Windows11",
            "rbacGroupName": "GroupTwo"
        }
        ...
    ]
}
```
