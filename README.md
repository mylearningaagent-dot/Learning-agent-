Reinforcement Learning in Gridworld and Pacman: Performance Analysis of Q-Learning vs Value Iteration

Group Members
- Archana Mannam
- Sai Supraja Ganta
- Raymond Frimpong Amoateng

1. Introduction

This project investigates how Q-Learning (model-free) and Value Iteration (model-based) differ in terms of:

- Convergence rate
- Cumulative reward
- Policy optimality

The comparison is performed in two reinforcement learning environments:

- Gridworld, which is deterministic and fully observable
- Pacman, which is dynamic, stochastic, and adversarial

The project evaluates algorithm behavior through agent–environment interactions, measuring:

- Cumulative reward per episode
- Convergence time
- Episode length
- Success rate

These environments were selected to highlight the strengths of each algorithm:

- Value Iteration performs best in deterministic environments.
- Q-Learning adapts well to uncertain and adversarial environments.

2. Codebase and Implementation Structure

The project uses the UC Berkeley CS188 RL Framework.

Navigation to the Project Directory:
cd reinforcement/reinforcement/reinforcement/
dir

Environment Layer:
- gridworld.py – defines Gridworld states, transitions, and rewards.
- pacman.py – defines Pacman states, actions, food, ghosts, and rewards.

Agent Layer:
- qlearningAgents.py
  Implements Q-Learning using the update rule:
  Q(s,a) ← Q(s,a) + α [ r + γ max_a' Q(s',a') − Q(s,a) ]

- valueIterationAgents.py
  Implements Value Iteration using full transition models.

This modular architecture ensures clarity, reproducibility, and easy experimentation.

3. Value Iteration in Gridworld

Purpose:
To demonstrate fast convergence in a deterministic environment.

Expected Results:
- Convergence in 1 episode
- Average reward: +0.59

Command:
python autograder.py -q q4

Outcome:
- Autograder passes all tests.
- Confirms immediate convergence and optimal policy selection.

4. Q-Learning in Gridworld

Purpose:
To evaluate model-free learning in a simple environment.

Expected Behavior:
- Initial average reward: –0.25
- Reward after ~50 episodes: +0.08
- Slower but steady convergence

Commands:
python autograder.py -q q1 --verbose
python gridworld.py -a q

Outcome:
- Early episodes show oscillating rewards.
- Rewards gradually improve and stabilize.

5. Q-Learning in Pacman (SmallGrid)

Purpose:
To study learning efficiency in a simple, partially adversarial maze.

Expected Behavior:
- Rewards improve from –510 → –159 over 2000 episodes
- Testing scores consistently exceed 495
- Visual movement becomes efficient and stable

Command:
python pacman.py -p PacmanQAgent -x 2000 -n 2100 -l smallGrid -a epsilon=0.1,alpha=0.5

Outcome:
- Pacman learns optimal routes efficiently.
- Smooth, stable movement demonstrated visually.

6. Q-Learning in Pacman (mediumClassic)

Purpose:
Evaluate learning under complex, stochastic, and adversarial conditions.

Expected Behavior:
- Frequent early deaths
- Slow but steady improvement
- Reward progression: –437 → –385 over 2000 episodes
- Visible improvement in ghost avoidance and pathing

Command:
python pacman.py -p PacmanQAgent -x 2000 -n 2100 -l mediumClassic -a epsilon=0.1,alpha=0.5

Outcome:
- Initial random movement
- Gradual reduction in ghost collisions
- More stable cumulative rewards over time

7. Logging Metrics for Analysis

The project tracks:
- Cumulative reward per episode
- Convergence time
- Episode length
- Success rate (completion of food collection)

Command:
python pacman.py -p QLearningAgent -n 200 | tee pacman_log.txt

Outcome:
- Log file contains detailed episode scores
- Used for plotting and statistical analysis

8. Challenges and Solutions

Challenge                            Solution                                 Outcome
------------------------------------------------------------------------------------------------------
Reward oscillation in Q-Learning     Tuned α and ε                           Stabilized learning curves
Slow Value Iteration on large maps   Introduced convergence threshold Δ      Faster computation
Pacman stochastic behavior           Averaged multiple runs                  Smoother reward curves
Agent–environment inconsistencies    Modularized state/action structures     Seamless execution

9. Conclusion

- Value Iteration is the fastest and most stable in deterministic environments like Gridworld.
- Q-Learning adapts well to stochastic and adversarial environments like Pacman.
- Gridworld highlights the strengths of model-based RL.
- Pacman demonstrates the flexibility and robustness of model-free RL.
- All experimental findings align with theoretical expectations in reinforcement learning.

The project meets all planned objectives, and results are verified through logs, autograder outputs, and visual demonstrations.
