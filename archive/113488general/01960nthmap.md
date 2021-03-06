---
layout: page
title: Lean Prover Zulip Chat Archive 
permalink: archive/113488general/01960nthmap.html
---

## [general](index.html)
### [nth_map](01960nthmap.html)

#### [Patrick Massot (May 13 2018 at 22:59)](https://leanprover.zulipchat.com/#narrow/stream/113488-general/topic/nth_map/near/126509555):
Do we have something like
```lean
lemma nth_le_map {α : Type*} {β : Type*} {l : list α} (n : ℕ) (H: n < length l) 
  (f : α → β) : nth_le (map f l) n ((length_map f l).symm ▸ H) = f (nth_le l n H) :=
```

#### [Patrick Massot (May 13 2018 at 22:59)](https://leanprover.zulipchat.com/#narrow/stream/113488-general/topic/nth_map/near/126509560):
It feels a bit weird to stick a proof in the middle of the statement

#### [Patrick Massot (May 13 2018 at 22:59)](https://leanprover.zulipchat.com/#narrow/stream/113488-general/topic/nth_map/near/126509561):
Am I doing something wrong?

#### [Mario Carneiro (May 13 2018 at 23:01)](https://leanprover.zulipchat.com/#narrow/stream/113488-general/topic/nth_map/near/126509612):
One approach I have used in the past is to have two proof arguments, but this makes rewriting produce proof obligations that look superfluous

#### [Patrick Massot (May 13 2018 at 23:01)](https://leanprover.zulipchat.com/#narrow/stream/113488-general/topic/nth_map/near/126509615):
And I don't know how to prove it

#### [Mario Carneiro (May 13 2018 at 23:01)](https://leanprover.zulipchat.com/#narrow/stream/113488-general/topic/nth_map/near/126509620):
i.e. you would prove `nth_le (map f l) n H1 = f (nth_le l n H2) `

#### [Patrick Massot (May 13 2018 at 23:01)](https://leanprover.zulipchat.com/#narrow/stream/113488-general/topic/nth_map/near/126509621):
You you mean adding `(H' : n < length (map f l))`?

#### [Patrick Massot (May 13 2018 at 23:02)](https://leanprover.zulipchat.com/#narrow/stream/113488-general/topic/nth_map/near/126509651):
ok

#### [Patrick Massot (May 13 2018 at 23:02)](https://leanprover.zulipchat.com/#narrow/stream/113488-general/topic/nth_map/near/126509663):
I still don't know how to prove it though

#### [Patrick Massot (May 13 2018 at 23:03)](https://leanprover.zulipchat.com/#narrow/stream/113488-general/topic/nth_map/near/126509671):
Why is this not in mathlib? It looks like it would be useful for many proofs

#### [Mario Carneiro (May 13 2018 at 23:03)](https://leanprover.zulipchat.com/#narrow/stream/113488-general/topic/nth_map/near/126509672):
I'm asking the same question

#### [Mario Carneiro (May 13 2018 at 23:03)](https://leanprover.zulipchat.com/#narrow/stream/113488-general/topic/nth_map/near/126509674):
I would start with `nth`

#### [Mario Carneiro (May 13 2018 at 23:03)](https://leanprover.zulipchat.com/#narrow/stream/113488-general/topic/nth_map/near/126509675):
since that avoids the proof argument stuff

#### [Patrick Massot (May 13 2018 at 23:03)](https://leanprover.zulipchat.com/#narrow/stream/113488-general/topic/nth_map/near/126509676):
I also thought that

#### [Patrick Massot (May 13 2018 at 23:03)](https://leanprover.zulipchat.com/#narrow/stream/113488-general/topic/nth_map/near/126509677):
But I couldn't even state it :disappointed:

#### [Patrick Massot (May 13 2018 at 23:04)](https://leanprover.zulipchat.com/#narrow/stream/113488-general/topic/nth_map/near/126509716):
Because `f` doesn't want an `option α`

#### [Mario Carneiro (May 13 2018 at 23:08)](https://leanprover.zulipchat.com/#narrow/stream/113488-general/topic/nth_map/near/126509823):
```
theorem nth_map (f : α → β) : ∀ l n, nth (map f l) n = (nth l n).map f
| []       n     := rfl
| (a :: l) 0     := rfl
| (a :: l) (n+1) := nth_map l n

theorem nth_le_map (f : α → β) {l n} (H1 H2) : nth_le (map f l) n H1 = f (nth_le l n H2) :=
option.some.inj $ by rw [← nth_le_nth, nth_map, nth_le_nth]; refl
```

