<!-- Source: https://learn.microsoft.com/en-us/graph/api/cloudpcsnapshot-importsnapshot?view=graph-rest-beta -->
<!-- Sitemap-Last-Modified: 2025-11-05 -->

# cloudPCSnapshot: importSnapshot

Namespace: microsoft.graph

Important

APIs under the `/beta` version in Microsoft Graph are subject to change. Use of these APIs in production applications is not supported. To determine whether an API is available in v1.0, use the **Version** selector.

Import the [snapshot](https://learn.microsoft.com/en-us/graph/api/resources/cloudpcsnapshot?view=graph-rest-beta) from the customer-managed storage account using the provided information, and store it in the Azure storage account within the Cloud PC service on behalf of the customer.

To provision a new Cloud PC for a licensed user, import a valid .vhd snapshot from a customer-managed storage account into the Azure storage account used by the Cloud PC service.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ✅ | ❌ | ❌ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | CloudPC.Read.All | CloudPC.ReadWrite.All |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | CloudPC.Read.All | CloudPC.ReadWrite.All |

## HTTP request

```http
POST /deviceManagement/virtualEndpoint/snapshots/importSnapshot
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |

## Request body

In the request body, supply a JSON representation of the parameters.

The following table shows the parameters that can be used with this method.

| Parameter | Type | Description |
| :--- | :--- | :--- |
| assignedUserId | String | The unique identifier of the user assigned to the snapshot, who uses the imported snapshot to provision a new Cloud PC. |
| sourceFiles | [cloudPcSnapshotImportActionDetail](https://learn.microsoft.com/en-us/graph/api/resources/cloudpcsnapshotimportactiondetail?view=graph-rest-beta) collection | Detailed source information for the files to be imported. |

## Response

If successful, this method returns a `200 OK` response code and a [cloudPcSnapshotImportActionResult](https://learn.microsoft.com/en-us/graph/api/resources/cloudpcsnapshotimportactionresult?view=graph-rest-beta) object in the response body.

## Examples

### Request

The following example shows a request.

- [HTTP](#tabpanel_1_http)
- [C#](#tabpanel_1_csharp)
- [Go](#tabpanel_1_go)
- [Java](#tabpanel_1_java)
- [JavaScript](#tabpanel_1_javascript)
- [PHP](#tabpanel_1_php)
- [Python](#tabpanel_1_python)

```http
POST https://graph.microsoft.com/beta/deviceManagement/virtualEndpoint/snapshots/importSnapshot
Content-Type: application/json

{
  "sourceFiles": [
    {
      "sourceType": "azureStorageAccount",
      "fileType": "dataFile",
      "storageBlobInfo": {
        "storageAccountId": "/subscriptions/subscription-id/resourceGroups/resource-group-name/providers/Microsoft.Storage/storageAccounts/account-name",
        "containerName": "myContainer",
        "blobName": "snapshotForCloudPc.vhd"
      }
    },
    {
      "sourceType": "azureStorageAccount",
      "fileType": "virtualMachineGuestState",
      "storageBlobInfo": {
        "storageAccountId": "/subscriptions/subscription-idresourceGroups/resource-group-name/providers/Microsoft.Storage/storageAccounts/account-name",
        "containerName": "myContainer",
        "blobName": "virtualMachineGuestState.vhd"
      }
    }
  ],
  "assignedUserId": "93aff428-61f2-467f-a879-1102af6fd4a8"
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Beta.DeviceManagement.VirtualEndpoint.Snapshots.ImportSnapshot;
using Microsoft.Graph.Beta.Models;

var requestBody = new ImportSnapshotPostRequestBody
{
	SourceFiles = new List<CloudPcSnapshotImportActionDetail>
	{
		new CloudPcSnapshotImportActionDetail
		{
			SourceType = CloudPcSnapshotImportSourceType.AzureStorageAccount,
			FileType = CloudPcSnapshotImportFileType.DataFile,
			StorageBlobInfo = new CloudPcStorageBlobDetail
			{
				StorageAccountId = "/subscriptions/subscription-id/resourceGroups/resource-group-name/providers/Microsoft.Storage/storageAccounts/account-name",
				ContainerName = "myContainer",
				AdditionalData = new Dictionary<string, object>
				{
					{
						"blobName" , "snapshotForCloudPc.vhd"
					},
				},
			},
		},
		new CloudPcSnapshotImportActionDetail
		{
			SourceType = CloudPcSnapshotImportSourceType.AzureStorageAccount,
			FileType = CloudPcSnapshotImportFileType.VirtualMachineGuestState,
			StorageBlobInfo = new CloudPcStorageBlobDetail
			{
				StorageAccountId = "/subscriptions/subscription-idresourceGroups/resource-group-name/providers/Microsoft.Storage/storageAccounts/account-name",
				ContainerName = "myContainer",
				AdditionalData = new Dictionary<string, object>
				{
					{
						"blobName" , "virtualMachineGuestState.vhd"
					},
				},
			},
		},
	},
	AssignedUserId = "93aff428-61f2-467f-a879-1102af6fd4a8",
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.DeviceManagement.VirtualEndpoint.Snapshots.ImportSnapshot.PostAsync(requestBody);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```go


// Code snippets are only available for the latest major version. Current major version is $v0.*

// Dependencies
import (
	  "context"
	  msgraphsdk "github.com/microsoftgraph/msgraph-beta-sdk-go"
	  graphdevicemanagement "github.com/microsoftgraph/msgraph-beta-sdk-go/devicemanagement"
	  graphmodels "github.com/microsoftgraph/msgraph-beta-sdk-go/models"
	  //other-imports
)

requestBody := graphdevicemanagement.NewImportSnapshotPostRequestBody()


cloudPcSnapshotImportActionDetail := graphmodels.NewCloudPcSnapshotImportActionDetail()
sourceType := graphmodels.AZURESTORAGEACCOUNT_CLOUDPCSNAPSHOTIMPORTSOURCETYPE 
cloudPcSnapshotImportActionDetail.SetSourceType(&sourceType) 
fileType := graphmodels.DATAFILE_CLOUDPCSNAPSHOTIMPORTFILETYPE 
cloudPcSnapshotImportActionDetail.SetFileType(&fileType) 
storageBlobInfo := graphmodels.NewCloudPcStorageBlobDetail()
storageAccountId := "/subscriptions/subscription-id/resourceGroups/resource-group-name/providers/Microsoft.Storage/storageAccounts/account-name"
storageBlobInfo.SetStorageAccountId(&storageAccountId) 
containerName := "myContainer"
storageBlobInfo.SetContainerName(&containerName) 
additionalData := map[string]interface{}{
	"blobName" : "snapshotForCloudPc.vhd", 
}
storageBlobInfo.SetAdditionalData(additionalData)
cloudPcSnapshotImportActionDetail.SetStorageBlobInfo(storageBlobInfo)
cloudPcSnapshotImportActionDetail1 := graphmodels.NewCloudPcSnapshotImportActionDetail()
sourceType := graphmodels.AZURESTORAGEACCOUNT_CLOUDPCSNAPSHOTIMPORTSOURCETYPE 
cloudPcSnapshotImportActionDetail1.SetSourceType(&sourceType) 
fileType := graphmodels.VIRTUALMACHINEGUESTSTATE_CLOUDPCSNAPSHOTIMPORTFILETYPE 
cloudPcSnapshotImportActionDetail1.SetFileType(&fileType) 
storageBlobInfo := graphmodels.NewCloudPcStorageBlobDetail()
storageAccountId := "/subscriptions/subscription-idresourceGroups/resource-group-name/providers/Microsoft.Storage/storageAccounts/account-name"
storageBlobInfo.SetStorageAccountId(&storageAccountId) 
containerName := "myContainer"
storageBlobInfo.SetContainerName(&containerName) 
additionalData := map[string]interface{}{
	"blobName" : "virtualMachineGuestState.vhd", 
}
storageBlobInfo.SetAdditionalData(additionalData)
cloudPcSnapshotImportActionDetail1.SetStorageBlobInfo(storageBlobInfo)

sourceFiles := []graphmodels.CloudPcSnapshotImportActionDetailable {
	cloudPcSnapshotImportActionDetail,
	cloudPcSnapshotImportActionDetail1,
}
requestBody.SetSourceFiles(sourceFiles)
assignedUserId := "93aff428-61f2-467f-a879-1102af6fd4a8"
requestBody.SetAssignedUserId(&assignedUserId) 

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
importSnapshot, err := graphClient.DeviceManagement().VirtualEndpoint().Snapshots().ImportSnapshot().Post(context.Background(), requestBody, nil)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

com.microsoft.graph.beta.devicemanagement.virtualendpoint.snapshots.importsnapshot.ImportSnapshotPostRequestBody importSnapshotPostRequestBody = new com.microsoft.graph.beta.devicemanagement.virtualendpoint.snapshots.importsnapshot.ImportSnapshotPostRequestBody();
LinkedList<CloudPcSnapshotImportActionDetail> sourceFiles = new LinkedList<CloudPcSnapshotImportActionDetail>();
CloudPcSnapshotImportActionDetail cloudPcSnapshotImportActionDetail = new CloudPcSnapshotImportActionDetail();
cloudPcSnapshotImportActionDetail.setSourceType(CloudPcSnapshotImportSourceType.AzureStorageAccount);
cloudPcSnapshotImportActionDetail.setFileType(CloudPcSnapshotImportFileType.DataFile);
CloudPcStorageBlobDetail storageBlobInfo = new CloudPcStorageBlobDetail();
storageBlobInfo.setStorageAccountId("/subscriptions/subscription-id/resourceGroups/resource-group-name/providers/Microsoft.Storage/storageAccounts/account-name");
storageBlobInfo.setContainerName("myContainer");
HashMap<String, Object> additionalData = new HashMap<String, Object>();
additionalData.put("blobName", "snapshotForCloudPc.vhd");
storageBlobInfo.setAdditionalData(additionalData);
cloudPcSnapshotImportActionDetail.setStorageBlobInfo(storageBlobInfo);
sourceFiles.add(cloudPcSnapshotImportActionDetail);
CloudPcSnapshotImportActionDetail cloudPcSnapshotImportActionDetail1 = new CloudPcSnapshotImportActionDetail();
cloudPcSnapshotImportActionDetail1.setSourceType(CloudPcSnapshotImportSourceType.AzureStorageAccount);
cloudPcSnapshotImportActionDetail1.setFileType(CloudPcSnapshotImportFileType.VirtualMachineGuestState);
CloudPcStorageBlobDetail storageBlobInfo1 = new CloudPcStorageBlobDetail();
storageBlobInfo1.setStorageAccountId("/subscriptions/subscription-idresourceGroups/resource-group-name/providers/Microsoft.Storage/storageAccounts/account-name");
storageBlobInfo1.setContainerName("myContainer");
HashMap<String, Object> additionalData1 = new HashMap<String, Object>();
additionalData1.put("blobName", "virtualMachineGuestState.vhd");
storageBlobInfo1.setAdditionalData(additionalData1);
cloudPcSnapshotImportActionDetail1.setStorageBlobInfo(storageBlobInfo1);
sourceFiles.add(cloudPcSnapshotImportActionDetail1);
importSnapshotPostRequestBody.setSourceFiles(sourceFiles);
importSnapshotPostRequestBody.setAssignedUserId("93aff428-61f2-467f-a879-1102af6fd4a8");
var result = graphClient.deviceManagement().virtualEndpoint().snapshots().importSnapshot().post(importSnapshotPostRequestBody);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const cloudPcSnapshotImportActionResult = {
  sourceFiles: [
    {
      sourceType: 'azureStorageAccount',
      fileType: 'dataFile',
      storageBlobInfo: {
        storageAccountId: '/subscriptions/subscription-id/resourceGroups/resource-group-name/providers/Microsoft.Storage/storageAccounts/account-name',
        containerName: 'myContainer',
        blobName: 'snapshotForCloudPc.vhd'
      }
    },
    {
      sourceType: 'azureStorageAccount',
      fileType: 'virtualMachineGuestState',
      storageBlobInfo: {
        storageAccountId: '/subscriptions/subscription-idresourceGroups/resource-group-name/providers/Microsoft.Storage/storageAccounts/account-name',
        containerName: 'myContainer',
        blobName: 'virtualMachineGuestState.vhd'
      }
    }
  ],
  assignedUserId: '93aff428-61f2-467f-a879-1102af6fd4a8'
};

await client.api('/deviceManagement/virtualEndpoint/snapshots/importSnapshot')
	.version('beta')
	.post(cloudPcSnapshotImportActionResult);
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\Beta\GraphServiceClient;
use Microsoft\Graph\Beta\Generated\DeviceManagement\VirtualEndpoint\Snapshots\ImportSnapshot\ImportSnapshotPostRequestBody;
use Microsoft\Graph\Beta\Generated\Models\CloudPcSnapshotImportActionDetail;
use Microsoft\Graph\Beta\Generated\Models\CloudPcSnapshotImportSourceType;
use Microsoft\Graph\Beta\Generated\Models\CloudPcSnapshotImportFileType;
use Microsoft\Graph\Beta\Generated\Models\CloudPcStorageBlobDetail;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new ImportSnapshotPostRequestBody();
$sourceFilesCloudPcSnapshotImportActionDetail1 = new CloudPcSnapshotImportActionDetail();
$sourceFilesCloudPcSnapshotImportActionDetail1->setSourceType(new CloudPcSnapshotImportSourceType('azureStorageAccount'));
$sourceFilesCloudPcSnapshotImportActionDetail1->setFileType(new CloudPcSnapshotImportFileType('dataFile'));
$sourceFilesCloudPcSnapshotImportActionDetail1StorageBlobInfo = new CloudPcStorageBlobDetail();
$sourceFilesCloudPcSnapshotImportActionDetail1StorageBlobInfo->setStorageAccountId('/subscriptions/subscription-id/resourceGroups/resource-group-name/providers/Microsoft.Storage/storageAccounts/account-name');
$sourceFilesCloudPcSnapshotImportActionDetail1StorageBlobInfo->setContainerName('myContainer');
$additionalData = [
	'blobName' => 'snapshotForCloudPc.vhd',
];
$sourceFilesCloudPcSnapshotImportActionDetail1StorageBlobInfo->setAdditionalData($additionalData);
$sourceFilesCloudPcSnapshotImportActionDetail1->setStorageBlobInfo($sourceFilesCloudPcSnapshotImportActionDetail1StorageBlobInfo);
$sourceFilesArray []= $sourceFilesCloudPcSnapshotImportActionDetail1;
$sourceFilesCloudPcSnapshotImportActionDetail2 = new CloudPcSnapshotImportActionDetail();
$sourceFilesCloudPcSnapshotImportActionDetail2->setSourceType(new CloudPcSnapshotImportSourceType('azureStorageAccount'));
$sourceFilesCloudPcSnapshotImportActionDetail2->setFileType(new CloudPcSnapshotImportFileType('virtualMachineGuestState'));
$sourceFilesCloudPcSnapshotImportActionDetail2StorageBlobInfo = new CloudPcStorageBlobDetail();
$sourceFilesCloudPcSnapshotImportActionDetail2StorageBlobInfo->setStorageAccountId('/subscriptions/subscription-idresourceGroups/resource-group-name/providers/Microsoft.Storage/storageAccounts/account-name');
$sourceFilesCloudPcSnapshotImportActionDetail2StorageBlobInfo->setContainerName('myContainer');
$additionalData = [
	'blobName' => 'virtualMachineGuestState.vhd',
];
$sourceFilesCloudPcSnapshotImportActionDetail2StorageBlobInfo->setAdditionalData($additionalData);
$sourceFilesCloudPcSnapshotImportActionDetail2->setStorageBlobInfo($sourceFilesCloudPcSnapshotImportActionDetail2StorageBlobInfo);
$sourceFilesArray []= $sourceFilesCloudPcSnapshotImportActionDetail2;
$requestBody->setSourceFiles($sourceFilesArray);

$requestBody->setAssignedUserId('93aff428-61f2-467f-a879-1102af6fd4a8');

$result = $graphServiceClient->deviceManagement()->virtualEndpoint()->snapshots()->importSnapshot()->post($requestBody)->wait();
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph_beta import GraphServiceClient
from msgraph_beta.generated.devicemanagement.virtualendpoint.snapshots.import_snapshot.import_snapshot_post_request_body import ImportSnapshotPostRequestBody
from msgraph_beta.generated.models.cloud_pc_snapshot_import_action_detail import CloudPcSnapshotImportActionDetail
from msgraph_beta.generated.models.cloud_pc_snapshot_import_source_type import CloudPcSnapshotImportSourceType
from msgraph_beta.generated.models.cloud_pc_snapshot_import_file_type import CloudPcSnapshotImportFileType
from msgraph_beta.generated.models.cloud_pc_storage_blob_detail import CloudPcStorageBlobDetail
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = ImportSnapshotPostRequestBody(
	source_files = [
		CloudPcSnapshotImportActionDetail(
			source_type = CloudPcSnapshotImportSourceType.AzureStorageAccount,
			file_type = CloudPcSnapshotImportFileType.DataFile,
			storage_blob_info = CloudPcStorageBlobDetail(
				storage_account_id = "/subscriptions/subscription-id/resourceGroups/resource-group-name/providers/Microsoft.Storage/storageAccounts/account-name",
				container_name = "myContainer",
				additional_data = {
						"blob_name" : "snapshotForCloudPc.vhd",
				}
			),
		),
		CloudPcSnapshotImportActionDetail(
			source_type = CloudPcSnapshotImportSourceType.AzureStorageAccount,
			file_type = CloudPcSnapshotImportFileType.VirtualMachineGuestState,
			storage_blob_info = CloudPcStorageBlobDetail(
				storage_account_id = "/subscriptions/subscription-idresourceGroups/resource-group-name/providers/Microsoft.Storage/storageAccounts/account-name",
				container_name = "myContainer",
				additional_data = {
						"blob_name" : "virtualMachineGuestState.vhd",
				}
			),
		),
	],
	assigned_user_id = "93aff428-61f2-467f-a879-1102af6fd4a8",
)

result = await graph_client.device_management.virtual_endpoint.snapshots.import_snapshot.post(request_body)
```

Important

Microsoft Graph SDKs use the v1.0 version of the API by default, and do not support all the types, properties, and APIs available in the beta version. For details about accessing the beta API with the SDK, see [Use the Microsoft Graph SDKs with the beta API](https://learn.microsoft.com/en-us/graph/sdks/use-beta).

For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

The following example shows the response.

```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "@odata.context": "https://graph.microsoft.com/beta/$metadata#microsoft.graph.cloudPcSnapshotImportActionResult",
  "filename": "snapshotForCloudPc",
  "usageStatus": "notUsed",
  "importStatus": "inProgress",
  "assignedUserPrincipalName": "snapshot@contoso.com",
  "policyName": "Test_ProvisioningPolicy",
  "startDateTime": "2025-01-13T15:13:14Z",
  "endDateTime": null,
  "additionalDetail": null
}
```
