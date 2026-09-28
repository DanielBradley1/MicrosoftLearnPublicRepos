<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/test-base/download-analyze-test-result-files?view=o365-worldwide -->
<!-- Sitemap-Last-Modified: 2024-03-06 -->

# Downloading and Analyzing Test Result Files

Important

**Test Base for Microsoft 365 will transition to end-of-life \(EOL\) on May 31, 2024.** We're committed to working closely with each customer to provide support and guidance to make the transition as smooth as possible. If you have any questions, concerns, or need assistance, [submit a support request](https://aka.ms/TestBaseSupport).

**Test Base for Microsoft 365** generates downloadable event trace log \(ETL\) files that collect low-level data based on application testing. These trace files contain event data that is captured during test execution, from which memory utilization, CPU utilization, and other performance data is derived.

Additional relevant test execution results data that you can analyze is described in the table that follows. The data folders listed in the table below exist within the a **logs.zip** folder that is accessible from the **Log files: Download** link in the Test Base results for an application that completed testing against a specified operating system version.

## Table 1. Data Sources for Performance and Results Analysis

| Data Folder | Performance or Results Data Source | FileType | Description |
| --- | --- | --- | --- |
| package | Application installation results \(.log\) | .log | See app installation and script logs. |
| performance | Performance counters \(.csv\) | .csv | Review Perf counter data. |
| results | Exit codes \(.csv\) | .csv | See application exit codes. |
| scripts | Script log files \(.log\) | .log | Analyze script stderr and stdout logs. |
| systemInfo | System information \(.json\) | .json | Review system information data. |
| trace | % Memory utilization by process | .csv | Evaluate utilization results data. |
| trace | % CPU utilization by process | .csv | Evaluate utilization results data. |
| trace | WPA Trace | .etl | Performance trace to be analyzed in WPA. |
| winEvt | Event Viewer \(.evtx\) | .evtx | Examine application event logs. |

If you choose not to download the log files because you would rather analyze data in the **Test Base** web view, you have the option to observe certain data from the **Script execution** tab. To do so, click the linked name of an individual script and view the **Log Output** directly in the portal, as shown in the right-hand sector of the figure that follows.

[![Screenshot shows Scripts Execution Results.](https://learn.microsoft.com/en-us/microsoft-365/test-base/media/downloadingandanalyzingtestresultfiles01.png?view=o365-worldwide)](https://learn.microsoft.com/en-us/microsoft-365/test-base/media/downloadingandanalyzingtestresultfiles01.png?view=o365-worldwide#lightbox)

**Figure 6. Viewing log output in the Script Execution tab**
