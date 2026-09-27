<!-- Source: https://learn.microsoft.com/en-us/intune/device-enrollment/windows/quickstart-automatic-mdm -->
<!-- Sitemap-Last-Modified: 2026-04-09 -->

# Step 4 - Set up automatic enrollment for Windows devices

In this article, you set up Microsoft Intune to automatically enroll Windows corporate-owned devices, and user-owned devices for bring-your-own-device \(BYOD\) deployments. You can scope automatic enrollment to some Microsoft Entra users, all users, or no users.

This article is [part of an Evaluate and Try series](https://learn.microsoft.com/en-us/intune/fundamentals/try-overview) that helps you evaluate Microsoft Intune's capabilities.

## Prerequisites

![](https://learn.microsoft.com/en-us/intune/media/icons/16/licensing.svg) **Licensing requirements**

> - A Microsoft Intune subscription. [Sign up for a free trial account](https://learn.microsoft.com/en-us/intune/fundamentals/free-trial-sign-up).
> - [Microsoft Entra ID P1 or P2](https://learn.microsoft.com/en-us/azure/active-directory/active-directory-get-started-premium) or the [Premium trial subscription](https://go.microsoft.com/fwlink/?LinkID=816845). You can activate a free Premium trial subscription during setup.

![](https://learn.microsoft.com/en-us/intune/media/icons/16/rbac.svg) **Roles requirements**

> Sign in to the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431) with the following role:
> 
> - Built-in **[Intune Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#intune-administrator)** Microsoft Entra role

![](https://learn.microsoft.com/en-us/intune/media/icons/16/configuration.svg) **Device configuration requirements**

> To complete this step, you must:
> 
> - [Create a user](https://learn.microsoft.com/en-us/intune/fundamentals/tenant-administration/quickstart-create-user).
> - [Create a group](https://learn.microsoft.com/en-us/intune/fundamentals/tenant-administration/quickstart-create-group).

## Set up automatic enrollment

In this example, you configure Microsoft Intune mobile device management \(MDM\) enrollment settings so that corporate-owned and personal devices automatically enroll in Microsoft Intune. *MDM user scope* enables automatic enrollment for Microsoft Intune device management.

1. In the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431), go to **Devices** > **Enrollment**.
2. Go to the **Windows** tab. Then select **Automatic Enrollment**.

   Important

   Automatic MDM enrollment is a premium Microsoft Entra feature available for Microsoft Entra ID Premium subscribers. If you can't see the automatic enrollment settings, select **Automatic MDM enrollment is available only for Microsoft Entra ID Premium subscribers** to activate a free trial.
3. Select **Microsoft Intune**.
4. Configure the MDM and WIP user scope.

   1. For **MDM user scope** select **All**. Or you can select **Some** and select **Contoso Testers** as the group. Make sure users aren't members of a group targeted by the WIP user scope.
   2. For **WIP user scope**, select **None**. You're only setting up automatic enrollment for mobile device management.

5. Use the default values for the remaining settings on the page.
6. Choose **Save**.

Important

If you configure both user scope types for the same user:

- The MDM user scope takes precedence if they're on a corporate-owned device. The device automatically enrolls in Microsoft Intune when they set it up for work.
- The WIP user scope takes precedence if they bring their own device. The device doesn't enroll in Microsoft Intune for device management. Microsoft Purview Information Protection policies are applied if you configured them.

## Clean up resources

To reconfigure Intune automatic enrollment, see [Set up enrollment for Windows devices](https://learn.microsoft.com/en-us/intune/device-enrollment/windows/enable-automatic-mdm).

## Next steps

In this task, you learned how to set up automatic enrollment for devices running Windows. For more information about device enrollment, see [Device enrollment overview](https://learn.microsoft.com/en-us/intune/device-enrollment/guide).

To continue evaluating Microsoft Intune, go to the next step:

[Step 5 - Enroll your Windows device](https://learn.microsoft.com/en-us/intune/device-enrollment/windows/quickstart-first-device)
