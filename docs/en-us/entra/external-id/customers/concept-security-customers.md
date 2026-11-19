<!-- Source: https://learn.microsoft.com/en-us/entra/external-id/customers/concept-security-customers -->
<!-- Sitemap-Last-Modified: 2026-06-17 -->

# Security fundamentals for Microsoft Entra External ID external tenants

Customer identity and access management \(CIAM\) systems face threats such as credential stuffing, automated bot sign-ups, account takeover attempts, and high-volume traffic spikes. Microsoft Entra External ID provides security capabilities you can build on to address these threats. Use this guide to prioritize controls and integrations that help protect your customer-facing applications.

**Applies to external tenants:** Feature support varies by authentication approach and API or SDK version. Compare Microsoft-hosted authentication, Embedded native authentication, and Bring Your Own UX \(BYO UX\) in the [authentication approach overview](https://learn.microsoft.com/en-us/entra/external-id/customers/concept-choose-authentication-approach). Check feature availability in the [authentication support matrix](https://learn.microsoft.com/en-us/entra/external-id/customers/concept-supported-features-customers#authentication-approach-supportability).

This article outlines:

- The attack vectors that commonly target CIAM systems.
- The security controls that can help you address them.
- A prioritized roadmap to guide implementation.
- Available third-party integrations for fraud, bot, and distributed denial-of-service \(DDoS\) protection.
- Known limitations specific to external tenants.

## Security model for external tenants

A defense‑in‑depth strategy requires combining multiple control layers:

- Front-door protection through a web application firewall \(WAF\), bot mitigation, and IP controls.
- Identity security through multifactor authentication \(MFA\), Conditional Access, and access control.
- Fraud prevention through third-party sign-up and sign-in detection providers.
- Application-level authorization.
- Monitoring and alerting.

Each layer addresses a different class of attacks, reducing the likelihood of compromise and limiting the blast radius.

Important

Confirm control and method availability for your integration in the [authentication approach comparison](https://learn.microsoft.com/en-us/entra/external-id/customers/concept-supported-features-customers#authentication-approach-supportability). Review the [security considerations in Choose an authentication approach](https://learn.microsoft.com/en-us/entra/external-id/customers/concept-choose-authentication-approach#security-considerations) before implementing your integration.

### Priority 1: Immediate implementation

Start with these protections to establish a security baseline for your external identity flows. Priority 2 adds protections against fraud, bots, DDoS, and more advanced attack patterns.

| **Security feature** | **Description** | **Threats addressed** | **User impact** | **Implementation effort** |
| --- | --- | --- | --- | --- |
| **[Brute force protection](https://learn.microsoft.com/en-us/entra/identity/authentication/howto-password-smart-lockout)** | Mitigates brute force attacks by limiting the number of sign-in attempts to prevent unauthorized access through repeated password guessing.  <br>**Note:** Smart lockout focuses on password misuse; broader bot and fraud activity is addressed through additional controls later in this article. | Prevents brute force, account takeover. | None — No end-user impact | None – Enabled by default |
| **[Common networking HTTP protection](https://learn.microsoft.com/en-us/entra/external-id/customers/reference-service-limits)** | These built‑in protections help filter malformed traffic, limit abusive request patterns, and mitigate common protocol‑level attacks.  <br>**Note:** These safeguards support application stability, but high‑volume DDoS and sophisticated bots require WAF or bot‑mitigation integrations described later. | Protects against common network attacks. | Low – Sensitive actions only | None – Enabled by default |
| **[Access Control](https://learn.microsoft.com/en-us/entra/external-id/customers/how-to-use-app-roles-customers)** | Limits user access by applying app roles and authorization rules.  <br>**Note:** Access control enforces authorization, not user verification. Combine it with MFA and adaptive controls to strengthen security. | Enforces authorization in applications. | Medium– User adoption | Medium – Setup required |
| **[Enable multifactor authentication \(MFA\) for all users](https://learn.microsoft.com/en-us/entra/external-id/customers/concept-multifactor-authentication-customers)** | MFA adds a second verification step beyond passwords, significantly reducing the risk of account takeover.  <br>**Note:** MFA limits stolen‑credential attacks but must be paired with fraud detection and monitoring to prevent automated or malicious sign‑up attempts. | Adds second factor authentication. | High – User adoption | Medium – Setup required |
| **[Passkeys \(FIDO2\)](https://learn.microsoft.com/en-us/entra/external-id/customers/how-to-sign-in-with-passkey)** | Phishing-resistant, passwordless authentication that uses face, fingerprint, PIN, or a security key. A passkey satisfies MFA in a single gesture and can also serve as a primary, passwordless sign-in method. | Prevents phishing, password theft, and credential replay. | Low – Familiar gestures | Medium – Setup and credential management UX required |
| **[Activity logging](https://learn.microsoft.com/en-us/entra/identity/monitoring-health/concept-sign-ups) & [User insights](https://learn.microsoft.com/en-us/entra/external-id/customers/how-to-user-insights)** | Activity logs and insights provide visibility into sign-ups, sign-ins, error patterns, and anomalies. They help you identify unusual trends and investigate issues quickly, supporting early detection, and informed decision making. | Enables threat detection. | None — No end-user impact | Medium – Setup required |

### Priority 2: Short-term implementation

Once baseline controls are in place, implement protections that materially improve threat resilience.

| **Security feature** | **Description** | **Threats addressed** | **User impact** | **Implementation effort** |
| --- | --- | --- | --- | --- |
| **[Conditional Access](https://learn.microsoft.com/en-us/entra/external-id/customers/concept-supported-features-customers#conditional-access)** | Configure policies to require MFA and manage sessions. Check control availability for your authentication integration, including [sign-in frequency \(SIF\)](https://learn.microsoft.com/en-us/entra/identity/conditional-access/concept-session-lifetime#user-sign-in-frequency). See [What is Conditional Access?](https://learn.microsoft.com/en-us/entra/identity/conditional-access/overview) and [Developer guide to Conditional Access authentication context](https://learn.microsoft.com/en-us/entra/identity-platform/developer-guide-conditional-access-authentication-context) for more information. | Provides access control. | Medium – User adoption | Medium – Setup required |
| **[Credential and secret management](https://learn.microsoft.com/en-us/entra/architecture/deployment-external-operations#application-security-credential-and-secret-management)** | Prefer certificates over client secrets for app authentication to External ID because certificates are more secure and harder to compromise. | Secures app credentials. | None — No end-user impact | Medium – Setup required |
| **[Token lifetime management](https://learn.microsoft.com/en-us/entra/architecture/deployment-external-operations#risk-reduction-with-token-lifetime-management)** | Configure the token lifetime to reduce your app’s exposure to compromised tokens. | Limits exposure. | High – Requires frequent refreshes | Medium – Setup required |
| **Custom Domain with Web Application Firewall \(WAF\)** | Use [Cloudflare](https://learn.microsoft.com/en-us/entra/external-id/customers/how-to-configure-waf-integration), [Akamai](https://learn.microsoft.com/en-us/entra/external-id/customers/how-to-configure-akamai-integration) or [Azure WAF](https://learn.microsoft.com/en-us/entra/external-id/customers/tutorial-configure-external-id-web-app-firewall) for tenant security against DDoS attacks. | Provides DDoS and bot protection. | Medium – User adoption | High – WAF integration |
| **Sign-up fraud protection** | Use [Arkose Labs](https://learn.microsoft.com/en-us/entra/external-id/customers/how-to-integrate-fraud-protection?pivots=arkose) and [HUMAN Security](https://learn.microsoft.com/en-us/entra/external-id/customers/how-to-integrate-fraud-protection?pivots=human) to protect against sign-up fraud and block automated bot attacks. | Provides fraud protection. | Medium – User adoption | High – Sign-up protection integration |
| **Enhanced monitoring and alerting** | Use [Azure Monitor and Microsoft Sentinel](https://learn.microsoft.com/en-us/entra/external-id/customers/how-to-azure-monitor) to enable built-in monitoring, log analytics, and advanced threat detection. | Provides early threat detection. | None — No end-user impact | High – Azure Monitor integration |

### Priority 3: Long-term implementation

These are iterative, ongoing improvements to strengthen posture over time.

| **Security feature** | **Description** | **Threats addressed** | **User impact** | **Implementation effort** |
| --- | --- | --- | --- | --- |
| **[Monitoring and alerting](https://learn.microsoft.com/en-us/entra/external-id/customers/how-to-azure-monitor)** | Fine-tune monitoring and alert thresholds to improve accuracy. | Provides accurate monitoring. | None — No end-user impact | Medium – Setup required |
| **Continuous security enhancements and new features** | Use the 3–12 month period to iterate on your security controls and adopt [new enhancements](https://learn.microsoft.com/en-us/entra/external-id/whats-new-docs?tabs=external-tenants). | Helps prevent security threats and vulnerabilities. | Depends on the new feature. | Depends on the new feature. |
| **[Zero Trust Assessment](https://learn.microsoft.com/en-us/security/zero-trust/assessment/overview)** | Tests hundreds of security settings based on Secure Future Initiative \(SFI\) and Zero Trust principles. | Provides thorough security configuration testing. | None — No end-user impact | Medium – Setup required |

## Known limitations

These security features have limitations or are unavailable in external tenants. The following table lists these limitations and suggests possible workarounds.

| **Feature** | **Current limitation** | **Workaround** |
| --- | --- | --- |
| **[ID Protection](https://learn.microsoft.com/en-us/entra/id-protection/overview-identity-protection)** | ID Protection isn’t supported in external tenants. | Not available in external tenants. |

## Related content

- [Supported features in workforce and external tenants](https://learn.microsoft.com/en-us/entra/external-id/customers/concept-supported-features-customers)
