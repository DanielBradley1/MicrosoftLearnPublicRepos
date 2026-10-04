<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/copilot/responsible-ai/copilot-cowork-application-card -->
<!-- Sitemap-Last-Modified: 2026-09-22 -->

# Application card: Microsoft Copilot Cowork

## What is an Application or Platform card?

Microsoft's Application and Platform cards are intended to help you understand how our AI technology works, the choices application owners can make that influence application performance and behavior, and the importance of considering the whole application, including the technology, the people, and the environment. Application cards are created for AI applications and platform cards are created for AI platform services. These resources can support the development or deployment of your own applications and can be shared with users or stakeholders impacted by them.

As part of its commitment to responsible AI, Microsoft adheres to [six core principles](https://www.microsoft.com/ai/principles-and-approach/?msockid=3da790040c776d6f2b5485e40de56c06#ai-principles): fairness, reliability and safety, privacy and security, inclusiveness, transparency, and accountability. These principles are embedded in the [Responsible AI Standard](https://cdn-dynmedia-1.microsoft.com/is/content/microsoftcorp/microsoft/final/en-us/microsoft-brand/documents/Microsoft-Responsible-AI-Standard-General-Requirements.pdf), which guides teams in designing, building, and testing AI applications. Application and Platform cards play a key role in operationalizing these principles by offering transparency around capabilities, intended uses, and limitations. For further insight, readers are encouraged to explore Microsoft's [Responsible AI Transparency Report](https://cdn-dynmedia-1.microsoft.com/is/content/microsoftcorp/microsoft/msc/documents/presentations/CSR/Responsible-AI-Transparency-Report-2025.pdf) and the [Microsoft Enterprise AI Services Code of Conduct](https://learn.microsoft.com/en-us/legal/ai-code-of-conduct), which outlines how to engage with AI responsibly.

## Overview

Microsoft Copilot Cowork is an AI-powered agentic system that carries out multi-step tasks on your behalf across Microsoft 365. You describe what you need in natural language, and Cowork executes it—sending emails, scheduling meetings, creating documents, posting in Teams, conducting research, and managing files. Each action is visible in the conversation, and sensitive actions require your explicit approval before they're executed.

Cowork is designed for information workers who use Microsoft 365 and want to delegate complex, multi-step tasks that would otherwise require switching between multiple applications. It connects to your Outlook, Calendar, Teams, OneDrive, SharePoint, and other Microsoft 365 services, operating within your existing permissions and security boundaries.

Cowork is available as part of Microsoft Copilot. For more information, see [Cowork overview](https://learn.microsoft.com/en-us/microsoft-365/copilot/cowork/)

## Key terms

The following table defines key terms related to Cowork.

| Term | Description |
| --- | --- |
| Agent | An AI-powered component that automates and executes tasks on behalf of a user, based on natural language instructions and access to organizational data. Cowork is an agentic system that executes multi-step tasks across Microsoft 365. |
| Skill | A specialized capability that Cowork acquires during a conversation to perform a specific type of work. For example, the Email skill enables Cowork to compose, reply, forward, and send emails. |
| Custom skill | A user-authored skill stored in OneDrive that teaches Cowork new domain expertise or workflows. Custom skills are defined in a `SKILL.md` file with a name, description, and instructions. |
| Plugin | A package distributed through the Microsoft 365 App Store that extends Cowork with new skills and connectors. Plugins can be built by Microsoft, partners, or your organization. |
| Connector | A link to an external data source or service that allows Cowork to retrieve or act on information outside of Microsoft 365. |
| Action approval | The process by which Cowork pauses before performing a sensitive action \(such as sending an email\) and presents a dialog for the user to review and approve or cancel the action. |
| Scheduled prompt | A recurring task that Cowork runs automatically at a set time or on a recurring basis, defined using natural language. |
| Conversation | A single interaction session with Cowork, which may include multiple messages, actions, and file operations. |
| Side panel | The panel on the right side of the Cowork interface that shows progress, input files, output files, active skills, scheduled prompts, and approved permissions. |
| Adaptive card | A structured, interactive card-based response that Cowork can generate with layouts, buttons, and data displays directly in the conversation. |

## Key features or capabilities

The key features and capabilities below describe what Cowork is designed to do and how it performs across supported tasks.

| Feature | Description |
| --- | --- |
| Multi-step task execution | Cowork breaks complex requests into individual steps and executes them sequentially across Microsoft 365 services. Users can follow along as each step appears in the conversation. |
| Action approval | Before performing sensitive actions such as sending an email, posting in Teams, or scheduling a meeting, Cowork presents an approval dialog showing a preview of the content. Users can approve, skip future prompts for similar actions, or cancel. Approval prompts for medium and high risk actions include a risk level indicator. |
| Built-in skills | Cowork includes specialized skills: Word, Excel, PowerPoint, PDF, Email, Scheduling, Calendar Management, Meetings, Daily Briefing, Enterprise Search, Communications, Deep Research, Adaptive Cards, and Skill Management. Skills are acquired dynamically as needed during a conversation. |
| Custom skills | Users can create up to 50 custom skills stored in OneDrive at `Documents/Cowork/skills/{name}/SKILL.md`. Each skill can include up to 20 companion files \(5 MB each, 10 MB total per skill\) for reference data. Cowork discovers custom skills automatically at the start of each conversation. |
| Skill Management | Users can create, edit, and manage custom skills directly through conversation using the Skill Management skill, without manually editing files in OneDrive. |
| Plugins | Cowork supports plugins from the Microsoft 365 App Store that add new skills and connectors. Microsoft plugins \(Dynamics 365 Customer Service, Dynamics 365 Finance & Operations, Dynamics 365 Sales, Fabric IQ\) and partner plugins \(Atlassian, Miro, monday.com, LSEG, S&P Global Energy\) are available. Admins can also deploy plugins for their organization. |
| Scheduled prompts | Users can schedule prompts to run automatically at a set time or on a recurring basis using natural language. Scheduled prompts are managed from the Scheduled tab in the Tasks view or from the Schedule section in the side panel. |
| Deep Research | Cowork can conduct in-depth research across multiple sources and compile comprehensive analysis on complex topics. |
| Adaptive Cards | Cowork can generate interactive card-based responses with structured layouts, buttons, and data displays directly in the conversation. |
| Conversation controls | Users can pause Cowork \(to finish the current step or immediately\), resume when ready, or cancel the current task. Users can also send additional messages while Cowork is working to adjust its approach. |
| File operations | Cowork creates, edits, and manages files in OneDrive and SharePoint. Output files appear in the side panel with download and preview options. Bulk download packages up to 50 files as a zip archive. |
| File preview | Users can preview files directly in the conversation without downloading. Supported formats include PDF, Word, Excel, PowerPoint, Markdown, code files, images, CSV, HTML, and email. |
| Voice input | Users can speak their request instead of typing using the microphone button. |
| Work context integration | Users can attach files, people, and meetings to their conversation using the Add attachments button, upload from their device, or attach cloud files from OneDrive, SharePoint, or Teams. |
| Feedback mechanisms | Users can provide thumbs up or thumbs down ratings on individual responses, leave inline comments on specific messages, rate previewed documents, and submit general feedback through the header menu. |

As an autonomous agentic AI application, Cowork exhibits the following agentic characteristics:

- **Planning**: Cowork decomposes complex natural language instructions into a sequence of individual steps and executes them across multiple Microsoft 365 services.
- **Adaptability**: Users can send additional messages while Cowork is working to adjust its approach in real time. Cowork adapts to the user's feedback and can change course mid-task.
- **Extensibility**: Cowork's capabilities can be extended through custom skills authored by users, plugins from the Microsoft 365 App Store, and connectors to external data sources.
- **Memory \(conversation-scoped\)**: Within a single conversation, Cowork maintains context across multiple steps and user messages. Approval preferences set during a conversation persist for that session. Memory does not persist across conversations.

## Intended uses

Cowork is designed for information workers who use Microsoft 365 and want to delegate multi-step tasks. Some examples of use cases include:

- **Communication management**: Draft and send emails based on written instructions, post status updates in Teams channels, prepare stakeholder communications, and manage inbox organization.
- **Document creation and management**: Create structured documents from unstructured input \(for example, turn meeting notes into a formatted report\), build presentations from data, and reorganize files across OneDrive and SharePoint.
- **Calendar and meeting coordination**: Schedule meetings and manage calendar conflicts using natural language, prepare meeting intelligence summaries, and start the day with a daily briefing.
- **Research and analysis**: Search across organizational resources, conduct deep research that synthesizes information from multiple sources, and compile comprehensive reports.
- **Recurring task automation**: Schedule prompts that run at set times or on recurring schedules, such as daily briefings, weekly status reports, or regular inbox summaries.
- **Cross-application workflows**: Complete tasks that span multiple Microsoft 365 services in a single conversation, such as researching a topic, creating a document, and emailing it to stakeholders.

**Agentic scope**: Cowork operates within the boundaries of your Microsoft 365 permissions. It executes tasks that you instruct it to perform, with explicit approval required before sensitive actions. It doesn't take autonomous action without user direction or approval.

Cowork isn't intended for use cases that require guaranteed accuracy without human review. Examples include legal filings, medical decisions, or financial transactions that bypass approval processes.

## Models and training data

Cowork leverages AI models provided by Anthropic to power the experience that users see, including [Claude Sonnet 4.6](https://assets.anthropic.com/m/12f214efcc2f457a/original/Claude-Sonnet-4-5-System-Card.pdf) and [Claude Opus 4.7](https://assets.anthropic.com/m/64823ba7485345a7/Claude-Opus-4-5-System-Card.pdf). These models are provided to Microsoft as a subprocessor. For more information, see [Anthropic as a subprocessor for Microsoft Online Services](https://learn.microsoft.com/en-us/microsoft-365/copilot/connect-to-ai-subprocessor).

Prompts, responses, and data accessed through Microsoft Graph aren't used to train foundation LLMs, including those used by Microsoft Copilot. Your organizational data remains within Microsoft 365 and is subject to your organization's existing data governance policies. For more information about how data is handled, see [Data, Privacy, and Security for Microsoft Copilot](https://learn.microsoft.com/en-us/microsoft-365/copilot/microsoft-365-copilot-privacy).

## Performance

Cowork is designed to carry out multi-step tasks reliably across Microsoft 365 services. Performance is evaluated based on whether Cowork successfully completes the requested actions and whether the output meets the user's intent.

### Supported modalities

- **Input**: Text prompts from users \(up to 250,000 characters\), voice input via microphone, and attached files \(up to 200 MB per file\) from local devices, OneDrive, SharePoint, or Teams.
- **Output**: Text responses streamed in real time, created or modified files stored in OneDrive, sent emails and Teams messages, scheduled calendar events, and interactive adaptive card responses.

### How Cowork processes requests

1. Cowork receives a natural language instruction from the user.
2. Cowork plans the steps needed to fulfill the request, acquiring specialized skills as needed.
3. For each step, Cowork executes the action and shows progress in the conversation. Skill messages indicate when Cowork loads a new capability.
4. Before performing sensitive actions \(sending, posting, scheduling\), Cowork presents an approval dialog with a preview of the content.
5. Cowork returns the response and any created files to the user for review.

### Conditions for reliable operation

- Cowork performs best when instructions are clear and specific, including details about recipients, formatting, and expected outcomes.
- Stable internet connectivity is required. Cowork relies on cloud services and automatically reconnects if connectivity is interrupted.
- Cowork can only access data and services that your Microsoft 365 account is authorized to use.
- Performance might degrade for highly complex, multi-step tasks with many interdependencies.

### Multilingual capabilities

- Cowork is optimized for English. Support for additional languages is based on the underlying model capabilities and Microsoft 365 service availability. For more information on supported languages, see [Supported languages for Microsoft Copilot](https://support.microsoft.com/office/94518d61-644b-4118-9492-617eea4801d8).

## Limitations

Understanding Cowork's limitations is crucial to determine if it's used within safe and effective boundaries. While we encourage customers to use Cowork in their innovative solutions or applications, it's important to note that Cowork was not designed for every possible scenario. We encourage users to refer to either the [Microsoft Enterprise AI Services Code of Conduct](https://learn.microsoft.com/en-us/legal/ai-code-of-conduct) \(for organizations\) or the Code of Conduct section in the [Microsoft Services Agreement](https://www.microsoft.com/servicesagreement) \(for individuals\) as well as the following considerations when choosing a use case:

- **Instruction interpretation**: Cowork might misinterpret ambiguous or overly broad instructions, leading to actions that don't match your intent. Provide clear, specific requests for better results.
- **Content accuracy**: AI-generated documents, emails, and messages should be treated as drafts. Always review content before approving send or share actions. Cowork might produce inaccurate information, particularly when source data across your organization is incomplete or outdated.
- **Task complexity**: Complex, multi-step tasks with many dependencies might not always complete as expected. Users should monitor progress and use the pause or cancel controls when needed.
- **Permission boundaries**: Cowork is dependent on your existing Microsoft 365 permissions. It can't access data or services that your account isn't authorized to use.
- **File access limitations**: Cowork can't access files stored on your local device \(it works with files in OneDrive, SharePoint, and other connected cloud services\), can't delete files or folders in OneDrive or SharePoint, and can't read encrypted or rights-protected files. File uploads are limited to 200 MB per file.
- **Platform and device support**: Cowork is available in your browser, the Microsoft Copilot desktop app for Windows and Mac, the Microsoft Copilot mobile app for iOS and Android, and in Outlook and Teams. Feature availability may vary by platform. Voice input availability depends on your browser and device.
- **Custom skills and plugins**: Custom skills authored by users or your organization are not validated by Microsoft. Plugin skills and connectors are provided by third-party publishers. Review outputs from custom skills and plugins carefully, as quality depends on how they were written or who published them.
- **Bias, stereotyping, and ungrounded content**: Despite responsible AI controls, AI-generated content might still reflect biases, stereotypes, or ungrounded information. Users should always review responses and actions before approving them. For more information on the known limitations of AI-generated content from Anthropic models, refer to the linked system cards in the [Models and training data](#models-and-training-data) section.
- **Potential significant physical or psychological injury to an individual**: Avoid use or misuse of the system that could result in significant physical or psychological injury to an individual. For example, scenarios that diagnose patients or prescribe medications have the potential to cause significant harm.
- **Consequential impact on life opportunities or legal status**: Avoid use or misuse of the system that could have a consequential impact on life opportunities or legal status. Examples include scenarios where the AI system could affect an individual's legal status, legal rights, or their access to credit, education, employment, healthcare, housing, insurance, social welfare benefits, services, opportunities, or the terms on which they're provided.

## Evaluations

Performance and safety evaluations assess whether Cowork is operating reliably and securely by examining factors like groundedness, relevance, and coherence while identifying the risks of generating harmful content. The following evaluations were conducted with safety components already in place, which are also described in [Safety components and mitigations](#safety-components-and-mitigations).

### Performance and quality evaluations

Performance evaluations for Cowork are essential to improving its reliability in real-world usage. We regularly conduct performance evaluations for the following metrics, which are available through Microsoft Foundry:

- Groundedness
- Coherence
- Fluency
- Similarity

### Performance and quality evaluation methods

Our evaluation data is custom-built to assess AI application performance across key areas of safety and quality, simulating real-world scenarios and risks. We begin by identifying relevant evaluation aspects of concern based on multi-disciplinary research and expert input. These concerns are translated into targeted evaluation objectives and guide formulation of evaluation metrics. For safety, we create adversarial prompts to elicit undesirable or edge-case responses, which are then scored using AI-assisted annotators trained to assess alignment with Microsoft's safety standards. For quality, we craft rubric-based prompts relevant to scenarios including evaluating retrieval-augmented generation \(RAG\) applications and agents. Datasets are curated from diverse sources including synthetic and public datasets to simulate real-world user scenarios. Using the curated datasets, both evaluations undergo iterative refinement and human alignment to improve metric efficacy and reliability. This methodology forms the foundation of repeatable, rigorous assessments that reflect how customers use evaluations to build better and safer AI.

Cowork was evaluated using text-based scenarios that reflect how users work across Microsoft 365 apps. Evaluations for metrics like task completion, groundedness, and response quality used established LLM-as-judge methods. Offline test sets included multi-step task execution, document creation, email composition, scheduling, and representative enterprise scenarios. Evaluators assessed whether actions were correctly executed, responses were factually supported, and outputs were consistent across variations of the same task. Ideal outcomes reflect accurate task completion, correct action parameters, and consistent performance. Suboptimal outcomes include incorrect recipients, unsupported claims in generated content, or incomplete task execution.

### Custom evaluations

In addition to the standard metrics, Cowork was evaluated using custom metrics specific to its agentic capabilities:

- Task completion \(whether the requested action was successfully executed across multiple steps\)
- Response relevance \(whether the output matches the user's intent\)
- Action accuracy \(whether the correct recipients, content, and parameters are used in executed actions\)

Custom evaluations used text-based scenarios designed to test multi-step task execution, action parameter accuracy, and cross-application workflow completion. Ideal results demonstrate that Cowork correctly identifies the steps needed, executes each action with accurate parameters \(recipients, dates, file names\), and completes the full task as instructed. Suboptimal results include skipped steps, incorrect action parameters, or partial task completion.

### Risk and safety evaluations

Evaluating potential risks associated with AI-generated content is essential for safeguarding against content risks with varying degrees of severity. This includes evaluating Cowork's predisposition towards generating harmful content or testing for vulnerabilities to jailbreak attacks. The following risk and safety evaluations were conducted:

- Hate and unfairness
- Sexual
- Violence
- Self-harm
- Protected material
- Indirect jailbreak
- Direct jailbreak
- Ungrounded attributes
- Unauthorized action execution

### Risk and safety evaluation methods

Risk and safety evaluations used text-based adversarial prompts and automated classifiers to assess potential harms. Tests combined LLM-judge evaluations with classifier-based detection and manual testing where needed. Additional evaluations specific to Cowork's action-execution capability tested whether the agentic system could be manipulated into performing unauthorized or harmful actions \(sending emails to unintended recipients, executing actions without proper approval, or bypassing permission boundaries\). Ideal results redirect or decline unsafe requests and maintain consistent boundary-keeping across prompt variations. Suboptimal results include producing harmful content, executing actions without proper approval, or responding inconsistently to adversarial inputs.

## Safety components and mitigations

As we identified potential risks and misuse through processes like red team testing and measured them, we developed mitigations to reduce the potential for harm. The following list describes some of those mitigations. We continue to evaluate Cowork to improve product performance and mitigations.

- **Action approval system.** Cowork's primary safety mechanism is the action approval system. Before performing any sensitive action \(sending emails, posting messages, scheduling meetings, modifying files\), Cowork pauses and presents a preview for user review. This ensures no irreversible action is taken without explicit human consent. Approval prompts for medium and high risk actions include a risk level indicator.
- **Permission boundaries.** Cowork operates strictly within the user's existing Microsoft 365 permissions. It can't access data, services, or resources that the user's account isn't authorized to use. This prevents privilege escalation and ensures organizational access controls are respected.
- **Conversation-scoped approvals.** When a user selects "Don't ask again" for a type of action, that approval applies only to the current conversation. Approvals don't persist across conversations, limiting the blast radius of any unintended permission grant.
- **AI-based classifiers and content filtering.** Cowork uses AI-based classifiers and content filters to identify and block potentially harmful content in both user prompts and generated responses. These include filters for hate speech, violence, sexual content, self-harm, and protected material.
- **Metaprompting.** System instructions guide Cowork's behavior to align with Microsoft's AI Principles and user expectations, including instructions to decline inappropriate requests and maintain professional boundaries.
- **Grounding in organizational data.** Cowork grounds responses in the user's organizational data accessed through Microsoft Graph. This reduces hallucination by anchoring outputs in actual documents, emails, and calendar events that the user has access to.
- **User-centered design and transparency.** Cowork shows each step as it works, making the AI's actions transparent. Users can see what skills are being loaded, what actions are being taken, and what the current progress is. This transparency helps users identify when Cowork is heading in an unintended direction.
- **Conversation controls.** Users can pause, resume, or cancel Cowork's work at any time. This gives users the ability to interrupt if Cowork is heading in the wrong direction, without waiting for it to complete.
- **Feedback mechanisms.** Users can submit feedback through thumbs up/down on individual responses, inline comments on specific messages, document-level ratings, and general feedback through the header menu. This feedback is used to evaluate and improve Cowork's quality and safety.
- **Tenant-level admin controls.** Administrators can manage access to Cowork through the Microsoft 365 admin center, including disabling access for specific users or security groups, controlling plugin deployment, and managing organizational policies.
- **Cybersecurity measures.** Cowork implements cybersecurity practices including encrypted data transmission, secure authentication through Microsoft Entra ID, and adherence to Microsoft's security development lifecycle. Organizational data remains within Microsoft 365 boundaries and is subject to existing data governance and compliance policies. Regular security audits and threat model reviews are conducted to identify and address potential vulnerabilities.

## Best practices for deploying and adopting Cowork

Responsible AI is a shared commitment between Microsoft and its customers. While Microsoft builds AI applications and platform services with safety, fairness, and transparency at the core, customers play a critical role in deploying and using these technologies responsibly within their own contexts. To support this partnership, we offer the following best practices for deployers and end users to help customers implement responsible AI effectively.

### Deployers and end users should:

- **Exercise caution and evaluate outcomes when using Cowork for consequential decisions or in sensitive domains.** Consequential decisions are those that may have a legal or significant impact on a person's access to education, employment, financial platforms, government benefits, healthcare, housing, insurance, legal platforms, or that could result in physical, psychological, or financial harm. Sensitive domains—such as financial platforms, healthcare, and housing—require particular care due to the potential for disproportionate impact on different groups of people. When using AI for decisions in these areas, make sure that impacted stakeholders can understand how decisions are made, appeal decisions, and update any relevant input data.
- **Evaluate legal and regulatory considerations.** Customers need to evaluate potential specific legal and regulatory obligations when using any AI platforms and solutions, which may not be appropriate for use in every industry or scenario. Additionally, AI platforms or solutions are not designed for and may not be used in ways prohibited in applicable terms of service and relevant codes of conduct.

### Deployers should:

- **Configure access controls appropriately.** Use the Microsoft 365 admin center to manage which users and groups have access to Cowork. Consider starting with a pilot group before broader deployment.
- **Educate users on the approval model.** Ensure users understand that they are responsible for reviewing and approving actions Cowork takes on their behalf. Emphasize that AI-generated content should be treated as drafts.
- **Review plugin deployment.** Evaluate plugins before deploying them to your organization. Understand what data each plugin accesses and what actions it can perform.
- **Monitor usage and feedback.** Review user feedback submitted through the Microsoft 365 admin center to identify patterns, common issues, or areas where additional training might be needed.

### End users should:

- **Exercise human oversight when appropriate.** Human oversight is an important safeguard when interacting with AI applications. While we continuously improve our AI applications, AI might still make mistakes. The outputs generated may be inaccurate, incomplete, biased, misaligned, or irrelevant to your intended goals. This could happen due to various reasons, such as ambiguity in the inputs or limitations of the underlying models. As such, users should review the responses generated by Cowork and verify that they match their expectations and requirements.
- **Be aware of the risk of overreliance.** Overreliance on AI happens when users accept incorrect or incomplete AI outputs, mainly because mistakes in AI outputs may be hard to detect. For the end user, overreliance could result in decreased productivity, loss of trust, application abandonment, financial loss, psychological harm, or physical harm.
- **Exercise caution when using Cowork in sensitive domains.** Users should exercise caution when using agentic AI applications in sensitive domains where agentic actions are irreversible or highly consequential. Additional precautions should also be taken when creating autonomous agentic AI as described further in either the [Microsoft Enterprise AI Services Code of Conduct](https://learn.microsoft.com/en-us/legal/ai-code-of-conduct) \(for organizations\) or the Code of Conduct section in the [Microsoft Services Agreement](https://www.microsoft.com/servicesagreement) \(for individuals\).
- **Provide clear, specific instructions.** Include details about recipients, formatting, content expectations, and desired outcomes. The more specific the instruction, the better the result.
- **Review all generated content before approving.** Always verify that emails, documents, Teams messages, and calendar events are correct before approving send or share actions. Pay attention to recipients, dates, and content accuracy.
- **Use conversation controls actively.** If Cowork is heading in the wrong direction, pause or cancel rather than waiting for it to complete. You can also send additional messages to steer its approach.
- **Provide feedback regularly.** Use the thumbs up/down buttons and inline comments to help improve Cowork's performance over time.

## Learn more about Cowork

For additional guidance or to learn more about the responsible use of Cowork, we recommend reviewing the following documentation:

- [Cowork overview](https://learn.microsoft.com/en-us/microsoft-365/copilot/cowork/)
- [Get started with Cowork](https://learn.microsoft.com/en-us/microsoft-365/copilot/cowork/get-started)

## Learn more about responsible AI

- [Responsible AI FAQ for Cowork](https://learn.microsoft.com/en-us/microsoft-365/copilot/responsible-ai/cowork-responsible-ai-faq)
- [Responsible AI overview for Cowork](https://learn.microsoft.com/en-us/microsoft-365/copilot/responsible-ai/cowork-responsible-ai-overview)
- [Microsoft AI principles](https://www.microsoft.com/ai/responsible-ai)
- [Microsoft responsible AI resources](https://www.microsoft.com/ai/tools-practices)
- [Microsoft Azure Learning courses on responsible AI](https://learn.microsoft.com/en-us/training/paths/responsible-ai-business-principles/)
- [Data, Privacy, and Security for Microsoft Copilot](https://learn.microsoft.com/en-us/microsoft-365/copilot/microsoft-365-copilot-privacy)
