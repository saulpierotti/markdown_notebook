% Algorithms and Data Structures
% Saul Pierotti
% \today

---
header-includes:
	\usepackage{algpseudocode}
	\MakeRobust{\Call}
---

# Zeynep Kizyltan module

---

# Math backgroud

## Sums
* Finite sums
$$\sum_{k=1}^{n}a_k  = a_1+a_2+...+a_n$$
* Infinite sums
$$\sum_{k=1}^{\infty}a_k  = a_1+a_2+...$$
* Sums are linear
$$\sum_{k=1}^{n}(ca_k+b_k)  = c\sum_{k=1}^{n}a_k + \sum_{k=1}^{n}b_k$$
* The arithmetic series
$$\sum_{k=1}^{n}k = 1+2+...+n=\frac{n(n+1)}{2}$$
* The quadratic arithmentic series
$$\sum_{k=1}^{n}k^2 = 1+4+...+n^2=\frac{n(n+1)(2n+1)}{6}$$
* The cubic arithmetic series
$$\sum_{k=1}^{n}k^3 = 1+8+...+n^3=\frac{n^2(n+1)^2}{4}$$
* Arithmetic series of any power
$$\sum_{k=1}^n k^p \approx \frac{n^{p+1}}{p+1}$$
* The geometric series
$$\sum_{k=1}^{n}x^k = 1+x+x^2...+x^n=\frac{x^{n+1}-1}{x-1}$$
* Infinite geometric series with base lower than 1
$$\sum_{k=1}^{\infty}x^k = \frac{1}{1-x}$$
$$\sum_{k=1}^{\infty}kx^k = \frac{x}{(1-x)^2}$$
* Logarithmic sum
$$\sum_{k=1}^n \log{k} \approx n \log{n}$$

## Sets
* Logic operations have specific symbols
	* Logic and: $\land$
	* Logic or: $\lor$
	* Logic not: $\lnot$
* A set is a non-ordered and non repetitive collection of elements
* A set is described by listing explicitly all of its elements inside curly braces 
$$S=\{...\}$$
* A member $x$ of the set $S$ is an element that belongs to $S$ ($x \in S$)
* A non-member $y$ of the set $S$ is an element that does not belongs to $S$ ($y \not\in S$)
* 2 sets are equal if they contain the same elements
* The cardinality of a set $S$, represented as $|S|$, is the number of elements that it contains
	* If the cardinality of a set is a natural number, the set is finite, otherwise it is infinite
* 2 sets $A$ and $B$ are equal ($A=B$) if they contain the same elements
* The empty set $E$ is represented as $E=\{\}=\emptyset$ and it respect the condition $|E|=0$
* If $A$ contains all the elements contained in $B$, then $B$ is a subset of $A$
$$(x \in A \implies x \in B \quad \forall \ x\in A) \iff B \subseteq A$$
* If $A$ contains all the elements contained in $B$ but $A$ and $B$ are not equal, then $B$ is a proper subset of $A$
* The universe $U$ is a set including all the possible elements
$$B \subseteq A \ \land \ A\not=B \iff B \subset A$$

## Basic set operations
* Set intersection
$$A \cap B = \{x:x \in A \land x \in B\}$$
* Set union
$$A \cup B = \{x:x \in A \lor x \in B\}$$
* Set difference
$$A-B = \{x:x \in A \land x \not\in B\}$$
* Set complement
$$A' = U-A \text{ where } A \subseteq U$$

## Set laws
* Empty set laws
$$ A \cap \emptyset = \emptyset$$
$$ A \cup \emptyset = A$$
* Idempotency laws
$$ A \cap A = A \cup A = A$$
* Commutative laws
$$ A \cap B = B \cap A$$
$$ A \cup B = B \cup A$$
* Associative laws
$$ A \cap (B \cap C) = (A \cap B) \cap C$$
$$ A \cup (B \cup C) = (A \cup B) \cup C$$
* Distributive laws
$$ A \cap (B \cup C) = (A \cap B) \cup (A \cap C)$$
$$ A \cup (B \cap C) = (A \cup B) \cap (A \cup C)$$
* De Morgan's laws
$$ (A \cap B)'=A' \cup B'$$
$$ (A \cup B)'=A' \cap B'$$
* Two sets are disjoint if their intersection is the empty set

## Other set operations and definitions
* A collection of nonempty sets $S_1, S_2, ..., S_n$ is a partition of the set $S$ if
	* All the sets $S_1, S_2, ..., S_n$ are pairwise disjoint
	$$ S_i \cap S_j = \emptyset \qquad \forall \ i,j = 1,2,...,n \qquad i \not= j$$
	* Their unioun gives S
	$$ \cup_{S_i \in S} \ S_i = S$$
* The power set $P(S)$ is the set of all subset of $S$, including the empty set and $S$ itself
$$|P(S)| = 2^{|S|}$$
* The cartesian product of 2 sets is a set containing all possible pairs of elements
$$ A \times B = \{(a,b): a \in A \land b \in B\}$$
$$ |A \times B| = |A|*|B|$$
* The cartesian product of n sets is a set of n-tuples

## Relations
* A binary relation $R$ on two sets $A$ and $B$ is a subset of their cartesian product
$$R \subseteq A \times B$$
* The relation $(a,b) \in R$ can be written as $a\ R\ b$
	* If I have a relation $a \leq b$ on natural numbers $N$, this means $\{(a,b): a, b \in N \land a \leq b\}$
	* I can also write $a \leq b = (a,b) \in \ \leq$
* A relation $R$ on $n$ sets $A_1, A_2, ..., A_n$ is a subset of $A_1 \times A_2 \times ... \times A_n$
* A relation $R \subseteq A \times A$ is reflexive if each element is in that relation with itself
$$a\ R\ a \quad  \forall\ a \in A$$
	* $=, \leq, \geq$ are reflexive relations in $N$ but $<, >$ are not
* A relation is symmetric if it works both ways
$$ a\ R\ b \implies b\ R\ a \quad \forall\ a,b \in A$$
	* $=$ is a symmetric relation in $N$
* A relation is transitive if 
$$a\ R\ b \land b\ R\ c \implies a\ R\ c \quad \forall \ a,b,c \in A$$
	* $=, \leq, \geq, <, >$ are transitive relations in $N$
* A relation is antisymmetric if symmetry exists only among equal elements
$$a\ R\ b \land b\ R\ a \implies a = b \quad \forall \ a,b \in A$$
	* $\leq$ is an antisymmetric relation in $N$
* A relation that is reflexive, antisymmetric and transitive is said partial order
* A set in which a partial order is defined is called partially ordered set
* A partial order $R$ on the set $A$ is a total order if
$$ \forall\ a,b \in A\qquad a\ R\ b \lor b\ R\ a$$

## Functions
 * A function $f\colon A$, given 2 sets $A$ and $B$ is defined as a subset of their cartesian product such that there is one and only one element of $B$ for each element of $A$ such that their are related by $f$
 $$ f \subseteq A \times B\colon\ \forall\ a \in A\ \exists!\ b \in B\colon\ a,b \in f$$
 	* $A$ is the domain of $f$, $B$ its codomain
 	* We can write $f\colon A \to B$ to represent the function
 	* If $a,b \in f$ we can write $f(a) = b$
 		* $a$ is called argument of $f$ and $b$ is called image of $a$ under $f$
 * 2 functions are equal if they have the same domain and codomain and their image is equal for every argument
 $$ f = g \iff f\colon A \to B, g\colon A \to B \land f(a)=g(a)\quad \forall\ a \in A$$
 * The range of a function $f(A)$ if a function $f\colon A \to B$ is the set of possible values that it can produce as output
 $$f(A) = \{b \in B\colon b=f(a) \land a \in A\}$$
 * It is different from the codomain since it includes only the values that can actually be taken by the function
 	* In $f\colon N \to N\colon f(n)=2n$ $N$ is the codomain but the range is represented by only the even numbers in $N$
* A function is an injection if it maps one-to-one elements in the domain and codomain
$$f\colon A \to B\colon f(a) = f(b) \implies a = b \quad \forall\ a,b \in A$$
* A function is a surjection if its range is equal to its codomain (if for each element in the codomain there is an argument that can produce it)
$$f\colon A \to B\colon \exists\ a\colon f(a) = b\ \forall\ b \in B$$
* A function is a bijection if it is both a surjection and an injection
	* For a bijection the inverse function $f^{-1}$ is defined
	$$f^{-1}(b) = a \iff f(a) = b$$

## Floors and ceilings
* The floor of a number is the greatest integer less than or equal to it
$$ \lfloor x \rfloor $$
* The ceiling of a number is the smallest integer greater than or equal to it
$$ \lceil x \rceil $$
* For all real numbers $x$
$$ x-1 < \lfloor x \rfloor \leq x \leq \lceil x \rceil < x+1$$
* For any integer $n$
$$ \lfloor n/2 \rfloor + \lceil n/2 \rceil = n$$

# Introduction on algorithms
* The word algorithm comes from the name of the persian scientist Muhammad ibn Musa al-Khwaruzmi
	* He lived in Uzbekstan and wrote Algoritmi de numero Indorum, wrongly understood as a latin plural
	* He was also the founder of algebra (from al-jabr, a procedure to solve quadratic equations)
* First algorithms were written by Babylonian in 1600 BC
* Study of algorithms dates to Euclid in 300 BC
* Modern algortihms study started in 1920 and was formalized in 1930 by Turing and Church (matematicians)
* Many algos were discovered recently also by students
* An algorithm is a finite series of steps that solves a problem
* In CS, an algorithm is a well defined computational procedure that takes some inputs, follows a series of steps and eventually produces outputs in order to solve a computational problem
* Algorithms are for humans, while a program is for a computer
* Algorithms are written in pseudocode, which follow specific conventions
* A problem can be solved by many algorithms
* An algorithm can be implemented in many different programs
* Fundamental properties of algorithms
	* Inputs can be 0 or more
	* Outputs are always 1 or more
	* An algorithm should be clearly defined and unanbiguous
	* It should terminate after a finite number of steps
	* All operations described must be basic, meaning that they can be solved exactly and in finite time
* Correct algorithms are necessary to solve computational problems
* Efficient algorithms are necessary to solve computational problems with the available resources
* An algorithm is correct if for every input, it halts with the correct output
* An incorrect algorithm does not halt or halts with incorrect results on at least 1 instance
	* In some cases they are still useful, if I can control their error rate
* The correctness of an algorithm is difficult to prove
	* Showing correctness in one instance is not a guarantee of correctness in every instance
	* I can prove correctness by testing instances only if the possible number of instances is finite
* Published algorithms needs to have a mathematical proof of correctness that shows that, for any given valid input, it halts with an output that is a solution for the problem
* An algorithm without proof is an heuristic procedure that is not guaranteed to be correct

# Introduction on data structures
* A data structure is a way to store and organise data so to facilitate its access and modification
* A data structure is a way to represent and organize data needed to solve a problem
* Algorithm efficiency is affected by the choice of data structures

# Pseudocode
* Pseudocode is a way of representing an algorithm intended for human reading
* It has a syntax similar to that of many popular programming languages
* It provides a compact, semi-formal, high-level description of an algorithm
* In pseudocode I can omit environment-based details that are not essential to the human understanding the algorithm
* Variables are always local to the given procedure, not global
* Reserved words with special meaning are written in **bold**
* **return** trasnfers control back to the point of call and can optionally return a value
* **error** indicates that an error occurred
	* There is no need to specify how the error should be handled, since this is managed by the calling procedure
* Some constructs
\begin{algorithmic}
\Statex
\While{condition}
	\State statement
\EndWhile
\Statex
\For{counter inizialization to/downto condition (by increment)}
	\State statement
\EndFor
\Statex
\If{condition}
	\State statement 1
\ElsIf{condition}
	\State statement 2
\Else
	\State statement 3
\EndIf
\Statex
\Procedure{proc-name}{arguments}
	\State statement
\EndProcedure
\Statex
\end{algorithmic}

* Assignment of the value $j$ to the variable $i$ is represented as $i = j$
* The conditional statement of equivalence is $i == j$
* Comments are written after `//`
* Block structure is represented with indentation
* In our pseudocode we start array counters from 1 instead of 0 since it is easier to understand
* Elements in an array are accessed by placing the index in squared brackets after the name of the array
	* $A[3]$ gives the third element of the array $A$
* A slice of an array is indicated as $A[3...5]$
* There is no colon/semicolon at the end of lines
* Attributes of objects are indicated as `object_name.attribute`
	* The lenght of an array can be indicated as `A.lenght`

# Algorithm design approaches
* Incremental approach: add one element at a time
* Divide and conquer: divide into subproblems, solve them and combine their solutions
	* It is inspired by the political control tactique of making your enemies fight against each other for controlling them
	* The divide step involves dividing the problem in sub-problems of smaller size
	* The conquer step involves solving the sub-problems recursively
		* If the sub-problem is too big I break it into sub-sub-problems (recursive case)
		* If it is small enough I solve it directly (base case)
	* The combine step uses the solutions of the elementary problems to give a solution of the original problem

# Algorithm analysis
* Efficiency is related to the ability of an algorithm to be executed with available resources
* Resources are time and memory
* CPU time is number of instruction divided by number of istructions per unit time
	* It is hardware-dependent
* Running time is the number of primitive operations to be performeda before termination, in proportion to the input size
	* A primitive operation is an arithmetic operation, data movement, comparison, decision (if)
* Generally when referring to the time complexity of an algorithm this is measured in running time, not CPU time
* The algorithm influences time much more than hardware, so we do not focus on hardware
* Time and memory are bounded resources and must be used wisely
* The input size is the number of elements in the input
* A running time $\geq n^2$ is unacceptable for large inputs
* In a while and for loop, the test is always executed once more than the body
* Analysing algorithms is useful for predicting the amount of resources required for running them and for selecting the most efficient one
* We assume that instructions are executed sequentially and that each instructuon is simple and commonly found in real CPU instruction sets
* One instructuion is assumed to require constant time
* The running time of an algorithm is the proportionality between the input size and the number of primitive instructions executed
* Caution note: the test of a loop is always executed once more than the body

## Order of growth
* In running time analyses we can ignore constants, since we are interested in the asymptotic behaviour of the algorithm
* I can focus only on the leading term, since the others are relatively insignificant
* In general I am interested in the limiting behaviour of the algorithm as the input size increases

## Limiting behaviour of functions
* There are different notations to define the behaviour of functions
* The $\Theta$ (theta) notation signifies asymptotic equality
$$ \Theta(g(n))= \{f(n): \exists (c_1, c_2, n_0 > 0)\colon 0 \leq c_1*g(n)\leq f(n) \leq c_2*g(n) \quad \forall \ n \geq n_0\}$$
	* For a function $f(n)$ having a certain $\Theta$ notation there are 2 constant that multiplied for the $\Theta$ function are constantly greater or smaller than $f(n)$ for $n \geq n_0$
	* It provides a tight bound
	* $\Theta(g(n))$ is the set of functions with the same order of growth as $g(n)$
* The $O$ (big-O) notation indicates an upper bound for the asymptotic behaviour
$$ O(g(n))= \{f(n): \exists (c, n_0 > 0)\colon 0 \leq f(n) \leq c*g(n) \quad \forall \ n \geq n_0\}$$
	* The formal definiton is similar to that of $\Theta$, but instead of a tight bound I only search for an upper bound
	* $O(g(n))$ is the set of functions with the same or smaller order of growth as $g(n)$
	* It provides an asymptotic upper bound
* The $\Omega$ (big-Omega) notation indicates a lower bound for the function
$$ \Omega(g(n))= \{f(n): \exists (c, n_0 > 0)\colon 0 \leq c*g(n) \leq f(n) \quad \forall \ n \geq n_0\}$$
	* $\Omega(g(n))$ is the set of functions with the same or larger order of growth as $g(n)$
	* It provides an asymptotic lower bound
* An important theorem: a $\Theta$ bound implies both a lower and upper bound
$$f(n) = \Theta(g(n)) \iff f(n) = O(g(n)) \land f(n) = \Omega(g(n))$$
* The $o$ and $\omega$ (small-O and small-Omega) notation are equivalent to the big-O and big-Omega notations but require a strict inequality ($>, <$) instead of a $\geq, \leq$
	* They define bounds which are not asymptotically tight
* If I say that $f(n) = \Theta(g(n))$ I mean that $f(n) \in \Theta(g(n))$, and in the same way for $O$ and $\Omega$ notation
* When I use one of these notations in an equation, I want to indicate a generic function with that asymptotic behavior
* In general , there is no unique set of constants that satisfies this notations: It is enough to find 1 set of constants that works

### Limiting behaviour of notable functions
* Any positive polynomial is faster than a polylogarithmic function
* The logarithm of a factorial is $\Theta(n\log{n})$
* Factorials are faster than exponentials, but slower than $n^n$!

## Recurrence equations
* A recurrence equation describes a function in terms of its value on a smaller input
termine a tight bound

### Iteration method
* I take as an example the following recurrence equation
$$ T(n) = T(n/2)+c$$
* I expand the recurrence to look at its structure
$$T(n)=T(n/2)+c \implies T(n/2)=T(n/4)+c \implies T(n)=T(n/4)+2c$$
* I imagine to continue this until I get to the base case $T(1)$
* The base case will occur when the argument of the function is $1$
* I am halving the input at each recursion, so at recursion call $k$ the size of the input is $2^k$
* If I start from an original input size $n$, the base case happens when the argument is
$$n/n=n/2^k=1 \implies k=\log{n}$$
* So I can solve for $T(n)$ as
$$T(n)=T(n/2^k)+kc$$
$$T(n)=c\log{n}+T(n/2^{\log{n}})=c\log{n}+T(1)$$
* Therefore the running time is
$$T(n)=\Theta(\log{n})+\Theta(1)=\Theta(\log{n})$$

### Recursion tree method
* I convert the equation into a tree and sum up the cost of each node for each level
* The cost at each level is the cost icurred at that recursion level
* I then sum up the cost for all the levels
* I take as an example the following recurrence equation
$$T(n)=2T(n/2)+n^2$$
* The root has a cost $n^2$
* The first level has a cost
$$2T(n/2)=2(n/2)^2$$
* The second level has a cost
$$4T(n/4)=4(n/4)^2$$
* I see that in general, level at depth $i$ has a cost
$$2^iT(n/2^i)=2^i(n/2^i)^2$$
* I continue to expand until the base case
$$T(n/2^i)=T(1) \implies 2^i=n \implies i=\log_2{n}$$
$$T(n/2^{\log_2{n}})=2^{\log_2{n}}T(n/\log_2{n})^2=2^{\log_2{n}}T(1)^2=2^{\log_2{n}}T(1)$$
* So the total cost will be
$$T(n)=\sum_{i=0}^{\log_2{n}-1}(\frac{n}{2^i})^2+2^{\log_2{n}}T(1)=n^2\sum_{i=0}^{\log_2{n}-1}(\frac{1}{2})^{2i}+O(n) \leq n^2 \sum_{i=0}^\infty (\frac{1}{2})^{2i}+O(n)= O(n^2)$$

# Basic data structures

## Arrays
* An array is a data structure consisting of a group of similar elements accessed by indexing
* They typically have a fixed size that cannot change after their storage has been allocated
* An array provides direct access to data: $A[i]$ contains the element $a_i$
* Every array is created empty by declaring its size, and then it is filled by assginment
* Each location in the array can be accessed and modified in constant time
* Arrays are easy to use and they can implement many more complex data structures
* They are fast for direct access to a defined location
* With arrays their size is fixed and needs to be specified at initialization time
* The reorganization of data in an array is complex and costly
* It is really inflexible for organising data
* However, I cannot implement every possible data structure with arrays


## Trees
* A tree is a set of nodes connected by edges such that there is one and only one way to get  to go from one node to another
* A tree is an acyclic graph
* A forest is a set containing trees
* Any non-empty tree with n nodes has n-1 edges
	* If this is not true, we don't have a tree
* A tree is rooted if one of its nodes is distinguished as root
	* It can be defined recursively such that every non-root node of a rooted tree is itself the root of a subtree
	* The base case of the recursive definition of root is when the subtrees are empty: in this case the current node is a leaf
* Tree terminology is similar to that of ancestry trees: parents, ancestors, , children, descendant, sibilings
	* Among the ancestors of a node it is included the node itself
	* The proper ancestors of a node are its ancenstors minus the node itself
	* All the ancestors of a node form a path from the node to the root
* Nodes can be leaves or internal nodes
	* A leaf is a node whose subtrees are empty
* The depth of a node is the lenght of the path from it it the root (number of edges)
* The height of a node is the lenght of the longest path from it to a leaf
* The height of a tree is the height of its root
* A sub-tree is formed by a node and all of its descendants
* An ordered tree is a rooted tree  in which the children of each node are ordered according to some criterion
* A binary tree is an ordered tree which is empty or consists of a root node and 2 sub-trees wich are themselves binary trees
* A full binary tree is a binary tree in which each node is either a leaf or it has degree exactly 2
* A complete binary tree is a full binary tree in which all leaves have the same depth and all the internal nodes have exactly degree 2

## Heaps
* An heap is a nearly complete binary tree with peculiar properties
* Structural property: all nodes of an heap are binary except for possibly the last level, that is filled always from left to righ
* Heap property: the key of a parent must always be greter that that of its children (except for the root, that has no parent)
$$ Parent(i) \geq i \quad \forall i$$
	* This is a max heap, there are also min heaps where the property is opposite
	* The maximum element of an heap is always the root
* The size of an heap is the number of nodes it contains
* The heigh of an heap of size $n$ is $\lfloor \log{n} \rfloor$
	* I use the floor and not the ceiling since the root has level 0
* We can represent an heap with an array
	* The first element is the root
	* The children of the root are the second and third element
	* The fourth and fifth element are the children of the second, and so on
* The children of node $A[i]$ are nodes $A[2i]$ (left child) and $A[2i+1]$ (right child)
* The parent of $A[i]$ is $A[\lfloor i/2 \rfloor]$
* It always holds that the size of an heap is smaller or equal to the lenght of the array in which it is contained
$$ A.heapsize \leq A.lenght$$
	* It can be smallr if not all the array is used for storing the heap
* Leaves are all the elements in the sub-array $A[(\lfloor n/2 \rfloor+1)...n]$

### Fundamental heap operations
* These operations return fundamental feautures of an heap, like the values stored in the children and parent of the current node
* Returning the maximum of an heap means returning its root value

\begin{algorithmic}
\Statex
\Procedure{LEFT}{$i$}
	\State \Return{$2i$}
\EndProcedure

\Statex
\Procedure{RIGHT}{$i$}
	\State \Return{$2i+1$}
\EndProcedure

\Statex
\Procedure{PARENT}{i}
	\State \Return{$\lfloor i/2 \rfloor$}
\EndProcedure

\Statex
\Procedure{HEAP-MAXIMUM}{$A$}
	\State \Return{$A[1]$}
\EndProcedure
\Statex
\end{algorithmic}

* max-heapify maintains the heap property when new elements are added to it
* I assume that there is always at most 1 heap violation after I add 1 element to the heap
	* I am assuming that the sub-trees rooted in the children are max-heaps
	* Both children can never be bigger that their parent!
* I recursively explore the heap
* If I find a parent that has a smaller key than one of its children, I swap them
* This could generate a new heap violation down the tree
* I continue swapping until no violations are left
* Since an heap has $\log{n}$ levels and I do constant work at each level (there are no loops and at most 1 recursive call), max-heapify has $O(\log{n})$ running time
* Equivalently, I can say that the running time of max-heapify is linear on the height of the heap $h$ (it is $O(h)$)
	* This is because $h=\lfloor \log{n} \rfloor$

\begin{algorithmic}
\Statex
\Procedure{MAX-HEAPIFY}{$A,i$}
	\State $l =$ \Call{LEFT}{$i$}
	\State $r =$ \Call{RIGHT}{$i$}
	\If{$l \leq A.heapsize$ and $A[l] > A[i]$} \Comment{if the heap did not finish}
		\State $largest=l$ \Comment{the left child is larger than the parent}
	\Else
		\State $largest = i$ \Comment{the parent is larger than the child}
	\EndIf
	\If{$r \leq A.heapsize$ and $A[r] > A[largest]$}
		\State $largest=r$ \Comment{the right child is larger than the parent}
	\EndIf
	\If{$largest \not= i$} \Comment{the parent is not largest element}
		\State exchange $A[i]$ with $A[largest]$
		\State \Call{MAX-HEAPIFY}{$A.largest$} \Comment{recursive call on the child who violated the heap-property}
	\EndIf
\EndProcedure
\Statex
\end{algorithmic}

* build-max-heap converts an array $A[1...n]$ to a max-heap of size $n=A.lenght$
* The elements in the sub-array $A[(\lfloor n/2 \rfloor+1)...n]$ are leaves
* I call max-heapify from the last non-leaf node to the root, so to reconstruct the max-heap property
* I am constructive max-heaps in the subtrees by starting at the bottom, and then going up when everithing below the current level is a max-heap

\begin{algorithmic}
\Statex
\Procedure{BUILD-MAX-HEAP}{$A$}
	\State $A.heapsize = A.lenght$
	\For{$i=\lfloor A.lenght/2 \rfloor$ downto 1}
		\State \Call{MAX-HEAPIFY}{$A,i$}
	\EndFor
\EndProcedure
\Statex
\end{algorithmic}

* Since max-heapify has a running time of $O(\log{n})$ and the for loop is executed $O(n)$ times, it holds that the running time of buil-max-heap is $O(n\log{n})$
* This however is not a tight upper bound, we can define it more stringently
* If $i$ is the depth of a level, each levels has $n_i=2^i$ nodes
* An heap rooted at level $i$ has an height of $h_i = h-i$, where $h$ is the height of the complete heap
* The cost of a max-heapify call is $O(h_i)$ at level $i$
	* Its cost is linear to the height of the node on which it is called
* The last level has height $h = i_{max} = \lfloor \log{n} \rfloor$
* Consider also that $h=\log{n}$ and so $2^h=n$
* I can therefore write
$$ T(n) = \sum_{i=0}^h n_i h_i$$
$$ T(n) = \sum_{i=0}^h 2^i (h-i)$$
$$ T(n) = \sum_{i=0}^h 2^i (h-i)\frac{2^h}{2^h}$$
$$ T(n) = 2^h \sum_{i=0}^h \frac{h-i}{2^h-i}$$
$$ T(n) = n \sum_{k=0}^h \frac{k}{2^k} \qquad\text{with } k=h-i$$
$$ T(n) \leq n \sum_{k=0}^\infty \frac{k}{2^k} = \sum_{k=0}^\infty k (\frac{1}{2})^{k} = \frac{1/2}{(1-1/2)^2} = 2$$
$$ T(n) = O(n)$$

## Priority queues
* A priority queue is a data structure from which I can extract elements according to their priority level (key value)
* Application: it can manage job scheduling in a PC with jobs that have different priority
* There are min-priority queues, which always return the lowest key in them, and max-priority queue, that always return the highest key in them
* A max-priority queue can be conveniently implemented with a max-heap
	* A max-heap allows retrieval of the largest element in $O(1)$ with the heap-maximum routine
* A max priority queue supports the following operations
	* Return the element with largest key (heap-maximum, see heap operations)
	* Remove the element with largest key and return it (extract-max-heap)
	* Increase the key of an element (heap-increase-key)
	* Insert a new element (max-heap-insert)
* I can read the maximum element of the priority queue and remove it from the queue with the heap-extract-max procedure
	* I replace the root of the heap with the last element
	* I decrease the size of the heap by 1
	* I call max-heapify on the new root to restore the max-heap property
	* I do all constant time operations except for the max-heapify call, which is $O(\log{n})$

\begin{algorithmic}
\Statex
\Procedure{HEAP-EXTRACT-MAX}{$A$}
	\If{$A.heapsize < 1$} \Comment{the heap is empty, nothing to extract}
		\State \Return error "heap underflow"
	\EndIf
	\State $max=A[1]$
	\State $A[1] = A[A.heapsize]$ \Comment{put the last element as root}
	\State $A.heapsize = A.heapsize-1$
	\State \Call{MAX-HEAPIFY}{$A,1$}
	\State \Return $max$
\EndProcedure
\Statex
\end{algorithmic}

* Increasing the value of an element is useful when I want to update its priority in the queue
	* Note that I can increase priority, not decrease!
* I first increase the value and then check if the new heap respects the max-heap property
* If it does not i traverse the tree from the updated node to the root to find a proper place for it
* It is doing all constant time operations, and a while loop
* The while loop is executed at most once for each level, so the complexity is $O(\log{n})$ on the size of the heap

\begin{algorithmic}
\Statex
\Procedure{HEAP-INCREASE-KEY}{$A,i,key$}
	\If{$key < A[i]$} \Comment{check that the new key is actually bigger than the old one}
		\State \Return error "new key is smaller than current key"
	\EndIf
	\State $A[i] = key$ \Comment{increase the key}
	\While{$i > 1$ and $A[$\Call{PARENT}{$i$}$]<A[i]$} 
	\State \Comment{until I am not at the root and while the max-heap property is not respected at $A[i]$}
		\State exchange $A[i]$ with $A[$\Call{PARENT}{$i$}$]$
		\State $i =$\Call{PARENT}{$i$} \Comment{move up one node}
	\EndWhile
\EndProcedure
\Statex
\end{algorithmic}

* Inserting a new element to a max-heap takes advantage of heap-increase-key
* I insert the new element with a placeholder key of $-\infty$
* I then increase its key to the actual value with heap-increase-key
* max-heap-insert does all constant time operations and a call to heap-increase-key (which is $O(\log{n})$), so the running time is $O(\log{n})$

\begin{algorithmic}
\Statex
\Procedure{MAX-HEAP-INSERT}{$A,key$}
	\State $A.heapsize = A.heapsize + 1$
	\State $A.heapsize = - \infty$
	\State \Call{HEAP-INCREASE-KEY}{$A,A.heapsize,key$}
\EndProcedure
\Statex
\end{algorithmic}

# Sorting
* Sorting is a common computational problem
	* The typical input is a series of numbers
	* The output is a permutation of the input such that $a_i \leq a_{i+1}$
	* A specific input sequence is an instance of the sorting problem
* Sorting is an intermediate step in many tasks in CS
* There are many sorting algorithms
* The input of the sorting problem is a sequence of numbers $<a_1, a_2, ..., a_n>$
* The numbers in the input are also called keys
* The output of the sorting problem is a permutation $a_1', a_2', ..., a_n'$ of the input such that $a_1' \leq a_2 \leq...\leq a_n$
* When there are at least 2 elements that are identical, sorting algorithms can maintain the respective previous order of the elements or not
* Normally, the numbers to be sorted are a key that is paired to other data, forming a record
	* A record is composed of a key and satellite data
	* A sorting algorithm permutes the keys, and then it permutes the satellite data accordingly
