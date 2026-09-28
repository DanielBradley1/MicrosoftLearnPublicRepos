<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/faq/access-token-length -->
<!-- Sitemap-Last-Modified: 2022-06-02 -->

# What is the maximum length of a WOPI access token?

There’s no enforced length limit on a WOPI [access token](https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/rest/concepts#access-token); however, the overall URL length limit for Office for the web is 2000 characters, and the access token is included on some GET requests between the Office for the web browser apps and the Office for the web service. This means that at some point, the access token can become so long that requests between the browser and the service will fail, which manifests as failing sessions. PowerPoint for the web is particularly susceptible to this problem.
