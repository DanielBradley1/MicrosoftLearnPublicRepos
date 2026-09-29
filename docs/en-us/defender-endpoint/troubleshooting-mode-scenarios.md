<!-- Source: https://learn.microsoft.com/en-us/defender-endpoint/troubleshooting-mode-scenarios -->
<!-- Sitemap-Last-Modified: 2026-09-08 -->

# Troubleshooting mode scenarios in Microsoft Defender for Endpoint

Troubleshooting mode in Microsoft Defender for Endpoint lets local administrators temporarily test certain policy-managed Microsoft Defender Antivirus settings on individual Windows devices. Use the scenarios in this article to determine whether antivirus scanning, exclusions, attack surface reduction \(ASR\) rules, or network protection contribute to an issue.

Before testing a scenario, review the requirements and [enable troubleshooting mode in the Microsoft Defender portal](https://learn.microsoft.com/en-us/defender-endpoint/troubleshooting-mode-enable#enable-troubleshooting-mode-in-the-microsoft-defender-portal). Changes made during troubleshooting mode are temporary. When troubleshooting mode expires, policy-managed settings return to their previous values.

For Microsoft Defender Antivirus performance investigations, start with the [Microsoft Defender Antivirus performance analyzer](https://learn.microsoft.com/en-us/defender-endpoint/tune-performance-defender-antivirus).

Tip

- If tamper protection blocks a temporary setting change, follow the [PowerShell procedure to temporarily disable tamper protection and verify that it's off](https://learn.microsoft.com/en-us/defender-endpoint/troubleshooting-mode-enable#temporarily-disable-tamper-protection-using-powershell).

## Scenario 1: Troubleshoot a blocked application installation

Use this scenario when Microsoft Defender Antivirus blocks an application installation that you believe is safe.

1. [Capture process logs using Process Monitor](https://learn.microsoft.com/en-us/defender-endpoint/troubleshoot-av-performance-issues-with-procmon#capture-process-logs-using-process-monitor) and review the guidance for [troubleshooting performance issues related to real-time protection](https://learn.microsoft.com/en-us/defender-endpoint/troubleshoot-performance-issues).
2. If the investigation indicates that real-time protection is blocking the installation, enable troubleshooting mode and [temporarily disable tamper protection](https://learn.microsoft.com/en-us/defender-endpoint/troubleshooting-mode-enable#temporarily-disable-tamper-protection).
3. Run the following command in an elevated PowerShell session to temporarily disable real-time protection:

   ```powershell
   Set-MpPreference -DisableRealtimeMonitoring $true
   ```

4. Retry the installation. Only test applications that your organization has independently validated as safe.
5. If the installation succeeds only while real-time protection is off, use the diagnostic results to determine whether you need a narrowly scoped [Microsoft Defender Antivirus exclusion](https://learn.microsoft.com/en-us/defender-endpoint/microsoft-defender-antivirus-exclusions-configure).
6. To restore real-time protection immediately instead of waiting for troubleshooting mode to expire, run the following command in an elevated PowerShell session:

   ```powershell
   Set-MpPreference -DisableRealtimeMonitoring $false
   ```

## Scenario 2: Investigate high CPU usage by MsMpEng.exe

Use this scenario when the Microsoft Defender Antivirus process `MsMpEng.exe` uses high CPU during a scan or while an application is running.

1. Use the [Microsoft Defender Antivirus performance analyzer](https://learn.microsoft.com/en-us/defender-endpoint/tune-performance-defender-antivirus#run-the-microsoft-defender-antivirus-performance-analyzer) to identify the files, file extensions, and processes that contribute most to scan time.
2. If you need more process-level detail, [capture process logs using Process Monitor](https://learn.microsoft.com/en-us/defender-endpoint/troubleshoot-av-performance-issues-with-procmon#capture-process-logs-using-process-monitor).
3. After you identify the cause, [enable troubleshooting mode](https://learn.microsoft.com/en-us/defender-endpoint/troubleshooting-mode-enable#enable-troubleshooting-mode-in-the-microsoft-defender-portal) and test the smallest appropriate [file, folder, file type, or process exclusion](https://learn.microsoft.com/en-us/defender-endpoint/microsoft-defender-antivirus-exclusions-overview). To create the temporary exclusion without overwriting existing exclusions, follow [Configure Microsoft Defender Antivirus exclusions in PowerShell](https://learn.microsoft.com/en-us/defender-endpoint/microsoft-defender-antivirus-exclusions-configure#configure-microsoft-defender-antivirus-exclusions-in-powershell).
4. Only keep an exclusion if testing confirms that it's necessary. Before deploying an exclusion broadly, review [Common mistakes to avoid when defining exclusions](https://learn.microsoft.com/en-us/defender-endpoint/defender-endpoint-exclusions-common-mistakes).

## Scenario 3: Investigate slow application performance

Use this scenario when an application takes longer than expected to open files, save data, compile code, or complete another file-intensive action.

1. Use the [Microsoft Defender Antivirus performance analyzer](https://learn.microsoft.com/en-us/defender-endpoint/tune-performance-defender-antivirus#record-and-analyze-events-with-the-microsoft-defender-antivirus-performance-analyzer) to identify the affected paths and processes.
2. If the results suggest that real-time scanning contributes to the delay, [enable troubleshooting mode](https://learn.microsoft.com/en-us/defender-endpoint/troubleshooting-mode-enable#enable-troubleshooting-mode-in-the-microsoft-defender-portal) and [temporarily disable tamper protection](https://learn.microsoft.com/en-us/defender-endpoint/troubleshooting-mode-enable#temporarily-disable-tamper-protection).
3. Run the following command in an elevated PowerShell session to temporarily disable real-time protection:

   ```powershell
   Set-MpPreference -DisableRealtimeMonitoring $true
   ```

4. Repeat the affected application action.
5. If performance improves, use the analyzer results to evaluate a narrow exclusion instead of leaving real-time protection disabled. For configuration guidance, see [Configure Microsoft Defender Antivirus exclusions](https://learn.microsoft.com/en-us/defender-endpoint/microsoft-defender-antivirus-exclusions-configure).
6. To restore real-time protection immediately instead of waiting for troubleshooting mode to expire, run the following command in an elevated PowerShell session:

   ```powershell
   Set-MpPreference -DisableRealtimeMonitoring $false
   ```

## Scenario 4: Investigate an Office add-in blocked by an ASR rule

Use this scenario when the [Block all Office applications from creating child processes](https://learn.microsoft.com/en-us/defender-endpoint/attack-surface-reduction-rules-reference#block-all-office-applications-from-creating-child-processes) ASR rule prevents a trusted Office add-in from working.

1. [Enable troubleshooting mode](https://learn.microsoft.com/en-us/defender-endpoint/troubleshooting-mode-enable#enable-troubleshooting-mode-in-the-microsoft-defender-portal).
2. Use [Configure ASR rules in PowerShell](https://learn.microsoft.com/en-us/defender-endpoint/attack-surface-reduction-rules-configure#configure-asr-rules-in-powershell) to temporarily set the affected rule to `Disabled`.
3. Test the add-in again to determine whether the rule causes the issue.
4. If disabling the rule resolves the issue, don't leave the rule disabled. Evaluate whether `Warn` mode, `Audit` mode, or a scoped exclusion meets your organization's security and business requirements. For planning and testing guidance, see [Operationalize attack surface reduction rules](https://learn.microsoft.com/en-us/defender-endpoint/attack-surface-reduction-rules-deployment-operationalize).

## Scenario 5: Investigate a domain blocked by network protection

Use this scenario when network protection blocks access to a domain that your organization expects to allow.

1. [Review network protection events in the Microsoft Defender portal](https://learn.microsoft.com/en-us/defender-endpoint/network-protection#review-network-protection-events-in-the-microsoft-defender-portal) or [Windows Event Viewer](https://learn.microsoft.com/en-us/defender-endpoint/network-protection#review-network-protection-events-in-windows-event-viewer) to confirm that network protection generated the block.
2. [Enable troubleshooting mode](https://learn.microsoft.com/en-us/defender-endpoint/troubleshooting-mode-enable#enable-troubleshooting-mode-in-the-microsoft-defender-portal).
3. Follow [Configure network protection by using PowerShell](https://learn.microsoft.com/en-us/defender-endpoint/enable-network-protection#configure-network-protection-by-using-powershell) to temporarily set network protection to `Disabled`.
4. Test access to the domain again.
5. If disabling network protection resolves the issue, turn network protection back on and follow [Troubleshoot network protection](https://learn.microsoft.com/en-us/defender-endpoint/troubleshoot-np) to evaluate audit events, report an incorrect detection, or configure an appropriate exclusion.

## Related content

- [Enable and use troubleshooting mode in Microsoft Defender for Endpoint](https://learn.microsoft.com/en-us/defender-endpoint/troubleshooting-mode-enable)
- [Tamper protection overview](https://learn.microsoft.com/en-us/defender-endpoint/tamper-protection-overview)
- [**Set-MpPreference**](https://learn.microsoft.com/en-us/powershell/module/defender/set-mppreference)
- [Configure Microsoft Defender Antivirus exclusions](https://learn.microsoft.com/en-us/defender-endpoint/microsoft-defender-antivirus-exclusions-configure)
- [Configure attack surface reduction rules](https://learn.microsoft.com/en-us/defender-endpoint/attack-surface-reduction-rules-configure)
- [Configure network protection](https://learn.microsoft.com/en-us/defender-endpoint/enable-network-protection)
- [Get an overview of Microsoft Defender for Endpoint](https://learn.microsoft.com/en-us/defender-endpoint/microsoft-defender-endpoint)
