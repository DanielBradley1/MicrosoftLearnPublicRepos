<!-- Source: https://learn.microsoft.com/en-us/graph/api/security-ediscoverycase-list-legalholds?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-03-21 -->

# List ediscoveryHoldPolicies

Namespace: microsoft.graph.security

Get a list of the [ediscoveryHoldPolicy](https://learn.microsoft.com/en-us/graph/api/resources/security-ediscoveryholdpolicy?view=graph-rest-1.0) objects and their properties.

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

- **eDiscovery Manager**. Allows members to view and access eDiscovery cases they create, including searching and accessing case data. However, eDiscovery Managers can only access and manage the cases they create. **This is the least privileged option for managing their own cases**.
- **eDiscovery Administrator**. Provides all the permissions of eDiscovery Manager, plus the ability to view and access all eDiscovery cases in the organization.

Additional roles that provide read access to eDiscovery cases:

- **Compliance Administrator**. Includes Case Management and Compliance Search permissions.
- **Organization Management**. Includes Case Management and Compliance Search permissions.
- **Reviewer**. Provides read-only access to review sets within eDiscovery cases where the user is a member.

The eDiscovery Manager and eDiscovery Administrator roles are part of the Microsoft Purview role groups and provide access to eDiscovery features through [role-based access control \(RBAC\)](https://learn.microsoft.com/en-us/purview/edisc-permissions#rbac-roles-related-to-ediscovery).

For more information about eDiscovery permissions and roles, see [Assign permissions in eDiscovery](https://learn.microsoft.com/en-us/purview/edisc-permissions).

## HTTP request

```http
GET /security/cases/ediscoveryCases/{ediscoveryCaseId}/legalHolds
```

## Optional query parameters

This method supports some of the OData query parameters to help customize the response. For general information, see [OData query parameters](https://learn.microsoft.com/en-us/graph/query-parameters).

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |

## Request body

Don't supply a request body for this method.

## Response

If successful, this method returns a `200 OK` response code and a collection of [microsoft.graph.security.ediscoveryHoldPolicy](https://learn.microsoft.com/en-us/graph/api/resources/security-ediscoveryholdpolicy?view=graph-rest-1.0) objects in the response body.

## Examples

### Request

The following example shows a request.

```msgraph
GET https://graph.microsoft.com/v1.0/security/cases/ediscoveryCases/b0073e4e-4184-41c6-9eb7-8c8cc3e2288b/legalHolds
```

---

### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
    "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#security/cases/ediscoveryCases('b0073e4e-4184-41c6-9eb7-8c8cc3e2288b')/legalHolds",
    "@odata.count": 2,
    "value": [
        {
            "isEnabled": false,
            "errors": [],
            "contentQuery": "",
            "description": null,
            "createdDateTime": "2022-05-23T01:09:53Z",
            "lastModifiedDateTime": "2022-05-23T02:36:26Z",
            "status": "pending",
            "id": "783c3ea4-d474-4051-9c13-08707ce8c8b6",
            "displayName": "CustodianHold-b0073e4e-4184-41c6-9eb7-8c8cc3e2288b",
            "createdBy": {
                "application": null,
                "user": {
                    "id": "MOD Administrator",
                    "displayName": null
                }
            },
            "lastModifiedBy": {
                "application": null,
                "user": {
                    "id": "MOD Administrator",
                    "displayName": null
                }
            }
        },
        {
            "isEnabled": false,
            "errors": [],
            "contentQuery": "",
            "description": null,
            "createdDateTime": "2022-05-23T02:09:27Z",
            "lastModifiedDateTime": "2022-05-23T02:41:26Z",
            "status": "pending",
            "id": "ff7e8841-b1ac-41f0-87c5-fa00da045ae0",
            "displayName": "NCDSHold-b0073e4e-4184-41c6-9eb7-8c8cc3e2288b",
            "createdBy": {
                "application": null,
                "user": {
                    "id": "MOD Administrator",
                    "displayName": null
                }
            },
            "lastModifiedBy": {
                "application": null,
                "user": {
                    "id": "MOD Administrator",
                    "displayName": null
                }
            }
        }
    ]
}
```
