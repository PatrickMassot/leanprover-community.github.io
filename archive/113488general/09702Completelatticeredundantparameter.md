---
layout: page
title: Lean Prover Zulip Chat Archive 
permalink: archive/113488general/09702Completelatticeredundantparameter.html
---

## [general](index.html)
### [Complete lattice redundant parameter](09702Completelatticeredundantparameter.html)

#### [Kenny Lau (Mar 31 2018 at 08:52)](https://leanprover.zulipchat.com/#narrow/stream/113488-general/topic/Complete%20lattice%20redundant%20parameter/near/124445675):
Isn't bot and top provable from supremum and infimum, respectively?

#### [Mario Carneiro (Mar 31 2018 at 09:15)](https://leanprover.zulipchat.com/#narrow/stream/113488-general/topic/Complete%20lattice%20redundant%20parameter/near/124446222):
Yes, and `Sup` is definable from `Inf`, and `sup` is definable from `Sup`. The reason these additional definitions are in the structure is that sometimes you want a different definitional reduction for the expression than the lattice definition gives you, i.e. `Prop` is a complete lattice with top `true`, but if it was defined with `Sup` then that would be some cumbersome forall false thing

