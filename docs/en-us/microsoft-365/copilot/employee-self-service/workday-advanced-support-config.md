<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/copilot/employee-self-service/workday-advanced-support-config -->
<!-- Sitemap-Last-Modified: 2025-11-05 -->

# User context advanced support configuration for Workday integration with Employee Self-Service agent

This support configuration is used for retrieving the required user context **advanced** attributes from Workday. Refer to this table to create a custom report following this table for different configuration sections in the Workday custom report.

| Report Name | WD User Context |
| --- | --- |
| Report Type | Advanced |
| Data Source | All Workday Accounts |
| Data Source Type | Standard |
| Primary Business Object | Workday Account |
| Report Definition Usages |  |
| Saved Filter Usages |  |
| **Additional Info** |  |
| Data Source Description | Accesses the Workday Account object and returns one row per Workday account. Includes all Workday accounts ever created, either currently enabled or not. Doesn't contain built-in prompts. This data source shows settings of a user's sign in information and preferences in Workday. |
| Brief Description |  |
| Passes Report Column Toggles |  |
| **Advanced** |  |
| Specify advanced options for the report |  |
| **Report performance** |  |
| Optimized for performance |  |
| Background only |  |
| **View options** |  |
| Freeze first column |  |
| Enable preferred currency |  |
| Enable save parameters |  |
| Exclude execution link from search |  |
| **Web services options** |  |
| A save and reopen is required to see and modify the web service aliases if they aren't shown |  |
| Enable as a web service | Yes |
| Web service API version | v43.0 |
| Namespace | urn:com.workday.report/WD\_User\_Context |
| **Worksheets** |  |
| Enable for worksheets |  |
| **Prism** |  |
| Enable for prism |  |
| **Temporary report** |  |
| Temporary report |  |
| Date report definition will be deleted |  |

The report name can be anything but rest of the definition including column sequences, xml alias, and so on, should be kept intact to have the report return the exact same response expected by the Employee Self-Service agent.

This report takes **Username** as an input and returns the following responses:

- First Name
- Last Name
- Work\_Email
- User\_Name
- Employee\_ID
- Country\_Code
- Company\_Code
- Is\_Manager
- Is\_People\_Manager
- Level
- Display\_Language
- Locale
- Mgr\_Sup\_Org\_Id

Note

The ownership of this custom report should be transferred to the generic user "ISU\_WQL\_COPILOT" that you created in task 3 in . This report is configured to get only employee details and doesn't return external staff or nonemployees.
