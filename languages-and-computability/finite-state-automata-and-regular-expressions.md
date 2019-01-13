<!-- TITLE: Finite State Automata And Regular Expressions -->
<!-- SUBTITLE: A quick summary of Finite State Automata And Regular Expressions -->

# Slides
* [CS 3518 Lec 1 1 FSA](/uploads/langandcomp/cs-3518-lec-1-1-fsa.pdf "Cs 3518 Lec 1 1 Fsa")
* [CS 2013 Formal Languages](/uploads/langandcomp/cs-2013-lec-1-2-formal-languages.pdf "Cs 2013 Lec 1 2 Formal Languages")
* [CS 2013 Lec 2 1 Finite Automata](/uploads/langandcomp/cs-2013-lec-2-1-finite-automata.pdf "Cs 2013 Lec 2 1 Finite Automata")
* [CS 2013 Lec 3 1 Regular Expressions 1](/uploads/langandcomp/cs-2013-lec-3-1-regular-expressions-1.pdf "Cs 2013 Lec 3 1 Regular Expressions 1")
* [CS 2013 Lec 3 2 Fsa Re Equivalence](/uploads/langandcomp/cs-2013-lec-3-2-fsa-re-equivalence.pdf "Cs 2013 Lec 3 2 Fsa Re Equivalence")

# FSA
* finite state automaton is an abstract model of a simple machine.
* FSAs check if a string of characters adhere to syntax
* **Acceptance of String:** scans entire string, if we reach a final state from an initial state
* **Acceptance of Language:** if all **strings in a language are accepted** and all strings **not** in the language are **rejected.**

* with output
	* Moore
	* Mealy 
* without output
	* Deterministic FSA
	* Non DFSA
	* λ-NDFSA

### Formal Definition
A finite state automaton M is a tuple M = (Q, Σ, δ, q0, F) where
* Q is a finite set of states
* Σ is a finite set of symbols, our alphabet
* δ : Q × Σ → Q is the transition function
* q0 ∈ Q is the initial/start state
* F ⊆ Q is the set of accept states


