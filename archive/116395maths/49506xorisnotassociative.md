---
layout: page
title: Lean Prover Zulip Chat Archive 
permalink: archive/116395maths/49506xorisnotassociative.html
---

## [maths](index.html)
### [xor is not associative](49506xorisnotassociative.html)

#### [Kenny Lau (Apr 18 2018 at 17:27)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/xor%20is%20not%20associative/near/125256439):
Could someone prove that xor is not associative constructively, perhaps by constructing a Kripke model where this fails?

#### [Kenny Lau (Apr 18 2018 at 17:27)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/xor%20is%20not%20associative/near/125256453):
here `xor` is defined as Lean defines it: `p xor q := (p and not q) or (not p and q)`

#### [Kenny Lau (Apr 18 2018 at 17:28)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/xor%20is%20not%20associative/near/125256507):
or maybe show that `xor` is associative implies LEM

#### [Kevin Buzzard (Apr 18 2018 at 17:32)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/xor%20is%20not%20associative/near/125256694):
if you defined `xor'` as `(p or q) and (not p or not q)` then can you constructively prove that this is the same as `xor`?

#### [Kevin Buzzard (Apr 18 2018 at 17:32)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/xor%20is%20not%20associative/near/125256703):
I can't believe I'm thinking about such nonsense

#### [Kenny Lau (Apr 18 2018 at 17:33)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/xor%20is%20not%20associative/near/125256719):
let's say you can. and then?

#### [Kenny Lau (Apr 18 2018 at 17:34)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/xor%20is%20not%20associative/near/125256762):
I've convinced myself that you can

#### [Kevin Buzzard (Apr 18 2018 at 17:35)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/xor%20is%20not%20associative/near/125256781):
I guess distributivity is all fine constructively

#### [Patrick Massot (Apr 18 2018 at 17:35)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/xor%20is%20not%20associative/near/125256783):
```quote
I can't believe I'm thinking about such nonsense
```
Kevin, I'm very disappointed

#### [Kevin Buzzard (Apr 18 2018 at 17:35)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/xor%20is%20not%20associative/near/125256787):
I'm trying to finish this affine scheme thing and he keeps pestering me!

#### [Patrick Massot (Apr 18 2018 at 17:36)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/xor%20is%20not%20associative/near/125256846):
He should work on mechanics each time he is tempted by constructivist non-sense

#### [Patrick Massot (Apr 18 2018 at 17:36)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/xor%20is%20not%20associative/near/125256848):
mechanics is super constructive

#### [Kenny Lau (Apr 18 2018 at 17:36)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/xor%20is%20not%20associative/near/125256851):
you bunch are horrible people

#### [Kevin Buzzard (Apr 18 2018 at 17:36)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/xor%20is%20not%20associative/near/125256852):
with spanners and everything

#### [Patrick Massot (Apr 18 2018 at 17:39)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/xor%20is%20not%20associative/near/125256971):
```quote
you bunch are horrible people
```
We are working on saving your soul

#### [Kenny Lau (Apr 18 2018 at 17:39)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/xor%20is%20not%20associative/near/125256975):
:(

#### [Kevin Buzzard (Apr 18 2018 at 17:40)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/xor%20is%20not%20associative/near/125257018):
Kenny, the only technique I know for this sort of thing is to imagine Prop is some topological space

#### [Kenny Lau (Apr 18 2018 at 17:40)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/xor%20is%20not%20associative/near/125257032):
that's one interpretation

#### [Kevin Buzzard (Apr 18 2018 at 17:40)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/xor%20is%20not%20associative/near/125257034):
and then there's something with open sets

#### [Kenny Lau (Apr 18 2018 at 17:40)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/xor%20is%20not%20associative/near/125257036):
but I like Kripke model more

#### [Patrick Massot (Apr 18 2018 at 17:40)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/xor%20is%20not%20associative/near/125257042):
Imagining Prop is a topological space saves souls??

#### [Kenny Lau (Apr 18 2018 at 17:40)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/xor%20is%20not%20associative/near/125257043):
since it's morally what's going on behind constructivism

#### [Kevin Buzzard (Apr 18 2018 at 17:40)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/xor%20is%20not%20associative/near/125257044):
where not p is something like the interior of the complement of p

#### [Kenny Lau (Apr 18 2018 at 17:40)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/xor%20is%20not%20associative/near/125257048):
@**Patrick Massot** he's unsaving me

#### [Kevin Buzzard (Apr 18 2018 at 17:41)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/xor%20is%20not%20associative/near/125257062):
All I'm saying is that the one time in my life when I thought about this was a few months ago, when I proved that not not p implies p was not provable constructively

#### [Kevin Buzzard (Apr 18 2018 at 17:41)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/xor%20is%20not%20associative/near/125257070):
by making some trivial observation about topological spaces

#### [Kenny Lau (Apr 18 2018 at 17:41)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/xor%20is%20not%20associative/near/125257074):
right, but the connection is not trivial at all :-)

