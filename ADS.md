% Algorithms and Data Structures
% Saul Pierotti
% \today

---
header-includes:
	\usepackage{algpseudocode}
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
		\State \Return nil
	\EndIf
	\State $max=A[1]$
	\State $A[1] = A[A.heapsize]$ \Comment{put the last element as root}
	\State $A.heapsize = A.heapsize-1$
	\State \Call{MAX-HEAPIFY}{$A,1$}
	\State \Return $max$
\EndProcedure
\Statex
\end{algorithmic}


* Increseing the value of a key is $O(\log{n})$ since the maximum possible number of place exchanges is equal to the height of the heap, log n

```pascal
HEAP-INCREASE-KEY(A, i, key)
	if key < A[i]
		error "new key smaller than current key"
	A[i] = key
	while i > 1 and A[PARENT(i)] < A[i]
		exchange A[i] with A[PARENT(i)]
		i = PARENT(i)
```

* Inserting a new element into the heap is equivalent to increasing the key of an alredy existing one
	* I can insert an element with key infinitely small and update it to the real value
	* It uses HEAP-INCREASE-KEY so its running time is O(log n)

```pascal
MAX-HEAP-INSERT(A, key)
	A-heapsize = A.heapsize + 1
	A[A.heapsize] = - infinity
	HEAP-INCREASE-KEY(A, A.heapsize, key)
```


# Basic sorting algorithms
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
* An algorithm that sorts without altering the order of equal keys is said to sort in place


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
\Procedure{HEAPSORT}{$A$}
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


# Quicksort
* It is a divide and conquer algorithm
* The conquer and combine parts are really easy, but divide requires effort
	* This is sharply different from MERGESORT, where combine is the most demanding part
* Divide: we want to find indexes p, q, r such that the elements $A[p...q-1] \leq A[q] \leq A[q+1...r]$
	* q is determined by the PARTITION function
* Partioning: I want to create 4 zones with indeces p, i, j, r such that $A[p...i] \leq A[r] < A[i+1...j]$
	* A[r]=x is called pivot element and it can be choosen freely
	* Usually the implementation places x at the end of the array
	* The region $A[j+1...r-1]$ is unrestricted
	* The value returned by the partitioning step will be the q of the divide step
	* i is initialized to p-1 so that there are no elements between them
	* In the for loop j is always mooving
		* If the new element is bigger than x, nothing happens
		* If it is smaller, I increse i of 1 and place it in the new i position
		* What was previously in the i position is necessarilyh bigger than x, since it was in the j region, and so I place it as element j
		* After the end of the for I have a series of elements smaller than x, a series of elements bigger, and x itself at the end
		* I exchange x with the element i+1, which is necessarily bigger than it
		* Now x is what splits the array in a smaller and a bigger subarray, and so I return its index (i+1 now) which will be assigned to q
* The base case is when the subarray has 3, 2, or 1 elements
	* In this case the PARTITION function puts them in order
* Conquer: the 2 subarrays $A[p:q-1]$ and $A[q+1:r]$ are sorted recursively with QUICKSORT
* Combine: trivial, everithing is sorted because QUICKSORT sorts in place(!)


```pascal
QUICKSORT(A, p, r)
	if p < r
		q = PARTITION(A, p, r)
		QUICKSORT(A, p, q-1)
		QUICKSORT(A, q+1, r)

PARTITION(A, p, r)
	x = A[r]
	i = p - 1
	for j = p to r - 1
		if A[j] <= x
			i = i + 1
			exchange A[i] and A[j]
	exchange A[i+1] and A[r]
	return i + 1

QUICKSORT(A, 1, A.lenght)
```

* The running time depends on wether the array is balanced or not
	* This in turn depends on the choice of the pivot element x
	* The choice of the pivot influences the running time (!)
	* The array is balanced if the pivot cause a constant proportional split
	* If the array is balanced we are in the best case
* The worst case running time is $\Theta(n^2)$ (unbalanced array) and the average and best case running times are $\Theta(n\log{n})$
	* In practice we are almost always in the best case or close to it (!)
