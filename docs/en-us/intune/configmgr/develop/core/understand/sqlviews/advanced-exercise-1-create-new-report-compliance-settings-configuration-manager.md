<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/sqlviews/advanced-exercise-1-create-new-report-compliance-settings-configuration-manager -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# Advanced exercise 1: Create a new report for compliance settings in Configuration Manager

In this exercise, you will create a Configuration Manager report that displays the name and description of the configuration baselines that are deployed to a specified computer and whether the computer returns compliant or noncompliant for the configuration baseline.

Important

Before you begin this exercise, you should review the basic exercises to learn about the report elements, the properties for a report, and the different ways to create the report SQL statement.

## Report requirements

Use the following report requirements to create the new report.

## SQL Server views in the SQL statement

Use the following Configuration Manager SQL views when creating the report SQL statement:

- **v\_CICurrentComplianceStatus:** This SQL view contains compliance information for all configuration items. For more information about this SQL view, see [Compliance Settings Views in Configuration Manager](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/sqlviews/compliance-settings-views-configuration-manager).
- **v\_ConfigurationItems:** This SQL view contains all of the configuration items. For more information about this SQL view, see [Compliance Settings Views in Configuration Manager](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/sqlviews/compliance-settings-views-configuration-manager).
- **v\_LocalizedCIProperties:** This SQL view contains the localized titles and descriptions for the configuration items. For more information about this SQL view, see [Compliance Settings Views in Configuration Manager](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/sqlviews/compliance-settings-views-configuration-manager).
- **v\_R\_System:** This SQL view contains all of the discovered system resources. For more information about this SQL view, see [Discovery Views in Configuration Manager](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/sqlviews/discovery-views-configuration-manager).

## JOINS in the SQL statement

Create the following JOINS in the SQL statement:

- **v\_CICurrentComplianceStatus** is joined to **v\_ConfigurationItems** by using the **CI\_ID** column.
- **v\_CICurrentComplianceStatus** is joined to **v\_LocalizedCIProperties** by using the **CI\_ID** column.
- **v\_CICurrentComplianceStatus** is joined to **v\_R\_System** by using the **ResourceID** column.

## Columns in the SQL statement

Use the following report columns, in the order listed:

1. **ComplianceStateName** from **v\_CICurrentComplianceStatus**
2. **DisplayName** from **v\_LocalizedCIProperties**
3. **Description** from **v\_LocalizedCIProperties**
4. **Netbios\_Name0** from **v\_R\_System**
5. **CIType\_ID** from **v\_ConfigurationItems** \(Not displayed\)

Sort the returned data in ascending order, using the **Netbios\_Name0** column.

## Filters in the SQL statement

The report SQL statement should meet the following filtering criteria:

- Select only configuration baselines. You can filter specifically on configuration baselines by selecting the **CIType\_ID**. Configuration baselines are CI type 2.

## Report prompts

The Configuration Manager report should contain a report prompt for the computer name that will be reported on.

## Solution

See [Advanced exercise 1 solution: create a new report for compliance settings in Configuration Manager](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/sqlviews/advanced-exercise-1-solution-create-new-report-compliance-settings-configuration-manager) for detailed information about how to create this report.

## See also

[Exercise 1: run an existing Configuration Manager report](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/sqlviews/exercise-1-run-existing-configuration-manager-report) [Advanced exercise 1 solution: create a new report for compliance settings in Configuration Manager](https://learn.microsoft.com/en-us/intune/configmgr/develop/core/understand/sqlviews/advanced-exercise-1-solution-create-new-report-compliance-settings-configuration-manager)
