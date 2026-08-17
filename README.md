# entities-gyre

The Gyre hexagon: the simulated things and the actions on them. Rooms, NPCs, contracts, items, and the drivers that act on them.

Setting and loop are **RFD 0085**, "The Gyre — a MUD setting on the loot-action core-loop shell". This repository is content and drivers for that setting; it is not a new architecture. The authoritative zone server is `interactor-gyre`, the client stays Godot unchanged, and transport lives on `transport-ingest-c` and `transport-gateway-c`.

## What is here

| path | what |
|---|---|
| `sim/commons.py` | rung 0: a settlement you can watch, no engine and no model |
| `docs/planner-ladder.md` | the RECTGTN planner ladder, drivers, and the parity gates |
| `docs/mtp-measurements.md` | measured MTP decode numbers, with the spec-off floor beside them |
| `sim/probe.py` | the streaming probe from `qwen38-mtp`, unmodified, kept as the throughput reference |

## Why a planner

RFD 0085 already says NPC companions fill empty party slots when a party is short. That is the whole design constraint in one line: **a companion and a player drive a Spark through the same surface**, or the companion is a different game.

Everything in `docs/planner-ladder.md` follows from taking that seriously — one action surface, parity gates in both directions, and equal budgets rather than a handicapped companion.

## What rung 0 already showed

The scripted greedy driver **thrashes**. Three residents walk four hours to reach the only Spark who can mend, and the mender turns in before any of them arrive; one reverses course twice mid-journey. Greedy re-decides on arrival, so it fails whenever travel time exceeds the need dynamics that motivated the trip.

That is the empirical argument for planning with commitment over a horizon, and it is a better one than the prose version: the baseline is a real opponent that fails in a legible, watchable way rather than a number to be beaten.

## Provenance, and what the setting supplied

`docs/PROVENANCE.md` records what the Gyre already had that the planner ladder would otherwise have invented, where this code came from, and what was deliberately left behind.
