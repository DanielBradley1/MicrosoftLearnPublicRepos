<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/cloud-storage-partner-program/faq/access-token-passing -->
<!-- Sitemap-Last-Modified: 2022-06-02 -->

# Office for the web sometimes sends the access token in the query string when making requests to the service. Is this a problem?

If you monitor the traffic between the Office for the web browser applications and the Office for the web service, you may notice that some requests include the WOPI access token on the URL. We recognize that this is an issue and have designed our service Office for the web logging infrastructure to deal with it. We scrub the query string from URLs before they are written to our logs. We have built a scrubber module into our standard server logging system that finds and redacts the access token in the two or three different forms it can take in a URL.

We believe that zero access tokens are currently being written to the Office for the web service logs, and we consider it an urgent bug if we discover that they are.
