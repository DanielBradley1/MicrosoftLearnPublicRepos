<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/education/guide/1-reference/design-credential-authentication-strategies -->
<!-- Sitemap-Last-Modified: 2026-02-11 -->

# Design authentication and credential strategies

This article describes the actions necessary to secure and manage credentials and authentication methods in an educational organization that spans multiple tenants.

*Credentials* are specific to a user’s identity. For example, their individual username and password, PIN, or biometric information. Every user, including IT administrators, teachers, staff persons, and students has credentials.

An *authentication method* is how the user submits or attests to their credentials. For example, a user inputs their credentials in a sign-in screen or via the Microsoft Authenticator app in which they set up their account.

Authentication methods can also be broken down into categories, or types, such as:

- Sign-in authentication
- Password reset authentication
- Multifactor authentication

Sign-in authentication is when the user initially enters credentials. Self-service password reset \(SSPR\) and multifactor authentication \(MFA\), are additional types of authentication.

The following table shows how various authentication methods can be used in these scenarios.

| Authentication method | Sign-in authentication | SSPR and MFA |
| --- | --- | --- |
| Password | Yes |  |
| Windows Hello for Business | Yes |  |
| Microsoft Authenticator app | Yes \(Preview\) | MFA and SSPR |
| FIDO2 security keys | Yes \(Preview\) | MFA-only |
| SMS | Yes \(Preview\) | MFA and SSPR |
| Voice call | No | MFA and SSPR |
| Security questions | No | SSPR-only |
| Email address | No | SSPR-only |

Note

