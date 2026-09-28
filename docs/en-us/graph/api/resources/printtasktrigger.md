<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/printtasktrigger?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-05-24 -->

# printTaskTrigger resource type

Namespace: microsoft.graph

Determines the condition under which a new [printTask](https://learn.microsoft.com/en-us/graph/api/resources/printtask?view=graph-rest-1.0) will be triggered based on the associated [printTaskDefinition](https://learn.microsoft.com/en-us/graph/api/resources/printtaskdefinition?view=graph-rest-1.0).

For details about how to use this resource to add pull printing support to Universal Print, see [Extending Universal Print to support pull printing](https://learn.microsoft.com/en-us/graph/universal-print-concept-overview#extending-universal-print-to-support-pull-printing).

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [List task triggers](https://learn.microsoft.com/en-us/graph/api/printer-list-tasktriggers?view=graph-rest-1.0) | [printTaskTrigger](https://learn.microsoft.com/en-us/graph/api/resources/printtasktrigger?view=graph-rest-1.0) collection | Get a list of printTaskTriggers associated with a particular [printer](https://learn.microsoft.com/en-us/graph/api/resources/printer?view=graph-rest-1.0). |
| [Get task trigger](https://learn.microsoft.com/en-us/graph/api/printtasktrigger-get?view=graph-rest-1.0) | [printTaskTrigger](https://learn.microsoft.com/en-us/graph/api/resources/printtasktrigger?view=graph-rest-1.0) | Get the printTaskTrigger associated with a particular [printTask](https://learn.microsoft.com/en-us/graph/api/resources/printtask?view=graph-rest-1.0). |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| event | printEvent | The Universal Print event that causes a new [printTask](https://learn.microsoft.com/en-us/graph/api/resources/printtask?view=graph-rest-1.0) to be triggered. Valid values are described in the following table. |
| id | String | The printTaskTrigger's identifier. Read-only. |

### printEvent values

| Member | Value | Description |
| :--- | :--- | :--- |
| jobStarted | 0 | Represents an event that occurs when a new print job is started. |
| unknownFutureValue | 1 | Evolvable enumeration sentinel value. Don't use. |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| definition | [printTaskDefinition](https://learn.microsoft.com/en-us/graph/api/resources/printtaskdefinition?view=graph-rest-1.0) | An abstract definition that is used to create a [printTask](https://learn.microsoft.com/en-us/graph/api/resources/printtask?view=graph-rest-1.0) when triggered by a print event. Read-only. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.printTaskTrigger",
  "id": "String (identifier)",
  "event": "String"
}
```
