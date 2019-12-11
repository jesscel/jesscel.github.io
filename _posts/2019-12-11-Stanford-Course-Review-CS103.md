For me, **CS103: Mathematical Foundations of Computing** is one of the class in which I had the most fun and also most pain taking it. Before taking this class, I did not have a lot experience writing mathematical proofs, and the only memories I had for writing proofs were painful and boring. However, this course made me realize how much fun it is to write proofs from all different angles and to explore the fundamental aspects of the world around us via proofs. 

Structurally, CS103 covers and addresses three major questions:

* Why are some problems harder to solve than others?
* What problems can we solve with a computer?
* How can we be certain in our answers to these questions?

The actual order the course address the problems is backward. Starting from the third problem, we were introduced to a bunch of new concepts in discrete math - e.g. sets, graphs, binary relations - logic - e.g. first-order logic, propositional logic - and proving methods - e.g. proof by contrapositive, contradiction, induction. All of these concepts are preparation for the most challenging part of the course where we address the first two problems listed above. I personally found the first two questions, which are addressed by Computability Theory and Complexity Theory, respectively - the most interesting and challenging topics of the course. So in this article, I tried to put together the important concepts and theorems for these two topics, which I focused on during my review for the final.

## Computability Theory

What *problems* can we *solve* with a *computer*?

To address this question above, we need to first define "problem" and "computer".  Later, we will also need to know what it means to "solve" a problem. In CS103, the Formal Language Theory is adopted to define "problem". As for "computer", we will focus on two big categories: finite automata and Turing machine. 

### Formal Lanuage Theory

Since every problem is a sequence of characters, or a string, the Formal Language Theory formulate problems as set of strings.

### Finite automata

*Finite automata are an abstraction of computers with finite amount of resources.*

**Finite automata**: a type of mathematical machine for determing whether a string is in a language.

**DFA (Deterministic Finite Automata)**: a type of finite automata in which for each state in it, there is exactly one transition for each symbol in its alphabet $\Sigma$.

<img src="/Users/jessicaaaaaa/Desktop/Screen Shot 2019-12-06 at 12.34.17 PM.png" alt="Screen Shot 2019-12-06 at 12.34.17 PM" style="zoom: 33%;" description="An example DFA for language that ends with \texttt{aa}"/>

**NFA (Nondeterministic Finite Automata)**: a type of finite automata in which for each state in it, there can be zero or multiple decisions that can be made at one point.

**Regular language**: a language *L* is regular if there is a DFA for *L*.

> Intuiiton: Regular languages correspond to problems that can be solved with finite memory.

<u>***Theorem***</u>: The following are equivalent:

* *L* is a regular language.
* There is a DFA for *L*.
* There is an NFA for *L*. 
* There is a regular expression for *L*.

**Language concatenation**: the concatenation of two languages is defined as
$$
L_1L_2 = \{wx\ |\ w\in L_1 and x \in L_2\}
$$
**Lanauge exponentiation**: the exponentiation of a language is defined by the following rules
$$
L^0 =\{\varepsilon\} \\
L^{n+1}=LL^n
$$
**Kleene closure**: the Kleene closure operation of a language is defined as
$$
L^* = \{w \in \Sigma^*\ | \exist n \in \mathbb{N}. w \in L^n\}
$$
Note that the empty string $\varepsilon$ is always in L* for any language L.

<u>***Closure properties of the regular languages***</u>: If $L_1$ and $L_2$ are regular languages over the alphabet $\Sigma$, then their *complement, union, intersection, concatenation, and Kleene star* are all regular languages.



**Regular expression**: a way to describe a regular language using a string representation. 

- Atomic regular expressions include the symbols $\emptyset$, $a \in \Sigma$, and $\varepsilon$.
- Compound regular expressions include $(R)$, $R^*$, $R_1R_2$, and $R_1 \unison R_2$ (in operator precedence order).

<u>***Theorem***</u>: If R is a regular expression, then L(R) is regular.

<u>***Theorem***</u>: If L is a regular language, then there is a regular expression for L.

