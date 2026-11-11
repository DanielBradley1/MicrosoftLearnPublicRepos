<!-- Source: https://learn.microsoft.com/en-us/intune/device-security/compliance/become-mobile-device-management-compliance-provider -->
<!-- Sitemap-Last-Modified: 2026-11-09 -->

# Become a Microsoft Intune Mobile Device Management Partner

The Third-Party Compliance MDM Partner Program is designed for mobile device management \(MDM\) solutions that determine and manage compliance for user-associated devices and use Microsoft Entra ID to communicate device compliance status to Microsoft services.

## Supported scenarios

To be eligible as an Intune compliance partner, your MDM solution must meet the following criteria:

- Manage devices using MDM protocols.
- Evaluate device compliance for user-based scenarios.
- Use Microsoft Entra ID for user identification.
- Support one or more of the following platforms: Android, iOS/iPadOS, and macOS.

## Apply to become an Intune compliance MDM partner

Partners interested in integrating with Microsoft should begin by creating a Microsoft Entra app for their MDM product. For instructions, see [Register a Microsoft Entra app and create a service principal](https://learn.microsoft.com/en-us/entra/identity-platform/howto-create-service-principal-portal).

After you create a Microsoft Entra app and obtain a Microsoft Entra app ID, you can apply to become a partner through the [Intune Compliance MDM Partner Application](https://forms.cloud.microsoft/r/GKYuFnrSdv).

Microsoft uses the submitted information to validate that:

- The solution aligns with the intended Intune and Microsoft Entra ID Conditional Access scenario.
- The proposed integration is appropriate for the Intune Device Compliance API.
- The partner is prepared to provide enterprise-grade support to customers after launch.

To protect your organization and customers, do not include detailed implementation information, source code, API payloads, security internals, proprietary design details, or other information not reasonably necessary for Microsoft's evaluation.

If Microsoft accepts your application, an API agreement is sent to the business or legal contact identified by your organization for review and signature. After your organization signs and returns the agreement, Microsoft provides the technical documentation required to begin developing the integration.

Partners are responsible for implementing the integration based on the provided documentation. Microsoft does not guarantee dedicated onboarding assistance, implementation guidance, or engineering support during development.

Submission of an application does not guarantee API documentation access, approval to integrate, public listing, or production availability. Microsoft might request additional information as part of the review process.

Note

For partners onboarded through the new self-service process, Microsoft does not publish partner-specific setup documentation or list each partner by name in the Microsoft Intune admin center. Partners should provide their customers with the setup information required to use their solution.

To configure an MDM integration, a customer adds a custom MDM compliance partner in the Intune admin center by entering the Microsoft Entra application ID provided by their selected third-party MDM provider. Intune uses this application ID to create the connector and enable the partner integration.
