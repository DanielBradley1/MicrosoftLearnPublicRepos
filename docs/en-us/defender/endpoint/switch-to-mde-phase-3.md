<!-- Source: https://learn.microsoft.com/en-us/defender-endpoint/switch-to-mde-phase-3 -->
<!-- Sitemap-Last-Modified: 2026-07-29 -->

# Migrate to Microsoft Defender for Endpoint - Phase 3: Onboard

| [![Diagram of the migration phases with Phase 1 Prepare highlighted.](https://learn.microsoft.com/en-us/defender-endpoint/media/phase-diagrams/prepare.png#lightbox)](https://learn.microsoft.com/en-us/defender-endpoint/switch-to-mde-phase-1)<br><br>  <br>[Phase 1: Prepare](https://learn.microsoft.com/en-us/defender-endpoint/switch-to-mde-phase-1) | [![Diagram of the migration phases with Phase 2 Set up highlighted.](https://learn.microsoft.com/en-us/defender-endpoint/media/phase-diagrams/setup.png#lightbox)](https://learn.microsoft.com/en-us/defender-endpoint/switch-to-mde-phase-2)<br><br>  <br>[Phase 2: Set up](https://learn.microsoft.com/en-us/defender-endpoint/switch-to-mde-phase-2) | ![Diagram of the migration phases with Phase 3 Onboard highlighted as the current step.](https://learn.microsoft.com/en-us/defender-endpoint/media/phase-diagrams/onboard.png#lightbox)  <br>Phase 3: Onboard |
| --- | --- | --- |
|  |  | *You're here!* |

**Welcome to Phase 3 of [migrating to Defender for Endpoint](https://learn.microsoft.com/en-us/defender-endpoint/switch-to-mde-overview#the-migration-process)**. Before you begin, make sure you've completed [Phase 1: Prepare](https://learn.microsoft.com/en-us/defender-endpoint/switch-to-mde-phase-1) and [Phase 2: Set up](https://learn.microsoft.com/en-us/defender-endpoint/switch-to-mde-phase-2). This migration phase includes the following steps:

1. Onboard devices to Defender for Endpoint.
2. Run a detection test.
3. Confirm that Microsoft Defender Antivirus is in passive mode on your endpoints.
4. Get updates for Microsoft Defender Antivirus.
5. Uninstall your non-Microsoft solution.
6. Make sure Defender for Endpoint is working correctly.

Important

If you want to run multiple security solutions side by side, see [Considerations for performance, configuration, and support](https://learn.microsoft.com/en-us/defender-endpoint/mde-side-by-side).

You might have already configured mutual security exclusions for devices onboarded to Microsoft Defender for Endpoint. If you still need to set mutual exclusions to avoid conflicts, see [Add Microsoft Defender for Endpoint to the exclusion list for your existing solution](https://learn.microsoft.com/en-us/defender-endpoint/switch-to-mde-phase-2#step-2-add-microsoft-defender-for-endpoint-to-the-exclusion-list-for-your-existing-solution).

## Step 1: Onboard devices to Microsoft Defender for Endpoint

Follow these steps to start onboarding devices to Microsoft Defender for Endpoint.

1. Go to the [Microsoft Defender portal](https://security.microsoft.com) and sign in.
2. Choose **Settings** > **Endpoints** > **Onboarding** \(under **Device management**\).
3. In the **Select operating system to start onboarding process** list, select an operating system.
4. Under **Deployment method**, select an option. Follow the links and prompts to onboard your organization's devices. Need help? See [Onboarding methods](#onboarding-methods) \(in this article\).

Note

If something goes wrong while onboarding, see [Troubleshoot Microsoft Defender for Endpoint onboarding issues](https://learn.microsoft.com/en-us/defender-endpoint/troubleshoot-onboarding). That article describes how to resolve onboarding issues and common errors on endpoints.

### Onboarding methods

Deployment methods vary, depending on operating system and preferred methods. The following table lists resources to help you onboard to Defender for Endpoint:

| Operating systems | Methods |
| --- | --- |
| Windows 10 or later  <br>  <br>Windows Server 2016 or later  <br>  <br>Windows Server, version 1803 or later  <br>  <br>Windows Server 2012 R2 | [Microsoft Intune or Mobile Device Management](https://learn.microsoft.com/en-us/defender-endpoint/configure-endpoints-mdm)  <br>  <br>[Microsoft Configuration Manager](https://learn.microsoft.com/en-us/defender-endpoint/configure-endpoints-sccm)  <br>  <br>[Group Policy](https://learn.microsoft.com/en-us/defender-endpoint/configure-endpoints-gp)  <br>  <br>[VDI scripts](https://learn.microsoft.com/en-us/defender-endpoint/configure-endpoints-vdi)  <br>  <br>[Local script \(up to 10 devices\)](https://learn.microsoft.com/en-us/defender-endpoint/configure-endpoints-script)  <br>The local script method is suitable for a proof of concept but shouldn't be used for production deployment. For a production deployment, we recommend using Group Policy, Microsoft Configuration Manager, or Intune. |
| Windows Server 2008 R2 SP1 | [Microsoft Monitoring Agent \(MMA\)](https://learn.microsoft.com/en-us/defender-endpoint/onboard-downlevel#install-and-configure-microsoft-monitoring-agent-windows-81-only) or [Microsoft Defender for Cloud](https://learn.microsoft.com/en-us/azure/security-center/security-center-wdatp)  <br>The Microsoft Monitoring Agent is now Azure Log Analytics agent. To learn more, see [Log Analytics agent overview](https://learn.microsoft.com/en-us/azure/azure-monitor/platform/log-analytics-agent). |
| Windows 8.1 Enterprise  <br>  <br>Windows 8.1 Pro  <br>  <br>Windows 7 SP1 Pro  <br>  <br>Windows 7 SP1 | [Microsoft Monitoring Agent \(MMA\)](https://learn.microsoft.com/en-us/defender-endpoint/onboard-downlevel)  <br>The Microsoft Monitoring Agent is now Azure Log Analytics agent. To learn more, see [Log Analytics agent overview](https://learn.microsoft.com/en-us/azure/azure-monitor/platform/log-analytics-agent). |
| **Windows servers  <br>  <br>Linux servers** | [Integration with Microsoft Defender for Cloud](https://learn.microsoft.com/en-us/defender-endpoint/azure-server-integration) |
| macOS | [Local script](https://learn.microsoft.com/en-us/defender-endpoint/mac-install-manually)  <br>[Microsoft Intune](https://learn.microsoft.com/en-us/defender-endpoint/mac-install-with-intune)  <br>[JAMF Pro](https://learn.microsoft.com/en-us/defender-endpoint/mac-install-with-jamf)  <br>[Mobile Device Management](https://learn.microsoft.com/en-us/defender-endpoint/mac-install-with-other-mdm) |
| Linux | [Local script](https://learn.microsoft.com/en-us/defender-endpoint/linux-install-manually)  <br>[Puppet](https://learn.microsoft.com/en-us/defender-endpoint/linux-install-with-puppet)  <br>[Ansible](https://learn.microsoft.com/en-us/defender-endpoint/linux-install-with-ansible)  <br>[Chef](https://learn.microsoft.com/en-us/defender-endpoint/linux-deploy-defender-for-endpoint-with-chef) |
| Android | [Microsoft Intune](https://learn.microsoft.com/en-us/intune/intune-service/protect/microsoft-defender-deploy-android) |
| iOS | [Microsoft Intune](https://learn.microsoft.com/en-us/defender-endpoint/ios-install)  <br>[Mobile Application Manager](https://learn.microsoft.com/en-us/defender-endpoint/ios-install-unmanaged) |

Note

If you're using Windows Server 2016 or Windows Server 2012 R2, see [Onboard Windows Server 2012 R2 and Windows Server 2016 to Microsoft Defender for Endpoint](https://learn.microsoft.com/en-us/defender-endpoint/onboard-server).

Important

The standalone versions of Defender for Endpoint Plan 1 and Plan 2 do not include server licenses. To onboard servers, you'll need an additional license, such as [Microsoft Defender for Servers Plan 1 or Plan 2](https://learn.microsoft.com/en-us/azure/defender-for-cloud/plan-defender-for-servers-select-plan). To learn more, see [Server plans](https://learn.microsoft.com/en-us/defender-endpoint/onboard-server#server-plans).

## Step 2: Run a detection test

To verify that your onboarded devices are properly connected to Defender for Endpoint, you can run a detection test. Before running a detection test on macOS or Linux, make sure the device meets the system requirements for [macOS](https://learn.microsoft.com/en-us/defender-endpoint/microsoft-defender-endpoint-mac) or [Linux](https://learn.microsoft.com/en-us/defender-endpoint/mde-linux-prerequisites).

| Operating system | Guidance |
| --- | --- |
| Windows 10 or later  <br>  <br>Windows Server 2012 R2 and later  <br>  <br>  <br>Windows Server, version 1803, or later  <br>  <br> | See [Run a detection test](https://learn.microsoft.com/en-us/defender-endpoint/run-detection-test). |
| macOS \(see [System requirements](https://learn.microsoft.com/en-us/defender-endpoint/microsoft-defender-endpoint-mac)\) | Download and use the [DIY detection test app for macOS](https://aka.ms/mdatpmacosdiy). Also see [Run the connectivity test](https://learn.microsoft.com/en-us/defender-endpoint/troubleshoot-cloud-connect-mdemac#run-the-connectivity-test). |
| Linux \(see [System requirements](https://learn.microsoft.com/en-us/defender-endpoint/mde-linux-prerequisites)\) | 1. Run the following command, and look for a result of **1**: `mdatp health --field real_time_protection_enabled`.  <br>  <br>2. Open a Terminal window, and run the following command: `curl -o ~/Downloads/eicar.com.txt https://www.eicar.org/download/eicar.com.txt`.  <br>  <br>3. Run the following command to list any detected threats: `mdatp threat list`.  <br>  <br>For more information, see [Defender for Endpoint on Linux](https://learn.microsoft.com/en-us/defender-endpoint/microsoft-defender-endpoint-linux). |

## Step 3: Confirm that Microsoft Defender Antivirus is in passive mode on your endpoints

Now that your endpoints have been onboarded to Defender for Endpoint, your next step is to make sure Microsoft Defender Antivirus is running in passive mode by using PowerShell.

1. On a Windows device, open Windows PowerShell as an administrator.
2. Run the following PowerShell cmdlet: `Get-MpComputerStatus|select AMRunningMode`.
3. Review the results. You should see **Passive mode**.

Note

To learn more about passive mode and active mode, see [More details about Microsoft Defender Antivirus states](https://learn.microsoft.com/en-us/defender-endpoint/microsoft-defender-antivirus-compatibility#more-details-about-microsoft-defender-antivirus-states).

### Set Microsoft Defender Antivirus on Windows Server to passive mode manually

The **ForceDefenderPassiveMode** registry value controls whether Microsoft Defender Antivirus stays in passive mode on supported Windows Server versions. To set this value on Windows Server 2019 and later, Windows Server, version 1803 or later and Azure Stack HCI OS, version 23H2 and later, follow these steps:

1. Open Registry Editor, and then navigate to `Computer\HKEY_LOCAL_MACHINE\SOFTWARE\Policies\Microsoft\Windows Advanced Threat Protection`.
2. Edit \(or create\) a DWORD entry called **ForceDefenderPassiveMode**, and specify the following settings:

   - Set the DWORD's value to **1**.
   - Under **Base**, select **Hexadecimal**.

Note

You can use other methods to set the registry key, such as the following:

- [Group Policy Preference](https://learn.microsoft.com/en-us/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/dn581922\(v=ws.11\))
- [Local Group Policy Object tool](https://learn.microsoft.com/en-us/windows/security/operating-system-security/device-management/windows-security-configuration-framework/security-compliance-toolkit-10#what-is-the-local-group-policy-object-lgpo-tool)
- [A package in Configuration Manager](https://learn.microsoft.com/en-us/intune/configmgr/apps/deploy-use/packages-and-programs)

### Start Microsoft Defender Antivirus on Windows Server 2016

If you're using Windows Server 2016, you might need to start Microsoft Defender Antivirus manually by doing the following steps:

1. In an elevated Command Prompt \(a Command Prompt window you opened by selecting **Run as administrator**\), run the following commands:

   Tip

   The first command changes the directory to the latest version of <antimalware platform version> in `%ProgramData%\Microsoft\Windows Defender\Platform\<antimalware platform version>`. If that path doesn't exist, it goes to `%ProgramFiles%\Microsoft Defender`.

   Run the following batch commands to switch to the latest Windows Defender platform folder and then enable Windows Defender:

   ```dos
   (set "_done=" & if exist "%ProgramData%\Microsoft\Windows Defender\Platform\" (for /f "delims=" %d in ('dir "%ProgramData%\Microsoft\Windows Defender\Platform" /ad /b /o:-n 2^>nul') do if not defined _done (cd /d "%ProgramData%\Microsoft\Windows Defender\Platform\%d" & set _done=1)) else (cd /d "%ProgramFiles%\Windows Defender")) >nul 2>&1

   MpCmdRun.exe -WdEnable
   ```

2. Restart the device.

## Step 4: Get updates for Microsoft Defender Antivirus

Keep Microsoft Defender Antivirus up to date so your devices can protect against new malware and attack methods. Updates are important even when Microsoft Defender Antivirus runs in passive mode. For more information, see [Microsoft Defender Antivirus compatibility](https://learn.microsoft.com/en-us/defender-endpoint/microsoft-defender-antivirus-compatibility).

There are two types of updates related to keeping Microsoft Defender Antivirus up to date:

- Security intelligence updates
- Product updates

To get your updates, follow the guidance in [Manage Microsoft Defender Antivirus updates and apply baselines](https://learn.microsoft.com/en-us/defender-endpoint/microsoft-defender-antivirus-updates).

## Step 5: Uninstall your non-Microsoft solution

Important

If, for some reason, Microsoft Defender Antivirus does not go into active mode after you uninstall your non-Microsoft antivirus/antimalware solution, see [Microsoft Defender Antivirus seems to be stuck in passive mode](https://learn.microsoft.com/en-us/defender-endpoint/switch-to-mde-troubleshooting#microsoft-defender-antivirus-seems-to-be-stuck-in-passive-mode).

If, at this point you have onboarded your organization's devices to Defender for Endpoint, and Microsoft Defender Antivirus is installed and enabled, then your next step is to uninstall your non-Microsoft antivirus, antimalware, and endpoint protection solution. When you uninstall your non-Microsoft solution, Microsoft Defender Antivirus changes from passive mode to active mode. In most cases, this happens automatically.

You can monitor the state of Microsoft Defender Antivirus at scale from the Defender XDR Portal using the [Device Health Report](https://security.microsoft.com/devicehealth?viewid=oldavhealthreport). This report highlights the state of Microsoft Defender Antivirus on devices onboarded to Defender for Endpoint, helping you to track current antivirus mode, engine version and various other details.

Important

If, for some reason, Microsoft Defender Antivirus does not go into active mode after you have uninstalled your non-Microsoft antivirus/antimalware solution, see [Microsoft Defender Antivirus seems to be stuck in passive mode](https://learn.microsoft.com/en-us/defender-endpoint/switch-to-mde-troubleshooting#microsoft-defender-antivirus-seems-to-be-stuck-in-passive-mode).

To get help with uninstalling your non-Microsoft solution, contact their technical support team.

## Step 6: Make sure Defender for Endpoint is working correctly

Now that you have onboarded to Defender for Endpoint, and you have uninstalled your former non-Microsoft solution, your next step is to make sure that Defender for Endpoint working correctly.

1. Go to the [Microsoft Defender portal](https://security.microsoft.com) and sign in.
2. In the navigation pane, choose **Endpoints** > **Device inventory**. There, you're able to see protection status for devices.

To learn more, see [Device inventory](https://learn.microsoft.com/en-us/defender-endpoint/machines-view-overview).

## Next steps

**Congratulations**! You have completed your [migration to Defender for Endpoint](https://learn.microsoft.com/en-us/defender-endpoint/switch-to-mde-overview#the-migration-process)!

- [Configure your Defender for Endpoint settings](https://learn.microsoft.com/en-us/defender-endpoint/preferences-setup).
