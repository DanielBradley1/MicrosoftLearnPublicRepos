<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/domaindnscnamerecord?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-04-25 -->

# domainDnsCnameRecord resource type

Namespace: microsoft.graph

Represents a CNAME record added to the DNS zone file of a particular domain in the tenant. Inherited from [DomainDnsRecord](https://learn.microsoft.com/en-us/graph/api/resources/domaindnsrecord?view=graph-rest-1.0) entity.

## Methods

Direct queries to this resource aren't supported. See the [domain](https://learn.microsoft.com/en-us/graph/api/resources/domain?view=graph-rest-1.0) article for information on how to query for domain service records.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| canonicalName | String | The canonical name of the CNAME record. Used to configure the CNAME record at the DNS host. |
| id | String | Unique identifier assigned to this entity. Not nullable, Read-only |
| isOptional | Boolean | If false, the CNAME record must be configured by the customer at the DNS host for Microsoft Online Services to operate correctly with the domain. Not nullable |
| label | String | Value used when configuring the *alias/host/name* of the CNAME record at the DNS host. |
| recordType | String | Type of DNS record. The value is always *CName*. Key |
| supportedService | String | Microsoft Online Service or feature that has a dependency on this CNAME record. Can be one of the following values: **null**, *Email*, *Sharepoint*, *EmailInternalRelayOnly*, *OfficeCommunicationsOnline*, *SharePointDefaultDomain*, *FullRedelegation*, *SharePointPublic*, *OrgIdAuthentication*, *Yammer*, *Intune* |
| ttl | Int32 | Value to use when configuring the time-to-live \(ttl\) property of the CNAME record at the DNS host. Not nullable |

## Relationships

None

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "canonicalName": "String",
  "id": "String (identifier)",
  "isOptional": true,
  "label": "String",
  "recordType": "String",
  "supportedService": "String",
  "ttl": 1024
}
```
