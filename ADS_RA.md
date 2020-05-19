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
* The LCA problem is a classical problem that can be solved with dynamic programming
