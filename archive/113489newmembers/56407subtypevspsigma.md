---
layout: page
title: Lean Prover Zulip Chat Archive 
permalink: archive/113489newmembers/56407subtypevspsigma.html
---

## [new members](index.html)
### [subtype vs psigma](56407subtypevspsigma.html)

#### [Sebastian Zimmer (Oct 14 2018 at 20:07)](https://leanprover.zulipchat.com/#narrow/stream/113489-new%20members/topic/subtype%20vs%20psigma/near/135787450):
What is the difference between `{a:α // p a}` and `Σ' a, P a`?
It seems like they are both a dependent pair.

#### [Chris Hughes (Oct 14 2018 at 20:08)](https://leanprover.zulipchat.com/#narrow/stream/113489-new%20members/topic/subtype%20vs%20psigma/near/135787505):
`psigma` is a less restrictive definition than `subtype`, because the second element does not have to be a proof, but for subtypes it does.

#### [Sebastian Zimmer (Oct 14 2018 at 20:09)](https://leanprover.zulipchat.com/#narrow/stream/113489-new%20members/topic/subtype%20vs%20psigma/near/135787529):
So in the case where the second element is a proof, which one would you recommend using?

#### [Chris Hughes (Oct 14 2018 at 20:10)](https://leanprover.zulipchat.com/#narrow/stream/113489-new%20members/topic/subtype%20vs%20psigma/near/135787578):
Definitely `subtype`. Subtypes have the extensionality rule, that two elements are equal iff the first of the pair is equal, which is very handy.

