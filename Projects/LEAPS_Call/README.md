# QQQ LEAPS Call Extension Strategy (Personal Notes)

## Overview

- Starting Capital: 100,000 USD
- Ending Capital: 660,000 USD
- Underlying Asset: QQQ
- Strategy Type: Long-term bullish using LEAPS calls
- Core Idea: Use call options with high delta to simulate stock exposure with lower capital usage

---

## Basic Concepts

### QQQ Exposure

- 100 units of QQQ ≈ 60,000 USD
- 1 LEAPS Call (Delta ≈ 0.8) ≈ 15,000 USD

Delta meaning:
- Delta = 0.8 → If QQQ increases by 1 USD, the call price increases by ~0.8 USD
- This provides ~80% of stock exposure using much less capital

Using ~25% of capital:
- 15,000 USD controls ~48,000 USD worth of QQQ exposure
- Remaining capital stays as cash buffer

Note:
- LEAPS still suffer from time decay (theta), though slower than short-term options

---

## Core Strategy: Buy Call With Extension

- Long-term bullish bias
- Maintain exposure through rolling LEAPS calls
- Use rolling to manage time decay and lock in profits

---

## Rolling (Extension) Mechanics

Rolling consists of two actions:
1. Sell the current call
2. Buy a new call with a longer time to expiration

### Roll Out

Purpose:
- Extend duration as time decay accelerates

Trigger:
- DTE (Days to Expiration) < 300 days

Action:
- Sell current LEAPS call
- Buy a new LEAPS call with DTE > 700 days

Effect:
- Spend capital to extend duration
- Maintain bullish exposure

---

### Roll Up and Out (Lock in Profit)

Purpose:
- Lock in gains during strong bullish moves

Situation:
- QQQ is in a strong bull trend
- Call delta increases toward 0.9

Action:
- Sell the current deep ITM call
- Buy a higher strike call with longer DTE and lower delta (~0.7)

Effect:
- Realize profit
- Reduce delta to avoid overexposure
- Extend option duration

---

## Example Roll Up and Out

- QQQ price: 600 USD
- Old call strike: 500 USD
- Equivalent stock exposure: 50,000 USD
- Original cost: ~15,000 USD
- Profit on sale: ~10,000 USD

New position:
- Buy a new call with strike near 600 USD
- Longer DTE
- Lower delta

---

## Portfolio Allocation

- 60% LEAPS calls
- 40% cash
- Strategy bias: long-term bullish (QQQ target range 650–800)

Typical delta target:
- Entry delta: ~0.8
- Avoid delta > 0.9 for extended periods

---

## Entry Rules

- Entry trigger: QQQ drops 1% or more
- Buy LEAPS call with:
  - Delta ≈ 0.8
  - DTE between 600–800 days

---

## Bull Case Management

Situation:
- Strong bullish trend
- Delta rises above 0.9

Action:
- Close current call
- Buy new call with:
  - Delta ≈ 0.7
  - DTE > 650 days

Effect:
- Lock in profit
- Reset delta exposure
- Extend duration

---

## Bear Case Management

Situation:
- Delta falls below 0.5
- Cash position > 10%
- Market shows weakness

Rules:
- Apply a 30-day cooldown period to avoid overtrading

Actions:
- If total position > 40%:
  - Use 10% capital to re-enter
- If total position < 40%:
  - Use 5% capital to re-enter

New entry:
- Delta ≈ 0.8
- DTE between 600–800 days

---

## Time Decay Risk Management

Situation:
- DTE < 300 days
- Delta ≈ 0.9

Action:
- Roll out to DTE > 700 days

Effect:
- Pay premium to extend time
- Wait for price recovery if needed

---

## Key Risks

- Time decay (theta)
- Volatility contraction
- Large drawdowns during prolonged bear markets
- Overexposure when delta approaches 1.0

---

## Key Takeaway

This strategy uses LEAPS calls to achieve high QQQ exposure with reduced capital, while actively managing time decay and locking in gains through rolling and delta control.