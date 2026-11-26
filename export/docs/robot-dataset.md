---
title: "A robot's own dataset, saved"
description: >-
  The walk a robot records on its own host, saved as one volume a reader can open beside the page and
  ask an address of afterwards. The cockpit reads mock data today, and this is the run that
  replaces it.
ktma:
  kind: "planned"
  order: 19
  line: "cockpit-over-the-record"
  products: ["Kletos"]
  platforms: ["browser", "host"]
  claim: >-
    A walk recorded on the robot's own host is read by the cockpit, and an address asked after the
    fact answers from that volume rather than from a sample.
---

## Purpose

To establish that the room a device answers in is a volume the machine wrote rather than a sample the
cockpit shipped with: one walk, recorded on the robot's own host, opened in the cockpit, and asked one
address afterwards from a machine that never met the robot.

## Procedure

1. Run the engine on the robot's host and record a walk as facts, intents and hints.
2. Save that volume as the host's first dataset, with the revision it was written on.
3. Serve the cockpit over that volume rather than over mock data.
4. Ask one address afterwards from a machine that never met the robot.

## Preconditions

- The robot host's first saved dataset. The cockpit reads mock data today, and this is the run that
  supplies the one it reads instead.
- A recording of the walk that a reader can follow beside the page.

## Deliverable

A saved volume from the robot's own host, the cockpit served over it, and one address asked after
the fact.

## Verification

A recorded walk opened in the cockpit from the volume the robot wrote, and an address answered from
a machine that never met it.
