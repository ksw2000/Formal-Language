# The Halting Problem

One of the most philosophyically(哲學地) important theorems of the theory of computation: There is a specific problem that is __algorithmically unsolvable__.

The general problem of software verification is not solvable by computer.

The problem of determining whether a Turing machine accepts a given input string:
A<sub>TM</sub> = { &lt; M,w &gt; | M is a TM and M accepts w}.

### Theorem: A<sub>TM</sub> is undecidable

Before we get to the proof, let's first observe that A<sub>TM</sub> is Turing-recognizable. Thus this theorem shows that recognizers are more powerful than deciders. Requring a TM to halt on all inputs restricrt the kinds of languages that it can recognize. The following Turing machine U recognizes A<sub>TM</sub>.

__U = "On input &lt;M,w&gt;, where M is a TM and w is a string":__

1. __Simulate M on input w__
2. __If M ever enters its accept state, accpet; if M ever enters its reject state, reject.__

__Proof__

We assume that A<sub>TM</sub> is decidable and obtain a contradiction. Suppose that H is a decider for A<sub>TM</sub>. On input &lt;M, w&gt;, where M is a TM and w is a string, H halts and accpets if M accepts w. Furthermore, H halts and rejects if M fails to accept w. In other words, we assume that H is a TM, where

H(&lt;M,w&gt;) = accept , if M accepts w; otherwise reject

Now we construct a new Turing machine D with H a subroutine. This new TM calls H to determine what M does when the input to M is its own description &lt;M&gt;. Once D has determined this information, it does the opposite. That is, it rejects if M accepts and accepts if M doesn't accept. The following is a description of D.

D = "On input &lt;M&gt;", where M is a TM:

1. Run H on input &lt;M.&lt;M&gt;&gt;
2. Output the opposite of what H outputs; that is, if H accepts, reject and if H rejects, accpte.

D(&lt;M&gt;) = accept , if M does not accepts w; otherwise reject

What happens when we run D with its own descript &lt;D&gt; as input? In that case we get

D(&lt;D&gt;) = accpect if D does not accept &lt;D&gt;; if D accepts &lt;D&gt;

No matter what D does, it is forced to do the opposite, which is obviously a contradiction. __Thus neither TM D not TM H can exist__.

Let's review the steps of this proof. Assume that a TM H decides A<sub>TM</sub>. Then use H to build a TM D that when given input &lt;M&gt; accepts exactly when M does not accept input &lt;M&gt; accepts exactly when M does not accept input &lt;M&gt;. Finally, run D on itself. The machines take the following actions, with the last line being the contradiction.

+ H accepts &lt;M, w&gt; exactly when M accepts w.
+ D rejects &lt;M&gt; exactly when M accepts &lt;M&gt;.
+ D rejects &lt;D&gt; exactly when D accepts &lt;D&gt;.

### The Diagonalization Method (一種證明的方法)

The proof of the undecidability of the halting problem uses a technique called diagonalization, discovered by Georg Cantor in 1973.

Let __N__ be the set of natural numbers and let __ε__ be the set of even natural numbers. Using Cantor's definition of size we can see that __N and ε have the same size__. The correspondence f mapping N to ε is simply f(n)=2n. __(自然數所成的集合和偶數所成的集合有相同的大小)__

### Definition (Countable)

A set _A_ is __countable__ if either it is __finite__ or it has __the same size as N__.

### The set of real number is uncountable

### Some languages are not Turing-recognizable

To show taht the set of all Turing machines is countable we first observe that the set of all strings Σ* is countable, for any alphabet Σ. With only finitely many strings of each length, we may form a list of Σ* by writing down all strings of length 0, length 1, length 2, and so on.

The set of all Turing machines is countable because each Turing machine M has an enoding into a strings &lt;M&gt;. If we simply omit those strings that are not legal encodings of Turing machines, we can obtain a list of all Turing machines.

To show that the set of all language is uncountable we first observe that the set of all infinite binary sequences is uncountable. An infinite binary sequence is an unending sequence of 0s ad 1s. Let B be the set of all infinite binary sequences. We can show that B is uncountable by using a proof by diagonalization similar to the one we used in Theorem 4.17 to show that R is uncountable.

Let L be the set of all languages over =
