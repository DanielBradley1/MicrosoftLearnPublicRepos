<!-- Source: https://learn.microsoft.com/en-us/graph/api/networkaccess-threatintelligencepolicy-list-policyrules?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-11-08 -->

# List policyRules for threatIntelligencePolicy

Namespace: microsoft.graph.networkaccess

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Get a list of the [threatIntelligenceRule](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-threatintelligencerule?view=graph-rest-beta) objects associated with a [threatIntelligencePolicy](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-threatintelligencepolicy?view=graph-rest-beta). These rules define the specific conditions and actions for evaluating network traffic against known threat intelligence data.

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permission | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | Not supported. | Not supported. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | Not supported. | Not supported. |

Important

For delegated access using work or school accounts, the signed-in user must be assigned a supported [Microsoft Entra role](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=%2Fgraph%2Ftoc.json) or a custom role that grants the permissions required for this operation. This operation supports the following built-in roles, which provide only the least privilege necessary:

- Global Reader
- Global Secure Access Log Reader
- Global Secure Access Administrator
- Security Administrator

## HTTP request

```http
GET /networkAccess/filteringProfiles/{filteringProfileId}/policies/{policyLinkId}/policyRules
```

## Optional query parameters

This method supports the `$select`, `$top`, `expand`, and `$filter` OData query parameters to help customize the response. For general information, see [OData query parameters](https://learn.microsoft.com/en-us/graph/query-parameters).

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |

## Request body

Don't supply a request body for this method.

## Response

If successful, this method returns a `200 OK` response code and a collection of [policyRule](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-policyrule?view=graph-rest-beta) objects in the response body.

## Examples

### Request

The following example shows a request.

```http
GET https://graph.microsoft.com/beta/networkAccess/filteringProfiles/{filteringProfileId}/policies/{policyLinkId}/policyRules
```

### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "@odata.context": "https://graph.microsoft.com/beta/$metadata#networkAccess/threatIntelligencePolicies('a8352c78-90c6-4edd-aaca-9dc4292e7750')/policyRules",
  "@microsoft.graph.tips": "Use $select to choose only the properties your app needs, as this can lead to performance improvements. For example: GET networkAccess/threatIntelligencePolicies('<guid>')/policyRules?$select=name",
  "value": [
    {
      "@odata.type": "#microsoft.graph.networkaccess.threatIntelligenceRule",
      "id": "eee10b7a-437b-4212-b8c1-38a016ace6da",
      "name": "Rule 1",
      "priority": 100,
      "description": "Rule 1",
      "action": "allow",
      "settings": {
        "status": "enabled"
      },
      "matchingConditions": {
        "severity": "high",
        "destinations": [
          {
            "@odata.type": "#microsoft.graph.networkaccess.threatIntelligenceFqdnDestination",
            "values": [
              "babsite.com",
              "*.verybabwebsite.com"
            ]
          }
        ]
      }
    },
    {
      "@odata.type": "#microsoft.graph.networkaccess.threatIntelligenceRule",
      "id": "e2854585-68ba-4889-868d-45668ff7a295",
      "name": "Default threat intel rule",
      "priority": 65000,
      "description": "Auto-created rule blocking access to sites with high severity threat detected",
      "action": "block",
      "settings": {
        "status": "enabled"
      },
      "matchingConditions": {
        "severity": "high",
        "destinations": [
          {
            "@odata.type": "#microsoft.graph.networkaccess.threatIntelligenceFqdnDestination",
            "values": [
              "*"
            ]
          }
        ]
      }
    }
  ]
}
```
