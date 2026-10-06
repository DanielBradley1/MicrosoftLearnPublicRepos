<!-- Source: https://learn.microsoft.com/en-us/defender-business/mdb-create-edit-device-groups -->
<!-- Sitemap-Last-Modified: 2026-10-01 -->

# Device groups in Microsoft Defender for Business

In Defender for Business, you apply policies to devices through collections called *device groups*.

## What is a device group?

A *device group* is a collection of devices grouped together based on specified criteria, such as operating system version. Devices that meet the criteria are included in that device group, unless you exclude them. In Defender for Business, you apply policies to devices by using device groups.

Defender for Business includes default device groups that you can use. The default device groups include all the devices that you onboard to Defender for Business. For example, there's a default device group for Windows devices. When you onboard Windows devices, you automatically add them to the default device group.

You can also create new device groups to assign policies with specific settings to certain devices. For example, you might have a firewall policy assigned to one set of Windows devices, and a different firewall policy assigned to another set of Windows devices. You can define specific device groups to use with your policies.

Note

As you create policies in Defender for Business, the system assigns an order of priority. If you apply multiple policies to a given set of devices, those devices receive the first applied policy only. For more information, see [Understand policy order in Defender for Business](https://learn.microsoft.com/en-us/defender-business/mdb-policy-order).

All device groups, including your default device groups and any custom device groups that you define, are stored in [Microsoft Entra ID](https://learn.microsoft.com/en-us/entra/fundamentals/what-is-entra).

## Create a new device group

In Defender for Business, a *policy* is a set of security configuration settings that are applied to devices. You create device groups from within the policy creation or editing workflow.

Currently, you can create a new device group while you're creating or editing a policy, as described in the following procedure:

1. Go to the [Microsoft Defender portal](https://security.microsoft.com) and sign in.
2. In the navigation pane, choose **Configuration management** and select **Device configuration**.
3. Take one of the following actions:

   - Select an existing policy, and then choose **Edit**.
   - Choose **+ Add** to create a new policy.


   Tip


   To get help creating or editing a policy, see [View or edit policies in Defender for Business](https://learn.microsoft.com/en-us/defender-business/mdb-view-edit-create-policies).

4. On the **General information** page, review the information, edit if necessary, and then choose **Next**.
5. Choose **+ Create new group**.
6. Specify a name and description for the device group, and then choose **Next**.
7. Select the devices to include in the group, and then choose **Create group**.
8. On the **Device groups** step, review the list of device groups for the policy. If needed, remove a group from the list. Then choose **Next**.
9. On the **Configuration settings** page, review and edit settings as needed, and then choose **Next**. For more information about these settings, see [Configuration settings](https://learn.microsoft.com/en-us/defender-business/mdb-next-generation-protection).
10. On the **Review your policy** step, review all the settings, make any needed edits, and then choose **Create policy** or **Update policy**.

## View an existing device group

Currently, in Defender for Business, you can view your existing device groups while you are in the process of creating or editing a policy, as described in the following procedure:

1. Go to the [Microsoft Defender portal](https://security.microsoft.com) and sign in.
2. In the navigation pane, choose **Device configuration**.
3. Take one of the following actions:

   - Select an existing policy, and then choose **Edit**.
   - Choose **+ Add** to create a new policy.


   Tip


   To get help creating or editing a policy, see [View or edit policies in Defender for Business](https://learn.microsoft.com/en-us/defender-business/mdb-view-edit-create-policies).

4. On the **General information** step, review the information, edit if necessary, and then select **Next**.
5. Select **Use existing group**. A flyout opens and displays device groups. If you don't have any device groups yet, it prompts you to create a new device group.

## What does the Add All Devices option do?

When you create or edit a policy, you might see the **Add all devices** option.

![Screenshot of the Add All Devices option.](https://learn.microsoft.com/en-us/defender-business/media/add-all-devices-option.png)

Microsoft Intune is the service that manages and tracks your devices. If you select this option, all devices in Intune get the current policy.

## Related content

- [View or edit policies](https://learn.microsoft.com/en-us/defender-business/mdb-view-edit-create-policies)
- [Create a new policy](https://learn.microsoft.com/en-us/defender-business/mdb-view-edit-create-policies)
- [View and manage incidents in Defender for Business](https://learn.microsoft.com/en-us/defender-business/mdb-view-manage-incidents)
- [Respond to and mitigate threats in Defender for Business](https://learn.microsoft.com/en-us/defender-business/mdb-respond-mitigate-threats)
- [Review remediation actions in the Action center](https://learn.microsoft.com/en-us/defender-business/mdb-review-remediation-actions)
