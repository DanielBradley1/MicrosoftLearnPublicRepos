<!-- Source: https://learn.microsoft.com/en-us/intune/app-management/protection/validate-policy-setup -->
<!-- Sitemap-Last-Modified: 2026-04-14 -->

# How to Validate Your App Protection Policy Setup in Microsoft Intune

Validate that your app protection policy is correctly set up and working. This guidance applies to app protection policies in the portal.

## Checking for symptoms

Users are unlikely to report issues since app protection is a data protection tool. If there's a problem with the app protection configuration, the user will have unrestricted access, as they would have without app protection, and they wouldn't know there's an issue. For this reason, we recommend you validate your app protection configuration by piloting your app protection policies with a small group of users who can deliberately test the app protection restrictions.

## What to check

If testing shows that your app protection policy behavior isn't functioning as expected, check these items:

- Are the users licensed for app protection?
- Are the users licensed for Microsoft 365?
- Is the status of each of the users' app protection apps as expected. The possible statuses for the apps are **Checked in** and **Not checked in**.

### User app protection status

1. Sign in to the [Microsoft Intune admin center](https://go.microsoft.com/fwlink/?linkid=2109431).
2. Select **Apps** > **Monitor** > **App protection status**, and then select the **Assigned users** tile.
3. On the **App reporting** page, select **Select user** to bring up a list of users and groups.
4. Search for and select a user from the list, then choose **Select user**. At the top of the **App reporting** pane, you can see whether the user is licensed for app protection. You can also see whether the user has a license for Microsoft 365 and the app status for all of the user's devices.

## What to do

Here are the actions to take based on the user status:

- If the user isn't licensed for app protection, assign an [Intune license](https://learn.microsoft.com/en-us/intune/fundamentals/licensing) to the user.
- If the user isn't licensed for Microsoft 365, get a [license](https://learn.microsoft.com/en-us/intune/fundamentals/licensing) for the user.
- If a user's app is listed as **Not checked in**, check if you've correctly configured an [app protection policy](https://learn.microsoft.com/en-us/intune/app-management/protection/validate-policy-setup) for that app.
- Ensure that these conditions apply across all users to which you want [app protection policies](https://learn.microsoft.com/en-us/intune/app-management/protection/monitor-policies) to apply.

## See also

- [What is Intune app protection policy?](https://learn.microsoft.com/en-us/intune/app-management/protection/create-policy)
- [Licenses that include Intune](https://learn.microsoft.com/en-us/intune/fundamentals/licensing)
- [Assign licenses to users so they can enroll devices in Intune](https://learn.microsoft.com/en-us/intune/fundamentals/assign-licenses)
- [How to validate your app protection policy setup](https://learn.microsoft.com/en-us/intune/app-management/protection/validate-policy-setup)
- [How to monitor app protection policies](https://learn.microsoft.com/en-us/intune/app-management/protection/monitor-policies)
