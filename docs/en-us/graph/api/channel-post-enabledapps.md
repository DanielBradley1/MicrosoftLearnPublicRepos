<!-- Source: https://learn.microsoft.com/en-us/graph/api/channel-post-enabledapps?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-04-07 -->

# Add teamsApp

Namespace: microsoft.graph

Add a [teamsApp](https://learn.microsoft.com/en-us/graph/api/resources/teamsapp?view=graph-rest-1.0) that enables an [app](https://learn.microsoft.com/en-us/graph/api/resources/teamsapp?view=graph-rest-1.0) in the specified [channel](https://learn.microsoft.com/en-us/graph/api/resources/channel?view=graph-rest-1.0) within a [team](https://learn.microsoft.com/en-us/graph/api/resources/team?view=graph-rest-1.0). This operation is allowed only for channels with a **membershipType** value of `shared`.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ✅ | ✅ | ✅ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permission | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | TeamsAppInstallation.ManageSelectedForTeam | TeamsAppInstallation.ReadWriteForTeam |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | TeamsAppInstallation.ManageSelectedForTeam.All | TeamsAppInstallation.ReadWriteForTeam.All |

## HTTP request

```http
POST /teams/{team-id}/channels/{channel-id}/enabledApps/$ref
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |

## Request body

In the request body, supply a JSON object that contains an **@odata.id** property with a reference by ID to a [teamsApp](https://learn.microsoft.com/en-us/graph/api/resources/teamsapp?view=graph-rest-1.0) object.

## Response

If successful, this method returns a `204 No Content` response code.

## Examples

### Request

The following example shows a request.

- [HTTP](#tabpanel_1_http)
- [JavaScript](#tabpanel_1_javascript)

```http
POST https://graph.microsoft.com/v1.0/teams/893075dd-2487-4122-925f-022c42e20265/channels/19:561fbdbbfca848a3a8df3ffe558b1c1@thread.tacv2/enabledApps/$ref
Content-Type: application/json

{
  "@odata.id": "https://graph.microsoft.com/v1.0/appCatalogs/teamsApps/b1c5353a-7aca-41b3-830f-27d5218fe0e5"
}
```

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const teamsApp = {
  '@odata.id': 'https://graph.microsoft.com/v1.0/appCatalogs/teamsApps/b1c5353a-7aca-41b3-830f-27d5218fe0e5'
};

await client.api('/teams/893075dd-2487-4122-925f-022c42e20265/channels/19:561fbdbbfca848a3a8df3ffe558b1c1@thread.tacv2/enabledApps/$ref')
	.post(teamsApp);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

The following example shows the response.

```http
HTTP/1.1 204 No Content
```