* In some applications it can be important that sorting does not alter the ordering of equal keys, especially when satellite data is involved
	* The other data can already be sorted following another criterion and I may need to not alter this
* An algorithm that sorts without altering the order of equal keys is said to perform a stable sort
* A sorting algorithm is said to sort in place if it does not require extra space besides that needed to store the original array
	* It can require additional $O(n)$ space for variables, but it needs a constant amount of them at each given time
	* In practice, it is an algorithm that does not copy the array to be sorted

## Insertion sort
* Intuition: It is like arranging card in order in your hand by picking one at a time and placing it in the right position, by comparing it with all the other cards already in your hand
* I always work on the same array but I put a moving boundary $i$ before which all the elements are sorted
	* The loop invariant is that $A[1...j-1]$ is always sorted
* I start with $j=2$ and I loop on it until $A.lenght$
* The current element at each iteration, called key, is $A[j]$
* I update the moving boundary $i$ to be $j-1$
* I compare the key with all the objects in the sorted portion of the array starting from the end of it $A[i]$, until I find an element smaller than the current one or I reach the start of the array
	* At each loop iteration I move the element $A[i]$ to position $A[i+1]$
	* I decrease $i$ of 1
* When the loop ends (for any of the 2 reasons) I assign the value of the current element $key=A[j]$ to the position $A[i+1]$
	* That position is empty since I shifted all the values in the previous loop

\begin{algorithmic}
\Statex
\Procedure{INSERTION-SORT}{$A$}
	\For{$j = 2$ to $A.lenght$}
		\State $key = A[j]$
		\State $i = j-1$
		\While{$i > 0$ and $A[i] > key$}
		\Comment{Insert $A[j]$ into the sorted sequence $A[1...j-1]$}
			\State $A[i+1] = A[i]$
		\EndWhile
		\State $A[i+1] = key$
	\EndFor
\EndProcedure
\Statex
\end{algorithmic}

* Let's assume that the input has $n$ elements
* The initial **for** test is executed n time, while the body of the **for** is executed n-1 times
	* I am looping on $n-1$ elements, but I do a test more that will return false and exit the procedure!
* The body contains 3 constant operations and the while loop
* The **while** test is executed a variable number of times at each iteration, for n-1 iterations (from $j=2 \to n$)
	* If $t_j$ is the number of times the while loop test is exectuted at each iteration of the **for** loop, then the test in total is executed $\sum_{j=2}^n t_j$ times
* The body of the **while** is executed always once less then the test ($t_j-1$ times for each iteration of the **for** loop)
	* In total it is executed $\sum_{j=2}^n t_j-1$ times
	* There are 2 assignments on the while body
* The total running time is therefore $T(n) = n+3(n-1)+\sum_{j=2}^nt_j+2\sum_{j=2}^n(t_j-1)$
* In the best case, the array is already sorted
	* I never enter the **while** at each iteration of the **for**
	* This means that $t_j=1$, I only do the test
	* The time is linear: $T(n)=n+3(n-1)+(n-1)+2*0=\Theta(n)$
	* Nearly sorted numbers can be sorted fast with insertion sort
* In the worst case the array is in reverse sorted order
	* For each iteration of the for loop, I iterate the while loop on all the elements
	* The time is quadratic ($\Theta(n^2)$)
* Average case analysis is really difficult to do (it is probabilistic), therefore we prefer to focus on the worst case
	* The worst case provides an upper bound for the running time
	* For some algorithms, the worst case occurs frequently
	* The average case can be as bad as the worst case
* For almost sorted sequences the running time of insertion-sort is almost linear: good when this is the case
* For unsorted array I go towards quadratic time: there are better alternatives
* Time is quadratic also in the average case
* Insertion-sort can operate online: it can sort sequences as they arrive
* Typical application: keep a dynamic file sorted when adding elements to it and sorting almost-sorted files

# Merge-sort
* Merge-sort is a divide and conquer algorithm for sorting
	* I divide the input array of $n$ elements in 2 sub-sequences of $n/2$ elements each
	* I sort the sub-sequences recursively
	* When the sub-sequence has just 1 element I am in the base case
	* A sub-sequence of 1 element is always sorted
	* I combine the sub-sequences to produce the sorted sequence
* Idea of the combine step
	* I need to combine 2 sorted sub-sequences
	* The first element of each sub-sequence is the smallest of that sub-sequence
	* I take the respective first elements of the 2 sub-sequences and compare them
	* I select the smallest of the 2 and put it as first element in the output
	* I proceed with what is now the first element of the 2 sub-sequences and repeat
	* When one of the 2 sub-sequences is empty I put in order all the remaining elements of the remaining sub-sequence to the end of the output array
	* The output array is sorted
* Implementation of merging
	* I actually use always only the original array but I maintain 3 indexes to separate diferent zones of it
	* The indexes are $p,q,r$ such that $p\leq q \leq r$ always holds
	* The indexes split the array $A$ into 2 sub-arrays $A[p...q]$ and $A[q+1...r]$
	* I check that I am not in the base case ($p==r$)
		* I sort recursively the 2 sub-arrays by calling again merge-sort 2 times with $(p=p, r=q)$ and $(p=q+1, r=r)$
		* After the 2 recursive calls return I have 2 sorted sub-arrays to merge, $A[p...q]$ and $A[q+1...r]$
		* I copy them to the new arrays $L$ and $R$
		* I add at the end of both $L$ and $R$ an $\infty$, so that always the other sub-sequence will be added when I reach the end of one sequence
		* I compare the first element of $L$ and $R$, and I place the smallest in the first position of the output array $A$
		* I continue with the second smallest and place it in the second position of $A$ and so on
		* When $L$ or $R$ finish, there is the $\infty$ remaining so all the comparison to it will return that the other sub-sequence has a smaller element
		* When both sequence finish I stop the comparison and return control to the calling procedure: now $A[p...r]$ is sorted (for the $p,r$ used in the current recursive call)
	* If I am in the base case I do not do anything: the sub-arrays are sorted
	* The output is one sorted array input array

\begin{algorithmic}
\Statex
\Procedure{MERGE}{$A,p,q,r$}
	\State $n_1 = q - p + 1$ \Comment{lenght of sub-array 1}
	\State $n_2 = r - q$ \Comment{lenght of sub-array 2}
	\State let $L[1...n_1+1]$ and $R[1...n_2+1]$ be new arrays \Comment{I do $+1$ at the end since add $\infty$ at the end}
	\For{$i = 1$ to $n_1$} \Comment{copying $A[p...q]$ to $L$}
		\State $L[i] = A[p+i-1]$
	\EndFor
	\For{$j = 1$ to $n_2$} \Comment{copying $A[q+1...r]$ to $R$}
		\State $R[i] = A[q+j]$
	\EndFor
	\State $L[n_1+1] = \infty$
	\State $R[n_2+1] = \infty$
	\State $i = 1$
	\State $j = 1$
	\For{$k = p$ to $r$} \Comment{go through all positions in both sub-arrays}
		\If{$L[i] \leq R[j]$} \Comment{add an element from $L$ to the output}
			\State $A[k] = L[i]$
			\State $i = i + 1$
		\Else \Comment{add an element from $R$ to the output}
			\State $A[k] = R[j]$
			\State $j = j + 1$
		\EndIf
	\EndFor
\EndProcedure

\Statex
\Procedure{MERGE-SORT}{$A,p,r$}
	\If{$p < r$} \Comment{if false $p==r$ so I am in the base case}
		\State $q = \lfloor(p+r)/2 \rfloor$ \Comment{divide}
		\State \Call{MERGE-SORT}{$A,p,q$} \Comment{conquer sub-array 1}
		\State \Call{MERGE-SORT}{$A,q+1,r$} \Comment{conquer sub-array 2}
		\State \Call{MERGE}{$A,p,q,r$} \Comment{combine}
	\EndIf
\EndProcedure

\Statex
\State \Call{MERGE-SORT}{$A,1,A.lenght$} \Comment{initial call with $p=1,r=A.lenght$}
\Statex
\end{algorithmic}

* Running time of merge-sort
$$ T(n) = 2T(n/2)+T_{merge}(n)+c$$
	* I perform 2 costant time operations at each call
	* I have 2 recursive calls on an input of $n/2$ size
	* I have 1 merge call on an input of size $n$
* Running time of merge
	* I perform 8 constant time operation
	* I have 2 for loops which are executed $n/2$ times each, so together they take $\Theta(n)$ time
	* The last for loop is executed $n$ times
		* It always consists of 3 constant operations plus the initial test
	* The total time is $T_{merge}(n)=2(n/2)+n+c=\Theta(n)$
* The recurrence equation
$$T(n)=\begin{cases}\Theta(1) & \text{if } n=1 \\ 2T(n/2)+n & \text{if } n>1 \end{cases}$$

* It runs always as $\Theta(n\log{n})$, there is not worst or best case
* The advantage of merge-sort is that its running time is guaranteed
	* It is worse than insertion sort in the insertion-sort best case, but better in most cases
* The disadvantage is that it requires extra space and cannot work online
	* Merge-sort cannot work online, since I need the whole input array at the first step
	* It requires a lot of memory to store all the sub-arrays
* Typical application: sort a huge randomly ordered data file
* The complicated part of merge-sort is the combine step
* Merge-sort does not sort in place: it copies the values to other arrays

# Heap-sort
* Heap-sort is another sorting algorithm running in $O(n\log{n})$ (like merge-sort)
* It is able to sort in place and it uses an heap as data structure
* The sub-routines not written here are the ones for general heap operations
* We start from a random array and we make it a max heap by calling build-max-heap on it
* We swap the root of the heap with the last element of the array and decrease the heap-size by 1
	* What was the root is now not part of the heap
* We call max-heapify on the root to rebuild the max-heap property
	* The only heap violation is the root itself, and max-heapify will descend the tree to recover the max-heap property
* I repeat until the the heap has size 1: now the array is sorted

\begin{algorithmic}
\Statex
\Procedure{HEAP-SORT}{$A$}
	\State \Call{BUILD-MAX-HEAP}{$A$}
	\For{$i = A.lenght$ downto $2$}
		\State exchange $A[1]$ with $A[i]$
		\State $A.heapsize = A.heapsize - 1$
		\State \Call{MAX-HEAPIFY}{$A,1$}
	\EndFor
\EndProcedure
\Statex
\end{algorithmic}

* As we saw, build-max-heap is an $O(n)$ operation
* The for loop body is called $n-1$ times
	* It performs 2 constant time operations and a call to max-heapify on input size from $n-1$ down to $2$
* max-heapify is an $O(\log{n})$ operation
* The total running time is therefore  $O(n \log{n})$
* Heap-sort is insensitive to input arrangement: there is no best or worst case
* Compared to mergesort, which has a $\Theta(n\log{n})$, it as the same upper bound but the bound is not tight
	* It is marginally better


## Quick-sort
* Quick-sort is a divide and conquer sorting algorithm with a worst-case running time of $\Theta(n^2)$ and an average case running time of $\Theta(n\log{n})$
* It is one of the most popular sorting algorithms because of its good average performances
* I works by splitting the array on a pivot, and then calling recursively on the sub-arrays at the 2 sides of the pivot (but not including it)
	* Before calling the recursions all the elements to the left of the pivot are smaller than it (or equal), and all the elements at its right are larger
	* This means that the pivot is in its correct final position in the array
	* The base case is when the sub-arrays is just made of 1 element, and so it is sorted
* After I select a pivot and before calling the recursions, I need to swap elements so that the pivot is in the right position
	* I select as a pivot $A[r] = x$
	* I mantain 4 regions in the array
		* $A[r]$ is $x$ itself
		* $A[p...i]$ is smaller or equal to $x$
		* $A[i+1...j-1]$ is greater than $x$
		* $A[j...r-1]$ is unrestricted
	* I start by initializing $A[p...i]$ empty (I assign $i = p-1$)
	* I check elements 1 by 1 from $p$ to $r-1$ (just before the pivot)
	* When I find an element taht belogs to $A[p...i]$ I increase $i$ of 1 to make space for it and I place it there by swapping with the current $A[i]$
	* When I reach $A[r-1]$ the unrestricted region $A[j...r-1]$ disappears
	* As a last thing I swap the pivot from the end of the array to where it belongs ($A[i+1]$)
* The conquer and combine parts are really easy in quick-sort, but divide requires effort
	* Conquer is just a recursive call on the sub-arrays
	* This is sharply different from MERGESORT, where combine is the most demanding part

\begin{algorithmic}
\Statex
\Procedure{QUICK-SORT}{$A,p,r$}
	\If{$p < r$} \Comment{if $p=r$ I am in the base case: sub-array of 1 element}
		\State $q =$ \Call{PARTITION}{$A,p,r$} \Comment{separate on a pivot}
		\State \Call{QUICK-SORT}{$A,p,q-1$} \Comment{call recursively on the 2 sub-arrays at the sides of the pivot}
		\State \Call{QUICK-SORT}{$A,q+1,r$}
	\EndIf
\EndProcedure
\Statex
\Procedure{PARTITION}{$A,p,r$}
	\State $x = A[r]$ \Comment{select the pivot}
	\State $i = p-1$ \Comment{start with $A[p...i]$ empty}
	\For{$j=p$ to $r-1$} \Comment{j takes all the values in the (sub-)array except the last (the pivot)}
		\If{$A[j] \leq x$} \Comment{check if the current element is smaller or equal to the pivot}
			\State $i = i+1$ \Comment{if it is, I can extend the $A[p...i]$ region to make space for it}
			\State exchange $A[i]$ with $A[j]$ \Comment{and I actually place it in $A[p...i]$}
		\EndIf
	\EndFor
	\State exchange $A[i+1]$ with $A[r]$ \Comment{put the pivot where it belongs}
	\State \Return $i+1$ \Comment{I return the index of the pivot to be used by quick-sort for splitting the array}
\EndProcedure
\Statex
\Statex
Initial call $\implies$ \Call{QUICK-SORT}{$A,1,A.lenght$}
\Statex
\end{algorithmic}

* The partitioning procedure performs constant time operations and has a for loop
* The for loop contains constant time operations and it is executed $n-1$ times
* The running time of partition is $\Theta(n)$
* quicksort has a cost of $O(1)$ in the base case while in the recursive case it calls partition ($\Theta(n)$) and it makes 2 recursive calls on an input size which depends on the partitioning used
* I am in the worst case when the partitioning is maximally unbalanced, since the recursion tree will have its maximum height ($n$)
	* In this case one recursive call will be called on $0$ element and one on $n-1$ elements
	* If I am choosing the last elements as a pivot, the worst case occurs when the array is already sorted
	* In the worst case the recurrence equation is
$$ T(n) = T(n-1)+T(0)+\Theta(n) = T(n-1) + \Theta(n)$$
$$ T(n) = \sum_{i=0}^{n-1} n-i = \sum_{k=1}^n k = \Theta(n^2)$$
* The best case occurs when the partitioning is always perfectly balanced
	* In this case the recursive calls are done on input sizes $n/2$ and $n/2-1$
	* At recursion level $i$ I have $2^i$ recursive calls on an input size of $n/2^i$
	* The total cost at each level is $n$ and I have $\log{n}$ levels
	* The recursion equation of the best case is
$$ T(n) = 2T(n/2) + \Theta(n)$$
$$ T(n) = \Theta(n\log{n})$$
* Actually I am in the best case when the split has constant proportionality, even if it is not perfectly balanced
* In the average case I have a randomly ordered array
	* I expect a mix of balanced and unbalanced splits randomly distributed along the recursion tree
	* The average case running time is similar to the best case, $\Theta(n \log{n})$
* The choice of the pivot influences the performances of quick-sort, since it affects the proportionality of the split
	* The solution presented here is to choice always the last element as a pivot
	* Another approach is to pick 3 values from the array and choose their median as a pivot
* The worst case running time of quick-sort is pretty bad and could be caused volountarily by submitting a specific instance
	* This could be a security risk
* To assure that no particular input (i.e. a sorted array) cause the worst-case scenario of quicksort, I can use the randomized version of the algorithm
	* I can either randomize the input or the choice of the pivot
* Also quick-sort sorts is able to sort in place

# Some reflections on comparison-based sorting
* All the algorithms we saw sort by comparing elements
* All of them sort in place with the exception of MERGESORT
* Insertion-sort and merge-sort are stable, while heap-sort and quick-sort are not
* The worst-case running time of insertion-sort and quick-sort is $O(n^2)$
* Heap-sort and merge-sort have a guaranteed running time of $O(n\log{n})$ on every possible instance
* Insertion-sort is linear in the best case
* The lower bound for comparision-based sorting is $\Omega(n \log{n})$ because in the worst case I need to do at least $n\log{n}$ comparisons
	* Any comparison-based sorting alogrithm must be able to sort any possible input of size $n$
	* There are $n!$ possible permutations of an array of size $n$, and the algorthm must be able to sort all of them
	* Every permutation requires a different rearrangement of the array in order to be sorted
	* I can imagine a decision tree with $n!$ leaves, corresponding to all the permutions
	* The height of the decision tree represent the number of single comparisons that the algorithm has to do in the worst case
	* A tree of heigh h has $2^h$ leaves, and so a tree with $n!$ leaves has heigh $\log{n!}$
	* We saw before that $\Theta (n!) = \Theta (n \log{n})$
* Heapsort and Mergesort are asymptotically optimal comparison-based sorting algorithms

# Linear-time sorting
* It is possible to sort in a time lower to $\Theta{n \log{n}}$ if my algorithm is not based on comparisons
* In this case I need to make assumptions about the input elements
* Linear-timesorting algorithms are counting-sort and radix-sort

## Counting sort
* Counting-sort assumes that the input array contains only integers in the range $0...k$
* For each element $x$ into the array, I determine how many elements are equal or smaller than $x$
* I put element $x$ in the correct position in the output array by knowing how many elements are smaller or equal to it
* It uses an input array $A[1...n]$, an output array $B[1...n]$ and a counter array $C[1...k]$
* I first initialize $C[0...k]$ to contain all $0$s
* I go through all the elements in A
	* In each iteration i use A[j] as an index in C, and I increment that position of 1
	* In this way element C[i] contains the number of occurrences of the value i in the array A
* I go through C and I add, starting from the beginning, the value of C[i-1] to C[i]
	* In this way element C[i] contains the number of elements in A that are smaller or equal to i
	* I am converting a counter for i in a cumulative counter
* Finally, I iterate j from the A.lenght downto 1
	* I put in the output array B the element A[j] in the position that is stored in C[A[j]]
		* If there are i elements in A smaller than A[j], then A[j] is put in B[i]
	* I decrease the respective counter in C of 1, so that if I find another element in A with the same key it is put in the previous position of B

\begin{algorithmic}
\Statex
\Procedure{COUNTING-SORT}{$A, B, k$}
	\State let $C[0...k]$ be a new array
	\For{$i = 0$ to $k$} \Comment{I just initialize the counter array $C[0...k]$}
		\State $C[i] = 0$
	\EndFor
	\For{$j = 1$ to $A.length$}
		$C[A[j]] = C[A[j]] + 1$ 
	\EndFor
	\State \Comment{now $C[i]$ contains how many values equal to $i$ are present in the array}
	\For{$i = 1$ to $k$}
		\State $C[i] = C[i] + C[i-1]$
	\EndFor
	\State \Comment{now $C[i]$ contains the number of elements smaller or equal to $i$}
	\For{$j = A.length$ downto $1$} \Comment{from the last index of the array ($A.lenght$) to the first ($1$)}
		\State $B[C[A[j]]] = A[j]$
		\State \Comment{the output array will store the value $A[j]$ in the correct position}
		\State $C[A[j]] = C[A[j]] - 1$
		\State \Comment{update the counter whenre the next element should be placed}
		\State \Comment{this is needed only when there are equal elements}
	\EndFor
\EndProcedure
\Statex
\end{algorithmic}

* The first and third for loops require both time $\Theta(k)$ since they loop through the counter array
* The second and last for loops require both $\Theta(n)$, since they loop through the input array
* The total running time is therefore $\Theta(n+k)$
* In practice, we use counting-sort only when $k = O(n)$, so we can say that its running time is $O(n)$
* The running time is at minimum $\Omega(n)$, and O(n+k)
	* If k = O(n), then COUNTING-SORT runs in $\Theta(n)$
	* Since I use COUNTING-SORT only when k = O(n), in practice the algorithm runs in $\Theta(n)$
* counting-sort is stable since the last of the equal-key elements of the input array is the first of them to be put in the output array (the last for loop runs backwards)
	* This means that it will be put with the highest index, and so as last element in the output array
* The stability of counting-sort is important because the algorithm is frequently used as a subroutine of radix-sort, and radix-sort requires a stable sorting subroutine

## Radix sort
* It consideres the key as a number in base $k$, which has $d$ digits and so occupies $d$ columns
* It looks at $1$ column at a time, starting from the LEAST significant and sorting it with any stable sorting algorithm
	* If I start from the most significant column, I need to recurse for sorting the least significant digits
		* This implementation is called MSD (most significant digit) radix-sort
	* If I start from the least significant digits and I use a stable sort, when I sort the most significant column everithing is correclty sorted
		* This implementation is called LSD (least significant digit) radix-sort
* It requires only a for loop that runs from the lowest order digit (last column) to the highest order digit (column $d$)
	* In each iteration it calls a stable sorting algorithm on the column
	* It takes only $d$ passes on the array each with a running time depending on the sorting subroutine used, with input size $n$

\begin{algorithmic}
\Statex
\Procedure{RADIX-SORT}{$A, d$}
	\For{$i = 1$ to $d$}
		\State use a stable sort to sort $A$ on digit $i$
	\EndFor
\EndProcedure
\Statex
\end{algorithmic}

* radix-sort takes $\Theta(d\ f(n))$ time, where f(n) is the running time of the subroutine used
* If (as it is usually the case) I use counting-sort as a subroutine, it take $\Theta(d\ (n+k))$ time
* In decimal notation $k=9$ since a column can only hold digits in the range $0...9$
* Therefore when the base used is smaller than $n$, radix-sort has complexity $\Theta(n)$
* LSD radix-sort is stable while MSD radix-sort is not stable
* radix-sort usually is implemented not in place, since it uses counting-sort
	* If memory is a problem then quick-sort is a better choice

# Dynamic sets
* Sets are fundamental both for computer science and for maths
* In maths sets are static, but in computer science they are dynamic
	* They can grow or change over time when manipulated by algorithms
* Elementary set operations are insertion, deletion and membership test
* A set supporting all of the elementary operations is called a dictionary
* A priority queue is a set that support the extract-max operation
* Each set elements is identified by a key, and it can have optional features
	* It can have satellite data associated to it
	* It can store a pointer, which points to another element in the set
* Set operations can be queries or modifying operations
* A query always returns a pointer to another element in the set: search, minimum, maximum, successor, predecessor
* A modifying operation modifies the set itself: insert and delete
* Dynamic sets can be represented with different data structures that use pointers: stacks, queues, linked lists, rooted trees

## Stacks
* A stack is a pile of elements on top of each other, deriving its element from an actual stack of plates in a resturant
* A new element is always added to the top of the stack with a push operation
* Elements are also always removed from the top of the stack, with a pop operation
* The popping order is the reverse of the push order: stacks follow a last in first out (LIFO) policy
* Elements cannot be accessed from a stack if they are not at its top
* The top element can be popped (read and removed), or it can be accessed without removing it
* A stack is NOT a good data structure for sorting and it is not used for this purpose
* Some applications of stacks
	* Storing undo history in text editors
	* Synthax parsing: evaluating missing parenteses
		* I push open and close parenthesis to the stack and pop twice when I find matching parenthesis
		* At the end of the file I require the stack to be empty
* A stack of $n$ elements can be implemented with an array $S[1..n]$
* A stack has a $S.top$ attribute that contains the index of the top element of the stack
	* The top element of a stack is usually the last element (index $n$)
	* If the stack is empty $S.top = 0$
* Some basic stack operations

\begin{algorithmic}
\Statex
\Procedure{STACK-EMPTY}{$S$}
	\If{$S.top == 0$}
		\State \Return TRUE
	\Else
		\State \Return FALSE
	\EndIf
\EndProcedure
\Statex
\Procedure{PUSH}{$S,x$}
	\If{$S.top == S.lenght$}
		\State \Return error "stack overflow"
	\EndIf
	\State $S.top = S.top + 1$
	\State $S[S.top] = x$
\EndProcedure
\Statex
\Procedure{POP}{$S$}
	\If{\Call{STACK-EMPTY}{$S$}}
		\State \Return error "stack underflow"
	\Else
		\State $S.top = S.top-1$
		\State \Return $S[S.top+1]$
	\EndIf
\EndProcedure
\Statex
\end{algorithmic}

* All these stack operations run in constant time


## Queues
* A queue is a line of elements that behaves like a line of people in a shop
* In a queue I use a FIFO policy instead of a LIFO policy
* I add elements from the tail of the queue with the enqueue procedure and extract them from its head with the dequeue procedure
* Elements can be always enqueued, but only the element that sat in the queue the longest can be dequeued
* It is not possible to access elements in the middle of the queue
* The element at the head of the queue can be dequeued or also read without removing it
* Queues are used for scheduling processes in operating systems and for reservations for accessing a shared resource
* A queue of $n-1$ elements can be implemented with an array $Q[1...n]$
* Queues are circular, there is no end and beginning for their representaion on the array
	* An empty elements marks where the queue ends and starts
*  The array must be $1$ element longer than the queue because I need an empty element for marking the end of the queue
* $Q.head$ is the index of first element of the queue
* $Q.tail$ is the index of the last element of the queue $+ 1$, it is the index of the spacer that marks the end of the queue
		* $Q[Q.tail]$ is always an empty element!
* The queue spans positions $Q[Q.head...Q.tail-1]$ in circular order
* A queue is empty when $Q.head = Q.tail$
	* A new queue is initialized with $Q.head = Q.tail = 1$
* A queue is full when $Q.head = Q.tail + 1$ (circular case, the queue wraps around the end of the array) or when $Q.head = 1$ and $Q.tail = Q.lenght = n$ (linear case. the queue does not wrap around the end of the array)

\begin{algorithmic}
\Statex
\Procedure{ENQUEUE}{$Q,x$}
	\If{($Q.head == Q.tail+1$) or ($Q.head == 1$ and $Q.tail == Q.lenght$)}
		\State \Return error "queue overflow"
	\EndIf
	\State $Q[Q.tail] = x$ \Comment{$Q[Q.tail]$ is always empty}
	\If{$Q.tail == Q.lenght$} \Comment{in this case I wrap around the end of the array}
		\State $Q.tail = 1$
	\Else
		\State $Q.tail = Q.tail + 1$
	\EndIf
\EndProcedure
\Statex
\Procedure{DEQUEUE}{$Q$}
	\If{$Q.head == Q.tail$}
		\State \Return error "queue underflow"
	\EndIf
	\State $x = Q[Q.head]$
	\If{$Q.head == Q.lenght$} \Comment{in this case I wrap around the end of the array}
		\State $Q.head = 1$
	\Else
		\State $Q.head = Q.head + 1$
	\EndIf
	\State \Return $x$
\EndProcedure
\Statex
\end{algorithmic}

* In queue and dequeue operations, the pointers $Q.head$ and $Q.tail$ always move forward, running behind each other
* When one of them reaches $Q.lenght$, it wraps around the end of the array and becomes $1$
* Enquque and dequeue require both constant time

## Linked lists
* A linked list $L$ is a data structure in which elements are arranged in a linear order
* Differently from arrays, linked lists are dynamically allocated
* The order of elements in a linked list is NOT determined by indeces, but by pointers in each element
* Each element $x$ of a linked list has 2 fundamental attributes
	* $x.key$ is the content of the element itself
	* $x.next$ is a pointer to the next element in the linked list
* $L.head$ is an attribute of the linked list itself that stores a pointer to the first element of the list
* A linked list is empty when $L.head = NIL$
* The last element $x$ of a linked list is the one for which $x.next = NIL$
* Singly-linked lists store just the $x.next$ attrivbute in each element $x$
* Doubly-linked lists store an $x.next$ and a $x.prev$ attribute for each element $x$
	* $x.prev$ stores a pointer to the previous element in the linked list
	* $L.tail$ is an attribute of a doubly linked list that stores a pointer to the last element of the list
* A circular list is a doubly-linked list where
	* $L.tail$ points to the last element of $L$
	* $L.head.prev = L.tail$
	* $L.tail.next = L.head$
* Basic operations on linked lists are: list-search(key), list-insert(element), list-delete(element)
* The following pseudocodes refer to doubly-linked lists

\begin{algorithmic}
\Statex
\Procedure{LIST-SEARCH}{$L,k$}
	\State $x = L.head$
	\While{$x \not= NIL$ and $x.key \not= k$} \Comment{until I find what I want or I  reach the end of the list}
		\State $x = x.next$ \Comment{move forward of 1 element}
	\EndWhile
	\State \Return $x$ \Comment{if I do not find $x$, I return NIL at this point}
\EndProcedure
\Statex
\Procedure{LIST-INSERT}{$L,x$}
	\State $x.next = L.head$
	\If{$L.head \not= NIL$} \Comment{If the list is not empty}
		\State $L.head.prev = x$ \Comment{update the prev pointer of the old head}
	\EndIf
	\State $L.head = x$ \Comment{update the list head}
	\State $x.prev = NIL$
\EndProcedure
\Statex
\Procedure{LIST-DELETE}{$L,x$}
	\If{$x.prev \not= NIL$}
		\State $x.prev.next = x.next$ \Comment{update the pointer of $x.prev$ so to skip $x$}
	\Else
		\State $L.head = x.next$ \Comment{if $x.prev$ is NIL $x$ was the old head of the list, so update it}
	\EndIf
	\If{$x.next \not= NIL$}
		\State $x.next.prev = x.prev$ \Comment{update the pointer of $x.next$ so to skip $x$}
	\EndIf
\EndProcedure
\Statex
\end{algorithmic}

* list-insert and list-delete are both constant time operations in linked lists
* list-search is an $O(n)$ operation in linked lists since in the worst case I need to scan the entire list

## Representing rooted trees with linked lists
* We already saw how to represent a binary rooted tree with arrays
* I can represent them also with linked lists
* In this case each element $x$ of the linked list will contain
	* $x.left$ and $x.right$, pointers to the childrens of $x$
	* $x.p$, a pointer to the parent node of $x$
	* $x.key$ and $x.data$, key and satellite data of $x$
