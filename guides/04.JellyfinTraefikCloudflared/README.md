# 🔐 Secure Jellyfin Deployment with Traefik, Docker & Cloudflare Tunnel

This project demonstrates how I securely expose [Jellyfin](https://jellyfin.org) to the internet using:

- 🌀 **Cloudflare Tunnel** — No port forwarding, zero-trust-style ingress
- 🛡️ **Traefik v3** — Reverse proxy with TLS, smart routing, and middleware
- 📦 **Docker** — Easy, repeatable deployment
- 📊 **Grafana** — Real-time monitoring
- 🧠 **Pi-hole / Internal DNS** — Clean domain-based routing for internal services

> ✅ Designed for homelabs, small businesses, and self-hosters who want **secure remote access** to internal services — without compromising on observability or hygiene.

---

## 🗺️ Architecture Overview

![Architecture Diagram](docs/architecture-diagram.png)

| Component     | Role                              |
|---------------|-----------------------------------|
| Jellyfin      | Media server                      |
| Traefik v3    | Reverse proxy + HTTPS termination |
| Cloudflared   | Secure tunnel to Cloudflare       |
| Docker        | Container orchestration           |
| Pi-hole       | Internal DNS                      |
| Grafana       | Metrics and observability         |

### Flow Summary

1. External requests hit `jlyfn.example.com` (Cloudflare Tunnel)
2. Tunnel forwards request to Traefik (on another machine)
3. Traefik routes `jlyfn.example.com` → `jelly.example.com` (the internal hostname)
4. Jellyfin responds, and metrics are piped to Grafana
5. Internal DNS resolution is handled by Pi-hole or AD DNS

---

## 🛠️ Project Layout

jellyfin-secure/
├── docker-compose.yml
├── traefik/
│ ├── traefik.yml
│ └── dynamic.yml
├── cloudflare/
│ └── config.yml
├── .env.example
├── docs/
│ ├── architecture-diagram.png
│ └── tunnel-flow.md
└── screenshots/
  ├── jellyfin-ui.png
  ├── grafana-dashboard.png

---

## 🚀 Deployment

1. Clone the Jellyfin folder found in this repo
2. Copy `.env.example` to `.env` and add your `TUNNEL_TOKEN`  
3. Start it all:

``` bash

 docker compose up -d

```

---

## ✨ Features

🔐 No open ports — all traffic tunnels through Cloudflare securely

🛡️ Middleware-enhanced Traefik: Secure headers, TLS, and access control

🎨 Smart DNS naming: jf01.truenas.jjfab.xyz style for traceability

📊 Metrics-first: Everything visible via Grafana

🤖 Self-healing: Containers auto-restart, token-driven tunnels reconnect

📚 Blog Post

➡️ **Coming Soon**

## 🙋 Why?

Because exposing internal services shouldn't mean exposing your home IP, opening ports, or compromising on security.

This project taught me more about:

Reverse proxies

DNS flow logic

Traefik internals

Container networking

Real-world ops problem-solving

### 💬 Contact

Built and maintained by @JJFABxIT
