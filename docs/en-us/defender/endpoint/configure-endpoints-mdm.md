<!-- Source: https://learn.microsoft.com/en-us/defender-endpoint/configure-endpoints-mdm -->
<!-- Sitemap-Last-Modified: 2026-08-25 -->

# Onboard Windows devices to Microsoft Defender for Endpoint by using Microsoft Intune

Note

The Defender deployment tool can be used to deploy Defender endpoint security on Windows and Linux devices. The tool is a lightweight, self-updating application that streamlines the deployment process. For more information, see [Deploy Microsoft Defender endpoint security to Windows devices using the Defender deployment tool](https://learn.microsoft.com/en-us/defender-endpoint/defender-deployment-tool-windows) and [Deploy Microsoft Defender endpoint security to Linux devices using the Defender deployment tool \(preview\)](https://learn.microsoft.com/en-us/defender-endpoint/linux-install-with-defender-deployment-tool).

Use Microsoft Intune to onboard Windows 10 and Windows 11 devices to Microsoft Defender for Endpoint. Onboarding configures devices to communicate with Defender for Endpoint for threat detection and device risk assessment. You can also use Intune to offboard devices that no longer need monitoring.

Defender for Endpoint supports mobile device management \(MDM\) configuration through Open Mobile Alliance Uniform Resource Identifier \(OMA-URI\) settings. For more information, see [WindowsAdvancedThreatProtection CSP](https://learn.microsoft.com/en-us/windows/client-management/mdm/windowsadvancedthreatprotection-csp) and [WindowsAdvancedThreatProtection DDF file](https://learn.microsoft.com/en-us/windows/client-management/mdm/windowsadvancedthreatprotection-ddf).

## Before you begin

- Enroll the devices in Microsoft Intune as your MDM solution. For more information, see [Device enrollment in Microsoft Intune](https://learn.microsoft.com/en-us/intune/intune-service/fundamentals/deployment-guide-enrollment).
- To create endpoint detection and response \(EDR\) policies, use an account with the **Endpoint Security Manager** role or equivalent permissions.

Intune is a separate product that's not included with every Defender for Endpoint subscription. You need a subscription that includes Intune, or you can buy Intune separately as a standalone subscription or add-on. For details, see [Microsoft Intune licensing](https://learn.microsoft.com/en-us/intune/intune-service/fundamentals/licenses). If you don't have Intune, review the other methods in [Identify Defender for Endpoint architecture and deployment method](https://learn.microsoft.com/en-us/defender-endpoint/deployment-strategy).

## Onboard devices using Microsoft Intune

Review [Defender for Endpoint architecture and deployment methods](https://learn.microsoft.com/en-us/defender-endpoint/deployment-strategy) to select the appropriate onboarding method for your environment.

To connect Intune to Defender for Endpoint and onboard devices, follow the instructions in [Configure Microsoft Defender for Endpoint with Intune and onboard devices](https://learn.microsoft.com/en-us/intune/device-security/microsoft-defender/configure-integration).

Note

- The **Health Status for onboarded devices** policy uses read-only properties and can't be remediated.
- The diagnostic data reporting frequency setting was added in Windows 10, version 1703. In Intune EDR policies, the setting is deprecated and doesn't affect new devices.
- Onboarding a device to Defender for Endpoint also onboards it to [Endpoint data loss prevention \(DLP\)](https://learn.microsoft.com/en-us/purview/endpoint-dlp-learn-about).

## Run a detection test to verify onboarding

After onboarding the device, you can choose to run a detection test to verify that a device is properly onboarded to the service. For more information, see [Run a detection test on a newly onboarded Microsoft Defender for Endpoint device](https://learn.microsoft.com/en-us/defender-endpoint/run-detection-test).

## Offboard devices using Mobile Device Management tools

For security reasons, the package used to offboard devices expires seven days after you download it. Expired offboarding packages sent to a device are rejected. When you download an offboarding package, the portal displays its expiration date, which is also included in the package name.

Note

To avoid unpredictable policy collisions, don't deploy onboarding and offboarding policies on a device at the same time.

1. Get the offboarding package from the Defender portal.

   On the **Offboarding** page in the Defender portal at [https://security.microsoft.com/securitysettings/endpoints/offboarding](https://security.microsoft.com/securitysettings/endpoints/offboarding), configure the following settings:

   1. At the top of the page, select **Windows 10 and Windows 11**.
   2. In the **Offboard a device** section that appears, select **Mobile Device Management / Microsoft Intune** as the **Deployment method**.
   3. At the bottom of the page, select **Download package**, select **Download** in the confirmation dialog, and then save the `WindowsDefenderATPOffboardingPackage_valid_until_YYYY-MM-DD.offboarding.zip` file in a location that's easy to find.

2. Extract the contents of the `.zip` file \(a file named `WindowsDefenderATP_valid_until_YYYY-MM-DD.offboarding`\) to a shared, read-only location that's accessible to the admins who are responsible for deploying the package.
3. In the Microsoft Intune admin center, use one of the following deployment methods:

   - **Custom configuration policy**: To create a **Windows** device configuration policy, see [Create a device configuration profile in Microsoft Intune](https://learn.microsoft.com/en-us/intune/device-configuration/create-device-profile) \(opens in a new tab in the Intune documentation\). When you create the policy, use these specific settings:

     - **Platform**: Select **Windows 10 and later**.
     - **Profile type**: Select **Templates**.
     - **Template name**: Select **Custom**.
     - **Configuration settings** tab: Add the following settings:

       - **OMA-URI**: Enter `./Device/Vendor/MSFT/WindowsAdvancedThreatProtection/Offboarding`.
       - **Data type**: Select **String**.
       - **Value**: Paste the value from the content of the `WindowsDefenderATP_valid_until_YYYY-MM-DD` offboarding file.

   - **EDR policy**: To create an **Endpoint detection and response** policy, see [Deploy endpoint detection and response policy with Intune](https://learn.microsoft.com/en-us/intune/device-configuration/endpoint-security/deploy-edr) \(opens in a new tab in the Intune documentation\). When you create the policy, use these specific settings:

     - **Platform**: Select **Windows**.
     - **Profile**: Select **Endpoint detection and response**.
     - **Configuration settings** tab:

       - **Microsoft Defender for Endpoint client configuration package type**: Select **Offboard**.
       - In the **Offboarding \(Device\)** setting that appears, paste the value from the content of the `WindowsDefenderATP_valid_until_YYYY-MM-DD` offboarding file.

Important

The **Health Status for offboarded devices** policy uses read-only properties and can't be remediated.

Offboarding stops the device from sending new detection, vulnerability, and security data to Defender for Endpoint. Historical data remains in the Defender portal until the configured retention period expires. The device profile, without data, remains in the device inventory for up to 180 days. For more information, see [Offboard devices](https://learn.microsoft.com/en-us/defender-endpoint/offboard-machines).

## Related content

- [Onboard Windows devices using Group Policy](https://learn.microsoft.com/en-us/defender-endpoint/configure-endpoints-gp)
- [Onboard Windows devices using Microsoft Configuration Manager](https://learn.microsoft.com/en-us/defender-endpoint/configure-endpoints-sccm)
- [Onboard Windows devices using a local script](https://learn.microsoft.com/en-us/defender-endpoint/configure-endpoints-script)
- [Onboard non-persistent virtual desktop infrastructure \(VDI\) devices](https://learn.microsoft.com/en-us/defender-endpoint/configure-endpoints-vdi)
- [Run a detection test on a newly onboarded Microsoft Defender for Endpoint device](https://learn.microsoft.com/en-us/defender-endpoint/run-detection-test)
- [Troubleshoot Microsoft Defender for Endpoint onboarding issues](https://learn.microsoft.com/en-us/defender-endpoint/troubleshoot-onboarding)
