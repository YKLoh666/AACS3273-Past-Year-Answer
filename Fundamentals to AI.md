## 📚 Table of Contents

### Chapter 1: Introduction to AI

- **1.1 Approaches to AI**
  - [Acting Humanly](#acting-humanly)
  - [Thinking Humanly](#thinking-humanly)
  - [Thinking Rationally](#thinking-rationally)
  - [Acting Rationally](#acting-rationally)
- **1.2 AI Agents**
  - [Agents](#agents)
  - [Task Environment](#task-environment)

### Chapter 2: Solving Problems by Searching

- **2.1 Fundamentals of Search**
  - [Problem Solving Agents](#problem-solving-agents)
  - [Problem Solving Phases](#problem-solving-phases)
  - [Problem Formulation](#problem-formulation)
  - [Abstraction](#abstraction)
  - [Search Tree](#search-tree)
  - [Nodes](#nodes)
  - [Paths](#paths)
  - [Frontier](#frontier)
- **2.2 Measuring Search Effectiveness**
  - [Performance Measures](#performance-measures)
  - [Measurement of Complexity](#measurement-of-complexity)
- **2.3 Uninformed Search Strategies**
  - [Breadth-First Search (BFS)](#breadth-first-search-bfs)
  - [Best-First Search](#best-first-search)
  - [Depth-First Search (DFS)](#depth-first-search-dfs)
  - [Depth-Limited Search](#depth-limited-search)
  - [Iterative Deepening Search (IDS)](#iterative-deepening-search-ids)
  - [Bidirectional Search](#bidirectional-search)
  - [Backtracking Search](#backtracking-search)
- **2.4 Informed Search Strategies**
  - [Greedy Best-First Search](#greedy-best-first-search)
  - [A\* Search](#a-search)
  - [Optimality](#optimality)

### Chapter 3: Local Search and Optimization Problems

- **3.1 Local Search Basics**
  - [Local Search Strategies](#local-search-strategies)
  - [State Space Landscape](#state-space-landscape)
- **3.2 Optimization Techniques**
  - [Hill Climbing Search](#hill-climbing-search)
  - [Simulated Annealing](#simulated-annealing)
  - [Local Beam Search](#local-beam-search)
  - [Evolutionary Algorithms](#evolutionary-algorithms)

# Chapter 1: Introduction to AI

## Approaches of AI

### Acting Humanly

- Capability to think like a human being.
- **Turing Test**
  - Proposed by Alan Turing in 1950.
  - Imitation Game.
  - Involves a computer, a human respondent, and a human interrogator.
  - Direct physical interaction is avoided.
  - Pass the test if the interrogator cannot distinguish between the computer and the human.
  - 6 capabilities:
    1. Natural language processing (NLP) - communication
    2. Knowledge representation - storing what it perceives
    3. Automated reasoning - drawing conclusions from knowledge
    4. Machine learning - adapting to new circumstances
    5. Computer vision - interpreting visual information
    6. Robotics - manipulating objects

### Thinking Humanly

- Capability to think like a human being.
- **Cognitive Modeling**
  - Ways to understand how humans think.
    - Introspection - self-observation of mental processes.
    - Psychological experiments - controlled experiments to study behavior, observe human in action.
    - Brain imaging - study of brain activity.
  - **Cognitive Science** - interdisciplinary field combining AI computer models and psychological experimental techniques to construct a theory of human thought.

### Thinking Rationally

- Capability to think rationally.
- **Laws of Thought** - rules that guide human thinking rationally.
  - Attempt to codify the rational reasoning process.
  - Initiated the field of **logic**.
    - Syllogism - a form of reasoning in which a conclusion is drawn from two premises.
    - Example:
      1. Premise: All humans are mortal.
      2. Premise: Socrates is a human.
      3. Conclusion: Socrates is mortal.
  - Challenge
    1. Hard to state informal knowledge in logical notations.
    2. Differences between solving problems in principle and solving them in practice. Computer resources can be exhausted before finding a solution.

### Acting Rationally

- Capability to act rationally.
- **Rational Agent** - an agent that acts to achieve the best outcome or the best expected outcome if the outcome is uncertain.

### Comparison

| Comparison of Approaches                                   | Description                                                                                                                                                                                                                           |
| ---------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Acting Rationally vs. Thinking Rationally                  | - Acting rationally is more practical than thinking rationally. <br> - Reflex actions can be more rational than making correct inferences. <br> - Thinking rationally is only one of the many ways to act rationally.                 |
| Acting Rationally vs. (Thinking Humanly or Acting Humanly) | - Standard of rationality is general and can be defined mathematically, easier to implement. <br> - Thinking humanly and acting humanly are more subjective and harder to implement, can be biased by human emotions and experiences. |

- Rational agents is more practical than the other three approaches.

## Agents

- **Agent** - anything that can be viewed as **perceiving** its environment through **sensors** and **acting** upon that environment through **actuators**.
- Interaction between the agent and the environment is called **perception** and **action**.
  - **Perception** - A passive interaction, gaining information from the environment without changing it.
  - **Action** - An active interaction, changing the environment after acting upon it.
- Choice of actions is based on the **built-in knowledge** and percept sequences observed.
- **Agent Function** - a mapping from percept sequences to actions.

  ```

  --------------------------          ---------------
  | Agent                  |          |             |
  |                        | Percepts |             |
  |         Sensors <-----------------|             |
  |            |           |          |             |
  |            v           |          |             |
  |   ------------------   |          |             |
  |   | Agent Function |   |          | Environment |
  |   ------------------   |          |             |
  |            |           |          |             |
  |            v           | Actions  |             |
  |        Actuators ---------------->|             |
  |                        |          |             |
  |                        |          |             |
  |                        |          |             |
  --------------------------          ---------------

  ```

- **Agent Program** - an implementation of the agent function, running on physical system.
- **Consequentialism** - the rightness of an action is determined by its outcomes.
  - Best action is the one that leads to the desired outcome.
  - Performance measure is used to evaluate the success of an agent's action quantitatively.
    - Example: A car's performance measure is time taken to reach the destination, fuel consumption, safety, etc.
    - If the car reaches the destination in the shortest time, it is considered a good agent.
    - Design the performance measure based on the desired outcome in the environment, not the agent's behavior.
- **Rationality**

  - Make the best decision based on the up-to-date percept sequence and prior knowledge about the environment.
  - Depends on 4 factors (PEAS):
    1. **Performance measure** - the criteria for success.
    2. **Environment** - Agent prior knowledge about the environment (agent might not know everything about the environment).
    3. **Actuators** - Actions available to the agent.
    4. **Sensors** - Percept sequences to date.
  - Definition of rational agent:
    - For each possible (4) **percept sequence**, the rational agent should select an (3) **action** that (1) **maximizes performance measure**, based on **evidence** provided by the (4) **percept sequence** and the (2) **prior knowledge about the environment**.
  - Rational Agent should be able to:
    1. **Gather information** - perceive the environment before acting.
    2. **Learning** - compensate for the incomplete or incorrect prior knowledge about the environment. Increase adaptability.
    3. **Autonomy** - act depends on its own percepts and learning experience, not fully relying on the prior knowledge provided by the designer.

- **Rational Agent vs. Omniscient Agent**

  | Rational Agent                                               | Omniscient Agent                                           |
  | ------------------------------------------------------------ | ---------------------------------------------------------- |
  | Does not know actual outcome of actions                      | Knows actual outcome of actions                            |
  | Acts under uncertainty most of the time                      | Acts under certainty all the time                          |
  | Maximizes performance by achieving the best expected outcome | Maximizes performance by achieving the best actual outcome |

## Task Environment

- Represents a problem
- PEAS
  - **Performance measure** - the criteria for success.
  - **Environment** - the environment in which the agent operates.
  - **Actuators** - the actions available to the agent.
  - **Sensors** - the percepts available to the agent.
- Environment Properties

  - **Observability** - whether the agent can **observe the complete state** of the environment at each time step.

    - Fully observable - agent can observe the complete state of the environment at each time step.
    - Partially observable - agent cannot observe the complete state of the environment at each time step. May due to faulty sensor etc.
    - Fully unobservable - agent without any sensors cannot observe the state of the environment at any time step.

    | Description                                                   | Fully Observable | Partially Observable |
    | ------------------------------------------------------------- | ---------------- | -------------------- |
    | **Access to environment state** at each point in time         | Full State       | Partial State        |
    | Detection of **any aspects** relevant to the choice of action | All              | Some                 |
    | Maintain **internal state** to keep track of the environment  | No               | Some                 |
    | Handling **uncertainty** in the environment                   | No               | Yes                  |

  - **Agent Number** - the number of agents in the environment.

    - Single agent - only one agent in the environment.
    - Multi-agent - multiple agents in the environment.
      - Require distinguishing agents from objects.
      - Competitive - gain of one agent is the loss of another agent.
      - Cooperative - agents work together to achieve a common goal. Receive a common reward.
      - Partially both - Example: Soccer game, the players are cooperative, but the teams are competitive.
      - Issues:
        - How to distinguish agents from objects?
        - How to maximize the performance of the agent, given it depends on the actions of other agents?

  - **Determinism** - whether the environment is deterministic or stochastic.

    - Deterministic - the next environment state is completely determined by the current state and the action taken by the agent.
      - In principle, the agent not need to consider uncertainty in a fully observable environment.
      - Every action has single guaranteed effect.
      - Example: Chess, Tic-Tac-Toe, etc.
    - Stochastic - the next environment state is not completely determined by the current state and the action taken by the agent.
      - Example: Taxi driving, Soccer, etc.

  - **Episodic vs. Sequential**

    - Episodic - the agent's experience is divided into **episodes**.
      - Each episode consists of a single action and its outcome.
      - The next episode does not depend on the previous episode.
      - Example: Image recognition, etc.
    - Sequential - the agent's experience is not divided into episodes.
      - The next episode depends on the previous episode.
      - Example: Chess, Tic-Tac-Toe, etc.

  - **Static vs. Dynamic**

    - Static - the environment does not change until the agent takes an action.
      - Example: Chess, Tic-Tac-Toe, etc.
    - Dynamic - the environment changes while the agent is deliberating.
      - Example: Taxi driving, Soccer, etc.
    - Semi-dynamic - the environment does not change while the agent is deliberating, but the performance measure changes.
      - Example: Chess with time limit, etc.

  - **Discrete vs. Continuous**

    - Discrete - the environment has finite number of states, percepts, actions and time points.
      - Example: Chess, Tic-Tac-Toe, etc.
    - Continuous - the environment has infinite number of states, percepts, actions and time points.
      - Example: Taxi driving, Soccer, etc.

  - **Agent State of Knowledge**

    - Known - the agent knows the outcome of its actions.
    - Unknown - the agent needs to learn the outcome of its actions.

## Structure of Agents

- Agent = Architecture + Agent Program

- **Architecture**

  - Makes the percepts from the sensors available to the agent program.
  - Runs the agent program on hardware.
  - Feeds the action chosen by the agent program to the actuators.

- **Table-Driven Agent**

  - A simple agent that uses a table to **map percepts to actions**.
  - Issues:
    - How to store gigantic table in memory?
    - How much time needed to create the table?
    - How to learn from its experience?

- **Agent Program**

  1. **Simple Reflex Agent** - selects actions based on the current percept, ignoring the rest of the percept history.
     - **Condition-Action Rule** - a rule that maps a condition to an action, or if-then rule. Can be write as if-else statement.
       - Example: If the light is red, then stop the car.
     - Easy to implement
     - Issues:
       - Cannot handle partial observability.
       - Vulnerable to infinite loops.
     - Example: Simple reflex agent for a thermostat.
       - If the temperature is above 75 degrees, then turn on the air conditioner.
       - If the temperature is below 65 degrees, then turn on the heater.
       - If the temperature is between 65 and 75 degrees, then do nothing.
  2. **Model-Based Reflex Agent** - maintains an internal state to keep track of the unobservable aspects of the environment.
     - Sensor Model - Knowledge reflects the state of the environment.
     - Transition Model - Knowledge of how world changes, does it depend on the action taken by the agent.
     - Issues:
       - Internal state may not be accurate
       - Make decisions under uncertainty
       - May not know what to do if given more than one action without having a goal that specifies the desired outcome.
     - Example: Model-based reflex agent for a vacuum cleaner.
       - Model: Stores the map of the room and the location of the dirt as it perceives it.
       - Transition Model: Knows how the world changes when it moves to a different location.
       - Based on the internal state, it can decide to move to a different location or clean the current location.
  3. **Goal-Based Agent** - Keeps track of the goal information and uses it to select actions.
     - track world state and sets goals to achieve.
     - Issues:
       - Can only provide binary distinction between achieving and not achieving the goal.
       - Uncertain on which sequence of world state are more desirable.
     - Example: Goal-based agent for a self-driving car.
       - Goal: Reach the destination in the shortest time possible.
       - Actions: Accelerate, brake, turn left, turn right, etc.
       - The agent uses the goal information to select the best action to achieve the goal.
       - The agent can also learn from its experience and update its goal information.
  4. **Utility-Based Agent** - Using utility function to evaluate the desirability of the world state.
     - Maximizes the utility value.
     - Averaging all the possible outcome states weighted by the probability of each outcome.
     - Issues:
       - How to keep track of complex world state?
       - Requires great deal of research on perception, representation, reasoning, and learning.
       - Requires efficient algorithms to compute the utility function.
       - Solution with high computational cost may not be practical.
     - Example: Utility-based agent for a automated stock trading system.
       - Utility function: A function that evaluates the desirability of a stock based on its price, volume, and other factors.
       - The agent uses the utility function to select the best action to maximize its profit.
       - The agent can also learn from its experience and update its utility function.

- **Learning Agent** - an agent that can learn from its experience and improve its performance over time. Has competitive advantage due to its capability to solve in an unknown environment.

  - **Performance Element** - the part of the agent that selects actions based on the current percept and the learned knowledge.
  - **Learning Element** - the part of the agent that learns from its experience.
  - **Critic** - the part of the agent that evaluates the performance of the agent
  - **Problem Generator** - the part of the agent that generates new problems for the learning element to solve.
  - Example: Self-driving Taxi
    - Performance Element - A collection of knowledge and procedures the taxi has for selecting its driving actions.
    - Critic - Observe the world state and the taxi's actions, and evaluate the taxi's performance based on the performance measure.
    - Learning Element - Learn from the taxi's experience and amend the performance element to improve its performance.
    - Problem Generator - Experiment with new actions and learn from the experience, such as trying to drive faster or slower, or taking a different route.

- **Representation** - How to represent the world state

  1. Atomic Representation - Represent the world state as a black box, with no internal structure.
  2. Factored Representation - Represent the world state as a set of attributes-values pairs, with each attribute representing a different aspect of the world state. Can have common attributes for different world states.
  3. Structured Representation - Consists of objects and relations within a world state.

# Chapter 2: Solving Problems by Searching

## Problem Solving Agents

- Goal-based agents
- Find a sequence of actions to achieve the goal.
- Atomic representation of the world state.

## Problem Solving Phases

1. Goal Formulation

- Performance measure
- Limit objectives and actions to achieve the goal.

2. Problem Formulation

- Abstract Model of relevant parts of the environment.
- Consists of:
  - A state
  - An action necessary to reach the goal

3. Solution Searching

- simulate the sequence of actions to reach the goal.
- the sequence called **solution**.
- the solution which has the lowest cost is the **optimal solution**.

4. Solution Execution

- Agent executes all the actions in the solution.

## Problem Formulation

- Define the problem in 6 components:
  1. **States** - the possible configurations of the environment, referred to as **state space**.
  2. **Initial State** - the state agent starts in.
  3. **Goal State** - the state agent wants to reach.
  4. **Actions** - the actions available to the agent in a particular state.
  5. **Transition Model** - the model that describes how the world changes when an action is taken.
  6. **Cost Function** - the cost of each action to reach another state.

## Abstraction

- Valid if any abstract solution can be elaborated into a solution in the more detailed world
- Useful if carrying out each if the action is easier than the original problem
- Simplify the problem representation by removing unnecessary details.
- A good abstraction should:
  - Remove as much detail as possible while preserving validity.
  - Ensure the actions are easy to implement.

## Search Tree

- Consists of nodes (states) and edges (actions).
- The root node is the initial state.
- Frontier (open list): the set of nodes that have been generated but not yet expanded.
- Steps:
  1. Add the initial state to the frontier.
  2. Expand the node at the top of the frontier.
  3. Generate all the child nodes of the expanded node.
  4. Add the child nodes to the frontier.
  5. Repeat steps 2-4 until the goal state is found.
  6. If the goal state is found, return the path from the root node to the goal node.
- Explored Set (closed list): the set of nodes that have been expanded.

| Search Tree                                             | State Space                                                                                       |
| ------------------------------------------------------- | ------------------------------------------------------------------------------------------------- |
| Describes path from the initial state to the goal state | Describes set of states in the world, and allowed actions to transition from one state to another |
| Multiple node can correspond to the same state          | Each state is uniquely represented                                                                |

## Nodes

- **Node** - a data structure that represents a state in the search tree.
- Contains:
  - **State** - the state represented by the node.
  - **Parent** - the parent node of the current node.
  - **Action** - the action taken to reach the current node from the parent node.
  - **Path Cost** - the cost of the path from the root node to the current node.

## Frontier

- Data structure that stores the nodes that have been generated but not yet expanded.
- Operations:
  - **IS_EMPTY()** - check if the frontier is empty.
  - **ADD(node)** - add a node to the frontier.
  - **POP()** - remove a node from the frontier.
- Types:
  - Stack - Last In First Out (LIFO) data structure.
    - Depth-First Search (DFS) - expands the deepest node in the search tree first.
  - Queue - First In First Out (FIFO) data structure.
    - Breadth-First Search (BFS) - expands the shallowest node in the search tree first.
  - Priority Queue - a data structure that pops the node with minimum cost according to evaluation function, _f_
    - Uniform Cost Search (UCS) - expands the node with the lowest path cost, _g(n)_.
    - Greedy Best-First Search - expands the node with the lowest heuristic cost, _h(n)_.
      - Does not guarantee optimal solution.
      - _h(n)_ - estimated cost from the current node to the goal node.
    - A\* Search - expands the node with the lowest evaluation function, _f(n) = g(n) + h(n)_.
      - _g(n)_ - path cost from the root node to the current node.
      - _h(n)_ - estimated cost from the current node to the goal node.
      - _f(n)_ - total estimated cost of the cheapest solution through the current node.

## Paths

- **Path** - a sequence of nodes from the root node to a leaf node.
- Redundant paths - paths that lead to the same state.
  - Solution: Use a **closed list** to keep track of the nodes that have been expanded.
  - Loopy paths - paths that lead to the same state multiple times. A special case of redundant paths.

## Performance Measures

- **Completeness** - the algorithm is guaranteed to find a solution if one exists.
  - Must be systematic, meaning it must explore all the nodes in the state space.
- **Optimality** - the algorithm is guaranteed to find the optimal solution if one exists.
  - Must ensure that the path cost is minimized.
- **Time Complexity** - the amount of time taken by the algorithm to find a solution.
- **Space Complexity** - the amount of memory used by the algorithm to find a solution.

## Measurement of Complexity

- Measure in terms of
  - `b`, the branching factor, i.e., the maximum successor nodes for any node.
  - `d`, the depth of the shallowest solution.
  - `m`, the maximum depth of the search tree.
- **Big-O Notation** - a mathematical notation that describes the worst-case efficiency of an algorithm.
  - Example: O(1), O(log n), O(n), O(n log n), O(n^2), O(2^n), O(n!), etc.

## Uninformed Search Strategies

- **Uninformed Search** - blind search, solely relies on the information provided by the problem formulation.
  - Can only differentiate between goal and non-goal states.
  - Cannot differentiate among non-goal states.

## Breadth-First Search (BFS)

- Expands all the nodes at the current depth before moving on to the next depth level.
- Uses a FIFO queue to store the nodes in the frontier.
- Goal Test
  | Early Goal Test | Late Goal Test |
  | ------------------ | --------------- |
  | Goal test is performed when the node is generated | Goal test is performed when the node is expanded |
  | Can stop the search early | Ensures only test the best node in the frontier (optimal solution) |
  | May miss the optimal solution | May expand more nodes than necessary |
  | Useful for unoptimal solutions | Useful for optimal solutions |
- Performance Evaluation
  - Completeness: Yes, if `b` is finite.
  - Optimality: Yes, if all path costs are equal.
  - Time Complexity: 1 + b + b<sup>2</sup> + ... + b<sup>d</sup> = O(b<sup>d</sup>)
    - In complexity calculation, the sum is approximated to the largest term.
  - Space Complexity: O(b<sup>d</sup>)
    - number of nodes stored in the frontier and the explored set.

## Depth-First Search (DFS)

- Expands the deepest node in the search tree first.
- Uses a LIFO stack to store the nodes in the frontier.
- Performance Evaluation
  - Completeness: Yes, if `b` is finite and check for repeated states.
  - Optimality: No, the solution may be at a shallower depth than the current node but is in a different branch.
  - Time Complexity: 1 + b + b<sup>2</sup> + ... + b<sup>m</sup> = O(b<sup>m</sup>)
    - In complexity calculation, the sum is approximated to the largest term.
  - Time Complexity: 1 + b + b<sup>2</sup> + ... + b<sup>m</sup> = O(b<sup>m</sup>)
  - Space Complexity: O(bm)
    - number of nodes stored in the frontier => O(b<sup>m</sup>)
    - number of nodes stored in the explored set => O(m)

## Best-First Search

- Or Uniform Cost Search (UCS)
- Expands the node with the lowest path cost, _g(n)_.
- Uses a priority queue to store the nodes in the frontier.
- Performance Evaluation
  - Completeness: Complete if `b` is finite and every action has a cost greater than a positive constant (ε).
    - ε represents the minimum cost of an action.
  - Optimality: Guarantees the optimal solution provided all step costs are strictly positive.
  - Time Complexity: O(b<sup>1 + ⌊C\*/ε⌋</sup>), where C\* is the cost of the optimal solution.
    - 1 + ⌊C\*/ε⌋ refers to the number of nodes expanded in the search tree.
    - It is derived from the fact that the number of nodes expanded is proportional to the cost of the optimal solution divided by the minimum cost of an action.
  - Space Complexity: O(b<sup>1 + ⌊C\*/ε⌋</sup>)

## Backtracking Search

- A variant of DFS which implements with function recursion.
- Only the nodes in the current path are stored in the stack.
- Each node knows which child node to expand next.
- Space complexity is O(m), where m is the maximum depth of the search tree.

## Depth-Limited Search

- Imposing a limit (`l`) on the depth of the search tree.
- If the goal state is not found within the limit, the search fails.
- Returns cut-off value if the goal state is not found within the limit.
- Performance Evaluation
  - Completeness: No, if `l` < `d`
  - Optimality: No, if `d` < `l`
  - Time Complexity: O(b<sup>l</sup>)
  - Space Complexity: O(bl)

## Iterative Deepening Search (IDS)

- Uses a combination of DFS and BFS.
- Performs a series of depth-limited searches with increasing depth limits until the goal state is found.
- Can find the **diameter** of the state space
- Returns failure if the goal state is not found within the limit.
- Performance Evaluation
  - Completeness: Yes, if `b` is finite and has acyclic state space, otherwise requires closed list to check for cycles.
  - Optimality: Yes, if all path costs are equal.
  - Time Complexity: O(b<sup>d</sup>) with solution, O(b<sup>m</sup>) without solution.
    - (d)b + (d-1)b<sup>2</sup> + ... + (1)b<sup>d</sup>
  - Space Complexity: O(bd) with solution, O(bm) without solution.

## Bidirectional Search

- Search from both the initial state and the goal state simultaneously.
- The search stops when the two searches meet in the middle.
- Performance Evaluation
  - Completeness: Depends on the search strategy used. (BFS, DFS, etc.)
  - Optimality: Depends on the search strategy used. (BFS, DFS, etc.)
  - Time Complexity: O(b<sup>d/2</sup>)
    - 2 x (b<sup>d/2</sup>), constant is ignored.
  - Space Complexity: O(b<sup>d/2</sup>)

## Informed Search Strategies

- **Informed Search** - heuristic search, uses additional information to guide the search process.
- Able to estimate how close the current state is to the goal state.
- Using Evaluation Function, _f(n)_
- Use priority queue to store the nodes in the frontier.
- Pops the node with the lowest _f(n)_ value.

## Greedy Best-First Search

- _f(n) = h(n)_
- Similar to UCS which uses _g(n)_ as the evaluation function.
- Performance Evaluation
  - Completeness: No if tree search, Yes if graph search.
  - Optimality: No, does not guarantee the optimal solution.
  - Time Complexity: O(b<sup>m</sup>), but can be improved to O(bm) with a good heuristic.
  - Space Complexity: O(bm) for tree search, O(b<sup>m</sup>) for graph search.

## A\* Search

- _f(n) = g(n) + h(n)_
- Uses both the path cost and the heuristic cost to guide the search process.
- Performance Evaluation
  - Completeness: Yes, if `b` is finite and cost of each action is greater than a positive constant (ε).
  - Optimality: Yes, if the heuristic function is admissible and consistent.
  - Time Complexity: O(b<sup>d</sup>)
  - Space Complexity: O(b<sup>d</sup>)

## Optimality

- **Admissible Heuristic** - a heuristic function that never overestimates the cost to reach the goal.
- **Consistent Heuristic** - a heuristic function that satisfies the triangle inequality, i.e. two sides of a triangle are always greater than the third side.

  - _h(n) ≤ c(n, a, n') + h(n')_
  - c(n, a, n') - cost of action _a_ from state _n_ to state _n'_.

  ```
                   n
                  /|
                 / |
        h(n)    /  | c(n, a, n')
               /   |
              /    v
             <------
        goal  h(n') n'
  ```

# Chapter 3: Local Search and Optimization Problems

- Optimization problems - finding the best solution from a set of feasible solutions.
- Objective function - a function that evaluates the quality of a solution.
- Cost function - a function that evaluates the cost of a solution.
- Candidate solution - a set of solutions that are being considered for optimization.

## Local Search Strategies

- Searching from the start state to neighboring states.
- Decision is made based on the current state and its neighbors.
- Path and visited nodes are not stored in the memory.
- Not systematic
- Advantages:
  - Low memory requirement.
  - Can be used for large search spaces.

## State Space Landscape

- Graphical representation of the state space.
- Components:
  - **X-axis** - the state space.
  - **Elevation** - corresponds to the value to optimize.
    - Objective function: find global maximum, hill climbing.
    - Cost function: find global minimum, gradient descent.
  - **State** - a point in the state space.
  - **Global Maximum/Minimum** - the best solution in the state space. Has the highest objective function value (global maximum) or the lowest cost function value (global minimum).
  - **Local Maximum/Minimum** - a solution that is better than its neighbors but not the best solution in the state space.
  - **Flat Local Maximum/Minimum** - Neighboring states have the same objective function value. A plateau.
  - **Shoulder** - A plateau whose edge is stretched out in one direction.

## Hill Climbing Search

- Start from the initial state
- Move to immediate neighbor with the highest objective function value (or lowest cost function value).
- Terminate when no neighbor has a higher objective function value (or lower cost function value).
- Pros
  - Only need to keep track of the current state and its neighbors.
  - Acceptable performance in practice.
  - Low memory requirement and computation time.
- Cons
  - Suboptimal solution.
  - Stuck in local maximum/minimum.
  - Stuck in plateau.
  - Stuck in ridge.
- Solutions:
  - Allow a limited number of sideway moves to escape plateau.
  - Backtrack to the previous state and try a different neighbor.
  - Stochastic hill climbing - randomly select a neighbor to move to, which each uphill move's probability vary by steepness.
  - First-choice hill climbing - explore the neighbors randomly until a neighbor with a higher objective function value than the current state is found. (The first better neighbor)
  - Random-restart hill climbing - restart the search from a random state if the current state is stuck in local maximum/minimum.
- Completeness
  - No, can get stuck in local maximum/minimum.
  - If using complete variant, can be extremely inefficient.

## Simulated Annealing

- A probabilistic search algorithm that uses randomization to escape local maximum/minimum.
- Inspired by the annealing process in metallurgy, where metal is heated and then cooled to remove defects and improve strength.
- Uses a temperature parameter to control the probability of accepting a worse solution.
- Similar to stochastic hill climbing, but allows for downhill moves based on the temperature parameter.

## Local Beam Search

- A variant of hill climbing that keeps track of multiple states (k states) instead of just one.
- Each state is called a **beam**.
- k, or beam width, is the number of states to keep track of.
- Selects the k best neighbors from all the beams to form the next beam.
- To overcome lack of diversity, stochastic beam search is used. (randomly select k neighbors from all the beams).
- Pros:
  - Can quickly abandon unfruitful paths.
  - Utilizes parallelism.

## Evolutionary Algorithms

- Inspired by the process of natural selection and evolution.
- Uses a population of candidate solutions (individuals) to search for the optimal solution.
- A variant of stochastic beam search.
- Steps: (Using 8-Queen problem as an example)
  1. **Initialization** - Generate a random population of candidate solutions (individuals).
     - Each individual represents a possible solution to the problem.
  2. **Evaluation** - Evaluate the fitness of each individual in the population.
     - Fitness function - a function that evaluates the quality of a solution.
     - Example: In the 8-Queen problem, the fitness function can be the number of pairs of queens that are not attacking each other. The best solution has a fitness of 8C2 = 28.
     - Normalise the score to probability.
  3. **Selection** - Select individuals from the population to create a new generation.
     - Select individuals randomly based on probability.
     - Choose random crossovers from the population.
  4. **Crossover** - Combine two individuals to create a new individual.
     - Example: In the 8-Queen problem, two individuals can be combined by taking the first half of one individual and the second half of the other individual.
     - Crossover point is randomly selected.
     - Convergence: The process of individuals becoming more similar over generations.
     - Can be single-point, multi-point crossover, or uniform crossover (randomly select genes from both parents).
  5. **Mutation**
     - Randomly change an individual to create a new individual.
     - Example: In the 8-Queen problem, a mutation can be swapping two queens in the same row or column.
     - Mutation rate is the probability of mutation occurring.
- **Termination** - The algorithm terminates when a stopping criterion is met.
  - When there is no improvement in the population for a certain number of generations.
  - When predefined number of generations is reached.
  - When the fitness of the best individual reaches a certain threshold.
- Pros:
  - Has uphill tendency.
  - Random exploration of the search space.
  - Exchange of information among parallel search processes.
