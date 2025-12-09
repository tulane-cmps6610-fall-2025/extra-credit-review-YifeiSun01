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


3. **Randomization**

- 3a. 

- 3b.

4. **Greedy Algorithms**

5. **Dynamic Programming**

6. **Graphs**
