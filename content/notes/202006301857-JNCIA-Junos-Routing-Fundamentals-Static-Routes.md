---
title: "JNCIA Junos | Routing Fundamentals: Static Routes"
date: 2020-06-30T18:57:38-05:00
tags:
  - JNCIA-Junos
categories:
  - Certifications
  - Juniper
  - Networking
---
## Notes

Static routes, or manually entered routes, require at a minimum to be defined as static and associate a next-hop address for the route.

To create a static route issue the following: `set routing-options static route <destination> next-hop <value>`

Instead of setting the next-hop address or interface, you can also set traffic destined for a prefix to be either rejected or dropped. Reject will send an ICMP unreachable message back to the source while *discard* will not.

It is a best practice to use the `no-readvertise` option on static routes that must go out the management interface. This prevents them from being advertised throughout the routing tables of the other routers on the network.

To verify use: `show route protocol static`

## References

* [Juniper Open Learning: Junos, Associate](https://cloud.contentraven.com/junosgenius/learningpath-detail/1004/3/0/1)
* [Configuring Static Routes](https://www.juniper.net/documentation/en_US/junos/topics/topic-map/policy-static-routing.html)
