<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-cloudpkigraphservice-cloudcertificationauthoritytype?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# cloudCertificationAuthorityType enum type

Namespace: microsoft.graph

> **Important:** Microsoft supports Intune /beta APIs, but they are subject to more frequent change. Microsoft recommends using version v1.0 when possible. Check an API's availability in version v1.0 using the Version selector.

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

Enum type of possible certificate authority types. This feature supports a two-tier certification authority model with a root certification authority and one or more child issuing \(intermediate\) certification authorities.

## Members

| Member | Value | Description |
| :--- | :--- | :--- |
| unknown | 0 |  |
| rootCertificationAuthority | 1 |  |
| issuingCertificationAuthority | 2 |  |
| issuingCertificationAuthorityWithExternalRoot | 3 |  |
| unknownFutureValue | 4 |  |
