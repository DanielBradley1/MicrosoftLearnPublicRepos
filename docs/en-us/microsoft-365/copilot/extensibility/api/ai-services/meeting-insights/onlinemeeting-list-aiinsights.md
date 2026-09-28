<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/ai-services/meeting-insights/onlinemeeting-list-aiinsights -->
<!-- Sitemap-Last-Modified: 2026-04-03 -->

# List aiInsights

Important

APIs under the `/beta` version are subject to change. Use of these APIs in production applications is not supported.

Get the list of [callAiInsight](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/ai-services/meeting-insights/resources/callaiinsight) objects associated with an [onlineMeeting](https://learn.microsoft.com/en-us/graph/api/resources/onlinemeeting).

Note

- Usage-based payment models and evaluation mode aren't supported for this API. All users of applications that use this API must have a [Microsoft 365 Copilot](https://www.microsoft.com/en-us/microsoft-365-copilot) license.
- This API works differently in one or more national clouds. For more information, see [Microsoft Teams API implementation differences in national clouds](https://learn.microsoft.com/en-us/graph/teamwork-national-cloud-differences).

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ❌ | ❌ | ❌ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | OnlineMeetingAiInsight.Read.All | Not available. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | OnlineMeetingAiInsight.Read.All | Not supported. |

To use application permissions for this API, tenant administrators must create an application access policy and grant it to a user. It authorizes the app configured in the policy to fetch online meetings or online meeting artifacts on behalf of that user \(with the user ID specified in the request path\). For more information, see [Allow applications to access online meetings on behalf of a user](https://learn.microsoft.com/en-us/graph/cloud-communication-online-meeting-application-access-policy).

Note

This API works only for a meeting that hasn't expired. For more information, see [Limits and specifications for Microsoft Teams](https://learn.microsoft.com/en-us/microsoftteams/limits-specifications-teams#meeting-expiration).

## HTTP request

```http
GET https://graph.microsoft.com/v1.0/copilot/users/{userId}/onlineMeetings/{onlineMeetingId}/aiInsights
```

```http
GET https://graph.microsoft.com/beta/copilot/users/{userId}/onlineMeetings/{onlineMeetingId}/aiInsights
```

## Optional query parameters

This method supports the `$select` [OData query parameter](https://learn.microsoft.com/en-us/graph/query-parameters) to customize the response.

## Request headers

| Name | Description |
| :--- | :--- |
| `Authorization` | `Bearer {token}`. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |

## Request body

Don't supply a request body for this method.

## Response

If successful, this method returns a `200 OK` response code and a collection of [callAiInsight](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/api/ai-services/meeting-insights/resources/callaiinsight) objects in the response body.

Note

The list API output has a default limit of 20 items. However, some meetings may include more AI insights. To retrieve all available data for these meetings, you can keep calling the API using the @odata.nextLink property found in response, and continue to call the API until this property is no longer provided. For more information, see [Paging](https://learn.microsoft.com/en-us/graph/paging).

## Example

### Request

The following example shows a request. The IDs in the example have been shortened for readability.

```http
GET https://graph.microsoft.com/v1.0/copilot/users/b935e675-5e67-48b9-8d45-249d5f88e964/onlineMeetings/YTc3O.../aiInsights
```

```http
GET https://graph.microsoft.com/beta/copilot/users/b935e675-5e67-48b9-8d45-249d5f88e964/onlineMeetings/YTc3O.../aiInsights
```

### Response

The following example shows the response. The IDs in the example have been shortened for readability.

```http
HTTP/1.1 200 OK
Content-Type: application/json
{
  "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#copilot/users('b935e675-5e67-48b9-8d45-249d5f88e964')/onlineMeetings('YTc3O...')/aiInsights",
  "@odata.count": 1,
  "value": [
    {
      "id": "VjEj...",
      "callId": "af630fe0-04d3-4559-8cf9-91fe45e36296",
      "contentCorrelationId": "bc842d7a-2f6e-4b18-a1c7-73ef91d5c8e3",
      "createdDateTime": "2024-05-27T08:17:10.7261294Z",
      "endDateTime": "2024-05-27T08:17:10.7261294Z"
    }
  ]
}
```

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "@odata.context": "https://graph.microsoft.com/beta/$metadata#copilot/users('b935e675-5e67-48b9-8d45-249d5f88e964')/onlineMeetings('YTc3O...')/aiInsights",
  "@odata.count": 1,
  "value": [
    {
      "id": "VjEj...",
      "callId": "af630fe0-04d3-4559-8cf9-91fe45e36296",
      "contentCorrelationId": "bc842d7a-2f6e-4b18-a1c7-73ef91d5c8e3",
      "createdDateTime": "2024-05-27T08:17:10.7261294Z",
      "endDateTime": "2024-05-27T08:17:10.7261294Z"
    }
  ]
}
```
