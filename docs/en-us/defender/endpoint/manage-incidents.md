<!-- Source: https://learn.microsoft.com/en-us/defender-endpoint/manage-incidents -->
<!-- Sitemap-Last-Modified: 2026-01-14 -->

# Manage Microsoft Defender for Endpoint incidents

Managing incidents is an important part of every cybersecurity operation. You can manage incidents by selecting an incident from the **Incidents queue** or the **Incidents management pane**.

Selecting an incident from the **Incidents queue** brings up the **Incident management pane** where you can open the incident page for details.

[![The incidents management pane](https://learn.microsoft.com/en-us/defender-endpoint/media/atp-incidents-mgt-pane-updated.png)](https://learn.microsoft.com/en-us/defender-endpoint/media/atp-incidents-mgt-pane-updated.png#lightbox)

You can assign incidents to yourself, change the status and classification, rename, or comment on them to keep track of their progress.

Tip

For additional visibility at a glance, incident names are automatically generated based on alert attributes such as the number of endpoints affected, users affected, detection sources, or categories. This allows you to quickly understand the scope of the incident.

For example: *Multi-stage incident on multiple endpoints reported by multiple sources.*

Incidents that existed prior to the rollout of automatic incident naming retain their names.

[![The incident detail page](https://learn.microsoft.com/en-us/defender-endpoint/media/atp-incident-details-updated.png)](https://learn.microsoft.com/en-us/defender-endpoint/media/atp-incident-details-updated.png#lightbox)

## Assign incidents

If an incident hasn't been assigned yet, you can select **Assign to me** to assign the incident to yourself. Doing so assumes ownership of not just the incident, but also all the alerts associated with it.

## Set status and classification

### Incident status

You can categorize incidents \(as **Active**, or **Resolved**\) by changing their status as your investigation progresses. This helps you organize and manage how your team can respond to incidents.

For example, your SOC analyst can review the urgent **Active** incidents for the day, and decide to assign them to their self for investigation.

Alternatively, your SOC analyst might set the incident as **Resolved** if the incident was remediated.

### Classification

You can choose not to set a classification, or decide to specify whether an incident is true or false. Doing so helps the team see patterns and learn from them.

### Add comments

You can add comments and view historical events about an incident to see previous changes made to it.

Whenever a change or comment is made to an alert, it's recorded in the Comments and history section.

Added comments instantly appear on the pane.

## Related articles

- [Incidents queue](https://learn.microsoft.com/en-us/defender-endpoint/view-incidents-queue)
- [View and organize the Incidents queue](https://learn.microsoft.com/en-us/defender-endpoint/view-incidents-queue)
- [Investigate incidents](https://learn.microsoft.com/en-us/defender-endpoint/investigate-incidents)
