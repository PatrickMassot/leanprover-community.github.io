---
layout: page
title: Lean Prover Zulip Chat Archive 
permalink: archive/113488general/89951circumflexnotation.html
---

## [general](index.html)
### [circumflex notation](89951circumflexnotation.html)

#### [Miko de Amsterdamo (Apr 12 2018 at 14:08)](https://leanprover.zulipchat.com/#narrow/stream/113488-general/topic/circumflex%20notation/near/124981819):
What does this notation do? (hat/circumflex) I'm looking at an example in https://leanprover.github.io/programming_in_lean/#09_Writing_Automation.html and I found it in "(assume ha, h^.left ha)"

#### [Simon Hudon (Apr 12 2018 at 14:16)](https://leanprover.zulipchat.com/#narrow/stream/113488-general/topic/circumflex%20notation/near/124982270):
That's old notation. It was for field projection. Now it's only `.`

#### [Miko de Amsterdamo (Apr 12 2018 at 14:17)](https://leanprover.zulipchat.com/#narrow/stream/113488-general/topic/circumflex%20notation/near/124982310):
So the token `^.` has been replaced by just `.` ?

#### [Simon Hudon (Apr 12 2018 at 14:54)](https://leanprover.zulipchat.com/#narrow/stream/113488-general/topic/circumflex%20notation/near/124983725):
That's correct. So `.` has the double duty of qualifying names with name spaces and resolving projections.

#### [Miko de Amsterdamo (Apr 12 2018 at 14:54)](https://leanprover.zulipchat.com/#narrow/stream/113488-general/topic/circumflex%20notation/near/124983730):
Thanks!

