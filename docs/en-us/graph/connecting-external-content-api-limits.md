<!-- Source: https://learn.microsoft.com/en-us/graph/connecting-external-content-api-limits -->
<!-- Sitemap-Last-Modified: 2026-07-24 -->

# Copilot connectors API limits

This article describes implementation and operational limits for Microsoft 365 Copilot connectors \(formerly Microsoft Graph connectors\). Keep these limits in mind when designing connectors.

## Schema limits

| Limit type | Limit |
| --- | --- |
| Properties that can be defined in a [schema](https://learn.microsoft.com/en-us/graph/api/resources/externalconnectors-schema), characterizing the data ingested through a connection | 128 |

## Group limits

| Limit type | Limit |
| --- | --- |
| [External groups](https://learn.microsoft.com/en-us/graph/api/resources/externalconnectors-externalgroup) per Microsoft 365 tenant | 100,000 |
| Requests allowed per second \(requests/sec\) in the group administration [throttling](#throttling) threshold | 1,000 |
| [External groups](https://learn.microsoft.com/en-us/graph/api/resources/externalconnectors-externalgroup) per user for search query | 10,000 |

## Item ingestion

| Limit type | Limit |
| --- | --- |
| Item size; this limit applies to the request body when [ingesting and indexing an item](https://learn.microsoft.com/en-us/graph/api/externalconnectors-externalconnection-put-items) | 30 MB |
| Number of [activities](https://learn.microsoft.com/en-us/graph/api/resources/externalconnectors-externalactivity); this is the [throttling](#throttling) threshold per activities call | 20 activities |
| Property size | N/A |

> **Note:** The 30 MB item size limit refers to the total size of *parsed text content* that is typically 10% of the original file size for common formats \(for example, docx, ppt, and PDF\). To contextualize, 30 MB translates to 10,000 pages of parsed content\(averaging 500 words per page\).

## Throttling

When a [throttling](https://learn.microsoft.com/en-us/graph/throttling) threshold is exceeded, Microsoft Graph limits any further requests from that client for a period of time. When throttling occurs, Microsoft Graph returns HTTP status code 429 \(Too many requests\), and the requests fail. A suggested wait time is returned in the response header of the failed request.

Throttling behavior can depend on the type and number of requests. For example, if you have a high volume of requests, all request types are throttled. Threshold limits vary based on the request type. Therefore, you could encounter a scenario where writes are throttled but reads are still permitted.
