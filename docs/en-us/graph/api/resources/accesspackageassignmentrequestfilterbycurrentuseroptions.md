<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/accesspackageassignmentrequestfilterbycurrentuseroptions?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-07-02 -->

# accessPackageAssignmentRequestFilterByCurrentUserOptions enum type

Namespace: microsoft.graph

The list of current user options that can be used to filter on the [access package assignment requests](https://learn.microsoft.com/en-us/graph/api/accesspackageassignmentrequest-filterbycurrentuser?view=graph-rest-1.0) list.

## Members

The following table lists the members of an [evolvable enumeration](https://learn.microsoft.com/en-us/graph/best-practices-concept#handling-future-members-in-evolvable-enumerations). Use the `Prefer: include-unknown-enum-members` request header to get the following members in this evolvable enum: `targetManager`, `targetAgentIdentitySponsorOrOwner`.

| Member | Description |
| :--- | :--- |
| target | Used to get the `accessPackageAssignmentRequest` objects where the signed-in user is the target. The resulting list includes all the assignment requests, current and expired, that were requested by the caller or for the caller, across all catalogs and access packages. |
| createdBy | Used to get the `accessPackageAssignmentRequest` objects created by the signed-in user. The resulting list includes all of the assignment requests that the caller has created for themselves or on behalf of others, such as in case of admin direct assignment, across all catalogs and access packages. |
| unknownFutureValue | Evolvable enumeration sentinel value. Don't use. |
| targetManager |  |
| targetAgentIdentitySponsorOrOwner |  |
