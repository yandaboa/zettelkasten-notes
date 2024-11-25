
A separate field from supervised/unsupervised
- in supervised learning, a supervisor helps the model learn both correct and abstractable behavior — unrealistic in interactable systems. Not realistic to provide correct examples that also always generalize — there will be unforeseen situations
- in unsupervised learning, the goal is to extrapolate patterns or structures in heaps of data. Goal is different from RL, since you're not maximizing reward

A few challenges:
- having to balance exploring new behaviors with sticking to known, practiced, well-rewarding ones.
- RL models always already are "whole"

**Components of a RL Model**

	policy

The policy is what determines behavior of the agent, given an input of its current state. This is what is being changed and improved to maximize rewards.

	reward

The reward is given directly by the environment. It is analogous with human concepts like pleasure, and in the cases of negative reward, pain.

	value

Essentially a prediction of reward to come. For example, the policy could ignore short term reward to take a choice that provides more value — the choice predicted to give more rewards down the line.
- secondary to reward, since value only exists given reward
- still, **more important** than reward

	model

Like a simulation of the real-world system. The model can help reinforcement systems with *planning*, where multiple outcomes are experienced before it happens. Functions as a part of the RL agent! Not the same as the environment. Modern agents do zero planning to a lot of planning - it varies.