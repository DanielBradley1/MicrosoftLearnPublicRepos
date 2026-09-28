<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-rapolicy-windows10xscepcertificateprofile?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# windows10XSCEPCertificateProfile resource type

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

Windows X SCEP Certificate configuration profile

Inherits from [windows10XCertificateProfile](https://learn.microsoft.com/en-us/graph/api/resources/intune-rapolicy-windows10xcertificateprofile?view=graph-rest-beta)

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List windows10XSCEPCertificateProfiles](https://learn.microsoft.com/en-us/graph/api/intune-rapolicy-windows10xscepcertificateprofile-list?view=graph-rest-beta) | [windows10XSCEPCertificateProfile](https://learn.microsoft.com/en-us/graph/api/resources/intune-rapolicy-windows10xscepcertificateprofile?view=graph-rest-beta) collection | List properties and relationships of the [windows10XSCEPCertificateProfile](https://learn.microsoft.com/en-us/graph/api/resources/intune-rapolicy-windows10xscepcertificateprofile?view=graph-rest-beta) objects. |
| [Get windows10XSCEPCertificateProfile](https://learn.microsoft.com/en-us/graph/api/intune-rapolicy-windows10xscepcertificateprofile-get?view=graph-rest-beta) | [windows10XSCEPCertificateProfile](https://learn.microsoft.com/en-us/graph/api/resources/intune-rapolicy-windows10xscepcertificateprofile?view=graph-rest-beta) | Read properties and relationships of the [windows10XSCEPCertificateProfile](https://learn.microsoft.com/en-us/graph/api/resources/intune-rapolicy-windows10xscepcertificateprofile?view=graph-rest-beta) object. |
| [Create windows10XSCEPCertificateProfile](https://learn.microsoft.com/en-us/graph/api/intune-rapolicy-windows10xscepcertificateprofile-create?view=graph-rest-beta) | [windows10XSCEPCertificateProfile](https://learn.microsoft.com/en-us/graph/api/resources/intune-rapolicy-windows10xscepcertificateprofile?view=graph-rest-beta) | Create a new [windows10XSCEPCertificateProfile](https://learn.microsoft.com/en-us/graph/api/resources/intune-rapolicy-windows10xscepcertificateprofile?view=graph-rest-beta) object. |
| [Delete windows10XSCEPCertificateProfile](https://learn.microsoft.com/en-us/graph/api/intune-rapolicy-windows10xscepcertificateprofile-delete?view=graph-rest-beta) | None | Deletes a [windows10XSCEPCertificateProfile](https://learn.microsoft.com/en-us/graph/api/resources/intune-rapolicy-windows10xscepcertificateprofile?view=graph-rest-beta). |
| [Update windows10XSCEPCertificateProfile](https://learn.microsoft.com/en-us/graph/api/intune-rapolicy-windows10xscepcertificateprofile-update?view=graph-rest-beta) | [windows10XSCEPCertificateProfile](https://learn.microsoft.com/en-us/graph/api/resources/intune-rapolicy-windows10xscepcertificateprofile?view=graph-rest-beta) | Update the properties of a [windows10XSCEPCertificateProfile](https://learn.microsoft.com/en-us/graph/api/resources/intune-rapolicy-windows10xscepcertificateprofile?view=graph-rest-beta) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | Profile identifier Inherited from [deviceManagementResourceAccessProfileBase](https://learn.microsoft.com/en-us/graph/api/resources/intune-rapolicy-devicemanagementresourceaccessprofilebase?view=graph-rest-beta) |
| version | Int32 | Version of the profile Inherited from [deviceManagementResourceAccessProfileBase](https://learn.microsoft.com/en-us/graph/api/resources/intune-rapolicy-devicemanagementresourceaccessprofilebase?view=graph-rest-beta) |
| displayName | String | Profile display name Inherited from [deviceManagementResourceAccessProfileBase](https://learn.microsoft.com/en-us/graph/api/resources/intune-rapolicy-devicemanagementresourceaccessprofilebase?view=graph-rest-beta) |
| description | String | Profile description Inherited from [deviceManagementResourceAccessProfileBase](https://learn.microsoft.com/en-us/graph/api/resources/intune-rapolicy-devicemanagementresourceaccessprofilebase?view=graph-rest-beta) |
| creationDateTime | DateTimeOffset | DateTime profile was created Inherited from [deviceManagementResourceAccessProfileBase](https://learn.microsoft.com/en-us/graph/api/resources/intune-rapolicy-devicemanagementresourceaccessprofilebase?view=graph-rest-beta) |
| lastModifiedDateTime | DateTimeOffset | DateTime profile was last modified Inherited from [deviceManagementResourceAccessProfileBase](https://learn.microsoft.com/en-us/graph/api/resources/intune-rapolicy-devicemanagementresourceaccessprofilebase?view=graph-rest-beta) |
| roleScopeTagIds | String collection | Scope Tags Inherited from [deviceManagementResourceAccessProfileBase](https://learn.microsoft.com/en-us/graph/api/resources/intune-rapolicy-devicemanagementresourceaccessprofilebase?view=graph-rest-beta) |
| serverApplicabilityRules | [applicabilityRule](https://learn.microsoft.com/en-us/graph/api/resources/intune-rapolicy-applicabilityrule?view=graph-rest-beta) collection | The list of Applicability Rules for a Device Configuration Profile Inherited from [deviceManagementResourceAccessProfileBase](https://learn.microsoft.com/en-us/graph/api/resources/intune-rapolicy-devicemanagementresourceaccessprofilebase?view=graph-rest-beta) |
| certificateStore | [certificateStore](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-certificatestore?view=graph-rest-beta) | Target store certificate. Possible values are: `user`, `machine`. |
| certificateValidityPeriodScale | [certificateValidityPeriodScale](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-certificatevalidityperiodscale?view=graph-rest-beta) | Scale for the Certificate Validity Period. Possible values are: `days`, `months`, `years`. |
| certificateValidityPeriodValue | Int32 | Value for the Certificate Validity Period |
| extendedKeyUsages | [extendedKeyUsage](https://learn.microsoft.com/en-us/graph/api/resources/intune-rapolicy-extendedkeyusage?view=graph-rest-beta) collection | Extended Key Usage \(EKU\) settings. |
| hashAlgorithm | [hashAlgorithms](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-hashalgorithms?view=graph-rest-beta) collection | SCEP Hash Algorithm. |
| keySize | [keySize](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-keysize?view=graph-rest-beta) | SCEP Key Size. Possible values are: `size1024`, `size2048`, `size4096`. |
| keyStorageProvider | [keyStorageProviderOption](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-keystorageprovideroption?view=graph-rest-beta) | Key Storage Provider \(KSP\). Possible values are: `useTpmKspOtherwiseUseSoftwareKsp`, `useTpmKspOtherwiseFail`, `usePassportForWorkKspOtherwiseFail`, `useSoftwareKsp`. |
| keyUsage | [keyUsages](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-keyusages?view=graph-rest-beta) | SCEP Key Usage. Possible values are: `keyEncipherment`, `digitalSignature`. |
| renewalThresholdPercentage | Int32 | Certificate renewal threshold percentage |
| rootCertificateId | Guid | Trusted Root Certificate ID |
| scepServerUrls | String collection | SCEP Server Url\(s\). |
| subjectAlternativeNameFormats | [windows10XCustomSubjectAlternativeName](https://learn.microsoft.com/en-us/graph/api/resources/intune-rapolicy-windows10xcustomsubjectalternativename?view=graph-rest-beta) collection | Custom AAD Attributes. |
| subjectNameFormatString | String | Custom format to use with SubjectNameFormat = Custom. Example: CN={{EmailAddress}},E={{EmailAddress}},OU=Enterprise Users,O=Contoso Corporation,L=Redmond,ST=WA,C=US |

## Relationships

| Relationship | Type | Description |
| :--- | :--- | :--- |
| assignments | [deviceManagementResourceAccessProfileAssignment](https://learn.microsoft.com/en-us/graph/api/resources/intune-rapolicy-devicemanagementresourceaccessprofileassignment?view=graph-rest-beta) collection | The list of assignments for the device configuration profile. Inherited from [deviceManagementResourceAccessProfileBase](https://learn.microsoft.com/en-us/graph/api/resources/intune-rapolicy-devicemanagementresourceaccessprofilebase?view=graph-rest-beta) |

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.windows10XSCEPCertificateProfile",
  "id": "String (identifier)",
  "version": 1024,
  "displayName": "String",
  "description": "String",
  "creationDateTime": "String (timestamp)",
  "lastModifiedDateTime": "String (timestamp)",
  "roleScopeTagIds": [
    "String"
  ],
  "serverApplicabilityRules": [
    {
      "@odata.type": "microsoft.graph.applicabilityRule",
      "filterType": "String"
    }
  ],
  "certificateStore": "String",
  "certificateValidityPeriodScale": "String",
  "certificateValidityPeriodValue": 1024,
  "extendedKeyUsages": [
    {
      "@odata.type": "microsoft.graph.extendedKeyUsage",
      "name": "String",
      "objectIdentifier": "String"
    }
  ],
  "hashAlgorithm": [
    "String"
  ],
  "keySize": "String",
  "keyStorageProvider": "String",
  "keyUsage": "String",
  "renewalThresholdPercentage": 1024,
  "rootCertificateId": "Guid",
  "scepServerUrls": [
    "String"
  ],
  "subjectAlternativeNameFormats": [
    {
      "@odata.type": "microsoft.graph.windows10XCustomSubjectAlternativeName",
      "sanType": "String",
      "name": "String"
    }
  ],
  "subjectNameFormatString": "String"
}
```
