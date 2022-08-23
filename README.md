# Garbled Merkle Tree

Imagine that multiple parties are collaborating on computation. Imagine that to
ensure computation accuracy that multiple parties will perform the same calculation.
In a decentralized network, we need to ensure all parties:

  1. do not shirk the responsibility to perform the calculations asked of them and
  2. perform the calculations accurately.

There are [Economic ways to Influence](Economic-Influences.md) this outcome.

### Garbled Circuits

On approach to solving this problem is by means of a 
[Garbled Circuit](https://en.wikipedia.org/wiki/Garbled_circuit). Vitalik Buterin provides 
[nice introduction](https://vitalik.ca/general/2020/03/21/garbled.html) to Garbled Circuits.

### Why a Binary Tree

The goal is not provide a general solution to all problems but by showing a solution to one 
problem we can show that a whole class of problems can be solved. The complexity of
the problem in both [time](https://en.wikipedia.org/wiki/Time_complexity) and 
[space](https://en.wikipedia.org/wiki/Space_complexity) will not remain the same, 
but the solvability of a solution will remain the same.

Many computing problems can be represented as a 
[Directed Acyclical Graph (or DAG)](https://en.wikipedia.org/wiki/Directed_acyclic_graph).

Other computing problems can be represented as a [Cyclical Graph](https://en.wikipedia.org/wiki/Cycle_graph) 
these can be by 

With a bit of effort one can show the equivalence between these two problems and a finite
deterministic [Turing Machine](https://en.wikipedia.org/wiki/Turing_machine). Each stopping
point in the Turing Machine is a node in the Graph. Each movement of the Turing Machine tape head 
is a line between two nodes in a graph. Because the Turing Machine is finite, there are at most
M stopping locations for the tape machine head. If we constrain the Turing Machine so that each
node is visited only once, then there are at most M transitions which means
the Turing machine can be represented as a Graph with M nodes.

This is reasonable because computing problems execute in finite time with finite resources.
The state of the entire computer storage at any given point in time can be considered a stopping point
in a Turing machine or a node in a Graph. Updating a memory location can be seen as visiting another node rather than the first node. 
Each operation can be seen as a transition from one node to the another.

A DAG can be converted to an [M-Ary Tree](https://en.wikipedia.org/wiki/M-ary_tree) by:

   - Adding a parent node above all root nodes which then become children of this newly created parent/root node.
   - Whenever a subtree has more than one parent we can duplicate the subtree at both parents.

We can convert an M-Ary Tree to a [Binary Tree](https://en.wikipedia.org/wiki/Binary_tree) 
by introducing intermediate nodes:

   - Whenever a node has more than 2 children, we select two of the children and add an intermediate
     node as a new parent of these two nodes. For example, if node A has children B, C and D. Then we introduce a node E which has
     children B and C. A now has children E and D. 
     We repeat this step until there are no more than two children per node.

Various [Tree rebalancing algorithms](https://en.wikipedia.org/wiki/Tree_rotation#Rotations_for_rebalancing) 
show a logical mapping from any binary tree of X leaves to any other binary tree of X leaves.

### Logical mapping of And/Or/Xor/etc. Gate inputs/outputs to Merkle Tree Hash values.

The goal is to demonstrate that using hashes can be seen as a logical for a computation step
or set of computation steps. 

  - A set of inputs and corresponding outputs for a circuit can be seen as a unique state or node.
  - The intermediary inputs and outputs from internal gates can be seen as supplemental states
    which may or may not be represented. We can create a one-to-one mapping from the
    inputs to the outputs for a circuit regardless of the intermediary nodes.

Any set of inputs and output can be reasonably considered to be represented by a unique 256 hash 
such as a SHA-256 hash value. This value can then be encrypted by as Symmetric key known only to the
encryptor. In practice a weaker encoding might be considered for hashing and encryption since
cracking the encryption would cost more than performing the computation.

### Digital Identity

A follow in requirement is to verify that a specific Actor performed the computations correctly and
should receive a reward. A couple of ideas in this area are:

- [Decentralized Digital Certificates](https://oblivc.org/docs/dca.pdf) and
- [Self-Sovereign Identity](https://en.wikipedia.org/wiki/Self-sovereign_identity).
