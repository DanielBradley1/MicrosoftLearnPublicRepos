<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/work-iq/permissions -->
<!-- Sitemap-Last-Modified: 2026-06-17 -->

# Work IQ API permissions reference

Work IQ APIs are protected by Microsoft Entra ID. Applications that access the Work IQ APIs must use [Microsoft Entra ID OAuth 2.0](https://learn.microsoft.com/en-us/entra/architecture/auth-oauth2) to authenticate and request authorization. This article lists the permissions exposed by Work IQ APIs.

Important

An organization administrator must [enable Work IQ in your organization](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/work-iq/enable-work-iq) before these permissions can be used by applications.

## Application ID URI

The application ID URI for Work IQ APIs is `api://workiq.svc.cloud.microsoft`. This URI is the prefix for all Work IQ permission scopes in the OAuth protocol.

For example, to request the `WorkIQAgent.Ask` permission, use the OAuth `scope` value `api://workiq.svc.cloud.microsoft/WorkIQAgent.Ask`.

## Permissions

### WorkIQAgent.Ask

| Category | Application | Delegated |
| --- | --- | --- |
| Identifier | - | 0b1715fd-f4bf-4c63-b16d-5be31f9847c2 |
| DisplayText | - | Ask Work IQ agents on behalf of the user |
| Description | - | Allows the app to ask Work IQ agents questions and receive responses on behalf of the signed-in user. This includes read and write access to Microsoft 365 resources that are accessible to Work IQ agents and scoped to the signed-in user. |
| AdminConsentRequired | - | Yes |

---
