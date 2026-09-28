<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/migration/migration-orchestrator-8-faq?view=o365-worldwide -->
<!-- Sitemap-Last-Modified: 2026-06-26 -->

# FAQ and troubleshooting

## Cancellation

If you start a migration and realize that you need to cancel it, you need to cancel it before the CompleteAfterDate passes. If the CompleteAfterDate is past and the mailbox is cutover, then the user data migration completes automatically with Teams chats and meetings. Once the migration completes, it's possible to move the user data back to the source.

## Moving user data back

If you need to move a user's mailbox and OneDrive back to the source tenant after completing a successful migration to the target tenant, use the standalone mailbox and OneDrive migration options and configure all steps in the direction of target to source. This process doesn't require Identity Mapping. Teams meetings aren't recreated after this migration and need to be recreated manually. Teams chat messages are never deleted from the source tenant after migration, so users can continue to use those messages. If a user's removed from a chat, create a new version of the chat while still having access to all historical chat messages.

## General migration

[Learn more](https://learn.microsoft.com/en-us/microsoft-365/migration/cross-tenant-mailbox-migration?view=o365-worldwide#frequently-asked-questions) about Exchange Mailbox Migration.

### Do you have any recommendations for batches?

To ensure a smooth migration process, we recommend limiting the number of mailboxes per batch to 2,000 and submitting batches at least two weeks before the cut-over date. This limit doesn't affect end users during synchronization. For guidance on migrating quantities exceeding 50,000 mailboxes, contact your account team for assistance.

If you're migrating OneDrive, there's a 4,000 limit between SharePoint and OneDrive sites that can be moved and queued to move at one time.

### Can I perform a cross-cloud tenant-to-tenant migration?

Cross-cloud tenant-to-tenant migration isn't supported. An example scenario would be moving from Office 365 Worldwide to Office 365 Government Cloud.

### Are voicemails migrated cross-tenant?

- Yes, voicemails are migrated cross-tenant.
- Received voicemails in email as attachments are available in the target mailbox.
- Received voicemails are available in Teams if you call voicemail and listen to saved messages \(Voicemails received in the source tenant are available as saved messages\).
- Received voicemails aren't available in the Teams client UI in target post-migration.
- The voicemail greeting also migrates to the target.

For more troubleshooting guidance, see [Resolve orchestrated migration errors](https://learn.microsoft.com/en-us/troubleshoot/microsoft-365/admin/orchestrated-migration/resolve-orchestrated-migration-errors).

## How long does migration take?

Important

The timing information in this article is guidance only. It isn't a service level agreement \(SLA\), and it shouldn't be treated as a guaranteed completion time for any tenant, batch, or user.

Migration duration varies based on the total traffic in the service, the workloads selected, the amount of data being moved, and the number of users included in the migration. Migration timing isn't the same for every tenant or every user. The time required to validate and migrate depends on several factors:

- Workloads selected: Different workloads have different processing patterns. Exchange, OneDrive, Teams chats, and Teams meetings can progress differently.
- Amount of data: Users with larger mailboxes, more OneDrive content, or more Teams data can take longer than users with smaller data sets.
- Number of users in the batch: Larger migration waves can take longer to validate, monitor, and complete than smaller pilot groups.
- Overall service traffic: Processing time can vary based on the volume of migration traffic currently being handled across the service.
- Tenant readiness and configuration quality: Validation can take longer when prerequisites are missing or when admins need multiple validation attempts to resolve issues.

### What to expect from validation timing

Validation starts automatically when you create a migration batch. Validation checks whether tenant-level and user-level prerequisites are in place before migration can begin.

Validation timing can vary based on:

- The number of users in the batch
- The number of workloads selected
- The number of prerequisite failures that need to be fixed
- Overall system traffic at the time validation is processed

Validation doesn't guarantee a fixed completion time. Some batches validate quickly, while others require multiple rounds of review and correction before they reach `ValidatePassed`.

Admins should plan for validation as an active part of the migration process rather than a near-instant precheck.

### What to expect from migration timing

After validation passes, migration timing still varies by user and by workload.

- Users in the same batch might not complete at the same time.
- Different workloads for the same user can complete at different times.
- A tenant's migration duration can vary from one batch to the next.
- Higher overall service traffic can affect how quickly migration work progresses.

Migration timing should be planned as a range of possible outcomes, not as a single guaranteed timestamp.

### What to do if your mailbox migration appears stuck

If you're using the Orchestrator and notice that a mailbox migration is taking longer than expected to cutover once the CompleteAfterDate passed \(typically more than 24 hours, or significantly longer than other mailboxes in your batch\), a Data Consistency Score issue may be blocking completion.

You need to use Exchange Online PowerShell to investigate.

```powershell

Get-MigrationUser -Identity user@domain.com | Select-Object BatchId, Status, DataConsistencyScore
```

Replace `user@domain.com` with the email address of the user whose mailbox is stuck.

If the output shows a DataConsistencyScore of "Investigate" or "Poor", then a DCS issue is causing the delay.

If the DCS grade is "Investigate", your administrator can approve the migration to proceed:

```powershell

Set-MigrationUser -Identity user@domain.com -ApproveSkippedItems
```

This approval tells the Exchange service to complete the migration with the items that could be transferred. The migration should then complete within a few minutes.

After approving, you can optionally see which items were skipped:

```powershell

$userStats = Get-MigrationUserStatistics -Identity user@domain.com -IncludeSkippedItems

$userStats.SkippedItems | Select-Object Subject, Sender, DateSent
```

If the DCS grade is "Poor", don't approve the migration. Instead:

1. Contact Microsoft Support with your migration batch ID
2. Explain that your DCS grade is "Poor"
3. Microsoft investigates the root cause before proceeding

When the Migration Orchestrator orchestrates an Exchange mailbox migration, it submits the migration to the Exchange service and waits for completion. In rare cases, the Exchange service detects a DCS issue and pauses to await approval before proceeding. The Orchestrator continues waiting, which appears as a stalled migration to you. This waiting function is a safety mechanism to prevent unexpected data loss—once you \(or your administrator\) approve, the migration completes normally.
