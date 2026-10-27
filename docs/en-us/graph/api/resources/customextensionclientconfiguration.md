<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/customextensionclientconfiguration?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-10-24 -->

# customExtensionClientConfiguration resource type

Namespace: microsoft.graph

Connection settings that define how long Microsoft Entra ID can wait for a response from an external app before it shuts down the connection when trying to trigger the external app. This object is configured in the **clientConfiguration** property of the [customTaskExtension](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-customtaskextension?view=graph-rest-1.0) and [roleManagementCustomCalloutExtension](https://learn.microsoft.com/en-us/graph/api/resources/rolemanagementcustomcalloutextension?view=graph-rest-1.0) resources.

In entitlement management, this object is configured in the **clientConfiguration** property of:

- [accessPackageAssignmentRequestWorkflowExtension](https://learn.microsoft.com/en-us/graph/api/resources/accesspackageassignmentrequestworkflowextension?view=graph-rest-1.0)
- [accessPackageAssignmentWorkflowExtension](https://learn.microsoft.com/en-us/graph/api/resources/accesspackageassignmentworkflowextension?view=graph-rest-1.0)
- [customCalloutExtension](https://learn.microsoft.com/en-us/graph/api/resources/customcalloutextension?view=graph-rest-1.0)

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| maximumRetries | Int32 | The max number of retries that Microsoft Entra ID makes to the external API. For a **roleManagementCustomCalloutExtension**, the valid range is from `0` through `5`. For other custom extensions, values of `0` or `1` are supported. If `null`, the default for the service applies. |
| timeoutInMilliseconds | Int32 | The max duration in milliseconds that Microsoft Entra ID waits for a response from the external app before it shuts down the connection. For a **roleManagementCustomCalloutExtension**, the valid range is from `1000` through `60000` milliseconds. For other custom extensions, the valid range is from `200` through `2000` milliseconds and the default is `1000` milliseconds. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.customExtensionClientConfiguration",
  "maximumRetries": "Integer",
  "timeoutInMilliseconds": "Integer"
}
```
