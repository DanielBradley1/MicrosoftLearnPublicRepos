<!-- Source: https://learn.microsoft.com/en-us/graph/api/agentcollection-list-members?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-04-28 -->

# List agentCollection members

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Important

**Upcoming change to Agent Registry APIs**

Starting May 2026, the Agent Registry APIs in Microsoft Graph will be replaced by the [Agent Registry APIs powered by Microsoft Agent 365](https://learn.microsoft.com/en-us/microsoft-agent-365/admin/graph-api). This change consolidates agent management experiences to make it easier to observe, govern, and secure all agents in your tenant. We recommend that you plan to migrate to the new Agent 365-based APIs when they are released. Learn more about [Agent Registry convergence with Microsoft Agent 365](https://learn.microsoft.com/en-us/entra/agent-id/agent-registry-convergence).

Return the list of [agent instances](https://learn.microsoft.com/en-us/graph/api/resources/agentinstance?view=graph-rest-beta) that are members for the specified [agentCollection](https://learn.microsoft.com/en-us/graph/api/resources/agentcollection?view=graph-rest-beta). This API returns only the **agentCollection** and doesn't support using $select to return other properties. Attempting to select more properties returns a `400 Bad Request` error code.

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permission | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | AgentCollection.Read.All | AgentCollection.ReadWrite.All |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | AgentCollection.Read.All | AgentCollection.ReadWrite.All, AgentCollection.ReadWrite.ManagedBy |

Important

In addition to the permissions listed in the preceding table, the following lesser-privileged permissions scoped to the special collections are supported for this API:

- *AgentCollection.Read.Global* and *AgentCollection.ReadWrite.Global* for the **Global** collection
- *AgentCollection.Read.Quarantined* and *AgentCollection.ReadWrite.Quarantined* for the **Quarantined** collection

Important

When using delegated permissions, the authenticated user must be assigned a supported [Microsoft Entra role](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=%2Fgraph%2Ftoc.json) or a custom role that grants the permissions required for this operation.

*Agent Registry Administrator* is the least privileged role supported for this operation.

## HTTP request

```http
GET /agentRegistry/agentInstances/{agentInstanceId}/collections/{agentCollectionId}/members
```

## Optional query parameters

This method supports the `$select` and `$count` OData query parameters to help customize the response. For general information, see [OData query parameters](https://learn.microsoft.com/en-us/graph/query-parameters).

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |

## Request body

Don't supply a request body for this method.

## Response

If successful, this method returns a `200 OK` response code and a collection of [agentInstance](https://learn.microsoft.com/en-us/graph/api/resources/agentinstance?view=graph-rest-beta) objects in the response body.

## Examples

### Request

The following example shows a request.

- [HTTP](#tabpanel_1_http)
- [JavaScript](#tabpanel_1_javascript)

```http
GET https://graph.microsoft.com/beta/agentRegistry/agentInstances/{agentInstanceId}/collections/{agentCollectionId}/members
```

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

let members = await client.api('/agentRegistry/agentInstances/{agentInstanceId}/collections/{agentCollectionId}/members')
	.version('beta')
	.get();
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

The following example shows the response.

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "value": [
    {
      "id": "Security Copilot Platform Agent: 00123",
      "managedBy": "719cc904-9700-4e08-9941-fd826cc84c60",
      "originatingStore": "Microsoft Security Copilot",
      "displayName": "Conditional Access Agent",
      "agentIdentityBlueprintId": "cc08c41-d2d2-4e78-b073-92f57b752bd0",
      "agentIdentityId": "cd108c41-d2d2-4e78-b073-92f57b752bd0",
      "agentUserId": null
    },
    {
      "id": "Security Copilot Platform Agent: 00222",
      "managedBy": "719cc904-9700-4e08-9941-fd826cc84c60",
      "originatingStore": "Microsoft Security Copilot",
      "displayName": "Conditional Access Agent",
      "agentIdentityBlueprintId": "ab108c41-d2d2-4e78-b073-92f57b752bd0",
      "agentIdentityId": "ac108c41-d2d2-4e78-b073-92f57b752bd0",
      "agentUserId": null
    }
  ]
}
```