#### [Mario Carneiro (May 13 2018 at 23:08)](https://leanprover.zulipchat.com/#narrow/stream/113488-general/topic/nth_map/near/126509824):
`option.map` takes `f : A -> B` to `map f : option A -> option B`

#### [Patrick Massot (May 13 2018 at 23:09)](https://leanprover.zulipchat.com/#narrow/stream/113488-general/topic/nth_map/near/126509827):
:open_mouth:

#### [Patrick Massot (May 13 2018 at 23:10)](https://leanprover.zulipchat.com/#narrow/stream/113488-general/topic/nth_map/near/126509881):
I was clearly missing that `option.map` piece

#### [Patrick Massot (May 13 2018 at 23:10)](https://leanprover.zulipchat.com/#narrow/stream/113488-general/topic/nth_map/near/126509886):
but probably not only that

#### [Mario Carneiro (May 13 2018 at 23:10)](https://leanprover.zulipchat.com/#narrow/stream/113488-general/topic/nth_map/near/126509887):
`option` is a functor

#### [Kenny Lau (May 13 2018 at 23:10)](https://leanprover.zulipchat.com/#narrow/stream/113488-general/topic/nth_map/near/126509889):
is this proven in mathlib / Lean?

#### [Mario Carneiro (May 13 2018 at 23:10)](https://leanprover.zulipchat.com/#narrow/stream/113488-general/topic/nth_map/near/126509891):
yes, because every monad is a functor

#### [Mario Carneiro (May 13 2018 at 23:11)](https://leanprover.zulipchat.com/#narrow/stream/113488-general/topic/nth_map/near/126509898):
and `option` is like the very first monad you write

#### [Kenny Lau (May 13 2018 at 23:11)](https://leanprover.zulipchat.com/#narrow/stream/113488-general/topic/nth_map/near/126509900):
you mean sentence

#### [Mario Carneiro (May 13 2018 at 23:12)](https://leanprover.zulipchat.com/#narrow/stream/113488-general/topic/nth_map/near/126509942):
like when learning what monads are and examples, `option` is always the example

#### [Patrick Massot (May 13 2018 at 23:12)](https://leanprover.zulipchat.com/#narrow/stream/113488-general/topic/nth_map/near/126509946):
Thank you very much Mario. I hope this will also be a good reference next time I'll hit this `option` stuff

#### [Patrick Massot (May 13 2018 at 23:12)](https://leanprover.zulipchat.com/#narrow/stream/113488-general/topic/nth_map/near/126509947):
I still think you could put those two lemmas in mathlib

#### [Mario Carneiro (May 13 2018 at 23:14)](https://leanprover.zulipchat.com/#narrow/stream/113488-general/topic/nth_map/near/126509993):
I'm doing that now

#### [Mario Carneiro (May 13 2018 at 23:15)](https://leanprover.zulipchat.com/#narrow/stream/113488-general/topic/nth_map/near/126510003):
I definitely want more `nth` and `index_of` theorems, to make it easier to think of `list` as finitely supported functions on nat

#### [Patrick Massot (May 13 2018 at 23:17)](https://leanprover.zulipchat.com/#narrow/stream/113488-general/topic/nth_map/near/126510056):
Great

#### [Patrick Massot (May 13 2018 at 23:18)](https://leanprover.zulipchat.com/#narrow/stream/113488-general/topic/nth_map/near/126510097):
I was going after something like `reverse (range' a b) = map (lam x, ...) (range' a b)` and stuff like that

#### [Patrick Massot (May 13 2018 at 23:20)](https://leanprover.zulipchat.com/#narrow/stream/113488-general/topic/nth_map/near/126510108):
And was also thinking about defining `int_range k n` same as `range'` but `k` is an integer

#### [Patrick Massot (May 13 2018 at 23:20)](https://leanprover.zulipchat.com/#narrow/stream/113488-general/topic/nth_map/near/126510154):
and generalizing all the `range'` lemmas to this case

#### [Mario Carneiro (May 14 2018 at 00:56)](https://leanprover.zulipchat.com/#narrow/stream/113488-general/topic/nth_map/near/126512722):
That makes sense. I guess you could define `range'` generalized to any semiring, although it doesn't have the "consecutivity" property except in `nat` and `int`

