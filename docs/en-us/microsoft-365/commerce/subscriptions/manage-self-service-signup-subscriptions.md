<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/commerce/subscriptions/manage-self-service-signup-subscriptions?view=o365-worldwide -->
<!-- Sitemap-Last-Modified: 2026-02-03 -->

# Manage self-service sign-up subscriptions in the Microsoft 365 admin center

## What are self-service sign-up subscriptions?

There are a limited number of free self-service sign-up subscriptions available for users in your organization to sign up for. A user can only sign up for and use a self-service sign-up subscription for themselves. You manage self-service sign-up subscriptions by blocking users from signing up, and by deleting free subscriptions that users signed up for. For more information about self-service sign-up and the available subscriptions, see [Using up self-service sign in your organization](https://learn.microsoft.com/en-us/microsoft-365/admin/misc/self-service-sign-up?view=o365-worldwide).

## Before you begin

You must be at least a Billing Administrator to perform the tasks in this article. For more information, see [About admin roles](https://learn.microsoft.com/en-us/microsoft-365/admin/add-users/about-admin-roles?view=o365-worldwide).

## View a list of self-service sign-up subscriptions

Tip

If you're using Microsoft 365 operated by 21Vianet in China, use the following link to access the admin center: [https://portal.partner.microsoftonline.cn/](https://go.microsoft.com/fwlink/p/?linkid=513813)

1. In the Microsoft 365 admin center, go to the **Billing** > [Your products](https://go.microsoft.com/fwlink/p/?linkid=842054) page.
2. On the **Products** tab, select the filter icon, then select **Free**. A list of all self-service sign-up subscriptions is displayed.

## How are these subscriptions different from self-service purchase subscriptions?

Self-service sign-up subscriptions are free and are available for a larger list of products than self-service purchase subscriptions. When a user signs up for a self-service purchase subscription, they're responsible for paying for it. For more information, see [Self-service purchase FAQ](https://learn.microsoft.com/en-us/microsoft-365/commerce/subscriptions/self-service-purchase-faq?view=o365-worldwide).

## Block users from signing up

You use the [**Update-MgPolicyAuthorizationPolicy**](https://learn.microsoft.com/en-us/powershell/module/microsoft.graph.identity.signins/update-mgpolicyauthorizationpolicy?view=graph-powershell-1.0&preserve-view=true) cmdlet with the **AllowedToSignUpEmailBasedSubscriptions** parameter to control whether users can sign up for self-service sign-up subscriptions. For more information, see [How do I control self-service settings?](https://learn.microsoft.com/en-us/azure/active-directory/users-groups-roles/directory-self-service-signup#how-do-i-control-self-service-settings)

## Delete a self-service sign-up subscription

Important

When you delete a self-service sign-up subscription, you block all users from accessing their data and email and delete all data and email.

Tip

If you're using Microsoft 365 operated by 21Vianet in China, use the following link to access the admin center: [https://portal.partner.microsoftonline.cn/](https://go.microsoft.com/fwlink/p/?linkid=513813)

1. In the admin center, go to the **Billing** > [Your products](https://go.microsoft.com/fwlink/p/?linkid=842054) page.
2. On the **Products** tab, select the filter icon, then select **Free**.
3. Select the self-service sign-up subscription that you want to delete.
4. On the subscription details page, in the **Subscriptions and payment settings** section, select **Delete subscription**.
5. In the **Delete subscription** pane, select the check box, then select **Delete subscription**.

## I have a self-service sign-up subscription that blocks directory deletion

The self-service sign-up products that individual users can sign up for also create a guest user for authentication in your Microsoft Entra directory. To avoid data loss, these self-service products block directory deletions until they're fully deleted from the directory. Only a Microsoft Entra admin can delete a directory. For more information, see [Delete a directory in Microsoft Entra ID](https://learn.microsoft.com/en-us/azure/active-directory/users-groups-roles/directory-delete-howto).
