<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/resulttemplate?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-08-09 -->

# resultTemplate resource type

Namespace: microsoft.graph

Represents a dictionary of **resultTemplateIds** and associated values, which includes the name and JSON schema of the result templates.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| body | Json | JSON schema of the result template. |
| displayName | String | Name of the result template. |
| key | String | ID of a result template. The **key** property must map to a **resultTemplateId** in the [searchHit](https://learn.microsoft.com/en-us/graph/api/resources/searchhit?view=graph-rest-1.0) collection. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
    "displayName": "String",
     "body":{
         "@odata.type":"microsoft.graph.Json"
      }
}
```
