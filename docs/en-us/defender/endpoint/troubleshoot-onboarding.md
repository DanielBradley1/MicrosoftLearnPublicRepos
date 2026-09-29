<!-- Source: https://learn.microsoft.com/en-us/defender-endpoint/troubleshoot-onboarding -->
<!-- Sitemap-Last-Modified: 2026-03-05 -->

# Troubleshoot Microsoft Defender for Endpoint onboarding issues

You might need to troubleshoot the Microsoft Defender for Endpoint onboarding process if you encounter issues. This article provides detailed steps to troubleshoot onboarding issues that might occur when deploying with one of the deployment tools and common errors that might occur on the devices.

Before you start troubleshooting issues with onboarding tools, it's important to check if the minimum requirements are met for onboarding devices to the services. [Learn about the licensing, hardware, and software requirements to onboard devices to the service](https://learn.microsoft.com/en-us/defender-endpoint/minimum-requirements).

Tip

As a companion to this article, see our [Microsoft Defender for Endpoint setup guide](https://go.microsoft.com/fwlink/p/?linkid=2268087) to review best practices and learn about essential tools such as attack surface reduction and next-generation protection. For a customized experience based on your environment, you can access the Defender for [Endpoint automated setup guide](https://go.microsoft.com/fwlink/p/?linkid=2268088) in the Microsoft 365 admin center.

## Prerequisites

### Supported operating systems

- Windows Server 2012 R2 and later

## Troubleshoot issues with onboarding tools

If you've completed the onboarding process and don't see devices in the [Devices list](https://learn.microsoft.com/en-us/defender-endpoint/investigate-machines) after an hour, it might indicate an onboarding or connectivity problem.

### Troubleshoot onboarding when deploying with Group Policy

Deployment with Group Policy is done by running the onboarding script on the devices. The Group Policy console doesn't indicate if the deployment has succeeded or not.

If you've completed the onboarding process and don't see devices in the [Devices list](https://learn.microsoft.com/en-us/defender-endpoint/investigate-machines) after an hour, you can check the output of the script on the devices. For more information, see [Troubleshoot onboarding when deploying with a script](#troubleshoot-onboarding-when-deploying-with-a-script).

If the script completes successfully, see [Troubleshoot onboarding issues on the devices](#troubleshoot-onboarding-issues-on-the-device) for additional errors that might occur.

### Troubleshoot onboarding issues when deploying with Microsoft Configuration Manager

### Troubleshoot onboarding when deploying with a script

Tip

In Microsoft Configuration Manager version 1606 \(July 2016\) or later, you're no longer required to onboard devices using a local script. Instead, you can deploy onboarding configuration files via applications or endpoint protection policies. You can still use local scripts for manual device onboarding of a small number of devices.

You can track the deployment in the Configuration Manager Console. If the deployment fails, you can check the output of the script on the devices.

If the onboarding completed successfully but the devices aren't showing up in the **Devices list** after one hour, see [Troubleshoot onboarding issues on the device](#troubleshoot-onboarding-issues-on-the-device) for additional errors that might occur.

**Check the result of the script on the device:**

1. Click **Start**, type **Event Viewer**, and press **Enter**.
2. Go to **Windows Logs** > **Application**.
3. Look for an event from **WDATPOnboarding** event source.

If the script fails and the event is an error, you can check the event ID in the following table to help you troubleshoot the issue.

Note

The following event IDs are specific to the onboarding script only.

| Event ID | Error Type | Resolution steps |
| :---: | --- | --- |
| `5` | Offboarding data was found but couldn't be deleted | Check the permissions on the registry, specifically<br><br>`HKLM\\SOFTWARE\\Policies\\Microsoft\\Windows Advanced Threat Protection`. |
| `10` | Onboarding data couldn't be written to registry | Check the permissions on the registry, specifically<br><br>`HKLM\\SOFTWARE\\Policies\\Microsoft\\Windows Advanced Threat Protection`.<br><br>Verify that the script has been run as an administrator. |
| `15` | Failed to start SENSE service | Check the service health \(`sc query sense` command\). Make sure it's not in an intermediate state \(*'Pending\_Stopped'*, *'Pending\_Running'*\) and try to run the script again \(with administrator rights\).<br><br>If the device is running Windows 10, version 1607 and running the command `sc query sense` returns `START_PENDING`, reboot the device. If rebooting the device doesn't address the issue, upgrade to KB4015217 and try onboarding again. |
| `15` | Failed to start SENSE service | If the message of the error is: System error 577 or error 1058 has occurred, you need to enable the Microsoft Defender Antivirus ELAM driver, see [Ensure that Microsoft Defender Antivirus is not disabled by a policy](#ensure-that-microsoft-defender-antivirus-is-not-disabled-by-a-policy) for instructions. |
| `15` | Failed to start SENSE service | The SENSE Feature on Demand \(FoD\) may not be installed. To determine whether it is installed, enter the following command from an Admin CMD/PowerShell prompt: `DISM.EXE /Online /Get-CapabilityInfo /CapabilityName:Microsoft.Windows.Sense.Client~~~~` If it returns an error or the state is not "Installed," then the SENSE FoD must be installed. See [Available Features on Demand: SENSE Client for Microsoft Defender for Endpoint](https://learn.microsoft.com/en-us/windows-hardware/manufacture/desktop/features-on-demand-non-language-fod?view=windows-11&preserve-view=true) for installation instructions. |
| `30` | The script failed to wait for the service to start running | The service could have taken more time to start or has encountered errors while trying to start. For more information on events and errors related to SENSE, see [Review events and errors using Event viewer](https://learn.microsoft.com/en-us/defender-endpoint/event-error-codes). |
| `35` | The script failed to find needed onboarding status registry value | When the SENSE service starts for the first time, it writes onboarding status to the registry location<br><br>`HKLM\\SOFTWARE\\Microsoft\\Windows Advanced Threat Protection\\Status`.<br><br>The script failed to find it after several seconds. You can manually test it and check if it's there. For more information on events and errors related to SENSE, see [Review events and errors using Event viewer](https://learn.microsoft.com/en-us/defender-endpoint/event-error-codes). |
| `40` | SENSE service onboarding status isn't set to **1** | The SENSE service has failed to onboard properly. For more information on events and errors related to SENSE, see [Review events and errors using Event viewer](https://learn.microsoft.com/en-us/defender-endpoint/event-error-codes). |
| `65` | Insufficient privileges | Run the script again with administrator privileges. |
| `70` | Offboarding script is for a different organization | Get an offboarding script for the correct organization that the SENSE service is onboarded to. |

### Troubleshoot onboarding issues using Microsoft Intune

You can use Microsoft Intune to check error codes and attempt to troubleshoot the cause of the issue.

If you have configured policies in Intune and they aren't propagated on devices, you might need to configure automatic MDM enrollment.

Use the following tables to understand the possible causes of issues while onboarding:

- Microsoft Intune error codes and OMA-URIs table
- Known issues with non-compliance table
- Mobile Device Management \(MDM\) event logs table

If none of the event logs and troubleshooting steps work, download the Local script from the **Device management** section of the portal, and run it in an elevated command prompt.

#### Microsoft Intune error codes and OMA-URIs

| Error Code Hex | Error Code Dec | Error Description | OMA-URI | Possible cause and troubleshooting steps |
| :---: | --- | --- | --- | --- |
| 0x87D1FDE8 | -2016281112 | Remediation failed | Onboarding<br><br>Offboarding | **Possible cause:** Onboarding or offboarding failed on a wrong blob: wrong signature or missing PreviousOrgIds fields.<br><br>**Troubleshooting steps:**<br><br>Check the event IDs in the [View agent onboarding errors in the device event log](#view-agent-onboarding-errors-in-the-device-event-log) section.<br><br>Check the MDM event logs in the following table or follow the instructions in [Diagnose MDM failures in Windows](https://learn.microsoft.com/en-us/windows/client-management/mdm/diagnose-mdm-failures-in-windows-10). |
|  |  |  | Onboarding<br><br>Offboarding<br><br>SampleSharing | **Possible cause:** Microsoft Defender for Endpoint Policy registry key doesn't exist or the OMA DM client doesn't have permissions to write to it.<br><br>**Troubleshooting steps:** Ensure that the following registry key exists: `HKEY_LOCAL_MACHINE\\SOFTWARE\\Policies\\Microsoft\\Windows Advanced Threat Protection`<br><br>If it doesn't exist, open an elevated command and add the key. |
|  |  |  | SenseIsRunning<br><br>OnboardingState<br><br>OrgId | **Possible cause:** An attempt to remediate by read-only property. Onboarding has failed.<br><br>**Troubleshooting steps:** Check the troubleshooting steps in [Troubleshoot onboarding issues on the device](#troubleshoot-onboarding-issues-on-the-device).<br><br>Check the MDM event logs in the following table or follow the instructions in [Diagnose MDM failures in Windows](https://learn.microsoft.com/en-us/windows/client-management/mdm/diagnose-mdm-failures-in-windows-10). |
|  |  |  | All | **Possible cause:** Attempt to deploy Microsoft Defender for Endpoint on non-supported SKU/Platform, particularly Holographic SKU.<br><br>Currently supported platforms:<br><br>Enterprise, Education, and Professional.<br><br>Server isn't supported. |
| 0x87D101A9 | -2016345687 | SyncML\(425\): The requested command failed because the sender doesn't have adequate access control permissions \(ACL\) on the recipient. | All | **Possible cause:** Attempt to deploy Microsoft Defender for Endpoint on non-supported SKU/Platform, particularly Holographic SKU.<br><br>Currently supported platforms:<br><br>Enterprise, Education, and Professional. |

#### Known issues with non-compliance

The following table provides information on issues with non-compliance and how you can address the issues.

| Case | Symptoms | Possible cause and troubleshooting steps |
| :---: | --- | --- |
| `1` | Device is compliant by SenseIsRunning OMA-URI. But is non-compliant by OrgId, Onboarding and OnboardingState OMA-URIs. | **Possible cause:** Check that user passed OOBE after Windows installation or upgrade. During OOBE onboarding couldn't be completed but SENSE is running already.<br><br>**Troubleshooting steps:** Wait for OOBE to complete. |
| `2` | Device is compliant by OrgId, Onboarding, and OnboardingState OMA-URIs, but is non-compliant by SenseIsRunning OMA-URI. | **Possible cause:** Sense service's startup type is set as "Delayed Start". Sometimes this causes the Microsoft Intune server to report the device as non-compliant by SenseIsRunning when DM session occurs on system start.<br><br>**Troubleshooting steps:** The issue should automatically be fixed within 24 hours. |
| `3` | Device is non-compliant | **Troubleshooting steps:** Ensure that Onboarding and Offboarding policies aren't deployed on the same device at same time. |

#### Mobile Device Management \(MDM\) event logs

View the MDM event logs to troubleshoot issues that might arise during onboarding:

Log name: Microsoft\\Windows\\DeviceManagement-EnterpriseDiagnostics-Provider

Channel name: Admin

| ID | Severity | Event description | Troubleshooting steps |
| --- | --- | --- | --- |
| 1819 | Error | Microsoft Defender for Endpoint CSP: Failed to Set Node's Value. NodeId: \(%1\), TokenName: \(%2\), Result: \(%3\). | Download the [Cumulative Update for Windows 10, 1607](https://go.microsoft.com/fwlink/?linkid=829760). |

## Troubleshoot onboarding issues on the device

If the deployment tools used do not indicate an error in the onboarding process, but devices are still not appearing in the devices list in an hour, go through the following verification topics to check if an error occurred with the Microsoft Defender for Endpoint agent.

- [View agent onboarding errors in the device event log](#view-agent-onboarding-errors-in-the-device-event-log)
- [Ensure the diagnostic data service is enabled](#ensure-the-diagnostics-service-is-enabled)
- [Ensure the service is set to start](#ensure-the-service-is-set-to-start)
- [Ensure the device has an Internet connection](#ensure-the-device-has-an-internet-connection)
- [Ensure that Microsoft Defender Antivirus is not disabled by a policy](#ensure-that-microsoft-defender-antivirus-is-not-disabled-by-a-policy)

### View agent onboarding errors in the device event log

1. Click **Start**, type **Event Viewer**, and press **Enter**.
2. In the **Event Viewer \(Local\)** pane, expand **Applications and Services Logs** > **Microsoft** > **Windows** > **SENSE**.

   Note

   SENSE is the internal name used to refer to the behavioral sensor that powers Microsoft Defender for Endpoint.
3. Select **Operational** to load the log.
4. In the **Action** pane, click **Filter Current log**.
5. On the **Filter** tab, under **Event level:** select **Critical**, **Warning**, and **Error**, and click **OK**.

   [![The Event Viewer log filter](https://learn.microsoft.com/en-us/defender-endpoint/media/filter-log.png)](https://learn.microsoft.com/en-us/defender-endpoint/media/filter-log.png#lightbox)
6. Events which can indicate issues appear in the **Operational** pane. You can attempt to troubleshoot them based on the solutions in the following table:
   | Event ID | Message | Resolution steps |
   | :---: | --- | --- |
   | `5` | Microsoft Defender for Endpoint service failed to connect to the server at *variable* | [Ensure the device has Internet access](#ensure-the-device-has-an-internet-connection). |
   | `6` | Microsoft Defender for Endpoint service isn't onboarded and no onboarding parameters were found. Failure code: *variable* | [Run the onboarding script again](https://learn.microsoft.com/en-us/defender-endpoint/configure-endpoints-script). |
   | `7` | Microsoft Defender for Endpoint service failed to read the onboarding parameters. Failure code: *variable* | [Ensure the device has Internet access](#ensure-the-device-has-an-internet-connection), then run the entire onboarding process again. |
   | `9` | Microsoft Defender for Endpoint service failed to change its start type. Failure code: variable | If the event happened during onboarding, reboot and re-attempt running the onboarding script. For more information, see [Run the onboarding script again](https://learn.microsoft.com/en-us/defender-endpoint/configure-endpoints-script).  <br>  <br>If the event happened during offboarding, contact support. |
   | `10` | Microsoft Defender for Endpoint service failed to persist the onboarding information. Failure code: variable | If the event happened during onboarding, re-attempt running the onboarding script. For more information, see [Run the onboarding script again](https://learn.microsoft.com/en-us/defender-endpoint/configure-endpoints-script).  <br>  <br>If the problem persists, contact support. |
   | `15` | Microsoft Defender for Endpoint can't start command channel with URL: *variable* | [Ensure the device has Internet access](#ensure-the-device-has-an-internet-connection). |
   | `17` | Microsoft Defender for Endpoint service failed to change the Connected User Experiences and Telemetry service location. Failure code: variable | [Run the onboarding script again](https://learn.microsoft.com/en-us/defender-endpoint/configure-endpoints-script). If the problem persists, contact support. |
   | `25` | Microsoft Defender for Endpoint service failed to reset health status in the registry. Failure code: *variable* | Contact support. |
   | `27` | Failed to enable Microsoft Defender for Endpoint mode in Windows Defender. Onboarding process failed. Failure code: variable | Contact support. |
   | `29` | Failed to read the offboarding parameters. Error type: %1, Error code: %2, Description: %3 | Ensure the device has Internet access, then run the entire offboarding process again. |
   | `30` | Failed to disable $\(build.sense.productDisplayName\) mode in Microsoft Defender for Endpoint. Failure code: %1 | Contact support. |
   | `32` | $\(build.sense.productDisplayName\) service failed to request to stop itself after offboarding process. Failure code: %1 | Verify that the service start type is manual and reboot the device. |
   | `55` | Failed to create the Secure ETW autologger. Failure code: %1 | Reboot the device. |
   | `63` | Updating the start type of external service. Name: %1, actual start type: %2, expected start type: %3, exit code: %4 | Identify what is causing changes in start type of mentioned service. If the exit code isn't 0, fix the start type manually to expected start type. |
   | `64` | Starting stopped external service. Name: %1, exit code: %2 | Contact support if the event keeps re-appearing. |
   | `68` | The start type of the service is unexpected. Service name: %1, actual start type: %2, expected start type: %3 | Identify what is causing changes in start type. Fix mentioned service start type. |
   | `69` | The service is stopped. Service name: %1 | Start the mentioned service. Contact support if the issue persists. |

There are additional components on the device that the Microsoft Defender for Endpoint agent depends on to function properly. If there are no onboarding related errors in the Microsoft Defender for Endpoint agent event log, proceed with the following steps to ensure that the additional components are configured correctly.

<span id="ensure-the-diagnostics-service-is-enabled">
<h3 id="ensure-the-diagnostic-data-service-is-enabled">Ensure the diagnostic data service is enabled</h3>
<div class="NOTE">
<p>Note</p>
<p>In Windows 10 build 1809 and later, the Defender for Endpoint EDR service no longer has a direct dependency on the DiagTrack service.
The EDR cyber evidence can still be uploaded if this service is not running.</p>
</div>
<p>If the devices aren&#39;t reporting correctly, you might need to check that the Windows diagnostic data service is set to automatically start and is running on the device. The service might have been disabled by other programs or user configuration changes.</p>
<p>First, you should check that the service is set to start automatically when Windows starts, then you should check that the service is currently running (and start it if it isn&#39;t).</p>
<h3 id="ensure-the-service-is-set-to-start">Ensure the service is set to start</h3>
<p><strong>Use the command line to check the Windows diagnostic data service startup type</strong>:</p>
<ol>
<li><p>Open an elevated command-line prompt on the device:</p>
<p>a. Click <strong>Start</strong>, type <strong>cmd</strong>, and press <strong>Enter</strong>.</p>
<p>b. Right-click <strong>Command prompt</strong> and select <strong>Run as administrator</strong>.</p>
</li>
<li><p>Enter the following command, and press <strong>Enter</strong>:</p>
<pre><code class="lang-console">sc qc diagtrack
</code></pre>
<p>If the service is enabled, then the result should look like the following screenshot:</p>
<p><span class="mx-imgBorder">
<a href="https://learn.microsoft.com/en-us/defender-endpoint/media/windefatp-sc-qc-diagtrack.png#lightbox" data-linktype="relative-path">
<img src="https://learn.microsoft.com/en-us/defender-endpoint/media/windefatp-sc-qc-diagtrack.png" alt="The result of the sc query command for diagtrack" data-linktype="relative-path">
</a>
</span>
</p>
<p>If the <code>START_TYPE</code> isn&#39;t set to <code>AUTO_START</code>, then you need to set the service to automatically start.</p>
</li>
</ol>
<p><strong>Use the command line to set the Windows diagnostic data service to automatically start:</strong></p>
<ol>
<li><p>Open an elevated command-line prompt on the device:</p>
<p>a. Click <strong>Start</strong>, type <strong>cmd</strong>, and press <strong>Enter</strong>.</p>
<p>b. Right-click <strong>Command prompt</strong> and select <strong>Run as administrator</strong>.</p>
</li>
<li><p>Enter the following command, and press <strong>Enter</strong>:</p>
<pre><code class="lang-console">sc config diagtrack start=auto
</code></pre>
</li>
<li><p>A success message is displayed. Verify the change by entering the following command, and press <strong>Enter</strong>:</p>
<pre><code class="lang-console">sc qc diagtrack
</code></pre>
</li>
<li><p>Start the service. In the command prompt, type the following command and press <strong>Enter</strong>:</p>
<pre><code class="lang-console">sc start diagtrack
</code></pre>
</li>
</ol>
<h3 id="ensure-the-device-has-an-internet-connection">Ensure the device has an Internet connection</h3>
<p>The Microsoft Defender for Endpoint sensor requires Microsoft Windows HTTP (WinHTTP) to report sensor data and communicate with the Microsoft Defender for Endpoint service.</p>
<p>WinHTTP is independent of the Internet browsing proxy settings and other user context applications and must be able to detect the proxy servers that are available in your particular environment.</p>
<p>To ensure that sensor has service connectivity, follow the steps described in the <a href="https://learn.microsoft.com/en-us/defender-endpoint/verify-connectivity" data-linktype="relative-path">Verify client connectivity to Microsoft Defender for Endpoint service URLs</a> topic.</p>
<p>If the verification fails and your environment is using a proxy to connect to the Internet, then follow the steps described in <a href="https://learn.microsoft.com/en-us/defender-endpoint/configure-proxy-internet" data-linktype="relative-path">Configure proxy and Internet connectivity settings</a> topic.</p>
<h3 id="ensure-that-microsoft-defender-antivirus-is-not-disabled-by-a-policy">Ensure that Microsoft Defender Antivirus is not disabled by a policy</h3>
<div class="IMPORTANT">
<p>Important</p>
<p>The following only applies to devices that have <strong>not</strong> yet received the August 2020 (version 4.18.2007.8) update to Microsoft Defender Antivirus.</p>
<p>The update ensures that Microsoft Defender Antivirus cannot be turned off on client devices via system policy.</p>
</div>
<p><strong>Problem</strong>: The Microsoft Defender for Endpoint service doesn&#39;t start after onboarding.</p>
<p><strong>Symptom</strong>: Onboarding successfully completes, but you see error 577 or error 1058 when trying to start the service.</p>
<p><strong>Solution</strong>: If your devices are running a third-party antimalware client, the Microsoft Defender for Endpoint agent needs the Early Launch Antimalware (ELAM) driver to be enabled. You must ensure that it&#39;s not turned off by a system policy.</p>
<ul>
<li><p>Depending on the tool that you use to implement policies, you need to verify that the following Windows Defender policies are cleared:</p>
<ul>
<li>DisableAntiSpyware</li>
<li>DisableAntiVirus</li>
</ul>
<p>For example, in Group Policy there should be no entries such as the following values:</p>
<ul>
<li><code>&lt;Key Path=&quot;SOFTWARE\Policies\Microsoft\Windows Defender&quot;&gt;&lt;KeyValue Value=&quot;0&quot; ValueKind=&quot;DWord&quot; Name=&quot;DisableAntiSpyware&quot;/&gt;&lt;/Key&gt;</code></li>
<li><code>&lt;Key Path=&quot;SOFTWARE\Policies\Microsoft\Windows Defender&quot;&gt;&lt;KeyValue Value=&quot;0&quot; ValueKind=&quot;DWord&quot; Name=&quot;DisableAntiVirus&quot;/&gt;&lt;/Key&gt;</code></li>
</ul>
</li>
</ul>
<div class="IMPORTANT">
<p>Important</p>
<p>The <code>disableAntiSpyware</code> setting is discontinued and will be ignored on all Windows 10 devices, as of the August 2020 (version 4.18.2007.8) update to Microsoft Defender Antivirus.</p>
</div>
<ul>
<li><p>After clearing the policy, run the onboarding steps again.</p>
</li>
<li><p>You can also check the previous registry key values to verify that the policy is disabled, by opening the registry key <code>HKEY_LOCAL_MACHINE\SOFTWARE\Policies\Microsoft\Windows Defender</code>.</p>
<p><span class="mx-imgBorder">
<a href="https://learn.microsoft.com/en-us/defender-endpoint/media/atp-disableantispyware-regkey.png#lightbox" data-linktype="relative-path">
<img src="https://learn.microsoft.com/en-us/defender-endpoint/media/atp-disableantispyware-regkey.png" alt="The registry key for Microsoft Defender Antivirus" data-linktype="relative-path">
</a>
</span>
</p>
<div class="NOTE">
<p>Note</p>
<p>All Windows Defender services (<code>wdboot</code>, <code>wdfilter</code>, <code>wdnisdrv</code>, <code>wdnissvc</code>, and <code>windefend</code>) should be in their default state. Changing the startup of these services is unsupported and may force you to reimage your system. Example default configurations for <code>WdBoot</code> and <code>WdFilter</code>:</p>
<ul>
<li><code>&lt;Key Path=&quot;SYSTEM\CurrentControlSet\Services\WdBoot&quot;&gt;&lt;KeyValue Value=&quot;0&quot; ValueKind=&quot;DWord&quot; Name=&quot;Start&quot;/&gt;&lt;/Key&gt;</code></li>
<li><code>&lt;Key Path=&quot;SYSTEM\CurrentControlSet\Services\WdFilter&quot;&gt;&lt;KeyValue Value=&quot;0&quot; ValueKind=&quot;DWord&quot; Name=&quot;Start&quot;/&gt;&lt;/Key&gt;</code></li>
</ul>
<p>If Microsoft Defender Antivirus is in passive mode, these drivers are set to manual (<code>0</code>).</p>
</div>
</li>
</ul>
<h2 id="troubleshoot-onboarding-issues-on-windows-server-2016-and-earlier-versions-of-windows-server">Troubleshoot onboarding issues on Windows Server 2016 and earlier versions of Windows Server.</h2>
<p>If you encounter issues while onboarding a server, go through the following verification steps to address possible issues.</p>
<ul>
<li>Ensure Microsoft Monitoring Agent (MMA) is installed and configured to report sensor data to the service</li>
<li>Ensure that the server proxy and Internet connectivity settings are configured properly</li>
<li>See <a href="https://learn.microsoft.com/en-us/defender-endpoint/onboard-server#onboard-windows-server-2016-and-windows-server-2012-r2" data-linktype="relative-path">Onboard Windows Server 2016 and Windows Server 2012 R2</a></li>
</ul>
<p>You might also need to check the following:</p>
<ul>
<li><p>Check that there&#39;s a Microsoft Defender for Endpoint Service running in the <strong>Processes</strong> tab in <strong>Task Manager</strong>. For example:</p>
<p><span class="mx-imgBorder">
<a href="https://learn.microsoft.com/en-us/defender-endpoint/media/atp-task-manager.png#lightbox" data-linktype="relative-path">
<img src="https://learn.microsoft.com/en-us/defender-endpoint/media/atp-task-manager.png" alt="The process view with Microsoft Defender for Endpoint Service running" data-linktype="relative-path">
</a>
</span>
</p>
</li>
<li><p>Check <strong>Event Viewer</strong> &gt; <strong>Applications and Services Logs</strong> &gt; <strong>Operation Manager</strong> to see if there are any errors.</p>
</li>
<li><p>In <strong>Services</strong>, check if the <strong>Microsoft Monitoring Agent</strong> is running on the server. For example,</p>
<p><span class="mx-imgBorder">
<a href="https://learn.microsoft.com/en-us/defender-endpoint/media/atp-services.png#lightbox" data-linktype="relative-path">
<img src="https://learn.microsoft.com/en-us/defender-endpoint/media/atp-services.png" alt="The services" data-linktype="relative-path">
</a>
</span>
</p>
</li>
<li><p>In <strong>Microsoft Monitoring Agent</strong> &gt; <strong>Azure Log Analytics (OMS)</strong>, check the Workspaces and verify that the status is running.</p>
<p><span class="mx-imgBorder">
<a href="https://learn.microsoft.com/en-us/defender-endpoint/media/atp-mma-properties.png#lightbox" data-linktype="relative-path">
<img src="https://learn.microsoft.com/en-us/defender-endpoint/media/atp-mma-properties.png" alt="The Microsoft Monitoring Agent Properties" data-linktype="relative-path">
</a>
</span>
</p>
</li>
<li><p>Check to see that devices are reflected in the <strong>Devices list</strong> in the portal.</p>
</li>
</ul>
<h2 id="confirming-onboarding-of-newly-built-devices">Confirming onboarding of newly built devices</h2>
<p>There may be instances when onboarding is deployed on a newly built device but not completed.</p>
<p>The steps in this article provide guidance for the following scenario:</p>
<ul>
<li>Onboarding package is deployed to newly built devices</li>
<li>Sensor doesn&#39;t start because the Out-of-box experience (OOBE) or first user logon hasn&#39;t been completed</li>
<li>Device is turned off or restarted before the end user performs a first logon</li>
<li>In this scenario, the SENSE service won&#39;t start automatically even though onboarding package was deployed</li>
</ul>
<div class="NOTE">
<p>Note</p>
<p>User Logon after OOBE is no longer required for SENSE service to start on the following or more recent Windows versions:</p>
<ul>
<li>Windows 10 version 1809 or later.</li>
<li>Windows Server 2019 or later.</li>
<li>Azure Stack HCI OS version 23H2 and later.</li>
</ul>
</div>
<p>&lt;a name=&quot;troubleshoot-onboarding-with-microsoft-endpoint-configuration-manager&quot;</p>
<h2 id="troubleshoot-onboarding-with-microsoft-configuration-manager">Troubleshoot onboarding with Microsoft Configuration Manager</h2>
<div class="NOTE">
<p>Note</p>
<p>The following steps are only relevant when using Microsoft Configuration Manager. For more information about onboarding using Microsoft Configuration Manager, see <a href="https://learn.microsoft.com/en-us/intune/configmgr/protect/deploy-use/windows-defender-advanced-threat-protection" data-linktype="absolute-path">Microsoft Defender for Endpoint</a>.</p>
</div>
<ol>
<li><p>Create an application in Microsoft Configuration Manager.</p>
<p><span class="mx-imgBorder">
<a href="https://learn.microsoft.com/en-us/defender-endpoint/media/mecm-1.png#lightbox" data-linktype="relative-path">
<img src="https://learn.microsoft.com/en-us/defender-endpoint/media/mecm-1.png" alt="The Microsoft Configuration Manager configuration-1" data-linktype="relative-path">
</a>
</span>
</p>
</li>
<li><p>Select <strong>Manually specify the application information</strong>.</p>
<p><span class="mx-imgBorder">
<a href="https://learn.microsoft.com/en-us/defender-endpoint/media/mecm-2.png#lightbox" data-linktype="relative-path">
<img src="https://learn.microsoft.com/en-us/defender-endpoint/media/mecm-2.png" alt="The Microsoft Configuration Manager configuration-2" data-linktype="relative-path">
</a>
</span>
</p>
</li>
<li><p>Specify information about the application, then select <strong>Next</strong>.</p>
<p><span class="mx-imgBorder">
<a href="https://learn.microsoft.com/en-us/defender-endpoint/media/mecm-3.png#lightbox" data-linktype="relative-path">
<img src="https://learn.microsoft.com/en-us/defender-endpoint/media/mecm-3.png" alt="The Microsoft Configuration Manager configuration-3" data-linktype="relative-path">
</a>
</span>
</p>
</li>
<li><p>Specify information about the software center, then select <strong>Next</strong>.</p>
<p><span class="mx-imgBorder">
<a href="https://learn.microsoft.com/en-us/defender-endpoint/media/mecm-4.png#lightbox" data-linktype="relative-path">
<img src="https://learn.microsoft.com/en-us/defender-endpoint/media/mecm-4.png" alt="The Microsoft Configuration Manager configuration-4" data-linktype="relative-path">
</a>
</span>
</p>
</li>
<li><p>In <strong>Deployment types</strong> select <strong>Add</strong>.</p>
<p><span class="mx-imgBorder">
<a href="https://learn.microsoft.com/en-us/defender-endpoint/media/mecm-5.png#lightbox" data-linktype="relative-path">
<img src="https://learn.microsoft.com/en-us/defender-endpoint/media/mecm-5.png" alt="The Microsoft Configuration Manager configuration-5" data-linktype="relative-path">
</a>
</span>
</p>
</li>
<li><p>Select <strong>Manually specify the deployment type information</strong>, then select <strong>Next</strong>.</p>
<p><span class="mx-imgBorder">
<a href="https://learn.microsoft.com/en-us/defender-endpoint/media/mecm-6.png#lightbox" data-linktype="relative-path">
<img src="https://learn.microsoft.com/en-us/defender-endpoint/media/mecm-6.png" alt="The Microsoft Configuration Manager configuration-6" data-linktype="relative-path">
</a>
</span>
</p>
</li>
<li><p>Specify information about the deployment type, then select <strong>Next</strong>.</p>
<p><span class="mx-imgBorder">
<a href="https://learn.microsoft.com/en-us/defender-endpoint/media/mecm-7.png#lightbox" data-linktype="relative-path">
<img src="https://learn.microsoft.com/en-us/defender-endpoint/media/mecm-7.png" alt="The Microsoft Configuration Manager configuration-7" data-linktype="relative-path">
</a>
</span>
</p>
</li>
<li><p>In <strong>Content</strong> &gt; <strong>Installation program</strong> specify the command: <code>net start sense</code>.</p>
<p><span class="mx-imgBorder">
<a href="https://learn.microsoft.com/en-us/defender-endpoint/media/mecm-8.png#lightbox" data-linktype="relative-path">
<img src="https://learn.microsoft.com/en-us/defender-endpoint/media/mecm-8.png" alt="The Microsoft Configuration Manager configuration-8" data-linktype="relative-path">
</a>
</span>
</p>
</li>
<li><p>In <strong>Detection method</strong>, select <strong>Configure rules to detect the presence of this deployment type</strong>, then select <strong>Add Clause</strong>.</p>
<p><span class="mx-imgBorder">
<a href="https://learn.microsoft.com/en-us/defender-endpoint/media/mecm-9.png#lightbox" data-linktype="relative-path">
<img src="https://learn.microsoft.com/en-us/defender-endpoint/media/mecm-9.png" alt="The Microsoft Configuration Manager configuration-9" data-linktype="relative-path">
</a>
</span>
</p>
</li>
<li><p>Specify the following detection rule details, then select <strong>OK</strong>:</p>
<p><span class="mx-imgBorder">
<a href="https://learn.microsoft.com/en-us/defender-endpoint/media/mecm-10.png#lightbox" data-linktype="relative-path">
<img src="https://learn.microsoft.com/en-us/defender-endpoint/media/mecm-10.png" alt="The Microsoft Configuration Manager configuration-10" data-linktype="relative-path">
</a>
</span>
</p>
</li>
<li><p>In <strong>Detection method</strong> select <strong>Next</strong>.</p>
<p><span class="mx-imgBorder">
<a href="https://learn.microsoft.com/en-us/defender-endpoint/media/mecm-11.png#lightbox" data-linktype="relative-path">
<img src="https://learn.microsoft.com/en-us/defender-endpoint/media/mecm-11.png" alt="The Microsoft Configuration Manager configuration-11" data-linktype="relative-path">
</a>
</span>
</p>
</li>
<li><p>In <strong>User Experience</strong>, specify the following information, then select <strong>Next</strong>:</p>
<p><span class="mx-imgBorder">
<a href="https://learn.microsoft.com/en-us/defender-endpoint/media/mecm-12.png#lightbox" data-linktype="relative-path">
<img src="https://learn.microsoft.com/en-us/defender-endpoint/media/mecm-12.png" alt="The Microsoft Configuration Manager configuration-12" data-linktype="relative-path">
</a>
</span>
</p>
</li>
<li><p>In <strong>Requirements</strong>, select <strong>Next</strong>.</p>
<p><span class="mx-imgBorder">
<a href="https://learn.microsoft.com/en-us/defender-endpoint/media/mecm-13.png#lightbox" data-linktype="relative-path">
<img src="https://learn.microsoft.com/en-us/defender-endpoint/media/mecm-13.png" alt="The Microsoft Configuration Manager configuration-13" data-linktype="relative-path">
</a>
</span>
</p>
</li>
<li><p>In <strong>Dependencies</strong>, select <strong>Next</strong>.</p>
<p><span class="mx-imgBorder">
<a href="https://learn.microsoft.com/en-us/defender-endpoint/media/mecm-14.png#lightbox" data-linktype="relative-path">
<img src="https://learn.microsoft.com/en-us/defender-endpoint/media/mecm-14.png" alt="The Microsoft Configuration Manager configuration-14" data-linktype="relative-path">
</a>
</span>
</p>
</li>
<li><p>In <strong>Summary</strong>, select <strong>Next</strong>.</p>
<p><span class="mx-imgBorder">
<a href="https://learn.microsoft.com/en-us/defender-endpoint/media/mecm-15.png#lightbox" data-linktype="relative-path">
<img src="https://learn.microsoft.com/en-us/defender-endpoint/media/mecm-15.png" alt="The Microsoft Configuration Manager configuration-15" data-linktype="relative-path">
</a>
</span>
</p>
</li>
<li><p>In <strong>Completion</strong>, select <strong>Close</strong>.</p>
<p><span class="mx-imgBorder">
<a href="https://learn.microsoft.com/en-us/defender-endpoint/media/mecm-16.png#lightbox" data-linktype="relative-path">
<img src="https://learn.microsoft.com/en-us/defender-endpoint/media/mecm-16.png" alt="The Microsoft Configuration Manager configuration-16" data-linktype="relative-path">
</a>
</span>
</p>
</li>
<li><p>In <strong>Deployment types</strong>, select <strong>Next</strong>.</p>
<p><span class="mx-imgBorder">
<a href="https://learn.microsoft.com/en-us/defender-endpoint/media/mecm-17.png#lightbox" data-linktype="relative-path">
<img src="https://learn.microsoft.com/en-us/defender-endpoint/media/mecm-17.png" alt="The Microsoft Configuration Manager configuration-17" data-linktype="relative-path">
</a>
</span>
</p>
</li>
<li><p>In <strong>Summary</strong>, select <strong>Next</strong>.</p>
<p><span class="mx-imgBorder">
<a href="https://learn.microsoft.com/en-us/defender-endpoint/media/mecm-18.png#lightbox" data-linktype="relative-path">
<img src="https://learn.microsoft.com/en-us/defender-endpoint/media/mecm-18.png" alt="The Microsoft Configuration Manager configuration-18" data-linktype="relative-path">
</a>
</span>
</p>
<p>The status is then displayed:
<span class="mx-imgBorder">
<a href="https://learn.microsoft.com/en-us/defender-endpoint/media/mecm-19.png#lightbox" data-linktype="relative-path">
<img src="https://learn.microsoft.com/en-us/defender-endpoint/media/mecm-19.png" alt="The Microsoft Configuration Manager configuration-19" data-linktype="relative-path">
</a>
</span>
</p>
</li>
<li><p>In <strong>Completion</strong>, select <strong>Close</strong>.</p>
<p><span class="mx-imgBorder">
<a href="https://learn.microsoft.com/en-us/defender-endpoint/media/mecm-20.png#lightbox" data-linktype="relative-path">
<img src="https://learn.microsoft.com/en-us/defender-endpoint/media/mecm-20.png" alt="The Microsoft Configuration Manager configuration-20" data-linktype="relative-path">
</a>
</span>
</p>
</li>
<li><p>You can now deploy the application by right-clicking the app and selecting <strong>Deploy</strong>.</p>
<p><span class="mx-imgBorder">
<a href="https://learn.microsoft.com/en-us/defender-endpoint/media/mecm-21.png#lightbox" data-linktype="relative-path">
<img src="https://learn.microsoft.com/en-us/defender-endpoint/media/mecm-21.png" alt="The Microsoft Configuration Manager configuration-21" data-linktype="relative-path">
</a>
</span>
</p>
</li>
<li><p>In <strong>General</strong> select <strong>Automatically distribute content for dependencies</strong> and <strong>Browse</strong>.</p>
<p><span class="mx-imgBorder">
<a href="https://learn.microsoft.com/en-us/defender-endpoint/media/mecm-22.png#lightbox" data-linktype="relative-path">
<img src="https://learn.microsoft.com/en-us/defender-endpoint/media/mecm-22.png" alt="The Microsoft Configuration Manager configuration-22" data-linktype="relative-path">
</a>
</span>
</p>
</li>
<li><p>In <strong>Content</strong> select <strong>Next</strong>.
<span class="mx-imgBorder">
<a href="https://learn.microsoft.com/en-us/defender-endpoint/media/mecm-23.png#lightbox" data-linktype="relative-path">
<img src="https://learn.microsoft.com/en-us/defender-endpoint/media/mecm-23.png" alt="The Microsoft Configuration Manager configuration-23" data-linktype="relative-path">
</a>
</span>
</p>
</li>
<li><p>In <strong>Deployment settings</strong>, select <strong>Next</strong>.</p>
<p><span class="mx-imgBorder">
<a href="https://learn.microsoft.com/en-us/defender-endpoint/media/mecm-24.png#lightbox" data-linktype="relative-path">
<img src="https://learn.microsoft.com/en-us/defender-endpoint/media/mecm-24.png" alt="The Microsoft Configuration Manager configuration-24" data-linktype="relative-path">
</a>
</span>
</p>
</li>
<li><p>In <strong>Scheduling</strong> select <strong>As soon as possible after the available time</strong>, then select <strong>Next</strong>.</p>
<p><span class="mx-imgBorder">
<a href="https://learn.microsoft.com/en-us/defender-endpoint/media/mecm-25.png#lightbox" data-linktype="relative-path">
<img src="https://learn.microsoft.com/en-us/defender-endpoint/media/mecm-25.png" alt="The Microsoft Configuration Manager configuration-25" data-linktype="relative-path">
</a>
</span>
</p>
</li>
<li><p>In <strong>User experience</strong>, select <strong>Commit changes at deadline or during a maintenance window (requires restarts)</strong>, then select <strong>Next</strong>.
<span class="mx-imgBorder">
<a href="https://learn.microsoft.com/en-us/defender-endpoint/media/mecm-26.png#lightbox" data-linktype="relative-path">
<img src="https://learn.microsoft.com/en-us/defender-endpoint/media/mecm-26.png" alt="The Microsoft Configuration Manager configuration-26" data-linktype="relative-path">
</a>
</span>
</p>
</li>
<li><p>In <strong>Alerts</strong> select <strong>Next</strong>.</p>
<p><span class="mx-imgBorder">
<a href="https://learn.microsoft.com/en-us/defender-endpoint/media/mecm-27.png#lightbox" data-linktype="relative-path">
<img src="https://learn.microsoft.com/en-us/defender-endpoint/media/mecm-27.png" alt="The Microsoft Configuration Manager configuration-27" data-linktype="relative-path">
</a>
</span>
</p>
</li>
<li><p>In <strong>Summary</strong>, select <strong>Next</strong>.
<span class="mx-imgBorder">
<a href="https://learn.microsoft.com/en-us/defender-endpoint/media/mecm-28.png#lightbox" data-linktype="relative-path">
<img src="https://learn.microsoft.com/en-us/defender-endpoint/media/mecm-28.png" alt="The Microsoft Configuration Manager configuration-28" data-linktype="relative-path">
</a>
</span>
</p>
<p>The status is then displayed
<span class="mx-imgBorder">
<a href="https://learn.microsoft.com/en-us/defender-endpoint/media/mecm-29.png#lightbox" data-linktype="relative-path">
<img src="https://learn.microsoft.com/en-us/defender-endpoint/media/mecm-29.png" alt="The Microsoft Configuration Manager configuration-29" data-linktype="relative-path">
</a>
</span>
</p>
</li>
<li><p>In <strong>Completion</strong>, select <strong>Close</strong>.</p>
<p><span class="mx-imgBorder">
<a href="https://learn.microsoft.com/en-us/defender-endpoint/media/mecm-30.png#lightbox" data-linktype="relative-path">
<img src="https://learn.microsoft.com/en-us/defender-endpoint/media/mecm-30.png" alt="The Microsoft Configuration Manager configuration-30" data-linktype="relative-path">
</a>
</span>
</p>
</li>
</ol>
<h2 id="related-topics">Related topics</h2>
<ul>
<li><a href="https://learn.microsoft.com/en-us/defender-endpoint/troubleshoot-mdatp" data-linktype="relative-path">Troubleshoot Microsoft Defender for Endpoint</a></li>
<li><a href="https://learn.microsoft.com/en-us/defender-endpoint/onboard-configure" data-linktype="relative-path">Onboard devices</a></li>
<li><a href="https://learn.microsoft.com/en-us/defender-endpoint/configure-proxy-internet" data-linktype="relative-path">Configure device proxy and Internet connectivity settings</a></li>
</ul>
</span>
