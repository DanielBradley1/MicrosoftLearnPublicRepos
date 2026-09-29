<!-- Source: https://learn.microsoft.com/en-us/defender-xdr/security-upload-guide -->
<!-- Sitemap-Last-Modified: 2026-06-11 -->

# Customize incident responses for your organization

[Microsoft Security Copilot](https://learn.microsoft.com/en-us/security-copilot/microsoft-security-copilot) in the Microsoft Defender portal provides guided responses to support the response team in resolving incidents. Copilot in Defender uses AI and machine learning to contextualize an incident and learn from previous investigations to generate appropriate response actions.

This guide outlines how to upload your organization's specific guidelines to Microsoft Security Copilot to improve the guided response recommendations.

## Prerequisites

- You must be at least a security administrator to upload, approve, or delete files. Security operators can review the guidebooks but not manage them.
- Your organization-specific guidelines should be in a supported format \(PDF, DOCX, TXT\) and shouldn't exceed the maximum file size limit of 3 MB.

## Steps to customize Copilot's guided response using your organization's guidebook

Upload your guidebook from Copilot settings. You can get there in one of two ways:

- From the Microsoft Defender portal, select **System** > **Settings** > **Copilot in Defender** > **Custom guidebooks**.

  ![Screenshot of adding custom guidebooks from settings.](https://learn.microsoft.com/en-us/defender-xdr/media/security-upload-guide/add-from-settings.png)
- From the Copilot tasks pane inside an incident, go to **Create tasks from your own guidebook** and select **Open Copilot settings**.

  ![Screenshot of opening Copilot settings from the tasks pane.](https://learn.microsoft.com/en-us/defender-xdr/media/security-upload-guide/add-from-incident.png)

Then follow these steps:

1. Select **Add new guidebook**.
2. Select **Upload file**.
3. Browse to the file location, choose the file, and then select **Generate**.
4. After the file is uploaded, go to the **Pending review** tab.

   ![Screenshot of the pending review tab for uploaded guidebooks.](https://learn.microsoft.com/en-us/defender-xdr/media/security-upload-guide/pending-review.png)
5. The pending review tab shows the new recommendations based on the uploaded guidebook. Review the file to ensure it meets your organization's standards. Select the guidebook name and review the suggested generated tasks.
6. If the guidebook meets your standards, select **Approve and activate** to make it available for use in guided responses. If it doesn't meet your standards, select **Delete** to remove it.

   ![Screenshot of the approve and activate button for uploaded guidebooks.](https://learn.microsoft.com/en-us/defender-xdr/media/security-upload-guide/approve-guidebook.png)
7. Make sure the guidebook appears as active in the **Guidebooks** tab. To deactivate it later, select the guidebook and choose **Deactivate**.

   ![Screenshot of the active guidebooks tab.](https://learn.microsoft.com/en-us/defender-xdr/media/security-upload-guide/active-guidebooks.png)

Copilot will prioritize your organization's custom guidebooks over the default ones provided by Microsoft. If multiple guidebooks are relevant, Copilot will use the one that best matches the incident context.

![Screenshot of suggested responses based on the custom guidebooks.](https://learn.microsoft.com/en-us/defender-xdr/media/security-upload-guide/custom-responses.png)

You have the opportunity to provide feedback on the effectiveness of the guided responses generated from your organization's guidebooks. This feedback helps improve future recommendations.

![Screenshot of the feedback window for guided responses.](https://learn.microsoft.com/en-us/defender-xdr/media/security-upload-guide/feedback.png)

## Best practices for creating effective guidebooks

For examples of Microsoft's own incident response playbooks, see [Incident response playbooks](https://learn.microsoft.com/en-us/security/operations/incident-response-playbooks).

To create a guidebook for your organization, start with the [SOP template - Compromised identity](https://learn.microsoft.com/en-us/defender-xdr/sop-documentation-template).

When creating your organization's guidebooks, keep in mind that the guidebook can only read text. Avoid using images, graphs, or complex formatting that may hinder text extraction.
