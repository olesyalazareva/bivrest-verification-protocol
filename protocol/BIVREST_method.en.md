# BIVREST Method: Complete Protocol

## Overview

BIVREST (Behavioral Verification through Role-Play and Binary Assessment) is a structured 7-step protocol for generating ground truth data for AI training. The method uses a game-based approach with binary "Believe/Don't Believe" voting to collect authentic behavioral and emotional responses.

---

## The 7 Steps of BIVREST

### Step 1: Preparation
- Select 2-6 participants
- Prepare avatars (maximally different from participants' real selves)
- Set up the "Universe 69" game environment
- Brief participants on rules and mechanics

### Step 2: Character Creation
- Each participant creates an avatar with:
  - Name
  - Backstory (minimal: 3 sentences)
  - Personality traits (5 max)
  - Goals within the game universe

### Step 3: Role Assignment
- Assign initial resources (points/coins) to each avatar
- Define the scenario context (provided in Universe69_rules.md)
- Ensure roles are clearly distinct from participants' real identities

### Step 4: Gameplay Round (Iterative)
- Each round consists of:
  1. Action declaration by a player
  2. Interaction with other avatars
  3. Binary vote by all other players: **"Believe"** or **"Don't Believe"**
  4. Penalty for imitation: if "Don't Believe" votes exceed 50%, the acting player loses resources

### Step 5: Data Collection
- Log every action, vote, and resource change
- Record timestamps for each event
- Store raw data in structured format (CSV/JSON)

### Step 6: Role Switching
- After 3-5 rounds, force participants to switch to a different avatar
- Repeat Steps 3-5 with new roles
- This prevents masking and encourages authentic responses

### Step 7: Annotation & Export
- Use the annotation guide (`/annotation-guide/README.md`) to label data
- Export datasets for AI training
- Include metadata: session ID, participant IDs, avatar traits

---

## Core Mechanics

### Binary Verification
- Every action is verified by peers through a simple "Believe/Don't Believe" vote
- No expert judgment—eliminates bias
- Creates objective ground truth labels

### Penalty for Imitation
- If the majority votes "Don't Believe," the player loses resources
- This incentivizes authentic emotional expression
- Forces participants to act genuinely to succeed in the game

### AI Double for the Empty Chair
- When a participant is absent, their avatar is replaced by an AI "double"
- The AI double behaves based on previously collected data
- This ensures continuity in the game

---

## Pseudocode Example
function bivrest_session(participants, rounds):
initialize_game(participants)
create_avatars(participants)
assign_roles(avatars)

for round in 1 to rounds:
for player in participants:
action = player.declare_action()
votes = []
for other in participants:
if other != player:
vote = other.cast_vote(player.action)
votes.append(vote)

disbelief_ratio = count(votes == "Don't Believe") / len(votes)
if disbelief_ratio > 0.5:
player.lose_resource()

log_event(player, action, votes, disbelief_ratio)

if round % 3 == 0:
switch_roles(participants)

return export_dataset()

text

---

## API Reference

### Core Functions

#### `initialize_game(participants: list) -> GameState`
Initializes game with given participants.

#### `create_avatars(participants: list) -> list[Avatar]`
Creates avatars based on participant inputs.

#### `cast_vote(player: Player, action: Action) -> Vote`
Allows a player to vote "Believe" or "Don't Believe" on another's action.

#### `log_event(player: Player, action: Action, votes: list[Vote], ratio: float)`
Logs a complete round event to storage.

#### `export_dataset(session_id: str) -> Dataset`
Exports all logs as a structured dataset for AI training.

---

## Data Schema

### Session Log (JSON)
```json
{
  "session_id": "BIVREST_2026_06_22_001",
  "timestamp": "2026-06-22T14:30:00Z",
  "participants": ["P1", "P2", "P3"],
  "rounds": [
    {
      "round_number": 1,
      "actor": "P1",
      "action": "offers trade to P2",
      "votes": {
        "P2": "Believe",
        "P3": "Don't Believe"
      },
      "disbelief_ratio": 0.5,
      "resource_change": 0
    }
  ]
}
Validation Metrics
Inter-rater Agreement: High agreement in voting indicates clear signal

Resource Loss Rate: Indicates authenticity pressure effectiveness

Role Switching Impact: Measures change in behavior after role change

References
Original method deposited in NRIS (National Register of Intellectual Property)

Author: Olesya Lazareva

License: Non-commercial with attribution

Related project: UNIVERSE 69
