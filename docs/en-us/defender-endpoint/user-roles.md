<!-- Source: https://learn.microsoft.com/en-us/defender-endpoint/user-roles -->
<!-- Sitemap-Last-Modified: 2026-06-17 -->

# Create and manage roles for role-based access control

This article explains how to create, edit, and delete custom roles for role-based access control \(RBAC\) in Microsoft Defender for Endpoint. You can define permissions for each role and assign the role to Microsoft Entra security groups to control user access to portal features.

Important

Some information in this article relates to a prereleased product which may be substantially modified before it's commercially released. Microsoft makes no warranties, expressed or implied, with respect to the information provided here.

Important

Starting February 16, 2025, new Microsoft Defender for Endpoint customers will only have access to the Unified Role-Based Access Control \(URBAC\). Existing customers keep their current roles and permissions. For more information, see URBAC [Unified Role-Based Access Control \(URBAC\) for Microsoft Defender for Endpoint](https://learn.microsoft.com/en-us/defender-xdr/manage-rbac)

## Create roles and assign the role to a Microsoft Entra group

Important

Microsoft recommends that you use roles with the fewest permissions. This helps improve security for your organization. Global Administrator is a highly privileged role that should be limited to emergency scenarios when you can't use an existing role.

The following steps guide you on how to create roles in the Microsoft Defender portal. It assumes that you have already created Microsoft Entra user groups.

1. Sign in to the [Microsoft Defender portal](https://security.microsoft.com) using account with the Security Administrator role assigned.
2. In the navigation pane, select **Settings** > **Endpoints** > **Roles** \(under **Permissions**\).
3. Select **Add role**.
4. Enter the role name, description, and permissions you'd like to assign to the role.
5. Select **Next** to assign the role to a Microsoft Entra Security group.
6. Use the filter to select the Microsoft Entra group that you'd like to add to this role to.
7. **Save and close**.
8. Apply the role and group assignment settings.

Important

After creating roles, you'll need to create a device group and provide access to the device group by assigning it to a role that you created.

Note

Device group creation is supported in Defender for Endpoint Plan 1 and Plan 2.

### Permission options

The following permissions are available when you configure roles:

- **View data**

  - **Security Operations** - View all security operations data in the portal
  - **Defender Vulnerability Management** - View Defender Vulnerability Management data in the portal

- **Active remediation actions**

  - **Security Operations** - Take response actions, approve or dismiss pending remediation actions, manage allowed/blocked lists for automation and indicators
  - **Defender Vulnerability Management - Exception handling** - Create new exceptions and manage active exceptions
  - **Defender Vulnerability Management - Remediation handling** - Submit new remediation requests, create tickets, and manage existing remediation activities
  - **Defender Vulnerability Management - Application handling** - Apply immediate mitigation actions by blocking vulnerable applications, as part of the remediation activity and manage the blocked apps and perform unblock actions

- **Security baselines**

  - **Defender Vulnerability Management – Manage security baselines assessment profiles** - Create and manage profiles so you can assess if your devices comply to security industry baselines.

- **Alerts investigation** - Manage alerts, initiate automated investigations, run scans, collect investigation packages, manage device tags, and download only portable executable \(PE\) files
- **Manage portal system settings** - Configure storage settings, SIEM, and threat intel API settings \(applies globally\), advanced settings, automated file uploads, roles, and device groups

  Note

  This setting is only available in the Microsoft Defender for Endpoint Administrator \(default\) role.
- **Manage security settings in Security Center** - Configure alert suppression settings, manage folder exclusions for automation, onboard and offboard devices, manage email notifications, manage evaluation lab, and manage allowed/blocked lists for indicators
- **Live response capabilities**

  - **Basic** commands:

    - Start a live-response session
    - Perform read-only live-response commands on remote device \(excluding file copy and execution\)
    - Download a file from the remote device via live response

  - **Advanced** commands:

    - Download PE and non-PE files from the file page
    - Upload a file to the remote device
    - View a script from the files library
    - Execute a script on the remote device from the files library

For more information on the available commands, see [Investigate devices using Live response](https://learn.microsoft.com/en-us/defender-endpoint/live-response).

## Edit roles

To edit an existing role, perform the following steps:

1. Sign in to the [Microsoft Defender portal](https://security.microsoft.com) using account with the Security administrator role assigned.
2. In the navigation pane, select **Settings** > **Endpoints** > **Roles** \(under **Permissions**\).
3. Select the role you'd like to edit.
4. Select **Edit**.
5. Modify the details or the groups that are assigned to the role.
6. Select **Save and close**.

## Delete roles

To delete a role that you no longer need, perform the following steps:

1. Sign in to the [Microsoft Defender portal](https://security.microsoft.com) using account with the Security Administrator role assigned.
2. In the navigation pane, select **Settings** > **Endpoints** > **Roles** \(under **Permissions**\).
3. Select the role you'd like to delete.
4. Select the drop-down button and select **Delete role**.

## Related articles

- [Assign Microsoft Entra roles to users](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/manage-roles-portal)
- [Assign user access](https://learn.microsoft.com/en-us/defender-endpoint/assign-portal-access)
- [Create and manage device groups](https://learn.microsoft.com/en-us/defender-endpoint/machine-groups)
