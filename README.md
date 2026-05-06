# cn402

**China Data Gateway for AI Agents** · 中国数据 · 直供 AI 代理

Pay-per-call APIs designed for autonomous agents. Built on the [X402 protocol](https://github.com/x402-foundation/x402) — settled in USDC on Base, no accounts, no API keys, no subscriptions.

🌐 **Live**: [cn402.com](https://cn402.com)

## Endpoints

| Endpoint | Price | Description | Status |
|---|---|---|---|
| `GET /forex` | $0.03 | Real-time FX rates — USDCNY and major pairs (ECB reference data) | ✅ Live |
| `GET /holiday` | $0.01 | China official holidays & workday lookup with makeup days | 🚧 Planned |
| `GET /astock` | $0.10 | A-share market snapshot — SSE/SZSE indices, northbound flow | 🚧 Planned |
| `GET /crypto` | $0.05 | Multi-asset crypto snapshot with RSI/MA technical indicators | 🚧 Planned |

## Quick Start

Without payment — receive 402 with payment terms:

    curl https://api.cn402.com/forex?pair=USDCNY

With X402 client (TypeScript example):

    import { wrapFetchWithPayment } from "x402-fetch";
    const fetchWithPayment = wrapFetchWithPayment(fetch, walletClient);
    const res = await fetchWithPayment("https://api.cn402.com/forex?pair=USDCNY");

## Why cn402

Most agent-facing APIs are US-centric. cn402 closes the China data gap — A-share quotes, CNY rates, mainland holidays — priced for the high-frequency consumption pattern of autonomous agents, settled trustlessly on Base.

## Tech Stack

- **Protocol**: x402 (HTTP 402 Payment Required) + EIP-3009
- **Settlement**: USDC on Base mainnet via Coinbase CDP facilitator
- **Server**: Node.js + Express + `x402-express`
- **Site**: Astro on Cloudflare Workers
- **Wallet**: `0x4466d4A84b7c49a6A094ec6eef4a0712D6dd125e`

## First Live Transaction

`/forex` first paid call on Base mainnet:

[basescan.org/tx/0x96e74c68...d3a25d](https://basescan.org/tx/0x96e74c68b401fbddf2d73755d35ae082bb845132fd5c827a7674e73d8ed3a25d)

## License

MIT — feel free to fork, learn, build on top.

---

Built solo. Questions / collab: business@cn402.com (coming soon)