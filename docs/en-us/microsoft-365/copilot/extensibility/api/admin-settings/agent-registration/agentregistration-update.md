<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/agent-registration/agentregistration-update -->
<!-- Sitemap-Last-Modified: 2026-04-30 -->

# Update agentRegistration

Important

APIs under the `/beta` version are subject to change. Use of these APIs in production applications is not supported.

Update an [agentRegistration](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/agent-registration/resources/agentregistration) object.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ❌ | ❌ | ❌ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | AgentRegistration.ReadWrite.All | Not available. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | AgentRegistration.ReadWrite.All | Not available. |

## HTTP request

```http
PATCH https://graph.microsoft.com/beta/copilot/agentRegistrations/{id}
```

## Request headers

| Name | Description |
| :--- | :--- |
| `Authorization` | `Bearer {token}`. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| `Content-Type` | `application/json`. Required. |

## Request body

In the request body, supply a JSON representation of the properties to update on the [agentRegistration](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/agent-registration/resources/agentregistration) object.

| Property | Type | Description |
| :--- | :--- | :--- |
| `agentCard` | [Json](https://learn.microsoft.com/en-us/graph/api/resources/json) | Flexible JSON manifest containing agent card information. Optional. |
| `agentIdentityBlueprintId` | String | Agent identity blueprint identifier. Optional. |
| `agentIdentityId` | String | Entra agent identity identifier. Optional. |
| `description` | String | The agent description. Optional. |
| `displayName` | String | Display name for the agent instance. Optional. |
| `lastPublishedBy` | String | The unique identifier of the last person to publish the agent. Optional. |
| `managedByAppId` | String | Application identifier managing this agent. Optional. |
| `originatingStore` | String | Name of the store or system where the agent originated. Optional. |
| `ownerIds` | String collection | List of owner identifiers for the agent. Optional. |
| `sourceAgentId` | String | Original agent identifier from source system. Optional. |
| `sourceLastModifiedDateTime` | DateTimeOffset | The date and time when the agent instance was last modified from source. Optional. |

## Response

If successful, this method returns a `200 OK` response code. It doesn't return anything in the response body.

## Example

### Request

The following example shows a request.

```http
PATCH https://graph.microsoft.com/beta/copilot/agentRegistrations/550e8400-e29b-41d4-a716-446655440000
Content-Type: application/json

{
  "displayName": "Contoso Sales Assistant",
  "description": "AI-powered sales assistant that integrates with Contoso CRM",
  "ownerIds": [
    "3fa85f64-5717-4562-b3fc-2c963f66afa6"
  ]
}
```

### Response

The following example shows the response.

```http
HTTP/1.1 200 OK
```
