---
layout: page
title: Lean Prover Zulip Chat Archive 
permalink: archive/113488general/00468OferGabberonformalproof.html
---

## [general](index.html)
### [Ofer Gabber on formal proof](00468OferGabberonformalproof.html)

#### [Kevin Buzzard (Jan 17 2019 at 18:30)](https://leanprover.zulipchat.com/#narrow/stream/113488-general/topic/Ofer%20Gabber%20on%20formal%20proof/near/155353065):
Ofer Gabber is an extremely precise pure mathematician, and has even been known to refuse to put his name on a paper containing joint work with others because he didn't 100% check all of the work of all of the other people. 

He turned 60 recently and as part of the celebrations he was interviewed by Luc Illusie. Illusie asks Gabber about formal proof verification systems here:

https://youtu.be/OokyTw9mYYc?t=4159

Gabber is talking in particular about checking that certain signs are +1. His comments are interesting, but I think that they are also naive to a certain extent. I'd be interested to hear the views of others.

****

Here's the background. There is a running joke in algebraic geometry about commutative diagrams. In technical algebraic geometry of the kind being done in the 70s it was not uncommon to run into squares of maps (I mean four abelian groups A,B,C,D coming from algebraic geometry and group homomorphisms A -> B, B -> D, A -> C, C -> D) for which the resulting diagram would "surely commute" (i.e. the composite maps A -> B -> D and A - >C -> D were "surely equal") because a mathematician has a good nose for this sort of thing -- if all the maps are "natural" and "canonical" and other words for which I can offer no formal definition (but which I feel I intuitively understand at some level), then obviously both maps A -> D were equal because they were both "the natural map". This sort of argument falls somewhat short of a proof, however mathematicians might be convinced about it anyway, especially if writing down the details of a proof was going to be manifestly painful. If only 100 people in the world understand what you're doing, and if they all can see the pain involved checking something which is "bound to be true", they might well understand why you don't check it.

However the obvious counterexample to this is that perhaps the two maps A -> D differ by a sign. This can happen -- anyone who has worked through the details of collapsing double complexes to single complexes knows that signs can be subtle; I think they come up in K-theory too, although I know no K-theory. There is a story that Hartshorne's "Residues and duality" was so full of these issues that he gave up in the end, and the book got published anyway. However if you do care about these issues, then one natural approach was to approach Gabber and see if you can persuade him to check that your diagrams really do commute. In fact this is the issue which starts the conversation on this topic, with Illusie's question here

https://youtu.be/OokyTw9mYYc?t=3921

referring explicitly to these diagrams commuting. 

The reason I think Gabber is wrong is that to verify that you typed the question into a computer correctly, you only need to check that your *definitions* are the right ones, and if you are proving complicated theorems about relatively simple objects (e.g. duality theorems about schemes) and you already proved 100 lemmas about these objects, then your definition is extremely likely to be correct by this point.

#### [Mario Carneiro (Jan 17 2019 at 20:20)](https://leanprover.zulipchat.com/#narrow/stream/113488-general/topic/Ofer%20Gabber%20on%20formal%20proof/near/155361336):
I think he is largely correct, but he overstates the difficulty of overcoming the problem. There *is* a danger of infinite regress, just as there is a danger of infinite regress in justifying axioms by recourse to intuitions that are formalized as more axioms, which themselves need justification... The whole point of axiomatic reasoning is to say "okay, this is the bottom, we are making no attempt to justify these statements mathematically so you should read these and convince yourself that they are correct / coherent with respect to your intuitions".

The same thing happens in verified computation. You have programs that check proofs, and you have to trust that they are correct and don't smuggle in any false statements or "cheat" in the verification. You can verify these programs are correct, but then the methods by which you do this check are themselves open to criticism of the same kind. The way to break the loop is to have an equivalent of axioms, a program where you say "okay, this is the bottom, the 'trusted kernel' - we make no attempt to justify this is correct so you need to read it and believe it works in order to trust the results of everything after". So the correctness claim involves both the definitions involved as well as the programs doing the checking. The important part is that it does not involve the proof itself - this is where computers can lift the burden off the human to read through the whole argument and check every bit; instead the human has to read the meta-proof, the proof checker, and believe that it actually checks proofs.

#### [Thales (Jan 17 2019 at 23:43)](https://leanprover.zulipchat.com/#narrow/stream/113488-general/topic/Ofer%20Gabber%20on%20formal%20proof/near/156326053):
Both Illusie and Gabber were at my talk on formal proofs at the Loeser conference a few weeks before this interview was published.  Illusie's question to Gabber was essentially the same question he asked me at the end of my talk.  Illusie wants a machine-verified way to check signs in commutative diagrams.  It is not uncommon for results only to hold up to a  unknown sign, and these signs can be hard to get right, and different papers have incompatible sign conventions.

Gabber had questions and comments after my talk, and we also talked after my Bourbaki seminar on formal proofs a few years ago.    I'm not sure why he would have a issue with a trusted kernel with proof correctness verified by the type system.

