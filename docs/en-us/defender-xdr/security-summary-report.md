<!-- Source: https://learn.microsoft.com/en-us/defender-xdr/security-summary-report -->
<!-- Sitemap-Last-Modified: 2026-08-11 -->

# Highlight security impact and achievements with the unified security summary

Security operations center \(SOC\) teams can easily showcase their security achievements and the impact of Microsoft Defender using the unified security summary. Having the summary readily available in the Microsoft Defender portal streamlines the process for SOC teams to generate security reports, saving time usually spent on collecting data from various sources and creating reports tailored to their audiences. SOC teams can readily communicate performance and achievements to their stakeholders with the unified security summary.

The unified security summary highlights the following information:

- **Posture**: Your organization’s posture includes data from [Microsoft Secure Score](https://learn.microsoft.com/en-us/defender-xdr/microsoft-secure-score), threat protection information related to ransomware and phishing prevention, [exposure score](https://learn.microsoft.com/en-us/defender-vulnerability-management/tvm-exposure-score) based on Microsoft Defender Vulnerability Management, and the number of onboarded devices to Microsoft Defender for Endpoint

  <span class="mx-imgBorder">
  <a href="https://learn.microsoft.com/en-us/defender-xdr/media/security-summary-report/summary-posture.png#lightbox" data-linktype="relative-path">
  <img src="https://learn.microsoft.com/en-us/defender-xdr/media/security-summary-report/summary-posture-small.png" alt="Screenshot of the Posture section in the security summary report" data-linktype="relative-path">
  </a>
  </span>

- **Detection**: This section contains the number of [incidents and alerts overview](https://learn.microsoft.com/en-us/defender-xdr/incidents-overview), including how many alerts were consolidated into incidents, the number of alerts grouped into incidents, and information on active detection rules and the corresponding response actions produced by those rules

  <span class="mx-imgBorder">
  <a href="https://learn.microsoft.com/en-us/defender-xdr/media/security-summary-report/summary-detection.png#lightbox" data-linktype="relative-path">
  <img src="https://learn.microsoft.com/en-us/defender-xdr/media/security-summary-report/summary-detection-small.png" alt="Screenshot of the Detection section in the security summary report" data-linktype="relative-path">
  </a>
  </span>

- **Protection**: Cards under this section include data from Microsoft’s automatic investigation and response features like the total number of [automatic attack disruptions](https://learn.microsoft.com/en-us/defender-xdr/automatic-attack-disruption), a list of the disruption incidents, the number of malicious activities blocked by Microsoft Defender Antivirus, and the number of malicious emails and URLs blocked

  <span class="mx-imgBorder">
  <a href="https://learn.microsoft.com/en-us/defender-xdr/media/security-summary-report/summary-protection.png#lightbox" data-linktype="relative-path">
  <img src="https://learn.microsoft.com/en-us/defender-xdr/media/security-summary-report/summary-protection-small.png" alt="Screenshot of the Protection section in the security summary report" data-linktype="relative-path">
  </a>
  </span>

- **Investigation and response**: This section contains the number of active and resolved alerts and incidents, top 10 critical incidents with each incident’s status and affected number of assets, the number of [automated investigation and response in Microsoft Defender](https://learn.microsoft.com/en-us/defender-xdr/m365d-autoir) actions taken on impacted assets, and the number of email messages where malicious files were automatically identified and extracted through [Microsoft Defender for Office 365 Zero-hour auto purge \(ZAP\)](https://learn.microsoft.com/en-us/defender-office-365/zero-hour-auto-purge)

  <span class="mx-imgBorder">
  <a href="https://learn.microsoft.com/en-us/defender-xdr/media/security-summary-report/summary-investigation.png#lightbox" data-linktype="relative-path">
  <img src="https://learn.microsoft.com/en-us/defender-xdr/media/security-summary-report/summary-investigation-small.png" alt="Screenshot of the Investigation and Response section in the security summary report" data-linktype="relative-path">
  </a>
  </span>

- **Copilot-powered investigation and response**: This section contains the number of [file analysis in Copilot in Defender](https://learn.microsoft.com/en-us/defender-xdr/copilot-in-defender-file-analysis) and [script analysis in Copilot in Defender](https://learn.microsoft.com/en-us/defender-xdr/security-copilot-m365d-script-analysis) operations where Microsoft Copilot in Defender was used.

  <span class="mx-imgBorder">
  <a href="https://learn.microsoft.com/en-us/defender-xdr/media/security-summary-report/summary-copilot.png#lightbox" data-linktype="relative-path">
  <img src="https://learn.microsoft.com/en-us/defender-xdr/media/security-summary-report/summary-copilot-small.png" alt="Screenshot of the Copilot section in the security summary report" data-linktype="relative-path">
  </a>
  </span>

SOC teams can use the unified security summary to highlight the impact of their day-to-day operations. They can also emphasize how Microsoft’s automated actions impact the efficient protection of their organization with features like automatic attack disruption, which stops attacks before they become widespread.

## Prerequisites

Important

Data for the unified security summary is based on the Microsoft security products and services present in the organization. Data is limited only to the Microsoft products which the user has provisioned access to. For example, if the organization has Microsoft Defender for Endpoint and Microsoft Defender for Office 365, the summary will only show data from these two products.

Users must have the following permissions to view the unified security summary:

- Security data basics \(read\)
- Vulnerability management \(read\)

Additionally, users must have permissions to view all devices in the organization.

## View the unified security summary

To access and share the unified security summary, follow these steps:

1. Sign in to the [Microsoft Defender portal](https://security.microsoft.com).
2. In the navigation, select **Reports**. Under General, select **Unified security summary**.
3. The report page automatically generates data from the last 90 days by default. You can adjust the data to show the last 30 days if needed.  ![Screenshot highlighting the report data duration options in the security summary report](https://learn.microsoft.com/en-us/defender-xdr/media/security-summary-report/duration-picker.png)
4. Once the summary is generated, you can check the details of each card under each section.

   Tip

   Select a card's title to learn more about that card. Selecting the title opens the Microsoft documentation page for that card's feature or metric.
5. You can export the summary as a PDF or CSV file. To export, select the dropdown menu on the upper right corner of the page and choose the format.  ![Screenshot highlighting the export options in the security summary report](https://learn.microsoft.com/en-us/defender-xdr/media/security-summary-report/export-picker.png)
6. If you choose to export the summary as a PDF, an option to customize by adding a logo of your choice is available. Select **Upload logo** to add a logo to the PDF. Otherwise, you can select **Generate PDF** to proceed exporting the summary to a PDF file.  ![Screenshot of the export to PDF dialog box](https://learn.microsoft.com/en-us/defender-xdr/media/security-summary-report/pdf-dialog.png)
7. When exporting the summary as a CSV file, the file is automatically saved to your device as *Unified security summary\_{date and time exported}.csv*. The file contains three columns for the card name, the field name in the card, and the value of the field. Here’s an example.  ![Screenshot of the CSV output of the security summary report](https://learn.microsoft.com/en-us/defender-xdr/media/security-summary-report/csv-sample-values.png)

## Related content

- [Microsoft Defender Antivirus overview](https://learn.microsoft.com/en-us/defender-endpoint/microsoft-defender-antivirus-windows)
- [Microsoft Copilot in Microsoft Defender](https://learn.microsoft.com/en-us/defender-xdr/security-copilot-in-microsoft-365-defender)
