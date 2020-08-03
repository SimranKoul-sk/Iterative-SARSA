# Iterative-SARSA

The optimal path is the shortest path there is, after applying all the parameters and
restrictions. The optimal path can be either safe or unsafe to execute. The safe paths do
not pass close to obstacles or cliffs, unless absolutely necessary. On the other hand, the
unsafe paths disregard their closeness to cliffs and obstacles in order to find the most
optimal path (or the shortest path). The main need of path finding algorithms heightened
when the concept of self-driving cars started to float. In the present scenario, most of the
path calculations are done via reinforcement learning algorithms. Some of the
reinforcement learning algorithms that have been highlighted in the recent times are
SARSA and Q-learning. These algorithms trace the path of robot, helping it to avoid
obstacles as well as reach the target location via the shortest path. The main concept used
in these algorithms is the concept of rewards. Rewards are calculated based on two key
policies, i.e., on-policy and off-policy. The on-policy method calculates the coordinate of
the next step using the coordinate of the current step as well as the action of the current
policy, by the process of exploration. This removes the question of experimental risk,
which might lead to a sudden collapse of the program. SARSA uses this risk-free
approach. On the other hand, the off-policy method predicts the next coordinate of the
robot using the current coordinate of the robot along with a greedy action. The reward is
calculated using this greedy policy, although the robot follows the path as though the
greedy action wasn’t used. The off-policy has a better outcome factor in terms of shortest
path execution speed, but there is a heightened risk wherein the program might end up
crashing. Developing on these algorithms, we have come up with a new algorithm, called
Iterative SARSA, that provides us with the safest as well as the most optimal path
available.

LITERATURE SURVEY
Reinforcement Learning
A striking assortment of issues in mechanical autonomy might be normally expressed as
issues of reinforcement learning. Reinforcement learning empowers a robot to selfsufficiently find an ideal conduct through experimentation associations with the given
condition. Rather than expressly specifying the answer to the issue, in order to calculate
each step of the robot, the reinforcement methodology utilizes the feedback received from
the agent in the form of a scalar function.
The main aim of reinforcement learning to figure out an optimal policy π∗ that maps states
to actions, hence, maximizing the expected return J, which is analogous to the aggregated
expected reward.
J = E { ∑ 𝑅ℎ
𝐻
ℎ=0 }
The rewards can also be discounted to accommodate errors. This is done using the
discount factor  (where, 01)
J = E { ∑ 
ℎ𝑅ℎ

ℎ=0 }
where,
Rh is the overall reward w.r.t. agent h
Optimal Path
Traditionally, paths were calculated manually by entering the coordinates of the path into
the program. Since this method was tedious and posed various problems, the need to
create a new self-learning approach to autonomously calculate the path was needed. To
calculate the path, the work environment with all the cliffs and obstacles is created and
provided. The program runs the algorithm on this environment. This training is done with
reinforcement learning and neural networks.
On-policy
The on-policy is a method of reinforcement learning in which the next state is calculated
using the current state along with the data received by the exploration steps. The SARSA
algorithm uses this policy. Although, this policy may be a bit more expensive, when
compared to the off-policy method, it is safer and has lower risks.
Off-policy
The off-policy is a method of reinforcement learning in which the next state is calculated
using the current state along with a greedy step. This policy predicts the next
coordinate/state instead of calculating it, as seen in the on-policy method. The coordinate
with the greatest reward is chosen as the next state. Even though the next state is chosen
based on the reward system, the program processes it as though the greedy algorithm
wasn’t used at all. On using this algorithm, even though we get the most optimal path
possible, it might be risky in some situations, in which we end up with a high negative
reward. The Q-learning algorithm uses this policy. 

SARSA
SARSA (State-Action-Reward-State-Action) is called so, because it experiences to
update the Q-values. It uses the on-policy method. SARSA is represented with the
attributes {S, A, , }, where, S is the set of states, A is a set of actions, (01) is the
discount and (01) is the step size. These are used to calculate the Q-values (Q [S,
A]).
Qnew (st,at)  Qold (st,at) + [rt+ .Qexploration value (st+1,at+1) – Qold (st,at)]
where,
st represents the initial state,
st+1 represents the final state,
rt represents the reward
Q-learning
Q-learning is the reinforcement algorithm in which, the agent takes the most optimal
action under different circumstances. This algorithm uses the off-policy model to obtain
its Q-values, and hence, reward is calculated based on the greedy action. Q-learning is
also represented with the attributes {S, A, , }, where, S is the set of states, A is a set of
actions, (01) is the discount and (01) is the step size. These are used to
calculate the Q-values (Q [S, A]).
Qnew (st,at)  Qold (st,at) + [rt+ .maxa.Qestimated future value (st+1,a) – Qold (st,at)]
where,
st represents the initial state,
st+1 represents the final state,
rt represents the reward

PROPOSED METHOD
Iterative SARSA
Elaborating on the concept of the SARSA algorithm, we have proposed our new iterative
algorithm. Like in the SARSA algorithm, the actor moves from the start to the end
location. In the iterative SARSA algorithm, once the actor reaches the final destination,
the start and end point are interchanged and the algorithm is rerun. According to the
concept of SARSA, the path found is always a safe one, unlike in the Q-learning
algorithm. Hence, any path that’s calculated is going to be safe. Once the iteration is
completed, the shortest path is selected out of all the iterations and the path is highlighted.
Although, iterative SARSA has a high time complexity, it provides us with the best safe
path.

Algorithm
1: initialize number of iterations ‘i’
2: initialize pathlength l →  (based on grid environment)
3: initialize Q (s, a) for all s, a
4: store the coordinate value of the start location
5: loop over episodes
6: initialize s
7: repeat this for each step of the episode
8: choose a from s using the * policy extracted from Q
9: Qnew (st,at)  Qold (st,at)
+[rt+ .Qexploration value (st+1,at+1) – Qold (st,at)]
10: st  st+1
11: end loop
12: store the length of the path calculated in l’
13: if (l’< l)
 {
 l = l’;
 }
14: store the coordinate value of the end location
15: i--;
16: interchange the coordinate values of the start and end location
17: if (i  0)
 {
 jump to step 3
 }
 else
 {
 display l and terminate
 }
 
IMPLEMENTATION
The analysis for the program was done by creating a fixed environment wherein, we ran
the Q-learning, SARSA and Iterative SARSA algorithm. Based on the time of execution,
optimal path and safeness of the algorithm, we have concluded the appropriate scenarios
for each algorithm. For the shortest path, we have used the Q-table to calculate and count
the path length. As for the time calculation, we have used the timeit() function. The
episode via steps and episode via cost graphs have also been calculated. An, episode is a
sequence of steps the actor takes in each traversal. The episode via steps graph shows us
the number of episodes vs. the number of steps in each episode and the episode via cost
graph shows us the number of episodes vs. the cost of each episode. 

CONCLUSION
According to our inference, the Q-learning algorithm executes the fastest and gives the
most optimal path. But, as we can see in Fig2., the path chosen by Q-learning passes
between the 2 cliffs. This possesses a high executional risk in which the program might
crash. Coming to SARSA, this algorithm takes comparatively more time to execute.
Although this algorithm is safe, it has a longer path length (Fig4.). As we come to the
Iterative SARSA algorithm, although it has a much higher time complexity, it finds the
safest optimal path (Fig6(c).).
Hence, if one wants to calculate the path without considering the executional risks, the
Q-learning algorithm can be considered. If a safe path, disregarding the path length, and
with low execution time has to be calculated, the SARSA algorithm can be used. The
Iterative SARSA algorithm can be used when time complexity is not an issue and we
want the safest most optimal path.
