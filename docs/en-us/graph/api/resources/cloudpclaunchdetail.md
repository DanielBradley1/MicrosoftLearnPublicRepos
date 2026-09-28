<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/cloudpclaunchdetail?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-12-16 -->

# cloudPcLaunchDetail resource type

Namespace: microsoft.graph

Contains the details to connect a [Cloud PC](https://learn.microsoft.com/en-us/graph/api/resources/cloudpc?view=graph-rest-1.0).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| cloudPcId | String | The unique identifier of the Cloud PC. |
| cloudPcLaunchUrl | String | The connect URL of the Cloud PC. |
| windows365SwitchCompatibilityFailureReasonType | [windows365SwitchCompatibilityFailureReasonType](https://learn.microsoft.com/en-us/graph/api/resources/cloudpclaunchdetail?view=graph-rest-1.0#windows365switchcompatibilityfailurereasontype-values) | Indicates the reason the Cloud PC isn't compatible with Windows 365 Switch. Possible values are: `osVersionNotSupported`, `hardwareNotSupported`, `unknownFutureValue`. `osVersionNotSupported` indicates that the user needs to update their Cloud PC operating system version. `hardwareNotSupported` indicates that the Cloud PC needs more CPUs or RAM to support the functionality. |
| windows365SwitchCompatible | Boolean | Indicates whether the Cloud PC supports switch functionality. If the value is `true`, it supports switch functionality; otherwise, `false`. |

### windows365SwitchCompatibilityFailureReasonType values

Defines the reason for switch compatibility failure on a Cloud PC.

| Member | Description |
| :--- | :--- |
| osVersionNotSupported | Default. Indicates that the Cloud PC operating system version doesn't meet the requirements to use Windows 365 Switch. |
| hardwareNotSupported | Indicates that the Cloud PC hardware doesn't meet the requirements to use Windows 365 Switch. |
| unknownFutureValue | Evolvable enumeration sentinel value. Don't use. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.cloudPcLaunchDetail",
  "cloudPcId": "String",
  "cloudPcLaunchUrl": "String",
  "windows365SwitchCompatibilityFailureReasonType": "String",
  "windows365SwitchCompatible": "Boolean"
}
```
