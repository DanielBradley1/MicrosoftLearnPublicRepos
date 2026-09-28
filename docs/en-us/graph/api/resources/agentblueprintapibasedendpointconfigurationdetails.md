<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/agentblueprintapibasedendpointconfigurationdetails?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-08-25 -->

# agentBlueprintApiBasedEndpointConfigurationDetails resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents the API-based endpoint details for an agent, including the callback URI that Teams posts message events to.

This complex type is used by the **apiBased** property of [agentEndpointConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/agentendpointconfiguration?view=graph-rest-beta).

## Methods

None.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| callbackUri | String | The absolute HTTPS URI that Teams posts agent message events to. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.agentBlueprintApiBasedEndpointConfigurationDetails",
  "callbackUri": "String"
}
```
