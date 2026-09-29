<!-- Source: https://learn.microsoft.com/en-us/defender-xdr/investigate-incident-cases -->
<!-- Sitemap-Last-Modified: 2026-09-23 -->

# Investigate incident cases in the Microsoft Defender portal

Use incident cases to investigate incidents in the Microsoft Defender portal. Incident cases bring together investigation context, related alerts, impacted assets, evidence, activities, and attachments so analysts can understand what happened and take response actions.

For case management tasks, such as assigning ownership, updating status, adding comments, managing tasks, and resolving or closing an incident case, see [Manage incident cases in the Microsoft Defender portal](https://learn.microsoft.com/en-us/defender-xdr/manage-incident-cases).

Note

Incident cases are in preview and are the recommended experience for managing incidents in the Microsoft Defender portal. The legacy incident experience remains available during this preview.

## Prerequisites

Before you begin, make sure that:

- Your tenant is onboarded to the Microsoft Defender portal.
- You have access to incident cases in the Defender portal.
- You have one of the following Microsoft Defender unified RBAC permissions:

  - **Security Data Read** to view and investigate incident cases.
  - **Security Data Manage** to view, investigate, and manage incident cases.

Incident case permissions and scoping follow the same permissions model as the legacy incident experience. Permissions for specific response actions can vary by action and workload.

For more information, see [Microsoft Defender unified role-based access control \(RBAC\)](https://learn.microsoft.com/en-us/defender-xdr/manage-rbac).

## Review the incident case summary

Use the **Summary** page to review the main details of the incident case before you start a deeper investigation.

Use the summary to review:

- Priority assessment
- Summary by Copilot, when available
- Case details
- Case description
- Case ID
- Created and updated details

To review the incident case summary:

1. Sign in to the [Microsoft Defender portal](https://security.microsoft.com).
2. Select **Cases**.
3. Select **Incident**.
4. Select the relevant incident case.
5. Go to **Overview** > **Summary by Copilot**.
6. Review the case context, priority, and key details.

   ![Screenshot showing the Summary by Copilot section for an incident case in the Microsoft Defender portal.](https://learn.microsoft.com/en-us/defender-xdr/media/investigate-incident-cases/investigate-incident-cases-summary-by-copilot.png)

## Review the attack story

Use the **Attack story** page to review the incident graph, related alerts, affected entities, and attack context.

Use the attack story to review:

- Incident graph
- Related alerts
- Affected entities
- Detection and category details
- First and last activity times
- Alert details
- Actions taken
- Related events

To review the attack story:

1. Sign in to the [Microsoft Defender portal](https://security.microsoft.com).
2. Select **Cases**.
3. Select **Incident**.
4. Select the relevant incident case.
5. Go to **Overview** > **Attack graph**.

   ![Screenshot showing the Attack graph view for an incident case in the Microsoft Defender portal.](https://learn.microsoft.com/en-us/defender-xdr/media/investigate-incident-cases/investigate-incident-cases-attack-story.png)
6. Review the detection and category details, alert list, and incident graph.
7. Select an alert to review more details.
8. Review **Actions taken** and **Related events** for the selected alert.

### Filter and focus the incident graph

Use filters and graph controls to simplify the incident graph and focus on the alerts or entities that matter most.

To filter and focus the incident graph:

1. Sign in to the [Microsoft Defender portal](https://security.microsoft.com).
2. Select **Cases**.
3. Select **Incident**.
4. Select the relevant incident case.
5. Go to **Overview** > **Attack graph**.
6. Use the available filters to focus the attack story by severity, status, service source, or other available criteria.
7. Select **Add filter** to add more filters.
8. Select **Reset all** to clear the filters.
9. Use **Layout** to change the graph layout.
10. Turn **Group similar nodes** on or off to group or separate similar entities.
11. Select **Entity types** to filter the graph by entity type, or select **Show all** to show all entity types.

### Review blast radius analysis

Use blast radius analysis to explore potential paths from breached entities to target assets in the incident graph. Blast radius analysis helps you understand possible impact and prioritize investigation or response actions.

To review blast radius analysis:

1. Sign in to the [Microsoft Defender portal](https://security.microsoft.com).
2. Select **Cases**.
3. Select **Incident**.
4. Select the relevant incident case.
5. Go to **Overview** > **Attack graph**.
6. Select an entity in the incident graph.
7. If blast radius analysis is available, review the blast radius paths and related target assets.

Note

Blast radius analysis availability can depend on your environment, available data, and permissions.

## Review alerts

Use the **Alerts** page to review alerts associated with the incident case.

Use alerts to review:

- Alert severity
- Investigation state
- Alert status
- Category
- Impacted assets
- Correlation reason
- Detection source
- Product name
- First and last activity times

To review alerts:

1. Sign in to the [Microsoft Defender portal](https://security.microsoft.com).
2. Select **Cases**.
3. Select **Incident**.
4. Select the relevant incident case.
5. Go to **Artifacts** > **Alerts**.

   ![Screenshot showing the Alerts page for an incident case in the Microsoft Defender portal.](https://learn.microsoft.com/en-us/defender-xdr/media/investigate-incident-cases/investigate-incident-cases-alerts.png)
6. Filter, search, or customize the alerts table as needed.
7. Select an alert to review more details.

Alert details can include alert state, classification, assigned user, MITRE ATT&CK techniques, detection source, service source, evidence, alert description, related events, and impacted assets.

To move an alert to another incident case, see [Move alerts from one incident case to another in the Microsoft Defender portal](https://learn.microsoft.com/en-us/defender-xdr/move-alert-to-another-incident-case).

## Review assets

Use the **Assets** page to review assets associated with the incident case.

Assets can include:

- Devices
- Users
- Mailboxes
- Apps
- Cloud resources
- AI agents

To review assets:

1. Sign in to the [Microsoft Defender portal](https://security.microsoft.com).
2. Select **Cases**.
3. Select **Incident**.
4. Select the relevant incident case.
5. Go to **Artifacts** > **Assets**.

   ![Screenshot showing the Assets page for an incident case in the Microsoft Defender portal.](https://learn.microsoft.com/en-us/defender-xdr/media/investigate-incident-cases/investigate-incident-cases-assets.png)
6. Select an asset type.
7. Filter, export, or customize the asset table as needed.
8. Select an asset to review more details.

The asset details pane provides more context about the selected asset. Details vary by asset type and can include related alerts, risk or exposure information, activity details, metadata, and links to open the asset page for deeper investigation.

Available actions vary by asset type and permissions. For example, you might be able to open the asset page, summarize the asset, view the asset in a map, manage tags, initiate an automated investigation, mark a user as compromised, or review device actions.

## Review investigations

Use the **Investigations** page to review automated investigations associated with the incident case, when available.

Use investigations to review:

- Automated investigation status
- Investigation details
- Remediation status
- Pending actions, when available

To review investigations:

1. Sign in to the [Microsoft Defender portal](https://security.microsoft.com).
2. Select **Cases**.
3. Select **Incident**.
4. Select the relevant incident case.
5. Go to **Artifacts** > **Investigations**.
6. Review any investigations associated with the incident case.
7. Select an investigation to review more details, if available.

## Review evidence

Use the **Evidence** page to review evidence associated with the incident case.

Evidence can include:

- IP addresses
- Email clusters
- Emails
- Cloud logon sessions
- Other supported entities or suspicious activity

Use evidence to review:

- First seen time
- Entity or entity type
- Verdict
- Remediation status
- Impacted assets
- Detection origin
- Threats

To review evidence:

1. Sign in to the [Microsoft Defender portal](https://security.microsoft.com).
2. Select **Cases**.
3. Select **Incident**.
4. Select the relevant incident case.
5. Go to **Artifacts** > **Evidence**.
6. Select an evidence type, or select **All evidence**.
7. Filter or customize the evidence table as needed.
8. Select an evidence item to review more details, if available.

## Review activity history

Use the **Activities** page to review manual and automated activity associated with the incident case. Activities can include case updates, severity changes, automation actions, and other case management events.

Use activity history to review:

- Case creation
- Assignment changes
- Status changes
- Severity or priority changes
- Classification or determination changes
- Task updates
- Comments
- Automation updates
- Other workflow changes

To review activity history:

1. Sign in to the [Microsoft Defender portal](https://security.microsoft.com).
2. Select **Cases**.
3. Select **Incident**.
4. Select the relevant incident case.
5. Go to **Artifacts** > **Activities**.
6. Filter the activity history as needed.
7. Select an activity item to review more details.

## Review attachments

Use the **Attachments** tab to review files added to the incident case. Attachments can provide supporting context for investigation, handoff, or post-incident review.

To review attachments:

1. Sign in to the [Microsoft Defender portal](https://security.microsoft.com).
2. Select **Cases**.
3. Select **Incident**.
4. Select the relevant incident case.
5. Select **Comments & Attachments**.
6. Select the **Attachments** tab.
7. Review the files attached to the incident case.
8. Select an attachment to view its details.

You can also download attachments for further review.

For information about adding or removing attachments, see [Manage incident cases in the Microsoft Defender portal](https://learn.microsoft.com/en-us/defender-xdr/manage-incident-cases#add-comments-and-attachments).

## Related content

- [Manage incident cases in the Microsoft Defender portal](https://learn.microsoft.com/en-us/defender-xdr/manage-incident-cases)
- [Manage incident case tasks in the Microsoft Defender portal](https://learn.microsoft.com/en-us/defender-xdr/manage-incident-case-tasks)
- [Move alerts from one incident case to another in the Microsoft Defender portal](https://learn.microsoft.com/en-us/defender-xdr/move-alert-to-another-incident-case)
- [Plan an incident response workflow in the Microsoft Defender portal](https://learn.microsoft.com/en-us/defender-xdr/plan-incident-response)
- [Alert correlation and incident merging in the Microsoft Defender portal](https://learn.microsoft.com/en-us/defender-xdr/alerts-incidents-correlation)
