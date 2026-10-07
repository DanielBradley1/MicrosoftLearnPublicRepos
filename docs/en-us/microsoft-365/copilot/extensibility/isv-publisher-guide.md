<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/isv-publisher-guide -->
<!-- Sitemap-Last-Modified: 2026-09-30 -->

# Build and publish Microsoft 365 Copilot plugins for customers

Define the customer scenario, choose supported capabilities and development tools, validate the exact publishing artifact, submit it through an approved route, support customer deployment, and maintain the published solution throughout its lifecycle.

Public distribution eligibility depends on the solution type, package model, capabilities, authoring tool, target Microsoft experiences, and current marketplace support. A capability that you can package isn't automatically eligible for public distribution.

A plugin package can contain definitions, metadata, and references to remote capabilities. A remote MCP server, API, connector service, or other hosted runtime isn't physically contained in the package. Each Microsoft experience activates only the capabilities it supports, and authentication, connections, licensing, administration, and runtime behavior can differ by experience.

Track the plugin, plugin package, any Microsoft 365 app package, Marketplace offer, catalog listing, included agent, skill, connector, or MCP-server component, and external runtime service as distinct objects. Follow the current product-specific procedure for each object and distribution route.

## Follow the plugin lifecycle

| Stage | What you need to do | Start with |
| --- | --- | --- |
| Prepare to build your plugin | Define the target customers, business outcome, supported Microsoft experiences, components, publisher identity, commercial model, support model, data handling, licensing, and distribution scope. | [Plan your plugin](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/planning-guide) |
| Build or reuse capabilities | Create or reuse the required components by using supported development tools, and confirm that each works with its required development or test dependencies. | [Build or reuse capabilities for your plugin](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/build-reuse-plugin) |
| Package and test | Integrate the components, prepare the exact versioned publishing artifact, and validate manifests, metadata, identity, permissions, authentication, dependencies, customer setup, claimed Microsoft experiences, and agent quality when required. | [Integrate capabilities](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/integrate-test-plugin-components) |
| Publish and distribute | Submit the tested object through the supported Partner Center, Marketplace, Store Operations, registry, organizational, or other documented route. Complete the applicable certification process, and record the offer, package, listing, or catalog identifiers. | [Publish publicly through Microsoft Marketplace](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/publish-plugin-publicly) |
| Make available and govern | Give customer administrators the information they need to acquire, approve, assign, enable, connect, and govern the solution. | [Make plugins and agents available and govern access](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/govern-plugins) |
| Monitor, update, and retire | Maintain support, review available signals and customer feedback, evaluate behavior when appropriate, validate and publish updates, communicate breaking changes, transfer ownership where supported, manage deprecation, and retire the solution and its dependencies safely. | [Monitor, update, and retire](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/improve-plugin) |

## Choose the customer distribution model

Choose the route that matches the object, audience, and supported destination. These routes don't use one shared intake or certification process.

| Your goal | Start with |
| --- | --- |
| Publish an eligible plugin publicly | Follow [Publish publicly through Microsoft Marketplace](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/publish-plugin-publicly) and the applicable Partner Center, Marketplace, certification, and Store Operations procedures. |
| Publish an agent or Microsoft 365 app | Start with [Build Copilot-powered apps and agents](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/apps-agents-overview), then follow the product-specific packaging, submission, certification, and distribution procedure. |
| Publish a connector | Start with the [Microsoft 365 Copilot connectors overview](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/overview-copilot-connector), then follow the publishing or deployment procedure for the connector model and target Microsoft experience. |
| Publish an organizational or line-of-business solution | Follow [Publish your plugin or agent to your organization](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/publish-plugin-organization) or the documented organizational route for the object and authoring tool. |
| Combine a public package with an externally hosted application or service | Follow the lifecycle requirements for both parts, and document which identity, deployment, support, and governance requirements apply to each part. |

Partner Center package submission steps don't automatically apply to an API-powered application or service distributed through another channel.

## Plan the public offer

Before implementation:

- Identify the customer problem, target industries, users, and supported Microsoft experiences.
- Determine whether the solution uses a supported plugin package, an agent package, APIs and SDKs, or a combination.
- Confirm whether every capability in the package is eligible for the intended public route.
- Record the plugin, exact plugin package, any Microsoft 365 app package, Marketplace offer, catalog listing, included components, and external runtime services separately.
- Plan multitenant identity, authentication, consent, permissions, external services, and customer configuration.
- Define privacy, terms of use, support, servicing, versioning, and deprecation commitments.
- Review licensing, infrastructure, marketplace, certification, and operational costs.

