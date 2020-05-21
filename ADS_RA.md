% Algorithms and Data Structures - Roberto Amandini module
% Saul Pierotti
% \today


---
header-includes:
	\usepackage{algpseudocode}
---

# Disjoint sets
* A disjoint set is a set containing a number of sets without elements in common
	* $S=\{S_1,S_2,...,S_k\}=\{\{a_1,a_2,...,a_n\},\{b_1, b_2,...,b_n\},...,\{k_1,k_2,...,k_n\}\}$
* Each set is identified by a representative, which is a menìmber of the set itslef
	* In most cases it doen't matter which element is the representative, it just matters that it is always the same for the given set
* MAKE-SET($x$) creates a new set containing only $x$, which is this also its representative
	* Since we are defining disjoint sets, we need also to assure that $x$ in not in any other set
* UNION($x, y$) unites the 2 sets containing $x$ and $y$ into a new set
* FIND-SET($x$) returns a pointer to the representative of the set containing $x$
* A disjoint set can be useful to describe the connected components of a grahp
	* We can define the function CONNECTED-COMPONENTS($G$) that computes the connected components and SAME-COMPONENTS($u$, $v$) that checks if 2 nodes belong to the same connected component

\begin{algorithmic}
\Statex
\Statex
\Procedure{CONNECTED-COMPONETS}{$G$}
	\ForAll{nodes $v \in G.V$}
		\State \Call{MAKE-SET}{v}
	\EndFor
	\ForAll{edges $(u,v) \in G.E$}
		\If{\Call{FIND-SET}{u} $\neq$ \Call{FIND-SET}{v}}
		\State \Call{Union}{$u,v$}
		\EndIf
	\EndFor
\EndProcedure
\Statex
\Statex
\Procedure{SAME-COMPONETS}{$u,v$}
	\If{\Call{FIND-SET}{u} $\neq$ \Call{FIND-SET}{v}}
		\State \Return TRUE
	\Else
		\State \Return FALSE
	\EndIf
\EndProcedure
\end{algorithmic}

* A disjoint set can be implemented naively with a linked list
	* Each set is represented by a linked list
	* Each element of the list stores
		* The object itself
		* A pointer to the next element
		* A pointer to the set representative
	* The first object of the list is taken as representative
	* In this case MAKE-SET and FIND-SET are easy to implement and cost O(1)
		* MAKE-SET just creates a new list with the object
		* FIND-SET follows the pointer back to the representative
	* UNION is implemented by appending 2 lists and updating the pointers
		* Updating the pointers costs $\Theta(|L_y|)$! ($|L_y|$ is the lenght of the second list)
* A disjoint-set forest is a better representation
	* Each set is a rooted tree
	* Each node contains an element and a pointer to its parent
		* The root points to itself
	* FIND-SET needs to trasverse the tree until the root and costs O(n) in the worst case
	* UNION is easy: I just make the root of one tree point to the root of another
		* However, I need to call 2 times FIND-SET to find the 2 roots if I am not storing them!
	* We can improve average performances by doing union by rank and path compression
	* Union by rank: the smaller tree should point to the bigger, not vice-versa
		* In this way I minimize the height of the resulting tree
		* To do this I store a property x.rank for each node
		* The rank is the heigh of the subtree rooted in the current node
	* Path compression: I redirect to the root each node so that I do not need to transverse the entire tree each time
	* If I am using both path compression and union by rank, the rank is not any more the exact heigh, but its upper bound
	* Path compression and union by rank are dynamically applied and maintained by FIND-SET and UNION

\begin{algorithmic}
\Statex
\Statex
\Procedure{MAKE-SET}{$x$}
	\State $x.p = x$
	\State $x.rank = 0$
\EndProcedure
\Statex
\Statex
\Procedure{UNION}{$x, y$}
	\State $x.root =$\Call{FIND-SET}{$x$}
	\State $y.root =$\Call{FIND-SET}{$y$}
	\State \Call{LINK}{$x.root, y.root$}
\EndProcedure
\Statex
\Statex
\Procedure{LINK}{$x, y$}
	\If{$x.rank > y.rank$}
		\State $y.p = x$
	\Else
		\State $x.p = y$
		\If{$x.rank == y.rank$}
			\State $y.rank = y.rank + 1$ // if the ranks are different adding the subtree cannot change either rank!
		\EndIf
	\EndIf
\EndProcedure
\Statex
\Statex
\Procedure{FIND-SET}{$x$}
	\If{$x.p \neq x$} // x is not a root
		\State $x.p =$ \Call{FIND-SET}{$x.p$}
	\EndIf
	\State \Return $x.p$
\EndProcedure
\Statex
\Statex
\end{algorithmic}

# Longest common subsequence (LCA) 
* The LCA problem is a classical problem that can be solved with dynamic programmin
* In this context an LCA is considered as a possibly gapped subsequence
* The algorithm is essentially the NW withouth gap penalties
* I can make it more space-efficient by not storing the backtrack matrix
	* I can always compute it from the scores
