<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/authenticationmethods-usage-insights-overview?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-08-02 -->

# Working with the authentication methods usage report API

Namespace: microsoft.graph

Authentication methods activity reports provides information on the registration and usage of [authentication methods](https://learn.microsoft.com/en-us/graph/api/resources/authenticationmethods-overview?view=graph-rest-1.0) in your tenant.

These reports provide information such as:

- How many users are registered for each authentication method
- How many users are registered for features such as multifactor authentication \(MFA\), Self-Service Password Reset \(SSPR\), and passwordless authentication.
- The failure rates of each authentication method

These reports are available on the Microsoft Entra portal through **Protection** tab group > **Authentication methods** tab > **Activity** tab under the *Monitoring* tab group.

## Licenses

A Microsoft Entra ID P1 or P2 license is required to access authentication methods usage and insights reports. Microsoft Entra multifactor authentication and self-service password reset \(SSPR\) licensing information can be found on the [Microsoft Entra pricing site](https://www.microsoft.com/security/business/microsoft-entra-pricing).

## Available reports

The following reports are available through Microsoft Graph:

- Per-user report of the status of their authentication methods including the default methods, whether registered for MFA, SSPR, and a passwordless authentication method, and so on. For more information, see the [userRegistrationDetails resource type](https://learn.microsoft.com/en-us/graph/api/resources/userregistrationdetails?view=graph-rest-1.0).
- Count of users registered, enabled, and capable of using MFA, SSPR, and passwordless authentication. For more information, see the [usersRegisteredByFeature resource type](https://learn.microsoft.com/en-us/graph/api/resources/userregistrationfeaturesummary?view=graph-rest-1.0).
- Raw count of users registered for email, password, and phone authentication methods. For more information, see the [usersRegisteredByMethod resource type](https://learn.microsoft.com/en-us/graph/api/resources/userregistrationmethodsummary?view=graph-rest-1.0).

The following reports are available on the `beta` endpoint only:

- Users registered and capable of self-service password reset \(SSPR\) and Azure multifactor authentication \(MFA\). For more information, see the [credentialUserRegistrationCount resource type](https://learn.microsoft.com/en-us/graph/api/resources/credentialuserregistrationcount).
- SSPR usage activity. For more information, see the [userCredentialUsageDetails resource type](https://learn.microsoft.com/en-us/graph/api/resources/usercredentialusagedetails).
- Tenant-level summary of user SSPR activity, including failure and successes. For more information, see the [credentialUsageSummary resource type](https://learn.microsoft.com/en-us/graph/api/resources/credentialusagesummary).

## Related content

- [Microsoft Entra authentication methods activity](https://learn.microsoft.com/en-us/entra/identity/authentication/howto-authentication-methods-activity)
