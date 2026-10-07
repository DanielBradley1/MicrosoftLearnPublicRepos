<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/core/clients/manage/asset-intelligence/deprecation -->
<!-- Sitemap-Last-Modified: 2026-09-28 -->

# Asset intelligence deprecation

*Applies to: Configuration Manager \(current branch\)*

Starting in November 2021, the asset intelligence feature of Configuration Manager is [deprecated](https://learn.microsoft.com/en-us/intune/configmgr/core/plan-design/changes/deprecated/removed-and-deprecated-cmfeatures). This article provides more detail about the specific functional areas of asset intelligence that are deprecated or still supported.

Important

Starting in version 2609, the built-in Asset Intelligence reports are removed from the **Monitoring > Reporting > Reports** node. References to these reports in this article apply to version 2603 and earlier.

## Deprecated functionality

The following functional areas are deprecated and may be removed in a future version. Support for these areas will end November 2022.

- The [asset intelligence catalog](https://learn.microsoft.com/en-us/intune/configmgr/core/clients/manage/asset-intelligence/introduction-to-asset-intelligence#BKMK_AssetIntelligenceCatalog), which includes the following functionality:

  - Cloud updates to the predefined software title information such as product name and vendor
  - Cloud updates to the predefined [software categories](https://learn.microsoft.com/en-us/intune/configmgr/core/clients/manage/asset-intelligence/introduction-to-asset-intelligence#BKMK_SoftwareCategories) and [software families](https://learn.microsoft.com/en-us/intune/configmgr/core/clients/manage/asset-intelligence/introduction-to-asset-intelligence#BKMK_SoftwareFamilies) and the associated SQL views and reports
  - Cloud updates to the predefined [hardware requirements](https://learn.microsoft.com/en-us/intune/configmgr/core/clients/manage/asset-intelligence/introduction-to-asset-intelligence#BKMK_HardwareRequirements) for software titles and the associated SQL views and reports

- The [asset intelligence synchronization point](https://learn.microsoft.com/en-us/intune/configmgr/core/clients/manage/asset-intelligence/introduction-to-asset-intelligence#AssetIntelligenceSycnronizationPoint), which includes the following functionality:

  - Catalog synchronization
  - The ability to [request catalog updates](https://learn.microsoft.com/en-us/intune/configmgr/core/clients/manage/asset-intelligence/operations-for-asset-intelligence#BKMK_RequestCatalogUpdate) for uncategorized software

- The [Microsoft Volume License import and reconciliation](https://learn.microsoft.com/en-us/intune/configmgr/core/clients/manage/asset-intelligence/configuring-asset-intelligence#BKMK_ImportSoftwareLicenseInformation) including the associated SQL views and reports

## Supported functionality

The following functional areas aren't currently included in the deprecation and will remain supported:

- The [inventoried software titles](https://learn.microsoft.com/en-us/intune/configmgr/core/clients/manage/asset-intelligence/introduction-to-asset-intelligence#BKMK_InventoriedSoftwareTitles), which includes the following functionality:

  - [Asset intelligence hardware inventory reporting WMI classes](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/client-classes/asset-intelligence-client-wmi-classes)
  - The associated SQL views:

    - [Asset intelligence hardware inventory views](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/sqlviews/asset-intelligence-views-configuration-manager#asset-intelligence-hardware-inventory-views)
    - [Asset intelligence status view](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/sqlviews/asset-intelligence-views-configuration-manager#asset-intelligence-status-view)

  - The associated reports

- The [product lifecycle dashboard](https://learn.microsoft.com/en-us/intune/configmgr/core/clients/manage/asset-intelligence/product-lifecycle-dashboard) and its associated reports
- The [General License Statement import and reconciliation](https://learn.microsoft.com/en-us/intune/configmgr/core/clients/manage/asset-intelligence/configuring-asset-intelligence#BKMK_CreateGeneralLicenseStatement) and the associated SQL views and reports
- The ability to view the asset intelligence inventory in the console from the **Inventoried Software** node
- The existing static, predefined software title information provided with setup for new and existing sites:

  - Product name
  - Vendor
  - Product category
  - Product family
  - Hardware requirement

- The ability to customize the inventoried software title information such as the product name and vendor
- The ability to add custom software categories, families, and labels to inventoried software titles
- The ability for an administrator to add custom hardware requirements to inventoried software titles

## References

[Asset intelligence reports](https://learn.microsoft.com/en-us/intune/configmgr/core/servers/manage/list-of-reports#asset-intelligence)

[Asset intelligence client WMI classes](https://learn.microsoft.com/en-us/intune/configmgr/develop/reference/core/clients/client-classes/asset-intelligence-client-wmi-classes)

[Asset intelligence views](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/sqlviews/asset-intelligence-views-configuration-manager)
