---
layout: page
title: Lean Prover Zulip Chat Archive 
permalink: archive/113488general/21444natstrongrecon.html
---

## [general](index.html)
### [nat.strong_rec_on](21444natstrongrecon.html)

#### [Kenny Lau (Sep 14 2018 at 19:04)](https://leanprover.zulipchat.com/#narrow/stream/113488-general/topic/nat.strong_rec_on/near/133965949):
Can we make this `@[elab_as_eliminator]`?

#### [Kevin Buzzard (Sep 14 2018 at 20:09)](https://leanprover.zulipchat.com/#narrow/stream/113488-general/topic/nat.strong_rec_on/near/133969734):
How will that change things?

#### [Chris Hughes (Sep 14 2018 at 20:11)](https://leanprover.zulipchat.com/#narrow/stream/113488-general/topic/nat.strong_rec_on/near/133969852):
It means it changes the way the motive is inferred, without which, these lemmas are pretty much unusable.

#### [Kenny Lau (Sep 14 2018 at 20:22)](https://leanprover.zulipchat.com/#narrow/stream/113488-general/topic/nat.strong_rec_on/near/133970442):
also I just wrote a beta lemma

#### [Kenny Lau (Sep 14 2018 at 20:22)](https://leanprover.zulipchat.com/#narrow/stream/113488-general/topic/nat.strong_rec_on/near/133970444):
```lean
attribute [elab_as_eliminator] nat.strong_rec_on

@[simp] lemma nat.strong_rec_on_beta {p : nat → Sort*} (n : nat) (h : ∀ n, (∀ m, m < n → p m) → p n) :
  (nat.strong_rec_on n h : p n) = h n (λ m H, nat.strong_rec_on m h) :=
begin
  cases n with n,
  { dsimp only [nat.strong_rec_on, or.by_cases],
    rw [dif_neg (lt_irrefl _), dif_pos rfl],
    congr' 1, funext m H, cases H },
  dsimp only [nat.strong_rec_on, or.by_cases],
  rw [dif_neg (lt_irrefl _), dif_pos rfl],
  congr' 1, funext m H,
  cases H with H1 H1,
  { rw [dif_neg (lt_irrefl _)] },
  change m < n at H1,
  rw [dif_pos H1, dif_neg (lt_irrefl _), dif_pos rfl],
  clear H, revert m H1,
  apply nat.strong_induction_on n,
  intros n ih m H1,
  cases n with n,
  { cases H1 },
  dsimp only,
  by_cases H2 : m < n,
  { rw [dif_pos H2], apply ih, exact nat.lt_succ_self _ },
  by_cases H3 : m = n,
  { rw [dif_neg H2, dif_pos H3], subst H3 },
  exact false.elim (or.elim (nat.lt_succ_iff_lt_or_eq.1 H1) H2 H3)
end
```

