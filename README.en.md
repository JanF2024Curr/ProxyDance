<p align="center">
  <img src="docs/icon-blue128.png" width="96" alt="ProxyDance" />
</p>

<h1 align="center">ProxyDance</h1>

<p align="center">
  Lightweight proxy switching × privacy diagnostics · Chrome MV3 extension
</p>

<p align="center">
  <a href="README.md">中文</a> | <a href="README.en.md">English</a>
  <br/>
  <img src="https://img.shields.io/badge/license-GPL--3.0-blue" alt="License: GPL-3.0" />
  <img src="https://img.shields.io/badge/Chrome-Manifest%20V3-4285F4" alt="Chrome MV3" />
  <img src="https://img.shields.io/badge/TypeScript-strict-3178C6" alt="TypeScript strict" />
  <img src="https://img.shields.io/badge/runtime%20dependencies-0-success" alt="Zero runtime dependencies" />
</p>

---

ProxyDance switches your browser between direct connection and your own proxy server (HTTP / HTTPS / SOCKS4 / SOCKS5) in one click, with a built-in network health check in the popup: egress IP health, DNS leak test, and connectivity to popular sites. **It does not provide or sell proxies, and collects no user data.**

## Screenshots

<p align="center">
  <img src="docs/popup.png" width="360" alt="Popup" />
  <img src="docs/options.png" width="480" alt="Options" />
</p>

## Features

- **One-click switching** — Instant Direct / Proxy toggle; the toolbar icon color shows where the current site's traffic goes (whitelisted sites flip back to the direct color automatically)
- **IP health** — Egress IP, region, ISP / ASN, plus an "IP purity" rating that flags datacenter / proxy IPs likely to be risk-blocked by streaming and AI services
- **DNS leak test** — Verifies domain resolution happens on the proxy side, listing the resolvers actually used in resolution order, with their regions
- **Site connectivity** — Reachability, latency and restriction status for Google, YouTube, X, ChatGPT and Claude
- **Cloudflare speed test** — Optional download speed sampling
- **Wildcard direct whitelist** — `*.example.com` syntax; the PAC is generated safely by the extension (patterns are whitelist-validated, no script injection)
- **Config import / export**, **English / 中文 UI**, **dark mode**

## Inspiration & Improvements

ProxyDance is inspired by the classic proxy switcher [SwitchyOmega](https://github.com/FelisCatus/SwitchyOmega) (22k+ stars) — many thanks to [FelisCatus](https://github.com/FelisCatus) and its community. This project is an **independent implementation, not a fork**.

How it differs:

| | SwitchyOmega | ProxyDance |
|---|---|---|
| Scope | Full proxy manager (multi-profile, rule-based auto switching) | Single proxy + network health check, focused and light |
| Architecture | Manifest V2, **no longer maintained** | **Manifest V3**, actively maintained |
| Privacy checks | None | IP purity rating, DNS leak test, site connectivity |
| Size | Large project | ~1,500 lines of TypeScript, zero runtime dependencies |

Feature Comparison: **SwitchyOmega answers "how do I switch"; ProxyDance also answers "is my egress environment clean after switching".**

## Installation
**Option 1: Chrome Web Store Extension** (recommended)

[Chrome Web Store](https://chromewebstore.google.com/category/extensions): Submission is currently under review. Stay tuned!

**Option 2: Download a release**

1. Download the latest `proxydance-*.zip` from [Releases](https://github.com/JanF2024Curr/ProxyDance/releases) and unzip it
2. Open `chrome://extensions` and enable **Developer mode**
3. Click **Load unpacked** and select the unzipped folder


## Quick Start

1. **Configure** — Open the settings page, enter your proxy server address and port, save
2. **Switch** — Click the toolbar icon and toggle Proxy / Direct in the popup
3. **Detect** — Click "Detect Now" to check IP health, DNS leaks and site connectivity

> Note: Chrome MV3's PAC mechanism does not support proxy authentication. For proxies requiring username / password, allowlist your egress on the server side, or use a local converter (e.g. gost / clash mixed port).

## Privacy

ProxyDance **collects, stores and uploads no user data**. Detection requests (including your egress IP) are sent — only when you click "Detect Now" — directly to these third-party services:

| Service | Purpose |
|---|---|
| ipwho.is / ipinfo.io | IP geolocation and ASN lookup |
| bash.ws | DNS leak test |
| speed.cloudflare.com | Optional speed test |


## License

[GPL-3.0](LICENSE) © ProxyDance contributors

## Acknowledgements

- [FelisCatus/SwitchyOmega](https://github.com/FelisCatus/SwitchyOmega) — the classic proxy switcher; this project's product shape is directly inspired by it
- [bash.ws](https://bash.ws) / [ipwho.is](https://ipwho.is) / [ipinfo.io](https://ipinfo.io) / [Cloudflare](https://www.cloudflare.com) — free detection services
