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

### Search in 2-3 trees
```python
def search23(v,k):
    if v is None:
        return None
    if v is leaf:
        if v.key == k:
            return v
        else:
            return None
    else:
        if k <= v.L:
            return search23(v.left, k)
        elif (v.right != None) and (k > v.M):
            return search23(v.right, k)
        else:
            return search23(v.mid, k)
```
This operation takes $O(\log{n})$

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

``` python
def btree_search(v, k):
    i = 1
    while (i <= len(v) and key > v[i]):
        i += 1
    if (i <= len(v) and k==v[i]:
        return v[i].data
    elif (v is leaf):
        return None
    else:
        return btree_search(v.child[i], k)
```

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
* I can represent a graph with a boolean matrix $M$ of dimensions $n^2$ with $n$ being the number of nodes
    * The space requires is $O(n^2)$
* I can use an adjacency list
    * It is formed by a list for each vertex containing all the adjacent vertices to it
    * Space is $\Theta(n+\sum deg(v))=\Theta(n+m)$
* I can use adjacency sets
    * I have a vector for vertices and one for edges
    * The edge vector is just a list of adjacent vertices for each node
    * The node vector contains for each node the number of its adjacent vertices
        * In low-level languages I also need to keep track of the end of the array, so I insert a fake node that starts at end of array + 1
    * I can use the node vector to parse correctly the edge vector
    * The space is $\Theta(n+m)$

### Graph trasversal
* It refers to the problem of visiting all the vertices of a graph

#### Breath-first search (BFS)
* I first explore closer vertices, and then far ones, starting from vertix $s$

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

* The time complexity is $O(n+m)$ in an adjacency list and $O(n^2)$ in an adjacency matrix

#### Depth-first search (DFS)
* I need an adjacency set for each node
* The adjacency set has no particular order
* When I go to a node, I recursively visit the unexplore neighbors of it
* At the end I backtrack to the original node

```python
def DFS(G, u):
    visit(u)
    for v in AdjSet(G, u):
        if not IsVisited(v):
            DFS(G, v)
```
* The time complexity is $O(n+m)$ with an adjacency list and $O(n^2)$ with an adjacency matrix
