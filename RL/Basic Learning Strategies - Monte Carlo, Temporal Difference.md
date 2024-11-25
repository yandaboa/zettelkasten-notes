Monte Carlo requires a full episode to play out before using the sequence of rewards to then adjust the state-value functions of the policy. After getting a sequence of rewards, it goes through each of the states experienced and updates their state value functions through this equation:
The Monte Carlo update for the state-value function is given by:
$$
V(s) \leftarrow V(s) + \alpha \left[ G_t - V(s) \right]
$$Where:
- \( G_t \): The total return observed from the episode starting at time \( t \).

In **temporal difference learning**, the state value functions are updated after each update step

$$

V(s) \leftarrow V(s) + \alpha \left[ r + \gamma V(s') - V(s) \right]

$$

  Where:
- $r$: The reward received after transitioning from $s$ to $s'$.
- $\gamma$: The discount factor.
- $V(s')$: The estimated value of the next state.
- $r + V(s')$ is the TD target (essentially, an estimate of $G_t$ from the Monte Carlo update)