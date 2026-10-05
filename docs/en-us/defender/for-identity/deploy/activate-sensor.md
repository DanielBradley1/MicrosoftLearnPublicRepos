<!-- Source: https://learn.microsoft.com/en-us/defender-for-identity/deploy/activate-sensor -->
<!-- Sitemap-Last-Modified: 2026-09-14 -->

# Activate the Microsoft Defender for Identity sensor v3.x

For complete protection of your on-premises deployment, activate the Microsoft Defender for Identity sensor v3.x on all eligible servers. Supported server types include domain controllers. They also include Active Directory Federation Services \(AD FS\), Active Directory Certificate Services \(AD CS\), and Microsoft Entra Connect servers that aren't domain controllers. Eligible servers must meet the sensor v3.x prerequisites, including Windows Server 2019 or later. For supported servers running older operating systems, [deploy the Defender for Identity sensor v2.x](https://learn.microsoft.com/en-us/defender-for-identity/deploy/install-sensor) instead.

Note

Activating the Defender for Identity sensor v3.x on AD FS, AD CS, and Microsoft Entra Connect servers that aren't domain controllers is in preview.

## Prerequisites

See [Microsoft Defender for Identity sensor v3.x prerequisites](https://learn.microsoft.com/en-us/defender-for-identity/deploy/deploy-sensor-v3) for system requirements and [Sensor version limitations](https://learn.microsoft.com/en-us/defender-for-identity/deploy/deploy-sensor-v3#sensor-version-limitations) for supported scenarios before activating the Defender for Identity sensor v3.x on eligible servers.

## Turn on automatic sensor activation

Note

When **Automatic sensor v3.x activation** is enabled, Defender for Identity automatically activates sensor v3.x on eligible domain controllers, AD FS, AD CS, or Microsoft Entra Connect servers that you onboard to Defender for Endpoint. The servers must run Windows Server 2019 or later.

Automatic activation doesn't install a separate Defender for Identity sensor package. It activates the sensor capability on eligible servers that are already onboarded to Defender for Endpoint. Servers that already have a Defender for Identity sensor aren't targeted by this flow.

On the **Advanced features** page in the Microsoft Defender portal at [https://security.microsoft.com/securitysettings/identities](https://security.microsoft.com/securitysettings/identities), use the **Automatic sensor v3.x activation** toggle to turn on automatic activation for eligible servers. Automatic activation applies only to eligible servers onboarded to Defender for Endpoint.

- Turn on the setting to automatically activate eligible servers when they're discovered.
- Turn off the setting to stop future automatic activations.

The **Advanced features** page also includes **Automatic Windows auditing configuration**. For details, see [Configure automatic Windows event auditing](https://learn.microsoft.com/en-us/defender-for-identity/deploy/configure-windows-event-collection#configure-defender-for-identity-to-collect-windows-events-automatically).

## Activate the Defender for Identity sensor v3.x

To activate the Defender for Identity sensor v3.x on an eligible server, follow these steps:

1. On the **Sensor management** tab of the **On-premises** page in the Microsoft Defender portal, select the eligible server where you want to activate Defender for Identity.
2. Select **Activate**, and confirm your selection when prompted.
3. When v3.x sensor activation for the selected server is complete, a green success banner appears. In the banner, select **Click here to see the onboarded servers**. The **Sensor management** tab opens, where you can check the sensor's health.

   [![Screenshot of the successful sensor activation banner with a link to view onboarded servers.](https://learn.microsoft.com/en-us/defender-for-identity/deploy/media/activated-sensor.png)](https://learn.microsoft.com/en-us/defender-for-identity/deploy/media/activated-sensor.png#lightbox)

## Onboard a domain controller without Defender for Endpoint deployment \(preview\)

Use onboarding without Defender for Endpoint deployment to activate the Defender for Identity sensor v3.x without first onboarding the domain controller to Defender for Endpoint:

Note

This onboarding method supports new Defender for Identity sensor v3.x deployments on eligible domain controllers that don't have sensor v2.x installed. The standalone onboarding package activates sensor v3.x on the Windows Sense platform in restricted identity-only mode. It doesn't deploy or license the full Defender for Endpoint experience. The server still requires connectivity to Defender for Endpoint cloud services because the underlying Sense component uses that infrastructure.

1. [Configure your network environment to ensure connectivity with Defender for Endpoint](https://learn.microsoft.com/en-us/defender-endpoint/configure-environment#enable-access-to-microsoft-defender-for-endpoint-service-urls-in-the-proxy-server) by using [streamlined URLs](https://learn.microsoft.com/en-us/defender-endpoint/configure-device-connectivity#option-1-configure-connectivity-using-the-simplified-domain).
2. On the **Sensor management** tab of the **On-premises** page in the Microsoft Defender portal, select **Download onboarding package**.
3. In the **Download onboarding package** pane, expand **Windows Server 2019 or later**, enter a **Package name**, and select **Generate package**.

   [![Screenshot of the Download onboarding package pane with package name and Generate package options for Windows Server 2019 or later.](https://learn.microsoft.com/en-us/defender-for-identity/deploy/media/activate-sensor/sensor-deployment-package-options.png)](https://learn.microsoft.com/en-us/defender-for-identity/deploy/media/activate-sensor/sensor-deployment-package-options.png#lightbox)
4. When the package is ready, download it and copy the access key.

   Important

   The access key is used only during sensor installation. Regenerating the key invalidates the existing key, and installations that use the previous key fail.
5. Copy the downloaded package to the domain controller.
6. Extract the package, making sure the `resources` subfolder is preserved.
7. Open PowerShell as an administrator, change to the extracted folder, and run the onboarding script:

   ```powershell
   Set-Location .\DfiOnboarding
   .\DefenderForIdentityV3StandaloneOnboardingScript.cmd
   ```

8. When prompted, enter the access key from the Microsoft Defender portal. The input is masked.

## Confirm sensor activation

To confirm that the v3.x sensor is working:

1. On the **Sensor management** tab of the **On-premises** page in the Microsoft Defender portal, check that the activated server is listed.

Note

The first Defender for Identity sensor v3.x activation in your environment might take up to an hour to show as **Running** on the **Sensor management** tab. Subsequent activations appear within five minutes. Activation doesn't require a restart.

## What if I want to add Defender for Endpoint later?

If you onboarded a domain controller with Defender for Identity only and now want to add Defender for Endpoint, follow these steps:

1. [Offboard the domain controller and remove the sensor](https://learn.microsoft.com/en-us/defender-for-identity/uninstall-sensor#offboard-a-domain-controller-that-isnt-onboarded-to-defender-for-endpoint-preview).
2. [Onboard the domain controller to Defender for Endpoint](https://learn.microsoft.com/en-us/defender-endpoint/onboard-server).
3. After the domain controller appears on the **Sensor management** tab, [activate the Defender for Identity sensor v3.x](#activate-the-defender-for-identity-sensor).

## Next step

- [Manage and update Microsoft Defender for Identity sensors](https://learn.microsoft.com/en-us/defender-for-identity/sensor-settings)
