# Reinforcement Learning

# Comparing Algorithms

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



1. **Multi-Armed Bandits**
    1. **ε-Greedy action selection**
        1. Simplest way to balance exploration and exploitation
        2. Pick best action (1-ε) of the time
    2. **Gradient Bandit Algorithm**
        3. Use stochastic gradient ascent to optimise the policy
2. **Dynamic Programming**
    3. **Policy Iteration**
        4. State-value equation is the Bellman equation
        5. Updates estimates based on other estimates (bootstraps)
        6. Requires probability model of the environment
        7. Policy improvement is done by making the policy greedy w.r.t to the state-action-values [which you get cause v(s) = policy(s)*q(s, a)]
        8. Convergence can take many sweeps even when we already have the optimal solution
        9. Applications
            1. Jacks car rental
        10. DP methods perform exhaustive sweeps and so this doesn’t really work if the state space is large
        11. Asynchronous DP methods
            2. Evaluate and improve policy on subset of states
            3. Gives flexibility to choose best states to update
            4. Can perform updates in parallel (on multiple processors)
            5. Still guaranteed to converge to the optimum
3. **Monte Carlo Methods**
    4. Learns the value function based on experience
    5. Estimates the value function by averages sample returns
    6. Can learn value function without knowledge of a model for the probability of the reward and next state
    7. Generating sample games (of Blackjack) required by Monte Carlo methods is easy. The ability of Monte Carlo methods to work with sample episodes alone can be significant advantage even when one has complete knowledge of the environments dynamics
    8. The estimates for each state are independent. The estimate for one state does not build upon the estimate for any other state (as happens in DP). Monte Carlo does NOT bootstrap.
    9. Therefore the computational expense of estimating the value of a single state is independent of the number of states. Therefore one can generate many sample episodes starting from the states of interest, averaging returns from only these states, ignoring all others. This is a third advantage Monte Carlo methods can have over DP methods (after the ability to learn from actual experience and from simulated experience).  
    10. **First visit Monte Carlo Policy Evaluation**
        12. Only tracks the return from the first time a state was visited
    11. **Every visit Monte Carlo**
        13. Tracks the return from ALL times a state was visited
    12. **Monte Carlo Control**
        14. Steps
            6. Evaluates the state-action values (Q)
            7. Improves the policy by making it greedy w.r.t. Q
        15. **Monte Carlo Exploring Starts**
        16. **Monte Carlo with Soft Policy**
            8. Policy improvement is made soft by changing the probability of picking the best action to ε/|A| + (1 - ε)
        17. **Off policy Monte Carlo Control**
            9. Learn Q based on experience generated with behaviour policy
            10. Advantages of off-policy is that the target policy can be deterministic e.g. greedy, while the behaviour policy can continue to sample all possible actions
            11. However, if the behaviour policy isn’t greedy then you only learn in the tail of the episodes
4. **Temporal Difference Learning**
    13. This learns from experience AND bootstraps
    14. Like MC: it does not require a full model of the probabilities, it only requires experience
    15. Unlike MC: TD is fully incremental, learn before final return is known, less memory and computation
    16. TD often converges faster in practice
    17. TD works better with tasks that are continuing with no episodes at all
    18. **TD(0)**
        18. Learns from the latest timestep
    19. **TD Control**
        19. **SARSA**
            12. Learn Q and improve policy while following the policy (on-policy)
            13. Windy grid world
        20. **Q Learning**
            14. Learn Q and improve policy while following behaviour policy (off line)
            15. Example: walking on a cliff with an edge at both ends
            16. This is off-policy and this dramatically simplifies the analysis of the algorithm and enabled early convergence proofs.
        21. **Expected SARSA**
            17. Consider the learning algorithm that is just like Q-learning except that instead of the maximum over next state–action pairs it uses the expected value, taking into account how likely each action is under the current policy.
            18. Expected Sarsa is more complex computationally than Sarsa but, in return, it eliminates the variance due to random selection of the next action.
            19. It tends to perform better than Sarsa 
            20. Moves deterministically in the same direction as SARSA on expectation
            21. Can use on-policy or off-policy
    20. **N-step TD methods**
        22. In many applications one wants to be able to update the action very fast to take into account anything that has changed, but bootstrapping works best if it is over a length of time in which a significant and recognizable state change has occurred.
        23. TD(0) uses 1-step return. MC uses the full return. n-step bridges the TD(0) and MC 
        24. **N-step SARSA**
            22. Combining n-step with SARSA makes a control algorithm (not just a prediction)
