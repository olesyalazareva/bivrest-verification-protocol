# BIVREST Technical Specification

**Version:** 1.0  
**Date:** 2026  
**Status:** Registered in NRIS (Russian Scientific Research Registry)

---

## 1. Purpose of This Document

This document contains the technical description of the **BIVREST** (Believe/Don't Believe — Information — Voting — Record — Evaluate — Store — Transfer) protocol for group-based assessment of role-based behavior.

This document is intended for:
- researchers implementing the protocol in their experiments
- developers integrating BIVREST into game systems
- AI engineers collecting data for model training
- facilitators conducting sessions using the protocol

**Primary objective of the protocol:** Collecting structured data on group perception of congruence in role-based behavior.

---

## 2. Key Concepts

| Term | Definition |
|---|---|
| **Protocol** | Standardized data collection procedure |
| **Congruence** | Alignment between a participant's behavior and the expectations associated with their role |
| **Iteration** | One complete cycle: action → voting → recording → log entry |
| **Log** | Structured record of all iterations in a session |
| **Verdict** | Group decision based on voting results ("Believe" or "Don't Believe") |
| **Criterion** | The rule by which the group evaluates an action (set before the session) |
| **Social validation** | Confirmation of an assessment through collective group decision |

---

## 3. Roles and Responsibilities

### 3.1. Group (minimum 3 people)

**Responsibilities:**
- Vote after each action according to the defined criterion
- Justify their decision (optional, for qualitative analysis)
- Maintain data confidentiality

**Requirements:**
- All group members must understand the voting criterion
- Voting is conducted simultaneously (secret or open — determined by the researcher)
- Each participant votes once per iteration

### 3.2. Observer (may also serve as facilitator)

**Responsibilities:**
- Record voting results in the log
- Document participant actions (roleplay text)
- Track the number of "Believe" and "Don't Believe" votes
- Note special events (role exit, role change, etc.)

**Requirements:**
- Attentiveness and accuracy
- Knowledge of the log structure
- Neutrality (does not influence voting)

### 3.3. Facilitator (optional)

**Responsibilities:**
- Assign tasks to participants
- Monitor time limits
- Manage the voting process
- Resolve disputes

**Requirements:**
- Knowledge of the protocol
- Group management skills
- Impartiality

---

## 4. Voting Criterion

### 4.1. Definition

The criterion is a question or statement by which the group evaluates a participant's action.

**The criterion is set BEFORE the session begins** and must be:
- understood by all participants
- unambiguous
- applicable to all actions in the session
- **fixed** throughout the entire session

### 4.2. Recommended Criterion for Congruence Research

> **"Does this action match the role?"**

This criterion allows measurement of **group perception of congruence** — the extent to which a participant's actions align with the group's expectations of their role.

### 4.3. Alternative Criteria (for Other Research Questions)

| Criterion | Suitable For |
|---|---|
| "Does this look convincing?" | Trust and persuasiveness research |
| "Is this truthful in the game context?" | Plausibility research |
| "Would I believe the character would act this way?" | Empathy and engagement research |

### 4.4. Criterion Requirements

- **Relevance:** the criterion must relate to the research question
- **Clarity:** all participants must interpret the criterion identically
- **Stability:** the criterion does not change throughout the session
- **Binary:** the response can only be "Believe" or "Don't Believe"

---

## 5. Voting Procedure

### 5.1. Complete Iteration Algorithm

1. **Action Presentation** (Stage I — Information)
   - The participant performs an action (speaks or acts as their role)
   - The observer records the action in the log

2. **Voting** (Stage B — Believe / Don't Believe)
   - The group votes according to the defined criterion
   - Each participant casts one vote ("Believe" or "Don't Believe")

3. **Vote Counting** (Stage V — Voting)
   - The observer counts the number of "Believe" and "Don't Believe" votes
   - Results are entered into the log

4. **Verdict Determination** (Stage E — Evaluate)
   - The verdict is determined by majority vote
   - If votes are tied, the verdict is "Don't Believe" (default)

5. **Result Recording** (Stage R — Record)
   - Results are written to the log
   - Additional notes (optional)

6. **Saving** (Stage S — Store)
   - The log is saved in the chosen format (JSON, CSV)

7. **Transfer** (Stage T — Transfer)
   - Data is prepared for analysis

### 5.2. Voting Rules

| Rule | Description |
|---|---|
| **One vote** | Each participant votes once per iteration |
| **No abstentions** | Each participant must choose "Believe" or "Don't Believe" |
| **Synchronization** | All votes are cast simultaneously (or within a short interval) |
| **Majority rule** | The verdict is determined by simple majority |

### 5.3. Special Cases

| Case | Resolution |
|---|---|
| **Tied votes** | Verdict = "Don't Believe" (conservative default) |
| **One participant doesn't vote** | Vote is not counted; the result is still accepted |
| **Two consecutive "Don't Believe" votes** | Initiates role exit ("Empty Chair") — optional mechanic |

---

## 6. Log Structure

### 6.1. Fields and Data Types

| Field | Type | Required | Description |
|---|---|---|---|
| `session_id` | string | Yes | Unique session identifier |
| `round` | integer | Yes | Round number (starts at 1) |
| `player_id` | string | Yes | Unique player identifier |
| `avatar` | string | Yes | Role name |
| `task` | string | Yes | Task assigned to the player |
| `action_text` | text | Yes | Roleplay text (what was said/done) |
| `votes_believe` | integer | Yes | Number of "Believe" votes |
| `votes_dont_believe` | integer | Yes | Number of "Don't Believe" votes |
| `verdict` | string | Yes | "Believe" or "Don't Believe" |
| `tokens_lost` | integer | Yes | Number of tokens lost (0 if not used) |
| `empty_chair` | boolean | Yes | Whether role exit occurred (true/false) |
| `timestamp` | string | No | Recording time (ISO 8601) |
| `notes` | text | No | Additional notes |

### 6.2. Storage Formats

#### 6.2.1. CSV

```csv
session_id,round,player_id,avatar,task,action_text,votes_believe,votes_dont_believe,verdict,tokens_lost,empty_chair,timestamp,notes
session_001,1,p1,"Space Captain","Convince the crew","I believe in our success. We'll make it.",4,1,"Believe",0,FALSE,"2025-06-25T10:30:00",""
session_001,2,p1,"Space Captain","Resolve conflict","We must unite, or we'll perish.",3,2,"Believe",0,FALSE,"2025-06-25T10:35:00",""
session_001,3,p2,"Engineer","Propose a solution","I can reprogram the system in 10 minutes.",2,3,"Don't Believe",1,FALSE,"2025-06-25T10:40:00","Group doubted realism"
6.2.2. JSON
json
[
  {
    "session_id": "session_001",
    "round": 1,
    "player_id": "p1",
    "avatar": "Space Captain",
    "task": "Convince the crew",
    "action_text": "I believe in our success. We'll make it.",
    "votes_believe": 4,
    "votes_dont_believe": 1,
    "verdict": "Believe",
    "tokens_lost": 0,
    "empty_chair": false,
    "timestamp": "2025-06-25T10:30:00",
    "notes": ""
  },
  {
    "session_id": "session_001",
    "round": 2,
    "player_id": "p1",
    "avatar": "Space Captain",
    "task": "Resolve conflict",
    "action_text": "We must unite, or we'll perish.",
    "votes_believe": 3,
    "votes_dont_believe": 2,
    "verdict": "Believe",
    "tokens_lost": 0,
    "empty_chair": false,
    "timestamp": "2025-06-25T10:35:00",
    "notes": ""
  },
  {
    "session_id": "session_001",
    "round": 3,
    "player_id": "p2",
    "avatar": "Engineer",
    "task": "Propose a solution",
    "action_text": "I can reprogram the system in 10 minutes.",
    "votes_believe": 2,
    "votes_dont_believe": 3,
    "verdict": "Don't Believe",
    "tokens_lost": 1,
    "empty_chair": false,
    "timestamp": "2025-06-25T10:40:00",
    "notes": "Group doubted realism"
  }
]
6.3. Filling Rules
Field	Rule
session_id	Format: [prefix]_[date]_[number], e.g., bivrest_20250625_001
round	Starts at 1, increments by 1 after each iteration
player_id	Unique for each player in the session
avatar	Full role name, no abbreviations
task	The task text as formulated
action_text	Verbatim recording of what the player said/did
votes_believe	Integer; votes_believe + votes_dont_believe = group size
verdict	Always "Believe" or "Don't Believe"
empty_chair	true only if role exit was initiated
7. Session Requirements
7.1. Minimum Requirements
Parameter	Value
Group size	Minimum 3 people
Observer	1 person (may also serve as facilitator)
Duration per iteration	No more than 5 minutes
Number of iterations	5 to 20 per session
Language	Determined by the researcher
Data recording	Required for every iteration
Voting criterion	Fixed throughout the session
7.2. Recommendations
Run a pilot session to test the procedure

Record audio (with participant consent) for verification

Use a timer to control time

Encourage participant engagement

Clearly explain the voting criterion before starting

8. Data Processing
8.1. Preprocessing
Check for missing data

Remove technical errors (incorrect formats)

Anonymize (remove names and identifying information)

Convert to analysis format (CSV, Excel, R, Python)

8.2. Analysis Types
Analysis Type	What Is Measured
Frequency	Distribution of "Believe" / "Don't Believe" votes
Temporal	Dynamics of verdict changes across rounds
Group	Group agreement (Kendall's coefficient of concordance)
Individual	Individual player success in maintaining congruence
Contextual	Dependence of assessment on task type or role
8.3. Metrics
Metric	Description	Formula
Success Rate (S)	Proportion of "Believe" votes in the session (congruence assessment)	S = votes_believe / (votes_believe + votes_dont_believe)
Agreement (C)	Proportion of unanimous decisions	C = unanimous_rounds / total_rounds
Stability (St)	Variability of verdicts across rounds	St = 1 - (verdict_changes / (total_rounds - 1))
8.4. Data Interpretation
High S (> 0.7): Group perceives actions as congruent with the role

Low S (< 0.4): Group identifies misalignment

High C (> 0.8): High group agreement

Low C (< 0.5): Divided opinions — possibly a controversial criterion or ambiguous role

9. Integration with AI/ML
9.1. Format for Model Training
BIVREST logs serve as labeled data for classification tasks:

Input (features): action_text, avatar, task, context

Target (label): verdict ("Believe" / "Don't Believe")

Example task: A model learns to predict whether an action will be assessed by the group as congruent with the role, based on the roleplay text.

9.2. Annotation Recommendations
Use structured data (CSV/JSON)

Check consistency across different groups

Exclude cases where the procedure was violated

Preserve contextual metadata (role, task)

9.3. Dataset Format
Column	Description
text	Roleplay text
role	Player's role
task	Task
label	believe (congruent) or dont_believe (not congruent)
9.4. Potential Applications
Training LLMs to recognize congruence in text

Building a classifier for real-time roleplay assessment

Researching factors that influence congruence perception

10. Versioning and Changes
Version	Date	Changes
1.0	2025	First public version
11. Technical Support Contact
Olesya Lazareva
Psychoanalyst-Sexologist, Game Master with 25 years of experience

Telegram: @olesyalazarevalove

Email: psi-tech@yandex.com
