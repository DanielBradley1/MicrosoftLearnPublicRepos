<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/copilot/people-skills-manage-skills-library -->
<!-- Sitemap-Last-Modified: 2026-07-09 -->

# Manage your skills library in People Skills

After completing the [initial setup](https://learn.microsoft.com/en-us/microsoft-365/copilot/people-skills-setup), you can return to the People Skills page in the Microsoft 365 Admin Center to manage the skills library and admin settings.

You can find People Skills setup page by visiting the Copilot page in the [Microsoft 365 admin center](https://admin.microsoft.com/adminportal/home#/featureexplorer) and selecting **People Skills in Microsoft Copilot**. Alternatively, you can find People Skills page under **Settings** > **Viva** > **Data Management**.

If you're looking for how to set up People Skills for the first time, see [Set up People Skills](https://learn.microsoft.com/en-us/microsoft-365/copilot/people-skills-setup).

## Options to manage your skills library

You can manage your skills library in the following ways:

- [Manage out-of-the-box library](https://learn.microsoft.com/en-us/microsoft-365/copilot/people-skills-manage-skills-library): Add and delete skills from a previously selected list of skills from the out-of-the-box library.
- [Manage custom skills](https://learn.microsoft.com/en-us/microsoft-365/copilot/people-skills-manage-custom-skill): Add custom skills if you haven't previously added them during the initial setup. You can also reimport custom skills, add new ones, or delete custom skills at any point.
- [Manage AI-restricted skills](https://learn.microsoft.com/en-us/microsoft-365/copilot/people-skills-manage-custom-skill): Mark certain skills as sensitive to restrict them from being returned by skills AI inferencing.
- [Import or export skills](https://learn.microsoft.com/en-us/microsoft-365/copilot/people-skills-import-export-skills): Import user skills from third-party platforms and export your custom skills library or confirmed user skills for each individual user in your tenant.
- People Skills removal and deletion: Permanently remove People Skills and all skills data from your tenant.

### Manage out-of-the-box skills library

You can view, add, or delete the skills that you selected from the out-of-the-box library. The more skills you include from the out-of-the-box library, the more specific AI-generated skill profiles are for the users. Our recommendation is to use all 16,000 skills, with a minimum of 500 skills.

To view, add, or delete the skills that you selected from the out-of-the-box library, follow these steps:

1. Navigate to the People Skills setup page and select *Skills*\* to manage your skills library.
2. Under **Skills**, select **People Skills Library**.
3. Review the list. You can also filter the list by domain or search by skill name.
4. To add skills, select **Add Skills**. You can filter by domain or search by skill name. Select **Add**.
5. To delete skills, select the skills you want to delete. You can filter by domain or search by skill name. Select **Delete skills**. Select **Delete** again to confirm you want to delete the selected skills.

   Note

   Deleting skills removes the skills and associated skills data from your organization and from your users' experience.
6. Select **Done**.

### Expand AI Skill Inferencing to Microsoft 365 E3 and E5 licensed users

Admins can turn on AI-powered skill inferencing for Microsoft 365 Enterprise E3 and E5 licensed users directly in the Microsoft 365 admin center. AI-powered skill inferencing is turned on by default for Copilot and Viva users and turned off by default for Microsoft 365 E3/E5 licensed users. Please note that Microsoft 365 E3 and E5 is not the same as Office 365 E3 and E5. Only Microsoft 365 E3 and E5 licenses are eligible for inferencing. [Learn more about the difference between Microsoft 365 and Office 365](https://www.microsoft.com/microsoft-365/enterprise/compare-microsoft-365-and-office-365). When an Admin turns on AI-powered skill inferencing for Microsoft 365 E3/E5 licensed users, it turns on inferencing for all Microsoft 365 E3/E5 licensed users in the organization.

Note

This control is only available to tenants with at least one Microsoft Copilot license. People Skills must be set up in your tenant before you can turn on this control. [Learn about People skills initial setup](https://learn.microsoft.com/en-us/microsoft-365/copilot/people-skills-setup)

Once AI-powered inferencing is turned on for Microsoft 365 E3/E5 licensed users, it may take up to 15 days for inferred skills to be added to their profiles. After the initial set of inferred Skills are added to Microsoft 365 E3/E5 licensed user's profiles, new inferred skills will be refreshed periodically, typically every 180 days.

#### Why would you want to use this control?

AI-powered skill inferencing is turned for Copilot and Viva users by default. Expanding AI-powered skill inferencing to Microsoft 365 E3/E5 licensed users means your organization will have better coverage of Skills data, resulting in richer workforce analytics for leaders, more robust results in People queries in Copilot and Agents, and may allow you to better meet your organization goals.

#### How to turn-on AI inferencing for Microsoft 365 E3/E5 users

See instructions for how to turn on AI-powered inferencing for Microsoft 365 E3/E5 licensed users:

Go to the Copilot page in the [Microsoft 365 admin center](https://admin.microsoft.com/Adminportal/Home#/copilot/overview) and select **Settings** > **Data access** and then **People Skills in Microsoft Copilot**. Alternatively, you can find People Skills page under **Settings** > **Viva** > **Data Management**.

![E3E5inferencing\_pic2.](https://learn.microsoft.com/en-us/microsoft-365/copilot/media/people-skills-manage-skills-library/e4.png)

1. On the **Manage People Skills for your organization** page, Select **Settings**
2. Select **Manage skill inferencing by AI**
3. Check the box to enable AI-powered inferencing for E3 and E5 licensed users, or uncheck the box if you'd like to turn disable it

### People Skills removal and deletion

Admins can permanently remove People Skills from their tenant by using the People Skills removal and deletion control on the Manage People Skills page in Admin Center. Use this control if your organization no longer wants to use People Skills and wants to remove all associated skills data.

Warning

Removing People Skills is permanent. Deleted data \(such as your organization’s skill library and user skills\) will not be restored if you set up People Skills again later.

#### What gets deleted

When you remove People Skills, the following data is permanently deleted from your tenant:

- Your organization’s skills library and all library data, including any custom skills.
- All users’ confirmed, inferred, and imported skills data.

**How deletion affects users and connected experiences**

After you remove People Skills:

- Users no longer see skills on their profile card.
- Skills data no longer flows into Microsoft Copilot, Microsoft Viva, or other Microsoft 365 skills experiences. For details, see [Where does People Skills data appear](https://learn.microsoft.com/en-us/microsoft-365/copilot/people-skills-overview).
- Most data is deleted within 48–72 hours. Skills data in Viva Learning can take up to one week to be fully deleted; however, the Viva Learning skills experience is turned off immediately.

#### Prerequisites

- People Skills must already be set up in your tenant. The control isn’t available to tenants that haven’t deployed People Skills. To setup People Skills, see [Set Up People Skills for Your Organization](https://learn.microsoft.com/en-us/microsoft-365/copilot/people-skills-setup)
- You must be a Global Administrator, Knowledge Admin or AI admin to use this control.

#### How to remove People Skills

To permanently remove People Skills from your tenant, follow these steps:

1. Go to the Copilot page in the [Microsoft 365 admin center](https://admin.microsoft.com/Adminportal/Home#/copilot/overview) and select **Settings** > **Data access** > **People Skills in Microsoft Copilot**. Alternatively, you can find the People Skills page under **Settings** > **Viva** > **Data Management**.
2. On the **Manage People Skills for your organization** page, select **Settings**.
3. Select **People Skills removal and deletion**.

   [![Screenshot that shows People Skills settings in the Microsoft 365 admin center.](https://learn.microsoft.com/en-us/microsoft-365/copilot/media/people-skills-manage-skills-library/delete-skills-admin-center-settings.png)](https://learn.microsoft.com/en-us/microsoft-365/copilot/media/people-skills-manage-skills-library/delete-skills-admin-center-settings.png#lightbox)

4. Review the confirmation dialog, which lists the data that will be removed. To confirm, follow the prompts in the dialog, and then select **Delete People Skills**.

   [![Screenshot that shows People Skills deletion dialog in the Microsoft 365 admin center.](https://learn.microsoft.com/en-us/microsoft-365/copilot/media/people-skills-manage-skills-library/delete-skills-confirmation-screen.png)](https://learn.microsoft.com/en-us/microsoft-365/copilot/media/people-skills-manage-skills-library/delete-skills-confirmation-screen.png#lightbox)

#### After deletion

After you confirm, deletion begins automatically. You don’t need to take any further action. Most data will be deleted within 48–72 hours. Skills data in Viva Learning can take up to one week to be fully deleted; however, the Viva Learning skills experience is turned off immediately.

If you want to use People Skills again later, you must complete the [initial setup](https://learn.microsoft.com/en-us/microsoft-365/copilot/people-skills-setup) again. We recommend waiting for at least 1 week before setting up People Skills again to ensure previous data is removed completely. Previously deleted skills library data and user skills data won’t be restored.
