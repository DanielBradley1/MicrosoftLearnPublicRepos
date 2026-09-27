<!-- Source: https://learn.microsoft.com/en-us/intune/fundamentals/tenant-administration/quickstart-create-group -->
<!-- Sitemap-Last-Modified: 2026-04-16 -->

# Step 3 - Create a group to manage users

In this article, you use Intune to create a group based on an existing user. Use groups to manage your users and control your employees' access to your company resources. These resources can be part of your company's intranet or can be external resources, such as SharePoint sites, SaaS apps, or web apps.

This article is [part of an Evaluate and Try series](https://learn.microsoft.com/en-us/intune/fundamentals/try-overview) that helps you evaluate Microsoft Intune's capabilities.

## Prerequisites

![](https://learn.microsoft.com/en-us/intune/media/icons/16/licensing.svg) **Licensing requirements**

> - A Microsoft Intune subscription. [Sign up for a free trial account](https://learn.microsoft.com/en-us/intune/fundamentals/free-trial-sign-up).

![](https://learn.microsoft.com/en-us/intune/media/icons/16/rbac.svg) **Roles requirements**

> Sign in to the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431) with the following role:
> 
> - Built-in **[User Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#user-administrator)** Microsoft Entra role

## All users and All devices groups

When you create an Intune subscription, Intune automatically creates the **All Users** and **All Devices** groups. These groups have built-in optimizations. Use these groups when you want to apply policies to all users or all devices in your organization.

When you create your policies, assign your policies to these built-in groups or the groups you create.

For more information about using groups in Intune, like using filters, and assigning to user groups vs. device groups, see:

- [Assign policies in Microsoft Intune](https://learn.microsoft.com/en-us/intune/device-configuration/assign-device-profile)
- [Assign Apps to Groups With Microsoft Intune](https://learn.microsoft.com/en-us/intune/app-management/deployment/assign-groups)

## Create a group

In this step, you create a group. You use this group later in another task in this evaluation series.

To create a group:

1. In the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431), select **Groups** > **New group**.
2. In the **Group type** dropdown box, select **Security**.
3. In the **Group name** field, enter the name for the new group \(for example, **Contoso Testers**\).
4. Add a **Group description** for the group.
5. Set the **Membership type** to **Assigned**.
6. Under **Members**, select the link and add one or more members for the group from the list. If you created a user in [Step 2 - Create a user in Intune and assign the user a license](https://learn.microsoft.com/en-us/intune/fundamentals/tenant-administration/quickstart-create-user), you can add that user to this group.

   [![Screenshot of creating a group in Microsoft Intune.](https://learn.microsoft.com/en-us/intune/fundamentals/tenant-administration/media/quickstart-create-group/quickstart-use-groups-01.png)](https://learn.microsoft.com/en-us/intune/fundamentals/tenant-administration/media/quickstart-create-group/quickstart-use-groups-01.png#lightbox)
7. Choose **Select** > **Create**.

After you create the group, it appears in the list of **All groups**.

Note

By using the added support for soft-deleting groups by Microsoft Entra, Intune displays those groups as soft deleted in the admin center when they're in that state. When you soft-delete groups, the process removes their assignments. When you restore these groups, the process also restores any policy assignments.

## Next steps

In this article, you used Intune to create a group based on an existing user. For more information about adding groups to Intune, see [Add groups to organize users and devices](https://learn.microsoft.com/en-us/intune/fundamentals/tenant-administration/add-groups).

To continue evaluating Microsoft Intune, go to the next step:

[Step 4 - Set up automatic enrollment for Windows devices](https://learn.microsoft.com/en-us/intune/device-enrollment/windows/quickstart-automatic-mdm)
