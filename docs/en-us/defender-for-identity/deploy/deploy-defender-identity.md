<!-- Source: https://learn.microsoft.com/en-us/defender-for-identity/deploy/deploy-defender-identity -->
<!-- Sitemap-Last-Modified: 2026-09-10 -->

# Microsoft Defender for Identity deployment overview

Microsoft Defender for Identity sensors collect signals from your on-premises identity infrastructure. Defender for Identity uses these signals to detect threats such as privilege escalation and high-risk lateral movement. It also reports identity security issues, such as unconstrained Kerberos delegation, so your security team can correct them.

Install Defender for Identity sensors on all domain controllers, including read-only domain controllers \(RODCs\). Also install sensors on Active Directory Federation Services \(AD FS\), Active Directory Certificate Services \(AD CS\), and Microsoft Entra Connect servers that aren't domain controllers. Use the table in this article to select the sensor version.

## Select your deployment method

The sensor version you deploy depends on the server role and operating system. Use the following table to select the appropriate deployment for each server in your environment.

For eligible domain controllers running Windows Server 2019 or later, sensor v3.x supports onboarding with or without Microsoft Defender for Endpoint deployment. Other eligible identity-role servers require Defender for Endpoint onboarding.

![Diagram of sensor deployment: use sensor v3.x on supported servers running Windows Server 2019 or later, and v2.x on earlier versions.](https://learn.microsoft.com/en-us/defender-for-identity/deploy/media/deploy-defender-identity/sensor-deployment-decision.png)

| Server configuration | Server operating system | Recommended deployment | Onboarding options |
| --- | --- | --- | --- |
| Any supported server type | Windows Server 2019 or later with the July 2026 or later cumulative update | [Defender for Identity sensor v3.x](https://learn.microsoft.com/en-us/defender-for-identity/deploy/deploy-sensor-v3) | For servers onboarded to Defender for Endpoint, activate sensor v3.x directly. For domain controllers that aren't onboarded to Defender for Endpoint, use the sensor v3.x onboarding package. AD FS, AD CS, and Microsoft Entra Connect servers must be onboarded to Defender for Endpoint before activation. |
| Any supported server type | Windows Server 2016 or earlier | [Defender for Identity sensor v2.x](https://learn.microsoft.com/en-us/defender-for-identity/deploy/prerequisites-sensor-version-2) | [Install the sensor v2.x package](https://learn.microsoft.com/en-us/defender-for-identity/deploy/install-sensor). |

Defender for Identity supports sensor v3.x and sensor v2.x in the same workspace. For example, you might deploy sensor v3.x on servers running Windows Server 2019 or later and sensor v2.x on servers running Windows Server 2016 or earlier.

If your organization requires [VPN integration](https://learn.microsoft.com/en-us/defender-for-identity/vpn-integration) or [syslog notifications](https://learn.microsoft.com/en-us/defender-for-identity/notifications#configure-syslog-notifications), use the v2.x sensor on the applicable domain controllers. These features aren't supported by the v3.x sensor.

Important

If any of your sensors are v3.x, select **Automatically use the sensor's local system account** for all sensors. The v3.x sensors don't use gMSA accounts configured for v2.x sensors; they always use the local system account. For more information, see [Sensor v3.x service account requirements](https://learn.microsoft.com/en-us/defender-for-identity/deploy/deploy-sensor-v3#service-account-requirements).

Before you activate the Defender for Identity sensor v3.x, note that v3.x:

- Supports onboarding through Defender for Endpoint. Eligible domain controllers can instead use the sensor v3.x onboarding package.
- Doesn't support VPN integration.
- Doesn't support [syslog notifications](https://learn.microsoft.com/en-us/defender-for-identity/notifications#configure-syslog-notifications).
- Has limitations working with Azure ExpressRoute. For more information, see [Azure ExpressRoute for Microsoft 365](https://learn.microsoft.com/en-us/microsoft-365/enterprise/azure-expressroute).

## Review the Sensor management tab

The **Sensor management** tab displays deployed sensors and servers discovered in Device Inventory. Each server's onboarding status shows whether the server is eligible for sensor v3.x and what action to take.

### Review action cards

Action cards summarize servers and sensors that need attention. Select a card to open a pane with more information and available actions.

| Action card | What the pane presents | Available actions |
| --- | --- | --- |
| **Domain controllers ready for activation** | Eligible domain controllers that are onboarded to Microsoft Defender for Endpoint and ready for sensor v3.x activation. | To automatically activate eligible domain controllers, select **Enable automatic activation**. On the **Advanced features** page, turn on **Automatic sensor v3.x activation**. To review the servers instead, select **Show in table**. |
| **Domain controllers ready for manual onboarding** | Eligible domain controllers that aren't onboarded to Microsoft Defender for Endpoint or that run Windows Server 2016 or earlier. | Select **Download onboarding package** to choose the applicable manual sensor deployment package. |
| **Servers ready for migration** | Eligible servers that are ready to migrate from sensor v2.x to sensor v3.x. | Select **Show in table** to filter the server list to servers that are **Ready for migration**. Start migration by selecting servers in the filtered table. |
| **AD CS, AD FS, or Entra Connect servers ready for activation** | Eligible AD FS, AD CS, or Microsoft Entra Connect servers that are onboarded to Microsoft Defender for Endpoint and ready for sensor v3.x activation. | Select **Show in table** to review the servers. Select an eligible server, and then select **Activate**. |
| **AD CS, AD FS, or Entra Connect servers ready for manual onboarding** | Eligible AD FS, AD CS, or Microsoft Entra Connect servers that aren't onboarded to Microsoft Defender for Endpoint or that run Windows Server 2016 or earlier. | Select **Download onboarding package** to choose the applicable manual sensor deployment package. |
| **Sensors not healthy** | Sensors with open health issues that require attention. | Select **Show in table** to filter the sensor list to unhealthy sensors, or select **Go to health page** to review the health issues. |

The **Onboarding status** column uses the following values:

| Onboarding status | Next steps |
| --- | --- |
| Onboarded | The Defender for Identity sensor is deployed on the server. |
| Activate sensor | The server is ready for sensor v3.x activation. [Activate the v3.x sensor](https://learn.microsoft.com/en-us/defender-for-identity/deploy/activate-sensor#activate-the-defender-for-identity-sensor). |
| Manually onboard | The server requires manual sensor deployment. [Choose the appropriate deployment method](#select-your-deployment-method). |
| Upgrade to the latest Windows Update | The server doesn't meet the operating system requirements for sensor v3.x. Install the latest Windows updates before activation. |

Note

The table combines deployed sensors with servers discovered through Device Inventory. A server without a deployed sensor must be onboarded to Microsoft Defender for Endpoint to appear as a server row. Servers that aren't onboarded to Defender for Endpoint can appear in the manual onboarding action cards.

## Choose a deployment flow

Choose the sensor deployment flow that matches the server configuration:

- If the server is onboarded to Microsoft Defender for Endpoint, [activate sensor v3.x from the Sensor management tab](https://learn.microsoft.com/en-us/defender-for-identity/deploy/activate-sensor#activate-the-defender-for-identity-sensor).
- If an eligible domain controller isn't onboarded to Defender for Endpoint, [download and run the sensor v3.x onboarding package](https://learn.microsoft.com/en-us/defender-for-identity/deploy/activate-sensor#onboard-the-domain-controller-preview).
- If the server already runs sensor v2.x, [migrate the sensor to v3.x](https://learn.microsoft.com/en-us/defender-for-identity/deploy/migrate-to-sensor-v3).
- If the server supports sensor v2.x only, [install sensor v2.x](https://learn.microsoft.com/en-us/defender-for-identity/deploy/install-sensor).

## Deployment steps for sensor v3.x

Follow these steps to deploy sensor v3.x on eligible servers running Windows Server 2019 or later:

1. [Verify prerequisites](https://learn.microsoft.com/en-us/defender-for-identity/deploy/deploy-sensor-v3#before-you-activate).
2. [Activate the sensor](https://learn.microsoft.com/en-us/defender-for-identity/deploy/activate-sensor).
3. [Configure Windows event auditing](https://learn.microsoft.com/en-us/defender-for-identity/deploy/configure-windows-event-collection#configure-defender-for-identity-to-collect-windows-events-automatically).
4. [Configure RPC auditing](https://learn.microsoft.com/en-us/defender-for-identity/deploy/deploy-sensor-v3#configure-rpc-auditing).
5. [Validate deployment](https://learn.microsoft.com/en-us/defender-for-identity/deploy/test-sensor).

## Deployment steps for sensor v2.x

Follow these steps to deploy the sensor v2.x on supported servers running Windows Server 2016 or earlier:

1. [Verify prerequisites](https://learn.microsoft.com/en-us/defender-for-identity/deploy/prerequisites-sensor-version-2).
2. [Plan capacity](https://learn.microsoft.com/en-us/defender-for-identity/deploy/capacity-planning).
3. [Configure connectivity](https://learn.microsoft.com/en-us/defender-for-identity/deploy/configure-proxy).
4. [Install the sensor](https://learn.microsoft.com/en-us/defender-for-identity/deploy/install-sensor).
5. [Configure the sensor](https://learn.microsoft.com/en-us/defender-for-identity/deploy/configure-sensor-settings).
6. [Configure Windows event auditing](https://learn.microsoft.com/en-us/defender-for-identity/deploy/configure-windows-event-collection#configure-windows-event-collection-manually).
7. [Configure Directory Service accounts](https://learn.microsoft.com/en-us/defender-for-identity/deploy/directory-service-accounts).
8. [Configure for AD FS, AD CS, or Entra Connect \(if applicable\)](https://learn.microsoft.com/en-us/defender-for-identity/deploy/active-directory-federation-services).
9. [Validate deployment](https://learn.microsoft.com/en-us/defender-for-identity/deploy/test-sensor).

## Next steps

- [Prepare your environment for sensor v3](https://learn.microsoft.com/en-us/defender-for-identity/deploy/deploy-sensor-v3)
- [Prepare your environment for sensor v2](https://learn.microsoft.com/en-us/defender-for-identity/deploy/prerequisites-sensor-version-2)
