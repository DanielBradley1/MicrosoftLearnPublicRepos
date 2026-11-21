<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/cloudpcflexaccessconfiguration?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-11-17 -->

# cloudPcFlexAccessConfiguration resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Represents the current access configuration of a Windows 365 Flex \(formerly Windows 365 Frontline\) [Cloud PC](https://learn.microsoft.com/en-us/graph/api/resources/cloudpc?view=graph-rest-beta). The [retrieveFlexCloudPcAccessConfiguration](https://learn.microsoft.com/en-us/graph/api/cloudpc-retrieveflexcloudpcaccessconfiguration?view=graph-rest-beta) function on the [cloudPC](https://learn.microsoft.com/en-us/graph/api/resources/cloudpc?view=graph-rest-beta) resource returns this type.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| accessState | [cloudPcFlexAccessState](#cloudpcflexaccessstate-values) | The current access state of the Flex Cloud PC. The possible values are: `unassigned`, `activationFailed`, `active`, `activating`, `standbyMode`, `unknownFutureValue`. The `/me` endpoint resolves the state for the signed-in user; the administrative endpoint returns the runtime state of the device. Read-only. |

### cloudPcFlexAccessState values

| Member | Description |
| :--- | :--- |
| unassigned | The Cloud PC isn't currently assigned. |
| activationFailed | Activation of the Cloud PC failed. |
| active | The Cloud PC is active and ready to connect. |
| activating | The Cloud PC is in the activation process. |
| standbyMode | The Cloud PC is in standby mode and remains accessible. |
| unknownFutureValue | Evolvable enumeration sentinel value. Don't use. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.cloudPcFlexAccessConfiguration",
  "accessState": "String"
}
```
