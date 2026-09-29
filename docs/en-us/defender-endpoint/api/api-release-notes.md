<!-- Source: https://learn.microsoft.com/en-us/defender-endpoint/api/api-release-notes -->
<!-- Sitemap-Last-Modified: 2025-09-29 -->

# Microsoft Defender for Endpoint API release notes

The following information lists the updates made to the Microsoft Defender for Endpoint APIs and the dates they were made.

## Release notes - newest to oldest \(dd.mm.yyyy\)

### 08.08.2022

- Added new Export Device Health API method - GET /api/public/avdeviceshealth [Export device health methods and properties](https://learn.microsoft.com/en-us/defender-endpoint/api/device-health-api-methods-properties)

### 06.10.2021

- Added new Export assessment API method - *Delta Export software vulnerabilities assessment \(JSON response\)* [Export assessment methods and properties per device](https://learn.microsoft.com/en-us/defender-endpoint/api/get-assessment-methods-properties).

### 25.05.2021

- Added new API [Export assessment methods and properties per device](https://learn.microsoft.com/en-us/defender-endpoint/api/get-assessment-methods-properties).

### 03.05.2021

- Added new API: [Remediation activity methods and properties](https://learn.microsoft.com/en-us/defender-endpoint/api/get-remediation-methods-properties).

### 10.02.2021

- Added new API: [Batch update alerts](https://learn.microsoft.com/en-us/defender-endpoint/api/batch-update-alerts).

### 25.01.2021

- Updated rate limitations for [Advanced Hunting API](https://learn.microsoft.com/en-us/defender-endpoint/api/run-advanced-query-api) from 15 to 45 requests per minute.

### 21.01.2021

- Added new API: [Find devices by tag](https://learn.microsoft.com/en-us/defender-endpoint/machine-tags).
- Added new API: [Import Indicators](https://learn.microsoft.com/en-us/defender-endpoint/api/import-ti-indicators).

### 03.01.2021

- Updated Alert evidence: added ***detectionStatus***, ***parentProcessFilePath*** and ***parentProcessFileName*** properties.
- Updated [Alert entity](https://learn.microsoft.com/en-us/defender-endpoint/api/alerts): added ***detectorId*** property.

### 15.12.2020

- Updated [Device](https://learn.microsoft.com/en-us/defender-endpoint/api/machine) entity: added ***IpInterfaces*** list. See [List devices](https://learn.microsoft.com/en-us/defender-endpoint/api/get-machines).

### 04.11.2020

- Added new API: [Set device value](https://learn.microsoft.com/en-us/defender-endpoint/api/set-device-value).
- Updated [Device](https://learn.microsoft.com/en-us/defender-endpoint/api/machine) entity: added ***deviceValue*** property.

### 01.09.2020

- Added option to expand the Alert entity with its related Evidence. See [List Alerts](https://learn.microsoft.com/en-us/defender-endpoint/api/get-alerts).

Tip

Do you want to learn more? Engage with the Microsoft Security community in our Tech Community: [Microsoft Defender for Endpoint Tech Community](https://techcommunity.microsoft.com/t5/microsoft-defender-for-endpoint/bd-p/MicrosoftDefenderATP).
