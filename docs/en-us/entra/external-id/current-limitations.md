<!-- Source: https://learn.microsoft.com/en-us/entra/external-id/current-limitations -->
<!-- Sitemap-Last-Modified: 2026-04-24 -->

# Limitations of Microsoft Entra B2B collaboration

Microsoft Entra B2B collaboration is currently subject to the limitations described in this article.

## Possible double multifactor authentication

With Microsoft Entra B2B, you can enforce multifactor authentication at the resource organization \(the inviting organization\). The reasons for this approach are detailed in [Conditional Access for B2B collaboration users](https://learn.microsoft.com/en-us/entra/external-id/authentication-conditional-access). If a partner already has multifactor authentication set up and enforced, their users might have to perform the authentication once in their home organization and then again in yours.

## Instant-on

In the B2B collaboration flows, we add users to the directory and dynamically update them during invitation redemption, app assignment, and so on. The updates and writes ordinarily happen in one directory instance and must be replicated across all instances. Replication is completed once all instances are updated. Sometimes when the object is written or updated in one instance and the call to retrieve this object is to another instance, replication latencies can occur. If that happens, refresh or retry to help. If you're writing an app using our API, then retries with some back-off is a good, defensive practice to alleviate this issue.

## Microsoft Entra directories

Microsoft Entra B2B is subject to Microsoft Entra service directory limits. For details about the number of directories a user can create and the number of directories to which a user or guest user can belong, see [Microsoft Entra service limits and restrictions](https://learn.microsoft.com/en-us/entra/identity/users/directory-service-limits-restrictions).

## Next steps

See the following articles on Microsoft Entra B2B collaboration:

- [Microsoft Entra B2B in government and national clouds](https://learn.microsoft.com/en-us/entra/external-id/b2b-government-national-clouds)
- [What is Microsoft Entra B2B collaboration?](https://learn.microsoft.com/en-us/entra/external-id/what-is-b2b)
- [Delegate B2B collaboration invitations](https://learn.microsoft.com/en-us/entra/external-id/external-collaboration-settings-configure)
