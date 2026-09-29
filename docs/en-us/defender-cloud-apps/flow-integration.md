<!-- Source: https://learn.microsoft.com/en-us/defender-cloud-apps/flow-integration -->
<!-- Sitemap-Last-Modified: 2026-07-03 -->

# Integrate with Microsoft Power Automate for custom alert automation

Defender for Cloud Apps integrates with [Microsoft Power Automate](https://learn.microsoft.com/en-us/power-automate/getting-started) to provide custom alert automation and orchestration playbooks. By using the [Power Automate connectors](https://learn.microsoft.com/en-us/connectors/) available in Power Automate, you can automate the triggering of playbooks when Defender for Cloud Apps generates alerts. For example, automatically create an issue in ticketing systems using [ServiceNow connector](https://learn.microsoft.com/en-us/connectors/service-now/) or send an approval email to execute a custom governance action when an alert is triggered in Defender for Cloud Apps. Before you begin, make sure you meet the [prerequisites](#prerequisites).

## Prerequisites

Before you create playbooks, make sure you meet the following prerequisites:

- You must have a valid [Microsoft Power Automate plan](https://flow.microsoft.com/pricing/)
- [Create an API token](https://learn.microsoft.com/en-us/defender-cloud-apps/api-tokens-legacy) in Defender for Cloud Apps.

## How it works

On its own, Defender for Cloud Apps provides predefined governance options such as suspend a user or make a file private when defining policies. By creating a playbook in Power Automate using a Defender for Cloud Apps connector, you can create workflows to enable customized governance options for your policies. After the playbook is created in Power Automate, it will be automatically synchronized to Defender for Cloud Apps. Then associate the playbook with a policy in Defender for Cloud Apps to send alerts to Power Automate. Microsoft Power Automate offers several connectors and conditions to create a customized workflow for your organization.

The [Defender for Cloud Apps connector](https://learn.microsoft.com/en-us/connectors/cloudappsecurity/) in Power Automate supports automated triggers and actions. Power Automate is triggered automatically when Defender for Cloud Apps generates an alert. Actions include changing the alert status in Defender for Cloud Apps.

## Create Power Automate playbooks for Defender for Cloud Apps

Perform the following steps to create a Power Automate playbook for Defender for Cloud Apps:

1. [Create an API token](https://learn.microsoft.com/en-us/defender-cloud-apps/api-tokens-legacy) in Defender for Cloud Apps.
2. Navigate to the [Power Automate portal](https://flow.microsoft.com/), select **My flows**, select **New flow**, and in the drop-down, under **Build your own from blank**, select **Automated cloud flow**.

   ![Screenshot of the Power Automate portal showing the create new flow option.](https://learn.microsoft.com/en-us/defender-cloud-apps/media/flow-create-new.png)

3. Provide a name for the flow, and in **Choose your flow's trigger**, type *Defender for Cloud Apps* and select **When an alert is generated**.

   ![Screenshot of the Power Automate trigger configuration selecting When an alert is generated for Defender for Cloud Apps.](https://learn.microsoft.com/en-us/defender-cloud-apps/media/flow-when-alert.png)

4. Under **Authentication settings**, paste the Defender for Cloud Apps API token you created in step 1. Give your connection a name and select **Create**.

   ![Screenshot of the Power Automate authentication settings where the API token is pasted to create a connection.](https://learn.microsoft.com/en-us/defender-cloud-apps/media/add-token.png)

5. Now create the playbook according to your requirements. Select **+New step** to define the workflow that should be triggered when a policy in Defender for Cloud Apps generates an alert. You can add an action, logical condition, switch case conditions, or loops and save the playbook. In this example, we'll be adding a [ServiceNow connector](https://learn.microsoft.com/en-us/connectors/service-now/).

   ![Screenshot of the Power Automate workflow showing the alert trigger and configured ServiceNow connector action.](https://learn.microsoft.com/en-us/defender-cloud-apps/media/flow-workflow.png)

6. Continue to configure your playbook. The playbook will be automatically synchronized with Defender for Cloud Apps. For more information about creating cloud flows in Power Automate, see [Create a cloud flow in Power Automate](https://learn.microsoft.com/en-us/power-automate/get-started-logic-flow).
7. In the Microsoft Defender Portal, under **Cloud Apps**, go to **Policies** -> **Policy management**. In the row of the policy whose alerts you want to forward to Power Automate, select the three dots and then select **Edit Policy**.
8. Under **Alerts**, select **Send Alerts to Power Automate** and choose the name of your Power Automate playbook from the drop-down menu.

   ![Screenshot of policy Alerts settings with Send Alerts to Power Automate enabled and a playbook selected.](https://learn.microsoft.com/en-us/defender-cloud-apps/media/flow-alerts-config.png)

9. Defender for Cloud Apps playbooks that you've authored or are granted access to can be seen by in the Microsoft Defender Portal, by going to **Settings**, then choosing **Cloud Apps**, and under **System** selecting **Playbooks**.

   ![Screenshot of the Microsoft Defender Portal Settings, Cloud Apps, System, Playbooks page listing available playbooks.](https://learn.microsoft.com/en-us/defender-cloud-apps/media/flow-extensions.png)

Note

The maximum supported number of Power Platform environments is 80, but there is no limit to the number of playbooks that can be used within each environment.

## Next steps

[Control cloud apps with policies](https://learn.microsoft.com/en-us/defender-cloud-apps/control-cloud-apps-with-policies)

If you run into any problems, we're here to help. To get assistance or support for your product issue, please [open a support ticket](https://learn.microsoft.com/en-us/defender-xdr/contact-defender-support).

## Related content

Use the following resource to learn more about alert automation:

- Try our interactive guide: [Automate alerts management with Microsoft Power Automate and Defender for Cloud Apps](https://mslearn.cloudguides.com/guides/Automate%20alerts%20management%20with%20Microsoft%20Power%20Automate%20and%20Cloud%20App%20Security)
