# spec-to-ship

**Agent skills and quality gates for taking a product from fuzzy idea to verified delivery.**
Clear specs. Sound architecture. Verified delivery. Built by a Technical PM, and every agent is used on a real project before it ships here.

[🚀 Quick start](#-quick-start) · [🧩 The pipeline](#-the-pipeline) · [📦 Case studies](#-case-studies) · [🙏 Built on](#-built-on)

> 🛠️ **Building in public.** This repo grows every weekday. Follow along on X: [@PrasinMotion](https://x.com/PrasinMotion)

---

## Why this exists

Most AI coding setups optimise for one thing: writing code faster. But the hardest problems in delivery happen *before* and *after* the code:

- **Before:** the agent builds the wrong thing because the spec was vague.
- **During:** the architecture drifts because nobody wrote down why decisions were made.
- **After:** "it works on my machine" ships, and nobody can tell whether it keeps working.

`spec-to-ship` closes those gaps. Every skill and agent here belongs to one of three stages.

```
  CLEAR SPECS             SOUND ARCHITECTURE          VERIFIED DELIVERY
 ┌──────────────────┐    ┌───────────────────┐      ┌──────────────────────┐
 │ grill            │    │ decision records  │      │ two-axis reviewer    │
 │ spec             │──▶ │ app rescuer       │ ──▶  │ scope-creep check    │
 │ acceptance       │    │ decision detective│      │ evals + fact-checker │
 │   criteria       │    │ prototype         │      │ flight recorder      │
 │ client brief     │    │                   │      │ delivery reporter    │
 └──────────────────┘    └───────────────────┘      └──────────────────────┘
```

---

## 🚀 Quick start

> The first skills land in week 2. Until then, star the repo to follow along.

```bash
npx skills@latest add Prasinmotion/spec-to-ship
```

Then ask your coding agent: *"Grill me on this idea: an app that helps salons cut no-show appointments."*

---

## 🧩 The pipeline

Status: ✅ shipped · 🔨 in progress · 🔜 planned

### 1 · Clear Specs
*Close the gap between what you mean and what gets built.*

| Skill | What it does | Status |
|---|---|---|
| **grill** | Interviews you about an idea until there is nothing left to guess | 🔜 |
| **spec** | Turns the interview into a one-page spec: goals, non-goals, constraints | 🔜 |
| **acceptance-criteria** | Testable Given/When/Then checks for every story | 🔜 |
| **client-brief** | The same spec, rewritten for a non-technical client or founder | 🔜 |

### 2 · Sound Architecture
*Every technical decision is made on purpose, and written down.*

| Skill / agent | What it does | Status |
|---|---|---|
| **app-rescuer** | Honest audit of a half-built app: what works, what's missing, what's risky | 🔜 |
| **decision-detective** | Finds decisions hidden in the code that nobody documented, and drafts the records | 🔜 |
| **prototype** | Cheap, throwaway versions to settle design questions before building | 🔜 |

### 3 · Verified Delivery
*Nothing is "done" until it's proven done, and stays working.*

| Skill / agent | What it does | Status |
|---|---|---|
| **two-axis-reviewer** | Reviews every pull request on two axes: *is it good code?* and *is it what the spec asked for?* | 🔜 |
| **scope-creep-check** | Flags changes that grew beyond what was asked | 🔜 |
| **itinerary-fact-checker** | An eval set and a self-correcting loop for AI output | 🔜 |
| **flight-recorder** | Logs every agent run: time, cost, steps, failures | 🔜 |
| **delivery-reporter** | Weekly report: what shipped, what didn't work and how it was fixed | 🔜 |

---

## 📦 Case studies

Every case study goes through the full pipeline and comes with its spec, decision records, test results and real numbers.

| Project | What it is | Status |
|---|---|---|
| **Rescuing a half-built travel app** | Taking an AI trip planner from "mostly works" to live, with evals and monitoring | 🔜 |
| **Chain Brain** | Ask one question, get an answer from six systems of a 70-outlet restaurant group (synthetic data, MCP, Docker) | 🔜 |
| **AI agents for my own restaurant** | Morning brief, review replies, report fetching and a voice host, with a human in the loop | 🔜 |

---

## 🙏 Built on

`spec-to-ship` stands on the shoulders of excellent open-source work:

- **[mattpocock/skills](https://github.com/mattpocock/skills)** (MIT): grilling, spec, TDD and review foundations
- **pstack** by Lauren Tan (MIT): verification and multi-model review patterns

This repo adds the product and delivery layer on top: acceptance criteria, decision records, scope checks, evals, observability and reporting.

---

⭐ **Star the repo** to get notified when new skills and case studies land.

MIT · Fork it, adapt it, ship with it.
