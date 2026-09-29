<!-- Source: https://learn.microsoft.com/en-us/defender-endpoint/api/get-software-ver-distribution -->
<!-- Sitemap-Last-Modified: 2025-11-24 -->

# List software version distribution

Important

Some information in this article relates to a prereleased product which may be substantially modified before it's commercially released. Microsoft makes no warranties, expressed or implied, with respect to the information provided here.

Retrieves a list of your organization's software version distribution.

## Permissions

One of the following permissions is required to call this API. To learn more, including how to choose permissions, see [Use Microsoft Defender for Endpoint APIs](https://learn.microsoft.com/en-us/defender-endpoint/api/apis-intro) for details.

| Permission type | Permission | Permission display name |
| --- | --- | --- |
| Application | Software.Read.All | 'Read Threat and Vulnerability Management Software information' |
| Delegated \(work or school account\) | Software.Read | 'Read Threat and Vulnerability Management Software information' |

## HTTP request

```http
GET /api/Software/{Id}/distributions
```

## Request headers

| Name | Type | Description |
| --- | --- | --- |
| Authorization | String | Bearer {token}.**Required**. |

## Request body

Empty

## Response

If successful, this method returns 200 OK with a list of software distributions data in the body.

## Example

### Request example

Here is an example of the request.

```http
GET https://api.security.microsoft.com/api/Software/microsoft-_-edge/distributions
```

### Response example

Here's an example of the response.

```json

{
    "@odata.context": "https://api.security.microsoft.com/api/$metadata#Distributions",
    "value": [
        {
            "version": "11.0.17134.1039",
            "installations": 1,
            "vulnerabilities": 11
        },
        {
            "version": "11.0.18363.535",
            "installations": 750,
            "vulnerabilities": 0
        }
        ...
    ]
}
```