* The tree $T$ will contain $T.root$, a pointer to the root of the tree
* The tree is empty when $T.root = NIL$
* If $x.left = NIL$ and $x.right = NIL$, then $x$ is a leaf
* Note that always holds that $T.root.p = NIL$
* I am not necessarily limited to binary trees with linked lists
* I can have any number of branching factor by just increasing the number of child pointers for each element
	* This works well when I have a fixed branching factor $k$ such that I can allocate pointers $x.child_1, x.child_2, ..., x.child_k$ for each node
	* This approach is wasteful when the branching factor is unbounded since I need to allocate statically the number of children for each node
* I can do it more efficiently by using a linked list also for representing the children
	* Each node $x$ has the usual $x.key$, $x.data$, $x.p$ pointers
	* The $x.left$ pointer points to the leftmost child of $x$
	* The $x.right$ pointer is put to new use: it points to the right sibiling of $x$
	* In this representation if $x.left= NIL$, then $x$ is a leaf
	* If $x.right = NIL$, then $x$ is the rightmost child of $x.p$

## Hash tables
* In many applications I need a dynamic set that supports only the dictionary oerations INSERT, SEARCH and DELETE
* A data structure implementing these operations is called a dictionary
* An direct-address table is a convenient way of implementing a dictionary
	* In an direct-access table under reasonable assumptions, SEARCH and INSERT take $O(1)$, but the worst case SEARCH time is $\Theta(n)$
* An direct-address table is a generalization of an ordinary array
	* It contains $n$ elements in the array, and each element is associated with a unique key $k$
	* The keys are drawn from a reasonably small universe $U = \{0,1,...,m-1\}$
* I can represent the direct-address table with an array $T[0...m-1]$
	* Each position in $T$ is called slot and maps to a key in $U$
	* For each element $x$ with key $k$, $T[k]$ contains $x$ itself or a pointer to it
	* If no elements has key $k$, then $T[k] = NIL$
* All the fundamental operations in direct adress tables have an $O(1)$ running time

\begin{algorithmic}
\Statex
\Procedure{DIRECT-ADDRESS-SEARCH}{$T,k$}
	\State \Return{$T[k]$}
\EndProcedure
\Statex
\Procedure{DIRECT-ADDRESS-INSERT}{$T,x$}
	\State $T[x.key] = x$
\EndProcedure
\Statex
\Procedure{DIRECT-ADDRESS-DELETE}{$T,x$}
	\State $T[x.key] = NIL$
\EndProcedure
\Statex
\end{algorithmic}

* In general $U$ can be very large and the actual number of used keys can be small, so direct-access tables can be unpractical
	* I need to allocate the table with all the possible keys in $U$!
	* I want to be able to allocate a table of lenght equal to the subset $K$ of keys actually used from the universe $U$
* To solve the space usage limitations of of direct-address tables, I can use an hash table
	* An hash table does not use $T[k]$ as a slot for the key $k$, but $T[h(k)]$, where $h$ is an hash function
* An hash function $h$ converts a key $k$ into an index in an hash table $T[0...m-1]$
$$ h:U \to \{0,1,...,m-1\}$$
	* We say that $k$ hashes to the slot $h(k)$
	* We will not study hash functions, but we assume them to be well designed and to output with equal probability to each slot
	* Using a subset of the possible keys reduces the storage requirements
* It can happen that 2 elements hash to the same slot, and I define this event as a collision
	* It is impossible to completely avoid collisions, since $m$ is smaller than the universe $U$ of possible elements
* To solve the collision problem, When I have a collision I create a linked list of the elements hashing at that location
	* In this configuration a slot does not contain a pointer to an element $x$, but to the head of a linked list containing all the elements that hash to that slot
	* This approach is called collision by chaining

\begin{algorithmic}
\Statex
\Procedure{CHAIN-HASH-INSERT}{$T,x$}
	\State insert x at the head of the list $T[h(x.key)]$
\EndProcedure
\Statex
\Procedure{CHAIN-HASH-DELETE}{$T,x$}
	\State delete x from the list $T[h(x.key)]$
\EndProcedure
\Statex
\end{algorithmic}

* Insertion in a chained hash table takes $O(1)$ in the worst case
* Deletion takes $O(1)$ if the the lists are doubly linked, and takes the time needed for searching if singly linked
	* If the lists are single-linked, I need to find its predecessor in order to update the pointers in the list, but I do not have a pointer to it!
	* No search is needed to find the element to delete, since I am given a pointer to it
* In the average case hashing with chaining has performances that depend on how well the hash function distributes the $n$ keys among the $m$ slots
* The load factor $\alpha$ of an hash table is the number of elements in the table $n$ divided by the number of slots $m$
$$\alpha = n/m$$
	* This is true if I assume that every slot has the same probability to be hashed by an element (simple uniform hashing assumption)
	* $\alpha$ can be 1, bigger than 1 or smaller than 1
* An unsucessfull search in a chained hash table takes expected time $\Theta(1+\alpha)$ under simple uniform hashing
	* An unsuccessfull search is the worst case search for a chained hash table
	* In an unsuccessfull search I need to go through the all list, which has expected lenght $\alpha$
	* If choose $m$ to be proportional to $n$ I have that $m=O(n)$
	* In this case $\alpha=O(1)$ since $O(n)/O(n)=O(1)$ and therefore an unsuccessfull search has a $O(1)$ running time
* The size of the hash table influences the speed in operating with it
	* If it has only 1 element essentially I don't have an hash table but a linked list
	* If it is too big it requires a lot of space
	* Typically the right size is 1/5 to 1/10 of the number of elements to be stored in it
* I can keep the lists in an hash table ordered or not
	* If the lists are not ordered inserting is faster and I can implement a LIFO behaviour
	* If they are ordered seaching is faster

## Binary search trees (BST)
* A BST supports many dynamic set operations: SEARCH, MINIMUM, MAXIMUM, PREDECESSOR, SUCCESSOR, INSERT, DELETE
	* It can be used both as a dictionary and as a priority queue
* On average all operations take $\Theta(log n)$, with a worst case $\Theta(n)$
	* The expected height of the tree is $\Theta(\log n)$, while its biggest possible height is $\Theta(n)$ when the tree is actually alinear chain of elements
* A BST is represented as a linked data structure in which each node stores an object and several pointers
	* It has a key field, a ponter to the parent node, and pointers ti the right and left children of the node
* Binary search trees respect the binary search tree property
	* The key of all the elements in the left subtree of node $x$ are smaller or equal to $x.key$
	* The key of all the elements in the right subtree of node $x$ are bigger or equal to $x.key$
* Traversing a BST can be done with different tree walks
* The inorder tree walk visits the keys of the BST in sorted order: each key is printed after the key of its left child and before the one of its right child
	* The order is therefore: $left \to root \to right$
* The preorder tree walk prints first the key of the current node and than the one of its right and lef children in this order
	* The order is therefore: $root \to left \to right$
* The postorder tree walk prints first the children and then the parent
	* The order is therefore: $left \to right \to root$
* Tree walks visit all the $n$ nodes of the tree so they have always $\Theta(n)$ time complexity
* The initial calls of tree walks are with $x$ equal to a pointer to the root of the tree

\begin{algorithmic}
\Statex
\Procedure{INORDER-TREE-WALK}{$x$}
	\If{$x \not= NIL$}
		\State \Call{INORDER-TREE-WALK}{$x.left$}
		\State print $x.key$
		\State \Call{INORDER-TREE-WALK}{$x.right$}
	\EndIf
\EndProcedure
\Statex
\Procedure{PREORDER-TREE-WALK}{$x$}
	\If{$x \not= NIL$}
		\State print $x.key$
		\State \Call{PREORDER-TREE-WALK}{$x.left$}
		\State \Call{PREORDER-TREE-WALK}{$x.right$}
	\EndIf
\EndProcedure
\Statex
\Procedure{POSTORDER-TREE-WALK}{$x$}
	\If{$x \not= NIL$}
		\State \Call{POSTORDER-TREE-WALK}{$x.left$}
		\State \Call{POSTORDER-TREE-WALK}{$x.right$}
		\State print $x.key$
	\EndIf
\EndProcedure
\Statex
\end{algorithmic}

* Searching for a key $k$ in a BST means returning a pointer to the node whose key is $k$ if it exists, NIL otherwise
	* The input of TREE-SEARCH are the root of the tree and the key to be found
	* I start from the root and compare the key of current node $x.key$ with the one to be found $k$
	* If the keys are equal, I return the current node
	* If $k < x.key$ I call recursively TREE-SEARCH on $x.left$
	* If $k > x.key$ I call recursively TREE-SEARCH on $x.right$
	* If the function is called on NIL (I reached a leaf and call the function on one of its non-existen children), I return NIL
* The running time of TREE-SEARCH is $O(h)$, where $h$ is the height of the tree (which is $O(\log n)$)

\begin{algorithmic}
\Statex
\Procedure{TREE-SEARCH}{$x,k$}
	\If{$x == NIL$ or $k == x.key$}
		\State \Return $x$
	\EndIf
	\If{$k < x.key$}
		\State \Return \Call{TREE-SEARCH}{$x.left, k$}
	\Else
		\State \Return \Call{TREE-SEARCH}{$x.right, k$}
	\EndIf
\EndProcedure
\Statex
\end{algorithmic}

* The search function can be equivalently performed also iteratively instead tan with recursion

\begin{algorithmic}
\Statex
\Procedure{ITERATIVE-TREE-SEARCH}{$x,k$}
	\While{$x \not= NIL$ and $k \not= x.key$}
		\If{$k < x.key$}
			\State $x = x.left$
		\Else
			\State $x = x.right$
		\EndIf
	\EndWhile
	\State \Return $x$
\EndProcedure
\Statex
\end{algorithmic}

* Finding the minimum or maximum key in a BST is easy: always go left or always go right (respectively) until you reach a leaf
	* The running time is $O(h)$, which in the average case equals $O(\log n)$

\begin{algorithmic}
\Statex
\Procedure{TREE-MINIMUM}{$x$}
	\While{$x.left \not= NIL$}
		\State $x = x.left$
	\EndWhile
	\State \Return $x$
\EndProcedure
\Statex
\Procedure{TREE-MAXIMUM}{$x$}
	\While{$x.right \not= NIL$}
		\State $x = x.right$
	\EndWhile
	\State \Return $x$
\EndProcedure
\Statex
\end{algorithmic}

* If all keys are distinct, the successor of the node $x$ is defined as the node $y = successor(x)$ such that $y.key$ is the smallest key bigger or equal to $x.key$
	* The successor is the node with key just bigger (or equal) to that of $x$
	* If $x$ has a right subtree, the successor of $x$ is the smallest key of $x.right$
	* If it has not, I need to go up the tree until I find a node that is the left child of its parent
		* If such a node exists, the successor of $x$ is the parent of that node
	* If $x$ is the biggest element of the tree I return NIL: there is no successor
* Similarly, the predecessor of a node is defined as the node with key which is the largest among the ones smaller than the key of that node
* Successor and predecessor require both $O(h)$ time, since they at most pass once for each level of the tree

\begin{algorithmic}
\Statex
\Procedure{TREE-SUCCESSOR}{$x$}
	\If{$x.right \not= NIL$}
		\State \Return \Call{TREE-MINIMUM}{$x.right$}
	\EndIf
	\State $y = x.p$
	\While{$y \not= NIL$ and $x == y.right$}
		\State $x = y$
		\State $y = y.p$
	\EndWhile
	\State \Return $y$
\EndProcedure
\Statex
\Procedure{TREE-PREDECESSOR}{$x$}
	\If{$x.left \not= NIL$}
		\State \Return \Call{TREE-MAXIMUM}{$x.left$}
	\EndIf
	\State $y = x.p$
	\While{$y \not= NIL$ and $x == y.left$}
		\State $x = y$
		\State $y = y.p$
	\EndWhile
	\State \Return $y$
\EndProcedure
\Statex
\end{algorithmic}

* Insertion in a BST happens always on the leaves
	* I want to insert a node $z$ with key $z.key = v$ into a BST $T$
	* I start from the root and maintain 2 pointers
		* $x$ is the current node
		* $y$ is the parent of $x$ (called trailing pointer)
	* If $x.key < v$ I move to $x.right$, else I move to $x.left$
	* When $x == NIL$ we are at the correct position
		* At this point either $y$ is a leaf or it is a node with only 1 child
		* If $v$ is smaller than $y.key$, then I insert $z$ as $y.left$, else I insert it as $y.right$
* The running time for insertion is also $O(h)$ since I go from the root to a leaf

\begin{algorithmic}
\Statex
\Procedure{TREE-INSERT}{$T,z$}
	\State $y = NIL$
	\State $x = T.root$
	\While{$x \not= NIL$}
		\State $y = x$
		\If{$z.key < x.key$}
			\State $x = x.left$
		\Else
			\State $x = x.right$
		\EndIf
	\EndWhile
	\State $z.p = y$
	\If{$y == NIL$}
		\State {$T.root = z$} \Comment{Tree $T$ was empty}
	\ElsIf{$z.key < y.key$}
		\State $y.left = z$
	\Else
		\State $y.right = z$
	\EndIf
\EndProcedure
\Statex
\end{algorithmic}

* Deletion of a node $z$ from a BST $T$ is more complicated than insertion
	* $z$ can be a leaf, have one child, or have 2 children
	* If $z$ has no children I just make $z.p$ point to $NIL$ instead of to $z$
	* If $z$ has 1 child I set the pointer of $z.p$ to the child of $z$ instead of to $z$ itself
		* I also need to update the parent pointer of $z$'s child
	* If $z$ has 2 children it is more complicated
		* $successor(z) = y$ is the minimum element in $z$'s right subtree
			* Since $z$ has 2 children it cannot be otherwise
		* $y$ cannot have a left child since there cannot be elements smaller than $y$ in that subtree by definition
			* Either $y$ has no children or it has only a right child
		* I delete $y$ from the tree as seen for the cases above and replace $z$ with $y$
			* $y$ will be in the right position when placed in where $z$ was, since it is its successor
* To make the code for delete easier to read I define a function called TRANSPLANT
	* It replaces the subtree rooted at $u$ with the one rooted at $v$
* The TREE-DELETE operation also runs in $O(h)$

\begin{algorithmic}
\Statex
\Procedure{TRANSPLANT}{$T,u,v$}
	\If{$u.p == NIL$}
		\State {$T.root = v$}
	\ElsIf{$u == u.p.left$}
		\State $u.p.left = v$
	\Else
		\State $u.p.right = v$
	\EndIf
	\If{$v \not= NIL$}
		\State $v.p = u.p$
	\EndIf
