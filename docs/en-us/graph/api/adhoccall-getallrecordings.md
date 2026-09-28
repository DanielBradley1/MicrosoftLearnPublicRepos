<!-- Source: https://learn.microsoft.com/en-us/graph/api/adhoccall-getallrecordings?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-03-23 -->

# adhocCall: getAllRecordings

Namespace: microsoft.graph

Get the [callRecording](https://learn.microsoft.com/en-us/graph/api/resources/callrecording?view=graph-rest-1.0) objects from [ad hoc call](https://learn.microsoft.com/en-us/graph/api/resources/adhoccall?view=graph-rest-1.0) instances that a specific user initiates. This API enables you to programmatically access and analyze meeting recordings for calls organized by a given user, filtered by optional date ranges.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ❌ | ❌ | ❌ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | Not supported. | Not supported. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | CallRecordings.Read.All | Not available. |

## HTTP request

```http
GET /users/{usersId}/adhocCalls/getAllRecordings
```

## Function parameters

In the request URL, provide the following function parameters with values.

| Parameter | Type | Description |
| :--- | :--- | :--- |
| endDateTime | DateTimeOffset | Optional. Filter for artifacts created before the given end date. The timestamp type represents date and time information using ISO 8601 format and is always in UTC. For example, midnight UTC on Jan 1, 2025 is `2025-01-01T00:00:00Z`. |
| startDateTime | DateTimeOffset | Optional. Filter for artifacts created after the given start date. The timestamp type represents date and time information using ISO 8601 format and is always in UTC. For example, midnight UTC on Jan 1, 2025 is `2025-01-01T00:00:00Z`. |
| userId | String | The user identifier of the meeting organizer to filter for artifacts for meetings organized by the given user identifier. Required. |

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |

## Request body

Don't supply a request body for this method.

## Response

If successful, this function returns a `200 OK` response code and a [callRecording](https://learn.microsoft.com/en-us/graph/api/resources/callrecording?view=graph-rest-1.0) collection in the response body.

## Examples

### Request

The following example shows a request.

```http
GET https://graph.microsoft.com/v1.0/adhocCalls/getAllRecordings(userId=d4220f1b-4c12-436c-8a03-dc3e362f9d54,startDateTime=2025-10-07T07:25:21.9730833Z,endDateTime=2025-10-07T07:25:52.4130833Z)
```

### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#users('d4220f1b-4c12-436c-8a03-dc3e362f9d54')/adhocCalls",
  "@odata.count": 2,
  "value": [
    {
      "id": "ktVizJvGAAAAnfCMlATZWzE5OmNkYWQ5MTQ4LWQ5MjYtNDczMS04NjE4LTM3MWU1ODdkZGVkMF9kNDIyMGYxYi00YzEyLTQzNmMtOGEwMy1kYzNlMzYyZjlkNTRAdW5xLmdibC5zcGFjZXOg2TlmYjdlNWMxZS04YWI4LTQ2NDctOTdhMS03Mzk5MDhkNDE3YjMtMTc1OTgyMTkyMS1SZWNvcmRpbmc=",
      "callId": "fb7e5c1e-8ab8-4647-97a1-739908d417b3",
      "contentCorrelationId": "7cc3ae2a-0aa9-4e47-9d85-e98e607d1af2-20251007_072521",
      "createdDateTime": "2025-10-07T07:25:21.9730833Z",
      "endDateTime": "2025-10-07T07:25:52.4130833Z",
      "recordingContentUrl": "https://graph.microsoft.com/v1.0/users/d4220f1b-4c12-436c-8a03-dc3e362f9d54/adhocCalls/fb7e5c1e-8ab8-4647-97a1-739908d417b3/recordings/ktVizJvGAAAAnfCMlATZWzE5OmNkYWQ5MTQ4LWQ5MjYtNDczMS04NjE4LTM3MWU1ODdkZGVkMF9kNDIyMGYxYi00YzEyLTQzNmMtOGEwMy1kYzNlMzYyZjlkNTRAdW5xLmdibC5zcGFjZXOg2TlmYjdlNWMxZS04YWI4LTQ2NDctOTdhMS03Mzk5MDhkNDE3YjMtMTc1OTgyMTkyMS1SZWNvcmRpbmc=",
      "meetingOrganizer": {
        "application": null,
        "device": null,
        "user": {
          "@odata.type": "#microsoft.graph.teamworkUserIdentity",
          "id": "d4220f1b-4c12-436c-8a03-dc3e362f9d54",
          "displayName": null,
          "userIdentityType": "aadUser",
          "tenantId": "2432b57b-0abd-43db-aa7b-16eadd115d34"
        }
      }
    },
    {
      "id": "ktVizJvGAAAAnfCMlATZWzE5OmNkYWQ5MTQ4LWQ5MjYtNDczMS04NjE4LTM3MWU1ODdkZGVkMF9kNDIyMGYxYi00YzEyLTQzNmMtOGEwMy1kYzNlMzYyZjlkNTRAdW5xLmdibC5zcGFjZXOg2TkwNTQ3ZDUzOS0wNTExLTRiZDEtODRjZi01YTA3M2ZhYjcxMmQtMTc1OTgxODY3My1SZWNvcmRpbmc=",
      "callId": "0547d539-0511-4bd1-84cf-5a073fab712d",
      "contentCorrelationId": "94c3eb48-4271-4b60-b7b7-121b9d798eb3-20251007_063113",
      "createdDateTime": "2025-10-07T06:31:13.1759028Z",
      "endDateTime": "2025-10-07T06:31:26.5759028Z",
      "recordingContentUrl": "https://graph.microsoft.com/v1.0/users/d4220f1b-4c12-436c-8a03-dc3e362f9d54/adhocCalls/0547d539-0511-4bd1-84cf-5a073fab712d/recordings/ktVizJvGAAAAnfCMlATZWzE5OmNkYWQ5MTQ4LWQ5MjYtNDczMS04NjE4LTM3MWU1ODdkZGVkMF9kNDIyMGYxYi00YzEyLTQzNmMtOGEwMy1kYzNlMzYyZjlkNTRAdW5xLmdibC5zcGFjZXOg2TkwNTQ3ZDUzOS0wNTExLTRiZDEtODRjZi01YTA3M2ZhYjcxMmQtMTc1OTgxODY3My1SZWNvcmRpbmc=",
      "meetingOrganizer": {
        "application": null,
        "device": null,
        "user": {
          "@odata.type": "#microsoft.graph.teamworkUserIdentity",
          "id": "d4220f1b-4c12-436c-8a03-dc3e362f9d54",
          "displayName": null,
          "userIdentityType": "aadUser",
          "tenantId": "2432b57b-0abd-43db-aa7b-16eadd115d34"
        }
      }
    }
  ]
}
```