<img src="/Users/jessicaaaaaa/Desktop/Screen Shot 2019-12-06 at 2.08.03 PM.png" style="zoom: 25%;" />

Starting with an NFA *N* for a regular language *L*, use the following **state elimination algorithm** to find the regular expression for *L*:

1. Add a new start state $q_s$ and an accept state $q_f$ for *N*; 
2. Add $\varepsilon$-transition from $q_s$ to the original start state of N;
3. Add $\varepsilon$-transition from every original accepting state of N to $q_f$ and mark them as not accepting;
4. Repeatedly remove states other than $q_s$ and $q_f$ from the NFA by “shortcutting” them until only two states remain: $q_s$ and $q_f$ .



**Distinguishability**: Two strings x ∈ Σ* and y ∈ Σ* are called *distinguishable relative to L* if there is a string w ∈ Σ* such that exactly one of xw and yw is in L. Formally,
$$
x \not\equiv_L y \ \text{ if }\ \exist w \in \Sigma^*. (xw \in L \leftrightarrow yw \not\in L)
$$
To prove a language is **nonregular**, we use distinguishability to do so. 
$$
\mathscr{L}(G) = \{w \in \Sigma^*\ | S \Rightarrow^* w\}
$$
A **distinguishing set** for *L* is a set *S*, where
$$
\forall x \in S. \forall y \in S. (x \not= y \rightarrow x \not\equiv_L y)
$$
<u>***Myhill-Nerode Theorem***</u>: If L is a language and S is a distinguishing set for L that contains infinitely many strings, then L is not regular.

**Context-free grammar**: 

* **Nonterminal symbols** are variables. 
* **Terminal symbols** are the alphabet of the CFG.
* A set of **production rules** tell how a nonterminal symbol can be replaced by a string of terminal  and nonterminal symbols.
* A **start symbol (*S*)**, which starts the derivation following the production, must be a *nonterminal*.

The language of a CFG *G* with alphabet Σ is defined as ℒ(G), which is the set of strings of terminals derivable from the start symbol. Formally,

<u>***Theorem***</u>: Every regular language is context-free.

### Turing machines

*Turing machines are an abstraction of computers with unbounded resources.*

A **Turing machine (TM)** contains three parts:

- A **finite-state control** that gives commands
- An **infinite tape** for input and scratch
- A **tape head** that reads and writes on the tape

The **tape alphabet** of a TM contains all characters that can be written on the TM tape, and it always contains the blank symbol.

Each transition of a TM is in the form:
$$
\text{read} \rightarrow \text{write}, \text{dir} 
$$
A TM has a *finite* number of states.

**TM subroutine**: A TM that instead of accepting or rejecting an input, do some kind of processing on it.

<u>***Church-Turing Thesis***</u>: every effective method of computation is either equivalent to or weaker than a Turing machine.

**The Hailstone Sequence**: 

The **Collatz Conjecture** says that the Hailstone Turing Machine will terminates.

For a TM *M*, one of the following can happen given an input string *w*: 

* *M* **accepts** a string *w* if it enters an accept state when run on *w*. 
* *M* **rejects** a string *w* if it enters a reject state when run on *w*. 
* *M* **loops on** a string *w* if when run on *w* it enters neither an accept nor a reject state.

*M* **halts on** the string *w* if it accepts or rejects it.

**Decider**: A TM that always halts on any input.

**Recognizer**: A TM that either halts or loop on an input.

**Verifier**: A TM that always halts given any input *w* and a potential certificate *c* for *w*, you can check whether the certificate is correct.



### R and RE

**R**: the set of all decidable languages; the class of languages that have deciders. Formally, 
$$
\textbf{R}=\{L\ |\ L\text{ is decidable}\}
$$

> Intuition: "Run the program on every possible input. If you see it crash, return true. If it never crashes, you will never learn this."

**RE**: the set of all recognizable languages; the class of languages that have verifiers. Formally,
$$
\textbf{RE}=\{L\ |\ L \text{ is recognizable}\}
$$

