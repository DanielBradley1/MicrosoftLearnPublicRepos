<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/callsettings?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-03-28 -->

# callSettings resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Contains information about a call settings resource.

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List delegates](https://learn.microsoft.com/en-us/graph/api/callsettings-list-delegates?view=graph-rest-beta) | [delegationSettings](https://learn.microsoft.com/en-us/graph/api/resources/delegationsettings?view=graph-rest-beta) collection | Get a list of all delegates for a user. |
| [List delegators](https://learn.microsoft.com/en-us/graph/api/callsettings-list-delegators?view=graph-rest-beta) | [delegationSettings](https://learn.microsoft.com/en-us/graph/api/resources/delegationsettings?view=graph-rest-beta) collection | Get a list of all delegators for a user. |

## Properties

None.

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| delegates | [delegationSettings](https://learn.microsoft.com/en-us/graph/api/resources/delegationsettings?view=graph-rest-beta) collection | Represents the delegate settings. |
| delegators | [delegationSettings](https://learn.microsoft.com/en-us/graph/api/resources/delegationsettings?view=graph-rest-beta) collection | Represents the delegator settings. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.callSettings"
}
```
