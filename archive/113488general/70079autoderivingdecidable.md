---
layout: page
title: Lean Prover Zulip Chat Archive 
permalink: archive/113488general/70079autoderivingdecidable.html
---

## [general](index.html)
### [auto deriving decidable](70079autoderivingdecidable.html)

#### [Zesen Qian (Jun 20 2018 at 19:53)](https://leanprover.zulipchat.com/#narrow/stream/113488-general/topic/auto%20deriving%20decidable/near/128374348):
Is there some way to derive decidable instance from a inductive definition?

#### [Zesen Qian (Jun 20 2018 at 19:56)](https://leanprover.zulipchat.com/#narrow/stream/113488-general/topic/auto%20deriving%20decidable/near/128374554):
sorry, I mean the decidable instance for equality on this inductive type.

#### [Simon Hudon (Jun 20 2018 at 19:57)](https://leanprover.zulipchat.com/#narrow/stream/113488-general/topic/auto%20deriving%20decidable/near/128374581):
Try:

```lean
instance : decidable_eq my_type :=
by mk_dec_eq_instance
```

#### [Mario Carneiro (Jun 20 2018 at 20:49)](https://leanprover.zulipchat.com/#narrow/stream/113488-general/topic/auto%20deriving%20decidable/near/128377002):
or `@[derive decidable_eq]`

