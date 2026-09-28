<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/plannerchecklistitems?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-08-10 -->

# plannerChecklistItems resource type

Namespace: microsoft.graph

Represents the collection of checklist items on a task. This complex type is an open type that's part of the [task details](https://learn.microsoft.com/en-us/graph/api/resources/plannertaskdetails?view=graph-rest-1.0) object. The value in the property-value pair is the [checklistItem](https://learn.microsoft.com/en-us/graph/api/resources/plannerchecklistitem?view=graph-rest-1.0) object.

## Properties

Properties of an open type can be defined by the client. In this case, the client should provide **GUIDs** as properties and their values must be [checklistItem](https://learn.microsoft.com/en-us/graph/api/resources/plannerchecklistitem?view=graph-rest-1.0) objects. To remove an item in the checklist, set the value of the property to `null`.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "String-value":
  {
    "@odata.type": "microsoft.graph.plannerChecklistItem",
    "isChecked": true,
    "lastModifiedBy": {"@odata.type": "microsoft.graph.identitySet"},
    "lastModifiedByDateTime": "String(timestamp)",
    "orderHint": "String-value",
    "title": "String-value"
  }
}
```
