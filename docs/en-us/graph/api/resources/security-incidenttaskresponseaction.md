<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/security-incidenttaskresponseaction?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-06-20 -->

# incidentTaskResponseAction resource type \(deprecated\)

Namespace: microsoft.graph.security

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Important

The **incidentTaskResponseAction** resource type is deprecated and will be removed on October 1, 2026. Use [automatedAction](https://learn.microsoft.com/en-us/graph/api/resources/security-automatedaction?view=graph-rest-beta) \(grouped via [automatedActionSet](https://learn.microsoft.com/en-us/graph/api/resources/security-automatedactionset?view=graph-rest-beta)\) on the [detectionAction](https://learn.microsoft.com/en-us/graph/api/resources/security-detectionaction?view=graph-rest-beta) resource instead.

Represents the base type for all incident task response actions in Microsoft Defender XDR. This is an abstract type that cannot be instantiated directly but serves as the parent type for the following specific response actions that can be executed on incident tasks.

- [stopAndQuarantineFileIncidentTaskResponseAction](https://learn.microsoft.com/en-us/graph/api/resources/security-stopandquarantinefileincidenttaskresponseaction?view=graph-rest-beta) - Used to stop and quarantine a file.
- [collectInvestigationPackageIncidentTaskResponseAction](https://learn.microsoft.com/en-us/graph/api/resources/security-collectinvestigationpackageincidenttaskresponseaction?view=graph-rest-beta) - Used to collect device logs for investigation.
- [disableUserIncidentTaskResponseAction](https://learn.microsoft.com/en-us/graph/api/resources/security-disableuserincidenttaskresponseaction?view=graph-rest-beta) - Used to temporarily disable a user account.
- [enableUserIncidentTaskResponseAction](https://learn.microsoft.com/en-us/graph/api/resources/security-enableuserincidenttaskresponseaction?view=graph-rest-beta) - Used to re-enable a previously disabled user account.
- [forceUserPasswordResetIncidentTaskResponseAction](https://learn.microsoft.com/en-us/graph/api/resources/security-forceuserpasswordresetincidenttaskresponseaction?view=graph-rest-beta) - Used to force a user to reset their password.
- [hardDeleteEmailIncidentTaskResponseAction](https://learn.microsoft.com/en-us/graph/api/resources/security-harddeleteemailincidenttaskresponseaction?view=graph-rest-beta) - Used to permanently delete an email message.
- [isolateDeviceIncidentTaskResponseAction](https://learn.microsoft.com/en-us/graph/api/resources/security-isolatedeviceincidenttaskresponseaction?view=graph-rest-beta) - Used to isolate a device from the network.
- [markUserAsCompromisedIncidentTaskResponseAction](https://learn.microsoft.com/en-us/graph/api/resources/security-markuserascompromisedincidenttaskresponseaction?view=graph-rest-beta) - Used to mark a user account as compromised.
- [requireSignInIncidentTaskResponseAction](https://learn.microsoft.com/en-us/graph/api/resources/security-requiresigninincidenttaskresponseaction?view=graph-rest-beta) - Used to require a user to sign in again.
- [restrictAppExecutionIncidentTaskResponseAction](https://learn.microsoft.com/en-us/graph/api/resources/security-restrictappexecutionincidenttaskresponseaction?view=graph-rest-beta) - Used to restrict application execution on a device.
- [runAntivirusScanIncidentTaskResponseAction](https://learn.microsoft.com/en-us/graph/api/resources/security-runantivirusscanincidenttaskresponseaction?view=graph-rest-beta) - Used to initiate an antivirus scan on a device.
- [softDeleteIncidentTaskResponseAction](https://learn.microsoft.com/en-us/graph/api/resources/security-softdeleteincidenttaskresponseaction?view=graph-rest-beta) - Used to move an email message to the deleted items folder.
- [unIsolateDeviceIncidentTaskResponseAction](https://learn.microsoft.com/en-us/graph/api/resources/security-unisolatedeviceincidenttaskresponseaction?view=graph-rest-beta) - Used to remove network isolation from a device.
- [unRestrictAppExecutionIncidentTaskResponseAction](https://learn.microsoft.com/en-us/graph/api/resources/security-unrestrictappexecutionincidenttaskresponseaction?view=graph-rest-beta) - Used to remove application execution restrictions from a device.

Inherits from [responseAction](https://learn.microsoft.com/en-us/graph/api/resources/security-responseaction?view=graph-rest-beta).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| identifierValue | String | Required. The identifier value for the response action. This value is specific to the type of action being performed. |

## Relationships

None.

## JSON representation

The following is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.security.incidentTaskResponseAction",
  "identifierValue": "String"
}
```
