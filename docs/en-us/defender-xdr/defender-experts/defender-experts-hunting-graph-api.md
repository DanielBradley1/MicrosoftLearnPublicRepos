<!-- Source: https://learn.microsoft.com/en-us/defender-xdr/defender-experts/defender-experts-hunting-graph-api -->
<!-- Sitemap-Last-Modified: 2026-07-01 -->

# Access incident notifications using Graph API

[Defender Experts Notifications](https://learn.microsoft.com/en-us/defender-xdr/defender-experts/defender-experts-hunting-onboarding#receive-defender-experts-notifications) are incidents that have been generated from hunting conducted by Defender Experts in your environment. They contain information regarding the hunting investigation and recommended actions provided by Defender Experts. You can now access DENs using the [Microsoft Graph security API](https://learn.microsoft.com/en-us/graph/api/resources/security-api-overview).

Note

Any incident in the Microsoft Defender portal is a collection of correlated alerts. [Microsoft Graph security incident resource type](https://learn.microsoft.com/en-us/graph/api/resources/security-incident)

The following Defender Experts Notification details are available in the Microsoft Defender portal:

- **Incident title** - starts with *Defender Experts* to distinguish Defender Experts Notifications from other incidents
- **Executive summary** - provides an overview of the investigation summary
- **Recommendation summary** - lists the recommended actions from Defender Experts
- **Advanced hunting queries** - lists the converted KQL hunting queries used for the investigation

In Microsoft Graph security API, the following fields are also available:

- **Graph endpoint** - [https://graph.microsoft.com/beta/security/incidents](https://graph.microsoft.com/beta/security/incidents)
- The following **field names** that correspond to the Defender Experts Notification details listed above:

  - displayName
  - description
  - recommendedActions
  - recommendedHuntingQueries

Note

The displayName, description, recommendedActions, and recommendedHuntingQueries fields will soon be available in the Graph v1.0 endpoint. For more information, see [Microsoft Graph REST API v1.0](https://learn.microsoft.com/en-us/graph/api/resources/security-incident)

Your approach to consuming Defender Experts Notifications from the API will vary depending on the downstream system you intend to use and your specific requirements. However, the following steps are a basic implementation to help you get started:

**Starting from incidents in the Graph API**

1. Get incidents from Graph security API.
2. Check for new incidents where **displayName** starts with *Defender Experts*.
3. Continue reading the remaining fields for such incidents.
4. Synchronize the Defender Experts Notification \(DEN\) information into your downstream tool \(for example, ServiceNow\).

**Starting from alerts in the Graph API**

1. Get alerts from Graph security API.
2. Check for new alerts where **detectionSource** starts with *microsoftThreatExperts*.
3. Look up corresponding incident by checking **incidentId** listed on the alert.
4. Continue reading the remaining fields for such incidents.
5. Synchronize the Defender Experts Notification \(DEN\) information into your downstream tool \(for example, ServiceNow\).

## Next step

- [Collaborate with Experts on Demand](https://learn.microsoft.com/en-us/defender-xdr/defender-experts/defender-experts-hunting-ask-experts)

Tip

Do you want to learn more? Engage with the Microsoft Security community in our Tech Community: [Microsoft Defender XDR Tech Community](https://techcommunity.microsoft.com/t5/microsoft-365-defender/bd-p/MicrosoftThreatProtection).
