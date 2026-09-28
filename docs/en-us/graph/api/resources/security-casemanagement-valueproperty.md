<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/security-casemanagement-valueproperty?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-07-16 -->

# valueProperty resource type

Namespace: microsoft.graph.security.caseManagement

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents the abstract base type for values in a [modifiedProperty](https://learn.microsoft.com/en-us/graph/api/resources/security-casemanagement-modifiedproperty?view=graph-rest-beta). Returned in the **oldValue** and **newValue** properties. Use derived types such as [stringValueProperty](https://learn.microsoft.com/en-us/graph/api/resources/security-casemanagement-stringvalueproperty?view=graph-rest-beta) or [booleanValueProperty](https://learn.microsoft.com/en-us/graph/api/resources/security-casemanagement-booleanvalueproperty?view=graph-rest-beta) for concrete value payloads.

## Properties

None.

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.security.caseManagement.valueProperty"
}
```
