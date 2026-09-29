<!-- Source: https://learn.microsoft.com/en-us/defender-for-iot/set-up-rbac -->
<!-- Sitemap-Last-Modified: 2026-07-02 -->

# Set up RBAC permissions to access site security

The Microsoft Defender portal allows granular access to features and data based on user roles and the permissions given to each user with Role-Based Access Control \(RBAC\).

To access the Microsoft Defender for IoT features in the Defender portal, such as site security, and Defender for IoT specific alerts and vulnerability updates, you need to assign permissions and roles to the correct users.

This article shows you how to set up the new roles and permissions to access the site security and Defender for IoT specific features. Before you begin, make sure you meet the [prerequisites](#prerequisites).

To make general changes to RBAC roles and permissions that relate to all other areas of Defender for IoT, see [configure general RBAC permissions](https://learn.microsoft.com/en-us/defender-for-iot/configure-permissions).

Important

This article discusses Microsoft Defender for IoT in the Defender portal \(Preview\).

Some features are not yet available in the Defender portal. If you're interested in these features, or you're an existing customer working on the Azure portal, see the [Defender for IoT on Azure documentation](https://learn.microsoft.com/en-us/azure/defender-for-iot/organizations/overview).

Learn more about the [Defender for IoT management portals](https://learn.microsoft.com/en-us/defender-for-iot/microsoft-defender-iot#what-are-the-different-management-portals-for-microsoft-defender-for-iot).

Some information in this article relates to a prereleased product which may be substantially modified before it's commercially released. Microsoft makes no warranties, expressed or implied, with respect to the information provided here.

## Prerequisites

- Review [the general prerequisites for Microsoft Defender for IoT](https://learn.microsoft.com/en-us/defender-for-iot/prerequisites).
- Details of all users to be assigned site security permissions.

## Access management options

There are three ways to manage user access to the Defender portal, depending on whether your organization uses Global Microsoft Entra roles, Microsoft Defender unified RBAC, or Microsoft Defender for Endpoint XDR RBAC. Each access-control system listed below has different permission names that allow access to site security:

- [Global Microsoft Entra roles](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference).
- [Microsoft Defender unified RBAC](https://learn.microsoft.com/en-us/defender-xdr/manage-rbac): Use Defender unified role-based access control \(RBAC\) to manage access to specific data, tasks, and capabilities in the Defender portal.
- [Microsoft Defender for Endpoint XDR RBAC](https://learn.microsoft.com/en-us/defender-endpoint/user-roles): Use Defender for Endpoint XDR role-based access control \(RBAC\) to manage access to specific data, tasks, and capabilities in the Defender portal.

The instructions and permission settings listed in this article apply to both Defender unified RBAC and Microsoft Defender for Endpoint RBAC.

## Set up Defender unified RBAC roles for site security

Assign RBAC permissions and roles, based on the [RBAC roles and permissions summary](#summary-of-rbac-roles-and-permissions-for-site-security), to give users access to site security features:

1. In the Defender portal, select **Settings** > **Microsoft Defender XDR** > **Permissions and roles**.
2. Enable **Endpoints & Vulnerability Management**.
3. Select **Go to Permissions and roles**.
4. Select **Create custom role**.
5. Type a **Role name**, and then select **Next** for Permissions.

   [![Screenshot of the permissions set up page for site security.](https://learn.microsoft.com/en-us/defender-for-iot/media/set-up-rbac/permissions-set-up.png)](https://learn.microsoft.com/en-us/defender-for-iot/media/set-up-rbac/permissions-set-up.png#lightbox)
6. For read permissions, select **Security operations**, and select **Select custom permissions**.
7. In **Security data**, select **Security data basics\(read\)** and select **Apply**.

   [![Screenshot of the permissions set up page with the specific read permissions chosen for site security.](https://learn.microsoft.com/en-us/defender-for-iot/media/set-up-rbac/permissions-unified-read-options.png)](https://learn.microsoft.com/en-us/defender-for-iot/media/set-up-rbac/permissions-unified-read-options.png#lightbox)
8. For write permissions, in **Authorization and settings**, select **Select custom permissions**.
9. In **Security data**, select **Core security settings \(manage\)** and select **Apply**.

   [![Screenshot of the permissions set up page with the specific write permissions chosen for site security.](https://learn.microsoft.com/en-us/defender-for-iot/media/set-up-rbac/permissions-choose-options.png)](https://learn.microsoft.com/en-us/defender-for-iot/media/set-up-rbac/permissions-choose-options.png#lightbox)
10. Select **Next** for Assignments.
11. Select **Add assignment**, type a name, choose users and groups and select the Data sources.
12. Select **Add**.
13. Select **Next** to **Review and finish**.
14. Select **Submit**.

## Set up Microsoft Defender for Endpoint XDR RBAC \(Version 2\) roles for site security

Assign RBAC permissions and roles, based on the [RBAC roles and permissions summary for site security](#summary-of-rbac-roles-and-permissions-for-site-security), to give users access to site security features:

1. In the Defender portal, select **Settings** > **Endpoints** > **Roles**.
2. Select **Add role**.
3. Type a **Role name**, and a **Description**.
4. Select **Next** for Permissions.

   [![Screenshot of the Microsoft Defender for Endpoint XDR RBAC \(version2\) permissions set up page for site security.](https://learn.microsoft.com/en-us/defender-for-iot/media/set-up-rbac/permissions-mde-rbac2-add-role.png)](https://learn.microsoft.com/en-us/defender-for-iot/media/set-up-rbac/permissions-mde-rbac2-add-role.png#lightbox)
5. For read permissions, in **View Data**, select **Security Operations**.

   [![Screenshot of the Microsoft Defender for Endpoint XDR RBAC \(version2\) permissions set up page with the specific read permissions chosen for site security.](https://learn.microsoft.com/en-us/defender-for-iot/media/set-up-rbac/permissions-mde-rbac2-read-options.png)](https://learn.microsoft.com/en-us/defender-for-iot/media/set-up-rbac/permissions-mde-rbac2-read-options.png#lightbox)
6. For write permissions, select **Manage security settings in Security Center**.

   [![Screenshot of the Microsoft Defender for Endpoint XDR RBAC \(version2\) permissions set up page with the specific read and write permissions chosen for site security.](https://learn.microsoft.com/en-us/defender-for-iot/media/set-up-rbac/permissions-mde-rbac2-write-options.png)](https://learn.microsoft.com/en-us/defender-for-iot/media/set-up-rbac/permissions-mde-rbac2-write-options.png#lightbox)
7. Select **Next**.
8. In **Assigned user groups**, select the user groups from the list to assign to this role.
9. Select **Submit**.

### Summary of RBAC roles and permissions for site security

The following tables summarize the write and read permissions required for site security across the supported RBAC models.

**For Unified RBAC**:

| Write permissions | Read permissions |
| --- | --- |
| **Defender permissions**: Core security settings \(manage\) under Authorization and Settings and scoped to all device groups.  <br>**Entra ID roles**: Global Administrator, Security Administrator, Security Operator and scoped to all device groups. | Write roles \(including roles that are non-scoped to all device groups\).  <br>**Defender permissions**: Security data basics \(under Security Operations\).  <br>**Entra ID roles**: Global Reader, Security Reader. |

**For Microsoft Defender for Endpoint RBAC \(version 2\)**:

| Write permissions | Read permissions |
| --- | --- |
| **Defender for Endpoint roles**: Manage security settings in Security Center and scoped to all device groups.  <br>**Entra ID roles**: Global Administrator, Security Administrator. | Write roles \(including roles that are non-scoped to all device groups\).  <br>**Defender for Endpoint roles**: View data - Security operations \(read\).  <br>**Entra ID roles**: Global Reader, Security Reader. |

## Next steps

Once you have set up the RBAC roles and permissions, [set up a site](https://learn.microsoft.com/en-us/defender-for-iot/set-up-sites) so that Microsoft Defender for IoT can begin sending data to the Defender portal.
