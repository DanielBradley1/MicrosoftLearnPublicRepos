<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/build-declarative-agents-add-custom-skills -->
<!-- Sitemap-Last-Modified: 2026-11-11 -->

# Add skills to a declarative agent created with Microsoft 365 Agents Toolkit

Tip

**Recommended:** Start with [Work IQ Dev Tools](https://aka.ms/wiqd/docs) for supported pro-code declarative-agent and plugin scenarios. See the [WIQD quickstart](https://microsoft.github.io/wiqd/getting-started/quickstart/). Toolkit-based instructions remain available for existing projects and workflows that require them. Check [capability and target-experience support](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/choose-plugin-development-tools) before choosing a tool: WIQD doesn't target custom engine agents.

Important

In tenants that use [Microsoft Purview Information Barriers \(IB\)](https://learn.microsoft.com/en-us/purview/information-barriers), admins can deploy declarative agents with skills, but end users can't add skills to declarative agents they create.

A skill is a modular component that you add to a declarative agent to package instructions, resources, and scripts for a specific task. During **Build or reuse**, use this article when your chosen project already uses Microsoft 365 Agents Toolkit \(ATK\). You finish with a skill registered in the agent, saved task instructions, and a provisioned test version.

For a new professional-developer plugin project, start with [Work IQ Dev Tools](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/quickstart-plugin) and a [documented environment](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/choose-plugin-development-tools#choose-your-environment). Keep this Toolkit procedure when its project controls fit your selected agent route; it isn't a requirement for every plugin.

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

**Verify:** The restarted tool process sees `TEAMSFX_AGENT_SKILLS` set to `true`. A user-level Windows setting doesn't change a process that was already running.

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


   **Verify:** The project contains the skill directory and `SKILL.md`, and the declarative-agent manifest references that skill. Follow the [support matrix](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/declarative-agent-skills#support-matrix); this import option doesn't establish reuse across agents.

2. Edit the skill's `SKILL.md` with the task instructions, resources, and supported scripts.

   **Verify:** The saved file retains its required metadata and describes the task, expected output, and boundaries.
3. Provision the declarative agent to make it available in your environment:

   ```powershell
   atk provision --env local
   ```


   **Verify:** Provisioning succeeds for the intended tenant and environment. Test the skill's task in the intended agent; provisioning success doesn't establish runtime behavior.

1. Open your agent project in Visual Studio Code.

   **Verify:** The workspace is the intended existing Toolkit agent project.
2. Select **Microsoft 365 Agents Toolkit**, and then select **Add Skill** in the Agents Toolkit pane on the left.

   ![A screenshot of the Add Skill button in the Microsoft 365 Agents Toolkit pane](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/assets/images/declarative-agents/skills/toolkit-add-skill.png)

   **Verify:** The skill authoring prompt opens for this project.
3. Select **Create a new skill**.

   ![A screenshot of the Agents Toolkit prompt to create a new skill](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/assets/images/declarative-agents/skills/toolkit-create-a-new-skill.png)

   **Verify:** The tool requests details for a new skill.
4. Enter a name for the skill, and then enter a description.

   **Verify:** The name and description identify the intended task and when to use it.
5. Review the scope offered by the tool and choose the option appropriate to the target agent and supported distribution route.

   **Verify:** The selection matches your plan. A scope option doesn't establish compatibility with every Copilot surface or support for cross-agent reuse.
6. Select **manifest.json** when prompted for the manifest, and then select **Add**.

   **Verify:** The selected app manifest belongs to this project and the tool adds the skill files and reference.
7. Open the declarative-agent manifest referenced by **manifest.json** and ensure that its version is set to `v1.9`.

   **Verify:** The declarative-agent manifest, rather than the app manifest's separate schema version, meets the required version.
8. Open the **./appPackage/skills/your-skill-name/SKILL.md** \(replace **your-skill-name** with the name of your skill\).

   **Verify:** The agent's new skill registration references this file.
9. Add your instructions to **SKILL.md** and save the file.

   **Verify:** The saved instructions define the task, expected output, and boundaries, and retain required skill metadata.
10. Select **Provision** in the left pane to make the declarative agent available in your environment.

    **Verify:** Provisioning succeeds for the intended tenant and environment. Test the task in the target agent before treating the skill as ready.

## Limits

In the Agents Toolkit, you add a skill as a directory \(you can't use `.zip`\), and the complete app package is limited to 10 MB. You can add up to eight skills per agent, with a maximum directory depth of three and up to 350 files across all skills. For the full support matrix, see [Skills in declarative agents](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/declarative-agent-skills#support-matrix).

## Publish your agent

Independent software vendors \(ISVs\) can submit declarative agents that include skills to Microsoft Marketplace. Use Work IQ Dev Tools to validate and build the submittable package from an existing declarative agent project. For plugin packages, `wiqd publish pc` can create the Partner Center offer, populate the draft listing, upload the package and images, submit for certification with separate authorization, and track status. Partner Center account enrollment and verification remain portal steps, and Microsoft controls certification and publication.

Follow [Publish to Partner Center with WIQD](https://microsoft.github.io/wiqd/getting-started/publish-to-partner-center/) for prerequisites, package validation, listing setup, submission, and status tracking. Portal submission remains an alternative; see the [Microsoft Marketplace submission guide](https://learn.microsoft.com/en-us/partner-center/marketplace-offers/add-in-submission-guide). Follow the confirmed agent submission route, not an Office Add-in example or an assumed offer type for composed plugins.

## Next step

Enter **Package & test** with [Integrate and test your components](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/integrate-test-plugin-components). When the agent is ready for public distribution, continue to [Publish through Microsoft Marketplace](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/publish-plugin-publicly).

## Related content

- [Skills in declarative agents](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/declarative-agent-skills)
- [Add skills to your declarative agent in Agent Builder](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/agent-builder-add-skills)
- [Declarative agent manifest reference](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/declarative-agent-manifest-1.9)
