<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/customsecurityattributestringvalueexemption?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-05-14 -->

# customSecurityAttributeStringValueExemption resource type

Namespace: microsoft.graph

Configuration object to configure a custom security attribute exemption for a restriction on application management policies.

Inherits from [customSecurityAttributeExemption](https://learn.microsoft.com/en-us/graph/api/resources/customsecurityattributeexemption?view=graph-rest-1.0).

## Methods

None.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | Unique identifier with combination of the custom security attribute set name and attribute name \(`AttributeSetName_AttributeName`\). Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-1.0). |
| operator | customSecurityAttributeComparisonOperator | Inherited from [customSecurityAttributeExemption](https://learn.microsoft.com/en-us/graph/api/resources/customsecurityattributeexemption?view=graph-rest-1.0). The possible values are: `equals`, `unknownFutureValue`. If `equals`, the customSecurityAttributeExemption value is compared to match the custom security attribute value for the exemption to be applied. The comparison is case sensitive. |
| value | String | Value representing custom security attribute value to compare against while evaluating the exemption. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.customSecurityAttributeStringValueExemption",
  "id": "String",
  "operator": "String",
  "value": "String"
}
```