#### [Kevin Buzzard (Apr 18 2018 at 17:41)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/xor%20is%20not%20associative/near/125257075):
having just read some Wikipedia article about this sort of thing

#### [Patrick Massot (Apr 18 2018 at 17:41)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/xor%20is%20not%20associative/near/125257083):
soon they will be using toposes...

#### [Kevin Buzzard (Apr 18 2018 at 17:41)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/xor%20is%20not%20associative/near/125257087):
and it seems to me that your question might yield to the same strategy

#### [Mario Carneiro (Apr 18 2018 at 20:24)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/xor%20is%20not%20associative/near/125264808):
here is a simpler problem: if not (p xor q), is p decidable?

#### [Mario Carneiro (Apr 18 2018 at 20:30)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/xor%20is%20not%20associative/near/125265116):
ah, of course not: if p <-> q then not (p xor q) but then p may be some arbitrary nondecidable proposition

#### [Kenny Lau (Apr 18 2018 at 20:40)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/xor%20is%20not%20associative/near/125265606):
use non-well-founded recursion to prove that p is decidable :P @**Mario Carneiro**

#### [Kenny Lau (Apr 18 2018 at 20:40)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/xor%20is%20not%20associative/near/125265608):
using p <-> q

#### [Gabriel Ebner (Apr 18 2018 at 20:50)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/xor%20is%20not%20associative/near/125266047):
Maybe a better problem: if `xor p q`, is `p` decidable?

#### [Gabriel Ebner (Apr 18 2018 at 20:50)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/xor%20is%20not%20associative/near/125266061):
BTW, this is a nice puzzle!  Thanks, @**Kenny Lau**

#### [Kenny Lau (Apr 18 2018 at 20:50)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/xor%20is%20not%20associative/near/125266065):
no problem

#### [Kenny Lau (Apr 18 2018 at 20:51)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/xor%20is%20not%20associative/near/125266078):
here's what inspired me

#### [Kenny Lau (Apr 18 2018 at 20:51)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/xor%20is%20not%20associative/near/125266084):
I wanted to prove that Prop is a group under xor

#### [Kenny Lau (Apr 18 2018 at 20:51)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/xor%20is%20not%20associative/near/125266088):
but if this is possible, then it would imply double negation elimination

#### [Kenny Lau (Apr 18 2018 at 20:51)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/xor%20is%20not%20associative/near/125266089):
so one of the group axioms must go wrong

#### [Kenny Lau (Apr 18 2018 at 20:51)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/xor%20is%20not%20associative/near/125266091):
who can possibly know that it is the associativity

#### [Kenny Lau (Apr 18 2018 at 20:51)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/xor%20is%20not%20associative/near/125266093):
(well I eliminated the other trivial axioms though)

#### [Kenny Lau (Apr 18 2018 at 20:52)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/xor%20is%20not%20associative/near/125266148):
```quote
Maybe a better problem: if `xor p q`, is `p` decidable?
```
technically, even `p or not p` doesn't mean `p` is decidable

#### [Kevin Buzzard (Apr 18 2018 at 20:53)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/xor%20is%20not%20associative/near/125266159):
Kenny did you try the topological space approach?

#### [Gabriel Ebner (Apr 18 2018 at 20:53)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/xor%20is%20not%20associative/near/125266173):
Ah, you're right of course.

#### [Kenny Lau (Apr 18 2018 at 20:54)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/xor%20is%20not%20associative/near/125266216):
```quote
Kenny did you try the topological space approach?
```
I'm busy getting free group to work

#### [Kevin Buzzard (Apr 18 2018 at 20:54)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/xor%20is%20not%20associative/near/125266225):
You need to check p xor not p is provable :-)

#### [Kevin Buzzard (Apr 18 2018 at 20:55)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/xor%20is%20not%20associative/near/125266232):
OK let me just spend a few minutes doing the top space thing in case it clarifies anything

