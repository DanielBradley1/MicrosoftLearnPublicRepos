<!-- Source: https://learn.microsoft.com/en-us/defender-office-365/trial-user-guide-defender-for-office-365 -->
<!-- Sitemap-Last-Modified: 2025-02-24 -->

# Trial user guide: Microsoft Defender for Office 365

Tip

*Did you know you can try the features in Microsoft Defender for Office 365 Plan 2 for free?* Use the 90-day Defender for Office 365 trial at the [Microsoft Defender portal trials hub](https://security.microsoft.com/trialHorizontalHub?sku=MDO&ref=DocsRef). Learn about who can sign up and trial terms on [Try Microsoft Defender for Office 365](https://learn.microsoft.com/en-us/defender-office-365/try-microsoft-defender-for-office-365).

Welcome to the Microsoft Defender for Office 365 trial user guide! This user guide helps you make the most of your free trial by teaching you how to safeguard your organization against malicious threats posed by email messages, links \(URLs\), and collaboration tools.

## What is Defender for Office 365?

Defender for Office 365 helps organizations secure their enterprise by offering a comprehensive slate of capabilities, including threat policies, reports, threat investigation and response capabilities, and automated investigation and response capabilities.

[![Microsoft Defender for Office 365 conceptual diagram.](https://learn.microsoft.com/en-us/defender-office-365/media/microsoft-defender-for-office-365.png)](https://learn.microsoft.com/en-us/defender-office-365/media/microsoft-defender-for-office-365.png#lightbox)

In addition to the detection of advanced threats, the following video shows how the SecOps capabilities of Defender for Office 365 can help your team respond to threats:

<iframe src="https://learn-video.azurefd.net/vod/player?id=29ff5c90-7b71-468c-92b9-d1d8ca9ee8fa" allowfullscreen="true" data-linktype="external" frameborder="0"></iframe>

### Audit mode vs. blocking mode for Defender for Office 365

Do you want your Defender for Office 365 experience to be active or passive? These are the two modes that you can select from:

- **Audit mode**: Special *evaluation policies* are created for anti-phishing \(which includes impersonation protection\), Safe Attachments, and Safe Links. These evaluation policies are configured to *detect* threats only. Defender for Office 365 detects harmful messages for reporting, but the messages aren't acted upon \(for example, detected messages aren't quarantined\). The settings of these evaluation policies are described in the [Policies in audit mode](https://learn.microsoft.com/en-us/defender-office-365/try-microsoft-defender-for-office-365#policies-in-audit-mode) section later in this article.

  Audit mode provides access to customized reports for threats detected by the evaluation policies in Defender for Office 365 on the **Microsoft Defender for Office 365 evaluation** page at [https://security.microsoft.com/atpEvaluation](https://security.microsoft.com/atpEvaluation).
- **Blocking mode**: The Standard template for [preset security policies](https://learn.microsoft.com/en-us/defender-office-365/preset-security-policies#profiles-in-preset-security-policies) is turned on and used for the trial, and the users you specify to include in the trial are added to the Standard preset security policy. Defender for Office 365 *detects* and *takes action on* harmful messages \(for example, detected messages are quarantined\).

  The default and recommended selection is to scope these Defender for Office 365 policies to all users in the organization. But, during or after the setup of your trial, you can change the policy assignment to specific users, groups, or email domains in the Microsoft Defender portal or in [Exchange Online PowerShell](https://learn.microsoft.com/en-us/powershell/exchange/connect-to-exchange-online-powershell).

  Blocking mode doesn't provide customized reports for threats detected by Defender for Office 365. Instead, the information is available in the regular reports and investigation features of Defender for Office 365 Plan 2. For more information, see [Reports for blocking mode](https://learn.microsoft.com/en-us/defender-office-365/try-microsoft-defender-for-office-365#reports-for-blocking-mode).

The key factors that determine which modes are available to you are:

- Whether or not you currently have Defender for Office 365 \(Plan 1 or Plan 2\) as described in [Evaluation vs. trial for Defender for Office 365](https://learn.microsoft.com/en-us/defender-office-365/try-microsoft-defender-for-office-365#evaluation-vs-trial-for-defender-for-office-365).
- How email is delivered to your Microsoft 365 organization as described in the following scenarios:

  - Mail from the internet flows directly into Microsoft 365, but your current subscription has [the built-in security features for all cloud mailboxes](https://learn.microsoft.com/en-us/defender-office-365/eop-about) only or [Defender for Office 365 Plan 1](https://learn.microsoft.com/en-us/defender-office-365/mdo-about#defender-for-office-365-plan-1-vs-plan-2-cheat-sheet).

    [![Mail flows from the internet into Microsoft 365, with the built-in security features for all cloud mailboxes and/or Defender for Office 365 Plan 1.](https://learn.microsoft.com/en-us/defender-office-365/media/mdo-trial-mail-flow.png)](https://learn.microsoft.com/en-us/defender-office-365/media/mdo-trial-mail-flow.png#lightbox)

    In these environments, **audit mode** or **blocking mode** are available, [depending on your licensing](https://learn.microsoft.com/en-us/defender-office-365/try-microsoft-defender-for-office-365#evaluation-vs-trial-for-defender-for-office-365).
  - You're currently using a non-Microsoft service or device for email protection of your cloud mailboxes. Mail from the internet flows through the protection service before delivery into your Microsoft 365 organization. Microsoft 365 protection is as low as possible \(it's never completely off; for example, malware protection is always enforced\).

    [![Mail flows from the internet through the non-Microsoft protection service or device before delivery into Microsoft 365.](https://learn.microsoft.com/en-us/defender-office-365/media/mdo-migration-before.png)](https://learn.microsoft.com/en-us/defender-office-365/media/mdo-migration-before.png#lightbox)

    In these environments, only **audit mode** is available. You don't need to change your mail flow \(MX records\) to evaluate Defender for Office 365 Plan 2.

Let's get started!

## Blocking mode

### Step 1: Getting started in blocking mode

#### Start your Microsoft Defender for Office 365 trial

After you've initiated the trial and completed the [setup process](https://learn.microsoft.com/en-us/defender-office-365/try-microsoft-defender-for-office-365#set-up-an-evaluation-or-trial-in-blocking-mode), it may take up to 2 hours for changes to take effect.

We've automatically enabled the [Standard preset security policy](https://learn.microsoft.com/en-us/defender-office-365/preset-security-policies) in your environment. This profile represents a baseline protection profile that's suitable for most users. Standard protection includes:

- Safe Links, Safe Attachments and anti-phishing policies that are scoped to the entire tenant or subset of users you may have chosen during the trial setup process.
- Safe Attachments protection for SharePoint, OneDrive, and Microsoft Teams.
- Safe Links protection for supported Office 365 apps.

Watch this video to learn more: [Protect against malicious links with Safe Links in Microsoft Defender for Office 365 - YouTube](https://www.youtube.com/watch?v=vhIJ1Veq36Y&list=PL3ZTgFEc7LystRja2GnDeUFqk44k7-KXf&index=9).

#### Enable users to report suspicious content in blocking mode

Defender for Office 365 enables users to report messages to their security teams and allows admins to submit messages to Microsoft for analysis.

- Verify or configure [user reported settings](https://learn.microsoft.com/en-us/defender-office-365/submissions-user-reported-messages-custom-mailbox) so reported messages go to a specified reporting mailbox, to Microsoft, or both.
- Use the built-in **Report** button in [supported versions of Outlook](https://learn.microsoft.com/en-us/defender-office-365/submissions-outlook-report-messages#use-the-built-in-report-button-in-outlook) for users to report messages.
- Establish a workflow to [Report false positives and false negatives](https://learn.microsoft.com/en-us/defender-office-365/submissions-outlook-report-messages).
- Use the **User reported** tab on the **Submissions** page at [https://security.microsoft.com/reportsubmission?viewid=user](https://security.microsoft.com/reportsubmission?viewid=user) to see and manage user reported messages.

Watch this video to learn more: [Learn how to use the Submissions page to submit messages for analysis - YouTube](https://www.youtube.com/watch?v=ta5S09Yz6Ks&ab_channel=MicrosoftSecurit).

#### Review reports to understand the threat landscape in blocking mode

Use the reporting capabilities in Defender for Office 365 to get more details about your environment.

- Understand threats received in email and collaboration tools with the [Threat protection status report](https://learn.microsoft.com/en-us/defender-office-365/reports-email-security#threat-protection-status-report).
- See where threats are blocked with the [Mailflow status report](https://learn.microsoft.com/en-us/defender-office-365/reports-email-security#mailflow-status-report).
- Use the [URL protection report](https://learn.microsoft.com/en-us/defender-office-365/reports-defender-for-office-365#url-protection-report) to review links that were viewed by users or blocked by the system.

[![The Email & collaboration reports in the Microsoft Defender portal.](https://learn.microsoft.com/en-us/defender-office-365/media/mdo-trial-playbook-reporting.png)](https://learn.microsoft.com/en-us/defender-office-365/media/mdo-trial-playbook-reporting.png#lightbox)

### Step 2: Intermediate steps in blocking mode

#### Prioritize focus on your most targeted users

Protect your most targeted and most visible users with Priority Account Protection in Defender for Office 365, which helps you prioritize your workflow to ensure these users are safe.

- Identify your most targeted or most visible users.
- [Tag these users](https://learn.microsoft.com/en-us/microsoft-365/admin/setup/priority-accounts#add-priority-accounts-from-the-microsoft-365-defender-page) as priority accounts.
- Track threats to priority accounts throughout the portal.

Watch this video to learn more: [Protecting priority accounts in Microsoft Defender for Office 365 - YouTube](https://www.youtube.com/watch?v=tqnj0TlzQcI&list=PL3ZTgFEc7LystRja2GnDeUFqk44k7-KXf&index=11).

[![The Alerts in the Microsoft Defender portal.](https://learn.microsoft.com/en-us/defender-office-365/media/mdo-trial-playbook-alerts.png)](https://learn.microsoft.com/en-us/defender-office-365/media/mdo-trial-playbook-alerts.png#lightbox)

### Avoid costly breaches by preventing user compromise

Get alerted to potential compromise and automatically limit the impact of these threats to prevent attackers from gaining deeper access to your environment.

- Review [compromised user alerts](https://learn.microsoft.com/en-us/defender-office-365/address-compromised-users-quickly#compromised-user-alerts).
- [Investigate and respond](https://learn.microsoft.com/en-us/defender-office-365/address-compromised-users-quickly) to compromised users.

[![The Investigate compromised users.](https://learn.microsoft.com/en-us/defender-office-365/media/mdo-trial-playbook-investigation.png)](https://learn.microsoft.com/en-us/defender-office-365/media/mdo-trial-playbook-investigation.png#lightbox)

Watch this video to learn more: [Detect and respond to compromise in Microsoft Defender for Office 365 - YouTube](https://www.youtube.com/watch?v=Pc7y3a-wdR0&list=PL3ZTgFEc7LystRja2GnDeUFqk44k7-KXf&index=5).

#### Use Threat Explorer to investigate malicious email

Defender for Office 365 enables you to investigate activities that put people in your organization at risk and to take action to protect your organization. You can do this using [Threat Explorer \(Explorer\)](https://learn.microsoft.com/en-us/defender-office-365/threat-explorer-real-time-detections-about):

- [Find suspicious email that was delivered](https://learn.microsoft.com/en-us/defender-office-365/threat-explorer-investigate-delivered-malicious-email#find-suspicious-email-that-was-delivered): Find and delete messages, identify the IP address of a malicious email sender, or start an incident for further investigation.
- [Email security scenarios in Threat Explorer and Real-time detections](https://learn.microsoft.com/en-us/defender-office-365/threat-explorer-threat-hunting#email-security-scenarios-in-threat-explorer-and-real-time-detections)

#### See campaigns targeting your organization

See the bigger picture with Campaign Views in Defender for Office 365, which gives you a view of the attack campaigns targeting your organization and the impact they have on your users.

- [Identify campaigns](https://learn.microsoft.com/en-us/defender-office-365/campaigns#what-is-a-campaign) targeting your users.
- [Visualize the scope](https://learn.microsoft.com/en-us/defender-office-365/campaigns#campaigns-page-in-the-microsoft-defender-portal) of the attack.
- [Track user interaction](https://learn.microsoft.com/en-us/defender-office-365/campaigns#campaign-details) with these messages.

  [![The Campaign details in the Microsoft Defender portal.](https://learn.microsoft.com/en-us/defender-office-365/media/mdo-trial-playbook-campaign-details.png)](https://learn.microsoft.com/en-us/defender-office-365/media/mdo-trial-playbook-campaign-details.png#lightbox)

Watch this video to learn more: [Campaign Views in Microsoft Defender for Office 365 - YouTube](https://www.youtube.com/watch?v=DvqzzYKu7cQ&list=PL3ZTgFEc7LystRja2GnDeUFqk44k7-KXf&index=14).

#### Use automation to remediate risks

Respond efficiently using Automated investigation and response \(AIR\) to review, prioritize, and respond to threats.

- [Learn more](https://learn.microsoft.com/en-us/defender-office-365/air-examples) about investigation user guides.
- [View details and results](https://learn.microsoft.com/en-us/defender-office-365/email-analysis-investigations) of an investigation.
- Eliminate threats by [approving remediation actions](https://learn.microsoft.com/en-us/defender-office-365/air-remediation-actions).

[![The investigation results.](https://learn.microsoft.com/en-us/defender-office-365/media/mdo-trial-playbook-investigation-results.png)](https://learn.microsoft.com/en-us/defender-office-365/media/mdo-trial-playbook-investigation-results.png#lightbox)

### Step 3: Advanced content in blocking mode

#### Dive deep into data with query-based hunting

Use Advanced hunting to write custom detection rules, proactively inspect events in your environment, and locate threat indicators. Explore raw data in your environment.

- [Build custom detection rules](https://learn.microsoft.com/en-us/defender-xdr/custom-detections-overview).
- [Access shared queries](https://learn.microsoft.com/en-us/defender-xdr/advanced-hunting-shared-queries) created by others.

Watch this video to learn more: [Threat hunting with Microsoft Defender XDR - YouTube](https://www.youtube.com/watch?v=l3OmH4U6XAs&list=PL3ZTgFEc7Lyt1O81TZol31YXve4e6lyQu&index=4).

#### Train users to spot threats by simulating attacks

Equip your users with the right knowledge to identify threats and report suspicious messages with Attack simulation training in Defender for Office 365.

- [Simulate realistic threats](https://learn.microsoft.com/en-us/defender-office-365/attack-simulation-training-simulations) to identify vulnerable users.
- [Assign training](https://learn.microsoft.com/en-us/defender-office-365/attack-simulation-training-simulations#assign-training) to users based on simulation results.
- [Track progress](https://learn.microsoft.com/en-us/defender-office-365/attack-simulation-training-insights) of your organization in simulations and training completion.

  [![The attack simulation training insights in the Microsoft Defender portal.](https://learn.microsoft.com/en-us/defender-office-365/media/mdo-trial-playbook-attack-simulation-training-results.png)](https://learn.microsoft.com/en-us/defender-office-365/media/mdo-trial-playbook-attack-simulation-training-results.png#lightbox)

## Auditing mode

### Step 1: Get started in auditing mode

#### Start your Defender for Office 365 evaluation

After you've completed the [setup process](https://learn.microsoft.com/en-us/defender-office-365/try-microsoft-defender-for-office-365#set-up-an-evaluation-or-trial-in-audit-mode), it may take up to 2 hours for changes to take effect. We've automatically configured Preset Evaluation policies in your environment.

Evaluation policies ensure no action is taken on email that's detected by Defender for Office 365.

#### Enable users to report suspicious content in auditing mode

Defender for Office 365 enables users to report messages to their security teams and allows admins to submit messages to Microsoft for analysis.

- Verify or configure [user reported settings](https://learn.microsoft.com/en-us/defender-office-365/submissions-user-reported-messages-custom-mailbox) so reported messages go to a specified reporting mailbox, to Microsoft, or both.
- Use the built-in **Report** button in [supported versions of Outlook](https://learn.microsoft.com/en-us/defender-office-365/submissions-outlook-report-messages#use-the-built-in-report-button-in-outlook) for users to report messages.
- Establish a workflow to [Report false positives and false negatives](https://learn.microsoft.com/en-us/defender-office-365/submissions-outlook-report-messages).
- Use the **User reported** tab on the **Submissions** page at [https://security.microsoft.com/reportsubmission?viewid=user](https://security.microsoft.com/reportsubmission?viewid=user) to see and manage user reported messages.

Watch this video to learn more: [Learn how to use the Submissions page to submit messages for analysis - YouTube](https://www.youtube.com/watch?v=ta5S09Yz6Ks&ab_channel=MicrosoftSecurit).

#### Review reports to understand the threat landscape in auditing mode

Use the reporting capabilities in Defender for Office 365 to get more details about your environment.

- The [Evaluation dashboard](https://learn.microsoft.com/en-us/defender-office-365/try-microsoft-defender-for-office-365#reports-for-audit-mode) provides an easy view of the threats detected by Defender for Office 365 during evaluation.
- Understand threats received in email and collaboration tools with the [Threat protection status report](https://learn.microsoft.com/en-us/defender-office-365/reports-email-security#threat-protection-status-report).

### Step 2: Intermediate steps in auditing mode

#### Use Threat Explorer to investigate malicious email in auditing mode

Defender for Office 365 enables you to investigate activities that put people in your organization at risk and to take action to protect your organization. You can do this using [Threat Explorer \(Explorer\)](https://learn.microsoft.com/en-us/defender-office-365/threat-explorer-real-time-detections-about):

- [Find suspicious email that was delivered](https://learn.microsoft.com/en-us/defender-office-365/threat-explorer-investigate-delivered-malicious-email#find-suspicious-email-that-was-delivered): Find and delete messages, identify the IP address of a malicious email sender, or start an incident for further investigation.
- [Email security scenarios in Threat Explorer and Real-time detections](https://learn.microsoft.com/en-us/defender-office-365/threat-explorer-threat-hunting#email-security-scenarios-in-threat-explorer-and-real-time-detections)

#### Convert to Standard Protection at the end of evaluation period

When you're ready to turn on Defender for Office 365 policies in production, you can use [Convert to Standard Protection](https://learn.microsoft.com/en-us/defender-office-365/try-microsoft-defender-for-office-365#convert-to-standard-protection) to easily move from audit mode to blocking mode by turning on the [Standard preset security policy](https://learn.microsoft.com/en-us/defender-office-365/preset-security-policies#profiles-in-preset-security-policies), which contains any/all recipients from audit mode.

#### Migrate from a non-Microsoft protection service or device to Defender for Office 365

If you already have an existing non-Microsoft protection service or device that sits in front of Microsoft 365, you can migrate your protection to Microsoft Defender for Office 365 to get the benefits of a consolidated management experience, potentially reduced cost \(using products that you already pay for\), and a mature product with integrated security protection.

For more information, see [Migrate from a non-Microsoft protection service or device to Microsoft Defender for Office 365](https://learn.microsoft.com/en-us/defender-office-365/migrate-to-defender-for-office-365).

### Step 3: Advanced content in auditing mode

#### Train users to spot threats by simulating attacks in auditing mode

Equip your users with the right knowledge to identify threats and report suspicious messages with Attack simulation training in Defender for Office 365.

- [Simulate realistic threats](https://learn.microsoft.com/en-us/defender-office-365/attack-simulation-training-simulations) to identify vulnerable users.
- [Assign training](https://learn.microsoft.com/en-us/defender-office-365/attack-simulation-training-simulations#assign-training) to users based on simulation results.
- [Track progress](https://learn.microsoft.com/en-us/defender-office-365/attack-simulation-training-insights) of your organization in simulations and training completion.

  [![The attack simulation training insights in the Microsoft Defender portal.](https://learn.microsoft.com/en-us/defender-office-365/media/mdo-trial-playbook-attack-simulation-training-results.png)](https://learn.microsoft.com/en-us/defender-office-365/media/mdo-trial-playbook-attack-simulation-training-results.png#lightbox)

## Additional resources

- **Interactive guide**: Unfamiliar with Defender for Office 365? Review the [interactive guide](https://mslearn.cloudguides.com/guides/Safeguard%20your%20organization%20with%20Microsoft%20Defender%20for%20Office%20365) to understand how to get started.
- **Fast Track Get Started Guide**: [Microsoft Defender for Office 365](https://go.microsoft.com/fwlink/p/?linkid=2197415)
- **Microsoft Defender for Office 365 documentation**: Get detailed information on how Defender for Office 365 works and how to best implement it for your organization. Visit the [Microsoft Defender for Office 365 documentation](https://learn.microsoft.com/en-us/defender-office-365/mdo-about).
- **What's included**: For a full list of Office 365 email security features listed by product tier, view the [Feature Matrix](https://learn.microsoft.com/en-us/office365/servicedescriptions/office-365-advanced-threat-protection-service-description#feature-availability).
- **Why Defender for Office 365**: The [Defender for Office 365 Datasheet](https://cdn-dynmedia-1.microsoft.com/is/content/microsoftcorp/microsoft/final/en-us/microsoft-brand/documents/Defender-For-Office-365-Datasheet.pdf) shows the top 10 reasons customers choose Microsoft.
