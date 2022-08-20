# Garbled Merkle Tree

Imagine that multiple parties are collaborating on computation. Imagine that to
ensure computation accuracy that multiple parties will perform the same calculation.
In a decentralized network, we need to ensure all parties:

  1. do not shirk the responsibility to perform the calculations asked of them and
  2. perform the calculations accurately.

### Garbled Circuits

On approach to solving this problem is by means of a 
[Garbled Circuit](https://en.wikipedia.org/wiki/Garbled_circuit). Vitalik Buterin provides [nice introduction](https://vitalik.ca/general/2020/03/21/garbled.html) 
to Garbled Circuits.

### Why a Binary Tree

The goal is not provide a general solution to all problems but by showing that a solution to one 
problem we can show that a whole class of problems can be solved in the same 
[order of magnitude](https://en.wikipedia.org/wiki/Order_of_magnitude) in 
both [space](https://en.wikipedia.org/wiki/Space_complexity) 
and [time](https://en.wikipedia.org/wiki/Time_complexity) complexity.

Many computing problems can be represented as a 
[Directed Acyclical Graph (or DAG)](https://en.wikipedia.org/wiki/Directed_acyclic_graph).

Recursive computing problems can be represented as a [Cyclical Graph](https://en.wikipedia.org/wiki/Cycle_graph) 
......

With a bit of effort one can show the equivalence between these two problems are a finite
deterministic [Turing Machine](https://en.wikipedia.org/wiki/Turing_machine). Each stopping
point in the Turing Machine is a node in the Graph. Each movement of the Turing Machine tape head 
is a line between two nodes in a graph. Because the Turing Machine is finite, there are at most
M stopping locations for the tape machine head. So there are at most M transitions which means
the Turing machine can be represented as a Graph with M nodes.

A DAG can be converted to an [M-Ary Tree](https://en.wikipedia.org/wiki/M-ary_tree) by:

   - Adding a parent node above all root nodes which are now it's children.
   - Whenever a subtree has more than one parent we can duplicate the subtree at both parents.

We can convert an M-Ary Tree to a [Binary Tree](https://en.wikipedia.org/wiki/Binary_tree) 
by introducing intermediate nodes:

   - Whenever a node has more than 2 children we select two of the children and add an intermediate
     node. For example, if node A has children B, C and D. Then we introduce a node E which has
     children B and C. A now has children E and D. We repeat this step until there are no more than to 

[Various Tree rebalancing algorithms](https://en.wikipedia.org/wiki/Tree_rotation#Rotations_for_rebalancing) 
show a logical mapping from any binary tree of X leaves to any other binary tree of X leaves.

### Logical mapping of And/Or/Xor/etc. Gate inputs/outputs to Merkle Tree Hash values.

The goal is to demonstrate that using hashes can be seen as a logical for a computation step
or series of computation steps. 

  - Each 

