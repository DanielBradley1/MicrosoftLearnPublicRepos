<!-- Source: https://learn.microsoft.com/en-us/graph/api/agenticsecurityroot-list-playbookdefinitions?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-11-13 -->

# List playbookDefinitions

Namespace: microsoft.graph

List the read-only playbook catalog available to the signed-in user. This operation uses the [playbookDefinition](https://learn.microsoft.com/en-us/graph/api/resources/playbookdefinition?view=graph-rest-beta) resource.

## API availability

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ❌ | ❌ | ❌ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | Perception.Read.All | Perception.Manage.All |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | Perception.Read.All | Perception.Manage.All |

The signed-in user must have access to the requested resources. Granting an OAuth permission does not override the service's access controls.

## HTTP request

```http
GET /security/agenticSecurity/playbookDefinitions
```

## Optional query parameters

This method supports the `$select` OData query parameter. Other query parameters aren't supported. When the response contains `@odata.nextLink`, follow that complete URL to retrieve the next page.

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |

## Request body

Don't supply a request body for this method.

## Response

If successful, this method returns a `200 OK` response code and a collection of [playbookDefinition](https://learn.microsoft.com/en-us/graph/api/resources/playbookdefinition?view=graph-rest-beta) objects in the response body.

## Examples

### Request

```http
GET https://graph.microsoft.com/beta/security/agenticSecurity/playbookDefinitions
```

### Response

The following example shows one playbook from the response.

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "value": [
    {
      "id": "732b84ae-26ad-4eb4-b4fb-f2f45d7571e6",
      "uniqueName": "investigate-incident",
      "displayName": "Investigate attack",
      "description": "Prepare a detailed report about an attack. This playbook outlines the full attack story, providing timelines, attack techniques, indicators, and affected assets.",
      "acceptedInputTypes": [
        "defenderIncidentId",
        "defenderAlertId"
      ]
    }
  ]
}
```
