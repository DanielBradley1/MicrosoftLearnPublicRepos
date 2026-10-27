<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/copilot/use-remote-browser-microsoft-copilot -->
<!-- Sitemap-Last-Modified: 2026-10-22 -->

# Use a remote browser with Microsoft Copilot

Microsoft Copilot can use a secure remote Microsoft Edge browser to complete tasks without taking over your device. This feature is available only for enterprise work accounts managed by an organization. This article explains how remote browser use works, how to get started, and what to expect while Copilot works.

## How Remote Browser Use Works

When your request requires a website, Copilot can start a remote Microsoft Edge session hosted in the cloud through a virtual machine, navigate the site, and interact with pages as part of the task. Copilot reports progress in the conversation and can show screenshots from the session. If information, authentication, or approval is required, Copilot pauses and asks you in chat.

Because the Microsoft Edge session runs remotely, Copilot can continue working even if you step away from your computer. You can return later to review progress, respond to questions, approve an action, or take control when needed.

## How Remote Browser Use Differs from Local Browser Use

Both options let Copilot navigate websites and complete tasks, but they run in different browser environments. Remote browser use is designed for delegated work that can continue independently, while local browser use is best when the task depends on the browser session already open on your device.

| **Remote browser use** | **Local browser use** |
| --- | --- |
| Runs in a secure Microsoft Edge session hosted in the cloud. | Runs in Microsoft Edge on your device. |
| Does not automatically use your open tabs, cookies, saved passwords, or signed-in local browser session. | Can use existing tabs, cookies, sign-ins, and browser context that are available in your local session. |
| Can continue while you step away or your local browser is not active. | Depends on your device and local browser remaining available during the task. |

## Where Remote Browser Use Is Available

| **Surface** | **Remote browser use supported?** |
| --- | --- |
| Copilot on the web \(Microsoft Edge\) | Yes |
| Copilot on the web \(other browsers\) | Yes |
| Microsoft Copilot desktop app | Yes |
| Mobile | Not Yet |

## Requirements

- Enterprise account: You are signed in with a work account managed by an organization, and your tenant admin has enabled Copilot Browsing.
- You are using Copilot on the web or in the Microsoft Copilot desktop app. Remote browser use is not currently supported on mobile.

## First-run consent

The first time Copilot needs remote-browser access, a consent notice appears in the conversation. This notice applies only to remote-browser use. Local browser use in Cowork has a separate consent notice.

- Select I understand to allow Copilot to use remote browser-use. Copilot then applies any site-specific permissions and asks for approval before sensitive or consequential actions.
- If you select Cancel, remote browser-use stays off. Copilot keeps working on any parts of your request that don't need the browser and tells you which steps it skipped. The notice appears again the next time you ask for a browser task.

If you decide to not use the browser, you can tell Copilot "Do not use the browser" in your query.

## Run a browser task

You don't need a special command to start a browser task. Ask Copilot to do something that requires the web, and it decides when to open the browser.

1. In the Copilot conversation, describe the outcome you want and include important details such as the site, item, date, or constraints. For example: *“Go to Contoso Travel, find a flight to Seattle next Tuesday, and stop before booking.”*
2. Follow progress in the conversation. Copilot shows updates such as opening the remote browser, navigating to a site, completing a step, or waiting for your input. Review screenshots and progress updates to confirm the task is proceeding as expected.
3. Answer any questions Copilot asks. When Copilot needs information it can't get from the page, it asks you in the chat—for example, *"Please upload your payment details"*—and waits for your reply before continuing.
4. Approve sensitive actions when prompted. For actions that submit personal data, make payments or purchases, send communications such as emails, or are otherwise sensitive or consequential, Copilot shows an approval card in the conversation. Review it and select **Approve** to approve the action once, or select **Reject**.

The remote browser runs separately from your local device. You can continue working while Copilot completes the task, monitor its progress in the conversation, or take control when needed.

## Take control of the remote browser

- **When Copilot asks you to take control:** Complete steps that require your direct interaction, such as entering credentials, completing multi-factor authentication, solving a verification challenge, or providing information that should not be shared in chat.
- **When you choose to take control:** Open the remote session when you want to inspect the page, correct a selection, or complete a step yourself.
- **When you finish:** Select the option to return control to Copilot. Copilot resumes from the current page and continues the task.

While you have control, Copilot pauses and does not interact with the page. If you cannot complete the required step, return to the conversation and stop the task; Copilot reports what was completed and what remains unfinished.

## Sites Your Organization Allows or Blocks

For enterprise accounts, your organization controls which sites the remote Microsoft Edge browser can access. If a site is not permitted by the organization’s remote-browser website policy, Copilot does not open or interact with it.

If a task cannot continue because of an enterprise data loss prevention or other organizational restriction, Copilot identifies the blocked step, explains that your organization’s policy does not allow the browser action, and suggests manual steps you can take.

## Privacy and auditing

Remote browser tasks run in an isolated virtual machine that is separate from your local Microsoft Edge browser. The remote session does not automatically use your local browser profile, saved passwords, payment methods, cookies, or open tabs.

Copilot accesses only the sites needed to complete your request and allowed by your organization’s remote-browser policy.

Copilot does not use credentials saved in your local browser. If you need to sign in, Copilot asks you to take control and enter your credentials directly.

Screenshots shown in Copilot remain available as part of your Copilot conversation history.

You can review progress and screenshots, take control when needed, and review approval prompts before Copilot completes sensitive actions.

For enterprise accounts, browser activity remains subject to your organization’s applicable Microsoft 365 security, compliance, data loss prevention, and auditing policies.

## Admin control

The controls in this section apply only to enterprise work or school accounts. Admins can control whether remote browser use is available, who can use it, and which websites it can access. Remote sessions run in a managed virtual machine, so admins configure access and website policy specifically for remote browser use.

- To turn on: In the Microsoft 365 admin center, under the **Copilot Settings > View All** tab > select **Allow Copilot to use a remote Microsoft Edge browser to perform tasks on behalf of users**
- Choose whether access applies to all users or only selected security groups.
- Configure website access using both an allow list and a block list:

  - **Allow list:** Specify the approved URLs or domains that Copilot can access.
  - **Block list:** Specify URLs or domains that Copilot must not access.
  - Microsoft’s implicit safety block list takes precedence if a domain is also included in the tenant allow list.
