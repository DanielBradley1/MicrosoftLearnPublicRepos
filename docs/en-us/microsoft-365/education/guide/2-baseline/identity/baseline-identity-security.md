<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/education/guide/2-baseline/identity/baseline-identity-security -->
<!-- Sitemap-Last-Modified: 2026-04-28 -->

# Step 7: Configure security in identity

![](https://learn.microsoft.com/en-us/microsoft-365/education/guide/images/pillars/icon-identity.png)

![](https://learn.microsoft.com/en-us/microsoft-365/education/guide/images/sections/baselinesm.png)

Security around identity can be accomplished using various security defaults. These security defaults allow you to configure a wide variety of established security configurations. All security defaults and settings can be configured or not configured based on your requirements.

## Roles and responsibilities

- IT Admin
- Identity Admin
- Security Admin

## Security defaults

**Security defaults** is a single switch in Microsoft Entra ID which allows you to enable various security protections quickly and easily, like multifactor authentication \(MFA\) and blocking legacy authentication protocols. While this option might seem appealing, there are several considerations when deciding if this is right for your education organization. [Learn more.](https://learn.microsoft.com/en-us/entra/fundamentals/security-defaults)

### Microsoft recommendations vary based on user population

| Level | Notes |
| :--- | :--- |
| **Disable in K-12** | Since this setting requires MFA for all users, it isn't viable for K12 organizations where students might not have the phones needed to facilitate MFA setup and configuration. For K12, this setting should be disabled. |
| **Consider carefully in Higher Education** | It's possible some higher education organizations might be able to deploy this setting successfully if they can meet the phone requirement for the MFA configuration. If there are concerns over some students not having phones, Microsoft recommends leaving this setting in the disabled state. |
| **Enable in tenants with Faculty and Staff only** | While Microsoft recommends deploying Microsoft 365 tenants with both students and faulty co-located, some organizations have just deployed faculty and staff users, without students. For these tenants, Microsoft recommends enabling security defaults. |

## Block legacy authentication or Disable Basic Authentication in Exchange

Microsoft recommends all education customers block legacy authentication protocols and methods to better protect the organization and end users on Microsoft 365. This can be accomplished by enabling security defaults, but security defaults aren't viable for a variety of education customers. If you have the required Microsoft Entra ID premium licenses, you can easily disable legacy authentication using conditional access policy. If you're only running a free education tenant, you can still block some legacy authentication protocols through Exchange Online Authentication Policy. Before dropping legacy authentication, ensure your end users are only using client applications which support modern authentication. [Learn more.](https://learn.microsoft.com/en-us/exchange/clients-and-mobile-in-exchange-online/enable-or-disable-modern-authentication-in-exchange-online)

Note

For education scenarios: This recommendation is consistent with every other industry. Legacy authentication poses a security risk, and its use should be eliminated if not done so already. Not taking this step leaves students vulnerable to account compromise and organizational breaches.

## Deploy at least one more Global Admin account

When deploying Microsoft 365, you create your first Global Admin account upon the tenant’s creation. It's highly recommended to create at least one more Global Admin account, to ensure an issue with a single account can't prevent you from accessing and managing the tenant. [Learn more.](https://learn.microsoft.com/en-us/microsoft-365/business-premium/m365bp-protect-admin-accounts#create-other-admin-accounts)

Note

For education scenarios: This recommendation is consistent with every other industry. If you take the time to create a tenant, you must make sure you’re not going to lose the password and get locked out, leaving any provisioned students vulnerable to unrestricted access and applications without the ability to provide oversight and management.

## Only use admin accounts for admin purposes

Administrators should only use their admin accounts for administrative actions and tasks and only assign the roles to those administrative accounts. Admins should maintain completely separate work accounts with Microsoft 365 apps and licenses assigned to perform general work tasks like Teams meetings, email, etc. Admin accounts should remain unlicensed and configured with different passwords, ideally with MFA whenever possible. [Learn more.](https://learn.microsoft.com/en-us/microsoft-365/business-premium/m365bp-protect-admin-accounts#create-other-admin-accounts)

Note

For education scenarios: This long-standing best practice is often overlooked and ignored by education and other industry admins. Education organizations should adhere to this best practice despite it seeming slightly inconvenient to manage and use multiple accounts. If you don’t associate email and teams with the admin account, they can’t be easily compromised through phishing campaigns, in addition to several other underlying protections.

## Set passwords to never expire

Microsoft no longer recommends requiring users to continuously update their passwords, as most users select predictable updates closely related to each other. [Learn more.](https://learn.microsoft.com/en-us/microsoft-365/admin/add-users/set-password-to-never-expire)

Note

For education scenarios: Microsoft guidance at one time suggested regular password changes were beneficial. However, this guidance has since changed after some extensive research indicated password changes can do more harm than good. The reasons are most prevalent in education populations, so ensuring you don't require password changes will help reduce the volume of password reset requests and also help better protect the students and organization from account compromises.

## Enable teachers or school admins to reset student passwords

In addition to deploying administrative units, Microsoft recommends K12 organizations enable teachers and/or designated school level representatives with the password administrator role, scoped to school level admin units. This deployment ensures password reset requests can be handled at the school level instead of requiring escalation to the central IT team, savings them massive amounts of time each school year with student password reset requests. By scoping the password admin role to just the students of school admin units, this approach also ensures the staff enabled with these permissions can't reset passwords for other staff or for students outside of their immediate school.

Note

For education scenarios: Empowering your educators, at least one representative per school, allows the inevitable password reset requests to be handled locally in the classroom when they are needed most, as opposed to blocking logins during class and waiting for IT to address the ticket at their earliest convenience. The Microsoft 365 Admin Center was customized specifically for education to be streamlined and only shows the scoped user directory and password reset functionality, if you assign just this admin unit scoped role to your teachers.

## Disable MFA registration campaigns

With MFA not being viable for many education customers, admins in these organizations should disable registration campaigns that nudge all users to enable MFA. From the Microsoft Entra ID portal, admins can navigate to the **Identity Protection** menu, select **Registration campaign**, and set the state to disabled. [Learn More.](https://learn.microsoft.com/en-us/entra/identity/authentication/how-to-mfa-registration-campaign)

Note

For education scenarios: This step will prevent the confusion with MFA setup processes, which are often not viable for K12 organizations due to phone requirements and cost-prohibitive MFA methods like FIDO keys.

## Require and train all users on healthy passwords formation and use

Microsoft has enabled a new form of [Password Protection,](https://learn.microsoft.com/en-us/entra/identity/authentication/concept-password-ban-bad-combined-policy) which mandates users meet the [scoring algorithm](https://learn.microsoft.com/en-us/entra/identity/authentication/concept-password-ban-bad#how-are-passwords-evaluated) for passwords in Microsoft Entra ID. This method blocks the use of common words which are most often used and easily compromised by common password crackers. One of the best ways for younger students in K12 to meet these new requirements is to pick two short words \(three or four letters each\) and enter a short string of three special characters between them. For example, dog$&^run or fast#%\*tree. Each password may include these words which may be contained within the banned password list, but in a combined string these passwords score at least a 5 in the algorithm, which is the minimum required score for a healthy and usable password in Microsoft Entra ID. This approach and strategy can be explained, taught, and applied by students of all ages, in addition to faculty and staff, providing a much higher level of protection over legacy password policy with just basic length and complexity requirements. [Learn more.](https://learn.microsoft.com/en-us/entra/identity/authentication/concept-password-ban-bad)

Note

For education scenarios: Many of the password policies and practices require end user training to understand what passwords are acceptable and safe versus those which might be rejected. Training students and teachers on these best practices will help reduce the volume of password reset requests and help students and teachers from the frustration of having their password changes rejected by the system when they attempt to reset to a value not allowed within Microsoft Entra ID. Ultimately we want to keep students safe, so training them on strong authentication is an extremely important and beneficial life skill, applicable way beyond the classroom.

## Restrict end users from creating security groups

Microsoft recommends only allowing education IT administrators the permission to create security groups. Restricting this permission for end users ensures IT administrators maintain full control over the directory and all security groups are named and managed by the central IT organizations versus end users. This setting can be found in the Microsoft Entra Admin Center under **Identity** section **> Users > User settings**. [Learn more.](https://aka.ms/AAhj9jy)

Note

For education scenarios: Teachers and students usually don't have a need to create security groups, and keeping this permission restricted to admins will ensure consistent naming conventions and prevent unnecessary directory bloat.

## Deploy age groups and consent status

Microsoft recommends that all education customers in K12 environments deploy age group and consent status. These fields allow administrators to identify users who are minors within the tenant. Often, there are government regulations tied to the security and compliance of minors, and being able to identify users in this way is often the first step. Once deployed, these fields can be used to ensure minors and non-adults aren't accessing specific Microsoft applications. [Learn more.](https://techcommunity.microsoft.com/t5/education-blog/elevating-user-management-with-age-group-and-consent-provided/ba-p/4002713)

Note

For education scenarios: Age groups in education tenants are be used to configure default safety measures and protections for students of various ages, so setting these attributes is a fundamental step in the directory setup and maintenance for education IT Admins.

### Deploy security groups

Microsoft 365 contains various group types. Security groups are critical for configuring a variety of policies in bulk, where settings apply to all group members versus being set one by one on users. Building and maintaining a directory of security groups is critical. For K12 organizations, Microsoft recommends deploying a security group for each school, a security group for each grade, and a security group for each user role \(students, teachers, staff, etc.\). For higher education, it’s common to deploy security groups per campus and per user role, along with many others. Microsoft recommends planning the groups you need based on the policies you plan to implement. Often, the security groups mirror the administrative units, so it might be best to update each group type accordingly as membership needs to be changed. You can also create dynamic security groups to let Microsoft Entra ID keep memberships updated based on user attributes. [Learn more.](https://learn.microsoft.com/en-us/microsoft-365/admin/email/create-edit-or-delete-a-security-group)

Note

For education scenarios: Microsoft recommends creating and maintaining Microsoft Entra ID security groups split by school, grade level, and user role. SDS can assist in security group provisioning and help maintain memberships are they change. You can also leverage dynamic groups to ensure memberships are maintained over time. For example, students of Contoso High School and teachers of Contoso High School, students of Grade 9 and teachers of Grade 9, all teachers and all students, etc.

## Next steps

Next, you're ready to manage access controls.

[Next: Identity Access Controls>](https://learn.microsoft.com/en-us/microsoft-365/education/guide/2-baseline/identity/baseline-identity-access)
