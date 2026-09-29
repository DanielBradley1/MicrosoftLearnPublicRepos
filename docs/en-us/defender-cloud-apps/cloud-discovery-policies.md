<!-- Source: https://learn.microsoft.com/en-us/defender-cloud-apps/cloud-discovery-policies -->
<!-- Sitemap-Last-Modified: 2026-08-11 -->

# Create cloud discovery policies

You can create app discovery policies to alert you when new apps are detected. Defender for Cloud Apps also searches all the logs in your cloud discovery for anomalies. This article explains how to create and configure app discovery policies to monitor newly discovered apps, and how to use cloud discovery anomaly detection to identify unusual usage patterns in your environment.

## Creating an app discovery policy

Discovery policies enable you to set alerts that notify you when new apps are detected within your organization.

1. In the Microsoft Defender Portal, under **Cloud Apps**, go to **Policies** -> **Policy management**. Then select the **Shadow IT** tab.
2. Select **Create policy** and then select **App discovery policy**.

   ![Screenshot of the Shadow IT tab showing the Create policy menu with the App discovery policy option.](https://learn.microsoft.com/en-us/defender-cloud-apps/media/create-policy-from-shadow-it-tab.png)

3. Give your policy a name and description. If you want, you can base it on a template. For more information on policy templates, see [Control cloud apps with policies](https://learn.microsoft.com/en-us/defender-cloud-apps/control-cloud-apps-with-policies).
4. Set the **Severity** of the policy.
5. To set which discovered apps trigger this policy, add filters.
6. You can set a threshold for how sensitive the policy should be. Enable **Trigger a policy match if all the following occur on the same day**. You can set criteria that the app must exceed daily to match the policy. Select one of the following criteria:

   - Daily traffic
   - Downloaded data
   - Number of IP addresses
   - Number of transactions
   - Number of users
   - Uploaded data

7. Set a **Daily alert limit** under **Alerts**. Select if the alert is sent as an email. Then provide email addresses as needed.

   - Selecting **Save alert settings as the default for your organization** enables future policies to use these alert settings.
   - If you have default alert settings saved for your organization, you can select **Use your organization's default settings**.

8. Select **Governance** actions to apply when an app matches this policy. It can tag policies as **Sanctioned**, **Unsanctioned**, **Monitored**, or a custom tag.
9. Select **Create**.

Note

- Newly created discovery policies \(or policies with updated continuous reports\) trigger an alert once in 90 days per app per continuous report, regardless of whether there are existing alerts for the same app. So, for example, if you create a policy for discovering new popular apps, it might trigger additional alerts for apps that have already been discovered and alerted on.
- Data from **snapshot reports** don't trigger alerts in app discovery policies.

For example, if you're interested in discovering risky hosting apps found in your cloud environment, set your policy as follows:

Set the policy filters to discover any services found in the **hosting services** category, and that have a risk score of 1, indicating they're highly risky.

In the **Trigger a policy match if all the following occur on the same day** section, set the thresholds that should trigger an alert for a certain discovered app. For instance, alert only if over 100 users in the environment used the app and if they downloaded a certain amount of data from the service. Additionally, you can set the limit of daily alerts you wish to receive.

![Screenshot of app discovery policy settings showing filter and threshold options for risky hosting apps.](https://learn.microsoft.com/en-us/defender-cloud-apps/media/app-discovery-policy-example.png "app discovery policy example")

## Cloud discovery anomaly detection

Defender for Cloud Apps searches all the logs in your cloud discovery for anomalies. For instance, when a user, who never used Dropbox before, suddenly uploads 600 GB to it, or when there are a lot more transactions than usual on a particular app. The anomaly detection policy is enabled by default. It's not necessary to configure a new policy for it to work. However, you can fine-tune which types of anomalies you want to be alerted about in the default policy.

1. In the Microsoft Defender Portal, under **Cloud Apps**, go to **Policies** -> **Policy management**. Then select the **Shadow IT** tab.
2. Select **Create policy** and select **Cloud Discovery anomaly detection policy**.

   ![Screenshot of the Create policy menu with the Cloud Discovery anomaly detection policy option selected.](https://learn.microsoft.com/en-us/defender-cloud-apps/media/cloud-discovery-anomaly-detection-policy-menu.png "cloud discovery anomaly detection policy menu")

3. Give your policy a name and description. If you want, you can base it on a template, For more information on policy templates, see [Control cloud apps with policies](https://learn.microsoft.com/en-us/defender-cloud-apps/control-cloud-apps-with-policies).
4. To set which discovered apps trigger this policy, select **Add filters**.

   The filters are chosen from drop-down lists. To add filters, select **Add a filter**. To remove a filter, select the 'X'.
5. Under **Apply to** choose whether this policy applies **All continuous reports** or **Specific continuous reports**. Select whether the policy applies to **Users**, **IP addresses**, or both.

   [![Screenshot of Apply to settings for an app discovery policy with options for all or specific continuous reports and filters for users and IP addresses.](https://learn.microsoft.com/en-us/defender-cloud-apps/media/apply-to-continous-reports.png)](https://learn.microsoft.com/en-us/defender-cloud-apps/media/apply-to-continous-reports.png#lightbox)

   Important

   When you configure an app discovery policy and select **Apply to > All continuous reports**, multiple alerts are generated for each discovery stream, including the global stream which aggregates data from all sources. To control alert volume, select **Apply to > Specific continuous reports** and choose only the relevant streams for your policy. Learn more: [Defender for Cloud apps continuous risk assessment reports](https://learn.microsoft.com/en-us/defender-cloud-apps/set-up-cloud-discovery#snapshot-and-continuous-risk-assessment-reports)
6. Select the dates during which the anomalous activity occurred to trigger the alert under **Raise alerts only for suspicious activities occurring after date.**
7. Set a **Daily alert limit** under **Alerts**. Select if the alert is sent as an email. Then provide email addresses as needed.

   - Selecting **Save alert settings as the default for your organization** enables future policies to use these alert settings.
   - If you have default alert settings saved for your organization, you can select **Use your organization's default settings**.

8. Select **Create**.

   ![Screenshot of the new discovery anomaly policy page showing anomaly detection criteria and alert settings.](https://learn.microsoft.com/en-us/defender-cloud-apps/media/new-discovery-anomaly-policy.png "new discovery anomaly policy")

## Next steps

[User activity policies](https://learn.microsoft.com/en-us/defender-cloud-apps/user-activity-policies)

If you run into any problems, we're here to help. To get assistance or support for your product issue, please [open a support ticket](https://learn.microsoft.com/en-us/defender-xdr/contact-defender-support).
