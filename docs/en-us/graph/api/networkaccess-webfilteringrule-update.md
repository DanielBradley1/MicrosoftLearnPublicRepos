<!-- Source: https://learn.microsoft.com/en-us/graph/api/networkaccess-webfilteringrule-update?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-11-13 -->

# Update webFilteringRule

Namespace: microsoft.graph.networkaccess

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Update a [webFilteringRule](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-webfilteringrule?view=graph-rest-beta).

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
PATCH /networkAccess/filteringProfiles/{filteringProfileId}/policies/{policyLinkId}/policy/policyRules/{webFilteringRuleId}
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
| action | [microsoft.graph.networkaccess.webFilteringAction](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-webfilteringaction?view=graph-rest-beta) | The action to apply when the rule matches web traffic. |
| description | String | The description of the object. |
| matchingConditions | [microsoft.graph.networkaccess.webFilteringMatchingConditions](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-webfilteringmatchingconditions?view=graph-rest-beta) | The source and destination conditions that determine whether traffic matches the rule. |
| name | String | The display name of the object. |
| priority | Int64 | The processing order of the rule. Rules with lower values are evaluated first. |
| settings | [microsoft.graph.networkaccess.webFilteringRuleSettings](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-webfilteringrulesettings?view=graph-rest-beta) | The settings for the object. |

## Response

If successful, this method returns a `200 OK` response code and an updated [microsoft.graph.networkaccess.webFilteringRule](https://learn.microsoft.com/en-us/graph/api/resources/networkaccess-webfilteringrule?view=graph-rest-beta) object in the response body.

## Examples

### Request

The following example shows a request.

```http
PATCH https://graph.microsoft.com/beta/networkAccess/filteringProfiles/d734d2de-f2df-4b4a-8c4c-5111f8878275/policies/70405a6c-b823-4521-8981-de9d08a21f8f/policy/policyRules/67f2edf8-1dc0-4a4f-87ea-9117541646de
Content-Type: application/json

{
  "@odata.type": "#microsoft.graph.networkaccess.webFilteringRule",
  "name": "Block social networking sites",
  "description": "Blocks access to selected social networking destinations",
  "action": {
    "@odata.type": "#microsoft.graph.networkaccess.webFilteringActionBlock"
  },
  "priority": 100,
  "settings": {
    "@odata.type": "#microsoft.graph.networkaccess.webFilteringRuleSettings",
    "status": "enabled"
  },
  "matchingConditions": {
    "@odata.type": "#microsoft.graph.networkaccess.webFilteringMatchingConditions",
    "destinations": {
      "@odata.type": "#microsoft.graph.networkaccess.webFilteringDestinationMatching",
      "httpRequestMethod": "get",
      "targets": [
        {
          "@odata.type": "#microsoft.graph.networkaccess.webFilteringWebCategoryDestination",
          "values": ["SocialNetworking"]
        }
      ]
    },
    "sources": {
      "@odata.type": "#microsoft.graph.networkaccess.webFilteringSourceMatching",
      "sessionType": "user"
    }
  }
}
```

### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "@odata.type": "#microsoft.graph.networkaccess.webFilteringRule",
  "id": "cf463f9e-41bd-2423-dcef-e495df5353da",
  "name": "Block social networking sites",
  "description": "Blocks access to selected social networking destinations",
  "action": {
    "@odata.type": "#microsoft.graph.networkaccess.webFilteringActionBlock"
  },
  "priority": 100,
  "settings": {
    "@odata.type": "#microsoft.graph.networkaccess.webFilteringRuleSettings",
    "status": "enabled"
  },
  "matchingConditions": {
    "@odata.type": "#microsoft.graph.networkaccess.webFilteringMatchingConditions",
    "destinations": {
      "@odata.type": "#microsoft.graph.networkaccess.webFilteringDestinationMatching",
      "httpRequestMethod": "get",
      "targets": [
        {
          "@odata.type": "#microsoft.graph.networkaccess.webFilteringWebCategoryDestination",
          "values": ["SocialNetworking"]
        }
      ]
    },
    "sources": {
      "@odata.type": "#microsoft.graph.networkaccess.webFilteringSourceMatching",
      "sessionType": "user"
    }
  }
}
```
