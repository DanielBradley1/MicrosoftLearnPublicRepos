<!-- Source: https://learn.microsoft.com/en-us/defender-cloud-apps/ops-guide/ops-guide -->
<!-- Sitemap-Last-Modified: 2026-06-14 -->

# Microsoft Defender for Cloud Apps operational guide

This section of the Microsoft Defender for Cloud Apps documentation helps security operations \(SOC\) teams and security administrators to plan and run regular security activities with Microsoft Defender for Cloud Apps.

## Prerequisites

The activities in this article assume that you deployed Defender for Cloud Apps. For more information, see [Basic setup for Defender for Cloud Apps](https://learn.microsoft.com/en-us/defender-cloud-apps/general-setup) and the [Defender for Cloud Apps Ninja training](https://aka.ms/MDCANinjaTraining).

## Activity reference

The following table lists activities that we recommend you perform regularly with Defender for Cloud Apps:

| Frequency | Activities |
| --- | --- |
| **Daily** | - [Review alerts and incidents](https://learn.microsoft.com/en-us/defender-cloud-apps/ops-guide/ops-guide-daily#review-alerts-and-incidents)  <br>- [Review threat detection data](https://learn.microsoft.com/en-us/defender-cloud-apps/ops-guide/ops-guide-daily#review-threat-detection-data)  <br>- [Review application governance](https://learn.microsoft.com/en-us/defender-cloud-apps/ops-guide/ops-guide-daily#review-application-governance)  <br>- [Review Conditional Access app control](https://learn.microsoft.com/en-us/defender-cloud-apps/ops-guide/ops-guide-daily#review-conditional-access-app-control)  <br>- [Review shadow IT - cloud discovery](https://learn.microsoft.com/en-us/defender-cloud-apps/ops-guide/ops-guide-daily#review-shadow-it---cloud-discovery)  <br>- [Review the cloud discovery dashboard](https://learn.microsoft.com/en-us/defender-cloud-apps/ops-guide/ops-guide-daily#review-the-cloud-discovery-dashboard)  <br>- [Review information protection](https://learn.microsoft.com/en-us/defender-cloud-apps/ops-guide/ops-guide-daily#review-information-protection) |
| **Weekly** | - [Review SaaS security posture management](https://learn.microsoft.com/en-us/defender-cloud-apps/ops-guide/ops-guide-weekly#review-saas-security-posture-management)  <br>- [Check app connectors, log collectors, and SIEM agent health](https://learn.microsoft.com/en-us/defender-cloud-apps/ops-guide/ops-guide-weekly#check-app-connectors-log-collectors-and-siem-agent-health)  <br>- [Track new changes in Microsoft Defender XDR](https://learn.microsoft.com/en-us/defender-cloud-apps/ops-guide/ops-guide-weekly#track-new-changes-in-microsoft-defender-xdr)  <br>- [Review the governance log](https://learn.microsoft.com/en-us/defender-cloud-apps/ops-guide/ops-guide-weekly#review-the-governance-log) |
| **Monthly** | - [Review policy assessments](https://learn.microsoft.com/en-us/defender-cloud-apps/ops-guide/ops-guide-monthly#review-policy-assessments)  <br>- [Review activity logs](https://learn.microsoft.com/en-us/defender-cloud-apps/ops-guide/ops-guide-monthly#review-activity-logs) |
| **Ad-hoc** | - [Review Microsoft service health](https://learn.microsoft.com/en-us/defender-cloud-apps/ops-guide/ops-guide-ad-hoc#review-microsoft-service-health)  <br>- [Run advanced hunting queries](https://learn.microsoft.com/en-us/defender-cloud-apps/ops-guide/ops-guide-ad-hoc#run-advanced-hunting-queries)  <br>- [Review file quarantines](https://learn.microsoft.com/en-us/defender-cloud-apps/ops-guide/ops-guide-ad-hoc#review-file-quarantines)  <br>- [Review app risk scores](https://learn.microsoft.com/en-us/defender-cloud-apps/ops-guide/ops-guide-ad-hoc#review-app-risk-scores)  <br>- [Delete cloud discovery data](https://learn.microsoft.com/en-us/defender-cloud-apps/ops-guide/ops-guide-ad-hoc#delete-cloud-discovery-data)  <br>- [Generate a cloud discovery executive report](https://learn.microsoft.com/en-us/defender-cloud-apps/ops-guide/ops-guide-ad-hoc#generate-a-cloud-discovery-executive-report)  <br>- [Generate a cloud discovery snapshot report](https://learn.microsoft.com/en-us/defender-cloud-apps/ops-guide/ops-guide-ad-hoc#generate-a-cloud-discovery-snapshot-report) |

## Related content

- [Integrating Microsoft Defender into your security operations](https://learn.microsoft.com/en-us/microsoft-365/security/defender/integrate-microsoft-365-defender-secops?bc=%2Fsecurity%2Foperations%2Fbreadcrumb%2Ftoc.json&toc=%2Fsecurity%2Foperations%2Ftoc.json)
- [Microsoft Defender for Office 365 Security Operations Guide](https://learn.microsoft.com/en-us/microsoft-365/security/office-365-security/mdo-sec-ops-guide?bc=%2Fsecurity%2Foperations%2Fbreadcrumb%2Ftoc.json&toc=%2Fsecurity%2Foperations%2Ftoc.json)
- [Microsoft Entra security operations guide](https://learn.microsoft.com/en-us/entra/architecture/security-operations-introduction?bc=%2Fsecurity%2Foperations%2Fbreadcrumb%2Ftoc.json&toc=%2Fsecurity%2Foperations%2Ftoc.json)
