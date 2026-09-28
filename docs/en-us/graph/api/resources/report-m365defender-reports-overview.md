<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/report-m365defender-reports-overview?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-05-13 -->

# Reports API overview for attack simulation training as part of Microsoft Defender for Office 365

This section describes reporting capabilities of Microsoft Defender for Office 365, specifically APIs that access reports on a tenant's participation in attack simulation training. Attack simulation trainings set up benign cyberattack simulations to train users in the tenant to increase their awareness, and help identify vulnerable users.

## What role do the attack simulation reports play in enterprise defense?

Attack simulation reports help tenant administrators identify security knowledge gaps, so that they can further train their users to decrease their susceptibility to attacks. The attack simulation training service is part of [Microsoft Defender for Office 365](https://learn.microsoft.com/en-us/microsoft-365/security/office-365-security/defender-for-office-365?view=o365-worldwide&preserve-view=true) which safeguards your organization against malicious threats posed by email messages, links \(URLs\), and collaboration tools.

Microsoft Defender for Office 365 belongs to the [Microsoft 365 Defender](https://learn.microsoft.com/en-us/microsoft-365/security/defender/microsoft-365-defender?view=o365-worldwide&preserve-view=true) suite which includes the following services:

- [Microsoft Defender for Endpoint](https://learn.microsoft.com/en-us/microsoft-365/security/defender-endpoint/microsoft-defender-endpoint)
- [Microsoft Defender for Office 365](https://learn.microsoft.com/en-us/microsoft-365/security/office-365-security/overview)
- [Microsoft Defender for Identity](https://learn.microsoft.com/en-us/defender-for-identity/)
- [Microsoft Defender for Cloud Apps](https://learn.microsoft.com/en-us/cloud-app-security/)

Microsoft 365 Defender is a unified enterprise defense suite that helps detect security risks, investigate attacks to an organization, and prevent harmful activities automatically. It provides a central administrators portal \([https://security.microsoft.com/](https://security.microsoft.com)\) that combines protection, detection, investigation, and response to *email*, *collaboration*, *identity*, and *device* threats.

To access attack simulation training, open the Microsoft 365 Defender portal, go to **Email & collaboration** > **Attack simulation training**.

## Authorization

Microsoft Graph controls access to resources using permissions. You must specify the permissions you need in order to access reports resources. For more information, see [Microsoft Graph permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference) and [reports permissions](https://learn.microsoft.com/en-us/graph/permissions-reference#reports-permissions).

## What kinds of data do the reports return?

| Kinds of data | Resource | API |
| :--- | :--- | :--- |
| Vulnerable repeat offenders in a tenant | [attackSimulationRepeatOffender](https://learn.microsoft.com/en-us/graph/api/resources/attacksimulationrepeatoffender?view=graph-rest-1.0) | [getAttackSimulationRepeatOffenders](https://learn.microsoft.com/en-us/graph/api/securityreportsroot-getattacksimulationrepeatoffenders?view=graph-rest-1.0) |
| Simulation data and results for each user in a tenant | [attackSimulationSimulationUserCoverage](https://learn.microsoft.com/en-us/graph/api/resources/attacksimulationsimulationusercoverage?view=graph-rest-1.0) | [getAttackSimulationSimulationUserCoverage](https://learn.microsoft.com/en-us/graph/api/securityreportsroot-getattacksimulationsimulationusercoverage?view=graph-rest-1.0) |
| Training coverage for each user in a tenant | [attackSimulationTrainingUserCoverage](https://learn.microsoft.com/en-us/graph/api/resources/attacksimulationtrainingusercoverage?view=graph-rest-1.0) | [getAttackSimulationTrainingUserCoverage](https://learn.microsoft.com/en-us/graph/api/securityreportsroot-getattacksimulationtrainingusercoverage?view=graph-rest-1.0) |

## Next steps

Reports resources and APIs can open up new ways for you to engage with users and manage their experiences with Microsoft Graph. To learn more:

- Drill down on the methods and properties of the resources most helpful to your scenario.
- Try the API in the [Graph Explorer](https://developer.microsoft.com/graph/graph-explorer).
