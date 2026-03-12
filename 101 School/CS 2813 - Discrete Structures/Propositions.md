
A proposition is a declarative sentence that is either **true** or **false**. 
aka. A statement that has exactly one truth value: **True** or **False**.
- 2 + 2 = 4       **True**
- 2 + 2 = 5       **False**

# Propositional Variable

In the real world, statements are often complex. We break them into simpler propositions, and use p, q, r... to represent each proposition as a **propositional variable** (**True/False**)

**q**: Students in CS2813 like Ziming.
**r**: Ziming prepared everything carefully

**q** $\oplus$ **r** : Students in CS2813 like Ziming or he prepared everything carefully **but not both.**
**q** $\rightarrow$ **r** : **If** students in CS2813 like Ziming, **then** he prepared everything carefully
**q** $\iff$ **r** : Students in CS2813 like Ziming, **if and only if** he prepared everything carefully

A basic step of logic is to replace a statement with another one that has the same truth values in all cases. This is also useful in order to reason about sentences. This is called **Propositional Equivalences.**

| **p** | **q** | **p $\wedge$ q** | **-(p $\wedge$ q)** |     |     |     |
| ----- | ----- | ---------------- | ------------------- | --- | --- | --- |
| T     | T     | T                | F                   | F   | F   | F   |
| T     | F     | F                | T                   | F   | T   | T   |
| F     | T     | F                | T                   | T   | F   | T   |
| F     | F     | F                | T                   | T   | T   | T   |

Logical implication: **p $\rightarrow$ q** is always true, then **p** => **q**
Logical Equivalence: **p $\rightarrow$ q** is always true, then **p $\equiv$ q**


**(p $\rightarrow$ q) $\wedge$ (q $\rightarrow$ p) $\equiv$ p $\iff$ q**
**p** implies **q**, **and** **q** implies **p**



# Normal Forms for Compound Propositions

- [[Literal]]
- [[Term]]
- [[Clause]]
- [[DNF]]
- [[CNF]]

# Why do we need CNF & DNF?

A logic gate is built from **transistors,** which behave like switches:
- **ON** (conduct) or **OFF** (block)

- Natural for switches
	- **NOT** flips a signal
	- **AND / OR** combine multiple conditions

- Easy, fast, and reliable to implement.
	- Simple gates are smaller, cheaper, and more stable in circuits. 

- Functionally complete
	- Using only **AND, OR, NOT** we can build **any** logic rule

# De Morgan's Law

- See -> [[De Morgan Law]]