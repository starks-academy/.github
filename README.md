# Stacks Academy

> AI-powered learning for Bitcoin builders on Stacks L2. Learn Clarity, build with sBTC, and earn a verifiable NFT certificate — secured by Bitcoin.

![Stacks](https://img.shields.io/badge/Network-Stacks%20L2-5546FF?style=flat-square) ![Bitcoin](https://img.shields.io/badge/Secured%20By-Bitcoin-F7931A?style=flat-square) ![License](https://img.shields.io/badge/License-MIT-00D4AA?style=flat-square)

---

## The Problem

Developer onboarding is Stacks' biggest growth bottleneck. Learning resources are scattered, there's no AI-guided curriculum, and no standardized way to prove you're a real Stacks builder.

## The Solution

Stacks Academy combines structured learning paths, an AI tutor, and on-chain NFT certificates into one platform.

```
Learn → Practice in Clarity Playground → Pass AI Assessment (80%+) → Mint NFT Certificate
```

---

## Features

- **4 Learning Paths** — Stacks Fundamentals, Clarity Contracts, sBTC & DeFi, Capstone Project
- **AI Tutor** — Claude-powered assistant for real-time Q&A and Clarity code review
- **Clarity Playground** — Write and test smart contracts in-browser, no setup needed
- **AI-Graded Assessments** — Score 80%+ to qualify for certification
- **NFT Certificates** — SIP-009 NFTs minted to your Stacks wallet, Bitcoin-finalized
- **Builder Gallery** — Public leaderboard of verified Stacks developers with on-chain badges
- **Gamification** — XP, levels, streaks, and milestone rewards

---

## NFT Certificate Contract

```clarity
(define-non-fungible-token stacks-cert uint)

(define-public (mint-certificate (course (string-ascii 64)) (grade uint))
  (let ((token-id (+ (var-get last-token-id) u1)))
    (asserts! (>= grade u80) (err u401))   ;; 80% minimum enforced on-chain
    (try! (nft-mint? stacks-cert token-id tx-sender))
    (map-set cert-metadata { token-id: token-id }
      { owner: tx-sender, course: course, grade: grade, timestamp: block-height })
    (ok token-id)
  )
)
```

Certificates are immutable, Bitcoin-anchored, and composable — DAOs and protocols can gate access by cert ownership.

---

## Tech Stack

| | |
|---|---|
| Frontend | React + Tailwind CSS |
| AI Tutor | Anthropic Claude API |
| Contracts | Clarity + Clarinet |
| Wallet | Stacks.js + Leather |
| NFT Standard | SIP-009 |
| Storage | IPFS |

---

## Getting Started

```bash
git clone https://github.com/your-username/stacks-academy
cd stacks-academy && npm install
npm run dev
```

```bash
# Contract development
clarinet check && clarinet test
```

---

## Roadmap

- **Now** — Core platform, AI tutor, NFT certs, builder gallery
- **Next** — $LEARN reward token (SIP-010), peer code review, Discord verification bot
- **Later** — DAO governance for curriculum, job board gated by cert tier, mobile app

---

## Links

- [Live Demo](https://stacks-academy.xyz)
- [Stacks Docs](https://docs.stacks.co)

---

<div align="center">Built on Stacks · Secured by Bitcoin</div>
