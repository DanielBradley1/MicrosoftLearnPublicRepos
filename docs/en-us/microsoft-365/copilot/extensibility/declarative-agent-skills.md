<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/declarative-agent-skills -->
<!-- Sitemap-Last-Modified: 2026-11-11 -->

# Skills in declarative agents

This article covers skills attached to a declarative agent. To author a skill for use directly in Microsoft 365 Copilot Chat without creating an agent, see [Build skills for Copilot Chat](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/build-copilot-chat-skills). The support matrix in this article applies to agent-scoped skills, not to all skills or plugin packages.

Important

In tenants that use [Microsoft Purview Information Barriers \(IB\)](https://learn.microsoft.com/en-us/purview/information-barriers), admins can deploy declarative agents with skills, but end users can't add skills to declarative agents they create.

A *skill* is a modular capability that you add to a declarative agent to help it accomplish a specific task more reliably and repeatably. A skill is a file directory that contains a required `SKILL.md` file, plus optional resource files and scripts. The `SKILL.md` file holds the instructions that direct the model to complete the task.

Skills are a distinct component of a declarative agent. In earlier guidance, the word *skills* referred to task descriptions that you wrote inline within an agent's instructions. Skills replace that approach: instead of writing task detail directly in the instructions, you package it as a separate component that the agent references. For guidance on how instructions should reference skills, see [Write effective instructions for declarative agents](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/declarative-agent-instructions).

You can add skills to a declarative agent by using [Agent Builder](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/agent-builder). For supported pro-code scenarios, [Work IQ Dev Tools](https://aka.ms/wiqd/docs) is recommended. Its `wiqd agent add skill` route requires the `agent-skills` feature flag, which is off by default; see [Choose the skill implementation path](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/build-reuse-skills#work-iq-dev-tools). The [Toolkit-based walkthrough](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/build-declarative-agents-add-custom-skills) remains available for existing Toolkit projects.

## What is a skill

A skill is a directory with the following contents:

- A required `SKILL.md` file that contains:

  - A skill name and description in the YAML front matter.
  - Skill instructions, which must be under 20,000 characters.

- Optional resource files, such as templates, reference data, or definitions.
- Optional scripts and supporting folders.

For example, a finance team might build a quarterly business review skill that bundles the instructions for producing the review, scripts that transform data and generate charts, and assets such as financial models, KPI definitions, and branded slide templates. The agent uses the skill when a user asks for that task.

## Why use skills in declarative agents

Skills help you build more reliable, repeatable agent workflows:

- **Optimized context use and improved accuracy.** Skills use progressive disclosure: the model loads a skill's instructions and contents into context only when the task requires them. The agent's context stays focused even as its library of skills grows. Providing scripts, rather than relying on model-generated code, also brings more repeatability to your workflows.
- **Scale instructions without quality loss.** You can decompose complex instructions into modular, reusable skills. This approach lets you provide longer, more specific guidance without degrading instruction-following quality and without running into the 8,000-character limit on declarative agent instructions.
- **Package reusable assets.** You can package instructions, resources, and scripts together as a skill and integrate that capability into your declarative agent.
- **Enterprise-ready.** Scripts run in a secure sandbox, sensitivity labels on skill files are retained and honored, and admin governance is available.

## Support matrix

Some limits differ depending on whether you add the skill with Agent Builder or Agents Toolkit.

The following table describes those two authoring paths, not WIQD limits or feature coverage. For the recommended pro-code route, confirm current requirements in the [WIQD documentation](https://aka.ms/wiqd/docs).

| Item | Agent Builder | Agents Toolkit |
| :--- | :--- | :--- |
| Maximum skills per agent | 8 | 8 |
| Skill package | Compressed `.zip`, maximum 50 MB | Skill directory; `.zip` isn't supported |
| Maximum file size | 25 MB per file | No skill-level limit; the complete app package is limited to 10 MB |
| Maximum files per package | 350 files across all skills | 350 files across all skills |
| Build a skill from individual uploads | Not supported; upload the complete `.zip` | Add or import the complete skill directory |
| Directory hierarchy | Maximum directory depth is 3 | Maximum directory depth is 3 |
| Reuse across agents | Not supported | Not supported |

## Supported file and script types

A skill can include the following file types:

| Category | File types |
| :--- | :--- |
| Instructions and resource files | `.json`, `.xml`, `.yaml`, `.yml`, `.ini`, `.config`, `.utf8`, `.docx`, `.doc`, `.docm`, `.pdf`, `.txt`, `.rtf`, `.md`, `.ppt`, `.pptx`, `.ppsm`, `.xlsx`, `.xls`, `.xlsm`, `.csv`, `.tsv`, `.html`, `.htm`, `.png`, `.jpg`, `.jpeg`, `.gif`, `.bmp`, `.log` |
| Scripts and binaries | `.py`, `.js`, `.mjs`, `.cjs`, `.ts`, `.mts`, `.sh`, `.bash` |

## Script execution sandbox

Skill scripts run in a secure sandbox with the following limits:

| Capability | Support |
| :--- | :--- |
| Internet or network access from scripts | The sandbox has no network access at runtime, except during browser use. |
| Package installation | Not supported. A skill can't install packages at runtime. |
| Authenticated network calls from scripts | Not supported. |
| Preinstalled packages and tools | A skill can use only packages and tools already present in the sandbox. See [Available packages and tools](#available-packages-and-tools). |
| Connectors, API plugins, and MCP servers | The agent can use enabled capabilities through the orchestrator. Scripts can't call them through the sandbox. |

### Available packages and tools

The same sandbox and package inventory apply to skills attached to declarative agents and skills used directly in Copilot Chat. Service updates can change package availability and versions.

| Category | Packages and tools |
| :--- | :--- |
| Documents and spreadsheets | `python-docx`, `python-pptx`, `openpyxl`, `xlsxwriter`, `docx`, `pptxgenjs`; LibreOffice, Pandoc |
| PDF processing | `pypdf`, `pymupdf`, `pdfplumber`, `reportlab`, `pdf-lib`, `pdfjs-dist`; Poppler \(`pdftotext`, `pdfinfo`, `pdftoppm`\), Ghostscript |
| Data analysis | `numpy`, `pandas`, `scipy`, `scikit-learn` |
| Charting | `matplotlib`, `plotly`, `seaborn` |
| Image and vector processing | `pillow`, `sharp`; ImageMagick, Inkscape |
| OCR | `pytesseract`, `ocrmypdf`; Tesseract |
| Audio/video processing | FFmpeg |
| LaTeX document generation | TeX Live \(`pdflatex`, `latexmk`\) |
| JSON processing | `jq` |
| Developer tooling | TypeScript, `ts-node`, Jupyter components, Playwright |

## Sensitivity and storage

| Item | Support |
| :--- | :--- |
| Sensitivity labels | The sandbox retains sensitivity labels and honors label policies. It doesn't support user-defined permissions or Double Key Encryption. |
| Storage | The system stores uploaded skill files in tenant-scoped SharePoint Embedded containers. |

## Related content

- [Add skills to your declarative agent in Agent Builder](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/agent-builder-add-skills)
- [Add skills to a declarative agent created with Microsoft 365 Agents Toolkit](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/build-declarative-agents-add-custom-skills)
