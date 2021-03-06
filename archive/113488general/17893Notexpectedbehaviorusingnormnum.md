---
layout: page
title: Lean Prover Zulip Chat Archive 
permalink: archive/113488general/17893Notexpectedbehaviorusingnormnum.html
---

## [general](index.html)
### [Not expected behavior using norm_num](17893Notexpectedbehaviorusingnormnum.html)

#### [Bruno Bentzen (Dec 21 2018 at 03:02)](https://leanprover.zulipchat.com/#narrow/stream/113488-general/topic/Not%20expected%20behavior%20using%20norm_num/near/152302446):
Hi everyone,

I have a bare project (with mathlib imported) in which the following code

````
import data.nat.prime  tactic.norm_num

lemma prime_seven : nat.prime (7 : ℕ) := by
norm_num
````

displays the error 'norm_num failed to simplify'. Does it work for you?

Best,
Bruno

#### [Bryan Gin-ge Chen (Dec 21 2018 at 03:08)](https://leanprover.zulipchat.com/#narrow/stream/113488-general/topic/Not%20expected%20behavior%20using%20norm_num/near/152302655):
I get no errors on my system. What version of mathlib are you using? Do other primes like 2, 3 work?

#### [Mario Carneiro (Dec 21 2018 at 03:12)](https://leanprover.zulipchat.com/#narrow/stream/113488-general/topic/Not%20expected%20behavior%20using%20norm_num/near/152302857):
If you click on `norm_num` to go to the definition, search in that file for a function called `eval_prime`

#### [Mario Carneiro (Dec 21 2018 at 03:13)](https://leanprover.zulipchat.com/#narrow/stream/113488-general/topic/Not%20expected%20behavior%20using%20norm_num/near/152302868):
If you don't have it, chances are you are running an old version of mathlib

#### [Bryan Gin-ge Chen (Dec 21 2018 at 03:13)](https://leanprover.zulipchat.com/#narrow/stream/113488-general/topic/Not%20expected%20behavior%20using%20norm_num/near/152302883):
Oh, is this the 3.4.1 branch issue again?

#### [Mario Carneiro (Dec 21 2018 at 03:13)](https://leanprover.zulipchat.com/#narrow/stream/113488-general/topic/Not%20expected%20behavior%20using%20norm_num/near/152302890):
oh, that might be it

#### [Mario Carneiro (Dec 21 2018 at 03:15)](https://leanprover.zulipchat.com/#narrow/stream/113488-general/topic/Not%20expected%20behavior%20using%20norm_num/near/152302964):
go into `_target/deps/mathlib` and `git checkout master` then `lean --make` (which will take a while)

#### [Bruno Bentzen (Dec 21 2018 at 03:15)](https://leanprover.zulipchat.com/#narrow/stream/113488-general/topic/Not%20expected%20behavior%20using%20norm_num/near/152302974):
yeah, no `eval_prime`. Then I should be really using an old version of it.

#### [Bruno Bentzen (Dec 21 2018 at 03:21)](https://leanprover.zulipchat.com/#narrow/stream/113488-general/topic/Not%20expected%20behavior%20using%20norm_num/near/152303187):
Thanks! I'm fixing the build, I think it should work now.

#### [Bruno Bentzen (Dec 21 2018 at 03:59)](https://leanprover.zulipchat.com/#narrow/stream/113488-general/topic/Not%20expected%20behavior%20using%20norm_num/near/152304585):
It works now. Thanks, Bryan and Mario!

