<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/plus/file-transfer/content-sequence -->
<!-- Sitemap-Last-Modified: 2022-07-06 -->

# Content sequence numbering and coherency

The host stores the following parts of the content:

- Primary document content \(`MainContent`\)
- Multiple streams within the document in addition to MainContent \(for example, the alternate stream used by Excel to write revision records\)
- "Side car" information, which is used to store the last OCS save for the specific session.

Note

All three of these content parts can be modified and fetched in a single request or response. Modifications must be processed within a transaction.

## Strict content sequence numbering

The content parts are bundled together and associated with any given state of the file on the host. Each state on the host is assigned an integer sequence number, which must be assigned increasing values greater than zero. The maximum valid value is 2,147,483,647.

## Coherency

All modification transactions with a `Coauth` lock must be gated with a sequence number. The request provides the expected sequence number. If the host's current state doesn't match that sequence number, then the request fails.

## Next steps

[Chunk streams](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/plus/file-transfer/chunk-streams) for efficient file transfer.
