<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/online/security -->
<!-- Sitemap-Last-Modified: 2025-01-29 -->

# Considerations for security and privacy

The considerations for security and privacy in Microsoft 365 for the web implementation follow.

## Microsoft 365 for the web and customer data

Two classes of customer data flow through Microsoft 365 for the web servers: user metadata and customer content \(documents, presentations, workbooks, and notebooks\).

### User metadata

User metadata consists of URLs, email addresses, user IDs, and so on. This data lives in memory and travels back and forth between Microsoft 365 for the web and the WOPI host through HTTPS. Microsoft 365 for the web goes to great lengths to scrub all personally identifying information \(PII\) from its logs. This is regularly audited to ensure Microsoft 365 for the web is compliant with several different privacy standards \(such as FedRamp in the USA\).

### Customer content

In the case of customer content, Microsoft 365 for the web retrieves it from the host in order to render it for viewing or editing. In the following image, you can see how WOPI is used to fetch content from the host and send content changes to the host \(ContosoDrive in this case\).

![Figure 18 WOPI protocol workflow](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/online/images/wopi-flow.png)

***Figure 18 -** WOPI protocol workflow*

With the exception of caching \(discussed below\), it's reasonable to say that customer content only lives on Microsoft 365 for the web servers during a user session. That is, a user can reasonably expect that when they end an editing session, their content no longer lives anywhere on Microsoft 365 for the web servers once it's been saved to the host. The key exception here is the Microsoft 365 for the web viewing cache.

## Microsoft 365 for the web viewing cache

In order to optimize view performance for PowerPoint for the web and Word for the web, Microsoft 365 for the web stores rendered documents in a local disk cache. This way, if more than one person wants to view a document, Microsoft 365 for the web only has to fetch it and render it once. It's important to note that a complete removal of the cache would significantly degrade the customer experience for many users and dramatically increase the cost of running Microsoft 365 for the web.

Documents in the cache are indexed using a [SHA256](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/files/checkfileinfo/checkfileinfo-other#sha256) hash that's generated based on the contents of the file \(or some other unique attribute of the file\). No user information is used to index the file. On every request for a file, if the WOPI host validates the access token, Microsoft 365 for the web uses the SHA256 hash returned by the host \(or generated based on [file id](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/concepts#file-id) plus [version](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/files/checkfileinfo/checkfileinfo-response#version) value\) to check for the file in the document cache.

Since the SHA256 hash is an enormous number that's generated using information unique to the file, there's essentially no chance of the same number being generated twice. Also, since the hash generates using information unique to the file and not based on any sort of user data, Microsoft 365 for the web can't retrieve information that's specific to a given user. Microsoft 365 for the web specifically doesn't log the SHA256 hash when the file is cached so that it's effectively impossible for Microsoft 365 for the web to retrieve information associated with a specific host or user without the participation of the host.

Documents live in the cache until they become unpopular. That is, the cache isn't time-based but rather based on available space and usage. Unpopular files might expire out of the cache in only a few days while popular documents might remain in the cache for up to 30 days.

As of May 2016, the contents of the cache are encrypted using a [FIPS 140-2](http://csrc.nist.gov/publications/fips/fips140-2/fips1402.pdf) compliant encryption algorithm.

## Compliance for Cloud Storage Partner Program Integrations

When you integrate with Microsoft 365 through the Cloud Storage Partner Program using the WOPI API, your requests hit the same infrastructure used for Microsoft 365 for the web and related services in Microsoft 365. Which means you and your customers benefit from the same strong security and privacy protections.

More information on the compliance of Microsoft services as related to the Cloud Storage Partner Program is available in the Microsoft 365 for the web portions of the audit reports related to Microsoft 365 provided in the [Microsoft Service Trust document portal](https://servicetrust.microsoft.com/ViewPage/MSComplianceGuideV3).

Note

Compliance for the overall end-to-end system for Cloud Storage Partner Program integrations requires that appropriate security and compliance requirements are also met by the cloud storage partner.