#### [Kevin Buzzard (Apr 18 2018 at 20:55)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/xor%20is%20not%20associative/near/125266237):
I don't remember the details

#### [Kevin Buzzard (Apr 18 2018 at 20:55)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/xor%20is%20not%20associative/near/125266244):
but is the idea somehow that we can think of a prop as being an open set in a topological space

#### [Kenny Lau (Apr 18 2018 at 20:55)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/xor%20is%20not%20associative/near/125266248):
right

#### [Kenny Lau (Apr 18 2018 at 20:55)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/xor%20is%20not%20associative/near/125266250):
not = exterior, or = union, and = intersection

#### [Kevin Buzzard (Apr 18 2018 at 20:55)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/xor%20is%20not%20associative/near/125266254):
not is what?

#### [Kenny Lau (Apr 18 2018 at 20:55)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/xor%20is%20not%20associative/near/125266255):
exterior

#### [Kevin Buzzard (Apr 18 2018 at 20:55)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/xor%20is%20not%20associative/near/125266256):
Do I take the interior of the complement?

#### [Kenny Lau (Apr 18 2018 at 20:56)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/xor%20is%20not%20associative/near/125266294):
right

#### [Kevin Buzzard (Apr 18 2018 at 20:56)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/xor%20is%20not%20associative/near/125266296):
Is that what exterior means? I've never heard that

#### [Kenny Lau (Apr 18 2018 at 20:56)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/xor%20is%20not%20associative/near/125266300):
yes

#### [Kenny Lau (Apr 18 2018 at 20:56)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/xor%20is%20not%20associative/near/125266303):
interior + boundary + exterior = whole space

#### [Kenny Lau (Apr 18 2018 at 20:56)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/xor%20is%20not%20associative/near/125266305):
interior + boundary = closure

#### [Kevin Buzzard (Apr 18 2018 at 20:56)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/xor%20is%20not%20associative/near/125266306):
So are we 100 percent fixed on definition of xor?

#### [Kenny Lau (Apr 18 2018 at 20:56)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/xor%20is%20not%20associative/near/125266309):
what is xor here?

#### [Kenny Lau (Apr 18 2018 at 20:56)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/xor%20is%20not%20associative/near/125266313):
oh right, we already have everything

#### [Kenny Lau (Apr 18 2018 at 20:56)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/xor%20is%20not%20associative/near/125266316):
yes then

#### [Mario Carneiro (Apr 18 2018 at 20:56)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/xor%20is%20not%20associative/near/125266318):
so here is a proof of LEM from xor assoc:
```
example (h : ∀ p q r, xor p (xor q r) ↔ xor (xor p q) r) {p} : p ∨ ¬ p :=
have ¬ xor p p, from λ h, h.elim (λ ⟨hp, np⟩, np hp) (λ ⟨hp, np⟩, np hp),
have xor p (xor p true), from (h p p true).2 (or.inr ⟨trivial, this⟩),
this.imp and.left and.right
```

#### [Kevin Buzzard (Apr 18 2018 at 20:57)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/xor%20is%20not%20associative/near/125266332):
great, Mario just saved me a job :-)

#### [Kenny Lau (Apr 18 2018 at 20:57)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/xor%20is%20not%20associative/near/125266341):
@**Mario Carneiro** muito obrigado

#### [Andrew Ashworth (Apr 18 2018 at 20:58)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/xor%20is%20not%20associative/near/125266387):
this is random but related to xor: has anyone seen a definition of one-hot encoding?

#### [Kevin Buzzard (Apr 18 2018 at 20:58)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/xor%20is%20not%20associative/near/125266388):
now the other way!

#### [Kevin Buzzard (Apr 18 2018 at 20:58)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/xor%20is%20not%20associative/near/125266391):
Oh the other way is trivial, right?

#### [Kevin Buzzard (Apr 18 2018 at 20:58)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/xor%20is%20not%20associative/near/125266392):
Just do cases

#### [Kenny Lau (Apr 18 2018 at 20:58)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/xor%20is%20not%20associative/near/125266396):
right

#### [Kevin Buzzard (Apr 18 2018 at 20:58)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/xor%20is%20not%20associative/near/125266400):
so this is another way of formulating LEM :-)

