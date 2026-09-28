<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/security-alertevidence?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-05-12 -->

# alertEvidence resource type

Namespace: microsoft.graph.security

Represents evidence related to an [alert](https://learn.microsoft.com/en-us/graph/api/resources/security-alert?view=graph-rest-1.0).

The **alertEvidence** base type and its derived evidence types provide a means to organize and track rich data about each artifact involved in an **alert**. For example, an **alert** about an attacker's IP address signing in to a cloud service using a compromised user account can track the following evidence:

- [IP evidence](https://learn.microsoft.com/en-us/graph/api/resources/security-ipevidence?view=graph-rest-1.0) with the roles of `attacker` and `source`, remediation status of `running`, and verdict of `malicious`.
- [Cloud application evidence](https://learn.microsoft.com/en-us/graph/api/resources/security-cloudapplicationevidence?view=graph-rest-1.0) with a role of `contextual`.
- [Mailbox evidence](https://learn.microsoft.com/en-us/graph/api/resources/security-mailboxevidence?view=graph-rest-1.0) for the hacked user account with a role of `compromised`.

This resource is the base type for the following evidence types:

- [activeDirectoryDomainEvidence](https://learn.microsoft.com/en-us/graph/api/resources/security-activedirectorydomainevidence?view=graph-rest-1.0)
- [aiAgentEvidence](https://learn.microsoft.com/en-us/graph/api/resources/security-aiagentevidence?view=graph-rest-1.0)
- [amazonResourceEvidence](https://learn.microsoft.com/en-us/graph/api/resources/security-amazonresourceevidence?view=graph-rest-1.0)
- [analyzedMessageEvidence](https://learn.microsoft.com/en-us/graph/api/resources/security-analyzedmessageevidence?view=graph-rest-1.0)
- [azureResourceEvidence](https://learn.microsoft.com/en-us/graph/api/resources/security-azureresourceevidence?view=graph-rest-1.0)
- [blobContainerEvidence](https://learn.microsoft.com/en-us/graph/api/resources/security-blobcontainerevidence?view=graph-rest-1.0)
- [blobEvidence](https://learn.microsoft.com/en-us/graph/api/resources/security-blobevidence?view=graph-rest-1.0)
- [cloudApplicationEvidence](https://learn.microsoft.com/en-us/graph/api/resources/security-cloudapplicationevidence?view=graph-rest-1.0)
- [cloudLogonRequestEvidence](https://learn.microsoft.com/en-us/graph/api/resources/security-cloudlogonrequestevidence?view=graph-rest-1.0)
- [cloudLogonSessionEvidence](https://learn.microsoft.com/en-us/graph/api/resources/security-cloudlogonsessionevidence?view=graph-rest-1.0)
- [containerEvidence](https://learn.microsoft.com/en-us/graph/api/resources/security-containerevidence?view=graph-rest-1.0)
- [containerImageEvidence](https://learn.microsoft.com/en-us/graph/api/resources/security-containerimageevidence?view=graph-rest-1.0)
- [containerRegistryEvidence](https://learn.microsoft.com/en-us/graph/api/resources/security-containerregistryevidence?view=graph-rest-1.0)
- [deviceEvidence](https://learn.microsoft.com/en-us/graph/api/resources/security-deviceevidence?view=graph-rest-1.0)
- [dnsEvidence](https://learn.microsoft.com/en-us/graph/api/resources/security-dnsevidence?view=graph-rest-1.0)
- [fileEvidence](https://learn.microsoft.com/en-us/graph/api/resources/security-fileevidence?view=graph-rest-1.0)
- [fileHashEvidence](https://learn.microsoft.com/en-us/graph/api/resources/security-filehashevidence?view=graph-rest-1.0)
- [gitHubOrganizationEvidence](https://learn.microsoft.com/en-us/graph/api/resources/security-githuborganizationevidence?view=graph-rest-1.0)
- [gitHubRepoEvidence](https://learn.microsoft.com/en-us/graph/api/resources/security-githubrepoevidence?view=graph-rest-1.0)
- [gitHubUserEvidence](https://learn.microsoft.com/en-us/graph/api/resources/security-githubuserevidence?view=graph-rest-1.0)
- [googleCloudResourceEvidence](https://learn.microsoft.com/en-us/graph/api/resources/security-googlecloudresourceevidence?view=graph-rest-1.0)
- [hostLogonSessionEvidence](https://learn.microsoft.com/en-us/graph/api/resources/security-hostlogonsessionevidence?view=graph-rest-1.0)
- [ioTDeviceEvidence](https://learn.microsoft.com/en-us/graph/api/resources/security-iotdeviceevidence?view=graph-rest-1.0)
- [ipEvidence](https://learn.microsoft.com/en-us/graph/api/resources/security-ipevidence?view=graph-rest-1.0)
- [kubernetesClusterEvidence](https://learn.microsoft.com/en-us/graph/api/resources/security-kubernetesclusterevidence?view=graph-rest-1.0)
- [kubernetesControllerEvidence](https://learn.microsoft.com/en-us/graph/api/resources/security-kubernetescontrollerevidence?view=graph-rest-1.0)
- [kubernetesNamespaceEvidence](https://learn.microsoft.com/en-us/graph/api/resources/security-kubernetesnamespaceevidence?view=graph-rest-1.0)
- [kubernetesPodEvidence](https://learn.microsoft.com/en-us/graph/api/resources/security-kubernetespodevidence?view=graph-rest-1.0)
- [kubernetesSecretEvidence](https://learn.microsoft.com/en-us/graph/api/resources/security-kubernetessecretevidence?view=graph-rest-1.0)
- [kubernetesServiceAccountEvidence](https://learn.microsoft.com/en-us/graph/api/resources/security-kubernetesserviceaccountevidence?view=graph-rest-1.0)
- [kubernetesServiceEvidence](https://learn.microsoft.com/en-us/graph/api/resources/security-kubernetesserviceevidence?view=graph-rest-1.0)
- [mailboxConfigurationEvidence](https://learn.microsoft.com/en-us/graph/api/resources/security-mailboxconfigurationevidence?view=graph-rest-1.0)
- [mailboxEvidence](https://learn.microsoft.com/en-us/graph/api/resources/security-mailboxevidence?view=graph-rest-1.0)
- [mailClusterEvidence](https://learn.microsoft.com/en-us/graph/api/resources/security-mailclusterevidence?view=graph-rest-1.0)
- [malwareEvidence](https://learn.microsoft.com/en-us/graph/api/resources/security-malwareevidence?view=graph-rest-1.0)
- [networkConnectionEvidence](https://learn.microsoft.com/en-us/graph/api/resources/security-networkconnectionevidence?view=graph-rest-1.0)
- [nicEvidence](https://learn.microsoft.com/en-us/graph/api/resources/security-nicevidence?view=graph-rest-1.0)
- [oauthApplicationEvidence](https://learn.microsoft.com/en-us/graph/api/resources/security-oauthapplicationevidence?view=graph-rest-1.0)
- [processEvidence](https://learn.microsoft.com/en-us/graph/api/resources/security-processevidence?view=graph-rest-1.0)
- [registryKeyEvidence](https://learn.microsoft.com/en-us/graph/api/resources/security-registrykeyevidence?view=graph-rest-1.0)
- [registryValueEvidence](https://learn.microsoft.com/en-us/graph/api/resources/security-registryvalueevidence?view=graph-rest-1.0)
- [sasTokenEvidence](https://learn.microsoft.com/en-us/graph/api/resources/security-sastokenevidence?view=graph-rest-1.0)
- [securityGroupEvidence](https://learn.microsoft.com/en-us/graph/api/resources/security-securitygroupevidence?view=graph-rest-1.0)
- [servicePrincipalEvidence](https://learn.microsoft.com/en-us/graph/api/resources/security-serviceprincipalevidence?view=graph-rest-1.0)
- [submissionMailEvidence](https://learn.microsoft.com/en-us/graph/api/resources/security-submissionmailevidence?view=graph-rest-1.0)
- [teamsMessageEvidence](https://learn.microsoft.com/en-us/graph/api/resources/security-teamsmessageevidence?view=graph-rest-1.0)
- [urlEvidence](https://learn.microsoft.com/en-us/graph/api/resources/security-urlevidence?view=graph-rest-1.0)
- [userEvidence](https://learn.microsoft.com/en-us/graph/api/resources/security-userevidence?view=graph-rest-1.0)

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| createdDateTime | DateTimeOffset | The date and time when the evidence was created and added to the alert. The Timestamp type represents date and time information using ISO 8601 format and is always in UTC time. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z`. |
| detailedRoles | String collection | Detailed description of the entity role/s in an alert. Values are free-form. |
| remediationStatus | [microsoft.graph.security.evidenceRemediationStatus](#evidenceremediationstatus-values) | Status of the remediation action taken. The possible values are: `none`, `remediated`, `prevented`, `blocked`, `notFound`, `unknownFutureValue`, `active`, `pendingApproval`, `declined`, `unremediated`, `running`, `partiallyRemediated`. Use the `Prefer: include-unknown-enum-members` request header to get the following values from this [evolvable enum](https://learn.microsoft.com/en-us/graph/best-practices-concept#handling-future-members-in-evolvable-enumerations): `active`, `pendingApproval`, `declined`, `unremediated`, `running`, `partiallyRemediated`. |
| remediationStatusDetails | String | Details about the remediation status. |
| roles | [microsoft.graph.security.evidenceRole](#evidencerole-values) collection | The role/s that an evidence entity represents in an alert, for example, an IP address that is associated with an attacker has the evidence role **Attacker**. |
| tags | String collection | Array of custom tags associated with an evidence instance, for example, to denote a group of devices, high-value assets, etc. |
| verdict | [microsoft.graph.security.evidenceVerdict](#evidenceverdict-values) | The decision reached by automated investigation. The possible values are: `unknown`, `suspicious`, `malicious`, `noThreatsFound`, `unknownFutureValue`. |

### detectionSource values

| Value | Description |
| :--- | :--- |
| detected | A product of the threat that executed was detected. |
| blocked | The threat was remediated at run time. |
| prevented | The threat was prevented from occurring \(running, downloading, and so on.\). |
| unknownFutureValue | Evolvable enumeration sentinel value. Don't use. |

### evidenceRemediationStatus values

| Member | Description |
| :--- | :--- |
| none | No threats were found. |
| remediated | Remediation action has completed successfully. |
| prevented | The threat was prevented from executing. |
| blocked | The threat was blocked while executing. |
| notFound | The evidence wasn't found. |
| unknownFutureValue | Evolvable enumeration sentinel value. Don't use. |
| active | Investigation is running/pending and remediation is not complete yet. |
| pendingApproval | The remediation action is pending approval. |
| declined | The remediation action was declined. |
| unremediated | Investigation undid the remediation and the entity is recovered. |
| running | The remediation action is running. |
| partiallyRemediated | The threat was partially remediated. |

### evidenceRole values

| Member | Description |
| :--- | :--- |
| unknown | The evidence role is unknown. |
| contextual | An entity that arose likely benign but was reported as a side effect of an attacker's action. For example, the benign services.exe process was used to start a malicious service. |
| scanned | An entity identified as a target of discovery scanning or reconnaissance actions. For example, a port scanner was used to scan a network. |
| source | The entity the activity originated from. For example, a device, user, IP address, or so on. |
| destination | The entity the activity was sent to. For example, a device, user, IP address, or so on. |
| created | The entity was created as a result of the actions of an attacker. For example, a user account was created. |
| added | The entity was added as a result of the actions of an attacker. For example, a user account was added to a permissions group. |
| compromised | The entity was compromised and is under the control of an attacker. For example, a user account was compromised and used to log into a cloud service. |
| edited | The entity was edited or changed by an attacker. For example, the registry key for a service was edited to point to the location of a new malicious payload. |
| attacked | The entity was attacked. For example, a device was targeted in a DDoS attack. |
| attacker | The entity represents the attacker. For example, the attacker`s IP address observed logging into a cloud service using a compromised user account. |
| commandAndControl | The entity is being used for command and control. For example, a C2 \(command and control\) domain used by malware. |
| loaded | The entity was loaded by a process under the control of an attacker. For example, a DLL was loaded into an attacker-controlled process. |
| suspicious | The entity is suspected of being malicious or controlled by an attacker but hasn't been incriminated. |
| policyViolator | The entity is a violator of a customer defined policy. |
| unknownFutureValue | Evolvable enumeration sentinel value. Don't use. |

### evidenceVerdict values

| Member | Description |
| :--- | :--- |
| unknown | No verdict was determined for the evidence. |
| suspicious | Recommended remediation actions awaiting approval. |
| malicious | The evidence was determined to be malicious. |
| noThreatsFound | No threat was detected - the evidence is benign. |
| unknownFutureValue | Evolvable enumeration sentinel value. Don't use. |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.security.alertEvidence",
  "createdDateTime": "String (timestamp)",
  "verdict": "String",
  "remediationStatus": "String",
  "remediationStatusDetails": "String",
  "roles": [
    "String"
  ],
  "detailedRoles": [
    "String"
  ],
  "tags": [
    "String"
  ]
}
```
