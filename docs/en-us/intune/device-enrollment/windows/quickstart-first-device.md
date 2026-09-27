<!-- Source: https://learn.microsoft.com/en-us/intune/device-enrollment/windows/quickstart-first-device -->
<!-- Sitemap-Last-Modified: 2026-04-09 -->

# Step 5 - Enroll a Windows device in Microsoft Intune

Enrollment ensures that all devices trying to access data within your organization are secure and compliant with your policies and requirements. Upon enrollment, the device gets access to resources like work email, files, VPN, and Wi-Fi. Employees and students who want remote access to work or school resources can also enroll their devices into Microsoft Intune.

This article is [part of an Evaluate and Try series](https://learn.microsoft.com/en-us/intune/fundamentals/try-overview) that helps you evaluate Microsoft Intune's capabilities.

In this article, you:

- Try out the device user experience by enrolling a device running Windows into Microsoft Intune.
- Try out the admin user experience by verifying the enrollment in the Microsoft Intune admin center.

## Prerequisites

![](https://learn.microsoft.com/en-us/intune/media/icons/16/licensing.svg) **Licensing requirements**

> - A Microsoft Intune subscription. [Sign up for a free trial account](https://learn.microsoft.com/en-us/intune/fundamentals/free-trial-sign-up).

![](https://learn.microsoft.com/en-us/intune/media/icons/16/rbac.svg) **Roles requirements**

> Sign in to the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431) with the following role:
> 
> - Built-in **[Intune Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#intune-administrator)** Microsoft Entra role

![](https://learn.microsoft.com/en-us/intune/media/icons/16/configuration.svg) **Device configuration requirements**

> To complete this step, you must:
> 
> - Complete the evaluation step for [setting up automatic enrollment in Intune](https://learn.microsoft.com/en-us/intune/device-enrollment/windows/quickstart-automatic-mdm).
> - Be using a [supported Windows version](https://learn.microsoft.com/en-us/intune/fundamentals/ref-supported-platforms).

## Enroll device

These steps guide you through using the Settings app on a Windows device to enroll the device into Intune.

1. On the device, open the Settings app, and select **Accounts**.
2. Select **Access work or school**.
3. Select **Connect** to add a work or school account.

   [![Screenshot of Windows Settings, Accounts section, showing Access work or school with Connect button highlighted.](https://learn.microsoft.com/en-us/intune/device-enrollment/windows/media/quickstart-first-device/quickstart-enroll-windows-device-04.png)](https://learn.microsoft.com/en-us/intune/device-enrollment/windows/media/quickstart-first-device/quickstart-enroll-windows-device-04.png#lightbox)
4. Enter the username and password for your work account. If you followed the [create a user and assign a license](https://learn.microsoft.com/en-us/intune/fundamentals/tenant-administration/quickstart-create-user) evaluation step, you can use the user account that you created.
5. Wait for your device to finish registering. When you see the **You're all set!** screen, select **Done**. Your work account should now be visible under **Accounts**.

   [![Screenshot of Windows Settings showing a connected work or school account under Access work or school.](https://learn.microsoft.com/en-us/intune/device-enrollment/windows/media/quickstart-first-device/quickstart-enroll-windows-device-06.png)](https://learn.microsoft.com/en-us/intune/device-enrollment/windows/media/quickstart-first-device/quickstart-enroll-windows-device-06.png#lightbox)

   If you followed the previous steps, but still can't access your work or school email account and files, see [Troubleshoot Windows device access](https://learn.microsoft.com/en-us/intune/user-help/troubleshooting/troubleshoot-device-access-windows).

When the device is enrolled in Intune, it starts to receive the Intune policies you create. [Common questions, answers, and scenarios with policies and profiles in Microsoft Intune](https://learn.microsoft.com/en-us/intune/device-configuration/troubleshoot-device-profiles) provides more information about how policies and profiles work in Intune.

## Confirm device enrollment

1. Sign in to the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Select **Devices** > **All devices** to view the enrolled devices in Intune.
3. Verify that you have an additional device enrolled within Intune.

## Clean up resources

To unenroll the device, see [Remove your Windows device from management](https://learn.microsoft.com/en-us/intune/user-help/unenrollment/unenroll-windows).

## Next steps

In this task, you learned how to enroll a Windows device into Intune. For more information about the user experience on the device, see the following resources:

- [Windows device enrollment with Intune Company Portal](https://learn.microsoft.com/en-us/intune/user-help/enrollment/overview-windows)
- [What info can your company see when you enroll your device?](https://learn.microsoft.com/en-us/intune/user-help/enrollment/data-visibility)

You can also automate Windows device enrollment. To learn more, see [Windows enrollment guide for Microsoft Intune](https://learn.microsoft.com/en-us/intune/device-enrollment/windows/guide).

To continue evaluating Microsoft Intune, go to the next step:

[Step 6 - Set a required password length for Android devices](https://learn.microsoft.com/en-us/intune/device-security/compliance/quickstart-password-compliance-android)
