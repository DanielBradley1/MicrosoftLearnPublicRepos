<!-- Source: https://learn.microsoft.com/en-us/entra/msal/java/advanced/best-practices-enterprise -->
<!-- Sitemap-Last-Modified: 2024-01-27 -->

# Best practices for enterprises

To build robust, enterprise-ready applications, you will need to ensure that you implement a few additional guardrails. We recommend developers to:

- Handle exceptions, both when acquiring a token, but also when calling a protected web API. In particular, if an application runs in a Microsoft Entra tenant where the tenant admins have set [Conditional Access](https://learn.microsoft.com/en-us/entra/identity/conditional-access/overview) policies to enforce Multiple Factor Authentication \(MFA\), you will need to handle a claim challenge which is described in [Exceptions](https://learn.microsoft.com/en-us/entra/msal/java/advanced/exceptions).
- Enable [Logging](https://learn.microsoft.com/en-us/entra/msal/java/advanced/msal-logging-java) to troubleshoot applications, while respecting user privacy and remain compliant with privacy regulations, such as GDPR.
