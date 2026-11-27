<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/baseline-security-mode/block-chats-initiated-by-teams-free-accounts?view=o365-worldwide -->
<!-- Sitemap-Last-Modified: 2026-11-17 -->

# Block chats initiated by Teams free accounts

Chats initiated from Teams Free \(consumer\) accounts originate outside your organization's authentication, compliance, and threat protection boundaries. Because Microsoft Entra doesn't govern these unmanaged identities, attackers can use them to deliver unsolicited messages, impersonation attempts, or social engineering lures. Allowing inbound chat from Teams Free accounts increases the risk of phishing, spam outreach, and accidental exposure of sensitive information.

Microsoft Teams enforces this control using the **EnableTeamsConsumerInbound** setting in the external access policy. When disabled, Teams blocks inbound chat requests from consumer Teams identities at the service boundary, ensuring users can't override the restriction through client settings or user level policies. This setting maintains a trusted communication channel by limiting chat interactions to verified organizational identities.

You need to be a member of the [Global administrator role](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#global-administrator) or [Teams administrator role](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#teams-administrator) to be able to configure this setting.

For more information, see [EnableTeamsConsumerInbound in the Set CsExternalAccessPolicy PowerShell documentation](https://learn.microsoft.com/en-us/powershell/module/microsoftteams/set-csexternalaccesspolicy?#-enableteamsconsumerinbound).

## Why this setting matters

Teams consumer accounts aren't managed by an organization and do not enforce the same identity assurance, auditing, or compliance controls as enterprise identities. Allowing these accounts to initiate conversations creates an untrusted inbound communication path. This setting helps mitigate those risks by:

- **Blocking inbound communication from unmanaged identities** When disabled, Teams prevents consumer \(Teams Free\) accounts from initiating chats with users in your organization. This configuration reduces exposure to phishing, spam, and impersonation attempts.
- **Reducing social engineering attack surface** Attackers can easily create Teams Free accounts. Preventing inbound initiation limits their ability to reach users directly through Teams.
- **Maintaining enterprise trust boundaries** This control ensures inbound chat is limited to identities that are governed by organizational policies and security controls.
- **Aligning with Microsoft's recommended security posture** This setting is marked Recommended and At risk because consumer initiated chat significantly increases the likelihood of unsolicited and malicious messaging.

## How this setting works

When this setting is enabled:

- **Inbound chat requests from Teams Free \(consumer\) accounts are blocked** at the service level by the external access policy.
- **Users can't override the restriction** through client settings. Enforcement is handled centrally through the external access policy.
- **The setting applies through Set CsExternalAccessPolicy**, using the EnableTeamsConsumerInbound parameter, which explicitly controls whether consumer accounts can initiate contact.
- **User level external access policies can override the global policy**, and the admin center surfaces users who have such overrides applied.
- **Admins can review recent inbound chat activity and download a CSV report**, helping identify exposure and remediate policy exceptions.
