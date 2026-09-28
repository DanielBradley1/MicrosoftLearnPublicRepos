<!-- Source: https://learn.microsoft.com/en-us/graph/api/networkaccess-threatintelligencerule-update?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-11-08 -->

# Update threatIntelligenceRule

Namespace: microsoft.graph.networkaccess

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Update the properties of a threatIntelligenceRule object.

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permission | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | Not supported. | Not supported. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | Not supported. | Not supported. |

Important

For delegated access using work or school accounts, the signed-in user must be assigned a supported [Microsoft Entra role](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=%2Fgraph%2Ftoc.json) or a custom role that grants the permissions required for this operation. This operation supports the following built-in roles, which provide only the least privilege necessary:

- Global Secure Access Administrator
- Security Administrator

## HTTP request

```http
PATCH /networkAccess/filteringProfiles/{filteringProfileId}/policies/{policyLinkId}/policyRules/{id}
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
| name | String | The display name of the threat intelligence rule. Inherited from [microsoft.graph.networkaccess.policyRule](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-policyrule?view=graph-rest-beta). |
| description | String | A description of the threat intelligence rule. |
| action | microsoft.graph.networkaccess.threatIntelligenceAction | The action to take when network traffic matches this rule's conditions. The possible values are: `allow`, `block`, `unknownFutureValue`. |
| priority | Int64 | The priority of the rule which determines the order of rule evaluation. Lower values indicate higher priority. |
| settings | [microsoft.graph.networkaccess.threatIntelligenceRuleSettings](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-threatintelligencerulesettings?view=graph-rest-beta) | Settings that define how the threat intelligence rule operates and is enforced. |
| matchingConditions | [microsoft.graph.networkaccess.threatIntelligenceMatchingConditions](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-threatintelligencematchingconditions?view=graph-rest-beta) | Conditions that define what network traffic should be evaluated by this rule. |

## Response

If successful, this method returns a `200 OK` response code and an updated [microsoft.graph.networkaccess.threatIntelligenceRule](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-threatintelligencerule?view=graph-rest-beta) object in the response body.

## Examples

### Request

The following example shows a request.

```http
PATCH https://graph.microsoft.com/beta/networkAccess/filteringProfiles/ab4f3459-c39d-4e99-b8d0-b1aee4726b84/policies/ac253559-37a0-4f72-b666-103420b94e38/policyRules/0823cb1e-644b-4585-80db-1c1055894ec7
Content-Type: application/json

{
  "@odata.type": "#microsoft.graph.networkaccess.threatIntelligenceRule",
  "name": "Exclusion List Rule 1",
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
          "*.bing.com"
        ]
      }
    ]
  }
}
```

### Response

The following example shows the response.

```http
HTTP/1.1 204 No Content
```
