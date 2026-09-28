<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/security-casemanagement-customfieldvalue?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-07-16 -->

# customFieldValue resource type

Namespace: microsoft.graph.security.caseManagement

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents the abstract base type for values in [customFieldValues](https://learn.microsoft.com/en-us/graph/api/resources/security-casemanagement-customfieldvalues?view=graph-rest-beta), which is returned in the **customFields** property of a [case](https://learn.microsoft.com/en-us/graph/api/resources/security-casemanagement-case?view=graph-rest-beta). Use derived types such as [customFieldStringValue](https://learn.microsoft.com/en-us/graph/api/resources/security-casemanagement-customfieldstringvalue?view=graph-rest-beta), [customFieldNumberValue](https://learn.microsoft.com/en-us/graph/api/resources/security-casemanagement-customfieldnumbervalue?view=graph-rest-beta), [customFieldDateTimeValue](https://learn.microsoft.com/en-us/graph/api/resources/security-casemanagement-customfielddatetimevalue?view=graph-rest-beta), or [customFieldOptionsValue](https://learn.microsoft.com/en-us/graph/api/resources/security-casemanagement-customfieldoptionsvalue?view=graph-rest-beta) for concrete value payloads.

## Properties

None.

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.security.caseManagement.customFieldValue"
}
```
