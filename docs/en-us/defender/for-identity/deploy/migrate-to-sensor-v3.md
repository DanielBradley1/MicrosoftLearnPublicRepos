<!-- Source: https://learn.microsoft.com/en-us/defender-for-identity/deploy/migrate-to-sensor-v3 -->
<!-- Sitemap-Last-Modified: 2026-09-14 -->

# Migrate from Defender for Identity sensor v2 to sensor v3.x

You can migrate your Defender for Identity sensors from v2.x to v3.x directly from the Microsoft Defender portal. The migration automatically completes the switchover and maintains your server configurations and security monitoring, with no downtime or data duplication.

Before migrating, review the [prerequisites](#prerequisites) and [sensor version limitations](https://learn.microsoft.com/en-us/defender-for-identity/deploy/deploy-sensor-v3#sensor-version-limitations), including that v3.x doesn't support VPN integration or syslog notifications.

## Prerequisites

Note

Migration requires Defender for Endpoint and is currently supported only for domain controllers, including domain controllers that also run AD FS, AD CS, or Microsoft Entra Connect.

To migrate, each server must meet the following requirements:

- Domain controller, including a domain controller that also runs AD FS, AD CS, or Microsoft Entra Connect
- Defender for Identity sensor v2.x \(version 2.254.19112.470 or later\)
- Windows Server 2019 or later
- Microsoft Defender for Endpoint deployed, with the July 2026 or later Windows Server cumulative update installed.

For the full list of v3.x requirements, see [Defender for Identity sensor v3.x prerequisites](https://learn.microsoft.com/en-us/defender-for-identity/deploy/deploy-sensor-v3).

## Start the migration

Servers that meet all prerequisites appear as **Ready for migration** on the **Sensors** page.

1. In the [Microsoft Defender portal](https://security.microsoft.com), go to **Settings** > **Identities** > **On-premises** > **Sensors**.
2. Select one or more servers marked as **Ready for migration** and select **Migrate**.
3. In the confirmation prompt, review the details and confirm to start the migration.

Note

The migration typically takes up to 20 minutes. During this time, the v2.x sensor continues to run until the v3.x sensor is ready, so your server stays protected without interruption.

### Understand migration states

The **Migration state** column on the **Sensors** page shows the current status of each server:

| State | Description |
| --- | --- |
| **Ready for migration** | The server meets all prerequisites and can be migrated. Select the server and choose **Migrate** to begin. |
| **Not ready for migration** | The server doesn't meet one or more prerequisites. |
| **Migrating** | The migration is in progress. The v2.x sensor continues running while the v3.x sensor is being activated. |
| **Migration failed** | The migration encountered an error. |
| **Up to date** | The server is running sensor v3.x. |

## Configure the v3.x sensor

For optimal protection and monitoring, complete the configuration steps described in [Defender for Identity sensor v3.x prerequisites](https://learn.microsoft.com/en-us/defender-for-identity/deploy/deploy-sensor-v3), including:

- [Configure automatic Windows event auditing](https://learn.microsoft.com/en-us/defender-for-identity/deploy/deploy-sensor-v3#configure-windows-event-auditing). Existing auditing configurations from the v2.x sensor are preserved and converted for v3.x, but we recommend [enabling automatic Windows event auditing](https://learn.microsoft.com/en-us/defender-for-identity/deploy/configure-windows-event-collection#configure-defender-for-identity-to-collect-windows-events-automatically) for optimal configuration validation.
- [Switch action accounts from gMSA to local system](https://learn.microsoft.com/en-us/defender-for-identity/deploy/deploy-sensor-v3#service-account-requirements). The v3.x sensor uses the local system identity for response actions. If you had a gMSA configured for [action accounts](https://learn.microsoft.com/en-us/defender-for-identity/deploy/manage-action-accounts), select **Automatically use the sensor's local system account** in the Microsoft Defender portal. If gMSA remains enabled for action accounts, response actions \(including attack disruption\) won't work.
- [Understand DSA and gMSA health alerts in environments with both v2 and v3 sensors](https://learn.microsoft.com/en-us/defender-for-identity/deploy/deploy-sensor-v3#dsa-and-gmsa-health-alerts-in-environments-with-both-v2-and-v3-sensors). If your workspace still has a Directory Service Account \(DSA\) or group Managed Service Account \(gMSA\) configured for v2 sensors, DSA and gMSA credentials continue to be validated on all sensors, including v3 sensors. This is by design. V3 sensors ignore the DSA and gMSA for auditing and response actions, but credential validation occurs at the workspace level. To stop receiving the **Directory services user credentials are incorrect** health alert, remove the DSA or gMSA after all sensors are migrated to v3.
- [Configure RPC auditing](https://learn.microsoft.com/en-us/defender-for-identity/deploy/deploy-sensor-v3#configure-rpc-auditing). Starting with sensor version 3.0.8 \(July 2026 release\), RPC auditing is enabled automatically when you upgrade the sensor, so no manual configuration is required.

Important

The v3.x sensor updates through Windows Update as part of the server's operating system update process. The per-sensor **Delayed update** option available for v2.x sensors doesn't apply to v3.x. For more information, see [Manage and update sensors](https://learn.microsoft.com/en-us/defender-for-identity/sensor-settings#update-sensors).

## Troubleshoot "Not ready for migration" status

When a server is marked **Not ready for migration**, hover over the status on the **Sensors** page to see a tooltip that lists the reasons the server doesn't meet the migration prerequisites.

The following table lists each reason that can appear in the tooltip, how to verify it, and how to resolve it:

| Reason shown in the tooltip | How to verify | Resolution |
| --- | --- | --- |
| Device isn't properly onboarded to Microsoft Defender for Endpoint. | Run the Microsoft Defender for Endpoint Client Analyzer and check `RegOnboardingInfoPolicy.Json` in the results ZIP. The connectivity log shows *"OnboardingInfo could not be found in the registry"* if the onboarding info is missing. | Re-onboard the server to Microsoft Defender for Endpoint. |
| Operating system version isn't supported. Requires Windows Server 2019 or later. | Run `winver` to confirm the operating system version and build number. | Upgrade the operating system to Windows Server 2019 or later and install the July 2026 or later cumulative update. |
| Microsoft Defender for Endpoint sensor version is outdated or unsupported. | In the Client Analyzer report, check the **Sense version** field. | Update the Microsoft Defender for Endpoint sensor to the latest version. |
| Microsoft Defender for Endpoint \(Sense\) service isn't running. | In the Client Analyzer report, confirm the **Sense service Status** is **Running**. | Start the Sense service and verify Microsoft Defender for Endpoint onboarding is complete. |
| Migration is currently supported only for domain controllers. | Confirm the server is a domain controller. | In-place migration is available only for domain controllers. |
| Microsoft Defender for Endpoint device ID is missing or not registered. | In the Client Analyzer report, confirm the **Device ID** field contains a valid GUID. | Verify Microsoft Defender for Endpoint onboarding completed successfully, and re-onboard the server if the device ID is empty. |
| Sensor v2.x status is unreachable or disconnected. | On the **Sensors** page, check the sensor's status. | Verify network connectivity between the server and the Defender for Identity service, and confirm the sensor v2.x is running. |
| Sensor v2.x service status is not running. | On the **Sensors** page, confirm the **Service status** column shows **Running**, or run `sc query AATPSensorUpdater` to confirm the service state. | Start the `AATPSensorUpdater` service. If the service fails to start, reinstall the sensor v2.x. |

## Troubleshoot migration failures

If a server shows a **Migration failed** status, run the [Microsoft Defender for Endpoint Client Analyzer](https://learn.microsoft.com/en-us/defender-endpoint/overview-client-analyzer) on the server to validate that the Defender for Endpoint sensor is running, healthy, and sending events. If the Client Analyzer results show the sensor is healthy, raise a support case for further assistance.

## Clean up the v2.x sensor

The migration disables the v2.x sensor service, but the v2.x sensor software remains installed on the server. Complete the following cleanup steps to fully clean your server from the v2.x sensor files:

- **Uninstall the v2.x sensor**: Remove the v2.x sensor software from the server. This step might require a server restart. For instructions, see [Delete and uninstall a sensor v2.x from a domain controller](https://learn.microsoft.com/en-us/defender-for-identity/uninstall-sensor#delete-and-uninstall-a-sensor-v2x-from-a-domain-controller).
- **Remove Npcap**: Npcap was used by the v2.x sensor but isn't required by the v3.x sensor. If Npcap isn't used by other applications on the server, remove it. Leaving Npcap installed doesn't affect the v3.x sensor.

## Related content

- [Defender for Identity sensor v3.x prerequisites](https://learn.microsoft.com/en-us/defender-for-identity/deploy/deploy-sensor-v3)
- [Activate the Defender for Identity sensor v3.x](https://learn.microsoft.com/en-us/defender-for-identity/deploy/activate-sensor)
- [Manage and update sensors](https://learn.microsoft.com/en-us/defender-for-identity/sensor-settings)
- [Remove the Microsoft Defender for Identity sensor](https://learn.microsoft.com/en-us/defender-for-identity/uninstall-sensor)
- [Microsoft Defender for Endpoint Client Analyzer](https://learn.microsoft.com/en-us/defender-endpoint/overview-client-analyzer)
