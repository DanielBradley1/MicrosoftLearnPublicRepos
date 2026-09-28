<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/cloudpctenantencryptionsetting?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-12-03 -->

# cloudPcTenantEncryptionSetting resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents the Cloud PC encryption setting for a tenant. Only one encryption setting can be applied to the tenant.

## Methods

None.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| tenantDiskEncryptionType | [cloudPcDiskEncryptionType](#cloudpcdiskencryptiontype-values) | Indicates the Cloud PC disk encryption type for a tenant. It is a tenant-level setting that applies globally to all Cloud PCs in the tenant. The possible values are: `platformManagedKey`, `customerManagedKey`, `unknownFutureValue`. Read-only. |
| lastSyncDateTime | DateTimeOffset | Indicates the date and time when last sync tenant encryption setting. |

### cloudPcDiskEncryptionType values

| Member | Description |
| :--- | :--- |
| platformManagedKey | Default. The Cloud PC disk is encrypted with a platform-managed key. |
| customerManagedKey | Indicates that the Cloud PC disk is encrypted with a customer-managed key. |
| unknownFutureValue | Evolvable enumeration sentinel value. Don't use. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.cloudPcTenantEncryptionSetting",
  "tenantDiskEncryptionType": "customerManagedKey",
}
```
