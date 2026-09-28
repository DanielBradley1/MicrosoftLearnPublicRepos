<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-lifecyclemanagementsettings?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-07-02 -->

# lifecycleManagementSettings resource type

Namespace: microsoft.graph.identityGovernance

The settings of Microsoft Entra Lifecycle Workflows in the tenant.

## Methods

| Method | Return type | Description |
| :--- | :--- | :--- |
| [Get](https://learn.microsoft.com/en-us/graph/api/identitygovernance-lifecyclemanagementsettings-get?view=graph-rest-1.0) | [microsoft.graph.identityGovernance.lifecycleManagementSettings](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-lifecyclemanagementsettings?view=graph-rest-1.0) | Read the properties and relationships of a [lifecycleManagementSettings](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-lifecyclemanagementsettings?view=graph-rest-1.0) object. |
| [Update](https://learn.microsoft.com/en-us/graph/api/identitygovernance-lifecyclemanagementsettings-update?view=graph-rest-1.0) | [microsoft.graph.identityGovernance.lifecycleManagementSettings](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-lifecyclemanagementsettings?view=graph-rest-1.0) | Update the properties of a [lifecycleManagementSettings](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-lifecyclemanagementsettings?view=graph-rest-1.0) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| emailSettings | [microsoft.graph.emailSettings](https://learn.microsoft.com/en-us/graph/api/resources/emailsettings?view=graph-rest-1.0) | Defines the settings for emails sent out from email-specific [tasks](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-task?view=graph-rest-1.0) within workflows. Accepts 2 parameters  <br>  <br>senderDomain- Defines the domain of who is sending the email.  <br>useCompanyBranding- A Boolean value that defines if company branding is to be used with the email. |
| quarantineConfiguration | [microsoft.graph.identityGovernance.quarantineConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-quarantineconfiguration?view=graph-rest-1.0) | The tenant-level quarantine configuration that automatically halts a [workflow](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-workflow?view=graph-rest-1.0) when its threshold conditions are met. Optional. |
| workflowScheduleIntervalInHours | Int32 | The interval in hours at which all [workflows](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-workflow?view=graph-rest-1.0) running in the tenant should be scheduled for execution. This interval has a minimum value of 1 and a maximum value of 24. The default value is 3 hours. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.identityGovernance.lifecycleManagementSettings",
  "workflowScheduleIntervalInHours": "Integer",
  "emailSettings": {
    "@odata.type": "microsoft.graph.emailSettings"
  },
  "quarantineConfiguration": {
    "@odata.type": "microsoft.graph.identityGovernance.quarantineConfiguration"
  }
}
```
