<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/education/guide/2-baseline/identity/baseline-identity-ops -->
<!-- Sitemap-Last-Modified: 2026-04-28 -->

# Step 5: Set up access to operation services

![](https://learn.microsoft.com/en-us/microsoft-365/education/guide/images/pillars/icon-identity.png)

![](https://learn.microsoft.com/en-us/microsoft-365/education/guide/images/sections/baselinesm.png)

The interoperability of all services and the tenant are key to running smoothly. This article describes considerations when setting up access to services like SharePoint, OneDrive, Exchange Online and Teams, and the deployment of administrative units. These administrative units are the cloud version of on-premises organization units and help organize students and organization assets.

## Roles and responsibilities

- IT Admin
- Identity Admin

## Block Microsoft 365 group, SharePoint site, and Team Creation for students

Microsoft recommends blocking group creation for students in K12 organizations to prevent unmanaged and unmonitored communication and collaboration between students. To do this, you first create a group which specifies all of the users who should be able to create groups, like staff and faculty. Then you run the script in [this link.](https://learn.microsoft.com/en-us/microsoft-365/solutions/manage-creation-of-groups) Additionally, admins can also disable the ability for users to create sites by disabling the site creation setting in the SharePoint Online Admin Center. [Learn more about managing who can create Microsoft 365 groups.](https://learn.microsoft.com/en-us/microsoft-365/solutions/manage-creation-of-groups)

Note

Students often don't require this permission and limiting it to a subset of the teacher population is often adequate. Once this permission is blocked, IT admins can ensure their data and storage management strategy can be effective, and unexpected costs associated with storage are not unexpectedly impacted by new group, team, and site creation. This also ensures students are always operating in these communication and collaboration spaces with a teacher, staff member, or educator to ensure the proper oversight and protection, preventing a vector for cyber-bullying and other potential harms.

## Restrict access to Microsoft Entra Admin Center

Microsoft recommends enabling this setting for K12 and higher education tenants to prevent end users from accessing the Microsoft Entra Admin Center and more easily browsing the directory. This setting is found in the Microsoft Entra Admin Center under **Identity section > Users > User settings**. [Learn more.](https://aka.ms/AAhj9jy)

Note

Students and teachers typically will not require access to the Admin Center, and some educational institutions view broad directory access as a privacy violation. Restricting access to the Entra Admin Center is an easy way to adopt and maintain the principle of least privilege and meet student data privacy requirement in M365.

## Deploy administrative units

Administrative units are a special type of group or container in Microsoft 365 which can contain users, groups, or devices. Once configured, you can assign [specific administrator roles](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/admin-units-assign-roles#roles-that-can-be-assigned-with-administrative-unit-scope) to just the scope of the administrative unit, instead of providing the administrator permission for the entire tenant and directory. This is useful and recommended in medium and large K12 and higher education Microsoft 365 tenants to reduce the administrative permissions being granted and to ensure admins have only the permissions they need for the specific scope they need. This general concept and security principle is known as least privilege access. For K12, Microsoft recommends deploying an administrative unit for each school and grade level. For higher education, Microsoft recommends deploying an administrative unit for each course, campus, or college within a broader university system, at a minimum. [Learn more.](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/administrative-units)

Note

Administrative units have an ever-expanding set of use cases, allowing IT admins to protect and manage subsets of their often-large student and teacher populations and directories. They allow for granular permission distribution to teachers and allow for lower-level administrative tasks to be delegated down to the school level, instead of handling all administration and operations tasks at the central IT level. Many education organizations are facing budget constraints, so offloading some of this time and effort can be beneficial, allowing EDU IT Admin to focus on the larger and most strategic of administrative tasks.

## Deploy education attributes like user role, grade, and school ID

Microsoft recommends all education customers deploy core extension attributes to users which provide education context within the directory. The core attributes include user role, grade, and school ID. These attributes can be useful for tasks like deploying dynamic security groups and general Microsoft 365 operations management through PowerShell. So often, PowerShell cmdlets need to target subsets of users, and being able to filter cmdlets based on a predefined attribute can save admins plenty of time over the course of managing Microsoft 365 tenants. These attributes can be set directly through School Data Sync \(SDS\) or through MS Graph APIs.

Note

Taking this step helps education organizations build the security groups, admin units, Microsoft 365 groups, and teams they need to be successful. These attributes also help with running PowerShell based queries and reports, providing contextual user details to focus your query when running them against large organizations and directories, saving IT admins time and providing an easier path to manage the environment at scale.

## Next steps

Next, you're ready to review your lifecycle process.

[Next: Set up your identity lifecycle>](https://learn.microsoft.com/en-us/microsoft-365/education/guide/2-baseline/identity/baseline-identity-lifecycle)
