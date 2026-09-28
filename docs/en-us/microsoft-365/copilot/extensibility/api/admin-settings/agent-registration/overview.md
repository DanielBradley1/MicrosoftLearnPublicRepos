<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/agent-registration/overview -->
<!-- Sitemap-Last-Modified: 2026-04-30 -->

# Agent Registration API overview \(preview\)

Important

APIs under the `/beta` version are subject to change. Use of these APIs in production applications is not supported.

The Agent Registration API enables developers and administrators to programmatically register and manage agents within their Microsoft 365 environment. The API allows users to create agent registrations with associated metadata and an agent card. Developers can manage agent lifecycle operations such as creating new registrations, updating configurations, retrieving registration details, and deleting registrations as needed.

## Key capabilities

- Create agent registrations with metadata and agent card manifests.
- Retrieve full details of an agent registration by ID.
- Update specific properties of an existing agent registration.
- Delete agent registrations that are no longer needed.

## Example scenarios

- A developer at Contoso wants to register a custom Sales Assistant agent that integrates with their CRM system. Using the Agent Registration API, they can create a registration with the agent's metadata, provide an agent card, and set owner permissions.
- An administrator retrieves the details of an existing agent registration to review its configuration and agent card.
- A developer updates the display name and description of an existing agent registration after a product rename.
- An administrator deletes an outdated agent registration that is no longer in use.

## API list

| Operation | HTTP method | Description |
| :--- | :--- | :--- |
| [Create agentRegistration](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/agent-registration/agentregistration-create) | POST `/copilot/agentRegistrations` | Create a new agent registration. |
| [Get agentRegistration](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/agent-registration/agentregistration-get) | GET `/copilot/agentRegistrations/{id}` | Get details of a specific agent registration. |
| [Update agentRegistration](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/agent-registration/agentregistration-update) | PATCH `/copilot/agentRegistrations/{id}` | Update an existing agent registration. |
| [Delete agentRegistration](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/agent-registration/agentregistration-delete) | DELETE `/copilot/agentRegistrations/{id}` | Delete an agent registration. |

## Resources

- [agentRegistration resource](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/agent-registration/resources/agentregistration)
