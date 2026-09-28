<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/plannerexternalreferences?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-07-26 -->

# plannerExternalReferences resource type

Namespace: microsoft.graph

The **plannerExternalReferences** resource represents the collection of references on a task. This is an Open Type. It's part of the [task details](https://learn.microsoft.com/en-us/graph/api/resources/plannertaskdetails?view=graph-rest-1.0) object. The value in the property-value pair is the [externalReference](https://learn.microsoft.com/en-us/graph/api/resources/plannerexternalreference?view=graph-rest-1.0) object.

## Properties

Properties of an Open Type can be defined by the client. In this case, the client must provide **valid URLs** based on the **HTTP/HTTPS** protocols as properties and their values must be the [externalReference](https://learn.microsoft.com/en-us/graph/api/resources/plannerexternalreference?view=graph-rest-1.0) objects. Based on OData, property names in Open Types can't contain the following characters: `.`, `:`, `%`, `@`, `#` so they need to be encoded. Example is shown below. To remove a reference, set the value of the property to `null`.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "String-value":
  {
    "alias": "String-value",
    "lastModifiedBy": "String-value",
    "lastModifiedDateTime": "String(timestamp)",
    "previewPriority": "String-value",
    "type": "String-value"
  }
}
```

## Example

```json
{
  "https%3A//contoso%2Esharepoint%2Ecom/teams/agile/documents/AnnualReport%2Epptx":
  {
    "@odata.type": "microsoft.graph.externalReference", // required in PATCH requests to edit the references on a task
    "alias": "Agile Team Annual Report",
    "lastModifiedBy": {
      "user": {
        "id": "ebf3b108-5234-4e22-b93d-656d7dae5874"
      }
    },
    "lastModifiedDateTime": "2015-09-21T17:45:12.039Z",
    "previewPriority": "0009005756397228702",
    "type": "PowerPoint"
  }
}
```
