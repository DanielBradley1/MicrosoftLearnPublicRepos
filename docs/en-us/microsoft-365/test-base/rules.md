<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/test-base/rules?view=o365-worldwide -->
<!-- Sitemap-Last-Modified: 2024-03-06 -->

# Application/Test rules

Important

**Test Base for Microsoft 365 will transition to end-of-life \(EOL\) on May 31, 2024.** We're committed to working closely with each customer to provide support and guidance to make the transition as smooth as possible. If you have any questions, concerns, or need assistance, [submit a support request](https://aka.ms/TestBaseSupport).

All applications or tests in Test Base need to comply with the following rules:

## Test Base folders

The following folders are used by the Test Base infrastructure:

- %SYSTEMDRIVE%\\USL
- %SYSTEMDRIVE%\\EtlExport
- %SYSTEMDRIVE%\\Ffmpeg
- %SYSTEMDRIVE%\\Monitoring
- %SYSTEMDRIVE%\\powershell-yaml
- %SYSTEMDRIVE%\\ProcMon
- %SYSTEMDRIVE%\\PSTools
- %SYSTEMDRIVE%\\TokenProviderTool
- %SYSTEMDRIVE%\\USLPowershellModules
- %SYSTEMDRIVE%\\UtcUtil
- %SYSTEMDRIVE%\\WPT
- %SYSTEMDRIVE%\\WULogs

Important

**Avoid the following**:

- Blocking the execution of any process from these folders. If your application is anti-malware software, configure your app installation to allow unimpeded execution of all processes from these folders.
- Tampering with any of these folders.

## Test Base registry keys

The applications/tests should not delete or modify any registry keys related to:

- Windows telemetry level
- Removing TLS 1.2
