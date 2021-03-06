---
layout: page
title: Lean Prover Zulip Chat Archive 
permalink: archive/113488general/98442mulandaddtypeclasshierarchies.html
---

## [general](index.html)
### [mul and add type class hierarchies](98442mulandaddtypeclasshierarchies.html)

#### [Sean Leather (Oct 04 2018 at 09:53)](https://leanprover.zulipchat.com/#narrow/stream/113488-general/topic/mul%20and%20add%20type%20class%20hierarchies/near/135157838):
I'm curious why we have two nearly duplicate type class hierarchies – multiplicative and additive – in Lean. It seems like it would be better to have the type classes be parameterized by the binary operator instead of inheriting the operator. I suppose there are technical/practical problems here which led to the current design.

#### [Johan Commelin (Oct 04 2018 at 09:54)](https://leanprover.zulipchat.com/#narrow/stream/113488-general/topic/mul%20and%20add%20type%20class%20hierarchies/near/135157910):
Yes. You are right. I'll search for the discussion. 1 sec

#### [Johan Commelin (Oct 04 2018 at 09:56)](https://leanprover.zulipchat.com/#narrow/stream/113488-general/topic/mul%20and%20add%20type%20class%20hierarchies/near/135157995):
https://leanprover.zulipchat.com/#narrow/stream/116395-maths/subject/additive.20group.20homs/near/127064577

#### [Johan Commelin (Oct 04 2018 at 09:56)](https://leanprover.zulipchat.com/#narrow/stream/113488-general/topic/mul%20and%20add%20type%20class%20hierarchies/near/135157999):
@**Sean Leather** :up:

#### [Chris Hughes (Oct 04 2018 at 09:57)](https://leanprover.zulipchat.com/#narrow/stream/113488-general/topic/mul%20and%20add%20type%20class%20hierarchies/near/135158019):
Also https://github.com/leanprover/lean/wiki/Refactoring-structures

#### [Sean Leather (Oct 04 2018 at 10:08)](https://leanprover.zulipchat.com/#narrow/stream/113488-general/topic/mul%20and%20add%20type%20class%20hierarchies/near/135158491):
```quote
Also https://github.com/leanprover/lean/wiki/Refactoring-structures
```
I've tried to read that before and my eyes glazed over every time.

