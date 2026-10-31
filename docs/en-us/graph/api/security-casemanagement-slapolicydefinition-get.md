<!-- Source: https://learn.microsoft.com/en-us/graph/api/security-casemanagement-slapolicydefinition-get?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-10-28 -->

# Get slaPolicyDefinition

Namespace: microsoft.graph.security.caseManagement

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Get an [slaPolicyDefinition](https://learn.microsoft.com/en-us/graph/api/resources/security-casemanagement-slapolicydefinition?view=graph-rest-beta), including its criteria and timers.

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | CaseManagement.Read.All | CaseManagement.ReadWrite.All |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | CaseManagement.Read.All | CaseManagement.ReadWrite.All |

Important

For delegated access using work or school accounts, the signed-in user must be assigned a supported built-in [Microsoft Entra role](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=%2Fgraph%2Ftoc.json), in addition to the required Microsoft Graph permission. The following built-in roles are supported, listed from least to most privileged:

- Security Reader
- Security Administrator

**Security Reader** is the least privileged role supported for this operation.

## HTTP request

```http
GET /security/caseManagement/caseTypeConfigurations/{caseTypeConfiguration-id}/slaPolicies/{slaPolicyDefinition-id}
```

Replace `{caseTypeConfiguration-id}` with the owning case type: `incidentCase`, `genericCase`, or `exposureCase`.

## Optional query parameters

This method supports the `$select` OData query parameter to select which properties are returned. For general information, see [OData query parameters](https://learn.microsoft.com/en-us/graph/query-parameters).

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |

## Request body

Don't supply a request body for this method.

## Response

If successful, this method returns a `200 OK` response code and a [slaPolicyDefinition](https://learn.microsoft.com/en-us/graph/api/resources/security-casemanagement-slapolicydefinition?view=graph-rest-beta) object in the response body.

The full resource is returned unless `$select` is used. If the policy doesn't exist, this method returns `404 Not Found`.

Response payloads can omit `@odata.type` on non-polymorphic objects.

## Examples

#### Request

The following example shows a request.

```http
GET https://graph.microsoft.com/beta/security/caseManagement/caseTypeConfigurations/incidentCase/slaPolicies/8f3b6c2e-2f2a-4b8e-9a1e-2f1c4d5a6b7c
```

#### Response

The following example shows the response.

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "@odata.context": "https://graph.microsoft.com/beta/$metadata#security/caseManagement/caseTypeConfigurations/incidentCase/slaPolicies/$entity",
  "@odata.type": "#microsoft.graph.security.caseManagement.slaPolicyDefinition",
  "id": "8f3b6c2e-2f2a-4b8e-9a1e-2f1c4d5a6b7c",
  "displayName": "High priority incident response",
  "description": "Tracks time-to-resolution for high priority incident cases.",
  "setCriteria": {
    "@odata.type": "#microsoft.graph.security.caseManagement.slaPolicyCriteriaBlock",
    "logicalOperator": "and",
    "conditions": [
      {
        "@odata.type": "#microsoft.graph.security.caseManagement.slaPolicyCondition",
        "property": "priority",
        "operator": "equals",
        "values": ["High"]
      }
    ]
  },
  "exitCriteria": {
    "@odata.type": "#microsoft.graph.security.caseManagement.slaPolicyCriteriaBlock",
    "logicalOperator": "or",
    "conditions": [
      {
        "@odata.type": "#microsoft.graph.security.caseManagement.slaPolicyCondition",
        "property": "status",
        "operator": "equals",
        "values": ["Closed"]
      }
    ]
  },
  "pauseCriteria": null,
  "recalculateCondition": {
    "@odata.type": "#microsoft.graph.security.caseManagement.slaPolicyRecalculateCondition",
    "shouldResetTime": false
  },
  "isActive": true,
  "timers": [
    {
      "policyTimerId": "b1a2c3d4-5e6f-4a7b-8c9d-0e1f2a3b4c5d",
      "order": 0,
      "isDefault": true,
      "warningThresholdInMinutes": 240,
      "breachThresholdInMinutes": 480
    }
  ],
  "createdDateTime": "2026-08-17T08:15:00Z",
  "createdBy": "8b2e1f6a-51ce-4a53-bd08-ec42a3b768e1",
  "lastModifiedDateTime": "2026-08-17T08:15:00Z",
  "lastModifiedBy": "8b2e1f6a-51ce-4a53-bd08-ec42a3b768e1"
}
```
