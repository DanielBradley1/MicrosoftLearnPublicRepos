<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/fieldvalueset?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-12-26 -->

# fieldValueSet resource type

Namespace: microsoft.graph

Represents the column values in a [listItem](https://learn.microsoft.com/en-us/graph/api/resources/listitem?view=graph-rest-1.0) resource.

## JSON representation

Here's a JSON representation of a **fieldValueSet** resource.

```json
{
    "Author": "Brad Cleaver",
    "AuthorLookupId": "13",
    "Color": "Red",
    "Name": "Kangaroos and Wallabies: A Deep Dive",
    "Quantity": 350,
}
```

## Properties

Each user-visible field in the **listItem** is returned as a name-value pair in the **fieldValueSet**. The example above is for a list that contains four columns, **Author**, **Name**, **Color**, and **Quantity**.

Lookup fields \(like `Author` above\) aren't returned by default. Instead, the server returns a 'LookupId' field \(like `AuthorLookupId` above\) referencing the listItem targeted in the lookup. The name of the 'LookupId' field is the original field name followed by `LookupId`.

Up to 12 lookup fields may be requested in a single query. The server returns lookup values if your request includes a `select` statement with the fields you need. Example:

```http
GET https://graph.microsoft.com/v1.0/sites/{site-id}/lists/{list-id}/items?expand=fields(select=Author,BookTitle,PageCount)
```

You may request up to 12 lookup fields in a single query, plus any number of regular fields.
