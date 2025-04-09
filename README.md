# Transition Reinforcement Learning

This document outlines a way to cast reinforcement learning problems to supervised learning problems.

## Bellman Principle of Optimality

We'll need to start from the fundamentals. The [Bellman optimality principle](https://en.wikipedia.org/wiki/Bellman_equation) states:

> An optimal policy has the property that whatever the initial state and initial decision are, the remaining decisions must constitute an optimal policy with regard to the state resulting from the first decision.

This means that any subpolicy of an optimal policy is itself an optimal policy. To give a concrete example of the principle, I'll [quote myself](https://aaltodoc.aalto.fi/items/874eec9f-9841-464e-91fb-ec45b26066c4):
> To put it more concretely, if the shortest route from Helsinki to Turku is Helsinki–Lohja–Salo–Turku, the shortest route from Lohja to Turku must be Lohja–Salo–Turku and for example Lohja–Rovaniemi–Turku is ruled out.

The principle is often presented in the formula form.
```math
R = \max_{a_0,...,a_\infty} \sum_{t=0}^{\infty} \gamma^t r(s_t,a_t) = \max_{a_0} \left[ \gamma^0 r(s_0,a_0) + \max_{a_1,...,a_\infty} \sum_{t=1}^\infty \gamma^t r(s_t,a_t)\right]
```

Here $r$ is the reward, $s$ is the state, $a$ is the action, $\gamma$ is the discount factor forcing the infinite horizon cost to be finite, and $t$ is time.

If we have a function $\pi$, which relates the actions to the states $a=\pi(s)$, we call it a policy. Given a specific policy, the reward function $R$ is only dependent on the state $s$. It's customary to refer the reward function in this case as the value function $V$.
```
R(a,s) = R(\pi(s),s) = V^\pi (s)
```
The value function of the optimal policy is usually marked as V* or simply V.

## Bellman Principle of Optimality Next Steps

The insight to cast the reinforcement learning problem to a supervised learning problem comes from expanding the Bellman optimality principle:
```math
R = \max_{a_0,...,a_\infty} \sum_{t=0}^{\infty} \gamma^t r(s_t,a_t) = \max_{a_0,...,a_T} \left[ \sum_{t=0}^{t=T} \gamma^t r(s_t,a_t) + \max_{a_{T+1},...,a_\infty} \sum_{t=T+1}^\infty \gamma^t r(s_t,a_t)\right]
```
This can be written more briefly as:
```math
R = V(s_0) = \max_{a_0,...,a_T} \left[ \sum_{t=0}^{t=T} \gamma^t r(s_t,a_t) + V(s_{T+1})\right]
```
