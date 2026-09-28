<!-- Source: https://learn.microsoft.com/en-us/entra/external-id/add-users-information-worker -->
<!-- Sitemap-Last-Modified: 2025-04-25 -->

# How users in your organization can invite guest users to an app

**Applies to**: ![Green circle with a white check mark symbol that indicates the following content applies to workforce tenants.](https://learn.microsoft.com/en-us/entra/external-id/media/common/applies-to-yes.png) Workforce tenants \([learn more](https://learn.microsoft.com/en-us/entra/external-id/tenant-configurations)\)

After a guest user is added to the directory in Microsoft Entra ID, an application owner sends the guest user a direct link to the app they want to share. Microsoft Entra admins can set up self-service management for gallery or SAML-based apps in their Microsoft Entra tenant. This way, application owners manage their guest users, even if the guest users aren't added to the directory yet. When an app is configured for self-service, the application owner uses their Access Panel to invite a guest user to an app or add a guest user to a group that has access to the app.

Self-service app management for gallery and SAML-based apps requires some initial setup by an admin. Follow the summary of the setup steps \(for more detailed instructions, see [Prerequisites](#prerequisites) later on this page\):

- Enable self-service group management for the tenant
- Create a group to assign to the app and make the user an owner
- Set up the app for self-service and assign the group to the app

Note

- This article describes how to set up self-service management for gallery and SAML-based apps that you’ve added to your Microsoft Entra tenant. You can also [set up self-service Microsoft 365 groups](https://learn.microsoft.com/en-us/entra/identity/users/groups-self-service-management) so your users can manage access to their own Microsoft 365 groups. For more ways users can share Office files and apps with guest users, see [Guest access in Microsoft 365 groups](https://support.office.com/article/guest-access-in-office-365-groups-bfc7a840-868f-4fd6-a390-f347bf51aff6) and [Share SharePoint files or folders](https://support.office.com/article/share-sharepoint-files-or-folders-1fe37332-0f9a-4719-970e-d2578da4941c).
- Users are only able to invite guests if they have the **Guest inviter** role.

## Invite someone to join a group that has access to the app

After you configure an app for self-service, you can invite guest users to the groups you manage that have access to the apps you want to share. Guest users don't need to already exist in the directory. The application owner follows these steps to invite a guest user to the group so that they can access the app.

1. Confirm that you're an owner of the self-service group that has access to the app you want to share.
2. Open your Access Panel by going to `https://myapps.microsoft.com`.
3. Select the **Groups** app.

![Screenshot showing the Groups app in the Access Panel.](https://learn.microsoft.com/en-us/entra/external-id/media/add-users-iw/access-panel-groups.png)

4. In **Groups I own**, select the group that has access to the app you want to share.

![Screenshot showing where to select a group under the Groups I own.](https://learn.microsoft.com/en-us/entra/external-id/media/add-users-iw/access-panel-groups-i-own.png)

5. At the top of the group members list, select the **+** button.

![Screenshot showing the plus symbol for adding members to the group.](https://learn.microsoft.com/en-us/entra/external-id/media/add-users-iw/access-panel-groups-add-member.png)

6. In the **Add members** search box, enter the guest user's email address. Optionally, include a welcome message.

![Screenshot showing the Add members window for adding a guest.](https://learn.microsoft.com/en-us/entra/external-id/media/add-users-iw/access-panel-invitation.png)

7. Select **Add** to automatically send the invitation to the guest user. After you send the invitation, the user account is automatically added to the directory as a guest.

## Prerequisites

Self-service app management requires some initial setup by a Microsoft Entra admin. As part of this setup, you configure the app for self-service and assign a group to the app that the application owner can manage. You can also set up the group to let anyone request membership but require a group owner's approval. \(Learn more about [self-service group management](https://learn.microsoft.com/en-us/entra/identity/users/groups-self-service-management).\)

Note

You can't add guest users to a dynamic group or to a group that is synced with on-premises Active Directory.

### Enable self-service group management for your tenant

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [User Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#user-administrator).
2. Browse to **Entra ID** > **Groups** > **All groups**.
3. Under **Settings**, select **General**.
4. Under **Self Service Group Management**, next to **Owners can manage group membership requests in the Access Panel**, select **Yes**.
5. Select **Save**.

### Create a group to assign to the app and make the user an owner

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [User Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#user-administrator).
2. Browse to **Entra ID** > **Groups** > **All groups**.
3. Select **New group**.
4. Under **Group type**, select **Security**.
5. Type a **Group name** and **Group description**.
6. Under **Membership type**, select **Assigned**.
7. Select **Create**, and close the **Group** page.
8. On the **Groups - All groups** page, open the group.
9. Under **Manage**, select **Owners** > **Add owners**. Search for the user who should manage access to the application. Select the user, and then select **Select**.

### Configure the app for self-service and assign the group to the app

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [User Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#user-administrator).
2. Browse to **Entra ID** > **Enterprise apps**.
3. Select **All applications**, in the application list, find and open the app.
4. Under **Manage**, select **Single sign-on**, and set up the application for single sign-on. \(For details, see [how to manage single sign-on for enterprise apps](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/add-application-portal-setup-sso).\)
5. Under **Manage**, select **Self-service**, and set up self-service app access. \(For details, see [how to use self-service app access](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/manage-self-service-access).\)

   Note

   For the setting **To which group should assigned users be added?** select the group you created in the previous section.
6. Under **Manage**, select **Users and groups**, and verify that the self-service group you created appears in the list.
7. To add the app to the group owner's Access Panel, select **Add user** > **Users and groups**. Search for the group owner and select the user, select **Select**, and then select **Assign** to add the user to the app.

## Next steps

See the following articles on Microsoft Entra B2B collaboration:

- [What is Microsoft Entra B2B collaboration?](https://learn.microsoft.com/en-us/entra/external-id/what-is-b2b)
- [How do Microsoft Entra admins add B2B collaboration users?](https://learn.microsoft.com/en-us/entra/external-id/add-users-administrator)
- [B2B collaboration invitation redemption](https://learn.microsoft.com/en-us/entra/external-id/redemption-experience)
- [External ID pricing](https://learn.microsoft.com/en-us/entra/external-id/external-identities-pricing)
