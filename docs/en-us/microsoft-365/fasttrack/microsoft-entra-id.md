<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/fasttrack/microsoft-entra-id -->
<!-- Sitemap-Last-Modified: 2026-08-05 -->

# Microsoft Entra

## Zero Trust

FastTrack provides comprehensive guidance on implementing Zero Trust security principles. The Zero Trust model assumes breach and verifies each request as though it originates from an uncontrolled network. This approach ensures robust security across your networks, applications, and environment. FastTrack accomplishes this by focusing on identity, devices, applications, data, infrastructure, and networks. With FastTrack, you can confidently advance your Zero Trust security journey and protect your digital assets effectively.

With Microsoft Entra, you can implement Zero Trust principles by ensuring strong authentication and access policies. This includes enforcing least privileged access with granular permissions and controls, managing access to secure resources, and minimizing the blast radius of potential attacks. By integrating with Microsoft Entra ID, you can create secure Zero Trust solutions that protect your organization's identity and access management.

## Microsoft Entra ID P1

FastTrack provides remote guidance to enable secure access to apps and to protect identities from security threats.

This guidance includes:

- Multifactor authentication \(MFA\) \(cloud only\).
- Self-service password reset \(SSPR\).
- Conditional Access.
- Self-service group management.
- Dynamic group membership.
- Business-to-business \(B2B\) collaboration between Microsoft Entra tenants.
- Setup of a multitenant organization in Microsoft 365 admin center.
- B2B direct connect.
- Cross-tenant synchronization.
- Cross-tenant access.
- Password protection.
- Application Proxy for on-premises web apps.
- Connect Health.
- Company branding.
- Managing collections in My Apps.
- Role-based access control \(RBAC\) for built-in administrative roles.
- Administrative units.
- Built-in monitoring and reporting capabilities.
- Terms of use.

## Microsoft Entra ID P2 \(included in Microsoft 365 E5\)

FastTrack provides remote guidance to enable secure access to apps and to protect identities from security threats.

This guidance includes:

- Identity Protection.
- Risk-based Conditional Access.
- Privileged Identity Management \(PIM\).
- Basic entitlement management.
- Access reviews.

## Microsoft Entra ID Governance

FastTrack provides remote guidance for:

- Deploying Privileged Identity Management \(PIM\) \(also included in Microsoft Entra ID P2\).
- Deploying entitlement management.
- Configuring access reviews.
- Configuring automatic user provisioning to on-premises Active Directory or Microsoft Entra ID for Workday HCM or SAP SuccessFactors through tutorial assistance.
- Configuring attribute writeback from Microsoft Entra ID to Workday HCM or SAP SuccessFactors through tutorial assistance.
- Deploying lifecycle workflow built-in tasks and templates including use of custom security attributes to scope a workflow.

### Out of scope

- Any API-related configuration or customization.
- Any configuration inside of Workday HCM or SAP SuccessFactors portals.
- Configuring advanced attribute mappings.
- Custom expression mapping for provisioning or writeback.
- Data remediation for manual human resource \(HR\) data.
- Lifecycle workflow custom task extensions and APIs.
- Azure Logic Apps customization or integration.

## Microsoft Entra Global Secure Access

### Global Secure Access configuration

FastTrack provides remote guidance for:

- Activating Global Secure Access in the tenant.
- Enabling traffic forwarding profiles for Microsoft Entra Internet Access, Microsoft Entra Private Access, and Microsoft traffic.
- Enabling source IP restoration.
- Installing the Global Secure Access client on Windows 10/11, macOS, iOS, and Android clients.

### Microsoft Entra Internet Access for Microsoft Services \(included in Microsoft Entra ID P1\)

FastTrack provides remote guidance for:

- Enabling Global Secure Access signaling for Conditional Access.
- Enabling universal tenant restrictions including blocking access for all external identities and applications.
- Configuring compliant network access.
- Configuring applicable Conditional Access policies.

### Microsoft Entra Internet Access

FastTrack provides remote guidance for:

- Creating and applying web filtering policies.
- Applying web filtering policies to security profiles.
- Creating Conditional Access policies that apply to Microsoft Entra Internet Access.