* The array is maximally unbalanced when it is already sorted (!)
	* In this case I have a subarray with 0 elements and one with n-1 elements
	* I do n-1 recursions, sicne at each step I decrease n by 1 and I stop when I get to 1
	* I pay a cost T(0) for the branch with 0 elements and a cost T(n-1) for the branch with n-1 elements
	* At each level of the tree I pay a fixed cost $\Theta(n)$ for the partitioning
	* $T(n) = T(n-1) + T(0) + \Theta(n)$
	* I have n calls of $\Theta(n)$ complexity: the cost is $\Theta(n^2)$
* The array is perfectly balanced when I get a constant proportional split
	* Doesn't matter the proportionality, it can also be a 1/100 to 99/100 split, as long as it is not 0 to n-1
	* In this case $T(n) = 2T(n/2) + \Theta(n)$
	* T(n) is of complexity $\Theta(n\log{n})$
* In a random array I expect a mix of good and bad splits
	* This only adds a constant term to the complexity
	* In this case I still have a complexity of $\Theta(n \log{n})$
* To assure that no particular input (i.e. a sorted array) cause the worst-case scenario of quicksort, I can use the randomized version of the algorithm
	* I can either randomize the input or the choice of the pivot


# Sone reflections on sorting
* All the algorithms we saw sort in place with the exception of MERGESORT
* A sort can be stable or not
	* Sorting stability is the preserving of the orders of records with equal keys
	* This is important for sorting keys with satellite data, to not mix up the satellite data order
		* If I order column A and then column B, I see that column A is not ordered anymore even for entries with the same keys on column B
	* Insertion sort and mergesort are stable, heapsort and quicksort are not stable
* All the algorithms we saw sort by comparing elements
* The lower bound for comparision-based sorting is $\Omega(n \log{n})$ because in the worst case I need to do at least n log n comparisons
	* Any comparison sort alogrithm must be able to sort any possible input of size n
	* There are n! possible permutations of an array of size n, and the algorthm must be able to solve all of them
	* Every permutation requires a different rearrangement of the array in order to be sorted
	* I can imagine a decision tree with n! leaves, corresponding to all the permutions
	* The height of the decision tree represent the number of single comparisons that the algorithm has to do in the worst case
	* A tree of heigh h has $2^h$ leaves, and so a tree with n! leaves has heigh $\log{n!}$
	* We saw before that $\Theta (n!) = \Theta (n \log{n})$
* Heapsort and Mergesort are asymptotically optimal comparison sort algorithms

# Counting sort
* It can sort in linear time since it is not based on comparison
* It assumes that the input array contains only integers in the range 0 - k
* For each element x into the array, determine how many elements are equal or smaller than x
* Put x in the correct position in the array
* It uses an input array A, an output array B and a counter array C
* I first create an array C of lenght k containing all 0s
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

```pascal
COUNTING-SORT(A, B, k)
	let C[0...k] be a new array
	for i = 0 to k
		C[i] = 0
	for j = 1 to A.length
		C[A[j]] = C[A[j]] + 1
	for i = i to k
		C[i] = C[i] + C[i-1]
	for j = A.length downto 1
		B[C[A[j]]] = A[j]
		C[A[j]] = C[A[j]] - 1
```

* The first and third for loops require both time $\Theta(k)$
* The second and last for loops require both $\Theta(n)$
* The total running time is $\Theta(n+k)$
* The running time is at minimum $\Omega(n)$, and O(n+k)
	* If k = O(n), then COUNTING-SORT runs in $\Theta(n)$
	* Since I use COUNTING-SORT only when k = O(n), in practice the algorithm runs in $\Theta(n)$
* COUNTING-SORT is stable
	* The last equal key element of A is the first to be put in B
	* The last for loop runs backwards, so the first element is put in the last position
	* Order is preserved
	* This is important because COUNTING-SORT is frequently used as a subroutine of RADIX-SORT
		* RADIX-SORT requires a stable sorting subroutine

# Radix sort
* It consideres the key as a number in base k, which has d digit and so occupies d columns
* It looks at 1 column at a time, starting from the LEAST significant and sorting it with any stable algorithm
	* If I start from the most significant, I need to recurse for sorting the least significant digits
	* If I start from the least significant and I use a stable sort, when I sort the most significant column everithing is correclty sorted
