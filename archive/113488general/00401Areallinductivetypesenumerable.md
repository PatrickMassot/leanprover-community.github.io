---
layout: page
title: Lean Prover Zulip Chat Archive 
permalink: archive/113488general/00401Areallinductivetypesenumerable.html
---

## [general](index.html)
### [Are all inductive types enumerable?](00401Areallinductivetypesenumerable.html)

#### [Kenny Lau (Aug 01 2018 at 08:51)](https://leanprover.zulipchat.com/#narrow/stream/113488-general/topic/Are%20all%20inductive%20types%20enumerable%3F/near/130696713):
Are all inductive types enumerable?

#### [Mario Carneiro (Aug 01 2018 at 08:54)](https://leanprover.zulipchat.com/#narrow/stream/113488-general/topic/Are%20all%20inductive%20types%20enumerable%3F/near/130696827):
inductive types whose parts are enumerable are enumerable

#### [Mario Carneiro (Aug 01 2018 at 08:55)](https://leanprover.zulipchat.com/#narrow/stream/113488-general/topic/Are%20all%20inductive%20types%20enumerable%3F/near/130696857):
indeed it's not unreasonable to have a `derive_handler` for that

#### [Kenny Lau (Aug 01 2018 at 08:55)](https://leanprover.zulipchat.com/#narrow/stream/113488-general/topic/Are%20all%20inductive%20types%20enumerable%3F/near/130696864):
it would solve Q4 of my questions lol

#### [Kenny Lau (Aug 01 2018 at 08:56)](https://leanprover.zulipchat.com/#narrow/stream/113488-general/topic/Are%20all%20inductive%20types%20enumerable%3F/near/130696907):
https://leanprover.zulipchat.com/#narrow/stream/113488-general/subject/Lean.20assignment.20from.20Kenny/near/130567187

#### [Mario Carneiro (Aug 01 2018 at 08:56)](https://leanprover.zulipchat.com/#narrow/stream/113488-general/topic/Are%20all%20inductive%20types%20enumerable%3F/near/130696921):
You can prove finite trees are enumerable by using `denumerable (list A)` recursively

