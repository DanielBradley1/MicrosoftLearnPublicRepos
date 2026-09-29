<!-- Source: https://learn.microsoft.com/en-us/defender-office-365/attack-simulation-training-settings -->
<!-- Sitemap-Last-Modified: 2026-08-24 -->

# Global settings in Attack simulation training

Tip

*Did you know you can try the features in Microsoft Defender for Office 365 Plan 2 for free?* Use the 90-day Defender for Office 365 trial at the [Microsoft Defender portal trials hub](https://security.microsoft.com/trialHorizontalHub?sku=MDO&ref=DocsRef). Learn about who can sign up and trial terms on [Try Microsoft Defender for Office 365](https://learn.microsoft.com/en-us/defender-office-365/try-microsoft-defender-for-office-365).

In Attack simulation training in Microsoft 365 E5 or Microsoft Defender for Office 365 Plan 2, the **Settings** tab contains settings that affect all simulations:

- **Repeat offender threshold**: A *repeat offender* is someone who gives up their credentials in multiple consecutive simulations. How many simulations in a row constitute a repeat offender is determined by the repeat offender threshold. Information about repeat offenders appears in the following locations:

  - The [Repeat offenders card on the Overview tab](https://learn.microsoft.com/en-us/defender-office-365/attack-simulation-training-insights#repeat-offenders-card) and the [Repeat offenders tab in the Attack simulation report](https://learn.microsoft.com/en-us/defender-office-365/attack-simulation-training-insights#repeat-offenders-tab-for-the-attack-simulation-report).
  - When you select users in [target users for simulations](https://learn.microsoft.com/en-us/defender-office-365/attack-simulation-training-simulation-automations#target-users), [target users for simulation automations](https://learn.microsoft.com/en-us/defender-office-365/attack-simulation-training-simulation-automations#target-users), and [target users for training campaigns](https://learn.microsoft.com/en-us/defender-office-365/attack-simulation-training-training-campaigns#target-users), you can find and filter repeat offenders.

- **Training threshold**: In [Training campaigns](https://learn.microsoft.com/en-us/defender-office-365/attack-simulation-training-training-campaigns), the *training threshold* specifies a time period in days to prevent users from having the same training modules assigned to them. Specifically, a training module isn't reassigned to users who completed the module during the training threshold, nor is a training module assigned to users who haven't completed modules assigned during the training threshold. For more information, see [Set the training threshold time period](https://learn.microsoft.com/en-us/defender-office-365/attack-simulation-training-training-campaigns#set-the-training-threshold).
- **View exclude simulations from reporting**: After a simulation has completed, you can exclude the results of the simulation from reporting. For instructions, see [Exclude completed simulations from reporting](https://learn.microsoft.com/en-us/defender-office-365/attack-simulation-training-simulations#exclude-completed-simulations-from-reporting). You can use the **View all** link in the **Simulations excluded from reporting** section to see excluded simulations on the **Simulations** tab.

To get to the **Settings** tab, do the following steps:

1. Open the Microsoft Defender portal at [https://security.microsoft.com](https://security.microsoft.com).
2. Go to **Email & collaboration** > **Attack simulation training**.
3. Select the **Settings** tab.

To go directly to the **Settings** tab, use [https://security.microsoft.com/attacksimulator?viewid=setting](https://security.microsoft.com/attacksimulator?viewid=setting).

For getting started information about Attack simulation training, see [Get started using Attack simulation training](https://learn.microsoft.com/en-us/defender-office-365/attack-simulation-training-get-started).

## Configure the repeat offender threshold

To configure the repeat offender threshold, use the box in the **Repeat offender threshold** section on the **Settings** tab. The default value is 2.

## Configure the training threshold

To configure the training threshold, use the box in the **Training threshold** section on the **Settings** tab. The default value is 90 days.

The training threshold starts from the time that modules are assigned to users.

We recommend that the training threshold is greater than the number of days users have to complete a training module.

To remove the training threshold and always assign training, regardless of whether a user has already completed or been assigned a training, set value to 0.

## View simulations excluded from reporting

To view completed simulations that have been excluded from reporting on the **Settings** tab, select the **View all** link in the **Simulations excluded from reporting** section. This link takes you to the **Simulations** tab at [https://security.microsoft.com/attacksimulator?viewid=simulations](https://security.microsoft.com/attacksimulator?viewid=simulations) where **Show excluded simulations** is automatically toggled on ![](https://learn.microsoft.com/en-us/defender-office-365/media/scc-toggle-on.png) .

On the **Simulations** tab, both excluded *and* included completed simulations are shown on the **Simulations** tab together. You can tell the difference by the **Status** values \(**Excluded** vs. **Completed**\).

If you go directly to the **Simulations** tab and manually toggle **Show excluded simulations** on ![](https://learn.microsoft.com/en-us/defender-office-365/media/scc-toggle-on.png) , *only* excluded simulations are shown.

To exclude completed simulations from reporting, see [Exclude completed simulations from reporting](https://learn.microsoft.com/en-us/defender-office-365/attack-simulation-training-simulations#exclude-completed-simulations-from-reporting).

## Related content

- [Get started using Attack simulation training](https://learn.microsoft.com/en-us/defender-office-365/attack-simulation-training-get-started)
- [Simulate a phishing attack with Attack simulation training](https://learn.microsoft.com/en-us/defender-office-365/attack-simulation-training-simulations)
- [Simulation automations for Attack simulation training](https://learn.microsoft.com/en-us/defender-office-365/attack-simulation-training-simulation-automations)
