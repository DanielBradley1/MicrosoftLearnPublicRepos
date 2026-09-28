<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/lti/teams-assignments-with-other-lms?view=o365-worldwide -->
<!-- Sitemap-Last-Modified: 2026-09-04 -->

# Use Microsoft Teams Assignments with any LTI 1.3® Advantage compliant LMS/VLE

Note

The classic Microsoft OneDrive, OneNote, Teams Assignments, and Reflect LTI apps have been replaced by the [new Microsoft 365 LTI](https://aka.ms/LMSAdminDocs). The classic apps will be sunset on September 17, 2026. After that date, the classic apps and any content links in courses will stop working. However, the files, notebooks, teams, meetings, and check-ins created by the classic app will continue to be accessible through Microsoft 365. For further guidance on moving your users and courses to the new Microsoft 365 LTI experiences and migrating content links, review the [migration guidance for the classic LTI apps](https://learn.microsoft.com/en-us/microsoft-365/lti/microsoft-365-lti-first-time-configuration#migration-guidance).

This guide provides steps for deploying the Microsoft Teams Assignments Learning Tools Interoperability \(LTI®\) app in any learning management system \(LMS\) that implements [the LTI® 1.3 Advantage](https://www.imsglobal.org/spec/lti/v1p3/impl/) standard as a fully conformant platform \(LTI® Advantage Complete\).

For an overview of all of the Microsoft integrations for LMS, see [Integrating Microsoft products with your LMS](https://learn.microsoft.com/en-us/microsoft-365/lti/).

## Request a Microsoft 365 sandbox environment

Important

If you're a **Microsoft Partner** that has an LTI® 1.3 Advantage compliant platform and wish to test deployment and functionality of the Teams Assignments LTI® tool on behalf of your customers, you need a Microsoft 365 Education sandbox environment to deploy and use the application.

**To request a Microsoft 365 sandbox environment:**

1. You first need a Microsoft Partner ID. Your Microsoft Partner ID appears in the top right corner next to your name when you log into the [Microsoft Partner Center](https://partner.microsoft.com). If you don't have one, you can obtain one by [joining the Microsoft AI Cloud Partner program](https://partner.microsoft.com/partnership).
2. When you have your Microsoft Parter ID, request a sandbox using one of the following methods based on your business type:

   - [Request a Microsoft 365 Education development/testing sandbox](https://m365edupartnerportal.powerappsportals.com/MSEDUIntegrationSignup/) as an Education ISV or SI partner who builds and supports integrations with Microsoft products and services.
   - [Request to join the Microsoft Global Training Partner program](https://m365edupartnerportal.powerappsportals.com/MSGTPSignup/) as a Training Partner who delivers training and support to customers on Microsoft products and services.

Note

The person who performs this integration should be an administrator of their LMS and have a Microsoft 365 Education \(school\) account.

## Deploy the Teams Assignments LTI® tool for your LMS

1. Go to the [Microsoft LMS Gateway](https://m365lti.edu.cloud.microsoft/admin/).
2. Select the **Go to Registration Portal** button.
3. Sign in with a *Microsoft 365 Education* account \(this is the account provided to you by your qualified education institution, or an account in your Edu Partner Microsoft 365 Education sandbox environment\).
4. After signing in, select **Add new registration**.
5. Select **Microsoft** **Teams Assignments**, and then select **Next**.
6. Enter an easily identifiable **Registration name**.
7. Select **Other** as the **LMS platform**, and then select **Next**. You're given a list of keys that need to be copied and pasted to your LMS site.
8. Leave the Microsoft LMS Gateway open in your browser tab and open the LMS site in another browser or tab and log in as an administrator.
9. Navigate to your platform's LTI Tool configurations and add a new LTI 1.3 tool.
10. Copy the values provided and save them. You need to add them to your LMS LTI® 1.3 tool configuration in the following steps. Hint: Check your LMS documentation to find the steps to create a new LTI® 1.3 registration and the correct fields to paste these values into.
11. On the **Microsoft LMS gateway** tab, select **LMS provided registration keys**.
12. Copy and paste the LTI® 1.3 platform values from the LMS tool registration into correct fields on Microsoft's **LMS provided registration keys** page. Hint: Check your LMS's documentation to find the correct place to get the registration values from your LMS.
13. Select **Next**.
14. Review the fields and values summarized on the **Review and add** page.
15. If there are no errors, select **Save and exit**.
16. When you see a message indicating successful registration, you've completed registration of the platform on the Microsoft LMS Gateway. You're now ready to continue configure common registration settings in the LTI® 1.3 tool in your LMS platform.

## Configure common registration settings

Every platform may have different options and steps for completing tool registration and adding placements for where the tool is launched within the platform. However, many common settings and steps are required to successfully deploy the app.

1. Enable the tool to be available to both instructor \(teacher\) and learner \(student\) roles in the platform.
2. Enable Deep Linking.
3. Enable Names and Roles Provisioning Service \(NRPS\).
4. Enable Assignment and Grading Services \(AGS\).
5. Confirm that the Name, Email, and Username of the user that launches the tool will be sent to the tool in the privacy settings.
6. Add the following custom parameters to be replaced by the platform at runtime. The LTI spec suggests the following variables be available, but platforms may have additional variables that are better suited based on definitions.
   | **Name** | **LTI/LIS Variable** | **Description** | **Example expression** |
   | --- | --- | --- | --- |
   | **t** | ResourceLink.title | Title of the resource lineItem \(assignment\) from the label property | t=$ResourceLink.title |
   | **dd** | ResourceLink.submission.endDateTime | Due date of the resource lineItem \(assignment\) from the endDateTime property | dd=$ResourceLink.submission.endDateTime |
   | **mp** | N/A | Maximum score possible for a lineItem submission form the scoreMaximum property | mp=$ResourceLink.lineItem.scoreMaximum |
   | **csid** | CourseOffering.sourcedId | Sourced ID for the course offering in the LMS | csid=$CourseOffering.sourcedId |
   | **ssid** | CourseSection.sourcedId | Sourced IDs for the course sections in the LMS | ssid=$CourseSection.sourcedId |
7. Add the secure **Icon URL** from the tool values copied if the platform requires this URL to display an icon.

## Add placements for the tool to launch from in the LMS platform

The Teams Assignments LTI® tool implements both a Resource Launch and a Deep Linking launch using the same **Target link URL** that is used in the core registration.

- **Resource Launch placement** - best used in a course context as a navigation menu item placement, or where course level resources are available to instructor and student member roles.
- **Deep Linking Launch placement** - best used in a new assignment or content activity placement \(external tool type of assignment/content\) where the tool, when launched by an instructor, creates a resource link that can be launched from the assignments or content activity list by instructors and teachers. The tool also creates a lineItem and sends scores back to the LMS to sync into its gradebook as Teams Assignments are graded by the instructor.
