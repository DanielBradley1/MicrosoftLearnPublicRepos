<!-- Source: https://learn.microsoft.com/en-us/entra/id-protection/concept-identity-protection-user-experience -->
<!-- Sitemap-Last-Modified: 2026-03-25 -->

# Self-remediation experience with Microsoft Entra ID Protection and Conditional Access

With Microsoft Entra ID Protection and Conditional Access, you can:

- Require users to register for Microsoft Entra multifactor authentication
- Automate remediation of risky sign-ins and compromised users
- Block users in specific cases.

Conditional Access policies that integrate user and sign-in risk affect the sign in experience for users. Allowing users to use tools like Microsoft Entra multifactor authentication + secure password change or self service password reset \(SSPR\) can lessen the impact. These tools, along with the appropriate policy choices, give users a self-remediation option when they need it while still enforcing strong security controls.

## Multifactor authentication registration

When an administrator enables the ID Protection policy requiring Microsoft Entra multifactor authentication registration, users can use Microsoft Entra multifactor authentication to self-remediate. Configuring this policy gives users a 14-day period to register, after which they're forced to register.

### Registration interrupt

1. At sign-in to any Microsoft Entra integrated application, the user gets a notification about the requirement to set up the account for multifactor authentication. This policy is also triggered in the Windows Out of Box Experience for new users with a new device.

   ![A screenshot showing the more information required prompt in a browser window.](https://learn.microsoft.com/en-us/entra/id-protection/media/concept-identity-protection-user-experience/identity-protection-experience-more-info-mfa.png)

2. Complete the guided steps to register for Microsoft Entra multifactor authentication and sign in.

## Risk self-remediation

When an administrator configures risk-based Conditional Access policies, affected users are interrupted when they reach the configured risk level. If administrators allow self-remediation using multifactor authentication, this process appears to a user as a normal multifactor authentication prompt.

If the user completes multifactor authentication, their risk is remediated and they can sign in.

[![A screenshot showing a multifactor authentication prompt at sign in.](https://learn.microsoft.com/en-us/entra/id-protection/media/concept-identity-protection-user-experience/conditional-access-mfa-prompt.png)](https://learn.microsoft.com/en-us/entra/id-protection/media/concept-identity-protection-user-experience/conditional-access-mfa-prompt.png#lightbox)

If the user is at risk, not just the sign-in, administrators can configure a user risk policy in Conditional Access to require a password change in addition to multifactor authentication. In that case, the user sees the following extra screen.

[![A screenshot showing the password change is required prompt when user risk is detected.](https://learn.microsoft.com/en-us/entra/id-protection/media/concept-identity-protection-user-experience/conditional-access-password-change-prompt.png)](https://learn.microsoft.com/en-us/entra/id-protection/media/concept-identity-protection-user-experience/conditional-access-password-change-prompt.png#lightbox)

### Adaptive risk remediation

The adaptive risk remediation policy accommodates all authentication methods, including password-based and passwordless. The grant controls for this policy automatically include **Require authentication strength** and **Sign-in frequency - Every time** to ensure that users are prompted to reauthenticate after their sessions are revoked. For more information, see \[concept-identity-protection-policies#require-risk-remediation-control-preview\].

When a user is required to remediate risk with this policy turned on, users must sign in immediately after their sessions are revoked. If the user just signed in but they're at risk, they'll be prompted to sign in again. The risk is remediated after the user successfully signed in the second time.

### Risky sign-in administrator unblock

Administrators might block users upon sign-in depending on their risk level. To get unblocked, users must contact their IT staff or try signing in from a familiar location or device. Self-remediation isn't an option in this case.

[![A screenshot showing your account is blocked screen.](https://learn.microsoft.com/en-us/entra/id-protection/media/concept-identity-protection-user-experience/conditional-access-blocked.png)](https://learn.microsoft.com/en-us/entra/id-protection/media/concept-identity-protection-user-experience/conditional-access-blocked.png#lightbox)

IT staff can follow the instructions in [Unblocking users](https://learn.microsoft.com/en-us/entra/id-protection/howto-identity-protection-remediate-unblock#unblock-users) to allow users to sign back in.

## High risk technician

If the home tenant didn't enable self-remediation policies, an administrator in the technician's home tenant must remediate the risk. For example:

1. An organization has a managed service provider \(MSP\) or cloud solution provider \(CSP\) who takes care of configuring their cloud environment.
2. One of the MSPs technicians credentials are leaked and triggers high risk. That technician is blocked from signing in to other tenants.
3. The technician can self-remediate and sign in if the home tenant enabled the appropriate policies [requiring password change for high risk users](https://learn.microsoft.com/en-us/entra/identity/conditional-access/policy-risk-based-user) or [MFA for risky users](https://learn.microsoft.com/en-us/entra/identity/conditional-access/policy-risk-based-sign-in).

   - If the home tenant didn't enable self-remediation policies, an administrator in the technician's home tenant has to [remediate the risk](https://learn.microsoft.com/en-us/entra/id-protection/howto-identity-protection-remediate-unblock).

## Related content

- [Remediate risks and unblock users](https://learn.microsoft.com/en-us/entra/id-protection/howto-identity-protection-remediate-unblock)
- [Microsoft Entra ID Protection](https://learn.microsoft.com/en-us/entra/id-protection/overview-identity-protection)
