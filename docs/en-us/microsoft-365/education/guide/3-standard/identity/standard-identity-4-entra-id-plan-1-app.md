<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/education/guide/3-standard/identity/standard-identity-4-entra-id-plan-1-app -->
<!-- Sitemap-Last-Modified: 2025-08-22 -->

# Step 4: Application proxy in Microsoft Entra ID P1

![](https://learn.microsoft.com/en-us/microsoft-365/education/guide/images/sections/standardsm.png)

Microsoft Entra Application Proxy in Microsoft Entra ID P1 for education enables secure, remote access to on-premises web applications without requiring a VPN. This is valuable for educational institutions that maintain legacy systems \(like student information systems or internal portals\) behind firewalls but want to make them accessible to students, faculty, or staff from anywhere.

Application Proxy is a feature of Microsoft Entra ID P1 that allows you to:

- Publish on-premises web apps to external users securely.
- Use Microsoft Entra ID for pre-authentication and single sign-on \(SSO\).
- Avoid exposing internal networks directly to the internet.

**How it works in education:**

- **Connector Installation:** A lightweight connector is installed on a Windows Server inside the school’s network. This connector securely relays traffic between Microsoft Entra and the internal app.
- **App Publishing:** Admins publish the internal app via the Microsoft Entra admin center, specifying internal and external URLs, authentication settings, and access policies.
- **User Access:** Students or staff sign in using their Microsoft Entra credentials. Based on Conditional Access policies, they're either granted or denied access. SSO can be configured for seamless sign in.
- **Security Enforcement:** Risk-based Conditional Access, MFA, and device compliance policies can be layered on top to protect sensitive educational data.

**Key benefits for education:**

- Remote access to legacy systems: Enables secure access to apps like SIS, HR portals, or research databases without VPN.
- Simplified IT management: Reduces the need for complex firewall rules or third-party remote access tools.
- Enhanced security: Integrates with Microsoft Entra Conditional Access, Identity Protection, and logging for audit and compliance.
- Cost-effective: Included in Microsoft Entra ID P1, which is part of Microsoft 365 A5 for Education.

**Considerations and limitations:**

- Pre-authentication is designed for interactive user sessions. For service-to-service scenarios \(for example, bots or APIs\), JWT bearer tokens may not be supported unless specific configurations are met.
- HTTP/2 support is limited; some customers report fallback to HTTP/1.1.
- Automation of connector deployment and app registration \(for example, via Terraform\) is possible but may require workarounds due to current limitations in service principal support.

**Feature list:**

- **Secure remote access**: Allows users to access on-premises web applications from anywhere, without the need for a VPN.
- **Single sign-on \(SSO\)**: Integrates with Microsoft Entra ID to provide a seamless single sign-on experience for users accessing on-premises applications.
- **Pre-authentication**: Ensures that users are authenticated by Microsoft Entra ID before they can access the on-premises application, enhancing security.
- **Conditional Access**: Supports conditional access policies, allowing administrators to enforce security requirements such as multifactor authentication and device compliance.
- **Seamless integration**: Works with a variety of on-premises applications, including those that use Integrated Windows Authentication \(IWA\) and header-based authentication.
- **Scalability**: Can be deployed using existing infrastructure and scales to support a large number of users and applications.
- **Monitoring and reporting**: Provides detailed logs and reports on user access and application usage, helping administrators monitor and manage access.

**Learn more:**

- [Using Microsoft Entra application proxy to publish on-premises apps for remote users](https://learn.microsoft.com/en-us/entra/identity/app-proxy/overview-what-is-app-proxy)
