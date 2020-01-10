# Decidable Languages

+ Turing machine is a model of a general purpose computer.

+ By Church-Turing Thesis, the notion of algorithm is defined in terms of Turing machine algorithm.

+ The objective of this chapter is to __explore the limits of algorithmic solvability__.

---

## Decidable Problems Concerning Regular Languages

### Theorem 4.1: A<sub>DFA</sub> is a decidable language

Represent computational problems by languages

The acceptance problem for DFAs can be expressed by language.

__A<sub>DFA</sub> = {&lt; B,W &gt; | B is a DFA taht accepts the input string w }__

We simply need to present a __Turing machine M__ that decides A<sub>DFA</sub>.

M = "On input &lt; __B__, __w__ &gt;, where __B is a DFA__ and __w is a string__": (利用圖靈機模擬DFA，即輸入一個DFA和一個字串)

1. __Simulate B on input w.__
2. __If the simulation ends in an accept state, accept. If it ends in a nonaccepting state, reject.__

如果 DFA 最後停在 accept state 那這個圖靈機 M 也回傳 accept，反之回傳 reject

The problem of testing whether a DFA. B acceppts

__proof__

We mention just a few implementation details of this proof. For those of you familiar with writing programs in any standard programming language, imagine how you would write a program to carry out the simulation.

First, let's examine the input &lt;B, w&gt;. It is a reqresentation of a DFA B together with a string w. One reasonable representation of B is simply a list of its __five components, Q, Σ, δ, q<sub>0</sub> and F__. When M receives its input, M first determines whether is properly represents a DFA B and a string w. If not, M rejects.  (當 M 接收到輸入時，M 第時間就會決定這字串是否符合，要是不符合會回傳 reject)

Then M carries out the simulation directly. It keeps track of B's current state and B's current position in the ipnut w by writing this information down on its tape. Initially, B's current state is q<sub>0</sub> and B's current input position is the leftmost symbol of w. The states and position are updated according to the specified transition function δ. When M finishes processing the last symbol of w, M accepts the input if B is in an accepting state; M rejects the input if B is in a nonaccepting state.

### Theorem 4.2: A<sub>NFA</sub> is a decidable language

__proof__
We present a TM N that decides A<sub>NFA</sub>. We could design N to operate like M, simulating an NFA instead of a DFA. Instead, we'll do it differently illustrate a new idea: have N use M as a subroutine. Because M is designedto work with DFAs, N first coverts the NFA it recives as input to a DFA be passing it to M.

N = "On input &lt; __B__, __w__ &gt; where B is an NFA, and w is string":

1. Convert NFA B to an equivalent DFA C

2. Run TM M from Theorem 4.1 on input &lt;C, w&gt;

3. If M accepts, accept; otherwise, reject

### Theorem 4.3: A<sub>REX</sub> is a decidable language

__proof__
The following TM P decides A<sub>REX</sub>.
P = "On input &lt; __R__, __w__ &gt; where R is a regular expression and w is a string":

1. Convert regular expression R to an equivalent NFA A

2. Run TM N on input &lt;A, w&gt;

3. If N accepts, accept; otherwise, reject

---

## Decidable Problems Concerning CFL

### Theorem 4.7: A<sub>CFG</sub> is a decidable language

(P.15 待)
