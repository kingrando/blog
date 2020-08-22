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

To create a static route issue the following:

```bash
# Command
set routing-options static route <destination> next-hop <value>
# Example
set routing-options static route 0.0.0.0/0 next-hop 10.0.0.1
```

Instead of setting the next-hop address or interface, you can also set traffic destined for a prefix to be either rejected or discarded. Reject will send an ICMP unreachable message back to the source while *discard* will not.

```bash
# Command
set routing-options static route <destination> discard
set routing-options static route <destination> reject
# Example
set routing-options static route 10.0.0.0/24 discard
set routing-options static route 10.0.0.0/24 reject
```

It is a best practice to use the `no-readvertise` option on static routes that must go out the management interface. This prevents them from being advertised throughout the routing tables of the other routers on the network.

```bash
# Command
set routing-options static route <destination> no-readvertise
# Example
set routing-options static route 10.0.0.0/24 no-readvertise
```

To verify use: `show route protocol static`

```bash
# Command
show route protocol static
# Output
kameron@RE4> show route protocol static

inet.0: 18 destinations, 18 routes (18 active, 0 holddown, 0 hidden)
+ = Active Route, - = Last Active, * = Both

192.168.5.0/24    *[Static/5] 4w3d 19:04:25
                    > to 192.168.30.1 via fxp0.0
192.168.25.0/24    *[Static/5] 4w3d 19:04:25
                    > to 192.168.30.1 via fxp0.0

Test-Instance.inet.0: 6 destinations, 6 routes (6 active, 0 holddown, 0 hidden)

inet6.0: 1 destinations, 1 routes (1 active, 0 holddown, 0 hidden)

Test-Instance.inet6.0: 1 destinations, 1 routes (1 active, 0 holddown, 0 hidden)
```

## References

* [Juniper Open Learning: Junos, Associate](https://cloud.contentraven.com/junosgenius/learningpath-detail/1004/3/0/1)
* [Configuring Static Routes](https://www.juniper.net/documentation/en_US/junos/topics/topic-map/policy-static-routing.html)
