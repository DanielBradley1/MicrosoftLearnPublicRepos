<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/test-base/learn-cpu-regression-analysis?view=o365-worldwide -->
<!-- Sitemap-Last-Modified: 2024-03-06 -->

# Understanding CPU Regression Analysis

Important

**Test Base for Microsoft 365 will transition to end-of-life \(EOL\) on May 31, 2024.** We're committed to working closely with each customer to provide support and guidance to make the transition as smooth as possible. If you have any questions, concerns, or need assistance, [submit a support request](https://aka.ms/TestBaseSupport).

After uploading your application's binaries along with associated test scripts, the Test Base service will then run the test scripts, and automatically perform CPU and Memory regression analysis. The service will then check if the CPU utilization for the application on the pre-release version of the update for the target OS is in line with the CPU utilization for the released version of the OS.

CPU utilization is not likely to be a direct comparative match by operating system, given there can be differences for processes that are running on two different operating system versions. However, in these cases, the **Test Base** service analysis should be able to demonstrate whether CPU utilization for your application is impacted by an upcoming operating system update and specifically which processes have regressed from previous test runs.

In the figure that follows, there are two OS release versions against which CPU utilizations are compared for the same application. The list of processes should expose any significant regressions. The graphs show CPU % utilization over time along with the average % utilization per operating system version release.

Note

Memory or CPU utilization might also improve as a result of an operating system update, rather than simply deteriorate.

[![Screenshot shows C P U Regression.](https://learn.microsoft.com/en-us/microsoft-365/test-base/media/understandingcpuregressionanalysis01.png?view=o365-worldwide)](https://learn.microsoft.com/en-us/microsoft-365/test-base/media/understandingcpuregressionanalysis01.png?view=o365-worldwide#lightbox)

**Figure 5. CPU utilization data graph**
