<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/baseline-security-mode/dont-allow-meeting-participants-to-change-names?view=o365-worldwide -->
<!-- Sitemap-Last-Modified: 2026-11-17 -->

# Block meeting participants from changing their display names

Allowing meeting participants to change their display names during a meeting can create opportunities for impersonation, confusion, or social engineering attacks. Participants may rename themselves to appear as trusted individuals, executives, or organizers, making it harder for attendees to accurately identify who is present. Disabling display name changes helps preserve identity integrity in meetings by ensuring that participants are represented consistently and transparently throughout the session.

Microsoft Teams enforces this control through the ParticipantNameChange setting in Teams meeting policies. When disabled, participants can't edit their display names during meetings, and the names shown reflect their authenticated identity.

You need to be a member of the [Global administrator role](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference) and [Teams administrator role](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#teams-administrator) to be able to configure this setting.

For more information, see [ParticipantNameChange in the Set CsTeamsMeetingPolicy PowerShell documentation](https://learn.microsoft.com/en-us/powershell/module/microsoftteams/set-csteamsmeetingpolicy#-participantnamechange).

## Why this setting matters

Meeting identity integrity is critical for trust and security, especially in meetings that involve external participants, executives, or sensitive discussions. Allowing participants to alter their display names can be abused to mislead others or obscure accountability.

This setting helps mitigate those risks by:

- **Allowing participant renaming creates a risk of roster spoofing**, where attackers can impersonate trusted individuals during meetings, increasing the likelihood of social engineering attacks.
- **Preventing impersonation during meetings** Participants can't rename themselves to resemble other users, roles, or trusted identities, reducing the risk of social engineering attacks.
- **Reducing confusion and misidentification** Consistent display names make it easier for organizers and attendees to recognize who is present and who is speaking.
- **Preserving audit and accountability** Disabling name changes ensures that participant identities remain tied to their authenticated accounts, supporting clearer meeting records and investigation if issues arise.
- **Aligning with Microsoft's recommended security posture** This control is disabled by default and should remain disabled in security sensitive environments to reduce impersonation and trust based risks.

## How this setting works

When this setting is disabled:

- **Participants can't edit their display names** during meetings they join.
- **Names displayed in the meeting reflect the authenticated identity**, rather than a user supplied alias.
- **The restriction is enforced through Teams meeting policies**, which can be applied globally or assigned to specific users.
- **Meeting organizers can't override the restriction** unless the policy explicitly allows name changes.
- **Permanent meeting artifacts**- such as attendance reports and transcripts- continue to reflect the original authenticated names.
- A **detailed CSV report is available for download**, providing visibility into affected meetings and users so organizations can assess risk and standardize policy assignments.

This approach ensures that participant identity remains consistent and trustworthy throughout the meeting experience.
