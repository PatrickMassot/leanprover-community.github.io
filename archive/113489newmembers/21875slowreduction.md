---
layout: page
title: Lean Prover Zulip Chat Archive 
permalink: archive/113489newmembers/21875slowreduction.html
---

## [new members](index.html)
### [slow reduction](21875slowreduction.html)

#### [Scott Olson (Sep 28 2018 at 02:26)](https://leanprover.zulipchat.com/#narrow/stream/113489-new%20members/topic/slow%20reduction/near/134782780):
I have a `#reduce` that's leading to "(deterministic) timeout" and I'm wondering what I can do to find out what's taking so long. Can I `#reduce` step-by-step?

#### [Mario Carneiro (Sep 28 2018 at 02:46)](https://leanprover.zulipchat.com/#narrow/stream/113489-new%20members/topic/slow%20reduction/near/134783570):
Unfortunately no. `#reduce` is not really intended for serious use

#### [Mario Carneiro (Sep 28 2018 at 02:46)](https://leanprover.zulipchat.com/#narrow/stream/113489-new%20members/topic/slow%20reduction/near/134783577):
It turns out that unfolding a proof down to axioms is actually kind of expensive :)

#### [Scott Olson (Sep 28 2018 at 02:48)](https://leanprover.zulipchat.com/#narrow/stream/113489-new%20members/topic/slow%20reduction/near/134783646):
Hmm, well it's also breaking my examples/tests, since it can't even prove things by `rfl` at very small input sizes, and I can't figure out why, because the code seems fairly straightforward.

#### [Mario Carneiro (Sep 28 2018 at 02:49)](https://leanprover.zulipchat.com/#narrow/stream/113489-new%20members/topic/slow%20reduction/near/134783655):
this is also not unusual

#### [Mario Carneiro (Sep 28 2018 at 02:49)](https://leanprover.zulipchat.com/#narrow/stream/113489-new%20members/topic/slow%20reduction/near/134783660):
I think `theorem nat.prime 5 := dec_trivial` times out

#### [Mario Carneiro (Sep 28 2018 at 02:50)](https://leanprover.zulipchat.com/#narrow/stream/113489-new%20members/topic/slow%20reduction/near/134783706):
it depends on what numerical functions you are calling

#### [Scott Olson (Sep 28 2018 at 02:50)](https://leanprover.zulipchat.com/#narrow/stream/113489-new%20members/topic/slow%20reduction/near/134783720):
I guess it would be nice to have bytecode-based tests for quick dumb sanity checks

#### [Mario Carneiro (Sep 28 2018 at 02:51)](https://leanprover.zulipchat.com/#narrow/stream/113489-new%20members/topic/slow%20reduction/near/134783731):
You should use `#eval` for that

#### [Scott Olson (Sep 28 2018 at 02:51)](https://leanprover.zulipchat.com/#narrow/stream/113489-new%20members/topic/slow%20reduction/near/134783741):
I do, I just wish I could write something that asserts on the result rather than simply printing it

#### [Mario Carneiro (Sep 28 2018 at 03:06)](https://leanprover.zulipchat.com/#narrow/stream/113489-new%20members/topic/slow%20reduction/near/134784254):
you can use `run_cmd`: 
```
run_cmd guard (2 + 2 = 4)
run_cmd guard (2 + 2 = 5) -- failed
```

#### [Scott Olson (Sep 28 2018 at 03:07)](https://leanprover.zulipchat.com/#narrow/stream/113489-new%20members/topic/slow%20reduction/near/134784267):
Perfect, thanks!

