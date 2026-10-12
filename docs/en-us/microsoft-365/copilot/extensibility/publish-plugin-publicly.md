<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/publish-plugin-publicly -->
<!-- Sitemap-Last-Modified: 2026-09-30 -->

# Publish your plugin through Microsoft Marketplace

Publish an eligible plugin package through Microsoft Marketplace so customers in other organizations can discover it. Submit the package through the supported Microsoft Partner Center offer type, complete the required review, and make the approved offer available.

Not every plugin package is eligible for Marketplace publication. Confirm support for your package type, included capabilities, authoring tool, and intended Microsoft 365 experiences before preparing a submission.

Marketplace publication is a public distribution method. It is distinct from sharing a plugin with specific users or an organization through a tool-specific sharing workflow. Neither method automatically completes the customer's installation, access, consent, or connection requirements.

## Before you begin

Ensure you have:

- The exact plugin package and version that passed [validation and testing](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/validate-plugin).
- Confirmation that a supported Marketplace offer type accepts your package and included capabilities.
- A publisher account enrolled in the [Microsoft 365 and Copilot program](https://learn.microsoft.com/en-us/partner-center/marketplace-offers/open-a-developer-account).
- Permission to create and submit offers in Microsoft Partner Center.
- Listing details, a privacy statement, terms of use, and support information.
- Customer setup instructions for required licenses, accounts, permissions, consent, connections, and external services.
- An owner responsible for the submission, updates, support, security response, and retirement.

When authentication or customer-specific data access is required, confirm that the setup supports customers in other organizations and keeps each customer's access and data appropriately scoped.

## Check the publishing requirements

Before preparing your listing, confirm that:

- The selected offer type supports your plugin's package type and included capabilities.
- The authoring and packaging method produces the package or manifest required for that offer.
- The plugin works in each Microsoft 365 experience you intend to support.
- The package and its dependencies meet the applicable security, identity, permissions, and customer setup requirements.
- You can maintain the external services and support commitments described in the listing.

Use the requirements for the selected offer type and package as the source of truth. Review the applicable [Marketplace certification policies](https://learn.microsoft.com/en-us/legal/marketplace/certification-policies).

Successful package testing doesn't establish Marketplace eligibility. Support in one Microsoft 365 experience doesn't establish support in another.

Important

If no documented offer type supports your package and included capabilities, resolve eligibility before submitting. Don't substitute a different package type or assume that an agent-only submission procedure accepts a composed plugin package.

## Prepare your listing

Your Marketplace listing tells customers what the plugin does, where it works, and what they need to use it.

Prepare:

- A name, description, icons, screenshots, and any other required listing assets.
- Publisher contact details and a support link.
- A privacy statement and terms of use.
- Required licenses, supported regions, and supported Microsoft 365 experiences.
- Setup instructions for accounts, permissions, consent, connections, and customer configuration.
- Disclosures about external services, data access, additional purchases, and known limitations.
- Your update, support, security-response, and retirement policy.

Keep the listing consistent with the exact package you tested. Describe external services as dependencies; don't imply that their hosting, credentials, or data are contained in the plugin package.

## Submit your plugin

Follow the [add-in submission guide](https://learn.microsoft.com/en-us/partner-center/marketplace-offers/add-in-submission-guide) and the requirements for your selected offer type:

1. Sign in to [Microsoft Partner Center](https://partner.microsoft.com/).
2. Open **Marketplace offers** and select the **Microsoft 365 and Copilot** tab. If the program isn't available, confirm that the publisher account is enrolled.
3. Select **New offer** and choose the offer type that supports your plugin package.
4. Add the required listing and technical information.
5. Upload the package or manifest required by the selected offer type.
6. Provide the certification reviewers with the requested testing instructions and access information through the submission process.
7. Review the submission and submit it for certification.

Record the offer ID, submitted package version, submission date, submission status, and responsible owner.

Note

Supported sharing methods can publish a plugin to the plugin registry without creating a Marketplace offer. Work IQ Dev Tools sharing and organizational publishing commands don't replace Microsoft Partner Center submission for public Marketplace distribution.

## Complete the review

Track the submission in Microsoft Partner Center and address certification findings.

If you change the package, validate and test the updated version before resubmitting it. If reviewers request changes to the listing, customer setup instructions, or support information, update those items and keep them consistent with the package.

Additional requirements or programs can apply:

- [Microsoft 365 store validation guidelines for agents](https://learn.microsoft.com/en-us/microsoftteams/platform/concepts/deploy-and-publish/appsource/prepare/review-copilot-validation-guidelines?context=/microsoft-365/copilot/extensibility/context), when applicable to an included agent and the selected submission method.
- [Microsoft 365 App Compliance Program certification](https://learn.microsoft.com/en-us/microsoft-365-app-certification/docs/certification), if you choose to pursue this optional certification.

After approval, complete any remaining publishing or availability steps required by the offer type.

**Submission isn't publication.** Publication is complete when the approved offer is available in Microsoft Marketplace.

Record the published offer, package version, supported experiences, availability, and support owner.

## Help customers get started

Publishing in the marketplace doesn't automatically install, enable, authorize, or configure the plugin in every customer organization or Microsoft 365 experience.

Provide clear instructions for:

- Finding and acquiring the plugin.
- Completing any required administrator approval, user assignment, or installation.
- Enabling the plugin in supported experiences when required.
- Signing in, granting consent, and connecting required services.
- Verifying that the plugin completes its intended task.
- Getting support and receiving updates.
- Safely removing access or retiring the deployment.

Explain which steps the customer administrator completes and which steps individual users complete. Include only the actions required by the supported publishing method and experience.

Continue to [Make your plugin available and govern access](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/govern-plugins) for the post-publication lifecycle.

## Related content

- [Publish or share your plugin](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/publish)
- [For ISVs and software publishers](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/isv-publisher-guide)
- [Publish your plugin to your organization](https://learn.microsoft.com/en-us/microsoft-365/copilot/extensibility/publish-plugin-organization)
