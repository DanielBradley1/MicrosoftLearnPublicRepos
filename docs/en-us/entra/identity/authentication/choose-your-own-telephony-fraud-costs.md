<!-- Source: https://learn.microsoft.com/en-us/entra/identity/authentication/choose-your-own-telephony-fraud-costs -->
<!-- Sitemap-Last-Modified: 2026-10-30 -->

# Protect against telephony fraud with your own telecom provider

With Choose Your Own Telephony Provider \(CYOT\), SMS and voice traffic runs through your own telecom provider account. You control the fraud protections, allowed destinations, and spending limits that match your organization's traffic and risk profile.

Important

Set up your provider's fraud and spending controls before you move production traffic to CYOT.

## Shared responsibility

| Owner | Responsibility |
| --- | --- |
| Microsoft | Protects code generation and validation in Microsoft Entra ID, and the handoff to your endpoint. |
| Your organization | Manages the provider account, secures the integration, and configures fraud controls. |
| Telecom provider | Delivers SMS and voice, and offers fraud, destination, and spending controls. |

## Configure fraud protections with your provider

Work with your provider to turn on the controls available for your account:

- **Fraud protection:** Turn on the provider's detection for suspicious SMS and voice traffic.
- **Destination restrictions:** Allow only the countries and regions where your users are.
- **Channel restrictions:** Turn on only the channels you use.
- **Spending controls:** Set usage limits and budget alerts.
- **Notifications:** Turn on alerts for unusual activity.

Note

Controls and defaults vary by provider. Ask your provider which protections are on by default and which you need to configure.

## Keep your integration secure

The setup script configures authentication and request validation for your Azure Function. Keep these settings in place, including when you customize the Function.

Your organization is responsible for renewing and rotating the integration's application credentials and certificates.

## Monitor for unusual activity

Review SMS and voice volume in your provider's usage reports. A sudden increase in volume, or traffic to destinations you don't expect, can signal fraud.

## Respond to suspected fraud

1. Contact your telecom provider to review the affected traffic.
2. Restrict the affected destinations, channels, or usage with your provider's controls.
3. Investigate the requests using the Microsoft Entra audit logs, the Function App logs, and your provider's records.
4. Update your protections before you restore traffic.

## Get support

| Issue | Contact |
| --- | --- |
| Fraud, provider account restrictions, delivery, or charges | Your telecom provider. Find contact details in the provider's [Microsoft Security Store](https://securitystore.microsoft.com/) listing. |
| Microsoft Entra authentication, code validation, or the handoff to your endpoint | Microsoft Support. See [Find help and get support for Microsoft Entra](https://learn.microsoft.com/en-us/entra/fundamentals/how-to-get-support). |

## Related content

- [Set up SMS and voice with your own telecom provider in the Microsoft Entra admin center](https://learn.microsoft.com/en-us/entra/identity/authentication/choose-your-own-telephony-set-up).
- [Monitor and troubleshoot SMS and voice with your own telecom provider](https://learn.microsoft.com/en-us/entra/identity/authentication/choose-your-own-telephony-troubleshoot#monitor-and-troubleshoot-your-own-telephony-provider).
- [Plan for resiliency and high availability](https://learn.microsoft.com/en-us/entra/identity/authentication/choose-your-own-telephony-reliability).
- [Estimate telecom provider and Azure hosting costs](https://learn.microsoft.com/en-us/entra/identity/authentication/phone-providers-faq#how-much-does-choose-your-own-telephony-provider-cost).
- [Security Store](https://learn.microsoft.com/en-us/security/store/what-is-security-store).
