<!-- Source: https://learn.microsoft.com/en-us/defender-endpoint/api/get-discovered-vulnerabilities -->
<!-- Sitemap-Last-Modified: 2025-12-11 -->

# Get discovered vulnerabilities

## API description

Retrieves a collection of discovered vulnerabilities related to a given device ID.

## Limitations

Rate limitations for this API are 50 calls per minute and 1500 calls per hour.

## Permissions

One of the following permissions is required to call this API. To learn more, including how to choose permissions, see [Use Microsoft Defender for Endpoint APIs](https://learn.microsoft.com/en-us/defender-endpoint/api/apis-intro)

| Permission type | Permission | Permission display name |
| --- | --- | --- |
| Application | Vulnerability.Read.All | 'Read Threat and Vulnerability Management vulnerability information' |
| Delegated \(work or school account\) | Vulnerability.Read | 'Read Threat and Vulnerability Management vulnerability information' |

## HTTP request

```http
GET /api/machines/{machineId}/vulnerabilities
```

## Request headers

| Name | Type | Description |
| --- | --- | --- |
| Authorization | String | Bearer {token}. **Required**. |

## Request body

Empty

## Response

If successful, this method returns 200 OK with the discovered vulnerability information in the body.

## Example

### Request

Here is an example of the request.

```http
GET https://api.security.microsoft.com/api/machines/ac233fa6208e1579620bf44207c4006ed7cc4501/vulnerabilities
```

### Response

Here is an example of the response.

```json
{
    "@odata.context": "https://api.security.microsoft.com/api/$metadata#Collection(Analytics.Contracts.PublicAPI.PublicVulnerabilityDto)",
    "value": [
        {
            "id": "CVE-2019-1348",
            "name": "CVE-2019-1348",
            "description": "Git could allow a remote attacker to bypass security restrictions, caused by a flaw in the --export-marks option of git fast-import. By persuading a victim to import specially-crafted content, an attacker could exploit this vulnerability to overwrite arbitrary paths.",
            "severity": "Medium",
            "cvssV3": 4.3,
            "exposedMachines": 1,
            "publishedOn": "2019-12-13T00:00:00Z",
            "updatedOn": "2019-12-13T00:00:00Z",
            "publicExploit": false,
            "exploitVerified": false,
            "exploitInKit": false,
            "exploitTypes": [],
            "exploitUris": []
        }
    ]
}
```
