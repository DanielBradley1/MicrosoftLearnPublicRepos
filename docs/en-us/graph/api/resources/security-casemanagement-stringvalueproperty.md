<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/security-casemanagement-stringvalueproperty?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-07-16 -->

# stringValueProperty resource type

Namespace: microsoft.graph.security.caseManagement

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents a string value in a [modifiedProperty](https://learn.microsoft.com/en-us/graph/api/resources/security-casemanagement-modifiedproperty?view=graph-rest-beta). Returned in the **oldValue** and **newValue** properties.

Inherits from [microsoft.graph.security.caseManagement.valueProperty](https://learn.microsoft.com/en-us/graph/api/resources/security-casemanagement-valueproperty?view=graph-rest-beta).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| value | String | The string value. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.security.caseManagement.stringValueProperty",
  "value": "String"
}
```