* It requires only a for loop with i from 1 to d
	* In each iteration it calls a stable sorting algorithm on column i
* It takes only d passes on the array

```pascal
RADIX-SORT(A, d)
	for i = 1 to d
		use a stable sort to sort A on digit i
```

* RADIX-SORT takes $\Theta(d*f(n))$ time, where f(n) is the running time of the subroutine used
* If I use COUNTIG-SORT as a subroutine, it take $\Theta(d(n+k))$
* In decimal notation k=9 since a column can only hold digits in the range 0 - 9
* Therefore when the base used is smaller than n, RADIX-SORT has complexity $\Theta(n)$
* RADIX-SORT is not stable and does not sort in place
	* If memory is a problem then QUICKSORT is better

# Dynamic sets
* In CS, differently from maths, sets can change
* A set supporting elementary operations is a dictionary
	* Elementary set operations are insertion, deletion and test membership
* Each set elements has key, and optional features
	* It can have satellite data
	* It can have a pointer, which points to another element in the set
* Set operations can be queries or modifying operations
	* A query always returns a pointer to an element in the set
	* A modifying operation modifies the set
		* INSERT(S,x) and DELETE(S,x)
* Dynamic sets can be represented with different data structures: stacks

# Stack
* It is a pile of elements on top of each other
* A new element is always added to the top of the stack: PUSH(S, x)
* Elements are always removed from the top of the stack: POP(S)
* Popping order is the reverse of the push order
	* They follow the last in first out (LIFO) policy
* A stack is NOT a good data structure for sorting and it is not used for this purpose
* Some applications of stacks
	* Storing undo history in text editors
	* Synthax parsing: evaluating missing parenteses
		* I push open and close parenthesis to the stack and pop twice when I find matching parenthesis
		* At the end of the file I require the stack to be empty
* A stack of n elements can be implemented with an array S[1..n]
* The S.top call returns the index of the top of the stack
* STACK-EMPTY(S) and STACK-FULL(S) return true or false in O(1)

```pascal
STACK-EMPTY(S)
	if S.top == 0
		return True
	else
		return False

STACK-FULL(S)
	if S.top == S.lenght
		return True
	else
		return False
```

* PUSH(S,x) is also O(1)
* If the size of the stack is not infinite I need first to check if it is full

```pascal
PUSH(S,x)
	if not STACK-FULL(S)
		S.top = S-top + 1
		S[S.top] = x
	else
		error "stack is full, cannot push"
```

* POP(S) returns the element we popped and removes it from the stack

```pascal
POP(S)
	if not STACK-EMPTY(S)
		S.top = S.top - 1
		return S[S.top + 1]

	else:
		error "stack empty, nothing to pop"
```

# Queue
* In a queue I use a FIFO policy instead of a LIFO
* I add elements to the queue with the enque operation in O(1)
	* New elements are added at the end of the queue
* Elements are removed with the dequeue operation
	* They are always removed from the top of the queue
* Also queues can be implemented with arrays
* Queues are circular, there is no end and beginning for the array (!)
	* For n elements I need an array of n+1 size (!)
	* This is because I need an empty element for marking the end of the queue
* I define several attributes for the queue
	* Q.head is the index of first element of the queue
	* Q.tail is the index of the last element of the queue + 1, it is the next available position
		* It points to an empty element of the array (!)
* Initally I have that Q.head = Q.tail = 1
* The queue is full when Q.head = Q.tail + 1 (circular case) or when Q.head = 1 and Q.tail = Q.lenght (linear case)

```pascal
QUEUE-EMPTY(Q)
	if Q.head == Q.tail
		return True
	else
		return False

QUEUE-FULL(Q)
	if Q.head == Q.tail + 1 or (Q.head == 1 and Q.tail = Q.lenght)
		return True
	else
		return False

ENQUEUE(Q,x)
	if QUEUE-FULL(Q)
		error "Queue is full, cannot add"
	Q[Q.tail] = x
	if Q.tail == Q.lenght
		Q.tail = 1
	else
		Q.tail = Q.tail + 1

DEQUEUE(Q)
	if QUEUE-EMPTY(Q)
		error "Queue is empty, nothing to dequeue"
	x = Q[Q.head]
	if Q.head == Q.lenght
		Q.head = 1
	else
		Q.head = Q.head + 1
	return x
```

