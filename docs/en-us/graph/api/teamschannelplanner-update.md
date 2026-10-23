<!-- Source: https://learn.microsoft.com/en-us/graph/api/teamschannelplanner-update?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-10-15 -->

# Update teamsChannelPlanner

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Update the properties of a teamsChannelPlanner object.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ✅ | ✅ | ❌ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permission | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | Not supported. | Not supported. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | Not supported. | Not supported. |

## HTTP request

```http
PATCH /teams/{teamsId}/channels/{channelId}/planner
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |

## Request body

No properties are currently supported for update.

## Response

If successful, this method returns a `200 OK` response code and an updated [teamsChannelPlanner](https://learn.microsoft.com/en-us/graph/api/resources/teamschannelplanner?view=graph-rest-beta) object in the response body.

## Examples

### Request

The following example shows a request.

```http
PATCH https://graph.microsoft.com/beta/teams/{teamsId}/channels/{channelId}/planner
Content-Type: application/json

{
  "@odata.type": "#microsoft.graph.teamsChannelPlanner"
}
```

### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "@odata.type": "#microsoft.graph.teamsChannelPlanner",
  "id": "c027a7c0-56ae-908c-2e54-85fc78ea073d"
}
```