#### [Kevin Buzzard (Apr 18 2018 at 20:58)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/xor%20is%20not%20associative/near/125266406):
that Prop is a group :-)

#### [Kenny Lau (Apr 18 2018 at 21:03)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/xor%20is%20not%20associative/near/125266595):
right

#### [Kenny Lau (Apr 18 2018 at 21:03)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/xor%20is%20not%20associative/near/125266598):
and people won't guess that it is associativity that fails

#### [Kevin Buzzard (Apr 18 2018 at 21:03)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/xor%20is%20not%20associative/near/125266605):
I'll put it on next year's Christmas Quiz

#### [Mario Carneiro (Apr 18 2018 at 21:04)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/xor%20is%20not%20associative/near/125266655):
I wonder if there is any group structure on Prop?

#### [Gabriel Ebner (Apr 18 2018 at 21:04)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/xor%20is%20not%20associative/near/125266662):
The double-negation translation of `xor` should do the job.

#### [Kevin Buzzard (Apr 18 2018 at 21:04)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/xor%20is%20not%20associative/near/125266665):
rofl

#### [Kevin Buzzard (Apr 18 2018 at 21:05)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/xor%20is%20not%20associative/near/125266676):
I am not so sure life is so easy

#### [Mario Carneiro (Apr 18 2018 at 21:05)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/xor%20is%20not%20associative/near/125266694):
I don't think that will satisfy the cancellation laws on nondecidable props

#### [Kevin Buzzard (Apr 18 2018 at 21:05)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/xor%20is%20not%20associative/near/125266697):
I am not sure this has inverses.

#### [Kevin Buzzard (Apr 18 2018 at 21:06)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/xor%20is%20not%20associative/near/125266758):
This question is related to putting a group structure on the set of open sets in a topological space I guess

#### [Gabriel Ebner (Apr 18 2018 at 21:06)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/xor%20is%20not%20associative/near/125266765):
Mmh, the double-negation translation turns classical theorems into intuitionistic theorems.  So if `xor` is associative, etc., classicaly then `xor^N` should be intuitionistically associative, etc.

#### [Mario Carneiro (Apr 18 2018 at 21:07)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/xor%20is%20not%20associative/near/125266781):
true, but the group has to include all props, not just the negative props

#### [Kevin Buzzard (Apr 18 2018 at 21:08)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/xor%20is%20not%20associative/near/125266840):
in my language, consider open sets which are dense. Their negation is empty

#### [Kevin Buzzard (Apr 18 2018 at 21:08)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/xor%20is%20not%20associative/near/125266846):
so you have lost information which is never coming back, and that's bad for groups

#### [Kevin Buzzard (Apr 18 2018 at 21:09)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/xor%20is%20not%20associative/near/125266861):
Does the following make sense:

#### [Kevin Buzzard (Apr 18 2018 at 21:09)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/xor%20is%20not%20associative/near/125266864):
there is a two-point space with one point open

#### [Kevin Buzzard (Apr 18 2018 at 21:09)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/xor%20is%20not%20associative/near/125266869):
and this space has three open sets

#### [Kevin Buzzard (Apr 18 2018 at 21:10)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/xor%20is%20not%20associative/near/125266871):
and so if it were a group it would be cyclic of order 3

#### [Kevin Buzzard (Apr 18 2018 at 21:10)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/xor%20is%20not%20associative/near/125266923):
and now I want to write down a map from bool to this set or from this set to bool

#### [Kevin Buzzard (Apr 18 2018 at 21:10)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/xor%20is%20not%20associative/near/125266927):
and argue that if Prop had a group structure it would have to be a group homomorphism

#### [Kevin Buzzard (Apr 18 2018 at 21:10)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/xor%20is%20not%20associative/near/125266929):
but things don't add up

#### [Mario Carneiro (Apr 18 2018 at 21:11)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/xor%20is%20not%20associative/near/125266957):
Ah, how about this: every (definable in intuitionistic logic) one-arg operator is noninjective on some topological space or is the identity

#### [Kevin Buzzard (Apr 18 2018 at 21:11)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/xor%20is%20not%20associative/near/125266960):
because I am hoping I am writing down two incompatible "interpretations" of Prop somehow

#### [Gabriel Ebner (Apr 18 2018 at 21:11)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/xor%20is%20not%20associative/near/125266964):
Ah yes, everything goes through except `xor p false <-> p`...

