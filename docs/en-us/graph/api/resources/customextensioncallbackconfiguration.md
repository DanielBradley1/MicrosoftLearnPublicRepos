<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/customextensioncallbackconfiguration?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-07-04 -->

# customExtensionCallbackConfiguration resource type

Namespace: microsoft.graph

Callback settings that define how long Microsoft Entra ID can wait for a resume signal for the callout that it made to the logic app. This is an abstract type that's inherited by [customTaskExtensionCallbackConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-customtaskextensioncallbackconfiguration?view=graph-rest-1.0). In Lifecycle Workflows, the derived types of this object are configured in the **callbackConfiguration** property of the [customTaskExtension](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-customtaskextension?view=graph-rest-1.0) resource.

In entitlement management, the derived types of this object are configured in the **callbackConfiguration** property of:

- [accessPackageAssignmentCalloutData](https://learn.microsoft.com/en-us/graph/api/resources/accesspackageassignmentcalloutdata?view=graph-rest-1.0)
- [accessPackageAssignmentRequestCalloutData](https://learn.microsoft.com/en-us/graph/api/resources/accesspackageassignmentrequestcalloutdata?view=graph-rest-1.0)
- [accessPackageAssignmentRequestWorkflowExtension](https://learn.microsoft.com/en-us/graph/api/resources/accesspackageassignmentrequestworkflowextension?view=graph-rest-1.0)
- [accessPackageAssignmentWorkflowExtension](https://learn.microsoft.com/en-us/graph/api/resources/accesspackageassignmentworkflowextension?view=graph-rest-1.0)

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| timeoutDuration | Duration | The maximum duration in ISO 8601 format that Microsoft Entra ID will wait for a resume action for the callout it sent to the logic app. The valid range for custom extensions in lifecycle workflows is five minutes to three hours. The valid range for custom extensions in entitlement management is between 5 minutes and 14 days. For example, `PT3H` refers to three hours, `P3D` refers to three days, `PT10M` refers to ten minutes. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.customExtensionCallbackConfiguration",
  "timeoutDuration": "String (duration)"
}
```
