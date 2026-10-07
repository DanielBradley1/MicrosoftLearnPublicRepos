<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/admin/manage/manage-tools-gateway?view=o365-worldwide -->
<!-- Sitemap-Last-Modified: 2026-09-29 -->

# Manage Tools Gateway

Connect your AI Gateway or Azure API Management \(APIM\) instance to the Microsoft 365 admin center to discover and govern the Model Context Protocol \(MCP\) servers registered with it. After a Global Administrator grants tenant-wide consent, the MCP servers appear on the **Tools** page, where administrators can manage them alongside other agent tools.

Important

- This feature is in preview.
- Preview features aren't meant for production use and might have restricted functionality. These features are subject to [supplemental terms of use](https://learn.microsoft.com/en-us/legal/microsoft-365/supplemental-terms), and are available before an official release so that customers can get early access and provide feedback.

## Capabilities

As an administrator, you can:

- View MCP servers registered in the connected gateway.
- Review MCP servers in the centralized tools inventory.
- Apply governance policies and control availability for agents.
- Automatically discover MCP servers added to the gateway later.

## Prerequisites

Before you begin, make sure that:

- An AI Gateway or APIM instance is configured.
- MCP servers are registered in the gateway.
- A Global Administrator is available to grant consent.
- You have access to the Microsoft 365 admin center.

## Connect your gateway

1. Sign in to the [Microsoft 365 admin center](https://admin.microsoft.com/) as a Global Administrator.
2. Go to **Agents** > **Settings**.
3. Select **Gateways**.
4. Under **Gateways**, connect one of the following gateway types:

   - **Microsoft Azure**: Turn on the toggle to connect an Azure API Management service or Azure AI Gateway. Review and accept the requested permissions. For Azure configuration and governance guidance, see [Govern tools with Microsoft Agent 365 and Azure API Management \(preview\)](https://go.microsoft.com/fwlink/?LinkId=2382608).
   - **LiteLLM gateway**: Select **Connect a gateway**, and then enter the gateway name, gateway URL, and API key.

Consent is required once per tenant and applies to all MCP servers in the connected gateway. Individual servers don't require separate consent.

## Review and govern MCP servers

Discovery starts automatically after consent is granted and typically completes within a few minutes.

1. In the Microsoft 365 admin center, go to **Agents** > **Tools**.
2. Filter the list by source, and then select **AI gateway** to review the discovered MCP servers.
3. Apply governance policies to block or allow each server.

Note

Tool-level granular control is supported for MCP servers registered in an AI Gateway tier in Azure API Management service. You can block or allow individual tools within a server instead of the entire server. For more information, see [Manage individual tools within an MCP server](https://learn.microsoft.com/en-us/microsoft-365/admin/manage/manage-plugins-skills-mcp-servers?view=o365-worldwide#manage-individual-tools-within-an-mcp-server).

New MCP servers registered in the connected gateway are discovered automatically during subsequent refreshes.

## Frequently asked questions

**Is AI Gateway or APIM required?**

Yes. The Microsoft 365 admin center discovers only MCP servers registered in a connected AI Gateway or APIM instance.

**Who can grant consent?**

A user assigned the Global Administrator role must complete the consent process.

**Is consent required for each MCP server?**

No. Consent is granted once per tenant and applies to all MCP servers in the connected gateway.

**How long does discovery take?**

MCP servers typically appear within a few minutes. If they don't appear, refresh the **Tools** page and allow more time.

**Can the Microsoft 365 admin center discover MCP servers outside the connected gateway?**

No. Only MCP servers registered in the connected gateway are discovered.

**Are newly registered MCP servers discovered automatically?**

Yes. New MCP servers surface during the gateway discovery and refresh process.
