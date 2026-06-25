# BIVREST — Group Assessment Protocol for Role-Based Behavior

**Version:** 1.0


---

## 1. The Problem BIVREST Solves

**The problem:** In role-playing games and research sessions, it is difficult to objectively assess the quality of performance. The facilitator's assessment is subjective, participants lack a unified criterion, and data is hard to structure and compare.

Conventional data collection methods (interviews, surveys, focus groups) produce distorted results due to social desirability bias. Participants say what is "acceptable" rather than what they actually think.

**What BIVREST offers:** A unified assessment mechanism through group voting. The group votes "Believe / Don't Believe" after each action. The verdict is determined by majority. The result is recorded in a structured log.

**This protocol is designed for collecting data in situations where conventional methods (interviews, surveys) produce distorted results due to social desirability bias.** Role-playing reduces this effect because the participant acts as a character, not as themselves.

---

## 2. What Is BIVREST

BIVREST is a data collection protocol using role-playing. It is built on a binary voting mechanism: **"Believe / Don't Believe"**.

The protocol records:
- participant actions
- group voting results
- final verdict

All of this is saved in a structured log.

**Name breakdown:**

| Letter | Meaning | Description |
|---|---|---|
| **B** | Bifurcation | Split between the "Self" and avatar |
| **I** | Inversion | Acting through the opposite role |
| **V** | Verification | "Believe / Don't Believe" mechanism |
| **R** | Role | Avatar as a protective screen |
| **E** | Empty | Deconstruction through the "Empty Chair" |
| **S** | Script | Scenario to be deconstructed |
| **T** | Therapy | Integration of a new scenario |

---

## 3. Who BIVREST Is For

| Audience | Purpose |
|---|---|
| **Researchers** | Collecting structured data on role-based behavior where social desirability interferes with obtaining truthful responses |
| **Psychologists** | Recording group dynamics and moments of role exit |
| **Game Designers** | A ready-made performance assessment mechanic for embedding into games |
| **AI/ML Engineers** | A protocol for collecting labeled data for model training |

### 3.1. Key Differences from Alternatives

| Parameter | BIVREST | Psychodrama / CBT / Focus Groups |
|---|---|---|
| **Avatar** | Maximally different from self | Role is close to self or absent |
| **Verification** | Binary group voting | Authoritative verdict of expert / facilitator |
| **Penalty** | For role mismatch — loss of resource | No penalty — may perform unconvincingly |
| **Empty Chair** | On repeated "Don't Believe" — exit from role | Requires presence of a second person (in psychodrama) |
| **Role Change** | Mandatory (via game mechanics) | Can hide behind the mask indefinitely |
| **Data Format** | Structured log (JSON/CSV) | Qualitative description, difficult to structure |

---

## 4. How BIVREST Works

### 4.1. Protocol Participants

| Role | Description |
|---|---|
| **Group** | Minimum 3 people, vote after each action |
| **Observer** | Records voting results and maintains the log |
| **Facilitator** | Manages the session, assigns tasks (optional) |

### 4.2. Voting Criteria

BIVREST does not prescribe a specific criterion — it is defined before the start of work.

**Examples of criteria:**
- "Does this action match the role?"
- "Does this look convincing?"
- "Is this truthful within the game's context?"

The group votes "Believe / Don't Believe" relative to the specified criterion.

### 4.3. Protocol Stages

| Letter | Stage | Action |
|---|---|---|
| **B** | Believe / Don't Believe | The group votes according to the specified criterion |
| **I** | Information | Information is presented for assessment |
| **V** | Voting | Each participant casts their vote |
| **R** | Record | Voting results are recorded |
| **E** | Evaluate | Verdict is determined by majority |
| **S** | Store | Structured log is saved |
| **T** | Transfer | Data is handed over for analysis |

### 4.4. Full Cycle of One Iteration
Participant Action → Group Voting → Result Recording → Log

text

Each iteration produces one entry in the log.

---

## 5. Implementation of BIVREST in the UNIVERSE 69 Game

UNIVERSE 69 is a game in which BIVREST is embedded as a built-in mechanism. The full rules, cards, and roles are in a separate repository:

