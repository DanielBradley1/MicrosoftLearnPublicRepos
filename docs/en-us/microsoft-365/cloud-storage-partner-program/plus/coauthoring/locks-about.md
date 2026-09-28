<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/plus/coauthoring/locks-about -->
<!-- Sitemap-Last-Modified: 2022-07-06 -->

# Locks overview

To support editing and coauthoring files, clients that use the WOPI protocol require the WOPI host to support locking files. For more information, see the full list of [WOPI lock APIs](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/files/lock).

## Lock types

- **WOPI locks**: Existing [WOPI locks](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/files/lock) that are already used in Cloud Services Partner Program Plus \(CSPP Plus\), and which are extended with more properties for better support for clients. WOPI locks are mutually exclusive for use with all other lock types the host supports, including `Coauth` and `CoauthExclusive` locks.

Additional lock types provided by the coauthoring extensions:

- **`Coauth` lock**: New locks that are used to support the coauthoring extensions. The document must have `SupportsCoauth` enabled. The client must have edit permissions to request this lock. A client can acquire this lock only if one of the following scenarios is true:

  - The file isn't locked by any mechanism that the host understands \(including but not limited to WOPI locks\); or
  - The file is locked by any number of clients that hold `Coauth` lock references, and zero or one client holds a `CoauthExclusive` lock reference. If this lock is held, only clients that hold a `Coauth` lock may update the document \(unless there is a `CoauthExclusive` lock\).

- **`CoauthExclusive` lock**: A subtype of a `Coauth` lock that can be held by *at most* one client per document at any given time. The document must have `SupportsCoauth` enabled. The client must have edit permissions to request this lock. A client can acquire this lock only if one of the following scenarios is true:

  - The file isn't locked by any mechanism that the host understands \(including but not limited to WOPI locks\); or
  - The file is locked by any number of clients that hold `Coauth` lock references and no client holds a `CoauthExclusive` lock reference. This lock doesn't inhibit other client's abilities to acquire or release `Coauth` locks. If this lock is held, only the client that holds this lock may update the document.

Note

Locks only affect modifying the file, and do not impact requests to read the file.

Note

For the purposes of the existing WOPI lock semantics, the new `Coauth` locks are considered "another interface." As a result, if a `Coauth` or `CoauthExclusive` lock is held on the document, all [409 Conflict](https://www.w3.org/Protocols/rfc2616/rfc2616-sec10.html#sec10.4.10) responses should omit the `X-WOPI-Lock` response header for all WOPI methods.

## How clients work with locks

A client can switch between a `Coauth` lock and a `CoauthExclusive` lock by calling the `GetCoauthLock` method and requesting the other type of lock. The same rules for evaluating the success of the `GetCoauthLock` call apply, regardless of the client’s current lock status. `UnlockCoauthLock` removes the client’s lock. When a client acquires a `CoauthExclusive` lock, only that client may update the document on the host. Requests for document updates that are made without the `CoauthExclusive` lock reference should fail.

`Coauth` lock and `CoauthExclusive` lock references are associated with their `CoauthLockId` value instead of with the user identity. A single user identity might have multiple lock references and a distinct `CoauthLockId` value, while a lock with a specific reference might be taken, refreshed, or released by calls that have different user identities.

## Next steps

- Learn what's new in the [CheckFileInfo](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/files/checkfileinfo/checkfileinfo-csppp) coauthoring extensions.
- Learn what's new in the [GetNewAccessToken](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/plus/coauthoring/get-new-access-token) coauthoring extensions.
- Learn what's new in the [WOPI locks](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/plus/coauthoring/wopi-locks) coauthoring extensions.
