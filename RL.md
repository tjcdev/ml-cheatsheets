# Comparing Algorithms

TODO:
- Add Deep RL section
- Give clearer explanations of the below concepts like https://github.com/FrancescoSaverioZuppichini/Reinforcement-Learning-Cheat-Sheet/blob/master/rl_cheatsheet.pdf

**MC vs. TD vs. DP**



*   DP and TD updates are biased on their initial conditions of the learning parameters. This bias can cause significant problems, especially for off-policy methods and when using function approximators (this is the deadly triad)
*   MC doesn’t suffer from the bias but the high variance means more samples are required to achieve the same degree of learning compared to TD.
*   In practice TD appears to learn more efficiently
*   MC learning is conceptually simple, robust and easy to implement, albeit often slower than TD.

**Direct vs. Indirect Methods**



*   Learning the model of the environment (transition and reward function) is more informative than simply updating our evaluation of how good the current policy is and/or updating our estimation of the optimal policy
*   But that is if our assumptions about the environment (state and action space, Markov Assumption) are correct enough, and the environment dynamics are learnt correctly.

**Offline vs Online Planning**



*   In offline the policy is complete and therefore gives the optimal action for all possible states
*   In offline it can also use as much time as it needs to find policy


# Algorithm Summaries



*   **Multi-Armed Bandits**
    *   **ε-Greedy action selection**
        *   Simplest way to balance exploration and exploitation
        *   Pick best action (1-ε) of the time
    *   **Gradient Bandit Algorithm**
        *   Use stochastic gradient ascent to optimise the policy
*   **Dynamic Programming**
    *   **Policy Iteration**
        *   State-value equation is the Bellman equation
        *   Updates estimates based on other estimates (bootstraps)
        *   Requires probability model of the environment
        *   Policy improvement is done by making the policy greedy w.r.t to the state-action-values [which you get cause v(s) = policy(s)*q(s, a)]
        *   Convergence can take many sweeps even when we already have the optimal solution
        *   Applications
            *   Jacks car rental
        *   DP methods perform exhaustive sweeps and so this doesn’t really work if the state space is large
        *   Asynchronous DP methods
            *   Evaluate and improve policy on subset of states
            *   Gives flexibility to choose best states to update
            *   Can perform updates in parallel (on multiple processors)
            *   Still guaranteed to converge to the optimum
*   **Monte Carlo Methods**
    *   Learns the value function based on experience
    *   Estimates the value function by averages sample returns
    *   Can learn value function without knowledge of a model for the probability of the reward and next state
    *   Generating sample games (of Blackjack) required by Monte Carlo methods is easy. The ability of Monte Carlo methods to work with sample episodes alone can be significant advantage even when one has complete knowledge of the environments dynamics
    *   The estimates for each state are independent. The estimate for one state does not build upon the estimate for any other state (as happens in DP). Monte Carlo does NOT bootstrap.
    *   Therefore the computational expense of estimating the value of a single state is independent of the number of states. Therefore one can generate many sample episodes starting from the states of interest, averaging returns from only these states, ignoring all others. This is a third advantage Monte Carlo methods can have over DP methods (after the ability to learn from actual experience and from simulated experience).  
    *   **First visit Monte Carlo Policy Evaluation**
        *   Only tracks the return from the first time a state was visited
    *   **Every visit Monte Carlo**
        *   Tracks the return from ALL times a state was visited
    *   **Monte Carlo Control**
        *   Steps
            *   Evaluates the state-action values (Q)
            *   Improves the policy by making it greedy w.r.t. Q
        *   **Monte Carlo Exploring Starts**
        *   **Monte Carlo with Soft Policy**
            *   Policy improvement is made soft by changing the probability of picking the best action to ε/|A| + (1 - ε)
        *   **Off policy Monte Carlo Control**
            *   Learn Q based on experience generated with behaviour policy
            *   Advantages of off-policy is that the target policy can be deterministic e.g. greedy, while the behaviour policy can continue to sample all possible actions
            *   However, if the behaviour policy isn’t greedy then you only learn in the tail of the episodes
