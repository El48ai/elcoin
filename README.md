# ElCoin

**Educational blockchain simulator** — built with plain HTML/CSS/JS, no backend, runs entirely in your browser.

Live demo: hosted on GitHub Pages.

---

## ⚠️ Important: this is a simulation

ElCoin is a **learning project**, not a real cryptocurrency. The coins have **no real-world value** and cannot be sent to anyone else's device. A static page on GitHub Pages physically cannot process real-money transactions, because:

- GitHub Pages only serves static files — there is no server to validate or settle anything.
- "Decentralized" requires many independent computers (nodes) running consensus. This demo has exactly one node: your browser.
- The ledger lives only in your browser's `localStorage` and is shared with no one.

## What IS real in this version

Even though it's a simulation, the cryptography is genuine:

- **Real keypairs** — ECDSA on the P-256 curve via the Web Crypto API. Your address is derived from a SHA-256 hash of your public key (same idea as Bitcoin).
- **Digitally signed transactions** — every transfer is signed with your private key and **verified** before it can enter the mempool or a block. Forged or unfunded transactions are rejected.
- **Chain-derived balances** — balances are computed by replaying the whole chain, not stored in a single editable number.
- **Proof of Work** — SHA-256 mining with adjustable difficulty.
- **Tamper detection** — the integrity check recomputes every block hash, verifies the links, the PoW, and all signatures.
- **XSS-hardened** — recipient addresses are format-validated and all user content is HTML-escaped before rendering.
- **Persistence** — wallet and chain survive page reloads.

## How to use

1. Open the page — a wallet and genesis block are created automatically.
2. **MINE** tab → mine blocks to earn ELC.
3. **SEND** (sidebar) → enter a valid `ELC...` address, amount, fee → it signs and broadcasts to the mempool.
4. Mine again to confirm pending transactions into a block.
5. **RESET BLOCKCHAIN** wipes everything and starts a fresh genesis.

> ⚠️ Your private key is stored in plain text in your browser's `localStorage`. Fine for a demo; never reuse this key anywhere real.

## If you genuinely want real on-chain transactions

You cannot get there by editing this HTML file. The real path is to deploy a **token on an existing blockchain** and connect a frontend to it:

1. **Learn first, free:** write an ERC-20 smart contract (Solidity) and deploy it to a **test network** (e.g. Sepolia). Test ETH is free from faucets, so this costs nothing and is the right place to experiment.
2. **Wallet integration:** connect your site to MetaMask using `ethers.js`. Real signatures, real testnet transactions you can see on a block explorer.
3. **Mainnet (real value):** deploying to a real chain costs real gas fees, and **issuing a token has real legal/regulatory implications** — in Indonesia crypto assets are regulated (OJK/Bappebti). Understand the rules before doing anything with real money.

For most people the testnet route gives you everything that feels "real" — real wallets, real signatures, a public explorer — without spending money or taking legal risk.

## Tech

Vanilla JS · Web Crypto (ECDSA P-256, SHA-256) · Canvas · `localStorage` · Google Fonts (Orbitron, Share Tech Mono, Exo 2)