# Arrays
* They are easy and fast to use, they can implement many data structures
* It is really inflexible for organising data
* I need (directly or nor) to specify the size of the array at the beginning
* I cannot implement all data structures with arrays

# Linked lists
* It is like an array where elements are next to each other
* The order is NOT determined by indeces, but by pointers in each element for the next element
* They are allocated dynamically when new elements are added
* L.head is a pointer to the first element of the linked list
* Each element x has 2 attributes
	* x.key is the content of the element
	* x.next is a pointer to the next element
* If x.next = NIL it means that we reached the end of the list
* If x.head = NIL the list is empty
* In double linked lists each elements has also a x.prev attribute
	* x.prev is a pointer to the previous element in the list
* Returning an element is O(1) in an array but O(n) in a linked list
	* I need to go through all the elements (!)
	* In this pseudocode if k is not in list I am returning NIL

```pascal
SEARCH-LIST(L, k)
	x = L.head
	while x != NIL and x.key != k
		x = x.next
	return x
```

* Inserting at the beginning of a double linked list is O(1)

```pascal
LIST-INSERT(L, x)
	x.next = L.head
	if x.head != NIL
		L.head.prev = x
	L.head = x
	x.prev = NIL
```

* Deleting when I have a pointer x is general and it takes also O(1)

```pascal
LIST-DELETE(L, x)
	if x.prev != NIL
		x.prev.next = x.next
	else
		L.head = x.next
	if x.next != NIL
		x.next.prev = x.prev
```

# Rooted trees
* We already saw how to represent a binary rooted tree with arrays
* I can represent them also with linked lists
* Each element x of the linked list will contain
	* x.left and x.right, pointers to the childrens
	* x.p is a pointer to the parent
	* x.key and x.data are key and satellite data
* Some properties of the tree T
	* T.root is a pointer to the root
		* T.root.p = NIL
	* The tree is empty if T.root = NIL
	* If x.left and x.right are NIL x doesn't have children nodes
* I am not cenessarily limited to binary trees with linked lists
	* I can have x.child1, x.child2, x.childk
	* This is wasteful since I need to know the number of children in advance (!)
* I can do it more efficiently
	* x.child is the first chilf of x
	* x.child.sibiling is the next child of x
	* If x.child.sibiling = NIL x.child is the last children
	* The children are themselves a linked list (!)

# Hash tables
* Dictionaries are really useful in many scenarios in CS
	* They implement INSERT, SEARCH and DELETE operations
	* An hash table can be used for implementing a dictionary
* An hash table is a generalization of a simple array
	* I have n elements that associated with one key each
	* The keys are drawn from the key universe U of size m
	* The key of each element is unique
* I can represent the hash table with an array T[0...m-1]
	* Each position in T is called slot and maps to a key in U
	* For each element x with key k, T[k] contains x itself or a pointer to it
	* If no elements has key k, then T[k] = NIL
* I can implement SEARCH, INSERT and DELETE with hash tables in O(1)

```pascal
SEARCH(T,k)
	return T[k]

INSERT(T,x)
	T[x.key] = x

DELETE(T,x)
	T[x.key] = NIL
```

* In general U can be very large, so I do not really store it
	* I only store the U subset K containing the keys that I am actually yusing
* An hash function maps every input to a slot in the hash table
	* In this case I reduce U to K, which has size m
	* We will not study hash functions, but we assume them to be well designed and to output with equal probability to each slot
* It can happen that 2 elements hash to the same slot, and I define this as a collision
	* It is impossible to completely avoid collisions, since m is smaller than the univers U of possible elements
	* When I have a collision I create a linked list of the elements hashing at that location
* The size of the hash table influences the speed in operating with it
	* If it has only 1 element essentially I don't have an hash table but a linked list
	* If it is too big it requires a lot of space
	* Typically the right size is 1/5 to 1/10 of the number of elements
