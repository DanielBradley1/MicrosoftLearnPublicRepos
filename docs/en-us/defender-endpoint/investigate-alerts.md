<!-- Source: https://learn.microsoft.com/en-us/defender-endpoint/investigate-alerts -->
<!-- Sitemap-Last-Modified: 2026-01-14 -->

# Investigate alerts in Microsoft Defender for Endpoint

Investigate alerts that are affecting your network, understand what they mean, and how to resolve them.

Select an alert from the alerts queue to go to alert page. This view contains the alert title, the affected assets, the details side pane, and the alert story.

From the alert page, begin your investigation by selecting the affected assets or any of the entities under the alert story tree view. The details pane automatically populates with further information about what you selected. To see what kind of information you can view here, read [Review alerts in Microsoft Defender for Endpoint](https://learn.microsoft.com/en-us/defender-endpoint/review-alerts).

## Investigate using the alert story

The alert story details why the alert was triggered, related events that happened before and after, as well as other related entities.

Entities are clickable and every entity that isn't an alert is expandable using the expand icon on the right side of that entity's card. The entity in focus will be indicated by a blue stripe to the left side of that entity's card, with the alert in the title being in focus at first.

Expand entities to view details at a glance. Selecting an entity will switch the context of the details pane to this entity, and will allow you to review further information, as well as manage that entity. Selecting *...* to the right of the entity card will reveal all actions available for that entity. These same actions appear in the details pane when that entity is in focus.

Note

The alert story section may contain more than one alert, with additional alerts related to the same execution tree appearing before or after the alert you've selected.

[![an alert story with an alert in focus and some expanded cards](https://learn.microsoft.com/en-us/defender-endpoint/media/alert-story-tree.png)](https://learn.microsoft.com/en-us/defender-endpoint/media/alert-story-tree.png#lightbox)

## Investigate using the alert timeline

The alert timeline complements the existing 'process tree' view by offering users a comprehensive perspective on each alert. While the process tree provides a detailed breakdown of the alert's associated processes and activities, the alert timeline presents a condensed chronological view that facilitates rapid triage and decision-making.

## Take action from the details pane

Once you've selected an entity of interest, the details pane will change to display information about the selected entity type, historic information when it's available, and offer controls to **take action** on this entity directly from the alert page.

Once you're done investigating, go back to the alert you started with, mark the alert's status as **Resolved** and classify it as either **False alert** or **True alert**. Classifying alerts helps tune this capability to provide more true alerts and less false alerts.

If you classify it as a true alert, you can also select a determination, as shown in the image below.

[![The details pane with a resolved alert and the determination drop-down expanded](https://learn.microsoft.com/en-us/defender-endpoint/media/alert-details-resolved-true.png)](https://learn.microsoft.com/en-us/defender-endpoint/media/alert-details-resolved-true.png#lightbox)

If you are experiencing a false alert with a line-of-business application, create a suppression rule to avoid this type of alert in the future.

[![The actions and classification in the details pane with the suppression rule highlighted](https://learn.microsoft.com/en-us/defender-endpoint/media/alert-false-suppression-rule.png)](https://learn.microsoft.com/en-us/defender-endpoint/media/alert-false-suppression-rule.png#lightbox)

Tip

If you're experiencing any issues not described above, use the 🙂 button to provide feedback or open a support ticket.

## Related topics

- [View and organize the Microsoft Defender for Endpoint Alerts queue](https://learn.microsoft.com/en-us/defender-endpoint/alerts-queue)
- [Manage Microsoft Defender for Endpoint alerts](https://learn.microsoft.com/en-us/defender-xdr/investigate-alerts?toc=/defender-endpoint/toc.json&bc=/defender-endpoint/breadcrumb/toc.json#manage-alerts)
- [Investigate a file associated with a Defender for Endpoint alert](https://learn.microsoft.com/en-us/defender-endpoint/investigate-files)
- [Investigate devices in the Defender for Endpoint Devices list](https://learn.microsoft.com/en-us/defender-endpoint/investigate-machines)
- [Investigate an IP address associated with a Defender for Endpoint alert](https://learn.microsoft.com/en-us/defender-endpoint/investigate-ip)
- [Investigate a domain associated with a Defender for Endpoint alert](https://learn.microsoft.com/en-us/defender-endpoint/investigate-domain)
- [Investigate a user account in Defender for Endpoint](https://learn.microsoft.com/en-us/defender-endpoint/investigate-user)
