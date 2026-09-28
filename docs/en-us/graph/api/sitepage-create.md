<!-- Source: https://learn.microsoft.com/en-us/graph/api/sitepage-create?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2025-07-23 -->

# Create a page in the site pages list of a site

Namespace: microsoft.graph

Create a new [sitePage](https://learn.microsoft.com/en-us/graph/api/resources/sitepage?view=graph-rest-1.0) in the site pages [list](https://learn.microsoft.com/en-us/graph/api/resources/list?view=graph-rest-1.0) in a [site](https://learn.microsoft.com/en-us/graph/api/resources/site?view=graph-rest-1.0).

This API is available in the following [national cloud deployments](https://learn.microsoft.com/en-us/graph/deployments).

| Global service | US Government L4 | US Government L5 \(DOD\) | China operated by 21Vianet |
| --- | --- | --- | --- |
| ✅ | ✅ | ✅ | ✅ |

## Permissions

Choose the permission or permissions marked as least privileged for this API. Use a higher privileged permission or permissions [only if your app requires it](https://learn.microsoft.com/en-us/graph/permissions-overview#best-practices-for-using-microsoft-graph-permissions). For details about delegated and application permissions, see [Permission types](https://learn.microsoft.com/en-us/graph/permissions-overview#permission-types). To learn more about these permissions, see the [permissions reference](https://learn.microsoft.com/en-us/graph/permissions-reference).

| Permission type | Least privileged permissions | Higher privileged permissions |
| :--- | :--- | :--- |
| Delegated \(work or school account\) | Sites.ReadWrite.All | Not available. |
| Delegated \(personal Microsoft account\) | Not supported. | Not supported. |
| Application | Sites.ReadWrite.All | Not available. |

## HTTP request

```http
POST /sites/{site-id}/pages
```

## Request headers

| Name | Description |
| :--- | :--- |
| Authorization | Bearer {token}. Required. Learn more about [authentication and authorization](https://learn.microsoft.com/en-us/graph/auth/auth-concepts). |
| Content-Type | application/json. Required. |

## Request body

In the request body, supply a JSON representation of the [sitePage](https://learn.microsoft.com/en-us/graph/api/resources/sitepage?view=graph-rest-1.0) resource to create.

> **Notes:** :
> 
> 1. To ensure successful parsing of the request body, the `@odata.type=#microsoft.graph.sitePage` must be included in the request body.
> 2. If you're using the response from the [Get sitepage](https://learn.microsoft.com/en-us/graph/api/sitepage-get?view=graph-rest-1.0) operation to create a **sitePage**, we recommend that you add the HTTP header `Accept: application/json;odata.metadata=none`. This will remove all OData metadata from the response. You can also manually remove all OData metadata.
> 3. Only the web part listed in the [Supported web parts](#supported-web-parts) section are supported when creating a [sitePage](https://learn.microsoft.com/en-us/graph/api/resources/sitepage?view=graph-rest-1.0) using the Microsoft Graph API. Attempting to add unsupported web parts will result in a failure or exception.

### Supported web parts

There are two kinds of web parts that can be added to a [sitePage](https://learn.microsoft.com/en-us/graph/api/resources/sitepage?view=graph-rest-1.0): [standardWebParts](https://learn.microsoft.com/en-us/graph/api/resources/standardwebpart?view=graph-rest-1.0) and [textWebPart](https://learn.microsoft.com/en-us/graph/api/resources/textwebpart?view=graph-rest-1.0). The following table lists the supported web parts for standard web parts.

| # | Web Part | Type |
| --- | --- | --- |
| 1 | Bing Maps | `e377ea37-9047-43b9-8cdb-a761be2f8e09` |
| 2 | Button | `0f087d7f-520e-42b7-89c0-496aaf979d58` |
| 3 | Call To Action | `df8e44e7-edd5-46d5-90da-aca1539313b8` |
| 4 | Divider | `2161a1c6-db61-4731-b97c-3cdb303f7cbb` |
| 5 | Document Embed | `b7dd04e1-19ce-4b24-9132-b60a1c2b910d` |
| 6 | Image | `d1d91016-032f-456d-98a4-721247c305e8` |
| 7 | Image Gallery | `af8be689-990e-492a-81f7-ba3e4cd3ed9c` |
| 8 | Link Preview | `6410b3b6-d440-4663-8744-378976dc041e` |
| 9 | Org Chart | `e84a8ca2-f63c-4fb9-bc0b-d8eef5ccb22b` |
| 10 | People | `7f718435-ee4d-431c-bdbf-9c4ff326f46e` |
| 11 | Quick Links | `c70391ea-0b10-4ee9-b2b4-006d3fcad0cd` |
| 12 | Spacer | `8654b779-4886-46d4-8ffb-b5ed960ee986` |
| 13 | Youtube Embed | `544dd15b-cf3c-441b-96da-004d5a8cea1d` |
| 14 | Title Area | `cbe7b0a9-3504-44dd-a3a3-0e5cacd07788` |

## Response

If successful, this method returns a `201` and the created [sitePage](https://learn.microsoft.com/en-us/graph/api/resources/basesitepage?view=graph-rest-1.0) object.

## Example

The following example shows how to create a new page.

### Request

- [HTTP](#tabpanel_1_http)
- [C#](#tabpanel_1_csharp)
- [Java](#tabpanel_1_java)
- [JavaScript](#tabpanel_1_javascript)
- [PHP](#tabpanel_1_php)
- [PowerShell](#tabpanel_1_powershell)
- [Python](#tabpanel_1_python)

```http
POST /sites/{site-id}/pages
Content-Type: application/json

{
  "@odata.type": "#microsoft.graph.sitePage",
  "name": "test.aspx",
  "title": "test",
  "pageLayout": "article",
  "showComments": true,
  "showRecommendedPages": false,
  "titleArea": {
    "enableGradientEffect": true,
    "imageWebUrl": "https://cdn.hubblecontent.osi.office.net/m365content/publish/005292d6-9dcc-4fc5-b50b-b2d0383a411b/image.jpg",
    "layout": "colorBlock",
    "showAuthor": true,
    "showPublishedDate": false,
    "showTextBlockAboveTitle": false,
    "textAboveTitle": "TEXT ABOVE TITLE",
    "textAlignment": "left",
    "imageSourceType": 2,
    "title": "sample1"
  },
  "canvasLayout": {
    "horizontalSections": [
      {
        "layout": "oneThirdRightColumn",
        "id": "1",
        "emphasis": "none",
        "columns": [
          {
            "id": "1",
            "width": 8,
            "webparts": [
              {
                "id": "6f9230af-2a98-4952-b205-9ede4f9ef548",
                "innerHtml": "<p><b>Hello!</b></p>"
              }
            ]
          },
          {
            "id": "2",
            "width": 4,
            "webparts": [
              {
                "id": "73d07dde-3474-4545-badb-f28ba239e0e1",
                "webPartType": "d1d91016-032f-456d-98a4-721247c305e8",
                "data": {
                  "dataVersion": "1.9",
                  "description": "Show an image on your page",
                  "title": "Image",
                  "properties": {
                    "imageSourceType": 2,
                    "altText": "",
                    "overlayText": "",
                    "siteid": "0264cabe-6b92-450a-b162-b0c3d54fe5e8",
                    "webid": "f3989670-cd37-4514-8ccb-0f7c2cbe5314",
                    "listid": "bdb41041-eb06-474e-ac29-87093386bb14",
                    "uniqueid": "d9f94b40-78ba-48d0-a39f-3cb23c2fe7eb",
                    "imgWidth": 4288,
                    "imgHeight": 2848,
                    "fixAspectRatio": false,
                    "captionText": "",
                    "alignment": "Center"
                  },
                  "serverProcessedContent": {
                    "imageSources": [
                      {
                        "key": "imageSource",
                        "value": "/_LAYOUTS/IMAGES/VISUALTEMPLATEIMAGE1.JPG"
                      }
                    ],
                    "customMetadata": [
                      {
                        "key": "imageSource",
                        "value": {
                          "siteid": "0264cabe-6b92-450a-b162-b0c3d54fe5e8",
                          "webid": "f3989670-cd37-4514-8ccb-0f7c2cbe5314",
                          "listid": "bdb41041-eb06-474e-ac29-87093386bb14",
                          "uniqueid": "d9f94b40-78ba-48d0-a39f-3cb23c2fe7eb",
                          "width": "4288",
                          "height": "2848"
                        }
                      }
                    ]
                  }
                }
              }
            ]
          }
        ]
      }
    ]
  }
}
```

```csharp

// Code snippets are only available for the latest version. Current version is 5.x

// Dependencies
using Microsoft.Graph.Models;
using Microsoft.Kiota.Abstractions.Serialization;

var requestBody = new SitePage
{
	OdataType = "#microsoft.graph.sitePage",
	Name = "test.aspx",
	Title = "test",
	PageLayout = PageLayoutType.Article,
	ShowComments = true,
	ShowRecommendedPages = false,
	TitleArea = new TitleArea
	{
		EnableGradientEffect = true,
		ImageWebUrl = "https://cdn.hubblecontent.osi.office.net/m365content/publish/005292d6-9dcc-4fc5-b50b-b2d0383a411b/image.jpg",
		Layout = TitleAreaLayoutType.ColorBlock,
		ShowAuthor = true,
		ShowPublishedDate = false,
		ShowTextBlockAboveTitle = false,
		TextAboveTitle = "TEXT ABOVE TITLE",
		TextAlignment = TitleAreaTextAlignmentType.Left,
		AdditionalData = new Dictionary<string, object>
		{
			{
				"imageSourceType" , 2
			},
			{
				"title" , "sample1"
			},
		},
	},
	CanvasLayout = new CanvasLayout
	{
		HorizontalSections = new List<HorizontalSection>
		{
			new HorizontalSection
			{
				Layout = HorizontalSectionLayoutType.OneThirdRightColumn,
				Id = "1",
				Emphasis = SectionEmphasisType.None,
				Columns = new List<HorizontalSectionColumn>
				{
					new HorizontalSectionColumn
					{
						Id = "1",
						Width = 8,
						Webparts = new List<WebPart>
						{
							new WebPart
							{
								Id = "6f9230af-2a98-4952-b205-9ede4f9ef548",
								AdditionalData = new Dictionary<string, object>
								{
									{
										"innerHtml" , "<p><b>Hello!</b></p>"
									},
								},
							},
						},
					},
					new HorizontalSectionColumn
					{
						Id = "2",
						Width = 4,
						Webparts = new List<WebPart>
						{
							new WebPart
							{
								Id = "73d07dde-3474-4545-badb-f28ba239e0e1",
								AdditionalData = new Dictionary<string, object>
								{
									{
										"webPartType" , "d1d91016-032f-456d-98a4-721247c305e8"
									},
									{
										"data" , new UntypedObject(new Dictionary<string, UntypedNode>
										{
											{
												"dataVersion", new UntypedString("1.9")
											},
											{
												"description", new UntypedString("Show an image on your page")
											},
											{
												"title", new UntypedString("Image")
											},
											{
												"properties", new UntypedObject(new Dictionary<string, UntypedNode>
												{
													{
														"imageSourceType", new UntypedString("2")
													},
													{
														"altText", new UntypedString("")
													},
													{
														"overlayText", new UntypedString("")
													},
													{
														"siteid", new UntypedString("0264cabe-6b92-450a-b162-b0c3d54fe5e8")
													},
													{
														"webid", new UntypedString("f3989670-cd37-4514-8ccb-0f7c2cbe5314")
													},
													{
														"listid", new UntypedString("bdb41041-eb06-474e-ac29-87093386bb14")
													},
													{
														"uniqueid", new UntypedString("d9f94b40-78ba-48d0-a39f-3cb23c2fe7eb")
													},
													{
														"imgWidth", new UntypedString("4288")
													},
													{
														"imgHeight", new UntypedString("2848")
													},
													{
														"fixAspectRatio", new UntypedBoolean(false)
													},
													{
														"captionText", new UntypedString("")
													},
													{
														"alignment", new UntypedString("Center")
													},
												})
											},
											{
												"serverProcessedContent", new UntypedObject(new Dictionary<string, UntypedNode>
												{
													{
														"imageSources", new UntypedArray(new List<UntypedNode>
														{
															new UntypedObject(new Dictionary<string, UntypedNode>
															{
																{
																	"key", new UntypedString("imageSource")
																},
																{
																	"value", new UntypedString("/_LAYOUTS/IMAGES/VISUALTEMPLATEIMAGE1.JPG")
																},
															}),
														})
													},
													{
														"customMetadata", new UntypedArray(new List<UntypedNode>
														{
															new UntypedObject(new Dictionary<string, UntypedNode>
															{
																{
																	"key", new UntypedString("imageSource")
																},
																{
																	"value", new UntypedObject(new Dictionary<string, UntypedNode>
																	{
																		{
																			"siteid", new UntypedString("0264cabe-6b92-450a-b162-b0c3d54fe5e8")
																		},
																		{
																			"webid", new UntypedString("f3989670-cd37-4514-8ccb-0f7c2cbe5314")
																		},
																		{
																			"listid", new UntypedString("bdb41041-eb06-474e-ac29-87093386bb14")
																		},
																		{
																			"uniqueid", new UntypedString("d9f94b40-78ba-48d0-a39f-3cb23c2fe7eb")
																		},
																		{
																			"width", new UntypedString("4288")
																		},
																		{
																			"height", new UntypedString("2848")
																		},
																	})
																},
															}),
														})
													},
												})
											},
										})
									},
								},
							},
						},
					},
				},
			},
		},
	},
};

// To initialize your graphClient, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=csharp
var result = await graphClient.Sites["{site-id}"].Pages.PostAsync(requestBody);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```java

// Code snippets are only available for the latest version. Current version is 6.x

GraphServiceClient graphClient = new GraphServiceClient(requestAdapter);

SitePage baseSitePage = new SitePage();
baseSitePage.setOdataType("#microsoft.graph.sitePage");
baseSitePage.setName("test.aspx");
baseSitePage.setTitle("test");
baseSitePage.setPageLayout(PageLayoutType.Article);
baseSitePage.setShowComments(true);
baseSitePage.setShowRecommendedPages(false);
TitleArea titleArea = new TitleArea();
titleArea.setEnableGradientEffect(true);
titleArea.setImageWebUrl("https://cdn.hubblecontent.osi.office.net/m365content/publish/005292d6-9dcc-4fc5-b50b-b2d0383a411b/image.jpg");
titleArea.setLayout(TitleAreaLayoutType.ColorBlock);
titleArea.setShowAuthor(true);
titleArea.setShowPublishedDate(false);
titleArea.setShowTextBlockAboveTitle(false);
titleArea.setTextAboveTitle("TEXT ABOVE TITLE");
titleArea.setTextAlignment(TitleAreaTextAlignmentType.Left);
HashMap<String, Object> additionalData = new HashMap<String, Object>();
additionalData.put("imageSourceType", 2);
additionalData.put("title", "sample1");
titleArea.setAdditionalData(additionalData);
baseSitePage.setTitleArea(titleArea);
CanvasLayout canvasLayout = new CanvasLayout();
LinkedList<HorizontalSection> horizontalSections = new LinkedList<HorizontalSection>();
HorizontalSection horizontalSection = new HorizontalSection();
horizontalSection.setLayout(HorizontalSectionLayoutType.OneThirdRightColumn);
horizontalSection.setId("1");
horizontalSection.setEmphasis(SectionEmphasisType.None);
LinkedList<HorizontalSectionColumn> columns = new LinkedList<HorizontalSectionColumn>();
HorizontalSectionColumn horizontalSectionColumn = new HorizontalSectionColumn();
horizontalSectionColumn.setId("1");
horizontalSectionColumn.setWidth(8);
LinkedList<WebPart> webparts = new LinkedList<WebPart>();
WebPart webPart = new WebPart();
webPart.setId("6f9230af-2a98-4952-b205-9ede4f9ef548");
HashMap<String, Object> additionalData1 = new HashMap<String, Object>();
additionalData1.put("innerHtml", "<p><b>Hello!</b></p>");
webPart.setAdditionalData(additionalData1);
webparts.add(webPart);
horizontalSectionColumn.setWebparts(webparts);
columns.add(horizontalSectionColumn);
HorizontalSectionColumn horizontalSectionColumn1 = new HorizontalSectionColumn();
horizontalSectionColumn1.setId("2");
horizontalSectionColumn1.setWidth(4);
LinkedList<WebPart> webparts1 = new LinkedList<WebPart>();
WebPart webPart1 = new WebPart();
webPart1.setId("73d07dde-3474-4545-badb-f28ba239e0e1");
HashMap<String, Object> additionalData2 = new HashMap<String, Object>();
additionalData2.put("webPartType", "d1d91016-032f-456d-98a4-721247c305e8");
 data = new ();
data.setDataVersion("1.9");
data.setDescription("Show an image on your page");
data.setTitle("Image");
 properties = new ();
properties.setImageSourceType(2);
properties.setAltText("");
properties.setOverlayText("");
properties.setSiteid("0264cabe-6b92-450a-b162-b0c3d54fe5e8");
properties.setWebid("f3989670-cd37-4514-8ccb-0f7c2cbe5314");
properties.setListid("bdb41041-eb06-474e-ac29-87093386bb14");
properties.setUniqueid("d9f94b40-78ba-48d0-a39f-3cb23c2fe7eb");
properties.setImgWidth(4288);
properties.setImgHeight(2848);
properties.setFixAspectRatio(false);
properties.setCaptionText("");
properties.setAlignment("Center");
data.setProperties(properties);
 serverProcessedContent = new ();
LinkedList<Object> imageSources = new LinkedList<Object>();
 property = new ();
property.setKey("imageSource");
property.setValue("/_LAYOUTS/IMAGES/VISUALTEMPLATEIMAGE1.JPG");
imageSources.add(property);
serverProcessedContent.setImageSources(imageSources);
LinkedList<Object> customMetadata = new LinkedList<Object>();
 property1 = new ();
property1.setKey("imageSource");
 value1 = new ();
value1.setSiteid("0264cabe-6b92-450a-b162-b0c3d54fe5e8");
value1.setWebid("f3989670-cd37-4514-8ccb-0f7c2cbe5314");
value1.setListid("bdb41041-eb06-474e-ac29-87093386bb14");
value1.setUniqueid("d9f94b40-78ba-48d0-a39f-3cb23c2fe7eb");
value1.setWidth("4288");
value1.setHeight("2848");
property1.setValue(value1);
customMetadata.add(property1);
serverProcessedContent.setCustomMetadata(customMetadata);
data.setServerProcessedContent(serverProcessedContent);
additionalData2.put("data", data);
webPart1.setAdditionalData(additionalData2);
webparts1.add(webPart1);
horizontalSectionColumn1.setWebparts(webparts1);
columns.add(horizontalSectionColumn1);
horizontalSection.setColumns(columns);
horizontalSections.add(horizontalSection);
canvasLayout.setHorizontalSections(horizontalSections);
baseSitePage.setCanvasLayout(canvasLayout);
BaseSitePage result = graphClient.sites().bySiteId("{site-id}").pages().post(baseSitePage);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```javascript

const options = {
	authProvider,
};

const client = Client.init(options);

const baseSitePage = {
  '@odata.type': '#microsoft.graph.sitePage',
  name: 'test.aspx',
  title: 'test',
  pageLayout: 'article',
  showComments: true,
  showRecommendedPages: false,
  titleArea: {
    enableGradientEffect: true,
    imageWebUrl: 'https://cdn.hubblecontent.osi.office.net/m365content/publish/005292d6-9dcc-4fc5-b50b-b2d0383a411b/image.jpg',
    layout: 'colorBlock',
    showAuthor: true,
    showPublishedDate: false,
    showTextBlockAboveTitle: false,
    textAboveTitle: 'TEXT ABOVE TITLE',
    textAlignment: 'left',
    imageSourceType: 2,
    title: 'sample1'
  },
  canvasLayout: {
    horizontalSections: [
      {
        layout: 'oneThirdRightColumn',
        id: '1',
        emphasis: 'none',
        columns: [
          {
            id: '1',
            width: 8,
            webparts: [
              {
                id: '6f9230af-2a98-4952-b205-9ede4f9ef548',
                innerHtml: '<p><b>Hello!</b></p>'
              }
            ]
          },
          {
            id: '2',
            width: 4,
            webparts: [
              {
                id: '73d07dde-3474-4545-badb-f28ba239e0e1',
                webPartType: 'd1d91016-032f-456d-98a4-721247c305e8',
                data: {
                  dataVersion: '1.9',
                  description: 'Show an image on your page',
                  title: 'Image',
                  properties: {
                    imageSourceType: 2,
                    altText: '',
                    overlayText: '',
                    siteid: '0264cabe-6b92-450a-b162-b0c3d54fe5e8',
                    webid: 'f3989670-cd37-4514-8ccb-0f7c2cbe5314',
                    listid: 'bdb41041-eb06-474e-ac29-87093386bb14',
                    uniqueid: 'd9f94b40-78ba-48d0-a39f-3cb23c2fe7eb',
                    imgWidth: 4288,
                    imgHeight: 2848,
                    fixAspectRatio: false,
                    captionText: '',
                    alignment: 'Center'
                  },
                  serverProcessedContent: {
                    imageSources: [
                      {
                        key: 'imageSource',
                        value: '/_LAYOUTS/IMAGES/VISUALTEMPLATEIMAGE1.JPG'
                      }
                    ],
                    customMetadata: [
                      {
                        key: 'imageSource',
                        value: {
                          siteid: '0264cabe-6b92-450a-b162-b0c3d54fe5e8',
                          webid: 'f3989670-cd37-4514-8ccb-0f7c2cbe5314',
                          listid: 'bdb41041-eb06-474e-ac29-87093386bb14',
                          uniqueid: 'd9f94b40-78ba-48d0-a39f-3cb23c2fe7eb',
                          width: '4288',
                          height: '2848'
                        }
                      }
                    ]
                  }
                }
              }
            ]
          }
        ]
      }
    ]
  }
};

await client.api('/sites/{site-id}/pages')
	.post(baseSitePage);
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```php

<?php
use Microsoft\Graph\GraphServiceClient;
use Microsoft\Graph\Generated\Models\SitePage;
use Microsoft\Graph\Generated\Models\PageLayoutType;
use Microsoft\Graph\Generated\Models\TitleArea;
use Microsoft\Graph\Generated\Models\TitleAreaLayoutType;
use Microsoft\Graph\Generated\Models\TitleAreaTextAlignmentType;
use Microsoft\Graph\Generated\Models\CanvasLayout;
use Microsoft\Graph\Generated\Models\HorizontalSection;
use Microsoft\Graph\Generated\Models\HorizontalSectionLayoutType;
use Microsoft\Graph\Generated\Models\SectionEmphasisType;
use Microsoft\Graph\Generated\Models\HorizontalSectionColumn;
use Microsoft\Graph\Generated\Models\WebPart;


$graphServiceClient = new GraphServiceClient($tokenRequestContext, $scopes);

$requestBody = new SitePage();
$requestBody->setOdataType('#microsoft.graph.sitePage');
$requestBody->setName('test.aspx');
$requestBody->setTitle('test');
$requestBody->setPageLayout(new PageLayoutType('article'));
$requestBody->setShowComments(true);
$requestBody->setShowRecommendedPages(false);
$titleArea = new TitleArea();
$titleArea->setEnableGradientEffect(true);
$titleArea->setImageWebUrl('https://cdn.hubblecontent.osi.office.net/m365content/publish/005292d6-9dcc-4fc5-b50b-b2d0383a411b/image.jpg');
$titleArea->setLayout(new TitleAreaLayoutType('colorBlock'));
$titleArea->setShowAuthor(true);
$titleArea->setShowPublishedDate(false);
$titleArea->setShowTextBlockAboveTitle(false);
$titleArea->setTextAboveTitle('TEXT ABOVE TITLE');
$titleArea->setTextAlignment(new TitleAreaTextAlignmentType('left'));
$additionalData = [
	'imageSourceType' => 2,
	'title' => 'sample1',
];
$titleArea->setAdditionalData($additionalData);
$requestBody->setTitleArea($titleArea);
$canvasLayout = new CanvasLayout();
$horizontalSectionsHorizontalSection1 = new HorizontalSection();
$horizontalSectionsHorizontalSection1->setLayout(new HorizontalSectionLayoutType('oneThirdRightColumn'));
$horizontalSectionsHorizontalSection1->setId('1');
$horizontalSectionsHorizontalSection1->setEmphasis(new SectionEmphasisType('none'));
$columnsHorizontalSectionColumn1 = new HorizontalSectionColumn();
$columnsHorizontalSectionColumn1->setId('1');
$columnsHorizontalSectionColumn1->setWidth(8);
$webpartsWebPart1 = new WebPart();
$webpartsWebPart1->setId('6f9230af-2a98-4952-b205-9ede4f9ef548');
$additionalData = [
	'innerHtml' => '<p><b>Hello!</b></p>',
];
$webpartsWebPart1->setAdditionalData($additionalData);
$webpartsArray []= $webpartsWebPart1;
$columnsHorizontalSectionColumn1->setWebparts($webpartsArray);

$columnsArray []= $columnsHorizontalSectionColumn1;
$columnsHorizontalSectionColumn2 = new HorizontalSectionColumn();
$columnsHorizontalSectionColumn2->setId('2');
$columnsHorizontalSectionColumn2->setWidth(4);
$webpartsWebPart1 = new WebPart();
$webpartsWebPart1->setId('73d07dde-3474-4545-badb-f28ba239e0e1');
$additionalData = [
'webPartType' => 'd1d91016-032f-456d-98a4-721247c305e8',
'data' => [
	'dataVersion' => '1.9',
	'description' => 'Show an image on your page',
	'title' => 'Image',
	'properties' => [
		'imageSourceType' => 2,
		'altText' => '',
		'overlayText' => '',
		'siteid' => '0264cabe-6b92-450a-b162-b0c3d54fe5e8',
		'webid' => 'f3989670-cd37-4514-8ccb-0f7c2cbe5314',
		'listid' => 'bdb41041-eb06-474e-ac29-87093386bb14',
		'uniqueid' => 'd9f94b40-78ba-48d0-a39f-3cb23c2fe7eb',
		'imgWidth' => 4288,
		'imgHeight' => 2848,
		'fixAspectRatio' => false,
		'captionText' => '',
		'alignment' => 'Center',
	],
	'serverProcessedContent' => [
		'imageSources' => [
				[
					'key' => 'imageSource',
					'value' => '/_LAYOUTS/IMAGES/VISUALTEMPLATEIMAGE1.JPG',
				],
			],
		'customMetadata' => [
				[
					'key' => 'imageSource',
					'value' => [
						'siteid' => '0264cabe-6b92-450a-b162-b0c3d54fe5e8',
						'webid' => 'f3989670-cd37-4514-8ccb-0f7c2cbe5314',
						'listid' => 'bdb41041-eb06-474e-ac29-87093386bb14',
						'uniqueid' => 'd9f94b40-78ba-48d0-a39f-3cb23c2fe7eb',
						'width' => '4288',
						'height' => '2848',
					],
				],
			],
	],
],
];
$webpartsWebPart1->setAdditionalData($additionalData);
$webpartsArray []= $webpartsWebPart1;
$columnsHorizontalSectionColumn2->setWebparts($webpartsArray);

$columnsArray []= $columnsHorizontalSectionColumn2;
$horizontalSectionsHorizontalSection1->setColumns($columnsArray);

$horizontalSectionsArray []= $horizontalSectionsHorizontalSection1;
$canvasLayout->setHorizontalSections($horizontalSectionsArray);

$requestBody->setCanvasLayout($canvasLayout);

$result = $graphServiceClient->sites()->bySiteId('site-id')->pages()->post($requestBody)->wait();
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```powershell

Import-Module Microsoft.Graph.Sites

$params = @{
	"@odata.type" = "#microsoft.graph.sitePage"
	name = "test.aspx"
	title = "test"
	pageLayout = "article"
	showComments = $true
	showRecommendedPages = $false
	titleArea = @{
		enableGradientEffect = $true
		imageWebUrl = "https://cdn.hubblecontent.osi.office.net/m365content/publish/005292d6-9dcc-4fc5-b50b-b2d0383a411b/image.jpg"
		layout = "colorBlock"
		showAuthor = $true
		showPublishedDate = $false
		showTextBlockAboveTitle = $false
		textAboveTitle = "TEXT ABOVE TITLE"
		textAlignment = "left"
		imageSourceType = 
		title = "sample1"
	}
	canvasLayout = @{
		horizontalSections = @(
			@{
				layout = "oneThirdRightColumn"
				id = "1"
				emphasis = "none"
				columns = @(
					@{
						id = "1"
						width = 
						webparts = @(
							@{
								id = "6f9230af-2a98-4952-b205-9ede4f9ef548"
								innerHtml = "<p><b>Hello!</b></p>"
							}
						)
					}
					@{
						id = "2"
						width = 
						webparts = @(
							@{
								id = "73d07dde-3474-4545-badb-f28ba239e0e1"
								webPartType = "d1d91016-032f-456d-98a4-721247c305e8"
								data = @{
									dataVersion = "1.9"
									description = "Show an image on your page"
									title = "Image"
									properties = @{
										imageSourceType = 
										altText = ""
										overlayText = ""
										siteid = "0264cabe-6b92-450a-b162-b0c3d54fe5e8"
										webid = "f3989670-cd37-4514-8ccb-0f7c2cbe5314"
										listid = "bdb41041-eb06-474e-ac29-87093386bb14"
										uniqueid = "d9f94b40-78ba-48d0-a39f-3cb23c2fe7eb"
										imgWidth = 
										imgHeight = 
										fixAspectRatio = $false
										captionText = ""
										alignment = "Center"
									}
									serverProcessedContent = @{
										imageSources = @(
											@{
												key = "imageSource"
												value = "/_LAYOUTS/IMAGES/VISUALTEMPLATEIMAGE1.JPG"
											}
										)
										customMetadata = @(
											@{
												key = "imageSource"
												value = @{
													siteid = "0264cabe-6b92-450a-b162-b0c3d54fe5e8"
													webid = "f3989670-cd37-4514-8ccb-0f7c2cbe5314"
													listid = "bdb41041-eb06-474e-ac29-87093386bb14"
													uniqueid = "d9f94b40-78ba-48d0-a39f-3cb23c2fe7eb"
													width = "4288"
													height = "2848"
												}
											}
										)
									}
								}
							}
						)
					}
				)
			}
		)
	}
}

New-MgSitePage -SiteId $siteId -BodyParameter $params
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

```python

# Code snippets are only available for the latest version. Current version is 1.x
from msgraph import GraphServiceClient
from msgraph.generated.models.site_page import SitePage
from msgraph.generated.models.page_layout_type import PageLayoutType
from msgraph.generated.models.title_area import TitleArea
from msgraph.generated.models.title_area_layout_type import TitleAreaLayoutType
from msgraph.generated.models.title_area_text_alignment_type import TitleAreaTextAlignmentType
from msgraph.generated.models.canvas_layout import CanvasLayout
from msgraph.generated.models.horizontal_section import HorizontalSection
from msgraph.generated.models.horizontal_section_layout_type import HorizontalSectionLayoutType
from msgraph.generated.models.section_emphasis_type import SectionEmphasisType
from msgraph.generated.models.horizontal_section_column import HorizontalSectionColumn
from msgraph.generated.models.web_part import WebPart
# To initialize your graph_client, see https://learn.microsoft.com/en-us/graph/sdks/create-client?from=snippets&tabs=python
request_body = SitePage(
	odata_type = "#microsoft.graph.sitePage",
	name = "test.aspx",
	title = "test",
	page_layout = PageLayoutType.Article,
	show_comments = True,
	show_recommended_pages = False,
	title_area = TitleArea(
		enable_gradient_effect = True,
		image_web_url = "https://cdn.hubblecontent.osi.office.net/m365content/publish/005292d6-9dcc-4fc5-b50b-b2d0383a411b/image.jpg",
		layout = TitleAreaLayoutType.ColorBlock,
		show_author = True,
		show_published_date = False,
		show_text_block_above_title = False,
		text_above_title = "TEXT ABOVE TITLE",
		text_alignment = TitleAreaTextAlignmentType.Left,
		additional_data = {
				"image_source_type" : 2,
				"title" : "sample1",
		}
	),
	canvas_layout = CanvasLayout(
		horizontal_sections = [
			HorizontalSection(
				layout = HorizontalSectionLayoutType.OneThirdRightColumn,
				id = "1",
				emphasis = SectionEmphasisType.None,
				columns = [
					HorizontalSectionColumn(
						id = "1",
						width = 8,
						webparts = [
							WebPart(
								id = "6f9230af-2a98-4952-b205-9ede4f9ef548",
								additional_data = {
										"inner_html" : "<p><b>Hello!</b></p>",
								}
							),
						],
					),
					HorizontalSectionColumn(
						id = "2",
						width = 4,
						webparts = [
							WebPart(
								id = "73d07dde-3474-4545-badb-f28ba239e0e1",
								additional_data = {
										"web_part_type" : "d1d91016-032f-456d-98a4-721247c305e8",
										"data" : {
												"data_version" : "1.9",
												"description" : "Show an image on your page",
												"title" : "Image",
												"properties" : {
														"image_source_type" : 2,
														"alt_text" : "",
														"overlay_text" : "",
														"siteid" : "0264cabe-6b92-450a-b162-b0c3d54fe5e8",
														"webid" : "f3989670-cd37-4514-8ccb-0f7c2cbe5314",
														"listid" : "bdb41041-eb06-474e-ac29-87093386bb14",
														"uniqueid" : "d9f94b40-78ba-48d0-a39f-3cb23c2fe7eb",
														"img_width" : 4288,
														"img_height" : 2848,
														"fix_aspect_ratio" : False,
														"caption_text" : "",
														"alignment" : "Center",
												},
												"server_processed_content" : {
														"image_sources" : [
															{
																	"key" : "imageSource",
																	"value" : "/_LAYOUTS/IMAGES/VISUALTEMPLATEIMAGE1.JPG",
															},
														],
														"custom_metadata" : [
															{
																	"key" : "imageSource",
																	"value" : {
																			"siteid" : "0264cabe-6b92-450a-b162-b0c3d54fe5e8",
																			"webid" : "f3989670-cd37-4514-8ccb-0f7c2cbe5314",
																			"listid" : "bdb41041-eb06-474e-ac29-87093386bb14",
																			"uniqueid" : "d9f94b40-78ba-48d0-a39f-3cb23c2fe7eb",
																			"width" : "4288",
																			"height" : "2848",
																	},
															},
														],
												},
										},
								}
							),
						],
					),
				],
			),
		],
	),
)

result = await graph_client.sites.by_site_id('site-id').pages.post(request_body)
```

> For details about how to [add the SDK](https://learn.microsoft.com/en-us/graph/sdks/sdk-installation) to your project and [create an authProvider](https://learn.microsoft.com/en-us/graph/sdks/choose-authentication-providers) instance, see the [SDK documentation](https://learn.microsoft.com/en-us/graph/sdks/sdks-overview).

---

### Response

If successful, this method returns a [sitePage](https://learn.microsoft.com/en-us/graph/api/resources/sitepage?view=graph-rest-1.0) in the response body for the created page.

```http
HTTP/1.1 201 Created
Content-type: application/json

{
    "@odata.type": "microsoft.graph.sitePage",
    "id": "0dd6ddd6-45bd-4acd-b683-de0e6e7231b7",
    "name": "test.aspx",
    "webUrl": "https://contoso.sharepoint.com/SitePages/test.aspx",
    "title": "test",
    "pageLayout": "article",
    "showComments": true,
    "showRecommendedPages": false,
    "createdBy": {
      "user": {
          "displayName": "Rahul Mittal",
          "email": "rahmit@contoso.com"
      }
    },
    "lastModifiedBy": {
      "user": {
          "displayName": "Rahul Mittal",
          "email": "rahmit@contoso.com"
      }
    },
    "publishingState": {
      "level": "checkout",
      "versionId": "0.1",
      "checkedOutBy": {
        "user": {
          "displayName": "Rahul Mittal",
          "email": "rahmit@contoso.com"
        }
      }
    },
    "titleArea": {
        "enableGradientEffect": true,
        "imageWebUrl": "https://cdn.hubblecontent.osi.office.net/m365content/publish/005292d6-9dcc-4fc5-b50b-b2d0383a411b/image.jpg",
        "layout": "colorBlock",
        "showAuthor": true,
        "showPublishedDate": false,
        "showTextBlockAboveTitle": false,
        "textAboveTitle": "TEXT ABOVE TITLE",
        "textAlignment": "left",
        "title": "sample4",
        "imageSourceType": 2
    }
}
```

**Note:** The response object is truncated for clarity. Default properties will be returned from the actual call.
