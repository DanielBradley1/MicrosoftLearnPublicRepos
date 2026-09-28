<!-- Source: https://learn.microsoft.com/en-us/graph/sdks/batch-requests -->
<!-- Sitemap-Last-Modified: 2024-11-07 -->

# Use the Microsoft Graph SDKs to batch requests

[Batching](https://learn.microsoft.com/en-us/graph/json-batching) is a way of combining multiple requests into a single HTTP request. The requests are combined in a single JSON payload, which is sent via POST to the `\$batch` endpoint. Microsoft Graph SDKs have a set of classes to simplify how you create batch payloads and parse batch response payloads.

Important

For current limitations with JSON batching in Microsoft Graph, see [Known Issues](https://developer.microsoft.com/en-us/graph/known-issues/?filterBy=JSON%20batching&search=).

## Create a batch request

The Microsoft Graph SDKs provide three classes to work with batch requests and responses.

- **BatchRequestStep** - Represents a single request \(such as `GET /me`\) within a batch. It enables assigning a unique identifier to the request and specifying dependencies between requests.
- **BatchRequestContent** - Simplifies creating the batch request payload. It contains multiple **BatchRequestStep** objects.
- **BatchResponseContent** - Simplifies parsing the response from a batch request. It enables you to get all responses, get a specific response by ID, and get the `@odata.nextLink` property if present.

### Automatic batching for request limits

The Microsoft Graph SDK automatically handles batching requests with respect to the limit of 20 requests per batch. This means that if your code exceeds this limit, the SDK splits the requests into separate batches behind the scenes. This ensures that each batch complies with the limitation. You no longer need to manually implement logic to handle this batching limit, which makes your code cleaner and easier to manage.

## Simple batching example

This example shows how to send multiple requests in a batch that are not dependent on each other. The service can run the requests in any order. This example gets the user and gets the user's calendar view for the current day.

- [C#](#tabpanel_1_csharp)
- [Go](#tabpanel_1_go)
- [Java](#tabpanel_1_java)
- [PHP](#tabpanel_1_PHP)
- [TypeScript](#tabpanel_1_typescript)

```csharp
// Use the request builder to generate a regular
// request to /me
var userRequest = graphClient.Me.ToGetRequestInformation();

var today = DateTime.Now.Date;

// Use the request builder to generate a regular
// request to /me/calendarview?startDateTime="start"&endDateTime="end"
var eventsRequest = graphClient.Me.CalendarView
    .ToGetRequestInformation(requestConfiguration =>
        {
            requestConfiguration.QueryParameters.StartDateTime =
                today.ToString("yyyy-MM-ddTHH:mm:ssK");
            requestConfiguration.QueryParameters.EndDateTime =
                today.AddDays(1).ToString("yyyy-MM-ddTHH:mm:ssK");
        });

// Build the batch
var batchRequestContent = new BatchRequestContentCollection(graphClient);

// Using AddBatchRequestStepAsync adds each request as a step
// with no specified order of execution
var userRequestId = await batchRequestContent
    .AddBatchRequestStepAsync(userRequest);
var eventsRequestId = await batchRequestContent
    .AddBatchRequestStepAsync(eventsRequest);

var returnedResponse = await graphClient.Batch.PostAsync(batchRequestContent);

// De-serialize response based on known return type
try
{
    var user = await returnedResponse
        .GetResponseByIdAsync<User>(userRequestId);
    Console.WriteLine($"Hello {user.DisplayName}!");
}
catch (Exception ex)
{
    Console.WriteLine($"Get user failed: {ex.Message}");
}

// For collections, must use the *CollectionResponse class to deserialize
// The .Value property will contain the *CollectionPage type that the Graph client
// returns from GetAsync().
try
{
    var events = await returnedResponse
        .GetResponseByIdAsync<EventCollectionResponse>(eventsRequestId);
    Console.WriteLine(
        $"You have {events.Value?.Count} events on your calendar today.");
}
catch (Exception ex)
{
    Console.WriteLine($"Get calendar view failed: {ex.Message}");
}
```

```go
// Use the request builder to generate a regular
// request to /me
meRequest, err := graphClient.Me().
    ToGetRequestInformation(context.Background(), nil)
if err != nil {
    log.Fatalf("Error creating GET /me request: %v\n", err)
}

now := time.Now()
nowMidnight := time.Date(now.Year(), now.Month(), now.Day(),
    0, 0, 0, 0, time.Local)

viewStart := nowMidnight.UTC().Format(time.RFC3339)
viewEnd := nowMidnight.AddDate(0, 0, 1).UTC().Format(time.RFC3339)

query := users.ItemCalendarViewRequestBuilderGetQueryParameters{
    StartDateTime: &viewStart,
    EndDateTime:   &viewEnd,
    Select:        []string{"subject", "id"},
}

// Use the request builder to generate a request
// to /me/calendarView?startDateTime="start"&endDateTime="end"
eventsRequest, err := graphClient.Me().
    CalendarView().
    ToGetRequestInformation(context.Background(),
        &users.ItemCalendarViewRequestBuilderGetRequestConfiguration{
            QueryParameters: &query,
        })
if err != nil {
    log.Fatalf("Error creating GET /me/calendarView request: %v\n", err)
}

// Build the batch
batch := graphcore.NewBatchRequest(graphClient.GetAdapter())

// Using AddBatchRequestStep adds each request as a step
// with no specified order of execution
meRequestItem, err := batch.AddBatchRequestStep(*meRequest)
if err != nil {
    log.Fatalf("Error adding GET /me request to batch: %v\n", err)
}
eventsRequestItem, err := batch.AddBatchRequestStep(*eventsRequest)
if err != nil {
    log.Fatalf("Error adding GET /me/calendarView request to batch: %v\n", err)
}

batchResponse, err := batch.Send(context.Background(), graphClient.GetAdapter())
if err != nil {
    log.Fatalf("Error sending batch: %v\n", err)
}

// De-serialize response based on known return type
user, err := graphcore.GetBatchResponseById[models.Userable](
    batchResponse, *meRequestItem.GetId(), models.CreateUserFromDiscriminatorValue)
if err != nil {
    log.Fatalf("Error reading GET /me response: %v\n", err)
}
fmt.Printf("Hello %s\n", *(user.GetDisplayName()))

// For collections, must use the *CollectionResponseable class to deserialize
events, err := graphcore.GetBatchResponseById[models.EventCollectionResponseable](
    batchResponse, *eventsRequestItem.GetId(),
    models.CreateEventCollectionResponseFromDiscriminatorValue)
if err != nil {
    log.Fatalf("Error reading GET /me/calendarView response: %v\n", err)
}
fmt.Printf("You have %d events on your calendar today\n", len(events.GetValue()))
```

```java
// Create the batch request content with the steps
final BatchRequestContent batchRequestContent = new BatchRequestContent(
    graphClient);

// Use the Graph client to generate the requestInformation object for GET /me
final RequestInformation meRequestInformation = graphClient.me()
    .toGetRequestInformation();

final ZoneOffset localTimeZone = OffsetDateTime.now().getOffset();
final OffsetDateTime today = OffsetDateTime.of(LocalDate.now(),
    LocalTime.MIDNIGHT, localTimeZone);
final OffsetDateTime tomorrow = today.plusDays(1);

// Use the Graph client to generate the requestInformation for
// GET /me/calendarView?startDateTime="start"&endDateTime="end"
RequestInformation calenderViewRequestInformation = graphClient.me()
    .calendarView().toGetRequestInformation(requestConfiguration -> {
        requestConfiguration.queryParameters.startDateTime = today.toString();
        requestConfiguration.queryParameters.endDateTime = tomorrow.toString();
    });

// Add the requestInformation objects to the batch request content
final String meRequestId = batchRequestContent
    .addBatchRequestStep(meRequestInformation);
final String calendarViewRequestStepId = batchRequestContent
    .addBatchRequestStep(calenderViewRequestInformation);

// Send the batch request content to the /$batch endpoint
final BatchResponseContent batchResponseContent = Objects.requireNonNull(
    graphClient.getBatchRequestBuilder().post(batchRequestContent, null));

// Get the user response using the id assigned to the request
final User me = batchResponseContent.getResponseById(meRequestId,
    User::createFromDiscriminatorValue);
System.out.println(String.format("Hello %s!", me.getDisplayName()));

// Get the calendar view response by id
final EventCollectionResponse eventsResponse = Objects.requireNonNull(
    batchResponseContent.getResponseById(calendarViewRequestStepId,
        EventCollectionResponse::createFromDiscriminatorValue));
System.out.println(String.format("You have %d events on your calendar today",
    Objects.requireNonNull(eventsResponse.getValue()).size()));
```

```php
// Use the request builder to generate a GET
// request to /me
$userRequest = $graphClient->me()->toGetRequestInformation();

$timeZone = new \DateTimeZone('America/New_York');
$today = new \DateTimeImmutable('today midnight', $timeZone);
$tomorrow = new \DateTimeImmutable('tomorrow midnight', $timeZone);

// Use the request builder to generate a GET
// request to /me/calendarView?startDateTime="start"&endDateTime="end"
$query = new CalendarViewRequestBuilderGetQueryParameters(
    startDateTime: $today->format(\DateTime::ATOM),
    endDateTime: $tomorrow->format(\DateTime::ATOM));
$config = new CalendarViewRequestBuilderGetRequestConfiguration(queryParameters: $query);
$eventsRequest = $graphClient->me()->calendarView()->toGetRequestInformation($config);

// Build the batch
$userRequestItem = new BatchRequestItem($userRequest);
$eventsRequestItem = new BatchRequestItem($eventsRequest);
$batchRequestContent = new BatchRequestContent([$userRequestItem, $eventsRequestItem]);

// Create a batch request builder to send the batched requests
$batchRequestBuilder = new BatchRequestBuilder($graphClient->getRequestAdapter());
/** @var BatchResponseContent $batchResponse */
$batchResponse = $batchRequestBuilder->postAsync($batchRequestContent)->wait();

// De-serialize the responses
$user = $batchResponse->getResponseBody($userRequestItem->getId(), Models\User::class);
print('Hello '.$user->getDisplayName().'!'.PHP_EOL);

// For collections, must use the *CollectionResponse class to deserialize
// getValue will return an array of items
$events = $batchResponse->getResponseBody($eventsRequestItem->getId(), Models\EventCollectionResponse::class);
print('You have '.count($events->getValue()).' events on your calendar today'.PHP_EOL);
```

```typescript
// Create a batch request step to GET /me
// Request is from fetch polyfill, i.e. node-fetch
const userRequestStep: BatchRequestStep = {
  id: '1',
  request: new Request('https://graph.microsoft.com/me', {
    method: 'GET',
  }),
};

// startOfToday and endOfToday from date-fns
const start = startOfToday().toISOString();
const end = endOfToday().toISOString();

// Create a batch request step to GET
// /me/calendarView?startDateTime="start"&endDateTime="end"
const calendarViewRequestStep: BatchRequestStep = {
  id: '2',
  request: new Request(
    `https://graph.microsoft.com/me/calendarView?startDateTime=${start}&endDateTime=${end}`,
    {
      method: 'GET',
    },
  ),
};

// Create the batch request content with the steps created
// above
const batchRequestContent = new BatchRequestContent([
  userRequestStep,
  calendarViewRequestStep,
]);

const content = await batchRequestContent.getContent();

// POST the batch request content to the /$batch endpoint
const batchResponse = await graphClient.api('/$batch').post(content);

// Create a BatchResponseContent object to parse the response
const batchResponseContent = new BatchResponseContent(batchResponse);

// Get the user response using the id assigned to the request
const userResponse = batchResponseContent.getResponseById('1');

// For a single entity, the JSON payload can be deserialized
// into the expected type
// Types supplied by @microsoft/microsoft-graph-types
if (userResponse.ok) {
  const user: User = (await userResponse.json()) as User;
  console.log(`Hello ${user.displayName}!`);
} else {
  console.log(`Get user failed with status ${userResponse.status}`);
}

// Get the calendar view response by id
const calendarResponse = batchResponseContent.getResponseById('2');

// For a collection of entities, the "value" property of
// the JSON payload can be deserialized into an array of
// the expected type
if (calendarResponse.ok) {
  const rawResponse = (await calendarResponse.json()) as PageCollection;
  const events: Event[] = rawResponse.value;
  console.log(`You have ${events.length} events on your calendar today.`);
} else {
  console.log(
    `Get calendar view failed with status ${calendarResponse.status}`,
  );
}
```

## Batches with dependent requests

This example shows how to send multiple requests in a batch that are dependent on each other. The service runs the request in the order specified by the dependencies. This example adds an event with a start time during the current day to the user's calendar and gets the user's calendar view for the current day. To make sure that the calendar review returned includes the new event created, the request for the calendar view is configured as dependent on the request to add the new event. This ensures that the add event request runs first.

Note

If the add event request fails, the get calendar view request fails with a `424 Failed Dependency` error.

- [C#](#tabpanel_2_csharp)
- [Go](#tabpanel_2_go)
- [Java](#tabpanel_2_java)
- [PHP](#tabpanel_2_PHP)
- [TypeScript](#tabpanel_2_typescript)

```csharp
var today = DateTime.Now.Date;

var newEvent = new Event
{
    Subject = "File end-of-day report",
    Start = new DateTimeTimeZone
    {
        // 5:00 PM
        DateTime = today.AddHours(17)
            .ToString("yyyy-MM-ddTHH:mm:ss"),
        TimeZone = TimeZoneInfo.Local.StandardName,
    },
    End = new DateTimeTimeZone
    {
        // 5:30 PM
        DateTime = today.AddHours(17).AddMinutes(30)
            .ToString("yyyy-MM-ddTHH:mm:ss"),
        TimeZone = TimeZoneInfo.Local.StandardName,
    },
};

// Use the request builder to generate a regular
// POST request to /me/events
var addEventRequest = graphClient.Me.Events
    .ToPostRequestInformation(newEvent);

// Use the request builder to generate a regular
// request to /me/calendarview?startDateTime="start"&endDateTime="end"
var calendarViewRequest = graphClient.Me.CalendarView.ToGetRequestInformation(
    requestConfiguration =>
    {
        requestConfiguration.QueryParameters.StartDateTime =
            today.ToString("yyyy-MM-ddTHH:mm:ssK");
        requestConfiguration.QueryParameters.EndDateTime =
            today.AddDays(1).ToString("yyyy-MM-ddTHH:mm:ssK");
    });

// Build the batch
var batchRequestContent = new BatchRequestContentCollection(graphClient);

// Force the requests to execute in order, so that the request for
// today's events will include the new event created.

// First request, no dependency
var addEventRequestId = await batchRequestContent
    .AddBatchRequestStepAsync(addEventRequest);

// Second request, depends on addEventRequestId
var eventsRequestId = Guid.NewGuid().ToString();
var eventsRequestMessage = await graphClient.RequestAdapter
    .ConvertToNativeRequestAsync<HttpRequestMessage>(calendarViewRequest);
batchRequestContent.AddBatchRequestStep(new BatchRequestStep(
    eventsRequestId,
    eventsRequestMessage,
    [addEventRequestId]));

var returnedResponse = await graphClient.Batch.PostAsync(batchRequestContent);

// De-serialize response based on known return type
try
{
    var createdEvent = await returnedResponse
        .GetResponseByIdAsync<Event>(addEventRequestId);
    Console.WriteLine($"New event created with ID: {createdEvent.Id}");
}
catch (Exception ex)
{
    Console.WriteLine($"Add event failed: {ex.Message}");
}

// For collections, must use the *CollectionResponse class to deserialize
// The .Value property will contain the *CollectionPage type that the Graph client
// returns from GetAsync().
try
{
    var events = await returnedResponse
        .GetResponseByIdAsync<EventCollectionResponse>(eventsRequestId);
    Console.WriteLine(
        $"You have {events.Value?.Count} events on your calendar today.");
}
catch (Exception ex)
{
    Console.WriteLine($"Get calendar view failed: {ex.Message}");
}
```

```go
now := time.Now()
nowMidnight := time.Date(now.Year(), now.Month(), now.Day(),
    0, 0, 0, 0, time.Local)
timeZone, _ := tzlocal.RuntimeTZ()

// 5:00 PM
startDateTime := nowMidnight.Add(time.Hour * 17)
// 5:30 PM
endDateTime := startDateTime.Add(time.Minute * 30)
graphDateTimeFormat := "2006-01-02T15:04:05"

// Create event
newEvent := models.NewEvent()
subject := "File end-of-day report"
newEvent.SetSubject(&subject)

start := models.NewDateTimeTimeZone()
startString := startDateTime.Format(graphDateTimeFormat)
start.SetDateTime(&startString)
start.SetTimeZone(&timeZone)
newEvent.SetStart(start)

end := models.NewDateTimeTimeZone()
endString := endDateTime.Format(graphDateTimeFormat)
end.SetDateTime(&endString)
end.SetTimeZone(&timeZone)
newEvent.SetEnd(end)

addEventRequest, err := graphClient.Me().
    Events().
    ToPostRequestInformation(context.Background(), newEvent, nil)
if err != nil {
    log.Fatalf("Error creating POST /me/events request: %v\n", err)
}

viewStart := nowMidnight.UTC().Format(time.RFC3339)
viewEnd := nowMidnight.AddDate(0, 0, 1).UTC().Format(time.RFC3339)

query := users.ItemCalendarViewRequestBuilderGetQueryParameters{
    StartDateTime: &viewStart,
    EndDateTime:   &viewEnd,
    Select:        []string{"subject", "id"},
}

// Use the request builder to generate a request
// to /me/calendarView?startDateTime="start"&endDateTime="end"
eventsRequest, err := graphClient.Me().
    CalendarView().
    ToGetRequestInformation(context.Background(),
        &users.ItemCalendarViewRequestBuilderGetRequestConfiguration{
            QueryParameters: &query,
        })
if err != nil {
    log.Fatalf("Error creating GET /me/calendarView request: %v\n", err)
}

// Build the batch
batch := graphcore.NewBatchRequest(graphClient.GetAdapter())

// Force the requests to execute in order, so that the request for
// today's events will include the new event created.

// First request, no dependency
addEventRequestItem, err := batch.AddBatchRequestStep(*addEventRequest)
if err != nil {
    log.Fatalf("Error adding POST /me/events request to batch: %v\n", err)
}

// Second request, depends on addEventRequestId
eventsRequestItem, err := batch.AddBatchRequestStep(*eventsRequest)
if err != nil {
    log.Fatalf("Error creating GET /me/calendarView request to batch: %v\n", err)
}
eventsRequestItem.DependsOnItem(addEventRequestItem)

batchResponse, err := batch.Send(context.Background(), graphClient.GetAdapter())
if err != nil {
    log.Fatalf("Error sending batch: %v\n", err)
}

// De-serialize response based on known return type
event, err := graphcore.GetBatchResponseById[models.Eventable](
    batchResponse, *addEventRequestItem.GetId(),
    models.CreateEventFromDiscriminatorValue)
if err != nil {
    log.Fatalf("Error reading POST /me/events response: %v\n", err)
}
fmt.Printf("New event created with ID: %s\n", *(event.GetId()))

// For collections, must use the *CollectionResponseable class to deserialize
events, err := graphcore.GetBatchResponseById[models.EventCollectionResponseable](
    batchResponse, *eventsRequestItem.GetId(),
    models.CreateEventCollectionResponseFromDiscriminatorValue)
if err != nil {
    log.Fatalf("Error reading GET /me/calendarView response: %v\n", err)
}
fmt.Printf("You have %d events on your calendar today\n", len(events.GetValue()))
```

```java
// Create the batch request content with the steps
final BatchRequestContent batchRequestContent = new BatchRequestContent(
    graphClient);

final ZoneOffset localTimeZone = OffsetDateTime.now().getOffset();
final OffsetDateTime today = OffsetDateTime.of(LocalDate.now(),
    LocalTime.MIDNIGHT, localTimeZone);
final OffsetDateTime tomorrow = today.plusDays(1);

// Create a new event for today at 5:00 PM
final Event newEvent = new Event();
newEvent.setSubject("File end-of-day report");
// 5:00 PM
final DateTimeTimeZone start = new DateTimeTimeZone();
start.setDateTime(
    today.plusHours(17).format(DateTimeFormatter.ISO_LOCAL_DATE_TIME));
start.setTimeZone(ZoneOffset.systemDefault().getId());
newEvent.setStart(start);
// 5:30 PM
final DateTimeTimeZone end = new DateTimeTimeZone();
end.setDateTime(today.plusHours(17).plusMinutes(30)
    .format(DateTimeFormatter.ISO_LOCAL_DATE_TIME));
end.setTimeZone(ZoneOffset.systemDefault().getId());
newEvent.setEnd(end);

// Use the Graph client to add the requestInformation for POST /me/events
RequestInformation postEventRequestInformation = graphClient.me().events()
    .toPostRequestInformation(newEvent);

// Get the id assigned to the request
String postEventRequestId = batchRequestContent
    .addBatchRequestStep(postEventRequestInformation);

// Use the Graph client to generate the requestInformation
// GET /me/calendarView?startDateTime="start"&endDateTime="end"
final RequestInformation calendarViewRequestInformation = graphClient.me()
    .calendarView().toGetRequestInformation(requestConfiguration -> {
        requestConfiguration.queryParameters.startDateTime = today.toString();
        requestConfiguration.queryParameters.endDateTime = tomorrow.toString();
    });

final String calendarViewRequestId = batchRequestContent
    .addBatchRequestStep(calendarViewRequestInformation);
// Set the dependsOnId to 'postEventRequestId'
batchRequestContent.getBatchRequestSteps().get(calendarViewRequestId)
    .addDependsOnId(postEventRequestId);

// Send the batch request content to the /$batch endpoint
final BatchResponseContent batchResponseContent = Objects.requireNonNull(
    graphClient.getBatchRequestBuilder().post(batchRequestContent, null));

// Get the event response using the id assigned to the request
final Event postedEvent = batchResponseContent.getResponseById(postEventRequestId,
    Event::createFromDiscriminatorValue);
System.out.println(String.format("New event created with ID: %s",
    Objects.requireNonNull(postedEvent.getId())));

// Get the calendar view response by id
final EventCollectionResponse eventsResponse = Objects
    .requireNonNull(batchResponseContent.getResponseById(calendarViewRequestId,
        EventCollectionResponse::createFromDiscriminatorValue));
System.out.println(String.format("You have %d events on your calendar today",
    Objects.requireNonNull(eventsResponse.getValue().size())));
```

```php
$startTime = new \DateTimeImmutable('today 5PM');
$endTime = $startTime->add(new \DateInterval('PT30M'));

$newEvent = new Models\Event();
$newEvent->setSubject('File end-of-day report');
$start = new Models\DateTimeTimeZone();
$start->setDateTime($startTime->format('Y-m-d\TH:i:s'));
$start->setTimeZone('Eastern Standard Time');
$newEvent->setStart($start);
$end = new Models\DateTimeTimeZone();
$end->setDateTime($endTime->format('Y-m-d\TH:i:s'));
$end->setTimeZone('Eastern Standard Time');
$newEvent->setEnd($end);

// Use the request builder to generate a
// POST request to /me/events
$addEventRequest = $graphClient->me()->events()->toPostRequestInformation($newEvent);

$timeZone = new \DateTimeZone('America/New_York');
$today = new \DateTimeImmutable('today midnight', $timeZone);
$tomorrow = new \DateTimeImmutable('tomorrow midnight', $timeZone);

// Use the request builder to generate a GET
// request to /me/calendarView?startDateTime="start"&endDateTime="end"
$query = new CalendarViewRequestBuilderGetQueryParameters(
    startDateTime: $today->format(\DateTime::ATOM),
    endDateTime: $tomorrow->format(\DateTime::ATOM));
$config = new CalendarViewRequestBuilderGetRequestConfiguration(queryParameters: $query);
$eventsRequest = $graphClient->me()->calendarView()->toGetRequestInformation($config);

// Build the batch
// Force the requests to execute in order, so that the request for
// today's events will include the new event created.

// First request, no dependency
$addEventRequestItem = new BatchRequestItem($addEventRequest);

// Second request, depends on addEventRequestItem
$eventsRequestItem = new BatchRequestItem($eventsRequest, dependsOn: [$addEventRequestItem]);
$batchRequestContent = new BatchRequestContent([$addEventRequestItem, $eventsRequestItem]);

// Create a batch request builder to send the batched requests
$batchRequestBuilder = new BatchRequestBuilder($graphClient->getRequestAdapter());
/** @var BatchResponseContent $batchResponse */
$batchResponse = $batchRequestBuilder->postAsync($batchRequestContent)->wait();

// De-serialize the responses
$createdEvent = $batchResponse->getResponseBody($addEventRequestItem->getId(), Models\Event::class);
print('New event created with ID: '.$createdEvent->getId().PHP_EOL);

// For collections, must use the *CollectionResponse class to deserialize
// getValue will return an array of items
$events = $batchResponse->getResponseBody($eventsRequestItem->getId(), Models\EventCollectionResponse::class);
print('You have '.count($events->getValue()).' events on your calendar today'.PHP_EOL);
```

```typescript
// 5:00 PM today
// startOfToday, endOfToday, setHours, setMinutes, format from date-fns
const eventStart = setHours(startOfToday(), 17);
const eventEnd = setMinutes(eventStart, 30);

// Create a batch request step to add an event
const newEvent: Event = {
  subject: 'File end-of-day report',
  start: {
    dateTime: format(eventStart, `yyyy-MM-dd'T'HH:mm:ss`),
    timeZone: 'Pacific Standard Time',
  },
  end: {
    // 5:30 PM
    dateTime: format(eventEnd, `yyyy-MM-dd'T'HH:mm:ss`),
    timeZone: 'Pacific Standard Time',
  },
};

// Request is from fetch polyfill, i.e. node-fetch
const addEventRequestStep: BatchRequestStep = {
  id: '1',
  request: new Request('https://graph.microsoft.com/me/events', {
    method: 'POST',
    body: JSON.stringify(newEvent),
    headers: {
      'Content-Type': 'application/json',
    },
  }),
};

const start = startOfToday().toISOString();
const end = endOfToday().toISOString();

// Create a batch request step to GET
// /me/calendarView?startDateTime="start"&endDateTime="end"
const calendarViewRequestStep: BatchRequestStep = {
  id: '2',
  // This step will happen after step 1
  dependsOn: ['1'],
  request: new Request(
    `https://graph.microsoft.com/me/calendarView?startDateTime=${start}&endDateTime=${end}`,
    {
      method: 'GET',
    },
  ),
};

// Create the batch request content with the steps created
// above
const batchRequestContent = new BatchRequestContent([
  addEventRequestStep,
  calendarViewRequestStep,
]);

const content = await batchRequestContent.getContent();

// POST the batch request content to the /$batch endpoint
const batchResponse = await graphClient.api('/$batch').post(content);

// Create a BatchResponseContent object to parse the response
const batchResponseContent = new BatchResponseContent(batchResponse);

// Get the create event response by id
const newEventResponse = batchResponseContent.getResponseById('1');
if (newEventResponse.ok) {
  const event: Event = (await newEventResponse.json()) as Event;
  console.log(`New event created with ID: ${event.id}`);
} else {
  console.log(`Create event failed with status ${newEventResponse.status}`);
}

// Get the calendar view response by id
const calendarResponse = batchResponseContent.getResponseById('2');

if (calendarResponse.ok) {
  // For a collection of entities, the "value" property of
  // the JSON payload can be deserialized into an array of
  // the expected type
  const rawResponse = (await calendarResponse.json()) as PageCollection;
  const events: Event[] = rawResponse.value;
  console.log(`You have ${events.length} events on your calendar today.`);
} else {
  console.log(
    `Get calendar view failed with status ${calendarResponse.status}`,
  );
}
```
