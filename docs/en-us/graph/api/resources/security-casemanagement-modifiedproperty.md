<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/security-casemanagement-modifiedproperty?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-07-16 -->

# modifiedProperty resource type

Namespace: microsoft.graph.security.caseManagement

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents a property value change recorded in an [auditLog](https://learn.microsoft.com/en-us/graph/api/resources/security-casemanagement-auditlog?view=graph-rest-beta). Returned in the **modifiedProperties** property.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| newValue | [microsoft.graph.security.caseManagement.valueProperty](https://learn.microsoft.com/en-us/graph/api/resources/security-casemanagement-valueproperty?view=graph-rest-beta) | The new value after the change. |
| oldValue | [microsoft.graph.security.caseManagement.valueProperty](https://learn.microsoft.com/en-us/graph/api/resources/security-casemanagement-valueproperty?view=graph-rest-beta) | The previous value before the change. |
| propertyName | String | The name of the property that changed. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.security.caseManagement.modifiedProperty",
  "propertyName": "String",
  "oldValue": {
    "@odata.type": "#microsoft.graph.security.caseManagement.valueProperty"
  },
  "newValue": {
    "@odata.type": "#microsoft.graph.security.caseManagement.valueProperty"
  }
}
```
