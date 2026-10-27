<!-- Source: https://learn.microsoft.com/en-us/graph/api/windowsupdates-policy-post-rings?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-10-23 -->

# Create ring

Namespace: microsoft.graph.windowsUpdates

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Create a new [ring](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-ring?view=graph-rest-beta) object.

You can use this method with the following child object types: [driverUpdateRing](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-driverupdatering?view=graph-rest-beta), [featureUpdateRing](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-featureupdatering?view=graph-rest-beta), and [qualityUpdateRing](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-qualityupdatering?view=graph-rest-beta).

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ✅ | ✅ | ❌ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | WindowsUpdates.ReadWrite.All | Not available. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | WindowsUpdates.ReadWrite.All | Not available. |

Important

For delegated access using work or school accounts, the signed-in user must be an owner or member of the group or be assigned a supported [Microsoft Entra role](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference?toc=%2Fgraph%2Ftoc.json) or a custom role that grants the permissions required for this operation. *Intune Administrator*, or *Windows Update Deployment Administrator* are the least privileged roles supported for this operation.

## HTTP request

```http
POST /admin/windows/updates/policies/{policyId}/rings
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |

## Request body

In the request body, supply a JSON representation of the [ring](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-ring?view=graph-rest-beta) object.

Because **ring** is abstract, specify the concrete type in the `@odata.type` property. Supported values include `#microsoft.graph.windowsUpdates.driverUpdateRing`, `#microsoft.graph.windowsUpdates.featureUpdateRing`, and `#microsoft.graph.windowsUpdates.qualityUpdateRing`.

You can specify the following properties when you create a **ring** object.

| Property | Type | Description |
| :--- | :--- | :--- |
| deferralInDays | Int32 | The update deferral period in days. The value must be between `0` and `30`. Optional. |
| description | String | The ring description. The maximum length is 1,500 characters. Required. |
| displayName | String | The ring display name. The maximum length is 200 characters. Required. |
| excludedGroupAssignment | [microsoft.graph.windowsUpdates.excludedGroupAssignment](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-excludedgroupassignment?view=graph-rest-beta) | Governs the update deployment audience with excluded groups. Groups are logical containers of devices represented by Microsoft Entra groups. Required. |
| includedGroupAssignment | [microsoft.graph.windowsUpdates.includedGroupAssignment](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-includedgroupassignment?view=graph-rest-beta) | Governs the update deployment audience with included groups. Groups are logical containers of devices represented by Microsoft Entra groups. Required. |
| isHotpatchEnabled | Boolean | Indicates whether hotpatch updates are enabled. Applies only to **qualityUpdateRing**. Required for that type. |
| isOfferOptional | Boolean | Indicates whether the feature update is offered to end users as optional. Applies only to **featureUpdateRing**. Required for that type. |
| isPaused | Boolean | Indicates whether update offers for the ring are paused. Required. |
| offerDurationInDays | Int32 | The total length of the gradual rollout window, in days. Applies only to **featureUpdateRing**. Optional. |
| offerIntervalInDays | Int32 | How often, in days, a new subset of devices is offered the update. Applies only to **featureUpdateRing**. Optional. |

## Response

If successful, this method returns a `201 Created` response code and a [microsoft.graph.windowsUpdates.ring](https://learn.microsoft.com/en-us/graph/api/resources/windowsupdates-ring?view=graph-rest-beta) object in the response body.

## Examples

### Request

The following example shows how to create a feature update ring.

```http
POST https://graph.microsoft.com/beta/admin/windows/updates/policies/22222222-2222-4222-8222-222222222222/rings
Content-Type: application/json

{
  "@odata.type": "#microsoft.graph.windowsUpdates.featureUpdateRing",
  "displayName": "Pilot",
  "description": "Pilot devices",
  "includedGroupAssignment": {
    "assignments": [
      {
        "groupId": "33333333-3333-4333-8333-333333333333"
      }
    ]
  },
  "excludedGroupAssignment": {
    "assignments": []
  },
  "deferralInDays": 0,
  "isPaused": false,
  "isOfferOptional": false,
  "offerDurationInDays": 1,
  "offerIntervalInDays": 0
}
```

### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 201 Created
Content-Type: application/json

{
  "@odata.type": "#microsoft.graph.windowsUpdates.featureUpdateRing",
  "createdDateTime": "2026-09-28T11:05:00Z",
  "deferralInDays": 0,
  "description": "Pilot devices",
  "displayName": "Pilot",
  "excludedGroupAssignment": {
    "assignments": []
  },
  "id": "44444444-4444-4444-8444-444444444444",
  "includedGroupAssignment": {
    "assignments": [
      {
        "groupId": "33333333-3333-4333-8333-333333333333"
      }
    ]
  },
  "isOfferOptional": false,
  "isPaused": false,
  "lastModifiedDateTime": "2026-09-28T11:05:00Z",
  "offerDurationInDays": 1,
  "offerIntervalInDays": 0
}
```