* I can also only store the last 2 rows, instead of the entire matrix
	* In this case I cannot do bactrack!
* The cost is O(nm) for building the matrx and O(n+m) for the backtrack

# Approzimate string matching (ASM)
* I want to serch a query string $P$ of lenght $m$ in a target string $T$ of lenght $n$ with $m < n$
* In some cases I may want to allow inexact matches
* A k-approximation of $P$ in $T$ is a string $P'$ shorter or equal to $P$ itself which occurs in $T$ and can be obtained from $P$ in $0 \leq k \leq m$ edit operations
* An edit operation is a substitution, insertion or deletion
* ASM takes in input $P$ and $T$ and returns the k-approximation $P'$ with minimum $k$
	* It returns the approximation with minimum edit distance, without aatention to its lenght!
* I define a table $D$ that stores the minimum edit distance between the $P[1:i]$ and $T[1:j]$
* I initialise the first row and column
	* $D[0,j] = 0$ since I can match an empty $P$ everywhere in $T$ without any edit
	* $D[i,0] = i$ since to match a string of lenght $i$ to an empty string I need to delete $i$ charachters
* Then I fill iteratively or recursively
	* If $p_i = t_j \implies D[i,j] = D[i-1,j-1]$ since I don't need to do any additional edit
	* If $p_i \neq t_j$ I increment $k$ by assigning to $D[i,j]$ the minimum between
		* $D[i-1,j-1] + 1$
		* $D[i-1,j] + 1$
		* $D[i,j-1] + 1$
* The minimum $k$ can be retrieved from the smallest value of the last row
* I can backtrack to rebuild the match
* The cost is O(nm) for building the matrix
* Backtracking costs O(n+m) in the worst case (if I need tro tranverse all the table)

# Minimum Spanning Tree (MST)
* Given an undirected weighted graph $G = (V, E)$ I want to find an MST with $T \subseteq E$ such that
	* $T$ is a tree (undirected, connected, acyclic)
	* $T$ is connects all the nodes in $V$ (it is a spanning tree)
	* $w(T) = \sum_{(u,v) \in T}w(u,v)$ is the minimal possible
		* I want the tree with the minimum total weight
* It can be applied to designing electric circuits with the minimum amount of wire and to construct minimum ultrametric trees
* The MST problem can be solved with a greedy strategy
* An MST always exists for connected undirected graphs but may not be unique
* For designing an MST algo is important the concept of safe edge
	* It is an edge that when added to a subset $A \subseteq T$ makes $A'$ still a subset of $T$
* It is said that a cut respects a set of edges if there is no edge crossing the cut
* An edge crossing the cut is called light edge if its weight is minimum among all the edges that cross the cut
* **Safe edge theorem**
	* $A \subseteq T$ is the subset of some MST $T$ for the graph $G = (V,E)$
	* If $(S, V-S)$ is a cut respecting A and $(u,v)$ is a light edge crossing that cut, then $(u,v)$ is safe for $A$

\begin{algorithmic}
\Statex
\Procedure{GENERIC-MST}{$G$}
	\State $T_0 = \emptyset$
	\While{$T_i$ is not an MST for $G$}
		\State Find $(u,v) \in G.E - T_i$ which is $\textbf{safe}$ for $T_i$
		\State i = i + 1
		\State $T_i = T_{i-1} \cup \{(u,v)\}$
	\EndWhile
	\State \Return $T_i$
\EndProcedure
\end{algorithmic}

## Kruskal algorithm
* I incrementally grow and merge a forest of MSTs by adding light edges intil I have the complete MST
* I use disjoint sets to represent the forest, one set per tree
* It's complexity is $O=(n \log{m})$
* It is not the fastes algo, there are MST algos in $O(n+m)$

\begin{algorithmic}
\Statex
\Procedure{KRUSCAL-MST}{$G$}
	\State $A = \emptyset$
	\ForAll $v \in G.V$
		\State MAKE-SET($v$)
	\EndFor 
	\State $S =$ \Call{SORT}{$G.E, w$} // sort edges non-decreasingly according to weight
	\ForAll $(u,v) \in S$
		\If{\Call{FIND-SET}{$u$} $\neq$ \Call{FIND-SET}{$u$}} // if u and v are on different trees
			\State $A = A \cup {(u,v)}$
			\State \Call{UNION}{$(u,v)$}
		\EndIf
	\EndFor
	\State \Return $A$
\EndProcedure
\end{algorithmic}

## Local search (LS)
* It is an apporach for solving optimization problems
* It starts from a sub-optimal solution $S$ and seraches for a better solution $S'$ in the neighborhood of $S$ $N(S)$ in an iterative way
* It finds a local optimum in the solution space
* We can use LS to solve the MST problem

