---
layout: page
title: Lean Prover Zulip Chat Archive 
permalink: archive/113488general/77009AccessingNattypewithininductiveTyp.html
---

## [general](index.html)
### [Accessing Nat type within inductive Typ](77009AccessingNattypewithininductiveTyp.html)

#### [Cameron Crossman (Dec 13 2018 at 19:43)](https://leanprover.zulipchat.com/#narrow/stream/113488-general/topic/Accessing%20Nat%20type%20within%20inductive%20Typ/near/151722800):
I have the following inductive definition
inductive Typ
  | Nat
  | Fun : Typ → Typ → Typ

and I am trying to write a theorem and start by assuming some variable p is of type Typ.Nat, how do I go about doing so?  I get  

type expected at
  Typ.Nat
term has type
  Typ

error from assume p : Typ.Nat or something similar. Thanks!

#### [Chris Hughes (Dec 13 2018 at 19:58)](https://leanprover.zulipchat.com/#narrow/stream/113488-general/topic/Accessing%20Nat%20type%20within%20inductive%20Typ/near/151723856):
Something like this might be what you want
```lean
inductive Typ
| Nat : nat → Typ
| Fun : Typ → Typ → Typ
```

#### [Chris Hughes (Dec 13 2018 at 19:58)](https://leanprover.zulipchat.com/#narrow/stream/113488-general/topic/Accessing%20Nat%20type%20within%20inductive%20Typ/near/151723870):
Hang on.

#### [Chris Hughes (Dec 13 2018 at 19:58)](https://leanprover.zulipchat.com/#narrow/stream/113488-general/topic/Accessing%20Nat%20type%20within%20inductive%20Typ/near/151723876):
Typ.Nat is not a Type, it's a constructor.

#### [Cameron Crossman (Dec 13 2018 at 20:00)](https://leanprover.zulipchat.com/#narrow/stream/113488-general/topic/Accessing%20Nat%20type%20within%20inductive%20Typ/near/151723976):
Oh okay :+1:

#### [Cameron Crossman (Dec 13 2018 at 20:00)](https://leanprover.zulipchat.com/#narrow/stream/113488-general/topic/Accessing%20Nat%20type%20within%20inductive%20Typ/near/151724023):
So I just construct of that type with variable p : Typ.Nat or something along those lines

#### [Chris Hughes (Dec 13 2018 at 20:01)](https://leanprover.zulipchat.com/#narrow/stream/113488-general/topic/Accessing%20Nat%20type%20within%20inductive%20Typ/near/151724050):
`Typ.nat : Typ`

#### [Reid Barton (Dec 13 2018 at 20:01)](https://leanprover.zulipchat.com/#narrow/stream/113488-general/topic/Accessing%20Nat%20type%20within%20inductive%20Typ/near/151724057):
`Typ` has nothing to do with actual types, despite the name

#### [Chris Hughes (Dec 13 2018 at 20:01)](https://leanprover.zulipchat.com/#narrow/stream/113488-general/topic/Accessing%20Nat%20type%20within%20inductive%20Typ/near/151724064):
(deleted)

#### [Reid Barton (Dec 13 2018 at 20:01)](https://leanprover.zulipchat.com/#narrow/stream/113488-general/topic/Accessing%20Nat%20type%20within%20inductive%20Typ/near/151724065):
Maybe you want to define an interpretation `Typ -> Type`

#### [Cameron Crossman (Dec 13 2018 at 20:04)](https://leanprover.zulipchat.com/#narrow/stream/113488-general/topic/Accessing%20Nat%20type%20within%20inductive%20Typ/near/151724268):
thanks!