* I can keep the list ordered or not
	* If not ordered inserting is faster and I can implement a LIFO behaviour
* In a chained hash insert I usually insert new elements at the top of the respective linked list
	* Inserting is O(1) and searching is O(k), with k lenght of the list
	* Deleting takes O(k) if the list is single linked, O(1) if double-linked
		* I assume that I have a pointer for x so I don't have to search it
		* If the list is single linked I need to find the predecessor of x in order to recreate the list (!)
* The load factor $\alpha$ of an hash table is the number of elements in the table n divided by the number of slots m
	* $\alpha = n/m$
	* This is true if I assume that every slot has the same probability to be hashed by an element
	* $\alpha$ can be 1, bigger or smaller
* The worst case in hash table searching is an unsuccessful search
	* The time complexity is $O(1+\alpha)$
		* O(1) is required for computing the hash function
	* I need to look through the whole table (!)
	* If I assume m to be proportional to n I have that $m=O(n)$
	* In this case $\alpha=O(1)$ since $O(n)/O(n)=O(1)$

# Binary search trees
* It can be used both as a dictionary and as a priority queue
* On average all operations are O(log n), with a worst case O(n)
	* Tree walks are an exception and always require O(n) since they go across the whole tree
* It can be represented by a linked list with parent, left child, right child, key attributes
* They respect the binary search tree property
	* The key of all the elements in the left subtree of node x are smaller or equal to x.key
	* The key of all the elements in the right subtree of node x are bigger or equal to x.key
* In the following algorithms the initial calls are with x equal to a pointer to the root of the tree
* Inorder tree walk: print the keys in sorted order
	* For each node, I need to print first the left child, then the node itself, then the right child

```pascal
INORDER-TREE-WALK(x)
	if x is not NIL
		INORDER-TREE-WALK(x.left)
		print x.key
		INORDER-TREE-WALK(x.right)
```

* Preorder tree walk: root is printed first, then the children in order

```pascal
PREORDER-TREE-WALK(x)
	if x is not NIL
		print x.key
		INORDER-TREE-WALK(x.left)
		INORDER-TREE-WALK(x.right)
```

* Postorder tree walk: the children in order are printed first, then the root

```pascal
POTSORDER-TREE-WALK(x)
	if x != NIL
		INORDER-TREE-WALK(x.left)
		INORDER-TREE-WALK(x.right)
		print x.key
```

* Search a key x: at every level I half the search space
	* If the current node is smaller than x I go to the right child, if it is bigger I go to the left child, If it is equal I stop
	* I go recursively until I find the key or I finish the tree
* This recursive approach has complexity proportional to the height of the tree O(h)

```pascal
TREE-SEARCH(x,k)
	if x == NIL or k == x.key
		return x
	if k < x.key
		return TREE-SEARCH(x.left,k)
	else
		return TREE-SEARCH(x.right,k)
```

* I can do the same also iteratively

```pascal
ITERATIVE-TREE-SEARCH(x,k)
	while x is not NIL and k is not x.key
		if k < x.key
			x = x.left
		else
			x = x.right
	return x
```

* Finding the minimum key: always go left
	* The running time is O(h), so on average O(log n)
* Finding the maximum: always go right
	* It is equivalent to finding a minimum

```pascal
TREE-MINIMUM(x)
	while x.left != NIL
		x = x.left
	return x

TREE-MAXIMUM(x)
	while x.right != NIL
		x = x.right
	return x
```

* If all keys are distinct, the successor of x is defined as the y such that y.key is the smallest key bigger or equal to x
	* It is the smallest element with key equal or bigger than that of x
* If x has a right subtree, the successor of x is the minumum of x.right
* If it has not, I need to go up the tree until I find a node that is the left child of its parent
	* The successor of x is the parent of that node
* If x is the biggest element of the tree I return NIL

```pascal
TREE-SUCCESSOR(x)
	if x.right != NIL
		return TREE-MINIMUM(x.right)
	y = x.p
	while y != NIL and x == y.right
		x = y
		y = y.p
	return y
```

* The predecessor of x is the node y for which x is its successor
	* It is the node with the biggest key that is smaller than that of x
	* The pseudocode is symmetrical to that for the successor

