<!-- Source: https://learn.microsoft.com/en-us/defender-xdr/manage-incident-case-merging -->
<!-- Sitemap-Last-Modified: 2026-09-23 -->

# Merge and split incident cases in the Microsoft Defender portal \(preview\)

Incident cases in the Microsoft Defender portal help security operations teams investigate and respond to related alerts in a single case management workflow. As an investigation develops, you might need to merge related incident cases or move alerts between incident cases to keep the investigation scope accurate.

Use merging and alert movement to reduce duplicate work, group related investigation context, and make sure analysts respond to the right set of alerts, assets, evidence, and activities.

Note

Incident cases are in preview and are the recommended experience for managing incidents in the Microsoft Defender portal. The legacy incident experience remains available during this preview.

For an overview of incident cases, see [Case management in the Microsoft Defender portal](https://learn.microsoft.com/en-us/defender-xdr/siem-defender-case-management).

For general information about alert correlation and incident merging in the existing incident experience, see [Alert correlation and incident merging in the Microsoft Defender portal](https://learn.microsoft.com/en-us/defender-xdr/alerts-incidents-correlation).

## Merge or split incident case scope

Use the following guidance to decide whether to merge incident cases or move alerts between incident cases.

| Action | Use when |
| --- | --- |
| Merge incident cases | Multiple incident cases represent the same attack, investigation, or related activity and should be handled together. |
| Move alerts between incident cases | One or more alerts don't belong in the current incident case and should be investigated as part of a different incident case. |

## Incident case correlation

Microsoft Defender automatically correlates related alerts and investigation context into incident cases. Correlation can be based on common entities, timing, attack behavior, service signals, detection sources, and other related activity.

Automatic correlation helps reduce duplicate investigation work and gives analysts a single incident case for related alerts, assets, evidence, and response activity.

The correlation logic is managed by Microsoft Defender.

## When to merge incident cases

Merge incident cases when multiple cases are part of the same investigation and should be handled together.

For example, merge incident cases when they include:

- Related alerts from the same attack or campaign
- Related users, devices, mailboxes, cloud resources, or other assets
- Shared indicators, such as files, IP addresses, senders, or processes
- Similar tactics, techniques, and procedures
- Activity that occurred in the same time frame
- Activity that represents a single multistage attack

Manual merging is useful when related incident cases weren't merged automatically, or when analysts determine during investigation that separate incident cases should be handled as one case.

When incident cases are merged, one case ID is retained, case data is consolidated into the retained case, and the other case IDs are removed.

Note

Incident cases with a resolved status can't be merged.

For step-by-step guidance, see [Merge incident cases manually in the Microsoft Defender portal](https://learn.microsoft.com/en-us/defender-xdr/merge-incident-cases-manually).

## When to move alerts between incident cases

Move alerts between incident cases when an alert doesn't belong in the current case or should be investigated with a different case.

For example, move an alert when:

- The alert was correlated to the wrong incident case.
- The alert is unrelated to the rest of the current incident case.
- The alert belongs to another active investigation.
- Moving the alert improves investigation ownership, scope, or response accuracy.

Every alert must belong to an incident case. Moving an alert changes the incident case where the alert is investigated and managed.

For step-by-step guidance, see [Move alerts from one incident case to another in the Microsoft Defender portal](https://learn.microsoft.com/en-us/defender-xdr/move-alert-to-another-incident-case).

## Related content

- [Merge incident cases manually in the Microsoft Defender portal](https://learn.microsoft.com/en-us/defender-xdr/merge-incident-cases-manually)
- [Move alerts from one incident case to another in the Microsoft Defender portal](https://learn.microsoft.com/en-us/defender-xdr/move-alert-to-another-incident-case)
- [Manage incident cases in the Microsoft Defender portal](https://learn.microsoft.com/en-us/defender-xdr/manage-incident-cases)
- [Investigate incident cases in the Microsoft Defender portal](https://learn.microsoft.com/en-us/defender-xdr/investigate-incident-cases)
- [Alert correlation and incident merging in the Microsoft Defender portal](https://learn.microsoft.com/en-us/defender-xdr/alerts-incidents-correlation)
