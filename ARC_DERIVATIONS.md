# ARC Derivations

## 2026-05-02 — Session 1 — Energy-Based Models from First Principles

### Starting gap

Current usable model of energy-based models or JEPA-style prediction: empty / not yet stated.

This means Session 1 starts from the primitive object: a scoring function over compatible and incompatible configurations.

### Core object

Let \(x\) be observed context and \(y\) be a candidate completion, action, latent state, or representation.

An energy-based model defines a scalar function:

\[
E_\theta(x, y) \in \mathbb{R}
\]

Interpretation:

- low energy means \(x\) and \(y\) are compatible;
- high energy means \(x\) and \(y\) are incompatible;
- inference means searching for the \(y\) that minimizes energy:

\[
\hat{y} = \arg\min_y E_\theta(x, y)
\]

This is the core move: instead of directly outputting one answer, the model learns a landscape where good answers sit in valleys and bad answers sit on hills.

### Probabilistic bridge

If we want to turn energy into a probability distribution, define:

\[
p_\theta(y \mid x) = \frac{\exp(-E_\theta(x,y))}{Z_\theta(x)}
\]

where:

\[
Z_\theta(x)=\sum_{y'} \exp(-E_\theta(x,y'))
\]

for discrete \(y\), or:

\[
Z_\theta(x)=\int \exp(-E_\theta(x,y'))dy'
\]

for continuous \(y\).

The normalizer \(Z_\theta(x)\) is the partition function. It is often expensive because it requires summing or integrating over every possible candidate \(y'\).

### Negative log-likelihood

For a correct pair \((x,y)\):

\[
-\log p_\theta(y \mid x)
= -\log \frac{\exp(-E_\theta(x,y))}{Z_\theta(x)}
\]

\[
= E_\theta(x,y) + \log Z_\theta(x)
\]

Training by likelihood therefore has two forces:

\[
\nabla_\theta[-\log p_\theta(y \mid x)]
= \nabla_\theta E_\theta(x,y) + \nabla_\theta \log Z_\theta(x)
\]

The first term lowers the energy of the observed correct pair. The second term raises or redistributes energy over alternatives through the partition function.

### JEPA-style move

JEPA avoids predicting raw pixels/tokens directly. It predicts a representation of the missing or future part.

Let:

\[
z_x = f_\theta(x)
\]

be the context representation, and let:

\[
z_y = g_\phi(y)
\]

be the target representation.

A simple JEPA-style energy can be:

\[
E_{\theta,\phi}(x,y) = \lVert h_\theta(z_x) - z_y \rVert_2^2
\]

where \(h_\theta\) predicts the representation of \(y\) from the representation of \(x\).

The model is not trying to reconstruct every surface detail. It is trying to make the predicted representation land near the target representation while avoiding collapse.

### Collapse risk

If every input maps to the same vector:

\[
z_x = z_y = c
\]

then:

\[
\lVert h_\theta(z_x) - z_y \rVert_2^2 = 0
\]

can become trivial without learning useful structure.

Therefore, JEPA-like methods need architectural, variance, information, masking, predictor, target-encoder, or objective constraints that prevent representation collapse.

### Session 1 success test

By the next checkpoint, explain without notes:

1. What an energy function is.
2. Why inference is an \(\arg\min\).
3. Why the partition function is expensive.
4. Why predicting representations instead of pixels changes the learning problem.
5. Where collapse enters if the representation has no anti-collapse constraint.

### Drill

Derive the negative log-likelihood identity alone:

\[
-\log p_\theta(y \mid x)=E_\theta(x,y)+\log Z_\theta(x)
\]

Deadline: before the next session starts.
