# sttfa_geocoq_euclid

Formalization of Euclid's Elements Book 1 in Dedukti.

This library contains a translation of a part of the 
[GeoCoq library](https://github.com/GeoCoq/GeoCoq).
It contains the formalization of the original proofs
of Euclid's Elements Book 1. This part of GeoCoq has 
been translated into Dedukti 
[here](https://github.com/Deducteam/GeoCoqInE-Euclid),
in an encoding of the Coq Theory. Hence, universes and
CiC functionalities were present, while they do not 
seem necessary. 

This library is based on of GeoCoqInE-Euclid. Its
code has been simplified and then transformed.
It uses the STTFA encoding (simple type theory
with prenex polymorphism and type operators), showing 
that these proofs could be expressed in a simpler theory
than the Calculus of Construction (not so surprising).

Having these proofs in this encoding permits to
translate them into other systems (Coq, HOL Light, 
Lean, Matita, OpenTheory and PVS).  
Besides, one could note that these proofs are in
predicate logic with two sorts (`Point` and `Circle`).
So, it should be possible to translate them into
systems with theories weaker than STTFA.


## Read the code

Big proof terms are not really readable, and it is not 
recommended to read the code to understand the proofs' 
formalization (it is better to consult GeoCoq, and maybe 
[this article](http://www.michaelbeeson.com/research/papers/ProofCheckingEuclid.pdf)).

However, some parts of the code are a good introduction
to Dedukti and to encoding. So,

- [`sttfa.dk`](./sttfa.dk) is the encoding file,
- [`logic.dk`](src/logic.dk) contains the logical connectives and their properties (inductive principles, etc.),
- [`euclidean__axioms`](src/euclidean__axioms.dk) contains the axiomatization of the geometry (some predicates and some axioms),
- [`euclidean__defs`](src/euclidean__defs.dk) contains some predicates that form definitions (`MidPoint`, `Triangle`, etc.).

Some other files could be interesting. For instance 
[`euclidean_tactics`](src/euclidean__defs.dk) defines 
helper functions that will facilitate the proofs. By the 
way, an axiom for classical logic is also added in this 
file. Therefore, the first elements of this file are the 
definition of the excluded middle (as an axiom), and the
proof of the double negation elimination principle.


## Translate the proofs

The proofs can be translated using
[Logipedia](https://github.com/Deducteam/Logipedia). 
Here are the size of the generated translations.

| Target system | Size of generated code |
|---------------|------------------------|
| Coq           | 16 Mib                 |
| HOL Light     | 98 Mib                 |
| Matita        | 10 Mib                 |
| Lean          | 22 Mib                 |
| Open Theory   | 854 Mib                |
| PVS           | 191 Mib                |

There is no comparison with the size to the size of the 
[proofs of GeoCoq](https://github.com/GeoCoq/GeoCoq/tree/master/Elements/OriginalProofs). 
Indeed, the code of the original proofs uses Coq tactics
while the translations only consists of proof terms, so
are bigger.
