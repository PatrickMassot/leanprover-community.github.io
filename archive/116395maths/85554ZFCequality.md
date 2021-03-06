---
layout: page
title: Lean Prover Zulip Chat Archive 
permalink: archive/116395maths/85554ZFCequality.html
---

## [maths](index.html)
### [ZFC equality](85554ZFCequality.html)

#### [Kevin Buzzard (May 28 2018 at 11:31)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127197270):
There were a couple of times in the schemes project when I really had to think "beyond ZFC" -- I had to write down a map, and there were two ways of doing it, and in ZFC they were the *literally the same way* but in Lean they were different. In this example I just chose a random Lean route to model my ZFC thoughts and it got me in to real trouble later.

#### [Kevin Buzzard (May 28 2018 at 11:32)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127197324):
Here's a naive definition of the image of a morphism in ZFC, translated seamlessly into Lean:

#### [Kevin Buzzard (May 28 2018 at 11:32)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127197326):
```lean
import data.set

-- ZFC-safe! The below code uses only Prop and Type

variables {X Y : Type} (f : X → Y) (U : set X) 

definition image := {y : Y | ∃ x ∈ U, f x = y}
```

#### [Kevin Buzzard (May 28 2018 at 11:33)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127197328):
And now here's something which doesn't work

#### [Kevin Buzzard (May 28 2018 at 11:33)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127197333):
`theorem they_are_not_defeq : image (@id X) U = U := rfl -- fails`

#### [Kevin Buzzard (May 28 2018 at 11:33)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127197336):
Does that mean that my definition of image is wrong?

#### [Kevin Buzzard (May 28 2018 at 11:33)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127197337):
Or is there literally no way to make that happen in dependent type theory

#### [Kenny Lau (May 28 2018 at 11:34)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127197379):
they are definitely not defeq

#### [Kenny Lau (May 28 2018 at 11:34)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127197384):
you see, a set is nothing more than a function to Prop

#### [Kevin Buzzard (May 28 2018 at 11:34)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127197385):
Is that because I am bad at writing the image function?

#### [Kevin Buzzard (May 28 2018 at 11:34)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127197386):
Can you write a better one for me

#### [Kenny Lau (May 28 2018 at 11:34)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127197387):
no, it isn't

#### [Kevin Buzzard (May 28 2018 at 11:34)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127197388):
where they are defeq

#### [Kenny Lau (May 28 2018 at 11:34)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127197391):
you can't

#### [Kenny Lau (May 28 2018 at 11:34)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127197392):
you have to have an existential quantifier

#### [Kevin Buzzard (May 28 2018 at 11:34)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127197393):
can you prove that you can't?

#### [Kevin Buzzard (May 28 2018 at 11:34)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127197395):
in Lean

#### [Kevin Buzzard (May 28 2018 at 11:35)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127197396):
3.4.1

#### [Mario Carneiro (May 28 2018 at 11:35)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127197403):
not in lean

#### [Mario Carneiro (May 28 2018 at 11:35)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127197405):
it's a metatheorem

#### [Kevin Buzzard (May 28 2018 at 11:35)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127197406):
Great.

#### [Kenny Lau (May 28 2018 at 11:35)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127197408):
@**Mario Carneiro** can it actually be proved?

#### [Mario Carneiro (May 28 2018 at 11:35)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127197410):
probably

#### [Kevin Buzzard (May 28 2018 at 11:35)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127197411):
Well you know what

#### [Kevin Buzzard (May 28 2018 at 11:35)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127197413):
I think defeq is rubbish

#### [Kevin Buzzard (May 28 2018 at 11:35)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127197414):
because those two sets are *equal*

#### [Kenny Lau (May 28 2018 at 11:36)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127197452):
f(x) = x^2 and f(x) = x^2+1-1 are *equal*

#### [Kevin Buzzard (May 28 2018 at 11:36)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127197453):
and mathematicians have been thinking of those sets as *equal* since they started formalizing mathematics

#### [Kenny Lau (May 28 2018 at 11:36)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127197454):
but not definitionally equal

#### [Kevin Buzzard (May 28 2018 at 11:36)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127197455):
so what has gone wrong?

#### [Mario Carneiro (May 28 2018 at 11:36)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127197468):
nothing is wrong

#### [Mario Carneiro (May 28 2018 at 11:36)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127197470):
defeq is not ZFC equality

#### [Kevin Buzzard (May 28 2018 at 11:36)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127197471):
Kenny -- the ZFC analogues of the two concepts `U` and `image id U` are *identical*

#### [Kevin Buzzard (May 28 2018 at 11:37)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127197475):
I mean equal in the purest form

#### [Kenny Lau (May 28 2018 at 11:37)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127197479):
are they?

#### [Kevin Buzzard (May 28 2018 at 11:37)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127197480):
they are indistinguishable with the tools of ZFC

#### [Mario Carneiro (May 28 2018 at 11:37)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127197481):
no, there is more to prove under one definition than the other in ZFC

#### [Kenny Lau (May 28 2018 at 11:37)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127197482):
the latter is `{ y in U | exists x, x = y }`

#### [Kevin Buzzard (May 28 2018 at 11:37)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127197483):
In ZFC they are the same object

#### [Mario Carneiro (May 28 2018 at 11:37)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127197484):
in lean they are the same object

#### [Kenny Lau (May 28 2018 at 11:37)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127197485):
sure, but they aren't equal by definition

#### [Kenny Lau (May 28 2018 at 11:37)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127197486):
they are equivalent

#### [Kenny Lau (May 28 2018 at 11:37)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127197488):
`exists x, x = y` is equivalent to `true`

#### [Kevin Buzzard (May 28 2018 at 11:38)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127197531):
How is one supposed to prove that stupid lemma anyway?

#### [Mario Carneiro (May 28 2018 at 11:38)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127197535):
`ext (by simp)`

#### [Mario Carneiro (May 28 2018 at 11:38)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127197539):
I would guess

#### [Mario Carneiro (May 28 2018 at 11:38)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127197541):
actually it's probably already a theorem

#### [Kevin Buzzard (May 28 2018 at 11:39)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127197552):
```lean
-- What actually happens in my head when proving the lemma id(U) = U for sets in Lean.

import data.set

-- ZFC-safe! The below code uses only Prop and Type 
-- (I didn't check the imports though)
variables {X Y : Type} (f : X → Y) (U : set X) 

definition image := {y : Y | ∃ x ∈ U, f x = y}

theorem are_they_equal : image (@id X) U = U := begin
/-
why am I wasting my time proving this stupid theorem. These
objects are ZFC-equal and thus equal. I will not even try. 
-/
-- rfl, -- fails
-- simp, -- fails -- *rolls eyes*
-- finish, -- I don't even understand what this one does but it sometimes works
-- cc (see comment above)
-- dsimp -- thought unlikely but maybe worth trying
-- can't think of any more tactics
unfold image,
apply set.eq_of_subset_of_subset,
{ intros x Hx,
  simpa using Hx},
{ intros x Hx,
  simpa using Hx,
}
-- thank goodness it's over
end
```

#### [Kevin Buzzard (May 28 2018 at 11:39)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127197553):
That's what actually happened

#### [Mario Carneiro (May 28 2018 at 11:39)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127197555):
`set.image_id`

#### [Mario Carneiro (May 28 2018 at 11:39)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127197559):
why are you proving trivial set theorems?

#### [Kevin Buzzard (May 28 2018 at 11:39)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127197561):
It's hard for me to prove that  ZFC-equal things are equal

#### [Kevin Buzzard (May 28 2018 at 11:40)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127197617):
because the tools I have honed in my brain to solve these problems

#### [Kevin Buzzard (May 28 2018 at 11:40)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127197618):
are ZFC tools

#### [Mario Carneiro (May 28 2018 at 11:40)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127197626):
that theorem is just as hard in zfc land

#### [Kevin Buzzard (May 28 2018 at 11:40)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127197627):
and here for some reason ZFC tools are not adequate

#### [Mario Carneiro (May 28 2018 at 11:40)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127197633):
the proof is literally no different

#### [Kevin Buzzard (May 28 2018 at 11:41)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127197644):
why does simp fail?

#### [Kevin Buzzard (May 28 2018 at 11:41)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127197646):
This proof is simple

#### [Kenny Lau (May 28 2018 at 11:41)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127197647):
@**Mario Carneiro** I tell you, when a mathematician says they work in ZFC, they actually don't. They won't even be able to name all of the ZFC axioms.

#### [Kevin Buzzard (May 28 2018 at 11:41)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127197650):
That's true for a general mathematician

#### [Mario Carneiro (May 28 2018 at 11:41)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127197654):
I can tell you I have worked in ZFC

#### [Kevin Buzzard (May 28 2018 at 11:41)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127197656):
but I know the axioms of ZFC and I've been working happily in it for years

#### [Mario Carneiro (May 28 2018 at 11:41)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127197657):
like for real

#### [Kevin Buzzard (May 28 2018 at 11:42)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127197697):
You mean "not using pen and paper"

#### [Kenny Lau (May 28 2018 at 11:42)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127197702):
```lean
example {α : Type*} (s : set α) : id '' s = s :=
set.ext (by simp [-set.image_id])
```

#### [Mario Carneiro (May 28 2018 at 11:42)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127197707):
I've done ZFC with pen and paper too, but that gets old fast

#### [Kevin Buzzard (May 28 2018 at 11:42)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127197709):
I guess LaTeX is the true home of ZFC.

#### [Kevin Buzzard (May 28 2018 at 11:43)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127197713):
For most people.

#### [Andrew Ashworth (May 28 2018 at 11:43)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127197722):
... isn't metamath basically zfc on pen and paper

#### [Kevin Buzzard (May 28 2018 at 11:43)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127197726):
OK so I think dependent type theory is stupid and I've decided to go back to ZFC and formulate perfectoid spaces there instead where I don't have to waste my time worrying about whether or not id U is equal to U.

#### [Kevin Buzzard (May 28 2018 at 11:43)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127197727):
So where do I start?

#### [Kevin Buzzard (May 28 2018 at 11:44)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127197767):
if I want to do it on a computer

#### [Kenny Lau (May 28 2018 at 11:44)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127197771):
I thought Isabelle works in ZFC

#### [Kevin Buzzard (May 28 2018 at 11:44)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127197773):
I don't even know what Isabelle is

#### [Mario Carneiro (May 28 2018 at 11:44)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127197775):
It uses HOL for all the good stuff

#### [Kevin Buzzard (May 28 2018 at 11:44)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127197778):
so Isabelle-ZFC is a thing?

#### [Mario Carneiro (May 28 2018 at 11:44)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127197779):
Isabelle/ZFC is more of a proof of concept

#### [Kevin Buzzard (May 28 2018 at 11:44)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127197780):
that doesn't sound good

#### [Kevin Buzzard (May 28 2018 at 11:44)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127197782):
does it have number fields?

#### [Kenny Lau (May 28 2018 at 11:45)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127197788):
and secondly, nobody works in ZFC. they work in ZFC + definitorial expansion

#### [Mario Carneiro (May 28 2018 at 11:45)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127197791):
If you want to really use ZFC on the computer, you should use Mizar or Metamath

#### [Kevin Buzzard (May 28 2018 at 11:45)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127197795):
Why not Isabelle-ZFC?

#### [Mario Carneiro (May 28 2018 at 11:45)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127197798):
because it is not mature enough

#### [Mario Carneiro (May 28 2018 at 11:45)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127197810):
maybe mature is the wrong word, it's been around for a while but it doesn't have enough theorems

#### [Kevin Buzzard (May 28 2018 at 11:45)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127197811):
Which of the three possibilities for computer-ZFC is most mathematician-friendly?

#### [Kevin Buzzard (May 28 2018 at 11:46)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127197852):
Or is it a case of "learn one of them, you just learned all of them"

#### [Kevin Buzzard (May 28 2018 at 11:46)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127197857):
I have no idea

#### [Kevin Buzzard (May 28 2018 at 11:46)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127197863):
I just play ZFC internally on my own emulator

#### [Mario Carneiro (May 28 2018 at 11:46)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127197864):
Mizar was written by mathematicians for mathematicians

#### [Mario Carneiro (May 28 2018 at 11:46)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127197866):
this is not necessarily a good thing

#### [Kevin Buzzard (May 28 2018 at 11:46)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127197867):
In ZFC

#### [Mario Carneiro (May 28 2018 at 11:46)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127197869):
in TG set theory

#### [Kevin Buzzard (May 28 2018 at 11:47)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127197879):
If ZFC and DTT had a race to perfectoid spaces, and you could choose your foundational system, and we started tomorrow, who would win?

#### [Mario Carneiro (May 28 2018 at 11:47)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127197883):
ZFC is an axiom system not a program

#### [Kevin Buzzard (May 28 2018 at 11:47)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127197888):
I am not CS-wise enough to understand the difference

#### [Kevin Buzzard (May 28 2018 at 11:47)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127197893):
I want a program whose only commands are things allowed in ZFC

#### [Kevin Buzzard (May 28 2018 at 11:48)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127197895):
and all things allowed in ZFC are commands

#### [Mario Carneiro (May 28 2018 at 11:48)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127197933):
You aren't choosing ZFC or DTT, you're choosing Mizar or Lean or Coq or Isabelle

#### [Kevin Buzzard (May 28 2018 at 11:48)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127197939):
Does this make sense -- "I choose Mizar, and therefore I choose ZFC"

#### [Mario Carneiro (May 28 2018 at 11:48)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127197941):
sure

#### [Kevin Buzzard (May 28 2018 at 11:48)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127197942):
I don't know what Mizar is

#### [Kevin Buzzard (May 28 2018 at 11:48)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127197946):
but I do know what ZFC is

#### [Kevin Buzzard (May 28 2018 at 11:48)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127197951):
And "I choose Lean, and therefore I choose dependent type theory"

#### [Mario Carneiro (May 28 2018 at 11:49)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127197959):
right, lean doesn't give you a choice here

#### [Mario Carneiro (May 28 2018 at 11:49)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127197963):
same with most other systems

#### [Kevin Buzzard (May 28 2018 at 11:49)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127197971):
So who would win the perfectoid space showdown between Lean and "insert computer program which models ZFC in some way"

#### [Kevin Buzzard (May 28 2018 at 11:50)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127198017):
If I got cloned into two people and just had a race with myself