### Microsoft Entra Private Access

FastTrack provides remote guidance for:

- Installing and configuring connectors.
- Publishing applications.
- Creating Conditional Access policies that apply to Microsoft Entra Private Access.

### Out of scope

- Network device, virtual local area network \(VLAN\) configuration, and internal network routing for Microsoft Entra Internet Access and Microsoft Entra Private Access.
- Remote network connectivity.
- Non-Microsoft security information and event management \(SIEM\) integration.

### Source environment expectations

The on-premises Active Directory and its environment are prepared for Microsoft Entra, including remediation of identified issues that prevent integration with Microsoft Entra ID and other in-scope features.

## Copilot in Entra

FastTrack provides remote guidance for:

- Onboarding assistance, including:

  - Provisioning Security Compute Units \(SCUs\) \(Microsoft 365 E5 customer tenants are automatically provisioned and onboarded to Security Copilot\).
  - Configuring default environments with necessary roles and permissions and enabling Security Copilot embedded experiences.

- Walkthroughs for Copilot in Entra embedded experiences using prompts and natural language, including:

  - Using Copilot in Entra to protect identities and secure access with AI-driven risk detection and mitigation.
  - Using Copilot in Entra to troubleshoot access failure during critical access attempts.
  - Demonstrating assistance in incident investigation and troubleshooting with Microsoft Entra skills in Security Copilot.
  - Demonstrating assistance in lifecycle workflows to assist with employee onboarding scenarios.
  - Demonstrating assistance to investigate and remediate risky applications registered with Microsoft Entra.

- Walkthroughs for Copilot in Entra for agentic AI experiences, including:

  - Using the Microsoft Entra Conditional Access optimization agent and demonstrating how the agent drives one-click recommendations to improve your security posture.

### Out of scope

- Detailed pricing information. Contact your account team for more information.
- Providing walkthroughs of standalone experiences.
- Creating new custom agents.
- Deploying third-party agents.

## Microsoft Entra ID Free

FastTrack provides remote guidance for:

- User and group management.
- User self-service password change \(cloud users\).
- Basic identity and access reports.
- Single Sign-On \(SSO\) for Microsoft 365, Azure, and thousands of SaaS applications.
- Enterprise application integration and application registrations.
- Security Defaults \(includes baseline security policies and MFA enforcement\).
- Multi-Factor Authentication \(MFA\) through Security Defaults.
- FIDO2 security keys or passkeys.
- Microsoft Authenticator passwordless sign-in.
- Windows Hello for Business.
- Certificate-Based Authentication \(CBA\).
- Microsoft Entra Join \(Azure AD Join\).
- Microsoft Entra Hybrid Join.
- Device registration.
- Password Hash Synchronization \(PHS\).
- Pass-Through Authentication \(PTA\).
- Seamless Single Sign-On \(Seamless SSO\).
- Microsoft Entra Connect.
- Microsoft Entra Cloud Sync.
- Hybrid identity and directory synchronization.
- Basic B2B collaboration or guest users.

### Out of scope

- Tenant and subscription management. \(Coordinate with your account team.\)
- Billing and account management. \(Coordinate with your account team.\)

### Microsoft advanced deployment guides

Microsoft provides customers with technology and guidance to assist with deploying your Microsoft 365, Microsoft Viva, and security services. We encourage our customers to start their deployment journey with [these](https://go.microsoft.com/fwlink/?linkid=2226341) offerings.

For non-IT admins, see [Microsoft 365 Setup](https://go.microsoft.com/fwlink/?linkid=2247616).

Note

If deployment guidance for a product is not listed in the FastTrack service, complete the Request for Assistance form, to ensure you’re directed to the most appropriate resources for your deployment goals and organizational needs. Once submitted, your request will be reviewed and routed to a resource who can best support your deployment goals.

Note

*Please note that the scope and SLA of support may vary depending on the specific workload. FastTrack can help recommend resources from self-guidance, Microsoft Unified offerings, or Microsoft partners to meet your deployment needs.*
