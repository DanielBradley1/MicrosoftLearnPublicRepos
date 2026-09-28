<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/education/guide/2-baseline/identity/baseline-identity-apps -->
<!-- Sitemap-Last-Modified: 2026-04-28 -->

# Step 4: Consider identity applications

![](https://learn.microsoft.com/en-us/microsoft-365/education/guide/images/pillars/icon-identity.png)

![](https://learn.microsoft.com/en-us/microsoft-365/education/guide/images/sections/baselinesm.png)

Education organizations need to consider applications that manage and control identities. Additionally, applications like parent contacts can allow better collaboration and integration with the organizations.

## Roles and responsibilities

- IT Admin
- Identity Admin

## Block user consent apps

With Microsoft Entra ID, you can require admins to provide all the apps that are available to their users in Microsoft 365. However, some apps can allow users to consent to permissions for an application to access a protected resource. In education, this type of consent can be highly problematic because it allows students to grant apps access to sensitive personal student data and information. Admins can disable user consent applications. Admins can also allow only verified applications and specify the permissions they allow consent for. Microsoft recommends K12 organizations disable user consent apps to better protect students. For higher education organizations, Microsoft recommends considering all options and choosing the option which best fits your needs and security profile. [Learn more about user and admin consent](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/user-admin-consent-overview). For step-by step instructions, see [How to disable user consent apps](https://learn.microsoft.com/en-us/entra/identity/enterprise-apps/configure-user-consent?pivots=portal).

Note

Education Institutions often have very strict policies on which apps can be enabled for teachers and students. Blocking the ability for teachers and students to grant consent in their own apps is key in managing against these common education requirements.

## Deploy parent contacts

Microsoft 365 allows IT admins to create and store parent contacts for [Teams-based communication and collaboration with teachers.](https://support.microsoft.com/topic/communicate-with-guardians-in-microsoft-teams-01471ecd-eb5d-4eda-9c5d-0064d672960e) Microsoft recommends deploying [parent contacts via School Data Sync](https://learn.microsoft.com/en-us/schooldatasync/parents-and-guardians-in-sds) to better connect educators and families. [Learn more](https://educationblog.microsoft.com/2023/01/strengthening-relationships-between-educators-and-families).

Note

Education institutions often require communications with parents. Enhancing your directory in Microsoft Entra ID can help. Whether you craft distribution groups, Microsoft 365 groups, communication sites, or any other Microsoft communication path using these contacts, the underlying directory is critical for communication success. The parent contacts are also completely hidden from being exposed to students through PowerShell or graph queries, so there should be no fear of mass data compromises and misuse.

## Next steps

Next, you're ready to go to operations.

[Next: Identity operations>](https://learn.microsoft.com/en-us/microsoft-365/education/guide/2-baseline/identity/baseline-identity-ops)
