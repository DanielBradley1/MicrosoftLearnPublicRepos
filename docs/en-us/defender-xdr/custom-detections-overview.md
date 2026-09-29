<!-- Source: https://learn.microsoft.com/en-us/defender-xdr/custom-detections-overview -->
<!-- Sitemap-Last-Modified: 2026-07-06 -->

# Custom detections overview

With custom detections, you can proactively monitor for and respond to various events and system states, including suspected breach activity and misconfigured endpoints. Custom detections are customizable detection rules that automatically trigger alerts and response actions.

Custom detections work with [advanced hunting](https://learn.microsoft.com/en-us/defender-xdr/advanced-hunting-overview), which provides a powerful, flexible query language that covers a broad set of event and system information from your network. You can set them to run at regular intervals, generating alerts and taking response actions whenever there are matches. You can create custom detection rules from the advanced hunting query editor or directly from the custom detection rules list.

Custom detections provide:

- Alerts for rule-based detections built from advanced hunting queries
- Automatic response actions

Optimizing your queries in custom detection rules is important in avoiding time-outs and ensuring efficiency. There are several resources available that provide guidance on optimizing your queries in [Advanced hunting query best practices](https://learn.microsoft.com/en-us/defender-xdr/advanced-hunting-best-practices).

## Manage custom detections as code \(Preview\)

You can manage custom detection rules as code in a GitHub or Azure DevOps repository using the Microsoft Security BICEP extension. Deploy custom detections through Microsoft Sentinel Repositories for automatic sync, or use BICEP CLI for custom pipelines. For more information, see [Deploy custom detection rules as code](https://learn.microsoft.com/en-us/azure/sentinel/ci-cd-custom-content#deploy-custom-detection-rules-as-code-preview).

## See also

- [Create and manage custom detection rules](https://learn.microsoft.com/en-us/defender-xdr/custom-detection-rules)
- [Advanced hunting query best practices](https://learn.microsoft.com/en-us/defender-xdr/advanced-hunting-best-practices)
- [Migrate advanced hunting queries from Microsoft Defender for Endpoint](https://learn.microsoft.com/en-us/defender-xdr/advanced-hunting-migrate-from-mde)
- [Microsoft Graph security API for custom detections](https://learn.microsoft.com/en-us/graph/api/resources/security-api-overview?view=graph-rest-beta&preserve-view=true#custom-detections)

Tip

Do you want to learn more? Engage with the Microsoft Security community in our Tech Community: [Microsoft Defender XDR Tech Community](https://techcommunity.microsoft.com/t5/microsoft-365-defender/bd-p/MicrosoftThreatProtection).