> Intuition: "Look at the source code and somehow determine, with 100% certainty, whether the program will ever crash." 



<u>***Theorem***</u>:  There is a Turing machine U_TM called the **universal Turing machine** that, when run on an input of the formc⟨M, w⟩, where M is a Turing machine and w is a string, simulates M running on w and does whatever M does on w (accepts, rejects, or loops). In other words, M does to w what U_TM does to ⟨M, w⟩.

The **acceptance language for Turing machines**, denoted as A_TM, is the language of the universal Turing machine U_TM. Formally,
$$
A_{TM} = \mathscr{L}(U_{TM}) = \{\langle M, w \rangle\ | \ M \text{ is a TM and }M \text{ accepts } w\}
$$

$$
\langle M, w \rangle \in A_{TM} \ \leftrightarrow\ M \text{ accepts } w
$$

Another important fact is that, 
$$
A_{TM} \in \mathbf{RE} \text{ and }  A_{TM} \not\in \mathbf{R}
$$
This fact implies that **RE** and **R** are not the same.



## Complexity Theory (briefly touched on)

What problems can we solve with *efficiently* with a computer?

### P and NP

**P**: the class of problems that can solved efficiently by a computer. Formally, 
$$
\textbf{P}=\{L\ |\ \text{There is a polynomial-time decider for } L \}
$$
**NP**: the class of problems whose "yes" answers can be verified efficiently by a computer. Formally,
$$
\textbf{NP}=\{L\ |\ \text{There is a polynomial-time verifier for } L \}
$$

<u>***Theorem***</u>: If any **NP**-complete language is in **P**, then **P** = **NP**.

> Intuition:  This means the hardest problems in NP aren’t actually that hard. We can solve them in polynomial time. So that means we can solve all problems in NP in polynomial time.



**Reducibilty**: 

A language is **NP-hard** if
$$
\forall A \in \mathbf{NP}. A \leq_p L.
$$
A language is **NP-complete** if L is in NP and L is NP-hard.

> Intuition: The NP-complete problems are the hardest problems in NP.

<img src="/Users/jessicaaaaaa/Desktop/Screen Shot 2019-12-07 at 12.46.52 PM.png" alt="Screen Shot 2019-12-07 at 12.46.52 PM" style="zoom: 33%;" />

**Satisfiability**: A propositional logic formula φ is called satisfiable if there is some assignment to its variables that makes it evaluate to true.

An assignment of true and false to the variables of φ that makes it evaluate to true is called a **satisfying assignment**.

**Boolean satisfiability problem (SAT)**: "Given a propositional logic formula φ, is φ satisfiable?" Formally, 
$$
SAT = \{\langle \varphi \rangle\ |\ \varphi \text{ is a satisfiable propositional logic formula}\}
$$
<u>***Cook-Levin Theorem***</u>: SAT is NP-complete.

Resolving P=?=NP is equivalent to figuring out how hard SAT is. Formally,
$$
SAT \in \mathbf{P} \leftrightarrow \mathbf{P}=\mathbf{NP}
$$
If A ≤ p B and B ∈ P, then A ∈ P. 

If A ≤ p B and B ∈ NP, then A ∈ NP

Any language that reduces to SAT must be in NP somewhere.

Any language that SAT can be reduced to must be NP-hard. 



## Summary

Since CS103 is essentially a course of writing proofs, I also made the following chart, which will help with the proving process. 

|           TO PROVE...           |                       ...IS TO SHOW...                       |
| :-----------------------------: | :----------------------------------------------------------: |
|     Language *L* is regular     |    There exists a DFA, NFA, or regular expression for *L*    |
|    Language *L* is decidable    |                There exists a decider for *L*                |
|  Language *L* is recognizable   |        There exists a recognizer or verifier for *L*         |
| Language *L* is co-recognizable |   There is a recognizer or verifier for strings not in *L*   |
|   Language *L* is nonregular    | Use Myhill-Nerode Teorem to show there is a distinguishing set for *L* |