**→ [UNIVERSE 69 on GitHub](https://github.com/olesyalazareva/universe69)**

### 5.1. How BIVREST Is Embedded in UNIVERSE 69 Mechanics

| UNIVERSE 69 Mechanic | Role in BIVREST |
|---|---|
| **Task cards** | Generate information for assessment (stage I — Information) |
| **Avatars (roles)** | Provide context for evaluation |
| **"Believe / Don't Believe" voting** | Core verification mechanism (stage B — Believe) |
| **"Chance" tokens** | Resource lost on "Don't Believe" (penalty mechanism) |
| **"Empty Chair"** | Exit from role on repeated "Don't Believe" (stage E — Empty) |
| **Logging** | Recording all actions and votes (stages R, E, S) |

### 5.2. Game Cycle with BIVREST
Player chooses an avatar (role)

Player receives a task card

Player performs the task as their avatar

Group votes "Believe" or "Don't Believe"

If "Don't Believe" — player loses a "Chance" token

If two "Don't Believe" in a row — player exits the role ("Empty Chair")

Results are written to the log

text

### 5.3. What This Connection Provides

| For the Game | For Research |
|---|---|
| Clear performance assessment criterion | Structured data |
| Objectivity through group decision | Binary labels for model training |
| Penalty for unconvincing performance | Recording of role-breakdown moments |
| Role exit mechanics | Data on group dynamics |

### 5.4. Log Format in UNIVERSE 69

| Field | Type | Description |
|---|---|---|
| `session_id` | string | Session identifier |
| `round` | integer | Round number |
| `player_id` | string | Player identifier |
| `avatar` | string | Player's role |
| `task` | string | Card task |
| `action_text` | text | Performance (what was said/done) |
| `votes_believe` | integer | Number of "Believe" votes |
| `votes_dont_believe` | integer | Number of "Don't Believe" votes |
| `verdict` | string | "Believe" or "Don't Believe" |
| `tokens_lost` | integer | Number of tokens lost |
| `empty_chair` | boolean | Whether role was exited |

BIVREST can be used with other role-playing systems, but in UNIVERSE 69 it is implemented as a complete mechanic.

---

## 6. Limitations

- Voting results reflect the group's opinion, not objective truth
- The protocol does not guarantee consistency of assessments across different groups
- Multiple sessions are required for statistically significant data
- No ready-made dataset is provided

---

## 7. Citation

```bibtex
@misc{lazareva2025bivrest,
  author = {Lazareva, Olesya},
  title = {BIVREST: Group Assessment Protocol for Role-Based Behavior},
  year = {2025},
  howpublished = {GitHub},
  url = {https://github.com/olesyalazareva/bivrest-method}
}
8. Repository Structure
text
bivrest-method/
├── README.md                          # Full protocol description (Russian)
├── README.en.md                       # Full protocol description (English)
├── LICENSE                            # MIT License with commercial clause
├── protocol_specification.md          # Technical specification (Russian)
├── protocol_specification.en.md       # Technical specification (English)
├── annotation_guide.md                # Data annotation guide (Russian)
├── annotation_guide.en.md             # Data annotation guide (English)
├── session_example.txt                # Sample log (Russian)
├── session_example.en.txt             # Sample log (English)
└── logs/                              # Folder for additional log examples
8.1. File Contents
File	Description
README.md	Full protocol description: problem, audience, mechanics, limitations
README.en.md	English version of README.md
LICENSE	License agreement
protocol_specification.md	Technical specification: log format, fields, data types, validation examples
protocol_specification.en.md	English version of protocol_specification.md
annotation_guide.md	Instructions for annotating collected data for model training
annotation_guide.en.md	English version of annotation_guide.md
session_example.txt	Example filled log from one session (Russian)
session_example.en.txt	English version of session_example.txt
logs/	Folder for storing additional log examples
9. Use Cases
Training LLMs to recognize subtle emotional signals in text

Developing models for distinguishing genuine from deceptive statements

Creating behavioral datasets for human-AI interaction research

10. Author and Contact
Olesya Lazareva
Psychoanalyst-Sexologist, Game Technician with 25 years of experience

Telegram: @olesyalazarevalove

Email: psi-tech@yandex.com

Method status: Registered in NRIS

11. License and Terms
Non-commercial use (scientific research, open-source projects) — free with mandatory attribution and link to this repository

Commercial use (selling AI solutions based on BIVREST, corporate implementations) — by agreement with the author

⭐ If this method is useful for your work, star the repository — so other researchers and engineers can find it.
