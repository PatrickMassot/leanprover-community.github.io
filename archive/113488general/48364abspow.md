---
layout: page
title: Lean Prover Zulip Chat Archive 
permalink: archive/113488general/48364abspow.html
---

## [general](index.html)
### [abs_pow](48364abspow.html)

#### [Kenny Lau (May 03 2018 at 00:18)](https://leanprover.zulipchat.com/#narrow/stream/113488-general/topic/abs_pow/near/126016992):
```lean
theorem abs_pow {α : Type*} [decidable_linear_ordered_comm_ring α]
  (x : α) (n : nat) : abs (x^n) = (abs x)^n :=
nat.rec_on n abs_one $ λ n ih, (abs_mul _ _).trans $ congr_arg _ ih
```

#### [Kenny Lau (May 03 2018 at 00:18)](https://leanprover.zulipchat.com/#narrow/stream/113488-general/topic/abs_pow/near/126016994):
but we all know what the answer is

#### [Kenny Lau (May 03 2018 at 00:18)](https://leanprover.zulipchat.com/#narrow/stream/113488-general/topic/abs_pow/near/126016995):
this thing is in core

#### [Mario Carneiro (May 03 2018 at 00:21)](https://leanprover.zulipchat.com/#narrow/stream/113488-general/topic/abs_pow/near/126017097):
Kenny, you need to work on making your issues more explicit. These code snippets don't speak for themselves

#### [Kenny Lau (May 03 2018 at 00:23)](https://leanprover.zulipchat.com/#narrow/stream/113488-general/topic/abs_pow/near/126017150):
oh sorry

#### [Kenny Lau (May 03 2018 at 00:23)](https://leanprover.zulipchat.com/#narrow/stream/113488-general/topic/abs_pow/near/126017152):
I mean, we should add this in our library

#### [Chris Hughes (May 03 2018 at 10:10)](https://leanprover.zulipchat.com/#narrow/stream/113488-general/topic/abs_pow/near/126034375):
I think it's called pow_abs in mathlib

#### [Kenny Lau (May 03 2018 at 10:10)](https://leanprover.zulipchat.com/#narrow/stream/113488-general/topic/abs_pow/near/126034378):
oh

#### [Kenny Lau (May 03 2018 at 10:11)](https://leanprover.zulipchat.com/#narrow/stream/113488-general/topic/abs_pow/near/126034379):
aha

#### [Kenny Lau (May 03 2018 at 10:11)](https://leanprover.zulipchat.com/#narrow/stream/113488-general/topic/abs_pow/near/126034387):
very consistent naming

