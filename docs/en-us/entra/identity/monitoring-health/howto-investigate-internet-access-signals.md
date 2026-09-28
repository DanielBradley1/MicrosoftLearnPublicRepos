<!-- Source: https://learn.microsoft.com/en-us/entra/identity/monitoring-health/howto-investigate-internet-access-signals -->
<!-- Sitemap-Last-Modified: 2026-09-14 -->

# Investigate the internet applications blocked by Entra Internet Access policy

Microsoft Entra Health monitoring provides a set of tenant-level health metrics you can monitor and alerts when a potential issue or failure condition is detected. There are multiple health scenarios that can be monitored, including internet applications blocked by Microsoft Entra Internet Access policy.

To learn more about how Microsoft Entra Health works, see:

- [What is Microsoft Entra Health?](https://learn.microsoft.com/en-us/entra/identity/monitoring-health/concept-microsoft-entra-health)
- [How to investigate Microsoft Entra health monitoring signals and alerts](https://learn.microsoft.com/en-us/entra/identity/monitoring-health/howto-investigate-health-scenario-alerts)

This article describes the health metrics related to internet applications blocked by Microsoft Entra Internet Access policies and how to troubleshoot a potential issue when you receive an alert.

This scenario:

- Aggregates the number of unique users accessing internet applications successfully.
- Aggregates the number of unique users who failed to access internet applications.
- Aggregates the number of unique internet applications accessed successfully.
- Aggregates the number of failed accesses to unique internet applications.

## Prerequisites

There are different roles, permissions, and license requirements to view health monitoring signals and configure and receive alerts. We recommend using a role with least privilege access to align with the [Zero Trust guidance](https://learn.microsoft.com/en-us/security/zero-trust/zero-trust-overview).

- A tenant with a [Microsoft Entra P1 or P2 license](https://learn.microsoft.com/en-us/entra/fundamentals/get-started-premium) is required to *view* the Microsoft Entra health scenario monitoring signals.
- A tenant with both a non-trial [Microsoft Entra P1 or P2 license](https://learn.microsoft.com/en-us/entra/fundamentals/get-started-premium) *and* at least 100 monthly active users is required to *view alerts* and *receive alert notifications*.
- A tenant with a Microsoft Entra Internet Access license is required. For details, see the licensing section of [What is Global Secure Access?](https://learn.microsoft.com/en-us/entra/global-secure-access/overview-what-is-global-secure-access).
- The [Reports Reader](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#reports-reader) role is the least privileged role required to *view scenario monitoring signals, alerts, and alert configurations*.
- The [Helpdesk Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#helpdesk-administrator) is the least privileged role required to *update alerts* and *update alert notification configurations*.
- The `HealthMonitoringAlert.Read.All` permission is required to *view the alerts using the Microsoft Graph API*.
- The `HealthMonitoringAlert.ReadWrite.All` permission is required to *view and modify the alerts using the Microsoft Graph API*.
- For a full list of roles, see [Least privileged role by task](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/delegate-by-task#microsoft-entra-health-least-privileged-roles).
- The [Global Secure Access Log Reader](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#global-secure-access-log-reader) role is required to view Microsoft Entra Internet Access traffic logs.

## Investigate the signal and alert

Start your investigation by comparing the alert timeframe, signal trend, and affected entities. Then correlate the affected users and applications with the traffic, sign-in, and audit logs.

1. View the details of the alert.

   - In the Microsoft Entra admin center, review the signal graph, alert timeframe, and affected entities. For more information, see [Investigate the signals and alerts](https://learn.microsoft.com/en-us/entra/identity/monitoring-health/howto-investigate-health-scenario-alerts#investigate-the-signals-and-alerts).
   - For Microsoft Graph guidance, see [Microsoft Graph health monitoring overview](https://learn.microsoft.com/en-us/graph/api/resources/healthmonitoring-overview?view=graph-rest-beta&preserve-view=true).

2. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com/) as at least a [Reports Reader](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#reports-reader).
3. Browse to **Entra ID** > **Monitoring & health** > **Health**. The page opens to the Service Level Agreement \(SLA\) Attainment page.
4. Select the **Health Monitoring** tab.
5. Select the **Internet applications blocked by Entra Internet Access Policy** scenario, and then select an active alert.

   [![Screenshot showing the Internet applications blocked by Entra Internet Access Policy scenario in the health monitoring dashboard.](https://learn.microsoft.com/en-us/entra/identity/monitoring-health/media/howto-investigate-internet-access-signals/internet-access-blocked.png)](https://learn.microsoft.com/en-us/entra/identity/monitoring-health/media/howto-investigate-internet-access-signals/internet-access-blocked.png#lightbox)
6. Review your Microsoft Entra Internet Access content filtering policies. Check the policy rules, linked security profiles, and Conditional Access assignments. For more information, see [Configure Global Secure Access web content filtering](https://learn.microsoft.com/en-us/entra/global-secure-access/how-to-configure-web-content-filtering).
7. Review the Microsoft Entra Internet Access forwarding profile, including its acquire and bypass policies and user and group assignments. For more information, see [Manage the Internet Access profile](https://learn.microsoft.com/en-us/entra/global-secure-access/how-to-manage-internet-access-profile).
8. Review the [sign-in logs](https://learn.microsoft.com/en-us/entra/identity/monitoring-health/concept-sign-in-log-activity-details). Look for affected users whose sign-ins have a Global Secure Access security profile applied.
9. Review the [Global Secure Access traffic logs](https://learn.microsoft.com/en-us/entra/global-secure-access/how-to-view-traffic-logs). Filter the logs to the alert timeframe and affected user or application. Review denied transactions and their web category.

   [![Screenshot of Internet Access traffic logs showing blocked internet destinations.](https://learn.microsoft.com/en-us/entra/identity/monitoring-health/media/howto-investigate-internet-access-signals/internet-access-traffic-logs.png)](https://learn.microsoft.com/en-us/entra/identity/monitoring-health/media/howto-investigate-internet-access-signals/internet-access-traffic-logs.png#lightbox)
10. Review the [Global Secure Access audit logs](https://learn.microsoft.com/en-us/entra/global-secure-access/how-to-access-audit-logs) for recent changes to filtering policies, security profiles, forwarding profiles, and assignments.

    [![Screenshot of audit logs filtered to the Global Secure Access service.](https://learn.microsoft.com/en-us/entra/identity/monitoring-health/media/howto-investigate-internet-access-signals/global-secure-access-audit-logs.png)](https://learn.microsoft.com/en-us/entra/identity/monitoring-health/media/howto-investigate-internet-access-signals/global-secure-access-audit-logs.png#lightbox)

## Understand the signal

An alert can indicate a change in the number of users or internet applications that Microsoft Entra Internet Access policies block.

- A spike can indicate that a new or updated filtering policy blocks a widely used application, or that a security profile or forwarding profile was assigned to more users.
- A dip can indicate that a filtering policy, security profile, forwarding profile, or assignment was disabled or narrowed.

The change might be intentional. Compare the alert start time with the audit logs and your deployment schedule before you modify a policy.

## Mitigate common issues

The following common issues can cause this alert. This list isn't exhaustive, but it provides a starting point for your investigation.

### Many users are unexpectedly blocked after a policy or assignment change

A filtering policy, linked security profile, Conditional Access policy, or forwarding profile assignment might have expanded to include more users than intended.

To investigate and mitigate the issue:

1. In the alert, compare the number of affected users and applications with your expected deployment scope.
2. In the traffic logs, filter to the alert timeframe and an affected user. Confirm that the **Action** is **Denied**, and identify the destination and web category.
3. Review the audit logs for changes made shortly before the alert started.
4. Review the user and group assignments for the Internet Access forwarding profile and linked Conditional Access policy. Confirm that the Conditional Access session control selects the intended security profile.
5. If the expanded scope is intentional, monitor the signal and no further action is required. If it isn't intentional, restore the intended assignments or policy scope.

### A required application is blocked by a filtering rule

A web category, URL, FQDN, or wildcard rule might match a business application that users need. When multiple matching policies have conflicting actions, the most restrictive action applies.

To investigate and mitigate the issue:

1. In the alert, identify an affected application and user.
2. In the traffic logs, filter by the affected user and destination. Review the **Action** and **Web category** values for denied transactions.
3. Review all filtering rules that match the destination. Check category rules, exact URLs or FQDNs, and wildcard entries.
4. If the block is unintended, narrow the blocking rule or add the required destination to an appropriate allow policy. Keep the change limited to the users and destinations that require access.
5. Allow time for the policy change to propagate, and then confirm that new traffic log entries show the expected action.

### Only a subset of users is unexpectedly blocked

Different forwarding profile, security profile, or Conditional Access assignments can cause users who access the same application to receive different policy decisions.

To investigate and mitigate the issue:

1. Compare traffic log entries for an affected user and an unaffected user accessing the same destination.
2. Compare their user and group memberships and the assignments for the forwarding profile and linked Conditional Access policy. Confirm that the Conditional Access session control selects the intended security profile.
3. Confirm that the Internet Access traffic forwarding profile is enabled and that its acquire and bypass policies match the intended traffic.
4. Correct the unintended assignment or traffic acquisition rule, and then validate the result in the traffic logs.

## Related content

- [Troubleshoot application access](https://learn.microsoft.com/en-us/entra/global-secure-access/troubleshoot-app-access)
- [Configure Global Secure Access web content filtering](https://learn.microsoft.com/en-us/entra/global-secure-access/how-to-configure-web-content-filtering)
- [Global Secure Access network traffic logs](https://learn.microsoft.com/en-us/entra/global-secure-access/how-to-view-traffic-logs)
