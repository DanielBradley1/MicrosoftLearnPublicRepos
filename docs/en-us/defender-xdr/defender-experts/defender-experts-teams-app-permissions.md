<!-- Source: https://learn.microsoft.com/en-us/defender-xdr/defender-experts/defender-experts-teams-app-permissions -->
<!-- Sitemap-Last-Modified: 2026-07-01 -->

# Troubleshooting issues with Microsoft Defender Experts app in Microsoft Teams

**Applies to:**

- [Microsoft Defender Experts MDR](https://learn.microsoft.com/en-us/defender-xdr/defender-experts/defender-experts-mdr-overview)
- [Microsoft Defender Experts Hunting](https://learn.microsoft.com/en-us/defender-xdr/defender-experts/defender-experts-hunting-overview)

You might encounter issues when setting up or using the Microsoft Defender Experts app in Microsoft Teams. Use the following guidance to diagnose and resolve them.

## App policy permissions

Note

Some screenshots use Defender Experts MDR as an example. Unless otherwise noted, the Teams app setup and troubleshooting steps are the same for Defender Experts Hunting.

The Microsoft Defender Experts app is available for Microsoft Teams by default. However, some environments might have limitations that block the app's installation because of app policy permissions in Teams. [Learn how to check Teams app permissions policies](#check-the-teams-app-permission-policies).

[![Screenshot of Teams showing a communication restriction notification for the Defender Experts channel.](https://learn.microsoft.com/en-us/defender-xdr/defender-experts/media/teams-restrictions-dexapp/teams-communication-issues.png)](https://learn.microsoft.com/en-us/defender-xdr/defender-experts/media/teams-restrictions-dexapp/teams-communication-issues.png#lightbox)

When you join the Defender Experts Teams channel, you can mention or tag the Defender Experts bot in the channel by typing *@Defender Experts*. If the bot doesn't show up in the list of suggestions, Teams permissions policies might prevent the app from functioning. To learn more, see [communicating with Defender Experts MDR](https://learn.microsoft.com/en-us/defender-xdr/defender-experts/defender-experts-mdr-communication).

The following screenshot is an example of the missing bot:

![Screenshot of the Teams mention list without the Defender Experts bot.](https://learn.microsoft.com/en-us/defender-xdr/defender-experts/media/teams-restrictions-dexapp/teams-app-bot.png)

### Check the Teams app permission policies

**To verify if the Teams permission policies are preventing the Defender Experts app from working, follow these steps.**

1. In Microsoft Teams, select **Apps** on the Teams workspace.

   ![Screenshot of the Apps icon in the Teams workspace navigation.](https://learn.microsoft.com/en-us/defender-xdr/defender-experts/media/teams-restrictions-dexapp/apps-teams-workspace.png)
2. Type **Defender Experts** in the search pane to see the Defender Experts app.
3. Select **Request** to request the Defender Experts service.

   ![Screenshot of the Defender Experts app request page in Microsoft Teams.](https://learn.microsoft.com/en-us/defender-xdr/defender-experts/media/teams-restrictions-dexapp/request-defender-experts.png)

**If you already have the Teams app installed and you encounter a policy issue, follow these steps:**

- Go to the **Manage apps** page for the Defender Experts app, and then go to the **User requests** tab. Learn more about [Manage app - Microsoft Teams admin center](https://admin.teams.microsoft.com/policies/manage-apps/81769126-d9ed-4a77-a1e8-2ab8107adf03/user-requests).

If you see the following notification, the Teams app permission policies prevent you from using the Defender Experts app:

```text
This app is blocked in app permission policies. To approve a user's app request, review the app permission policies assigned to them and allow the app in any policies where it's blocked.
```

![Screenshot of the Defender Experts app showing a blocked app permission policy notification in Teams.](https://learn.microsoft.com/en-us/defender-xdr/defender-experts/media/teams-restrictions-dexapp/app-permissions-blocked.png)

### Fix the Teams app permission policies

To fix the Teams app permission policy that stops the Defender Experts app from running, use one of the following options:

- [Change the policy that blocks the Defender Experts app from running](#change-the-policy-that-blocks-the-defender-experts-app-from-running)
- [Add a new policy that lets the Defender Experts app run](#add-a-new-policy-that-lets-the-defender-experts-app-run)

#### Change the policy that blocks the Defender Experts app from running

To change the policy that blocks the Defender Experts app, follow these steps:

1. Go to the [App permission policies page](https://admin.teams.microsoft.com/policies/app-permission). For more information, see [App permission policies - Microsoft Teams admin center](https://learn.microsoft.com/en-us/microsoftteams/teams-app-permission-policies).
2. Check each policy to see if **Microsoft apps** is set to **Allow specific apps and block all others**.

   ![Screenshot of the Microsoft apps policy set to Allow specific apps and block all others.](https://learn.microsoft.com/en-us/defender-xdr/defender-experts/media/teams-restrictions-dexapp/allow-apps-teams.png)
3. Select **Add apps**. On the panel, look for **Defender Experts**, and select **Allow**.

   ![Screenshot of the Add apps panel with the Defender Experts app set to Allow.](https://learn.microsoft.com/en-us/defender-xdr/defender-experts/media/teams-restrictions-dexapp/add-dex-app.png)

The change takes effect within 24 hours.

#### Add a new policy that lets the Defender Experts app run

To add a new app permission policy, follow these steps:

1. Go to the **App permission policies** page and then select **Add**.
2. In the panel, search for and select **Defender Experts**, and then select **Allow**.

   ![Screenshot of the app permission policy flyout panel with Defender Experts set to Allow.](https://learn.microsoft.com/en-us/defender-xdr/defender-experts/media/teams-restrictions-dexapp/add-dex-app-run.png)
3. Complete the rest of the fields as needed, and then select **Save**. If this policy is for a group of users, make sure that all the members in the channel are assigned to the policy. The change takes effect within 24 hours.

## Teams channel unavailable

You can't receive updates or chat with Defender Experts if the Managed Response or Hunting notification channel is archived or deleted. To learn more, see how to [archive](https://support.microsoft.com/office/archive-or-restore-a-channel-53c46491-a265-4391-a2a7-001c5026c9e5) or [restore a deleted channel](https://support.microsoft.com/office/delete-a-channel-in-microsoft-teams-973f9014-53db-4165-8ab4-365021fe36b7).

If the Teams app is deleted, you can reconfigure it again in the Defender portal by going to **Settings** > **Defender Experts** > **Teams**.

## Disabled Unified Group creation

Teams channel creation might fail if Microsoft 365 Unified Group creation is disabled in your organization.

The Defender Experts teams onboarding flow requires the creation of Microsoft 365 Unified Group during Teams provisioning on-behalf-of user performing the onboarding. If Unified group creation \(`EnableGroupCreation`\) is disabled in the tenant, the Teams team can't be created.

To verify your organization’s group settings, use one of the following options:

- **Using Graph Explorer:** Use [List group settings Graph API](https://developer.microsoft.com/en-us/graph/graph-explorer?request=groupSettings&method=GET&version=v1.0&GraphUrl=https://graph.microsoft.com) to review Microsoft 365 Group settings and determine whether the `EnableGroupCreation` setting is set to `false`.
- **Using PowerShell:** Use the [Microsoft Graph PowerShell module](https://learn.microsoft.com/en-us/previous-versions/microsoft-365/solutions/manage-creation-of-groups#step-2-run-powershell-commands) to view and update your tenant configurations and allow the onboarding user to create Unified Groups before retrying setup.

## Related content

- [Communicating with Defender Experts MDR](https://learn.microsoft.com/en-us/defender-xdr/defender-experts/defender-experts-mdr-communication)
- [Get started with Microsoft Defender Experts MDR](https://learn.microsoft.com/en-us/defender-xdr/defender-experts/defender-experts-mdr-get-started)
