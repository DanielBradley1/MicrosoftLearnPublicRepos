<!-- Source: https://learn.microsoft.com/en-us/defender-endpoint/view-incidents-queue -->
<!-- Sitemap-Last-Modified: 2026-01-15 -->

# View and organize the Microsoft Defender for Endpoint Incidents queue

The **Incidents queue** shows a collection of incidents that were flagged from devices in your network. It helps you sort through incidents to prioritize and create an informed cybersecurity response decision.

By default, the queue displays incidents seen in the last week, with the most recent incident showing at the top of the list, helping you see the most recent incidents first.

There are several options you can choose from to customize the Incidents queue view.

On the top navigation you can:

- Customize columns to add or remove columns
- Modify the number of items to view per page
- Select the items to show per page
- Batch-select the incidents to assign
- Navigate between pages
- Apply filters
- Customize and apply date ranges

[![The Incidents queue](https://learn.microsoft.com/en-us/defender-endpoint/media/atp-incident-queue.png)](https://learn.microsoft.com/en-us/defender-endpoint/media/atp-incident-queue.png#lightbox)

Tip

**Defender Boxed**, a series of cards showcasing your organization's security successes, improvements, and response actions in the past six months/year, appears for a limited time during January and July of each year. Learn how you can share your [Defender Boxed](https://learn.microsoft.com/en-us/defender-xdr/incident-queue#defender-boxed) highlights.

## Sort and filter the incidents queue

You can apply the following filters to limit the list of incidents and get a more focused view.

### Severity

| Incident severity | Description |
| :--- | :--- |
| High  <br>\(Red\) | Threats often associated with advanced persistent threats \(APT\). These incidents indicate a high risk due to the severity of damage they can inflict on devices. |
| Medium  <br>\(Orange\) | Threats rarely observed in the organization, such as anomalous registry change, execution of suspicious files, and observed behaviors typical of attack stages. |
| Low  <br>\(Yellow\) | Threats associated with prevalent malware and hack-tools that don't necessarily indicate an advanced threat targeting the organization. |
| Informational  <br>\(Grey\) | Informational incidents might not be considered harmful to the network but might be good to keep track of. |

## Assigned to

You can choose to filter the list by selecting assigned to anyone or ones that are assigned to you.

### Category

Incidents are categorized based on the description of the stage by which the cybersecurity kill chain is in. This view helps the threat analyst to determine priority, urgency, and corresponding response strategy to deploy based on context.

### Status

You can choose to limit the list of incidents shown based on their status to see which ones are active or resolved.

### Data sensitivity

Use this filter to show incidents that contain sensitivity labels.

## Incident naming

To understand the incident's scope at a glance, incident names are automatically generated based on alert attributes such as the number of endpoints affected, users affected, detection sources, or categories.

For example: *Multi-stage incident on multiple endpoints reported by multiple sources.*

Note

Incidents that existed prior to the rollout of automatic incident naming retains their original name.

## See also

- [Incidents queue](https://learn.microsoft.com/en-us/defender-endpoint/view-incidents-queue)
- [Manage incidents](https://learn.microsoft.com/en-us/defender-endpoint/manage-incidents)
- [Investigate incidents](https://learn.microsoft.com/en-us/defender-endpoint/investigate-incidents)
