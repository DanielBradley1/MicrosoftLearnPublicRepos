<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/faq/file-sizes -->
<!-- Sitemap-Last-Modified: 2025-02-27 -->

# What are the file sizes supported by Microsoft 365 for the web?

The explicit limits, where applicable, are listed in the table below. However, note that there is a 60-second file download time out that applies to all [GetFile](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/files/getfile#getfile) operations, and this time out can affect the perceived file size limit. In practice, this time out is rarely hit, since connectivity and bandwidth is typically very good between Microsoft 365 for the web and host datacenters. However, hosts should be aware of this limit.

Tip

The [**FileUrl**](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/files/checkfileinfo/checkfileinfo-response#fileurl) property can be set to change the URL that Microsoft 365 for the web will use to download files from the host. This can be used to increase download speeds depending on the host’s architecture.

***Table 8*** - *File size limits*

## File size limits

| Application | Mode | CSPP Limit | CSPP+ Limit | Notes |
| --- | --- | --- | --- | --- |
| Word for the web | View | See notes | See notes | No limit, but subject to the 60 second time out for file downloads as described above. |
| Word for the web | Edit | 100MB | 100MB |  |
| Excel for the web | View | 25MB | 100MB |  |
| Excel for the web | Edit | 25MB | 100MB |  |
| PowerPoint for the web | View | See notes | See notes | No limit, but subject to the 60 second time out for file downloads as described above. |
| PowerPoint for the web | Edit | 300MB | 2GB | This is still subject to the overall 60 second time out for file downloads so it is possible that smaller files will hit that timeout. In addition, for embedded media, the size limit is 100MB for most embedded media types. For WAV files the limit is 100KB. |

Note

The above limits only apply to Microsoft 365 for the web integrations via the CSPP program.

Desktop and mobile clients integrated via CSPP+ do not have these limitations. However, extremely large files, network bandwidth, and other environmental factors can reduce overall performance.

See [File size limits for workbooks in SharePoint](https://support.microsoft.com/office/file-size-limits-for-workbooks-in-sharepoint-9e5bc6f8-018f-415a-b890-5452687b325e) for additional information on workbook limits in Excel for the web for files stored in OneDrive or SharePoint.