\EndProcedure
\Statex
\Procedure{TREE-DELETE}{$T,z$}
	\If{$z.left == NIL$}
		\State \Call{TRANSPLANT}{$T,z,z.right$} \Comment{$z$ has no left child}
	\ElsIf{$z.right == NIL$}
		\State \Call{TRANSPLANT}{$T,z,z.left$} \Comment{$z$ has only a left child}
	\Else \Comment{$z$ has 2 children}
		\State $y =$ \Call{TREE-MINIMUM}{$z.right$} \Comment{$y$ is $z$ successor}
		\If{$y.p \not= z$} \Comment{$y$ is not the root of $z$'s right subtree, but lies in it}
			\State \Call{TRANSPLANT}{$T,y,y.right$}
			\State $y.right = z.right$ \Comment{replace $z$ by $y$}
		\EndIf
		\State \Call{TRANSPLANT}{$T,z,y$}
		\State $y.left = z.left$
		\State $y.left.p = y$
	\EndIf
\EndProcedure
\Statex
\end{algorithmic}

* All the operations in binary search trees are $O(h)$
* This means that they are fast when the tree is not too deep

# Ivan Lanese module

---

## Introduction
* Most algorithms on trees and graphs are recursive
* Algorithm efficiency is extremely important when the input size is large

## Balanced search trees
* A balanced tree is a special kind of bynary search tree (BST)
	* A BST must maintain the BST property during updates
	* The BST property is useful during lookups
* Insertions and deletions in a BST respect the BST property but they can alter the height of the tree
	* I can obtain a tree in which $h = O(n)$ with a sequence of n insertions by adding element with always increasing (or always decreasing) keys
* A tree built from ordered elements is maximally unbalanced
	* A way to create a generally balanced tree is to randomly permutate the input data when constructing the tree
* Modifications of BST have been developped for maintaining it as balanced as possible
* Since most BST operation have a complexity of $O(h)$, it is important to minimize the height of the tree
* There are variants of BSTs that aim at keeping the tree as balanced as possible, like red-black trees and AVL trees

### AVL trees
* An AVL (Adelson-Velskii and Landis) tree is a BST which is almost balanced
	* It was published by russian scientists in 1962
* It supports INSERT, DELETE, and LOOKUP operations in $O(\log n)$ in the worst case
* For each node $v$, an AVL tree evaluates the balancing factor $\beta(v)$ as the difference in height between the left and right subtrees of $v$
$$ \beta(v) = height(v.left) - height(v.right)$$
* A tree is said to be balanced in height if the absolute value of the load factor of each of its nodes is at most 1
$$ T \mbox{ is balanced} \iff |\beta(v)| \leq 1 \ \forall \ v$$
* An AVL tree is a BST which is balanced in height
* The height of an AVL tree is always logarithmic with respect to the number of nodes
$$ height(AVL) = O(\log n)$$
	* The most unbalanced AVL tree possible is a Fibonacci tree
		* It is a tree in which the heights of the left and right subtrees of the root are the Fibonacci trees of order (height) $n_{h-1}$ and $n_{h-2}$
		* The number of nodes in the Fibonacci tree of height $h$ is
$$ n_h = n_{h-1} + n_{h-2} +1$$
	* I want to prove now that a Fibonacci tree of heigh $h$ has $F_{h+3}-1$ nodes with $F_n$ being the $n^{th}$ Fibonacci number
$$ n_h = F_{h+3} -1$$
	* In the base case I have a Fibonacci tree where $h=0$
	* In this case I have 1 node and it satisfies the stated condition
$$n_0 = 1, F_3 = 2 \implies n_0 = F_{0+3} - 1$$
	* Induction: $n_h = n_{h-1} + n_{h-2} + 1$ by construction
$$n_h = n_{h-1} + n_{h-2} + 1=F_{h+2}-1+F_{h+1}-1+1=F_{h+3}-1$$
	* Therefore, any Fibonacci tree has $F_{h+3} -1$ nodes
	* Since it is known that
$$F_h = \Theta(\phi^h) \qquad, \phi \approx 1.618$$
	* Therefore
$$n_h = \Theta(\phi^h)$$
	* So I can conlude that
$$\Theta(\log{n_h}) = \Theta(h)$$
$$h=\Theta(\log{n_h})$$
	* Since the height of the most unbalanced possible AVL tree is $\Theta(\log{n})$, the heigh of an AVL tree is $O(\log n)$
* Operations in AVL trees are similar to those in BSTs
	* SEARCH is the same as in a generic BST, since it does not modify the AVL property
	* INSERT and DELETE have to be modified so to maintain the AVL property
	* The balancing factor is stored in each node and it is updated during INSERT and DELETE operations
* The AVL property is maintained through an operation called rotation
	* A tree rotation does not alter the horizontal arrangement of nodes but only the vertical arrangement
	* It is a transformation of the tree that preserves the BST property and restores (sometimes in more than 1 passage) the AVL property
	* It decreases by 1 the heigh of a subtree and increases by one the height of another subtree
	* It is a movent described always by 3 nodes that pulls them like a string around one of the nodes, which is called pivot
	* A rotation can be done to the right or to the left, depending on the fact that we pull from the righmost or leftmost node
	* If the left child of the pivot has a right child, this becomes the left child of the pivot itself after the rotation in a right rotation, and symmetrically in a left rotation
* Unbalances in an AVL 3 can be of 4 types, which are symmetric in pairs: LL, RR, LR, RL
	* An LL unbalance derives from adding a leaf to the left of the left child of a node, and it is symmetric to an RR unbalance
	* An LR unbalance derives from adding a leaf to the left of the right child of a node, and it is symmetric to an RL unbalance
* Which rotation on sequence of rotations must be applied to an AVL tree after insertions and deletions depends on the kind of inbalance
	* An LL (or RR) unbalance requires only 1 rotation, which is called LL (or RR) rotation
		* An LL rotation is a single right rotation on the unbalanced node, an RR rotation a single left rotation onto it
	* An LR (or RL) unbalance requires 2 rotations in sequence, on different pivots
		* I first do a left rotation on the left child of the unbalanced node: this brings me to the LL case
		* I then do the LL rotation to restore the AVL property: a right rotation on the unbalanced node
* Insertion in AVL tree is similar to the normal BST insertion, but it also recalculates all the balancing factors that changed and performs the required rotations
	* The balancing factor can change in at most one node per level on the path from the inserted node to the root
	* The recalculation of the balancing factor is therefore done on each node in the path from the new node to the root, with a $O(\log n)$ time complexity
	* If at least one node is critical ($|\beta| > 1$), I need to rebalance the tree with rotations
	* The overall cost of insertion in AVL trees is $O(\log n)$
* Deletion in AVL trees is similar to the standard BST deletion, but it is also needed to recalculate the balancing factors that possibly changed and to perform the required rotations
	* Similarly to insertion, the balancing factor needs to be recalculated in at most $O(\log n)$ nodes, in the path from the deleted node to the root
	* Critical nodes must be rebalanced with rotations, and rebalancing is performed from the bottom to the top
	* The overall cost of deletion is $O(\log n)$
* Search in an AVL tree is also an $O(\log n)$ operation in the worst case

## Data structures for working on disk
* Large data structures cannot be kept always in memory but instead need to be partially loaded in memory from disk, as needed
* Computational time in these cases is heavily dependent on the number of read/write operations, since disk is typically MUCH slower than memory
* Some data structures were developped so to minimize disk access operations

### 2-3 trees
* 2-3 trees are a data structure developped for minimizing disk access
* It is a tree in which all the internal nodes have 2 or 3 children and all the leaves are at the same depth (the path from the root to each of the leaves has constant lenght)
	* The leaves contain keys and satellite data, and they are sorted in ascending key order from left to right
	* Each internal node $v$ maintains up to 2 pieces of information
		* $v.L$ is the maximum key contained in the subtree rooted in the left child of $v$
		* Only if $v$ has 3 children, $v.M$ is the maximum key contained in the subtree rooted in the central child of $v$
* In 2-3 trees internal nodes are small and they can be easily kept in memory and read/written to disk in a single block, while leaves are large since they stire the satellite data
	* Leaves are typically left on disk and read when needed, while the internal nodes are kept in memory
* The height of a 2-3 tree is $\Theta(\log n)$
	* Let $T$ be a tree with $n$ nodes, $f$ leaves and height $h$
	* The following inequalities hold
$$2^h \leq f \leq 3^h$$
$$2^{h+1}-1 \leq n \leq \frac{3^{h+1}-1}{2}$$
	* If $h=0$ the number of leaves is $f=1$, and so $2^h \leq f \leq 3^h$ holds
	* If $h>0$ let's consider the tree $T'$ equal to $T$ but without the last level
	* $n'$ and $f'$ are respectively the number of nodes and leaves in $T'$ 
	* Every leaf in $T'$ can have either 2 or 3 children in $T$, so assuming that $2^{h-1} \leq f' \leq 3^{h-1}$ I observe that
$$2*2^{h-1} \leq f \leq 3*3^{h-1} \implies 2^h \leq f \leq 3^h$$
	* For the second inequality, when $h=0$ the number of nodes in the tree is $n=1$ and so $2^{h+1}-1 \leq n \leq \frac{3^{h+1}-1}{2}$ holds
	* If $h>0$ I do the inductive assumption that (resuming the tree $T'$ used before) $2^h-1 \leq n' \leq \frac{3^h-1}{2}$
	* I observe that $n = n'+f$ and $f'$ is under the previously computed bound $2^h \leq f \leq 3^h$

$$ (2^h-1)+(2^h) \leq n'+f \leq (\frac{3^h-1}{2})+(3^h)$$
$$ 2^{h+1}-1 \leq n \leq (\frac{3^{h+1}-1}{2})$$

* Search in a 2-3 tree is performed as follows, by calling initially 23-SEARCH on the root of the tree

\begin{algorithmic}
\Statex
\Procedure{23-SEARCH}{$v,k$}
	\If{$v == NIL$}
		\State \Return $NIL$
	\ElsIf{$v$ is a leaf}
		\If{$v.key == k$}
			\State \Return $v$
		\Else
			\State \Return NIL
		\EndIf
	\Else
		\If{$k \leq v.L$}
			\State \Return \Call{23-SEARCH}{$v.left, k$}
		\ElsIf{$v.right \not= NIL$ and $k > v.M$}
			\State \Return \Call{23-SEARCH}{$v.right, k$}
		\Else
			\State \Return \Call{23-SEARCH}{$v.mid, k$}
		\EndIf
	\EndIf
\EndProcedure
\Statex
\end{algorithmic}

* Insertion of a key $k$ in a 2-3 tree procedes as follows
	* I create a leaf $v$ with key $k$
	* I use 23-SERACH to find a node $u$ on the penultimate level that will become the father of $v$
	* If $u$ has not 3 children, I add $v$ to it at the appropriate position
	* If $u$ has 3 children already, I perform a splitting operation, that can also propagate back until the root
	* It takes $O(\log n)$ to find the father of the new node and $O(1)$ to do the each split
	* In the worst case I need to do $O(\log n)$ splits on the path from $u$ back until the root
	* The overall insertion cost is $O(\log{n})$
* Deletion of a leaf $v$ with key $k$ in a 2-3 tree procedes as follows
	* I remove $v$ by detaching it from its father $u$
	* If $u$ had 2 children it will remain with just 1 child, violating the 2-3 property: in this case I need to merge $u$ with a neighbor
	* The merging operations could propagate back until the root
	* Also deletion has an $O(\log n)$ cost

### B trees
* B trees are similar to 2-3 trees but used for even larger amounts of data, when also the keys themselves are too many to be kept in memory
* They are typically used to manage large sets of ordered keys
* A variant of B trees, called B+ trees, are an exact generalization of 2-3 trees and they are used in many filesystems and relational databases
* Differently from 2-3 trees, B trees store keys and also satellite data in the internal nodes
	* B+ trees store satellite data only on the leaves
* Each node in a B tree can have a large number of children 
	* They have a huge branching factor, they can have thousands of children per node
	* Thanks to the high branching factor, B trees can index vast amounts of data on disk, thus reducing the number of I/O operations
* B-trees are used for indexing large, slow storage disks
* In general I cannot read a single byte from a disk, data is read in sectors
	* Also SSDs have a minimal access unit, the block
* A constant number of sectors is kept in memory at any given time for a B tree, regardless of its size
* The grade $t \geq 2$ of a B tree is the minimum number of children that each node different from the root can have
	* We select the grade so that each node can be as large as possible but fit in a single sector on the disk
	* The grade is constant for the whole tree
	* The root has from 1 to $2t-1$ children
* A B tree with grade $t$ has the following properties
	* All the leaves have the same depth
	* Every node $v$ different from the root maintains $v.n$ ordered keys with $t-1 \leq v.n \leq 2t-1$
		* These are $v.key_1, v.key_2,...,v.key_{v.n}$
	* The root has at least 1 and at most $2t-1$ children
	* Every internal node $v$ has $v.n+1$ children
	* The keys $v.key$ split the intervals of keys stored in every subtree
		* The keys stored in the first subtree are smaller than the first key of the node, the ones in the second subtree are between the first and the second key, and so on
* In general the branching factor of a B tree is choosen so that a single node occupies a whole disk block and can be read/written to disk in a single operation
	* Typical branching factors are between 50 and 2000
	* The number of I/O operations is $O(h)$, since in general I perform one operation per node
* The heigh of a B-tree with $n$ keys is
$$h \leq \log_t \frac{n+1}{2}$$
	* Given a B tree of grade $t$, the higest possible tree is the one with fewer children per node
	* A B tree of grade $t$ as a minimum of $t$ children per node, by definition
	* The smallest B tree of grade $t$ has exactly $t$ children per internal node and 1 on the root
	* A tree with 1 node has depth 0
	* A tree of 2 nodes has depth 1
	* A tree of $2t$ nodes has depth 2
	* A tree of $2t^2$ nodes has depth 3
	* A tree of $2t^{i-1}$ nodes has depth $i$
	* The minimum total number of nodes in a B tree of height $h$ is therefore
$$ 1+\sum_{i=1}^h 2t^{i-1}$$
	* All the internal nodes (except the root) contain exactly $t-1$ keys
	* The total number of keys $n$ satisfies
$$ n \geq 1+(t-1) \sum_{i=1}^h2t^{i-1} = 1+2(t-1) \frac{t^h-1}{t-1} = 2t^h-1$$
	* This is because
$$\sum_{i=1}^h t^{i-1} = \sum_{i=0}^{h-1} t^i = \frac{t^h-1}{t-1}$$
	* Now, since $n \geq 2t^h-1$ we get that
$$ t^h \leq \frac{n+1}{2}$$
$$ h \leq \log_t \frac{n+1}{2}$$
* In the following pseudocodes I am assuming that the root is always in memory, and unused blocks are discarded from memory automatically
* The operations DISK-READ and DISK-WRITE are used to retrieve and write data from disk
* The search operation of the key $k$ in a B tree is a generalization of the BST search
	* At each recursion I search for $k$ in the current node
	* If I find $k$ I stop
	* If $k$ is not contained in the node I descend into the appropriate subtree of the current node
	* The number of visited nodes is $O(\log_t n)$
	* Each visit costs $O(t)$ since I need to scan all the keys in the node
	* The total cost of BTREE-SEARCH is $O(t log_t n)$
	* Note that the keys on any given node are sorted: I can do a binary search instead of a linear search to identify the right one
		* Binary search takes $O(\log n)$
		* In this case the total complexity will be $O(\log t \log_t n)=O(\log n)$ (using the change of base formula)
	* I search the leaf $f$ in which I can insert the key $k$
	* If the leaf is not full (less than 2t-1 keys) I insert $k$ in the correct position
	* If it is full I split the leaf $f$
		* I put the key number $t$ of $f$ to $f.parent$
			* If $f.p$ is full I need to split it and recurse
			* In the worst case this will split the root and generate a new one
	* I cannot use binary search in this case since I cannot split an array in that way, I need to copy half of its elements in $O(t)$
	* Total cost is $O(t \log_t{n})$

\begin{algorithmic}
\Statex
\Procedure{BTREE-SEARCH}{$v,k$}
	\State $i = 1$
	\While{$i \leq v.n$ and $k > v.kei_i$}: \Comment{if I reach the end of $v.key_i$ without finding $k$, $i = v.n + 1$}
		\State $i = i + 1$
	\EndWhile
	\If{$i \leq v.n$ and $k==v.key_i$}
	\State \Comment{if $i = v.n+1$ ($k$ is bigger than all the $v.key_i$) the second statement is not evaluated}
		\State \Return $(v,i)$
	\ElsIf{$v$ is a leaf} \Comment{I reached the bottom of the tree without finding $k$}
		\State \Return $NIL$
	\Else
		\State \Call{DISK-READ}{$v.child_i$}
		\State \Return \Call{BTREE-SEARCH}{$v.child_i, k$}
	\EndIf
\EndProcedure
\end{algorithmic}

* Insertion in B trees happens always in the leaves
	* I search for the leaf $f$ in which to insert the key $k$
	* If the selected leaf is not full (it has less than $2t-1$ keys) I insert $k$ into it
	* If the leaf has already $2t-1$ keys I need to split the nodes
		* The leaf $f$ is split into 2 and the key number $t$ is moved to the father of $f$
		* If also the father is full, the split backpropagates, possibly until the root
		* In the worst case the split propagates to the root, which is also full and needs to be split, generating a new root
	* In total I am visiting $O(\log_t n)$ nodes in the worst case
	* Each visit has a cost of $O(t)$ because of the split operations
	* The total cost of B tree insertion is $O(t \log_t n)$
	* To minimize disk access, I actually split all the full nodes (nodes with $2t-1$ children) in the path to the leaf, regardless to the fact that it is needed or not
		* This allows to perform the insertion with a single pass down the tree
		* In this way, every time that I need to split a node, I am sure that its parent cannot be full
	* The only way for a B tree to increase in height is through a split of its root
* Deletion in a B tree is different depending if the key $k$ to be deleted is in an internal node or in a leaf
	* If $k$ is in a leaf $v$
		* If the leaf has more than $t-$ keys, I just remove $k$
		* If the leaf has exactly $t-1$ keys there are 2 cases according on the adjacent brothers of $v$
			* If at least 1 of the adjacent brothers of $v$ has more than $t-1$ keys I redistribute the keys and perform the deletion of $k$
			* Note that the redistribution involves one brother of $v$ and also $v$'s parent!
			* If not, I perform a fusion operation of $v$ with one of the brothers and one key from $v$'s parent
	* If $k$ is in an internal node $v$
		* I find a node containing the predecessor of $k$, which is necessarily on a leaf
		* I copy the max key in $v$ in the place of $k$, which is thus deleted
		* I delete the original copy of the predecessor of $k$, which is on a leaf, using the procedure already seen
	* Also the cost of deletion in B trees is $O(t \log_t n)$ in the worst case
	* Also in deletion, I want to be able to operate in a single pass down the tree
		* I assure that whenever BTREE-DELETE is called on a node, that node has at least $t$ children (1 more than the minimum required of $t-1$)
		* This means that I can be sure that I can fuse to nodes without making their parent violate the B tree property
		* If the root ever becomes without any key, it is deleted and the tree decreases its height

## Graphs and visits
* A graph $G = (V,E)$ is composed of a set of verteces $V$ and edges $E \subset V*V$
* An edge $e = (u,v)$ is defiend by a pair of veritices
* An edge is said to be directed if it is composed by an ordered pair of verteces
* An edge is said to be undirected if it is composed by an unordered pair of verteces
* A graph is said undirected if all of its edges are undirected
* A graph is directed if all of its edges are directed
* Two verteces are said to be adjacent if they are connected by an edge
* The degree of a vertex is equal to the number of adjacent verteces it has
* The sum of the degree of all the verteces is two times the number of edges
$$ \sum_{v \in V} deg(v) = 2 (\mbox{number of edges})$$
* A path is a sequence of verteces $V_1,V_2,...,V_k$ such that $V_i$ and and $V_{I+1}$ are adjacent
* A simple path is a path that does not contain repeated verteces (it does not pass twice on the same vertex)
* A cycle is a simple path, except for the fact that the start and end vertex are the same
* A connected graph is a graph in which any 2 verteces are connected by a path
* A sub-graph is a subset of verteces and edges forming a graph
* A graph does not necessarily need to be connected
	* There can be verteces or sub-graphs that don't have edge between them
* A connected component is a maximal connected subgraph
	* Two verteces are in the same connected compenent iff there is a path between them
* A directed graphs is said to be strongly connected if for every pair of verteces $u,v$ there is a path from $u$ to $v$ and from $v$ to $u$
* The strongly connected components of a directed graph are its maximal strongly connected sub-graphs
	* The strongly connected components form a partition of the graph
* A tree is a connected graph without cycles
* A forest is a collection of trees
* Both trees and forests are special cases of graphs
* Fundamental graph operations are
	* Create a new graph: CREATE($G$)
	* Return True if a graph is empty, False otherwise: EMPTY($G$)
	* Insert a new vertex: INS-VERTEX($G,v$)
	* Insert a new edge: INS-EDGE($G,v_1,v_2$)
	* Delete an existing vertex: DEL-VERTEX($G,v$)
	* Delete an existing edge: DEL-EDGE($G,v_1,v_2$)
	* Return the set of adjacent verteces of $v$: ADJ-SET($G,v$)
* I can represent a graph with an adjacency matrix $M$
	* It is a boolean matrix where $M[i,j]$ is True if the edge $(i,j)$ exists in the graph, False otherwise
	* The space requirement of the adjacency matrix is $O(n^2)$, where $n$ is the number of verteces in the graph
	* An adjancency matrix representation is preferred when the grpah is dense ($|E| \approx |V|^2$), or when I need to quickly tell if 2 verteces are connected
* I can represent a graph also with adjacency lists
	* The adjacency list of a vertex $v$ is the list of verteces adjacent to it
	* A graph is represented by the adjacency lists of all of its verteces
	* The space requirement for the adjacency list of a graph is $\Theta(n+\sum deg(v) = \Theta(n+m))$
		* $n$ is the number of verteces in the graph, $m$ the number of edges
	* The adjacency list representation is preferred for sparse graphs
		* A sparse graph is a graph in which $|V| >> |E|$
* I can represent a graph using an adjacency set
	* An adjacency set is composed by a vector of verteces and a vector of edges
	* The space requirement for an adjacency set is also $\Theta(n+m)$
	* The verteces vector contains for each vertex the address, in the edges vector, of where the adjacent verteces of the current vertex are listed
	* In low-level programming languages I also need to keep track of the end of the array, so I need to insert in the verteces array a fake node that points to the last position of the edges vector
	* I can use the verteces vector to parse correctly the edges vector
	* The edges vector contains the address of the adjacent verteces for each vertex in the verteces vector, in a continuous uninterrupted array
* A graph traversal is the process of visiting all the verteces of a graph
* There are 2 common graph traversal algorithms: breadth-first serach (BFS) and depth-first search (DFS)
* Breadth-first search (BFS), given a source vertex $s$, explores all the verteces adjacent to $s$, and then all the verteces adjacent to those, iteratively
	* Vertices are explored in order of increasing distance from the source $s$
		* The distance of a vertex from the source $s$ is the number of edges in the path from $s$ to the vertex
	* At the beginning all the verteces are undiscovered (they are said to be WHITE)
	* I start from vertex $s$, I put it in the queue $Q$ and I mark it as discovered (referred to as GREY)
	* Until there is somenthing in $Q$ I dequeue one vertex $v$ from it and I loop on the verteces $u$ into its adjacency set
		* If the vertex $u$ in the set is WHITE I mark it as GREY (I discovered it) and I enqueue $u$ in $Q$
	* When all the adjacency set of $v$ is GREY I mark $v$ as BLACK
	* BFS works iteratively until the whole graph is BLACK (I discovered all the vertices)
	* BFS produces a breadth-first tree of the graph by adding verteces and edges to it when they are discovered
	* BFS tells me also which verteces are connected to the source $s$
	* If the graph is implemented with and adjacency list the time complexity of BFS is $O(n+m)$
		* Each vertex in the graph is marked only once
		* For each vertex, I explore once its adjacency set
		* The size of the adjacency set of the whole graph is $O(m)$ since $\sum_{v \in V} deg(v) = 2 (\mbox{number of edges})$
	* If the graph is implemented with and adjacency matrix the time complexity of BFS is $O(n^2)$
		* For each of the $n$ verteces, I need to scan its whole adjacency array of $n$ elements
		* With an adjacency matrix the complexity is independent from the number of edges in the graph

\begin{algorithmic}
\Statex
\Procedure{BFS}{$G, s$}
	\ForAll{$u \in G.V - \{s\}$}
		\State $u.color = WHITE$
		\State $u.d = \infty$ \Comment{$u.d$ is the distance of $u$ from $s$}
		\State $u.\pi = NIL$ \Comment{$u.\pi$ is the predecessor of $u$}
	\EndFor
	\State $s.color = GRAY$
	\State $s.d = 0$
	\State $s.\pi = NIL$
	\State $Q = \emptyset$ \Comment{$Q$ is a new empty queue}
	\State \Call{ENQUEUE}{$Q, s$}
	\While{$Q \not= \emptyset$}
		\State $u = $\Call{DEQUEUE}{$Q$}
		\ForAll{$v \in G.Adj[u]$} \Comment{all the verteces adjacent to $u$}
		\If{$v.color == WHITE$}
			\State $v.color = GREY$
			\State $v.d = u.d + 1$
			\State $v.\pi = u$
			\State \Call{ENQUEUE}{$Q, v$}
		\EndIf
		\EndFor
	\State $u.color = BLACK$
	\EndWhile
\EndProcedure
\end{algorithmic}

* Depth-first search (DFS), given a source vertex $s$, explores recursively all the verteces adjacent to $s$
	* When I visit a vertex $v$ from the vertex $u$, I recursively visit all the unvisited neighbors of $v$
	* When there are no more unvisited neighbors to explore, I backtrack to $u$ and give control to the upper recursion level
	* In general, differently from BFS, DFS is used on the entire graph in order to produce a DFS forest of DFS trees, one for each connected component
	* DFS also create timestamps that record when a given vertex was discovered ($v.d$) and when it was blackened ($v.f$)
		* Any vertex $v$ is WHITE before time $v.d$, GREY between time $v.d$ and time $v.f$, and BLACK after time $v.f$
	* The time complexity is $O(n+m)$ with an adjacency list and $O(n^2)$ with an adjacency matrix for the same considerations made for BFS

\begin{algorithmic}
\Statex
\Procedure{DFS}{$G$}
	\ForAll{$u \in G.V$}
		\State $u.color = WHITE$
		\State $u.\pi = NIL$ \Comment{$u.\pi$ is the predecessor of $u$}
	\EndFor
	\State $time = 0$ \Comment{$time$ is a global variable}
	\ForAll{$u \in G.V$}
		\If{$u.color == WHITE$}
			\State \Call{DFS-VISIT}{$G,u$}
		\EndIf
	\EndFor
\EndProcedure
\Statex
\Procedure{DFS-VISIT}{$G, u$}
	\State $time = time +1$
	\State $u.d = time$
	\State $u.color = GREY$
	\ForAll{$v \in G.Adj[u]$}
		\If{$v.color == WHITE$}
			\State $v.\pi =u$
			\State \Call{DFS-VISIT}{$G,v$}
		\EndIf
	\EndFor
	\State $u.color = BLACK$
	\State $time = time +1$
	\State $u.f = time$
\EndProcedure
\Statex
\end{algorithmic}

## Topological sorting
* A dependency graph is a graph representing casual dependencies between tasks
* In general, tasks to be completed can be arranged into a directed acyclic graph (DAG)
	* Each task is represented by a vertex
	* A directed edge in the DAG represent a casual dependecy relationship between tasks
* Tasks dependencies cannot be represented by a cyclic graph: there would be an infinite loop
* Given a DAG $G=(V,E)$, an ordered set of verteces $S=\{v_1,v_2,...,v_n\}$ is a topological sorting iff
	* It contains all the verteces in $V$
$$s=\{v_1,v_2,...,v_n\}=V$$
	* There is no path from $v_j$ to $v_i$ for all the $i < j$
	* Equivalently, I can say that if there is an edge $u,v$ then $u$ must appear before $v$ in the topological sorting
* A series of tasks can be executed in topological order without violating any dependency
* There can be more than 1 topological sorting for a given DAG
* Topological sorting algorithms add verteces one by one at the beginning of tha list such that any given vertex is added only after all the nodes reachable from it have been added
* The algorithm that we will see uses a modified version of DFS to find nodes that are reachable from the current node

\begin{algorithmic}
\Statex
\Procedure{TOPO-SORT}{$G$}
	\State $L = \emptyset$ \Comment{$L$ is a list}
	\ForAll{$u \in G.V$}
		\If{$u.color \not= WHITE$}
			\State \Call{TOPO-DFS}{$G,u,L$}
		\EndIf
	\EndFor
\EndProcedure
\Statex
\Procedure{TOPO-DFS}{$G,u,L$}
	\State $u.color = GREY$
	\ForAll{$v \in G.Adj[u]$}
		\If{$v.color == WHITE$}
			\State \Call{TOPO-DFS}{$G,v,L$}
		\EndIf
	\EndFor
	\State \Call{ADD-IN-FRONT}{$L,u$} \Comment{$u$ is added to the list only after all the calls on $v$ have returned}
	\State $u.color = BLACK$
\EndProcedure
\Statex
\end{algorithmic}

## Greedy algorithms
* Algorithms for optimization problems typically go through a series of steps, with a set of choices at each step
* For some optimization problems a dynamic programming approach is not needed, since a simpler and more efficient approach will suffice
* A greedy algorithm always makes the choice that looks best at the moment
* It makes a locally optimal choice with the hope that it will lead to a globally optimal solution
* Greedy algorithms can lead to a globally optimal solutions in some problems, but in general they are not guaranteed to do so in any possible problem
* Usually greedy algorithms are easy to design and write
* The basic steps of the greedy approach are first defining a problem and the greedy strategy for solving it, and then showing that the greedy approach leads to an optimal solution
* A problem is said to have optimal substructure if it is possible to find a globally optimal solution to it by combining optimal solutions to its sub-problems
* For a problem to be solvable with a greedy approach, it is necessary but not sufficient that it has an optimal substructure
* Problems that can be solved with a greedy approach are said to repsect the greedy choice property: locally optimal choices are optimal also globally

### The knapsack problem
* The problem is formulated as follows: a thief breaks into a museum and sees many items, of which he knows exactly the value and the weight. The thief has only a single knapsack with him, and he can take away only what he is able to carry with his knapsack. He is able to carry only items up to a certain total weight and he wants to maximise the value of the knapsack content. Items cannot be sub-divided, but just taken or not. The problem consists in finding the optimal set of items that will respect the weight contraint and maximize the value of the knapsack content.
* This problem formulation is said 0-1 knapsack problem since it is the whole or none variant, in which items cannot be split up.
* More formally, the problem can be formulated as: among a set of $n$ items, where item $i$ has value $v_i \in \mathbb{N}$ and weigth $w_i \in \mathbb{N}$, find the subset of items that maximises the total value $\sum_i v_i$ while respecting a total weight contraint $W \in \mathbb{N}$ such that $\sum_i w_i \leq W$
* The 0-1 knapsack problem cannot be solved with a greedy approach, but it can be solved with dynamic programming
* It shows optimal substructure but it does not have a greedy choice property
* The fractional knapsack problem is similar to the 0-1 knapsack problem with one fundamental difference: it is possible to take fractions of items
* The formulation is usually stated similarly to the one for the 0-1 knapsack, but instead of undividable items it is said that the thief wants to maximize the value of the dust of gold and other precious metals that he can carry
* Formally we can define the problem as: among a set of $n$ items, where item $i$ has value $v_i \in \mathbb{N}$ and $w_i \in \mathbb{N}$ amount (in weight) is available of it, find the set of fractions of items that maximises the total value $\sum_i v_i*t_i$ with $t_i \leq w_i$ being the amount of item $i$ taken, while respecting a total weight contraint $W \in \mathbb{N}$ such that $\sum_i t_i \leq W$
* The fractional knapsack problem can be solved with a greedy approach
	* I first choose the item with the highest unitary value and take as much of it as possible
	* If the I still have space in the knapsack after having taken all of the most precious item, I proceed with the second most valuable item and so on until the knapsack is full (until $\sum_i w_i = W$)
* The greedy approach is optimal in this case since it ensures that the knapsack will always be full (if there are enough items to fill it) and replacing any of the items choosen with any other possible item will decrease the total value of the knapsack
* This is the pseudocode for a possible greedy algorithm for the fractional case of the knapsack problem

\begin{algorithmic}
\Statex
\Procedure{FRACTIONAL-KNAPSACK-GREEDY}{$N,W$}
	\State \Comment{$W$ is the total weight constraint}
	\State \Comment{$N$ is a set of items $n$ with $n.v$ being the value of the item and $n.w$ its weight}
	\State $T = 0$ \Comment{$T$ is the total taken amount}
	\State $K = \emptyset$ \Comment{$K$ is a set of items that will store the knapsack content}
	\ForAll{$n \in N$}
		\State $n.d = n.v/n.w$
	\EndFor
	\State $N=$\Call{SORT-DESCENDING}{$N,n.d$} \Comment{sort the items from the most dense to the least dense}
	\ForAll{$n \in N$}
		\If{$n.w \leq W-T$} \Comment{I can take the whole amount of the current item}
			\State $T = T + n.w$
			\State $K.value = K.value + n.v$
			\State $n.a = n.w$ \Comment{$n.a$ is the amount of the current item put in the knapsack}
			\State $K = K + \{n\}$
		\Else
			\State $n.a = W-T$
			\State $K.value = K.value + (n.d*n.a)$
			\State $K = K + \{n\}$
			\State \Return $K$
		\EndIf
	\EndFor
\EndProcedure
\Statex
\end{algorithmic}

### Huffman codes
* Huffman codes are effective ways to compress sequences of characters with a 20% to 90% compression ratio
* The Huffman greedy algorithm uses a table of character frequencies in the data to built an optimal space-efficient binary representation of each character
* I can represent each possible charachter present in the message with an unique binary string called codeword
* If I choose to use fixed-length codewords, for an alphabet of 6 different characters I would need 3 bits per character ($2^3 = 8 \geq 6$ while $2^2 = 4 < 6$)
* With a variable-lenght code I can reach a greater efficency by reducing the average number of bits per character below 3
	* It would be efficient to assign a short codeword to frequent characters and a longer codeword to rare characters
* We will restrict our attention to binary codes in which no codeword is also a prefix of some other codeword
	* These codes are called, somewhat counter-intuitively, prefix codes
	* It can be proven that a prefix code can always achieve optimal data compression among any character code, so we are not suffering a loss in generality by limiting ourselves to prefix codes
	* Prefix codes are desirable since the decoding of characters from a binary string is unambiguous
* In Huffmann codes, I represent all the codewords in a given message as leaves in a binary tree
	* A codeword is interpreted as the simple path from the root to the corresponding leaf, where each left turn corresponds to a 0 and each right turn to a 1
	* Note that these trees are not BSTs, since leaves do not appear in sorted order and internal nodes do not contain any key
* Given an Huffman tree $T$, I can compute the number of bits needed to encode a file
	* For each charachter $c$ in the alphabet $C$, let $c.freq$ be the frequency of the charachter in the file and $d_T(c)$ denote the depth of the leaf corresponding to $c$ in the tree
	* Note that $d_T(c)$ is also the lenght of the codeword for character $c$
	* The number of bits required for encoding the file is thus
$$B(T) = \sum_{c \in C} c.freq*d_T(c)$$
	* $B(T)$ is also defined as the cost of the tree $T$
* The Huffman tree for a message can be built using the greedy Huffman algorithm
	* It works on an alphabet $C$
	* It uses a min-priority queue $Q$ keyed on the $freq$ attribute
	* It starts from a set of $|C|$ leaves
	* It merges together leaves starting from the least frequent ones
	* The frequency of an internal node is built from the sum of the frequencies of all the leaves under it

\begin{algorithmic}
\Statex
\Procedure{HUFFMAN}{$C$}
	\State $n = |C|$
	\State $Q = C$
	\For{$i=1$ to $n-1$}
		\State allocate a new node $z$
		\State $z.left = x =$\Call{EXTRACT-MIN}{$Q$}
		\State $z.right = y =$\Call{EXTRACT-MIN}{$Q$}
		\State $z.freq = x.freq+y.freq$
		\State \Call{INSERT}{$Q,z$}
	\EndFor
	\State \Return \Call{EXTRACT-MIN}{$Q$} \Comment{return the root of the tree}
\EndProcedure
\Statex
\end{algorithmic}

## Dynamic programming
* Dynamic programming, similarly to the divide-et-impera approach, solves problems by finding the solution to sub-problems
	* "Programming" here refers to the use of a matrix, not to computer programming (this is the same also in linear programming)
	* It was formalized in the 1950s by R. Bellman
* While divide-et-impera is used to solve problems made up of disjoint sub-problems, dynamic programming is used when the sub-problems overlap
	* This is, in dynamic programming sub-problems share sub-sub-problems
	* In this context a divide-et-impera approach wastes resources by solving multiple times the same sub-problems
	* Dynamic programming stores intermediate solution and so avoids to solve multiple times the same sub-problems
	* While divide-et-impera is typically done recursively and from the top-down, dynamic programmic is typically implemented iteratively and from the bottom-up
* Problems that can be solved with dynamic programming are typically optimization problems
	* These have many possible solutions, each associated one with a different value
	* We want to find the solution with associated value that is minimal/maximal (according to the problem) in the set of possible solution values
	* This solution is called **an** optimal solution instead as **the** optimal solution, since there can be many equally optimal solutions
* Developping a dynamic programming algorithm is done in a sequence of 4 steps
	* Describe what the structure of an optimal solution should be
	* Define the value of the optimal solution recursively
	* Compute the value of an optimal solution, typically from the bottom-up
	* Contruct the optimal solution from the computed information
		* This step can be omitted if I am only interested in the value of an optimal solution
* For a problem to be solvable with dynamic programming, it has to have some key characteristics
	* It should show optimal substructure
	* It should have overlapping sub-problems
* A problem is said to show optimal substructure if a solution to the problem contains the solution to its sub-problems
* To show that a problem has an optimal substructure a common pattern is followed
	* First I show that the solution to the problem consists in making a choice, and this choice leaves one or more similar sub-problems to be solved
	* Then I suppose that I know what is the optimal choice for the problem, the one that leads to an optimal solution
	* Given the optimal choice, I determine which sub-problems I should solve and how can I characterize the space of sub-problems
		* Characterizing the space of sub-problems means to define the parameter space relevant for the problem (in the 0-1 knapsack problem this corresponds to all the possible combinations of the maximum weight of the knapsack $j$ and the subset of items up to $i$)
	* I show by contradiction that the solution to sub-problems used for finding an optimal solution to the problem must be themselves optimal
		* I show that the solution of the problem obtain from sub-optimal solution to its sub-problems can be improved by choosing an optimal sub-problem solution, thus showing that the original problem solution was sub-optimal
* A problem solvable with dynamic programming has independent and overlapping sub-problems
	* Sub-problems are independent in the sense that they do not share resources
	* Sub-problems overlap in the sense that the same problem occurs as sub-problem of different problems
		* I can take advantage of this by storing the result of sub-problems
	* A problem with overlapping sub-problems shows a small sub-problem space
		* This is because the recursive solution to sub-problems incurs again and again in the same sub-problems
		* Quantitatively, the sub-problem space is typically polynomial on input size
		* A problem with optimal sub-structure but non-overlapping sub-problems is a typical divide-et-impera problem
* Storing the choice made in each sub-problem in a table allows to easily reconstruct a global solution
	* If we need to reconstruct the solution and not only to know its value, I typically keep 2 tables, one storing the solutions themselves and one storing the choices made to reach them
* A subtly different alternative to the iterative bottom-up dynamic programming approach is the memoized recursive dyanmic programming approach
	* Instead of using the iterative bottom-up approach, I maintain the recursive top-down approach of the divide-et-impera paradigm
	* I store the solution to the sub-problems that I encounter in a table, so to not solve the same sub-problems again and again
	* In general, if all the possible sub-problems in problem space must be solved at least once, than the bottom-up approach outperforms the memoized recursive approach by a constant factor
		* This is because the bottom-up approach lacks all the overhead due to recursive calls and has less overhead for mantaining the solution table
		* With the bottom-up approach I can also exploit the regular pattern of table access to store at any given time only a constant number of solutions
			* This is what we did in the last version of the Fibonacci algorithm
	* If some sub-problems do not need to be solved at all, the memoized recursive version has the advantage of solving only those sub-problems that are effectively needed

### Fibonacci numbers
* The Fibonacci sequence is defined by the Fibonacci function $F$ as
$$\begin{cases}F_1=1 \\F_2=1 \\ F_n= F_{n-1}+F_{n-2} & n > 2\end{cases}$$
* The number of clockwise and anticlockwise spirals in many vegetables (sunflower, cauliflower, ecc.) tend to have adjacent values of the Fibonacci sequence
* The $n^{th}$ Fibonacci number can be calculated recursively in a very ineffcient way
	* The computational cost of this implementation is described by the following recurrence equation
$$ T(n) = \begin{cases}c_1 & n \leq 2 \\ T(n-1)+T(n-2)+c_2 & n > 2\end{cases}$$
	* Solving the equation gives that $T(n)=O(2^n)$, so the algorith has exponential time complexity

\begin{algorithmic}
\Statex
\Procedure{FIBONACCI-NAIVE}{$n$}
	\If{$n \leq 2$}
		\State \Return $1$
	\Else
		\State \Return \Call{FIBONACCI-NAIVE}{$n-1$} $+$ \Call{FIBONACCI-NAIVE}{$n-2$}
	\EndIf
\EndProcedure
\Statex
\end{algorithmic}

* I can solve the same problem iteratively in linear time and space

\begin{algorithmic}
\Statex
\Procedure{FIBONACCI-ITERATIVE}{$n$}
	\If{$n \leq 2$}
		\State \Return $1$
	\Else
		\State initialize the array $f[1...n]$
		\State $f[1]=1$
		\State $f[2]=1$
		\For{$i=3$ to $n$}
			\State $f[i] = f[i-1]+f[i-2]$
		\EndFor
		\State \Return $f[n]$
	\EndIf
\EndProcedure
\Statex
\end{algorithmic}

* This approach can be further improved by not storing the intermediate values of the sequence
	* In this way I can reach linear time and constant space complexity

\begin{algorithmic}
\Statex
\Procedure{FIBONACCI-ITERATIVE-CONSTANT-SPACE}{$n$}
	\If{$n \leq 2$}
		\State \Return $1$
	\Else
		\State initialize the array $f[1...3]$
		\State $f[1]=1$
		\State $f[2]=1$
		\For{$i=3$ to $n$}
			\State $f[1] = f[2]$
			\State $f[2] = f[3]$
			\State $f[3] = f[1]+f[2]$
		\EndFor
		\State \Return $f[n]$
	\EndIf
\EndProcedure
\Statex
\end{algorithmic}

### Dynamic programming for the 0-1 knapsack problem
* For the 0-1 knapsack problem, I can describe an optimal solution in terms of the optimal solution for a smaller knapsack and number of objects
* I have an array of weights for each object $w[1...n]$ and an array of values $v[1...n]$
* The maximum capacity of the knapsack is $W$
* I start by creating the dynamic programming matrix $V(i,j)$ with $i=0...n$ and $j=1...W$
* I want to find the solution $V(i,j)$ consisting of a sub-set of the first $i$ objects whose total weight is less than $j$ and that maximize the total value of the knapsack
* The optimal solution for a knapsack of capacity $W$ with a set of $n$ objects available will be the value computed in $V(n,W)$
* I initialize the matrix by filling the first row and the first column as follows
	* I set the first column to 0 since for a capacity $j=0$ no object can fit, and so the maximal value of the knapsack is always 0
$$v(i,0)=0 \mbox{ for } i=1...n$$
	* I set the first row to the value of the first object if it can fit ($j \leq w[1]$), 0 otherwise
$$v(1,j)= \begin{cases} v[1] & \mbox{for } j \geq w[1] \\ 0 & \mbox{for } j < w[1] \end{cases}$$
* Then I compute the matrix $V$ iteratively for $i=0...n$ and $j=1...W$ as follows
$$V(i,j) = \begin{cases} V(i-1,j) & \mbox{if } w[i] > j\\ max(V(i-1,j),V(i-1,j-w[i])+v[i]) & \mbox{if } w[i] \leq j \end{cases}$$
	* If the $i^{th}$ item does not fit in an empty knapsack of capacity $j$, I cannot take it and the optimal composition of the knapsack of capacity $j$ considering the subset of objects $0...i$ is the same as considering the subset of objects $0...i-1$
$$ V(i,j) = V(i-1,j) \qquad \mbox{if } w[i] > j$$
	* If it can fit in the knapsack, I make the choice that maximizes the total knapsack value among
		* Putting the object in the knapsack and filling the remaining $j-w[i]$ free capacity with the optimal solution already found $V(i,j-w[i])$: in this case the value of the optimal knapsack of capacity $j$ is the value of the optimal knapsack of capacity $j-w[i]$ plus the value of the current object $v[i]$
$$V(i,j) = V(i-1,j-w[i])+v[i]$$
			* Note that since I am using $j-w[i]$ has an index for the matrix, $w[i]$ has to be an integer!
		* Not putting the $i^{th}$ object in the knapsack and retaining the composition that it had considering only the subset of objects $1...i-1$
$$ V(i,j) = V(i-1,j)$$
* In order to know which objects are in the best solution $V(n,W)$ I need to build an additional table of booleans $K(i,j)$
	* I set $K(i,j)=TRUE$ if the $i^{th}$ object belongs to the set of objects used for calculating $V(i,j)$, false otehrwise
$$K(i,j)= \begin{cases} TRUE & \mbox{if } V(i,j)\not=V(i-1,j) \\ FALSE & \mbox{if } V(i,j)==V(i-1,j) \end{cases}$$
* From the matrix $K$, I start from the bottom right and I procede by subtracting $w[i]$ at each step (I move to $K(i,j-w[i])$)
	* The included objects are the ones for which $K$ is true in this path
* The following pseudocode can print the objects included in the optimal solution

\begin{algorithmic}
\Statex
\Procedure{PRINT-KNAPSACK-CONTENT-DP}{$N,W,K$}
	\State $j = W$
	\State $i = |N|$
	\While{$i > 0$}
		\If{$K(i,j)$} \Comment{$K$ is a table of booleans}
			\State \Call{PRINT}{$N.item_i$}
			\State $j = j - N.w_i$
		\EndIf
		\State $i = i-1$
	\EndWhile
\EndProcedure
\Statex
\end{algorithmic}


### The subset-sum problem
* The subset-sum problem is a variant of the 0-1 knapsack problem in which I want to find a set of objects whose total weight is exactly $W$
	* Note that in this case the total value of the set is completely irrelevant (the value of the objects is not even defined)
* Given a set $X=\{1,2,...,n\}$ of $n$ objects where object $i$ weights $w[i]$ which is a positive integer, and a total capacity $W$, I want to find a subset $Y \subseteq X$ such that $\sum_{i \in Y} w[i] = W$
* I can solve the subset-sum problem with dynamic programming similarly to how I can solve the 0-1 knapsack problem
* In this case the sub-problem $P(i,j)$ is to determine if a set of objects drawn from the subset of objects $1...i$ with total weight exactly $j$ exists
* A solution $B(i,j)$ is TRUE iff a subset of the first $i$ objects with total weight exactly $j$ exists, FALSE otherwise
* To solve the subset-sum problem, I create the solution matrix $B$ and I initialize the first row to TRUE, since I can always find a set of objects that fills completely a capacity $j=0$: the empty set
$$B(i,0) = TRUE \qquad \mbox{for } i=1...n$$
* The first row is set to TRUE if the first object fits exactly in the capacity, 0 otherwise (this is, if $w[1]\not=j$)
$$B(1,j) = \begin{cases} TRUE & \mbox{if } j=w[1]\\FALSE & \mbox{if } j>0 \mbox{ and } j \not=w[1] \end{cases}$$
* Then in the general case, for each cell $B(i,j)$ I compute has follows
	* If $j<w[i]$ than the object $i$ does not fit in the capacity and so the optimal solution is the same found without considering that object
$$B(i,j)=B(i-1,j) \qquad \mbox{if } j<w[i]$$
	* Otherwise if $j \geq w[i]$ $B(i,j)$ is TRUE if either of these 2 conditions is verified
		* The capacity $j-w[i]$ can be filled exactly with the $1...i-1$ subset of objects
$$B(i-1,j-w[i]) = TRUE \implies B(i,j) = TRUE$$
		* I already filled exactly capacity $j$ without considering object $i$
$$B(i-1,j) = TRUE \implies B(i,j) = TRUE$$
	* If none of these conditions is verified than $B(i,j) = FALSE$
* The solution of the subset-sum problem can be found by interrogating $B(n,W)$ after the computation
* The following pseudocode prints the solution of the subset-sum problem

\begin{algorithmic}
\Statex
\Procedure{SUBSET-SUM}{$w,W$}
	\State \Comment{$w[1...n]$ is a list of weights for each item and $W$ the total capacity}
	\State initialize the matrix $B(1...n,0...W)$
	\For{$i=1$ to $n$}
		\State \Comment{I could also not do this loop and only set $B(1.0)=TRUE$, but check next comment}
		\State $B(i,0) = TRUE$
	\EndFor
	\For{$j=1$ to $W$}
		\If{$j=w[i]$}
			\State $B(1,j) = TRUE$
		\Else
			\State $B(1,j) = FALSE$
		\EndIf
	\EndFor
	\For{$i=2$ to $n$}
		\For{$j=1$ to $W$}
			\State \Comment{if in the previous comment I did so, the I should start from $j=0$, it would be less readable}
			\If{$j \geq w[i]$}
				\If{$B(i-1,j)$}
					\State $B(i,j) = B(i-1,j)$
				\Else
					\State $B(i,j) = B(i-1,j-w[i])$
				\EndIf
			\EndIf
		\EndFor
	\EndFor
	\State \Call{PRINT}{$B(n,W)$}
\EndProcedure
\Statex
\end{algorithmic}

## Shortest paths
* I am given an edge $(x,y) \in E$ with an associated cost $w(x,y)$
* The cost of a path $\pi=(v_0,v_1,...,v_k)$ that connects the vertex $v_0$ with the vertex $v_k$ is the sum of the weights of all the edges that it includes
$$w(\pi)=\sum_{i=1}^k w(v_{i-1}, v_i)$$
* The shortest path between the verteces $u$ and $v$ $pi^*_{uv}$ is the path with minimal cost between them (if it exists)
	* A path between 2 verteces does not exist when they are not reachable from each other
		* $v$ is not reachable from $u$ if there are no edges among them or if the edges are directed in the wrong direction
	* Also cycles with an overall negative cost make the target unreachable, since when one of them is present I will continuously go around the cycle getting lower and lower cost
	* There can be many shortest paths with equal costs
	* In a directed graph $\pi^*_{uv}$ is not necessarily equal to $\pi^*_{vu}$
* The single source shortest path from a source vertex $s$ is the set of shortest paths $\pi^*_{sv}$ from $s$ to all the verteces $v$ reachable from it
* The all-pairs shortest path is the set of shortest paths $\pi^*_{uv}$ for all possible pairs of connected verteces $u$ and $v$ in a graph
* There is no known algorithm that solves the shortest path between 2 arbitrary verteces $\pi^*_{uv}$ without solving also the single source shortest path for $u$ in the worst case
* The shortest path problem shows an optimal substructure: each sub-path of the shortest path is by itself a shortest path among different nodes
	* Let $\pi^*_{uv}$ be the shortest path from vertex $u$ to vertex $v$
	* Let $i$ and $j$ be 2 intermediate verteces along the path $\pi^*_{uv}$ that are connected by the sub-path $\pi_{ij}$, contained in $\pi^*_{uv}$
	* I assume by contradiction that there is an alternative path $\pi'_{ij}$ such that $w(\pi'_{ij}) < w(\pi_{ij})$
	* If that was true, then $\pi^*_{uv}$ would not be a shortest path, since I could find a path between $u$ and $v$ passing along $\pi'_{ij}$ instead that along $\pi_{ij}$
* In a directed graph without negative-weight cycles there is a shortest path between any pair of connected verteces
	* In the absence of negative-weight cycles a shortest path between connected verteces exists since there is only a finite number of paths among those verteces
	* There is a finite number of paths among them since I cannot create a shorter path by adding a cycle to it (I am in a graph without negative-wieght cycles)
* A shortest path cannot contain positive-weight cycles
	* If a path contains a positive-weight cycle it is always possible to make the path shorter by removing the cycle
* If a shortest path among 2 verteces exists, it is always possible to find an acyclic shortest path among them
	* I can have a shortest path between 2 verteces that contains a cycle with a total weight of 0, but in this case there would be also an alternative shortest path that skips that cycle
* A shortest path tree $T_s$ contains all the verteces reachable from a source $s$, which is the root of the tree, such that all the paths from $s$ are shortest paths
	* I can build it from a partial tree by exploiting the optimal substructure of shortest paths
* The distance $d_{uv}$ between the verteces $u$ and $v$ is the cost of any shortest path $\pi^*_{uv}$ connecting them if one exists, $+\infty$ otherwise
$$d_{uv} = \begin{cases}w(\pi^*_{uv}) & \mbox{if } \exists \ \pi^*_{uv}\\ +\infty & \mbox{if } \nexists \ \pi^*_{uv} \end{cases}$$
* The distance of a vertex to itself is always 0
$$d_{vv} = 0$$
* Distances on graphs respect the triangle inequality
$$ d_{uv} \leq d_{ux} + d_{xv}$$

### Relaxation
* Relaxation is a technique used by various shortest-path algorithms
* For each vertex $v \in V$ I maintain an attribute $v.d$ which is an upper bound for the shortest path from the source $s$ to $v$
	* $v.d$ is a shortest path estimate
* I also maintain $v.\pi$ as the predecessor of $v$ in the shortest path tree $T$
* First I initialise everithing by setting
$$s.d = 0$$
$$v.d = +\infty \quad \forall \ v \in V- \{s\}$$
$$v.\pi = NIL \quad \forall v \in G.V$$
* Then I relax the edge $(u,v)$ by testing whether I can improve the shortest path to $\pi^*_{sv}$ by passing through $u$, and updating the relative attributes of $v$ accordingly

\begin{algorithmic}
\Statex
\Procedure{INITIALIZE-SINGLE-SOURCE}{$G,s$}
	\ForAll{$v \in G.V$}
		\State $v.d = \infty$
		\State $v.\pi = NIL$
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

### Dijkstra algorithm
* The Dijkstra algorithm computes the single-source shortest path with a greedy approach provided that there are no negative-weight edges (not cycles, edges!) in the graph
* The similar Bellman-Ford algorithm solves the problem also when negative edges are present, but it is slower and it is based on dynamic programming
* With a good implementation the Dijkstra algorithm is faster than the Bellman-Ford algorithm
* Let $G=(V,E)$ be a drected weighted graph such that $w(u,v) \geq 0 \quad \forall \ (u,v) \in G.E$
* Let $S \subseteq G.V$ be the set of vertices that are part of a partial shortest path tree $T$ rooted in the vertex $s$
	* $T$ contains only shortest paths originating from $s$, but not all of them
* The edge $(u,v)$ with $u \in S$ and $v \in G.V-S$ that minimizes $d_{su}+w(u,v)$ belongs to the shortest path $\pi^*_{sv}$ if all the edges $(x,y) \in G.E$ are non-negative
	* In practice it means that the shortest edge connecting a shortest path to the node of interest is part of the shortest path to that node
	* If I take another route with more edges from the shortest path to the node I am guaranteed to not decrease the cost, sice weights are assumed to not be negative
	* If an edge is negative this is not necessarily true since adding an edge can decrese the cost
	* Let's assume by contradiction that $(u,v)$ does not belong to $\pi^*_{sv}$
	* In this case I have that
$$ d_{su}+w(u,v) > d_{sv}$$
	* Therefore, there must be a shortest path $\pi^*_{sv}$ that does not include $(u,v)$ with weight less than $d_{su} + w(u,v)$
	* I can decompose this hypotetical shortest path $\pi^*_{sv}$ into the shortest paths $\pi^*_{sy}$, $\pi^*_{xy}$ and $\pi^*_{xv}$ where $y$ and $x$ are a pair of adjacent verteces along the path $\pi^*_{sv}$
		* This is thanks to the optimal substructure property of shortest paths
	* Since $x$ and $y$ are adjacent verteces IN THE SHORTEST PATH $\pi^*_{sv}$, the shortest path among them is represented by the edge $(x,y)$
	* I can therefore write
$$ d_{sv} = d_{sx}+w(x,y)+d_{yv}$$
	* By definition, the edge $(u,v)$ is the edge among a vertex in the partial shortest-path tree $T$ and a vertex in the graph $G$ but not in $T$ that minimizes $d_{su}+w(uv)$
	* Therefore, for any alternative vertex $x \in S$ connected to $v$
$$ d_{su} +w(u,v) \leq d_{sx} + w(x,y)$$
	* Note that $u$ can be ANY vertex $\in S$ and $v$ can be ANY vertex $\in G.V-S$
	* The pair of verteces $u,v$ is choosen such that there is NO other pair $x,y$ with $d_{sx}+w(x,y) < d_{su}+w(u,v)$
$$ d_{su}+w(u,v) \leq d_{sx}+w(x,y) \qquad \forall \ x,u \in S, \qquad \forall \ y,v \in G.V-S $$
	* This leads to the absurd conclusion that $d_{su}+w(u,v)$ is shorter than $d_{sx}+w(x,y)$, but $d_{sx}+w(x,y)+d_{yv}$ is shorter than $d_{su}+w(u,v)$
	* By constraint of the algorithm, $w(x,y) \geq 0 \quad \forall (x,y) \in G.E$, so the above is impossible
	* From the last statement we can see also why the Dijkstra algorithm cannot work properly in the presence of negative-weight edges
* This implementation of the Dijkstra algorithm uses a min priority queue $Q$ containing the nodes $v$ with keys equal to $v.d$
	* Calling EXTRACT-MIN($Q$) means taking the node in the queue which is closest to the source $s$ in terms of shortest path estimate
	* At the fist call $s$ itself is extracted since $s.d = 0$ while $v.d = \infty$ for all the other nodes
* The running time of this implementation of the Dijkstra algorithm depends on how the min-priority queue is implemented
	* The INITIALIZE-SINGLE-SOURCE call is an $O(n)$ operation with $n$ being the number of verteces
		* It set 2 pointers for each of the $n$ verteces and finally it sets $s.d=0$
	* The initialization of $S$ to an empty set is an $O(1)$ operation
	* The queue is filled once with $n$ elements (an $O(n)$ operation with a min-heap) and since then always emptied
	* Each iteration of the while loop removes one element from $Q$, so it iterates $n$ times
		* EXTRACT-MIN is an $=O(\log n)$ operation in a min-heap
		* The addition of $u$ to the set $S$ is an $O(1)$ operation
		* The for loop iterates a number of times equal to the lenght of the adjacency set of the current node
			* The RELAX procedure is an $O(\log n)$ operation since it implicitely calls DECREASE-KEY ($O(\log n)$ in a min-heap)
	* In general the number of total iteration of the for loop across all the while loop iterations is the sum of the adjacency lists of all the nodes, $O(m)$
	* So we have an $O(n)$ time for the rows outside the loops, a while loop executed $n$ times containing a for loop executed, overall, $O(m)$ times
	* The unitary cost of the while loop except the for loop is $O(\log n)$, while the cost of each iteration of the for loop is $O(\log n)$
	* The overall cost of the while loop is $O((m+n) \log n)$
	* The final cost of DIJKSTRA implemented with a min-heap is thus
$$O((m+n)\log n) = O(m \log n)$$

\begin{algorithmic}
\Statex
\Require{$v.d \geq 0 \quad \forall \ v \in G.V$}
\Statex
\Procedure{DIJKSTRA}{$G, w, s$}
	\State \Call{INITIALIZE-SINGLE-SOURCE}{$G,s$}
	\State $S = \emptyset$
	\State $Q = G.V$
	\While{$Q \neq \emptyset$}
		\State $u =$ \Call{EXTRACT-MIN}{$Q$}
		\State $S = S \cup \{u\}$
		\ForAll{$v \in G.Adj[u]$}
			\State \Call{RELAX}{$u,v,w$}
		\EndFor
	\EndWhile
\EndProcedure
\end{algorithmic}

# Roberto Amandini module

---

## Disjoint sets
* Sometimes we are interested in joining $n$ distinct elements into a collection of disjoint-sets
	* It is useful for determining the connected components of an undirected graph
* Two sets are disjoint if they do not have any common element
$$ S_i,S_j \mbox{ are disjoint } \iff S_i \cap S_j = \emptyset$$
* A collection of disjoint-sets $S$ is a set of sets $S_1, S_2,..., S_n$ that are disjoint
$$S=\{S_1,S_2,...,S_n\} \ :\ S_i \cap S_j = \emptyset \ \forall \ i \not= j \ \land \ i,j \in 1,2,...,n$$
* The sets in a disjoint-set collection can change over time (they are dynamic)
* Data structures have been implemented for working with disjoint-set collections (disjoint-set data structures)
* These data structures must implement some basic operations
	* Creating a disjoint-set $S_i = \{x\}$
	* Finding the set $S_i$ to which an element $x$ belongs to
	* Merging the disjoint-sets $S_i, S_j$ by computing their unioin $S_i \cup S_j$
* Each disjoint-set $S_i$ is uniquely identified by a representative $\rho_i \in S_i$, a member of the set itself
	* In most cases it doesn't matter which element is choosen as a representative
	* Any FIND operation on the set $S_i$ must return the same representative $\rho_i$
	* When 2 disjoint-sets are merged, the representative can change
	* It is possible to use a specific element of $S_i$ as a representative, for instance the maximum or minimum element of the set
* MAKE-SET($x$) creates a set $\{x\}$ assuming that $x\not\in S_i \ \mbox{for } i=1...n$
	* Since $x$ is the only element of the new set, it will also be its representative
	* I need to check that $x$ is not contained in any other set before inserting it in a new set!
* FIND-SET($x$) returns a pointer to the representative $\rho_i$ of the unique set $S_i$ containing $x$
* UNION($x, y$) returns $S_x \cup S_y$ assuming that $x \in S_x$, $y \in S_y$, and $S_x \cap S_y = \emptyset$
	* The condition $S_x \cap S_y = \emptyset$ can be verified by enforcing that they belong to sets with different representatives
$$\mbox{FIND-SET}(x)\not=\mbox{FIND-SET}(y) \implies S_x \cap S_y = \emptyset$$
	* The UNION operation destroys the sets $S_x$ and $S_y$
	* After UNION, a new representative for the set $S_x \cup S_y$ must be choosen
		* Usually either the representative of $S_x$ or that of $S_y$ is used

### Connected components
* A subgrapg $G'=(V',E')$ of the graph $G=(V,E)$ is a connected component if there is a path among all the possible pairs of verteces in $V'$ and there is no path among any vertex in $V$ and any vertex in $V$ but not in $V'$
$$G'=(V',E') \mbox{ is a connected component } \iff \mbox{ for } x \in V' \begin{cases} \exists \ x \leadsto y \ \forall \ y \in V' \\  \nexists \ x \leadsto z \ \forall \ z \in V-V'  \end{cases}$$
* Disjoint sets can be used for determining the connected components in an undirected grpah $G=(V,E)$
	* When the graph $G$ is static, I can quickly determine the connected components with a series of depth-first searches
	* When the graph is dynamic (edges are added and removed over time), disjoint-sets are more efficient in maintaining the connected components as the graph is modified
		* When an edge is added I can just join the respective sets
* We can define some operations based on disjoint-sets to work on connected components
	* CONNECTED-COMPONENTS($G$) computes what are the connected components
	* SAME-COMPONENTS($u,v$) returns TRUE if $u$ and $v$ belong to the same component

\begin{algorithmic}
\Statex
\Procedure{CONNECTED-COMPONETS}{$G$}
	\ForAll{nodes $v \in G.V$}
		\State \Call{MAKE-SET}{$v$}
	\EndFor
	\ForAll{$(u,v) \in G.E$}
		\If{\Call{FIND-SET}{$u$} $\neq$ \Call{FIND-SET}{$v$}}
		\State \Call{Union}{$u,v$}
		\EndIf
	\EndFor
\EndProcedure
\Statex
\Procedure{SAME-COMPONETS}{$u,v$}
	\If{\Call{FIND-SET}{$u$} == \Call{FIND-SET}{$v$}}
		\State \Return TRUE
	\Else
		\State \Return FALSE
	\EndIf
\EndProcedure
\Statex
\end{algorithmic}

### Disjoint sets representations
* Disjoint sets can be implemented naively with linked lists
	* In this case each disjoint-set is represented by a linked list $L$ where each element $x$ stores
		* The set member $x.elem$
		* A pointer to the next element in the list $x.next$
		* A pointer back to the set object $x.set$
	* The first object of the list $S.head$ is taken as representative
	* In this case MAKE-SET($x$) and FIND-SET($x$) are easy to implement and have constant time complexity ($O(1)$)
		* MAKE-SET just creates a new list containing only the object $x$
		* FIND-SET follows the pointer $x.set$ back to the set object, and then returns the head of the respective list $L.head$
	* UNION($x,y$) can be implemented naively by appending the list $L_y$ to which $y$ belongs to the list $L_x$ to which $x$ belongs
		* This operations costs $O(|L_y|)$ since I need to update all the pointers $y.set$ for all the elements in $L_y$
	* In order to inprove the performances of UNION($x,y$) I can use a weighted-union heuristic: I always append the sortest list among $L_x$ and $L_y$ to the longer one
* Here we will always refer to the total number of MAKE-SET, UNION, and FIND-SET operations as $m$, and to the total number of MAKE-SET operations as $n$
	* Since the number of MAKE-SET operations $n$ is included in the number of total operations $m$, we have that $m \geq n$
	* We assume that the first $n$ operations performed of the $m$ total operations are all MAKE-SET operations
	* The total number of UNION operations in a collection of disjoint-sets is at most $n-1$
		* $n$ is the number of MAKE-SET operations, and so the number of initial sets
		* After $n-1$ unions on $n$ sets I am left with a single set
* The running time is $O(m+n \log n)$ with a linked lists representation of disjoint-sets
	* We are performing at most $n-1$ UNION operations
	* Since we are using the weighted-union heuristic, when I perform an UNION operation the pointers are always updated in the smaller original set
	* Let's look at an element $x$
	* After 1 union in which $x$'s pointer is updated the resulting set has at least 2 members, after 2 updates at least 4, and so on
	* For any $k \leq n$, when $x$'s pointer has been updated $\lceil \log k \rceil$ times, the resulting set has at least $k$ members
	* Since the largest set has at most $n$ members, each object's pointer is updated at most $\lceil \log n \rceil$ times overall
	* The total time spent in UNION operations is thus $O(n \log n)$
	* Each MAKE-SET and FIND-SET operation takes $O(1)$ time, and $O(m)$ of them are performed
	* Thus the total time for the entire sequence is $O(m+n\log n)$
* The amortized cost (average cost per operation) with a linked-list representation of disjoint-sets is thus
$$\frac{O(m+n \log n)}{m} = O\left(\frac{n \log n}{m}\right)$$
* Instead of linked lists, we can use a disjoint-set forest representation
	* In this case each disjoint-set is represented by a rooted tree
	* Each node in each tree contains an element $x$ and a pointer to its parent node $x.p$
	* The representative of a set is the root of the corresponding tree
	* The parent pointer of the root of each tree points to itself
$$ x.p = x \implies x \mbox{ is a root}$$
	* MAKE-SET($x$) creates a tree with just the root in $O(1)$ time
	* FIND-SET($x$) traverses the tree up to the root with a worst-case running time of $O(n)$
	* UNION($x,y$) just redirects the pointer $x.p$ of the root of a tree to the root of another tree
		* If I know who the 2 roots are the running time is $O(1)$
			* I know the roots if I am maintaining a table of all the roots
		* If I don't know I need to call FIND-SET($x$) and FIND-SET($y$)
			* In this case UNION becomes an $O(n)$ operation in the worst case
* So far it seems that the disjoint-set forest representation is not better than the linked-list representation, but we can improve dramatically the amortized cost of the disjoint-set forest by using some heuristics
* Union-by-rank: I can minimize the height of each tree resulting from UNION operations by making the root of the tree with fewer nodes point to the root of the tree with more nodes, and not vice-versa
	* I maintain an $x.rank$ attribute for each node which is equal to the height of the subtree rooted in $x$
	* When performing an UNION, I append the root with smaller rank to the root of higher rank
		* This cannot alter the rank of the resulting root
	* If the 2 roots have the same rank, I just choose one of the 2 trees and append it to the other
		* In this case I need to increment by 1 the rank of the resulting root
* Union-by-rank improves the running time from $O(m+n \log n)$ to $O(m \log n)$
	* A tree rooted in $x$ has at least $2^{x.rank}$ nodes
		* This can be proven by induction on the number of UNION operations performed
	* Since $2^{x.rank} \leq n$, I have that $x.rank \leq \log n$
	* FIND-SET can thus at most traverse $\log_n$ nodes in $O(\log n)$ time
	* Since I am performing at most $m-n$ FIND-SET operations, the overall cost is bounded by $O(m \log n)$
* The amortized cost implementing union-by-rank becomes
$$\frac{O(m \log n)}{m} = O\left(\frac{m \log n}{m}\right)=O(\log n)$$
* Path compression: I add redirect $x.p$ directly to the root of the respective tree on each node $x$ on the path to the root when performing a FIND-SET operation
	* This makes future FIND-SET operations on the affected nodes run in $O(1)$ time since I avoid traversing the whole path
* Path compression reduces the worst case running time to $O(n+f(1+\log_{2+f/n}n))$, where $f$ is the number of FIND-SET operations performed
	* This is complicated but possible to prove
* Hybrid approach: I can combine the use of union-by-rank and path compression
	* In this case when I perform a path compression with FIND-SET I do not waste time updating all the affected $x.rank$ pointers
	* $x.rank$ is update only bu UNION operations and is no more the exact height of the subtree rooted in $x$ (as in pure union-by-rank) but an upper bound on this height
* Combining both union-by-rank and path compression yields a worst case running time of $O(m \ \alpha(n)) \approx O(m)$, where $\alpha$ is the inverse Ackermann function
	* The inverse Ackermann function grows incredibly slowly: $\alpha(n) < 5$ for any $n$ that can be written in the physical universe
		* We can safely assume that $\alpha(n) \approx O(1)$
* The amortized cost of the hybrid approach is thus
$$\frac{O(m \ \alpha(n))}{m} = O\left(\frac{m \ \alpha(n)}{m}\right)=O(\alpha(n)) \approx O(1)$$
* The following pseudocode implements the hybrid approach with union-by-rank and path compression

\begin{algorithmic}
\Statex
\Procedure{MAKE-SET}{$x$}
	\State $x.p = x$
	\State $x.rank = 0$
\EndProcedure
\Statex
\Procedure{UNION}{$x,y$}
	\State \Call{LINK}{\Call{FIND-SET}{$x$},\Call{FIND-SET}{$y$}}
\EndProcedure
\Statex
\Procedure{LINK}{$x,y$} \Comment{assuming $x,y$ belong to different sets}
	\If{$x.rank > y.rank$}
		\State $y.p = x$
	\Else
		\State $x.p = y$
		\If{$x.rank == y.rank$}
			\State $y.rank = y.rank + 1$
		\EndIf
	\EndIf
\EndProcedure
\Statex
\Procedure{FIND-SET}{$x$}
	\If{$x.p \neq x$} \Comment{if $x$ is not a root}
		\State $x.p =$ \Call{FIND-SET}{$x.p$} \Comment{I update $x.p$ recursively until the root}
	\EndIf
	\State \Return $x.p$
\EndProcedure
\Statex
\end{algorithmic}

* Disjoint-sets are useful for the representation of dynamic sets that grow over time
* A disjoint-set forest implementing the heuristics union-by-rank and path compression reaches an almost constant $O(\alpha(n))$ amortized running time per operation
* The dishoint-sets representation of connected components does not support the removal of edges, but only their addition
* Many of the results for disjoint-sets are due to the american scientist Robert E. Tarjan

## Dynamic programming
* Divide-et-impera solve problems recursively in a top-down way
	* It is efficient when subproblems are disjoint and balanced
* Dynamic programming avoids to solve repeatedly the same sub-problem by storing the solution of sub-problems in a table
	* It works from the bottom-up and it is typically used for optimization problems
* In an optimization problem I want to find the solution $S^*$ such that its value $\phi(S^*)$ is minimal/maximal (according to the problem) in the set of possible solution values
$$S^* = argmax_S(\{\phi(S)\ |\ S \mbox{ is a solution of }P\})$$
* The value of an optimal solution $\phi(S^*)$ is called optimal value
* I should use dynamic programming on a problem $P$ when
	* The problem $P$ has optimal substructure
	* The subproblems of $P$ are independent and overlapping
	* There is a polynomial number of subproblems $P_1...P_k$
	* Deriving $S^*$ from $S_1^*...S_k^*$ requires polynomial time

### Longest common subsequence
* A sequence $X = \langle x_1, x_2, ..., x_m \rangle$ is a subsequence of the sequence $Y = \langle y_1, y_2, ..., y_n \rangle$ if it is possible to obtain $X$ from $Y$ by removing some elements $y_{i_1},...,y_{y_k}$
$$ subseq(X,Y) \iff \exists \ i_1,...,i_k \ : \ \forall \ j \in \{1,...,k\} \ :\ x_{i_j} = y_{i_j}$$
* For $X$ to be a subsequence of $Y$, the elements ion $X$ must appear in the same order as the elements in $Y$, but they are NOT required to be contiguous in $Y$
* The empty sequence $\langle \ \rangle$ is a subsequence of every sequence
* A string is a sequence of characters drawn from a given alphabet $\Sigma$
* A string $\langle c_1,...,c_m \rangle\ :\ c_i \in \Sigma^*$ is conventionally represented as $c_1 \cdot \cdot \cdot c_m$
	* The string $\langle h,e,l,l,o \rangle$ is represented as $hello$
* The empty string is represented with $\epsilon$
$$ \epsilon = \langle \ \rangle$$
* Given the sequences $X$ and $Y$ we say that $Z$ is a common subsequence of $X$ and $Y$ ($CS_{X,Y}$) if it is a subsequence of both
$$ CS_{X,Y} = \{Z\ |\ subseq(Z,X)\ \land\ subseq(Z,Y)\}$$
* $Z$ is a longest common subsequence of $X$ and $Y$ ($LCS_{X,Y}$) if it is a common subsequence of maximal lenght
$$ LCS_{X,Y} = \{Z \in CS_{X,Y}\ |\ \forall\ Z' \in CS_{X,Y}\ |Z| \geq |Z'|\}$$
* All the longest common sequences of 2 sequences are of the same length
$$ |Z| = |Z'| \ \forall\ Z,Z' \in LCS_{X,Y}$$
* The longest common subsequence problem consists in finding, given 2 sequences $X$ and $Y$, a longest common subsequence $Z \in LCS_{X,Y}$
	* Note that $\exists \ LCS_{X,Y} \ \forall \ X,Y$ since $\epsilon  = \langle \ \rangle \in CS_{X,Y} \ \forall \ X,Y$
	* There can be more than 1 LCS for a given pair of sequences
$$ |LCS_{X,Y}| \geq 1 \ \forall \ X,Y$$
	* In some cases we are interested in finding how many LCS there are among 2 sequences ($|LCS_{X,Y}|$), and not in finding the structure of any particolar LCS
* A brute force approach for the LCS problem requires to enumerate all of the possible $2^m$ subsequences of $X$ and checking wether they occur in $Y$ 
	* The worst-case running time is $O(n 2^m)$ where $m = |X|$ and $n = |Y|$
* Dynamic programming can drammatically reduce the time required for solving the LCS problem
* I can show that the LCS problem has an optimal substructure
	* I can define the $i$-th prefix of the sequence $X = \langle x_1,...,x_m \rangle$ as the subsequence $X_i = \langle x_1,...x_i \rangle$ with $i = 0,...,m$
$$ X_0 = \langle \ \rangle$$
$$ X_1 = \langle x_1 \rangle$$
$$ X_2 = \langle x_1,x_2 \rangle$$
$$ X_i = \langle x_1,..,x_i \rangle$$
$$ X_m = \langle x_1,..,x_m \rangle = X$$
	* I observe that, given $X = \langle x_1,...,x_m \rangle$, $Y = \langle y_1, y_2, ..., y_n \rangle$, and $Z = \langle z_1,...,z_k \rangle \in LCS_{X,Y}$
		* If $x_m = y_n$ then $z_k = x_n = y_m$ and $Z_{k-1}$ is an LCS of $X_{m-1}$ and $Y_{n-1}$
		* If $x_m \not= y_n$ and $z_k \not= x_m$ then $Z$ is an LCS of $X_{m-1}$ and $Y$
		* If $x_m \not= y_n$ and $z_k \not= y_n$ then $Z$ is an LCS of $X$ and $Y_{n-1}$
	* These statements can be prooven by contradiction assuming the negation of the aforementioned property $\lnot \mathbb{P}$
	* For the first statement, I assume by contradiction that $x_m = y_n \land z_k \not = x_m$
		* I can then append $x_m = y_n$ to $Z$ to get $Z'=\langle z_1,...,z_k,x_m \rangle \in LCS_{X,Y}$
		* Therefore, $Z'$ will be $k+1$ characters long: $|Z| = k+1$
		* This is impossible since $|W| = k \ \forall \ W \in LCS_{X,Y}$
	* For the second statement I assume by contradiction that $z_k \not= x_m$ and there is a sequence $W$ such that $W\in LCS_{X_{m-1},Y} \land |W| > |Z|$, where $Z = LCS_{X,Y}$
		* In this case then must be that $W \in LCS_{X,Y}$, which contradicts the assumption that $Z \in LCS_{X,Y}$
	* The third statement is symmetric to the second
	* Therefore, the LCS of 2 sequences contains the LCS of their subsequences: we have an optimal substructure
* I can define the LCS of 2 sequences recursively because of the theorems stated above
$$LCS_{X,Y} = \begin{cases}\epsilon = \langle \ \rangle & \mbox{if } m = 0 \lor n=0 \\ LCS_{X_{m-1},Y_{n-1}} \cdot x_m & \mbox{if } x_m = y_n \\ max(|LCS_{X_{m-1},Y}|,|LCS_{X,Y_{n-1}}|) & \mbox{otherwise}\end{cases}$$
* The LCS problem can involve many overlapping subproblems
	* If $m_m \not= y_n$ finding first $LCS_{X_{m-1},Y}$ and then from that $LCS_{X,Y_{n-1}}$ leads to calculating $LCS_{X_{m-1},Y_{n-1}}$, which is calculated directly also from $X,Y$ when $x_m = y_n$
	* This case happens for any $X_i,Y_j$ with $i=2,...,m$ and $j=2,...,n$
* I can create a dynamic programming table $C(i,j)$ of dimensions $\Theta(mn)$ such that
$$C(i,j) = \begin{cases} 0 & \mbox{if } i = 0 \lor j=0 \\ C(i-1,j-1)+1 & \mbox{if } x_i = y_j \\ max(C(i-1,j),C(i,j-1)) & \mbox{otherwise}\end{cases}$$
$$ i = 0,...,m \qquad j = 0,...,n$$
* After computing the whole table, $C(m,n)$ will contain the lenght of the LCS of $X$ and $Y$
$$ C(m,n) = |LCS_{X,Y}| \qquad m=|X|,\ n=|Y|$$
* The table $C$ can be filled iteratively by starting from $C(0,0)$
* In order to reconstruct the solution of the LCS problem we need to use a backtrack table $B(i,j)$ such that
$$B(i,j) = \begin{cases}MATCH & \mbox{if } x_i = y_j \\ UP & \mbox{if } C(i-1,j) \geq C(i,j-1)) \\ LEFT & \mbox{otherwise}\end{cases}$$
$$ i = 0,...,m \qquad j = 0,...,n$$
* Note that $S$ will contain the reverse of an LCS of $X$ and $Y$
$$ inv(S) \in LCS_{X,Y}$$
* The solution can be reconstructed by starting from $B(m,n)$ and iterating until $i=0 \lor j=0$, building the solution $S$ as
$$\begin{cases} B(i,j) = MATCH \implies S=S \cdot x_i,\ i=i-1,j=j-1 \\ B(i,j) = UP \implies i=i-1 \\ B(i,j)=LEFT \implies j=j-1\end{cases}$$
* I can now define the function LCS-LENGTH($X,Y$) that returns the corresponding $C$ and $B$ tables
	* Its cost is $O(mn)$ since I need to fill the tables $B$ and $C$ which have dimensions $O(mn)$

