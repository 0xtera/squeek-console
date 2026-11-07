# Squeekchain Aura & Merge Console

Read-only console for a Squeekchain holder. It reads the Squeekchain core API
and the `SqueekStaking` contract and shows, in one screen:

- SQEEK levels (L1/L2/L3) and per-token status (idle / staking / cooldown)
- the exact block height when two Squeeks can be merged (`nextMergeHeight`)
- total `nftPower` and claimable SQK balance
- Aura, rank, tier and earned badges
- live leaderboard top 10

No private keys. No write transactions. Everything is fetched read-only.

## Run

```bash
python3 -m http.server 80 --directory .
```

Then open `http://<host>/`.

## Contracts (Sepolia, chainId 11155111)

| Contract | Address |
|---|---|
| Squeeks NFT | `0xc4c7982657f00509548f3a3a41db7fa439a6856b` |
| SqueekStaking | `0x50fd1780526c3186a0c037c7622203bc4fb611ca` |
| SQK | `0xd78a3956cf63164d1fa1c622ad3c66623162fa1e` |

## Data sources

- `https://api.squeekchain.com`
- `https://community.squeekchain.com/v1/community`

Live: https://squeek.hexarin.site

## Verification

```
squeekchain-project: 9c965bfc-9bf4-4771-8806-bebb1c0ea7c7
```
