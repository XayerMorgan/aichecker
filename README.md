# AI Tell Checker (`v3.2.0`)

**Evidence-Based, Multi-Tier & Era-Calibrated AI Writing Diagnostic Scanner + Anti-Tell Prompt Shield**  
*100% Client-Side HTML/CSS/JS • Google Sites & Sandboxed `<iframe>` Ready • Versioned `tells.yaml` Lexicon*

---

## Overview

**AI Tell Checker** is an explainable, rule-based diagnostic scanner that audits text across **6 probabilistic/deterministic tiers** and **negative-weight human signs**, calibrated to 9 empirical corpus studies:

- **Kobak et al. (*Science Advances*, 2025):** 14.4M+ PubMed abstracts (*delves* $r=28.0$, *underscores* $r=10.9$, *showcasing* $r=10.2$).
- **Liang et al. (*ICML 2024* & *COLM 2024*):** ICLR/NeurIPS peer reviews & 950k papers (*meticulous* $34.7\times$, *intricate* $11.2\times$, *commendable* $9.8\times$).
- **Reinhart et al. (*PNAS*, 2025):** Biber tagger grammatical analysis (instruction-tuned LLMs use present participial clauses at $2\times\text{–}5\times$ and nominalizations at $1.5\times\text{–}2\times$ the human rate).
- **Juzek & Ward (*COLING 2025*):** RLHF lexical overuse analysis.
- **Graphite AI Tells Corpus (Sept/Oct 2026):** 10k pre-ChatGPT web articles vs. 90k AI articles across 11 models (*"the _ is not simply"* $576\times$ in GPT-6 Astra; *"this matters"* $116\times$ in Claude Opus 5.5; em-dash inversion across 2026 frontier models).
- **Czuma (*medRxiv*, 2026) & Congressional Press Release Corpus (*arXiv:2608.05889*):** Unspaced vs. spaced em-dash drift.
- **Liang et al. (*Patterns*, 2023):** Non-native English (TOEFL) detector false-positive bias ($61.3\%$ mean FPR on perplexity detectors).
- **Wikipedia WikiProject AI Cleanup (Oct 2026) & Assured Information (2026):** Era-dated catchphrases, markup leakage, copula avoidance, and 25-year human baseline comparisons.

---

## The Five Core Design Rules

1. **Tier the Signals:** Deterministic chat/paste residue (**Tier 1**: `oaicite`, `utm_source=chatgpt.com`, unfilled `[Company Name]` templates, `↩` footnote arrows) sets a score floor of **90**. Lexical, rhetorical, syntactic, and formatting tells (**Tiers 2–6**) are weighted and capped.
2. **Normalize Everything per 1,000 Words:** Raw counts penalize long human documents. All probabilistic tiers normalize density per 1,000 words (excluding fenced code blocks and bare URLs).
3. **Version the Lexicon by Model Era:** Consecutive model versions share only $18.7\%\text{–}45.5\%$ of their tells. Every rule in [`tells.yaml`](./tells.yaml) carries an explicit era fingerprint (`2023-24 GPT-4`, `2024-25 GPT-4o`, `2025-26 GPT-5`, `2026+ Gemini 3 / Opus 5.5 / GPT-6`).
4. **Never Invert a Reversed Signal Silently:** Em-dash density (`0.014/1k` in Gemini 3.1 Pro, `0.015/1k` in Claude Opus 5.5 vs. `3.14/1k` human) and the classic 8-word *delve/tapestry* list now run below the human baseline in 2026 frontier models. High em-dash density ($>6.28\text{/1k}$) flags 2023–25 GPT models; zero/low em-dash density is never scored as AI. Instead, the scanner tracks how 2026 models replace suppressed em-dashes with **colon-led dramatic reveals** and **semicolon antithesis pivots** (`X was not A; it was B`).
5. **Show Evidence, Not a Verdict:** Every matched span is highlighted in context with its `rule_id`, model era, and source citation, while **Human-Leaning Features** deduct up to `-25 pts`.

