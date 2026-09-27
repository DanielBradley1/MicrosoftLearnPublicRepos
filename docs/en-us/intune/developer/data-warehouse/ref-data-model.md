<!-- Source: https://learn.microsoft.com/en-us/intune/developer/data-warehouse/ref-data-model -->
<!-- Sitemap-Last-Modified: 2026-04-08 -->

# Microsoft Intune Data Warehouse Data Model

The Intune Data Warehouse samples data daily to provide a historical view of your continually changing environment of mobile devices. The view is composed of related entities in time.

## Entities: Entity sets

The warehouse exposes data in the following high-level areas:

- App protection enabled apps and usage
- Enrolled devices, properties, and inventory
- Apps and software inventory
- Device configuration and compliance policies

These areas contain the entities that are meaningful to your Intune environment. You find details about the entity sets in the following topics:

- [Application](https://learn.microsoft.com/en-us/intune/developer/data-warehouse/ref-application)
- [Date](https://learn.microsoft.com/en-us/intune/developer/data-warehouse/ref-date)
- [Devices](https://learn.microsoft.com/en-us/intune/developer/data-warehouse/ref-devices)
- [Intune Management Extension](https://learn.microsoft.com/en-us/intune/developer/data-warehouse/ref-intune-management-extension)
- [Policy](https://learn.microsoft.com/en-us/intune/developer/data-warehouse/ref-policy)
- [Mobile App Management \(MAM\)](https://learn.microsoft.com/en-us/intune/app-management/overview)
- [User](https://learn.microsoft.com/en-us/intune/developer/data-warehouse/ref-user)
- [User Device Associations](https://learn.microsoft.com/en-us/intune/developer/data-warehouse/ref-user-device)

## Relationships: Star-schema model

The warehouse organizes the entities in relationships that are meaningful to the type of questions you want to ask. For example, you can review the number of installations of an in-house developed Android application. The structure of the data warehouse enables you to gain insight into your mobile environment. In turn, analytics tools, such as Microsoft Power BI, can use the Data Warehouse data model to create visualizations and dynamic dashboards.

The entities and relationships use a star-schema model. A star-schema correlates facts over the dimension of time. A *fact* in the context of the model is a quantitative measurement such as the number of devices, number of apps, or time of enrollment. Fact tables store a lot of data. They can get very large, and so they typically limit information to 30 days. A *dimension* provides context to the facts. Where the fact measures what happened, the dimensions indicate to whom it happened. Dimension tables, such as the **User** table, are smaller and can retrain data for longer periods of time than fact tables.

A star-schema model is optimized for flexibility and data analysis so that you can create the reports needed to understand your evolving mobile environment.

## Time: Daily snapshots

The warehouse is downstream from your Intune data. Intune takes a daily snapshot at Midnight UTC and stores the snapshot in the warehouse. The duration of held snapshots vary from fact table to fact table. Some may hold seven days, others 30 days, and some even longer durations.

Note

The Data Warehouse does not sync Jamf devices. For more information about Jamf, see [Troubleshooting Jamf Pro integration with Microsoft Intune](https://learn.microsoft.com/en-us/troubleshoot/mem/intune/troubleshoot-jamf) and [Data Jamf Pro sends to Intune](https://learn.microsoft.com/en-us/intune/privacy/data-sharing/ref-jamf-to-intune).

## Next steps

- To learn more about how the data warehouse tracks a user's lifetime in Intune, see [User lifetime representation in the Intune Data Warehouse](https://learn.microsoft.com/en-us/intune/developer/data-warehouse/ref-user-timeline).
- To learn more about working with data warehouses, see [Microsoft Fabric Data Warehouse introduction](https://learn.microsoft.com/en-us/fabric/data-warehouse/tutorial-introduction).
- To learn more about working with Power BI and a data warehouse in [Create a new Power BI report by importing a dataset](https://powerbi.microsoft.com/documentation/powerbi-service-create-a-new-report/).
