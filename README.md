# Crashbound

A Castle Crashers–flavored fantasy brawler reimagined with **turn-based combat**. Phase 1 battle-core prototype.

Play it: open `index.html` (no build step — single file, vanilla JS + Canvas).

## The hook: launch → detonate

You control two knights who act on a speed-ordered **timeline**:

- **Brand** (front-line bruiser) — Slash, **Uppercut** (launches an enemy → ✦ airborne), Shove (reorders the enemy column).
- **Wisp** (back-line mage) — Arc Bolt, **Frostbite** (freezes → ❄ frozen), **Meteor** (the detonator).

Set up a launch or freeze, then **Meteor** the vulnerable target for **+20 bonus damage**. Launching/freezing also shoves the enemy back on the timeline, so they lose their turn — every combo is a choice between the tempo lock and the damage payoff.

## Status

Phase 1: positional turn-based combat, timeline, status-stacking, launch→detonate combo, vector-art scene. Single-file, data-driven party (scales past two knights without rework).

Roadmap: combat depth (more statuses, board-shuffle, a boss) → Slay-the-Spire-style roguelite map → 4-knight party with weapons/magic/companions → polish.
