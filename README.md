# chessbrah-habits

A Claude Code plugin that coaches chess habits based on the [ChessBrah "Building Habits"](https://www.youtube.com/playlist?list=PLUjxDD7HNNThwCNW3f36RZcMxPwQIjYae) series.

Given a chess position, it applies a strict rule-priority decision tree and returns a deterministic recommendation. Same position + same level = same recommendation.

## Install

```
/add-marketplace github:jeffwindsor/chessbrah-habits
/install chessbrah-habits@jeffwindsor-chessbrah-habits
```

## Usage

Provide your position in any format and specify a level:

```
Level 2. White. 1.e4 e5 2.Nf3 Nc6 3.Bc4 — your turn.
```

```
I'm Black at Level 3. They just played 3.Bc4.
```

The coach will restate the board position, apply the rule tree, and return:

```
Board: Bc4 Nf3 e4 | Nc6 e5 — Black, move 3

→ Nf6  [R6: Development]
Develops knight, attacks e4.

R1✓ R2✓ R3✓ R4✓ R5✓ R6✗
```

## Levels

| Level | Key habits | Restrictions |
|-------|-----------|-------------|
| 1 | Always trade, center, castle | No tactics, no premoves, no gambits, no sacrifices |
| 2 | Basic tactics (pin, fork, skewer, discovery) | No gambits, no sacrifices, premoves < 10s |
| 3 | Advanced tactics, openings, active play | No gambits, no sacrifices |
| 4 | Endgame theory, pawn structures, trade management | Never resign |

## Decision Framework

At every move, the coach works through the rules in strict priority order and stops at the first rule that fires. The trace at the bottom of every response shows exactly where it stopped and why.

The board restatement at the top of every response is a checkpoint — verify it before trusting the recommendation.