To enable the preview functionality for sign-in authentication, open the [Azure portal](https://portal.azure.com/), select **Microsoft Entra ID > Security > Authentication methods > Authentication method policy \(Preview\)**, and enable the preview methods you want to use.

## Authentication types

Passwords and PINs are common credential types. Less common types include picture passwords and pattern locks. Biometric authentication is also rising in popularity. Biometrics identify a user through facial recognition, a fingerprint, or a retinal print.

### Passwordless authentication

A passwordless solution is the most convenient and secure method of authentication. Passwordless authentication eliminates the inconvenience of having to remember passwords and responding to multifactor authentication. It’s more secure because it reduces the risk of phishing and password spray attacks by removing passwords as an attack surface. Microsoft supports the following passwordless authentication methods

- **Windows Hello for Business**. Windows Hello for Business is ideal for users that have a designated Windows PC. The biometric and PIN credentials are tied to the user's PC, which prevents access from anyone other than the designated user and prevents unauthorized access. With public key infrastructure \(PKI\) integration and built-in support for single sign-on \(SSO\), Windows Hello for Business provides a convenient method for seamlessly accessing resources on-premises and in the cloud.
- **Microsoft Authenticator app**. The Authenticator App turns your iOS or Android phone into a strong, passwordless credential. Users can sign in to any platform or browser by getting a notification to their phone, matching a number displayed on the screen to the one on their phone, and then using their biometric \(touch or face\) or PIN credentials to confirm. While this article references the Microsoft Authenticator app, there are other authenticator apps on the market.
- **FIDO2 security key**. FIDO2 security keys allow users to sign in to their resources without a username or password using an external security key or a platform key built into a device.

For more information, see [Passwordless authentication options for Microsoft Entra ID](https://learn.microsoft.com/en-us/azure/active-directory/authentication/concept-authentication-passwordless).

### Password reset authentication

Users’ password resets are one of the biggest sources of volume and cost for help desks. Microsoft Entra ID [self-service password reset \(SSPR\)](https://learn.microsoft.com/en-us/azure/active-directory/authentication/concept-sspr-howitworks) gives users the ability to change or reset their password, with no administrator or help desk involvement. In addition to reducing costs, [SSPR](https://learn.microsoft.com/en-us/azure/active-directory/authentication/concept-sspr-howitworks) mitigates user risk and improves the security posture of your organization. If a user's account is locked or compromised, or they forget their password, they can follow prompts to unblock themselves and get back to work.

Any password change with SSPR requires that passwords conform to [Microsoft Entra password policy](https://learn.microsoft.com/en-us/azure/active-directory/authentication/concept-sspr-policy). These policies determine the required complexity, length, expiration, and acceptable characters. If the password doesn't meet the Microsoft Entra ID \(or on-premises AD\) policy requirements, the user is prompted to try again.

### Multifactor authentication

We recommend requiring MFA for university students, educators, the IT department, and other staff. These groups can be more active on the internet and, therefore, more susceptible to a cyber attack.

Multifactor authentication requires a user to provide an additional form of authentication. It provides additional security by requiring a second form of authentication, such as:

- A code from an SMS text message.
- Answering a phone voice call.
- Providing a code from or biometric information in the Microsoft Authenticator app.
- Using an OAUTH Hardware token.

## Enable SSPR and Azure MFA

Enable both SSPR and MFA to keep your environment more secure. Users must register for these services.

### Enable SSPR

SSPR is managed in the [Azure portal](https://portal.azure.com/) under Microsoft Entra ID > Password reset and lets you choose from the following list of authentication methods:

Recommended – in order of preference

- Mobile app notification \(available only when Number of methods required to reset is set to 2\)
- Mobile app code
- Email
- Mobile phone \(SMS text\)

Not recommended if two recommended options exist

- Office phone \(Voice call\)
- Security questions

Note

Authentication methods you enable are available to every member of the tenant. Since Security questions is the least secure option, we recommend you don't enable it unless no other methods are available. A phone call to an office phone could be compromised and is also not recommended unless there's no other option.

We recommend you make SSPR available to everyone in your tenant except students in elementary and middle school. These students may not have access to a required second form of authentication. For those students, teachers or other staff should be assigned the role of [Password Administrator](https://learn.microsoft.com/en-us/azure/active-directory/users-groups-roles/directory-assign-admin-roles). To enable SSPR for all users except these students:

1. [Create a Microsoft 365 group](https://learn.microsoft.com/en-us/azure/active-directory/fundamentals/active-directory-groups-create-azure-portal) with a descriptive name such as “SSPR” in the Azure portal. Add everyone except for elementary and middle school students. In Microsoft Entra ID, you can [create attribute-based rules to enable dynamic memberships](https://learn.microsoft.com/en-us/azure/active-directory/users-groups-roles/groups-dynamic-membership) for groups. We recommend this approach if you're already capturing attributes that indicate student level. If you need to include external guests, see [Dynamic groups and Microsoft Entra B2B collaboration](https://learn.microsoft.com/en-us/azure/active-directory/external-identities/use-dynamic-groups).
2. Navigate to **Microsoft Entra ID > Security > [password reset](https://portal.azure.com/)** , choose **Selected**, then select that group.

   ![Picture 1.](https://learn.microsoft.com/en-us/microsoft-365/education/guide/1-reference/images/design-credential-authentication-strategies-1.png)

### Enable Azure MFA

We recommend enabling MFA in your tenants and requiring MFA for IT Administrators and anyone with access to student records not their own or their child's. You enforce MFA by using Conditional Access policies.

Once MFA is enabled, users should set one of the following options as their default multifactor authentication method:

- Microsoft Authenticator – notification \(Most recommended\)
- Microsoft Authenticator app or hardware token – code
- SMS text message
- Phone call \(Least recommended\)

Note

We don't recommend that you enable MFA for elementary, middle, and high school students. MFA is generally used to prevent account compromise and damage by a bad actor. Students should have access to only their own information, with limited potential for damage. Also, younger students may not have access to a second form of authentication.

There are two approaches to enabling Azure MFA. We recommend using [Microsoft Entra ID Protection](https://learn.microsoft.com/en-us/azure/active-directory/identity-protection/overview-identity-protection) to manage the roll-out by configuring a Conditional Access policy to require MFA registration. Identity protection [requires that your admins have a Microsoft Entra ID P2 license](https://learn.microsoft.com/en-us/azure/active-directory/identity-protection/overview-identity-protection). See [How To: Configure the Azure Multi-Factor Authentication registration policy](https://learn.microsoft.com/en-us/azure/active-directory/identity-protection/howto-identity-protection-configure-mfa-policy).

If you don't have a Microsoft Entra ID P2 license, you can still use a Conditional Access policy to require Azure Multi-Factor Authentication under specific circumstances. If your admins don't have Microsoft Entra ID P2 licenses, see [Tutorial: Secure user sign-in events with Azure Multi-Factor Authentication](https://learn.microsoft.com/en-us/azure/active-directory/authentication/tutorial-enable-azure-mfa).

### Enable combined security information registration

With combined security info registration, users can register once and get the benefits of both SSPR and Azure Multi-Factor Authentication \(MFA\).

Enable combined registration for all users and create a Conditional Access policy to require registration for the same users for which you enabled SSPR. You can use the same Office 365 group. Requiring registration enforces when and how users register for SSPR and Azure MFA.

SSPR and MFA are triggered only when conditions of a Conditional Access policy require the user to do them. You must create Conditional Access policies to enforce your security policies.

Note

For tenants created before August 2020, you must enable [combined security information registration](https://learn.microsoft.com/en-us/azure/active-directory/authentication/concept-registration-mfa-sspr-combined). For tenants created after August 2020, this is enabled by default.

For more information, see [Enable combined security information registration in Microsoft Entra ID](https://learn.microsoft.com/en-us/azure/active-directory/authentication/howto-registration-mfa-sspr-combined).

### Educate users

Before users can begin using SSPR or MFA, they need to register their security information. We recommend that you understand the user experience, then develop a plan to share awareness and educate your users as needed.

For more information, see the following end-user documentation:

- [Set up your Security info from a sign-in prompt](https://learn.microsoft.com/en-us/azure/active-directory/user-help/security-info-setup-signin)
- [Set up the Microsoft Authenticator app as your verification method](https://learn.microsoft.com/en-us/azure/active-directory/user-help/security-info-setup-auth-app)
- [Set up an authenticator app as your two-factor verification method](https://learn.microsoft.com/en-us/azure/active-directory/user-help/multi-factor-authentication-setup-auth-app)
- [Set up a mobile device as your two-factor verification method](https://learn.microsoft.com/en-us/azure/active-directory/user-help/multi-factor-authentication-setup-phone-number)
- [Set up an office phone as your two-factor verification method](https://learn.microsoft.com/en-us/azure/active-directory/user-help/multi-factor-authentication-setup-office-phone)
- [What is the Additional verification page?](https://learn.microsoft.com/en-us/azure/active-directory/user-help/multi-factor-authentication-end-user-first-time)

Microsoft provides end-user communication templates for both [MFA](https://aka.ms/mfatemplates) and [SSPR](https://aka.ms/ssprtemplates). You can modify these templates to help educate your users. We also provide deployment plans for various authentication methods. See [Deploy authentication](https://learn.microsoft.com/en-us/azure/active-directory/fundamentals/active-directory-deployment-plans).

### Install the Microsoft Authenticator app

Users who will be using the Microsoft Authenticator app for SSPR or MFA must install the latest version of the Microsoft Authenticator app.

- **Google Android**. On your Android device, go to Google Play to [download and install the Microsoft Authenticator app](https://app.adjust.com/e3rxkc_7lfdtm?fallback=https:%2F%2Fplay.google.com%2Fstore%2Fapps%2Fdetails%3Fid%3Dcom.azure.authenticator).
- **Apple iOS**. On your Apple iOS device, go to the App Store to [download and install the Microsoft Authenticator app](https://app.adjust.com/e3rxkc_7lfdtm?fallback=https:%2F%2Fitunes.apple.com%2Fus%2Fapp%2Fmicrosoft-authenticator%2Fid983156458).

If not currently on their mobile device, users can still get the Microsoft Authenticator app by sending themselves a download link from the [Microsoft Authenticator page](https://www.microsoft.com/account/authenticator).

## Microsoft Entra Password Protection

Despite your attempts at providing users with [guidance on how to choose passwords](https://www.microsoft.com/research/publication/password-guidance), weak or insecure passwords often occur. It's not uncommon for users to create passwords based on easy to remember terms such as the school name, a team mascot, a popular teacher's name, and so on.

Microsoft Entra Password Protection includes by default [global banned password lists](https://learn.microsoft.com/en-us/azure/active-directory/authentication/concept-password-ban-bad). These lists are automatically applied to all users to detect and block passwords that are susceptible to password spray attacks. To support your own security needs, you can define your own entries in a [custom banned password list](https://learn.microsoft.com/en-us/azure/active-directory/authentication/concept-password-ban-bad). When users change or reset their passwords, these banned password lists are checked to enforce the use of stronger passwords.

[Smart Lockout](https://learn.microsoft.com/en-us/azure/active-directory/authentication/howto-password-smart-lockout) also helps protect you from bad actors who use brute force methods to guess your users’ passwords. By default, smart lockout locks the account from sign-in attempts for one minute after 10 failed attempts. The account locks again after each failed sign-in attempt, for one minute at first and longer in subsequent attempts. Smart lockout is always on for all Microsoft Entra customers. The default settings offer a balance of security and usability. Customization of the smart lockout settings, with values specific to your organization, requires Microsoft Entra ID P1 or higher licenses for your users.

## Security reports

To limit your exposure to potential threats, [use the reporting capabilities that are available in Microsoft Entra ID](https://learn.microsoft.com/en-us/azure/active-directory/reports-monitoring/plan-monitoring-and-reporting). Microsoft Entra ID supports audit log and sign-in reports, security reports around risk detections, and reports to help you understand how authentication methods for Azure MFA and SSPR are working in your organization.

### Identity Protection

Microsoft Entra ID has many capabilities that automatically identify and generate alerts to remove the latency between the detection and response to attacks. To take full advantage of these capabilities, we recommend using [Microsoft Entra ID Protection](https://learn.microsoft.com/en-us/azure/active-directory/identity-protection/overview-identity-protection). This feature requires an [Microsoft Entra ID P2 license](https://learn.microsoft.com/en-us/azure/active-directory/identity-protection/overview-identity-protection). At a minimum, we recommend using Identity Protection for all admins.

There are three key reports that administrators use for investigations in Identity Protection:

- **Risky users report**. User risk indicates the likelihood a user's identity is compromised and is calculated based on [user risk detections](https://learn.microsoft.com/en-us/azure/active-directory/identity-protection/overview) for that identity. A user risk policy is a Conditional Access policy that evaluates the risk level to a specific user or group. Based on Low, Medium, and High risk-levels, a policy can be configured to block access or require a secure password change using multifactor authentication.
- **Risky sign-ins report**. Sign-in risk is the likelihood someone other than the account owner is attempting to sign on using the identity. A [sign-in risk policy](https://learn.microsoft.com/en-us/azure/active-directory/identity-protection/overview) is a Conditional Access policy that evaluates the risk level to a specific user or group. Based on the risk level \(high/medium/low\), a policy can be configured to block access or force multifactor authentication. Make sure you force multifactor authentication on Medium or above risk sign-ins.
- **Risk detections report**. Enables administrators to identify and remediate the following types of risk detections:

  - Atypical travel
  - Anonymous IP address
  - Unfamiliar sign-in properties
  - Malware linked IP address
  - Leaked credentials
  - Microsoft Entra threat intelligence

The following resource can help you operationalize your risk management strategies.

- [Plan monitoring and reporting](https://learn.microsoft.com/en-us/azure/active-directory/reports-monitoring/plan-monitoring-and-reporting)
- [How to investigate risk](https://learn.microsoft.com/en-us/azure/active-directory/identity-protection/howto-identity-protection-investigate-risk)
- [How to remediate risks and unblock users](https://learn.microsoft.com/en-us/azure/active-directory/identity-protection/howto-identity-protection-remediate-unblock)
- [Using the Graph API with identity protection](https://learn.microsoft.com/en-us/azure/active-directory/identity-protection/howto-identity-protection-graph-api)

Microsoft [maintains the information from Identity Protection reports for a limited time](https://learn.microsoft.com/en-us/azure/active-directory/reports-monitoring/reference-reports-data-retention). We recommend that you regularly export and archive it in other tools for further investigation and correlation. The Microsoft Graph APIs allow you to collect this data for further processing in tools such as your Security and Information Event Management \(SIEM\) solution. To learn how to implement these reports, see [Get started with Microsoft Entra ID Protection and Microsoft Graph](https://learn.microsoft.com/en-us/azure/active-directory/identity-protection/howto-identity-protection-graph-api).

### Audit logs and sign-in reports

The [audit logs report](https://learn.microsoft.com/en-us/azure/active-directory/reports-monitoring/howto-find-activity-reports) consolidates the following reports:

- Audit report
- Password reset activity
- Password reset registration activity
- Self-service groups activity
- Office365 Group Name Changes
- Account provisioning activity
- Password rollover status
- Account provisioning errors

### Authentication methods usage & insights

Microsoft Entra ID provides reports you can use to ensure users are registered for MFA and SSPR. Users who haven't registered may need to be educated on the process.

The authentication methods [Usage & Insights report](https://learn.microsoft.com/en-us/azure/active-directory/authentication/howto-authentication-methods-usage-insights) includes information about MFA and SSPR usage and gives you insights into how each is working in your organization. Having access to sign-in activity \(and audits and risk detections\) for Microsoft Entra ID is crucial for troubleshooting, usage analytics, and forensic investigations.

## Recommendations

We recommend that teachers, administrators, and IT staff use one of the passwordless authentication methods where possible. When you must use passwords, refer to [Microsoft’s Password Guidance](https://www.microsoft.com/research/wp-content/uploads/2016/06/Microsoft_Password_Guidance-1.pdf).

### Authentication methods

The following table summarizes the account types and our recommendations for all three types of authentication:

| Account type | Sign-in | SSPR | Azure MFA |
| --- | --- | --- | --- |
| Students \(elementary school\) | Password |  |  |
| Students \(middle school\) | Password |  |  |
| Students \(high school\) | Password or PIN  <br>Authenticator app if smart phones available | Student’s personal e-mail  <br>SMS  <br>Voice call |  |
| Students \(university\) | Password or PIN  <br>Authenticator app if smart phones available | Authenticator App  <br>SMS  <br>Personal e-mail | Authenticator app  <br>SMS  <br>Phone |
| Teachers | Windows Hello for Business \(PIN or Biometric\)  <br>FIDO 2 security key | •Authenticator App  <br>SMS  <br>Personal e-mail | Authenticator app  <br>SMS  <br>Phone |
| IT staff | Passwordless \(PIN, Biometric, FIDO 2 security key\) | Authenticator App  <br>SMS  <br>Personal e-mail | Authenticator app  <br>SMS  <br>Phone |
| Parents | Password \(Azure AD B2C\) | Authenticator App  <br>SMS  <br>Voice call  <br>Personal e-mail | Authenticator app  <br>SMS  <br>Phone |

### Credential Distribution

We recommend distributing authentication to primary and middle-school students using one of the following methods:

- Parent’s e-mail
- Parents mobile or landline phone
- Student’s personal email \(if it exists\)
- A printed copy of student’s temporary password delivered to teachers
- Post password to the student’s registered address

For educators, and IT admins, other staff, and high school or university students use one of the following methods:

- E-mail the temporary password to the personal e-mail address
- Send temporary password via SMS
- Printed copy of the temporary password

### Password security recommendations

IT admins should always

- Force expiration of initial or first-time passwords
- Implement [automated notification](https://learn.microsoft.com/en-us/azure/active-directory/authentication/tutorial-enable-sspr) of password change or reset

Additionally, provide all users with the following password security recommendations:

- Don’t write down or store your password in an insecure manner.
- Don’t reuse passwords – maintain password history.
- Don’t share your password with anyone.
- Use a passphrase instead of password.
- Change your password if/when you suspect your account has been compromised.
- Reset a provided password before the first use.

## Challenges and mitigations

Managing credentials can be challenging. This section describes features in Microsoft Entra ID that can help you mitigate the most common challenges.

### Updating user information

Administrators often manage user details: devices, security information, and passwords for each user. Manually updating this information is tedious and time-consuming.

To address this challenge, administrators should require users to use [My Account](https://myaccount.microsoft.com/). My Account is a self-service portal that enables end users to:

- Set up self-service password reset
- Configure two-factor authentication
- Change a password
- Disable a device if it's lost or stolen

### Maintaining group subscriptions

Students and faculty members often find themselves needing access to groups for access or communication purposes. The sheer number of groups and the frequency with which user needs change in educational institutions can make group management a daunting task for administrators.

In Microsoft 365 EDU, each group created from School Data Sync is automatically added to a school Administrative Unit to facilitate delegated and scoped administration for the groups in that school.

For delegation and management of individual groups, there are two additional options.

[Delegated group management](https://learn.microsoft.com/en-us/azure/active-directory/users-groups-roles/groups-self-service-management) enables admins to delegate management of group membership to a business owner. For example, if your school has an app that only students in a specific department should access, you typically add users to a group and assign the group access. You can then delegate membership management responsibilities to an employee in that department. The department will then manage membership in the group, which provides access to the application. In an academic setting, we recommend this over self-service group management.

[Self-service group management](https://learn.microsoft.com/en-us/azure/active-directory/users-groups-roles/groups-self-service-management) enables every user, including students, to create and manage their own security groups or Microsoft 365 groups in Microsoft Entra ID. The owner of the group can approve or deny membership requests and can delegate control of group membership. Thoroughly evaluate if enabling students to create groups is a desired state for your organization.

Note

Delegated group management and self-service group management features are available only with Microsoft 365 groups and Microsoft Entra security groups. They aren't available for mail-enabled security groups or distribution lists.

### Too many passwords to remember

Students and staff access multiple applications to complete their school work, which may require them to remember several unique passwords. Microsoft offers several mitigations.

We recommend enabling [Microsoft Entra single sign-on \(SSO\)](https://learn.microsoft.com/en-us/azure/active-directory/manage-apps/what-is-single-sign-on) with all compatible applications so that users can access all resources using their organizational credentials.

Windows 10 devices that are [Microsoft Entra joined](https://learn.microsoft.com/en-us/azure/active-directory/devices/plan-device-deployment) or [Microsoft Entra hybrid joined](https://learn.microsoft.com/en-us/azure/active-directory/devices/plan-device-deployment) will seamlessly access applications that are SSO enabled, provided the signed in user has access.

If your organization is hybrid and has computers running versions of Windows 8 or earlier, you can also implement [seamless single sign-on](https://learn.microsoft.com/en-us/azure/active-directory/hybrid/how-to-connect-sso). Seamless SSO avoids password prompts when teachers and staff are signing in from the organizational network.