```pascal
TREE-PREDECESSOR(x)
	if x.left != NIL
		return TREE-MAXIMUM(x.right)
	y = x.p
	while y != NIL and x == y.left
		x = y
		y = y.p
	return y
```

* Insertion: always at the leaves (!)
	* I want to insert an element z such that z.key = v
	* I start from the root and maintain 2 pointers
		* x is the current node
		* y is the parent of x (trailing pointer)
	* If x.key is smaller than v I go to the right, otherwise I go to the left
	* When x = NIL we are at the correct position
		* If v is smaller than y.key, then I insert z as y's left child
		* Otherwise I insert it as right child
	* The running time is O(h)

```pascal
TREE-INSERT(T,z)
	y = NIL
	x = T.root
	while x != NIL
		y = x
		if z.key < x.key
			x = x.left
		else
			x = x.right
	z.p = y
	if y == NIL
		T.root = z
	elif z.key < y.key
		y.left = z
	else
		y.right = z
```

* Deletion: it is complicated
	* If z has no children I just remove a pointer to it from its parent
	* If z has 1 child I set the pointer of its parent to z child instead of z itself
		* I also need to update the parent of z's child
	* If z has 2 children it is complicated
		* z's successor y is the minimum element in z's right subtree
		* y cannot have a left child since there cannot be elements smaller than y in that subtree
		* I delete y from the tree and replace z with y
* To make the code for delete easier to read I define a function TRANSPLANT
	* It replaces the subtree rooted at u with the one rooted at v
	* I check if u is the root
		* In this case I put v as the root
		* If not, I check if u is the left child of its parent
			* In this case, I put v as left child of u's parent
			* If not, it means that u is the right child of its parent
			* In this case, I put v as right child of u's parent
	* At the end I update the parent of the moved subtree v to make it equal to that of the previous subtree u

```pascal
TRANSPLANT(T,u,v)
	if u.p == NIL
		T.root = v
	elseif u == u.p.left
		u.p.left = v
	else
		u.p.right = v
	if v != NIL
		v.p = u.p
```

* Now we can describe the delete pseudocode
	* If z doesn't have a left child, I transplant the whole right subtree of z to z's parent
		* If there is no right subtree, I just put NIL as right childso it's ok
	* If z doesn't have a right child, I do the same with the left subtree
	* If both checks failed, z has 2 children
		* I set y as z's successor (minimum of its right subtree)
		* if the parent of y is not z
			* I remove y from the tree by transplanting it with its right child (it cannot have a left child!)
			* I replace z with y
			* I update the right child of y to that of z
			* I update the parent of the right child of y (that was of z before) to be y itself
		* I transplant z with y
		* I update pointers for y.left and for the parent of the new y.left

```pascal
TREE-DELETE(T,z)
	if z.left == NIL
		TRANSPLANT(T,z,z.right)
```

* All the operations in binary search trees are O(h)
* This means that they are fast when the tree is not too deep

# Ivan Lanese module

---

# Introduction
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

# Balanced search trees
* A balanced tree is a bynary search tree (BST) that minimizes the height of the tree
	* In a BST the left subtree contains elements smaller than the root, the right subtree bigger
	* The BST property is useful for lookups and must be mantained by insertions and deletions
* I BSTs insertion and delition have a complexity linear with the height of the tree, $O(h)$
	* In a complete BST $h=\log{n}$, so insertion and deletion are $O(\log{n})$ with $n =$ number of nodes
* Insertions and deletions can make a complete BST unbalanced
* A tree built from ordered elements is maximally unbalanced
	* A way to create a generally balanced tree is to randomly permutate the input data when constructing the tree
* Modifications of BST have been developped for maintaining it as balanced as possible

# AVL trees
* AVL trees are almost balanced BST that support `insert()`, `delete()` and `lookup()` in $O(\log{n})$ time
* AVL introduce a balancing factor for each node $\beta(n)$
	* It is the difference in the height of the 2 subtrees of the node
	* A tree is balanced if for each node $|\beta|$ is less than 1

## Proof that for AVL $h=O(\log{n})$
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

