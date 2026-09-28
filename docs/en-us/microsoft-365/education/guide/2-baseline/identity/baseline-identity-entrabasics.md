<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/education/guide/2-baseline/identity/baseline-identity-entrabasics -->
<!-- Sitemap-Last-Modified: 2026-04-28 -->

# Step 2: Configure Microsoft Entra ID - Basic

![](https://learn.microsoft.com/en-us/microsoft-365/education/guide/images/pillars/icon-identity.png)

![](https://learn.microsoft.com/en-us/microsoft-365/education/guide/images/sections/baselinesm.png)

Core to managing authentication and access is using Microsoft Entra ID. This article covers basic Microsoft Entra ID configuration steps and considerations for setting up Microsoft Entra ID following each step.

## Roles and responsibilities

- IT Admin
- Identity Admin

## Initial configuration steps for Microsoft Entra ID - Basic

To configure Microsoft Entra ID, open the [Microsoft Entra ID setup guide](https://learn.microsoft.com/en-us/entra/fundamentals/).

1. [Microsoft Entra ID license](https://learn.microsoft.com/en-us/entra/fundamentals/licensing) and [admin accounts](https://learn.microsoft.com/en-us/entra/fundamentals/users-assign-role-azure-portal)

   Microsoft Entra ID offers several licensing options to suit different organizational needs:

   - **Microsoft Entra ID license**

     - **Microsoft Entra ID Free:** Included with Microsoft cloud subscriptions like Azure and Microsoft 365. It provides basic identity and access management features.
     - **Microsoft Entra ID P1:** Available as a standalone product or included with Microsoft 365 E3 and Business Premium. It offers advanced identity management features, including conditional access and self-service password reset.
     - **Microsoft Entra ID P2:** Available as a standalone product or included with Microsoft 365 E5. It includes all P1 features plus advanced identity protection and privileged identity management.

   - **Admin Accounts** - Admin accounts in Microsoft Entra ID are crucial for managing and securing your organization’s identity infrastructure. Here are the key types of admin roles:

     - **Global Administrator:** Has access to all administrative features in Microsoft Entra ID and other Microsoft services.
     - **User Administrator:** Can manage users and groups, including resetting passwords and monitoring service health.
     - **Security Administrator:** Manages security-related features, including conditional access and identity protection.
     - **Privileged Role Administrator:** Manages role assignments in Microsoft Entra Privileged Identity Management \(PIM\) and can activate roles.

2. Authentication, single sign-on and application access

   Microsoft Entra ID provides robust authentication, single sign-on \(SSO\), and application access management features to enhance security and user experience.

   - **Authentication** - Microsoft Entra ID supports various authentication methods to ensure secure access:

     - **Password-based authentication:** Users sign in with their username and password.
     - **Multi-factor authentication \(MFA\):** Adds an extra layer of security by requiring additional verification methods, such as a phone call, text message, or app notification.
     - **Passwordless authentication:** Uses methods like Windows Hello, FIDO2 security keys, or the Microsoft Authenticator app to sign in without a password.

   - **[Single Sign-On \(SSO\)](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/what-is-single-sign-on)** - SSO allows users to access multiple applications with a single set of credentials, reducing password fatigue and improving security. Microsoft Entra ID supports several SSO methods:

     - **Federated SSO:** Uses protocols like SAML, WS-Federation, or OpenID Connect to authenticate users across different systems.
     - **Password-based SSO:** Stores and replays usernames and passwords for applications that don’t support modern authentication protocols.
     - **Linked-based SSO:** Redirects users to the application’s sign-in page and automatically signs them in.

   - [**Application access**](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/what-is-access-management) - Microsoft Entra ID simplifies application access management:

     - **Enterprise Applications:** Integrate thousands of pre-configured applications from the Microsoft Entra application gallery for SSO.
     - **Conditional Access:** Create policies to control access based on conditions like user location, device state, and risk level.
     - **My Apps Portal:** Provides a centralized location for users to access their applications and manage their credentials.

3. Administration and hybrid identity

   Microsoft Entra ID administration involves managing identities, access, and security within your organization. Here are some key aspects:

   - **User and Group Management:**

     - Add and manage users: Create, update, and delete user accounts.
     - Group management: Organize users into groups for easier management and access control.

   - **Role-Based Access Control \(RBAC\):**

     - Assign roles: Use predefined roles or create custom roles to delegate permissions.
     - Privileged Identity Management \(PIM\): Manage, control, and monitor access within your organization to reduce the risk of excessive, unnecessary, or misused access permissions.

   - **Security and Compliance:**

     - Conditional Access: Implement policies to control access based on conditions like user location, device state, and risk level.
     - Identity Protection: Detect and respond to identity-based risks using machine learning and behavioral analytics.

   - **Monitoring and Reporting:**

     - Audit logs: Track changes and access events.
     - Sign-in logs: Monitor user sign-ins to detect unusual activity.

4. [End user Self-Service](https://www.microsoft.com/security/business/identity-access/microsoft-entra-user-self-service-portals)

   Microsoft Entra ID offers several self-service features to empower users and reduce the burden on IT support. Here are some key self-service capabilities:

   - **Self-Service Password Reset \(SSPR\)** - Users can reset their passwords without needing to contact the help desk. This feature can be configured to require multiple authentication methods for added security.
   - **My Apps Portal** - The My Apps portal is a centralized location where users can discover and manage their applications. It provides single sign-on \(SSO\) access to all the apps they need, making it easier to find and use them.
   - **My Account Portal** - This portal allows users to manage their own identity information, including updating security contact details and managing their authentication methods.
   - **My Sign-ins** - Users can view their sign-in history and monitor for any suspicious activity. If they notice anything unusual, they can report it directly through the portal.
   - **My Access** - From the My Access portal, users can request access to applications and services, manage their access packages, and view the status of their requests.


   **Benefits of Self-Service**


   - **Reduced IT workload:** By enabling users to manage their own accounts and access, the number of help desk calls can be significantly reduced.
   - **Improved security:** Users can quickly update their security settings and monitor their own activity, helping to detect and respond to potential threats faster.
   - **Enhanced user experience:** Self-service portals provide a convenient and efficient way for users to manage their access and identity information.

## On-premises and hybrid considerations

1. [Microsoft Entra ID Connect \(Sync\) for Single-Sign-On \(SSO\)](https://learn.microsoft.com/en-us/entra/identity/hybrid/connect/how-to-connect-sso-quick-start)

   To enable Single Sign-On \(SSO\) with Microsoft Entra ID, you can use either Microsoft Entra Connect or Microsoft Entra Cloud Sync. Here’s a step-by-step guide to setting up SSO:

   - **Using Microsoft Entra Connect**

     - **Install Microsoft Entra Connect:**

       - Download the latest version of Microsoft Entra Connect from the Microsoft Entra admin center.
       - Run the installer and follow the setup wizard to configure synchronization between your on-premises Active Directory \(AD\) and Microsoft Entra ID.

   - **Enable Seamless SSO:**

     - Open the Microsoft Entra Connect tool and navigate to the **Additional tasks** section.
     - Select **Configure Seamless Single Sign-On** and follow the prompts to enable it.

   - **Configure Authentication:**

     - Choose your preferred authentication method \(Password Hash Synchronization, Pass-Through Authentication, or Federation\).
     - Ensure that your environment meets the prerequisites for the chosen method.

   - **Verify Configuration:**

     - Sign in to the Microsoft Entra admin center.
     - Navigate to **Identity > Hybrid management > Microsoft Entra Connect > Connect sync**.
     - Verify that Seamless SSO is set to **Enabled**.

2. Microsoft Entra ID Connect \(Sync\) with Cloud Identities

   - **Set Up Cloud Sync:**

     - Sign in to the Microsoft Entra admin center.
     - Navigate to **Identity > Hybrid management > Microsoft Entra Cloud Sync**.
     - Follow the setup wizard to configure synchronization between your on-premises AD and Microsoft Entra ID.

   - **Enable Seamless SSO:**

     - Download and extract the necessary files for Seamless SSO.
     - Import the Seamless SSO PowerShell module and enable the feature for your AD forests using PowerShell commands.

   - **Verify Configuration:**

     - Ensure that Seamless SSO is enabled and functioning correctly by checking the status in the Microsoft Entra admin center.


   **Benefits of SSO with Microsoft Entra ID**


   - **Improved User Experience:** Users can access multiple applications with a single set of credentials, reducing the need to remember multiple passwords.
   - **Enhanced Security:** Centralized authentication and conditional access policies help protect against unauthorized access.
   - **Simplified Management:** Administrators can manage user access and authentication settings from a single platform.

3. Secure access partnerships

   Microsoft Entra ID collaborates with various partners to enhance secure access to applications, especially for hybrid and legacy environments. Here are some key aspects of these partnerships:

   - **Secure Hybrid Access** - Microsoft Entra ID enables secure hybrid access by integrating with partner solutions to protect both on-premises and cloud applications. This includes:

     - Application Proxy: Provides secure remote access to on-premises web applications without the need for a VPN. Users can connect to applications from any device using single sign-on \(SSO\) and multifactor authentication \(MFA\).
     - Conditional Access: Allows organizations to apply policies that control access based on user location, device state, and risk level.

   - **Partner Integrations** - Microsoft collaborates with several partners to offer pre-built solutions for secure hybrid access. These partners help integrate on-premises and legacy applications with Microsoft Entra ID, ensuring they can use modern authentication methods like SSO and MFA. Some notable partners include:

     - Akamai Technologies: Provides solutions for integrating SSO with Microsoft Entra ID.
     - Banyan Security, Datawiza Access Broker, and CheckPoint Harmony: Offer secure hybrid access solutions to support legacy applications.


   **Benefits of Partner Integrations**


   - Enhanced Security: By integrating with trusted partners, organizations can ensure secure access to applications, protecting users, apps, and data both in the cloud and on-premises.
   - Simplified Management: Partner solutions help streamline the management of hybrid environments, making it easier to implement and enforce security policies.
   - Zero Trust Strategy: These integrations support the adoption of Zero Trust principles, ensuring that every access request is authenticated, authorized, and encrypted.

4. Role-based access control \(RBAC\)

   Microsoft Entra ID uses role-based access control \(RBAC\) to manage permissions and access to resources.

   - **Key Concepts**

     - Role Assignments: These link a role definition to a user, group, or service principal at a specific scope \(for example, organization-wide or specific resources\) to grant access1.
     - Role Definitions: There are built-in roles with predefined permissions and custom roles that you can tailor to meet specific needs1.
     - Scopes: Define the set of resources the role member can access. Common scopes include organization-wide or specific objects like applications.

   - **Types of Roles**

     - Built-in Roles: These come with a fixed set of permissions and can't be modified.
     - Custom Roles: You can create these by selecting permissions from a preset list and assigning them to users or groups.

   - **Application of RBAC**

     - App Roles: Define roles for applications and assign them to users or groups. These roles are included in security tokens and help in making authorization decisions.
     - Security Groups: Use groups to manage access, where group memberships are interpreted as role memberships.

## User and group provisioning

1. [User management](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/how-provisioning-works)

   User provisioning in Microsoft Entra ID involves the automatic creation, maintenance, and removal of user identities and roles in various applications that users need access to. Here’s a breakdown of how it works:

   - **Key Aspects of User Provisioning**

     - Automatic Provisioning: This process uses the System for Cross-Domain Identity Management \(SCIM\) 2.0 protocol to automate the creation, updating, and deletion of user accounts in cloud applications1. This ensures that user identities are consistently managed across different systems.
     - HR-Driven Provisioning: When a new employee is added to the HR system, their user account is automatically created in Microsoft Entra ID, Active Directory, and other necessary applications2. This also includes updating user attributes and disabling accounts when employees leave the organization.
     - App Provisioning: This refers to the automatic creation of user identities and roles specifically for cloud applications. It includes maintaining and removing these identities as user statuses or roles change.
     - Directory Provisioning: This involves synchronizing user identities between on-premises directories and Microsoft Entra ID, ensuring a unified identity across both environments.

   - **Provisioning Workflow**

     - Outbound Provisioning: From Microsoft Entra ID to SaaS applications, creating and managing user accounts based on changes in Microsoft Entra ID.
     - Inbound Provisioning: From HR systems to Microsoft Entra ID, ensuring new hires and changes in employee status are reflected in user accounts.

   - **Security and Compliance**

     - Encryption: All provisioning data is encrypted using HTTPS TLS 1.2 to ensure secure communication between Microsoft Entra ID and the application endpoints.
     - Authorization: Credentials are required to connect Microsoft Entra ID to the application’s user management API, ensuring secure and authorized access.

2. [Group management](https://learn.microsoft.com/en-us/entra/identity/hybrid/cloud-sync/tutorial-group-provisioning)

   Group provisioning in Microsoft Entra ID allows you to manage and automate the creation, maintenance, and removal of group memberships across various applications and directories.

   - **Key Features**

     - Automatic Group Provisioning: With a Microsoft Entra ID P1 or P2 license, you can use groups to assign access to SaaS applications. The provisioning service automatically adds or removes users from these applications based on their group memberships.
     - Group Sync: You can configure group provisioning to synchronize group memberships between Microsoft Entra ID and on-premises Active Directory. This ensures that group memberships are consistent across both environments.
     - SCIM Protocol: The System for Cross-Domain Identity Management \(SCIM\) protocol is used to automate the provisioning and deprovisioning of group memberships in cloud applications.

   - **Configuration Steps**

     - Sign In: Access the Microsoft Entra admin center with appropriate administrative privileges.
     - Navigate to Provisioning: Navigate to **Identity > Hybrid management > Microsoft Entra Connect > Cloud sync**.
     - Create Configuration: Select New configuration and choose Microsoft Entra ID to AD sync.
     - Set Provisioning Scope: Define the scope to sync only assigned users and groups.


   **Benefits** - Efficiency: Automates repetitive tasks, reducing administrative overhead. - Consistency: Ensures that group memberships are up-to-date across all connected systems. - Security: Helps maintain the principle of least privilege by ensuring users have appropriate access based on their group memberships.

## Multifactor authentication and conditional access

1. [Multifactor authentication \(MFA\)](https://learn.microsoft.com/en-us/entra/identity/authentication/tutorial-enable-azure-mfa) Microsoft Entra ID multifactor authentication \(MFA\) enhances security by requiring users to provide multiple forms of verification during sign-in.

   - **How It Works** - Microsoft Entra MFA requires two or more of the following authentication methods:

     - Something you know: Typically a password.
     - Something you have: A trusted device like a phone or hardware key.
     - Something you are: Biometrics such as a fingerprint or face scan.

   - **Available Verification Methods**

     - Microsoft Authenticator: A mobile app that provides a second layer of security.
     - Authenticator Lite \(in Outlook\): A simplified version of the Microsoft Authenticator.
     - Windows Hello for Business: Uses biometric sign-in options.
     - Passkey \(FIDO2\): A hardware-based authentication method.
     - Certificate-based authentication: Uses digital certificates.
     - OATH hardware and software tokens: One-time password tokens.
     - SMS and Voice Call: Sends a code via text message or phone call.

   - **Enabling MFA**

     - Security Defaults: Quickly enable MFA for all users using security defaults in Microsoft Entra tenants2.
     - Conditional Access Policies: Create policies to require MFA for specific sign-in events or user groups.


   **Benefits** - Increased Security: Reduces the risk of unauthorized access by adding layers of verification. - Flexibility: Supports various authentication methods to suit different user needs. - Ease of Use: Integrated into the Microsoft Entra sign-in process, making it seamless for users

2. [Passwordless](https://learn.microsoft.com/en-us/entra/identity/authentication/howto-authentication-passwordless-phone)

   Microsoft Entra ID offers several passwordless authentication methods to enhance security and user convenience by eliminating the need for passwords.

   - **Passwordless Authentication Methods**

     - Windows Hello for Business: Uses biometrics \(fingerprint or facial recognition\) or a PIN tied to the user’s device. This method is ideal for users with dedicated Windows PCs.
     - Microsoft Authenticator: This mobile app provides key-based authentication. Users can sign in by approving a notification on their device, using a PIN, or biometric verification.
     - FIDO2 Security Keys: These hardware devices use public key cryptography to provide strong authentication. Users can authenticate by inserting the key into a USB port or tapping it on an NFC reader.
     - Certificate-Based Authentication: Uses digital certificates to authenticate users, often in environments where smart cards are already in use.

   - **Benefits of Passwordless Authentication**

     - Enhanced Security: Reduces the risk of phishing and password-related attacks.
     - User Convenience: Simplifies the sign-in process by removing the need to remember and manage passwords.
     - Compliance: Helps meet regulatory requirements for strong authentication.

   - **Setting Up Passwordless Authentication**

     - Enable Passwordless Sign-In: In the Microsoft Entra admin center, navigate to the authentication methods policy and enable the desired passwordless methods.
     - User Registration: Users need to register their devices or methods \(for example, set up Windows Hello, register the Authenticator app\) through the security info page.
     - Conditional Access Policies: Configure policies to enforce passwordless authentication for specific scenarios or user groups.

3. [Global password protection and management \(cloud users only\)](https://learn.microsoft.com/en-us/entra/identity/authentication/concept-password-ban-bad)

   Microsoft Entra ID offers robust global password protection and management features to enhance security for cloud users.

   - **Key Features**

     - Global Banned Password List: Microsoft Entra ID automatically applies a global banned password list to all users. This list is continuously updated based on security telemetry to block commonly used weak passwords and their variants.
     - Custom Banned Password List: Organizations can define their own custom banned password lists to block specific terms that are weak or relevant to their environment1.
     - Password Spray Attack Protection: The system detects and blocks attempts to use common passwords across multiple accounts, protecting against password spray attacks.
     - Third-Party Compromised Password Lists: Microsoft Entra ID can integrate with third-party services to block passwords that have been compromised in data breaches.

   - **How It Works**

     - Password Change and Reset: When users change or reset their passwords, the system checks the new password against both the global and custom banned password lists to ensure it meets security standards.
     - No Configuration Needed: The global banned password list is automatically applied and can't be disabled, ensuring consistent protection across all users.

   - **Benefits**

     - Enhanced Security: By blocking weak and compromised passwords, the system significantly reduces the risk of unauthorized access.
     - Ease of Use: Users are guided to create stronger passwords without additional configuration required from administrators.
     - Compliance: Helps organizations meet security standards and regulatory requirements for password management.

4. [Conditional Access](https://learn.microsoft.com/en-us/entra/identity/conditional-access/overview)

   Microsoft Entra ID Conditional Access is a powerful feature that helps organizations enforce security policies based on specific conditions. Conditional Access is a policy-based approach that evaluates various signals to make decisions about granting or denying access to resources. It’s a core component of Microsoft’s Zero Trust security model.

   - **Key Components**

     - Signals: These are the conditions that Conditional Access policies evaluate, such as user identity, device compliance, location, and risk level1.
     - Policies: These are the rules that define what actions to take based on the evaluated signals. Policies can be configured to require multifactor authentication \(MFA\), block access, or grant access with restrictions.

   - **Common Use Cases**

     - Require MFA for All Users: Enforce MFA for all users accessing sensitive applications.
     - Block Access from Untrusted Locations: Deny access from specific geographic locations or IP ranges.
     - Device Compliance: Ensure that only compliant devices can access corporate resources.

   - **Setting Up Conditional Access**

     - Define Conditions: Specify the signals to evaluate, such as user groups, locations, devices, and applications.
     - Configure Access Controls: Decide what actions to take when conditions are met, like requiring MFA or blocking access.
     - Enable Policy: Test the policy with a small group before rolling it out organization-wide to ensure it works as expected.

   - **Benefits**

     - Enhanced Security: Protects against unauthorized access by evaluating multiple factors before granting access.
     - Flexibility: Allows for granular control over access based on various conditions.
     - Compliance: Helps meet regulatory requirements by enforcing strict access controls.

## Identity governance

1. [Automated user provisioning to SaaS apps](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/user-provisioning)

   Automated user provisioning in Microsoft Entra ID simplifies the process of managing user identities and roles in various SaaS applications.

   - **Key Features**

     - Automatic User Creation: When a new user is added to Microsoft Entra ID, their account is automatically created in connected SaaS applications like Salesforce, ServiceNow, and Dropbox.
     - Maintenance and Updates: The provisioning service keeps user information up-to-date across all applications. If a user’s role or status changes, these updates are automatically reflected in the connected apps.
     - Deprovisioning: When a user leaves the organization or no longer needs access, their accounts in the SaaS applications are automatically disabled or removed.

   - **Configuration Steps**

     - Sign In: Access the Microsoft Entra admin center with appropriate administrative privileges.
     - Navigate to **Enterprise Applications > Identity > Applications > Enterprise applications**.
     - Select **Application**: Choose the SaaS application you want to configure for provisioning.
     - Navigate to the **Provisioning** tab and set the Provisioning Mode to **Automatic**.
     - Admin Credentials: Provide the necessary admin credentials to connect Microsoft Entra ID to the application’s user management API.
     - Mapping and Scoping: Define the user attributes and scope of provisioning \(for example, specific groups or all users\).

   - **Benefits**

     - Efficiency: Reduces the manual effort required to manage user accounts across multiple applications.
     - Consistency: Ensures that user information is consistent and up-to-date across all connected systems.
     - Security: Automatically removes access for users who no longer need it, reducing the risk of unauthorized access.

## Event logging and reporting

1. Basic security and usage reports

   Microsoft Entra ID provides several basic security and usage reports to help you monitor and manage your environment effectively.

   - **Key Reports**

     - Sign-ins Report: This report provides detailed information about user sign-ins, including the status \(successful or failed\), location, and application accessed. It helps identify unusual sign-in patterns and potential security risks.
     - Audit Logs: These logs capture all changes made to your Microsoft Entra ID resources, such as user and group management activities. They're essential for tracking administrative actions and ensuring compliance1.
     - Usage and Insights Report: This report offers an application-centric view of your sign-in data, including authentication methods used, service principal sign-ins, and application credential activity. It helps you understand how users are accessing applications and identify any potential issues.
     - Authentication Methods Activity: This report shows how different authentication methods are being used within your organization. It includes data on registration and usage of methods like MFA, passwordless sign-ins, and more.

   - **Accessing Reports**

     - Microsoft Entra Admin Center: Sign in to the admin center and navigate to **Identity > Monitoring & health > Usage & insights** to access these reports.
     - Microsoft Graph API: You can also query these reports programmatically using the Microsoft Graph API for more customized reporting and integration with other tools.

   - **Benefits**

     - Enhanced Security: By monitoring sign-in activities and changes, you can quickly detect and respond to potential security threats.
     - Compliance: Audit logs and detailed reports help meet regulatory requirements and internal policies.
     - Operational Insights: Usage reports provide valuable insights into how users interact with applications, helping optimize resource allocation and user experience.

2. Security information and events management \(SIEM\) connectivity Microsoft Entra ID integrates with Security Information and Event Management \(SIEM\) tools to help you monitor and analyze security events.

   - **Steps to Integrate with SIEM**

     - Create an Azure Event Hub: This is the first step to stream your Microsoft Entra logs. The Event Hub acts as a pipeline to send logs to your SIEM tool.
     - Configure Diagnostic Settings:

       - Sign in to the Microsoft Entra admin center.
       - Navigate to **Identity > Monitoring & health > Diagnostic settings**.
       - Select **+ Add diagnostic setting** to create a new integration or **Edit setting** for an existing one.
       - Enter a name for the diagnostic setting.
       - Select the log categories you want to stream \(for example, AuditLogs, Sign-ins\).
       - Check the Stream to an event hub option.
       - Choose the Azure subscription and Event Hubs namespace.

   - Set Up SIEM Tool Integration:

     - Once logs are streaming to the Event Hub, configure your SIEM tool to collect these logs.
     - Supported SIEM tools include Splunk, SumoLogic, and ArcSight.
     - Follow the specific integration steps for your SIEM tool, such as installing the Splunk Add-on for Microsoft Cloud Services or configuring SumoLogic to collect logs.

   - **Benefits**

     - Centralized Monitoring: Consolidate logs from various sources for comprehensive security monitoring.
     - Enhanced Security: Detect and respond to security incidents more effectively by analyzing logs in real-time.
     - Compliance: Helps meet regulatory requirements by maintaining detailed logs of security events.

## Next steps

The next step is to consider which identity applications you want to use.

[Next: Consider education identity steps>](https://learn.microsoft.com/en-us/microsoft-365/education/guide/2-baseline/identity/baseline-identity-edu-steps)
