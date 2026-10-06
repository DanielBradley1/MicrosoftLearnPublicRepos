<!-- Source: https://learn.microsoft.com/en-us/defender-cloud-apps/app-governance-trial-user-guide -->
<!-- Sitemap-Last-Modified: 2025-08-18 -->

# Get started with app governance in Defender for Cloud Apps

App governance solutions require a deep understanding of app behavior within an environment to identify and address activities that fall within a tolerance level that requires more review to assess malicious intent. When layered over Defender for Cloud Apps, app governance gives you in-depth governance against risky app behavior in your environment.

Use this quickstart to begin using app governance features in Microsoft Defender for Cloud Apps.

## Prerequisites

- If you haven’t already, [sign up for app governance](https://security.microsoft.com/cloudapps/settings?tabid=activateAppG) and complete the steps to add it to your tenant. After you've signed up for app governance, you'll need to wait up to 10 hours to see and use the product.

  For more information, see [Turn on app governance for Microsoft Defender for Cloud Apps](https://learn.microsoft.com/en-us/defender-cloud-apps/app-governance-get-started).
- Your sign-in account must have a supported [app governance administrator role](https://learn.microsoft.com/en-us/defender-cloud-apps/app-governance-get-started#roles) to view any app governance data.
- To use full functionality for app governance alerts, you must have provisioned both Defender for Cloud Apps and Microsoft Defender by accessing their respective portals at least once.

## Step 1: Get visibility and insights

Start by using the following steps to get visibility and insights about your apps:

1. **Sign in**: In your browser, go to the **Microsoft Defender XDR > Cloud Apps > [App governance](https://aka.ms/appgovernance)** page.
2. **[Determine security posture](https://learn.microsoft.com/en-us/defender-cloud-apps/app-governance-visibility-insights-security-posture)**: Use the data on the **App governance > Overview** tab to assess the security posture of your apps and incidents in your tenant. View details like how many overprivileged apps are in your tenant, the number of active incidents, the total Graph API data access, and more.

   Tip

   You can also view app governance-related recommendations in [Secure Score](https://security.microsoft.com/securescore?viewid=overview&tid=b5304409-74ae-42bf-a3e3-d62da4845129) to help you holistically manage your posture.
3. **[View your apps](https://learn.microsoft.com/en-us/defender-cloud-apps/app-governance-visibility-insights-view-apps)**: Sort the data on the **App governance** tabs by apps with high data usage or number of consents given, or filter by high privileged apps, unused apps, apps with unused permissions, or unverified publisher, and more.

   Use these sorting and filtering options to gain deeper insights into your OAuth apps, including relevant app metadata and usage data.
4. **[Get detailed app information](https://learn.microsoft.com/en-us/defender-cloud-apps/app-governance-visibility-insights-view-apps#get-detailed-information-about-an-app)**: On the **App governance** tabs, select an app in the grid to view an app details page. Investigate [priority account](https://learn.microsoft.com/en-us/microsoft-365/admin/setup/priority-accounts) data usage for a specific app, trace exactly whose data is being accessed, which permissions are being used, and which permissions aren't used.

For more information, see [Get started with visibility and insights](https://learn.microsoft.com/en-us/defender-cloud-apps/app-governance-visibility-insights-overview#get-started-with-visibility-and-insights).

## Step 2: Implement app policies

App governance uses machine learning-based detection algorithms to detect anomalous app behavior in your environment, and then generates alerts that you can see, investigate, and resolve.

Beyond this built-in detection capability, use a set of default policy templates or create your own app policies to generate other alerts.

Policies for app and user patterns and behaviors can protect your users from using noncompliant or malicious apps, and limit the access of risky apps to your tenant data.

App governance supports the following types of policies:

| Policy type | Description |
| --- | --- |
| **Predefined policies** | App governance is equipped with a set of predefined policies tailored to your environment. Predefined policies allow you to start monitoring your apps even before you set up any policies. Use predefined policies to ensure that you're notified of any app anomalies early on. |
| **User defined policies** | In addition to predefined policies, admins can also use the available conditions to create their custom policies or pick from the available recommended policies. |

To see your list of current app governance policies, go to the **Microsoft Defender XDR > Cloud apps > App governance > Policies** tab.

Note

Built-in threat detection policies are *not* listed on the **App governance** page. For more information, see [Investigate threat detection alerts](https://learn.microsoft.com/en-us/defender-cloud-apps/app-governance-anomaly-detection-alerts).

**To implement app policies**:

1. **[Work with predefined policies](https://learn.microsoft.com/en-us/defender-cloud-apps/app-governance-app-policies-overview#work-with-predefined-policies)**: App governance contains a set of out of the box policies to detect anomalous app behaviors. These policies are activated by default, but you can deactivate them if you choose to.
2. **[Create app policies:](https://learn.microsoft.com/en-us/defender-cloud-apps/app-governance-app-policies-create)** App governance offers over 20 policy conditions and templates for you to use. App governance policies help you:

   - Specify conditions by which app governance can alert you to app behavior for automatic or manual remediation.
   - Implement the app compliance policies for your organization.

3. **[Manage app policies](https://learn.microsoft.com/en-us/defender-cloud-apps/app-governance-app-policies-create#manage-app-policies)**: To keep up with the latest apps your organization is using, respond to new app-based attacks, and for ongoing changes to your app compliance needs, you might need to manage your app policies as follows:

   - Create new policies targeted at new apps
   - Change the status of an existing policy \(active, inactive, audit mode\)
   - Change the conditions of an existing policy
   - Change the actions of an existing policy for autoremediation of alerts

For more information, see [Learn about app policies](https://learn.microsoft.com/en-us/defender-cloud-apps/app-governance-app-policies-overview).

## Step 3: Detect and remediate app threats

Use app governance to monitor the threat alerts that are generated by built-in app governance detection methods for malicious app activities and policy-based alerts generated by active app policies that you create.

These alerts can indicate anomalies in app activity and when noncompliant, malicious, or risky apps are used. You can also use patterns in alerts to create new app policies or modify the settings of existing policies for more restrictive actions.

You can also remediate alerts, manually after investigation, or automatically through the action settings on active app policies.

**Do any of the following steps to detect and remediate threats**:

- **[Get started with app threat detection and remediation:](https://learn.microsoft.com/en-us/defender-cloud-apps/app-governance-detect-remediate-overview#view-alerts)** App governance collects threat alerts that are generated by built-in, machine-learning-driven app governance detection methods. The threat alerts are based on malicious app activities and policy-based alerts generated by active app policies that you create.
- **[Monitor and respond to apps with unusual data usage:](https://learn.microsoft.com/en-us/defender-cloud-apps/app-governance-detect-remediate-overview#monitor-and-respond-to-apps-with-unusual-data-usage)** App governance provides data usage information that can help you identify unwanted and potentially malicious app activity.
- **[Investigate anomaly detection alerts:](https://learn.microsoft.com/en-us/defender-cloud-apps/app-governance-anomaly-detection-alerts)** App governance provides security detections and alerts for malicious activities. The purpose of this guide is to provide you with general and practical information on each alert, to help with your investigation and remediation tasks.
- [**Remediate app threats:**](https://learn.microsoft.com/en-us/defender-cloud-apps/app-governance-manage-alerts) You remediate harmful app and app activity identified by app governance alerts in the Defender portal.

For more information, see [Learn about app threat detection and remediation](https://learn.microsoft.com/en-us/defender-cloud-apps/app-governance-detect-remediate-overview).

## Next steps

[Frequently asked questions about app governance](https://learn.microsoft.com/en-us/defender-cloud-apps/app-governance-faq)
