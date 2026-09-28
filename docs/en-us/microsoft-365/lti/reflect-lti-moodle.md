<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/lti/reflect-lti-moodle?view=o365-worldwide -->
<!-- Sitemap-Last-Modified: 2026-01-16 -->

# Integrate Microsoft Reflect LTI with Moodle

Note

The classic Microsoft OneDrive, OneNote, Teams Assignments, and Reflect LTI apps have been replaced by the [new Microsoft 365 LTI](https://aka.ms/LMSAdminDocs). The classic apps will be sunset on September 17, 2026. After that date, the classic apps and any content links in courses will stop working. However, the files, notebooks, teams, meetings, and check-ins created by the classic app will continue to be accessible through Microsoft 365. For further guidance on moving your users and courses to the new Microsoft 365 LTI experiences and migrating content links, review the [migration guidance for the classic LTI apps](https://learn.microsoft.com/en-us/microsoft-365/lti/microsoft-365-lti-first-time-configuration#migration-guidance).

[Microsoft Reflect](https://reflect.microsoft.com) is a wellbeing app designed to foster connection, expression, and learning by promoting self-awareness, empathy, and emotional growth.

Reflect LTI integration with Moodle is designed in compliance with the latest Learning Tools Interoperability \(LTI\) standards, ensuring strong security and straightforward installation within your Moodle site.

Integrate Reflect into Moodle to create impactful check-ins, gain wellbeing insights, and build a happier, healthier learning community.

## One-time setup by administrator

Note

This section provides IT admins steps for registering the Reflect LTI app for Moodle.

The person performing this initial registration should be an administrator of the Moodle site and Microsoft 365 tenant.

1. Sign in with a *Microsoft 365 administrator account* to the [Microsoft LTI Registration Portal](https://m365lti.edu.cloud.microsoft/admin/registration).
2. Select **Add new registration**.
3. Select **Microsoft Reflect** and then select **Next**.
4. Enter a friendly **Registration** name like *Reflect for Moodle* and select **Moodle** as the LMS platform. Select **Next**.
5. You're given a list of keys that need to be added to your Moodle site.
6. Open your Moodle site in another tab. ***Don't*** close the Microsoft LTI portal tab.
7. On Moodle, navigate to **Site administration** > **Plugins** and select **External tool** then **Manage tools**.
8. Select **Configure a tool manually** and enter the values listed in the table:
   | Field on Moodle | Value |
   | --- | --- |
   | Tool name | Microsoft Reflect |
   | Tool URL | [https://reflect.microsoft.com/app](https://reflect.microsoft.com/app) |
   | LTI version | LTI 1.3 |
   | Initiate login URL | Copy the **Open ID connection URL** value from Microsoft LTI keys. |
   | Redirection URI\(s\) | Copy the **Redirect URL** value from Microsoft LTI keys. |
9. Select the **Save changes** button.
10. In the **Tools** section, on the new **Microsoft Reflect** tile, select the **View configuration details** icon to view a modal with the configuration details for the Microsoft LTI portal.
11. On the **Microsoft LTI portal** tab, select **Next** to navigate to **LMS provided registration keys**. Enter the values listed in the table:
    | Field on Microsoft LTI registration portal | Value |
    | --- | --- |
    | Issuer ID URL | Copy the **Platform ID** value from Moodle tool configuration details. |
    | Client ID | Copy the **Client ID** value from Moodle tool configuration details. |
    | Keyset URL | Copy the **Public keyset URL** value from Moodle tool configuration details. |
    | Platform authentication URL | Copy the **Authentication request URL** value from Moodle tool configuration details. |
    | Deployment ID | Copy the **Deployment ID** value from Moodle tool configuration details. |
    | Access token URL | Copy the **Access token URL** value from Moodle tool configuration details. |
12. Select **Next** in the Microsoft LTI registration portal tab.
13. Review the **Review and save** page. If there are no errors, select **Save and exit**. You should see a message indicating successful registration.

Reflect is now installed and ready to use on your Moodle site after teachers add it to their courses.

## Add Reflect to a course as the course teacher

Important

After the initial setup of Reflect as an LTI external tool in your Moodle site, course teachers need to add it to their courses to use it with their students.

1. On Moodle, navigate to your course and in the course navigation, select **More** > **LTI External tools**.
2. Find **Microsoft Reflect** and turn on the **Show in activity chooser** toggle.
3. Navigate back to the course, ensure you are in **Edit mode**, and select **Add an activity or resource** in the **General** section.
4. Search for **Microsoft Reflect** and select it.
5. Enter **Microsoft Reflect** as the **Activity name**.
6. Select **Save and return to course**.

Reflect is now installed and ready to use in your course by both teachers and students.

## Ongoing use by course teachers and students

1. After the initial course setup, teachers and students will find a link to Reflect in the **General** section.
2. On their first access, they need to sign in using their Microsoft account to get started.
3. Course teachers can [create and share check-ins](https://support.microsoft.com/topic/c6cbbacc-5655-450e-bca9-988ddc506017).
4. Once check-ins are created, course students can access and respond to them by navigating to their Reflect link.

Tip

[Explore the Educator Toolkit](https://reflect.microsoft.com/home/resources) for resources that can help educators bring the magic of Reflect to students and share it with peers.

## Recommended browser settings

- Cookies should be allowed for Microsoft Reflect.
- Popups shouldn't be blocked for Microsoft Reflect.

Note

Cookies aren't allowed by default in the Chrome browser incognito mode and will need to be allowed.

Microsoft Reflect LTI works in the private mode in Microsoft Edge browser. Ensure that you haven't blocked cookies, which are allowed by default.
