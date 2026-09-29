<!-- Source: https://learn.microsoft.com/en-us/defender-endpoint/analyzer-report -->
<!-- Sitemap-Last-Modified: 2026-01-15 -->

# Understand the client analyzer HTML report

The client analyzer produces a report in HTML format. Learn how to review the report to identify potential sensor issues so that you can troubleshoot them.

Use the following example to understand the report.

## Example output

In this example, the [Defender for Endpoint Client Analyzer](https://learn.microsoft.com/en-us/defender-endpoint/overview-client-analyzer) produced information about a device that was onboarded to an expired Org ID and failed to reach a required Defender for Endpoint URL:

[![The MDE Client Analyzer Results page](https://learn.microsoft.com/en-us/defender-endpoint/media/147cbcf0f7b6f0ff65d200bf3e4674cb.png)](https://learn.microsoft.com/en-us/defender-endpoint/media/147cbcf0f7b6f0ff65d200bf3e4674cb.png#lightbox)

- On top, the script version and script runtime are listed for reference
- The **Device Information** section provides basic OS and device identifiers to uniquely identify the device on which the analyzer has run.
- The **Endpoint Security Details** provides general information about Microsoft Defender for Endpoint-related processes including Microsoft Defender Antivirus and the sensor process. If important processes aren't online as expected, the color changes to red.

  [![The Check Results Summary page](https://learn.microsoft.com/en-us/defender-endpoint/media/85f56004dc6bd1679c3d2c063e36cb80.png)](https://learn.microsoft.com/en-us/defender-endpoint/media/85f56004dc6bd1679c3d2c063e36cb80.png#lightbox)
- On **Check Results Summary**, you'll have an aggregated count for error, warning, or informational events detected by the analyzer.
- On **Detailed Results**, you'll see a list \(sorted by severity\) with the results and the guidance based on the observations made by the analyzer.

## Open a support ticket to Microsoft and include the Analyzer results

To include analyzer result files [when opening a support ticket](https://learn.microsoft.com/en-us/defender-endpoint/contact-support#open-a-service-request), make sure you use the **Attachments** section and include the `MDEClientAnalyzerResult.zip` file:

[![An attachment prompt](https://learn.microsoft.com/en-us/defender-endpoint/media/508c189656c3deb3b239daf811e33741.png)](https://learn.microsoft.com/en-us/defender-endpoint/media/508c189656c3deb3b239daf811e33741.png#lightbox)

Note

If the file size is larger than 25 MB, the support engineer assigned to your case will provide a dedicated secure workspace to upload large files for analysis.

## See also

- [Troubleshoot sensor health using Microsoft Defender for Endpoint Client Analyzer](https://learn.microsoft.com/en-us/defender-endpoint/overview-client-analyzer)
