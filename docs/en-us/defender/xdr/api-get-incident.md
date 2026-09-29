<!-- Source: https://learn.microsoft.com/en-us/defender-xdr/api-get-incident -->
<!-- Sitemap-Last-Modified: 2025-12-10 -->

# Get incident information API

Note

If you're a US Government customer, use the URIs listed in [Microsoft Defender for Endpoint for US Government customers](https://learn.microsoft.com/en-us/defender-endpoint/gov#api).

Tip

For better performance, instead of using api.security.microsoft.com, use a server closer to your geolocation:

- us.api.security.microsoft.com
- eu.api.security.microsoft.com
- uk.api.security.microsoft.com
- au.api.security.microsoft.com
- swa.api.security.microsoft.com
- ina.api.security.microsoft.com
- aea.api.security.microsoft.com

Note

**Try our new APIs using MS Graph security API**. Find out more at: [Use the Microsoft Graph security API - Microsoft Graph \| Microsoft Learn](https://learn.microsoft.com/en-us/graph/api/resources/security-api-overview).

## API description

Retrieves a specific incident by its ID

## Limitations

1. Rate limitations for this API are 100 calls per minute and 1,500 calls per hour.

## Permissions

One of the following permissions is required to call this API.

| Permission type | Permission | Permission display name |
| --- | --- | --- |
| Application | Incident.Read.All | `Read all Incidents` |
| Application | Incident.ReadWrite.All | `Read and write all Incidents` |
| Delegated \(work or school account\) | Incident.Read | `Read Incidents` |
| Delegated \(work or school account\) | Incident.ReadWrite | `Read and write Incidents` |

Note

When obtaining a token using user credentials:

- The user needs to have at least the following role permission: `View Data`
- The response will only include incidents that the user is exposed to

## HTTP request

```console
GET .../api/incidents/{id}
```

## Request headers

| Name | Type | Description |
| --- | --- | --- |
| Authorization | String | Bearer {token}. **Required**. |

## Request body

Empty

## Response

If successful, this method returns `200 OK`, and the incident entity in the response body. If incident with the specified ID wasn't found - 404 Not Found.

## Example

### Request

Here's an example of the request.

```http
GET https://api.security.microsoft.com/api/incidents/{id}
```

## Related content

[Use the Microsoft Graph security API - Microsoft Graph \| Microsoft Learn](https://learn.microsoft.com/en-us/graph/api/resources/security-api-overview)

Tip

Do you want to learn more? Engage with the Microsoft Security community in our Tech Community: [Microsoft Defender XDR Tech Community](https://techcommunity.microsoft.com/t5/microsoft-365-defender/bd-p/MicrosoftThreatProtection).
