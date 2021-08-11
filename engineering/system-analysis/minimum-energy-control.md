# Minimum Energy Control

### Goal

We already know how to determine if a system is controllable in at most n time steps by analysing its controllability matrix. This is covered in depth in [Controllability](controllability.md).

The motivation for Minimum Energy control is a sort-of extension of the idea of controllability. What if we know that the system is controllable in $$n$$ __time steps, but we want to reach our goal in some $$t > n$$timesteps? 

The problem that this question poses is that we can technically do whatever we want for the first $$t - n$$timesteps \(even random movements\), since we know we can get to our desirable state from any initial state in just $$n $$timesteps.

**Minimum Energy Control** is just the policy of trying to minimize the size of our inputs, such that the system behaves normally. This is generally intuitive, since we'd rather slowly ramp up gradually \(even though we don't HAVE to\) in the first $$t-n $$timesteps, instead of just randomly jittering until we _have_ to start applying large control inputs to reach our desired state.

### Solution's Intuition

We attempt to construct an input that is entirely orthogonal to the nullspace of the controllability matrix, such that we minimize any unnecessary terms that don't contribute to getting us to our desired state. 

{% embed url="https://eecs16b.org/notes/sp21/note12.pdf" %}



