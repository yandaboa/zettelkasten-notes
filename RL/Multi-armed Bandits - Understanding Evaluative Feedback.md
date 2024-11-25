[[RL General Notes]]

**The K-Bandits Problem**

When presented with K choices that each provide some reward if chosen, maximize the total reward over n time stamps.
- when exact rewards for each choice are known, problem is trivial

*terminology:*
*t* = step
$A_t =$ action at step t
$R_t =$ corresponding reward at step t
$a =$ arbitrary action
$q_{*}(a) =$ arbitrary action
$$ q_{*}(a) = E[R_t | a_t = a]$$
If value of each action was known, then trivial problem. Thus, in most cases we only have estimates. Estimated value: $Q_t(a)$, we want $Q_t(a)$ to be as close to $q_{*}(a)$ as possible.

In short term, one can be *greedy*, *exploiting* existing knowledge of which choice is best at timestamp $t$. Yet, there may be many actions that we are more uncertain about, but could have a higher true value. Thus, we have to balance *exploitation* and *exploration*, but we can't do both at the same time. There is a conflict created -> need to balance.

# Action-value Methods
definition: methods for estimating value of action and then using estimates to make action selection decisions
- one natural estimation method - averaging the value obtained from an action.
$$ Q_t (a) = \frac{sum\ of\ rewards\ when\ a\ taken\ prior\ to\ t}{number\ of\ times\ a taken\ prior\ to\ t} = \frac{\sum_{i=1}^{t-1} R_i \cdot L_{A_i = a}}{\sum_{i=1}^{t-1} L_{A_i=a}}$$
$Q_t(a)$ will eventually converge to true value given a large enough denominator. If denominator is 0, set to some default (usually 0).

### Selecting action
Could be greedy, just select action with most reward.
$$A_t = argmax_a\ Q_t(a)$$
To learn about other actions, could have a small probability $\epsilon$ where a non greedy action is randomly selected. Called $\epsilon\ greedy$ methods, and as we approach infinite time steps, we eventually learn about all choices. Might not be most practical!

# 10-armed Testbed

Simulate runs for different values of $\epsilon$. Done by generating 10 different true rewards from a normal distribution, and then the actual rewards for those 10 choices where chosen based on a normal distribution based around the true reward. 1000 runs were then run for different values of epsilon, with their rewards averaged.

![[Screenshot 2024-10-10 at 11.41.30 AM.png]]
0.01 improved much slower, but possible to eventually do better than 0.1, since it could select the optimal action more often (0.99% greedy vs 0.9% greedy, which meant that the 0.1 $\epsilon$ can't always select greedy, even if it knows optimal choice)

performance of the different $\epsilon$ depend on reward variance. More variance means more exploration needed, an $\epsilon$ approach much better than always greedy (the greedy is likely to not gauge the best actions well). A low variance means that the greedy approach could actually work well, if variance were to be 0, greedy would be best. Also, exploration is better if rewards were non-stationary. Needs to check if optimum changed.

# Incremental Implementation
Action-value methods estimate the values of actions as simple averages of the past reward received. Yet, can be computationally inefficient to calculate new averages. In order to do the calculation with constant memory and runtime, denote $Q_n$ as estimate of action value given past $n-1$ reward values.
$$\frac{Q_n = R_1 + R_2 + ... + R_{n - 1}}{n-1}$$
Can incrementally update value estimates:
$$Q_{n + 1} = \frac{1}{n} \cdot \sum_{i = 1}^{n} R_i$$
$$Q_{n+1} = \frac{1}{n} (R_1 + R_2 + ... + R_n)$$
$$Q_{n + 1} = \frac{1}{n}(R_n \cdot \frac{1}{n - 1} \cdot (n - 1) \cdot (R_1 + R_2 + ... + R_{n - 1}))$$
simplifies to:
$$ Q_n + \frac{1}{n}[R_n - Q_n]$$
Only need memory for $Q_n$ and $n$, small computations each time. This **update rule** is common to see:
$$New Estimate <- OldEstimate + StepSize[Target - OldEstimate]$$
$[Target - OldEstimate]$ is the error in the estimate. Basically, takes steps toward the target (hence step size).

## Tracking Nonstationary Problems

Averaging methods are appropriate for stationary bandit, but better to weight newer rewards higher when the true value of an action can change over time. In this case, use a constant step size...

![[Screenshot 2024-10-11 at 12.40.29 AM.png]]

since $(1 - a)$ is less than 1, the weight given to $R_i$ decreases as number of intervening rewards increases. Goes down exponentially.

## Convergence
In stochastic approximation theory, for a RL algorithm to eventually converge to true action values by law of large numbers,
$$\sum_{n=1}^{\infty} a_n(a) = \infty$$
$$\sum_{n=1}{\infty}a_n^2(a)<\infty$$
First ensures that step size doesnt go to zero too fast, and that random noise/initial inaccuracies will be accounted for eventually
Second ensures that it does eventually converge - IT DOESNT FOR NON STATIC PROBLEM
- this is a good thing, and non static is most useful for real-world applications

## Optimistic Initial Values
For the sample average method, instead of starting with initial values of 0, start with something *wildly* optimistic! Starting with 5 (when true rewards are mean 1 with low std. dev.), any explored actions are not taken again for a while. Means a lot of exploration happens early.

![[Screenshot 2024-10-11 at 11.39.49 AM.png]]

This method doesn't work as well for constant step size — the initial weight would create permanent bias.

## Upper-Confidence-Bound Action Selection

Exploration doesn't have to be entirely random based on an $\epsilon$ - it's better to account for the specific uncertainty of an action. Use this equation to choose the action at each  timestep:
$$A_t = argmax_a \left[ Q_t(a) + c\sqrt{\frac{\ln t}{N_t(a)}}\right]$$
As t increases, the uncertainty of an action increases, and as that action gets tried more (denominator increase), the uncertainty decreases.
![[Screenshot 2024-10-11 at 12.17.57 PM.png]]
Note the spike at 11! My answer for why it occurs: The spike occurs because all 10 actions have been tried once in the first 10 steps, so an action close to optimal is chosen for the 11th. It drops again afterwards, since the uncertainty of the optimal action decreases, meaning the uncertainty term is greater for an suboptimal choice, leading to it being chosen by argmax.

## Gradient Bandit Algorithms

