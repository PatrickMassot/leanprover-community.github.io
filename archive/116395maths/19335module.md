---
layout: page
title: Lean Prover Zulip Chat Archive 
permalink: archive/116395maths/19335module.html
---

## [maths](index.html)
### [module](19335module.html)

#### [Johan Commelin (Nov 23 2018 at 13:49)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/module/near/148227117):
@**Mario Carneiro** Shouldn't this be flipped, for consistency with `comp` and `llcomp`?
```lean
def lcomp (f : M →ₗ N) : (N →ₗ P) →ₗ M →ₗ P := _ -- I would expect:   def lcomp (f : N →ₗ P) : (M →ₗ N) →ₗ M →ₗ P :=
```

#### [Mario Carneiro (Nov 23 2018 at 13:50)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/module/near/148227175):
maybe, but the other direction is harder

#### [Mario Carneiro (Nov 23 2018 at 13:50)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/module/near/148227185):
there is an order to the definitions

#### [Johan Commelin (Nov 23 2018 at 13:50)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/module/near/148227192):
Also, are there compatibilities between `comp` and `lcomp` etc...? Is `(lcomp f).to_fun` defeq to `f.comp`?

#### [Mario Carneiro (Nov 23 2018 at 13:50)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/module/near/148227195):
yeah, it's all defeq

#### [Mario Carneiro (Nov 23 2018 at 13:50)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/module/near/148227203):
it's just composition so it's easy

#### [Mario Carneiro (Nov 23 2018 at 13:52)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/module/near/148227283):
also there is a difference between `lcomp` that is there and the one you said

#### [Mario Carneiro (Nov 23 2018 at 13:52)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/module/near/148227284):
one is precomposition and the other is postcomposition

#### [Johan Commelin (Nov 23 2018 at 14:07)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/module/near/148228046):
Right, and I think the library isn't completely consistent about which one it uses for `comp`, `lcomp` and `llcomp`. Wouldn't it be easier if they were all post-composition?

#### [Mario Carneiro (Nov 23 2018 at 14:09)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/module/near/148228136):
I mean there is a need for it, I didn't write that for no reason

#### [Mario Carneiro (Nov 23 2018 at 14:09)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/module/near/148228156):
it's used before we have tensor products and swap and eval and such, so they aren't yet interchangeable

#### [Johan Commelin (Nov 23 2018 at 14:10)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/module/near/148228209):
Ok, I see

#### [Johan Commelin (Nov 23 2018 at 14:10)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/module/near/148228225):
So, may I then complain that the name is slightly confusing?

#### [Mario Carneiro (Nov 23 2018 at 14:10)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/module/near/148228232):
`rcomp` :)

#### [Johan Commelin (Nov 23 2018 at 18:23)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/module/near/148241025):
@**Mario Carneiro** I couldn't find where the zero linear map is defined, but apparently it is somewhere. However `⇑0 m` doesn't `simp` to `0`. Where should I add this simp rule?

