<!-- Source: https://learn.microsoft.com/en-us/defender-endpoint/configure-endpoints-script -->
<!-- Sitemap-Last-Modified: 2026-09-22 -->

# Onboard Windows devices to Microsoft Defender for Endpoint with a local script

You can use a local script to onboard up to 10 supported Windows client or Windows Server devices to Microsoft Defender for Endpoint. This method is useful for evaluating the service before you select a deployment method for a larger environment. Before you begin, review the prerequisites, and then download and run the script, configure sample collection, verify onboarding, or offboard devices.

Important

Use the local script on 10 devices or fewer. For a production deployment, select a scalable method such as Group Policy, Microsoft Configuration Manager, Microsoft Intune, or the Defender deployment tool. To compare the available methods, see [Identify Defender for Endpoint architecture and deployment methods](https://learn.microsoft.com/en-us/defender-endpoint/deployment-strategy) and [other deployment options for Windows client devices](https://learn.microsoft.com/en-us/defender-endpoint/onboard-client).

Note

The Defender deployment tool can be used to deploy Defender endpoint security on Windows and Linux devices. The tool is a lightweight, self-updating application that streamlines the deployment process. For more information, see [Deploy Microsoft Defender endpoint security to Windows devices using the Defender deployment tool](https://learn.microsoft.com/en-us/defender-endpoint/defender-deployment-tool-windows) and [Deploy Microsoft Defender endpoint security to Linux devices using the Defender deployment tool \(preview\)](https://learn.microsoft.com/en-us/defender-endpoint/linux-install-with-defender-deployment-tool).

## Prerequisites

- Review the [minimum requirements for Microsoft Defender for Endpoint](https://learn.microsoft.com/en-us/defender-endpoint/minimum-requirements) and [configure device connectivity](https://learn.microsoft.com/en-us/defender-endpoint/configure-device-connectivity).
- To download onboarding and offboarding packages, you need full access to Defender for Endpoint. The Microsoft Entra [Security Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#security-administrator) role grants this access. For more information, see [Assign basic permissions](https://learn.microsoft.com/en-us/defender-endpoint/basic-permissions).
- Sign in to the device with an account that has local administrator permissions.

## Onboard devices with a local script

Download the onboarding package from the Microsoft Defender portal, and then run the included script on each device.

1. On the **Onboarding** page in the Microsoft Defender portal at [https://security.microsoft.com/securitysettings/endpoints/onboarding](https://security.microsoft.com/securitysettings/endpoints/onboarding), configure the package:

   1. **Step 1: Select an operating system to start deployment**: Select the operating-system version group for the device. Don't select **Windows**, which starts the separate [Defender deployment tool workflow](https://learn.microsoft.com/en-us/defender-endpoint/defender-deployment-tool-windows).
   2. If **Connectivity type** is available, select the connectivity method for your environment:

      - **Standard**: Uses the full set of Defender for Endpoint service URLs.
      - **Streamlined**: Uses a smaller, consolidated set of service URLs. For more information, see [Onboard devices using streamlined connectivity](https://learn.microsoft.com/en-us/defender-endpoint/configure-device-connectivity).

   3. For **Deployment method**, select **Local script \(for up to 10 devices\)**.
   4. Select **Download onboarding package** to download `GatewayWindowsDefenderATPOnboardingPackage.zip`.

2. Extract the contents of the `.zip` file on the device to a location that's easy to find, such as the Desktop. The package contains `WindowsDefenderATPLocalOnboardingScript.cmd`.
3. Open Command Prompt as an administrator.
4. Go to the folder that contains `WindowsDefenderATPLocalOnboardingScript.cmd`. For example, the following command goes to the Desktop folder:

   ```dos
   if exist "%OneDrive%\Desktop" (cd /d "%OneDrive%\Desktop") else if exist "%USERPROFILE%\Desktop" cd /d "%USERPROFILE%\Desktop"
   ```

5. Run the onboarding script:

   ```dos
   WindowsDefenderATPLocalOnboardingScript.cmd
   ```

6. When the script displays **Press any key to continue...**, press any key to finish.

## Configure sample collection settings

Defender for Endpoint can collect files from an onboarded device when an analyst requests a file for deep analysis. The `AllowSampleCollection` registry value controls whether the device can respond to these requests:

- `0` \(`00000000`\): Don't allow sample sharing from the device.
- `1` \(`00000001`\): Allow sharing of all file types from the device. This setting is the default if the registry value doesn't exist.

To configure the setting manually, copy the following text into Notepad, set the `AllowSampleCollection` value, save the file with a `.reg` extension, and run the file on the device:

```text
Windows Registry Editor Version 5.00

[HKEY_LOCAL_MACHINE\SOFTWARE\Policies\Microsoft\Windows Advanced Threat Protection]
"AllowSampleCollection"=dword:00000000
```

## Verify device onboarding

After the script runs, verify that the device reports to Defender for Endpoint:

1. On the **Device inventory** page in the Microsoft Defender portal at [https://security.microsoft.com/machines?category=all-devices](https://security.microsoft.com/machines?category=all-devices), search for the device.
2. Open the device page, and verify that the device is onboarded and its sensor health state is active.

The device typically appears in the inventory within several minutes. Network connectivity and device state can delay reporting.

To generate a test alert and confirm end-to-end reporting, see [Run a detection test on a newly onboarded device](https://learn.microsoft.com/en-us/defender-endpoint/run-detection-test). If the device doesn't appear or report as expected, see [Troubleshoot Microsoft Defender for Endpoint onboarding issues](https://learn.microsoft.com/en-us/defender-endpoint/troubleshoot-onboarding).

## Offboard devices using a local script

The offboarding package expires seven days after you download it. Defender for Endpoint rejects expired packages, and the expiration date appears in the package file name.

Important

Don't run the onboarding and offboarding scripts on the same device at the same time. Complete onboarding or offboarding before you run the other script.

To offboard a device by using a local script, download and run the offboarding package:

1. On the **Offboarding** page in the Microsoft Defender portal at [https://security.microsoft.com/securitysettings/endpoints/offboarding](https://security.microsoft.com/securitysettings/endpoints/offboarding), configure the package:

   1. Select the operating-system version group for the device. Don't select **Windows**, which starts the separate [Defender deployment tool workflow](https://learn.microsoft.com/en-us/defender-endpoint/defender-deployment-tool-windows).
   2. For **Deployment method**, select **Local script \(for up to 10 devices\)**.
   3. Select **Download package**, and then select **Download** in the confirmation dialog.

2. Extract `WindowsDefenderATPOffboardingPackage_valid_until_YYYY-MM-DD.zip` on the device to a location that's easy to find, such as the Desktop. The package contains `WindowsDefenderATPOffboardingScript_valid_until_YYYY-MM-DD.cmd`.
3. Open Command Prompt as an administrator.
4. Go to the folder that contains the offboarding script. For example, the following command goes to the Desktop folder:

   ```dos
   if exist "%OneDrive%\Desktop" (cd /d "%OneDrive%\Desktop") else if exist "%USERPROFILE%\Desktop" cd /d "%USERPROFILE%\Desktop"
   ```

5. Run the offboarding script:

   ```dos
   WindowsDefenderATPOffboardingScript_valid_until_YYYY-MM-DD.cmd
   ```

Important

Offboarding stops the device from sending new detection, vulnerability, and security data to Defender for Endpoint. Historical data remains in the Defender portal until the configured retention period expires. The device profile, without data, remains in the device inventory for up to 180 days. For more information, see [Offboard devices](https://learn.microsoft.com/en-us/defender-endpoint/offboard-machines).

## Related content

- [Onboard Windows devices using Group Policy](https://learn.microsoft.com/en-us/defender-endpoint/configure-endpoints-gp)
- [Onboard Windows devices using Microsoft Configuration Manager](https://learn.microsoft.com/en-us/defender-endpoint/configure-endpoints-sccm)
- [Onboard Windows devices using Mobile Device Management tools](https://learn.microsoft.com/en-us/defender-endpoint/configure-endpoints-mdm)
- [Onboard non-persistent virtual desktop infrastructure \(VDI\) devices](https://learn.microsoft.com/en-us/defender-endpoint/configure-endpoints-vdi)
- [Run a detection test on a newly onboarded Microsoft Defender for Endpoint device](https://learn.microsoft.com/en-us/defender-endpoint/run-detection-test)
- [Troubleshoot Microsoft Defender for Endpoint onboarding issues](https://learn.microsoft.com/en-us/defender-endpoint/troubleshoot-onboarding)
