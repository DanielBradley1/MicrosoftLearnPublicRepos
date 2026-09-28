<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/externalconnectors-external?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-05-07 -->

# external resource type

Namespace: microsoft.graph.externalConnectors

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Note

Effective April 1, 2025, Microsoft Entra Permissions Management will no longer be available for purchase, and on October 1, 2025, we'll retire and discontinue support of this product. More information can be found [here](https://aka.ms/MEPMretire).

The base container for resource types such as the industry data ETL and Microsoft Entra Permissions Management for interacting with external data sources.

## Methods

None.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | Identifier for the object. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta). |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| authorizationSystems | [microsoft.graph.authorizationSystem](https://learn.microsoft.com/en-us/graph/api/resources/authorizationsystem?view=graph-rest-beta) collection | Represents an onboarded Amazon Web Services \(AWS\) account, Azure subscription, or Google Cloud Platform \(GCP\) project that Microsoft Entra Permissions Management collects and analyzes permissions and actions on. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.externalConnectors.external"
}
```
