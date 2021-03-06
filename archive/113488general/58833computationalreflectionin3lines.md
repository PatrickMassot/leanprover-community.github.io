---
layout: page
title: Lean Prover Zulip Chat Archive 
permalink: archive/113488general/58833computationalreflectionin3lines.html
---

## [general](index.html)
### [computational reflection in 3 lines](58833computationalreflectionin3lines.html)

#### [Mario Carneiro (Jun 25 2018 at 11:10)](https://leanprover.zulipchat.com/#narrow/stream/113488-general/topic/computational%20reflection%20in%203%20lines/near/128590733):
I managed to write a mini `norm_num` using computational reflection in only a few basic tactics:
```
import data.num.lemmas
example : 12402536340 * 2356324602 = 29224401505141036680 :=
begin
  rw ← num.of_nat_inj,
  simp [num.bit0_of_bit0, num.bit1_of_bit1],
  refl
end
```

#### [Mario Carneiro (Jun 25 2018 at 11:10)](https://leanprover.zulipchat.com/#narrow/stream/113488-general/topic/computational%20reflection%20in%203%20lines/near/128590737):
(The original theorem is on `nat`, so a straight `rfl` proof times out)

#### [Kevin Buzzard (Jun 25 2018 at 11:15)](https://leanprover.zulipchat.com/#narrow/stream/113488-general/topic/computational%20reflection%20in%203%20lines/near/128590887):
That is very cool :-)

#### [Johan Commelin (Jun 25 2018 at 12:56)](https://leanprover.zulipchat.com/#narrow/stream/113488-general/topic/computational%20reflection%20in%203%20lines/near/128594312):
Cool! Now we can start porting Sage to Lean!

#### [Johan Commelin (Jun 25 2018 at 12:57)](https://leanprover.zulipchat.com/#narrow/stream/113488-general/topic/computational%20reflection%20in%203%20lines/near/128594317):
Do some serious algebraic number theory.

