<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/accesspackagerequestapprovalstagecallbackconfiguration?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-10-02 -->

# accessPackageRequestApprovalStageCallbackConfiguration resource type

Namespace: microsoft.graph

Callback settings that define how long Microsoft Entra ID can wait for a resume signal for the callout [accessPackageRequestApprovalStageCallbackConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/accesspackagerequestapprovalstagecallbackconfiguration?view=graph-rest-1.0) that comes back from the logic app. Inherits from [customExtensionCallbackConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/customextensioncallbackconfiguration?view=graph-rest-1.0).

Inherits from [customExtensionCallbackConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/customextensioncallbackconfiguration?view=graph-rest-1.0).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| timeoutDuration | Duration | The maximum duration in ISO 8601 format that Microsoft Entra ID will wait for a resume action for the callout it sent to the logic app. The valid range for custom extensions in lifecycle workflows is five minutes to three hours. The valid range for custom extensions in entitlement management is between 5 minutes and 14 days. For example, `PT3H` refers to three hours, `P3D` refers to three days, `PT10M` refers to ten minutes. Inherited from [customExtensionCallbackConfiguration](https://learn.microsoft.com/en-us/graph/api/resources/customextensioncallbackconfiguration?view=graph-rest-1.0). |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.accessPackageRequestApprovalStageCallbackConfiguration",
  "timeoutDuration": "String (duration)"
}
```
