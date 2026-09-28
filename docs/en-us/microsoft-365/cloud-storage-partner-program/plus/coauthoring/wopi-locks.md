<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/plus/coauthoring/wopi-locks -->
<!-- Sitemap-Last-Modified: 2022-07-06 -->

# WOPI locks

The existing WOPI lock implementation is extended to allow clients to specify the lock duration when they acquire locks and to refresh locks. If the new header isn't specified, the current 30-minute duration applies.

## Lock/RefeshLock/UnlockAndRelock syntax

For full descriptions of these methods, see the existing API contracts:

- [Lock](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/files/lock)
- [RefreshLock](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/files/refreshlock)
- [UnlockAndRelock](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/files/unlockandrelock)

Additional headers for existing Lock, RefreshLock, and UnlockAndReLock methods:

## Request headers

- `X-WOPI-LockExpirationTimeout` \(uint\) – Optional. Represents the timeout duration for the lock expiration in seconds. The value can be part of a configuration value on the client side. The host must honor the lock expiration timeout duration the client provides. The timeout range must be within the values of 1 minute and 1 hour, inclusive of these values. If the value provided isn't within an acceptable range, the host should send 400 Bad Payload as a response.
- `X-WOPI-LockUserVisible` \(Boolean\) – Optional. If this header is set to `true`, the `UserFriendlyName` value that's associated with the access token for this request should be provided in `X-WOPI- ConflictingLockUsername` for responses that get a 409 Conflict response as a result of this lock being held. This value is valid only until the next time the lock is updated.

## Response headers

- `X-WOPI- ConflictingLockUsername` \(string\) – Optional. If the conflict is caused by a WOPI-exclusive lock being held, and if the `UserFriendlyName` value that's associated with the lock is visible \(see `X-WOPI-LockUserVisible`\), this header should contain that `UserFriendlyName` value when it responds to the request with 409 Conflict. This string may be presented to the user by the Microsoft 365 user interface.

## Next steps

- Learn what's new in the [CheckFileInfo](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/files/checkfileinfo/checkfileinfo-csppp) WOPI coauthoring extensions.
- Learn what's new in the [GetNewAccessToken](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/plus/coauthoring/get-new-access-token) WOPI coauthoring extensions.
