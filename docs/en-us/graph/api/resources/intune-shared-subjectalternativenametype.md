<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-shared-subjectalternativenametype?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# subjectAlternativeNameType enum type

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

Subject Alternative Name Options.

## Members

| Member | Value | Description |
| :--- | :--- | :--- |
| none | 0 | No subject alternative name. |
| emailAddress | 1 | Email address. |
| userPrincipalName | 2 | User Principal Name \(UPN\). |
| customAzureADAttribute | 4 | Custom Azure AD Attribute. |
| domainNameService | 8 | Domain Name Service \(DNS\). |
| universalResourceIdentifier | 16 | Universal Resource Identifier \(URI\). |
