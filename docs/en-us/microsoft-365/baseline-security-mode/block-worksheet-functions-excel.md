<!-- Source: https://learn.microsoft.com/en-us/microsoft-365/baseline-security-mode/block-worksheet-functions-excel?view=o365-worldwide -->
<!-- Sitemap-Last-Modified: 2026-11-17 -->

# Block Excel worksheet functions from accessing the web through insecure protocols

This setting helps protect your organization from insecure data transfers initiated through Excel worksheet functions. Some Excel functions can retrieve data from external sources using outdated, insecure protocols such as HTTP. Blocking these connections prevents unencrypted data exposure and reduces the risk of tampering or interception.

You need to be a member of the [Office Apps administrator role](https://learn.microsoft.com/en-us/entra/identity/role-based-access-control/permissions-reference) to be able to configure this setting.

## Why this setting matters

Allowing worksheet functions to connect over insecure protocols can:

- Expose sensitive data in plaintext over the network
- Allow attackers to intercept or modify responses from untrusted endpoints
- Enable legacy workflows that bypass organizational security requirements

Blocking these connections ensures only secure, encrypted web requests are permitted, aligning with modern security expectations and reducing attack surface in Excel workloads.

## How this setting works

When enabled, this control:

- Blocks Excel worksheet functions from connecting to external web sources over insecure protocols \(such as HTTP\)
- Helps prevent exposure of sensitive data to unencrypted connections
- Reduces the possibility of malicious content being injected from unsafe endpoints

Functions affected include those functions that pull external data when they attempt to connect through insecure URLs, such as:

- **WEBSERVICE**
- **IMPORTTEXT**
- **IMPORTCSV**

The functions return a BLOCKED error when Excel detects an insecure protocol.

Users see that the request is blocked when Excel detects an insecure protocol.

## Use Cloud Policy service

You can also make changes to the policy settings directly using the [Cloud Policy service](https://config.office.com/). Set the **Block Insecure Protocols in Excel Worksheet Functions** policy as not configured to revert to the default behavior.
