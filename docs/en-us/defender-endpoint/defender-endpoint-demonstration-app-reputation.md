<!-- Source: https://learn.microsoft.com/en-us/defender-endpoint/defender-endpoint-demonstration-app-reputation -->
<!-- Sitemap-Last-Modified: 2026-01-15 -->

# SmartScreen app reputation demonstration

Test how Microsoft Defender for Endpoint SmartScreen helps you identify phishing and malware websites based on App reputation.

## Prerequisites

- Microsoft Edge or Internet Explorer browser required.

### Supported operating systems

- Windows 11
- Windows 10
- Windows Server 2016 and later
- Windows Server 2012 R2
- Windows Server 2008 R2
- Azure Stack HCI OS, version 23H2 and later.

## Scenario Demos

### Known good program

This program has a good reputation; the download should run uninterrupted:

- [Known good program download](https://demo.smartscreen.msft.net/download/known/freevideo.exe)

  Launching this link should render a message similar to the following:

  ![Based on the target file's reputation, SmartScreen allows the download without interference.](https://learn.microsoft.com/en-us/defender-endpoint/media/smartscreen-app-reputation-known-good.png)

### Unknown program

Because the program download doesn't have sufficient reputation to ensure that it's trustworthy, SmartScreen will show a warning before running the program download.

- [Unknown program](https://demo.smartscreen.msft.net/download/unknown/freevideo.exe)

  Launching this link should render a message similar to the following:

  ![SmartScreen doesn't have sufficient reputation information about the download file, and warns the user to stop or proceed with caution.](https://learn.microsoft.com/en-us/defender-endpoint/media/smartscreen-app-reputation-unknown.png)

### Known malware

This download is known malware; SmartScreen should block this program from running.

- [Known malware](https://demo.smartscreen.msft.net/download/known/knownmalicious.exe)

  Launching this link should render a message similar to the following:

  ![Screenshot showing how SmartScreen detects a file download with an unsafe reputation; the download is blocked.](https://learn.microsoft.com/en-us/defender-endpoint/media/smartscreen-app-reputation-known-malware.png)

## Learn more

[Microsoft Defender SmartScreen Documentation](https://learn.microsoft.com/en-us/windows/security/operating-system-security/virus-and-threat-protection/microsoft-defender-smartscreen/)

## See also

[Microsoft Defender for Endpoint - demonstration scenarios](https://learn.microsoft.com/en-us/defender-endpoint/defender-endpoint-demonstrations)
