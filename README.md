# Cosmic Cleaners Wiki

A player-run reference and sale calculator for the Roblox game **Cosmic Cleaners**.

**→ [Open the wiki](https://3bdel7.github.io/cosmic-cleaner/)**

Unofficial. Not affiliated with the game or its developers.

---

## What's in it

**Sale calculator** — enter your cargo, the current market swing and your active boosts, and it shows what a sale will pay. The multiplier chain is displayed as a live conduit so you can see exactly where the value comes from.

**Full game data**

| Section | Contents |
|---|---|
| Jetpacks | All 5, with speed, thrust, storage and prices — including the two the shop hides behind "Owned" |
| Magnets | All 15 across 5 tiers, with range, pull and current prices |
| Base & Plot | Plot sizing, machine footprints, inventory breakdown |
| Furnaces & Crushers | Prices, tiers, and the throughput maths |
| Processing Speed | Smelt and crush rates taken from the game's own values |
| Market & Ingots | Ingot values, the ±30% swing cap, the 3-minute roll |
| Boosts & Passes | Golden Touch, 2X Credits, VIP, crew — and how they stack |
| Events | Star Flare and Ingot Rush, which behave differently |
| Rebirth Economy | Cost formula with a live calculator |
| Star Exchange | All 32 nodes, and how many stars each rebirth pays |

---

## How the numbers were worked out

Nothing here is guessed. The sale formula was reverse-engineered from **ten logged sales** and predicts payouts within **0.20%**, with one sale matching to the credit. Every remaining deviation is explained by the game rounding market percentages for display.

The verified formula:

```
total = [ (10 × normal) + (30 × charged) ]
      × (1 + market%)
      × (1 + event%)
      × (1 + GT level × 10%)
      × (VIP  ? 1.10 : 1)
      × (2X   ? 2.00 : 1)
      × (1 + crew × 5%)
```

**Bonuses multiply — they do not add.** At Golden Touch 4 with 2X and one crew member the real multiplier is ×2.94, where adding the percentages would predict ×2.45. On a large sale that gap is thousands of credits.

Anything not established by measurement is listed under **Not Yet Known** rather than filled in with a guess.

---

## Things worth knowing

- **Market swing is capped at ±30%.** Any reading higher than that means an event is folded into the number — don't count the event twice.
- **Star Flare and Ingot Rush work differently.** Star Flare multiplies on top of the market price and drifts between +70% and +90% over its 40-minute run. Ingot Rush is added into the market swing, so the displayed percentage already includes it.
- **Charged ingots are worth exactly 3× normal** — 30 credits against 10.
- **Furnace V1 and V2 take a quarter of a plot cell; V3 and above take a full cell.** This matters more than the tier numbers suggest.

---

## Contributing

The **Not Yet Known** section lists what's still missing. If you can measure any of it, open an issue with a screenshot. Particularly wanted:

- Scrap-to-ingot ratio, and how much storage each scrap type occupies
- Base crush time per scrap
- Plot expansion cost per cell
- Equipment Shop contents
- Whether furnaces and crushers have a capacity ceiling

Corrections are welcome too — if a number here is wrong, it should be fixed.

---

## Technical

Single self-contained `index.html`. No build step, no dependencies, no tracking. Item images are embedded as WebP. Works offline once loaded.
