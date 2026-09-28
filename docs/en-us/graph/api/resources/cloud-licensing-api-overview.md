<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/cloud-licensing-api-overview?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2026-02-06 -->

# Use the cloud licensing API in Microsoft Graph \(preview\)

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

The Microsoft Cloud Licensing platform improves license management by breaking down licenses from various subscriptions into smaller, manageable pools called allotments. The association of licenses to their unique subscriptions enables more granular accounting and reporting for an organization.

The cloud licensing API is defined in the OData subnamespace `microsoft.graph.cloudLicensing`.

## Authentication and permissions

Microsoft Graph controls access to resources via permissions. As a developer, you must specify the permissions you need to access cloud licensing resources. Typically, you specify the permissions in the Microsoft Entra admin center. For more information, see [Microsoft Graph permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

## Common use cases

The following table lists common use cases for the cloud licensing API.

| Use case | REST resources |
| :--- | :--- |
| List and get usage rights | [usageRight](https://learn.microsoft.com/en-us/graph/api/resources/cloudlicensing-usageright?view=graph-rest-beta) |
| List and get allotments | [allotment](https://learn.microsoft.com/en-us/graph/api/resources/cloudlicensing-allotment?view=graph-rest-beta) |
| Create and manage assignments | [assignment](https://learn.microsoft.com/en-us/graph/api/resources/cloudlicensing-assignment?view=graph-rest-beta) |
| Troubleshoot assignment synchronization errors | [assignmentError](https://learn.microsoft.com/en-us/graph/api/resources/cloudlicensing-assignmenterror?view=graph-rest-beta) |
| List and inspect waiting members | [waitingMember](https://learn.microsoft.com/en-us/graph/api/resources/cloudlicensing-waitingmember?view=graph-rest-beta) |

## API design details

The following sections describe design details for the cloud licensing API.

### Allotments

The [allotment](https://learn.microsoft.com/en-us/graph/api/resources/cloudlicensing-allotment?view=graph-rest-beta) entity represents a manageable pool of licenses associated with a subscription. Use allotments to track capacity, supported services, and the subscriptions behind those licenses.

### Assignments

The [assignment](https://learn.microsoft.com/en-us/graph/api/resources/cloudlicensing-assignment?view=graph-rest-beta) entity represents a license assignment that grants a license for an allotment to a user, device, or group. Use the assignments APIs to create, update, list, and remove assignments that consume allotment capacity.

### Assignment errors

The [assignmentError](https://learn.microsoft.com/en-us/graph/api/resources/cloudlicensing-assignmenterror?view=graph-rest-beta) entity surfaces asynchronous synchronization failures that affect assignment processing. Use these APIs to detect, inspect, and troubleshoot assignments that are failed or stuck.

### Subscriptions

The [subscription](https://learn.microsoft.com/en-us/graph/api/resources/cloudlicensing-subscription?view=graph-rest-beta) entity contains basic information about a subscription that supports an allotment, including lifecycle dates and state.

### Usage rights

The [usageRight](https://learn.microsoft.com/en-us/graph/api/resources/cloudlicensing-usageright?view=graph-rest-beta) entity is designed for client and workload license checks, with relationships structured to flow from the user or group to the **usageRight**.

### Waiting members

The [waitingMember](https://learn.microsoft.com/en-us/graph/api/resources/cloudlicensing-waitingmember?view=graph-rest-beta) entity represents a user or device that was added to the waiting room for an allotment due to license capacity limits; it includes how long each member is waiting.

## Next steps

- Explore the resources and methods that are most helpful to your scenario.
- Try the cloud licensing API in the [Graph Explorer](https://developer.microsoft.com/graph/graph-explorer).
