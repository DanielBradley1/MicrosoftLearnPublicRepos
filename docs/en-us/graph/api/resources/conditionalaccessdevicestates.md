<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/conditionalaccessdevicestates?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-07-23 -->

# conditionalAccessDeviceStates resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents device states in the policy scope.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| includeStates | String collection | States in the scope of the policy. `All` is the only allowed value. |
| excludeStates | String collection | States excluded from the scope of the policy. Possible values: `Compliant`, `DomainJoined`. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "includeStates": [ "String" ],
  "excludeStates": [ "String" ]
}
```
