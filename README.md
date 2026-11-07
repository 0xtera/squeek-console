# Squeekchain Aura & Merge Console

A read-only holder console for **Squeekchain** (Sepolia, chainId 11155111).

It reads the Squeekchain core API and the community API and shows, in one screen:

- **Chain** — target, chain id, indexed block, current round, core height, whether merges are open, max level
- **Power** — `nftPower`, `sqkPower` and their total
- **Stake & rewards** — principal / fresh / mature stake, claimable SQK, lifetime paid
- **Squeeks** — every token, its level, custody and merge state (with the exact block the next merge opens)
- **Leaderboard** — top 10 by Aura
- **Top collections** — holder collections ranked by their Aura bonus
- **Genesis** — member count, badges earned, verified projects, total Aura

No private keys. No write transactions. Nothing is signed or sent on-chain.

## Live

<https://squeek.hexarin.site>

## How it is served

The page is a static HTML file. A small Python server on `:443` serves it and
proxies the upstream APIs **same-origin**, because the community API does not
send `Access-Control-Allow-Origin` for third-party domains — a direct
browser fetch to `community.squeekchain.com` would be blocked by CORS.

| Route | Upstream |
|---|---|
| `/api/core/accounts/<address>` | `https://api.squeekchain.com/v1/accounts/<address>` |
| `/api/community/<path>` | `https://community.squeekchain.com/v1/community/<path>` |
| `/api/wheel` | `https://squeek.win/api/wheel` |

TLS comes from Let's Encrypt via DNS-01; renewal is automated.

## Contracts

| Contract | Address |
|---|---|
| Squeeks NFT | `0xc4c7982657f00509548f3a3a41db7fa439a6856b` |
| SqueekStaking | `0x50fd1780526c3186a0c037c7622203bc4fb611ca` |
| SQK | `0xd78a3956cf63164d1fa1c622ad3c66623162fa1e` |

## Data sources

- `https://api.squeekchain.com`
- `https://community.squeekchain.com/v1/community`

## Verification

```text
squeekchain-project: 9c965bfc-9bf4-4771-8806-bebb1c0ea7c7
```
