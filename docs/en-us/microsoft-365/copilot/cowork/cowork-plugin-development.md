<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/copilot/cowork/cowork-plugin-development -->
<!-- Sitemap-Last-Modified: 2026-10-02 -->

# Build plugins for Copilot Cowork

Microsoft Copilot Cowork supports extensibility through M365 App Packages—the same distribution mechanism used by Teams apps, Copilot agents, and Office add-ins. You can extend Cowork with:

- **Skills**: Prompt-based workflows that teach Cowork new domain expertise, such as financial analysis, legal research, or HR workflows.
- **Connectors**: Remote servers that give Cowork access to external data sources and APIs.

Both are packaged together in a standard Microsoft 365 app package and distributed through the Microsoft 365 App Store.

Important

[Microsoft Purview Information Barriers \(IB\)](https://learn.microsoft.com/en-us/purview/information-barriers) aren't currently supported for plugin or skill management and sharing. In tenants where IB is enabled, embedded knowledge file uploads are blocked at the tenant level. This prevents affected plugins and skills from being uploaded or published.

Microsoft doesn't create or maintain any persistent index, knowledge graph \(including the Microsoft Graph\), or database that includes ISV Content, whether by crawling, scraping, harvesting, bulk export, ingestion, or any other method \(via API, MCP server, or otherwise\). Microsoft might temporarily process ISV Content as necessary to respond to a user’s real-time query, but doesn't retain ISV Content beyond the duration of that session. Upon ISV's written request, Microsoft deletes any ISV Content in its possession or control within 10 business days and certifies such deletion in writing. Learn more in [Enterprise data protection in Microsoft Copilot and Microsoft Copilot Chat](https://learn.microsoft.com/en-us/microsoft-365/copilot/enterprise-data-protection).

## What you'll build

A Cowork plugin is a `.zip` package containing:

```
my-extension.zip
├── manifest.json          # M365 Unified App Manifest (v1.28)
├── color.png              # 192×192 full-color app icon
├── outline.png            # 32×32 outline icon
└── skills/                # Agent Skills (SKILL.md files)
    ├── skill-one/
    │   ├── SKILL.md
    │   └── references/    # Optional deep-dive docs
    └── skill-two/
        └── SKILL.md
```

Skills use the Agent Skills open standard—the same format supported by Claude Code, Visual Studio Code Copilot, Gemini CLI, Cursor, JetBrains Junie, and 30+ other AI tools.

## Choose your starting point

Build your plugin with the [wiqd CLI](https://microsoft.github.io/wiqd/). The CLI scaffolds the package and keeps `manifest.json` and your skill folders in sync. It also runs the platform's own validation rules before you upload, then provisions and shares the result. The CLI is in preview, so its commands and generated output can change before general availability. Everything it generates is a plain Microsoft 365 app package, so you can still open, edit, and version the files directly.

Assemble the package manually only when you can't install tooling, or when you're building your own packaging pipeline. In that case, the [package format reference](#assemble-a-package-by-hand) in this article is what you need—it describes exactly what `wiqd` produces.

| Starting point | Do this | Time to first package |
| --- | --- | --- |
| I'm starting from scratch | [Build a plugin with wiqd](#build-a-plugin-with-wiqd) | about 10 minutes |
| I have an existing Claude Code plugin | [Convert it](#import-an-existing-plugin) | about 5 minutes |
| I can't install tooling, or I'm scripting my own packaging | [Assemble a package by hand](#assemble-a-package-by-hand) | about 30 minutes |

## Build a plugin with wiqd

The wiqd CLI runs the same lifecycle you otherwise do manually—create, add capabilities, validate, provision, package, and share. The package it produces already satisfies the [validation rules](#validation-rules) in this article.

### Step 1: Install wiqd and sign in

Install the wiqd CLI by following the [wiqd installation guide](https://microsoft.github.io/wiqd/getting-started/installation/), which covers Windows, macOS, and Linux. Then sign in to the Microsoft 365 tenant you're developing against, because provisioning and sharing both touch your tenant:

```console
wiqd auth login --interactive
```

The installer also registers a GitHub Copilot CLI plugin, so you can drive the same lifecycle conversationally. For example, you can say, *Create a standalone plugin called Triage Helper* or *Validate my plugin.* The conversational path runs the same commands as this section. Use the commands directly when you're scripting a pipeline or want reproducible, non-interactive automation.

### Step 2: Scaffold the plugin and add capabilities

Create the plugin container, then add whatever capabilities you need, in any combination:

```console
wiqd plugin create --name my-plugin
wiqd plugin add skill --name "Contract Analysis"
wiqd plugin add connector --name "Contoso Legal" --description "Case law and statutes over MCP" --url https://api.contoso.com/legal/mcp
```

`add skill` scaffolds `appPackage/skills/contract-analysis/SKILL.md` and registers it in `agentSkills[]`. `add connector` writes the `agentConnectors[]` entry. Both commands enforce the platform's naming and size caps before writing, so a folder-name mismatch or an over-length `id` never reaches the manifest.

Write your skill logic in the generated `SKILL.md`. The frontmatter fields, progressive-loading model, and companion-file limits are the same ones described in [Step 1: Create your first skill](#step-1-create-your-first-skill) and [Step 2: Add reference materials \(optional\)](#step-2-add-reference-materials-optional).

Important

`wiqd plugin create` pins the package to `manifestVersion: "1.29"`, while the hand-authored examples in this article use `1.28`. The difference matters for connectors. At 1.28, `mcpToolDescription` is required, and the file it names must be in the ZIP. At 1.29, `agentConnectors[]` entries are URL-only and `mcpToolDescription` is optional, so a wiqd-generated package never hits that upload failure. wiqd doesn't scaffold connector authentication yet—configure it directly as described in [Supported auth types](#supported-auth-types).

### Step 3: Validate as you build

Validate continuously instead of assembling a package and hoping the upload passes:

```console
wiqd plugin validate
wiqd plugin validate --mode deep
```

`validate` is the offline static check over the declarative-agent surface. A skills-only or connector-only plugin passes it with nothing to check, which is expected—it's a check for your build loop, not full coverage. `validate --mode deep` packages the plugin first, then validates the built `.zip` against the same App Validation Library the upload uses. That's where the [ASKILL codes](#validation-rules) and connector rules surface.

### Step 4: Provision, package, and share

Run these three commands in order:

```console
wiqd plugin provision
wiqd plugin package
wiqd plugin share --scope users --email you@contoso.com
```

Run `provision` first because it writes the environment file that `package` and `share` both depend on. Use `--scope users` to share with the people you list, or `--scope tenant` to share with everyone in your organization. Either way, the plugin appears in **Shared with me** under **Cowork** > **Sources & Skills** > **Plugins**. To list it in the **Discover** section instead, an admin uploads the package. Learn more in [Step 8: Publish to your tenant](#step-8-publish-to-your-tenant). To remove what `provision` created, run `wiqd plugin delete --env local --yes`.

Public store submission is still a manual process in Partner Center. Learn more in [Step 9: Publish to the public](#step-9-publish-to-the-public).

### Take a plugin to another host

To use your skills in Claude Code, Cursor, or any other Agent Skills host, export the project rather than copying folders by hand:

```console
wiqd plugin export --format claude-plugin
```

`export` defaults to `--format open-plugin` and also accepts `cursor-plugin`. It writes an uncompressed directory under `<path>/export/<format>`.

## Import an existing plugin

If you already have a Claude Code plugin with skills and MCP servers, you have two conversion routes. The route you choose depends on whether you plan to keep developing the plugin or just ship what you have.

| Goal | Use |
| --- | --- |
| Keep developing, validating, and shipping the plugin from Microsoft 365 | [`wiqd plugin import`](#import-with-wiqd) |
| Produce a publishable `.zip` from an existing Claude plugin right now | [The conversion script](#convert-with-the-conversion-script) |

### Import with wiqd

`wiqd plugin import` recognizes an Open Plugin, Claude plugin, or Cursor plugin source and produces a wiqd plugin project from it. The imported plugin joins the same lifecycle as one you created with `wiqd plugin create`:

```console
wiqd plugin import --path ./my-claude-plugin --privacy-url https://contoso.com/privacy --terms-url https://contoso.com/terms
```

`--privacy-url` and `--terms-url` are required only on a plugin's first import. If the source came from a previous `wiqd plugin export`, the round-trip metadata already carries them.

Important

An imported project supports only the read-only part of the lifecycle—`wiqd plugin validate`, `show`, and `list`. It can't yet be packaged, provisioned, or shared, because the import doesn't scaffold the local deploy files those steps need. This is a tracked gap. For current status, check the [wiqd CLI reference](https://microsoft.github.io/wiqd/cli/reference/). If you need a publishable package today, use the conversion script.

### Convert with the conversion script

The [conversion script](https://aka.ms/copilot-cowork-plugin-conversion-script) translates a Claude plugin directly into a publishable M365 package:

1. Install the CLI \(requires version 1.1.12 or later\):

   ```bash
   npm install -g @microsoft/m365agentstoolkit-cli
   ```

2. Verify the version:

   ```bash
   atk --version
   ```

3. Import your plugin:

   ```bash
   atk import openplugin --path ./my-claude-plugin --output ./my-plugin-project \
     --privacy-url https://contoso.com/privacy \
     --terms-url https://contoso.com/terms
   ```

The command reads your plugin's `.claude-plugin/plugin.json` \(or `.cursor-plugin/plugin.json`\), `.mcp.json`, and `skills/` directory, then scaffolds an Agents Toolkit project containing `appPackage/manifest.json`, your skills, and generated icons.

You must include `--privacy-url` and `--terms-url` because plugin manifests don't have equivalent fields, and the Microsoft 365 manifest requires both.

Note

`atk import openplugin` locates a plugin manifest in a dot-prefixed directory—`.claude-plugin/plugin.json`, `.cursor-plugin/plugin.json`, or `.plugin/plugin.json`—alongside a `.mcp.json`. The [Agent Plugins 1.0.0](https://agent-plugins.org/) specification places the manifest at a top-level `plugin.json` and MCP configuration at `mcp.json`. To import a plugin that follows the 1.0.0 layout, move its manifest to `.plugin/plugin.json` and rename `mcp.json` to `.mcp.json`.

Package the result into an uploadable `.zip`:

```bash
cd my-plugin-project
atk package --manifest-file ./appPackage/manifest.json \
  --output-package-file ./appPackage/build/appPackage.zip \
  --output-folder ./appPackage/build
```

Note

`atk import openplugin` generates a `devPreview` manifest. The manifest examples elsewhere in this article target schema v1.28. If you're publishing through a channel that requires v1.28, update `manifestVersion` and `$schema` in the generated `appPackage/manifest.json`.

### What gets imported

| Plugin artifact | M365 equivalent | Notes |
| --- | --- | --- |
| `.claude-plugin/plugin.json` | `manifest.json` | Name, description, and developer fields mapped; GUID autogenerated \(deterministic UUID v5\) |
| `skills/*/SKILL.md` | `agentSkills[]` entries + `skills/` folder | Copied verbatim - identical format |
| `.mcp.json` servers | `agentConnectors[]` entries | URL and auth type autodetected |
| `color.png` / `outline.png` | Icons in package | Used if present; placeholders generated if missing |

Important

For each connector imported from `.mcp.json`, the generated `authorization.referenceId` is a placeholder derived from the plugin and server name. Replace it with your actual OAuth client registration ID before you publish. Learn more in [Supported auth types](#supported-auth-types).

### What's not converted

The following Claude plugin features aren't yet supported in the Microsoft 365 manifest:

| Claude plugin feature | Status |
| --- | --- |
| `commands/` \(slash commands\) | Not yet supported |
| `agents/` \(sub-agents\) | Not yet supported |
| `hooks/` \(event handlers\) | Not yet supported |
| `settings.json` | Not applicable |
| `bin/` \(executables\) | Not applicable |

### Import options

| Option | Description |
| --- | --- |
| `--path`, `-p` | **Required.** Plugin directory containing `.claude-plugin/plugin.json`, `.cursor-plugin/plugin.json`, or `.plugin/plugin.json` |
| `--output`, `-o` | Destination project folder \(default: `./<plugin-name>`\) |
| `--privacy-url` | `developer.privacyUrl` for the generated manifest |
| `--terms-url` | `developer.termsOfUseUrl` for the generated manifest |
| `--website-url` | `developer.websiteUrl`. Falls back to `homepage`, then `author.url` |
| `--app-id` | Override the deterministic UUID v5 generated for the manifest `id` |
| `--default-auth-type` | `Auto` \(default\), `None`, `OAuthPluginVault`, or `ApiKeyPluginVault` |

**Auth type autodetection:**

| Source | Default auth type | Reason |
| --- | --- | --- |
| External HTTPS URLs | `OAuthPluginVault` | Most remote APIs need auth |
| `localhost` and non-HTTPS URLs | `None` | Local development servers |

If the autodetection doesn't match your setup, use `--default-auth-type` to override it.

### Export back to a plugin directory

To move an Agents Toolkit project back to a plugin directory—for example, to keep a Claude Code plugin and a Cowork package in sync—use `atk export openplugin`:

```bash
atk export openplugin --path ./my-plugin-project \
  --output ./my-claude-plugin --manifest-kind claude-plugin
```

| Option | Description |
| --- | --- |
| `--path`, `-p` | **Required.** Agents Toolkit project folder containing `appPackage/manifest.json` |
| `--output`, `-o` | Destination plugin directory \(default: `./<plugin-name>-openplugin`\) |
| `--manifest-kind` | `open-plugin` \(default, writes `.plugin/plugin.json`\), `claude-plugin`, or `cursor-plugin` |

Export writes an `x-microsoft-365-agents-toolkit` block into the generated `plugin.json`. That block carries the manifest `id`, developer URLs, and connector settings, so a later `atk import openplugin` round-trips without needing `--privacy-url` or `--terms-url` again.

Note

The `x-microsoft-365-agents-toolkit` block is specific to Agents Toolkit, and the default `open-plugin` kind writes the manifest to `.plugin/plugin.json`. [Agent Plugins 1.0.0](https://agent-plugins.org/) uses a top-level `plugin.json` and carries client-specific data under an `extensions` key with a reverse-domain namespace, so other clients ignore this block rather than acting on it. When your target is Claude Code or Cursor, use `--manifest-kind claude-plugin` or `cursor-plugin`.

### Legacy: PowerShell conversion script

Before `atk` supported plugin import, conversion used a Windows-only PowerShell script, which remains available as the [conversion script](https://aka.ms/copilot-cowork-plugin-conversion-script):

```powershell
.\Convert-ClaudePluginToMOS3.ps1 -PluginPath ./my-claude-plugin -OutputPath ./output
```

Use `atk import openplugin` instead. It's cross-platform, supports Cursor as well as Claude Code sources, and can export back to a plugin directory.

## Assemble a package by hand

This section is the package-format reference: it describes exactly what [Build a plugin with wiqd](#build-a-plugin-with-wiqd) generates, field by field. Follow it end to end when you can't install tooling or you're building your own packaging pipeline. Use it as a reference when you need to understand or debug a generated package.

### Step 1: Create your first skill

A skill is a folder containing a `SKILL.md` file. Create the following folder structure:

```
my-extension/
└── skills/
    └── contract-analysis/
        └── SKILL.md
```

Write `SKILL.md` with YAML frontmatter and a Markdown body:

```yaml
---
name: contract-analysis
description: |
  Analyzes contracts for key terms, risks, and obligations.
  Use when user asks to "review this contract", "find the liability clause",
  "summarize the key terms", or "compare these two agreements".
license: MIT
metadata:
  author: Contoso Legal Tech
  version: "1.0"
---

# Contract Analysis

## What This Skill Does

Guides Cowork through systematic contract review, identifying:
- Key commercial terms (pricing, payment, renewal)
- Risk clauses (indemnification, limitation of liability, IP)
- Obligations and deadlines
- Non-standard or unusual provisions

## Workflow

1. Read the uploaded contract document
2. Extract and categorize all clauses
3. Flag risk areas with severity ratings
4. Generate a structured summary with recommendations

## Output Format

Present findings in a structured table:

| Clause | Category | Risk Level | Summary |
|--------|----------|------------|---------|
| Section 4.2-Indemnification | Risk | High | Unlimited indemnification for IP claims |
| Section 7.1-Term | Commercial | Low | 12-month auto-renewal with 30-day notice |
```

#### SKILL.md frontmatter fields

**Required fields:**

| Field | Constraints | Description |
| --- | --- | --- |
| `name` | 1-64 characters, kebab-case | Skill identifier - must match the folder name exactly |
| `description` | 1-1024 characters | When to use this skill - include trigger phrases |

Important

- The folder name must match the `name` field in the frontmatter. This mismatch is the most common cause of skill failures.
- Plugin listing `description` fields shouldn't include calls to action directing users to external marketplaces to purchase subscriptions.

| Folder path | `name` field | Valid? | Why |
| --- | --- | --- | --- |
| `skills/contract-analysis/SKILL.md` | `contract-analysis` | Yes | Folder and name match |
| `skills/contract-analysis/SKILL.md` | `ContractAnalysis` | No | Name uses PascalCase instead of matching folder |
| `skills/my-skill/SKILL.md` | `contract-analysis` | No | Folder is `my-skill` but name is `contract-analysis` |

**Naming rules \(kebab-case\):** Use only lowercase alphanumeric characters and hyphens. Don't use consecutive hyphens, and don't use leading or trailing hyphens.

| Example | Valid? | Issue |
| --- | --- | --- |
| `bond-relative-value` | Yes | Lowercase with hyphens |
| `fx-carry-trade` | Yes | Lowercase with hyphens |
| `email` | Yes | Single word, no hyphens needed |
| `Bond_Relative_Value` | No | Underscores and uppercase letters |
| `--my-skill--` | No | Leading and trailing hyphens |
| `my--skill` | No | Consecutive hyphens |

### Step 2: Add reference materials \(optional\)

For complex skills, keep the main `SKILL.md` lean and move detailed content to subdirectories. These extra files are **companion files**. The skill loads them when needed.

```
skills/
└── contract-analysis/
    ├── SKILL.md               # Core workflow (~1,500-2,000 words ideal)
    ├── references/            # Deep-dive docs loaded on demand
    │   ├── clause-taxonomy.md
    │   └── risk-scoring.md
    └── scripts/               # Executable utilities
        └── extract-clauses.py
```

#### Companion file limits

Each skill can include up to 20 companion files \(any file other than `SKILL.md`\). The following limits apply per skill:

| Limit | Value |
| --- | --- |
| Maximum companion files | 20 |
| Maximum size per companion file | 5 MB |
| Maximum total companion size | 10 MB |
| Download timeout \(all companions\) | 15 seconds |

#### Companion file rules

Companion file paths must follow these rules:

- Use relative paths only \(no absolute paths\).
- No path traversal \(`..` segments\).
- No backslashes or null bytes in file names.
- No hidden files \(names starting with `.`\).
- No Windows reserved names \(`CON`, `PRN`, `AUX`, `NUL`, `COM1`–`COM9`, `LPT1`–`LPT9`\).
- The file `SKILL.md` itself doesn't count as a companion file.
- File names must use safe characters: alphanumeric, hyphens, underscores, dots, spaces, and `!`.

To keep the context window efficient, the system loads skills in three layers:

| Layer | When loaded | Target size |
| --- | --- | --- |
| Frontmatter \(`name` + `description`\) | Always - at startup | ~100 tokens |
| `SKILL.md` body | When skill triggers | Less than 5,000 tokens \(1,500-2,000 words\) |
| References \(`references/`\) | On demand by the agent | Unlimited |
| Scripts \(`scripts/`\) | Executed, not loaded into context | N/A |

Reference the subdirectories explicitly in `SKILL.md` so the agent knows they exist:

```markdown
## Additional Resources

- **`references/clause-taxonomy.md`**-Full taxonomy of contract clause types
- **`references/risk-scoring.md`**-Risk scoring methodology and thresholds
- **`scripts/extract-clauses.py`**-Automated clause extraction utility
```

### Step 3: Add a connector \(optional\)

If your extension needs access to external data, add a remote MCP server. This step is optional. Skills-only packages work well for prompt-based workflows.

Tip

If your server gates tool visibility by client or attributes incoming traffic, go to [Identify Cowork traffic to your server](#identify-cowork-traffic-to-your-server) for the client identity Cowork presents.

Note

Custom plugins aren't supported in [Cowork on mobile](https://learn.microsoft.com/en-us/microsoft-365/copilot/cowork/cowork-mobile).

#### Connector requirements

| Requirement | Details |
| --- | --- |
| Transport | Streamable HTTP \(HTTPS required, TLS 1.2+\) |
| Protocol | JSON-RPC 2.0 message format |
| Tool discovery | Support `tools/list` for dynamic discovery \(recommended\) |
| Tool execution | Support `tools/call` for invocation |
| Availability | 99.9% uptime SLA recommended for store-published apps |
| Response time | Less than 30 seconds per tool call |

#### Tool design guidelines

- **One tool per action** for small APIs \(fewer than 15 operations\): `search_case_law`, `get_ruling`, `cite_precedent`
- **Search + execute** for large APIs \(50+ operations\): `search_actions` + `execute_action`
- **Descriptive names**: `get_bond_price` not `getData`
- **Rich input schemas**: Include a description for every parameter—this is what the agent reads
- **Structured output**: Return JSON that the agent can format for the user
- **File inputs**: To accept a file from the user's workspace, declare the parameter with `contentEncoding: base64`. Learn more in [Accept files from the Cowork workspace](#accept-files-from-the-cowork-workspace).

#### Describe your connector's tools \(`mcpToolDescription`\)

A `remoteMcpServer` connector can optionally include an `mcpToolDescription` object. When provided, its nested `file` property points to a tool-description JSON file that you package inside your `.zip` and reference by a relative path from the package root. Cowork discovers tools dynamically from your MCP server and doesn't use this file, even when it's present.

```json
"remoteMcpServer": {
  "mcpServerUrl": "https://api.contoso.com/legal/mcp",
  "mcpToolDescription": {
    "file": "./tools/contoso-legal-tools.json"
  },
  "authorization": {
    "type": "OAuthPluginVault",
    "referenceId": "A1bC2dE3fH4iJ5kL6mN7oP8qR9sT0u"
  }
}
```

If you include `mcpToolDescription`, the referenced file \(for example, `tools/contoso-legal-tools.json`\) describes the tools the connector exposes and **must be present in the ZIP package**. Include it alongside your `manifest.json` and `skills/` folder when you package the plugin.

Tip

This requirement applies to manifest version 1.28. Packages that `wiqd plugin create` generates target 1.29, where `agentConnectors[]` entries are URL-only, `mcpToolDescription` is optional, and there's no tool-description file to forget.

#### Supported auth types

| Auth type | When to use | User experience |
| --- | --- | --- |
| `None` | Public or anonymous APIs, internal services | Transparent - no auth prompt |
| `OAuthPluginVault` | OAuth 2.0 APIs \(recommended for production\) | User completes OAuth consent once |
| `ApiKeyPluginVault` | API key-based services | User provides key once |

Note

- Support for API key authentication isn't available in Cowork yet.
- If your MCP server requires an API key, use `OAuthPluginVault` or Dynamic Client Registration instead, or expose an endpoint that accepts `None`.

For `OAuthPluginVault` and `ApiKeyPluginVault`, the `referenceId` points to credentials stored in the Microsoft Enterprise Token Store - secrets never appear in the manifest or skill files. The `referenceId` value is the OAuth client registration ID that you create when you [register an OAuth client with Agents Toolkit](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api-plugin-authentication#register-an-oauth-client-with-agents-toolkit).

Important

When registering your OAuth client, set the usage by organization to **Any Microsoft 365 Organization** to ensure your plugin works across tenants.

#### MCP authentication

To use OAuth or ApiKey for authentication, refer to [Configure authentication for MCP and API plugins in agents in Microsoft 365 Copilot](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/plugin-authentication) for setup and configuration details.

#### Dynamic Client Registration

If your MCP server supports Dynamic Client Registration \(DCR\), you can omit an `authentication` configuration from your connector definition, and Cowork automatically creates an OAuth client on your plugin's behalf.

Note

Omitting the `authentication` configuration is supported only in Cowork. It isn't supported in Copilot Chat. If your plugin also needs to work in Copilot Chat, configure `OAuthPluginVault` authentication as described in [Supported auth types](#supported-auth-types).

You can omit the `authorization` object entirely. Configure your MCP server URL, and Cowork takes care of the OAuth client:

```json
"remoteMcpServer": {
  "mcpServerUrl": "https://api.contoso.com/legal/mcp"
}
```

### Step 4: Create the manifest

Create `manifest.json` in your package root. The example uses manifest version 1.28; `wiqd plugin create` pins 1.29 instead, where connector entries are URL-only.

```json
{
  "$schema": "https://developer.microsoft.com/json-schemas/teams/v1.28/MicrosoftTeams.schema.json",
  "manifestVersion": "1.28",
  "version": "1.0.0",
  "id": "YOUR-GUID-HERE",
  "developer": {
    "name": "Contoso Legal Tech",
    "websiteUrl": "https://contoso.com",
    "privacyUrl": "https://contoso.com/privacy",
    "termsOfUseUrl": "https://contoso.com/terms"
  },
  "name": {
    "short": "Contoso Legal Tools",
    "full": "Contoso Legal Tools for Copilot Cowork"
  },
  "description": {
    "short": "Contract analysis, clause extraction, and legal research",
    "full": "Comprehensive legal tools for Copilot Cowork including contract analysis, clause extraction, risk assessment, and legal research capabilities."
  },
  "icons": {
    "color": "color.png",
    "outline": "outline.png"
  },
  "accentColor": "#2B579A",
  "agentSkills": [
    { "folder": "./skills/contract-analysis" }
  ]
}
```

To add a connector, include `agentConnectors`:

```json
{
  "agentConnectors": [
    {
      "id": "contoso-legal-api",
      "displayName": "Contoso Legal Database",
      "description": "Access to case law, statutes, and regulatory databases",
      "toolSource": {
        "remoteMcpServer": {
          "mcpServerUrl": "https://api.contoso.com/legal/mcp",
          "mcpToolDescription": {
            "file": "./tools/contoso-legal-tools.json"
          },
          "authorization": {
            "type": "OAuthPluginVault",
            "referenceId": "A1bC2dE3fH4iJ5kL6mN7oP8qR9sT0u"
          }
        }
      }
    }
  ]
}
```

In the connector configuration, `referenceId` should be the OAuth registration ID. If you include `mcpToolDescription`, its `file` must point to a tool-description JSON file that's included in the ZIP package.

Important

The v1.28 manifest schema is strict: it sets `additionalProperties: false` at the root, so any field that isn't defined in the schema is rejected. Fields that are valid in standard Teams app manifests—such as `packageName`—cause the upload to fail with an error like `Property 'packageName' has not been defined and the schema does not allow additional properties.` Include only the fields shown here.

### Step 5: Add icons

Create two PNG icons:

| Icon | Size | Purpose |
| --- | --- | --- |
| `color.png` | 192×192 px | Full-color app icon shown in store and app list |
| `outline.png` | 32×32 px | Single-color outline icon for compact views |

If you don't have icons yet, `atk import openplugin` generates solid-color placeholders. Replace them before store submission.

### Step 6: Package

Create a ZIP file with all contents at the root level. \(`wiqd plugin package` produces this same structure after `wiqd plugin provision`.\)

```
contoso-legal-tools.zip
├── manifest.json
├── color.png
├── outline.png
├── tools/
│   └── contoso-legal-tools.json   # Referenced by mcpToolDescription (optional, connectors only)
└── skills/
    └── contract-analysis/
        ├── SKILL.md
        └── references/
            └── clause-taxonomy.md
```

If a connector includes `mcpToolDescription`, include the tool-description JSON file it references. Packages that don't use `mcpToolDescription`, including skills-only packages, don't need a `tools/` folder.

**Windows \(PowerShell\):**

```powershell
Compress-Archive -Path manifest.json, color.png, outline.png, tools, skills -DestinationPath contoso-legal-tools.zip
```

**macOS/Linux:**

```bash
zip -r contoso-legal-tools.zip manifest.json color.png outline.png tools/ skills/
```

**Using Microsoft 365 Agents Toolkit**

```
 atk package --manifest-file ./appPackage/manifest.json \
       --output-package-file ./appPackage/build/appPackage.zip \
       --output-folder ./appPackage/build
```

### Step 7: Test

To test your app, upload your app package to Teams as described in [Upload your app to Teams](https://learn.microsoft.com/en-us/microsoftteams/platform/concepts/deploy-and-publish/apps-upload).

If you built the plugin with wiqd, run `wiqd plugin provision` instead—it registers the plugin with your tenant for you. For personal testing of a hand-assembled package, sideload the app by using the Microsoft 365 Agents Toolkit command line interface:

1. Install `@microsoft/m365agentstoolkit-cli` from `npm`:

   ```bash
   npm install -g @microsoft/m365agentstoolkit-cli
   ```

2. Verify the installation by running:

   ```bash
   atk --version
   ```

3. Authenticate with your Microsoft 365 work account:

   ```bash
   atk auth login
   ```

4. Sign in to your work account and install the agent package. Replace the file path with the location of your ZIP package:

   ```bash
   atk install --file-path "C:/Users/myuser/myPackage.zip" --scope Personal
   ```


   A successful installation returns output that includes a `TitleId` and `AppId` for your account.

5. Save these IDs for later use when you update or uninstall.

Learn more in [Microsoft 365 Agents Toolkit command line interface](https://learn.microsoft.com/en-us/microsoftteams/platform/toolkit/microsoft-365-agents-toolkit-cli).

### Step 8: Publish to your tenant

Upload the package in the admin center to list your plugin in the **Discover** section, where anyone in your organization can find it:

1. Open **M365 admin center** > **Manage apps** > **Upload custom app**.
2. Select the ellipsis button \(**...**\) > **Add agent**.
3. Upload your `.zip` package.
4. Open **Cowork** > **Sources & Skills** > **Plugins**. Your plugin appears in the **Discover** section.

`wiqd plugin share` places the plugin in **Shared with me** rather than **Discover**. Use it for testing and for targeted rollout to specific people. Admin center upload is what lists a plugin for discovery.

### Step 9: Publish to the public

For plugins intended for public distribution, submit your plugin to the Microsoft 365 App Store via [Partner Center](https://partner.microsoft.com). Learn more in [Publish agents for Microsoft 365 Copilot](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/publish).

## Test a connector against a local MCP server

Connectors require an HTTPS `mcpServerUrl`. To test a server running on your machine, you need to expose it over a public HTTPS URL. [Dev tunnels](https://learn.microsoft.com/en-us/azure/developer/dev-tunnels/overview) provide a relay that terminates TLS for you.

```bash
devtunnel port create <tunnel> -p <port> --protocol http
```

Important

Use `--protocol http`, not `https`. The `--protocol` flag describes the **local** service the tunnel forwards to, not the public tunnel URL. Most local MCP servers speak plain HTTP, so if you set `--protocol https` while your server serves HTTP, every request through the tunnel returns a `502` error. The relay terminates TLS and serves the public URL over HTTPS regardless of this flag.

### Troubleshooting

| Symptom | Cause | Fix |
| --- | --- | --- |
| Every tunneled request returns `502` and the local server speaks HTTP | `devtunnel port create` was run with `--protocol https` | Recreate the port with `--protocol http` |
| Tunneled requests return `502` on macOS even though the local server is running | The server is bound to `0.0.0.0` \(IPv4-only\), but the tunnel dials `localhost`, which resolves to `::1` \(IPv6\) first | Bind the server to `::` so it accepts both IPv4 and IPv6 connections |
| Upload fails with `Property '<field>' has not been defined and the schema does not allow additional properties` | The manifest includes a field the v1.28 schema doesn't allow \(for example, `packageName`\) | Remove the field; the v1.28 schema uses `additionalProperties: false` |

## Packaging patterns

Choose the pattern that fits your extension:

### Skills only \(no connector\)

Best for prompt-based workflows, document analysis, and writing assistance.

```
my-skills-pack.zip
├── manifest.json          # agentSkills only, no agentConnectors
├── color.png
├── outline.png
└── skills/
    ├── skill-one/SKILL.md
    └── skill-two/SKILL.md
```

### Skills + remote connector

Best for data analysis, API integrations, and enterprise systems.

```
my-data-skills.zip
├── manifest.json          # agentSkills + agentConnectors
├── color.png
├── outline.png
├── tools/                 # Tool-description file(s) for mcpToolDescription (optional)
│   └── my-connector.json
└── skills/
    ├── analysis-workflow/SKILL.md
    └── reporting-workflow/SKILL.md
```

### Connector only \(no custom skills\)

Use this option for data sources that Cowork's built-in skills can already use.

```
my-connector.zip
├── manifest.json          # agentConnectors only, no agentSkills
├── color.png
├── outline.png
└── tools/                 # Tool-description file(s) for mcpToolDescription (optional)
    └── my-connector.json
```

### Imported Claude Code or Cursor plugin

Use this option for existing Claude ecosystem plugins that target Cowork. To keep developing the plugin in Microsoft 365, import it:

```console
wiqd plugin import --path ./claude-plugin --privacy-url https://contoso.com/privacy --terms-url https://contoso.com/terms
```

To produce a publishable `.zip` from the plugin as it stands today, use the conversion script:

```bash
atk import openplugin --path ./claude-plugin --output ./my-plugin-project \
  --privacy-url https://contoso.com/privacy \
  --terms-url https://contoso.com/terms
```

## Skill authoring best practices

Follow these guidelines to create skills that activate reliably and produce consistent results.

### Write effective descriptions

The `description` field determines when the agent activates your skill. Be specific:

```yaml
# Good-specific trigger phrases, concrete scenarios
description: |
  Analyzes bond relative value using Z-spreads, ASW spreads, and butterfly analysis.
  Use when user asks to "analyze bond spreads", "compare bonds",
  "rich-cheap analysis", "relative value", or "Z-spread calculation".

# Bad-vague, no trigger phrases
description: Provides bond analytics capabilities.
```

### Write effective workflows

- **Be specific in the description**. Include trigger phrases: "Use when user asks to..." This description is how the agent decides which skill to activate.
- **Structure as a workflow**. Number the steps. Each step should map to a concrete action \(read a file, call a tool, generate output\).
- **Define output format**. Show the exact table, list, or document structure users should expect. This definition improves consistency dramatically.
- **Reference tools by name**. If your skill depends on connector tools, name them explicitly: "Use the `search_case_law` tool to..."
- **Keep the main SKILL.md lean**. Move detailed reference material to the `references/` subdirectory. The skill body should be the workflow, not an encyclopedia.

### Avoid common mistakes

- **Don't embed secrets** in `SKILL.md` files. Use `agentConnectors` with authentication for API credentials.
- **Don't duplicate built-in skills**. Check the [built-in skills list](https://learn.microsoft.com/en-us/microsoft-365/copilot/cowork/use-cowork#cowork-skills) before building.
- **Don't make skills too broad**. "Do everything with legal documents" is worse than specific skills for "contract analysis", "clause extraction", and "legal research".
- **Don't hardcode file paths** or system commands. Skills should be portable across environments.
- **Don't put everything in SKILL.md**. If your body exceeds ~3,000 words, move detailed content to `references/`.

## Validation rules

When you submit your package, the platform validates it at multiple levels. Fix these errors before submission to avoid rejection.

To catch them as you build instead of at upload time, run `wiqd plugin validate --mode deep`. This command packages the plugin and runs these same rules locally. Learn more in [Step 3: Validate as you build](#step-3-validate-as-you-build).

### Manifest-level validation

| Code | Rule | Severity |
| --- | --- | --- |
| ASKILL-M001 | `folder` is required on each `agentSkills` entry | Error |
| ASKILL-M002 | `agentSkills` array can have up to 20 items | Error |
| ASKILL-M003 | `folder` path can have up to 256 characters | Error |

### Package-level validation

| Code | Rule | Common fix | Severity |
| --- | --- | --- | --- |
| ASKILL-P001 | Folder referenced in manifest exists in ZIP | Check your ZIP structure | Error |
| ASKILL-P002 | Folder contains a `SKILL.md` file | Add missing `SKILL.md` | Error |
| ASKILL-P003 | `SKILL.md` has valid YAML frontmatter between `---` delimiters | Fix YAML syntax | Error |
| ASKILL-P004 | Frontmatter includes `name` field | Add `name:` to frontmatter | Error |
| ASKILL-P005 | Frontmatter includes `description` field | Add `description:` to frontmatter | Error |
| ASKILL-P006 | `name` matches the folder name \(last path segment\) | Rename folder or fix `name:` | Error |
| ASKILL-P007 | `name` is kebab-case | Use `my-skill` not `MySkill` or `my_skill` | Error |
| ASKILL-P008 | No duplicate `folder` values in the array | Remove duplicates | Error |

### Connector validation

| Rule | Severity |
| --- | --- |
| Each connector requires an `id` and `displayName` | Error |
| All connector `id` values must be unique within the manifest | Error |
| Exactly one of `plugin` or `remoteMcpServer` | Error |
| `mcpServerUrl` must be a valid HTTPS URL | Error |
| If `mcpToolDescription` is present, its `file` must exist in the ZIP | Error |
| `authorization.referenceId` required unless type is `None` | Error |
| `authorization.referenceId` must not be present when type is `None` | Error |

### Companion file validation

The portal validates companion files \(reference materials, scripts, and other files alongside `SKILL.md`\) at upload and sync time:

| Rule | Severity |
| --- | --- |
| Maximum 20 companion files per skill \(excluding `SKILL.md`\) | Error |
| Each companion file must be 5 MB or smaller | Error |
| Total companion files must be 10 MB or smaller per skill | Error |
| File paths must be relative \(no absolute paths\) | Error |
| No path traversal segments \(`..`\) | Error |
| No backslashes or null bytes in file names | Error |
| No hidden files \(names starting with `.`\) | Error |
| No Windows reserved names \(`CON`, `PRN`, `AUX`, `NUL`, `COM1`–`COM9`, `LPT1`–`LPT9`\) | Error |
| File names must use safe characters only \(alphanumeric, hyphens, underscores, dots, spaces, `!`\) | Error |

## Cross-platform compatibility

Skills use the Agent Skills open standard. The same `SKILL.md` files work across multiple AI tools:

| Platform | Compatibility |
| --- | --- |
| Claude Code | Full-same `SKILL.md` format |
| Claude.ai Projects | Full-skills can be uploaded as project files |
| VS Code / GitHub Copilot | Full-Agent Skills supported in agent mode |
| Gemini CLI | Full-Agent Skills supported |
| JetBrains Junie | Full-Agent Skills supported |
| OpenAI Codex | Full-Agent Skills supported |
| Cursor | Full-Agent Skills supported |

If you're developing skills for both Claude Code and Copilot Cowork, author the plugin with wiqd. Then run `wiqd plugin export --format claude-plugin` to produce the Claude Code layout. If you'd rather start from the Claude Code plugin structure—it's the superset—the layout is:

```
my-plugin/
├── .claude-plugin/
│   └── plugin.json        # Claude plugin manifest
├── skills/
│   ├── skill-one/
│   │   ├── SKILL.md       # Works in both Claude Code AND M365
│   │   └── references/
│   └── skill-two/
│       └── SKILL.md
└── .mcp.json              # MCP server config (optional)
```

Then bring it into Microsoft 365 when you're ready to publish to the Microsoft 365 App Store, either with `wiqd plugin import` or with the conversion script:

```bash
atk import openplugin --path ./my-plugin --output ./my-plugin-project \
  --privacy-url https://contoso.com/privacy \
  --terms-url https://contoso.com/terms
```

## MCP annotation and confirmation management

Copilot Cowork reads the standard MCP `annotations` object on tools your server returns from `tools/list`, and uses it to decide whether a tool call needs user confirmation and what label to show on the prompt.

### Available fields

| Field | Type | Effect |
| --- | --- | --- |
| `readOnlyHint` | bool | `false`: confirmation required before the tool runs. |
| `destructiveHint` | bool | `true`: confirmation required before the tool runs. |
| `title` | string | Human-readable label shown on the confirmation dialog. Falls back to the tool name when absent. |

### Confirmation rules

Confirmation is required if `readOnlyHint == false` or `destructiveHint == true`.

All tools must have safety annotations specified. Tools without annotations are treated as destructive and require confirmation. Learn more in the [MCP schema reference](https://modelcontextprotocol.io/specification/latest/schema#toolannotations).

### MCP examples

A destructive action with a friendly label:

```json
{
  "name": "send_email",
  "description": "Send an email message.",
  "annotations": {
    "title": "Send Email",
    "destructiveHint": true
  },
  "inputSchema": { ... }
}
```

A safe read that auto-runs:

```json
{
  "name": "search_docs",
  "annotations": {
    "title": "Search Documents",
    "readOnlyHint": true
  }
}
```

### What's available now

- Microsoft tools \(Graph, Dataverse, and others\) are gated by Cowork's built-in policy regardless of annotations.
- For non-Microsoft MCP servers, annotation-driven confirmation is being rolled out progressively. Setting the hints now is forward-compatible, and confirmation prompts surface as the rollout expands with no developer change required.

## Accept files from the Cowork workspace

A connector tool can take a file from the user's Cowork session as input—a document the user attached, an email attachment Cowork saved, or a file an earlier step produced. Declare the parameter with the standard JSON Schema keyword `contentEncoding: base64` and Cowork handles the rest. No Microsoft-specific schema extension is required, and your server's API surface doesn't change.

Cowork resolves the workspace file and base64-encodes it *before* calling your server, so file bytes never enter the agent's context. The agent only ever sees and emits workspace file paths.

Note

Don't instruct the agent to base64-encode a file itself and paste the blob into a tool call. That approach loads the whole file into the model's context and depends on the model reproducing the blob exactly. It appears to work on small test files and fails on real ones.

### Declare a file parameter

A string property with `contentEncoding: base64` is recognized as a file input:

```json
{
  "name": "analyze_contract",
  "description": "Extract key terms from a contract document.",
  "annotations": {
    "title": "Analyze Contract",
    "readOnlyHint": true
  },
  "inputSchema": {
    "type": "object",
    "properties": {
      "document": {
        "type": "string",
        "contentEncoding": "base64",
        "description": "The contract file to analyze."
      },
      "jurisdiction": {
        "type": "string",
        "description": "Two-letter country code governing the contract."
      }
    },
    "required": ["document"]
  }
}
```

An array of such strings is also recognized, for tools that accept several files:

```json
"attachments": {
  "type": "array",
  "items": { "type": "string", "contentEncoding": "base64" },
  "description": "Receipt images to attach to the expense line."
}
```

### What the agent sees

For file parameters declared at the top level of `inputSchema.properties`, Cowork replaces them in the model-facing schema with a single `direct_attachment_file_paths` array—the same parameter Cowork's built-in tools use, so the agent already knows how to populate it. The schema above is presented to the agent as:

```json
{
  "type": "object",
  "properties": {
    "direct_attachment_file_paths": {
      "type": "array",
      "items": { "type": "string" },
      "description": "Workspace file paths to attach."
    },
    "jurisdiction": { "type": "string" }
  }
}
```

If your tool declares more than one top-level file parameter, all of them collapse into that single `direct_attachment_file_paths` array. At call time Cowork fans the resolved files back out into your original parameter names in declaration order.

### Nested file parameters

The agent supports a file parameter nested inside an object or an array of objects. The agent handles this parameter differently: instead of collapsing it, the agent rewrites it *in place* into a path string at its own location. This approach preserves the association between a file and its sibling fields. For example, you get one receipt per expense line:

```json
"line_items": {
  "type": "array",
  "items": {
    "type": "object",
    "properties": {
      "amount": { "type": "number" },
      "receipt": { "type": "string", "contentEncoding": "base64" }
    }
  }
}
```

The agent populates `line_items[].receipt` with a workspace path, and Cowork swaps each path for base64 content in place before forwarding the call.

Nesting is traversed to a depth of four levels below the top of `inputSchema`. `$ref` pointers aren't followed—define file parameters inline rather than behind a `$ref`.

### What your server receives

Your server receives an ordinary `tools/call` with your original parameter names populated with base64-encoded content:

```json
{
  "method": "tools/call",
  "params": {
    "name": "analyze_contract",
    "arguments": {
      "document": "JVBERi0xLjQKJcfsj6IKNSAwIG9iago8PC9MZW5...",
      "jurisdiction": "US"
    }
  }
}
```

Your server doesn't need to know that the agent used a path-based interface, and tools that don't declare `contentEncoding: base64` parameters are unaffected.

### Limits

| Limit | Value |
| --- | --- |
| Files per tool call | 8 |
| Size per file | 150 MiB |
| Total size per tool call | 150 MiB |
| Array file parameters per tool | 1 \(combine it with any number of scalar file parameters\) |
| Maximum nesting depth | 4 levels below the top of `inputSchema` |

A call that exceeds the file count or a size cap fails with a tool error and never reaches your server. Size your API and its timeouts with the 150 MiB ceiling in mind: base64 inflates the payload by roughly a third over the raw file size, and the encoded content is sent in the JSON-RPC request body.

### Recommendations

- **Describe the parameter for a human reader.** The agent uses the description to decide which file belongs in which parameter. For example, `"The signed contract PDF to analyze"` works better than `"file"`.
- **State the formats you accept** in the parameter description. Cowork passes through whatever the user attaches. Validate the content type on your side and return a clear tool error if it isn't usable.
- **Set annotations.** A tool that receives a file and acts on it is normally not read-only, so it prompts for confirmation. Learn more in [MCP annotation and confirmation management](#mcp-annotation-and-confirmation-management).
- **Keep file parameters inline.** A parameter behind a `$ref`, or nested deeper than four levels, isn't rewritten. Your server would receive a path string where it expects content.
- **Declare at most one array file parameter per tool.** With two or more, Cowork can't tell which file belongs in which array, and the call fails with a tool error. Use one array, or several scalar parameters, or a mix of scalars and a single array.
- **Expect an exact count on scalar-only tools.** If your tool declares only scalar file parameters, the number of files the agent passes must match the number declared. Mark optional file parameters clearly in their descriptions so the agent doesn't under- or over-supply.

Note

This mechanism predates the Model Context Protocol's own file-input work, which is being standardized by the [MCP File Uploads Working Group](https://modelcontextprotocol.io/community/working-groups/file-uploads). Cowork might add support for the standardized form of declarative file inputs once it lands. The `contentEncoding: base64` contract described here continues to work.

## Identify Cowork traffic to your server

If your MCP server gates tool visibility by client, or you want to attribute the traffic it receives, you can recognize requests that come from Cowork. Cowork presents a stable software identity on two channels:

| Channel | Where it appears | Value |
| --- | --- | --- |
| `User-Agent` request header | Every outbound request Cowork sends to your server | `copilot-cowork/1.0` |
| `clientInfo` in the MCP `initialize` handshake | The `initialize` request only | `{ "name": "copilot-cowork", "version": "<version>" }` |

### Match on the `copilot-cowork` prefix

Match the `copilot-cowork` **prefix**, case-insensitive, on either channel. Don't match the exact `copilot-cowork/1.0` string or a specific `clientInfo.version`. The version tracks the client-identity contract and is expected to change; a prefix match keeps your gate working across version bumps.

```
# Correct: case-insensitive prefix match
copilot-cowork

# Incorrect: exact match breaks when the version changes
copilot-cowork/1.0
```

### Choose the right channel for your gate

The two channels have different scopes, so key on the one that matches how your server enforces its gate:

- The `User-Agent` header is present on **every** request, including `tools/list` and `tools/call`. If you gate or attribute **per request**, key on this header.
- `clientInfo` is sent **only** on the `initialize` handshake. If you gate **per session** at connection time, you can read it there, but it isn't repeated on later requests.

### What the identity includes and doesn't include

The identity names the **software** only. It's the same for every Cowork user and connection, and it never carries user identity. User identity stays in the authorization flow your connector's auth configuration defines.

| The identity includes | The identity doesn't include |
| --- | --- |
| A stable software name \(`copilot-cowork`\) and a contract version | Any tenant, user, session, or conversation identifier |
| The same value on every request and every connection | A per-connector qualifier |

Because there's no per-connector qualifier, you can't currently use this identity to tell which connector made a call, or to separate a published Microsoft plugin from a sideloaded server pointed at the same URL. If you need that distinction, enforce it through your connector's authorization configuration rather than the client identity.

## Common questions

**Can I use skills from the M365 package in Claude Code?**

Yes. The skill folders contain standard Agent Skills. Run `wiqd plugin export --format claude-plugin` to produce the Claude Code layout, or copy the skill folders to `.claude/skills/` in any Claude Code project.

**Do I need a remote connector?**

No. Skills-only packages work well for prompt-based workflows. Connectors are only needed when your skill requires live data from an external system.

**How are plugin skills different from built-in skills?**

Plugin skills appear with source `"package"` in the API. They can't override built-in skills of the same name. Admin-deployed packages show `isAdminDeployed: true`.

**Can IT admins control which plugins are available?**

Yes. Standard M365 admin controls apply: tenant-level allow/block lists, admin-managed deployments, and compliance policies.

**What happens if a plugin is revoked?**

On the next sync cycle, the skills and connectors from that package are removed from the user's session. Active conversations aren't interrupted, but new sessions don't have the package's capabilities.

**What's the maximum number of skills per package?**

Twenty \(20\) skills \(per ASKILL-M002\). For connectors, the limit is 10 per package.

**Can skills reference connector tools from the same package?**

Yes, and they should. Name the tools explicitly in your `SKILL.md` workflow \(for example, "Use the `search_case_law` tool to..."\). The agent connects them at runtime.

**Can my plugin's tools accept files from the Cowork workspace?**

Yes. Declare the tool parameter with `contentEncoding: base64`, and Cowork resolves the user's workspace file to base64 content before calling your server. The model passes file paths, not file content, so large files don't consume the model's context. For declaration details and limits, learn more in [Accept files from the Cowork workspace](#accept-files-from-the-cowork-workspace).

**How do I generate a deterministic GUID for my package?**

`wiqd plugin create` generates and pins the app ID for you. The conversion script uses UUID v5 \(SHA-1 based\) from your plugin name, so running the conversion twice produces the same GUID. For manual packaging, use any GUID generator. Be sure to keep it stable across versions.

**Which manifest version should I target?**

Target 1.29 if you're building with wiqd, which pins it for you. At 1.29, `agentConnectors[]` entries are URL-only and `mcpToolDescription` is optional. The hand-authored examples in this article use 1.28, where `mcpToolDescription` is required and the file it names must be in the ZIP. `atk import openplugin` uses UUID v5 \(SHA-1 based\) from your plugin name. Running the import twice produces the same GUID. To set your own, pass `--app-id`. For manual packaging, use any GUID generator. Be sure to keep it stable across versions.

## Related content

- [Cowork overview](https://learn.microsoft.com/en-us/microsoft-365/copilot/cowork/)
- [Use Cowork](https://learn.microsoft.com/en-us/microsoft-365/copilot/cowork/use-cowork)
- [Manage Cowork for your organization](https://learn.microsoft.com/en-us/microsoft-365/copilot/cowork/cowork-admin-governance)
- [Manage plugins for Cowork](https://learn.microsoft.com/en-us/microsoft-365/copilot/cowork/cowork-manage-plugins)
- [wiqd plugin CLI reference](https://microsoft.github.io/wiqd/cli/reference/)
