<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/requiredresourceaccess?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-12-26 -->

# requiredResourceAccess resource type

Namespace: microsoft.graph

Specifies the set of OAuth 2.0 permission scopes and app roles under the specified resource that an application requires access to. The [application](https://learn.microsoft.com/en-us/graph/api/resources/application?view=graph-rest-1.0) may request the specified OAuth 2.0 permission scopes or app roles through the **requiredResourceAccess** property, which is a collection of [requiredResourceAccess](https://learn.microsoft.com/en-us/graph/api/resources/requiredresourceaccess?view=graph-rest-1.0) objects.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| resourceAccess | [resourceAccess](https://learn.microsoft.com/en-us/graph/api/resources/resourceaccess?view=graph-rest-1.0) collection | The list of OAuth2.0 permission scopes and app roles that the application requires from the specified resource. |
| resourceAppId | String | The unique identifier for the resource that the application requires access to. This should be equal to the **appId** declared on the target resource application. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "resourceAccess": [
    {
      "@odata.type": "microsoft.graph.resourceAccess"
    }
  ],
  "resourceAppId": "String"
}
```
