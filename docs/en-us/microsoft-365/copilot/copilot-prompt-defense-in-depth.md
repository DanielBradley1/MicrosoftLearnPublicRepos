<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/copilot/copilot-prompt-defense-in-depth -->
<!-- Sitemap-Last-Modified: 2026-09-10 -->

# Microsoft Copilot prompt defense in depth

**Applies to:** ✅ Microsoft Copilot

Microsoft Copilot applies layered protections at multiple stages of prompt processing. These protections help reduce security, privacy, compliance, and data-protection risks before a prompt reaches a language model, while organizational data is being grounded, and before responses are delivered to users.

This article describes proactive protections that help reduce AI-related risks, runtime protections that apply throughout the prompt lifecycle, and how Microsoft helps protect against prompt injection attacks.

## Proactive protections that help reduce AI risk

Proactive protections reduce risk by improving visibility, limiting exposure to harmful content, controlling content discovery, and protecting customer data.

| Protection | Description |
| --- | --- |
| **Third-party skill egress transparency** | Administrators can review agent details, including the data sources, tools, and connections used by agents. This information helps administrators assess risk and make deployment decisions. See [Understand agent details in Microsoft 365 admin center](https://learn.microsoft.com/en-us/microsoft-365/admin/manage/agent-details). |
| **Prompt injection audit logs** | Microsoft provides audit and security monitoring capabilities for Microsoft Copilot and AI application interactions. Audit records and related security signals help organizations investigate potentially risky AI interactions and agent activity.  <br>  <br>Look for `JailbreakDetected` as a Boolean flag to denote whether a jailbreak attempt was made using a prompt message. See [Audit logs for Copilot and AI applications](https://learn.microsoft.com/en-us/purview/audit-copilot). |
| **Spam, scam, and suspicious content blocking** | Microsoft applies protections to help reduce the likelihood that Microsoft Copilot retrieves or presents harmful, malicious, deceptive, or low-quality web content during web-grounded experiences. See [Security for Microsoft Copilot](https://learn.microsoft.com/en-us/microsoft-365/copilot/security-microsoft-365-copilot). |
| **No grounding in spam mail or chats** | Microsoft Copilot excludes certain categories of unwanted content from grounding sources to help reduce the risk of malicious or deceptive instructions influencing responses. |
| **Restricted Content Discovery** | Administrators can configure Restricted Content Discovery to help limit the discoverability of SharePoint content in organization-wide search and Copilot experiences, without changing site permissions. See [Restrict discovery of SharePoint sites and content](https://learn.microsoft.com/en-us/sharepoint/restricted-content-discovery) |
| **Prompt injection protection for email** | Microsoft Defender for Office 365 Plan 2 detects prompt injection content in inbound email before that content reaches a user or an AI assistant. See [Prompt injection protection in Microsoft Defender for Office 365](https://learn.microsoft.com/en-us/defender-office-365/step-by-step-guides/prompt-injection-protection-defender-for-office-365). |
| **Domain exclusion** | Administrators can use a PowerShell script to exclude up to 1,000 sites from web grounding in Microsoft Copilot and Microsoft Copilot Chat. See [Domain exclusion overview](https://learn.microsoft.com/en-us/copilot/domain-exclusion). |
| **Updated web search product terms** | Microsoft states that prompts, responses, and Microsoft Graph data aren't used to train foundation models. Other protections apply to web-grounding queries, including contractual commitments regarding the handling of customer data. See [Data, privacy, and security for web search in Microsoft Copilot and Microsoft Copilot Chat](https://learn.microsoft.com/en-us/microsoft-365/copilot/manage-public-web-access). |

## Runtime protections across the prompt lifecycle

Runtime protections help reduce risks to security, privacy, compliance, and data before a prompt reaches a language model, while organizational data is being grounded, and before responses are delivered to users.

The following stages represent the flow of a typical Microsoft Copilot interaction:

- **[Stage 1: Prompt input](#stage-1-prompt-input)**: A user enters a prompt or attaches content to a Microsoft Copilot or agentic experience.
- **[Stage 2: Prompt ingress](#stage-2-prompt-ingress)**: The prompt is sent to the Microsoft Copilot orchestrator.
- **[Stage 3: Grounding](#stage-3-grounding)**: Content is retrieved from documents, messages, meetings, and other Microsoft 365 data.
- **[Stage 4: Web search](#stage-4-web-search)**: If enabled, web content is retrieved.
- **[Stage 5: Response egress](#stage-5-response-egress)**: A response is displayed.

Note

Microsoft manages some controls, and you configure others. The availability of some protections described in this article depends on your organization's licensing. Some features might require [Microsoft Purview](https://learn.microsoft.com/en-us/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-purview-service-description), [Microsoft Defender](https://learn.microsoft.com/en-us/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-defender-service-description), or other applicable licenses.

### Stage 1: Prompt input

During the prompt input stage, a user enters a prompt or attaches content to a Microsoft Copilot or agentic experience. If you have [Microsoft Purview DLP for Microsoft Copilot](https://learn.microsoft.com/en-us/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-purview-service-description#microsoft-purview-data-loss-prevention-dlp-for-microsoft-365-copilot), the following protection applies:

| Protection | Description |
| --- | --- |
| **Paste to browser controls** | Administrators can restrict users from pasting sensitive content into browser-based applications by using Microsoft Purview Endpoint DLP. See [Help prevent leakage of sensitive content by restricting paste actions into browsers](https://learn.microsoft.com/en-us/purview/endpoint-dlp-create-policy-restrict-paste-in-browsers). |

### Stage 2: Prompt ingress

During prompt ingress, the system sends prompts to the Microsoft Copilot orchestrator. Before the underlying AI systems process prompts, Microsoft applies multiple safeguards designed to detect and mitigate potentially harmful content. You can also configure certain controls, such as [Microsoft Purview DLP for Microsoft Copilot](https://learn.microsoft.com/en-us/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-purview-service-description#microsoft-purview-data-loss-prevention-dlp-for-microsoft-365-copilot) to help safeguard your data.

| Protection | Description |
| --- | --- |
| **Block list** | Microsoft continuously updates safeguards that help identify and block known malicious prompts, jailbreak attempts, and other unsafe interactions. See [Data, Privacy, and Security for Microsoft Copilot](https://learn.microsoft.com/en-us/microsoft-365/copilot/microsoft-365-copilot-privacy). |
| **Responsible AI classifier filtering** | Microsoft implements Responsible AI classifiers in Microsoft Copilot. See [How Copilot blocks harmful content](https://learn.microsoft.com/en-us/microsoft-365/copilot/microsoft-365-copilot-privacy#how-does-copilot-block-harmful-content). |
| **Protected materials** | Microsoft applies protections designed to help detect and prevent the generation of protected or copyrighted material when applicable. See [Copilot provides protected material detection](https://learn.microsoft.com/en-us/microsoft-365/copilot/microsoft-365-copilot-privacy#does-copilot-provide-protected-material-detection). |
| **Microsoft Purview DLP controls for prompt processing** | Administrators can configure Microsoft Purview DLP to protect interactions with Microsoft Copilot and Copilot Chat. Microsoft Purview DLP for Copilot prompts helps organizations protect sensitive data at the point of interaction with AI. By enforcing DLP policies on prompts submitted to Microsoft Copilot and Copilot Chat, organizations can prevent sensitive information from being included in prompts, helping reduce data leakage, oversharing, and exposure to risky or unauthorized content. See [Learn about using Microsoft Purview Data Loss Prevention to protect interactions with Microsoft Copilot and Copilot Chat](https://learn.microsoft.com/en-us/purview/dlp-microsoft365-copilot-location-learn-about). |
| **Block hidden Unicode instructions in copy-paste prompts** | Microsoft Copilot helps protect against hidden-instruction attacks by detecting and sanitizing certain Unicode-based obfuscation techniques that can conceal instructions in copied and pasted text. This helps prevent invisible content from influencing prompt processing. Based on the security descriptions in the internal Unicode sanitization and prompt injection mitigation materials. |

### Stage 3: Grounding

During the grounding stage, Microsoft Copilot generates responses by combining large language models with organizational content that users already have permission to access. Content retrieved during grounding can include documents, emails, meetings, chats, and other Microsoft 365 data sources. If you have Microsoft Purview, you can configure controls to help protect sensitive files and emails.

| Protection | Description |
| --- | --- |
| **Microsoft Purview DLP for Microsoft Copilot** | Administrators can configure Microsoft Purview DLP to help restrict sensitive files and email messages that have sensitivity labels from being processed by Copilot and agentic experiences. See [Block files and emails with sensitivity labels from being processed](https://learn.microsoft.com/en-us/purview/dlp-microsoft365-copilot-location-learn-about#block-files-and-emails-with-sensitivity-labels-from-being-processed). |
| **Tool chain analysis** | Microsoft's analysis includes evaluating tool usage, assessing the risk of a prompt injection attack, validating tool capabilities, and deciding whether to block or allow a request. Tool chain analysis produces a signal that is used to support task adherence. |

### Stage 4: Web search

During this stage, Microsoft Copilot uses web content if it's enabled. Some Copilot experiences use web content to improve response quality. Web grounding is separate from Microsoft Graph grounding and doesn't change existing Microsoft 365 permissions applied to organizational content. When you use web grounding, Microsoft applies extra safeguards to improve response safety and quality.

| Protection | Description |
| --- | --- |
| **Web grounding controls** | By default, web search is enabled for Microsoft Copilot and Microsoft Copilot Chat in commercial tenants, but not for U.S. Government Community Cloud \(GCC, GCC-High, and DoD\) tenants. Administrators can configure whether to allow web search. See [Controls available to manage web search](https://learn.microsoft.com/en-us/microsoft-365/copilot/manage-public-web-access#controls-available-to-manage-web-search). |
| **DLP controls for sensitive information in web search** | Microsoft Purview DLP helps organizations prevent users from inadvertently exposing sensitive information when interacting with AI experiences that use web content. Administrators can configure DLP policies to detect and block sensitive data, such as credit card numbers, regulated data, or other protected information, from being included in prompts sent to web-based AI services. These DLP controls help reduce data leakage risks while allowing employees to safely benefit from web-powered AI capabilities. See [Block sensitive information types in web search](https://learn.microsoft.com/en-us/purview/dlp-microsoft365-copilot-location-learn-about#block-sensitive-information-types-in-web-search). |

### Stage 5: Response egress

During the response egress stage, before Microsoft Copilot displays a response to a user, it applies extra safeguards to identify and prevent potentially harmful outputs. If you have [Microsoft Defender for Office 365](https://learn.microsoft.com/en-us/office365/servicedescriptions/office-365-advanced-threat-protection-service-description), you can configure Safe Links protection.

| Protection | Description |
| --- | --- |
| **Citation resilience and completeness** | Microsoft Copilot provides citations and references to help users understand the sources used to generate responses and improve transparency. |
| **RAI classifier filtering on egress** | Microsoft's responsible AI protections evaluate generated content before it's presented to the user. See [How Copilot blocks harmful content](https://learn.microsoft.com/en-us/microsoft-365/copilot/microsoft-365-copilot-privacy#how-does-copilot-block-harmful-content). |
| **Safe Links** | Administrators can configure Safe Links protection to help protect users when they follow links returned by Microsoft Copilot. URLs are evaluated at the time they're selected, helping identify malicious destinations before users access them. Organizations with Microsoft Defender for Office 365 can use Safe Links policies for more URL protection. See [Safe Links in Defender for Office 365](https://learn.microsoft.com/en-us/defender-office-365/safe-links-about). |
| **User awareness about external content** | Microsoft surfaces indicators that help users distinguish organizational content from external content in supported experiences. |
| **User in the loop** | Microsoft Copilot is designed to assist users, who remain responsible for reviewing, validating, and acting on generated content. |
| **Disclaimers** | Microsoft reminds users that AI-generated content should be reviewed for accuracy and appropriateness before use. |

## Defense against prompt injection attacks

Microsoft provides controls to help protect against both types of prompt injection attacks and tools to respond to an attack. Here's a high-level overview of the attack response flow:

1. **A prompt injection attempt occurs**. Prompt injection attacks can be direct or indirect attacks.

   - **Direct**: The user types a prompt designed to coerce Microsoft Copilot into doing something malicious.
   - **Indirect**: The user's prompt refers to instructions that attempt to coerce Microsoft Copilot to do something malicious. The instructions can be contained in text files, images, code, files, or encoded text, but not in the prompt itself.

2. **Microsoft applies prompt injection protections and other security controls** to help detect and mitigate malicious instructions. Examples of protections applied during prompt processing include:

   - Prompt injection and jailbreak mitigation
   - Spam, scam, and suspicious content detection


   Depending on what your Microsoft 365 plan includes, your administrators can use capabilities in [Microsoft Defender XDR](https://learn.microsoft.com/en-us/defender-xdr/security-for-ai/defender-security-for-ai) and [Microsoft Purview](https://learn.microsoft.com/en-us/purview/ai-microsoft-purview) to help guard against prompt injection attacks.

3. **Alerts are created**. Microsoft operates jailbreak classifiers on behalf of customers. When those classifiers are triggered, they expose signals in two places: the Microsoft Defender portal and Microsoft Purview audit logging. These signals notify your organization's security operations team \(SecOps\) and your data security administrators so they can investigate.

   - **In the [Microsoft Defender portal](https://learn.microsoft.com/en-us/defender-xdr/microsoft-365-defender-portal)** \([https://security.microsoft.com/](https://security.microsoft.com/)\), **SecOps teams investigate alerts** using Microsoft Defender XDR and Microsoft Sentinel. Alerts are enriched with threat intelligence data to provide more context, and automated investigation, remediation, and attack-disruption actions can be used to help contain threats and accelerate response. See [Threat response in the Microsoft Defender portal](https://learn.microsoft.com/en-us/unified-secops/respond-threats-overview).
   - **Using [Audit logs for Copilot and AI applications](https://learn.microsoft.com/en-us/purview/audit-copilot), data security administrators and investigators can review user activities**. Once onboarded, the system automatically generates audit logs when a user interacts with Copilot or an AI Application. These audit records contain details about which user interacted with Copilot, when the interaction took place, and where it occurred. Audit records also include references to files, sites, or other resources Copilot and AI applications accessed to generate responses to user prompts.

     Note

     Additional capabilities in Microsoft Purview, such as Insider Risk Management, can help detect, investigate, and mitigate potential malicious or inadvertent insider activities. See [Use Microsoft Purview to manage data security & compliance for Microsoft Copilot & Microsoft Copilot Chat](https://learn.microsoft.com/en-us/purview/ai-m365-copilot).

## Next steps

- [Understand AI functionality and models in Microsoft Online Services](https://learn.microsoft.com/en-us/microsoft-365/copilot/ai-models-overview).
- See [Secure and govern Microsoft Copilot: Foundational deployment guidance](https://learn.microsoft.com/en-us/microsoft-365/copilot/secure-govern-copilot-foundational-deployment-guidance) \(deployment blueprint\).
- See [Microsoft Copilot data and compliance readiness](https://learn.microsoft.com/en-us/microsoft-365/copilot/microsoft-365-copilot-minimum-requirements-data-compliance).
