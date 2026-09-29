<!-- Source: https://learn.microsoft.com/en-us/defender-endpoint/run-analyzer-windows -->
<!-- Sitemap-Last-Modified: 2026-07-02 -->

# Run the client analyzer on Windows

Tip

Watch this video to get an overview of the client analyzer: [Defender for Endpoint client analyzer overview](https://www.youtube.com/watch?v=GnqDsvYYL6w)

The Microsoft Defender for Endpoint client analyzer collects diagnostic data and support logs to troubleshoot sensor health, connectivity, and performance issues on Windows devices. You have two options for running the client analyzer:

- Use live response
- Run the client analyzer locally on the device

## Option 1: Live response

You can collect the Defender for Endpoint analyzer support logs remotely using [Live Response](https://learn.microsoft.com/en-us/defender-endpoint/troubleshoot-collect-support-log).

## Option 2: Run MDE Client Analyzer locally

Perform the following steps to download and run MDE Client Analyzer directly on the Windows device:

1. Download the [MDE Client Analyzer tool](https://aka.ms/mdatpanalyzer) or [MDE Client Analyzer tool \(preview\)](https://aka.ms/MDEClientAnalyzerPreview) to the Windows device you want to investigate. The file is saved to your Downloads folder by default.
2. Extract the contents of `MDEClientAnalyzer.zip` to an available folder.
3. Open a command line with administrator permissions:

   1. Go to **Start** and type **cmd**.
   2. Right-click **Command prompt** and select **Run as administrator**.

4. Type the following command and then press **Enter**:

   ```cmd
   *DrivePath*\MDEClientAnalyzer.cmd
   ```


   Replace *DrivePath* with the path where you extracted MDEClientAnalyzer. For example, if you extracted the tool to `C:\Work\tools`, run the following command:


   ```cmd
   C:\Work\tools\MDEClientAnalyzer\MDEClientAnalyzer.cmd
   ```

In addition to running the client analyzer locally on the device, you can also [collect analyzer support logs with Live Response](https://learn.microsoft.com/en-us/defender-endpoint/troubleshoot-collect-support-log).

Note

On Windows 10 and 11, Windows Server 2019 and 2022, or Windows Server 2012R2 and 2016 with the [modern unified solution](https://learn.microsoft.com/en-us/defender-endpoint/onboard-server#functionality-in-the-modern-unified-solution-for-windows-server-2016-and-windows-server-2012-r2) installed, the client analyzer script calls into an executable file called `MDEClientAnalyzer.exe` to run the connectivity tests to cloud service URLs.

On Windows 8.1, Windows Server 2016 or any previous OS edition where Microsoft Monitoring Agent \(MMA\) is used for onboarding, the client analyzer script calls into an executable file called `MDEClientAnalyzerPreviousVersion.exe` to run connectivity tests for Command and Control \(CnC\) URLs while also calling into the MMA connectivity tool `TestCloudConnection.exe` for Cyber Data channel URLs.

Tip

Watch this video to learn more about onboarding issues: [Defender for Endpoint client analyzer onboarding issues](https://www.youtube.com/watch?v=HdhePgMBqs8)

## Important points to keep in mind

All the PowerShell scripts and modules included with the analyzer are Microsoft-signed. If files were modified in any way, then the analyzer is expected to exit with the following error:

[![The client analyzer error](https://learn.microsoft.com/en-us/defender-endpoint/media/sigerror.png)](https://learn.microsoft.com/en-us/defender-endpoint/media/sigerror.png#lightbox)

If the analyzer exits with a file-signature validation error, the issuerInfo.txt output contains detailed information about why the signature check failed and which file was affected:

[![The issuer info](https://learn.microsoft.com/en-us/defender-endpoint/media/issuerinfo.png)](https://learn.microsoft.com/en-us/defender-endpoint/media/issuerinfo.png#lightbox)

The following example shows the contents of issuerInfo.txt when MDEClientAnalyzer.ps1 has been modified:

[![The modified ps1 file](https://learn.microsoft.com/en-us/defender-endpoint/media/modified-ps1.png)](https://learn.microsoft.com/en-us/defender-endpoint/media/modified-ps1.png#lightbox)

## Result package contents on Windows

After the analyzer completes, it produces a result package containing diagnostic files and folders.

Note

The exact files captured might change depending on factors such as:

- The version of windows on which the analyzer is run.
- Event log channel availability on the machine.
- The start state of the EDR sensor \(Sense is stopped if machine isn't yet onboarded\).
- If an advanced troubleshooting parameter was used with the analyzer command.

By default, the unpacked `MDEClientAnalyzerResult.zip` file contains the items listed in the following table:

| Folder | Item | Description |
| --- | --- | --- |
|  | `MDEClientAnalyzer.htm` | This is the main HTML output file, which contains the findings and guidance that the analyzer script run on the machine can produce. |
| `SystemInfoLogs` | `AddRemovePrograms.csv` | List of x64 installed software on x64 OS collected from registry |
| `SystemInfoLogs` | `AddRemoveProgramsWOW64.csv` | List of x86 installed software on x64 OS collected from registry |
| `SystemInfoLogs` | `CertValidate.log` | Detailed result from certificate revocation executed by calling into [CertUtil](https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/certutil) |
| `SystemInfoLogs` | `dsregcmd.txt` | Output from running [dsregcmd](https://learn.microsoft.com/en-us/azure/active-directory/devices/troubleshoot-device-dsregcmd). This provides details about the Microsoft Entra status of the machine. |
| `SystemInfoLogs` | `IFEO.txt` | Output of [Image File Execution Options](https://learn.microsoft.com/en-us/previous-versions/windows/desktop/xperf/image-file-execution-options) configured on the machine |
| `SystemInfoLogs` | `MDEClientAnalyzer.txt` | This is verbose text file showing with details of the analyzer script execution. |
| `SystemInfoLogs` | `MDEClientAnalyzer.xml` | XML format containing the analyzer script findings |
| `SystemInfoLogs` | `RegOnboardedInfoCurrent.Json` | The onboarded machine information gathered in JSON format from the registry |
| `SystemInfoLogs` | `RegOnboardingInfoPolicy.Json` | The onboarding policy configuration gathered in JSON format from the registry |
| `SystemInfoLogs` | `SCHANNEL.txt` | Details about [SCHANNEL configuration](https://learn.microsoft.com/en-us/windows-server/security/tls/manage-tls) applied to the machine such gathered from registry |
| `SystemInfoLogs` | `SessionManager.txt` | Session Manager specific settings gather from registry |
| `SystemInfoLogs` | `SSL_00010002.txt` | Details about [SSL configuration](https://learn.microsoft.com/en-us/windows-server/security/tls/manage-tls) applied to the machine gathered from registry |
| `EventLogs` | `utc.evtx` | Export of DiagTrack event log |
| `EventLogs` | `senseIR.evtx` | Export of the Automated Investigation event log |
| `EventLogs` | `sense.evtx` | Export of the Sensor main event log |
| `EventLogs` | `OperationsManager.evtx` | Export of the Microsoft Monitoring Agent event log |
| `MdeConfigMgrLogs` | `SecurityManagementConfiguration.json` | Configurations sent from MEM \(Microsoft Endpoint Manager\) for enforcement |
| `MdeConfigMgrLogs` | `policies.json` | Policies settings to be enforced on the device |
| `MdeConfigMgrLogs` | `report_xxx.json` | Corresponding enforcement results |

## Related content

- [Client analyzer overview](https://learn.microsoft.com/en-us/defender-endpoint/overview-client-analyzer)
- [Data collection for advanced troubleshooting on Windows](https://learn.microsoft.com/en-us/defender-endpoint/data-collection-analyzer)
- [Understand the analyzer HTML report](https://learn.microsoft.com/en-us/defender-endpoint/analyzer-report)
