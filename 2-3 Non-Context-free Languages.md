# 2-3 Non-Context-free Language
(本章類似 1-4 Noneregular Language)
### Pumping Lemma for Context-free Language
上下文無關語言要滿足 pumping lemma for context-free language (必要條件), 所以如果有語言不符合 pumping lemma for context-free language，這個語言就不是上下文無關語言。但 __不能因為滿足 pumping lemma for context-free language 就一定是 context-free language__

If A is context-free language, than there is a number p (the pumping length ) where, if s is any string in A of length at least p, then s may be divided into five pieces s = uvxyz satisfying the conditions. 比 pumping lemma for regular language 複雜更多。

* ∀ i ≥ 0, u v<sup>i</sup> x y<sup>i</sup> z ∈ A
* | vy | > 0 ( vy 不是空字串 )
* | vxy | ≤ p

### Proof of "pumping Lemma for CFL"
...待補...

### Show that B={a<sup>n</sup>b<sup>n</sup>c<sup>n</sup> | n≥0} is not CFL.
We assume that B is a CFL and obtain a contradiction. Let p be the pumping length for B that is guaranteed to exist the pumping lemma. Select the string s = a<sup>n</sup>b<sup>n</sup>c<sup>n</sup>. Clearly s is a member of B and of length at least p. The pumping lemma states that s can be pumped, but we show that it cannot. i.e. we show that no matter how we divided s nto uvxyz, one of the three conditions of the lemma is vioated.

First, condition 2 stipulates(規定) that either v or y is nonempty. Then we consider one of two cases, depending on whether substrings v and y contain more than one type of alphabet symbol.

1. When both v and y __contain only one type of alphabet symbol__, v does not contain both a's and b's or both b's and c's, and the same holds for y. In this case the string uv<sup>2</sup>xy<sup>2</sup>z cannot contain equal numbers of a's, b's, and c's. Therefore it can't be member of B. That violates conditoin 1 of lemma and is thus a contradiction.

2. When either v or y __contain more than one type of symbol__ uv<sup>2</sup>xy<sup>2</sup>z may contain equl numbers of the three alphabet symbols but not in the correct order. Hence it can't be a member of B and a contradiction occurs.

A language is called Turing-recognizable if some Turing machine recogizes it.

### Prove that A={0<sup>n</sup>1<sup>n</sup>0<sup>n</sup>1<sup>n</sup> | n≥0 } is not context-free.
Assume that A is context-free

s = 0<sup>p</sup>1<sup>p</sup>0<sup>p</sup>1<sup>p</sup> pumping length 4p > p <br>
s = uvxyz

case1: 假設 u,y 包含 1 個符號，則 uv<sup>2</sup>xy<sup>2</sup>z is not in A (矛盾)

case2: 假設 u,y 包含有 2 個不同符號，則 uv<sup>2</sup>xy<sup>2</sup>z is not in A (因為0,1會交錯出現) (矛盾)
