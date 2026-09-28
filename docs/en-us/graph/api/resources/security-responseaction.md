<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/security-responseaction?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-06-20 -->

# responseAction resource type \(deprecated\)

Namespace: microsoft.graph.security

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Important

The **responseAction** resource type and all 17 derived types are deprecated and will be removed on 2026-10-01. Use [automatedAction](https://learn.microsoft.com/en-us/graph/api/resources/security-automatedaction?view=graph-rest-beta) \(grouped via [automatedActionSet](https://learn.microsoft.com/en-us/graph/api/resources/security-automatedactionset?view=graph-rest-beta)\) on the [detectionAction](https://learn.microsoft.com/en-us/graph/api/resources/security-detectionaction?view=graph-rest-beta) resource instead.

Describes an action taken on [impacted assets](https://learn.microsoft.com/en-us/graph/api/resources/security-impactedasset?view=graph-rest-beta) as set in a [custom detection rule](https://learn.microsoft.com/en-us/graph/api/resources/security-detectionrule?view=graph-rest-beta). For more information, see [response actions](https://learn.microsoft.com/en-us/microsoft-365/security/defender/custom-detection-rules#4-specify-actions).

This type is abstract and has multiple response action types that are derived from it:

- [Stop and quarantine file](https://learn.microsoft.com/en-us/graph/api/resources/security-stopandquarantinefileresponseaction?view=graph-rest-beta)
- [Disable user](https://learn.microsoft.com/en-us/graph/api/resources/security-disableuserresponseaction?view=graph-rest-beta)
- [Force user password reset](https://learn.microsoft.com/en-us/graph/api/resources/security-forceuserpasswordresetresponseaction?view=graph-rest-beta)
- [Mark user as compromised](https://learn.microsoft.com/en-us/graph/api/resources/security-markuserascompromisedresponseaction?view=graph-rest-beta)
- [Collect investigation package](https://learn.microsoft.com/en-us/graph/api/resources/security-collectinvestigationpackageresponseaction?view=graph-rest-beta)
- [Initiate investigation](https://learn.microsoft.com/en-us/graph/api/resources/security-initiateinvestigationresponseaction?view=graph-rest-beta)
- [Isolate device](https://learn.microsoft.com/en-us/graph/api/resources/security-isolatedeviceresponseaction?view=graph-rest-beta)
- [Restrict app execution](https://learn.microsoft.com/en-us/graph/api/resources/security-restrictappexecutionresponseaction?view=graph-rest-beta)
- [Run antivirus scan](https://learn.microsoft.com/en-us/graph/api/resources/security-runantivirusscanresponseaction?view=graph-rest-beta)
- [Allow file](https://learn.microsoft.com/en-us/graph/api/resources/security-allowfileresponseaction?view=graph-rest-beta)
- [Block file](https://learn.microsoft.com/en-us/graph/api/resources/security-blockfileresponseaction?view=graph-rest-beta)
- [Hard delete email](https://learn.microsoft.com/en-us/graph/api/resources/security-harddeleteresponseaction?view=graph-rest-beta)
- [Soft delete email](https://learn.microsoft.com/en-us/graph/api/resources/security-softdeleteresponseaction?view=graph-rest-beta)
- [Move to inbox](https://learn.microsoft.com/en-us/graph/api/resources/security-movetoinboxresponseaction?view=graph-rest-beta)
- [Move to deleted items](https://learn.microsoft.com/en-us/graph/api/resources/security-movetodeleteditemsresponseaction?view=graph-rest-beta)
- [Move to junk](https://learn.microsoft.com/en-us/graph/api/resources/security-movetojunkresponseaction?view=graph-rest-beta)
- [Incident task](https://learn.microsoft.com/en-us/graph/api/resources/security-incidenttaskresponseaction?view=graph-rest-beta)

## Properties

None.

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.security.responseAction"
}
```
