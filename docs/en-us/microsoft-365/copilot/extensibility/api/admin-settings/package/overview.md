<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/package/overview -->
<!-- Sitemap-Last-Modified: 2026-09-28 -->

# Agent 365 Package Management API overview

A package represents an agent in the organization catalog. The Package Management API enables IT administrators to view and manage agents across your organization. This API provides endpoints to list all agents and retrieve detailed information about an individual agent, including metadata and detailed elements.

Important

Access to the Package Management API requires a [Microsoft Agent 365](https://www.microsoft.com/microsoft-agent-365) license.

## Key capabilities

- Retrieve an inventory of all agents within the organization, optionally filtering by:

  - Host \(Copilot, Outlook, Teams\)
  - Platform \(Copilot Studio, Microsoft 365 Copilot Agent Builder\)
  - Last updated time
  - Element types contained in the agent package \(bots, declarative agents, and more\).
  - Request status or request type, to review the agents that users in the organization requested.

- Retrieve more metadata for a specific agent.
- Block, unblock, and reassign ownership of packages.

## Example scenarios

- Organization admin retrieves the inventory of all agents.
- Admin reviews package details, including availability and deployment status.
- Admin reviews the agents that users requested, so that they can triage pending demand.
- Admin reviews agent element details, including declarativeAgent or customEngineAgent element object.
- Admin blocks a package to prevent its usage across the organization.
- Admin reassigns package ownership when an employee leaves the organization.

## API list

| Operation | HTTP Method | Description |
| --- | --- | --- |
| [List packages](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/package/copilotpackages-list) | GET `/copilot/admin/catalog/packages` | Get all agents in the organization. |
| [Get package details](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/package/copilotpackagedetail-get) | GET `/copilot/admin/catalog/packages/{id}` | Get detailed metadata for a specific agent. |
| [Update package](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/package/copilotpackagedetail-update) \(preview\) | PATCH `/copilot/admin/catalog/packages/{id}` | Update package metadata. |
| [Block](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/package/copilotpackage-block) \(preview\) | POST `/copilot/admin/catalog/packages/{id}/block` | Block a package to prevent its usage. |
| [Unblock](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/package/copilotpackage-unblock) \(preview\) | POST `/copilot/admin/catalog/packages/{id}/unblock` | Unblock a package to allow its usage. |
| [Reassign](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/package/copilotpackage-reassign) \(preview\) | POST `/copilot/admin/catalog/packages/{id}/reassign` | Reassign ownership of a package to a different user. |
| [List agent requests](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/package/copilotpackages-list#filter-by-request-properties) | GET `/copilot/admin/catalog/packages` | Get all active agent requests in the organization. |
| [Get agent request details](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/package/copilotpackagedetail-get) | GET `/copilot/admin/catalog/packages/{id}` | Get detailed metadata for a specific agent request. |

## Resources

- [copilotPackage resource](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/package/resources/copilotpackage)
- [copilotPackageDetail resource](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/package/resources/copilotpackagedetail)

## Related content

- [Microsoft 365 app manifest schema reference](https://learn.microsoft.com/en-us/microsoft-365/extensibility/schema)
