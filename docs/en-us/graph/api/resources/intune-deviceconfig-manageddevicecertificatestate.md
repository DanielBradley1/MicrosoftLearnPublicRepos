<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-manageddevicecertificatestate?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# managedDeviceCertificateState resource type

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

## Methods

| Method | Return Type | Description |
| :--- | :--- | :--- |
| [List managedDeviceCertificateStates](https://learn.microsoft.com/en-us/graph/api/intune-deviceconfig-manageddevicecertificatestate-list?view=graph-rest-beta) | [managedDeviceCertificateState](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-manageddevicecertificatestate?view=graph-rest-beta) collection | List properties and relationships of the [managedDeviceCertificateState](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-manageddevicecertificatestate?view=graph-rest-beta) objects. |
| [Get managedDeviceCertificateState](https://learn.microsoft.com/en-us/graph/api/intune-deviceconfig-manageddevicecertificatestate-get?view=graph-rest-beta) | [managedDeviceCertificateState](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-manageddevicecertificatestate?view=graph-rest-beta) | Read properties and relationships of the [managedDeviceCertificateState](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-manageddevicecertificatestate?view=graph-rest-beta) object. |
| [Create managedDeviceCertificateState](https://learn.microsoft.com/en-us/graph/api/intune-deviceconfig-manageddevicecertificatestate-create?view=graph-rest-beta) | [managedDeviceCertificateState](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-manageddevicecertificatestate?view=graph-rest-beta) | Create a new [managedDeviceCertificateState](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-manageddevicecertificatestate?view=graph-rest-beta) object. |
| [Delete managedDeviceCertificateState](https://learn.microsoft.com/en-us/graph/api/intune-deviceconfig-manageddevicecertificatestate-delete?view=graph-rest-beta) | None | Deletes a [managedDeviceCertificateState](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-manageddevicecertificatestate?view=graph-rest-beta). |
| [Update managedDeviceCertificateState](https://learn.microsoft.com/en-us/graph/api/intune-deviceconfig-manageddevicecertificatestate-update?view=graph-rest-beta) | [managedDeviceCertificateState](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-manageddevicecertificatestate?view=graph-rest-beta) | Update the properties of a [managedDeviceCertificateState](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-manageddevicecertificatestate?view=graph-rest-beta) object. |

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| id | String | Key of the entity. |
| devicePlatform | [devicePlatformType](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-deviceplatformtype?view=graph-rest-beta) | Device platform. Possible values are: `android`, `androidForWork`, `iOS`, `macOS`, `windowsPhone81`, `windows81AndLater`, `windows10AndLater`, `androidWorkProfile`, `unknown`, `androidAOSP`, `androidMobileApplicationManagement`, `iOSMobileApplicationManagement`, `unknownFutureValue`, `windowsMobileApplicationManagement`. |
| certificateKeyUsage | [keyUsages](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-keyusages?view=graph-rest-beta) | Key usage. Possible values are: `keyEncipherment`, `digitalSignature`. |
| certificateValidityPeriodUnits | [certificateValidityPeriodScale](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-certificatevalidityperiodscale?view=graph-rest-beta) | Validity period units. Possible values are: `days`, `months`, `years`. |
| certificateIssuanceState | [certificateIssuanceStates](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-certificateissuancestates?view=graph-rest-beta) | Issuance State. Possible values are: `unknown`, `challengeIssued`, `challengeIssueFailed`, `requestCreationFailed`, `requestSubmitFailed`, `challengeValidationSucceeded`, `challengeValidationFailed`, `issueFailed`, `issuePending`, `issued`, `responseProcessingFailed`, `responsePending`, `enrollmentSucceeded`, `enrollmentNotNeeded`, `revoked`, `removedFromCollection`, `renewVerified`, `installFailed`, `installed`, `deleteFailed`, `deleted`, `renewalRequested`, `requested`. |
| certificateKeyStorageProvider | [keyStorageProviderOption](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-keystorageprovideroption?view=graph-rest-beta) | Key Storage Provider. Possible values are: `useTpmKspOtherwiseUseSoftwareKsp`, `useTpmKspOtherwiseFail`, `usePassportForWorkKspOtherwiseFail`, `useSoftwareKsp`. |
| certificateSubjectNameFormat | [subjectNameFormat](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-subjectnameformat?view=graph-rest-beta) | Subject name format. Possible values are: `commonName`, `commonNameIncludingEmail`, `commonNameAsEmail`, `custom`, `commonNameAsIMEI`, `commonNameAsSerialNumber`, `commonNameAsAadDeviceId`, `commonNameAsIntuneDeviceId`, `commonNameAsDurableDeviceId`. |
| certificateSubjectAlternativeNameFormat | [subjectAlternativeNameType](https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-subjectalternativenametype?view=graph-rest-beta) | Subject alternative name format. Possible values are: `none`, `emailAddress`, `userPrincipalName`, `customAzureADAttribute`, `domainNameService`, `universalResourceIdentifier`. |
| certificateRevokeStatus | [certificateRevocationStatus](https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-certificaterevocationstatus?view=graph-rest-beta) | Revoke status. Possible values are: `none`, `pending`, `issued`, `failed`, `revoked`. |
| certificateProfileDisplayName | String | Certificate profile display name |
| deviceDisplayName | String | Device display name |
| userDisplayName | String | User display name |
| certificateExpirationDateTime | DateTimeOffset | Certificate expiry date |
| certificateLastIssuanceStateChangedDateTime | DateTimeOffset | Last certificate issuance state change |
| lastCertificateStateChangeDateTime | DateTimeOffset | Last certificate issuance state change |
| certificateIssuer | String | Issuer |
| certificateThumbprint | String | Thumbprint |
| certificateSerialNumber | String | Serial number |
| certificateKeyLength | Int32 | Key length |
| certificateEnhancedKeyUsage | String | Extended key usage |
| certificateValidityPeriod | Int32 | Validity period |
| certificateSubjectNameFormatString | String | Subject name format string for custom subject name formats |
| certificateSubjectAlternativeNameFormatString | String | Subject alternative name format string for custom formats |
| certificateIssuanceDateTime | DateTimeOffset | Issuance date |
| certificateErrorCode | Int32 | Error code |

## Relationships

None

## JSON Representation

Here is a JSON representation of the resource.

```json
{
  "@odata.type": "#microsoft.graph.managedDeviceCertificateState",
  "id": "String (identifier)",
  "devicePlatform": "String",
  "certificateKeyUsage": "String",
  "certificateValidityPeriodUnits": "String",
  "certificateIssuanceState": "String",
  "certificateKeyStorageProvider": "String",
  "certificateSubjectNameFormat": "String",
  "certificateSubjectAlternativeNameFormat": "String",
  "certificateRevokeStatus": "String",
  "certificateProfileDisplayName": "String",
  "deviceDisplayName": "String",
  "userDisplayName": "String",
  "certificateExpirationDateTime": "String (timestamp)",
  "certificateLastIssuanceStateChangedDateTime": "String (timestamp)",
  "lastCertificateStateChangeDateTime": "String (timestamp)",
  "certificateIssuer": "String",
  "certificateThumbprint": "String",
  "certificateSerialNumber": "String",
  "certificateKeyLength": 1024,
  "certificateEnhancedKeyUsage": "String",
  "certificateValidityPeriod": 1024,
  "certificateSubjectNameFormatString": "String",
  "certificateSubjectAlternativeNameFormatString": "String",
  "certificateIssuanceDateTime": "String (timestamp)",
  "certificateErrorCode": 1024
}
```
