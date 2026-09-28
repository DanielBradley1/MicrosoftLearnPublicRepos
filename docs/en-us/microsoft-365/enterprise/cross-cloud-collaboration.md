<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/enterprise/cross-cloud-collaboration?view=o365-worldwide -->
<!-- Sitemap-Last-Modified: 2026-05-07 -->

# Cross-cloud collaboration with Microsoft 365

## Addressing Challenges, Enhancing Collaboration

In the current multicloud environment, organizations encounter significant challenges in ensuring secure and convenient collaboration across diverse sovereign and commercial clouds. Microsoft's Cross-Cloud B2B \(CCB2B\) solution, enhanced by Microsoft Entra ID, effectively addresses these challenges by offering a comprehensive identity management framework. This framework ensures secure guest access, enforces conditional access policies, and integrates with applications such as Teams, SharePoint, and Power BI. This article delves into the critical features, implementation procedures, and best practices for utilizing CCB2B, enabling organizations to achieve secure, compliant, and efficient cross-cloud collaboration.

Note

The multicloud environment refers to the clouds that are operated by Microsoft or its partners, and the CCB2B only supports collaboration across those Microsoft clouds.

## Introduction

In the ever-evolving digital landscape, organizations increasingly adopt multicloud strategies to optimize their operations. As of 2025, Microsoft \(or partners\) operates or has plans to operate the following Microsoft 365 clouds:

- Commercial cloud – serving most customers world-wide
- GCC, GCC High \(GCCH\), DoD clouds – serving US Government
- 21Vianet cloud – serving China market
- Bleu cloud – serving France market \(target launch mid 2026\)
- Delos cloud – serving Germany market \(target launch end of 2026\)

While Microsoft offers various cloud options, most customers would naturally prefer to operate within the Commercial cloud. However, some organizations are often required to use specific sovereign cloud instances—such as those sovereign cloud instances in France, Germany, China, or for US Government workloads—to meet regulatory and compliance mandates like iTAR or local data sovereignty laws. These requirements mean that customers may not always have the flexibility to choose their cloud environment freely, and frequently, parts of their organization are placed in separate clouds to comply with these regulations. However, this diversity also brings challenges related to cloud boundaries, data sovereignty, compliance/security. Ensuring secure and convenient collaboration across sovereign and global clouds is crucial for organizations to protect sensitive data, meet regulatory requirements, and foster innovation through efficient teamwork.

This article is primarily aimed at IT managers, CIOs, and others seeking cross-cloud solutions to streamline their employees' collaboration user experience. An FAQ section is included at the end for customer self-serve.

## Problem Statement

Note

Cross-Cloud collaboration refers to interoperability and interaction between business entities operating on different clouds. It ensures that users from various organizations can securely access and share resources, applications, and data across sovereign and global cloud environments. The goal is to enable efficient and secure cooperation while making it possible to adhere to regional compliance regulations.

Microsoft's customers are distributed around the world; to empower our customers running business in global markets, Microsoft commits to providing secure & compliant products to address regulation & compliance challenges in different countries/regions, and therefore Microsoft operates several cloud instances in different countries/regions to meet these dynamic requirements. In each cloud, Microsoft offers products like Microsoft 365 and Azure, and each cloud instance is intended to meet different customer needs.

These cloud instances are comprised of the SaaS, PaaS, and IaaS stacks and include critical elements such as identity, security, and commerce. Nothing is shared across these cloud instances and in some cases like GCCH and DoD, they were designed as secure enclaves with more rigorous compliance requirements and in some cases functionality that differs from the core commercial cloud. These different cloud instances help customers to meet various regulatory requirements that can't be met in our commercial cloud. However, there are several occasions where customers may need to establish a compliant way to collaborate across clouds, including but not limited to the following scenarios:

1. **Employee collaboration within a Multi-National-Corporation \(MNC\):** some companies have offices in different countries/regions, and due to industry and\(or\) local regulation requirements, their employees are separated into different clouds. But their daily work sometimes requires collaboration across different clouds.
2. **Global acquisition:** different companies may adopt different clouds based on their best judgment when the company was founded. However, when a company acquires another one who adopted different clouds, if they don't migrate employees to the same cloud, their employees may have the need to collaborate across clouds as part of their colleagues are in other clouds.
3. **Collaboration with partners and vendors:** Many companies choose a specific cloud for themselves based on their individual requirements but still must have the ability to collaborate with partners, vendors and/or Government agencies. This pattern includes government agencies who need the ability to securely interact with contractors and suppliers who are in different clouds.
4. **Enclave Employees \(Customers with ITAR-regulated divisions\):** These groups are required to maintain all project data in the enclave \(GCCH\). They may participate in other applications and communications with their corporate colleagues in commercial.

## Practical Collaboration Scenarios

In this section, we first briefly introduce how we could use different Cross-cloud features to fulfill collaboration scenarios in our daily work. In later sections, we dive deep into Cross-cloud solutions from a workload & feature perspective to include detailed configuration processes.

### Ad-hoc meeting scenarios

**Personas:**

- **Alice:** Sales representative at Contoso selling electronic products who is in the Microsoft Commercial cloud
- **Bob:** Supply chain manager at Fabricam who is in the 21Vianet cloud environment

**Objective:** Alice has been connecting with Bob via emails, after several rounds of email exchange, since Fabricam is a new customer to Contoso, Alice wants to set up a meeting with Bob to provide a comprehensive introduction & some live demos about Contoso's product.

