<!-- Source: https://learn.microsoft.com/en-us/entra/external-id/b2b-quickstart-add-guest-users-portal -->
<!-- Sitemap-Last-Modified: 2026-04-24 -->

# Quickstart: Add a guest user and send an invitation

**Applies to**: ![Green circle with a white check mark symbol that indicates the following content applies to workforce tenants.](https://learn.microsoft.com/en-us/entra/external-id/media/common/applies-to-yes.png) Workforce tenants \([learn more](https://learn.microsoft.com/en-us/entra/external-id/tenant-configurations)\)

With Microsoft Entra [B2B collaboration](https://learn.microsoft.com/en-us/entra/external-id/what-is-b2b), you can invite anyone to collaborate with your organization using their own work, school, or social account.

In this quickstart, you'll learn how to add a new guest user to your Microsoft Entra directory in the Microsoft Entra admin center. You'll also send an invitation and see what the guest user's invitation redemption process looks like.

This guide provides the basic steps to invite an external user. To learn about all of the properties and settings that you can include when you invite an external user, see [How to create and delete a user](https://learn.microsoft.com/en-us/entra/fundamentals/how-to-create-delete-users).

If you don’t have an Azure subscription, create a [free account](https://azure.microsoft.com/pricing/purchase-options/azure-account?cid=msft_learn) before you begin.

Note

B2B invitation emails that originate from onmicrosoft default domains are subject to Exchange Online sending limits. See [Limiting onmicrosoft domain usage for sending emails](https://learn.microsoft.com/en-us/office365/servicedescriptions/exchange-online-service-description/exchange-online-limits#sending-limits) for more information. Consider updating to a custom domain if you need higher limits. For more information, see [Add your custom domain name to your tenant](https://learn.microsoft.com/en-us/entra/fundamentals/add-custom-domain).

## Prerequisites

To complete the scenario in this quickstart, you need:

- A role that allows you to create users in your tenant directory, such as at least a [Guest Inviter role](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#guest-inviter) or a [User Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#user-administrator).
- Access to a valid email address outside of your Microsoft Entra tenant, such as a separate work, school, or social email address. You'll use this email to create the guest account in your tenant directory and access the invitation.

## Invite an external guest user

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [User Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#user-administrator).
2. Browse to **Entra ID** > **Users**.

   ![Screenshot of the All users page.](https://learn.microsoft.com/en-us/entra/external-id/media/quickstart-add-users-portal/all-users-page.png)
3. Select **Invite external user** from the menu.

   ![Screenshot of the invite external user menu option.](https://learn.microsoft.com/en-us/entra/external-id/media/quickstart-add-users-portal/invite-external-user-menu.png)

### Basics for external users

In this section, you're inviting the guest to your tenant using *their email address*. For this quickstart, enter an email address that you can access.

- **Email**: Enter the email address for the guest user you're inviting.
- **Display name**: Provide the display name.
- **Invitation message**: Select the **Send invite message** checkbox to send an invitation message. When you enable this checkbox, you can also set up a customized short message and another CC recipient.

![Screenshot of the invite external user Basics tab.](https://learn.microsoft.com/en-us/entra/external-id/media/quickstart-add-users-portal/invite-external-user-basics-tab.png)

Select the **Review and invite** button to finalize the process.

### Review and invite

The final tab captures several key details from the user creation process. Review the details and select the **Invite** button if everything looks good.

An email invitation is sent automatically.

1. After you send the invitation, the user account is automatically added to the directory as a guest.

   ![Screenshot showing the new guest user in the directory.](https://learn.microsoft.com/en-us/entra/external-id/media/quickstart-add-users-portal/new-guest-user-directory.png)

## Accept the invitation

Now sign in as the guest user to see the invitation.

1. Sign in to your test guest user's email account.
2. In your inbox, open the email from "Microsoft Invitations on behalf of Contoso."

   ![Screenshot showing the B2B invitation email.](https://learn.microsoft.com/en-us/entra/external-id/media/quickstart-add-users-portal/quickstart-users-portal-email-small.png)
3. In the email body, select **Accept invitation**. A **Permission requested by:** page opens in the browser.

   ![Screenshot showing the Review permissions page.](https://learn.microsoft.com/en-us/entra/external-id/media/quickstart-add-users-portal/consent-screen.png)
4. Select **Accept**.
5. The **My Apps** page opens. Because we haven't assigned any apps to this guest user, you'll see the message "There are no apps to show." In a real-life scenario, you would [add the guest user to an app](https://learn.microsoft.com/en-us/entra/external-id/add-users-administrator#add-guest-users-to-an-application) so the app would appear here.

## Clean up resources

When no longer needed, delete the test guest user.

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least a [User Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#user-administrator).
2. Browse to **Entra ID** > **Users** > **User settings**.
3. Select the test user, and then select **Delete user**.

## Next steps

In this quickstart, you created a guest user in the Microsoft Entra admin center and sent an invitation to share apps. Then you viewed the redemption process from the guest user's perspective, and verified that the guest user was able to access their My Apps page. To learn more about adding guest users for collaboration, see [Add Microsoft Entra B2B collaboration users in the Microsoft Entra admin center](https://learn.microsoft.com/en-us/entra/external-id/add-users-administrator). To learn more about adding guest users with PowerShell, see [Add and invite guests with PowerShell](https://learn.microsoft.com/en-us/entra/external-id/b2b-quickstart-invite-powershell). You can also bulk invite guest users [via the admin center](https://learn.microsoft.com/en-us/entra/external-id/tutorial-bulk-invite) or [via PowerShell](https://learn.microsoft.com/en-us/entra/external-id/bulk-invite-powershell).