## Operations in AVL trees
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

## AVL insertion
* I insert a new value like in a normal BST
* I recalculate $\beta$ for all nodes that contain the leaf
	* In the worst case I need to calculate it for one node for each leavel from the leaf to the root, so it is $O(h)=O(\log{n})$
* If at least 1 node has $|\beta| > 1$ I need to rebalance the tree with rotations from bottom to top, in $O(1)$
* In total, an insertion in an AVL tree takes $O(\log{n})$

## AVL deletion
* I remove like in a normal BST
* I rebalance like for the insertion

All the basic operations in AVL take $O(\log{n})$

# Working on disk
* Big data structures cannot be kept in memory but need to be partially loaded in memory from disk, when needed
* Computational time is heavily dependent on the number of r/w operations into disk, since it is much slower than memory
* There are data structures that minimize disk access

# 2-3 trees
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

## Insertion in 2-3 trees
* I create al leaf `v` with key `k`
* I search for a node `u` at the penultimate level, that will become father of `v`
* If possible I add `v` as a child of `u`
* If `u` has already 3 children, I do a recursive splitting back until it is needed
* It takes $O(\log{n}$ to find the father of the new node and $O(1)$ to do the splitting
* In the worst case I do $O(\log{n})$ splits back until the root
* The overall insertion cost is $O(\log{n})$

## Deletion in 2-3 trees
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

# Exercise on recursion
Write a recursive function that computes the height of a node
```python
def h(node):
	if ((n is leaf) or (n==None)): # n is a leaf or it is not existent
		return 0
	else:
		return max(h(n.left),h(n.right))+1
```
Computing the height of a node recursively has complexity O(n)

# B-trees
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

## Search in B-trees
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

## Insert in B-trees
* I search the leaf $f$ in which I can insert the key $k$
* If the leaf is not full (less than 2t-1 keys) I insert $k$ in the correct position
* If it is full I split the leaf $f$
	* I put the key number $t$ of $f$ to $f.parent$
		* If $f.p$ is full I need to split it and recurse
		* In the worst case this will split the root and generate a new one
* I cannot use binary search in this case since I cannot split an array in that way, I need to copy half of its elements in $O(t)$
* Total cost is $O(t \log_t{n})$

## Delete in B-trees
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

# Graphs
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

## Representations
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

## Graph trasversal
* It refers to the problem of visiting all the vertices of a graph
* The 2 most used graph trasversal algorithms are BFS and DFS

### Breath-first search (BFS)
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

### Depth-first search (DFS)
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

## Topological sort
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

# Greedy algorithms
* It always makes the locally optimal choice
* It is not guaranteed to give a globally optimal solution
* It is normally easy to code
* A problem has optimal substructure if the solution contains the solution of its subproblems

## Knapsack problem
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

## Huffman Codes
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

# Dynamic programming
* It was developped in 1950 by Bellman
* It is similar to divide et impera, but it stores the solution of subproblems (it has memoization)
* It requires the problem to have optimal substructure
* It can be implemented recursively (divide et impera with memoization) or iteratively (on a matrix)
	* The iterative version requires to be able to sort the problems so that I can solve all the dependecies of a problem before solving it
	* The recursive implementation is also called top-down and the iterative bottom-up
	* The iterative version has usually smaller constant factor because I avoid the many function calls

## Knapsack problem
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

# Shortest Path
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

## Relaxation
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

## Dijkstra Algrithm
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
	* Branch refers to the branching of possibilities at each step, bound to the application of a lower bound to their cost
* I have a minimization problem where $\phi(S)$ is the cost function for solution $S$
* I define the function LB that estimates a lower bound on the cost of any feasible solution from a partial solution 
	* This function depends on the specific problem!
* I define $S^*$ as the best known solution at any given node of the search tree and $z^*$ its cost
* At any point if $LB(S,i) \geq z^*$ I can prune that branch of the tree and avoid evaluating it
	* No need to evaluate a branch that will lead to a worse solution than those I already found
* In general I need an initial solution to be used as a first $z^*$
	* I can choose it randomly or with heuristics

# Exam info
* Exam will be written, but you can do oral if you want
