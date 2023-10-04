# Classical Search

## Uninformed Search

These strategies have no additional information about states beyond that
provided in the problem definition, so they can only proceed by generating
successors until they find a goal state.

### Types of Uniform Search

- **Breadth-first Search (BFS)** is a search strategy that expands the
  shallowest unexpanded node first. BFS expands the root node, then explores all
  the children of the root node, and so on. It is gauranteed to find the
  shortest past.
- **Depth-first Search (DFS)** applies a similar search strategy as BFS but
  expands the deepest node in the current frontier of the search tree. DFS
  expands the first child of the root node and explores farther to the deepest
  leaf node. DFS will expand all the way down one route first to look for a
  goal. If it cannot find the goal down that path, it turns around to go back to
  the next-furthest node and searches along that route. It does find the goal
  down that route, no matter how far, it will terminate.
- **Uniform Cost Search (UCS)** is a search strategy that expands the successor
  node with the cheapest cost. It's also called **Cheapest-First Search**. In a
  route finding problem, the cheapest cost could be defined as the shortest
  distance (in miles) between two cities. The reason it is gauranteed to find
  the cheapest path to the goal is because you do not add the goal the first
  time you reach it on a given path. Instead you wait until all other cheaper
  paths have been explored, at which point the goal state would be the next to
  expand. You don't need to actually expand it, but that tells you that the
  algorithm is complete and has found the cheapest path. Awesome!

### Terminology:

- **Optimal Search**: an optimal search is one that is **gauranteed** to find
  the shortest or cheapest path to the goal.
- **Complete Search**: a complete search is gauranteed to find a goal. Depth
first search is not gauranteed since if one of the paths is keeps going deeper
and deeper (indefinitely) it will never find the goal when it exists in a
different branch of the tree.
- **Tree vs Graph Search**: A tree search is a formal description of the available
states and actions in the problem in the forms of nodes (states) and edges
(actions). The graph search is different from the tree search in which graph
search prevents redundancy by going back to the explored states.

## Informed Search

These strategies have additional information about search states, so they can
guide the search by ranking successors according to some fitness score until
they find a goal state.

### Types

- **Greedy best-first search**:  expands outward toward locations estimated as
  closer to the goal. If a direct path is available, expends much less effort
  than Uniform Cost; however, it does not consider any routes in which it may
  need to temporarily take a further away path (say, due to a contraint near the
  goal) in order to arrive at an overall shorter path. This is different from
  **Uniform Cost search**, which is uninformed and expands out equally in all
  directions, may expend additional effort getting to a fairly direct path to
  the goal. 
- **A$^*$ Search** - utilizes both of Uniform and greedy search to optimize with
  both the shortest path and the goal in mind.

  #### A* Search

  Find the shortest length path while keeping while expanding the minimum number
  of paths possible. The algorithm always chooses to expand the cheapest
  *estimated* (full path) first.

  It tries to minimize:

  $f = g + h$

  where:

  $g$ = Known path cost (so far) to the current state/path. This helps keep the
  path short

  $h$ = Estimated distance to the goal from current state/path. This helps keep
  us focused on the goal (for efficiency)

  A* will find the lowest cost path only if:

  $h(s) <$ true cost

  In other words, $h$ should never overestimate the remaining path to the goal.

      h should never overestimate
      h is optimistic
      h is admissible
  
  Question: he says that A* is gauranteed to find the cheapest path is h is
  always less than the true cost because when you get to the goal, $h=0$ (since
  you know the true cost of the path)). All the other paths would have had
  higher costs, he says, but doesn't this assume that $h$ is equally and
  consistently optimistic **to the same degree** for every path in the tree? How
  can that be true? 
  
#### Heuristics

When creating heuristics we want them to be as accurate to the actual cost
remaining, but never to overestimate the cost. If they are always less than the
cost then they are said to be admissable. Given two admissable heuristics, we
would always choose the one that predicts the greater cost, since it would be
the closest guess without going over (the Price is Right!).

