<!-- Source: https://learn.microsoft.com/en-us/graph/api/agentidentityblueprint-update-communicationconfiguration?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-08-26 -->

# Update communicationConfiguration

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Replace the [agentCommunicationConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/agentcommunicationconfiguration?view=graph-rest-beta) of an [agentIdentityBlueprint](https://learn.microsoft.com/en-us/graph/api/resources/agentidentityblueprint?view=graph-rest-beta). This operation is a full replace: the request replaces the entire configuration object with the supplied body.

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
PUT /applications/{agentIdentityBlueprintId}/microsoft.graph.agentIdentityBlueprint/communicationConfiguration
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |

## Request body

In the request body, supply a full JSON representation of the [agentCommunicationConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/agentcommunicationconfiguration?view=graph-rest-beta) object. Because this operation is a full replace, include all properties you want to persist; properties that are omitted are cleared.

| Property | Type | Description |
| :--- | :--- | :--- |
| isOverridableAtAgentIdLevel | Boolean | Indicates whether individual agent instances created from this blueprint can override the **endpointConfiguration**. Optional. |
| endpointConfiguration | [agentEndpointConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/agentendpointconfiguration?view=graph-rest-beta) | The endpoint binding \(bot ID or callback URI\) that the agent uses to receive messages. Optional. |
| teamworkConfiguration | [agentTeamworkConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/agentteamworkconfiguration?view=graph-rest-beta) | The per-conversation-context message notification settings that agents use. Optional. |

## Response

If successful, this method returns a `200 OK` response code and an updated [agentCommunicationConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/agentcommunicationconfiguration?view=graph-rest-beta) object in the response body.

## Examples

### Request

The following example shows a request.

- [HTTP](#tabpanel_1_http)
- [JavaScript](#tabpanel_1_javascript)

```http
PUT https://graph.microsoft.com/beta/applications/2a665ec0-9d8b-43ed-9fa3-2b4c5d6e7f80/microsoft.graph.agentIdentityBlueprint/communicationConfiguration
Content-Type: application/json

{
  "isOverridableAtAgentIdLevel": false,
  "endpointConfiguration": {
    "configurationType": "apiBased",
    "apiBased": {
      "callbackUri": "https://agent.contoso.com/api/messages"
    }
  },
  "teamworkConfiguration": {
    "groupChatConfiguration": {
      "messageNotificationMode": "atMentionedMessagesOnly"
    },
    "channelConfiguration": {
      "messageNotificationMode": "allMessages"
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

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const agentCommunicationConfiguration = {
  isOverridableAtAgentIdLevel: false,
  endpointConfiguration: {
    configurationType: 'apiBased',
    apiBased: {
      callbackUri: 'https://agent.contoso.com/api/messages'
    }
  },
  teamworkConfiguration: {
    groupChatConfiguration: {
      messageNotificationMode: 'atMentionedMessagesOnly'
    },
    channelConfiguration: {
      messageNotificationMode: 'allMessages'
    },
    oneOnOneChatConfiguration: {
      messageNotificationMode: 'allMessages'
    },
    meetingChatConfiguration: {
      messageNotificationMode: 'atMentionedMessagesOnly'
    }
  }
};

await client.api('/applications/2a665ec0-9d8b-43ed-9fa3-2b4c5d6e7f80/microsoft.graph.agentIdentityBlueprint/communicationConfiguration')
	.version('beta')
	.put(agentCommunicationConfiguration);
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
  "@odata.context": "https://graph.microsoft.com/beta/$metadata#applications('2a665ec0-9d8b-43ed-9fa3-2b4c5d6e7f80')/microsoft.graph.agentIdentityBlueprint/communicationConfiguration/$entity",
  "isOverridableAtAgentIdLevel": false,
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
      "messageNotificationMode": "allMessages"
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
