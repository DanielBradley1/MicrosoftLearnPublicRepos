<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/baseline-security-mode/require-external-users-wait-lobby-before-meetings?view=o365-worldwide -->
<!-- Sitemap-Last-Modified: 2026-11-17 -->

# Require external participants to remain in the lobby until admitted to the meeting

External participants present a higher security risk because they join from outside your organization's identity, compliance, and threat protection boundaries. Allowing them to bypass the lobby can enable unauthorized users to enter meetings without being screened, increasing the likelihood of meeting hijacking, impersonation, or exposure of confidential information. Requiring external users to wait in the lobby ensures that organizers can manually admit them only after validating their identity. This requirement helps prevent unauthorized access while maintaining a friction free experience for internal users and trusted guests.

Microsoft Teams enforces this control through the AutoAdmittedUsers meeting policy setting. When configured to a restrictive value \(such as OrganizerOnly or EveryoneInCompany\), only internal or explicitly trusted participants are automatically admitted to meetings. All other users, including external participants, partners, and consumer accounts, are placed in the lobby until an organizer approves their entry. This placement ensures that no external user can circumvent the lobby requirement through client settings or legacy policy behaviors.

You need to be a member of the [Global administrator role](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference) and [Teams administrator role](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#teams-administrator) to be able to configure this setting.

For more information, see [AutoAdmittedUsers in the Set CsTeamsMeetingPolicy PowerShell documentation](https://learn.microsoft.com/en-us/powershell/module/microsoftteams/set-csteamsmeetingpolicy#-autoadmittedusers).

## Why this setting matters

Online meetings are a frequent target for attackers seeking to gain unauthorized access or disrupt business operations. External users are more difficult to verify and may not be subject to the same organizational controls as internal participants. This setting helps mitigate those risks by:

- **Preventing unauthorized meeting access** External users must wait in the lobby until explicitly admitted, reducing the risk of meeting hijacking or accidental exposure of sensitive discussions.
- **Protecting against impersonation and social engineering** Requiring organizer approval allows hosts to confirm participant identities before granting access.
- **Maintaining a secure default without impacting internal users** Internal users and trusted participants can join meetings directly, while external users are appropriately gated.
- **Aligning with Microsoft's recommended security posture** This setting is marked Recommended and At risk because allowing external users to bypass the lobby significantly increases the likelihood of unauthorized meeting access.

## How this setting works

When this setting is enabled:

- **External users are placed in the meeting lobby by default** and can join only after an organizer admits them.
- **Only internal users or explicitly trusted participants** are automatically admitted, depending on the configured AutoAdmittedUsers value.
- **Users can't override the behavior** through client side meeting options. Enforcement is handled centrally through meeting policies.
- **User level meeting policies can override the global policy**, and the admin center highlights users with such overrides so admins can review and remediate exceptions.
- **Meetings remain accessible to trusted participants** while reducing risk from unverified external attendees. This approach ensures consistent, organizer controlled access to meetings and reduces the risk of unauthorized participation without adding friction for internal collaboration.

## Additional considerations

- The AutoAdmittedUsers setting determines which types of participants are automatically admitted to meetings organized by a user. When set to restrictive values such as *OrganizerOnly* or *EveryoneInCompany*, all other participants- including external users- are placed in the lobby.
- This control is enforced through Teams meeting policies, which can be applied globally or assigned to specific users. Users with custom meeting policies may have different lobby behavior.
- The setting governs meeting join behavior only. It doesn't control chat access, file sharing, or other collaboration features.
- Lobby enforcement is policy driven and meeting participants can't bypass it, ensuring consistent screening of external users.
