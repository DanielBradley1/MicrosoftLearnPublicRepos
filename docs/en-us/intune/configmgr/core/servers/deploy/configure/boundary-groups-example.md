<!-- Source: https://learn.microsoft.com/en-us/intune/configmgr/core/servers/deploy/configure/boundary-groups-example -->
<!-- Sitemap-Last-Modified: 2022-10-04 -->

# Example of using boundary groups

*Applies to: Configuration Manager \(current branch\)*

The following example uses a client searching for content from a distribution point. This example can be applied to other site system roles that use boundary groups.

Create three boundary groups that don't share boundaries or site system servers:

- Group BG\_A with distribution points DP\_A1 and DP\_A2
- Group BG\_B with distribution points DP\_B1 and DP\_B2
- Group BG\_C with distribution points DP\_C1 and DP\_C2

Add the network locations of your clients as boundaries to only the BG\_A boundary group. Then configure relationships from that boundary group to the other two boundary groups:

- Configure distribution points for the first *neighbor* group \(BG\_B\) to be used after 10 minutes. This group contains distribution points DP\_B1 and DP\_B2. Both are well connected to the first group's boundary locations.
- Configure the second *neighbor* group \(BG\_C\) to be used after 20 minutes. This group contains distribution points DP\_C1 and DP\_C2. Both are across a WAN from the other two boundary groups.
- Also add to the default site boundary group another distribution point that's on the site server. This server is your least preferred content source location, but it's centrally located to all your boundary groups.

  Example of boundary groups and fallback times:

  [![Conceptual diagram of example boundary groups and fallback times.](https://learn.microsoft.com/en-us/intune/configmgr/core/servers/deploy/configure/media/boundary-group-fallback.png)](https://learn.microsoft.com/en-us/intune/configmgr/core/servers/deploy/configure/media/boundary-group-fallback.png#lightbox)

With this configuration:

- The client begins searching for content from distribution points in its *current* boundary group \(BG\_A\). It searches each distribution point for two minutes, and then switches to the next distribution point in the boundary group. The client's pool of valid content source locations includes DP\_A1 and DP\_A2.
- If the client fails to find content from its *current* boundary group after searching for 10 minutes, it then adds the distribution points from the BG\_B boundary group to its search. It then continues to search for content from a distribution point in its combined pool of servers. This pool now includes servers from both the BG\_A and BG\_B boundary groups. The client continues to contact each distribution point for two minutes, and then switches to the next server in its pool. The client's pool of valid content source locations includes DP\_A1, DP\_A2, DP\_B1, and DP\_B2.
- After another 10 minutes \(20 minutes total\), if the client still hasn't found a distribution point with content, it expands its pool to include available servers from the second *neighbor* group, boundary group BG\_C. The client now has six distribution points to search: DP\_A1, DP\_A2, DP\_B2, DP\_B2, DP\_C1, and DP\_C2. It continues changing to a new distribution point every two minutes until it finds content.
- If the client hasn't found content after a total of 120 minutes, it falls back to include the *default site boundary group* as part of its continued search. Now the pool includes all distribution points from the three configured boundary groups, and the final distribution point located on the site server. The client then continues its search for content, changing distribution points every two minutes until content is found.

By configuring the different neighbor groups to be available at different times, you control when specific distribution points are added as a content source location. The client uses fallback to the default site boundary group as a safety net for content that isn't available from any other location.

## Next steps

[Procedures for boundary groups](https://learn.microsoft.com/en-us/intune/configmgr/core/servers/deploy/configure/boundary-group-procedures)
