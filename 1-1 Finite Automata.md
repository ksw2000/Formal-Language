# 1-1 Finite Automata
What is finite ?  finite condition

## Automatic door controller
![auto door controller](https://imgur.com/TUMbOW2.png)

|       | Neither | Front | Rear  | Both
--------|---------|-------|-------|-----
Closed  | Closed  | Open  | Closed| Closed
Open    | Closed  | Open  | Open  | Open

## A finite Automaton is a 5-tuple
+ __Q__ is a finite set called the states
+ __Σ__ is a finite set called the alphabet
+ __δ__ Q × Σ → Q is the transition function
    + Q: current state
    + Σ: input symbol
    + Q: next state
+ __q<sub>0</sub>__ ( q<sub>0</sub> ∈ Q ) is the start state
+ __F__ ( F ⊆ Q ) is the set of accept state

## For Example a Finite Machine M<sub>1</sub>
![M1](https://imgur.com/aEva9zQ.png)

**接受狀態以雙圓圈表示(q<sub>2</sub>)**<br>
__M<sub>1</sub> accepts :__
+ Any string that ends with a 1
+ Any string that ends with an even number of 0s
following the last 1

001 (accepted)<br/>
0010 (doesn't accept)<br/>
00100 (accepted)
+ M<sub>1</sub> = ( Q, Σ, δ, q, F )
+ Q = { q<sub>1</sub>, q<sub>2</sub>, q<sub>3</sub> }
+ Σ = { 0 , 1}
+ F = { q<sub>2</sub> }
+ δ =
    |       |   0    |   1
    --------|--------|--------
    **q1**  | **q1** | **q2**
    **q2**  | **q3** | **q2**
    **q3**  | **q2** | **q2**

## Definition of a language of machine
+ A string is accepted by a finite automaton
M if M stops at the accept state after
reading the string.
+ If A is the set of all strings that machine M accepts, we say that A is **the language of machine M and write L(M)=A.** We say that **M recognizes A** or that **M accepts A**.

## Formal Definition of Computation
+ Let M = ( Q, Σ, δ, q<sub>0</sub>, F) be a finite automata.
+ Let w = w<sub>0</sub>, w<sub>1</sub>, w<sub>2</sub> be a string where each w<sub>i</sub> is a member of the alphabet

**M accepts w if a sequence of states r<sub>0</sub>, r<sub>1</sub>,...r<sub>n</sub> in Q exists with 3 conditions:**

+ r<sub>0</sub> = q<sub>0</sub>
+ δ( r<sub>i</sub>, w<sub>i+1</sub> ) = r<sub>i+1</sub>
+ r<sub>n</sub> ∈ F

**M recognizes language A if A={ w | M accepts w }**

---
## Definition of regular language
If a language is called a **regular language** if some finite automaton recognizes it.<br>
__能被有限自動機辨識的語言稱為正規語言__<br>
The Definition of **language**: 來自於某個字母集所成的字串的集合<br>
**i.e. L ⊂ Σ\***

---

## Examples of designing finite automata
如何知道一個語言是否為 regular language？可以試著設計一台有限自動機( finite automata )，如果設計的出來，那這個語言就是 regular language (proof by construction)
##### Design L(E)={ w | w contains the string 001 as a substing }
4 possibilities:
1. haven't just seen any symbols of the pattern
2. have just seen a 0
3. have just seen 00
4. have seen the entire pattern 001

![](https://imgur.com/4DQwLaJ.png)

**每個狀態都要定義 n 個 outgoing edge, n: 有幾種輸入**

## The Regular Operations
Let A and B be languages. We define the regular operations union, concatenation, and star as follows:
+ Union
    + A∪B = { x | x ∈ or x ∈ B }
+ Concatenation
    + A。B = { xy | x ∈ A and y ∈ B }
+ Star:
    + A\* = { x<sub>1</sub>x<sub>2</sub>x<sub>3</sub> | k ≥ 0 and each x<sub>i</sub> ∈ A }
    + ε 代表空字串(empty string) ε ∈ A\*

A collection of objects is **closed(封閉性) under some operation** if applying that operation to members of the collection returns an object still in the collection.

##### Theorem: The class of regular languages is closed under the `UNION` operation
proof: (proof by construction)

Assume that A<sub>1</sub> and A<sub>2</sub> are regular languages from the same alphabet.

Let M<sub>1</sub> recognized A<sub>1</sub>, where M<sub>1</sub> = ( Q<sub>1</sub>, Σ, δ<sub>1</sub>, q<sub>1</sub>, F<sub>1</sub>) and<br>&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
M<sub>2</sub> recognized A<sub>2</sub>, where M<sub>2</sub> = ( Q<sub>2</sub>, Σ, δ<sub>2</sub>, q<sub>2</sub>, F<sub>2</sub>)

Construct M to recognize **A<sub>1</sub> ∪ A<sub>2</sub>**, where M = ( Q, Σ, δ, q<sub>0</sub>, F)

1. Q = { (r<sub>1</sub>,r<sub>2</sub>) | r<sub>1</sub> ∈ Q<sub>1</sub> and r<sub>2</sub> ∈ Q<sub>2</sub>}
2. Σ = Σ<sub>1</sub> ∪ Σ<sub>2</sub>
3. For each ( r<sub>1</sub>, r<sub>2</sub> ) ∈ Q and each a ∈ Σ , Let δ(( r<sub>1</sub>, r<sub>2</sub> ) , a ) = (δ<sub>1</sub>( r<sub>1</sub>, a ) , δ<sub>2</sub>( r<sub>2</sub>, a ))
4. q<sub>0</sub> = ( q<sub>1</sub> , q<sub>2</sub> )
5. F = { ( r<sub>1</sub> , r<sub>2</sub> ) | r<sub>1</sub> ∈ F<sub>1</sub> or r<sub>2</sub> ∈ F<sub>2</sub> }<br>&nbsp;&nbsp;
= ( F<sub>1</sub> × Q<sub>2</sub> ) ∪ ( Q<sub>1</sub> × F<sub>2</sub> )

##### Theorem: The class of regular languages is closed under the `CONCATENATION` operation
**\* 比較難證明，為解決這類問題我們需要一種新技巧稱為「非確定性」(nondeterminism)**
