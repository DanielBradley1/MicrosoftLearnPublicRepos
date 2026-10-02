<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/copilot/microsoft-365-copilot-overview -->
<!-- Sitemap-Last-Modified: 2026-09-17 -->

# Microsoft Copilot overview

Note

Microsoft Copilot is available in many regions worldwide. However, it might not be accessible in certain markets. Some organizations might gain access through an account support escalation process, but access is subject to approval. For more information, see [International availability](https://www.microsoft.com/microsoft-365/business/international-availability).

Microsoft Copilot Chat and Microsoft Copilot responses and experiences differ by data grounding, integration depth, and licensing.

However, all experiences are powered by:

- [Large language models \(LLMs\)](https://azure.microsoft.com/resources/cloud-computing-dictionary/what-are-large-language-models-llms) for natural language understanding and generation
- [Grounding in web](https://learn.microsoft.com/en-us/microsoft-365/copilot/manage-public-web-access) and/or [organizational data](https://learn.microsoft.com/en-us/viva/organizational-data) \([Microsoft Graph](https://learn.microsoft.com/en-us/graph/overview-major-services) and [Work IQ](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/work-iq/)\)
- Access scoped by user permissions \(security and compliance enforced\)

Note

Anthropic subprocessors are available only in applicable Microsoft 365 licensed experiences and aren't available to all users by default. Anthropic operates with [Microsoft Enterprise data protections](https://learn.microsoft.com/en-us/microsoft-365/copilot/enterprise-data-protection). For more information, see [Anthropic models in Microsoft Online Services](https://learn.microsoft.com/en-us/microsoft-365/copilot/connect-to-ai-subprocessor).

| Copilot Chat \(Basic\) license | Microsoft 365 Copilot \(Basic\) license | Microsoft 365 Copilot \(Premium\) license |
| --- | --- | --- |
| Securely interact with Copilot Chat using web data only | Securely interact with Copilot Chat using web data only | Securely interact with Copilot using web data and work data \([Microsoft Graph](https://learn.microsoft.com/en-us/graph/overview-major-services) and [Work IQ](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/work-iq/)\) |
| You **don't** have the Microsoft 365 Copilot add-on license and **don't** have access to Copilot in Word, Excel, PowerPoint, and OneNote.  <br>  <br>For more information, see [Copilot Chat \(Basic\) license and experience](#copilot-features-in-microsoft-365-apps). | You **don't** have the Microsoft 365 Copilot add-on license but have **[standard access](https://support.microsoft.com/topic/standard-versus-priority-access-to-features-in-microsoft-365-copilot-chat-12c8d9f8-db32-4f99-8ebe-d8d85879137f)** to Copilot in Word, Excel, PowerPoint, and OneNote.  <br>  <br>For more information, see [Microsoft 365 Copilot \(Basic\) license and experience](#copilot-features-in-microsoft-365-apps). | You **have** the Microsoft 365 Copilot add-on license with **[priority access](https://support.microsoft.com/topic/standard-versus-priority-access-to-features-in-microsoft-365-copilot-chat-12c8d9f8-db32-4f99-8ebe-d8d85879137f)** to the full experience of Copilot in Word, Excel, PowerPoint, and OneNote.  <br>  <br>You have access to [Microsoft Copilot Cowork](https://learn.microsoft.com/en-us/microsoft-365/copilot/cowork/) via [usage-based billing](https://learn.microsoft.com/en-us/microsoft-365/copilot/usage-based-billing-manage-copilot-credits).  <br>  <br>For more information, see [Microsoft 365 Copilot \(Premium\) license and experience](#copilot-features-in-microsoft-365-apps). |
| - Access to agents that use web data.<br>- Pay-as-you-go work data agents. | - Access to agents that use web data.<br>- Pay-as-you-go work data agents. | Includes access to agents that use web and work data \([Microsoft Graph](https://learn.microsoft.com/en-us/graph/overview-major-services) and [Work IQ](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/work-iq/)\). |
| Basic usage management controls and reporting for admins. | Basic usage management controls and reporting for admins. | Added advanced management controls and analytics for admins. |

Note

In-product labels are displayed in Microsoft 365 apps like Word, Excel, PowerPoint, and OneNote, and in the Microsoft Copilot app, to help users identify their Copilot experience.

## Copilot features in Microsoft 365 apps

Important

**Chat experiences in Microsoft 365 apps vary depending on your tenant configuration and license**. For more information, see [licensing prerequisites](https://www.microsoft.com/licensing/terms/productoffering/Microsoft365/EAEAS#clause-2213-h3-1), [Microsoft Copilot service descriptions](https://learn.microsoft.com/en-us/office365/servicedescriptions/office-365-platform-service-description/microsoft-365-copilot?context=/microsoft-365/copilot/context/copilot), [Copilot license options](https://learn.microsoft.com/en-us/microsoft-365/copilot/microsoft-365-copilot-licensing), and [Microsoft Copilot requirements](https://learn.microsoft.com/en-us/microsoft-365/copilot/microsoft-copilot-requirements).  
  
For more information about US government cloud, see [Understand Microsoft US government cloud environments for Microsoft 365 and Microsoft Copilot](https://learn.microsoft.com/en-us/microsoft-365/copilot/gov-overview).

- [Microsoft Copilot Chat \(Basic\) license and experience](#tabpanel_1_microsoft-copilot-chat-basic)
- [Microsoft 365 Copilot \(Basic\) license and experience](#tabpanel_1_microsoft-365-copilot-basic)
- [Microsoft 365 Copilot \(Premium\) license and experience](#tabpanel_1_microsoft-365-copilot-premium)

**Copilot Chat \(Basic\)** is the standalone baseline experience included with eligible Microsoft 365 licenses. It provides a secure, enterprise-ready AI chat that primarily uses web data and has limited use of organizational content. Copilot Chat can use organizational content, but you must explicitly provide that content with your prompt.

You can access Copilot Chat \(Basic\) through:

- `copilot.cloud.microsoft`
- Microsoft Copilot app \(web, desktop, mobile\)
- Copilot Chat in Edge \(select the Copilot icon in the upper-right corner of the Edge browser\). Use Copilot Chat to summarize website content and [some document types](https://learn.microsoft.com/en-us/DeployEdge/edge-learnmore-copilot-page-summary-results) displayed in Edge.
- Copilot Chat in Outlook and Teams

Note

**The Microsoft 365 Copilot Chat app is now called Microsoft Copilot Chat**. The primary URL for accessing the updated Copilot app is changing from `m365.cloud.microsoft` to `copilot.cloud.microsoft`. To help ensure users' connections aren't blocked, see [Network requirements for Microsoft Copilot](https://learn.microsoft.com/en-us/microsoft-365/copilot/microsoft-copilot-requirements#network-requirements).

Declarative agents that are grounded in instructions and public websites are included with Copilot Chat. Access to custom or other agents is pay-as-you-go only.

To use organizational content with Copilot Chat:

- Copy and paste content, upload a file, or select a file when creating your prompt.
- Use Copilot Chat in select Microsoft 365 apps like Teams and Outlook with content you have open. In this context, Copilot Chat is aware of your open content and can use it instead of requiring you to copy and paste information or upload a file.
- Use a pay-as-you-go agent that has access to organizational content.

**Microsoft 365 Copilot \(Basic\)** refers to users without the Copilot add-on license, but who still have [standard access](https://support.microsoft.com/topic/standard-versus-priority-access-to-features-in-microsoft-365-copilot-chat-12c8d9f8-db32-4f99-8ebe-d8d85879137f) to Copilot capabilities inside apps \(for example, Word or Excel\). These experiences are more limited and might not include full chat integration or priority access. Standard access is subject to service capacity and might vary throughout the day.

You can access Microsoft 365 Copilot \(Basic\) through:

- `copilot.cloud.microsoft`
- [Microsoft Copilot app \(web, desktop, mobile\)](https://www.microsoft.com/microsoft-365-copilot/download-copilot-app?msockid=3fbdc68005c06723095dd00004ef664d)
- Microsoft 365 apps \(Word, Excel, PowerPoint, and OneNote\)

Note

**The Microsoft 365 Copilot Chat app is now called Microsoft Copilot Chat**. The primary URL for accessing the updated Copilot app is changing from `m365.cloud.microsoft` to `copilot.cloud.microsoft`. To help ensure users' connections aren't blocked, see [Network requirements for Microsoft Copilot](https://learn.microsoft.com/en-us/microsoft-365/copilot/microsoft-copilot-requirements#network-requirements).

In-app features you can use:

- Word: Draft, rewrite, and summarize documents
- Excel: Analyze data, generate insights, create formulas and visuals
- PowerPoint: Create presentations from prompts or existing content, summarize presentations or edit presentations \(add images, apply deck-wide formatting changes\)
- Outlook: Draft emails, summarize threads, and use the coaching tips to improve clarity, sentiment and tone
- OneNote: Draft plans, ideas, and lists
- Teams: Summarize \(up to 30 days\) and transcribe meetings, and capture action items
- Forms: Draft questions to create surveys, polls and other forms

Pay-as-you-go access to agents that use work data.

**Microsoft 365 Copilot \(Premium\)** is the full add-on licensed experience, which includes everything in Microsoft 365 Copilot \(Basic\) and:

- [Priority access](https://support.microsoft.com/topic/standard-versus-priority-access-to-features-in-microsoft-365-copilot-chat-12c8d9f8-db32-4f99-8ebe-d8d85879137f) for better performance and availability. Priority access provides faster response times and more consistent availability even during peak usage periods.
- Deep integration and advanced AI capabilities with Microsoft 365 apps and services.
- Grounding responses in [organizational data](https://learn.microsoft.com/en-us/viva/organizational-data) \(emails, files, meetings, calendars, teams, or organizational relationships\) through [Microsoft Graph](https://learn.microsoft.com/en-us/graph/overview), [Work IQ](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/work-iq/), Copilot Search, and semantic indexing.

  - [Microsoft Graph](https://learn.microsoft.com/en-us/graph/overview) brings a personalized organizational data context into the prompt, like information from a user's emails, files, meetings, calendars, teams, or organizational relationships.
  - [Work IQ](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/work-iq/) is an intelligence layer that enables agents access to reason over organizational data, content and tools. **You can turn Work IQ on or off**.

    - When Work IQ is **on**, Copilot responses are grounded in web, and in [Microsoft Graph](https://learn.microsoft.com/en-us/graph/overview) and [Work IQ](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/work-iq/). Responses are enriched with work-specific contexts such as emails, files, meetings, calendars, teams, or organizational relationships.
    - When Work IQ is **off**, Copilot responses aren't grounded in Microsoft Graph and Work IQ. Users can still receive responses, but those responses aren't enriched with work-specific context such as emails, files, meetings, calendars, teams, or organizational relationships.
    - Although both use the Work IQ platform, Work IQ is included with Microsoft 365 Copilot \(Premium\), whereas the [Work IQ API](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/work-iq/#access-and-pricing) is a distinct [usage-based billing offering](https://learn.microsoft.com/en-us/microsoft-365/copilot/usage-based-billing-overview-copilot-credits) that can be purchased and consumed independently for custom apps, agents, and integrations.

  - [Copilot Search](https://learn.microsoft.com/en-us/copilot/microsoft-365/microsoft-365-copilot-search) is an AI-powered universal search experience across all your Microsoft 365 applications and connected non-Microsoft data sources. It's integrated with Microsoft Copilot, so users can find the results they need by using search, then seamlessly transition to chat for deeper exploration or follow-up task completion.
  - [Semantic indexing](https://learn.microsoft.com/en-us/microsoftsearch/semantic-index-for-copilot) enhances search relevance and accuracy by using advanced lexical and semantic understanding of Microsoft Graph data, resulting in more contextually precise information retrieval. Copilot preserves security, compliance, and privacy, ensuring organizational boundaries are respected while offering a seamless user experience.

- [SharePoint Advanced Management \(SAM\)](https://learn.microsoft.com/en-us/sharepoint/get-ready-copilot-sharepoint-advanced-management): helps you reduce oversharing and cleanup inactive sites. These tasks declutter Copilot's data sources and improve the quality of the responses.

  - [Restricted content discovery](https://learn.microsoft.com/en-us/sharepoint/restricted-content-discovery): helps you limit discovery of content from specific SharePoint sites, including recently interacted files, in organization-wide search results and Microsoft Copilot responses while those reviews are taking place.

- [Microsoft Purview](https://learn.microsoft.com/en-us/purview/ai-microsoft-purview): can classify and label your data based on the sensitivity of the content. It can also help prevent unauthorized sharing or leakage and review Copilot prompts and responses.
- [Microsoft Agents](https://learn.microsoft.com/en-us/microsoft-365-copilot/extensibility): agents are scoped or focused versions of Microsoft Copilot that act as AI assistants and can automate business processes. These Agents use web and work data \([Microsoft Graph](https://learn.microsoft.com/en-us/graph/overview-major-services) and [Work IQ](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/work-iq/)\).
- [Usage reports](https://learn.microsoft.com/en-us/microsoft-365/admin/activity-reports/microsoft-copilot-usage): helps you understand how users are engaging with Copilot and can be useful in tracking adoption over time and in Microsoft 365 apps. Use the [organizational messages](https://learn.microsoft.com/en-us/copilot/microsoft-365/microsoft-365-copilot-enable-users) feature to act on adoption trends they are seeing. It lets you reach your users in the flow of their daily work with targeted, actionable guidance.
- [Microsoft Copilot Cowork](https://learn.microsoft.com/en-us/microsoft-365/copilot/cowork/): you have access to [Cowork](https://learn.microsoft.com/en-us/microsoft-365/copilot/cowork/) via [usage-based billing](https://learn.microsoft.com/en-us/microsoft-365/copilot/usage-based-billing-manage-copilot-credits). Cowork carries out tasks across your Microsoft 365 environment on your behalf.

You can access Microsoft 365 Copilot \(Premium\) through:

- `copilot.cloud.microsoft`
- [Microsoft Copilot app \(web, desktop, mobile\)](https://www.microsoft.com/microsoft-365-copilot/download-copilot-app?msockid=3fbdc68005c06723095dd00004ef664d)
- Microsoft 365 apps \(Word, Excel, PowerPoint, and OneNote\)

Note

**The Microsoft 365 Copilot app is now called Microsoft Copilot**. The primary URL for accessing the updated Copilot app is changing from `m365.cloud.microsoft` to `copilot.cloud.microsoft`. To help ensure users' connections aren't blocked, see [Network requirements for Microsoft Copilot](https://learn.microsoft.com/en-us/microsoft-365/copilot/microsoft-copilot-requirements#network-requirements).

Other resources:

- [Major services and features in Microsoft Graph](https://learn.microsoft.com/en-us/graph/overview-major-services)
- [Semantic indexing explained by Microsoft \(YouTube video\)](https://www.youtube.com/watch?v=KtsVRCsdvoU)
- [Compare features in the Microsoft 365 licenses that affect Copilot](https://learn.microsoft.com/en-us/microsoft-365/copilot/microsoft-365-copilot-license-feature-overview)
- [Configure a secure and governed data foundation for Microsoft Copilot](https://learn.microsoft.com/en-us/microsoft-365/copilot/microsoft-365-copilot-license-feature-overview)
- Measure insights with [Copilot Analytics](https://techcommunity.microsoft.com/blog/microsoftvivablog/introducing-copilot-analytics-to-measure-ai-impact-on-your-business/4301717)
- Microsoft offers Copilot experiences in many products. For more information, see [documentation, training, and other technical resources](https://learn.microsoft.com/en-us/copilot/) to make the most of the enterprise-grade data-security and privacy features for your organization.

Note

To ensure your users access Copilot Chat for work and education, instruct them to sign in with their Microsoft Entra account before accessing Copilot via the Microsoft Copilot app, copilot.cloud.microsoft, Copilot Chat in Edge, or productivity apps. Entry points for users signed in with a personal account \(MSA\):

- Microsoft Copilot app \(web, desktop, mobile\)
- Copilot Chat in Edge
- Copilot Chat in Outlook and Teams
- Copilot Chat agents for Word, Excel, and PowerPoint
- Integrations within other Microsoft 365 apps and products

You can manage whether your users can sign in to Microsoft 365 apps using a personal account \(MSA\). For more information, see [use tenant restrictions V2](https://learn.microsoft.com/en-us/entra/external-id/tenant-restrictions-v2).

## Data security and privacy

The following table outlines key security considerations:

| Data security consideration | Copilot Chat \(Basic\) license | Microsoft 365 Copilot \(Basic\) license | Microsoft 365 Copilot \(Premium\) license |
| --- | --- | --- | --- |
| [Enterprise Data Protection \(EDP\)](https://learn.microsoft.com/en-us/microsoft-365/copilot/enterprise-data-protection) | Yes | Yes | Yes |
| Responses grounded in web data | Yes | Yes | Yes |
| Responses grounded in organizational data | Yes, but you must:<br><br>- Upload the files with your prompt<br>- Use Copilot Chat with open content \(Outlook and Teams\)<br>- Use a pay-as-you-go agent that has access to organizational content | Yes, but you must:<br><br>- Upload the files with your prompt<br>- Use Copilot Chat with open content \(Outlook and Teams\)<br>- Use a pay-as-you-go agent that has access to organizational content | Yes, automatic via [Microsoft Graph](https://learn.microsoft.com/en-us/graph/overview) and [Work IQ](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/work-iq/). |
| European Union Data Boundary \(EUDB\) | Yes | Yes | Yes |

### Enterprise Data Protection \(EDP\)

Copilot Chat \(Basic\), Microsoft 365 Copilot \(Basic\), and Microsoft 365 Copilot \(Premium\) are protected by [Enterprise Data Protection \(EDP\)](https://learn.microsoft.com/en-us/microsoft-365/copilot/enterprise-data-protection) when you sign in with Microsoft Entra accounts. With EDP, [prompts and responses are protected](https://learn.microsoft.com/en-us/copilot/microsoft-365/enterprise-data-protection#enterprise-data-protection-for-prompts-and-responses)by the same contractual terms and commitments that customers widely trust for their emails in Exchange and files in SharePoint.

Additional resources:

- [Microsoft Copilot data protection architecture](https://learn.microsoft.com/en-us/microsoft-365/copilot/microsoft-365-copilot-architecture-data-protection-auditing)
- [Data, privacy, and security for web search in Microsoft Copilot and Microsoft Copilot Chat](https://learn.microsoft.com/en-us/microsoft-365/copilot/manage-public-web-access)

### Responses grounded in web data

**Copilot Chat \(Basic\)** and **Microsoft 365 Copilot \(Basic\)** responses are grounded in data from the public web. Copilot Chat \(Basic\) and Microsoft 365 Copilot \(Basic\) **can't** use organizational data via Microsoft Graph when interacting with Copilot Chat. You must upload the content with your prompt, work with open content \(Teams and Outlook\), or use a pay-as-you-go agent that has access to organizational data.

**Microsoft 365 Copilot \(Premium\)** uses **both** web and organizational data via [Microsoft Graph](https://learn.microsoft.com/en-us/graph/overview) and [Work IQ](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/work-iq/), and pulls information automatically. You can specify the files to focus on, but you don't need to upload them manually.

### Responses grounded in organizational data

Copilot Chat \(Basic\) and Microsoft 365 Copilot \(Basic\) users can provide organizational content as part of their prompt by manually uploading a file directly or by using a pay-as-you-go agent that has access to organizational content. However, Copilot Chat \(Basic\) and Microsoft 365 Copilot \(Basic\) users don't have access to Microsoft Graph. For more information, see [organizational data and Copilot Chat](https://learn.microsoft.com/en-us/microsoft-365/copilot/microsoft-365-copilot-privacy#how-does-microsoft-365-copilot-protect-organizational-data).

Microsoft 365 Copilot \(Premium\) uses both web and organizational data via Microsoft Graph and pulls information automatically. You can specify the files to focus on, but you don't need to upload them manually.

### European Union Data Boundary \(EUDB\)

Copilot Chat \(Basic\), Microsoft 365 Copilot \(Basic\), and Microsoft 365 Copilot \(Premium\) route calls to the LLM to the closest data centers in the region but can also call into other regions where greater capacity is available when utilization is especially high. For European Union \(EU\) users, Microsoft Copilot has additional safeguards to comply with the EU Data Boundary. EU traffic stays within the [EU Data Boundary](https://learn.microsoft.com/en-us/privacy/eudb/eu-data-boundary-learn), while worldwide traffic can be sent to the EU and other countries or regions for LLM processing.

### Responsible AI

Microsoft Copilot adheres to Microsoft's [Responsible AI principles](https://www.microsoft.com/ai/principles-and-approach?msockid=3be31cda99b962db1b5a0a8398f063ed#ai-principles). For more information, see [Microsoft Copilot Responsible AI FAQ](https://learn.microsoft.com/en-us/microsoft-365/copilot/responsible-ai/responsible-ai-overview), and [Responsible AI at Microsoft](https://www.microsoft.com/ai/responsible-ai).

## Model selection

Microsoft Copilot offers the latest models tailored to your business needs without changing your [security, compliance, and privacy settings](https://learn.microsoft.com/en-us/microsoft-365/copilot/microsoft-365-copilot-privacy). You can select different models by using the model selector in the UI. By default, Copilot uses a real-time router to adjust the underlying model it uses based on your prompt.

Note

Anthropic subprocessors are available only in applicable Microsoft 365 licensed experiences and aren't available to all users by default. Anthropic operates with [Microsoft Enterprise data protections](https://learn.microsoft.com/en-us/microsoft-365/copilot/enterprise-data-protection). For more information, see [Anthropic models in Microsoft Online Services](https://learn.microsoft.com/en-us/microsoft-365/copilot/connect-to-ai-subprocessor).

| Model | Description |
| --- | --- |
| Auto | Copilot determines which model to use while in the default "Auto" mode. |
| Quick response | For common or routine questions, Copilot prioritizes speed, using a high-throughput model to craft quick, succinct responses to straightforward questions. |
| Think deeper | For complex or more open-ended questions, Copilot might detect that the prompt requires advanced reasoning. In these cases, Copilot uses a deeper reasoning model, taking its time to craft a plan, gather and comprehend all relevant context, and check its work before providing a thorough response. |

These options update as new models become available.

## Copilot controls

In the admin center, use the [Copilot controls](https://learn.microsoft.com/en-us/microsoft-365/copilot/copilot-controls/overview) to manage Copilot Chat experiences, including Copilot Chat \(Basic\), Microsoft 365 Copilot \(Basic\), and Microsoft 365 Copilot \(Premium\).

In Copilot controls, you can configure how users interact with Copilot and related AI experiences, including:

- Control whether Copilot Chat is [pinned across experiences](https://learn.microsoft.com/en-us/microsoft-365/copilot/pin-copilot-chat-navbar#pinning-options), such as in the Microsoft 365 app and other Copilot surfaces, based on licensing.
- Manage whether users can [generate images in Copilot Chat](https://learn.microsoft.com/en-us/microsoft-365/copilot/microsoft-365-copilot-page#copilot-actions).
- Control how users can [create and use agents](https://learn.microsoft.com/en-us/microsoft-365/copilot/copilot-controls/management-controls). Agents might have expanded capabilities and integration options for Microsoft 365 Copilot \(Premium\) users.
- Manage web search grounding by using the [Allow web search in Copilot policy](https://learn.microsoft.com/en-us/microsoft-365/copilot/manage-public-web-access#it-admin-control-for-both-microsoft-365-copilot-and-microsoft-365-copilot-chat). This policy applies to Copilot Chat experiences across all licenses.
- [Remove user access to Copilot Chat entirely](https://learn.microsoft.com/en-us/copilot/manage#remove-access-to-copilot-chat), including for Copilot Chat \(Basic\) users.

For broader governance, you can assign the [AI Administrator role](https://learn.microsoft.com/en-us/microsoft-365/admin/add-users/about-admin-roles), which provides least-privilege access to manage Copilot and AI features across Copilot Chat \(Basic\), Microsoft 365 Copilot \(Basic\), and Microsoft 365 Copilot \(Premium\) without requiring Global Administrator permissions.

## Train your users

Help users understand how to use Copilot to assist them with work tasks by pointing them to the following resources:

- [Copilot Chat \(Basic\) training](#tabpanel_2_microsoft-copilot-chat-basic-training)
- [Microsoft 365 Copilot \(Basic\) training](#tabpanel_2_microsoft-copilot-basic-training)
- [Microsoft 365 Copilot \(Premium\) training](#tabpanel_2_microsoft-copilot-premium-training)

- [Microsoft Copilot Chat, your AI assistant for work](https://support.microsoft.com/copilot-microsoft365-chat): Guidance on how to get started, use different prompts, and understand the differences between Copilot Chat and other Copilot offerings.
- [Microsoft Copilot Chat video tutorial](https://support.microsoft.com/topic/microsoft-365-copilot-chat-video-tutorial-e54fb679-9554-435a-8418-d0e0ce2646c6): Short, easy-to-understand videos on getting started and tasks you can do with Copilot Chat.

- [Transform ideas into action with Copilot](https://learn.microsoft.com/en-us/training/paths/explore-microsoft-365-copilot-business-chat): This course teaches learners how to get started with Microsoft Copilot, craft effective prompts, and use its AI-powered features to enhance productivity, streamline work, and collaborate securely in real-time.

- [Copilot Prompt Gallery](https://copilot.cloud.microsoft/prompts?products%2Fname=CWC&createdBy=CreatedByAll): Example prompts for your user to help them do their work \(for example, "How can I more concisely describe change management?"\).
- [Copilot Success Kit](https://adoption.microsoft.com/copilot-chat/success-kit/): Use it to prepare your tenant for Microsoft 365 Copilot \(Premium\) and to enable your users to create and use agents. The kit includes information on admin controls, licensing and payment methods, training materials, onboarding email templates, and more.
- [Copilot Trainer Kit](https://aka.ms/CopilotChat/TrainerKit): Downloadable PowerPoint training presentation to help businesses get started with Copilot Chat.
- [Copilot user tools and templates](https://adoption.microsoft.com/copilot/user-engagement-tools-and-templates/): A collection of user-facing tools and templates for you to quickly onboard your organization.

## Track and increase Copilot adoption

The [Microsoft Copilot Chat usage report](https://learn.microsoft.com/en-us/microsoft-365/admin/activity-reports/microsoft-copilot-usage) provides you with insights into how users are engaging with Copilot Chat \(applies to all licenses\) and related chat-based experiences, helping track adoption trends and prompt activity over time. The report includes metrics such as total and daily active users, total prompts submitted, average prompts per user, and anonymized per-user engagement details \(for example, last activity date and active days\) across 7, 30, 90, or 180-day views.

In contrast, the [Microsoft Copilot usage report](https://learn.microsoft.com/en-us/microsoft-365/admin/activity-reports/microsoft-365-copilot-usage) focuses on usage of Microsoft Copilot within Microsoft 365 apps such as Teams, Outlook, Word, Excel, and PowerPoint \(requires Microsoft 365 \(Basic\) or Microsoft 365 Copilot \(Premium\) licenses\). Use the Microsoft Copilot usage report to understand how licensed Copilot features are being used in-app, this report complements the [Copilot Chat usage report](https://learn.microsoft.com/en-us/microsoft-365/admin/activity-reports/microsoft-copilot-usage) by providing a broader view of integrated Copilot adoption across workloads.

Together, with these reports, you can distinguish between standalone chat engagement \(Copilot Chat \(Basic\)\) and deeper, app-integrated Copilot usage \(Microsoft 365 \(Basic\) and \(Premium\)\), and to identify opportunities to drive adoption across both experiences.

You use the [Organizational messages](https://learn.microsoft.com/en-us/microsoft-365/copilot/microsoft-365-copilot-enable-users) feature to act on report insights, delivering targeted, contextual guidance directly within users' workflows to increase awareness and effective usage.

## Other Copilot products

The following Copilot products are independently licensed and don't require a Microsoft 365 Copilot \(Premium\) license. Organizations can purchase and use each offering based on their specific needs, audience, and use cases.

- [Microsoft Security Copilot](https://learn.microsoft.com/en-us/copilot/security/microsoft-security-copilot): helps security professionals with incident response, threat hunting, intelligence gathering, posture management, and more.
- [GitHub Copilot](https://docs.github.com/copilot/about-github-copilot/what-is-github-copilot/): is an AI coding assistant that can help you write code faster. This Copilot is licensed by your work organization.
- [Microsoft Copilot Studio](https://learn.microsoft.com/en-us/microsoft-copilot-studio/fundamentals-what-is-copilot-studio): is a low-code graphical tool that you can use to create agents and connect to other data sources. Agents let you customize your organization's Copilot experience. They can automate and execute business processes, like help desk, change management, and managing guests in meetings.

For other Microsoft Copilot products, see the [Microsoft Copilot learning hub](https://learn.microsoft.com/en-us/copilot/).
