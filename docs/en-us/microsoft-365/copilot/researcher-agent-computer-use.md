<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/copilot/researcher-agent-computer-use -->
<!-- Sitemap-Last-Modified: 2025-11-04 -->

# Researcher with Computer Use admin configuration

## Overview

For onboarding instructions, check out this short video:

<iframe src="https://www.youtube-nocookie.com/embed/N3vLF9mnd8w" allowfullscreen="true" data-linktype="external" frameborder="0"></iframe>

Researcher with Computer Use is a powerful extension that builds on the capabilities of the Researcher agent. With Computer Use, Researcher agent can securely interact with public, gated, and interactive web content through virtual computer-enabling users to uncover deeper insights, take action, and generate richer reports grounded in both their work data and the web. For more details, see [Use Researcher with Computer use in Microsoft Copilot](https://support.microsoft.com/topic/1f274537-6648-46e8-8264-052a49b92af4).

[![Screenshot showing the computer use option active in Researcher agent.](https://learn.microsoft.com/en-us/microsoft-365/copilot/media/computer-use-active-option.png)](https://learn.microsoft.com/en-us/microsoft-365/copilot/media/computer-use-active-option.png#lightbox)

## Configure admin settings for Researcher agent with Computer Use

Follow these instructions to configure admin settings for Researcher agent with **Computer Use** by following the setup instructions.

1. Navigate to [Microsoft Admin Controls \(MAC\) Agents](https://admin.cloud.microsoft/?#/copilot/agents) page.

   [![Screenshot showing the Microsoft Admin Controls Agents page.](https://learn.microsoft.com/en-us/microsoft-365/copilot/media/microsoft-admin-control-agents-page.png)](https://learn.microsoft.com/en-us/microsoft-365/copilot/media/microsoft-admin-control-agents-page.png#lightbox)
2. In the left navigation pane, select **Researcher** under **Agents**, and check if there's another tab for **Computer use**.

   [![Screenshot showing the option to allow Researcher to access work data.](https://learn.microsoft.com/en-us/microsoft-365/copilot/media/computer-use-researcher-agent.png)](https://learn.microsoft.com/en-us/microsoft-365/copilot/media/computer-use-researcher-agent.png#lightbox)
3. Customize users that have access to Researcher with Computer Use.

   a. There are three options for configuring who has access to the experience-

   - Allow all users in your organization
   - Allow specific users or groups only
   - No users in your organization


   b. For users that have it disabled, the **Computer Use** option will appear grayed out.


   [![Screenshot showing the Computer Use option enabled in Researcher Agent.](https://learn.microsoft.com/en-us/microsoft-365/copilot/media/computer-use-enabled.png)](https://learn.microsoft.com/en-us/microsoft-365/copilot/media/computer-use-enabled.png#lightbox)


   [![Screenshot showing the Computer Use option disabled in Researcher Agent.](https://learn.microsoft.com/en-us/microsoft-365/copilot/media/computer-use-disabled.png)](https://learn.microsoft.com/en-us/microsoft-365/copilot/media/computer-use-disabled.png#lightbox)

4. Configure **Work access** for Researcher with Computer Use

   a. The work option allows users to toggle on **Work** in the Sources menu, allowing Researcher agent to leverage a user's work content, for example, emails, chats, files, with Computer Use.

   b. When enabled by admins, users must still manually toggle on Work access.

   c. When disabled, the **Work** source will appear grayed out and not selectable.

   [![Screenshot showing the Work option enabled in Researcher agent.](https://learn.microsoft.com/en-us/microsoft-365/copilot/media/work-toggle-enabled.png)](https://learn.microsoft.com/en-us/microsoft-365/copilot/media/work-toggle-enabled.png#lightbox)

   [![Screenshot showing the Work option disabled in Researcher agent.](https://learn.microsoft.com/en-us/microsoft-365/copilot/media/work-toggle-disabled.png)](https://learn.microsoft.com/en-us/microsoft-365/copilot/media/work-toggle-disabled.png#lightbox)
5. Select which websites are allowed for Computer Use.

   a. There are three options for configuring websites the virtual device can access:  


   - All websites  

   - Allow specific URLs or domains only  

   - Exclude specific URLs or domains


   b. You can allow "All websites", block some with the "Exclude specified" option, or only allow certain sites with the "Allow specified" option.

### Learn more about Researcher with Computer Use

- [Introducing Researcher with Computer Use in Microsoft Copilot](https://techcommunity.microsoft.com/blog/microsoft365copilotblog/introducing-researcher-with-computer-use-in-microsoft-365-copilot/4464766)
- [Get started using Researcher with Computer Use](https://support.microsoft.com/topic/1f274537-6648-46e8-8264-052a49b92af4)
- [Frequently asked questions for Researcher with Computer Use](https://learn.microsoft.com/en-us/microsoft-365/copilot/researcher-agent-computer-use-faq)
