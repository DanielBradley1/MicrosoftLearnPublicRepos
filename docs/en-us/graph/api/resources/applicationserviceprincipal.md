<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/applicationserviceprincipal?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-07-23 -->

# applicationServicePrincipal resource type

Namespace: microsoft.graph

When an instance of an application from the Microsoft Entra application gallery is added, [application](https://learn.microsoft.com/en-us/graph/api/resources/application?view=graph-rest-1.0) and [servicePrincipal](https://learn.microsoft.com/en-us/graph/api/resources/serviceprincipal?view=graph-rest-1.0) objects are created in the directory. The **applicationServicePrincipal** represents the concatenation of the **application** and **servicePrincipal** object.

## Methods

None

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| application | [application](https://learn.microsoft.com/en-us/graph/api/resources/application?view=graph-rest-1.0) | Represents an application registered in Microsoft Entra ID. |
| servicePrincipal | [servicePrincipal](https://learn.microsoft.com/en-us/graph/api/resources/serviceprincipal?view=graph-rest-1.0) | Represents an instance of an application in a directory. |

## Relationships

None

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "application": { "@odata.type": "microsoft.graph.application" },
  "servicePrincipal": { "@odata.type": "microsoft.graph.servicePrincipal" }
}
```
