---
layout: page
title: Lean Prover Zulip Chat Archive 
permalink: archive/113488general/56418Tactichelp.html
---

## [general](index.html)
### [Tactic help](56418Tactichelp.html)

#### [Koundinya Vajjha (Jan 02 2019 at 17:54)](https://leanprover.zulipchat.com/#narrow/stream/113488-general/topic/Tactic%20help/near/154186308):
Hi, in order to get familiar with writing tactics, I am trying to write a simple tactic to count the number of occurrences of `∅` in a goal. Here is what I have so far:

```lean
meta def is_empty' : expr → bool 
| `(has_emptyc.emptyc _) := tt
| _ := ff

meta def list_emptys' (e : expr) : list expr :=
e.fold [] 
(λ e' _ es, if (is_empty' e') then insert e' es else es)

meta def find_empty : tactic unit := 
do e ← tactic.target,
tactic.trace $ (list_emptys' e) 
```
But if I run this tactic
```lean
universe u
example {s : Type u} (a b : set s) : ∅ ∩ ∅ = a :=
begin
find_empty,
end
```
I only get `[∅]`. Can someone help me figure out what I am doing wrong? I'm guessing it's me not understanding how `fold` works for `expr`...

#### [Mario Carneiro (Jan 02 2019 at 18:23)](https://leanprover.zulipchat.com/#narrow/stream/113488-general/topic/Tactic%20help/near/154187855):
you used `insert` to accumulate the list, this removes duplicates

#### [Mario Carneiro (Jan 02 2019 at 18:23)](https://leanprover.zulipchat.com/#narrow/stream/113488-general/topic/Tactic%20help/near/154187873):
and the only thing you ever put in the list is `∅` (twice)

#### [Mario Carneiro (Jan 02 2019 at 18:24)](https://leanprover.zulipchat.com/#narrow/stream/113488-general/topic/Tactic%20help/near/154187929):
use `::` instead

#### [Koundinya Vajjha (Jan 02 2019 at 18:25)](https://leanprover.zulipchat.com/#narrow/stream/113488-general/topic/Tactic%20help/near/154187975):
Aha! that worked. Thanks @**Mario Carneiro**

#### [Kenny Lau (Jan 02 2019 at 18:33)](https://leanprover.zulipchat.com/#narrow/stream/113488-general/topic/Tactic%20help/near/154188502):
anticlimax...

#### [Johan Commelin (Jan 02 2019 at 19:25)](https://leanprover.zulipchat.com/#narrow/stream/113488-general/topic/Tactic%20help/near/154191437):
@**Koundinya Vajjha** Have you seen https://github.com/leanprover/mathlib/blob/master/docs/extras/tactic_writing.md? I have no idea about your level of experience with Lean or other programming languages. But for mathematicians who have never written anything in a functional programming language before, I think this is a very good introduction.

