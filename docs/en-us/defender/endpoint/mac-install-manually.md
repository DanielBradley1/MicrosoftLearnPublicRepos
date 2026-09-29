<!-- Source: https://learn.microsoft.com/en-us/defender-endpoint/mac-install-manually -->
<!-- Sitemap-Last-Modified: 2026-09-19 -->

# Manually deploy Microsoft Defender for Endpoint on macOS

> Want to experience Defender for Endpoint? [Sign up for a free trial](https://go.microsoft.com/fwlink/p/?linkid=2225630).

You can use manual deployment to install and onboard Microsoft Defender for Endpoint on an individual evaluation or test Mac without using mobile device management \(MDM\). For centrally managed production devices, choose an MDM method in [Deploy Defender for Endpoint on macOS](https://learn.microsoft.com/en-us/defender-endpoint/microsoft-defender-endpoint-mac#deploy-defender-for-endpoint-on-macos).

Complete the following tasks:

- [Download installation and onboarding packages](#download-installation-and-onboarding-packages)
- [Install the application](#install-the-application)
- [Approve system extensions and macOS permissions](#approve-system-extensions-and-macos-permissions)
- [Onboard the device](#onboard-the-device)
- [Verify the deployment](https://learn.microsoft.com/en-us/defender-endpoint/microsoft-defender-endpoint-mac#verify-the-deployment)

## Prerequisites

Before you start, review the [Defender for Endpoint on macOS prerequisites](https://learn.microsoft.com/en-us/defender-endpoint/microsoft-defender-endpoint-mac-prerequisites). You need local administrator privileges and a supported Mac that meets the licensing, system, permission, and network requirements.

Important

Manual installation requires changes to macOS privacy and security settings. For Apple's instructions, see [Change Privacy & Security settings on Mac](https://support.apple.com/guide/mac-help/change-privacy-security-settings-on-mac-mchl211c911f/mac).

## Download installation and onboarding packages

Download the installation and onboarding packages from the Microsoft Defender portal:

Warning

Repackaging the Defender for Endpoint installation package is not a supported scenario. Doing so can negatively impact the integrity of the product and lead to adverse results, including but not limited to triggering tampering alerts and updates failing to apply.

1. On the **Onboarding** page in the Microsoft Defender portal in the Microsoft Defender portal at [https://security.microsoft.com/securitysettings/endpoints/onboarding](https://security.microsoft.com/securitysettings/endpoints/onboarding), select the following options:

   - **Step 1: Select an operating system to start deployment**: Select **macOS**.
   - **Connectivity type**: Select **Streamlined**.
   - **Deployment method**: Verify **Local script \(for up to 10 devices\)** is selected.

2. Select **Download installation package**, to download and save the `wdav.pkg` file.
3. Select **Download onboarding package** to download and save the `WindowsDefenderATPOnboardingPackage.zip` in the same folder.
4. Extract `WindowsDefenderATPOnboardingPackage.zip` to get the `WindowsDefenderATPOnboarding.mobileconfig` file.
5. Confirm that `wdav.pkg` and `WindowsDefenderATPOnboarding.mobileconfig` exist on the Mac where you want to deploy Defender for Endpoint.

## Install the application

Install `wdav.pkg` by using Finder or Terminal.

### Install by using Finder

To use the graphical installer:

1. In Finder, locate and open `wdav.pkg`.
2. Select **Continue**.
3. Review the **Software License Agreement**, and then select **Continue**.
4. Select **Agree** to accept the license agreement.
5. On the **Destination Select** page, select the installation disk, and then select **Continue**.
6. To use a different disk, select **Change Install Location...**.
7. Select **Install**.
8. Enter the local administrator password when prompted.
9. Select **Install Software**.

### Install by using Terminal

If `wdav.pkg` is in `/Users/admin/Downloads`, run the following command to install the application:

```console
sudo installer -pkg /Users/admin/Downloads/wdav.pkg -target /
```

## Approve system extensions and macOS permissions

After installation, [approve the system extensions and grant the applicable macOS permissions](https://learn.microsoft.com/en-us/defender-endpoint/manage-sys-extensions-manual-deployment). The procedure covers Full Disk Access, Accessibility, and notifications. When prompted to allow Microsoft Defender to filter network content, select **Allow**.

When macOS notifies you that Microsoft Defender added background items, keep the Microsoft Defender and Microsoft Corporation items enabled. If you use Bluetooth-based Device Control policies, select **Allow** when macOS prompts you to grant Microsoft Defender Bluetooth access.

For the required extension identifiers and permissions, see [System extensions and macOS permissions](https://learn.microsoft.com/en-us/defender-endpoint/microsoft-defender-endpoint-mac-prerequisites#system-extensions-and-macos-permissions). To resolve extension approval problems, see [Troubleshoot system extension issues](https://learn.microsoft.com/en-us/defender-endpoint/mac-support-sys-ext).

## Onboard the device

Install the onboarding configuration profile:

1. In Finder, open `WindowsDefenderATPOnboarding.mobileconfig`.
2. On the Mac, open the Apple menu, select **System Settings**, select **General** in the sidebar, and then select **Device Management**.
3. In the **Downloaded** section, double-click the onboarding profile.
4. Review the profile, and then select **Continue** or **Install**. Enter the local administrator password if prompted.

For more information about manually installing a configuration profile, see [Use configuration profiles to standardize settings on Mac computers](https://support.apple.com/guide/mac-help/configuration-profiles-standardize-settings-mh35561/mac).

After onboarding, the Microsoft Defender icon appears in the macOS menu bar.

![Screenshot of the Microsoft Defender icon in the macOS menu bar.](https://learn.microsoft.com/en-us/defender-endpoint/media/mdatp-icon-bar.png)

Use the shared [deployment verification procedure](https://learn.microsoft.com/en-us/defender-endpoint/microsoft-defender-endpoint-mac#verify-the-deployment) to confirm the organization identifier and service connectivity. Then run an [antivirus detection test](https://learn.microsoft.com/en-us/defender-endpoint/validate-antimalware) and an [endpoint detection and response \(EDR\) detection test](https://learn.microsoft.com/en-us/defender-endpoint/edr-detection).

If onboarding doesn't assign a license or connect the device to the service, see [Troubleshoot license issues](https://learn.microsoft.com/en-us/defender-endpoint/mac-support-license) and [Troubleshoot cloud connectivity issues](https://learn.microsoft.com/en-us/defender-endpoint/troubleshoot-cloud-connect-mdemac).

## Troubleshoot installation

The installer writes detailed errors to the [installation log](https://learn.microsoft.com/en-us/defender-endpoint/mac-resources#logging-installation-issues). Use the following resources to troubleshoot manual deployment:

- [Troubleshoot system extension issues in Microsoft Defender for Endpoint on macOS](https://learn.microsoft.com/en-us/defender-endpoint/mac-support-sys-ext)
- [Troubleshoot installation issues for Microsoft Defender for Endpoint on macOS](https://learn.microsoft.com/en-us/defender-endpoint/mac-support-install)
- [Troubleshoot license issues for Microsoft Defender for Endpoint on macOS](https://learn.microsoft.com/en-us/defender-endpoint/mac-support-license)
- [Troubleshoot cloud connectivity issues for Microsoft Defender for Endpoint on macOS](https://learn.microsoft.com/en-us/defender-endpoint/troubleshoot-cloud-connect-mdemac)
- [Troubleshoot performance issues for Microsoft Defender for Endpoint on macOS](https://learn.microsoft.com/en-us/defender-endpoint/mac-support-perf)

## Uninstall Defender for Endpoint

Follow the [Defender for Endpoint uninstallation procedure](https://learn.microsoft.com/en-us/defender-endpoint/mac-resources#uninstalling) to offboard the device and remove the application.

Tip

To share product feedback, open Microsoft Defender on the Mac, and then select **Help** > **Send feedback**.

## Related content

- [Microsoft Defender for Endpoint on macOS overview](https://learn.microsoft.com/en-us/defender-endpoint/microsoft-defender-endpoint-mac).
- [Configure Defender for Endpoint on macOS](https://learn.microsoft.com/en-us/defender-endpoint/mac-preferences).
- [Configure potentially unwanted application protection](https://learn.microsoft.com/en-us/defender-endpoint/mac-pua).
- [Configure network protection](https://learn.microsoft.com/en-us/defender-endpoint/network-protection-macos).
- [Configure Device Control](https://learn.microsoft.com/en-us/defender-endpoint/mac-device-control-overview).
- [Configure tamper protection](https://learn.microsoft.com/en-us/defender-endpoint/tamper-protection-macos-configure).
- [Get started with Microsoft Purview Endpoint data loss prevention](https://learn.microsoft.com/en-us/purview/endpoint-dlp-getting-started).
- [Defender for Endpoint on macOS resources](https://learn.microsoft.com/en-us/defender-endpoint/mac-resources).
- [Configure Defender for Endpoint policies in Jamf Pro](https://learn.microsoft.com/en-us/defender-endpoint/mac-jamfpro-policies).
- [Deploy Defender for Endpoint by using Jamf Pro](https://learn.microsoft.com/en-us/defender-endpoint/mac-install-with-jamf).
- [Deploy Defender for Endpoint by using another MDM solution](https://learn.microsoft.com/en-us/defender-endpoint/mac-install-with-other-mdm).
