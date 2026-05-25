# LeWM Mastery Gym — Grok Build Spec

## Product thesis

Build a mastery tool that makes it difficult to fake progress in LeWorldModel, JEPA, ARC-AGI, and world-model research.

The app is not a note-taking tool. It is a training room.

It forces the user through the protocol:

1. predict before reading;
2. derive before intuition;
3. log failure immediately;
4. teach back without notes;
5. block paper completion unless all four criteria are met.

## Target user

Rico Allen: solo founder, self-taught engineer, serious AI learner, working under LeWorldModel Mastery Coach Protocol v3.0.

The user is not trying to become "familiar" with JEPA or LeWM. The user is trying to become a cited practitioner who can reproduce, extend, and defend the line of work.

## Core problem

Most research-study tools reward consumption: papers read, videos watched, notes collected.

This protocol requires proof of mastery:

- prediction before reading;
- derivation of core equations;
- implementation or reproduction artifacts;
- teach-back without notes;
- failure logging when the mental model breaks.

The app must make passive consumption visible and unacceptable.

## Product name

LeWM Mastery Gym

## One-line description

A research mastery cockpit for forcing predict-derive-log-teach-back cycles across LeWM, JEPA, ARC-AGI, and world-model papers.

## Primary user flow

### Flow 1: start a study session

1. User chooses a paper, concept, or math primitive.
2. App asks: "What is your current model of this?"
3. User must write an answer before unlocking notes.
4. App creates a session card with:
   - starting model;
   - likely prerequisite gap;
   - target deliverable;
   - timer;
   - success test.

### Flow 2: paper mastery cycle

For each paper:

1. Prediction log:
   - What problem does the paper solve?
   - What objective do you expect?
   - What ablation do you predict?
   - What result would falsify your model?

2. Derivation log:
   - core equation;
   - symbols defined;
   - step-by-step derivation;
   - gap flag if stuck.

3. Reading log:
   - actual claims;
   - actual method;
   - actual ablations;
   - actual failure modes.

4. Teach-back:
   - 90-second defense;
   - "explain to LeCun / Lucas Maes" mode;
   - no-notes summary.

5. Completion gate:
   - predict complete;
   - derive complete;
   - log complete;
   - teach-back complete.

If any item is missing, the paper status remains `not read`.

### Flow 3: math gap handling

When the user flags a gap:

1. App asks for the exact failed step.
2. Gap becomes a tracked object.
3. If the same gap persists across more than two sessions, the app blocks forward paper progress and creates a 2-hour fill-in block.

Gap categories:

- linear algebra;
- probability;
- information theory;
- optimization;
- PyTorch/JAX implementation;
- RL/world-model substrate.

### Flow 4: weekly review

Every Sunday:

1. Mastery ratio:
   - papers meeting four-criteria / total claimed.

2. Cross-paper connection:
   - one connection that was impossible last Sunday.

3. Slippage index:
   - missed 60-minute sessions;
   - root cause.

4. Calibration trend:
   - prediction vs actual gap shrinking or not.

5. Next week deliverables:
   - papers;
   - derivations;
   - experiments;
   - commits.

## Required screens

### Dashboard

Purpose: show whether mastery is happening or whether the user is consuming.

Components:

- current phase;
- weekly mastery ratio;
- daily 60-minute streak;
- papers truly read;
- derivations completed;
- active math gaps;
- blocked papers;
- next required action.

### Session cockpit

Purpose: run one 60- to 90-minute block.

Components:

- session timer;
- current model prompt;
- target deliverable;
- prerequisite gap box;
- derivation workspace;
- success test;
- commit/log checklist.

### Paper tracker

Purpose: prevent fake paper completion.

Columns:

- paper;
- tier;
- status;
- prediction log;
- derivation;
- reading log;
- teach-back;
- reproduction link;
- failure notes.

Statuses:

- queued;
- predicting;
- deriving;
- reading;
- teach-back pending;
- reproduced;
- mastered;
- not read.

### Derivation dojo

Purpose: math from first principles.

Components:

- equation target;
- symbol table;
- step-by-step scratchpad;
- "where did it break?" field;
- analogous drill generator;
- mastery checkbox.

### Failure log

Purpose: make wrong models useful.

Fields:

- claim I believed;
- where it broke;
- source of correction;
- updated model;
- prevention rule.

### Weekly review

Purpose: enforce Sunday review.

Components:

- mastery ratio;
- slippage index;
- prediction calibration;
- cross-paper connection;
- next week block planner.

## Data model

### Paper

- id
- title
- authors
- year
- tier
- url
- status
- predictionComplete
- derivationComplete
- readingLogComplete
- teachBackComplete
- reproductionStatus

### StudySession

- id
- date
- durationMinutes
- topic
- startingModel
- targetDeliverable
- successTest
- outputType
- completed

### Derivation

- id
- topic
- equation
- symbolTable
- steps
- stuckStep
- gapCategory
- mastered

### Failure

- id
- date
- falseBelief
- breakPoint
- correction
- updatedModel
- preventionRule

### WeeklyReview

- id
- weekStart
- masteryRatio
- slippageCount
- calibrationTrend
- crossPaperConnection
- nextDeliverables

## P0 requirements

