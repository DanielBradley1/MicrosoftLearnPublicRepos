<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/copilot/ai-models-overview -->
<!-- Sitemap-Last-Modified: 2026-09-10 -->

# Understanding AI functionality and models in Microsoft Online Services

Note

Microsoft 365 Copilot is now named Microsoft Copilot, and Microsoft 365 Copilot Chat is now named Microsoft Copilot Chat. There are no changes to security, compliance, and privacy for organizations.

Some Microsoft Online Services offer features that use AI models and functionalities to deliver intelligent capabilities \(collectively, AI Functionalities\). AI Functionalities may be operated and provided by Microsoft or by third-parties. Third-party AI providers may offer AI functionalities either as independent data processors with their own direct contractual relationship with Microsoft enterprise customers or as AI Subprocessors. This classification determines how data is processed by that third party and governs the applicable contractual, privacy, and compliance obligations.

AI Functionalities can help people in your organization with tasks such as:

- Summarize complex information
- Answer questions using source material
- Synthesize across multiple sources
- Generate ideas, draft and edit content

Each AI model enhances Microsoft Copilot features differently, with unique strengths and specialties that can improve performance, response quality, or cost efficiency depending on your needs. To learn more about Microsoft Copilot, see [Microsoft Copilot overview](https://learn.microsoft.com/en-us/microsoft-365/copilot/microsoft-365-copilot-overview).

To learn more about how different Microsoft Online Services incorporate such AI services, please review the applicable product documentation.

This article explains the differences between the types of AI models used in Microsoft Online Services:

- AI models hosted and operated by Microsoft
- AI independent processors
- AI Subprocessors

Important

Microsoft applies [Responsible AI \(RAI\)](https://learn.microsoft.com/en-us/microsoft-copilot-studio/guidance/responsible-ai) principles and security and safety evaluations across AI Services integrated with Microsoft online services. AI Services offered by third-party AI Subprocessors may also have their own RAI and safety evaluations embedded in their models which operate in addition to Microsoft's processes. Please review product documentation for more information.

## Types of AI models used in Microsoft Online Services

### AI Models hosted and operated by Microsoft

Certain AI models used in Microsoft Online Services are hosted on Azure and provided to customers directly by Microsoft \(such as Azure OpenAI or Black Forest Labs FLUX\). These models are evaluated by Microsoft and deeply integrated into the Azure ecosystem. Therefore, they are offered under Microsoft's [Data Protection Addendum \(DPA\)](https://go.microsoft.com/fwlink/?LinkId=2365802), [Product Terms](https://go.microsoft.com/fwlink/?LinkId=2356100), and applicable enterprise safeguards. Data does not leave Microsoft.

### AI Subprocessor

An [AI Subprocessor](https://go.microsoft.com/fwlink/?linkid=2353420) is a third-party AI provider that handles data on Microsoft's behalf and under Microsoft's [Data Protection Addendum \(DPA\)](https://go.microsoft.com/fwlink/?LinkId=2365802), [Product Terms](https://go.microsoft.com/fwlink/?linkid=2356100), and [enterprise safeguards](https://learn.microsoft.com/en-us/microsoft-365/copilot/enterprise-data-protection). This helps ensure enterprise-grade compliance, security, and privacy.

When used, an AI Subprocessor handles data to deliver the specific services and functionalities Microsoft has engaged them to provide. Microsoft provides transparency through [published disclosures](https://aka.ms/subprocessors) and product documentation. For more information on these differences, see [Overview of AI Subprocessors](https://go.microsoft.com/fwlink/?LinkId=2365902).

### AI Independent Processor

An AI independent processor is a third-party AI provider that processes data under its own data processing commitments, privacy, compliance, and enterprise terms. As a result, this data handling occurs outside of Microsoft's [Data Protection Addendum](https://www.microsoft.com/licensing/docs/view/Microsoft-Products-and-Services-Data-Protection-Addendum-DPA?lang=18&msockid=344e0e6ad66c6b3e19441848d7416abd), [Product Terms](https://go.microsoft.com/fwlink/?linkid=2356100), and [enterprise safeguards](https://learn.microsoft.com/en-us/microsoft-365/copilot/enterprise-data-protection). As the admin, you control which models users can access by turning models on or off in the [Microsoft 365 admin center](https://admin.microsoft.com/) or [Power Platform admin center](https://admin.powerplatform.microsoft.com/environments).

Note

If an AI independent processor isn't enabled by an admin in the Microsoft 365 admin center or equivalent admin center, third-party AI Functionalities aren't used by any Microsoft Online Services.

## How Microsoft evaluates and communicates AI model changes

Microsoft continuously evaluates and updates the AI models used in Microsoft Copilot to help improve quality, performance, reliability, safety, and responsible AI outcomes. Before new or updated models are introduced, they undergo extensive testing and safety validation, and are reviewed against Microsoft's Responsible AI requirements.

Because AI innovation evolves rapidly, not every model change is communicated through a dedicated announcement to customers. Many model changes are upgraded versions to existing models and are considered part of the normal operation and continuous improvement of the service. Microsoft will provide targeted communications to customers in the Microsoft 365 Message center when a model change meets criteria such as the following:

- Requires administrator action
- Affects contractual, compliance, security, privacy, or data processing commitments
- Represents a significant service change

For model changes that don’t have targeted customer communications, other forms of customer communications, such as the [Copilot blog](https://techcommunity.microsoft.com/category/microsoft365copilot/blog/microsoft365copilotblog) and the [Copilot release notes](https://learn.microsoft.com/en-us/microsoft-365/copilot/release-notes), may be used to provide information about model changes and improved capabilities.

## Related articles

- [Anthropic models in Microsoft Online Services](https://learn.microsoft.com/en-us/microsoft-365/copilot/connect-to-ai-subprocessor)
- [OpenAI as a subprocessor in Microsoft Online Services](https://learn.microsoft.com/en-us/microsoft-365/copilot/openai-subprocessor)
- [Connect to SpaceXAI models](https://learn.microsoft.com/en-us/microsoft-365/copilot/connect-to-ai-models)
- [Connect to Mistral AI models](https://learn.microsoft.com/en-us/microsoft-365/copilot/connect-mistral-ai-models)
- [Copilot in Microsoft 365 apps with Anthropic models](https://learn.microsoft.com/en-us/microsoft-365/copilot/copilot-anthropic-apps)
- [Data, privacy, and security for Microsoft Copilot](https://learn.microsoft.com/en-us/microsoft-365/copilot/microsoft-365-copilot-privacy)
