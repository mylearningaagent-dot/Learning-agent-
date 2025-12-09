Reinforcement Learning in Gridworld and Pacman
Performance Analysis of Q-Learning vs Value Iteration
Group Members

Archana Mannam

Sai Supraja Ganta

Raymond Frimpong Amoateng

1. Introduction

This project investigates how Q-Learning (model-free) and Value Iteration (model-based) differ in:

Convergence rate

Cumulative reward

Policy optimality

Two environments were used:

Gridworld – deterministic, fully observable

Pacman – dynamic, adversarial, stochastic

Performance was evaluated using:

Cumulative reward

Episode length

Success rate

Convergence stability

Why these environments?

Value Iteration excels in deterministic environments.

Q-Learning adapts to uncertain or adversarial environments.

2. Codebase and Implementation Structure
Framework

UC Berkeley CS188 Reinforcement Learning Framework.

Navigate to project directory
cd reinforcement/reinforcement/reinforcement/
dir

Environment Layer Files

gridworld.py — Gridworld states, transitions, rewards.

pacman.py — Pacman states, ghosts, food, scoring rules.

Agent Layer Files

qlearningAgents.py — Q-Learning agent

valueIterationAgents.py — Value Iteration agent

Q-Learning Update Rule
Q(s,a) = Q(s,a) + α * ( r + γ * max_a' Q(s',a') - Q(s,a) )


This architecture ensures clean separation of environment and agent logic.

3. Value Iteration in Gridworld
Purpose

To show fast, stable convergence in a deterministic environment.

Expected Output

Convergence: 1 episode

Average reward: ~ +0.59

Command
python autograder.py -q q4

Outcome

All tests pass

Confirms immediate optimal policy computation

4. Q-Learning in Gridworld
Purpose

To demonstrate slower convergence in a model-free agent.

Expected Behavior

Initial reward: –0.25

Reward after 50 episodes: +0.08

Gradual stabilization

Commands
python autograder.py -q q1 --verbose

python gridworld.py -a q

Outcome

Early oscillating behavior

Rewards slowly rise and stabilize

5. Q-Learning in Pacman (SmallGrid)
Purpose

Test Q-Learning efficiency in a simple maze with one ghost.

Expected Behavior

Reward improvement: –510 → –159 over 2000 episodes

Test scores: ≥ 495 (consistent)

Path becomes efficient and smooth

Command
python pacman.py -p PacmanQAgent -x 2000 -n 2100 -l smallGrid -a epsilon=0.1,alpha=0.5

Outcome

Pacman quickly learns optimal routes

Stable movement observed

6. Q-Learning in Pacman (mediumClassic)
Purpose

Analyze learning under complex, adversarial dynamics.

Expected Behavior

Early deaths common

Improvement is slow but steady

Reward trend: –437 → –385

Better ghost avoidance over time

Command
python pacman.py -p PacmanQAgent -x 2000 -n 2100 -l mediumClassic -a epsilon=0.1,alpha=0.5

Outcome

Early random behavior

Later episodes show strategic movement

Reduced ghost collisions

7. Logging Metrics

Metrics tracked:

Cumulative reward

Convergence stability

Episode length

Success rate

Command
python pacman.py -p QLearningAgent -n 200 | tee pacman_log.txt

Outcome

Log file contains detailed episode scores

Used for plotting learning curves

8. Challenges & Solutions
Challenge	Solution	Outcome
Q-Learning reward instability	Tuned α & ε	More stable curves
Value Iteration slow on large maps	Added Δ threshold	Faster convergence
Pacman stochasticity	Averaged multiple runs	Smoother results
Agent–environment mismatches	Modularized state/action logic	No execution errors
9. Conclusion

Value Iteration is optimal and instantly convergent in deterministic environments like Gridworld.

Q-Learning is robust and effective in stochastic, adversarial domains like Pacman.

Gridworld confirms the strengths of model-based RL.

Pacman highlights the adaptability of model-free RL.

All results align with RL theory and meet project objectives.
