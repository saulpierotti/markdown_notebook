---
header-includes:
	\usepackage{algpseudocode}
---

# Algorithms and Data Structures - Ivan Lanese module
* Our main topic will be data structures (balanced trees, graphs) and algorithms (greedy, dynamic programming)
* Recursion will be essential for exploring search trees

Fibonacci recursive is incredibly slow with n above 35 while it can compute huge numbers in the iterative form.


```python
def fib(n):
	if n==1 or n==0:
		return 1
	elif n>1:
		return fib(n-1)+fib(n-2)
	else:
		print("fib not possible for negative numbers")

fib(10)
```

```python
def fib(n):
	if n==0 or n==1:
		return 1
	list = [1,1,2]
	for i in range(n-2):
		list=[list[1],list[2],list[1]+list[2]]
	return list[2]

fib(100)
```

## Balanced search trees
* A balanced tree is a bynary search tree (BST) that minimizes the height of the tree
	* In a BST the left subtree contains elements smaller than the root, the right subtree bigger
	* The BST property is useful for lookups and must be mantained by insertions and deletions
* I BSTs insertion and delition have a complexity linear with the height of the tree, $O(h)$
	* In a complete BST $h=\log{n}$, so insertion and deletion are $O(\log{n})$ with $n =$ number of nodes
* Insertions and deletions can make a complete BST unbalanced
* A tree built from ordered elements is maximally unbalanced
	* A way to create a generally balanced tree is to randomly permutate the input data when constructing the tree
* Modifications of BST have been developped for maintaining it as balanced as possible

## AVL trees
* AVL trees are almost balanced BST that support `insert()`, `delete()` and `lookup()` in $O(\log{n})$ time
* AVL introduce a balancing factor for each node $\beta(n)$
	* It is the difference in the height of the 2 subtrees of the node
	* A tree is balanced if for each node $|\beta|$ is less than 1

### Proof that for AVL $h=O(\log{n})$
* The most unbalanced AVL (and therefore the longest one) is a fibonacci tree
	* It puts everything on one side but it leaves on the other side only what is needed to make it AVL
	* It is defined as a BST of height $h$ having a left subtree of heigh $h-1$ and a right subtree of heigh $h-2$
		* $n_h = n_{h-1} + n_{h-2} + 1$
	* I want to prove that a fibonacci tree of heigh $h$ has $F_{h+3}-1$ nodes with $F_n$ being the $n^{th}$ fibonacci number
	* Base case: $h=0$
		* I have 1 node and it satisfies the condition
			* $n_0 = 1, F_3 = 2$
	* Induction: $n_h = n_{h-1} + n_{h-2} + 1$ by construction
		* $n_h = n_{h-1} + n_{h-2} + 1=F_{h+2}-1+F_{h+1}-1+1=F_{h+3}-1$
		* Since this is true for $h=0$, it is true for every $h$
	* Since $F_h = \Theta(\phi^h)$ with $\phi \approx 1.618$
		* $n_h = \Theta(\phi^h)$
		* $\Theta(\log{n_h}) = \Theta(h)$
		* $h=\Theta(\log{n_h})$
* Since the height of the longest AVL tree is $\Theta(\log{n})$, the heigh of an AVL tree is $O(n)$

### Operations in AVL trees
* `search()` is the same as in a generic BST, since it does not modify the AVL property
* `insert()` and `delete()` have to be modified so to maintain the AVL property
* The AVL property is maintained through an operation called rotation
	* It is a transformation that preserves the BST property
* There are 4 possible rotations, and they are symmetric 2 by 2
	* Which one to apply depends on the kind of inbalance
	* The rotation LL can be applied when the imbalance is the the left subtree of the left child, LR, RL, and RR in the corresponding cases
* The rotation LL has cost $O(1)$ and restores the AVL property
	* I can use it when the leftmost subtree is of heigh $h+2$ and the leftomost one $h$
	* I will restore AVL by creating 2 $h+1$ subtrees
