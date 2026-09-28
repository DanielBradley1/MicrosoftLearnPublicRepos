<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/test-base/analyze-regression-causes?view=o365-worldwide -->
<!-- Sitemap-Last-Modified: 2024-03-06 -->

# Analyzing the Causes of Regressions

Important

**Test Base for Microsoft 365 will transition to end-of-life \(EOL\) on May 31, 2024.** We're committed to working closely with each customer to provide support and guidance to make the transition as smooth as possible. If you have any questions, concerns, or need assistance, [submit a support request](https://aka.ms/TestBaseSupport).

In order to understand the cause of a Memory or CPU utilization regression, you have various data sources and tools that you can utilize to assist you. As part of the Windows Assessment and Deployment Kit \(Windows ADK\), Windows Performance Recorder \(WPR\) is a performance recording tool based on Event Tracing for Windows \(ETW\). This tool assists you in gathering the right data from which you can gain an understanding of the cause\(s\) of a regression. It records system and application events in an .etl file, which you will thereafter use as input to the Windows Performance Analyzer \(WPA\). you can also use WPR and WPA together to investigate specific areas of performance and to gain an overall understanding of resource consumption.

Once a regression is detected, you can download the Windows Performance Analyzer toolkit and analyze reasons for Memory or CPU performance regressions, that is, after you provide the above mentioned .etl file as input to the WPA.

Note that these .etl files are available in the log files that are downloadable for test runs on the Test Base user portal. After completing a test run, you can download zip files for one or more test executions run by clicking the **Log files: Download** link for a set of test results. Once downloaded, you can unzip the logs for the test run/s, then locate the associated WPR-generated .etl file/s, each within a separate **\\trace** folder.

**To learn more** about Windows Performance Recorder, see the [Windows Performance Recorder](https://learn.microsoft.com/en-us/windows-hardware/test/wpt/windows-performance-recorder) documentation on [learn.Microsoft.com](https://learn.microsoft.com/en-us/).

**To learn more** about debugging Memory and CPU utilization regressions with Windows Performance Analyzer \(WPA\), see the [Windows Performance Analyzer](https://learn.microsoft.com/en-us/windows-hardware/test/wpt/windows-performance-analyzer) documentation on [learn.Microsoft.com](https://learn.microsoft.com/en-us/). It is an example of how to debug a type of regressions. More info on how to use WPA and our zip is not covered on this page.

**To learn more** about CPU regression analysis, see [Intelligent CPU regression analysis with Test Base for Microsoft 365](https://techcommunity.microsoft.com/t5/test-base-blog/intelligent-cpu-regression-analysis-with-test-base-for-microsoft/ba-p/2112977).

**To learn more** about Windows Event Tracing, see [ETW Framework Conceptual Tutorial](https://learn.microsoft.com/en-us/message-analyzer/etw-framework-conceptual-tutorial).
