<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/enumerateddomains?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-03-06 -->

# enumeratedDomains resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

A derived complex type that defines the specified domains that Microsoft Entra ID validates.

Inherits from [validatingDomains](https://learn.microsoft.com/en-us/graph/api/resources/validatingdomains?view=graph-rest-beta).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| domainNames | String collection | List of federated or managed root domains that Microsoft Entra ID validates. |
| rootDomains | rootDomains | Defines the types of domains that Microsoft Entra ID validates. Inherited from [validatingDomains](https://learn.microsoft.com/en-us/graph/api/resources/validatingdomains?view=graph-rest-beta). The possible values are: `none`, `all`, `allFederated`, `allManaged`, `enumerated`, `allManagedAndEnumeratedFederated`, `unknownFutureValue`. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.enumeratedDomains",
  "rootDomains": "String",
  "domainNames": [
    "String"
  ]
}
```
