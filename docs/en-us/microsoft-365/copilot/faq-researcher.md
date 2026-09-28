<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/copilot/faq-researcher -->
<!-- Sitemap-Last-Modified: 2026-08-24 -->

# Microsoft Copilot Researcher agent frequently asked questions

Researcher is an advanced AI Copilot agent in Microsoft 365 designed to tackle complex, multi-step questions by acting as a deep research assistant.

## General functionality

### What is Researcher agent and how is it different from Copilot chat?

Researcher is designed for deep, multi-step research tasks, unlike standard Copilot chat, which handles quick Q&A.

### Does Researcher agent use the Archive Mailbox/Folder?

Yes, archived emails are included as backfill when primary inbox lacks sufficient data.

### Does Researcher agent support multiple languages?

Yes, it supports over 30 languages, the same as Microsoft Copilot.

### Does Researcher agent provide citations for its answers?

Yes, building trust through source citations is a core design principle.

### Is Researcher agent available in Sovereign Clouds?

To be released soon.

### Can Researcher agent fetch data from Graph Connectors?

Yes, and future updates will allow connector configuration.

### How does Researcher agent interact with enterprise and web data?

Researcher uses Microsoft Graph, connectors, and Bing index for recent web data.

### Can we restrict which websites or web content the Researcher agent can pull information from \(aside from disabling web search entirely\)?

No. There isn't a granular setting to block or allow specific websites. The only admin control over web content is the global *web search toggle*. If web search is enabled, Researcher agent will use Bing to search the web generally; if web search is disabled at the tenant level, Researcher agent won't use any web data.

### Is the Researcher agent available on mobile devices \(iOS and Android\)?

Yes, it's available on iOS and Android in the Copilot mobile app.

### Can I enable Claude in Researcher agent?

Yes. Learn more about enabling [Claude in Researcher agent](https://learn.microsoft.com/en-us/microsoft-365/copilot/connect-to-ai-subprocessor).

### Can I select which model will be used within Researcher?

Yes, you can pick the model and mode in the model picker on the top right corner of the page when in the Researcher Agent. If you are adding Researcher \(@Researcher\) to a Copilot chat outside of the agent, the model picker will be disabled and it will default to auto. The ability to select the model when adding Researcher outside of the agent is coming soon.

## Administration and controls

### How can administrators disable the Researcher agent?

Researcher is a first-party Microsoft experience built on the same foundation as Microsoft Copilot, operating entirely within the Microsoft 365 commercial data processing boundary. This tool inherits all existing security, privacy, and compliance commitments that apply across the suite of Microsoft 365 products. Researcher is part of the core default experience for Microsoft Copilot licensed users. This tool will remain accessible in Microsoft Copilot Chat under **Tools**, even when Copilot agents are disabled for some or all users in Microsoft 365 admin center. In addition, admins can block Researcher and Analyst agents. For related information, see [Manage Microsoft Copilot agents in the Microsoft 365 admin center](https://learn.microsoft.com/en-us/microsoft-365/admin/manage/manage-copilot-agents-integrated-apps) and [Agent settings in Microsoft 365 admin center](https://learn.microsoft.com/en-us/microsoft-365/admin/manage/agent-settings).

### How can users disable Researcher?

Users can't disable Researcher agent.

### If the Researcher Agent is automatically enabled \(and even pre-pinned\) for users, can an individual user remove or hide it?

No. Researcher agent is a core part of the Microsoft Copilot experience and users cannot independently remove or unpin it.

### Is there any report or dashboard available for admins to track the usage of the Researcher \(and Analyst\) agent in their tenant?

No. There is no existing reporting tool for Copilot agents like Researcher and Analyst.

## Web search integration

### Is Web Search a prerequisite for Researcher Agent?

No, web search is not required. Users can scope their search. However, because the model was trained on web data available up to 2024, its responses reflect information from that period, consistent with its design.

### Will Researcher agent adhere to the Admin Web Search toggle?

Yes. If web search is disabled at the tenant level, Researcher won't use web data.

## Data protection and privacy

### What are the data protection policies of Researcher agent?

Researcher agent adheres to the following data protection policies. See [Microsoft Copilot Privacy](https://learn.microsoft.com/en-us/microsoft-365/copilot/microsoft-365-copilot-privacy) and [Microsoft Privacy Statement.](https://www.microsoft.com/privacy/privacystatement?msockid=02283d33f3b26a153db42c6af7b26c18)

### Does Researcher agent adhere to DLP Policies?

Yes, Researcher agent adheres to DLP policies and follows the same policies as Microsoft Copilot.

### Does Researcher agent adhere to Responsible AI standards?

Yes, Researcher agent follows the same Responsible AI practices as Microsoft Copilot.

### Is Researcher agent trained on tenant data?

No. It can access work data but isn't trained on tenant data; all data remains within the Microsoft 365 boundary.

### Does Researcher agent send file attachments or customer content to OpenAI?

No. Researcher agent doesn't send user data. It complies with the Microsoft 365 data boundary.

### What are the data retention and privacy policies for content used or generated by Researcher agent?

Researcher agent adheres to the same [data handling and retention policies](https://learn.microsoft.com/en-us/microsoft-365/copilot/microsoft-365-copilot-privacy) as Microsoft Copilot.

## Usage limits

### Are there any usage limits for Researcher agent in Microsoft 365?

A maximum of 25 queries per user per month.

## Security and compliance

### What is the security posture for auto-on capabilities?

Researcher agent adheres to the same security practices as Microsoft Copilot.

### How is data in transit handled?

It's securely transmitted, following the same standards as Microsoft Copilot.

### Does Researcher agent adhere to the European Union \(EU\) boundary?

Researcher agent does adhere to the EU and Microsoft 365 boundaries.

### Can administrators or compliance officers e-discover or review the prompts and outputs from the Researcher agent?

By default, no. The content of Researcher sessions isn't directly accessible to admins or compliance tools. Admins can see usage metrics \(like how many times it's used\) but not the actual conversation content. The only exception is if a user explicitly submits feedback that includes the session data; such feedback might be stored.

## Features and future enhancements

### Can Researcher agent process images in input documents?

No, Researcher agent can't process images as input.

### Can Researcher agent generate PowerPoint and PDFs?

To be released soon.

### Does Researcher agent have memory?

To be released soon.

### How long does a typical Researcher agent response take?

Researcher agent responses typically range from under five minutes for simple queries. Then 10 to 45 minutes for highly complex ones.

### Can report length or detail be controlled in Researcher-generated reports?

To be released soon.

### Can Researcher agent have Agent-to-Agent conversations?

To be released soon.

### Can we customize or extend the Researcher agent's behavior \(for example, by using Copilot Studio to add our own prompts or connect it to additional data\)?

No - not at this time. The Researcher agent is a first-party Microsoft-built agent. Unlike custom agents, you create yourself, you can't modify Researcher's predefined logic or content.

## Other common questions

### Is Researcher agent suited for spreadsheet creation?

Analyst agent is better suited for Microsoft Excel related tasks.
