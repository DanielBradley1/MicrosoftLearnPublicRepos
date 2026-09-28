<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/detailsinfo?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-07-04 -->

# detailsInfo resource type

Namespace: microsoft.graph

A property bag that can contain any information about the associated identity or system. This can include details about the property that is being provisioned or the source/target system.

This object is configured in the **details** property of the following resources:

- [provisionedIdentity](https://learn.microsoft.com/en-us/graph/api/resources/provisionedidentity?view=graph-rest-1.0)
- [provisioningStep](https://learn.microsoft.com/en-us/graph/api/resources/provisioningstep?view=graph-rest-1.0)
- [provisioningSystem](https://learn.microsoft.com/en-us/graph/api/resources/provisioningsystem?view=graph-rest-1.0)

## Properties

The **detailsInfo** resource is a JSON string that contains more properties such as **ApplicationId**, **ObjectId**, and **UPN**. The set of properties varies based on the type of resource that is being provisioned. [List provisioningObjectSummary](https://learn.microsoft.com/en-us/graph/api/provisioningobjectsummary-list?view=graph-rest-1.0) shows an example of this.

## Relationships

None

## JSON Representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "microsoft.graph.detailsInfo"
}
```
