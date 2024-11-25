- an approach for learning the Q value of a state-action pair through TD learning
- **Q-value:** the quality of taking an action, $a$, when in state $s$. Essentially, how much return do we expect after taking the action?
- traditionally, can store in table of all state-action pairs

Equations:
The off-policy update for Q-learning is given by:
$$
Q(s, a) \leftarrow Q(s, a) + \alpha \left[ r + \gamma \max_{a'} Q(s', a') - Q(s, a) \right]
$$
The on-policy update for Q-learning (SARSA) is given by:
$$
Q(s, a) \leftarrow Q(s, a) + \alpha \left[ r + \gamma Q(s', a') - Q(s, a) \right]
$$
**Off-policy:** the policy used for the update step is different from the policy used to select actions to take.
- the action is selected with something like $\epsilon-greedy$
- the update step is performed using $\max_{a'} Q(s', a')$
**On-policy**: uses the same policy for both, so the update step would also be performed with $\epsilon-greedy$

The algorithm for performing Q-Learning:
1. initialize Q-table with proper dimensions (usually all 0)
2. initialize environment
3. for i in range(num_episodes):
	1. use $\epsilon-greedy$ to select an action, conditioned on current state
	2. step the environment with the action
	3. collect reward, next state, done, info
	4. use the off-policy update equation to update the Q-value of the state-action pair taken (on-policy makes it SARSA, not Q-learning)
		1. note: Q-learning often converges to optimal Q-function faster, while SARSA is more resilient in a stochastic environment
	5. set the current state to be the new state received