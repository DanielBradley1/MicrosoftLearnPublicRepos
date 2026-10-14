<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/copilot/employee-self-service/declarative-agent-landing-page -->
<!-- Sitemap-Last-Modified: 2026-10-13 -->

# Configure the landing page for the Employee Self-Service declarative agent

Configure the landing page to help employees discover common scenarios, open important resources, and see personalized information when they start the Employee Self-Service declarative agent.

You can manage the tenant-level landing-page configuration through either of these surfaces:

- The Employee Self-Service Agent Developer Kit \(ADK\).
- The Microsoft 365 admin center.

Both surfaces manage the same landing-page configuration. Avoid editing in both surfaces at the same time. Finish and publish or save your changes in one surface, and then refresh the other surface and review the current values before you make another change.

Copilot Studio manages agent-level properties, including the agent name and icon. ADK can display these properties, but it can't change them.

## Choose a configuration surface

| Configuration | ADK | Microsoft 365 admin center | Copilot Studio |
| --- | --- | --- | --- |
| Accent colors | Interactive editor | Available | Not available |
| Quick links | Interactive editor | Available | Not available |
| Categorized starter prompts | Interactive editor | Available | Not available |
| Stay up to date | Guided configuration | Available | Not available |
| Quick Access | Guided configuration | Availability can vary | Not available |
| Basic starter prompts | Not part of the landing-page command | Not available | Available |
| Agent name and icon | Read-only | Not editable | Available |
| Conversation History | No Employee Self-Service-specific configuration | No Employee Self-Service-specific configuration | No Employee Self-Service-specific configuration |

Tenant-level categorized starter prompts override basic starter prompts configured in Copilot Studio.

## Configure the landing page with ADK

