# There Is No Spoon

A machine learning primer built from first principles. Written for engineers who want to reason about ML systems the way they reason about software systems.

## What This Is

A high-signal, low-noise reference that covers ML fundamentals through the lens of **when to reach for which tool and why**. Not a textbook. Not a tutorial. A mental model.

Covers:
- The neuron, composition, and what depth and width actually buy you
- Learning as optimization — derivatives, chain rule, backpropagation, and why things get stuck
- Generalization — why overparameterized networks work when classical theory says they shouldn't
- Representation — features as directions, superposition, distributed knowledge
- The combination rule family — dense, convolution, recurrence, attention, graph ops, state-space models
- The transformer — self-attention, multi-head attention, FFN as volumetric lookup, residual connections
- Encoding — what gets preserved, what gets lost, and why encoder choice is the ceiling
- Learning rules — backprop, Hebbian, contrastive, energy-based, and their tradeoffs
- Frameworks — supervised, self-supervised, RL, GANs, diffusion
- Topology — matching architecture to problem structure
- Gates as control systems — primitives, composition, branching, recursion, and the math toolbox

## Read It

The primer is a single markdown file: **[ml-primer.md](ml-primer.md)**

## Origin

This was built through an extended conversational exploration between a software engineer and Claude. The analogies (polarizing filters, paper folding, gear trains, pipeline valves, shadow projections) emerged from bridging deep software engineering intuition into ML concepts. The syllabus tracked what was covered: **[SYLLABUS.md](SYLLABUS.md)**

## Contributing

PRs welcome. The goal is high signal — if you can explain a concept more clearly, fix an error, or add a section that fills a gap, open a PR. Keep the tone: direct, concrete, analogies over notation, when-to-use over how-it-works.

## License

MIT
