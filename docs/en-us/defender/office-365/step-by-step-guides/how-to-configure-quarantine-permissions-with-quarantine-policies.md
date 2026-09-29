<!-- Source: https://learn.microsoft.com/en-us/defender-office-365/step-by-step-guides/how-to-configure-quarantine-permissions-with-quarantine-policies -->
<!-- Sitemap-Last-Modified: 2026-07-14 -->

# How to configure quarantine permissions and policies

Providing security admins and users with a simple way to manage false positive folders is vital, given the increased demand for a more aggressive security posture with the evolution of hybrid work. Taking a prescriptive approach, admins and users can manage false positive folders effectively with the guidance in this article.

Tip

For a short video aimed at admins trying to set quarantine permissions and policies, see [Configure quarantine permissions and policies](https://www.youtube.com/watch?v=vnar4HowfpY). If you are an end user, see this [overview of quarantine permissions and policies](https://www.youtube.com/watch?v=s-vozLO43rI).

## Prerequisites

Before you begin, make sure you have the following:

- Sufficient permissions \(Security Administrator role\)
- 5 minutes to perform the following procedures.

## Deciding between built-in or custom quarantine policies

Custom quarantine policies let admins decide which items users can triage in the ***False positive*** folder. Admins can also allow users to request the *release* of those items from the folder.

1. Decide what verdicts category \(bulk, spam, phish, high confidence phish, or malware\) of items you want your user to triage and not triage.
2. For each verdict category that you don't want users to triage, assign messages in that category to the **AdminOnlyPolicy**. As for the category you want users to triage with limited access, you can *create a custom policy* with a request release access and assign users to that verdict category.
3. It's **strongly recommended** that malware and high confidence phish items be assigned to **AdminOnlyPolicy**, regular confidence phish items be assigned *limited access with request release*, while bulk and spam can be left as full access for users.

Important

For more information on how to create granular custom quarantine policies, see [Quarantine policies](https://learn.microsoft.com/en-us/defender-office-365/quarantine-policies).

## Assigning quarantine policies and enabling notification with organization branding

When your security team has decided on which categories of items that users can triage \(or not\), and they've created the corresponding quarantine policies, admins should assign the corresponding quarantine policies to the appropriate users and enable notifications.

1. Identify the users, groups, or domains that you would like to include in the *full access* category vs. the *limited access* category, versus the *Admin-Only* category.
2. Sign in to the [Microsoft Security portal](https://security.microsoft.com).
3. On the left nav, under **Email & collaboration**, select **Policies & rules**.
4. Select **Threat policies**.
5. Select each of the following: **Anti-spam policies**, **Anti-phishing policy**, **Anti-Malware policy**.
6. Select **Create policy** and choose **Inbound**.
7. Add policy Name, users, groups, or domains to apply the policy to, and **Next**.
8. In the **Actions** tab, select **Quarantine message** for categories. You notice another panel for *select quarantine policy*. Use the dropdown to select the custom quarantine policy you created in [Deciding between built-in or custom quarantine policies](#deciding-between-built-in-or-custom-quarantine-policies).
9. Move on to the **Review** section and select the **Confirm** button to create the new policy.
10. For each remaining policy \(**Anti-phishing policy**, **Anti-Malware policy**, and **Safe Attachment policy**\), select **Create policy** > **Inbound**, add the policy name and recipients, select **Quarantine message** with your custom quarantine policy in the **Actions** tab, and then select **Confirm** in the **Review** section.

Tip

For more detailed information about configuring anti-spam, anti-phishing, and Safe Attachments policies, see:

- [Configure spam filter policies](https://learn.microsoft.com/en-us/defender-office-365/anti-spam-policies-configure)
- [Configure anti-phishing policies if you don't have Microsoft Defender for Office 365](https://learn.microsoft.com/en-us/defender-office-365/anti-phishing-policies-eop-configure)
- [Configure anti-phishing policies in Microsoft Defender for Office 365](https://learn.microsoft.com/en-us/defender-office-365/anti-phishing-policies-mdo-configure)
- [Set up Safe Attachments policies in Microsoft Defender for Office 365](https://learn.microsoft.com/en-us/defender-office-365/safe-attachments-policies-configure)

## Next Steps

To finish setup, apply these settings:

- In quarantine policy, open **Global policy**. Turn on your branding logo, display name, and disclaimer.
- Set **User frequency to 1 day** for quarantine notices.

## Related content

For more information about organization branding and notification settings, see [Quarantine policies](https://learn.microsoft.com/en-us/defender-office-365/quarantine-policies).
