<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/agent-registration/agentregistration-get -->
<!-- Sitemap-Last-Modified: 2026-04-30 -->

# Get agentRegistration

Important

APIs under the `/beta` version are subject to change. Use of these APIs in production applications is not supported.

Retrieve the properties of an [agentRegistration](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/agent-registration/resources/agentregistration) object.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ❌ | ❌ | ❌ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | AgentRegistration.Read.All | Not available. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | AgentRegistration.Read.All | Not available. |

## HTTP request

```http
GET https://graph.microsoft.com/beta/copilot/agentRegistrations/{id}
```

## Optional query parameters

This method supports the `$select` [OData query parameter](https://learn.microsoft.com/en-us/graph/query-parameters) to help customize the response.

## Request headers

| Name | Description |
| :--- | :--- |
| `Authorization` | `Bearer {token}`. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |

## Request body

Don't supply a request body for this method.

## Response

If successful, this method returns a `200 OK` response code and an [agentRegistration](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/admin-settings/agent-registration/resources/agentregistration) object in the response body.

## Example

### Request

The following example shows a request.

```http
GET https://graph.microsoft.com/beta/copilot/agentRegistrations/550e8400-e29b-41d4-a716-446655440000
```

### Response

The following example shows the response. The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "@odata.context": "https://graph.microsoft.com/beta/$metadata#copilot/agentRegistration/$entity",
  "id": "550e8400-e29b-41d4-a716-446655440000",
  "displayName": "Contoso Travel Booking Agent",
  "description": "Helps users search and book flights and hotels",
  "ownerIds": [
    "3fa85f64-5717-4562-b3fc-2c963f66afa6",
    "8b7e9c42-1234-5678-90ab-def123456789"
  ],
  "createdBy": "3fa85f64-5717-4562-b3fc-2c963f66afa6",
  "sourceCreatedDateTime": "2025-02-15T10:00:00Z",
  "sourceLastModifiedDateTime": "2025-03-10T14:30:00Z",
  "lastPublishedBy": "8b7e9c42-1234-5678-90ab-def123456789",
  "managedByAppId": "7c3f8d45-e29b-41d4-a716-556677889900",
  "sourceAgentId": "contoso-sales-v1",
  "originatingStore": "ContosoAgentStore",
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
