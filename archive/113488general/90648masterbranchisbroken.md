---
layout: page
title: Lean Prover Zulip Chat Archive 
permalink: archive/113488general/90648masterbranchisbroken.html
---

## [general](index.html)
### [master branch is broken](90648masterbranchisbroken.html)

#### [Scott Morrison (Oct 07 2018 at 08:07)](https://leanprover.zulipchat.com/#narrow/stream/113488-general/topic/master%20branch%20is%20broken/near/135340328):
Ugh, `master` is broken in mathlib.

#### [Scott Morrison (Oct 07 2018 at 08:07)](https://leanprover.zulipchat.com/#narrow/stream/113488-general/topic/master%20branch%20is%20broken/near/135340329):
```
arguta:mathlib scott$ git status
On branch master
Your branch is up-to-date with 'origin/master'.

nothing to commit, working tree clean
arguta:mathlib scott$ lean --make tests/tactics.lean 
/Users/scott/projects/lean/mathlib/tests/tactics.lean:641:2: error: is_def_eq tactic failed, the following expressions are not definitionally equal (remark: is_def_eq tactic does modify the metavariable assignment)
  p : Prop
and
  s : Prop
state:
p q r s : Prop,
h₀ : p ↔ q,
h₁ : q ↔ r,
h₂ : r ↔ s
⊢ p ↔ s
```

#### [Scott Morrison (Oct 07 2018 at 08:07)](https://leanprover.zulipchat.com/#narrow/stream/113488-general/topic/master%20branch%20is%20broken/near/135340330):
(I spent 20 minutes trying to work out how my branch had broken something, before realising it wasn't my fault.)

#### [Simon Hudon (Oct 07 2018 at 08:08)](https://leanprover.zulipchat.com/#narrow/stream/113488-general/topic/master%20branch%20is%20broken/near/135340368):
My bad. we should comment out those tests while I'm fixing that tactic

#### [Simon Hudon (Oct 07 2018 at 08:14)](https://leanprover.zulipchat.com/#narrow/stream/113488-general/topic/master%20branch%20is%20broken/near/135340518):
@**Mario Carneiro** Can you comment out these test cases please?

#### [Mario Carneiro (Oct 07 2018 at 08:15)](https://leanprover.zulipchat.com/#narrow/stream/113488-general/topic/master%20branch%20is%20broken/near/135340525):
eh, can you PR it? It takes me an hour to move to and from `module` branch

#### [Simon Hudon (Oct 07 2018 at 08:22)](https://leanprover.zulipchat.com/#narrow/stream/113488-general/topic/master%20branch%20is%20broken/near/135340729):
Here you go: https://github.com/leanprover/mathlib/pull/398

