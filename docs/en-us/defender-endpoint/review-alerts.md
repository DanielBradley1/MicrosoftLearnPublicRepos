<!-- Source: https://learn.microsoft.com/en-us/defender-endpoint/review-alerts -->
<!-- Sitemap-Last-Modified: 2026-07-29 -->

# Review alerts in Microsoft Defender for Endpoint

The alert page in Microsoft Defender for Endpoint provides full context to the alert, by combining attack signals and alerts related to the selected alert, to construct a detailed alert story.

Quickly triage, investigate, and take effective action on alerts that affect your organization. Understand why the alerts were triggered, and their impact from one location. Learn more about alerts in [Investigate alerts in Microsoft Defender for Endpoint](https://learn.microsoft.com/en-us/defender-endpoint/investigate-alerts).

<iframe src="https://learn-video.azurefd.net/vod/player?id=8a9c08a6-558c-47a8-a336-d748acbdaa80" allowfullscreen="true" data-linktype="external" frameborder="0"></iframe>

## Getting started with an alert

Selecting an alert's name in Defender for Endpoint will land you on the alert's page. On the alert page, all the information will be shown in context of the selected alert. Each alert page consists of 4 sections:

1. **The alert title** shows the alert's name and is there to remind you which alert started your current investigation regardless of what you have selected on the page.
2. [**Affected assets**](#review-affected-assets) lists cards of devices and users affected by this alert that are clickable for further information and actions.
3. The **alert story** displays all entities related to the alert, interconnected by a tree view. The alert in the title will be the one in focus when you first land on your selected alert's page. Entities in the alert story are expandable and clickable, to provide additional information and expedite response by allowing you to take actions right in the context of the alert page. Use the alert story to start your investigation. Learn how in [Investigate alerts in Microsoft Defender for Endpoint](https://learn.microsoft.com/en-us/defender-endpoint/investigate-alerts).
4. The **details pane** will show the details of the selected alert at first, with details and actions related to this alert. If you select any of the affected assets or entities in the alert story, the details pane will change to provide contextual information and actions for the selected object.

Note the detection status for your alert.

- Prevented: The attempted suspicious action was avoided. For example, a file either wasn't written to disk or executed.

  [![The page showing the prevention of a threat](https://learn.microsoft.com/en-us/defender-endpoint/media/detstat-prevented.png)](https://learn.microsoft.com/en-us/defender-endpoint/media/detstat-prevented.png#lightbox)
- Blocked: Suspicious behavior was executed and then blocked. For example, a process was executed but because it subsequently exhibited suspicious behaviors, the process was terminated.

  [![The page showing the blockage of a threat](https://learn.microsoft.com/en-us/defender-endpoint/media/detstat-blocked.png)](https://learn.microsoft.com/en-us/defender-endpoint/media/detstat-blocked.png#lightbox)
- Detected: An attack was detected and is possibly still active.

  [![The page showing the detection of a threat](https://learn.microsoft.com/en-us/defender-endpoint/media/detstat-detected.png)](https://learn.microsoft.com/en-us/defender-endpoint/media/detstat-detected.png#lightbox)

You can then also review the *automated investigation details* in your alert's details pane, to see which actions were already taken, as well as reading the alert's description for recommended actions.

[![The details pane with the alert description and automatic investigation sections highlighted](https://learn.microsoft.com/en-us/defender-endpoint/media/alert-air-and-alert-description.png)](https://learn.microsoft.com/en-us/defender-endpoint/media/alert-air-and-alert-description.png#lightbox)

Other information available in the details pane when the alert opens includes MITRE techniques, source, and additional contextual details.

Note

If you see an *Unsupported alert type* alert status, it means that automated investigation capabilities cannot pick up that alert to run an automated investigation. However, you can [investigate these alerts manually](https://learn.microsoft.com/en-us/defender-xdr/investigate-incidents#alerts).

## Review affected assets

Selecting a device or a user card in the Affected assets section will switch to the details of the device or user in the details pane.

- **For devices**, the details pane will display information about the device itself, like Domain, Operating System, and IP. Active alerts and the logged on users on that device are also available. You can take immediate action by isolating the device, restricting app execution, or running an antivirus scan. Alternatively, you could collect an investigation package, initiate an automated investigation, or go to the device page to investigate from the device's point of view.

  [![The details pane when a device is selected](https://learn.microsoft.com/en-us/defender-endpoint/media/device-page-details.png)](https://learn.microsoft.com/en-us/defender-endpoint/media/device-page-details.png#lightbox)
- **For users**, the details pane will display detailed user information, such as the user's SAM name and SID, as well as logon types performed by this user and any alerts and incidents related to that user. You can select *Open user page* to continue the investigation from that user's point of view.

  [![The details pane when a user is selected](https://learn.microsoft.com/en-us/defender-endpoint/media/user-page-details.png)](https://learn.microsoft.com/en-us/defender-endpoint/media/user-page-details.png#lightbox)

## Related content

- [View and organize the incidents queue](https://learn.microsoft.com/en-us/defender-endpoint/view-incidents-queue)
- [Investigate incidents](https://learn.microsoft.com/en-us/defender-endpoint/investigate-incidents)
- [Manage incidents](https://learn.microsoft.com/en-us/defender-endpoint/manage-incidents)
