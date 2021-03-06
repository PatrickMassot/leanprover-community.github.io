---
layout: page
title: Lean Prover Zulip Chat Archive 
permalink: archive/113488general/68526typeresizing.html
---

## [general](index.html)
### [type resizing](68526typeresizing.html)

#### [Reid Barton (Jun 01 2018 at 18:30)](https://leanprover.zulipchat.com/#narrow/stream/113488-general/topic/type%20resizing/near/127424550):
Suppose I have a type `α : Type (u+1)` and I know `∃ β : Type u, nonempty (β ≃ α)`. Is there a "canonical" (= without choice, I guess?) way to obtain a type `α' : Type u` and an equivalence `α ≃ α'`?

#### [Simon Hudon (Jun 01 2018 at 18:33)](https://leanprover.zulipchat.com/#narrow/stream/113488-general/topic/type%20resizing/near/127424655):
I think you would be able to prove the axiom of choice if you had that

#### [Simon Hudon (Jun 01 2018 at 18:34)](https://leanprover.zulipchat.com/#narrow/stream/113488-general/topic/type%20resizing/near/127424744):
Sorry, I take it back, you could pick `α` and `α ≃ α'` as the identity equivalence

#### [Mario Carneiro (Jun 01 2018 at 18:45)](https://leanprover.zulipchat.com/#narrow/stream/113488-general/topic/type%20resizing/near/127425203):
You could use `ordinal` to give it a kind of canonicity, but that doesn't really avoid choice, it's nonconstructive all over the place.

#### [Mario Carneiro (Jun 01 2018 at 18:46)](https://leanprover.zulipchat.com/#narrow/stream/113488-general/topic/type%20resizing/near/127425253):
Also that doesn't provide the equiv itself, just a proof of existence; only the type is canonical

