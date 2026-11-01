<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/copilot/employee-self-service/declarative-agent-workday-samples -->
<!-- Sitemap-Last-Modified: 2026-10-30 -->

# Add more Workday scenarios to the Employee Self-Service declarative agent

The Employee Self-Service HR declarative agent includes a set of [built-in Workday scenarios](https://learn.microsoft.com/en-us/microsoft-365/copilot/employee-self-service/declarative-agent-workday#supported-scenarios). If your employees or managers need Workday tasks beyond those, you can add scenario topics from the open-source Workday samples in the [Employee Self-Service Agent Developer Kit repository](https://github.com/microsoft/Employee-Self-Service-Agent-Developer-Kit/tree/main/samples/Workday). The samples use the same Workday connection and runtime package that `/connect workday` sets up for the built-in scenarios.

Note

The samples work only after you connect the Employee Self-Service HR agent to Workday. If you haven't set up the Workday integration yet, start with [Run /connect workday in Dev](https://learn.microsoft.com/en-us/microsoft-365/copilot/employee-self-service/declarative-agent-workday#run-connect-workday-in-dev).

You add samples manually in Copilot Studio. This article lists the available scenarios and helps you decide when to add them. For the step-by-step instructions, see the [Workday samples README](https://github.com/microsoft/Employee-Self-Service-Agent-Developer-Kit/tree/main/samples/Workday).

## Available scenarios

Add only the scenarios your organization needs. Each scenario is a separate topic.

### Employee scenarios

| Scenario | What employees can do | Workday access |
| --- | --- | --- |
| [EmployeeGetVacationBalance](https://github.com/microsoft/Employee-Self-Service-Agent-Developer-Kit/tree/main/samples/Workday/Employee/EmployeeGetVacationBalance) | View their vacation and time-off balance. | Read |
| [WorkdayEmployeeRequestTimeOff](https://github.com/microsoft/Employee-Self-Service-Agent-Developer-Kit/tree/main/samples/Workday/Employee/WorkdayEmployeeRequestTimeOff) | Request time off for themselves. | Read and write |
| [WorkdayGetUserProfile](https://github.com/microsoft/Employee-Self-Service-Agent-Developer-Kit/tree/main/samples/Workday/Employee/WorkdayGetUserProfile) | View their profile, including identity, contact, organization, and manager. | Read |
| [WorkdayGetContactInformation](https://github.com/microsoft/Employee-Self-Service-Agent-Developer-Kit/tree/main/samples/Workday/Employee/WorkdayGetContactInformation) | View their work and home phone numbers, email addresses, and addresses. | Read |
| [WorkdayGetEducation](https://github.com/microsoft/Employee-Self-Service-Agent-Developer-Kit/tree/main/samples/Workday/Employee/WorkdayGetEducation) | View their education history. | Read |
| [WorkdayGetGovernmentIDs](https://github.com/microsoft/Employee-Self-Service-Agent-Developer-Kit/tree/main/samples/Workday/Employee/WorkdayGetGovernmentIDs) | View the government IDs on their profile. | Read |
| [WorkdayEmployeesviewtheirjobtaxonomy](https://github.com/microsoft/Employee-Self-Service-Agent-Developer-Kit/tree/main/samples/Workday/Employee/WorkdayEmployeesviewtheirjobtaxonomy) | View their job title, job function, and job profile. | Read |
| [WorkdayGivePeerFeedback](https://github.com/microsoft/Employee-Self-Service-Agent-Developer-Kit/tree/main/samples/Workday/Employee/WorkdayGivePeerFeedback) | Give feedback about a coworker. | Write |
| [EmployeeAddDependents](https://github.com/microsoft/Employee-Self-Service-Agent-Developer-Kit/tree/main/samples/Workday/Employee/EmployeeAddDependents) | Add a dependent to their profile and benefits. | Read and write |
| [EmployeeUpdateResidentialAddress](https://github.com/microsoft/Employee-Self-Service-Agent-Developer-Kit/tree/main/samples/Workday/Employee/EmployeeUpdateResidentialAddress) | View and update their home address. | Read and write |
| [WorkdayManageEmergencyContact](https://github.com/microsoft/Employee-Self-Service-Agent-Developer-Kit/tree/main/samples/Workday/Employee/WorkdayManageEmergencyContact) | View, add, update, or remove their emergency contacts. | Read and write |

### Manager scenarios

Manager scenarios return information about the signed-in manager's direct reports.

| Scenario | What managers can do | Workday access |
| --- | --- | --- |
| [WorkdayManagersdirect-CompanyCode](https://github.com/microsoft/Employee-Self-Service-Agent-Developer-Kit/tree/main/samples/Workday/Manager/WorkdayManagersdirect-CompanyCode) | View company codes for their direct reports. | Read |
| [WorkdayManagersdirect-CostCenter](https://github.com/microsoft/Employee-Self-Service-Agent-Developer-Kit/tree/main/samples/Workday/Manager/WorkdayManagersdirect-CostCenter) | View cost centers for their direct reports. | Read |
| [WorkdayManagersdirect-Jobtaxanomy](https://github.com/microsoft/Employee-Self-Service-Agent-Developer-Kit/tree/main/samples/Workday/Manager/WorkdayManagersdirect-Jobtaxanomy) | View job titles, job profiles, and job families for their direct reports. | Read |
| [WorkdayManagerServiceAnniversary](https://github.com/microsoft/Employee-Self-Service-Agent-Developer-Kit/tree/main/samples/Workday/Manager/WorkdayManagerServiceAnniversary) | View upcoming service anniversaries for their direct reports. | Read |
| [WorkdayGetManagerReporteesTimeInPosition](https://github.com/microsoft/Employee-Self-Service-Agent-Developer-Kit/tree/main/samples/Workday/Manager/WorkdayGetManagerReporteesTimeInPosition) | View how long each direct report has been in their current position. | Read |

## When to add samples

Add samples when your employees or managers need a Workday task that the built-in scenarios don't cover, such as requesting time off, checking a vacation balance, updating a home address, or viewing information about direct reports.

Add samples only after:

- `/connect workday` completes in your development \(Dev\) environment, and the maker validation in [Phase 6](https://learn.microsoft.com/en-us/microsoft-365/copilot/employee-self-service/declarative-agent-workday#phase-6-validate-in-the-test-pane) succeeds. The samples depend on the Workday connection, runtime package, and Workday system topics that the skill configures. If the built-in scenarios don't work, the samples don't work either.
- Your Workday administrator confirms that the security groups for your rollout can access the data and business processes that each selected scenario uses. The samples call Workday as the signed-in employee, so Workday security decides what each employee can view and change.

Add and test samples in Dev, and then promote the agent to Test and Production. The sample topics move with the agent, so you don't add them again in Test or Production. Don't add samples directly in Test or Production.

## Before you add samples

- **Plan for upgrades.** Upgrading the Employee Self-Service HR agent or the Workday package overwrites the sample topics and the shared setup topic. Before you upgrade, back up these topics. After the upgrade, add them again, and then test them.
- **Check for overlap with built-in scenarios.** Some samples cover information that a built-in scenario also returns. For example, **WorkdayManageEmergencyContact** overlaps **Workday Get EmergencyContact**, and **WorkdayGetUserProfile** can answer "What's my employee ID?", which **Workday Get EmployeeId** also answers. After you add a sample, test prompts for both topics to see which one responds. If the response isn't the one you want, turn off the topic you don't want.
- **Prepare test data for write scenarios.** Scenarios that update Workday, such as requesting time off or adding a dependent, submit real changes. Test them with approved test workers.
- **Review tenant-specific values.** Some samples include picklists, IDs, or URLs that you must align with your Workday tenant.
- **Understand the support model.** The samples are provided as open source in the Agent Developer Kit repository. For questions and issues, use the repository's [GitHub issues](https://github.com/microsoft/Employee-Self-Service-Agent-Developer-Kit/issues).

## How to add samples

The [Workday samples README](https://github.com/microsoft/Employee-Self-Service-Agent-Developer-Kit/tree/main/samples/Workday) has the complete steps. At a high level:

1. Create the shared setup topic, **WorkdayOSSTemplateConfigurationSetup**, once for the agent. Call it from the **Conversation Start** topic after **Workday \[System\] - 1: Set Runtime Template Configurations**.
2. For each scenario you want, create a topic from the scenario's YAML, and review its tenant-specific values.
3. Start a new conversation in the Copilot Studio test pane. Test each scenario you added, and retest the built-in Workday scenarios.

Important

The shared setup topic must run after the built-in Workday configuration topic. If the order is reversed, the built-in configuration overwrites the sample configuration, and the sample scenarios fail.

## Related content

- [Integrate Workday with the Employee Self-Service declarative agent](https://learn.microsoft.com/en-us/microsoft-365/copilot/employee-self-service/declarative-agent-workday)
- [Microsoft Entra and Workday administrator reference for the Employee Self-Service declarative agent](https://learn.microsoft.com/en-us/microsoft-365/copilot/employee-self-service/declarative-agent-workday-reference)
- [Manage the lifecycle of Employee Self-Service declarative agents](https://learn.microsoft.com/en-us/microsoft-365/copilot/employee-self-service/alm-declarative-agent)
- [Employee Self-Service Agent Developer Kit](https://learn.microsoft.com/en-us/microsoft-365/copilot/employee-self-service/declarative-agent-developer-kit-overview)
