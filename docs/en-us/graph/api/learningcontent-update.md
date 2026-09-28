<!-- Source: https://learn.microsoft.com/en-us/graph/api/learningcontent-update?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-04-26 -->

# Update learningContent

Namespace: microsoft.graph

Update the specified [learningContent](https://learn.microsoft.com/en-us/graph/api/resources/learningcontent?view=graph-rest-1.0) resource.

Used by a [learning provider](https://learn.microsoft.com/en-us/graph/api/resources/learningprovider?view=graph-rest-1.0) to ingest or update the metadata for their content in Viva Learning. If the specified learning content doesn't yet exist for the specified provider, this operation creates the metadata for the new content. Otherwise, this operation replaces the metadata of the existing content.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ❌ | ❌ | ❌ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | Not supported. | Not supported. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | LearningContent.ReadWrite.All | Not available. |

## HTTP request

For a specific learning content based on its ID \(primary key\):

```http
PATCH /employeeExperience/learningProviders/{learningProviderId}/learningContents/{learningContentId}
```

For a specific learning content based on its external ID \(secondary key\):

```http
PATCH /employeeExperience/learningProviders/{learningProviderId}/learningContents(externalId='{externalId}') 
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |

## Request body

In the request body, supply *only* the values for properties to update. Existing properties that aren't included in the request body maintain their previous values or are recalculated based on changes to other property values.

The following table specifies the properties that can be updated.

| Property | Type | Description |
| :--- | :--- | :--- |
| additionalTags | String collection | Keywords, topics, and other tags associated with the learning content. Optional. |
| contentWebUrl | String | The content web URL for the learning content. Required. |
| contributors | String collection | The authors, creators, or contributors of the learning content. Optional. |
| createdDateTime | DateTimeOffset | The date and time when the learning content was created. The Timestamp type represents date and time information using ISO 8601 format and is always in UTC time. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z`. Optional. |
| description | String | The description or summary for the learning content. Optional. |
| duration | Duration | The duration of the learning content in seconds. The value is represented in ISO 8601 format for durations. Optional. |
| externalId | String | Unique external content ID for the learning content. Required. |
| format | String | The format of the learning content. For example, `Course`, `Video`, `Book`, `Book Summary`, `Audiobook Summary`. Optional. |
| level | Level | The difficulty level of the learning content. The possible values are: `Beginner`, `Intermediate`, `Advanced`. Optional. |
| isActive | Boolean | Indicates whether the content is active or not. Inactive content doesn't show up in the UI. The default value is `true`. Optional. |
| isPremium | Boolean | Indicates whether the learning content requires the user to sign-in on the learning provider platform or not. The default value is `false`. Optional. |
| isSearchable | Boolean | Indicates whether the learning content is searchable or not. The default value is `true`. Optional. |
| languageTag | String | The language of the learning content, for example, `en-us` or `fr-fr`. Required. |
| lastModifiedDateTime | DateTimeOffset | The date and time when the learning content was last modified. The Timestamp type represents date and time information using ISO 8601 format and is always in UTC time. For example, midnight UTC on Jan 1, 2014 is `2014-01-01T00:00:00Z`. Optional. |
| numberOfPages | Int32 | The number of pages of the learning content, for example, `9`. Optional. |
| skillTags | String collection | The skills tags associated with the learning content. Optional. |
| sourceName | String | The source name of the learning content, such as `LinkedIn Learning` or `Coursera`. Optional. |
| thumbnailWebUrl | String | The URL of learning content thumbnail image. Optional. |
| title | String | The title of the learning content. Required. |

## Response

If successful, this method returns a `202 Accepted` response code and an updated [learningContent](https://learn.microsoft.com/en-us/graph/api/resources/learningcontent?view=graph-rest-1.0) object in the response body.

## Examples

### Example 1: Update the metadata of a learning content based on its ID

The following example shows a request that updates the metadata of a learning content based on its ID \(primary key\).

#### Request

The following example shows the request.

- [HTTP](#tabpanel_1_http)
- [C#](#tabpanel_1_csharp)
- [Go](#tabpanel_1_go)
- [Java](#tabpanel_1_java)
- [JavaScript](#tabpanel_1_javascript)
- [PHP](#tabpanel_1_php)
- [Python](#tabpanel_1_python)

```http
PATCH  https://graph.microsoft.com/v1.0/employeeExperience/learningProviders/13727311-e7bb-470d-8b20-6a23d9030d70/learningContents/77029588-a660-46b6-ba58-3ce4d21d5678
Content-Type: application/json

{
    "title": "Manage classes, resources, assessment, and planning in Microsoft Teams with Beedle",
    "description": "A module to guide users through the various teaching and learning enhancements that Beedle provides within Microsoft Teams, with many examples of everyday application.",
    "contentWebUrl": "https://learn.microsoft.com/learn/modules/manage-classes-resources-assessment-planning-beedle/",
    "sourceName": "MsLearn",
    "thumbnailWebUrl": "https://syndetics.com/index.aspx?isbn=9783319672175/LC.GIF",
    "languageTag": "en-us",
    "numberOfPages": 9,
    "duration": "PT20M",
    "format": "Book",
    "level": "Beginner",
    "createdDateTime": "2018-01-01T00:00:00Z",
    "lastModifiedDateTime": "2021-04-01T04:26:06.1995367Z",
    "contributors": [
      "Lina Wagner",
      "Lisa Richter"
    ],
    "additionalTags": [
        "Create private or public teams",
        "Add members to teams"
    ],
    "skillTags": [
        "Create teams",
        "Teams channels",
        "Teams members"
    ],
    "isActive": true,
    "isPremium": false,
    "isSearchable": true
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models;

var requestBody = new LearningContent
{
	Title = "Manage classes, resources, assessment, and planning in Microsoft Teams with Beedle",
	Description = "A module to guide users through the various teaching and learning enhancements that Beedle provides within Microsoft Teams, with many examples of everyday application.",
	ContentWebUrl = "https://learn.microsoft.com/learn/modules/manage-classes-resources-assessment-planning-beedle/",
	SourceName = "MsLearn",
	ThumbnailWebUrl = "https://syndetics.com/index.aspx?isbn=9783319672175/LC.GIF",
	LanguageTag = "en-us",
	NumberOfPages = 9,
	Duration = TimeSpan.Parse("PT20M"),
	Format = "Book",
	Level = Level.Beginner,
	CreatedDateTime = DateTimeOffset.Parse("2018-01-01T00:00:00Z"),
	LastModifiedDateTime = DateTimeOffset.Parse("2021-04-01T04:26:06.1995367Z"),
	Contributors = new List<string>
	{
		"Lina Wagner",
		"Lisa Richter",
	},
	AdditionalTags = new List<string>
	{
		"Create private or public teams",
		"Add members to teams",
	},
	SkillTags = new List<string>
	{
		"Create teams",
		"Teams channels",
		"Teams members",
	},
	IsActive = true,
	IsPremium = false,
	IsSearchable = true,
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.EmployeeExperience.LearningProviders["{learningProvider-id}"].LearningContents["{learningContent-id}"].PatchAsync(requestBody);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```go


// Code snippets are only available for the latest major version. Current major version is $v1.*

// Dependencies
import (
	  "context"
	  "time"
	  abstractions "github.com/microsoft/kiota-abstractions-go"
	  msgraphsdk "github.com/microsoftgraph/msgraph-sdk-go"
	  graphmodels "github.com/microsoftgraph/msgraph-sdk-go/models"
	  //other-imports
)

requestBody := graphmodels.NewLearningContent()
title := "Manage classes, resources, assessment, and planning in Microsoft Teams with Beedle"
requestBody.SetTitle(&title) 
description := "A module to guide users through the various teaching and learning enhancements that Beedle provides within Microsoft Teams, with many examples of everyday application."
requestBody.SetDescription(&description) 
contentWebUrl := "https://learn.microsoft.com/learn/modules/manage-classes-resources-assessment-planning-beedle/"
requestBody.SetContentWebUrl(&contentWebUrl) 
sourceName := "MsLearn"
requestBody.SetSourceName(&sourceName) 
thumbnailWebUrl := "https://syndetics.com/index.aspx?isbn=9783319672175/LC.GIF"
requestBody.SetThumbnailWebUrl(&thumbnailWebUrl) 
languageTag := "en-us"
requestBody.SetLanguageTag(&languageTag) 
numberOfPages := int32(9)
requestBody.SetNumberOfPages(&numberOfPages) 
duration , err := abstractions.ParseISODuration("PT20M")
requestBody.SetDuration(&duration) 
format := "Book"
requestBody.SetFormat(&format) 
level := graphmodels.BEGINNER_LEVEL 
requestBody.SetLevel(&level) 
createdDateTime , err := time.Parse(time.RFC3339, "2018-01-01T00:00:00Z")
requestBody.SetCreatedDateTime(&createdDateTime) 
lastModifiedDateTime , err := time.Parse(time.RFC3339, "2021-04-01T04:26:06.1995367Z")
requestBody.SetLastModifiedDateTime(&lastModifiedDateTime) 
contributors := []string {
	"Lina Wagner",
	"Lisa Richter",
}
requestBody.SetContributors(contributors)
additionalTags := []string {
	"Create private or public teams",
	"Add members to teams",
}
requestBody.SetAdditionalTags(additionalTags)
skillTags := []string {
	"Create teams",
	"Teams channels",
	"Teams members",
}
requestBody.SetSkillTags(skillTags)
isActive := true
requestBody.SetIsActive(&isActive) 
isPremium := false
requestBody.SetIsPremium(&isPremium) 
isSearchable := true
requestBody.SetIsSearchable(&isSearchable) 

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
learningContents, err := graphClient.EmployeeExperience().LearningProviders().ByLearningProviderId("learningProvider-id").LearningContents().ByLearningContentId("learningContent-id").Patch(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

LearningContent learningContent = new LearningContent();
learningContent.setTitle("Manage classes, resources, assessment, and planning in Microsoft Teams with Beedle");
learningContent.setDescription("A module to guide users through the various teaching and learning enhancements that Beedle provides within Microsoft Teams, with many examples of everyday application.");
learningContent.setContentWebUrl("https://learn.microsoft.com/learn/modules/manage-classes-resources-assessment-planning-beedle/");
learningContent.setSourceName("MsLearn");
learningContent.setThumbnailWebUrl("https://syndetics.com/index.aspx?isbn=9783319672175/LC.GIF");
learningContent.setLanguageTag("en-us");
learningContent.setNumberOfPages(9);
PeriodAndDuration duration = PeriodAndDuration.ofDuration(Duration.parse("PT20M"));
learningContent.setDuration(duration);
learningContent.setFormat("Book");
learningContent.setLevel(Level.Beginner);
OffsetDateTime createdDateTime = OffsetDateTime.parse("2018-01-01T00:00:00Z");
learningContent.setCreatedDateTime(createdDateTime);
OffsetDateTime lastModifiedDateTime = OffsetDateTime.parse("2021-04-01T04:26:06.1995367Z");
learningContent.setLastModifiedDateTime(lastModifiedDateTime);
LinkedList<String> contributors = new LinkedList<String>();
contributors.add("Lina Wagner");
contributors.add("Lisa Richter");
learningContent.setContributors(contributors);
LinkedList<String> additionalTags = new LinkedList<String>();
additionalTags.add("Create private or public teams");
additionalTags.add("Add members to teams");
learningContent.setAdditionalTags(additionalTags);
LinkedList<String> skillTags = new LinkedList<String>();
skillTags.add("Create teams");
skillTags.add("Teams channels");
skillTags.add("Teams members");
learningContent.setSkillTags(skillTags);
learningContent.setIsActive(true);
learningContent.setIsPremium(false);
learningContent.setIsSearchable(true);
LearningContent result = graphClient.employeeExperience().learningProviders().byLearningProviderId("{learningProvider-id}").learningContents().byLearningContentId("{learningContent-id}").patch(learningContent);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const learningContent = {
    title: 'Manage classes, resources, assessment, and planning in Microsoft Teams with Beedle',
    description: 'A module to guide users through the various teaching and learning enhancements that Beedle provides within Microsoft Teams, with many examples of everyday application.',
    contentWebUrl: 'https://learn.microsoft.com/learn/modules/manage-classes-resources-assessment-planning-beedle/',
    sourceName: 'MsLearn',
    thumbnailWebUrl: 'https://syndetics.com/index.aspx?isbn=9783319672175/LC.GIF',
    languageTag: 'en-us',
    numberOfPages: 9,
    duration: 'PT20M',
    format: 'Book',
    level: 'Beginner',
    createdDateTime: '2018-01-01T00:00:00Z',
    lastModifiedDateTime: '2021-04-01T04:26:06.1995367Z',
    contributors: [
      'Lina Wagner',
      'Lisa Richter'
    ],
    additionalTags: [
        'Create private or public teams',
        'Add members to teams'
    ],
    skillTags: [
        'Create teams',
        'Teams channels',
        'Teams members'
    ],
    isActive: true,
    isPremium: false,
    isSearchable: true
};

await client.api('/employeeExperience/learningProviders/13727311-e7bb-470d-8b20-6a23d9030d70/learningContents/77029588-a660-46b6-ba58-3ce4d21d5678')
	.update(learningContent);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\LearningContent;
use Microsoft\Graph\Generated\Models\Level;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new LearningContent();
$requestBody->setTitle('Manage classes, resources, assessment, and planning in Microsoft Teams with Beedle');
$requestBody->setDescription('A module to guide users through the various teaching and learning enhancements that Beedle provides within Microsoft Teams, with many examples of everyday application.');
$requestBody->setContentWebUrl('https://learn.microsoft.com/learn/modules/manage-classes-resources-assessment-planning-beedle/');
$requestBody->setSourceName('MsLearn');
$requestBody->setThumbnailWebUrl('https://syndetics.com/index.aspx?isbn=9783319672175/LC.GIF');
$requestBody->setLanguageTag('en-us');
$requestBody->setNumberOfPages(9);
$requestBody->setDuration(new \DateInterval('PT20M'));
$requestBody->setFormat('Book');
$requestBody->setLevel(new Level('beginner'));
$requestBody->setCreatedDateTime(new \DateTime('2018-01-01T00:00:00Z'));
$requestBody->setLastModifiedDateTime(new \DateTime('2021-04-01T04:26:06.1995367Z'));
$requestBody->setContributors(['Lina Wagner', 'Lisa Richter', 	]);
$requestBody->setAdditionalTags(['Create private or public teams', 'Add members to teams', 	]);
$requestBody->setSkillTags(['Create teams', 'Teams channels', 'Teams members', 	]);
$requestBody->setIsActive(true);
$requestBody->setIsPremium(false);
$requestBody->setIsSearchable(true);

$result = $graphServiceClient->employeeExperience()->learningProviders()->byLearningProviderId('learningProvider-id')->learningContents()->byLearningContentId('learningContent-id')->patch($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.learning_content import LearningContent
from msgraph.generated.models.level import Level
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = LearningContent(
	title = "Manage classes, resources, assessment, and planning in Microsoft Teams with Beedle",
	description = "A module to guide users through the various teaching and learning enhancements that Beedle provides within Microsoft Teams, with many examples of everyday application.",
	content_web_url = "https://learn.microsoft.com/learn/modules/manage-classes-resources-assessment-planning-beedle/",
	source_name = "MsLearn",
	thumbnail_web_url = "https://syndetics.com/index.aspx?isbn=9783319672175/LC.GIF",
	language_tag = "en-us",
	number_of_pages = 9,
	duration = "PT20M",
	format = "Book",
	level = Level.Beginner,
	created_date_time = "2018-01-01T00:00:00Z",
	last_modified_date_time = "2021-04-01T04:26:06.1995367Z",
	contributors = [
		"Lina Wagner",
		"Lisa Richter",
	],
	additional_tags = [
		"Create private or public teams",
		"Add members to teams",
	],
	skill_tags = [
		"Create teams",
		"Teams channels",
		"Teams members",
	],
	is_active = True,
	is_premium = False,
	is_searchable = True,
)

result = await graph_client.employee_experience.learning_providers.by_learning_provider_id('learningProvider-id').learning_contents.by_learning_content_id('learningContent-id').patch(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 202 Accepted
Content-Type: application/json

{
    "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#learningProviders('13727311-e7bb-470d-8b20-6a23d9030d70')/learningContents/$entity",
    "id": "77029588-a660-46b6-ba58-3ce4d21d5678",
    "externalId": "LP4471",
    "title": "Manage classes, resources, assessment, and planning in Microsoft Teams with Beedle",
    "description": "A module to guide users through the various teaching and learning enhancements that Beedle provides within Microsoft Teams, with many examples of everyday application.",
    "contentWebUrl": "https://learn.microsoft.com/learn/modules/manage-classes-resources-assessment-planning-beedle/",
    "sourceName": "MsLearn",
    "thumbnailWebUrl": "https://syndetics.com/index.aspx?isbn=9783319672175/LC.GIF",
    "languageTag": "en-us",
    "numberOfPages": 9,
    "duration": "PT20M",
    "format": "Book",
    "level": "Beginner",
    "createdDateTime": "2018-01-01T00:00:00",
    "lastModifiedDateTime": "2021-04-01T04:26:06.1995367Z",
    "contributors": [
      "Lina Wagner",
      "Lisa Richter"
    ],
    "additionalTags": [
        "Create private or public teams",
        "Add members to teams"
    ],
    "skillTags": [
        "Create teams",
        "Teams channels",
        "Teams members"
    ],
    "isActive": true,
    "isPremium": false,
    "isSearchable": true
}
```

### Example 2: Update the metadata of a learning content based on its external ID

The following example shows a request that updates the metadata of a learning content based on its external ID \(secondary key\).

#### Request

The following example shows the request.

- [HTTP](#tabpanel_2_http)
- [C#](#tabpanel_2_csharp)
- [Go](#tabpanel_2_go)
- [Java](#tabpanel_2_java)
- [JavaScript](#tabpanel_2_javascript)
- [PHP](#tabpanel_2_php)
- [Python](#tabpanel_2_python)

```http
PATCH  https://graph.microsoft.com/v1.0/employeeExperience/learningProviders/13727311-e7bb-470d-8b20-6a23d9030d70/learningContents(externalId='LP4471') 
Content-Type: application/json

{
    "title": "Manage classes, resources, assessment, and planning in Microsoft Teams with Beedle",
    "description": "A module to guide users through the various teaching and learning enhancements that Beedle provides within Microsoft Teams, with many examples of everyday application.",
    "contentWebUrl": "https://learn.microsoft.com/learn/modules/manage-classes-resources-assessment-planning-beedle/",
    "sourceName": "MsLearn",
    "thumbnailWebUrl": "https://syndetics.com/index.aspx?isbn=9783319672175/LC.GIF",
    "languageTag": "en-us",
    "numberOfPages": 9,
    "duration": "PT20M",
    "format": "Book",
    "level": "Beginner",
    "createdDateTime": "2018-01-01T00:00:00",
    "lastModifiedDateTime": "2021-04-01T04:26:06.1995367Z",
    "contributors": [
        "Lina Wagner",
        "Lisa Richter"
    ],
    "additionalTags": [
        "Create private or public teams",
        "Add members to teams"
    ],
    "skillTags": [
        "Create teams",
        "Teams channels",
        "Teams members"
    ],
    "isActive": true,
    "isPremium": false,
    "isSearchable": true
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models;

var requestBody = new LearningContent
{
	Title = "Manage classes, resources, assessment, and planning in Microsoft Teams with Beedle",
	Description = "A module to guide users through the various teaching and learning enhancements that Beedle provides within Microsoft Teams, with many examples of everyday application.",
	ContentWebUrl = "https://learn.microsoft.com/learn/modules/manage-classes-resources-assessment-planning-beedle/",
	SourceName = "MsLearn",
	ThumbnailWebUrl = "https://syndetics.com/index.aspx?isbn=9783319672175/LC.GIF",
	LanguageTag = "en-us",
	NumberOfPages = 9,
	Duration = TimeSpan.Parse("PT20M"),
	Format = "Book",
	Level = Level.Beginner,
	CreatedDateTime = DateTimeOffset.Parse("2018-01-01T00:00:00"),
	LastModifiedDateTime = DateTimeOffset.Parse("2021-04-01T04:26:06.1995367Z"),
	Contributors = new List<string>
	{
		"Lina Wagner",
		"Lisa Richter",
	},
	AdditionalTags = new List<string>
	{
		"Create private or public teams",
		"Add members to teams",
	},
	SkillTags = new List<string>
	{
		"Create teams",
		"Teams channels",
		"Teams members",
	},
	IsActive = true,
	IsPremium = false,
	IsSearchable = true,
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.EmployeeExperience.LearningProviders["{learningProvider-id}"].LearningContentsWithExternalId("{externalId}").PatchAsync(requestBody);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```go


// Code snippets are only available for the latest major version. Current major version is $v1.*

// Dependencies
import (
	  "context"
	  "time"
	  abstractions "github.com/microsoft/kiota-abstractions-go"
	  msgraphsdk "github.com/microsoftgraph/msgraph-sdk-go"
	  graphmodels "github.com/microsoftgraph/msgraph-sdk-go/models"
	  //other-imports
)

requestBody := graphmodels.NewLearningContent()
title := "Manage classes, resources, assessment, and planning in Microsoft Teams with Beedle"
requestBody.SetTitle(&title) 
description := "A module to guide users through the various teaching and learning enhancements that Beedle provides within Microsoft Teams, with many examples of everyday application."
requestBody.SetDescription(&description) 
contentWebUrl := "https://learn.microsoft.com/learn/modules/manage-classes-resources-assessment-planning-beedle/"
requestBody.SetContentWebUrl(&contentWebUrl) 
sourceName := "MsLearn"
requestBody.SetSourceName(&sourceName) 
thumbnailWebUrl := "https://syndetics.com/index.aspx?isbn=9783319672175/LC.GIF"
requestBody.SetThumbnailWebUrl(&thumbnailWebUrl) 
languageTag := "en-us"
requestBody.SetLanguageTag(&languageTag) 
numberOfPages := int32(9)
requestBody.SetNumberOfPages(&numberOfPages) 
duration , err := abstractions.ParseISODuration("PT20M")
requestBody.SetDuration(&duration) 
format := "Book"
requestBody.SetFormat(&format) 
level := graphmodels.BEGINNER_LEVEL 
requestBody.SetLevel(&level) 
createdDateTime , err := time.Parse(time.RFC3339, "2018-01-01T00:00:00")
requestBody.SetCreatedDateTime(&createdDateTime) 
lastModifiedDateTime , err := time.Parse(time.RFC3339, "2021-04-01T04:26:06.1995367Z")
requestBody.SetLastModifiedDateTime(&lastModifiedDateTime) 
contributors := []string {
	"Lina Wagner",
	"Lisa Richter",
}
requestBody.SetContributors(contributors)
additionalTags := []string {
	"Create private or public teams",
	"Add members to teams",
}
requestBody.SetAdditionalTags(additionalTags)
skillTags := []string {
	"Create teams",
	"Teams channels",
	"Teams members",
}
requestBody.SetSkillTags(skillTags)
isActive := true
requestBody.SetIsActive(&isActive) 
isPremium := false
requestBody.SetIsPremium(&isPremium) 
isSearchable := true
requestBody.SetIsSearchable(&isSearchable) 

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
externalId := "{externalId}"
learningContents, err := graphClient.EmployeeExperience().LearningProviders().ByLearningProviderId("learningProvider-id").LearningContentsWithExternalId(&externalId).Patch(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

LearningContent learningContent = new LearningContent();
learningContent.setTitle("Manage classes, resources, assessment, and planning in Microsoft Teams with Beedle");
learningContent.setDescription("A module to guide users through the various teaching and learning enhancements that Beedle provides within Microsoft Teams, with many examples of everyday application.");
learningContent.setContentWebUrl("https://learn.microsoft.com/learn/modules/manage-classes-resources-assessment-planning-beedle/");
learningContent.setSourceName("MsLearn");
learningContent.setThumbnailWebUrl("https://syndetics.com/index.aspx?isbn=9783319672175/LC.GIF");
learningContent.setLanguageTag("en-us");
learningContent.setNumberOfPages(9);
PeriodAndDuration duration = PeriodAndDuration.ofDuration(Duration.parse("PT20M"));
learningContent.setDuration(duration);
learningContent.setFormat("Book");
learningContent.setLevel(Level.Beginner);
OffsetDateTime createdDateTime = OffsetDateTime.parse("2018-01-01T00:00:00");
learningContent.setCreatedDateTime(createdDateTime);
OffsetDateTime lastModifiedDateTime = OffsetDateTime.parse("2021-04-01T04:26:06.1995367Z");
learningContent.setLastModifiedDateTime(lastModifiedDateTime);
LinkedList<String> contributors = new LinkedList<String>();
contributors.add("Lina Wagner");
contributors.add("Lisa Richter");
learningContent.setContributors(contributors);
LinkedList<String> additionalTags = new LinkedList<String>();
additionalTags.add("Create private or public teams");
additionalTags.add("Add members to teams");
learningContent.setAdditionalTags(additionalTags);
LinkedList<String> skillTags = new LinkedList<String>();
skillTags.add("Create teams");
skillTags.add("Teams channels");
skillTags.add("Teams members");
learningContent.setSkillTags(skillTags);
learningContent.setIsActive(true);
learningContent.setIsPremium(false);
learningContent.setIsSearchable(true);
LearningContent result = graphClient.employeeExperience().learningProviders().byLearningProviderId("{learningProvider-id}").learningContentsWithExternalId("{externalId}").patch(learningContent);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```
Snippet not available
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\LearningContent;
use Microsoft\Graph\Generated\Models\Level;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new LearningContent();
$requestBody->setTitle('Manage classes, resources, assessment, and planning in Microsoft Teams with Beedle');
$requestBody->setDescription('A module to guide users through the various teaching and learning enhancements that Beedle provides within Microsoft Teams, with many examples of everyday application.');
$requestBody->setContentWebUrl('https://learn.microsoft.com/learn/modules/manage-classes-resources-assessment-planning-beedle/');
$requestBody->setSourceName('MsLearn');
$requestBody->setThumbnailWebUrl('https://syndetics.com/index.aspx?isbn=9783319672175/LC.GIF');
$requestBody->setLanguageTag('en-us');
$requestBody->setNumberOfPages(9);
$requestBody->setDuration(new \DateInterval('PT20M'));
$requestBody->setFormat('Book');
$requestBody->setLevel(new Level('beginner'));
$requestBody->setCreatedDateTime(new \DateTime('2018-01-01T00:00:00'));
$requestBody->setLastModifiedDateTime(new \DateTime('2021-04-01T04:26:06.1995367Z'));
$requestBody->setContributors(['Lina Wagner', 'Lisa Richter', 	]);
$requestBody->setAdditionalTags(['Create private or public teams', 'Add members to teams', 	]);
$requestBody->setSkillTags(['Create teams', 'Teams channels', 'Teams members', 	]);
$requestBody->setIsActive(true);
$requestBody->setIsPremium(false);
$requestBody->setIsSearchable(true);

$result = $graphServiceClient->employeeExperience()->learningProviders()->byLearningProviderId('learningProvider-id')->learningContentsWithExternalId('{externalId}', )->patch($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.learning_content import LearningContent
from msgraph.generated.models.level import Level
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = LearningContent(
	title = "Manage classes, resources, assessment, and planning in Microsoft Teams with Beedle",
	description = "A module to guide users through the various teaching and learning enhancements that Beedle provides within Microsoft Teams, with many examples of everyday application.",
	content_web_url = "https://learn.microsoft.com/learn/modules/manage-classes-resources-assessment-planning-beedle/",
	source_name = "MsLearn",
	thumbnail_web_url = "https://syndetics.com/index.aspx?isbn=9783319672175/LC.GIF",
	language_tag = "en-us",
	number_of_pages = 9,
	duration = "PT20M",
	format = "Book",
	level = Level.Beginner,
	created_date_time = "2018-01-01T00:00:00",
	last_modified_date_time = "2021-04-01T04:26:06.1995367Z",
	contributors = [
		"Lina Wagner",
		"Lisa Richter",
	],
	additional_tags = [
		"Create private or public teams",
		"Add members to teams",
	],
	skill_tags = [
		"Create teams",
		"Teams channels",
		"Teams members",
	],
	is_active = True,
	is_premium = False,
	is_searchable = True,
)

result = await graph_client.employee_experience.learning_providers.by_learning_provider_id('learningProvider-id').learning_contents_with_external_id("{externalId}").patch(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 202 Accepted
Content-Type: application/json

{
    "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#learningProviders('13727311-e7bb-470d-8b20-6a23d9030d70')/learningContents/$entity",
    "id": "77029588-a660-46b6-ba58-3ce4d21d5678",
    "externalId": "LP4471",
    "title": "Manage classes, resources, assessment, and planning in Microsoft Teams with Beedle",
    "description": "A module to guide users through the various teaching and learning enhancements that Beedle provides within Microsoft Teams, with many examples of everyday application.",
    "contentWebUrl": "https://learn.microsoft.com/learn/modules/manage-classes-resources-assessment-planning-beedle/",
    "sourceName": "MsLearn",
    "thumbnailWebUrl": "https://syndetics.com/index.aspx?isbn=9783319672175/LC.GIF",
    "languageTag": "en-us",
    "numberOfPages": 9,
    "duration": "PT20M",
    "format": "Book",
    "level": "Beginner",
    "createdDateTime": "2018-01-01T00:00:00",
    "lastModifiedDateTime": "2021-04-01T04:26:06.1995367Z",
    "contributors": [
        "Lina Wagner",
        "Lisa Richter"
    ],
    "additionalTags": [
        "Create private or public teams",
        "Add members to teams"
    ],
    "skillTags": [
        "Create teams",
        "Teams channels",
        "Teams members"
    ],
    "isActive": true,
    "isPremium": false,
    "isSearchable": true
}
```
