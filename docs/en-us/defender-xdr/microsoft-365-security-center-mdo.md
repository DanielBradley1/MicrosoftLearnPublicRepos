<!-- Source: https://learn.microsoft.com/en-us/defender-xdr/microsoft-365-security-center-mdo -->
<!-- Sitemap-Last-Modified: 2026-07-29 -->

# Microsoft Defender for Office 365 in the Microsoft Defender portal

**Applies to:**

- [Microsoft Defender XDR](https://learn.microsoft.com/en-us/defender-xdr/microsoft-365-defender)
- [Microsoft Defender for Office 365 Plan 1 and Plan 2](https://learn.microsoft.com/en-us/defender-office-365/mdo-about#defender-for-office-365-plan-1-vs-plan-2-cheat-sheet)

This article describes the Microsoft Defender for Office 365 experience in the Microsoft Defender portal at [https://security.microsoft.com](https://security.microsoft.com). Formerly, Defender for Office 365 customers used the Office 365 Security & Compliance Center at [https://protection.office.com](https://protection.office.com), but access to that portal ended in 2022.

The Defender portal combines security capabilities from existing Microsoft 365 security portals. This improved portal helps security teams protect their organization from threats more effectively and efficiently.

For more information about the benefits of Microsoft Defender, see [Overview of Defender](https://learn.microsoft.com/en-us/defender-xdr/microsoft-365-defender).

If you're looking for compliance-related items, see [Microsoft Purview portal](https://learn.microsoft.com/en-us/purview/purview-compliance-portal).

## Capabilities

With the unified Defender XDR solution, you can stitch together the threat signals and determine the full scope of the threat, and how it currently affects the organization.

[![A screenshot of the left navigation pane of the Microsoft 365 Defender portal.](https://learn.microsoft.com/en-us/defender-xdr/media/microsoft-365-security-center-mdo/mdo-m36d-nav-collapsed.png)](https://learn.microsoft.com/en-us/defender-xdr/media/microsoft-365-security-center-mdo/mdo-m36d-nav-collapsed.png#lightbox)

Defender for Office 365 safeguards your organization against malicious threats posed by email messages, links \(URLs\), and collaboration tools. Most Defender for Office 365 specific features are available under the **Email & collaboration** node as described in the [Email & collaboration](#email--collaboration) section.

[![A screenshot that shows the Email & collaboration node expanded in the Defender portal.](https://learn.microsoft.com/en-us/defender-xdr/media/mdo-m365d-nav.png)](https://learn.microsoft.com/en-us/defender-xdr/media/mdo-m365d-nav.png#lightbox)

Tip

- Defender for Office 365 includes the built-in security features for all cloud mailboxes. For more information, see [Built-in security features for all cloud mailboxes](https://learn.microsoft.com/en-us/defender-office-365/eop-about).
- What you see or don't see in the Defender portal depends on your subscription \(for example, Microsoft 365 E5 vs. an add-on or standalone Defender for Office 365 Plan 2 subscription\).

  For more information about the differences between Defender for Office 365 Plan 1 and Plan 2, see [Defender for Office 365 Plan 1 vs. Plan 2 cheat sheet](https://learn.microsoft.com/en-us/defender-office-365/mdo-about#defender-for-office-365-plan-1-vs-plan-2-cheat-sheet).

### Home

The **Home** page of the Defender portal shows important summary information \(cards\) about the security status of your Microsoft 365 environment.

- Use ![](https://learn.microsoft.com/en-us/defender-xdr/media/defender-portal-icon-guided-tour.png) **Guided tour** to take a quick tour of:

  - Email & collaboration
  - Attack simulation training \(Defender for Office 365 Plan 2 only\)

- Use ![](https://learn.microsoft.com/en-us/defender-xdr/media/defender-portal-icon-take-actions.png) **What's New** to go to the [Microsoft Defender XDR Blog](https://techcommunity.microsoft.com/t5/microsoft-defender-xdr-blog/bg-p/MicrosoftThreatProtectionBlog).
- Use ![](https://learn.microsoft.com/en-us/defender-xdr/media/defender-portal-icon-community.png) **Community** to go to the [Security, Compliance, and Identity community](https://techcommunity.microsoft.com/t5/security-compliance-and-identity/ct-p/MicrosoftSecurityandCompliance).
- Use ![](https://learn.microsoft.com/en-us/defender-xdr/media/defender-portal-icon-create.png) **Add cards** to customize the information on the page.

### Investigation & response

The following subsections describe the features that are available in the **Investigation & response** node in the Defender portal.

[![A screenshot showing the expanded Investigation & response node in the Defender portal.](https://learn.microsoft.com/en-us/defender-xdr/media/microsoft-365-security-center-mdo/m365d-investigation-and-response-nav.png)](https://learn.microsoft.com/en-us/defender-xdr/media/microsoft-365-security-center-mdo/m365d-investigation-and-response-nav.png#lightbox)

#### Incidents & alerts

Brings together incident and alert management across your email, devices, and identities. Alerts are now available under the Investigation node, and help provide a broader view of an attack. The alert page provides full context to the alert, by combining attack signals to construct a detailed story. Previously, alerts were specific to different workloads. A new, unified experience now brings together a consistent view of alerts across workloads. You can quickly triage, investigate, and take effective action. For more information, see the following articles:

- [Incident response in the Microsoft Defender portal](https://learn.microsoft.com/en-us/defender-xdr/incidents-overview)
- [Alerts queue in Microsoft Defender XDR](https://learn.microsoft.com/en-us/defender-endpoint/alerts-queue-endpoint-detection-response)

Tip

**Email & collaboration alerts** at [https://security.microsoft.com/viewalertsv2](https://security.microsoft.com/viewalertsv2) is available in Defender for Office 365 Plan 1 only.

#### Hunting

Proactively search for threats, malware, and malicious activity across your endpoints, Microsoft 365 mailboxes, and more by using [advanced hunting queries](https://learn.microsoft.com/en-us/defender-xdr/advanced-hunting-overview). You can use these powerful queries to locate and review threat indicators and entities for known and potential threats.

You can build [custom detection rules](https://learn.microsoft.com/en-us/windows/security/threat-protection/microsoft-defender-atp/custom-detection-rules) from advanced hunting queries to proactively monitor events that might indicate breach activity and misconfigured devices.

### Actions & submissions

**Action center** shows you the investigations created by automated investigation and response capabilities. This automated, self-healing capability in the Defender portal can help security teams by automatically responding to specific events.

For more information, see [Action center](https://learn.microsoft.com/en-us/defender-xdr/m365d-action-center).

Admins can use the **Submissions** page to submit email messages, email attachments, and URLs to Microsoft for analysis. Messages reported as **Junk**, **Not junk**, or \*\*Phishing by users in Outlook are also available to review or resubmit to Microsoft.

For more information, see [Admin submissions](https://learn.microsoft.com/en-us/defender-office-365/submissions-admin).

### Threat intelligence in Defender for Office 365 Plan 2

The following subsections describe the features that are available in the **Threat intelligence** node in the Defender portal in organizations with Defender for Office 365 Plan 2.

[![A screenshot showing the expanded Threat intelligence node in the Defender portal.](https://learn.microsoft.com/en-us/defender-xdr/media/microsoft-365-security-center-mdo/m365d-threat-intelligence-nav.png)](https://learn.microsoft.com/en-us/defender-xdr/media/microsoft-365-security-center-mdo/m365d-threat-intelligence-nav.png#lightbox)

#### Threat Analytics

Get threat intelligence from expert Microsoft security researchers. Threat Analytics helps security teams be more efficient when facing emerging threats. Threat Analytics includes:

- Email-related detections and mitigations from Microsoft Defender for Office 365.
- Incidents view related to the threats.
- Enhanced experience for quickly identifying and using actionable information in the reports.

You can access Threat analytics either from the left navigation pane in the Defender portal, or from a dedicated dashboard card that shows the top threats for your organization.

For more information, see [Threat analytics in Microsoft Defender](https://learn.microsoft.com/en-us/defender-xdr/threat-analytics).

### Email & collaboration

The **Email & collaboration** node contains features that are specific to Defender for Office 365:

- **Investigations**: Defender for Office 365 Plan 2 only. For more information, see [Automated investigation and response \(AIR\)](https://learn.microsoft.com/en-us/defender-office-365/air-about).
- **Explorer \(Threat Explorer\)**: Defender for Office 365 Plan 2 only. Defender for Office 365 Plan 1 has **Real-time detections** instead. For more information, see [About Threat Explorer and Real-time detections](https://learn.microsoft.com/en-us/defender-office-365/threat-explorer-real-time-detections-about).
- **Review** at [https://security.microsoft.com/threatreview](https://security.microsoft.com/threatreview) contains the following features:

  - [Action center](https://learn.microsoft.com/en-us/defender-xdr/m365d-action-center): Defender for Office 365 Plan 2 only.
  - **Quarantine** for [users](https://learn.microsoft.com/en-us/defender-office-365/quarantine-end-user) and [admins](https://learn.microsoft.com/en-us/defender-office-365/quarantine-admin-manage-messages-files).
  - **Restricted entities**: Contains [restricted users](https://learn.microsoft.com/en-us/defender-office-365/outbound-spam-restore-restricted-users) and [restricted connectors](https://learn.microsoft.com/en-us/defender-office-365/connectors-detect-respond-to-compromise).
  - **Malware trends**

- [Campaigns](https://learn.microsoft.com/en-us/defender-office-365/campaigns): Defender for Office 365 Plan 2 only.
- [Threat trackers](https://learn.microsoft.com/en-us/defender-office-365/threat-trackers): Defender for Office 365 Plan 2 only.
- [Exchange message trace](https://learn.microsoft.com/en-us/defender-office-365/message-trace-defender-portal)
- [Attack simulation training](https://learn.microsoft.com/en-us/defender-office-365/attack-simulation-training-get-started): Defender for Office 365 Plan 2 only.
- **Policies & rules** at [https://security.microsoft.com/securitypoliciesandrules](https://security.microsoft.com/securitypoliciesandrules) contains the following features:

  - **Threat policies**:

    - **Templated policies** section:

      - [Preset security policies](https://learn.microsoft.com/en-us/defender-office-365/preset-security-policies)
      - [Configuration analyzer](https://learn.microsoft.com/en-us/defender-office-365/configuration-analyzer-for-security-policies)

    - **Policies** section:

      - [Anti-phishing](https://learn.microsoft.com/en-us/defender-office-365/anti-phishing-policies-about)
      - **Anti-spam**: Includes [inbound anti-spam](https://learn.microsoft.com/en-us/defender-office-365/anti-spam-protection-about#anti-spam-policies), [outbound anti-spam](https://learn.microsoft.com/en-us/defender-office-365/outbound-spam-policies-configure), and [connection filtering](https://learn.microsoft.com/en-us/defender-office-365/connection-filter-policies-configure).
      - [Anti-malware](https://learn.microsoft.com/en-us/defender-office-365/anti-malware-protection-about#anti-malware-policies)
      - [Safe Attachments](https://learn.microsoft.com/en-us/defender-office-365/safe-attachments-about)
      - [Safe Links](https://learn.microsoft.com/en-us/defender-office-365/safe-links-about)

    - **Rules** section:

      - [Tenant Allow/Block List](https://learn.microsoft.com/en-us/defender-office-365/tenant-allow-block-list-about)
      - **Email authentication settings**: Settings for [trusted ARC sealers](https://learn.microsoft.com/en-us/defender-office-365/email-authentication-arc-configure) and [DKIM](https://learn.microsoft.com/en-us/defender-office-365/email-authentication-dkim-configure).
      - [Advanced delivery](https://learn.microsoft.com/en-us/defender-office-365/advanced-delivery-policy-configure)
      - [Enhanced filtering](https://learn.microsoft.com/en-us/Exchange/mail-flow-best-practices/use-connectors-to-configure-mail-flow/enhanced-filtering-for-connectors)
      - [Quarantine policies](https://learn.microsoft.com/en-us/defender-office-365/quarantine-policies)

  - [Alert policies](https://learn.microsoft.com/en-us/defender-xdr/alert-policies)

[![A screenshot that shows the left navigation pane of the Defender portal focused on Email & collaboration.](https://learn.microsoft.com/en-us/defender-xdr/media/mdo-m365d-nav.png)](https://learn.microsoft.com/en-us/defender-xdr/media/mdo-m365d-nav.png#lightbox)

Tip

For more information about the differences between Defender for Office 365 Plan 1 and Plan 2, see [Defender for Office 365 Plan 1 vs. Plan 2 cheat sheet](https://learn.microsoft.com/en-us/defender-office-365/mdo-about#defender-for-office-365-plan-1-vs-plan-2-cheat-sheet).

Although it isn't directly accessible from the left navigation pane in the Defender portal, the **Email entity page** in Defender for Office 365 *unifies* and *centralizes* email information to empower admins and security operations \(SecOps\) teams to quickly understand and act on email threats. For more information, see [The Email entity page](https://learn.microsoft.com/en-us/defender-office-365/mdo-email-entity-page).

### SOC optimization

For more information, see [SOC optimization reference of recommendations](https://learn.microsoft.com/en-us/azure/sentinel/soc-optimization/soc-optimization-reference).

### Reports

Defender for Office 365 reports are available on the **Reports** page at [https://security.microsoft.com/securityreports](https://security.microsoft.com/securityreports) > **Email & collaboration** section > **Email & collaboration reports**.

For more information, see the following articles:

- [Email security report](https://learn.microsoft.com/en-us/defender-office-365/reports-email-security)
- [Defender for Office 365 reports](https://learn.microsoft.com/en-us/defender-office-365/reports-defender-for-office-365)

### Learning hub

Redirects to the [Microsoft Defender learning paths](https://learn.microsoft.com/en-us/training/defender/).

### Trials

Start trials of eligible Defender security products and Microsoft Purview compliance products.

Organizations with Defender for Office 365 Plan 1 can start a trial of Defender for Office 365 Plan 2. For more information, see [Trial user guide: Microsoft Defender for Office 365](https://learn.microsoft.com/en-us/defender-office-365/trial-user-guide-defender-for-office-365).

### System

The following subsections describe the features that are available in the **System** node in the Defender portal.

[![A screenshot showing the expanded System node in the Defender portal.](https://learn.microsoft.com/en-us/defender-xdr/media/microsoft-365-security-center-mdo/m365d-system-nav.png)](https://learn.microsoft.com/en-us/defender-xdr/media/microsoft-365-security-center-mdo/m365d-system-nav.png#lightbox)

#### Audit

[Audit log search](https://learn.microsoft.com/en-us/purview/audit-search) and [audit log retention policies](https://learn.microsoft.com/en-us/purview/audit-log-retention-policies).

#### Permissions

- [Microsoft Defender Unified role-based access control \(RBAC\)](https://learn.microsoft.com/en-us/defender-xdr/manage-rbac)
- **Microsoft Entra ID**. You can view information about the roles that are shown, but you can't manage role membership here. The details flyout of each role contains a link to the **Users** page in Microsoft Entra where you can add users to roles.
- [Email & collaboration roles](https://learn.microsoft.com/en-us/defender-office-365/scc-permissions)

#### Health

- **Service health**: View the health status of the Microsoft 365 services that are included in your company's subscription.
- **Message center**: The [Microsoft 365 Message center](https://learn.microsoft.com/en-us/microsoft-365/admin/manage/message-center) in the Microsoft 365 admin center.

#### Settings

**Email & collaboration** contains the following Defender for Office 365 features:

- [User reported settings](https://learn.microsoft.com/en-us/defender-office-365/submissions-user-reported-messages-custom-mailbox)
- [User tags](https://learn.microsoft.com/en-us/defender-office-365/user-tags-about)
- [Priority account protection](https://learn.microsoft.com/en-us/defender-office-365/priority-accounts-turn-on-priority-account-protection) \(Defender for Office 365 Plan 2 only\)
- [Microsoft Teams protection](https://learn.microsoft.com/en-us/defender-office-365/mdo-support-teams-about#configure-zap-for-teams-protection-in-defender-for-office-365-plan-2) \(Defender for Office 365 Plan 2 only\)

## Related information

- [The Action center](https://learn.microsoft.com/en-us/defender-xdr/m365d-action-center)
- [Email & collaboration alerts](https://learn.microsoft.com/en-us/Microsoft-365/compliance/alert-policies#default-alert-policies)
- [Custom detection rules](https://learn.microsoft.com/en-us/defender-xdr/custom-detection-rules)
- [Create a phishing attack simulation](https://learn.microsoft.com/en-us/defender-office-365/attack-simulation-training-simulations) and [create a payload for training your people](https://learn.microsoft.com/en-us/defender-office-365/attack-simulation-training-payloads)

Tip

Do you want to learn more? Engage with the Microsoft Security community in our Tech Community: [Microsoft Defender XDR Tech Community](https://techcommunity.microsoft.com/t5/microsoft-365-defender/bd-p/MicrosoftThreatProtection).
