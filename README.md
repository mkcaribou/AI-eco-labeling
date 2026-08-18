# AI eco-labeling

A proof of concept for estimating the marginal environmental impact of AI model choice. Pick a task and two models, and see what right-sizing saves in energy and carbon.

**Live calculator:** https://mkcaribou.github.io/AI-eco-labeling/

## Why

AI services report tokens and dollar cost, but not electricity, carbon, or water. If that information existed per model and per task, users and platforms could weigh it alongside quality, speed, and price. This repo is a first step: a small, transparent dataset and a calculator that shows the math.

The headline finding: model choice spans one to two orders of magnitude in energy per task, and the gap widens once you account for reasoning tokens. Right-sizing the model to the task is one of the cheapest efficiency levers available.

## What is in this repo

| File | Purpose |
|---|---|
| `index.html` | Interactive calculator (single file, no dependencies) |
| `AI model energy calculator.xlsx` | The underlying model: dataset, assumptions, calculator, scenarios |
| `data/model_energy_dataset_mvp_v3_2026-08-12.csv` | Curated MVP dataset (8 models, capability data, confidence grades) |
| `data/raw_artificialanalysis_2026-08-12.csv` | Raw source snapshot for provenance |
| `IMPACT.md` | The funding case: market size, leverage, and tiered impact scenarios |

## Method

Energy per query = (latency + output tokens / throughput) × server power × utilization × PUE, estimated per model from API telemetry ([Jegham et al. 2025](https://arxiv.org/abs/2505.09598)), standardized at 1,500 output tokens and scaled by task-dependent token counts.

The task-first logic: a task determines which models are capable of it (via capability floors on the Artificial Analysis intelligence index and agentic benchmarks) and how many tokens each model burns on it (thinking models emit reasoning tokens on every task). Models below a task's floor are flagged: comparing against a model that would fail the task is not meaningful.

## Confidence grades

- **A** — vendor-disclosed. None in the dataset yet.
- **B** — estimated from API telemetry and hardware assumptions. All energy rows.
- **C** — editorial working assumption: task token counts, calls per agentic task, the success proxy, and the Claude Opus 5 estimate (computed with the same formula from Artificial Analysis speed and latency; no telemetry row exists yet).

## Caveats that matter

1. Vendor-disclosed figures (Google: 0.24 Wh per median Gemini prompt; OpenAI: 0.34 Wh per average ChatGPT query) sit roughly 10x below these estimates because they cover shorter prompts and assume high batching. Treat levels as indicative and comparisons as the signal.
2. Telemetry conflates model size with serving speed: a slowly served small model can score worse than a fast large one. The cross-tier pattern is robust; single readings are not.
3. Scope is inference only. Training, embodied hardware carbon, and networking are excluded.

## Sources

- Jegham et al. (2025), [How hungry is AI?](https://arxiv.org/abs/2505.09598) and the [daily-updating dashboard pipeline](https://github.com/Nidhal-Jegham/HowHungryisAIDashboard)
- [Energy use of AI inference](https://www.cell.com/joule/fulltext/S2542-4351(26)00114-5), Joule (2026)
- [The real energy use of agentic AI](https://www.theclimatebrink.com/p/the-real-energy-use-of-agentic-ai), The Climate Brink

## Contributing

The long-term vision is a public dataset that providers and data centers update with vetted figures. Corrections to the data, better-grounded task assumptions, and vendor disclosures are all welcome: open an issue or a pull request.
