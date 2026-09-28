<!-- Source: https://learn.microsoft.com/en-us/graph/api/resources/filehash?view=graph-rest-1.0 -->
<!-- Sitemap-Last-Modified: 2024-12-26 -->

# fileHash resource type

Namespace: microsoft.graph

Contains stateful information about file hashes \(cryptographic and location-sensitive\).

## Properties

| Property | Type | Description |
| :--- | :--- | :--- |
| hashType | fileHashType | File hash type. The possible values are: `unknown`, `sha1`, `sha256`, `md5`, `authenticodeHash256`, `lsHash`, `ctph`, `peSha1`, `peSha256`. |
| hashValue | String | Value of the file hash. |

## JSON representation

The following JSON representation shows the resource type.

```json
{
  "hashType": "@odata.type: microsoft.graph.fileHashType",
  "hashValue": "String"
}
```
