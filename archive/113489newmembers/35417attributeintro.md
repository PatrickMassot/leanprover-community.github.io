---
layout: page
title: Lean Prover Zulip Chat Archive 
permalink: archive/113489newmembers/35417attributeintro.html
---

## [new members](index.html)
### [attribute [intro]](35417attributeintro.html)

#### [Kenny Lau (Oct 19 2018 at 02:01)](https://leanprover.zulipchat.com/#narrow/stream/113489-new%20members/topic/attribute%20%5Bintro%5D/near/136080016):
What does this attribute do? I saw it here:
```lean
inductive Exists {α : Sort u} (p : α → Prop) : Prop
| intro (w : α) (h : p w) : Exists

attribute [intro] Exists.intro
```
and when I hover it says "introduction rule for backward chaining"

