<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/cloudpcdomainjoincredential?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-10-30 -->

# cloudPcDomainJoinCredential resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

An abstract type that represents an Active Directory domain join credential for a [Cloud PC Azure network connection](https://learn.microsoft.com/en-us/graph/api/resources/cloudpconpremisesconnection?view=graph-rest-beta).

This abstract type can't be instantiated directly. Use the [cloudPcPlainTextDomainJoinCredential](https://learn.microsoft.com/en-us/graph/api/resources/cloudpcplaintextdomainjoincredential?view=graph-rest-beta) or [cloudPcKeyVaultDomainJoinCredential](https://learn.microsoft.com/en-us/graph/api/resources/cloudpckeyvaultdomainjoincredential?view=graph-rest-beta) derived type, identified by the **@odata.type** property.

## Properties

None.

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.cloudPcDomainJoinCredential"
}
```
