<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/migration/migration-orchestrator-1-overview?view=o365-worldwide -->
<!-- Sitemap-Last-Modified: 2026-07-09 -->

# An overview of tenant-to-tenant migration with orchestrator in Microsoft 365

## What is tenant-to-tenant migration with orchestrator?

Tenant-to-tenant migration using orchestrator in Microsoft 365 enables organizations to move user data and workloads between separate Microsoft 365 tenants. This functionality supports scenarios such as mergers, acquisitions, divestitures, and internal reorganizations.

This article provides a high-level overview of the migration process, including architecture models, licensing requirements, key security and compliance considerations, and supported workloads.

To provide feedback to the product team, use [this form](https://forms.cloud.microsoft/r/Gy5jMxfy1y).

## Migration Architecture Models

Organizations can choose from several migration models depending on their business needs:

- **Single-Event Migration**

  - All users and workloads are migrated in a single cutover event.
  - Best suited for small to medium businesses or simple organizational changes.

- **Phased Migration**

  - Users are migrated in batches over time.
  - Ideal for large enterprises or complex environments.

- **Tenant Move/Split**

  - A subset of users is moved to a new tenant while others remain.
  - Common in divestiture scenarios.

All migration models require planning, communication, and time to allow the data to move.

## Licensing and availability

Cross-Tenant migrations require a per-user license \(one-time fee\) and can be assigned on either the source or target user object. This license enables the migration of all content supported by orchestration. Cross Tenant User Data Migration is available as an add-on to the following Microsoft 365 subscription plans:

- Microsoft 365 Business Basic, Standard, and Premium
- Microsoft 365 F1/F3/E3/E5
- Office 365 F3/E1/E3/E5
- Exchange Online
- SharePoint in Microsoft 365
- OneDrive
- EDU

This product is available for EA, CSP, Web direct, small business, and EDU customers.

## Security and compliance considerations

Organizations subject to regulatory compliance \(for example, GDPR, HIPAA\) should consult legal and compliance teams before initiating migration.

## Supported scenarios

Important

This migration moves **content**, not **identities**. Customers are responsible for correctly creating and configuring users, and the product moves the in-scope content from its source tenant location to its target tenant location. We designed this product with the end-user in mind. This migration is intended to minimize disruption to the end-user.

This new product simplifies both an admin's role in migrating content cross-tenant and a user's experience when they migrate. There are four supported workloads that can be specified to be moved when creating a batch: Exchange mailboxes, OneDrives, Teams chats, and Teams meetings. If you intend to run the migration of multiple workloads \(such as Exchange, chats, meetings, and OneDrive\), you should run them all together in the same batch, rather than managing separate batches for individual workloads. The orchestrator was designed to intelligently migrate the workloads in an order that accounts for all dependencies and minimizes risk for migrations to fail.

While customers can run migrations for individual workloads by specifying those workloads when creating the batch, the Teams Meeting migration does depend on a successful mailbox migration. **The migration batch will fail to initiate if the Teams meeting workload is selected without also selecting Teams chats and mailboxes.** Otherwise, Exchange mailboxes, OneDrives, and Teams Chats can be migrated independently. The product does, however, require that a user be specifically configured as having a mailbox on the source tenant and not having a mailbox on the target tenant \(MailUser\) before Identity Mapping can be performed. This requirement stands even if mailboxes are not being moved.

Note

If you intend to migrate OneDrive sites, there's a limit to how many OneDrive accounts can be scheduled to migrate at a time. This limit is shared between the OneDrive and SharePoint migrations. [Learn more](https://learn.microsoft.com/en-us/microsoft-365/migration/cross-tenant-onedrive-migration?view=o365-worldwide) about this limit.

Important

Identity Mapping is required, which means the specific user configuration supported by Identity Mapping is required. [Learn more](https://learn.microsoft.com/en-us/microsoft-365/migration/cross-tenant-identity-mapping?view=o365-worldwide) about Identity mapping.

### Exchange mailbox scope

Mailboxes on any type of hold aren't migrated, and a move for those mailboxes is blocked. Talk to our engineering team before attempting to move any users with holds applied.

Only user-visible content in the mailbox \(email, contacts, calendar, tasks, and notes\) migrates to the target tenant. The source mailbox is deleted after a successful migration. This deletion means that, after migration, under no circumstances is the source mailbox available, discoverable, or accessible in the source tenant. The calendar isn't available on the source tenant after migration.

After the moves are complete, the source user mailbox is converted to a MailUser, and the targetAddress \(shown as ExternalEmailAddress in Exchange\) is stamped with the routing address to the destination tenant. This process leaves the legacy MailUser in the source tenant and allows for coexistence and mail routing. When business processes allow, the source tenant can remove the source MailUser or convert them to a mail contact.

All limitations listed on the public documentation for [mailbox migration](https://learn.microsoft.com/en-us/microsoft-365/migration/cross-tenant-mailbox-migration?view=o365-worldwide) apply.

### OneDrive scope

The OneDrive content moves from the source to the target, leaving behind a redirect link on the source. Incremental and delta migration passes can't be performed. All limitations listed in the [public documentation for OneDrive migration](https://learn.microsoft.com/en-us/microsoft-365/migration/cross-tenant-onedrive-migration?view=o365-worldwide) apply.

### Teams chat and meeting scope

Chats and meetings are migrated from the source to the target. The original content on the source remains, though it might be in an edited form. This configuration means that the user participant list might change, with source users removed and target users added. There might be duplicate threads created on both tenants. Once the migration completes, users should only use their target identity to use Teams. If there's out-of-scope content, they can reference the source Teams client if they still have a licensed source user.

### Not in-scope

The Cross-Tenant User Data Migration solution doesn't migrate shared data, such as Teams and Channels or SharePoint Sites. This data remains in the source tenant.

For workload-specific items that are out-of-scope, refer to the [known issues](https://learn.microsoft.com/en-us/microsoft-365/migration/migration-orchestrator-8-faq?view=o365-worldwide) list.

## Next steps

See [Planning and prerequisites](https://learn.microsoft.com/en-us/microsoft-365/migration/migration-orchestrator-2-planning-prerequisites?view=o365-worldwide) for information on the prerequisites for migrating with orchestrator and other planning guidance.

For information about the end-user experience during and after migration, see [End-user experience for cross-tenant migration](https://learn.microsoft.com/en-us/microsoft-365/migration/migration-orchestrator-7-end-user-exp?view=o365-worldwide).
