<!-- Source: https://learn.microsoft.com/en-us/defender-endpoint/manage-suppression-rules -->
<!-- Sitemap-Last-Modified: 2026-07-29 -->

# Manage suppression rules

There might be scenarios where you need to suppress alerts from appearing in the portal. You can create suppression rules for specific alerts that are known to be innocuous such as known tools or processes in your organization. For more information on how to suppress alerts, see [Suppress alerts](https://learn.microsoft.com/en-us/defender-xdr/investigate-alerts?toc=/defender-endpoint/toc.json&bc=/defender-endpoint/breadcrumb/toc.json#manage-alerts).

You can view a list of all the suppression rules and manage them in one place. You can also turn an alert suppression rule on or off.

Important

Microsoft recommends that you use roles with the fewest permissions. This helps improve security for your organization. Global Administrator is a highly privileged role that should be limited to emergency scenarios when you can't use an existing role.

1. Sign in to the [Microsoft Defender portal](https://go.microsoft.com/fwlink/p/?linkid=2077139) using an account with the Security administrator or Global Administrator role assigned.
2. In the navigation pane, select **Settings** > **Endpoints** > **Rules** > **Alert suppression**. The list of suppression rules that users in your organization have created is displayed.
3. Select a rule by clicking on the check-box beside the rule name.
4. Click **Turn rule on**, **Edit rule**, or **Delete rule**. When making changes to a rule, you can choose to release alerts that the rule has already suppressed, regardless whether or not these alerts match the new criteria.

## View details of a suppression rule

To view the details of a suppression rule, perform the following steps:

1. In the navigation pane, select **Settings** > **Endpoints** > **Rules** > **Alert suppression**. The list of suppression rules that users in your organization have created is displayed.
2. Select a rule name. Details of the rule is displayed. You'll see the rule details such as status, scope, action, number of matching alerts, created by, and date when the rule was created. You can also view associated alerts and the rule conditions.

## Related content

- [Manage alerts](https://learn.microsoft.com/en-us/defender-xdr/investigate-alerts?toc=/defender-endpoint/toc.json&bc=/defender-endpoint/breadcrumb/toc.json#manage-alerts)
