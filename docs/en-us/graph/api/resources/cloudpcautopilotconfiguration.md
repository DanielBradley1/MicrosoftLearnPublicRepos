<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/cloudpcautopilotconfiguration?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-09-27 -->

# cloudPcAutopilotConfiguration resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents specific settings for Windows Autopilot that enable Windows 365 customers to experience it on Cloud PC.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| applicationTimeoutInMinutes | Int32 | Indicates the number of minutes allowed for the Autopilot application to apply the device preparation profile \(DPP\) configurations to the device. If the Autopilot application doesn't finish within the specified time \(**applicationTimeoutInMinutes**\), the application error is added to the **statusDetail** property of the [cloudPC](https://learn.microsoft.com/en-us/graph/api/resources/cloudpc?view=graph-rest-beta) object. The supported value is an integer between `30` and `360`. Required. |
| devicePreparationProfileId | String | The unique identifier \(ID\) of the Autopilot device preparation profile \(DPP\) that links a Windows Autopilot device preparation policy to ensure that devices are ready for users after provisioning. Required. |
| onFailureDeviceAccessDenied | Boolean | Indicates whether the access to the device is allowed when the application of Autopilot device preparation profile \(DPP\) configurations fails or times out. If `true`, the **status** of the device is `failed` and the device is unable to access; otherwise, the **status** of the device is `provisionedWithWarnings` and the device is allowed to access. The default value is `false`. Required. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.cloudPcAutopilotConfiguration",
  "applicationTimeoutInMinutes": "Int32",
  "devicePreparationProfileId": "String (identifier)",
  "onFailureDeviceAccessDenied": "Boolean"
}
```
