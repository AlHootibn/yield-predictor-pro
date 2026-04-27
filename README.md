# Yield Predictor Pro — JyväSisu Fungi

> An AgriTech decision platform for mushroom growers. Predict production, track real farm performance, and optimize profitability across multiple grow cycles.

---

## Overview

Yield Predictor Pro is a professional planning and performance-tracking tool built for mushroom cultivation operations. It combines financial modelling, risk analysis, and real-data feedback into a single offline web application — no server, no account, no installation required.

Built by **Hisham AlHoot** for **JyväSisu Fungi** · Finland · 2026

---

## Features

### 🔮 Predictor Tab
- Select mushroom species: Lion's Mane, Blue Oyster, King Oyster, Enoki, Shiitake
- Configure bag count and bag weight (2.5 / 3.0 / 4.0 kg)
- Bag-weight-dependent yield model (`yield = bags × weight × baseYield[species]`)
- **3-month forecast**: total production, revenue, cost, net profit, break-even point
- **Monthly breakdown**: average monthly production and revenue
- **Scenario modelling**: Worst (−15%) / Expected / Best (+15%) range with visual bar
- **Risk assessment**: species-specific risk level (Low / Medium / High) with colour coding
- **AI Recommendation**: actionable advice per species and margin level
- **Profit Optimizer**: evaluates all 15 combinations (5 species × 3 bag weights) and recommends the highest-profit configuration for your bag count
- **Simulate Expansion**: shows projected profit at 0.5× / 1× / 1.5× / 2× / 3× scale

### 🌾 Real Farm Tab
- Enter actual cycle results: harvested kg, lost bags, cycle duration
- **Operational Efficiency %** displayed as a large hero metric (colour-coded)
- Visual comparison bar: Expected vs Actual production
- **Contamination rate** with threshold-based classification:
  - 0–2%: Excellent · 2–5%: Good · 5–10%: Warning · 10–20%: High Risk · >20%: Critical
- Cycle duration vs species baseline (e.g. Blue Oyster expected 21 days)
- Revenue delta: actual vs expected revenue gap
- **Save to Batch History** button — persists data in browser localStorage

### 📋 Batch History Tab
- All saved batches displayed in a sortable table
- Each batch shows: ID, date, type, bags, expected/actual kg, efficiency %, contamination %, cycle days
- **Farm Intelligence panel** (activates with 2+ batches):
  - Average efficiency across all batches
  - Average contamination rate
  - Best-performing species by average efficiency
  - Total production tracked
  - Data-driven recommendation (e.g. species reallocation advice)
- **Export CSV** — download all batch data as a spreadsheet
- **Clear All** with confirmation

---

## Yield Model

```js
// Yield depends on bag weight — larger bags produce more per cycle
const baseYield = {
  lion_mane:   0.18,  // 18% of bag mass
  blue_oyster: 0.25,  // 25% of bag mass
  king_oyster: 0.20,
  enoki:       0.18,
  shiitake:    0.22
};

yieldPerCycle = bags × bagWeight × baseYield[type]
total3Months  = yieldPerCycle × cycles[type]
```

### Cycles per 3 months
| Species | Cycles |
|---------|--------|
| Lion's Mane | 3 |
| Blue Oyster | 4 |
| King Oyster | 3 |
| Enoki | 2 |
| Shiitake | 2 |

### Market Prices (Finland)
| Species | €/kg |
|---------|------|
| Lion's Mane | €30 |
| Blue Oyster | €12 |
| King Oyster | €22 |
| Enoki | €18 |
| Shiitake | €20 |

### Cost Model
```
totalCost = bags × €2.50 × cycles   (substrate + labour estimate)
```

---

## Financial Outputs

| Metric | Formula |
|--------|---------|
| Revenue | `total3Months × pricePerKg` |
| Net Profit | `revenue − totalCost` |
| Margin | `profit / revenue × 100` |
| Break-even | `totalCost / pricePerKg` |
| Monthly Revenue | `revenue / 3` |

---

## Tech Stack

- **Pure HTML / CSS / JavaScript** — zero dependencies, zero build step
- **localStorage** — batch history persists across browser sessions
- **Single file** — open `index.html` directly in any browser
- Fully responsive (mobile + desktop)

---

## How to Use

1. Open `index.html` in any modern browser
2. **Predictor tab**: select species → enter bag count and weight → click Calculate
3. Use **Optimize Profit** to find the best species/weight combo
4. Use **Simulate Expansion** to model scaling scenarios
5. After a real grow cycle, go to **Real Farm tab** → enter actual results → Save
6. Visit **Batch History** to track performance trends over time

---

## Project Structure

```
Yeild/
├── index.html     # Complete application (single file)
└── README.md      # This file
```

---

## Brand

**JyväSisu Fungi**  
Hisham AlHoot · Finland · 2026

> *"Sisu"* — a Finnish concept of stoic determination, resilience, and acting rationally in the face of adversity. The spirit of every successful grow.
