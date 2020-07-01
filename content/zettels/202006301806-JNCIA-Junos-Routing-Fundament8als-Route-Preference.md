---
title: "JNCIA Junos | Routing Fundamentals: Route Preference"
date: 2020-06-30T18:06:17-05:00
draft: false
type: "zettel"
tags:
  - JNCIA-Junos
  - Junos
  - Juniper
  - Networking
id: 
  - "5"
---
## Route Preference
Route preference, also called Administrative Distance, is used by the router to determine the preferred route for a destination prefix. The lower the route preference the more preferred the route is. 

**Route preference values**:

  * **Direct**: 0
  * **Local**: 0
  * **Static**: 5
  * **OSPF Internal**: 10
  * **RIP**: 100
  * **OSPF AS external**: 150
  * **BGP (both EBGP and IBGP)**: 170

When a prefix has equal cost for multiple preferences, the `rpd` (routing protocol daemon) will randomly select one of the paths. 

You can configure per-flow load balancing by using a routing policy as well. 

## References
  * [Juniper Open Learning: Junos, Associate](https://cloud.contentraven.com/junosgenius/learningpath-detail/1004/3/0/1)
