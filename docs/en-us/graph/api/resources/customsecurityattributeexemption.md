<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/customsecurityattributeexemption?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-05-14 -->

# customSecurityAttributeExemption resource type

Namespace: microsoft.graph

Configuration object to configure a custom security attribute exemption for a restriction on application management policies. This resource is an abstract type from which the [customSecurityAttributeStringValueExemption](https://learn.microsoft.com/en-us/graph/api/resources/customsecurityattributestringvalueexemption?view=graph-rest-1.0) derives.

Inherits from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-1.0).

## Methods

None.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | Unique identifier with combination of the custom security attribute set name and attribute name. For example, `AttributeSetName_AttributeName`. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-1.0). |
| operator | customSecurityAttributeComparisonOperator | The possible values are: `equals`, `unknownFutureValue`. If `equals`, the customSecurityAttributeExemption value is compared to match the custom security attribute value for the exemption to be applied. The comparison is case sensitive. Not nullable. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.customSecurityAttributeExemption",
  "id": "String",
  "operator": "String"
}
```