* The LR case cannot be resolved with a single rotation
	* I need 2 rotations, one to the left and one to the right

### AVL insertion
* I insert a new value like in a normal BST
* I recalculate $\beta$ for all nodes that contain the leaf
	* In the worst case I need to calculate it for one node for each leavel from the leaf to the root, so it is $O(h)=O(\log{n})$
* If at least 1 node has $|\beta| > 1$ I need to rebalance the tree with rotations from bottom to top, in $O(1)$
* In total, an insertion in an AVL tree takes $O(\log{n})$

### AVL deletion
* I remove like in a normal BST
* I rebalance like for the insertion

All the basic operations in AVL take $O(\log{n})$

## Working on disk
* Big data structures cannot be kept in memory but need to be partially loaded in memory from disk, when needed
* Computational time is heavily dependent on the number of r/w operations into disk, since it is much slower than memory
* There are data structures that minimize disk access

## 2-3 trees
* It is a tree in which all nodes have 2 or 3 children and all the leaves are at the same distance from the root
* Keys and satellite data are stored in the leaves
* Leaves are sorted in ascending order from left to right
* Every internal node $v$ maintains up to 2 pieces of information
	* `v.L`, the max key in the subtree rooted at its left child
	* `v.M`, the max key in the subtree rooted at its middle child
* Internal nodes are small, since they contain only keys, while leaves are large
	* I can keep the internal nodes in memory and the leaves into disk
* In a 2-3 tree with $n$ nodes, $f$ leaves and with heigh $h$
	* $2^h \leq f \leq 3^h$
	* $2^{h+1} -1 \leq n \leq \frac{3^{h+1}-1}{2}$
* The heigh of a 2-3 tree is $\Theta(\log{n})$

The following searches a 2-3 tree in $O(\log{n})$ time

\begin{algorithmic}
\vspace{1em}
\Procedure{SEARCH-23}{$v,k$}
	\If{$v$ is None}:
		\State \Return None
	\ElsIf{$v$ is leaf}
		\If{$v.key == k$}
			\State \Return $v$
		\Else
			\State \Return None
		\EndIf
	\Else
		\If{$k <= v.L$}
			\State \Return \Call{SEARCH-23}{$v.left, k$}
		\ElsIf{$v.right \not= \mbox{None}$ \textbf{and} $k > v.M$}:
			\State \Return \Call{SEARCH-23}{$v.right, k$}
		\Else
			\State \Return \Call{SEARCH-23}{$v.mid, k$}
		\EndIf
	\EndIf
\EndProcedure
\end{algorithmic}

