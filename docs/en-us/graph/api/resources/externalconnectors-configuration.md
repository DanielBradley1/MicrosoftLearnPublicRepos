<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/externalconnectors-configuration?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-12-06 -->

# configuration resource type

Namespace: microsoft.graph.externalConnectors

Specifies additional application IDs that are allowed to manage the externalConnection and to index content in a [externalConnection](https://learn.microsoft.com/en-us/graph/api/resources/externalconnectors-externalconnection?view=graph-rest-1.0).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| authorizedAppIds | String collection | A collection of application IDs for registered Microsoft Entra apps that are allowed to manage the externalConnection and to index content in the externalConnection. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "authorizedAppIds": [
    "String"
  ]
}
```
