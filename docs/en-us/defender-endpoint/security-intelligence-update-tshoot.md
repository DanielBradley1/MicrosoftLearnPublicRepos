<!-- Source: https://learn.microsoft.com/en-us/defender-endpoint/security-intelligence-update-tshoot -->
<!-- Sitemap-Last-Modified: 2025-09-29 -->

# Troubleshooting Security Intelligence Updates from Microsoft Update source

Use this article to learn how to troubleshoot security intelligence updates for Microsoft Defender Antivirus when the first source is from Microsoft Update \(formerly known as Windows Update\). Follow these steps to troubleshoot issues with getting your security intelligence updates:

1. Make sure that the URLs needed for security intelligence updates are allowed thru the firewall or proxy. See the Defender for Endpoint URL spreadsheets in [Configure your network environment to ensure connectivity with Defender for Endpoint service](https://learn.microsoft.com/en-us/defender-endpoint/configure-environment).

   If you're only using Microsoft Defender Antivirus, see the **Windows Update** section in [Manage connection endpoints for Windows 11 Enterprise](https://learn.microsoft.com/en-us/windows/privacy/manage-windows-11-endpoints).
2. Make sure that the URLs you reviewed during the previous step aren't SSL inspected. Otherwise, you might see the following error in the event log:

   ```properties

   Source: Windows Defender

   Event ID: 2001 

   Microsoft Defender Antivirus has encountered an error trying to update security intelligence.

   Error code: 0x80072ee7

   Error description: The server name or address could not be resolved.
   ```


   What is error code `0x80072ee7`?


   ```properties

   C:\>err 0x80072ee7

   # as an HRESULT: Severity: FAILURE (1), Facility: 0x7, Code 0x2ee7

   # for hex 0x2ee7 / decimal 12007 :

   ERROR_INTERNET_NAME_NOT_RESOLVED                              inetmsg.h

   ERROR_INTERNET_NAME_NOT_RESOLVED                              wininet.h
   ```

3. Make sure that the services needed for Windows Update are started. These services include:

   - Windows Update service
   - Background Intelligence Transfer Service \(BITS\)

4. If you're using a [Fallback order](https://learn.microsoft.com/en-us/defender-endpoint/manage-protection-updates-microsoft-defender-antivirus) policy, make sure that *Microsoft Update* \(`MicrosoftUpdateServer`\) is the first item in the list.
5. Gather diagnostic data from the [Microsoft Defender for Endpoint Client Analyzer tool](https://learn.microsoft.com/en-us/defender-endpoint/overview-client-analyzer).

   - If you have Microsoft Defender for Endpoint Plan 2 and access to Live Response, you can gather the diagnostic data remotely. See [Collect support logs in Microsoft Defender for Endpoint using live response](https://learn.microsoft.com/en-us/defender-endpoint/troubleshoot-collect-support-log).
   - If you have Microsoft Defender for Endpoint Plan 1 or only Microsoft Defender Antivirus, you can gather the diagnostic data using the client analyzer on Windows. See [Run the client analyzer on Windows](https://learn.microsoft.com/en-us/defender-endpoint/run-analyzer-windows).
   - If either method doesn't work for you, use Microsoft Defender Antivirus diagnostic data collection. See [Collect Microsoft Defender Antivirus diagnostic data](https://learn.microsoft.com/en-us/defender-endpoint/collect-diagnostic-data).

6. When you have your diagnostic data, convert the `WindowsUpdate.etl` logs into a human readable format by using the PowerShell command, [Get-WindowsUpdateLog](https://learn.microsoft.com/en-us/powershell/module/windowsupdate/get-windowsupdatelog). Use that information to troubleshoot issues with security intelligence updates.

## See also

- [Troubleshoot Microsoft Defender Antivirus settings](https://learn.microsoft.com/en-us/defender-endpoint/troubleshoot-settings)
- [Troubleshoot problems with tamper protection](https://learn.microsoft.com/en-us/defender-endpoint/tamper-protection-troubleshoot)
