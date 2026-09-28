<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-customtaskextensioncallbackconfiguration?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-07-04 -->

# customTaskExtensionCallbackConfiguration resource type

Namespace: microsoft.graph.identityGovernance

Defines if, and in, which time span a callback is expected from the Azure Logic App. This object is configured in the **callbackConfiguration** property of the [customTaskExtension](https://learn.microsoft.com/en-us/graph/api/resources/identitygovernance-customtaskextension?view=graph-rest-1.0) resource.

Inherits from [customExtensionCallbackConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/customextensioncallbackconfiguration?view=graph-rest-1.0).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| timeoutDuration | Duration | Callback time out in ISO 8601 time duration. Accepted time durations are between 30 minutes to 3 hours. For example, PT30M for 30 minutes and PT3H for three hours. Inherited from [customExtensionCallbackConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/customextensioncallbackconfiguration?view=graph-rest-1.0). |
| authorizedApps | microsoft.graph.application collection | A collection of unique identifiers or **appIds** of the applications that are allowed to [resume](https://learn.microsoft.com/en-us/graph/api/identitygovernance-taskprocessingresult-resume?view=graph-rest-1.0) a task processing result. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.identityGovernance.customTaskExtensionCallbackConfiguration",
  "timeoutDuration": "String (duration)",
  "authorizedApps":[
    {
      "@odata.type": "microsoft.graph.application"
    }
] 
}
```
