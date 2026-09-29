<!-- Source: https://learn.microsoft.com/en-us/defender-cloud-apps/saas-security-initiative -->
<!-- Sitemap-Last-Modified: 2026-08-08 -->

# Use the SaaS Security Initiative in Defender for Cloud Apps

This article shows you how to view and prioritize SaaS security recommendations in Microsoft Defender XDR by using the SaaS Security Initiative. Before you start, make sure you meet the [prerequisites](#prerequisites).

## Overview of the SaaS Security Initiative

The SaaS Security Initiative is the main hub for SaaS security posture management \(SSPM\). It gives you a central place to manage software as a service \(SaaS\) security best practices.

The initiative groups best-practice tips into 12 metrics. You can use these metrics to rank and act on security tasks. Focus on the metrics with the most impact to improve your SaaS security posture.

## How to use the SaaS Security Initiative

Watch the following video for an overview of how to use the SaaS Security Initiative.

<iframe src="https://learn-video.azurefd.net/vod/player?id=352cf722-69b2-45c1-932e-0ca32ef40fa0" allowfullscreen="true" data-linktype="external" frameborder="0"></iframe>

## Prerequisites

Before you view these recommendations, make sure you meet these requirements:

- Your organization must have Microsoft Defender for Cloud Apps licenses.
- The app you want to check must be connected to Defender for Cloud Apps. To learn how to connect apps and which connectors provide security tips, see [Connect apps to get visibility and control with Microsoft Defender for Cloud Apps](https://learn.microsoft.com/en-us/defender-cloud-apps/enable-instant-visibility-protection-and-governance-actions-for-your-apps).

## View SaaS Security Initiative recommendations

To view SaaS Security Initiative recommendations, perform the following steps:

1. In the Defender portal, go to **Exposure Management** and select **Initiatives**.
2. Select the **SaaS Security** initiative, and then select **Open Initiative Page**.

The page that appears lists the 12 metrics that categorize hundreds of best-practice recommendations.

[![Screenshot of the SaaS Security Initiative home page.](https://learn.microsoft.com/en-us/defender-cloud-apps/media/saas-securty-initiative/screenshot-of-the-saas-security-initiative-home-page.png)](https://learn.microsoft.com/en-us/defender-cloud-apps/media/saas-securty-initiative/screenshot-of-the-saas-security-initiative-home-page.png#lightbox)

Start with the metrics that have the highest **Impact on Initiative Score** level. This score combines the **Weight** of each item with the share of **Non-Compliant** items.

To track progress, set a **target score** for your security posture. Use this target as a benchmark to measure gains over time.

For example, to review tips for privileged access in SaaS apps, select **Missing Best Practices to Secure Privileged Access in SaaS Apps**. Then select any **Non-Compliant** item to see the fix steps.

## Related resources for SaaS Security Initiative

Use these resources to understand and build on the initiative results:

- Each metric lists its linked app connectors. Enable more connectors to get broader coverage. To see tips for a specific app, go to the **Security recommendations** tab and filter by that app.
- To learn more about Microsoft Security Exposure Management initiatives, see [Review security initiatives](https://learn.microsoft.com/en-us/security-exposure-management/initiatives).
