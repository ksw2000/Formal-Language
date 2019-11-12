# 1-3 Regular Expressions
Assume that R is a regular expression
+ R<sup>+</sup> = RR* ( 至少出現一次 R，且 R 可重複 )
+ R<sup>+</sup> ∪ ε = R* ( 可以不出現 R，且 R 可重複 )
+ R<sup>k</sup> = R...RR ( R 重複 k 次)
+ L(R) = the language of R

precedence order of regular operators: __star > concatenation > union__

##### Example
1. 0\*10\* { w | w contains a single 1} 1, 01, 010, 00100,...
2. Σ\*001Σ\* { w | w contains 001 as a substring} 001, 0010, 000110,...
3. 1\*(01<sup>+</sup>)* = { w | every 0 in w is followed by at least one 1 } 01, 101, 11010101,...
4. (0 ∪ ε)1\* = 01\* ∪ 1\*
5. 1\*φ = φ (Concatenating the empty set to any set yields the empty set)
6. φ\* = { ε }

### Lemma : If a language is described by a regular expression, then it is regular.
proof idea :<br>
Assume that a regular expression R describing some language A, We show how to convert R into an NFA recogizing A.

### If a language is regular, then it is described by a regular expression.
![a regular language can be described by regexp](https://imgur.com/mwnRUol.png)
↑轉換示意圖
* First we show how to convert DFA into ``generalized nondeterministic finite automaton (GNFA)``, and then GNFA into regular expression.

* __A GNFA is an NFA except the transition arrows may have any regular expressions as labels__. ( GNFA 是 NFA 的一種，他允許我們在箭頭中使用正規表示式 )


### Convert Regular Expression to an NFA (考試重點)

![An example for converting rexp to NFA](https://imgur.com/VXe0ma8.png)

### Convert a DFA into a Regular Expression
由前面證明可知，可以用正規表示式去表示 DFA.<BR>
轉換流程：<BR>
* 3-state DFA
* 5-state GNFA (因為增加 start state && accept state)
* 4-state GNFA (把其中一個轉成 regexp)
* 3-state GNFA (再把其中一個轉成 regexp)
* 2-state GNFA
* Regular expression

↓Example for converting 2-state DFA to regular expression
![convert a DFA into regexp](https://imgur.com/gruJ3hs.png)

↓Another example
![convert a DFA into regexp (2)](https://imgur.com/D3PxKve.png)
