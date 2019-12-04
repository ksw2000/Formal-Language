# 3-1 Turing Machines
+ Turing machine model is proposed by Alan Turing in 1936.
+ A Turing machine can do everything that a real computer can do.

1. A Turing machinne can both write on the tape and read from it. (可寫可讀)
2. The read-write head can move both to the left and to the right. (讀寫頭可左移右移)
3. The tape is infinite
4. The special states for rejecting and accepting take effect immediately.

### Definition of Turing Machine
A Turing machine is a 7-tuple (Q, Σ, Γ, δ, q<sub>0</sub>, q<sub>accept</sub>, q<sub>reject</sub>)
+ __Q__ is the set of states (非空有限狀態的集合)
+ __Σ__ is the input alphabet not containing the blank symbole 口 (非空有限輸入字母的集合且「不包含空字符」)
+ __Γ__ is the tape alphabet, where 口 ∈ Γ and Σ ⊆ Γ (有限帶字母的集合，且包含Σ )
+ __δ__ Q x Γ -> Q x Γ x { L, R } is the transition function (L: 左移, R: 右移)
+ __q<sub>0</sub>__ ∈ Q is start state
+ __q<sub>accept</sub>__ ∈ Q is the accept state
+ __q<sub>reject</sub>__ ∈ Q is the reject state

### Definition: configuration C<sub>1</sub> yields configuration C<sub>2</sub> if the Turing machine can legally go from C<sub>1</sub> to C<sub>2</sub> in a single step.
Suppose that we hava a, b, and c in Γ, as well as u and v in Γ* and states q<sub>i</sub> and q<sub>j</sub>. In that case uaq<sub>i</sub>bv and uq<sub>j</sub>acv are two configurations. Say that

uaq<sub>i</sub>bv yiedls uq<sub>j</sub>acv

if in the transition function δ(q<sub>i</sub>, b)=(q<sub>j</sub>, c, L). That handles the case where the Turing machine moves leftward. For a rightWard move, say that

uaq<sub>i</sub>bv yields uacq<sub>j</sub>v

if  δ(q<sub>i</sub>, b)=(q<sub>j</sub>, c, R)

The start configuration of M on input w is the configuration q<sub>0</sub> w, which indicates that the machine is in the start state q<sub>0</sub> with its head at the leftmost position on the tape.

In an __accepting configuration__ the state of the configuration is q<sub>accept</sub>

In an __rejecting configuration__ the state of the configuration is q<sub>reject</sub>

Accepting and rejecting configurations are __halting configuration__ and don't yield further configuration.

Because the machine is defined to halt when in the states q<sub>accept</sub> and q<sub>reject</sub>. A Turing machine M accepts input w if a sequence of configuration C<sub>1</sub>, C<sub>2</sub>, ..., C<sub>k</sub> exists, where
1. C<sub>1</sub> is the start configuration of M on input w
2. each C<sub>i</sub> yield C<sub>i+1</sub>
3. C<sub>k</sub> is an accepting configuration

The collection of strings taht M accepts is the language of M, or the language  recognized by M. denoted L(M).

### Turing-recognizable
We call a __language__ __"Turing-recognizable"__(圖靈可識別語言) if some Turing machine recognizes it.

Turing-recognizable language is also called __recursively enumberable language__(遞歸可枚舉語言).

### Turing-decidable
A Turing machine on an input has three possible outcomes: __accpet__, __reject__, or __loop__.

A Turing machine on that halts on all inputs is called a __decider__ because it always make a decision to __accept__ or __reject__ an input. ( __decider 只包含接受或拒絕，如果是loop則不算__，可以說 decider 是 Turing-recognizable 的特例 )

A decider that recoginizes some language also is said to decide that language. We call a __language__ "__Turing-decidable language__"(圖靈可判定語言) or simply __decidable__ if some Turing machine decides it.

Turing-decidable language language is alse called __recursive language__(遞迴語言)

#### Regular language ⊆ Context-free language ⊆ Turing-decidable language ⊆ Turing-recognizable language

### Example
(...待補...)
