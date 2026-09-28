<!-- Source: https://learn.microsoft.com/en-us/entra/architecture/resilience-in-credentials -->
<!-- Sitemap-Last-Modified: 2026-04-03 -->

# Build resilience with credential management

When a credential is presented to Microsoft Entra ID in a token request, there can be multiple dependencies that must be available for validation. The first authentication factor relies on Microsoft Entra authentication and, in some cases, on external \(non-Entra ID\) dependency, such as on-premises infrastructure. For more information on hybrid authentication architectures, see [Build resilience in your hybrid infrastructure](https://learn.microsoft.com/en-us/entra/architecture/resilience-in-hybrid).

The most secure and resilient credential strategy is to use passwordless authentication. [Windows Hello for Business](https://learn.microsoft.com/en-us/entra/identity/authentication/concept-authentication-passkeys-fido2) and [Passkey \(FIDO 2.0\)](https://learn.microsoft.com/en-us/entra/identity/authentication/concept-authentication-passkeys-fido2) security keys have fewer dependencies than other MFA methods. For macOS users customers can enable [Platform Credential for macOS](https://learn.microsoft.com/en-us/entra/identity/authentication/concept-authentication-passkeys-fido2). When you implement these methods users are able to perform strong passwordless and **phishing-resistant** Multi-Factor authentication \(MFA\).

![Image of preferred authentication methods and dependencies](https://learn.microsoft.com/en-us/entra/architecture/media/resilience-in-credentials/passwordless-pr.png)

Tip

For a video series deep dive on deploying these authentication methods, see [Phishing-resistant authentication in Microsoft Entra ID](https://learn.microsoft.com/en-us/entra/identity/authentication/phishing-resistant-authentication-videos)

If you implement a second factor, the dependencies for the second factor are added to the dependencies for the first. For example, if your first factor is via [Pass Through Authentication \(PTA\)](https://learn.microsoft.com/en-us/entra/identity/hybrid/connect/how-to-connect-pta) and your second factor is [SMS](https://learn.microsoft.com/en-us/entra/identity/authentication/howto-authentication-sms-signin), your dependencies are as follows.

- Microsoft Entra authentication services
- Microsoft Entra multifactor authentication service
- On-premises infrastructure
- Phone carrier
- The user's device \(not pictured\)

![Image of remaining authentication methods and dependencies.](https://learn.microsoft.com/en-us/entra/architecture/media/resilience-in-credentials/updated-admin-resilience-credentials.png)

Your credential strategy should consider the dependencies of each authentication type and provision methods that avoid a single point of failure.

Because authentication methods have different dependencies, it's a good idea to enable users to register for as many second factor options as possible. Be sure to include second factors with different dependencies, if possible. For example, Voice call and SMS as second factors share the same dependencies, so having them as the only options doesn't mitigate risk.

For second factors, the Microsoft Authenticator app or other authenticator apps using time-based one time passcode \(TOTP\) or OAuth hardware tokens have the fewest dependencies and are, therefore, more resilient.

## Additional Detail on External \(Non-Entra\) Dependencies

| Authentication Method | External \(Non-Entra\) Dependency | More Information |
| --- | --- | --- |
| Certificate Based Authentication \(CBA\) | In most cases \(depending on configuration\) CBA will require a revocation check. This adds an external dependency on the CRL distribution point \(CDP\) | [Understanding the certificate revocation process](https://learn.microsoft.com/en-us/entra/identity/authentication/concept-certificate-based-authentication-certificate-revocation-list#enforce-crl-validation-for-cas) |
| Pass Through Authentication \(PTA\) | PTA uses on-premise agents to process the password authentication. | [How does Microsoft Entra pass-through authentication work?](https://learn.microsoft.com/en-us/entra/identity/hybrid/connect/how-to-connect-pta-how-it-works#how-does-microsoft-entra-pass-through-authentication-work) |
| Federation | Federation server\(s\) must be online and available to process the authentication attempt | [High availability cross-geographic AD FS deployment in Azure with Azure Traffic Manager](https://learn.microsoft.com/en-us/windows-server/identity/ad-fs/deployment/active-directory-adfs-in-azure-with-azure-traffic-manager) |
| External Multifactor Authentication \(External MFA\) | External MFA provides a path for customers to use external MFA providers. | [Manage external MFA in Microsoft Entra ID](https://learn.microsoft.com/en-us/entra/identity/authentication/how-to-authentication-external-method-manage) |

## How do multiple credentials help resilience?

Provisioning multiple credential types gives users options that accommodate their preferences and environmental constraints. As a result, interactive authentication where users are prompted for multifactor authentication will be more resilient to specific dependencies being unavailable at the time of the request. You can [optimize reauthentication prompts for multifactor authentication](https://learn.microsoft.com/en-us/entra/identity/authentication/concepts-azure-multi-factor-authentication-prompts-session-lifetime).

In addition to individual user resiliency described above, enterprises should plan contingencies for large-scale disruptions such as operational errors that introduce a misconfiguration, a natural disaster, or an enterprise-wide resource outage to an on-premises federation service \(especially when used for multifactor authentication\).

## How do I implement resilient credentials?

- Deploy [Passwordless credentials](https://learn.microsoft.com/en-us/entra/identity/authentication/howto-authentication-passwordless-deployment). Prefer phishing-resistant methods such as Windows Hello for Business, Passkeys \(both Authenticator Passkey Sign-in and FIDO2 security keys\) and certificate based authentication \(CBA\) to increase security while reducing dependencies.
- Deploy the [Microsoft Authenticator App](https://support.microsoft.com/account-billing/how-to-use-the-microsoft-authenticator-app-9783c865-0308-42fb-a519-8cf666fe0acc) as a second factor.
- [Migrate from federation to cloud authentication](https://learn.microsoft.com/en-us/entra/identity/hybrid/connect/migrate-from-federation-to-cloud-authentication) to remove reliance on federated identity provider.
- Turn on [password hash synchronization](https://learn.microsoft.com/en-us/entra/identity/hybrid/connect/whatis-phs) for hybrid accounts that are synchronized from Windows Server Active Directory. This option can be enabled alongside federation services such as Active Directory Federation Services \(AD FS\) and provides a fallback in case the federation service fails.
- [Analyze usage of multifactor authentication methods](https://learn.microsoft.com/en-us/entra/identity/authentication/howto-authentication-methods-activity) to improve user experience.
- [Implement a resilient access control strategy](https://learn.microsoft.com/en-us/entra/identity/authentication/concept-resilient-controls)

## Next steps

### Resilience resources for administrators and architects

- [Build resilience with device states](https://learn.microsoft.com/en-us/entra/architecture/resilience-with-device-states)
- [Build resilience by using Continuous Access Evaluation \(CAE\)](https://learn.microsoft.com/en-us/entra/architecture/resilience-with-continuous-access-evaluation)
- [Build resilience in external user authentication](https://learn.microsoft.com/en-us/entra/architecture/resilience-b2b-authentication)
- [Build resilience in your hybrid authentication](https://learn.microsoft.com/en-us/entra/architecture/resilience-in-hybrid)
- [Build resilience in application access with Application Proxy](https://learn.microsoft.com/en-us/entra/architecture/resilience-on-premises-access)

### Resilience resources for developers

- [Build IAM resilience in your applications](https://learn.microsoft.com/en-us/entra/architecture/resilience-app-development-overview)
- [Build resilience in your CIAM systems](https://learn.microsoft.com/en-us/entra/architecture/resilience-b2c)