**Solution:** Alice chooses to use Teams Cross-cloud Anonymous meeting \(CCA\) to address the collaboration with Bob. This decision is because the conversation doesn't involve any confidential content and CCA doesn't require administrators from the two tenants to make any specific configuration changes \(by default it's on.\) Hosting a Cross-cloud Anonymous meeting would be the most convenient way without breaking any security guidelines.

### Ad-hoc chat scenarios

**Personas:**

- **Alice:** Sales representative at Contoso selling electronic products who is in the Microsoft Commercial cloud
- **Bob:** Supply chain manager at Fabricam who is in the 21Vianet cloud environment

**Objective:** Bob receives an urgent update from the team that Contoso is offering a limited-time discount on the product that Bob is considering. Knowing that time is of the essence, Bob wants to talk with Alice immediately.

**Solution:** Without worrying about cross-cloud restrictions or waiting for IT admins to configure permissions, Bob simply opens Microsoft Teams, searches for Alice's contact, and starts a chat. This scenario is empowered by the Teams External Access chat feature, which doesn't require an admin to set up **other** configs \(by default on\), so it works out-of-the-box, allowing users in different cloud environments to connect immediately. It ensures Business agility, as Alice and Bob can collaborate without delays, leading to quicker decision-making and improved efficiency. The chat history generated during the Teams External Access chat session is stored in both user's tenants.

### Confidential/Compliant meeting scenarios

**Personas:**

- **Alice:** Sales representative at Contoso selling electronic products who is in the Microsoft Commercial cloud
- **Bob:** Supply chain manager at Fabricam who is in the 21Vianet cloud environment

**Objective:** Alice is finalizing a high-value electronics supply deal with Bob. Given the sensitivity of pricing details, contract terms, and proprietary product specifications, both parties need to ensure that their discussion remains secure and that only verified participants can attend the meeting.

**Solution:** To maintain security and prevent unauthorized access, Alice and Bob decide to use the Microsoft Teams Cross-cloud Authenticated Meeting \(also known as CCM\) feature. This feature ensures that all meeting participants are verified and authenticated before joining, reducing the risk of data leaks or security breaches. Since this type of meeting requires tenant admins from both Contoso and Fabricam to configure authentication settings, Alice reaches out to Contoso's IT admin, and Bob does the same with Fabricam's IT team. Once the necessary configurations are in place, Alice schedules the meeting and invites Bob. When Bob joins, the participant's identity is verified against the organization's authentication system, ensuring that only authorized Fabricam employees can access the meeting. This added security allows Alice to confidently share confidential pricing models and product roadmap without worrying about unauthorized access.

By using Teams Cross-cloud Authenticated Meeting, Alice and Bob achieve:

- Verified identities for meeting participants ensuring only trusted participants join.
- Secure collaboration on sensitive business information.
- Compliance with company policies on secure communications.

Though it required some initial admin configuration, the long-term benefit of a more secure and trusted communication channel makes it the ideal choice for sensitive business discussions.

### Teams long-term collaboration scenarios

**Personas:**

- **Peggy:** Sales representative at Contoso \(US\) who is in the Microsoft Commercial cloud
- **Victor:** Sales representative at Contoso \(China\) who is in the 21Vianet cloud environment

**Objective:** Peggy, a sales representative at Contoso \(US\), and Victor, a sales representative at Contoso \(China\), are working together on a global client deal that requires close collaboration. They need to jointly manage sales proposals, coordinate regional pricing strategies, and share client documents. It's also critical that they have a convenient and secure way to collaborate frequently.

**Solution:** To facilitate rich and secure cross-cloud collaboration, Peggy and Victor decide to use the Microsoft Teams Cross-cloud Guest Access \(also known as CCGA\) feature. This feature allows them to work together as if they were in the "same tenant", giving them access to:

- Teams channel collaboration – They can have discussions within a Teams channel and edit/share sales proposals and pricing documents within Teams.
- 1:1 and group chats/calls – They can quickly discuss updates and resolve issues in real time.
- Meeting collaboration – During the meeting, "Guest" can send messages to others in the meeting chat session, and they can revisit the chat history even after the meeting ends.

Since Cross-cloud Guest Access requires tenant admins from both Contoso \(US\) and Contoso \(China\) to configure guest access permissions, Peggy and Victor coordinate with their respective IT teams to enable the setup. Once configured, Victor is added as a guest in Peggy's Teams environment, allowing them to collaborate smoothly. By choosing Teams Cross-cloud Guest Access, Peggy and Victor gain:

- An authenticated collaboration experience – access to Teams features including chat, channels, file sharing, and meetings.
- Stronger security – ensuring that only authorized users access sensitive sales data. In this example collaboration is occurring within Peggy's tenant ensuring that Contoso \(US\) compliance requirements are maintained always.
- Improved productivity – with direct access to Teams channels, files, 1:1 and 1: many communications.
- Data sovereignty – the Teams chat data generated by the Guest users is only stored in the resource tenant, it's not copied to the Guests' home tenant.

Though it required initial admin setup, the long-term efficiency and security benefits made it the ideal choice for their cross-regional collaboration.

### Sending emails & booking meetings scenarios

**Personas:**

- **Peggy:** Sales representative at Contoso \(US\) who is in the Microsoft Commercial cloud
- **Victor:** Sales representative at Contoso \(China\) who is in the 21Vianet cloud environment

**Objective:** Peggy and Victor frequently coordinate on joint sales opportunities and need a more efficient way to schedule meetings and communicate via email. However, since they are in separate cloud environments, Peggy finds it difficult to check Victor's availability when setting up meetings, and both struggle with manually entering each other's full email addresses when sending emails/setting up meetings. They need a more convenient way to schedule meetings efficiently and improve email communication across clouds.

**Solution:** To overcome these challenges, Peggy and Victor choose to enable Exchange Online \(EXO\) Free/Busy and Global Address List \(GAL\) for cross-cloud collaboration.

*Scenario 1: Efficient Meeting Scheduling with Free/Busy*

Peggy wants to schedule a strategy call with Victor but is unsure of his availability. Instead of waiting for email replies or manually coordinating time zones, Peggy simply opens Outlook's scheduling assistant. Thanks to the EXO Free/Busy feature, Peggy can instantly see Victor's availability—whether he's free, busy for a given time window.

Since tenant admins from both Contoso \(US\) and Contoso \(China\) enable cross-cloud Free/Busy sharing, Peggy can pick a time that works for both of them without back-and-forth emails, improving efficiency and ensuring faster decision-making.

*Scenario 2: Faster Email Communication with Global Address List \(GAL\)*

Later, Peggy needs to loop Victor into a client update email. Instead of manually typing the full email address, Peggy simply types "Victor" in the recipient field. Thanks to the GAL feature, Outlook automatically finds Victor's correct contact information, ensuring the correct email address is selected and reducing the risk of mistyping. By enabling EXO Free/Busy and GAL, Peggy and Victor achieve:

- Efficient meeting scheduling – No more delays in finding a suitable meeting time.
- Faster, error-free email communication – Avoids the risk of misaddressing emails.
- Improved productivity & collaboration – Less administrative overhead, more focus on sales.

Although tenant admin configuration was required, the enhanced user experience and time-saving benefits made these features the perfect choice for their cross-cloud collaboration.

### File collaboration scenarios

**Personas:**

- **Peggy:** Sales representative at Contoso \(US\) who is in the Microsoft Commercial cloud
- **Victor:** Sales representative at Contoso \(China\) who is in the 21Vianet cloud environment

**Objective:** Peggy and Victor are working together to plan an end-of-year offsite event to celebrate their team's achievements over the past year. They need to collaborate on a shared event planning document and store other materials, such as agendas and budget sheets, in a centralized location. Since they are in different cloud environments, they require a way to co-author documents and manage shared files efficiently.

**Solution:** To facilitate smooth collaboration, they choose to use Microsoft OneDrive for real-time document co-authoring and SharePoint Online for structured file sharing and organization \(via CCB2B solution, which requires specific configuration from tenant admins on both sides\).

*Scenario 1: Co-authoring the Event Planning Document in OneDrive*

Victor drafts the initial event planning document in OneDrive, outlining potential venues, catering options, and the event schedule. Instead of sending multiple versions via email, Victor shares the document link with Peggy, allowing Peggy to edit the file in real time. With OneDrive's co-authoring feature, both Peggy and Victor can simultaneously add notes, adjust schedules, and leave comments—ensuring a dynamic and efficient planning process. They can see each other's edits instantly, preventing miscommunication and version conflicts.

*Scenario 2: Uploading More Event Materials to SharePoint*

As the planning progresses, Victor needs to upload supporting files like vendor proposals, budget spreadsheets, and slogans/pictures. Victor stores these files in a SharePoint Online site, where both Victor and Peggy have access. With SharePoint's structured folder system and version control, they can keep all event-related documents organized and updated without worrying about data loss or outdated versions. Peggy can quickly review and update files, ensuring that the latest information is always available. By enabling OneDrive & SharePoint Online, Peggy and Victor gain:

- Convenient cross-cloud document collaboration – No email attachments needed.
- Real-time co-authoring – Faster decision-making and improved accuracy.
- Centralized file storage in SharePoint – Easy access to all planning materials.

Although tenant admins had to configure cross-cloud file sharing, the improved workflow and secure collaboration made it the ideal solution for planning the event.

### Preparing business review scenarios

**Personas:**

- **John:** Business lead at Contoso \(US\) who is in the Microsoft Commercial cloud
- **Victor:** Sales representative at Contoso \(China\) who is in the 21Vianet cloud environment

**Objective:** John and Victor are preparing for an upcoming business review where they need to present and analyze key sales data using a Power BI dashboard. John creates a dashboard with essential metrics and insights, which John needs to share with Victor so they can review the data together and finalize their presentation. Since they are in different cloud environments, they require a secure and convenient way to collaborate on Power BI.

**Solution:** To enable cross-cloud data collaboration John and Victor choose to use Power BI's cross-cloud sharing feature. John creates a Power BI dashboard that includes sales performance metrics, market trend analysis, and customer insights. Since Victor also needs to get the China market insights, John needs to share the live dashboard with him so they can review and refine the data together. Because Power BI cross-cloud sharing requires tenant admin configurations, both Contoso \(US\) and Contoso \(China\) IT teams enable the necessary settings. Once configured, Victor can securely access and interact with the dashboard. By using Power BI cross-tenant sharing, John and Victor gain:

- Secure access to shared reports across cloud environments.
- Real-time collaboration on data insights without exporting static reports.
- More engaging and data-driven business reviews with interactive dashboards.

## CCB2B – Entra ID level

### What is B2B

To accommodate the challenges mentioned in previous sections, Microsoft Entra ID introduced the **[B2B](https://learn.microsoft.com/en-us/entra/external-id/what-is-b2b)** \(Business-to-Business\) collaboration solution aiming to improve Cross-Tenant collaboration user experiences. The **B2B** solution allows users in your tenants to share the resources that are hosted in your tenants with someone who comes from another tenant, while maintaining control over your own corporate data. Microsoft Entra ID lets you invite external users as guests to your Microsoft Entra ID tenant. When you invite an external user, Microsoft Entra ID creates a guest account in your tenant. These guest accounts differ from regular Microsoft Entra ID user accounts in multiple ways:

- Guests don't have a password. To sign on, guests are automatically redirected to their home tenant or to the external identity provider \(IdP\) that they're invited from.
- The user principal name \(UPN\) of the guest account uses a prefix derived from the invitee's email address, combined with the tenant's initial domain—for example: prefix#EXT#@tenant.onmicrosoft.com.
- When you’re preparing the invitation, the guest can be invited as **External Guest role** or **External Member role.** These roles are described in more detail in later sections.

Microsoft Entra ID unblocks collaboration between users in your tenants and the following roles:

- **Your business partners** – who usually have their own tenants that are different from yours
- **Users belonging to your organization but separated into different tenants** – some customers adopt a multitenant organization architecture, which means they allocate accounts for their employees in different tenants, but those employees logically belong to the same organization. This tenant separation is usually the result of regulatory requirements or an acquisition.

![Diagram of B2B allows users to collaborate across tenants.](https://learn.microsoft.com/en-us/microsoft-365/enterprise/media/cross-cloud-whitepaper/figure-1-b2b-allows-users-to-collaborate-across-tenants.png?view=o365-worldwide)

*Figure 1: B2B allows users to collaborate across tenants*

### What is CCB2B

Based on B2B, the **Cross-Cloud B2B** solution \(also known as CCB2B\) was announced\([link](https://learn.microsoft.com/en-us/entra/external-id/cross-cloud-settings)\) aiming to address similar collaboration user scenarios but in Cross-cloud situations. With CCB2B as infrastructure, the Microsoft 365 workloads are now able to expand their features to support Cross-cloud scenarios. For example, The Teams **Cross-Cloud Guest Access** \(CCGA\) feature was developed based on Entra ID CCB2B solution, which allows users to be invited to other tenants as a Teams Guest across clouds so the user can have richer & more intuitive collaboration experiences.

![Diagram of CCB2B allows users to collaborate across clouds.](https://learn.microsoft.com/en-us/microsoft-365/enterprise/media/cross-cloud-whitepaper/figure-2-ccb2b-allows-users-to-collaborate-across-clouds.png?view=o365-worldwide)

*Figure 2: CCB2B allows users to collaborate across clouds*

Microsoft Entra ID is a pivotal component of the CCB2B solution. It provides a comprehensive identity management framework that facilitates secure guest access and conditional access policies tailored to an organization's specific needs. Since CCB2B integrates with applications like Teams, SharePoint, and Power BI, tenant admins can use Entra ID to ensure that users from different clouds can collaborate with internal teams without compromising security. This robust identity management solution addresses the complexities of cross-cloud interoperability, enabling organizations to extend their collaboration capabilities beyond traditional boundaries while maintaining stringent security standards.

### CCB2B hands-on

Important

The CCB2B solution isn’t enabled by default. When customers need to collaborate with others across clouds, tenant admins need to configure their Microsoft Entra ID settings to specifically enable the target clouds and the target Entra ID tenants, and such configuration is required in both tenants – both tenants must trust each other, otherwise configuring the CCB2B settings only in one tenant doesn't work.

The following sections briefly describe how tenant admins should configure CCB2B from an Entra ID perspective. For detailed information, visit this [link](https://learn.microsoft.com/en-us/entra/external-id/cross-cloud-settings), which contains a comprehensive guide from hands-on guidance to license requirements, from best practice to detailed instructions. We recommend you walk through the document & child links for a deeper understanding of the Cross-cloud setup process.

#### Cross-tenant access settings

To enable collaboration between two organizations in different Microsoft clouds, admins in each organization need to trust each other by completing the Cross-Tenant Access settings.

Note

Some configuration options may require other licensing. Visit [here](https://learn.microsoft.com/en-us/entra/external-id/cross-tenant-access-overview) for more info.

##### Step 1: Configure cloud settings to enable collaboration with the target cloud.

By default, your tenant isn't configured to allow collaboration across clouds, but you can enable the collaboration for the following cloud-pairs in the Entra ID admin portal \(a more comprehensive guide can be found [here](https://learn.microsoft.com/en-us/entra/external-id/cross-cloud-settings)\):

| Target/Source cloud | Microsoft Azure Commercial | Microsoft Azure Government | Microsoft Azure in China |
| --- | --- | --- | --- |
| Microsoft Azure Commercial | N/A \(covered by B2B\) | Supported | Supported |
| Microsoft Azure Government | Supported | N/A \(covered by B2B\) | Not Supported |
| Microsoft Azure in China | Supported | Not Supported | N/A \(covered by B2B\) |

Microsoft 365 organizations have one of several tenant types and are located in one of three Microsoft clouds:

| Microsoft Azure cloud environment | Microsoft 365 cloud environment |
| --- | --- |
| Microsoft Azure Commercial | Commercial, GCC |
| Microsoft Azure Government | GCC High, DoD |
| Microsoft Azure in China | China \(21Vianet\) |

1. Sign in to the [Microsoft Entra ID admin center](https://entra.microsoftonline.cn/) \(Note: The Entra ID portal endpoint is different for each cloud, so use the correct endpoint\).
2. Browse to **Identity** > **External Identities** > **Cross-tenant access settings**, then select **Microsoft cloud settings**.
3. Select the checkbox for the clouds you want to enable.

   ![Screenshot that shows Enable Cross-cloud trust settings.](https://learn.microsoft.com/en-us/microsoft-365/enterprise/media/cross-cloud-whitepaper/figure-3-enable-cross-cloud-trust-settings.png?view=o365-worldwide)

*Figure 3: Enable Cross-cloud trust settings*

##### Step 2: Configure target tenant ID

By default, your tenant isn't configured to collaborate with any external tenants even if you enable the target clouds from the previous step. To create a trust connection with other tenants, admins need to add the target tenant ID in the Entra ID admin portal \(a more comprehensive guide can be found here\):

1. Sign in to the Microsoft Entra ID admin center.
2. Browse to **Identity** > **External Identities** > **Cross-tenant access settings**, then select **Organizational settings**.
3. Select **Add organization** \(#1\). On the Add organization panel, input the tenant ID for the organization\(#2\). Don't forget to click **Add** \(#3\). Once done, the newly added tenant ID shows up on the left side \(#4\).

   ![Screenshot that shows Trust the other tenants.](https://learn.microsoft.com/en-us/microsoft-365/enterprise/media/cross-cloud-whitepaper/figure-4-trust-the-other-tenants.png?view=o365-worldwide)

*Figure 4: Trust the other tenants*

##### Step 3: Configure inbound and outbound settings

Once the above steps are completed, the CCB2B configuration process is done. However, tenant admins can apply specific settings for the target tenant to handle customized requirements \(a more comprehensive guide can be found [here](https://learn.microsoft.com/en-us/entra/external-id/external-collaboration-settings-configure) and [here](https://learn.microsoft.com/en-us/entra/external-id/cross-tenant-access-settings-b2b-collaboration#configure-default-settings)\).

- **Inbound access settings** – determines whether users from target tenant can be invited to your organization and added to your tenant as guests.
- **Outbound access settings** – determines whether your users can be invited to the target tenant for B2B collaboration and added to their directory as guests.

![Screenshot that shows Customize in/out bound as needed.](https://learn.microsoft.com/en-us/microsoft-365/enterprise/media/cross-cloud-whitepaper/figure-5-customize-in-out-bound-as-needed.png?view=o365-worldwide)

*Figure 5: Customize in/out bound as needed*

With the inbound & outbound settings, tenant admins can allow one-direction CCB2B setup – which means only allows users from one tenant to be invited to the other, however based on our observation, customers usually adopt bi-directional CCB2B setup for smooth collaboration.

#### External Collaboration settings

External collaboration settings in Microsoft Entra allow you to manage how users in your organization interact with external users through B2B collaboration. These settings let you control invitation permissions, domain access, and guest visibility within your directory. Detailed descriptions of each setting can be found at this [link](https://learn.microsoft.com/en-us/entra/external-id/external-collaboration-settings-configure). Key configuration options include:

- **Guest User Access Control:** Define what external guests can view in your directory. You can restrict access to group memberships or allow guests to see only their own profile information.
- **Invitation Permissions:** By default, all users, including external guests, can invite others for B2B collaboration. You can restrict this capability by disabling invitations globally or limiting it to specific roles.
- **Domain Restrictions:** Manage collaboration by specifying which domains are allowed or blocked for guest invitations. For more information, see [Allow or block domains](https://learn.microsoft.com/en-us/entra/external-id/allow-deny-list).

![Screenshot that shows External Collaboration settings.](https://learn.microsoft.com/en-us/microsoft-365/enterprise/media/cross-cloud-whitepaper/figure-6-external-collaboration-settings.png?view=o365-worldwide)

*Figure 6: External Collaboration settings*

#### CCB2B invitation

Once previous steps are done, tenant admins can invite external users via Entra ID Admin portal. For a comprehensive guide on invitation & redemption visit [Quick start: Add a guest user and send an invitation](https://learn.microsoft.com/en-us/entra/external-id/b2b-quickstart-add-guest-users-portal) and [B2B invitation email layout and language settings](https://learn.microsoft.com/en-us/entra/external-id/invitation-email-elements)

##### Step 1: Initiate the invitation

1. Sign in to the Microsoft Entra ID admin center.
2. Browse to **Users** > **All users** > **New user**, then select **Invite external user**.
3. Following the instructions to fill in the external user’s email address \(must have\) & other info such as Job title, Display name\(optional\) as needed.
4. To send out the invitation, click **Invite** in "Review + invite" step.

   ![Screenshot that shows External user invitation.](https://learn.microsoft.com/en-us/microsoft-365/enterprise/media/cross-cloud-whitepaper/figure-7-external-user-invitation.png?view=o365-worldwide)

*Figure 7: External user invitation*

5. Admins can check whether the external user accepts the invitation.

   ![Screenshot that shows B2B invitation status.](https://learn.microsoft.com/en-us/microsoft-365/enterprise/media/cross-cloud-whitepaper/figure-8-b2b-invitation-status.png?view=o365-worldwide)

*Figure 8: B2B invitation status*

##### Step 2: Redeem the invitation

1. The external user receives an email in their inbox regarding the CCB2B invitation
2. The external user is required to click on the invitation link in the email to redeem the invitation

   ![Screenshot that shows Accept the invitation.](https://learn.microsoft.com/en-us/microsoft-365/enterprise/media/cross-cloud-whitepaper/figure-9-accept-the-invitation.png?view=o365-worldwide)

   *Figure 9: Accept the invitation*
3. Once accepted. This external user becomes a CCB2B External Guest user in your tenant. They're able to access resources in your tenant & collaborate with users in your tenant by using their own account & credentials.
4. External users can defer the redemption until they try to access resources hosted in your tenant. In such cases, they still need to login using their own account & credentials when accessing resources, but the redemption page shows up first for user consent.

##### Step 3 \[Optional\]: CCB2B user types

By default, CCB2B invitation allows you to invite external users to your tenant as a **CCB2B External Guest** user, but it’s worth mentioning that Entra ID offers four user types in total, and among them **External Member** type might be needed for some scenarios. The following table describes B2B collaboration users based on how they authenticate \(internally or externally\) and their relationship to your organization \(guest or member\). For a comprehensive introduction of user properties & types, visit [Understand and manage the properties of B2B guest users](https://learn.microsoft.com/en-us/entra/external-id/user-properties)

|  | Guest | Member |
| --- | --- | --- |
| **External** | External Business partners  <br>  <br>Most users who are commonly considered external users or guests fall into this category. This B2B collaboration user has an account in an external Microsoft Entra organization or an external identity provider \(such as a social identity\), and they have guest-level permissions in the resource organization. The user object created in the resource Microsoft Entra directory has a UserType of Guest. | FTEs in your org, but in other tenants  <br>  <br>This B2B collaboration user has an account in an external Microsoft Entra organization or an external identity provider \(such as a social identity\) and member-level access to resources in your organization. This scenario is common in organizations consisting of multiple tenants, where users are considered part of the larger organization and need member-level access to resources in the organization’s other tenants. The user object created in the resource Microsoft Entra directory has a UserType of Member. |
| **Internal** | Before Microsoft Entra B2B collaboration was available, it was common to collaborate with distributors, suppliers, vendors, and others by setting up internal credentials for them and designating them as guests by setting the user object UserType to Guest. If you have internal guest users like these, you can invite them to use B2B collaboration instead so they can use their own credentials, allowing their external identity provider to manage authentication and their account lifecycle. | FTEs in your tenants  <br>  <br>These users are considered employees of your organization. The user authenticates internally via Microsoft Entra ID, and the user object created in the resource Microsoft Entra directory has a UserType of Member. |

While CCB2B External Member is a supported configuration by Entra, it isn't supported by Teams. External Member may also have other licensing requirements. Tradeoffs in support and functionality must be considered before implementing External Member.

#### \[Optional\] Cross tenant synchronization

Cross-tenant synchronization automates creating, updating, and deleting B2B collaboration users. These users continue to benefit from the security capabilities in Microsoft Entra ID, such as Microsoft Entra Conditional Access and cross-tenant access settings and can be governed through features such as Microsoft Entra entitlement management. But with Cross-tenant sync feature, it offers a better way to govern the lifecycle of users across clouds instead of manually inviting external users across tenants and clouds or relying on custom scripts to manage thousands of users. Cross-cloud synchronization enables organizations to save time and reduce risk by automatically provisioning users across tenants and clouds. Tenant admins can use this Cross-tenant sync feature to sync their users to different tenants as B2B External Member or B2B External Guest at scale! Here are the primary benefits of Cross-tenant synchronization:

- Automatically create B2B collaboration users within your organization and provide them with access to the applications they need, without creating and maintaining custom scripts.
- Improve the user experience and ensure that users can access resources, without receiving an invitation email and having to accept a consent prompt in each tenant.
- Automatically update users and remove them when they leave the organization

For the latest information, check the following resources:

- Introduction: [What is cross-tenant synchronization](https://learn.microsoft.com/en-us/entra/identity/multi-tenant-organizations/cross-tenant-synchronization-overview)
- Feature blog: [Streamline user management across Microsoft clouds](https://techcommunity.microsoft.com/blog/microsoft-entra-blog/streamline-user-management-across-microsoft-clouds/4422536)
- Limitations: for known issues check [here](https://learn.microsoft.com/en-us/entra/identity/app-provisioning/known-issues?pivots=cross-tenant-synchronization#cross-tenant-synchronization)

As of 2025 August, the Cross-tenant synchronization feature is now in public preview stage for Cross-cloud scenarios, which means tenant admins can sync users across different clouds, detailed instructions can be found here [Configure cross-tenant synchronization](https://learn.microsoft.com/en-us/entra/identity/multi-tenant-organizations/cross-tenant-synchronization-configure). And note that

- The Cross-cloud synchronization requires Microsoft Entra ID Governance or Microsoft Entra Suite license, see details [here](https://learn.microsoft.com/en-us/entra/identity/multi-tenant-organizations/cross-tenant-synchronization-overview#license-requirements).
- Only the specific cloud pairs are supported in the public preview stage, see details [here](https://learn.microsoft.com/en-us/entra/identity/multi-tenant-organizations/cross-tenant-synchronization-overview#clouds).

### Understand B2B & CCB2B from different perspectives

Note

There are a few topics related to CCB2B and sometimes it could be confusing to beginners. In this section, we walk through the following topics to clarify the relationship & differences between them:

- Entra ID supports B2B/CCB2B
- Microsoft 365/Power Platforms workloads support B2B/CCB2B

#### Entra ID perspective

Recognizing external users’ identity before allowing them to access your resources is critical in external collaboration scenarios. Entra ID as the infrastructure of such external collaboration provides a way to securely validate users’ identity, which allows external users to login/authenticate using the credentials of their home tenant account to access resources in your tenant, so that you don’t have to provision separate accounts for them in your tenant. The key difference between B2B & CCB2B on Entra ID level is that:

- **B2B** – the Entra ID B2B makes it possible for a tenant to recognize a user’s identity even if the user is from a different tenant, but the two tenants must be in the same cloud.
- **CCB2B** – comparing with Entra ID B2B, the Entra ID CCB2B offers a similar identity recognition ability but extends it to Cross-cloud scenarios. A tenant is able to recognize a user’s identity even if the user is from a different tenant, and the two tenants can be in different clouds

So, from the Entra ID perspective, the difference between Entra ID B2B and Entra ID CCB2B is whether the tenants are from the same cloud or not, and from an engineering perspective, CCB2B is built on top of B2B, it extends similar feature sets to Cross-cloud situations.

#### Microsoft 365 perspective

With the capability of recognizing a user’s identity powered by Entra ID B2B/CCB2B, Microsoft 365 workloads are then able to implement external collaboration based on their different business logic. The key difference between B2B & CCB2B on Microsoft 365 workloads level is that:

- **B2B** – based on Entra ID B2B capability, Microsoft 365 workloads can support external collaboration within the same cloud. For example, "Teams Guest Access" feature is built based on Entra ID B2B aiming to address the Cross-tenant chat/meeting scenarios; SharePoint achieves "File collaboration" scenarios based on Entra ID B2B aiming to address the Cross-tenant file sharing & Co-authoring requirements.
- **CCB2B** – given Entra ID CCB2B can recognize user’s identity across different clouds, with that power, Microsoft 365 workloads can further extend their Cross-tenant\(in-cloud\) feature sets to Cross-cloud scenarios. For example, Teams extended the "Guest Access" feature to Cross-cloud scenarios named "Cross-Cloud Guest Access" \(also known as Teams CCGA\)

So, from the Microsoft 365 perspective, Entra ID B2B & CCB2B provides the capability to recognize users’ identity, and on top of that, different Microsoft 365 workloads implement B2B differently in a way that best suits their business logic and then extend the same feature sets to Cross-cloud scenarios by implementing CCB2B. Based on the best practices observed from different Microsoft 365 workloads, we can describe the relationship between Entra ID B2B/CCB2B & Microsoft 365 B2B/CCB2B using a DAG\(Directed Acyclic Graph\) – which illustrates the dependency info from engineering implementation perspective.

![Diagram of Entra ID and Microsoft 365 relationship from dependency perspective.](https://learn.microsoft.com/en-us/microsoft-365/enterprise/media/cross-cloud-whitepaper/figure-10-entra-id-microsoft-365-relationship-from-dependency-perspective.png?view=o365-worldwide)

*Figure 10: Entra ID & Microsoft 365 relationship from dependency perspective*

Important

- Entra ID supporting B2B/CCB2B doesn't necessarily mean that all Microsoft 365 workloads support B2B/CCB2B as well. Because Entra ID B2B/CCB2B only solves the user identity recognition problem, it’s the different Microsoft 365 workloads responsibility to unblock more collaboration user scenarios based on Entra ID B2B/CCB2B.
- Whenever a feature is released from any Microsoft 365 workloads, it doesn't necessarily mean that it would support Cross-cloud scenarios by default, as the feature is designed to be functional within the **same tenant**, and it usually requires extra engineering efforts to bring the same feature to **Cross-tenant** and **Cross-cloud** scenarios via B2B and CCB2B respectively.
- Each Microsoft 365 workload implements B2B & CCB2B in different rhythms. So, you may find that one workload supports both B2B & CCB2B \(for example, Teams\), while some of others only support B2B \(for example, Power Automate\) or they don't support B2B & CCB2B at all \(for example, Forms\).

### Introduction to Conditional access

Conditional Access for B2B users, including CCB2B users, allows tenant admins to enforce security policies for external users collaborating with their organizations. Tenant admins can apply policies to B2B users, including CCB2B users, by targeting them specifically within the Conditional Access policy configuration.

#### Conditional Access policy configuration

Admins can configure Access policies targeting B2B Guests, including CCB2B users \(you can specify different policies for "Guest User Type" and "Member User Type" users\).

![Screenshot that shows Configure the policy as needed.](https://learn.microsoft.com/en-us/microsoft-365/enterprise/media/cross-cloud-whitepaper/figure-11-configure-the-policy-as-needed.png?view=o365-worldwide)

*Figure 11: Configure the policy as needed*

#### Trust compliant devices

Organizations can use Conditional Access policies to require users' devices to be managed by Microsoft Intune, so devices stay at compliant status. However, a device can't be managed by two organizations, and users’ devices must be managed by their home tenants. So, tenant admins can't manage B2B users' devices directly \(same for CCB2B users\), but admins can use "Cross-tenant access settings" to choose to trust device compliance claims from a B2B\(or CCB2B\) user's home tenant about whether the user's device meets their device compliance policies or is [Microsoft Entra hybrid joined](https://learn.microsoft.com/en-us/entra/identity/conditional-access/policy-alt-all-users-compliant-hybrid-or-mfa). Tenant admins can set device trust settings for all Microsoft Entra organizations or individual organizations. When device trust settings are enabled, Microsoft Entra ID checks a user's authentication session for a device claim, if the session contains a device claim indicating that the policies were already met in the user's home tenant, the external user is granted sign-on to your shared resource \(for more comprehensive reading, visit [here](https://learn.microsoft.com/en-us/entra/external-id/authentication-conditional-access)\). Here's the basic instructions of how to enable the device trust:

1. Go to Entra ID portal.
2. Find "External Identities" -> "Cross-tenant access settings" -> "Inbound access" for the specific tenant you want to trust -> "Customize settings" \(or alternatively, admins can go to "Cross-tenant access settings" -> "Default settings" to change the default settings\).
3. Make sure the "Trust compliant devices" is enabled.

   ![Screenshot that shows Navigate to inbound configs in Microsoft Entra admin center.](https://learn.microsoft.com/en-us/microsoft-365/enterprise/media/cross-cloud-whitepaper/figure-12-navigate-to-inbound-configs-in-microsoft-entra-admin-center.png?view=o365-worldwide)

   *Figure 12: Navigate to inbound configs in Microsoft Entra admin center*

   ![Screenshot that shows Customize the device trust settings as needed.](https://learn.microsoft.com/en-us/microsoft-365/enterprise/media/cross-cloud-whitepaper/figure-13-customize-the-device-trust-settings-as-needed.png?view=o365-worldwide)

   *Figure 13: Customize the device trust settings as needed*

#### Trust MFA

Like **Device trust** tenant, admins can also allow Conditional Access policies to trust B2B \(or CCB2B\) users’ MFA claims from external organizations. During authentication, Microsoft Entra ID checks a user's credentials for a claim that the user completed MFA. If not, an MFA challenge is initiated in the user's home tenant.

1. Go to Entra ID portal.
2. Find "External Identities" -> "Cross-tenant access settings" -> "Inbound access" for the specific tenant you want to trust -> "Customize settings" \(or alternatively, admins can go to "Cross-tenant access settings" -> "Default settings" to change the default settings\)
3. Make sure the "Trust multifactor authentication from Microsoft Entra tenants" is enabled.

   ![Screenshot that shows Customize the MFA trust settings as needed.](https://learn.microsoft.com/en-us/microsoft-365/enterprise/media/cross-cloud-whitepaper/figure-14-customize-the-mfa-trust-settings-as-needed.png?view=o365-worldwide)

   *Figure 14: Customize the MFA trust settings as needed*

## CCB2B – Microsoft 365 workload level

Note

In this section, we introduce Cross-cloud features from Microsoft 365 workloads perspective, from what the feature resolves to how to configure your tenants so users in your tenant can use them for Cross-cloud collaboration. Note the official detailed guidance might change over time. We add links for each workload so you can always get to know the latest information.

### Introduction of Teams

Teams offers few solutions that allow users to chat & have meetings and even channel collaboration experience in Cross-cloud scenarios. In the following sections, we guide you through each of them, introduce the capabilities and how to apply the solution to your tenants.

#### Cross-cloud Anonymous Meeting

Cross-cloud Anonymous Meeting \(also known as CCA\) allows users to anonymously join Teams meetings that hosted in a different cloud. Because it’s anonymous, so users don't need to install Teams Desktop client, they can join via Teams Web client as long as they have the meeting link. To enable this feature, tenant admins need to do the following \(check the comprehensive guide [here](https://techcommunity.microsoft.com/blog/microsoftteamssupport/cross-cloud-communications-between-the-21vianet-teams-in-china-and-the-worldwide/3909302)\):

1. Go to Teams Admin Center \(also known as TAC\)
2. Select "Settings & policies" on the left panel, under "Meetings & Events" section, choose "Meetings".
3. Under "Meeting join & lobby" section, turn on "Anonymous users and dial-in callers can start a meeting".
4. Save the changes.

   ![Screenshot that shows How to configure CCA in TAC.](https://learn.microsoft.com/en-us/microsoft-365/enterprise/media/cross-cloud-whitepaper/figure-15-how-to-configure-cca-in-tac.png?view=o365-worldwide)

*Figure 15: How to configure CCA in TAC*

Once done, users are able to invite external users to meetings or send meeting links directly to them. From the invitee perspective, when they select the meeting link or the "Join" button from their calendar in Teams client, they're asked to provide a temporary name during the "Pre-Join" stage, it encourages users to input their name, but it could be any arbitrary text given by the user:

![Screenshot that shows User Experience of CCA during meeting pre-join.](https://learn.microsoft.com/en-us/microsoft-365/enterprise/media/cross-cloud-whitepaper/figure-16-user-experience-of-cca.png?view=o365-worldwide)

*Figure 16: User Experience of CCA\(during meeting pre-join\)*

Once pass the "Pre-Join" stage, the external user is in lobby pending for approval, once approved, the external user joins the meeting successfully. Meeting participants see the external user’s name whatever provided by the external user in previous step, with a suffix of "\(Unverified\)" indicating that the name of the user isn't verified by Microsoft.

![Screenshot that shows User Experience of CCA during the meeting.](https://learn.microsoft.com/en-us/microsoft-365/enterprise/media/cross-cloud-whitepaper/figure-17-user-experience-of-cca.png?view=o365-worldwide)

*Figure 17: User Experience of CCA\(during the meeting\)*

#### Cross-cloud Authenticated Meeting

Cross-cloud Authenticated Meeting \(also known as CCM\) allows a Teams user to join meetings that hosted in another cloud while signed into their account in their home tenant. This feature provides the meeting host with the ability to validate the identities of meeting participants.

To enable this feature, tenant admins need to configure the following \(check the comprehensive guide [here](https://learn.microsoft.com/en-us/microsoftteams/cross-cloud-meetings)\):

1. Go to TAC.
2. On the left panel, select **Settings & policies**, under "Meetings & Events" section, choose **Meetings**.
3. Under Cross-cloud meetings section, add the ID of the tenant that the external user belongs to. a. Enable the cloud that the external user belongs to. b. The default inbound & outbound configs should be working but also can customize them according to customers’ needs.
4. Save the changes.

   ![Screenshot that shows How to configure CCM.](https://learn.microsoft.com/en-us/microsoft-365/enterprise/media/cross-cloud-whitepaper/figure-18-how-to-configure-ccm.png?view=o365-worldwide)

   *Figure 18: How to configure CCM*

Once done, users are able to invite external users to meetings or send meeting links directly to them. From the invitee perspective, when they select the meeting link or the "Join" button from their calendar in Teams client, they're asked to sign-in using their home tenant accounts/credentials and then they're redirected to the meeting. Other meeting participants see the external user’s name, which is exactly the external user’s display name in their home tenant.

#### Cross-cloud Guest Access

Teams Cross Cloud Guest Access \(also known as CCGA\) extends existing Guest Access functionality allowing a user to participate in rich collaboration experiences in channels, documents, and Teams meetings between tenants across different clouds. Guests are able to participate in a full collaboration experience including audio/video, screen share, Channel file share and both 1:1 and 1: many chats. These features are enabled through the Microsoft Entra ID CCB2B feature and Cross Tenant Access Settings, which allows tenant admins to trust tenants between different clouds.

To enable this feature, the followings are required \(check the comprehensive guide [here](https://techcommunity.microsoft.com/blog/microsoftteamssupport/cross-cloud-meeting--cross-cloud-guest-access-between-ww-teams-and-21vianet-team/3990829)\):

##### Step 1: Configure Cross-tenant access setting

For detailed guidance, refer to previous section "Cross-tenant access settings". If you complete the CCM configuration, you might find that the cloud enabled during that process in TAC is also automatically enabled here, that’s because this cloud enablement setting is synchronized between Microsoft Entra ID portal & TAC, and vice-versa, if you complete the cloud enablement from Microsoft Entra ID portal first, the same cloud enablement setting is synced to TAC.

##### Step 2: Enable CCB2B users in Teams

There are two options to complete this user enablement

###### Option #1 Enable users through Microsoft Entra admin center

1. Go to Microsoft Entra admin center -> Go to **Users** -> **All users** -> **New user** -> **Invite external user**

   ![Screenshot that shows Invite from Entra.](https://learn.microsoft.com/en-us/microsoft-365/enterprise/media/cross-cloud-whitepaper/figure-19-invite-from-entra.png?view=o365-worldwide)

   *Figure 19: Invite from Entra*
2. In the invitation detail page, input the email of the external user in **Basic** tab, and in **Properties** tab, fill names and other info as needed. Keep the "User Type" as "Guest". Once all information is provided, send out the invitation.
3. The external user receives an email notification in their inbox \(see comprehensive guide [here](https://learn.microsoft.com/en-us/entra/external-id/invitation-email-elements)\) with a link, which they can visit and accept the "Guest invite", once done, there's a Guest identity created in the resource tenant \(the tenant they're invited to\).
4. Go to Teams client -> Go to the "Teams channel" where you want the collaboration happens and then Add the external user to the Team by typing their email address or display name, the people picker should be able to return the user in suggestion list for you to choose.

###### Option #2 Enable user through Teams client directly

In this case, there’s no actions required from tenant admins, and the end-users are able to do the followings: Go to Teams client -> Go to the "Teams channel" where you want the collaboration happens -> Add the external user to the Team by adding their email address.

##### Step 3: Switch to Guest profile

1. After being invited to a team, the user receives a welcome email with information about the team and notifies the user that they're now added to the team. There’s a link to the team, which can redirect the user to the team. Or the user can sign-in to their home tenant Teams, and they see a "Guest profile" list under "Me Menu", they're redirected to the resource tenant Teams by switching to the Guest profile, and they can switch back to the home tenant later via "Me Menu" as well.
2. Once external users switch to "Guest profile", they're "Guest" users in the resource tenant, and they can start 1:1/group chat/call or have channel meetings, participate into channel conversations & upload/download channel files as if they were in their home tenant. \(note that attaching files to 1:1 chat/group chat isn't supported\). Users are able to collaborate with others in the resource tenant only by switching to the "Guest profile", the currently active profile defines which people, channels, and chats the user can access and interact with.
3. For Cross-cloud meeting scenarios \(join a meeting that set up by resource tenant users\), users don't need to switch to "Guest profile", and they can stay at their home tenant profile and go to Calendar tab in Teams client -> select the Cross-cloud meeting from calendar -> select "Join" button, the user might be asked for providing the home tenant account/credential, once complete the sign-in process, the user is able to join the meeting.

   ![Screenshot that shows Choose the correct profile.](https://learn.microsoft.com/en-us/microsoft-365/enterprise/media/cross-cloud-whitepaper/figure-20-choose-the-correct-profile.png?view=o365-worldwide)

   *Figure 20: Choose the correct profile*

   a. When a "Guest" user joins the meeting, their display name is appended with a suffix "\(Guest\)".

   ![Screenshot that shows User Experience of CCGA.](https://learn.microsoft.com/en-us/microsoft-365/enterprise/media/cross-cloud-whitepaper/figure-21-user-experience-of-ccga.png?view=o365-worldwide)

   *Figure 21: User Experience of CCGA*

   b. When the Guests exit the meeting, if they want to revisit the meeting chats, they need to switch to the Guest profile.

### Introduction of OneDrive and SharePoint

With OneDrive and SharePoint integration with Microsoft Entra ID B2B/CCB2B, it unblocks scenarios sharing files/folders/document libraries and sites with people outside your organization. And such Cross-tenant collaboration also works even if the tenants are in different clouds. From user experience perspective, one can share a file/folder/site/… with External Guest users and collaborate with them like coediting the same file at the same time as if there were in the same tenant. Refer to previous sections for detailed steps of how to invite external user as a "Guest" user & how those external users should accept/redeem the Guest invitation.

For the tenants that provisioned after June 2023, the OneDrive and SharePoint CCB2B collaboration config is enabled by default, however, if your tenant was provisioned before that date, then the following configurations are required via manual process\(check comprehensive guide [here](https://learn.microsoft.com/en-us/sharepoint/sharepoint-azureb2b-integration), and [here](https://learn.microsoft.com/en-us/entra/external-id/what-is-b2b#integrate-with-sharepoint-and-onedrive)\):

#### Tenant-level

1. Download the latest SharePoint Management Shell\([link](https://go.microsoft.com/fwlink/p/?LinkId=255251)\).
2. Connect to SharePoint as a [SharePoint Administrator](https://learn.microsoft.com/en-us/sharepoint/sharepoint-admin-role) permission or [higher](https://learn.microsoft.com/en-us/microsoft-365/admin/add-users/about-admin-roles) in Microsoft 365. To learn how, see [Getting started with SharePoint Management Shell](https://learn.microsoft.com/en-us/powershell/sharepoint/sharepoint-online/connect-sharepoint-online).
3. Run the following cmdlets:

   ```powershell
   Set-SPOTenant -EnableAzureADB2BIntegration $true
   ```

#### Site-level

Even if the tenant-level is configured correctly, from end users perspective, when they try to share a file hosted in a SharePoint site, they might realize that the Guests can't show up in "People picker", it’s a component where users input others name and it returns potential contacts based on the user’s input. To enable the Guests in SharePoint site, the following are required \(see comprehensive command guidance [here](https://learn.microsoft.com/en-us/powershell/module/sharepoint-online/set-sposite#-showpeoplepickersuggestionsforguestusers) where you can find extensive examples about the Set-SPOSite command and its parameters\). Run the following cmdlets:

```powershell
Set-SPOSite -Identity url-to-the-SPO-site ShowPeoplePickerSuggestionsForGuestUsers $true
```

Tip

During the Microsoft Entra ID invitation, besides "User Type: Guest" you can also choose to invite the external user as "User Type: Member", the major difference is that when users share OneDrive and SharePoint resources, if they choose the scope like "All people in xyz org can access", then this scope includes "User Type: Member", but exclude "User Type: Guest".

### Introduction of Exchange Online

By default, when you invite external users to your tenant as External Guest users, they aren't visible in the Exchange Global Address List \(GAL\). And when a user tries to book a meeting with the Guest, the "Meeting assistant" doesn't show free/busy status for those Guests. To unblock the above scenarios, the steps listed are required.

#### Enable Guests in GAL

Check the comprehensive guide [here](https://learn.microsoft.com/en-us/microsoft-365/solutions/per-group-guest-access#add-guests-to-the-global-address-list)

1. Find the guest's ObjectID by running:

   ```powershell
   Get-MgBetaUser -All | ?{$_.CreationType -eq "Invitation"}
   ```

2. Then run the following using the appropriate values for ObjectID, GivenName, Surname, DisplayName, and TelephoneNumber.

   ```powershell
   Update-MgBetaUser -UserId input-the-user-id-from-previous-step -ShowInAddressList $true -GivenName 'input-name' -Surname 'input-name' -DisplayName 'input-name' -mobilePhone 'input-phone-number'
   ```

#### Enable Free/Busy for CCB2B users

To enable calendar availability sharing across Microsoft 365 tenants in different sovereign or commercial clouds, administrators have two supported configuration options: Availability Address Space \(AAS\) and Organization Relationship \(OrgRel\). Each method has distinct characteristics that align with different operational models and security postures.

| Feature | Availability Address Space \(AAS\) | Organization Relationship \(OrgRel\) |
| --- | --- | --- |
| **Configuration Interface** | PowerShell \(Exchange Online\) | Exchange Admin Center \(GUI\) |
| **Token Model** | Protected Forwarded Token \(PFT\) | Delegation Auth Token \(DAuth\) |
| **Endpoint Dependency** | Requires Autodiscover endpoint | Supports Autodiscover or direct calendar service |
| **Access Control Granularity** | Basic \(time-only availability\) | Fine-grained \(time, subject, location\) |
| **Security Context** | Operates under elevated app privileges | Supports user-context delegation |
| **Preferred for** | Scripted legacy environments | Modern hybrid or federated deployments |

##### When to Choose Organization Relationship

- You require **fine-grained control** over calendar data visibility \(for example, subject and location\).
- You prefer **GUI-based configuration** for ease of management.
- You aim to align with Microsoft's **security best practices**, especially the reduction of high-privilege access.
- You're operating in a **modern hybrid or federated identity environment**.

##### When to Choose Availability Address Space

- You need **automated or scripted setup** via PowerShell.
- You're working in a **legacy Exchange environment** or require compatibility with older configurations.
- You're comfortable managing **Autodiscover endpoints manually**.
- Given that OrgRel depends on DAuth, however DAuth isn’t supported in 21Vianet cloud yet, so 21Vianet cloud tenant admins need to use AAS.

##### Security Considerations

Microsoft is actively encouraging customers to adopt **user-context delegation models** such as those supported by OrgRel. This approach aligns with the broader initiative to reduce high-privilege access and improve tenant isolation and auditability. While AAS remains supported, it's less aligned with current security architecture principles and might introduce operational complexity in multicloud scenarios.

##### Option #1: Enable calendar availability sharing via Organization Relationship

To enable Free/Busy status, tenant admins from **both** clouds need to follow this organization relationship [guidance](https://learn.microsoft.com/en-us/exchange/sharing/organization-relationships/create-an-organization-relationship#use-the-exchange-admin-center-to-create-an-organization-relationship) to create an organization relationship.

##### Option #2: Enable calendar availability sharing via AAS

Alternatively, admins can also configure the free/busy sharing using the following AAS instructions over PowerShell:

1. Use PowerShell to Connect to Exchange, see command Connect-ExchangeOnline guidance [here](https://learn.microsoft.com/en-us/powershell/exchange/connect-to-exchange-online-powershell). WW cloud tenant admins can use the command directly, while other cloud tenant admins must specify ExchangeEnvironmentName parameter according to the provided guidance.
2. Enable Organization customization for both orgs, see command guidance [here](https://learn.microsoft.com/en-us/powershell/module/exchangepowershell/enable-organizationcustomization).
3. Configure AvailabilityConfigs, see guidance [here](https://learn.microsoft.com/en-us/powershell/module/exchangepowershell/new-availabilityconfig). If you want to update/remove existing AvailabilityConfigs, check guidance [here](https://learn.microsoft.com/en-us/powershell/module/exchangepowershell/set-availabilityconfig)
4. Configure AvailabilityAddressSpace by following [this guidance](https://learn.microsoft.com/en-us/powershell/module/exchangepowershell/add-availabilityaddressspace). It’s recommended to configure AccessMethod as OrgWideFBToken, but you can configure as per your organization’s requirements. \(if you want to remove the AvailabilityAddressSpace, then follow [this guidance](https://learn.microsoft.com/en-us/powershell/module/exchangepowershell/remove-availabilityaddressspace)\) After administrators complete the PowerShell configuration, both tenants can access each other's Free/Busy information. Here are more tips for the AAS configuration:

- You can add the new AAS immediately when the previous one is removed, but the changes take about 15 mins to sync. If you configure AAS for the target tenant before, remove them and create new ones for them.
- AllowedTenantIds limitation is 25.
- The mailboxes, for whom you want to access free/busy, must exist in the local tenant’s global address list. In case the mailboxes of the remote tenant aren't present in the local tenant, you can add them using the command `New-MailContact`, see guidance [here](https://learn.microsoft.com/en-us/powershell/module/exchangepowershell/new-mailcontact). Another method is to invite remote users as Guest and then enabling them to show in global address list. \([check Prevent guests from being added to a specific group \| Microsoft Learn](https://learn.microsoft.com/en-us/microsoft-365/solutions/per-group-guest-access#add-guests-to-the-global-address-list)\)

### Introduction of Power Platforms

#### Introduction to Power BI

Power BI supports B2B \(for extensive reading, visit [here](https://learn.microsoft.com/en-us/fabric/enterprise/powerbi/service-admin-entra-b2b)\), and Power BI also supports similar capabilities across Microsoft Azure clouds by configuring Microsoft cloud settings for B2B collaboration. Find instructions in previous sections to learn how to establish mutual B2B collaboration between the following clouds:

- Microsoft Azure Global Cloud and Microsoft Azure Government
- Microsoft Azure Global cloud and Microsoft Azure in China

There are some limitations to the B2B experience that you should be aware of in the Cross-cloud scenarios\(to get the latest info, check [here](https://learn.microsoft.com/en-us/fabric/enterprise/powerbi/service-admin-entra-b2b#cross-cloud-b2b)\):

- Guests might already have a Power BI license that was assigned to them through their own organization. But "BYOL - Bring Your Own License" doesn’t work across different Microsoft Azure clouds for B2B guests. A new license has to be assigned to these guests by the resource tenant.
- New external users can't be invited to the organization through Power BI sharing, permissions, and subscription experiences.
- On the Home page, the "From external orgs" tab doesn't list content shared from other clouds.
- Cross-cloud sharing doesn't work when sharing with a security group. For instance, if a user using Power BI in a national cloud invites a security group from the public cloud or vice versa, access isn't granted. This limitation occurs because the service can't resolve the members of these groups across clouds.

#### Introduction to Power Automate

The Power Automate experience for Guests \(both B2B & CCB2B\) is similar as it is for non-Guests. Guests have the same experience in both the Power Automate portal and the Power Automate mobile app. Here are the capabilities of Guests \(for comprehensive introduction, visit [here](https://learn.microsoft.com/en-us/power-automate/share-guest-users)\):

- Search for a guest

A user can search for, find, and select a guest in a trigger or action. As they start typing the name of the guest, they see a list of names to choose from in the dropdown list. When they see the name of the guest, they can select it. This people picker feature saves the user time because they don't need to finish typing the entire name. \(Some connectors don't support this capability.\)

- Sharing

If a guest needs to only run a flow, they need to have the Sharing-Run Only role assigned. If they need to edit flows and perform actions to flow runs such as canceling or resubmitting a flow run, they need a co-owner role assigned.

- Approvals

A guest can be assigned an approval, receive an approval email, and be routed to the Approvals page in the guest tenant to approve or reject. They can also view and interact with the approval email body in the same way as a non-Guest. Guests can't see the approvals from their guest tenant while they're in their original tenant, or from their original tenant while they're in their guest tenant.

- Widgets

A guest can create, manage, or run flows using widgets in apps like SharePoint, Teams, Excel, Power BI, and more. Power Automate supports "Guest User Type", however "Member User Type" isn't supported yet.

## Others you should know about Cross-cloud collaboration

### Teams

#### CCGA user experience

- When the external user switches to the "Guest profile" inside Teams client, or when the external user tries to join a CCM meeting in their home tenant Teams calendar, they might be asked to provide their passwords \(although external users are going to access to a Cross-cloud resource, but users’ password isn't sent out of the cloud boundary, the identity authentication flow happens within the same cloud\).
- After invitees receive a Teams channel invitation, invitees should be able to see "Guest profile" in the "Me menu" within minutes; in rare cases, it might take up to 24 hours.
- If a user satisfies both CCM and CCGA condition, then the user joins the meeting via CCGA identity, which means they sign-in to the meeting using their Guest profile, which means there's "\(Guest\)" suffix.
- Keep in mind that CCM only works for external users, if external users are invited on Microsoft Entra ID level \(no matter if it’s invited as "Guest type" or "Member type"\), even though they aren't invited to any Teams channels to complete the CCGA invitation flow, they aren't able to join Cross-cloud meetings via CCM, in such case, CCGA takes place.
- Guests can revisit the meeting chat history after the meeting \(need to switch to the Guest profile, can't see them in home tenant Teams profile\)
- The "\(Guest\)" suffix only applies to "External Guest" users – if you invited the External user as "Member type" \(also known as External Member role\) on Microsoft Entra ID level then invite that user to your Teams team, in such case, that user doesn't have "\(Guest\)" suffix in the resource tenant.
- As of 2026 Q2, Teams CCGA doesn't support External Member users, and choose to use External Guest users instead.

#### Teams External Access

Besides the Teams CCGA, Teams also offers a lightweight solution to address Cross-cloud chat needs, that’s Teams External Access. It's a feature that allows Teams users from Cloud A to communicate with Teams users in Cloud B, but it doesn't require admins to set-up CCB2B between tenants, nor require users to be invited to other tenants. This feature is enabled by default for all tenants, and the default policy of this feature allows such external chat ability with all other tenants. Tenant admins can configure other options in the Teams Admin Center \(TAC\) that best suit their business & security needs, for example,

- Allow this feature with all external tenants
- Allow this feature for some specific external tenants
- Block this feature with all external tenants
- Block this feature for some specific external tenants

To enable & customize the policy \(check the comprehensive guide [here](https://techcommunity.microsoft.com/blog/microsoftteamssupport/cross-cloud-communications-between-the-21vianet-teams-in-china-and-the-worldwide/3909302)\)

1. Go to TAC \(FYI endpoints are different in each cloud, in 21Vianet cloud, it’s [link](https://admin.teams.microsoftonline.cn/)\)
2. Select "Users" on the left panel, then select "External access".
3. Turn on "Users can communicate with other Skype for Business and Teams users".
4. Add domains that you want to allow or block for external access.
5. Save the changes.

   ![Screenshot that shows How to configure Teams External Access in TAC.](https://learn.microsoft.com/en-us/microsoft-365/enterprise/media/cross-cloud-whitepaper/figure-22-how-to-configure-teams-external-access-in-tac.png?view=o365-worldwide)

   *Figure 22: How to configure Teams External Access in TAC*

Once done, the user is able to search and initiate chats with external users by searching for their full email address inside Teams client. Here are more tips for searching for the external user:

- If you're using customized domain instead of the Microsoft default domain, ensure that SRV records are configured, see guidance [here](https://learn.microsoft.com/en-us/microsoft-365/enterprise/external-domain-name-system-records#external-dns-records-required-for-teams).
- The external user’s tenant admin also needs to enable this feature and allow your tenant domain on their side.
- When searching for the external user, use their Email address. If search results return more than one several entries, choose the one with "\(External\)" suffix. By default, users’ UPN/SIP address is the same as their Email address, but some tenant admins might specifically configure them differently, in such case, try to search for their UPN/SIP address.

  ![Screenshot that shows How to search the external user in Teams External Access scenario.](https://learn.microsoft.com/en-us/microsoft-365/enterprise/media/cross-cloud-whitepaper/figure-23-how-to-search-the-external-user-in-teams-external-access-scenario.png?view=o365-worldwide)

  *Figure 23: How to search the external user in Teams External Access scenario*

Once the Teams External Access chat session is established, there's an "External" tag indicating that you're chatting with someone out of your organization, and the "1:1 Chat" only supports plain text, it doesn't support uploading file or rich text like emoji, image,…

![Screenshot that shows User experience of Cross-cloud chat.](https://learn.microsoft.com/en-us/microsoft-365/enterprise/media/cross-cloud-whitepaper/figure-24-user-experience-of-cross-cloud-chat.png?view=o365-worldwide)

*Figure 24: User experience of Cross-cloud chat*

## Best Practices

Since Cross-cloud solution was released, we observe wide adoption by in different clouds including Commercial clouds & 21Vianet cloud and US Government clouds. It’s also already widely adopted in customers’ production environments. One example of successful Cross-cloud solution adoption is a Multi-National-Company \(also known as MNC\) customer from "Power & Utilities" industry who used Teams CCGA feature to build the connection between their headquarter employees \(in Commercial cloud\) and their China employees \(in 21Vianet cloud\), which enables communication and collaboration on joint projects. By using Teams' CCGA capabilities, they were able to streamline workflows, reduce email clutter, and improve project outcomes. The customer also uses SharePoint CCB2B feature to collaborate on files across-clouds between their headquarter employees and their China employees. The adoption of CCB2B ensured compliance with industry regulations while facilitating efficient daily collaboration.

Different customers have different needs according to their unique business & the regulation requirements from different industries. Based on research & engagement with customers from different industries, here are some best practices you can consider when adopting CCB2B in your business.

### Refine your requirements

Different solutions require different processes to enable. As tenant admin, always start with requirement analysis, which is to think through what major Cross-cloud user scenarios are in your daily work, understand your requirements first before making any decisions. Then find the correct process according to previous sections to configure your tenants.

### Understanding User Experience

Some Microsoft 365 workloads might introduce different user experience in Cross-cloud scenarios, for example:

- Teams CCGA feature requires users to switch to "Guest profile" within Teams client when they want to access to a Teams channel hosted in other tenants across clouds.
- Teams External Access feature only supports plain text 1:1 chat if the participants are from different clouds.
- Teams CCM feature requires users to input accounts/passwords during the meeting join process.

Such different user experiences need to be communicated with end-users by tenant admins in advance to set the right expectation.

### Configure Microsoft Entra ID for CCB2B

When tenant admins invite External users on Entra ID level, there are two options:

- Invite the user as "Guest" user type \(also known as External Guest\), which is the by default option.
- Invite the user as "Member" user type \(also known as External Member\).

Whenever which choice is selected, this decision is shared with all Microsoft 365/Power Platform workloads for example, Teams, OneDrive and SharePoint …, because Microsoft products depend on Microsoft Entra ID to validate user’s identity. However, from workload perspective, "External Guest" & "External Member" might have slightly differences, such as

- Supportability schedule – different workload engineering teams might have different roadmap planning for "External Guest" & "External Member", one being ready does **NOT** necessarily mean that the other is ready as well. And different user types might have differences from workload feature perspective. Regarding supportability & feature difference visit previous sections for details.
- Double-license requirements – comparing with "External Guest", some workloads need the "External Member" user to have a license in the resource tenant.

Besides Microsoft products, customers might have their own LOB \(Line of Business\) applications or their own services that integrated with Microsoft Entra ID. In such case, choosing "External Member" or "External Guest" also impacts those services, which may or may not require engineering effort to support External Member/Guest scenarios, it depends on how those LOB/services implemented, and customers need to self-review & refactor as needed.

### Configure each workload

Enabling CCB2B on Microsoft Entra ID level is the prerequisite of enabling CCB2B for Microsoft 365/Power Platform workloads, however, enabling CCB2B on Entra ID level doesn't necessarily mean that CCB2B is automatically enabled on those workloads level. To enable CCB2B for those workloads, tenant admins need to specifically make configurations respectively, check the previous sections for detailed guidance for different workloads.

### Validate in Pre-production environment

Cross-cloud solutions provide extensive configurations, both on Microsoft Entra ID level & Microsoft 365 level, to accommodate different needs for different customers. The by-default configs during the Cross-cloud setup works for demo purposes, however, it’s recommended to customize the configuration as needed so the Cross-cloud solution meets compliance and security requirements. To avoid interruption on the end-user side, it’s recommended that admins do some Cross-cloud validation work in non-production environment, once it’s proved working as expected, then roll out the same to production environment.

## Appendix

### Terminology

- **Tenants**: when a customer purchases Microsoft 365 or Azure products, there's a dedicated tenant provisioned for the customer. A Microsoft 365 tenant is a dedicated instance of the services of Microsoft 365 and the customer’s organization data stored within a specific location, which is specified when the customer creates the tenant for their organizations.
- **Home tenant**: the tenant that user was originally provisioned from
- **Resource tenant**: the tenant that a user was invited to
- **B2B user**: refers to a user who is invited to another tenant as External Guest/Member \(the resource tenant and the user’s home tenant are in the same cloud\)
- **CCB2B user**: refers to a user who is invited to another tenant as External Guest/Member \(the resource tenant and the user’s home tenant are in different clouds\)
- **External user**: for a given tenant, if a user is never invited to that tenant, then that user is an "External user" to that tenant.
- **NCOE**: National Cloud Operating Entity
- **Sovereign cloud\(s\)**: refers to clouds besides the commercial cloud, they're operated by Microsoft or an independent local third party, for example, 21Vianet cloud/GCC/GCCH/DoD/Delos/Bleu clouds
- **Cross-tenant collaboration**: two users from different tenants to chat/call/share resource with each other, but within the same cloud
- **Cross-cloud collaboration**: two users from different clouds to chat/call/share resource with each other, but across different clouds

### CCB2B FAQ

- Q: What is CCB2B? A: CCB2B stands for Cross-Cloud Business-to-Business solution, which is designed to facilitate collaboration between businesses using Microsoft products.
- Q: Which Microsoft products support CCB2B? A: Currently, Microsoft Entra ID fully supports CCB2B, Microsoft 365 products like OneDrive, Teams, Power BI, Exchange Online, and SharePoint Online support it, however others like PowerApps, Forms don't support it at the moment.
- Q: How to integrate my own apps with Microsoft Entra ID? A: Microsoft Entra ID is a cloud-based identity and access management service that your employees can use to access external resources. Example resources include Microsoft 365, the Azure portal, and thousands of other SaaS applications. Microsoft Entra ID also helps them access internal resources like apps on your corporate intranet, and any cloud apps developed for your own organization. For the latest information, visit [here](https://learn.microsoft.com/en-us/entra/fundamentals/five-steps-to-full-application-integration)
- Q: Does PowerApps support Cross-cloud scenario? A: PowerApps supports B2B scenario, for example, users can share PowerApps Canvas apps with Guests. However, it doesn't support Cross-cloud scenarios yet as of CY26 Q2. Although some PowerApps B2B scenarios might just happen to work in Cross-cloud situations, it’s not by design on purpose, it’s undefined behavior, which means it may or may not work overtime until PowerApps officially commits to supporting those CCB2B scenarios. Given customers don't receive official support within SLA for any features that aren't Generally Available, we don’t recommend customers to try PowerApps CCB2B scenarios in production environments. To understand what PowerApps B2B supports \(within the same cloud, visit [here](https://learn.microsoft.com/en-us/power-apps/maker/canvas-apps/share-app-guests)\)
- Q: I encounter issues when following this article, what help resource can I use? A: If you're 21Vianet cloud tenant admin, then you can use this self-serve agent\([link](https://officesupport.azure.cn/)\) to troubleshoot, otherwise, use the routine customer support channel.
