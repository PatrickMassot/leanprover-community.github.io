---
layout: page
title: Lean Prover Zulip Chat Archive 
permalink: archive/113488general/04462ringbugagain.html
---

## [general](index.html)
### [ring bug again?](04462ringbugagain.html)

#### [Patrick Massot (Jul 31 2018 at 15:45)](https://leanprover.zulipchat.com/#narrow/stream/113488-general/topic/ring%20bug%20again%3F/near/130644147):
```lean
example {α : Type*} [ring α] : ∀ a' b' a₁ b₁ a₂ b₂ : α, 
    a₂*b₂ - a₁*b₁ = (a₂ - a₁)*b' + (a₂ - a₁)*(b₂ - b') + (b₂ - b₁)*a' + (b₂ - b₁)*(a₁ - a') :=
begin
  intros,
  ring,
  sorry
end
```
:disappointed:

#### [Johan Commelin (Jul 31 2018 at 15:47)](https://leanprover.zulipchat.com/#narrow/stream/113488-general/topic/ring%20bug%20again%3F/near/130644291):
`comm_ring`?

#### [Patrick Massot (Jul 31 2018 at 15:47)](https://leanprover.zulipchat.com/#narrow/stream/113488-general/topic/ring%20bug%20again%3F/near/130644301):
oh yes

#### [Patrick Massot (Jul 31 2018 at 15:47)](https://leanprover.zulipchat.com/#narrow/stream/113488-general/topic/ring%20bug%20again%3F/near/130644306):
Good observation

#### [Johan Commelin (Jul 31 2018 at 15:48)](https://leanprover.zulipchat.com/#narrow/stream/113488-general/topic/ring%20bug%20again%3F/near/130644361):
"In the following file, all rings are assumed commutative"

#### [Patrick Massot (Jul 31 2018 at 15:48)](https://leanprover.zulipchat.com/#narrow/stream/113488-general/topic/ring%20bug%20again%3F/near/130644369):
I blame Kevin who is always writing all rings are commutative

#### [Kevin Buzzard (Jul 31 2018 at 16:19)](https://leanprover.zulipchat.com/#narrow/stream/113488-general/topic/ring%20bug%20again%3F/near/130646253):
It's true by definition! It's a bug in Lean -- they missed commutativity out

