<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/agentendpointconfiguration?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-08-25 -->

# agentEndpointConfiguration resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents the endpoint binding that an agent uses to receive messages, either through a bot or an API callback.

This complex type is configured in the **endpointConfiguration** property of [agentCommunicationConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/agentcommunicationconfiguration?view=graph-rest-beta).

## Methods

None.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| apiBased | [agentBlueprintApiBasedEndpointConfigurationDetails](https://learn.microsoft.com/en-us/graph/api/resources/agentblueprintapibasedendpointconfigurationdetails?view=graph-rest-beta) | The API-based endpoint details. Populated when `configurationType` is `apiBased`; carries the callback URI that Teams posts to. Must be null when `configurationType` is `botBased`. |
| botBased | [agentBlueprintBotBasedEndpointConfigurationDetails](https://learn.microsoft.com/en-us/graph/api/resources/agentblueprintbotbasedendpointconfigurationdetails?view=graph-rest-beta) | The bot-based endpoint details. Populated when `configurationType` is `botBased`; carries the bot ID that Teams messages. Must be null when `configurationType` is `apiBased`. |
| configurationType | [agentEndpointConfigurationType](https://learn.microsoft.com/en-us/graph/api/resources/enums?view=graph-rest-beta#agentendpointconfigurationtype-values) | The discriminator that indicates which endpoint variant is in effect. The possible values are: `apiBased`, `botBased`, `unknownFutureValue`. Not nullable. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.agentEndpointConfiguration",
  "configurationType": "String",
  "botBased": {"@odata.type": "microsoft.graph.agentBlueprintBotBasedEndpointConfigurationDetails"},
  "apiBased": {"@odata.type": "microsoft.graph.agentBlueprintApiBasedEndpointConfigurationDetails"}
}
```
