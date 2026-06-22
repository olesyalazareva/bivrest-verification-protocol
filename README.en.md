# BIVREST — Ground Truth Generator for AI

**Behavioral Verification through Role-Play and Binary Assessment**

**The Problem:** AI engineers and researchers spend months and hundreds of thousands of dollars on manual data labeling to train deception detection and emotion recognition models. Public datasets are almost non-existent, and those that exist are synthetic or low-quality.

**What BIVREST does:** It's a ready-to-use protocol that **generates labeled data automatically** through a game with "Believe / Don't Believe" mechanics. Every player action receives an objective binary label without expert involvement.

**The Result:** You get a high-quality dataset with real behavioral responses for AI training in **hours, not months**, and without manual labeling.

[![License: Custom](https://img.shields.io/badge/License-NonCommercial--with--attribution-blue.svg)](./LICENSE)
[![Status](https://img.shields.io/badge/Status-Deposited%20(NRIS)-green)](./LICENSE)

---

## 🎯 Who Is This For

- **AI/ML Engineers** — get ready-to-use labeled datasets for model training
- **R&D Teams** — get an objective assessment tool without manual labeling
- **Researchers** — study emotional authenticity and defense mechanisms through gameplay

---

## 🔥 What Problem Does BIVREST Solve

| **Problem** | **Traditional Approach** | **BIVREST** |
|:---|:---|:---|
| Where to get data? | Hire dozens of people for manual labeling | Game session automatically generates labels |
| Subjectivity | Labelers make mistakes or have bias | Binary "Believe/Don't Believe" voting gives objective results |
| Cost | Thousands of dollars for labeled datasets | Minimal costs to organize a game |
| Time | Months to collect and label | Data collected in real-time during one session |

---

## 🧠 How It Works

1. **Game Session:** 2–6 people play a role-playing game with avatars. Each turn is an action from the character's perspective.

2. **Binary Voting:** After each action, the group votes **"Believe"** or **"Don't Believe"**.

3. **Penalty for Role Mismatch:** If the majority says "Don't Believe" — the player loses a resource. The penalty is **not for truth or lies**, but for **fantasy that doesn't fit the role**. This creates a natural incentive to be emotionally authentic.

4. **Empty Chair:** After two "Don't Believe" votes in a row, the player steps out of their role and speaks as themselves. The AI gets a benchmark example of an honest response.

5. **Ready Dataset:** Every action, vote, and result is logged in a structured format (CSV/JSON). The output is a dataset with fields: `action`, `verdict` (Believe/Don't Believe), `player_id`, `avatar`.

---

## 📦 What's Included

- **`/protocol`** — full BIVREST method description (7 steps, 7 differences, pseudocode, API reference)
- **`/game`** — "Universe 69" game (rules, cards, avatars)
- **`/annotation-guide`** — guide for annotating data for AI
- **`/logs`** — example raw session log ([view example](./logs/session_example.en.txt))

---

## 🆚 How BIVREST Compares to Alternatives

| **BIVREST** | **Psychodrama / CBT** |
|:---|:---|
| Avatar is maximally different from self | Role is close to self |
| Binary verification without a therapist | Authoritative verdict by an expert |
| Penalty for role mismatch | No penalty — safe to lie |
| Uses an AI "double" for the empty chair | Requires the presence of a second person |
| Enforces role switching | Can hide behind a mask indefinitely |

---

## 🚀 How to Use the Method

1. **Study** the full protocol in [`protocol/BIVREST_method.en.md`](./protocol/BIVREST_method.en.md)
2. **Organize** pilot sessions following the structured game rules
3. **Collect** raw action logs and "Believe / Don't Believe" votes from participants
4. **Annotate** the data using the guide in [`annotation-guide/README.en.md`](./annotation-guide/README.en.md)
5. **Train** your AI models on this behavioral dataset

---

## 🎮 Connection to UNIVERSE 69 Game

BIVREST and **UNIVERSE 69** are two complementary projects:

| **BIVREST** | **UNIVERSE 69** |
|:---|:---|
| Ground truth data generator for AI | LLM-native role-play game engine |
| Deception detection & emotion recognition training | Context drift & hallucination prevention |
| Protocol with binary verification | UNO card mechanics as structural container |
| For AI/ML engineers and researchers | For game designers, psychologists, and developers |

**How to use them together:**
1. Use **UNIVERSE 69** for conducting role-play sessions with LLM
2. Apply **BIVREST** protocol for verification and data collection
3. Train your models on annotated data generated from the game

**Link to project:** [UNIVERSE 69 on GitHub](https://github.com/olesyalazareva/universe69)

---

## 🔬 Example Use Cases

- **Training an LLM** to detect subtle emotional cues in text
- **Developing a model** to distinguish between genuine and deceptive statements
- **Building a behavioral dataset** for research on human-AI interaction and trust

---

## 👩‍💻 Author & Contact

**Olesya Lazareva**  
Psychoanalyst-sexologist, Game Technician with 25+ years of practice

- **Telegram:** [@olesyalazarevalove](https://t.me/olesyalazarevalove)
- **Email:** [psi-tech@yandex.com](mailto:psi-tech@yandex.com)
- **Method Status:** Deposited in the National Register of Intellectual Property (NRIS)

---

## 📄 License & Terms

- **Non-Commercial Use:** Freely permitted for scientific research and open-source projects, provided that proper attribution is given and a link to this repository is included
- **Commercial Use:** (e.g., selling AI solutions based on BIVREST, corporate implementation) requires explicit permission from the author

---

**⭐ If you find this method useful for your work, please star the repository — so others can find it too.**
