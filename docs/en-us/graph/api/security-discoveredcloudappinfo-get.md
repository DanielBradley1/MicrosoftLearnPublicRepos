<!-- Source: https://learn.microsoft.com/en-us/graph/api/security-discoveredcloudappinfo-get?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2024-12-17 -->

# Get discoveredCloudAppInfo

Namespace: microsoft.graph.security

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Get the [details](https://learn.microsoft.com/en-us/graph/api/resources/security-discoveredcloudappinfo?view=graph-rest-beta) of the security, legal, and compliance risk attributes of the discovered cloud apps.

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | CloudApp-Discovery.Read.All | Not available. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | CloudApp-Discovery.Read.All | Not available. |

## HTTP request

```http
GET /security/dataDiscovery/cloudAppDiscovery/uploadedStreams/{streamId}/microsoft.graph.security.aggregatedAppsDetails(period=duration'{duration}')/{appId}/appInfo
```

Note

`period` is a required parameter of type Duration that specifies the time frame for querying the data. Supported time frames include the last 7, 30, or 90 days.

## Optional query parameters

This method supports the `$select` OData query parameter to help customize the response. For general information, see [OData query parameters](https://learn.microsoft.com/en-us/graph/query-parameters).

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |

## Request body

Don't supply a request body for this method.

## Response

If successful, this method returns a `200 OK` response code and a [microsoft.graph.security.discoveredCloudAppInfo](https://learn.microsoft.com/en-us/graph/api/resources/security-discoveredcloudappinfo?view=graph-rest-beta) object in the response body.

## Examples

### Request

The following example shows a request.

- [HTTP](#tabpanel_1_http)
- [JavaScript](#tabpanel_1_javascript)

```msgraph
GET https://graph.microsoft.com/beta/security/dataDiscovery/cloudAppDiscovery/uploadedStreams/93b60b3e-3a28-bf33-2d73-3cb0199c5f7a/microsoft.graph.security.aggregatedAppsDetails(period=duration'P90D')/12345/appInfo
```

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

let discoveredCloudAppInfo = await client.api('/security/dataDiscovery/cloudAppDiscovery/uploadedStreams/93b60b3e-3a28-bf33-2d73-3cb0199c5f7a/microsoft.graph.security.aggregatedAppsDetails(period=duration'P90D')/12345/appInfo')
	.version('beta')
	.get();
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
    "@odata.type": "#microsoft.graph.security.discoveredCloudAppInfo",
    "id": "93b60b3e-3a28-bf33-2d73-3cb0199c5f7a",
    "isGdprDataProtectionImpactAssessment": "unknown",
    "isGdprDataProtectionSecureCrossBorderDataTransfer": "unknown",
    "isHttpSecurityHeadersContentSecurityPolicy": "unknown",
    "isHttpSecurityHeadersStrictTransportSecurity": "unknown",
    "isHttpSecurityHeadersXContentTypeOptions": "unknown",
    "isHttpSecurityHeadersXFrameOptions": "unknown",
    "isHttpSecurityHeadersXXssProtection": "unknown",
    "isTrustedCertificate": "unknown",
    "isValidCertificateName": "unknown",
    "isCoppaCompliant": "unknown",
    "isFerpaCompliant": "unknown",
    "isFfiecCompliant": "unknown",
    "isFinraCompliant": "unknown",
    "isFismaCompliant": "unknown",
    "isGaapCompliant": "unknown",
    "isGdprDataProtectionOfficer": "unknown",
    "isGdprImpactAssessment": "unknown",
    "isGdprLawfulBasisForProcessing": "unknown",
    "isGdprReportDataBreaches": "unknown",
    "isGdprRightToAccess": "unknown",
    "isGdprRightToBeInformed": "unknown",
    "isGdprRightToDataPortablility": "unknown",
    "isGdprRightToErasure": "unknown",
    "isGdprRightToObject": "unknown",
    "isGdprRightToRectification": "unknown",
    "isGdprRightToRestrictionOfProcessing": "unknown",
    "isGdprRightsRelatedToAutomatedDecisionMaking": "unknown",
    "isGdprSecureCrossBorderDataControl": "unknown",
    "isGlbaCompliant": "unknown",
    "isHipaaCompliant": "unknown",
    "isHitrustCsfCompliant": "unknown",
    "isIsae3402Compliant": "unknown",
    "isIso27018Compliant": "unknown",
    "isItarCompliant": "unknown",
    "isPrivacyShieldCompliant": "unknown",
    "isSoc1Compliant": "unknown",
    "isSoxCompliant": "unknown",
    "isSsae16Compliant": "unknown",
    "dataTypes": "documents",
    "csaStarLevel": "continuousMonitoring",
    "fedRampLevel": "moderate",
    "pciDssVersion": "v3_2_1",
    "dataAtRestEncryptionMethod": "des3",
    "holding": "public",
    "encryptionProtocol": "tls1_0", 
    "dataCenter": "Multiple Locations",
    "headquarters": "United States",
    "founded": 2001,
    "isAdminAuditTrail": "unknown",
    "isCobitCompliant": "unknown",
    "isDataAuditTrail": "unknown",
    "isDataClassification": "unknown",
    "isDataOwnership": "unknown",
    "dataRetentionPolicy": "dataRetained",
    "isDisasterRecoveryPlan": "unknown",
    "isDmca": "unknown",
    "isFileSharing": "unknown",
    "isIpAddressRestriction": "unknown",
    "isIso27001Compliant": "unknown",
    "isIso27017Compliant": "unknown",
    "isMultiFactorAuthentication": "unknown",
    "isPasswordPolicy": "unknown",
    "isPasswordPolicyChangePasswordPeriod": "unknown",
    "isPasswordPolicyCharacterCombination": "unknown",
    "isPasswordPolicyPasswordHistoryAndReuse": "unknown",
    "isPasswordPolicyPasswordLengthLimit": "unknown",
    "isPasswordPolicyPersonalInformationUse": "unknown",
    "isPenetrationTesting": "unknown",
    "isRememberPassword": "unknown",
    "isRequiresUserAuthentication": "unknown",
    "isSoc2Compliant": "unknown",
    "isSoc3Compliant": "unknown",
    "isSp80053Compliant": "unknown",
    "isSupportsSaml": "unknown",
    "isUserAuditTrail": "unknown",
    "isUserCanUploadData": "unknown",
    "isUserRolesSupport": "unknown",
    "latestBreachDateTime": "2023-09-15T13:45:30Z",
    "domainRegistrationDateTime": "2020-01-01T00:00:00Z",
    "gdprReadinessStatement": "Our app complies with GDPR regulations and ensures data protection.",
    "hostingCompany": "Contoso Hosting Services",
    "logonUrls": "https://login.contosoapp.com",
    "vendor": "Contoso Ltd."
}
```
