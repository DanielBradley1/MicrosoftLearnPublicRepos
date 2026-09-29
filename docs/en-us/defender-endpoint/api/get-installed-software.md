<!-- Source: https://learn.microsoft.com/en-us/defender-endpoint/api/get-installed-software -->
<!-- Sitemap-Last-Modified: 2025-12-11 -->

# Get installed software

Important

Some information in this article relates to a prereleased product which may be substantially modified before it's commercially released. Microsoft makes no warranties, expressed or implied, with respect to the information provided here.

Retrieves a collection of installed software related to a given device ID.

## Permissions

One of the following permissions is required to call this API. To learn more, including how to choose permissions, see [Use Microsoft Defender for Endpoint APIs](https://learn.microsoft.com/en-us/defender-endpoint/api/apis-intro)

| Permission type | Permission | Permission display name |
| --- | --- | --- |
| Application | Software.Read.All | 'Read Threat and Vulnerability Management Software information' |
| Delegated \(work or school account\) | Software.Read | 'Read Threat and Vulnerability Management Software information' |

## HTTP request

```http
GET /api/machines/{machineId}/software
```

## Request headers

| Name | Type | Description |
| --- | --- | --- |
| Authorization | String | Bearer {token}. **Required**. |

## Request body

Empty

## Response

If successful, this method returns 200 OK with the installed software information in the body.

## Example

### Request example

Here is an example of the request.

```http
GET https://api.security.microsoft.com/api/machines/ac233fa6208e1579620bf44207c4006ed7cc4501/software
```

### Response example

Here's an example of the response.

```json
{
"@odata.context": "https://api.security.microsoft.com/api/$metadata#Software",
"value": [
        {
"id": "microsoft-_-internet_explorer",
"name": "internet_explorer",
"vendor": "microsoft",
"weaknesses": 67,
"publicExploit": true,
"activeAlert": false,
"exposedMachines": 42115,
"impactScore": 46.2037163
        }
    ]
}
```
