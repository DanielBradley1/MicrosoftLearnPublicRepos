<!-- Source: https://learn.microsoft.com/en-us/intune/developer/data-warehouse/ref-user-device -->
<!-- Sitemap-Last-Modified: 2026-04-08 -->

# Reference for User Device Association entity

The **userDeviceAssociation** entity contains user device associations in your organization.

## userDeviceAssociations

| Name | Description | Example |
| --- | --- | --- |
| userKey | Unique identifier of the user in the data warehouse. \(Surrogate key\). | 123 |
| deviceKey | Unique identifier of the device in the data warehouse. | 123 |
| createdDateTimeUTC | Date and time when the user device association was created. Uses UTC format. | 11/23/2016 12:00:00 AM |
| isDeleted | Indicates that the user unenrolled that device, and that the association is not current anymore. | True/False |
| endedDateTimeUTC | Date and time in UTC when IsDeleted changed to **True**. | 06/23/2017 12:00:00 AM |

## Next steps

- Learn more about the [Intune Data Warehouse](https://learn.microsoft.com/en-us/intune/developer/data-warehouse/create-reports).
