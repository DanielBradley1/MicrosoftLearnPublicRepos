<!-- Source: https://learn.microsoft.com/en-us/intune/device-security/compliance/configure-wsl -->
<!-- Sitemap-Last-Modified: 2026-05-20 -->

# Evaluate compliance for Windows Subsystem for Linux

Create a Microsoft Intune policy that checks the compliance of devices running Windows Subsystem for Linux \(WSL\). Microsoft Intune incorporates the WSL compliance results into the overall compliance state of the host device so you can see the whole health of the device.

This article applies to Windows and describes how to set up compliance checks for WSL.

## Requirements

![](https://learn.microsoft.com/en-us/intune/media/icons/16/devices.svg) **Device platform requirements**

> Windows

![](https://learn.microsoft.com/en-us/intune/media/icons/16/plugin.svg) **Plugins requirements**

> You must install the [Intune WSL plugin](https://go.microsoft.com/fwlink/?linkid=2296896) for compliance evaluation.

![](https://learn.microsoft.com/en-us/intune/media/icons/16/rbac.svg) **Roles requirements**

> Sign in to the Microsoft Intune admin center with the following role:
> 
> - Built-in [Intune Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#intune-administrator) Microsoft Entra role

The Microsoft Intune management extension must be installed on the target device. Make sure devices meet one of the following conditions so that the management extension can install:

- Assign a PowerShell script or a proactive remediation to the user or device.
- Deploy a Win32 app or Microsoft Store app to the user or device.
- Assign a custom compliance policy to the user or device.

## Before you begin

Unassign and remove existing custom compliance policies for WSL. Then review the [limitations](#limitations) with WSL settings in compliance policies so that you know what to expect.

## Add Intune WSL plugin as a Win32 app

Create a Win32 app policy for the [Intune WSL plugin](https://github.com/microsoft/shell-intune-samples/blame/master/Linux/WSL/IntuneWSLPluginInstaller/IntuneWSLPluginInstaller.msi), and assign it to the target Microsoft Entra group.

1. Use the [Microsoft Win32 Content Prep Tool](https://github.com/Microsoft/Microsoft-Win32-Content-Prep-Tool) to convert the Intune WSL plugin to the *.intunewin* format. For more information, see [Convert the Win32 app content](https://learn.microsoft.com/en-us/intune/app-management/deployment/create-win32-package#convert-the-win32-app-content).
2. Sign in to the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431).
3. Go to **Apps** > **All Apps** > **Add**.
4. For **App type**, scroll down to **Other**, and then select **Windows app \(Win32\)**.
5. Choose **Select**. The **Add app** steps appear.
6. Choose **Select app package file**.
7. Select the **Folder** button and browse your files for the app package file. Upload the Intune WSL plugin installation file with the *.intunewin* extension.
8. Select **OK** to continue.
9. Enter the following app information:

   - **Select file**: The app package file you selected in the previous step appears here. Select the file to upload a different installation package file for the Intune WSL plugin.
   - **Name**: Enter **Intune WSL Plugin**.
   - **Description**: Select **Edit Description** to enter a description for the app. For example, you can describe its purpose or how your organization plans to use it. This setting is optional but recommended.
   - **Publisher**: Enter **Microsoft Intune**.

10. Select **Next** to go to **Program**.
11. Review the settings that are prepopulated so that you're familiar with how the app behaves. Leave the settings as-is.
12. Select **Next** to go to **Requirements**.
13. Enter the requirements devices must meet to install the app.
14. Select **Next** to go to **Detection rules**.
15. Review the detection rules that are prepopulated. These rules are app-specific and detect the presence of the app. Leave the settings as-is.
16. Select **Next** to go to **Dependencies**. Leave the settings as-is.
17. Select **Next** to go to **Supersedence**. Leave the settings as-is.
18. Select **Next** to go to **Assignments**.
19. To assign the policy, add Microsoft Entra users under **Required**.
20. Select **Next** to go to **Review + create**.
21. Review the summary, and then select **Create** to save the policy.

Note

When you create a compliance policy with WSL settings, it automatically generates a read-only custom script. Editing the compliance policy also edits the associated custom script. These scripts appear in the Microsoft Intune admin center in **Devices** > **Compliance** > **Scripts** and are called *Built-in WSL Compliance-< compliance policy id >*.

## Limitations

This section describes the known limitations when using the Intune WSL plugin for compliance evaluation.

- Compliance evaluation requires the installed Linux distributions in WSL to run at least once before it works. If you install a Linux distribution by using the `--no-launch` [command for WSL](https://learn.microsoft.com/en-us/windows/wsl/basic-commands), the compliance evaluation doesn't work.
- Compliance evaluation might not function as expected on custom Linux images or Linux images without the `etc/os-release` directory.
- Even with the Intune WSL plugin, malicious software or user actions can compromise the compliance evaluation mechanism.

## Next steps

- [Create a compliance policy](https://learn.microsoft.com/en-us/intune/device-security/compliance/create-policy#create-the-policy), and set the **Platform** to **Windows 10 and later**. For more information about the compliance settings for Windows Subsystem for Linux, see [Windows Subsystem for Linux](https://learn.microsoft.com/en-us/intune/device-security/compliance/ref-windows-settings#windows-subsystem-for-linux).
- [Add actions for noncompliant devices](https://learn.microsoft.com/en-us/intune/device-security/compliance/configure-noncompliance-actions) and [use scope tags to filter policies](https://learn.microsoft.com/en-us/intune/fundamentals/role-based-access-control/scope-tags).
- [Monitor your compliance policies](https://learn.microsoft.com/en-us/intune/device-security/compliance/monitor-policy).
- For troubleshooting help, see [Troubleshooting Windows Subsystem for Linux](https://learn.microsoft.com/en-us/windows/wsl/troubleshooting).
