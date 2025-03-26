https://tonyzhaozh.github.io/aloha/?ref=radekosmulski.com

- motivation is to develop a lower-cost system for fine grain manipulation by leveraging learning
- introduces the Action Chunking Transformer (ACT), which is trained on human demonstrations (input is 4 RGB cameras + joint positions, all collected during demo) and produces K next actions (joint positions). Imitation learning!
- instead of a policy that produces the next action, it produces the next K actions
	- action chunking reduces the length of the total MDP of a task - if your policy can effectively solve the MDP over the length of your action chunk (K), you're effectively dividing your MDP by K
	- turns the normally exponentially compounding error of imitation learning into a more linear one - effectively, because you predict K instead of 1 action, you're less sensitive to perturbations in the environment. Those perturbations tend to average out over your action chunk (K), so you dont deviate from expert data distribution as quickly
- in order to get smoother and more responsive trajectories, requery from the policy at the normal control frequency, and then the executed actions are a weighted average from the overlapping action chunks
	- makes it closed loop at every frequency
	- doesnt have to wait for the K actions to be executed and then produce the next K <- this would be a relatively jerky policy
	- weighting scheme is exponential![[Screenshot 2025-03-26 at 3.59.12 PM.png]]

## Further exploration?
- their actual hardware implementation was interesting, w a master and follower arm. Why and how?
- model architecture (relatively simple?) Encodes images and joint positions, and then decodes them. Trained as a conditional VAE with an attention mechanism.
	- this was done because attention is inherently designed for sequence generation, and conditional VAE was used due to the nature of the task - imitation learning, where you map image input to actions
