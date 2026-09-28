<!-- Source: https://learn.microsoft.com/en-us/graph/api/filestoragecontainer-post-columns?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2026-07-01 -->

# Create column

Namespace: microsoft.graph

Create a column for a [fileStorageContainer](https://learn.microsoft.com/en-us/graph/api/resources/filestoragecontainer?view=graph-rest-1.0) that specifies a [columnDefinition](https://learn.microsoft.com/en-us/graph/api/resources/columndefinition?view=graph-rest-1.0).

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ✅ | ✅ | ✅ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | FileStorageContainer.Selected | Not available. |
| Delegated \(personal Microsoft account\) | FileStorageContainer.Selected | Not available. |
| Application | FileStorageContainer.Selected | Not available. |

In addition to Microsoft Graph permissions, your app also must have the necessary container-type level permission or permissions to call this API. For details about container types, see [Container Types](https://learn.microsoft.com/en-us/sharepoint/dev/embedded/concepts/app-concepts/containertypes). To learn more about container-type level permissions, see [SharePoint Embedded Authorization](https://learn.microsoft.com/en-us/sharepoint/dev/embedded/concepts/app-concepts/auth#Authorization).

## HTTP request

```http
POST /storage/fileStorage/containers/{containerId}/columns
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |

## Request body

In the request body, supply a JSON representation of the [columnDefinition](https://learn.microsoft.com/en-us/graph/api/resources/columndefinition?view=graph-rest-1.0) object.

Only the following type-related properties are supported and they're mutually exclusive; a column can only have one of them specified at a time.

| Property | Type | Description |
| :--- | :--- | :--- |
| Boolean | [booleanColumn](https://learn.microsoft.com/en-us/graph/api/resources/booleancolumn?view=graph-rest-1.0) | This column stores Boolean values. |
| choice | [choiceColumn](https://learn.microsoft.com/en-us/graph/api/resources/choicecolumn?view=graph-rest-1.0) | This column stores data from a list of choices. |
| currency | [currencyColumn](https://learn.microsoft.com/en-us/graph/api/resources/currencycolumn?view=graph-rest-1.0) | This column stores currency values. |
| dateTime | [dateTimeColumn](https://learn.microsoft.com/en-us/graph/api/resources/datetimecolumn?view=graph-rest-1.0) | This column stores DateTime values. |
| hyperlinkOrPicture | [hyperlinkOrPictureColumn](https://learn.microsoft.com/en-us/graph/api/resources/hyperlinkorpicturecolumn?view=graph-rest-1.0) | This column stores hyperlink or picture values. |
| number | [numberColumn](https://learn.microsoft.com/en-us/graph/api/resources/numbercolumn?view=graph-rest-1.0) | This column stores number values. |
| personOrGroup | [personOrGroupColumn](https://learn.microsoft.com/en-us/graph/api/resources/personorgroupcolumn?view=graph-rest-1.0) | This column stores Person or Group values. |
| text | [textColumn](https://learn.microsoft.com/en-us/graph/api/resources/textcolumn?view=graph-rest-1.0) | This column stores text values. |

## Response

If successful, this method returns a `201 Created` response code and a [columnDefinition](https://learn.microsoft.com/en-us/graph/api/resources/columndefinition?view=graph-rest-1.0) object in the response body.

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
POST https://graph.microsoft.com/v1.0/storage/fileStorage/containers/b!ISJs1WRro0y0EWgkUYcktDa0mE8zSlFEqFzqRn70Zwp1CEtDEBZgQICPkRbil_5Z/columns
Content-Type: application/json

{
  "description": "test",
  "enforceUniqueValues": false,
  "hidden": false,
  "indexed": false,
  "name": "Title",
  "text": {
    "allowMultipleLines": false,
    "appendChangesToExistingText": false,
    "linesForEditing": 0,
    "maxLength": 255
  }
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models;

var requestBody = new ColumnDefinition
{
	Description = "test",
	EnforceUniqueValues = false,
	Hidden = false,
	Indexed = false,
	Name = "Title",
	Text = new TextColumn
	{
		AllowMultipleLines = false,
		AppendChangesToExistingText = false,
		LinesForEditing = 0,
		MaxLength = 255,
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Storage.FileStorage.Containers["{fileStorageContainer-id}"].Columns.PostAsync(requestBody);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```go


// Code snippets are only available for the latest major version. Current major version is $v1.*

// Dependencies
import (
	  "context"
	  msgraphsdk "github.com/microsoftgraph/msgraph-sdk-go"
	  graphmodels "github.com/microsoftgraph/msgraph-sdk-go/models"
	  //other-imports
)

requestBody := graphmodels.NewColumnDefinition()
description := "test"
requestBody.SetDescription(&description) 
enforceUniqueValues := false
requestBody.SetEnforceUniqueValues(&enforceUniqueValues) 
hidden := false
requestBody.SetHidden(&hidden) 
indexed := false
requestBody.SetIndexed(&indexed) 
name := "Title"
requestBody.SetName(&name) 
text := graphmodels.NewTextColumn()
allowMultipleLines := false
text.SetAllowMultipleLines(&allowMultipleLines) 
appendChangesToExistingText := false
text.SetAppendChangesToExistingText(&appendChangesToExistingText) 
linesForEditing := int32(0)
text.SetLinesForEditing(&linesForEditing) 
maxLength := int32(255)
text.SetMaxLength(&maxLength) 
requestBody.SetText(text)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
columns, err := graphClient.Storage().FileStorage().Containers().ByFileStorageContainerId("fileStorageContainer-id").Columns().Post(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

ColumnDefinition columnDefinition = new ColumnDefinition();
columnDefinition.setDescription("test");
columnDefinition.setEnforceUniqueValues(false);
columnDefinition.setHidden(false);
columnDefinition.setIndexed(false);
columnDefinition.setName("Title");
TextColumn text = new TextColumn();
text.setAllowMultipleLines(false);
text.setAppendChangesToExistingText(false);
text.setLinesForEditing(0);
text.setMaxLength(255);
columnDefinition.setText(text);
ColumnDefinition result = graphClient.storage().fileStorage().containers().byFileStorageContainerId("{fileStorageContainer-id}").columns().post(columnDefinition);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const columnDefinition = {
  description: 'test',
  enforceUniqueValues: false,
  hidden: false,
  indexed: false,
  name: 'Title',
  text: {
    allowMultipleLines: false,
    appendChangesToExistingText: false,
    linesForEditing: 0,
    maxLength: 255
  }
};

await client.api('/storage/fileStorage/containers/b!ISJs1WRro0y0EWgkUYcktDa0mE8zSlFEqFzqRn70Zwp1CEtDEBZgQICPkRbil_5Z/columns')
	.post(columnDefinition);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\ColumnDefinition;
use Microsoft\Graph\Generated\Models\TextColumn;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new ColumnDefinition();
$requestBody->setDescription('test');
$requestBody->setEnforceUniqueValues(false);
$requestBody->setHidden(false);
$requestBody->setIndexed(false);
$requestBody->setName('Title');
$text = new TextColumn();
$text->setAllowMultipleLines(false);
$text->setAppendChangesToExistingText(false);
$text->setLinesForEditing(0);
$text->setMaxLength(255);
$requestBody->setText($text);

$result = $graphServiceClient->storage()->fileStorage()->containers()->byFileStorageContainerId('fileStorageContainer-id')->columns()->post($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.column_definition import ColumnDefinition
from msgraph.generated.models.text_column import TextColumn
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = ColumnDefinition(
	description = "test",
	enforce_unique_values = False,
	hidden = False,
	indexed = False,
	name = "Title",
	text = TextColumn(
		allow_multiple_lines = False,
		append_changes_to_existing_text = False,
		lines_for_editing = 0,
		max_length = 255,
	),
)

result = await graph_client.storage.file_storage.containers.by_file_storage_container_id('fileStorageContainer-id').columns.post(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 201 Created
Content-Type: application/json

{
  "description": "test",
  "displayName": "Title",
  "enforceUniqueValues": false,
  "hidden": false,
  "id": "99ddcf45-e2f7-4f17-82b0-6fba34445103",
  "indexed": false,
  "name": "Title",
  "text": {
    "allowMultipleLines": false,
    "appendChangesToExistingText": false,
    "linesForEditing": 0,
    "maxLength": 255
  }
}
```
