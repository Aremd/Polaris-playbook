# Polaris Operational Playbook

A 7-layer operational framework for Polaris Finance — built from real testnet practice.

**Live:** [aremd.github.io/Polaris-playbook](https://aremd.github.io/Polaris-playbook/)

---

## What this is

A standalone interactive playbook for practicing and operating on Polaris Finance. It covers the full decision loop: reading market conditions, selecting a strategy, executing actions, and managing open positions through changing conditions.

It was built during testnet practice on Sepolia (March 2026) by a real user — not assembled from documentation. The thresholds, decision trees, and observations reflect what actually happens when you use the protocol.

---

## What it covers

**Layer 0 — Scenario library**
Real observed conditions matched to a strategy and an Action #1. Built from sessions J+12→J+28 on Sepolia. Five scenarios: normal conditions, NBR rising (yield squeeze), ETH drop (LTV pressure), pUSD depeg, and floor pETH rising (Loop window). Each card shows the signal fingerprint, matched strategy, and numbered steps.

**! Misreads — Common misreads**
Six recurring interpretation errors confirmed across testnet sessions. Each one documents the wrong read, the correct read, the reflex to develop, and the consequence of the error. Covers: LTF ≠ liquidation threshold, LTV ≠ LTF, TCR drop ≠ personal liquidation, pETH Gain = 0 ≠ system quiet, SP APY rising ≠ danger, NBR ≠ IR controller.

**Layer 1 — Context reading**
Two reading modes depending on your situation. MONITORING mode (open positions → am I safe?) and DECISION mode (no position → is now the right time to act?). Daily routine in under 15 minutes, weekly review in under 30.

**Layer 2 — Strategies**
Four strategies with full decision trees, optimal context, key indicators, and entry/exit triggers:
- **SP First** — recurring yield on pUSD via the Stability Pool
- **Leverage Loop** — recursive pETH/ETH leverage via ETH Loan (testnet mechanics, subject to change before mainnet)
- **Bonding Curve Arb** — capturing the market/floor spread (calibrated: 0.31% slippage / +0.73% floor impact on 50 ETH)
- **Defensive** — capital preservation under stress

**Layer 3 — Metrics circuit**
The causal chain that connects ETH price to your net yield: ETH spot → Oracle → LTV (CDP) → TCR → IR controller → Net Borrow Rate → SP APY → Net Yield. Each metric explained with what it tells you, what it doesn't, and the reflex to develop.

**Layer 4 — Triggers**
Configurable thresholds per strategy. Edit the input panel and trigger tables update in real time. Covers pUSD/CDP, pETH/ETH Loan, POLAR, and strategy switching conditions.

**Layer 5 — Tools**
Priority map of monitoring tools (P0 to P3), setup instructions, and mainnet vs testnet flags. Includes a pre-mainnet checklist.

---

## How to use it

Open [aremd.github.io/Polaris-playbook](https://aremd.github.io/Polaris-playbook/) in any browser.

- **Start with Layer 0** if you're opening the dashboard without a plan — match what you observe to a scenario and go directly to Action #1.
- Use the **MONITORING / DECISION toggle** to set your reading mode. A banner shows the reading order and the key question for your situation. Layer 1 and Layer 4 adapt automatically.
- Use the **strategy selector** at the top to switch between SP First, Leverage Loop, Bonding Curve Arb, and Defensive. Thresholds in Layer 4 auto-update.
- Edit the **configurable parameters** in Layer 4 to match your own risk profile.
- Use **! Misreads** before your first real session to avoid the six most common interpretation errors.
- Toggle **light / dark mode** using the button in the header.

Works on iOS, Android, and desktop. No login, no account, no dependencies.

---

## Key protocol facts documented

- **ETH Loan is non-liquidatable.** LTF is a borrowing capacity ratio, not a liquidation threshold. The risk is leverage risk (market value of collateral), not forced liquidation.
- **ETH Loan max borrow** = pETH collateral × floor price. As floor rises, additional borrowing capacity is released automatically.
- **LTV (CDP) and LTF (ETH Loan) are distinct metrics** for distinct products. Never conflate them.
- **pUSD repeg is automatic** — observed in 27 minutes during a live stress event (March 18, 2026).
- **SP APY rises when depositors panic-exit** — staying in the Stability Pool during stress is often the correct decision, not exiting.
- **IR controller softening** is in progress by the team. Track Net Borrow Rate, not IR directly.
- Causal chain: ETH spot → Oracle → LTV → TCR → IR → Net Borrow Rate → SP APY → Net Yield.

---

## Status and roadmap

**Current version:** v6.1 — testnet Sepolia

**This playbook is a work in progress.** The following are known gaps being addressed:

| Gap | Status |
|-----|--------|
| Mainnet threshold calibration | Pending mainnet launch |
| pGOLD decision tree (S7) | Pending team mechanics |
| Liquidation scenario — Loan #56 absorbed by SP (S6) | Data pending |
| Position sizing framework | Planned |
| Gas cost overlay (Loop + Arb) | Planned |
| Smart contract risk layer | Planned |

**Note on the Leverage Loop:** the current ETH Loan mechanism is testnet-specific. The team is exploring changes before mainnet due to free-rider dynamics. This section will be updated when the mainnet design is confirmed.

---

## ⚠️ Disclaimer — Honest limitations


**This playbook is not financial advice.** It documents one operator's testnet experience and is provided for educational purposes only. Do not use these thresholds or strategies with real capital without independent validation.


This playbook was built on 27+ days of testnet practice with fictional capital. It has not been validated with real money, real gas costs, or real liquidity constraints. All thresholds (LTV 55/65/75%, NBR 2%, SP APY 9%) are testnet-calibrated. Recalibration against real mainnet conditions is planned for the first 30 days post-launch.

---

## Contributing

Feedback, corrections, and strategy contributions are welcome via GitHub Issues.

If you are using Polaris on mainnet and observe behavior that contradicts what is documented here, please open an issue — real data is the only way to keep this accurate.

---

*Arem with ❤️ for Polaris*

---

## License

This work is licensed under [Creative Commons Attribution-NonCommercial 4.0 International (CC BY-NC 4.0)](https://creativecommons.org/licenses/by-nc/4.0/).

You are free to share and adapt this material for non-commercial purposes, provided you give appropriate credit to the author (Arem) and indicate if changes were made. Commercial use requires explicit written permission from the author.

© 2026 Arem — All commercial rights reserved.
