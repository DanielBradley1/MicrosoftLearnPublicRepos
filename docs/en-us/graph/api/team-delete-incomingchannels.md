<!-- Source: https://learn.microsoft.com/en-us/graph/api/team-delete-incomingchannels?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-09-17 -->

# Remove channel

Namespace: microsoft.graph

Remove an incoming [channel](https://learn.microsoft.com/en-us/graph/api/resources/channel?view=graph-rest-1.0) \(a **channel** shared with a **team**\) from a [team](https://learn.microsoft.com/en-us/graph/api/resources/team?view=graph-rest-1.0).

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | Channel.Delete.All | Not available. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | Channel.Delete.All | Not available. |

> **Note**: This API supports admin permissions. Microsoft Teams service admins can access teams that they are not a member of.

## HTTP request

```http
DELETE /teams/{team-id}/incomingChannels/{incoming-channel-id}/$ref
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |

## Request body

Don't supply a request body for this method.

## Response

If successful, this method returns a `204 No Content` response code.

## Examples

### Request

The following example shows a request.

- [HTTP](#tabpanel_1_http)
- [JavaScript](#tabpanel_1_javascript)

```http
DELETE https://graph.microsoft.com/v1.0/teams/ece6f0a1-7ca4-498b-be79-edf6c8fc4d82/incomingChannels/19%3A56eb04e133944cf69e603c5dac2d292e%40thread.skype/$ref
```

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

await client.api('/teams/ece6f0a1-7ca4-498b-be79-edf6c8fc4d82/incomingChannels/19:56eb04e133944cf69e603c5dac2d292e@thread.skype/$ref')
	.delete();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

The following example shows the response.

```http
HTTP/1.1 204 No Content
```

## Related content

- [Remove member from channel](https://learn.microsoft.com/en-us/graph/api/channel-delete-members?view=graph-rest-1.0)
- [Remove member from team](https://learn.microsoft.com/en-us/graph/api/team-delete-members?view=graph-rest-1.0)
