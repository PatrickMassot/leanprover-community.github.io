---
layout: page
title: Lean Prover Zulip Chat Archive 
permalink: archive/113489newmembers/19949issubtypeinjective.html
---

## [new members](index.html)
### [is "subtype" injective?](19949issubtypeinjective.html)

#### [Kenny Lau (Sep 13 2018 at 21:32)](https://leanprover.zulipchat.com/#narrow/stream/113489-new%20members/topic/is%20%22subtype%22%20injective%3F/near/133907830):
if {x // p x} = {x // q x}, then is it true that p = q?

#### [Chris Hughes (Sep 13 2018 at 21:33)](https://leanprover.zulipchat.com/#narrow/stream/113489-new%20members/topic/is%20%22subtype%22%20injective%3F/near/133907874):
Pretty sure it's independent unless they're different sizes.

#### [Kenny Lau (Sep 13 2018 at 21:36)](https://leanprover.zulipchat.com/#narrow/stream/113489-new%20members/topic/is%20%22subtype%22%20injective%3F/near/133908076):
great, I just found another independent proposition

#### [Kenny Lau (Sep 13 2018 at 21:36)](https://leanprover.zulipchat.com/#narrow/stream/113489-new%20members/topic/is%20%22subtype%22%20injective%3F/near/133908080):
ZFC 1 : 0 Lean

#### [Mario Carneiro (Sep 13 2018 at 21:57)](https://leanprover.zulipchat.com/#narrow/stream/113489-new%20members/topic/is%20%22subtype%22%20injective%3F/near/133909373):
Lean has loads of independent propositions like this

#### [Kenny Lau (Sep 13 2018 at 21:57)](https://leanprover.zulipchat.com/#narrow/stream/113489-new%20members/topic/is%20%22subtype%22%20injective%3F/near/133909397):
ZFC aleph[0] : 0 Lean

#### [Mario Carneiro (Sep 13 2018 at 21:57)](https://leanprover.zulipchat.com/#narrow/stream/113489-new%20members/topic/is%20%22subtype%22%20injective%3F/near/133909398):
Equality of types is essentially "freely generated"; unless it's obviously true it's probably independent

#### [Mario Carneiro (Sep 13 2018 at 21:58)](https://leanprover.zulipchat.com/#narrow/stream/113489-new%20members/topic/is%20%22subtype%22%20injective%3F/near/133909453):
of course there is a whole cottage industry built around alternative models that fit in this gap (see: HoTT)

#### [Mario Carneiro (Sep 13 2018 at 22:00)](https://leanprover.zulipchat.com/#narrow/stream/113489-new%20members/topic/is%20%22subtype%22%20injective%3F/near/133909548):
the distance from axioms to independent statements is very short in lean:
```
inductive A. inductive B.
example : A = B := independent
```

#### [Kenny Lau (Sep 13 2018 at 22:00)](https://leanprover.zulipchat.com/#narrow/stream/113489-new%20members/topic/is%20%22subtype%22%20injective%3F/near/133909561):
wait what

#### [Kenny Lau (Sep 13 2018 at 22:00)](https://leanprover.zulipchat.com/#narrow/stream/113489-new%20members/topic/is%20%22subtype%22%20injective%3F/near/133909567):
well I suppose it makes sense

#### [Kenny Lau (Sep 13 2018 at 22:01)](https://leanprover.zulipchat.com/#narrow/stream/113489-new%20members/topic/is%20%22subtype%22%20injective%3F/near/133909593):
so we can essentially have two copies of `empty` and nobody will notice

#### [Kenny Lau (Sep 13 2018 at 22:01)](https://leanprover.zulipchat.com/#narrow/stream/113489-new%20members/topic/is%20%22subtype%22%20injective%3F/near/133909604):
also is there any way to create an inductive type?

#### [Kenny Lau (Sep 13 2018 at 22:01)](https://leanprover.zulipchat.com/#narrow/stream/113489-new%20members/topic/is%20%22subtype%22%20injective%3F/near/133909605):
inside a proof?

#### [Kenny Lau (Sep 13 2018 at 22:01)](https://leanprover.zulipchat.com/#narrow/stream/113489-new%20members/topic/is%20%22subtype%22%20injective%3F/near/133909613):
i.e. how much does Lean itself know about inductive types?

#### [Mario Carneiro (Sep 13 2018 at 22:02)](https://leanprover.zulipchat.com/#narrow/stream/113489-new%20members/topic/is%20%22subtype%22%20injective%3F/near/133909625):
oh wait, I forgot to define equality
```
prelude
inductive A. inductive B.
inductive eqA : Type → Type | refl : eqA A
example : eqA B := independent
```

#### [Kenny Lau (Sep 13 2018 at 22:02)](https://leanprover.zulipchat.com/#narrow/stream/113489-new%20members/topic/is%20%22subtype%22%20injective%3F/near/133909675):
lol

#### [Mario Carneiro (Sep 13 2018 at 22:03)](https://leanprover.zulipchat.com/#narrow/stream/113489-new%20members/topic/is%20%22subtype%22%20injective%3F/near/133909720):
inductive types in lean are essentially an axiom schema

#### [Mario Carneiro (Sep 13 2018 at 22:04)](https://leanprover.zulipchat.com/#narrow/stream/113489-new%20members/topic/is%20%22subtype%22%20injective%3F/near/133909741):
you have to write down the type specification, and then poof appears a new type constant

#### [Mario Carneiro (Sep 13 2018 at 22:04)](https://leanprover.zulipchat.com/#narrow/stream/113489-new%20members/topic/is%20%22subtype%22%20injective%3F/near/133909795):
so they only work at the top level

#### [Kenny Lau (Sep 13 2018 at 22:04)](https://leanprover.zulipchat.com/#narrow/stream/113489-new%20members/topic/is%20%22subtype%22%20injective%3F/near/133909828):
I see

#### [Mario Carneiro (Sep 13 2018 at 22:05)](https://leanprover.zulipchat.com/#narrow/stream/113489-new%20members/topic/is%20%22subtype%22%20injective%3F/near/133909849):
although you can always define a very general type and then narrow it down from inside a definition, i.e. defining a particular subtype of sigma of W type of whatever rather than writing a new inductive type

