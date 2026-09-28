<!-- Source: https://learn.microsoft.com/en-us/graph/sdks/large-file-upload -->
<!-- Sitemap-Last-Modified: 2024-11-07 -->

# Upload large files using the Microsoft Graph SDKs

Many entities in Microsoft Graph support [resumable file uploads](https://learn.microsoft.com/en-us/graph/api/driveitem-createuploadsession?view=graph-rest-1.0&preserve-view=true) to make it easier to upload large files. Instead of trying to upload the entire file in a single request, the file is sliced into smaller pieces and a request is used to upload a single slice. In order to simplify this process, the Microsoft Graph SDKs implement a large file upload task that manages the uploading of the slices.

## Upload large file to OneDrive

- [C#](#tabpanel_1_csharp)
- [Go](#tabpanel_1_go)
- [Java](#tabpanel_1_java)
- [PHP](#tabpanel_1_PHP)
- [TypeScript](#tabpanel_1_typescript)

```csharp
using var fileStream = File.OpenRead(filePath);

// Use properties to specify the conflict behavior
// IMPORTANT: you must add the following using directive to define DriveUpload:
// using DriveUpload = Microsoft.Graph.Drives.Item.Items.Item.CreateUploadSession;
// For more information, see:
// https://learn.microsoft.com/dotnet/csharp/language-reference/keywords/using-directive#the-using-alias
var uploadSessionRequestBody = new DriveUpload.CreateUploadSessionPostRequestBody
{
    Item = new DriveItemUploadableProperties
    {
        AdditionalData = new Dictionary<string, object>
        {
            { "@microsoft.graph.conflictBehavior", "replace" },
        },
    },
};

// Create the upload session
// itemPath does not need to be a path to an existing item
var myDrive = await graphClient.Me.Drive.GetAsync();
var uploadSession = await graphClient.Drives[myDrive?.Id]
    .Items["root"]
    .ItemWithPath(itemPath)
    .CreateUploadSession
    .PostAsync(uploadSessionRequestBody);

// Max slice size must be a multiple of 320 KiB
int maxSliceSize = 320 * 1024;
var fileUploadTask = new LargeFileUploadTask<DriveItem>(
    uploadSession, fileStream, maxSliceSize, graphClient.RequestAdapter);

var totalLength = fileStream.Length;
// Create a callback that is invoked after each slice is uploaded
IProgress<long> progress = new Progress<long>(prog =>
{
    Console.WriteLine($"Uploaded {prog} bytes of {totalLength} bytes");
});

try
{
    // Upload the file
    var uploadResult = await fileUploadTask.UploadAsync(progress);

    Console.WriteLine(uploadResult.UploadSucceeded ?
        $"Upload complete, item ID: {uploadResult.ItemResponse.Id}" :
        "Upload failed");
}
catch (ODataError ex)
{
    Console.WriteLine($"Error uploading: {ex.Error?.Message}");
}
```

```go
import (
    "context"
    "fmt"
    "os"
    "path/filepath"

    graph "github.com/microsoftgraph/msgraph-sdk-go"
    "github.com/microsoftgraph/msgraph-sdk-go-core/fileuploader"
    "github.com/microsoftgraph/msgraph-sdk-go/drives"
    "github.com/microsoftgraph/msgraph-sdk-go/models"
    "github.com/microsoftgraph/msgraph-sdk-go/users"
)
```

```go
byteStream, _ := os.Open(largeFile)

// Use properties to specify the conflict behavior
itemUploadProperties := models.NewDriveItemUploadableProperties()
itemUploadProperties.SetAdditionalData(map[string]any{"@microsoft.graph.conflictBehavior": "replace"})
uploadSessionRequestBody := drives.NewItemItemsItemCreateUploadSessionPostRequestBody()
uploadSessionRequestBody.SetItem(itemUploadProperties)

// Create the upload session
// itemPath does not need to be a path to an existing item
myDrive, _ := graphClient.Me().Drive().Get(context.Background(), nil)

uploadSession, _ := graphClient.Drives().
    ByDriveId(*myDrive.GetId()).
    Items().
    ByDriveItemId("root:/"+itemPath+":").
    CreateUploadSession().
    Post(context.Background(), uploadSessionRequestBody, nil)

// Max slice size must be a multiple of 320 KiB
maxSliceSize := int64(320 * 1024)
fileUploadTask := fileuploader.NewLargeFileUploadTask[models.DriveItemable](
    graphClient.RequestAdapter,
    uploadSession,
    byteStream,
    maxSliceSize,
    models.CreateDriveItemFromDiscriminatorValue,
    nil)

// Create a callback that is invoked after each slice is uploaded
progress := func(progress int64, total int64) {
    fmt.Printf("Uploaded %d of %d bytes\n", progress, total)
}

// Upload the file
uploadResult := fileUploadTask.Upload(progress)

if uploadResult.GetUploadSucceeded() {
    fmt.Printf("Upload complete, item ID: %s\n", *uploadResult.GetItemResponse().GetId())
} else {
    fmt.Print("Upload failed.\n")
}
```

```java
// Get an input stream for the file
File file = new File(filePath);
InputStream fileStream = new FileInputStream(file);
long streamSize = file.length();

// Set body of the upload session request
CreateUploadSessionPostRequestBody uploadSessionRequest = new CreateUploadSessionPostRequestBody();
DriveItemUploadableProperties properties = new DriveItemUploadableProperties();
properties.getAdditionalData().put("@microsoft.graph.conflictBehavior", "replace");
uploadSessionRequest.setItem(properties);

// Create an upload session
// ItemPath does not need to be a path to an existing item
String myDriveId = graphClient.me().drive().get().getId();
UploadSession uploadSession = graphClient.drives()
        .byDriveId(myDriveId)
        .items()
        .byDriveItemId("root:/"+itemPath+":")
        .createUploadSession()
        .post(uploadSessionRequest);

// Create the upload task
int maxSliceSize = 320 * 10;
LargeFileUploadTask<DriveItem> largeFileUploadTask = new LargeFileUploadTask<>(
        graphClient.getRequestAdapter(),
        uploadSession,
        fileStream,
        streamSize,
        maxSliceSize,
        DriveItem::createFromDiscriminatorValue);

int maxAttempts = 5;
// Create a callback used by the upload provider
IProgressCallback callback = (current, max) -> System.out.println(
            String.format("Uploaded %d bytes of %d total bytes", current, max));

// Do the upload
try {
    UploadResult<DriveItem> uploadResult = largeFileUploadTask.upload(maxAttempts, callback);
    if (uploadResult.isUploadSuccessful()) {
        System.out.println("Upload complete");
        System.out.println("Item ID: " + uploadResult.itemResponse.getId());
    } else {
        System.out.println("Upload failed");
    }
} catch (CancellationException ex) {
    System.out.println("Error uploading: " + ex.getMessage());
}
```

```php
// Create a file stream
$file = GuzzleHttp\Psr7\Utils::streamFor(fopen($filePath, 'r'));

// Create the upload session request
$uploadProperties = new Models\DriveItemUploadableProperties();
$uploadProperties->setAdditionalData([
    '@microsoft.graph.conflictBehavior' => 'replace'
]);

// use Microsoft\Graph\Generated\Drives\Item\Items\Item\CreateUploadSession\CreateUploadSessionPostRequestBody
// as DriveItemCreateUploadSessionPostRequestBody;
$uploadSessionRequest = new DriveItemCreateUploadSessionPostRequestBody();
$uploadSessionRequest->setItem($uploadProperties);

// Create the upload session
/** @var Models\Drive $drive */
$drive = $graphClient->me()->drive()->get()->wait();
$uploadSession = $graphClient->drives()
    ->byDriveId($drive->getId())
    ->items()
    ->byDriveItemId('root:/'.$itemPath.':')
    ->createUploadSession()
    ->post($uploadSessionRequest)
    ->wait();

$largeFileUpload = new LargeFileUploadTask($uploadSession, $graphClient->getRequestAdapter(), $file);
$totalSize = $file->getSize();
$progress = function(array $prog) use ($totalSize): void {
    echo 'Uploaded '.$prog[1].' of '.$totalSize.' bytes'.PHP_EOL;
};

try {
    $largeFileUpload->upload($progress)->wait();
} catch (\Psr\Http\Client\NetworkExceptionInterface $ex) {
    $largeFileUpload->resume()->wait();
}
```

```typescript
// readFile from fs/promises
const file = await readFile(filePath);
// basename from path
const fileName = basename(filePath);

const options: OneDriveLargeFileUploadOptions = {
  // Relative path from root folder
  path: targetFolderPath,
  fileName: fileName,
  rangeSize: 1024 * 1024,
  uploadEventHandlers: {
    // Called as each "slice" of the file is uploaded
    progress: (range, _) => {
      console.log(`Uploaded bytes ${range?.minValue} to ${range?.maxValue}`);
    },
  },
};

// Create FileUpload object
const fileUpload = new FileUpload(file, fileName, file.byteLength);
// Create a OneDrive upload task
const uploadTask = await OneDriveLargeFileUploadTask.createTaskWithFileObject(
  graphClient,
  fileUpload,
  options,
);

// Do the upload
const uploadResult: UploadResult = await uploadTask.upload();

// The response body will be of the corresponding type of the
// item being uploaded. For OneDrive, this is a DriveItem
const driveItem = uploadResult.responseBody as DriveItem;
console.log(`Uploaded file with ID: ${driveItem.id}`);
```

## Resuming a file upload

The Microsoft Graph SDKs support [resuming in-progress uploads](https://learn.microsoft.com/en-us/graph/api/driveitem-createuploadsession?view=graph-rest-1.0&preserve-view=true#resuming-an-in-progress-upload). If your application encounters a connection interruption or a 5.x.x HTTP status during upload, you can resume the upload.

- [C#](#tabpanel_2_csharp)
- [Go](#tabpanel_2_go)
- [Java](#tabpanel_2_java)
- [PHP](#tabpanel_2_PHP)
- [TypeScript](#tabpanel_2_typescript)

```csharp
await fileUploadTask.ResumeAsync(progress);
```

```go
import (
    "context"
    "fmt"
    "os"
    "path/filepath"

    graph "github.com/microsoftgraph/msgraph-sdk-go"
    "github.com/microsoftgraph/msgraph-sdk-go-core/fileuploader"
    "github.com/microsoftgraph/msgraph-sdk-go/drives"
    "github.com/microsoftgraph/msgraph-sdk-go/models"
    "github.com/microsoftgraph/msgraph-sdk-go/users"
)
```

```go
fileUploadTask.Resume(progress)
```

```java
int maxAttempts = 5;
largeFileUploadTask.resume(maxAttempts, callback);
```

```php
$largeFileUpload->resume();
```

```typescript
const resumedFile = (await uploadTask.resume()) as DriveItem;
```

## Upload large attachment to Outlook message

- [C#](#tabpanel_3_csharp)
- [Go](#tabpanel_3_go)
- [Java](#tabpanel_3_java)
- [PHP](#tabpanel_3_PHP)
- [TypeScript](#tabpanel_3_typescript)

```csharp
// Create message
var draftMessage = new Message
{
    Subject = "Large attachment",
};

var savedDraft = await graphClient.Me
    .Messages
    .PostAsync(draftMessage);

using var fileStream = File.OpenRead(filePath);
var largeAttachment = new AttachmentItem
{
    AttachmentType = AttachmentType.File,
    Name = Path.GetFileName(filePath),
    Size = fileStream.Length,
};

// IMPORTANT: you must add the following using directive to define AttachmentUpload:
// using AttachmentUpload = Microsoft.Graph.Me.Messages.Item.Attachments.CreateUploadSession;
// For more information, see:
// https://learn.microsoft.com/dotnet/csharp/language-reference/keywords/using-directive#the-using-alias
var uploadSessionRequestBody = new AttachmentUpload.CreateUploadSessionPostRequestBody
{
    AttachmentItem = largeAttachment,
};

var uploadSession = await graphClient.Me
    .Messages[savedDraft?.Id]
    .Attachments
    .CreateUploadSession
    .PostAsync(uploadSessionRequestBody);

// Max slice size must be a multiple of 320 KiB
int maxSliceSize = 320 * 1024;
var fileUploadTask = new LargeFileUploadTask<FileAttachment>(
    uploadSession, fileStream, maxSliceSize, graphClient.RequestAdapter);

var totalLength = fileStream.Length;
// Create a callback that is invoked after each slice is uploaded
IProgress<long> progress = new Progress<long>(prog =>
{
    Console.WriteLine($"Uploaded {prog} bytes of {totalLength} bytes");
});

try
{
    // Upload the file
    var uploadResult = await fileUploadTask.UploadAsync(progress);
    Console.WriteLine(uploadResult.UploadSucceeded ? "Upload complete" : "Upload failed");
}
catch (ODataError ex)
{
    Console.WriteLine($"Error uploading: {ex.Error?.Message}");
}
```

```go
import (
    "context"
    "fmt"
    "os"
    "path/filepath"

    graph "github.com/microsoftgraph/msgraph-sdk-go"
    "github.com/microsoftgraph/msgraph-sdk-go-core/fileuploader"
    "github.com/microsoftgraph/msgraph-sdk-go/drives"
    "github.com/microsoftgraph/msgraph-sdk-go/models"
    "github.com/microsoftgraph/msgraph-sdk-go/users"
)
```

```go
// Create message
message := models.NewMessage()
subject := "Large attachment"
message.SetSubject(&subject)

savedDraft, _ := graphClient.Me().Messages().Post(context.Background(), message, nil)

// Set up the attachment
byteStream, _ := os.Open(largeFile)
largeAttachment := models.NewAttachmentItem()
attachmentType := models.FILE_ATTACHMENTTYPE
largeAttachment.SetAttachmentType(&attachmentType)
fileName := filepath.Base(largeFile)
largeAttachment.SetName(&fileName)
fileInfo, _ := byteStream.Stat()
fileSize := fileInfo.Size()
largeAttachment.SetSize(&fileSize)

uploadSessionRequestBody := users.NewItemMessagesItemAttachmentsCreateUploadSessionPostRequestBody()
uploadSessionRequestBody.SetAttachmentItem(largeAttachment)

uploadSession, _ := graphClient.Me().
    Messages().
    ByMessageId(*savedDraft.GetId()).
    Attachments().
    CreateUploadSession().
    Post(context.Background(), uploadSessionRequestBody, nil)

// Max slice size must be a multiple of 320 KiB
maxSliceSize := int64(320 * 1024)
fileUploadTask := fileuploader.NewLargeFileUploadTask[models.FileAttachmentable](
    graphClient.RequestAdapter,
    uploadSession,
    byteStream,
    maxSliceSize,
    models.CreateFileAttachmentFromDiscriminatorValue,
    nil)

// Create a callback that is invoked after each slice is uploaded
progress := func(progress int64, total int64) {
    fmt.Printf("Uploaded %d of %d bytes\n", progress, total)
}

// Upload the file
uploadResult := fileUploadTask.Upload(progress)

if uploadResult.GetUploadSucceeded() {
    fmt.Print("Upload complete\n")
} else {
    fmt.Print("Upload failed.\n")
}
```

```java
// Create message
Message draftMessage = new Message();
draftMessage.setSubject("Large attachment");
Message savedDraft = graphClient.me().messages().post(draftMessage);

// Get an input stream for the file
File file = new File(filePath);
InputStream fileStream = new FileInputStream(file);
long streamSize = file.length();

final AttachmentItem largeAttachment = new AttachmentItem();
largeAttachment.setAttachmentType(AttachmentType.File);
largeAttachment.setName(file.getName());
largeAttachment.setSize(streamSize);

com.microsoft.graph.users.item.messages.item.attachments.createuploadsession.CreateUploadSessionPostRequestBody uploadRequestBody
        = new com.microsoft.graph.users.item.messages.item.attachments.createuploadsession.CreateUploadSessionPostRequestBody();
uploadRequestBody.setAttachmentItem(largeAttachment);

final UploadSession uploadSession = graphClient.me()
        .messages()
        .byMessageId(savedDraft.getId())
        .attachments()
        .createUploadSession()
        .post(uploadRequestBody);

LargeFileUploadTask<FileAttachment> largeFileUploadTask = new LargeFileUploadTask<>(
        graphClient.getRequestAdapter(),
        uploadSession,
        fileStream,
        streamSize,
        FileAttachment::createFromDiscriminatorValue);

int maxAttempts = 5;
// Create a callback used by the upload provider
IProgressCallback callback = (current, max) -> System.out.println(
        String.format("Uploaded %d bytes of %d total bytes", current, max));

// Do the upload
try {
    UploadResult<FileAttachment> uploadResult = largeFileUploadTask.upload(maxAttempts, callback);
    if (uploadResult.isUploadSuccessful()) {
        System.out.println("Upload complete");
        System.out.println("Item ID: " + uploadResult.itemResponse.getId());
    } else {
        System.out.println("Upload failed");
    }
} catch (CancellationException ex) {
    System.out.println("Error uploading: " + ex.getMessage());
}
```

```php
// Create a message
$draftMessage = new Models\Message();
$draftMessage->setSubject('Large attachment');

/** @var Models\Message $savedDraft */
$savedDraft = $graphClient->me()
    ->messages()
    ->post($draftMessage)
    ->wait();

// Create a file stream
$file = GuzzleHttp\Psr7\Utils::streamFor(fopen($filePath, 'r'));

// Create an attachment
$attachment = new Models\AttachmentItem();
$attachment->setAttachmentType(new Models\AttachmentType(Models\AttachmentType::FILE));
$attachment->setName(basename($filePath));
$attachment->setSize($file->getSize());

// use Microsoft\Graph\Generated\Users\Item\Messages\Item\Attachments\CreateUploadSession\CreateUploadSessionPostRequestBody
// as AttachmentCreateUploadSessionPostRequestBody;
$uploadSessionRequest = new AttachmentCreateUploadSessionPostRequestBody();
$uploadSessionRequest->setAttachmentItem($attachment);

// Create the upload session
$uploadSession = $graphClient->me()
    ->messages()
    ->byMessageId($savedDraft->getId())
    ->attachments()
    ->createUploadSession()
    ->post($uploadSessionRequest)
    ->wait();

$largeFileUpload = new LargeFileUploadTask($uploadSession, $graphClient->getRequestAdapter(), $file);
$totalSize = $file->getSize();
$progress = function(array $prog) use ($totalSize): void {
    echo 'Uploaded '.$prog[1].' of '.$totalSize.' bytes'.PHP_EOL;
};

try {
    $largeFileUpload->upload($progress)->wait();
} catch (\Psr\Http\Client\NetworkExceptionInterface $ex) {
    $largeFileUpload->resume()->wait();
}
```

```typescript
// readFile from fs/promises
const file = await readFile(filePath);
// basename from path
const fileName = basename(filePath);

const options: LargeFileUploadTaskOptions = {
  rangeSize: 1024 * 1024,
  uploadEventHandlers: {
    // Called as each "slice" of the file is uploaded
    progress: (range, _) => {
      console.log(`Uploaded bytes ${range?.minValue} to ${range?.maxValue}`);
    },
  },
};

// Create a draft message
const message: Message = await graphClient.api('/me/messages').post({
  subject: 'Large file attachment',
});

// Create upload session using draft message's ID
const uploadUrl = `/me/messages/${message.id}/attachments/createUploadSession`;
const uploadSession = await LargeFileUploadTask.createUploadSession(
  graphClient,
  uploadUrl,
  {
    AttachmentItem: {
      attachmentType: 'file',
      name: fileName,
      size: file.byteLength,
    },
  },
);

// Create file upload
const fileUpload = new FileUpload(file, fileName, file.byteLength);

// Create upload task
const uploadTask = new LargeFileUploadTask(
  graphClient,
  fileUpload,
  uploadSession,
  options,
);

// Upload the file
const uploadResult = await uploadTask.upload();
console.log(`File uploaded to ${uploadResult.location}`);
```
