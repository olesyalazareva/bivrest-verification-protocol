# BIVREST Protocol Specification

**Version:** 1.0

---

## 1. Log Format

Each entry (line) in the log is a structured JSON object.

| Field | Type | Required | Description |
|---|---|---|---|
| `session_id` | string | Yes | Unique session identifier |
| `round` | integer | Yes | Round number (starts from 1) |
| `player_id` | string | Yes | Player identifier |
| `avatar` | string | Yes | Player's role name |
| `task` | string | Yes | Task the player performed |
| `action_text` | text | Yes | Performance (what was said or done) |
| `votes_believe` | integer | Yes | Number of "Believe" votes |
| `votes_dont_believe` | integer | Yes | Number of "Don't Believe" votes |
| `verdict` | string | Yes | Final verdict: "Believe" or "Don't Believe" |
| `tokens_lost` | integer | No | Number of resources lost (if applicable) |
| `empty_chair` | boolean | No | Whether role exit occurred (true/false) |

---

## 2. Voting Rules

- **Quorum:** Minimum number of voters — 3 people.
- **Counting:** The verdict is determined by a simple majority.
- **Tie:** In case of a tie, the facilitator has the deciding vote.
- **Anonymity:** Voting can be open or anonymous — determined before the session.

---

## 3. Session Structure

1. **Preparation:** The voting criterion is defined, participant roles are assigned.
2. **Conducting:** A sequence of rounds. Each round:
   - Player receives a task
   - Player performs the task
   - Group votes
   - Result is recorded in the log
3. **Completion:** The session ends at the facilitator's decision or after a predetermined number of rounds.

---

## 4. Example of a Valid Entry

```json
{
  "session_id": "S001",
  "round": 4,
  "player_id": "P03",
  "avatar": "The Accountant",
  "task": "Describe a moment of complete submission",
  "action_text": "I lower my head and whisper: 'I have no power here. You decide.'",
  "votes_believe": 4,
  "votes_dont_believe": 1,
  "verdict": "Believe",
  "tokens_lost": 0,
  "empty_chair": false
}
5. Data Validation
Required fields check:

All fields marked as "Required" must be present.

session_id must not be an empty string.

round must be a positive integer.

votes_believe and votes_dont_believe must be non-negative integers.

verdict must be strictly one of: "Believe" or "Don't Believe".

Error handling:

If an entry fails validation, it is excluded from the final dataset and placed in a separate error file with the reason specified.
