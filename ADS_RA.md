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
