<!-- Source: https://learn.microsoft.com/en-us/graph/api/identitygovernance-lifecyclepolicy-impact?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-10-07 -->

# lifecyclePolicy: impact

Namespace: microsoft.graph.identityGovernance

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Evaluate the impact of a [lifecyclePolicy](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-lifecyclepolicy?view=graph-rest-beta) on its subjects during a specified period. If you omit the start and end dates, the function evaluates the previous seven days. The maximum supported period is 30 days.

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | LifecyclePolicies-Guests.Read.All | LifecyclePolicies-AgentId.Read.All, LifecyclePolicies-AgentId.ReadWrite.All, LifecyclePolicies-Guests.ReadWrite.All |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | LifecyclePolicies-Guests.Read.All | LifecyclePolicies-AgentId.Read.All, LifecyclePolicies-AgentId.ReadWrite.All, LifecyclePolicies-Guests.ReadWrite.All |

## HTTP request

```http
GET /identityGovernance/lifecycleWorkflows/lifecyclePolicies/{lifecyclePolicyId}/impact(startDateTime={startDateTime},endDateTime={endDateTime})
```

## Function parameters

| Parameter | Type | Description |
| :--- | :--- | :--- |
| startDateTime | DateTimeOffset | Optional. The start of the evaluation period. |
| endDateTime | DateTimeOffset | Optional. The end of the evaluation period. |

## Optional query parameters

This method supports `$filter` with the `eq` and `ne` operators on `subject/id`, `$expand=subject`, and `$select` to customize the response.

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |

## Request body

Don't supply a request body for this method.

## Response

If successful, this function returns a `200 OK` response code and a collection of [lifecyclePolicyImpactSummary](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-lifecyclepolicyimpactsummary?view=graph-rest-beta) objects in the response body.

## Examples

### Request

```http
GET https://graph.microsoft.com/beta/identityGovernance/lifecycleWorkflows/lifecyclePolicies/37c2a69d-38d7-42ad-8b77-24da70f35bd4/impact(startDateTime=2026-08-01T00:00:00Z,endDateTime=2026-08-08T00:00:00Z)?$expand=subject
```

### Response

```http
HTTP/1.1 200 OK
Content-Type: application/json
```

```json
{
  "@odata.context": "https://graph.microsoft.com/beta/$metadata#Collection(microsoft.graph.identityGovernance.lifecyclePolicyImpactSummary)",
  "value": [
    {
      "id": "e4f5d67a-5a10-4c40-9734-0c5f2d83a1bf",
      "actionsTaken": [
        {
          "dateTime": "2026-08-04T10:00:00Z",
          "actionType": "attestationNeededNotificationSent"
        }
      ],
      "subject": {
        "@odata.type": "#microsoft.graph.user",
        "id": "e4f5d67a-5a10-4c40-9734-0c5f2d83a1bf",
        "displayName": "Adele Vance"
      }
    }
  ]
}
```