---

## Built-In Calibration Samples & Case Studies

| Sample Button | Score & Band | Likely Model Era | Diagnostic Highlights |
| :--- | :--- | :--- | :--- |
| **`Oct 2026 Gemini (Taco Story)`** | **91–94 / 100** (`HIGH DENSITY`) | `2026+ Gemini 3 / Opus 5.5 / GPT-6` | `0.00/1k` em-dashes & `0.00/1k` Classic-8 words, caught via 4 contrast/negation frames, colon/semicolon pivots, curly/straight apostrophe mixing (`city’s` vs `Unit-7's`), 7 participial clauses (`19.7/1k`), and 6 paired `adj, adj + noun` phrases (`16.9/1k`). |
| **`Oct 2026 AI Essay`** | **100 / 100** (`HIGH DENSITY`) | `2026+ Gemini 3 / Opus 5.5 / GPT-6` | High-ratio 2026 markers (*why X matters*, *the _ is not simply*, *is more than a _ it*, *rather than simply*, *does not by itself establish*, *looking ahead, the*). |
| **`2024 GPT-4 + Artifact`** | **100 / 100** (`ARTIFACT FLOOR 90+`) | `2023-24 GPT-4` | Tier 1 artifacts (`Certainly!`, `[Company Name]`, `contentReference[oaicite:0]`, `utm_source=chatgpt.com`, `↩1`), `[U+202F]` narrow no-break space, `37.04/1k` em-dashes, `44.44/1k` Classic-8 rate. |
| **`1776 Human Control`** | **0 / 100** (`LOW`) | `Human / Pre-2022 Baseline` | Declaration of Independence excerpt: classical triads and stone-engraving `--` pauses lack Tier 1/3/4/6 corroboration and are offset by `-18 pts` of human/historical markers. |

---

## ⚡ Anti-Tell Prompt Shield & Gem/GPT Builder (`v3.2.0`)

Click **⚡ Anti-Tell Prompt Shield** in the top bar (or see [`PROMPTS.md`](./PROMPTS.md)) to turn the checker's 6-Tier detection rules into a preventative prompt wrapper or system instruction:

1. **Preface a Writing Prompt (Standalone Chat):** Select your register (*Creative/Narrative Fiction*, *General Essay*, *Executive Email*, or *Academic/Technical*) and length (*Compact ~150w* or *Full 6-Tier Protocol ~380w*), type your creative prompt, and copy a ready-to-paste prompt that blocks negation-reveal pivots, paired `adj, adj + noun` stacks, trailing `-ing` participial clauses, colon-led dramatic reveals, mid-sentence bolding, and high-ratio AI lexicon before generation starts.
2. **Gem / Custom GPT / LM Studio System Prompt:** Copy the `<writing_style_protocol version="3.2">` system block directly into a **Google Gem**, **OpenAI Custom GPT**, **Claude Project**, or **LM Studio System Prompt**.
3. **Surgical De-Tell Rewrite Prompt (From Scan Hits):** After scanning any draft, click **⚡ Generate De-Tell Rewrite Prompt from Hits** to build a customized rewrite prompt that lists every specific Tier 1–6 span matched in your text and instructs the LLM how to rewrite the passage cleanly.

---

## Usage & Google Sites Embed

### Local Usage
Open [`index.html`](./index.html) directly in any browser—no build step, server, or external network requests required.

### Embedding in Google Sites
1. Open your Google Site editor and click **Insert &rarr; Embed &rarr; Embed code**.
2. Paste the entire contents of [`index.html`](./index.html) into the code box and click **Next &rarr; Insert**.
3. The app is hardened for sandboxed `<iframe>` environments (including a `document.execCommand('copy')` clipboard fallback and automatic rich-text paste conversion that preserves `<strong>`/`<em>` formatting when pasting from Gemini or ChatGPT).
