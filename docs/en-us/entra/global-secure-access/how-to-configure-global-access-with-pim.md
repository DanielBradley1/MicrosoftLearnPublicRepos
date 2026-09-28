<!-- Source: https://learn.microsoft.com/en-us/entra/global-secure-access/how-to-configure-global-access-with-pim -->
<!-- Sitemap-Last-Modified: 2026-03-25 -->

# Secure private application access with Privileged Identity Management \(PIM\) and Global Secure Access

## Overview

Microsoft Entra Private Access provides secure access to private applications. Private Access includes built-in capabilities for maintaining a secure environment. Microsoft Entra Private Access does this by controlling access to private apps and preventing unauthorized or compromised devices from accessing critical resources. For general corporate access, see [Microsoft Entra Private Access](https://learn.microsoft.com/en-us/entra/global-secure-access/concept-private-access).

For the scenario where you need to control access to specific *critical* resources, such as highly valued servers and applications, Microsoft recommends that you add an extra security layer by enforcing just-in-time privileged access on top of their already secured private access.

This article discusses how to use Microsoft Entra Private Access to enable Privileged Identity Management \(PIM\) with Global Secure Access. For details about enabling \(PIM\), see [What is Microsoft Entra Privileged Identity Management?](https://learn.microsoft.com/en-us/entra/id-governance/privileged-identity-management/pim-configure).

<iframe src="https://www.youtube-nocookie.com/embed/Wb6Bh2PbHaM" allowfullscreen="true" data-linktype="external" frameborder="0"></iframe>

## Ensure secure access to your high value private applications

Customers should consider configuring PIM using Global Secure Access to enable:

**Enhanced Security:** PIM allows for just-in-time privileged access, reducing the risk of excessive, unnecessary, or misused access permissions within your environment. This enhanced security aligns with the [Zero Trust](https://www.microsoft.com/security/business/zero-trust) principle, ensuring that users have access only when they need it.

**Compliance and Auditing**: Using PIM with Microsoft Global Secure Access can help ensure that your organization meets compliance requirements by providing detailed tracking and logging of privileged access requests. For details about PIM licensing, see [Microsoft Entra ID Governance licensing fundamentals](https://learn.microsoft.com/en-us/entra/id-governance/licensing-fundamentals)

## Prerequisites

- [Microsoft Entra ID license that includes Privileged Identity Management \(PIM\)](https://learn.microsoft.com/en-us/entra/fundamentals/licensing)
- [Microsoft Entra Private Access](https://learn.microsoft.com/en-us/entra/global-secure-access/concept-private-access)

## Secure private access

To successfully implement secure private access, you must complete these three steps:

1. [Configure and assign groups](#step-1-configure-and-assign-groups)
2. [Activate privileged access](#step-2-activate-privileged-access)
3. [Follow compliance guidance](#step-3-follow-compliance-guidance)

## Step 1: Configure and assign groups

To begin, configure and assign groups by creating a Microsoft Entra ID group, onboard it as a PIM managed group, update group assignments with eligible membership, and specify access for user and devices.

1. Sign in to [Microsoft Entra](https://entra.microsoft.com/) as at least a [Privileged Role Administrator](https://learn.microsoft.com/en-us/entra/id-governance/privileged-identity-management/pim-configure).
2. Browse to **Microsoft Entra ID** > **Groups** > **All groups**.

   [![Screenshot of the All groups screen.](https://learn.microsoft.com/en-us/entra/global-secure-access/media/pim-global-secure-access/all-groups.png)](https://learn.microsoft.com/en-us/entra/global-secure-access/media/pim-global-secure-access/all-groups.png#lightbox)
3. Select **New group**.
4. In the **Group type**, select **Security**.
5. Provide a group name; for example, `FinReport-SeniorAnalyst-SecureAccess`.

   - This group name example indicates the application \(FinReport\), the role \(SeniorAnalyst\), and the nature of the group \(SecureAccess\), Choose a name that reflects the group's function or the assets it protects.

6. In the **Membership type** option, select **Assigned**.
7. Select **Create**.

   [![Screenshot of the New group screen.](https://learn.microsoft.com/en-us/entra/global-secure-access/media/pim-global-secure-access/new-group.png)](https://learn.microsoft.com/en-us/entra/global-secure-access/media/pim-global-secure-access/new-group.png#lightbox)

### Onboard the group to PIM

1. Sign in to [Microsoft Entra](https://entra.microsoft.com/) as at least a [Privileged Role Administrator](https://learn.microsoft.com/en-us/entra/id-governance/privileged-identity-management/pim-configure).
2. Browse to **ID Governance** > **Privileged Identity Management**.
3. Select **Groups**, then **Discover groups**.
4. Select the group that you created; for example, `FinReport-SeniorAnalyst-SecureAccess`, then select **Manage groups**.
5. When prompted for onboarding, select **OK**.

### Update PIM policy role settings \(optional step\)

1. Select **Setting**, then select **Member**.
2. Adjust any other settings you want in the **Activation** tab.
3. Set the **Activation Max Duration**; for example, 0.5 hours.
4. In the **On activation** option, require **Azure MFA**, and select **Update**.

### Assign eligible membership

1. Select **Assignments**, then **Add assignments**.

   [![Screenshot of the Add assignments option.](https://learn.microsoft.com/en-us/entra/global-secure-access/media/pim-global-secure-access/add-assignments.png)](https://learn.microsoft.com/en-us/entra/global-secure-access/media/pim-global-secure-access/add-assignments.png#lightbox)
2. In the **Role** option, select **Member**, then select **Next**.
3. Add the selected members that you would like to include for the role.
4. In the **Assignment Type** option, select **Eligible**, then select **Assign**.

### Quick Access assignment

1. Sign in to [Microsoft Entra](https://entra.microsoft.com/) as at least a [Privileged Role Administrator](https://learn.microsoft.com/en-us/entra/id-governance/privileged-identity-management/pim-configure).
2. Browse to **Global Secure Access** > **Quick Access** > **Users and groups**.
3. Select **Add user/group**, then specify the group that you created; for example, `FinReport-SeniorAnalyst-SecureAccess`.

Note

This scenario is most effective when you choose **Per-app Access**, as **Quick Access** is used here for reference only. Apply the same steps if you choose **Enterprise Applications**.

### Client-side experience

Even if a user and their device meet security requirements, attempting to access a privileged resource results in an error. This error occurs because Microsoft Entra Private Access recognizes that the user hasn't been assigned access to the application.

[![Screenshot of the client experience error message.](https://learn.microsoft.com/en-us/entra/global-secure-access/media/pim-global-secure-access/client-experience.png)](https://learn.microsoft.com/en-us/entra/global-secure-access/media/pim-global-secure-access/client-experience.png#lightbox)

## Step 2: Activate privileged access

Next, we activate group membership using the Microsoft Entra admin center, and then attempt to connect with the new role activated.

1. Sign in to [Microsoft Entra](https://entra.microsoft.com/).
2. Browse to **ID Governance** > **Privileged Identity Management**.
3. Select **My roles** > **Groups** to see all eligible assignments.

   [![Screenshot of My role groups screen.](https://learn.microsoft.com/en-us/entra/global-secure-access/media/pim-global-secure-access/my-roles-groups.png)](https://learn.microsoft.com/en-us/entra/global-secure-access/media/pim-global-secure-access/my-roles-groups.png#lightbox)
4. Select **Activate**, then type the reason in the **Reason** box. You can also choose to adjust the parameters of the session, then select **Activate**.

   [![Screenshot of the Activate member screen.](https://learn.microsoft.com/en-us/entra/global-secure-access/media/pim-global-secure-access/activate-member.png)](https://learn.microsoft.com/en-us/entra/global-secure-access/media/pim-global-secure-access/activate-member.png#lightbox)
5. Once the role is activated, you receive a confirmation from the portal.

   [![Screenshot of the member being activated in the portal.](https://learn.microsoft.com/en-us/entra/global-secure-access/media/pim-global-secure-access/member-activated.png)](https://learn.microsoft.com/en-us/entra/global-secure-access/media/pim-global-secure-access/member-activated.png#lightbox)

### Reattempt to connect with role activated

Browse any of the published resources, as you should be able to successfully connect to them.

[![Screenshot of connecting to published resource.](https://learn.microsoft.com/en-us/entra/global-secure-access/media/pim-global-secure-access/identify-remote-computer.png)](https://learn.microsoft.com/en-us/entra/global-secure-access/media/pim-global-secure-access/identify-remote-computer.png#lightbox)

### Deactivate the role

If the work is completed ahead of the time you allocated, you can choose to deactivate the role. This action terminates the role membership.

1. Sign in to [Microsoft Entra](https://entra.microsoft.com/).
2. Browse to **ID Governance** > **Privileged Identity Management**.
3. Select **My roles**, then **Groups**.
4. Select **Deactivate**.

   [![Screenshot of Deactivate member screen.](https://learn.microsoft.com/en-us/entra/global-secure-access/media/pim-global-secure-access/deactivate-member.png)](https://learn.microsoft.com/en-us/entra/global-secure-access/media/pim-global-secure-access/deactivate-member.png#lightbox)
5. A confirmation is sent to you once the role is deactivated.

## Step 3: Follow compliance guidance

This final step enables you to successfully maintain a history of access requests and activations. The standard log format helps to meet tracking and logging compliance guidance and provide an audit trail.

[![Screenshot of the Audit log details screen.](https://learn.microsoft.com/en-us/entra/global-secure-access/media/pim-global-secure-access/audit-log-details.png)](https://learn.microsoft.com/en-us/entra/global-secure-access/media/pim-global-secure-access/audit-log-details.png#lightbox)
