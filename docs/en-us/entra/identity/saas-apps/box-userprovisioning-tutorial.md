<!-- Source: https://learn.microsoft.com/en-us/entra/identity/saas-apps/box-userprovisioning-tutorial -->
<!-- Sitemap-Last-Modified: 2026-03-05 -->

# Configure Box for automatic user provisioning with Microsoft Entra ID

The objective of this article is to show the steps you need to perform in Box and Microsoft Entra ID to automatically provision and de-provision user accounts from Microsoft Entra ID to Box.

Note

This article describes a connector built on top of the Microsoft Entra user Provisioning Service. For important details on what this service does, how it works, and frequently asked questions, see [Automate user provisioning and deprovisioning to SaaS applications with Microsoft Entra ID](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/user-provisioning).

Box is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government | China operated by 21Vianet |
| --- | --- | --- |
| ✅ | ✅ |  |

## Prerequisites

To configure Microsoft Entra integration with Box, you need the following items:

- A Microsoft Entra tenant
- A Box Business plan or better

Note

When you test the steps in this article, we recommend that you do *not* use a production environment.

Note

Apps need to be enabled in the Box application first.

To test the steps in this article, follow these recommendations:

- don't use your production environment, unless it's necessary.
- If you don't have a Microsoft Entra trial environment, you can [get a one-month trial](https://azure.microsoft.com/pricing/free-trial/).

## Step 1: Assign users to Box

Microsoft Entra ID uses a concept called "assignments" to determine which users should receive access to selected apps. In the context of automatic user account provisioning, only the users and groups that have been "assigned" to an application in Microsoft Entra ID is synchronized.

Before configuring and enabling the provisioning service, you need to decide what users and/or groups in Microsoft Entra ID represent the users who need access to your Box app. Once decided, you can assign these users to your Box app by following the instructions here:

[Assign a user or group to an enterprise app](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/assign-user-or-group-access-portal)

## Step 2: Assign users and groups

The **Box > Users and Groups** tab in the Azure portal allows you to specify which users and groups should be granted access to Box. Assignment of a user or group causes the following things to occur:

- Microsoft Entra ID permits the assigned user \(either by direct assignment or group membership\) to authenticate to Box. If a user isn't assigned, then Microsoft Entra ID doesn't permit them to sign in to Box and returns an error on the Microsoft Entra sign-in page.
- An app tile for Box is added to the user's [application launcher](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/end-user-experiences).
- If automatic provisioning is enabled, then the assigned users and/or groups are added to the provisioning queue to be automatically provisioned.

  - If only user objects were configured to be provisioned, then all directly assigned users are placed in the provisioning queue, and all users that are members of any assigned groups are placed in the provisioning queue.
  - If group objects were configured to be provisioned, then all assigned group objects are provisioned to Box, and all users that are members of those groups. The group and user memberships are preserved upon being written to Box.

You can use the **Attributes > Single Sign-On** tab to configure which user attributes \(or claims\) are presented to Box during SAML-based authentication, and the **Attributes > Provisioning** tab to configure how user and group attributes flow from Microsoft Entra ID to Box during provisioning operations.

### Important tips for assigning users to Box

- It's recommended that a single Microsoft Entra user assigned to Box to test the provisioning configuration. Additional users and/or groups may be assigned later.
- When assigning a user to box, you must select a valid user role. The "Default Access" role doesn't work for provisioning.

## Step 3: Enable Automated User Provisioning

This section guides through connecting your Microsoft Entra ID to Box's user account provisioning API, and configuring the provisioning service to create, update, and disable assigned user accounts in Box based on user and group assignment in Microsoft Entra ID.

If automatic provisioning is enabled, then the assigned users and/or groups are added to the provisioning queue to be automatically provisioned.

- If only user objects are configured to be provisioned, then directly assigned users are placed in the provisioning queue, and all users that are members of any assigned groups are placed in the provisioning queue.
- If group objects were configured to be provisioned, then all assigned group objects are provisioned to Box, and all users that are members of those groups. The group and user memberships are preserved upon being written to Box.

Tip

You may also choose to enabled SAML-based Single Sign-On for Box, following the instructions provided in the [Azure portal](https://portal.azure.com). Single sign-on can be configured independently of automatic provisioning, though these two features complement each other.

### Configure automatic user account provisioning

The objective of this section is to outline how to enable provisioning of Active Directory user accounts to Box.

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [Cloud Application Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#cloud-application-administrator).
2. Browse to **Entra ID** > **Enterprise apps**.
3. If you have already configured Box for single sign-on, search for your instance of Box using the search field. Otherwise, select **Add** and search for **Box** in the application gallery. Select Box from the search results, and add it to your list of applications.
4. Select your instance of Box, then select the **Provisioning** tab.
5. Select **+ New configuration**.

   ![Screenshot for the new configuration steps into the box.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/application-provisioning.png)

6. Under the **Admin Credentials** section, select **Authorize** to open a Box login dialog in a new browser window.
7. On the **Login to grant access to Box** page, provide the required credentials, and then select **Authorize**.

   ![Screenshot of the Log in to grant access to box screen, showing entry for Email and Password, and the Authorize button.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/box-userprovisioning-tutorial/ic769546.png "Enable automatic user provisioning")

8. Select **Grant access to Box** to authorize this operation and to return to the Azure portal.

   ![Screenshot of the authorize access screen in Box, showing an explanatory message and the Grant access to Box button.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/box-userprovisioning-tutorial/ic769549.png "Enable automatic user provisioning")

9. Select **Test Connection** to ensure Microsoft Entra ID can connect to your Box app. If the connection fails, ensure your Box account has Team Admin permissions and try the **"Authorize"** step again.
10. Select **Create** to create your configuration.
11. Select **Properties** in the **Overview** page.
12. Select the **Edit** icon to edit the properties. Enable notification emails and provide an email to receive quarantine notifications. Enable **Accidental deletions prevention**. Select **Apply** to save the changes.

    ![Screenshot of Provisioning properties.](https://learn.microsoft.com/en-us/entra/identity/saas-apps/common/provisioning-properties.png)

13. Select **Attribute Mapping** in the left panel and select **users**.
14. In the **Attribute Mappings** section, review the user attributes that are synchronized from Microsoft Entra ID to Box. The attributes selected as **Matching** properties are used to match the user accounts in Box for update operations. Select the Save button to commit any changes.
15. To configure scoping filters, refer to the following instructions provided in the [Scoping filter article](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/define-conditional-rules-for-provisioning-user-accounts).
16. Use [on-demand provisioning](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/provision-on-demand) to validate sync with a small number of users before deploying more broadly in your organization.
17. When you're ready to provision, select **Start Provisioning** from the **Overview** page.

For more information on how to read the Microsoft Entra provisioning logs, see [Reporting on automatic user account provisioning](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/check-status-user-account-provisioning).

In your Box tenant, synchronized users are listed under **Managed Users** in the **Admin Console**.

![Integration status](https://learn.microsoft.com/en-us/entra/identity/saas-apps/media/box-userprovisioning-tutorial/ic769556.png "Integration status")

## Additional resources

- [Managing user account provisioning for Enterprise Apps](https://learn.microsoft.com/en-us/entra/identity/saas-apps/tutorial-list)
- [What is application access and single sign-on with Microsoft Entra ID?](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/what-is-single-sign-on)
- [Configure Single Sign-on](https://learn.microsoft.com/en-us/entra/identity/saas-apps/box-tutorial)
