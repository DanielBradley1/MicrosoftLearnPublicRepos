<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/work-iq/mcp/overview -->
<!-- Sitemap-Last-Modified: 2026-08-21 -->

# Work IQ MCP overview

The Work IQ MCP server exposes Microsoft 365 intelligence capabilities to AI agents through the [Model Context Protocol \(MCP\)](https://modelcontextprotocol.io). It provides a set of generic tools that enable agents to read, create, update, and delete Microsoft 365 entities, invoke Microsoft 365 Copilot for natural-language reasoning, and discover API schemas - all through a single MCP endpoint.

Tip

Explore the Work IQ MCP tools in the [Interactive Demo](https://aka.ms/copilot.dev?page=%2Fwork-iq%2Fmcp&server=workiq-remote). You can inspect tool schemas, load examples, and preview responses in Demo mode.

## Design principles

Work IQ MCP is built on the following design principles:

- **Fewer tools, more paths.** Generic tools operate on resource paths. New workloads add paths, not tools - the tool surface never grows.
- **Introspection over enumeration.** Agents ask for schemas at runtime \(`get_schema`\) rather than loading thousands of type definitions into context.
- **Policy over scopes.** Four broad OAuth permissions gate capability; fine-grained access control is enforced per path, method, and tenant policy.

## Tool categories

The 10 tools are organized into four categories:

| Category | Tools | Description |
| --- | --- | --- |
| Entity tools | `fetch`, `create_entity`, `update_entity`, `delete_entity`, `do_action`, `call_function` | CRUD operations and actions on Microsoft 365 resources |
| Copilot tools | `ask`, `list_agents` | Invoke Microsoft 365 Copilot for natural-language intelligence and discover available agents |
| Schema tools | `get_schema`, `search_paths` | Discover available API paths and retrieve OpenAPI schemas at runtime |

For detailed information about each tool, including parameters, see [Work IQ MCP tool reference](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/work-iq/mcp/tool-reference).

## How tools work

Tools work with **relative resource paths**. The path shows the resource, and the tool acts as the verb:

```text
fetch /me/messages                         → read my emails
do_action /me/sendMail                     → send an email
create_entity /me/events                   → create a calendar event
fetch /me/chats/{id}/messages              → read Teams chat messages
call_function /search/query                → semantic search
ask "What deals closed this quarter?"      → invoke Copilot agent
```

New workloads, backends, and data sources add **paths**, not tools. The tool surface stays fixed at 10.

## Authentication

The Work IQ MCP server uses Microsoft Entra ID for authentication. MCP clients automatically discover the authentication configuration through the `/.well-known/oauth-protected-resource` endpoint. For details on required permissions, see [Work IQ API permissions reference](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/work-iq/permissions).

Note

The Work IQ service principal is created automatically in the tenant when Work IQ is used for the first time. In some corner cases, such as configuring Work IQ MCP policy in the Microsoft 365 admin center before any MCP use in the tenant, the service principal might not exist yet and policy configuration can fail. Tenant administrators can provision it by following the steps in [Enable your tenant for Work IQ](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/work-iq/enable-work-iq).

## Related content

- [Work IQ API overview](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/work-iq/api-overview)
- [Work IQ MCP tool reference](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/work-iq/mcp/tool-reference)
- [Work IQ API permissions reference](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/work-iq/permissions)
