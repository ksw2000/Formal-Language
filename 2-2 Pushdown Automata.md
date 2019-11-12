# 2-2 Pushdown Automata
+ A new type of computational model. ( pushdown automata 比 finite automata 多了一個記憶體 (stack) 的裝置 )
+ Pushdown automata are equivalent in power to context-free grammars.( Pushdown automata 的計算能力跟 context-free grammar 相同，也就是比第一章教的 finite automata 強 )
+ To prove a language is context-free, we can give either a __context-free grammar__ generating it or a __pushdown automaton__ recognizeing it.

![Compare pushdown automata and finite automata](https://imgur.com/fXXkvDY.png)

+ A pushdown automaton is a finite automaton with an extra component called stack of unlimited size.
+ Pushdown automata may be deterministic or nondeterministic, but __deterministic__ and __nondeterministic__ pushdown automata __are not equivalent in power__.
+ We focus on nondeterministic pushdown automata because these automata are equvalent in power to context-free grammars.

### Formal Definition of Pushdown automaton
A pushdown automaton is a __6-tuple ( Q, Σ, Γ, δ, q<sub>0</sub>, F)__
+ __Q__ iS the set of states
+ __Σ__ is the set of input alphabet
+ __Γ__ is the stack alphabet
+ __δ__ is transition function
+ __q<sub>0</sub>__ (q<sub>0</sub> ∈ Q) is the start state
+ __F__ (F ⊆ Q) is the set of accept state

---
### Use PDA to recognize { 0<sup>n</sup>1<sup>n</sup> | n ≥ 0 }
The following is formal description of the PDA ( pushdown automaton ) that recognizes the language
{ 0<sup>n</sup>1<sup>n</sup> | n ≥ 0 }


即 { ε, 01, 0011, 000111, ... }

![](https://imgur.com/yMUBEjp.png)
↑ $ 用來作為標記，提供堆疊pop()時判斷pop()到最底下

__a,b → c 讀入 a pop(b) push(c)__

__如果 b 是 ε 代表不做 pop()，如果 c 是 ε 則代表不做 push()__

---
### Another Example. Use PDA to recognize { ww<sup>R</sup> | w ∈ (0,1)* }
{ ww<sup>R</sup> | w ∈ (0,1)* } where w<sup>R</sup> means w written backwards

![](https://imgur.com/rgZi2zJ.png)

---
### If a language is context-free, then some PDA recognizes it
(太複雜證明不會考)

proof ( 待補 )

---
## Review
DFA,NFA 具有相同計算能力能 __辨識__ regular language ( regexp 能表示 )

pumping lemma 告訴我們，這三種模型有侷限。有些語言不是 regular language 沒有辨法用這三種模型表示。

Context-free grammar：可以用 context-free grammar __產生__ 的語言稱為 context-free grammar

PDA (Pushdown automata)：計算能力又比 DFA,NFA 強，可以用來 __辨識__ 一個語言是不是 Context-free language

__Regular language ⊂ Context-free language__
