# Syllabus

A map, not a rail. Navigate conversationally, glance here to check for gaps.

## The Neuron and Signal
- [x] What a single unit actually computes, geometrically
- [x] Nonlinearities as design decisions (ReLU, sigmoid, tanh, RePU, GELU — what each does to signal and gradient)
- [x] What "linearity" means and why it's the thing you're breaking

## Composition: What Depth and Width Buy You
- [x] Why stacking layers isn't just "more neurons"
- [x] What a layer can represent that a single neuron can't
- [x] Width vs depth as an actual tradeoff with different failure modes

## Learning as Optimization
- [x] What the loss landscape looks like and why it matters
- [x] Gradient descent as a physical process, not an algorithm
- [x] Why things get stuck, and the different ways they get stuck (vanishing gradients, saddle points, sharp vs flat minima)

## Generalization: The Central Mystery
- [x] Why do overparameterized networks generalize at all (they shouldn't, by classical theory)
- [x] Regularization as a design philosophy, not a checklist
- [x] The bias-variance story and where it breaks down

## Architecture as Inductive Bias
- [x] Convolutions encode spatial locality. Attention encodes pairwise relevance. What does each assume?
- [x] Why architecture choice matters more than hyperparameter tuning
- [x] The relationship between structure and the kind of function the network "wants" to learn

## Representation: What Networks Actually Store
- [x] Features, superposition, distributed representations
- [x] Why the internal structure matters for continual learning and knowledge decoupling

## Tangents That Mattered
- Calculus foundations: derivatives as rise-over-run at the limit, power rule derivation from first principles, FOIL
- Chain rule as gear train / unit conversion — each layer is a local derivative, total is the product
- Optical neuron analogy: polarizing filters, Malus's Law, nonlinearity requires matter
- Paper folding model: activation functions as folds, depth creates creases that bend subsequent cuts
- Superposition: not a bug but the mechanism behind generalization; features are directions in layer-wide vector space, not per-node
- HDC vs neural representations: exact algebra vs approximate learned structure
- MoE routes between same-architecture experts by specialization, not by architectural type
- NEAT evolves topology but can't scale; local evaluation of structural changes is the bottleneck
- Greedy layerwise training: locally optimal but globally uncoordinated; interpretability vs performance tension
- Architecture and encoding are paired design decisions, not independent choices
- Eigenvectors/eigenvalues: directions a matrix doesn't bend, eigenvalues as decay rates / per-key TTLs
- Hidden state as belief state (compressed posterior), not a database
- W_h eigenvalues directly predict vanishing/exploding gradients: <1 vanishes, >1 explodes, =1 preserves
- LSTM cell state as additive bypass — same trick as residual connections
- SSMs vs LSTMs: different lineage (control theory vs neural network intuition), converging interface
- Compression hierarchy: task-relevant statistics survive, positional detail lost first, similar events conflated
- FFN as volumetric lookup: expansion activates a neighborhood in learned feature space, contraction blends activated features
- Attention routes information between elements, FFN applies stored knowledge per element — clean division of labor
- Residual connections as running sum of deltas — preservation is the default, each layer adds rather than replaces
- Cross-attention against external datastores uses the same mechanism as encoder-decoder attention
- RoPE: existing linear algebra property (rotation preserves relative dot products) recognized as exact solution to positional encoding
- Transformer assembled from pre-existing components — novel contribution was the composition, not the parts

---

# Part 2: Architectures in Depth

## The Family: Structured Linear Operations
- [ ] Dense, convolution, attention, recurrence, graph ops, state-space models, sparse/structured matrices — what each assumes and restricts
- [ ] The common pattern: choose a combination rule, apply a nonlinearity, repeat

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
- [x] Positional encoding — injecting the structure that attention lacks
- [x] The feed-forward layers — what they do between attention blocks
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

## Learning Rules Beyond Backprop
- [x] Hebbian learning — local updates, no global error signal, biological motivation
- [x] Energy-based models and modern Hopfield networks — attractors and memory
- [x] Contrastive learning — learning representations from similarity, not labels
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

## Gates Around Frozen Models
- [x] The frozen model as a fixed function — what you can and can't control
- [x] Input gating — controlling what the model sees (context management, retrieval, compression)
- [x] Output gating — controlling what the model's output feeds into (routing, filtering, tool dispatch)
- [x] Inter-call state gating — memory management between inference calls as a learned gate
- [x] Training the gate layer without backprop through the model — RL, evolution, distillation

## The Math Toolbox for Gates
- [x] Sigmoid, softmax, sparsemax, straight-through estimators — the practitioner's gating toolkit
- [x] Linear algebra of projection and masking — what it means to gate in vector space
- [x] Geometric intuition: gating as selecting subspaces, rotating between representations, interpolating paths

---

## Surprises
- Superposition is load-bearing for generalization, not just a storage density hack
- Many apparent flaws (noise in SGD, overparameterization, superposition) are functional
- Convolutions and attention aren't antagonistic — they address different structural properties and combine well
- Interpretability and performance pull in opposite directions
- RAG is lossy because embeddings collapse relational structure that the model must re-derive
- External cross-attention with learned gating is the same design pattern as LSTM forget gates