5. **Planning and Learning**
    21. Learning the model directly rather than learning the value function and policy
    22. Direct methods have the advantage that they make fuller use of a limited amount of experience and thus achieve a better policy in few environmental interactions
    23. However, direct methods are simpler and are not affected by biases in the design of the model 
    24. **Dyna-Q**
        25. Learns the model alongside learning the state-action values (Q)
    25. **Dyna-Q+**
        26. Keeps track of time since each state-action pair was tried in real environment
        27. Bonus reward is added if it was a long time ago
        28. Incentivised to visit old state-action pairs
    26. **Rollout Planning**
        29. Dyna-Q uses model to reuse past experiences
        30. This uses model to simulate future trajectories
        31. Focus usually on finding best action A for state S
    27. **Monte Carlo Tree Search**
        32. Efficient rollout planner
        33. More general
        34. Stores partial Q as tree and asymmetrically expands tree based on most promising actions
6. **Value Function Approximation**
    28. Solves the curse of dimensionality
    29. Good at generalisation (since some states may not be visited)
    30. It is more compact since the number of parameters is less than the number of states
    31. Generalises: changing one parameter may change value of many states/actions
    32. Learning a value function is a form of supervised learning
    33. **Stochastic gradient descent**
        35. Find the parameter w by minimising the mean-squared error between approximate values and the true value
    34. **Linear value function**
        36. There is only one optimum
        37. **MC gradient updates**
            23. Using the linear value function approximation, MC gradient updates converge to global optimum
            24. TD gradient updates con
        38. **TD gradient updates**
    35. **Semi-gradient TD control**
        39. Called a semi-gradient because U_t also depends on w
7. **Eligibility Traces**
    36. Short term fading memory
    37. The unify and generalise TD and MC methods.
    38. When TD methods are augmented with eligibility traces, they produce a family of methods spanning a spectrum that has MC methods at one end and TD methods at the other. In between the intermediate methods are often better.
    39. Eligibility traces are better than n-step TD methods because they offer an elegant algorithmic mechanism with significant computational advantages.
    40. One advantage is that only a single trace vector is required rather than a store of the last n feature vectors.
    41. Another advantage is that learning occurs continually and uniformly in time. 
    42. It’s also on policy which can be an advantage.
    43. **Λ-return**
        40. Averages all n-step returns
        41. Λ = 0 is same as TD(0) target
        42. Λ = 1 is the same as MC target
    44. **Offline λ-return algorithm**
        43. Waits until the end of an episode then go back over the timesteps updating the weights
        44. Online λ-return algorithm performs best of all
    45. **Semi-gradient TD(λ)**
        45. Performs similarly to offline λ-return but worse at high alpha
    46. ** True online TD(λ)**
        46. Produces identical parameter updates to online λ-return algorithm but is less expensive in memory and time complexity is the same as TD(λ-return**) **which is O(d)
8. **Policy Gradient Methods**
    47. Compact: number of parameters in theta can be much smaller than the number of states
    48. Generalises: changing one parameter may change action in many states
    49. Advantages of optimising the policy directly
        47. Better convergence properties, typically to local optimum
        48. Effective in high-dimensional and continuous action spaces (robotics for example)
        49. Can learn stochastic policies 
    50. **REINFORCE**
        50. Uses MC updates
        51. Large variance in updates (as with any MC method)
        52. Has to wait until end of episode (as any MC method)
    51. **Actor-Critic Methods**
        53. V(s) calculated by the critic is actually one of the best baselines
        54. Good at reducing variance