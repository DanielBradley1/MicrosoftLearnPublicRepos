<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/educationroot?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-09-25 -->

# educationRoot resource type

Namespace: microsoft.graph

The `/education` namespace exposes functionality that is specific to the education sector. Some objects in the `/education` namespace can be found in other parts of Microsoft Graph \(for example, [users](https://learn.microsoft.com/en-us/graph/api/resources/user?view=graph-rest-1.0)\). The education namespace provides education-specific properties and features on these objects.

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List classes](https://learn.microsoft.com/en-us/graph/api/educationclass-list?view=graph-rest-1.0) | [educationClass](https://learn.microsoft.com/en-us/graph/api/resources/educationclass?view=graph-rest-1.0) collection | Get an **educationClass** object collection. |
| [Create class](https://learn.microsoft.com/en-us/graph/api/educationclass-post?view=graph-rest-1.0) | [educationClass](https://learn.microsoft.com/en-us/graph/api/resources/educationclass?view=graph-rest-1.0) | Create a new **educationClass** by posting to the classes collection. |
| [List schools](https://learn.microsoft.com/en-us/graph/api/educationschool-list?view=graph-rest-1.0) | [educationSchool](https://learn.microsoft.com/en-us/graph/api/resources/educationschool?view=graph-rest-1.0) collection | Get an **educationSchool** object collection. |
| [Create school](https://learn.microsoft.com/en-us/graph/api/educationschool-post?view=graph-rest-1.0) | [educationSchool](https://learn.microsoft.com/en-us/graph/api/resources/educationschool?view=graph-rest-1.0) | Create a new **educationSchool** by posting to the schools collection. |
| [List users](https://learn.microsoft.com/en-us/graph/api/educationuser-list?view=graph-rest-1.0) | [educationUser](https://learn.microsoft.com/en-us/graph/api/resources/educationuser?view=graph-rest-1.0) collection | Get an **educationUser** object collection. |
| [Create user](https://learn.microsoft.com/en-us/graph/api/educationuser-post?view=graph-rest-1.0) | [educationUser](https://learn.microsoft.com/en-us/graph/api/resources/educationuser?view=graph-rest-1.0) | Create a new **educationUser** by posting to the users collection. |

## Properties

None.

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| classes | [educationClass](https://learn.microsoft.com/en-us/graph/api/resources/educationclass?view=graph-rest-1.0) collection | Classes taught at the school. Nullable. |
| me | [educationUser](https://learn.microsoft.com/en-us/graph/api/resources/educationuser?view=graph-rest-1.0) | Represents a user in the system. Nullable. |
| reports | [reportsRoot](https://learn.microsoft.com/en-us/graph/api/resources/reportsroot?view=graph-rest-1.0) | A container for all endpoints related to education analytics reports. Read-only. Nullable. |
| schools | [educationSchool](https://learn.microsoft.com/en-us/graph/api/resources/educationschool?view=graph-rest-1.0) collection | Schools to which the user belongs. Nullable. |
| users | [educationUser](https://learn.microsoft.com/en-us/graph/api/resources/educationuser?view=graph-rest-1.0) collection | Users in the school. Nullable. |
