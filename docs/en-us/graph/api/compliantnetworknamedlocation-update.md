<!-- Source: https://learn.microsoft.com/en-us/graph/api/compliantnetworknamedlocation-update?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-12-10 -->

# Update compliantNetworkNamedLocation

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Update the properties of a [compliantNetworkNamedLocation](https://learn.microsoft.com/en-us/graph/api/resources/compliantnetworknamedlocation?view=graph-rest-beta) object.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ✅ | ✅ | ✅ |

## Permissions

One of the following permissions is required to call this API. To learn more, including how to choose permissions, see [Permissions](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Permissions \(from least to most privileged\) |
| :--- | :--- |
| Delegated \(work or school account\) | Policy.Read.All and Policy.ReadWrite.ConditionalAccess |
| Delegated \(personal Microsoft account\) | Not supported. |
| Application | Policy.Read.All and Policy.ReadWrite.ConditionalAccess |

Important

For delegated access using work or school accounts where the signed-in user is acting on another user, they must be assigned a supported [Microsoft Entra role](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=%2Fgraph%2Ftoc.json) or a custom role that grants the permissions required for this operation. This operation supports the following built-in roles, which provide only the least privilege necessary:

- Security Administrator
- Conditional Access Administrator

## HTTP request

```http
PATCH /identity/conditionalAccess/namedLocations/{id}
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |

## Request body

In the request body, supply the values for relevant fields that should be updated. Existing properties that aren't included in the request body maintains their previous values or be recalculated based on changes to other property values. For best performance, don't include existing values that haven't changed.

You must specify the **@odata.type** as `#microsoft.graph.compliantNetworkNamedLocation`.

| Property | Type | Description |
| :--- | :--- | :--- |
| isTrusted | Boolean | The value is `true` if this location is explicitly trusted. |

## Response

If successful, this method returns a `204 No content` response code. It doesn't return anything in the response body.

## Examples

### Request

The following example shows a request.

```http
PATCH https://graph.microsoft.com/beta/compliantNetworkNamedLocation
Content-Type: application/json

{
  "@odata.type": "#microsoft.graph.compliantNetworkNamedLocation",
  "isTrusted": true
}
```

### Response

The following example shows the response.

```http
HTTP/1.1 204 No Content
```
