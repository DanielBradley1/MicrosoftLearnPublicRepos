<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/domaindnstxtrecord?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-05-15 -->

# domainDnsTxtRecord resource type

Namespace: microsoft.graph

Represents a TXT record added to the DNS zone file of a particular domain in the tenant. Inherited from [DomainDnsRecord](https://learn.microsoft.com/en-us/graph/api/resources/domaindnsrecord?view=graph-rest-1.0) entity.

## Methods

Direct queries to this resource aren't supported. See the [domain](https://learn.microsoft.com/en-us/graph/api/resources/domain?view=graph-rest-1.0) article for information on how to query for domain service records.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | Unique identifier assigned to this entity. Not nullable, Read-only. |
| isOptional | Boolean | If false, the TXT record must be configured by the customer at the DNS host for Microsoft Online Services to operate correctly with the domain. |
| label | String | Value to use when configuring the *name* property of the TXT record at the DNS host. |
| recordType | String | Type of DNS record. The value is always *Txt*. Key |
| supportedService | String | Microsoft Online Service or feature that has a dependency on this TXT record. Can be one of the following values: **null**, *Email*, *Sharepoint*, *EmailInternalRelayOnly*, *OfficeCommunicationsOnline*, *SharePointDefaultDomain*, *FullRedelegation*, *SharePointPublic*, *OrgIdAuthentication*, *Yammer*, *Intune* |
| text | String | Value used when configuring the *text* property at the DNS host. |
| ttl | Int32 | Value to use when configuring the *time-to-live \(ttl\)* property of the MX record at the DNS host. Not nullable |

## Relationships

None

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "id": "String (identifier)",
  "isOptional": true,
  "label": "String",
  "recordType": "String",
  "supportedService": "String",
  "text": "String",
  "ttl": 1024
}
```
