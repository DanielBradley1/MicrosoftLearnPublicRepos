<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/delegateallowedactions?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-03-28 -->

# delegateAllowedActions resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents the allowed actions for a delegate and delegator.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| joinActiveCalls | Boolean | Indicates whether the delegator or delegate allows participation in active calls. |
| makeCalls | Boolean | Indicates whether the delegator or delegate allows calls to be made on their behalf. |
| manageCallAndDelegateSettings | Boolean | Indicates whether the delegator or delegate allows the management of call and delegation settings. |
| pickUpHeldCalls | Boolean | Indicates whether the delegator or delegate allows held calls to be picked up. |
| receiveCalls | Boolean | Indicates whether the delegator or delegate allows calls to be received on their behalf. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.delegateAllowedActions",
  "joinActiveCalls": "Boolean",
  "makeCalls": "Boolean",
  "manageCallAndDelegateSettings": "Boolean",
  "pickUpHeldCalls": "Boolean",
  "receiveCalls": "Boolean"
}
```
