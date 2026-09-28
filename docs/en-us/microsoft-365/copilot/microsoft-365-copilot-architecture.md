<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/copilot/microsoft-365-copilot-architecture -->
<!-- Sitemap-Last-Modified: 2026-09-14 -->

# Microsoft Copilot architecture and how it works

When you create a Microsoft 365 subscription, you automatically create a tenant for your organization. Your tenant sits inside the **Microsoft 365 service boundary**, where [Microsoft Copilot](https://learn.microsoft.com/en-us/microsoft-365/copilot/microsoft-365-copilot-overview) can access your organization's data.

Operating inside the **Microsoft 365 service boundary** doesn't grant Copilot tenant-wide visibility. Data access is always scoped to the signed-in user's permissions.

This data includes information that the user can access, including their activities, and the content they create and interact with in Microsoft 365 apps.

[![Diagram that shows the Microsoft 365 tenant architecture with Microsoft Copilot and user data.](https://learn.microsoft.com/en-us/microsoft-365/copilot/media/microsoft-365-copilot-architecture/copilot-tenant-architecture.png)](https://learn.microsoft.com/en-us/microsoft-365/copilot/media/microsoft-365-copilot-architecture/copilot-tenant-architecture.png#lightbox)

Copilot is a shared service, just like many other services in Microsoft 365. When you use Copilot in your tenant:

- Your customer data stays within the Microsoft 365 service boundary.
- Existing security, compliance, and privacy policies already deployed by your organization secure your data.

This article describes how Microsoft Copilot works, including the data flow in a user prompt, how Copilot accesses data, and how Copilot honors Conditional Access and multifactor authentication \(MFA\).

This article is intended for IT admins, security teams, and technical decision-makers who want to understand the core architecture of Microsoft Copilot. It focuses on data flow, permissions, and security boundaries.

This article applies to:

- Microsoft Copilot

## User prompts and Copilot responses

When users open a Microsoft 365 app, like Word or PowerPoint, they can use Copilot to get real-time data.

The following diagram provides a visual representation of how a Copilot prompt works.

[![Diagram that shows the relationship between users, devices, apps, and Microsoft Copilot.](https://learn.microsoft.com/en-us/microsoft-365/copilot/media/microsoft-365-copilot-architecture/copilot-query-flow.png)](https://learn.microsoft.com/en-us/microsoft-365/copilot/media/microsoft-365-copilot-architecture/copilot-query-flow.png#lightbox)

Let's take a look:

1. In a Microsoft 365 app, a user enters a prompt in Copilot.
2. Copilot preprocesses the input prompt by using **grounding** and accesses Microsoft Graph in the user's tenant.

   The following video provides an overview of how grounding works in Microsoft Copilot:

   <iframe src="https://learn-video.azurefd.net/vod/player?id=ca405f29-ce24-41ea-8fa4-e27f73ed0624" allowfullscreen="true" data-linktype="external" frameborder="0"></iframe>


   - Grounding improves the specificity of your prompt, and helps you get answers that are relevant and actionable to your specific task. The prompt can include text from input files or other content Copilot discovers.
   - The data Copilot uses to generate responses is encrypted in transit.

3. Copilot sends the grounded prompt to the LLM. The LLM uses the prompt to generate a response that is contextually relevant to the user's task.
4. Copilot returns the response to the app and the user.

## User access and data privacy

Copilot only accesses data that an individual user is authorized to access, based on, for example, existing Microsoft 365 role-based access controls. Copilot doesn't access data that the user doesn't have permission to access.

The following diagram provides a visual representation of how Copilot and user access work together.

[![Diagram that shows Microsoft Copilot only accesses the data the user has permissions to access.](https://learn.microsoft.com/en-us/microsoft-365/copilot/media/microsoft-365-copilot-architecture/copilot-user-access.png)](https://learn.microsoft.com/en-us/microsoft-365/copilot/media/microsoft-365-copilot-architecture/copilot-user-access.png#lightbox)

Let's take a look:

- On devices, users open an app and enter a prompt in Copilot.
- Copilot uses [Microsoft Graph](https://learn.microsoft.com/en-us/graph/overview) to access user data that's in the user's unique context. This user data includes emails, chats, and documents that the user has permission to access.

  Microsoft 365 services help control access and security to your organization's data. These services include Restricted SharePoint Search \(RSS\), SharePoint Advanced Management \(SAM\), and Microsoft Purview. To learn more, see [Microsoft 365 E3 and E5 feature comparison list for Microsoft Copilot](https://learn.microsoft.com/en-us/microsoft-365/copilot/microsoft-365-copilot-license-feature-overview).
- Copilot can't access data that the user doesn't have permission to access. In the diagram, the grayed-out data represents data that Copilot can't access.
- When a user enters a prompt and Copilot responds, the **interaction** is stored in the user's Copilot chat history. Users can review and reuse their previous prompts. They can also [delete their chat history](https://support.microsoft.com/office/delete-your-microsoft-365-copilot-activity-history-76de8afa-5eaf-43b0-bda8-0076d6e0390f).

To learn more, see [Data stored about user interactions with Microsoft Copilot](https://learn.microsoft.com/en-us/microsoft-365/copilot/microsoft-365-copilot-privacy#data-stored-about-user-interactions-with-microsoft-copilot).

## Copilot honors Conditional Access and MFA

Copilot honors Conditional Access policies and multifactor authentication \(MFA\).

[![Diagram that shows Conditional Access and MFA can control access to Microsoft Copilot.](https://learn.microsoft.com/en-us/microsoft-365/copilot/media/microsoft-365-copilot-architecture/copilot-conditional-access-mfa.png)](https://learn.microsoft.com/en-us/microsoft-365/copilot/media/microsoft-365-copilot-architecture/copilot-conditional-access-mfa.png#lightbox)

This means:

- If you [enable and configure Conditional Access policies](https://learn.microsoft.com/en-us/entra/identity/conditional-access/plan-conditional-access), make sure your users can access Microsoft 365 services. You can manage access based on conditions you configure, including enforcing device compliance policies you set. To learn more, see [Protect AI with Conditional Access policy](https://learn.microsoft.com/en-us/entra/identity/conditional-access/policy-all-users-copilot-ai-security).

  If you use Microsoft Intune, you can use Intune compliance policies and Conditional Access together. To learn more, see [Use compliance policies to set rules for devices you manage with Intune](https://learn.microsoft.com/en-us/intune/device-security/compliance/overview).
- Copilot uses the same MFA features you configure for your tenant. With MFA, like all Microsoft 365 services, users must provide multiple forms of verification before they're allowed to access Copilot.

  If your tenant uses [security defaults](https://learn.microsoft.com/en-us/microsoft-365/solutions/empower-people-to-work-remotely-secure-sign-in), then MFA is enabled by default. If MFA isn't enabled, then Microsoft recommends [enabling MFA](https://learn.microsoft.com/en-us/entra/identity/authentication/tutorial-enable-azure-mfa).

## Related content

- [Microsoft Copilot data protection and auditing architecture](https://learn.microsoft.com/en-us/microsoft-365/copilot/microsoft-365-copilot-architecture-data-protection-auditing)
- [Setup and deploy Microsoft Copilot](https://learn.microsoft.com/en-us/microsoft-365/copilot/microsoft-365-copilot-setup)
- [Read about Data, Privacy, and Security for Microsoft Copilot](https://learn.microsoft.com/en-us/microsoft-365/copilot/microsoft-365-copilot-privacy)
