<!-- Source: https://learn.microsoft.com/en-us/defender-xdr/api-overview -->
<!-- Sitemap-Last-Modified: 2026-06-24 -->

# Overview of Microsoft Defender XDR APIs

Note

The **Microsoft Graph security API** is a unified schema and interface that integrates with various Microsoft security solutions and Microsoft security partners. To get started, see [Use the Microsoft Graph security API](https://learn.microsoft.com/en-us/graph/api/resources/security-api-overview).

Important

Some information relates to prereleased product which may be substantially modified before it's commercially released. Microsoft makes no warranties, express or implied, with respect to the information provided here.

Microsoft Defender is built on top of an integration-ready platform.

Use the Microsoft Defender APIs to automate workflows based on the shared incident and advanced hunting tables.

- **[Combined incidents queue](https://learn.microsoft.com/en-us/defender-xdr/api-incident)** - Focus on what's critical by grouping the full attack scope and all impacted assets together under the incident API.
- **[Cross-product threat hunting](https://learn.microsoft.com/en-us/defender-xdr/api-advanced-hunting)** - Leverage your security team's organizational knowledge to hunt for signs of compromise, by creating your own custom queries to sift over raw data collected from multiple protection products.
- **[Event streaming API](https://learn.microsoft.com/en-us/defender-xdr/streaming-api)** - Ship real-time events and alerts in a single data stream as they occur.

Along with these Microsoft Defender-specific APIs, each of our other security products expose [additional APIs](https://learn.microsoft.com/en-us/defender-xdr/api-articles) to help you take advantage of their unique capabilities.

Note

The transition to the unified portal should not affect the PowerBi dashboards based on Microsoft Defender for Endpoint APIs. You can continue to work with the existing APIs regardless of the interactive portal transition.

Watch this short video to learn how you can use Microsoft Defender XDR to automate workflows and integrate apps.

<iframe src="https://learn-video.azurefd.net/vod/player?id=f6300637-b48e-49d7-aa76-2778a711ae6c" allowfullscreen="true" data-linktype="external" frameborder="0"></iframe>

## Learn more

| **Understand how to access the APIs** |
| --- |
| [Use the Microsoft Graph security API - Microsoft Graph \| Microsoft Learn](https://learn.microsoft.com/en-us/graph/api/resources/security-api-overview) |
| [Learn about API quotas and licensing](https://learn.microsoft.com/en-us/legal/microsoft-365/api-terms) |
| [Access the Microsoft Defender XDR APIs](https://learn.microsoft.com/en-us/defender-xdr/api-access) |
| **Build apps** |
| [Create a 'Hello world' app](https://learn.microsoft.com/en-us/defender-xdr/api-hello-world) |
| [Create an app to access Microsoft Defender APIs on behalf of a user](https://learn.microsoft.com/en-us/defender-xdr/api-create-app-user-context) |
| [Create an app to access Microsoft Defender without a user](https://learn.microsoft.com/en-us/defender-xdr/api-create-app-web) |
| [Create an app with multi-tenant partner access to Microsoft Defender APIs](https://learn.microsoft.com/en-us/defender-xdr/api-partner-access) |
| **Troubleshoot and maintain your apps** |
| [Understand API error codes](https://learn.microsoft.com/en-us/defender-xdr/api-error-codes) |
| [Manage secrets in your apps with Azure Key Vault](https://learn.microsoft.com/en-us/training/modules/manage-secrets-with-azure-key-vault/) |
| [Implement OAuth 2.0 authorization for user sign in](https://learn.microsoft.com/en-us/azure/active-directory/develop/active-directory-v2-protocols-oauth-code) |

Tip

Do you want to learn more? Engage with the Microsoft Security community in our Tech Community: [Microsoft Defender XDR Tech Community](https://techcommunity.microsoft.com/t5/microsoft-365-defender/bd-p/MicrosoftThreatProtection).
