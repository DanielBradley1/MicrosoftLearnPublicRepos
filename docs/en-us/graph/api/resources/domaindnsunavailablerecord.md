<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/domaindnsunavailablerecord?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-05-15 -->

# domainDnsUnavailableRecord resource type

Namespace: microsoft.graph

When you query for the navigation property **serviceConfigurationRecords** for a [Domain](https://learn.microsoft.com/en-us/graph/api/resources/domain?view=graph-rest-1.0) entity, you may get back one or more [DomainDnsCnameRecord](https://learn.microsoft.com/en-us/graph/api/resources/domaindnscnamerecord?view=graph-rest-1.0), [DomainDnsMxRecord](https://learn.microsoft.com/en-us/graph/api/resources/domaindnsmxrecord?view=graph-rest-1.0), [DomainDnsSrvRecord](https://learn.microsoft.com/en-us/graph/api/resources/domaindnssrvrecord?view=graph-rest-1.0), and/or [DomainDnsTxtRecord](https://learn.microsoft.com/en-us/graph/api/resources/domaindnstxtrecord?view=graph-rest-1.0) entities. These entities indicate what DNS records you must add to the zone file of the domain, before the domain can be used by Microsoft Online Services. When it isn't possible to generate such entities, a DomainDnsUnavailableRecord Entity is returned instead. Inherited from [DomainDnsRecord](https://learn.microsoft.com/en-us/graph/api/resources/domaindnsrecord?view=graph-rest-1.0) entity.

## Methods

Direct queries to this resource aren't supported. See the [domain](https://learn.microsoft.com/en-us/graph/api/resources/domain?view=graph-rest-1.0) article for information on how to query for domain service records.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| description | String | Provides the reason why the **DomainDnsUnavailableRecord** entity is returned. |

## Relationships

None

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "description": "String"
}
```
