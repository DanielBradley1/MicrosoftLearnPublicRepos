<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/cloudpcconnectionsettings?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-09-19 -->

# cloudPcConnectionSettings resource type \(deprecated\)

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

The connection settings of a Cloud PC. Currently, only **enableSingleSignOn** is supported. IT admins can enable it by updating the provisioning policy and calling [applyConfig](https://learn.microsoft.com/en-us/graph/api/cloudpcprovisioningpolicy-applyconfig?view=graph-rest-beta)/[apply](https://learn.microsoft.com/en-us/graph/api/cloudpcprovisioningpolicy-apply?view=graph-rest-beta) API.

Note

This resource type is deprecated and stopped returning data on August 31, 2024. Use [cloudPcConnectionSetting](https://learn.microsoft.com/en-us/graph/api/resources/cloudpcconnectionsetting?view=graph-rest-beta) instead.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| enableSingleSignOn | Boolean | Indicates whether single sign-on is enabled. The default value is `false`. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.cloudPcConnectionSettings",
  "enableSingleSignOn": false,
}
```
