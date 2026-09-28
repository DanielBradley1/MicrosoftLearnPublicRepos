<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/agent-registration/agentregistration-create -->
<!-- Sitemap-Last-Modified: 2026-04-30 -->

# Create agentRegistration

Important

APIs under the `/beta` version are subject to change. Use of these APIs in production applications is not supported.

Create a new [agentRegistration](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/agent-registration/resources/agentregistration) object.

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
POST https://graph.microsoft.com/beta/copilot/agentRegistrations
```

## Request headers

| Name | Description |
| :--- | :--- |
| `Authorization` | `Bearer {token}`. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| `Content-Type` | `application/json`. Required. |

## Request body

In the request body, supply a JSON representation of an [agentRegistration](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/agent-registration/resources/agentregistration) object.

The following table lists the required properties when you create an agentRegistration.

| Property | Type | Description |
| :--- | :--- | :--- |
| `displayName` | String | Display name for the agent instance. Required. |
| `createdBy` | String | The unique identifier of the user or app who created the agent registration. Required. |
| `sourceCreatedDateTime` | DateTimeOffset | The date and time when the agent instance was created from source. Required. |
| `sourceLastModifiedDateTime` | DateTimeOffset | The date and time when the agent instance was last modified from source. Required. |

## Response

If successful, this method returns a `201 Created` response code and an [agentRegistration](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/agent-registration/resources/agentregistration) object in the response body.

## Example

### Request

The following example shows a request.

```http
POST https://graph.microsoft.com/beta/copilot/agentRegistrations
Content-Type: application/json

{
  "displayName": "Contoso Travel Booking Agent",
  "description": "Helps users search and book flights and hotels",
  "ownerIds": [
    "3fa85f64-5717-4562-b3fc-2c963f66afa6",
    "8b7e9c42-1234-5678-90ab-def123456789"
  ],
  "sourceAgentId": "contoso-sales-assistant-v1",
  "originatingStore": "ContosoAgentStore",
  "managedByAppId": "7c3f8d45-e29b-41d4-a716-556677889900",
  "agentIdentityId": "identity-550e8400-e29b-41d4-a716-446655440000",
  "agentIdentityBlueprintId": "blueprint-550e8400-e29b-41d4-a716-446655440000",
  "agentCard": {
    "name": "Contoso Travel Booking Agent",
    "version": "1.0.0",
    "description": "Helps users search and book flights and hotels",
    "provider": "Contoso",
    "capabilities": {
      "streaming": false,
      "pushNotifications": false
    },
    "defaultInputModes": ["text"],
    "defaultOutputModes": ["text"],
    "skills": [
      {
        "id": "book-flight",
        "name": "Book Flight",
        "description": "Search and book flights based on user preferences"
      },
      {
        "id": "book-hotel",
        "name": "Book Hotel",
        "description": "Search and book hotels at the destination"
      }
    ]
  }
}
```

### Response

The following example shows the response.

```http
HTTP/1.1 201 Created
Content-Type: application/json

{
  "@odata.context": "https://graph.microsoft.com/beta/$metadata#copilot/agentRegistrations/$entity",
  "id": "550e8400-e29b-41d4-a716-446655440000"
}
```
