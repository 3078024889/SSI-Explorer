# SSI Explorer

On-chain dashboard for [SoSoValue's SSI Protocol](https://ssi.sosovalue.com) on Base. Every number on the page is read live — nothing is hardcoded or simulated.

## What it does

- **Live index prices** — MAG7.ssi, DEFI.ssi, MEME.ssi, USSI prices, 24h change, and volume, pulled from live Base Uniswap pools via the public DexScreener API, auto-refreshing every 20s
- **Live Mint/Redeem activity** — scans real `Transfer` events on each token contract via `eth_getLogs`, flags transfers to/from the zero address as mints/redeems, auto-refreshing every 25s
- **Live portfolio lookup** — real `balanceOf()` calls against all 4 index token contracts for any address you enter
- **Live block height** — real Base chain block number, refreshed every 12s
- **Contract registry** — verified Base-mainnet addresses for AssetFactory, AssetIssuer, Rebalancer, FeeManager, Swap, AssetLocking, and all 4 index tokens, linking to BaseScan

## Why it was rebuilt

An earlier version of this project pointed to Ethereum mainnet / Etherscan and used placeholder contract addresses, while SSI Protocol is actually deployed on **Base**. Index prices and the Mint/Redeem feed were also hardcoded/simulated rather than read from chain. This version fixes both: correct chain, correct contract addresses (sourced from SoSoValue's official docs), and every data point backed by a live RPC or API call.

## Data sources

- Base RPC (`mainnet.base.org`, with `base.llamarpc.com` / `base-rpc.publicnode.com` as fallbacks)
- [DexScreener public API](https://docs.dexscreener.com) for pool price/volume
- No API key required, no proprietary key exposed in client code

## Tech stack

Single-file vanilla HTML/CSS/JS — no build step, no framework. Deploy anywhere static files are served.

## Run it

Just open `index.html` in a browser, or serve the folder with any static file host.