\begin{algorithmic}
\Statex
\Procedure{LCS-LENGTH}{$X,Y$}
	\State $m = X.lenght$
	\State $n = Y.lenght$
	\State let $C(0...m,0...n)$ and $B(1...m,1...n)$ be two new tables
	\For{$i=0,...,m$}
		\For{$j=0,...,n$}
			\If{$x_i=0 \lor y_j=0$}
				\State $C(i,j) = 0$
			\ElsIf{$x_i == y_j$}
				\State $C(i,j) = C(i-1,j-1)+1$
				\State $B(i,j) = MATCH$
			\ElsIf{$C(i-1,j) \geq C(i,j-1)$}
				\State $C(i,j) = C(i-1,j)$
				\State $B(i,j) = UP$
			\Else
				\State $C(i,j) = C(i,j-1)$
				\State $B(i,j) = LEFT$
			\EndIf
		\EndFor
	\EndFor
	\State \Return $B,C$
\EndProcedure
\Statex
\end{algorithmic}

* The function PRINT-LCS($B,X,i,j$) prints a sequence $\in LCS_{X,Y}$ using the $B$ table
	* Its initial call is PRINT-LCS($B,X,m,n$)
	* Note that since the function is recursive the LCS is printed in the correct order! 
	* Its cost is $O(m+n)$ since at each step either $i$ or $j$ is decreased, and at most I can have $m$ steps in which $i$ is reduced and $n$ steps in which $j$ is reduced