### P0-1: Paper completion gate

Given a paper exists in the tracker,
when the user marks it complete,
then the app must verify prediction, derivation, reading log, and teach-back are complete.

If any are missing, the app must label the paper `not read`.

### P0-2: Session starts with current model

Given the user starts a session,
when no current model is entered,
then the app must block session progress.

### P0-3: Derivation gap logging

Given the user gets stuck on a derivation,
when they flag a gap,
then the app must create a tracked math gap with category and stuck step.

### P0-4: Weekly review

Given it is Sunday,
when the user opens the app,
then the weekly review should be the default required action.

### P0-5: Required output per session

Given a session ends,
when no artifact, derivation, code link, experiment log, or drill is recorded,
then the app marks the session performative.

## P1 requirements

- GitHub export to living artifact markdown files.
- ARC-AGI submission tracker.
- Reproduction run tracker.
- Quiz mode for random devil's-advocate checks.
- 90-second defense timer.

## P2 requirements

- Spaced repetition for equations.
- Paper dependency graph.
- Model comparison map.
- GPU run budget tracking.
- Public progress page.

## Non-goals

- This is not a generic notes app.
- This is not a paper summarizer.
- This is not a passive reading tracker.
- This does not replace actual reproduction work.
- This does not mix with Hardseal execution management.

## Visual direction

Mood:

- austere;
- focused;
- research cockpit;
- no gamified cartoon UI;
- no dopamine confetti.

Palette:

- dark neutral base;
- off-white text;
- single cyan/teal accent;
- red only for blocked or failed criteria;
- amber only for gaps or warnings.

Typography:

- serious sans-serif for UI;
- monospace for equations, IDs, and status labels.

Layout:

- left sidebar for phases;
- main cockpit panel;
- right rail for active gaps and next action;
- dense but readable.

## Grok Build prompt

Build a full-stack web app called "LeWM Mastery Gym."

It is a research mastery cockpit for forcing predict-before-reading, derive-before-intuition, failure logging, and teach-back cycles across LeWorldModel, JEPA, ARC-AGI, and world-model papers.

The app should feel like a serious research training room, not a generic notes app.

Use a dark, austere cockpit design with neutral panels, off-white text, teal/cyan accent, red for blocked criteria, and amber for active gaps. Use a readable sans-serif for UI and monospace for equations/status labels.

Create these screens:

1. Dashboard
   - current mission phase;
   - weekly mastery ratio;
   - daily 60-minute streak;
   - papers truly read;
   - derivations completed;
   - active math gaps;
   - blocked papers;
   - next required action.

2. Session Cockpit
   - session timer;
   - "What is your current model of this?" required text box;
   - likely prerequisite gap field;
   - target deliverable;
   - derivation scratchpad;
   - success test;
   - end-session gate.

3. Paper Tracker
   - table of papers;
   - columns: title, tier, status, prediction log, derivation, reading log, teach-back, reproduction status;
   - a paper can only be marked mastered if all four criteria are complete;
   - if any criterion is missing, show status "not read."

4. Derivation Dojo
   - equation target;
   - symbol table;
   - step-by-step derivation workspace;
   - stuck-step field;
   - math gap category;
   - analogous drill assignment.

5. Failure Log
   - false belief;
   - where the model broke;
   - correction;
   - updated model;
   - prevention rule.

6. Weekly Review
   - mastery ratio;
   - slippage index;
   - prediction vs actual calibration trend;
   - cross-paper connection;
   - next week deliverables.

Use this core rule everywhere:

"If predict, derive, log, and teach-back are not complete, the paper is not read."

Seed the app with these initial papers:

- LeCun 2022: A Path Towards Autonomous Machine Intelligence
- I-JEPA
- V-JEPA
- V-JEPA 2
- LeWM, arXiv:2603.19312
- ARC-AGI-3, arXiv:2603.24621
- DreamerV3
- MuZero
- Genie

The app should store data locally or in a simple built-in database depending on what Grok Build supports. Do not require auth for the first version.

Make the primary call to action: "Start 60-minute block."

The first session should default to "Foundation: vectors, dot products, norms, and squared distance."

Include sample data showing:

- one paper blocked because derivation is missing;
- one active math gap in linear algebra;
- one failure log entry;
- one weekly review due.

## First version acceptance test

The build is acceptable if:

1. starting a session requires a current model;
2. paper mastery is blocked unless all four criteria are complete;
3. derivation gaps are visible on the dashboard;
4. weekly review shows mastery ratio and slippage index;
5. the UI makes the next required action obvious.

## Moat upgrade

The app should encode the `LEWM_MASTERY_MOAT_STANDARD.md` doctrine directly into product behavior.

The product should not merely track progress. It should prevent false progress.

Add these as first-class concepts:

- claim-to-test mapping;
- adversarial challenge mode;
- blocked paper states;
- derivation gap escalation;
- reproduction evidence;
- public artifact checklist;
- weekly mastery ratio;
- teach-back without notes.

The key rule:

> Move only as fast as the verification loop can support.

If a session produces no artifact, derivation, code, experiment log, failure log, or drill, the app marks it performative.

If a claim is not derived, tested, reproduced, or defended, the app marks it unowned.
