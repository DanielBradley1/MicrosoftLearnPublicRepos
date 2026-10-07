<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/copilot/cowork/cowork-faq -->
<!-- Sitemap-Last-Modified: 2026-09-29 -->

# Copilot Cowork common questions

Find answers to common questions about Microsoft Copilot Cowork.

## What is Cowork?

Cowork is available in Microsoft Copilot. It carries out tasks on your behalf. For example, it can send emails, schedule meetings, create documents, post in Teams, and handle multistep tasks across your Microsoft 365 environment.

## What can Cowork do for me?

Cowork can send emails, schedule meetings, create documents \(Word, Excel, PowerPoint, PDF\), post in Teams, manage your calendar, prepare daily briefings, search across your organization, conduct deep research, and draft stakeholder communications. You can also schedule prompts to run automatically.

Get a full breakdown by category in [What can Cowork do for you?](https://learn.microsoft.com/en-us/microsoft-365/copilot/cowork/#what-can-cowork-do-for-you)

## How is Cowork different from Copilot Chat?

Cowork completes multistep work across Microsoft 365 by taking action on your behalf, while Copilot Chat helps you generate content and insights within a single session.

| Feature | Copilot Chat | Cowork |
| --- | --- | --- |
| What it is | Always-on AI for drafting, summarizing, answering questions | Agentic AI that completes multistep work across Microsoft 365 |
| Best for | Fast, focused, single-task support | End-to-end work across multiple apps |
| Speed | Seconds to minutes | Minutes to hours \(autonomous execution\) |
| Task complexity | Single-step, single-session | Multistep workflows across tasks and sources |
| Use when... | You need a quick draft, answer, or insight | You need Copilot to take action across apps, files, or systems |
| Top scenarios | Quick daily catch-up, project status, Q&A, or drafting content | Inbox and calendar clean-up, project launches, or meeting preparation. |

Copilot Chat helps you think through your work, supports fast, single-step inputs, and generates output for you to act on. Cowork helps you get work done by completing complex, coordinated actions across your apps, files, and data.

## What skills does Cowork have?

Cowork has built-in skills: Word, Excel, PowerPoint, PDF, Email, Scheduling, Calendar Management, Meetings, Daily Briefing, Enterprise Search, Communications, Deep Research, Adaptive Cards, and App \(Frontier\). The App skill lets you build lightweight, interactive apps in Cowork without writing code. You can also create your own custom skills by placing a `SKILL.md` file in a subfolder of your OneDrive `/Documents/Cowork/skills/` folder \(for example, `/Documents/Cowork/skills/weekly-report/SKILL.md`\).

Get a detailed description of each skill in [Cowork skills](https://learn.microsoft.com/en-us/microsoft-365/copilot/cowork/use-cowork#cowork-skills).

## Can I create my own custom skills?

Yes. You can create up to 50 custom skills by placing `SKILL.md` files in your OneDrive `/Documents/Cowork/skills/` folder. Each file contains a YAML frontmatter block with a name and description, followed by the skill instructions. Cowork discovers your custom skills automatically at the start of each session.

Get step-by-step instructions in [Create custom skills](https://learn.microsoft.com/en-us/microsoft-365/copilot/cowork/use-cowork#create-custom-skills).

## Can I give Cowork custom instructions?

Yes. On the **Preferences** tab of the **Customize** page, add custom instructions that describe how you prefer to work, such as your preferred tone, document formatting, or scheduling rules. Cowork applies them to every task. Your instructions are personal to you and can contain up to 20 KB.

Get details in [Custom instructions in Cowork](https://learn.microsoft.com/en-us/microsoft-365/copilot/cowork/cowork-customize#custom-instructions-in-cowork).

## What can Cowork access?

Cowork inherits your permissions, so it can access only the files and emails you can already access. If you don't have access to a file or email, Cowork can't access it either. When a referenced file or email has a sensitivity label, Cowork shows that label and displays the highest sensitivity label for the session.

## Can I add plugins to Cowork?

Yes. Cowork supports plugins from the Microsoft 365 App Store that add new skills and connectors. You can browse and install plugins from the **Browse plugins** menu. Once acquired, a plugin's skills appear alongside the built-in skills, and its connectors become available for your sessions.

Get step-by-step instructions in [Use plugins with Cowork](https://learn.microsoft.com/en-us/microsoft-365/copilot/cowork/cowork-plugins).

## Can my admin control which plugins I can use?

Yes. Your IT admin can deploy plugins to your organization or specific groups by using the same controls in the Microsoft 365 admin center. Admin-deployed plugins are automatically available to you and can't be removed. Your admin can also restrict which plugins are visible in the App Store.

Learn more in [Manage plugins](https://learn.microsoft.com/en-us/microsoft-365/copilot/cowork/cowork-admin-governance#manage-plugins).

## What happens when I remove a plugin?

When you remove a plugin or an admin revokes it, the plugin's skills and connectors are removed from your next session. Any session that's already in progress isn't interrupted, but the plugin's capabilities won't be available in new sessions.

## Can a plugin work with my files?

Yes. Some plugin tools can act on files from your session—for example, to convert a document, analyze an image, or attach a receipt to a record in another system. When a tool needs a file, Cowork sends the file you point to, and the plugin acts on it. Cowork asks for your approval before the tool runs. Learn more about building plugins in [Accept files from the Cowork workspace](https://learn.microsoft.com/en-us/microsoft-365/copilot/cowork/cowork-plugin-development#accept-files-from-the-cowork-workspace).

## How do I start using Cowork?

Getting started takes just a few steps.

1. Open [Microsoft Copilot](https://copilot.cloud.microsoft).
2. Select **Cowork**.
3. Describe the task you want to accomplish. You can type up to 250,000 characters and attach files by dragging them into the chat or using the file picker.
4. Send your message. Cowork begins processing your request.

## Does Cowork work on mobile devices?

Yes. You can access Cowork in the following ways:

- On the Microsoft Copilot mobile app for iOS and Android devices \(for example, iPhone, iPad, and Galaxy\)

  - Learn more about the experience and what's different on mobile in [Use Cowork on mobile](https://learn.microsoft.com/en-us/microsoft-365/copilot/cowork/cowork-mobile).
  - Plugins are discoverable and configurable on the mobile app. To find them, select the attach menu \(**+**\) > **Skills**. Plugins are also accessible in the Cowork mobile app if you set it up on your desktop.

- From your browser at [copilot.cloud.microsoft](https://copilot.cloud.microsoft) \(desktop\)
- On the Microsoft Copilot desktop app for Windows and macOS

## What file types does Cowork support?

You can attach a wide variety of files to your sessions. Cowork supports the following categories:

- **Word**: `.doc`, `.docx`, `.docm`, `.dot`, `.dotx`, `.odt`, `.rtf`
- **Excel**: `.csv`, `.xls`, `.xlsm`, `.xlsx`, `.ods`
- **PowerPoint**: `.odp`, `.ppt`, `.pptm`, `.pptx`
- **PDF**: `.pdf`
- **Markdown**: `.md`, `.markdown`, `.mdx`
- **Image**: `.png`, `.jpg`, `.jpeg`, `.gif`, `.webp`, `.bmp`, `.svg`, `.ico`
- **Text**: `.txt`, `.log`
- **Code**: `.js`, `.ts`, `.py`, `.java`, `.c`, `.cpp`, `.go`, `.rb`, `.rs`, and others
- **Config**: `.json`, `.yaml`, `.yml`, `.toml`, `.ini`, `.xml`, `.env`
- **Notebook**: `.ipynb`
- **Audio**: `.mp3`, `.wav`, `.m4a`, `.ogg`, `.aac`, `.flac`
- **Video**: `.mp4`, `.mov`, `.avi`, `.mkv`, `.webm`, `.wmv`
- **Archive**: `.zip`, `.rar`, `.7z`, `.tar`, `.gz`, `.bz2`

## Can I preview files without downloading them?

Yes. You can preview the following file types directly in the session:

- PDF
- Microsoft 365 documents \(Word, Excel, PowerPoint\)
- CSV
- Markdown
- Code files \(with syntax highlighting\)
- Images
- HTML
- Email

Select a file to open an inline preview. You can also go full-screen or open the file in its native app.

## How does action approval work?

Before Cowork takes a sensitive action like sending an email or posting in Teams, it displays an approval prompt. Approvals for medium and high risk actions include a risk level indicator so you can gauge the impact. Your choices are:

- **Action button**: \(for example, **Send**, **Post**, or **Create**\): Let Cowork proceed with the action this one time.
- **More options**: \(the dropdown next to the action button\): Approve the action and skip the prompt for similar actions for the rest of the current session. For emails and Teams messages, you can choose how broadly to skip future prompts, such as only for a specific recipient, only for a domain, or always for that action.
- **Cancel**: Stop Cowork from taking the action.

You can also select **Show parameters** to display the technical details of the action before deciding.

Note

For some actions, such as sending an email, posting a Teams message, or scheduling a meeting, Cowork shows you a preview of the content so you can review it before approving.

## Can I pause or stop Cowork while it's working?

Yes. You have the following controls:

- **Pause**: Cowork waits for the current step to finish, then pauses. You can also do a hard pause that stops it immediately.
- **Resume**: Continue from where Cowork stopped.
- **Cancel**: End the current task entirely.

## What happens if I lose my connection?

Cowork automatically reconnects and picks up where it left off. Progress made while you were disconnected is preserved, so you don't lose any work.

## Can I use my voice to talk to Cowork?

Yes. Select the microphone button in the chat input to speak your message. Cowork transcribes your words and sends them as text.

Note

Voice input availability depends on your browser. Not all browsers support this feature.

## How do I manage my tasks?

To show all your sessions with Cowork, select **Tasks** from the main navigation. You can switch between two views:

- **Recent**: Shows your tasks in reverse chronological order. You can filter by status \(In progress, Needs input, Done, Failed\).
- **Automations**: Shows your scheduled prompts with options to edit, pause, resume, or delete them. This view only appears when you have at least one scheduled prompt.

Select any task to jump back into its session.

## Can I schedule recurring prompts?

Yes. Describe what you want and when in your message—for example, "Send me a daily briefing every morning at 9 AM." Cowork sets up the schedule based on your request. You can manage your scheduled prompts from the **Automations** tab in the **Tasks** view, or from the **Schedule** section of the side panel. Learn more in [Schedule prompts](https://learn.microsoft.com/en-us/microsoft-365/copilot/cowork/use-cowork#schedule-prompts).

## Can Cowork act automatically when something happens?

Yes. In addition to scheduled prompts, you can set up event-driven tasks that run when a matching email arrives or when a Teams message is posted, including when you're @mentioned. Describe what to watch for in your message, and Cowork proposes the automation for you to review and confirm. By default, event-driven tasks prepare actions for your approval rather than acting on their own, and each task runs with your permissions. Learn more in [Set up event-driven tasks](https://learn.microsoft.com/en-us/microsoft-365/copilot/cowork/use-cowork#set-up-event-driven-tasks).

## Can Cowork use my local browser?

Yes. Cowork can complete web tasks for you in Microsoft Edge on your device, using the sites you're already signed in to. The browser tab runs on your machine, your credentials and cookies stay on your device, and Cowork uses only the access you already have. If Cowork hits a sign-in step it can't complete on its own, it hands the browser back to you to finish. Learn more in [Use the local browser with Cowork](https://learn.microsoft.com/en-us/microsoft-365/copilot/cowork/cowork-local-browser).

## Can I generate images with Cowork?

Yes. Ask Cowork to make an image—for example, "Create a landscape image of a mountain lake at sunset"—and Cowork uses its built-in image-generation skill. Finished images are saved to your session and to your OneDrive output folder. Learn more in [Generate images](https://learn.microsoft.com/en-us/microsoft-365/copilot/cowork/use-cowork#generate-images).

## How do I pick a model?

Most of the time, leave the model picker on **Auto** and Cowork chooses the model that fits your task. To pick a specific model, select **Auto** in the compose box and choose from the list that your organization makes available. The choices include GPT 5.5, GPT 5.6, and GPT 6 variants, Claude Opus, Claude Sonnet, and Claude Fable 5.1 and 5 \(Preview\). Claude Fable 5 \(Preview\) is off by default, so it appears only after an admin turns it on in the **Microsoft 365 admin center** under Copilot settings. Some models, such as Claude Fable 5, require data retention, and Cowork shows a note in the picker and a banner while the model is selected. Learn more in [Choose a model for Cowork](https://learn.microsoft.com/en-us/microsoft-365/copilot/cowork/cowork-models).

You can also set the reasoning effort level that determines how Cowork balances quality, speed, and cost. Since your tasks might require different levels of power, you can choose the level next to the model picker. **Medium** is the default, which gives you a strong balance for everyday work.

## Where are my files saved?

Files that Cowork creates are saved to your **OneDrive and SharePoint** workspace. You can browse them in the side panel during a session or access them directly in OneDrive at any time.

## Can Cowork edit an existing Office file?

Yes. Cowork can edit existing Word, Excel, and PowerPoint files stored in OneDrive or SharePoint. You can approve edit access for the current task or select **Always allow** to let Cowork edit the file without asking again in the current conversation. Cowork updates the shared file in its existing location, and the file's version history remains available if you need an earlier version. For steps, see [Edit an existing Office file](https://learn.microsoft.com/en-us/microsoft-365/copilot/cowork/use-cowork#edit-an-existing-office-file).

## Can I download all output files at once?

Yes. When Cowork produces multiple files, select **Download All** at the top of the output file list to download everything as a single ZIP archive.

## Can an administrator disable Cowork?

Yes. Administrators can manage access to Cowork through the Microsoft 365 admin center:

- **Disable for specific users**: Add users to a security group configured to exclude them from the Copilot experience.
- **Control deployment**: In the Microsoft 365 Apps admin center, administrators can disable automatic installation of the Microsoft Copilot app or manage distribution through Microsoft Intune, Configuration Manager, or Group Policy.
- **Manage availability**: Administrators can manage availability for users in their organization through the Copilot settings in the admin center.
- **Turn off individual models**: Administrators can disable models, including [Anthropic models](https://learn.microsoft.com/en-us/microsoft-365/copilot/connect-to-ai-subprocessor#disable-connection-to-anthropics-models), for their organization in the Microsoft 365 admin center under Copilot settings.

Learn more in [Microsoft Copilot admin settings](https://learn.microsoft.com/en-us/microsoft-365-copilot/copilot-for-microsoft-365-admin).

## Can customers use Cowork in the education industry?

Yes, faculty and staff users in the education industry can access Cowork. Students aren't eligible for access at this time.

## How is Cowork billed?

Cowork uses a usage-based billing model—your organization is charged based on how much your users do with Cowork. Activities such as model responses, tool and skill calls, image generation, and browser tasks count toward consumption. Administrators see consumption in the Microsoft 365 admin center and can set limits per user or group. Learn more in [Usage-based billing](https://learn.microsoft.com/en-us/microsoft-365/copilot/cowork/cowork-admin-governance#usage-based-billing).

## Are there known limitations?

Yes. The following limitations are by design:

- Cowork can't access or edit files stored locally on your device. It works with files in OneDrive and SharePoint.
- Cowork can't delete files or folders in OneDrive or SharePoint.
- Microsoft doesn't validate custom skills created by users. Review custom skill outputs carefully.
- Attached files must be less than 200 MB.
- Cowork can't read encrypted files, even if the user has access.

## Is Cowork secure?

Yes. Every action Cowork takes is authorized through your Microsoft 365 account. Cowork accesses only the services and data you're already permitted to use. Cowork runs in a secure, isolated environment.

## How do I give feedback?

You can share feedback in the following ways:

- **Thumbs up or thumbs down**: Rate any response from Cowork directly in the conversation.
- **Document feedback**: When previewing a file Cowork created, use the feedback controls to rate it.
- **Inline comments**: Leave comments directly on messages in the session to provide targeted feedback on specific parts of a response.
- **General feedback**: To share broader thoughts about your experience, open the menu and select the feedback option.

## Does Cowork ask me questions?

Yes. Sometimes Cowork needs more information to complete your request. When this need arises, it presents a question with a set of choices for you to pick from. You can select an option, type your own answer, or select **Skip** to let Cowork continue without additional input. The task status shows **Needs user input** when Cowork is waiting for your answer.

## Does Cowork connect to external models for processing?

Cowork can use Anthropic Claude models as a subprocessor for most reasoning, drafting, and tool-using work. It also uses ChatGPT Images 2.0 for image generation. Learn more about the Anthropic integration in [Anthropic as a subprocessor for Microsoft Online Services](https://learn.microsoft.com/en-us/microsoft-365/copilot/connect-to-ai-subprocessor).

Microsoft might deploy other AI models for Microsoft Copilot to use that are hosted and operated by Microsoft. These models are governed by the same contractual and data protection commitments already in place, including that no data leaves Microsoft. Learn more in [Understanding AI functionality and models in Microsoft Online Services](https://learn.microsoft.com/en-us/microsoft-365/copilot/ai-models-overview).

## Are there unsupported regions?

Access to use Anthropic models through Microsoft services is limited to the [regions that Anthropic currently supports](https://www.anthropic.com/news/updating-restrictions-of-sales-to-unsupported-regions). There are limited exceptions to these regional restrictions for features in worldwide products and services that constrain access and use of Anthropic models. Cowork isn't an exception, and use and access is currently limited to Anthropic-supported regions.

## Related content

- [Cowork overview](https://learn.microsoft.com/en-us/microsoft-365/copilot/cowork/)
- [Manage Cowork](https://learn.microsoft.com/en-us/microsoft-365/copilot/cowork/cowork-admin-governance)
- [Get started with Cowork](https://learn.microsoft.com/en-us/microsoft-365/copilot/cowork/get-started)
- [Use Cowork](https://learn.microsoft.com/en-us/microsoft-365/copilot/cowork/use-cowork)
- [Use the local browser with Cowork](https://learn.microsoft.com/en-us/microsoft-365/copilot/cowork/cowork-local-browser)
- [Choose a model for Cowork](https://learn.microsoft.com/en-us/microsoft-365/copilot/cowork/cowork-models)
