# Engine52

A crossplay multiplayer trick-taking card game (Oh Hell–style bidding) built in Unreal Engine 5.8, on top of Epic's Lyra framework and the Gameplay Ability System.

<!-- TODO: screenshot or GIF of a hand being played -->
![gameplay placeholder](docs/screenshot-placeholder.png)

## Play it

<!-- TODO: link to the packaged build (GitHub Release or itch.io) once one exists -->
🎮 [Download a playable build](#)

## Overview

Engine52 is a solo project reworking Lyra's meta-framework — Experiences, Game Feature plugins, the Gameplay Ability System, EOS-backed sessions — around a turn-based card game instead of Lyra's default FPS gameplay. The core loop: bid how many tricks you'll take before a round is played, then play cards following suit, scored against how close your bid landed.

## Tech stack

- **Engine**: Unreal Engine 5.8, C++
- **Framework**: Lyra Starter Game (Experience/Game Feature architecture), stripped of its FPS-specific gameplay
- **Multiplayer**: Gameplay Ability System (GAS) driving turn/phase state and legal-move validation; Epic Online Services (EOS) for crossplay sessions across PC, console, and mobile

## Architecture highlights

- **Turn/phase state machine via GameplayTags** — `State.Phase.Bidding` / `Playing` / `Scoring`, `State.Turn.Active` — rather than hand-rolled bools, gating ability activation the same way Lyra gates combat abilities.
- **Hidden information over replication** — each player's hand replicates `COND_OwnerOnly`; only played cards become public state on GameState.
- **Rulesets as data** — house rules and scoring variants ship as separate Game Feature plugins + Experience assets, swappable per lobby without branching gameplay code.

<!-- TODO: expand this section as more of the architecture doc's design actually lands in code -->

## Status

- [ ] Base Lyra project stripped down and building clean
- [ ] Own Game Feature plugin scaffolded
- [ ] Bidding/play/scoring loop working locally (no networking)
- [ ] Replicated hidden hands + turn gating working over a listen server
- [ ] EOS session create/join working
- [ ] First playable build published

## Building from source

This repo contains my own gameplay code layered on top of Epic's Lyra Sample Game — it isn't a complete, buildable project on its own (Lyra's base content isn't redistributed here). To see it running, use the playable build link above instead of compiling from source.

## About

Built by [Jack Hopkins](#) <!-- TODO: link to portfolio/LinkedIn --> — Senior Gameplay/Technical Designer.
