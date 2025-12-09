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

5. **Dynamic Programming**

6. **Graphs**