## LS sorting
* I can frame a sorting problem as an optimization problem
* Given a set of elements $A$ we say that $a_j$ and $a_i$ are misplaced if they are in the wrong order
* If $a_i$ and $a_j$ are misplaced we say that $(i,j)$ is a conflict for $A$
* $A$ is sorted when there are no conflicts
* I can sort $A$ by minimising the number of conflicts
* The neighborhood of $A$ is the set of all the possible permutations oof $A$ that can be obtained by swapping 2 elements
* INSERTION-SORT can be seen as an LS algo however
	* It only swaps contiguous elements
	* At each step it solves just 1 conflict
* SHELL-SORT was proposed by D. L. Shell to overcome this problems
	* It is a generalization of INSERTION-SORT
	* It considers elements at distance $h \geq 1$
	* $h$ is decreased at each iteration until $h = 1$
	* The algorthm is correct if at a certain point I use $h = 1$
	* The series of $h$ used is called gap sequence
		* For instance I can use $h = ..., 1093, 363, 32, 1$
	* When $h = 1$ SHELL-SORT is exactly equivalent to INSERTION-SORT
	* It is empirically one of the fastest sorting algorithms when the sequence is small (~5000 elements)

\begin{algorithmic}
\Statex
\Procedure{SHELL-SORT}{$A$}
	\State $h = 1$
	\While{$h \leq A.lenght$} // I am generating a series of h, this can vary
		\State $h = 3*h+1$
	\EndWhile 
	\State $h = \lfloor h/3 \rfloor$
	\While{$h \geq 1$}
		\For{$i = h+1$ to $A.lenght$}
		\State $k = A[i]$
		\State $j = i$
			\While{$j > h$ and $A[j-h] > k$}
				\State $A[j] = A[j-h]$
				\State $j = j - h$
			\EndWhile
		\State $A[j] = k$
		\EndFor
	\State $h =\lfloor h/3 \rfloor$
	\EndWhile
\EndProcedure
\end{algorithmic}

# Backtracking
* Try a solution, if it is not good go back and try a different one
* It can be used for decision and optimization problems
* These algorithms are usually really expensive, exponential or super-exponential
	* This is due to the magnitude of the search space
* It can be recursively or iteratively implemented


# Hard problems
* P is the set of problems solvable in polynomial time
* NP is the set of problems verifyable in polynomial time
* A problem in P is always also in NP, so $P \subseteq NP$
	* This is beacause If I can find a solution in polynomial time, I do not need to check it!
* NP-hard problems are at least as hard or harder than any problem in NP
	* An NP-hard problem does not necessarily belong to NP
	* It could be not possible to verify it in polynomial time
* NP-complete problems are NP-hard problems that are in NP
	* They are NP problems (so verifyable in polynomial time) that are by definition the hardest in NP
* Any given NP problem is either NP-complete itself, or easier than an NP-complete problem
* If I can find a polynomial solution for one NP-complete probelm, then by definition all the NP porblems have a polynomial solution
* The open questionthen is: Is $P=NP$?
	* Are all the NP problems solvable in polynomial time?
	* If I can solve an NP-hard problem in polynomial time, then all the NP problems are polynomial
	* This means than $P=NP$
* I have a decision problem for which
	* I have a polynomial algo for verifying a solution to it
		* A verifyer given a solution returns True if the solution is feasible, Fasle otherwise
		* A solution $S$ is also called certificate or witness for the problem
	* I have an exponential algo for finding a solution with exhaustive search
	* We don't know any polynomial algorithm to find a solution to it
* If I can find a polynomial algorithm for this problem, then I found a polynomiam algortihm for all the problems of this class!
* If I have an NP-hard problem I can
	* Solve a special case
	* Find a good enough solution
	* I can use an exponential algorithm but in a clever way (branch and bound)
	* I use an heuristic algorithm (one that is not guaranteed to be correct)

## Graph coloring
* Can I color all the nodes of a graph with $k$ colors, without having any neighbor node with the same color?
* I can easily verify this by checking the size of the maximal clique of the graph
	* A clique is a set of completely interconnected nodes

\begin{algorithmic}
\Statex
\Procedure{VERIFY-CLIQUE}{$G, k, S$}
	\If{$|S| < k$}
		\State \Return{FALSE}
	\EndIf
	\For{$u \in S$}
		\For{$v \in S - \{u\}$}
			\If{$(u,v) \not\in G.E$}
				\State \Return{FALSE}
			\EndIf
		\EndFor
	\EndFor
	\State \Return{TRUE}
\EndProcedure
\end{algorithmic}

## Traveling salesperson

## Integer linear programming
* I have an integer matrix $A$ and an integer vector $b$
* Is there a boolean vector $x$ such that $Ax \leq b$?

## Boolean satisfiability
* I have a boolean formula in conjunctive normal form (CNF)
* A CNF is a conjunction of disjunctions clauses
* Can I assign its variables so that it evaluates to True?

## Branch and bound
* It is a smart enumeration method that avoids evaluating decisions that cannot lead to an optimal solution
