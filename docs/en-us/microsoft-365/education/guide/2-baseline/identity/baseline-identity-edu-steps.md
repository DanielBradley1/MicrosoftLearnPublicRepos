<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/education/guide/2-baseline/identity/baseline-identity-edu-steps -->
<!-- Sitemap-Last-Modified: 2026-04-28 -->

# Step 3: Education identity considerations steps

![](https://learn.microsoft.com/en-us/microsoft-365/education/guide/images/pillars/icon-identity.png)

![](https://learn.microsoft.com/en-us/microsoft-365/education/guide/images/sections/baselinesm.png)

## Roles and responsibilities

- IT Admin
- Identity Admin

## School Data Sync

[Microsoft School Data Sync \(SDS\)](https://learn.microsoft.com/en-us/microsoft-365/education/deploy/school-data-sync) is a free service designed for educational institutions. It automates the synchronization of user and roster data from Student Information Systems \(SIS\) with Microsoft 365. Here are some key features:

- Automated Data Synchronization: SDS reads rosters from your SIS and creates classes and groups for Microsoft Teams, Intune for Education, and other third-party applications.
- Integration with Microsoft 365: It helps manage educational organizations, users, classes, and roles within Microsoft 365, making it easier to set up online classrooms and manage educational resources.
- Support for Multiple Applications: SDS supports integration with various Microsoft services like Exchange Online, SharePoint Online, and OneNote Class Notebooks

## Duty of care

Microsoft Education emphasizes a strong [duty of care](https://www.microsoft.com/education/school-leaders/k-12-microsoft-education-transformation-framework), ensuring the safety and well-being of students and staff. Here are some key aspects:

- Safe and secure environments: Microsoft provides tools and resources to create secure online and onsite environments, using data analytics to optimize student outcomes and ensure safety.
- Equity and inclusion: The focus is on building inclusive educational environments that support all students, including students with functional needs.
- Professional development: Microsoft offers training and resources for educators to help them understand and fulfill their duty of care responsibilities.

### Cybersecurity

Attacks from the bad actors in education should be taken as high priority.

- **High cyberattack frequency:** Education institutions face an average of 2,507 cyberattack attempts per week, making them prime targets for malware, phishing, and IoT vulnerabilities.
- **Unique vulnerabilities:** The sector’s diverse user base, including young students and various staff, creates a highly fluid environment for cyberthreats.
- **QR code phishing:** QR codes are increasingly used for phishing attacks, exploiting the widespread use of personal and multiuser devices in educational settings.
- **Nation-state threats:** Universities conducting sensitive research are targeted by nation-state actors for intellectual property theft and espionage.
- **Security Measures:** Recommendations include implementing multifactor authentication, educating users on security hygiene, and using protective domain name services to block harmful websites.

## School IT admin

As a school IT admin using Microsoft Education tools, you have access to various resources and features to help manage your school’s technology infrastructure effectively. Here are some key aspects:

- **Microsoft 365 Admin Center**: This centralized hub allows you to manage users, devices, and applications across your school. You can perform common administrative tasks for services like Microsoft Entra ID, Teams, Exchange, and SharePoint.
- **Teams for Education**: This platform enables you to create collaborative classrooms, connect in professional learning communities, and communicate with students and guardians. IT admin resources are available to help you deploy, adopt, and manage Teams effectively.
- **Documentation and support**: Microsoft provides extensive documentation and support for IT admins, including guides on deploying and managing Microsoft 365 Education, ensuring a smooth transition to cloud-based solutions.

### School IT admin features

Education IT Admins in the Microsoft 365 Admin Center. Here are the key points:

- **New Experience for Education IT Admins:** The Microsoft 365 Admin Center is introducing a centralized place for delegated school-level IT admins to manage common administrative tasks across Microsoft 365 workloads like Microsoft Entra ID, Teams, Exchange, and SharePoint. This allows central IT teams and Global Administrators to focus on higher privileged tasks while delegating operational tasks to school-level admins.
- **M365 Admin Center UX for School IT:** The new streamlined experience allows school-level IT admins to manage users, groups, teams, sites, and objects associated with their schools. Tasks and permissions span Microsoft Entra ID, Teams, Exchange, and SharePoint, including managing users, attributes, resetting passwords, assigning licenses, managing groups, teams, group-connected sites, email, chat, external sharing, privacy, memberships, and access.
- **Administrative unit Support:** Administrative units provide a way to define the structure of an organization for delegated management. Microsoft extended administrative unit support to Teams, Microsoft Groups, and SharePoint sites, with new scoped administration roles: Teams Admin, SharePoint Admin, and Exchange Recipient Admin. These roles can be assigned to an admin over a particular administrative unit, granting them rights to manage only the objects within that administrative unit.
- **Delegated Password Reset with Password Writeback Support:** The Microsoft 365 Admin Center now supports delegated password reset on hybrid identities with password writeback enabled via MIcrosoft Entra ID Connect Sync. This allows education organizations to delegate password reset permissions to educators and school leaders.

## Information barriers in education

Information barriers \(IB\) tailored for Education, aimed at protecting students within Microsoft 365 tenants that contain multiple schools. Here are the key points:

- **Information barriers enhancements:**

  - Users in Multiple IB Segments: EDU institutions often have educators teaching across multiple schools. To support this, educators can now exist in multiple IB segments. Microsoft recommends creating an **All Staff IB** segment and policy to facilitate broad communication among educators while keeping students segmented to their respective schools. Support Scale of 5K+ IB Segments per Tenant: Microsoft supports up to 5,000 segments per tenant, allowing organizations with up to 1 million users to deploy Microsoft 365 in a single tenant model while protecting students and their data1.
  - Support for four IB Modes on Groups: New IB modes on Microsoft 365 Groups restrict people's ability to see and find other users in various experiences like adding users to a chat and communicating via Teams. The modes include:

    - Open mode: No restrictions on the group or its content.
    - ownerModerated mode: Group membership is restricted to users within the owner’s IB segments.
    - Implicit mode: Group membership is restricted to users within group members' IB segments.
    - Explicit mode: Group membership is restricted to users within the segments explicitly stamped on the group by IT admins.

- **Support IBs based on AU membership:**

  - For organizations using School Data Sync \(SDS\), Microsoft supports creating IB segments based on the membership of an Administrative Unit. This allows schools to mirror their administrative unit memberships with corresponding IB segments easily.

- **SDS provisioning of groups with IB mode ownerModerated:**

  - SDS begins creating all Class Groups with IB mode ownerModerated, allowing educators to add and invite users from their segments and share content with their segment members.

- **IBs + Address Book Policy in the same tenant:**

  - Information barriers will be fully supported by Teams and SharePoint, but Outlook and OWA don't yet support IBs. To mitigate directory exposure, Microsoft supports configuring and running both Information Barriers and Address Book Policy within the same tenant.

## Windows Hello for Business

Windows Hello for Business is a security feature designed to provide a more secure and convenient way to sign in to Windows devices and applications. Here are some key aspects:

- **Key Features** Biometric Authentication: Allows users to sign in using facial recognition, fingerprint, or iris scan, providing a password-less experience1.

  - PIN Sign-In: Users can also use a PIN, which is device-specific and not transmitted over the network, enhancing security.
  - Multifactor authentication \(MFA\): Combines biometrics or PIN with additional factors, making it more secure than traditional password-based authentication.

- **Security Benefits**

  - Resistance to Phishing and Breaches: By using public/private key or certificate-based authentication, it reduces the risk of credential theft. Enterprise-Grade Security: Provides robust security management for organizations, ensuring that only authorized users can access sensitive information.

- **Deployment Options** Cloud-Only: Suitable for organizations using Microsoft Entra ID.

  - Hybrid: Combines on-premises Active Directory with Microsoft Entra ID.
  - On-premises: For organizations that prefer to keep their infrastructure entirely on-premises.

## Next steps

Next, you're ready to consider identity applications.

[Next: Consider identity applications>](https://learn.microsoft.com/en-us/microsoft-365/education/guide/2-baseline/identity/baseline-identity-apps)