### Insertion in 2-3 trees
* I create al leaf `v` with key `k`
* I search for a node `u` at the penultimate level, that will become father of `v`
* If possible I add `v` as a child of `u`
* If `u` has already 3 children, I do a recursive splitting back until it is needed
* It takes $O(\log{n}$ to find the father of the new node and $O(1)$ to do the splitting
* In the worst case I do $O(\log{n})$ splits back until the root
* The overall insertion cost is $O(\log{n})$

### Deletion in 2-3 trees
* I search for a leaf `v` with key `k` to be deleted in $O(\log{n})$
	* I detach it from its father `u`
* If `u` had 2 children now it violates the 2-3 property, so I need to merge it with a neighbor
	* This can be propagated until the root if needed

* I search for a node `u` at the penultimate level, that will become father of `v`
* If possible I add `v` as a child of `u`
* If `u` has already 3 children, I do a recursive splitting back until it is needed
* It takes $O(\log{n}$ to find the father of the new node and $O(1)$ to do the splitting
* In the worst case I do $O(\log{n})$ splits back until the root
* The overall insertion cost is $O(\log{n})$

## Exercise on recursion
Write a recursive function that computes the height of a node
```python
def h(node):
	if ((n is leaf) or (n==None)): # n is a leaf or it is not existent
		return 0
	else:
		return max(h(n.left),h(n.right))+1
```
Computing the height of a node recursively has complexity O(n)

## B-trees
* They are similar to 2-3 trees but used for even larger amounts of data, when also the keys are too many to be kept in memory
* B-trees are used for indexing large storages with slow access
	* They are used by many databases
	* They have a huge branching factor, they can have thousands of childre per node
* I want to minimize disk access, since it is usually a bottleneck
* I cannot read a single byte from a disk, it is read in sectors
	* Also SSDs have a minimal access unit, the block
* In B-trees I have keys stored in all nodes
* The grade $t \geq 2$ of a B-tree is the minimum number of children that each node different from the root can have
	* We select the grade so that a node can be as large as possible but fit in a single sector on the disk
* It has the following properties
	* All the leaves have the same depth
	* Every node but the root maintains $v$ ordered keys with $t-1 \leq v \leq 2t-1$
	* The root has $1 \leq v \leq 2t-1$
	* The keys stored in the first subtree are smaller than the first key of the node, the ones in the second subtree are between the first and the second key, and so on
* The heigh of a B-tree with n keys is $h \leq \log_t{(n+1)/2}$

### Search in B-trees
* I check keys in the current node
* If I don't find it I search it in the correct subtree
* I visit $O(\log_t{n})$ nodes and each time I have a cost of $O(t)$, so the total cost is $O(t\log_t{n})$

\begin{algorithmic}
\vspace{1em}
\Procedure{BTREE-SEARCH}{$v, k$}
	\State $i = 1$
	\While{$i <= len(v)$ \textbf{and} $key > v[i]$}:
		\State $i += 1$
	\EndWhile
	\If{$i <= len(v)$ \textbf{and} $k==v[i]$}
		\State \Return v[i].data
	\ElsIf{$v$ is leaf}
		\State \Return None
	\Else
		\State \Return \Call{BTREE-SEARCH}{$v.child[i], k$}
	\EndIf
\EndProcedure
\end{algorithmic}

* Note that the keys on a node are ordered: I can do a binary search instead of a linear search
	* Binary search takes $O(\log{n})$
	* In this case the total complexity will be $O(\log{t}\log_t{n})=O(\log{n})$

### Insert in B-trees
* I search the leaf $f$ in which I can insert the key $k$
* If the leaf is not full (less than 2t-1 keys) I insert $k$ in the correct position
* If it is full I split the leaf $f$
	* I put the key number $t$ of $f$ to $f.parent$
		* If $f.p$ is full I need to split it and recurse
		* In the worst case this will split the root and generate a new one
* I cannot use binary search in this case since I cannot split an array in that way, I need to copy half of its elements in $O(t)$
* Total cost is $O(t \log_t{n})$

### Delete in B-trees
* I want to delete key $k$
* I first search it
* If it is not in a leaf
	* I find the node containing the predecessor of k (biggest smaller value)
	* I substitute the $k$ with $k.p$
* If it is in a leaf
	* If the leaf has more that $t-1$ keys I just delete it
	* If it has $t-1$ keys
		* If one brother of the leaf has more than $t-1$ keys I redistribute the keys
		* If not I make a fusion with one of the brothers
* It has the same complexity of insertion, $O(t \log_t{n})$

## Graphs
* A graph is composed of a set of vertices and edges, $G=(V, E)$
* An edge $e=(u,v)$ is a pair of vertices
* The number of edges $E$ can at most be $V^2$
* A graph can be directed or undirected
* A simple path is one in which I never pass on the same vertex
* A cycle is a symple path with the same start and end vertex
* Adjacent vertices are those connected by an edge
* The degree of a vertex is the number of adjacent vertices that it has
* A graph does not necessarily need to be connected
	* There can be node or subgraphs that don't have edges between them
* A strongly connected graph has edges between each pair of vertices
* The strongly connected components of a graph are its maximal strongly connected subgraphs
* A tree is a connected acyclic graph and a forest is a collection of trees
* Fundamental graph operations ($G$, $v$, $e$ are graph, vertex, edge)
	* `Create(G)`
	* `IsEmpty(G)`
	* `InsVertex(G,v)`
	* `InsEdge(G,v1,v2)`
	* `DelVertex(G,v)`
	* `DelEdge(G,v1,v2)`
	* `AdjSet(G,v)` (return the set of adjacent vertices of $v$)

### Representations
* I can represent a graph with an adjacency matrix of dimensions $V^2$ with $V$ being the number of nodes
	* It is preferred when I need to quickly get information about gthe connectivity if 2 specific nodes, or when the graph is dense (a lot of edges)
	* The space requires is $O(V^2)$
	* It can be a boolean matrix or contain weights for the respective edges
* I can use an adjacency list
	* It is formed by a list for each vertex containing all the adjacent vertices to it
	* Space is $\Theta(V+\sum deg(v))=\Theta(E+V)$
	* It is generally more used than the matrix, especially with sparse graphs (few edges)
	* It can also support weights
* I can use adjacency sets
	* I have a vector for vertices and one for edges
	* The edge vector is just a list of adjacent vertices for each node
	* The node vector contains for each node the number of its adjacent vertices
		* In low-level languages I also need to keep track of the end of the array, so I insert a fake node that starts at end of array + 1
	* I can use the node vector to parse correctly the edge vector
	* The space is $\Theta(E+V)$

### Graph trasversal
* It refers to the problem of visiting all the vertices of a graph
* The 2 most used graph trasversal algorithms are BFS and DFS

#### Breath-first search (BFS)
* I first explore closer vertices, and then far ones, starting from vertix $s$
* At the beginning all the verteces are undiscovered (sometimes said WHITE)
* I start from vertex s, I put it in the queue Q and I mark it as discovered
	* Discovered vertexes are referred to as GREY
* Until there is somenthing in Q
	* I take one vertex v from Q
	* I loop on the adjacency set of v
		* If the vertex u in the set is not discovered (WHITE)
			* I mark it as discovered (GREY)
			* I put u in Q
	* All the adjacenct set of v is GREY: I now mark v as BLACK

```python
def BFS(G, s):
	Q = NewQueue()
	EnQueue(Q, s)
	s.discovered = True
	while not IsEmpty(Q):
		v = DeQueue(Q)
		visit(v)
		for nv in AdjSet(G, v):
			if not nv.dicovered:
				EnQueue(Q,nv)
				nv.discovered = True
```
* Complexity analysis on an adjacency list
	* Each vertex is put in the queue once, since it is put in only when WHITE and it is marked as GREY before being put in
	* The queue operations take $O(1)$, and I do V of them, so $O(V)$
	* The adjacency list of v is scanned only when v is dequeued, so once
	* The sum of the lenght of the adjacency lists is $\Theta(E)$ with E the number of edges
	* The time spent scanning the adjacency lists is therefore $O(E)$
	* The toal time is therefore $O(V+E)$
* Complexity analysis on an adjacency matrix
	* Here there are the same considerations as above, but
	* For computing the adjacency set I need to scan the respective row of the matrix, so $O(V)$
	* I need to do this for all the V verteces so the toal complexity is $O(V^2)$

#### Depth-first search (DFS)
* I visit recursively all the unexplored neighbors of the current node
* At the end I backtrack to the original node

```python
def DFS(G, u):
	visit(u)
	for v in AdjSet(G, u):
		if not IsVisited(v):
			DFS(G, v)
```
* The time complexity is $O(E+V)$ with an adjacency list and $O(V^2)$ with an adjacency matrix for the same considerations made in BFS

### Topological sort
* A dependency graph shows casual dependencies between tasks
* I can arrange a series of tasks in a directed acyclic graph (DAG)
* A topological sort of a DAG $G=(V,E)$ is a linear ordering of its vertices such that if there is an edge $(u,v)$ then u appears before v in the ordering
* I can execute tasks in topological order without violating dependecies
* Topological sort algorithm
	* Nodes are added one by one at the start of a list
	* One node can be added only after all of its dependecies

```python
TopoSort(G):
	L = empty_list()
	for u in verteces(G):
		if u is not marked:
			topoDFS(G,u,L)
	return L

topoDFS(G, u, L):
	mark(u)
	for v in AdjSet(G,u):
		if v is not marked:
			topoDFS(G, v, L)
	addInFront(L,u) # u is added to L only after all the recursive calls have finished
```

## Greedy algorithms
* It always makes the locally optimal choice
* It is not guaranteed to give a globally optimal solution
* It is normally easy to code
* A problem has optimal substructure if the solution contains the solution of its subproblems

### Knapsack problem
* A thief can carry only a certain weight and he wants to maximise the value
* In the 0-1 formulation, only integer items can be taken (no half items)
	* It cannot be solved with a greedy approach, but it requires dynamic programming
* In the fractional formulation fractions of items are allowed
	* It can be solved with a greedy approach

```python
greeedy_knapsack_frac(weights, values, total_weight):
	unitary_val = []
	for i in indeces(weights):
		unitary_val.append(values[i]/weights[i])
	taken_index, taken_weight = [], []
	while total_weight > 0:
		for i in weights.indeces:
			if unitary_val[i] > max_i and i not in taken_index:
				max_i = i
		if total_weigth > weigths[max_i]:
			taken_index.append(i)
			taken_weight.append(weights[max_i])
			total_weight -= weights[max_i]
		else:
			taken_index.append(i)
			taken_weight.append(total_weight)
			total_weight = 0
	return taken_index, taken weight
```

### Huffman Codes
* If we assume that our alphabet has 26 letters, I need to use 5 bits for each letter (32 possible combinations) to represent it
* If I just assign a code to each letter, my message takes $n*5$ bits with n the number of letters in it
* Since letters have different frequency, I can exploit this and give shorter codes to the most frequent letters
	* The problem here is that the code is ambiguous, since I do not know how long a letter is
* Huffman codes are non-ambiguous variable-lenght codes
* They use a greedy approach based on a binary tree
* First I calculate the frequency of each letter
* I order the set of letters in non-increasing order
* The 2 least frequent letters are selected and placed as children of a node, and assign a new cumulative symbol
* I calculate again the frequencies with the new symbol and repeat the process
* At the end I have a binary tree with the letters as leaves
* I associate 1 to go left and 0 to go right
* I start always from the root and I explore the tree until I reach a leave
* Now I have one letter and I start again from the root
* They can save 20% to 90% of space compared to a fixed lenght code!
* An Huffman code is a prefix code: no codeword is part of the prefix of another

## Dynamic programming
* It was developped in 1950 by Bellman
* It is similar to divide et impera, but it stores the solution of subproblems (it has memoization)
* It requires the problem to have optimal substructure
* It can be implemented recursively (divide et impera with memoization) or iteratively (on a matrix)
	* The iterative version requires to be able to sort the problems so that I can solve all the dependecies of a problem before solving it
	* The recursive implementation is also called top-down and the iterative bottom-up
	* The iterative version has usually smaller constant factor because I avoid the many function calls

### Knapsack problem
* For the 0-1 knapsack problem, I can try to find the optimal solution for a subset of the objects
* I want to find the solution V of i objects with total weight less than the capacity of the sack j that maximises the value
	* $V(i,j)$ is the maximum value that can be obtained with the first i objects in a sack of capacity j
* In this algorithm the weights must be integers
* I create a matrix with i=(number of objects) and j=capacity and for each cell I compute the value of the sack
* The real solution (value) for the complete set is in the bottom right cell
* Base cases
	* $v(i,0)=0$, if capacity is 0 nothing fits
	* $v(1,j)=v[1] \mbox{ if } j>=w[1]\mbox{, } 0 \mbox{ if } j<w[1]$, if I can put only object 1 if it fits I have its value, otherwise 0
* For each cell and for each object, if it fits the maximum value selecting it is the maximum value of the knapsack with one object less plus the value of the object, if it does not fit is the maximum value of the knapsack with one object less
* General case
	* If object i does not fit, the value is the maximum value with j-1 objects (I am copying from the right)
		* $v(i,j)=v(i-1,j) \mbox{ if } j<w[i]$
	* If it fits and I decide to take, the value is the maximum value of the knapsack with just enough space for the object ($j-w[i]$) plus the value of the object
	* If it fits but I do not take it, the value is the maximum value of the knapsack with i-1 objects
	* Among those 2 possibilities I choose the one that gives the highest value
		* $v(i,j) = \max(v(i-1,j-w[i])+v[i],v(i-1,j)) \mbox{ if } j>=w[i]$
	* Since I am subtracting the weight from j, it has to be integer!
* In order to know which objects are in the best solution I need an additional table of booleans $k(i,j)$
	* A cell is true if object i belongs to the object used for calculating V(i,j), false otehrwise
	* $k(i,j)=1 \mbox{ if } v(i,j)!=v(i-1,j) \mbox{ else } 0$
* From matrix k, I start from the bottom right and I procede by subtracting w[i] at each step (I go to k(i,j-w[i]))
	* The included objects are the ones for which k is true in that position
* The subset sum problem is a variant of the knapsack in which I request that the sack is completely full

## Shortest Path
* Given a weighted graph $G=(V,E)$ which each edge having an associated cost $w(x,y)$, the cost of path $\pi=(v_0,v_1,...,v_k)$ that connects node $v_0$ with node $v_k$ is the sum of the weights of each edge
	* $w(\pi)=\sum_{i=1}^k w(v_{i-1}, v_i)$
* The shortest path $\pi^*$ is the one with the minimal cost
	* It does not exist when the 2 nodes are not reachable from each other
	* Also cycles with negative costs make the target unreachable, since I will continuously go around the cycle getting lower and lower cost
	* There can be more than one shortest path, with equal costs
* The single source shortest path from the source s is the set of shortest paths from s to all the reachable nodes
* The all-pairs shortest path is the set of shortest paths for all possible pairs of connected nodes
* There is no known algorithm that solves the shortest path without solving the single source shortest paths in the worst case
* The shortest path has optimal substructure: each subpath of it is by itself a shortest path
* In a directed graph without negative cycles there is a shortest path between any pair of nodes
* The shortest path tree $T$ of vertex s contains all the verteces rechable from s such that each path along $T$ is a shortest path
	* Given the optimal substructure, it is always possible to grow the partial tree $T$ until I reach the node of interest
* The distance between nodes $x$ and $y$ $d_{xy}$ is the cost of a shortest path connecting them if it exists, otherwise $+\infty$ if they are not connected and $-\infty$ if there is a negative weight cycle between them
	* It always holds that $d_{xx}=0$ and the triangular inequality $d_{xz}<=d_{xy}+d_{yz}>$
* A shortest path cannot contain cycles
	* It could contain 0 weight cycles, but in this case it is always possible to find another shortest path without the cycle
	* I can safely assume that in a graph with $V$ nodes, if a shortest path exists it has at most $V-1$ edges
		* If there are no cycles I can at most visit $V$ nodes, and they will be connected by $V-1$ edges

### Relaxation
* It is a technique used by various shortest-path algorithms
* For each vertex $v \in V$ I maintain an attribute $v.d$ which is an upper bound for the shortest path from the source $s$ to $v$
	* $v.d$ is a shortest path estimate
* In this representation $v.\pi$ is the predecessor of $v$ in the shortest path tree
* First I initialise everithing
	* $s.d = 0$ and $v.d = \infty \mbox{ } \forall \mbox{ } v \in V- \{s\}$
	* $v,\pi = \mbox{NIL}$ for all the nodes
* Then I relax the edge $(u,v)$ by testing whether I can improve the shortest path to $v$ by passing through $u$

\begin{algorithmic}
\Statex
\Procedure{INITIALIZE-SINGLE-SOURCE}{$G,s$}
	\ForAll{$v \in G.V$}
		\State $v.d = \infty$
		\State $v.\pi = \mbox{NIL}$
	\EndFor
	\State $s.d = 0$
\EndProcedure
\Statex
\Procedure{RELAX}{$u,v,w$}
	\If{$v.d > u.d + w(u,v)$}
		\State $v.d = u.d + w(u,v)$
		\State $v.\pi = u$
	\EndIf
\EndProcedure
\end{algorithmic}

### Dijkstra Algrithm
* It computes the shortest path from a single source provided that there are no negative edges
	* It is a greedy algorithm
	* The similar Bellman-Ford algorithm solves the problem also for negative edges but it is slower and it is based on dynamic programming
* The central lemma of Dijkstra: given a partial shortest path tree $T$ of node $s$, a node $u$ in $T$ and a node $v$ not in $T$, the edge $(u,v)$ that minimizes $d_{su}+w(u,v)$ belongs to the shortest path $\pi^*_{sv}$
	* In practice it means that the shortest edge connecting a shortest path to the node of interest is part of the shortest path to that node
	* If I take another route with more edges from the shortest path to the node I am guaranteed to not decrease the cost, sice weights are assumed to not be negative
	* If an edge is negative this is not necessarily true since adding an edge can decrese the cost
* Given the graph $G=(V,E)$ the algorithm maintains a subset of nodes $S \in V$ such that for each node in $S$ the shortest path from the source $s$ to that node has been determined
* Repeatedly, it selects a node $u \in V-S$ (a node for which I do not know still the shortest path) and add it to $S$ with the minimum shortest path estimate and relaxes all the edges leaving $u$
* I am here assuming that each weight $w(u,v) \geq 0$
* This implementation uses a min priority queue $Q$ containing the nodes $v$ with keys equal to $v.d$
	* Calling EXTRACT-MIN($Q$) means taking the node in the queue which is closest to the source $s$ in terms of shortest path estimate
	* At the fist call $s$ itself is extracted since $s.d = 0$ while $v.d = \infty$ for all the other nodes
* Running time
	* The INITIALIZE-SINGLE-SOURCE call is a $\Theta(V)$ operation
	* The queue is filled once with $V$ elements and since then always emptied
	* Each iteration of the while loop removes one element from $Q$, so it iterates $V$ times
		* EXTRACT-MIN is an $=O(\log{V})$ operation, as well as the assignment of $S$
		* The for loop iterates a number of times equal to the lenght of the adjacency set of the current node
			* The RELAX procedure is $\Theta(1)$
	* In general the number of total iteration of the for loop is the sum of all the adjacency lists, so it is $\Theta(E)$
	* The total running time is $O(V*\log{V}+E)$

\begin{algorithmic}
\Statex
\Require{$v.d \geq 0 \mbox{ } \forall \mbox{ } v \in G.V$}
\Statex
\Procedure{DIJKSTRA}{$G, w, s$}
	\State \Call{INITIALIZE-SINGLE-SOURCE}{$G,s$}
	\State $S = \emptyset$
	\State $Q = G.V$
	\While{$Q \not= \emptyset$}
		\State $u =$ \Call{EXTRACT-MIN}{$Q$}
		\State $S = S \cup \{u\}$
		\ForAll{$v \in G.Adj[u]$}
			\State \Call{RELAX}{$u,v,w$}
		\EndFor
	\EndWhile
\EndProcedure
\end{algorithmic}
