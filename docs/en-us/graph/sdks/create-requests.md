<!-- Source: https://learn.microsoft.com/en-us/graph/sdks/create-requests -->
<!-- Sitemap-Last-Modified: 2024-11-07 -->

# Make API calls using the Microsoft Graph SDKs

The Microsoft Graph SDK service libraries provide a client class to use as the starting point for creating all API requests. There are two styles of client class: one uses a fluent interface to create the request \(for example, `client.Users["user-id"].Manager`\) and the other accepts a path string \(for example, `api("/users/user-id/manager")`\). When you have a request object, you can specify various options, such as filtering and sorting, and finally, you select the type of operation you want to perform.

There's also the [Microsoft Graph PowerShell SDK](https://learn.microsoft.com/en-us/powershell/microsoftgraph/get-started), which has no client class. Instead, all requests are represented as PowerShell commands. For example, to get a user's manager, the command is `Get-MgUserManager`. For more information on finding commands for API calls, see [Navigating the Microsoft Graph PowerShell SDK](https://learn.microsoft.com/en-us/powershell/microsoftgraph/navigating).

## Read information from Microsoft Graph

To read information from Microsoft Graph, you first need to create a request object and then run the `GET` method on the request.

- [C#](#tabpanel_1_csharp)
- [Go](#tabpanel_1_go)
- [Java](#tabpanel_1_java)
- [PHP](#tabpanel_1_PHP)
- [PowerShell](#tabpanel_1_powershell)
- [Python](#tabpanel_1_python)
- [TypeScript](#tabpanel_1_typescript)

```csharp
// GET https://graph.microsoft.com/v1.0/me
var user = await graphClient.Me
    .GetAsync();
```

```go
// GET https://graph.microsoft.com/v1.0/me
result, _ := graphClient.Me().Get(context.Background(), nil)
```

```java
// GET https://graph.microsoft.com/v1.0/me
final User user = graphClient.me().get();
```

```php
// GET https://graph.microsoft.com/v1.0/me
/** @var Models\User $user */
$user = $graphClient->me()
    ->get()
    ->wait();
```

```PowerShell
# GET https://graph.microsoft.com/v1.0/users/{user-id}

$userId = "71766077-aacc-470a-be5e-ba47db3b2e88"

$user = Get-MgUser -UserId $userId
```

```python
# GET https://graph.microsoft.com/v1.0/me
user = await graph_client.me.get()
```

```typescript
// GET https://graph.microsoft.com/v1.0/me
const user = await graphClient.api('/me').get();
```

## Use $select to control the properties returned

When retrieving an entity, not all properties are automatically retrieved; sometimes, they need to be explicitly selected. Also, returning the default set of properties isn't necessary in some scenarios. Selecting just the required properties can improve the performance of the request. You can customize the request to include the `$select` query parameter with a list of properties.

- [C#](#tabpanel_2_csharp)
- [Go](#tabpanel_2_go)
- [Java](#tabpanel_2_java)
- [PHP](#tabpanel_2_PHP)
- [PowerShell](#tabpanel_2_powershell)
- [Python](#tabpanel_2_python)
- [TypeScript](#tabpanel_2_typescript)

```csharp
// GET https://graph.microsoft.com/v1.0/me?$select=displayName,jobTitle
var user = await graphClient.Me
    .GetAsync(requestConfiguration =>
    {
        requestConfiguration.QueryParameters.Select =
            ["displayName", "jobTitle"];
    });
```

```go
// GET https://graph.microsoft.com/v1.0/me?$select=displayName,jobTitle

// import github.com/microsoftgraph/msgraph-sdk-go/users
query := users.UserItemRequestBuilderGetQueryParameters{
    Select: []string{"displayName", "jobTitle"},
}

options := users.UserItemRequestBuilderGetRequestConfiguration{
    QueryParameters: &query,
}

result, _ := graphClient.Me().Get(context.Background(), &options)
```

```java
// GET https://graph.microsoft.com/v1.0/me?$select=displayName,jobTitle
final User user = graphClient.me().get( requestConfiguration -> {
    requestConfiguration.queryParameters.select = new String[] {"displayName", "jobTitle"};
});
```

```php
// GET https://graph.microsoft.com/v1.0/me?$select=displayName,jobTitle
// Microsoft\Graph\Generated\Users\Item\UserItemRequestBuilderGetQueryParameters
$query = new UserItemRequestBuilderGetQueryParameters(
    select: ['displayName', 'jobTitle']);

// Microsoft\Graph\Generated\Users\Item\UserItemRequestBuilderGetRequestConfiguration
$config = new UserItemRequestBuilderGetRequestConfiguration(
    queryParameters: $query);

/** @var Models\User $user */
$user = $graphClient->me()
    ->get($config)
    ->wait();
```

```PowerShell
# GET https://graph.microsoft.com/v1.0/users/{user-id}?$select=displayName,jobTitle

$userId = "71766077-aacc-470a-be5e-ba47db3b2e88"

# The -Property parameter causes a $select parameter to be included in the request
$user = Get-MgUser -UserId $userId -Property DisplayName,JobTitle
```

```python
# GET https://graph.microsoft.com/v1.0/me?$select=displayName,jobTitle

# msgraph.generated.users.item.user_item_request_builder
query_params = UserItemRequestBuilder.UserItemRequestBuilderGetQueryParameters(
    select=['displayName', 'jobTitle']
)

config = RequestConfiguration(
    query_parameters=query_params
)

user = await graph_client.me.get(config)
```

```typescript
// GET https://graph.microsoft.com/v1.0/me?$select=displayName,jobTitle
const user = await graphClient
  .api('/me')
  .select(['displayName', 'jobTitle'])
  .get();
```

## Retrieve a list of entities

Retrieving a list of entities is similar to retrieving a single entity, except other options exist for configuring the request. The `$filter` query parameter can reduce the result set to only those rows that match the provided condition. The `$orderby` query parameter requests that the server provide the list of entities sorted by the specified properties.

Note

Some requests for Microsoft Entra resources require the use of advanced query capabilities. If you get a response indicating a bad request, unsupported query, or a response that includes unexpected results, including the `$count` query parameter and `ConsistencyLevel` header may allow the request to succeed. For details and examples, see [Advanced query capabilities on directory objects](https://learn.microsoft.com/en-us/graph/aad-advanced-queries).

- [C#](#tabpanel_3_csharp)
- [Go](#tabpanel_3_go)
- [Java](#tabpanel_3_java)
- [PHP](#tabpanel_3_PHP)
- [PowerShell](#tabpanel_3_powershell)
- [Python](#tabpanel_3_python)
- [TypeScript](#tabpanel_3_typescript)

```csharp
// GET https://graph.microsoft.com/v1.0/me/messages?
// $select=subject,sender&$filter=subject eq 'Hello world'
var messages = await graphClient.Me.Messages
    .GetAsync(requestConfig =>
    {
        requestConfig.QueryParameters.Select =
            ["subject", "sender"];
        requestConfig.QueryParameters.Filter =
            "subject eq 'Hello world'";
    });
```

```go
// GET https://graph.microsoft.com/v1.0/me/messages?
// $select=subject,sender&$filter=subject eq 'Hello world'

// import github.com/microsoftgraph/msgraph-sdk-go/users
filterValue := "subject eq 'Hello world'"
query := users.ItemMessagesRequestBuilderGetQueryParameters{
    Select: []string{"subject", "sender"},
    Filter: &filterValue,
}

options := users.ItemMessagesRequestBuilderGetRequestConfiguration{
    QueryParameters: &query,
}

result, _ := graphClient.Me().Messages().
    Get(context.Background(), &options)
```

```java
// GET https://graph.microsoft.com/v1.0/me/messages?
// $select=subject,sender&$filter=subject eq 'Hello world'
final MessageCollectionResponse messages = graphClient.me().messages().get( requestConfiguration -> {
    requestConfiguration.queryParameters.select = new String[] {"subject", "sender"};
    requestConfiguration.queryParameters.filter = "subject eq 'Hello world'";
});
```

```php
// GET https://graph.microsoft.com/v1.0/me/messages?
// $select=subject,sender&$filter=subject eq 'Hello world'
// Microsoft\Graph\Generated\Users\Item\Messages\MessagesRequestBuilderGetQueryParameters
$query = new MessagesRequestBuilderGetQueryParameters(
    select: ['subject', 'sender'],
    filter: 'subject eq \'Hello world\''
);

// Microsoft\Graph\Generated\Users\Item\Messages\MessagesRequestBuilderGetRequestConfiguration
$config = new MessagesRequestBuilderGetRequestConfiguration(
    queryParameters: $query);

/** @var Models\MessageCollectionResponse $messages */
$messages = $graphClient->me()
    ->messages()
    ->get($config)
    ->wait();
```

```PowerShell
# GET https://graph.microsoft.com/v1.0/users/{user-id}/messages?$select=subject,sender&
# $filter=<some condition>&orderBy=receivedDateTime

$userId = "71766077-aacc-470a-be5e-ba47db3b2e88"

# -Sort is equivalent to $orderby
# -Filter is equivalent to $filter
$messages = Get-MgUserMessage -UserId $userId -Property Subject,Sender `
-Sort ReceivedDateTime -Filter "some condition"
```

```python
# GET https://graph.microsoft.com/v1.0/me/messages?
# $select=subject,sender&$filter=subject eq 'Hello world'

# msgraph.generated.users.item.messages.messages_request_builder
query_params = MessagesRequestBuilder.MessagesRequestBuilderGetQueryParameters(
    select=['subject', 'sender'],
    filter='subject eq \'Hello world\''
)

config = RequestConfiguration(
    query_parameters=query_params
)

messages = await graph_client.me.messages.get(config)
```

```typescript
// GET https://graph.microsoft.com/v1.0/me/messages?
// $select=subject,sender&$filter=subject eq 'Hello world'
const messages = await graphClient
  .api('/me/messages')
  .select(['subject', 'sender'])
  .filter(`subject eq 'Hello world'`)
  .get();
```

The object returned when retrieving a list of entities will likely be a paged collection. For details about how to get the complete list of entities, see [paging through a collection](https://learn.microsoft.com/en-us/graph/paging).

## Access an item of a collection

For SDKs that support a fluent style, collections of entities can be accessed using an array index. For template-based SDKs, it's sufficient to embed the item identifier in the path segment following the collection. For PowerShell, identifiers are passed as parameters.

- [C#](#tabpanel_4_csharp)
- [Go](#tabpanel_4_go)
- [Java](#tabpanel_4_java)
- [PHP](#tabpanel_4_PHP)
- [PowerShell](#tabpanel_4_powershell)
- [Python](#tabpanel_4_python)
- [TypeScript](#tabpanel_4_typescript)

```csharp
// GET https://graph.microsoft.com/v1.0/me/messages/{message-id}
// messageId is a string containing the id property of the message
var message = await graphClient.Me.Messages[messageId]
    .GetAsync();
```

```go
// GET https://graph.microsoft.com/v1.0/me/messages/{message-id}
// messageId is a string containing the id property of the message
result, _ := graphClient.Me().Messages().
    ByMessageId(messageId).Get(context.Background(), nil)
```

```java
// GET https://graph.microsoft.com/v1.0/me/messages/{message-id}
// messageId is a string containing the id property of the message
final Message message = graphClient.me().messages().byMessageId(messageId).get();
```

```php
// GET https://graph.microsoft.com/v1.0/me/messages/{message-id}
// messageId is a string containing the id property of the message
/** @var Models\Message $message */
$message = $graphClient->me()
    ->messages()
    ->byMessageId($messageId)
    ->get()
    ->wait();
```

```PowerShell
# GET https://graph.microsoft.com/v1.0/users/{user-id}/messages/{message-id}

$userId = "71766077-aacc-470a-be5e-ba47db3b2e88"
$messageId = "AQMkAGUy.."

$message = Get-MgUserMessage -UserId $userId -MessageId $messageId
```

```python
# GET https://graph.microsoft.com/v1.0/me/messages/{message-id}
# message_id is a string containing the id property of the message
message = await graph_client.me.messages.by_message_id(message_id).get()
```

```typescript
// GET https://graph.microsoft.com/v1.0/me/messages/{message-id}
// messageId is a string containing the id property of the message
const message = await graphClient.api(`/me/messages/${messageId}`).get();
```

## Use $expand to access related entities

You can use the `$expand` filter to request a related entity or collection of entities at the same time that you request the main entity.

- [C#](#tabpanel_5_csharp)
- [Go](#tabpanel_5_go)
- [Java](#tabpanel_5_java)
- [PHP](#tabpanel_5_PHP)
- [PowerShell](#tabpanel_5_powershell)
- [Python](#tabpanel_5_python)
- [TypeScript](#tabpanel_5_typescript)

```csharp
// GET https://graph.microsoft.com/v1.0/me/messages/{message-id}?$expand=attachments
// messageId is a string containing the id property of the message
var message = await graphClient.Me.Messages[messageId]
    .GetAsync(requestConfig =>
        requestConfig.QueryParameters.Expand =
            ["attachments"]);
```

```go
// GET https://graph.microsoft.com/v1.0/me/messages/{message-id}?$expand=attachments

// import github.com/microsoftgraph/msgraph-sdk-go/users
expand := users.ItemMessagesMessageItemRequestBuilderGetQueryParameters{
    Expand: []string{"attachments"},
}

options := users.ItemMessagesMessageItemRequestBuilderGetRequestConfiguration{
    QueryParameters: &expand,
}
// messageId is a string containing the id property of the message
result, _ := graphClient.Me().Messages().
    ByMessageId(messageId).Get(context.Background(), &options)
```

```java
// GET
// https://graph.microsoft.com/v1.0/me/messages/{message-id}?$expand=attachments
// messageId is a string containing the id property of the message
final Message message = graphClient.me().messages().byMessageId(messageId).get( requestConfiguration -> {
    requestConfiguration.queryParameters.expand = new String[] {"attachments"};
});
```

```php
// GET https://graph.microsoft.com/v1.0/me/messages/{message-id}?$expand=attachments
// messageId is a string containing the id property of the message
// Microsoft\Graph\Generated\Users\Item\Messages\Item\MessageItemRequestBuilderGetQueryParameters
$query = new MessageItemRequestBuilderGetQueryParameters(
    expand: ['attachments']
);

// Microsoft\Graph\Generated\Users\Item\Messages\Item\MessageItemRequestBuilderGetRequestConfiguration
$config = new MessageItemRequestBuilderGetRequestConfiguration(
    queryParameters: $query);

/** @var Models\Message $message */
$message = $graphClient->me()
    ->messages()
    ->byMessageId($messageId)
    ->get($config)
    ->wait();
```

```PowerShell
# GET https://graph.microsoft.com/v1.0/users/{user-id}/messages?$expand=attachments

$userId = "71766077-aacc-470a-be5e-ba47db3b2e88"
$messageId = "AQMkAGUy.."

# -ExpandProperty is equivalent to $expand
$message = Get-MgUserMessage -UserId $userId -MessageId $messageId -ExpandProperty Attachments
```

```python
# GET https://graph.microsoft.com/v1.0/me/messages/{message-id}?$expand=attachments
# message_id is a string containing the id property of the message

# msgraph.generated.users.item.messages.item.message_item_request_builder
query_params = MessageItemRequestBuilder.MessageItemRequestBuilderGetQueryParameters(
    expand=['attachments']
)

config = RequestConfiguration(
    query_parameters=query_params
)

message = await graph_client.me.messages.by_message_id(message_id).get(config)
```

```typescript
// GET https://graph.microsoft.com/v1.0/me/messages/{message-id}?$expand=attachments
// messageId is a string containing the id property of the message
const message = await graphClient
  .api(`/me/messages/${messageId}`)
  .expand('attachments')
  .get();
```

## Delete an entity

Delete requests are constructed in the same way as requests to retrieve an entity, but use a `DELETE` request instead of a `GET`.

- [C#](#tabpanel_6_csharp)
- [Go](#tabpanel_6_go)
- [Java](#tabpanel_6_java)
- [PHP](#tabpanel_6_PHP)
- [PowerShell](#tabpanel_6_powershell)
- [Python](#tabpanel_6_python)
- [TypeScript](#tabpanel_6_typescript)

```csharp
// DELETE https://graph.microsoft.com/v1.0/me/messages/{message-id}
// messageId is a string containing the id property of the message
await graphClient.Me.Messages[messageId]
    .DeleteAsync();
```

```go
// DELETE https://graph.microsoft.com/v1.0/me/messages/{message-id}
// messageId is a string containing the id property of the message
err := graphClient.Me().Messages().
    ByMessageId(messageId).Delete(context.Background(), nil)
```

```java
// DELETE https://graph.microsoft.com/v1.0/me/messages/{message-id}
// messageId is a string containing the id property of the message
graphClient.me().messages().byMessageId(messageId).delete();
```

```php
// DELETE https://graph.microsoft.com/v1.0/me/messages/{message-id}
// messageId is a string containing the id property of the message
$graphClient->me()
    ->messages()
    ->byMessageId($messageId)
    ->delete()
    ->wait();
```

```PowerShell
# DELETE https://graph.microsoft.com/v1.0/users/{user-id}/messages/{message-id}

$userId = "71766077-aacc-470a-be5e-ba47db3b2e88"
$messageId = "AQMkAGUy.."

Remove-MgUserMessage -UserId $userId -MessageId $messageId
```

```python
# DELETE https://graph.microsoft.com/v1.0/me/messages/{message-id}
# message_id is a string containing the id property of the message
await graph_client.me.messages.by_message_id(message_id).delete()
```

```typescript
// DELETE https://graph.microsoft.com/v1.0/me/messages/{message-id}
// messageId is a string containing the id property of the message
await graphClient.api(`/me/messages/${messageId}`).delete();
```

## Creating a new entity with POST

For fluent style and template-based SDKs, new items can be added to collections with a `POST` method. For PowerShell, a `New-*` command accepts parameters that map to the entity to add. The created entity is returned from the call.

- [C#](#tabpanel_7_csharp)
- [Go](#tabpanel_7_go)
- [Java](#tabpanel_7_java)
- [PHP](#tabpanel_7_PHP)
- [PowerShell](#tabpanel_7_powershell)
- [Python](#tabpanel_7_python)
- [TypeScript](#tabpanel_7_typescript)

```csharp
// POST https://graph.microsoft.com/v1.0/me/calendars
var calendar = new Calendar
{
    Name = "Volunteer",
};

var newCalendar = await graphClient.Me.Calendars
    .PostAsync(calendar);
```

```go
// POST https://graph.microsoft.com/v1.0/me/calendars

calendar := models.NewCalendar()
name := "Volunteer"
calendar.SetName(&name)

result, _ := graphClient.Me().Calendars().Post(context.Background(), calendar, nil)
```

```java
// POST https://graph.microsoft.com/v1.0/me/calendars
final Calendar calendar = new Calendar();
calendar.setName("Volunteer");

final Calendar newCalendar = graphClient.me().calendars().post(calendar);
```

```php
// POST https://graph.microsoft.com/v1.0/me/calendars
$calendar = new Models\Calendar();
$calendar->setName('Volunteer');

/** @var Models\Calendar $newCalendar */
$newCalendar = $graphClient->me()
    ->calendars()
    ->post($calendar)
    ->wait();
```

```PowerShell
# POST https://graph.microsoft.com/v1.0/users/{user-id}/calendars

$userId = "71766077-aacc-470a-be5e-ba47db3b2e88"

New-MgUserCalendar -UserId $userId -Name "Volunteer"
```

```python
# POST https://graph.microsoft.com/v1.0/me/calendars

# msgraph.generated.models.calendar
calendar = Calendar()
calendar.name = 'Volunteer'

new_calendar = await graph_client.me.calendars.post(calendar)
```

```typescript
// POST https://graph.microsoft.com/v1.0/me/calendars
const calendar: Calendar = {
  name: 'Volunteer',
};

const newCalendar = await graphClient.api('/me/calendars').post(calendar);
```

## Updating an existing entity with PATCH

Most updates in Microsoft Graph are performed using a `PATCH` method; therefore, it's only necessary to include the properties you want to change in the object you pass.

- [C#](#tabpanel_8_csharp)
- [Go](#tabpanel_8_go)
- [Java](#tabpanel_8_java)
- [PHP](#tabpanel_8_PHP)
- [PowerShell](#tabpanel_8_powershell)
- [Python](#tabpanel_8_python)
- [TypeScript](#tabpanel_8_typescript)

```csharp
// PATCH https://graph.microsoft.com/v1.0/teams/{team-id}
var team = new Team
{
    FunSettings = new TeamFunSettings
    {
        AllowGiphy = true,
        GiphyContentRating = GiphyRatingType.Strict,
    },
};

// teamId is a string containing the id property of the team
await graphClient.Teams[teamId]
    .PatchAsync(team);
```

```go
// PATCH https://graph.microsoft.com/v1.0/teams/{team-id}

funSettings := models.NewTeamFunSettings()
allowGiphy := true
funSettings.SetAllowGiphy(&allowGiphy)
giphyRating := models.STRICT_GIPHYRATINGTYPE
funSettings.SetGiphyContentRating(&giphyRating)

team := models.NewTeam()
team.SetFunSettings(funSettings)

graphClient.Teams().ByTeamId(teamId).Patch(context.Background(), team, nil)
```

```java
// PATCH https://graph.microsoft.com/v1.0/teams/{team-id}
final Team team = new Team();
final TeamFunSettings funSettings = new TeamFunSettings();
funSettings.setAllowGiphy(true);
funSettings.setGiphyContentRating(GiphyRatingType.Strict);
team.setFunSettings(funSettings);

// teamId is a string containing the id property of the team
graphClient.teams().byTeamId(teamId).patch(team);
```

```php
// PATCH https://graph.microsoft.com/v1.0/teams/{team-id}
$funSettings = new Models\TeamFunSettings();
$funSettings->setAllowGiphy(true);
$funSettings->setGiphyContentRating(
    new Models\GiphyRatingType(Models\GiphyRatingType::STRICT));

$team = new Models\Team();
$team->setFunSettings($funSettings);

// $teamId is a string containing the id property of the team
$graphClient->teams()
    ->byTeamId($teamId)
    ->patch($team);
```

```PowerShell
# PATCH https://graph.microsoft.com/v1.0/teams/{team-id}

$teamId = "71766077-aacc-470a-be5e-ba47db3b2e88"

Update-MgTeam -TeamId $teamId -FunSettings @{ AllowGiphy = $true; GiphyContentRating = "strict" }
```

```python
# PATCH https://graph.microsoft.com/v1.0/teams/{team-id}

# msgraph.generated.models.team_fun_settings.TeamFunSettings
fun_settings = TeamFunSettings()
fun_settings.allow_giphy = True
# msgraph.generated.models.giphy_rating_type
fun_settings.giphy_content_rating = GiphyRatingType.Strict

# msgraph.generated.models.team.Team
team = Team()
team.fun_settings = fun_settings

# team_id is a string containing the id property of the team
await graph_client.teams.by_team_id(team_id).patch(team)
```

```typescript
// PATCH https://graph.microsoft.com/v1.0/teams/{team-id}
const team: Team = {
  funSettings: {
    allowGiphy: true,
    giphyContentRating: 'strict',
  },
};

// teamId is a string containing the id property of the team
await graphClient.api(`/teams/${teamId}`).update(team);
```

## Use HTTP headers to control request behavior

You can attach custom headers to a request using the `Headers` collection. For PowerShell, adding headers is only possible with the `Invoke-GraphRequest` method. Some Microsoft Graph scenarios use custom headers to adjust the behavior of the request.

- [C#](#tabpanel_9_csharp)
- [Go](#tabpanel_9_go)
- [Java](#tabpanel_9_java)
- [PHP](#tabpanel_9_PHP)
- [PowerShell](#tabpanel_9_powershell)
- [Python](#tabpanel_9_python)
- [TypeScript](#tabpanel_9_typescript)

```csharp
// GET https://graph.microsoft.com/v1.0/me/events
var events = await graphClient.Me.Events
    .GetAsync(requestConfig =>
    {
        requestConfig.Headers.Add(
            "Prefer", @"outlook.timezone=""Pacific Standard Time""");
    });
```

```go
// GET https://graph.microsoft.com/v1.0/me/events

// import abstractions "github.com/microsoft/kiota-abstractions-go"
headers := abstractions.NewRequestHeaders()
headers.Add("Prefer", "outlook.timezone=\"Pacific Standard Time\"")

// import github.com/microsoftgraph/msgraph-sdk-go/users
options := users.ItemEventsRequestBuilderGetRequestConfiguration{
    Headers: headers,
}

result, _ := graphClient.Me().Events().Get(context.Background(), &options)
```

```java
// GET https://graph.microsoft.com/v1.0/me/events
final EventCollectionResponse events = graphClient.me().events().get( requestConfiguration -> {
    requestConfiguration.headers.add("Prefer", "outlook.timezone=\"Pacific Standard Time\"");
});
```

```php
// GET https://graph.microsoft.com/v1.0/me/events
// Microsoft\Graph\Generated\Users\Item\Events\EventsRequestBuilderGetRequestConfiguration
$config = new EventsRequestBuilderGetRequestConfiguration(
    headers: ['Prefer' => 'outlook.timezone="Pacific Standard Time"']
);

/** @var Models\EventCollectionResponse $events */
$events = $graphClient->me()
    ->events()
    ->get($config)
    ->wait();
```

```PowerShell
# GET https://graph.microsoft.com/v1.0/users/{user-id}/events

$userId = "71766077-aacc-470a-be5e-ba47db3b2e88"
$requestUri = "/v1.0/users/" + $userId + "/events"

$events = Invoke-GraphRequest -Method GET -Uri $requestUri `
-Headers @{ Prefer = "outlook.timezone=""Pacific Standard Time""" }
```

```python
# GET https://graph.microsoft.com/v1.0/me/events

# msgraph.generated.users.item.events.events_request_builder
config = RequestConfiguration()
config.headers.add('Prefer', 'outlook.timezone="Pacific Standard Time"')

events = await graph_client.me.events.get(config)
```

```typescript
// GET https://graph.microsoft.com/v1.0/me/events
const events = await graphClient
  .api('/me/events')
  .header('Prefer', 'outlook.timezone="Pacific Standard Time"')
  .get();
```

## Provide custom query parameters

For SDKs that support the fluent style, you can provide custom query parameter values using the `QueryParameters` object. For template-based SDKs, the parameters are URL-encoded and added to the request URI. For PowerShell and Go, defined query parameters for a given API are exposed as parameters to the corresponding command.

- [C#](#tabpanel_10_csharp)
- [Go](#tabpanel_10_go)
- [Java](#tabpanel_10_java)
- [PHP](#tabpanel_10_PHP)
- [PowerShell](#tabpanel_10_powershell)
- [Python](#tabpanel_10_python)
- [TypeScript](#tabpanel_10_typescript)

```csharp
// GET https://graph.microsoft.com/v1.0/me/calendarView?
// startDateTime=2023-06-14T00:00:00Z&endDateTime=2023-06-15T00:00:00Z
var events = await graphClient.Me.CalendarView
    .GetAsync(requestConfiguration =>
    {
        requestConfiguration.QueryParameters.StartDateTime =
            "2023-06-14T00:00:00Z";
        requestConfiguration.QueryParameters.EndDateTime =
            "2023-06-15T00:00:00Z";
    });
```

```go
// GET https://graph.microsoft.com/v1.0/me/calendarView?
// startDateTime=2023-06-14T00:00:00Z&endDateTime=2023-06-15T00:00:00Z

startDateTime := "2023-06-14T00:00:00"
endDateTime := "2023-06-15T00:00:00Z"

// import github.com/microsoftgraph/msgraph-sdk-go/users
query := users.ItemCalendarViewRequestBuilderGetQueryParameters{
    StartDateTime: &startDateTime,
    EndDateTime:   &endDateTime,
}

options := users.ItemCalendarViewRequestBuilderGetRequestConfiguration{
    QueryParameters: &query,
}

result, _ := graphClient.Me().CalendarView().Get(context.Background(), &options)
```

```java
// GET https://graph.microsoft.com/v1.0/me/calendarView?
// startDateTime=2023-06-14T00:00:00Z&endDateTime=2023-06-15T00:00:00Z
final EventCollectionResponse events = graphClient.me().calendarView().get( requestConfiguration -> {
    requestConfiguration.queryParameters.startDateTime = "2023-06-14T00:00:00Z";
    requestConfiguration.queryParameters.endDateTime = "2023-06-15T00:00:00Z";
});
```

```php
// GET https://graph.microsoft.com/v1.0/me/calendarView?
// startDateTime=2023-06-14T00:00:00Z&endDateTime=2023-06-15T00:00:00Z
// Microsoft\Graph\Generated\Users\Item\CalendarView\CalendarViewRequestBuilderGetQueryParameters
$query = new CalendarViewRequestBuilderGetQueryParameters(
    startDateTime: '2023-06-14T00:00:00Z',
    endDateTime: '2023-06-15T00:00:00Z');

// Microsoft\Graph\Generated\Users\Item\CalendarView\CalendarViewRequestBuilderGetRequestConfiguration
$config = new CalendarViewRequestBuilderGetRequestConfiguration(
    queryParameters: $query);

/** @var Models\EventCollectionResponse $events */
$events = $graphClient->me()
    ->calendarView()
    ->get($config)
    ->wait();
```

```PowerShell
# GET https://graph.microsoft.com/v1.0/users/{user-id}/calendars/{calendar-id}/calendarView

$userId = "71766077-aacc-470a-be5e-ba47db3b2e88"
$calendarId = "AQMkAGUy..."

$events = Get-MgUserCalendarView -UserId $userId -CalendarId $calendarId `
-StartDateTime "2020-08-31T00:00:00Z" -EndDateTime "2020-09-02T00:00:00Z"
```

```python
# GET https://graph.microsoft.com/v1.0/me/calendarView?
# startDateTime=2023-06-14T00:00:00Z&endDateTime=2023-06-15T00:00:00Z

# msgraph.generated.users.item.calendar_view.calendar_view_request_builder
query_params = CalendarViewRequestBuilder.CalendarViewRequestBuilderGetQueryParameters(
    start_date_time='2023-06-14T00:00:00Z',
    end_date_time='2023-06-15T00:00:00Z'
)

config = RequestConfiguration(
    query_parameters=query_params
)

events = await graph_client.me.calendar_view.get(config)
```

```typescript
// GET https://graph.microsoft.com/v1.0/me/calendarView?
// startDateTime=2023-06-14T00:00:00Z&endDateTime=2023-06-15T00:00:00Z
const events = await graphClient
  .api('me/calendar/calendarView')
  .query({
    startDateTime: '2023-06-14T00:00:00Z',
    endDateTime: '2023-06-15T00:00:00Z',
  })
  .get();
```
