<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/test-base/view-application-liability-results?view=o365-worldwide -->
<!-- Sitemap-Last-Modified: 2024-03-06 -->

# Viewing Application Reliability Results

Important

**Test Base for Microsoft 365 will transition to end-of-life \(EOL\) on May 31, 2024.** We're committed to working closely with each customer to provide support and guidance to make the transition as smooth as possible. If you have any questions, concerns, or need assistance, [submit a support request](https://aka.ms/TestBaseSupport).

You can determine application reliability by reviewing the data in the tables on the **Reliability** tab. For example, by reviewing data from this tab on how your application processes performed, you can determine if such processes are crashing or hanging at an unacceptable rate. This is possible because the **Reliability** tab exposes statistics for all the underlying running processes, which is inclusive of specific application reliability performance data. The dashboard also organizes the details of these processes that ran on the test machine into **Crash** signal and **Unresponding** signal categories for better assessment of results.

To display the **Reliability** tab, perform the steps of the procedure that follows:

1. Click **Security update results** under **Insights**.
2. Select the values associated with your package in the following drop-downs: **Package name, Package version, Operating system, Release**, and **Release build version**, as shown in the figure that follows.

   The drop-downs are populated with data followed by Test results for the **Functional** and **Out of box** tests.

   [![Screenshot shows Security update results.](https://learn.microsoft.com/en-us/microsoft-365/test-base/media/applicationreliability01.png?view=o365-worldwide)](https://learn.microsoft.com/en-us/microsoft-365/test-base/media/applicationreliability01.png?view=o365-worldwide#lightbox)

**Figure 2. Populating security update results**

1. Click **See details** in the **Reliability** row to display the **Reliability** data, providing that the status is **Completed**, as shown in the figure that follows.

   [![Screenshot shows Reliability data.](https://learn.microsoft.com/en-us/microsoft-365/test-base/media/applicationreliability02.png?view=o365-worldwide)](https://learn.microsoft.com/en-us/microsoft-365/test-base/media/applicationreliability02.png?view=o365-worldwide#lightbox)

**Figure 3. Reliability tab**

From the **Reliability** tab you can also sort the **Crash** and **Unresponding** data to ensure quick visibility into prominent information of interest. For example, you could sort processes by the highest failure rate, by the number of crashes, or by the number of times a process became unresponsive.

**For more information** about how relevant processes are identified, see [Determining Relevant Process for Regression Detection](https://learn.microsoft.com/en-us/microsoft-365/test-base/determine-relevant-processes-regression-detection?view=o365-worldwide).
