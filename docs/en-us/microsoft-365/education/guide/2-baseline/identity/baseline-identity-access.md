<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/education/guide/2-baseline/identity/baseline-identity-access -->
<!-- Sitemap-Last-Modified: 2026-04-28 -->

# Step 8: Manage access controls

![](https://learn.microsoft.com/en-us/microsoft-365/education/guide/images/pillars/icon-identity.png)

![](https://learn.microsoft.com/en-us/microsoft-365/education/guide/images/sections/baselinesm.png)

This article helps define options for identity access configuration for external and guest users in education organizations.

## Roles and responsibilities

- IT Admin
- Identity Admin
- Security Admin

## Configure external and guest user access and invitation

Guests in your Microsoft 365 tenant inherit their permissions based on the **External Collaboration** settings set by the administrator. Microsoft recommends K12 organizations set the guest user access setting to most restrictive, unless you have a specific use case where guests require broader directory and group visibility and permissions. [Learn more.](https://learn.microsoft.com/en-us/entra/identity/users/users-restrict-guest-permissions#update-in-the-azure-portal)

Additionally, Microsoft recommends K12 organizations to limit guest invitations to only those users with specific admin roles to prevent students and unauthorized staff from inviting guests into the tenant and potentially exposing students and their data to others outside the organization and tenant boundary.

Finally, Microsoft recommends disabling guest user self-service signup and enabling external user leave settings so guests can remove themselves from the organization as appropriate. [Learn more.](https://learn.microsoft.com/en-us/entra/identity/users/users-restrict-guest-permissions)

Note

For education scenarios: Microsoft recommends the most restrictive guest access settings to ensure external users aren't inadvertently exposed to students, and vice versa, and limiting guest invites to just those admins and/or faculty that absolutely require the ability to invite guests. This approach helps prevent unwanted guests in the tenant with access to student data and the ability to communicate and collaborate with students.

## Next steps

Now that you completed the identity baseline section, you're ready for the applications section.

[Next: Applications>](https://learn.microsoft.com/en-us/microsoft-365/education/guide/0-start-baseline/start-applications)
