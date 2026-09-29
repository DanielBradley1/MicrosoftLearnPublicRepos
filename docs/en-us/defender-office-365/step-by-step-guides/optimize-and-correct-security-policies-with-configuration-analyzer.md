<!-- Source: https://learn.microsoft.com/en-us/defender-office-365/step-by-step-guides/optimize-and-correct-security-policies-with-configuration-analyzer -->
<!-- Sitemap-Last-Modified: 2026-07-14 -->

# Optimize and correct threat policies with configuration analyzer

## Overview

Configuration analyzer is a central location for managing email threat policies in your tenant. Compare your settings with Standard and Strict recommendations. You can also apply changes and review past updates that affected your security posture.

## Prerequisites

- A Microsoft 365 organization with cloud mailboxes.
- Sufficient permissions \(Security Administrator role\)
- 5 minutes to perform the steps below.

## Compare settings and apply recommendations

Perform the following steps to compare your settings and apply recommended changes:

1. Navigate to [Configuration analyzer in the Microsoft Defender portal](https://security.microsoft.com/configurationAnalyzer).
2. Select **Standard recommendations** or **Strict recommendations** from the top menu.
3. If your settings differ from the chosen baseline, suggested changes appear.
4. Select a recommendation to view the suggested action, affected policy, and current setting.
5. To apply it, select **Apply recommendation**, then select **OK** to confirm.
6. To edit a policy directly, select **View policy** instead. A new tab opens with the policy for the selected recommendation.

## View historical configuration changes

In **Configuration analyzer**, select **Configuration drift analysis and history** from the top menu bar.

This page shows changes made to your threat policies in the selected time range. It also shows whether each change improved or lowered your security posture.

To learn more details about Configuration Analyzer, see [Configuration analyzer](https://learn.microsoft.com/en-us/defender-office-365/configuration-analyzer-for-security-policies).
