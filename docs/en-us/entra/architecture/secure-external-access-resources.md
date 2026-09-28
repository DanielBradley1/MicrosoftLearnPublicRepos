<!-- Source: https://learn.microsoft.com/en-us/entra/architecture/secure-external-access-resources -->
<!-- Sitemap-Last-Modified: 2023-10-23 -->

# Plan a Microsoft Entra B2B collaboration deployment

Secure collaboration with your external partners ensures they have correct access to internal resources, and for the expected duration. Learn about governance practices to reduce security risks, meet compliance goals, and ensure accurate access.

## Governance benefits

Governed collaboration improves clarity of ownership of access, reduces exposure of sensitive resources, and enables you to attest to access policy.

- Manage external organizations, and their users who access resources
- Ensure access is correct, reviewed, and time bound
- Empower business owners to manage collaboration with delegation

## Collaboration methods

Traditionally, organizations use one of two methods to collaborate:

- Create locally managed credentials for external users, or
- Establish federations with partner identity providers \(IdP\)

Both methods have drawbacks. For more information, see the following table.

| Area of concern | Local credentials | Federation |
| --- | --- | --- |
| Security | - Access continues after external user terminates  <br>- UserType is Member by default, which grants too much default access | - No user-level visibility  <br>- Unknown partner security posture |
| Expense | - Password and multi-factor authentication \(MFA\) management  <br>- Onboarding process  <br>- Identity cleanup  <br>- Overhead of running a separate directory | Small partners can't afford the infrastructure, lack expertise, and might use consumer email |
| Complexity | Partner users manage more credentials | Complexity grows with each new partner, and increased for partners |

Microsoft Entra B2B integrates with other tools in Microsoft Entra ID, and Microsoft 365 services. Microsoft Entra B2B simplifies collaboration, reduces expense, and increases security.

## Microsoft Entra B2B benefits

- If the home identity is disabled or deleted, external users can't access resources
- User home IdP handles authentication and credential management
- Resource tenant controls guest-user access and authorization
- Collaborate with users who have an email address, but no infrastructure
- IT departments don't connect out-of-band to set up access or federation
- Guest user access is protected by the same security processes as internal users
- Clear end-user experience with no extra credentials required
- Users collaborate with partners without IT department involvement
- Guest default permissions in the Microsoft Entra directory aren't limited or highly restricted

## Next steps

- [Determine your security posture for external access](https://learn.microsoft.com/en-us/entra/architecture/1-secure-access-posture)
- [Discover the current state of external collaboration in your organization](https://learn.microsoft.com/en-us/entra/architecture/2-secure-access-current-state)
- [Create a security plan for external access](https://learn.microsoft.com/en-us/entra/architecture/3-secure-access-plan)
- [Securing external access with groups](https://learn.microsoft.com/en-us/entra/architecture/4-secure-access-groups)
- [Transition to governed collaboration with Microsoft Entra B2B collaboration](https://learn.microsoft.com/en-us/entra/architecture/5-secure-access-b2b)
- [Manage external access with entitlement management](https://learn.microsoft.com/en-us/entra/architecture/6-secure-access-entitlement-managment)
- [Secure access with Conditional Access policies](https://learn.microsoft.com/en-us/entra/architecture/7-secure-access-conditional-access)
- [Control access with sensitivity labels](https://learn.microsoft.com/en-us/entra/architecture/8-secure-access-sensitivity-labels)
- [Secure external access to Microsoft Teams, SharePoint, and OneDrive for Business](https://learn.microsoft.com/en-us/entra/architecture/9-secure-access-teams-sharepoint)
- [Convert local guest accounts](https://learn.microsoft.com/en-us/entra/architecture/10-secure-local-guest)
- [Onboard external users to Line-of-business applications](https://learn.microsoft.com/en-us/entra/architecture/11-onboard-external-user)
