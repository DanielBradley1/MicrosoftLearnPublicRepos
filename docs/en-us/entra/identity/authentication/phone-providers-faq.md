<!-- Source: https://learn.microsoft.com/en-us/entra/identity/authentication/phone-providers-faq -->
<!-- Sitemap-Last-Modified: 2026-11-11 -->

# Frequently asked questions

These are common questions about Choose Your Own Telephony Provider \(CYOT\) and Bring Your Own Telephony \(BYOT\) in Microsoft Entra ID. For an overview, see [Choose your own telephony provider for SMS and voice authentication](https://learn.microsoft.com/en-us/entra/identity/authentication/concept-telephony-providers). For BYOT setup, see [Set up SMS and voice with your own telephony provider by using APIs \(BYOT\)](https://learn.microsoft.com/en-us/entra/identity/authentication/bring-your-own-telephony-set-up).

This FAQ covers:

- [Provider selection and availability](#provider-selection-and-availability).
- [Supported scenarios](#supported-scenarios).
- [Costs and billing](#costs-and-billing).
- [Evaluation and migration](#evaluation-and-migration).
- [Reliability and recovery](#reliability-and-recovery).
- [Support](#support).

## Provider selection and availability

### Are CYOT and BYOT generally available?

CYOT and BYOT are generally available for Microsoft Entra ID workforce tenants in global Azure.

### Can I purchase a telephony provider offer in my country or region?

For CYOT, check [Microsoft Marketplace geographic availability](https://learn.microsoft.com/en-us/partner-center/marketplace-offers/marketplace-geo-availability-currencies) for purchase availability in your billing country or region. If Marketplace purchasing is unavailable, contact your Microsoft field team to discuss BYOT. For BYOT, confirm account availability and telephony coverage directly with your provider. Marketplace purchase availability is separate from telephony coverage.

### Which telephony providers can I use?

For CYOT, you can choose Soprano, Telesign, or Infobip. For coverage, pricing, and terms, see [Available telephony providers](https://learn.microsoft.com/en-us/entra/identity/authentication/concept-telephony-providers#available-telephony-providers) and each provider's [Microsoft Security Store](https://securitystore.microsoft.com/) listing. For BYOT, obtain your provider's ready-to-deploy integration package and setup instructions. See [Set up SMS and voice with your own telephony provider by using APIs \(BYOT\)](https://learn.microsoft.com/en-us/entra/identity/authentication/bring-your-own-telephony-set-up).

### Can I use my existing account with a provider?

For both CYOT and BYOT, check with your provider. Your provider might also need its own registration, such as sender registration.

### Can I use a provider that isn't on the list?

CYOT supports the providers listed in [Available telephony providers](https://learn.microsoft.com/en-us/entra/identity/authentication/concept-telephony-providers#available-telephony-providers). Check that list for providers as they're added. Use BYOT only when regulatory, compliance, or other specific requirements call for a provider outside these offerings. Your provider must supply a ready-to-deploy integration package and setup instructions. See [Set up SMS and voice with your own telephony provider by using APIs \(BYOT\)](https://learn.microsoft.com/en-us/entra/identity/authentication/bring-your-own-telephony-set-up).

### Can I use different providers for SMS and voice?

Yes. For CYOT and BYOT, you can use one provider for SMS and another for voice, subject to the channels supported by each provider and its integration.

## Supported scenarios

### Which Microsoft Entra products support CYOT and BYOT?

CYOT and BYOT are available for Microsoft Entra ID workforce tenants. Neither is currently available for Microsoft Entra External ID or Azure AD B2C.

### Can I use CYOT or BYOT for SMS sign-in as a primary method?

No. CYOT and BYOT support SMS and voice as verification methods, not as primary sign-in. Move users who sign in with SMS to another supported method.

Important

Microsoft recommends phishing-resistant methods such as [passkeys](https://learn.microsoft.com/en-us/entra/identity/authentication/concept-authentication-passkeys-fido2). Use SMS or voice only for users with a business, regulatory, or technical need for it.

## Costs and billing

### How much do CYOT and BYOT cost?

Plan for two costs:

- **Provider costs:** For CYOT, SMS and voice charges are set by your provider's offer on [Microsoft Security Store](https://securitystore.microsoft.com/). For BYOT, charges follow the commercial terms you agree directly with your provider.
- **Azure costs:** the resources that host the integration in your subscription.

For estimates, see [Estimate telephony provider and Azure hosting costs](https://github.com/Azure-Samples/ExternalPhoneProvider-AzureFunction-Sample/blob/main/docs/COST-CALCULATOR.md).

### Does Microsoft charge me for SMS and voice sent through my provider?

For CYOT, your provider sets SMS and voice charges under the offer you purchase in [Microsoft Security Store](https://securitystore.microsoft.com/). For BYOT, charges follow the terms you agree directly with your provider. For both options, Azure hosting costs are billed to your Azure subscription.

## Evaluation and migration

### How do I move to my own telephony provider?

For CYOT:

1. Subscribe to a provider offer in [Microsoft Security Store](https://securitystore.microsoft.com/).
2. Set up the integration in your Azure subscription.
3. Create an SMS and voice profile.
4. Evaluate the integration.
5. Roll out traffic to your provider.

For details, see [Set up SMS and voice with your own telephony provider in the Microsoft Entra admin center \(CYOT\)](https://learn.microsoft.com/en-us/entra/identity/authentication/choose-your-own-telephony-set-up).

For BYOT, set up your account directly with your provider, deploy its published integration, and configure the authentication method policy through APIs. See [Set up SMS and voice with your own telephony provider by using APIs \(BYOT\)](https://learn.microsoft.com/en-us/entra/identity/authentication/bring-your-own-telephony-set-up). For both options, preserve existing production SMS and voice targets. Test targeting changes in a test tenant.

### Can I test CYOT or BYOT before I move traffic?

Yes. Evaluation mode sends requests to your integration while Microsoft continues to deliver codes to users. For CYOT, set the **Evaluation sampling percentage** in your profile, then switch to **Production** at a low traffic percentage to test provider delivery. For BYOT, set `isEvaluationModeEnabled` to `true` and use `migrationPercentage` for evaluation sampling. To test provider credentials and actual delivery, set `isEvaluationModeEnabled` to `false` with a low `migrationPercentage`. See [Set up SMS and voice with your own telephony provider by using APIs \(BYOT\)](https://learn.microsoft.com/en-us/entra/identity/authentication/bring-your-own-telephony-set-up#step-5-test-the-integration).

### Can I move traffic gradually?

Yes. For CYOT, increase the **Traffic routed through provider percentage** in stages. For BYOT, increase `migrationPercentage` with `isEvaluationModeEnabled` set to `false`. For both options, check results before each increase and preserve existing production targets.

### How long do policy changes take to apply?

Changes to the authentication methods policy can take up to about an hour to apply.

### I lost the setup output when Cloud Shell closed. What do I do?

Copy the deployment summary as soon as the script finishes. Cloud Shell sessions are temporary and can close when you switch tabs. If you lost it, find the deployed resources in the Azure portal.

## Reliability and recovery

### What should I do if SMS or voice codes aren't arriving?

If you're partway through a rollout, pause it. Then use [Monitor and troubleshoot SMS and voice with your own telephony provider](https://learn.microsoft.com/en-us/entra/identity/authentication/choose-your-own-telephony-troubleshoot#monitor-and-troubleshoot-your-own-telephony-provider) to find where the request stopped and who to contact.

### How do I plan for high availability?

You can deploy the integration across multiple Azure regions, review your provider's redundancy, and add a secondary provider. The multi-region and secondary-provider designs are sample-only guidance. Test failover before you rely on it. See [Plan for resiliency and high availability](https://learn.microsoft.com/en-us/entra/identity/authentication/choose-your-own-telephony-reliability).

## Support

### Who manages each part of CYOT and BYOT?

| Owner | Responsibility |
| --- | --- |
| Microsoft | Microsoft Entra authentication and the handoff to your endpoint |
| Your organization | Deploying and running the integration, managing the provider account, and renewing integration credentials and certificates |
| Telephony provider | SMS and voice delivery, and fraud controls |

### Who do I contact for help?

| Issue | Contact |
| --- | --- |
| Microsoft Entra authentication, code validation, or the handoff to your endpoint | [Microsoft Support](https://learn.microsoft.com/en-us/entra/fundamentals/how-to-get-support) |
| Your Azure Function or Azure resources | Your Azure team |
| Delivery, sender registration, destinations, fraud controls, or charges | Your telephony provider. For CYOT, use its [Security Store](https://securitystore.microsoft.com/) listing. For BYOT, use support details supplied directly by your provider. |

## Related content

- [Choose your own telephony provider for SMS and voice authentication](https://learn.microsoft.com/en-us/entra/identity/authentication/concept-telephony-providers).
- [Set up SMS and voice with your own telephony provider in the Microsoft Entra admin center \(CYOT\)](https://learn.microsoft.com/en-us/entra/identity/authentication/choose-your-own-telephony-set-up).
- [Set up SMS and voice with your own telephony provider by using APIs \(BYOT\)](https://learn.microsoft.com/en-us/entra/identity/authentication/bring-your-own-telephony-set-up).
- [Troubleshoot SMS and voice with your own telephony provider](https://learn.microsoft.com/en-us/entra/identity/authentication/choose-your-own-telephony-troubleshoot#monitor-and-troubleshoot-your-own-telephony-provider).
- [Protect against telephony fraud with your own telephony provider](https://learn.microsoft.com/en-us/entra/identity/authentication/choose-your-own-telephony-fraud-protection).
- [Plan for resiliency and high availability](https://learn.microsoft.com/en-us/entra/identity/authentication/choose-your-own-telephony-reliability).
- [Estimate provider and Azure hosting costs](https://github.com/Azure-Samples/ExternalPhoneProvider-AzureFunction-Sample/blob/main/docs/COST-CALCULATOR.md).
- [Passkeys by default and retirement of Microsoft-provided SMS and voice authentication](https://learn.microsoft.com/en-us/entra/identity/authentication/concept-sms-voice-retirement).
- [Frequently asked questions](#how-much-does-choose-your-own-telephony-provider-cost).
- [Community Center \| Not monitored](https://learn.microsoft.com/en-us/answers/topics/azure-active-directory.html).
