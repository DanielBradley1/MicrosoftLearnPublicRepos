<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/migration/migration-orchestrator-5-running-migration?view=o365-worldwide -->
<!-- Sitemap-Last-Modified: 2026-06-16 -->

# Running the migration

The migration is run by creating a migration job in the form of a batch. Users are grouped together into a batch and submitted together. The maximum batch size is 100 users. Migrations are managed through Graph APIs. These APIs can be run with PowerShell 5 or 7, or with [Graph Explorer](https://developer.microsoft.com/graph/graph-explorer#mode=canary).

All commands below are run through Microsoft Graph from the **target** tenant by Microsoft M365 Migration Administrators or Global Administrators. Source tenants cannot run the migration commands. To connect to Graph to run the migration commands, run this command as a target Microsoft M365 Migration Administrator or Global Administrator:

```powershell
Connect-MgGraph **-Scopes 'CrossTenantContentMigration.ReadWrite.All'**
```

Important

Microsoft recommends that you use roles with the fewest permissions. Using lower permissioned accounts helps improve security for your organization. Global Administrator is a highly privileged role that should be limited to emergency scenarios when you can't use an existing role.

## Understanding the batch lifecycle

Step 1: Create the batch: Define the batch with your users, workloads, and settings. When you create the batch, validation begins automatically to check that all prerequisites are met. Users feel no impact during validation.

Step 2: Monitor and fix validation: Monitor the batch status. If validation passes \(ValidatePassed\), you can proceed to migrate. If validation fails \(ValidateFailed\), review the per-user errors, fix the issues, and call validate again on the same batch. Repeat until the batch reaches ValidatePassed.

Step 3: Migrate the batch: Once validation passes, call migrate on the same batch to start the actual migration. Migration can only begin after validation passes. Validation must pass within the last seven days. If more than seven days elapsed since validation passed, you must revalidate before migrating.

## Understanding validation

Because there are many [Prerequisites](https://learn.microsoft.com/en-us/microsoft-365/migration/migration-orchestrator-2-planning-prerequisites?view=o365-worldwide) for migration, there's a step during the pre-cutover phase called *validation* that checks whether those prerequisites are met. Validation acts similarly to running a what-if. It checks for all the known requirements for a successful migration in the general migration ecosystem \(app permissions, relationships between tenants, and so on\) and at a user level \(licenses, identity mapping, and so on\). A batch must pass validation before it can be submitted for migration. Validation runs automatically when you create a batch, and you can rerun it as many times as needed until all prerequisites are met.

Submitting a validation request on a batch results in either:

1. Confirmation that a batch and its users meet all prerequisites. Status is ValidatePassed, meaning that all users in the batch meet all prerequisites for all selected workloads. You can proceed to migrate the batch.
2. A list of errors resulting from failed checks. Status is ValidateFailed, meaning that one or more users failed one or more prerequisite checks. Review the per-user results, fix the issues, and call validate again on the same batch.

Note

The list of errors might not be exhaustive. Admins should run validation and fix errors until all prerequisites are met and there are no failures.

When you submit the migration, we do another check of all of the prerequisites, but we don't return a list of the failures per workload.

Note

For a list of the different stages and descriptions of batch migration processing, see [Batch migration description values](#batch-migration-description-values).

## Understanding the migration process

The migration occurs at a user-level, meaning that if one user passes the validation phase, their migration continues. If another user fails any validation check, their migration fails \(and never actually begins\). To migrate these failed users, create a new batch that includes the failed users, after correcting the validation failures. It retries the migration if there was a terminal failure. When migration requests are submitted for a batch, they follow the flow in the following sections.

### Pre-Cutover Phase: Validation and Syncing

The first step that takes place is the Pre-Cutover Phase. Throughout this step, the selected workloads \(Exchange, OneDrive, Teams Chats, and/or Teams Meetings\) perform preparation work for migration, with no impact to end users. All necessary setup steps are validated \(again\). If any checks fail for a user, then the migration fails for that user. Other users continue in the process if they meet all prerequisites. For a list of the prechecks, consult the [Prerequisites](https://learn.microsoft.com/en-us/microsoft-365/migration/migration-orchestrator-2-planning-prerequisites?view=o365-worldwide) article.

Until the CompleteAfterDate \(Cutover time\) occurs, workloads only perform preparation work, with no user impact. Exchange, if selected, begins to sync user mailbox content. Users feel no impact and continue to use their source mailboxes without interruption. We strongly recommend submitting batches two weeks before the CompleteAfterDate as there's no impact on the end users during synchronization. OneDrive, Teams Chats, and Teams Meetings don't begin to move during the Pre-Cutover Phase.

The CompleteAfterDate can be updated at any point before it passes. Migrations can only be canceled before the CompleteAfterDate passes.

### Cutover Phase: User Impacting

When all Pre-Cutover steps complete and the CompleteAfterDate passes, the migration begins to move the data and to impact end users.

- Exchange, if selected, begins to cutover from source to target, giving the target user a mailbox and making the source user a MailUser. If selected, Exchange migration cuts over before other workloads begin to move. All other workloads migrate in parallel.
- OneDrive, if selected, begins to cutover from source to target, giving the target user a OneDrive and removing the source OneDrive.
- Teams Chats, if selected, creates new Teams message threads in the target and edit source threads.
- Teams Meetings, if selected, is edited for hosting on the target tenant.

After the CompleteAfterDate passes, no cancelations can take place. Migration can be retried if it fails at any point.

### Migration conclusion

Users can use their target tenant accounts to use their mailboxes, chats, meetings, and OneDrive sites.

### Retry

If a migration completes with errors \(Status: CompletedWithErrors\) or fails \(Status: Failed\), you can call migrate again on the same batch to retry. This call starts a new migration attempt for the users that didn't complete successfully.

## Understanding Migration Status and Errors

For a breakdown of the meanings behind the statuses and errors, see [Batch migration description values](#batch-migration-description-values).

There's up to an hour-long delay between when updates are made to the group containing the authorized users for migration and when our system processes those changes. Allow for up to an hour to start the migration after changes are made to the group membership.

Note

For more troubleshooting guidance, see [Resolve orchestrated migration errors](https://learn.microsoft.com/en-us/troubleshoot/microsoft-365/admin/orchestrated-migration/resolve-orchestrated-migration-errors).

## Running a migration

### Create a batch

Create a migration batch with your users and settings. When the batch is created, validation begins automatically to check prerequisites. Each batch you create needs a unique name. Users can only belong to one active batch at one time. The maximum batch size is 100 users.

There are two ways to create a batch.

#### Option 1: Define request body

```powershell
body = '{
  "displayName": "xtmigration1",
  "completeAfterDateTime": "2024-12-09T22:48:03.092Z",
  "sourceTenantId": "XXXXX-XXXXX-XXXXXX-XXXXXX",
  "exchangeSettings": {
    "targetDeliveryDomain": "DOMAIN.onmicrosoft.com",
    "sourceEndpoint": "sampleEndpointText"
  },
  "resources": [
    "XXXXXXX-XXXXXXX-XXXXXXX-XXXXXXX",
    "XXXXXXX-XXXXXXX-XXXXXXX-XXXXXXX",
    "XXXXXXX-XXXXXXX-XXXXXXX-XXXXXXX"
  ],
  "resourceType": "Users",
  "workloads": [
    "Teams",
    "Exchange",
    "ODSP",
"Meeting"
  ]
}'
New-MgBetaCrossTenantMigrationJob -BodyParameter $body
```

#### Option 2: Use parameters

```powershell
New-MgBetaCrossTenantMigrationJob -DisplayName "xtmigration1" -CompleteAfterDateTime 2024-12-09T22:48:03.092Z -Resources @("XXXXXXX-XXXXXXX-XXXXXXX-XXXXXXX","XXXXXXX-XXXXXXX-XXXXXXX-XXXXXXX", "XXXXXXX-XXXXXXX-XXXXXXX-XXXXXXX") -ResourceType Users -SourceTenantId XXXXXXX-XXXXXXX-XXXXXXX-XXXXXXX -ExchangeSettings @{SourceEndpoint = "sampleEndpointText"; TargetDeliveryDomain = "DOMAIN.onmicrosoft.com"} 
```

### Validate a batch

After you create a batch, call validate to run prerequisite checks. Validation operates on the existing batch. You don't create a new batch. You can validate when the batch status is `Submitted` or `ValidateFailed`.

```powershell
Test-MgBetaCrossTenantMigrationJob -CrossTenantMigrationJobId <batch display name or job id>
```

Monitor the status:

```powershell
Get-MgBetaCrossTenantMigrationJob -CrossTenantMigrationJobId <batch display name or job id> | ConvertTo-Json
```

By default, the 20 most recent results appear. To access more, run the command with the parameter **-All**.

If the status is `ValidateFailed`, drill into per-user results to see specific errors:

```powershell
Get-MgBetaCrossTenantMigrationJobUser -CrossTenantMigrationJobId <batch display name or job id> | ConvertTo-Json -Depth 100
```

By default, the 20 most recent results appear. To access more, run the command with the parameter **-All**.

Fix any issues and call validate again on the same batch. Repeat until the status is `ValidatePassed`.

### Migrate a batch

Once the batch status is `ValidatePassed`, call migrate to start the actual migration. Migration is also permitted when the status is `CompletedWithErrors` or `Failed`, allowing you to retry.

```powershell
Move-MgBetaCrossTenantMigrationJob -CrossTenantMigrationJobId <batch display name or job id>
```

If the batch doesn't pass validation, this command returns an error: "Migration can't be started because the current status is {status}".

### Retrieve all batches

A retrieve allows you to see all submitted batches. It shows active and past batches.

```powershell
Get-MgBetaCrossTenantMigrationJob | ConvertTo-Json
```

By default, the 20 most recent results appear. To access more, run the command with the parameter \(code\) **-All**.

### Retrieve a specific batch

Allows you to receive information about a specific batch and its properties.

```powershell
Get-MgBetaCrossTenantMigrationJob -CrossTenantMigrationJobId <batch display name or job id> | ConvertTo-Json
```

By default, the 20 most recent results appear. To access more, run the command with the parameter \(code\) **-All**.

### Retrieve user status within a specific batch

Allows you to receive information about the users within a specific batch. You see the state for each of the workloads, including Exchange, Teams Chats, Teams Meetings, and OneDrive.

```powershell
Get-MgBetaCrossTenantMigrationJobUser -CrossTenantMigrationJobId <batch display name or job id> -CrossTenantMigrationTaskId <ExternalDirectoryObjectId for the target user> | ConvertTo-Json -Depth 100
```

By default, the 20 most recent results appear. To access more, run the command with the parameter **-All**.

### Update the complete after date for a specific batch

Allows you to change the complete after date. Moving the date pushes the earliest date at which the cutovers for mailboxes occur and when the Teams chat and meeting and OneDrive migration begins.

```powershell
Update-MgBetaCrossTenantMigrationJob -CrossTenantMigrationJobId <batch display name or job id> -CompleteAfterDateTime <date time to update to>
```

Acceptable date and time formats are available on [Standard date and time format](https://learn.microsoft.com/en-us/dotnet/standard/base-types/standard-date-and-time-format-strings).

### Cancel a batch

Allows you to cancel an entire batch and all of its users' migrations. It cancels all migrations for users whose mailboxes aren't yet cut over and whose Teams Chats, Teams Meetings, and OneDrive migrations aren't started. A batch can only be canceled before the Complete After Date is reached. After this point, the migration continues without cancelation.

```powershell
Stop-MgBetaCrossTenantMigrationJob -CrossTenantMigrationJobId <batch display name or job id> 
```

### Remove a user from a batch and cancel that user's migration

Allows you to cancel a single user's migration by removing them from that batch. It needs to be run multiple times if multiple users need to be removed. The remaining users in the batch are unaffected. This option is only possible before the cutover of the user's mailbox and before the Teams Chats, Teams Meetings, and OneDrive migrations start.

```powershell
Stop-MgBetaCrossTenantMigrationJobUser -CrossTenantMigrationJobId <batch display name or job id> -CrossTenantMigrationTaskId <ExternalDirectoryObjectId for the target user> 
```

If the removal is successful, you see a 202 Accepted request with the response:

> Cancelation request for user ID: `<XXXX-XXXXX-XXXXX-XXXX>` from batch: `<batch name or batch request ID>` was accepted.

At this point, the user is removed from the batch, their migration is canceled, and any mailbox syncing that took place is canceled. A user can't be readded to the same batch, but a user can be added to a new batch. No other user within that batch is affected. The identity mapping isn't edited at all.

If the removal is unsuccessful, here are the possible responses:

1. The User ID provided in the request doesn't exist within the batch provided. This message likely means the admin provided an incorrect User ID and should check it again. There's a 404 error.
2. The batch ID or batch name can't be found in the tenant. This message likely means the admin provided an incorrect batch ID or batch name in the cancelation request and should check it again. There's a 404 error.
3. If the cancelation request comes in after the specified completeAfterDate passed, the user's migration can't be canceled, and they can't be removed from the batch. There's a 409 error.
   > Cancel is not possible. Current status is `<user status>`


   If a removal is unsuccessful, the user continues belonging to the batch and is migrated.

## Common parameters

There are many parameters that must be provided in a specific format for the migration input:

- **displayName** - A batch name of your choosing to help you identify this specific batch.
- **completeAfterDateTime** - The date that specifies the **earliest** acceptable time for the cutover of Exchange to begin. There's no user impact until this date passes **and** the Exchange sync is complete. This date can be updated later. The acceptable date and time formats are available on [Microsoft Learn](https://learn.microsoft.com/en-us/dotnet/standard/base-types/standard-date-and-time-format-strings#table-of-format-specifiers).
- **sourceTenantId** - The ID of the source tenant. This ID can be found in the Microsoft Entra admin center.
- **targetDeliveryDomain** - Your target tenant domain. Example: domain.onmicrosoft.com.
- **sourceEndpoint** - The name of the endpoint created on the target tenant. You can find it using the `Get-MigrationEndpoint` command with the `-Name` parameter.
- **resources** - A list of ExternalDirectoryObjectIds for the **target** users you're including in this batch. These resources are available in the Azure portal under the user as "**Object ID**" or through PowerShell.
- **resourceType** - Is always "**Users**" for all user content migrations.
- **workloads** - A string with the list of workloads you intend to migrate. These strings should be formatted in a comma-delimited list. The proper strings are:

  - "**Exchange**"
  - "**ODSP**"
  - "**Teams**"
  - "**Meeting**"

If you don't provide a string, the migration defaults to moving all available workloads.

## Migrating using PowerShell

### Connect to PowerShell and Microsoft Graph

1. Open Microsoft PowerShell.
2. Install the [Graph SDK](https://learn.microsoft.com/en-us/powershell/microsoftgraph/?view=graph-powershell-bet&preserve-view=truea):

   - `Set-ExecutionPolicy -ExecutionPolicy RemoteSigned -Scope CurrentUser`

3. Connect to Microsoft Graph

```powershell
Connect-MgGraph **-Scopes 'CrossTenantContentMigration.ReadWrite.All'**
```

4. Sign in with target tenant Microsoft 365 Migration Administrator or Global Administrator credentials:
5. Confirm you're in the right tenant:

   - `Get-MgContext`

All commands below are run through Microsoft Graph from the **target** tenant by Microsoft M365 Migration Administrators or Global Administrators. Source tenants cannot run the migration commands. To connect to Graph to run the migration commands, run this command as a target Microsoft M365 Migration Administrator or Global Administrator:

#### Create the batch

Create the migration batch with your users and settings. Validation begins automatically when the batch is created. Note the batch ID or display name returned. You use it for all subsequent steps.

Note

Validation results expire after seven days. If more than seven days pass between validation passing and calling migrate, you must revalidate the batch before migration can proceed.

#### Validate the batch

Run validation to check that all prerequisites are met. See the full list of prerequisites that are checked during validation: [Prevalidation checks](https://learn.microsoft.com/en-us/microsoft-365/migration/migration-orchestrator-2-planning-prerequisites?view=o365-worldwide#prevalidation-checks).

Monitor the status at the batch level \([Retrieve a specific batch](#retrieve-a-specific-batch)\) and at the user level \([Retrieve user status within a specific batch](#retrieve-user-status-within-a-specific-batch)\). Wait for the status to reach `ValidatePassed` or `ValidateFailed`.

If `ValidateFailed`, review per-user errors: [Retrieve user status within a specific batch](#retrieve-user-status-within-a-specific-batch).

Fix the issues and revalidate the same batch. Repeat until the status is `ValidatePassed`.

#### Migrate the batch

Once validation passes, start the migration on the same batch. Regularly monitor the migration at the batch level and at the user level. To understand progress, consult the [Batch status values](#batch-status-values) table.

If there are failures, investigate the errors and messages returned on the user objects: [Troubleshoot orchestrated migration](https://learn.microsoft.com/en-us/troubleshoot/microsoft-365/admin/orchestrated-migration/resolve-orchestrated-migration-errors).

#### After migration completes

When the migration is completed, monitor the results of the batch and user statuses. If any migrations failed, examine the error code and message for retry instructions.

If the batch status is `CompletedWithErrors` or `Failed`, you can retry by calling migrate again on the same batch:

#### Make any required changes

You may need to make changes to the migration, like changing the [Complete After Date](#update-the-complete-after-date-for-a-specific-batch), [removing a user from a batch](#remove-a-user-from-a-batch-and-cancel-that-users-migration), or [canceling a migration](#cancel-a-batch). These changes can be done until a certain point in the migration, as defined in the [batch status table](#batch-migration-description-values).

## Batch migration description values

Use the following table to understand the batch lifecycle and status values. A single batch progresses through validation and then migration statuses.

Note

For more information about troubleshooting, see **[Troubleshoot orchestrated migration](https://learn.microsoft.com/en-us/troubleshoot/microsoft-365/admin/orchestrated-migration/resolve-orchestrated-migration-errors)**.

### Batch status values

| Status | Description | Validate allowed? | Migrate allowed? | Cancel allowed? |
| --- | --- | --- | --- | --- |
| `Submitted` | Batch created, awaiting validation. | Yes | No | Yes |
| `ValidateSubmitted` | Validation is triggered. | No | No | Yes |
| `ValidateProcessing` | Validation is being set up. | No | No | Yes |
| `ValidateInProgress` | Prerequisite checks are running for all workloads. | No | No | Yes |
| `ValidatePassed` | All users passed all prerequisite checks. Ready for migration. | No | Yes | Yes |
| `ValidateFailed` | One or more users failed prerequisite checks. Fix issues and revalidate. | Yes | No | Yes |
| `Processing` | Migration is being set up after calling migrate. | No | No | Yes |
| `InProgress` | Migration is running. Mailboxes are syncing. | No | No | Yes |
| `CuttingOver` | Mailboxes are cutting over. No cancelations possible. | No | No | No |
| `Completed` | Migration completed successfully for all users. | No | No | No |
| `CompletedWithErrors` | Migration completed, but some users had errors. Can retry. | No | Yes | No |
| `Failed` | Migration failed. Can retry. | No | Yes | No |
| `Canceled` | Batch was canceled. | No | No | No |
| `PendingCancel` | Cancelation is being processed. | No | No | No |
| `PendingDelete` | Deletion is being processed. | No | No | No |
| `Deleted` | Batch data is deleted. | No | No | No |

### User workload statuses by batch status

The following table shows the possible per-user workload statuses you may see when querying user status at each stage of the batch lifecycle. Each user has a status for each workload \(Exchange, Teams Chats, Teams Meetings, OneDrive\).

| Batch Status | Exchange | Teams Chats | Teams Meetings | OneDrive |
| --- | --- | --- | --- | --- |
| `Submitted` | NotStarted | NotStarted | NotStarted | NotStarted |
| `ValidateSubmitted` | NotStarted | NotStarted | NotStarted | NotStarted |
| `ValidateProcessing` | NotStarted | NotStarted | NotStarted | NotStarted |
| `ValidateInProgress` | NotStarted / InProgress / Valid / Invalid | NotStarted / InProgress / Valid / Invalid | NotStarted / InProgress / Valid / Invalid | NotStarted / InProgress / Valid / Invalid |
| `ValidatePassed` | Valid | Valid | Valid | Valid |
| `ValidateFailed` | Valid / Invalid | Valid / Invalid | Valid / Invalid | Valid / Invalid |
| `Processing` | NotStarted | NotStarted | NotStarted | NotStarted |
| `InProgress` | Syncing / Synced / Finalizing / Completed / Failed | Synced / InProgress / Completed / Failed | Synced / InProgress / Completed / Failed | Synced / InProgress / Completed / Failed |
| `CuttingOver` | Synced / Finalizing / Completed | Synced / InProgress / Completed | Synced / InProgress / Completed | Synced / InProgress / Completed |
| `Completed` | Completed | Completed | Completed | Completed |
| `CompletedWithErrors` | Completed / Failed | Completed / Failed | Completed / Failed | Completed / Failed |
| `Failed` | Failed | Failed | Failed | Failed |
| `Canceled` | Canceled | Canceled | Canceled | Canceled |

### User workload status descriptions

| Workload Status | Description |
| --- | --- |
| `NotStarted` | The workload migration isn't started for this user. |
| `Valid` | Validation passed for this workload. All prerequisites are met. |
| `Invalid` | Validation failed for this workload. Review the errors for details. |
| `InProgress` | The workload migration is actively running. |
| `Synced` | The sync phase is complete for this workload, awaiting cutover. |
| `Finalizing` | \(Exchange only\) Mailbox is being finalized during cutover. |
| `Completed` | The workload migration completed successfully for this user. |
| `Failed` | The workload migration failed for this user. Review errors for details. |
| `Error` | An unexpected error occurred during migration. |
| `Canceled` | The workload migration was canceled for this user. |
| `PendingCancel` | Cancelation is being processed for this workload. |

## Understanding Teams chat migration status

Teams chat migration status reflects the overall quality of a user's migration based on defined success thresholds. Because Teams has a rich history of content types, including some that are deprecated or are unsupported by downstream services, expect that a small number of messages or threads may not migrate successfully. The status values described here help you distinguish between expected minor failures and issues that require your attention.

#### Statuses

- inProgress: The user's Teams chat migration is currently running.
- completed: The user's Teams chat migration finished and met the success thresholds. Some messages or threads may not be migrated, but the number of failures was within acceptable limits. Review the migration message for your success and failure counts.
- failed: The user's Teams chat migration finished but didn't meet the success thresholds, or a validation failure occurred that prevented the migration from completing. Review the error message for details and recommended actions.

#### Success thresholds

A user's migration concludes with a status of failed if either of the following thresholds is exceeded:

- More than 20% of attempted messages failed to import
- More than 10% of attempted threads failed

If both failure rates are below these thresholds, the migration concludes with a status of completed. These thresholds apply to content that the migration service attempted to process. [Content that was skipped because it's explicitly known to be unsupported](https://learn.microsoft.com/en-us/microsoft-365/enterprise/migration-orchestrator-7-end-user-exp) isn't counted toward these thresholds.

#### Reading the migration message

When a user's Teams chat migration concludes, the message field in the user status contains a summary in this format:

- Teams migration for user {0} **completed**. {1}/{2} \({3}%\) messages imported successfully \(>= {4}% threshold\). {5}/{6} \({7}%\) threads imported successfully \(>= {8}% threshold\). Request Id: {9}. Batch Id: {10}. To understand these figures, refer to migration documentation.
- Teams migration for user {0} **failed a quality threshold**. {1}/{2} \({3}%\) messages imported successfully \(< {4}% threshold\). {5}/{6} \({7}%\) threads imported successfully \(<{8}% threshold\). Request Id: {9}. Batch Id: {10}. To understand these figures, refer to migration documentation.
- {0}: user ID
- {1}: successfully migrated messages
- {2}: attempted messages
- {3}: percentage of successfully migrated messages/attempted messages
- {4}: threshold for message success \(80%\)
- {5}: successfully migrated threads
- {6}: attempted threads
- {7}: percentage of successfully migrated threads/attempted threads
- {8}: threshold for thread success \(90%\)
- {9}: request ID
- {10}: batch ID

#### Implication

If a user's migration status is completed, the migration was largely successful according to the thresholds of expected success. If the user's status is failed, there were more failures of messages and threads than expected. This failure can be due to a specific user's frequent use of now-deprecated Teams content historically. If there are concerns about high failure rates, reach out to Microsoft Support.

## Next steps

For information on what to do after the migration is complete, see [Post-migration tasks for tenant-to-tenant migrations](https://learn.microsoft.com/en-us/microsoft-365/migration/migration-orchestrator-6-post-migration?view=o365-worldwide).

For FAQs and troubleshooting regarding the migration orchestrator, see [Migration orchestrator FAQ](https://learn.microsoft.com/en-us/microsoft-365/migration/migration-orchestrator-8-faq?view=o365-worldwide).