*   **Temporal Difference Learning**
    *   This learns from experience AND bootstraps
    *   Like MC: it does not require a full model of the probabilities, it only requires experience
    *   Unlike MC: TD is fully incremental, learn before final return is known, less memory and computation
    *   TD often converges faster in practice
    *   TD works better with tasks that are continuing with no episodes at all
    *   **TD(0)**
        *   Learns from the latest timestep
    *   **TD Control**
        *   **SARSA**
            *   Learn Q and improve policy while following the policy (on-policy)
            *   Windy grid world
        *   **Q Learning**
            *   Learn Q and improve policy while following behaviour policy (off line)
            *   Example: walking on a cliff with an edge at both ends
            *   This is off-policy and this dramatically simplifies the analysis of the algorithm and enabled early convergence proofs.
        *   **Expected SARSA**
            *   Consider the learning algorithm that is just like Q-learning except that instead of the maximum over next state–action pairs it uses the expected value, taking into account how likely each action is under the current policy.
            *   Expected Sarsa is more complex computationally than Sarsa but, in return, it eliminates the variance due to random selection of the next action.
            *   It tends to perform better than Sarsa 
            *   Moves deterministically in the same direction as SARSA on expectation
            *   Can use on-policy or off-policy
    *   **N-step TD methods**
        *   In many applications one wants to be able to update the action very fast to take into account anything that has changed, but bootstrapping works best if it is over a length of time in which a significant and recognizable state change has occurred.
        *   TD(0) uses 1-step return. MC uses the full return. n-step bridges the TD(0) and MC 
        *   **N-step SARSA**
            *   Combining n-step with SARSA makes a control algorithm (not just a prediction)
*   **Planning and Learning**
    *   Learning the model directly rather than learning the value function and policy
    *   Direct methods have the advantage that they make fuller use of a limited amount of experience and thus achieve a better policy in few environmental interactions
    *   However, direct methods are simpler and are not affected by biases in the design of the model 
    *   **Dyna-Q**
        *   Learns the model alongside learning the state-action values (Q)
    *   **Dyna-Q+**
        *   Keeps track of time since each state-action pair was tried in real environment
        *   Bonus reward is added if it was a long time ago
        *   Incentivised to visit old state-action pairs
    *   **Rollout Planning**
        *   Dyna-Q uses model to reuse past experiences
        *   This uses model to simulate future trajectories
        *   Focus usually on finding best action A for state S
    *   **Monte Carlo Tree Search**
        *   Efficient rollout planner
        *   More general
        *   Stores partial Q as tree and asymmetrically expands tree based on most promising actions
*   **Value Function Approximation**
    *   Solves the curse of dimensionality
    *   Good at generalisation (since some states may not be visited)
    *   It is more compact since the number of parameters is less than the number of states
    *   Generalises: changing one parameter may change value of many states/actions
    *   Learning a value function is a form of supervised learning
    *   **Stochastic gradient descent**
        *   Find the parameter w by minimising the mean-squared error between approximate values and the true value
    *   **Linear value function**
        *   There is only one optimum
        *   **MC gradient updates**
            *   Using the linear value function approximation, MC gradient updates converge to global optimum
            *   TD gradient updates con
        *   **TD gradient updates**
    *   **Semi-gradient TD control**
        *   Called a semi-gradient because U_t also depends on w
*   **Eligibility Traces**
    *   Short term fading memory
    *   The unify and generalise TD and MC methods.
    *   When TD methods are augmented with eligibility traces, they produce a family of methods spanning a spectrum that has MC methods at one end and TD methods at the other. In between the intermediate methods are often better.
    *   Eligibility traces are better than n-step TD methods because they offer an elegant algorithmic mechanism with significant computational advantages.
    *   One advantage is that only a single trace vector is required rather than a store of the last n feature vectors.
    *   Another advantage is that learning occurs continually and uniformly in time. 
    *   It’s also on policy which can be an advantage.
    *   **Λ-return**
        *   Averages all n-step returns
        *   Λ = 0 is same as TD(0) target
        *   Λ = 1 is the same as MC target
    *   **Offline λ-return algorithm**
        *   Waits until the end of an episode then go back over the timesteps updating the weights
        *   Online λ-return algorithm performs best of all
    *   **Semi-gradient TD(λ)**
        *   Performs similarly to offline λ-return but worse at high alpha
    *   ** True online TD(λ)**
        *   Produces identical parameter updates to online λ-return algorithm but is less expensive in memory and time complexity is the same as TD(λ-return**) **which is O(d)
*   **Policy Gradient Methods**
    *   Compact: number of parameters in theta can be much smaller than the number of states
    *   Generalises: changing one parameter may change action in many states
    *   Advantages of optimising the policy directly
        *   Better convergence properties, typically to local optimum
        *   Effective in high-dimensional and continuous action spaces (robotics for example)
        *   Can learn stochastic policies 
    *   **REINFORCE**
        *   Uses MC updates
        *   Large variance in updates (as with any MC method)
        *   Has to wait until end of episode (as any MC method)
    *   **Actor-Critic Methods**
        *   V(s) calculated by the critic is actually one of the best baselines
        *   Good at reducing variance