<!-- Source: https://learn.microsoft.com/en-us/graph/api/trainingcampaignreportoverview-get?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-06-11 -->

# Get trainingCampaignReportOverview

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Get an overview of a training campaign.

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | AttackSimulation.Read.All | Not available. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | AttackSimulation.Read.All | Not available. |

## HTTP request

```http
GET /security/attackSimulation/trainingCampaigns/{trainingCampaignId}/report/overview
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |

## Request body

Don't supply a request body for this method.

## Response

If successful, this method returns a `200 OK` response code and a [trainingCampaignReportOverview](https://learn.microsoft.com/en-us/graph/api/resources/trainingcampaignreportoverview?view=graph-rest-beta) object in the response body.

## Examples

### Request

The following example shows a request.

```http
GET https://graph.microsoft.com/beta/security/attackSimulation/trainingCampaigns/f1b13829-3829-f1b1-2938-b1f12938b1a/report/overview
```

---

### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
    "trainingModuleCompletion": {
        "trainingsAssignedUserCount": 1,
        "assignedTrainingsInfos": [
            {
                "assignedUserCount": 1,
                "completedUserCount": 0,
                "displayName": "Identity Theft"
            },
            {
                "assignedUserCount": 1,
                "completedUserCount": 0,
                "displayName": "Introduction to Information Security"
            },
            {
                "assignedUserCount": 1,
                "completedUserCount": 0,
                "displayName": "Malware"
            }
        ]
    },
    "userCompletionStatus": {
        "notStartedUsersCount": 0,
        "completedUsersCount": 0,
        "inProgressUsersCount": 1,
        "notCompletedUsersCount": 0,
        "previouslyAssignedUsersCount": 0
    },
    "trainingNotificationDeliveryStatus": {
        "resolvedTargetsCount": 1,
        "successfulMessageDeliveryCount": 1,
        "failedMessageDeliveryCount": 0
    }
}
```
