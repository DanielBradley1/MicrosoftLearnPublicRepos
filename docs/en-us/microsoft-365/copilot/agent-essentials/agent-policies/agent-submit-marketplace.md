<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/copilot/agent-essentials/agent-policies/agent-submit-marketplace -->
<!-- Sitemap-Last-Modified: 2026-03-31 -->

# Create a Microsoft Marketplace offer for your AI agents extended with Microsoft Agent 365 in Partner Center

To publish AI agent offers to Microsoft Marketplace, you need a Microsoft AI Cloud Partner Program account in Partner Center and to join the Microsoft 365 and Copilot program. As a member of the Microsoft 365 and Copilot program, you can create offers in [Partner Center](https://learn.microsoft.com/en-us/partner-center/enroll/overview) to publish your AI agents extended using Agent 365 to Microsoft Marketplace. This article provides guidance with links to resources that help you create a Partner Center account, enroll in the Microsoft 365 and Copilot program, and submit your AI agents extended using Agent 365 to Microsoft Marketplace.

## Prerequisites

To enroll in and manage a Microsoft AI Cloud Partner Program account in Partner Center, you need a Microsoft Entra ID tenant and appropriate roles and permissions. To learn more, see:

- [Microsoft Entra ID tenant](https://learn.microsoft.com/en-us/entra/fundamentals/what-is-entra)
- [Enroll in Partner Center programs](https://learn.microsoft.com/en-us/partner-center/enroll/partner-center-enroll-overview)
- [Create user accounts and set permissions](https://learn.microsoft.com/en-us/partner-center/account-settings/create-user-accounts-and-set-permissions)

## Create a Partner Center account

The Microsoft AI Cloud Partner Program is a hub of people, resources, and offerings brought together to help you build and deliver successful solutions to your customers. You need to enroll in the Microsoft AI Cloud Partner Program in Partner Center to get your PartnerID. The PartnerID is a unique identifier that links your AI agents extended using Agent 365 offer to your Microsoft AI Cloud Partner Program account and enables you to manage your offers, track performance, and access support.

If you're new to Partner Center and don't have a Microsoft AI Cloud Partner Program account yet, follow the instructions in [Create a Microsoft AI Cloud Partner Program account in Partner Center](https://learn.microsoft.com/en-us/partner-center/enroll/mpn-create-a-partner-center-account).

For answers to common questions about Partner Center accounts, see [Manage Partner Center Account Q&A - Teams](https://learn.microsoft.com/en-us/microsoftteams/platform/concepts/deploy-and-publish/appsource/prepare/create-partner-center-dev-account).

## Enroll in the Microsoft 365 and Copilot program

The Microsoft 365 and Copilot program provides the resources and support you need to create and publish your AI agent extended using Agent 365 offers to Microsoft Marketplace. If your tenant is already enrolled in Partner Center with a Microsoft AI Cloud Partner Program account, you can [use your current enrollments to join the Microsoft 365 and Copilot program.](https://learn.microsoft.com/en-us/partner-center/marketplace-offers/open-a-developer-account#ensure-you-have-a-partner-center-account-and-are-enrolled-in-the-microsoft-365-and-copilot-program)

When you enroll in a new program in Partner Center or change legal details in your profile, Microsoft verifies the information that you provide. Microsoft verifies three areas: **Email Ownership**, **Employment**, and **Business**.

For more information, see:

- [What is verified and how to respond](https://learn.microsoft.com/en-us/partner-center/verification-responses#what-is-verified-and-how-to-respond)
- [Get Verified Credentials - Partner Center](https://learn.microsoft.com/en-us/partner-center/enroll/get-verifiable-credentials)
- [Manage Partner Center Account Q&A - Teams](https://learn.microsoft.com/en-us/microsoftteams/platform/concepts/deploy-and-publish/appsource/prepare/create-partner-center-dev-account)

## Submit an AI agent extended using Agent 365 to Microsoft Marketplace

Before you submit your AI agent extended using Agent 365 offer to Microsoft Marketplace, review the following resources:

- The checklist in [Prepare to publish](https://learn.microsoft.com/en-us/partner-center/marketplace-offers/checklist) to ensure that your offer is ready for submission.
- The [validation guidelines](https://learn.microsoft.com/en-us/microsoftteams/platform/concepts/deploy-and-publish/appsource/prepare/review-copilot-validation-guidelines) to increase the likelihood of your offer passing the submission process.
- The [Microsoft Marketplace general listing and offer policies](https://learn.microsoft.com/en-us/legal/marketplace/certification-policies#1140-apps-and-agents-for-microsoft-365-and-copilot) to understand the policies your offer must comply with.

When your agent is ready, follow the [Microsoft Marketplace step-by-step submission guide](https://learn.microsoft.com/en-us/partner-center/marketplace-offers/add-in-submission-guide) to submit your agent for validation. Regularly review your submission status in Partner Center and address any feedback or required changes promptly.

Two monetization models are supported:

- **Microsoft‑managed transactable model**: Monetize an AI agent extended using Agent 365 by linking it to a SaaS offer and leveraging the same SaaS offer monetization capabilities. For guidance, see [Monetize a Microsoft 365 agent](https://learn.microsoft.com/en-us/partner-center/marketplace-offers/monetize-addins-through-microsoft-commercial-marketplace).
- **Bring Your Own License \(BYOL\) model**: If your agent uses the Bring Your Own License \(BYOL\) model, don't include licenses. End users must use existing licenses or acquire them separately. To clearly communicate license requirements:

  - Enable Additional purchases during the product setup step.
  - Explicitly state license requirements in:

    - The agent manifest description
    - The Marketplace listing description  
      Example:  
      To use the Contoso Agent with Microsoft Copilot or Microsoft Teams, you must have an active Microsoft Copilot or Microsoft Teams license, along with a valid Contoso license. For more information, see [example link](https://www.example.com).

To learn more, see [Microsoft Marketplace](https://learn.microsoft.com/en-us/partner-center/marketplace-offers/overview).

## Publisher verification

Before submitting your agent, ensure your organization completes publisher verification. Publisher verification confirms to Microsoft that your organization is authentic — when verified, a blue verified badge appears on your app's Microsoft Entra consent prompt and on Microsoft Marketplace listings, giving users and admins greater confidence in your agent.

To complete publisher verification, your organization must have a verified Microsoft AI Cloud Partner Program account, and the app registration in Microsoft Entra ID must be associated with that account. Publisher verification is free, has no license requirement, and typically takes only a few minutes once the prerequisites are in place.

For full details, see [Publisher verification overview](https://learn.microsoft.com/en-us/entra/identity-platform/publisher-verification-overview).
