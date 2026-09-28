<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/finding?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-05-07 -->

# finding resource type

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Note

Effective April 1, 2025, Microsoft Entra Permissions Management will no longer be available for purchase, and on October 1, 2025, we'll retire and discontinue support of this product. More information can be found [here](https://aka.ms/MEPMretire).

The output of the permissions usage data analysis performed by Permissions Management to assess risk with identities and resources.

Inherits from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta).

The following resources inherit from this resource type:

- [identityFinding](https://learn.microsoft.com/en-us/graph/api/resources/identityfinding?view=graph-rest-beta)
- [awsExternalSystemAccessFinding](https://learn.microsoft.com/en-us/graph/api/resources/awsexternalsystemaccessfinding?view=graph-rest-beta)
- [awsExternalSystemAccessRoleFinding](https://learn.microsoft.com/en-us/graph/api/resources/awsexternalsystemaccessrolefinding?view=graph-rest-beta)
- [awsIdentityAccessManagementKeyAgeFinding](https://learn.microsoft.com/en-us/graph/api/resources/awsidentityaccessmanagementkeyagefinding?view=graph-rest-beta)
- [awsIdentityAccessManagementKeyUsgeFinding](https://learn.microsoft.com/en-us/graph/api/resources/awsidentityaccessmanagementkeyusagefinding?view=graph-rest-beta)
- [awsSecretInformationAccessFinding](https://learn.microsoft.com/en-us/graph/api/resources/awssecretinformationaccessfinding?view=graph-rest-beta)
- [awsSecurityToolAdministrationFinding](https://learn.microsoft.com/en-us/graph/api/resources/awssecuritytooladministrationfinding?view=graph-rest-beta)
- [encryptedAwsStorageBucketFinding](https://learn.microsoft.com/en-us/graph/api/resources/encryptedawsstoragebucketfinding?view=graph-rest-beta)
- [encryptedAzureStorageAccountFinding](https://learn.microsoft.com/en-us/graph/api/resources/encryptedazurestorageaccountfinding?view=graph-rest-beta)
- [encryptedGcpStorageBucketFinding](https://learn.microsoft.com/en-us/graph/api/resources/encryptedgcpstoragebucketfinding?view=graph-rest-beta)
- [externallyAccessibleAwsStorageBucketFinding](https://learn.microsoft.com/en-us/graph/api/resources/externallyaccessibleawsstoragebucketfinding?view=graph-rest-beta)
- [externallyAccessibleAzureBlobContainerFinding](https://learn.microsoft.com/en-us/graph/api/resources/externallyaccessibleazureblobcontainerfinding?view=graph-rest-beta)
- [externallyAccessibleGcpStorageBucketFinding](https://learn.microsoft.com/en-us/graph/api/resources/externallyaccessiblegcpstoragebucketfinding?view=graph-rest-beta)
- [inactiveGroupFinding](https://learn.microsoft.com/en-us/graph/api/resources/inactivegroupfinding?view=graph-rest-beta)
- [openAwsSecurityGroupFinding](https://learn.microsoft.com/en-us/graph/api/resources/openawssecuritygroupfinding?view=graph-rest-beta)
- [openNetworkAzureSecurityGroupFinding](https://learn.microsoft.com/en-us/graph/api/resources/opennetworkazuresecuritygroupfinding?view=graph-rest-beta)
- [privilegeEscalationFinding](https://learn.microsoft.com/en-us/graph/api/resources/privilegeescalationfinding?view=graph-rest-beta)
- [virtualMachineWithAwsStorageBucketAccessFinding](https://learn.microsoft.com/en-us/graph/api/resources/virtualmachinewithawsstoragebucketaccessfinding?view=graph-rest-beta)

## Methods

None.

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| createdDateTime | DateTimeOffset | Defines when the finding was created. |
| id | String | Unique identifier for the finding. Inherited from [entity](https://learn.microsoft.com/en-us/graph/api/resources/entity?view=graph-rest-beta). |

## Relationships

None.

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "@odata.type": "#microsoft.graph.finding",
  "id": "String (identifier)",
  "createdDateTime": "String (timestamp)"
}
```
