
---
language: en
tags:
  - behavioral-science
  - psychological-research
  - research-methodology
  - group-dynamics
  - congruence-assessment
  - role-playing-research
  - data-collection
  - verification-method
  - bivrest-method
  - social-validation
license: mit
---

[![GitHub stars](https://img.shields.io/github/stars/olesyalazareva/bivrest-method.svg?style=social)](https://github.com/olesyalazareva/bivrest-method/stargazers)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

# BIVREST — Group Verification Protocol for Role-Based Behavior

**Version:** 1.0  
**Status:** Registered in NRIS (Russian Scientific Research Registry)

---

## 📑 Table of Contents

- [The Problem](#the-problem)
- [What BIVREST Offers](#what-bivrest-offers)
- [What BIVREST Actually Measures](#what-bivrest-actually-measures)
- [Who Is BIVREST For](#who-is-bivrest-for)
- [How the Protocol Works](#how-the-protocol-works)
- [Data Structure](#data-structure)
- [Quick Start](#quick-start)
- [Implementation in UNIVERSE 69 Game](#implementation-in-universe-69-game)
- [Limitations](#limitations)
- [Citation](#citation)
- [Contacts](#contacts)

---

## The Problem

In role-playing games and research sessions, it's difficult to assess how well a participant's behavior **matches their role**. Psychologists call this **congruence** — the alignment between actions and the expectations associated with a role.

**What researchers and facilitators typically face:**

| Method | Problem |
|---|---|
| **Expert evaluation** | Subjective, depends on the facilitator's experience and preferences |
| **Participant surveys** | Social desirability bias — participants say what is "acceptable" rather than what they actually think |
| **Self-assessment** | Doesn't reflect group perception; gap between "how I intended to play" and "how I was perceived" |
| **Open observation** | Data is hard to structure, compare, and analyze |

**The result:** no unified criterion, data is incomparable, and conclusions are built on subjective impressions.

---

## What BIVREST Offers

BIVREST is a **data collection protocol** that standardizes the process of evaluating role-based behavior.

**Core mechanism:**

The group votes **"Believe / Don't Believe"** after each action. The voting criterion is **set before the session begins** and can be, for example:

> *"Does this action match the role?"*

Votes are counted, the verdict is determined by majority, and the result is recorded in a structured log.

**Key idea:**

Instead of asking the participant: *"How did you feel in the role?"* — we ask the group: *"Was this congruent with the role?"*

This **shifts the focus** from self-assessment to **social perception** and produces data that can be statistically analyzed.

---

## What BIVREST Actually Measures

**It's important to understand:** BIVREST does not claim to measure "objective truth." It measures **group perception**.

| What BIVREST Provides | What BIVREST Does NOT Provide |
|---|---|
| Socially validated assessment of congruence | Objective truth about roleplay quality |
| Structured data for analysis | A ready-made answer to "was it played well?" |
| Ability to compare sessions with a fixed criterion | Comparison across different criteria |
| Data on group dynamics and social expectations | Individual psychological diagnostics |

**BIVREST is a tool for studying how a group perceives role-based behavior.**

It is useful if your research question is:
- "What actions does the group consider congruent with the role?"
- "How does perception of a role change over time?"
- "What causes misalignment between expectations and actions?"

---

## Who Is BIVREST For

| Audience | Purpose |
|---|---|
| **Researchers** | Collect structured data on role-based behavior and group perception |
| **Psychologists** | Record group dynamics, study social expectations |
| **Game Designers** | Ready-made mechanics for evaluating roleplay to integrate into games |
| **AI Engineers** | Protocol for collecting labeled data for training models to recognize congruence |

### Name Breakdown (Process-Oriented)

| Letter | Meaning | Description |
|---|---|---|
| **B** | Believe / Don't Believe | Binary voting mechanism |
| **I** | Information | Presenting information for evaluation |
| **V** | Voting | Group voting |
| **R** | Record | Recording results |
| **E** | Evaluate | Determining the verdict by majority |
| **S** | Store | Saving the structured log |
| **T** | Transfer | Transferring data for analysis |

---

## How the Protocol Works

### Protocol Participants

| Role | Description |
|---|---|
| **Group** | Minimum 3 people, vote after each action |
| **Observer** | Records voting results and maintains the log |
| **Facilitator** | Manages the session, assigns tasks (optional) |

### Voting Criterion

The criterion is **set before the session** and remains unchanged throughout the session.

**Recommended criterion for congruence research:**

> *"Does this action match the role?"*

**Other possible criteria (for other research tasks):**

- "Does this look convincing?"
- "Is this truthful in the game context?"
- "Would I believe the character would act this way?"

### Protocol Stages

| Letter | Stage | Action |
|---|---|---|
| **B** | Believe / Don't Believe | The group votes according to the defined criterion |
| **I** | Information | The participant presents an action (roleplay) |
| **V** | Voting | Each participant casts their vote ("Believe" or "Don't Believe") |
| **R** | Record | The observer records the results |
| **E** | Evaluate | The verdict is determined by majority |
| **S** | Store | Data is saved in a structured log |
| **T** | Transfer | Data is prepared for analysis |

### Complete Iteration Cycle

**Participant Action → Group Voting → Result Recording → Log Entry**

Each iteration produces one row in the log.

---

## Data Structure

### Log Format

| Field | Type | Description |
|---|---|---|
| `session_id` | string | Session identifier |
| `round` | integer | Round number |
| `player_id` | string | Player identifier |
| `avatar` | string | Player's role |
| `task` | string | Task from the card |
| `action_text` | text | Roleplay (what was said/done) |
| `votes_believe` | integer | Number of "Believe" votes |
| `votes_dont_believe` | integer | Number of "Don't Believe" votes |
| `verdict` | string | "Believe" or "Don't Believe" |
| `tokens_lost` | integer | How many tokens were lost (if penalty system is used) |
| `empty_chair` | boolean | Whether role exit occurred |

**Example of a filled log:** [session_example.en.txt](session_example.en.txt)

**Empty template for filling:** [templates/log_template.csv](templates/log_template.csv)

---

## 🚀 Quick Start

### 1. Download the Protocol Description
This repository contains everything you need to conduct a research session.

### 2. Read the Key Documents
- **[Technical Specification](protocol_specification.en.md)** — detailed rules and data formats
- **[Annotation Guide](annotation_guide.en.md)** — for labeling data for AI tasks
- **[Log Example](session_example.en.txt)** — what a filled record looks like

### 3. Conduct a Session

1. **Gather a group** — minimum 3 people
2. **Define the criterion** — for example: "Does this action match the role?"
3. **Run a series of iterations** — 5–20 rounds
4. **Record the results** — fill in the log after each action

### 4. Analyze the Data

The resulting log enables:

- **Quantitative analysis** — frequencies, distributions, dynamics
- **Comparative analysis** — across different roles and players
- **Model training** — if you're labeling data for AI

**If you need consultation on applying the method** — contact the author (contacts below).

---

## Implementation in UNIVERSE 69 Game

UNIVERSE 69 is a game where BIVREST is built in as a core mechanic. Full rules, cards, and roles are in a separate repository:

**→ [UNIVERSE 69 on GitHub](https://github.com/olesyalazareva/universe-69)**

### How BIVREST Is Integrated into UNIVERSE 69 Mechanics

| UNIVERSE 69 Mechanic | Role in BIVREST |
|---|---|
| **Task Cards** | Generate information for evaluation (Stage I) |
| **Avatars (Roles)** | Set the context for evaluating congruence |
| **"Believe / Don't Believe" Voting** | Core verification mechanism (Stage B) |
| **"Chance" Tokens** | Resource lost on "Don't Believe" |
| **"Empty Chair"** | Role exit upon repeated "Don't Believe" |
| **Logging** | Recording all actions and votes |

BIVREST can be used with any role-playing system — UNIVERSE 69 is an example of a ready-made implementation.

---

## Limitations

- **Group assessment ≠ objective truth** — the result reflects the group's opinion, not absolute reality
- **The criterion must be fixed** — if you change the criterion, data becomes incomparable
- **Multiple sessions are required** — for statistically significant data
- **Social desirability does not disappear** — it transforms into a desire to meet group expectations

---

## Citation

```bibtex
@misc{lazareva2025bivrest,
  author = {Lazareva, Olesya},
  title = {BIVREST: Group Verification Protocol for Role-Based Behavior},
  year = {2025},
  howpublished = {GitHub},
  url = {https://github.com/olesyalazareva/bivrest-method}
}
Contacts
Olesya Lazareva
Psychoanalyst-Sexologist, Game Master with 25 years of experience

Telegram: @olesyalazarevalove

Email: psi-tech@yandex.com

Method Status: Registered in NRIS (Russian Scientific Research Registry)

License and Terms
Non-commercial use (scientific research, open-source projects) — free with mandatory attribution and link to this repository

Commercial use (selling AI solutions based on BIVREST, corporate implementations) — by agreement with the author

⭐ If this method is useful for your work, please star the repository — so other researchers and engineers can find it.
