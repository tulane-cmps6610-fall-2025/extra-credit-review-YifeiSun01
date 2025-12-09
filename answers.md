# CMPS 6610 Extra Credit Answers
  
In this extra credit assignment, we will test and review concepts you
   have learned since the midterm exam. Please add your written answers
   to `answers.md` which you can convert to a PDF using
   `convert.sh`. Alternatively, you may scan and upload written
   answers to a file named `answers.pdf`.



1. **Algorithmic Paradigms**

My favorite algorithmic paradigm is Dynamic Programming (DP). I find DP appealing because it applies to a wide range of problems without requiring the strict structural assumptions that greedy algorithms rely on. Greedy methods need a very strong “greedy-choice property,” but DP works as long as a problem has optimal substructure and overlapping subproblems, which appear far more commonly in practice.

DP essentially uses space to save time. A naïve recursive solution often forms an exponentially large recursion tree, because the same subproblems are recomputed many times. DP turns this recursion tree into a Directed Acyclic Graph (DAG) of subproblems, where each subproblem is solved exactly once. This eliminates exponential blow-up and makes the solution both elegant and efficient.

Classic examples such as Edit Distance and Dynamic Time Warping (DTW) are fundamentally DP problems: they use a table to store the solutions of all pairs of prefixes, and each entry depends on a constant number of neighboring entries. Without DP, these problems would take an impractically long time using pure recursion. DP makes them run in polynomial time.

I particularly remember the coin-change and edit-distance examples: the plain recursive version grows exponentially, but with DP the solution finishes almost instantly. That contrast made the power of DP very vivid to me.

Of course, DP has trade-offs. It typically requires large memory, since we store many intermediate results. For sequence problems, DP often needs a full 2D table. DTW is a good example: although elegant, its complexity is $O(n^2)$ because we must fill a 2D matrix. Extending DTW to higher-dimensional signals becomes difficult because the number of alignment directions and required storage grows rapidly.

Even so, I appreciate DP for its generality, clarity, and the deep idea behind it: identify the core repeated structure of a problem, store subproblem results, and transform exponential recursion into a manageable DAG. It feels both powerful and conceptually intuitive.

2. **Divide and Conquer**

No.
Problems that can be solved by divide and conquer do not necessarily satisfy the optimal substructure property.
Optimal substructure is a property of optimization problems: an optimal solution can be constructed from optimal solutions to subproblems. However, many classic divide-and-conquer problems are not optimization problems at all, so optimal substructure does not even apply.
For example, sorting an array (e.g., using mergesort or quicksort) is solved by divide and conquer: we split the array into subarrays, recursively sort each subarray, and then combine the results. But sorting is not an optimization problem — there is no notion of a “more optimal” sorted array, only correct vs incorrect. Thus sorting is a divide-and-conquer problem without an optimal substructure property.

3. **Randomization**


We consider the random variable X denoting the number of comparisons performed by randomized Quicksort on an input of size n. It is known that the expected work satisfies $E[X] = O(n \log n)$. For convenience we use the bound $E[X] \le C n \log n$ for some constant $C > 0$. By Markov's inequality,
$$P[X \ge a] \le \frac{E[X]}{a}.$$

To study the likelihood of quadratic behavior, we set $a = k n^{2}$ for any constant $k > 0$. Then
$$P[X \ge k n^{2}] \le \frac{C n \log n}{k n^{2}} = \frac{C}{k} \cdot \frac{\log n}{n}.$$
This goes to zero as $n$ grows. Therefore the probability that Quicksort performs quadratic work vanishes, and large deviations of this type become increasingly unlikely.

We next examine the probability that Quicksort exceeds its expected running time by a factor of $10^{c}$ where $c > 0$. Setting $a = 10^{c} n \log n$ in Markov's inequality gives
$$P[X \ge 10^{c} n \log n] \le \frac{C n \log n}{10^{c} n \log n} = \frac{C}{10^{c}}.$$
Thus the probability of exceeding the expected value by a multiplicative factor of $10^{c}$ decreases exponentially in $c$.

These two bounds together imply that the work of Quicksort is concentrated near its expectation. Catastrophically large running times occur with vanishing probability, and extremely large constant-factor deviations from the mean have exponentially small probability.

4. **Greedy Algorithms**

To minimize the average waiting time, it is enough to minimize the total waiting time. Suppose a schedule is not ordered by nondecreasing processing times. Then there exists an adjacent pair of jobs $i$ and $j$ such that $p_i > p_j$ and the schedule places them in the order $(i,j)$. Let $W$ be the sum of processing times of all jobs before this pair. In this order, the waiting times of the two jobs are

$$wait(i) = W$$
$$wait(j) = W + p_i$$

and their total contribution is $$2W + p_i$$. After swapping the pair so that the order becomes $(j,i)$, the waiting times become

$$wait(j) = W$$
$$wait(i) = W + p_j$$

and their contribution becomes $$2W + p_j$$. Since $p_j < p_i$, the inequality $$2W + p_j < 2W + p_i$$ holds, so the swap strictly decreases the total waiting time. All other jobs keep the same waiting time, because only this adjacent pair changes order.

Therefore any schedule containing such an inversion cannot be optimal, since swapping the inverted pair always reduces the total waiting time. Repeating this process removes all inversions and produces exactly the schedule in which jobs appear in nondecreasing order of processing time. This schedule is the unique schedule that admits no improving swap, so it minimizes the total and therefore the average waiting time.```



5. **Dynamic Programming**

Consider first a recurrence with maximum span. The recurrence $$dp[n]=dp[n-1]+1$$ has optimal substructure, but every value depends on the previous one. The induced DAG is a single chain of length $$n$$ because each $$dp[k]$$ requires $$dp[k-1]$$ before it can be computed. Thus the longest path is $$n$$ and the span is $$Theta(n)$$, so no parallelism is possible.

Consider now a recurrence with polylogarithmic span. The recurrence $$T(n)=T(n/2)+T(n/2)+1$$ also has optimal substructure, but each subproblem $$T(n/2)$$ is independent of the other. The induced DAG is a balanced binary tree of height $$log n$$, so the longest path has length $$Theta(log n)$$. Therefore the span is polylogarithmic and the recurrence admits ideal parallelism.


6. **Graphs**
