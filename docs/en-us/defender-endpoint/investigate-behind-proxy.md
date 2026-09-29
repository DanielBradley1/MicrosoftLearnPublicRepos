<!-- Source: https://learn.microsoft.com/en-us/defender-endpoint/investigate-behind-proxy -->
<!-- Sitemap-Last-Modified: 2026-07-15 -->

# Investigate connection events that occur behind forward proxies

Defender for Endpoint supports network connection monitoring from different levels of the network stack. A challenging case is when the network uses a forward proxy as a gateway to the Internet.

The proxy acts as if it was the target endpoint. When a forward proxy acts as the target endpoint, simple network connection monitors audit the connections with the proxy that is correct but has lower investigation value.

Defender for Endpoint supports advanced HTTP level monitoring through network protection. When network protection is turned on, a new type of event is surfaced that exposes the real target domain names.

## Use network protection to monitor connections behind a forward proxy or firewall

Monitoring network connection behind a forward proxy is possible due to other network events that originate from network protection. To see these network events on a device timeline, turn on network protection \(at the minimum in audit mode\).

Network protection can be controlled using the following modes:

- **Block**: Users or apps are blocked from connecting to dangerous domains. You'll be able to see this activity in the Defender portal.
- **Audit**: Users or apps won't be blocked from connecting to dangerous domains. However, you'll still see this activity in the Defender portal.

If you turn off network protection, users or apps won't be blocked from connecting to dangerous domains. You won't see any network activity in Microsoft Defender XDR.

If you don't configure it, network blocking is turned off by default.

For more information, see [Enable network protection](https://learn.microsoft.com/en-us/defender-endpoint/enable-network-protection).

## How network protection reveals real targets behind forward proxies

When network protection is turned on, a device's timeline shows the proxy IP address while also displaying the real target address.

[![The network events on device's timeline](https://learn.microsoft.com/en-us/defender-endpoint/media/atp-proxy-investigation.png)](https://learn.microsoft.com/en-us/defender-endpoint/media/atp-proxy-investigation.png#lightbox)

Additional network protection connection events are available to surface the real domain names even behind a proxy.

Event's information:

[![The URLs of a single network event](https://learn.microsoft.com/en-us/defender-endpoint/media/atp-proxy-investigation-event.png)](https://learn.microsoft.com/en-us/defender-endpoint/media/atp-proxy-investigation-event.png#lightbox)

## Hunt for connection events using advanced hunting

The network protection connection events are also available through advanced hunting. You can find them in the DeviceNetworkEvents table under the `ConnectionSuccess` action type.

The following query returns all relevant ConnectionSuccess events:

```console
DeviceNetworkEvents
| where ActionType == "ConnectionSuccess"
| take 10
```

[![The advanced hunting query](https://learn.microsoft.com/en-us/defender-endpoint/media/atp-proxy-investigation-ah.png)](https://learn.microsoft.com/en-us/defender-endpoint/media/atp-proxy-investigation-ah.png#lightbox)

You can also filter out events that are related to connection to the proxy itself.

Use the following query to filter out the connections to the proxy:

```console
DeviceNetworkEvents
| where ActionType == "ConnectionSuccess" and RemoteIP != "ProxyIP"
| take 10
```

## Related articles

- [Enable network protection with Group Policy or policy CSP](https://learn.microsoft.com/en-us/windows/client-management/mdm/policy-csp-defender#defender-enablenetworkprotection)