#### [Mario Carneiro (May 28 2018 at 11:50)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127198018):
Isabelle and Metamath are a bit special since they are foundational frameworks, so you can technically pick your favorite axiom system, but in practice all the theorems go to one particular axiom system

#### [Mario Carneiro (May 28 2018 at 11:50)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127198031):
If you got cloned? Lean of course

#### [Kevin Buzzard (May 28 2018 at 11:50)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127198032):
Are there more mathematical theorems in Mathlib than in any library for any ZFC system?

#### [Mario Carneiro (May 28 2018 at 11:51)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127198036):
because you know lean better than any other system

#### [Kevin Buzzard (May 28 2018 at 11:51)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127198040):
But Mario, I speak *fluent* ZFC

#### [Mario Carneiro (May 28 2018 at 11:51)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127198049):
and you will find that it doesn't matter

#### [Kevin Buzzard (May 28 2018 at 11:51)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127198051):
It's my native language

#### [Mario Carneiro (May 28 2018 at 11:51)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127198055):
because you will be struggling with formal details the whole way

#### [Mario Carneiro (May 28 2018 at 11:51)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127198060):
that's always the way it goes

#### [Kevin Buzzard (May 28 2018 at 11:51)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127198063):
I think this is precisely the point I don't understand

#### [Kevin Buzzard (May 28 2018 at 11:52)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127198138):
let me rephrase that -- the distinction between "Lean" and "Dependent type theory" is quite blurred in my mind

#### [Kevin Buzzard (May 28 2018 at 11:53)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127198148):
I thought I could just define dependent type theory to be Lean

#### [Kenny Lau (May 28 2018 at 11:53)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127198151):
it's one thing to know the theory behind Python

#### [Kenny Lau (May 28 2018 at 11:53)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127198154):
it's a completely other thing to use Python

#### [Kevin Buzzard (May 28 2018 at 11:53)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127198158):
I guess

#### [Kevin Buzzard (May 28 2018 at 11:53)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127198160):
I completely understand that

#### [Kevin Buzzard (May 28 2018 at 11:53)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127198162):
I see

#### [Kevin Buzzard (May 28 2018 at 11:54)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127198205):
But this is a really easy problem

#### [Kevin Buzzard (May 28 2018 at 11:54)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127198206):
I just get the CS people to write python for me

#### [Kevin Buzzard (May 28 2018 at 11:54)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127198207):
so they are the same thing

#### [Kevin Buzzard (May 28 2018 at 11:54)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127198210):
Now who wrote ZFC for me?

#### [Mario Carneiro (May 28 2018 at 11:54)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127198214):
but you don't want ZFC, not really

#### [Kevin Buzzard (May 28 2018 at 11:55)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127198218):
I love ZFC Mario

#### [Mario Carneiro (May 28 2018 at 11:55)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127198219):
you want by schoolkid and tactics and magic

#### [Kevin Buzzard (May 28 2018 at 11:55)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127198223):
Yeah and we _need_ schoolkid

#### [Mario Carneiro (May 28 2018 at 11:55)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127198227):
ZFC is an axiom system, it made no magical promises

#### [Kevin Buzzard (May 28 2018 at 11:55)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127198230):
no but you CS guys will just sort all that out

#### [Kevin Buzzard (May 28 2018 at 11:55)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127198234):
that's just some stupid engineering issue

#### [Kevin Buzzard (May 28 2018 at 11:55)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127198237):
I want to do ZFC, like I do Python in Python

#### [Mario Carneiro (May 28 2018 at 11:55)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127198238):
but it's a really important engineering issue for you

#### [Kenny Lau (May 28 2018 at 11:55)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127198239):
@**Kevin Buzzard** how would you prove in ZFC that `id '' U = U`?

#### [Mario Carneiro (May 28 2018 at 11:56)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127198279):
I dare say it's far more important than the underlying axiom system

#### [Kevin Buzzard (May 28 2018 at 11:56)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127198286):
id(u) is the same as u

#### [Kenny Lau (May 28 2018 at 11:56)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127198290):
no they aren't

#### [Kevin Buzzard (May 28 2018 at 11:56)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127198292):
sure it is

#### [Kenny Lau (May 28 2018 at 11:56)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127198294):
how would you prove it?

#### [Mario Carneiro (May 28 2018 at 11:56)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127198295):
that's not a proof

#### [Kevin Buzzard (May 28 2018 at 11:56)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127198297):
id is a big set of ordered pairs

#### [Kevin Buzzard (May 28 2018 at 11:56)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127198301):
and they're all just (u,u)

#### [Kenny Lau (May 28 2018 at 11:56)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127198302):
a proper class

#### [Kevin Buzzard (May 28 2018 at 11:56)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127198303):
no it's a set

#### [Kevin Buzzard (May 28 2018 at 11:56)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127198307):
don't be silly

#### [Mario Carneiro (May 28 2018 at 11:57)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127198309):
wha...

#### [Kenny Lau (May 28 2018 at 11:57)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127198310):
ok

#### [Kevin Buzzard (May 28 2018 at 11:57)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127198312):
it's a function from U to U

#### [Kenny Lau (May 28 2018 at 11:57)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127198319):
but here it isn't

#### [Mario Carneiro (May 28 2018 at 11:57)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127198324):
ZFC warning

#### [Kenny Lau (May 28 2018 at 11:57)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127198325):
it's a function from alpha to alpha, U is just a subset

#### [Kevin Buzzard (May 28 2018 at 11:57)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127198326):
but here is stupid. I'm telling you the right way.

#### [Mario Carneiro (May 28 2018 at 11:57)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127198328):
that's doing to make your job messy

#### [Kevin Buzzard (May 28 2018 at 11:57)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127198329):
so id(u) is *equal* to u OK

#### [Kevin Buzzard (May 28 2018 at 11:57)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127198331):
so {id(u) : u in U}

#### [Kevin Buzzard (May 28 2018 at 11:57)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127198332):
EQUALS

#### [Kevin Buzzard (May 28 2018 at 11:57)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127198333):
{u : u in U}

#### [Kevin Buzzard (May 28 2018 at 11:57)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127198334):
which

#### [Kenny Lau (May 28 2018 at 11:57)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127198335):
```quote
so id(u) is *equal* to u OK
```
you still haven't proved it. what after id being a big set of pairs

#### [Kevin Buzzard (May 28 2018 at 11:57)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127198337):
EQUALS

#### [Kevin Buzzard (May 28 2018 at 11:57)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127198339):
U

#### [Kevin Buzzard (May 28 2018 at 11:58)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127198382):
I don't understand which bit I missed

#### [Kenny Lau (May 28 2018 at 11:58)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127198384):
you're abusing notations.

#### [Kevin Buzzard (May 28 2018 at 11:58)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127198385):
oh

#### [Mario Carneiro (May 28 2018 at 11:58)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127198389):
yes, you unfold the definitions, that {id(u) : u in U} thing becomes {y : \ex u, id(u) = y}

#### [Kenny Lau (May 28 2018 at 11:58)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127198390):
{u : u in U} isn't equal to {u in U | true}

#### [Kevin Buzzard (May 28 2018 at 11:58)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127198393):
I thought I was using "=" as in the underlying logic or syntax or whatever it's called of ZFC or logic or

#### [Kenny Lau (May 28 2018 at 11:58)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127198394):
you mixed comprehension notation and subset notation

#### [Kevin Buzzard (May 28 2018 at 11:58)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127198395):
I am not clear about what = is in ZFC

#### [Kevin Buzzard (May 28 2018 at 11:58)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127198396):
I forgot the details

#### [Mario Carneiro (May 28 2018 at 11:58)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127198397):
and then you have a lemma proving that id(u) = u since (u,u) in id

#### [Kevin Buzzard (May 28 2018 at 11:58)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127198400):
but it just means they're the same object

#### [Kenny Lau (May 28 2018 at 11:58)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127198401):
by "isn't equal to" I mean "you haven't proved that they are equal"

#### [Mario Carneiro (May 28 2018 at 11:59)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127198402):
and id is a function because ...

#### [Kenny Lau (May 28 2018 at 11:59)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127198407):
```quote
but it just means they're the same object
```
but it needs to be proved

#### [Kenny Lau (May 28 2018 at 11:59)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127198412):
you can't just say "they must be equal"

#### [Kenny Lau (May 28 2018 at 11:59)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127198415):
you see, the problem is not in the axioms

#### [Kenny Lau (May 28 2018 at 11:59)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127198416):
but in the formality

#### [Mario Carneiro (May 28 2018 at 11:59)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127198417):
and then you get \ex u in U, u = y <-> u in U

#### [Mario Carneiro (May 28 2018 at 11:59)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127198421):
and hey presto it's the lean proof

#### [Kevin Buzzard (May 28 2018 at 11:59)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127198425):
But in the world where proofs are free and can be appealed to at will using good tactics, "simp" would prove this

#### [Kenny Lau (May 28 2018 at 12:00)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127198428):
right, so ZFC isn't the problem at all

#### [Mario Carneiro (May 28 2018 at 12:00)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127198429):
SIMP CAN PROVE THIS

#### [Kenny Lau (May 28 2018 at 12:00)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127198470):
yes

#### [Kevin Buzzard (May 28 2018 at 12:00)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127198471):
because my definition of "simp" is the ZFC tactic "this is simple if you use ZFC"

#### [Mario Carneiro (May 28 2018 at 12:00)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127198481):
That's not a tactic, that's magic

#### [Kevin Buzzard (May 28 2018 at 12:00)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127198482):
I think that's why my understanding of tactics is so poor

#### [Kenny Lau (May 28 2018 at 12:00)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127198483):
```lean
example {α : Type*} (s : set α) : id '' s = s :=
set.ext $ by simp [-set.image_id]
```

#### [Kenny Lau (May 28 2018 at 12:00)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127198484):
simp **can** prove this

#### [Kevin Buzzard (May 28 2018 at 12:00)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127198488):
There are a whole bunch of distinct things in dependent type theory which I have truly identified in my head

#### [Kevin Buzzard (May 28 2018 at 12:01)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127198490):
and the big question is

#### [Kevin Buzzard (May 28 2018 at 12:01)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127198497):
is that going to give you problems down the line

#### [Kevin Buzzard (May 28 2018 at 12:01)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127198499):
by which I mean me

#### [Kevin Buzzard (May 28 2018 at 12:01)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127198500):
the ZFCist

#### [Kevin Buzzard (May 28 2018 at 12:01)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127198505):
I got lucky. I needed a map `F U -> F (id '' U)`

#### [Kevin Buzzard (May 28 2018 at 12:02)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127198545):
and I chose wrong. I proved `id '' U = U` and then did a rewrite and used id.

#### [Kevin Buzzard (May 28 2018 at 12:02)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127198547):
because they're the SAME OBJECT

#### [Kevin Buzzard (May 28 2018 at 12:02)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127198552):
and the identity map from an object to itself is called id.

#### [Mario Carneiro (May 28 2018 at 12:02)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127198561):
this is a better argument

#### [Kevin Buzzard (May 28 2018 at 12:02)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127198565):
So I used id and instantly got into all manner of trouble the moment I tried to prove things

#### [Kenny Lau (May 28 2018 at 12:02)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127198567):
1. you don't really work in pure ZFC. you work in ZFC + definitorial expansion + a whole bunch of other things

#### [Kenny Lau (May 28 2018 at 12:02)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127198584):
in ZFC `id '' U` isn't even defined

#### [Kenny Lau (May 28 2018 at 12:03)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127198597):
ZFC says that there exists such an object

#### [Mario Carneiro (May 28 2018 at 12:03)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127198598):
The dtt analogue of this is called equality reflection

#### [Kenny Lau (May 28 2018 at 12:03)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127198611):
you're using the axiom of replacement

#### [Kevin Buzzard (May 28 2018 at 12:03)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127198615):
And then I went back and thought "do you know what -- I could use res!"

#### [Mario Carneiro (May 28 2018 at 12:03)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127198618):
it says that if `x = y` then `x` and `y` are defeq

#### [Kenny Lau (May 28 2018 at 12:03)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127198620):
it begins `forall A exists B`

#### [Kevin Buzzard (May 28 2018 at 12:03)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127198623):
And I thought "that's funny, because it's an *axiom of a functor* that res U U = id"

#### [Kenny Lau (May 28 2018 at 12:03)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127198624):
in ZFC everything is Prop

#### [Mario Carneiro (May 28 2018 at 12:03)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127198626):
This is needed to typecheck things like `id : F U -> F (id '' U)`

#### [Kevin Buzzard (May 28 2018 at 12:03)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127198629):
"so res is *the same as* id"

#### [Kevin Buzzard (May 28 2018 at 12:04)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127198674):
and I tried res

#### [Kevin Buzzard (May 28 2018 at 12:04)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127198676):
and then all my one page long goals were rfl

#### [Kevin Buzzard (May 28 2018 at 12:05)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127198689):
because I gave same ZFC answer in two different ways, the first arguably being "more natural for the ZFC-ist", and the second apparently being "more natural for the DTT-ist".

#### [Kevin Buzzard (May 28 2018 at 12:05)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127198694):
I don't understand why my id is the wrong idea.

#### [Patrick Massot (May 28 2018 at 12:05)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127198695):
Kevin, formalized maths will be crazy in any system. You can only hope automation will get better at hiding this crazyness. And it seems DTT is better that set theory in order to build automation

#### [Mario Carneiro (May 28 2018 at 12:05)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127198697):
You can use `id` like you did, but you need a lemma about it

#### [Kevin Buzzard (May 28 2018 at 12:05)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127198699):
I cannot envisage a single problem doing this in ZFC

#### [Kevin Buzzard (May 28 2018 at 12:06)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127198743):
The issue is making a computer assert this statement?

#### [Mario Carneiro (May 28 2018 at 12:06)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127198744):
this would be WAY harder in metamath because of all the dependencies

#### [Kenny Lau (May 28 2018 at 12:06)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127198746):
```quote
I cannot envisage a single problem doing this in ZFC
```
no, you would need as many lemmas

#### [Kevin Buzzard (May 28 2018 at 12:06)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127198747):
is metamath ZFC?

#### [Kenny Lau (May 28 2018 at 12:06)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127198748):
ZFC / DTT is not the issue at all

#### [Mario Carneiro (May 28 2018 at 12:06)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127198749):
lean is good at hiding complexity, which is not always a good thing

#### [Kevin Buzzard (May 28 2018 at 12:07)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127198757):
I should do a proper survey.

