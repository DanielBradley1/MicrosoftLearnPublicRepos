<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/educationmoduleresource?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-07-26 -->

# educationModuleResource resource type

Namespace: microsoft.graph

A wrapper object that stores the resources associated with a module. The student isn't able to update this resource. This resource is a handout from the teacher to the student with nothing to be turned in.

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List module resources](https://learn.microsoft.com/en-us/graph/api/educationmodule-list-resources?view=graph-rest-1.0) | [educationModuleResource](https://learn.microsoft.com/en-us/graph/api/resources/educationmoduleresource?view=graph-rest-1.0) collection | Get an **educationModuleResource** object collection. |
| [Create module resource](https://learn.microsoft.com/en-us/graph/api/educationmodule-post-resources?view=graph-rest-1.0) | [educationModuleResource](https://learn.microsoft.com/en-us/graph/api/resources/educationmoduleresource?view=graph-rest-1.0) | Create and return an **educationModuleResource** object. |
| [Get module resource](https://learn.microsoft.com/en-us/graph/api/educationmoduleresource-get?view=graph-rest-1.0) | [educationModuleResource](https://learn.microsoft.com/en-us/graph/api/resources/educationmoduleresource?view=graph-rest-1.0) | Read properties and relationships of an **educationModuleResource** object. |
| [Update module resource](https://learn.microsoft.com/en-us/graph/api/educationmoduleresource-update?view=graph-rest-1.0) | [educationModuleResource](https://learn.microsoft.com/en-us/graph/api/resources/educationmoduleresource?view=graph-rest-1.0) | Update an **educationModuleResource** object. |
| [Delete resource from module](https://learn.microsoft.com/en-us/graph/api/educationmoduleresource-delete?view=graph-rest-1.0) | None | Delete an **educationModuleResource** object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | ID of this resource. Read-only. |
| resource | [educationResource](https://learn.microsoft.com/en-us/graph/api/resources/educationresource?view=graph-rest-1.0) | Resource object that is with this module. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "id": "String (identifier)",
  "resource": { "@odata.type": "microsoft.graph.educationResource" }
}
```