\begin{algorithmic}
\Statex
\Procedure{PRINT-LCS}{$B,X,i,j$}
	\If{$i==0 \lor j==0$}
		\Return
	\ElsIf{$B(i,j)== MATCH$}
		\State \Call{PRINT-LCS}{$B,X,i-1,j-1$}
		\State \Call{PRINT}{$x_i$}
	\ElsIf{$B(i,j) == UP$}
		\State \Call{PRINT-LCS}{$B,X,i-1,j$}
	\Else
		\State \Call{PRINT-LCS}{$B,X,i,j-1$}
	\EndIf
\EndProcedure
\Statex
\end{algorithmic}

* Note that the $B$ table speeds up the reconstruction of the solution but it is redundant
	* If space is an issue I can avoid storing it and re-calculate the backtrack path (at a time cost)
* If I am only interested in $|LCS_{X,Y}|$ I can avoid filling $B$ without worries and I can at any time store only 2 rows of $C$

### Approximate string matching
* The string matching problem: I want to find occurrences of a query string $P=p_1 \cdot \cdot \cdot p_m$ called pattern in a target string $T = t_1 \cdot \cdot \cdot t_n$ with $m \leq n$
* A k-approximation of a string $P = p_1 \cdot \cdot \cdot p_m$ is a string $P'=p_1' \cdot \cdot \cdot p_m'$ that can be obtained from the $P$ by performing $0 \leq k \leq m$ edit operations
	* $k$ is defined as the edit distance between $P$ and $P'$
* An edit operation is one of the following
	* A substitution where a character $p_i$ is replaced by the character $p_i'$
	* An insertion where a new character $p_i'$ is added
	* A deletion where a character $p_i$ is removed from $P$
* Approximate string matching (ASM) takes in input the strings $P$ and $T$ and it returns a k-approximation $P'$ of $P$ in $T$ with minimum $k$
	* Note that all the approximations $P'$ with minimum $k$ that occur in $T$ are solution to the ASM problem, regardless of their length
* Let now $P'$ be a k-approximated occurrence of $P$ in $T$ with minimum $k$
* I can compute $P'$ by defining a table $D$ where $D(i,j)$ is the minimum $k$ for which a k-approximation of the prefix $P_i$ in the prefix $T_j$ exists
$$D(i,j) = \begin{cases} 0 & \mbox{if } i=0 \\ i & \mbox{if } j=0 \\ min(D(i-1,j-1)+\delta_{ij},D(i-1,j), D(i,j-1))+1 & \mbox{otherwise}\end{cases}$$
$$\delta_{ij} = \begin{cases} 0 & \mbox{if } p_i=t_j \\ 1 & \mbox{otherwise}\end{cases}$$
$$ i = 0,...,m \qquad j = 0,...,n$$
	* The value $D(i,j)$ remains equal to $D(i-1,j-1)$ if $p_i = t_j$
	* If $p_i \not= t_j$, the cell from which $D(i,j)$ is derived is choosen so to minimize its final value
	* Note how the ASM problem shows optimal substructure
	* $D(0,j) = 0 \ \forall\ j=0,...,n$ since the prefix $P_0 = \epsilon$ occurs in any possible substring $T_j$
	* $D(i,0) = i \ \forall\ i=0,...,m$ since to match $P_i$ with $T_0$ I need to delete all the characters in $P_i$
	* $D(m,j)$ contains the minimum $k$ for a k-approximation of $P$ in $T_j$
	* The minimum value $k^*$ for a k-approximation of $P$ in $T$ is the smallest value of the last row (except the trivial $i=0$, where $k=|P|$)
$$ k^* = min\{D(m,j)|j=1,...,n\}$$
* I can define the function APP-STR-MATCH($P,T$) that returns $k^*$ and the prefix $T_j$ on which it was obtained
	* This algorithm costs $O(mn)$ similarly to the LCS algorithm and we can use a backtrack matrix to build the solution
* To build the solution I follow the backtrack matrix from the cell corresponding to the minimal value in the last row of the matrix $D$ 
	* Each direction on the backtrack matrix indicates what kind of edit operation must be performed
	* A special direction can be inserted in the matrix for when $p_i = t_j$ and $D(i-1,j-1)$ was the minimal value choosen,
		* In this case no edit needs to be performed

\begin{algorithmic}
\Statex
\Procedure{APP-STR-MATCH}{$P,T$}
	\State $m = P.lenght$
	\State $n = T.lenght$
	\State let $D(0...m,0...n)$ be a new table
	\For{$i=0,...,m$}
		$D(i,0)=i$
	\EndFor
	\For{$j=0,...,n$}
		$D(0,j)=0$
	\EndFor
	\For{$i=1,...,m$}
		\For{$j=1,...,n$}
			\If{$p_i == t_j$}
				\State $\delta_{ij}=0$
			\Else
				\State $\delta_{ij}=1$
			\EndIf
			\State $sub = D(i-1,j-1)+\delta_{ij}$
			\State $del = D(i-1,j)+1$
			\State $ins = D(i,j-1)+1$
			\State $D(i,j)=min(sub,del,ins)$
		\EndFor
	\EndFor
	\State $k=0$
	\For{$i=0,...,n$}
		\If{$D(m,i) < k$}
			\State $k=D(m,i)$
			\State $j=i$
		\EndIf
	\EndFor
	\State \Return $j,k$
\EndProcedure
\Statex
\end{algorithmic}

### Related problems
* Dynamic programming can be applied to many problems related to finding the longest common subsequent and to approximate string matching, but it is not necessarily the best approach
* The longest common substring problem is similar to the longest common subsequence problem but with the further constraint that the common characters must be contiguous (they must be a substring, not a subsequence!)
* Exact string matching is similar to approximate string matching but it requires the edit distance $k$ to be 0
* Minimum edit distance is similar to ASM but it requires that the $P'$ approximation found be equal to $T$
	* It is the problem of finding the minimum number of edits that can transform $P$ in $T$

## Greedy algorithms
* An optimization algorithm typically go through a series of steps $S_1,...,S_n$ where at each step $S_i$ I can have different choices $C_{i_1},...,C_{i_m}$
* Dynamic programming evaluates all the possible choices at each step in a bottom-up fashion, avoiding to re-evaluate the same choice multiple times
* Dynamic programming guarantees to find a globally optimal solution if its assumptions are respected
* However, sometimes a simpler and more efficient greedy approach suffices for our problem
* Greedy algorithms make a single choice $C_{i^*}$ that is locally optimal at each step without considering all the possible choices
* Greedy algorithms first appeared in a 1971 paper form Jack Edmonds "Matroids and the greedy algorithm"
* A greedy approach is based on the hope that a sequence of locally optimal choice will bring to a globally optimal solution
	* This is NOT guaranteed to be true, and in general greedy algorithms are NOT guaranteed to find a globally optimal solution
* However, if our problem shows the 2 following properties it is possible to develop a globally optimal greedy algorithm
	* The problem shows optimal substructure
	* The problem exhibits the greedy-choice property: I can get a globally optimal solution by making always locally optimal choices
* Any problem that can be solved by a greedy approach can also be solved by dynamic programming, but DP is typically slower than a greedy algorithm in these cases
* Given an input set of objects $X$, a greedy strategy selects an hopefully optimal subset $S \subseteq X$
* The solution $S$ is built incrementally, adding at each step the locally optimal object $x \in X$ according to an optimality criterion $c$

\begin{algorithmic}
\Statex
\Procedure{GREEDY}{$X,c$}
	\State $S = \emptyset$
	\For{$x \in X$}
		\If{$c(x,X,S)$} \Comment{I may also want to sort $X$ according to $c$}
			\State $S = S \cup \{x\}$
		\EndIf
	\EndFor
	\State \Return $S$
\EndProcedure
\Statex
\end{algorithmic}

* In a greedy algorithm decisions are take from the top-down and do not depend on sub-problems
* Advantages of a greedy strategy
	* It is easy and intuitive to design
	* It is pretty efficient
	* It is globally optimal if the probelm has optimal substructure and it exhibits the greedy choice property
	* Even when it gives a sub-optimal solution, for some problems this can be acceptable!
		* This is true especially when I can give a bound to the distance between the greedy solution and the globally optimal solution
* Disadvantages of a greedy strategy
	* Only few problems exhibit the greedy choice property

### Minimum spanning tree
* The minimum spanning tree problem is formulated as follows: given a connected, undirected, and
weighted graph $G = (V, E)$ with weight function $w : V \times V \to E$, return a minimum spanning tree
(MST) $T \subseteq E$ such that
	* $T$ is a connected, undirected and acyclic graph (it is a tree!)
	* $T$ connects all the nodes in $V$ (it is a spanning tree!)
$$\exists u \leadsto v \in T \qquad \forall \ u, v \in V$$
	* The weight of $T$ is minimal: there is no other spanning tree $T_0$ with weight smaller than that of $T$
$$\nexists T' : w(T') < w(T) \qquad w(T) = \sum_{(u,v) \in T} w(u,v)$$
* The minimum spanning tree probelm is relevant for many applications
	* Designing an electronic circuit with the least amount of wire
	* Constructin a minimum ultrametric tree
* The MST problem can be optimally solved with a greedy strategy
* An MST always exists for a connected and undirected graph, but it may not be unique
* The greedy algorithm for obtaining a MST starts from an empty tree $T = \emptyset$ add adds to it a safe edge $(u,v)$ at a time
$$ T_i = \begin{cases} T_{i-1} \cup \{(u,v)\} & \mbox{for } i > 0 \\ T_i = 0 & \mbox{for } i = 0 \end{cases}$$
* An edge $(u,v)$ is safe for $T_i$ iff the tree resulting from adding it to $T_i$ is a subset of some MST $T$
$$(u,v) \mbox{ is safe } \iff T_i \cup \{(u,v)\} \\subseteq T$$

\begin{algorithmic}
\Statex
\Procedure{GENERIC-MST}{$G$}
	\State $T_0 = \emptyset$
	\While{$T_i$ is not an MST for $G$}
		\State find $(u,v) \in G.E - T_i$ such that $(u,v)$ is safe for $T_i$
		\State $i = i + 1$
		\State $T_i = T_i-1 \cup \{(u, v)\}$
	\EndWhile
\State \Return $T_i$
\EndProcedure
\Statex
\end{algorithmic}

* A cut $(S, V - S)$ of $G=(V, E)$ is a partition of $V$
* An edge $(u,v)$ crosses the cut $(S, V - S)$ if $(u \in S \land v \in V - S)\lor(v \in S \land u \in V - S)$
* A cut $(S,S-V)$ respects a set of edges $A \subseteq E$ if no edge in $A$ crosses the cut
* An edge $(u,v)$ crossing a cut $(S,V-S)$ is a light edge if $w(u,v)$ is minimal among all the edges crossing the cut
* Let $G=(V,E)$ be a connected, underected graph with weight function $w$
* Let $A \subseteq T$ be the subset of some MST $T$ for $G$
* If $(S,V-S)$ is a cut repsecting $A$ and if $(u,v)$ is a light edge crossing the cut, then $(u,v)$ is safe for $A$
	* I know that $A \subseteq T$, but I have to prove that $(u,v)$ is safe for $A$
	* Proving that $(u,v)$ is safe for $A$ means proving that adding $(u,v)$ to $A$ I get a subset of some MST $T$
