<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/security-auditrecordtypedictionary?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-08-14 -->

# auditRecordTypeDictionary resource type

Namespace: microsoft.graph.security

Represents an open-type dictionary for dynamic audit event properties. This type follows the [Graph Dictionary pattern](https://github.com/microsoft/api-guidelines/blob/vNext/graph/patterns/dictionary.md) and is declared as an open type to allow arbitrary name-value pairs at runtime.

This type is used as the type of the **dynamicProperties** property on [auditData](https://learn.microsoft.com/en-us/graph/api/resources/security-auditdata?view=graph-rest-1.0), enabling dynamic properties in audit event payloads.

## Methods

None.

## Properties

None. This is an open type that accepts additional dynamic properties as name-value pairs at runtime.

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.security.auditRecordTypeDictionary"
}
```