One way to create a heuristic is to consider the "relaxed" problem where one
relaxes some of the constraints on how you can move around the tree, usually
introducing more choices. The exact cost of a solution to this easier problem
then becomes the heuristic for the original problem.

#### Paths defined as Nodes

When creating an algorithm, we define a path as a data model containing certain
information. For example:

Path = $A \rightarrow S \rightarrow F$

Node Object has attributes:
- *end_state* = F (State at end of path)
- *action* = SF (Action it took to get there)
- *cost* = 234 (Total cost)
- *parent* = S (pointer to the parent node)

The Path is an abstract idea, whereas the node is the representaiton in the
numerical algorithm (and in memory).

## Problems with Search

The search we are talking about here works given the following conditions:
1. **Fully Observable**: Must be able to see what initial state we start out with
2. **Known**: Must know the set of available actions to us
3. **Discrete**: Must be a finite number of actions to choose from
4. **Deterministic**: Must know the resul tof taking an action
5. **Sattic**: Must be nothing else that can change the world other than our own action

## Suggested Readings
- Dijkstra's algorithm vs UCS
http://www.ise.bgu.ac.il/faculty/felner/papers/2011/socs/dikstra.pdf
- Variants of A*: http://theory.stanford.edu/~amitp/GameProgramming/Variations.html
- Jump Point Search (can be 100x faster than A*): 
https://en.wikipedia.org/wiki/Jump_point_search

# Propositional Logic

(E v B) > A: If E OR B is true it implies A is true

A > (J ^ M): A implies that J AND M are true

J <> M: J is true if and only if M is true

J<>-|M: J is true if annd only if M is NOT true

## Definitions
**valid sentence**: one that is `true in every possible model` for every combination of values of he propositional symbols

**satisfiable sentence**: one that `true in some model` and not necessarily in all the models

**unsatisfiable sentence**: one that `cannot be true in every possible model`

## Limitations of Propsition Logic

Propositional logic has a few limitations as follows

- It can only handle boolean value (ie. true or false) and does not have a capability to handle complex values, such as uncertainty (probability value).
- It can't include objects that have properties, such as size, weight, color, nor shows the relationship between objects.
- There are no shortcuts to succinctly talk about a lot of different things happening.

## First Order Logic

First Order Logic (FOL) is built around two elements:

- **objects**: are the noun phrases that refer to things, such as a house, a
  person, an event.
- **relations**: are the verb phrases among the objects. The relations can be a
  property, such as "the car is red", or a function, which maps the input to an
  output, such as "times two".

FOL expresses the facts about some or all of the objects in the world. It
represents the general laws or rules. For example, in this sentence of "Peter
Norvig wrote the best Artificial Intelligence textbook", the objects are "Peter
Norvig" and "textbook", the property are "the best" and "Artificial
Intelligence", and the relation is "wrote".

FOL may remind you of the Object-Oriented Programming (OOP). Similar to FOL, OOP
is a programming paradigm around objects, rather than functions or logics. Both
FOL and OOP objects can have properties and functions (or methods). FOL,
however, is different from OOP, in which FOL has a declarative nature that
separates the knowledge of the world and their inferences. The other difference
is that OOP lacks the expressiveness required to handle partial information,
such as `if x is in loc A, then it is not in loc B.`

The model in First Order Logic can process more complex representations than
that in Propositional Logic.

In the Propositional Logic, a model is a set of objects with boolean values,
such as `pl_model = { P: true, Q: false, ... }.` Whereas, in the First Order
Logic, a model is a set of tuples and can consist of the properties or
functional relationship of the objects, such as `fol_model = {
Write(Author(Peter), Book(AI textbook)) }`.


### Logical Connectives for FOL:

- ¬	= NOT
- ∧	= AND
- ∨	= OR
- ⇒	= IMPLY
- ⇔	= IF AND ONLY IF

However, FOL can also express the property of a `collection of objects`, known as
quantifiers. There are two standard quantifiers:

