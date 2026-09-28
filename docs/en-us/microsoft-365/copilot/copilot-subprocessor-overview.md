<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/copilot/copilot-subprocessor-overview -->
<!-- Sitemap-Last-Modified: 2026-08-18 -->

# Overview of AI Subprocessors

Note

Microsoft 365 Copilot is now named Microsoft Copilot, and Microsoft 365 Copilot Chat is now named Microsoft Copilot Chat. There are no changes to security, compliance, and privacy for organizations.

Microsoft Online Services, such as Microsoft 365, Dynamics 365, and Microsoft Azure, may use third-party providers, also known as subprocessors, as defined in the [Microsoft Data Protection Addendum](https://www.microsoft.com/licensing/docs/view/Microsoft-Products-and-Services-Data-Protection-Addendum-DPA/?msockid=344e0e6ad66c6b3e19441848d7416abd) to help operate, maintain, or support AI functionalities offered in Microsoft cloud services. These AI Subprocessors are contractually required to meet Microsoft's security, privacy, and data protection standards.

This article focuses specifically on AI Subprocessors that provide AI functionalities offered or used within Microsoft Online Services. It explains what these AI Subprocessors are, how Microsoft onboards them, and what it means for your organization. To learn more about the types of AI models used in Microsoft Online Services, see [Understanding AI functionality and models in Microsoft Online Services](https://learn.microsoft.com/en-us/microsoft-365/copilot/ai-models-overview).

## AI Subprocessors overview

Subprocessors are third-party organizations and Microsoft affiliates that assist Microsoft in delivering Online Services, which may include processing Customer Data or Personal Data on Microsoft's behalf.

Subprocessors are contractually limited to using data only to provide the services Microsoft has engaged them to perform and may not use such data for any other purpose.

Microsoft's use of subprocessors is governed by the [Microsoft Product Terms](https://go.microsoft.com/fwlink/?LinkId=2356100), [Data Protection Addendum \(DPA\)](https://go.microsoft.com/fwlink/?LinkId=2365802), and if applicable, product documentation. Microsoft uses subprocessors for different types of services, including third parties that power integrated cloud technologies, provide ancillary support and maintenance services, provide AI functionalities, or supply contract staff working under Microsoft's direction.

Subprocessors authorized to process Customer Data or Personal Data in Microsoft Online Services are listed on the Microsoft Trust Center. For more information, see [Microsoft Data Access](https://go.microsoft.com/fwlink/?LinkId=2365804) and the [Microsoft Online Services Subprocessors List](https://aka.ms/subprocessor).

Before a third party becomes a Microsoft subprocessor, Microsoft requires it to complete a formal onboarding and assessment process. This process is governed by Microsoft's [Supplier Security and Privacy Assurance \(SSPA\)](https://go.microsoft.com/fwlink/?LinkId=2366000) program, which defines baseline security, compliance, and privacy requirements for all suppliers that may process data.

As part of onboarding, subprocessors must:

- Meet Microsoft's security, compliance and privacy control requirements.
- Agree to contractual commitments and oversight that ensures Microsoft meets its obligation to Microsoft Customers.

Microsoft also performs ongoing monitoring and verification to ensure subprocessors continue to meet these requirements.

## Microsoft product integration with AI Subprocessors

Microsoft 365 includes select third-party AI models and features in Copilot experiences to expand functionality. These capabilities are delivered by trusted partners approved by Microsoft as AI Subprocessors. When enabled, they support AI features across certain Microsoft GenAI services. These features are offered under while continuing to operate under Microsoft's [Data Protection Addendum \(DPA\)](https://go.microsoft.com/fwlink/?LinkId=2365802), [Product Terms](https://go.microsoft.com/fwlink/?LinkId=2356100), enterprise standards, including security, compliance, and data protection requirements.

Microsoft 365 includes select third-party AI models and features in Copilot experiences to expand functionality. These capabilities are delivered by trusted partners approved by Microsoft as AI Subprocessors.

When enabled, they support AI features across certain Microsoft GenAI services while continuing to operate under Microsoft's enterprise standards, including security, compliance, and data protection requirements.

## User product integration

Once administrators enable \(or verify that it's enabled\) supported AI Subprocessors for your tenant or environment, those models or functionalities might be used in supported Microsoft Copilot \(apps and chat\), Copilot Studio, Power Platform, and SharePoint AI capabilities.

For example:

- **Researcher agent** in Microsoft Copilot supports working with Claude AI models from Anthropic.

  - Some Copilot experiences might also use multiple AI models during generation workflows. For example, Researcher can generate a report using one model and apply an additional reasoning pass using another model to improve completeness and structure before delivering the result.

- **Copilot in Excel**, enterprise users can choose Claude models for editing workflows after Anthropic is enabled in the Microsoft 365 admin center.
- **Copilot Cowork** uses Anthropic models to help securely carry out tasks across Microsoft 365 apps including Outlook, Teams, Word, Excel, SharePoint, and OneDrive.
- Fireworks AI inference platform on Microsoft Foundry delivers high-performance, low-latency inference for open models. For more information, see [Introducing Fireworks AI on Microsoft Foundry](https://azure.microsoft.com/blog/introducing-fireworks-ai-on-microsoft-foundry-bringing-high-performance-low-latency-open-model-inference-to-azure).

Some AI subprocessors are enabled by default, so you should verify the status of the subprocessor to make sure it aligns with your organization's governance requirements.

## How Microsoft uses AI Subprocessors

Microsoft may use third-party AI Subprocessors to perform limited functionality that support internal service orchestration, including:

- Support building product features
- Troubleshooting

AI Subprocessors participating in these processing activities are disclosed in the [Microsoft Online Services Subprocessors List](https://aka.ms/subprocessor) and are subject to enterprise security and compliance commitments consistent with Microsoft's [Data Protection Addendum \(DPA\)](https://go.microsoft.com/fwlink/?LinkId=2365802).

## How customers are notified

The [Microsoft Online Services Subprocessors List](https://aka.ms/subprocessor) identifies all AI Subprocessors authorized to process Customer Data or Personal Data. Customers can review the list and subscribe to notifications about updates or changes.

## Related topics

For more information on Microsoft Copilot working with other AI models, see:

- [Anthropic models in Microsoft Online Services](https://learn.microsoft.com/en-us/microsoft-365/copilot/connect-to-ai-subprocessor)
- [Connect to Mistral AI models](https://learn.microsoft.com/en-us/microsoft-365/copilot/connect-mistral-ai-models)
- [Connect to SpaceXAI models](https://learn.microsoft.com/en-us/microsoft-365/copilot/connect-to-ai-models)

To explore Microsoft's approach to subprocessor governance and data protection in more detail, see the following resources:

- [Understand Microsoft Online Services subprocessor management](https://learn.microsoft.com/en-us/training/modules/audit-subprocessor-management/)
- [Microsoft Data Access management](https://www.microsoft.com/trust-center/privacy/data-access)
