<!-- Source: https://learn.microsoft.com/en-us/defender-xdr/api-supported -->
<!-- Sitemap-Last-Modified: 2025-04-18 -->

# Supported Microsoft Defender XDR APIs

Note

**Try our new APIs using MS Graph security API**. Find out more at: [Use the Microsoft Graph security API - Microsoft Graph \| Microsoft Learn](https://learn.microsoft.com/en-us/graph/api/resources/security-api-overview).

Important

Some information relates to prereleased product which may be substantially modified before it's commercially released. Microsoft makes no warranties, express or implied, with respect to the information provided here.

## List of available APIs

| Article | Description |
| --- | --- |
| [Advanced Hunting API](https://learn.microsoft.com/en-us/defender-xdr/api-advanced-hunting) | Run Advanced Hunting queries. |
| [Incident APIs](https://learn.microsoft.com/en-us/defender-xdr/api-incident) | List and update incidents, along with other practical tasks. |
| [Streaming API](https://learn.microsoft.com/en-us/defender-xdr/streaming-api) | Ship real-time events and alerts as they occur in a single data stream. |

### Endpoint URIs

The base URI for both of the main APIs is: [https://api.security.microsoft.com](https://api.security.microsoft.com). For better performance, use a server closer to your geolocation:

- The United States: api-us.security.microsoft.com
- Europe: api-eu.security.microsoft.com
- The United Kingdom: api-uk.security.microsoft.com

Tokens can be acquired by accessing [https://api.security.microsoft.com](https://api.security.microsoft.com).

All APIs along the `/api` path use the [OData](https://learn.microsoft.com/en-us/odata/overview) Protocol; for example, [https://api.security.microsoft.com/api/incidents](https://api.security.microsoft.com/api/incidents).

## Related articles

- [Use the Microsoft Graph security API - Microsoft Graph \| Microsoft Learn](https://learn.microsoft.com/en-us/graph/api/resources/security-api-overview)
- [Microsoft Defender XDR APIs overview](https://learn.microsoft.com/en-us/defender-xdr/api-overview)
- [Access the Microsoft Defender XDR APIs](https://learn.microsoft.com/en-us/defender-xdr/api-access)
- [Streaming API](https://learn.microsoft.com/en-us/defender-endpoint/api/raw-data-export)
- [Learn about API limits and licensing](https://learn.microsoft.com/en-us/legal/microsoft-365/api-terms)
- [Understand error codes](https://learn.microsoft.com/en-us/defender-xdr/api-error-codes)

Tip

Do you want to learn more? Engage with the Microsoft Security community in our Tech Community: [Microsoft Defender XDR Tech Community](https://techcommunity.microsoft.com/t5/microsoft-365-defender/bd-p/MicrosoftThreatProtection).
