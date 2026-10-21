<!-- Source: https://learn.microsoft.com/en-us/defender-for-identity/security-posture-assessments/group-policy -->
<!-- Sitemap-Last-Modified: 2026-10-14 -->

# Group policy security assessments

Group policy security assessments identify Group Policy Objects \(GPOs\) that grant excessive access or expose credentials in your Active Directory environment.

## GPO assigns unprivileged identities to local groups with elevated privileges

**Description**

This recommendation identifies GPOs that grant unprivileged identities elevated access through membership in local groups.

Using a GPO to add users or groups to a local group can introduce a security risk when the resulting access exceeds their business requirements. For example, granting **Authenticated Users** or **Everyone** membership in the local **Administrators** or **Remote Desktop Users** group can provide broad administrative privileges or remote access to affected devices.

Attackers can exploit these group memberships to gain additional access and move laterally within the environment. Review the affected GPOs and restrict membership to identities that require the access.

**User impact**

Removing group memberships can prevent users, services, or applications from performing operations that depend on those memberships. Review business requirements and dependencies before making changes.

**Implementation**

1. Review the affected GPOs and the local group memberships they configure.
2. Identify unprivileged users or broadly scoped groups, such as **Authenticated Users** or **Everyone**, that receive unnecessary elevated privileges or remote access.
3. Modify the GPOs to remove unnecessary memberships. Retain only the users and groups that require access for their responsibilities.
4. Allow the updated policy to apply to affected devices, then verify that the resulting local group memberships meet your security and operational requirements.

## GPO can be modified by unprivileged accounts

**Description**

This recommendation lists any Group Policy Objects in your environment that can be modified by standard users which can potentially lead to the compromise of the domain.

Attackers may attempt to obtain information on Group Policy settings to uncover vulnerabilities that can be exploited to gain higher levels of access, understand the security measures in place within a domain, and identify patterns in domain objects. This information can be used to plan subsequent attacks, such as identifying potential paths to exploit within the target network or finding opportunities to blend in or manipulate the environment.

**User impact**

A user, service or application that relies on these permissions may stop functioning.

**Implementation**

Carefully review each assigned permission, identify any dangerous permission granted, and modify them to remove any unnecessary or excessive user rights.

## Reversible passwords found in GPOs

**Description**

This recommendation identifies GPOs that contain password data in Group Policy Preferences \(GPP\).

Group Policy Preferences previously allowed administrators to embed credentials in domain policies. [Security update MS14-025](https://learn.microsoft.com/en-us/security-updates/securitybulletins/2014/ms14-025) removed the ability to configure and distribute passwords through the affected preference extensions because the passwords were stored insecurely.

However, applying the update doesn't remove previously configured password data. Files containing these credentials can remain in the domain's `SYSVOL` folder, where domain users can read them. The passwords can be decrypted using a publicly available AES key.

An attacker who obtains these credentials might use them to gain unauthorized access or elevate privileges. Remove existing preferences that contain embedded credentials.

**User impact**

Removing password-containing preferences can disrupt dependent configurations, such as mapped drives, scheduled tasks, services, local account management, or data source connections. Identify these dependencies and arrange an alternative that doesn't store passwords in Group Policy Preferences before removing the affected configuration.

**Implementation**

Use **Group Policy Management Console \(GPMC\)** on a domain controller or on a management computer with **Remote Server Administration Tools \(RSAT\)** installed.

1. In the recommendation's **Exposed entities** tab, identify the affected GPOs.
2. In GPMC, edit each reported GPO and locate the preference items that contain password data.
3. Review the affected configuration and its dependencies. Replace any required functionality with a configuration that doesn't store passwords in Group Policy Preferences.
4. If you need to remove the configured item from clients, use the cleanup action supported by that preference type. For example, to remove a scheduled task deployed by a preference, open the preference's properties, set **Action** to **Delete**, and select **Apply** and **OK**.

   [![Screenshot of a scheduled task preference with Delete highlighted in the Action list.](https://learn.microsoft.com/en-us/defender-for-identity/media/reversible-passwords-group-policy/screenshot-of-group-policy-objects.png)](https://learn.microsoft.com/en-us/defender-for-identity/media/reversible-passwords-group-policy/screenshot-of-group-policy-objects.png#lightbox)
5. Allow the policy changes to replicate and apply to affected clients. If you configured a cleanup action, verify that it completed on the affected clients before removing the preference item from the GPO.
6. Remove the password-containing preference items from the GPO. Verify that the password-containing preference data is no longer present in `SYSVOL` after replication.
7. Change the exposed account passwords and update legitimate dependencies. Removing the stored credentials doesn't invalidate passwords that might already have been obtained.
8. Repeat the procedure for all affected GPOs.

Important

Removing a preference item from a GPO doesn't necessarily remove settings that were previously applied to clients. The **Delete** action removes the configured item, such as a scheduled task or local user account, rather than just its stored password. Review the impact before applying a cleanup action. Don't delete an entire GPO when only individual preference items require remediation.

For more information, see [MS14-025: Vulnerability in Group Policy Preferences could allow elevation of privilege](https://support.microsoft.com/kb/2962486).

## Next steps

[Learn more about Microsoft Secure Score](https://learn.microsoft.com/en-us/microsoft-365/security/defender/microsoft-secure-score)
