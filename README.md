# Transition Reinforcement Learning

This document outlines a new approach to reinforcement learning. We'll need to start from the fundamentals. The [Bellman optimality principle](https://en.wikipedia.org/wiki/Bellman_equation) states:

> An optimal policy has the property that whatever the initial state and initial decision are, the remaining decisions must constitute an optimal policy with regard to the state resulting from the first decision.

This means that any subpolicy of an optimal policy is itself an optimal policy. To give a concrete example of the principle, I'll [quote myself](https://aaltodoc.aalto.fi/items/874eec9f-9841-464e-91fb-ec45b26066c4):
> To put it more concretely, if the shortest route from Helsinki to Turku is Helsinki–Lohja–Salo–Turku, the shortest route from Lohja to Turku must be Lohja–Salo–Turku and for example Lohja–Rovaniemi–Turku is ruled out.

The principle is often presented in the formula form.
```math
\max_{\mathbf{a}_0,...,\mathbf{a}_\infty} \sum_{t=0}^{\infty} \gamma^t r(\mathbf{s}_t,\mathbf{a}_t) &=& \max_{\mathbf{a}_0} \left[ \gamma^0 r(\mathbf{s}_0,\mathbf{a}_0) + \max_{\mathbf{a}_1,...,\mathbf{a}_\infty} \sum_{t=1}^\infty \gamma^t r(\mathbf{s}_t,\mathbf{a}_t)\right]
```

Here $r$ is the reward, $s$ is the state, $a$ is the action, $\gamma$ is the discount factor forcing the infinite horizon cost finite, and $t$ is time.