<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/intune-deviceconfig-firewallcertificaterevocationlistcheckmethodtype?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-07-11 -->

# firewallCertificateRevocationListCheckMethodType enum type

Namespace: microsoft.graph

> **Note:** The Microsoft Graph API for Intune requires an [active Intune license](https://go.microsoft.com/fwlink/?linkid=839381) for the tenant.

Possible values for firewallCertificateRevocationListCheckMethod

## Members

| Member | Value | Description |
| :--- | :--- | :--- |
| deviceDefault | 0 | No value configured by Intune, do not override the user-configured device default value |
| none | 1 | Do not check certificate revocation list |
| attempt | 2 | Attempt CRL check and allow a certificate only if the certificate is confirmed by the check |
| require | 3 | Require a successful CRL check before allowing a certificate |
