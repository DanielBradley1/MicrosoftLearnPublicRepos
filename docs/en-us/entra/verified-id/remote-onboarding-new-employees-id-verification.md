<!-- Source: https://learn.microsoft.com/en-us/entra/verified-id/remote-onboarding-new-employees-id-verification -->
<!-- Sitemap-Last-Modified: 2026-03-17 -->

# Remote onboarding with Microsoft Entra Verified ID overview

Remote onboarding with Microsoft Entra Verified ID uses government-issued, ID-based attestations to help establish trust with users who aren't yet inside your organization's trust boundary.

Choose between two onboarding patterns. If your organization uses Lifecycle Workflows in Microsoft Entra ID Governance, use the built-in identity-verification templates and tasks. If you have your own onboarding portal or solution and need to customize the experience, integrate with the Verified ID REST APIs.

## Pattern 1: Built-in identity verification tasks with Lifecycle Workflows

Use this pattern to configure onboarding through the Pre-hire and New-hire identity-verification templates and tasks in Lifecycle Workflows, rather than implement the verification journey in a custom portal.

The pattern connects pre-hire identity verification with new-hire credential registration. An ID verification profile defines the verification journey, and the workflow uses that profile for its identity-verification tasks.

For this pattern, use an identity verification \(IDV\) partner offer with **Security Store-based integration**. The [IDV partner gallery](https://aka.ms/verifiedidisv) lists Security Store integration partners separately from Verified ID API-based integration partners. Review the relevant integration type when selecting a provider.

For configuration and the complete user journey, see [Onboard users with identity verification \(Preview\)](https://learn.microsoft.com/en-us/entra/id-governance/how-to-onboard-users-with-identity-verification). That guide covers:

- Pre-hire and new-hire workflow configuration.
- Inline passkey registration and the alternative that uses a Temporary Access Pass \(TAP\) with Conditional Access-protected registration.
- Device, passkey-policy, and guest-account eligibility considerations.

## Pattern 2: Custom onboarding portal with Verified ID REST APIs

Use this pattern if you have your own onboarding portal or solution and want to customize the experience by using Microsoft Entra Verified ID REST APIs. Your application coordinates identity verification, credential presentation, user matching, and the remaining onboarding logic.

For this pattern, select a provider that supports **Verified ID API-based integration** from the [IDV partner gallery](https://aka.ms/verifiedidisv), and follow that partner's integration guidance. Don't assume that a partner supports both integration types just because it appears in the gallery.

### Custom-portal example

The following employee-onboarding example assumes a human resources \(HR\) system with API support for querying records and matching user profiles. The new hire's account is already provisioned in Microsoft Entra ID, and the organization uses TAP as part of its passwordless onboarding.

A backend job sends the new hire a link to their onboarding process. [Lifecycle Workflows](https://learn.microsoft.com/en-us/entra/id-governance/what-are-lifecycle-workflows) can trigger this invitation, but the custom portal still implements the API-based flow described here.

| Stage | Custom-portal behavior |
| --- | --- |
| **Invitation** | The backend sends an employee-specific link. The new hire opens it, and the onboarding portal validates the link. |
| **Identity verification and issuance** | The portal redirects the new hire to the IDV partner to complete verification and receive a Verified ID in their wallet. |
| **Credential presentation** | The new hire returns to the onboarding portal and presents the Verified ID. The portal uses the Verified ID service to request presentation and receive the credential claims. |
| **Account matching** | The application validates the claims against the HR record and locates the new hire's Microsoft Entra account. |
| **TAP generation** | The application uses Microsoft Graph to [generate a TAP](https://learn.microsoft.com/en-us/graph/api/resources/temporaryaccesspassauthenticationmethod?view=graph-rest-1.0&preserve-view=true), then presents it to the new hire to continue onboarding. |

The sequence diagram shows this custom-portal example, not the built-in Lifecycle Workflows templates.

[![Sequence diagram of custom-portal identity verification, HR matching, and TAP generation in Microsoft Entra ID.](https://learn.microsoft.com/en-us/entra/verified-id/media/remote-onboarding-new-employees-id-verification/high-level-flow-diagram.png)](https://learn.microsoft.com/en-us/entra/verified-id/media/remote-onboarding-new-employees-id-verification/high-level-flow-diagram.png#lightbox)

[The partner redirects the new hire to the onboarding portal. The new hire selects the presentation link, and the portal creates a presentation request with the Verified ID service. Microsoft Authenticator consumes the request, and the new hire consents to present the credential. The service returns the presentation response to the onboarding portal. The portal validates the user record against the credential claims through the HR system, calls Microsoft Graph to generate a TAP in Microsoft Entra ID, and presents the TAP to the new hire so onboarding can continue.](https://learn.microsoft.com/en-us/entra/verified-id/media/remote-onboarding-new-employees-id-verification/high-level-flow-diagram.png#lightbox)

### Custom-portal design considerations

These considerations apply to the custom application and HR matching in Pattern 2.

- **Invitation links:** Make each link specific to one remote employee, valid for only a short period, and invalid after the flow finishes. Correlate it with a unique HR record identifier.
- **Account validation:** Precreate the Microsoft Entra account and use it as part of the portal's request validation.
- **Name differences:** HR records and government-issued documents can contain different names, such as "Jim" and "James." Ask candidates to use the name on their government-issued documents at the beginning of the HR process to simplify validation.
- **Matching attributes:** Design validation around attributes likely to match the HR record exactly. In addition to first and last name, examples include street address, date of birth, nationality, and a national or regional identification number, where applicable.
- **Human review:** Plan a fallback for ambiguous or nonconclusive matches, such as a phone call with the user.
- **Regional coverage:** Multinational organizations might need different identity verification partners for different user regions.
- **Auditing:** Treat the initial user interaction as untrusted. Generate detailed audit logs for requests processed by the onboarding portal. Don't log TAP values, invitation links, or unnecessary credential claims.

## Related content

- [Onboard users with identity verification \(Preview\)](https://learn.microsoft.com/en-us/entra/id-governance/how-to-onboard-users-with-identity-verification)
- [Get started with the Verified ID REST APIs](https://learn.microsoft.com/en-us/entra/verified-id/get-started-request-api)
- [Plan your Microsoft Entra Verified ID verification solution](https://learn.microsoft.com/en-us/entra/verified-id/plan-verification-solution#account-onboarding)
