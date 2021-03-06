---
layout: page
title: Lean Prover Zulip Chat Archive 
permalink: archive/113488general/98393descendinguniverses.html
---

## [general](index.html)
### [descending universes](98393descendinguniverses.html)

#### [Kevin Buzzard (Jul 19 2018 at 19:32)](https://leanprover.zulipchat.com/#narrow/stream/113488-general/topic/descending%20universes/near/129944915):
My universe issue with perfectoid spaces has become: if I have `X : Type u` and `(Y : Type v) [group Y]` and an injection `f : X -> Y` then I want a *group* `G : Type u` and an injection `i:X -> G` and an injective group homomorphism `j:G -> Y` with `ji=f`. Morally I want `G` to be "the subgroup of `Y` generated by the image of `f`, except in universe `u`". How does one construct that sort of thing? I've never worried about this sort of question before.

#### [Kevin Buzzard (Jul 19 2018 at 19:34)](https://leanprover.zulipchat.com/#narrow/stream/113488-general/topic/descending%20universes/near/129945009):
I guess that WLOG `Y` is generated, as a group, by the image of `f`, and then `j` would be a bijection -- but I don't know if this helps.

#### [Reid Barton (Jul 19 2018 at 19:36)](https://leanprover.zulipchat.com/#narrow/stream/113488-general/topic/descending%20universes/near/129945114):
Well, in this case, you can take the free group on X modulo whatever relations are true after applying `f`.

#### [Kevin Buzzard (Jul 19 2018 at 19:38)](https://leanprover.zulipchat.com/#narrow/stream/113488-general/topic/descending%20universes/near/129945232):
Oh that'll do for me. Are free groups in Lean?

#### [Kevin Buzzard (Jul 19 2018 at 19:39)](https://leanprover.zulipchat.com/#narrow/stream/113488-general/topic/descending%20universes/near/129945235):
Actually everything is abelian

#### [Kevin Buzzard (Jul 19 2018 at 19:39)](https://leanprover.zulipchat.com/#narrow/stream/113488-general/topic/descending%20universes/near/129945264):
but making a free group as a subset of maps from X to the integers, for example -- would that bump up the universe level by 1?

#### [Reid Barton (Jul 19 2018 at 19:41)](https://leanprover.zulipchat.com/#narrow/stream/113488-general/topic/descending%20universes/near/129945350):
No, only quantifying over types (belong to the same universe as X) would do that.

#### [Kevin Buzzard (Jul 19 2018 at 19:41)](https://leanprover.zulipchat.com/#narrow/stream/113488-general/topic/descending%20universes/near/129945374):
yes you're right. Thanks Reid -- this is perfect!

#### [Johan Commelin (Jul 19 2018 at 20:12)](https://leanprover.zulipchat.com/#narrow/stream/113488-general/topic/descending%20universes/near/129947066):
Kevin, so you could use `finsupp` for the free groups. The would be additive, so you need to extract a multiplicative group out of it afterwards...

#### [Patrick Massot (Jul 19 2018 at 20:22)](https://leanprover.zulipchat.com/#narrow/stream/113488-general/topic/descending%20universes/near/129947558):
https://github.com/leanprover/mathlib/blob/master/group_theory/free_group.lean

#### [Johan Commelin (Jul 19 2018 at 20:33)](https://leanprover.zulipchat.com/#narrow/stream/113488-general/topic/descending%20universes/near/129948130):
But that's non-abelian...

#### [Patrick Massot (Jul 19 2018 at 20:33)](https://leanprover.zulipchat.com/#narrow/stream/113488-general/topic/descending%20universes/near/129948135):
indeed

