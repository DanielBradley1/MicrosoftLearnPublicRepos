<!-- Source: https://learn.microsoft.com/en-us/defender-for-identity/deploy/capacity-planning -->
<!-- Sitemap-Last-Modified: 2026-07-02 -->

# Plan capacity for Microsoft Defender for Identity deployment

Note

The capacity planning tool was designed for version 2.x of the sensor due to its resource-intensive network processes. Sensor v3.x does not require a sizing tool since it relies mainly on Windows events and event tracing, which significantly reduces resource requirements.

Use the Microsoft Defender for Identity sizing tool to determine whether your domain controller servers have enough resources for a Microsoft Defender for Identity sensor v2. Before you run the sizing tool, review the [Prerequisites](#prerequisites).

While domain controller performance may not be affected if the server doesn't have required resources, the Defender for Identity sensor may not operate as expected. For more information, see [Microsoft Defender for Identity prerequisites](https://learn.microsoft.com/en-us/defender-for-identity/deploy/prerequisites-sensor-version-2).

The sizing tool measures the capacity needed for domain controllers only. There is no need to run it against servers that are only AD FS, AD CS, or Entra Connect \(unless those servers also function as a domain controller\), as the performance impact on these servers is extremely minimal to not existent.

Tip

By default, Defender for Identity supports up to 1000 sensors. To install more sensors, contact Defender for Identity support.

## Prerequisites

Before you run the sizing tool, complete the following prerequisites:

- Download the [Defender for Identity sizing tool](https://aka.ms/mdi/sizingtool).
- Review the [Defender for Identity prerequisites](https://learn.microsoft.com/en-us/defender-for-identity/deploy/prerequisites-sensor-version-2). The Microsoft Defender for Identity Sizing Tool currently only applies to the sensor version 2.x.

To ensure accurate results, only run the sizing tool *before* you've installed any Defender for Identity sensors in your environment.

## Use the sizing tool

Use the following steps to run the sizing tool and review the results:

1. Run the Defender for Identity sizing tool, **TriSizingTool.exe**, from the zip file you downloaded.
2. When the tool finishes running, open the Excel file results.
3. In the Excel file, locate and select the **Azure ATP Summary** sheet, and then check the **Sensor Supported** column for results that indicate whether your server is supported.

   For example:

   [![Screenshot of a sample capacity planning tool.](https://learn.microsoft.com/en-us/defender-for-identity/media/capacity-tool.png)](https://learn.microsoft.com/en-us/defender-for-identity/media/capacity-tool.png#lightbox)

   Note

   The other sheet in the file is used for [Advanced Threat Analytics \(ATA\)](https://learn.microsoft.com/en-us/advanced-threat-analytics/what-is-ata) planning and isn't needed for Defender for Identity.

The sizing tool determines whether your server is supported based on the **Busy Packets/Second** value, which is calculated based on the 15 busiest minutes over a 24 hour period.

Common results include:

| Result | Description |
| --- | --- |
| **Yes** | The sensor is supported on your server. |
| **Yes, but additional resources required** | The sensor is supported on your server as long you add any specified missing resources. |
| **Maybe** | The current **Busy Packets/sec** value may be significantly higher at that point than average. Check the timestamps to understand the processes running at that time, and whether you can limit the bandwidth for those processes under normal circumstances. |
| **Maybe, but additional resources required** | The sensor may be supported on your server as long you add any specified missing resources, or the **Busy packets/sec** may be above 60K. |
| **No** | The sensor isn't supported on your server.  <br>  <br>The current **Busy Packets/sec** value may be significantly higher at that point than average. Check the timestamps to understand the processes running at that time, and whether you can limit the bandwidth for those processes under normal circumstances. |
| **Missing OS Data** | There was an issue reading the operating system data. Make sure the connection to your server is able to query WMI remotely. |
| **Missing Traffic Data** | There was an issue reading the traffic data. Make sure the connection to your server is able to query performance counters remotely. |
| **Missing RAM data** | There was an issue reading the RAM data. Make sure the connection to your server is able to query WMI remotely. |
| **Missing core data** | There was an issue reading the core data. Make sure the connection to your server is able to query WMI remotely. |

For example, the following image shows a set of results where the **Maybe** indicates that the **Busy Packets/sec** value is significantly higher at that point than average. Note that the **Display DC Times as UTC/Local** is set to *Local DC Time*. This setting helps highlight the fact that the values were taken at around 3:30 AM.

[![Screenshot of a capacity tool results showing Maybe values.](https://learn.microsoft.com/en-us/defender-for-identity/media/capacity-tool-maybe.png)](https://learn.microsoft.com/en-us/defender-for-identity/media/capacity-tool-maybe.png#lightbox)

## Defender for Identity sensor estimated sizing

The following table shows the estimated CPU and RAM capacity needed for a Defender for Identity sensor, based on the typical amount of network traffic generated by a domain controller.

**This table is an estimate. The final amount that the sensor parses is dependent on the amount of traffic and the distribution of traffic.**

| Busy packets / second | CPU \(physical cores\) | RAM \(GB\) |
| --- | --- | --- |
| 0-1k | 0.25 | 2.50 |
| 1k-5k | 0.75 | 6.00 |
| 5k-10k | 1.00 | 6.50 |
| 10k-20k | 2.00 | 9.00 |
| 20k-50k | 3.50 | 9.50 |
| 50k-75k | 5.50 | 11.50 |
| 75k-100k | 7.50 | 13.50 |

In this table:

- CPU and RAM capacity refers to the **sensor's own consumption**, not the domain controller capacity.
- CPU capacity doesn't include hyper-threaded cores. We recommend that you don't work with hyper-threaded cores, which can result in health issues in the Defender for Identity sensor.

When determining sizing, keep in mind the total number of cores and total amount of memory that will be used by the sensor service.

## Manual sizing estimation for domain controllers

If you're unable to use the Defender for Identity sizing tool described in [Use the sizing tool](#use-the-sizing-tool), you can manually estimate whether your domain controller servers have enough resources for a Defender for Identity sensor instead.

Manually gather the packet/second counter information from all your domain controllers, over 24 hours with a low collection interval like 5 seconds. For each domain controller, calculate the daily average and the busiest period \(15 minutes\) average.

Various tools can help you discover the average packet/second counter for your domain controller. This procedure describes an example of how to use Performance Monitor to gather packet-per-second counter data for your domain controllers.

1. Open Performance Monitor and expand **Data Collector Sets**.
2. Right-click **User Defined** and select **New > Data Collector Set**.
3. Enter a meaningful name for the collector set and select **Create Manually \(Advanced\)**.
4. Under **What type of data do you want to include?**, select **Create data logs, and Performance counter**.
5. Expand **Network Adapter** and then select **Packets/sec** and the relevant workspace. If you're not sure which workspace to select, select **<All workspaces>**. Select **Add** > **OK** to complete the step.

   Alternately, if you're performing this step from the command line, run `ipconfig /all` to see the adapter name and configuration.
6. Change the **Sample interval** to **five seconds**, and define where you want the data to be saved.
7. Under **Create the data collector set**, select **Start this data collector set now** > **Finish**.

   You should now see the data collector set you created with a green triangle indicating that it's working.
8. After 24 hours, stop the data collector set. Right-click the data collector set and select **Stop**.
9. In File Explorer, browse to the folder where the **.blg** file was saved. Double-click it to open it in Performance Monitor.
10. Select the **Packets/sec** counter, and record the average and maximum values.

Note

By default, Defender for Identity supports up to 350 sensors. If you want to install more sensors, contact Defender for Identity support.

Important

If your domain controller runs low on available memory, a corresponding health issue will appear in the Defender for Identity portal to alert you of this condition. Learn more about [Defender for Identity health alerts](https://learn.microsoft.com/en-us/defender-for-identity/health-alerts).

## Next step

[Configure endpoint proxy and internet connectivity settings »](https://learn.microsoft.com/en-us/defender-for-identity/deploy/configure-proxy)
