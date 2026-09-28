<!-- Source: https://learn.microsoft.com/en-us/graph/api/usertrainingcampaigndetails-list?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-06-11 -->

# List trainingCampaignUsers

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

List users of a tenant and their online actions in a training campaign.

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | AttackSimulation.Read.All | Not available. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | AttackSimulation.Read.All | Not available. |

## HTTP request

```http
GET /security/attackSimulation/trainingCampaigns/{trainingCampaignId}/report/campaignUsers
```

## Optional query parameters

This method supports the `$count`, `$skipToken`, and `$top` [OData query parameters](https://learn.microsoft.com/en-us/graph/query-parameters) to help customize the response.

If the result set spans multiple pages, the response body contains an `@odata.nextLink` that you can use to page through the result set.

The following list shows some examples of requests that use the supported OData query parameters:

```http
GET /security/attackSimulation/trainingCampaigns/{trainingCampaignId}/report/campaignUsers?$count=true
GET /security/attackSimulation/trainingCampaigns/{trainingCampaignId}/report/campaignUsers?$skipToken={skipToken}
GET /security/attackSimulation/trainingCampaigns/{trainingCampaignId}/report/campaignUsers?$top=1
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |

## Request body

Don't supply a request body for this method.

## Response

If successful, this method returns a `200 OK` response code and a collection of [userSimulationDetails](https://learn.microsoft.com/en-us/graph/api/resources/usersimulationdetails?view=graph-rest-beta) objects in the response body.

## Examples

### Request

The following example shows a request.

- [HTTP](#tabpanel_1_http)
- [JavaScript](#tabpanel_1_javascript)

```msgraph
GET https://graph.microsoft.com/beta/security/attackSimulation/trainingCampaigns/f1b13829-3829-f1b1-2938-b1f12938b1a/report/campaignUsers
```

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

let campaignUsers = await client.api('/security/attackSimulation/trainingCampaigns/f1b13829-3829-f1b1-2938-b1f12938b1a/report/campaignUsers')
	.version('beta')
	.get();
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

---

### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "value": [
    {
      "isCompromised": true,
      "compromisedDateTime": "2021-01-01T01:02:01.01Z",
      "simulationEvents": [
        {
          "eventName": "SuccessfullyDeliveredEmail",
          "eventDateTime": "2021-01-01T01:01:01.01Z",
          "ipAddress": "100.200.100.200",
          "osPlatformDeviceDetails": "Sample OS",
          "browser": "Sample Browser"
        },
        {
          "eventName": "EmailLinkClicked",
          "eventDateTime": "2021-01-01T01:02:01.01Z",
          "ipAddress": "100.200.100.200",
          "osPlatformDeviceDetails": "Sample OS",
          "browser": "Sample Browser"
        }
      ],
      "trainingEvents": [
        {
          "displayName": "Sample Training",
          "latestTrainingStatus": "assigned",
          "trainingAssignedProperties": {
            "contentDateTime": "2021-01-01T01:03:01.01Z",
            "ipAddress": "100.200.100.200",
            "osPlatformDeviceDetails": "Sample OS",
            "browser": "Sample Browser",
            "potentialScoreImpact": 5.0
          },
          "trainingUpdatedProperties": {
            "contentDateTime": "2021-01-01T01:04:01.01Z",
            "ipAddress": "100.200.100.201",
            "osPlatformDeviceDetails": "Sample OS-2",
            "browser": "Sample Browser",
            "potentialScoreImpact": 5.0
          },
          "trainingCompletedProperties": {
            "contentDateTime": "2021-01-01T01:05:01.01Z",
            "ipAddress": "100.200.100.202",
            "osPlatformDeviceDetails": "Sample OS",
            "browser": "Sample Browser-2",
            "potentialScoreImpact": 5.0
          }
        }
      ],
      "assignedTrainingsCount": 1,
      "completedTrainingsCount": 0,
      "inProgressTrainingsCount": 0,
      "reportedPhishDateTime": "2021-01-01T01:01:01.01Z",
      "simulationUser": {
        "userId": "99af58b9-ef1a-412b-a581-cb42fe8c8e21",
        "displayName": "Reed Flores",
        "email": "reed@contoso.com"
      }
    }
  ]
}
```
