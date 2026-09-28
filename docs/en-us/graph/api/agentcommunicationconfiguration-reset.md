<!-- Source: https://learn.microsoft.com/en-us/graph/api/agentcommunicationconfiguration-reset?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-08-26 -->

# agentCommunicationConfiguration: reset

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Reset the communication configuration override for an [agentIdentity](https://learn.microsoft.com/en-us/graph/api/resources/agentidentity?view=graph-rest-beta), which restores effective configuration resolution to the agent blueprint level. The action takes no request body and returns the agent blueprint's [agentCommunicationConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/agentcommunicationconfiguration?view=graph-rest-beta) as the new effective configuration for the agent identity.

Note

When you set the **endpointConfiguration**, we recommend that you use the `apiBased` [agentEndpointConfigurationType](https://learn.microsoft.com/en-us/graph/api/resources/enums?view=graph-rest-beta#agentendpointconfigurationtype-values) rather than `botBased`.

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permission | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | AgentCommunicationConfiguration.ReadWrite | Not available. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | AgentCommunicationConfiguration.ReadWrite.All | Not available. |

## HTTP request

```http
POST /servicePrincipals/microsoft.graph.agentIdentity/{agentIdentityId}/communicationConfiguration/reset
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |

## Request body

Don't supply a request body for this method.

## Response

If successful, this action returns a `200 OK` response code and an [agentCommunicationConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/agentcommunicationconfiguration?view=graph-rest-beta) object in the response body.

## Examples

### Request

The following example shows a request.

- [HTTP](#tabpanel_1_http)
- [JavaScript](#tabpanel_1_javascript)

```http
POST https://graph.microsoft.com/beta/servicePrincipals/microsoft.graph.agentIdentity/1f554dbf-8c7a-42dc-8f92-1a3b4c5d6e7f/communicationConfiguration/reset
```

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

await client.api('/servicePrincipals/microsoft.graph.agentIdentity/1f554dbf-8c7a-42dc-8f92-1a3b4c5d6e7f/communicationConfiguration/reset')
	.version('beta')
	.post();
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "@odata.context": "https://graph.microsoft.com/beta/$metadata#servicePrincipals/microsoft.graph.agentIdentity/communicationConfiguration/$entity",
  "isOverridableAtAgentIdLevel": true,
  "endpointConfiguration": {
    "configurationType": "apiBased",
    "apiBased": {
      "callbackUri": "https://agent.contoso.com/api/messages"
    },
    "botBased": null
  },
  "teamworkConfiguration": {
    "groupChatConfiguration": {
      "messageNotificationMode": "atMentionedMessagesOnly"
    },
    "channelConfiguration": {
      "messageNotificationMode": "atMentionedMessagesOnly"
    },
    "oneOnOneChatConfiguration": {
      "messageNotificationMode": "allMessages"
    },
    "meetingChatConfiguration": {
      "messageNotificationMode": "atMentionedMessagesOnly"
    }
  }
}
```
