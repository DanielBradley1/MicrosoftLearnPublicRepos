<!-- Source: https://learn.microsoft.com/en-us/entra/identity/authentication/feature-availability -->
<!-- Sitemap-Last-Modified: 2026-01-15 -->

# Microsoft Entra feature availability

This following tables list Microsoft Entra feature availability in Azure for US Government.

## Microsoft Entra ID

| Service | Feature | Availability |
| :--- | --- | :---: |
| **Authentication, single sign-on, and MFA** | Cloud authentication \(Pass-through authentication, password hash synchronization\) | ✅ |
|  | Federated authentication \(Active Directory Federation Services or federation with other identity providers\) | ✅ |
|  | Single sign-on \(SSO\) unlimited | ✅ |
|  | Multifactor authentication \(MFA\) | ✅ |
|  | Passwordless \(Windows Hello for Business, Microsoft Authenticator, FIDO2 security key integrations\) | ✅ |
|  | Certificate-based authentication | ✅ |
|  | Service-level agreement | ✅ |
| **Applications access** | SaaS apps with modern authentication \(Microsoft Entra application gallery apps, SAML, and OAUTH 2.0\) | ✅ |
|  | Group assignment to applications | ✅ |
|  | Cloud app discovery \(Microsoft Defender for Cloud Apps\) | ✅ |
|  | Application Proxy for on-premises, header-based, and Integrated Windows Authentication | ✅ |
|  | Secure hybrid access partnerships \(Kerberos, NTLM, LDAP, RDP, and SSH authentication\) | ✅ |
| **Authorization and Conditional Access** | Role-based access control \(RBAC\) | ✅ |
|  | Conditional Access | ✅ |
|  | SharePoint limited access | ✅ |
|  | Session lifetime management | ✅ |
|  | ID Protection \(vulnerabilities, risky accounts, risk event investigation, SIEM connectivity\) | See [Microsoft Entra ID Protection](#microsoft-entra-id-protection). |
| **Administration and hybrid identity** | User and group management | ✅ |
|  | Group Source of Authority \(SOA\) | ✅ |
|  | Advanced group management \(Dynamic groups, naming policies, expiration, default classification\) | ✅ |
|  | Directory synchronization—Microsoft Entra Connect \(sync and cloud sync\) | ✅ |
|  | Microsoft Entra Connect Health reporting | ✅ |
|  | Delegated administration—built-in roles | ✅ |
|  | Global password protection and management – cloud-only users | ✅ |
|  | Global password protection and management – custom banned passwords, users synchronized from on-premises Active Directory | ✅ |
|  | Microsoft Identity Manager user client access license \(CAL\) | ✅ |
| **End-user self-service** | Application launch portal \(My Apps\) | ✅ |
|  | User application collections in My Apps | ✅ |
|  | Self-service account management portal \(My Account\) | ✅ |
|  | Self-service password change for cloud users | ✅ |
|  | Self-service password reset/change/unlock with on-premises write-back | ✅ |
|  | Self-service sign-in activity search and reporting | ✅ |
|  | Self-service group management \(My Groups\) | ✅ |
|  | Self-service entitlement management \(My Access\) | ✅ |
| **Identity governance** | Automated user provisioning to apps | ✅ |
|  | Automated group provisioning to apps | ✅ |
|  | HR-driven provisioning | Partial. See [HR-provisioning apps](#hr-provisioning-apps). |
|  | Terms of use | ✅ |
|  | Access reviews | ✅ |
|  | Entitlement management | ✅ |
|  | Privileged Identity Management \(PIM\) | ✅ |
|  | Lifecycle workflows, in Microsoft Entra ID Governance | ✅ |
| **Event logging and reporting** | Basic security and usage reports | ✅ |
|  | Advanced security and usage reports | ✅ |
|  | ID Protection: vulnerabilities and risky accounts | ✅ |
|  | ID Protection: risk events investigation, SIEM connectivity | ✅ |
| **Frontline workers** | SMS sign-in | ✅ |
|  | Shared device sign-out | Enterprise state roaming for Windows 10 devices isn't available. |
|  | Delegated user management portal \(My Staff\) | ❌ |

## Microsoft Entra ID Protection

| Risk Detection | Availability |
| --- | :---: |
| Leaked credentials \(Microsoft Account Compromise Exchange\) | ✅ |
| Microsoft Entra threat intelligence | ❌ |
| Anonymous IP address | ✅ |
| Atypical travel | ✅ |
| Anomalous Token | ✅ |
| Token Issuer Anomaly | ✅ |
| Malware linked IP address | ✅ |
| Suspicious browser | ✅ |
| Unfamiliar sign-in properties | ✅ |
| Admin confirmed user compromised | ✅ |
| Malicious IP address | ✅ |
| Suspicious inbox manipulation rules | ✅ |
| Password spray | ✅ |
| Impossible travel | ✅ |
| New country | ✅ |
| Activity from anonymous IP address | ✅ |
| Suspicious inbox forwarding | ✅ |
| Additional risk detected | ✅ |

## HR provisioning apps

| HR-provisioning app | Availability |
| --- | :---: |
| Workday to Microsoft Entra user provisioning | ✅ |
| Workday Writeback | ✅ |
| SuccessFactors to Microsoft Entra user provisioning | ✅ |
| SuccessFactors to Writeback | ✅ |
| API-driven inbound provisioning | ✅ |
| Provisioning agent configuration and registration with Azure for US Government tenant | ✅ |

## Other Microsoft Entra products

[Microsoft Entra ID Governance](https://learn.microsoft.com/en-us/entra/id-governance/licensing-fundamentals) is available in the US Government community cloud \(GCC\), GCC-High, and Department of Defense cloud environments. [Microsoft Entra Workload Identities Premium edition](https://learn.microsoft.com/en-us/entra/workload-id/workload-identities-faqs#is-the-workload-id-premium-plan-available-on-azure-government-clouds) is available in Azure for US government.
