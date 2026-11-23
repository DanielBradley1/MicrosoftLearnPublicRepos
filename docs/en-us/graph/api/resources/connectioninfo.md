<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/connectioninfo?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-08-20 -->

# connectionInfo resource type

Namespace: microsoft.graph

The connectionInfo object defines the resource locator that is used to communicate with a resource in Microsoft Entra Entitlement Management.

The following types are derived from connectionInfo:

- [externalTokenBasedSapIagConnectionInfo](https://learn.microsoft.com/en-us/graph/api/resources/externaltokenbasedsapiagconnectioninfo?view=graph-rest-1.0)

In entitlement management, this object is configured in the following properties and relationships:

- **connectionInfo** property of [accessPackageResourceEnvironment](https://learn.microsoft.com/en-us/graph/api/resources/accesspackageresourceenvironment?view=graph-rest-1.0)
- **connectionInfo** property of [externalOriginResourceConnector](https://learn.microsoft.com/en-us/graph/api/resources/externaloriginresourceconnector?view=graph-rest-1.0)

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| url | String | The endpoint that is used by Entitlement Management to communicate with the access package resource. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.connectionInfo",
  "url": "String"
}
```
