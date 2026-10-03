<!-- Source: https://learn.microsoft.com/en-us/graph/api/tenantgovernanceservices-governancepolicytemplate-update?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-09-25 -->

# Update tenantGovernancePolicyTemplate

Namespace: microsoft.graph

Update the properties of a [tenantGovernancePolicyTemplate](https://learn.microsoft.com/en-us/graph/api/resources/tenantgovernanceservices-tenantgovernancepolicytemplate?view=graph-rest-1.0) object.

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | TenantGovernance-PolicyTemplate.ReadWrite.All | Not available. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | Not supported. | Not supported. |

Important

For delegated access using work or school accounts, the signed-in user must be assigned a supported [Microsoft Entra role](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=%2Fgraph%2Ftoc.json). The following least privileged roles are supported for this operation.

- Tenant Governance Administrator
- Tenant Governance Relationship Administrator

## HTTP request

```http
PATCH /directory/tenantGovernance/governancePolicyTemplates/{governancePolicyTemplateId}
PATCH /directory/tenantGovernance/governancePolicyTemplates/default
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |

## Request body

In the request body, supply *only* the values for properties to update. Existing properties that aren't included in the request body maintain their previous values or are recalculated based on changes to other property values.

The following table specifies the properties that can be updated.

| Property | Type | Description |
| :--- | :--- | :--- |
| displayName | String | The display name of the policy template. |
| description | String | A description of the policy template. |
| multiTenantApplicationsToProvision | [microsoft.graph.multiTenantApplicationsToProvision](https://learn.microsoft.com/en-us/graph/api/resources/tenantgovernanceservices-multitenantapplicationstoprovision?view=graph-rest-1.0) collection | A collection of multitenant applications to be provisioned in the governed tenant when the governance relationship is established. |
| delegatedAdministrationRoleAssignments | [microsoft.graph.delegatedAdministrationRoleAssignment](https://learn.microsoft.com/en-us/graph/api/resources/tenantgovernanceservices-delegatedadministrationroleassignment?view=graph-rest-1.0) collection | A collection of delegated administration role assignments to be applied in the governed tenant when the governance relationship is established. |

## Response

If successful, this method returns a `200 OK` response code and an updated [microsoft.graph.tenantGovernancePolicyTemplate](https://learn.microsoft.com/en-us/graph/api/resources/tenantgovernanceservices-tenantgovernancepolicytemplate?view=graph-rest-1.0) object in the response body.

## Examples

### Example 1: Update a custom governance policy template

#### Request

The following example shows a request.

```http
PATCH https://graph.microsoft.com/v1.0/directory/tenantGovernance/governancePolicyTemplates/aaaaaaaa-0000-1111-2222-bbbbbbbbbbbb
Content-Type: application/json

{
  "multiTenantApplicationsToProvision": [
    {
        "appId": "66667777-aaaa-8888-bbbb-9999cccc0000",
        "objectId": "cccccccc-2222-3333-4444-dddddddddddd",
        "displayName": "Mega Monitor",
        "requiredResourceAccesses": [
            {
              "resourceAppId": "00000003-0000-0000-c000-000000000000",
              "permissions": [
              {
                "id": "633e0fce-8c58-4cfb-9495-12bbd5a24f7c",
                "name": "Policy.Read.ConditionalAccess",
                "type": "scope"
              },
              {
                "id": "e1fe6dd8-ba31-4d61-89e7-88639da4683d",
                "name": "User.Read",
                "type": "scope"
              }
              ]
            }
        ]
    }
  ],
  "delegatedAdministrationRoleAssignments": [
    {
        "roleTemplates": [
            {
                "id": "f2ef992c-3afb-46b9-b7cf-a126ee74c451",
                "name": "Global Reader"
            }
        ],
        "group": {
            "id": "ffffffff-5555-6666-7777-aaaaaaaaaaaa"
        }
    }
  ]
}
```

#### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "@odata.type": "#microsoft.graph.tenantGovernancePolicyTemplate",
  "id": "aaaaaaaa-0000-1111-2222-bbbbbbbbbbbb",
  "displayName": "Monitor Entra resource configurations",
  "description": "Grants Global reader and provisions a custom multi-tenant application to monitor conditional access policies",
  "createdDateTime": "2026-03-06T22:29:00.2110638Z",
  "lastModifiedDateTime": "2026-03-06T22:29:00.2110638Z",
  "version": "1.0",
  "multiTenantApplicationsToProvision": [
    {
        "appId": "66667777-aaaa-8888-bbbb-9999cccc0000",
        "objectId": "cccccccc-2222-3333-4444-dddddddddddd",
        "displayName": "Mega Monitor",
        "requiredResourceAccesses": [
            {
              "resourceAppId": "00000003-0000-0000-c000-000000000000",
              "permissions": [
              {
                "id": "633e0fce-8c58-4cfb-9495-12bbd5a24f7c",
                "name": "Policy.Read.ConditionalAccess",
                "type": "scope"
              },
              {
                "id": "e1fe6dd8-ba31-4d61-89e7-88639da4683d",
                "name": "User.Read",
                "type": "scope"
              }
              ]
            }
        ]
    }
  ],
  "delegatedAdministrationRoleAssignments": [
    {
        "roleTemplates": [
            {
                "id": "f2ef992c-3afb-46b9-b7cf-a126ee74c451",
                "name": "Global Reader"
            }
        ],
        "group": {
            "id": "ffffffff-5555-6666-7777-aaaaaaaaaaaa"
        }
    }
  ]
}
```

### Example 2: Update the default governance policy template

#### Request

The following example shows a request.

```http
PATCH https://graph.microsoft.com/v1.0/directory/tenantGovernance/governancePolicyTemplates/default
Content-Type: application/json

{
  "multiTenantApplicationsToProvision": [
    {
        "appId": "66667777-aaaa-8888-bbbb-9999cccc0000",
        "objectId": "cccccccc-2222-3333-4444-dddddddddddd",
        "displayName": "Mega Monitor",
        "requiredResourceAccesses": [
            {
              "resourceAppId": "00000003-0000-0000-c000-000000000000",
              "permissions": [
              {
                "id": "633e0fce-8c58-4cfb-9495-12bbd5a24f7c",
                "name": "Policy.Read.ConditionalAccess",
                "type": "scope"
              },
              {
                "id": "e1fe6dd8-ba31-4d61-89e7-88639da4683d",
                "name": "User.Read",
                "type": "scope"
              }
              ]
            }
        ]
    }
  ],
  "delegatedAdministrationRoleAssignments": [
    {
        "roleTemplates": [
            {
                "id": "f2ef992c-3afb-46b9-b7cf-a126ee74c451",
                "name": "Global Reader"
            }
        ],
        "group": {
            "id": "ffffffff-5555-6666-7777-aaaaaaaaaaaa"
        }
    }
  ]
}
```

#### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "@odata.type": "#microsoft.graph.tenantGovernancePolicyTemplate",
  "id": "default",
  "displayName": "Default Policy Template",
  "description": "The system-provided default governance policy template",
  "version": "1.0",
  "createdDateTime": "2026-03-06T22:29:00.2110638Z",
  "lastModifiedDateTime": "2026-03-06T22:29:00.2110638Z",
  "multiTenantApplicationsToProvision": [
    {
        "appId": "66667777-aaaa-8888-bbbb-9999cccc0000",
        "objectId": "cccccccc-2222-3333-4444-dddddddddddd",
        "displayName": "Mega Monitor",
        "requiredResourceAccesses": [
            {
              "resourceAppId": "00000003-0000-0000-c000-000000000000",
              "permissions": [
              {
                "id": "633e0fce-8c58-4cfb-9495-12bbd5a24f7c",
                "name": "Policy.Read.ConditionalAccess",
                "type": "scope"
              },
              {
                "id": "e1fe6dd8-ba31-4d61-89e7-88639da4683d",
                "name": "User.Read",
                "type": "scope"
              }
              ]
            }
        ]
    }
  ],
  "delegatedAdministrationRoleAssignments": [
    {
        "roleTemplates": [
            {
                "id": "f2ef992c-3afb-46b9-b7cf-a126ee74c451",
                "name": "Global Reader"
            }
        ],
        "group": {
            "id": "ffffffff-5555-6666-7777-aaaaaaaaaaaa"
        }
    }
  ]
}
```
