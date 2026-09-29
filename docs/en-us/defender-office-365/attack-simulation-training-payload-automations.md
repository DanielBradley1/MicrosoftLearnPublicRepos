<!-- Source: https://learn.microsoft.com/en-us/defender-office-365/attack-simulation-training-payload-automations -->
<!-- Sitemap-Last-Modified: 2026-07-03 -->

# Payload automations for Attack simulation training

Tip

*Did you know you can try the features in Microsoft Defender for Office 365 Plan 2 for free?* Use the 90-day Defender for Office 365 trial at the [Microsoft Defender portal trials hub](https://security.microsoft.com/trialHorizontalHub?sku=MDO&ref=DocsRef). Learn about who can sign up and trial terms on [Try Microsoft Defender for Office 365](https://learn.microsoft.com/en-us/defender-office-365/try-microsoft-defender-for-office-365).

In Attack simulation training in Microsoft 365 E5 or Microsoft Defender for Office 365 Plan 2, payload automations \(also known as *payload harvesting*\) collect information from real-world phishing attacks that were reported by users in your organization. You can specify the conditions to look for in phishing attacks \(for example, recipients, social engineering technique, or sender information\).

Payload automation mimics the messages and payloads from the attack and stores them as custom payloads with identifiers in the payload name. You can then use the harvested payloads in simulations or automations to automatically launch harmless simulations to targeted users.

Payload automations rely on email messages that Defender for Office 365 identifies as phishing campaigns. Eligible payloads are harvested from user-reported messages that were delivered to the Inbox, reported as phishing, and confirmed as phishing by Microsoft. For more details, see [How payload automations collect payloads](#appendix).

For getting started information about Attack simulation training, see [Get started using Attack simulation training](https://learn.microsoft.com/en-us/defender-office-365/attack-simulation-training-get-started).

To see any existing payload automations that you created, open the Microsoft Defender portal at [https://security.microsoft.com](https://security.microsoft.com), go to **Email & collaboration** > **Attack simulation training** > **Automations** tab, then select **Payload automations**. To go directly to the **Automations** tab where you can select **Payload automations**, use [https://security.microsoft.com/attacksimulator?viewid=automations](https://security.microsoft.com/attacksimulator?viewid=automations).

The following information is shown for each payload automation. You can sort the payload automations by clicking on an available column header.

- **Automation name**
- **Type**: The value is **Payload**.
- **Items collected**
- **Last modified**
- **Status**: The value is **Ready** or **Draft**.

Tip

To see all columns, you likely need to do one or more of the following steps:

- Horizontally scroll in your web browser.
- Narrow the width of appropriate columns.
- Remove columns from the view.
- Zoom out in your web browser.

## Create payload automations

To create a payload automation, do the following steps:

1. In the Microsoft Defender portal at [https://security.microsoft.com/](https://security.microsoft.com/), go to **Email & collaboration** > **Attack simulation training** > **Automations** tab > **Payload automations**. To go directly to the **Automations** tab where you can select **Payload automations**, use [https://security.microsoft.com/attacksimulator?viewid=automations](https://security.microsoft.com/attacksimulator?viewid=automations).
2. On the **Payload automations** page, select ![](https://learn.microsoft.com/en-us/defender-office-365/media/defender-portal-icon-create.png) **Create automation** to start the new payload automation wizard.

   [![The Create simulation button on the Payload automations tab in Attack simulation training in the Microsoft Defender portal](https://learn.microsoft.com/en-us/defender-office-365/media/attack-sim-training-sim-automations-create.png)](https://learn.microsoft.com/en-us/defender-office-365/media/attack-sim-training-sim-automations-create.png#lightbox)

   Note

   At any point after you name the payload automation during the new payload automation wizard, you can select **Save and close** to save your progress and continue configuring the payload automation later. The incomplete payload automation has the **Status** value **Draft** in **Payload automations** on the **Automations** tab. You can pick up where you left off by selecting the payload automation and clicking ![](https://learn.microsoft.com/en-us/defender-office-365/media/defender-portal-icon-edit.png) **Edit automation**.

   Currently, payload harvesting isn't enabled in GCC environments due to data gathering restrictions.
3. On the **Automation name** page, configure the following settings:

   - **Name**: Enter a unique, descriptive name for the payload automation.
   - **Description**: Enter an optional detailed description for the payload automation.


   When you're finished on the **Automation name** page, select **Next**.

4. On the **Run conditions** page, select the conditions of the real phishing attack that determines when the automation runs.

   Select ![](https://learn.microsoft.com/en-us/defender-office-365/media/defender-portal-icon-create.png) **Add condition** and then select from one of the following conditions:

   - **No. of users targeted in the campaign**: In the boxes that appear, configure the following settings:

     - **Equal to**, **Less than**, **Greater than**, **Less than or equal to**, or **Greater than or equal to**.
     - **Enter value**: The number of users that were targeted by the phishing campaign.

   - **Campaigns with a specific phish technique**: In the box that appears, select one of the available values:

     - **Credential Harvest**
     - **Malware Attachment**
     - **Link in Attachment**
     - **Link to Malware**
     - **How-to Guide**

   - **Specific sender domain**: In the box that appears, enter a sender email domain value \(for example, contoso.com\).
   - **Specific sender name**: In the box that appears, enter a sender name value.
   - **Specific sender email**: In the box that appears, enter a sender email address.
   - **Specific user and group recipients**: In the box that appears, start typing the name or email address of the user or group. When it appears, select it.


   You can use each condition only once. Multiple conditions use AND logic \(<Condition1> and <Condition2>\).


   To add another condition, select ![](https://learn.microsoft.com/en-us/defender-office-365/media/defender-portal-icon-create.png) **Add condition**.


   To remove a condition after you add it, select ![](https://learn.microsoft.com/en-us/defender-office-365/media/defender-portal-icon-delete.png) .


   When you're finished on the **Run conditions** page, select **Next**.

5. On the **Review automation** page, you can review the details of your payload automation.

   You can select **Edit** in each section to modify the settings within the section. Or you can select **Back** or the specific page in the wizard.

   When you're finished on the **Review automation** page, select **Submit**.
6. On the **New automation created** page, you can use the links to turn on the payload automation or go to the **Simulations** page.

   When you're finished, select **Done**.
7. Back on **Payload automations** in the **Automations** tab, the payload automation that you created is now listed with the **Status** value **Ready**.

## Turn payload automations on or off

You can turn on or turn off payload automations with the **Status** value **Ready**. You can't turn on or turn off incomplete payload automations with the **Status** value **Draft**.

To turn on a payload automation, select it from the list by clicking the check box next to the name. Select the ![](https://learn.microsoft.com/en-us/defender-office-365/media/defender-portal-icon-turn-on-off.png) **Turn on** action that appears, and then select **Confirm** in the dialog.

To turn off a payload automation, select it from the list by clicking the check box next to the name. Select the ![](https://learn.microsoft.com/en-us/defender-office-365/media/defender-portal-icon-turn-on-off.png) **Turn off** action that appears, and then select **Confirm** in the dialog.

## Modify payload automations

You can only modify payload automations with the **Status** value **Draft** or that are turned off.

To modify an existing payload automation on the **Payload automations** page, do one of the following steps:

- Select the payload automation from the list by selecting the check box next to the name. Select the ![](https://learn.microsoft.com/en-us/defender-office-365/media/defender-portal-icon-edit.png) **Edit automation** action that appears.
- Select the payload automation from the list by clicking anywhere in the row except the check box. In the details flyout that opens, on the **General** tab, select **Edit** in the **Name**, **Description**, or **Run conditions** sections.

The payload automation wizard opens with the settings and values of the selected payload automation. The wizard uses the same pages: **Automation name** \(name and description\), **Run conditions** \(phishing attack criteria\), and **Review automation** \(review and submit\). For detailed descriptions of each page, see [Create payload automations](#create-payload-automations).

## Remove payload automations

Warning

You can't undo this action. When you delete a payload automation, all collected payloads and run history for that automation are also deleted.

To remove a payload automation, select it from the list by selecting the check box. Select the ![](https://learn.microsoft.com/en-us/defender-office-365/media/defender-portal-icon-delete.png) **Delete** action that appears, then select **Confirm** in the dialog.

## View payload automation details

To view details, the payload automation must have the **Status** value **Ready**. On the **Payload automations** page, click anywhere in the row other than the check box. A details flyout opens with the following information:

- The automation name and the number of items collected.
- **General** tab:

  - **Last modified**
  - **Type**: The value is **Payload**.
  - **Name**, **Description**, and **Run conditions** sections: Select **Edit** to open the wizard for that page.

- **Run history** tab: Available only when **Status** is **Ready**.

  Shows the run history of simulations that used this automation.

  [![The Run history tab in the details flyout of a payload automation.](https://learn.microsoft.com/en-us/defender-office-365/media/attack-sim-training-payload-automations-details-run-history.png)](https://learn.microsoft.com/en-us/defender-office-365/media/attack-sim-training-payload-automations-details-run-history.png#lightbox)

Tip

To see details about other payload automations without leaving the details flyout, use ![](https://learn.microsoft.com/en-us/defender-office-365/media/updownarrows.png) **Previous item** and **Next item** at the top of the flyout.

## Appendix: How payload automations collect payloads

Payload automation relies on email messages that are identified as campaigns by Defender for Office 365:

- Admins [marking messages as phishing](https://learn.microsoft.com/en-us/defender-office-365/submissions-admin#notify-users-about-admin-submitted-messages-to-microsoft) doesn't result in payload harvesting.
- Payload automation needs access to the raw payload. The raw payload is the original email content, including headers, body, links, and attachments. Raw payloads come from user reported messages that meet the following criteria:

  - The message was delivered to the Inbox \(false negative\).
  - The user reported the message as phishing.
  - The message was sent to Microsoft \(by the user or [by an admin from the Submissions portal](https://learn.microsoft.com/en-us/defender-office-365/submissions-admin#submit-user-reported-messages-to-microsoft-for-analysis)\). Microsoft then confirmed the message was phishing.

- Payloads are harvested when messages meet the run conditions set for the automation. Examples include number of targeted users, phishing technique, sender domain, or specific recipients. For details, see Step 4 in [Create payload automations](#create-payload-automations).

## Related content

- [Get started using Attack simulation training](https://learn.microsoft.com/en-us/defender-office-365/attack-simulation-training-get-started)
- [Simulation automations for Attack simulation training](https://learn.microsoft.com/en-us/defender-office-365/attack-simulation-training-simulation-automations)
- [Reports for Attack simulation training](https://learn.microsoft.com/en-us/defender-office-365/attack-simulation-training-insights)
