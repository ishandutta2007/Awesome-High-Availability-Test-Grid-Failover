# Awesome-High-Availability-Test-Grid-Failover

# Top High Availability & Test Grid Failover Ecosystem

**Curated List of SaaS Platforms & Open-Source GitHub Projects**  
*Focused on DNS Failover, Global Server Load Balancing & Self-Hosted Resilience Orchestration*  
**Last updated: March 2026**

This repository tracks notable **SaaS platforms** and **open-source projects** for **High Availability & Test Grid Failover**. These tools help organizations keep test infrastructure and applications reachable when a region, cluster, or component fails—covering everything from managed DNS failover and global server load balancing to open-source chaos engineering tools that deliberately break things to prove failover actually works.

**Examples** include AWS Route 53, Cloudflare Load Balancing, Azure Traffic Manager, NS1, F5 BIG-IP DNS, K8gb, Krkn, and Rota (the category leaders).

**Open-source emphasis**: This section highlights every major active project for self-hosted global server load balancing, open-source chaos engineering, and community-driven failover validation—ideal for teams seeking data sovereignty and avoiding per-query or per-endpoint SaaS pricing. The open-source landscape is genuinely functional: **K8gb** is a CNCF-incubating Kubernetes-native GSLB solution used in production by Millennium bcp with 99.99% uptime , **Krkn** is a CNCF sandbox chaos tool for validating failover behavior , and **Rota** provides high-throughput proxy rotation with health checks for failover between proxy pools .

Contributions welcome! Open an PR to add/update entries. Keep descriptions factual and link to official sites.

