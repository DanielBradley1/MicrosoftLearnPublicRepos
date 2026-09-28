<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/agentblueprintbotbasedendpointconfigurationdetails?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-08-25 -->

# agentBlueprintBotBasedEndpointConfigurationDetails resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents the bot-based endpoint details for an agent, including the bot ID that Teams uses to deliver messages.

This complex type is used by the **botBased** property of [agentEndpointConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/agentendpointconfiguration?view=graph-rest-beta).

## Methods

None.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| botId | String | The identifier of the bot that Teams uses to deliver messages to the agent through the Bot Framework. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.agentBlueprintBotBasedEndpointConfigurationDetails",
  "botId": "String"
}
```
