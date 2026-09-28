<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/copilot/employee-self-service/workday-prompts-support-config -->
<!-- Sitemap-Last-Modified: 2025-11-05 -->

# User context prompts support configuration for Workday integration with Employee Self-Service agent

This support configuration is used for retrieving the required user context **context prompts** attributes from Workday. Refer to these tables to create a custom report following these tables for different configuration sections in the Workday custom report.

| Report Name | WD User Context |
| --- | --- |
| Report Type | Advanced |
| Data Source | All Workday Accounts |
| Data Source Type | Standard |
| Primary Business Object | Workday Account |
| Report Definition Usages | 0 |
| Saved Filter Usages | 0 |
| **Additional Info** |  |
| Data Source Description | Accesses the Workday Account object and returns one row per Workday account. Includes all Workday accounts ever created, either currently enabled or not. Doesn't contain built-in prompts. This data source shows settings of a user's sign in information and preferences in Workday. |
| Brief Description |  |
| Passes Report Column Toggles |  |
| **Prompts** |  |
| Specify the prompt defaults to use |  |
| **Prompt instructions** |  |
| Instructions |  |
| **Runtime data prompts** |  |
| Effective date | Use date and time at runtime |
| Entry date | Use date and time at runtime |
| Display prompt values in subtitle | Yes |

## Prompt Defaults

| Field | Prompt qualifier | Label for prompt | label for prompt XML alias | Default type | Default value | Required | Don't prompt at runtime | Don't include in subtitle |
| --- | --- | --- | --- | --- | --- | --- | --- | --- |
| User Name | Default prompt |  | User\_Name | No default value |  | Yes |  |  |
| Employee Type |  |  | Employee\_Type | No default value |  |  | Yes |  |
| Non-Employee Type |  |  | Employee\_Type | No default value |  |  | Yes |  |
| Include managers of employees |  |  | Include\_managers\_of\_employees | Specialty default value | Yes |  | Yes |  |
| Include managers of nonemployees |  |  | Include\_managers\_of\_non\_employees | No default value |  |  | Yes |  |
| Include managers of unfilled positions only |  |  | Include\_managers\_of\_unfilled\_positions\_only | No default value |  |  | Yes |  |