## Table of Contents
- [SaaS/Hosted Platforms](#saas-products)
- [Open-Source GitHub Projects](#open-source-github-projects)
- [How to Contribute](#how-to-contribute)
- [Disclaimer](#disclaimer)

## SaaS/Hosted Platforms

| Product | Description | Pricing (Starting) | Free Tier / Trial Limits |
|---------|-------------|-------------------|--------------------------|
| **[AWS Route 53](https://aws.amazon.com/route53/)** | **The benchmark for DNS-based failover.** Health checks aggregate responses from distributed checkers—**if more than 18% report healthy, the endpoint is considered healthy**; 18% or fewer triggers failover . Supports failover routing, latency-based routing, and geolocation policies. | Hosted zone: ~$0.50/month; health checks: ~$0.50/month each | **Free tier**: 1M queries/month for new AWS accounts (12 months) |
| **[Cloudflare Load Balancing](https://www.cloudflare.com/)** | Global server load balancing with health checks, geo-steering, and failover across origin pools. Integrated with Cloudflare's CDN and DDoS protection. | Quote-only (enterprise); free tier for basic DNS only | **Free**: basic DNS with no load balancing; Enterprise for full GSLB |
| **[Azure Traffic Manager](https://azure.microsoft.com/en-us/products/traffic-manager/)** | DNS-based traffic distribution with priority, weighted, performance, and geographic routing methods. Health checks monitor endpoint availability and automatically fail over. | Pay-per-million DNS queries and health checks | **Free tier**: 1M queries/month and 1,000 health check executions |
| **[NS1 Traffic Steering](https://ns1.com/)** | Enterprise DNS with advanced traffic steering (filter chains), real-time monitoring, and 100% uptime SLA. API-driven for DevOps workflows. | Quote-only (enterprise contract) | No free tier; trial via sales |
| **[F5 BIG-IP DNS](https://www.f5.com/)** | Enterprise GSLB with wide IPs, global availability, and advanced load balancing across data centers and clouds. | Quote-only (appliance or virtual edition) | No free tier; trial via sales |
| **[Google Cloud Load Balancing](https://cloud.google.com/load-balancing)** | Global external load balancing with cross-region failover, health checks, and anycast IPs. | Pay-per-forwarding rule and data processed | **Free tier**: limited usage for new GCP customers |

## Open-Source GitHub Projects

| Project | Star Badge | Description |
|---------|------------|-------------|
| **[K8gb](https://github.com/k8gb-io/k8gb)** | [![Stars](https://img.shields.io/github/stars/k8gb-io/k8gb?style=social&color=white)](https://github.com/k8gb-io/k8gb/stargazers) | **The leading open-source Kubernetes-native Global Server Load Balancing solution.** **CNCF incubating project**, Apache-2.0 . **Automates traffic management and failover across multiple Kubernetes clusters and regions** using standard Kubernetes APIs, CoreDNS, and ExternalDNS . **GSLB Custom Resource** provides a declarative API for configuring global traffic management. **Kubernetes-native health checks** rely on pod liveness and readiness probes for intelligent routing decisions. **Production-proven**: Millennium bcp (Portugal's largest privately owned bank) achieved **99.99% service uptime** across critical banking applications after adoption . **1,197 GitHub stars, 239 contributors, 105 organizations** . **Best for Kubernetes teams wanting vendor-neutral, multi-cluster failover** without commercial GSLB contracts . |
| **[Krkn](https://github.com/krkn-chaos/krkn)** | [![Stars](https://img.shields.io/github/stars/krkn-chaos/krkn?style=social&color=white)](https://github.com/krkn-chaos/krkn/stargazers) | **CNCF sandbox chaos engineering tool for validating failover behavior.** Runs controlled failure scenarios—**pod kill, node kill, time chaos, network chaos**—to prove your failover mechanisms actually work . **Four interfaces**: `krknctl` CLI (recommended, with auto-completion and workflow orchestration), `krkn-hub` container images for CI/CD, Krkn Dashboard (web UI), and standalone Python for full control . **Run external to the cluster**—running inside may be disruptive to itself . **Best for teams wanting to actively break things** to validate HA and failover under realistic failure conditions . |
| **[Rota](https://github.com/alpkeskin/rota)** | [![Stars](https://img.shields.io/github/stars/alpkeskin/rota?style=social&color=white)](https://github.com/alpkeskin/rota/stargazers) | **High-performance self-hosted proxy rotator with health checks and failover.** **Go-based**, handles thousands of requests per second. **Automatic proxy pool management**: health checker removes unhealthy proxies, `remove_unhealthy` keeps the pool clean . **Four rotation methods**: random, round-robin, least-conn, and time-based . **HTTP and SOCKS5** support. **Docker image available** (`ghcr.io/alpkeskin/rota:latest`). **Best for teams wanting failover between proxy pools** in test infrastructure without commercial proxy service fees . |
| **[dosev](https://pypi.org/project/dosev/)** | — | **Multi-protocol DNS resolver and forwarding server with upstream failover.** Supports **UDP, TCP, DoT, DoH (HTTP/1.1, HTTP/2, HTTP/3), and DoQ** as client and server . **Upstream selection strategies**: failover (try in order), parallel (query all, return first success), random, round-robin . **DNSSEC validation, caching, blocklists, and Prometheus metrics** included. **Best for teams wanting a self-hosted DNS resolver with failover** between upstream resolvers . |

### Additional Strong Open-Source Options

| Project | Star Badge | Description |
|---------|------------|-------------|
| **[RouteDNS](https://github.com/folbricht/routedns)** | — | **DNS stub resolver, proxy, and router with failover and load-balancing.** Supports **DoT, DoH, DoQ, and plain DNS** as input and output. **Multiple failover and load-balancing algorithms**; routing based on query name, type, or source address. **Written in Go**, Docker image available . **Best for teams wanting a programmable DNS failover layer** with protocol flexibility . |
| **[NovaEdge](https://github.com/azrtydxb/novaedge)** | — | **Kubernetes-native load balancer and service mesh with multi-cluster federation.** **Health-check based failover** for control-plane VIP; **BGP/BFD mode support** for VIP announcement. **Active and passive health checking**, circuit breaking, and graceful shutdown . **Best for Kubernetes teams wanting integrated load balancing and failover** without separate GSLB tooling . |

**Frameworks for building custom systems**: Choose **K8gb** for Kubernetes-native multi-cluster GSLB with production-proven 99.99% uptime , **Krkn** to validate failover actually works by injecting failures , and **Rota** or **dosev** for proxy/DNS-level failover in test infrastructure —all without per-query or per-endpoint SaaS fees.

## How to Contribute

1. Fork the repo.
2. Add/edit entries in `README.md` (follow existing format).
3. Include: name, link, 1–2 sentence description, and whether it's SaaS or open-source.
4. Submit PR with a short explanation.

Star the repo if you find it useful!

## Disclaimer

- This is a **community-curated** list — not exhaustive and not an endorsement.
- High availability and failover configurations are **safety-critical**; a misconfigured health check can either fail to detect a real outage or trigger a false failover that causes downtime. Test failover procedures in staging before relying on them in production.
- **Failover is not a product you buy—it's a behavior you prove.** **K8gb provides the mechanism** (DNS-based GSLB across clusters) and is production-proven at a major bank with 99.99% uptime , but **Krkn exists because you must actively verify failover works**—inject node kills, network partitions, and pod failures to confirm traffic actually shifts . **Commercial DNS failover (Route 53, NS1) is mature and reliable**, but pricing scales with query volume and health check count. **Open-source alternatives have different trade-offs**: K8gb requires Kubernetes expertise and CoreDNS/ExternalDNS integration , dosev and RouteDNS handle DNS-layer failover but not application-level health , and Rota manages proxy pool failover but not global traffic steering . **Validate whether you need managed DNS failover (Route 53, NS1), Kubernetes-native GSLB (K8gb), or chaos validation of your existing failover (Krkn)** before committing.

---

**Made for SREs, platform engineers, and organizations building resilient test infrastructure.**  
Let's make high availability and test grid failover more open, provable, and cost-predictable.
