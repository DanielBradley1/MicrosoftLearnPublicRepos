<!-- Source: https://learn.microsoft.com/en-us/graph/api/virtualeventsroot-list-townhalls?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-01-09 -->

# List townhalls

Namespace: microsoft.graph

Get the list of all [virtualEventTownhall](https://learn.microsoft.com/en-us/graph/api/resources/virtualeventtownhall?view=graph-rest-1.0) objects created in a tenant.

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
| Application | VirtualEvent.Read.All | Not available. |

Note

This API returns only **virtualEventTownhall** objects where the organizer is assigned an [application access policy](https://learn.microsoft.com/en-us/graph/cloud-communication-online-meeting-application-access-policy).

## HTTP request

```http
GET /solutions/virtualEvents/townhalls
```

## Optional query parameters

This method supports the `$count` [OData query parameter](https://learn.microsoft.com/en-us/graph/query-parameters) to help customize the response. If you use `?$count=true` in the request URL, the response contains a root-level property that denotes the total number of the resource; for example, `"@odata.count": 6`.

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |

## Request body

Don't supply a request body for this method.

## Response

If successful, this method returns a `200 OK` response code and a collection of [virtualEventTownhall](https://learn.microsoft.com/en-us/graph/api/resources/virtualeventtownhall?view=graph-rest-1.0) objects in the response body.

## Examples

### Request

The following example shows a request.

```http
GET https://graph.microsoft.com/v1.0/solutions/virtualEvents/townhalls
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
      "@odata.type": "#microsoft.graph.virtualEventTownhall",
      "id": "fc6e8c15-2fd7-1dd5-caa0-87056e6a12be",
      "status": "published",
      "displayName": "The Impact of Tech on Our Lives",
      "description": {
        "content": "<p>Discusses how technology has changed the way we communicate, work, and interact with each other.</p>",
        "contentType": "html"
      },
      "startDateTime": {
        "dateTime": "2023-11-30T16:30:00",
        "timeZone": "Eastern Standard Time"
      },
      "endDateTime": {
        "dateTime": "2023-11-30T17:00:00",
        "timeZone": "Eastern Standard Time"
      },
      "createdBy": {
        "@odata.type": "microsoft.graph.communicationsIdentitySet",
        "application": null,
        "device": null,
        "user": {
          "@odata.type": "#microsoft.graph.communicationsUserIdentity",
          "id": "b7ef013a-c73c-4ec7-8ccb-e56290f45f68",
          "displayName": "Diane Demoss",
          "tenantId": "77229959-e479-4a73-b6e0-ddac27be315c"
        }
      },
      "audience": "everyone",
      "coOrganizers": [
        {
          "id": "7b7e1acd-a3e0-4533-8c1d-c1a4ca0b2e2b",
          "displayName": "Kenneth Brown",
          "tenantId": "77229959-e479-4a73-b6e0-ddac27be315c"
        }
      ],
      "invitedAttendees": [
        {
          "@odata.type": "microsoft.graph.communicationsUserIdentity",
          "id": "127962bb-84e1-7b62-fd98-1c9d39def7b6",
          "displayName": "Emilee Pham",
          "tenantId": "77229959-e479-4a73-b6e0-ddac27be315c"
        }
      ],
      "settings": {
        "isAttendeeEmailNotificationEnabled": false
      },
      "isInviteOnly": false,
      "externalEventInformation": [
        {
          "applicationId" : "1b7ba4d1-c377-4b2f-ad0e-a3fc50bc987b",
          "externalEventId": "myExternalEventId"
        }
      ]
    }
  ]
}
```
