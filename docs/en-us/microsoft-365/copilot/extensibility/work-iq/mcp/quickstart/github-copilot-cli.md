<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/work-iq/mcp/quickstart/github-copilot-cli -->
<!-- Sitemap-Last-Modified: 2026-07-01 -->

# Connect GitHub Copilot CLI to the Work IQ MCP server

Use GitHub Copilot CLI as a Model Context Protocol \(MCP\) client to connect to the remote Work IQ MCP server. After you configure the connection, Copilot can discover Work IQ MCP tools, authenticate with Microsoft Entra ID, and use those tools to work with Microsoft 365 data according to the signed-in user's permissions and tenant policy.

This quickstart shows how to configure GitHub Copilot CLI for the remote Work IQ MCP endpoint and verify that the connection is working.

## Prerequisites

Before you start, make sure you have:

- Access to GitHub Copilot CLI.
- A Microsoft 365 account that can access the business data you want to retrieve.
- Access to the remote Work IQ MCP server endpoint, `https://workiq.svc.cloud.microsoft/mcp`.

## Set up GitHub Copilot CLI

If you don't already have GitHub Copilot CLI installed, install it by following the GitHub Copilot CLI setup instructions in [Using GitHub Copilot CLI](https://docs.github.com/copilot/how-tos/use-copilot-agents/use-copilot-cli).

After installation, start GitHub Copilot CLI from your terminal:

```console
copilot
```

If you're prompted to sign in, use the `/login` command and follow the prompts:

```console
/login
```

## Install the Work IQ plugin

Install the Work IQ plugin in GitHub Copilot CLI. The plugin configures the Work IQ MCP integration and makes the related skills available in Copilot CLI.

1. Add the Work IQ plugin marketplace. You only need to do this step once.

   ```console
   /plugin marketplace add microsoft/work-iq
   ```

2. Install the Work IQ plugin.

   ```console
   /plugin install workiq@work-iq
   ```

3. Follow the prompts to complete the installation.
4. Restart GitHub Copilot CLI.
5. A browser pop-up window appears and displays **Authorization Successful**.

## Verify the MCP server and skills

After you install the plugin, verify that the Work IQ MCP server and skills are loaded.

To manage or inspect configured MCP servers, run:

```console
/mcp
```

You see `workiq` in the plugins list with the Work IQ MCP server endpoint, `https://workiq.svc.cloud.microsoft/mcp`.

To manage or inspect available skills, run:

```console
/skills
```

You see `workiq` in the skills list.

## Play with your Microsoft 365 and business application data

After the Work IQ MCP server and skills load, ask Copilot CLI to retrieve Microsoft 365, Power Platform, and Dynamics 365 business data through Work IQ. The first request might prompt you to authenticate with Microsoft Entra ID.

For example, try prompts like:

```text
Summarize my upcoming meetings for today.
```

```text
Find recent messages about the Contoso account.
```

```text
Retrieve the latest email related to the quarterly business review.
```

```text
Show me my highest-priority open cases.
```

Copilot CLI uses the Work IQ MCP server to call the appropriate tools. The result depends on the signed-in user's Microsoft 365 permissions, the application's OAuth permissions, and tenant policy. If policy or permissions block a request, revise the request or contact your administrator.

## Related content

- [Work IQ MCP overview](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/work-iq/mcp/overview)
- [Work IQ MCP tool reference](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/work-iq/mcp/tool-reference)
- [Policy governance for Work IQ MCP](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/work-iq/mcp/policy-governance-mcp)