#### [Mario Carneiro (May 28 2018 at 12:07)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127198758):
on the one hand it means you can formalize much bigger statements, on the other it means you don't work as much on parsimony and as a result have to struggle with large goals

#### [Kevin Buzzard (May 28 2018 at 12:07)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127198759):
Do I have a complete list of "computer programs which help you do ZFC"?

#### [Mario Carneiro (May 28 2018 at 12:08)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127198798):
Of course lean is on that list

#### [Kevin Buzzard (May 28 2018 at 12:09)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127198806):
@**Kenny Lau** No! Simp didn't prove it! You had to write some .set.image gobble-de-gook theorem as well which probably also says "two identical things are equal"

#### [Kenny Lau (May 28 2018 at 12:09)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127198810):
@**Kevin Buzzard** no, I had to write `-set.image_id` to show that it isn't automated

#### [Kenny Lau (May 28 2018 at 12:09)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127198811):
because `set.image_id` is the theorem

#### [Mario Carneiro (May 28 2018 at 12:09)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127198812):
the set_image thing is just to avoid an even more trivial proof

#### [Kevin Buzzard (May 28 2018 at 12:09)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127198814):
If simp worked properly, it would solve that goal

#### [Kevin Buzzard (May 28 2018 at 12:09)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127198815):
just by simp

#### [Kevin Buzzard (May 28 2018 at 12:09)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127198817):
because it's simple

#### [Kenny Lau (May 28 2018 at 12:09)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127198818):
Kevin.

#### [Kenny Lau (May 28 2018 at 12:09)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127198819):
it's a minus.

#### [Kenny Lau (May 28 2018 at 12:09)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127198820):
I'm telling `simp` not to use that theorem.

#### [Kevin Buzzard (May 28 2018 at 12:10)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127198821):
I know

#### [Kenny Lau (May 28 2018 at 12:10)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127198861):
because otherwise the proof would be trivial

#### [Mario Carneiro (May 28 2018 at 12:10)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127198863):
just `by simp` does prove that theorem

#### [Mario Carneiro (May 28 2018 at 12:10)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127198866):
because it's a simp lemma

#### [Mario Carneiro (May 28 2018 at 12:10)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127198868):
and without the theorem, the proof is `ext $ by simp`

#### [Kevin Buzzard (May 28 2018 at 12:10)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127198869):
```lean
Tactic State

X : Type,
U : set X
⊢ image id U = U
id_U_equals_U.lean:11:51: error

simplify tactic failed to simplify
state:
X : Type,
U : set X
⊢ image id U = U
```

#### [Kevin Buzzard (May 28 2018 at 12:10)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127198872):
"by simp" doesn't solve it so "by simp" is broken

#### [Kevin Buzzard (May 28 2018 at 12:10)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127198873):
because it's simple

#### [Kevin Buzzard (May 28 2018 at 12:10)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127198874):
that's all I'm saying

#### [Mario Carneiro (May 28 2018 at 12:10)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127198875):
you defined your own image

#### [Mario Carneiro (May 28 2018 at 12:11)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127198878):
it has no simp lemmas like the real one

#### [Kevin Buzzard (May 28 2018 at 12:11)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127198883):
you guys are just weirdos

#### [Kenny Lau (May 28 2018 at 12:11)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127198885):
Kevin

#### [Mario Carneiro (May 28 2018 at 12:11)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127198887):
It's like you shot me in the leg and asked why I can't run as fast

#### [Kenny Lau (May 28 2018 at 12:11)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127198889):
have we established that in ZFC you still need to prove it

#### [Kevin Buzzard (May 28 2018 at 12:11)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127198890):
Maybe it's time I tried Mizar.

#### [Kevin Buzzard (May 28 2018 at 12:11)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127198892):
I'll come back with egg on my face later

#### [Kenny Lau (May 28 2018 at 12:12)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127198929):
I don't really see the issue

#### [Kenny Lau (May 28 2018 at 12:12)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127198932):
I think you're misunderstanding

#### [Kenny Lau (May 28 2018 at 12:12)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127198933):
you said it's stupid because they aren't defeq

#### [Kevin Buzzard (May 28 2018 at 12:12)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127198935):
if it's not by simp for some reason

#### [Mario Carneiro (May 28 2018 at 12:12)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127198936):
simp requires a whole library of carefully crafted lemmas to work well

#### [Kevin Buzzard (May 28 2018 at 12:12)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127198937):
then it should be by schoolkid

#### [Mario Carneiro (May 28 2018 at 12:12)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127198938):
because it's not magic

#### [Kevin Buzzard (May 28 2018 at 12:12)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127198940):
How can you claim it works well

#### [Kevin Buzzard (May 28 2018 at 12:12)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127198942):
if it cannot even prove id(U)=U

#### [Kevin Buzzard (May 28 2018 at 12:12)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127198945):
when they're the same object

#### [Kevin Buzzard (May 28 2018 at 12:13)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127198950):
That's what I'm hearing :-)

#### [Mario Carneiro (May 28 2018 at 12:13)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127198951):
you are being unusually stubborn today

#### [Kenny Lau (May 28 2018 at 12:13)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127198952):
1. you said Lean is stupid because `id '' U = U` isn't `rfl`. But they also aren't rfl in ZFC, you also need to prove it (remember how you mixed comprehension notation and subset notation)

#### [Kevin Buzzard (May 28 2018 at 12:13)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127198956):
and I know it's not what you're saying

#### [Kevin Buzzard (May 28 2018 at 12:13)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127198957):
but I'm a bit deaf

#### [Kenny Lau (May 28 2018 at 12:13)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127198958):
2. you said Lean is stupid because `id '' U = u` isn't `by simp`. But it is.

#### [Kevin Buzzard (May 28 2018 at 12:13)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127198959):
I was just doing my ZFC-baiting thing

#### [Kenny Lau (May 28 2018 at 12:13)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127198960):
3. you said Lean is stupid because `id '' U = U` isn't `ext $ by simp`. But it is.

#### [Kenny Lau (May 28 2018 at 12:13)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127198961):
so I don't know what your issue is

#### [Kevin Buzzard (May 28 2018 at 12:14)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127199000):
by simp doesn't work for me

#### [Kevin Buzzard (May 28 2018 at 12:14)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127199002):
does it work for you?

#### [Kenny Lau (May 28 2018 at 12:14)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127199004):
because you're using the wrong image

#### [Kevin Buzzard (May 28 2018 at 12:14)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127199006):
I'm using the image I wrote

#### [Kenny Lau (May 28 2018 at 12:14)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127199007):
use the official image and everything will be fine

#### [Kenny Lau (May 28 2018 at 12:14)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127199011):
of course your new image doesn't have simp lemmas

#### [Kevin Buzzard (May 28 2018 at 12:14)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127199012):
Wait so didn't lots of people tell me that this was impossible or something?

#### [Kenny Lau (May 28 2018 at 12:15)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127199016):
4. you said Lean is stupid because `simp` doesn't simplify it with your **new** image definition. But we already established that it is not a rfl theorem, so you have to use the official image if you want to use a simp lemma

#### [Kevin Buzzard (May 28 2018 at 12:15)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127199027):
that's stupid. What if I can't find the official image so I just make my own image which would then be identical so all the old theorems would work anyway

#### [Kevin Buzzard (May 28 2018 at 12:15)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127199028):
hmm

#### [Mario Carneiro (May 28 2018 at 12:15)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127199030):
no

#### [Kevin Buzzard (May 28 2018 at 12:15)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127199032):
OK so

#### [Kevin Buzzard (May 28 2018 at 12:16)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127199063):
I can see there might be issues here

#### [Kenny Lau (May 28 2018 at 12:16)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127199071):
@**Kevin Buzzard** read my point 4 again

#### [Kevin Buzzard (May 28 2018 at 12:16)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127199072):
at least

#### [Kevin Buzzard (May 28 2018 at 12:16)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127199075):
from an engineering point of view

#### [Mario Carneiro (May 28 2018 at 12:16)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127199079):
the theorems only "work" if you apply them

#### [Kenny Lau (May 28 2018 at 12:16)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127199081):
@**Mario Carneiro** it doesn't work

#### [Kevin Buzzard (May 28 2018 at 12:16)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127199082):
No

#### [Kevin Buzzard (May 28 2018 at 12:16)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127199083):
I'm listening

#### [Mario Carneiro (May 28 2018 at 12:17)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127199084):
yeah, I messed up the copy there

#### [Kevin Buzzard (May 28 2018 at 12:17)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127199090):
I understand that I have to apply my theorems

#### [Kenny Lau (May 28 2018 at 12:17)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127199091):
@**Kevin Buzzard** so I don't really see where the issue is.

#### [Kevin Buzzard (May 28 2018 at 12:17)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127199093):
but in return

#### [Kevin Buzzard (May 28 2018 at 12:17)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127199095):
here's the thing

#### [Kenny Lau (May 28 2018 at 12:17)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127199098):
you're complaining that `simp` doesn't know about your new `image`

#### [Johan Commelin (May 28 2018 at 12:17)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127199099):
Kevin, don't think of `simp` as "simple", but as "simplify"

#### [Kevin Buzzard (May 28 2018 at 12:17)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127199100):
when I prove a theorem that says that A and B are equal

#### [Kevin Buzzard (May 28 2018 at 12:17)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127199101):
in DTT speak

#### [Kevin Buzzard (May 28 2018 at 12:18)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127199143):
`theorem they_are_equal : X = Y := by schoolkid`

#### [Johan Commelin (May 28 2018 at 12:18)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127199144):
So, it's not `simp`'s purpose to prove it. But `schoolkid` or `math_trivial` should be able to prove it

#### [Kevin Buzzard (May 28 2018 at 12:18)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127199146):
Whenever that happens in dependent type theory

#### [Kenny Lau (May 28 2018 at 12:18)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127199147):
@**Kevin Buzzard** Kevin.

#### [Kevin Buzzard (May 28 2018 at 12:18)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127199148):
I want dependent type theory to now collapse a little

#### [Kenny Lau (May 28 2018 at 12:18)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127199149):
I think this will convince you.

#### [Kenny Lau (May 28 2018 at 12:19)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127199150):
```lean
definition image := {y : Y | ∃ x ∈ U, f x = y}
example : image (@id X) U = U :=
by simp [image]
```

#### [Mario Carneiro (May 28 2018 at 12:20)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127199214):
I think you are focusing on the wrong issue Kevin

#### [Kenny Lau (May 28 2018 at 12:20)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127199217):
you broke the silence >_>

#### [Johan Commelin (May 28 2018 at 12:20)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127199218):
So we want `schoolkid_1` which just does `simp [..every definition preceding it in the file..]`

#### [Mario Carneiro (May 28 2018 at 12:21)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127199231):
There is nothing at all wrong with the proof of id '' U = U, but it caused problems later when you used it as a functor in your presheaf

#### [Mario Carneiro (May 28 2018 at 12:22)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127199275):
For that you need theorems about the action of `eq.rec` or `cast`

#### [Kevin Buzzard (May 28 2018 at 12:22)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127199279):
Is this supposed to be rfl?

#### [Mario Carneiro (May 28 2018 at 12:22)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127199280):
 and they aren't free, you have to state them

#### [Kevin Buzzard (May 28 2018 at 12:22)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127199282):
`theorem X : id '' U = U := sorry `

#### [Kenny Lau (May 28 2018 at 12:22)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127199285):
```quote
Is this supposed to be rfl?
```
I thought we already established that it is not rfl

#### [Kenny Lau (May 28 2018 at 12:22)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127199286):
not in ZFC either

#### [Kevin Buzzard (May 28 2018 at 12:22)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127199287):
So that is not rfl

#### [Kevin Buzzard (May 28 2018 at 12:22)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127199288):
but what was rfl?

#### [Kenny Lau (May 28 2018 at 12:22)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127199290):
rfl is using "forall x, x = x"

#### [Mario Carneiro (May 28 2018 at 12:22)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127199292):
`schoolkid_1` is `simp!`

#### [Kenny Lau (May 28 2018 at 12:23)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127199299):
so in ZFC, you need to do reductions to simplify them to the same expression, and then use that axiom

#### [Kenny Lau (May 28 2018 at 12:23)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127199301):
but they can't be reduced to the same thing

#### [Mario Carneiro (May 28 2018 at 12:23)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127199302):
ZFC has no reductions at all

#### [Kenny Lau (May 28 2018 at 12:23)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127199304):
```quote
`schoolkid_1` is `simp!`
```
nope, doesn't work

#### [Mario Carneiro (May 28 2018 at 12:23)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127199310):
In fact rfl is much weaker in ZFC

#### [Kenny Lau (May 28 2018 at 12:24)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127199346):
@**Kevin Buzzard** you aren't working in ZFC. you are working in ZFC + definition expansion + delta reduction

#### [Kevin Buzzard (May 28 2018 at 12:24)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127199349):
Mario quote
```
import data.set

-- ZFC-safe! The below code uses only Prop and Type

variables {X Y : Type} (f : X → Y) (U : set X)

theorem they_are_not_defeq : image (@id X) U = U := rfl -- works
```
Doesn't work for me

#### [Mario Carneiro (May 28 2018 at 12:24)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127199355):
`+` equality reflection

#### [Kevin Buzzard (May 28 2018 at 12:24)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127199361):
`unknown identifier 'image'`

#### [Kenny Lau (May 28 2018 at 12:24)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127199362):
@**Kevin Buzzard** I really do not see any problem at all. `id '' U` does not expand to `U`. you have to destruct the definitions and **use extensionality**

#### [Mario Carneiro (May 28 2018 at 12:24)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127199365):
I didn't say that

#### [Kenny Lau (May 28 2018 at 12:25)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127199367):
that's what I mean

#### [Kevin Buzzard (May 28 2018 at 12:25)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127199373):
I am just trying to get to the bottom of things

#### [Kevin Buzzard (May 28 2018 at 12:25)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127199374):
but I have never seen refl work for anything

#### [Kenny Lau (May 28 2018 at 12:25)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127199377):
if you need to **use the axiom of extensionality** to prove that they are equal, then they aren't definitionally equal

#### [Kevin Buzzard (May 28 2018 at 12:25)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127199378):
and I've never seen by simp work either

#### [Kenny Lau (May 28 2018 at 12:25)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127199380):
and i'm working in ZFC to say that

