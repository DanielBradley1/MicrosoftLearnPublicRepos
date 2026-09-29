<!-- Source: https://learn.microsoft.com/en-us/defender-endpoint/information-protection-investigation -->
<!-- Sitemap-Last-Modified: 2026-07-15 -->

# Microsoft Defender for Endpoint sensitivity labels protect and prioritize incident response

A typical advanced persistent threat \(APT\) lifecycle involves data exfiltration, where data is *taken* from the organization. Sensitivity labels help security teams know where to start. They show which data has the highest priority to protect.

Defender for Endpoint uses sensitivity labels to simplify how you prioritize security incidents. For example, labels help you quickly spot incidents that involve devices with sensitive or confidential information.

Here's how to use sensitivity labels in Defender for Endpoint.

## Investigate incidents that involve sensitive data on devices with Defender for Endpoint

Learn how to use data sensitivity labels to prioritize incident investigation.

Note

Labels are detected for Windows 10, version 1809 or later, and Windows 11.

1. In Microsoft Defender portal, select **Incidents & alerts** > **Incidents**.
2. Scroll over to see the **Data sensitivity** column. This column shows the sensitivity labels found on devices related to each incident. Use it to check whether sensitive files are affected.

   [![The Highly confidential option in the data sensitivity column](https://learn.microsoft.com/en-us/defender-endpoint/media/data-sensitivity-column.png)](https://learn.microsoft.com/en-us/defender-endpoint/media/data-sensitivity-column.png#lightbox)

   You can also filter based on **Data sensitivity**

   [![The data sensitivity filter](https://learn.microsoft.com/en-us/defender-endpoint/media/data-sensitivity-filter.png)](https://learn.microsoft.com/en-us/defender-endpoint/media/data-sensitivity-filter.png#lightbox)
3. Open the incident page to further investigate.

   [![The incident page details](https://learn.microsoft.com/en-us/defender-endpoint/media/incident-page.png)](https://learn.microsoft.com/en-us/defender-endpoint/media/incident-page.png#lightbox)
4. Select the **Devices** tab to identify devices storing files with sensitivity labels.

   [![The Device tab](https://learn.microsoft.com/en-us/defender-endpoint/media/investigate-devices-tab.png)](https://learn.microsoft.com/en-us/defender-endpoint/media/investigate-devices-tab.png#lightbox)
5. Select the devices that store sensitive data. Search the timeline to find which files might be affected. Then take action to protect that data.

   To narrow the results, search the device timeline for a specific sensitivity label. Only events for files that match that label name appear.

   [![The device timeline with narrowed down search results based on label](https://learn.microsoft.com/en-us/defender-endpoint/media/machine-timeline-labels.png)](https://learn.microsoft.com/en-us/defender-endpoint/media/machine-timeline-labels.png#lightbox)

Tip

Sensitivity label and file protection status data are also exposed through the 'DeviceFileEvents' in advanced hunting, allowing advanced queries and schedule detection to take into account sensitivity labels and file protection status.

## Related information about sensitivity labels

For more details about sensitivity labels, see the following articles:

- [Learn about sensitivity labels in Office 365](https://learn.microsoft.com/en-us/purview/sensitivity-labels)
- [Apply sensitivity labels in email or Office apps](https://support.microsoft.com/Office/security-privacy/apply-sensitivity-labels-to-your-files)
- [Use sensitivity labels as a condition in Data Loss Prevention policies](https://learn.microsoft.com/en-us/purview/dlp-sensitivity-label-as-condition)