- Universal quantification (∀): we can interpret universal quantification as `For
all x`, .... For example, ∀x Bird(x) ⇒ Animal(x) means "all birds are animal."
- Existential quantification (∃): we can interpret existential quantification as
For some x, .... For example, ∃x Car(x) ∧ Color(x,red) means "there exists some
cars with red color". Notes:

⇒ is a natural connective with ∀ quantification, and

∧ is a natural connective with ∃ quantification.

Note: High order logic is one in which the relations are transitive and could be based on objects, whereas FOL is simpler. The relations are based on the logical connectiives of FOL.

### Recap: Problem Solving vs Planning

A problem-solving AI agent does not store knowledge about the world. The agent relies on the algorithms, such as Constraint Satisfaction Problem and Search, to find the solutions in state space. A knowledge-based AI agent, however, has full or partial knowledge about the world and can make inferences from the knowledge.

For a knowledge-based AI agent to be able to reason and plan, they must apply logic to the knowledge about the world. The simplest form of logic is Propositional Logic. Propositional logic is the simplest language consisting of symbols and logical connectives. But it can only handle boolean propositions, which are True, False or Unknown.

We moved on to learn First Order Logic, which can help the knowledge-based agents to learn about the knowledge of the world through the more powerful knowledge representations. FOL is built around objects and relations. It also has universal and existential quantifiers to construct assertions about all or some of the possible values of the quantified variables.

# Introduction to Planning

Challenges in real world planning:

Uncertain environments *Stochastic: the outcomes resulted from a sequence of
actions cannot be determined with certainty. *Multiagent: the outcomes and
actions taken by an agent will be impacted by other agents in the environment.
*Partially Observable: the agent will rely on its own belief state, rather than
the actual states of the world.

Agent's own internal knowledge *Unknown: the agent does not have prior knowledge
about certain states. *Hierarchical: the actions and outcomes do not necessarily
follow a linear process.

Note: you may hear the terms “non-deterministic” and “stochastic” to be used
interchangeably. Both terms describe the uncertainty in the environment, as
opposed to the deterministic nature. There is a subtle difference between these
two terms. Stochastic refers to the randomness and can be quantified in
probabilities. On the other hand, non-deterministic exhibits different outcomes
on different runs with the same set of input.

## Belief State

In “informed search”, the vacuum cleaner operates in a fully observable and
deterministic environment. Under these conditions, the vacuum cleaner knows
where it is and whether there is dirt in all locations (fully observable). Also,
the actions taken by the vacuum cleaner will result in certain states
(deterministic). In order to achieve its goal under this environment, the vacuum
cleaner can search the state space.

In this lesson, our planning agent will take on a more challenging environment,
where it is only partially observable and nondeterministic. Under this
challenging environment, we will introduce the concepts of belief state (a set
of possible worlds). The belief state represents the agent’s current belief (not
actual state) about the possible states it might be in after taking an action
(or a sequence of actions) up to that point.

The vacuum/dirt example is sensorless if you do not know whether you are in the
Left or Right space and you do not know if it is clean or dirty (except for
initial state).

The sensorless vacuum cleaner's belief state space consists of:

- Nodes: the initial state and all possible new states after the agent takes an
  action.
- Edges: all possible actions for the agent to learn about its environment. In
  the sensorless vacuum cleaner example, the possible actions are move-left (L),
  move-right (R), or suck (S).

A `Partially Observable Space` is one in which you might be able to know locally
what is happening around you, for example the vacuum does know if the space is
dirty/clean AND it knows what space it is in (Left or Right). It can then act
(make a move) and then observe. After each observation we can learn more about
the space.  The belief state will either stay the same size, or it will shrink
in size due to the knowledge gained (or not gained) by the observation.
Performing the observation will not hurt our understanding.

In a `Stochastic Partially Observable Space` the belief space is larger due to
multiple possibilities. In this situation, actions tend to increase uncertainty
(multiple possible results) and the observations tend to bring the uncertainty
back down.