#### [Kenny Lau (Apr 18 2018 at 21:12)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/xor%20is%20not%20associative/near/125267027):
```quote
Ah yes, everything goes through except `xor p false <-> p`...
```
what do you mean?

#### [Kenny Lau (Apr 18 2018 at 21:13)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/xor%20is%20not%20associative/near/125267039):
isn't that intuitionistically valid

#### [Mario Carneiro (Apr 18 2018 at 21:13)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/xor%20is%20not%20associative/near/125267057):
`xor` implies both its arguments are decidable

#### [Mario Carneiro (Apr 18 2018 at 21:13)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/xor%20is%20not%20associative/near/125267060):
(in the LEM sense)

#### [Kenny Lau (Apr 18 2018 at 21:13)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/xor%20is%20not%20associative/near/125267075):
does it?

#### [Kenny Lau (Apr 18 2018 at 21:14)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/xor%20is%20not%20associative/near/125267093):
right, it does

#### [Kenny Lau (Apr 18 2018 at 21:14)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/xor%20is%20not%20associative/near/125267120):
something is wrong with me

#### [Gabriel Ebner (Apr 18 2018 at 21:15)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/xor%20is%20not%20associative/near/125267153):
`xor p false <-> p` fails for the double-negation translation.  It is true in the official version, though.

#### [Peter Jipsen (Apr 24 2018 at 17:04)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/xor%20is%20not%20associative/near/125624185):
Can't one just check associativity of xor in Heyting algebras? It fails in the 3-element Heyting algebra where 0<1<2:  (2 xor 2) xor 1 \ne 2 xor (2 xor 1)    (assuming a xor b is defined as (a or b) and not (a and b)). Of course this would require quite some background work defining Heyting algebras etc.

#### [Kenny Lau (Apr 24 2018 at 17:04)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/xor%20is%20not%20associative/near/125624194):
Is it the same thing as Kripke frames?

#### [Peter Jipsen (Apr 24 2018 at 17:05)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/xor%20is%20not%20associative/near/125624204):
Yes, it's the algebraic version

#### [Kenny Lau (Apr 24 2018 at 17:05)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/xor%20is%20not%20associative/near/125624210):
aha

#### [Kenny Lau (Apr 24 2018 at 17:05)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/xor%20is%20not%20associative/near/125624216):
a xor b is defined as (a and not b) or (not a and b)

#### [Kenny Lau (Apr 24 2018 at 17:05)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/xor%20is%20not%20associative/near/125624225):
would knowing about Kripke frames and boolean algebra make Heyting algebra easy to learn? if so, do you mind teaching me?

#### [Andrew Ashworth (Apr 24 2018 at 17:06)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/xor%20is%20not%20associative/near/125624285):
http://www.cri.ensmp.fr/classement/doc/E-372.pdf

#### [Kenny Lau (Apr 24 2018 at 17:08)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/xor%20is%20not%20associative/near/125624360):
:o infinite logic?

#### [Andrew Ashworth (Apr 24 2018 at 17:09)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/xor%20is%20not%20associative/near/125624389):
the paper is a little hard to read without a little more background

#### [Andrew Ashworth (Apr 24 2018 at 17:09)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/xor%20is%20not%20associative/near/125624390):
but the coq code is nice

#### [Andrew Ashworth (Apr 24 2018 at 17:09)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/xor%20is%20not%20associative/near/125624391):
https://github.com/SkySkimmer/NormalisationByCompleteness

#### [Peter Jipsen (Apr 24 2018 at 17:34)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/xor%20is%20not%20associative/near/125625538):
The definition (a and not b) or (not a and b) has the same counterexample.
The equivalence between finite Heyting algebras and finite partially ordered Kripke frames is similar to the equivalence between finite Boolean algebras and finite sets, so you have all the necessary background. (In the general case Esakia spaces are a categorical dual of Heyting algebras.) Propositional intuitionistic logic is decidable, so questions like this can be answered algorithmically by a tableau prover or Gentzen's sequent calculus LJ.

#### [Kenny Lau (Apr 24 2018 at 17:34)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/xor%20is%20not%20associative/near/125625548):
thanks

#### [Peter Jipsen (Apr 24 2018 at 18:03)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/xor%20is%20not%20associative/near/125626599):
A interesting test problem is to decide if the two definitions of xor are intuitionistically equivalent. I would like to understand how one would use Lean to help prove or refute it. E.g. is there a tactic that implements tableau?

