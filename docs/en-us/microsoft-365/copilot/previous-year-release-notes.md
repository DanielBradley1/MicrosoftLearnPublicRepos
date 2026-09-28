<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/copilot/previous-year-release-notes -->
<!-- Sitemap-Last-Modified: 2026-08-03 -->

# 2025 Microsoft 365 Copilot release notes

This page lists the features and improvements for Microsoft 365 Copilot released last year. It includes changes that were generally available \(Current Channel for Microsoft 365 apps\) and specific to each platform.

Copilot features are introduced using a safe deployment model, gradually rolling out to a subset of users within a tenant before expanding across the organization.

- [All features](#tabpanel_1_all)
- [Windows](#tabpanel_1_win)
- [Web](#tabpanel_1_Web)
- [Android](#tabpanel_1_androidos)
- [iOS](#tabpanel_1_appleios)
- [Mac](#tabpanel_1_mac)

## December 23, 2025

Updates released between December 10, 2025, and December 23, 2025.

### Microsoft 365 Copilot app

- **GPT-5 powers Copilot Chat by default** \[Android, Windows, iOS, Mac, Web\]

  Copilot Chat delivers faster, smarter results using GPT-5 as the default model.

  **Details:**

  **What Changed:** All Copilot Chat experiences run on GPT-5 by default. Copilot automatically routes prompts to the best-performing models for each task, using fast models for basic tasks and specialized reasoning models for multi-step requests.

  **Why:** Users want speed, accuracy, and minimal friction. This update helps to ensure consistent, high-quality AI interactions in Copilot Chat.

  **Try This:**

  - "Get me up to speed on the latest plans related to \[project/initiative\]. Help me think through what to do next."
  - "Use the attached spreadsheet with customer feedback to create a polished executive report that helps upper management decide where to prioritize resources in our next cycle."


  **Why this matters:**


  **Business Impact:** Increases accuracy and productivity, helping teams make strong decisions and complete complex work faster.


  **Personal Impact:** Removes friction by letting Copilot choose the best model--fast or reasoning--for the prompt.


  **Additional resources:**


  **Blogs:**


  [Available today: GPT-5 in Microsoft 365 Copilot](https://www.microsoft.com/microsoft-365/blog/2025/08/07/available-today-gpt-5-in-microsoft-365-copilot/?msockid=281b58ceea286c6226164ec5eb056dd6)

### Microsoft 365 Copilot Chat

- **Streamlined Copilot chat navigation with expanded history** \[Windows, Web\]

  A redesigned navigation pane provides a cleaner layout and expanded chat history, making it easier to switch between conversations. This allows you to switch between conversations and pick up where you left off, perfect for fast-paced projects and multitasking.

  **Roadmap ID:** [516570](https://www.microsoft.com/microsoft-365/roadmap?msockid=2484525e9a9b66d4330b47329bb667c9&filters=&searchterms=516570)

  **Details:**

  **What Changed:** The Copilot navigation pane highlights key agents, removes clutter, and expands visible chat history beyond the previous limit of five recent chats. Chat search is also more prominent for faster access to specific threads. This reduces interface clutter.

  **Why:** Users wanted an interface that feels organized and speeds up workflow. This redesign lets you quickly return to prior conversations without digging through menus.

  **Try This:**

  - Open the navigation pane in Copilot to see the improved design.
  - Search for a previous project conversation using the updated chat search bar.
  - Pin your most important chats to keep them accessible during critical work sessions.


  **Why this matters:**


  **Business Impact:** Standard, simplified navigation UI to help reduce downtime from searching old threads.


  **Personal Impact:** Enjoy a simpler, less cluttered workspace with easier access to past chats.

### Microsoft 365 Copilot extensibility

- **Access IT service documentation with Freshservice integration** \[Web\]

  Let Copilot retrieve IT documentation and troubleshooting instructions directly from Freshservice with this integration.

  **Roadmap ID:** [513280](https://www.microsoft.com/microsoft-365/roadmap?msockid=2484525e9a9b66d4330b47329bb667c9&filters=&searchterms=513280)

  **Details:**

  **What Changed:** Freshservice connector gives access to IT procedures and knowledge articles

  **Why:** IT teams and employees often struggle with finding the right documentation. With Copilot pulling service details in real time, response times and productivity benefit.

  **Try This:**

  - Connect Freshservice in Copilot settings.
  - Ask Copilot, "What's the procedure for resetting passwords from Freshservice?"
  - Insert a troubleshooting guide directly into a Teams post for your team.


  **Why this matters:**


  **Business Impact:** Faster issue resolution reduces downtime and keeps employees productive.


  **Personal Impact:** Remove frustration, solve issues, and prevent delays caused by searching for documentation.


  **Additional resources:**


  **Learn:**


  [Freshservice Microsoft 365 Copilot connector overview](https://learn.microsoft.com/en-us/microsoftsearch/freshservice-overview)

- **Upload Larger Files in Copilot Studio Agent Builder** \[Android, Windows, iOS, Web\]

  Agent Builder now supports file uploads up to 512 MB when creating agents, ideal for larger files.

  **Roadmap ID:** [500375](https://www.microsoft.com/microsoft-365/roadmap?msockid=2484525e9a9b66d4330b47329bb667c9&filters=&searchterms=500375)

  **Details:**

  **What Changed:** This increases the upload size limit in Agent Builder to 512 MB, enabling use of larger files as grounding data.

  **Why:** Users requested more flexibility for grounding agents. Larger files reduce the need to split or compress documents.

  **Try This:**

  - Drag and drop large documents such as training manuals into your agent project.
  - Create the agent and ask it to summarize information from uploaded files.


  **Why this matters:**


  **Business Impact:** Allows enterprises to build agents with richer, domain-specific knowledge.


  **Personal Impact:** Complete your work without the need to split files or compress data.


  **Additional resources:**


  **Learn:**


  [Embedded file content](https://learn.microsoft.com/en-us/microsoft-365-copilot/extensibility/agent-builder-add-knowledge#embedded-file-content)

- **Use .NET client libraries to integrate Microsoft 365 Copilot APIs** \[Web\]

  Offers official .NET SDKs for integrating with Microsoft 365 Copilot APIs.

  **Details:**

  **What changed:** Released a .NET SDK for Copilot API calls, making integration easier.

  **Why:** Meets enterprise developers' need for secure .NET integration options.

  **Try This:**

  - Install NuGet package
  - Authenticate and initiate Copilot prompt calls
  - Process responses in your .NET app


  **Why this matters:**


  **Business Impact:** Improves developer productivity and project speed.


  **Personal Impact:** Gives .NET teams direct hooks into Copilot capabilities.


  **Additional resources:**


  **Learn:**


  [Microsoft 365 Copilot APIs client libraries](https://learn.microsoft.com/en-us/microsoft-365-copilot/extensibility/sdks/api-libraries?tabs=csharp)

- **Use Python client libraries to integrate Microsoft 365 Copilot APIs** \[Web\]

  Adds official Python libraries for secure integration with Microsoft 365 Copilot APIs.

  **Details:**

  **What changed:** Developers can now leverage Microsoft 365 Copilot APIs using Python SDKs.

  **Why:** Opens opportunities for AI workflows in Python-based applications.

  **Try This:**

  - Install Python SDK
  - Authenticate using OAuth
  - Send prompts and parse results


  **Why this matters:**


  **Business Impact:** Expands Copilot customization for enterprise developers.


  **Personal Impact:** Python devs gain first-class access to Copilot APIs.


  **Additional resources:**


  **Learn:**


  [Microsoft 365 Copilot APIs client libraries](https://learn.microsoft.com/en-us/microsoft-365-copilot/extensibility/sdks/api-libraries?tabs=csharp)

- **Use TypeScript client libraries to integrate Microsoft 365 Copilot APIs** \[Web\]

  Build custom integrations with Microsoft 365 Copilot APIs using official TypeScript SDK libraries.

  **Roadmap ID:** [501574](https://www.microsoft.com/microsoft-365/roadmap?msockid=2484525e9a9b66d4330b47329bb667c9&filters=&searchterms=501574)

  **Details:**

  **What changed:** Official TypeScript SDK released for Copilot API integration in web apps.

  **Why:** Standardizes developer integration with Microsoft 365 Copilot features.

  **Try This:**

  - Install SDK via npm
  - Authenticate using Microsoft Identity
  - Test API calls for Copilot prompts


  **Why this matters:**


  **Business Impact:** Enables custom enterprise apps with AI-powered features.


  **Personal Impact:** Developers have a secure, documented method for advanced builds.


  **Additional resources:**


  **Learn:**


  [Microsoft 365 Copilot APIs client libraries](https://learn.microsoft.com/en-us/microsoft-365-copilot/extensibility/sdks/api-libraries?tabs=csharp)

- **View and Manage SharePoint Agents with Greater Control** \[Web\]

  Admins can now see all SharePoint agents in a single unified view and manage them more intuitively with a streamlined delete action.

  **Details:**

  **What Changed:** The enhanced Copilot controls UI introduces a centralized SharePoint agent inventory and replaces the previous block/unblock workflow with a clear, simplified delete option.

  **Why:** Admins requested more transparent oversight of deployed agents, and this update delivers easier tracking, review, and lifecycle management.

  **Try This:**

  - Go to Agents and Connectors in Copilot controls.
  - Review all existing SharePoint agents and delete those that are outdated, unused, or no longer compliant.


  **Why this matters:**


  **Business Impact:** Strengthens governance and operational hygiene by reducing risk from stale or misconfigured agents.


  **Personal Impact:** Saves time with straightforward, intuitive controls instead of complex, multi-step administration.

### Microsoft 365 Copilot Studio

- **Build Copilot agents using organizational People data** \[Windows, Web\]

  Developers can build agents in Copilot Studio that deliver personalized, context-aware responses using organizational People data.

  **Details:**

  **What changed:** Added the ability for agent builders to access and use People data from your directory in responses.

  **Why:** Makes interactions more contextual and human-centric for better relevance.

  **Try This:**

  - Enable People data in Agent Builder
  - Create an agent to answer org-specific directory questions
  - Test in Microsoft Teams


  **Why this matters:**


  **Business Impact:** Improves accuracy and personalization in enterprise workflows.


  **Personal Impact:** Users get tailored answers courtesy of context-rich data.


  **Additional resources:**


  **Learn:**


  [Add knowledge sources to your declarative agent in Microsoft 365 Copilot](https://learn.microsoft.com/en-us/microsoft-365-copilot/extensibility/agent-builder-add-knowledge)

### PowerPoint

- **Use your organization's approved assets in Copilot presentations** \[Mac, Windows, Web\]

  Create branded PowerPoint slides by pulling images and templates from your company's SharePoint asset library or Templafy integration.

  **Roadmap ID:** [496366](https://www.microsoft.com/microsoft-365/roadmap?msockid=2484525e9a9b66d4330b47329bb667c9&filters=&searchterms=496366)

  **Details:**

  **What changed:** PowerPoint Copilot integrates with SharePoint Organization Asset Library and Templafy for approved, compliant visuals.

  **Why:** Ensures quality designs aligned with corporate branding guidelines.

  **Try This:**

  - Configure SharePoint OAL or Templafy in Microsoft 365
  - Ask Copilot: "Create a marketing update deck using brand imagery."


  **Why this matters:**


  **Business impact:** Maintains brand identity across all content.


  **Personal Impact:** Saves design time by eliminating manual asset searching.


  **Additional resources:**


  **Learn:**


  [Create an organization assets library](https://learn.microsoft.com/en-us/sharepoint/organization-assets-library)

### Word

- **Referenced sources cited in drafted content** \[Windows\]

  Draft content with confidence as Copilot automatically includes citations, referencing the information in your text. This feature ensures accuracy and credibility, saving time on manual citation.

  **Roadmap ID:** [380842](https://www.microsoft.com/microsoft-365/roadmap?msockid=2484525e9a9b66d4330b47329bb667c9&filters=&searchterms=380842)

  **Details:**

  **What changed:** Copilot in Word now automatically generates citations when incorporating external information into your drafts. This process highlights references directly within the text, eliminating the need for manual citation entry.

  **Why:** Proper attribution is vital for maintaining credibility and avoiding plagiarism. This enhancement simplifies the citation process, ensuring academic and professional integrity without added effort.

  **Try This:**

  - While drafting in Word, ask Copilot: "Include citations for referenced content."
  - Use Copilot commands to review the generated citations for completeness and accuracy.
  - Compare the citation style used with your preferred or required academic formatting.


  **Why this matters:**


  **Business Impact:** Enhances the reliability of professional documents by ensuring proper attribution without a complex citation process.


  **Personal Impact:** Save time creating references, allowing more focus on content quality and creativity.

## December 10, 2025

Updates released between November 25, 2025, and December 10, 2025.

### Microsoft 365 Copilot app

- **Create polished videos faster with seamless editing and brand customization** \[Web\]

  Turn text prompts or PowerPoint, Word, and PDF files into high-quality videos. Create professional videos quickly with easier editing, brand integration, and media customization.

  **Roadmap ID:** [501560](https://www.microsoft.com//microsoft-365/roadmap?msockid=2484525e9a9b66d4330b47329bb667c9&filters=&searchterms=501560)

  **Details:**

  **What changed:** With the upgraded AI Video Creator in Microsoft 365 Copilot, use these new capabilities:

  - Transcript-based editing for greater control.
  - Access to your assets from OneDrive to update stock media.
  - Natural-sounding voiceovers for more authentic narration.
  - Brand color integration from Brand Kit.
  - A redesigned, scene-based structure for streamlined storytelling.
  - A cleaner editing experience for faster, intuitive workflows.


  **Why:** Video is a powerful medium, but creating professional-quality content is often time-consuming and technically challenging. This update removes roadblocks, so teams create compelling videos in a fraction of the time, using assets and brand elements they already have.


  **Try this:**


  - In Microsoft 365 Copilot, select Create and upload a Word, PDF, or PowerPoint file to generate your first video draft.
  - Click on a sentence in the transcript to cut or move sections without timeline complexity.
  - Add your official colors from Brand Kit, and swap generic visuals with your OneDrive media for a branded look.


  **Why this matters:**


  **Business Impact:** Reduce production bottlenecks and costs by empowering employees to create professional videos for training, marketing, or executive updates without third-party agencies.


  **Personal Impact:** Focus on the story, save hours on content creation, and eliminate the need for advanced video editing.


  **Additional resources:**


  **Support:**


  [Create a video with the Microsoft 365 Copilot app](https://support.microsoft.com/topic/create-a-video-with-the-microsoft-365-copilot-app-4edd41f6-a7ad-47d5-9a55-3fd25622c9f8)

- **Get AI-powered summaries with search views**

  AI Views creates AI-generated summaries to help you identify relevant content, quickly understand search results, and spend less time digging through documents.

  **Details:**

  **What changed:** AI Views is now available in the Microsoft 365 Copilot app search experience. It uses AI and Microsoft Graph signals to generate key point summaries for your search results directly on the Copilot Search page.

  **Why:** Users often waste time viewing multiple documents to find the right information. Now users see an AI and Microsoft Graph-powered overview of search results inside the Search results page.

  **Try this:**

  - Open the Microsoft 365 Copilot app and run a search for a project or topic you're working on.
  - Hover over any search result to see the Overview button
  - View a summary containing context and use the input box at the bottom to Ask Copilot.


  **Why this matters:**


  **Business Impact:** Teams makes decisions faster with quick access to context-rich summaries, improving productivity.


  **Personal Impact:** Get key information immediately, letting you focus on delivering results instead of hunting for data.

### Microsoft 365 Copilot extensibility

- **Access custom engine agents in multiple apps** \[Web\]

  Use custom engine agents in Word and Excel for a unified Copilot experience everywhere you work.

  **Roadmap ID:** [481136](https://www.microsoft.com/microsoft-365/roadmap?msockid=2484525e9a9b66d4330b47329bb667c9&filters=&searchterms=481136)

  **Details:**

  **What changed:** You can see more available custom engine agents across key Microsoft 365 surfaces.

  **Why:** Power users and developers can experience reduced fragmentation and improved workflow consistency.

  **Try this:**

  - In Outlook, activate a custom agent for summarizing incoming correspondence based on enterprise policies.


  **Why this matters:**


  **Business Impact:** Extends the value of custom Copilot agents across the Microsoft 365 ecosystem.


  **Personal Impact:** Offers a seamless experience without switching apps or rebuilding context.

- **Edit adaptive cards inline for a faster build process** \[Web\]

  Developers can now make quick inline edits on adaptive cards without leaving their design environment, reducing turnaround times.

  **Details:**

  **What changed:** Action.Execute now supports inline editing for adaptive cards.

  **Why:** Custom apps allow for unblocked rapid iteration.

  **Try this:**

  - While building a card, adjust field labels and actions inline instead of exporting and re-importing.


  **Why this matters:**


  **Business Impact:** Speeds up partner development cycles for faster app rollouts.


  **Personal Impact:** Eliminates frustrating small text or layout changes.


  **Additional resources:**


  **Learn:**


  [Allow inline editing of Adaptive Card responses](https://learn.microsoft.com/en-us/microsoft-365-copilot/extensibility/adaptive-card-edits)

- **Better security insights help you build confidently** \[Web\]

  Makers can now see an agent's detailed protection status and actionable recommendations in Copilot Studio.

  **Details:** What changed: Enforce protections accurately with a richer visualization of security posture for agents.

  **Why:** Creators are empowered to manage compliance and proactively minimize risks.

  **Try this:**

  - In Copilot Studio, check the security summary for your agent and apply suggested actions to meet policy.


  **Why this matters:**


  **Business Impact:** Maintains compliance without slowing innovation.


  **Personal Impact:** Gives creators peace of mind knowing their agents meet enterprise security standards.


  **Additional resources:**


  **Learn:**


  [Agent runtime protection status](https://learn.microsoft.com/en-us/microsoft-copilot-studio/security-agent-runtime-view)

### Microsoft 365 SharePoint

- **Add multiple SharePoint agents in one Teams conversation** \[Web\]

  Include more than one SharePoint agent in a single Teams chat, meeting, or channel. Teams and SharePoint now work together better for smarter collaboration.

  **Roadmap ID:**[481136](https://www.microsoft.com/microsoft-365/roadmap?msockid=2484525e9a9b66d4330b47329bb667c9&filters=&searchterms=481136)

  **Details:**

  **What changed:** Teams supports multiple SharePoint agents in a single group chat or channel.

  **Why:** Experience richer scenarios where multiple libraries or sites provide simultaneous insights.

  **Try this:**

  - In your project channel, add two different SharePoint agents to get instant answers about separate libraries.


  **Why this matters:**


  **Business Impact:** Keeps all content conversation in context, reducing silos across different sites.


  **Personal Impact:** Stay focused without the need to use multiple chats or apps to gather information.


  **Additional resources:**


  **Support:**


  [Share an agent from SharePoint in Teams](https://support.microsoft.com/office/share-an-agent-from-sharepoint-in-teams-6dcbf7b5-8c13-44e5-a68a-dbd71fb76ad3)

### Viva Glint

- **Multilingual support in Copilot for Viva Glint** \[Web\]

  Copilot in Viva Glint now understands and responds in multiple languages, helping employees interact in their preferred language.

  **Roadmap ID:** [508531](https://www.microsoft.com/microsoft-365/roadmap?filters=&searchterms=508531)

  **Details:**

  **What changed:** Copilot for Viva Glint detects the language of a user's input and responds in that same language.

  **Why:** Global teams often face challenges when a tool's language support is limited. This update improves accessibility and usability, enabling employees to share feedback or gain insights without language barriers.

  **Try this:**

  - Type a prompt in your preferred language within Viva Glint Copilot.
  - Review the response to confirm it matches the language you used.
  - Share this experience with multilingual teams to streamline feedback processes.


  **Why it Matters:**


  **Business Impact:** Enhances inclusivity and compliance, making it easier to manage employee feedback across multiple regions.


  **Personal Impact:** Saves time and reduces friction for employees who can now interact with Copilot in the language they're most comfortable with.

## November 25, 2025

Updates released between November 12, 2025, and November 25, 2025.

### Microsoft 365 admin center

- **Monitor Copilot usage with Capacity Packs** \[Mac\]

  Prepay for Copilot message consumption with Capacity Packs and track usage easily-reducing unexpected billing surprises.

  **Roadmap ID:** [503145](https://www.microsoft.com/microsoft-365/roadmap?filters=&searchterms=503145)

  ****Details:****

  **What changed:** Introduced prepaid Capacity Packs \(25,000 messages per month\) that apply before pay-as-you-go billing kicks in, plus usage monitoring in PPAC.

  ****Why:**** Improves cost governance and simplifies budgeting for large-scale Copilot deployments.

  **Try this:**

  - In Microsoft 365 admin center, purchase a Capacity Pack and monitor allocations in Power Platform admin center.


  **Why this matters:**


  **Business Impact:** Predicts and controls Copilot spend with flexible prepaid options.


  **Personal Impact:** Gives admins peace of mind with transparent, upfront budgeting.


  **Additional resources:**


  **Learn:**


  [Use Copilot Studio prepaid capacity packs for Microsoft 365 Copilot Chat and SharePoint agents](https://learn.microsoft.com/en-us/microsoft-365/copilot/pay-as-you-go/copilot-capacity-packs)

- **Reassign agent ownership with full control** \[Windows, Web\]

  Admins can now transfer ownership of shared agents, granting the new owner full edit and delete permissions and revoking all access from the previous owner.

  ****Roadmap ID:**** [502867](https://www.microsoft.com/microsoft-365/roadmap?msockid=2484525e9a9b66d4330b47329bb667c9&filters=&searchterms=502867)

  ****Details:****

  **What changed:** Ownership reassignment capabilities are now live in Microsoft 365 admin center, with edits propagating to agent files and associated content.

  ****Why:**** Helps maintain governance when employees leave roles or teams without disrupting workflows.

  **Try this:**

  - From admin center, select a shared agent > choose **Reassign Owner** > confirm access update.


  **Why this matters:**


  **Business Impact:** Reduces compliance and business continuity risks during staff transitions.


  **Personal Impact:** Admins can easily manage lifecycle changes without escalating to engineering teams.


  **Additional resources:**


  **Learn:**


  [Reassign an agent's owner with PowerShell](https://learn.microsoft.com/en-us/power-platform/release-plan/2025wave2/microsoft-copilot-studio/reassign-agents-owner-powershell)

- **Restrict org-wide agent sharing for better governance** \[Web\]

  Manage who can create org-wide sharing links for Copilot Studio agents to maintain tighter organizational control.

  ****Roadmap ID:**** [500376](https://www.microsoft.com/microsoft-365/roadmap?filters=&searchterms=500376)

  ****Details:****

  **What changed:** New admin control blocks or enables org-wide visibility for Copilot agents.

  ****Why:**** Prevents accidental overexposure of sensitive workflows while allowing flexibility for approved agents.

  **Try this:**

  - In admin center, update **Sharing Settings** to limit org-wide agent links to specific roles or groups.


  **Why this matters:**


  **Business Impact:** Reduces risk of unauthorized data exposure.


  **Personal Impact:** Gives admins full confidence before rolling out custom agents at scale

### Microsoft 365 Copilot app

- **Customize audio overviews for Copilot notebooks** \[Web\]

  Personalize the content and tone of audio summaries from your Copilot notebooks by using natural language input.

  ****Roadmap ID:**** [499150](https://www.microsoft.com/microsoft-365/roadmap?filters=&searchterms=499150)

  ****Details:****

  **What changed:** Notebook audio overviews are now creator-driven with prompt-based customization.

  ****Why:**** Supports diverse use cases-like executive briefings or quick-learning sessions-without extra editing work.

  **Try this:**

  - Type: *"Create an upbeat 2-minute audio summary focused on key sales drivers."*


  **Why this matters:**


  **Business Impact:** Enhances the value of notebooks for communication and leadership updates.


  **Personal Impact:** Saves time creating engaging summaries without additional tools.


  **Additional resources:**


  **Support:**


  [Get an audio overview of your notebook with Microsoft 365 Copilot Notebooks](https://support.microsoft.com/topic/get-an-audio-overview-of-your-notebook-with-microsoft-365-copilot-notebooks-a22df989-b9cd-47fb-abac-e888d8f10cd9)

### Microsoft 365 Copilot Chat

- **Access shared mailboxes in Copilot Chat** \[Android, Windows, iOS, Mac, Web\]

  Copilot Chat now connects to shared mailboxes, so team-based conversations are more informed and collaborative.

  ****Roadmap ID:**** [488797](https://www.microsoft.com/microsoft-365/roadmap?msockid=2484525e9a9b66d4330b47329bb667c9&filters=&searchterms=488797)

  ****Details:****

  **What changed:** Users with shared mailbox permissions can ground Copilot responses in shared mail content, just like their own emails.

  ****Why:**** Eliminates context gaps in team workflows and improves shared visibility on projects.

  **Try this:**

  - Tell Copilot: *"Summarize recent emails in [mailbox@domain.com](mailto:mailbox@domain.com) mailbox."*
  - Tell Copilot: *"List all the emails around \(topic\) from \(mailbox@domain.com\) > mailbox."*


  **Why this matters:**


  **Business Impact:** Ensures customer responses or project updates aren't missed when responsibility spans multiple team members.


  **Personal Impact:** Reduces copying and manual email checks across shared accounts-Copilot does it for you.


  **Additional resources:**


  **Support:**


  [Use Copilot in shared mailboxes and delegate mailboxes](https://support.microsoft.com/topic/use-copilot-in-shared-mailboxes-and-delegate-mailboxes-3e7e5130-eabe-4c19-94ea-117b2a4c14d6)

- **Find files faster with improved Copilot Chat filters** \[Windows, Web\]

  Use new file type and people refiners in Copilot Chat to quickly get to the right file without sifting through results.

  ****Roadmap ID:**** [481136](https://www.microsoft.com/microsoft-365/roadmap?filters=&searchterms=481136)

  ****Details:****

  **What changed:** Introduced filters for file types and collaborators in Copilot Chat's CIQ Files tab.

  ****Why:**** Cuts down time spent filtering manually, especially in large file repositories.

  **Try this:**

  - In chat, search: *"Quarterly report"* → Filter by **Excel** and collaborator name.


  **Why this matters:**


  **Business Impact:** Improves productivity and reduces meeting prep time.


  **Personal Impact:** Less frustration-find what you need in seconds.

- **Talk to Copilot with voice for faster hands-free work** \[Android, Windows, iOS, Mac, Web\]

  Speak to Copilot naturally on mobile or desktop to prepare for meetings, brainstorm ideas, or catch up on work-hands-free and grounded in work data.

  **Roadmap ID:** [481138](https://www.microsoft.com/microsoft-365/roadmap?msockid=2484525e9a9b66d4330b47329bb667c9&filters=&searchterms=481138)

  ****Details:****

  **What changed:** Copilot now supports voice input, enabling natural, conversational interactions in the Microsoft 365 Copilot app on mobile, desktop and the web and across Microsoft 365 apps, starting with Outlook, Word and PowerPoint.

  ****Why:**** Professionals need faster, more intuitive ways to engage with AI during their flow of work, especially when multitasking or on the move. Voice removes friction, letting you work where typing isn't practical.

  **Try this:**

  - Say: *"Confirm the agenda and attendee list for my next meeting"*.
  - Try: *"Create a quick list of next steps from my recent meeting notes."*
  - Ask: *"Summarize this document in five key points."*


  **Why this Matters:**


  **Business Impact:** Voice drives productivity and inclusivity through natural interactions that increase engagement, accelerate task completion and reduce downtime.


  **Personal Impact:** Work more comfortably and naturally while saving time, gaining efficiency and giving you the flexibility to use Copilot on the go or at your desk.


  **Additional resources:**


  **Support:**


  [Get started with voice features in Microsoft 365 Copilot](https://support.microsoft.com/topic/get-started-with-voice-features-in-microsoft-365-copilot-9262968d-565e-470c-a04b-991eb8e0d1ea?preview=true)

### Microsoft 365 Copilot extensibility

- **Access Custom engine Agents on Microsoft 365 Copilot chat on mobile** \[Android, iOS\]

  You can now interact with your organization's custom engine agents directly from your mobile device \(iOS and Android\), making Copilot even more adaptable to your workflows on the go. Whether you're away from your desk or managing tasks during a commute, your tailored business logic and automations are always at your fingertips.

  ****Details:****

  **What changed:** Support for custom engine agents is now available on the Microsoft 365 mobile experience \(iOS and Android\). You can access the same business-specific workflows and logic you have on desktop, ensuring uninterrupted productivity.

  ****Why:**** Teams needs consistent, personalized Copilot functionality no matter where they work. Bringing extensibility to mobile ensures employees stay productive and connected-even when away from their primary workstation.

  **Try this:**

  - Open the Microsoft 365 mobile app, launch Copilot, and activate one of your custom engine agents.
  - **Ask Copilot:** *"Run our expense approval workflow and update me on pending approvals."*


  **Why this matters:**


  **Business Impact:** Keep critical business processes running smoothly even when employees are mobile, reducing delays in approvals and operations.


  **Personal Impact:** Enjoy the same customized Copilot experience wherever you work, saving time and reducing context-switching throughout your day.


  **Additional resources:**


  **Learn:**


  [Custom engine agents for Microsoft 365 overview](https://learn.microsoft.com/en-us/microsoft-365-copilot/extensibility/overview-custom-engine-agent)

- **Enhanced search in Agent Store for easier discovery** \[Windows, Web\]

  Finding the right agents in the Copilot Agent Store just got faster and smarter. Enjoy a streamlined search experience with typeahead suggestions and a clean results page-making it simple to locate exactly what you need without wasted time.

  ****Roadmap ID:**** [502617](https://www.microsoft.com/microsoft-365/roadmap?filters=&searchterms=502617)

  ****Details:****

  **What changed:** The Agent Store now includes enhanced search capabilities featuring a responsive drop-down menu, typeahead functionality for quick suggestions as you type, and a dedicated search results page for improved clarity.

  ****Why:**** Customers need a quicker, more intuitive way to explore and find agents. By reducing friction in discovery, you can deploy and extend Copilot solutions with less effort and greater confidence.

  **Try this:**

  - Start typing an agent name in the search bar to see type-ahead suggestions instantly.
  - Use the new full results page for a complete view of matching agents.


  **Why this matters:**


  **Business Impact:** Accelerate adoption by making it easy for teams to find and integrate the right Copilot tools quickly, boosting productivity across the organization.


  **Personal Impact:** Save time and reduce frustration with simple, intuitive search that helps you get back to meaningful work faster.

- **Export detailed agent metadata for better governance** \[Web\]

  Inventory exports now include richer metadata like capabilities, data sources, and creator details-empowering better auditing and lifecycle control.

  ****Roadmap ID:**** [502878](https://www.microsoft.com/microsoft-365/roadmap?filters=&searchterms=502878)

  ****Details:****

  **What changed:** Added expanded metadata fields to Microsoft 365 admin center's agent export.

  ****Why:**** Provides admins with transparency over how agents are built, what they access, and by whom.

  **Try this:**

  - Start agent inventory and filter by **Created By** or **Data Sources** to review compliance.


  **Why this matters:**


  **Business Impact:** Strengthens governance for AI usage across the organization.


  **Personal Impact:** Saves admins from chasing multiple tools for visibility-everything is in one export.


  **Additional resources:**


  **Learn:**


  [Export to Excel](https://learn.microsoft.com/en-us/microsoft-365/admin/manage/agent-registry#export-to-excel)

- **Support Message Extensions as Declarative Agents on Mobile** \[Android, iOS\]

  Stay productive on the move with support for message extensions as declarative agents in Copilot on iOS and Android. These extensions simplify workflows like inserting quick snippets, accessing integrated apps, or triggering processes directly from your mobile interface.

  ****Details:****

  **What changed:** Message extensions based Declarative agents" instead of "Message extensions as declarative agents.

  ****Why:**** Workers increasingly use mobile as their primary device for timely communication and task management. Extending message-based workflows to mobile keeps teams efficient and responsive.

  **Try this:**

  - In a Teams chat on your mobile app, use Copilot to insert a dynamic update from a connected app with a message extension.
  - **Ask Copilot:** *"Insert the latest sales figures into this conversation using our message extension agent."*


  **Why this matters:**


  **Business Impact:** Maintain seamless workflows across devices, ensuring real-time communication and agility for distributed teams.


  **Personal Impact:** Eliminate the frustration of being restricted to desktop for advanced actions-get the information and tools you need on the go.


  **Additional resources:**


  **Learn:**


  [Extend bot-based message extension as agent for Microsoft 365 Copilot](https://learn.microsoft.com/en-us/microsoftteams/platform/messaging-extensions/build-bot-based-agent?tabs=visual-studio-code)

- **Unified permissions management for agents** \[Windows, Web\]

  View detailed permissions for each Copilot agent in one place-including app dependencies, delegated permissions, and associated risks. Admins can grant consent directly, simplifying governance and deployment.

  ****Roadmap ID:**** [502617](https://www.microsoft.com/microsoft-365/roadmap?filters=&searchterms=502617)

  ****Details:****

  **What changed:** Unified Permissions Management now provides a clear view of all required applications, delegated permissions, and associated risk levels from a central console.

  ****Why:**** Helps admins ensure security and compliance while reducing friction in agent approval workflows.

  **Try this:**

  - Go to the Permissions tab in Microsoft 365 admin center to review and approve agent permissions.
  - Filter by risk level to prioritize oversight where needed.


  **Why This Matters:**


  **Business Impact:** Strengthens compliance and governance while accelerating agent deployment.


  **Personal Impact:** Simplifies decision-making for IT teams, saving hours of manual checks.


  **Additional resources:**


  **Learn:**


  [Agent Registry in the Microsoft 365 admin center](https://learn.microsoft.com/en-us/microsoft-365/admin/manage/agent-registry)

### Microsoft 365 Copilot Studio

- **Control org-wide agent sharing from one place** \[Web\]

  Admins now have granular control over whether agents built in Agent Builder can be shared with links that work for anyone in the organization, ensuring policies are followed.

  ****Details:****

  **What changed:** Admins can restrict or disable organization-wide sharing of agents built in Agent Builder.

  ****Why:**** This strengthens governance, prevents agent sprawl, and supports safe adoption at scale.

  **Try this:**

  - In Microsoft 365 admin center, go to Agents > Settings > Sharing and configure who can share agent links that work for anyone in the organization.


  **Why this matters:**


  **Business Impact:** Strengthens governance, prevents oversharing, and supports compliance as agent adoption needs evolve.


  **Personal Impact:** Gives admins confidence and transparency when scaling adoption. Makers receive clear guidance on enforced admin sharing policies


  **Additional resources:**


  **Learn:**


  [Sharing](https://learn.microsoft.com/en-us/microsoft-365/admin/manage/agent-settings#sharing)


  **Demo:**


  [Admin control for org-wide agent sharing links](https://microsoft-my.sharepoint-df.com/personal/sophieroy_microsoft_com/_layouts/15/stream.aspx?id=%2Fpersonal%2Fsophieroy%5Fmicrosoft%5Fcom%2FDocuments%2FRecordings%2FDemo%20Admin%20control%20for%20org%2Dwide%20agent%20sharing%20links%2D20250926%5F155245%2DMeeting%20Recording%2Emp4&nav=eyJyZWZlcnJhbEluZm8iOnsicmVmZXJyYWxBcHAiOiJTdHJlYW1XZWJBcHAiLCJyZWZlcnJhbFZpZXciOiJTaGFyZURpYWxvZy1MaW5rIiwicmVmZXJyYWxBcHBQbGF0Zm9ybSI6IldlYiIsInJlZmVycmFsTW9kZSI6InZpZXcifX0&referrer=StreamWebApp%2EWeb&referrerScenario=AddressBarCopied%2Eview%2Ea632fb0d%2D5e4c%2D4501%2D92a6%2D1c16c4381542&ct=1764029038871&or=Teams%2DHL&ga=1&gaS=47&isDarkMode=true)


  **Blogs:**


  [Manage and govern at scale](https://www.microsoft.com/microsoft-copilot/blog/copilot-studio/whats-new-in-copilot-studio-october-2025/#manage-and-govern-at-scale)

### Microsoft 365 PowerPoint

- **Reference Loop or Page in presentations** \[Mac, Windows, Web\]

  When building a presentation with Copilot, you can now pull in content from Loop components or pages for fully integrated and up-to-date slides.

  ****Roadmap ID:**** [500864](https://www.microsoft.com/microsoft-365/roadmap?msockid=2484525e9a9b66d4330b47329bb667c9&filters=&searchterms=500864)

  ****Details:****

  **What changed:** Copilot for PowerPoint supports referencing Loop components and pages across PC, Mac, and web.

  ****Why:**** Ensures your presentations reflect the latest collaborative content without manual copy-paste.

  **Try this:**

  - **Ask Copilot:** *"Create a status update deck using the project details from our Loop page."*


  **Why this matters:**


  **Business Impact:** Align updates across teams without tedious content migration.


  **Personal Impact:** Save time by reusing the content you already co-created, in just one step.

### Microsoft 365 SharePoint

- **Copilot skills for smarter SharePoint administration** \[Web\]

  Use Copilot to get step-by-step guidance for admin tasks and advanced site searches based on multiple criteria-all from the SharePoint admin center.

  ****Roadmap ID:**** [501455](https://www.microsoft.com/microsoft-365/roadmap?msockid=2484525e9a9b66d4330b47329bb667c9&filters=&searchterms=501455)

  ****Details:****

  **What changed:** Added two major skills:

  - Guided task instructions \(for example, fixing over-permissioned sites\)
  - Multi-criteria search for sites \(for example, inactive + shared externally\)


  ****Why:**** Improves efficiency and accuracy in managing large SharePoint environments.


  **Try this:**


  - **Ask Copilot:** *"Find all inactive sites over 60 days shared externally."*
  - **Prompt:** *"Show me steps to reduce permissions for over-shared sites."*


  **Why this matters:**


  **Business Impact:** Reduces security risk and speeds workload management.


  **Personal Impact:** Saves admins hours of navigating settings-answers are instant.


  **Additional resources:**


  **Learn:**


  [Copilot skills in SharePoint admin centers](https://learn.microsoft.com/en-us/sharepoint/sharepoint-copilot-best-practices)

## November 12, 2025

Updates released between October 28, 2025, and November 12, 2025.

### Copilot extensibility

- **Custom Agents can be used from inside of Office Applications** \[Web\]

  Supporting Custom Engine Agents inside Office applications offers numerous advantages that significantly enhance user experience and productivity. Firstly, it allows for highly tailored automation and customization, enabling users to create and deploy agents that cater specifically to their unique workflows and business needs.

  This flexibility can lead to more efficient processes and reduced manual effort. Secondly, Custom Engine Agents can integrate seamlessly with existing Office functionalities, providing a cohesive and unified user experience. This integration ensures that users can leverage the full power of Office applications while benefiting from the specialized capabilities of their custom agents.

  Additionally, these agents can help in automating repetitive tasks, improving accuracy, and freeing up time for more strategic activities. Overall, the support for Custom Engine Agents within Office applications empowers users to optimize their work environment, drive innovation, and achieve higher levels of productivity. [Learn more](https://learn.microsoft.com/en-us/microsoft-365-copilot/extensibility/agents-overview#custom-engine-agents).

### Copilot Studio

- **Quarantine and block unsecured agents** \[Web\]

  Improve security and compliance by using PowerShell to quarantine Copilot agents that don't meet policy requirements. This gives admins more control to prevent risks while investigating and resolving issues without disrupting business operations. [Learn more](https://learn.microsoft.com/en-us/microsoft-copilot-studio/admin-quarantine-api).

### Excel

- **Build and analyze surveys with ease using Surveys Agent** \[Windows, Mac, Web\]

  Let Surveys Agent handle the heavy lifting-from writing questions to launching surveys and breaking down results. It's like having a professional researcher inside Copilot, helping you make quick, data-driven decisions. [Learn more](https://aka.ms/SurveysAgentAvailable).

### Microsoft 365 admin center

- **Block SharePoint agents from Agents and connectors page** \[Web\]

  Administrators have the ability to oversee SharePoint agents as shared applications within the Agents & connectors section \(formerly known as integrated apps\) of the Microsoft 365 admin center. They can access a list of all shared SharePoint agents and have the option to block or unblock agents from being utilized on M365 Copilot. [Learn more](https://learn.microsoft.com/en-us/sharepoint/manage-access-agents-in-sharepoint).
- **New Enhancements in Organizational Data Ingestion in Microsoft 365** \[Web\]

  Experience a powerful upgrade with new attribute access and mapping, connectors, and a dedicated admin role. Streamline data ingestion from multiple sources to Viva Insights and Glint, simplifying data management and enhancing workflow efficiency.

### Microsoft 365 Copilot Chat

- **RSVP status-based meeting search in Copilot Chat** \[Android, Windows, Web\]

  Quickly find meetings based on RSVP status-either your own or others'. This feature helps you stay organized by surfacing RSVP details for upcoming events, so you can track commitments and follow up with attendees.

  **Roadmap:** [499429](https://www.microsoft.com/microsoft-365/roadmap?filters=&searchterms=499429)

  **Try this:**

  Open Microsoft 365 Chat. Enter queries like:

  - "Meetings I accepted this week"
  - "Meetings I have not RSVPed this week"
  - "Who all have accepted the Scrum meeting?"


  View results showing RSVP details for yourself or attendees.


  **Why this matters:**


  **Business:** Improves meeting management and accountability by enabling quick visibility into attendee responses, reducing missed follow-ups.


  **Personal:** Helps you stay on top of your schedule and commitments without manually checking each calendar invite.

- **Iterate on images with multi-turn editing** \[Windows, Mac, Web\]

  Copilot Chat now makes visual creation more flexible and intuitive. Upload reference images, edit them step by step, and maintain consistency across versions-perfect for refining designs for presentations, social posts, or print.
- **Updated UI for the Copilot Chat Navigation Pane in Teams** \[Web\]

  The navigation pane has been repositioned from the right side to the left, offering a more intuitive layout. Despite the shift, it continues to host agents and conversation history, ensuring continuity in user experience. This redesign introduces new features, including access to the "All Conversations" page, which provides a comprehensive view of chat history. The change aims to enhance usability and streamline navigation within Copilot Chat.

### Microsoft 365 Copilot Studio

- **Upload up to 1000 files for SharePoint and OneDrive training** \[Web\]

  Makers can now upload up to 1000 documents per agent when building custom Copilot experiences-five times the previous limit-making it easier to create well-informed, specialized solutions. [Learn more](https://learn.microsoft.com/en-us/power-platform/release-plan/2025wave1/microsoft-copilot-studio/use-up-1000-files-per-agent-sharepoint-onedrive-uploads).

### Outlook

- **Intelligent Draft Agenda with Copilot** \[Web\]

  Meetings are more successful with agendas. They align everyone on meeting goals, get the right people to attend, and keep discussions focused, leading to more productive and effective work. With Intelligent Draft Agenda, Copilot helps you create agendas for your meetings and streamlines your workday. When creating or editing an event in Calendar, Copilot will propose an agenda, ready for you to review, edit, and send as part of your meeting invite. [Learn more](https://support.microsoft.com/topic/31a44dfa-62bb-4751-82c4-14327a26759f).

### PowerPoint

- **Create new presentations without overwriting your original** \[Windows, Mac, Web\]

  When you use Copilot to generate a presentation from an existing one, it now creates a separate file-keeping your original content safe for future use. Perfect for creating tailored decks without starting from scratch. [Learn more](https://support.microsoft.com/office/create-a-new-presentation-with-copilot-in-powerpoint-3222ee03-f5a4-4d27-8642-9c387ab4854d).

### Viva Insights

- **Copilot Chat \(Web\) in Teams & Outlook metrics** \[Windows, Web\]

  Copilot Analytics users can now view metrics about their Copilot Chat \(Web\) usage in Teams and Outlook. These updates enable users to better understand both active usage and action counts in Teams and Outlook and will be available in the Copilot Dashboard, as well as with additional query support. [Learn more](https://learn.microsoft.com/en-us/viva/insights/advanced/reference/metrics).

## October 28, 2025

Updates released between October 15, 2025, and October 28, 2025.

### Copilot extensibility

- **@mention capability for mainline Copilot Chat** \[Android, iOS\]

  Use @mention in Copilot Chat to direct interactions to specific agents, ensuring focused and relevant responses from Copilot.
- **Static tab for custom agents in Teams meetings** \[Windows, Web\]

  Developers can now add static tabs in their custom engine agents using Teams Toolkit, enhancing experiences during meetings and calls.

### Microsoft 365 Copilot

- **Private previews in shared page edits** \[Web\]

  After edits in shared pages, view suggestions as private previews to refine and finalize content before public application.

### Microsoft 365 Copilot Chat

- **Focus mode in Teams** \[Web\]

  Enhance your concentration with Focus Mode in Teams, which hides unnecessary UI elements and provides alerts when launching the full app from chat.
- **Launch full app from side panes in Copilot Chat**

  Easily transition from the side pane in Microsoft 365 apps to the full Copilot app with a dedicated button, simplifying access to advanced features.
- **Stay informed with email alerts for scheduled prompts",** \[Web\]

  Get notified when your scheduled Copilot prompts finish running. Email notifications ensure you never miss results and can act on insights right away-no need to keep checking manually. [Learn more](https://learn.microsoft.com/en-us/power-platform/admin/recurring-copilot-prompts).

### Microsoft Planner

- **Copilot faster with new Planner button** \[Web\]

  A new floating action button \(FAB\) gives you quick, one-click access to the Project Manager Agent, making it easy to launch Copilot or start a chat without losing your place in your plan. [Learn more](https://techcommunity.microsoft.com/blog/plannerblog/what%E2%80%99s-new-in-microsoft-planner-%E2%80%93-august-2025/4449301).
- **Get a project manager agent in all premium plans",** \[Windows, Web\]

  The project manager agent is now included in all premium Planner plans. It helps you move work forward by creating plans from goals, executing tasks, and acting on feedback-all with less manual effort.
- **Get task recommendations grounded in real-time web data** \[Web\]

  Copilot's Project Manager Agent now includes web-grounded responses with source links, ensuring task updates and recommendations are timely, credible, and actionable.

### Outlook

- **Expanded coverage and Improvements to Preparing for Meetings with Copilot** \[Windows, Web\]

  Preparing for meetings can be time and effort-intensive. New enhancements to Copilot's meeting preparation experience help streamline the process. Directly within the Outlook meeting event form, Copilot can now proactively generate key insights to help you prepare for specific meetings. Copilot also suggests additional ways that it can help you prepare, from finding the pre-reads to learning more about the meeting's intended outcome. User can then continue the conversation via chat, and get answers to additional questions that are top-of-mind. In addition, Copilot now supports all meeting types - including 1:1 meetings - via the meeting preparation experience. [Learn more](https://support.microsoft.com/topic/prepare-for-your-meeting-with-copilot-f23326fc-7721-45f1-875e-23e77aaf3d89).

### PowerPoint

- **Copilot now offers an on-canvas experience for generating speaker notes** \[Mac, Web, iOS\]

  Now, Copilot in PowerPoint offers an on-canvas experience to generate speaker notes in place of the previous chat experience. [Learn more](https://support.microsoft.com/topic/add-speaker-notes-to-your-presentations-using-copilot-7139266b-8a1d-4056-8e30-4edcc4d80873).
- **PPT Copilot now offers an on-canvas experience for translating presentation** \[Mac, Web, iOS\]

  Now, when creating a presentation using Copilot from an existing presentation, it creates the new presentation in a new file without affecting the original presentation  
  [Learn more.](https://support.microsoft.com/topic/rewrite-text-with-copilot-in-powerpoint-d70b140b-bb3f-46b7-be64-ceec526a8dcd#:%7E:text=Select%20the%20textbox%20containing%20the%20text%20you%20want,for%20general%20improvements%20in%20grammar%2C%20spelling%2C%20and%20clarity.)

### Teams

- **Teams chats in ContextIQ** \[Web\]

  Enhance Copilot Chat prompts by searching and selecting Teams chats within ContextIQ, streamlining your workflow and improving context accuracy.  
  [Learn more.](https://support.microsoft.com/topic/using-context-iq-to-refer-to-specific-files-people-and-more-in-microsoft-365-copilot-and-copilot-chat-272ac2c1-c5f7-49c9-8a42-2a8a87846fa0)
- **Use Copilot in a call without recording or transcribing** \[Windows, Mac\]

  Now, users can benefit from Copilot during live Teams calls with sensitive conversations where a persistent record is not desired. When the admin enables this option, users can initiate Copilot without transcription or recording simply through clicking the Copilot button in the header menu, so they can use important Copilot administrative tasks such as capturing key points, task owners, and next steps, enabling participants to stay focused on the content of the call.  
  [Learn more.](https://learn.microsoft.com/en-us/microsoftteams/copilot-teams-calling-transcription#only-during-the-call)

### Viva Insights

- **Weekly user insights in Copilot Studio agent reports",** \[Windows, Mac, Web\]

  Copilot Studio reports now include weekly active user counts and provide aggregated data on a weekly basis for consistency across reporting. These updates make it easier to track engagement trends for planning and adoption. [Learn more](https://learn.microsoft.com/en-us/viva/insights/advanced/analyst/templates/copilot-studio-agents).

### Word

- **Instantly get helpful options from Copilot** \[Mac\]

  The Copilot icon in your document margin gives you various actions you can take on your selected text. One click lets you rewrite, get writing suggestions, and more

## October 15, 2025

Updates released between September 30, 2025, and October 15, 2025.

### Copilot extensibility

- **Context-aware search ranking** \[Windows, Web\]

  Search now delivers more personalized results by using user context and engagement signals, enhanced by the Microsoft 365 Copilot extension. This ensures that search results are intuitive and relevant.  
  [Learn more.](https://learn.microsoft.com/en-us/microsoftsearch/crossover-browser)

### Microsoft 365 admin center

- **Harmful content protection toggle** \[Web\]

  Admins can now control how users interact with harmful content protection settings in Microsoft 365 Copilot Chat. This is crucial for specialized roles like legal or investigative teams that may need exposure to sensitive content.  
  [Learn more.](https://learn.microsoft.com/en-us/microsoft-365/copilot/harmful-content-protection-copilot-chat)
- **Historical Data Upload Support in Organizational Data in Microsoft 365** \[Web\]

  Enhance your data management by uploading historical HR data manually via CSV files. If the historical option is selected, admins can assign an effective date for precise processing by apps like Viva Insights. This ensures consistent and accurate data across Microsoft 365 and Viva apps.  
  [Learn more.](https://learn.microsoft.com/en-us/viva/import-orgdata#step-5--make-retroactive-updates-to-existing-data)
- **Manage table list views with security roles** \[Web\]

  Enhance security and streamline operations by managing table list views according to specific security roles. This feature empowers administrators with increased control and customization over data access.  
  [Learn more.](https://learn.microsoft.com/en-us/power-apps/maker/model-driven-apps/manage-view-access)
- **Prepurchase capacity packs for chat** \[Web\]

  Admins can apply pre-purchased message capacity packs to Microsoft 365 Copilot Chat and other agent scenarios before incurring pay-as-you-go charges, optimizing budget management.  
  [Learn more.](https://learn.microsoft.com/en-us/microsoft-365/copilot/pay-as-you-go/copilot-capacity-packs)

### Microsoft 365 Copilot Chat

- **Create new images using reference uploads** \[Windows, Mac, Web\]

  Enhance image creation by uploading reference images in Copilot Chat, using them as creative foundations for new visuals.
- **Image generation with multiple aspect ratios** \[Windows, Mac, Web\]

  Generate images in various aspect ratios to suit any need, from social media to presentations, with landscape, portrait, and square options in Copilot Chat.
- **Inline citations and references in side pane** \[Web\]

  Improve clarity and transparency by replacing numeric citations with source-based citation pills. Access all sources, both cited and uncited, directly in the side pane for a better credibility assessment and exploration.

### Microsoft Loop

- **New file extension for Copilot pages** \[Web\]

  Introducing ".page", a new extension for Copilot pages that supports admin toggles, sensitivity labels, and compliance features just like ".loop". [Learn more.](https://support.microsoft.com/topic/get-started-with-microsoft-365-copilot-pages-6674bd51-9ff5-42c4-9256-44d9428a726f)

### Viva Learning

- **Providing users with notifications about Copilot Academy in Teams**

  If a user has a Microsoft 365 Copilot license, they receive notifications in Teams about the Copilot Academy through Viva Learning. This helps users stay informed about Copilot Academy enhancements with monthly reminders.  
  [Learn more.](https://learn.microsoft.com/en-us/viva/learning/academy-copilot)

## September 30, 2025

Updates released between September 16, 2025, and September 30, 2025.

### Copilot extensibility

- **Agents support for Copilot Chat and pay-as-you-go on Microsoft 365 Copilot Mobile** \[Android, iOS\]

  Agents support for pay-as-you-go and Copilot chat users in now supported on the Microsoft 365 Copilot mobile app for easy usage.
- **Enable ISV discovery through connector catalog** \[Web\]

  Discover Independent Software Vendor \(ISV\) built copilot connectors seamlessly through the connector catalog in the admin center, enhancing integration and functionality across your enterprise applications.
- **Pin agents for tenant-wide visibility** \[Web\]

  Admins can now pin Copilot agents for all users or specific groups within their tenant, ensuring greater accessibility and relevance of popular agents for user tasks. [Learn more.](https://learn.microsoft.com/en-us/microsoft-365/admin/manage/manage-pinning-agents)
- **Prompt grounding from specific sources**

  Users can ground the prompt to a specific content/data source directly from Microsoft 365 Copilot chat using CIQ Peek menu \(/\).

### Microsoft 365 admin center

- **Usage reports for Copilot search** \[Android, Windows, iOS, Mac, Web\]

  Administrators gain insights into organizational adoption of Copilot search with new usage reports. Track total search queries, assess trends, and analyze user activity to drive effective adoption strategies. [Learn more.](https://learn.microsoft.com/en-us/microsoft-365/admin/activity-reports/microsoft-365-copilot-search-usage)

### Microsoft 365 Copilot Chat

- **Copilot Chat now understands attached files like Word, Excel, PowerPoint, PDF, Text, JSON, and XML.** \[Android, Windows, iOS, Mac, Web\]

  Users can gather insights not only from the email content but also from attached files, enabling comprehensive context understanding.
- **Copilot Chat summarization in Microsoft Edge context menu** \[Web\]

  Unpack web pages and ask questions swiftly with a new Copilot Chat summarization option in the Edge context menu for efficient browsing. [Learn more.](https://support.microsoft.com/topic/using-microsoft-copilot-in-edge-at-work-012b3674-bab8-4f99-8585-c961dac68642)
- **Easily select meeting series in Copilot Chat** \[Windows, Web\]

  Effortlessly choose meeting series and related instances directly from the Context IQ \(CIQ\) menu to include in your Copilot Chat prompts.
- **Support for analyzing images in uploaded files** \[Windows, Web\]

  Analyze embedded images within PDF, DOCX, and PPTX files uploaded to Copilot. Ask Copilot to interpret image content, such as "analyze the image on page 4," and receive insights based on the visual data.
- **Upload multiple images for creative prompts** \[Android, iOS, Web\]

  Now upload multiple images into Copilot Chat prompts at once to enhance creative reasoning and generate new content with varied inspiration.

### Outlook

- **Highlight and rewrite email drafts with Copilot** \[Windows\]

  In classic Outlook for Windows, select parts of your email draft and use Copilot to rewrite with precision. Modify tone and length according to your needs, optimizing communication.

### PowerPoint

- **Copilot generates the new presentation in a new file when starting from an existing presentation** \[Web\]

  Now, when creating a presentation using Copilot from an existing presentation, it creates the new presentation in a new file without affecting the original presentation. [Learn more.](https://support.microsoft.com/office/create-a-new-presentation-with-copilot-in-powerpoint-3222ee03-f5a4-4d27-8642-9c387ab4854d)
- **Seamlessly add topics with Copilot** \[Mac, Web, Windows\]

  Enhance your presentations by adding new topics with slides via Copilot, ensuring consistency in look and feel with existing content. [Learn more.](https://support.microsoft.com/topic/add-topics-to-your-existing-powerpoint-presentation-with-copilot-7439e3d7-5b7f-4886-8d01-5e7f285fd99b?preview=true)

### SharePoint

- **AI-driven site content and policy comparison**

  Use AI to compare site contents and policies, identifying similar files and differing settings. This empowers admins to apply consistent policies across similar sites, enhancing security and governance. [Learn more.](https://learn.microsoft.com/en-us/sharepoint/site-policy-comparison)

## September 16, 2025

Updates released between September 3, 2025, and September 16, 2025.

### Copilot extensibility

- **Improve Response accuracy when handling large files in File Upload/CIQ.** \[Windows, Web\]

  Experience improved summaries and increased accuracy when querying long documents and PDFs. Copilot efficiently distills information, helping you extract insights and answer questions faster.
- **Makers can scope agents on subset of connections**

  Makers can reuse or build agents using connections by using only a subset of the ingested content to get more granular control on agent data. [Learn more.](https://learn.microsoft.com/en-us/microsoft-365-copilot/extensibility/copilot-studio-lite-knowledge?branch=main&branchFallbackFrom=pr-en-us-1060)
- **Mobile support for Analyst agent on Android and iOS** \[iOS, Android\]

  Access and utilize the Analyst agent on iOS and Android devices using the Microsoft 365 Copilot app, ensuring seamless mobile insights and analysis.
- **ServiceNow Connectors custom URL configuration** \[Windows, Web\]

  Enhance ServiceNow Connectors with customizable URLs for articles, tickets, and catalog items, tailored to organizational preferences.  
  [Learn more.](https://learn.microsoft.com/en-us/microsoftsearch/configure-connector#customize-values-for-certain-schema-properties)
- **Viral link sharing on M365 Copilot Mobile \(Android and iOS\)** \[Android, iOS\]

  Simplify collaboration with Agents with support for agent viral links on M365 Copilot app on Mobile, enhancing accessibility and engagement.

### Copilot Studio

- **Analyze ROI of autonomous agents in Analytics tab** \[Web\]

  Use Microsoft Copilot Studio ROI Analytics to define and calculate time or money saved for successful autonomous agent runs, enhancing decision-making efficiency. [Learn more](https://learn.microsoft.com/en-us/microsoft-copilot-studio/analytics-cost-savings)
- **Enhanced search and navigation in Copilot Studio** \[Web\]

  Boost productivity with streamlined search capabilities, allowing quick access to and navigation of elements within your agent. [Learn more](https://learn.microsoft.com/en-us/microsoft-copilot-studio/authoring-search-within-agent)
- **Use managed agents as a starting point for Copilot creation** \[Web\]

  Managed agents in Microsoft Copilot Studio serve as a starting point, allowing makers to leverage industry best practices and design guidelines to ensure a consistent and professional agent experience. Managed agents can be discovered, created, and analyzed by template developers for use by agent makers in your organization. With managed agents, you can quickly set up an agent so you can spend more time customizing your agent's logic and functionality. This streamlined approach not only speeds up the development process but also helps organizations quickly adapt to changing business requirements and improve overall operational efficiency. [Learn more](https://learn.microsoft.com/en-us/microsoft-copilot-studio/authoring-install-agent)

### Microsoft 365 admin center

- **Admins can easily manage orphaned agents with comprehensive lifecycle functionality** \[Windows, Web\]

  Admins can effectively manage the lifecycle of ownerless agents. They can easily filter, identify, block, or delete agents that are no longer associated with an owner, ensuring a streamlined and efficient workflow.
- **Copilot Search management under Copilot controls** \[Web\]

  Enable administrators to configure, customize, and measure Copilot Search across their organization. This feature provides centralized tools to manage search connectors, tailor search experiences to organizational needs, and gain actionable insights into adoption, usage patterns, and content engagement. Designed to enhance productivity and maximize the value of Microsoft 365 Copilot, it supports both setup and ongoing optimization of enterprise search experiences. [Learn more](https://learn.microsoft.com/en-us/microsoft-365/copilot/microsoft-365-copilot-search-admin-experience)

### Microsoft 365 Copilot app

- **Configure format, style, and durations of an audio overview in Copilot Notebooks** \[Web\]

  Choose between a podcast-style format with dual voices or a single voice narration, and customize the style and duration. This gives you more control over how your Notebook is brought to life in audio form.  
  [Learn more](https://support.microsoft.com/topic/get-an-audio-overview-of-your-notebook-with-microsoft-365-copilot-notebooks-a22df989-b9cd-47fb-abac-e888d8f10cd9)
- **Copilot Search for Premium SKU commercial users** \[Android\]

  Copilot Search allows you to search across files, people, 1P and 3P content \(for example, Figma, ServiceNow tickets\). You get Copilot answers for Natural Language Search queries.
- **Direct access to Copilot Chat in Microsoft 365 app** \[Android, iOS\]

  Microsoft 365 Copilot mobile app is removing bottom tabs and will open directly on Chat for eligible users, making it simpler and easier to chat with Copilot.
- **Filter past conversations in Copilot Chat** \[Web\]

  We're introducing a chat history filtering capability that empowers users to tailor their view of past conversations. This feature enables users to scope their chat history to a more relevant, workflow-aligned view, helping them quickly surface the chats that matters most. This enhancement is designed to support better context recall.
- **Microsoft 365 Copilot Search** \[Android, Windows, iOS, Web\]

  Copilot Search is the intelligent search experience within the Microsoft 365 Copilot app, designed to deliver fast, secure, and context-aware results across your organization's data. It enables users to search across emails, files, chats, meetings, and even third-party platforms like Salesforce, Jira, and Confluence using natural language queries.  
  [Learn more](https://learn.microsoft.com/en-us/microsoft-365/copilot/microsoft-365-copilot-search)
- **Unified Conversations \(Chat History\) List** \[Web\]

  We've made it easier to find what you need. Users now see a single, streamlined list of all your conversations. No more switching between tabs or wondering where to look for specific conversations. Select a conversation and you'll pick up in the same context and mode as where you left off.

### OneNote

- **Create and use Copilot Notebooks in OneNote** \[Windows\]

  Bring together your notes, Word documents, Excel files, PowerPoint decks, Copilot chats and more into Copilot Notebooks in OneNote to organize and reason over your content. [Learn more](https://support.microsoft.com/topic/introducing-microsoft-365-copilot-notebooks-in-onenote-c91a851a-77d6-4b70-a898-8aaf718a95df)

### Outlook

- **Schedule meetings effortlessly from email threads** \[iOS\]

  Use Copilot to quickly schedule meetings by analyzing email threads, crafting invitations, and including attendees-all with ease. [Learn more](https://support.microsoft.com/office/create-a-meeting-and-agenda-with-copilot-in-outlook-31a44dfa-62bb-4751-82c4-14327a26759f)

### PowerPoint

- **Copilot Chat creates and enhances presentation content and design** \[Web\]

  Develop comprehensive presentations with depth in content, narrative, and structure, using Copilot's assistance for a polished and compelling delivery.  
  [Learn more](https://learn.microsoft.com/en-us/copilot/overview)

### Viva Insights

- **Unlock team skills insights with AI-powered reports**

  With Microsoft 365 Copilot in Viva Insights, leaders can unlock powerful skills insights for their teams-driven by People Skills data. Copilot enables leaders to explore their organization's skill distribution, identify individuals with specific capabilities, and generate dynamic visual reports to support strategic decision-making.

### Word

- **Fix spelling and grammar all at once with Copilot** \[Web\]

  Simplify your editing process with Copilot's one-click solution. Apply all grammar and spelling corrections instantly while retaining the option to review and undo changes you don't want to keep. [Learn more](https://techcommunity.microsoft.com/blog/Microsoft365InsiderBlog/fix-spelling-and-grammar-faster-with-microsoft-365-copilot-in-word-for-the-web/4450625)

## September 3, 2025

Updates released between August 19, 2025, and September 3, 2025.

### Copilot extensibility

- **Add advanced scripting support for ServiceNow catalog** \[Windows, Web\]

  Use advanced scripting for user permissions with the ServiceNow Catalog Graph Connector, allowing more customized and secure experiences.  
  [Learn more](https://learn.microsoft.com/en-us/microsoftsearch/servicenow-catalog-advanced-flow)
- **Create agents from Teams meeting transcripts**

  Turn meeting discussions into smart assistants by using Copilot extensibility to create agents directly from Teams transcripts and calendar information.  
  [Learn more](https://learn.microsoft.com/en-us/microsoft-365-copilot/extensibility/copilot-studio-agent-builder-knowledge)
- **Get clear sync statuses and error insights** \[Windows, Web\]

  View actionable user sync and ingestion statuses across all states in Microsoft admin center to simplify troubleshooting.  
  [Learn more](https://learn.microsoft.com/en-us/microsoftsearch/connector-view-details)
- **Ground Copilot responses on specific content subsets** \[Windows, Web\]

  Increase precision with Copilot extensibility by using subsets of data connections, ensuring responses are based on the most relevant information.  
  [Learn more](https://learn.microsoft.com/en-us/microsoft-365-copilot/extensibility/copilot-studio-agent-builder-knowledge?branch=main&branchFallbackFrom=pr-en-us-1060)
- **Integrate SharePoint files in Agent Builder for smarter agents**

  Enrich your agents with comprehensive knowledge by adding extensive SharePoint files into Copilot Studio's Agent Builder, enabling more intelligent and context-aware interactions.  
  [Learn more](https://learn.microsoft.com/en-us/microsoft-365-copilot/extensibility/copilot-studio-agent-builder-knowledge#scope-copilot-connector-data-sources)
- **Search and browse connector catalog with ease** \[Windows, Web\]

  Admins can now quickly find connectors across categories and functions in the Copilot extensibility catalog-making integrations simpler than ever.  
  [Learn more](https://learn.microsoft.com/en-us/microsoftsearch/connector-view-details)
- **Use enterprise data for smarter agents in Agent Builder**

  Enhance agent accuracy by integrating diverse enterprise data sources like ServiceNow tickets or Google Workspace files into Copilot's Agent Builder.  
  [Learn more](https://learn.microsoft.com/en-us/microsoft-365-copilot/extensibility/copilot-studio-agent-builder-knowledge#scope-copilot-connector-data-sources)

### Copilot Studio

- **Discover and install Copilot Studio agents from Dataverse** \[Web\]

  Easily find and install Microsoft-built agents in Copilot Studio using the integrated Power Platform catalog, reducing governance and setup complexities.  
  [Learn more](https://learn.microsoft.com/en-us/microsoft-copilot-studio/authoring-install-agent)

### Excel

- **Copilot-generated formula in one step** \[Windows\]

  Just tell Copilot what you need, and it creates the formula and places it directly into the selected cell-quick and easy.  
  [Learn more](https://support.microsoft.com/topic/generate-single-cell-formulas-with-copilot-in-excel-2d0201f3-0c3f-41b8-b0b0-07da3ad8fb29)
- **Copilot-generated single cell formula in one step** \[Windows\]

  Copilot can generate a complete formula based on your prompt and place it directly into the selected cell-quick and easy.  
  [Learn more](https://support.microsoft.com/topic/generate-single-cell-formulas-with-copilot-in-excel-2d0201f3-0c3f-41b8-b0b0-07da3ad8fb29)

### Microsoft 365 Copilot app

- **Enrich agents with Store integration on mobile** \[Android, iOS\]

  Access and enhance agents through the Agent Store on mobile, making it easier to deploy and manage new capabilities on the go.
- **Save an audio overview from Copilot Notebooks to OneDrive** \[Web\]

  Save the audio overview that you have generated within a Copilot Notebook to OneDrive so you can download or share with others.  
  [Learn more](https://support.microsoft.com/topic/get-an-audio-overview-of-your-notebook-with-microsoft-365-copilot-notebooks-a22df989-b9cd-47fb-abac-e888d8f10cd9?preview=true)
- **Use Copilot in PDFs on mobile** \[Android, iOS\]

  Eligible users can now leverage Copilot within PDF files in the Microsoft 365 mobile app. Easily ask questions, gather summaries, and extract key insights from your PDFs for more efficient content understanding on the go.

### Microsoft 365 Copilot Chat

- **Graph Connectors in CIQ** \[Web\]

  Ground your Copilot prompts in CIQ using data from your organization's Graph Connectors, so responses reflect your third-party content and deliver richer, more relevant insights.  
  [Learn more.](https://support.microsoft.com/topic/using-context-iq-to-refer-to-specific-files-people-and-more-in-microsoft-365-copilot-and-copilot-chat-272ac2c1-c5f7-49c9-8a42-2a8a87846fa0)
- **Ground prompts with SharePoint Sites** \[Web\]

  Users can scope their prompts in Copilot Chat by searching and selecting relevant SharePoint Sites, allowing more focused and relevant discussions.
- **Personalize interactions with Copilot Memory** \[Android, iOS, Web\]

  Copilot Memory leverages insights inferred from conversations between the user and Copilot, along with data from the Microsoft Graph and custom instructions to provide personalized help for tasks. Users have full control and can view, manage, disable or clear memory at any time.  
  [Learn more.](https://techcommunity.microsoft.com/blog/microsoft365copilotblog/introducing-copilot-memory-a-more-productive-and-personalized-ai-for-the-way-you/4432059)
- **Use Copilot Chat to enhance Find on Page** \[Web\]

  Quickly locate the right information by combining CTRL+F with Copilot Chat for smarter, context-aware search in Microsoft Edge for Business.  
  [Learn more.](https://support.microsoft.com/topic/using-microsoft-copilot-in-edge-at-work-012b3674-bab8-4f99-8585-c961dac68642)
- **Utilize SharePoint and OneDrive folders in prompts** \[Web\]

  Users can now incorporate SharePoint and OneDrive folders into their Copilot Chat prompts via the "Attach cloud files" feature, refining content scoping capabilities.
- **View web queries used by Copilot for greater transparency** \[Web, Windows\]

  See the exact web queries Copilot sends in response to your prompts, along with the list of websites queried, enhancing your awareness and control over the information process.

### Microsoft Loop

- **Turn Copilot Pages into Word documents** \[Web\]

  Move research and content collected in Copilot Pages into Word with one click, simplifying sharing and finalizing documents.

### Microsoft Purview compliance portal

- **Data Loss Prevention to restrict Microsoft 365 Copilot processing on content with sensitivity labels** \[Web\]

  This feature allows DLP policies to provide detection of sensitivity labels in enterprise grounding data and restrict access of the content in Microsoft 365 Copilot. [Learn more.](https://learn.microsoft.com/en-us/purview/dlp-microsoft365-copilot-location-learn-about)
- **Ask Copilot questions on Teams meeting recordings** \[Web\]

  Select a Teams meeting recording in your OneDrive commercial account and ask Copilot to recap the meeting, highlight parts where you were mentioned, or recommend action items and next steps. This feature requires a Microsoft Copilot for Microsoft 365 license and will be available to commercial customers on OneDrive Web. This feature works only on Teams meeting recordings with a transcript.  
  [Learn more.](https://support.microsoft.com/office/get-started-with-copilot-in-onedrive-7fc81e10-e0cf-4da8-af2e-9876a2770e5d)
- **Catch up with hands-free audio overviews of your files** \[Web\]

  Effortlessly stay informed using Copilot to generate audio overviews for key documents, prepping for meetings, or catching up on updates. Providing a quick, engaging way to absorb file content-hands-free. [Learn more.](https://support.microsoft.com/topic/get-an-audio-overview-of-your-notebook-with-microsoft-365-copilot-notebooks-a22df989-b9cd-47fb-abac-e888d8f10cd9)

### Outlook

- **Copilot Chat Sidebar in Classic Outlook for Windows** \[Windows\]

  A new sidebar for Copilot Chat is available in classic Outlook for Windows, letting you chat with Copilot in the context of the content you're reading or writing. [Learn more.](https://learn.microsoft.com/en-us/copilot/manage)

### PowerPoint

- **Excel data when building a presentation** \[Web, Mac, Windows\]

  You can now reference an Excel file when you create a presentation with Copilot within the PowerPoint application. [Learn more.](https://support.microsoft.com/office/create-a-new-presentation-with-copilot-in-powerpoint-3222ee03-f5a4-4d27-8642-9c387ab4854d)

### Teams

- **Export Copilot interactions with new APIs**

  Use Graph APIs to securely export Copilot prompts and responses for compliance and security applications, ensuring full visibility of AI activity. [Learn more.](https://learn.microsoft.com/en-us/microsoft-365-copilot/extensibility/api/ai-services/interaction-export/aiinteractionhistory-getallenterpriseinteractions?pivots=graph-v1)

### Viva Glint

- **Enable Copilot for Company Admin role in Viva Glint** \[Web\]

  Viva Glint admins can now turn on Copilot for Company Admins without creating custom roles-simplifying Copilot access while maintaining permissions safeguards. [Learn more.](https://learn.microsoft.com/en-us/viva/glint/copilot/admin-enable#enable-copilot-for-company-admins)

### Word

- **Preserve formatting when drafting from selected text** \[Web\]

  When Copilot generates drafts based on a selection of text, Copilot retains the formatting of the selected text and allows users to apply new formatting, like bold, underline, italic, and more.

## August 19, 2025

Updates released between August 5, 2025, and August 19, 2025.

### Copilot extensibility

- **Build and deploy bots with Microsoft 365 Agents Toolkit**

  Developers can create, test, and update AI-driven bots using Microsoft 365 Agents Toolkit, making them compatible to run natively in Teams.
- **Craft actions using API chaining with low code** \[Windows, Web\]

  Makers can leverage low code and pro-code options to create actions with API chaining, enabling bulk actions and adaptive card contexts for streamlined processes.  
  [Learn more.](https://learn.microsoft.com/en-us/microsoft-365-copilot/extensibility/instructions-api-plugins)
- **Create simplified multi-step workflows** \[Windows, Web\]

  Streamline your tasks with an embedded builder that allows users to design and manage multi-step workflows effortlessly, enhancing productivity.  
  [Learn more.](https://learn.microsoft.com/en-us/microsoft-365-copilot/extensibility/declarative-agent-instructions)
- **Customize Copilot with Declarative Agents** \[Windows\]

  End-users can now tailor Copilot's capabilities with Declarative Agents, adding new knowledge and skills for enhanced functionality.  
  [Learn more.](https://learn.microsoft.com/en-us/microsoft-365-copilot/extensibility/overview-declarative-agent)
- **Develop custom agents for Copilot and Teams**

  Create, test, and update custom engine agents using Microsoft 365 Agents Toolkit and Microsoft Copilot Studio for seamless integration with Microsoft 365 Copilot and Teams.
- **Discover custom extensions for Copilot** \[Windows, Web\]

  Find and deploy customizable extensions \(CEAs\) for Copilot directly from the Store, enhancing the capabilities of your workflow with ease.
- **Enable pro-code support in Microsoft 365 Copilot Chat**

  Leverage both synchronous and asynchronous pro-code CEA support in Microsoft 365 Copilot Chat, expanding the capabilities for advanced user interactions and integrations.
- **Enhance agent grounding with context IQ**

  Utilize context IQ in Microsoft 365 Copilot Chat to select the ideal graph connector grounding information for agents, ensuring precise and relevant responses.  
  [Learn more.](https://support.microsoft.com/topic/using-context-iq-to-refer-to-specific-files-people-and-more-in-microsoft-365-copilot-272ac2c1-c5f7-49c9-8a42-2a8a87846fa0#:%7E:text=Context%20IQ%20%28CIQ%29%20is%20an%20AI-powered%20feature%20in,by%20making%20information%2C%20people%2C%20and%20conversations%20more%20accessible.)
- **Gain insight into conversation analysis**

  Users now see how utterances are transformed into keywords and items for grounding, enhancing transparency and understanding of Copilot interactions.
- **Integrate declarative agents into Excel** \[Windows, Web\]

  Users can now seamlessly integrate and leverage declarative Copilot agents directly within Excel, enhancing data interaction and task automation.  
  [Learn more.](https://learn.microsoft.com/en-us/microsoft-365-copilot/extensibility/overview-declarative-agent)
- **Publish agents for IT approval**

  Use Microsoft 365 Agents Toolkit and Copilot Studio to publish custom engine agents for IT review, approval, and deployment in your organization's tenant.
- **Regulate knowledge source with governance tools** \[Windows, Web\]

  Admins can now oversee and manage agents with uploaded files as their knowledge source, utilizing tools for agent filtering, reviewing sensitivity labels, and managing metadata.
- **See authors and descriptions in every agent interaction** \[Windows, Web\]

  Build trust and transparency by viewing the author name and agent description in each interaction, enhancing user confidence in responses.
- **Submit custom agents for validation**

  Developers can use Microsoft 365 Agents Toolkit to submit custom engine agents for Microsoft validation, facilitating their publication in the Agents store.

### Copilot Studio

- **Build a custom agent with natural language** \[Web\]

  Describe the agent you want, and Copilot Studio instantly proposes its name, purpose, instructions and starter prompts-so you can begin testing in minutes instead of hours.  
  [Learn more.](https://learn.microsoft.com/en-us/microsoft-copilot-studio/fundamentals-get-started)
- **Perform custom search as a topic action** \[Web\]

  Enhance your precision with Custom Search, allowing you to query knowledge sources and extract raw data effortlessly. This feature empowers you to create more transparent Copilot experiences by running searches on selected sources and saving data outputs for flexible use.  
  [Learn more.](https://learn.microsoft.com/en-us/microsoft-copilot-studio/authoring-create-custom-search)
- **See security-related views and statuses for agents within Copilot Studio** \[Web\]

  Enhanced security in Copilot Studio with visual indicators for agent protection, blocked prompts, and authentication guidelines. Makers can see how and when Microsoft has protected their agents, assessed their agents' status, and determine if any action is needed.  
  [Learn more.](https://learn.microsoft.com/en-us/microsoft-copilot-studio/security-agent-runtime-view)
- **Use managed agents as a starting point for Copilot creation** \[Web\]

  Explore and install managed agents in Copilot Studio to kickstart your projects with ready-to-use solutions featuring built-in service connections and autonomous capabilities. Streamline your workflow and enhance productivity without starting from scratch.

### Microsoft 365 admin center

- **Manage Copilot costs with budget limits** \[Web\]

  Define budget policies for Copilot services, set thresholds and alerts, and receive email notifications for proactive cost control.  
  [Learn more.](https://learn.microsoft.com/en-us/microsoft-365/copilot/pay-as-you-go/setup)

### Microsoft 365 Copilot app

- **Expanded language options with Microsoft 365 Copilot** \[Android, Windows, iOS, Mac, Web\]

  Microsoft 365 Copilot now supports six additional languages: Albanian, Filipino, Icelandic, Malay, Maltese, and Serbian \(Cyrillic\). [Learn more.](https://support.microsoft.com/office/supported-languages-for-microsoft-365-copilot-94518d61-644b-4118-9492-617eea4801d8)

### Microsoft 365 Copilot Chat

- **Advanced data analysis in Copilot Chat mobile apps** \[Android, iOS\]

  Solve complex tasks by generating and executing Python code with the advanced reasoning model in Copilot Chat mobile apps.
- **Copilot Chat available for EDU users ages 13 and older** \[Web\]

  Microsoft 365 Copilot Chat is now accessible for EDU users aged 13+, offering secure AI chat with the latest language models. Admins need to enable access for eligible users. [Learn more.](https://techcommunity.microsoft.com/blog/educationblog/microsoft-365-copilot-chat-for-students-13/4440370)
- **Edge contextual capabilities in Copilot Chat work mode** \[Web\]

  In Copilot Chat work mode, ask Copilot questions about web pages and PDFs opened in Edge-using page context to summarize or analyze content, and enhancing your research on the fly. [Learn more.](https://learn.microsoft.com/en-us/deployedge/edge-learnmore-copilot-page-summary-results)
- **Expanded file search capabilities in Copilot Chat** \[Windows, Web\]

  Copilot Chat now supports a wider range of file types in SharePoint and OneDrive, enhancing search and information retrieval. [Learn more.](https://support.microsoft.com/topic/file-formats-supported-by-microsoft-365-copilot-1afb9a70-2232-4753-85c2-602c422af3a8)
- **GPT-5 now available in Copilot Chat**

  Unlock advanced reasoning in Copilot Chat with GPT-5, offering dynamic model switching to address both simple and complex queries. Seamlessly obtain fast answers or dive deep into data analysis for tasks like summarizing RFPs or evaluating detailed proposals. Empower your productivity with intelligent, context-aware solutions tailored to your needs. [Learn more.](https://www.microsoft.com/microsoft-365/blog/2025/08/07/available-today-gpt-5-in-microsoft-365-copilot/)

### Microsoft Purview compliance portal

- **Monitor Microsoft 365 Copilot's security posture** \[Web\]

  A dedicated page in Data Security Posture Management for AI showcases Microsoft 365 Copilot's protection capabilities and usage metrics for improved oversight. [Learn more.](https://learn.microsoft.com/en-us/purview/dspm-for-ai-considerations)
- **New graph for departments** \[Web\]

  A newly added graph in Data Security Posture Management for AI shows AI interactions grouped by department. [Learn more.](https://learn.microsoft.com/en-us/purview/dspm-for-ai-considerations)
- **Web search query filtering in Data Security Posture Management for AI** \[Web\]

  Filter AI interactions for events that contain a web search query and view the content of the search within Microsoft Purview Data Security Posture Management for AI. [Learn more.](https://learn.microsoft.com/en-us/purview/dspm-for-ai-considerations)

### OneDrive

- **Sharing with Copilot summary now supports more file types** \[Web\]

  Enhance your collaboration workflow by using Copilot to generate summaries for PowerPoint, Excel, PDFs, images, and protected files directly within OneDrive Web and SharePoint document libraries. Get instant overviews while maintaining sensitivity labels on confidential files, ensuring secure and efficient sharing.

### Outlook

- **Summarize email attachments with Copilot** \[Android, Windows, iOS, Mac, Web\]

  Summarize PDF, Word, and PPT email attachments effortlessly in Outlook Web and the new Outlook for Windows, making it easier to extract key information without needing to open each file. [Learn more.](https://support.microsoft.com/office/summarize-an-email-thread-with-copilot-in-outlook-a79873f2-396b-46dc-b852-7fe5947ab640#id0ebbj=new_outlook)

### SharePoint

- **Microsoft 365/SharePoint Agent Insights for SharePoint Administrators** \[Web\]

  Provides comprehensive insights into newly created SharePoint agents with content governance actions within SharePoint Advanced Management controls. [Learn more.](https://learn.microsoft.com/en-us/sharepoint/insights-on-sharepoint-agents)

### Viva Insights

- **Bridge skill gaps with personalized insights** \[Windows, Web\]

  Discover and promote upskilling opportunities with People Skills. Share skills, connect with others, and enrich user experiences across Microsoft 365, including apps such as Copilot and Viva Learning. [Learn more.](https://learn.microsoft.com/en-us/microsoft-365/copilot/people-skills-overview)
- **Unified analytics for enhanced insights** \[Web\]

  Experience a streamlined approach with Copilot Dashboard and Viva Insights. This unified platform blends advanced analytics offerings, providing leaders, delegates, and analysts with cohesive, actionable insights. [Learn more.](https://learn.microsoft.com/en-us/viva/insights/introduction#viva-insights-web-app)

### Word

- **Select some text and explore actions with the Copilot icon in your margin.** \[Web\]

  Rewrite, get writing suggestions, and more with just one click.

## August 5, 2025

Updates released between July 22, 2025, and August 5, 2025.

### Copilot extensibility

- **Admin pre-approval for trusted declarative agents** \[Web\]

  Admins can now pre-approve specific agents so their actions are always allowed without extra confirmation. This reduces interruptions and helps ensure a smooth workflow in integrated apps.  
  [Learn more.](https://learn.microsoft.com/en-us/microsoft-365/admin/manage/manage-copilot-agents-integrated-apps)
- **Discover and install Copilot agents easily**

  Users in Word and PowerPoint can seamlessly find and install Copilot agents directly from the Unified App Store.  
  [Learn more.](https://learn.microsoft.com/en-us/microsoft-365/copilot/copilot-agent-install)
- **Enhance agent builder with full screen mode** \[Windows, Mac, Web\]

  Enjoy an improved agent builder with a full-screen view that streamlines the process of creating and managing your agents.  
  [Learn more.](https://learn.microsoft.com/en-us/microsoft-365-copilot/extensibility/copilot-studio-agent-builder-build)
- **Enhanced adaptive card capabilities in declarative agents**

  Developers now have access to enhanced adaptive card functionalities-including task modules, stage view, inline actions, and charts-directly in declarative agents for richer app experiences.  
  [Learn more.](https://learn.microsoft.com/en-us/training/modules/copilot-declarative-agent-action-api-plugin-adaptive-cards-vsc/)
- **Enhanced Q&A accuracy for SharePoint files** \[Windows, Web\]

  Improve the precision of Q&A interactions on SharePoint files that include tables, comments, and formatting. Benefit from more relevant and insightful responses whether you're working with Word, PDF, or PowerPoint files.
- **Fine-tune models with tenant data**

  Developers and makers can fine-tune a model used in Microsoft 365 Copilot using their tenant data.  
  [Learn more.](https://learn.microsoft.com/en-us/microsoft-365/copilot/copilot-tuning-overview)
- **Get relevant calendar results by time period** \[Windows, Web\]

  Quickly summarize meetings for a specific day to stay on top of your schedule and focus on the events that matter most.
- **Improve email responses with extra context** \[Windows, Web\]

  Get fuller email replies that expand your initial lists, indicate the number of related messages, and let you easily paginate for more details-all to help you manage your inbox more effectively.  
  [Learn more.](https://support.microsoft.com/topic/schedule-copilot-prompts-29dfd5fb-211a-4515-88a6-730b8074e489)
- **Schedule meetings with smart time insights** \[Windows, Web\]

  Easily discover optimal meeting times and streamline Outlook handoffs with intelligent calendar suggestions that make scheduling a breeze.  
  [Learn more.](https://support.microsoft.com/office/how-do-i-use-the-the-scheduling-assistant-to-find-meeting-times-bdd6c165-4186-45f1-ad9e-5af067ac69a3)
- **Semantically index more document pages**

  With improved indexing, P99 documents can now include up to 180,000 characters \(about 90-100 pages\) for more comprehensive document insights, while P99.99 documents support up to 1.8 million characters \(about 900-1,000 pages\), which is a significant increase from the previous 18-20 page limit.  
  [Learn more.](https://learn.microsoft.com/en-us/microsoftsearch/semantic-index-for-copilot)

### Copilot Studio

- **Ground your agents with live enterprise data** \[Web\]

  You can now enhance your copilots built with Microsoft Copilot Studio by incorporating structured data from both Microsoft and select non-Microsoft systems. These copilots enable users to ask natural language questions about enterprise systems within their Power Platform tenants. Building on the natural language query capabilities introduced with Microsoft Dataverse knowledge, Microsoft is extending this functionality to include certain third-party services.  
  [Learn more.](https://learn.microsoft.com/en-us/microsoft-copilot-studio/knowledge-real-time-connectors)
- **Only use grounded knowledge for agent response** \[Windows, Web\]

  Prevent agents from using model-trained knowledge by turning off internal knowledge, ensuring responses are based on specified grounded sources.  
  [Learn more.](https://learn.microsoft.com/en-us/microsoft-365-copilot/extensibility/copilot-studio-agent-builder-knowledge#prioritize-your-knowledge-sources-over-general-knowledge)

### Microsoft 365 admin center

- **Onboard SharePoint Agents as a pay-as-you-go scenario in CCS** \[Web\]

  This feature introduces SharePoint Agents to the Pay-as-you-go tab under Copilot → Billing & usage, aligning with the existing workflow used for Microsoft 365 Copilot Chat. Administrators gain the ability to manage and monitor SharePoint Agent consumption through the familiar Pay-as-you-go interface, ensuring consistent oversight across Copilot experiences. Integration with the SharePoint backend via API enables precise usage tracking and billing for this new scenario.  
  [Learn more.](https://learn.microsoft.com/en-us/microsoft-365/commerce/services/pay-as-you-go-services)

### Microsoft 365 Copilot app

- **Ask Microsoft 365 Copilot for insights using Click to Do** \[Windows\]

  Streamline your workflow by seamlessly sharing highlighted content with Microsoft 365 Copilot using Click to Do for quick insights and assistance.  
  [Learn more.](https://learn.microsoft.com/en-us/windows/client-management/manage-click-to-do)
- **Start an instant chat with Copilot** \[Windows\]

  Launch a chat with Copilot quickly using the quick view for instant assistance. Use the Win+C shortcut or the Copilot key on supported devices.

### Microsoft 365 Copilot Chat

- **Share agents with your enterprise** \[Windows, Web\]

  Generate sharing links for your agents in Business Chat. If the recipient doesn't have the agent, they are directed to the Microsoft 365 application catalog to install it. If they do, the agent opens directly in Microsoft 365 Copilot Business Chat.  
  [Learn more.](https://support.microsoft.com/topic/how-to-share-your-agent-44981c08-ab64-43f1-bcf8-ebadfc5469cc)

### Microsoft Intune

- **Analyze error codes efficiently**

  Use Copilot to analyze Intune error codes from device configuration profiles, compliance policies, and app installations, simplifying troubleshooting. [Learn more.](https://learn.microsoft.com/en-us/intune/intune-service/copilot/copilot-devices)
- **Compare device settings to uncover issues**

  Easily compare settings on two devices using Copilot in Intune to identify potential misconfigurations.  
  [Learn more.](https://learn.microsoft.com/en-us/intune/intune-service/copilot/copilot-devices)
- **Get device summaries with Copilot**

  Access device-specific information such as installed apps and group membership using Copilot in Intune for better device management.  
  [Learn more.](https://learn.microsoft.com/en-us/intune/intune-service/copilot/copilot-devices)

### PowerPoint

- **Copilot uses enterprise assets hosted on SharePoint OAL when creating presentations now** \[Mac, Windows, Web\]

  Once you integrate your organization's assets into a Sharepoint OAL \(Organization Asset Library\) you will be able to create presentations with your organization's image. [Learn more.](https://learn.microsoft.com/en-us/sharepoint/connect-organizational-asset-libraries-to-copilot)
- **Copilot uses Enterprise assets hosted on Templafy when creating presentations now** \[Mac, Windows, Web\]

  Once you connect your asset library hosted with Templafy to Microsoft365 and Copilot, you will be able to create presentations with your organization's images. [Learn more.](https://learn.microsoft.com/en-us/sharepoint/connect-organizational-asset-libraries-to-copilot)

### SharePoint

- **Manage site ownership effectively** \[Web\]

  The site ownership policy enables you to define and enforce ownership criteria for your SharePoint sites, automating actions to prevent data risks if sites remain ownerless for over three months. [Learn more.](https://learn.microsoft.com/en-us/sharepoint/create-sharepoint-site-ownership-policy)

### Teams

- **Ability to Stop Copilot while it is generating a response** \[Windows\]

  Copilot in Teams now has a 'stop' button after sending a prompt. This allows the user to stop Copilot's response either before the response has started to generate, or even after the response is generating. The user can then start a new prompt if they wish.
- **Interpreter agent for seamless communication** \[Windows, Mac\]

  Interpreter Agent acts like an instant translator during your Teams meetings. It listens to the spoken language in a meeting and immediately translates it into another language in real-time. This allows participants who speak different languages to understand each other and collaborate more effectively without waiting. Whether you're holding a business meeting, customer calls, or project discussions, the AI interpreter in Teams ensures everyone can participate fully, enhancing communication and productivity across diverse teams. It supports 9 different languages: English, Italian, German, French, Portuguese \(Brazil\), Japanese, Spanish, Chinese \(Mandarin\), and Korean. [Learn more.](https://support.microsoft.com/office/interpreter-in-microsoft-teams-meetings-c7efe2bb-535d-42ab-a5c4-d2d91619b46d)
- **Translated Intelligent meeting recap for multilingual meetings \(Copilot and Teams Premium\)** \[Windows, Mac\]

  Now, intelligent meeting recap supports multilingual meetings, ensuring you can easily catch up on key discussions even when multiple languages were spoken. After the meeting, your recap is automatically generated in the translation language you selected for live transcription and captions. [Learn more.](https://support.microsoft.com/office/recap-in-microsoft-teams-c2e3a0fe-504f-4b2c-bf85-504938f110ef)

### Word

- **Access audio overviews in Word** \[Web\]

  Generate a convenient audio overview of your document through Copilot from the Summary tab, enhancing your document review process.  
  [Learn more.](https://support.microsoft.com/topic/listen-to-an-audio-overview-of-your-document-9b2fad37-021e-4e89-b33b-323e850f9ae0)
- **Kickstart your document with contextual prompts** \[Windows\]

  Copilot suggests prompts by including files and meetings based on your recent activity, helping you draft a new document in Word seamlessly.
- **Use Writing suggestions to review content in Word** \[Mac\]

  Enhance your document content with AI-generated writing suggestion in the Copilot context menu. Get suggestions on logical structure, flow, and tone to make your documents more impactful. [Learn more.](https://support.microsoft.com/topic/use-writing-suggestions-to-review-content-in-word-fa09c055-d623-4d20-954f-9b064a5a7c80)

## July 22, 2025

Updates released between July 8, 2025, and July 22, 2025.

### Copilot extensibility

- **Hebrew support in Agent builder** \[Windows, Web\]

  Integrate Hebrew language support in agent builder to build accessible, localized solutions that simplify multilingual deployments and enhance user engagement.  
  [Learn more.](https://learn.microsoft.com/en-us/microsoft-365-copilot/extensibility/copilot-studio-agent-builder-availability)
- **Increased support for uploading up to 20 documents to agents' knowledge** \[Windows, Web\]

  End users and makers can now upload up to 20 documents to ground agents with richer, embedded knowledge in Microsoft Copilot agent builder.  
  [Learn more.](https://learn.microsoft.com/en-us/microsoft-365-copilot/extensibility/copilot-studio-agent-builder-knowledge)
- **Share agents from embedded builder** \[Windows, Web\]

  Users can share agents from an embedded agent builder to other individual users or group chats.  
  [Learn more.](https://learn.microsoft.com/en-us/microsoft-365/admin/manage/manage-embedded-knowledge-agents?)
- **Share agents with context-aware link previews** \[Windows, Web\]

  Streamline your interactions by using context-aware buttons that adapt based on where links are shared-making it easier to take the right action in chats and meetings.
- **Upload and embed knowledge in declarative agents** \[Windows, Web\]

  Empower your agents with enriched context by uploading your own files and embedding crucial knowledge for personalized, day-to-day assistance.  
  [Learn more.](https://learn.microsoft.com/en-us/microsoft-copilot-studio/knowledge-add-file-upload)
- **Users can share agents from SharePoint** \[Web\]

  Users can share agents via links from SharePoint to Teams group chats. This means users will be able to chat and collaborate with SharePoint agents in group chats. The shared links will unfurl into preview cards with actionable buttons to 'Add to this chat'.  
  [Learn more.](https://learn.microsoft.com/en-us/sharepoint/get-started-sharepoint-agents)

### Copilot Studio

- **Easily find and use knowledge data sources** \[Web\]

  In Copilot Studio agent builder you can now quickly identify and select the right knowledge data sources without manually scanning long lists. This streamlined workflow helps you get to the insights you need faster for everyday tasks.  
  [Learn more.](https://learn.microsoft.com/en-us/power-platform/release-plan/2025wave1/microsoft-copilot-studio/use-teams-chats-as-knowledge-sources)

### Excel

- **Ask Copilot to generate formulas** \[Web\]

  Type "=" anywhere on your grid or in the formula bar and let Copilot generate formulas from natural language, making complex calculations simpler and faster.  
  [Learn more.](https://support.microsoft.com/office/generate-formulas-with-copilot-in-excel-d866d926-9791-4e5f-be2a-c6dd9e587a47)
- **Copilot advanced text analysis in Excel** \[Web\]

  Copilot can now analyze text by identifying themes and sentiments, citing data examples, and inserting a column with labels-helping you quickly uncover actionable insights.  
  [Learn more.](https://support.microsoft.com/topic/text-insights-in-excel-cecc7821-39c1-4e12-8bd6-4d4348370585)
- **Copilot icon on the grid in Excel for the web for M365 personal and family** \[Web\]

  Access AI-powered support directly from your spreadsheet with a single click. The Copilot icon helps you stay in your flow by offering instant insights while you work.  
  [Learn more.](https://techcommunity.microsoft.com/blog/excelblog/how-to-get-started-with-copilot/4383870)

### Microsoft 365 Copilot app

- **Get an audio overview of a notebook** \[Web\]

  Turn the files in your notebook into a dynamic audio overview for an engaging listening experience. Simply select "Get audio overview" at the top of your notebook-available in English only, with more languages coming soon.  
  [Learn more.](https://support.microsoft.com/topic/get-an-audio-overview-of-your-notebook-with-microsoft-365-copilot-notebooks-a22df989-b9cd-47fb-abac-e888d8f10cd9)

### Microsoft 365 Copilot Chat

- **Dictate your prompts in Copilot Chat** \[Windows, Web\]

  You can now use the dictation button to input your prompts via speech, making interactions with Copilot more natural and efficient.  
  [Learn more.](https://www.microsoft.com/microsoft-365/roadmap?filters=&searchterms=475968)
- **[Researcher](https://go.microsoft.com/fwlink/?linkid=2329838) available in GA** \[Windows, Mac, Web\]

  The [Researcher](https://go.microsoft.com/fwlink/?linkid=2329838) agent is pre-installed in Copilot Chat for all worldwide users. Find it in the left navigation pane alongside other agents, giving you quick access to research tools as part of the Copilot Premium license.  
  [Learn more.](https://www.microsoft.com/microsoft-365/blog/2025/06/02/researcher-and-analyst-are-now-generally-available-in-microsoft-365-copilot/?msockid=2484525e9a9b66d4330b47329bb667c9)

### Microsoft 365 Purview compliance portal

- **Data Security Posture Management for AI - Data Risk Assessments.** \[Web\]

  Admins can drive better security outcomes by reviewing default assessments, examining data sensitivity, and monitoring user accesses-all to quickly identify risks and remediate them in daily operations.  
  [Learn more.](https://learn.microsoft.com/en-us/purview/dspm-for-ai)

### PowerPoint

- **Create a presentation with Microsoft 365 Copilot from menus** \[Windows\]

  You can quickly begin a new presentation using Microsoft 365 Copilot from the PowerPoint start menu or file menu. Copilot is easily accessible when you open PowerPoint or click the File tab, helping to simplify your workflow.  
  [Learn more.](https://support.microsoft.com/office/create-a-new-presentation-with-copilot-in-powerpoint-3222ee03-f5a4-4d27-8642-9c387ab4854d)
- **Microsoft 365 Copilot generates the new presentation in a new file when starting from an existing presentation** \[Mac, Windows\]

  Now, when creating a presentation using Microsoft 365 Copilot from an existing presentation using, it creates the new presentation in a new file without affecting the original presentation.  
  [Learn more.](https://support.microsoft.com/office/create-a-new-presentation-with-copilot-in-powerpoint-3222ee03-f5a4-4d27-8642-9c387ab4854d)
- **Reference multiple files in your presentation creation using Microsoft 365 Copilot** \[Windows, Mac, Web\]

  Enhance your PowerPoint presentations by referencing up to five files with Microsoft 365 Copilot, making it easier to incorporate detailed insights and comprehensive data without switching contexts.  
  [Learn more.](https://support.microsoft.com/office/create-a-new-presentation-with-copilot-in-powerpoint-3222ee03-f5a4-4d27-8642-9c387ab4854d)

### Teams

- **Catch up on meetings with AI recaps on mobile**

  On iOS and Android, view AI-generated notes, tasks, @mentions, and speaker-indexed recordings so you can quickly get up to speed when you miss a meeting.  
  [Learn more.](https://learn.microsoft.com/en-us/microsoftteams/intelligent-recap-calls-meetings)

### Word

- **Catch up on a summary of document comments in the top of your document** \[Web\]

  Copilot now has a Discussion tab in the top of your document to summarize open comments, helping you quickly understand what people have said.
- **Easily write a prompt or choose quick actions from the Copilot icon in your Word doc** \[Mac, Windows\]

  The Copilot icon in your document margin makes it easy to quickly add a prompt or choose from a range of quick options Copilot can offer. [Learn more.](https://www.microsoft.com/microsoft-365-life-hacks/everyday-ai/how-to-use-copilot-in-microsoft-word?msockid=2484525e9a9b66d4330b47329bb667c9)
- **Include citations in drafted content** \[Web\]

  Enhance the credibility and reliability of your documents with Copilot's ability to automatically include citations when drafting content from referenced sources. This feature ensures proper attribution and helps maintain academic and professional standards in your work.
- **Listen to an audio summary of your document** \[Web\]

  Transform your Word document into a dynamic audio experience with Copilot. Enjoy a podcast-style discussion that makes your content easy to consume on the go. Currently available in English, this feature allows you to listen to your documents anytime, anywhere.  
  [Learn more.](https://support.microsoft.com/topic/listen-to-an-audio-overview-of-your-document-9b2fad37-021e-4e89-b33b-323e850f9ae0)
- **Preserve text formatting in drafted content** \[Windows\]

  Word Copilot now preserves the styling of surrounding content when generating text, ensuring a seamless and professional authoring experience. Copilot now understands and respects more contextual formatting-whether the user is writing in a list, table, heading, or styled paragraph. This includes support for bold, italic, underline, and links. This allows the generated text to better match the structure and basic formatting of the document. The result is a smoother authoring experience with less need for manual reformatting.
- **Reference very large documents when prompting Copilot** \[Web\]

  Easily work with extensive documents by typing a forward slash \(/\) or selecting the attach icon to choose a document up to 3,000 pages long. This becomes the basis of the content you're requesting from Copilot, making it seamless to generate content from detailed sources. [Learn more.](https://support.microsoft.com/topic/keep-it-short-and-sweet-a-guide-on-the-length-of-documents-that-you-provide-to-copilot-66de2ffd-deb2-4f0c-8984-098316104389)

## July 8, 2025

Updates released between June 24, 2025, and July 8, 2025.

### Copilot extensibility

- **Ability to use the Graph connector selector when using Teams Toolkit**

  Developers using Teams Toolkit to author declarative agents can select specific Graph connectors to improve their knowledge grounding. [Learn more](https://github.com/OfficeDev/microsoft-365-agents-toolkit/blob/dev/packages/vscode-extension/CHANGELOG.md#new-features)
- **Add Dataverse as knowledge in Copilot** \[Web, Windows\]

  Users can now include Dataverse as a knowledge source in Copilot, enabling more comprehensive responses and insights. [Learn more](https://learn.microsoft.com/en-us/microsoft-365-copilot/extensibility/build-declarative-agents?tabs=ttk&tutorial-step=1).
- **Audit and eDiscovery for Copilot actions and declarative agents** \[Windows, Web\]

  View detailed audit logs and eDiscovery records for Copilot actions and declarative agents in Microsoft Purview to simplify compliance and investigation workflows. [Learn more](https://learn.microsoft.com/en-us/purview/audit-copilot).
- **Automatic project scaffolding in Teams Toolkit for building Graph connectors**

  Developers can now leverage an automatic project scaffolding for Graph connector applications within the Teams Toolkit, allowing for the generation of a full production-ready Graph connector application from just an API description file, significantly reducing setup time and complexity. [Learn more](https://learn.microsoft.com/en-us/microsoft-365-copilot/extensibility/build-your-first-connector).
- **Deploy Copilot agents for easy discovery** \[Windows, Web\]

  Deploy Copilot agents in the store for user discovery directly from your apps. Users can get new agents, open the store, install, and use them seamlessly within App Chat. [Learn more](https://learn.microsoft.com/en-us/microsoft-365/admin/manage/manage-copilot-agents-integrated-apps?).
- **Developers can use TypeSpec as an authoring experience**

  Developers can use TypeSpec as an authoring experience for declarative agents and API plugins in Teams Toolkit. [Learn more](https://learn.microsoft.com/en-us/microsoft-365-copilot/extensibility/build-declarative-agents-typespec).
- **Discover, acquire, and manage agents through in-app store in Word and PowerPoint** \[Windows, Web\]

  With Copilot extensibility, users can discover, acquire, and manage agents through the unified store. We are excited to introduce the Microsoft 365 unified store to Office documents, enabling users to discover, acquire, and manage agents directly within the in-app store for Word and PowerPoint, with Excel support coming soon. [Learn more](https://devblogs.microsoft.com/microsoft365dev/office-addins-at-build-2025/#modernized-store-for-office-add-ins-and-copilot-agents).
- **Ground agents in Outlook email**

  Makers can now build custom agents that read and reason over Outlook messages, delivering answers that reflect the latest decisions and context stored in your inbox-no data migration or retraining needed. [Learn more](https://learn.microsoft.com/en-us/microsoft-365-copilot/extensibility/copilot-studio-agent-builder-build).
- **Publish Microsoft Copilot Studio agents to Microsoft 365 Copilot**

  Organizations can now publish, manage, and use agents built with Copilot Studio directly within the Microsoft 365 Copilot app-across both web and desktop-and in Microsoft Teams, bringing intelligent assistance into the flow of everyday work. [Learn more](https://learn.microsoft.com/en-us/microsoft-365-copilot/extensibility/overview-custom-engine-agent).

### Copilot Studio

- **See performance metrics for every knowledge source** \[Web\]

  Review usage frequency, answer rate, and error rate for each knowledge source to spot high-value content and quickly fix low-performing links, keeping your agents accurate and helpful. [Learn more](https://learn.microsoft.com/en-us/power-platform/release-plan/2025wave2/microsoft-copilot-studio/analyze-action-usage-agents).

### Excel

- **Copilot in Excel with Python \| Reasoning Model Integration \(Think Deeper\)** \[Mac, Windows, Web\]

  While performing advanced analysis with Copilot in Excel with Python, users can choose the "Think Deeper" mode to get a more elaborate and detailed plan, followed by automatic execution to generate Python code, results, and explanations. This improves performance on complex asks by leveraging the power of the latest AI reasoning models.

### Microsoft 365 admin center

- **Metadata for Shared agent management in Microsoft 365 admin center** \[Web\]

  IT admins can view metadata for Shared agents in Microsoft 365 admin center similar to metadata information for line of business applications built by customer organization. It provides IT admins the opportunity to explore all data besides honoring UX filters for a seamless user experience. [Learn more](https://learn.microsoft.com/en-us/microsoft-365/admin/manage/manage-shared-agents).

### Microsoft 365 Copilot app

- **Create in the Microsoft 365 Copilot app** \[Windows, Web\]

  The creative hub for AI led artifact generation capabilities. [Learn more](https://support.microsoft.com/topic/get-started-with-microsoft-365-copilot-create-6e0c616d-69fb-42f2-a4cb-c59e006ec4f5).
- **Updated UI for Microsoft 365 Copilot App** \[Windows, Web\]

  The Microsoft 365 Copilot app is your starting place for AI at work, offering quick access to secure AI chat, search, files, and content creation in one seamless app. [Learn more](https://www.microsoft.com/microsoft-365/blog/2025/04/23/microsoft-365-copilot-built-for-the-era-of-human-agent-collaboration).

### Microsoft 365 Copilot Chat

- **Locate your Copilot Pages in Microsoft 365 Copilot Chat navigation pane** \[Windows, Web\]

  For quick access to your Copilot Pages, find all page artifacts created across your apps/modules in one place underneath the Chat section in the Microsoft 365 Copilot app. [Learn more](https://techcommunity.microsoft.com/blog/nonprofittechies/introduction-to-microsoft-copilot-pages/4421413).

### Microsoft Purview compliance portal

- **Data assessments in Microsoft Purview AI Hub** \[Web\]

  Create targeted assessments, review sensitivity and access for key locations, and take remediation actions to reduce oversharing risks-all from one dashboard. [Learn more](https://learn.microsoft.com/en-us/purview/dspm-for-ai).

### OneNote

- **Copilot Chat on OneNote for web and in Teams** \[Web\]

  User can enjoy the power of Microsoft Copilot to OneNote for web and in Teams. [Learn more](https://techcommunity.microsoft.com/blog/microsoft365copilotblog/increase-your-productivity-with-copilot-on-onenote-web-and-onenote-in-teams/4374756).

### Teams

- **Copilot in Meetings will suggest follow up questions to ask it** \[Windows, Mac\]

  When Copilot in Teams Meetings responds to a prompt, it will also suggest follow-up prompts to ask Copilot that builds on the prior response. These questions will generally be based on the response it gave prior, and could be related to honing in on a particular topic, asking for more details, or even reformatting the content into a table if appropriate. [Learn more](https://support.microsoft.com/office/use-copilot-in-microsoft-teams-meetings-0bf9dd3c-96f7-44e2-8bb8-790bedf066b1).

### Viva Connections

- **New News feature in Microsoft Teams** \[Android, Windows, iOS, Web\]

  This update replaces the current Feed experience in Viva Connections across desktop, mobile, and web platforms with a SharePoint News reader experience. This new experience presents SharePoint news from organizational sites, boosted news, users' followed sites, frequent sites, and people they work with in an immersive reader format. It includes a Copilot-powered news summary as well, available only in Teams for Windows desktop in this initial release. [Learn more](https://techcommunity.microsoft.com/blog/viva_connections_blog/introducing-enterprise-news-reader-in-viva-connections/4383832).

### Word

- **Automatic summary of documents on file-open in Word** \[Windows, Mac, Web\]

  When users open a document, Copilot generates a summary in the Word window. You can hide the summary or open the Copilot chat pane to ask specific questions about the document. [Learn more](https://support.microsoft.com/office/create-a-summary-of-your-document-with-copilot-in-word-79bb7a0a-3bf7-41fe-8c09-56f855b669bf).
- **Implement coaching suggestions when rewriting your text with Copilot** \[Web\]

  Enhance your writing process by letting Copilot apply tailored coaching tips when rewriting your selected text-refine your documents effortlessly. [Learn more](https://support.microsoft.com/topic/use-coaching-to-review-content-in-word-for-the-web-fa09c055-d623-4d20-954f-9b064a5a7c80).
- **Kickstart your document with contextual prompts** \[Mac\]

  Copilot leverages your recent files and meetings to suggest contextual prompts, helping you quickly draft a new document for day-to-day tasks.

## June 24, 2025

Updates released between June 10, 2025, and June 24, 2025.

### Copilot extensibility

- **Admins can manage Copilot extensibility under Copilot tab in Microsoft 365 admin center** \[Windows, Web\]

  Admins have options to manage Copilot extensibility under Copilot tab including agent management for IT published agents and shared agents. [Learn more](https://learn.microsoft.com/en-us/microsoft-365/admin/manage/manage-copilot-agents-integrated-apps).
- **Build agents faster with built in Office skills** \[Windows, Web\]

  Empower your agent building by consuming built-in Office skills like Q&A on documents and PowerPoint summaries. This feature speeds up integrations, reduces the need for custom solutions, and delivers context-aware insights for a smarter agent experience.
- **Build custom engine agents with Copilot Studio**

  Use Copilot Studio to create, test, and update custom engine agents that run seamlessly in Microsoft 365 Copilot Chat and Teams, streamlining your development and deployment process. [Learn more](https://learn.microsoft.com/en-us/microsoft-365-copilot/extensibility/overview-custom-engine-agent).
- **Declarative agents can read the current document in WXP** \[Windows, Web\]

  Improve your workflow with agents that dynamically interact with open documents. Receive real-time suggestions, automate edits, and extract key data to streamline reviews and boost productivity. [Learn more](https://adaptivecards.microsoft.com/?topic=Action.InsertImage).
- **Developers can use Copilot Studio to create declarative agents that include Teams Channel as knowledge**

  Developers can use Copilot Studio to create declarative agents that include Teams Channel as knowledge.
- **Developers can use Teams Toolkit to create declarative agents that include Teams Channel as knowledge**

  Developers can use Teams Toolkit to create declarative agents that include Teams Channel as knowledge.
- **Discover, acquire, and manage agents through in-app store** \[Windows, Web\]

  Users can now easily discover, acquire, and manage Copilot agents directly within their Word and PowerPoint documents through a unified in-app store. This streamlined experience simplifies adding new capabilities-and Excel support is coming soon. [Learn more](https://devblogs.microsoft.com/microsoft365dev/office-addins-at-build-2025/#modernized-store-for-office-add-ins-and-copilot-agents).
- **Manage custom Copilot agents in Agent Center** \[Windows, Web\]

  Organize, store, and update your declarative Copilot agents in one place. Agent Center lets developers register in-context actions, fine-tune prompts, and test behavior faster-so IT admins can roll out reliable, task-specific Copilot experiences at scale. [Learn more](https://devblogs.microsoft.com/microsoft365dev/introducing-the-agent-store-build-publish-and-discover-agents-in-microsoft-365-copilot/).
- **Microsoft 365 Agents Toolkit uses Kiota as the API plugin generation tool**

  The Microsoft 365 Agents Toolkit now generate API plugins using Kiota. This unlocks new scenarios in the Agents Toolkit like searching our repository of public APIs, visually selecting the main integration endpoints and improving the maintainability of existing plugins by adding new endpoints as the developer continue evolving their agents.
- **Non-citation links remain visible in custom actions** \[Windows, Web\]

  Links returned from your custom actions are no longer redacted when they aren't part of a citation, letting users follow the full URL for easier validation and deeper exploration. [Learn more](https://techcommunity.microsoft.com/blog/microsoftdefenderforoffice365blog/safelinks-protection-for-links-generated-by-m365-copilot-chat-and-office-apps/4396828).

### Copilot Studio

- **Add custom Copilot Studio agents to Microsoft 365** \[Web\]

  Publish your Copilot Studio agent to the Microsoft 365 channel in one click, then roll it out to yourself, a pilot group, or your whole org. Messages, quick replies, adaptive cards, and multi-turn chat work instantly, while Power Platform analytics and governance keep everything secure and measurable. [Learn more](https://learn.microsoft.com/en-us/microsoft-365-copilot/extensibility/publish).
- **Automate repetitive tasks with agent flows** \[Web\]

  Build agent flows in Copilot Studio using natural language to automate workflows with AI-powered actions. Makers can build intelligent, scalable, and flexible automations for tasks ranging from intelligent summarization to advanced approvals - and get fast, consistent results. [Learn more](https://learn.microsoft.com/en-us/microsoft-copilot-studio/flows-overview).
- **C2 image upload and Q&A** \[Web\]

  Allow your Microsoft Copilot Studio agent to analyze images that users upload during conversations with the agent. This feature enhances visual content collaboration with intelligent insights for everyday tasks. [Learn more](https://learn.microsoft.com/en-us/microsoft-copilot-studio/image-input-analysis).
- **Quarantine compromised agent to boost security**

  Give IT admins a critical tool to isolate potentially compromised agents, reducing risk and protecting your network without disrupting daily operations.

### Excel

- **Use Copilot with any table in the workbook, referring by natural language** \[iOS, Web, Mac, Windows\]

  Copilot uses the context of your prompt to pick what selection of data to answer about and reason over, including tables in other sheets. [Learn more](https://techcommunity.microsoft.com/blog/excelblog/smarter-context-awareness-for-copilot-in-excel/4424939).

### Microsoft 365 Copilot app

- **Copilot Notebooks** \[Web\]

  Copilot Notebook in the Microsoft 365 Copilot app streamlines your workflow by integrating notebook functionality directly into the app. [Learn more](https://support.microsoft.com/topic/get-started-with-microsoft-365-copilot-notebooks-0775e693-11c6-4d80-8aba-fcc81a737a06).
- **Upload phone images to Copilot in Office apps** \[Windows\]

  Snap a photo on your phone and send it straight to Copilot in Word, PowerPoint, Excel, or OneNote to generate content, extract text, or get design ideas-no cables or transfers needed. [Learn more](https://techcommunity.microsoft.com/blog/microsoft365insiderblog/upload-a-phone-image-to-microsoft-365-copilot/4398121).
- **Use Copilot suggested prompts for recommended entities** \[Windows, Mac, Web\]

  Empower your work with a $30 Copilot license by clicking on curated prompts within recommended entities. Uncover key insights on demand-helping you boost productivity in everyday tasks. [Learn more](https://techcommunity.microsoft.com/blog/microsoft365copilotblog/getting-the-most-from-the-copilot-prompt-gallery/4383106).

### Microsoft 365 Copilot

- **Copilot Prompt Gallery - share prompts with a Teams team** \[Windows, Web\]

  Share custom prompts with members of a Microsoft Teams team directly from Copilot Prompt Gallery, allowing colleagues to easily discover and reuse them in Copilot Chat. [Learn more](https://support.microsoft.com/topic/sharing-prompts-with-a-team-2fa7a228-8645-4dc4-beec-d75d6d0bc752).

### Microsoft 365 Copilot Chat

- **Catch up on Task related emails through Microsoft 365 Copilot Chat.** \[Windows\]

  Users can use Microsoft 365 Copilot Chat to prioritize emails that require immediate attention, address urgent tasks, or contain action items or questions. Timely identification of such emails helps users complete these tasks efficiently or plan their work effectively.
- **Find any past Copilot conversation instantly** \[Web\]

  Search your Copilot Chat history by keyword to revisit decisions, copy answers, or resume a discussion without endless scrolling. [Learn more](https://www.microsoft.com/microsoft-365/roadmap?filters=&searchterms=388371).
- **Locate your Copilot Pages in Copilot Chat navigation pane** \[Windows, Web\]

  For quick access to your Copilot Pages, find all page artifacts created across your apps/modules in one place underneath the Chat section in the Microsoft 365 Copilot app. [Learn more](https://techcommunity.microsoft.com/blog/nonprofittechies/introduction-to-microsoft-copilot-pages/4421413). .
- **Play back responses as audio** \[Windows, Web\]

  Listen to Copilot's replies with a built-in read aloud feature-ideal for multitasking or when you need to review content hands-free. [Learn more](https://www.microsoft.com/microsoft-365/roadmap?filters=&searchterms=475967).
- **Scheduled prompts** \[Windows, Mac, Web, Teams\]

  Plan ahead by scheduling essential prompts for repeated tasks in Copilot chat. Create a productive routine that helps you stay organized and efficient. [Learn more](https://learn.microsoft.com/en-us/microsoft-365/copilot/scheduled-prompts).

### Microsoft Clipchamp

- **Clipchamp Copilot video creator** \[Windows, Web\]

  Create a video draft on any topic by providing a prompt. Clipchamp will generate a script, source stock footage and music, add AI voice-over, text overlays, and transitions-giving you a ready-to-edit project you can export to OneDrive. [Learn more](https://support.microsoft.com/topic/how-to-create-video-with-copilot-7586329a-64e0-4ae9-9444-0da5b1c2b848).

### Microsoft Loop

- **Rich artifacts in Copilot Pages** \[Web\]

  You can now create rich artifacts, including interactive charts, tables, complex diagrams, and code created with Copilot from enterprise or web data. Artifacts can be added to Pages to further edit and refine with Copilot. They are interactive and stay in sync across Microsoft 365 when shared for collaborative work. [Learn more](https://support.microsoft.com/topic/turn-raw-data-into-dynamic-visuals-with-microsoft-365-copilot-pages-8a88637e-87f7-4099-b1c3-1472c2ba625c).

### Outlook

- **Content language is the default summarize language** \[Mac\]

  When summarizing Copilot tries to identify the language of the email and summarize in that language. [Learn more](https://support.microsoft.com/office/frequently-asked-questions-about-copilot-in-outlook-07420c70-099e-4552-8522-7d426712917b?storagetype=live).

### PowerPoint

- **Create a PowerPoint slide from a file or prompt** \[Web, Windows, Mac\]

  Creating impactful slides can be challenging and time-consuming. Copilot helps you quickly turn your ideas and files into a fully designed slide with content ready to edit and refine, making the presentation creation and refinement process more personalized and efficient. [Learn more](https://support.microsoft.com/topic/add-a-slide-from-a-file-with-copilot-in-powerpoint-9034b581-38df-46be-a725-986cbbd4b5d4).
- **Designer is now part of Copilot, enhanced with new template and slide suggestions** \[Mac, Windows, Web\]

  Enjoy familiar Designer slide layouts and presentation template suggestions in a vertical gallery. Copilot now brings you enhanced suggestions to quickly build impactful presentations. [Learn more](https://support.microsoft.com/office/create-professional-slide-layouts-with-designer-53c77d7b-dc40-45c2-b684-81415eac0617).
- **Easily select a template while you create a new PowerPoint presentation with Copilot** \[Mac, Web, Windows\]

  When creating a new presentation with Copilot in PowerPoint, choose a template from your organization's collection for on-brand presentations, or select from Microsoft's handpicked templates, ensuring the new presentation is built as per your chosen template. [Learn more](https://support.microsoft.com/topic/keep-your-presentation-on-brand-with-copilot-046c23d5-012e-49e0-8579-fe49302959fc).
- **Reference a PDF file when creating a presentation with Microsoft 365 Copilot** \[Mac, Windows, Web\]

  You can now reference a PDF file when you create a presentation with Copilot within the PowerPoint application. [Learn more](https://support.microsoft.com/office/create-a-new-presentation-with-copilot-in-powerpoint-3222ee03-f5a4-4d27-8642-9c387ab4854d).

### Teams

- **Copilot generated summaries for call transfers on Teams phone devices** \[Android\]

  Copilot generated summary provides an overview of the details and outcomes of transferred calls. It includes information such as the caller's details, the reason for the transfer, and the final resolution. [Learn more](https://support.microsoft.com/office/get-started-with-copilot-in-microsoft-teams-phone-97c55ffb-1499-4b0a-8caa-980ebb4b697b).
- **Speaker recognition and attribution in Teams Rooms on Android** \[Android\]

  Enhance your meetings with real-time speaker recognition and transcript attribution in Teams Rooms on Android. This feature identifies voices through cloud-enabled intelligent speakers and lets you securely enroll voices via Teams Settings-note that a Teams Rooms Pro license is required. [Learn more](https://learn.microsoft.com/en-us/microsoftteams/rooms/voice-recognition?branch=main&branchFallbackFrom=pr-en-us-14676).

## June 10, 2025

Updates released between May 29, 2025, and June 10, 2025.

### Copilot extensibility

- **One-click setup for all connectors** \[Windows, Web\]

  New and existing connectors now install in a single step within the admin center, speeding up data integration and reducing support calls. [Learn more](https://learn.microsoft.com/en-us/microsoft-365-copilot/extensibility/overview-copilot-connector).

### Copilot Studio

- **Encrypt Copilot content with your own keys** \[Web\]

  Microsoft Copilot Studio now allows you to use your own customer manager encryption keys \(CMKs, hosted in Microsoft Azure Key Vault\) to govern how Copilot Studio encrypts your copilot content.

  By using customer managed encryption keys \(CMKs\), you can ensure that any data provided to your agent by your users, and the data you provide to Microsoft, is encrypted with your own keys.

  You maintain control of your keys, providing you with further protection over the security of your data and ensuring you have control over how your data is stored at rest.

  Key capabilities include hosting with Azure Key Vault to manage your keys, lifetimes, and rotation periods, encryption of all of your content, including copilot topics, settings and configurations, and conversation transcript data, rotation of CMKs, and, evocation of access, if necessary. [Learn more](https://learn.microsoft.com/en-us/microsoft-copilot-studio/admin-customer-managed-keys).
- **Improve the agent template gallery in the create page** \[Web\]

  Experience a redesigned agent template gallery that makes it simple to find and select the right templates quickly. This modern, organized layout boosts productivity and encourages more frequent use. [Learn more](https://learn.microsoft.com/en-us/microsoft-copilot-studio/authoring-install-agent).

### Excel

- **Create with Copilot generates templates and tables** \[Web\]

  Create with Copilot in Excel empowers you to generate tailored templates and tables simply by writing prompts. Its multi-turn conversation refines schemas, formulas, and visuals for a polished result.
- **Improvements to Copilot chat experience** \[Windows, Web, Mac\]

  Improvements to the Excel Copilot chat experience to give more consistent responses to all chat questions.

### Microsoft 365 Copilot Chat

- **Advanced email filtering in Copilot chat** \[Windows\]

  Quickly surface exactly the emails you need-ask Microsoft 365 Copilot Chat for "last week's external emails," "threads I haven't replied to," "purple-category mail," or "summarize German emails" "emails where I'm on the To line"-and focus on what matters most.
- **Find emails awaiting your reply** \[Windows\]

  Tell Microsoft 365 Copilot Chat "show me emails that I need to reply" and instantly see unread, read, @mentioned emails or emails with some question, task that you haven't answered-while hiding threads you've already closed-so you can clear your inbox with confidence.
- **Manage Microsoft 365 Copilot personalization in one place**

  A new tenant-level control groups personal-productivity AI features under a single toggle, letting admins enable or disable them globally or by Entra group with ease. [Learn more](https://learn.microsoft.com/en-us/graph/control-enhanced-personalization-privacy).
- **Microsoft 365 Copilot Chat: Updates to Copilot Chat response output** \[Web\]

  Easily interact with Microsoft Graph content represented by bolder references, new action bar, and more.
- **Module UI refresh** \[Windows, Web\]

  Copilot Chat is designed to provide a streamlined UI, making it easy to get started and achieve your goals quickly. It offers a helpful, understanding, and personalized experience, allowing you to search for past interactions, content, agents, or pages with ease. [Learn more](https://support.microsoft.com/topic/get-started-with-microsoft-365-copilot-chat-5b00a52d-7296-48ee-b938-b95b7209f737).
- **Simplified Input box update** \[Windows, Web\]

  We've made it easier for users to type prompts with access to CIQ, local files, attach cloud files, and agents by adding it under the Plus Menu.

### Microsoft Loop

- **Add a Loop workspace to your Teams channel** \[Web\]

  Pin a Loop workspace as a channel tab so everyone can brainstorm, co-create, and organize project content in real time while membership, governance, and compliance stay in sync. [Learn more](https://techcommunity.microsoft.com/blog/microsoft365insiderblog/collaborate-in-real-time-with-workspaces-in-teams/4414334).
- **Copilot Pages module on Microsoft 365 Copilot mobile app** \[iOS\]

  With the Copilot Pages module in the Microsoft 365 Copilot app on your mobile, you can now access all of your Pages in one place on the go. [Learn more](https://support.microsoft.com/topic/create-edit-and-share-microsoft-365-copilot-pages-from-your-phone-6426dfd5-081c-4a9f-b35e-830685deeda7).
- **Create Copilot Pages from Copilot Chat on your mobile phone** \[iOS\]

  Create Copilot Pages on your mobile phone to continue working on the go. Pages shared in Microsoft 365 are interactive and automatically synchronized for seamless collaboration. [Learn more](https://support.microsoft.com/topic/create-edit-and-share-microsoft-365-copilot-pages-from-your-phone-6426dfd5-081c-4a9f-b35e-830685deeda7).

### Microsoft Purview compliance portal

- **Data Security Posture Management for AI** \[Web\]

  Microsoft Purview Data Security Posture Management for AI \(DSPM for AI\) is a centralized location to gain insights into generative AI activity including the sensitive data flowing in AI prompts. [Learn more](https://learn.microsoft.com/en-us/purview/ai-microsoft-purview-considerations).
- **Gain DLP policy insights with Copilot** \[Web\]

  Let Copilot instantly summarize Data Loss Prevention policies across locations, classifiers, and notifications. Use natural-language prompts to zoom into specific policies, spot gaps, and adjust settings faster-keeping your organization's data posture aligned without manual digging. [Learn more](https://learn.microsoft.com/en-us/purview/dlp-test-dlp-policies#get-insights-with-security-copilot).

### OneNote

- **Include OneNote pages in Copilot reasoning**

  Copilot can now use your OneNote content as context, helping you generate more informed summaries, drafts, and action items.

### Outlook

- **Custom Instructions for draft with Copilot** \[Android, Windows, iOS, Mac, Web\]

  Give Copilot some instructions about your emails - like the tone, length, greeting - so your Copilot generated drafts sound more like you want them to. #newoutlookforwindow
- **Schedule a meeting from an email with Copilot** \[Android, Windows, iOS, Mac, Web\]

  Turn any email thread into a meeting in one click. Copilot builds a complete invite for your review -title, agenda, attendee list, and a summary of the email conversation-plus attaches the original email thread so everyone is up to speed. Available in the new Outlook for Windows, web, Mac, and mobile. [Learn more](https://support.microsoft.com/office/create-a-meeting-and-agenda-with-copilot-in-outlook-31a44dfa-62bb-4751-82c4-14327a26759f).

### PowerPoint

- **Microsoft 365 Copilot Chat: Reference a TXT file when creating a presentation with Copilot** \[Windows, Mac, Web\]

  You can now reference a TXT file when you create a presentation with Copilot within the PowerPoint application. [Learn more](https://support.microsoft.com/office/create-a-new-presentation-with-copilot-in-powerpoint-3222ee03-f5a4-4d27-8642-9c387ab4854d).

### Teams

- **Improvements to the transcription experience in meetings** \[Windows, Mac\]

  These updates enhance the transcription experience in meetings. When transcription, recording, or Copilot is enabled, users are prompted to choose the spoken language for accurate captions. Once transcription is running, only the organizer, co-organizers, and transcript initiator can change that language. A new settings page under Caption settings > Language settings > Meeting spoken language, along with a matching option under Transcript > Language settings, streamlines configuration. If someone speaks a language that doesn't match the selected one, The organizer/co-organizer and initiator receive a mismatch notification so they can adjust quickly. [Learn more](https://support.microsoft.com/office/use-live-captions-in-microsoft-teams-meetings-4be2d304-f675-4b57-8347-cbd000a21260#:%7E:text=The%20meeting%20organizer%2C%20co%2Dorganizer\(s\)%2C%20transcript,Select%20Update%20to%20change.).
- **Microsoft Teams: Intelligent recap support for ad-hoc meetings and calls in GCC High** \[Android, Windows, iOS, Mac, Web\]

  Intelligent meeting recap is now available in GCC High for impromptu calls and meetings, like those started from 'Meet now' and calls started from chat. You can easily browse the recording by speakers and topics, as well as access AI-generated notes, AI-generated tasks, and name mentions after the ad-hoc meeting ends. This capability is available for users with a Teams Premium or M365 Copilot license.

### Viva Glint

- **Feature access management for Copilot in Viva Glint** \[Web\]

  Enable or disable Copilot in Viva Glint for specific users directly from the Microsoft 365 admin center, giving you granular control over AI access. [Learn more](https://learn.microsoft.com/en-us/viva/feature-access-management).

### Word

- **Draft content from up to 10 chosen references** \[Mac, Windows\]

  Type a forward slash \(/\) to pick as many as ten files, meetings, or emails for Copilot to cite while drafting your document. The release started with 10 chosen references but is expanding to support up to 20. [Learn more](https://techcommunity.microsoft.com/blog/microsoft365insiderblog/expanding-reference-capabilities-with-microsoft-365-copilot-in-word/4406054).
- **Write a prompt for selected portions of text in Word** \[Mac\]

  Writing a prompt to draft content based on your selection no longer expands your selection to the entire paragraph, table, or list. You can prompt based on a single sentence or item.
- **Write a prompt for selected text in Word** \[Windows\]

  Draft content based only on the sentence or list item you highlight-no more expanding the selection to the entire paragraph or table.

## May 29, 2025

Updates released between May 13, 2025, and May 29, 2025.

### Copilot extensibility

- **Create agents that learn from a Teams channel**

  Build custom Copilot agents that pull knowledge directly from a chosen Teams channel, letting them answer FAQs or surface project updates without extra coding.
- **Insert images in adaptive cards for richer interactions** \[Windows, Web\]

  Make your adaptive cards more dynamic by adding images-perfect for illustrating ideas, sharing visual data, or engaging users with eye-catching content. This feature helps teams communicate clearly, support diverse learning styles, and create more memorable interactions in everyday workflows. [Learn more](https://learn.microsoft.com/en-us/microsoft-copilot-studio/guidance/adaptive-card-summarize-responses).
- **Unified Agent Management for admins in Microsoft 365 admin center** \[Windows, Web\]

  Admins can consistently manage Copilot agents in the Microsoft 365 admin center, regardless of how they were built, simplifying deployment and governance. [Learn more](https://learn.microsoft.com/en-us/microsoft-365/admin/manage/manage-plugins-for-copilot-in-integrated-apps).

### Copilot Studio

- **Reuse connector and API actions across multiple copilots** \[Web\]

  Take an action that already works in Copilot for Sales and publish it to Customer Service-or any other eligible Copilot-in a few clicks. Skip duplicate setup, speed up delivery, and keep functionality consistent, all with built-in admin approval flows. [Learn more](https://learn.microsoft.com/en-us/microsoft-copilot-studio/agent-extend-action-rest-api).
- **Unpublish connector actions when data or services change** \[Web\]

  Roll back a published connector to draft so it no longer appears in Microsoft 365 Copilot. Makers can pause their own connectors, and admins can disable any connector to update configurations or retire obsolete services-without deleting them. [Learn more](https://learn.microsoft.com/en-us/power-platform/release-plan/2025wave1/microsoft-copilot-studio/unpublish-connector-actions-copilot-agents).

### Excel

- **Access Copilot tools right from the grid** \[Windows\]

  A handy Copilot icon and context menu now follow your work in the worksheet, letting you launch summaries, formula help, and more without breaking focus. [Learn more](https://techcommunity.microsoft.com/blog/excelblog/how-to-get-started-with-copilot/4383870).
- **Improved fallback answers in Copilot Chat** \[Web\]

  When specific data isn't found, Copilot seamlessly shifts to general reasoning so conversations keep flowing and users avoid dead ends in Excel for the web.
- **Visual outline confirms Copilot's data range** \[Mac\]

  When you call on Copilot, Excel now draws a clear border around the table or cell range in focus. Instantly see exactly what data is summarized, cleaned, or chart-ready-so you can adjust the selection before Copilot gets to work.

### Forms

- **Automate response collection and insights in Forms** \[Web\]

  Copilot builds a follow-up plan, sends reminders, tracks progress, and surfaces early trends-then hands off to Excel for deeper analysis-so you spend less time chasing respondents and more time acting on feedback. [Learn more](https://techcommunity.microsoft.com/blog/microsoftformsblog/introducing-new-agentic-features-for-copilot-in-forms-%E2%80%93-create-refine-and-share-/4406237).
- **Copilot in Forms can now reference files to help generate drafts** \[Web\]

  When creating a form with Copilot, users can now reference existing documents such as Word, Excel, and PowerPoint. Users can also reference an existing form by pasting the form's URL into the prompt box. Additionally, Copilot can search and suggest relevant files when generating a form, so users can easily create a draft that meets their needs. [Learn more](https://support.microsoft.com/office/frequently-asked-questions-about-copilot-in-forms-c9941b72-b32e-4c7e-9af9-e603929bb1d2).
- **Copilot in Forms has been refreshed to help users better refine and edit their forms** \[Web\]

  Copilot in Forms has been revamped to more easily help users refine and modify their forms. Users can now type prompts to Copilot to help with editing and refinement, so they can get tailored suggestions and easily get their forms ready to send. [Learn more](https://techcommunity.microsoft.com/blog/microsoftformsblog/introducing-new-agentic-features-for-copilot-in-forms-%E2%80%93-create-refine-and-share-/4406237).

### Microsoft 365 admin center

- **Usage reports - monitor m365.cloud.microsoft/chat/Teams/Outlook activity in Microsoft 365 Copilot Chat usage report** \[Web\]

  Track active users and last activity dates for m365.cloud.microsoft/chat, Teams, and Outlook-even for employees without a Copilot license-to gauge grassroots adoption and fine-tune rollout plans in Microsoft 365 Copilot Chat usage report. [Learn more](https://learn.microsoft.com/en-us/microsoft-365/admin/activity-reports/microsoft-copilot-usage).

### Microsoft 365 Copilot Chat

- **Analyze usage of declarative agent in Developer Portal**

  Developers of custom app and published apps can analyze declarative agent usage in Developer Portal. By using these analytics, developers can gain valuable insights into how users interact with your app, identify areas for improvement, and make data-driven decisions to enhance the overall user experience. [Learn more](https://learn.microsoft.com/en-us/microsoftteams/platform/concepts/build-and-test/analyze-your-apps-usage-in-developer-portal?tabs=custom-apps-built-for-your-org).
- **Bring Azure AI Search indexes into Copilot Studio knowledge** \[Web\]

  Attach existing Azure AI Search indexes as grounding data, enabling natural-language queries over enterprise content with minimal setup and no added cost.
- **Copilot Chat now offers access to cloud files to insert in user prompts** \[Windows, Web\]

  In the Web tab of Copilot Chat or Microsoft 365 Copilot, users can browse OneDrive or SharePoint, select a file, and drop it into their prompt to give Copilot precise context for richer responses.
- **Enable agent builder for Copilot chat** \[Windows, Web\]

  Empower developers with the ability to build custom agents to support Copilot Chat. This feature streamlines the creation of tailored chat experiences that enhance everyday communication and workflow. [Learn more](https://learn.microsoft.com/en-us/microsoft-365-copilot/extensibility/copilot-studio-agent-builder-build).
- **Enhanced typography improves readability** \[Windows\]

  Enjoy crisper fonts, roomier line spacing, clear headers, and neatly formatted tables and code blocks-making every Copilot chat easier to scan, share, and act on.
- **Expanded reference panel for sources and search results** \[Windows\]

  The reference widget now shows both cited sources and relevant web results, helping you verify information, resolve ambiguities, and ask smarter follow-up questions without leaving the chat.
- **Ground copilots with real-time data from Salesforce, ServiceNow, and more** \[Web\]

  Connect structured records from popular non-Microsoft apps directly in Copilot Studio so users can ask, "Show my open Zendesk tickets" and get instant answers without leaving chat.
- **Pay-as-you-go policies keep Copilot costs in check** \[Windows, Web\]

  Allocate budgets by department, set usage caps, and manage access from the admin center so your organization can innovate with Copilot while staying on budget. [Learn more](https://learn.microsoft.com/en-us/microsoft-365/copilot/pay-as-you-go/overview).
- **Safe Links validates redacted URLs** \[Windows\]

  When Copilot masks a link, Safe Links now scans it instantly and alerts users to malicious sites, adding an extra layer of protection before anyone clicks. [Learn more](https://techcommunity.microsoft.com/blog/microsoftdefenderforoffice365blog/safelinks-protection-for-links-generated-by-m365-copilot-chat-and-office-apps/4396828).

### PowerPoint

- **Ask Copilot to rewrite text as a list** \[Web, Mac, Windows\]

  Transform paragraphs into clear bullet points or lists with a single command-ideal for quickly organizing content when preparing your presentation. [Learn more](https://support.microsoft.com/topic/elevate-your-presentation-game-with-copilot-s-text-rewrite-feature-in-powerpoint-d70b140b-bb3f-46b7-be64-ceec526a8dcd).

### Word

- **Ask agents to refine any text selection** \[Windows, Web\]

  Highlight a section of your document and let Copilot agents rewrite, shorten, or expand it-keeping the rest of your file private while you perfect the details.
- **Ask Copilot to analyze document visuals** \[Mac\]

  Add any image, chart, or diagram to your prompt and Copilot instantly extracts text, explains trends, suggests alt text, and surfaces quick insights-making documents more accessible and informative in seconds.
- **Chat with Copilot about any image or chart** \[Windows\]

  Drop a visual into Copilot chat to extract text, get a plain-language description, generate alt text, or request quick insights-perfect for accessibility checks or fast analysis. [Learn more](https://support.microsoft.com/topic/file-upload-in-microsoft-copilot-8b7bf432-9576-4b16-9dee-6c19a4169e62).

## May 13, 2025

Updates released between April 29, 2025, and May 13, 2025.

### Copilot Studio

- **Deeper visibility into agent runs**

  Trace every agent session from trigger to transcript. Inspect actions, inputs, and outputs in one place to debug faster, refine behavior, and document compliance. [Learn more](https://learn.microsoft.com/en-us/power-platform/release-plan/2024wave2/change-history).
- **Monitor autonomous agents with detailed analytics** \[Web\]

  Instantly see run volume, trigger breakdowns, success rates, action paths, and run-time details for every autonomous agent. Use these insights to spot failures, tune performance, and boost reliability before your users notice issues.
- **Single connector for knowledge and actions** \[Web\]

  You can now reuse connector actions across multiple Copilot deployments without recreating them each time. This feature lets you select a previously published action-such as one from Copilot for Sales-and publish it to other endpoints, such as Copilot for Customer Service, with just a few clicks. It's enabled by default and streamlines deployment while reducing duplication. [Learn more](https://learn.microsoft.com/en-us/power-platform/release-plan/2024wave2/microsoft-copilot-studio/publish-connector-actions-multiple-copilot-deployments).

### Excel

- **Advanced analysis with Python and Copilot** \[Windows\]

  Chat with your spreadsheet and let Copilot run Python scripts to surface trends, build rich visuals, and test what-if scenarios-now fully localized for your team's language. [Learn more](https://support.microsoft.com/office/copilot-in-excel-with-python-364e4ae9-9343-4d56-952a-5f62b0f70db6).
- **Ask Copilot about any part of your sheet** \[Web, Mac, Windows, iOS\]

  When you ask questions about your worksheet, Copilot can look at the content of your sheet and use it to inform an answer to your question. This includes understanding worksheet data on your selected area, beyond tables and ranges, and provide Copilot answers in chat.
- **Easily access copilot on web** \[Web\]

  Find a dedicated Copilot icon in your web spreadsheet, allowing you to tap into AI-powered insights and streamline tasks without breaking your workflow. [Learn more](https://support.microsoft.com/office/get-started-with-copilot-in-excel-d7110502-0334-4b4f-a175-a73abdfc118a).
- **Visual cue for Copilot's data context** \[Web\]

  A subtle outline now highlights the exact cells or table Copilot is working with, so you can confirm the right data is selected before insights or edits are generated.

### Microsoft 365 admin center

- **AI adoption score** \[Web\]

  A new people experiences category in Adoption Score in the Microsoft 365 admin center introduces AI adoption metrics, helping organizations understand how Microsoft Copilot features are being used across Microsoft 365. [Learn more](https://learn.microsoft.com/en-us/microsoft-365/admin/adoption/ai-adoption-score#organizational-messages-in-ai-adoption-score).
- **Manage pay-as-you-go billing for Copilot** \[Windows, Web\]

  Admins can manage pay-as-you-go billing directly within Copilot settings in the Microsoft 365 admin center. This capability is available to users with Global admin, AI admin, and Global reader roles. [Learn more](https://learn.microsoft.com/en-us/microsoft-365/copilot/pay-as-you-go/setup).
- **Overview of Copilot for admin** \[Web\]

  Streamline IT management with Copilot's real-time, contextually relevant insights that help you make faster, data-driven decisions in the Microsoft 365 admin center. [Learn more](https://aka.ms/copilotinmac).

### Microsoft 365 Copilot app

- **Copilot in Excel with Python for Mac** \[Mac\]

  Speak plain English and let Copilot write and run Python for forecasting, machine learning, and rich visuals-results land right on the grid in Excel for Mac. [Learn more](https://support.microsoft.com/office/copilot-in-excel-with-python-364e4ae9-9343-4d56-952a-5f62b0f70db6).

### Microsoft 365 Copilot Chat

- **Conversation history grouped by time frame**

  Copilot Chat now clusters past sessions into daily and weekly views, making it easier to scan, revisit, and manage your conversations.
- **Copilot pages in Government Clouds** \[Windows\]

  Copilot Pages is an interactive, shareable canvas in Microsoft 365 Copilot Chat designed for multiplayer AI collaboration. With Pages, users can turn Copilot responses into something durable with a side-by-side page where users can edit and share with others to collaborate. Now available for Government Cloud users. [Learn more](https://support.microsoft.com/topic/introducing-microsoft-365-copilot-pages-6674bd51-9ff5-42c4-9256-44d9428a726f).
- **Create web-aware agents in Agent Builder**

  Build declarative agents that draw knowledge from up to four public websites, delivering more precise, source-linked answers inside Microsoft 365 chat experiences. [Learn more](https://learn.microsoft.com/en-us/microsoft-365-copilot/extensibility/copilot-studio-agent-builder-build).
- **Image generation in mobile Copilot chat** \[Android, iOS\]

  Create images using natural language to visualize concepts and ideas within the flow of work, directly in Copilot on Microsoft 365, Teams, and Outlook mobile apps.
- **Unified prompt box across web and work chats** \[Windows, Web\]

  Enjoy a consistent prompting experience across Copilot Chat with an input box that looks and behaves the same in both work and web chat modes.

### Microsoft Graph

- **Agent plugins for Semantic Kernel :** \[Developer\]

  Accelerate Copilot solutions by adding ready-made plugins that tap Microsoft 365 data and actions through Semantic Kernel-so you can build smarter agents with far less code. [Learn more](https://learn.microsoft.com/en-us/dotnet/api/microsoft.semantickernel.declarativeagentextensions).

### Microsoft Viva

- **AI Administrator can manage Microsoft Copilot Dashboard settings** \[Web\]

  Delegate Copilot Dashboard control to the new Entra AI Administrator role, giving admins the permissions they need without granting AI admin privileges. [Learn more](https://learn.microsoft.com/en-us/viva/insights/advanced/admin/manage-settings-copilot-dashboard).

### OneDrive

- **Ask Copilot questions about images** \[Web\]

  Select up to five pictures in OneDrive Web and chat with Copilot to summarize, extract text, or describe what's inside-perfect for cataloging photos or pulling details from scanned documents. [Learn more](https://support.microsoft.com/topic/ask-about-a-topic-without-opening-your-files-8ea1bb0d-5ae7-4f81-8cb8-cd755862834b).

### PowerPoint

- **Get slide template suggestions as you create** \[Windows\]

  Copilot now recommends polished layouts the moment you add or name a slide, letting you stay in the flow and skip manual design hunts. [Learn more](https://techcommunity.microsoft.com/blog/microsoft365insiderblog/jumpstart-your-presentations-with-slide-starters/4407669).
- **Suggestions for slide templates as you work** \[Mac, Web\]

  On PowerPoint for Mac, Copilot proposes design-ready layouts as soon as you insert a slide or start typing a title, helping you build polished decks faster. [Learn more](https://techcommunity.microsoft.com/blog/microsoft365insiderblog/jumpstart-your-presentations-with-slide-starters/4407669).

### Viva Insights

- **Viva Insights now included in Microsoft 365 Copilot subscriptions** \[Windows, Web\]

  Create advanced, custom reports with Viva Insights to understand Copilot adoption, productivity and business impact. Full access to Viva Insights is available now with Microsoft 365 Copilot subscriptions.

### Word

- **Choose the level of detail for summaries when documents are opened** \[Windows, Mac, Web\]

  Tailor each document opening with your preferred summary style-select brief, standard, or detailed insights to match your workflow. [Learn more](https://support.microsoft.com/office/create-a-summary-of-your-document-with-copilot-in-word-79bb7a0a-3bf7-41fe-8c09-56f855b669bf).
- **Key statistics at a glance in Copilot summaries** \[Web\]

  Instantly see critical numbers-totals, dates, percentages, and more-in the Understanding tab, so you can grasp a document's quantitative story in seconds. [Learn more](https://support.microsoft.com/office/create-a-summary-of-your-document-with-copilot-in-word-79bb7a0a-3bf7-41fe-8c09-56f855b669bf).
- **Suggested questions help you explore any document** \[Web\]

  The Understanding tab now proposes smart questions about the file you're reading-just click one to see Copilot's answer and dive deeper without crafting your own prompt. [Learn more](https://support.microsoft.com/office/create-a-summary-of-your-document-with-copilot-in-word-79bb7a0a-3bf7-41fe-8c09-56f855b669bf).

## April 29, 2025

Updates released between April 16, 2025, and April 29, 2025.

### Excel

- **Ask Copilot to extract insights from inserted images** \[Windows\]

  Transform images in your Excel workflows into actionable data. Simply insert an image into the prompt area and ask Copilot to break down details and trends, so you can make informed decisions on the fly.
- **Formula Explain on grid entry points** \[Web\]

  Understand complex formulas by triggering step-by-step explanations directly from the grid. Copilot breaks down calculations and clarifies references so you gain confidence when working with your data. [Learn more](https://support.microsoft.com/topic/understanding-formulas-with-copilot-7838fb47-7309-4dac-ba7a-8080cb75ee06).
- **Paste images into Copilot chat** \[Web, Windows\]

  Ask questions about images you insert into the prompt area to extract key data for your spreadsheets. [Learn more](https://techcommunity.microsoft.com/blog/microsoft365insiderblog/add-images-to-your-copilot-prompts-in-word-and-powerpoint/4359423).
- **Seamless transition from clean data to Copilot chat** \[Web\]

  After finalizing your data with Clean Data, effortlessly switch to Copilot chat for deeper insights and analysis. [Learn more](https://support.microsoft.com/office/clean-data-in-excel-7fe20d89-3f57-46d3-b659-e8f3ee853bda).

### Microsoft 365 Copilot extensibility

- **Agent Builder now available in new regions** \[Windows, Web\]

  You can now access Copilot Studio agent builder in Norway, Sweden, South Korea, and South Africa. [Learn more](https://learn.microsoft.com/en-us/microsoft-365-copilot/extensibility/copilot-studio-agent-builder-availability#regional-availability).
- **Developers using Copilot Studio can use API key auth for actions in a declarative agent**

  Developers using Copilot Studio can now leverage API key authentication to perform actions in a declarative agent, enhancing security and integration ease. [Learn more](https://learn.microsoft.com/en-us/microsoft-365-copilot/extensibility/overview-api-plugins).
- **Grounding with metered consumption in Copilot Studio**

  Makers can now ground their agents built in Copilot Studio with their enterprise data using metered consumption. This ensures compliant access to your enterprise data estate without need to export or egress content to an alternate location or public cloud, creating vector embeddings, or custom RAG solutions. This feature provides flexible and cost-effective access to secure data retrieval. [Learn more](https://learn.microsoft.com/en-us/microsoft-365-copilot/extensibility/prerequisites).

### Microsoft 365 Copilot Chat

- **Microsoft 365 Copilot for GCC Environments: Wave 2** \[Windows\]

  Bringing Microsoft 365 Copilot GCC your AI assistant for work in the GCC environment. It combines the power of Large Language Models with your work content and context, to help you draft and rewrite, summarize and organize, catch up on what you missed, and get answers to questions via open prompts. Copilot generates answers using the rich, people-centric data and insights available in the Microsoft Graph. Microsoft 365 Copilot GCC is now available in Stream, SharePoint, OneNote, and Pages in Loop. [Learn more](https://techcommunity.microsoft.com/blog/publicsectorblog/what%E2%80%99s-new-in-microsoft-365-copilot-for-government/4399086).
- **Submit feedback on the agent builder experience** \[Windows, Web\]

  Improve your custom Copilot Chat solutions by providing targeted feedback on RAI and agent response during test chats. This direct input helps refine and enhance the builder experience. [Learn more](https://learn.microsoft.com/en-us/microsoft-365-copilot/extensibility/copilot-studio-agent-builder#submit-feedback).

### Microsoft Purview

- **GCC Microsoft Purview capabilities for Microsoft 365 Copilot** \[Web\]

  Microsoft Purview is launching several capabilities in government cloud environments that help secure and govern data in Microsoft 365 Copilot. These are capabilities in Information Protection, Data Lifecycle Management, Audit, eDiscovery, and Communication Compliance. These capabilities are available once Microsoft 365 Copilot is deployed. [Learn more](https://learn.microsoft.com/en-us/purview/ai-microsoft-purview).

### Outlook

- **Chat with Copilot in Outlook for Mac** \[Mac\]

  The same Microsoft Copilot experience you can get in the Microsoft Teams app, at copilot.microsoft.com \(work mode\) and in other places is now available from within Microsoft Outlook for Mac. You can find the Copilot app in the left app bar. [Learn more](https://support.microsoft.com/office/frequently-asked-questions-about-copilot-in-outlook-07420c70-099e-4552-8522-7d426712917b).
- **Prepare for meetings with AI-generated insights** \[Web\]

  Stay ahead of busy schedules by using the proactive "Prepare" button in your inbox to generate key meeting insights and summarize relevant files-helping you arrive ready to engage. [Learn more](https://support.microsoft.com/topic/prepare-for-your-meeting-with-copilot-f23326fc-7721-45f1-875e-23e77aaf3d89).

### SharePoint

- **Restricted access control enhancements** \[Web\]

  New enhancements for RAC policy for SharePoint administrators to restrict access to SharePoint sites including managing Microsoft 365 group connected sites with Microsoft 365 groups or Security groups. [Learn more](https://learn.microsoft.com/en-us/sharepoint/restricted-access-control).

### Viva Learning

- **AI & Copilot Resources provider availability to all Viva Learning users** \[Windows, Web, Teams\]

  The AI & Copilot Resources provider is now enabled by default for all Viva Learning users. Administrators now have the ability to manage the visibility of this provider within Viva Learning. [Learn more](https://learn.microsoft.com/en-us/viva/learning/ai-and-copilot-resources).
- **Copilot Academy availability to all Microsoft 365 users** \[Windows, Web, Teams\]

  Copilot Academy is now accessible to users without Copilot licenses. Admins now have the option to select their preferred access settings for Copilot Academy. [Learn more](https://learn.microsoft.com/en-us/viva/learning/academy-copilot).

### Word

- **Coach is now generally available across all markets and languages that Copilot currently supports** \[Web\]

  Coach is now generally available across all markets and languages that Copilot currently supports, ensuring a consistent experience for every user. [Learn more](https://support.microsoft.com/topic/use-coaching-to-review-content-in-word-for-the-web-fa09c055-d623-4d20-954f-9b064a5a7c80).
- **Reference a whole folder when prompting Copilot** \[Web\]

  Quickly attach a folder from OneDrive or SharePoint by typing a forward slash \(/\) or selecting the attach icon. Copilot now uses the 10 most recent files from your selected folder to streamline your document creation. [Learn more](https://techcommunity.microsoft.com/blog/microsoft365insiderblog/expanding-reference-capabilities-with-microsoft-365-copilot-in-word/4406054).
- **Replace your selection with generated content** \[Web, Mac, Windows\]

  Selecting the Replace button lets you instantly replace your selected text with content that was generated in Draft with Copilot.

## April 16, 2025

Updates released between April 2, 2025, and April 16, 2025.

### Excel

- **Access Copilot on-grid in Windows** \[Windows\]

  A Copilot icon appears right within your spreadsheet on Windows, giving you quick AI assistance as you work to keep your flow uninterrupted.
- **Graph-grounded chat** \[Windows, Mac, Web\]

  Ask Copilot in Excel for insights drawn from your chats, documents, meetings, and emails via Microsoft Graph-enhancing your workbook analysis with contextual organizational data. [Learn more](https://support.microsoft.com/topic/use-copilot-to-find-data-from-the-web-or-your-organization-and-add-it-in-excel-7a72fb29-e623-49e2-9f7d-38664b593054).
- **Use Copilot to search for answers from the web** \[Windows, Mac, Web\]

  In Excel, simply ask Copilot to search the web for answers and integrate the insights directly into your workbook, making data analysis even smoother. [Learn more](https://support.microsoft.com/topic/use-copilot-to-find-data-from-the-web-or-your-organization-and-add-it-in-excel-7a72fb29-e623-49e2-9f7d-38664b593054).

### Microsoft 365 admin center

- **AI Admin role has permissions to manage agents** \[Web\]

  As an AI Admin, you manage agents with various capabilities including creating and overseeing Copilot connections that index data in Graph and perform actions, controlling which makers can build these connections and regulating the data sources used, maintaining observability over all connections, approving or denying agents, pre-installing them without requiring consent, and viewing them in Microsoft 365 admin center integrated apps page.

### Microsoft 365 Copilot Chat

- **Get contextual suggestions during Copilot agent conversations** \[Windows, Web\]

  Speed up tasks with AI-driven prompts for next steps in Copilot Chat. See real-time suggestions to refine queries, dive deeper into topics, or resolve issues faster during agent interactions.
- **Support for longer prompts** \[Windows, Web\]

  Copilot Chat now supports larger inputs for smoother handling of extensive documents and data.

### Microsoft 365 Copilot extensibility

- **Discover agents for unlicensed and metered users** \[Windows, Web\]

  Empower more users with easy access to agents tailored to their needs-even if they are unlicensed or metered-broadening Copilot's reach across your organization. [Learn more](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/debugging-agents-copilot-studio).
- **Enable developer mode in Copilot Chat** \[Developer\]

  Leverage Microsoft 365 Copilot Chat developer mode directly within your development tools, simplifying the process to build and test custom integrations. [Learn more](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/debugging-agents-copilot-studio).

### OneNote

- **Copilot-powered organization in OneNote** \[Windows\]

  Transform a flat list of pages within a section to have an intuitive hierarchy. Ask Copilot in chat to organize your section and apply the update for a streamlined Notebook organization experience. [Learn more](https://support.microsoft.com/topic/organize-your-notes-with-copilot-in-onenote-f7d0477b-676c-4fa1-8c82-8900bb888618).

### PowerPoint

- **Copilot in PowerPoint has improved performance when summarizing your presentation** \[Web\]

  PowerPoint Copilot now updates its language models regularly to deliver faster summaries, helping you quickly review your presentation content.

### SharePoint

- **Author engaging web pages with Authoring** \[Web\]

  Combine the power of Large Language Models, your data in the Microsoft Graph, built-in or custom templates, and existing documents to create high-quality SharePoint pages while ensuring enterprise-level data security and privacy. [Learn more](https://techcommunity.microsoft.com/blog/spblog/create-pages-with-copilot-in-sharepoint/4394588).

## April 2, 2025

Updates released between March 20, 2025, and April 2, 2025.

### Copilot Studio

- **Enhanced SharePoint URL support in Copilot Studio** \[Web\]

  Previously, only SharePoint site URLs could be used as knowledge for Copilot Studio agents. Users can now use SharePoint file, folder, and site URLs, including links from the Share button or browser address bar; once the URLs are added, the agents will be grounded to the content within the URL. Additionally, more granular error messages help with transparency and managing expectations. [Learn more](https://learn.microsoft.com/en-us/microsoft-copilot-studio/knowledge-add-sharepoint).
- **Public website scoping for agents** \[Web\]

  Makers can now scope agents' knowledge sources to specific websites, enhancing the precision of web searches. This capability, previously available in custom agents from Microsoft Copilot Studio, is now extended to agents in the Microsoft 365 context. [Learn more](https://learn.microsoft.com/en-us/microsoft-365-copilot/extensibility/copilot-studio-agent-builder-build#add-knowledge-sources).
- **SharePoint knowledge for agents** \[Web\]

  Makers can now leverage additional data sources, including Dataverse and SharePoint, when building autonomous agents. This expands the variety of use cases for autonomous agents.
- **Use agent builder in Copilot chat** \[Web\]

  Create custom agents in Copilot chat to streamline repetitive tasks and achieve consistency. Use specific instructions and grounding details to save time, reuse your agents, and enhance team productivity. [Learn more](https://learn.microsoft.com/en-us/microsoft-365-copilot/extensibility/copilot-studio-agent-builder-build).

### Excel

- **Gain insights with Copilot and Python in Excel on Web** \[Web\]

  Using everyday language, ask Copilot to perform advanced analytics like machine learning and predictive forecasting, which would usually take hours or require special skills. Copilot writes Python code and inserts it on the grid, providing deeper insights and stunning/ visuals. Available in multiple languages on Excel for the Web.
- **Read aloud for Excel text responses** \[Web\]

  Users can now use the Read Aloud button on the Copilot response card to have an audio narration of the response, enhancing accessibility and ease of information consumption.

### Microsoft 365 admin center

- **View security information and certification evidence**

  Admins in Microsoft 365 Admin center can view the evidence of audits, and self-attestation to provide further confidence as to the certification, and compliance, of public apps and agents.

### Microsoft 365 Copilot Chat

- **Ask questions about images with natural language** \[Android, iOS, Web\]

  Easily gain insights from images by asking natural language questions. Upload images for quick analysis using advanced vision models-helping you make sense of visual data across your apps.
- **Enhance email insights with interactive hovers** \[Web\]

  Enjoy enriched emails with interactive hovers that reveal contextual details-like sender info, dates, and follow-up prompts-to streamline your daily workflow.

### Microsoft 365 Copilot Studio

- **Collect user feedback in Copilot Studio agent builder** \[Web\]

  Makers can also now submit feedback-compliments, problems, or suggestions-directly to the product team from inside the Microsoft 365 agent builder. This can be done at any stage of the authoring process, including comments and optional metadata for troubleshooting. This feature allows quick issue reporting without disrupting workflow and enables the product team to address feedback efficiently. [Learn more](https://learn.microsoft.com/en-us/power-apps/maker/canvas-apps/agent-builder#provide-feedback).

### Microsoft Loop

- **Load existing Copilot pages and create multiple pages** \[Web\]

  With multipage functionality in Copilot Pages, users can load existing pages and create multiple pages within a single conversation. [Learn more](https://support.microsoft.com/topic/add-copilot-chat-responses-to-multiple-pages-a5c40f74-55d0-4f1f-80d8-539ccc1a4bcb).
- **Recap changes over a longer time** \[Web\]

  Recap changes in Loop over extended periods, such as the last week or last 30 days, instead of being limited to the current session. This feature helps users share updates more effectively.

### PowerPoint

- **Translate your presentation** \[Windows, Web, Mac\]

  Produce a translated copy of your entire presentation in about 40 languages while preserving your slide design and structure, making global collaboration effortless. [Learn more](https://support.microsoft.com/topic/translate-your-presentation-with-copilot-2c622fca-daaf-457c-bc74-f3496cf44a85).

### Viva Engage

- **Questions surfacing in Copilot results**

  Viva Engage questions from communities, storyline, and Answers surface in Copilot results.

### Word

- **Narrate your ideas to Copilot** \[iOS\]

  Brainstorm out loud and let Copilot convert your voice notes into structured documents, making it easier to organize and develop your ideas.
- **Rewrite with Copilot** \[iOS\]

  Get suggestions from Copilot on how to rewrite any text, helping you improve clarity and style effortlessly.
- **Simplified prompt experience in chat** \[Web\]

  The chat experience in Word is now simplified with access to attachments, images, and agents now accessed from a single plus-sign menu.
- **Visualize as table** \[iOS\]

  Easily convert plain text into structured tables, helping you organize and present data more effectively in your daily work.

## March 19, 2025

Updates released between March 5, 2025, and March 19, 2025.

### Copilot Studio

- **Use generative actions** \[Web\]

  Replace manual topic triggers with AI-powered orchestration. You can now configure an agent to use generative AI to dynamically select relevant topics or plugin actions, creating more fluid conversations while reducing manual topic configuration. [Learn more](https://learn.microsoft.com/en-us/microsoft-copilot-studio/advanced-generative-actions).
- **Create automated copilots triggered by events** \[Web\]

  Automates routine tasks by triggering copilots on events like table updates, new documents, or incoming emails-minimizing manual effort and keeping processes running smoothly. [Learn more](https://learn.microsoft.com/en-us/microsoft-copilot-studio/authoring-triggers-about).

### Microsoft 365 admin center

- **Enhanced transparency for declarative agent metadata**

  Admins can now view granular metadata in the Microsoft 365 admin center-including data source details and custom actions-for declarative agents. This clarity enables more informed decisions on app availability and management across your organization.
- **Manage shared Copilot agents across your organization** \[Web\]

  Tenant admins can now view, search, and block shared Copilot agents in the admin center. Maintain control over agent usage and ensure compliance with organizational policies.

### Microsoft 365 Copilot app

- **View, edit and share Copilot Pages on mobile** \[Android, iOS\]

  Stay productive while on the go-use the Microsoft 365 mobile app to view, edit, or share Copilot-generated pages instantly. Collaborate with colleagues in real time, whether you're commuting or between meetings. [Learn more](https://support.microsoft.com/topic/introducing-microsoft-365-copilot-pages-6674bd51-9ff5-42c4-9256-44d9428a726f).

### Microsoft 365 Copilot Chat

- **Copilot on Edge Update** \[Web\]

  Copilot on Edge has been updated and requires users to update their version of Edge to version 134.0.3124.51 or newer to receive the latest functionality. This update includes file upload availability on the web tab and a smoother authentication experience via the Edge Work Profile.
- **Enhanced large file support in Copilot Chat**

  Work seamlessly with larger documents in Copilot Chat. You can now reference and interact with bigger files, such as lengthy reports or detailed presentations.
- **Prompt suggestions in Copilot chat** \[Windows, Web, Mac\]

  Get started in Copilot chat quickly with automatic prompt suggestions that enhance your productivity by providing relevant and context-aware prompts based on your previous interactions.

### Microsoft 365 Copilot extensibility

- **Support for message extension and declarative agents** \[Windows, Web\]

  Transform legacy plugins into integrated experiences by exposing them as declarative agents-enhance Office apps like Word, Excel, and PowerPoint with message extensions.

### Microsoft Loop

- **Track collaborative changes with "who did what and when"** \[Web\]

  Ask Copilot about recent edits in Loop workspaces to identify contributors, review timeline updates, and maintain clarity during team projects. Example: "Show changes to the onboarding checklist this week."

### OneNote

- **Support image input in OneNote chat** \[Windows\]

  Ask Copilot to analyze image input and organize your notebook pages by detecting themes and topics. Quickly group pages and update your Notebook structure with a simple click.

### Microsoft 365 Copilot

- **Share a Copilot prompt with a Teams team** \[Windows, Web\]

  Easily share custom prompts from the Copilot Prompt Gallery with your Microsoft Teams team. This streamlined sharing makes it simple for team members to discover and make the most of these prompts in their daily workflow. [Learn more](https://support.microsoft.com/topic/sharing-prompts-with-a-team-2fa7a228-8645-4dc4-beec-d75d6d0bc752?OCID=copilot_ongoingemail_feb25).

### SharePoint

- **Create and share agents** \[Web\]

  Easily create agents by selecting SharePoint sites or files and share them with your team in SharePoint or Teams to boost collaboration. [Learn more](https://techcommunity.microsoft.com/blog/microsoft365copilotblog/ignite-2024-sharepoint-agents-now-in-general-availability/4298746).
- **Use Data Access Governance to analyze tenant permissions** \[Web\]

  Leverage detailed reports on permissioned user counts and sharing links to identify oversharing risks and make informed governance decisions. [Learn more](https://learn.microsoft.com/en-us/sharepoint/data-access-governance-reports).

## March 4, 2025

Updates released between February 20, 2025, and March 4, 2025.

### Microsoft 365 Copilot Chat

- **Search archived mailboxes in Copilot Chat** \[Windows, Web, Android, iOS, Mac\]

  Leverage Copilot Chat to search emails across both primary and archived mailboxes by appending 'from my archives' or 'also look for emails in my archives' in your prompts to quickly locate key messages.
- **Support lockbox for GenAI** \[Web\]

  Lets you review and approve data access requests in real time-ensuring sensitive information is safeguarded during critical support interactions.
- **Enrichment of Messages in Copilot Chat** \[Web\]

  This feature enhances your communication experience by making it easier to understand and interact with your chat messages in Copilot Chat. With this feature, you will see cards and hoverable experiences that provide additional details of the chat without leaving your current view. This means you can quickly grasp the context of your conversations and find the information you need more efficiently.

### Copilot Studio

- **Add enterprise data with new graph connections** \[Web\]

  Connect your organization's data seamlessly using pre-configured graph connectors like Stack Overflow, and Salesforce Knowledge. Build smarter agents with semantic search-no custom solution required. [Learn more](https://learn.microsoft.com/en-us/microsoftsearch/salesforce-knowledge-connector).

### Microsoft 365 admin center

- **Enhanced Copilot admin page with comprehensive tools** \[Web\]

  Navigate a refreshed admin interface featuring Overview, Health, Discover, and Settings-delivering key metrics, insights, and controls to tailor Copilot to your organization's needs.
- **Simplify Copilot license assignment** \[Web\]

  Use a data-driven license optimizer to identify users who gain the most value from Copilot. Streamline assignments in the admin center for efficient adoption across your organization.

### Microsoft 365 Copilot app

- **View, edit and share Copilot Pages on mobile** \[iOS\]

  Stay productive no matter where you are. With mobile access to Copilot Pages, you can view, edit, and share content on the go, ensuring seamless collaboration with colleagues. [Learn more](https://support.microsoft.com/topic/introducing-microsoft-365-copilot-pages-6674bd51-9ff5-42c4-9256-44d9428a726f).

### Microsoft 365 Copilot extensibility

- **Simplified 1-page Graph Connector setup**

  Quickly set up external data connections with a single, simplified page for all Graph Connectors, reducing complexity and saving admin time. [Learn more](https://learn.microsoft.com/en-us/microsoftsearch/configure-connector).
- **Create Copilot agents with scoped web knowledge**

  Build customized Copilot agents that integrate up to four public web sites. Enhance functionality with targeted web knowledge for smarter, context-aware experiences. [Learn more](https://learn.microsoft.com/en-us/microsoft-365-copilot/extensibility/copilot-studio-agent-builder-build).

### PowerPoint

- **Add speaker notes to all slides with one command** \[Windows\]

  Speed up your presentation creation by having Copilot automatically add speaker notes to every slide, getting your narrative draft ready in a flash. [Learn more](https://support.microsoft.com/topic/add-speaker-notes-to-your-presentations-using-copilot-7139266b-8a1d-4056-8e30-4edcc4d80873).
- **Narrative builder creates slides with tables** \[Windows, Web, Mac\]

  Convert grounded content from Word documents into dynamic slides with tables. Enhance your presentations with structured, data-driven visuals effortlessly.

## February 19, 2025

Updates released between February 5, 2025, and February 19, 2025.

### Microsoft 365 Copilot Chat

- **Enhanced entity context card** \[Web\]

  Enjoy smoother motion, improved reliability, and a more intuitive experience with the upgraded entity context card-making it easier to explore contextual details as you work. [Learn more](https://support.microsoft.com/topic/using-context-iq-to-refer-to-specific-files-people-and-more-in-microsoft-365-copilot-272ac2c1-c5f7-49c9-8a42-2a8a87846fa0).
- **Increased results in Copilot Chat responses** \[Web\]

  Get more comprehensive email and calendar results in Copilot Chat responses to easily summarize messages or track your meetings throughout the day.

### Excel

- **Get powerful insights with python** \[Windows\]

  Explore your data naturally with advanced analysis that leverages Python-no expert coding needed to uncover trends and create dynamic visualizations.

### Microsoft Teams

- **AI-enabled file summaries on mobile** \[Android, iOS\]

  Summarize Word, PowerPoint, and PDF files on mobile by tapping the summary icon or selecting "Summarize with Copilot" for a quick, digestible overview-even on small screens.
- **Intelligent meeting recap for instant meetings \(premium\)** \[Windows, Mac\]

  Effortlessly browse meeting recordings by speaker and topic and access AI-generated notes, tasks, and mentions for instant meetings-empowering premium Copilot users with comprehensive insights. [Learn more](https://support.microsoft.com/office/meeting-recap-in-microsoft-teams-c2e3a0fe-504f-4b2c-bf85-504938f110ef).

### OneNote

- **Enhance note-taking with iterative content proposals** \[Windows\]

  Refine your notes on the fly by iterating prompts and reviewing alternate drafts, giving you a dynamic, customizable note-taking experience. [Learn more](https://support.microsoft.com/topic/take-notes-with-copilot-in-onenote-d5ddf33d-2bab-48de-9096-79df65f81207).
- **Take notes with Copilot directly in the flow from the canvas** \[Windows\]

  Seamlessly gather and create notes right on your page with Copilot integrated into your personal OneNote notebook, making in-flow note-taking more intuitive. [Learn more](https://support.microsoft.com/topic/take-notes-with-copilot-in-onenote-d5ddf33d-2bab-48de-9096-79df65f81207).

### PowerPoint

- **Create a presentation from a file-based prompt** \[Windows, Web, Mac\]

  Pull key facts and data from a selected file to shape your narrative. Simply provide Copilot with a prompt and quickly build your deck with relevant information. [Learn more](https://support.microsoft.com/office/create-a-new-presentation-with-copilot-in-powerpoint-3222ee03-f5a4-4d27-8642-9c387ab4854d).

### Viva Insights

- **Copilot dashboard for usage and retention insights** \[Windows, Web, Android, iOS, Mac\]

  Dive into usage frequency, compare top user groups, and track retention metrics-all in a single, comprehensive dashboard for actionable insights. [Learn more](https://learn.microsoft.com/en-us/viva/insights/org-team-insights/copilot-dashboard#interpreting-the-data).
- **Simplify analysis with advanced insights**

  Build queries quickly with Copilot's intelligent suggestions for relevant metrics, filters, and attributes, streamlining your data analysis process effortlessly. [Learn more](https://learn.microsoft.com/en-us/viva/insights/advanced/analyst/copilot-query).

### Word

- **Chat with Copilot about selected text** \[Windows, Web, Mac\]

  Highlight text, start a chat with Copilot, and receive responses tailored to what you've selected. Get targeted writing assistance and refine your content in real time.

## February 4, 2025

Updates released between January 24, 2025, and February 4, 2025.

### Microsoft 365 Clipchamp

- **Video creation in Copilot Visual Creator powered by Clipchamp** \[Web\]

  Type your prompt and Clipchamp writes a bespoke script, sources high-quality footage, and assembles a video project with music, voiceover, text overlays, and transitions. Open your draft in the Clipchamp app to continue editing, exporting, and sharing your video. [Learn more](https://techcommunity.microsoft.com/blog/microsoft_365blog/clipchamp-elevating-work-communication-with-seamless-video-creation-in-copilot/4375660).

### Microsoft 365 Copilot app

- **Updates to the Microsoft 365 \(Office\) app** \[Windows, Web, Android, iOS\]

  The Microsoft 365 Copilot app \(formerly Microsoft 365 app\) has a new name and icon. [Learn more](https://support.microsoft.com/office/the-microsoft-365-app-transition-to-the-microsoft-365-copilot-app-22eac811-08d6-4df3-92dd-77f193e354a5).

### Microsoft 365 Copilot Chat

- **Access support pages in Copilot Chat** \[Windows, Web, Android, iOS, Mac\]

  View organizational support pages directly within Copilot Chat, for quick help and guidance in your workflow.
- **Accommodate user's time zones in Copilot** \[Windows, Web, Android, iOS\]

  Copilot now references your local time zone when responding helping to avoid confusion and scheduling errors.
- **Charts, graphs, and data analysis in Copilot for Microsoft 365** \[Windows, Web\]

  Use natural language to create charts, graphs, and data analysis in Copilot Chat work mode.
- **Get more Copilot value with Microsoft 365 Copilot** \[Web\]

  Easily add full Copilot Chat capabilities including grounding conversations in work data and accessing Copilot in your favorite Microsoft 365 apps by purchasing or requesting a Microsoft 365 Copilot license directly in Copilot Chat. [Learn more](https://www.microsoft.com/microsoft-365/blog/2024/12/02/three-new-ways-small-and-medium-sized-businesses-can-purchase-microsoft-365-copilot).
- **Automatic session titles for easier organization** \[Web\]

  Let Copilot Chat generate smart, descriptive titles for your chat sessions, making it simpler to find and revisit important conversations.

### Excel

- **Entry point from the column header** \[Web\]

  Offers an intuitive option to access column tools directly from the header, speeding up your workflow in Excel.

### Microsoft Teams

- **Speaker recognition and attribution in BYOD rooms with Copilot** \[Windows, Mac\]

  Take advantage of speaker recognition and transcript attribution, unleashing new AI capabilities in any meeting space, whether or not it has a Teams Rooms system deployed. This feature identifies and attributes people in live transcripts, utilizing a unique voice profile for each participant enabling intelligent recaps and unlocking maximum value from Microsoft 365 Copilot in Teams meetings. Users can easily and securely enroll their voices via Teams Settings. This feature requires a Microsoft 365 Copilot or Teams Premium license for the user hosting the meeting for Copilot experiences and intelligent recaps, respectively. [Learn more](https://learn.microsoft.com/en-us/microsoftteams/rooms/voice-recognition).

### PowerPoint

- **Use Copilot to rewrite, trim, or formalize text** \[Web, Mac\]

  Transform your presentation text by letting Copilot fix grammar, shorten lengthy content, or adopt a more professional tone-perfect for crafting clear, polished slides.

### Microsoft 365 Copilot

- **Share a prompt with a co-worker** \[Windows, Web\]

  Easily create, save, and share your favorite prompts using Copilot Prompt Gallery, inspiring your co-workers to achieve more with Copilot. [Learn more](https://learn.microsoft.com/en-us/microsoft-365/copilot/copilot-prompt-gallery-export-prompts).

### SharePoint

- **Restricted Content Discovery** \[Web\]

  Prevent specific SharePoint sites from being discoverable in tenant-wide search and Copilot. [Learn more](https://learn.microsoft.com/en-us/sharepoint/restricted-content-discovery).

### Word

- **Browse cloud files with the file picker** \[Mac\]

  Use a file picker to browse your cloud directory and include relevant files without searching by name, making it easy to add key references to your draft.
- **Draft from selected text, lists, or tables** \[iOS\]

  Generate new content right where you work by selecting text, lists, or tables and tapping into Copilot's on-canvas menu. Quickly refine drafts and collaborate more interactively. [Learn more](https://techcommunity.microsoft.com/blog/microsoft365copilotblog/draft-with-copilot-in-word-on-a-selection-of-text-a-list-or-a-table/4191926).
- **Draft with Copilot** \[iOS\]

  Quickly produce paragraphs or entire sections for your documents, whether you're creating a brand-new file or adding to existing text. [Learn more](https://support.microsoft.com/office/draft-and-add-content-with-copilot-in-word-069c91f0-9e42-4c9a-bbce-fddf5d581541).
- **Reference data from the Microsoft cloud when drafting with Copilot in Word** \[Windows, Web, Mac\]

  Draft with Copilot now supports attaching rich content from the Microsoft cloud-including emails and meetings-resulting in more contextually relevant content. [Learn more](https://techcommunity.microsoft.com/blog/microsoft365copilotblog/what%E2%80%99s-new-in-microsoft-365-copilot-in-word-at-ignite-2024/4303448).
- **Reference plain text files in Copilot** \[Windows, Web, Mac\]

  Add .txt files as sources with Copilot in Word, streamlining your process when working with text-based research or background content.

## January 23, 2025

Updates released between January 8, 2025, and January 23, 2025.

### Forms

- **Smart reminders with Copilot in Forms** \[Web\]

  Copilot in Forms now offers smart reminders to help you monitor response progress and get more engagement with your forms, delivered right to your email inbox. [Learn more](https://support.microsoft.com/topic/smart-reminders-in-copilot-in-forms-d41f412f-f64a-4bee-b745-eebf58b7e036).

### Microsoft 365 Copilot Chat

- **Introducing Microsoft 365 Copilot Chat** \[Windows, Web, Android, iOS\]

  Microsoft 365 Copilot Chat-secure AI chat powered by GPT-4o with agents accessible right in chat, and IT controls including enterprise data protection and agent management. Copilot Chat serves as a powerful new on-ramp for everyone in your organization to build an AI habit. And it is included with your Microsoft 365 subscription. Get started with Copilot Chat with the updated [Microsoft 365 Copilot app](https://www.m365copilot.com) \(formerly Microsoft 365 app\). [Learn more](https://www.microsoft.com/microsoft-365/blog/2025/01/15/copilot-for-all-introducing-microsoft-365-copilot-chat).
- **Updated Copilot Chat responses UI** \[Windows\]

  Enjoy a more intuitive Copilot experience with streamlined message boundaries, refined message count alerts, and a clearly positioned security badge for higher trust and transparency.
- **Updated meeting entity card in Copilot Chat** \[Windows, Web\]

  Check meeting details like RSVP status, date, and attachments without switching contexts in Copilot Chat.
- **Copilot agents available in Copilot Chat web mode** \[Web\]

  In Copilot Chat web mode, discover and use Copilot agents available for your organization. Agents are custom grounded chats that include specific knowledge sources from work and web.
- **Disable file upload in Copilot Chat** \[Windows, Web\]

  Admins gain control to turn off file uploads for Copilot Chat, helping maintain compliance when sharing sensitive content.
- **Use Pages in compliant Copilot web chat** \[Android, Windows, iOS, Mac, Web\]

  Admins gain control to turn off file uploads for Copilot Chat, helping maintain compliance when sharing sensitive content.

### Microsoft 365 Copilot app

- **Control auto-start behavior on windows** \[Windows\]

  Adjust Windows settings to let users auto-launch the M365 app upon login, while giving admins the option to enforce group policy controls for enterprise needs.
- **Keep the app running in the background** \[Windows\]

  Enable the setting to keep the app active as a background process after closing, ensuring faster subsequent launches without a full reload.

### Microsoft 365 Copilot extensibility

- **Consistent user experience with developer-submitted plugins**

  Developer-submitted plugins \(ME, PPC, DV\) are promoted to agents seamlessly, ensuring a uniform user experience and simplifying plugin management.
- **Use agents in Copilot Chat Web mode**

  You can now access agents in the web-grounded Copilot Chat, enabling you to get access to additional sources of knowledge across both the work and web grounded experiences of Copilot Chat. [Learn more](https://support.microsoft.com/topic/get-started-with-agents-for-microsoft-365-copilot-169469d7-328d-4d37-9090-bfc2058a39bd).

### Microsoft 365 Copilot Studio

- **Enable makers to configure SharePoint as a knowledge source for agents** \[Web\]

  Empowers makers to connect SharePoint, giving agents a richer context for delivering accurate and relevant responses. [Learn more](https://learn.microsoft.com/en-us/microsoft-copilot-studio/authoring-review-activity).

### PowerPoint

- **Generate summaries for longer presentations** \[Windows, Web, Mac\]

  Copilot now supports text summaries up to 40k words \(around 150 slides\), giving you richer information and more polished layouts. [Learn more](https://support.microsoft.com/office/summarize-your-presentation-with-copilot-in-powerpoint-499e604c-4ab9-4f6a-9dbe-691cc87f2f69).
- **Listen to Copilot's responses with Read Aloud** \[Windows, Mac\]

  Hear Copilot's replies in the chat pane, letting you stay hands-free while reviewing your content.

### SharePoint

- **Copilot in SharePoint** \[Web\]

  Copilot in SharePoint combines the power of Large Language Models \(LLMs\), your data in the Microsoft Graph, and best practices to create engaging web content. Get assistance drafting your content when creating new pages. Adjust the tone, expand meeting bullets into structured text, or get help making your message more concise. All within our existing commitments to data security and privacy in the enterprise. [Learn more](https://support.microsoft.com/topic/write-with-copilot-in-sharepoint-rich-text-editor-afc720be-666b-4d87-801e-b8ff62f309bb).

### Microsoft Teams

- **Require explicit consent for meeting recording and transcription.**

  Manage meeting recording policies via the Teams admin center or PowerShell to require explicit participant consent before recording or transcription in ad-hoc meetings or group calls. When enabled and recording/transcription starts, all participants are muted with cameras and sharing turned off until they give explicit consent to be recorded and transcribed, ensuring a compliant meeting experience.

### Viva Amplify

- **Microsoft 365 Copilot in Viva Amplify editor** \[Web\]

  The superpowers of Microsoft 365 Copilot integrates seamlessly into Viva Amplify, transforming content creation. Use Copilot in Amplify to auto-rewrite for suggestions, expand or condense text, and adjust tone for consistent, relevant messaging. [Learn more](https://learn.microsoft.com/en-us/viva/amplify/copilot-in-viva-amplify).

### Viva Insights

- **Copilot dashboard access can be granted using Entra groups** \[Web\]

  Global admins can now grant Microsoft Copilot Dashboard access using Microsoft Entra ID \(AAD\) Groups, reducing the manual effort needed for management. [Learn more](https://learn.microsoft.com/en-us/viva/insights/org-team-insights/copilot-dashboard).
- **New Copilot adoption metrics and completing total actions taken** \[Windows, iOS, Mac\]

  This adds seven new Copilot adoption metrics to the Copilot dashboard and Viva Insights Advanced insights. It also updates the "total actions taken" metric in the Copilot dashboard to include these new Copilot adoption metrics. [Learn more](https://techcommunity.microsoft.com/blog/viva_insights_blog/new-microsoft-copilot-analytics-features-now-available-%E2%80%93-novemberdecember-2024/4356206).

### Word

- **Get started on a draft immediately with example prompts** \[Windows, Mac\]

  On blank documents, Copilot in Word offers one-click example prompts to help you get started quickly. [Learn more](https://techcommunity.microsoft.com/blog/microsoft365copilotblog/what%E2%80%99s-new-in-microsoft-365-copilot-in-word-at-ignite-2024/4303448).
- **Listen to Copilot's responses with Read Aloud** \[Windows, Web, Mac\]

  Hear Copilot's replies in the chat pane, letting you stay hands-free while reviewing your content.

## January 7, 2025

Updates released between December 18, 2024, and January 7, 2025.

### Microsoft 365 Copilot

- **Access Copilot Prompt Gallery in Word and PowerPoint mobile apps** \[Android, iOS\]

  Discover and use suggested Copilot prompts in Prompt Gallery within the Word and PowerPoint apps on iOS and Android. Enhance your productivity on the go with helpful AI suggestions.

### Microsoft 365 admin center

- **Track usage of Microsoft 365 Copilot Chat** \[Web\]

  Filter data by date range, review Microsoft Copilot usage by app entry point, and use these insights plan adoption strategies more confidently. [Learn more](https://learn.microsoft.com/en-us/microsoft-365/admin/activity-reports/microsoft-copilot-usage).

### Microsoft 365 Copilot extensibility

- **Include Code Interpreter in agents** \[Windows, Web\]

  Enhance your agents by including Code Interpreter for advanced data analysis tasks in agent builder. [Learn more](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/code-interpreter).

### OneNote

- **Use Copilot quick actions in OneNote: Rewrite, Summarize, and Create To-Dos** \[Windows\]

  Enhance your notes by using Copilot directly on the OneNote canvas. Instantly generate summaries, create to-do lists, or rewrite selected content within your notes. [Learn more](https://support.microsoft.com/office/rewrite-text-with-copilot-in-onenote-a33f14c9-b2f4-46b0-87b9-389690221610).

### Outlook

- **Schedule meetings with Copilot chat in Outlook** \[Windows, Web\]

  Save time and streamline your day by asking Copilot to schedule meetings for you in Outlook. Whether it's a 1:1 or focus time, Copilot will find the best available time slots with ease. [Learn more](https://support.microsoft.com/topic/8090e7b3-5b1d-4c6d-9b06-02edac062f58).
- **Switch between Work and Web grounding in Microsoft 365 Copilot Chat** \[Android, iOS\]

  In Outlook mobile apps, you can now toggle between Microsoft 365 Graph \(Work\) and Web grounding in Microsoft 365 Copilot Chat. Choose the grounding source that best suits your needs for more personalized assistance.

### Viva Amplify

- **Copilot in Viva Amplify editor** \[Web\]

  Experience the power of Copilot right in your Amplify editing workflow. You can quickly auto-rewrite sections of your text, expand or condense content to match your preferred length, and seamlessly adjust the tone-casual, engaging, or professional-to suit your audience. [Learn more](https://support.microsoft.com/topic/introduction-to-copilot-in-viva-amplify-768222a0-9b83-402f-861e-9f7691183368).

### Viva Insights

- **Expand your understanding of Copilot adoption with enhanced metrics** \[Windows, iOS, Mac\]

  Access seven new Copilot metrics and see them reflected in "total actions taken," helping you better track how teams use Copilot. [Learn more](https://learn.microsoft.com/en-us/viva/insights/advanced/analyst/templates/microsoft-365-copilot-adoption).
- **New metrics for enterprise data-protected prompts** \[Windows, Web, Android, iOS, Mac\]

  Gain visibility into prompts submitted through Microsoft 365 Copilot Chat \(web\) and enterprise data-protected Copilot scenarios. [Learn more](https://learn.microsoft.com/en-us/viva/insights/advanced/reference/metrics#microsoft-365-copilot-metrics).

### Viva Learning

- **Copilot Academy support for external content** \[Web\]

  Enhance your learning experience with a wider range of external content in Copilot Academy, including links to Copilot Prompt Gallery. [Learn more](https://learn.microsoft.com/en-us/viva/learning/academy-copilot).

## December 23, 2025

Updates released between December 10, 2025, and December 23, 2025.

### Microsoft 365 Copilot app

- **GPT-5 powers Copilot Chat by default** \[Android, Windows, iOS, Mac, Web\]

  Copilot Chat delivers faster, smarter results using GPT-5 as the default model.

  **Details:**

  **What Changed:** All Copilot Chat experiences run on GPT-5 by default. Copilot automatically routes prompts to the best-performing models for each task, using fast models for basic tasks and specialized reasoning models for multi-step requests.

  **Why:** Users want speed, accuracy, and minimal friction. This update helps to ensure consistent, high-quality AI interactions in Copilot Chat.

  **Try This:**

  - "Get me up to speed on the latest plans related to \[project/initiative\]. Help me think through what to do next."
  - "Use the attached spreadsheet with customer feedback to create a polished executive report that helps upper management decide where to prioritize resources in our next cycle."


  **Why this matters:**


  **Business Impact:** Increases accuracy and productivity, helping teams make strong decisions and complete complex work faster.


  **Personal Impact:** Removes friction by letting Copilot choose the best model--fast or reasoning--for the prompt.


  **Additional resources:**


  **Blogs:**


  [Available today: GPT-5 in Microsoft 365 Copilot](https://www.microsoft.com/microsoft-365/blog/2025/08/07/available-today-gpt-5-in-microsoft-365-copilot/?msockid=281b58ceea286c6226164ec5eb056dd6)

### Microsoft 365 Copilot Chat

- **Streamlined Copilot chat navigation with expanded history** \[Windows, Web\]

  A redesigned navigation pane provides a cleaner layout and expanded chat history, making it easier to switch between conversations. This allows you to switch between conversations and pick up where you left off, perfect for fast-paced projects and multitasking.

  **Roadmap ID:** [516570](https://www.microsoft.com/microsoft-365/roadmap?msockid=2484525e9a9b66d4330b47329bb667c9&filters=&searchterms=516570)

  **Details:**

  **What Changed:** The Copilot navigation pane highlights key agents, removes clutter, and expands visible chat history beyond the previous limit of five recent chats. Chat search is also more prominent for faster access to specific threads. This reduces interface clutter.

  **Why:** Users wanted an interface that feels organized and speeds up workflow. This redesign lets you quickly return to prior conversations without digging through menus.

  **Try This:**

  - Open the navigation pane in Copilot to see the improved design.
  - Search for a previous project conversation using the updated chat search bar.
  - Pin your most important chats to keep them accessible during critical work sessions.


  **Why this matters:**


  **Business Impact:** Standard, simplified navigation UI to help reduce downtime from searching old threads.


  **Personal Impact:** Enjoy a simpler, less cluttered workspace with easier access to past chats.

### Microsoft 365 Copilot extensibility

- **Upload Larger Files in Copilot Studio Agent Builder** \[Android, Windows, iOS, Web\]

  Agent Builder now supports file uploads up to 512 MB when creating agents, ideal for larger files.

  **Roadmap ID:** [500375](https://www.microsoft.com/microsoft-365/roadmap?msockid=2484525e9a9b66d4330b47329bb667c9&filters=&searchterms=500375)

  **Details:**

  **What Changed:** This increases the upload size limit in Agent Builder to 512 MB, enabling use of larger files as grounding data.

  **Why:** Users requested more flexibility for grounding agents. Larger files improve reduce the need to split or compress documents.

  **Try This:**

  - Drag and drop large documents such as training manuals into your agent project.
  - Create the agent and ask it to summarize information from uploaded files.


  **Why this matters:**


  **Business Impact:** Allows enterprises to build agents with richer, domain-specific knowledge.


  **Personal Impact:** Complete your work without the need to split files or compress data.


  **Additional resources:**


  **Learn:**


  [Embedded file content](https://learn.microsoft.com/en-us/microsoft-365-copilot/extensibility/agent-builder-add-knowledge#embedded-file-content)

### Microsoft 365 Copilot Studio

- **Build Copilot agents using organizational People data** \[Windows, Web\]

  Developers can build agents in Copilot Studio that deliver personalized, context-aware responses using organizational People data.

  **Details:**

  **What changed:** Added the ability for agent builders to access and use People data from your directory in responses.

  **Why:** Makes interactions more contextual and human-centric for better relevance.

  **Try This:**

  - Enable People data in Agent Builder
  - Create an agent to answer org-specific directory questions
  - Test in Microsoft Teams


  **Why this matters:**


  **Business Impact:** Improves accuracy and personalization in enterprise workflows.


  **Personal Impact:** Users get tailored answers courtesy of context-rich data.


  **Additional resources:**


  **Learn:**


  [Add knowledge sources to your declarative agent in Microsoft 365 Copilot](https://learn.microsoft.com/en-us/microsoft-365-copilot/extensibility/agent-builder-add-knowledge)

### PowerPoint

- **Use your organization's approved assets in Copilot presentations** \[Mac, Windows, Web\]

  Create branded PowerPoint slides by pulling images and templates from your company's SharePoint asset library or Templafy integration.

  **Roadmap ID:** [496366](https://www.microsoft.com/microsoft-365/roadmap?msockid=2484525e9a9b66d4330b47329bb667c9&filters=&searchterms=496366)

  **Details:**

  **What changed:** PowerPoint Copilot integrates with SharePoint Organization Asset Library and Templafy for approved, compliant visuals.

  **Why:** Ensures quality designs aligned with corporate branding guidelines.

  **Try This:**

  - Configure SharePoint OAL or Templafy in Microsoft 365
  - Ask Copilot: "Create a marketing update deck using brand imagery."


  **Why this matters:**


  **Business impact:** Maintains brand identity across all content.


  **Personal Impact:** Saves design time by eliminating manual asset searching.


  **Additional resources:**


  **Learn:**


  [Create an organization assets library](https://learn.microsoft.com/en-us/sharepoint/organization-assets-library)

### Word

- **Referenced sources cited in drafted content** \[Windows\]

  Draft content with confidence as Copilot automatically includes citations, referencing the information in your text. This feature ensures accuracy and credibility, saving time on manual citation.

  **Roadmap ID:** [380842](https://www.microsoft.com/microsoft-365/roadmap?msockid=2484525e9a9b66d4330b47329bb667c9&filters=&searchterms=380842)

  **Details:**

  **What changed:** Copilot in Word now automatically generates citations when incorporating external information into your drafts. This process highlights references directly within the text, eliminating the need for manual citation entry.

  **Why:** Proper attribution is vital for maintaining credibility and avoiding plagiarism. This enhancement simplifies the citation process, ensuring academic and professional integrity without added effort.

  **Try This:**

  - While drafting in Word, ask Copilot: "Include citations for referenced content."
  - Use Copilot commands to review the generated citations for completeness and accuracy.
  - Compare the citation style used with your preferred or required academic formatting.


  **Why this matters:**


  **Business Impact:** Enhances the reliability of professional documents by ensuring proper attribution without a complex citation process.


  **Personal Impact:** Save time creating references, allowing more focus on content quality and creativity.

## November 25, 2025

Updates released between November 12, 2025, and November 25, 2025.

### Microsoft 365 admin center

- **Reassign agent ownership with full control** \[Windows, Web\]

  Admins can now transfer ownership of shared agents, granting the new owner full edit and delete permissions and revoking all access from the previous owner.

  ****Roadmap ID:**** [502867](https://www.microsoft.com/microsoft-365/roadmap?msockid=2484525e9a9b66d4330b47329bb667c9&filters=&searchterms=502867)

  ****Details:****

  **What changed:** Ownership reassignment capabilities are now live in Microsoft 365 admin center, with edits propagating to agent files and associated content.

  ****Why:**** Helps maintain governance when employees leave roles or teams without disrupting workflows.

  **Try this:**

  - From admin center, select a shared agent > choose **Reassign Owner** > confirm access update.


  **Why this matters:**


  **Business Impact:** Reduces compliance and business continuity risks during staff transitions.


  **Personal Impact:** Admins can easily manage lifecycle changes without escalating to engineering teams.


  **Additional resources:**


  **Learn:**


  [Reassign an agent's owner with PowerShell](https://learn.microsoft.com/en-us/power-platform/release-plan/2025wave2/microsoft-copilot-studio/reassign-agents-owner-powershell)

### Microsoft 365 Copilot Chat

- **Access shared mailboxes in Copilot Chat** \[Android, Windows, iOS, Mac, Web\]

  Copilot Chat now connects to shared mailboxes, so team-based conversations are more informed and collaborative.

  ****Roadmap ID:**** [488797](https://www.microsoft.com/microsoft-365/roadmap?msockid=2484525e9a9b66d4330b47329bb667c9&filters=&searchterms=488797)

  ****Details:****

  **What changed:** Users with shared mailbox permissions can ground Copilot responses in shared mail content, just like their own emails.

  ****Why:**** Eliminates context gaps in team workflows and improves shared visibility on projects.

  **Try this:**

  - Tell Copilot: *"Summarize recent emails in [mailbox@domain.com](mailto:mailbox@domain.com) mailbox."*
  - Tell Copilot: *"List all the emails around `topic` from < mailbox@domain.com > mailbox."*


  **Why this matters:**


  **Business Impact:** Ensures customer responses or project updates aren't missed when responsibility spans multiple team members.


  **Personal Impact:** Reduces copying and manual email checks across shared accounts-Copilot does it for you.


  **Additional resources:**


  [Use Copilot in shared mailboxes and delegate mailboxes](https://support.microsoft.com/topic/use-copilot-in-shared-mailboxes-and-delegate-mailboxes-3e7e5130-eabe-4c19-94ea-117b2a4c14d6)

- **Find files faster with improved Copilot Chat filters** \[Windows, Web\]

  Use new file type and people refiners in Copilot Chat to quickly get to the right file without sifting through results.

  ****Roadmap ID:**** [481136](https://www.microsoft.com/microsoft-365/roadmap?filters=&searchterms=481136)

  ****Details:****

  **What changed:** Introduced filters for file types and collaborators in Copilot Chat's CIQ Files tab.

  ****Why:**** Cuts down time spent filtering manually, especially in large file repositories.

  **Try this:**

  - In chat, search: *"Quarterly report"* → Filter by **Excel** and collaborator name.


  **Why this matters:**


  **Business Impact:** Improves productivity and reduces meeting prep time.


  **Personal Impact:** Less frustration-find what you need in seconds.

- **Talk to Copilot with voice for faster hands-free work** \[Android, Windows, iOS, Mac, Web\]

  Speak to Copilot naturally on mobile or desktop to prepare for meetings, brainstorm ideas, or catch up on work-hands-free and grounded in work data.

  **Roadmap ID:** [481138](https://www.microsoft.com/microsoft-365/roadmap?msockid=2484525e9a9b66d4330b47329bb667c9&filters=&searchterms=481138)

  ****Details:****

  **What changed:** Copilot now supports voice input, enabling natural, conversational interactions in the Microsoft 365 Copilot app on mobile, desktop and the web and across Microsoft 365 apps, starting with Outlook, Word and PowerPoint.

  ****Why:**** Professionals need faster, more intuitive ways to engage with AI during their flow of work, especially when multitasking or on the move.

  **Try this:**

  - Say: *"Confirm the agenda and attendee list for my next meeting"*.
  - Try: *"Create a quick list of next steps from my recent meeting notes."*
  - Ask: *"Summarize this document in five key points."*


  **Why this Matters:**


  **Business Impact:** Voice drives productivity and inclusivity through natural interactions that increase engagement, accelerate task completion and reduce downtime.


  **Personal Impact:** Work more comfortably and naturally while saving time, gaining efficiency and giving you the flexibility to use Copilot on the go or at your desk.


  **Additional resources:**


  [Get started with voice features in Microsoft 365 Copilot](https://support.microsoft.com/topic/get-started-with-voice-features-in-microsoft-365-copilot-9262968d-565e-470c-a04b-991eb8e0d1ea)

### Microsoft 365 Copilot extensibility

- **Enhanced search in Agent Store for easier discovery** \[Windows, Web\]

  Finding the right agents in the Copilot Agent Store just got faster and smarter. Enjoy a streamlined search experience with typeahead suggestions and a clean results page-making it simple to locate exactly what you need without wasted time.

  ****Roadmap ID:**** [502617](https://www.microsoft.com/microsoft-365/roadmap?filters=&searchterms=502617)

  ****Details:****

  **What changed:** The Agent Store now includes enhanced search capabilities featuring a responsive drop-down menu, typeahead functionality for quick suggestions as you type, and a dedicated search results page for improved clarity.

  ****Why:**** Customers need a quicker, more intuitive way to explore and find agents. By reducing friction in discovery, you can deploy and extend Copilot solutions with less effort and greater confidence.

  **Try this:**

  - Start typing an agent name in the search bar to see type-ahead suggestions instantly.
  - Use the new full results page for a complete view of matching agents.


  **Why this matters:**


  **Business Impact:** Accelerate adoption by making it easy for teams to find and integrate the right Copilot tools quickly, boosting productivity across the organization.


  **Personal Impact:** Save time and reduce frustration with simple, intuitive search that helps you get back to meaningful work faster.

- **Unified permissions management for agents** \[Windows, Web\]

  View detailed permissions for each Copilot agent in one place-including app dependencies, delegated permissions, and associated risks. Admins can grant consent directly, simplifying governance and deployment.

  ****Roadmap ID:**** [502617](https://www.microsoft.com/microsoft-365/roadmap?filters=&searchterms=502617)

  ****Details:****

  **What changed:** Unified Permissions Management now provides a clear view of all required applications, delegated permissions, and associated risk levels from a central console.

  ****Why:**** Helps admins ensure security and compliance while reducing friction in agent approval workflows.

  **Try this:**

  - Go to the Permissions tab in Microsoft 365 admin center to review and approve agent permissions.
  - Filter by risk level to prioritize oversight where needed.


  **Why This Matters:**


  **Business Impact:** Strengthens compliance and governance while accelerating agent deployment.


  **Personal Impact:** Simplifies decision-making for IT teams, saving hours of manual checks.


  **Additional resources:**


  **Learn:**


  [Agent Registry in the Microsoft 365 admin center](https://learn.microsoft.com/en-us/microsoft-365/admin/manage/agent-registry)

### Microsoft 365 PowerPoint

- **Reference Loop or Page in presentations** \[Mac, Windows, Web\]

  When building a presentation with Copilot, you can now pull in content from Loop components or pages for fully integrated and up-to-date slides.

  ****Roadmap ID:**** [500864](https://www.microsoft.com/microsoft-365/roadmap?msockid=2484525e9a9b66d4330b47329bb667c9&filters=&searchterms=500864)

  ****Details:****

  **What changed:** Copilot for PowerPoint supports referencing Loop components and pages across PC, Mac, and web.

  ****Why:**** Ensures your presentations reflect the latest collaborative content without manual copy-paste.

  **Try this:**

  - **Ask Copilot:** *"Create a status update deck using the project details from our Loop page."*


  **Why this matters:**


  **Business Impact:** Align updates across teams without tedious content migration.


  **Personal Impact:** Save time by reusing the content you already co-created, in just one step.

## November 12, 2025

Updates released between October 28, 2025, and November 12, 2025.

### Excel

- **Build and analyze surveys with ease using Surveys Agent** \[Windows, Mac, Web\]

  Let Surveys Agent handle the heavy lifting-from writing questions to launching surveys and breaking down results. It's like having a professional researcher inside Copilot, helping you make quick, data-driven decisions. [Learn more](https://aka.ms/SurveysAgentAvailable).

### Microsoft 365 Copilot Chat

- **RSVP status-based meeting search in Copilot Chat** \[Android, Windows, Web\]

  **Roadmap:** [499429](https://www.microsoft.com/microsoft-365/roadmap?filters=&searchterms=499429)

  Quickly find meetings based on RSVP status-either your own or others'. This feature helps you stay organized by surfacing RSVP details for upcoming events, so you can track commitments and follow up with attendees.

  **Try this:**

  Open Microsoft 365 Chat. Enter queries like:

  - "Meetings I accepted this week"
  - "Meetings I have not RSVPed this week"
  - "Who all have accepted the Scrum meeting?"


  View results showing RSVP details for yourself or attendees.


  **Business or Personal Impact:**


  **Business:** Improves meeting management and accountability by enabling quick visibility into attendee responses, reducing missed follow-ups.


  **Personal:** Helps you stay on top of your schedule and commitments without manually checking each calendar invite.

- **Iterate on images with multi-turn editing** \[Windows, Mac, Web\]

  Copilot Chat now makes visual creation more flexible and intuitive. Upload reference images, edit them step by step, and maintain consistency across versions-perfect for refining designs for presentations, social posts, or print.

### PowerPoint

- **Create new presentations without overwriting your original** \[Windows, Mac, Web\]

  When you use Copilot to generate a presentation from an existing one, it now creates a separate file-keeping your original content safe for future use. Perfect for creating tailored decks without starting from scratch. [Learn more](https://support.microsoft.com/office/create-a-new-presentation-with-copilot-in-powerpoint-3222ee03-f5a4-4d27-8642-9c387ab4854d).

### Viva Insights

- **Copilot Chat \(Web\) in Teams & Outlook metrics** \[Windows, Web\]

  Copilot Analytics users can now view metrics about their Copilot Chat \(Web\) usage in Teams and Outlook. These updates enable users to better understand both active usage and action counts in Teams and Outlook and will be available in the Copilot Dashboard, as well as with additional query support. [Learn more](https://learn.microsoft.com/en-us/viva/insights/advanced/reference/metrics).

## October 28, 2025

Updates released between October 15, 2025, and October 28, 2025.

### Copilot extensibility

- **Static tab for custom agents in Teams meetings** \[Windows, Web\]

  Developers can now add static tabs in their custom engine agents using Teams Toolkit, enhancing experiences during meetings and calls.

### Microsoft Planner

- **Get a project manager agent in all premium plans",** \[Windows, Web\]

  The project manager agent is now included in all premium Planner plans. It helps you move work forward by creating plans from goals, executing tasks, and acting on feedback-all with less manual effort.

### Outlook

- **Expanded coverage and Improvements to Preparing for Meetings with Copilot** \[Windows, Web\]

  Preparing for meetings can be time and effort-intensive. New enhancements to Copilot's meeting preparation experience help streamline the process. Directly within the Outlook meeting event form, Copilot can now proactively generate key insights to help you prepare for specific meetings. Copilot also suggests additional ways that it can help you prepare, from finding the pre-reads to learning more about the meeting's intended outcome. User can then continue the conversation via chat, and get answers to additional questions that are top-of-mind. In addition, Copilot now supports all meeting types - including 1:1 meetings - via the meeting preparation experience. [Learn more](https://support.microsoft.com/topic/prepare-for-your-meeting-with-copilot-f23326fc-7721-45f1-875e-23e77aaf3d89).

### Teams

- **Use Copilot in a call without recording or transcribing** \[Windows, Mac\]

  Now, users can benefit from Copilot during live Teams calls with sensitive conversations where a persistent record is not desired. When the admin enables this option, users can initiate Copilot without transcription or recording simply through clicking the Copilot button in the header menu, so they can use important Copilot administrative tasks such as capturing key points, task owners, and next steps, enabling participants to stay focused on the content of the call. [Learn more](https://learn.microsoft.com/en-us/microsoftteams/copilot-teams-calling-transcription#only-during-the-call).

### Viva Insights

- **Weekly user insights in Copilot Studio agent reports",** \[Windows, Mac, Web\]

  Copilot Studio reports now include weekly active user counts and provide aggregated data on a weekly basis for consistency across reporting. These updates make it easier to track engagement trends for planning and adoption.", [Learn more](https://learn.microsoft.com/en-us/viva/insights/advanced/analyst/templates/copilot-studio-agents).

## October 15, 2025

Updates released between September 30, 2025, and October 15, 2025.

### Copilot extensibility

- **Context-aware search ranking** \[Windows, Web\]

  Search now delivers more personalized results by using user context and engagement signals, enhanced by the Microsoft 365 Copilot extension. This ensures that search results are intuitive and relevant. [Learn more](https://learn.microsoft.com/en-us/microsoftsearch/crossover-browser).

### Microsoft 365 Copilot Chat

- **Create new images using reference uploads** \[Windows, Mac, Web\]

  Enhance image creation by uploading reference images in Copilot Chat, using them as creative foundations for new visuals.
- **Image generation with multiple aspect ratios** \[Windows, Mac, Web\]

  Generate images in various aspect ratios to suit any need, from social media to presentations, with landscape, portrait, and square options in Copilot Chat.

## September 30, 2025

Updates released between September 16, 2025, and September 30, 2025.

### Microsoft 365 admin center

- **Usage reports for Copilot search** \[Android, Windows, iOS, Mac, Web\]

  Administrators gain insights into organizational adoption of Copilot search with new usage reports. Track total search queries, assess trends, and analyze user activity to drive effective adoption strategies. [Learn more](https://learn.microsoft.com/en-us/microsoft-365/admin/activity-reports/microsoft-365-copilot-search-usage).

### Microsoft 365 Copilot Chat

- **Copilot Chat now understands attached files like Word, Excel, PowerPoint, PDF, Text, JSON, and XML.** \[Android, Windows, iOS, Mac, Web\]

  Users can gather insights not only from the email content but also from attached files, enabling comprehensive context understanding.
- **Easily select meeting series in Copilot Chat** \[Windows, Web\]

  Effortlessly choose meeting series and related instances directly from the Context IQ \(CIQ\) menu to include in your Copilot Chat prompts.
- **Support for analyzing images in uploaded files** \[Windows, Web\]

  Analyze embedded images within PDF, DOCX, and PPTX files uploaded to Copilot. Ask Copilot to interpret image content, such as "analyze the image on page 4," and receive insights based on the visual data.

### Outlook

- **Highlight and rewrite email drafts with Copilot** \[Windows\]

  In classic Outlook for Windows, select parts of your email draft and use Copilot to rewrite with precision. Modify tone and length according to your needs, optimizing communication.

### PowerPoint

- **Seamlessly add topics with Copilot** \[Mac, Web, Windows\]

  Enhance your presentations by adding new topics with slides via Copilot, ensuring consistency in look and feel with existing content. [Learn more](https://support.microsoft.com/topic/add-topics-to-your-existing-powerpoint-presentation-with-copilot-7439e3d7-5b7f-4886-8d01-5e7f285fd99b?preview=true).

## September 16, 2025

Updates released between September 3, 2025, and September 16, 2025.

### Copilot extensibility

- **Improve Response accuracy when handling large files in File Upload/CIQ.** \[Windows, Web\]

  Experience improved summaries and increased accuracy when querying long documents and PDFs. Copilot efficiently distills information, helping you extract insights and answer questions faster.
- **ServiceNow Connectors custom URL configuration** \[Windows, Web\]

  Enhance ServiceNow Connectors with customizable URLs for articles, tickets, and catalog items, tailored to organizational preferences. [Learn more](https://learn.microsoft.com/en-us/microsoftsearch/configure-connector#customize-values-for-certain-schema-properties).

### Microsoft 365 admin center

- **Admins can easily manage orphaned agents with comprehensive lifecycle functionality** \[Windows, Web\]

  Admins can effectively manage the lifecycle of ownerless agents. They can easily filter, identify, block, or delete agents that are no longer associated with an owner, ensuring a streamlined and efficient workflow.

### Microsoft 365 Copilot app

- **Microsoft 365 Copilot Search** \[Android, Windows, iOS, Web\]

  Copilot Search is the intelligent search experience within the Microsoft 365 Copilot app, designed to deliver fast, secure, and context-aware results across your organization's data. It enables users to search across emails, files, chats, meetings, and even third-party platforms like Salesforce, Jira, and Confluence using natural language queries. [Learn more](https://learn.microsoft.com/en-us/microsoft-365/copilot/microsoft-365-copilot-search).

### OneNote

- **Create and use Copilot Notebooks in OneNote** \[Windows\]

  Bring together your notes, Word documents, Excel files, PowerPoint decks, Copilot chats and more into Copilot Notebooks in OneNote to organize and reason over your content. [Learn more](https://support.microsoft.com/topic/introducing-microsoft-365-copilot-notebooks-in-onenote-c91a851a-77d6-4b70-a898-8aaf718a95df).

## September 3, 2025

Updates released between August 19, 2025, and September 3, 2025.

### Copilot extensibility

- **Add advanced scripting support for ServiceNow catalog** \[Windows, Web\]

  Use advanced scripting for user permissions with the ServiceNow Catalog Graph Connector, allowing more customized and secure experiences. [Learn more](https://learn.microsoft.com/en-us/microsoftsearch/servicenow-catalog-advanced-flow).
- **Get clear sync statuses and error insights** \[Windows, Web\]

  View actionable user sync and ingestion statuses across all states in Microsoft admin center to simplify troubleshooting. [Learn more](https://learn.microsoft.com/en-us/microsoftsearch/connector-view-details).
- **Ground Copilot responses on specific content subsets** \[Windows, Web\]

  Increase precision with Copilot extensibility by using subsets of data connections, ensuring responses are based on the most relevant information. [Learn more](https://learn.microsoft.com/en-us/microsoft-365-copilot/extensibility/copilot-studio-agent-builder-knowledge?branch=main&branchFallbackFrom=pr-en-us-1060).
- **Search and browse connector catalog with ease** \[Windows, Web\]

  Admins can now quickly find connectors across categories and functions in the Copilot extensibility catalogâ€"making integrations simpler than ever. [Learn more](https://learn.microsoft.com/en-us/microsoftsearch/connector-view-details).

### Excel

- **Copilot-generated formula in one step** \[Windows\]

  Just tell Copilot what you need, and it creates the formula and places it directly into the selected cell-quick and easy. [Learn more](https://support.microsoft.com/topic/generate-single-cell-formulas-with-copilot-in-excel-2d0201f3-0c3f-41b8-b0b0-07da3ad8fb29).
- **Copilot-generated single cell formula in one step** \[Windows\]

  Copilot can generate a complete formula based on your prompt and place it directly into the selected cell-quick and easy. [Learn more](https://support.microsoft.com/topic/generate-single-cell-formulas-with-copilot-in-excel-2d0201f3-0c3f-41b8-b0b0-07da3ad8fb29).

### Microsoft 365 Copilot Chat

- **View web queries used by Copilot for greater transparency** \[web, Windows\]

  See the exact web queries Copilot sends in response to your prompts, along with the list of websites queried, enhancing your awareness and control over the information process.

### Outlook

- **Copilot Chat Sidebar in Classic Outlook for Windows** \[Windows\]

  A new sidebar for Copilot Chat is available in classic Outlook for Windows, letting you chat with Copilot in the context of the content you're reading or writing. [Learn more](https://learn.microsoft.com/en-us/copilot/manage).

### PowerPoint

- **Excel data when building a presentation** \[Web, Mac, Windows\]

  You can now reference an Excel file when you create a presentation with Copilot within the PowerPoint application. [Learn more](https://support.microsoft.com/office/create-a-new-presentation-with-copilot-in-powerpoint-3222ee03-f5a4-4d27-8642-9c387ab4854d).

## August 19, 2025

Updates released between August 5, 2025, and August 19, 2025.

### Copilot extensibility

- **Craft actions using API chaining with low code** \[Windows, Web\]

  Makers can leverage low code and pro-code options to create actions with API chaining, enabling bulk actions and adaptive card contexts for streamlined processes. [Learn more](https://learn.microsoft.com/en-us/microsoft-365-copilot/extensibility/instructions-api-plugins).
- **Create simplified multi-step workflows** \[Windows, Web\]

  Streamline your tasks with an embedded builder that allows users to design and manage multi-step workflows effortlessly, enhancing productivity. [Learn more](https://learn.microsoft.com/en-us/microsoft-365-copilot/extensibility/declarative-agent-instructions).
- **Customize Copilot with Declarative Agents** \[Windows\]

  End-users can now tailor Copilot's capabilities with Declarative Agents, adding new knowledge and skills for enhanced functionality. [Learn more](https://learn.microsoft.com/en-us/microsoft-365-copilot/extensibility/overview-declarative-agent).
- **Discover custom extensions for Copilot** \[Windows, Web\]

  Find and deploy customizable extensions \(CEAs\) for Copilot directly from the Store, enhancing the capabilities of your workflow with ease.
- **Integrate declarative agents into Excel** \[Windows, Web\]

  Users can now seamlessly integrate and leverage declarative Copilot agents directly within Excel, enhancing data interaction and task automation. [Learn more](https://learn.microsoft.com/en-us/microsoft-365-copilot/extensibility/overview-declarative-agent).
- **Regulate knowledge source with governance tools** \[Windows, Web\]

  Admins can now oversee and manage agents with uploaded files as their knowledge source, utilizing tools for agent filtering, reviewing sensitivity labels, and managing metadata.
- **See authors and descriptions in every agent interaction** \[Windows, Web\]

  Build trust and transparency by viewing the author name and agent description in each interaction, enhancing user confidence in responses.

### Microsoft 365 Copilot app

- **Expanded language options with Microsoft 365 Copilot** \[Android, Windows, iOS, Mac, Web\]

  Microsoft 365 Copilot now supports six additional languages: Albanian, Filipino, Icelandic, Malay, Maltese, and Serbian \(Cyrillic\). [Learn more](https://support.microsoft.com/office/supported-languages-for-microsoft-365-copilot-94518d61-644b-4118-9492-617eea4801d8).

### Microsoft 365 Copilot Chat

- **Expanded file search capabilities in Copilot Chat** \[Windows, Web\]

  Copilot Chat now supports a wider range of file types in SharePoint and OneDrive, enhancing search and information retrieval. [Learn more](https://support.microsoft.com/topic/file-formats-supported-by-microsoft-365-copilot-1afb9a70-2232-4753-85c2-602c422af3a8).

### Outlook

- **Summarize email attachments with Copilot** \[Android, Windows, iOS, Mac, Web\]

  Summarize PDF, Word, and PPT email attachments effortlessly in Outlook Web and the new Outlook for Windows, making it easier to extract key information without needing to open each file. [Learn more](https://support.microsoft.com/office/summarize-an-email-thread-with-copilot-in-outlook-a79873f2-396b-46dc-b852-7fe5947ab640#id0ebbj=new_outlook).

### Viva Insights

- **Bridge skill gaps with personalized insights** \[Windows, Web\]

  Discover and promote upskilling opportunities with People Skills. Share skills, connect with others, and enrich user experiences across Microsoft 365, including apps such as Copilot and Viva Learning. [Learn more](https://learn.microsoft.com/en-us/microsoft-365/copilot/people-skills-overview).

## August 5, 2025

Updates released between July 22, 2025, and August 5, 2025.

### Copilot extensibility

- **Enhance agent builder with full screen mode** \[Windows, Mac, Web\]

  Enjoy an improved agent builder experience with a full-screen view that streamlines the process of creating and managing your agents. [Learn more](https://learn.microsoft.com/en-us/microsoft-365-copilot/extensibility/copilot-studio-agent-builder-build).
- **Enhanced Q&A accuracy for SharePoint files** \[Windows, Web\]

  Improve the precision of Q&A interactions on SharePoint files that include tables, comments, and formatting. Benefit from more relevant and insightful responses whether you're working with Word, PDF, or PowerPoint files.
- **Get relevant calendar results by time period** \[Windows, Web\]

  Quickly summarize meetings for a specific day to stay on top of your schedule and focus on the events that matter most.
- **Improve email responses with extra context** \[Windows, Web\]

  Get fuller email replies that expand your initial lists, indicate the number of related messages, and let you easily paginate for more details-all to help you manage your inbox more effectively. [Learn more](https://support.microsoft.com/topic/schedule-copilot-prompts-29dfd5fb-211a-4515-88a6-730b8074e489).
- **Schedule meetings with smart time insights** \[Windows, Web\]

  Easily discover optimal meeting times and streamline Outlook handoffs with intelligent calendar suggestions that make scheduling a breeze. [Learn more](https://support.microsoft.com/office/how-do-i-use-the-the-scheduling-assistant-to-find-meeting-times-bdd6c165-4186-45f1-ad9e-5af067ac69a3).

### Copilot Studio

- **Only use grounded knowledge for agent response** \[Windows, Web\]

  Prevent agents from using model-trained knowledge by turning off internal knowledge, ensuring responses are based on specified grounded sources. [Learn more](https://learn.microsoft.com/en-us/microsoft-365-copilot/extensibility/copilot-studio-agent-builder-knowledge#prioritize-your-knowledge-sources-over-general-knowledge).

### Microsoft 365 Copilot app

- **Ask Microsoft 365 Copilot for insights using Click to Do** \[Windows\]

  Streamline your workflow by seamlessly sharing highlighted content with Microsoft 365 Copilot using Click to Do for quick insights and assistance. [Learn more](https://learn.microsoft.com/en-us/windows/client-management/manage-click-to-do).
- **Start an instant chat with Copilot** \[Windows\]

  Launch a chat with Copilot quickly using the quick view for instant assistance. Use the Win+C shortcut or the Copilot key on supported devices.

### Microsoft 365 Copilot Chat

- **Share agents with your enterprise** \[Windows, Web\]

  Generate sharing links for your agents in Business Chat. If the recipient doesn't have the agent, they are directed to the Microsoft 365 application catalog to install it. If they do, the agent opens directly in Microsoft 365 Copilot Business Chat. [Learn more](https://support.microsoft.com/topic/how-to-share-your-agent-44981c08-ab64-43f1-bcf8-ebadfc5469cc).

### PowerPoint

- **Copilot uses enterprise assets hosted on SharePoint OAL when creating presentations now** \[Mac, Windows, Web\]

  Once you integrate your organization's assets into a Sharepoint OAL \(Organization Asset Library\) you will be able to create presentations with your organization's image. [Learn more](https://learn.microsoft.com/en-us/sharepoint/connect-organizational-asset-libraries-to-copilot).
- **Copilot uses Enterprise assets hosted on Templafy when creating presentations now** \[Mac, Windows, Web\]

  Once you connect your asset library hosted with Templafy to Microsoft365 and Copilot, you will be able to create presentations with your organization's images. [Learn more](https://learn.microsoft.com/en-us/sharepoint/connect-organizational-asset-libraries-to-copilot).

### Teams

- **Ability to Stop Copilot while it is generating a response** \[Windows\]

  Copilot in Teams now has a 'stop' button after sending a prompt. This allows the user to stop Copilot's response either before the response has started to generate, or even after the response is generating. The user can then start a new prompt if they wish.
- **Interpreter agent for seamless communication** \[Windows, Mac\]

  Interpreter Agent acts like an instant translator during your Teams meetings. It listens to the spoken language in a meeting and immediately translates it into another language in real-time. This allows participants who speak different languages to understand each other and collaborate more effectively without waiting. Whether you're holding a business meeting, customer calls, or project discussions, the AI interpreter in Teams ensures everyone can participate fully, enhancing communication and productivity across diverse teams. It supports 9 different languages: English, Italian, German, French, Portuguese \(Brazil\), Japanese, Spanish, Chinese \(Mandarin\), and Korean. [Learn more](https://support.microsoft.com/office/interpreter-in-microsoft-teams-meetings-c7efe2bb-535d-42ab-a5c4-d2d91619b46d).
- **Translated Intelligent meeting recap for multilingual meetings \(Copilot and Teams Premium\)** \[Windows, Mac\]

  Now, intelligent meeting recap supports multilingual meetings, ensuring you can easily catch up on key discussions even when multiple languages were spoken. After the meeting, your recap is automatically generated in the translation language you selected for live transcription and captions. [Learn more](https://support.microsoft.com/office/recap-in-microsoft-teams-c2e3a0fe-504f-4b2c-bf85-504938f110ef).

### Word

- **Kickstart your document with contextual prompts** \[Windows\]

  Copilot suggests prompts by including files and meetings based on your recent activity, helping you draft a new document in Word seamlessly.

## July 22, 2025

Updates released between July 8, 2025, and July 22, 2025.

### Copilot extensibility

- **Hebrew support in Agent builder** \[Windows, Web\]

  Integrate Hebrew language support in agent builder to build accessible, localized solutions that simplify multilingual deployments and enhance user engagement. [Learn more](https://learn.microsoft.com/en-us/microsoft-365-copilot/extensibility/copilot-studio-agent-builder-availability).
- **Increased support for uploading up to 20 documents to agents' knowledge** \[Windows, Web\]

  End users and makers can now upload up to 20 documents to ground agents with richer, embedded knowledge in Microsoft Copilot Studio agent builder. [Learn more](https://learn.microsoft.com/en-us/microsoft-365-copilot/extensibility/copilot-studio-agent-builder-knowledge).
- **Share agents from embedded builder** \[Windows, Web\]

  Users can share agents from an embedded agent builder to other individual users or group chats. [Learn more](https://learn.microsoft.com/en-us/microsoft-365/admin/manage/manage-embedded-knowledge-agents).
- **Share agents with context-aware link previews** \[Windows, Web\]

  Streamline your interactions by using context-aware buttons that adapt based on where links are shared-making it easier to take the right action in chats and meetings.
- **Upload and embed knowledge in declarative agents** \[Windows, Web\]

  Empower your agents with enriched context by uploading your own files and embedding crucial knowledge for personalized, day-to-day assistance. [Learn more](https://learn.microsoft.com/en-us/microsoft-copilot-studio/knowledge-add-file-upload).

### Microsoft 365 Copilot Chat

- **Dictate your prompts in Copilot Chat** \[Windows, Web\]

  You can now use the dictation button to input your prompts via speech, making interactions with Copilot more natural and efficient. [Learn more](https://www.microsoft.com/microsoft-365/roadmap?filters=&searchterms=475968).
- **Researcher available in GA** \[Windows, Mac, Web\]

  The researcher agent is pre-installed in Copilot Chat for all worldwide users. Find it in the left navigation pane alongside other agents, giving you quick access to research tools as part of the Copilot Premium license. [Learn more](https://www.microsoft.com/microsoft-365/blog/2025/06/02/researcher-and-analyst-are-now-generally-available-in-microsoft-365-copilot/?msockid=2484525e9a9b66d4330b47329bb667c9).

### PowerPoint

- **Create a presentation with Microsoft 365 Copilot from menus** \[Windows\]

  You can quickly begin a new presentation using Microsoft 365 Copilot from the PowerPoint start menu or file menu. Copilot is easily accessible when you open PowerPoint or click the File tab, helping to simplify your workflow. [Learn more](https://support.microsoft.com/office/create-a-new-presentation-with-copilot-in-powerpoint-3222ee03-f5a4-4d27-8642-9c387ab4854d).
- **Microsoft 365 Copilot generates the new presentation in a new file when starting from an existing presentation** \[Mac, Windows\]

  Now, when creating a presentation using Microsoft 365 Copilot from an existing presentation, it creates the new presentation in a new file without affecting the original presentation. [Learn more](https://support.microsoft.com/office/create-a-new-presentation-with-copilot-in-powerpoint-3222ee03-f5a4-4d27-8642-9c387ab4854d).
- **Reference multiple files in your presentation creation using Microsoft 365 Copilot** \[Windows, Mac, Web\]

  Enhance your PowerPoint presentations by referencing up to five files with Microsoft 365 Copilot, making it easier to incorporate detailed insights and comprehensive data without switching contexts. [Learn more](https://support.microsoft.com/office/create-a-new-presentation-with-copilot-in-powerpoint-3222ee03-f5a4-4d27-8642-9c387ab4854d).

### Word

- **Easily write a prompt or choose quick actions from the Copilot icon in your Word doc** \[Mac, Windows\]

  The Copilot icon in your document margin makes it easy to quickly add a prompt or choose from a range of quick options Copilot can offer. [Learn more](https://www.microsoft.com/microsoft-365-life-hacks/everyday-ai/how-to-use-copilot-in-microsoft-word?msockid=2484525e9a9b66d4330b47329bb667c9).
- **Preserve text formatting in drafted content** \[Windows\]

  Word Copilot now preserves the styling of surrounding content when generating text, ensuring a seamless and professional authoring experience. Copilot now understands and respects more contextual formatting-whether the user is writing in a list, table, heading, or styled paragraph. This includes support for bold, italic, underline, and links. This allows the generated text to better match the structure and basic formatting of the document. The result is a smoother authoring experience with less need for manual reformatting.

## July 8, 2025

Updates released between June 24, 2025, and July 8, 2025.

### Copilot extensibility

- **Add Dataverse as knowledge in Copilot** \[Web, Windows\]

  Users can now include Dataverse as a knowledge source in Copilot, enabling more comprehensive responses and insights. [Learn more](https://learn.microsoft.com/en-us/microsoft-365-copilot/extensibility/build-declarative-agents?tabs=ttk&tutorial-step=1).
- **Audit and eDiscovery for Copilot actions and declarative agents** \[Windows, Web\]

  View detailed audit logs and eDiscovery records for Copilot actions and declarative agents in Microsoft Purview to simplify compliance and investigation workflows. [Learn more](https://learn.microsoft.com/en-us/purview/audit-copilot).
- **Deploy Copilot agents for easy discovery** \[Windows, Web\]

  Deploy Copilot agents in the store for user discovery directly from your apps. Users can get new agents, open the store, install, and use them seamlessly within App Chat. [Learn more](https://learn.microsoft.com/en-us/microsoft-365/admin/manage/manage-copilot-agents-integrated-apps).
- **Discover, acquire, and manage agents through in-app store in Word and PowerPoint** \[Windows, Web\]

  With Copilot extensibility, users can discover, acquire, and manage agents through the unified store. We are excited to introduce the Microsoft 365 unified store to Office documents, enabling users to discover, acquire, and manage agents directly within the in-app store for Word and PowerPoint, with Excel support coming soon. [Learn more](https://devblogs.microsoft.com/microsoft365dev/office-addins-at-build-2025/#modernized-store-for-office-add-ins-and-copilot-agents).

### Excel

- **Copilot in Excel with Python \| Reasoning Model Integration \(Think Deeper\)** \[Mac, Windows, Web\]

  While performing advanced analysis with Copilot in Excel with Python, users can choose the "Think Deeper" mode to get a more elaborate and detailed plan, followed by automatic execution to generate Python code, results, and explanations. This improves performance on complex asks by leveraging the power of the latest AI reasoning models.

### Microsoft 365 Copilot app

- **Create in the Microsoft 365 Copilot app** \[Windows, Web\]

  The creative hub for AI led artifact generation capabilities. [Learn more](https://support.microsoft.com/topic/get-started-with-microsoft-365-copilot-create-6e0c616d-69fb-42f2-a4cb-c59e006ec4f5).
- **Updated UI for Microsoft 365 Copilot App** \[Windows, Web\]

  The Microsoft 365 Copilot app is your starting place for AI at work, offering quick access to secure AI chat, search, files, and content creation in one seamless app. [Learn more](https://www.microsoft.com/microsoft-365/blog/2025/04/23/microsoft-365-copilot-built-for-the-era-of-human-agent-collaboration/).

### Microsoft 365 Copilot Chat

- **Locate your Copilot Pages in Microsoft 365 Copilot Chat navigation pane** \[Windows, Web\]

  For quick access to your Copilot Pages, find all page artifacts created across your apps/modules in one place underneath the Chat section in the Microsoft 365 Copilot app. [Learn more](https://techcommunity.microsoft.com/blog/nonprofittechies/introduction-to-microsoft-copilot-pages/4421413).

### Teams

- **Copilot in Meetings will suggest follow up questions to ask it** \[Windows, Mac\]

  When Copilot in Teams Meetings responds to a prompt, it will also suggest follow-up prompts to ask Copilot that builds on the prior response. These questions will generally be based on the response it gave prior, and could be related to honing in on a particular topic, asking for more details, or even reformatting the content into a table if appropriate. [Learn more](https://support.microsoft.com/office/use-copilot-in-microsoft-teams-meetings-0bf9dd3c-96f7-44e2-8bb8-790bedf066b1).

### Viva Connections

- **New News feature in Microsoft Teams** \[Android, Windows, iOS, Web\]

  This update replaces the current Feed experience in Viva Connections across desktop, mobile, and web platforms with a SharePoint News reader experience. This new experience presents SharePoint news from organizational sites, boosted news, users' followed sites, frequent sites, and people they work with in an immersive reader format. It includes a Copilot-powered news summary as well, available only in Teams for Windows desktop in this initial release. [Learn more](https://techcommunity.microsoft.com/blog/viva_connections_blog/introducing-enterprise-news-reader-in-viva-connections/4383832).

### Word

- **Automatic summary of documents on file-open in Word** \[Windows, Mac, Web\]

  When users open a document, Copilot generates a summary in the Word window. You can hide the summary or open the Copilot chat pane to ask specific questions about the document. [Learn more](https://support.microsoft.com/office/create-a-summary-of-your-document-with-copilot-in-word-79bb7a0a-3bf7-41fe-8c09-56f855b669bf).

## June 24, 2025

Updates released between June 10, 2025, and June 24, 2025.

### Copilot extensibility

- **Admins can manage Copilot extensibility under Copilot tab in Microsoft 365 admin center** \[Windows, Web\]

  Admins have options to manage Copilot extensibility under Copilot tab including agent management for IT published agents and shared agents. [Learn more](https://learn.microsoft.com/en-us/microsoft-365/admin/manage/manage-copilot-agents-integrated-apps).
- **Build agents faster with built in Office skills** \[Windows, Web\]

  Empower your agent building by consuming built-in Office skills like Q&A on documents and PowerPoint summaries. This feature speeds up integrations, reduces the need for custom solutions, and delivers context-aware insights for a smarter agent experience.
- **Declarative agents can read the current document in WXP** \[Windows, Web\]

  Improve your workflow with agents that dynamically interact with open documents. Receive real-time suggestions, automate edits, and extract key data to streamline reviews and boost productivity. [Learn more](https://adaptivecards.microsoft.com/?topic=Action.InsertImage).
- **Discover, acquire, and manage agents through in-app store** \[Windows, Web\]

  Users can now easily discover, acquire, and manage Copilot agents directly within their Word and PowerPoint documents through a unified in-app store. This streamlined experience simplifies adding new capabilities-and Excel support is coming soon. [Learn more](https://devblogs.microsoft.com/microsoft365dev/office-addins-at-build-2025/#modernized-store-for-office-add-ins-and-copilot-agents).
- **Manage custom Copilot agents in Agent Center** \[Windows, Web\]

  Organize, store, and update your declarative Copilot agents in one place. Agent Center lets developers register in-context actions, fine-tune prompts, and test behavior faster-so IT admins can roll out reliable, task-specific Copilot experiences at scale. [Learn more](https://devblogs.microsoft.com/microsoft365dev/introducing-the-agent-store-build-publish-and-discover-agents-in-microsoft-365-copilot/).
- **Non-citation links remain visible in custom actions** \[Windows, Web\]

  Links returned from your custom actions are no longer redacted when they aren't part of a citation, letting users follow the full URL for easier validation and deeper exploration. [Learn more](https://techcommunity.microsoft.com/blog/microsoftdefenderforoffice365blog/safelinks-protection-for-links-generated-by-m365-copilot-chat-and-office-apps/4396828).

### Excel

- **Use Copilot with any table in the workbook, referring by natural language** \[iOS, Web, Mac, Windows\]

  Copilot uses the context of your prompt to pick what selection of data to answer about and reason over, including tables in other sheets. [Learn more](https://techcommunity.microsoft.com/blog/excelblog/smarter-context-awareness-for-copilot-in-excel/4424939).

### Microsoft 365 Copilot app

- **Upload phone images to Copilot in Office apps** \[Windows\]

  Snap a photo on your phone and send it straight to Copilot in Word, PowerPoint, Excel, or OneNote to generate content, extract text, or get design ideas-no cables or transfers needed. [Learn more](https://techcommunity.microsoft.com/blog/microsoft365insiderblog/upload-a-phone-image-to-microsoft-365-copilot/4398121).
- **Use Copilot suggested prompts for recommended entities** \[Windows, Mac, Web\]

  Empower your work with a $30 Copilot license by clicking on curated prompts within recommended entities. Uncover key insights on demand-helping you boost productivity in everyday tasks. [Learn more](https://techcommunity.microsoft.com/blog/microsoft365copilotblog/getting-the-most-from-the-copilot-prompt-gallery/4383106).

### Microsoft 365 Copilot

- **Copilot Prompt Gallery - share prompts with a Teams team** \[Windows, Web\]

  Share custom prompts with members of a Microsoft Teams team directly from Copilot Prompt Gallery, allowing colleagues to easily discover and reuse them in Copilot Chat. [Learn more](https://support.microsoft.com/topic/sharing-prompts-with-a-team-2fa7a228-8645-4dc4-beec-d75d6d0bc752).

### Microsoft 365 Copilot Chat

- **Catch up on Task related emails through Microsoft 365 Copilot Chat.** \[Windows\]

  Users can use Microsoft 365 Copilot Chat to prioritize emails that require immediate attention, address urgent tasks, or contain action items or questions. Timely identification of such emails helps users complete these tasks efficiently or plan their work effectively.
- **Locate your Copilot Pages in Copilot Chat navigation pane** \[Windows, Web\]

  For quick access to your Copilot Pages, find all page artifacts created across your apps/modules in one place underneath the Chat section in the Microsoft 365 Copilot app. [Learn more](https://techcommunity.microsoft.com/blog/nonprofittechies/introduction-to-microsoft-copilot-pages/4421413).
- **Play back responses as audio** \[Windows, Web\]

  Listen to Copilot's replies with a built-in read aloud feature-ideal for multitasking or when you need to review content hands-free. [Learn more](https://www.microsoft.com/microsoft-365/roadmap?filters=&searchterms=475967).
- **Scheduled prompts** \[Windows, Mac, Web, Teams\]

  Plan ahead by scheduling essential prompts for repeated tasks in Copilot chat. Create a productive routine that helps you stay organized and efficient. [Learn more](https://learn.microsoft.com/en-us/microsoft-365/copilot/scheduled-prompts).

### Microsoft Clipchamp

- **Clipchamp Copilot video creator** \[Windows, Web\]

  Create a video draft on any topic by providing a prompt. Clipchamp will generate a script, source stock footage and music, add AI voice-over, text overlays, and transitions-giving you a ready-to-edit project you can export to OneDrive. [Learn more](https://support.microsoft.com/topic/how-to-create-video-with-copilot-7586329a-64e0-4ae9-9444-0da5b1c2b848).

### PowerPoint

- **Create a PowerPoint slide from a file or prompt** \[Web, Windows, Mac\]

  Creating impactful slides can be challenging and time-consuming. Copilot helps you quickly turn your ideas and files into a fully designed slide with content ready to edit and refine, making the presentation creation and refinement process more personalized and efficient. [Learn more](https://support.microsoft.com/topic/add-a-slide-from-a-file-with-copilot-in-powerpoint-9034b581-38df-46be-a725-986cbbd4b5d4).
- **Designer is now part of Copilot, enhanced with new template and slide suggestions** \[Mac, Windows, Web\]

  Enjoy familiar Designer slide layouts and presentation template suggestions in a vertical gallery. Copilot now brings you enhanced suggestions to quickly build impactful presentations. [Learn more](https://support.microsoft.com/office/create-professional-slide-layouts-with-designer-53c77d7b-dc40-45c2-b684-81415eac0617).
- **Easily select a template while you create a new PowerPoint presentation with Copilot** \[Mac, Web, Windows\]

  When creating a new presentation with Copilot in PowerPoint, choose a template from your organization's collection for on-brand presentations, or select from Microsoft's handpicked templates, ensuring the new presentation is built as per your chosen template. [Learn more](https://support.microsoft.com/topic/keep-your-presentation-on-brand-with-copilot-046c23d5-012e-49e0-8579-fe49302959fc).
- **Reference a PDF file when creating a presentation with Microsoft 365 Copilot** \[Mac, Windows, Web\]

  You can now reference a PDF file when you create a presentation with Copilot within the PowerPoint application. [Learn more](https://support.microsoft.com/office/create-a-new-presentation-with-copilot-in-powerpoint-3222ee03-f5a4-4d27-8642-9c387ab4854d).

## June 10, 2025

Updates released between May 29, 2025, and June 10, 2025.

### Copilot extensibility

- **One-click setup for all connectors** \[Windows, Web\]

  New and existing connectors now install in a single step within the admin center, speeding up data integration and reducing support calls. [Learn more](https://learn.microsoft.com/en-us/microsoft-365-copilot/extensibility/overview-copilot-connector).

### Excel

- **Improvements to Copilot chat experience** \[Windows, Web, Mac\]

  Improvements to the Excel Copilot chat experience to give more consistent responses to all chat questions.

### Microsoft 365 Copilot Chat

- **Advanced email filtering in Copilot chat** \[Windows\]

  Quickly surface exactly the emails you need-ask Microsoft 365 Copilot Chat for "last week's external emails," "threads I haven't replied to," "purple-category mail," or "summarize German emails" "emails where I'm on the To line"-and focus on what matters most.
- **Find emails awaiting your reply** \[Windows\]

  Tell Microsoft 365 Copilot Chat "show me emails that I need to reply" and instantly see unread, read, @mentioned emails or emails with some question, task that you haven't answered-while hiding threads you've already closed-so you can clear your inbox with confidence.
- **Module UI refresh** \[Windows, Web\]

  Copilot Chat is designed to provide a streamlined UI, making it easy to get started and achieve your goals quickly. It offers a helpful, understanding, and personalized experience, allowing you to search for past interactions, content, agents, or pages with ease. [Learn more](https://support.microsoft.com/topic/get-started-with-microsoft-365-copilot-chat-5b00a52d-7296-48ee-b938-b95b7209f737).
- **Simplified Input box update** \[Windows, Web\]

  We've made it easier for users to type prompts with access to CIQ, local files, attach cloud files, and agents by adding it under the Plus Menu.

### Outlook

- **Custom Instructions for draft with Copilot** \[Android, Windows, iOS, Mac, Web\]

  Give Copilot some instructions about your emails - like the tone, length, greeting - so your Copilot generated drafts sound more like you want them to. #newoutlookforwindow
- **Schedule a meeting from an email with Copilot** \[Android, Windows, iOS, Mac, Web\]

  Turn any email thread into a meeting in one click. Copilot builds a complete invite for your review -title, agenda, attendee list, and a summary of the email conversation-plus attaches the original email thread so everyone is up to speed. Available in the new Outlook for Windows, web, Mac, and mobile. #newoutlookforwindows [Learn more](https://support.microsoft.com/office/create-a-meeting-and-agenda-with-copilot-in-outlook-31a44dfa-62bb-4751-82c4-14327a26759f).

### PowerPoint

- **Microsoft 365 Copilot Chat: Reference a TXT file when creating a presentation with Copilot** \[Windows, Mac, Web\]

  You can now reference a TXT file when you create a presentation with Copilot within the PowerPoint application. [Learn more](https://support.microsoft.com/office/create-a-new-presentation-with-copilot-in-powerpoint-3222ee03-f5a4-4d27-8642-9c387ab4854d).

### Teams

- **Improvements to the transcription experience in meetings** \[Windows, Mac\]

  These updates enhance the transcription experience in meetings. When transcription, recording, or Copilot is enabled, users are prompted to choose the spoken language for accurate captions. Once transcription is running, only the organizer, co-organizers, and transcript initiator can change that language. A new settings page under Caption settings > Language settings > Meeting spoken language, along with a matching option under Transcript > Language settings, streamlines configuration. If someone speaks a language that doesn't match the selected one, the organizer/co-organizer and initiator receive a mismatch notification so they can adjust quickly. [Learn more](https://support.microsoft.com/office/use-live-captions-in-microsoft-teams-meetings-4be2d304-f675-4b57-8347-cbd000a21260#:%7E:text=The%20meeting%20organizer%2C%20co%2Dorganizer\(s\)%2C%20transcript,Select%20Update%20to%20change.).
- **Microsoft Teams: Intelligent recap support for ad-hoc meetings and calls in GCC High** \[Android, Windows, iOS, Mac, Web\]

  Intelligent meeting recap is now available in GCC High for impromptu calls and meetings, like those started from 'Meet now' and calls started from chat. You can easily browse the recording by speakers and topics, as well as access AI-generated notes, AI-generated tasks, and name mentions after the ad-hoc meeting ends. This capability is available for users with a Teams Premium or M365 Copilot license.

### Word

- **Draft content from up to 10 chosen references** \[Mac, Windows\]

  Type a forward slash \(/\) to pick as many as ten files, meetings, or emails for Copilot to cite while drafting your document. The release started with 10 chosen references but is expanding to support up to 20. [Learn more](https://techcommunity.microsoft.com/blog/microsoft365insiderblog/expanding-reference-capabilities-with-microsoft-365-copilot-in-word/4406054).
- **Write a prompt for selected text in Word** \[Windows\]

  Draft content based only on the sentence or list item you highlight-no more expanding the selection to the entire paragraph or table.

## May 29, 2025

Updates released between May 13, 2025, and May 29, 2025.

### Copilot extensibility

- **Insert images in adaptive cards for richer interactions** \[Windows, Web\]

  Make your adaptive cards more dynamic by adding images-perfect for illustrating ideas, sharing visual data, or engaging users with eye-catching content. This feature helps teams communicate clearly, support diverse learning styles, and create more memorable interactions in everyday workflows. [Learn more](https://learn.microsoft.com/en-us/microsoft-copilot-studio/guidance/adaptive-card-summarize-responses).
- **Unified Agent Management for Admins in Microsoft admin center** \[Windows, Web\]

  Admins can consistently manage Copilot agents in the Microsoft admin center, regardless of how they were built, simplifying deployment and governance. [Learn more](https://learn.microsoft.com/en-us/microsoft-365/admin/manage/manage-plugins-for-copilot-in-integrated-apps).

### Excel

- **Access Copilot tools right from the grid** \[Windows\]

  A handy Copilot icon and context menu now follow your work in the worksheet, letting you launch summaries, formula help, and more without breaking focus. [Learn more](https://techcommunity.microsoft.com/blog/excelblog/how-to-get-started-with-copilot/4383870).

### Microsoft 365 Copilot Chat

- **Copilot Chat now offers access to cloud files to insert in user prompts** \[Windows, Web\]

  In the Web tab of Copilot Chat or Microsoft 365 Copilot, users can browse OneDrive or SharePoint, select a file, and drop it into their prompt to give Copilot precise context for richer responses.
- **Enable agent builder for Copilot chat** \[Windows, Web\]

  Empower developers with the ability to build custom agents to support Copilot Chat. This feature streamlines the creation of tailored chat experiences that enhance everyday communication and workflow. [Learn more](https://learn.microsoft.com/en-us/microsoft-365-copilot/extensibility/copilot-studio-agent-builder-build).
- **Enhanced typography improves readability** \[Windows\]

  Enjoy crisper fonts, roomier line spacing, clear headers, and neatly formatted tables and code blocks-making every Copilot chat easier to scan, share, and act on.
- **Expanded reference panel for sources and search results** \[Windows\]

  The reference widget now shows both cited sources and relevant web results, helping you verify information, resolve ambiguities, and ask smarter follow-up questions without leaving the chat.
- **Pay-as-you-go policies keep Copilot costs in check** \[Windows, Web\]

  Allocate budgets by department, set usage caps, and manage access from the admin center so your organization can innovate with Copilot while staying on budget. [Learn more](https://learn.microsoft.com/en-us/microsoft-365/copilot/pay-as-you-go/overview).
- **Safe Links validates redacted URLs** \[Windows\]

  When Copilot masks a link, Safe Links now scans it instantly and alerts users to malicious sites, adding an extra layer of protection before anyone clicks. [Learn more](https://techcommunity.microsoft.com/blog/microsoftdefenderforoffice365blog/safelinks-protection-for-links-generated-by-m365-copilot-chat-and-office-apps/4396828).

### PowerPoint

- **Ask Copilot to rewrite text as a list** \[Web, Mac, Windows\]

  Transform paragraphs into clear bullet points or lists with a single command-ideal for quickly organizing content when preparing your presentation. [Learn more](https://support.microsoft.com/topic/elevate-your-presentation-game-with-copilot-s-text-rewrite-feature-in-powerpoint-d70b140b-bb3f-46b7-be64-ceec526a8dcd).

### Word

- **Ask agents to refine any text selection** \[Windows, Web\]

  Highlight a section of your document and let Copilot agents rewrite, shorten, or expand it-keeping the rest of your file private while you perfect the details.
- **Chat with Copilot about any image or chart** \[Windows\]

  Drop a visual into Copilot chat to extract text, get a plain-language description, generate alt text, or request quick insights-perfect for accessibility checks or fast analysis. [Learn more](https://support.microsoft.com/topic/file-upload-in-microsoft-copilot-8b7bf432-9576-4b16-9dee-6c19a4169e62).

## May 13, 2025

Updates released between April 29, 2025, and May 13, 2025.

### Excel

- **Advanced analysis with Python and Copilot** \[Windows\]

  Chat with your spreadsheet and let Copilot run Python scripts to surface trends, build rich visuals, and test what-if scenarios-now fully localized for your team's language. [Learn more](https://support.microsoft.com/office/copilot-in-excel-with-python-364e4ae9-9343-4d56-952a-5f62b0f70db6).
- **Ask Copilot about any part of your sheet** \[Web, Mac, Windows, iOS\]

  When you ask questions about your worksheet, Copilot can look at the content of your sheet and use it to inform an answer to your question. This includes understanding worksheet data on your selected area, beyond tables and ranges, and provide Copilot answers in chat.

### Microsoft 365 admin center

- **Manage pay-as-you-go billing for Copilot** \[Windows, Web\]

  Admins can manage pay-as-you-go billing directly within Copilot settings in the Microsoft 365 admin center. This capability is available to users with Global admin, AI admin, and Global reader roles. [Learn more](https://learn.microsoft.com/en-us/microsoft-365/copilot/pay-as-you-go/setup).

### Microsoft 365 Copilot Chat

- **Copilot pages in Government Clouds** \[Windows\]

  Copilot Pages is an interactive, shareable canvas in Microsoft 365 Copilot Chat designed for multiplayer AI collaboration. With Pages, users can turn Copilot responses into something durable with a side-by-side page where users can edit and share with others to collaborate. Now available for Government Cloud users. [Learn more](https://support.microsoft.com/topic/introducing-microsoft-365-copilot-pages-6674bd51-9ff5-42c4-9256-44d9428a726f).
- **Unified prompt box across web and work chats** \[Windows, Web\]

  Enjoy a consistent prompting experience across Copilot Chat with an input box that looks and behaves the same in both work and web chat modes.

### PowerPoint

- **Get slide template suggestions as you create** \[Windows\]

  Copilot now recommends polished layouts the moment you add or name a slide, letting you stay in the flow and skip manual design hunts. [Learn more](https://techcommunity.microsoft.com/blog/microsoft365insiderblog/jumpstart-your-presentations-with-slide-starters/4407669).

### Viva Insights

- **Viva Insights now included in Microsoft 365 Copilot subscriptions** \[Windows, Web, TeamsAndSurfaceDevices\]

  Create advanced, custom reports with Viva Insights to understand Copilot adoption, productivity and business impact. Full access to Viva Insights is available now with Microsoft 365 Copilot subscriptions.

### Word

- **Choose the level of detail for summaries when documents are opened** \[Windows, Mac, Web\]

  Tailor each document opening with your preferred summary style-select brief, standard, or detailed insights to match your workflow. [Learn more](https://support.microsoft.com/office/create-a-summary-of-your-document-with-copilot-in-word-79bb7a0a-3bf7-41fe-8c09-56f855b669bf).

## April 29, 2025

Updates released between April 16, 2025, and April 29, 2025.

### Excel

- **Ask Copilot to extract insights from inserted images** \[Windows\]

  Transform images in your Excel workflows into actionable data. Simply insert an image into the prompt area and ask Copilot to break down details and trends, so you can make informed decisions on the fly.
- **Paste images into Copilot chat** \[Web, Windows\]

  Ask questions about images you insert into the prompt area to extract key data for your spreadsheets. [Learn more](https://techcommunity.microsoft.com/blog/microsoft365insiderblog/add-images-to-your-copilot-prompts-in-word-and-powerpoint/4359423).

### Microsoft 365 Copilot extensibility

- **Agent builder now available in new regions** \[Windows, Web\]

  You can now access Copilot Studio agent builder in Norway, Sweden, South Korea, and South Africa. [Learn more](https://learn.microsoft.com/en-us/microsoft-365-copilot/extensibility/copilot-studio-agent-builder-availability#regional-availability).

### Microsoft Copilot Chat

- **M365 Copilot for GCC Environments: Wave 2** \[Windows\]

  Bringing Microsoft 365 Copilot GCC your AI assistant for work in the GCC environment. It combines the power of Large Language Models with your work content and context, to help you draft and rewrite, summarize and organize, catch up on what you missed, and get answers to questions via open prompts. Copilot generates answers using the rich, people-centric data and insights available in the Microsoft Graph. Microsoft 365 Copilot GCC is now available in Stream, SharePoint, OneNote, and Pages in Loop. [Learn more](https://techcommunity.microsoft.com/blog/publicsectorblog/what%E2%80%99s-new-in-microsoft-365-copilot-for-government/4399086).
- **Submit feedback on the agent builder experience** \[Windows, Web\]

  Improve your custom Copilot Chat solutions by providing targeted feedback on RAI and agent response during test chats. This direct input helps refine and enhance the builder experience. [Learn more](https://learn.microsoft.com/en-us/microsoft-365-copilot/extensibility/copilot-studio-agent-builder#submit-feedback).

### Viva Learning

- **AI & Copilot Resources provider availability to all Viva Learning users** \[Windows, Web, Teams\]

  The AI & Copilot Resources provider is now enabled by default for all Viva Learning users. Administrators now have the ability to manage the visibility of this provider within Viva Learning. [Learn more](https://learn.microsoft.com/en-us/viva/learning/ai-and-copilot-resources).
- **Copilot Academy availability to all Microsoft 365 users** \[Windows, Web, Teams\]

  Copilot Academy is now accessible to users without Copilot licenses. Admins now have the option to select their preferred access settings for Copilot Academy. [Learn more](https://learn.microsoft.com/en-us/viva/learning/academy-copilot).

### Word

- **Replace your selection with generated content** \[Web, Mac, Windows\]

  Selecting the Replace button lets you instantly replace your selected text with content that was generated in Draft with Copilot.

## April 16, 2025

Updates released between April 2, 2025, and April 16, 2025.

### Excel

- **Access Copilot on-grid in Windows** \[Windows\]

  A Copilot icon appears right within your spreadsheet on Windows, giving you quick AI assistance as you work to keep your flow uninterrupted.
- **Graph grounded chat** \[Windows, Mac, Web\]

  Ask Copilot in Excel for insights drawn from your chats, documents, meetings, and emails via Microsoft Graph-enhancing your workbook analysis with contextual organizational data. [Learn more](https://support.microsoft.com/topic/use-copilot-to-find-data-from-the-web-or-your-organization-and-add-it-in-excel-7a72fb29-e623-49e2-9f7d-38664b593054).
- **Use Copilot to search for answers from the web** \[Windows, Mac, Web\]

  In Excel, simply ask Copilot to search the web for answers and integrate the insights directly into your workbook, making data analysis even smoother. [Learn more](https://support.microsoft.com/topic/use-copilot-to-find-data-from-the-web-or-your-organization-and-add-it-in-excel-7a72fb29-e623-49e2-9f7d-38664b593054).

### Microsoft 365 Copilot Chat

- **Get contextual suggestions during Copilot agent conversations** \[Windows, Web\]

  Speed up tasks with AI-driven prompts for next steps in Copilot Chat. See real-time suggestions to refine queries, dive deeper into topics, or resolve issues faster during agent interactions.
- **Support for longer prompts** \[Windows, Web\]

  Copilot Chat now supports larger inputs for smoother handling of extensive documents and data.

### Microsoft 365 Copilot extensibility

- **Discover agents for unlicensed and metered users** \[Windows, Web\]

  Empower more users with easy access to agents tailored to their needs-even if they are unlicensed or metered-broadening Copilot's reach across your organization. [Learn more](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/debugging-agents-copilot-studio).

### OneNote

- **Copilot-powered organization in OneNote** \[Windows\]

  Transform a flat list of pages within a section to have an intuitive hierarchy. Ask Copilot in chat to organize your section and apply the update for a streamlined Notebook organization experience. [Learn more](https://support.microsoft.com/topic/organize-your-notes-with-copilot-in-onenote-f7d0477b-676c-4fa1-8c82-8900bb888618).

## April 2, 2025

Updates released between March 20, 2025, and April 2, 2025.

### PowerPoint

- **Translate your presentation** \[Windows, Web, Mac\]

  Produce a translated copy of your entire presentation in about 40 languages while preserving your slide design and structure, making global collaboration effortless. [Learn more](https://support.microsoft.com/topic/translate-your-presentation-with-copilot-2c622fca-daaf-457c-bc74-f3496cf44a85).

## March 19, 2025

Updates released between March 5, 2025, and March 19, 2025.

### Microsoft 365 Copilot Chat

- **Prompt suggestions in Copilot chat** \[Windows, Web, Mac\]

  Get started in Copilot chat quickly with automatic prompt suggestions that enhance your productivity by providing relevant and context-aware prompts based on your previous interactions.

### Microsoft 365 Copilot extensibility

- **Support for message extension and declarative agents** \[Windows, Web\]

  Transform legacy plugins into integrated experiences by exposing them as declarative agents-enhance Office apps like Word, Excel, and PowerPoint with message extensions.

### OneNote

- **Support image input in OneNote chat** \[Windows\]

  Ask Copilot to analyze image input and organize your notebook pages by detecting themes and topics. Quickly group pages and update your Notebook structure with a simple click.

### Microsoft 365 Copilot

- **Share a Copilot prompt with a Teams team** \[Windows, Web\]

  Easily share custom prompts from the Copilot Prompt Gallery with your Microsoft Teams team. This streamlined sharing makes it simple for team members to discover and make the most of these prompts in their daily workflow. [Learn more](https://support.microsoft.com/topic/sharing-prompts-with-a-team-2fa7a228-8645-4dc4-beec-d75d6d0bc752?OCID=copilot_ongoingemail_feb25).

## March 4, 2025

Updates released between February 20, 2025, and March 4, 2025.

### Microsoft 365 Copilot Chat

- **Search archived mailboxes in Copilot Chat** \[Windows, Web, Android, iOS, Mac\]

  Leverage Copilot to search emails across both primary and archived mailboxes by appending 'from my archives' or 'also look for emails in archives' in your prompts to quickly locate key messages.

### PowerPoint

- **Add speaker notes to all slides with one command** \[Windows\]

  Speed up your presentation creation by having Copilot automatically add speaker notes to every slide, getting your narrative draft ready in a flash. [Learn more](https://support.microsoft.com/topic/add-speaker-notes-to-your-presentations-using-copilot-7139266b-8a1d-4056-8e30-4edcc4d80873).
- **Narrative builder creates slides with tables** \[Windows, Web, Mac\]

  Convert grounded content from Word documents into dynamic slides with tables. Enhance your presentations with structured, data-driven visuals effortlessly.

## February 19, 2025

Updates released between February 5, 2025, and February 19, 2025.

### Excel

- **Get powerful insights with python** \[Windows\]

  Explore your data naturally with advanced analysis that leverages Python-no expert coding needed to uncover trends and create dynamic visualizations.

### Microsoft Teams

- **Intelligent meeting recap for instant meetings \(premium\)** \[Windows, Mac\]

  Effortlessly browse meeting recordings by speaker and topic and access AI-generated notes, tasks, and mentions for instant meetings-empowering premium Copilot users with comprehensive insights. [Learn more](https://support.microsoft.com/office/meeting-recap-in-microsoft-teams-c2e3a0fe-504f-4b2c-bf85-504938f110ef).

### OneNote

- **Enhance note-taking with iterative content proposals** \[Windows\]

  Refine your notes on the fly by iterating prompts and reviewing alternate drafts, giving you a dynamic, customizable note-taking experience. [Learn more](https://support.microsoft.com/topic/take-notes-with-copilot-in-onenote-d5ddf33d-2bab-48de-9096-79df65f81207).
- **Take notes with Copilot directly in the flow from the canvas** \[Windows\]

  Seamlessly gather and create notes right on your page with Copilot integrated into your personal OneNote notebook, making in-flow note-taking more intuitive. [Learn more](https://support.microsoft.com/topic/take-notes-with-copilot-in-onenote-d5ddf33d-2bab-48de-9096-79df65f81207).

### PowerPoint

- **Create a presentation from a file-based prompt** \[Windows, Web, Mac\]

  Pull key facts and data from a selected file to shape your narrative. Simply provide Copilot with a prompt and quickly build your deck with relevant information. [Learn more](https://support.microsoft.com/office/create-a-new-presentation-with-copilot-in-powerpoint-3222ee03-f5a4-4d27-8642-9c387ab4854d).

### Viva Insights

- **Copilot dashboard for usage and retention insights** \[Windows, Web, Android, iOS, Mac\]

  Dive into usage frequency, compare top user groups, and track retention metrics-all in a single, comprehensive dashboard for actionable insights. [Learn more](https://learn.microsoft.com/en-us/viva/insights/org-team-insights/copilot-dashboard#interpreting-the-data).

### Word

- **Chat with Copilot about selected text** \[Windows, Web, Mac\]

  Highlight text, start a chat with Copilot, and receive responses tailored to what you've selected. Get targeted writing assistance and refine your content in real time.

## February 4, 2025

Updates released between January 24, 2025, and February 4, 2025.

### Microsoft 365 Copilot app

- **Updates to the Microsoft 365 \(Office\) app** \[Windows, Web, Android, iOS\]

  The Microsoft 365 Copilot app \(formerly Microsoft 365 app\) has a new name and icon. [Learn more](https://support.microsoft.com/office/the-microsoft-365-app-transition-to-the-microsoft-365-copilot-app-22eac811-08d6-4df3-92dd-77f193e354a5).

### Microsoft 365 Copilot Chat

- **Access support pages in Copilot Chat** \[Windows, Web, Android, iOS, Mac\]

  View organizational support pages directly within Copilot Chat, for quick help and guidance in your workflow.
- **Accommodate user's time zones in Copilot** \[Windows, Web, Android, iOS\]

  Copilot now references your local time zone when responding helping to avoid confusion and scheduling errors.
- **Charts, graphs, and data analysis in Copilot for Microsoft 365** \[Windows, Web\]

  Use natural language to create charts, graphs, and data analysis in Copilot Chat work mode.

### Microsoft Teams

- **Speaker recognition and attribution in BYOD rooms with Copilot** \[Windows, Mac\]

  Take advantage of speaker recognition and transcript attribution, unleashing new AI capabilities in any meeting space, whether or not it has a Teams Rooms system deployed. This feature identifies and attributes people in live transcripts, utilizing a unique voice profile for each participant enabling intelligent recaps and unlocking maximum value from Microsoft 365 Copilot in Teams meetings. Users can easily and securely enroll their voices via Teams Settings. This feature requires a Microsoft 365 Copilot or Teams Premium license for the user hosting the meeting for Copilot experiences and intelligent recaps, respectively. [Learn more](https://learn.microsoft.com/en-us/microsoftteams/rooms/voice-recognition).

### Microsoft 365 Copilot

- **Share a prompt with a co-worker** \[Windows, Web\]

  Easily create, save, and share your favorite prompts using Copilot Prompt Gallery, inspiring your co-workers to achieve more with Copilot. [Learn more](https://learn.microsoft.com/en-us/microsoft-365/copilot/copilot-prompt-gallery-export-prompts).

### Word

- **Reference data from the Microsoft cloud when drafting with Copilot in Word** \[Windows, Web, Mac\]

  Draft with Copilot now supports attaching rich content from the Microsoft cloud-including emails and meetings-resulting in more contextually relevant content. [Learn more](https://techcommunity.microsoft.com/blog/microsoft365copilotblog/what%E2%80%99s-new-in-microsoft-365-copilot-in-word-at-ignite-2024/4303448).
- **Reference plain text files in Copilot** \[Windows, Web, Mac\]

  Add .txt files as sources with Copilot in Word, streamlining your process when working with text-based research or background content.

## January 23, 2025

Updates released between January 8, 2025, and January 23, 2025.

### Microsoft 365 Copilot Chat

- **Introducing Microsoft 365 Copilot Chat** \[Windows, Web, Android, iOS\]

  Microsoft 365 Copilot Chat-secure AI chat powered by GPT-4o with agents accessible right in chat, and IT controls including enterprise data protection and agent management. Copilot Chat serves as a powerful new on-ramp for everyone in your organization to build an AI habit. And it is included with your Microsoft 365 subscription. Get started with Copilot Chat with the updated [Microsoft 365 Copilot app](https://www.m365copilot.com) \(formerly Microsoft 365 app\).

  [Learn more](https://www.microsoft.com/microsoft-365/blog/2025/01/15/copilot-for-all-introducing-microsoft-365-copilot-chat).
- **Updated Copilot Chat responses UI** \[Windows\]

  Enjoy a more intuitive Copilot experience with streamlined message boundaries, refined message count alerts, and a clearly positioned security badge for higher trust and transparency.
- **Updated meeting entity card in Copilot Chat** \[Windows, Web\]

  Check meeting details like RSVP status, date, and attachments without switching contexts in Copilot Chat.
- **Disable file upload in Copilot Chat** \[Windows, Web\]

  Admins gain control to turn off file uploads for Copilot Chat, helping maintain compliance when sharing sensitive content.
- **Use Pages in compliant Copilot web chat** \[Android, Windows, iOS, Mac, Web\]

  Admins gain control to turn off file uploads for Copilot Chat, helping maintain compliance when sharing sensitive content.

### Microsoft 365 Copilot app

- **Control auto-start behavior on windows** \[Windows\]

  Adjust Windows settings to let users auto-launch the M365 app upon login, while giving admins the option to enforce group policy controls for enterprise needs.
- **Keep the app running in the background** \[Windows\]

  Enable the setting to keep the app active as a background process after closing, ensuring faster subsequent launches without a full reload.

### PowerPoint

- **Generate summaries for longer presentations** \[Windows, Web, Mac\]

  Copilot now supports text summaries up to 40k words \(around 150 slides\), giving you richer information and more polished layouts. [Learn more](https://support.microsoft.com/office/summarize-your-presentation-with-copilot-in-powerpoint-499e604c-4ab9-4f6a-9dbe-691cc87f2f69).
- **Listen to Copilot's responses with Read Aloud** \[Windows, Mac\]

  Hear Copilot's replies in the chat pane, letting you stay hands-free while reviewing your content.

### Viva Insights

- **New Copilot adoption metrics and completing total actions taken** \[Windows, iOS, Mac\]

  This adds seven new Copilot adoption metrics to the Copilot dashboard and Viva Insights Advanced insights. It also updates the "total actions taken" metric in the Copilot dashboard to include these new Copilot adoption metrics. [Learn more](https://techcommunity.microsoft.com/blog/viva_insights_blog/new-microsoft-copilot-analytics-features-now-available-%E2%80%93-novemberdecember-2024/4356206).

### Word

- **Get started on a draft immediately with example prompts** \[Windows, Mac\]

  On blank documents, Copilot in Word offers one-click example prompts to help you get started quickly. [Learn more](https://techcommunity.microsoft.com/blog/microsoft365copilotblog/what%E2%80%99s-new-in-microsoft-365-copilot-in-word-at-ignite-2024/4303448).
- **Listen to Copilot's responses with Read Aloud** \[Windows, Web, Mac\]

  Hear Copilot's replies in the chat pane, letting you stay hands-free while reviewing your content.

## January 7, 2025

Updates released between December 18, 2024, and January 7, 2025.

### Microsoft 365 Copilot extensibility

- **Include Code Interpreter in agents** \[Windows, Web\]

  Enhance your agents by including Code Interpreter for advanced data analysis tasks in agent builder. [Learn more](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/code-interpreter).

### OneNote

- **Use Copilot quick actions in OneNote: Rewrite, Summarize, and Create To-Dos** \[Windows\]

  Enhance your notes by using Copilot directly on the OneNote canvas. Instantly generate summaries, create to-do lists, or rewrite selected content within your notes. [Learn more](https://support.microsoft.com/office/rewrite-text-with-copilot-in-onenote-a33f14c9-b2f4-46b0-87b9-389690221610).

### Outlook

- **Schedule meetings with Copilot chat in Outlook** \[Windows, Web\]

  Save time and streamline your day by asking Copilot to schedule meetings for you in Outlook. Whether it's a 1:1 or focus time, Copilot will find the best available time slots with ease. [Learn more](https://support.microsoft.com/topic/8090e7b3-5b1d-4c6d-9b06-02edac062f58).

### Viva Insights

- **Expand your understanding of Copilot adoption with enhanced metrics** \[Windows, iOS, Mac\]

  Access seven new Copilot metrics and see them reflected in "total actions taken," helping you better track how teams use Copilot. [Learn more](https://learn.microsoft.com/en-us/viva/insights/advanced/analyst/templates/microsoft-365-copilot-adoption).
- **New metrics for enterprise data-protected prompts** \[Windows, Web, Android, iOS, Mac\]

  Gain visibility into prompts submitted through Microsoft 365 Copilot Chat \(web\) and enterprise data-protected Copilot scenarios. [Learn more](https://learn.microsoft.com/en-us/viva/insights/advanced/reference/metrics#microsoft-365-copilot-metrics).

## December 23, 2025

Updates released between December 10, 2025, and December 23, 2025.

### Microsoft 365 Copilot app

- **GPT-5 powers Copilot Chat by default** \[Android, Windows, iOS, Mac, Web\]

  Copilot Chat delivers faster, smarter results using GPT-5 as the default model.

  **Details:**

  **What Changed:** All Copilot Chat experiences run on GPT-5 by default. Copilot automatically routes prompts to the best-performing models for each task, using fast models for basic tasks and specialized reasoning models for multi-step requests.

  **Why:** Users want speed, accuracy, and minimal friction. This update helps to ensure consistent, high-quality AI interactions in Copilot Chat.

  **Try This:**

  - "Get me up to speed on the latest plans related to \[project/initiative\]. Help me think through what to do next."
  - "Use the attached spreadsheet with customer feedback to create a polished executive report that helps upper management decide where to prioritize resources in our next cycle."


  **Why this matters:**


  **Business Impact:** Increases accuracy and productivity, helping teams make strong decisions and complete complex work faster.


  **Personal Impact:** Removes friction by letting Copilot choose the best model--fast or reasoning--for the prompt.


  **Additional resources:**


  **Blogs:**


  [Available today: GPT-5 in Microsoft 365 Copilot](https://www.microsoft.com/microsoft-365/blog/2025/08/07/available-today-gpt-5-in-microsoft-365-copilot/?msockid=281b58ceea286c6226164ec5eb056dd6)

### Microsoft 365 Copilot Chat

- **Streamlined Copilot chat navigation with expanded history** \[Windows, Web\]

  A redesigned navigation pane provides a cleaner layout and expanded chat history, making it easier to switch between conversations. This allows you to switch between conversations and pick up where you left off, perfect for fast-paced projects and multitasking.

  **Roadmap ID:** [516570](https://www.microsoft.com/microsoft-365/roadmap?msockid=2484525e9a9b66d4330b47329bb667c9&filters=&searchterms=516570)

  **Details:**

  **What Changed:** The Copilot navigation pane highlights key agents, removes clutter, and expands visible chat history beyond the previous limit of five recent chats. Chat search is also more prominent for faster access to specific threads. This reduces interface clutter.

  **Why:** Users wanted an interface that feels organized and speeds up workflow. This redesign lets you quickly return to prior conversations without digging through menus.

  **Try This:**

  - Open the navigation pane in Copilot to see the improved design.
  - Search for a previous project conversation using the updated chat search bar.
  - Pin your most important chats to keep them accessible during critical work sessions.


  **Why this matters:**


  **Business Impact:** Standard, simplified navigation UI to help reduce downtime from searching old threads.


  **Personal Impact:** Enjoy a simpler, less cluttered workspace with easier access to past chats.

### Microsoft 365 Copilot extensibility

- **Access IT service documentation with Freshservice integration** \[Web\]

  Let Copilot retrieve IT documentation and troubleshooting instructions directly from Freshservice with this integration.

  **Roadmap ID:** [513280](https://www.microsoft.com/microsoft-365/roadmap?msockid=2484525e9a9b66d4330b47329bb667c9&filters=&searchterms=513280)

  **Details:**

  **What Changed:** Freshservice connector gives access to IT procedures and knowledge articles

  **Why:** IT teams and employees often struggle with finding the right documentation. With Copilot pulling service details in real time, response times and productivity benefit.

  **Try This:**

  - Connect Freshservice in Copilot settings.
  - Ask Copilot, "What's the procedure for resetting passwords from Freshservice?"
  - Insert a troubleshooting guide directly into a Teams post for your team.


  **Why this matters:**


  **Business Impact:** Faster issue resolution reduces downtime and keeps employees productive.


  **Personal Impact:** Remove frustration, solve issues, and prevent delays caused by searching for documentation.


  **Additional resources:**


  **Learn:**


  [Freshservice Microsoft 365 Copilot connector overview](https://learn.microsoft.com/en-us/microsoftsearch/freshservice-overview)

- **Upload Larger Files in Copilot Studio Agent Builder** \[Android, Windows, iOS, Web\]

  Agent Builder now supports file uploads up to 512 MB when creating agents, ideal for larger files.

  **Roadmap ID:** [500375](https://www.microsoft.com/microsoft-365/roadmap?msockid=2484525e9a9b66d4330b47329bb667c9&filters=&searchterms=500375)

  **Details:**

  **What Changed:** This increases the upload size limit in Agent Builder to 512 MB, enabling use of larger files as grounding data.

  **Why:** Users requested more flexibility for grounding agents. Larger files improve reduce the need to split or compress documents.

  **Try This:**

  - Drag and drop large documents such as training manuals into your agent project.
  - Create the agent and ask it to summarize information from uploaded files.


  **Why this matters:**


  **Business Impact:** Allows enterprises to build agents with richer, domain-specific knowledge.


  **Personal Impact:** Complete your work without the need to split files or compress data.


  **Additional resources:**


  **Learn:**


  [Embedded file content](https://learn.microsoft.com/en-us/microsoft-365-copilot/extensibility/agent-builder-add-knowledge#embedded-file-content)

- **Use .NET client libraries to integrate Microsoft 365 Copilot APIs** \[Web\]

  Offers official .NET SDKs for integrating with Microsoft 365 Copilot APIs.

  **Details:**

  **What changed:** Released a .NET SDK for Copilot API calls, making integration easier.

  **Why:** Meets enterprise developers' need for secure .NET integration options.

  **Try This:**

  - Install NuGet package
  - Authenticate and initiate Copilot prompt calls
  - Process responses in your .NET app


  **Why this matters:**


  **Business Impact:** Improves developer productivity and project speed.


  **Personal Impact:** Gives .NET teams direct hooks into Copilot capabilities.


  **Additional resources:**


  **Learn:**


  [Microsoft 365 Copilot APIs client libraries](https://learn.microsoft.com/en-us/microsoft-365-copilot/extensibility/sdks/api-libraries?tabs=csharp)

- **Use Python client libraries to integrate Microsoft 365 Copilot APIs** \[Web\]

  Adds official Python libraries for secure integration with Microsoft 365 Copilot APIs.

  **Details:**

  **What changed:** Developers can now leverage Microsoft 365 Copilot APIs using Python SDKs.

  **Why:** Opens opportunities for AI workflows in Python-based applications.

  **Try This:**

  - Install Python SDK
  - Authenticate using OAuth
  - Send prompts and parse results


  **Why this matters:**


  **Business Impact:** Expands Copilot customization for enterprise developers.


  **Personal Impact:** Python devs gain first-class access to Copilot APIs.


  **Additional resources:**


  **Learn:**


  [Microsoft 365 Copilot APIs client libraries](https://learn.microsoft.com/en-us/microsoft-365-copilot/extensibility/sdks/api-libraries?tabs=csharp)

- **Use TypeScript client libraries to integrate Microsoft 365 Copilot APIs** \[Web\]

  Build custom integrations with Microsoft 365 Copilot APIs using official TypeScript SDK libraries.

  **Roadmap ID:** [501574](https://www.microsoft.com/microsoft-365/roadmap?msockid=2484525e9a9b66d4330b47329bb667c9&filters=&searchterms=501574)

  **Details:**

  **What changed:** Official TypeScript SDK released for Copilot API integration in web apps.

  **Why:** Standardizes developer integration with Microsoft 365 Copilot features.

  **Try This:**

  - Install SDK via npm
  - Authenticate using Microsoft Identity
  - Test API calls for Copilot prompts


  **Why this matters:**


  **Business Impact:** Enables custom enterprise apps with AI-powered features.


  **Personal Impact:** Developers have a secure, documented method for advanced builds.


  **Additional resources:**


  **Learn:**


  [Microsoft 365 Copilot APIs client libraries](https://learn.microsoft.com/en-us/microsoft-365-copilot/extensibility/sdks/api-libraries?tabs=csharp)

- **View and Manage SharePoint Agents with Greater Control** \[Web\]

  Admins can now see all SharePoint agents in a single unified view and manage them more intuitively with a streamlined delete action.

  **Details:**

  **What Changed:** The enhanced Copilot controls UI introduces a centralized SharePoint agent inventory and replaces the previous block/unblock workflow with a clear, simplified delete option.

  **Why:** Admins requested more transparent oversight of deployed agents, and this update delivers easier tracking, review, and lifecycle management.

  **Try This:**

  - Go to Agents and Connectors in Copilot controls.
  - Review all existing SharePoint agents and delete those that are outdated, unused, or no longer compliant.


  **Why this matters:**


  **Business Impact:** Strengthens governance and operational hygiene by reducing risk from stale or misconfigured agents.


  **Personal Impact:** Saves time with straightforward, intuitive controls instead of complex, multi-step administration.

### Microsoft 365 Copilot Studio

- **Build Copilot agents using organizational People data** \[Windows, Web\]

  Developers can build agents in Copilot Studio that deliver personalized, context-aware responses using organizational People data.

  **Details:**

  **What changed:** Added the ability for agent builders to access and use People data from your directory in responses.

  **Why:** Makes interactions more contextual and human-centric for better relevance.

  **Try This:**

  - Enable People data in Agent Builder
  - Create an agent to answer org-specific directory questions
  - Test in Microsoft Teams


  **Why this matters:**


  **Business Impact:** Improves accuracy and personalization in enterprise workflows.


  **Personal Impact:** Users get tailored answers courtesy of context-rich data.


  **Additional resources:**


  **Learn:**


  [Add knowledge sources to your declarative agent in Microsoft 365 Copilot](https://learn.microsoft.com/en-us/microsoft-365-copilot/extensibility/agent-builder-add-knowledge)

### PowerPoint

- **Use your organization's approved assets in Copilot presentations** \[Mac, Windows, Web\]

  Create branded PowerPoint slides by pulling images and templates from your company's SharePoint asset library or Templafy integration.

  **Roadmap ID:** [496366](https://www.microsoft.com/microsoft-365/roadmap?msockid=2484525e9a9b66d4330b47329bb667c9&filters=&searchterms=496366)

  **Details:**

  **What changed:** PowerPoint Copilot integrates with SharePoint Organization Asset Library and Templafy for approved, compliant visuals.

  **Why:** Ensures quality designs aligned with corporate branding guidelines.

  **Try This:**

  - Configure SharePoint OAL or Templafy in Microsoft 365
  - Ask Copilot: "Create a marketing update deck using brand imagery."


  **Why this matters:**


  **Business impact:**: Maintains brand identity across all content.


  **Personal Impact:** Saves design time by eliminating manual asset searching.


  **Additional resources:**


  **Learn:**


  [Create an organization assets library](https://learn.microsoft.com/en-us/sharepoint/organization-assets-library)

## December 10, 2025

Updates released between November 25, 2025, and December 10, 2025.

### Microsoft 365 Copilot app

- **Create polished videos faster with seamless editing and brand customization** \[Web\]

  Turn text prompts or PowerPoint, Word, and PDF files into high-quality videos. Create professional videos quickly with easier editing, brand integration, and media customization.

  **Roadmap ID:** [501560](https://www.microsoft.com/microsoft-365/roadmap?msockid=2484525e9a9b66d4330b47329bb667c9&filters=&searchterms=501560)

  **Details:**

  **What changed:** With the upgraded AI Video Creator in Microsoft 365 Copilot, use these new capabilities:

  - Transcript-based editing for greater control.
  - Access to your assets from OneDrive to update stock media.
  - Natural-sounding voiceovers for more authentic narration.
  - Brand color integration from Brand Kit.
  - A redesigned, scene-based structure for streamlined storytelling.
  - A cleaner editing experience for faster, intuitive workflows.


  **Why:** Video is a powerful medium, but creating professional-quality content is often time-consuming and technically challenging. This update removes roadblocks, so teams create compelling videos in a fraction of the time, using assets and brand elements they already have.


  **Try this:**


  - In Microsoft 365 Copilot, select Create and upload a Word, PDF, or PowerPoint file to generate your first video draft.
  - Click on a sentence in the transcript to cut or move sections without timeline complexity.
  - Add your official colors from Brand Kit, and swap generic visuals with your OneDrive media for a branded look.


  **Why this matters:**


  **Business Impact:** Reduce production bottlenecks and costs by empowering employees to create professional videos for training, marketing, or executive updates without third-party agencies.


  **Personal Impact:** Focus on the story, save hours on content creation, and eliminate the need for advanced video editing.


  **Additional resources:**


  **Support:**


  [Create a video with the Microsoft 365 Copilot app](https://support.microsoft.com/topic/create-a-video-with-the-microsoft-365-copilot-app-4edd41f6-a7ad-47d5-9a55-3fd25622c9f8)

### Microsoft 365 Copilot extensibility

- **Access custom engine agents in multiple apps** \[Web\]

  Use custom engine agents in Word and Excel for a unified Copilot experience everywhere you work.

  **Roadmap ID:** [481136](https://www.microsoft.com/microsoft-365/roadmap?msockid=2484525e9a9b66d4330b47329bb667c9&filters=&searchterms=481136)

  **Details:**

  **What changed:** You can see more available custom engine agents across key Microsoft 365 surfaces.

  **Why:** Power users and developers can experience reduced fragmentation and improved workflow consistency.

  **Try this:**

  - In Outlook, activate a custom agent for summarizing incoming correspondence based on enterprise policies.


  **Why this matters:**


  **Business Impact:** Extends the value of custom Copilot agents across the Microsoft 365 ecosystem.


  **Personal Impact:** Offers a seamless experience without switching apps or rebuilding context.

### Microsoft 365 Copilot Studio

- **Better security insights help you build confidently** \[Web\]

  Makers can now see an agent's detailed protection status and actionable recommendations in Copilot Studio.

  **Details:**

  **What changed:** Enforce protections accurately with a richer visualization of security posture for agents.

  **Why:** Creators are empowered to manage compliance and proactively minimize risks.

  **Try this:**

  - In Copilot Studio, check the security summary for your agent and apply suggested actions to meet policy.


  **Why this matters:**


  **Business Impact:** Maintains compliance without slowing innovation.


  **Personal Impact:** Gives creators peace of mind knowing their agents meet enterprise security standards.


  **Additional resources:**


  **Learn:**


  [Agent runtime protection status](https://learn.microsoft.com/en-us/microsoft-copilot-studio/security-agent-runtime-view)

### Microsoft 365 SharePoint

- **Add multiple SharePoint agents in one Teams conversation** \[Web\]

  Include more than one SharePoint agent in a single Teams chat, meeting, or channel. Teams and SharePoint now work together better for smarter collaboration.

  **Roadmap ID:**[481136](https://www.microsoft.com/microsoft-365/roadmap?msockid=2484525e9a9b66d4330b47329bb667c9&filters=&searchterms=481136)

  **Details:**

  **What changed:** Teams supports multiple SharePoint agents in a single group chat or channel.

  **Why:** Experience richer scenarios where multiple libraries or sites provide simultaneous insights.

  **Try this:**

  - In your project channel, add two different SharePoint agents to get instant answers about separate libraries.


  **Why this matters:**


  **Business Impact:** Keeps all content conversation in context, reducing silos across different sites.


  **Personal Impact:** Stay focused without the need to use multiple chats or apps to gather information.


  **Additional resources:**


  **Support:**


  [Share an agent from SharePoint in Teams](https://support.microsoft.com/office/share-an-agent-from-sharepoint-in-teams-6dcbf7b5-8c13-44e5-a68a-dbd71fb76ad3)

### Viva Glint

- **Multilingual support in Copilot for Viva Glint** \[Web\]

  Copilot in Viva Glint now understands and responds in multiple languages, helping employees interact in their preferred language.

  **Roadmap ID:** [508531](https://www.microsoft.com/microsoft-365/roadmap?filters=&searchterms=508531)

  **Details:**

  **What changed:** Copilot for Viva Glint detects the language of a user's input and responds in that same language.

  **Why:** Global teams often face challenges when a tool's language support is limited. This update improves accessibility and usability, enabling employees to share feedback or gain insights without language barriers.

  **Try this:**

  - Type a prompt in your preferred language within Viva Glint Copilot.
  - Review the response to confirm it matches the language you used.
  - Share this experience with multilingual teams to streamline feedback processes.


  **Why it Matters:**


  **Business Impact:** Enhances inclusivity and compliance, making it easier to manage employee feedback across multiple regions.


  **Personal Impact:** Saves time and reduces friction for employees who can now interact with Copilot in the language they're most comfortable with.

## November 25, 2025

Updates released between November 12, 2025, and November 25, 2025.

### Microsoft 365 admin center

- **Reassign agent ownership with full control** \[Windows, Web\]

  Admins can now transfer ownership of shared agents, granting the new owner full edit and delete permissions and revoking all access from the previous owner.

  ****Roadmap ID:**** [502867](https://www.microsoft.com/microsoft-365/roadmap?msockid=2484525e9a9b66d4330b47329bb667c9&filters=&searchterms=502867)

  ****Details:****

  **What changed:** Ownership reassignment capabilities are now live in Microsoft 365 admin center, with edits propagating to agent files and associated content.

  ****Why:**** Helps maintain governance when employees leave roles or teams without disrupting workflows.

  **Try this:**

  - From admin center, select a shared agent > choose **Reassign Owner** > confirm access update.


  **Why this matters:**


  **Business Impact:** Reduces compliance and business continuity risks during staff transitions.


  **Personal Impact:** Admins can easily manage lifecycle changes without escalating to engineering teams.


  **Additional resources:**


  **Learn:**


  [Reassign an agent's owner with PowerShell](https://learn.microsoft.com/en-us/power-platform/release-plan/2025wave2/microsoft-copilot-studio/reassign-agents-owner-powershell)

- **Restrict org-wide agent sharing for better governance** \[Web\]

  Manage who can create org-wide sharing links for Copilot Studio agents to maintain tighter organizational control.

  ****Roadmap ID:**** [500376](https://www.microsoft.com/microsoft-365/roadmap?filters=&searchterms=500376)

  ****Details:****

  **What changed:** New admin control blocks or enables org-wide visibility for Copilot agents.

  ****Why:**** Prevents accidental overexposure of sensitive workflows while allowing flexibility for approved agents.

  **Try this:**

  - In admin center, update **Sharing Settings** to limit org-wide agent links to specific roles or groups.


  **Why this matters:**


  **Business Impact:** Reduces risk of unauthorized data exposure.


  **Personal Impact:** Gives admins full confidence before rolling out custom agents at scale

### Microsoft 365 Copilot app

- **Customize audio overviews for Copilot notebooks** \[Web\]

  Personalize the content and tone of audio summaries from your Copilot notebooks by using natural language input.

  ****Roadmap ID:**** [499150](https://www.microsoft.com/microsoft-365/roadmap?filters=&searchterms=499150)

  ****Details:****

  **What changed:** Notebook audio overviews are now creator-driven with prompt-based customization.

  ****Why:**** Supports diverse use cases-like executive briefings or quick-learning sessions-without extra editing work.

  **Try this:**

  - Type: *"Create an upbeat 2-minute audio summary focused on key sales drivers."*


  **Why this matters:**


  **Business Impact:** Enhances the value of notebooks for communication and leadership updates.


  **Personal Impact:** Saves time creating engaging summaries without additional tools.


  **Additional resources:**


  **Learn:**


  [Get an audio overview of your notebook with Microsoft 365 Copilot Notebooks](https://support.microsoft.com/topic/get-an-audio-overview-of-your-notebook-with-microsoft-365-copilot-notebooks-a22df989-b9cd-47fb-abac-e888d8f10cd9)

### Microsoft 365 Copilot Chat

- **Access shared mailboxes in Copilot Chat** \[Android, Windows, iOS, Mac, Web\]

  Copilot Chat now connects to shared mailboxes, so team-based conversations are more informed and collaborative.

  ****Roadmap ID:**** [488797](https://www.microsoft.com/microsoft-365/roadmap?msockid=2484525e9a9b66d4330b47329bb667c9&filters=&searchterms=488797)

  ****Details:****

  **What changed:** Users with shared mailbox permissions can ground Copilot responses in shared mail content, just like their own emails.

  ****Why:**** Eliminates context gaps in team workflows and improves shared visibility on projects.

  **Try this:**

  - Tell Copilot: *"Summarize recent emails in [mailbox@domain.com](mailto:mailbox@domain.com) mailbox."*
  - Tell Copilot: *"List all the emails around `topic` from < mailbox@domain.com > mailbox."*


  **Why this matters:**


  **Business Impact:** Ensures customer responses or project updates aren't missed when responsibility spans multiple team members.


  **Personal Impact:** Reduces copying and manual email checks across shared accounts-Copilot does it for you.


  **Additional resources:**


  [Use Copilot in shared mailboxes and delegate mailboxes](https://support.microsoft.com/topic/use-copilot-in-shared-mailboxes-and-delegate-mailboxes-3e7e5130-eabe-4c19-94ea-117b2a4c14d6)

- **Find files faster with improved Copilot Chat filters** \[Windows, Web\]

  Use new file type and people refiners in Copilot Chat to quickly get to the right file without sifting through results.

  ****Roadmap ID:**** [481136](https://www.microsoft.com/microsoft-365/roadmap?filters=&searchterms=481136)

  ****Details:****

  **What changed:** Introduced filters for file types and collaborators in Copilot Chat's CIQ Files tab.

  ****Why:**** Cuts down time spent filtering manually, especially in large file repositories.

  **Try this:**

  - In chat, search: *"Quarterly report"* → Filter by **Excel** and collaborator name.


  **Why this matters:**


  **Business Impact:** Improves productivity and reduces meeting prep time.


  **Personal Impact:** Less frustration-find what you need in seconds.

- **Talk to Copilot with voice for faster hands-free work** \[Android, Windows, iOS, Mac, Web\]

  Speak to Copilot naturally on mobile or desktop to prepare for meetings, brainstorm ideas, or catch up on work-hands-free and grounded in work data.

  **Roadmap ID:** [481138](https://www.microsoft.com/microsoft-365/roadmap?msockid=2484525e9a9b66d4330b47329bb667c9&filters=&searchterms=481138)

  ****Details:****

  **What changed:** Copilot now supports voice input, enabling natural, conversational interactions in the Microsoft 365 Copilot app on mobile, desktop and the web and across Microsoft 365 apps, starting with Outlook, Word and PowerPoint.

  ****Why:**** Professionals need faster, more intuitive ways to engage with AI during their flow of work, especially when multitasking or on the move.

  **Try this:**

  - Say: *"Confirm the agenda and attendee list for my next meeting"*.
  - Try: *"Create a quick list of next steps from my recent meeting notes."*
  - Ask: *"Summarize this document in five key points."*


  **Why this Matters:**


  **Business Impact:** Voice drives productivity and inclusivity through natural interactions that increase engagement, accelerate task completion and reduce downtime.


  **Personal Impact:** Work more comfortably and naturally while saving time, gaining efficiency and giving you the flexibility to use Copilot on the go or at your desk.


  **Additional resources:**


  [Get started with voice features in Microsoft 365 Copilot](https://support.microsoft.com/topic/get-started-with-voice-features-in-microsoft-365-copilot-9262968d-565e-470c-a04b-991eb8e0d1ea)

### Microsoft 365 Copilot extensibility

- **Enhanced search in Agent Store for easier discovery** \[Windows, Web\]

  Finding the right agents in the Copilot Agent Store just got faster and smarter. Enjoy a streamlined search experience with typeahead suggestions and a clean results page-making it simple to locate exactly what you need without wasted time.

  ****Roadmap ID:**** [502617](https://www.microsoft.com/microsoft-365/roadmap?filters=&searchterms=502617)

  ****Details:****

  **What changed:** The Agent Store now includes enhanced search capabilities featuring a responsive drop-down menu, typeahead functionality for quick suggestions as you type, and a dedicated search results page for improved clarity.

  ****Why:**** Customers need a quicker, more intuitive way to explore and find agents. By reducing friction in discovery, you can deploy and extend Copilot solutions with less effort and greater confidence.

  **Try this:**

  - Start typing an agent name in the search bar to see type ahead suggestions instantly.
  - Use the new full results page for a complete view of matching agents.


  **Why this matters:**


  **Business Impact:** Accelerate adoption by making it easy for teams to find and integrate the right Copilot tools quickly, boosting productivity across the organization.


  **Personal Impact:** Save time and reduce frustration with simple, intuitive search that helps you get back to meaningful work faster.

- **Export detailed agent metadata for better governance** \[Web\]

  Inventory exports now include richer metadata like capabilities, data sources, and creator details-empowering better auditing and lifecycle control.

  ****Roadmap ID:**** [502878](https://www.microsoft.com/microsoft-365/roadmap?filters=&searchterms=502878)

  ****Details:****

  **What changed:** Added expanded metadata fields to Microsoft 365 admin center's agent export.

  ****Why:**** Provides admins with transparency over how agents are built, what they access, and by whom.

  **Try this:**

  - Start agent inventory and filter by **Created By** or **Data Sources** to review compliance.


  **Why this matters:**


  **Business Impact:** Strengthens governance for AI usage across the organization.


  **Personal Impact:** Saves admins from chasing multiple tools for visibility-everything is in one export.


  **Additional resources:**


  **Learn:**


  [Export to Excel](https://learn.microsoft.com/en-us/microsoft-365/admin/manage/agent-registry#export-to-excel)

- **Unified permissions management for agents** \[Windows, Web\]

  View detailed permissions for each Copilot agent in one place-including app dependencies, delegated permissions, and associated risks. Admins can grant consent directly, simplifying governance and deployment.

  ****Roadmap ID:**** [502617](https://www.microsoft.com/microsoft-365/roadmap?filters=&searchterms=502617)

  ****Details:****

  **What changed:** Unified Permissions Management now provides a clear view of all required applications, delegated permissions, and associated risk levels from a central console.

  ****Why:**** Helps admins ensure security and compliance while reducing friction in agent approval workflows.

  **Try this:**

  - Go to the Permissions tab in Microsoft 365 admin center to review and approve agent permissions.
  - Filter by risk level to prioritize oversight where needed.


  **Why This Matters:**


  **Business Impact:** Strengthens compliance and governance while accelerating agent deployment.


  **Personal Impact:** Simplifies decision-making for IT teams, saving hours of manual checks.


  **Additional resources:**


  **Learn:**


  [Agent Registry in the Microsoft 365 admin center](https://learn.microsoft.com/en-us/microsoft-365/admin/manage/agent-registry)

### Microsoft 365 Copilot Studio

- **Control org-wide agent sharing from one place** \[Web\]

  Admins now have granular control over whether agents built in Agent Builder can be shared with links that work for anyone in the organization, ensuring policies are followed.

  ****Details:****

  **What changed:** Admins can restrict or disable organization-wide sharing of agents built in Agent Builder.

  ****Why:**** This strengthens governance, prevents agent sprawl, and supports safe adoption at scale.

  **Try this:**

  - In Microsoft 365 admin center, go to Agents > Settings > Sharing and configure who can share agent links that work for anyone in the organization.


  **Why this matters:**


  **Business Impact:** Strengthens governance, prevents oversharing, and supports compliance as agent adoption needs evolve.


  **Personal Impact:** Gives admins confidence and transparency when scaling adoption. Makers receive clear guidance on enforced admin sharing policies


  **Additional resources:**


  **Learn:**


  [Sharing](https://learn.microsoft.com/en-us/microsoft-365/admin/manage/agent-settings#sharing)


  **Learn:**


  [Share an agent](https://learn.microsoft.com/en-us/microsoft-365-copilot/extensibility/copilot-studio-lite-share-manage-agent#share-an-agent)


  **Demo:**


  [Admin control for org-wide agent sharing links](https://microsoft-my.sharepoint-df.com/personal/sophieroy_microsoft_com/_layouts/15/stream.aspx?id=%2Fpersonal%2Fsophieroy%5Fmicrosoft%5Fcom%2FDocuments%2FRecordings%2FDemo%20Admin%20control%20for%20org%2Dwide%20agent%20sharing%20links%2D20250926%5F155245%2DMeeting%20Recording%2Emp4&nav=eyJyZWZlcnJhbEluZm8iOnsicmVmZXJyYWxBcHAiOiJTdHJlYW1XZWJBcHAiLCJyZWZlcnJhbFZpZXciOiJTaGFyZURpYWxvZy1MaW5rIiwicmVmZXJyYWxBcHBQbGF0Zm9ybSI6IldlYiIsInJlZmVycmFsTW9kZSI6InZpZXcifX0&referrer=StreamWebApp%2EWeb&referrerScenario=AddressBarCopied%2Eview%2Ea632fb0d%2D5e4c%2D4501%2D92a6%2D1c16c4381542&ct=1764029038871&or=Teams%2DHL&ga=1&gaS=47&isDarkMode=true)


  **Blogs:**


  [Manage and govern at scale](https://www.microsoft.com/microsoft-copilot/blog/copilot-studio/whats-new-in-copilot-studio-october-2025/#manage-and-govern-at-scale)

### Microsoft 365 PowerPoint

- **Reference Loop or Page in presentations** \[Mac, Windows, Web\]

  When building a presentation with Copilot, you can now pull in content from Loop components or pages for fully integrated and up-to-date slides.

  ****Roadmap ID:**** [500864](https://www.microsoft.com/microsoft-365/roadmap?msockid=2484525e9a9b66d4330b47329bb667c9&filters=&searchterms=500864)

  ****Details:****

  **What changed:** Copilot for PowerPoint supports referencing Loop components and pages across PC, Mac, and web.

  ****Why:**** Ensures your presentations reflect the latest collaborative content without manual copy-paste.

  **Try this:**

  - **Ask Copilot:** *"Create a status update deck using the project details from our Loop page."*


  **Why this matters:**


  **Business Impact:** Align updates across teams without tedious content migration.


  **Personal Impact:** Save time by reusing the content you already co-created, in just one step.

### Microsoft 365 SharePoint

- **Copilot skills for smarter SharePoint administration** \[Web\]

  Use Copilot to get step-by-step guidance for admin tasks and advanced site searches based on multiple criteria-all from the SharePoint admin center.

  ****Roadmap ID:**** [501455](https://www.microsoft.com/microsoft-365/roadmap?msockid=2484525e9a9b66d4330b47329bb667c9&filters=&searchterms=501455)

  ****Details:****

  **What changed:** Added two major skills:

  - Guided task instructions \(for example, fixing over-permissioned sites\)
  - Multi-criteria search for sites \(for example, inactive + shared externally\)


  ****Why:**** Improves efficiency and accuracy in managing large SharePoint environments.


  **Try this:**


  - **Ask Copilot:** *"Find all inactive sites over 60 days shared externally."*
  - **Prompt:** *"Show me steps to reduce permissions for over-shared sites."*


  **Why this matters:**


  **Business Impact:** Reduces security risk and speeds workload management.


  **Personal Impact:** Saves admins hours of navigating settings-answers are instant.


  **Additional resources:**


  **Learn:**


  [Copilot skills in SharePoint admin centers](https://learn.microsoft.com/en-us/SharePoint/copilot-skills-sharepoint-admin-centers)

## November 12, 2025

Updates released between October 28, 2025, and November 12, 2025.

### Copilot extensibility

- **Custom Agents can be used from inside of Office Applications** \[Web\]

  Supporting Custom Engine Agents inside Office applications offers numerous advantages that significantly enhance user experience and productivity. Firstly, it allows for highly tailored automation and customization, enabling users to create and deploy agents that cater specifically to their unique workflows and business needs.

  This flexibility can lead to more efficient processes and reduced manual effort. Secondly, Custom Engine Agents can integrate seamlessly with existing Office functionalities, providing a cohesive and unified user experience. This integration ensures that users can leverage the full power of Office applications while benefiting from the specialized capabilities of their custom agents.

  Additionally, these agents can help in automating repetitive tasks, improving accuracy, and freeing up time for more strategic activities. Overall, the support for Custom Engine Agents within Office applications empowers users to optimize their work environment, drive innovation, and achieve higher levels of productivity. [Learn more](https://learn.microsoft.com/en-us/microsoft-365-copilot/extensibility/agents-overview#custom-engine-agents).

### Copilot Studio

- **Quarantine and block unsecured agents** \[Web\]

  Improve security and compliance by using PowerShell to quarantine Copilot agents that don't meet policy requirements. This gives admins more control to prevent risks while investigating and resolving issues without disrupting business operations. [Learn more](https://learn.microsoft.com/en-us/microsoft-copilot-studio/admin-quarantine-api).

### Excel

- **Build and analyze surveys with ease using Surveys Agent** \[Windows, Mac, Web\]

  Let Surveys Agent handle the heavy lifting-from writing questions to launching surveys and breaking down results. It's like having a professional researcher inside Copilot, helping you make quick, data-driven decisions. [Learn more](https://aka.ms/SurveysAgentAvailable).

### Microsoft 365 admin center

- **Block SharePoint agents from Agents and connectors page** \[Web\]

  Administrators have the ability to oversee SharePoint agents as shared applications within the Agents & connectors section \(formerly known as integrated apps\) of the Microsoft 365 admin center. They can access a list of all shared SharePoint agents and have the option to block or unblock agents from being utilized on M365 Copilot. [Learn more](https://learn.microsoft.com/en-us/sharepoint/manage-access-agents-in-sharepoint).
- **New Enhancements in Organizational Data Ingestion in Microsoft 365** \[Web\]

  Experience a powerful upgrade with new attribute access and mapping, connectors, and a dedicated admin role. Streamline data ingestion from multiple sources to Viva Insights and Glint, simplifying data management and enhancing workflow efficiency.

### Microsoft 365 Copilot Chat

- **Iterate on images with multi-turn editing** \[Windows, Mac, Web\]

  Copilot Chat now makes visual creation more flexible and intuitive. Upload reference images, edit them step by step, and maintain consistency across versions-perfect for refining designs for presentations, social posts, or print.
- **RSVP status-based meeting search in Copilot Chat** \[Android, Windows, Web\]

  **Roadmap:** [499429](https://www.microsoft.com/microsoft-365/roadmap?filters=&searchterms=499429)

  Quickly find meetings based on RSVP status-either your own or others'. This feature helps you stay organized by surfacing RSVP details for upcoming events, so you can track commitments and follow up with attendees.

  **Try this:**

  Open Microsoft 365 Chat. Enter queries like:

  - "Meetings I accepted this week"
  - "Meetings I have not RSVPed this week"
  - "Who all have accepted the Scrum meeting?"


  View results showing RSVP details for yourself or attendees.


  **Business or Personal Impact:**


  **Business:** Improves meeting management and accountability by enabling quick visibility into attendee responses, reducing missed follow-ups.


  **Personal:** Helps you stay on top of your schedule and commitments without manually checking each calendar invite.

- **Updated UI for the Copilot Chat Navigation Pane in Teams** \[Web\]

  The navigation pane has been repositioned from the right side to the left, offering a more intuitive layout. Despite the shift, it continues to host agents and conversation history, ensuring continuity in user experience. This redesign introduces new features, including access to the "All Conversations" page, which provides a comprehensive view of chat history. The change aims to enhance usability and streamline navigation within Copilot Chat.

### Microsoft 365 Copilot Studio

- **Upload up to 1000 files for SharePoint and OneDrive training** \[Web\]

  Makers can now upload up to 1000 documents per agent when building custom Copilot experiences-five times the previous limit-making it easier to create well-informed, specialized solutions. [Learn more](https://learn.microsoft.com/en-us/power-platform/release-plan/2025wave1/microsoft-copilot-studio/use-up-1000-files-per-agent-sharepoint-onedrive-uploads).

### Outlook

- **Intelligent Draft Agenda with Copilot** \[Web\]

  Meetings are more successful with agendas. They align everyone on meeting goals, get the right people to attend, and keep discussions focused, leading to more productive and effective work. With Intelligent Draft Agenda, Copilot helps you create agendas for your meetings and streamlines your workday. When creating or editing an event in Calendar, Copilot will propose an agenda, ready for you to review, edit, and send as part of your meeting invite. [Learn more](https://support.microsoft.com/topic/31a44dfa-62bb-4751-82c4-14327a26759f?preview=true).

### PowerPoint

- **Create new presentations without overwriting your original** \[Windows, Mac, Web\]

  When you use Copilot to generate a presentation from an existing one, it now creates a separate file-keeping your original content safe for future use. Perfect for creating tailored decks without starting from scratch. [Learn more](https://support.microsoft.com/office/create-a-new-presentation-with-copilot-in-powerpoint-3222ee03-f5a4-4d27-8642-9c387ab4854d).

### Viva Insights

- **Copilot Chat \(Web\) in Teams & Outlook metrics** \[Windows, Web\]

  Copilot Analytics users can now view metrics about their Copilot Chat \(Web\) usage in Teams and Outlook. These updates enable users to better understand both active usage and action counts in Teams and Outlook and will be available in the Copilot Dashboard, as well as with additional query support. [Learn more](https://learn.microsoft.com/en-us/viva/insights/advanced/reference/metrics).

## October 28, 2025

Updates released between October 15, 2025, and October 28, 2025.

### Copilot extensibility

- **Static tab for custom agents in Teams meetings** \[Windows, Web\]

  Developers can now add static tabs in their custom engine agents using Teams Toolkit, enhancing experiences during meetings and calls.

### Microsoft 365 Copilot

- **Private previews in shared page edits** \[Web\]

  After edits in shared pages, view suggestions as private previews to refine and finalize content before public application.

### Microsoft 365 Copilot Chat

- **Focus mode in Teams** \[Web\]

  Enhance your concentration with Focus Mode in Teams, which hides unnecessary UI elements and provides alerts when launching the full app from chat.
- **Stay informed with email alerts for scheduled prompts",** \[Web\]

  Get notified when your scheduled Copilot prompts finish running. Email notifications ensure you never miss results and can act on insights right away-no need to keep checking manually. [Learn more](https://learn.microsoft.com/en-us/power-platform/admin/recurring-copilot-prompts).

### Microsoft Planner

- **Copilot faster with new Planner button** \[Web\]

  A new floating action button \(FAB\) gives you quick, one-click access to the Project Manager Agent, making it easy to launch Copilot or start a chat without losing your place in your plan. [Learn more](https://techcommunity.microsoft.com/blog/plannerblog/what%E2%80%99s-new-in-microsoft-planner-%E2%80%93-august-2025/4449301).
- **Get a project manager agent in all premium plans",** \[Windows, Web\]

  The project manager agent is now included in all premium Planner plans. It helps you move work forward by creating plans from goals, executing tasks, and acting on feedback-all with less manual effort.
- **Get task recommendations grounded in real-time web data** \[Web\]

  Copilot's Project Manager Agent now includes web-grounded responses with source links, ensuring task updates and recommendations are timely, credible, and actionable.

### Outlook

- **Expanded coverage and Improvements to Preparing for Meetings with Copilot** \[Windows, Web\]

  Preparing for meetings can be time and effort-intensive. New enhancements to Copilot's meeting preparation experience help streamline the process. Directly within the Outlook meeting event form, Copilot can now proactively generate key insights to help you prepare for specific meetings. Copilot also suggests additional ways that it can help you prepare, from finding the pre-reads to learning more about the meeting's intended outcome. User can then continue the conversation via chat, and get answers to additional questions that are top-of-mind. In addition, Copilot now supports all meeting types - including 1:1 meetings - via the meeting preparation experience. [Learn more](https://support.microsoft.com/topic/prepare-for-your-meeting-with-copilot-f23326fc-7721-45f1-875e-23e77aaf3d89).

### PowerPoint

- **Copilot now offers an on-canvas experience for generating speaker notes** \[Mac, Web, iOS\]

  Now, Copilot in PowerPoint offers an on-canvas experience to generate speaker notes in place of the previous chat experience. [Learn more](https://support.microsoft.com/topic/add-speaker-notes-to-your-presentations-using-copilot-7139266b-8a1d-4056-8e30-4edcc4d80873).
- **PPT Copilot now offers an on-canvas experience for translating presentation** \[Mac, Web, iOS\]

  Now, when creating a presentation using Copilot from an existing presentation, it creates the new presentation in a new file without affecting the original presentation. [Learn more](https://support.microsoft.com/topic/rewrite-text-with-copilot-in-powerpoint-d70b140b-bb3f-46b7-be64-ceec526a8dcd#:%7E:text=Select%20the%20textbox%20containing%20the%20text%20you%20want,for%20general%20improvements%20in%20grammar%2C%20spelling%2C%20and%20clarity.).

### Teams

- **Teams chats in ContextIQ** \[Web\]

  Enhance Copilot Chat prompts by searching and selecting Teams chats within ContextIQ, streamlining your workflow and improving context accuracy. [Learn more](https://support.microsoft.com/topic/using-context-iq-to-refer-to-specific-files-people-and-more-in-microsoft-365-copilot-and-copilot-chat-272ac2c1-c5f7-49c9-8a42-2a8a87846fa0).

### Viva Insights

- **Weekly user insights in Copilot Studio agent reports",** \[Windows, Mac, Web\]

  Copilot Studio reports now include weekly active user counts and provide aggregated data on a weekly basis for consistency across reporting. These updates make it easier to track engagement trends for planning and adoption. [Learn more](https://learn.microsoft.com/en-us/viva/insights/advanced/analyst/templates/copilot-studio-agents).

## October 15, 2025

Updates released between September 30, 2025, and October 15, 2025.

### Copilot extensibility

- **Context-aware search ranking** \[Windows, Web\]

  Search now delivers more personalized results by using user context and engagement signals, enhanced by the Microsoft 365 Copilot extension. This ensures that search results are intuitive and relevant. [Learn more](https://learn.microsoft.com/en-us/microsoftsearch/crossover-browser).

### Microsoft 365 admin center

- **Harmful content protection toggle** \[Web\]

  Admins can now control how users interact with harmful content protection settings in Microsoft 365 Copilot Chat. This is crucial for specialized roles like legal or investigative teams that may need exposure to sensitive content. [Learn more](https://learn.microsoft.com/en-us/microsoft-365/copilot/harmful-content-protection-copilot-chat).
- **Historical Data Upload Support in Organizational Data in Microsoft 365** \[Web\]

  Enhance your data management by uploading historical HR data manually via CSV files. If the historical option is selected, admins can assign an effective date for precise processing by apps like Viva Insights. This ensures consistent and accurate data across Microsoft 365 and Viva apps. [Learn more](https://learn.microsoft.com/en-us/viva/import-orgdata#step-5--make-retroactive-updates-to-existing-data).
- **Manage table list views with security roles** \[Web\]

  Enhance security and streamline operations by managing table list views according to specific security roles. This feature empowers administrators with increased control and customization over data access. [Learn more](https://learn.microsoft.com/en-us/power-apps/maker/model-driven-apps/manage-view-access).
- **Prepurchase capacity packs for chat** \[Web\]

  Admins can apply pre-purchased message capacity packs to Microsoft 365 Copilot Chat and other agent scenarios before incurring pay-as-you-go charges, optimizing budget management. [Learn more](https://learn.microsoft.com/en-us/microsoft-365/copilot/pay-as-you-go/copilot-capacity-packs).

### Microsoft 365 Copilot Chat

- **Create new images using reference uploads** \[Windows, Mac, Web\]

  Enhance image creation by uploading reference images in Copilot Chat, using them as creative foundations for new visuals.
- **Image generation with multiple aspect ratios** \[Windows, Mac, Web\]

  Generate images in various aspect ratios to suit any need, from social media to presentations, with landscape, portrait, and square options in Copilot Chat.
- **Inline citations and references in side pane** \[Web\]

  Improve clarity and transparency by replacing numeric citations with source-based citation pills. Access all sources, both cited and uncited, directly in the side pane for a better credibility assessment and exploration.

### Microsoft Loop

- **New file extension for Copilot pages** \[Web\]

  Introducing ".page", a new extension for Copilot pages that supports admin toggles, sensitivity labels, and compliance features just like ".loop". [Learn more](https://support.microsoft.com/topic/get-started-with-microsoft-365-copilot-pages-6674bd51-9ff5-42c4-9256-44d9428a726f).

## September 30, 2025

Updates released between September 16, 2025, and September 30, 2025.

### Copilot extensibility

- **Enable ISV discovery through connector catalog** \[Web\]

  Discover Independent Software Vendor \(ISV\) built copilot connectors seamlessly through the connector catalog in the admin center, enhancing integration and functionality across your enterprise applications.
- **Pin agents for tenant-wide visibility** \[Web\]

  Admins can now pin Copilot agents for all users or specific groups within their tenant, ensuring greater accessibility and relevance of popular agents for user tasks. [Learn more](https://learn.microsoft.com/en-us/microsoft-365/admin/manage/manage-pinning-agents).

### Microsoft 365 admin center

- **Usage reports for Copilot search** \[Android, Windows, iOS, Mac, Web\]

  Administrators gain insights into organizational adoption of Copilot search with new usage reports. Track total search queries, assess trends, and analyze user activity to drive effective adoption strategies. [Learn more](https://learn.microsoft.com/en-us/microsoft-365/admin/activity-reports/microsoft-365-copilot-search-usage).

### Microsoft 365 Copilot Chat

- **Copilot Chat now understands attached files like Word, Excel, PowerPoint, PDF, Text, JSON, and XML.** \[Android, Windows, iOS, Mac, Web\]

  Users can gather insights not only from the email content but also from attached files, enabling comprehensive context understanding.
- **Copilot Chat summarization in Microsoft Edge context menu** \[Web\]

  Unpack web pages and ask questions swiftly with a new Copilot Chat summarization option in the Edge context menu for efficient browsing. [Learn more](https://support.microsoft.com/topic/using-microsoft-copilot-in-edge-at-work-012b3674-bab8-4f99-8585-c961dac68642).
- **Easily select meeting series in Copilot Chat** \[Windows, Web\]

  Effortlessly choose meeting series and related instances directly from the Context IQ \(CIQ\) menu to include in your Copilot Chat prompts.
- **Support for analyzing images in uploaded files** \[Windows, Web\]

  Analyze embedded images within PDF, DOCX, and PPTX files uploaded to Copilot. Ask Copilot to interpret image content, such as "analyze the image on page 4," and receive insights based on the visual data.
- **Upload multiple images for creative prompts** \[Android, iOS, Web\]

  Now upload multiple images into Copilot Chat prompts at once to enhance creative reasoning and generate new content with varied inspiration.

### PowerPoint

- **Copilot generates the new presentation in a new file when starting from an existing presentation** \[Web\]

  Now, when creating a presentation using Copilot from an existing presentation, it creates the new presentation in a new file without affecting the original presentation. [Learn more](https://support.microsoft.com/office/create-a-new-presentation-with-copilot-in-powerpoint-3222ee03-f5a4-4d27-8642-9c387ab4854d).
- **Seamlessly add topics with Copilot** \[Mac, Web, Windows\]

  Enhance your presentations by adding new topics with slides via Copilot, ensuring consistency in look and feel with existing content. [Learn more](https://support.microsoft.com/topic/add-topics-to-your-existing-powerpoint-presentation-with-copilot-7439e3d7-5b7f-4886-8d01-5e7f285fd99b?preview=true).

## September 16, 2025

Updates released between September 3, 2025, and September 16, 2025.

### Copilot extensibility

- **Improve Response accuracy when handling large files in File Upload/CIQ.** \[Windows, Web\]

  Experience improved summaries and increased accuracy when querying long documents and PDFs. Copilot efficiently distills information, helping you extract insights and answer questions faster.
- **ServiceNow Connectors custom URL configuration** \[Windows, Web\]

  Enhance ServiceNow Connectors with customizable URLs for articles, tickets, and catalog items, tailored to organizational preferences. [Learn more](https://learn.microsoft.com/en-us/microsoftsearch/configure-connector#customize-values-for-certain-schema-properties).

### Copilot Studio

- **Analyze ROI of autonomous agents in Analytics tab** \[Web\]

  Use Microsoft Copilot Studio ROI Analytics to define and calculate time or money saved for successful autonomous agent runs, enhancing decision-making efficiency. [Learn more](https://learn.microsoft.com/en-us/microsoft-copilot-studio/analytics-cost-savings).
- **Enhanced search and navigation in Copilot Studio** \[Web\]

  Boost productivity with streamlined search capabilities, allowing quick access to and navigation of elements within your agent. [Learn more](https://learn.microsoft.com/en-us/microsoft-copilot-studio/authoring-search-within-agent).
- **Use managed agents as a starting point for Copilot creation** \[Web\]

  Managed agents in Microsoft Copilot Studio serve as a starting point, allowing makers to leverage industry best practices and design guidelines to ensure a consistent and professional agent experience. Managed agents can be discovered, created, and analyzed by template developers for use by agent makers in your organization. With managed agents, you can quickly set up an agent so you can spend more time customizing your agent's logic and functionality. This streamlined approach not only speeds up the development process but also helps organizations quickly adapt to changing business requirements and improve overall operational efficiency. [Learn more](https://learn.microsoft.com/en-us/microsoft-copilot-studio/authoring-install-agent).

### Microsoft 365 admin center

- **Admins can easily manage orphaned agents with comprehensive lifecycle functionality** \[Windows, Web\]

  Admins can effectively manage the lifecycle of ownerless agents. They can easily filter, identify, block, or delete agents that are no longer associated with an owner, ensuring a streamlined and efficient workflow.
- **Copilot Search management under Copilot controls** \[Web\]

  Enable administrators to configure, customize, and measure Copilot Search across their organization. This feature provides centralized tools to manage search connectors, tailor search experiences to organizational needs, and gain actionable insights into adoption, usage patterns, and content engagement. Designed to enhance productivity and maximize the value of Microsoft 365 Copilot, it supports both setup and ongoing optimization of enterprise search experiences. [Learn more](https://learn.microsoft.com/en-us/microsoft-365/copilot/microsoft-365-copilot-search-admin-experience).

### Microsoft 365 Copilot app

- **Configure format, style, and durations of an audio overview in Copilot Notebooks** \[Web\]

  Choose between a podcast-style format with dual voices or a single voice narration, and customize the style and duration. This gives you more control over how your Notebook is brought to life in audio form. [Learn more](https://support.microsoft.com/topic/get-an-audio-overview-of-your-notebook-with-microsoft-365-copilot-notebooks-a22df989-b9cd-47fb-abac-e888d8f10cd9).
- **Filter past conversations in Copilot Chat** \[Web\]

  We're introducing a chat history filtering capability that empowers users to tailor their view of past conversations. This feature enables users to scope their chat history to a more relevant, workflow-aligned view, helping them quickly surface the chats that matters most. This enhancement is designed to support better context recall.
- **Microsoft 365 Copilot Search** \[Android, Windows, iOS, Web\]

  Copilot Search is the intelligent search experience within the Microsoft 365 Copilot app, designed to deliver fast, secure, and context-aware results across your organization's data. It enables users to search across emails, files, chats, meetings, and even third-party platforms like Salesforce, Jira, and Confluence using natural language queries. [Learn more](https://learn.microsoft.com/en-us/microsoft-365/copilot/microsoft-365-copilot-search).
- **Unified Conversations \(Chat History\) List** \[Web\]

  We've made it easier to find what you need. Users now see a single, streamlined list of all your conversations. No more switching between tabs or wondering where to look for specific conversations. Select a conversation and you'll pick up in the same context and mode as where you left off.

### PowerPoint

- **Copilot Chat creates and enhances presentation content and design** \[Web\]

  Develop comprehensive presentations with depth in content, narrative, and structure, using Copilot's assistance for a polished and compelling delivery. [Learn more](https://learn.microsoft.com/en-us/copilot/overview).

### Word

- **Fix spelling and grammar all at once with Copilot** \[Web\]

  Simplify your editing process with Copilot's one-click solution. Apply all grammar and spelling corrections instantly while retaining the option to review and undo changes you don't want to keep. [Learn more](https://techcommunity.microsoft.com/blog/Microsoft365InsiderBlog/fix-spelling-and-grammar-faster-with-microsoft-365-copilot-in-word-for-the-web/4450625).

## September 3, 2025

Updates released between August 19, 2025, and September 3, 2025.

### Copilot extensibility

- **Add advanced scripting support for ServiceNow catalog** \[Windows, Web\]

  Use advanced scripting for user permissions with the ServiceNow Catalog Graph Connector, allowing more customized and secure experiences. [Learn more](https://learn.microsoft.com/en-us/microsoftsearch/servicenow-catalog-advanced-flow).
- **Get clear sync statuses and error insights** \[Windows, Web\]

  View actionable user sync and ingestion statuses across all states in Microsoft admin center to simplify troubleshooting. [Learn more](https://learn.microsoft.com/en-us/microsoftsearch/connector-view-details).
- **Ground Copilot responses on specific content subsets** \[Windows, Web\]

  Increase precision with Copilot extensibility by using subsets of data connections, ensuring responses are based on the most relevant information. [Learn more](https://learn.microsoft.com/en-us/microsoft-365-copilot/extensibility/copilot-studio-agent-builder-knowledge?branch=main&branchFallbackFrom=pr-en-us-1060).
- **Search and browse connector catalog with ease** \[Windows, Web\]

  Admins can now quickly find connectors across categories and functions in the Copilot extensibility catalogâ€"making integrations simpler than ever. [Learn more](https://learn.microsoft.com/en-us/microsoftsearch/connector-view-details).

### Copilot Studio

- **Discover and install Copilot Studio agents from Dataverse** \[Web\]

  Easily find and install Microsoft-built agents in Copilot Studio using the integrated Power Platform catalog, reducing governance and setup complexities. [Learn more](https://learn.microsoft.com/en-us/microsoft-copilot-studio/authoring-install-agent).

### Microsoft 365 Copilot app

- **Save an audio overview from Copilot Notebooks to OneDrive** \[Web\]

  Save the audio overview that you have generated within a Copilot Notebook to OneDrive so you can download or share with others. [Learn more](https://support.microsoft.com/topic/get-an-audio-overview-of-your-notebook-with-microsoft-365-copilot-notebooks-a22df989-b9cd-47fb-abac-e888d8f10cd9?preview=true).

### Microsoft 365 Copilot Chat

- **Graph Connectors in CIQ** \[Web\]

  Ground your Copilot prompts in CIQ using data from your organization's Graph Connectors, so responses reflect your third-party content and deliver richer, more relevant insights. [Learn more](https://support.microsoft.com/topic/using-context-iq-to-refer-to-specific-files-people-and-more-in-microsoft-365-copilot-and-copilot-chat-272ac2c1-c5f7-49c9-8a42-2a8a87846fa0).
- **Ground prompts with SharePoint Sites** \[Web\]

  Users can scope their prompts in Copilot Chat by searching and selecting relevant SharePoint Sites, allowing more focused and relevant discussions.
- **Personalize interactions with Copilot Memory** \[Android, iOS, Web\]

  Copilot Memory leverages insights inferred from conversations between the user and Copilot, along with data from the Microsoft Graph and custom instructions to provide personalized help for tasks. Users have full control and can view, manage, disable or clear memory at any time. [Learn more](https://techcommunity.microsoft.com/blog/microsoft365copilotblog/introducing-copilot-memory-a-more-productive-and-personalized-ai-for-the-way-you/4432059).
- **Use Copilot Chat to enhance Find on Page** \[Web\]

  Quickly locate the right information by combining CTRL+F with Copilot Chat for smarter, context-aware search in Microsoft Edge for Business. [Learn more](https://support.microsoft.com/topic/using-microsoft-copilot-in-edge-at-work-012b3674-bab8-4f99-8585-c961dac68642).
- **Utilize SharePoint and OneDrive folders in prompts** \[Web\]

  Users can now incorporate SharePoint and OneDrive folders into their Copilot Chat prompts via the "Attach cloud files" feature, refining content scoping capabilities.
- **View web queries used by Copilot for greater transparency** \[web, Windows\]

  See the exact web queries Copilot sends in response to your prompts, along with the list of websites queried, enhancing your awareness and control over the information process.

### Microsoft Loop

- **Turn Copilot Pages into Word documents** \[Web\]

  Move research and content collected in Copilot Pages into Word with one click, simplifying sharing and finalizing documents.

### Microsoft Purview compliance portal

- **Data Loss Prevention to restrict Microsoft 365 Copilot processing on content with sensitivity labels** \[Web\]

  This feature allows DLP policies to provide detection of sensitivity labels in enterprise grounding data and restrict access of the content in Microsoft 365 Copilot. [Learn more](https://learn.microsoft.com/en-us/purview/dlp-microsoft365-copilot-location-learn-about).

### OneDrive

- **Ask Copilot questions on Teams meeting recordings** \[Web\]

  Select a Teams meeting recording in your OneDrive commercial account and ask Copilot to recap the meeting, highlight parts where you were mentioned, or recommend action items and next steps. This feature requires a Microsoft Copilot for Microsoft 365 license and will be available to commercial customers on OneDrive Web. This feature works only on Teams meeting recordings with a transcript. [Learn more](https://support.microsoft.com/office/get-started-with-copilot-in-onedrive-7fc81e10-e0cf-4da8-af2e-9876a2770e5d).
- **Catch up with hands-free audio overviews of your files** \[Web\]

  Effortlessly stay informed using Copilot to generate audio overviews for key documents, prepping for meetings, or catching up on updates. Providing a quick, engaging way to absorb file content-hands-free. [Learn more](https://support.microsoft.com/topic/get-an-audio-overview-of-your-notebook-with-microsoft-365-copilot-notebooks-a22df989-b9cd-47fb-abac-e888d8f10cd9).

### PowerPoint

- **Excel data when building a presentation** \[Web, Mac, Windows\]

  You can now reference an Excel file when you create a presentation with Copilot within the PowerPoint application. [Learn more](https://support.microsoft.com/office/create-a-new-presentation-with-copilot-in-powerpoint-3222ee03-f5a4-4d27-8642-9c387ab4854d).

### Viva Glint

- **Enable Copilot for Company Admin role in Viva Glint** \[Web\]

  Viva Glint admins can now turn on Copilot for Company Admins without creating custom rolesâ€"simplifying Copilot access while maintaining permissions safeguards. [Learn more](https://learn.microsoft.com/en-us/viva/glint/copilot/admin-enable#enable-copilot-for-company-admins).

### Word

- **Preserve formatting when drafting from selected text** \[Web\]

  When Copilot generates drafts based on a selection of text, Copilot retains the formatting of the selected text and allows users to apply new formatting, like bold, underline, italic, and more.

## August 19, 2025

Updates released between August 5, 2025, and August 19, 2025.

### Copilot extensibility

- **Craft actions using API chaining with low code** \[Windows, Web\]

  Makers can leverage low code and pro-code options to create actions with API chaining, enabling bulk actions and adaptive card contexts for streamlined processes. [Learn more](https://learn.microsoft.com/en-us/microsoft-365-copilot/extensibility/instructions-api-plugins).
- **Create simplified multi-step workflows** \[Windows, Web\]

  Streamline your tasks with an embedded builder that allows users to design and manage multi-step workflows effortlessly, enhancing productivity. [Learn more](https://learn.microsoft.com/en-us/microsoft-365-copilot/extensibility/declarative-agent-instructions).
- **Discover custom extensions for Copilot** \[Windows, Web\]

  Find and deploy customizable extensions \(CEAs\) for Copilot directly from the Store, enhancing the capabilities of your workflow with ease.
- **Integrate declarative agents into Excel** \[Windows, Web\]

  Users can now seamlessly integrate and leverage declarative Copilot agents directly within Excel, enhancing data interaction and task automation. [Learn more](https://learn.microsoft.com/en-us/microsoft-365-copilot/extensibility/overview-declarative-agent).
- **Regulate knowledge source with governance tools** \[Windows, Web\]

  Admins can now oversee and manage agents with uploaded files as their knowledge source, utilizing tools for agent filtering, reviewing sensitivity labels, and managing metadata.
- **See authors and descriptions in every agent interaction** \[Windows, Web\]

  Build trust and transparency by viewing the author name and agent description in each interaction, enhancing user confidence in responses.

### Copilot Studio

- **Build a custom agent with natural language** \[Web\]

  Describe the agent you want, and Copilot Studio instantly proposes its name, purpose, instructions and starter prompts-so you can begin testing in minutes instead of hours. [Learn more](https://learn.microsoft.com/en-us/microsoft-copilot-studio/fundamentals-get-started).
- **Perform custom search as a topic action** \[Web\]

  Enhance your precision with Custom Search, allowing you to query knowledge sources and extract raw data effortlessly. This feature empowers you to create more transparent Copilot experiences by running searches on selected sources and saving data outputs for flexible use. [Learn more](https://learn.microsoft.com/en-us/microsoft-copilot-studio/authoring-create-custom-search).
- **See security-related views and statuses for agents within Copilot Studio** \[Web\]

  Enhanced security in Copilot Studio with visual indicators for agent protection, blocked prompts, and authentication guidelines. Makers can see how and when Microsoft has protected their agents, assessed their agents' status, and determine if any action is needed. [Learn more](https://learn.microsoft.com/en-us/microsoft-copilot-studio/security-agent-runtime-view).
- **Use managed agents as a starting point for Copilot creation** \[Web\]

  Explore and install managed agents in Copilot Studio to kickstart your projects with ready-to-use solutions featuring built-in service connections and autonomous capabilities. Streamline your workflow and enhance productivity without starting from scratch.

### Microsoft 365 admin center

- **Manage Copilot costs with budget limits** \[Web\]

  Define budget policies for Copilot services, set thresholds and alerts, and receive email notifications for proactive cost control. [Learn more](https://learn.microsoft.com/en-us/microsoft-365/copilot/pay-as-you-go/setup).

### Microsoft 365 Copilot app

- **Expanded language options with Microsoft 365 Copilot** \[Android, Windows, iOS, Mac, Web\]

  Microsoft 365 Copilot now supports six additional languages: Albanian, Filipino, Icelandic, Malay, Maltese, and Serbian \(Cyrillic\). [Learn more](https://support.microsoft.com/office/supported-languages-for-microsoft-365-copilot-94518d61-644b-4118-9492-617eea4801d8).

### Microsoft 365 Copilot Chat

- **Copilot Chat available for EDU users ages 13 and older** \[Web\]

  Microsoft 365 Copilot Chat is now accessible for EDU users aged 13+, offering secure AI chat with the latest language models. Admins need to enable access for eligible users. [Learn more](https://techcommunity.microsoft.com/blog/educationblog/microsoft-365-copilot-chat-for-students-13/4440370).
- **Edge contextual capabilities in Copilot Chat work mode** \[Web\]

  In Copilot Chat work mode, ask Copilot questions about web pages and PDFs opened in Edge-using page context to summarize or analyze content, and enhancing your research on the fly. [Learn more](https://learn.microsoft.com/en-us/deployedge/edge-learnmore-copilot-page-summary-results).
- **Expanded file search capabilities in Copilot Chat** \[Windows, Web\]

  Copilot Chat now supports a wider range of file types in SharePoint and OneDrive, enhancing search and information retrieval. [Learn more](https://support.microsoft.com/topic/file-formats-supported-by-microsoft-365-copilot-1afb9a70-2232-4753-85c2-602c422af3a8).

### Microsoft Purview compliance portal

- **Monitor Microsoft 365 Copilot's security posture** \[Web\]

  A dedicated page in Data Security Posture Management for AI showcases Microsoft 365 Copilot's protection capabilities and usage metrics for improved oversight. [Learn more](https://learn.microsoft.com/en-us/purview/dspm-for-ai-considerations).
- **New graph for departments** \[Web\]

  A newly added graph in Data Security Posture Management for AI shows AI interactions grouped by department. [Learn more](https://learn.microsoft.com/en-us/purview/dspm-for-ai-considerations).
- **Web search query filtering in Data Security Posture Management for AI** \[Web\]

  Filter AI interactions for events that contain a web search query and view the content of the search within Microsoft Purview Data Security Posture Management for AI. [Learn more](https://learn.microsoft.com/en-us/purview/dspm-for-ai-considerations).

### OneDrive

- **Sharing with Copilot summary now supports more file types** \[Web\]

  Enhance your collaboration workflow by using Copilot to generate summaries for PowerPoint, Excel, PDFs, images, and protected files directly within OneDrive Web and SharePoint document libraries. Get instant overviews while maintaining sensitivity labels on confidential files, ensuring secure and efficient sharing.

### Outlook

- **Summarize email attachments with Copilot** \[Android, Windows, iOS, Mac, Web\]

  Summarize PDF, Word, and PPT email attachments effortlessly in Outlook Web and the new Outlook for Windows, making it easier to extract key information without needing to open each file. [Learn more](https://support.microsoft.com/office/summarize-an-email-thread-with-copilot-in-outlook-a79873f2-396b-46dc-b852-7fe5947ab640#id0ebbj=new_outlook).

### SharePoint

- **Microsoft 365/SharePoint Agent Insights for SharePoint Administrators** \[Web\]

  Provides comprehensive insights into newly created SharePoint agents with content governance actions within SharePoint Advanced Management controls. [Learn more](https://learn.microsoft.com/en-us/sharepoint/insights-on-sharepoint-agents).

### Viva Insights

- **Bridge skill gaps with personalized insights** \[Windows, Web\]

  Discover and promote upskilling opportunities with People Skills. Share skills, connect with others, and enrich user experiences across Microsoft 365, including apps such as Copilot and Viva Learning. [Learn more](https://learn.microsoft.com/en-us/microsoft-365/copilot/people-skills-overview).
- **Unified analytics for enhanced insights** \[Web\]

  Experience a streamlined approach with Copilot Dashboard and Viva Insights. This unified platform blends advanced analytics offerings, providing leaders, delegates, and analysts with cohesive, actionable insights. [Learn more](https://learn.microsoft.com/en-us/viva/insights/introduction#viva-insights-web-app).

### Word

- **Select some text and explore actions with the Copilot icon in your margin.** \[Web\]

  Rewrite, get writing suggestions, and more with just one click.

## August 5, 2025

Updates released between July 22, 2025, and August 5, 2025.

### Copilot extensibility

- **Admin pre-approval for trusted declarative agents** \[Web\]

  Admins can now pre-approve specific agents so their actions are always allowed without extra confirmation. This reduces interruptions and helps ensure a smooth workflow in integrated apps. [Learn more](https://learn.microsoft.com/en-us/microsoft-365/admin/manage/manage-copilot-agents-integrated-apps).
- **Enhance agent builder with full screen mode** \[Windows, Mac, Web\]

  Enjoy an improved agent builder experience with a full-screen view that streamlines the process of creating and managing your agents. [Learn more](https://learn.microsoft.com/en-us/microsoft-365-copilot/extensibility/copilot-studio-agent-builder-build).
- **Enhanced Q&A accuracy for SharePoint files** \[Windows, Web\]

  Improve the precision of Q&A interactions on SharePoint files that include tables, comments, and formatting. Benefit from more relevant and insightful responses whether you're working with Word, PDF, or PowerPoint files.
- **Get relevant calendar results by time period** \[Windows, Web\]

  Quickly summarize meetings for a specific day to stay on top of your schedule and focus on the events that matter most.
- **Improve email responses with extra context** \[Windows, Web\]

  Get fuller email replies that expand your initial lists, indicate the number of related messages, and let you easily paginate for more details-all to help you manage your inbox more effectively. [Learn more](https://support.microsoft.com/topic/schedule-copilot-prompts-29dfd5fb-211a-4515-88a6-730b8074e489).
- **Schedule meetings with smart time insights** \[Windows, Web\]

  Easily discover optimal meeting times and streamline Outlook handoffs with intelligent calendar suggestions that make scheduling a breeze. [Learn more](https://support.microsoft.com/office/how-do-i-use-the-the-scheduling-assistant-to-find-meeting-times-bdd6c165-4186-45f1-ad9e-5af067ac69a3).

### Copilot Studio

- **Ground your agents with live enterprise data** \[Web\]

  You can now enhance your copilots built with Microsoft Copilot Studio by incorporating structured data from both Microsoft and select non-Microsoft systems. These copilots enable users to ask natural language questions about enterprise systems within their Power Platform tenants. Building on the natural language query capabilities introduced with Microsoft Dataverse knowledge, Microsoft is extending this functionality to include certain third-party services. [Learn more](https://learn.microsoft.com/en-us/microsoft-copilot-studio/knowledge-real-time-connectors).
- **Only use grounded knowledge for agent response** \[Windows, Web\]

  Prevent agents from using model-trained knowledge by turning off internal knowledge, ensuring responses are based on specified grounded sources. [Learn more](https://learn.microsoft.com/en-us/microsoft-365-copilot/extensibility/copilot-studio-agent-builder-knowledge#prioritize-your-knowledge-sources-over-general-knowledge).

### Microsoft 365 admin center

- **Onboard SharePoint Agents as a pay-as-you-go scenario in CCS** \[Web\]

  This feature introduces SharePoint Agents to the Pay-as-you-go tab under Copilot → Billing & usage, aligning with the existing workflow used for Microsoft 365 Copilot Chat. Administrators gain the ability to manage and monitor SharePoint Agent consumption through the familiar Pay-as-you-go interface, ensuring consistent oversight across Copilot experiences. Integration with the SharePoint backend via API enables precise usage tracking and billing for this new scenario. [Learn more](https://learn.microsoft.com/en-us/microsoft-365/commerce/services/pay-as-you-go-services)

### Microsoft 365 Copilot Chat

- **Share agents with your enterprise** \[Windows, Web\]

  Generate sharing links for your agents in Business Chat. If the recipient doesn't have the agent, they'll be directed to the Microsoft 365 application catalog to install it. If they do, the agent opens directly in Microsoft 365 Copilot Business Chat. [Learn more](https://support.microsoft.com/topic/how-to-share-your-agent-44981c08-ab64-43f1-bcf8-ebadfc5469cc).

### PowerPoint

- **Copilot uses enterprise assets hosted on SharePoint OAL when creating presentations now** \[Mac, Windows, Web\]

  Once you integrate your organization's assets into a Sharepoint OAL \(Organization Asset Library\) you will be able to create presentations with your organization's image. [Learn more](https://learn.microsoft.com/en-us/sharepoint/connect-organizational-asset-libraries-to-copilot).
- **Copilot uses Enterprise assets hosted on Templafy when creating presentations now** \[Mac, Windows, Web\]

  Once you connect your asset library hosted with Templafy to Microsoft365 and Copilot, you will be able to create presentations with your organization's images. [Learn more](https://learn.microsoft.com/en-us/sharepoint/connect-organizational-asset-libraries-to-copilot).

### SharePoint

- **Manage site ownership effectively** \[Web\]

  The site ownership policy enables you to define and enforce ownership criteria for your SharePoint sites, automating actions to prevent data risks if sites remain ownerless for over three months. [Learn more](https://learn.microsoft.com/en-us/sharepoint/create-sharepoint-site-ownership-policy).

### Word

- **Access audio overviews in Word** \[Web\]

  Generate a convenient audio overview of your document through Copilot from the Summary tab, enhancing your document review process. [Learn more](https://support.microsoft.com/topic/listen-to-an-audio-overview-of-your-document-9b2fad37-021e-4e89-b33b-323e850f9ae0).

## July 22, 2025

Updates released between July 8, 2025, and July 22, 2025.

### Copilot extensibility

- **Hebrew support in Agent builder** \[Windows, Web\]

  Integrate Hebrew language support in agent builder to build accessible, localized solutions that simplify multilingual deployments and enhance user engagement. [Learn more](https://learn.microsoft.com/en-us/microsoft-365-copilot/extensibility/copilot-studio-agent-builder-availability).
- **Increased support for uploading up to 20 documents to agents' knowledge** \[Windows, Web\]

  End users and makers can now upload up to 20 documents to ground agents with richer, embedded knowledge in Microsoft Copilot Studio agent builder. [Learn more](https://learn.microsoft.com/en-us/microsoft-365-copilot/extensibility/copilot-studio-agent-builder-knowledge).
- **Share agents from embedded builder** \[Windows, Web\]

  Users can share agents from an embedded agent builder to other individual users or group chats. [Learn more](https://learn.microsoft.com/en-us/microsoft-365/admin/manage/manage-embedded-knowledge-agents).
- **Share agents with context-aware link previews** \[Windows, Web\]

  Streamline your interactions by using context-aware buttons that adapt based on where links are shared-making it easier to take the right action in chats and meetings.
- **Upload and embed knowledge in declarative agents** \[Windows, Web\]

  Empower your agents with enriched context by uploading your own files and embedding crucial knowledge for personalized, day-to-day assistance. [Learn more](https://learn.microsoft.com/en-us/microsoft-copilot-studio/knowledge-add-file-upload).
- **Users can share agents from SharePoint** \[Web\]

  Users can share agents via links from SharePoint to Teams group chats. This means users will be able to chat and collaborate with SharePoint agents in group chats. The shared links will unfurl into preview cards with actionable buttons to 'Add to this chat'. [Learn more](https://learn.microsoft.com/en-us/sharepoint/get-started-sharepoint-agents).

### Copilot Studio

- **Easily find and use knowledge data sources** \[Web\]

  In Copilot Studio agent builder you can now quickly identify and select the right knowledge data sources without manually scanning long lists. This streamlined workflow helps you get to the insights you need faster for everyday tasks. [Learn more](https://learn.microsoft.com/en-us/power-platform/release-plan/2025wave1/microsoft-copilot-studio/use-teams-chats-as-knowledge-sources).

### Excel

- **Ask Copilot to generate formulas** \[Web\]

  Type "=" anywhere on your grid or in the formula bar and let Copilot generate formulas from natural language, making complex calculations simpler and faster. [Learn more](https://support.microsoft.com/office/generate-formulas-with-copilot-in-excel-d866d926-9791-4e5f-be2a-c6dd9e587a47).
- **Copilot advanced text analysis in Excel** \[Web\]

  Copilot can now analyze text by identifying themes and sentiments, citing data examples, and inserting a column with labels-helping you quickly uncover actionable insights. [Learn more](https://support.microsoft.com/topic/text-insights-in-excel-cecc7821-39c1-4e12-8bd6-4d4348370585).
- **Copilot icon on the grid in Excel for the web for M365 personal and family** \[Web\]

  Access AI-powered support directly from your spreadsheet with a single click. The Copilot icon helps you stay in your flow by offering instant insights while you work. [Learn more](https://techcommunity.microsoft.com/blog/excelblog/how-to-get-started-with-copilot/4383870).

### Microsoft 365 Copilot app

- **Get an audio overview of a notebook** \[Web\]

  Turn the files in your notebook into a dynamic audio overview for an engaging listening experience. Simply select "Get audio overview" at the top of your notebook-available in English only, with more languages coming soon. [Learn more](https://support.microsoft.com/topic/get-an-audio-overview-of-your-notebook-with-microsoft-365-copilot-notebooks-a22df989-b9cd-47fb-abac-e888d8f10cd9).

### Microsoft 365 Copilot Chat

- **Dictate your prompts in Copilot Chat** \[Windows, Web\]

You can now use the dictation button to input your prompts via speech, making interactions with Copilot more natural and efficient. [Learn more](https://www.microsoft.com/microsoft-365/roadmap?filters=&searchterms=475968).

- **Researcher available in GA** \[Windows, Mac, Web\]

  The researcher agent is pre-installed in Copilot Chat for all worldwide users. Find it in the left navigation pane alongside other agents, giving you quick access to research tools as part of the Copilot Premium license. [Learn more](https://www.microsoft.com/microsoft-365/blog/2025/06/02/researcher-and-analyst-are-now-generally-available-in-microsoft-365-copilot/?msockid=2484525e9a9b66d4330b47329bb667c9).

### Microsoft 365 Purview compliance portal

- **Data Security Posture Management for AI - Data Risk Assessments.** \[Web\]

  Admins can drive better security outcomes by reviewing default assessments, examining data sensitivity, and monitoring user accesses-all to quickly identify risks and remediate them in daily operations. [Learn more](https://learn.microsoft.com/en-us/purview/dspm-for-ai).

### PowerPoint

- **Reference multiple files in your presentation creation using Microsoft 365 Copilot** \[Windows, Mac, Web\]

  Enhance your PowerPoint presentations by referencing up to five files with Microsoft 365 Copilot, making it easier to incorporate detailed insights and comprehensive data without switching contexts. [Learn more](https://support.microsoft.com/office/create-a-new-presentation-with-copilot-in-powerpoint-3222ee03-f5a4-4d27-8642-9c387ab4854d).

### Word

- **Catch up on a summary of document comments in the top of your document** \[Web\]

  Copilot now has a Discussion tab in the top of your document to summarize open comments, helping you quickly understand what people have said.
- **Include citations in drafted content** \[Web\]

  Enhance the credibility and reliability of your documents with Copilot's ability to automatically include citations when drafting content from referenced sources. This feature ensures proper attribution and helps maintain academic and professional standards in your work.
- **Listen to an audio summary of your document** \[Web\]

  Transform your Word document into a dynamic audio experience with Copilot. Enjoy a podcast-style discussion that makes your content easy to consume on the go. Currently available in English, this feature allows you to listen to your documents anytime, anywhere. [Learn more](https://support.microsoft.com/topic/listen-to-an-audio-overview-of-your-document-9b2fad37-021e-4e89-b33b-323e850f9ae0).
- **Reference very large documents when prompting Copilot** \[Web\]

  Easily work with extensive documents by typing a forward slash \(/\) or selecting the attach icon to choose a document up to 3,000 pages long. This becomes the basis of the content you're requesting from Copilot, making it seamless to generate content from detailed sources. [Learn more](https://support.microsoft.com/topic/keep-it-short-and-sweet-a-guide-on-the-length-of-documents-that-you-provide-to-copilot-66de2ffd-deb2-4f0c-8984-098316104389).

## July 8, 2025

Updates released between June 24, 2025, and July 8, 2025.

### Copilot extensibility

- **Add Dataverse as knowledge in Copilot** \[Web, Windows\]

  Users can now include Dataverse as a knowledge source in Copilot, enabling more comprehensive responses and insights. [Learn more](https://learn.microsoft.com/en-us/microsoft-365-copilot/extensibility/build-declarative-agents?tabs=ttk&tutorial-step=1).
- **Audit and eDiscovery for Copilot actions and declarative agents** \[Windows, Web\]

  View detailed audit logs and eDiscovery records for Copilot actions and declarative agents in Microsoft Purview to simplify compliance and investigation workflows. [Learn more](https://learn.microsoft.com/en-us/purview/audit-copilot).
- **Deploy Copilot agents for easy discovery** \[Windows, Web\]

  Deploy Copilot agents in the store for user discovery directly from your apps. Users can get new agents, open the store, install, and use them seamlessly within App Chat. [Learn more](https://learn.microsoft.com/en-us/microsoft-365/admin/manage/manage-copilot-agents-integrated-apps).
- **Discover, acquire, and manage agents through in-app store in Word and PowerPoint** \[Windows, Web\]

  With Copilot extensibility, users can discover, acquire, and manage agents through the unified store. We are excited to introduce the Microsoft 365 unified store to Office documents, enabling users to discover, acquire, and manage agents directly within the in-app store for Word and PowerPoint, with Excel support coming soon. [Learn more](https://devblogs.microsoft.com/microsoft365dev/office-addins-at-build-2025/#modernized-store-for-office-add-ins-and-copilot-agents).

### Copilot Studio

- **See performance metrics for every knowledge source** \[Web\]

  Review usage frequency, answer rate, and error rate for each knowledge source to spot high-value content and quickly fix low-performing links, keeping your agents accurate and helpful. [Learn more](https://learn.microsoft.com/en-us/power-platform/release-plan/2025wave2/microsoft-copilot-studio/analyze-action-usage-agents).

### Excel

- **Copilot in Excel with Python \| Reasoning Model Integration \(Think Deeper\)** \[Mac, Windows, Web\]

  While performing advanced analysis with Copilot in Excel with Python, users can choose the "Think Deeper" mode to get a more elaborate and detailed plan, followed by automatic execution to generate Python code, results, and explanations. This improves performance on complex asks by leveraging the power of the latest AI reasoning models.

### Microsoft 365 admin center

- **Metadata for Shared agent management in Microsoft 365 admin center** \[Web\]

  IT admins can view metadata for Shared agents in Microsoft 365 admin center similar to metadata information for line of business applications built by customer organization. It provides IT admins the opportunity to explore all data besides honoring UX filters for a seamless user experience. [Learn more](https://learn.microsoft.com/en-us/microsoft-365/admin/manage/manage-shared-agents).

### Microsoft 365 Copilot app

- **Create in the Microsoft 365 Copilot app** \[Windows, Web\]

  The creative hub for AI led artifact generation capabilities. [Learn more](https://support.microsoft.com/topic/get-started-with-microsoft-365-copilot-create-6e0c616d-69fb-42f2-a4cb-c59e006ec4f5).
- **Updated UI for Microsoft 365 Copilot App** \[Windows, Web\]

  The Microsoft 365 Copilot app is your starting place for AI at work, offering quick access to secure AI chat, search, files, and content creation in one seamless app. [Learn more](https://www.microsoft.com/microsoft-365/blog/2025/04/23/microsoft-365-copilot-built-for-the-era-of-human-agent-collaboration/).

### Microsoft 365 Copilot Chat

- **Locate your Copilot Pages in Microsoft 365 Copilot Chat navigation pane** \[Windows, Web\]

  For quick access to your Copilot Pages, find all page artifacts created across your apps/modules in one place underneath the Chat section in the Microsoft 365 Copilot app. [Learn more](https://techcommunity.microsoft.com/blog/nonprofittechies/introduction-to-microsoft-copilot-pages/4421413).

### Microsoft Purview compliance portal

- **Data assessments in Microsoft Purview AI Hub** \[Web\]

  Create targeted assessments, review sensitivity and access for key locations, and take remediation actions to reduce oversharing risks-all from one dashboard. [Learn more](https://learn.microsoft.com/en-us/purview/dspm-for-ai).

### OneNote

- **Copilot Chat on OneNote for web and in Teams** \[Web\]

  User can enjoy the power of Microsoft Copilot to OneNote for web and in Teams. [Learn more](https://techcommunity.microsoft.com/blog/microsoft365copilotblog/increase-your-productivity-with-copilot-on-onenote-web-and-onenote-in-teams/4374756).

### Viva Connections

- **New News feature in Microsoft Teams** \[Android, Windows, iOS, Web\]

  This update replaces the current Feed experience in Viva Connections across desktop, mobile, and web platforms with a SharePoint News reader experience. This new experience presents SharePoint news from organizational sites, boosted news, users' followed sites, frequent sites, and people they work with in an immersive reader format. It includes a Copilot-powered news summary as well, available only in Teams for Windows desktop in this initial release. [Learn more](https://techcommunity.microsoft.com/blog/viva_connections_blog/introducing-enterprise-news-reader-in-viva-connections/4383832).

### Word

- **Automatic summary of documents on file-open in Word** \[Windows, Mac, Web\]

  When users open a document, Copilot generates a summary in the Word window. You can hide the summary or open the Copilot chat pane to ask specific questions about the document. [Learn more](https://support.microsoft.com/office/create-a-summary-of-your-document-with-copilot-in-word-79bb7a0a-3bf7-41fe-8c09-56f855b669bf).
- **Implement coaching suggestions when rewriting your text with Copilot** \[Web\]

  Enhance your writing process by letting Copilot apply tailored coaching tips when rewriting your selected text-refine your documents effortlessly. [Learn more](https://support.microsoft.com/topic/use-coaching-to-review-content-in-word-for-the-web-fa09c055-d623-4d20-954f-9b064a5a7c80).

## June 24, 2025

Updates released between June 10, 2025, and June 24, 2025.

### Copilot extensibility

- **Admins can manage Copilot extensibility under Copilot tab in Microsoft 365 admin center** \[Windows, Web\]

  Admins have options to manage Copilot extensibility under Copilot tab including agent management for IT published agents and shared agents. [Learn more](https://learn.microsoft.com/en-us/microsoft-365/admin/manage/manage-copilot-agents-integrated-apps).
- **Build agents faster with built in Office skills** \[Windows, Web\]

  Empower your agent building by consuming built-in Office skills like Q&A on documents and PowerPoint summaries. This feature speeds up integrations, reduces the need for custom solutions, and delivers context-aware insights for a smarter agent experience.
- **Declarative agents can read the current document in WXP** \[Windows, Web\]

  Improve your workflow with agents that dynamically interact with open documents. Receive real-time suggestions, automate edits, and extract key data to streamline reviews and boost productivity. [Learn more](https://adaptivecards.microsoft.com/?topic=Action.InsertImage).
- **Discover, acquire, and manage agents through in-app store** \[Windows, Web\]

  Users can now easily discover, acquire, and manage Copilot agents directly within their Word and PowerPoint documents through a unified in-app store. This streamlined experience simplifies adding new capabilities-and Excel support is coming soon. [Learn more](https://devblogs.microsoft.com/microsoft365dev/office-addins-at-build-2025/#modernized-store-for-office-add-ins-and-copilot-agents).
- **Manage custom Copilot agents in Agent Center** \[Windows, Web\]

  Organize, store, and update your declarative Copilot agents in one place. Agent Center lets developers register in-context actions, fine-tune prompts, and test behavior faster-so IT admins can roll out reliable, task-specific Copilot experiences at scale. [Learn more](https://devblogs.microsoft.com/microsoft365dev/introducing-the-agent-store-build-publish-and-discover-agents-in-microsoft-365-copilot/).
- **Non-citation links remain visible in custom actions** \[Windows, Web\]

  Links returned from your custom actions are no longer redacted when they aren't part of a citation, letting users follow the full URL for easier validation and deeper exploration. [Learn more](https://techcommunity.microsoft.com/blog/microsoftdefenderforoffice365blog/safelinks-protection-for-links-generated-by-m365-copilot-chat-and-office-apps/4396828).

### Copilot Studio

- **Add custom Copilot Studio agents to Microsoft 365** \[Web\]

  Publish your Copilot Studio agent to the Microsoft 365 channel in one click, then roll it out to yourself, a pilot group, or your whole org. Messages, quick replies, adaptive cards, and multi-turn chat work instantly, while Power Platform analytics and governance keep everything secure and measurable. [Learn more](https://learn.microsoft.com/en-us/microsoft-365-copilot/extensibility/publish)
- **Automate repetitive tasks with agent flows** \[Web\]

  Build agent flows in Copilot Studio using natural language to automate workflows with AI-powered actions. Makers can build intelligent, scalable, and flexible automations for tasks ranging from intelligent summarization to advanced approvals - and get fast, consistent results. [Learn more](https://learn.microsoft.com/en-us/microsoft-copilot-studio/flows-overview).
- **C2 image upload and Q&A** \[Web\]

  Allow your Microsoft Copilot Studio agent to analyze images that users upload during conversations with the agent. This feature enhances visual content collaboration with intelligent insights for everyday tasks. [Learn more](https://learn.microsoft.com/en-us/microsoft-copilot-studio/image-input-analysis).

### Excel

- **Use Copilot with any table in the workbook, referring by natural language** \[iOS, Web, Mac, Windows\]

  Copilot uses the context of your prompt to pick what selection of data to answer about and reason over, including tables in other sheets. [Learn more](https://techcommunity.microsoft.com/blog/excelblog/smarter-context-awareness-for-copilot-in-excel/4424939).

### Microsoft 365 Copilot app

- **Copilot Notebooks** \[Web\]

  Copilot Notebook in the Microsoft 365 Copilot app streamlines your workflow by integrating notebook functionality directly into the app. [Learn more](https://support.microsoft.com/topic/get-started-with-microsoft-365-copilot-notebooks-0775e693-11c6-4d80-8aba-fcc81a737a06).
- **Use Copilot suggested prompts for recommended entities** \[Windows, Mac, Web\]

  Empower your work with a $30 Copilot license by clicking on curated prompts within recommended entities. Uncover key insights on demand-helping you boost productivity in everyday tasks. [Learn more](https://techcommunity.microsoft.com/blog/microsoft365copilotblog/getting-the-most-from-the-copilot-prompt-gallery/4383106).

### Microsoft 365 Copilot

- **Copilot Prompt Gallery - share prompts with a Teams team** \[Windows, Web\]

  Share custom prompts with members of a Microsoft Teams team directly from Copilot Prompt Gallery, allowing colleagues to easily discover and reuse them in Copilot Chat. [Learn more](https://support.microsoft.com/topic/sharing-prompts-with-a-team-2fa7a228-8645-4dc4-beec-d75d6d0bc752).

### Microsoft 365 Copilot Chat

- **Find any past Copilot conversation instantly** \[Web\]

  Search your Copilot Chat history by keyword to revisit decisions, copy answers, or resume a discussion without endless scrolling. [Learn more](https://www.microsoft.com/microsoft-365/roadmap?filters=&searchterms=388371).
- **Locate your Copilot Pages in Copilot Chat navigation pane** \[Windows, Web\]

  For quick access to your Copilot Pages, find all page artifacts created across your apps/modules in one place underneath the Chat section in the Microsoft 365 Copilot app. [Learn more](https://techcommunity.microsoft.com/blog/nonprofittechies/introduction-to-microsoft-copilot-pages/4421413).
- **Play back responses as audio** \[Windows, Web\]

  Listen to Copilot's replies with a built-in read aloud feature-ideal for multitasking or when you need to review content hands-free. [Learn more](https://www.microsoft.com/microsoft-365/roadmap?filters=&searchterms=475967).
- **Scheduled prompts** \[Windows, Mac, Web, Teams\]

  Plan ahead by scheduling essential prompts for repeated tasks in Copilot chat. Create a productive routine that helps you stay organized and efficient. [Learn more](https://learn.microsoft.com/en-us/microsoft-365/copilot/scheduled-prompts).

### Microsoft Clipchamp

- **Clipchamp Copilot video creator** \[Windows, Web\]

  Create a video draft on any topic by providing a prompt. Clipchamp will generate a script, source stock footage and music, add AI voice-over, text overlays, and transitions-giving you a ready-to-edit project you can export to OneDrive. [Learn more](https://support.microsoft.com/topic/how-to-create-video-with-copilot-7586329a-64e0-4ae9-9444-0da5b1c2b848).

### Microsoft Loop

- **Rich artifacts in Copilot Pages** \[Web\]

  You can now create rich artifacts, including interactive charts, tables, complex diagrams, and code created with Copilot from enterprise or web data. Artifacts can be added to Pages to further edit and refine with Copilot. They are interactive and stay in sync across Microsoft 365 when shared for collaborative work. [Learn more](https://support.microsoft.com/topic/turn-raw-data-into-dynamic-visuals-with-microsoft-365-copilot-pages-8a88637e-87f7-4099-b1c3-1472c2ba625c).

### PowerPoint

- **Create a PowerPoint slide from a file or prompt** \[Web, Windows, Mac\]

  Creating impactful slides can be challenging and time-consuming. Copilot helps you quickly turn your ideas and files into a fully designed slide with content ready to edit and refine, making the presentation creation and refinement process more personalized and efficient. [Learn more](https://support.microsoft.com/topic/add-a-slide-from-a-file-with-copilot-in-powerpoint-9034b581-38df-46be-a725-986cbbd4b5d4).
- **Easily select a template while you create a new PowerPoint presentation with Copilot** \[Mac, Web, Windows\]

  When creating a new presentation with Copilot in PowerPoint, choose a template from your organization's collection for on-brand presentations, or select from Microsoft's handpicked templates, ensuring the new presentation is built as per your chosen template. [Learn more](https://support.microsoft.com/topic/keep-your-presentation-on-brand-with-copilot-046c23d5-012e-49e0-8579-fe49302959fc).
- **Reference a PDF file when creating a presentation with Microsoft 365 Copilot** \[Mac, Windows, Web\]

  You can now reference a PDF file when you create a presentation with Copilot within the PowerPoint application. [Learn more](https://support.microsoft.com/office/create-a-new-presentation-with-copilot-in-powerpoint-3222ee03-f5a4-4d27-8642-9c387ab4854d).

## June 10, 2025

Updates released between May 29, 2025, and June 10, 2025.

### Copilot extensibility

- **One-click setup for all connectors** \[Windows, Web\]

  New and existing connectors now install in a single step within the admin center, speeding up data integration and reducing support calls. [Learn more](https://learn.microsoft.com/en-us/microsoft-365-copilot/extensibility/overview-copilot-connector).

### Copilot Studio

- **Encrypt Copilot content with your own keys** \[Web\]

  Microsoft Copilot Studio now allows you to use your own customer manager encryption keys \(CMKs, hosted in Microsoft Azure Key Vault\) to govern how Copilot Studio encrypts your copilot content. By using customer managed encryption keys \(CMKs\), you can ensure that any data provided to your agent by your users, and the data you provide to Microsoft, is encrypted with your own keys. You maintain control of your keys, providing you with further protection over the security of your data and ensuring you have control over how your data is stored at rest. Key capabilities include hosting with Azure Key Vault to manage your keys, lifetimes, and rotation periods, encryption of all of your content, including copilot topics, settings and configurations, and conversation transcript data, rotation of CMKs, and, evocation of access, if necessary. [Learn more](https://learn.microsoft.com/en-us/microsoft-copilot-studio/admin-customer-managed-keys).
- **Improve the agent template gallery in the create page** \[Web\]

  Experience a redesigned agent template gallery that makes it simple to find and select the right templates quickly. This modern, organized layout boosts productivity and encourages more frequent use. [Learn more](https://learn.microsoft.com/en-us/microsoft-copilot-studio/authoring-install-agent).

### Excel

- **Create with Copilot generates templates and tables** \[Web\]

  Create with Copilot in Excel empowers you to generate tailored templates and tables simply by writing prompts. Its multi-turn conversation refines schemas, formulas, and visuals for a polished result.
- **Improvements to Copilot chat experience** \[Windows, Web, Mac\]

  Improvements to the Excel Copilot chat experience to give more consistent responses to all chat questions.

### Microsoft 365 Copilot Chat

- **Microsoft 365 Copilot Chat: Updates to Copilot Chat response output** \[Web\]

  Easily interact with Microsoft Graph content represented by bolder references, new action bar, and more.
- **Module UI refresh** \[Windows, Web\]

  Copilot Chat is designed to provide a streamlined UI, making it easy to get started and achieve your goals quickly. It offers a helpful, understanding, and personalized experience, allowing you to search for past interactions, content, agents, or pages with ease. [Learn more](https://support.microsoft.com/topic/get-started-with-microsoft-365-copilot-chat-5b00a52d-7296-48ee-b938-b95b7209f737).
- **Simplified Input box update** \[Windows, Web\]

  We've made it easier for users to type prompts with access to CIQ, local files, attach cloud files, and agents by adding it under the Plus Menu.

### Microsoft Loop

- **Add a Loop workspace to your Teams channel** \[Web\]

  Pin a Loop workspace as a channel tab so everyone can brainstorm, co-create, and organize project content in real time while membership, governance, and compliance stay in sync. [Learn more](https://techcommunity.microsoft.com/blog/microsoft365insiderblog/collaborate-in-real-time-with-workspaces-in-teams/4414334).

### Microsoft Purview compliance portal

- **Data Security Posture Management for AI** \[Web\]

  Microsoft Purview Data Security Posture Management for AI \(DSPM for AI\) is a centralized location to gain insights into generative AI activity including the sensitive data flowing in AI prompts. [Learn more](https://learn.microsoft.com/en-us/purview/ai-microsoft-purview-considerations).
- **Gain DLP policy insights with Copilot** \[Web\]

  Let Copilot instantly summarize Data Loss Prevention policies across locations, classifiers, and notifications. Use natural-language prompts to zoom into specific policies, spot gaps, and adjust settings faster-keeping your organization's data posture aligned without manual digging. [Learn more](https://learn.microsoft.com/en-us/purview/dlp-test-dlp-policies#get-insights-with-security-copilot).

### Outlook

- **Custom Instructions for draft with Copilot** \[Android, Windows, iOS, Mac, Web\]

  Give Copilot some instructions about your emails - like the tone, length, greeting - so your Copilot generated drafts sound more like you want them to. #newoutlookforwindow
- **Schedule a meeting from an email with Copilot** \[Android, Windows, iOS, Mac, Web\]

  Turn any email thread into a meeting in one click. Copilot builds a complete invite for your review -title, agenda, attendee list, and a summary of the email conversation-plus attaches the original email thread so everyone is up to speed. Available in the new Outlook for Windows, web, Mac, and mobile. #newoutlookforwindows [Learn more](https://support.microsoft.com/office/create-a-meeting-and-agenda-with-copilot-in-outlook-31a44dfa-62bb-4751-82c4-14327a26759f).

### PowerPoint

- **Microsoft 365 Copilot Chat: Reference a TXT file when creating a presentation with Copilot** \[Windows, Mac, Web\]

  You can now reference a TXT file when you create a presentation with Copilot within the PowerPoint application. [Learn more](https://support.microsoft.com/office/create-a-new-presentation-with-copilot-in-powerpoint-3222ee03-f5a4-4d27-8642-9c387ab4854d).

### Teams

- **Microsoft Teams: Intelligent recap support for ad-hoc meetings and calls in GCC High** \[Android, Windows, iOS, Mac, Web\]

  Intelligent meeting recap is now available in GCC High for impromptu calls and meetings, like those started from 'Meet now' and calls started from chat. You can easily browse the recording by speakers and topics, as well as access AI-generated notes, AI-generated tasks, and name mentions after the ad-hoc meeting ends. This capability is available for users with a Teams Premium or M365 Copilot license.

### Viva Glint

- **Feature access management for Copilot in Viva Glint** \[Web\]

  Enable or disable Copilot in Viva Glint for specific users directly from the Microsoft 365 admin center, giving you granular control over AI access. [Learn more](https://learn.microsoft.com/en-us/viva/feature-access-management).

## May 29, 2025

Updates released between May 13, 2025, and May 29, 2025.

### Copilot extensibility

- **Insert images in adaptive cards for richer interactions** \[Windows, Web\]

  Make your adaptive cards more dynamic by adding images-perfect for illustrating ideas, sharing visual data, or engaging users with eye-catching content. This feature helps teams communicate clearly, support diverse learning styles, and create more memorable interactions in everyday workflows. [Learn more](https://learn.microsoft.com/en-us/microsoft-copilot-studio/guidance/adaptive-card-summarize-responses).
- **Unified Agent Management for Admins in Microsoft admin center** \[Windows, Web\]

  Admins can consistently manage Copilot agents in the Microsoft admin center, regardless of how they were built, simplifying deployment and governance. [Learn more](https://learn.microsoft.com/en-us/microsoft-365/admin/manage/manage-plugins-for-copilot-in-integrated-apps).

### Copilot Studio

- **Reuse connector and API actions across multiple copilots** \[Web\]

  Take an action that already works in Copilot for Sales and publish it to Customer Service-or any other eligible Copilot-in a few clicks. Skip duplicate setup, speed up delivery, and keep functionality consistent, all with built-in admin approval flows. [Learn more](https://learn.microsoft.com/en-us/microsoft-copilot-studio/agent-extend-action-rest-api).
- **Unpublish connector actions when data or services change** \[Web\]

  Roll back a published connector to draft so it no longer appears in Microsoft 365 Copilot. Makers can pause their own connectors, and admins can disable any connector to update configurations or retire obsolete services-without deleting them. [Learn more](https://learn.microsoft.com/en-us/power-platform/release-plan/2025wave1/microsoft-copilot-studio/unpublish-connector-actions-copilot-agents).

### Excel

- **Improved fallback answers in Copilot Chat** \[Web\]

  When specific data isn't found, Copilot seamlessly shifts to general reasoning so conversations keep flowing and users avoid dead ends in Excel for the web.

### Forms

- **Automate response collection and insights in Forms** \[Web\]

  Copilot builds a follow-up plan, sends reminders, tracks progress, and surfaces early trends-then hands off to Excel for deeper analysis-so you spend less time chasing respondents and more time acting on feedback. [Learn more](https://techcommunity.microsoft.com/blog/microsoftformsblog/introducing-new-agentic-features-for-copilot-in-forms-%E2%80%93-create-refine-and-share-/4406237).
- **Copilot in Forms can now reference files to help generate drafts** \[Web\]

  When creating a form with Copilot, users can now reference existing documents such as Word, Excel, and PowerPoint. Users can also reference an existing form by pasting the form's URL into the prompt box. Additionally, Copilot can search and suggest relevant files when generating a form, so users can easily create a draft that meets their needs. [Learn more](https://support.microsoft.com/office/frequently-asked-questions-about-copilot-in-forms-c9941b72-b32e-4c7e-9af9-e603929bb1d2).
- **Copilot in Forms has been refreshed to help users better refine and edit their forms** \[Web\]

  Copilot in Forms has been revamped to more easily help users refine and modify their forms. Users can now type prompts to Copilot to help with editing and refinement, so they can get tailored suggestions and easily get their forms ready to send. [Learn more](https://techcommunity.microsoft.com/blog/microsoftformsblog/introducing-new-agentic-features-for-copilot-in-forms-%E2%80%93-create-refine-and-share-/4406237).

### Microsoft 365 admin center

- **Usage reports - monitor m365.cloud.microsoft/chat/Teams/Outlook activity in Microsoft 365 Copilot Chat usage report** \[Web\]

  Track active users and last activity dates for m365.cloud.microsoft/chat, Teams, and Outlook-even for employees without a Copilot license-to gauge grassroots adoption and fine-tune rollout plans in Microsoft 365 Copilot Chat usage report. [Learn more](https://learn.microsoft.com/en-us/microsoft-365/admin/activity-reports/microsoft-copilot-usage).

### Microsoft 365 Copilot Chat

- **Bring Azure AI Search indexes into Copilot Studio knowledge** \[Web\]

  Attach existing Azure AI Search indexes as grounding data, enabling natural-language queries over enterprise content with minimal setup and no added cost.
- **Copilot Chat now offers access to cloud files to insert in user prompts** \[Windows, Web\]

  In the Web tab of Copilot Chat or Microsoft 365 Copilot, users can browse OneDrive or SharePoint, select a file, and drop it into their prompt to give Copilot precise context for richer responses.
- **Enable agent builder for Copilot chat** \[Windows, Web\]

  Empower developers with the ability to build custom agents to support Copilot Chat. This feature streamlines the creation of tailored chat experiences that enhance everyday communication and workflow. [Learn more](https://learn.microsoft.com/en-us/microsoft-365-copilot/extensibility/copilot-studio-agent-builder-build).
- **Ground copilots with real-time data from Salesforce, ServiceNow, and more** \[Web\]

  Connect structured records from popular non-Microsoft apps directly in Copilot Studio so users can ask, "Show my open Zendesk tickets" and get instant answers without leaving chat.
- **Pay-as-you-go policies keep Copilot costs in check** \[Windows, Web\]

  Allocate budgets by department, set usage caps, and manage access from the admin center so your organization can innovate with Copilot while staying on budget. [Learn more](https://learn.microsoft.com/en-us/microsoft-365/copilot/pay-as-you-go/overview).

### PowerPoint

- **Ask Copilot to rewrite text as a list** \[Web, Mac, Windows\]

  Transform paragraphs into clear bullet points or lists with a single command-ideal for quickly organizing content when preparing your presentation. [Learn more](https://support.microsoft.com/topic/elevate-your-presentation-game-with-copilot-s-text-rewrite-feature-in-powerpoint-d70b140b-bb3f-46b7-be64-ceec526a8dcd).

### Word

- **Ask agents to refine any text selection** \[Windows, Web\]

  Highlight a section of your document and let Copilot agents rewrite, shorten, or expand it-keeping the rest of your file private while you perfect the details.

## May 13, 2025

Updates released between April 29, 2025, and May 13, 2025.

### Copilot Studio

- **Monitor autonomous agents with detailed analytics** \[Web\]

  Instantly see run volume, trigger breakdowns, success rates, action paths, and run-time details for every autonomous agent. Use these insights to spot failures, tune performance, and boost reliability before your users notice issues.
- **Single connector for knowledge and actions** \[Web\]

  You can now reuse connector actions across multiple Copilot deployments without recreating them each time. This feature lets you select a previously published action-such as one from Copilot for Sales-and publish it to other endpoints, such as Copilot for Customer Service, with just a few clicks. It's enabled by default and streamlines deployment while reducing duplication. [Learn more](https://learn.microsoft.com/en-us/power-platform/release-plan/2024wave2/microsoft-copilot-studio/publish-connector-actions-multiple-copilot-deployments).

### Excel

- **Ask Copilot about any part of your sheet** \[Web, Mac, Windows, iOS\]

  When you ask questions about your worksheet, Copilot can look at the content of your sheet and use it to inform an answer to your question. This includes understanding worksheet data on your selected area, beyond tables and ranges, and provide Copilot answers in chat.
- **Easily access copilot on web** \[Web\]

  Find a dedicated Copilot icon in your web spreadsheet, allowing you to tap into AI-powered insights and streamline tasks without breaking your workflow. [Learn more](https://support.microsoft.com/office/get-started-with-copilot-in-excel-d7110502-0334-4b4f-a175-a73abdfc118a).
- **Visual cue for Copilot's data context** \[Web\]

  A subtle outline now highlights the exact cells or table Copilot is working with, so you can confirm the right data is selected before insights or edits are generated.

### Microsoft 365 Admin center

- **AI adoption score** \[Web\]

  A new people experiences category in Adoption Score in the Microsoft 365 admin center introduces AI adoption metrics, helping organizations understand how Microsoft Copilot features are being used across Microsoft 365. [Learn more](https://learn.microsoft.com/en-us/microsoft-365/admin/adoption/ai-adoption-score#organizational-messages-in-ai-adoption-score).
- **Manage pay-as-you-go billing for Copilot** \[Windows, Web\]

  Admins can manage pay-as-you-go billing directly within Copilot settings in the Microsoft 365 admin center. This capability is available to users with Global admin, AI admin, and Global reader roles. [Learn more](https://learn.microsoft.com/en-us/microsoft-365/copilot/pay-as-you-go/setup).
- **Overview of Copilot for admin** \[Web\]

  Streamline IT management with Copilot's real-time, contextually relevant insights that help you make faster, data-driven decisions in the Microsoft 365 admin center. [Learn more](https://aka.ms/copilotinmac).

### Microsoft 365 Copilot Chat

- **Unified prompt box across web and work chats** \[Windows, Web\]

  Enjoy a consistent prompting experience across Copilot Chat with an input box that looks and behaves the same in both work and web chat modes.

### Microsoft Viva

- **AI Administrator can manage Microsoft Copilot Dashboard settings** \[Web\]

  Delegate Copilot Dashboard control to the new Entra AI Administrator role, giving admins the permissions they need without granting AI admin privileges. [Learn more](https://learn.microsoft.com/en-us/viva/insights/advanced/admin/manage-settings-copilot-dashboard).

### OneDrive

- **Ask Copilot questions about images** \[Web\]

  Select up to five pictures in OneDrive Web and chat with Copilot to summarize, extract text, or describe what's inside-perfect for cataloging photos or pulling details from scanned documents. [Learn more](https://support.microsoft.com/topic/ask-about-a-topic-without-opening-your-files-8ea1bb0d-5ae7-4f81-8cb8-cd755862834b).

### PowerPoint

- **Suggestions for slide templates as you work** \[Mac, Web\]

  On PowerPoint for Mac, Copilot proposes design-ready layouts as soon as you insert a slide or start typing a title, helping you build polished decks faster. [Learn more](https://techcommunity.microsoft.com/blog/microsoft365insiderblog/jumpstart-your-presentations-with-slide-starters/4407669).

### Viva Insights

- **Viva Insights now included in Microsoft 365 Copilot subscriptions** \[Windows, Web, TeamsAndSurfaceDevices\]

  Create advanced, custom reports with Viva Insights to understand Copilot adoption, productivity and business impact. Full access to Viva Insights is available now with Microsoft 365 Copilot subscriptions.

### Word

- **Choose the level of detail for summaries when documents are opened** \[Web\]

  Tailor each document opening with your preferred summary style-select brief, standard, or detailed insights to match your workflow. [Learn more](https://support.microsoft.com/office/create-a-summary-of-your-document-with-copilot-in-word-79bb7a0a-3bf7-41fe-8c09-56f855b669bf).
- **Key statistics at a glance in Copilot summaries** \[Web\]

  Instantly see critical numbers-totals, dates, percentages, and more-in the Understanding tab, so you can grasp a document's quantitative story in seconds. [Learn more](https://support.microsoft.com/office/create-a-summary-of-your-document-with-copilot-in-word-79bb7a0a-3bf7-41fe-8c09-56f855b669bf).
- **Suggested questions help you explore any document** \[Web\]

  The Understanding tab now proposes smart questions about the file you're reading-just click one to see Copilot's answer and dive deeper without crafting your own prompt. [Learn more](https://support.microsoft.com/office/create-a-summary-of-your-document-with-copilot-in-word-79bb7a0a-3bf7-41fe-8c09-56f855b669bf).
- **Choose the level of detail for summaries when documents are opened** \[Windows, Mac, Web\]

  Tailor each document opening with your preferred summary style-select brief, standard, or detailed insights to match your workflow. [Learn more](https://support.microsoft.com/office/create-a-summary-of-your-document-with-copilot-in-word-79bb7a0a-3bf7-41fe-8c09-56f855b669bf).

## April 29, 2025

Updates released between April 16, 2025, and April 29, 2025.

### Excel

- **Formula Explain on grid entry points** \[Web\]

  Understand complex formulas by triggering step-by-step explanations directly from the grid. Copilot breaks down calculations and clarifies references so you gain confidence when working with your data. [Learn more](https://support.microsoft.com/topic/understanding-formulas-with-copilot-7838fb47-7309-4dac-ba7a-8080cb75ee06).
- **Paste images into Copilot chat** \[Web, Windows\]

  Ask questions about images you insert into the prompt area to extract key data for your spreadsheets. [Learn more](https://techcommunity.microsoft.com/blog/microsoft365insiderblog/add-images-to-your-copilot-prompts-in-word-and-powerpoint/4359423).
- **Seamless transition from clean data to Copilot chat** \[Web\]

  After finalizing your data with Clean Data, effortlessly switch to Copilot chat for deeper insights and analysis. [Learn more](https://support.microsoft.com/office/clean-data-in-excel-7fe20d89-3f57-46d3-b659-e8f3ee853bda).

### Microsoft 365 Copilot extensibility

- **Agent builder now available in new regions** \[Windows, Web\]

  You can now access Copilot Studio agent builder in Norway, Sweden, South Korea, and South Africa. [Learn more](https://learn.microsoft.com/en-us/microsoft-365-copilot/extensibility/copilot-studio-agent-builder-availability#regional-availability).

### Microsoft Copilot Chat

- **Submit feedback on the agent builder experience** \[Windows, Web\]

  Improve your custom Copilot Chat solutions by providing targeted feedback on RAI and agent response during test chats. This direct input helps refine and enhance the builder experience. [Learn more](https://learn.microsoft.com/en-us/microsoft-365-copilot/extensibility/copilot-studio-agent-builder#submit-feedback).

### Microsoft Purview

- **GCC Microsoft Purview capabilities for Microsoft 365 Copilot** \[Web\]

  Microsoft Purview is launching several capabilities in government cloud environments that help secure and govern data in Microsoft 365 Copilot. These are capabilities in Information Protection, Data Lifecycle Management, Audit, eDiscovery, and Communication Compliance. These capabilities will be available once Microsoft 365 Copilot is deployed. [Learn more](https://learn.microsoft.com/en-us/purview/ai-microsoft-purview).

### Outlook

- **Prepare for meetings with AI-generated insights** \[Web\]

  Stay ahead of busy schedules by using the proactive "Prepare" button in your inbox to generate key meeting insights and summarize relevant files-helping you arrive ready to engage. [Learn more](https://support.microsoft.com/topic/prepare-for-your-meeting-with-copilot-f23326fc-7721-45f1-875e-23e77aaf3d89).

### SharePoint

- **Restricted access control enhancements** \[Web\]

  New enhancements for RAC policy for SharePoint administrators to restrict access to SharePoint sites including managing Microsoft 365 group connected sites with Microsoft 365 groups or Security groups. [Learn more](https://learn.microsoft.com/en-us/sharepoint/restricted-access-control).

### Viva Learning

- **AI & Copilot Resources provider availability to all Viva Learning users** \[Windows, Web, Teams\]

  The AI & Copilot Resources provider is now enabled by default for all Viva Learning users. Administrators now have the ability to manage the visibility of this provider within Viva Learning. [Learn more](https://learn.microsoft.com/en-us/viva/learning/ai-and-copilot-resources).
- **Copilot Academy availability to all Microsoft 365 users** \[Windows, Web, Teams\]

  Copilot Academy is now accessible to users without Copilot licenses. Admins now have the option to select their preferred access settings for Copilot Academy. [Learn more](https://learn.microsoft.com/en-us/viva/learning/academy-copilot).

### Word

- **Coach is now generally available across all markets and languages that Copilot currently supports** \[Web\]

  Coach is now generally available across all markets and languages that Copilot currently supports, ensuring a consistent experience for every user. [Learn more](https://support.microsoft.com/topic/use-coaching-to-review-content-in-word-for-the-web-fa09c055-d623-4d20-954f-9b064a5a7c80).
- **Reference a whole folder when prompting Copilot** \[Web\]

  Quickly attach a folder from OneDrive or SharePoint by typing a forward slash \(/\) or selecting the attach icon. Copilot now uses the 10 most recent files from your selected folder to streamline your document creation. [Learn more](https://techcommunity.microsoft.com/blog/microsoft365insiderblog/expanding-reference-capabilities-with-microsoft-365-copilot-in-word/4406054).
- **Replace your selection with generated content** \[Web, Mac, Windows\]

  Selecting the Replace button lets you instantly replace your selected text with content that was generated in Draft with Copilot.

## April 16, 2025

Updates released between April 2, 2025, and April 16, 2025.

### Excel

- **Graph grounded chat** \[Windows, Mac, Web\]

  Ask Copilot in Excel for insights drawn from your chats, documents, meetings, and emails via Microsoft Graph-enhancing your workbook analysis with contextual organizational data. [Learn more](https://support.microsoft.com/topic/use-copilot-to-find-data-from-the-web-or-your-organization-and-add-it-in-excel-7a72fb29-e623-49e2-9f7d-38664b593054).
- **Use Copilot to search for answers from the web** \[Windows, Mac, Web\]

  In Excel, simply ask Copilot to search the web for answers and integrate the insights directly into your workbook, making data analysis even smoother. [Learn more](https://support.microsoft.com/topic/use-copilot-to-find-data-from-the-web-or-your-organization-and-add-it-in-excel-7a72fb29-e623-49e2-9f7d-38664b593054).

### Microsoft 365 admin center

- **AI Admin role has permissions to manage agents** \[Web\]

  As an AI Admin, you manage agents with various capabilities including creating and overseeing Copilot connections that index data in Graph and perform actions, controlling which makers can build these connections and regulating the data sources used, maintaining observability over all connections, approving or denying agents, pre-installing them without requiring consent, and viewing them in Microsoft 365 admin center integrated apps page.

### Microsoft 365 Copilot Chat

- **Get contextual suggestions during Copilot agent conversations** \[Windows, Web\]

  Speed up tasks with AI-driven prompts for next steps in Copilot Chat. See real-time suggestions to refine queries, dive deeper into topics, or resolve issues faster during agent interactions.
- **Support for longer prompts** \[Windows, Web\]

  Copilot Chat now supports larger inputs for smoother handling of extensive documents and data.

### Microsoft 365 Copilot extensibility

- **Discover agents for unlicensed and metered users** \[Windows, Web\]

  Empower more users with easy access to agents tailored to their needs-even if they are unlicensed or metered-broadening Copilot's reach across your organization. [Learn more](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/debugging-agents-copilot-studio).

### PowerPoint

- **Copilot in PowerPoint has improved performance when summarizing your presentation** \[Web\]

  PowerPoint Copilot now updates its language models regularly to deliver faster summaries, helping you quickly review your presentation content.

### SharePoint

- **Author engaging web pages with Authoring** \[Web\]

  Combine the power of Large Language Models, your data in the Microsoft Graph, built-in or custom templates, and existing documents to create high-quality SharePoint pages while ensuring enterprise-level data security and privacy. [Learn more](https://techcommunity.microsoft.com/blog/spblog/create-pages-with-copilot-in-sharepoint/4394588).

## April 2, 2025

Updates released between March 20, 2025, and April 2, 2025.

### Copilot Studio

- **Enhanced SharePoint URL support in Copilot Studio** \[Web\]

  Previously, only SharePoint site URLs could be used as knowledge for Copilot Studio agents. Users can now use SharePoint file, folder, and site URLs, including links from the Share button or browser address bar; once the URLs are added, the agents will be grounded to the content within the URL. Additionally, more granular error messages help with transparency and managing expectations. [Learn more](https://learn.microsoft.com/en-us/microsoft-copilot-studio/knowledge-add-sharepoint).
- **Public website scoping for agents** \[Web\]

  Makers can now scope agents' knowledge sources to specific websites, enhancing the precision of web searches. This capability, previously available in custom agents from Microsoft Copilot Studio, is now extended to agents in the Microsoft 365 context. [Learn more](https://learn.microsoft.com/en-us/microsoft-365-copilot/extensibility/copilot-studio-agent-builder-build#add-knowledge-sources).
- **SharePoint knowledge for agents** \[Web\]

  Makers can now leverage additional data sources, including Dataverse and SharePoint, when building autonomous agents. This expands the variety of use cases for autonomous agents.
- **Use agent builder in Copilot chat** \[Web\]

  Create custom agents in Copilot chat to streamline repetitive tasks and achieve consistency. Use specific instructions and grounding details to save time, reuse your agents, and enhance team productivity. [Learn more](https://learn.microsoft.com/en-us/microsoft-365-copilot/extensibility/copilot-studio-agent-builder-build).

### Excel

- **Gain insights with Copilot and Python in Excel on Web** \[Web\]

  Using everyday language, ask Copilot to perform advanced analytics like machine learning and predictive forecasting, which would usually take hours or require special skills. Copilot writes Python code and inserts it on the grid, providing deeper insights and stunning/ visuals. Available in multiple languages on Excel for the Web.
- **Read aloud for Excel text responses** \[Web\]

  Users can now use the Read Aloud button on the Copilot response card to have an audio narration of the response, enhancing accessibility and ease of information consumption.

### Microsoft 365 Copilot Chat

- **Ask questions about images with natural language** \[Android, iOS, Web\]

  Easily gain insights from images by asking natural language questions. Upload images for quick analysis using advanced vision models-helping you make sense of visual data across your apps.
- **Enhance email insights with interactive hovers** \[Web\]

  Enjoy enriched emails with interactive hovers that reveal contextual details-like sender info, dates, and follow-up prompts-to streamline your daily workflow.

### Microsoft 365 Copilot Studio

- **Collect user feedback in Copilot Studio agent builder** \[Web\]

  Makers can also now submit feedback-compliments, problems, or suggestions-directly to the product team from inside the Microsoft 365 agent builder. This can be done at any stage of the authoring process, including comments and optional metadata for troubleshooting. This feature allows quick issue reporting without disrupting workflow and enables the product team to address feedback efficiently. [Learn more](https://learn.microsoft.com/en-us/power-apps/maker/canvas-apps/agent-builder#provide-feedback).

### Microsoft Loop

- **Load existing Copilot pages and create multiple pages** \[Web\]

  With multipage functionality in Copilot Pages, users can load existing pages and create multiple pages within a single conversation. [Learn more](https://support.microsoft.com/topic/add-copilot-chat-responses-to-multiple-pages-a5c40f74-55d0-4f1f-80d8-539ccc1a4bcb).
- **Recap changes over a longer time** \[Web\]

  Recap changes in Loop over extended periods, such as the last week or last 30 days, instead of being limited to the current session. This feature helps users share updates more effectively.

### PowerPoint

- **Translate your presentation** \[Windows, Web, Mac\]

  Produce a translated copy of your entire presentation in about 40 languages while preserving your slide design and structure, making global collaboration effortless. [Learn more](https://support.microsoft.com/topic/translate-your-presentation-with-copilot-2c622fca-daaf-457c-bc74-f3496cf44a85).

### Word

- **Simplified prompt experience in chat** \[Web\]

  The chat experience in Word is now simplified with access to attachments, images, and agents now accessed from a single plus-sign menu.

## March 19, 2025

Updates released between March 5, 2025, and March 19, 2025.

### Copilot Studio

- **Create automated copilots triggered by events** \[Web\]

  Automates routine tasks by triggering copilots on events like table updates, new documents, or incoming emails-minimizing manual effort and keeping processes running smoothly. [Learn more](https://learn.microsoft.com/en-us/microsoft-copilot-studio/authoring-triggers-about).
- **Use generative actions** \[Web\]

  Replace manual topic triggers with AI-powered orchestration. You can now configure an agent to use generative AI to dynamically select relevant topics or plugin actions, creating more fluid conversations while reducing manual topic configuration. [Learn more](https://learn.microsoft.com/en-us/microsoft-copilot-studio/advanced-generative-actions).

### Microsoft 365 admin center

- **Manage shared Copilot agents across your organization** \[Web\]

  Tenant admins can now view, search, and block shared Copilot agents in the admin center. Maintain control over agent usage and ensure compliance with organizational policies.

### Microsoft 365 Copilot Chat

- **Copilot on Edge Update** \[Web\]

  Copilot on Edge has been updated and requires users to update their version of Edge to version 134.0.3124.51 or newer to receive the latest functionality. This update includes file upload availability on the web tab as well as a smoother authentication experience via the Edge Work Profile.
- **Prompt suggestions in Copilot chat** \[Windows, Web, Mac\]

  Get started in Copilot chat quickly with automatic prompt suggestions that enhance your productivity by providing relevant and context-aware prompts based on your previous interactions.

### Microsoft 365 Copilot extensibility

- **Support for message extension and declarative agents** \[Windows, Web\]

  Transform legacy plugins into integrated experiences by exposing them as declarative agents-enhance Office apps like Word, Excel, and PowerPoint with message extensions.

### Microsoft Loop

- **Track collaborative changes with "who did what and when"** \[Web\]

  Ask Copilot about recent edits in Loop workspaces to identify contributors, review timeline updates, and maintain clarity during team projects. Example: "Show changes to the onboarding checklist this week."

### Microsoft 365 Copilot

- **Share a Copilot prompt with a Teams team** \[Windows, Web\]

  Easily share custom prompts from the Copilot Prompt Gallery with your Microsoft Teams team. This streamlined sharing makes it simple for team members to discover and make the most of these prompts in their daily workflow. [Learn more](https://support.microsoft.com/topic/sharing-prompts-with-a-team-2fa7a228-8645-4dc4-beec-d75d6d0bc752?OCID=copilot_ongoingemail_feb25).

### SharePoint

- **Create and share agents** \[Web\]

  Easily create agents by selecting SharePoint sites or files and share them with your team in SharePoint or Teams to boost collaboration. [Learn more](https://techcommunity.microsoft.com/blog/microsoft365copilotblog/ignite-2024-sharepoint-agents-now-in-general-availability/4298746).
- **Use Data Access Governance to analyze tenant permissions** \[Web\]

  Leverage detailed reports on permissioned user counts and sharing links to identify oversharing risks and make informed governance decisions. [Learn more](https://learn.microsoft.com/en-us/sharepoint/data-access-governance-reports).

## March 4, 2025

Updates released between February 20, 2025, and March 4, 2025.

### Microsoft 365 Copilot Chat

- **Search archived mailboxes in Copilot Chat** \[Windows, Web, Android, iOS, Mac\]

  Leverage Copilot to search emails across both primary and archived mailboxes by appending 'from my archives' or 'also look for emails in my archives' in your prompts to quickly locate key messages.
- **Support lockbox for GenAI** \[Web\]

  Lets you review and approve data access requests in real time-ensuring sensitive information is safeguarded during critical support interactions.
- **Enrichment of Messages in Copilot Chat** \[Web\]

  This feature enhances your communication experience by making it easier to understand and interact with your chat messages in Copilot Chat. With this feature, you will see cards and hoverable experiences that provide additional details of the chat without leaving your current view. This means you can quickly grasp the context of your conversations and find the information you need more efficiently.

### Copilot Studio

- **Add enterprise data with new graph connections** \[Web\]

  Connect your organization's data seamlessly using pre-configured graph connectors like Stack Overflow, and Salesforce Knowledge. Build smarter agents with semantic search-no custom solution required. [Learn more](https://learn.microsoft.com/en-us/microsoftsearch/salesforce-knowledge-connector).

### Microsoft 365 admin center

- **Enhanced Copilot admin page with comprehensive tools** \[Web\]

  Navigate a refreshed admin interface featuring Overview, Health, Discover, and Settings-delivering key metrics, insights, and controls to tailor Copilot to your organization's needs.
- **Simplify Copilot license assignment** \[Web\]

  Use a data-driven license optimizer to identify users who gain the most value from Copilot. Streamline assignments in the admin center for efficient adoption across your organization.

### PowerPoint

- **Narrative builder creates slides with tables** \[Windows, Web, Mac\]

  Convert grounded content from Word documents into dynamic slides with tables. Enhance your presentations with structured, data-driven visuals effortlessly.

## February 19, 2025

Updates released between February 5, 2025, and February 19, 2025.

### Microsoft 365 Copilot Chat

- **Enhanced entity context card** \[Web\]

  Enjoy smoother motion, improved reliability, and a more intuitive experience with the upgraded entity context card-making it easier to explore contextual details as you work. [Learn more](https://support.microsoft.com/topic/using-context-iq-to-refer-to-specific-files-people-and-more-in-microsoft-365-copilot-272ac2c1-c5f7-49c9-8a42-2a8a87846fa0).
- **Increased results in Copilot Chat responses** \[Web\]

  Get more comprehensive email and calendar results in Copilot Chat responses to easily summarize messages or track your meetings throughout the day.

### PowerPoint

- **Create a presentation from a file-based prompt** \[Windows, Web, Mac\]

  Pull key facts and data from a selected file to shape your narrative. Simply provide Copilot with a prompt and quickly build your deck with relevant information. [Learn more](https://support.microsoft.com/office/create-a-new-presentation-with-copilot-in-powerpoint-3222ee03-f5a4-4d27-8642-9c387ab4854d).

### Viva Insights

- **Copilot dashboard for usage and retention insights** \[Windows, Web, Android, iOS, Mac\]

  Dive into usage frequency, compare top user groups, and track retention metrics-all in a single, comprehensive dashboard for actionable insights. [Learn more](https://learn.microsoft.com/en-us/viva/insights/org-team-insights/copilot-dashboard#interpreting-the-data).

### Word

- **Chat with Copilot about selected text** \[Windows, Web, Mac\]

  Highlight text, start a chat with Copilot, and receive responses tailored to what you've selected. Get targeted writing assistance and refine your content in real time.

## February 4, 2025

Updates released between January 24, 2025, and February 4, 2025.

### Microsoft 365 Clipchamp

- **Video creation in Copilot Visual Creator powered by Clipchamp** \[Web\]

  Type your prompt and Clipchamp writes a bespoke script, sources high-quality footage, and assembles a video project with music, voiceover, text overlays, and transitions. Open your draft in the Clipchamp app to continue editing, exporting, and sharing your video. [Learn more](https://techcommunity.microsoft.com/blog/microsoft_365blog/clipchamp-elevating-work-communication-with-seamless-video-creation-in-copilot/4375660).

### Microsoft 365 Copilot app

- **Updates to the Microsoft 365 \(Office\) app** \[Windows, Web, Android, iOS\]

  The Microsoft 365 Copilot app \(formerly Microsoft 365 app\) has a new name and icon. [Learn more](https://support.microsoft.com/office/the-microsoft-365-app-transition-to-the-microsoft-365-copilot-app-22eac811-08d6-4df3-92dd-77f193e354a5).

### Microsoft 365 Copilot Chat

- **Access support pages in Copilot Chat** \[Windows, Web, Android, iOS, Mac\]

  View organizational support pages directly within Copilot Chat, for quick help and guidance in your workflow.
- **Accommodate user's time zones in Copilot** \[Windows, Web, Android, iOS\]

  Copilot now references your local time zone when responding helping to avoid confusion and scheduling errors.
- **Charts, graphs, and data analysis in Copilot for Microsoft 365** \[Windows, Web\]

  Use natural language to create charts, graphs, and data analysis in Copilot Chat work mode.
- **Get more Copilot value with Microsoft 365 Copilot** \[Web\]

  Easily add full Copilot Chat capabilities including grounding conversations in work data and accessing Copilot in your favorite Microsoft 365 apps by purchasing or requesting a Microsoft 365 Copilot license directly in Copilot Chat. [Learn more](https://www.microsoft.com/microsoft-365/blog/2024/12/02/three-new-ways-small-and-medium-sized-businesses-can-purchase-microsoft-365-copilot).
- **Automatic session titles for easier organization** \[Web\]

  Let Copilot Chat generate smart, descriptive titles for your chat sessions, making it simpler to find and revisit important conversations.
- **Disable file upload in Copilot Chat** \[Windows, Web\]

  Admins gain control to turn off file uploads for Copilot Chat, helping maintain compliance when sharing sensitive content.

### Excel

- **Entry point from the column header** \[Web\]

  Offers an intuitive option to access column tools directly from the header, speeding up your workflow in Excel.

### PowerPoint

- **Use Copilot to rewrite, trim, or formalize text** \[Web, Mac\]

  Transform your presentation text by letting Copilot fix grammar, shorten lengthy content, or adopt a more professional tone-perfect for crafting clear, polished slides.

### Microsoft 365 Copilot

- **Share a prompt with a co-worker** \[Windows, Web\]

  Easily create, save, and share your favorite prompts using Copilot Prompt Gallery, inspiring your co-workers to achieve more with Copilot. [Learn more](https://learn.microsoft.com/en-us/microsoft-365/copilot/copilot-prompt-gallery-export-prompts).

### SharePoint

- **Restricted Content Discovery** \[Web\]

  Prevent specific SharePoint sites from being discoverable in tenant-wide search and Copilot. [Learn more](https://learn.microsoft.com/en-us/sharepoint/restricted-content-discovery).

### Word

- **Reference data from the Microsoft cloud when drafting with Copilot in Word** \[Windows, Web, Mac\]

  Draft with Copilot now supports attaching rich content from the Microsoft cloud-including emails and meetings-resulting in more contextually relevant content. [Learn more](https://techcommunity.microsoft.com/blog/microsoft365copilotblog/what%E2%80%99s-new-in-microsoft-365-copilot-in-word-at-ignite-2024/4303448).
- **Reference plain text files in Copilot** \[Windows, Web, Mac\]

  Add .txt files as sources with Copilot in Word, streamlining your process when working with text-based research or background content.

## January 23, 2025

Updates released between January 8, 2025, and January 23, 2025.

### Forms

- **Smart reminders with Copilot in Forms** \[Web\]

  Copilot in Forms now offers smart reminders to help you monitor response progress and get more engagement with your forms, delivered right to your email inbox. [Learn more](https://support.microsoft.com/topic/smart-reminders-in-copilot-in-forms-d41f412f-f64a-4bee-b745-eebf58b7e036).

### Microsoft 365 Copilot Chat

- **Introducing Microsoft 365 Copilot Chat** \[Windows, Web, Android, iOS\]

  Microsoft 365 Copilot Chat-secure AI chat powered by GPT-4o with agents accessible right in chat, and IT controls including enterprise data protection and agent management. Copilot Chat serves as a powerful new on-ramp for everyone in your organization to build an AI habit. And it is included with your Microsoft 365 subscription. Get started with Copilot Chat with the updated [Microsoft 365 Copilot app](https://www.m365copilot.com) \(formerly Microsoft 365 app\). [Learn more](https://www.microsoft.com/microsoft-365/blog/2025/01/15/copilot-for-all-introducing-microsoft-365-copilot-chat).
- **Updated meeting entity card in Copilot Chat** \[Windows, Web\]

  Check meeting details like RSVP status, date, and attachments without switching contexts in Copilot Chat.
- **Copilot agents available in Copilot Chat web mode** \[Web\]

  In Copilot Chat web mode, discover and use Copilot agents available for your organization. Agents are custom grounded chats that include specific knowledge sources from work and web.
- **Use Pages in compliant Copilot web chat** \[Android, Windows, iOS, Mac, Web\]

  Admins gain control to turn off file uploads for Copilot Chat, helping maintain compliance when sharing sensitive content.

### Microsoft 365 Copilot Studio

- **Enable makers to configure SharePoint as a knowledge source for agents** \[Web\]

  Empowers makers to connect SharePoint, giving agents a richer context for delivering accurate and relevant responses. [Learn more](https://learn.microsoft.com/en-us/microsoft-copilot-studio/authoring-review-activity).

### PowerPoint

- **Generate summaries for longer presentations** \[Windows, Web, Mac\]

  Copilot now supports text summaries up to 40k words \(around 150 slides\), giving you richer information and more polished layouts. [Learn more](https://support.microsoft.com/office/summarize-your-presentation-with-copilot-in-powerpoint-499e604c-4ab9-4f6a-9dbe-691cc87f2f69).

### SharePoint

- **Copilot in SharePoint** \[Web\]

  Copilot in SharePoint combines the power of Large Language Models \(LLMs\), your data in the Microsoft Graph, and best practices to create engaging web content. Get assistance drafting your content when creating new pages. Adjust the tone, expand meeting bullets into structured text, or get help making your message more concise. All within our existing commitments to data security and privacy in the enterprise. [Learn more](https://support.microsoft.com/topic/write-with-copilot-in-sharepoint-rich-text-editor-afc720be-666b-4d87-801e-b8ff62f309bb).

### Viva Amplify

- **Microsoft 365 Copilot in Viva Amplify editor** \[Web\]

  The superpowers of Microsoft 365 Copilot integrates seamlessly into Viva Amplify, transforming content creation. Use Copilot in Amplify to auto-rewrite for suggestions, expand or condense text, and adjust tone for consistent, relevant messaging. [Learn more](https://learn.microsoft.com/en-us/viva/amplify/copilot-in-viva-amplify).

### Viva Insights

- **Copilot dashboard access can be granted using Entra groups** \[Web\]

  Global admins can now grant Microsoft Copilot Dashboard access using Microsoft Entra ID \(AAD\) Groups, reducing the manual effort needed for management. [Learn more](https://learn.microsoft.com/en-us/viva/insights/org-team-insights/copilot-dashboard).

### Word

- **Listen to Copilot's responses with Read Aloud** \[Windows, Web, Mac\]

  Hear Copilot's replies in the chat pane, letting you stay hands-free while reviewing your content.

## January 7, 2025

Updates released between December 18, 2024, and January 7, 2025.

### Microsoft 365 admin center

- **Track usage of Microsoft 365 Copilot Chat** \[Web\]

  Filter data by date range, review Microsoft Copilot usage by app entry point, and use these insights plan adoption strategies more confidently. [Learn more](https://learn.microsoft.com/en-us/microsoft-365/admin/activity-reports/microsoft-copilot-usage).

### Microsoft 365 Copilot extensibility

- **Include Code Interpreter in agents** \[Windows, Web\]

  Enhance your agents by including Code Interpreter for advanced data analysis tasks in agent builder. [Learn more](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/code-interpreter).

### Outlook

- **Schedule meetings with Copilot chat in Outlook** \[Windows, Web\]

  Save time and streamline your day by asking Copilot to schedule meetings for you in Outlook. Whether it's a 1:1 or focus time, Copilot will find the best available time slots with ease. [Learn more](https://support.microsoft.com/topic/8090e7b3-5b1d-4c6d-9b06-02edac062f58).

### Viva Amplify

- **Copilot in Viva Amplify editor** \[Web\]

  Experience the power of Copilot right in your Amplify editing workflow. You can quickly auto-rewrite sections of your text, expand or condense content to match your preferred length, and seamlessly adjust the tone-casual, engaging, or professional-to suit your audience. [Learn more](https://support.microsoft.com/topic/introduction-to-copilot-in-viva-amplify-768222a0-9b83-402f-861e-9f7691183368).

### Viva Insights

- **New metrics for enterprise data-protected prompts** \[Windows, Web, Android, iOS, Mac\]

  Gain visibility into prompts submitted through Microsoft 365 Copilot Chat \(web\) and enterprise data-protected Copilot scenarios. [Learn more](https://learn.microsoft.com/en-us/viva/insights/advanced/reference/metrics#microsoft-365-copilot-metrics).

### Viva Learning

- **Copilot Academy support for external content** \[Web\]

  Enhance your learning experience with a wider range of external content in Copilot Academy, including links to Copilot Prompt Gallery. [Learn more](https://learn.microsoft.com/en-us/viva/learning/academy-copilot).

## December 23, 2025

Updates released between December 10, 2025, and December 23, 2025.

### Microsoft 365 Copilot app

- **GPT-5 powers Copilot Chat by default** \[Android, Windows, iOS, Mac, Web\]

  Copilot Chat delivers faster, smarter results using GPT-5 as the default model.

  **Details:**

  **What Changed:** All Copilot Chat experiences run on GPT-5 by default. Copilot automatically routes prompts to the best-performing models for each task, using fast models for basic tasks and specialized reasoning models for multi-step requests.

  **Why:** Users want speed, accuracy, and minimal friction. This update helps to ensure consistent, high-quality AI interactions in Copilot Chat.

  **Try This:**

  - "Get me up to speed on the latest plans related to \[project/initiative\]. Help me think through what to do next."
  - "Use the attached spreadsheet with customer feedback to create a polished executive report that helps upper management decide where to prioritize resources in our next cycle."


  **Why this matters:**


  **Business Impact:** Increases accuracy and productivity, helping teams make strong decisions and complete complex work faster.


  **Personal Impact:** Removes friction by letting Copilot choose the best model--fast or reasoning--for the prompt.


  **Additional resources:**


  **Blogs:**


  [Available today: GPT-5 in Microsoft 365 Copilot](https://www.microsoft.com/microsoft-365/blog/2025/08/07/available-today-gpt-5-in-microsoft-365-copilot/?msockid=281b58ceea286c6226164ec5eb056dd6)

### Microsoft 365 Copilot extensibility

- **Upload Larger Files in Copilot Studio Agent Builder** \[Android, Windows, iOS, Web\]

  Agent Builder now supports file uploads up to 512 MB when creating agents, ideal for larger files.

  **Roadmap ID:** [500375](https://www.microsoft.com/microsoft-365/roadmap?msockid=2484525e9a9b66d4330b47329bb667c9&filters=&searchterms=500375)

  **Details:**

  **What Changed:** This increases the upload size limit in Agent Builder to 512 MB, enabling use of larger files as grounding data.

  **Why:** Users requested more flexibility for grounding agents. Larger files improve reduce the need to split or compress documents.

  **Try This:**

  - Drag and drop large documents such as training manuals into your agent project.
  - Create the agent and ask it to summarize information from uploaded files.


  **Why this matters:**


  **Business Impact:** Allows enterprises to build agents with richer, domain-specific knowledge.


  **Personal Impact:** Complete your work without the need to split files or compress data.


  **Additional resources:**


  **Learn:**


  [Embedded file content](https://learn.microsoft.com/en-us/microsoft-365-copilot/extensibility/agent-builder-add-knowledge#embedded-file-content)

## November 25, 2025

Updates released between November 12, 2025, and November 25, 2025.

### Microsoft 365 Copilot Chat

- **Access shared mailboxes in Copilot Chat** \[Android, Windows, iOS, Mac, Web\]

  Copilot Chat now connects to shared mailboxes, so team-based conversations are more informed and collaborative.

  ****Roadmap ID:**** [488797](https://www.microsoft.com/microsoft-365/roadmap?msockid=2484525e9a9b66d4330b47329bb667c9&filters=&searchterms=488797)

  ****Details:****

  **What changed:** Users with shared mailbox permissions can ground Copilot responses in shared mail content, just like their own emails.

  ****Why:**** Eliminates context gaps in team workflows and improves shared visibility on projects.

  **Try this:**

  - Tell Copilot: *"Summarize recent emails in [mailbox@domain.com](mailto:mailbox@domain.com) mailbox."*
  - Tell Copilot: *"List all the emails around `topic` from < mailbox@domain.com > mailbox."*


  **Why this matters:**


  **Business Impact:** Ensures customer responses or project updates aren't missed when responsibility spans multiple team members.


  **Personal Impact:** Reduces copying and manual email checks across shared accounts-Copilot does it for you.


  **Additional resources:**


  [Use Copilot in shared mailboxes and delegate mailboxes](https://support.microsoft.com/topic/use-copilot-in-shared-mailboxes-and-delegate-mailboxes-3e7e5130-eabe-4c19-94ea-117b2a4c14d6)

- **Talk to Copilot with voice for faster hands-free work** \[Android, Windows, iOS, Mac, Web\]

  Speak to Copilot naturally on mobile or desktop to prepare for meetings, brainstorm ideas, or catch up on work-hands-free and grounded in work data.

  **Roadmap ID:** [481138](https://www.microsoft.com/microsoft-365/roadmap?msockid=2484525e9a9b66d4330b47329bb667c9&filters=&searchterms=481138)

  ****Details:****

  **What changed:** Copilot now supports voice input, enabling natural, conversational interactions in the Microsoft 365 Copilot app on mobile, desktop and the web and across Microsoft 365 apps, starting with Outlook, Word and PowerPoint.

  ****Why:**** Professionals need faster, more intuitive ways to engage with AI during their flow of work, especially when multitasking or on the move. Voice removes friction, letting you work where typing isn't practical.

  **Try this:**

  - Say: *"Confirm the agenda and attendee list for my next meeting"*.
  - Try: *"Create a quick list of next steps from my recent meeting notes."*
  - Ask: *"Summarize this document in five key points."*


  **Why this Matters:**


  **Business Impact:** Voice drives productivity and inclusivity through natural interactions that increase engagement, accelerate task completion and reduce downtime.


  **Personal Impact:** Work more comfortably and naturally while saving time, gaining efficiency and giving you the flexibility to use Copilot on the go or at your desk.


  **Additional resources:**


  [Get started with voice features in Microsoft 365 Copilot](https://support.microsoft.com/topic/get-started-with-voice-features-in-microsoft-365-copilot-9262968d-565e-470c-a04b-991eb8e0d1ea)

### Microsoft 365 Copilot extensibility

- **Access Custom engine Agents on Microsoft 365 Copilot chat on mobile** \[Android, iOS\]

  You can now interact with your organization's custom engine agents directly from your mobile device \(iOS and Android\), making Copilot even more adaptable to your workflows on the go. Whether you're away from your desk or managing tasks during a commute, your tailored business logic and automations are always at your fingertips.

  ****Details:****

  **What changed:** Support for custom engine agents is now available on the Microsoft 365 mobile experience \(iOS and Android\). You can access the same business-specific workflows and logic you have on desktop, ensuring uninterrupted productivity.

  ****Why:**** Teams needs consistent, personalized Copilot functionality no matter where they work. Bringing extensibility to mobile ensures employees stay productive and connected-even when away from their primary workstation.

  **Try this:**

  - Open the Microsoft 365 mobile app, launch Copilot, and activate one of your custom engine agents.
  - **Ask Copilot:** *"Run our expense approval workflow and update me on pending approvals."*


  **Why this matters:**


  **Business Impact:** Keep critical business processes running smoothly even when employees are mobile, reducing delays in approvals and operations.


  **Personal Impact:** Enjoy the same customized Copilot experience wherever you work, saving time and reducing context-switching throughout your day.


  **Additional resources:**


  **Learn:**


  [Custom engine agents for Microsoft 365 overview](https://learn.microsoft.com/en-us/microsoft-365-copilot/extensibility/overview-custom-engine-agent)

- **Support Message Extensions as Declarative Agents on Mobile** \[Android, iOS\]

  Stay productive on the move with support for message extensions as declarative agents in Copilot on iOS and Android. These extensions simplify workflows like inserting quick snippets, accessing integrated apps, or triggering processes directly from your mobile interface.

  ****Details:****

  **What changed:**

  Message extensions based Declarative agents" instead of "Message extensions as declarative agents.

  ****Why:****

  Workers increasingly use mobile as their primary device for timely communication and task management. Extending message-based workflows to mobile keeps teams efficient and responsive.

  **Try this:**

  - In a Teams chat on your mobile app, use Copilot to insert a dynamic update from a connected app with a message extension.
  - **Ask Copilot:***"Insert the latest sales figures into this conversation using our message extension agent."*


  **Why this matters:**


  **Business Impact:** Maintain seamless workflows across devices, ensuring real-time communication and agility for distributed teams.


  **Personal Impact:** Eliminate the frustration of being restricted to desktop for advanced actions-get the information and tools you need on the go.


  **Additional resources:**


  **Learn:**


  [Extend bot-based message extension as agent for Microsoft 365 Copilot](https://learn.microsoft.com/en-us/microsoftteams/platform/messaging-extensions/build-bot-based-agent?tabs=visual-studio-code)

## November 12, 2025

Updates released between October 28, 2025, and November 12, 2025.

### Microsoft 365 Copilot Chat

**RSVP status-based meeting search in Copilot Chat** \[Android, Windows, Web\]

**Roadmap:** [499429](https://www.microsoft.com/microsoft-365/roadmap?filters=&searchterms=499429)

Quickly find meetings based on RSVP status-either your own or others'. This feature helps you stay organized by surfacing RSVP details for upcoming events, so you can track commitments and follow up with attendees.

**Try this:**

Open Microsoft 365 Chat. Enter queries like:

- "Meetings I accepted this week"
- "Meetings I have not RSVPed this week"
- "Who all have accepted the Scrum meeting?"

View results showing RSVP details for yourself or attendees.

**Business or Personal Impact:**

**Business:** Improves meeting management and accountability by enabling quick visibility into attendee responses, reducing missed follow-ups.

**Personal:** Helps you stay on top of your schedule and commitments without manually checking each calendar invite.

## October 28, 2025

Updates released between October 15, 2025, and October 28, 2025.

### Copilot extensibility

- **@mention capability for mainline Copilot Chat** \[Android, iOS\]

  Use @mention in Copilot Chat to direct interactions to specific agents, ensuring focused and relevant responses from Copilot.

## September 30, 2025

Updates released between September 16, 2025, and September 30, 2025.

### Copilot extensibility

- **Agents support for Copilot Chat and pay-as-you-go on Microsoft 365 Copilot Mobile** \[Android, iOS\]

  Agents support for pay-as-you-go and Copilot chat users in now supported on the Microsoft 365 Copilot mobile app for easy usage.

### Microsoft 365 admin center

- **Usage reports for Copilot search** \[Android, Windows, iOS, Mac, Web\]

  Administrators gain insights into organizational adoption of Copilot search with new usage reports. Track total search queries, assess trends, and analyze user activity to drive effective adoption strategies. [Learn more](https://learn.microsoft.com/en-us/microsoft-365/admin/activity-reports/microsoft-365-copilot-search-usage).

### Microsoft 365 Copilot Chat

- **Copilot Chat now understands attached files like Word, Excel, PowerPoint, PDF, Text, JSON, and XML.** \[Android, Windows, iOS, Mac, Web\]

  Users can gather insights not only from the email content but also from attached files, enabling comprehensive context understanding.
- **Upload multiple images for creative prompts** \[Android, iOS, Web\]

  Now upload multiple images into Copilot Chat prompts at once to enhance creative reasoning and generate new content with varied inspiration.

## September 16, 2025

Updates released between September 3, 2025, and September 16, 2025.

### Copilot extensibility

- **Mobile support for Analyst agent on Android and iOS** \[iOS, Android\]

  Access and utilize the Analyst agent on iOS and Android devices using the Microsoft 365 Copilot app, ensuring seamless mobile insights and analysis.
- **Viral link sharing on M365 Copilot Mobile \(Android and iOS\)** \[Android, iOS\]

  Simplify collaboration with Agents with support for agent viral links on M365 Copilot app on Mobile, enhancing accessibility and engagement.

### Microsoft 365 Copilot app

- **Copilot Search for Premium SKU commercial users** \[Android\]

  Copilot Search allows you to search across files, people, 1P and 3P content \(for example, Figma, ServiceNow tickets\). You get Copilot answers for Natural Language Search queries.
- **Direct access to Copilot Chat in Microsoft 365 app** \[Android, iOS\]

  Microsoft 365 Copilot mobile app is removing bottom tabs and will open directly on Chat for eligible users, making it simpler and easier to chat with Copilot.
- **Microsoft 365 Copilot Search** \[Android, Windows, iOS, Web\]

  Copilot Search is the intelligent search experience within the Microsoft 365 Copilot app, designed to deliver fast, secure, and context-aware results across your organization's data. It enables users to search across emails, files, chats, meetings, and even third-party platforms like Salesforce, Jira, and Confluence using natural language queries. [Learn more](https://learn.microsoft.com/en-us/microsoft-365/copilot/microsoft-365-copilot-search).

## September 3, 2025

Updates released between August 19, 2025, and September 3, 2025.

### Microsoft 365 Copilot app

- **Enrich agents with Store integration on mobile** \[Android, iOS\]

  Access and enhance agents through the Agent Store on mobile, making it easier to deploy and manage new capabilities on the go.
- **Use Copilot in PDFs on mobile** \[Android, iOS\]

  Eligible users can now leverage Copilot within PDF files in the Microsoft 365 mobile app. Easily ask questions, gather summaries, and extract key insights from your PDFs for more efficient content understanding on the go.

### Microsoft 365 Copilot Chat

- **Personalize interactions with Copilot Memory** \[Android, iOS, Web\]

  Copilot Memory leverages insights inferred from conversations between the user and Copilot, along with data from the Microsoft Graph and custom instructions to provide personalized help for tasks. Users have full control and can view, manage, disable or clear memory at any time. [Learn more](https://techcommunity.microsoft.com/blog/microsoft365copilotblog/introducing-copilot-memory-a-more-productive-and-personalized-ai-for-the-way-you/4432059).

## August 19, 2025

Updates released between August 5, 2025, and August 19, 2025.

### Microsoft 365 Copilot app

- **Expanded language options with Microsoft 365 Copilot** \[Android, Windows, iOS, Mac, Web\]

  Microsoft 365 Copilot now supports six additional languages: Albanian, Filipino, Icelandic, Malay, Maltese, and Serbian \(Cyrillic\). [Learn more](https://support.microsoft.com/office/supported-languages-for-microsoft-365-copilot-94518d61-644b-4118-9492-617eea4801d8).

### Microsoft 365 Copilot Chat

- **Advanced data analysis in Copilot Chat mobile apps** \[Android, iOS\]

  Solve complex tasks by generating and executing Python code with the advanced reasoning model in Copilot Chat mobile apps.

### Outlook

- **Summarize email attachments with Copilot** \[Android, Windows, iOS, Mac, Web\]

  Summarize PDF, Word, and PPT email attachments effortlessly in Outlook Web and the new Outlook for Windows, making it easier to extract key information without needing to open each file. [Learn more](https://support.microsoft.com/office/summarize-an-email-thread-with-copilot-in-outlook-a79873f2-396b-46dc-b852-7fe5947ab640#id0ebbj=new_outlook).

## July 8, 2025

Updates released between June 24, 2025, and July 8, 2025.

### Viva Connections

- **New News feature in Microsoft Teams** \[Android, Windows, iOS, Web\]

  This update replaces the current Feed experience in Viva Connections across desktop, mobile, and web platforms with a SharePoint News reader experience. This new experience presents SharePoint news from organizational sites, boosted news, users' followed sites, frequent sites, and people they work with in an immersive reader format. It includes a Copilot-powered news summary as well, available only in Teams for Windows desktop in this initial release. [Learn more](https://techcommunity.microsoft.com/blog/viva_connections_blog/introducing-enterprise-news-reader-in-viva-connections/4383832).

## June 24, 2025

Updates released between June 10, 2025, and June 24, 2025.

### Teams

- **Copilot generated summaries for call transfers on Teams phone devices** \[Android\]

  Copilot generated summary provides an overview of the details and outcomes of transferred calls. It includes information such as the caller's details, the reason for the transfer, and the final resolution. [Learn more](https://support.microsoft.com/office/get-started-with-copilot-in-microsoft-teams-phone-97c55ffb-1499-4b0a-8caa-980ebb4b697b).
- **Speaker recognition and attribution in Teams Rooms on Android** \[Android\]

  Enhance your meetings with real-time speaker recognition and transcript attribution in Teams Rooms on Android. This feature identifies voices through cloud-enabled intelligent speakers and lets you securely enroll voices via Teams Settings-note that a Teams Rooms Pro license is required. [Learn more](https://learn.microsoft.com/en-us/microsoftteams/rooms/voice-recognition?branch=main&branchFallbackFrom=pr-en-us-14676).

## May 29 - June 10, 2025

Updates released between May 29, 2025, and June 10, 2025.

### Outlook

- **Custom Instructions for draft with Copilot** \[Android, Windows, iOS, Mac, Web\]

  Give Copilot some instructions about your emails - like the tone, length, greeting - so your Copilot generated drafts sound more like you want them to. #newoutlookforwindow
- **Schedule a meeting from an email with Copilot** \[Android, Windows, iOS, Mac, Web\]

  Turn any email thread into a meeting in one click. Copilot builds a complete invite for your review -title, agenda, attendee list, and a summary of the email conversation-plus attaches the original email thread so everyone is up to speed. Available in the new Outlook for Windows, web, Mac, and mobile. #newoutlookforwindows [Learn more](https://support.microsoft.com/office/create-a-meeting-and-agenda-with-copilot-in-outlook-31a44dfa-62bb-4751-82c4-14327a26759f).

### Teams

- **Microsoft Teams: Intelligent recap support for ad-hoc meetings and calls in GCC High** \[Android, Windows, iOS, Mac, Web\]

  Intelligent meeting recap is now available in GCC High for impromptu calls and meetings, like those started from 'Meet now' and calls started from chat. You can easily browse the recording by speakers and topics, as well as access AI-generated notes, AI-generated tasks, and name mentions after the ad-hoc meeting ends. This capability is available for users with a Teams Premium or M365 Copilot license.

## Updates between May 13, 2025

Updates released between April 29, 2025, and May 13, 2025.

### Microsoft 365 Copilot Chat

- **Image generation in mobile Copilot chat** \[Android, iOS\]

  Create images using natural language to visualize concepts and ideas within the flow of work, directly in Copilot on Microsoft 365, Teams, and Outlook mobile apps.

## April 2, 2025 updates

Updates released between March 20, 2025, and April 2, 2025.

### Microsoft 365 Copilot Chat

- **Ask questions about images with natural language** \[Android, iOS, Web\]

  Easily gain insights from images by asking natural language questions. Upload images for quick analysis using advanced vision models-helping you make sense of visual data across your apps.

## March 19, 2025

Updates released between March 5, 2025, and March 19, 2025.

### Microsoft 365 Copilot app

- **View, edit and share Copilot Pages on mobile** \[Android, iOS\]

  Stay productive while on the go-use the Microsoft 365 mobile app to view, edit, or share Copilot-generated pages instantly. Collaborate with colleagues in real time, whether you're commuting or between meetings. [Learn more](https://support.microsoft.com/topic/introducing-microsoft-365-copilot-pages-6674bd51-9ff5-42c4-9256-44d9428a726f).

## March 4, 2025

Updates released between February 20, 2025, and March 4, 2025.

### Microsoft 365 Copilot Chat

- **Search archived mailboxes in Copilot Chat** \[Windows, Web, Android, iOS, Mac\]

  Leverage Copilot to search emails across both primary and archived mailboxes by appending 'from my archives' or 'also look for emails in my archives' in your prompts to quickly locate key messages.

## February 19, 2025

Updates released between February 5, 2025, and February 19, 2025.

### Microsoft Teams

- **AI-enabled file summaries on mobile** \[Android, iOS\]

  Summarize Word, PowerPoint, and PDF files on mobile by tapping the summary icon or selecting "Summarize with Copilot" for a quick, digestible overview-even on small screens.

### Viva Insights

- **Copilot dashboard for usage and retention insights** \[Windows, Web, Android, iOS, Mac\]

  Dive into usage frequency, compare top user groups, and track retention metrics-all in a single, comprehensive dashboard for actionable insights. [Learn more](https://learn.microsoft.com/en-us/viva/insights/org-team-insights/copilot-dashboard#interpreting-the-data).

## February 4, 2025

Updates released between January 24, 2025, and February 4, 2025.

### Microsoft 365 Copilot app

- **Updates to the Microsoft 365 \(Office\) app** \[Windows, Web, Android, iOS\]

  The Microsoft 365 Copilot app \(formerly Microsoft 365 app\) has a new name and icon. [Learn more](https://support.microsoft.com/office/the-microsoft-365-app-transition-to-the-microsoft-365-copilot-app-22eac811-08d6-4df3-92dd-77f193e354a5).

### Microsoft 365 Copilot Chat

- **Access support pages in Copilot Chat** \[Windows, Web, Android, iOS, Mac\]

  View organizational support pages directly within Copilot Chat, for quick help and guidance in your workflow.
- **Accommodate user's time zones in Copilot** \[Windows, Web, Android, iOS\]

  Copilot now references your local time zone when responding helping to avoid confusion and scheduling errors.

## January 23, 2025

Updates released between January 8, 2025, and January 23, 2025.

### Microsoft 365 Copilot Chat

- **Introducing Microsoft 365 Copilot Chat** \[Windows, Web, Android, iOS\]

  Microsoft 365 Copilot Chat-secure AI chat powered by GPT-4o with agents accessible right in chat, and IT controls including enterprise data protection and agent management. Copilot Chat serves as a powerful new on-ramp for everyone in your organization to build an AI habit. And it is included with your Microsoft 365 subscription. Get started with Copilot Chat with the updated [Microsoft 365 Copilot app](https://www.m365copilot.com) \(formerly Microsoft 365 app\). [Learn more](https://www.microsoft.com/microsoft-365/blog/2025/01/15/copilot-for-all-introducing-microsoft-365-copilot-chat).
- **Use Pages in compliant Copilot web chat** \[Android, Windows, iOS, Mac, Web\]

  Admins gain control to turn off file uploads for Copilot Chat, helping maintain compliance when sharing sensitive content.

## January 7, 2025

Updates released between December 18, 2024, and January 7, 2025.

### Microsoft 365 Copilot

- **Access Copilot Prompt Gallery in Word and PowerPoint mobile apps** \[Android, iOS\]

  Discover and use suggested Copilot prompts in Prompt Gallery within the Word and PowerPoint apps on iOS and Android. Enhance your productivity on the go with helpful AI suggestions.

### Outlook

- **Switch between Work and Web grounding in Microsoft 365 Copilot Chat** \[Android, iOS\]

  In Outlook mobile apps, you can now toggle between Microsoft 365 Graph \(Work\) and Web grounding in Microsoft 365 Copilot Chat. Choose the grounding source that best suits your needs for more personalized assistance.

### Viva Insights

- **New metrics for enterprise data-protected prompts** \[Windows, Web, Android, iOS, Mac\]

  Gain visibility into prompts submitted through Microsoft 365 Copilot Chat \(web\) and enterprise data-protected Copilot scenarios. [Learn more](https://learn.microsoft.com/en-us/viva/insights/advanced/reference/metrics#microsoft-365-copilot-metrics).

## December 23, 2025

Updates released between December 10, 2025, and December 23, 2025.

### Microsoft 365 Copilot app

- **GPT-5 powers Copilot Chat by default** \[Android, Windows, iOS, Mac, Web\]

  Copilot Chat delivers faster, smarter results using GPT-5 as the default model.

  **Details:**

  **What Changed:** All Copilot Chat experiences run on GPT-5 by default. Copilot automatically routes prompts to the best-performing models for each task, using fast models for basic tasks and specialized reasoning models for multi-step requests.

  **Why:** Users want speed, accuracy, and minimal friction. This update helps to ensure consistent, high-quality AI interactions in Copilot Chat.

  **Try This:**

  - "Get me up to speed on the latest plans related to \[project/initiative\]. Help me think through what to do next."
  - "Use the attached spreadsheet with customer feedback to create a polished executive report that helps upper management decide where to prioritize resources in our next cycle."


  **Why this matters:**


  **Business Impact:** Increases accuracy and productivity, helping teams make strong decisions and complete complex work faster.


  **Personal Impact:** Removes friction by letting Copilot choose the best model--fast or reasoning--for the prompt.


  **Additional resources:**


  **Blogs:**


  [Available today: GPT-5 in Microsoft 365 Copilot](https://www.microsoft.com/microsoft-365/blog/2025/08/07/available-today-gpt-5-in-microsoft-365-copilot/?msockid=281b58ceea286c6226164ec5eb056dd6)

### Microsoft 365 Copilot extensibility

- **Upload Larger Files in Copilot Studio Agent Builder** \[Android, Windows, iOS, Web\]

  Agent Builder now supports file uploads up to 512 MB when creating agents, ideal for larger files.

  **Roadmap ID:** [500375](https://www.microsoft.com/microsoft-365/roadmap?msockid=2484525e9a9b66d4330b47329bb667c9&filters=&searchterms=500375)

  **Details:**

  **What Changed:** This increases the upload size limit in Agent Builder to 512 MB, enabling use of larger files as grounding data.

  **Why:** Users requested more flexibility for grounding agents. Larger files improve reduce the need to split or compress documents.

  **Try This:**

  - Drag and drop large documents such as training manuals into your agent project.
  - Create the agent and ask it to summarize information from uploaded files.


  **Why this matters:**


  **Business Impact:** Allows enterprises to build agents with richer, domain-specific knowledge.


  **Personal Impact:** Complete your work without the need to split files or compress data.


  **Additional resources:**


  **Learn:**


  [Embedded file content](https://learn.microsoft.com/en-us/microsoft-365-copilot/extensibility/agent-builder-add-knowledge#embedded-file-content)

## November 25, 2025

Updates released between November 12, 2025, and November 25, 2025.

### Microsoft 365 Copilot Chat

- **Access shared mailboxes in Copilot Chat** \[Android, Windows, iOS, Mac, Web\]

  Copilot Chat now connects to shared mailboxes, so team-based conversations are more informed and collaborative.

  ****Roadmap ID:**** [488797](https://www.microsoft.com/microsoft-365/roadmap?msockid=2484525e9a9b66d4330b47329bb667c9&filters=&searchterms=488797)

  ****Details:****

  **What changed:** Users with shared mailbox permissions can ground Copilot responses in shared mail content, just like their own emails.

  ****Why:**** Eliminates context gaps in team workflows and improves shared visibility on projects.

  **Try this:**

  - Tell Copilot: *"Summarize recent emails in [mailbox@domain.com](mailto:mailbox@domain.com) mailbox."*
  - Tell Copilot: *"List all the emails around `topic` from < mailbox@domain.com > mailbox."*


  **Why this matters:**


  **Business Impact:** Ensures customer responses or project updates aren't missed when responsibility spans multiple team members.


  **Personal Impact:** Reduces copying and manual email checks across shared accounts-Copilot does it for you.


  **Additional resources:**


  [Use Copilot in shared mailboxes and delegate mailboxes](https://support.microsoft.com/topic/use-copilot-in-shared-mailboxes-and-delegate-mailboxes-3e7e5130-eabe-4c19-94ea-117b2a4c14d6)

- **Talk to Copilot with voice for faster hands-free work** \[Android, Windows, iOS, Mac, Web\]

  Speak to Copilot naturally on mobile or desktop to prepare for meetings, brainstorm ideas, or catch up on work-hands-free and grounded in work data.

  **Roadmap ID:** [481138](https://www.microsoft.com/microsoft-365/roadmap?msockid=2484525e9a9b66d4330b47329bb667c9&filters=&searchterms=481138)

  ****Details:****

  **What changed:**

  Copilot now supports voice input, enabling natural, conversational interactions in the Microsoft 365 Copilot app on mobile, desktop and the web and across Microsoft 365 apps, starting with Outlook, Word and PowerPoint.

  ****Why:****

  Professionals need faster, more intuitive ways to engage with AI during their flow of work, especially when multitasking or on the move. Voice removes friction, letting you work where typing isn't practical.

  **Try this:**

  - Say: *"Confirm the agenda and attendee list for my next meeting"*.
  - Try: *"Create a quick list of next steps from my recent meeting notes."*
  - Ask: *"Summarize this document in five key points."*


  **Why this Matters:**


  **Business Impact:** Voice drives productivity and inclusivity through natural interactions that increase engagement, accelerate task completion and reduce downtime.


  **Personal Impact:** Work more comfortably and naturally while saving time, gaining efficiency and giving you the flexibility to use Copilot on the go or at your desk.


  **Additional resources:**


  [Get started with voice features in Microsoft 365 Copilot](https://support.microsoft.com/topic/get-started-with-voice-features-in-microsoft-365-copilot-9262968d-565e-470c-a04b-991eb8e0d1ea)

### Microsoft 365 Copilot extensibility

- **Access Custom engine Agents on Microsoft 365 Copilot chat on mobile** \[Android, iOS\]

  You can now interact with your organization's custom engine agents directly from your mobile device \(iOS and Android\), making Copilot even more adaptable to your workflows on the go. Whether you're away from your desk or managing tasks during a commute, your tailored business logic and automations are always at your fingertips.

  ****Details:****

  **What changed:** Support for custom engine agents is now available on the Microsoft 365 mobile experience \(iOS and Android\). You can access the same business-specific workflows and logic you have on desktop, ensuring uninterrupted productivity.

  ****Why:**** Teams needs consistent, personalized Copilot functionality no matter where they work. Bringing extensibility to mobile ensures employees stay productive and connected-even when away from their primary workstation.

  **Try this:**

  - Open the Microsoft 365 mobile app, launch Copilot, and activate one of your custom engine agents.
  - **Ask Copilot:** *"Run our expense approval workflow and update me on pending approvals."*


  **Why this matters:**


  **Business Impact:** Keep critical business processes running smoothly even when employees are mobile, reducing delays in approvals and operations.


  **Personal Impact:** Enjoy the same customized Copilot experience wherever you work, saving time and reducing context-switching throughout your day.


  **Additional resources:**


  **Learn:**


  [Custom engine agents for Microsoft 365 overview](https://learn.microsoft.com/en-us/microsoft-365-copilot/extensibility/overview-custom-engine-agent)

- **Support Message Extensions as Declarative Agents on Mobile** \[Android, iOS\]

  Stay productive on the move with support for message extensions as declarative agents in Copilot on iOS and Android. These extensions simplify workflows like inserting quick snippets, accessing integrated apps, or triggering processes directly from your mobile interface.

  ****Details:****

  **What changed:**

  Message extensions based Declarative agents" instead of "Message extensions as declarative agents.

  ****Why:****

  Workers increasingly use mobile as their primary device for timely communication and task management. Extending message-based workflows to mobile keeps teams efficient and responsive.

  **Try this:**

  - In a Teams chat on your mobile app, use Copilot to insert a dynamic update from a connected app with a message extension.
  - **Ask Copilot:** *"Insert the latest sales figures into this conversation using our message extension agent."*


  **Why this matters:**


  **Business Impact:** Maintain seamless workflows across devices, ensuring real-time communication and agility for distributed teams.


  **Personal Impact:** Eliminate the frustration of being restricted to desktop for advanced actions-get the information and tools you need on the go.


  **Additional resources:**


  **Learn:**


  [Extend bot-based message extension as agent for Microsoft 365 Copilot](https://learn.microsoft.com/en-us/microsoftteams/platform/messaging-extensions/build-bot-based-agent?tabs=visual-studio-code)

## October 28, 2025

Updates released between October 15, 2025, and October 28, 2025.

### Copilot extensibility

- **@mention capability for mainline Copilot Chat** \[Android, iOS\]

  Use @mention in Copilot Chat to direct interactions to specific agents, ensuring focused and relevant responses from Copilot.

### PowerPoint

- **Copilot now offers an on-canvas experience for generating speaker notes** \[Mac, Web, iOS\]

  Now, Copilot in PowerPoint offers an on-canvas experience to generate speaker notes in place of the previous chat experience. [Learn more](https://support.microsoft.com/topic/add-speaker-notes-to-your-presentations-using-copilot-7139266b-8a1d-4056-8e30-4edcc4d80873).
- **PPT Copilot now offers an on-canvas experience for translating presentation** \[Mac, Web, iOS\]

  Now, when creating a presentation using Copilot from an existing presentation, it creates the new presentation in a new file without affecting the original presentation. [Learn more](https://support.microsoft.com/topic/rewrite-text-with-copilot-in-powerpoint-d70b140b-bb3f-46b7-be64-ceec526a8dcd#:%7E:text=Select%20the%20textbox%20containing%20the%20text%20you%20want,for%20general%20improvements%20in%20grammar%2C%20spelling%2C%20and%20clarity.).

## September 30, 2025

Updates released between September 16, 2025, and September 30, 2025.

### Copilot extensibility

- **Agents support for Copilot Chat and pay-as-you-go on Microsoft 365 Copilot Mobile** \[Android, iOS\]

  Agents support for pay-as-you-go and Copilot chat users in now supported on the Microsoft 365 Copilot mobile app for easy usage.

### Microsoft 365 admin center

- **Usage reports for Copilot search** \[Android, Windows, iOS, Mac, Web\]

  Administrators gain insights into organizational adoption of Copilot search with new usage reports. Track total search queries, assess trends, and analyze user activity to drive effective adoption strategies. [Learn more](https://learn.microsoft.com/en-us/microsoft-365/admin/activity-reports/microsoft-365-copilot-search-usage).

### Microsoft 365 Copilot Chat

- **Copilot Chat now understands attached files like Word, Excel, PowerPoint, PDF, Text, JSON, and XML.** \[Android, Windows, iOS, Mac, Web\]

  Users can gather insights not only from the email content but also from attached files, enabling comprehensive context understanding.
- **Upload multiple images for creative prompts** \[Android, iOS, Web\]

  Now upload multiple images into Copilot Chat prompts at once to enhance creative reasoning and generate new content with varied inspiration.

## September 16, 2025

Updates released between September 3, 2025, and September 16, 2025.

### Copilot extensibility

- **Mobile support for Analyst agent on Android and iOS** \[iOS, Android\]

  Access and utilize the Analyst agent on iOS and Android devices using the Microsoft 365 Copilot app, ensuring seamless mobile insights and analysis.
- **Viral link sharing on M365 Copilot Mobile \(Android and iOS\)** \[Android, iOS\]

  Simplify collaboration with Agents with support for agent viral links on M365 Copilot app on Mobile, enhancing accessibility and engagement.

### Microsoft 365 Copilot app

- **Direct access to Copilot Chat in Microsoft 365 app** \[Android, iOS\]

  Microsoft 365 Copilot mobile app is removing bottom tabs and will open directly on Chat for eligible users, making it simpler and easier to chat with Copilot.
- **Microsoft 365 Copilot Search** \[Android, Windows, iOS, Web\]

  Copilot Search is the intelligent search experience within the Microsoft 365 Copilot app, designed to deliver fast, secure, and context-aware results across your organization's data. It enables users to search across emails, files, chats, meetings, and even third-party platforms like Salesforce, Jira, and Confluence using natural language queries. [Learn more](https://learn.microsoft.com/en-us/microsoft-365/copilot/microsoft-365-copilot-search).

### Outlook

- **Schedule meetings effortlessly from email threads** \[iOS\]

  Use Copilot to quickly schedule meetings by analyzing email threads, crafting invitations, and including attendees-all with ease. [Learn more](https://support.microsoft.com/office/create-a-meeting-and-agenda-with-copilot-in-outlook-31a44dfa-62bb-4751-82c4-14327a26759f)

## September 3, 2025

Updates released between August 19, 2025, and September 3, 2025.

### Microsoft 365 Copilot app

- **Enrich agents with Store integration on mobile** \[Android, iOS\]

  Access and enhance agents through the Agent Store on mobile, making it easier to deploy and manage new capabilities on the go.
- **Use Copilot in PDFs on mobile** \[Android, iOS\]

  Eligible users can now leverage Copilot within PDF files in the Microsoft 365 mobile app. Easily ask questions, gather summaries, and extract key insights from your PDFs for more efficient content understanding on the go.

### Microsoft 365 Copilot Chat

- **Personalize interactions with Copilot Memory** \[Android, iOS, Web\]

  Copilot Memory leverages insights inferred from conversations between the user and Copilot, along with data from the Microsoft Graph and custom instructions to provide personalized help for tasks. Users have full control and can view, manage, disable or clear memory at any time. [Learn more](https://techcommunity.microsoft.com/blog/microsoft365copilotblog/introducing-copilot-memory-a-more-productive-and-personalized-ai-for-the-way-you/4432059).

## August 19, 2025

Updates released between August 5, 2025, and August 19, 2025.

### Microsoft 365 Copilot app

- **Expanded language options with Microsoft 365 Copilot** \[Android, Windows, iOS, Mac, Web\]

  Microsoft 365 Copilot now supports six additional languages: Albanian, Filipino, Icelandic, Malay, Maltese, and Serbian \(Cyrillic\). [Learn more](https://support.microsoft.com/office/supported-languages-for-microsoft-365-copilot-94518d61-644b-4118-9492-617eea4801d8).

### Microsoft 365 Copilot Chat

- **Advanced data analysis in Copilot Chat mobile apps** \[Android, iOS\]

  Solve complex tasks by generating and executing Python code with the advanced reasoning model in Copilot Chat mobile apps.

### Outlook

- **Summarize email attachments with Copilot** \[Android, Windows, iOS, Mac, Web\]

  Summarize PDF, Word, and PPT email attachments effortlessly in Outlook Web and the new Outlook for Windows, making it easier to extract key information without needing to open each file. [Learn more](https://support.microsoft.com/office/summarize-an-email-thread-with-copilot-in-outlook-a79873f2-396b-46dc-b852-7fe5947ab640#id0ebbj=new_outlook).

## July 8, 2025

Updates released between June 24, 2025, and July 8, 2025.

### Viva Connections

- **New News feature in Microsoft Teams** \[Android, Windows, iOS, Web\]

  This update replaces the current Feed experience in Viva Connections across desktop, mobile, and web platforms with a SharePoint News reader experience. This new experience presents SharePoint news from organizational sites, boosted news, users' followed sites, frequent sites, and people they work with in an immersive reader format. It includes a Copilot-powered news summary as well, available only in Teams for Windows desktop in this initial release. [Learn more](https://techcommunity.microsoft.com/blog/viva_connections_blog/introducing-enterprise-news-reader-in-viva-connections/4383832).

## June 24, 2025

Updates released between June 10, 2025, and June 24, 2025.

### Excel

- **Use Copilot with any table in the workbook, referring by natural language** \[iOS, Web, Mac, Windows\]

  Copilot uses the context of your prompt to pick what selection of data to answer about and reason over, including tables in other sheets. [Learn more](https://techcommunity.microsoft.com/blog/excelblog/smarter-context-awareness-for-copilot-in-excel/4424939).

## June 10, 2025

Updates released between May 29, 2025, and June 10, 2025.

### Microsoft Loop

- **Copilot Pages module on Microsoft 365 Copilot mobile app** \[iOS\]

  With the Copilot Pages module in the Microsoft 365 Copilot app on your mobile, you can now access all of your Pages in one place on the go. [Learn more](https://support.microsoft.com/topic/create-edit-and-share-microsoft-365-copilot-pages-from-your-phone-6426dfd5-081c-4a9f-b35e-830685deeda7).
- **Create Copilot Pages from Copilot Chat on your mobile phone** \[iOS\]

  Create Copilot Pages on your mobile phone to continue working on the go. Pages shared in Microsoft 365 are interactive and automatically synchronized for seamless collaboration. [Learn more](https://support.microsoft.com/topic/create-edit-and-share-microsoft-365-copilot-pages-from-your-phone-6426dfd5-081c-4a9f-b35e-830685deeda7).

### Outlook

- **Custom Instructions for draft with Copilot** \[Android, Windows, iOS, Mac, Web\]

  Give Copilot some instructions about your emails - like the tone, length, greeting - so your Copilot generated drafts sound more like you want them to. #newoutlookforwindow
- **Schedule a meeting from an email with Copilot** \[Android, Windows, iOS, Mac, Web\]

  Turn any email thread into a meeting in one click. Copilot builds a complete invite for your review -title, agenda, attendee list, and a summary of the email conversation-plus attaches the original email thread so everyone is up to speed. Available in the new Outlook for Windows, web, Mac, and mobile. #newoutlookforwindows [Learn more](https://support.microsoft.com/office/create-a-meeting-and-agenda-with-copilot-in-outlook-31a44dfa-62bb-4751-82c4-14327a26759f).

### Teams

- **Microsoft Teams: Intelligent recap support for ad-hoc meetings and calls in GCC High** \[Android, Windows, iOS, Mac, Web\]

  Intelligent meeting recap is now available in GCC High for impromptu calls and meetings, like those started from 'Meet now' and calls started from chat. You can easily browse the recording by speakers and topics, as well as access AI-generated notes, AI-generated tasks, and name mentions after the ad-hoc meeting ends. This capability is available for users with a Teams Premium or M365 Copilot license.

## May 13, 2025

Updates released between April 29, 2025, and May 13, 2025.

### Excel

- **Ask Copilot about any part of your sheet** \[Web, Mac, Windows, iOS\]

  When you ask questions about your worksheet, Copilot can look at the content of your sheet and use it to inform an answer to your question. This includes understanding worksheet data on your selected area, beyond tables and ranges, and provide Copilot answers in chat.

### Microsoft 365 Copilot Chat

- **Image generation in mobile Copilot chat** \[Android, iOS\]

  Create images using natural language to visualize concepts and ideas within the flow of work, directly in Copilot on Microsoft 365, Teams, and Outlook mobile apps.

## April 2, 2025 updates

Updates released between March 20, 2025, and April 2, 2025.

### Microsoft 365 Copilot Chat

- **Ask questions about images with natural language** \[Android, iOS, Web\]

  Easily gain insights from images by asking natural language questions. Upload images for quick analysis using advanced vision models-helping you make sense of visual data across your apps.

### Word

- **Narrate your ideas to Copilot** \[iOS\]

  Brainstorm out loud and let Copilot convert your voice notes into structured documents, making it easier to organize and develop your ideas.
- **Rewrite with Copilot** \[iOS\]

  Get suggestions from Copilot on how to rewrite any text, helping you improve clarity and style effortlessly.
- **Visualize as table** \[iOS\]

  Easily convert plain text into structured tables, helping you organize and present data more effectively in your daily work.

## March 19, 2025

Updates released between March 5, 2025, and March 19, 2025.

### Microsoft 365 Copilot app

- **View, edit and share Copilot Pages on mobile** \[Android, iOS\]

  Stay productive while on the go-use the Microsoft 365 mobile app to view, edit, or share Copilot-generated pages instantly. Collaborate with colleagues in real time, whether you're commuting or between meetings. [Learn more](https://support.microsoft.com/topic/introducing-microsoft-365-copilot-pages-6674bd51-9ff5-42c4-9256-44d9428a726f).

## March 4, 2025

Updates released between February 20, 2025, and March 4, 2025.

### Microsoft 365 Copilot Chat

- **Search archived mailboxes in Copilot Chat** \[Windows, Web, Android, iOS, Mac\]

  Leverage Copilot to search emails across both primary and archived mailboxes by appending 'from my archives' or 'also look for emails in my archives' in your prompts to quickly locate key messages.

### Microsoft 365 Copilot app

- **View, edit and share Copilot Pages on mobile** \[iOS\]

  Stay productive no matter where you are. With mobile access to Copilot Pages, you can view, edit, and share content on the go, ensuring seamless collaboration with colleagues. [Learn more](https://support.microsoft.com/topic/introducing-microsoft-365-copilot-pages-6674bd51-9ff5-42c4-9256-44d9428a726f).

## February 19, 2025

Updates released between February 5, 2025, and February 19, 2025.

### Microsoft Teams

- **AI-enabled file summaries on mobile** \[Android, iOS\]

  Summarize Word, PowerPoint, and PDF files on mobile by tapping the summary icon or selecting "Summarize with Copilot" for a quick, digestible overview-even on small screens.

### Viva Insights

- **Copilot dashboard for usage and retention insights** \[Windows, Web, Android, iOS, Mac\]

  Dive into usage frequency, compare top user groups, and track retention metrics-all in a single, comprehensive dashboard for actionable insights. [Learn more](https://learn.microsoft.com/en-us/viva/insights/org-team-insights/copilot-dashboard#interpreting-the-data).

## February 4, 2025

Updates released between January 24, 2025, and February 4, 2025.

### Microsoft 365 Copilot app

- **Updates to the Microsoft 365 \(Office\) app** \[Windows, Web, Android, iOS\]

  The Microsoft 365 Copilot app \(formerly Microsoft 365 app\) has a new name and icon. [Learn more](https://support.microsoft.com/office/the-microsoft-365-app-transition-to-the-microsoft-365-copilot-app-22eac811-08d6-4df3-92dd-77f193e354a5).

### Microsoft 365 Copilot Chat

- **Access support pages in Copilot Chat** \[Windows, Web, Android, iOS, Mac\]

  View organizational support pages directly within Copilot Chat, for quick help and guidance in your workflow.
- **Accommodate user's time zones in Copilot** \[Windows, Web, Android, iOS\]

  Copilot now references your local time zone when responding helping to avoid confusion and scheduling errors.

### Word

- **Draft from selected text, lists, or tables** \[iOS\]

  Generate new content right where you work by selecting text, lists, or tables and tapping into Copilot's on-canvas menu. Quickly refine drafts and collaborate more interactively. [Learn more](https://techcommunity.microsoft.com/blog/microsoft365copilotblog/draft-with-copilot-in-word-on-a-selection-of-text-a-list-or-a-table/4191926).
- **Draft with Copilot** \[iOS\]

  Quickly produce paragraphs or entire sections for your documents, whether you're creating a brand-new file or adding to existing text. [Learn more](https://support.microsoft.com/office/draft-and-add-content-with-copilot-in-word-069c91f0-9e42-4c9a-bbce-fddf5d581541).

## January 23, 2025

Updates released between January 8, 2025, and January 23, 2025.

### Microsoft 365 Copilot Chat

- **Introducing Microsoft 365 Copilot Chat** \[Windows, Web, Android, iOS\]

  Microsoft 365 Copilot Chat-secure AI chat powered by GPT-4o with agents accessible right in chat, and IT controls including enterprise data protection and agent management. Copilot Chat serves as a powerful new on-ramp for everyone in your organization to build an AI habit. And it is included with your Microsoft 365 subscription. Get started with Copilot Chat with the updated [Microsoft 365 Copilot app](https://www.m365copilot.com) \(formerly Microsoft 365 app\). [Learn more](https://www.microsoft.com/microsoft-365/blog/2025/01/15/copilot-for-all-introducing-microsoft-365-copilot-chat).
- **Use Pages in compliant Copilot web chat** \[Android, Windows, iOS, Mac, Web\]

  Admins gain control to turn off file uploads for Copilot Chat, helping maintain compliance when sharing sensitive content.

### Viva Insights

- **New Copilot adoption metrics and completing total actions taken** \[Windows, iOS, Mac\]

  This adds seven new Copilot adoption metrics to the Copilot dashboard and Viva Insights Advanced insights. It also updates the "total actions taken" metric in the Copilot dashboard to include these new Copilot adoption metrics. [Learn more](https://techcommunity.microsoft.com/blog/viva_insights_blog/new-microsoft-copilot-analytics-features-now-available-%E2%80%93-novemberdecember-2024/4356206).

## January 7, 2025

Updates released between December 18, 2024, and January 7, 2025.

### Microsoft 365 Copilot

- **Access Copilot Prompt Gallery in Word and PowerPoint mobile apps** \[Android, iOS\]

  Discover and use suggested Copilot prompts in Prompt Gallery within the Word and PowerPoint apps on iOS and Android. Enhance your productivity on the go with helpful AI suggestions.

### Outlook

- **Switch between Work and Web grounding in Microsoft 365 Copilot Chat** \[Android, iOS\]

  In Outlook mobile apps, you can now toggle between Microsoft 365 Graph \(Work\) and Web grounding in Microsoft 365 Copilot Chat. Choose the grounding source that best suits your needs for more personalized assistance.

### Viva Insights

- **Expand your understanding of Copilot adoption with enhanced metrics** \[Windows, iOS, Mac\]

  Access seven new Copilot metrics and see them reflected in "total actions taken," helping you better track how teams use Copilot. [Learn more](https://learn.microsoft.com/en-us/viva/insights/advanced/analyst/templates/microsoft-365-copilot-adoption).
- **New metrics for enterprise data-protected prompts** \[Windows, Web, Android, iOS, Mac\]

  Gain visibility into prompts submitted through Microsoft 365 Copilot Chat \(web\) and enterprise data-protected Copilot scenarios. [Learn more](https://learn.microsoft.com/en-us/viva/insights/advanced/reference/metrics#microsoft-365-copilot-metrics).

## December 23, 2025

Updates released between December 10, 2025, and December 23, 2025.

### Microsoft 365 Copilot app

- **GPT-5 powers Copilot Chat by default** \[Android, Windows, iOS, Mac, Web\]

  Copilot Chat delivers faster, smarter results using GPT-5 as the default model.

  **Details:**

  **What Changed:** All Copilot Chat experiences run on GPT-5 by default. Copilot automatically routes prompts to the best-performing models for each task, using fast models for basic tasks and specialized reasoning models for multi-step requests.

  **Why:** Users want speed, accuracy, and minimal friction. This update helps to ensure consistent, high-quality AI interactions in Copilot Chat.

  **Try This:**

  - "Get me up to speed on the latest plans related to \[project/initiative\]. Help me think through what to do next."
  - "Use the attached spreadsheet with customer feedback to create a polished executive report that helps upper management decide where to prioritize resources in our next cycle."


  **Why this matters:**


  **Business Impact:** Increases accuracy and productivity, helping teams make strong decisions and complete complex work faster.


  **Personal Impact:** Removes friction by letting Copilot choose the best model--fast or reasoning--for the prompt.


  **Additional resources:**


  **Blogs:**


  [Available today: GPT-5 in Microsoft 365 Copilot](https://www.microsoft.com/microsoft-365/blog/2025/08/07/available-today-gpt-5-in-microsoft-365-copilot/?msockid=281b58ceea286c6226164ec5eb056dd6)

### PowerPoint

- **Use your organization's approved assets in Copilot presentations** \[Mac, Windows, Web\]

  Create branded PowerPoint slides by pulling images and templates from your company's SharePoint asset library or Templafy integration.

  **Roadmap:** 496366

  **What changed:** PowerPoint Copilot integrates with SharePoint Organization Asset Library and Templafy for approved, compliant visuals.

  **Why:** Ensures quality designs aligned with corporate branding guidelines.

  **Try This:**

  - Configure SharePoint OAL or Templafy in Microsoft 365
  - Ask Copilot: "Create a marketing update deck using brand imagery."


  **Why this matters:**


  **Business impact:**: Maintains brand identity across all content.


  **Personal Impact:** Saves design time by eliminating manual asset searching.


  **Additional resources:** [Learn more.](https://learn.microsoft.com/en-us/sharepoint/organization-assets-library)

## November 25, 2025

Updates released between November 12, 2025, and November 25, 2025.

### Microsoft 365 admin center

- **Monitor Copilot usage with Capacity Packs** \[Mac\]

  Prepay for Copilot message consumption with Capacity Packs and track usage easily-reducing unexpected billing surprises.

  **Roadmap ID:** [503145](https://www.microsoft.com/microsoft-365/roadmap?filters=&searchterms=503145)

  ****Details:****

  **What changed:** Introduced prepaid Capacity Packs \(25,000 messages per month\) that apply before pay-as-you-go billing kicks in, plus usage monitoring in PPAC.

  ****Why:**** Improves cost governance and simplifies budgeting for large-scale Copilot deployments.

  **Try this:**

  - In Microsoft 365 admin center, purchase a Capacity Pack and monitor allocations in Power Platform admin center.


  **Why this matters:**


  **Business Impact:** Predicts and controls Copilot spend with flexible prepaid options.


  **Personal Impact:** Gives admins peace of mind with transparent, upfront budgeting.


  **Additional resources:**


  **Learn:**


  [Manage Microsoft 365 Copilot in Teams meetings and events](https://learn.microsoft.com/en-us/microsoftteams/copilot-teams-transcription)


  [Use Copilot Studio prepaid capacity packs for Microsoft 365 Copilot Chat and SharePoint agents](https://learn.microsoft.com/en-us/microsoft-365/copilot/pay-as-you-go/copilot-capacity-packs)

### Microsoft 365 Copilot Chat

- **Access shared mailboxes in Copilot Chat** \[Android, Windows, iOS, Mac, Web\]

  Copilot Chat now connects to shared mailboxes, so team-based conversations are more informed and collaborative.

  ****Roadmap ID:**** [488797](https://www.microsoft.com/microsoft-365/roadmap?msockid=2484525e9a9b66d4330b47329bb667c9&filters=&searchterms=488797)

  ****Details:****

  **What changed:** Users with shared mailbox permissions can ground Copilot responses in shared mail content, just like their own emails.

  ****Why:**** Eliminates context gaps in team workflows and improves shared visibility on projects.

  **Try this:**

  - Tell Copilot: *"Summarize recent emails in [mailbox@domain.com](mailto:mailbox@domain.com) mailbox."*
  - Tell Copilot: *"List all the emails around `topic` from < mailbox@domain.com > mailbox."*


  **Why this matters:**


  **Business Impact:** Ensures customer responses or project updates aren't missed when responsibility spans multiple team members.


  **Personal Impact:** Reduces copying and manual email checks across shared accounts-Copilot does it for you.


  **Additional resources:**


  [Use Copilot in shared mailboxes and delegate mailboxes](https://support.microsoft.com/topic/use-copilot-in-shared-mailboxes-and-delegate-mailboxes-3e7e5130-eabe-4c19-94ea-117b2a4c14d6)

- **Talk to Copilot with voice for faster hands-free work** \[Android, Windows, iOS, Mac, Web\]

  Speak to Copilot naturally on mobile or desktop to prepare for meetings, brainstorm ideas, or catch up on work-hands-free and grounded in work data.

  **Roadmap ID:** [481138](https://www.microsoft.com/microsoft-365/roadmap?msockid=2484525e9a9b66d4330b47329bb667c9&filters=&searchterms=481138)

  ****Details:****

  **What changed:** Copilot now supports voice input, enabling natural, conversational interactions in the Microsoft 365 Copilot app on mobile, desktop and the web and across Microsoft 365 apps, starting with Outlook, Word and PowerPoint.

  ****Why:**** Professionals need faster, more intuitive ways to engage with AI during their flow of work, especially when multitasking or on the move.

  **Try this:**

  - Say: *"Confirm the agenda and attendee list for my next meeting"*.
  - Try: *"Create a quick list of next steps from my recent meeting notes."*
  - Ask: *"Summarize this document in five key points."*


  **Why this Matters:**


  **Business Impact:** Voice drives productivity and inclusivity through natural interactions that increase engagement, accelerate task completion and reduce downtime.


  **Personal Impact:** Work more comfortably and naturally while saving time, gaining efficiency and giving you the flexibility to use Copilot on the go or at your desk.


  **Additional resources:**


  [Get started with voice features in Microsoft 365 Copilot](https://support.microsoft.com/topic/get-started-with-voice-features-in-microsoft-365-copilot-9262968d-565e-470c-a04b-991eb8e0d1ea)

### Microsoft 365 PowerPoint

- **Reference Loop or Page in presentations** \[Mac, Windows, Web\]

  When building a presentation with Copilot, you can now pull in content from Loop components or pages for fully integrated and up-to-date slides.

  ****Roadmap ID:**** [500864](https://www.microsoft.com/microsoft-365/roadmap?msockid=2484525e9a9b66d4330b47329bb667c9&filters=&searchterms=500864)

  ****Details:****

  **What changed:**

  Copilot for PowerPoint supports referencing Loop components and pages across PC, Mac, and web.

  ****Why:****

  Ensures your presentations reflect the latest collaborative content without manual copy-paste.

  **Try this:**

  - **Ask Copilot:** *"Create a status update deck using the project details from our Loop page."*


  **Why this matters:**


  **Business Impact:** Align updates across teams without tedious content migration.


  **Personal Impact:** Save time by reusing the content you already co-created, in just one step.

## November 12, 2025

Updates released between October 28, 2025, and November 12, 2025.

### Excel

- **Build and analyze surveys with ease using Surveys Agent** \[Windows, Mac, Web\]

  Let Surveys Agent handle the heavy lifting-from writing questions to launching surveys and breaking down results. It's like having a professional researcher inside Copilot, helping you make quick, data-driven decisions. [Learn more](https://aka.ms/SurveysAgentAvailable).

### Microsoft 365 Copilot Chat

- **Iterate on images with multi-turn editing** \[Windows, Mac, Web\]

  Copilot Chat now makes visual creation more flexible and intuitive. Upload reference images, edit them step by step, and maintain consistency across versions-perfect for refining designs for presentations, social posts, or print.

### PowerPoint

- **Create new presentations without overwriting your original** \[Windows, Mac, Web\]

  When you use Copilot to generate a presentation from an existing one, it now creates a separate file-keeping your original content safe for future use. Perfect for creating tailored decks without starting from scratch. [Learn more](https://support.microsoft.com/office/create-a-new-presentation-with-copilot-in-powerpoint-3222ee03-f5a4-4d27-8642-9c387ab4854d).

## October 28, 2025

Updates released between October 15, 2025, and October 28, 2025.

### PowerPoint

- **Copilot now offers an on-canvas experience for generating speaker notes** \[Mac, Web, iOS\]

  Now, Copilot in PowerPoint offers an on-canvas experience to generate speaker notes in place of the previous chat experience [Learn more](https://support.microsoft.com/topic/add-speaker-notes-to-your-presentations-using-copilot-7139266b-8a1d-4056-8e30-4edcc4d80873).
- **PPT Copilot now offers an on-canvas experience for translating presentation** \[Mac, Web, iOS\]

  Now, when creating a presentation using Copilot from an existing presentation, it creates the new presentation in a new file without affecting the original presentation [Learn more](https://support.microsoft.com/topic/rewrite-text-with-copilot-in-powerpoint-d70b140b-bb3f-46b7-be64-ceec526a8dcd#:%7E:text=Select%20the%20textbox%20containing%20the%20text%20you%20want,for%20general%20improvements%20in%20grammar%2C%20spelling%2C%20and%20clarity.).

### Teams

- **Use Copilot in a call without recording or transcribing** \[Windows, Mac\]

  Now, users can benefit from Copilot during live Teams calls with sensitive conversations where a persistent record is not desired. When the admin enables this option, users can initiate Copilot without transcription or recording simply through clicking the Copilot button in the header menu, so they can use important Copilot administrative tasks such as capturing key points, task owners, and next steps, enabling participants to stay focused on the content of the call. [Learn more](https://learn.microsoft.com/en-us/microsoftteams/copilot-teams-calling-transcription#only-during-the-call).

### Viva Insights

- **Weekly user insights in Copilot Studio agent reports",** \[Windows, Mac, Web\]

  Copilot Studio reports now include weekly active user counts and provide aggregated data on a weekly basis for consistency across reporting. These updates make it easier to track engagement trends for planning and adoption.", [Learn more](https://learn.microsoft.com/en-us/viva/insights/advanced/analyst/templates/copilot-studio-agents).

### Word

- **Instantly get helpful options from Copilot** \[Mac\]

  The Copilot icon in your document margin gives you a variety of actions you can take on your selected text. One click lets you rewrite, get writing suggestions, and more

## October 15, 2025

Updates released between September 30, 2025, and October 15, 2025.

### Microsoft 365 Copilot Chat

- **Create new images using reference uploads** \[Windows, Mac, Web\]

  Enhance image creation by uploading reference images in Copilot Chat, using them as creative foundations for new visuals.
- **Image generation with multiple aspect ratios** \[Windows, Mac, Web\]

  Generate images in various aspect ratios to suit any need, from social media to presentations, with landscape, portrait, and square options in Copilot Chat.

## September 30, 2025

Updates released between September 16, 2025, and September 30, 2025.

### Microsoft 365 admin center

- **Usage reports for Copilot search** \[Android, Windows, iOS, Mac, Web\]

  Administrators gain insights into organizational adoption of Copilot search with new usage reports. Track total search queries, assess trends, and analyze user activity to drive effective adoption strategies. [Learn more](https://learn.microsoft.com/en-us/microsoft-365/admin/activity-reports/microsoft-365-copilot-search-usage).

### Microsoft 365 Copilot Chat

- **Copilot Chat now understands attached files like Word, Excel, PowerPoint, PDF, Text, JSON, and XML.** \[Android, Windows, iOS, Mac, Web\]

  Users can gather insights not only from the email content but also from attached files, enabling comprehensive context understanding.

### PowerPoint

- **Seamlessly add topics with Copilot** \[Mac, Web, Windows\]

  Enhance your presentations by adding new topics with slides via Copilot, ensuring consistency in look and feel with existing content. [Learn more](https://support.microsoft.com/topic/add-topics-to-your-existing-powerpoint-presentation-with-copilot-7439e3d7-5b7f-4886-8d01-5e7f285fd99b?preview=true).

## September 3, 2025

Updates released between August 19, 2025, and September 3, 2025.

### PowerPoint

- **Excel data when building a presentation** \[Web, Mac, Windows\]

  You can now reference an Excel file when you create a presentation with Copilot within the PowerPoint application. [Learn more](https://support.microsoft.com/office/create-a-new-presentation-with-copilot-in-powerpoint-3222ee03-f5a4-4d27-8642-9c387ab4854d).

## August 19, 2025

Updates released between August 5, 2025, and August 19, 2025.

### Microsoft 365 Copilot app

- **Expanded language options with Microsoft 365 Copilot** \[Android, Windows, iOS, Mac, Web\]

  Microsoft 365 Copilot now supports six additional languages: Albanian, Filipino, Icelandic, Malay, Maltese, and Serbian \(Cyrillic\). [Learn more](https://support.microsoft.com/office/supported-languages-for-microsoft-365-copilot-94518d61-644b-4118-9492-617eea4801d8).

### Outlook

- **Summarize email attachments with Copilot** \[Android, Windows, iOS, Mac, Web\]

  Summarize PDF, Word, and PPT email attachments effortlessly in Outlook Web and the new Outlook for Windows, making it easier to extract key information without needing to open each file. [Learn more](https://support.microsoft.com/office/summarize-an-email-thread-with-copilot-in-outlook-a79873f2-396b-46dc-b852-7fe5947ab640#id0ebbj=new_outlook).

## August 5, 2025

Updates released between July 22, 2025, and August 5, 2025.

### Copilot extensibility

- **Enhance agent builder with full screen mode** \[Windows, Mac, Web\]

  Enjoy an improved agent builder experience with a full-screen view that streamlines the process of creating and managing your agents. [Learn more](https://learn.microsoft.com/en-us/microsoft-365-copilot/extensibility/copilot-studio-agent-builder-build).

### PowerPoint

- **Copilot uses enterprise assets hosted on SharePoint OAL when creating presentations now** \[Mac, Windows, Web\]

  Once you integrate your organization's assets into a Sharepoint OAL \(Organization Asset Library\) you will be able to create presentations with your organization's image.
- **Copilot uses Enterprise assets hosted on Templafy when creating presentations now** \[Mac, Windows, Web\]

  Once you connect your asset library hosted with Templafy to Microsoft365 and Copilot, you will be able to create presentations with your organization's images.

### Teams

- **Interpreter agent for seamless communication** \[Windows, Mac\]

  Interpreter Agent acts like an instant translator during your Teams meetings. It listens to the spoken language in a meeting and immediately translates it into another language in real-time. This allows participants who speak different languages to understand each other and collaborate more effectively without waiting. Whether you're holding a business meeting, customer calls, or project discussions, the AI interpreter in Teams ensures everyone can participate fully, enhancing communication and productivity across diverse teams. It supports 9 different languages: English, Italian, German, French, Portuguese \(Brazil\), Japanese, Spanish, Chinese \(Mandarin\), and Korean. [Learn more](https://support.microsoft.com/office/interpreter-in-microsoft-teams-meetings-c7efe2bb-535d-42ab-a5c4-d2d91619b46d).
- **Translated Intelligent meeting recap for multilingual meetings \(Copilot and Teams Premium\)** \[Windows, Mac\]

  Now, intelligent meeting recap supports multilingual meetings, ensuring you can easily catch up on key discussions even when multiple languages were spoken. After the meeting, your recap is automatically generated in the translation language you selected for live transcription and captions. [Learn more](https://support.microsoft.com/office/recap-in-microsoft-teams-c2e3a0fe-504f-4b2c-bf85-504938f110ef).

### Word

- **Use Writing suggestions to review content in Word** \[Mac\]

  Enhance your document content with AI-generated writing suggestion in the Copilot context menu. Get suggestions on logical structure, flow, and tone to make your documents more impactful. [Learn more](https://support.microsoft.com/topic/use-writing-suggestions-to-review-content-in-word-fa09c055-d623-4d20-954f-9b064a5a7c80).

## July 22, 2025

Updates released between July 8, 2025, and July 22, 2025.

### Microsoft 365 Copilot Chat

- **Researcher available in GA** \[Windows, Mac, Web\]

  The researcher agent is pre-installed in Copilot Chat for all worldwide users. Find it in the left navigation pane alongside other agents, giving you quick access to research tools as part of the Copilot Premium license. [Learn more](https://www.microsoft.com/microsoft-365/blog/2025/06/02/researcher-and-analyst-are-now-generally-available-in-microsoft-365-copilot/?msockid=2484525e9a9b66d4330b47329bb667c9).

### PowerPoint

- **Microsoft 365 Copilot generates the new presentation in a new file when starting from an existing presentation** \[Mac, Windows\]

  Now, when creating a presentation using Microsoft 365 Copilot from an existing presentation using, it creates the new presentation in a new file without affecting the original presentation [Learn more](https://support.microsoft.com/office/create-a-new-presentation-with-copilot-in-powerpoint-3222ee03-f5a4-4d27-8642-9c387ab4854d).
- **Reference multiple files in your presentation creation using Microsoft 365 Copilot** \[Windows, Mac, Web\]

  Enhance your PowerPoint presentations by referencing up to five files with Microsoft 365 Copilot, making it easier to incorporate detailed insights and comprehensive data without switching contexts. [Learn more](https://support.microsoft.com/office/create-a-new-presentation-with-copilot-in-powerpoint-3222ee03-f5a4-4d27-8642-9c387ab4854d).

### Word

- **Easily write a prompt or choose quick actions from the Copilot icon in your Word doc** \[Mac, Windows\]

  The Copilot icon in your document margin makes it easy to quickly add a prompt or choose from a range of quick options Copilot can offer. [Learn more](https://www.microsoft.com/microsoft-365-life-hacks/everyday-ai/how-to-use-copilot-in-microsoft-word?msockid=2484525e9a9b66d4330b47329bb667c9).

## July 8, 2025

Updates released between June 24, 2025, and July 8, 2025.

### Excel

- **Copilot in Excel with Python \| Reasoning Model Integration \(Think Deeper\)** \[Mac, Windows, Web\]

  While performing advanced analysis with Copilot in Excel with Python, users can choose the "Think Deeper" mode to get a more elaborate and detailed plan, followed by automatic execution to generate Python code, results, and explanations. This improves performance on complex asks by leveraging the power of the latest AI reasoning models.

### Teams

- **Copilot in Meetings will suggest follow up questions to ask it** \[Windows, Mac\]

  When Copilot in Teams Meetings responds to a prompt, it will also suggest follow-up prompts to ask Copilot that builds on the prior response. These questions will generally be based on the response it gave prior, and could be related to honing in on a particular topic, asking for more details, or even reformatting the content into a table if appropriate. [Learn more](https://support.microsoft.com/office/use-copilot-in-microsoft-teams-meetings-0bf9dd3c-96f7-44e2-8bb8-790bedf066b1).

### Word

- **Automatic summary of documents on file-open in Word** \[Windows, Mac, Web\]

  When users open a document, Copilot generates a summary in the Word window. You can hide the summary or open the Copilot chat pane to ask specific questions about the document. [Learn more](https://support.microsoft.com/office/create-a-summary-of-your-document-with-copilot-in-word-79bb7a0a-3bf7-41fe-8c09-56f855b669bf).
- **Kickstart your document with contextual prompts** \[Mac\]

  Copilot leverages your recent files and meetings to suggest contextual prompts, helping you quickly draft a new document for day-to-day tasks.

## June 24, 2025

Updates released between June 10, 2025, and June 24, 2025.

### Excel

- **Use Copilot with any table in the workbook, referring by natural language** \[iOS, Web, Mac, Windows\]

  Copilot uses the context of your prompt to pick what selection of data to answer about and reason over, including tables in other sheets. [Learn more](https://techcommunity.microsoft.com/blog/excelblog/smarter-context-awareness-for-copilot-in-excel/4424939).

### Microsoft 365 app

- **Use Copilot suggested prompts for recommended entities** \[Windows, Mac, Web\]

  Empower your work with a $30 Copilot license by clicking on curated prompts within recommended entities. Uncover key insights on demand-helping you boost productivity in everyday tasks. [Learn more](https://techcommunity.microsoft.com/blog/microsoft365copilotblog/getting-the-most-from-the-copilot-prompt-gallery/4383106).

### Microsoft 365 Copilot Chat

- **Scheduled prompts** \[Windows, Mac, Web, Teams\]

  Plan ahead by scheduling essential prompts for repeated tasks in Copilot chat. Create a productive routine that helps you stay organized and efficient. [Learn more](https://learn.microsoft.com/en-us/microsoft-365/copilot/scheduled-prompts).

### Outlook

- **Content language is the default summarize language** \[Mac\]

  When summarizing Copilot tries to identify the language of the email and summarize in that language. [Learn more](https://support.microsoft.com/office/frequently-asked-questions-about-copilot-in-outlook-07420c70-099e-4552-8522-7d426712917b?storagetype=live).

### PowerPoint

- **Create a PowerPoint slide from a file or prompt** \[Web, Windows, Mac\]

  Creating impactful slides can be challenging and time-consuming. Copilot helps you quickly turn your ideas and files into a fully designed slide with content ready to edit and refine, making the presentation creation and refinement process more personalized and efficient. [Learn more](https://support.microsoft.com/topic/add-a-slide-from-a-file-with-copilot-in-powerpoint-9034b581-38df-46be-a725-986cbbd4b5d4).
- **Designer is now part of Copilot, enhanced with new template and slide suggestions** \[Mac, Windows, Web\]

  Enjoy familiar Designer slide layouts and presentation template suggestions in a vertical gallery. Copilot now brings you enhanced suggestions to quickly build impactful presentations. [Learn more](https://support.microsoft.com/office/create-professional-slide-layouts-with-designer-53c77d7b-dc40-45c2-b684-81415eac0617).
- **Easily select a template while you create a new PowerPoint presentation with Copilot** \[Mac, Web, Windows\]

  When creating a new presentation with Copilot in PowerPoint, choose a template from your organization's collection for on-brand presentations, or select from Microsoft's handpicked templates, ensuring the new presentation is built as per your chosen template. [Learn more](https://support.microsoft.com/topic/keep-your-presentation-on-brand-with-copilot-046c23d5-012e-49e0-8579-fe49302959fc).
- **Reference a PDF file when creating a presentation with Microsoft 365 Copilot** \[Mac, Windows, Web\]

  You can now reference a PDF file when you create a presentation with Copilot within the PowerPoint application. [Learn more](https://support.microsoft.com/office/create-a-new-presentation-with-copilot-in-powerpoint-3222ee03-f5a4-4d27-8642-9c387ab4854d).

## June 10, 2025

Updates released between May 29, 2025, and June 10, 2025.

### Excel

- **Improvements to Copilot chat experience** \[Windows, Web, Mac\]

  Improvements to the Excel Copilot chat experience to give more consistent responses to all chat questions.

### Outlook

- **Custom Instructions for draft with Copilot** \[Android, Windows, iOS, Mac, Web\]

  Give Copilot some instructions about your emails - like the tone, length, greeting - so your Copilot generated drafts sound more like you want them to. #newoutlookforwindow
- **Schedule a meeting from an email with Copilot** \[Android, Windows, iOS, Mac, Web\]

  Turn any email thread into a meeting in one click. Copilot builds a complete invite for your review -title, agenda, attendee list, and a summary of the email conversation-plus attaches the original email thread so everyone is up to speed. Available in the new Outlook for Windows, web, Mac, and mobile. #newoutlookforwindows [Learn more](https://support.microsoft.com/office/create-a-meeting-and-agenda-with-copilot-in-outlook-31a44dfa-62bb-4751-82c4-14327a26759f).

### PowerPoint

- **Microsoft 365 Copilot Chat: Reference a TXT file when creating a presentation with Copilot** \[Windows, Mac, Web\]

  You can now reference a TXT file when you create a presentation with Copilot within the PowerPoint application. [Learn more](https://support.microsoft.com/office/create-a-new-presentation-with-copilot-in-powerpoint-3222ee03-f5a4-4d27-8642-9c387ab4854d).

### Teams

- **Improvements to the transcription experience in meetings** \[Windows, Mac\]

  These updates enhance the transcription experience in meetings. When transcription, recording, or Copilot is enabled, users are prompted to choose the spoken language for accurate captions. Once transcription is running, only the organizer, co-organizers, and transcript initiator can change that language. A new settings page under Caption settings > Language settings > Meeting spoken language, along with a matching option under Transcript > Language settings, streamlines configuration. If someone speaks a language that doesn't match the selected one, the organizer/co-organizer and initiator receive a mismatch notification so they can adjust quickly. [Learn more](https://support.microsoft.com/office/use-live-captions-in-microsoft-teams-meetings-4be2d304-f675-4b57-8347-cbd000a21260#:%7E:text=The%20meeting%20organizer%2C%20co%2Dorganizer\(s\)%2C%20transcript,Select%20Update%20to%20change.).
- **Microsoft Teams: Intelligent recap support for ad-hoc meetings and calls in GCC High** \[Android, Windows, iOS, Mac, Web\]

  Intelligent meeting recap is now available in GCC High for impromptu calls and meetings, like those started from 'Meet now' and calls started from chat. You can easily browse the recording by speakers and topics, as well as access AI-generated notes, AI-generated tasks, and name mentions after the ad-hoc meeting ends. This capability is available for users with a Teams Premium or M365 Copilot license.

### Word

- **Draft content from up to 10 chosen references** \[Mac, Windows\]

  Type a forward slash \(/\) to pick as many as ten files, meetings, or emails for Copilot to cite while drafting your document. The release started with 10 chosen references but is expanding to support up to 20. [Learn more](https://techcommunity.microsoft.com/blog/microsoft365insiderblog/expanding-reference-capabilities-with-microsoft-365-copilot-in-word/4406054).
- **Write a prompt for selected portions of text in Word** \[Mac\]

  Writing a prompt to draft content based on your selection no longer expands your selection to the entire paragraph, table, or list. You can prompt based on a single sentence or item.

## May 29, 2025

Updates released between May 13, 2025, and May 29, 2025.

### Excel

- **Visual outline confirms Copilot's data range** \[Mac\]

  When you call on Copilot, Excel now draws a clear border around the table or cell range in focus. Instantly see exactly what data will be summarized, cleaned, or chart-ready-so you can adjust the selection before Copilot gets to work.

### PowerPoint

- **Ask Copilot to rewrite text as a list** \[Web, Mac, Windows\]

  Transform paragraphs into clear bullet points or lists with a single command-ideal for quickly organizing content when preparing your presentation. [Learn more](https://support.microsoft.com/topic/elevate-your-presentation-game-with-copilot-s-text-rewrite-feature-in-powerpoint-d70b140b-bb3f-46b7-be64-ceec526a8dcd).

### Word

- **Ask Copilot to analyze document visuals** \[Mac\]

  Add any image, chart, or diagram to your prompt and Copilot instantly extracts text, explains trends, suggests alt text, and surfaces quick insights-making documents more accessible and informative in seconds.

## May 13, 2025

Updates released between April 29, 2025, and May 13, 2025.

### Excel

- **Ask Copilot about any part of your sheet** \[Web, Mac, Windows, iOS\]

  When you ask questions about your worksheet, Copilot can look at the content of your sheet and use it to inform an answer to your question. This includes understanding worksheet data on your selected area, beyond tables and ranges, and provide Copilot answers in chat.

### Microsoft 365 app

- **Copilot in Excel with Python for Mac** \[Mac\]

  Speak plain English and let Copilot write and run Python for forecasting, machine learning, and rich visuals-results land right on the grid in Excel for Mac. [Learn more](https://support.microsoft.com/office/copilot-in-excel-with-python-364e4ae9-9343-4d56-952a-5f62b0f70db6).

### PowerPoint

- **Suggestions for slide templates as you work** \[Mac, Web\]

  On PowerPoint for Mac, Copilot proposes design-ready layouts as soon as you insert a slide or start typing a title, helping you build polished decks faster. [Learn more](https://techcommunity.microsoft.com/blog/microsoft365insiderblog/jumpstart-your-presentations-with-slide-starters/4407669).

### Word

- **Choose the level of detail for summaries when documents are opened** \[Windows, Mac, Web\]

  Tailor each document opening with your preferred summary style-select brief, standard, or detailed insights to match your workflow. [Learn more](https://support.microsoft.com/office/create-a-summary-of-your-document-with-copilot-in-word-79bb7a0a-3bf7-41fe-8c09-56f855b669bf).

## April 29, 2025

Updates released between April 16, 2025, and April 29, 2025.

### Outlook

- **Chat with Copilot in Outlook for Mac** \[Mac\]

  The same Microsoft Copilot experience you can get in the Microsoft Teams app, at copilot.microsoft.com \(work mode\) and in other places is now available from within Microsoft Outlook for Mac. You can find the Copilot app in the left app bar. [Learn more](https://support.microsoft.com/office/frequently-asked-questions-about-copilot-in-outlook-07420c70-099e-4552-8522-7d426712917b).

### Word

- **Replace your selection with generated content** \[Web, Mac, Windows\]

  Selecting the Replace button lets you instantly replace your selected text with content that was generated in Draft with Copilot.

## April 16, 2025

Updates released between April 2, 2025, and April 16, 2025.

### Excel

- **Graph grounded chat** \[Windows, Mac, Web\]

  Ask Copilot in Excel for insights drawn from your chats, documents, meetings, and emails via Microsoft Graph-enhancing your workbook analysis with contextual organizational data. [Learn more](https://support.microsoft.com/topic/use-copilot-to-find-data-from-the-web-or-your-organization-and-add-it-in-excel-7a72fb29-e623-49e2-9f7d-38664b593054).
- **Use Copilot to search for answers from the web** \[Windows, Mac, Web\]

  In Excel, simply ask Copilot to search the web for answers and integrate the insights directly into your workbook, making data analysis even smoother. [Learn more](https://support.microsoft.com/topic/use-copilot-to-find-data-from-the-web-or-your-organization-and-add-it-in-excel-7a72fb29-e623-49e2-9f7d-38664b593054).

## April 2, 2025

Updates released between March 20, 2025, and April 2, 2025.

### PowerPoint

- **Translate your presentation** \[Windows, Web, Mac\]

  Produce a translated copy of your entire presentation in about 40 languages while preserving your slide design and structure, making global collaboration effortless. [Learn more](https://support.microsoft.com/topic/translate-your-presentation-with-copilot-2c622fca-daaf-457c-bc74-f3496cf44a85).

## March 19, 2025

Updates released between March 5, 2025, and March 19, 2025.

### Microsoft 365 Copilot Chat

- **Prompt suggestions in Copilot chat** \[Windows, Web, Mac\]

  Get started in Copilot chat quickly with automatic prompt suggestions that enhance your productivity by providing relevant and context-aware prompts based on your previous interactions.

## March 4, 2025

Updates released between February 20, 2025, and March 4, 2025.

### Microsoft 365 Copilot Chat

- **Search archived mailboxes in Copilot Chat** \[Windows, Web, Android, iOS, Mac\]

  Leverage Copilot to search emails across both primary and archived mailboxes by appending 'from my archives' or 'also look for emails in my archives' in your prompts to quickly locate key messages.

### PowerPoint

- **Narrative builder creates slides with tables** \[Windows, Web, Mac\]

  Convert grounded content from Word documents into dynamic slides with tables. Enhance your presentations with structured, data-driven visuals effortlessly.

## February 19, 2025

Updates released between February 5, 2025, and February 19, 2025.

### Microsoft Teams

- **Intelligent meeting recap for instant meetings \(premium\)** \[Windows, Mac\]

  Effortlessly browse meeting recordings by speaker and topic and access AI-generated notes, tasks, and mentions for instant meetings-empowering premium Copilot users with comprehensive insights. [Learn more](https://support.microsoft.com/office/meeting-recap-in-microsoft-teams-c2e3a0fe-504f-4b2c-bf85-504938f110ef).

### PowerPoint

- **Create a presentation from a file-based prompt** \[Windows, Web, Mac\]

  Pull key facts and data from a selected file to shape your narrative. Simply provide Copilot with a prompt and quickly build your deck with relevant information. [Learn more](https://support.microsoft.com/office/create-a-new-presentation-with-copilot-in-powerpoint-3222ee03-f5a4-4d27-8642-9c387ab4854d).

### Viva Insights

- **Copilot dashboard for usage and retention insights** \[Windows, Web, Android, iOS, Mac\]

  Dive into usage frequency, compare top user groups, and track retention metrics-all in a single, comprehensive dashboard for actionable insights. [Learn more](https://learn.microsoft.com/en-us/viva/insights/org-team-insights/copilot-dashboard#interpreting-the-data).

### Word

- **Chat with Copilot about selected text** \[Windows, Web, Mac\]

  Highlight text, start a chat with Copilot, and receive responses tailored to what you've selected. Get targeted writing assistance and refine your content in real time.

## February 4, 2025

Updates released between January 24, 2025, and February 4, 2025.

### Microsoft 365 Copilot Chat

- **Access support pages in Copilot Chat** \[Windows, Web, Android, iOS, Mac\]

  View organizational support pages directly within Copilot Chat, for quick help and guidance in your workflow.

### Microsoft Teams

- **Speaker recognition and attribution in BYOD rooms with Copilot** \[Windows, Mac\]

  Take advantage of speaker recognition and transcript attribution, unleashing new AI capabilities in any meeting space, whether or not it has a Teams Rooms system deployed. This feature identifies and attributes people in live transcripts, utilizing a unique voice profile for each participant enabling intelligent recaps and unlocking maximum value from Microsoft 365 Copilot in Teams meetings. Users can easily and securely enroll their voices via Teams Settings. This feature requires a Microsoft 365 Copilot or Teams Premium license for the user hosting the meeting for Copilot experiences and intelligent recaps, respectively. [Learn more](https://learn.microsoft.com/en-us/microsoftteams/rooms/voice-recognition).

### PowerPoint

- **Use Copilot to rewrite, trim, or formalize text** \[Web, Mac\]

  Transform your presentation text by letting Copilot fix grammar, shorten lengthy content, or adopt a more professional tone-perfect for crafting clear, polished slides.

### Word

- **Browse cloud files with the file picker** \[Mac\]

  Use a file picker to browse your cloud directory and include relevant files without searching by name, making it easy to add key references to your draft.
- **Reference data from the Microsoft cloud when drafting with Copilot in Word** \[Windows, Web, Mac\]

  Draft with Copilot now supports attaching rich content from the Microsoft cloud-including emails and meetings-resulting in more contextually relevant content. [Learn more](https://techcommunity.microsoft.com/blog/microsoft365copilotblog/what%E2%80%99s-new-in-microsoft-365-copilot-in-word-at-ignite-2024/4303448).
- **Reference plain text files in Copilot** \[Windows, Web, Mac\]

  Add .txt files as sources with Copilot in Word, streamlining your process when working with text-based research or background content.

## January 23, 2025

Updates released between January 8, 2025, and January 23, 2025.

### Microsoft 365 Copilot Chat

- **Use Pages in compliant Copilot web chat** \[Windows, Web\]

  Easily open and reference Pages while collaborating in a compliant web chat environment-keeping conversations and content connected without leaving your chat.

### PowerPoint

- **Generate summaries for longer presentations** \[Windows, Web, Mac\]

  Copilot now supports text summaries up to 40k words \(around 150 slides\), giving you richer information and more polished layouts. [Learn more](https://support.microsoft.com/office/summarize-your-presentation-with-copilot-in-powerpoint-499e604c-4ab9-4f6a-9dbe-691cc87f2f69).
- **Listen to Copilot's responses with Read Aloud** \[Windows, Mac\]

  Hear Copilot's replies in the chat pane, letting you stay hands-free while reviewing your content.

### Viva Insights

- **New Copilot adoption metrics and completing total actions taken** \[Windows, iOS, Mac\]

  This adds seven new Copilot adoption metrics to the Copilot dashboard and Viva Insights Advanced insights. It also updates the "total actions taken" metric in the Copilot dashboard to include these new Copilot adoption metrics. [Learn more](https://techcommunity.microsoft.com/blog/viva_insights_blog/new-microsoft-copilot-analytics-features-now-available-%E2%80%93-novemberdecember-2024/4356206).

### Word

- **Get started on a draft immediately with example prompts** \[Windows, Mac\]

  On blank documents, Copilot in Word offers one-click example prompts to help you get started quickly. [Learn more](https://techcommunity.microsoft.com/blog/microsoft365copilotblog/what%E2%80%99s-new-in-microsoft-365-copilot-in-word-at-ignite-2024/4303448).
- **Listen to Copilot's responses with Read Aloud** \[Windows, Web, Mac\]

  Hear Copilot's replies in the chat pane, letting you stay hands-free while reviewing your content.

## January 7, 2025

Updates released between December 18, 2024, and January 7, 2025.

### Viva Insights

- **Expand your understanding of Copilot adoption with enhanced metrics** \[Windows, iOS, Mac\]

  Access seven new Copilot metrics and see them reflected in "total actions taken," helping you better track how teams use Copilot. [Learn more](https://learn.microsoft.com/en-us/viva/insights/advanced/analyst/templates/microsoft-365-copilot-adoption).
- **New metrics for enterprise data-protected prompts** \[Windows, Web, Android, iOS, Mac\]

  Gain visibility into prompts submitted through Microsoft 365 Copilot Chat \(web\) and enterprise data-protected Copilot scenarios. [Learn more](https://learn.microsoft.com/en-us/viva/insights/advanced/reference/metrics#microsoft-365-copilot-metrics).
