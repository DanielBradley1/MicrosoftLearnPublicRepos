<!-- Source: https://learn.microsoft.com/en-us/intune/developer/data-warehouse/create-reports -->
<!-- Sitemap-Last-Modified: 2026-04-22 -->

# Use the Microsoft Intune Data Warehouse

Important

The Intune Data Warehouse \(beta\) connector in Power BI \(connector v1\) is being retired. If your Power BI reports use connector v1, migrate to the Intune connector v2 or OData Feed connector. For migration steps, see [Connect to the Data Warehouse with Power BI](https://learn.microsoft.com/en-us/intune/developer/data-warehouse/connect-power-bi#migrate-from-connector-v1).

Use the Intune Data Warehouse to build reports that provide insight into your enterprise mobile environment. For example, some of the reports include:

- Trend of users enrolling in Intune so you can optimize your license purchases
- App and OS versions breakdown so you can review that status of mobile devices
- Enrollment and device compliance trends so you can smoothly roll out policy updates

## Data Warehouse benefits

The Data Warehouse provides you access to more information about your mobile environment than the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431). With the Intune Data Warehouse you can access:

- Historical Intune data
- Data refreshed on a daily cadence
- A data model using the OData standard

Note

If you are a using co-managed mobile device management \(MDM\) with Microsoft Configuration Manager and Microsoft Intune, you need to retrieve your data from Configuration Manager. The Intune Data Warehouse only contains Intune data. You can use a Configuration Manager Power BI dashboard for your custom reports. For related information, see [Power BI Desktop](https://learn.microsoft.com/en-us/configmgr/develop/adminservice/usage#power-bi-desktop).

Important

You can now use the v1.0 version of the Intune Data Warehouse by setting the query parameter `api-version=v1.0`. Updates to collections in the Data Warehouse are additive in nature and do not break existing scenarios.  
  
You can try out the latest functionality of the Data Warehouse by using the beta version. To use the beta version, your URL must contain the query parameter `api-version=beta`. The beta version offers features before they are made generally available as a supported service. As Intune adds new features, the beta version may change behavior and data contracts. Any custom code or reporting tools dependent on the beta version may break with ongoing updates.

## Next steps

- Get a link and use Power BI to get insight. For instructions, see [Connect to the Intune Data Warehouse with Power BI](https://learn.microsoft.com/en-us/intune/developer/data-warehouse/connect-power-bi).
- With your link, create a custom report with Power BI. For instructions, see [Create a report from the OData feed with Power BI](https://learn.microsoft.com/en-us/intune/developer/data-warehouse/create-report-odata).
- Get more information about the Intune Data Warehouse API, the data model, and relationships between entities see [Intune Data Warehouse API](https://learn.microsoft.com/en-us/intune/developer/data-warehouse/).