In a stochastic environment, the vacuum cleaner may get stuck in infinite loops
as shown in the figure above. As the vacuum cleaner moves to the right (R
action), it may still end up in the same location (A state) or in a new location
(B state).

At the checkpoint after taking the action to move to the right, the vacuum
cleaner has a plan as follows: (i) suck if the vacuum cleaner observes it is in
location of B, or (ii) move right and suck if it is still in location of A. This
plan can be written as [S, while A: R,S].

This plan can reach the final state as long as it is still possible for the
vacuum cleaner to move to the right despite low probability. However, we will
not know how long it will take for the plan to reach the final state.

### Predictor and Update steps

In a deterministic environment, we can observe the new state directly from the
result of taking an action in the current state. We can write this condition as
a mathematical notation: `s’ = Results(s, a)`, where s in the current state, a is
an action, and `s’` is the new state.

However, in a stochastic and partially-observable environment, we can only rely
on the belief state, rather than the state space of the world. We apply two-step
process iteratively to find the goal or solution in the planning tree as
follows:

1. `Predict(b, a)`, where b is the current belief state and a is the action, and
2. `Update(Predict(b, a), o)`, where o is the observation from taking an action
above.

In the next section, we will deep dive into a `planning graph` that utilizes this
predict and update cycle. A planning graph is a special data structure that
gives *better heuristic estimates* from the initial planning state to the goal
states. It is a directed graph organized by alternate layers, between `states` and
`actions` layers, with `preconditions` and `effects` of each action.


## Classical Planning State Space Representation
A complete assignment is state space where every variable is assigned and a
solution is consistent. A partial assignment is state space that assigns values
to only some of the variables.

A complete assignment is possible in a deterministic and fully observable
environment, such as those in the search problems. However, most environments
are stochastic and partially deterministic. Therefore, we use belief state
space, which can be complete or partial assignments.

## Classical Planning Actions Representation
A planning agent relies on the action schemas to know what actions are possible
in the current state. An action schema consists of the action name, a list of
state variables in current space, the preconditions to create this action schema
possible, and the effects after this action is completed. An example of an
action schema is as follows:

    Action (Fly (p, from , to ),  
    	PRECOND:At(p, from) ∧ Plane(p) ∧ Airport(from) ∧ Airport(to) 
    	EFFECT:¬At(p, from) ∧ At(p, to))
    Schema: Action()
    Action name: Fly

- A list of state variables: plane (p), the airport it flies from (from), and the
airport it's flying to (to) 
- Preconditions: there is a plane ("Plane(p )") and
two airports ("Airport(from)") and "Airport(to)"), the current location of the
plane("At(p, from)") 
- Effects: the plane is no longer at previous location
("¬At(p, from)") and plane's new location("At(p, to)")

## Planning Domain Definition Language (PDDL)

The writings of planning domains and problems are commonly standardized in a Planning Domain Definition Language (PDDL). A complete PDDL consists of an initialization of the planning domains, the goal of the planning problem, and a set of action schemas.

An example of a PDDL is as follows:

    Init(At(C1, SFO) ∧ At(C2, JFK) ∧ At(P1, SFO) ∧ At(P2, JFK) 
    ∧ Cargo(C1) ∧ Cargo(C2) ∧ Plane(P1) ∧ Plane(P2)  
    ∧ Airport(JFK) ∧ Airport(SFO))
    
    Goal(At(C1, JFK) ∧ At(C2, SFO)) 
    
    Action(Load(c, p, a),
    	PRECOND: At(c, a) ∧ At(p, a) ∧ Cargo(c) ∧ Plane(p) ∧ Airport(a)
    	EFFECT: ¬At(c, a) ∧ In(c, p)) 
    
    Action(Unload(c, p, a),
    	PRECOND: In(c, p) ∧ At(p, a) ∧ Cargo(c) ∧ Plane(p) ∧ Airport(a)
    	EFFECT: At(c, a) ∧ ¬In(c, p)) 
    
    Action(Fly(p, from, to),
    	PRECOND: At(p, from) ∧ Plane(p) ∧ Airport(from) ∧ Airport(to) 	
    	EFFECT: ¬At(p, from) ∧ At(p, to))