## Plan customer onboarding

For public multitenant solutions, document the customer setup path before submission:

- Product and package name.
- Publisher identity.
- Exact version.
- Offer, listing, package, or catalog identifier.
- Supported Microsoft experiences.
- Included capabilities.
- Required licenses.
- Permissions and admin or user consent.
- Connections and external services.
- Setup and deployment requirements, including the Microsoft Entra tenant model, application registrations, regions, environments, external accounts, and customer-owned configuration.
- Data, privacy, security, and compliance information.
- Known limitations.
- Support contact.
- Update and deprecation policy.
- Steps for customers to verify setup, diagnose failures, and safely reverse or remove the deployment.

Use the route-specific Partner Center, product, and administration documentation as the source of truth for current procedures.

Publication doesn't make the solution immediately available to every customer or user. Customer administrators can still need to acquire or approve the item and assign, enable, deploy, or connect it as documented for the selected route.

## Prepare and submit the solution

1. Build the solution by using the supported authoring experience.
2. For a plugin, [create the plugin package](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/package-plugin). For an agent or app, use its applicable product-specific packaging guidance.
3. For a plugin, [test and validate the exact plugin package](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/validate-plugin). Apply the product-specific validation requirements for any other package type.
4. Prepare the listing, icons, privacy statement, terms of use, support information, and publisher details.
5. Review the applicable marketplace certification and Microsoft 365 store validation policies.
6. The publisher submits the eligible package or offer through the documented route, such as the **Microsoft 365 and Copilot** program in Microsoft Partner Center.
7. The applicable certification process validates the package, metadata, policies, and technical requirements. The publisher addresses Store Operations feedback and product-specific compatibility requirements.
8. The publishing service places the approved item into the supported catalog or distribution channel.
9. The customer administrator acquires or approves the item when required and assigns, enables, or deploys it to users as documented.
10. Users connect required accounts or services and use the solution in supported Microsoft experiences.
11. The publisher records the offer, package, listing, or catalog identifiers and plans updates, support, and lifecycle operations.

For the current public, organizational, and supported direct-sharing routes, see [Choose how to publish and distribute your plugin](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/publish).

## Plan servicing, support, and retirement

Before release:

- Maintain product support, security response, required service endpoints, external services, and customer communication.
- Monitor the operational and customer signals available for each component and Microsoft experience.
- Test each update against the supported Microsoft experiences.
- Resubmit or republish the updated object through the applicable route.
- Communicate material changes, and maintain compatibility or document breaking changes.
- Define rollback, incident response, escalation, and customer migration procedures.
- Deprecate and retire the solution according to the published support policy, including its dependencies and the treatment of customer data, credentials, and access.

Keep the support and servicing plan aligned with the commitments in the marketplace listing, privacy statement, terms of use, and product-specific publishing route.

## Review public-distribution requirements

- [Microsoft Commercial Marketplace certification policies](https://learn.microsoft.com/en-us/legal/marketplace/certification-policies)
- [Microsoft 365 store validation guidelines for agents](https://learn.microsoft.com/en-us/microsoftteams/platform/concepts/deploy-and-publish/appsource/prepare/review-copilot-validation-guidelines?context=/microsoft-365/copilot/extensibility/context)
- [Responsible AI validation](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/rai-validation)
- [Microsoft 365 App Compliance Program certification \(optional\)](https://learn.microsoft.com/en-us/microsoft-365-app-certification/docs/certification)
- [Microsoft Partner Center](https://partner.microsoft.com)

Submitting a package through one supported route doesn't replace marketplace certification, Store Operations review, administrator approval, or compatibility requirements for the target experience.

## Related content

- [Plugins for Microsoft 365 Copilot](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/plugins-overview)
- [Build Copilot-powered apps and agents](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/apps-agents-overview)
- [Plan your plugin](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/planning-guide)
- [Choose capabilities for your plugin](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/choose-plugin-components)
- [Choose development tools for your plugin](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/choose-plugin-development-tools)
- [Build or reuse capabilities for your plugin](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/build-reuse-plugin)
- [Make plugins and agents available and govern access](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/govern-plugins)
