<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/errorsettings?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-09-29 -->

# errorSettings resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents settings that control enforcement behavior when policy evaluation can't be completed. This type is used by the **errorSettings** property of [policyConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/policyconfiguration?view=graph-rest-beta).

## Methods

None.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| errorAction | [errorActions](https://learn.microsoft.com/en-us/graph/api/resources/enums?view=graph-rest-beta#erroractions-values) | The action that the enforcement plane takes when policy evaluation can't be completed. This flagged enumeration allows multiple members to be selected simultaneously. The possible values are: `none`, `audit`, `block`, `unknownFutureValue`. Don't combine `none` with another value. |
| isEnabled | Boolean | Indicates whether Secure by Default is enabled for the protection scope. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.errorSettings",
  "errorAction": "String",
  "isEnabled": "Boolean"
}
```
