# Why fund AI eco-labeling: the impact case

## The problem is invisibility, not appetite

Every AI API call reports tokens and dollar cost, but not electricity, carbon, or water. Developers already re-route traffic aggressively on the one signal they can see: when cheap models appeared, the [OpenRouter](https://openrouter.ai/rankings) market mix shifted toward them within months. The routing behavior exists. The energy signal does not.

## The market is large and compounding

AI-focused data centers consumed roughly 155 TWh in 2025, growing about 30% a year ([IEA](https://www.iea.org/reports/energy-and-ai/energy-demand-from-ai)). Google processed 3.2 quadrillion tokens in May 2026, a sevenfold increase in one year. Microsoft processed over 100 trillion tokens in a single quarter. Roughly 97% of Anthropic's API traffic is automation-dominant, meaning agents and pipelines rather than chat, and agentic tasks consume 600 to 1,000 times the tokens of a chat prompt ([The Climate Brink](https://www.theclimatebrink.com/p/the-real-energy-use-of-agentic-ai)).

## The intervention: make the energy signal exist, then put it where routing happens

This project maintains a public, per-model energy dataset with transparent methodology and confidence grades ([this repository](https://github.com/mkcaribou/AI-eco-labeling)), plus a reference calculator that shows what right-sizing saves per task. Our working model shows one to two orders of magnitude spread in energy per task across current models, and 50 to 95% savings from routing tasks to the cheapest capable model.

Leverage sits at the platform layer, not with end users. One integration into a router or aggregator (OpenRouter, Gooey.AI, enterprise gateways) moves more traffic than any number of individual choices. Three channels, in descending leverage: default routing at aggregators, enterprise procurement standards (CSRD-style reporting creates demand for per-token eco data), and disclosure competition among vendors (Mistral and Google already disclose; a public leaderboard pressures the rest).

## What a $1M project plausibly returns

Impact scales with the share of global inference traffic the signal reaches. Assuming ~120 TWh of inference electricity in 2026:

| Scenario | Traffic influenced | Savings on that slice | GWh/yr | $M/yr | ktCO2e/yr | $/tCO2e |
|---|---|---|---|---|---|---|
| Conservative | 0.1% | 30% | 36 | 2.9 | 17 | ~58 |
| Central | 0.5% | 50% | 300 | 24 | 144 | ~7 |
| Ambitious | 2% | 70% | 1,680 | 134 | 808 | ~1.2 |

Even the conservative case returns roughly 3x the grant annually. The central case lands near $7 per tonne of CO2e avoided, which compares favorably with typical climate philanthropy at $10 to $100 per tonne. All parameters are editable in the [accompanying workbook](https://github.com/mkcaribou/AI-eco-labeling); every assumption is graded and visible.

## What gets funded

Maintenance of the public dataset and methodology as models and serving infrastructure change; a public API so platforms can display eco data without rebuilding the research; reference integrations with routing platforms; and engagement with providers to replace estimates with vetted disclosures.

## Honest limitations

Current figures are telemetry-based estimates, not disclosures, and run roughly 10x above the two vendor-disclosed numbers on boundary differences. Adoption shares in the scenario table are working assumptions, not commitments. The counterfactual (would traffic have shifted anyway on price?) is real but cuts both ways: price-driven routing proves the mechanism this project makes environmental.
