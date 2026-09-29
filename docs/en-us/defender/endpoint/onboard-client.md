<!-- Source: https://learn.microsoft.com/en-us/defender-endpoint/onboard-client -->
<!-- Sitemap-Last-Modified: 2026-04-13 -->

# Onboard Windows client devices to Microsoft Defender for Endpoint

## Overview of onboarding client devices

Note

The Defender deployment tool can be used to deploy Defender endpoint security on Windows and Linux devices. The tool is a lightweight, self-updating application that streamlines the deployment process. For more information, see [Deploy Microsoft Defender endpoint security to Windows devices using the Defender deployment tool](https://learn.microsoft.com/en-us/defender-endpoint/defender-deployment-tool-windows) and [Deploy Microsoft Defender endpoint security to Linux devices using the Defender deployment tool \(preview\)](https://learn.microsoft.com/en-us/defender-endpoint/linux-install-with-defender-deployment-tool).

To onboard Windows client devices, follow this general process:

1. Make sure to review the [Minimum requirements for Defender for Endpoint](https://learn.microsoft.com/en-us/defender-endpoint/minimum-requirements).
2. In the [Microsoft Defender portal](https://security.microsoft.com), go to **System** > **Settings** > **Endpoints**, and then, under **Device management**, select **Onboarding**.

   [![Screenshot showing device onboarding in the Microsoft Defender portal for Defender for Endpoint.](https://learn.microsoft.com/en-us/defender-endpoint/media/mde-device-onboarding-ui.png)](https://learn.microsoft.com/en-us/defender-endpoint/media/mde-device-onboarding-ui.png#lightbox)
3. Under **Select operating system to start onboarding process**, select the operating system for the device.
4. Under **Connectivity type**, select either **Streamlined** or **Standard**. \(See [prerequisites for streamlined connectivity](https://learn.microsoft.com/en-us/defender-endpoint/configure-device-connectivity#prerequisites).\)
5. Under **Deployment method**, select an option. Then download the onboarding package \(and installation package, if there's one available\). Follow the instructions to onboard your devices. The following table lists available deployment methods:
   | Operating system | Deployment method |
   | --- | --- |
   | Windows 11  <br>Windows 10  <br>Windows 365 | [Local script \(up to 10 devices\)](https://learn.microsoft.com/en-us/defender-endpoint/configure-endpoints-script)  <br>[Microsoft Intune / Mobile Device Management](https://learn.microsoft.com/en-us/defender-endpoint/configure-endpoints-mdm)  <br>[Microsoft Configuration Manager](https://learn.microsoft.com/en-us/defender-endpoint/configure-endpoints-sccm)  <br>[Group Policy](https://learn.microsoft.com/en-us/defender-endpoint/configure-endpoints-gp)  <br>[VDI scripts](https://learn.microsoft.com/en-us/defender-endpoint/configure-endpoints-vdi) |
   | Windows 8.1 Enterprise or Pro  <br>Windows 7 SP1 Enterprise or Pro | [Microsoft Monitoring Agent](https://learn.microsoft.com/en-us/defender-endpoint/update-agent-mma-windows) |

Warning

Repackaging the Defender for Endpoint installation package is not a supported scenario. Doing so can negatively impact the integrity of the product and lead to adverse results, including but not limited to triggering tampering alerts and updates failing to apply.

## See also

- [Microsoft Defender for Endpoint - Mobile Threat Defense](https://learn.microsoft.com/en-us/defender-endpoint/mtd) \(for iOS and Android devices\)
- [Onboard servers to Microsoft Defender for Endpoint](https://learn.microsoft.com/en-us/defender-endpoint/onboard-server)
