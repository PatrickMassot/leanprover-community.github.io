---
layout: page
title: Lean Prover Zulip Chat Archive 
permalink: archive/113488general/88037equivbetweensubsingletons.html
---

## [general](index.html)
### [equiv between subsingletons](88037equivbetweensubsingletons.html)

#### [Johan Commelin (Nov 17 2018 at 09:09)](https://leanprover.zulipchat.com/#narrow/stream/113488-general/topic/equiv%20between%20subsingletons/near/147869242):
I want to prove an equiv between two subsingletons. Is there a little lemma in mathlib that says I don't have to check that the compositions are the identity?

#### [Kenny Lau (Nov 17 2018 at 09:59)](https://leanprover.zulipchat.com/#narrow/stream/113488-general/topic/equiv%20between%20subsingletons/near/147870493):
subsingleton.elim?

#### [Johan Commelin (Nov 17 2018 at 10:04)](https://leanprover.zulipchat.com/#narrow/stream/113488-general/topic/equiv%20between%20subsingletons/near/147870671):
That doesn't do exactly what I want, right? I could use it, but it would lead to an obfuscated proof of something that is math-trivial anyway.

