<!-- Source: https://learn.microsoft.com/en-us/graph/api/conditionalaccesssettings-update?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-11-13 -->

# Update conditionalAccessSettings \(Conditional Access\)

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Update the tenant's [Conditional Access settings](https://learn.microsoft.com/en-us/graph/api/resources/conditionalaccesssettings?view=graph-rest-beta).

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | Policy.ReadWrite.ConditionalAccess | Not available. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | Policy.ReadWrite.ConditionalAccess | Not available. |

## HTTP request

```http
PATCH /identity/conditionalAccess/settings
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
| exclusions | [conditionalAccessExclusions](https://learn.microsoft.com/en-us/graph/api/resources/conditionalaccessexclusions?view=graph-rest-beta) | The tenant-wide exclusions configuration. |

When updating **userActionExclusions**, supply the complete desired collection, not only the entries that changed.

## Response

If successful, this method returns a `200 OK` response code and an updated [conditionalAccessSettings](https://learn.microsoft.com/en-us/graph/api/resources/conditionalaccesssettings?view=graph-rest-beta) object in the response body.

## Examples

### Request

The following example shows a request.

```http
PATCH https://graph.microsoft.com/beta/identity/conditionalAccess/settings
Content-Type: application/json

{
  "exclusions": {
    "allResourcesExclusions": {
      "userActionExclusions": [
        {
          "state": "enabled",
          "userAction": "accountrecovery"
        }
      ]
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
  "id": "a8b2e051-a1c2-4da1-a2cb-4f8c5e7f4f77",
  "modifiedDateTime": "2026-10-28T12:05:00Z",
  "exclusions": {
    "allResourcesExclusions": {
      "userActionExclusions": [
        {
          "state": "enabled",
          "userAction": "accountrecovery"
        }
      ]
    }
  }
}
```
