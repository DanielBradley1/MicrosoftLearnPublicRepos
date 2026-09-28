<!-- Source: https://learn.microsoft.com/en-us/graph/api/security-ediscoveryholdpolicy-delete-sitesources?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-02-26 -->

# Delete siteSource

Namespace: microsoft.graph.security

Delete a [siteSource](https://learn.microsoft.com/en-us/graph/api/resources/security-sitesource?view=graph-rest-1.0) object associated with an [ediscoveryHoldPolicy](https://learn.microsoft.com/en-us/graph/api/resources/security-ediscoveryholdpolicy?view=graph-rest-1.0).

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ✅ | ✅ | ❌ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | eDiscovery.Read.All | eDiscovery.ReadWrite.All |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | eDiscovery.Read.All | eDiscovery.ReadWrite.All |

Important

For delegated access using work or school accounts, the signed-in user must be assigned a supported [Microsoft Purview role](https://learn.microsoft.com/en-us/purview/edisc-permissions) through one of the following options:

- **eDiscovery Manager**. Allows members to create and manage eDiscovery cases they create, including creating custodians, holds, searches, and other case management tasks. However, eDiscovery Managers can only create and manage the cases they create. **This is the least privileged option for managing their own cases**.
- **eDiscovery Administrator**. Provides all the permissions of eDiscovery Manager, plus the ability to access and manage all eDiscovery cases in the organization, configure eDiscovery settings, and manage any case after adding themselves as a member.

Additional roles that provide write access to eDiscovery features:

- **Compliance Administrator**. Includes Case Management, Compliance Search, and Hold permissions.
- **Organization Management**. Includes Case Management, Compliance Search, Hold, and Search And Purge permissions.

The eDiscovery Manager and eDiscovery Administrator roles are part of the Microsoft Purview role groups and provide access to eDiscovery features through [role-based access control \(RBAC\)](https://learn.microsoft.com/en-us/purview/edisc-permissions#rbac-roles-related-to-ediscovery).

For more information about eDiscovery permissions and roles, see [Assign permissions in eDiscovery](https://learn.microsoft.com/en-us/purview/edisc-permissions).

## HTTP request

```http
DELETE /security/cases/ediscoveryCases/{ediscoveryCaseId}/legalHolds/{ediscoveryHoldPolicyId}/siteSources/{siteSourceId}
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

```http
DELETE https://graph.microsoft.com/v1.0/security/cases/ediscoveryCases/4c551bc5-f6f8-435c-8391-d1a08f1ffd5b/legalHolds/2114ada2-3958-4945-bb6e-66fe9fca4772/siteSources/08345ae2-bc5a-4d71-a18b-c490993959ee
```

### Response

The following example shows the response.

```http
HTTP/1.1 204 No Content
```
