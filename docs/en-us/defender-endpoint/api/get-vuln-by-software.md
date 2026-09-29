<!-- Source: https://learn.microsoft.com/en-us/defender-endpoint/api/get-vuln-by-software -->
<!-- Sitemap-Last-Modified: 2025-11-24 -->

# List vulnerabilities by software

Important

Some information in this article relates to a prereleased product which may be substantially modified before it's commercially released. Microsoft makes no warranties, expressed or implied, with respect to the information provided here.

Retrieve a list of vulnerabilities in the installed software.

## Permissions

One of the following permissions is required to call this API. To learn more, including how to choose permissions, see [Use Microsoft Defender for Endpoint APIs](https://learn.microsoft.com/en-us/defender-endpoint/api/apis-intro) for details.

| Permission type | Permission | Permission display name |
| --- | --- | --- |
| Application | Vulnerability.Read.All | 'Read Threat and Vulnerability Management Software information' |
| Delegated \(work or school account\) | Vulnerability.Read | 'Read Threat and Vulnerability Management Software information' |

## HTTP request

```http
GET /api/Software/{Id}/vulnerabilities
```

## Request headers

| Name | Type | Description |
| --- | --- | --- |
| Authorization | String | Bearer {token}.**Required**. |

## Request body

Empty

## Response

If successful, this method returns 200 OK with a list of vulnerabilities exposed by the specified software.

## Example

### Request example

Here's an example of the request.

```http
GET https://api.security.microsoft.com/api/Software/microsoft-_-edge/vulnerabilities
```

### Response example

Here's an example of the response.

```json
{
    "@odata.context": "https://api.security.microsoft.com/api/$metadata#Collection(Analytics.Contracts.PublicAPI.PublicVulnerabilityDto)",
    "value": [
            {
                "id": "CVE-2017-0140",
                "name": "CVE-2017-0140",
                "description": "A security feature bypass vulnerability exists when Microsoft Edge improperly handles requests of different origins. The vulnerability allows Microsoft Edge to bypass Same-Origin Policy (SOP) restrictions, and to allow requests that should otherwise be ignored. An attacker who successfully exploited the vulnerability could force the browser to send data that would otherwise be restricted.In a web-based attack scenario, an attacker could host a specially crafted website that is designed to exploit the vulnerability through Microsoft Edge and then convince a user to view the website. The attacker could also take advantage of compromised websites, and websites that accept or host user-provided content or advertisements. These websites could contain specially crafted content that could exploit the vulnerability.The security update addresses the vulnerability by modifying how affected Microsoft Edge handles different-origin requests.",
                "severity": "Medium",
                "cvssV3": 4.2,
                "exposedMachines": 1,
                "publishedOn": "2017-03-14T00:00:00Z",
                "updatedOn": "2019-10-03T00:03:00Z",
                "publicExploit": false,
                "exploitVerified": false,
                "exploitInKit": false,
                "exploitTypes": [],
                "exploitUris": []
            }
            ...
        ]
}
```
