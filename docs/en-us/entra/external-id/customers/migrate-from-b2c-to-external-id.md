<!-- Source: https://learn.microsoft.com/en-us/entra/external-id/customers/migrate-from-b2c-to-external-id -->
<!-- Sitemap-Last-Modified: 2026-04-17 -->

# Migrate from Azure AD B2C to External ID

**Applies to**: ![Green circle with a white check mark symbol that indicates the following content applies to external tenants.](https://learn.microsoft.com/en-us/entra/external-id/media/common/applies-to-yes.png) External tenants \([learn more](https://learn.microsoft.com/en-us/entra/external-id/tenant-configurations)\)

Migrate your users, credentials, and applications from Azure AD B2C to Microsoft Entra External ID using the standard migration approach. This article focuses on migration scenarios where identities already exist in Azure AD B2C and must be transitioned with minimal disruption.

New customers evaluating Microsoft Entra External ID at scale should refer to [Planning your solution](https://learn.microsoft.com/en-us/entra/external-id/customers/concept-planning-your-solution).

If you're an Azure AD B2C customer and haven't yet reviewed the available options for migration, refer to [Plan your migration from Azure AD B2C to External ID](https://learn.microsoft.com/en-us/entra/external-id/customers/plan-your-migration-from-b2c-to-external-id).

In this article, you’ll learn how to:

- Assess your current Azure AD B2C implementation
- Prepare your destination External ID tenant and baseline security
- Migrate users and preserve passwords \(if needed\)
- Validate, monitor, and plan application cutover

## Prerequisites

This article assumes you've already chosen the **standard migration approach**. If you still need to decide between approaches \(standard vs. HSC mode\), start with [Plan your migration from Azure AD B2C to External ID](https://learn.microsoft.com/en-us/entra/external-id/customers/plan-your-migration-from-b2c-to-external-id).

## Stage 1: Assess your current Azure AD B2C implementation

Inventory what you have today so you can recreate equivalent behavior in External ID: applications, user flows, identity providers, token/claim requirements, and any custom business logic.

Use the following feature mapping table as a starting point when translating your Azure AD B2C implementation into External ID configuration.

### Feature mapping table

| Feature | Azure AD B2C | External ID equivalent |
| --- | --- | --- |
| Custom business logic | Custom policies \(XML/IEF\) | Custom authentication extensions |
| Authentication UI | Hosted pages with HTML/CSS | User flows with branding + native authentication |
| User management | Microsoft Graph API | Microsoft Graph API |
| Access policies | Custom policies, user flow conditions | Microsoft Entra conditional access |
| Mobile authentication | Browser-based flows, web redirects | Native authentication SDKs \(local accounts only\) |
| Token customization | Custom claims in policies | Custom authentication extensions |

For a full feature overview, see [Supported features](https://learn.microsoft.com/en-us/entra/external-id/customers/concept-supported-features-customers).

## Stage 2: Prepare your destination External ID tenant

Set up your destination External ID tenant and baseline security, compliance, and monitoring before migrating production users or cutting over applications. For step-by-step deployment guidance for new External ID tenants, see [Planning your solution](https://learn.microsoft.com/en-us/entra/external-id/customers/concept-planning-your-solution).

This stage typically includes:

- [Creating your external tenant](https://learn.microsoft.com/en-us/entra/external-id/customers/how-to-create-external-tenant-portal)
- [Registering applications and configuring user flows](https://learn.microsoft.com/en-us/entra/external-id/customers/how-to-user-flow-sign-up-sign-in-customers)
- [Setting up federation with social identity providers](https://learn.microsoft.com/en-us/entra/external-id/customers/concept-authentication-methods-customers) \(optional\)
- [Configuring security, compliance, and monitoring](https://learn.microsoft.com/en-us/entra/external-id/customers/concept-security-customers)

Complete these steps before you migrate any production user data.

## Stage 3: Migrate users and credentials

In this stage, you decide how users and credentials move from Azure AD B2C to External ID. Bulk user migration is always required, regardless of whether you preserve passwords. The key decision is whether you need to preserve existing passwords, and if so, which approach to use.

### Do you need to preserve passwords?

Decide whether you need to preserve existing passwords. Not every migration requires password preservation. If you don't need it, users can reset their password after migration using [self-service password reset \(SSPR\)](https://learn.microsoft.com/en-us/entra/external-id/customers/how-to-enable-password-reset-customers), or you can move to passwordless or social sign-in options.

You typically **don’t** need password preservation if:

- Users authenticate using **social identity providers** \(for example, Google or Facebook\).
- You plan to use **passwordless authentication** \(such as email one-time passcodes\).
- You're comfortable requiring users to **reset their password** after migration.
- Regulatory requirements mandate renewing user consent. In this case, you can obtain consent through outbound email communications followed by a user-initiated password reset.
- You have access to **plain-text passwords** and can set them directly via Microsoft Graph during bulk user migration.

If you don't need password preservation, complete Stage 1 in [Migrate users and credentials to External ID](https://learn.microsoft.com/en-us/entra/external-id/customers/how-to-migrate-users#stage-1-migrate-user-data) and skip directly to [Stage 4: Validate, monitor, and plan cutover](#stage-4-validate-monitor-and-plan-cutover).

### Choose a password preservation approach

If you need to preserve passwords, choose an approach based on where applications authenticate during the migration.

Use the following decision tree to determine the remaining password-preservation and cutover steps.

[![Diagram of Azure AD B2C migration decision tree showing password preservation and application cutover options.](https://learn.microsoft.com/en-us/entra/external-id/customers/media/migrate-from-b2c-to-external-id/azure-ad-b2c-password-migration-decision-tree.png)](https://learn.microsoft.com/en-us/entra/external-id/customers/media/migrate-from-b2c-to-external-id/azure-ad-b2c-password-migration-decision-tree.png#lightbox)

#### Just-in-Time \(JIT\) password migration \(External ID-initiated\)

In JIT password migration, applications have already moved to External ID endpoints. When a user signs in, External ID uses the `OnPasswordSubmit` custom authentication extension to validate the user's credentials against the legacy IdP, writes the password to the External ID account, and flags the account as migrated.

This diagram provides a deeper view of the standard migration path, combining bulk migration, JIT password migration, and application cutover.

- **1:** User accounts are pre-provisioned in External ID while applications continue to authenticate through your legacy IdP.
- **2:** Applications transition to External ID while passwords are migrated via JIT, with the legacy IdP validating credentials for migration.
- **3:** The legacy IdP is shut down once all users and credentials have been fully moved, leaving External ID as the sole authentication system.

[![Diagram of a three-stage user migration workflow showing legacy IdP, bulk migration, password sync, and cutover to external ID.](https://learn.microsoft.com/en-us/entra/external-id/customers/media/migrate-from-b2c-to-external-id/external-id-jit-migration-workflow-diagram.png)](https://learn.microsoft.com/en-us/entra/external-id/customers/media/migrate-from-b2c-to-external-id/external-id-jit-migration-workflow-diagram.png#lightbox) **Considerations when using JIT password migration**

JIT introduces a coexistence period where both Azure AD B2C and External ID must be monitored and supported. Keep the following in mind:

- **Bulk user migration is still required.** User accounts must exist in External ID before JIT sign-in can work. Complete bulk migration early.
- **Identity state sync grows harder over time.** Profile updates, password changes, and new sign-ups must stay aligned across both systems. Periodic reconciliation is typically required.
- **Users who never sign in won't migrate.** Plan forced password resets or a final bulk migration for remaining users, and set clear cutover timelines.

JIT works best when coexistence is time-boxed, not open-ended.

#### Azure AD B2C-initiated migration

In the B2C-initiated pattern, applications remain on Azure AD B2C endpoints while credentials are harvested in the background. A B2C custom policy calls a REST API to validate credentials against the legacy IdP and write them to the corresponding External ID accounts. Once enough credentials have been migrated, applications cut over to External ID.

- **1:** Applications keep authenticating with the legacy IdP while users are progressively migrated into External ID using Azure Functions for credential validation and background migration.
- **2:** Applications cut over to External ID once most users have been migrated, and External ID becomes the primary authentication service for all core user flows.

[![Diagram of Azure AD B2C migration workflow showing stages, authentication flow, and migration via Azure Functions.](https://learn.microsoft.com/en-us/entra/external-id/customers/media/migrate-from-b2c-to-external-id/azure-ad-b2c-migration-workflow-diagram.png)](https://learn.microsoft.com/en-us/entra/external-id/customers/media/migrate-from-b2c-to-external-id/azure-ad-b2c-migration-workflow-diagram.png#lightbox)

For step-by-step implementation instructions, see [Migrate users and credentials: Legacy IdP-initiated credential harvesting](https://learn.microsoft.com/en-us/entra/external-id/customers/how-to-migrate-users#legacy-idp-initiated-credential-harvesting). In a B2C-initiated migration, this pattern is implemented using Azure AD B2C custom policies that call a REST API during sign-in to validate and harvest credentials.

### Implementation steps

Once you've decided on your approach, complete the following in order:

1. **Migrate user data.** Complete Stage 1 in [Migrate users and credentials to External ID](https://learn.microsoft.com/en-us/entra/external-id/customers/how-to-migrate-users#stage-1-migrate-user-data).

   Tip

   When migrating large numbers of user objects, you might encounter Microsoft Graph throttling limits. See [Throttling limits](https://learn.microsoft.com/en-us/graph/throttling-limits) and [Throttling guidance](https://learn.microsoft.com/en-us/graph/throttling) for best practices.
2. **Prepare for credential migration** \(if preserving passwords\). Complete Stage 2 in [Migrate users and credentials to External ID](https://learn.microsoft.com/en-us/entra/external-id/customers/how-to-migrate-users#stage-2-prepare-for-credential-migration) to set up the migration extension property and flagged user accounts.
3. **Implement your chosen approach:**

   - **JIT.** [Just-in-time password migration](https://learn.microsoft.com/en-us/entra/external-id/customers/how-to-migrate-passwords-just-in-time)
   - **B2C-initiated.** [Migrate users and credentials: Legacy IdP-initiated credential harvesting](https://learn.microsoft.com/en-us/entra/external-id/customers/how-to-migrate-users#legacy-idp-initiated-credential-harvesting), implemented using Azure AD B2C custom policies

## Stage 4: Validate, monitor, and plan cutover

### Validate migration success

Before you move to production and decommission Azure AD B2C apps, validate end-to-end user journeys and integrations:

- Test all authentication flows \(sign-up, sign-in, password reset\).
- Validate token issuance and custom claims.
- Test application and API integrations.
- Verify custom authentication extensions.
- Test password provisioning and native authentication.
- Conduct performance and load tests.
- Ensure security policies and user data integrity.

Note

The following Azure AD B2C features aren't available in Microsoft Entra External ID and should be addressed before migration:

- **Social identity providers configured through B2C custom policies.** Social federation must be reconfigured using External ID's built-in social identity provider support. Third-party identity providers configured through B2C custom policies aren't supported.

See [Test user flows](https://learn.microsoft.com/en-us/entra/external-id/customers/how-to-test-user-flows), [Samples](https://learn.microsoft.com/en-us/entra/external-id/customers/samples-ciam-all), and [Custom extension attribute collection](https://learn.microsoft.com/en-us/entra/identity-platform/custom-extension-attribute-collection) for guidance.

### Monitor and optimize

After you go to production, implement monitoring and analytics to maintain system health and optimize user experience:

- Set up logging and monitoring with Azure Monitor and Microsoft Sentinel. For more information, see [Azure Monitor integration](https://learn.microsoft.com/en-us/entra/external-id/customers/how-to-azure-monitor).
- Use built-in dashboards for user activity, authentication, and engagement insights. For more information, see [User insights](https://learn.microsoft.com/en-us/entra/external-id/customers/how-to-user-insights). User Insights is being retired on August 31, 2026; for new deployments, use Azure Monitor with Log Analytics. See [Migrate from User Insights](https://learn.microsoft.com/en-us/entra/external-id/customers/how-to-user-insights#migrate-from-user-insights).

Ongoing monitoring enables proactive issue resolution, data-driven optimization, and continuous improvement of your CIAM solution.

## Related content

- [Microsoft Entra External ID](https://learn.microsoft.com/en-us/entra/external-id/)
- [Just-in-time password migration](https://learn.microsoft.com/en-us/entra/external-id/customers/how-to-migrate-passwords-just-in-time)
- [Migrate users and credentials](https://learn.microsoft.com/en-us/entra/external-id/customers/how-to-migrate-users)
- [Services and integration partners for External ID](https://learn.microsoft.com/en-us/entra/external-id/customers/services-integration-partners)
- [MSAL overview](https://learn.microsoft.com/en-us/azure/active-directory/develop/msal-overview)
- [Microsoft Entra External ID Q&A](https://learn.microsoft.com/en-us/answers/tags/438/entra-external-id)
- [External authentication and access control](https://learn.microsoft.com/en-us/entra/architecture/deployment-external-authentication-access-control)
- [Service limits](https://learn.microsoft.com/en-us/entra/external-id/customers/reference-service-limits)
