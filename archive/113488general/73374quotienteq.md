---
layout: page
title: Lean Prover Zulip Chat Archive 
permalink: archive/113488general/73374quotienteq.html
---

## [general](index.html)
### [quotient.eq](73374quotienteq.html)

#### [Patrick Massot (Dec 15 2018 at 19:31)](https://leanprover.zulipchat.com/#narrow/stream/113488-general/topic/quotient.eq/near/151846739):
We have 
```lean
@[simp] theorem quotient.eq [r : setoid α] {x y : α} : ⟦x⟧ = ⟦y⟧ ↔ x ≈ y :=
⟨quotient.exact, quotient.sound⟩
```
Are we sure this is a good simp lemma?

