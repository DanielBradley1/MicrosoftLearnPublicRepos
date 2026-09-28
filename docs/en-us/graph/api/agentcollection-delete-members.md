<!-- Source: https://learn.microsoft.com/en-us/graph/api/agentcollection-delete-members?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-04-28 -->

# Remove agentInstance from agentCollection

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Important

**Upcoming change to Agent Registry APIs**

Starting May 2026, the Agent Registry APIs in Microsoft Graph will be replaced by the [Agent Registry APIs powered by Microsoft Agent 365](https://learn.microsoft.com/en-us/microsoft-agent-365/admin/graph-api). This change consolidates agent management experiences to make it easier to observe, govern, and secure all agents in your tenant. We recommend that you plan to migrate to the new Agent 365-based APIs when they are released. Learn more about [Agent Registry convergence with Microsoft Agent 365](https://learn.microsoft.com/en-us/entra/agent-id/agent-registry-convergence).

Remove an [agentInstance](https://learn.microsoft.com/en-us/graph/api/resources/agentinstance?view=graph-rest-beta) object from an [agentCollection](https://learn.microsoft.com/en-us/graph/api/resources/agentcollection?view=graph-rest-beta).

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permission | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | AgentCollection.ReadWrite.All | AgentCollection.ReadWrite.All |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | AgentCollection.ReadWrite.ManagedBy | AgentCollection.ReadWrite.All |

Important

In addition to the permissions listed in the preceding table, the following lesser-privileged delegated and application permissions scoped to the special collections are supported for this API:

- *AgentCollection.ReadWrite.Global* for **Global** collection
- *AgentCollection.ReadWrite.Quarantined* for **Quarantined** collection

Important

When using delegated permissions, the authenticated user must be assigned a supported [Microsoft Entra role](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=%2Fgraph%2Ftoc.json) or a custom role that grants the permissions required for this operation.

*Agent Registry Administrator* is the least privileged role supported for this operation.

## HTTP request

```http
DELETE /agentRegistry/agentInstances/{agentInstanceId}/collections/{agentCollectionId}/members/{id}/$ref
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |

## Request body

Don't supply a request body for this method.

## Response

If successful, this method returns a `204 No Content` response code.

## Examples

### Request

The following example shows a request.

- [HTTP](#tabpanel_1_http)
- [JavaScript](#tabpanel_1_javascript)

```http
DELETE https://graph.microsoft.com/beta/agentRegistry/agentInstances/{agentInstanceId}/collections/{agentCollectionId}/members/{id}/$ref
```

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

await client.api('/agentRegistry/agentInstances/{agentInstanceId}/collections/{agentCollectionId}/members/{id}/$ref')
	.version('beta')
	.delete();
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

The following example shows the response.

```http
HTTP/1.1 204 No Content
```
