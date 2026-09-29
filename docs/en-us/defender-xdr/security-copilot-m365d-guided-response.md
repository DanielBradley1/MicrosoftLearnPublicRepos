<!-- Source: https://learn.microsoft.com/en-us/defender-xdr/security-copilot-m365d-guided-response -->
<!-- Sitemap-Last-Modified: 2024-11-18 -->

# Triage and investigate incidents with guided responses from Microsoft Copilot in Microsoft Defender

[Microsoft Security Copilot](https://learn.microsoft.com/en-us/security-copilot/microsoft-security-copilot) in the Microsoft Defender portal supports incident response teams in immediately resolving incidents with guided responses. Copilot in Defender uses AI and machine learning capabilities to contextualize an incident and learn from previous investigations to generate appropriate response actions.

This guide outlines how to access the guided response capability, including information on providing feedback about the responses.

## Know before you begin

If you're new to Security Copilot, you should familiarize yourself with it by reading the following articles:

- [What is Security Copilot?](https://learn.microsoft.com/en-us/security-copilot/microsoft-security-copilot)
- [Security Copilot experiences](https://learn.microsoft.com/en-us/security-copilot/experiences-security-copilot)
- [Get started with Security Copilot](https://learn.microsoft.com/en-us/security-copilot/get-started-security-copilot)
- [Understand authentication in Security Copilot](https://learn.microsoft.com/en-us/security-copilot/authentication)
- [Prompting in Security Copilot](https://learn.microsoft.com/en-us/security-copilot/prompting-security-copilot)

Responding to incidents in the Microsoft Defender portal often requires familiarity with the portal's available actions to stop attacks. In addition, new incident responders might have different ideas of where and how to start responding to incidents. The guided response capability of Copilot in Defender allows incident response teams at all levels to confidently and quickly apply response actions to resolve incidents with ease.

## Security Copilot integration in Microsoft Defender

Guided responses are available in the Microsoft Defender portal for customers who have provisioned access to Security Copilot.

Note

Microsoft Security Copilot provides contextual recommendations to help you respond to incidents more effectively. If your organization has its own recommended guidelines, your admin can [upload them](https://learn.microsoft.com/en-us/defender-xdr/security-upload-guide) so that the guided response will reflect the specific needs and policies for your organization.

Guided responses are also available in the Security Copilot standalone experience through the Microsoft Defender XDR plugin. Know more about [preinstalled plugins in Security Copilot](https://learn.microsoft.com/en-us/security-copilot/manage-plugins#preinstalled-plugins).

## Key features

Guided responses recommend actions in the following categories:

- Triage - includes a recommendation to classify incidents as informational, true positive, or false positive
- Containment - includes recommended actions to contain an incident
- Investigation - includes recommended actions for further investigation
- Remediation - includes recommended response actions to apply to specific entities involved in an incident

Each card contains information about the recommended action, including the entity where the action needs to be applied and why the action is recommended. The cards also emphasize when a recommended action was done by automated investigation like [attack disruption](https://learn.microsoft.com/en-us/defender-xdr/automatic-attack-disruption) or [automated investigation response](https://learn.microsoft.com/en-us/defender-xdr/m365d-autoir).

The guided response cards can be sorted based on the available status for each card. You can select a specific status when viewing the guided responses by clicking on **Status** and selecting the appropriate status you want to view. All guided response cards regardless of status are shown by default.

[![Screenshot that shows the status of responses in the Copilot pane in the Microsoft Defender incident page.](https://learn.microsoft.com/en-us/defender-xdr/media/security-copilot-m365d-guided-response/copilot-defender-guided-response-status-small.png)](https://learn.microsoft.com/en-us/defender-xdr/media/security-copilot-m365d-guided-response/copilot-defender-guided-response-status.png#lightbox)

To use guided responses, perform the following steps:

1. Open an incident page. Copilot automatically generates guided responses upon opening an incident page. The Copilot pane appears on the right side of the incident page, showing the guided response cards.

   [![Screenshot that shows the Copilot pane with the guided responses in the Microsoft Defender incident page.](https://learn.microsoft.com/en-us/defender-xdr/media/copilot-in-defender/guided-response/copilot-defender-guided-response-small.png)](https://learn.microsoft.com/en-us/defender-xdr/media/copilot-in-defender/guided-response/copilot-defender-guided-response.png#lightbox)
2. Review each card before applying the recommendations. Select the More actions ellipsis \(...\) on top of a response card to view the options available for each recommendation. Here are some examples.

   ![Screenshot that shows the options available to users in a guided response card in the Copilot side panel.](https://learn.microsoft.com/en-us/defender-xdr/media/security-copilot-m365d-guided-response/guided-response-options1.png)


   ![Screenshot that shows the options available to users in an automation response card in the Copilot pane in Microsoft Defender XDR.](https://learn.microsoft.com/en-us/defender-xdr/media/security-copilot-m365d-guided-response/guided-response-options2.png)

3. To apply an action, select the desired action found on each card. The guided response action on each card is tailored to the type of incident and the specific entity involved.

   [![Screenshot that shows the guided response cards in the Copilot pane in Microsoft Defender.](https://learn.microsoft.com/en-us/defender-xdr/media/security-copilot-m365d-guided-response/copilot-defender-guided-response-actions-small.png)](https://learn.microsoft.com/en-us/defender-xdr/media/security-copilot-m365d-guided-response/copilot-defender-guided-response-actions.png#lightbox)
4. You can provide feedback to each response card to continuously enhance future responses from Copilot. To provide feedback, select the feedback icon ![Screenshot that shows the feedback icon for Copilot in Defender cards](https://learn.microsoft.com/en-us/defender-xdr/media/copilot-in-defender/copilot-defender-feedback.png) found on the bottom right of each card.

Note

Grayed out action buttons mean these actions are limited by your permission. [Refer to the unified role-based access \(RBAC\) permissions](https://learn.microsoft.com/en-us/defender-xdr/manage-rbac) page for more information.

Copilot helps speed up analysts' investigation tasks. When an incident requires further investigation on a user activity, Copilot suggests text that analysts can use to communicate with a user. The guided response card includes a **Contact user in Teams** or **Copy to clipboard** action that copies the suggested text to the clipboard. Analysts can then paste the text into an email or another communication tool. The analyst can also gain more context about the user through the **View user** action.

![Screenshot that shows the suggested text for communication in a guided response card.](https://learn.microsoft.com/en-us/defender-xdr/media/security-copilot-m365d-guided-response/guided-response-teams-message-main.png)

Copilot also supports incident response teams by enabling analysts to gain more context about response actions with additional insights. For remediation responses, incident response teams can view additional information with options like **View similar incidents** or **View similar emails**.

The **View similar incidents** action becomes available when there are other incidents within the organization that are similar to the current incident. The Similar incidents tab lists similar incidents that you can review. Microsoft Defender automatically identifies similar incidents within the organization through machine learning. Incident response teams can use the information from these similar incidents to classify incidents and further review the actions done in those similar incidents.

The **View similar emails** action, which is specific to phishing incidents, takes you to the [advanced hunting](https://learn.microsoft.com/en-us/defender-xdr/advanced-hunting-overview) page, where a KQL query to list similar emails within the organization is automatically generated. This automatic query generation related to an incident helps incident response teams further investigate other emails that might be related to the incident. You can review the query and modify it as needed.

## Sample guided responses prompt

In the Security Copilot standalone portal, you can use the following prompt to generate guided responses:

- *Generate guided responses and recommendations for Defender incident {incident ID}.*

Tip

When generating guided responses in the Security Copilot portal, Microsoft recommends including the word ***Defender*** in your prompts to ensure that the guided responses capability delivers the results.

## Provide feedback

Microsoft highly encourages you to provide feedback to Copilot, as it's crucial for a capability's continuous improvement. To provide feedback, navigate to the bottom of the Copilot side panel and select the feedback icon ![Screenshot of the feedback icon for Copilot in Defender cards](https://learn.microsoft.com/en-us/defender-xdr/media/copilot-in-defender/create-report/copilot-defender-feedback.png).

## See also

- [Learn about other Security Copilot embedded experiences](https://learn.microsoft.com/en-us/security-copilot/experiences-security-copilot)
- [Privacy and data security in Security Copilot](https://learn.microsoft.com/en-us/copilot/security/privacy-data-security)
- [Upload organization-specific guidelines for Microsoft Security Copilot guided response](https://learn.microsoft.com/en-us/defender-xdr/security-upload-guide)

Tip

Do you want to learn more? Engage with the Microsoft Security community in our Tech Community: [Microsoft Defender XDR Tech Community](https://techcommunity.microsoft.com/t5/microsoft-365-defender/bd-p/MicrosoftThreatProtection).
