<!-- Source: https://learn.microsoft.com/en-us/graph/search-concept-custom-types -->
<!-- Sitemap-Last-Modified: 2025-12-01 -->

# Use the Microsoft Search API to search custom types imported using Copilot connectors

Use the Microsoft Search API in Microsoft Graph to search across external content ingested and indexed by [Microsoft 365 Copilot connectors](https://learn.microsoft.com/en-us/microsoftsearch/connectors-overview) \(formerly Microsoft Graph connectors\). The content is imported either via [built-in connectors](https://www.microsoft.com/microsoft-search/connectors) provided by Microsoft, or via custom connectors implemented by using the [Copilot connectors ingestion API](https://learn.microsoft.com/en-us/graph/api/resources/connectors-api-overview).

Caution

The search API schema has changed in the beta version. Some properties in a search request and response have been renamed or removed. For details, see [Schema change deprecation warning](https://learn.microsoft.com/en-us/graph/api/resources/search-api-overview?view=graph-rest-beta&preserve-view=true#schema-change-deprecation-warning). The examples in this topic show the up-to-date schema.

After the content has been imported and indexed, you can use the search API to query the content.

To search for custom types, specify the following properties in the request body of the [query](https://learn.microsoft.com/en-us/graph/api/search-query) method:

- The **contentSources** property to include the connection ID that is assigned during the connector setup. You can pass multiple connection IDs to search across multiple connections. Results are returned in a single list, ranked across the multiple connections.

- The **entityTypes** property as `externalItem`.
- The **fields** property to include the fields in the external item to retrieve. Note that if you do not include any **fields** in the request, the response will contain some of the fields marked as *retrievable* in the data schema specified for the specified connections in the **contentSources** property.

In addition, you can aggregate search results based on properties in an [externalItem](https://learn.microsoft.com/en-us/graph/api/resources/externalconnectors-externalitem) that are numeric or string type, and that are set to be refinable in the [schema](https://learn.microsoft.com/en-us/graph/api/resources/externalconnectors-schema). For more information, see [Refine search results using aggregations](https://learn.microsoft.com/en-us/graph/search-concept-aggregation).

## Example 1: Retrieve items using Azure SQL built-in connector

In this example, the content of the [AdventureWorks](https://learn.microsoft.com/en-us/sql/samples/adventureworks-install-configure) database has been ingested using the Azure SQL built-in connector.

### Request

```HTTP
POST https://graph.microsoft.com/v1.0/search/query
Content-Type: application/json

{
  "requests": [
    {
      "entityTypes": [
        "externalItem"
      ],
      "contentSources": [
          "/external/connections/azuresqlconnector",
          "/external/connections/azuresqlconnector2"
      ],
      "query": {
        "queryString": "yang"
      },
      "from": 0,
      "size": 25,
      "fields": [
        "BusinessEntityID",
        "firstName",
        "lastName"
      ]
    }
  ]
}
```

### Response

```HTTP
HTTP/1.1 200 OK
Content-type: application/json

{
  "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#Collection(microsoft.graph.searchResponse)",
  "value": [
    {
      "searchTerms": ["yang"],
      "hitsContainers": [
        {
          "total": 2,
          "moreResultsAvailable": false,
          "hits": [
            {
              "hitId": "AAMkADc0NDNlNTE0",
              "rank": 1,
              "summary": "<ddd/>",
              "contentSource": "/external/connections/azuresqlconnector",
              "resource": {
                "@odata.type": "#microsoft.graph.externalConnectors.externalItem",
                "properties": {
                  "businessEntityID": 20704,
                  "firstName": "Amy",
                  "lastName": "Yang"
                }
              }
            },
           {
              "hitId": "AQMkADg3M2I3YWMyLTEwZ",
              "rank": 2,
              "summary": "<ddd/>",
              "contentSource": "/external/connections/azuresqlconnector2",
              "resource": {
                "@odata.type": "#microsoft.graph.externalConnectors.externalItem",
                "properties": {
                  "businessEntityID": 20704,
                  "shortDescription": "Contoso maintenance guidelines",
                  "firstName": "Amy",
                  "lastName": "Yang"
                }
              }
            },
          ]
        }
      ]
    }
  ]
}
```

## Example 2: Retrieve items using semantic labels

### Request

```HTTP
POST https://graph.microsoft.com/v1.0/search/query
Content-Type: application/json

{
    "requests": [
      {
        "entityTypes": [
          "microsoft.graph.externalItem"
        ],
        "contentSources": [
          "/external/connections/FileAsUdt"
        ],
        "query": {
          "query_string": {
            "query": "test"
          }
        },
        "stored_fields": [
          "label_Title",
          "label_URL",
          "label_LastModifiedBy",
          "label_LastModifiedDateTime"
        ],
        "from": 0,
        "size": 25
      }
    ]
}
```

### Response

```HTTP
HTTP/1.1 200 OK
Content-type: application/json

{
  "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#Collection(microsoft.graph.searchResponse)",
"value": [
      {
        "searchTerms": [
          "test"
        ],
        "hitsContainers": [
          {
            "hits": [
              {
                "_id": "AQMkAGRjZWJjZTFkLTkzYWItNDhlOC1iODA2LTgwMTNjNjEzYzI2YwBGAAADOx0/YV2JckefuDmJtUO7mwcAHNjGq33S50uXSFeU/U9mogAAAgEWAAAAHNjGq33S50uXSFeU/U9mogAAAgleAAAA",
                "_contentSource": "FileAsUdt",
                "_score": 1,
                "_summary": "<c0>Test</c0> component to move data files and messages between the gateway and internal <ddd/>",
                "_source": {
                  "@odata.type": "#microsoft.graph.externalConnectors.externalItem",
                  "properties": {
                    "label_Title": "SONIC Operations support and test Guide for the month of March",
                    "label_URL": "D:\\\\ConnectorsEcho\\\\New\\\\MSW06SecondSet\\\\teams\\\\Enterprise_Platforms\\\\CCO\\\\Projects\\\\BTSi Modernization\\\\SONIC Retirement\\\\SONIC_Operations_Support_Guide.docx",
                    "label_LastModifiedBy": [
                      "Bob",
                      "Scott"
                    ],
                    "label_LastModifiedDateTime": "2020-01-30T12:44:19Z"
                  }
                }
              },
              {
                "_id": "AQMkAGRjZWJjZTFkLTkzYWItNDhlOC1iODA2LTgwMTNjNjEzYzI2YwBGAAADOx0/YV2JckefuDmJtUO7mwcAHNjGq33S50uXSFeU/U9mogAAAgEWAAAAHNjGq33S50uXSFeU/U9mogAAAgldAAAA",
                "_contentSource": "FileAsUdt",
                "_score": 2,
                "_summary": "File Transfer Workbench A <c0>test</c0> File transfer Management Solution File Transfer the number <ddd/>",
                "_source": {
                  "@odata.type": "#microsoft.graph.externalConnectors.externalItem",
                  "properties": {
                    "label_Title": "Test File Transfer Workbench for the month of January",
                    "label_URL": "D:\\\\ConnectorsEcho\\\\New\\\\MSW06SecondSet\\\\teams\\\\IssueLog\\\\FCAGA Organisation\\\\NSN CO CCA Infra YBCFTPAR entry\\\\File Transfer Workbench.ppt",
                    "label_LastModifiedBy": [
                      "Alice",
                      "Scott"
                    ],
                    "label_LastModifiedDateTime": "2020-01-31T11:44:19Z"
                  }
                }
              },
              {
                "_id": "AQMkAGRjZWJjZTFkLTkzYWItNDhlOC1iODA2LTgwMTNjNjEzYzI2YwBGAAADOx0/YV2JckefuDmJtUO7mwcAHNjGq33S50uXSFeU/U9mogAAAgEWAAAAHNjGq33S50uXSFeU/U9mogAAAglgAAAA",
                "_contentSource": "FileAsUdt",
                "_score": 3,
                "_summary": "document and the associated <c0>test</c0> software are the sole property of Express Logic.<ddd/>",
                "_source": {
                  "@odata.type": "#microsoft.graph.externalConnectors.externalItem",
                  "properties": {
                    "label_Title": "System User Guide Express Logic 858.613.6640",
                    "label_URL": "D:\\\\ConnectorsEcho\\\\New\\\\MSW06FirstSet\\\\teams\\\\AzureIoTMarketing\\\\Shared Documents\\\\Whitepapers\\\\RTOS Whitepapers\\\\User Guides\\\\Azure_RTOS_FileX_User_Guide.pdf",
                    "label_LastModifiedBy": [
                      "Alice",
                      "Bob"
                    ],
                    "label_LastModifiedDateTime": "2020-05-25T10:20:19Z"
                  }
                }
              }
            ],
            "total": 3,
            "moreResultsAvailable": false
          }
        ]
      }
    ]
}
```

For more details, see [Assign property labels](https://learn.microsoft.com/en-us/microsoftsearch/configure-connector#step-6-assign-property-labels).

## Next steps

- [Use the Microsoft Search API to query data](https://learn.microsoft.com/en-us/graph/api/resources/search-api-overview)
