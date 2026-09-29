<!-- Source: https://learn.microsoft.com/en-us/graph/api/tenantgovernanceservices-governancerelationship-update?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-09-25 -->

# Update governanceRelationship

Namespace: microsoft.graph

Update the **status** property of a [governanceRelationship](https://learn.microsoft.com/en-us/graph/api/resources/tenantgovernanceservices-governancerelationship?view=graph-rest-1.0) to initiate the termination process. There are two models for termination:

1. Initiated by the governing tenant: After the governing tenant updates the `status` to `terminationRequestedByGoverningTenant`, the governed tenant may subsequently update the `status` to `terminated`.
2. Directly terminated by the governed tenant: The governed tenant updates the `status` to `terminated` to immediately terminate the relationship.

When the governed tenant updates the `status` to `terminated` in either model, the resources that were provisioned in the governed tenant upon relationship creation are deleted.

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | TenantGovernance-Relationship.ReadWrite.All | Not available. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | Not supported. | Not supported. |

Important

For delegated access using work or school accounts, the signed-in user must be assigned a supported [Microsoft Entra role](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=%2Fgraph%2Ftoc.json). The following least privileged roles are supported for this operation.

- Tenant Governance Administrator
- Tenant Governance Relationship Administrator

## HTTP request

```http
PATCH /directory/tenantGovernance/governanceRelationships/{governanceRelationshipId}
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
| status | microsoft.graph.relationshipStatus | The current status of the governance relationship. The possible values are: `active`, `terminated`, `terminationRequestedByGoverningTenant`, `unknownFutureValue`. Required. |

## Response

If successful, this method returns a `200 OK` response code and an updated [microsoft.graph.governanceRelationship](https://learn.microsoft.com/en-us/graph/api/resources/tenantgovernanceservices-governancerelationship?view=graph-rest-1.0) object in the response body.

## Examples

### Request

The following example shows a request.

```http
PATCH https://graph.microsoft.com/v1.0/directory/tenantGovernance/governanceRelationships/aaaaaaaa-0000-1111-2222-bbbbbbbbbbbb
Content-Type: application/json

{
  "status": "terminated"
}
```

### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "@odata.type": "#microsoft.graph.governanceRelationship",
  "id": "aaaaaaaa-0000-1111-2222-bbbbbbbbbbbb",
  "status": "terminated",
  "governingTenantId": "aaaabbbb-0000-cccc-1111-dddd2222eeee",
  "governedTenantId": "bbbbcccc-1111-dddd-2222-eeee3333ffff",
  "governingTenantName": "Contoso, Inc",
  "governedTenantName": "Fabrikam",
  "policySnapshot": {
      "policyId": "d3d3d3d3-eeee-ffff-aaaa-b4b4b4b4b4b4",
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
  },
  "createdType": "approvedByAdmin",
  "creationDateTime": "2025-09-11T17:07:41.2019694Z"
}
```
