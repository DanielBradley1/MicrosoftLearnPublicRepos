<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/education/guide/3-standard/identity/standard-identity-2-entra-id-p1-access-controls -->
<!-- Sitemap-Last-Modified: 2025-12-02 -->

# Step 2: Microsoft Entra ID access controls

![](https://learn.microsoft.com/en-us/microsoft-365/education/guide/images/sections/standardsm.png)

Microsoft Entra ID Plan 1 provides educational institutions with robust access control capabilities to safeguard identities and resources. This article outlines the key features and benefits of Entra ID P1 access controls, including Conditional Access, multifactor authentication, dynamic group management, role-based access control, and single sign-on. These tools help schools and universities enhance security, streamline user management, and support compliance in a modern learning environment.

## Microsoft Entra ID P1 Conditional Access in education

Conditional Access in Microsoft Entra ID P1 provides educational institutions with advanced security controls to protect sensitive data and ensure secure access to resources.

**Key features:**

- **User and group targeting**: Administrators can create policies that apply to specific users or groups, providing fine-grained control over who can access certain resources.
- **IP location information**: Policies can be configured to allow or block access based on trusted IP address ranges or specific geographic locations.
- **Device-based policies**: Conditional Access can enforce policies based on the device's platform or compliance state, ensuring that only secure devices can access sensitive information.
- **Application-specific policies**: Different policies can be triggered based on the application being accessed, allowing for tailored security measures.
- **Real-time risk detection**: Integration with Microsoft Entra ID Protection allows for the identification and remediation of risky users and sign-in behaviors.
- **Multi-factor authentication \(MFA\)**: Policies can require MFA for extra security, ensuring that users verify their identity through multiple methods.
- **Session controls**: Integration with Microsoft Defender for Cloud Apps enables monitoring and controlling user sessions in real-time, providing greater visibility and control over cloud activities.

**Learn more:**

- [What is Conditional Access?](https://learn.microsoft.com/en-us/entra/identity/conditional-access/overview)

## Microsoft Entra ID P1 multifactor authentication \(MFA\) in education

Multifactor authentication \(MFA\) in Microsoft Entra ID P1 provides enhanced security for educational institutions by requiring multiple forms of verification to access resources.

**Key features:**

- **Multiple authentication methods**: Supports various methods such as push notifications, text messages, phone calls, and app-based authentication \(for example, Microsoft Authenticator\) to verify user identity.
- **Conditional Access integration**: Allows administrators to enforce MFA based on specific conditions, such as user location, device compliance, or application being accessed.
- **Passwordless authentication**: Supports passwordless sign-in options like Windows Hello, FIDO2 security keys, and biometric authentication, providing a more secure and user-friendly experience.
- **Combined security information registration**: Simplifies the user onboarding process by allowing users to register for both MFA and self-service password reset \(SSPR\) at the same time.
- **Resiliency**: Encourages users to register multiple authentication methods, ensuring they have alternative options if one method is unavailable.
- **Risk-based authentication**: Detects and responds to suspicious sign-in attempts, prompting for additional verification when necessary.

**Learn more:**

- [How it works: Microsoft Entra multifactor authentication](https://learn.microsoft.com/en-us/entra/identity/authentication/concept-mfa-howitworks)

## Microsoft Entra ID P1 Dynamic group management in education

Dynamic group management in Microsoft Entra ID P1 offers several features that enhance user and device management for educational institutions.

**Key features:**

- **Attribute-based rules**: Allows administrators to create dynamic membership rules based on user or device attributes, such as department, job title, or device compliance state.
- **Automated group membership**: Automatically adds or removes users and devices from groups based on the defined rules, ensuring that group memberships are always up-to-date.
- **Rule builder**: Provides a user-friendly interface in the Azure portal to create and update membership rules quickly and easily.
- **Support for security and Microsoft 365 groups**: Enables dynamic membership for both security groups and Microsoft 365 groups, although security groups can include both users and devices, while Microsoft 365 groups can include only users.
- **Scalability**: Supports up to 15,000 dynamic membership groups per tenant, allowing for extensive and flexible group management.
- **Real-time evaluation**: Continuously evaluates user and device attributes to ensure that group memberships reflect the most current information.

**Learn more:**

- [Create or update a dynamic membership group in Microsoft Entra ID](https://learn.microsoft.com/en-us/entra/identity/users/groups-create-rule)

## Role-based access control \(RBAC\) in Microsoft Entra ID P1

Role-based access control \(RBAC\) in Microsoft Entra ID P1 provides a structured approach to managing access to resources based on user roles within an organization.

**Key features:**

- **Role assignment**: Users are assigned roles that grant them specific permissions to perform tasks and access resources. This ensures that users only have the access necessary for their job functions.
- **Built-in and custom roles**: Microsoft Entra ID P1 includes a variety of built-in roles with predefined permissions. Additionally, administrators can create custom roles tailored to the specific needs of their organization.
- **Role-assignable groups**: Roles can be assigned to groups instead of individual users, simplifying the management of permissions. Adding or removing users from a group automatically updates their access rights.
- **Administrative units**: These units allow for the delegation of administrative tasks within specific scopes, such as departments or regions, providing more granular control over resource management.
- **Scope definition**: Roles can be assigned at different scopes, such as organization-wide or specific to certain resources, ensuring that permissions are applied appropriately.
- **Least privilege principle**: RBAC supports the principle of least privilege by ensuring users have the minimum level of access necessary to perform their duties, reducing the risk of unauthorized access.

**Learn more:**

- [Overview of role-based access control in Microsoft Entra ID](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/custom-overview)

## Single sign-on \(SSO\) in Microsoft Entra ID P1

Single sign-on \(SSO\) in Microsoft Entra ID P1 provides a seamless and secure authentication experience for users accessing multiple applications.

**Key features:**

- **Unified access**: Allows users to sign in once with their Microsoft Entra ID credentials and gain access to all their applications, both on-premises and cloud-based, without needing to sign in again.
- **Federated authentication**: Supports federated SSO using protocols like SAML 2.0, WS-Federation, and OpenID Connect, enabling integration with a wide range of applications.
- **Application integration**: Easily integrates with thousands of SaaS applications, as well as custom and on-premises applications, providing a consistent authentication experience.
- **Conditional Access**: Works in conjunction with Conditional Access policies to ensure that access to applications is secure and compliant with organizational policies.
- **Improved user experience**: Reduces the need for multiple passwords and sign-ins, enhancing user productivity and satisfaction.
- **Centralized management**: Administrators can manage access to all applications from a single platform, simplifying the administration of user identities and permissions.

**Learn more:**

- [What is single sign-on in Microsoft Entra ID?](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/what-is-single-sign-on)
