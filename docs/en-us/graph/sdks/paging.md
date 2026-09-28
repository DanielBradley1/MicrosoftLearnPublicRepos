<!-- Source: https://learn.microsoft.com/en-us/graph/sdks/paging -->
<!-- Sitemap-Last-Modified: 2025-04-03 -->

# Page through a collection using the Microsoft Graph SDKs

For performance reasons, collections of entities are often split into pages and each page is returned with a URL to the next page. The **PageIterator** class simplifies consuming of paged collections. **PageIterator** handles enumerating the current page and requesting subsequent pages automatically.

Alternatively, you can use the `@odata.nextLink` property to [manually request subsequent pages](#manually-requesting-subsequent-pages).

## Request headers

If you send any additional request headers in your initial request, those headers are not included by default in subsequent page requests. If those headers need to be sent on subsequent requests, you must set them explicitly.

## Iterate over all the messages

The following example shows iterating over all the messages in a user's mailbox.

Tip

This example sets a small page size using the `top` parameter for demonstration purposes. You can set the page size up to 999 to minimize the number of requests that are necessary.

- [C#](#tabpanel_1_csharp)
- [Go](#tabpanel_1_go)
- [Java](#tabpanel_1_java)
- [PHP](#tabpanel_1_PHP)
- [TypeScript](#tabpanel_1_typescript)

```csharp
var messages = await graphClient.Me.Messages
    .GetAsync(requestConfiguration =>
    {
        requestConfiguration.QueryParameters.Top = 10;
        requestConfiguration.QueryParameters.Select =
            ["sender", "subject", "body"];
        requestConfiguration.Headers.Add(
            "Prefer", "outlook.body-content-type=\"text\"");
    });

if (messages == null)
{
    return;
}

var pageIterator = PageIterator<Message, MessageCollectionResponse>
    .CreatePageIterator(
        graphClient,
        messages,
        // Callback executed for each item in
        // the collection
        (msg) =>
        {
            Console.WriteLine(msg.Subject);
            return true;
        },
        // Used to configure subsequent page
        // requests
        (req) =>
        {
            // Re-add the header to subsequent requests
            req.Headers.Add("Prefer", "outlook.body-content-type=\"text\"");
            return req;
        });

await pageIterator.IterateAsync();
```

```go
import (
    "context"
    "fmt"
    "log"
    "time"

    abstractions "github.com/microsoft/kiota-abstractions-go"
    graph "github.com/microsoftgraph/msgraph-sdk-go"
    graphcore "github.com/microsoftgraph/msgraph-sdk-go-core"
    "github.com/microsoftgraph/msgraph-sdk-go/models"
    "github.com/microsoftgraph/msgraph-sdk-go/users"
)
```

```go
headers := abstractions.NewRequestHeaders()
headers.Add("Prefer", "outlook.body-content-type=\"text\"")

var pageSize int32 = 10
query := users.ItemMessagesRequestBuilderGetQueryParameters{
    Select: []string{"body", "sender", "subject"},
    Top:    &pageSize,
}

options := users.ItemMessagesRequestBuilderGetRequestConfiguration{
    Headers:         headers,
    QueryParameters: &query,
}

result, err := graphClient.Me().Messages().Get(context.Background(), &options)
if err != nil {
    log.Fatalf("Error getting messages: %v\n", err)
}

// Initialize iterator
pageIterator, err := graphcore.NewPageIterator[*models.Message](
    result,
    graphClient.GetAdapter(),
    models.CreateMessageCollectionResponseFromDiscriminatorValue)
if err != nil {
    log.Fatalf("Error creating page iterator: %v\n", err)
}

// Any custom headers sent in original request should also be added
// to the iterator
pageIterator.SetHeaders(headers)

// Iterate over all pages
err = pageIterator.Iterate(
    context.Background(),
    func(message *models.Message) bool {
        fmt.Printf("%s\n", *message.GetSubject())
        // Return true to continue the iteration
        return true
    })
if err != nil {
    log.Fatalf("Error iterating over messages: %v\n", err)
}
```

```java
ArrayList<Message> messages = new ArrayList<>();

MessageCollectionResponse messageResponse = graphClient.me().messages().get( requestConfiguration -> {
    requestConfiguration.headers.add("Prefer", "outlook.body-content-type=\"text\"");
    requestConfiguration.queryParameters.select = new String[] {"sender, subject, body"};
    requestConfiguration.queryParameters.top = 10;
});

PageIterator<Message, MessageCollectionResponse> pageIterator =
        new PageIterator.Builder<Message, MessageCollectionResponse>()
        .client(graphClient)
        // Response from the first request
        .collectionPage(Objects.requireNonNull(messageResponse))
        // Factory to create a new collection response
        .collectionPageFactory(MessageCollectionResponse::createFromDiscriminatorValue)
        // Used to configure subsequent requests
        .requestConfigurator( requestInfo -> {
            // Re-add the header and query parameters to subsequent requests
            requestInfo.headers.add("Prefer", "outlook.body-content-type=\"text\"");
            requestInfo.addQueryParameter("%24select", new String[] {"sender, subject, body"});
            requestInfo.addQueryParameter("%24top", 10);
            return requestInfo;
        })
        // Callback executed for each item in the collection
        .processPageItemCallback( message -> {
            messages.add(message);
            return true;
        }).build();

pageIterator.iterate();
```

```php
$query = new MessagesRequestBuilderGetQueryParameters(
    top: 10,
    select: ['sender', 'subject', 'body']);

$config = new MessagesRequestBuilderGetRequestConfiguration(
    queryParameters: $query,
    headers: ['Prefer' => 'outlook.body-content-type="text"']);

$messages = $graphClient->me()
    ->messages()
    ->get($config)
    ->wait();

// Microsoft\Graph\Core\Tasks\PageIterator
$pageIterator = new PageIterator($messages, $graphClient->getRequestAdapter());

$callback = function($message): bool {
    /** @var Models\Message $message */
    print($message->getSubject().PHP_EOL);
    // Return true to continue iteration
    return true;
};

// Re-add the header to subsequent requests
$pageIterator->setHeaders(['Prefer' => 'outlook.body-content-type="text"']);

$pageIterator->iterate($callback);
```

```typescript
const response: PageCollection = await graphClient
  .api('/me/messages?$top=10&$select=sender,subject,body')
  .header('Prefer', 'outlook.body-content-type="text"')
  .get();

// A callback function to be called for every item in the collection.
// This call back should return boolean indicating whether not to
// continue the iteration process.
const callback: PageIteratorCallback = (message: Message) => {
  console.log(message.subject);
  return true;
};

// A set of request options to be applied to
// all subsequent page requests
const requestOptions: GraphRequestOptions = {
  // Re-add the header to subsequent requests
  headers: {
    Prefer: 'outlook.body-content-type="text"',
  },
};

// Creating a new page iterator instance with client a graph client
// instance, page collection response from request and callback
const pageIterator = new PageIterator(
  graphClient,
  response,
  callback,
  requestOptions,
);

// This iterates the collection until the nextLink is drained out.
await pageIterator.iterate();
```

## Stopping and resuming the iteration

Some scenarios require stopping the iteration process in order to perform other actions. It is possible to pause the iteration by returning `false` from the iteration callback. Iteration can be resumed by calling the `resume` method on the **PageIterator**.

- [C#](#tabpanel_2_csharp)
- [Go](#tabpanel_2_go)
- [Java](#tabpanel_2_java)
- [PHP](#tabpanel_2_PHP)
- [TypeScript](#tabpanel_2_typescript)

```csharp
int count = 0;
int pauseAfter = 25;

var messages = await graphClient.Me.Messages
    .GetAsync(requestConfiguration =>
    {
        requestConfiguration.QueryParameters.Top = 10;
        requestConfiguration.QueryParameters.Select =
            ["sender", "subject"];
    });

if (messages == null)
{
    return;
}

var pageIterator = PageIterator<Message, MessageCollectionResponse>
    .CreatePageIterator(
        graphClient,
        messages,
        (msg) =>
        {
            Console.WriteLine(msg.Subject);
            count++;
            // If we've iterated over the limit,
            // stop the iteration by returning false
            return count < pauseAfter;
        });

await pageIterator.IterateAsync();

while (pageIterator.State != PagingState.Complete)
{
    Console.WriteLine("Iteration paused for 5 seconds...");
    await Task.Delay(5000);
    // Reset count
    count = 0;
    await pageIterator.ResumeAsync();
}
```

```go
import (
    "context"
    "fmt"
    "log"
    "time"

    abstractions "github.com/microsoft/kiota-abstractions-go"
    graph "github.com/microsoftgraph/msgraph-sdk-go"
    graphcore "github.com/microsoftgraph/msgraph-sdk-go-core"
    "github.com/microsoftgraph/msgraph-sdk-go/models"
    "github.com/microsoftgraph/msgraph-sdk-go/users"
)
```

```go
var pageSize int32 = 10
query := users.ItemMessagesRequestBuilderGetQueryParameters{
    Select: []string{"body", "sender", "subject"},
    Top:    &pageSize,
}

options := users.ItemMessagesRequestBuilderGetRequestConfiguration{
    QueryParameters: &query,
}

result, err := graphClient.Me().Messages().Get(context.Background(), &options)
if err != nil {
    log.Fatalf("Error getting messages: %v\n", err)
}

// Initialize iterator
pageIterator, err := graphcore.NewPageIterator[*models.Message](
    result,
    graphClient.GetAdapter(),
    models.CreateMessageCollectionResponseFromDiscriminatorValue)
if err != nil {
    log.Fatalf("Error creating page iterator: %v\n", err)
}

// Pause iterating after 25
var count, pauseAfter = 0, 25

// Iterate over all pages
err = pageIterator.Iterate(
    context.Background(),
    func(message *models.Message) bool {
        count++
        fmt.Printf("%d: %s\n", count, *message.GetSubject())
        // Once count = 25, this returns false,
        // Which pauses the iteration
        return count < pauseAfter
    })
if err != nil {
    log.Fatalf("Error iterating over messages: %v\n", err)
}

// Pause 5 seconds
fmt.Printf("Iterated first %d messages, pausing for 5 seconds...\n", pauseAfter)
time.Sleep(5 * time.Second)
fmt.Printf("Resuming iteration...\n")

// Resume iteration
err = pageIterator.Iterate(
    context.Background(),
    func(message *models.Message) bool {
        count++
        fmt.Printf("%d: %s\n", count, *message.GetSubject())
        // Return true to continue the iteration
        return true
    })
if err != nil {
    log.Fatalf("Error iterating over messages: %v\n", err)
}
```

```java
int iterations = 1;
ArrayList<Message> messages = new ArrayList<>();
int pauseAfter = iterations*25;

MessageCollectionResponse messageResponse = graphClient.me().messages().get( requestConfiguration -> {
    requestConfiguration.queryParameters.top = 10;
    requestConfiguration.queryParameters.select = new String[] {"sender, subject"};
});

PageIterator<Message, MessageCollectionResponse> pageIterator =
        new PageIterator.Builder<Message, MessageCollectionResponse>()
        .client(graphClient)
        .collectionPage(Objects.requireNonNull(messageResponse))
        .collectionPageFactory(MessageCollectionResponse::createFromDiscriminatorValue)
        .requestConfigurator( requestInfo -> {
            requestInfo.addQueryParameter("%24select", new String[] {"sender, subject"});
            requestInfo.addQueryParameter("%24top", 10);
            return requestInfo;
        })
        .processPageItemCallback( message -> {
            messages.add(message);
            // Pause paging by returning false after 25 messages
            return messages.size() < pauseAfter;
        }).build();

pageIterator.iterate();

// Resume paging
while (pageIterator.getPageIteratorState() != PageIterator.PageIteratorState.COMPLETE) {
    iterations+=1;
    pageIterator.resume();
}
```

```php
$count = 0;

$messages = $graphClient->me()
    ->messages()
    ->get()
    ->wait();

// Microsoft\Graph\Core\Tasks\PageIterator
$pageIterator = new PageIterator($messages, $graphClient->getRequestAdapter());

$callback = function($message) use (&$count): bool {
    /** @var Models\Message $message */
    $count++;
    print($count.'. '.$message->getSubject().PHP_EOL);
    // Return true to continue iteration
    // Return false once first 5 have been processed
    return $count < 5;
};

$pageIterator->iterate($callback);

print('Pausing iteration after first 5'.PHP_EOL);
sleep(5);

// Process next 5
$count = 0;
$pageIterator->iterate($callback);
```

```typescript
let count = 0;
const pauseAfter = 25;

const response: PageCollection = await graphClient
  .api('/me/messages?$top=10&$select=sender,subject,body')
  .get();

const callback: PageIteratorCallback = (message: Message) => {
  console.log(message.subject);
  count++;

  // If we've iterated over the limit,
  // stop the iteration by returning false
  return count < pauseAfter;
};

const pageIterator = new PageIterator(graphClient, response, callback);
await pageIterator.iterate();

while (!pageIterator.isComplete()) {
  console.log('Iteration paused for 5 seconds...');
  await new Promise((resolve) => setTimeout(resolve, 5000));

  // Reset count
  count = 0;
  await pageIterator.resume();
}
```

## Manually requesting subsequent pages

As an alternative to using the **PageIterator** class, you can manually check the response for an `@odata.nextLink` property and request the next page.

- [C#](#tabpanel_3_csharp)
- [Go](#tabpanel_3_go)
- [Java](#tabpanel_3_java)
- [PHP](#tabpanel_3_PHP)
- [TypeScript](#tabpanel_3_typescript)

```csharp
var messages = await graphClient.Me.Messages
    .GetAsync(requestConfiguration =>
    {
        requestConfiguration.QueryParameters.Top = 10;
    });

while (messages?.Value != null)
{
    foreach (var message in messages.Value)
    {
        Console.WriteLine(message.Subject);
    }

    // If OdataNextLink has a value, there is another page
    if (!string.IsNullOrEmpty(messages.OdataNextLink))
    {
        // Pass the OdataNextLink to the WithUrl method
        // to request the next page
        messages = await graphClient.Me.Messages
            .WithUrl(messages.OdataNextLink)
            .GetAsync();
    }
    else
    {
        // No more results, exit loop
        break;
    }
}
```

```go
import (
    "context"
    "fmt"
    "log"
    "time"

    abstractions "github.com/microsoft/kiota-abstractions-go"
    graph "github.com/microsoftgraph/msgraph-sdk-go"
    graphcore "github.com/microsoftgraph/msgraph-sdk-go-core"
    "github.com/microsoftgraph/msgraph-sdk-go/models"
    "github.com/microsoftgraph/msgraph-sdk-go/users"
)
```

```go
var pageSize int32 = 10
query := users.ItemMessagesRequestBuilderGetQueryParameters{
    Top: &pageSize,
}

options := users.ItemMessagesRequestBuilderGetRequestConfiguration{
    QueryParameters: &query,
}

result, err := graphClient.Me().Messages().Get(context.Background(), &options)
if err != nil {
    log.Fatalf("Error getting messages: %v\n", err)
}

for {
    for _, message := range result.GetValue() {
        fmt.Printf("%s\n", *message.GetSubject())
    }

    nextPageUrl := result.GetOdataNextLink()
    if nextPageUrl != nil {
        result, err = graphClient.Me().Messages().
            WithUrl(*nextPageUrl).
            Get(context.Background(), nil)
        if err != nil {
            log.Fatalf("Error getting messages: %v\n", err)
        }
    } else {
        break
    }
}
```

```java
MessageCollectionResponse messagesPage = graphClient.me().messages().get( requestConfiguration -> {
    requestConfiguration.headers.add("Prefer", "outlook.body-content-type=\"text\"");
    requestConfiguration.queryParameters.select = new String[] {"sender, subject, body"};
    requestConfiguration.queryParameters.top = 10;
});

while (messagesPage != null) {
    final List<Message> messages = messagesPage.getValue();
    for (Message message : messages) {
        System.out.println(message.getSubject());
    }

    // Get the next page
    final String odataNextLink = messagesPage.getOdataNextLink();
    if (odataNextLink == null || odataNextLink.isEmpty()) {
        break;
    } else {
        messagesPage = graphClient.me().messages().withUrl(odataNextLink).get();
    }
}
```

```php
/** @var MessageCollectionResponse $messages */
$messages = $graphClient->me()
    ->messages()
    ->get()
    ->wait();

while (null !== $messages->getValue())
{
    foreach($messages->getValue() as $message) {
        /** @var Models\Message $message */
        print($message->getSubject().PHP_EOL);
    }

    if (null !== $messages->getOdataNextLink()) {
        $messages = $graphClient->me()
            ->messages()
            ->withUrl($messages->getOdataNextLink())
            ->get()
            ->wait();
    }
    else {
        break;
    }
}
```

```typescript
let response: PageCollection = await graphClient
  .api('/me/messages?$top=10')
  .get();

while (response.value.length > 0) {
  for (const message of response.value as Message[]) {
    console.log(message.subject);
  }

  if (response['@odata.nextLink']) {
    response = await graphClient.api(response['@odata.nextLink']).get();
  } else {
    break;
  }
}
```

## Error handling

### Avoiding DirectoryPageTokenNotFoundException errors

When paging through large sets of data, you might encounter the `DirectoryPageTokenNotFoundException` error, which prevents the client app from successfully retrieving subsequent pages. This error occurs when the client app uses a token from a retry operation to request the next page of results.

To avoid this error, don't use tokens from retry operations for subsequent page requests as these tokens aren't guaranteed to be valid for future requests. Instead, persist the token from the last successful response and use it for the next page request. Therefore, the `@odata.nextLink` value used for the retry should be used for the subsequent page request.

#### Example scenario

1. Retrieve Page 1 and receive a token "Token1".
2. Use "Token1" to request Page 2.
3. If you encounter a network error, retry the request.
4. During the retry, you receive a new token "RetryToken".
5. Do not use "RetryToken" to request Page 3, as it might cause the `DirectoryPageTokenNotFoundException` error.
6. Instead, use "Token1" \(the token from the last successful non-retry response\) to request Page 3.
