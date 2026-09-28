<!-- Source: https://learn.microsoft.com/en-us/graph/api/educationuser-post-rubrics?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-07-23 -->

# Create educationRubric

Namespace: microsoft.graph

Create a new [educationRubric](https://learn.microsoft.com/en-us/graph/api/resources/educationrubric?view=graph-rest-1.0) object.

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ❌ | ❌ | ❌ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | EduAssignments.ReadWriteBasic | EduAssignments.ReadWrite |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | Not supported. | Not supported. |

## HTTP request

```http
POST /education/me/rubrics
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |

## Request body

In the request body, supply a JSON representation of an [educationRubric](https://learn.microsoft.com/en-us/graph/api/resources/educationrubric?view=graph-rest-1.0) object.

## Response

If successful, this method returns a `201 Created` response code and a new [educationRubric](https://learn.microsoft.com/en-us/graph/api/resources/educationrubric?view=graph-rest-1.0) object in the response body.

## Examples

### Example 1: Post a credit rubric

#### Request

The following example shows a request to post a credit rubric \(a rubric with no points\).

- [HTTP](#tabpanel_1_http)
- [C#](#tabpanel_1_csharp)
- [Go](#tabpanel_1_go)
- [Java](#tabpanel_1_java)
- [JavaScript](#tabpanel_1_javascript)
- [PHP](#tabpanel_1_php)
- [PowerShell](#tabpanel_1_powershell)
- [Python](#tabpanel_1_python)

```http
POST https://graph.microsoft.com/v1.0/education/me/rubrics
Content-type: application/json

{
    "displayName":"Example Credit Rubric",
    "description":{
        "content":"This is an example of a credit rubric (no points)",
        "contentType":"text"
    },
    "levels":[
        {
            "displayName":"Good",
            "description":{
                "content":"",
                "contentType":"text"
            }
        },
        {
            "displayName":"Poor",
            "description":{
                "content":"",
                "contentType":"text"
            }
        }
    ],
    "qualities":[
        {
            "description":{
                "content":"Argument",
                "contentType":"text"
            },
            "criteria":[
                {
                    "description":{
                        "content":"The essay's argument is persuasive.",
                        "contentType":"text"
                    }
                },
                {
                    "description":{
                        "content":"The essay's argument does not make sense.",
                        "contentType":"text"
                    }
                }
            ]
        },
        {
            "description":{
                "content":"Spelling and Grammar",
                "contentType":"text"
            },
            "criteria":[
                {
                    "description":{
                        "content":"The essay uses proper spelling and grammar with few or no errors.",
                        "contentType":"text"
                    }
                },
                {
                    "description":{
                        "content":"The essay has numerous errors in spelling and/or grammar.",
                        "contentType":"text"
                    }
                }
            ]
        }
    ]
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models;

var requestBody = new EducationRubric
{
	DisplayName = "Example Credit Rubric",
	Description = new EducationItemBody
	{
		Content = "This is an example of a credit rubric (no points)",
		ContentType = BodyType.Text,
	},
	Levels = new List<RubricLevel>
	{
		new RubricLevel
		{
			DisplayName = "Good",
			Description = new EducationItemBody
			{
				Content = "",
				ContentType = BodyType.Text,
			},
		},
		new RubricLevel
		{
			DisplayName = "Poor",
			Description = new EducationItemBody
			{
				Content = "",
				ContentType = BodyType.Text,
			},
		},
	},
	Qualities = new List<RubricQuality>
	{
		new RubricQuality
		{
			Description = new EducationItemBody
			{
				Content = "Argument",
				ContentType = BodyType.Text,
			},
			Criteria = new List<RubricCriterion>
			{
				new RubricCriterion
				{
					Description = new EducationItemBody
					{
						Content = "The essay's argument is persuasive.",
						ContentType = BodyType.Text,
					},
				},
				new RubricCriterion
				{
					Description = new EducationItemBody
					{
						Content = "The essay's argument does not make sense.",
						ContentType = BodyType.Text,
					},
				},
			},
		},
		new RubricQuality
		{
			Description = new EducationItemBody
			{
				Content = "Spelling and Grammar",
				ContentType = BodyType.Text,
			},
			Criteria = new List<RubricCriterion>
			{
				new RubricCriterion
				{
					Description = new EducationItemBody
					{
						Content = "The essay uses proper spelling and grammar with few or no errors.",
						ContentType = BodyType.Text,
					},
				},
				new RubricCriterion
				{
					Description = new EducationItemBody
					{
						Content = "The essay has numerous errors in spelling and/or grammar.",
						ContentType = BodyType.Text,
					},
				},
			},
		},
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Education.Me.Rubrics.PostAsync(requestBody);
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

requestBody := graphmodels.NewEducationRubric()
displayName := "Example Credit Rubric"
requestBody.SetDisplayName(&displayName) 
description := graphmodels.NewEducationItemBody()
content := "This is an example of a credit rubric (no points)"
description.SetContent(&content) 
contentType := graphmodels.TEXT_BODYTYPE 
description.SetContentType(&contentType) 
requestBody.SetDescription(description)


rubricLevel := graphmodels.NewRubricLevel()
displayName := "Good"
rubricLevel.SetDisplayName(&displayName) 
description := graphmodels.NewEducationItemBody()
content := ""
description.SetContent(&content) 
contentType := graphmodels.TEXT_BODYTYPE 
description.SetContentType(&contentType) 
rubricLevel.SetDescription(description)
rubricLevel1 := graphmodels.NewRubricLevel()
displayName := "Poor"
rubricLevel1.SetDisplayName(&displayName) 
description := graphmodels.NewEducationItemBody()
content := ""
description.SetContent(&content) 
contentType := graphmodels.TEXT_BODYTYPE 
description.SetContentType(&contentType) 
rubricLevel1.SetDescription(description)

levels := []graphmodels.RubricLevelable {
	rubricLevel,
	rubricLevel1,
}
requestBody.SetLevels(levels)


rubricQuality := graphmodels.NewRubricQuality()
description := graphmodels.NewEducationItemBody()
content := "Argument"
description.SetContent(&content) 
contentType := graphmodels.TEXT_BODYTYPE 
description.SetContentType(&contentType) 
rubricQuality.SetDescription(description)


rubricCriterion := graphmodels.NewRubricCriterion()
description := graphmodels.NewEducationItemBody()
content := "The essay's argument is persuasive."
description.SetContent(&content) 
contentType := graphmodels.TEXT_BODYTYPE 
description.SetContentType(&contentType) 
rubricCriterion.SetDescription(description)
rubricCriterion1 := graphmodels.NewRubricCriterion()
description := graphmodels.NewEducationItemBody()
content := "The essay's argument does not make sense."
description.SetContent(&content) 
contentType := graphmodels.TEXT_BODYTYPE 
description.SetContentType(&contentType) 
rubricCriterion1.SetDescription(description)

criteria := []graphmodels.RubricCriterionable {
	rubricCriterion,
	rubricCriterion1,
}
rubricQuality.SetCriteria(criteria)
rubricQuality1 := graphmodels.NewRubricQuality()
description := graphmodels.NewEducationItemBody()
content := "Spelling and Grammar"
description.SetContent(&content) 
contentType := graphmodels.TEXT_BODYTYPE 
description.SetContentType(&contentType) 
rubricQuality1.SetDescription(description)


rubricCriterion := graphmodels.NewRubricCriterion()
description := graphmodels.NewEducationItemBody()
content := "The essay uses proper spelling and grammar with few or no errors."
description.SetContent(&content) 
contentType := graphmodels.TEXT_BODYTYPE 
description.SetContentType(&contentType) 
rubricCriterion.SetDescription(description)
rubricCriterion1 := graphmodels.NewRubricCriterion()
description := graphmodels.NewEducationItemBody()
content := "The essay has numerous errors in spelling and/or grammar."
description.SetContent(&content) 
contentType := graphmodels.TEXT_BODYTYPE 
description.SetContentType(&contentType) 
rubricCriterion1.SetDescription(description)

criteria := []graphmodels.RubricCriterionable {
	rubricCriterion,
	rubricCriterion1,
}
rubricQuality1.SetCriteria(criteria)

qualities := []graphmodels.RubricQualityable {
	rubricQuality,
	rubricQuality1,
}
requestBody.SetQualities(qualities)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
rubrics, err := graphClient.Education().Me().Rubrics().Post(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

EducationRubric educationRubric = new EducationRubric();
educationRubric.setDisplayName("Example Credit Rubric");
EducationItemBody description = new EducationItemBody();
description.setContent("This is an example of a credit rubric (no points)");
description.setContentType(BodyType.Text);
educationRubric.setDescription(description);
LinkedList<RubricLevel> levels = new LinkedList<RubricLevel>();
RubricLevel rubricLevel = new RubricLevel();
rubricLevel.setDisplayName("Good");
EducationItemBody description1 = new EducationItemBody();
description1.setContent("");
description1.setContentType(BodyType.Text);
rubricLevel.setDescription(description1);
levels.add(rubricLevel);
RubricLevel rubricLevel1 = new RubricLevel();
rubricLevel1.setDisplayName("Poor");
EducationItemBody description2 = new EducationItemBody();
description2.setContent("");
description2.setContentType(BodyType.Text);
rubricLevel1.setDescription(description2);
levels.add(rubricLevel1);
educationRubric.setLevels(levels);
LinkedList<RubricQuality> qualities = new LinkedList<RubricQuality>();
RubricQuality rubricQuality = new RubricQuality();
EducationItemBody description3 = new EducationItemBody();
description3.setContent("Argument");
description3.setContentType(BodyType.Text);
rubricQuality.setDescription(description3);
LinkedList<RubricCriterion> criteria = new LinkedList<RubricCriterion>();
RubricCriterion rubricCriterion = new RubricCriterion();
EducationItemBody description4 = new EducationItemBody();
description4.setContent("The essay's argument is persuasive.");
description4.setContentType(BodyType.Text);
rubricCriterion.setDescription(description4);
criteria.add(rubricCriterion);
RubricCriterion rubricCriterion1 = new RubricCriterion();
EducationItemBody description5 = new EducationItemBody();
description5.setContent("The essay's argument does not make sense.");
description5.setContentType(BodyType.Text);
rubricCriterion1.setDescription(description5);
criteria.add(rubricCriterion1);
rubricQuality.setCriteria(criteria);
qualities.add(rubricQuality);
RubricQuality rubricQuality1 = new RubricQuality();
EducationItemBody description6 = new EducationItemBody();
description6.setContent("Spelling and Grammar");
description6.setContentType(BodyType.Text);
rubricQuality1.setDescription(description6);
LinkedList<RubricCriterion> criteria1 = new LinkedList<RubricCriterion>();
RubricCriterion rubricCriterion2 = new RubricCriterion();
EducationItemBody description7 = new EducationItemBody();
description7.setContent("The essay uses proper spelling and grammar with few or no errors.");
description7.setContentType(BodyType.Text);
rubricCriterion2.setDescription(description7);
criteria1.add(rubricCriterion2);
RubricCriterion rubricCriterion3 = new RubricCriterion();
EducationItemBody description8 = new EducationItemBody();
description8.setContent("The essay has numerous errors in spelling and/or grammar.");
description8.setContentType(BodyType.Text);
rubricCriterion3.setDescription(description8);
criteria1.add(rubricCriterion3);
rubricQuality1.setCriteria(criteria1);
qualities.add(rubricQuality1);
educationRubric.setQualities(qualities);
EducationRubric result = graphClient.education().me().rubrics().post(educationRubric);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const educationRubric = {
    displayName: 'Example Credit Rubric',
    description: {
        content: 'This is an example of a credit rubric (no points)',
        contentType: 'text'
    },
    levels: [
        {
            displayName: 'Good',
            description: {
                content: '',
                contentType: 'text'
            }
        },
        {
            displayName: 'Poor',
            description: {
                content: '',
                contentType: 'text'
            }
        }
    ],
    qualities: [
        {
            description: {
                content: 'Argument',
                contentType: 'text'
            },
            criteria: [
                {
                    description: {
                        content: 'The essay\'s argument is persuasive.',
                        contentType: 'text'
                    }
                },
                {
                    description: {
                        content: 'The essay\'s argument does not make sense.',
                        contentType: 'text'
                    }
                }
            ]
        },
        {
            description: {
                content: 'Spelling and Grammar',
                contentType: 'text'
            },
            criteria: [
                {
                    description: {
                        content: 'The essay uses proper spelling and grammar with few or no errors.',
                        contentType: 'text'
                    }
                },
                {
                    description: {
                        content: 'The essay has numerous errors in spelling and/or grammar.',
                        contentType: 'text'
                    }
                }
            ]
        }
    ]
};

await client.api('/education/me/rubrics')
	.post(educationRubric);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\EducationRubric;
use Microsoft\Graph\Generated\Models\EducationItemBody;
use Microsoft\Graph\Generated\Models\BodyType;
use Microsoft\Graph\Generated\Models\RubricLevel;
use Microsoft\Graph\Generated\Models\RubricQuality;
use Microsoft\Graph\Generated\Models\RubricCriterion;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new EducationRubric();
$requestBody->setDisplayName('Example Credit Rubric');
$description = new EducationItemBody();
$description->setContent('This is an example of a credit rubric (no points)');
$description->setContentType(new BodyType('text'));
$requestBody->setDescription($description);
$levelsRubricLevel1 = new RubricLevel();
$levelsRubricLevel1->setDisplayName('Good');
$levelsRubricLevel1Description = new EducationItemBody();
$levelsRubricLevel1Description->setContent('');
$levelsRubricLevel1Description->setContentType(new BodyType('text'));
$levelsRubricLevel1->setDescription($levelsRubricLevel1Description);
$levelsArray []= $levelsRubricLevel1;
$levelsRubricLevel2 = new RubricLevel();
$levelsRubricLevel2->setDisplayName('Poor');
$levelsRubricLevel2Description = new EducationItemBody();
$levelsRubricLevel2Description->setContent('');
$levelsRubricLevel2Description->setContentType(new BodyType('text'));
$levelsRubricLevel2->setDescription($levelsRubricLevel2Description);
$levelsArray []= $levelsRubricLevel2;
$requestBody->setLevels($levelsArray);

$qualitiesRubricQuality1 = new RubricQuality();
$qualitiesRubricQuality1Description = new EducationItemBody();
$qualitiesRubricQuality1Description->setContent('Argument');
$qualitiesRubricQuality1Description->setContentType(new BodyType('text'));
$qualitiesRubricQuality1->setDescription($qualitiesRubricQuality1Description);
$criteriaRubricCriterion1 = new RubricCriterion();
$criteriaRubricCriterion1Description = new EducationItemBody();
$criteriaRubricCriterion1Description->setContent('The essay\'s argument is persuasive.');
$criteriaRubricCriterion1Description->setContentType(new BodyType('text'));
$criteriaRubricCriterion1->setDescription($criteriaRubricCriterion1Description);
$criteriaArray []= $criteriaRubricCriterion1;
$criteriaRubricCriterion2 = new RubricCriterion();
$criteriaRubricCriterion2Description = new EducationItemBody();
$criteriaRubricCriterion2Description->setContent('The essay\'s argument does not make sense.');
$criteriaRubricCriterion2Description->setContentType(new BodyType('text'));
$criteriaRubricCriterion2->setDescription($criteriaRubricCriterion2Description);
$criteriaArray []= $criteriaRubricCriterion2;
$qualitiesRubricQuality1->setCriteria($criteriaArray);

$qualitiesArray []= $qualitiesRubricQuality1;
$qualitiesRubricQuality2 = new RubricQuality();
$qualitiesRubricQuality2Description = new EducationItemBody();
$qualitiesRubricQuality2Description->setContent('Spelling and Grammar');
$qualitiesRubricQuality2Description->setContentType(new BodyType('text'));
$qualitiesRubricQuality2->setDescription($qualitiesRubricQuality2Description);
$criteriaRubricCriterion1 = new RubricCriterion();
$criteriaRubricCriterion1Description = new EducationItemBody();
$criteriaRubricCriterion1Description->setContent('The essay uses proper spelling and grammar with few or no errors.');
$criteriaRubricCriterion1Description->setContentType(new BodyType('text'));
$criteriaRubricCriterion1->setDescription($criteriaRubricCriterion1Description);
$criteriaArray []= $criteriaRubricCriterion1;
$criteriaRubricCriterion2 = new RubricCriterion();
$criteriaRubricCriterion2Description = new EducationItemBody();
$criteriaRubricCriterion2Description->setContent('The essay has numerous errors in spelling and/or grammar.');
$criteriaRubricCriterion2Description->setContentType(new BodyType('text'));
$criteriaRubricCriterion2->setDescription($criteriaRubricCriterion2Description);
$criteriaArray []= $criteriaRubricCriterion2;
$qualitiesRubricQuality2->setCriteria($criteriaArray);

$qualitiesArray []= $qualitiesRubricQuality2;
$requestBody->setQualities($qualitiesArray);


$result = $graphServiceClient->education()->me()->rubrics()->post($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Education

$params = @{
	displayName = "Example Credit Rubric"
	description = @{
		content = "This is an example of a credit rubric (no points)"
		contentType = "text"
	}
	levels = @(
		@{
			displayName = "Good"
			description = @{
				content = ""
				contentType = "text"
			}
		}
		@{
			displayName = "Poor"
			description = @{
				content = ""
				contentType = "text"
			}
		}
	)
	qualities = @(
		@{
			description = @{
				content = "Argument"
				contentType = "text"
			}
			criteria = @(
				@{
					description = @{
						content = "The essay's argument is persuasive."
						contentType = "text"
					}
				}
				@{
					description = @{
						content = "The essay's argument does not make sense."
						contentType = "text"
					}
				}
			)
		}
		@{
			description = @{
				content = "Spelling and Grammar"
				contentType = "text"
			}
			criteria = @(
				@{
					description = @{
						content = "The essay uses proper spelling and grammar with few or no errors."
						contentType = "text"
					}
				}
				@{
					description = @{
						content = "The essay has numerous errors in spelling and/or grammar."
						contentType = "text"
					}
				}
			)
		}
	)
}

New-MgEducationMeRubric -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.education_rubric import EducationRubric
from msgraph.generated.models.education_item_body import EducationItemBody
from msgraph.generated.models.body_type import BodyType
from msgraph.generated.models.rubric_level import RubricLevel
from msgraph.generated.models.rubric_quality import RubricQuality
from msgraph.generated.models.rubric_criterion import RubricCriterion
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = EducationRubric(
	display_name = "Example Credit Rubric",
	description = EducationItemBody(
		content = "This is an example of a credit rubric (no points)",
		content_type = BodyType.Text,
	),
	levels = [
		RubricLevel(
			display_name = "Good",
			description = EducationItemBody(
				content = "",
				content_type = BodyType.Text,
			),
		),
		RubricLevel(
			display_name = "Poor",
			description = EducationItemBody(
				content = "",
				content_type = BodyType.Text,
			),
		),
	],
	qualities = [
		RubricQuality(
			description = EducationItemBody(
				content = "Argument",
				content_type = BodyType.Text,
			),
			criteria = [
				RubricCriterion(
					description = EducationItemBody(
						content = "The essay's argument is persuasive.",
						content_type = BodyType.Text,
					),
				),
				RubricCriterion(
					description = EducationItemBody(
						content = "The essay's argument does not make sense.",
						content_type = BodyType.Text,
					),
				),
			],
		),
		RubricQuality(
			description = EducationItemBody(
				content = "Spelling and Grammar",
				content_type = BodyType.Text,
			),
			criteria = [
				RubricCriterion(
					description = EducationItemBody(
						content = "The essay uses proper spelling and grammar with few or no errors.",
						content_type = BodyType.Text,
					),
				),
				RubricCriterion(
					description = EducationItemBody(
						content = "The essay has numerous errors in spelling and/or grammar.",
						content_type = BodyType.Text,
					),
				),
			],
		),
	],
)

result = await graph_client.education.me.rubrics.post(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 201 Created
Content-type: application/json

{
    "displayName": "Example Credit Rubric",
    "id": "63618139-2e8d-4f56-a762-dd734736816f",
    "description": {
        "content": "This is an example of a credit rubric (no points)",
        "contentType": "text"
    },
    "qualities": [
        {
            "qualityId": "461e866a-4844-4a3f-9a3c-e5464a32acf1",
            "description": {
                "content": "Argument",
                "contentType": "text"
            },
            "criteria": [
                {
                    "description": {
                        "content": "The essay's argument is persuasive.",
                        "contentType": "text"
                    }
                },
                {
                    "description": {
                        "content": "The essay's argument does not make sense.",
                        "contentType": "text"
                    }
                }
            ]
        },
        {
            "qualityId": "ccb47c1c-1a01-4027-93d7-f14b9fe86fdd",
            "description": {
                "content": "Spelling and Grammar",
                "contentType": "text"
            },
            "criteria": [
                {
                    "description": {
                        "content": "The essay uses proper spelling and grammar with few or no errors.",
                        "contentType": "text"
                    }
                },
                {
                    "description": {
                        "content": "The essay has numerous errors in spelling and/or grammar.",
                        "contentType": "text"
                    }
                }
            ]
        }
    ],
    "levels": [
        {
            "levelId": "564e68f6-984b-4574-bea7-ffae3c92633f",
            "displayName": "Good",
            "description": {
                "content": "",
                "contentType": "text"
            }
        },
        {
            "levelId": "3f082e35-46e3-4944-baea-ea6c7e36ef37",
            "displayName": "Poor",
            "description": {
                "content": "",
                "contentType": "text"
            }
        }
    ]
}
```

### Example 2: Post a points rubric

The following example shows a request to post a rubric with points.

- [HTTP](#tabpanel_2_http)
- [C#](#tabpanel_2_csharp)
- [Go](#tabpanel_2_go)
- [Java](#tabpanel_2_java)
- [JavaScript](#tabpanel_2_javascript)
- [PHP](#tabpanel_2_php)
- [PowerShell](#tabpanel_2_powershell)
- [Python](#tabpanel_2_python)

```http
POST https://graph.microsoft.com/v1.0/education/me/rubrics
Content-type: application/json

{
    "displayName":"Example Points Rubric",
    "description":{
        "content":"This is an example of a rubric with points",
        "contentType":"text"
    },
    "levels":[
        {
            "displayName":"Good",
            "description":{
                "content":"",
                "contentType":"text"
            },
            "grading":{
                "@odata.type":"#microsoft.graph.educationAssignmentPointsGradeType",
                "maxPoints":2
            }
        },
        {
            "displayName":"Poor",
            "description":{
                "content":"",
                "contentType":"text"
            },
            "grading":{
                "@odata.type":"#microsoft.graph.educationAssignmentPointsGradeType",
                "maxPoints":1
            }
        }
    ],
    "qualities":[
        {
            "description":{
                "content":"Argument",
                "contentType":"text"
            },
            "criteria":[
                {
                    "description":{
                        "content":"The essay's argument is persuasive.",
                        "contentType":"text"
                    }
                },
                {
                    "description":{
                        "content":"The essay's argument does not make sense.",
                        "contentType":"text"
                    }
                }
            ],
            "weight":50.0
        },
        {
            "description":{
                "content":"Spelling and Grammar",
                "contentType":"text"
            },
            "criteria":[
                {
                    "description":{
                        "content":"The essay uses proper spelling and grammar with few or no errors.",
                        "contentType":"text"
                    }
                },
                {
                    "description":{
                        "content":"The essay has numerous errors in spelling and/or grammar.",
                        "contentType":"text"
                    }
                }
            ],
            "weight":50.0
        }
    ],
    "grading":{
        "@odata.type":"#microsoft.graph.educationAssignmentPointsGradeType"
    }
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models;

var requestBody = new EducationRubric
{
	DisplayName = "Example Points Rubric",
	Description = new EducationItemBody
	{
		Content = "This is an example of a rubric with points",
		ContentType = BodyType.Text,
	},
	Levels = new List<RubricLevel>
	{
		new RubricLevel
		{
			DisplayName = "Good",
			Description = new EducationItemBody
			{
				Content = "",
				ContentType = BodyType.Text,
			},
			Grading = new EducationAssignmentPointsGradeType
			{
				OdataType = "#microsoft.graph.educationAssignmentPointsGradeType",
				MaxPoints = 2f,
			},
		},
		new RubricLevel
		{
			DisplayName = "Poor",
			Description = new EducationItemBody
			{
				Content = "",
				ContentType = BodyType.Text,
			},
			Grading = new EducationAssignmentPointsGradeType
			{
				OdataType = "#microsoft.graph.educationAssignmentPointsGradeType",
				MaxPoints = 1f,
			},
		},
	},
	Qualities = new List<RubricQuality>
	{
		new RubricQuality
		{
			Description = new EducationItemBody
			{
				Content = "Argument",
				ContentType = BodyType.Text,
			},
			Criteria = new List<RubricCriterion>
			{
				new RubricCriterion
				{
					Description = new EducationItemBody
					{
						Content = "The essay's argument is persuasive.",
						ContentType = BodyType.Text,
					},
				},
				new RubricCriterion
				{
					Description = new EducationItemBody
					{
						Content = "The essay's argument does not make sense.",
						ContentType = BodyType.Text,
					},
				},
			},
			Weight = 50.0f,
		},
		new RubricQuality
		{
			Description = new EducationItemBody
			{
				Content = "Spelling and Grammar",
				ContentType = BodyType.Text,
			},
			Criteria = new List<RubricCriterion>
			{
				new RubricCriterion
				{
					Description = new EducationItemBody
					{
						Content = "The essay uses proper spelling and grammar with few or no errors.",
						ContentType = BodyType.Text,
					},
				},
				new RubricCriterion
				{
					Description = new EducationItemBody
					{
						Content = "The essay has numerous errors in spelling and/or grammar.",
						ContentType = BodyType.Text,
					},
				},
			},
			Weight = 50.0f,
		},
	},
	Grading = new EducationAssignmentPointsGradeType
	{
		OdataType = "#microsoft.graph.educationAssignmentPointsGradeType",
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Education.Me.Rubrics.PostAsync(requestBody);
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

requestBody := graphmodels.NewEducationRubric()
displayName := "Example Points Rubric"
requestBody.SetDisplayName(&displayName) 
description := graphmodels.NewEducationItemBody()
content := "This is an example of a rubric with points"
description.SetContent(&content) 
contentType := graphmodels.TEXT_BODYTYPE 
description.SetContentType(&contentType) 
requestBody.SetDescription(description)


rubricLevel := graphmodels.NewRubricLevel()
displayName := "Good"
rubricLevel.SetDisplayName(&displayName) 
description := graphmodels.NewEducationItemBody()
content := ""
description.SetContent(&content) 
contentType := graphmodels.TEXT_BODYTYPE 
description.SetContentType(&contentType) 
rubricLevel.SetDescription(description)
grading := graphmodels.NewEducationAssignmentPointsGradeType()
maxPoints := float32(2)
grading.SetMaxPoints(&maxPoints) 
rubricLevel.SetGrading(grading)
rubricLevel1 := graphmodels.NewRubricLevel()
displayName := "Poor"
rubricLevel1.SetDisplayName(&displayName) 
description := graphmodels.NewEducationItemBody()
content := ""
description.SetContent(&content) 
contentType := graphmodels.TEXT_BODYTYPE 
description.SetContentType(&contentType) 
rubricLevel1.SetDescription(description)
grading := graphmodels.NewEducationAssignmentPointsGradeType()
maxPoints := float32(1)
grading.SetMaxPoints(&maxPoints) 
rubricLevel1.SetGrading(grading)

levels := []graphmodels.RubricLevelable {
	rubricLevel,
	rubricLevel1,
}
requestBody.SetLevels(levels)


rubricQuality := graphmodels.NewRubricQuality()
description := graphmodels.NewEducationItemBody()
content := "Argument"
description.SetContent(&content) 
contentType := graphmodels.TEXT_BODYTYPE 
description.SetContentType(&contentType) 
rubricQuality.SetDescription(description)


rubricCriterion := graphmodels.NewRubricCriterion()
description := graphmodels.NewEducationItemBody()
content := "The essay's argument is persuasive."
description.SetContent(&content) 
contentType := graphmodels.TEXT_BODYTYPE 
description.SetContentType(&contentType) 
rubricCriterion.SetDescription(description)
rubricCriterion1 := graphmodels.NewRubricCriterion()
description := graphmodels.NewEducationItemBody()
content := "The essay's argument does not make sense."
description.SetContent(&content) 
contentType := graphmodels.TEXT_BODYTYPE 
description.SetContentType(&contentType) 
rubricCriterion1.SetDescription(description)

criteria := []graphmodels.RubricCriterionable {
	rubricCriterion,
	rubricCriterion1,
}
rubricQuality.SetCriteria(criteria)
weight := float32(50.0)
rubricQuality.SetWeight(&weight) 
rubricQuality1 := graphmodels.NewRubricQuality()
description := graphmodels.NewEducationItemBody()
content := "Spelling and Grammar"
description.SetContent(&content) 
contentType := graphmodels.TEXT_BODYTYPE 
description.SetContentType(&contentType) 
rubricQuality1.SetDescription(description)


rubricCriterion := graphmodels.NewRubricCriterion()
description := graphmodels.NewEducationItemBody()
content := "The essay uses proper spelling and grammar with few or no errors."
description.SetContent(&content) 
contentType := graphmodels.TEXT_BODYTYPE 
description.SetContentType(&contentType) 
rubricCriterion.SetDescription(description)
rubricCriterion1 := graphmodels.NewRubricCriterion()
description := graphmodels.NewEducationItemBody()
content := "The essay has numerous errors in spelling and/or grammar."
description.SetContent(&content) 
contentType := graphmodels.TEXT_BODYTYPE 
description.SetContentType(&contentType) 
rubricCriterion1.SetDescription(description)

criteria := []graphmodels.RubricCriterionable {
	rubricCriterion,
	rubricCriterion1,
}
rubricQuality1.SetCriteria(criteria)
weight := float32(50.0)
rubricQuality1.SetWeight(&weight) 

qualities := []graphmodels.RubricQualityable {
	rubricQuality,
	rubricQuality1,
}
requestBody.SetQualities(qualities)
grading := graphmodels.NewEducationAssignmentPointsGradeType()
requestBody.SetGrading(grading)

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=go
rubrics, err := graphClient.Education().Me().Rubrics().Post(context.Background(), requestBody, nil)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

EducationRubric educationRubric = new EducationRubric();
educationRubric.setDisplayName("Example Points Rubric");
EducationItemBody description = new EducationItemBody();
description.setContent("This is an example of a rubric with points");
description.setContentType(BodyType.Text);
educationRubric.setDescription(description);
LinkedList<RubricLevel> levels = new LinkedList<RubricLevel>();
RubricLevel rubricLevel = new RubricLevel();
rubricLevel.setDisplayName("Good");
EducationItemBody description1 = new EducationItemBody();
description1.setContent("");
description1.setContentType(BodyType.Text);
rubricLevel.setDescription(description1);
EducationAssignmentPointsGradeType grading = new EducationAssignmentPointsGradeType();
grading.setOdataType("#microsoft.graph.educationAssignmentPointsGradeType");
grading.setMaxPoints(2f);
rubricLevel.setGrading(grading);
levels.add(rubricLevel);
RubricLevel rubricLevel1 = new RubricLevel();
rubricLevel1.setDisplayName("Poor");
EducationItemBody description2 = new EducationItemBody();
description2.setContent("");
description2.setContentType(BodyType.Text);
rubricLevel1.setDescription(description2);
EducationAssignmentPointsGradeType grading1 = new EducationAssignmentPointsGradeType();
grading1.setOdataType("#microsoft.graph.educationAssignmentPointsGradeType");
grading1.setMaxPoints(1f);
rubricLevel1.setGrading(grading1);
levels.add(rubricLevel1);
educationRubric.setLevels(levels);
LinkedList<RubricQuality> qualities = new LinkedList<RubricQuality>();
RubricQuality rubricQuality = new RubricQuality();
EducationItemBody description3 = new EducationItemBody();
description3.setContent("Argument");
description3.setContentType(BodyType.Text);
rubricQuality.setDescription(description3);
LinkedList<RubricCriterion> criteria = new LinkedList<RubricCriterion>();
RubricCriterion rubricCriterion = new RubricCriterion();
EducationItemBody description4 = new EducationItemBody();
description4.setContent("The essay's argument is persuasive.");
description4.setContentType(BodyType.Text);
rubricCriterion.setDescription(description4);
criteria.add(rubricCriterion);
RubricCriterion rubricCriterion1 = new RubricCriterion();
EducationItemBody description5 = new EducationItemBody();
description5.setContent("The essay's argument does not make sense.");
description5.setContentType(BodyType.Text);
rubricCriterion1.setDescription(description5);
criteria.add(rubricCriterion1);
rubricQuality.setCriteria(criteria);
rubricQuality.setWeight(50.0f);
qualities.add(rubricQuality);
RubricQuality rubricQuality1 = new RubricQuality();
EducationItemBody description6 = new EducationItemBody();
description6.setContent("Spelling and Grammar");
description6.setContentType(BodyType.Text);
rubricQuality1.setDescription(description6);
LinkedList<RubricCriterion> criteria1 = new LinkedList<RubricCriterion>();
RubricCriterion rubricCriterion2 = new RubricCriterion();
EducationItemBody description7 = new EducationItemBody();
description7.setContent("The essay uses proper spelling and grammar with few or no errors.");
description7.setContentType(BodyType.Text);
rubricCriterion2.setDescription(description7);
criteria1.add(rubricCriterion2);
RubricCriterion rubricCriterion3 = new RubricCriterion();
EducationItemBody description8 = new EducationItemBody();
description8.setContent("The essay has numerous errors in spelling and/or grammar.");
description8.setContentType(BodyType.Text);
rubricCriterion3.setDescription(description8);
criteria1.add(rubricCriterion3);
rubricQuality1.setCriteria(criteria1);
rubricQuality1.setWeight(50.0f);
qualities.add(rubricQuality1);
educationRubric.setQualities(qualities);
EducationAssignmentPointsGradeType grading2 = new EducationAssignmentPointsGradeType();
grading2.setOdataType("#microsoft.graph.educationAssignmentPointsGradeType");
educationRubric.setGrading(grading2);
EducationRubric result = graphClient.education().me().rubrics().post(educationRubric);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const educationRubric = {
    displayName: 'Example Points Rubric',
    description: {
        content: 'This is an example of a rubric with points',
        contentType: 'text'
    },
    levels: [
        {
            displayName: 'Good',
            description: {
                content: '',
                contentType: 'text'
            },
            grading: {
                '@odata.type':'#microsoft.graph.educationAssignmentPointsGradeType',
                maxPoints: 2
            }
        },
        {
            displayName: 'Poor',
            description: {
                content: '',
                contentType: 'text'
            },
            grading: {
                '@odata.type':'#microsoft.graph.educationAssignmentPointsGradeType',
                maxPoints: 1
            }
        }
    ],
    qualities: [
        {
            description: {
                content: 'Argument',
                contentType: 'text'
            },
            criteria: [
                {
                    description: {
                        content: 'The essay\'s argument is persuasive.',
                        contentType: 'text'
                    }
                },
                {
                    description: {
                        content: 'The essay\'s argument does not make sense.',
                        contentType: 'text'
                    }
                }
            ],
            weight: 50.0
        },
        {
            description: {
                content: 'Spelling and Grammar',
                contentType: 'text'
            },
            criteria: [
                {
                    description: {
                        content: 'The essay uses proper spelling and grammar with few or no errors.',
                        contentType: 'text'
                    }
                },
                {
                    description: {
                        content: 'The essay has numerous errors in spelling and/or grammar.',
                        contentType: 'text'
                    }
                }
            ],
            weight: 50.0
        }
    ],
    grading: {
        '@odata.type':'#microsoft.graph.educationAssignmentPointsGradeType'
    }
};

await client.api('/education/me/rubrics')
	.post(educationRubric);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\EducationRubric;
use Microsoft\Graph\Generated\Models\EducationItemBody;
use Microsoft\Graph\Generated\Models\BodyType;
use Microsoft\Graph\Generated\Models\RubricLevel;
use Microsoft\Graph\Generated\Models\EducationAssignmentPointsGradeType;
use Microsoft\Graph\Generated\Models\RubricQuality;
use Microsoft\Graph\Generated\Models\RubricCriterion;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new EducationRubric();
$requestBody->setDisplayName('Example Points Rubric');
$description = new EducationItemBody();
$description->setContent('This is an example of a rubric with points');
$description->setContentType(new BodyType('text'));
$requestBody->setDescription($description);
$levelsRubricLevel1 = new RubricLevel();
$levelsRubricLevel1->setDisplayName('Good');
$levelsRubricLevel1Description = new EducationItemBody();
$levelsRubricLevel1Description->setContent('');
$levelsRubricLevel1Description->setContentType(new BodyType('text'));
$levelsRubricLevel1->setDescription($levelsRubricLevel1Description);
$levelsRubricLevel1Grading = new EducationAssignmentPointsGradeType();
$levelsRubricLevel1Grading->setOdataType('#microsoft.graph.educationAssignmentPointsGradeType');
$levelsRubricLevel1Grading->setMaxPoints(2);
$levelsRubricLevel1->setGrading($levelsRubricLevel1Grading);
$levelsArray []= $levelsRubricLevel1;
$levelsRubricLevel2 = new RubricLevel();
$levelsRubricLevel2->setDisplayName('Poor');
$levelsRubricLevel2Description = new EducationItemBody();
$levelsRubricLevel2Description->setContent('');
$levelsRubricLevel2Description->setContentType(new BodyType('text'));
$levelsRubricLevel2->setDescription($levelsRubricLevel2Description);
$levelsRubricLevel2Grading = new EducationAssignmentPointsGradeType();
$levelsRubricLevel2Grading->setOdataType('#microsoft.graph.educationAssignmentPointsGradeType');
$levelsRubricLevel2Grading->setMaxPoints(1);
$levelsRubricLevel2->setGrading($levelsRubricLevel2Grading);
$levelsArray []= $levelsRubricLevel2;
$requestBody->setLevels($levelsArray);

$qualitiesRubricQuality1 = new RubricQuality();
$qualitiesRubricQuality1Description = new EducationItemBody();
$qualitiesRubricQuality1Description->setContent('Argument');
$qualitiesRubricQuality1Description->setContentType(new BodyType('text'));
$qualitiesRubricQuality1->setDescription($qualitiesRubricQuality1Description);
$criteriaRubricCriterion1 = new RubricCriterion();
$criteriaRubricCriterion1Description = new EducationItemBody();
$criteriaRubricCriterion1Description->setContent('The essay\'s argument is persuasive.');
$criteriaRubricCriterion1Description->setContentType(new BodyType('text'));
$criteriaRubricCriterion1->setDescription($criteriaRubricCriterion1Description);
$criteriaArray []= $criteriaRubricCriterion1;
$criteriaRubricCriterion2 = new RubricCriterion();
$criteriaRubricCriterion2Description = new EducationItemBody();
$criteriaRubricCriterion2Description->setContent('The essay\'s argument does not make sense.');
$criteriaRubricCriterion2Description->setContentType(new BodyType('text'));
$criteriaRubricCriterion2->setDescription($criteriaRubricCriterion2Description);
$criteriaArray []= $criteriaRubricCriterion2;
$qualitiesRubricQuality1->setCriteria($criteriaArray);

$qualitiesRubricQuality1->setWeight(50.0);
$qualitiesArray []= $qualitiesRubricQuality1;
$qualitiesRubricQuality2 = new RubricQuality();
$qualitiesRubricQuality2Description = new EducationItemBody();
$qualitiesRubricQuality2Description->setContent('Spelling and Grammar');
$qualitiesRubricQuality2Description->setContentType(new BodyType('text'));
$qualitiesRubricQuality2->setDescription($qualitiesRubricQuality2Description);
$criteriaRubricCriterion1 = new RubricCriterion();
$criteriaRubricCriterion1Description = new EducationItemBody();
$criteriaRubricCriterion1Description->setContent('The essay uses proper spelling and grammar with few or no errors.');
$criteriaRubricCriterion1Description->setContentType(new BodyType('text'));
$criteriaRubricCriterion1->setDescription($criteriaRubricCriterion1Description);
$criteriaArray []= $criteriaRubricCriterion1;
$criteriaRubricCriterion2 = new RubricCriterion();
$criteriaRubricCriterion2Description = new EducationItemBody();
$criteriaRubricCriterion2Description->setContent('The essay has numerous errors in spelling and/or grammar.');
$criteriaRubricCriterion2Description->setContentType(new BodyType('text'));
$criteriaRubricCriterion2->setDescription($criteriaRubricCriterion2Description);
$criteriaArray []= $criteriaRubricCriterion2;
$qualitiesRubricQuality2->setCriteria($criteriaArray);

$qualitiesRubricQuality2->setWeight(50.0);
$qualitiesArray []= $qualitiesRubricQuality2;
$requestBody->setQualities($qualitiesArray);

$grading = new EducationAssignmentPointsGradeType();
$grading->setOdataType('#microsoft.graph.educationAssignmentPointsGradeType');
$requestBody->setGrading($grading);

$result = $graphServiceClient->education()->me()->rubrics()->post($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```
Snippet not available
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.education_rubric import EducationRubric
from msgraph.generated.models.education_item_body import EducationItemBody
from msgraph.generated.models.body_type import BodyType
from msgraph.generated.models.rubric_level import RubricLevel
from msgraph.generated.models.education_assignment_points_grade_type import EducationAssignmentPointsGradeType
from msgraph.generated.models.rubric_quality import RubricQuality
from msgraph.generated.models.rubric_criterion import RubricCriterion
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = EducationRubric(
	display_name = "Example Points Rubric",
	description = EducationItemBody(
		content = "This is an example of a rubric with points",
		content_type = BodyType.Text,
	),
	levels = [
		RubricLevel(
			display_name = "Good",
			description = EducationItemBody(
				content = "",
				content_type = BodyType.Text,
			),
			grading = EducationAssignmentPointsGradeType(
				odata_type = "#microsoft.graph.educationAssignmentPointsGradeType",
				max_points = 2,
			),
		),
		RubricLevel(
			display_name = "Poor",
			description = EducationItemBody(
				content = "",
				content_type = BodyType.Text,
			),
			grading = EducationAssignmentPointsGradeType(
				odata_type = "#microsoft.graph.educationAssignmentPointsGradeType",
				max_points = 1,
			),
		),
	],
	qualities = [
		RubricQuality(
			description = EducationItemBody(
				content = "Argument",
				content_type = BodyType.Text,
			),
			criteria = [
				RubricCriterion(
					description = EducationItemBody(
						content = "The essay's argument is persuasive.",
						content_type = BodyType.Text,
					),
				),
				RubricCriterion(
					description = EducationItemBody(
						content = "The essay's argument does not make sense.",
						content_type = BodyType.Text,
					),
				),
			],
			weight = 50.0,
		),
		RubricQuality(
			description = EducationItemBody(
				content = "Spelling and Grammar",
				content_type = BodyType.Text,
			),
			criteria = [
				RubricCriterion(
					description = EducationItemBody(
						content = "The essay uses proper spelling and grammar with few or no errors.",
						content_type = BodyType.Text,
					),
				),
				RubricCriterion(
					description = EducationItemBody(
						content = "The essay has numerous errors in spelling and/or grammar.",
						content_type = BodyType.Text,
					),
				),
			],
			weight = 50.0,
		),
	],
	grading = EducationAssignmentPointsGradeType(
		odata_type = "#microsoft.graph.educationAssignmentPointsGradeType",
	),
)

result = await graph_client.education.me.rubrics.post(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

#### Response

The following example shows the response.

> **Note:** The response object shown here might be shortened for readability.

```http
HTTP/1.1 201 Created
Content-type: application/json

{
    "displayName": "Example Points Rubric",
    "id": "bf040af7-a5ff-4abe-a8c8-1bdc532344c2",
    "description": {
        "content": "This is an example of a rubric with points",
        "contentType": "text"
    },
    "levels": [
        {
            "levelId": "519cd134-c513-40b9-aa71-fdb0d063c084",
            "displayName": "Good",
            "description": {
                "content": "",
                "contentType": "text"
            },
            "grading": {
                "@odata.type": "#microsoft.graph.educationAssignmentPointsGradeType",
                "maxPoints": 2
            }
        },
        {
            "levelId": "db2a0c91-abef-44cb-b8b1-ef1f85ef4a77",
            "displayName": "Poor",
            "description": {
                "content": "",
                "contentType": "text"
            },
            "grading": {
                "@odata.type": "#microsoft.graph.educationAssignmentPointsGradeType",
                "maxPoints": 1
            }
        }
    ],
    "qualities": [
        {
            "qualityId": "bbf3fb4a-a794-4b51-a1ad-c22fb891c5d8",
            "weight": 50.0,
            "description": {
                "content": "Argument",
                "contentType": "text"
            },
            "criteria": [
                {
                    "id": "5e637d79-f26b-4ea6-acd7-73824f0c0967",
                    "description": {
                        "content": "The essay's argument is persuasive.",
                        "contentType": "text"
                    }
                },
                {
                    "id": "ebdcc27f-d1ec-4aa3-9da7-bd8d7842e3d3",
                    "description": {
                        "content": "The essay's argument does not make sense.",
                        "contentType": "text"
                    }
                }
            ]
        },
        {
            "qualityId": "ebe97fd7-47f7-4e9a-b31b-221ad731fc5a",
            "weight": 50.0,
            "description": {
                "content": "Spelling and Grammar",
                "contentType": "text"
            },
            "criteria": [
                {
                    "id": "5417252a-f810-41eb-9a83-09276a258a08",
                    "description": {
                        "content": "The essay uses proper spelling and grammar with few or no errors.",
                        "contentType": "text"
                    }
                },
                {
                    "id": "5de220bd-74b9-41a7-85d5-9be7c6cb7933",
                    "description": {
                        "content": "The essay has numerous errors in spelling and/or grammar.",
                        "contentType": "text"
                    }
                }
            ]
        }
    ],
    "grading": {
        "@odata.type": "#microsoft.graph.educationAssignmentPointsGradeType",
        "maxPoints": 100
    }
}
```
