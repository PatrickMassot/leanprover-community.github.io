---
layout: page
title: Lean Prover Zulip Chat Archive 
permalink: archive/113488general/73253normalformintacticsmode.html
---

## [general](index.html)
### [normal form in tactics mode](73253normalformintacticsmode.html)

#### [petercommand (Dec 01 2018 at 15:31)](https://leanprover.zulipchat.com/#narrow/stream/113488-general/topic/normal%20form%20in%20tactics%20mode/near/150685526):
is there any tactic that can be used to reduce a type to head normal form in tactics mode? thanks!

#### [petercommand (Dec 01 2018 at 15:32)](https://leanprover.zulipchat.com/#narrow/stream/113488-general/topic/normal%20form%20in%20tactics%20mode/near/150685572):
like coq's compute tactic

#### [Mario Carneiro (Dec 01 2018 at 15:38)](https://leanprover.zulipchat.com/#narrow/stream/113488-general/topic/normal%20form%20in%20tactics%20mode/near/150685787):
`whnf`

#### [petercommand (Dec 01 2018 at 15:51)](https://leanprover.zulipchat.com/#narrow/stream/113488-general/topic/normal%20form%20in%20tactics%20mode/near/150686132):
hmm, I have no idea how to use whnf..

#### [petercommand (Dec 01 2018 at 15:51)](https://leanprover.zulipchat.com/#narrow/stream/113488-general/topic/normal%20form%20in%20tactics%20mode/near/150686137):
I want to reduce the goal to hnf though, not whnf

