# Transition Reinforcement Learning

This document outlines a new approach to reinforcement learning. We'll need to start from the fundamentals. The [Bellman optimality principle](https://en.wikipedia.org/wiki/Bellman_equation) states:

> An optimal policy has the property that whatever the initial state and initial decision are, the remaining decisions must constitute an optimal policy with regard to the state resulting from the first decision.

The principle is often presented in the formula form.
```math
\max_{\mathbf{a}_0,...,\mathbf{a}_T} \sum_{t=0}^T r(\mathbf{s}_t,\mathbf{a}_t) = \max_{\mathbf{a}_0} \left[ r(\mathbf{s}_0,\mathbf{a}_0) + \max_{\mathbf{a}_1,...,\mathbf{a}_T} \sum_{t=1}^T r(\mathbf{s}_t,\mathbf{a}_t)\right].
```