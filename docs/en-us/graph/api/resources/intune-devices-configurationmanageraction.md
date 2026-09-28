<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-configurationmanageraction?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-01-08 -->

# configurationManagerAction resource type

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

Parameter for action triggerConfigurationManagerAction

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| action | [configurationManagerActionType](https://learn.microsoft.com/en-us/graph/api/resources/intune-devices-configurationmanageractiontype?view=graph-rest-beta) | The action type to trigger on Configuration Manager client. Possible values are: `refreshMachinePolicy`, `refreshUserPolicy`, `wakeUpClient`, `appEvaluation`, `quickScan`, `fullScan`, `windowsDefenderUpdateSignatures`. |

## Relationships

None

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.configurationManagerAction",
  "action": "String"
}
```