Use the `main` branch of the ADK for the native declarative agent. For setup information, see [Agent Developer Kit for declarative agents: overview](https://learn.microsoft.com/en-us/microsoft-365/copilot/employee-self-service/declarative-agent-developer-kit-overview). The public [Employee Self-Service Agent Developer Kit repository](https://github.com/microsoft/Employee-Self-Service-Agent-Developer-Kit) provides the current ADK source.

After you complete ADK setup and select the target agent, enter this command in GitHub Copilot Chat:

```text
/landing-page
```

The command summarizes the current configuration and guides you through one setting at a time. For command details, see [Configure the landing page](https://learn.microsoft.com/en-us/microsoft-365/copilot/employee-self-service/declarative-agent-commands-reference#configure-the-landing-page).

### Use the interactive editors

ADK provides interactive editors for these settings:

- **Accent colors**: Review the current light and dark colors, edit them, and publish the changes.
- **Quick links**: Add, edit, remove, and arrange employee-facing links.
- **Starter prompts**: Organize suggested prompts into categories.

Opening an editor doesn't publish a change. Review the draft, and then select **Publish** in the editor. Published changes can take a few hours to appear for employees.

### Configure settings without a dedicated editor

ADK uses guided or direct configuration for these settings:

- **Stay up to date**: Turn personalized ticket-related cards on or off.
- **Quick Access**: Turn personalized information cards on or off.

### View the agent name and icon

ADK treats the agent name and icon as read-only. It can report the name and display the icon for the selected agent.

To change either property, open the declarative agent in Copilot Studio, update the applicable agent details, and republish the agent.

## Configure the landing page in the Microsoft 365 admin center

Use an account with one of these roles:

- AI Administrator.
- Global Administrator.

Use the role with the fewest permissions that can complete the task. Limit the Global Administrator role to scenarios where a lower-privileged role isn't sufficient.

To open the landing-page settings:

1. Sign in to the Microsoft 365 admin center.
2. Expand **Copilot**, and then select **Settings**.
3. On the **Data access** tab, select **View all**.
4. Select **Employee Self-Service Agent**.
5. Select an existing primary Employee Self-Service agent.

If the agent isn't listed, select **Add an agent**, search for the published primary Employee Self-Service declarative agent, and add it. Landing-page configuration applies to supported primary Employee Self-Service Core, HR, and IT agents, not attached subagents or general agents.

### Configure categorized starter prompts

Categorized starter prompts help employees understand what the agent can do and start common scenarios.

Use these limits:

- Maximum 10 categories.
- Maximum 35 characters in a category name.
- Maximum 12 prompts in each category.
- Maximum 128 characters in a prompt title. Use a unique title for each prompt.
- Maximum 4,000 characters in the prompt text.

These tenant-level prompts override basic starter prompts configured in Copilot Studio.

To configure the prompts:

1. Open the selected agent's landing-page settings.
2. Select the **Starter prompts** tab.
3. Download the CSV template.
4. Add the categories, unique prompt titles, and prompt text.
5. Upload the completed CSV file and review the validation results.
6. Select **Save**.

### Configure accent colors

Configure separate accent colors for the light and dark themes. Each value must be a six-digit HEX color in `#RRGGBB` format.

Use a contrast ratio of at least 4.5:1 for readability. The Microsoft 365 admin center warns about a low-contrast value before you save it. In ADK, a generated suggestion must meet the recommended contrast ratio. If you provide an exact low-contrast value, ADK shows the contrast result and asks you to confirm the value before it applies the change.

To configure the colors:

1. Open the selected agent's landing-page settings.
2. Select the **Accent colors** tab.
3. Enter or select the light-theme and dark-theme colors.
4. Review any contrast warning.
5. Select **Save**.

If you don't configure custom colors, the landing page uses the default Copilot colors.

### Configure quick links

Quick links give employees direct access to important tenant resources.

Use these requirements:

- Maximum 10 links.
- A nonempty display label for each link.
- An absolute HTTPS URL for each destination.

The configuration validates the URL format. It doesn't verify that the destination is available or that every employee is authorized to open it. Test each link with the intended audience and confirm the destination's access controls.

To configure the links:

1. Open the selected agent's landing-page settings.
2. Select the **Quick links** tab.
3. Download the CSV template.
4. Add the display labels and absolute HTTPS URLs.
5. Upload the completed CSV file and review the validation results.
6. Select **Save**.

No Quick Links section appears when you don't configure any links.

### Configure Stay up to date

**Stay up to date** displays a personalized carousel of actionable cards. The cards can show in-progress ticket status, required follow-ups, and time-sensitive tasks. Employees can select a card to start a related conversation.

The cards use configured ticket-related sources, such as ServiceNow topics and connectors. They don't create or modify tickets.

To configure the setting:

1. Open the selected agent's landing-page settings.
2. Select the **Personalized content** tab.
3. Turn **Show stay up to date cards** on or off.
4. Select **Save**.

The toggle is available after you add the supported primary agent.

### Configure Quick Access

**Quick Access** displays personalized, high-frequency information cards. Examples include:

- Time-off balance and status.
- Upcoming paid holidays.
- Service anniversaries for the employee and, where applicable, team members.

Employees can select a card to start a related conversation.

ADK supports the Quick Access toggle. The corresponding control might not be available in every Microsoft 365 admin center experience. If **Quick Access** appears in the selected agent's landing-page settings, turn it on or off and save the change.

### Understand Conversation History

Conversation History uses the shared Microsoft Copilot chat-history experience so employees can reopen prior conversations.

Employee Self-Service doesn't provide a separate Conversation History store or an Employee Self-Service-specific setting in ADK, the Microsoft 365 admin center landing-page configuration, or Copilot Studio. The Microsoft Copilot platform governs retention, deletion, and compliance behavior.

## Validate related changes

FlightCheck doesn't validate settings that affect only the landing page. Review the published landing page directly and test links and prompts with representative employee accounts.

Run FlightCheck when your work also changes broader readiness areas, such as topics, connectors, identity, permissions, publishing, or deployment. For more information, see [FlightCheck readiness check](https://learn.microsoft.com/en-us/microsoft-365/copilot/employee-self-service/declarative-agent-commands-reference#flightcheck-readiness-check).

## Related content

- [Customize the Employee Self-Service declarative agent](https://learn.microsoft.com/en-us/microsoft-365/copilot/employee-self-service/declarative-agent-customize)
- [Agent Developer Kit for declarative agents: overview](https://learn.microsoft.com/en-us/microsoft-365/copilot/employee-self-service/declarative-agent-developer-kit-overview)
- [Agent Developer Kit commands for declarative agents](https://learn.microsoft.com/en-us/microsoft-365/copilot/employee-self-service/declarative-agent-commands-reference)
