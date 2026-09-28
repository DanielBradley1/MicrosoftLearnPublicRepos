<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-apploguploadstate?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# appLogUploadState enum type

Namespace: microsoft.graph

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

AppLogUploadStatus

## Members

| Member | Value | Description |
| :--- | :--- | :--- |
| pending | 0 | Default. Indicates that request is waiting to be processed or under processing. |
| completed | 1 | Indicates that request is completed with file uploaded to Azure blob for download. |
| failed | 2 | Indicates that request is completed with file uploaded to Azure blob for download. |
| unknownFutureValue | 3 | Evolvable enumeration sentinel value. Do not use. |