## Progression Search

There are two approaches to find possible solutions in the planning problem state space. They are

- Progression Search: a forward search from the initial state to the goal state.
- Regression Search: a reverse search from the goal state back to the initial
state. 

In a tree search, we stack the nodes from top to bottom (the initial state is
set as the root node). In the planning graph, it is common to line up the
initial state to the goal state from left to right. In the progression search,
we start from the initial node on the left and expand the nodes to the right
until we find the possible solutions by reaching the goal states.

While the progression search is commonly used, there are two limitations with
this approach:

1. The graph may explore unnecessary actions. For example, the graph may explore
   a state where a plane with an empty cargo flies from one airport to another.
2. The graph may require large storage as the number of nodes expands
exponentially with the number of variables. 

Next video, we will learn how the regression search only considers the relevant
action schemas from the goal state.

## Regression Search

The regression search is also known as the **relevant-state search**. As we have seen
in the previous lesson, a complete PDDL includes the action schemas along with
the preconditions and effects associated with certain actions. By working
backward from the goal state, the regression search will expand only the
relevant nodes according to the action schemas. Therefore, the branching factor
for the regression search is smaller than the progression search. However, the
regression search has a limitation because we cannot apply heuristics to speed
up the search back to the initial state.

Basically, you take each Goal assertion and you branch backwards from there. To
branch backwards from there, you know that the given goal state must be the
"effect" of the previous state's "action", but you also have to make sure that
it doesn't negate one of the other goals. For example Effect `At(C1,JFK)` would
require the Unload action: `Action(Unload(C1,p,a))`, but you don't yet know
anything about the plane `p` or the airport `a`.

Regression searches have the disadvantage of not allowing for the definition of
heuristic estimation.

# Partial-order Planning
Any planning algorithm that can place two actions into a plan without specifying
which comes first is called a partial-order planner. The partial-order solution
corresponds to all the possible solutions of total-order plans; each of these is
called a linearization of the partial-order plan.



## Planning Graph

In the following project, you will implement a **planning graph**, which is a
special data structure that is optimized to search for the solutions for a PDDL.

A planning graph is a directed graph organized into levels: the first level S0
is the initial state, consisting of nodes representing each fluent; then the
first level A0 consisting of nodes for each possible action from the states in
S0; followed by the alternating levels of Si and Ai until we reach a termination
condition. A planning graph terminates when two consecutive levels are
identical. At this point, we say that the graph has **leveled off**.

A planning graph is more efficient than progression and regression searches
because the **graphplan** algorithm can eliminate conflicting actions within an
action layer. The conflicting actions can be prevented by the **mutual exclusion
(mutex)** relationships. When the algorithm decides to not taking any action, it
is called taking a persistence action, also known as **no-op**.

There are three possible mutex conditions holds between two actions:

- **Inconsistent effects**: one action negates an effect of the other. For example,
  Load(Cargo) and the persistence of Unload(Cargo) have inconsistent effects
  because they disagree on the effect Unload(Cargo).
- **Interference**: one of the effects of one action is the negation of a
  precondition of the other. For example Fly(p, a, b) interferes with the
  persistence of At(p, a) by negating its precondition.
- **Competing needs**: one of the preconditions of one action is mutually
exclusive with a precondition of the other. For example, Fly(p, a, b) and Fly(p,
a, c) are mutex because they compete on the value of the At(p, a) precondition.

The planning graph is a robust data structure to solve a planning problem. If a
solution is not found by the end of the planning graph layer, the problem is
considered unsolvable.

The planning graph can also provide a **heuristic estimation**, which calculates the
cost to reach the goal states. The cost is known as the **level cost** based on the
number of layers that the algorithm needs to go through to find the solutions.
For example, let’s say we have a planning graph with the following alternating
layers: S0, A0, S1, A1, S2, A2, S3, A3. If the algorithm finds the conjunction
goals at S2 and S3, we can say the cost or level-sum heuristic estimation is 5
(=2 + 3).

