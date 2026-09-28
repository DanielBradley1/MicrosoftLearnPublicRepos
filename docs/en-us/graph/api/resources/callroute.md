<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/callroute?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-12-26 -->

# callRoute resource type

Namespace: microsoft.graph

Represents the call route type.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| final | [identitySet](https://learn.microsoft.com/en-us/graph/api/resources/identityset?view=graph-rest-1.0) | The identity that was resolved to in the call. |
| original | [identitySet](https://learn.microsoft.com/en-us/graph/api/resources/identityset?view=graph-rest-1.0) | The identity that was originally used in the call. |
| routingType | String | The possible values are: `forwarded`, `lookup`, `selfFork`. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "final": {"@odata.type": "#microsoft.graph.identitySet"},
  "original": {"@odata.type": "#microsoft.graph.identitySet"},
  "routingType": "forwarded | lookup | selfFork"
}
```
