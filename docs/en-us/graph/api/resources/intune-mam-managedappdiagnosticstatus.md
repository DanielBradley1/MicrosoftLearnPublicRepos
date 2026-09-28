<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-mam-managedappdiagnosticstatus?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# managedAppDiagnosticStatus resource type

Namespace: microsoft.graph

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

Represents diagnostics status.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| validationName | String | The validation friendly name |
| state | String | The state of the operation |
| mitigationInstruction | String | Instruction on how to mitigate a failed validation |

## Relationships

None

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.managedAppDiagnosticStatus",
  "validationName": "String",
  "state": "String",
  "mitigationInstruction": "String"
}
```
