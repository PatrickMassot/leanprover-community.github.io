---
layout: page
title: Lean Prover Zulip Chat Archive 
permalink: archive/113488general/04670obtain.html
---

## [general](index.html)
### [obtain](04670obtain.html)

#### [Johan Commelin (Nov 09 2018 at 05:59)](https://leanprover.zulipchat.com/#narrow/stream/113488-general/topic/obtain/near/147351059):
I just realised there is `obtain`:
https://github.com/leanprover/mathlib/search?q=obtain&unscoped_q=obtain

#### [Johan Commelin (Nov 09 2018 at 06:00)](https://leanprover.zulipchat.com/#narrow/stream/113488-general/topic/obtain/near/147351108):
I have not yet figured out what it does.

#### [Bryan Gin-ge Chen (Nov 09 2018 at 06:01)](https://leanprover.zulipchat.com/#narrow/stream/113488-general/topic/obtain/near/147351132):
I think I looked it up before and I concluded it was a lean 2 thing?

#### [Mario Carneiro (Nov 09 2018 at 06:24)](https://leanprover.zulipchat.com/#narrow/stream/113488-general/topic/obtain/near/147351875):
it is a lean 2 thing. `obtain x h, from expr, expr'` is the lean 2 way of writing `let <x, h> := expr in expr'`, at least when `expr` has exists type. I forget how general it is

#### [Mario Carneiro (Nov 09 2018 at 06:26)](https://leanprover.zulipchat.com/#narrow/stream/113488-general/topic/obtain/near/147351938):
the style guide also uses `take`, which is no longer a keyword and is the same as `λ`

#### [Johan Commelin (Nov 09 2018 at 06:28)](https://leanprover.zulipchat.com/#narrow/stream/113488-general/topic/obtain/near/147351993):
Ok, thanks for explaining!

#### [Floris van Doorn (Nov 09 2018 at 06:34)](https://leanprover.zulipchat.com/#narrow/stream/113488-general/topic/obtain/near/147352250):
`obtain` used to work on all inductive types with a single constructor. It was the way to do `cases` in term mode.