#### [Kevin Buzzard (May 28 2018 at 12:25)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127199381):
but I'm just trying to put everything together

#### [Kevin Buzzard (May 28 2018 at 12:25)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127199384):
it's hard trying to distinguish between equal things

#### [Mario Carneiro (May 28 2018 at 12:26)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127199440):
It's not so hard: `id '' U` has more words than `U`, so they aren't the same

#### [Mario Carneiro (May 28 2018 at 12:28)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127199502):
Here's an example of `rfl` working:
```
definition image := {y : Y | ∃ x ∈ U, y = f x}

example : image (@id X) U = {y | ∃ x ∈ U, y = x} := rfl
```

#### [Mario Carneiro (May 28 2018 at 12:29)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127199506):
that's how definitional expansion is supposed to work

#### [Mario Carneiro (May 28 2018 at 12:29)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127199512):
this is what ZFC gives you (except you would have to work on id(x) = x in the middle there, that's not definitional in ZFC)

#### [Kenny Lau (May 28 2018 at 12:29)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127199516):
@**Kevin Buzzard** here's how I can formalize what I say: if you didn't have `propext` as an axiom, then you won't be able to prove that the two sets are equal, in Lean

#### [Kenny Lau (May 28 2018 at 12:30)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127199557):
the ZFC version replaces `propext` with the axiom of extensionality

#### [Kevin Buzzard (May 28 2018 at 12:31)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127199573):
```lean
import data.set

-- ZFC-safe! The below code uses only Prop and Type

variables {X Y : Type} (f : X → Y) (U : set X)

definition image' := {y : Y | ∃ x ∈ U, f x = y}

theorem they_are_the_same : image' (@id X) U = U := by refl -- fails
theorem they_are_the_same' : id '' U = U := by refl -- fails
theorem they_are_all_the_same_thing_ : id '' U = image' (@id X) U := by refl -- fails
theorem but_they_are_all_the_same : set.image (@id X) U = U := by refl -- fails
theorem why_are_they_all_different : id '' U = set.image (@id X) U := by refl -- thank god


```

#### [Kevin Buzzard (May 28 2018 at 12:31)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127199574):
:-(

#### [Kevin Buzzard (May 28 2018 at 12:31)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127199585):
They are the same -- you just have the wrong equivalence relation

#### [Kenny Lau (May 28 2018 at 12:31)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127199588):
I've been repeating the same thing 100 times.

#### [Mario Carneiro (May 28 2018 at 12:32)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127199627):
`set.image` is defined as `{y : Y | ∃ x, x ∈ U ∧ f x = y}`

#### [Kevin Buzzard (May 28 2018 at 12:32)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127199633):
```quote
I've been repeating the same thing 100 times.
```
I know but you didn't fix it yet

#### [Kevin Buzzard (May 28 2018 at 12:32)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127199634):
all the proofs are "by schoolkid"

#### [Kevin Buzzard (May 28 2018 at 12:32)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127199636):
Kenny do you want to do that for your 1st year project?

#### [Kenny Lau (May 28 2018 at 12:32)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127199637):
```quote
```lean
definition image := {y : Y | ∃ x ∈ U, f x = y}
example : image (@id X) U = U :=
by simp [image]
```
```

#### [Kenny Lau (May 28 2018 at 12:32)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127199638):
you must be blind

#### [Kevin Buzzard (May 28 2018 at 12:33)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127199643):
but it never just says "by simp"

#### [Kevin Buzzard (May 28 2018 at 12:33)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127199648):
which ones get done by simp

#### [Mario Carneiro (May 28 2018 at 12:33)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127199649):
no because that would be horrible in most proofs

#### [Kenny Lau (May 28 2018 at 12:33)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127199651):
Kevin, you don't want `by simp` to automatically unfold every definition for you.

#### [Kevin Buzzard (May 28 2018 at 12:34)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127199692):
```lean
import data.set

-- ZFC-safe! The below code uses only Prop and Type

variables {X Y : Type} (f : X → Y) (U : set X)

definition image' := {y : Y | ∃ x ∈ U, f x = y}

theorem they_are_the_same : image' (@id X) U = U := by simp -- fails
theorem they_are_the_same' : id '' U = U := by simp -- fails
theorem they_are_all_the_same_thing_ : id '' U = image' (@id X) U := by simp -- fails
theorem but_they_are_all_the_same : set.image (@id X) U = U := by simp -- fails
theorem why_are_they_all_different : id '' U = set.image (@id X) U := by simp -- I wasn't 100% confident but we got through



```

#### [Kevin Buzzard (May 28 2018 at 12:34)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127199695):
Why do I have to work, or even *think*, about proving that two objects are the same, when they are the same object?

#### [Kenny Lau (May 28 2018 at 12:34)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127199696):
here we go again

#### [Kevin Buzzard (May 28 2018 at 12:34)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127199697):
Why doesn't it do it for me?

#### [Kevin Buzzard (May 28 2018 at 12:34)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127199699):
That's what I want

#### [Kevin Buzzard (May 28 2018 at 12:34)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127199700):
Make it do it for me

#### [Kevin Buzzard (May 28 2018 at 12:34)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127199701):
simp is rubbish

#### [Kevin Buzzard (May 28 2018 at 12:34)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127199703):
make a proper one

#### [Kenny Lau (May 28 2018 at 12:34)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127199704):
do we have to go through the ZFC proof that they are the same again?

#### [Kevin Buzzard (May 28 2018 at 12:34)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127199705):
make schoolkid

#### [Mario Carneiro (May 28 2018 at 12:35)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127199710):
Stop trolling Kevin

#### [Kevin Buzzard (May 28 2018 at 12:35)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127199713):
I don't understand why this can't be done

#### [Kenny Lau (May 28 2018 at 12:35)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127199715):
I already explained 100 times

#### [Kevin Buzzard (May 28 2018 at 12:35)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127199716):
Why can my brain do it?

#### [Kevin Buzzard (May 28 2018 at 12:35)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127199717):
Aren't I just a computer?

#### [Kenny Lau (May 28 2018 at 12:35)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127199718):
because your brain knows when to expand a definition and when not to

#### [Kevin Buzzard (May 28 2018 at 12:36)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127199763):
I think Lean can also decide when to expand a definition and when not to

#### [Kenny Lau (May 28 2018 at 12:36)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127199765):
how?

#### [Kevin Buzzard (May 28 2018 at 12:36)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127199768):
I don't get what I'm so good at that Lean can't do

#### [Kenny Lau (May 28 2018 at 12:36)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127199769):
with 10 definitions that is 1024 choices

#### [Kenny Lau (May 28 2018 at 12:36)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127199771):
humans are good at small things

#### [Kenny Lau (May 28 2018 at 12:36)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127199773):
humans don't have the guarantee that their algorithm works in every case

#### [Kevin Buzzard (May 28 2018 at 12:36)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127199775):
I guess here's a good analogue.

#### [Kevin Buzzard (May 28 2018 at 12:37)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127199784):
"OK so I'm quite good at go. Why don't you CS guys quickly knock up something that's as good as me at go and then I can retire"

#### [Kenny Lau (May 28 2018 at 12:37)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127199787):
a human may be able to square a small number faster than a computer (not really)

#### [Kenny Lau (May 28 2018 at 12:37)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127199789):
but as the number gets large, the computer wins by a lot

#### [Kevin Buzzard (May 28 2018 at 12:37)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127199793):
I square small numbers by lookup

#### [Kevin Buzzard (May 28 2018 at 12:37)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127199794):
they're hard wired

#### [Kenny Lau (May 28 2018 at 12:37)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127199796):
right

#### [Kevin Buzzard (May 28 2018 at 12:37)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127199799):
unlike whatever I said 5 minutes ago

#### [Kenny Lau (May 28 2018 at 12:37)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127199800):
humans are good at small things

#### [Kenny Lau (May 28 2018 at 12:37)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127199803):
`id '' U = U` is short

#### [Kevin Buzzard (May 28 2018 at 12:37)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127199806):
and true!

#### [Kenny Lau (May 28 2018 at 12:38)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127199822):
here we go again

#### [Kevin Buzzard (May 28 2018 at 12:38)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127199846):
The world just became a smaller place!

#### [Kevin Buzzard (May 28 2018 at 12:38)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127199849):
Two things became equal!

#### [Kevin Buzzard (May 28 2018 at 12:38)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127199851):
They are now the same thing, everyone please update your records

#### [Kevin Buzzard (May 28 2018 at 12:38)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127199852):
Why doesn't it work like that?

#### [Kevin Buzzard (May 28 2018 at 12:38)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127199856):
Where's the tactic that takes care of this for me?

#### [Kenny Lau (May 28 2018 at 12:38)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127199858):
you want a tactic to try to expand definitions

#### [Kevin Buzzard (May 28 2018 at 12:39)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127199862):
I have no clear idea what tactics do

#### [Kenny Lau (May 28 2018 at 12:39)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127199864):
that will work for small cases

#### [Kenny Lau (May 28 2018 at 12:39)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127199866):
that will not work for big cases

#### [Mario Carneiro (May 28 2018 at 12:39)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127199867):
In general that's undecidable

#### [Kenny Lau (May 28 2018 at 12:39)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127199868):
humans are **only** good at small things

#### [Kevin Buzzard (May 28 2018 at 12:39)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127199869):
Maybe learning tactics would help me understand my frustrations better.

#### [Andrew Ashworth (May 28 2018 at 12:39)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127199870):
```quote
Maybe learning tactics would help me understand my frustrations better.
```
yes

#### [Kevin Buzzard (May 28 2018 at 12:39)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127199871):
It's a huge hole in my Lean knowledge

#### [Kenny Lau (May 28 2018 at 12:39)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127199873):
```lean
definition image' := {y : Y | ∃ x ∈ U, f x = y}

attribute [simp] set.image_id

theorem they_are_the_same : image' (@id X) U = U := by simp [image'] -- works
theorem they_are_the_same' : id '' U = U := by simp -- works
theorem they_are_all_the_same_thing_ : id '' U = image' (@id X) U := by simp [image'] -- works
theorem but_they_are_all_the_same : set.image (@id X) U = U := by simp -- works
theorem why_are_they_all_different : id '' U = set.image (@id X) U := by simp
```

#### [Kevin Buzzard (May 28 2018 at 12:39)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127199874):
All I know is that tactic is a monoid or monad or something

#### [Kevin Buzzard (May 28 2018 at 12:40)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127199920):
`theorem they_are_the_same' : id '' U = U := by simp -- fails`

#### [Kevin Buzzard (May 28 2018 at 12:40)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127199921):
?

#### [Kevin Buzzard (May 28 2018 at 12:40)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127199923):
it works for you?

#### [Kenny Lau (May 28 2018 at 12:40)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127199924):
@**Mario Carneiro** can I get `simp` to automatically unfold certain definitions? `reducible` doesn't work

#### [Kevin Buzzard (May 28 2018 at 12:40)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127199928):
oh you CHEATED

#### [Mario Carneiro (May 28 2018 at 12:40)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127199929):
`@[simp]` can go on definitions

#### [Kevin Buzzard (May 28 2018 at 12:40)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127199931):
You gave simp a hint

#### [Mario Carneiro (May 28 2018 at 12:41)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127199934):
YES

#### [Kevin Buzzard (May 28 2018 at 12:41)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127199938):
So that hint should have been there alreadyt

#### [Kevin Buzzard (May 28 2018 at 12:41)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127199939):
already

#### [Kenny Lau (May 28 2018 at 12:41)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127199941):
thanks @**Mario Carneiro**

#### [Kevin Buzzard (May 28 2018 at 12:41)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127199942):
why isn't it a simp lemma?

#### [Kenny Lau (May 28 2018 at 12:41)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127199943):
now I can convince him:

#### [Kenny Lau (May 28 2018 at 12:41)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127199944):
```lean
@[simp] def image' := {y : Y | ∃ x ∈ U, f x = y}

attribute [simp] set.image

theorem they_are_the_same : image' (@id X) U = U := by simp -- works
theorem they_are_the_same' : id '' U = U := by simp -- works
theorem they_are_all_the_same_thing_ : id '' U = image' (@id X) U := by simp -- works
theorem but_they_are_all_the_same : set.image (@id X) U = U := by simp -- works
theorem why_are_they_all_different : id '' U = set.image (@id X) U := by simp
```

#### [Mario Carneiro (May 28 2018 at 12:41)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127199945):
like I said, you shoot me in the leg and ask me to run a marathon

#### [Mario Carneiro (May 28 2018 at 12:41)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127199947):
it should be a simp lemma, I fixed

#### [Johan Commelin (May 28 2018 at 12:41)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127199948):
```quote
why isn't it a simp lemma?
```
you mean a simp definition?

#### [Kenny Lau (May 28 2018 at 12:41)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127199949):
@**Johan Commelin** no, `set.image_id`

#### [Kenny Lau (May 28 2018 at 12:42)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127199951):
not a definition

#### [Johan Commelin (May 28 2018 at 12:42)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127199990):
Aaah, ok, true

#### [Kenny Lau (May 28 2018 at 12:42)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127199991):
now is @**Kevin Buzzard** happy?

#### [Kenny Lau (May 28 2018 at 12:42)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127199995):
after the fix I will be able to remove that line

#### [Kevin Buzzard (May 28 2018 at 12:42)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127199996):
Oh!

#### [Kenny Lau (May 28 2018 at 12:42)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127199997):
```lean
@[simp] def image' := {y : Y | ∃ x ∈ U, f x = y}

attribute [simp] set.image_id

theorem they_are_the_same : image' (@id X) U = U := by simp -- works
theorem they_are_the_same' : id '' U = U := by simp -- works
theorem they_are_all_the_same_thing_ : id '' U = image' (@id X) U := by simp -- works
theorem but_they_are_all_the_same : set.image (@id X) U = U := by simp -- works
theorem why_are_they_all_different : id '' U = set.image (@id X) U := by simp
```

#### [Kevin Buzzard (May 28 2018 at 12:43)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127199998):
You see I have *absolutely no idea* about whether this is suitable as a simp lemma.

#### [Kevin Buzzard (May 28 2018 at 12:43)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127200003):
All i know is that it passes two basic tests

#### [Kevin Buzzard (May 28 2018 at 12:43)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127200004):
(1) it's an equality

#### [Kevin Buzzard (May 28 2018 at 12:43)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127200005):
(2) the left hand side has more characters than the right hand side

#### [Mario Carneiro (May 28 2018 at 12:43)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127200007):
image_id is a good simp lemma

#### [Kevin Buzzard (May 28 2018 at 12:43)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127200009):
My entry requirements for simp are pretty low

#### [Kenny Lau (May 28 2018 at 12:43)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127200010):
so is @**Kevin Buzzard** satisfied now?

#### [Mario Carneiro (May 28 2018 at 12:43)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127200011):
most theorems of the form "my_func special_arg = value" are good simp lemmas

#### [Kevin Buzzard (May 28 2018 at 12:43)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127200013):
```quote
image_id is a good simp lemma
```
I feel I could not say that with confidence

#### [Kevin Buzzard (May 28 2018 at 12:44)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127200051):
and that's what I mean when I say that I still don't understand simp properly

#### [Mario Carneiro (May 28 2018 at 12:44)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127200058):
It takes more knowledge to set up good simp lemmas than to use simp of course

#### [Kevin Buzzard (May 28 2018 at 12:44)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127200060):
Exactly.

#### [Kevin Buzzard (May 28 2018 at 12:44)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127200061):
I want to become a power user

#### [Mario Carneiro (May 28 2018 at 12:45)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127200062):
because it's a global problem with some locality

#### [Kevin Buzzard (May 28 2018 at 12:45)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127200072):
but I don't know anywhere where random nuggets such as

#### [Kevin Buzzard (May 28 2018 at 12:45)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127200074):
```quote
most theorems of the form "my_func special_arg = value" are good simp lemmas
```

#### [Kevin Buzzard (May 28 2018 at 12:45)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127200075):
appear, other than here

#### [Mario Carneiro (May 28 2018 at 12:45)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127200080):
You could just look at the many many examples in mathlib

#### [Kevin Buzzard (May 28 2018 at 12:46)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127200120):
reading code is so *boring*

#### [Andrew Ashworth (May 28 2018 at 12:46)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127200121):
only masochistic CS graduate students get interested in software verification

#### [Kevin Buzzard (May 28 2018 at 12:46)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127200122):
that's what CS people do

#### [Andrew Ashworth (May 28 2018 at 12:46)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127200123):
your tips are folklore in CS departments

#### [Kevin Buzzard (May 28 2018 at 12:46)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127200126):
I want to talk to more CS people

#### [Andrew Ashworth (May 28 2018 at 12:46)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127200127):
and that textbook I mentioned yesterday

#### [Kevin Buzzard (May 28 2018 at 12:46)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127200128):
I need simp tips so I can be a power user

#### [Mario Carneiro (May 28 2018 at 12:46)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127200130):
term rewriting and all that?

#### [Andrew Ashworth (May 28 2018 at 12:46)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127200131):
yeah

#### [Kevin Buzzard (May 28 2018 at 12:46)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127200132):
I remember a couple of months ago it all dawning on Chris

#### [Mario Carneiro (May 28 2018 at 12:46)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127200134):
I'm willing to bet it's full of tips on setting up simp

#### [Kevin Buzzard (May 28 2018 at 12:47)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127200135):
all of a sudden every other day he was saying to me "wooah simp does much more than you'd expect"

#### [Kevin Buzzard (May 28 2018 at 12:47)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127200141):
and then I knew he'd cracked it

#### [Mario Carneiro (May 28 2018 at 12:47)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127200146):
and now you are stuck on the other end, where you think simp is magic that solves all problems

#### [Kevin Buzzard (May 28 2018 at 12:48)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127200191):
I'm still at the novice stage, behind Patrick who can remember the {something = true} stuff that you sometimes have to write at the end of simp for some reason and which you don't have to write in schoolkid

#### [Kevin Buzzard (May 28 2018 at 12:48)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127200194):
Actually, how about this for a tactic

#### [Kevin Buzzard (May 28 2018 at 12:48)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127200200):
I look through all the permutations and incantations that people have been using with simp recently

#### [Kevin Buzzard (May 28 2018 at 12:49)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127200203):
and I just write a tactic that tries all of them on my goal

#### [Kevin Buzzard (May 28 2018 at 12:49)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127200204):
and calls it schoolkid

#### [Mario Carneiro (May 28 2018 at 12:49)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127200215):
I think you could use some CS education, if only so that your suggestions come with algorithms

#### [Kevin Buzzard (May 28 2018 at 12:49)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127200216):
that way I will never have to remember what comes after the [] in simp

#### [Kevin Buzzard (May 28 2018 at 12:50)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127200280):
So I was under the misapprehension that the "your brain is just a big computer" people think that writing tactics to do what we do should be fine

#### [Kenny Lau (May 28 2018 at 12:50)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127200283):
your brain is a big computer that doesn't have to do everything correctly, just the small things

#### [Mario Carneiro (May 28 2018 at 12:51)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127200284):
That same argument says that general AI is just around the corner

#### [Kevin Buzzard (May 28 2018 at 12:51)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127200289):
I see

#### [Kevin Buzzard (May 28 2018 at 12:51)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127200294):
So is it possible to isolate "the techniques that I use to solve goals in ZFC"?

#### [Kevin Buzzard (May 28 2018 at 12:51)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127200295):
Is that the question?

#### [Kevin Buzzard (May 28 2018 at 12:51)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127200296):
Can I code this in a Lean tactic?

#### [Kenny Lau (May 28 2018 at 12:52)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127200297):
those techniques only work for small cases

#### [Kevin Buzzard (May 28 2018 at 12:52)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127200303):
Are you saying that this is hard

#### [Kenny Lau (May 28 2018 at 12:52)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127200336):
they can't be verified

#### [Andrew Ashworth (May 28 2018 at 12:52)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127200340):
can you write those techniques down as a sequence of steps in the language of Lean?

#### [Kevin Buzzard (May 28 2018 at 12:52)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127200342):
I find it so difficult to see how it can be hard when it's just checking that things are all the same

#### [Kevin Buzzard (May 28 2018 at 12:52)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127200344):
@**Andrew Ashworth** This is exactly the point.

#### [Kenny Lau (May 28 2018 at 12:52)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127200345):
@**Kevin Buzzard** the techniques include "run upon seeing a theorem with 10000 characters", which can't be one of the things a verified algorithm can do

#### [Mario Carneiro (May 28 2018 at 12:52)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127200346):
https://en.wikipedia.org/wiki/Word_problem_for_groups

#### [Kevin Buzzard (May 28 2018 at 12:52)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127200347):
When I discovered Lean I realised that it was the computer language I had been waiting for all my life

#### [Kevin Buzzard (May 28 2018 at 12:52)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127200350):
and so just thought I'd code my brain up in it

#### [Kevin Buzzard (May 28 2018 at 12:53)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127200353):
and I was just assuming it was going to be easy

#### [Kenny Lau (May 28 2018 at 12:53)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127200354):
the world is imperfect

#### [Kenny Lau (May 28 2018 at 12:53)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127200357):
computability matters

#### [Mario Carneiro (May 28 2018 at 12:53)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127200358):
just checking that things are all the same is undecidable in some simple situations

#### [Kevin Buzzard (May 28 2018 at 12:53)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127200360):
that's an engineering problem

#### [Kevin Buzzard (May 28 2018 at 12:53)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127200361):
you CS guys write great algos

#### [Kevin Buzzard (May 28 2018 at 12:53)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127200363):
I'm sure you can decide all the stuff I want decided

#### [Mario Carneiro (May 28 2018 at 12:53)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127200364):
no that's a fundamental limit on progress

#### [Kenny Lau (May 28 2018 at 12:53)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127200367):
no, you can't

#### [Kevin Buzzard (May 28 2018 at 12:54)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127200368):
because I have a *really good feeling* for the provability boundaries of ZFC

#### [Kevin Buzzard (May 28 2018 at 12:54)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127200409):
I know which questions look "weird to me" like CH

#### [Kenny Lau (May 28 2018 at 12:54)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127200410):
you don't

#### [Kevin Buzzard (May 28 2018 at 12:54)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127200411):
and which questions look sensible to me like the Langlands Programme

#### [Kenny Lau (May 28 2018 at 12:54)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127200414):
there are infinitely many independent theorem in any computable extension of ZFC

#### [Kenny Lau (May 28 2018 at 12:54)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127200416):
and there's no way any algorithm can decide whether a theorem is independent

#### [Kenny Lau (May 28 2018 at 12:54)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127200418):
including your brain

#### [Kenny Lau (May 28 2018 at 12:54)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127200423):
your brain only knows special cases like CH and AD and AC

#### [Mario Carneiro (May 28 2018 at 12:55)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127200439):
and it only knows those because it has lots of simp lemmas

#### [Andrew Ashworth (May 28 2018 at 12:55)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127200440):
hmm, I don't know if you will have long-term success with formal proofs if you don't engage with CS theory and tactic writing. because the tedious bits need to be attacked via automation, and lots of custom automation at that. Remember Bertrand Russell tried to do everything by hand and spent 5 years proving 2+2=4

#### [Andrew Ashworth (May 28 2018 at 12:55)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127200442):
and this is my own failing too, it's hard, I haven't learned Lean tactics yet

#### [Mario Carneiro (May 28 2018 at 12:56)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127200482):
I could argue that automation is not necessary for getting things done formally

#### [Mario Carneiro (May 28 2018 at 12:56)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127200484):
I have plenty of theorems in metamath as evidence

#### [Mario Carneiro (May 28 2018 at 12:57)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127200487):
but proof engineering is a really important skill

#### [Andrew Ashworth (May 28 2018 at 12:58)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127200534):
but there's also evidence from adam chlipala and john harrison that automation is kind of a big deal

#### [Andrew Ashworth (May 28 2018 at 12:59)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127200547):
well, and I don't know about math, but software definitely needs automation to discharge repetitive, yet tediously involved goals

#### [Mario Carneiro (May 28 2018 at 12:59)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127200548):
there are multiple styles of proof, and they are all effective in the right hands

#### [Andrew Ashworth (May 28 2018 at 12:59)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127200550):
and i get the feeling from Kevin's worry about schemes that advanced mathematical constructs could also use a large helping of custom automation

#### [Mario Carneiro (May 28 2018 at 12:59)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127200551):
I find that good lemmas take most of the brunt of that

#### [Mario Carneiro (May 28 2018 at 13:00)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127200599):
but I grant that working with lean encourages good automation practices

#### [Andrew Ashworth (May 28 2018 at 13:01)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127200608):
there was that whole week long discussion about transporting across equivs and I was thinking "so use `transfer` or write a tactic" bingo problem solved

#### [Kenny Lau (May 28 2018 at 13:01)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127200610):
what was the solution?

#### [Andrew Ashworth (May 28 2018 at 13:03)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127200664):
to what?

#### [Kevin Buzzard (May 28 2018 at 13:11)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127200954):
```quote
in ZFC `id '' U` isn't even defined
```
Oh what a bore, you're right

#### [Mario Carneiro (May 28 2018 at 13:12)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127201003):
metamath uses ZFC + classes to get around this

#### [Mario Carneiro (May 28 2018 at 13:13)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127201012):
it's a conservative extension, it just lets you express class equalities like this

#### [Mario Carneiro (May 28 2018 at 13:13)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127201028):
http://us.metamath.org/mpeuni/imai.html

#### [Kevin Buzzard (May 28 2018 at 13:16)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127201134):
```quote
that's stupid. What if I can't find the official image so I just make my own image which would then be identical so all the old theorems would work anyway
```
This is bad, isn't it? Doesn't it mean that every time I have a terrific new idea for a function, I have to stop what I'm doing and plough through the library to see if someone already wrote it?

#### [Kenny Lau (May 28 2018 at 13:16)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127201143):
it's called using interface to make your life better

#### [Kevin Buzzard (May 28 2018 at 13:24)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127201412):
```quote
`schoolkid_1` is `simp!`
```
Then why do I even bother using simp? Should I just be using simp! all the time? Is there any case where simp works and simp! doesn't?

#### [Kevin Buzzard (May 28 2018 at 13:26)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127201465):
```quote
@**Kevin Buzzard** I really do not see any problem at all. `id '' U` does not expand to `U`. you have to destruct the definitions and **use extensionality**
```
Yes -- you mean the definition of equal, right?

#### [Kenny Lau (May 28 2018 at 13:26)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127201474):
no, I mean the axiom of extensionality.

#### [Kevin Buzzard (May 28 2018 at 13:27)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127201493):
```quote
@**Kevin Buzzard** here's how I can formalize what I say: if you didn't have `propext` as an axiom, then you won't be able to prove that the two sets are equal, in Lean
```
But propext is in Lean! Is it a good simp lemma?

#### [Mario Carneiro (May 28 2018 at 13:27)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127201500):
no

#### [Kevin Buzzard (May 28 2018 at 13:27)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127201502):
it looks good to me

#### [Kevin Buzzard (May 28 2018 at 13:27)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127201504):
simple predicate

#### [Kevin Buzzard (May 28 2018 at 13:27)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127201505):
implies an equality

#### [Mario Carneiro (May 28 2018 at 13:28)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127201545):
it says p = q in the conclusion

#### [Kevin Buzzard (May 28 2018 at 13:28)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127201548):
it got over my simp bar

#### [Mario Carneiro (May 28 2018 at 13:28)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127201551):
that means anything equals anything

#### [Mario Carneiro (May 28 2018 at 13:28)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127201553):
it's too general

#### [Kevin Buzzard (May 28 2018 at 13:28)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127201555):
Just apply it sensibly

#### [Kevin Buzzard (May 28 2018 at 13:28)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127201556):
and stop moaning

#### [Kevin Buzzard (May 28 2018 at 13:28)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127201557):
don't just apply it randomly

#### [Kevin Buzzard (May 28 2018 at 13:28)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127201558):
:-/

#### [Kevin Buzzard (May 28 2018 at 13:28)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127201559):
This is really interesting

#### [Kevin Buzzard (May 28 2018 at 13:29)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127201576):
this is the hard bit

#### [Mario Carneiro (May 28 2018 at 13:29)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127201577):
Here's another constraint: all the variables on the RHS should appear on the LHS

#### [Kevin Buzzard (May 28 2018 at 13:29)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127201583):
You can't make all the things I know are obvious yield to one tactic because you haven't worked hard enough

#### [Mario Carneiro (May 28 2018 at 13:29)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127201584):
otherwise simp has to be creative when rewriting

#### [Kevin Buzzard (May 28 2018 at 13:29)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127201586):
So again this is somehow about can we build a tactic that beats a human at maths

#### [Kevin Buzzard (May 28 2018 at 13:30)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127201629):
Will this happen before I die? Say I live another 30 years

#### [Mario Carneiro (May 28 2018 at 13:30)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127201630):
I think you should try writing that tactic and get back to me

#### [Kevin Buzzard (May 28 2018 at 13:30)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127201635):
That's your job

#### [Kevin Buzzard (May 28 2018 at 13:30)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127201637):
you went to math classe

#### [Kevin Buzzard (May 28 2018 at 13:30)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127201638):
s

#### [Kevin Buzzard (May 28 2018 at 13:30)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127201640):
you know how we think

#### [Mario Carneiro (May 28 2018 at 13:30)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127201643):
I want you to fail at it first so you understand what you are asking

#### [Kevin Buzzard (May 28 2018 at 13:30)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127201644):
can you write a better interface?

#### [Johan Commelin (May 28 2018 at 13:30)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127201659):
Kevin, I completely agree that we need a smarter tactic. But I think that doesn't have to be `simp`. Simp is a very straightforward tool, that shouldn't try to be smart.

#### [Kevin Buzzard (May 28 2018 at 13:30)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127201667):
Yes, I need to go and play with Mizar and then some things which are conflated in my mind will become more separate

#### [Kevin Buzzard (May 28 2018 at 13:31)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127201677):
no, we should use schoolkid or whatever you wanted to call it

#### [Kevin Buzzard (May 28 2018 at 13:31)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127201678):
I think you had a more grown-up name

#### [Kenny Lau (May 28 2018 at 13:31)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127201682):
```quote
Yes, I need to go and play with Mizar and then some things which are conflated in my mind will become more separate
```
I don't see the point going to a weaker foundational system

#### [Johan Commelin (May 28 2018 at 13:31)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127201689):
```quote
I think you had a more grown-up name
```
`math_trivial`?

#### [Mario Carneiro (May 28 2018 at 13:32)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127201726):
Mizar is actually stronger axiomatically than lean

#### [Kenny Lau (May 28 2018 at 13:32)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127201733):
why?

#### [Mario Carneiro (May 28 2018 at 13:32)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127201734):
it has a proper class of inaccessibles

#### [Johan Commelin (May 28 2018 at 13:32)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127201735):
But I wouldn't mind have `kindergarten` or `schoolkid`

#### [Kenny Lau (May 28 2018 at 13:32)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127201750):
@**Kevin Buzzard** again, your issue is not in the foundational system

#### [Kenny Lau (May 28 2018 at 13:32)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127201752):
but it seems that you are deaf

#### [Andrew Ashworth (May 28 2018 at 13:33)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127201760):
it can't hurt to play around with Mizar and Isabelle

#### [Kevin Buzzard (May 28 2018 at 13:34)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127201761):
```quote
why are you proving trivial set theorems?
```
in this case it was because I was trying to understand something. But on other occasions the answer is "because I don't really know a good way of finding it in the library and it's almost certainly in a file which I haven't imported yet"

#### [Andrew Ashworth (May 28 2018 at 13:34)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127201798):
most of us here are refugees from Coq / Agda / Isabelle anyway

#### [Mario Carneiro (May 28 2018 at 13:34)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127201807):
they are organized fairly logically

#### [Mario Carneiro (May 28 2018 at 13:35)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127201810):
`set.image_id` is in the `image` section of `data.set.basic`

#### [Kevin Buzzard (May 28 2018 at 13:35)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127201820):
```quote
I don't see the point going to a weaker foundational system
```
I need to see it, in order to refine my definition of "equality in ZFC".

#### [Kevin Buzzard (May 28 2018 at 13:37)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127201903):
```quote
`set.image_id` is in the `image` section of `data.set.basic`
```
I just can't remember all this data.set.basic stuff. I just want to write set.image and hit tab a few times. This is a genuine frustration I have in my lean life

#### [Kevin Buzzard (May 28 2018 at 13:37)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127201904):
I am not capable of learning all the names of all the library files

#### [Kevin Buzzard (May 28 2018 at 13:37)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127201907):
it's init this and data that

#### [Kevin Buzzard (May 28 2018 at 13:37)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127201908):
when I want set.image_id

#### [Kevin Buzzard (May 28 2018 at 13:38)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127201947):
I type `#check set.image_id`

#### [Kevin Buzzard (May 28 2018 at 13:38)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127201948):
and it's not there

#### [Kevin Buzzard (May 28 2018 at 13:38)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127201951):
and then I have to stop what I'm doing and start faffing around with the search tool

#### [Kevin Buzzard (May 28 2018 at 13:38)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127201953):
I have no clue where anything is

#### [Kevin Buzzard (May 28 2018 at 13:38)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127201954):
they're just all theorems

#### [Kevin Buzzard (May 28 2018 at 13:38)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127201965):
Can we have a better search?

#### [Mario Carneiro (May 28 2018 at 13:38)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127201974):
I just type `import set` and the autocomplete is pretty smart about it

#### [Kevin Buzzard (May 28 2018 at 13:39)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127201988):
oh!

#### [Kevin Buzzard (May 28 2018 at 13:39)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127201994):
Because I know it's set.something I can just import set?

#### [Kevin Buzzard (May 28 2018 at 13:39)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127201996):
Does that work with everything?

#### [Mario Carneiro (May 28 2018 at 13:39)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127202000):
it's not even set.something

#### [Kevin Buzzard (May 28 2018 at 13:39)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127202001):
can I import scheme?

#### [Mario Carneiro (May 28 2018 at 13:39)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127202002):
it's data.set.basic

#### [Mario Carneiro (May 28 2018 at 13:39)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127202004):
but vscode will still give it to you

#### [Kevin Buzzard (May 28 2018 at 13:39)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127202007):
I see

#### [Kevin Buzzard (May 28 2018 at 13:40)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127202054):
I should "key on set"

#### [Kevin Buzzard (May 28 2018 at 13:45)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127202211):
```quote
there are infinitely many independent theorem in any computable extension of ZFC
```
I know but Kenny my point is that those independent theorems are just junk theorems like stupid theorems about how pi can't be a complex manifold.

#### [Kenny Lau (May 28 2018 at 13:45)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127202214):
are they

#### [Kevin Buzzard (May 28 2018 at 13:46)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127202215):
All the undecidable statements about stupid things like sets. [added later] -- that's not what ZFC is even _for_!

#### [Kevin Buzzard (May 28 2018 at 13:46)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127202255):
I am only interested in the Langlands Programme

#### [Kevin Buzzard (May 28 2018 at 13:48)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127202302):
```quote
there was that whole week long discussion about transporting across equivs and I was thinking "so use `transfer` or write a tactic" bingo problem solved
```
That's on my todo list. I'm going to write a short paper about my whole scheme experience for the ZFC people and I am going to have to get up to date as to exactly what we think is possible there

#### [Kevin Buzzard (May 28 2018 at 13:48)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127202312):
```quote
it's called using interface to make your life better
```
I need better interface search.

#### [Kevin Buzzard (May 28 2018 at 13:48)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127202315):
I thought we have google nowadays. Why isn't search easy?

#### [Kevin Buzzard (May 28 2018 at 13:49)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127202321):
Why can't I write set.image_id and something pops up saying "do you want to import data.set.basic"?

#### [Kevin Buzzard (May 28 2018 at 13:49)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127202323):
Can that be a thing one day?

#### [Sean Leather (May 28 2018 at 13:50)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127202339):
Because nobody's written the code to do it. That's usually your answer.

#### [Andrew Ashworth (May 28 2018 at 13:50)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127202392):
It could be. Maybe Lean gets tremendously popular, gets a research grant, and somebody gets hired to work on it to make it easier to use for mathematicians

#### [Kevin Buzzard (May 28 2018 at 13:50)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127202401):
```quote
Here's another constraint: all the variables on the RHS should appear on the LHS
```
Is it possible to make a flowchart -- "am I a good simp lemma?"

#### [Kevin Buzzard (May 28 2018 at 13:53)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127202484):
```quote
It could be. Maybe Lean gets tremendously popular, gets a research grant, and somebody gets hired to work on it to make it easier to use for mathematicians
```
How much does that cost in your CS world?

#### [Kevin Buzzard (May 28 2018 at 13:53)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127202487):
I could do all the costings for that other than salary

#### [Kevin Buzzard (May 28 2018 at 13:53)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127202488):
I have no idea how much you guys get paid

#### [Kevin Buzzard (May 28 2018 at 13:53)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127202490):
the administration would be able to fill in the other boxes

#### [Kevin Buzzard (May 28 2018 at 13:54)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127202537):
I'm meeting with EPSRC in two weeks

#### [Kevin Buzzard (May 28 2018 at 13:54)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127202540):
I have several hours of meetings with them and I have already pre-warned them that I will be after money to spend on computer scientists

#### [Kevin Buzzard (May 28 2018 at 13:55)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127202557):
But it would be good to get an idea of how much to pay someone to do that job

#### [Andrew Ashworth (May 28 2018 at 14:06)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127202970):
I'm not too familiar with London CS pay, my general instinct is that it ranges from 30 ~ 70 thousand pounds / year

#### [Andrew Ashworth (May 28 2018 at 14:10)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127203100):
you could wait until Lean 4. We've been promised by **Moses Schönfinkel** that he wants to take a look at theorem search in Lean after the parser and tactics framework settles down

#### [Kevin Buzzard (May 28 2018 at 14:20)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127203426):
I just wrote a theorem that was in the library

#### [Kevin Buzzard (May 28 2018 at 14:20)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127203427):
yay me

#### [Kevin Buzzard (May 28 2018 at 14:20)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127203430):
`#check topological_space.open_immersion_id `

#### [Kevin Buzzard (May 28 2018 at 14:21)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127203433):
`#check topological_space.id_open_immersion`

#### [Kevin Buzzard (May 28 2018 at 14:21)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127203436):
what should it be called?

#### [Kevin Buzzard (May 28 2018 at 14:21)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127203444):
The statement that the identity map is an open immersion

#### [Kevin Buzzard (May 28 2018 at 14:21)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127203447):
I did the other one

#### [Kevin Buzzard (May 28 2018 at 14:22)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127203495):
is there a hard and fast convention for naming that extends beyond my `mul_one` levels?

#### [Kevin Buzzard (May 28 2018 at 14:22)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127203497):
I get the feeling that there's more of an art to it

#### [Kevin Buzzard (May 28 2018 at 14:22)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127203498):
What do the artists say about this one?

#### [Patrick Massot (May 28 2018 at 14:24)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127203562):
Yeah, Kevin is back to work! I'm amazed how fast he travels those math formalization [DTT stages](https://en.wikipedia.org/wiki/K%C3%BCbler-Ross_model#Stages_of_grief) every month or so.

#### [Patrick Massot (May 28 2018 at 14:25)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127203575):
I'm much slower

#### [Kevin Buzzard (May 28 2018 at 14:36)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127203932):
I am trying to write a hard level for these CS guys

#### [Kevin Buzzard (May 28 2018 at 14:36)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127203934):
But I am stuck on something

#### [Kevin Buzzard (May 28 2018 at 14:36)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127203938):
If I have `x :
  (presheaf_of_types_pullback_under_open_immersion ((zariski.structure_presheaf_of_rings R).to_presheaf_of_types) id
     _).F
    HU
`

#### [Kevin Buzzard (May 28 2018 at 14:36)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127203939):
in my context

#### [Kevin Buzzard (May 28 2018 at 14:36)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127203941):
oh I can answer my own question

#### [Kevin Buzzard (May 28 2018 at 14:38)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127204007):
oh no I can't

#### [Kevin Buzzard (May 28 2018 at 14:38)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127204009):
Ok so there's my x

#### [Kevin Buzzard (May 28 2018 at 14:39)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127204015):
and `presheaf_of_types_pullback_under_open_immersion` just has some definition

#### [Kevin Buzzard (May 28 2018 at 14:39)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127204017):
which explictly says what its F bit is

#### [Kevin Buzzard (May 28 2018 at 14:39)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127204021):
and so probably this expands out to something with no .F in, by rfl

#### [Kevin Buzzard (May 28 2018 at 14:39)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127204022):
but how do I find out what it expands to without having to work it out myself?

#### [Kevin Buzzard (May 28 2018 at 14:40)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127204062):
I can't unfold `presheaf_of_types_pullback_under_open_immersion`

#### [Kevin Buzzard (May 28 2018 at 14:40)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127204066):
Do people need more context?

#### [Kevin Buzzard (May 28 2018 at 14:40)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127204070):
I can provide a MWE but I just wondered if I'd already said enough for someone to tell me a trick

#### [Patrick Massot (May 28 2018 at 14:41)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127204078):
Did you try `dsimp at x`?

#### [Kevin Buzzard (May 28 2018 at 14:41)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127204083):
I did

#### [Kevin Buzzard (May 28 2018 at 14:41)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127204089):
it wasn't very effective

#### [Kevin Buzzard (May 28 2018 at 14:41)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127204090):
it turned `presheaf_of_rings_pullback_under_open_immersion`

#### [Kevin Buzzard (May 28 2018 at 14:41)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127204091):
into `presheaf_of_types_pullback_under_open_immersion`

#### [Kevin Buzzard (May 28 2018 at 14:42)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127204093):
and then stopped

#### [Kevin Buzzard (May 28 2018 at 14:43)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127204146):
Actually I should do it manually and see if it is refl

#### [Patrick Massot (May 28 2018 at 14:43)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127204154):
Is it something I can git clone?

#### [Kevin Buzzard (May 28 2018 at 14:47)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127204298):
I have just done a bunch of editing to scheme.lean but not committed or pushed or anything

#### [Kevin Buzzard (May 28 2018 at 14:47)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127204299):
I'd rather just move all those edits to a different file

#### [Kevin Buzzard (May 28 2018 at 14:47)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127204303):
can git help me here?

#### [Kevin Buzzard (May 28 2018 at 14:47)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127204309):
i.e. I want to push the file I have open

#### [Kevin Buzzard (May 28 2018 at 14:47)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127204312):
but unfortunately it's an important file which I just broke

#### [Kevin Buzzard (May 28 2018 at 14:48)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127204326):
goofing around

#### [Patrick Massot (May 28 2018 at 14:48)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127204355):
you could create a broken branch

#### [Kevin Buzzard (May 28 2018 at 14:48)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127204372):
Can I do that in VS Code?

#### [Kevin Buzzard (May 28 2018 at 14:49)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127204380):
I only have master

#### [Patrick Massot (May 28 2018 at 14:49)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127204398):
`git stash`, `git checkout -b experimental`, `git stash pop`, `git commit -a`, `git push --set-upstream experimental`

#### [Kevin Buzzard (May 28 2018 at 14:49)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127204401):
I've got it

#### [Patrick Massot (May 28 2018 at 14:49)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127204403):
you can problably do it in VScode but it would be longer

#### [Kevin Buzzard (May 28 2018 at 14:50)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127204445):
Oh crap I didn't stash

#### [Kevin Buzzard (May 28 2018 at 14:50)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127204449):
is that an issue?

#### [Patrick Massot (May 28 2018 at 14:50)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127204453):
maybe not

#### [Patrick Massot (May 28 2018 at 14:50)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127204459):
it wrote that to be on the safe side

#### [Kevin Buzzard (May 28 2018 at 14:51)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127204471):
          let y := (presheaf_of_types_pullback_under_open_immersion ((zariski.structure_presheaf_of_rings R).to_presheaf_of_types) id

#### [Kevin Buzzard (May 28 2018 at 14:51)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127204473):
oops

#### [Kevin Buzzard (May 28 2018 at 14:51)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127204479):
https://github.com/kbuzzard/lean-stacks-project/blob/broken/src/scheme.lean#L495

#### [Kevin Buzzard (May 28 2018 at 14:51)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127204480):
was what I meant to say

#### [Kevin Buzzard (May 28 2018 at 14:52)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127204485):
line 495, I want to unfold that presheaf_of_types_pullback_under_open_immersion

#### [Kevin Buzzard (May 28 2018 at 14:52)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127204523):
no

#### [Kevin Buzzard (May 28 2018 at 14:52)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127204528):
I want Lean to unfold it

#### [Kevin Buzzard (May 28 2018 at 14:52)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127204532):
I'm going to try it myself to see what I'm missing

#### [Patrick Massot (May 28 2018 at 15:10)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127205165):
This is really irritating

#### [Kevin Buzzard (May 28 2018 at 15:38)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127206165):
OK I minimised

#### [Kevin Buzzard (May 28 2018 at 15:38)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127206167):
https://gist.github.com/kbuzzard/e051858b8e3348e884610ace8cd87c20

#### [Kevin Buzzard (May 28 2018 at 15:39)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127206173):
That is me setting up the theory of pre-semi-sheaves

#### [Kevin Buzzard (May 28 2018 at 15:39)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127206176):
which are a bit like distribs

#### [Kevin Buzzard (May 28 2018 at 15:39)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127206178):
and although the objects are a bit silly

#### [Kevin Buzzard (May 28 2018 at 15:39)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127206184):
I have tried to set up the theory in a sensible way

#### [Kevin Buzzard (May 28 2018 at 15:40)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127206235):
and to create Line 53 of that script I had to do some work

#### [Kevin Buzzard (May 28 2018 at 15:40)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127206236):
which I am convinced a computer could have done for me

#### [Kevin Buzzard (May 28 2018 at 15:40)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127206243):
I cut and pasted the definition of `pre_semi_sheaf_of_rings_pullback`

#### [Kevin Buzzard (May 28 2018 at 15:40)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127206245):
because I wanted to know what would happen if I unfolded it

#### [Kevin Buzzard (May 28 2018 at 15:41)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127206254):
but the problem is that the unfolding is refl

#### [Kevin Buzzard (May 28 2018 at 15:41)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127206257):
so the lemma has no name and I can't rewrite it to see what the answer is

#### [Kevin Buzzard (May 28 2018 at 15:41)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127206258):
I have to work it out myself

#### [Kevin Buzzard (May 28 2018 at 15:41)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127206265):
This is an independent question

#### [Johan Commelin (May 28 2018 at 15:45)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127206396):
(Aside: Kevin, you can tell Github that your gist is a lean file. Then you/we have syntax highlighting.)

#### [Kevin Buzzard (May 28 2018 at 15:46)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127206440):
Oh cool

#### [Kevin Buzzard (May 28 2018 at 15:46)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127206445):
but OK I have finally minimised my question

#### [Kevin Buzzard (May 28 2018 at 15:47)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127206468):
my question is this gist which I'll attempt to highlight properly

#### [Kevin Buzzard (May 28 2018 at 15:47)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127206469):
https://gist.github.com/kbuzzard/123384f9132d6db8650c3484e42bda81

#### [Kevin Buzzard (May 28 2018 at 15:48)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127206511):
That's my challenge to the CS people, I think

#### [Kevin Buzzard (May 28 2018 at 15:48)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127206515):
I'm not sure I can prove that goal

#### [Kevin Buzzard (May 28 2018 at 15:48)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127206517):
I'm not even sure that goal is true

#### [Kevin Buzzard (May 28 2018 at 15:48)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127206519):
but I think it is

#### [Kevin Buzzard (May 28 2018 at 15:48)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127206521):
for some reason it's a pain to prove though

#### [Kevin Buzzard (May 28 2018 at 15:49)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127206545):
I'm hoping the file is fairly self-explanatory

#### [Johan Commelin (May 28 2018 at 15:49)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127206550):
It is "math-true", right?

#### [Kevin Buzzard (May 28 2018 at 15:50)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127206592):
exactly Johan

#### [Kevin Buzzard (May 28 2018 at 15:50)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127206597):
Before I had something which was math-true

#### [Kevin Buzzard (May 28 2018 at 15:50)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127206600):
and Kenny and Mario kept telling me it could be done by simp

#### [Kevin Buzzard (May 28 2018 at 15:50)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127206603):
I would like them to tell me how to do this one

#### [Johan Commelin (May 28 2018 at 15:52)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127206673):
Are the rings essential to the problem?

#### [Johan Commelin (May 28 2018 at 15:53)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127206679):
Or could you just use semi-quasi-demi-pre-sheaves of types?

#### [Kevin Buzzard (May 28 2018 at 15:58)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127206859):
No it's crucial they're rings

#### [Kevin Buzzard (May 28 2018 at 15:58)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127206863):
because it's a trivial way to make it even harder

#### [Kevin Buzzard (May 28 2018 at 15:59)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127206876):
this is a content-free statement from where I'm standing

#### [Kevin Buzzard (May 28 2018 at 15:59)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127206880):
and if there aren't algorithms which currently prove content-free statements like this

#### [Kevin Buzzard (May 28 2018 at 15:59)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127206883):
then I think that mathematicians will find it hard to learn Lean

#### [Kevin Buzzard (May 28 2018 at 15:59)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127206885):
@**Kenny Lau** @**Mario Carneiro** Can you fill in my sorry?

#### [Kevin Buzzard (May 28 2018 at 15:59)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127206888):
Am I missing something easy?

#### [Patrick Massot (May 28 2018 at 16:00)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127206939):
Oh, he went back a couple of stages

#### [Kevin Buzzard (May 28 2018 at 16:00)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127206941):
I removed topology

#### [Kevin Buzzard (May 28 2018 at 16:00)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127206944):
and open immersions

#### [Kenny Lau (May 28 2018 at 16:00)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127206945):
```quote
Am I missing something easy?
```
no

#### [Kevin Buzzard (May 28 2018 at 16:00)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127206948):
crap

#### [Kevin Buzzard (May 28 2018 at 16:00)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127206950):
is that a provable but hard goal?

#### [Kenny Lau (May 28 2018 at 16:00)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127206953):
well not really hard

#### [Kenny Lau (May 28 2018 at 16:00)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127206954):
i could do it

#### [Kenny Lau (May 28 2018 at 16:00)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127206957):
but not exactly easy

#### [Kevin Buzzard (May 28 2018 at 16:01)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127206958):
Teach me how to do it

#### [Kevin Buzzard (May 28 2018 at 16:01)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127206962):
I can't do it

#### [Kevin Buzzard (May 28 2018 at 16:01)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127206963):
and it's obvious

#### [Kevin Buzzard (May 28 2018 at 16:01)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127206968):
and these are my least favourite things in Lean

#### [Kevin Buzzard (May 28 2018 at 16:01)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127206970):
teach me how to kill this pokemon

#### [Johan Commelin (May 28 2018 at 16:01)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127206971):
@**Kevin Buzzard** you don't only want `schoolkid` tactic, you also want `kenny_lau` and `mario_carneiro`

#### [Kevin Buzzard (May 28 2018 at 16:01)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127206972):
exactly

#### [Kevin Buzzard (May 28 2018 at 16:01)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127206974):
Kenny

#### [Kevin Buzzard (May 28 2018 at 16:01)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127206975):
I'm up to here

#### [Kevin Buzzard (May 28 2018 at 16:01)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127206977):
```lean
theorem pre_semi_sheaves_iso (X : Type) (F : pre_semi_sheaf_of_rings X) : 
are_isomorphic_pre_semi_sheaves_of_rings
    (pre_semi_sheaf_of_rings_pullback F id) F
:= 
begin
  constructor,
  { constructor,tactic.swap,
    { constructor,tactic.swap,
      { intros U s,
        unfold pre_semi_sheaf_of_rings_pullback,
        suffices : F.F (id '' U), by simpa using this,
        have reluctant_to_use : id '' U = U := by rw set.image_id,
        rw reluctant_to_use,
        exact s,
      },
      intro U,
      simp,
      sorry
    },
    sorry,
  },
  sorry,
end 

```

#### [Kenny Lau (May 28 2018 at 16:02)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127207029):
I'm trying

#### [Kevin Buzzard (May 28 2018 at 16:02)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127207030):
Thanks

#### [Kevin Buzzard (May 28 2018 at 16:03)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127207039):
Are you writing a tactic?

#### [Kevin Buzzard (May 28 2018 at 16:03)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127207041):
Don't try to solve the goal

#### [Kenny Lau (May 28 2018 at 16:03)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127207042):
no

#### [Kevin Buzzard (May 28 2018 at 16:03)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127207043):
try to write a tactic which solves the goal

#### [Kenny Lau (May 28 2018 at 16:03)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127207045):
I don't know how to write tactics

#### [Kevin Buzzard (May 28 2018 at 16:03)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127207046):
because this goal is solved by math_trivial

#### [Kevin Buzzard (May 28 2018 at 16:04)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127207095):
This goal is the nightmare which I could avoid in my case of presheaves

#### [Kevin Buzzard (May 28 2018 at 16:04)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127207098):
but a pre_semi_sheaf does not have res

#### [Kevin Buzzard (May 28 2018 at 16:04)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127207100):
so you have to bite the bullet

#### [Kevin Buzzard (May 28 2018 at 16:05)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127207109):
@**Simon Hudon** Can you solve my goal with a tactic?

#### [Kevin Buzzard (May 28 2018 at 16:05)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127207122):
https://gist.github.com/kbuzzard/123384f9132d6db8650c3484e42bda81

#### [Kevin Buzzard (May 28 2018 at 16:05)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127207124):
Last line

#### [Kevin Buzzard (May 28 2018 at 16:05)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127207128):
the pre_semi_sheaves are isomorphic via the identity map

#### [Kevin Buzzard (May 28 2018 at 16:05)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127207134):
but checking the details is apparently a little tricky

#### [Kevin Buzzard (May 28 2018 at 16:06)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127207138):
Would I have exactly the same problems in Mizar?

#### [Kevin Buzzard (May 28 2018 at 16:06)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127207186):
@**Assia Mahboubi** Would my goal be any easier to solve in Coq?

#### [Kevin Buzzard (May 28 2018 at 16:07)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127207194):
I have isolated a frustration I have with dependent type theory

#### [Kevin Buzzard (May 28 2018 at 16:07)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127207202):
I need to define a map from `F U` to `F (id '' U)`

#### [Kevin Buzzard (May 28 2018 at 16:07)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127207205):
where `id '' U` is the image of the set U under the identity map

#### [Kevin Buzzard (May 28 2018 at 16:08)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127207244):
I define the map by rewriting `id '' U = U` and then using the identity

#### [Kevin Buzzard (May 28 2018 at 16:08)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127207245):
and I never recover

#### [Kevin Buzzard (May 28 2018 at 16:08)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127207253):
But I don't know any other way of doing it

#### [Kevin Buzzard (May 28 2018 at 16:10)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127207319):
Is there some sort of reason why I should not be proving this goal at all?

#### [Simon Hudon (May 28 2018 at 16:14)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127207481):
How would you prove it without tactics?

#### [Kenny Lau (May 28 2018 at 16:15)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127207490):
he can't function without tactics

#### [Kenny Lau (May 28 2018 at 16:15)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127207496):
you would do `eq.drec` without tactics

#### [Simon Hudon (May 28 2018 at 16:24)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127207893):
I mean, I don't know any of the context so I'm not sure how the definitions relate to each other

#### [Assia Mahboubi (May 28 2018 at 17:06)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127209693):
@**Kevin Buzzard** It will take me some time to catch up, the thread is long. Why did you use this equality at all? Aren't ``F U`` and ``F (id '' U)`` the exact same thing (aka convertible?). How can I play your formalization?

#### [Kenny Lau (May 28 2018 at 17:07)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127209705):
https://gist.github.com/kbuzzard/123384f9132d6db8650c3484e42bda81

#### [Kenny Lau (May 28 2018 at 17:07)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127209710):
@**Assia Mahboubi** just prove the above

#### [Kenny Lau (May 28 2018 at 17:09)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127209792):
@**Kevin Buzzard** you know what, I take back my word, it's harder than I thought

#### [Assia Mahboubi (May 28 2018 at 17:09)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127209810):
Hi @**Kenny Lau** ! Thanks! But I am more ignorant than you think : I meant, what install instructions should I follow. I am not a regular Lean user.

#### [Kenny Lau (May 28 2018 at 17:10)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127209855):
oh, sorry

#### [Kenny Lau (May 28 2018 at 17:10)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127209865):
I think you can try it online

#### [Kenny Lau (May 28 2018 at 17:11)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127209872):
https://leanprover.github.io/live/latest/

#### [Assia Mahboubi (May 28 2018 at 17:11)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127209873):
Ok thanks, I am doing that now.

#### [Kevin Buzzard (May 28 2018 at 17:13)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127209968):
Does one run into the same issues in Coq?

#### [Kevin Buzzard (May 28 2018 at 17:13)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127209974):
Does one run into the same issues in Mizar?

#### [Kevin Buzzard (May 28 2018 at 17:14)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127210018):
Which systems is this easy in?

#### [Kevin Buzzard (May 28 2018 at 17:14)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127210029):
@**Assia Mahboubi** I suspect you can see what I'm trying to do

#### [Kevin Buzzard (May 28 2018 at 17:15)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127210064):
I'm happy to let a lean expert like Mario or Kenny solve the lean one

#### [Kevin Buzzard (May 28 2018 at 17:15)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127210072):
I am trying to understand to what extent my worldview of mathematics is naive

#### [Kenny Lau (May 28 2018 at 17:15)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127210074):
lol it's been an hour already

#### [Kevin Buzzard (May 28 2018 at 17:16)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127210131):
The challenge was embedded well in a very long thread and I would imagine many have stopped reading

#### [Kevin Buzzard (May 28 2018 at 17:17)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127210149):
One could ask in a new thread, I think this question is sufficiently interesting

#### [Kevin Buzzard (May 28 2018 at 17:18)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127210215):
I am hoping that someone will come up with a curve ball solution of the form "don't prove that, prove something that implies that

#### [Kenny Lau (May 28 2018 at 17:19)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127210220):
I tried to build up an interface

#### [Kenny Lau (May 28 2018 at 17:19)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127210221):
didn't work

#### [Assia Mahboubi (May 28 2018 at 17:21)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127210326):
Thanks @**Kenny Lau**, it works like a charm. But unfortunately I will have to leave now (and I have not finished to read the problem :disappointed: ).  I will definitely look again later.

#### [Kenny Lau (May 28 2018 at 17:21)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127210332):
see you

#### [Kevin Buzzard (May 28 2018 at 17:28)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127210576):
@**Kenny Lau**

#### [Kevin Buzzard (May 28 2018 at 17:28)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127210577):
I had an idea

#### [Kevin Buzzard (May 28 2018 at 17:28)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127210579):
but you would be quicker to implement it than me

#### [Kenny Lau (May 28 2018 at 17:28)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127210581):
what is it

#### [Kevin Buzzard (May 28 2018 at 17:28)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127210583):
and I have to tidy the kitchen anyway

#### [Kevin Buzzard (May 28 2018 at 17:28)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127210585):
I claim that my definition is incomplete

#### [Kevin Buzzard (May 28 2018 at 17:28)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127210586):
as far as Lean is concerned

#### [Kevin Buzzard (May 28 2018 at 17:29)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127210587):
I am missing some extra structure

#### [Kevin Buzzard (May 28 2018 at 17:29)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127210591):
which can be filled in easily

#### [Kevin Buzzard (May 28 2018 at 17:29)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127210600):
Is the "correct" object a pre_semi_sheaf whatever, but also equipped with maps res : F U -> F V whenever U = V

#### [Kevin Buzzard (May 28 2018 at 17:29)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127210603):
plus axiom that res U U = id

#### [Kevin Buzzard (May 28 2018 at 17:29)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127210604):
plus axiom of composition

#### [Kevin Buzzard (May 28 2018 at 17:30)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127210649):
res U V then res V W is res U W

#### [Kevin Buzzard (May 28 2018 at 17:30)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127210654):
Given my stupid annoying structure

#### [Kevin Buzzard (May 28 2018 at 17:30)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127210655):
can it be beefed up to such a structure

#### [Kevin Buzzard (May 28 2018 at 17:30)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127210657):
and for this beefed-up structure

#### [Kevin Buzzard (May 28 2018 at 17:30)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127210659):
can the map be defined to be res

#### [Kevin Buzzard (May 28 2018 at 17:30)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127210673):
and then we deduce the result for the stupid structure

#### [Kevin Buzzard (May 28 2018 at 17:31)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127210679):
My experience with schemes tells me

#### [Kevin Buzzard (May 28 2018 at 17:31)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127210680):
that when the map is res

#### [Kevin Buzzard (May 28 2018 at 17:31)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127210684):
all the hard proofs become rfl

#### [Kevin Buzzard (May 28 2018 at 17:31)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127210688):
maybe not the ring one

#### [Kevin Buzzard (May 28 2018 at 17:31)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127210690):
the ring one we have to use some equiv tactic thing

#### [Reid Barton (May 28 2018 at 20:17)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127216106):
@**Kevin Buzzard** 
```lean
definition pre_semi_sheaf_of_rings_pullback_setmap
  {α : Type}
  {β : Type}
  (PR : pre_semi_sheaf_of_rings β)
  (f : set α → set β)
  : pre_semi_sheaf_of_rings α :=
{ F := λ V,PR.F (f V)
}

theorem pre_semi_sheaves_iso_setmap (X : Type) (F : pre_semi_sheaf_of_rings X) :
are_isomorphic_pre_semi_sheaves_of_rings
    (pre_semi_sheaf_of_rings_pullback_setmap F id) F :=
⟨⟨λ (U : set X), id, by apply_instance⟩,
 ⟨λ (U : set X), id, by apply_instance⟩,
 λ _, rfl, λ _, rfl⟩

definition pre_semi_sheaf_of_rings_pullback
  {α : Type}
  {β : Type}
  (PR : pre_semi_sheaf_of_rings β)
  (f : α → β)
  : pre_semi_sheaf_of_rings α :=
{ F := λ V,PR.F (f '' V)
}

theorem pre_semi_sheaves_iso (X : Type) (F : pre_semi_sheaf_of_rings X) :
are_isomorphic_pre_semi_sheaves_of_rings
    (pre_semi_sheaf_of_rings_pullback F id) F
:= begin
  convert pre_semi_sheaves_iso_setmap X F,
  change pre_semi_sheaf_of_rings_pullback_setmap F (λ U, id '' U) = _,
  congr, funext U, simp [set.image_id]
end
```

#### [Kevin Buzzard (May 28 2018 at 20:18)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127216158):
I was hoping you'd show up

#### [Kevin Buzzard (May 28 2018 at 20:18)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127216160):
I thought you'd like this one

#### [Kevin Buzzard (May 28 2018 at 20:19)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127216179):
I am cooking, will look later. Did you do it?

#### [Reid Barton (May 28 2018 at 20:19)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127216188):
Yes

#### [Kevin Buzzard (May 28 2018 at 20:19)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127216190):
Convert? What does that do?

#### [Reid Barton (May 28 2018 at 20:20)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127216241):
I split your construction into two pieces: pullback of a presheaf by a functor between sites and the functor between sites induced by a map of spaces

#### [Reid Barton (May 28 2018 at 20:20)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127216251):
`convert` basically says "this is the term I want to be the proof, aside from some fiddling about the type not being definitionally equal to the desired one"

#### [Reid Barton (May 28 2018 at 20:21)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127216267):
so it generates a new goal which is that the type of the term you provided is the same as the goal type

#### [Mario Carneiro (May 28 2018 at 21:56)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127219336):
> https://leanprover.zulipchat.com/#narrow/stream/116395-maths/subject/ZFC.20equality/near/127204479

Here's how you can use `cast` as a morphism without any `res` trickery:
```

def pre_semi_sheaf_of_rings.cast {α} (FPT : pre_semi_sheaf_of_rings α)
  {U V : set α} (e : U = V) : FPT.F U → FPT.F V :=
cast (congr_arg _ e)

instance pre_semi_sheaf_of_rings.cast.is_ring_hom
  {α} (FPT : pre_semi_sheaf_of_rings α) {U V : set α} (e : U = V) :
  is_ring_hom (FPT.cast e) :=
by subst e; exact is_ring_hom.id

theorem pre_semi_sheaf_of_rings.cast_comp
  {α} (FPT : pre_semi_sheaf_of_rings α) {U V W : set α}
  (e₁ : U = V) (e₂ : V = W) (a) :
  FPT.cast e₂ (FPT.cast e₁ a) = FPT.cast (e₁.trans e₂) a :=
by substs e₂ e₁; exact rfl

theorem presheaves_iso (X : Type) (F : pre_semi_sheaf_of_rings X) : 
are_isomorphic_pre_semi_sheaves_of_rings
    (pre_semi_sheaf_of_rings_pullback F id) F :=
begin 
  refine ⟨⟨λ U, F.cast (by simp), by apply_instance⟩,
     ⟨λ U, F.cast (by simp), by apply_instance⟩, _, _⟩;
  { intros U, funext a,
    dsimp [is_identity_morphism_of_pre_semi_sheaves_of_rings,
      composition_of_morphisms_of_pre_semi_sheaves_of_rings],
    rw F.cast_comp, refl }
end 
```

#### [Patrick Massot (May 29 2018 at 10:51)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127241361):
```quote
I think you can try it online
```
I think it's a bad idea to tell people to use the online version. Maybe it's my computer fault, but I find it too slow to be usable. I think it's very bad advertisement. So let me try something new: https://www.math.u-psud.fr/~pmassot/en/misc/index.html @**Assia Mahboubi** I guess you have a Debian/Ubuntu computer at hand. Could you try using my installation script? It's meant to be a single step, one minute fully setup Lean install  (this obviously includes a compiled mathlib).

#### [Johan Commelin (May 29 2018 at 10:54)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127241525):
Does `https://www.math.u-psud.fr/~pmassot/files/lean/install_lean.sh` contain precompiled mathlib nightlies?

#### [Patrick Massot (May 29 2018 at 10:55)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127241534):
yes

#### [Johan Commelin (May 29 2018 at 10:55)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127241549):
Nice! I guess in this file, right? `https://www.math.u-psud.fr/~pmassot/files/lean/.lean.tar.gz`

#### [Patrick Massot (May 29 2018 at 10:55)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127241555):
yes

#### [Johan Commelin (May 29 2018 at 10:55)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127241560):
Ok, you should change the topic of your anouncement. This deserves more PR.

#### [Patrick Massot (May 29 2018 at 10:57)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127241637):
I think this deserves to be taken up by Mario and Johannes. Right now, I set up an emergency solution. I don't want Assia to go away because Javascript was never meant to run proof assistants

#### [Patrick Massot (May 29 2018 at 10:58)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127241710):
But now I need to stop. This was meant to be a no Lean day. I'll go to my IHES office where I can't install anything on the computer (and nothing Lean related is pre-installed) and get some real work done

#### [Patrick Massot (May 29 2018 at 10:59)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127241720):
Have fun!

#### [Assia Mahboubi (May 29 2018 at 10:59)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127241724):
Hi @**Patrick Massot** . Yes, it was very slow and I eventually gave up. I was planning to (re)install Lean on my machine today. What is your script doing? Will it be easy for me to update my Lean later? My plan is to look at @**Kevin Buzzard** 's stack project and he says [here](https://github.com/kbuzzard/lean-stacks-project) that I need a version from nightly of 2018-04-06. Does it matter? And yes, I have Debian/Ubuntu OS.

#### [Patrick Massot (May 29 2018 at 11:00)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127241791):
It does what it says in https://www.math.u-psud.fr/~pmassot/files/lean/install_lean.sh

#### [Patrick Massot (May 29 2018 at 11:01)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127241810):
install VScode using MS debian package, manually install the Lean extension, download Lean 3.4.1 and set the bash path variable, download precompiled mathlib

#### [Patrick Massot (May 29 2018 at 11:01)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127241834):
Let me check you can run Kevin's code using this version of mathlib

#### [Johan Commelin (May 29 2018 at 11:01)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127241835):
[sorry, wrong topic]

#### [Assia Mahboubi (May 29 2018 at 11:06)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127242075):
@**Patrick Massot** Thanks for the answer to my silly question: I should have open the file first. It looks great. I'll wait from a confirmation (from you or from anyone else) and try (I guess that otherwise it's just a matter of changing a couple of lines in your script). Happy no-Lean day.

#### [Johan Commelin (May 29 2018 at 11:08)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127242147):
@**Assia Mahboubi** It will be super easy to update Lean later.

#### [Johan Commelin (May 29 2018 at 11:08)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127242154):
Patrick's script just puts together the steps that you would otherwise perform manually.

#### [Johan Commelin (May 29 2018 at 11:09)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127242162):
And he has compiled mathlib for you. Which saves you an hour of coffee breaks :wink:

#### [Assia Mahboubi (May 29 2018 at 11:09)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127242169):
Hi @**Johan Commelin** , thanks for the help. I am trying it now.

#### [Patrick Massot (May 29 2018 at 11:14)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127242352):
It seems you still need to manually copy mathlib to the stacks directory. Maybe I shouldn't have skipped using Sbeastian's elan. So, after running my script, the next steps are: `git clone https://github.com/kbuzzard/lean-stacks-project.git` then `cp -r ~/.lean/_target/ lean-stacks-project` then `cd lean-stacks-project`, `lean --make`

#### [Patrick Massot (May 29 2018 at 11:14)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127242357):
There will probably be some errors because this repo is still a messy playground

#### [Patrick Massot (May 29 2018 at 11:21)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127242554):
Ok, I confirm I'm able to do that and then open the lean-stacvks-project folder in VScode and open scheme.lean without error. Assia: the first command to learn after opening a Lean file in VScode (and putting the cursor anywhere in that file) is Ctrl-shift-return which opens the Lean message window where all the interesting communication with lean takes place

#### [Patrick Massot (May 29 2018 at 11:22)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127242565):
Now I'll really go to IHES where I'll probably open Zulip anyway, but not VScode

#### [Assia Mahboubi (May 29 2018 at 11:27)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127242718):
Thanks again! Meanwhile I tried the instruction provided in the README.md (using ``leanpkg``) and it is now indeed building stuff. If it goes wrong I''fall back to your suggestion.

#### [Assia Mahboubi (May 29 2018 at 11:32)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127242887):
It's very long (and warms my office) : it seems that a mathlib has been copied and is being re-compiled in a ``_target/dep`` sub-directory...

#### [Johan Commelin (May 29 2018 at 11:35)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127242954):
Yes, we know that feeling... (-;

#### [Johan Commelin (May 29 2018 at 11:35)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127242957):
I wasn't joking when I told you about the "hour of coffee breaks"

#### [Patrick Massot (May 29 2018 at 11:37)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127243006):
This is exactly what I tried to avoid

#### [Patrick Massot (May 29 2018 at 11:37)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127243011):
My instructions should bypass mathlib compilation

#### [Patrick Massot (May 29 2018 at 11:39)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/ZFC%20equality/near/127243059):
(I'm waiting for my train)

