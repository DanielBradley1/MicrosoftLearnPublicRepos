<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/sum/deploy-use/third-party-software-update-catalogs -->
<!-- Sitemap-Last-Modified: 2024-04-18 -->

# Available third-party software update catalogs

*Applies to: Configuration Manager \(current branch\)*

The **Third-Party Software Update Catalogs** node in the Configuration Manager console allows you to subscribe to third-party catalogs, publish their updates to your software update point \(SUP\), and then deploy them to clients. You can [add custom catalogs](https://learn.microsoft.com/en-us/intune/configmgr/sum/deploy-use/third-party-software-updates#add-a-custom-catalog) from third-party vendors.

## Third-party update catalogs available for import

To make it easier to find custom catalogs, we're providing a list of links as a convenience. Some catalogs are freely available and some catalogs have an additional cost associated with them. This list includes catalogs that may only work with [System Center Updates Publisher](https://learn.microsoft.com/en-us/intune/configmgr/sum/tools/updates-publisher) and not the **Third-Party Software Update Catalogs** node in the Configuration Manager console. Check with the catalog provider for details including pricing, support, and if the catalog supports in-console third-party updates.

|   <br>  <br>Custom catalog provider |   <br>  <br>URL |
| --- | --- |
| Adobe | Multiple catalogs are available from Adobe.  <br>[https://www.adobe.com/devnet-docs/acrobatetk/tools/DesktopDeployment/sccm.html](https://www.adobe.com/devnet-docs/acrobatetk/tools/DesktopDeployment/sccm.html) |
| Centero Software Manager | [https://docs.software-manager.com/docs/csm-for-sccm](https://docs.software-manager.com/docs/csm-for-sccm) |
| Dell | *Partner catalog* available in the **Third-Party Software Update Catalogs** node  <br>[https://www.dell.com/support/article/sln311138/](https://www.dell.com/support/article/sln311138/)  <br>  <br>[https://downloads.dell.com/Catalog/DellSDPCatalogPC.cab](https://downloads.dell.com/Catalog/DellSDPCatalogPC.cab)  <br>  <br>https://downloads.dell.com/Catalog/DellSDPCatalog.cab |
| Fujitsu | [https://support.ts.fujitsu.com/GFSMS/globalflash/FJSVUMCatalogForSCCM.cab](https://support.ts.fujitsu.com/GFSMS/globalflash/FJSVUMCatalogForSCCM.cab) |
| HP | *Partner catalog* available in the **Third-Party Software Update Catalogs** node  <br>[https://hpia.hpcloud.hp.com/downloads/sccmcatalog/HpCatalogForSms.latest.cab](https://hpia.hpcloud.hp.com/downloads/sccmcatalog/HpCatalogForSms.latest.cab)  <br>  <br>`http://ftp.hp.com/pub/softlib/software/sms_catalog/HpCatalogForSms.latest.cab` |
| Ivanti Patch for MEM | [https://www.ivanti.com.au/products/patch-management-for-mem](https://www.ivanti.com.au/products/patch-management-for-mem) |
| Lenovo | *Partner catalog* available in the **Third-Party Software Update Catalogs** node  <br>[https://download.lenovo.com/luc/v3/LenovoUpdatesCatalogv3.cab](https://download.lenovo.com/luc/v3/LenovoUpdatesCatalogv3.cab)  <br>  <br>Lenovo updates catalog V3 information  <br>[https://thinkdeploy.blogspot.com/2020/06/lenovo-updates-catalog-v3-for-sccm.html](https://thinkdeploy.blogspot.com/2020/06/lenovo-updates-catalog-v3-for-sccm.html)  <br>  <br>Lenovo Patch  <br>[https://www.lenovo.com/us/en/software/lenovo-patch-sccm](https://www.lenovo.com/us/en/software/lenovo-patch-sccm) |
| ManageEngine Patch Connect Plus | [https://www.manageengine.com/sccm-third-party-patch-management](https://www.manageengine.com/sccm-third-party-patch-management) |
| Patch My PC | Full catalog  <br>[https://patchmypc.com/third-party-patch-management-for-sccm-and-intune](https://patchmypc.com/third-party-patch-management-for-sccm-and-intune)  <br>  <br>Limited catalog  <br>[https://patchmypc.com/frequently-asked-questions#trial-catalog](https://patchmypc.com/frequently-asked-questions#trial-catalog) |
| SolarWinds Patch Manager | [https://www.solarwinds.com/patch-manager/use-cases/third-party-patch-management-sccm](https://www.solarwinds.com/patch-manager/use-cases/third-party-patch-management-sccm) |

## Open this article from the Configuration Manager console

Starting in Configuration Manager 2107, you can choose **More Catalogs** from the ribbon in the **Third-party software update catalogs** node to get to this article. Right-clicking on **Third-Party Software Update Catalogs** node displays a **More Catalogs** menu item. Selecting **More Catalogs** opens a link to this page.

![Screenshot of the Third-Party Software Update Catalogs node with the More Catalogs icon in the ribbon](https://learn.microsoft.com/en-us/intune/configmgr/sum/deploy-use/media/9989251-more-catalogs.png)

## Next steps

- [Add custom catalogs for third party software updates](https://learn.microsoft.com/en-us/intune/configmgr/sum/deploy-use/third-party-software-updates#add-a-custom-catalog)
- [Configure the SUP to synchronize the product](https://learn.microsoft.com/en-us/intune/configmgr/sum/get-started/configure-classifications-and-products#to-configure-classifications-and-products-to-synchronize) into Configuration Manager
