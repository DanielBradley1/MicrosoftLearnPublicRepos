<!-- Source: https://learn.microsoft.com/en-us/defender-endpoint/api-microsoft-flow -->
<!-- Sitemap-Last-Modified: 2026-07-29 -->

# Use the Power Automate connector to create an event flow

Automating security procedures is a standard requirement for every modern Security Operations Center \(SOC\). For SOC teams to operate in the most efficient way, automation is a must. Use Microsoft Power Automate to help you create automated workflows and build an end-to-end procedure automation within a few minutes. Microsoft Power Automate supports different connectors that were built exactly for automating security workflows.

Use this guide to create event-triggered automations in Power Automate, such as workflows that run when a new alert is created in your tenant. Microsoft Defender API has an official Power Automate Connector with many capabilities.

[![The Actions page in the Microsoft Defender 365 portal](https://learn.microsoft.com/en-us/defender-endpoint/media/api-flow-0.png)](https://learn.microsoft.com/en-us/defender-endpoint/media/api-flow-0.png#lightbox)

Note

For more information about premium connectors licensing prerequisites, see [Licensing for premium connectors](https://learn.microsoft.com/en-us/power-automate/triggers-introduction#licensing-for-premium-connectors).

## Example: Create an event-triggered flow

This example demonstrates how to create a flow that is triggered whenever a new alert occurs on your tenant. You'll define what event starts the flow and which follow-up action the flow takes when the trigger occurs.

1. Log in to [Microsoft Power Automate](https://make.powerautomate.com).
2. Go to **My flows** > **New** > **Automated-from blank**.

   a.  [![The New flow pane under My flows menu item in the Microsoft Defender 365 portal](https://learn.microsoft.com/en-us/defender-endpoint/media/api-flow-1.png)](https://learn.microsoft.com/en-us/defender-endpoint/media/api-flow-1.png#lightbox)
3. Choose a name for your Flow, search for "Microsoft Defender ATP Triggers" as the trigger, and then select the new Alerts trigger.

   [![The Choose your flow's trigger section in the Microsoft Defender 365 portal](https://learn.microsoft.com/en-us/defender-endpoint/media/api-flow-2.png)](https://learn.microsoft.com/en-us/defender-endpoint/media/api-flow-2.png#lightbox)

   Now you have a Flow that is triggered every time a new Alert occurs.

   [![A trigger description](https://learn.microsoft.com/en-us/defender-endpoint/media/api-flow-3.png)](https://learn.microsoft.com/en-us/defender-endpoint/media/api-flow-3.png#lightbox)

   Next, add actions to retrieve alert details and define the automated response. For example, you can isolate the device if the Severity of the Alert is High and send an email about the alert. The Alert trigger provides only the Alert ID and the Machine ID. You can use the Microsoft Defender ATP connector to expand these entities.

### Get the Alert entity using the connector

Perform the following steps to retrieve the full Alert entity by using the connector:

1. Choose **Microsoft Defender ATP** for the new step.
2. Choose **Alerts - Get single alert API**.
3. Set the **Alert ID** from the last step as **Input**.

   [![The Alerts pane](https://learn.microsoft.com/en-us/defender-endpoint/media/api-flow-4.png)](https://learn.microsoft.com/en-us/defender-endpoint/media/api-flow-4.png#lightbox)

### Isolate the device if the Alert's severity is High

Use the following steps to isolate the device when the alert severity is High:

1. Add **Condition** as a new step.
2. Check if the Alert severity **is equal to** High.

   If yes, add the **Microsoft Defender ATP - Isolate machine** action with the Machine ID and a comment.

   [![The Actions pane](https://learn.microsoft.com/en-us/defender-endpoint/media/api-flow-5.png)](https://learn.microsoft.com/en-us/defender-endpoint/media/api-flow-5.png#lightbox)
3. Add a new step for emailing about the Alert and the Isolation. There are multiple email connectors that are easy to use, such as Outlook or Gmail.
4. Save your flow.

   You can also create a **scheduled** flow that runs Advanced Hunting queries and much more!

## Related content

- [Supported operating systems and platforms for Defender Vulnerability Management](https://learn.microsoft.com/en-us/defender-vulnerability-management/tvm-supported-os)
