<!-- Source: https://learn.microsoft.com/en-us/defender-for-identity/ops-guide/ops-guide-quarterly -->
<!-- Sitemap-Last-Modified: 2026-08-08 -->

# Quarterly / ad-hoc operational guide - Microsoft Defender for Identity

This article reviews the Microsoft Defender for Identity activities we recommend for your team on a quarterly or ad-hoc basis, depending on your organization's needs and processes.

Perform ad hoc activities as issues arise in your organization, or as part of a quarterly operational review.

## Review Microsoft service health

Check the current status of Microsoft services to identify any known issues that might affect your environment.

**Where**: Check the following locations:

- In the Microsoft 365 admin center, select **Health > Service health**
- [Microsoft 365 Service health status](https://status.office365.com/)
- X: [https://twitter.com/MSFT365status](https://twitter.com/MSFT365status)

**Persona**: Security and compliance administrators

If you're experiencing issues with a cloud service, we recommend checking service health updates to determine whether it's a known issue, with a resolution in progress, before you call support or spend time troubleshooting.

For more information, see [Review Defender for Identity health issues](https://learn.microsoft.com/en-us/defender-for-identity/ops-guide/ops-guide-daily#review-defender-for-identity-health-issues).

## Review server setup process to include sensors

**Where**: Your organization's internal process documentation

**Persona**: Security administrators

We recommend that you periodically verify your organization's server setup process to make sure that it includes installing the Defender for Identity sensor. This ensures that all new domain controllers, AD CS, and AD FS servers are protected right away.

For more information, see [Deploy Microsoft Defender for Identity with Microsoft Defender](https://learn.microsoft.com/en-us/defender-for-identity/deploy/deploy-defender-identity).

## Check domain configuration via PowerShell

**Where**: PowerShell on your Defender for Identity sensor machines

**Persona**: Security administrators

We recommend that you periodically run the **Test-MDIConfiguration** PowerShell command. It checks whether your domain controller audit policy settings are correct. Wrong settings can cause gaps in the Event Log and reduce Defender for Identity coverage.

For more information, see:

- [Configure audit policies for Windows event logs](https://learn.microsoft.com/en-us/defender-for-identity/deploy/configure-windows-event-collection)
- [Test-MDIConfiguration](https://learn.microsoft.com/en-us/powershell/module/defenderforidentity/test-mdiconfiguration) PowerShell documentation

## Related content

- [Microsoft Defender Security operations overview](https://learn.microsoft.com/en-us/security/operations/overview)
- [Microsoft Defender for Identity operational guide](https://learn.microsoft.com/en-us/defender-for-identity/ops-guide/ops-guide)
- [Daily operational guide - Microsoft Defender for Identity](https://learn.microsoft.com/en-us/defender-for-identity/ops-guide/ops-guide-daily)
- [Weekly operational guide - Microsoft Defender for Identity](https://learn.microsoft.com/en-us/defender-for-identity/ops-guide/ops-guide-weekly)
- [Monthly operational guide - Microsoft Defender for Identity](https://learn.microsoft.com/en-us/defender-for-identity/ops-guide/ops-guide-monthly)