## Components of a Plan

1. **Actions**: A set of actions that make up the steps of the plan. These are
taken from the set of actions in the planning problem. The “empty” plan contains
just the Start and Finish actions. Start has no preconditions and has as its
effect all the literals in the initial state of the planning problem. Finish has
no effects and has as its preconditions the goal literals of the planning
problem.

2. **Ordering Constraints:** A set of ordering constraints. Each ordering
constraint is of the form A ≺ B, which is read as “A before B” and means that
action A must be executed sometime before ac- tion B, but not necessarily
immediately before. The ordering constraints must describe a proper partial
order. Any cycle—such as A ≺ B and B ≺ A—represents a contradic- tion, so an
ordering constraint cannot be added to the plan if it creates a cycle.

3. **Causal Links (and Conflicts):** A set of causal links. A causal link
between two actions A and B in the plan is written as A → p B and is read as *A
achieves p for B*. For example, the causal link RightSockOn RightSock →
RightShoe asserts that RightSockOn is an effect of the RightSock action and a
precondition of RightShoe. It also asserts that RightSockOn must remain true
from the time of ac- tion RightSock to the time of action RightShoe. In other
words, the plan may not be extended by adding a new action C that conflicts with
the causal link. An action C conflicts with A → p B if C has the effect ¬p and
if Ccould (according to the ordering constraints) come after A and before B.
Some authors call causal links protection intervals, because the link A → p B
protects p from being negated over the interval from A to B.

4. **Open Preconditions:** A set of open preconditions. A precondition is open
   if it is not achieved by some action in the plan. Planners will work to
   reduce the set of open preconditions to the empty set, without introducing a
   contradiction.


## Planning Graphs for Heuristic Estimation

A planning graph, once constructed, is a rich source of information about the
problem. For example, a literal that does not appear in the final level of the
graph cannot be achieved by any plan. This observation can be used in backward
search as follows: any state containing an unachievable literal has a cost h(n)
= ∞. Similarly, in partial-order planning, any plan with an unachievable open
condition has h(n) = ∞.

**Level Cost Heuristic:** 

The cost of each Literal (multiple literals per state) is simply the how many steps it would take to get to the goal state. If you're only one action away from achieving your goal, then your level cost is 1. It does not account for how many possible actions there are, but only how many steps you are away from the goal.

The level cost is a helper function used by MaxLevel and LevelSum. The level
cost of a goal is equal to the level number of the first literal layer in the
planning graph where the goal literal appears.

**Serial Planning Graph:**

A serial graph insists that only one action can actually occur at any given time
step; this is done by adding mutex links between every pair of actions except
persistence actions. Level costs extracted from serial graphs are often quite
reasonable estimates of actual costs.

### Estimating the cost of a conjunction (multiple simultaneous) of goals

**Max-Level Heuristic:** Calculates the cost to reach each goal and takes the maximum as the cost for the given level. Admissable, but not bery accurate.

**Level-Sum Heuristic:** Returns the sum of the level-costs of the goals. This
is inadmissable (since it may overpredict the cost) but works well in practices
for problems that are largely decomposable.

       The level sum is the sum of the level costs of all the goal literals
       combined. The "level cost" to achieve any single goal literal is the
       level at which the literal first appears in the planning graph. Note
       that the level cost is **NOT** the minimum number of actions to
       achieve a single goal literal.
       
       For example, if Goal_1 first appears in level 0 of the graph (i.e.,
       it is satisfied at the root of the planning graph) and Goal_2 first
       appears in level 3, then the levelsum is 0 + 3 = 3.


**Set-Level Heuristic:** Finds the level at which all the literals in the
conjunctive goal appear in the planning graph without any pair of them being
mutually exclusive. This heuristic gives the correct values of 2 for our
original problem and infinity for the problem without Bake(Cake). It dominates
the max-level heuristic and works extremely well on tasks in which there is a
good deal of interaction among subplans.









$\hspace{4cm}$


# Hello world






