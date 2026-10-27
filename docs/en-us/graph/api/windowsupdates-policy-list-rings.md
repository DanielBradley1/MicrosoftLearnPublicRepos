<!-- Source: https://learn.microsoft.com/en-us/graph/api/windowsupdates-policy-list-rings?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-10-23 -->

# List rings

Namespace: microsoft.graph.windowsUpdates

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Get a list of the [ring](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-ring?view=graph-rest-beta) objects and their properties.

You can use this method with the following child object types: [driverUpdateRing](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-driverupdatering?view=graph-rest-beta), [featureUpdateRing](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-featureupdatering?view=graph-rest-beta), and [qualityUpdateRing](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-qualityupdatering?view=graph-rest-beta).

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ✅ | ✅ | ❌ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | WindowsUpdates.Read.All | WindowsUpdates.ReadWrite.All |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | WindowsUpdates.Read.All | WindowsUpdates.ReadWrite.All |

Important

For delegated access using work or school accounts, the signed-in user must be an owner or member of the group or be assigned a supported [Microsoft Entra role](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=%2Fgraph%2Ftoc.json) or a custom role that grants the permissions required for this operation. *Intune Administrator*, or *Windows Update Deployment Administrator* are the least privileged roles supported for this operation.

## HTTP request

To get all ring objects for a policy or only rings of a specific derived type:

```http
GET /admin/windows/updates/policies/{policyId}/rings
GET /admin/windows/updates/policies/{policyId}/rings/microsoft.graph.windowsUpdates.driverUpdateRing
GET /admin/windows/updates/policies/{policyId}/rings/microsoft.graph.windowsUpdates.featureUpdateRing
GET /admin/windows/updates/policies/{policyId}/rings/microsoft.graph.windowsUpdates.qualityUpdateRing
```

## Optional query parameters

This method supports the `$select`, `$filter`, `$count`, and `$top` OData query parameters to help customize the response. For general information, see [OData query parameters](https://learn.microsoft.com/en-us/graph/query-parameters).

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |

## Request body

Don't supply a request body for this method.

## Response

If successful, this method returns a `200 OK` response code and a collection of [microsoft.graph.windowsUpdates.ring](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-ring?view=graph-rest-beta) objects in the response body.

## Examples

### Request

The following example shows how to get a list that contains each supported ring type.

```http
GET https://graph.microsoft.com/beta/admin/windows/updates/policies/45a01ef3-fb4b-8c1d-2428-1f060464033c/rings
```

### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "value": [
    {
      "@odata.type": "#microsoft.graph.windowsUpdates.driverUpdateRing",
      "createdDateTime": "2026-09-28T11:00:00Z",
      "deferralInDays": 5,
      "description": "Pilot devices for driver and firmware updates",
      "displayName": "Driver pilot",
      "excludedGroupAssignment": {
        "assignments": []
      },
      "id": "44444444-4444-4444-8444-444444444444",
      "includedGroupAssignment": {
        "assignments": [
          {
            "groupId": "77777777-7777-4777-8777-777777777777"
          }
        ]
      },
      "isPaused": false,
      "lastModifiedDateTime": "2026-09-28T11:00:00Z"
    },
    {
      "@odata.type": "#microsoft.graph.windowsUpdates.featureUpdateRing",
      "createdDateTime": "2026-09-28T11:05:00Z",
      "deferralInDays": 0,
      "description": "Pilot devices for feature updates",
      "displayName": "Feature pilot",
      "excludedGroupAssignment": {
        "assignments": []
      },
      "id": "55555555-5555-4555-8555-555555555555",
      "includedGroupAssignment": {
        "assignments": [
          {
            "groupId": "88888888-8888-4888-8888-888888888888"
          }
        ]
      },
      "isOfferOptional": false,
      "isPaused": false,
      "lastModifiedDateTime": "2026-09-28T11:05:00Z",
      "offerDurationInDays": 1,
      "offerIntervalInDays": 0
    },
    {
      "@odata.type": "#microsoft.graph.windowsUpdates.qualityUpdateRing",
      "createdDateTime": "2026-09-28T11:10:00Z",
      "deferralInDays": 2,
      "description": "Production devices for monthly quality updates",
      "displayName": "Quality production",
      "excludedGroupAssignment": {
        "assignments": []
      },
      "id": "66666666-6666-4666-8666-666666666666",
      "includedGroupAssignment": {
        "assignments": [
          {
            "groupId": "99999999-9999-4999-8999-999999999999"
          }
        ]
      },
      "isHotpatchEnabled": true,
      "isPaused": false,
      "lastModifiedDateTime": "2026-09-28T11:10:00Z"
    }
  ]
}
```
