<!-- Source: https://learn.microsoft.com/en-us/defender-xdr/shield-predict-threats-manage -->
<!-- Sitemap-Last-Modified: 2026-07-02 -->

# Manage predictive shielding in Microsoft Defender \(Preview\)

Important

Some information in this article relates to a prereleased product which may be substantially modified before it's commercially released. Microsoft makes no warranties, expressed or implied, with respect to the information provided here.

Microsoft Defender uses predictive shielding \(Preview\) as a proactive defense strategy designed to anticipate and mitigate threats before they materialize. Learn [how predictive shielding works](https://learn.microsoft.com/en-us/defender-xdr/shield-predict-threats#how-predictive-shielding-works) to dynamically infer risk, anticipate attacker progression, and harden your environment.

This article describes how to manage predictive shielding so that you can enrich your prediction data and understand how predictive shielding actions are applied in your environment.

## Review predictive shielding details and results

The incident details page in Microsoft Defender includes built-in predictive shielding details. Use the incident graph and activity information to assess the predictive shielding impact and status.

Tip

To enrich your predictive shielding data, we recommend that you use the Microsoft Defender for Identity sensor to improve security insights and expand coverage. For more information, see [Enrich predictive shielding data](#enrich-predictive-shielding-data).

### Review the incident information

In the **Incidents** page, filter by the **Predictive Shielding** tag to find incidents where predictive shielding is applied.

[![Screenshot of the incident list filtered by the Predictive Shielding tag.](https://learn.microsoft.com/en-us/defender-xdr/media/shield-predict-threats-manage/shield-predict-threats-filter-incidents.png)](https://learn.microsoft.com/en-us/defender-xdr/media/shield-predict-threats-manage/shield-predict-threats-filter-incidents.png#lightbox)

Note

While the incident and alert details show historical data from the inception of the incident, the **Activities** tab shows a snapshot of the current status. For more information, see [Track the action status in the Activities tab](https://learn.microsoft.com/en-us/defender-xdr/autoad-results#track-the-action-status-in-the-activities-tab-preview).

You can then select the relevant incident, and review the incident graph to get the entire [attack story](https://learn.microsoft.com/en-us/defender-xdr/investigate-incidents#attack-story) and assess the predictive shielding impact and status.

[![Screenshot of predictive shielding data shown in the incident graph, attack story, and disruption summary card.](https://learn.microsoft.com/en-us/defender-xdr/media/shield-predict-threats-manage/shield-predict-threats-attack-story.png)](https://learn.microsoft.com/en-us/defender-xdr/media/shield-predict-threats-manage/shield-predict-threats-attack-story.png#lightbox)

You can also review the alert, and disruption information for predictive shielding details and results:

- In the alert details, view the **Predictive shielding** label and the specific threat type identified \(for example, ransomware\). If you subscribe to incident email notifications, these tags also appear in the emails.

  ![Screenshot of the alert details with the Predictive Shielding label.](https://learn.microsoft.com/en-us/defender-xdr/media/shield-predict-threats-manage/shield-predict-threats-alert-details.png)
- In the [disruption summary](https://learn.microsoft.com/en-us/defender-xdr/autoad-results#review-the-attack-disruption-summary-card), view the number of predictive shielding policies invoked as part of this incident, and the number of hardened devices across all policies.

  ![Screenshot of the disruption summary card showing predictive shielding details.](https://learn.microsoft.com/en-us/defender-xdr/media/shield-predict-threats-manage/shield-predict-threats-disruption-summary.png)

### Review the activity information

On the incident details page, select the **Activities** tab and filter by the **Response** category to get a live snapshot of the activities where predictive shielding actions are applied:

- Review the **Type** column to see the actions triggered by predictive shielding.

  In this example, the **Contain User**, **GPO Hardening**, and **SafeBoot Hardening** actions are applied as part of predictive shielding. Learn more about [predictive shielding actions](https://learn.microsoft.com/en-us/defender-xdr/shield-predict-threats#predictive-shielding-actions).

  [![Screenshot of the Activities tab filtered by Response category, showing predictive shielding actions.](https://learn.microsoft.com/en-us/defender-xdr/media/shield-predict-threats-manage/shield-predict-threats-view-activities.png)](https://learn.microsoft.com/en-us/defender-xdr/media/shield-predict-threats-manage/shield-predict-threats-view-activities.png#lightbox)
- Select the **Triggering alert** column to open the alert details pane, and review the alert that led to the predictive shielding action. For more information, see [Review the triggering alert information](#review-the-triggering-alert-information).
- Review the **Policy status** column to see which hardening policies are currently applied.

Note

The **Performed by** column indicates **Attack Disruption** both for attack disruption and predictive shielding actions. To understand which specific actions apply to predictive shielding, see the [Predictive shielding actions](https://learn.microsoft.com/en-us/defender-xdr/shield-predict-threats#predictive-shielding-actions).

- Select a specific action to open the activity details pane, which describes the activity, and shows the number of devices where the relevant policy is currently applied.

  ![Screenshot of the activity details pane showing the number of devices hardened by a predictive shielding action.](https://learn.microsoft.com/en-us/defender-xdr/media/shield-predict-threats-manage/shield-predict-threats-view-activity-details.png)

Tip

While the **Activities** tab displays actions that are specific to the current incident, the Action center displays all activites. To track predictive shielding actions in the Action center, see [Use the Action center](https://learn.microsoft.com/en-us/defender-xdr/m365d-action-center).

### Review the triggering alert information

To investigate the alert that triggered a specific predictive shielding action, select the triggering alert for the action you are investigating, either from the incident details pane or from the activity page.

[![Screenshot of the alert details pane showing relevant alert data.](https://learn.microsoft.com/en-us/defender-xdr/media/shield-predict-threats-manage/shield-predict-threats-view-triggering-alert.png)](https://learn.microsoft.com/en-us/defender-xdr/media/shield-predict-threats-manage/shield-predict-threats-view-triggering-alert.png#lightbox)

In the triggering alert details pane, you can review:

- Which assets are at risk.
- The triggering malicious activity from the **Alert chain**.
- The exposure data used to calculate this risk.

## Enrich predictive shielding data

We recommend that you use the Microsoft Defender for Identity sensor to improve security insights and expand coverage. Using the Defender for Identity sensor adds metadata like usernames, Active Directory details, and group memberships to alerts, making them more actionable.

To add the Defender for Identity sensor, see [Deploy Microsoft Defender for Identity](https://learn.microsoft.com/en-us/defender-for-identity/deploy/deploy-defender-identity).

### Enriched data example

This example scenario shows how enriched data enhances predictive shielding:

- Both Microsoft Defender for Endpoint and Microsoft Defender for Identity are enabled in the environment.
- An attacker gained a foothold on a jump box and conducted malicious activities that led to compromising a workstation named WSA.
- The enriched data reveals suspicious PowerShell activities on WSA, **indicating the attacker's intent to perform remote credential harvesting on another workstation, WSB**.
- This enrichment adds predictive data on the incident, and indicates intent for further compromise.

![Screenshot of enriched predictive shielding data in an incident, showing user and Active Directory details.](https://learn.microsoft.com/en-us/defender-xdr/media/shield-predict-threats-manage/shield-predict-threats-enriched-data.png)

## Track policy modifications in advanced hunting

You can use specific queries in [advanced hunting](https://learn.microsoft.com/en-us/defender-xdr/advanced-hunting-overview) to track policy modifications in your environment.

### Track enabled predictive shielding hardening policies

The following query retrieves events related to changes in predictive shielding hardening policies, and allows you to monitor when policies are enabled or disabled for specific domains. The query uses the [DisruptionAndResponseEvents table](https://learn.microsoft.com/en-us/defender-xdr/advanced-hunting-disruptionandresponseevents-table).

```kusto
  DisruptionAndResponseEvents
let hardeningPolicyType = 
let lookBackTime = 
DisruptionAndResponseEvents
| where Timestamp > lookBackTime
| where PolicyName == hardeningPolicyType
| where DomainName == domainName
| summarize arg_max(Timestamp, IsPolicyOn) by DeviceId
| where IsPolicyOn
```

### Track policy modification events in the environment

The following query retrieves policy modification events in the environment, including application and removal of hardening policies from devices onboarded to Defender for Endpoint. The query uses the [DisruptionAndResponseEvents table](https://learn.microsoft.com/en-us/defender-xdr/advanced-hunting-disruptionandresponseevents-table).

```kusto
  DisruptionAndResponseEvents
let hardeningPolicyType = dynamic(["GpoPrevention", "SafebootPrevention"]);
let lookBackTime = datetime("");
DisruptionAndResponseEvents
| where PolicyName in (hardeningPolicyType)
| where Timestamp > lookBackTime
| where ReportType == 'PolicyUpdated' and IsPolicyOn == '1'
| summarize arg_max(Timestamp, DeviceName) , PoliciesApplied = make_set(PolicyName)  by DeviceId
```

### Track blocked events related to predictive shielding hardening policies

The following query retrieves blocked events related to predictive shielding hardening policies, and allows you to monitor when specific actions were blocked on devices. The query uses the [DisruptionAndResponseEvents table](https://learn.microsoft.com/en-us/defender-xdr/advanced-hunting-disruptionandresponseevents-table).

```kusto
  DisruptionAndResponseEvents
let hardeningPolicyType = dynamic(["GpoPrevention", "SafebootPrevention"]);
DisruptionAndResponseEvents
| where PolicyName in (hardeningPolicyType)
| where ReportType == 'Prevented'
```

## Undo actions triggered by predictive shielding

You can undo an action that was applied as part of predictive shielding.

To undo an action, do one of the following:

- In the **Activity** tab of the incident, select the specific action you want to undo.
- [Undo an action from the Action center](https://learn.microsoft.com/en-us/defender-xdr/m365d-autoir-actions#undo-completed-actions).
