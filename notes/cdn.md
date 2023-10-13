---
id: oqfs3y0jx2k1q2px7gt9g6f
title: cdn
desc: ''
updated: 1697218287211
created: 1697218051447
---

- a CDN serves only content?? that means the link to a resource is specified AS WHAT in the code that serves people from different geographic locations??
- that means the same picture will be on many different servers? how will they be identified uniquely throughout the server network?
- how does a CDN relate to a [[load balancer]]?
- "Your servers do not have to serve requests that the CDN fulfills"
- How do you even CDN??
  - [The 5-Hour CDN](https://news.ycombinator.com/item?id=28053168)
  - [Set up a practically free CDN](https://news.ycombinator.com/item?id=29947320)
- Kleppman: "Consistent hashing, as defined by Karger et al. [7], is a way of evenly distributing load across an internet-wide system of caches such as a content delivery network (CDN). It uses randomly chosen partition boundaries to avoid the need for central control or distributed consensus. Note that consistent here has nothing to do with replica consistency (see Chapter 5) or ACID consistency (see Chapter 7), but rather describes a particular approach to rebalancing. As we shall see in “Rebalancing Partitions” on page 209, this particular approach actually doesn’t work very well for databases [8], so it is rarely used in practice (the documentation of some databases still refers to consistent hashing, but it is often inaccurate). Because this is so confusing, it’s best to avoid the term consistent hashing and just call it hash partitioning instead."
