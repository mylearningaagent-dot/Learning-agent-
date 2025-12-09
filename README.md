<img width="704" height="105" alt="image" src="https://github.com/user-attachments/assets/706d8d66-c9a9-4084-bb4c-9598b48806d5" />
<body>

  <h1>Reinforcement Learning in Gridworld and Pacman: Performance Analysis of Q-Learning vs Value Iteration</h1>

  <h2>Group Members</h2>
  <ul>
    <li>Archana MannamSai</li>
    <liSupraja GantaRaymond </li>
    <li>Frimpong Amoateng</li>
  </ul>

  <h2 id="introduction">1. Introduction</h2>
  <p>
    This project investigates how <strong>Q-Learning (model-free)</strong> and <strong>Value Iteration (model-based)</strong> differ in terms of:
  </p>
  <ul>
    <li>Convergence rate</li>
    <li>Cumulative reward</li>
    <li>Policy optimality</li>
  </ul>

  <p>The comparison is performed in two reinforcement-learning environments:</p>
  <ul>
    <li><strong>Gridworld</strong> — deterministic and fully observable</li>
    <li><strong>Pacman</strong> — dynamic, stochastic, and adversarial</li>
  </ul>

  <p>The project evaluates algorithm behavior through agent–environment interactions, measuring:</p>
  <ul>
    <li>Cumulative reward per episode</li>
    <li>Convergence time</li>
    <li>Episode length</li>
    <li>Success rate</li>
  </ul>

  <p>These environments were selected to highlight the strengths of each algorithm:</p>
  <ul>
    <li>Value Iteration performs best in deterministic environments.</li>
    <li>Q-Learning adapts well to uncertain and adversarial environments.</li>
  </ul>

  <h2 id="codebase">2. Codebase and Implementation Structure</h2>
  <p><em>Framework:</em> UC Berkeley CS188 Reinforcement Learning Framework.</p>

  <h3>Navigate to the Project Directory</h3>
  <pre><code class="language-bash">cd reinforcement/reinforcement/reinforcement/
