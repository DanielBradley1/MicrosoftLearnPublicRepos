<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/copilot/cowork/cowork-local-browser -->
<!-- Sitemap-Last-Modified: 2026-09-23 -->

# Use the local browser with Copilot Cowork

Microsoft Copilot Cowork can complete browser automation for you in Microsoft Edge on your device, using the sites you're already signed in to. Cowork shows its work in a hidden Edge tab so you can stay in the conversation while it acts on your behalf. This article explains how browser use works, what you need to set up, and what to expect when Cowork hands the browser back to you.

## How browser use works

When Cowork needs to use a website to complete a task, it opens a hidden tab in Microsoft Edge and works there. You stay in the Cowork conversation and watch progress through chat updates and the side panel.

Because the tab runs in your own copy of Edge, it uses your existing single sign-on, cookies, and sessions. The agent has exactly the same access to sites that you have when you browse by hand—no more and no less. Credentials, cookies, and session tokens stay on your device.

If Cowork needs information from you to keep going—for example, an address or a confirmation code—it asks you in the chat instead of switching you over to the browser. For sensitive requests, such as signing in, Cowork switches to the browser so you can enter the required information.

## Where browser use is available

Browser use is available in Cowork on the web at [copilot.cloud.microsoft.com](https://copilot.cloud.microsoft.com).

| Surface | Browser use supported? |
| --- | --- |
| Cowork on the web \(Microsoft Edge\) | Yes |
| Cowork on the web \(other browsers\) | Not yet. More information: [If you're not using Microsoft Edge](#if-youre-not-using-microsoft-edge) |
| Microsoft Copilot desktop app | No. If you ask the desktop app to run a browser task, Cowork tells you that browser tasks run in Cowork on the web. |

## Requirements

Before Cowork can use the browser on your behalf, ensure the following requirements are met:

- Your tenant admin enabled **Cowork Browsing** for your organization.
- You're using Cowork in a browser. This feature isn't currently supported in the desktop app or [on mobile](https://learn.microsoft.com/en-us/microsoft-365/copilot/cowork/cowork-mobile).
- Edge is installed on your device. Edge doesn't need to be your default browser.
- You're using the recommended minimum Edge version 152.0.4191.53 or higher.
- You're signed in to Edge with the same work or school account you use for Cowork. InPrivate windows and guest profiles don't have your sign-in sessions, so browser tasks can't run there.

### If you're not using Microsoft Edge

Browser tasks currently work only in Microsoft Edge. If you start Cowork from a different browser or if Edge isn't installed:

- Cowork tells you in the conversation that browser tasks run in Microsoft Edge and offers a link to **Get Microsoft Edge**.
- Cowork still completes every step of your request that doesn’t need the browser. For example, if you ask it to file an expense report, it can still pull receipts from Outlook and draft the line items, then tell you which step needs Edge.

## First-run consent

The first time Cowork needs to use the browser for one of your tasks, a consent notice appears in the conversation.

- Select **I understand** to let Cowork use the browser. After that, Cowork uses normal per-site and per-action permissions and doesn't show the first-run notice again.
- If you don't select **I understand**, browser use stays off. Cowork keeps working on any parts of your request that don't need the browser, and tells you which steps it skipped. The notice appears again the next time you ask for a browser task.

Your acknowledgment is stored in Microsoft Edge on your device, not in Cowork.

Note

You can assign policies to user groups to enable browser automation through Edge with Edge 152, released the week of August 24, 2026. Tenant admins can use the Edge policy documented in [Microsoft Edge Browser policy documentation](https://learn.microsoft.com/en-us/deployedge/microsoft-edge-policies/copilotcoworktoolactionsenabled) to control the Edge instances in which Cowork is allowed to use the browser.

## Run a browser task

You don't need a special command to start a browser task. Ask Cowork to do something that requires the web, and it decides when to open the browser.

1. In the Cowork conversation, describe the task—for example, *"File my expense report in Concur for last week's trip to Seattle"* or *"Find the cheapest nonstop flight from SEA to JFK on Friday and put a hold on it."*
2. Watch the conversation. Cowork shows progress chips as it works, such as *Opening Concur*, *Filling expense details*, or *Submitting form*.
3. Answer any questions Cowork asks. When the agent needs information it can't get from the page, it asks you in the chat—for example, *"Which corporate card did you use?"*—and waits for your reply before continuing.
4. Approve sensitive actions when prompted. For actions that submit personal data or are otherwise sensitive or consequential, Cowork shows an approval card in the conversation. Review it and select **Approve** to approve the action once, or select **Reject**.

The hidden tab stays out of your way during the task. Cowork shows it only when it needs to hand the browser back to you or when you select **Switch to tab**.

## When Cowork hands the browser back to you

For most tasks, you never see the Edge tab. In a few cases, Cowork asks you to take over and shows the tab, including:

- When a **CAPTCHA** or human-verification prompt appears and must be resolved.
- When **credentials**, such as a **password**, or a **multifactor authentication** code are needed.
- When account settings must be changed, or when the account is **locked** or requires a **password reset**.

In each case, Cowork pauses the task and asks you to take over. When you're done, Cowork picks the task back up. If you can't complete the step, Cowork stops the task and reports what was left unfinished.

## Sites your organization blocks

Because Cowork drives your local Edge, it inherits every site restriction your admin already enforces—web filtering, Conditional Access, browser-management policy, and Microsoft Purview data loss prevention \(DLP\). The agent has the same reach you do, never more.

If a task can't continue because of a DLP restriction, Cowork tells you which step is blocked, explains that your organization's policy doesn't allow that browser action on that site, and suggests manual steps you can take.

## Resume an interrupted browser task

If a browser task is interrupted—for example, you close the tab, put your device to sleep, or lose your network connection—Cowork pauses the task instead of failing it.

To pick the task back up:

1. Open the same Cowork conversation when you're ready.
2. Send a message such as *"continue"*, *"resume"*, or any follow-up that relates to the task.
3. Cowork detects the interrupted browser task, checks that Edge is available again, and either keeps going or asks you to confirm before it resumes.

## Privacy and auditing

When Cowork uses the browser on your behalf:

- The session, cookies, and credentials stay in your local copy of Edge. They aren't sent to Cowork's servers.
- The sites Cowork visits and the actions it takes are scoped to your identity and your device. Existing Microsoft Entra sign-in, Conditional Access, and Microsoft Purview policies apply unchanged.

Learn more about tenant-level controls and audit logs in [Manage Cowork](https://learn.microsoft.com/en-us/microsoft-365/copilot/cowork/cowork-admin-governance).

## Admin control

The following browser use is supported for admins:

- Opt the tenant in to browser use in the Microsoft 365 admin center.
- Limit the browser use feature to specific security groups or individuals.

Tenant admins must enable Cowork browsing by performing the following steps. This feature is disabled by default.

1. From the menu, select **Copilot** > **Settings** > **View All** > **Cowork settings**.
2. Under **Allow browser access**, select **Allow Cowork to use the Microsoft Edge browser to perform tasks on behalf of users**.

## Related content

- [Use Cowork](https://learn.microsoft.com/en-us/microsoft-365/copilot/cowork/use-cowork)
- [Get started with Cowork](https://learn.microsoft.com/en-us/microsoft-365/copilot/cowork/get-started)
- [Best practices for Cowork](https://learn.microsoft.com/en-us/microsoft-365/copilot/cowork/best-practices)
- [Cowork common questions](https://learn.microsoft.com/en-us/microsoft-365/copilot/cowork/cowork-faq)
- [Manage Cowork](https://learn.microsoft.com/en-us/microsoft-365/copilot/cowork/cowork-admin-governance)
