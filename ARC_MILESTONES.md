# ARC Milestones

## 2026-05-02 — Foundation Reset Before EBM / JEPA

### Correction

Session 1 initially jumped to energy-based models before establishing the minimum primitives.

This is a sequencing error. The foundation must be:

1. Scalars, vectors, matrices.
2. Functions as input-output maps.
3. Dot products and similarity.
4. Norms and distance.
5. Optimization as "find the input that makes a function small."
6. Probability only after energy is understood as a score.
7. Energy-based models.
8. JEPA-style representation prediction.

### Correct starting point

Start with the question:

What does it mean to represent an object as a vector, and what does it mean for two vectors to be close?

### First 60-minute block deliverable

Produce a derivation in `ARC_DERIVATIONS.md` covering:

- vector as an ordered list of numbers;
- dot product as weighted overlap;
- norm as length;
- squared distance as \(\lVert a-b\rVert_2^2\);
- why minimizing squared distance is the primitive behind many prediction losses.

### Success test

Explain why:

\[
\arg\min_y \lVert y-\hat{y}\rVert_2^2
\]

means "choose the candidate closest to the target under squared Euclidean distance."
