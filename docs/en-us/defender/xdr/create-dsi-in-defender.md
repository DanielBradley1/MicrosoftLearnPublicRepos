<!-- Source: https://learn.microsoft.com/en-us/defender-xdr/create-dsi-in-defender -->
<!-- Sitemap-Last-Modified: 2026-06-24 -->

# Create investigations in Data Security Investigations \(preview\) from the Microsoft Defender portal

Important

Some information in this article relates to a prereleased product which may be substantially modified before it's commercially released. Microsoft makes no warranties, expressed or implied, with respect to the information provided here.

You can now start an investigation on data security incidents from the Microsoft Defender portal with the integration of [Microsoft Purview Data Security Investigations \(preview\)](https://learn.microsoft.com/en-us/purview/data-security-investigations) and Microsoft Defender XDR.

Security operations center \(SOC\) teams can take advantage of the integration between Microsoft Purview Data Security Investigations \(preview\) and Microsoft Defender XDR to enhance their investigation and response to potential data security incidents like data breaches or data leaks. Data Security Investigations \(preview\) uses generative AI to analyze impacted data, draws connections to identify risks, and provide actionable insights to protect your organization.

SOC teams can start an investigation in Data Security Investigations \(preview\) from an incident page where a potentially affected data set is in the Microsoft Defender portal.

## Prerequisites

To create investigations in Data Security Investigations \(preview\) in the Microsoft Defender portal, you must have the following permissions:

- Security Administrator
- Security Operator

To view and access the investigation in Data Security Investigations \(preview\) in the Microsoft Purview portal, the *Data Security Investigations Administrator* [Data Security Investigations permissions](https://learn.microsoft.com/en-us/purview/data-security-investigations-permissions) role is required.

## Create a data security investigation

Microsoft Defender XDR identifies possibly impacted sensitive data in incidents. You can start creating an investigation in Data Security Investigations \(preview\) from the incident page in the Microsoft Defender portal. Investigations support mailboxes, files, and mail messages as the scope of the investigation.

To create an investigation in Data Security Investigations \(preview\) in the Microsoft Defender portal, follow these steps:

1. Sign in to the [Microsoft Defender portal](https://security.microsoft.com).
2. In the navigation pane, select **Investigation & response** > **Incidents & alerts** > **Incidents** to open the incident queue. Select an incident from the queue to open the incident page.
3. When the selected incident contains potentially impacted data, the option to create a Data Security investigation appears on the incident page message banner. Choose **Investigate this incident**.

   <span class="mx-imgBorder">
   <a href="https://learn.microsoft.com/en-us/defender-xdr/media/create-dsi-in-defender/xdr-dsi-banner.png#lightbox" data-linktype="relative-path">
   <img src="https://learn.microsoft.com/en-us/defender-xdr/media/create-dsi-in-defender/xdr-dsi-banner-small.png" alt="Screenshot of the incident page highlighting the create investigation message banner" data-linktype="relative-path">
   </a>
   </span>

4. In the pop-up window, provide a name and description for the investigation. Investigation names must be unique.

   <span class="mx-imgBorder">
   <a href="https://learn.microsoft.com/en-us/defender-xdr/media/create-dsi-in-defender/xdr-dsi-popup.png#lightbox" data-linktype="relative-path">
   <img src="https://learn.microsoft.com/en-us/defender-xdr/media/create-dsi-in-defender/xdr-dsi-popup-small.png" alt="Screenshot of the Data Security investigations pop-up window" data-linktype="relative-path">
   </a>
   </span>

5. In the Investigation scope, attach mailboxes or files and mail messages to the investigation.

   Note

   You can attach either mailboxes or files and mail messages in an investigation, but not both at the same time. If an incident involves both mailboxes and files or mail messages, you need to create separate investigations. For example, create one investigation for all mailboxes and another for all files and mail messages. Files and mail messages can be attached in one investigation.
6. Select **Create investigation** to finish creating the data security investigation.

Once the investigation in Data Security Investigations \(preview\) is created, a link to the Microsoft Purview portal appears on the message banner in the incident page. Here’s an example.

[![Screenshot highlighting the link to Microsoft Purview portal after successful creation](https://learn.microsoft.com/en-us/defender-xdr/media/create-dsi-in-defender/xdr-dsi-success-link-small.png)](https://learn.microsoft.com/en-us/defender-xdr/media/create-dsi-in-defender/xdr-dsi-success-link.png#lightbox)

You can also create an investigation in Data Security Investigations \(preview\) from the incident page in the following ways:

- From the **Incidents** page, select the **More actions** ellipsis to see the options, then choose **Investigate data security with AI**.

  [![Screenshot highlighting the Create Data Security investigation option from the more actions ellipsis](https://learn.microsoft.com/en-us/defender-xdr/media/create-dsi-in-defender/xdr-dsi-create-action-small.png)](https://learn.microsoft.com/en-us/defender-xdr/media/create-dsi-in-defender/xdr-dsi-create-action.png#lightbox)
- When you select an entity like an email in the incident graph, choose **Investigate data security with AI** from the entity context menu.

  [![Screenshot highlighting the Create Data Security investigation option from an entity in the incident graph](https://learn.microsoft.com/en-us/defender-xdr/media/create-dsi-in-defender/xdr-dsi-create-entity-small.png)](https://learn.microsoft.com/en-us/defender-xdr/media/create-dsi-in-defender/xdr-dsi-create-entity.png#lightbox)

Each investigation in Data Security Investigations \(preview\) created is recorded in the Microsoft Defender portal activity log. The activity log entry also includes the relevant link to the investigation created in the Microsoft Purview portal.

[![Screenshot highlighting the link to Microsoft Purview portal in the activity log](https://learn.microsoft.com/en-us/defender-xdr/media/create-dsi-in-defender/xdr-dsi-activity-log-small.png)](https://learn.microsoft.com/en-us/defender-xdr/media/create-dsi-in-defender/xdr-dsi-activity-log.png#lightbox)

## Next step

[Manage the investigation scope in Microsoft Purview Data Security Investigations \(preview\)](https://learn.microsoft.com/en-us/purview/data-security-investigations-scope)
