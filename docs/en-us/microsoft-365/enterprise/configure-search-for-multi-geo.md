<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/enterprise/configure-search-for-multi-geo?view=o365-worldwide -->
<!-- Sitemap-Last-Modified: 2025-12-07 -->

# Configure Search for Microsoft 365 Multi-Geo

## Configure Multi-Geo Search

Your Multi-Geo *Tenant* will have aggregate search capabilities allowing a search query to return results from anywhere within the *Tenant*.

By default, searches from these entry points will return aggregate results, even though each search index is located within its relevant *Geography* location:

- OneDrive
- Delve
- SharePoint Home
- Search Center

Additionally, Multi-Geo search capabilities can be configured for your custom search applications that use the SharePoint search API.

Please review [Configure Search for OneDrive Multi-Geo](https://learn.microsoft.com/en-us/microsoft-365/enterprise/configure-search-for-multi-geo?view=o365-worldwide) for instructions including any limitations and differences.

## Validating the Microsoft 365 Multi-Geo configuration

Below are some basic use cases you may wish to include in your validation plan before broadly rolling out Microsoft 365 Multi-Geo to your company. Once you have completed these tests and any additional use cases that are relevant to your company, you may choose to move on to adding the users in your initial pilot group.

OneDrive:

Select OneDrive from the Microsoft 365 app launcher and confirm that you are automatically directed to the appropriate *Geography* location for the user, based on the user's PDL. OneDrive should now begin provisioning at that location. Once provisioned, try uploading and downloading some documents.

OneDrive Mobile App:

Log in to your OneDrive mobile App with your test account credentials. Confirm that you can see your OneDrive files and can interact with them from your mobile device.

OneDrive sync client:

Confirm that the OneDrive sync client automatically detects your OneDrive *Geography* location upon login. If you need to download the sync client, you can click **Sync** in the OneDrive library.

Office applications:

Confirm that you can access OneDrive by logging in from an Office application, such as Word. Open the Office application and select **OneDrive - <TenantName>**. Office will detect your OneDrive location and show you the files that you can open.

Sharing:

Try sharing OneDrive files. Confirm that the people picker shows you all your SharePoint users regardless of their *Geography* location.

In a multi-geo environment, each *Geography* location has its own search index and Search Center. When a user searches, the query is fanned out to all the indexes, and the returned results are merged.

For example, a user in one *Geography* location can search for content stored in another *Geography* location, or for content on a SharePoint site that's restricted to a different Geography location. If the user has access to this content, search will show the result.

## Which search clients work in a Multi-Geo environment?

These clients can return results from all Geography locations:

- OneDrive
- Delve
- The SharePoint home page
- The Search Center
- Custom search applications that use the SharePoint Search API

### OneDrive

As soon as the Multi-Geo environment has been set up, users that search in OneDrive get results from all *Geography* locations.

### Delve

As soon as the Multi-Geo environment has been set up, users that search in Delve get results from all *Geography* locations.

The Delve feed and the profile card only show previews of files that are stored in the central location. For files that are stored in *Satellite Geography* locations, the icon for the file type is shown instead.

### The SharePoint home page

As soon as the Multi-Geo environment has been set up, users will see news, recent and followed sites from multiple *Geography* locations on their SharePoint home page. If they use the search box on the SharePoint home page, they'll get merged results from multiple *Geography* locations.

### The Search Center

After the multi-geo environment has been set up, each Search Center continues to only show results from their own *Geography* location. Admins must [change the settings of each Search Center](#_Set_up_a_1) to get results from all *Geography* locations. Afterwards, users that search in the Search Center get results from all *Geography* locations.

### Custom search applications

As usual, custom search applications interact with the search indexes by using the existing SharePoint Search REST APIs. To get results from all, or some *Geography* locations, the application must [call the API and include the new Multi-Geo query parameters](#_Get_custom_search) in the request. This triggers a fan out of the query to all *Geography* locations.

## What's different about search in a Multi-Geo environment?

Some search features you might be familiar with, work differently in a multi-geo environment.

| Feature | How it works | Workaround |
| :--- | :--- | :--- |
| Promoted results | You can create query rules with promoted results at different levels: for the whole *Tenant*, for a site collection, or for a site. In a Multi-Geo environment, define promoted results at the *Tenant* level to promote the results to the Search Centers in all *Geography* locations. If you only want to promote results in the Search Center that's in the *Geography* location of the site collection or site, define the promoted results at the site collection or site level. These results are not promoted in other *Geography* locations. | If you don't need different promoted results per *Geography* location, for example different rules for traveling, we recommend defining promoted results at the *Tenant* level. |
| Search refiners | Search returns refiners from all the *Geography* locations of a *Tenant* and then aggregates them. The aggregation is a best effort, meaning that the refiner counts might not be 100% accurate. For most search-driven scenarios, this accuracy is sufficient. | For search-driven applications that depend on refiner completeness, query each *Geography* location independently. |
|  | Multi-Geo search doesn't support dynamic bucketing for numerical refiners. | Use the ["Discretize" parameter](https://learn.microsoft.com/en-us/sharepoint/dev/general-development/query-refinement-in-sharepoint) for numerical refiners. |
| Document IDs | If you're developing a search-driven application that depends on document IDs, note that document IDs in a Multi-Geo environment aren't unique across *Geography* locations, they are unique per *Geography* location. | We've added a column that identifies the *Geography* location. Use this column to achieve uniqueness. This column is named "GeoLocationSource". |
| Number of results | The search results page shows combined results from the *Geography* locations, but it's not possible to page beyond 500 results. |  |
| Hybrid search | In a hybrid SharePoint environment with [cloud hybrid search](https://learn.microsoft.com/en-us/sharepoint/hybrid/learn-about-cloud-hybrid-search-for-sharepoint), on-premises content is added to the Microsoft 365 index of the central location. |  |

## What's not supported for search in a multi-geo environment?

Some of the search features you might be familiar with, aren't supported in a multi-geo environment.

| Search feature | Note |
| :--- | :--- |
| App-only authentication | App-only authentication \(privileged access from services\) isn't supported in multi-geo search. |
| Guests | Guests only get results from the *Geography* location that they're searching from. |

## How does search work in a Multi-Geo environment?

All the search clients use the existing SharePoint Search REST APIs to interact with the search indexes.

![Diagram showing how SharePoint Search REST APIs interact with the search indexes.](https://learn.microsoft.com/en-us/microsoft-365/media/configure-search-for-multi-geo-image1-1.png?view=o365-worldwide)

1. A search client calls the Search REST endpoint with the query property EnableMultiGeoSearch= true.
2. The query is sent to all *Geography* locations in the *Tenant*.
3. Search results from each *Geography* location are merged and ranked.
4. The client gets unified search results.

Notice that we don't merge the search results until we've received results from all the geo locations. This means that multi-geo searches have additional latency compared to searches in an environment with only one geo location.

## Get a Search Center to show results from all geo locations

Each Search Center has several verticals and you have to set up each vertical individually.

1. Ensure that you perform these steps with an account that has permission to edit the search results page and the Search Result Web Part.
2. Navigate to the search results page \(see the [list](https://support.office.com/article/174d36e0-2f85-461a-ad9a-8b3f434a4213) of search results pages\)
3. Select the vertical to set up, click **Settings** gear icon in the upper, right corner, and then click **Edit Page**. The search results page opens in Edit mode.

   ![Edit page selection in Settings.](https://learn.microsoft.com/en-us/microsoft-365/media/configure-search-for-multi-geo-image2.png?view=o365-worldwide)
4. In the Search Results Web Part, move the pointer to the upper, right corner of the web part, click the arrow, and then click **Edit Web Part** on the menu. The Search Results Web Part tool pane opens under the ribbon in the top right of the page.

   ![Edit Web Part selection.](https://learn.microsoft.com/en-us/microsoft-365/media/configure-search-for-multi-geo-image3.png?view=o365-worldwide)
5. In the Web Part tool pane, in the **Settings** section, under **Results control settings**, select **Show Multi-Geo results** to get the Search Results Web Part to show results from all geo locations.
6. Click **OK** to save your change and close the Web Part tool pane.
7. Check your changes to the Search Results Web Part by clicking **Check-In** on the Page tab of the main menu.
8. Publish the changes by using the link provided in the note at the top of the page.

## Get custom search applications to show results from all or some geo locations

Custom search applications get results from all, or some, *Geography* locations by specifying query parameters with the request to the SharePoint Search REST API. Depending on the query parameters, the query is fanned out to all *Geography* locations, or to some geo locations. For example, if you only need to query a subset of *Geography* locations to find relevant information, you can control the fan out to only these. If the request succeeds, the SharePoint Search REST API returns response data.

### Requirement

For each geo location, you must ensure that all users in the organization have been granted the **Read** permission level for the root website \(for example contoso**APAC**.sharepoint.com/ and contoso**EU**.sharepoint.com/\). [Learn about permissions](https://support.office.com/article/understanding-permission-levels-in-sharepoint-87ecbb0e-6550-491a-8826-c075e4859848).

### Query parameters

EnableMultiGeoSearch - This is a Boolean value that specifies whether the query shall be fanned out to the indexes of other geo locations of the multi-geo *Tenant*. Set it to **true** to fan out the query; **false** to not fan out the query. If you don't include this parameter, the default value is **false**, except when making a REST API call against a site which uses the Enterprise Search Center template, in this case the default value is **true**. If you use the parameter in an environment that isn't multi-geo, the parameter is ignored.

ClientType - This is a string. Enter a unique client name for each search application. If you don't include this parameter, the query is not fanned out to other geo locations.

MultiGeoSearchConfiguration - This is an optional list of which geo locations in the multi-geo *Tenant* to fan the query out to when **EnableMultiGeoSearch** is **true**. If you don't include this parameter, or leave it blank, the query is fanned out to all geo locations. For each geo location, enter the following items, in JSON format:

| Item | Description |
| :--- | :--- |
| DataLocation | The *Geography* location, for example NAM. |
| EndPoint | The endpoint to connect to, for example https://contoso.sharepoint.com |
| SourceId | The GUID of the result source, for example B81EAB55-3140-4312-B0F4-9459D1B4FFEE. |

If you omit DataLocation or EndPoint, or if a DataLocation is duplicated, the request fails. [You can get information about the endpoint of a tenant's geo locations by using Microsoft Graph](https://learn.microsoft.com/en-us/sharepoint/dev/solution-guidance/multigeo-discovery).

### Response data

MultiGeoSearchStatus - This is a property that the SharePoint Search API returns in response to a request. The value of the property is a string and gives the following information about the results that the SharePoint Search API returns:

| Value | Description |
| :--- | :--- |
| Full | Full results from **all** the *Geography* locations. |
| Partial | Partial results from one or more *Geography* locations. The results are incomplete due to a transient error. |

### Query using the REST service

With a GET request, you specify the query parameters in the URL. With a POST request, you pass the query parameters in the body in JavaScript Object Notation \(JSON\) format.

#### Request headers

| Name | Value |
| :--- | :--- |
| Content-Type | application/json;odata=verbose |

#### Sample GET request that's fanned out to **all** geo locations

```http
https://<tenant>/_api/search/query?querytext='sharepoint'&Properties='EnableMultiGeoSearch:true'&ClientType='my_client_id'
```

#### Sample GET request to fan out to **some** geo locations

```http
https://<tenant>/_api/search/query?querytext='site'&ClientType='my_client_id'&Properties='EnableMultiGeoSearch:true, MultiGeoSearchConfiguration:[{DataLocation\\:"NAM"\\,Endpoint\\:"https\\://contosoNAM.sharepoint.com"\\,SourceId\\:"B81EAB55-3140-4312-B0F4-9459D1B4FFEE"}\\,{DataLocation\\:"CAN"\\,Endpoint\\:"https\\://contosoCAN.sharepoint-df.com"}]'
```

Note

Commas and colons in the list of geo locations for the MultiGeoSearchConfiguration property are preceded by the **backslash** character. This is because GET requests use colons to separate properties and commas to separate arguments of properties. Without the backslash as an escape character, the MultiGeoSearchConfiguration property is interpreted wrongly.

#### Sample POST request that's fanned out to **all** geo locations

```http
    {
    "request": {
            "__metadata": {
            "type": "Microsoft.Office.Server.Search.REST.SearchRequest"
        },
        "Querytext": "sharepoint",
        "Properties": {
            "results": [
                {
                    "Name": "EnableMultiGeoSearch",
                    "Value": {
                        "QueryPropertyValueTypeIndex": 3,
                        "BoolVal": true
                    }
                }
            ]
        },
        "ClientType": "my_client_id"
        }
    }
```

#### Sample POST request that's fanned out to **some** geo locations

```http
    {
        "request": {
            "Querytext": "SharePoint",
            "ClientType": "my_client_id",
            "Properties": {
                "results": [
                    {
                        "Name": "EnableMultiGeoSearch",
                        "Value": {
                            "QueryPropertyValueTypeIndex": 3,
                            "BoolVal": true
                        }
                    },
                    {
                        "Name": "MultiGeoSearchConfiguration",
                        "Value": {
                        "StrVal": "[{\"DataLocation\":\"NAM\",\"Endpoint\":\"https://contoso.sharepoint.com\",\"SourceId\":\"B81EAB55-3140-4312-B0F4-9459D1B4FFEE\"},{\"DataLocation\":\"CAN\",\"Endpoint\":\"https://contosoCAN.sharepoint.com\"}]",
                            "QueryPropertyValueTypeIndex": 1
                        }
                    }
                ]
            }
        }
    }
```

### Query using CSOM

Here's a sample CSOM query that's fanned out to **all** *Geography* locations:

```CSOM
var keywordQuery = new KeywordQuery(ctx);
keywordQuery.QueryText = query.SearchQueryText;
keywordQuery.ClientType = <enter a string here>;
keywordQuery.Properties["EnableMultiGeoSearch"] = true;
```
