<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/baseline-security-mode/block-microsoft365-trial-tenants-federate-with-your-organization?view=o365-worldwide -->
<!-- Sitemap-Last-Modified: 2026-11-17 -->

# Don't allow Microsoft 365 trial tenants to federate with your organization

Microsoft 365 trial tenants can be created quickly and anonymously, making them attractive to attackers who use these temporary environments to impersonate organizations, initiate unsolicited contact, or probe users through social engineering. Blocking federation with these tenants prevents users in your organization from communicating with identities in trial only tenants and removes trial tenant users from existing chats. This configuration reduces exposure to phishing attempts, spoofed identities, and untrusted external communication.

Teams enforces this control using the AllowedTrialTenantDomains parameter in the tenant federation configuration. By default, trial only tenants are blocked at the service boundary. Unless a trial domain is explicitly added to the allowed list, users in those tenants can't search for, contact, or join meetings with your organization. Enabling this setting ensures that your organization can't inadvertently override the default protection and that only trusted, vetted domains can be federated.

You need to be a member of the [Global administrator role](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference) and [Teams administrator role](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#teams-administrator) to be able to configure this setting.

For more information, see [AllowedTrialTenantDomains in the Set CsTenantFederationConfiguration PowerShell documentation](https://learn.microsoft.com/en-us/powershell/module/microsoftteams/set-csexternalaccesspolicy?#-enableteamsconsumerinbound).

## Why this setting matters

Trial only tenants aren't subject to the same identity assurance, subscription validation, or operational scrutiny as paid Microsoft 365 tenants. Because they're easy to create and discard, attackers frequently use them as staging environments for phishing and social engineering campaigns.

This setting helps mitigate those risks by:

- **Blocking communication from untrusted trial environments** Users in trial only tenants are prevented from contacting, searching for, or inviting users in your organization, reducing unsolicited outreach and impersonation attempts.
- **Reducing phishing and social engineering exposure** Trial tenants can be rapidly created to mimic legitimate organizations. Preventing federation limits attackers' ability to engage users through Teams.
- **Maintaining clear trust boundaries for external collaboration** Federation is limited to tenants with established, trusted domains rather than temporary or anonymous environments.
- **Aligning with Microsoft's recommended security posture** This setting is marked Recommended and At risk because allowing federation with trial only tenants significantly increases the likelihood of malicious external communication.

## How this setting works

When this setting is enabled:

- Federation with Microsoft 365 trial only tenants is blocked by default at the Teams service boundary.
- Users in trial tenants can't search for, contact, or invite users in your organization, and existing chats with trial tenants are removed.
- Only trial tenant domains explicitly added to AllowedTrialTenantDomains are permitted, allowing admins to make narrow, intentional exceptions for trusted scenarios.
- Admins can review recent communications with trial tenants directly in the admin center to understand exposure before or after enforcement.
- A detailed CSV report is available for download, showing chats, meetings, and calls involving trial tenants to support assessment and remediation.

This approach ensures that external federation remains intentional and risk aware, while still allowing administrators to explicitly trust specific trial tenants when there's a valid business need.

## Additional considerations

- A trial only tenant is defined as a Microsoft 365 tenant that has only trial subscriptions and no purchased licenses. These tenants are blocked from federating with your organization by default.
- Blocking applies to both new and existing communication. Users in trial tenants can't search for or contact users in your organization, and existing chats with trial tenants are removed.
- Exceptions must be explicitly configured. Federation with a trial tenant is allowed only if its domain is added to the AllowedTrialTenantDomains list using PowerShell. There's no UI-based override.
- Cross cloud communication with trial only tenants remains blocked, even if a domain is added to the allowed list.
