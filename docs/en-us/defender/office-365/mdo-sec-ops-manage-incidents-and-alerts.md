<!-- Source: https://learn.microsoft.com/en-us/defender-office-365/mdo-sec-ops-manage-incidents-and-alerts -->
<!-- Sitemap-Last-Modified: 2025-12-23 -->

# Manage incidents and alerts from Microsoft Defender for Office 365 in Microsoft Defender XDR

Tip

*Did you know you can try the features in Microsoft Defender for Office 365 Plan 2 for free?* Use the 90-day Defender for Office 365 trial at the [Microsoft Defender portal trials hub](https://security.microsoft.com/trialHorizontalHub?sku=MDO&ref=DocsRef). Learn about who can sign up and trial terms on [Try Microsoft Defender for Office 365](https://learn.microsoft.com/en-us/defender-office-365/try-microsoft-defender-for-office-365).

An [incident](https://learn.microsoft.com/en-us/defender-xdr/incidents-overview) in the Microsoft Defender portal is a collection of correlated alerts and associated data that define the complete story of an attack. Defender for Office 365 [alerts](https://learn.microsoft.com/en-us/defender-xdr/alert-policies#default-alert-policies), [automated investigation and response \(AIR\)](https://learn.microsoft.com/en-us/defender-office-365/air-about#the-overall-flow-of-air), and the outcome of the investigations are natively integrated and correlated on the **Incidents** page in the Microsoft Defender portal at [https://security.microsoft.com/incidents](https://security.microsoft.com/incidents). We refer to this page as the *Incidents* queue.

Alerts are created when malicious or suspicious activity affects an entity \(for example, email, users, or mailboxes\). Alerts provide valuable insights about in-progress or completed attacks. However, an ongoing attack can affect multiple entities, which results in multiple alerts from different sources. Some built-in alerts automatically trigger AIR playbooks. These playbooks do a series of investigation steps to look for other impacted entities or suspicious activity.

Watch this short video on how to manage Microsoft Defender for Office 365 alerts in the Microsoft Defender portal.

<iframe src="https://learn-video.azurefd.net/vod/player?id=494596e0-41fe-4861-9df5-076312777b0d" allowfullscreen="true" data-linktype="external" frameborder="0"></iframe>

Defender for Office 365 alerts, investigations, and their data are automatically correlated. When a relationship is determined, the system creates an incident to give security teams visibility for the entire attack. Incidents represent more than just static events; they represent attack stories that happen over time. As the attack progresses, new Defender for Office 365 alerts, AIR investigations, and their data are continuously added to the existing incident.

We strongly recommend that SecOps teams manage incidents and alerts from Defender for Office 365 in the Incidents queue at [https://security.microsoft.com/incidents](https://security.microsoft.com/incidents). This approach has the following benefits:

- Multiple options for [management](https://learn.microsoft.com/en-us/defender-xdr/manage-incidents):

  - Prioritization
  - Filtering
  - Classification
  - Tag management


  You can take incidents directly from the queue or assign them to someone. Comments and comment history can help track progress.

- If the attack impacts other workloads that are protected by Microsoft Defender<sup>\*</sup>, the related alerts, investigations, and their data are also correlated to the same incident.

  \<sup>\*</sup>Microsoft Defender for Endpoint, Microsoft Defender for Identity, and Microsoft Defender for Cloud Apps.
- Complex correlation logic isn't required, because the logic is provided by the system.
- If the correlation logic doesn't fully meet your needs, you can add alerts to existing incidents or create new incidents.
- Related Defender for Office 365 alerts, AIR investigations, and pending actions from investigations are automatically added to incidents.
- If the AIR investigation finds no threat, the system automatically resolves the related alerts If all alerts within an incident are resolved, the incident status also changes to **Resolved**.
- Related evidence and response actions are automatically aggregated on the **Evidence and response** tab of the incident.
- Security team members can take response actions directly from the incidents. For example, they can soft-delete email in mailboxes or remove suspicious Inbox rules from mailboxes.
- Recommended email actions are created only when the latest delivery location of a malicious email is a cloud mailbox.
- Pending email actions are updated based on the latest delivery location. If the email was already remediated by a manual action, the status reflects that.
- Recommended actions are created only for email and email clusters that are determined to be the most critical threats:

  - Malware
  - High confidence phishing
  - Malicious URLs
  - Malicious files

Note

The Defender portal shows a single evidence cluster for Defender for Office 365 instead of listing individual evidence items.

Manage incidents on the **Incidents** page in the Microsoft Defender portal at [https://security.microsoft.com/incidents](https://security.microsoft.com/incidents):

[![Incidents page in the Microsoft Defender portal.](https://learn.microsoft.com/en-us/defender-office-365/media/mdo-sec-ops-incidents.png)](https://learn.microsoft.com/en-us/defender-office-365/media/mdo-sec-ops-incidents.png#lightbox)

[![Details flyout on the Incidents page in the Microsoft Defender portal.](https://learn.microsoft.com/en-us/defender-office-365/media/mdo-sec-ops-incident-details.png)](https://learn.microsoft.com/en-us/defender-office-365/media/mdo-sec-ops-incident-details.png#lightbox)

[![Filter flyout on the Incidents page in the Microsoft Defender portal.](https://learn.microsoft.com/en-us/defender-office-365/media/mdo-sec-ops-incident-filters.png)](https://learn.microsoft.com/en-us/defender-office-365/media/mdo-sec-ops-incident-filters.png#lightbox)

[![Summary tab of the incident details in the Microsoft Defender portal.](https://learn.microsoft.com/en-us/defender-office-365/media/mdo-sec-ops-incident-summary-tab.png)](https://learn.microsoft.com/en-us/defender-office-365/media/mdo-sec-ops-incident-summary-tab.png#lightbox)

[![Evidence and alerts tab of the incident details in the Microsoft Defender portal.](https://learn.microsoft.com/en-us/defender-office-365/media/mdo-sec-ops-incident-evidence-and-response-tab.png)](https://learn.microsoft.com/en-us/defender-office-365/media/mdo-sec-ops-incident-evidence-and-response-tab.png#lightbox)

Manage incidents on the **Incidents** page in Microsoft Sentinel at [https://portal.azure.com/#blade/HubsExtension/BrowseResource/resourceType/microsoft.securityinsightsarg%2Fsentinel](https://portal.azure.com/#blade/HubsExtension/BrowseResource/resourceType/microsoft.securityinsightsarg%2Fsentinel):

[![Incidents page in Microsoft Sentinel.](https://learn.microsoft.com/en-us/defender-office-365/media/microsoft-sentinel-incidents.png)](https://learn.microsoft.com/en-us/defender-office-365/media/microsoft-sentinel-incidents.png#lightbox)

[![Incident details page in Microsoft Sentinel.](https://learn.microsoft.com/en-us/defender-office-365/media/mdo-sec-ops-microsoft-sentinel-incident-details.png)](https://learn.microsoft.com/en-us/defender-office-365/media/mdo-sec-ops-microsoft-sentinel-incident-details.png#lightbox)

## Response actions to take

Security teams can take wide variety of response actions on email using Defender for Office 365 tools:

- You can delete messages, but you can also take the following actions on email:

  - Move to Inbox
  - Move to Junk
  - Move to Deleted Items
  - Soft delete
  - Hard delete.


  You can take these actions from the following locations:


  - The **Evidence and response** tab from the details of the incident on the **Incidents** page at [https://security.microsoft.com/incidents](https://security.microsoft.com/incidents) \(recommended\).
  - **Threat Explorer** at [https://security.microsoft.com/threatexplorer](https://security.microsoft.com/threatexplorer).
  - The unified **Action center** at [https://security.microsoft.com/action-center/pending](https://security.microsoft.com/action-center/pending).

- You can start an AIR playbook manually on any email message using the **Trigger investigation** action in Threat Explorer.
- You can report false positive or false negative detections directly to Microsoft using [Threat Explorer](https://learn.microsoft.com/en-us/defender-office-365/threat-explorer-real-time-detections-about) or [admin submissions](https://learn.microsoft.com/en-us/defender-office-365/submissions-admin).
- You can block undetected malicious files, URLs, or senders using the [Tenant Allow/Block List](https://learn.microsoft.com/en-us/defender-office-365/tenant-allow-block-list-about).

Actions in Defender for Office 365 are seamlessly integrated into hunting experiences and the history of actions are visible on the **History** tab in the unified **Action center** at [https://security.microsoft.com/action-center/history](https://security.microsoft.com/action-center/history).

The most effective way to take action is to use the built-in integration with Incidents in Microsoft Defender XDR. You can approve the actions that were recommended by AIR in Defender for Office 365 on the [Evidence and response](https://learn.microsoft.com/en-us/defender-xdr/investigate-incidents#evidence-and-response) tab of an incident in Microsoft Defender XDR. This method of tacking action is recommended for the following reasons:

- You investigate the complete attack story.
- You benefit from the built-in correlation with other workloads: Microsoft Defender for Endpoint, Microsoft Defender for Identity, and Microsoft Defender for Cloud Apps.
- You take actions on email from a single place.

You take action on email based on the result of a manual investigation or hunting activity. [Threat Explorer](https://learn.microsoft.com/en-us/defender-office-365/threat-explorer-real-time-detections-about) allows security team members to take action on any email messages that might still exist in cloud mailboxes. They can take action on intra-org messages that were sent between users in your organization. Threat Explorer data is available for the last 30 days.

Watch this short video to learn how the Microsoft Defender portal combines alerts from various detection sources, like Defender for Office 365, into incidents.

<iframe src="https://learn-video.azurefd.net/vod/player?id=6d002a6f-7009-428c-983e-1b5be8e0db36" allowfullscreen="true" data-linktype="external" frameborder="0"></iframe>
