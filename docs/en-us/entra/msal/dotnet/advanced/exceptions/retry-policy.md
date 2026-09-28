<!-- Source: https://learn.microsoft.com/en-us/entra/msal/dotnet/advanced/exceptions/retry-policy -->
<!-- Sitemap-Last-Modified: 2025-05-20 -->

# Retry Policies are baked in the libary

MSAL has its own retry policies. In rare cases you can choose to disable the internal retry policies and add your own. See [HttpClient tips](https://learn.microsoft.com/en-us/entra/msal/dotnet/advanced/httpclient).

### MSAL implements a simple "retry-once" for errors with HTTP error codes 5xx

MSAL.NET implements a simple retry-once with 1 second delay mechanism for errors with HTTP error codes 500-600, for the token endpoint. For managed identity, the retry follows the guidelines of each source.

## Customize the HTTP stack

In some cases, such as using proxies, you might want to customize the Http Stack. See [HttpClient tips](https://learn.microsoft.com/en-us/entra/msal/dotnet/advanced/httpclient) for details.
