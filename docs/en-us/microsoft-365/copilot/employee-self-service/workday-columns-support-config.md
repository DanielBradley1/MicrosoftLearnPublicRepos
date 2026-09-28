<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/copilot/employee-self-service/workday-columns-support-config -->
<!-- Sitemap-Last-Modified: 2025-11-05 -->

# Columns

This support configuration is used for retrieving the required user columns attributes from Workday. Refer to these tables to create a custom report following these tables for different configuration sections in the Workday custom report.

## Abbreviations in some tables

CLRV= Calculation Lookup related value

| Field name | Business object | CLRV Lookup field | CLRV Related business object | CLRV return value | Additional Category | Additional authorized usage |
| --- | --- | --- | --- | --- | --- | --- |
| CF - ISO 2 Country Code LRV | Worker | Location Address - Country/Region | Country/Region | Alpha-2 Code | Uncategorized | Default areas |
| CF - EE Level LRV | Worker | Supervisory Organization - Primary Position | Supervisory Organization | Organization on Level from Top | Uncategorized | Default Areas |
| CF LRV Sup Org Ref ID | Worker | Manager's Default Supervisory Organization | Supervisory Organization | Reference ID |  |  |

## View Custom Report: WD User Context - COLUMNS

| Report Name | WD User Context |
| --- | --- |
| Report Name | WD User Context |
| Report Type | Advanced |
| Data Source | All Workday Accounts |
| Data Source Type | Standard |
| Primary Business Object | Workday Account |
| Report Definition Usages | 0 |
| Saved Filter Usages | 0 |
| Data Source Description | Accesses the Workday Account object and returns one row per Workday account. Includes all Workday accounts ever created, either currently enabled or not. Doesn't contain built-in prompts. This data source shows settings of a user's sign in information and preferences in Workday. |
| Brief Description |  |
| Passes Report Column Toggles |  |

## Columns

| Business Object | Field | Column Heading Override XML Alias | Format | Options |
| --- | --- | --- | --- | --- |
| Worker | Preferred Name - First Name | First\_Name |  |  |
| Worker | Preferred Name - Last Name | Last\_Name |  |  |
| Worker | Email - Primary Work | Work\_Email |  |  |
| Workday Account | User Name | User\_Name |  |  |
| Worker | Employee ID | Employee\_ID |  |  |
| Worker | CF - ISO 2 Country Code LRV | Country\_Code |  |  |
| Worker | Company - ID | Company\_Code |  |  |
| Worker | Is Manager | Is\_Manager |  |  |
| Worker | Is People Manager \(with prompts\) | Is\_People\_Manager |  |  |
| Worker | CF - EE Level LRV | Level |  |  |
| Workday Account | Display Language | Display\_Language |  |  |
| Workday Account | Locale | Locale |  |  |
| Worker | CF LRV Sup Org Ref ID | Mgr\_Sup\_Org\_Id |  |  |

## Group Column Headings

| Business Object | Group Column Heading XML Alias |
| --- | --- |
| Worker | Worker\_group |
