<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/build-declarative-agents-add-custom-skills -->
<!-- Sitemap-Last-Modified: 2026-11-06 -->

# Add skills to a declarative agent created with Microsoft 365 Agents Toolkit

Important

In tenants that use [Microsoft Purview Information Barriers \(IB\)](https://learn.microsoft.com/en-us/purview/information-barriers), admins can deploy declarative agents with skills, but end users can't add skills to declarative agents they create.

A skill is a modular, reusable component that you add to a declarative agent to package instructions, resources, and scripts for a specific task. This article describes how to add a skill to a declarative agent by using the Microsoft 365 Agents Toolkit \(ATK\) command-line interface \(CLI\) or the Visual Studio Code extension.

To learn what skills are, why to use them, and the full support matrix, supported file types, sandbox behavior, and governance, see [Skills in declarative agents](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/declarative-agent-skills).

This guide adds agent-scoped skills. To distribute a skill for use directly in Copilot Chat through a plugin, see [Build skills for Copilot Chat](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/build-copilot-chat-skills#package-a-skill-in-a-plugin).

Important

This guide assumes you completed the [Create declarative agents by using Microsoft 365 Agents Toolkit and JSON](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/build-declarative-agents) tutorial. Adding a skill requires declarative agent manifest version 1.9. If you're using an agent created with an older version of Agents Toolkit, you might need to update the version of your agent manifest. For more information, see [Declarative agent manifest reference](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/declarative-agent-manifest-1.9).

## Prerequisites

- [Microsoft 365 Agents Toolkit CLI](https://learn.microsoft.com/en-us/microsoftteams/platform/toolkit/microsoft-365-agents-toolkit-cli) or the [Microsoft 365 Agents Toolkit Visual Studio Code extension](https://learn.microsoft.com/en-us/microsoftteams/platform/toolkit/agents-toolkit-fundamentals)

### Enable agent skills

Agent skills support is controlled by the `TEAMSFX_AGENT_SKILLS` environment variable. Set it before you launch the CLI or Visual Studio Code.

- **Windows \(PowerShell\)** - To persist the variable across sessions, add it to your user environment variables:

  ```powershell
  [System.Environment]::SetEnvironmentVariable("TEAMSFX_AGENT_SKILLS", "true", "User")
  ```

- **macOS or Linux** - Set the variable:

  ```bash
  export TEAMSFX_AGENT_SKILLS=true
  ```


  To persist the variable, add the `export` line to your `~/.bashrc`, `~/.zshrc`, or equivalent shell profile.

If you set the variable after you install the Visual Studio Code extension, restart Visual Studio Code completely.

## Add a skill to your agent

- [CLI](#tabpanel_1_cli)
- [Visual Studio Code](#tabpanel_1_vscode)

1. In your existing project, add a skill. To create a new skill, provide a name and description:

   ```powershell
   atk add skill --name skill-name --description description
   ```


   To add an existing skill folder, use the `--from` option:


   ```powershell
   atk add skill --from PATH_TO_SKILL
   ```

2. Provision the declarative agent to make it available in your environment:

   ```powershell
   atk provision --env local
   ```

1. Open your agent project in Visual Studio Code.
2. Select **Microsoft 365 Agents Toolkit**, and then select **Add Skill** in the Agents Toolkit pane on the left.

   ![A screenshot of the Add Skill button in the Microsoft 365 Agents Toolkit pane](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/assets/images/declarative-agents/skills/toolkit-add-skill.png)
3. Select **Create a new skill**.

   ![A screenshot of the Agents Toolkit prompt to create a new skill](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/assets/images/declarative-agents/skills/toolkit-create-a-new-skill.png)
4. Enter a name for the skill, and then enter a description.
5. Choose whether you want to keep the skill scoped to this agent only or expose it to all Copilot surfaces.
6. Select **manifest.json** when prompted for the manifest, and then select **Add**.
7. Open **manifest.json** and ensure that the declarative agent manifest version is set to **1.9**.
8. Open the **./appPackage/skills/your-skill-name/SKILL.md** \(replace **your-skill-name** with the name of your skill\).
9. Add your instructions to **SKILL.md** and save the file.
10. Select **Provision** in the left pane to make the declarative agent available in your environment.

## Limits

In the Agents Toolkit, you add a skill as a directory \(you can't use `.zip`\), and the complete app package is limited to 10 MB. You can add up to eight skills per agent, with a maximum directory depth of three and up to 350 files across all skills. For the full support matrix, see [Skills in declarative agents](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/declarative-agent-skills#support-matrix).

## Publish your agent

Independent software vendors \(ISVs\) can submit declarative agents that include skills to Microsoft Marketplace. Use Work IQ Dev Tools to validate and build the submittable package from an existing declarative agent project. For the public third-party path, Work IQ Dev Tools doesn't submit the offer on your behalf. Use Partner Center to upload the package, complete the store listing, and submit the offer for certification.

For the end-to-end workflow, see [Partner Center Publishing \(3P\)](https://github.com/microsoft/wiqd/blob/main/plugins/wiqd/skills/wiqd/workflows/partner-center.md) and the [Microsoft Marketplace step-by-step submission guide](https://learn.microsoft.com/en-us/partner-center/marketplace-offers/add-in-submission-guide).

## Related content

- [Skills in declarative agents](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/declarative-agent-skills)
- [Add skills to your declarative agent in Agent Builder](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/agent-builder-add-skills)
- [Declarative agent manifest reference](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/declarative-agent-manifest-1.9)
