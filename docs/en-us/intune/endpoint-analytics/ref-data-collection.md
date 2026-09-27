<!-- Source: https://learn.microsoft.com/en-us/intune/endpoint-analytics/ref-data-collection -->
<!-- Sitemap-Last-Modified: 2026-04-09 -->

# Endpoint analytics data collection

This article explains the data flow, data collection, and how to stop gathering data for endpoint analytics. For more information about data handling policies, see Intune's [Data storage and processing](https://learn.microsoft.com/en-us/intune/privacy/data-handling/data-storage-processing) and the [Microsoft Trust Center](https://www.microsoft.com/trust-center/privacy/data-location).

## Data flow

Endpoint analytics is available in all Intune locations in global Azure. Endpoint analytics respects the storage location elections made by the administrator for customer data. The following illustration shows how required functional data flows from individual devices through our data services, transient storage, and to your tenant.

[![User experience data flow diagram.](https://learn.microsoft.com/en-us/intune/endpoint-analytics/media/ref-data-collection/dataflow.png)](https://learn.microsoft.com/en-us/intune/endpoint-analytics/media/ref-data-collection/dataflow.png#lightbox)

1. An administrator [starts gathering data](https://learn.microsoft.com/en-us/intune/endpoint-analytics/configure).

   - For Intune-managed devices, this step configures the **Intune data collection** policy. By default, this policy is assigned to **All Devices**. You can [change the assignment](https://learn.microsoft.com/en-us/intune/endpoint-analytics/configure#change-the-assignment-of-the-intune-data-collection-policy) at any time to a subset of devices or no devices at all.
   - For Configuration Manager-managed devices, enable [endpoint analytics data collection and enroll devices](https://learn.microsoft.com/en-us/intune/endpoint-analytics/configure?pivots=cm).

2. Devices send required functional data.

   - For Intune and co-managed devices with the assigned policy, devices send required functional data in near real-time directly to the Microsoft Endpoint Management Service in the Microsoft public cloud where is processed every 24 hours. For more information, see [Network and connectivity requirements](https://learn.microsoft.com/en-us/intune/endpoint-analytics/#prerequisites).
   - For Configuration Manager-managed devices, data flows to the Microsoft Endpoint Management Service through the ConfigMgr [tenant attach](https://learn.microsoft.com/en-us/intune/configmgr/tenant-attach/device-sync-actions) connector. Devices don't need direct access to the Microsoft public cloud, but the ConfigMgr connector is cloud attached and requires connection to an Intune tenant. Devices send data to the Configuration Manager Server role every 24 hours, and the connector sends data to the Gateway Service every hour. For more information, see [Tenant attach data collection](https://learn.microsoft.com/en-us/intune/configmgr/tenant-attach/data-collection)

3. The Microsoft Endpoint Management service processes data for each device and publishes the results for both individual devices and organizational aggregates in the Intune admin center using [MS Graph APIs](https://learn.microsoft.com/en-us/graph/api/resources/intune-device-mgt-conceptual?view=graph-rest-beta&preserve-view=true). The maximum latency end to end is 96 hours.

Note

When you first setup endpoint analytics, the reports in endpoint analytics portal might not show complete data right away. The data required to compute the startup score for a device is generated during boot time. Depending on power settings and user behavior, it might take weeks after a device has been enrolled to show the startup score on the Intune admin center.

## Data collection

Endpoint analytics data collection falls into the [optional](https://learn.microsoft.com/en-us/intune/privacy/data-handling/data-collection#optional-data) category. This section includes some examples of the optional data collected for devices enrolled in endpoint analytics:

- Diagnostic, performance, and usage data tied to a user and/or device

  - `logOnId`
  - `bootId`: The system boot ID
  - `coreBootTimeInMilliseconds`: Time for core boot
  - `totalBootTimeInMilliseconds`: Total boot time
  - `updateTimeInMilliseconds`: Time for OS updates to complete
  - `gpLogonDurationInMilliseconds`: Time for Group policies to process
  - `desktopShownDurationInMilliseconds`: Time for desktop \(explorer.exe\) to be loaded
  - `desktopUsableDurationInMilliseconds`: Time for desktop \(explorer.exe\) to be usable
  - `topProcesses`: List of processes loaded during boot with name, with cpu usage stats and app details \(Name, publisher, version\). For example *{"ProcessName":"svchost","CpuUsage":43,"ProcessFullPath":"C:\\\\Windows\\\\System32\\\\svchost.exe","ProductName":"Microsoft® Windows® Operating System","Publisher":"Microsoft Corporation","ProductVersion":"10.0.18362.1"}*

- Device data not tied to a device or user \(if this data is tied to a device or user, Intune treats it as identified data\)

  - `ID`: Unique device ID used by Windows Update
  - `localId`: A locally defined unique ID for the device. This ID isn't the human-readable device name. Most likely equal to the value stored at HKLM\\Software\\Microsoft\\SQMClient\\MachineId.
  - `aaddeviceid`: Microsoft Entra device ID
  - `orgId`: Unique GUID representing the Microsoft 365 Tenant

- Application inventory, like

  - `name`: Windows
  - `ver`: The version of the current OS.

Important

Our data handling policies are described in [Privacy and personal data in Intune](https://learn.microsoft.com/en-us/intune/privacy/). We only use your customer data to provide you the services you signed up for. As described during the onboarding process, we anonymize and aggregate the scores from all enrolled organizations to keep the **All organizations \(median\)** baseline up-to-date.

## Stop gathering data

- If you're enrolling Intune managed devices only, unselect the **Endpoint analytics** scope from the [Intune data collection policy](https://learn.microsoft.com/en-us/intune/endpoint-analytics/configure#change-the-assignment-of-the-intune-data-collection-policy). Optionally, [revoke consent](https://learn.microsoft.com/en-us/intune/endpoint-analytics/configure#consent-to-share-data) to share anonymized and aggregate metrics for seeing updated endpoint analytics scores and insights.
- If you're enrolling devices that are managed by Configuration Manager, you need to do the following steps to disable data upload in Configuration Manager:

  1. In the Configuration Manager console, go to **Administration** > **Cloud Services** > **Co-management**.
  2. Select **CoMgmtSettingsProd** then select **Properties**.
  3. On the **Configure upload** tab, uncheck the option to **Enable Endpoint analytics for devices uploaded to Microsoft Endpoint Manager**.
  4. Optionally, [revoke consent](https://learn.microsoft.com/en-us/intune/endpoint-analytics/configure#consent-to-share-data) to share anonymized and aggregate metrics for seeing updated endpoint analytics scores and insights.

- Disable endpoint analytics data collection in Configuration Manager \(optional\):

  1. In the Configuration Manager console, go to **Administration** > **Client Settings** > **Default Client Settings**.
  2. Right-click and select **Properties** then select the **Computer Agent** settings.
  3. Set **Enable Endpoint analytics data collection** to **No**.


  Important


  If you have an existing custom client agent setting that's been deployed to your devices, you'll need to update the **Enable Endpoint analytics data collection** option in that custom setting then redeploy it to your machines for it to take effect.

## Resources

For more information about related privacy aspects, see the following articles:

- [Microsoft Privacy Statement](https://go.microsoft.com/fwlink/?LinkId=521839)
- [Windows 10 and privacy compliance](https://learn.microsoft.com/en-us/windows/privacy/windows-10-and-privacy-compliance)
- [Licensing terms and documentation](https://www.microsoft.com/licensing/terms)
- [Security and privacy at Microsoft Azure data centers](https://azure.microsoft.com/global-infrastructure/)
- [Confidence in the trusted cloud](https://azure.microsoft.com/overview/trusted-cloud/)
- [Trust Center](https://www.microsoft.com/trustcenter)
- [Intune Data storage and processing](https://learn.microsoft.com/en-us/intune/privacy/data-handling/data-storage-processing)
