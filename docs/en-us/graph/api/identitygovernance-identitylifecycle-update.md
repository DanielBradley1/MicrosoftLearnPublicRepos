<!-- Source: https://learn.microsoft.com/en-us/graph/api/identitygovernance-identitylifecycle-update?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-10-07 -->

# Update identityLifecycle

Namespace: microsoft.graph.identityGovernance

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Update the properties of an [identityLifecycle](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-identitylifecycle?view=graph-rest-beta) object for a [servicePrincipal](https://learn.microsoft.com/en-us/graph/api/resources/serviceprincipal?view=graph-rest-beta).

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permission | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | Not supported. | Not supported. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | Not supported. | Not supported. |

## HTTP request

```http
PATCH /servicePrincipals/{servicePrincipalsId}/lifecycle
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |

## Request body

In the request body, supply *only* the values for properties to update. Existing properties that aren't included in the request body maintain their previous values or are recalculated based on changes to other property values.

The following table specifies the properties that can be updated.

You must specify the `@odata.type` property when updating an [identityLifecycle](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-identitylifecycle?view=graph-rest-beta) object. For example, to update an [agentIdentityLifecycle](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-agentidentitylifecycle?view=graph-rest-beta) object, set `@odata.type` to `#microsoft.graph.identityGovernance.agentIdentityLifecycle`.

| Property | Type | Description |
| :--- | :--- | :--- |
| lastAttestationDateTime | DateTimeOffset | The date and time when the identity was last attested. Nullable. |

## Response

If successful, this method returns a `204 No Content` response code.

## Examples

### Request

The following example shows a request.

```http
PATCH https://graph.microsoft.com/beta/servicePrincipals/55bc54bb-f5ef-431b-9e8f-6ee6320191fe/lifecycle
Content-Type: application/json

{
  "@odata.type": "#microsoft.graph.identityGovernance.agentIdentityLifecycle",
  "lastAttestationDateTime": "2026-07-15T09:30:00Z"
}
```

### Response

The following example shows the response.

```http
HTTP/1.1 204 No Content
```
