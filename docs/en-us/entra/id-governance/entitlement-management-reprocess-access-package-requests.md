<!-- Source: https://learn.microsoft.com/en-us/entra/id-governance/entitlement-management-reprocess-access-package-requests -->
<!-- Sitemap-Last-Modified: 2025-04-25 -->

# Reprocess requests for an access package in entitlement management

As an access package manager, you can automatically retry a user’s request for access to an access package at any time by using the reprocess functionality. Reprocessing eliminates the need for users to repeat the access package request process if their access to resources isn't successfully provisioned.

Note

You can reprocess a request for up to 14 days from the time that the original request is completed. For requests that were completed more than 14 days ago, users will need to cancel and make new requests in MyAccess.

This article describes how to reprocess requests for an existing access package.

## Prerequisites

To use entitlement management and assign users to access packages, you must have one of the following licenses:

- Microsoft Entra ID P2 or Microsoft Entra ID Governance
- Enterprise Mobility + Security \(EMS\) E5 license

## Open an existing access package and reprocess user requests

If you have a set of users whose requests are in the "Partially Delivered" or "Failed" state, you might need to reprocess some of those requests. Follow these steps to reprocess requests for an existing access package:

1. Sign in to the [Microsoft Entra admin center](https://entra.microsoft.com) as at least an [Identity Governance Administrator](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference#identity-governance-administrator).

   Tip

   Other least privilege roles that can complete this task include the Catalog owner, Access package manager, and Access package assignment manager.
2. Browse to **ID Governance** > **Entitlement management** > **Access package**.
3. On the Access packages,\*\* open the access package.
4. Underneath **Manage** on the left side, select **Requests**.
5. Select all users whose requests you wish to reprocess.
6. Select **Reprocess**.

## Next steps

- [View requests for an access package](https://learn.microsoft.com/en-us/entra/id-governance/entitlement-management-access-package-requests)
- [Approve or deny access requests](https://learn.microsoft.com/en-us/entra/id-governance/entitlement-management-request-approve)
