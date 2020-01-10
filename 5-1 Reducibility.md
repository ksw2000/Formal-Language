## Reducibility (可歸約性)

#### Closure Properties (封閉性) of  __Regular Languages__:

The class of regular languages is __closed under__ union, intersection, subtraction, complementation, concatenation, Kleene star, and reversl.

#### Closure Properties (封閉性) of Context Free Languages:

The  class of context-free languages __is not closed under__ intersection, or complementation.

#### Closure Properties of Decidable Languages:

The class of decidable languages is closed under union, intersection, complementation, concatemation, Kleene star.

#### Closure Properteis of Turing-recognizable Languages:

The class of Turing-recognizale languages is closed under union, intersection, concatenation, Kleene star.

---

## Basic Ideas

+ The acceptance prolem A<sub>TM</sub> is a computationally unsolvable problem.

+ This chapter introduces more unsolvable problems.

+ __Reducibility is the primary method for proving that problems are computationally unsolvable. (利用可歸約性證明一個問題是不可解的)__

+ **Reduction** is a way of converting one problem to another problem in such a way that a solution to the second problem can be used to solve the first problem.

+ If problem A reduces to problem B ( A ≤ <sub>m</sub>B), then we can use a solution to B to solve A. For example, the problem of measuging the area of a rectangle reduces to the problem of measuring its length and width.

+ In computability theory, if A is reducible to B and B is decidable, then A is also decidable. Equivalenty, if A is undecidable and reducible to B, then B is undecidable. (如果 問題 A 可以歸約成 問題 B，且 問題 B 是 decidable 那麼 問題A 也是 decidable，反之亦然) ex: 圓的面積可以歸約成圓的半徑，所以如果你知道圓的半徑那麼你就能知道約的面積

+ The acceptance problem A<sub>TM</sub> is undecidable.

## 5.1 Undecidable Problems from language Theory

The halting problem, HALT<sub>TM</sub> , is the problem of determining whether a Turing machine halts on a given input.

HALT<sub>TM</sub>= {&lt; M, w &gt; | M is a TM and M halts on input w }

#### Theorem: HALT<sub>TM</sub> is undecidable

**proof** (利用 reducible 的特性 )

Let's assume for the purposes of obtaining a contradiction that Turing machine R decides HALT<sub>TM</sub>. We construct TM S to decide A<sub>TM</sub>, with S operating as follows.

S = " On input &lt; M, w &gt; , an encoding of a TM M and a string w : "

1. Run TM R on input &lt; M, w&gt;

2. If R rejects, reject

3. If R accepts, simulate M on w until it halts.

4. If M accepted, accept; if M has rejected, reject. 

----

# ↑ 期末考範圍 ↑

-----

#### Theorem: E<sub>TM</sub> is undecidable

#### Theorem: EQ<sub>TM</sub> is undecidable

#### Theorem: Regular<sub>TM</sub> is undecidable
