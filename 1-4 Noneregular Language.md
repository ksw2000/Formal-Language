# 1-4 Nonregular Languages
### Pumping Lemma
正規語言要滿足 pumping lemma (必要條件), 所以如果有語言不符合 pumping lemma，這個語言就不是正規語言。但 __不能因為滿足 pumping lemma 就一定是 regular language__，要證明一個語言是 regular language 可以利用建構式證明法，比如設計一個 DFA, NFA, 或以regular expression表示。

If A is a regular language, then there is a number p (the pumping length) where, if s is any string in A of length at least p, then s may be divided into three pieces, s=xyz, satisfying the following conditions:
* ∀ i ≥ 0, x y<sup>i</sup> z ∈ A (y<sup>i</sup> 表示y重複 i 次)
* | y | > 0 ( y不是空字串 )
* | xy | ≤ p ( xy 長度不超過 p )

### Proof of pumping Lemma
(用鴿籠定理證)<br>
__Let__ M = ( Q, Σ, δ, q<sub>1</sub>, Q) be a DFA recognizing A and p be the number of states of M.

__Let__ s = s<sub>1</sub>s<sub>2</sub>...s<sub>n</sub> be a string in A and n≥p.

__Let__ r<sub>1</sub>,...r<sub>n+1</sub> be the sequence of states that M enters while processing s, so <br>r<sub>i+1</sub> = δ(r<sub>i</sub>, s<sub>i</sub>) for 1 ≤ i ≤ n <br>This sequence has length n+1 ( ≥p+1 ). Among the first p+1 elements in the sequence, two must be the same state, by the pigeonhole principle. We call the first of these r<sub>j</sub> and the second r<sub>k</sub>. We have k ≤ p+1.

__Let__ __x__=s<sub>1</sub>…s<sub>j-1</sub>, __y__=s<sub>j</sub>…s<sub>k-1</sub>,and __z__=s<sub>k</sub>…s<sub>n</sub> .

As __x__ takes M from r<sub>1</sub> to r<sub>j</sub>, __y__ takes M from r<sub>j</sub> to r<sub>j</sub>, and __z__ takes M from r<sub>j</sub> to r<sub>n+1</sub>, which is an accept state, M must accept xy<sup> i </sup>z for i ≥ 0.

We know that j ≠ k, so | y |>0 ,  and k ≤ p+1, so | xy | ≤ p.

# 這裡會考↓
### Use pumping lemma to proof that B={ 0<sup>n</sup>1<sup>n</sup> | n ≥ 0 } is not regular.
Assume __B__ is regular and __p__ is the pumping length given by the pumping lemma.

Let __s__ = 0<sup>p</sup>1<sup>p</sup>

Assume that __s__ = xyz ( ... 拆成 xyz 三部分)

根據 pumping lemma 的第三個條件( | xy | ≤ p )，__x,y 都必須由 0 組成__

000..000111...111 (0有 p 個, 1有 p 個)

Therefor, xyyz is not in B. ( 我們增加y時，只增加 0 的個數，此時0的個數與 1 的個數不相同 ) 不符合 pumping lemma 的第一個條件 ( 矛盾 )

B={ 0<sup>n</sup>1<sup>n</sup> | n ≥ 0 } 不符合 pumping lemma，所以 B 不是 regular language

### Use pumping lemma to proof that E={ 0<sup>i</sup>1<sup>j</sup> | i > j } is not regular.
Assumbe __E__ is regular and __p__ is the pumping length given by the pumping lemma.

Let __s__ = 0<sup>p+1</sup>1<sup>p</sup>.

Assume that __s__ = xyz ( ... 拆成 xyz 三部分)

根據 pumping lemma 的第三個條件( | xy | ≤ p )，__x,y 都必須由 0 組成__

Therefore, xz is not in E. ( 我們拿掉y時，因為 y 不能是空字串，因此我們拿掉至少 1 個 0，這時 x 中 0 的個數 ( 1~p-1個 ) 會小於等於 z 中 1 的個數 (p個)  ) 不符合 pumping lemma 的第一個條件 ( 矛盾 )
