<!-- Source: https://learn.microsoft.com/en-us/intune/app-management/protection/quickstart-create-assign-policy -->
<!-- Sitemap-Last-Modified: 2026-04-14 -->

# Step 9 - Create and assign an app protection policy in Microsoft Intune

In this article, you learn how to create and assign an app protection policy in Microsoft Intune to protect apps on user devices. App protection policies help ensure your apps meet your organization's data protection requirements, keeping corporate data secure.

This article is [part of an Evaluate and Try series](https://learn.microsoft.com/en-us/intune/fundamentals/try-overview) that helps you evaluate Microsoft Intune's capabilities.

## Prerequisites

![](https://learn.microsoft.com/en-us/intune/media/icons/16/licensing.svg) **Licensing requirements**

> - A Microsoft Intune subscription. [Sign up for a free trial account](https://learn.microsoft.com/en-us/intune/fundamentals/free-trial-sign-up).

![](https://learn.microsoft.com/en-us/intune/media/icons/16/rbac.svg) **Roles requirements**

> Sign in to the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431) with the following role:
> 
> - Built-in **[Application Manager](https://learn.microsoft.com/en-us/intune/fundamentals/role-based-access-control/ref-built-in-roles#application-manager)** Microsoft Intune role

![](https://learn.microsoft.com/en-us/intune/media/icons/16/configuration.svg) **Device configuration requirements**

> To complete this step, you must:
> 
> - [Create a user](https://learn.microsoft.com/en-us/intune/fundamentals/tenant-administration/quickstart-create-user).
> - [Create a group](https://learn.microsoft.com/en-us/intune/fundamentals/tenant-administration/quickstart-create-group).
> - [Enroll a device](https://learn.microsoft.com/en-us/intune/device-enrollment/windows/quickstart-automatic-mdm)
> - [Add and assign an app](https://learn.microsoft.com/en-us/intune/app-management/deployment/quickstart-add-assign).

## Create an app protection policy

Use the following steps to create an app protection policy:

1. Sign in to the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431) and select **Apps** > **Windows** > **Create**.
2. Enter the following details:

   - **Name**: *Windows content protection*
   - **Description**: *Users associated with this policy can't cut, copy, or paste any content between the assigned app and other nonmanaged apps on the device.*
   - **Enrollment state**: *With enrollment*

3. Under **Protected apps**, select **Add**. The **Add apps** pane is displayed.
4. Choose the apps that must adhere to this policy and select **OK**.
5. Select **Next** to display the **Required settings**.
6. Select **Allow Overrides** to set the Windows Information Protection mode. Selecting this option blocks enterprise data from leaving the protected app.
7. Select **Next** to display the **Advanced settings**.
8. Select **Next** to display the **Assignments**.
9. Select **Select groups to include**, select the users group, and select **Select**.

   You can only apply app protection policies to groups that contain users, not groups that contain devices.
10. Select **Next** to display the **Review + create** step.
11. Select **Create** to create your policy.

You see the app protection policy in Intune.

## Next steps

In this article, you created and assigned an app protection policy. Users of the app that have this policy assigned can't cut, copy, or paste any content between the assigned app and other unmanaged apps on the device. This type of protection helps protect your organization's data. For more information about app protection policies in Intune, see [What are app protection policies?](https://learn.microsoft.com/en-us/intune/app-management/protection/overview)

To continue evaluating Microsoft Intune, go to the next step:

[Step 10 - Create and assign a custom role](https://learn.microsoft.com/en-us/intune/fundamentals/role-based-access-control/quickstart-custom-role)
