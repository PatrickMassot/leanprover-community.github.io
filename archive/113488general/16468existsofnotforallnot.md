---
layout: page
title: Lean Prover Zulip Chat Archive 
permalink: archive/113488general/16468existsofnotforallnot.html
---

## [general](index.html)
### [exists_of_not_forall_not](16468existsofnotforallnot.html)

#### [Kevin Buzzard (Mar 10 2018 at 15:49)](https://leanprover.zulipchat.com/#narrow/stream/113488-general/topic/exists_of_not_forall_not/near/123536960):
I am a classical guy. Is `example (α : Type) (P : α → Prop) : (¬ (∀ a : α, ¬ P a)) → (∃ a : α, P a) := sorry` already in Lean or mathlib?

#### [Andrew Ashworth (Mar 10 2018 at 15:59)](https://leanprover.zulipchat.com/#narrow/stream/113488-general/topic/exists_of_not_forall_not/near/123537206):
some variant is in mathlib, see `not_forall` and the lemmas near it in `logic/basic.lean`

#### [Kevin Buzzard (Mar 10 2018 at 16:52)](https://leanprover.zulipchat.com/#narrow/stream/113488-general/topic/exists_of_not_forall_not/near/123538465):
Thanks. My mistake was searching for exists_of rather than concentrating on not_forall...

#### [Chris Hughes (Mar 10 2018 at 17:31)](https://leanprover.zulipchat.com/#narrow/stream/113488-general/topic/exists_of_not_forall_not/near/123539394):
```quote
Thanks. My mistake was searching for exists_of rather than concentrating on not_forall...
```
I thought the convention was that lemmas should be named after their conclusion.

#### [Kevin Buzzard (Mar 10 2018 at 18:12)](https://leanprover.zulipchat.com/#narrow/stream/113488-general/topic/exists_of_not_forall_not/near/123540476):
Yes but the lemma in the library was an iff ;-)

