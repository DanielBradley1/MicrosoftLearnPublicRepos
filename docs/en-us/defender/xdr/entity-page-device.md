<!-- Source: https://learn.microsoft.com/en-us/defender-xdr/entity-page-device -->
<!-- Sitemap-Last-Modified: 2026-04-21 -->

# Device entity page in Microsoft Defender

The device entity page in the Microsoft Defender portal helps you in your investigation of device entities. The page contains all the important information about a given device entity. If an alert or incident indicates that a device is behaving suspiciously or might be compromised, investigate the details of the device to identify other behaviors or events that might be related to the alert or incident, and discover the potential scope of the breach. You can also use the device entity page to perform some common security tasks, as well as some response actions to mitigate or remediate security threats.

Important

The content set displayed on the device entity page may differ slightly, depending on the device's enrollment in Microsoft Defender for Endpoint and Microsoft Defender for Identity.

If your organization onboarded Microsoft Sentinel to the Defender portal, additional information will appear.

In Microsoft Sentinel, device entities are also known as **host** entities. [Learn more](https://learn.microsoft.com/en-us/azure/sentinel/entities-reference).

Microsoft Sentinel is generally available in the Microsoft Defender portal, with or without Microsoft Defender XDR or an E5 license. For more information, see [Microsoft Sentinel in the Microsoft Defender portal](https://go.microsoft.com/fwlink/p/?linkid=2263690).

After **March 31, 2027**, Microsoft Sentinel will no longer be supported in the Azure portal and will be available only in the Microsoft Defender portal.

If you're currently using Microsoft Sentinel in the Azure portal, we recommend that you start planning your transition to the Defender portal now to ensure a smooth transition and take full advantage of the [unified security operations experience offered by Microsoft Defender](https://learn.microsoft.com/en-us/defender-xdr/isoc-overview). For more information, see [Transition your Microsoft Sentinel environment to the Defender portal](https://learn.microsoft.com/en-us/azure/sentinel/move-to-defender) and [Planning your move to Microsoft Defender portal for all Microsoft Sentinel customers](https://techcommunity.microsoft.com/blog/microsoft-security-blog/planning-your-move-to-microsoft-defender-portal-for-all-microsoft-sentinel-custo/4428613) \(blog\).

Device entities can be found in the following areas:

- Devices list, under **Assets**
- Alerts queue
- Any individual alert/incident
- Any individual user entity page
- Any individual file details view
- Any IP address or domain details view
- Activity log
- Advanced hunting queries
- Action center

You can select devices whenever you see them in the portal to open the device's entity page, which displays more details about the device. For example, you can see the details of devices listed in the alerts of an incident in the Microsoft Defender portal at **Investigation & response > Incidents & alerts > Incidents > *incident* > Assets > Devices**.

![Screenshot of the Users page for an incident in the Microsoft Defender portal.](https://learn.microsoft.com/en-us/defender-xdr/media/entity-page-device/device-incident-assets.png)

The device entity page presents its information in a tabbed format. This article lays out the types of information available in each tab, and also the actions you can take on a given device.

The following tabs are displayed on the device entity page:

- [Overview](#overview-tab)
- [Incidents and alerts](#incidents-and-alerts-tab)
- [Timeline](#timeline-tab)
- [Configuration management](#configuration-management-tab)
- [Security recommendations](#security-recommendations-tab)
- [Inventories](#inventories-tab)
- [Discovered vulnerabilities](#discovered-vulnerabilities-tab)
- [Missing KBs](#missing-kbs-tab)
- [Security baselines](#missing-kbs-tab)
- [Security policies](#missing-kbs-tab)
- [Sentinel events](#sentinel-events-tab)

## Entity page header

The topmost section of the entity page includes the following details:

- **Entity name**
- **Risk severity**, **criticality**, and **device value** indicators
- **Tags** by which the device can be classified. Can be added by Defender for Endpoint, Defender for Identity, or by users. Tags from Microsoft Defender for Identity aren't editable.
- **[Response actions](#response-actions)** are also located here. Read more about them below.

## *Overview* tab

The default tab is **Overview**. It provides a quick look at the most important security facts about the device. The **Overview** tab contains the [device details](#device-details) sidebar and a [dashboard](#dashboard) with some cards displaying high-level information.

### Device details

The sidebar lists the device's full name and exposure level. It also provides some important basic information in small subsections, which can be expanded or collapsed, such as:

| Section | Included information |
| --- | --- |
| **VM details** | Machine and domain names and IDs, health and onboarding statuses, timestamps for first and last seen, IP addresses, and more |
| **DLP policy sync details** | If relevant |
| **Configuration status** | Details regarding Microsoft Defender for Endpoint configuration |
| **Cloud resource details** | Cloud platform, resource ID, subscription information, and more |
| **Hardware and firmware** | VM, processor, and BIOS information, and more |
| **Device management** | Microsoft Defender for Endpoint enrollment status and management info |
| **Directory data** | [UAC](https://learn.microsoft.com/en-us/windows/security/identity-protection/user-account-control/user-account-control-overview) flags, [SPNs](https://learn.microsoft.com/en-us/windows/win32/ad/service-principal-names), and group memberships. |

### Dashboard

The main part of the **Overview** tab shows several dashboard-type display cards:

- **Active alerts** and risk level involving the device over the last six months, grouped by severity
- **Security assessments** and exposure level of the device
- **Logged on users** on the device over the last 30 days
- **Device health status** and other information on the most recent scans of the device.

Tip

Exposure level relates to how much the device is complying with security recommendations, while risk level is calculated based on a number of factors, including the types and severity of active alerts.

[![Screenshot of the Overview tab for the device entity page in the Microsoft Defender portal.](https://learn.microsoft.com/en-us/defender-xdr/media/entity-page-device/entity-device-overview-tab.png)](https://learn.microsoft.com/en-us/defender-xdr/media/entity-page-device/entity-device-overview-tab.png#lightbox)

## *Incidents and alerts* tab

The **Incidents and alerts** tab contains a list of incidents that contain alerts that have been raised on the device, from any of a number of Microsoft Defender detection sources, including, if onboarded, Microsoft Sentinel. This list is a filtered version of the [incidents queue](https://learn.microsoft.com/en-us/defender-xdr/incidents-overview), and shows a short description of the incident or alert, its severity \(high, medium, low, informational\), its status in the queue \(new, in progress, resolved\), its classification \(not set, false alert, true alert\), investigation state, category, who is assigned to address it, and last activity observed.

You can customize which columns are displayed for each item. You can also filter the alerts by severity, status, or any other column in the display.

The *impacted entities* column refers to all the device and user entities referenced in the incident or alert.

When an incident or alert is selected, a fly-out appears. From this panel you can manage the incident or alert and view more details such as incident/alert number and related devices. Multiple alerts can be selected at a time.

To see a full page view of an incident or alert, select its title.

[![Screenshot of the Incidents and alerts tab for the device entity page in the Microsoft Defender portal.](https://learn.microsoft.com/en-us/defender-xdr/media/entity-page-device/entity-device-incidents-tab.png)](https://learn.microsoft.com/en-us/defender-xdr/media/entity-page-device/entity-device-incidents-tab.png#lightbox)

## *Timeline* tab

The **Timeline** tab displays a chronological view of all events that have been observed on the device. This can help you correlate any events, files, and IP addresses in relation to the device.

The choice of columns displayed on the list can both be customized. The default columns list the event time, active user, action type, associated entities \(processes, files, IP addresses\), and additional information about the event.

You can govern the time period for which events are displayed by sliding the borders of the time period along the overall timeline graph at the top of the page. You can also pick a time period from the drop-down at the top of the list \(the default is 30 days\). To further control your view, you can filter by event groups or customize the columns.

You can export up to seven days' worth of events to a CSV file, for download.

Drill down into the details of individual events by selecting and event and viewing its details in the resulting flyout panel. See [Event details](#event-details) below.

#### Unified timeline \(Preview\)

**As of January 2025**, if you onboarded Microsoft Sentinel to the Defender portal, device activities that appear on the [Sentinel timeline](#sentinel-timeline) on the [*Sentinel events* tab](#sentinel-events-tab) *are also displayed* here on the main *Timeline* tab, so they can be viewed together with events recorded by other Microsoft Defender services in a single context. This unified timeline helps simplify investigations by providing a unified view of device activities, eliminating the need to toggle between screens, and enabling faster decision-making.

![Screenshot of unified device timeline.](https://learn.microsoft.com/en-us/defender-xdr/media/entity-page-device/entity-device-unified-timeline.png)

You can elect not to show events from Microsoft Sentinel in the main timeline, and instead continue to view them as before, only on the *Sentinel events* tab. To do this, select **Timeline settings** and move the **Stream events from Microsoft Sentinel queries** toggle to **Off**. Select **Apply** to save the setting.

![Screenshot of entity device timeline settings toggle.](https://learn.microsoft.com/en-us/defender-xdr/media/entity-page-device/entity-device-timeline-settings.png)

For more information about these activity events, see [Entity pages in Microsoft Sentinel](https://learn.microsoft.com/en-us/azure/sentinel/entity-pages?tabs=defender-portal#entity-pages).

Note

For firewall events to be displayed, you'll need to enable the audit policy. For instructions, see [Audit Filtering Platform connection](https://learn.microsoft.com/en-us/windows/security/threat-protection/auditing/audit-filtering-platform-connection).

Firewall covers the following events:

- [5025](https://learn.microsoft.com/en-us/windows/security/threat-protection/auditing/event-5025) - firewall service stopped
- [5031](https://learn.microsoft.com/en-us/windows/security/threat-protection/auditing/event-5031) - application blocked from accepting incoming connections on the network
- [5157](https://learn.microsoft.com/en-us/windows/security/threat-protection/auditing/event-5157) - blocked connection

[![Screenshot of the Timeline tab for the device entity page in the Microsoft Defender portal.](https://learn.microsoft.com/en-us/defender-xdr/media/entity-page-device/entity-device-timeline-tab.png)](https://learn.microsoft.com/en-us/defender-xdr/media/entity-page-device/entity-device-timeline-tab.png#lightbox)

#### Event details

Select an event to view relevant details about that event. A flyout panel displays to show much more information about the event. The types of information displayed depends on the type of event. When applicable and data is available, you might see a graph showing related entities and their relationships, like a chain of files or processes. You might also see a summary description of the MITRE ATT&CK tactics and techniques applicable to the event.

To further inspect the event and related events, you can quickly run an [advanced hunting](https://learn.microsoft.com/en-us/defender-xdr/advanced-hunting-overview) query by selecting **Hunt for related events**. The query returns the selected event and the list of other events that occurred around the same time on the same endpoint.

![Screenshot of the event details panel.](https://learn.microsoft.com/en-us/defender-xdr/media/entity-page-device/entity-device-event-details.png)

## *Configuration management* tab

### Security policies

The **Security policies** tab shows the endpoint security policies that are applied on the device. You see a list of policies, type, status, and last check-in time. Selecting the name of a policy takes you to the policy details page where you can see the policy settings status, applied devices, and assigned groups.

[![Screenshot showing the Security policies tab.](https://learn.microsoft.com/en-us/defender-endpoint/media/mde-security-policies.png)](https://learn.microsoft.com/en-us/defender-endpoint/media/mde-security-policies.png#lightbox)

### Effective settings

The **Effective settings** tab provides visibility into the actual value of each security setting and identifies the source that configured it. It lists setting names, policy types, effective values, the source of each effective value, and the last report time.

Configuration sources can include tools like Microsoft Defender for Endpoint, Group Policy, Intune, or default settings. They can also be specific registry paths, such as the MDM or Group Policy hives. If the source is a registry location, the Configured By field shows as **Unknown** along with the registry path.

Select a setting to open a side panel with more details. You see the current value, any other configuration attempts that didn’t take effect, and—for complex settings like ASR rules or AV exclusions—a breakdown of all configured rules, their sources, and any exclusions.

Note

The presented settings are AV security settings, Attack Surface Reduction rules, and exclusions, for Windows platforms.

[![Screenshot showing the Effective settings tab.](https://learn.microsoft.com/en-us/defender-endpoint/media/mde-effective-settings.png)](https://learn.microsoft.com/en-us/defender-endpoint/media/mde-effective-settings.png#lightbox)

[![Screenshot showing the opened Effective settings value tab.](https://learn.microsoft.com/en-us/defender-endpoint/media/mde-effective-settings-open.png)](https://learn.microsoft.com/en-us/defender-endpoint/media/mde-effective-settings-open.png#lightbox)

## *Security recommendations* tab

The **Security recommendations** tab lists actions you can take to protect the device. Selecting an item on this list opens a flyout where you can get instructions on how to apply the recommendation.

As with the previous tabs, the choice of displayed columns can be customized.

The default view includes columns that detail the security weaknesses addressed, the associated threat, the related component or software affected by the threat, and more. Items can be filtered by the recommendation's status.

Learn more about [security recommendations](https://learn.microsoft.com/en-us/defender-vulnerability-management/tvm-security-recommendation).

[![Screenshot of the Security recommendations tab for the device entity page.](https://learn.microsoft.com/en-us/defender-xdr/media/entity-page-device/entity-device-recommendations-tab.png)](https://learn.microsoft.com/en-us/defender-xdr/media/entity-page-device/entity-device-recommendations-tab.png#lightbox)

## *Inventories* tab

This tab displays inventories of four types of components: Software, vulnerable components, browser extensions, and certificates.

### Software inventory

This card lists software installed on the device.

The default view displays the software vendor, installed version number, number of known software weaknesses, threat insights, product code, and tags. The number of items displayed and which columns are displayed can both be customized.

Selecting an item from this list opens a flyout containing more details about the selected software, and the path and timestamp for the last time the software was found.

This list can be filtered by product code, weaknesses, and the presence of threats.

[![Screenshot of the Software inventory tab for device profile in the Microsoft Defender portal](https://learn.microsoft.com/en-us/defender-xdr/media/entity-page-device/entity-device-inventories-tab.png)](https://learn.microsoft.com/en-us/defender-xdr/media/entity-page-device/entity-device-inventories-tab.png#lightbox)

### Vulnerable components

This card lists software components that contain vulnerabilities.

The default view and filtering options are the same as for software.

Select an item to display more information in a flyout.

### Browser extensions

This card shows the browser extensions installed on the device. The default fields displayed are the extension name, the browser for which it's installed, the version, the permission risk \(based on the type of access to devices or sites requested by the extension\), and the status. Optionally, the vendor can also be displayed.

Select an item to display more information in a flyout.

### Certificates

This card displays all the certificates installed on the device.

The fields displayed by default are the certificate name, issue date, expiration date, key size, issuer, signature algorithm, key usage, and number of instances.

The list can be filtered by status, self-signed or not, key size, signature hash, and key usage.

Select a certificate to display more information in a flyout.

## *Discovered vulnerabilities* tab

This tab lists any Common Vulnerabilities and Exploits \(CVEs\) that may affect the device.

The default view lists the severity of the CVE, the Common Vulnerability Score \(CVSS\), the software related to the CVE, when the CVE was published, when the CVE was first detected and last updated, and threats associated with the CVE.

As with the previous tabs, the choice of columns to be displayed can be customized. The list can be filtered by severity, threat status, device exposure, and tags.

Selecting an item from this list opens a flyout that describes the CVE.

[![Screenshot of the Discovered vulnerabilities tab for device profile in the Microsoft Defender portal](https://learn.microsoft.com/en-us/defender-xdr/media/entity-page-device/entity-device-vulnerabilities-tab.png)](https://learn.microsoft.com/en-us/defender-xdr/media/entity-page-device/entity-device-vulnerabilities-tab.png#lightbox)

## *Missing KBs* tab

The **Missing KBs** tab lists any Microsoft Updates that have yet to be applied to the device. The "KBs" in question are [Knowledge Base articles](https://support.microsoft.com/help/242450/how-to-query-the-microsoft-knowledge-base-by-using-keywords-and-query), which describe these updates; for example, [KB4551762](https://support.microsoft.com/help/4551762/windows-10-update-kb4551762).

The default view lists the bulletin containing the updates, OS version, the KB ID number, products affected, CVEs addressed, and tags.

The choice of columns to be displayed can be customized.

Selecting an item opens a flyout that links to the update.

## *Sentinel events* tab

If your organization onboarded Microsoft Sentinel to the Defender portal, this additional tab is on the device entity page. This tab imports the [Host entity page from Microsoft Sentinel](https://learn.microsoft.com/en-us/azure/sentinel/entity-pages), and displays the following sections:

### Sentinel timeline

This timeline shows four types of messages associated with the device entity, known in Microsoft Sentinel as the *host* entity, and they can be found on the [Microsoft Sentinel entity page](https://learn.microsoft.com/en-us/azure/sentinel/entity-pages?tabs=defender-portal#the-timeline) for the device. The four message types are:

- **Alerts** created by Microsoft Sentinel [analytics rules](https://learn.microsoft.com/en-us/azure/sentinel/threat-detection) from Azure services and non-Microsoft data sources.

  These alerts are also displayed on the main [Incidents and alerts tab](#incidents-and-alerts-tab), so they can be viewed together with alerts generated by other Microsoft Defender services in a single context.
- [**Bookmarks** of hunts](https://learn.microsoft.com/en-us/azure/sentinel/bookmarks) from other Microsoft Sentinel investigations that reference this device entity.
- **Anomalies**, that is, unusual behaviors detected by Microsoft Sentinel's [anomaly rules](https://learn.microsoft.com/en-us/azure/sentinel/soc-ml-anomalies).
- **Device activities** collected from Azure services and non-Microsoft data sources. Activities are aggregations of notable events collected by queries developed by Microsoft security research teams. You can also [add your own custom activities](https://learn.microsoft.com/en-us/azure/sentinel/customize-entity-activities?tabs=defender).

  **As of January 2025:**

  - Device activities include dropped, blocked, or denied network traffic originating from a given device, based on data collected from industry-leading network device logs. These logs provide your security teams with critical information to quickly identify and address potential threats.
  - Device activities are now displayed in the **unified device timeline** alongside device events from other Defender portal sources. For more information, see [Unified timeline \(Preview\)](#unified-timeline-preview).

### Insights

Entity insights are queries defined by Microsoft security researchers to help you investigate more efficiently and effectively. These insights automatically ask the big questions about your device entity, providing valuable security information in the form of tabular data and charts. The insights include data regarding sign-ins, group additions, process executions, anomalous events and more, and include advanced machine learning algorithms to detect anomalous behavior.

The following are some of the insights shown:

- Screenshot taken on the host.
- Processes unsigned by Microsoft detected.
- Windows process execution info.
- Windows sign-in activity.
- Actions on accounts.
- Event logs cleared on host.
- Group additions.
- Enumeration of hosts, users, groups on host.
- Microsoft Defender Application Control.
- Process rarity via entropy calculation.
- Anomalously high number of a security event.
- Watchlist insights \(Preview\).
- Windows Defender Antivirus events.

The insights are based on the following data sources:

- Syslog \(Linux\)
- SecurityEvent \(Windows\)
- AuditLogs \(Microsoft Entra ID\)
- SigninLogs \(Microsoft Entra ID\)
- OfficeActivity \(Office 365\)
- BehaviorAnalytics \(Microsoft Sentinel UEBA\)
- Heartbeat \(Azure Monitor Agent\)
- CommonSecurityLog \(Microsoft Sentinel\)

![Screenshot of Sentinel events tab in user entity page.](https://learn.microsoft.com/en-us/defender-xdr/media/entity-page-device/entity-device-sentinel-events-tab.png)

If you want to further explore any of the insights in this panel, select the link accompanying the insight. The link takes you to the **Advanced hunting** page, where it displays the query underlying the insight, along with its raw results. You can modify the query or drill down into the results to expand your investigation or just satisfy your curiosity.

![Screenshot of Advanced hunting screen with insight query.](https://learn.microsoft.com/en-us/defender-xdr/media/entity-page-device/device-insights-advanced-hunting.png)

## Response actions

Response actions offer shortcuts to analyze, investigate, and defend against threats.

![Screenshot of the Action bar for the device entity page in the Microsoft Defender portal.](https://learn.microsoft.com/en-us/defender-xdr/media/entity-page-device/entity-device-response-actions.png)

Important

- [Response actions](https://learn.microsoft.com/en-us/windows/security/threat-protection/microsoft-defender-atp/respond-machine-alerts) are only available if the device is enrolled in Microsoft Defender for Endpoint.

- Devices that are enrolled in Microsoft Defender for Endpoint may display different numbers of response actions, based on the device's OS and version number.

Response actions run along the top of a specific device page and include:

| Action | Description |
| --- | --- |
| **Device value** |  |
| **Set criticality** |  |
| **Manage tags** | Updates custom tags you've applied to this device. |
| **Report device inaccuracy** |  |
| **Run Antivirus Scan** | Updates Microsoft Defender Antivirus definitions and immediately runs an antivirus scan. Choose between Quick scan or Full scan. |
| **Collect Investigation Package** | Gathers information about the device. When the investigation is completed, you can download it. |
| **Restrict app execution** | Prevents applications that aren't signed by Microsoft from running. |
| **Initiate automated investigation** | Automatically [investigates and remediates threats](https://learn.microsoft.com/en-us/defender-office-365/air-about). Although you can manually trigger automated investigations to run from this page, [certain alert policies](https://learn.microsoft.com/en-us/Microsoft-365/compliance/alert-policies#default-alert-policies) trigger automatic investigations on their own. |
| **Initiate Live Response Session** | Loads a remote shell on the device for [in-depth security investigations](https://learn.microsoft.com/en-us/defender-endpoint/live-response). |
| **Isolate device** | Isolates the device from your organization's network while keeping it connected to Microsoft Defender. You can choose to allow Outlook, Teams, and Skype for Business to run while the device is isolated, for communication purposes. |
| **Ask Defender Experts** |  |
| **Action Center** | Displays information about any response actions that are currently running. Only available if another action has already been selected. |
| **Download force release from isolation script** |  |
| **Exclude** |  |
| **Go hunt** |  |
| **Turn on troubleshooting mode** |  |
| **Policy sync** |  |

## Related topics

- [Microsoft Defender overview](https://learn.microsoft.com/en-us/defender-xdr/microsoft-365-defender)
- [Turn on Microsoft Defender XDR](https://learn.microsoft.com/en-us/defender-xdr/m365d-enable)
- [User entity page in Microsoft Defender](https://learn.microsoft.com/en-us/defender-xdr/investigate-users)
- [IP address entity page in Microsoft Defender](https://learn.microsoft.com/en-us/defender-xdr/entity-page-ip)
- [Microsoft Defender XDR integration with Microsoft Sentinel](https://learn.microsoft.com/en-us/defender-xdr/microsoft-365-defender-integration-with-azure-sentinel)
- [Connect Microsoft Sentinel to Microsoft Defender XDR](https://learn.microsoft.com/en-us/azure/sentinel/microsoft-sentinel-onboard)

Tip

Do you want to learn more? Engage with the Microsoft Security community in our Tech Community: [Microsoft Defender XDR Tech Community](https://techcommunity.microsoft.com/t5/microsoft-365-defender/bd-p/MicrosoftThreatProtection).
