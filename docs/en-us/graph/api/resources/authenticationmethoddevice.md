<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/authenticationmethoddevice?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-12-10 -->

# authenticationMethodDevice resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Exposes the hardware OATH method in the directory.

Inherits from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta).

## Methods

None.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| displayName | String | Optional name given to the hardware OATH device. |
| id | String | Unique identifier for the device. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta). |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| hardwareOathDevices | [hardwareOathTokenAuthenticationMethodDevice](https://learn.microsoft.com/en-us/graph/api/resources/hardwareoathtokenauthenticationmethoddevice?view=graph-rest-beta) collection | Exposes the hardware OATH method in the directory. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.authenticationMethodDevice",
  "id": "String (identifier)",
  "displayName": "String"
}
```
