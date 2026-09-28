<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/domaindnsrecord?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-04-26 -->

# domainDnsRecord resource type

Namespace: microsoft.graph

For each [domain](https://learn.microsoft.com/en-us/graph/api/resources/domain?view=graph-rest-1.0) in the tenant, you may be required to add DNS records to the DNS zone file of the domain before the domain can be used by Microsoft Online Services. These DNS records are represented.

The **domainDnsRecord** resource type is used to present such DNS records as exposed through the **serviceConfigurationRecords** and **verificationDnsRecords**. This resource type is the base entity for the following resources:

- [domainDnsCnameRecord](https://learn.microsoft.com/en-us/graph/api/resources/domaindnscnamerecord?view=graph-rest-1.0)
- [domainDnsMxRecord](https://learn.microsoft.com/en-us/graph/api/resources/domaindnsmxrecord?view=graph-rest-1.0)
- [domainDnsSrvRecord](https://learn.microsoft.com/en-us/graph/api/resources/domaindnssrvrecord?view=graph-rest-1.0)
- [domainDnsTxtRecord](https://learn.microsoft.com/en-us/graph/api/resources/domaindnstxtrecord?view=graph-rest-1.0)
- [domainDnsUnavailableRecord](https://learn.microsoft.com/en-us/graph/api/resources/domaindnsunavailablerecord?view=graph-rest-1.0)

## Methods

None.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | Unique identifier assigned to this entity. Not nullable, Read-only. |
| isOptional | Boolean | If `false`, the customer must configure this record at the DNS host for Microsoft Online Services to operate correctly with the domain. |
| label | String | Value used when configuring the name of the DNS record at the DNS host. |
| recordType | String | Indicates what type of DNS record this entity represents. The value can be `CName`, `Mx`, `Srv`, or `Txt`. |
| supportedService | String | Microsoft Online Service or feature that has a dependency on this DNS record. Can be one of the following values: `null`, `Email`, `Sharepoint`, `EmailInternalRelayOnly`, `OfficeCommunicationsOnline`, `SharePointDefaultDomain`, `FullRedelegation`, `SharePointPublic`, `OrgIdAuthentication`, `Yammer`, `Intune`. |
| ttl | Int32 | Value to use when configuring the time-to-live \(ttl\) property of the DNS record at the DNS host. Not nullable. |

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
  "ttl": 1024
}
```