$$A \cup \{(u,v)\} \subseteq T$$
	* If $(u,v) \in T$ I am done since $A\subseteq T$ and so $A\cup\{(u,v)\} \subseteq T$
	* If $(u,v) \not\in T$ I build a spanning tree $T'=(T-\{(u',v')\})\cup\{(u,v)\}$ where $(u',v') \not\in A$ is an edge on the path $u \leadsto v$
	* I note that $w(T')=w(T)-w(u',v')+w(u,v)$ and $(u,v)$ is light, so $w(T')\leq w(T)$
	* I also know that $T$ is a MST so $w(T')\geq w(T)$
$$ w(T') \leq w(T) \land w(T') \geq w(T) \implies w(T')=w(T)$$
	* Since $w(T')=w(T)$, I conclude that $T'$ is a MST
	* Since $A \subseteq T$ and $(u',v') \not\in A$ I have that $A \subseteq T-\{(u',v')\}$ and thus $A \cup\{(u,v)\}\subseteq (T-\{(u',v')\})\cup\{(u,v)\}=T'$
* Thanks to this theorem, I can build a MST by adding safe edges to a smaller MST

#### Kruskal algorithm
* The Kruskal algorithm is a possible implementation of the GENERIC-MST algorithm seen above
* I grow and merge forests of MSTs by incrementally adding safe edges until the final MST is computed
* The algorithm is greedy since at each steps it adds to the forest the edge with minimal weight 
* It is possible to implement the Kruscal algorithm with the disjoint-set data structure
	* I represent each MST as a disjoint-set, where each MST node is an element of the set
	* FIND-SET and UNION operations are used to determine whether to merge disjoint sets
* If $n=|V|$ and $m=|E|$, I have the following time costs
	* MAKE-SET costs in total $O(n)$
	* SORT costs in total $O(m \log m)$
	* FIND-SET and UNION are performed $m$ times so their total cost is $O(m \alpha(n)) \approx O(m)$ using path compression and union-by-rank
	* The overall cost is $O(m \log m)$

\begin{algorithmic}
\Statex
\Procedure{MST-KRUSCAL}{$G$}
	\State $A = \emptyset$
	\ForAll{$v \in G.V$}
		\State MAKE-SET($v$) \Comment{I create $|V|$ trees}
	\EndFor 
	\State $S =$ \Call{SORT}{$G.E, w$} \Comment{sort edges non-decreasingly according to their weight}
	\ForAll{$(u,v) \in S$}
		\If{\Call{FIND-SET}{$u$} $\neq$ \Call{FIND-SET}{$v$}} \Comment{if $u$ and $v$ are on different trees}
			\State $A = A \cup {(u,v)}$
			\State \Call{UNION}{$(u,v)$}
		\EndIf
	\EndFor
	\State \Return $A$
\EndProcedure
\Statex
\end{algorithmic}

#### Other MST algorithms
* Kruskal's algorithm is not the only MST algorithm known
* Prim's MST algorithm works similarly to the Dijkstra algorihtm for the shortest path in a graph and it has the same asymptotic complexity of Kruscal's algorithm ($O(m \log m)$)
* Fredman and Tarjan's MST algorithm is based on the Fibonacci heap and runs in $O(m+n \log n)$
* Karger, Klein and Tarjan's MST randomized algorithm runs in $O(m+n)$
* Fredman and Willard's MST algorithm is not based on comparisons and runs in $O(m+n)$

### Optimal greedy algorithms
* Greedy algorithms can find the globally optimal solution for other problems besides MST in polynomial time
* Huffman codes: given an alphabet $\Sigma$ and weights $w : \Sigma \to \mathbb{R}$ return a prefix code with codewords of minimum lenght
* Activity selection: given $n$ activities $S=\{a_1,...,a_n\}$ having start and finish times $(s_i,e_i)$ select a maximum-size set $T \subseteq S$ of non-overlapping activities to be executed
* Fractional knapsack: given objects $O_1,...,O_n$ where $O_i$ has value $v_i$ and weight $w_i$, and a knapsack of capacity $W$, select an amount $x_i \in [0,1]$ for each object $O_i$ such that $\sum_{i=1}^n w_ix_i \leq W$ and the total value $\sum_{i=1}^n v_ix_i$ is maximal
	* It is a generalization of the 0-1 knapsack problem in which $x_i \in {0,1}$

### Non-optimal greedy algorithms
* For several problems greedy algorithms exist but they do not find a globally optimal solution
* Change-making: given $n > 0$, return the smallest number of coins whose total value adds up to $n$
	* The greedy approach involves sorting the coins in decreasing value order and, at each step, using the largest number of coins from the current value
	* It is a particular case of the $O,1$ knapsack problem where each object has the same value (I want to minimize the number of objects)
* Set-cover: given an universe $U = \{1,...,n\}$ and a set of sets $S = \{S_1,...,S_m\}$ such that $\cup_{i=1}^m S_i = U$ identify the smallest set $C \subseteq S$ such that $\cup_{S_i \in C} S_i = U$
	* The greeady approach is to always choose the set $S_i$ that contains the biggest number of elements not yet in a set $S_k$ already in $C$
	* The greedy strategy is not optimal but guarantees that the solution found $C$ will be at most $O(\log n)$ bigger than the optimal solution $C^*$

## Local search
* Local search is yet another approach to tackle optimization problems
* It starts from a feasible solution $S$ and searches for a better solution $S'$ in the neighborod $N(S)$ of $S$
	* This approach is then iterated on $S'$ to obtain $S''$, and so on
* Local search converges on a local optimum, that may or may not correspond to a global optimum
	* Because of this we say that local search is not complete
* Formally we can define local serach in the following way
	* Let $\zeta$ be the set of solutions for a given problem
	* I define a neighborhood function $N : \zeta \to 2^\zeta$ such that $N(S)=\{S,S_1,...,S_k\}$ is the neighborhood of the solution $S \in \zeta$
		* The codomain of $N(S)$ is $2^\zeta$ since it produces 1 of the $2^\zeta$ possible subsets of solutions from the set of all possible solutions $\zeta$
	* I define a transition function $\delta_N$ for each neighborhood $N(S)$ such that $\delta_N(S) \in N(S)$ is the next solution to explore after $S$
		* $\delta_N(S)$ is 1 of the solutions in $N(S)$
		* When there are no more solutions to explore in $N(S)$, then $\delta_N(S)=S$
		* If $n=|N(S)|$, there are $n!$ possible transition functions for $N(S)$
	* I define a cost function $\phi : \zeta \to \mathbb{R}$ to rank the solutions $S \in \zeta$
$$ \phi(S) < \phi(S') \iff S \mbox{ is better than } S'$$
	* The solution $S^*$ is a local optimum for $N(S)$ iff its cost is minimal among all the solutions in $N(S)$
$$ S^* : \phi(S^*) = min\{\phi(S')|S' \in N(S)\}$$
* The local optimum on which a local search converges depends on the starting solution $S_0$
* A general local search algorithm looks like this

\begin{algorithmic}
\Statex
\Procedure{LOCAL-SEARCH}{$S_0,N,\delta_N,\phi$}
	\State $S^* = S_0$
	\While{$N(S) \not= {S^*}$}
		\State $S=S^*$
		\While{$\phi(S) \geq \phi(S^*)$ and $\delta_N(S) \not= S$}
			\State $S=\delta_N(S)$
			\If{$\phi(S)<\phi(S^*)$}
				\State $S = S^*$
			\Else
				\State \Return $S^*$
			\EndIf
		\EndWhile
	\EndWhile
	\State \Return $S^*$
\EndProcedure
\Statex
\end{algorithmic}

* Many local search approaches have been developped: hill climbing, simulated annealing, tabu search, ...
* Local search has been effectively applied to a number of famous problems: minimum vertex cover, travelling saleseman problem, boolean satisfiability problem* Local search can be applied to sorting problems: insertion-sort, shell-sort, and bubble-sort can be seen as local search approaches that try to minimize conflicts (misplaced elements)

### Minimum spanning tree with local search
* It is possible to use local search to solve the MST problem
* Let $T$ be any spanning tree for the graph $G=(V,E)$ with cost function $w$
* I define $N(T)$ as the set of trees obtained from $T$ by adding an edge from the set of edges $E-T$ and removing an edge from the resulting circuit
	* Since $T$ is a spanning tree, adding an edge to it necessarily results in forming a circuit
	* In practice I am exchanging an edge in $T$ for an edge which is not in $T$
* I define the cost function $\phi(T)$ so to be equal to the weight of the tree $w(T)$
$$ \phi(T)=w(T)$$
* I can then use local search to possibly replace an edge from a spanning tree $T$ at each iteration until $T$ becomes a MST
* In any case, I replace the edge $(u,v)$ with the edge $(u',v')$ only if this reduces the weight of the tree $T$
* For the MST problem, local search is guaranteed to find the global optimum, but the Kruskal algorithm is faster

### Sorting with local search
* Local search can be used to sort a collection of elements by reframing the sorting problem as an optimization problem
* Given the sequence $A = \langle a_1,...,a_n \rangle$ I say that $(i,j)$ is a conflict for $A$ if $a_i > a_j$ while $i<j$
$$ (i,j) \mbox{ is a conflict for } A \iff 1\leq i < j \leq n \ \land \ a_i > a_j$$
$$A = \langle a_1,...,a_n \rangle$$
* If $(i,j)$ is a conflict for $A$, then $a_i$ and $a_j$ are conflicting elements with distance $j-i$
* The problem of sorting the sequence $A = \langle a_1,...,a_n \rangle$ can rephrased as the problem of finding a permutation $A'$ of $A$ having minimal number of conflicts
* The sequence $A$ is sorted when it has 0 conflicts
* The neighborhood of $A$ is defined as the set of all the permutations of $A$ that can be obtained by swapping 2 conflicting elements
* If $A = \langle a_1,...,a_n \rangle$ and $\pi_{i,j}(A)$ is the sequence obtained by swapping $a_i$ and $a_j$, then I can defined the neighborhood of $A$, $N(A)$ as
$$N(A)=\{\pi_{i,j}(A)|i<j \land a_i>a_j\}$$
* The cost function $\phi(A)$ can be then defined as the number of conflicts in $A$ (the numerosity of the set of all the conflicts in $A$)
$$\phi(A)=|\{(i,j)|i<j \land a_i > a_j\}|$$
* In this case, the transition function $\delta_N(A)$ defines how the array is sorted at each step

#### Insertion sort
* Insertion sort is not explicitly local search-based, but it follows a similar logic
$$ \delta_N(A)=\pi_{i,i+1}(A) \qquad \mbox{where } i = min(\{k|a_k > a_{k+1}\})$$
	* It recognizes the first conflict $min(\{k|a_k > a_{k+1}\})$ among consecutive elements $a_k,a_{k+1}$ and swaps the offending elements
* Insertion sort is simple and efficient when the sequence to be sorted $A$ is small

\begin{algorithmic}
\Statex
\Procedure{INSERTION-SORT}{$A$}
	\For{$i = 2$ to $A.lenght$}
		\State $k = A[i]$
		\State $j = i$
		\While{$j > 1$ and $A[j-1] > k$}
			\State $A[j] = A[j-1]$
			\State $j=j-1$
		\EndWhile
		\State $A[j] = k$
	\EndFor
\EndProcedure
\Statex
\end{algorithmic}

* The loop invariant in this pseudocode is that $\langle A[1],...,A[i] \rangle$ is always sorted after the $i$-th iteration of the for loop
* The cost of insertion-sort depends on the number of conflicts in $A$
	* In the best case, when $A$ is already sorted, the cost is $O(n)$
	* In the worst case, when $A$ is in reversed sorted order, there are $\frac{n^2-n}{2}$ conflicts and the running time becomes $O(n^2)$

#### Shell sort
* We can see that insertion-sort works like a local search by gradually reducing the muber of conflicts but
	* Only pairs contiguous elements are considered
	* Only 1 conflict is resolved at each step
* Shell-sort was proposed by Donald L. Shell in 1959 to overcome these limitations of insertion-sort
* Shell-sort is a generalization of insertion-sort by considering the elements $a[i],a[i+h]$ at distance $h \geq 1$ from each other on the sequence
	* $h$ is decreased at each iteration until eventually shell-sort becomes equivalent to insertion-sort when $h=1$
	* Shell-sort is correct only if, eventually, $h$ becomes 1
* We can see shell-sort as a local search approach where
$$ \delta_N(A)=\pi_{i,i+h}(A) \qquad \mbox{where } i = min(\{k|a_k > a_{k+h}\})$$
* In practice shell-sort at each iteration sorts distinct subsequences where the elements are $h$ apart from each other
$$\langle a_1,a_{h+1},a_{2h+1},... \rangle,\langle a_2,a_{h+2},a_{2h+2},... \rangle,...$$
* Then, after having sorted all such subsequences it decreases $h$ and repeats, until eventually $h=1$ and it becomes equal to insertion-sort and $A$ is thus sorted
* The variable $h$ can be reduced in different steps
* A commonly used approach is to reduce $h$ by dividing it by 3 and taking the floor of the result
$$h_{k+1} = \lfloor h_k/3 \rfloor$$
* In this case the sequence of $h$ values will be
$$h = ...,1093,264,121,40,13,4,1$$

\begin{algorithmic}
\Statex
\Procedure{SHELL-SORT}{$A$}
	\State $h = 1$
	\While{$h \leq A.lenght$}  \Comment{I generate the starting value for $h$}
		\State $h = 3*h+1$
	\EndWhile 
	\State $h = \lfloor h/3 \rfloor$ \Comment{in the last while iteration $h$ can become bigger than $A.lenght$}
	\While{$h \geq 1$}
		\State \Comment{the while loop only updates $h$, I want to stop after $h = 1$, when the algorithm is correct}
		\For{$i = h+1$ to $A.lenght$} \Comment{$i=h+1,h+2,h+3,...,A.lenght$}
		\State $k = A[i]$ \Comment{$k$ is the forward element of the pair checked}
		\State $j = i$
			\While{$j > h$ and $A[j-h] > k$}
				\State \Comment{$j=i,i-h,i-2h,...$ until I cannot decrease any more since $j<h$ and so $i-xh < 0$}
				\State \Comment{note that $j-h$ is the value of $j$ at the next iteration}
				\State \Comment{I compare $A[j-h]$ with $k=A[i]$ and stop when $A[j-h]$ is smaller than $A[i]$}
				\State \Comment{Since $i \geq j$ the elements are NOT conflicting when $A[j-h]$ is smaller than $k$}
				\State $A[j] = A[j-h]$
				\State \Comment{At the first iteration $A[j]=A[i]=k$ so I am not loosing the value of $A[j]$}
				\State \Comment{At the next iterations I am shifting $A[j-h]$ $h$ positions ahead to make space for placing $A[i]$}
				\State $j = j - h$
			\EndWhile
			\State \Comment{the while ends when either I came to the beginning of the array or I found the correct place for $k$ in the sequence $A[i],A[i-h],A[i-2h],...$}
		\State $A[j] = k$
		\State \Comment{at this point I place $k$ in $A[j]$, which has already been copied to $A[j+h]$}
		\State \Comment{$A[j]$ is the old $A[j-h]$ of the while loop!}
		\EndFor
		\State $h =\lfloor h/3 \rfloor$ \Comment{update $h$ for the next round}
	\EndWhile
\EndProcedure
\end{algorithmic}

* The complexity of shell-sort depends on the gap sequence adopted
* Using the sequence $h_{k+1} = \lfloor h_k/3 \rfloor$ the complexity is usually $O(n^{1.5})$
* Using other sequences, it can be from $O(n^{1.25})$ to $O(n \log^2 n)$
* Shell-sort is the most efficient sorting algorithm for short ($n < 5000$) sequences
* For long sequences ($n > 5000$) quick-sort is better, provided that some optimizations are implemented (iterative algorithm with random pivot, Bertossi et al.)

## Backtracking
* The general idea of backtracking is to try a solution, check if it is feasible and if not go back and try a new solution
* The term backtracking was coined by D.H. Lehmer in the 1950s
* Backtrack explores exhaustively the search space and halts either at a feasible solution or after having explored all the solutions to the problem
* It can be used for decision or optimization problems
	* In a decision problem all the solutions are equivalent
	* In an optimization problem solutiuons are ranked
* The time complexity of backtracking is typically high (exponential) since it is linear to the magnitude of the search space for the problem
	* A selected number of simple problems can be solved by a polynomial complexity backtracking approach
* Recursive backtracking works by generating and recursively visiting a search tree
	* When a leaf is reached if the solution is feasible the algorithm halts, if it is note it backtracks to the first node with yet unexplored branches
	* Its approach is similar to a tree visit or a DFS graph search
* Iterative backtracking uses a greedy strategy, but it possibly undoes some decisions
	* An example is the Knuth-Morris-Pratt algorithm for exact string matching
* Backtracking can be used for
	* Finding one feasible solution to a problem (e.g. for the $n\times n$ magic square problem)
	* Finding one optimal solution to a problem (e.g. for the 0-1 knapsack problem)
	* Counting all the feasible solutions to a problem (e.g. counting all the solutions to the $n$-queens problem)
		* Here I am ony interested in how many solutions there are
	* Enumerate all the feasible solutions to a problem (e.g generate all the subsets of size $k$ for a set of $n \geq k$ elements)
		* Here I am interested in the solutions themselves
* I can use bactracking to enumerate all the feasible solutions to a problem in the following way
	* I represent a solution with an array of decisions $S[1...n]$, where $S[i]$ is a decision take from a set $C$ of possible choices
	* The choices depend on the problem, and not all the choice lead to a feasible solution for the problem (i.e. a choice may lead to a dead end)
	* At each step $i \leq n$ I consider a partial solution $S[1...i]$
	* If $i=n$ and $S[1...i]$ is feasible, then I process the solution (print it or whatever)
	* If $i < n$ and $S[1...i]$ is feasible, I extend it to $S[1...i+1]$ with a new choice, and I recursively check $S[1...i+1]$
	* If $S[1...i]$ is NOT feasible I backtrack to the solution $S[1...i-1]$ and I explore a different solution (if any), otherwise I backtrack again from there
* A generic backtacking enumeration algorithm can look like this
	* The function CHOICES($S,i,n,...$) returns a set of possible choices for the decision $S[i]$, and it must return $\emptyset$ if $i > n$

\begin{algorithmic}
\Statex
\Procedure{ENUMERATE}{$S,i,n,...$} \Comment{the dots are for other optional problem-specific parameters}
	\State $C = CHOICES(S,i,n,...)$
	\For{$c \in C$}
		\State $S[i] = c$
		\If{$S[1...i]$ is feasible $\land i == n$}
			\State \Call{PROCESS}{$S,n,...$}
		\Else
			\State \Call{ENUMERATE}{$S,i+1,n,...$}
		\EndIf
	\EndFor
\EndProcedure
\Statex
\end{algorithmic}

* The following pseudocode enumerates all the $2^n$ subset of the set $S=\{1,...,n\}$
	* In this case there is no need to check for the feasibility of a solution, since all the solutions are feasible
	* The initial call is ALL-SUBSETS($S,1,n$)
	* I am describing a solution as a boolean vector for which an element is TRUE if the corresponding index is part of the current subset $S'$
$$ S[i]=TRUE \iff i \in S' \qquad \mbox{for } i = 1,...,n$$
	* The worst case time complexity is $O(2^n)$

\begin{algorithmic}
\Statex
\Procedure{ALL-SUBSETS}{$S,i,n$}
	\If{$i \leq n$}
		\State $C = \{FALSE,TRUE\}$
	\Else
		\State $C = \emptyset$
	\EndIf
	\For{$c \in C$}
		\State $S[i] = c$
		\If{$i == n$}
			\State \Call{PROCESS}{$S,n$}
		\Else
			\State \Call{ALL-SUBSETS}{$S,i+1,n$}
		\EndIf
	\EndFor
\EndProcedure
\Statex
\end{algorithmic}

* The following pseudocode enumerates all the $n \choose k$ subsets of $S=\{1,...,n\}$ composed of $k \leq n$ elements
	* The variable $j$ is used for counting the current number of elements for each subset
	* $k-j$ is the number of elements that must be added to reach a solution of the desired lenght $k$
	* $k-j$ cannot exceed the total number of elements remainin $n-i+1 = |\{i,i+1,...,n\}|$
		* This reduces the number of choices by pruning some dead branches
		* I cannot refuse more elements if then there are not enough elements remaining for completing a set of $k$ elements!
	* The worst case time complexity is $O(2^n)$

\begin{algorithmic}
\Statex
\Procedure{K-SUBSETS}{$S,i,j,k,n$}
	\If{$0 < k-j \leq n-i+1$}
		\State $C = \{FALSE,TRUE\}$
	\Else
		\State $C = \emptyset$
	\EndIf
	\For{$c \in C$}
		\State $S[i] = c$
		\If{$c$}
			\State $j = j+1$
		\EndIf
		\If{$j == k$}
			\State \Call{PROCESS}{$S,i$}
		\Else
			\State \Call{K-SUBSETS}{$S,i+1,j,k,n$}
		\EndIf
		\If{$c$}
			\State $j = j-1$
		\EndIf
	\EndFor
\EndProcedure
\Statex
\end{algorithmic}

* The following pseudocode enumerates all the $n!$ permutations of a set $A=\{a_i,...,a_n\}$
	* In this case there is no need to define explicitly a set of choices $C$
	* The time complexity is $O(n!)$

\begin{algorithmic}
\Statex
\Procedure{PERMUTATIONS}{$S,i,n,A$}
	\For{$c \in A$}
		\State $S[i] = c$
		\State $A = A - \{c\}$
		\If{$A = \emptyset$}
			\State \Call{PROCESS}{$S,n$}
		\Else
			\State \Call{PERMUTATIONS}{$S,i+1,n,A$}
		\EndIf
		\State $A = A \cup \{c\}$
	\EndFor
\EndProcedure
\Statex
\end{algorithmic}

## Hard problems
* A problem $Q$ is defined as a binary relation on a set $I$ of problem instances and a set $S$ of problem solutions
* A decision problem is a problem in which the set of solutions is $S=\{0,1\}$

* A problem is hard or untractable if it cannot be solved in polynomial time, while it is considered easy or tractable if a polynomial time algorithm able to solve it exists
	* History shows that if a polynomial time algorithm is discovered for a problem, it is usually of reasonable degree ($O(n^3)$ at most)
	* Even if only an high degree polynomial algorithm is discovered, then usually other more effcient polynomial algorithms of much lower degree are discovered
* A problem is said to be concrete if its input is a set of binary strings
* The input size of a concrete problem is the lenght of its binary input strings
* An abstract problem can be mapped to a concrete problem unsing an encoding
	* The choice of which encoding to use influences the running time, but if I rule out expensive encodings, then the running time is quite independent on the encoding used
* A verfier (also called certifier or checker) is an algorithm $A_{ver}$ such that, given a problem instance $P$ and a candidate solution $S$ for $P$, returns TRUE if $S$ is a valid solution for $P$, FALSE otherwise
$$ A_{ver} = \begin{cases}TRUE & \mbox{if $S$ is feasible for $P$}\\ FALSE & \mbox{otherwise}\end{cases}$$
	* A candidate solution $S$ for a problem instance $P$ is called a certificate or witness for $P$
	* A verifier does not solve the problem $P$, but only chekcs if a given solution is valid
* Let $P$ be a decision problem (its answer is either yer or no) such that
	* An polynomial algorithm $A_{ver}$ exists to verify if a candidate solution $S$ is feasible for $P$
		* The running time of $A_{ver}$ is $O(n^k)$ for some constant $k$
	* An exponential algorithm $A_{exp}$ exists to find a feasible solution $S$ for $P$ via exhaustive search
		* The running time of $A_{exp}$ is $O(k^n)$ for some constant $k$
	* There is no known polynomial algorithm $A_{poly}$ that can find a feasible solution $S$ for $P$
* The open question is: does such an algorith $A_{poly}$ exist, given that a polynomial verification algorithm $A_{ver}$ exists?
	* If the answer is YES, then all the problem for which a polynomial verification algorithm $A_{ver}$ is available can be solved in polynomial time
	* If the answer is NO, then these problems are intrinsically exponential and hard to solve
* The class **P** contains all the problems solvable in polynomial time
* The class **NP** contains all the problems verifiable in polynomial time
* It is obvious that **P** is contained in **NP**, since if I can find a solution to a problem in polynomial time, I don't need to verify that solution: I can just compute it ex-novo 
$$\mbox{P} \subseteq \mbox{NP}$$
* So far, it has not been proven if **P** and **NP** coincide: if all the problems verifiable in polynomial time are also solvable in polynomial time
* There is a million US dollar prize for showing that either $\mbox{P}=\mbox{NP}$ or $\mbox{P} \not= \mbox{NP}$
* The most difficult problems in **NP** are called NP-hard problems: they are at least as hard as the hardest problem in NP
	* **NP-hard** intersecates with **NP** but it is not a subset of it
	* Some NP-hard problems are also NP problems, while some NP-hard problems are not NP problems (i.e. they cannot be verified in polynomial time)
* A problem which is NP-hard and also belongs to **NP** is called NP-complete
	* **NP-complete** is the intersection of **NP** and **NP-hard**
$$\mbox{NP-complete} = \mbox{NP} \cap \mbox{NP-hard}$$
* If I can find a polynomial-time algorithm for a single NP-hard problem, then since all the NP problems are easier than it (by definition), a polynomial algorithm must exist for all the problems in **NP**
	* This would mean that $\mbox{P}=\mbox{NP}$
* If no polynomial time algorithm exist for a single NP-hard problem, then no polynomial time algorithm exists for all the NP-hard problems
	* This would mean that $\mbox{P}\not=\mbox{NP}$
	* This is considered the most likely, albeit sad, scenario
* Even though these classes refer to decision problems and not to optimization problems, I can easily reframe an optimization problem into a related decision problem by imposing a threshold on the score of an acceptable solution
* If I want to show that an optimization problem is NP-complete, I can show that the related decision problem is NP-complete
	* The optimization problem can be as hard or harder than its corresponding decision problem
	* If the decision problem is NP-complete the optimization problem must be hard
* I can show that a decision problem $A$ is not harder than another decision problem $B$ by finding an algorith that reduces any instance (i.e. all the inputs) of problem $A$ to a corresponding instance of problem $B$ such that
	* The transformation takes polynomial time
	* The answer to the transformed problem is the same that would have been obtained for the original problem
	* Such a procedure is called a polynomial time reduction algorithm
* Conversely, I can show that a problem $A$ is not easier than a problem $B$ for which its hardness has been proven
	* If I can reduce $B$ to $A$, and $B$ has been proven to be hard, then also $A$ is hard
	* This can be proven by contradiction: If $A$ was easy, then I can reduce $B$ to an easy problem, but $B$ has been proven to be hard adn so this is absurd
* A problem $A$ is NP-complete if it can be show that a polynomial reduction algorithm exists that can reduce $A$ to a problem $B \in \mbox{NP-complete}$
	* We do not know hard NP-complete problems are, but we know that they are all equal since they can be reduced into one another
* In order to show that a given problem is NP-complete, we must define a prototype NP-complete problem to which other problems must me reducable in order to show their NP-completeness
	* We will use the circuit satisfiability problem as a prototype NP-complete problem
* Any NP problem can be reduced in polynomial time to the boolean circuit satisfiability problem
	* As a consequence, the boolean circuit satisfiability problem is no easier than any problem in NP (and so it is NP-hard!)
	* Internally in a computer any problem goes trhough a set of logic gates, and so it can be represented by a boolean circuit
* The boolean circuit satisfiability problem is verfiable in polynomial time: it is an NP problem
* Since the boolean satisfiability problem is both an NP and an NP-hard problem, it is an NP-complete problem
* I can thus show that a problem is NP-complete by reducing it to the boolean circuit satisfiability problem

### Graph coloring problem
* The graph coloring problem: given an undirected graph $G=(V,E)$ and $k \in \mathbb{N}$, can I color its nodes with $m \leq k$ colors such that adjacent nodes have different colors?
* This problem can be reframed as the clique problem: given a graph $G=(V,E)$ and $k \in \mathbb{N}$, is there a subset of nodes $S \subseteq V$ with $|S| = m \geq k$ such that there is an edge $(u,v)$ among all the possible pairs of nodes $u,v \in S$?
	* In other words, is there a clique $S \in V$ such that $|S| \geq k$?
* If the answer to the clique problem is YES, then the answer to the graph coloring problem is NO, and vice versa
	* If there is a clique of $k$ elements in a graph, I need at least $k$ colors for coloring it
	* If in a graph the maximal clique has $k$ elements, then it is possible to color the nodes in the graph with $k$ colors

### Traveling salesperson problem
* The travelling salesperson problem (TSP): given $n$ cities at a certain distance from each other and given $k \in \mathbb{N}$, is there a tour of lenght $l \leq k$ that visits each city exactly once and returns back to the original city?
* This is equivalent to the hamiltonian cycle problem: given a weighted completely connected graph $G=(V,E)$ is there a circuit $\pi$ such that each node of the graph is visited exactly once and the last node is connected to the starting node?
* The travelling saleseman problem can be formulated with symmetric or asymmetric distances: either $w(u,v)=w(v,u)$ or $w(u,v) \not= w(v,u)$

### 0-1 linear programming problem
* The 0-1 linear programming problem: given an integer matrix $A \in \mathbb{Z}^{m \times n}$ and an integer vector $b \in \mathbb{Z}^m$, is there a binary vector $x \in \{0,1\}^n$ such that $Ax \leq b$?

### Boolean satisfiability problem
* The boolean satisfiability problem: given a boolean formula $\phi$ in conjunctive normal form (CNF), is there an assignment of truth values such that $\phi$ is true?
* A boolean formula is a conjuntive normal form if it is a conjunction of disjunctions of literals, where a literal is a boolean variable or a negated boolean variable 
$$ \phi = (\lnot a \lor \lnot b \lor \lnot c) \land (v \lor \lnot c) \land (a \lor \lnot b \lor c)$$
$$ a=b=TRUE, c = FALSE \implies \phi = TRUE \implies \phi \mbox{ is satisfiable}$$

### Some search and verification algorithms
* The following algorithm is a verifier for the clique problem: it takes in input an instace of the clique problem ($G=(V,E)$, $k \in \mathbb{N}$) and a certificate $S \subseteq V$ for it, and checks if $S$ is indeed a clique of at least $k$ nodes for $G$
	* It is a polynomial-time verifier for the clique problem with worst case complexity $O(n^2)$ with $n = |V|$

\begin{algorithmic}
\Statex
\Procedure{VERIFY-CLIQUE}{$G,k,S$}
	\If{$|S| < k$}
		\Return $FALSE$
	\EndIf
	\For{$u \in S$}
		\For{$v \in S-\{u\}$}
			\If{$(u,v) \not\in G.E$}
				\Return $FALSE$
			\EndIf
		\EndFor
	\EndFor
	\State \Return $TRUE$
\EndProcedure
\Statex
\end{algorithmic}

* An exhaustive search algorithm for the clique problem explores all the $2^n$ possible subsets of nodes in $V$
* A backtracking algorithm can solve it in $O(2^n)$ by enumerating the $n \choose k$ subsets of $V$ that have $k$ nodes and checking each subset with VERIFY-CLIQUE

\begin{algorithmic}
\Statex
\Procedure{CLIQUE}{$G,S,i,k,n$}
	\If{$0 < k-|S| \leq n-i+1$}
		\State $C=\{FALSE,TRUE\}$
	\Else
		\State $C=\emptyset$
	\EndIf
	\For{$c \in C$}
		\If{$c$} $S=S \cup \{c\}$\EndIf
		\If{\Call{VERIFY-CLIQUE}{$G,k,S$}} \Return $TRUE$
		\ElsIf{\Call{CLIQUE}{$G,S,i+1,k,n$}} \Return $TRUE$
		\EndIf
		\If{$c$} $S=S -\{c\}$\EndIf
	\EndFor
	\State \Return $FALSE$
\EndProcedure
\Statex
\end{algorithmic}

* The following is a polynomial verifier for the travelling salesman problem that runs in $O(n)$ time
	* $D$ is the distance matrix and $S[1...n]$ is the certificate of the tour $S[1] \leadsto S[2] \leadsto ... \leadsto S[n] \leadsto S[1]$

\begin{algorithmic}
\Statex
\Procedure{VERIFY-TSP}{$S,k,n,D$}
	\State $l = D[S[n],S[1]]$
	\For{$i=2$ to $n$}
		\State $l = l + D[S[i-1],S[i]]$
	\EndFor
	\State \Return $l \leq k$
\EndProcedure
\Statex
\end{algorithmic}

* If $C$ is the set of possible cities the possible tours for the TSP are $O(n!)$ where $n = |C|$ , since I need to consider all the possible permutations of the set of cities
* I can use backtracking to solve the TSP problem in $O(n!)$ time by enumerating all the possible permutations of $C$ and using VERIFY-TSP for each of them

\begin{algorithmic}
\Statex
\Procedure{TSP}{$S,i,k,C,D$}
	\State $l = D[S[n],S[1]]$
	\For{$c \in C$}
		\State $S[i] = c$
		\State $C = C- \{c\}$
		\If{$C=\emptyset \land$ \Call{VERIFY-TSP}{$S,k,n,D$}} \Return $TRUE$
		\ElsIf{\Call{TSP}{$S,i+1,k,C,D$}} \Return $TRUE$
		\EndIf
		\State $C=C\cup\{c\}$
	\EndFor
	\State \Return $FALSE$
\EndProcedure
\Statex
\end{algorithmic}

### Working with hard problems
* It is not possible to solve exactly an hard problem in polynomial time
* To handle NP-hard problems, I need to renounce to something
* Generality: I may be able to solve an hard problem in polynomial time for special cases of the problem
	* The graph coloring problem can be solved in polynomial time for $k=2$, but it is NP-hard for $k\geq 3$
	* The linear programming problem can be solved in polynomial time if $x \in \mathbb{R}^n$ is a vector of real numbers instead of an integer vector
	* The boolean satisfiability problem can be solved in polynomial time if $\phi$ is a 2-CNF, but it is NP-hard if it is a 3-CNF
		* A 2-CNF has at most 2 literals per clause, a 3-CNF has at most 3 literals per clause
* Optimality: I may be able to compute a sub-optimal solution in polynomial time
	* In an optimization problem, I can decide to halt when I reach a treshold score $\epsilon$, instead of halting at an extremum
* Efficiency: I can accept to use a super-polynomial algorithm if I am able to prune the search space to a reasonable leavel (e.g. with branch-and-bound algorithms)
* Formality: I can design a polynomial time algorithm that I am not able to proove correct, but seems to halt with the right solution (an heuristic algorithm)

### Approximation algorithms
* An approximation algorithm returns a sub-optimal solution $C$ within a factor $\rho(n)$ from an optimal solution $C^*$, for an input of size $n$
$$max\left(\frac{C}{C^*},\frac{C^*}{C}\right) \leq \rho(n)$$
	* Note that this definition applyies to both maximization and minimization problems
* An algorithm that achieves an approzimation ration $\rho(n)$ is said to be a $\rho(n)$-approximation algorithm
	* An optimal algorithm produces an 1-approximated solution
* The $\Delta$-TSP problem is a variant of the travelling saleseperson problem enforcing triangle inequalities
* Given $n$ cities and their distances in a matrix $D$, where $D(i,j) \leq D(i,k)+D(k,j)$ for all $i,j,k \in \{1,...,n\}$, find a minimum-lenght tour $l$ that visits each city exactly once and ends in the first city
* The optimization version of $\Delta-TSP$ is NP-hard, and also the decision version of this problem (find a $l : |l| \leq k$ for some bound $k$ on the tour lenght) is NP-hard
* However, the $\Delta$-TSP admits approximation algorithms (not all the NP-hard problems do)
* An optimal $\Delta-TSP$ tour is a Hamiltonian circuit with minimum weight
* I can get an approximate Hamiltonian circuit for $G$ by finding a minimum spanning tree $T$ for $G$ and returning a list $H$ of the nodes corresponding to a pre-order traversal of $T$
	* By removing any single edge from a Hamiltonian circuit $H$ for a graph $G=(V,E)$, I get a spanning tree $T'$ for $G$
		* This spanning tree is not necessarily a minimum spanning tree
	* The cost of the spanning tree $T'$ obtained from $H$ is necessarily lower than the cost of $H$ itself, since it is obtained by removing a non-negative edgefrom it
$$ c(T') \leq c(H)$$
	* A minimum spanning tree $T$ for $G$ cannot cost more than any other spanning tree $T'$, included the one obtained from an optimal Hamiltonian circuit $H^*$
$$ c(T) \leq c(T')$$
	* Thus, by combining the 2 inequalities I get that the cost of a MST $T$ is necessarily lower than the cost of an optimal Hamiltonian circuit $H^*$
$$ c(T) \leq c(H^*)$$
	* When I perform a full tree walk $W$ on $T$, the same nodes are returned multiple times with a path that crosses all the edges in $T$ exactly twice
	* Thus, the cost of the walk is exactly twice the cost of the MST $T$
$$c(W)=2c(T)$$
$$c(W)\leq 2c(H^*)$$
	* Thanks to the triangle inequality, I can remove any repeated node by knowing that I am not increasing the lenght of the tour
	* The maximal length of a tour $H$ returned by the approximated algorithm is thus at most twice the lenght of an optimal tour
$$ c(H)= \leq c(H^*)$$
	* This is thus a 2-approximated algorithm
* The total time cost of the approximate Hamiltonian circuit is $O(n^2 \log n)$
	* The cost of finding an MST using Kruskal's algorithm is $O(m \log n)$
	* The cost of visiting $T$ in pre-order is $O(n)$
$$ O(m \log n)+O(n)=O(n + m \log n)=O(m \log n) = O(n^2 \log n)$$
* There are also much better practical approximations for the $\Delta$-TSP problem
* If $\mbox{P} \not= \mbox{NP}$ there is NO constant-approximation algorithm for the general TSP problem without triangle inequalities
* For many other problems finding an approximate solution within a constant factor from the optimal solution is itself an NP-hard problem!

### Branch and bound
* Branch-and-bound is a more efficient enumeration approach based on avoiding decisions that cannot lead to an optimal solution
* It was developped by Alisa Land and Alison Dong in 1960
* Let's assume a minimizazion problem with cost function $\phi(x)$
	* This is not a restrictive condition since I can apply the same reasoning for maximization problems
$$ min(\phi(x)) = max(-\phi(x))$$
* I define a function $lb(S,i)$ that gives a lower bound on the cost of every possible solution in $S'[1...j]$ with $j \geq i$ obtainable by extending the solutionm $S[1...i]$ with new decisions
$$ lb(S,i) \leq \phi(S') \qquad \forall \ S'[1...j] \ , j \geq i$$
* I denote with $S^*$ the best known solution at any given node of the search tree, and with $z^*=\phi(S^*)$ its cost
* If at any given node the lower bound is higher than $z^*$, I avoid exploring the subtree rooted in that node
	* This action is called pruning the search tree
* I assume that the number of choices at step $i$ $C_i$ is bounded by some constant $m$ such that $|C_i| \leq m$ for $i=1,...,n$
* I assume that computing $lb(S,i)$ costs $O(f(n))$ where $f(n)$ is some function $\mathbb{N} \to \mathbb{N}$
* With these assumptions, the worst-case time complexity of branch-and-bound is still exponential
	* At each step $i \in \{1,...,n\}$ I can take $m$ choices, each costing $f(n)$
	* The total cost is thus $O(m^n f(n))$
* The actual running time of branch-and-bound depends on a set of conditions
	* The initial solution adopted, that can be random or come from an heuristic algorithm
	* The branching factor of the search tree (this is $m$)
	* How costly it is to compute $lb(S,i)$ and how tight its bound is (this is $f(n)$ and the tightness of the bound influences how much of the tree I can avoid exploring)
	* The order in which the search tree is visited (pre-order, by levels, by some priority key,...)

\begin{algorithmic}
\Statex
\Procedure{BRANCH-BOUND}{$S,\phi,i,n,...$}
	\State $C =$ \Call{CHOICES}{$S,i,n,...$}
	\State $z^* = \infty$
	\For{$c \in C$}
		\State $S[i] = c$
		\State $l = lb(S,i)$
		\If{$l < z^*$}
			\If{$i < n$}
				\State \Call{BRANCH-BOUND}{$S,\phi,i+1,n,...$}
			\Else
				\State $S^* = S$
				\State $z^* = \phi(S)$
			\EndIf
		\EndIf
	\EndFor
\EndProcedure
\Statex
\end{algorithmic}

* I can use the branch-and-bound approach for the TSP
* I have $n = \{1,...,n\}$ cities and their distance matrix $D \in \mathbb{R}^{n \times n}$
* At step $i = 1,...,n$ I have visited $i$ cities $S[1,...,i]$ and I need to decide which one to visit next, $S[i+1]$
* In order to compute a lower bound $lb(S,i)$ for the TSP I need to consider some parameters
	* The cost $\alpha$ for reaching $S[1]$ for any city not yet visited $j \not\in S$
	* The cost $\beta$ for leaving $S[i]$ for reaching any city $j \not \in S$
	* The cost $\gamma$ of the travel $S[1...i]$ up to the current state
	* The cost $\delta_j$ for visiting each city $j \not \in S$
* The above parameters can be computed for $S[1...i]$ as follows
$$\alpha = min\{D(j,S[1])|j \not\in S\}$$
$$\beta = min\{D(S[i],j)|j \not\in S\}$$
$$\gamma = \begin{cases} 0 & \mbox{if }i=1\\ \sum_{j=1}^{i-1} D(S[j],S[j+1]]) & \mbox{otherwise}\end{cases}$$
$$\delta_j = min_{p,q}\{D(p,j)+D(j,q)|j\not=p\not=q\} \ \forall \ j \not\in S$$
* Now I can compute the lower bound $lb(S,i)$ as
$$lb(S,i)=\begin{cases}\gamma+D(S[n],S[1]) & \mbox{if } i=n \\ \gamma+\lceil \frac{\alpha+\beta+\sum_{j\not\in S}d_j}{2} \rceil & \mbox{if } i < n\end{cases}$$
* The worst-case time complexity of $lb(S,i)$ is $O(n^2)$, since for calculating $\delta_j$ I need to evaluate all the possible pairs of node with one of them not in $S$

\begin{algorithmic}
\Statex
\Procedure{BRANCH-BOUND-TSP}{$S,i,n,R,G,D$} \Comment{$R$ is the set of cities not yet visited}
	\State $C =$ \Call{CHOICES}{$S,i,n,...$}
	\State $z^* = \infty$
	\For{$c \in R$}
		\State $S[i] = c$
		\State $R = R - \{c\}$
		\If{$i > 1$}
			\State $G[i]=G[i-1]+D(S[i-1],S[i])$ \Comment{$G[i]$ is $\gamma$}
		\EndIf
		\State compute $\alpha,\beta,delta_j$
		\If{$i = n$}
			\State $lb=G[i]+D(S[n],S[1])$
		\Else
			\State $lb=G[i]+\lceil (\alpha+\beta+\sum\delta_j)/2 \rceil$
		\EndIf
		\If{$lb < z^*$}
			\If{$i < n$}
				\State \Call{BRANCH-BOUND-TSP}{$S,i+1,n,R,G,D$}				
			\Else
				\State $S^* = S$
				\State $z^* = lb$
			\EndIf
		\EndIf
		\State $R = R \cup \{c\}$
	\EndFor
\EndProcedure
\Statex
\end{algorithmic}

### Heuristic algorithms
* For some hard problems, it is too expensive to find an optimal solution, and an approximation algorithm does not exist
* In these cases, it is possible to develop a heuristic procedure to search for feasible solutions
* An heuristic algorithm cannot guarantee that an optimal solution, or even sub-optimal solution under a certain bound, will be found
	* Nonetheless, the solutions obtained may be useful in practice
* Heuristic algorithms follow 2 main approaches
	* Greedy approaches applied when the greedy choice property is NOT repsected
	* Local search approaches that restrict the search space to a neighbotrhood of a given solution
* It is possible to devise a greedy heuristic for the TSP
	* Let $G=(V,E)$ be a complete graph of cities, $S=\emptyset$
	* Sort $G.E$ according to their weight
	* For each sorted edge $(u,v) \in G.E$, starting from the one with lowest weight, if both $u$ and $v$ are not saturated in $S$ (they have a degree $< 2$), add the edge $(u,v)$ to the solution $S$
	* Finally, add to the solution $S$ the edge $(u,v)$ that closes the tour
	* An implementation of this heursitic using disjoint-sets with path compression and union-by-rank costs $O(n^2 \log n)$ with $n=|V|$

\begin{algorithmic}
\Statex
\Procedure{GREEDY-TSP}{$G$}
	\State $S = \emptyset$
	\For{$u \in G.V$}
		\State $D[u]=0$ \Comment{$D[u]$ is the degree of node $u$}
		\State \Call{MAKE-SET}{$u$}
	\EndFor
	\State \Call{SORT}{$G.E$}
	\For{$(u,v) \in G.E$}
		\If{$D[u] < 2 \land D[v] < 2 \ \land $ \Call{FIND-SET}{$u$} $\not=$ \Call{FIND-SET}{$v$}}
			\State $S = S \cup \{(u,v)\}$
			\State $D[u] = D[u] +1$
			\State $D[v] = D[v] +1$
			\State \Call{UNION}{$u,v$}
		\EndIf
	\EndFor
	\State $u = 1$ \Comment{now I am adding the closing edge}
	\While{$D[u] \not= 1$} $u = u+1$
	\EndWhile
	\State $v = u+1$
	\While{$D[v] \not= 1$} $v = v+1$
	\EndWhile
	\State \Return $S \cup \{(u,v)\}$
\EndProcedure
\Statex
\end{algorithmic}

* The following is instead a local search procedure for the TSP
	* Let $H$ be a Hamiltonian circuit for the graph $G=(V,E)$
	* I define its neighborhood $N_2(H)$ as the circuit $H'$ obtained from $H$ by replacing 2 non-consecutive edges $e_1, e_2 \in H$ with the edges $e_1', e_2' \not\in H$ such that $\{e_1,e_2,e_1',e_2'\}$ is an Hamiltonian circuit
	* We see that $H$ has $n=|V|$ edges and $|N_2(H)|=\frac{n(n-1)}{2}-n$ neighbors
		* Since we are in a circuit, $n=|V|=|E|$
		* The number of neighbors is the number of possible pairs of edges in $H$ ($n(n-1)/2$) minus the number of consecutive pairs of edges $n$
	* Computing $N_2(H)$ costs $O(n^2)$ for a given $H$
	* I can have an exponential number of local search iterations $N_2(H)$, $N_2(H')$,...
	* I can generalize $N_2(H)$ to $N_k(H)$, where I replace an arbitrary number $k$ of edges to form the neighborhood of $H$
	* I am sure to reach a global optimum only when I analyse all the possible neighborhoods of $H$ $\cup_{k=2}^n N_k(H)$
		* In this way I am effectively performing an exhaustive search!
	* Experimentally, it can be observed that $N_2(h) \cup N_3(H)$ gives good results, and it has a search space of magnitude $O(n^3)$

## Sequence comparison and assembly

### Global alignment
* The global alignment problem: given the sequences $X = \langle X_1, ..., X_m \rangle$ and $Y = \langle Y_1,...,Y_n \rangle$ over the alphabet $\Sigma$, return the alignment between $X$ and $Y$ with maximum score
* Typically, $X$ and $Y$ have similar lenght ($m \approx n$) and they consist of thousand of elements
* An alignment $X',Y'$ is an insertion of spaces _ in arbitrary positions of $X$ and $Y$ so that the resulting sequences $X'$ and $Y'$
	* Have the same lenght
$$ k = |X'| = |Y'|$$
	* Don't have matching spaces
$$ X'[i] = Y'[i] \implies X'[i] \not=\_ \qquad \mbox{for } i = 1,...,k$$
* The pair score $\sigma(x,y)$ for the characters $x,y \in \Sigma$ is defined as
$$ \sigma(x,y) = \begin{cases}+1 & \mbox{if }x=y\not=\_ \\
				-1 & \mbox{if }x\not=y \land x \not= \_ \land y \not= \_ \\
				-2 & \mbox{if } x \not=y \land (x=\_ \lor y=\_)
\end{cases}$$
* The overall alignment score is
$$ \sum_{i=1}^k \sigma(X'[i],Y'[i])$$
* The global alignment problem has optimal substructure
* I can use a dynamic programming matrix $A \in \mathbb{Z}^{(m+1) \times (n+1)}$ such that $A(i,j)$ is the score of the best alignment for the prefixes $X_i$ and $X_j$
	* This score is also called similarity of $X_i$ and $X_j$
* The matrix $A$ is initialized with initial gaps
$$A(i,0)= -2i \ \mbox{for } i= 1,...,m$$
$$A(0,j)= -2j \ \mbox{for } j= 1,...,n$$
	* I am aligning $X_0=\epsilon$ to $Y_j$ and vice-versa $X_i$ to $Y_0=\epsilon$
* I define the match score $p_{i,j}$ as
$$ p_{i,j} = \begin{cases}+1 & \mbox{if } x_i=y_j\\ -1 & \mbox{if } x_i \not= y_j \end{cases}$$
* The dynamic programming recurrence relation for the position $A(i,j)$ is
$$A(i,j) = max\{A(i,j-1)-2,A(i-1,j)-2,A(i-1,j-1)+p_{i,j}\}$$
* After filling table $A$, the best score for the alignment of $X$ and $Y$ can be retrieved from the last cell in the matrix
$$BEST=A(m,n)$$
* I can also build a bactrack matrix $B \in \{MATCH,UP,LEFT\}^{m\times n}$ to obtain the alignments themselves

### Local alignment
* The local alignment problem: given the sequences $X = \langle X_1, ..., X_m \rangle$ and $Y = \langle Y_1,...,Y_n \rangle$ over the alphabet $\Sigma$, return the alignment between a substring $\tilde{X}$ of $X$ and a substring $\tilde{Y}$ of $Y$ with maximum score
* As for the global alignment problem, I create a dynamic programming matrix $A \in \mathbb{Z}^{(m+1) \times (n+1)}$ such that $A(i,j)$ is the score of the best alignment for suffixes of prefixes $X_i$ and $X_j$
* The matrix $A$ is initialized with initial gaps
$$A(i,0)= 0 \ \mbox{for } i= 1,...,m$$
$$A(0,j)= 0 \ \mbox{for } j= 1,...,n$$
* The dynamic programming recurrence relation for the position $A(i,j)$ is
$$A(i,j) = max\{A(i,j-1)-2,A(i-1,j)-2,A(i-1,j-1)+p_{i,j},0\}$$
* After filling table $A$, the best score for the alignment of $X$ and $Y$ can be retrieved from the highest cell in the whole matrix
$$BEST=max_{i,j}(A(i,j))$$
* I can build a bactrack matrix $B \in \{MATCH,UP,LEFT,END\}^{m\times n}$ to obtain the alignments themselves

### Semiglobal alignment
* The semiglobal alignment problem is similar to the global alignment problem, but it ingnores the spaces at the beginning and end of $X$ and $Y$
* The inizialization of $A$ is done as follows
$$A(i,0)= 0 \ \mbox{for } i= 1,...,m$$
$$A(0,j)= 0 \ \mbox{for } j= 1,...,n$$
* Its recurrence equation is identical to that of the global alignment
$$A(i,j) = max\{A(i,j-1)-2,A(i-1,j)-2,A(i-1,j-1)+p_{i,j}\}$$
* After filling table $A$, the best score for the alignment of $X$ and $Y$ can be retrieved from the highest value of the last row and column
$$BEST = max(\{A(i,n)|i=1,...,m\}\cup\{A(m,j)|j=1,...,n\})$$

### Multiple alignment
* The multiple sequence alignment problem: given $m >1$ sequences $X_1,...,X_m$ having about the same length, return the best alignment among all of them
* Spaces are inserted at arbitrary locations of the sequences so to make all the sequences of the same length $n \geq max\{|X_i||i=1,...,m\}$
* Multiple sequence alignment is a generalization of the global alignment problem (where $m=2$)
* A multiple sequence alignment is evaluated with a multiple scoring function that must be
	* Independent to the order of the arguments (it should be commutative)
	* It should reward strongly related fragments
	* It should penalize spaces and unrelated sequences
* The sum-of-pairs ($SP$) scoring function is a possible solution consisting in summing the pair scores of all the pairs of symbols in a column of the multiple sequence alignment
$$SP(S) = \sum_{(x,y) \in S \times S} \sigma(x,y)/2 \qquad S=\{S_1,...,S_m\} \mbox{ is the set of symbols in a column} $$
	* I am dividing by 2 since for each pair $x,y \in S \times S$ there is also an equal pair $y,x$, and I want to consider its score only once!
* Finding the best multiple sequence alignment score using the SP score is an NP-hard problem!
	* I need to score $O(m^2)$ pairs of symbols for each of the $O(n)$ positions in the alignment
	* Just scoring a given alignment with the SP score has a $O(m^2n)$ running time
	* If I use dynamic programming I need to calculate $O(n^m)$ cells in the matrix to find the optimal alignment
	* Each cell requires calculating an SP score for a position plus a constant amount of work for determining which direction to adopt
	* Calculating the SP score for the position is an $O(m^2)$ problem
	* Finding an optimal alignment is a superexponential $O(n^mm^2)=O(n^m)$ problem

### Star alignment heuristic
* I can use the start alignment heuristic for calclulationg multiple sequence alignments
* Given the sequences $X_1,...,X_m$, I first select a sequence $X_c$ with $c \in \{1,...,m\}$, which represents the center of the star
* I find then the $m-1$ optimal global alignments between $X_c$ and $X_i$ with $i \in \{1,...,m\}-\{c\}$
* To select the star center $X_c$ I can compute the $O(m^2)$ possible pairwise alignments and choose as $X_c$ the sequence that maximizes the sum of scores between itself and any of the other sequences
$$ X_c = argmax_{X_c} \{\sum_{i \in \{1,...,m\}-\{c\}} \sigma(X_c,X_i) | c \in  \{1,...,m\} \}$$
	* The time complexity of this approach is $O(m^2n^2)$ where $n = max\{|X_i| | i = 1,...,m\}$
	* I am computinf $O(m^2)$ global alignments which cost $O(n^2)$ each
* After I have selected a star center $X_c$, I align all the $X_i \not=X_c$ to it with a global alignment
	* Once gaps are introduced in $X_c$, they are never removed for avoiding altering other alignments
* After having performed all the alignments, I add padding gaps to the aligned sequences to bring all of them to the same length
* There is no guarantee of optimality for the star alignment heuristic, but in practice I tend to get good sub-optimal results

### Similarity
* Similarity is a metric based on sequence alignments
* An alignment $\alpha$ between 2 sequences $X,Y$ over some alphabet $\Sigma$ is a pair $(X',Y')$ such that $|X'|=|Y'|$, $X'$ and $Y'$ are obtained by optionally adding $\_$ in $X$ and/or $Y$, and if $X'[i]=Y'[i] \implies X'[i] \not= \_ \ \mbox{for } i=1,...,k$
	* We say that the symbols $X'[i]$ and $Y'[i]$ are aligned under $\alpha$
* A scoring system is a pair $(p,g)$ such that
	* $p: \Sigma \times \Sigma \to \mathbb{R}$ is a function from all the pairs of symbols in an alphabet $\Sigma$ to the real numbers such that for each pair of aligned symbols it returns a score
	* $g \in \mathbb{R}$ is a (usually negative) constant used for penalizing a gap
* The total score of an alignment $\alpha$, denoted $score(\alpha)$, os the sum of all the scores for each pair of aligned residues
$$ score(\alpha) = \sum_{i=1}^n p(X'[i],Y'[i])$$
* The similarity $sum(X,Y)$ among 2 sequences $X$ and $Y$ is the maximum score achievable among all the possible alignments of $X$ and $Y$
$$sim(X,Y) = max\{score(\alpha)|\alpha \in \mathbb{A}_{X,Y}\} \qquad \mathbb{A}_{X,Y} \mbox{ is the set of all the possible alignments of $X$ and $Y$}$$
* $\mathbb{A}_{X,Y}$ has finite dimentions but it is far too big to be enumerated in practice

### Distance
* A distance $d$ over a set $E$ is a function $d: E \times E \to \mathbb{R}$ such that
$$d(x,x) = 0 \ \forall \ x \in E$$
$$d(x,y) > 0 \ \forall \ x\not=y$$
$$d(x,y) = d(y,x) \ \forall \ x,y \in E$$
$$d(x,y) \leq d(x,z)+d(z,y) \ \forall \ x,y,z \in E$$
* The Manhattan distance over $E = \mathbb{R} \times \mathbb{R}$ is defined as
$$ d((x,y),(x',y')) = |x-x'|+|y-y'|$$
* The Euclidean distance over $E = \mathbb{R} \times \mathbb{R}$ is defined as
$$ d((x,y),(x',y')) = \sqrt{(x-x')^2+(y-y')^2}$$
* It is possible to define also a distance over strings, where $E = \Sigma^*$
* The edit distance $dist(X,Y)$ is the minimum number of edit operations needed to transfrom a string $X$ into a string $Y$
	* Edit operations are substitutions, insertions and deletions of symbols
* I can assign a cost to each edit operation: a cost measure is a pair $(c,h)$ where $c : \Sigma \times \Sigma \to \mathbb{R}$ is a distance over each possible pair of symbols in the alphabet $\Sigma$ and $h > 0$ is the cost of inserting or deleting a symbol
* If I have $k > 0$ edit operations $O = \langle o_1,...,o_k \rangle$ the total cost $cost(O)$ is the sum of all the individual costs $o_1,...o_k$
$$ cost(O) = \sum_{i=1}^k o_i$$
* The edit distance $dist(X,Y)$ is formally defined as
$$ dist(X,Y) = min\{cost(O)|O \in \mathbb{S}_{X,Y}\}$$
	* $\mathbb{S_{X,Y}}$ is the set of all the possible series of operations that can transform the sequence $X$ into the sequence $Y$
	* $\mathbb{S_{X,Y}}$ is infinite since I can do any number of insertions and deletions on the same character so that the initial and final state of the character are the same
$$ x \to xa \to xaa \to x\underbrace{a\cdot \cdot \cdot a}_n \to ... \to x\underbrace{a\cdot \cdot \cdot a}_{n-1} \to ... \to xaa \to xa \to x$$
		* For each $n \in \mathbb{N}$, I can transform $x \to x$ with cost $2*h*n$ by performing $n$ insertions followed by $n$ deletions of a character $a \in \Sigma$
* The most commonly used edit distance is the Levensthein distance where
$$\begin{matrix} h=1 \\ \\ c(a,b) =  \begin{cases}0 & \mbox{if } a=b \\ 1 & \mbox{if } a\not=b\end{cases}\end{matrix}$$
	* Because of its mainstream use, Levensthein distance is sometimes used as a synonim of edit distance
	* It was first described by the Russian scientist Vladimir I. Levensthein in 1965
* Given a cost measure $(c,h)$ and a constant $M$, it is possible to devise a scoring system $(p,g)$ for a global alignment as
$$p(a,b) = M - c(a,b)$$
$$g = -h+M/2$$
* With such a scoring system and cost measure, I observe that for any pair of sequences $X,Y$
$$sim(X,Y)+dist(X,Y)=\frac{M(|X|+|Y|)}{2}$$
* This means that similarity and distance are interchangable: I can compute the distance from the similarity and vice-versa
* For the Levensthein distance, if I choose $M=0$ such that a match has score 0, a mismatch has score -1, and a gap has score -1, or I can choose $M=2$ such that a match has score 2, a mismatch has score 1, and a gap has score 0
* The choice of a constant $M'\not=M$ does not affect which alignment has an optimal score among 2 sequences, but it affects its score, such that $S'\not=S$ but $S' \propto S$
$$S=\frac{|X|+|Y|}{2}(M-M')+S'$$
	* Note that this holds only for global alignments!

### Sequence assembly and shortest common superstring
* Sequence assembly is the act of assebling fragments of DNA obtained from a sequencer in order to reconstruct a genome
* A multiple sequence alignment can be used to assemble sequences
* The shortest common superstring (SCS) problem is a simplified version of the sequence assembly problem that does not take into accounts errors into the sequenced fragments
* The SCS problem takes in input $m > 1$ sequences $X_1,...,X_m$ and returns the shortest string $X$ which is a superstring of each $X_i$ for $i=1,..,m$
	* For $X$ to be superstring of $X_i$, $X_i$ must be a substring of $X$
* If $m$ is bounded by a constant, then the time complexity of the SCS problem is $O(n^m)$ using a dynamic programming approach where $n=max\{|X_i||i=1,...,m\}$
	* For an arbitrary number $m$ of sequences, the SCS problem is NP-hard
* SCS can be reduced to the TSP by creating an overlap graph
	* Let $X = x_1, \cdot \cdot \cdot x_m$ and $Y = y_1, \cdot \cdot \cdot y_n$ be 2 sequences
	* I define their overlap $\theta(X,Y)$ as the maximum number of characters $k$ such that the k-suffix of $X$ is equal to the k-prefix of $Y$
$$ \theta(X,Y)=max\{k|x_{m-k+1}x_{m-k+2}\cdot \cdot \cdot x_m = y_1y_2 \cdot \cdot \cdot y_k\}$$
	* An overlap graph for the strings $X_1,...,X_m$ is a weighted, directed and complete graph $G=(V,E)$ with weight function $w$ such that each string is a vertex and the weight of each edge is the difference among the length of the first sequence it connects and the overlap of the connected sequences
$$ V =\{X_1,...,X_m\}$$
$$ w(X_i,X_j)=|X_i|-\theta(X_i,X_j) \ \forall (X_i,X_j) \in E$$
* Let $X_1,...,X_m$ be $m$ input sequences where no sequence is a substring of another (otherwise we just ignore it)
	* I can find the SCS for $X_1,...,X_m$ by solving the TSP for the corresponding overlap graph
	* Once I find an Hamiltonian path on the overlap graph, I can reconstruct the alignment by aligning without gaps the suffix of any sequence in the path with the prefix of the next sequence
* The transformation of the SCS problem into the TSP is a polynomial-time reduction
	* This proves that the TSP is at least has hard as the SCS probelm, not the opposite
* Since besides being NP-hard the SCS problem is also NP (it can be verified in polynomial time), the SCS problem is NP-complete
* If I decide to admit errors in the strings to assemble, things become more complicated
	* An error is any substitution, insertion or deletion in the string as compared to the original sequenced genome
	* Typically we observe a 1-5% error rate next to the end of a fragment
	* It may still be possible to reconstruct the right consensus by using gaps and majority voting, if the coverage is high enough
	* Base call errors are not the only possible sequencing error
	* A chimera is a fragment made up of sequences that are not contiguous in the original genome
		* Chimeras should be recognized and removed from the input pool before the assebmly step
	* The orientation of each fragment (the strand to which it belongs) is unknown
		* A fragment $X$ is a substring of the string $Y$ iff the reverse complement of $X$ is a substring of the reverse complement of $Y$
		* In general, given $m$ fragments, I should try all the $2^m$ possible combinations of fragment orientations
		* In practice, I consider all the fragments and their reverse complement as separate nodes in the overlap graph where $w(X,Y)$ is the score of the semiglobal alignment between $X$ and $Y$
	* Repetitive sequences and missing regions leads to further assembly problems
		* A repetitive region can be identified in the overlap graph as a cycle
		* A missing region can be identified from the fact that the overlap graph is disconnected

## Suffix tries, trees, and arrays
* In many applications we need to store efficiently a long, known, and fixed string $S$ over an alphabet $\Sigma$
	* For example, a genome to which I want to align some reads
* I can preprocess $S$ in such a way to facilitate future queries over $S$
* Given a string $Q \in \Sigma^* : |Q| << |S|$ common queries that I may want to answer are
	* Is $Q$ a substring of $S$?
	* Is $Q$ a subsequence of $S$?
	* How many times deos $Q$ occurr in $S$?
	* What is the longest common substring of $Q$ and $S$?
	* What is the longest common subsequence of $Q$ and $S$?
	* What is the best approximation of $Q$ in $S$?
* Other queries are possible that do not depend on any query $Q$
	* What is the longest repeat in $S$?

### Suffix trie
* A suffix trie is a space-efficient tree used for storing strings in such a way to facilitate the processing of common query types
* Given a string $S \in \Sigma^*$ ending with a special final symbol $\$$, a suffix trie for it is a tree $SuffTrie(S)$ such that
	* Each edge corresponds to a character in $\Sigma$, the same character can correspond to many edges
	* Any edge from a node to a leaf is labelled with the special character $\$$
	* Every path from the root to a leaf represents a suffix of $S$
	* Every suffix of $S$ is represented by some path from the root to a leaf
	* Suffixes with the same prefix share a common path corresponding to that prefix
* The utility of a suffix trie is based on the fact that any substring of any string $S$ is a prefix of some suffix of $S$ itself
* To find if $Q$ is a substring of $S$ using a suffix trie I follow the path in $SuffTrie(S)$ given by $Q$
	* I am looking for a suffix of $S$ starting with $Q$
	* If I am able to match all the characters of $Q$ in a path down the tree, $Q$ is a substring of $S$, otherwise it is not
	* The worst-case time complexity is $O(m)$, where $m=|Q|$, and it does not depend on the size of $S$
* To understand if $Q$ is a suffix of $S$ I can follow the $Q$-path in $SuffTrie(S)$ and, if the path ends in a leaf the answer is yes, otherwise no
* To count the occurrences of $Q$ is $S$ I can follow the $Q$-path in $SuffTrie(S)$ and count the number of leaves in the subtree rooted in the node where the $Q$-path terminates
	* I am counting how many suffixes of $S$ start with $Q$
* To find the longest repeat in $S$ I can find the deepest node having at least 2 leaves in its subtree
* To find the lexicographically smallest suffix of $S$ I can start from the root and follow always the character with smallest alphabetical order until the special character $\$$ is found
* Suffix links connect a node representing the string $a \cdot w$ where $a \in \Sigma$ and $w \in \Sigma^*$ with the only node representing the string $w$
	* Every node represents the prefix of some suffix, and it has a suffix link that points to another node representing a string of one character less
	* A suffix link for a leaf (for a suffix!) always points to another leaf, apart for the suffix link of $\$$, which points to the root
* To find the longest common substring between $S$ and $Q$, I can walk down the $Q$-path and
	* If there is no edge $(u,v)$ matching the character $Q[i]$, I save the node $u$ and I try to match the character $Q[i]$ starting from the suffix link of $u$
		* I am searching for another substring of $S$ containing the same characters of the common substring found up to now, except for the first character
		* I then try to extend it, and if not possible I remove another starting character and try again
		* If it is not possible to match the character $Q[i]$, I eventually backtrack until the root (I start again from scratch)
		* If the root does not have any edge matching $Q[i]$, it means that character $Q[i]$ is absent from $S$
			* If $S,Q \in \Sigma^*$, this is not possible
	* When $Q$ is exhausted, the longest common substring among $S$ and $Q$ is the deepest of the saved nodes
	* The cost of finding the longest common substring among $S$ and $Q$ is $O(m)$ when $SuffTrie(S)$ is already available, while it is $O(nm)$ with dynamic programming, with $n=|S|$ and $m=|Q|$
* In order to build $SuffTrie(S)$, I scan $S$ from left to right and I build $n$ tries $SuffTrie(S_i)$ for each prefix $S_i$ of $S$
* To get $SuffTrie(S_i)$ from $SuffTrie(S_{i-1})$ I add $S[i]$ to ALL of the suffixes of $S_{i-1}$
	* Let $CurrentSuffix$ be the longest suffix in $SuffTrie(S_{i-1})$
	* Until you reach the root or the current node has already an outgoing edge labeled $S[i]$
		* Add a child labeled $S[i]$ to $CurrentSuffix$
		* Save the new node in a list
		* Follow the suffix link of $CurrentSuffix$ and set $CurrentSuffix$ to it
			* The suffix link of the longest suffix in $SuffTrie(S_{i-1})$ is the second longest suffix in it, and so on
		* Set the suffix link of the previous new node to the node you will create at the next iteration
	* Make the sSet tuffix link of the last new node added to point to
		* The root if I terminated because I reached the root
		* The already existing node if I terminated because the current node has already an outgoing edge labeled $S[i]$
* The number of nodes in a suffix trie is not necessarily linear: it is $O(n^2)$ with $n=|S|$
	* Let $S = \underbrace{a \cdot ... \cdot a}_{n/2}\cdot \underbrace{b \cdot ... \cdot b}_{n/2}$
	* Its suffix trie is composed of the root and
		* A path of $n/2$ nodes all labeled with $a$
			* This path does not lead to a leaf since $a$ is not a suffix of $S$
		* $n/2+1$ paths which are labeled with only $b$, each containing $n/2$ nodes
			* All of these paths end in a leaf, since $b$ is a suffix for $S$
			* There is 1 such path starting from the root, and 1 for each of the nodes in the path containing all $a$
	* Therefore, the total number of nodes in the suffix trie is
$$1+n/2+(n/2+1)(n/2) = 1+n+n^2/4 = O(1)+O(n)+O(n^2)=O(n^2)$$

### Suffix tree
* Suffix trees improve the space efficiency of suffix tries by compressing the paths without choices and representing suffixes with a range $i:j$ corresponding to the substring $S[i...j]$
	* If a path does not involve any real choice, there is no need to keep additional nodes, but I can represent that path with a single edge
	* This edge will correspond not to a symbol $S[i]$ but to a range of forced choices $S[i...j]$
* A compressed representation of a string $S$ in a suffix tree takes $O(n)$ space with $n=|S|$, compared to the $O(n^2)$ space taken by the uncompressed suffix trie
	* There are $n$ leaves, corresponding to each starting position of a suffix in $S$
	* Each internal node has $k$ children, with $2 \leq k \leq n$
		* $k \geq 2$ since If there is just 1 in choice in a position I remove the node
	* The number of internal nodes (and thus of edges) is $O(k) = O(n)$
		* The number of internal nodes if $k=2$ is at most $n-1$, with $n$ being the number of leaves
		* Base case: for 2 leaves I have 1 internal node, and $2-1=1 \geq 1$
		* Inductive step: I want to prove that a binary tree with $n$ leaves has exactly $n-1$ internal nodes
			* A binary tree of $n$ leaves is made up of a root and
			* A left binary subtree of the root with $k$ leaves
			* A right binary subtree of the root with $n-k$ leaves
			* By induction, the left binary subtree has $k-1$ internal nodes, and the right binary subtree has $n-k-1$ internal nodes
		* Thus, a binary tree of $n$ leaves has $n-1$ internal nodes
$$(k-1)+(n-k-1)+1 = n-k+k-1-1+1 = n-1 = O(n)$$
		* If $k > 2$, the number of internal nodes is smaller than if $k=2$, so the number of internal nodes is $O(n)$ in any case
	* The total number of nodes (leaves and internal nodes) in a suffix tree $T$ is thus
$$ |T| \leq n+n-1 = 2n-1 = O(n)$$
	* Each edge in the tree takes constant space, if I assume that each range is encoded by $O(1)$ bits
* A suffix tree can be built in $O(n)$ time using the algorithm of the Finnish scientist Esko J. Ukkonen (1995)
	* It works similarly to the algorithm for building a suffix trie, but with some additional tricks
	* The hidden constant for this algorithm is big: I need about 20 bytes per character of $S$
		* For a 10 Gbp genome I need around 200 Gb of storage space!

### Suffix array
* A suffix array is a more efficient way to store the suffixes of a string $S$ in $O(n)$ space
* A suffix array has the same capabilities of a suffix tree, but operations on it are a bit slower
* The main idea is to sort lexicographically all the suffixes and store their starting indexes into an array
* I first define a total order $\preceq$ on the characters in the alphabet $\Sigma$
	* $\preceq$ is a total order because $a \preceq b \lor b \preceq a \quad \forall \ a,b \in \Sigma$
* I then extend the total order $\preceq$ from single characters to strings: for each $X,Y \in \Sigma^*$, with $m=|X|$ and $n=|Y|$, $X \preceq Y$ iff there is a $k \in \{0,...,min(m,n)\}$ such that $X_k = Y_k$ and $X[k+1] \prec Y[k+1]$ or $k=m$
$$X \preceq Y \iff \exists k \in \{0,...,min(m,n)\} : X_k=Y_k \land (X[k+1] \prec Y[k+1] \lor k=m)$$
* The space complexity for suffix arrays is $O(n)$ like for suffix trees, but the hidden constant is much smaller
	* I just need to store the string $S$ itself and an array of $n$ indexes
* To search for a query string $Q$ in $S$, I perform a binary search on the index array to find a suffix of $S$ starting with $Q$
	* It is equivalent to a binary search among numbers (I am just using a $\preceq$ order instead of an $\leq$ order)
	* The cost of checking $x \leq y$ is $O(1)$, but the worst case complexity for checking whether $X \preceq Y$ is $O(|X|)$ since I may need to check all the characters in $X$
	* Since I need to perform $O(\log n)$ comparisons in the worst case for a binary search with $n=|S|$, the total worst case time complexity for searching $Q$ in $S$ is $O(m \log n)$ with $m=|Q|$
		* This compares to a $O(m)$ time complexity using suffix tries or trees
* I can build a suffix array in $O(n^2 \log n)$ time by sorting the $n$ suffixes with $O(n \log n)$ comparisons (the bound for comparison-based sorting), each costing $O(n)$
* I can actually do better and build a suffix array in $O(n)$ by exploiting the relationship of suffix arrays with suffix trees
	* I build a suffix tree in $O(n)$ using the Ukkonnen algorithm such that
		* The edges leaving a node in a suffix tree are sorted lexicographically by their labels
		* Each leaf in a suffix tree is labelled with the start position of the corresponding suffix
	* I can perform a in-order visit of this suffix tree and just output the labels of the leaves that I encounter, putting them in the suffix array
* I can also obtain a suffix array in $O(n)$ without building a suffix tree, using the Skew algorithm designed in 2003 by Karkainnen and Sanders
	* This algorithm is based on a skewed (2/3 to 1/3) divide-et-impera approach on radix-sort
	* I assume that the string $S$ starts from position 0 instead of from position 1
	* I use the special symbol $\$$ to pad $S$, if needed
	* I divide the suffixes of $S$ into 3 groups: the ones starting in position $i=0,3k,...$ with $k \in \mathbb{N}$, the ones starting in position $i=1,3k+1,...$, and the ones starting in position $i=2,3k+2,...$
	* I build the suffix array $SA^{1,2}$ for suffixes starting at position $i : i \mod 3 \not = 0$ (all the suffixes not belonging to the first group)

### Burrows-Wheeler transform

% Reviewed

---

# Exam info
* Exam will be written, but you can do also an oral part if you want
