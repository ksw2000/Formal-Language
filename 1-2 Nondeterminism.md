# 1-2 Nondeterminism
+ Determinism machine: When a machine is in a given state and reads the next input symbol, only one next state exists ── it is uniquely determined.( 決定狀態機器在一個狀態中讀入下一個符號後只會再進入下一個唯一的狀態 )

+ Nondeterministic machine: When a machine is in a given state and reads the next input symbol, several choices may exist for the next state.( 非確定狀態機器再輸入一個符號時可以有不同種下一個狀態可以選擇 )

Every deterministic finite automaton(DFA) is a nondeterministic finite automaton(NFA). ( 可以視DFA是NFA的特例 )

## Example: NFA N<sub>1</sub>
![NFA example](https://imgur.com/1r3UAqR.png)

q<sub>2</sub> 的情況下可以不讀入任何符號就可以跳到 q<sub>3</sub>

![Compare DFA and NFA](https://imgur.com/ttd32FY.png)

如果輸入的字串進入 reject，表示這個字串不是我這機器所要的字串<br>
NFA 的樣子有點類似於平行處理

+ Nondeterminism may be viewed as **a kind
of parallel computation** wherein multiple independent **“processes”** or **“threads”** can be running concurrently. ( 非確定狀態有限自動機可以視為平行處理，可以同時處理多個獨立的程序或線程 )

+ If any one of these “threads” is **in an accept** state at the end of the input, the NFA **accepts the input string**. ( 只要有任意一條線程進入接受狀態即代表這個字串能被 NFA 接受)

## How useful are NFAs
+ Every NFA can be converted into an equivalent DFA.( 表示說 NFA 和 DFA 擁有相同的計算能力 )

+ Constructing NFAs is sometimes easier than directly constructing DFAs. ( 比較容易用此證明 concatenation 的封閉性 )

+ An NFA may be much smaller than its deterministic counterpart, or its functioning may be easier to understand.

## Example: NFA N<sub>2</sub>
A = { x | x is a string over { 0, 1 } containing a 1 in the third position from the end. } The following NFA N<sub>2</sub> recognizes A.

![Example of N2](https://imgur.com/unF2eS0.png)

如果倒數第三個位置有 1 ，那麼一定會有一條路徑可以抵達 q<sub>4</sub><br>
110<br>
q<sub>1</sub> → q<sub>2</sub> → q<sub>3</sub> → q<sub>4</sub>

011<br>
q<sub>1</sub> → q<sub>1</sub> → q<sub>1</sub> → q<sub>1</sub> → reject<br>
q<sub>1</sub> → q<sub>1</sub> → q<sub>2</sub> → q<sub>3</sub> → reject<br>
...

如果改用 DFA 設計將會相當複雜

![DFA for N2](https://imgur.com/EbiXDPE.png)

## Formal Definition of NFA
A nonedeterministic finite automaton is a 5-tuple ( Q, Σ, δ, q<sub>0</sub>, F ) where
+ Q is a finite set called the states
+ Σ is a finite set called the alphabet
+ δ Q × Σ<sub>ε</sub> → P(Q) ( power set of Q ) is the transition function **(與 DFA 主要差別)**
    + power set of Q : Q 所有子集合的集合
+ q<sub>0</sub> ∈ Q is the start state
+ F ⊆ Q is the set of accept state

Recall N<sub>1</sub>

![NFA example](https://imgur.com/1r3UAqR.png)

||0|1|ε
-|-|-|-
q<sub>1</sub>|{ q<sub>1</sub> }|{ q<sub>1</sub>,q<sub>2</sub> }|∅
q<sub>2</sub>|{ q<sub>3</sub> }|∅|{ q<sub>3</sub> }
q<sub>3</sub>|∅|{ q<sub>4</sub> }|∅
q<sub>4</sub>|{ q<sub>4</sub> }|{ q<sub>4</sub> }|∅

+ ε : Empty string
+ ∅ : Undefined

## Equivalence of NFAs and DFAs
+ Two machines are equivalent if they recognize the same language.

+ Deterministic and nondeterministic finite automata recognize the same class of languages.

#### Theorem : Every NFA has an equivalent DFA
Proof: Let N = { Q, Σ, δ, q<sub>0</sub>, F } be the NFA recognizing some language A. <br>We construct a DFA M= { Q', Σ, δ', q<sub>0</sub>', F' }

###### First, we consider the easier case wherein N has no ε arrows.
1. Q' = P(Q)

2. For R ∈ Q' and a ∈ Σ let δ'( R, a ) = ∪<sub>(r ∈ R)</sub>δ( R, a )

3. q<sub>0</sub>'={ q<sub>0</sub> }

4. F = { R ∈ Q' | R contains an accept state of N }

###### Now we need to consider the ε arrows

+ For R ⊆ Q, let E(R) = { q ∈ Q | q can be reached from R by traveling along 0 or more ε arrows}
+ δ'(R,a) = {q ∈ Q | q ∈ E(δ(r,a)) for some r ∈ R}
+ let q<sub>0</sub>' = E({q<sub>0</sub>})

At every step in the computation of M on an input, it clearly enters a state that corresponds to the subset of states that N could be in at that point.


#### Corollary : A language is regular if and only if some NFA recognizes it.
P: A language is regular

Q: some NFA recognizes it

proof:<br>
P → Q<br>
This is true because a regular language has a DFA recognizing it and any DFA is also an NFA

P ← Q<br>
If an NFA recognizes some language, so
does some DFA, and hence the language is
regular

##### Theorem: The class of regular languages is closed under the `UNION` operation
proof: (proof by construction, and use NFAs in model)

Let N<sub>1</sub> = ( Q<sub>1</sub>, Σ, δ<sub>1</sub>, q<sub>1</sub>, F<sub>1</sub> ) recognizes A<sub>1</sub>, N<sub>2</sub>=( Q<sub>2</sub>, Σ, δ<sub>2</sub>, q<sub>2</sub>, F<sub>2</sub> ) recognizes A<sub>2</sub>

Construct N = ( Q, Σ, δ, q<sub>0</sub>, F ) to recognize A<sub>1</sub> ∪ A<sub>2</sub>.
1. Q = {q<sub>0</sub>} ∪ Q<sub>1</sub> ∪ Q<sub>2</sub>
2. q<sub>0</sub> = start state
3. F = F<sub>1</sub> ∪ F<sub>2</sub>
4. For any q ∈ Q and any a ∈ Σ<sub>ε</sub>
+ δ(q,a) =
    + δ<sub>1</sub>(q,a) ... q ∈ Q<sub>1</sub>
    + δ<sub>2</sub>(q,a) ... q ∈ Q<sub>2</sub>
    + {q<sub>1</sub>, q<sub>2</sub>} ... q=q<sub>0</sub> and a = ε
    + φ ... q=q<sub>0</sub> and a ≠ ε

![UNION 示意圖](https://imgur.com/irL0hKP.png)

##### Theorem: The class of regular languages is closed under the `CONCATENATION` operation
proof: (proof by construction, and use NFAs in model)

Let N<sub>1</sub> = ( Q<sub>1</sub>, Σ, δ<sub>1</sub>, q<sub>1</sub>, F<sub>1</sub> ) recognizes A<sub>1</sub>, N<sub>2</sub>=( Q<sub>2</sub>, Σ, δ<sub>2</sub>, q<sub>2</sub>, F<sub>2</sub> ) recognizes A<sub>2</sub>

Construct N = ( Q, Σ, δ, q<sub>1</sub>, F<sub>2</sub> ) to recognize A<sub>1</sub>。A<sub>2</sub>.
1. Q = Q<sub>1</sub> ∪ Q<sub>2</sub>
2. q<sub>1</sub> = start state
3. F<sub>2</sub> = set of accept states
4. For any q ∈ Q and any a ∈ Σ<sub>ε</sub>
+ δ(q,a) =
    + δ<sub>1</sub>(q,a) ... q ∈ Q<sub>1</sub> and q ∉ F<sub>1</sub>
    + δ<sub>1</sub>(q,a) ... q ∈ F<sub>1</sub> and a ≠ ε
    + δ<sub>1</sub>(q,a) ∪ {q<sub>2</sub>} ... q ∈ F<sub>1</sub> and a = ε
    + δ<sub>2</sub>(q,a) ... q ∈ Q<sub>2</sub>

![CONCATENATION 示意圖](https://imgur.com/BkEJb0M.png)

##### Theorem: The class of regular languages is closed under the `STAR` operation

Let N<sub>1</sub> = ( Q, )
Let N<sub>1</sub> = ( Q<sub>1</sub>, Σ , δ<sub>1</sub>, q<sub>1</sub>, F<sub>1</sub> ) recognizes A<sub>1</sub>

Construct N = ( Q, Σ, δ, q<sub>0</sub>, F ) to recognize A<sub>1</sub>*
1. Q = {q<sub>0</sub>} ∪ Q<sub>1</sub>
2. q<sub>0</sub> = start state
3. F = {q<sub>0</sub>} ∪ F<sub>1</sub>
4. For any q ∈ Q and any a ∈ Σ<sub>ε</sub>
+ δ(q,a) =
    + δ<sub>1</sub>(q,a) ... q ∈ Q<sub>1</sub> and q ∉ F<sub>1</sub>
    + δ<sub>1</sub>(q,a) ... q ∈ F<sub>1</sub> and a ≠ ε
    + δ<sub>1</sub>(q,a) ∪ {q<sub>1</sub>} ... q ∈ F<sub>1</sub> and a = ε
    + {q<sub>1</sub>} ... q = q<sub>0</sub> and a = ε
    + φ ... q = q<sub>0</sub> and a ≠ ε

![STAR 示意圖](https://imgur.com/sy8jOTY.png)
