<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/securesigninsessioncontrol?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-07-23 -->

# secureSignInSessionControl resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Session control to require sign in sessions to be bound to a device. Inherits from [conditionalAccessSessionControl](https://learn.microsoft.com/en-us/graph/api/resources/conditionalaccesssessioncontrol?view=graph-rest-beta).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| isEnabled | Boolean | Specifies whether the session control is enabled. Inherited from [conditionalAccessSessionControl](https://learn.microsoft.com/en-us/graph/api/resources/conditionalaccesssessioncontrol?view=graph-rest-beta). |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.secureSignInSessionControl",
  "isEnabled": "Boolean"
}
```
