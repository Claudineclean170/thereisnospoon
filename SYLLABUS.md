# Syllabus

A map of the primer's territory. Use this to find topics, identify gaps, or plan a self-study path. The three parts build on each other — Fundamentals establishes the vocabulary, Architectures applies it, and Gates extends it.

---

# Part 1: Fundamentals

## The Neuron and Signal
- [x] The dot product as alignment measurement
- [x] What a single unit actually computes, geometrically
- [x] Nonlinearities as design decisions (ReLU, sigmoid, tanh, RePU, GELU — what each does to signal and gradient)
- [x] What "linearity" means and why it's the thing you're breaking

## Composition: What Depth and Width Buy You
- [x] Why stacking layers isn't just "more neurons"
- [x] What a layer can represent that a single neuron can't
- [x] Width vs depth as an actual tradeoff with different failure modes

## Learning as Optimization
- [x] Derivatives from first principles (FOIL, power rule, the "nudge" method)
- [x] The chain rule as a gear train — each layer is a local derivative, total is the product
- [x] What the loss landscape looks like and why it matters
- [x] Gradient descent as a physical process, not an algorithm
- [x] Why things get stuck: vanishing gradients, saddle points, sharp vs flat minima

## Generalization: The Central Mystery
- [x] Why do overparameterized networks generalize at all (they shouldn't, by classical theory)
- [x] Regularization as a design philosophy, not a checklist
- [x] The bias-variance story and where it breaks down

## Representation: What Networks Actually Store
- [x] Features as directions in layer-wide vector space, not per-node
- [x] Superposition — more features than dimensions, load-bearing for generalization
- [x] Distributed representation and its consequences (no surgical edits, catastrophic forgetting, knowledge-computation entanglement)
- [x] Transfer learning — when it helps, when transplanted layers get destroyed

---

# Part 2: Architectures in Depth

## The Combination Rule Family
- [x] The common pattern: choose a combination rule, apply a nonlinearity, repeat
- [x] Dense, convolution, attention, recurrence, graph ops, state-space models, sparse/structured matrices — what each assumes and restricts

## Convolutions: The Local Pattern Machine
- [x] What a filter actually computes — sliding dot products, feature maps as transformed images
- [x] Pooling, stride, and dilation — different strategies for expanding the receptive field
- [x] Hierarchical feature composition — how edges become textures become objects across layers
- [x] Where convolutions break down — when locality and translation invariance are the wrong bet

## Recurrence and Sequential Processing
- [x] The hidden state as compressed memory — what it preserves, what it destroys
- [x] Vanilla RNNs and why they fail — the vanishing gradient problem through time
- [x] LSTMs and GRUs — gating as learned information management (what to remember, what to forget, what to output)
- [x] Bidirectionality and the tradeoff between causal and full-context processing
- [x] Why attention replaced recurrence for most sequence tasks — and where recurrence still wins

## The Transformer
- [x] Self-attention end to end — queries, keys, values, and what the dot products mean
- [x] Multi-head attention — why parallel attention patterns matter
- [x] Positional encoding — injecting the structure that attention lacks (sinusoidal, learned, RoPE, ALiBi)
- [x] The feed-forward layers — volumetric lookup in learned feature space
- [x] Residual connections and layer norm — keeping signal alive through depth
- [x] Encoder-decoder vs decoder-only — different bets on the task structure

## Graph Networks
- [x] Message passing — nodes inform neighbors, neighbors inform nodes
- [x] What graph structure assumes about the problem — entities and explicit relationships
- [x] Where they excel (molecules, social networks, physics simulations) and where they don't

## State-Space Models (SSMs / Mamba)
- [x] Continuous-time recurrence — what it means to model a process rather than a sequence
- [x] How SSMs relate to recurrence and convolutions (they bridge both)
- [x] The Mamba selective mechanism — input-dependent state transitions
- [x] Why SSMs are gaining ground against transformers for long sequences

## Sparse and Structured Operations
- [x] Low-rank, block-diagonal, butterfly matrices — efficiency through constrained connectivity
- [x] When structure in the operation matches structure in the data vs when it's just a compute shortcut

## Encoding: Getting Data Into the Right Shape
- [x] Trivial vs learned encoders — pixel grids, tokenizers, molecular graphs
- [x] How encoder choices constrain what the combination rule can see
- [x] Encoder-architecture pairing as a joint design decision
- [x] Multimodal alignment — adapters, contrastive training, shared representation spaces

## Learning Rules Beyond Backprop
- [x] Hebbian learning — local updates, no global error signal, biological motivation
- [x] Energy-based models and modern Hopfield networks — attractors and memory
- [x] Contrastive learning — learning representations from similarity, not labels
- [x] Learned loss functions — when you can judge quality but can't formalize it
- [x] Where these learning rules win and where backprop dominates

## Frameworks: What the Training Objective Is
- [x] Supervised, self-supervised, reinforcement learning — different definitions of "correct"
- [x] Diffusion — learning to reverse a noise process, generation by iterative denoising
- [x] GANs — adversarial training, generator vs discriminator
- [x] How frameworks combine with architectures and learning rules independently

## Topology for the Problem
- [x] Matching inductive bias to data structure — a decision framework
- [x] Hybrid architectures — when and how to combine operations
- [x] The role of scale — when architecture matters less because data and parameters compensate
- [x] Practical heuristics — what practitioners actually reach for and why

---

# Part 3: Gates as Control Systems

## Gate Primitives
- [x] What a gate actually is mathematically — scalar gates, vector gates, matrix gates
- [x] Simple gates: pass/block, interpolate, scale — and the functions that implement each
- [x] Complex gates: can a gate be an arbitrary function? Where is the boundary between a gate and a subnetwork?
- [x] Composing gates — AND, OR, NOT analogs in continuous differentiable space

## Branching and Routing
- [x] Conditional computation — hard routing vs soft routing and the differentiability constraint
- [x] Mixture of experts as a branching gate — router selects which path, experts are the branches
- [x] Learned branching: can the network decide its own control flow?
- [x] The Gumbel-softmax trick — making discrete decisions differentiable

## Recursion and Looping Within a Forward Pass
- [x] Adaptive computation time — learned halting within a forward pass
- [x] Universal transformers — shared weights across layers with a learned exit condition
- [x] Subtree recursion — a gate triggers repeated processing of a sub-path before continuing forward
- [x] Fixed-point iteration — running a block until output converges, and why this relates to energy-based models

## The Math Toolbox for Gates
- [x] Sigmoid, softmax, sparsemax, straight-through estimators — the practitioner's gating toolkit
- [x] Linear algebra of projection and masking — what it means to gate in vector space
- [x] Geometric intuition: gating as selecting subspaces, rotating between representations, interpolating paths

---

## Key Insights

Concepts that emerged from exploration and are worth keeping in mind:

- Superposition is load-bearing for generalization, not just a storage density trick
- Many apparent flaws (noise in SGD, overparameterization, superposition) are functional — removing them removes the capability
- Convolutions and attention aren't antagonistic — they address different structural properties and combine well
- Interpretability and performance pull in opposite directions
- Architecture and encoding are paired design decisions, not independent choices
- The transformer was assembled from pre-existing components — the novel contribution was the composition, not the parts
- Attention is mathematically equivalent to Hopfield retrieval with exponential energy
- Residual connections are a running sum of deltas — preservation is the default, each layer adds rather than replaces
- FFN layers are volumetric lookups in learned feature space — attention routes, FFN applies knowledge
- The LSTM cell state uses the same additive bypass trick as residual connections
- When the loss function is too complex to specify, learn it (GANs, RLHF)
- Eigenvalues of the recurrence matrix are literally per-direction information decay rates
