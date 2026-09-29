<!-- Source: https://learn.microsoft.com/en-us/defender-endpoint/api/get-remediation-methods-properties -->
<!-- Sitemap-Last-Modified: 2025-11-24 -->

# Remediation activity methods and properties

Important

Some information in this article relates to a prereleased product which may be substantially modified before it's commercially released. Microsoft makes no warranties, expressed or implied, with respect to the information provided here.

The API response contains [Microsoft Defender Vulnerability Management](https://learn.microsoft.com/en-us/defender-vulnerability-management/defender-vulnerability-management) remediation activities that have been created in your tenant. For more information,see: [remediation activities](https://learn.microsoft.com/en-us/defender-vulnerability-management/tvm-remediation).

## Properties

| Property ID | Data type | Description |
| --- | --- | --- |
| Category | String | Category of the remediation activity \(Software/Security configuration\) |
| completerEmail | String | If the remediation activity was manually completed by someone, this column contains their email |
| completerId | String | If the remediation activity was manually completed by someone, this column contains their object ID |
| completionMethod | String | A remediation activity can be completed "automatically" \(if all the devices are patched\) or "manually" by a person who selects "mark as completed." |
| createdOn | DateTime | Time this remediation activity was created |
| Description | String | Description of this remediation activity |
| dueOn | DateTime | Due date the creator set for this remediation activity |
| fixedDevices |  | The number of devices that have been fixed |
| ID | String | ID of this remediation activity |
| nameId | String | Related product name |
| Priority | String | Priority the creator set for this remediation activity \(High\\Medium\\Low\) |
| productId | String | Related product ID |
| productivityImpactRemediationType | String | A few configuration changes could be requested only for devices that don't affect users. This value indicates the selection between "all exposed devices" or "only devices with no user impact." |
| rbacGroupNames | String | Related device group names |
| recommendedProgram | String | Recommended program to upgrade to |
| recommendedVendor | String | Recommended vendor to upgrade to |
| recommendedVersion | String | Recommended version to update/upgrade to |
| relatedComponent | String | Related component of this remediation activity \(similar to the related component for a security recommendation\) |
| requesterEmail | String | Creator email address |
| requesterId | String | Creator object ID |
| requesterNotes | String | The notes \(free text\) the creator added for this remediation activity |
| Scid | String | SCID of the related security recommendation |
| Status | String | Remediation activity status \(Active/Completed\) |
| statusLastModifiedOn | DateTime | Date when the status field was updated |
| targetDevices | Long | Number of exposed devices that this remediation is applicable to |
| Title | String | Title of this remediation activity |
| Type | String | Remediation type |
| vendorId | String | Related vendor name |
