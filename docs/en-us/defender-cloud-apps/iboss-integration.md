<!-- Source: https://learn.microsoft.com/en-us/defender-cloud-apps/iboss-integration -->
<!-- Sitemap-Last-Modified: 2026-08-11 -->

# Integrate Defender for Cloud Apps with iboss

If you work with both Defender for Cloud Apps and iboss, you can integrate the two products to enhance your security cloud discovery experience. iboss is a standalone secure cloud gateway that monitors your organization's traffic and enables you to set policies that block transactions. Together, Defender for Cloud Apps and iboss provide the following capabilities:

- Seamless deployment of cloud discovery - Use iboss to proxy your traffic and send it to Defender for Cloud Apps. Proxying traffic through iboss eliminates the need for installation of log collectors on your network endpoints to enable cloud discovery.
- iboss's block capabilities are automatically applied on apps you set as unsanctioned in Defender for Cloud Apps.
- Enhance your iboss admin portal with the Defender for Cloud Apps risk assessment of the top 100 cloud apps in your organization, which can be viewed directly in the iboss admin portal.

## Prerequisites

Before you begin, make sure you have the following licenses:

- A valid license for Microsoft Defender for Cloud Apps
- A valid license for iboss secure cloud gateway \(release 9.1.100.0 or later\)

## Deploy the iboss integration

To deploy the iboss integration with Defender for Cloud Apps, complete the following steps:

1. In the [Microsoft Defender Portal](https://security.microsoft.com/), do the following integration steps:

   1. Select **Settings**. Then choose **Cloud Apps**.
   2. Under **Cloud Discovery**, select **Automatic log upload**. Then select **+Add data source**.
   3. In the **Add data source** page, enter the following settings:

      - Name = iboss
      - Source = iboss Secure Cloud Gateway
      - Receiver type = Syslog - UDP


      ![Screenshot of the Add data source page with iboss Secure Cloud Gateway selected and Syslog UDP receiver type configured.](https://learn.microsoft.com/en-us/defender-cloud-apps/media/iboss-integration.png)

   4. Select **View sample of expected log file**. Then select **Download sample log** to view a sample discovery log, and make sure it matches your logs.

2. Investigate cloud apps discovered on your network. For more information and investigation steps, see [Working with cloud discovery](https://learn.microsoft.com/en-us/defender-cloud-apps/working-with-cloud-discovery-data).
3. Any app that you set as unsanctioned in Defender for Cloud Apps will be pinged by iboss once every ten minutes, and then automatically blocked by iboss. For more information about unsanctioning apps, see [Sanctioning/unsanctioning an app](https://learn.microsoft.com/en-us/defender-cloud-apps/governance-discovery#sanctioningunsanctioning-an-app).
4. To configure iboss to send traffic logs to Microsoft Defender for Cloud Apps, contact iboss support.

## Next steps

[Control cloud apps with policies](https://learn.microsoft.com/en-us/defender-cloud-apps/control-cloud-apps-with-policies)

If you run into any problems, we're here to help. To get assistance or support for your product issue, please [open a support ticket](https://learn.microsoft.com/en-us/defender-xdr/contact-defender-support).
