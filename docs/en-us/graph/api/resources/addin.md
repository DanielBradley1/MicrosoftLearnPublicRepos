<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/addin?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-12-26 -->

# addIn resource type

Namespace: microsoft.graph

Defines custom behavior that a consuming service can use to call an app in specific contexts. For example, applications that can render file streams [may configure addIns](https://learn.microsoft.com/en-us/onedrive/developer/file-handlers/) for its "FileHandler" functionality. The addIn resource type lets services like Microsoft 365 call the application in the context of a document the user is working on.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | GUID | The unique identifier for the **addIn** object. |
| properties | [keyValue](https://learn.microsoft.com/en-us/graph/api/resources/keyvalue?view=graph-rest-1.0) collection | The collection of key-value pairs that define parameters that the consuming service can use or call. You must specify this property when performing a POST or a PATCH operation on the **addIns** collection. Required. |
| type | string | The unique name for the functionality exposed by the app. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "id": "Guid",
  "properties": [{"@odata.type": "microsoft.graph.keyValue"}],
  "type": "String"
}
```
