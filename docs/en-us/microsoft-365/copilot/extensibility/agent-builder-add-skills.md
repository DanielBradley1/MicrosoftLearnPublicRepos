<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/agent-builder-add-skills -->
<!-- Sitemap-Last-Modified: 2026-09-04 -->

# Add custom skills to your declarative agent in Agent Builder \(preview\)

A custom skill is a modular, reusable component that you add to a declarative agent to help it perform a specific packaged task. A skill is a directory that contains a required `SKILL.md` file with instructions, plus optional resource files and scripts. This article describes how to add a custom skill to your declarative agent by uploading a skill package in Agent Builder.

To learn what custom skills are, why to use them, and the full support matrix, supported file types, sandbox behavior, and governance, see [Custom skills in declarative agents](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/declarative-agent-skills).

Important

Custom skills in declarative agents are in preview for organizations that are part of the Microsoft Frontier Preview. For more information, see [Explore AI Early Access in Microsoft 365](https://www.microsoft.com/en-us/microsoft-365-copilot/frontier-program).

Custom skills aren't available in tenants that use [Microsoft Purview Information Barriers \(IB\)](https://learn.microsoft.com/en-us/purview/information-barriers). This restriction applies to both admin-deployed and user-created declarative agents.

Support for independent software vendors \(ISVs\) to publish declarative agents with custom skills through Partner Center isn't available yet and is coming soon. ISVs shouldn't submit declarative agent packages that include custom skills to Partner Center.

## Prerequisites

- A qualifying Microsoft 365 Copilot license, or access through pay-as-you-go.
- Your organization must be enrolled in the Microsoft Frontier Program.

Note

In Agent Builder, you can add up to eight skills per agent, and each skill package is a compressed `.zip` file of up to 50 MB. For the full support matrix and limits, see [Custom skills in declarative agents](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/declarative-agent-skills#support-matrix).

## Create a skill from a description

You can ask Agent Builder to create a reusable skill from a natural-language description.

1. In [Copilot chat](https://m365.cloud.microsoft), select **Agents & Skills**, and then select **New agent**.
2. Select the **Message Agent Builder** text box and ask Agent Builder to create a reusable workflow.

   ```text
   Create an agent that helps my team write release notes. Add a reusable skill that always follows the same steps:

   1. Takes a list of merged changes (a pasted list or an uploaded  .csv  of PR titles).
   2. Groups them into Features, Fixes, and Other.
   3. Runs a script to format them into a clean Markdown changelog with a version heading and today's date.

   Package this as a skill with clear instructions and the formatting script so the output looks the same every time.
   ```


   ![A screenshot of Agent Builder prompt to create an agent](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/assets/images/agent-builder-screenshots/skills/create-agent-prompt.png)

3. Review the agent in **Configure** to confirm a skill was created.

   ![A screenshot of the Configure tab in Agent Builder showing a skill attached](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/assets/images/agent-builder-screenshots/skills/skill-attached.png)
4. Select the skill to review its details.

   ![A screenshot of the details of the newly added skill](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/assets/images/agent-builder-screenshots/skills/skill-detail.png)

If the skill isn't added, you can explicitly add skills by [uploading a skill package](#upload-a-skill-package).

## Upload a skill package

To add a skill package, first create the package, and then upload it in Agent Builder.

### Create your skill package

Before you add a skill in Agent Builder, package the skill as a `.zip` file that contains:

- A required `SKILL.md` file.
- A skill name and description in the `SKILL.md` YAML front matter.
- Optional supported resource files.
- Optional supported scripts and supporting folders.
- Skill instructions under 20,000 characters.

Your package resembles the following directory structure:

```text
my-skill.zip
|-- SKILL.md              # required
|-- <resource files>      # optional
`-- <scripts or folders>  # optional
```

For the supported file and script types, see [Supported file and script types](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/declarative-agent-skills#supported-file-and-script-types).

Important

Upload the complete `.zip` package. Don't upload `SKILL.md` by itself.

### Upload your skill package

1. Open or create a declarative agent in Agent Builder.
2. Open **Configure**, expand **Skills**, and then select **Add**.

   ![A screenshot of the Add button in the Skills section of the Agent Builder Configure pane](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/assets/images/agent-builder-screenshots/skills/add-skill.png)
3. Upload the complete `.zip` skill package.
4. Review the skill name, description, instructions, and included files.
5. Open **Preview** and try a prompt that should use the skill.

## Related content

- [Custom skills in declarative agents](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/declarative-agent-skills)
