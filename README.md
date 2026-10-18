# Awesome-Realtime-Messaging

# Top Realtime Messaging Tools Ecosystem

**Curated List of SaaS Products & Open-Source GitHub Projects**  
*Focused on WebSocket Pub/Sub, Presence Tracking & Postgres Change Data Capture*  
**Last updated: March 2026**

This repository tracks notable **SaaS platforms** and **open-source projects** for **Realtime Messaging**. These tools push data to connected clients instantly — enabling live chat, collaborative editing, real-time dashboards, notifications, and multiplayer experiences — without polling.

**Examples** include Pusher, Ably, PubNub, Supabase Realtime, Centrifugo, Soketi, Mercure, deepstream.io, Firebase, and AWS AppSync (the category leaders).

**Open-source emphasis**: This section is heavily expanded with every major active project for self-hosting, Pusher-protocol compatibility, and transparent WebSocket infrastructure — ideal for developers prioritizing data sovereignty, avoiding per-message SaaS costs, and maintaining control over real-time transport.

Contributions welcome! Open a PR to add/update entries. Keep descriptions factual and link to official sites.

## Table of Contents
- [SaaS/Hosted Platforms](#saas-hosted-platforms)
- [Open-Source GitHub Projects](#open-source-github-projects)
- [How to Contribute](#how-to-contribute)
- [Disclaimer](#disclaimer)

## SaaS/Hosted Platforms

- **[Pusher Channels](https://pusher.com/)**  
  **The reference hosted pub/sub service** with a massive SDK ecosystem and the Pusher protocol that many open-source tools implement. **Free Sandbox plan: 200,000 messages/day, 100 concurrent connections** [citation:2][citation:9]. Paid Startup tier at $49/month. **The strongest free message throughput** for event-heavy applications, though chat-product features are thinner than purpose-built platforms [citation:2]. **Best for teams wanting the least infrastructure work** and straightforward real-time transport.

- **[Ably](https://ably.com/)**  
  **The reliability-focused realtime platform** with a **99.999% uptime SLA** and seven-year history of 100% uptime [citation:16]. **Free package: 200 concurrent connections, 500 messages/second, 6 million messages/month** — the most generous free headroom for message-intensive apps [citation:2][citation:9]. **Channel Groups** support up to 20K channels per socket; **Presence Scaling** supports 20K users per channel [citation:16]. **Trade-offs**: consumption-based pricing ($2.50/million messages, $1.00/million channel minutes) can be complex and expensive for startups [citation:16].

- **[PubNub](https://www.pubnub.com/)**  
  Multi-purpose realtime platform combining messaging, push notifications, and serverless functions. **Free tier: 200 MAU, 1M transactions/month, 1GB storage for 7 days** [citation:9]. **The breadth of channels** (push + functions alongside messaging) is its free-tier advantage, but the 200 MAU cap is low for user-facing apps [citation:2].

- **[Supabase Realtime](https://supabase.com/)**  
  **Globally distributed Elixir/Phoenix cluster** providing **Broadcast, Presence, and Postgres Changes** via WebSockets [citation:1]. **Benchmarked at 224,000 messages/second with 32,000 concurrent users** (median latency 6ms) on a 2-6 node cluster [citation:8]. Postgres Changes streams WAL via logical replication slots with automatic reconnection [citation:1]. **Free tier with usage-based pricing**; open-source and self-hostable.

- **[Firebase Realtime Database](https://firebase.google.com/)**  
  Google's NoSQL realtime database with client SDKs that sync state across devices automatically. Deep integration with Firebase Authentication and Cloud Functions.

- **[AWS AppSync](https://aws.amazon.com/appsync/)**  
  Managed GraphQL service with real-time subscriptions over WebSockets, integrated with DynamoDB, Lambda, and Cognito.

## Open-Source GitHub Projects

- **[Centrifugo](https://github.com/centrifugal/centrifugo)**  
  **The most feature-complete self-hosted realtime messaging server** — Apache 2.0 licensed, **10,800+ GitHub stars** [citation:7]. **Language-agnostic** with official SDKs for JavaScript, Swift, Java/Android, C#, Dart/Flutter, Python, and Go [citation:7]. **Transport flexibility**: WebSocket, HTTP-streaming, Server-Sent Events (SSE), gRPC, and WebTransport [citation:3]. **Built-in scalability** with Redis (or Redis Cluster, Valkey, KeyDB, DragonflyDB) or Nats [citation:3]. **Channel history with automatic recovery on reconnect**, delta compression, presence with join/leave, and **asynchronous PostgreSQL/Kafka consumers for outbox and CDC patterns** [citation:3]. **HTTP and gRPC server API** for backend integration, JWT or proxy authentication, and a beautiful embedded admin UI with Prometheus metrics [citation:3]. **Best for teams wanting a production-grade, self-hosted PubNub/Pusher/Ably alternative** without vendor lock-in.

- **[Soketi](https://github.com/soketi/soketi)**  
  **The Pusher-protocol-compatible self-hosted server** — AGPL-3.0 licensed, **5,600+ GitHub stars** [citation:11]. **Drop-in replacement for Pusher Channels** — existing Pusher SDKs and applications work without code changes [citation:4]. **Written in Node.js/TypeScript** with a Rust adapter for performance. **Deployable via Docker, Cloudflare Workers, or bare Node.js** [citation:4]. **Best for teams already using Pusher SDKs** who want to migrate to self-hosting without rewriting client code.

- **[Mercure](https://github.com/dunglas/mercure)**  
  **The standards-based SSE pub/sub hub** — AGPL-3.0 licensed, **5,000+ GitHub stars** [citation:5][citation:12]. **Hub-based publish/subscribe protocol over HTTP and Server-Sent Events (SSE)** — designed for server-to-client real-time updates [citation:5]. **Spec stabilized for 1.0** with refreshed Internet-Draft, using **OAuth 2.0 Rich Authorization Requests** and **WHATWG URL Pattern** instead of bespoke machinery [citation:5]. **SSE-native** — the same transport used by OpenAI, Anthropic, and MCP for token streaming — with authorization, multiplexing, discovery, and reconnection that ad-hoc SSE lacks [citation:5]. **First-class integration in Symfony, API Platform, Laravel, and FrankenPHP** [citation:5]. **Best for PHP/Symfony ecosystems** and applications where SSE is preferred over WebSockets.

- **[deepstream.io](https://github.com/deepstreamIO/deepstream.io)**  
  **The realtime server with records, events, and RPC** — MIT licensed, **7,100+ GitHub stars** [citation:6]. **Three core primitives**: schema-less persistent documents (records) that sync across clients, topic-based events for many-to-many messaging, and remote procedure calls with load-balancing and failover [citation:13]. **Valve permission language** for fine-grained authorization [citation:13]. **Connectors for PostgreSQL, MongoDB, Redis, and Memcached** [citation:6]. **Best for applications needing realtime data sync plus RPC** in one server.

### Additional Strong Open-Source Options

- **Socket.IO** — The most widely used WebSocket library for Node.js with fallback transports and rooms. Huge ecosystem.
- **Centrifuge** — The Go library powering Centrifugo. Use it to embed realtime WebSocket support directly in Go applications [citation:7].
- **Mercure.rocks Hub** — Managed high-scalability Mercure hub for teams wanting the protocol without self-hosting [citation:12].
- **Nchan** — Nginx module for pub/sub over WebSocket, SSE, and long-polling.

**Frameworks for building custom systems**: Combine **Centrifugo** for a full-featured self-hosted pub/sub server with multi-transport support and Redis clustering, **Soketi** for drop-in Pusher compatibility without rewriting SDK code, **Supabase Realtime** for Postgres-native CDC and Broadcast at scale, **Mercure** for standards-based SSE where WebSockets aren't required, and **deepstream.io** for realtime records plus RPC — to build a realtime messaging layer tailored to your transport preferences, existing SDK ecosystem, and infrastructure constraints.

## How to Contribute

1. Fork the repo.
2. Add/edit entries in `README.md` (follow existing format).
3. Include: name, link, 1–2 sentence description, and whether it's SaaS or open-source.
4. Submit PR with a short explanation.

Star the repo if you find it useful!

## Disclaimer

- This is a **community-curated** list — not exhaustive and not an endorsement.
- Realtime messaging tools differ significantly in transport support, free-tier limits, and operational complexity. **Pusher's free tier offers 200K messages/day** — the strongest daily message allowance [citation:2]. **Ably's free tier offers 6M messages/month and 200 concurrent connections** — the most headroom before paying [citation:9]. **PubNub's free tier caps at 200 MAU**, which is restrictive for user-facing apps [citation:9]. **Centrifugo is the most feature-complete self-hosted option** with multi-transport support, Redis clustering, and CDC consumers [citation:3]. **Soketi is the drop-in Pusher replacement** but its last release was March 2025 — evaluate maintenance activity [citation:11]. **Mercure's SSE approach is standards-based** and aligns with AI streaming patterns, but SSE is one-way server-to-client [citation:5]. **Supabase Realtime's benchmarks are cluster-dependent** — production performance varies with network and hardware [citation:8].
- Self-hosted open-source solutions require proper Redis/Nats configuration for horizontal scaling, WebSocket-aware load balancers, and monitoring of connection counts and message throughput.

---

**Made for developers, platform engineers, and teams building real-time collaborative and live-update applications.**
Let's make realtime messaging more open, self-hostable, and transport-flexible.
