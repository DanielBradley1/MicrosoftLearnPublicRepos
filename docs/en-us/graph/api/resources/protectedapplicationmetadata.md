<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/protectedapplicationmetadata?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-09-04 -->

# protectedApplicationMetadata resource type

Namespace: microsoft.graph

Represents metadata about an application whose activities governed by an integrated application.

Inhertits from [integratedApplicationMetadata](https://learn.microsoft.com/en-us/graph/api/resources/integratedapplicationmetadata?view=graph-rest-1.0).

For internal use only. Don't use.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| applicationLocation | [policyLocation](https://learn.microsoft.com/en-us/graph/api/resources/policylocation?view=graph-rest-1.0) | The client \(application\) ID of the Microsoft Entra application. Required. |
| name | String | The name of the integrated application. Inherited from [integratedApplicationMetadata](https://learn.microsoft.com/en-us/graph/api/resources/integratedapplicationmetadata?view=graph-rest-1.0). |
| version | String | The version number of the integrated application. Inherited from [integratedApplicationMetadata](https://learn.microsoft.com/en-us/graph/api/resources/integratedapplicationmetadata?view=graph-rest-1.0). |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.protectedApplicationMetadata",
  "applicationLocation": {
    "@odata.type": "#microsoft.graph.policyLocation",
    "location": "String"
  }
}
```
