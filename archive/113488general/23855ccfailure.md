---
layout: page
title: Lean Prover Zulip Chat Archive 
permalink: archive/113488general/23855ccfailure.html
---

## [general](index.html)
### [cc failure](23855ccfailure.html)

#### [Reid Barton (May 16 2018 at 19:03)](https://leanprover.zulipchat.com/#narrow/stream/113488-general/topic/cc%20failure/near/126654388):
Is this a bug?
```lean
example {α β : Type} (x1 x2 : α) (y : β) (h : x1 = x2)
  {p : β → Prop} (hp : p y) :
  ∃ y', p y' ∧ (x2, y') = (x1, y) :=
begin
  existsi _, split, exact hp, -- ⊢ (x2, y) = (x1, y)                                                                                               
  cc                          -- cc tactic failed                                                                                                  
end
```

#### [Reid Barton (May 16 2018 at 19:06)](https://leanprover.zulipchat.com/#narrow/stream/113488-general/topic/cc%20failure/near/126654522):
(I know the lemma and proof are strange, this is a minimized version of some real code)

#### [Reid Barton (May 16 2018 at 19:08)](https://leanprover.zulipchat.com/#narrow/stream/113488-general/topic/cc%20failure/near/126654615):
It seems that `cc` doesn't recognize that the `y`s are equal because one of them was created by substituting for a metavariable, or something.

#### [Kenny Lau (May 16 2018 at 19:09)](https://leanprover.zulipchat.com/#narrow/stream/113488-general/topic/cc%20failure/near/126654631):
`subst h`

#### [Reid Barton (May 16 2018 at 19:10)](https://leanprover.zulipchat.com/#narrow/stream/113488-general/topic/cc%20failure/near/126654692):
I observed this a few days ago as well, but in a setting which was too hard to minimize.

#### [Kenny Lau (May 16 2018 at 19:11)](https://leanprover.zulipchat.com/#narrow/stream/113488-general/topic/cc%20failure/near/126654713):
try `set_option pp.all true`

#### [Chris Hughes (May 16 2018 at 19:11)](https://leanprover.zulipchat.com/#narrow/stream/113488-general/topic/cc%20failure/near/126654714):
```quote
`subst h`
```
`rw h`

#### [Reid Barton (May 16 2018 at 19:11)](https://leanprover.zulipchat.com/#narrow/stream/113488-general/topic/cc%20failure/near/126654717):
stop!

#### [Chris Hughes (May 16 2018 at 19:13)](https://leanprover.zulipchat.com/#narrow/stream/113488-general/topic/cc%20failure/near/126654798):
this works
```lean
example {α β : Type} (x1 x2 : α) (y : β) (h : x1 = x2)
  {p : β → Prop} (hp : p y) :
  ∃ y', p y' ∧ (x2, y') = (x1, y) := ⟨_, hp, begin
    cc,
  end⟩
```
So it seems like a bug.

#### [Kenny Lau (May 16 2018 at 19:13)](https://leanprover.zulipchat.com/#narrow/stream/113488-general/topic/cc%20failure/near/126654801):
`by cc`

#### [Reid Barton (May 16 2018 at 19:13)](https://leanprover.zulipchat.com/#narrow/stream/113488-general/topic/cc%20failure/near/126654812):
Yeah, changing `cc` to `exact by cc` works also

#### [Reid Barton (May 16 2018 at 19:14)](https://leanprover.zulipchat.com/#narrow/stream/113488-general/topic/cc%20failure/near/126654831):
(And also in my real code.)

#### [Chris Hughes (May 16 2018 at 19:14)](https://leanprover.zulipchat.com/#narrow/stream/113488-general/topic/cc%20failure/near/126654862):
It's to do with the metavariable
```lean
example {α β : Type} (x1 x2 : α) (y : β) (h : x1 = x2)
  {p : β → Prop} (hp : p y) :
  ∃ y', p y' ∧ (x2, y') = (x1, y) :=
begin
  existsi y, split, exact hp, -- ⊢ (x2, y) = (x1, y)
  cc                          -- cc tactic failed
end
```
works

#### [Kenny Lau (May 16 2018 at 19:14)](https://leanprover.zulipchat.com/#narrow/stream/113488-general/topic/cc%20failure/near/126654867):
I thought `exact hp` unified the metavariable

#### [Reid Barton (May 16 2018 at 19:14)](https://leanprover.zulipchat.com/#narrow/stream/113488-general/topic/cc%20failure/near/126654875):
It does. That's what makes this so confusing.

#### [Reid Barton (May 16 2018 at 19:15)](https://leanprover.zulipchat.com/#narrow/stream/113488-general/topic/cc%20failure/near/126654908):
The displayed proof state is exactly the same whether you write `existsi _` or `existsi y`

#### [Reid Barton (May 16 2018 at 19:16)](https://leanprover.zulipchat.com/#narrow/stream/113488-general/topic/cc%20failure/near/126654948):
but `cc` only works in the second case