dir</code></pre>

  <h3>Environment Layer</h3>
  <ul>
    <li><code>gridworld.py</code> — defines Gridworld states, transitions, and rewards.</li>
    <li><code>pacman.py</code> — defines Pacman states, actions, food, ghosts, and rewards.</li>
  </ul>

  <h3>Agent Layer</h3>
  <ul>
    <li><code>qlearningAgents.py</code> — Q-Learning agent.</li>
    <li><code>valueIterationAgents.py</code> — Value Iteration agent.</li>
  </ul>

  <p>This modular architecture ensures clarity, reproducibility, and easy experimentation.</p>

  <h2 id="value-iteration">3. Value Iteration in Gridworld</h2>

  <h3>Purpose</h3>
  <p>Demonstrate fast, stable convergence in a deterministic environment.</p>

  <h3>Expected Results</h3>
  <ul>
    <li>Convergence: <strong>1 episode</strong></li>
    <li>Average reward: <strong>+0.59</strong></li>
  </ul>

  <h3>Command</h3>
  <pre><code class="language-bash">python autograder.py -q q4</code></pre>

  <h3>Outcome</h3>
  <p>Autograder passes all tests. Confirms immediate convergence and optimal policy selection.</p>

  <h2 id="qlearning-gridworld">4. Q-Learning in Gridworld</h2>

  <h3>Purpose</h3>
  <p>Evaluate model-free learning in a simple environment.</p>

  <h3>Expected Behavior</h3>
  <ul>
    <li>Initial average reward: <strong>−0.25</strong></li>
    <li>Reward after ~50 episodes: <strong>+0.08</strong></li>
    <li>Slower but steady convergence</li>
  </ul>

  <h3>Commands</h3>
  <pre><code class="language-bash">python gridworld.py -a q -k 50</code></pre>

  <h3>Outcome</h3>
  <p>Early episodes show oscillating rewards; rewards gradually improve and stabilize.</p>

  <h2 id="pacman-small">5. Q-Learning in Pacman (SmallGrid)</h2>

  <h3>Purpose</h3>
  <p>Study learning efficiency in a simple, partially adversarial maze.</p>

  <h3>Expected Behavior</h3>
  <ul>
    <li>Rewards improve from <strong>−510 → −159</strong> over 2000 episodes</li>
    <li>Testing scores consistently exceed <strong>495</strong></li>
    <li>Visual movement becomes efficient and stable</li>
  </ul>

  <h3>Command</h3>
  <pre><code class="language-bash">python pacman.py -p PacmanQAgent -x 2000 -n 2100 -l smallGrid -a epsilon=0.1,alpha=0.5</code></pre>

  <h3>Outcome</h3>
  <p>Pacman learns optimal routes efficiently. Smooth, stable movement demonstrated visually.</p>

  <h2 id="pacman-medium">6. Q-Learning in Pacman (mediumClassic)</h2>

  <h3>Purpose</h3>
  <p>Evaluate learning under complex, stochastic, and adversarial conditions.</p>

  <h3>Expected Behavior</h3>
  <ul>
    <li>Frequent early deaths</li>
    <li>Slow but steady improvement</li>
    <li>Reward progression: <strong>−437 → −385</strong> over 2000 episodes</li>
    <li>Visible improvement in ghost avoidance and pathing</li>
  </ul>

  <h3>Command</h3>
  <pre><code class="language-bash">python pacman.py -p PacmanQAgent -x 2000 -n 2100 -l mediumClassic -a epsilon=0.1,alpha=0.5</code></pre>

  <h3>Outcome</h3>
  <p>Initial random movement, then gradual reduction in ghost collisions and more stable cumulative rewards over time.</p>

  <h2 id="logging">7. Logging Metrics for Analysis</h2>

  <p>The project tracks the following metrics:</p>
  <ul>
    <li>Cumulative reward per episode</li>
    <li>Convergence time</li>
    <li>Episode length</li>
    <li>Success rate (completion of food collection)</li>
  </ul>

  <h3>Command</h3>
  <pre><code class="language-bash">python pacman.py -p QLearningAgent -n 200 | tee pacman_log.txt</code></pre>

  <h3>Outcome</h3>
  <p>Log file contains detailed episode scores and is used for plotting and statistical analysis.</p>

  <h2 id="challenges">8. Challenges and Solutions</h2>

  <table>
    <thead>
      <tr>
        <th>Challenge</th>
        <th>Solution</th>
        <th>Outcome</th>
      </tr>
    </thead>
    <tbody>
      <tr>
        <td>Reward oscillation in Q-Learning</td>
        <td>Tuned α and ε</td>
        <td>Stabilized learning curves</td>
      </tr>
      <tr>
        <td>Slow Value Iteration on larger maps</td>
        <td>Introduced convergence threshold Δ</td>
        <td>Faster computation</td>
      </tr>
      <tr>
        <td>Pacman stochastic behavior</td>
        <td>Averaged multiple runs</td>
        <td>Smoother reward curves</td>
      </tr>
      <tr>
        <td>Agent–environment inconsistencies</td>
        <td>Modularized state/action structures</td>
        <td>Seamless execution</td>
      </tr>
    </tbody>
  </table>

  <h2 id="conclusion">9. Conclusion</h2>

  <ul>
    <li>Value Iteration is the fastest and most stable in deterministic environments like Gridworld.</li>
    <li>Q-Learning adapts well to stochastic and adversarial environments like Pacman.</li>
    <li>Gridworld highlights the strengths of model-based RL.</li>
    <li>Pacman demonstrates the flexibility and robustness of model-free RL.</li>
    <li>All experimental findings align with theoretical expectations in reinforcement learning.</li>
  </ul>

  <p>The project meets all planned objectives. Results are verified through logs, autograder outputs, and visual demonstrations.</p>

</body>
</html>
