<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/sqlviews/advanced-exercise-2-create-new-report-hardware-inventory-configuration-manager -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# Advanced exercise 2: Create a new report for hardware inventory in Configuration Manager

In this exercise, you will create a Configuration Manager report that displays the computer name, site code, the date of the last scan for hardware inventory, and the number of days since the last scan for a specified computer.

Important

Before you begin this exercise, you should review the basic exercises to learn about the report elements, the properties for a report, and the different ways to create the report SQL statement.

## Report requirements

Use the following report requirements to create the new report.

## SQL Server views in the SQL statement

Use the following Configuration Manager SQL Server views when creating the report SQL statement:

- **v\_GS\_WORKSTATION\_STATUS**: This SQL Server view contains the date and time of the last scan for hardware inventory reported by client computers. For more information about this SQL Server view, see [Hardware Inventory Views in Configuration Manager](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/sqlviews/hardware-inventory-views-configuration-manager).
- **v\_R\_System**: This SQL Server view contains all of the discovered system resources. For more information about this SQL Server view, see [Discovery Views in Configuration Manager](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/sqlviews/discovery-views-configuration-manager).
- **v\_RA\_System\_SMSInstalledSites**: This SQL Server view contains the installed site for all client computers. For more information about this SQL Server view, see [Discovery Views in Configuration Manager](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/sqlviews/discovery-views-configuration-manager).

## JOINS in the SQL statement

Create the following JOINS in the SQL statement:

- **v\_GS\_WORKSTATION\_STATUS** is joined to **v\_R\_System** by using the **ResourceID** columns.
- **v\_RA\_System\_SMSInstalledSites** is joined to **v\_R\_System** by using the **ResourceID** columns.

## Columns in the SQL statement

Use the following report columns, in the order listed:

1. **Netbios\_Name0** AS **\[Computer Name\]** from **v\_R\_System**
2. **SMS\_Installed\_Sites0** AS **\[Site Code\]** from **v\_RA\_System\_SMSInstalledSites**
3. **LastHWScan** AS **\[Last HWScan\]** from **v\_GS\_WORKSTATION\_STATUS**
4. **DATEDIFF\(day, v\_GS\_WORKSTATION\_STATUS.LastHWScan, GETDATE\(\)\)** AS **\[Days Since Last HWScan\]**

Note

This report integrates two SQL Server functions to determine the difference between the last hardware scan date and the current date. To display this column, you can copy the whole line into the SQL statement, or you can copy **DATEDIFF\(day, v\_GS\_WORKSTATION\_STATUS.LastHWScan, GETDATE\(\)\)** into the **Column** column and **Days Since Last HWScan** into the **Alias** column in Query Designer.

Sort the data in descending order, using the **LastHWScan** column.

## Filters in the SQL statement

The report SQL statement does not contain any filters.

## Report prompts

The Configuration Manager report should contain a report prompt for the computer name that will be reported on.

## Solution

See [Advanced exercise 2 solution: Create a new report for hardware inventory in Configuration Manager](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/sqlviews/advanced-exercise-2-solution-create-new-report-hardware-inventory-configuration-manager) for detailed information about how to create this report.

## See also

[Exercise 1: run an existing Configuration Manager report](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/sqlviews/exercise-1-run-existing-configuration-manager-report) [Advanced exercise 2 solution: Create a new report for hardware inventory in Configuration Manager](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/sqlviews/advanced-exercise-2-solution-create-new-report-hardware-inventory-configuration-manager)
