# LeWM Mastery Moat Standard

## Core doctrine

We are not trying to move fast in the shallow sense.

We are trying to compound faster than everyone else by making every unit of work real, tested, logged, and reusable.

The standard:

> Fly what we test. Test what we fly.

Nothing counts because it was watched, skimmed, saved, or discussed.

Work counts only when it survives a gate:

- derivation gate;
- reproduction gate;
- adversarial gate;
- teach-back gate;
- public artifact gate.

## What makes this hard to catch

The moat is not one insight.

The moat is a loop repeated longer and cleaner than other people can tolerate:

1. Read from first principles.
2. Predict before consuming.
3. Derive the math.
4. Implement the core mechanism.
5. Reproduce the baseline.
6. Break the system with adversarial tests.
7. Log the failure.
8. Update the model.
9. Teach it back without notes.
10. Publish the artifact.

Most people stop at step 2 or 3 and call it learning.

We do not.

## Quality over quantity, without becoming slow

Quality over quantity does not mean slow.

It means:

- fewer targets;
- tighter loops;
- cleaner artifacts;
- more verification;
- less rework;
- no fake progress.

Speed comes from removing waste, not skipping rigor.

The rule:

> Move only as fast as the verification loop can support.

If verification breaks, speed is fake.

## The Elon-standard interpretation

The standard is not celebrity worship. The standard is engineering discipline:

- first-principles reduction;
- aggressive deletion of unnecessary parts;
- tight feedback loops;
- physical or executable proof;
- direct inspection of failure;
- high tolerance for hard work;
- low tolerance for excuses;
- no respect for untested claims.

If a claim cannot be derived, tested, reproduced, or defended, it is not yet part of the operating model.

## Mastery gates

### Gate 1: Prediction gate

Before reading a paper, write:

- what problem the paper likely solves;
- what method it likely uses;
- what objective it likely optimizes;
- what ablation should matter;
- what result would falsify the current model.

No prediction log means reading has not started.

### Gate 2: Derivation gate

For every central equation:

- define every symbol;
- derive every step;
- identify hidden assumptions;
- write the analogous equation alone.

No derivation means no mastery.

### Gate 3: Reproduction gate

For every reproduction target:

- pin repo version;
- pin environment;
- log hardware;
- run baseline;
- compare numbers to paper;
- record divergence and likely cause.

No runnable result means no reproduction.

### Gate 4: Adversarial gate

For every claimed understanding:

- find the failure case;
- ask what breaks if an assumption changes;
- create a counterexample;
- explain the boundary.

No boundary means no understanding.

### Gate 5: Teach-back gate

Explain the idea:

- in 90 seconds;
- with the core equation;
- with one failure mode;
- with one comparison to an adjacent method;
- without notes.

No teach-back means the idea is not owned.

### Gate 6: Public artifact gate

Every completed unit creates one public artifact:

- reading log;
- derivation;
- experiment log;
- failure log;
- reproduction note;
- code commit.

No artifact means the session was performative.

## Slow-and-sure cadence

Daily floor:

- 60 minutes.

Weekly deep block:

- 6 to 8 hours.

Weekly output:

- one public artifact;
- one derivation or reproduction improvement;
- one failure log entry if the model broke;
- one Sunday review.

We do not rush the field. We outlast it with better loops.

## What we refuse

We refuse:

- paper collecting;
- shallow summaries;
- leaderboard hacking without mechanism;
- novelty before baseline reproduction;
- moving past math gaps;
- private-only notebooks;
- untested claims;
- broad plans without deliverables;
- rushing because someone else is loud.

## What we optimize

We optimize:

- correctness;
- reproducibility;
- taste in problem selection;
- derivation depth;
- implementation truth;
- experimental honesty;
- failure recovery speed;
- public credibility.

## The compounding stack

Each completed cycle should improve at least one layer:

1. **Math substrate**: linear algebra, probability, information theory, optimization.
2. **Architecture substrate**: JEPA, LeWM, predictive coding, world models.
3. **Implementation substrate**: PyTorch, JAX, reproducible training, evaluation harnesses.
4. **ARC substrate**: task structure, abstraction, program induction, evaluation.
5. **Communication substrate**: teach-back, public logs, defensible claims.
6. **Original contribution substrate**: one reproducible improvement that others can test.

If a session improves none of these layers, it is waste.

## The next product step

LeWM Mastery Gym must encode this standard directly into the interface.

The app should not merely display progress. It should prevent false progress.

Required moat features:

- blocked paper states;
- forced current-model entry;
- derivation gap escalation;
- teach-back timer;
- adversarial challenge mode;
- public artifact checklist;
- weekly mastery ratio;
- reproduction tracker;
- claim-to-test mapping.

The app is successful only if it changes behavior.

## One-sentence operating rule

We do fewer things than everyone else, but every thing is derived, tested, reproduced, attacked, logged, and taught back until it becomes hard to catch.

