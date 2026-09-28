<!-- Source: https://learn.microsoft.com/en-us/entra/external-id/customers/migrate-to-external-id -->
<!-- Sitemap-Last-Modified: 2026-05-27 -->

# Plan and execute a migration to Microsoft Entra External ID

Developers building applications often control authentication and authorization for customers accessing their applications. They use customer identity access management \(CIAM\) solutions to avoid building and maintaining a full identity and access management \(IAM\) solution. Microsoft Entra External ID lets developers connect their applications to a customer-focused version of Microsoft Entra ID, a standard IAM solution. This guide gives a migration path and resources for developers and identity teams.

## What is Microsoft Entra External ID?

For organizations and businesses that want to make their apps available to consumers and business customers, [Microsoft Entra External ID](https://learn.microsoft.com/en-us/entra/external-id/customers/overview-customers-ciam) lets you add CIAM features such as self-service registration, personalized sign-in experiences, and customer account management. Because these CIAM capabilities are built into Microsoft Entra ID, you benefit from platform features like enhanced security, compliance, and scalability.

## Why migrate from other CIAM solutions?

Organizations might migrate to Microsoft Entra External ID from another tool based on strategic goals such as:

- Consolidate cloud identity providers
- Align with an existing enterprise identity solution
- Enhance security and compliance
- Access to [strong developer guidance and an active community](https://developer.microsoft.com/identity/external-id)
- [Feature availability](https://learn.microsoft.com/en-us/entra/external-id/customers/concept-supported-features-customers#general-feature-comparison)
- [Reduce costs](https://azure.microsoft.com/pricing/details/microsoft-entra-external-id)

## Plan your migration

The [Microsoft Entra External ID deployment guide](https://learn.microsoft.com/en-us/entra/architecture/deployment-external-intro) helps organizations get started with their deployment if they're new to the concept of a CIAM solution. Following that along with the steps outlined in this article help organizations with existing CIAM deployments complete their migration to Microsoft Entra External ID. Organizations start by [evaluating the availability of critical features in Microsoft Entra External ID](https://learn.microsoft.com/en-us/entra/external-id/customers/concept-supported-features-customers#general-feature-comparison) to confirm readiness for migration.

If you plan to migrate a workload from AWS to Azure, we suggest you have a methodical approach to that initiative. Component selection and Azure fundamentals are important parts of that larger process. To fine tune your migration plan using Microsoft's guidance, see [Migrate security services from Amazon Web Services](https://learn.microsoft.com/en-us/azure/migration/migrate-security-from-aws).

### Migration steps

This guide helps you migrate legacy customer identity access management \(CIAM\) solutions to Microsoft Entra External ID. Follow this series of articles to navigate the steps in the migration process.

| Stage | Steps |
| --- | --- |
| Premigration planning | • Map legacy CIAM features to [Microsoft Entra External ID capabilities](https://learn.microsoft.com/en-us/entra/external-id/customers/overview-customers-ciam).  <br>• Complete an [inventory of the existing CIAM solution](#inventory). |
| Microsoft Entra External ID setup | • [Create an external tenant](https://learn.microsoft.com/en-us/entra/external-id/customers/how-to-create-external-tenant-portal).  <br>• [Add and manage admin accounts](https://learn.microsoft.com/en-us/entra/external-id/customers/how-to-manage-admin-accounts).  <br>• [Enable other identity providers](https://learn.microsoft.com/en-us/entra/external-id/customers/concept-authentication-methods-customers).  <br>• [Register all customer-facing applications](https://learn.microsoft.com/en-us/entra/identity-platform/quickstart-register-app).  <br>• [Add an application to the user flow](https://learn.microsoft.com/en-us/entra/external-id/customers/how-to-user-flow-add-application).  <br>• [Test the user flow](https://learn.microsoft.com/en-us/entra/external-id/customers/how-to-test-user-flows). |
| Identity flows and branding | • [Add a sign-up and sign-in user flow](https://learn.microsoft.com/en-us/entra/external-id/customers/how-to-user-flow-sign-up-sign-in-customers)  <br>• [Add an application to the user flow](https://learn.microsoft.com/en-us/entra/external-id/customers/how-to-user-flow-add-application)  <br>• [Manage access](https://learn.microsoft.com/en-us/entra/external-id/customers/how-to-use-app-roles-customers)  <br>• [Test the user flow](https://learn.microsoft.com/en-us/entra/external-id/customers/how-to-test-user-flows)  <br>• [Customize branding](https://learn.microsoft.com/en-us/entra/external-id/customers/how-to-customize-branding-customers) |
| Security and monitoring | • [Configure MFA](https://learn.microsoft.com/en-us/entra/external-id/customers/how-to-multifactor-authentication-customers)  <br>• [Create dashboards](https://learn.microsoft.com/en-us/entra/external-id/customers/how-to-user-insights) \(retiring August 31, 2026; see [migration guidance](https://learn.microsoft.com/en-us/entra/external-id/customers/how-to-user-insights#migrate-from-user-insights)\)  <br>• [Set up Azure Monitor](https://learn.microsoft.com/en-us/entra/external-id/customers/how-to-azure-monitor) |
| Test and rollout | • Define your rollout strategy.  <br>• Import the final batch of users if needed using the [Microsoft Graph API](https://learn.microsoft.com/en-us/graph/api/user-post-users).  <br>• Cut over live traffic to Microsoft Entra External ID.  <br>• Monitor live authentication logs and error rates.  <br>• Collect feedback.  <br>• Decommission legacy solution. |

### Inventory

Take inventory of the existing configuration and architecture, including:

- Users
- Access and security groups
- Connected applications
- Sign-up and sign-in user flows
- Multifactor authentication mechanisms
- Social identity providers
- Any specific compliance or regulatory requirements

At this phase, determine if user data transformation is required, then complete [transformation and mapping](https://learn.microsoft.com/en-us/entra/external-id/customers/concept-user-attributes).

## Related content

- Learn more in [developer resources](https://developer.microsoft.com/identity/external-id)
- Review the [Microsoft Entra External ID deployment guide](https://learn.microsoft.com/en-us/entra/architecture/deployment-external-intro)
- [Integrate authentication into your consumer and business customer applications](https://learn.microsoft.com/en-us/entra/external-id/customers/visual-studio-code-extension)
- [Compare AWS and Azure identity management solutions](https://learn.microsoft.com/en-us/azure/architecture/aws-professional/security-identity)
- [Build a sample app to evaluate Microsoft Entra External ID](https://learn.microsoft.com/en-us/training/entra-external-identities/)
