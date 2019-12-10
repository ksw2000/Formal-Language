# The Definition of Algorithm
Informal definition:<br> An algorithm is a collection of simple instructions for carrying out some task.

Formal definitions:<br>
+ Using λ-calculus by Alonzo Church in 1936
+ Using Turing machine by Alan Turing in 1936

### Computable Functions
The association between inputs and outputs is called a function.

The process of determining an output of a function from its input is called computing the function

The set of functions that are computable by a computational system is a measure of the computational power of that system.

### Church-Turing thesis
The Church-Turing thesis states taht if an algorithm (a procedure that terminates) exists then there is an equivalent Turing machine or applicable λ-function for that algorithm.

The computational power of Turing machines is as great as any algorithmic system.

圖靈機即現代電腦的數學模型，利用圖靈機可知道一個問題是否可以用電腦解決。

### Implications of Church-Turing Thesis
Computable functions and Turing-computable functions are the same.

Using the set of Turing-computable functions as a test set for comparing the computational powers of various computational system.

If a computational system is capable of computing all the Turing-computable functions, it is considered to be a universal system.

### Hilbert's Problems
In 1900, German Mathematician David Hilbert identified 23 mathematical problems as a challenge for the coming century.

Hilbert's Problems: Devise an algorithm that tests whether a polynomial has an integral root.

In 1970, Yuri Matijasevic *showed that no algorithm exists* for testing whether a polynomial has integral roots.

D = { p | p is a polynomial with an integral root}<br>
D<sub>1</sub> = { p | p is a polynomial over x with an integral root}<br>
D and d<sub>1</sub> are Turing-recognizable

Here is a TM M<sub>1</sub> that recognizes

M<sub>1</sub> = "The input is a polynomial p over the variable x"

Evaluate p with x set successively to the values 0, 1, -1, 2, -2, 3, -3, ... If at any point the polynomial evaluates to 0, accept."

If p has an integral root, M<sub>1</sub> eventually will find it and accept (如果是單變數函數有整數根我們都能分辨出來). If p does not have an integral root, M<sub>1</sub> will run forever. __For the multivariable case__, we can present a similar TM M that recognizes D. Here M goes through all possible settings of its variables to integral values.

__Both M<sub>1</sub> and M are recognizes but not deciders.__ We can convert __M<sub>1</sub> to be a decider for D<sub>1</sub>__ because we can calculate bounds within which the roots of a single variable polynomial must lie and restrict the search to these bounds. In this problem, you are asked to show that the roots of such a polynomial must lie between the values.

p(x) = a<sub>0</sub>+a<sub>1</sub>x<sup>1</sup>+a<sub>2</sub>x<sup>2</sup>+...+a<sub>n</sub>x<sup>n</sup>

bound: x in ± k (C<sub>max</sub> / C<sub>1</sub>)

Where __k__ is the number of terms in the polynomial, __c<sub>max</sub>__ is the coefficient with largest absolute value, and __c<sub>1</sub>__ is the coefficient of the highest order term. If
a root is not found within these bounds, the machine __reject__

Hilbert’s tenth problem:
+ D<sub>1</sub> is __Turing-decidable__. (單個變數的多項式)(可解)
+ D is __Turing-recognizable__, but __NOT Turing-decidable__. (多個變數的多項式)(不可解)

Turing-decidable 的情況下才能討論時間複雜度，並用時間複雜度區分困難或簡單，比如多項式時間，這種問題都算簡單，但如果是2<sup>n</sup>則屬於困難的問題。

而 Turing-decidable 和 Turing-recognizable 則是決定這問題可不可解

### Terminology or Describing Turing Machines
Representations of algorithms are generally classed into three accepted levels of Turing machine description:
1. High-level description
2. Implementation description
3. Formal description

### Encoding input into an string
We now set up a format and notation for describing Turing machines. The input to a Turing machine is always a string. If we __want to provide an object other than a string as input__, we must first represent that object as a string. Strings can easily represent polynomials, graphs, grammars, automata, and any combination of those objects. A Turing machine may be programmed to decode the representation so that it can be interpreted in the way we intend. Our notation for the encoding of an object O into its representation as a string is <O> . If we have several objects O<sub>1</sub>,O<sub>2</sub>,...,O<sub>k</sub>, we denote their encoding into a single string <O<sub>1</sub>,O<sub>2</sub>,...,O<sub>k</sub>>. The encoding itself can be done in many reasonable ways. It doesn't matter which one we pick because a Turing machine can always translate one such encoding into another.

#### Example
Let A are the language consisting of all strings representing undirected graphs that are connected. Recall that a graph is connected if every node can be reached from every other node by traveling along the edges of a graph. We write

A = { < G > | G is a connected undirected graph }

The following is a __high-level description__ of a TM M that decides A.

M = On input < G >, the encoding of a graph G":

    1. Select the first node of G and mark it.
    2. Repeat the following stage until no new nodes are marked :
        3. For each node in G, mark it if it is attached by an edge to a node that is already marked.
        4. Scan all the nodes of G to determine whether they all are marked. If they are, accept; otherwise, reject

![](https://imgur.com/51k0OHV.png)
(透過程式檢查一個圖有沒有連通)
