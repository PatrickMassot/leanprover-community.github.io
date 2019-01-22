---
layout: page
title: Lean Prover Zulip Chat Archive 
permalink: archive/116395maths/31797centreofpartialorderclosedundersupremum.html
---

## [maths](index.html)
### [centre of partial order closed under supremum?](31797centreofpartialorderclosedundersupremum.html)

#### [Kenny Lau (Apr 28 2018 at 17:43)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/centre of partial order closed under supremum?/near/125823474):
Let (P, <=) be a partially ordered set.

Say an element x in P is in the "centre" of P if for every y in P we have x <= y or y <= x.
Is the supremum of a collection of elements in the centre of P also necessarily in the centre of P, assuming that the supremum exists?

#### [Kenny Lau (Apr 28 2018 at 17:44)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/centre of partial order closed under supremum?/near/125823514):
And is this equivalent to LEM?

#### [Kenny Lau (Apr 28 2018 at 17:44)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/centre of partial order closed under supremum?/near/125823516):
it seems true to me but I have no idea how to prove it

#### [Mario Carneiro (Apr 28 2018 at 22:28)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/centre of partial order closed under supremum?/near/125830606):
Here's a proof assuming LEM:
```
import logic.basic

variables {α : Type*} [partial_order α]

def is_sup (S : set α) (a : α) : Prop :=
∀ b, a ≤ b ↔ ∀ s ∈ S, s ≤ b

def center (α) [partial_order α] : set α :=
{ a | ∀ b, a ≤ b ∨ b ≤ a }

example {S} (H : S ⊆ center α) {a} (hs : is_sup S a) :
  a ∈ center α :=
by haveI := classical.dec; exact
λ b,
  if h : ∀ s ∈ S, s ≤ b then or.inl ((hs _).2 h) else
  let ⟨c, sc, hc⟩ := not_ball.1 h in
  or.inr $ le_trans
    ((H sc _).resolve_left hc)
    ((hs _).1 (le_refl _) _ sc)
```
