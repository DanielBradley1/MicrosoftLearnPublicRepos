<!-- Source: https://learn.microsoft.com/en-us/defender-business/mdb-policy-order -->
<!-- Sitemap-Last-Modified: 2026-01-20 -->

# Understand policy order in Microsoft Defender for Business

Defender for Business includes [predefined policies](https://learn.microsoft.com/en-us/defender-business/mdb-view-edit-create-policies#default-policies-in-defender-for-business) to help ensure user devices are protected. Your security team can [add new policies](https://learn.microsoft.com/en-us/defender-business/mdb-view-edit-create-policies#create-a-new-policy) as well.

For example, suppose that your security team wants to apply different settings to different groups of devices. They can accomplish this goal by adding more next-generation protection policies or firewall policies. As you add policies, policy order comes into play.

## Policy order in Defender for Business

When you add policies, a priority order is assigned to all policies in the group, as shown in the following screenshot:

[![Screenshot showing multiple policies and policy order column.](https://learn.microsoft.com/en-us/defender-business/media/mdb-deviceconfig-multpolicies.png)](https://learn.microsoft.com/en-us/defender-business/media/mdb-deviceconfig-multpolicies.png#lightbox)

The **Order** column lists the priority for each policy. Predefined policies move down in priority order when you add new policies. You can edit the order of priority for policies you create \(select a policy, and then choose **Change order**\). You can't change the priority of default policies \(they're always last\).

For example, suppose you have three next-generation protection policies that apply to Windows client devices. The default policy is priority 3 \(last\) and you can't change it. You can change the priority of policies 1 and 2 \(switch places\).

**When multiple policies apply to a device, the device receives the policy with the highest priority only**. After the settings of the highest priority policy are applied, policy processing for that type of policy stops. In the previous example, the affected Windows client devices get the next-generation policy with priority 1. The devices never receive policies 2 and 3.

## Key points to remember about policy order

- Policies are automatically assigned a priority.
- You can change the priority for custom policies, but not for default policies.
- Default policies always get the lowest priority as new policies are added.
- Devices receive the first applied policy only, even if the devices are included in multiple policies.

## See also

- [Set up, review, and edit your security policies and settings](https://learn.microsoft.com/en-us/defender-business/mdb-configure-security-settings)
- [View or edit policies](https://learn.microsoft.com/en-us/defender-business/mdb-view-edit-create-policies)
- [Onboard devices](https://learn.microsoft.com/en-us/defender-business/mdb-onboard-devices)
