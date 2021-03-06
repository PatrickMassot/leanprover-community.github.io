---
layout: page
title: Lean Prover Zulip Chat Archive 
permalink: archive/116395maths/10127ChurchNumeralPuzzles.html
---

## [maths](index.html)
### [Church Numeral Puzzles](10127ChurchNumeralPuzzles.html)

#### [Kevin Buzzard (May 02 2018 at 21:55)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/Church%20Numeral%20Puzzles/near/126010843):
I am trying to understand church numerals by writing a collection of basic theorems about them.

#### [Kevin Buzzard (May 02 2018 at 21:55)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/Church%20Numeral%20Puzzles/near/126010845):
I just solved this one:

#### [Kevin Buzzard (May 02 2018 at 21:56)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/Church%20Numeral%20Puzzles/near/126010886):
```lean
def chℕ := Π X : Type, (X → X) → X → X

namespace chnat 

open nat

definition to_nat : chℕ → ℕ := λ m, m ℕ nat.succ 0 

def of_nat : ℕ → chℕ 
| (zero) := λ X f x, x
| (succ n) := λ X f x, f (of_nat n X f x) -- f (f^n x)

definition of_nat' : ℕ → chℕ 
| 0 := λ X f x, x
| (n + 1) := λ X f x, of_nat' n X f (f x) -- f^n (f x)

theorem of_nat_is_of_nat' (n : ℕ) : of_nat n = of_nat' n := sorry 

end chnat
```

#### [Kevin Buzzard (May 02 2018 at 21:57)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/Church%20Numeral%20Puzzles/near/126010904):
it was harder than I expected though, so I probably missed a trick, which is why I mention it here.

#### [Gabriel Ebner (May 02 2018 at 22:06)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/Church%20Numeral%20Puzzles/near/126011292):
Hmm, this was a pretty straightforward induction:
```lean
theorem of_nat_is_of_nat' (n : ℕ) : of_nat n = of_nat' n :=
begin
induction n with n; funext X f x; simp! *,
clear n_ih, induction n generalizing x; simp! *,
end
```

#### [Kevin Buzzard (May 02 2018 at 22:33)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/Church%20Numeral%20Puzzles/near/126012437):
This is the key lemma I've been after:

#### [Kevin Buzzard (May 02 2018 at 22:33)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/Church%20Numeral%20Puzzles/near/126012439):
```lean
lemma of_nat_functorial (n : ℕ) (X Y : Type) (a : X → Y) (f : X → X) : ∀ x, 
a (of_nat n X f x) = @of_nat n (X → Y) (λ g x', g (f x')) a x := 
```

#### [Kevin Buzzard (May 02 2018 at 22:35)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/Church%20Numeral%20Puzzles/near/126012493):
I have never used `generalizing` or `simp!` before.

#### [Kevin Buzzard (May 02 2018 at 22:35)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/Church%20Numeral%20Puzzles/near/126012503):
So thanks very much for these!

#### [Kevin Buzzard (May 02 2018 at 22:35)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/Church%20Numeral%20Puzzles/near/126012504):
@**Gabriel Ebner**

#### [Kevin Buzzard (May 02 2018 at 22:36)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/Church%20Numeral%20Puzzles/near/126012553):
I also have this:

#### [Kevin Buzzard (May 02 2018 at 22:36)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/Church%20Numeral%20Puzzles/near/126012554):
`example (m n : ℕ) : of_nat (m + n) = of_nat m + of_nat n := sorry`

#### [Chris Hughes (May 02 2018 at 22:47)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/Church%20Numeral%20Puzzles/near/126012995):
```lean
lemma of_nat_functorial : ∀ (n : ℕ) (X Y : Type) (a : X → Y) (f : X → X) (x : X),
a (of_nat n X f x) = @of_nat n (X → Y) (λ g x', g (f x')) a x
| 0 := by intros; refl
| (n+1) := begin
  assume X Y a f x,
  rw [of_nat],
  dsimp,
  rw ← of_nat_functorial,
  dsimp,
   apply congr_arg,
   clear of_nat_functorial,
   induction n with n ih generalizing x,
   refl,
   rw of_nat,
   dsimp,
   rw ih,
end
```

#### [Chris Hughes (May 02 2018 at 22:47)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/Church%20Numeral%20Puzzles/near/126013010):
Not the cleanest, but done.

#### [Gabriel Ebner (May 02 2018 at 22:58)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/Church%20Numeral%20Puzzles/near/126013555):
These lemmas are all induction+simp, if you set them up correctly:
```lean
instance: has_add chℕ := ⟨λ a b X f, a _ f ∘ b _ f⟩
@[simp] lemma chℕ_add (a b : chℕ) : a + b = (λ X f, a _ f ∘ b _ f) := rfl

@[simp] lemma of_nat_f (n X f x) : of_nat n X f (f x) = f (of_nat n X f x) :=
by induction n generalizing x; simp! *

local attribute [-simp] add_comm
lemma of_nat_add  (m n : ℕ) : of_nat (m + n) = of_nat m + of_nat n :=
by induction n with n generalizing m; funext X f x; simp [of_nat, *]
```

#### [Gabriel Ebner (May 02 2018 at 23:00)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/Church%20Numeral%20Puzzles/near/126013667):
Unfortunately you can't orient `of_nat_f` the other way around because it won't work as a simp lemma then.

#### [Kevin Buzzard (May 02 2018 at 23:34)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/Church%20Numeral%20Puzzles/near/126015189):
Thanks so much Gabriel!

#### [Kevin Buzzard (May 03 2018 at 00:12)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/Church%20Numeral%20Puzzles/near/126016767):
These proofs are really cool :-)

#### [Kevin Buzzard (May 03 2018 at 00:13)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/Church%20Numeral%20Puzzles/near/126016801):
I understand better the way you think about the question now. I want to prove all the intermediate lemmas first, because historically I have been trained to go forwards. You just keep reducing the problem to simpler statements by induction because dependent type theory is somehow better at pushing backwards.

#### [Kevin Buzzard (May 03 2018 at 00:16)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/Church%20Numeral%20Puzzles/near/126016926):
The one with `clear n_ih` is interesting!

#### [Kevin Buzzard (May 03 2018 at 00:26)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/Church%20Numeral%20Puzzles/near/126017263):
```lean
def pow : chℕ → chℕ → chℕ :=
λ m n, λ X f x,
  n (X → X) (λ g, (m X g)) f x
theorem of_nat_pow (m n : ℕ) : of_nat (m + n) = of_nat m + of_nat n := sorry 

```

#### [Mario Carneiro (May 03 2018 at 00:28)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/Church%20Numeral%20Puzzles/near/126017321):
I think the proof is `of_nat_add _ _` :)

#### [Kevin Buzzard (May 03 2018 at 00:28)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/Church%20Numeral%20Puzzles/near/126017327):
wait a second

#### [Kevin Buzzard (May 03 2018 at 00:29)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/Church%20Numeral%20Puzzles/near/126017334):
```lean
def chℕ := Π X : Type, (X → X) → X → X

namespace chnat 

open nat

definition to_nat : chℕ → ℕ := λ m, m ℕ nat.succ 0 

def of_nat : ℕ → chℕ 
| (zero) := λ X f x, x
| (succ n) := λ X f x, f (of_nat n X f x) -- f (f^n x)

def pow : chℕ → chℕ → chℕ :=
λ m n, λ X f x,
  n (X → X) (λ g, (m X g)) f x
theorem of_nat_pow (m n : ℕ) : of_nat (m ^ n) = pow (of_nat m) (of_nat n) := sorry


end chnat
```

#### [Kevin Buzzard (May 03 2018 at 00:29)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/Church%20Numeral%20Puzzles/near/126017344):
I think that runs and asks the question I want to ask :-)

#### [Kenny Lau (May 03 2018 at 00:29)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/Church%20Numeral%20Puzzles/near/126017350):
I thought I already proved it

#### [Kevin Buzzard (May 03 2018 at 00:29)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/Church%20Numeral%20Puzzles/near/126017353):
Can you golf it though?

#### [Kenny Lau (May 03 2018 at 00:29)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/Church%20Numeral%20Puzzles/near/126017355):
...

#### [Kevin Buzzard (May 03 2018 at 00:29)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/Church%20Numeral%20Puzzles/near/126017360):
Did you see Gabriel's proofs?

#### [Mario Carneiro (May 03 2018 at 00:31)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/Church%20Numeral%20Puzzles/near/126017446):
```lean
def chℕ := Π X : Type, (X → X) → X → X

namespace chnat

open nat

def to_nat (m : chℕ) : ℕ := m ℕ nat.succ 0

def of_nat : ℕ → chℕ
| (zero) X f x := x
| (succ n) X f x := f (of_nat n X f x) -- f (f^n x)

def pow (m n : chℕ) : chℕ
| X f x := n (X → X) (m X) f x

theorem of_nat_pow (m n : ℕ) : of_nat (m ^ n) = pow (of_nat m) (of_nat n) :=
sorry

end chnat
```
golfed

#### [Kenny Lau (May 03 2018 at 00:32)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/Church%20Numeral%20Puzzles/near/126017509):
...

#### [Kevin Buzzard (May 03 2018 at 00:35)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/Church%20Numeral%20Puzzles/near/126017581):
Mario I guess that in reality I am more interested in the style. Is yours both preferable and golfier? Ultimately I want to write good style Lean.

#### [Kenny Lau (May 03 2018 at 00:37)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/Church%20Numeral%20Puzzles/near/126017660):
I wouldn't prefer it

#### [Kevin Buzzard (May 03 2018 at 00:37)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/Church%20Numeral%20Puzzles/near/126017666):
ooh the `lam g` on my part was a rookie error

#### [Kenny Lau (May 03 2018 at 00:37)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/Church%20Numeral%20Puzzles/near/126017667):
you see, it uses the equation compiler

#### [Kenny Lau (May 03 2018 at 00:37)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/Church%20Numeral%20Puzzles/near/126017674):
and uses "external" definitional equality

#### [Kenny Lau (May 03 2018 at 00:38)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/Church%20Numeral%20Puzzles/near/126017718):
like it isn't "expressionally equal" but somehow they made it definitionally equal (by all those ._equation_1) thing

#### [Kenny Lau (May 03 2018 at 00:38)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/Church%20Numeral%20Puzzles/near/126017719):
do `#print prefix chnat.pow` to see what I mean

#### [Mario Carneiro (May 03 2018 at 00:39)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/Church%20Numeral%20Puzzles/near/126017740):
huh? There is no fancy business in any of the definitions except `of_nat`, but that was already defined by eqn compiler

#### [Kenny Lau (May 03 2018 at 00:40)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/Church%20Numeral%20Puzzles/near/126017781):
hmm...

#### [Kenny Lau (May 03 2018 at 00:40)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/Church%20Numeral%20Puzzles/near/126017791):
they don't do `._main` if you don't have two cases?

#### [Mario Carneiro (May 03 2018 at 00:40)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/Church%20Numeral%20Puzzles/near/126017800):
the eqn compiler always produces `._main` I guess

#### [Mario Carneiro (May 03 2018 at 00:40)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/Church%20Numeral%20Puzzles/near/126017804):
for uniformity I assume

#### [Kenny Lau (May 03 2018 at 00:43)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/Church%20Numeral%20Puzzles/near/126017880):
I don't like main

#### [Kenny Lau (May 03 2018 at 00:44)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/Church%20Numeral%20Puzzles/near/126017922):
as a sidenote now I prefer `trans_rel_left` over `calc` lol

#### [Kenny Lau (May 03 2018 at 00:44)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/Church%20Numeral%20Puzzles/near/126017924):
because _ with the tactics

#### [Kevin Buzzard (May 03 2018 at 00:45)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/Church%20Numeral%20Puzzles/near/126017938):
Oh you're right Kenny. So Mario does this  mean that the lambda style is preferred in practice?

#### [Kenny Lau (May 03 2018 at 00:46)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/Church%20Numeral%20Puzzles/near/126017985):
I think Mario prefers the equation compiler because it looks nicer

#### [Mario Carneiro (May 03 2018 at 00:46)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/Church%20Numeral%20Puzzles/near/126017988):
I always locally optimize `def T : A -> B := \lam x, t` =>  `def T (x : A) : B := t`

#### [Mario Carneiro (May 03 2018 at 00:47)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/Church%20Numeral%20Puzzles/near/126017995):
and `def T : B := \lam x, t` => `def T : B | x := t`

#### [Kenny Lau (May 03 2018 at 00:47)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/Church%20Numeral%20Puzzles/near/126018003):
what next, `\la x, A $ B x` => `A \o B`?

#### [Kenny Lau (May 03 2018 at 00:48)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/Church%20Numeral%20Puzzles/near/126018043):
does your optimization have church rosser?

#### [Mario Carneiro (May 03 2018 at 00:48)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/Church%20Numeral%20Puzzles/near/126018044):
that one depends on whether the \o gets in the way later

#### [Mario Carneiro (May 03 2018 at 00:48)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/Church%20Numeral%20Puzzles/near/126018045):
but usually yes

#### [Kenny Lau (May 03 2018 at 00:48)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/Church%20Numeral%20Puzzles/near/126018048):
even if `x` is a proposition?

#### [Mario Carneiro (May 03 2018 at 00:49)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/Church%20Numeral%20Puzzles/near/126018054):
sure, why not?

#### [Kenny Lau (May 03 2018 at 00:49)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/Church%20Numeral%20Puzzles/near/126018057):
wow

#### [Kevin Buzzard (May 03 2018 at 00:49)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/Church%20Numeral%20Puzzles/near/126018064):
It's the `|` that causes the trouble

#### [Mario Carneiro (May 03 2018 at 00:49)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/Church%20Numeral%20Puzzles/near/126018065):
it often doesn't work as a straight replacement since it could be dependent

#### [Kevin Buzzard (May 03 2018 at 00:49)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/Church%20Numeral%20Puzzles/near/126018066):
suddenly I have `pow._main`

#### [Kenny Lau (May 03 2018 at 00:49)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/Church%20Numeral%20Puzzles/near/126018073):
yay we're on the same side for this time

#### [Mario Carneiro (May 03 2018 at 00:49)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/Church%20Numeral%20Puzzles/near/126018075):
Yes, the `|` triggers the equation compiler

#### [Mario Carneiro (May 03 2018 at 00:50)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/Church%20Numeral%20Puzzles/near/126018124):
It also gives you the correct (applied) equation lemma

#### [Mario Carneiro (May 03 2018 at 00:50)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/Church%20Numeral%20Puzzles/near/126018133):
rather than the lambda equation lemma

#### [Kenny Lau (May 03 2018 at 00:50)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/Church%20Numeral%20Puzzles/near/126018134):
I don't like that

#### [Kevin Buzzard (May 03 2018 at 00:51)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/Church%20Numeral%20Puzzles/near/126018164):
But Kenny is that just because you haven't learned how to use the more complex type properly?

#### [Kevin Buzzard (May 03 2018 at 00:51)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/Church%20Numeral%20Puzzles/near/126018169):
What is an example of where this causes you problems?

#### [Kenny Lau (May 03 2018 at 00:51)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/Church%20Numeral%20Puzzles/near/126018171):
heh... I use the equation compiler all the time

#### [Kenny Lau (May 03 2018 at 00:51)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/Church%20Numeral%20Puzzles/near/126018172):
I just don't like it

#### [Kevin Buzzard (May 03 2018 at 00:51)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/Church%20Numeral%20Puzzles/near/126018175):
and I am asking why exactly

#### [Kenny Lau (May 03 2018 at 00:52)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/Church%20Numeral%20Puzzles/near/126018218):
i don't know

#### [Mario Carneiro (May 03 2018 at 00:52)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/Church%20Numeral%20Puzzles/near/126018232):
I understand wanting a simple underlying term, but that's an issue best aimed at the equation compiler

#### [Kevin Buzzard (May 03 2018 at 00:53)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/Church%20Numeral%20Puzzles/near/126018242):
I am just learning all these tricks now. I have learned that when you write a substantial amount of code you end up picking stuff up as you need it; Kenny you wrote a lot of code a lot quicker than me.

#### [Kevin Buzzard (May 03 2018 at 00:53)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/Church%20Numeral%20Puzzles/near/126018247):
Mario, did you do my Ackermann church question? ;-)

#### [Kenny Lau (May 03 2018 at 00:53)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/Church%20Numeral%20Puzzles/near/126018250):
I'm convinced you can't do it

#### [Kenny Lau (May 03 2018 at 00:53)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/Church%20Numeral%20Puzzles/near/126018252):
you need a higher order functional

#### [Kenny Lau (May 03 2018 at 00:54)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/Church%20Numeral%20Puzzles/near/126018256):
since chNat lives in Type 1

#### [Kenny Lau (May 03 2018 at 00:54)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/Church%20Numeral%20Puzzles/near/126018295):
you need an empowered chNat that lives in Type 2

#### [Kenny Lau (May 03 2018 at 00:54)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/Church%20Numeral%20Puzzles/near/126018296):
Ackermann isn't primitive recursive

#### [Kenny Lau (May 03 2018 at 00:54)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/Church%20Numeral%20Puzzles/near/126018297):
its image is in Delta_1 not Delta_0

#### [Kenny Lau (May 03 2018 at 00:54)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/Church%20Numeral%20Puzzles/near/126018299):
in the arithmetic hierarchy

#### [Kevin Buzzard (May 03 2018 at 00:54)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/Church%20Numeral%20Puzzles/near/126018300):
`def ack : chℕ → chℕ → chℕ := sorry -- KB didn't try this one`

#### [Kenny Lau (May 03 2018 at 00:54)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/Church%20Numeral%20Puzzles/near/126018302):
whatever that means

#### [Kevin Buzzard (May 03 2018 at 00:54)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/Church%20Numeral%20Puzzles/near/126018303):
(for good reason!)

#### [Mario Carneiro (May 03 2018 at 00:54)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/Church%20Numeral%20Puzzles/near/126018306):
what ackermann church question

#### [Kevin Buzzard (May 03 2018 at 00:54)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/Church%20Numeral%20Puzzles/near/126018308):
fill in the def above

#### [Kenny Lau (May 03 2018 at 00:54)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/Church%20Numeral%20Puzzles/near/126018309):
@**Mario Carneiro** make ackermann using church

#### [Kevin Buzzard (May 03 2018 at 00:55)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/Church%20Numeral%20Puzzles/near/126018311):
so that it commutes with usual ack on nat

#### [Kenny Lau (May 03 2018 at 00:55)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/Church%20Numeral%20Puzzles/near/126018324):
@**Kevin Buzzard** or do you already know that one can't do it

#### [Kevin Buzzard (May 03 2018 at 00:55)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/Church%20Numeral%20Puzzles/near/126018327):
I don't have a clue

#### [Mario Carneiro (May 03 2018 at 00:55)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/Church%20Numeral%20Puzzles/near/126018329):
You can do it

#### [Kevin Buzzard (May 03 2018 at 00:55)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/Church%20Numeral%20Puzzles/near/126018330):
I just think this is really cool :-)

#### [Kevin Buzzard (May 03 2018 at 00:55)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/Church%20Numeral%20Puzzles/near/126018334):
How do you know you can do it?

#### [Kenny Lau (May 03 2018 at 00:56)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/Church%20Numeral%20Puzzles/near/126018375):
@**Mario Carneiro** I tried to do it and found myself requiring a more complex term in each iteration

#### [Kenny Lau (May 03 2018 at 00:56)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/Church%20Numeral%20Puzzles/near/126018379):
you can't iterate on (chN -> chN) either

#### [Kevin Buzzard (May 03 2018 at 00:57)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/Church%20Numeral%20Puzzles/near/126018387):
When a computer scientist says "you can do it" do they mean "there exists some computer code which does that job" or "it's possible to construct, in polynomial time, some computer code which does that job"

#### [Kenny Lau (May 03 2018 at 00:57)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/Church%20Numeral%20Puzzles/near/126018390):
the former

#### [Mario Carneiro (May 03 2018 at 00:57)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/Church%20Numeral%20Puzzles/near/126018391):
I mean there is a solution in less than 50 chars

#### [Kevin Buzzard (May 03 2018 at 00:57)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/Church%20Numeral%20Puzzles/near/126018393):
:-)

#### [Kenny Lau (May 03 2018 at 00:57)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/Church%20Numeral%20Puzzles/near/126018394):
??????

#### [Kenny Lau (May 03 2018 at 00:57)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/Church%20Numeral%20Puzzles/near/126018395):
50 chars....

#### [Mario Carneiro (May 03 2018 at 00:57)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/Church%20Numeral%20Puzzles/near/126018396):
so just go through all the lambda terms, you'll get it

#### [Kevin Buzzard (May 03 2018 at 00:57)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/Church%20Numeral%20Puzzles/near/126018398):
that's not polynomial time though

#### [Mario Carneiro (May 03 2018 at 00:58)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/Church%20Numeral%20Puzzles/near/126018438):
heck no

#### [Kevin Buzzard (May 03 2018 at 00:58)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/Church%20Numeral%20Puzzles/near/126018448):
Just to be clear, we're talking about the church numeral type without the axiom.

#### [Kevin Buzzard (May 03 2018 at 00:59)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/Church%20Numeral%20Puzzles/near/126018459):
`def chℕ := Π X : Type, (X → X) → X → X`

#### [Kenny Lau (May 03 2018 at 00:59)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/Church%20Numeral%20Puzzles/near/126018461):
@**Mario Carneiro** so what is wrong with my analysis?

#### [Mario Carneiro (May 03 2018 at 00:59)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/Church%20Numeral%20Puzzles/near/126018467):
Ah, I see what you mean now

#### [Mario Carneiro (May 03 2018 at 01:00)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/Church%20Numeral%20Puzzles/near/126018518):
In lambda calculus it's untyped so there is no problems

#### [Kenny Lau (May 03 2018 at 01:00)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/Church%20Numeral%20Puzzles/near/126018519):
exactly

#### [Mario Carneiro (May 03 2018 at 01:00)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/Church%20Numeral%20Puzzles/near/126018522):
but lean has universe issues

#### [Kenny Lau (May 03 2018 at 01:00)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/Church%20Numeral%20Puzzles/near/126018523):
we're in typed lamdba calculus

#### [Kevin Buzzard (May 03 2018 at 01:00)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/Church%20Numeral%20Puzzles/near/126018525):
as opposed to his rather more well-behaved friend `chℕfree := {m : Π X : Type, (X → X) → X → X // ∀ (X Y : Type) (a : X → Y) (f : X → X) (x : X),
  m (X → Y) (λ g, g ∘ f) a x = a (m X f x)}`

#### [Kevin Buzzard (May 03 2018 at 01:00)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/Church%20Numeral%20Puzzles/near/126018526):
which comes with a free theorem

#### [Mario Carneiro (May 03 2018 at 01:00)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/Church%20Numeral%20Puzzles/near/126018530):
you can still do it but you need inductive types, I think

#### [Kevin Buzzard (May 03 2018 at 01:01)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/Church%20Numeral%20Puzzles/near/126018540):
oh wait I can do it by cheating!

#### [Kevin Buzzard (May 03 2018 at 01:01)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/Church%20Numeral%20Puzzles/near/126018549):
There's a projection from church nat to nat

#### [Mario Carneiro (May 03 2018 at 01:01)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/Church%20Numeral%20Puzzles/near/126018550):
exactly

#### [Mario Carneiro (May 03 2018 at 01:01)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/Church%20Numeral%20Puzzles/near/126018551):
so you do an induction on `nat -> nat`

#### [Kenny Lau (May 03 2018 at 01:02)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/Church%20Numeral%20Puzzles/near/126018553):
that's cheating

#### [Kevin Buzzard (May 03 2018 at 01:02)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/Church%20Numeral%20Puzzles/near/126018567):
so I can define an "incorrect" pow

#### [Kevin Buzzard (May 03 2018 at 01:02)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/Church%20Numeral%20Puzzles/near/126018594):
But this is cheating

#### [Kevin Buzzard (May 03 2018 at 01:02)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/Church%20Numeral%20Puzzles/near/126018596):
Is this what they do with pred?

#### [Mario Carneiro (May 03 2018 at 01:02)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/Church%20Numeral%20Puzzles/near/126018597):
like I said, you need inductive types

#### [Kenny Lau (May 03 2018 at 01:02)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/Church%20Numeral%20Puzzles/near/126018598):
that's like asking can I define pow by of_nat and to_nat

#### [Kevin Buzzard (May 03 2018 at 01:02)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/Church%20Numeral%20Puzzles/near/126018600):
If you were to project to nat and then project back with any of add, mul or pow

#### [Mario Carneiro (May 03 2018 at 01:02)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/Church%20Numeral%20Puzzles/near/126018602):
I think you are right that chN only allows primrec definitions directly

#### [Kevin Buzzard (May 03 2018 at 01:02)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/Church%20Numeral%20Puzzles/near/126018605):
you would get a different answer to the "pure" answers which exist

#### [Kenny Lau (May 03 2018 at 01:03)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/Church%20Numeral%20Puzzles/near/126018627):
```quote
I mean there is a solution in less than 50 chars
```
this wouldn't work. how are you going to check if a given lambda term produces ack?

#### [Mario Carneiro (May 03 2018 at 01:04)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/Church%20Numeral%20Puzzles/near/126018668):
solve the halting problem of course

#### [Kevin Buzzard (May 03 2018 at 01:04)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/Church%20Numeral%20Puzzles/near/126018669):
in the proof I'm envisaging

#### [Kenny Lau (May 03 2018 at 01:04)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/Church%20Numeral%20Puzzles/near/126018675):
you...

#### [Kevin Buzzard (May 03 2018 at 01:04)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/Church%20Numeral%20Puzzles/near/126018677):
:-)

#### [Kevin Buzzard (May 03 2018 at 01:04)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/Church%20Numeral%20Puzzles/near/126018684):
it's going to follow from some cunning unravelling isn't it?

#### [Mario Carneiro (May 03 2018 at 01:09)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/Church%20Numeral%20Puzzles/near/126018841):
wait, no I lied again, it is possible

#### [Kenny Lau (May 03 2018 at 01:09)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/Church%20Numeral%20Puzzles/near/126018844):
hmm

#### [Mario Carneiro (May 03 2018 at 01:09)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/Church%20Numeral%20Puzzles/near/126018846):
the motive is `X → X`

#### [Kenny Lau (May 03 2018 at 01:10)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/Church%20Numeral%20Puzzles/near/126018890):
you need to store a function each time

#### [Kevin Buzzard (May 03 2018 at 01:18)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/Church%20Numeral%20Puzzles/near/126019177):
```lean
theorem nat_of_chnat_of_nat (n : ℕ) : to_nat (of_nat n) = n := sorry -- exercise

-- breakthough! I implemented my exciting new foo function on church numerals
def foo : ℕ → ℕ → ℕ := sorry
def choo (m n : chℕ) : chℕ := of_nat (foo (to_nat m) (to_nat n))

theorem amazing_compatibility (a b : ℕ) :
of_nat (foo a b) = choo (of_nat a) (of_nat b) :=
begin
unfold choo,
simp [nat_of_chnat_of_nat]
end
```

#### [Kevin Buzzard (May 03 2018 at 01:20)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/Church%20Numeral%20Puzzles/near/126019267):
That makes me slightly sad

#### [Kevin Buzzard (May 03 2018 at 01:21)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/Church%20Numeral%20Puzzles/near/126019292):
I spent some time today thinking about the Church Numeral which given X and f and x, returns x unless X = nat and f = succ and x = 0, in which case it returns 1

#### [Kevin Buzzard (May 03 2018 at 01:22)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/Church%20Numeral%20Puzzles/near/126019341):
it's quite a good way of reminding yourself exactly how far you can expect to push things

#### [Kevin Buzzard (May 03 2018 at 01:24)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/Church%20Numeral%20Puzzles/near/126019415):
e.g. I believe that funny numeral doesn't commute with + 1 and this can be easily checked via  very concrete calculation on nat

#### [Kevin Buzzard (May 03 2018 at 01:24)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/Church%20Numeral%20Puzzles/near/126019425):
so you know you shouldn't be trying to prove that add commutes

#### [Kevin Buzzard (May 03 2018 at 01:25)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/Church%20Numeral%20Puzzles/near/126019428):
I'm not sure what Mr Ackermann would have thought about evaluating his function there

#### [Mario Carneiro (May 03 2018 at 01:26)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/Church%20Numeral%20Puzzles/near/126019502):
By the way, you got the free statement a bit off:
```
def chℕfree := {m : Π X : Type, (X → X) → X → X //
  ∀ (X Y : Type) (a : X → Y) (f : X → X) (g : Y → Y),
  a ∘ f = g ∘ a → m Y g ∘ a = a ∘ m X f}
```

#### [Kevin Buzzard (May 03 2018 at 01:30)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/Church%20Numeral%20Puzzles/near/126019642):
Do you think that's the same?

#### [Kevin Buzzard (May 03 2018 at 01:30)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/Church%20Numeral%20Puzzles/near/126019651):
You are quantifying over g too

#### [Kevin Buzzard (May 03 2018 at 01:31)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/Church%20Numeral%20Puzzles/near/126019661):
It might be the same

#### [Mario Carneiro (May 03 2018 at 01:34)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/Church%20Numeral%20Puzzles/near/126019775):
It might be the same, but my version fits a more regular pattern

#### [Mario Carneiro (May 03 2018 at 01:34)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/Church%20Numeral%20Puzzles/near/126019789):
and it doesn't require evaluating `m` at a function type

#### [Mario Carneiro (May 03 2018 at 01:35)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/Church%20Numeral%20Puzzles/near/126019821):
It's basically saying that if `a : f -> g` is a natural transformation, then so is `m`

#### [Mario Carneiro (May 03 2018 at 01:36)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/Church%20Numeral%20Puzzles/near/126019871):
That's probably a poor reading, but something like that

#### [Mario Carneiro (May 03 2018 at 01:38)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/Church%20Numeral%20Puzzles/near/126019886):
What makes `chN` not quite as powerful as system T is that `chN` isn't a type in the internal sense

#### [Mario Carneiro (May 03 2018 at 01:38)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/Church%20Numeral%20Puzzles/near/126019930):
with impredicative quantification (like in system F) this would work

#### [Mario Carneiro (May 03 2018 at 01:41)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/Church%20Numeral%20Puzzles/near/126020008):
Godel's system T is simply typed lambda calculus with arrows and products, and a type `N` with `0 : N` and `S : N -> N` and `iter_A : (A -> A) -> A -> N -> A`

#### [Mario Carneiro (May 03 2018 at 01:42)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/Church%20Numeral%20Puzzles/near/126020060):
Then `N` there is just like lean's `ℕ`, but `chℕ` is not a substitute because it lives in `Type 1` so it is not a type in STLC

#### [Kevin Buzzard (May 03 2018 at 01:49)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/Church%20Numeral%20Puzzles/near/126020250):
This is really interesting

#### [Kevin Buzzard (May 03 2018 at 01:49)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/Church%20Numeral%20Puzzles/near/126020253):
I identified nat as the universal object

#### [Kevin Buzzard (May 03 2018 at 01:49)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/Church%20Numeral%20Puzzles/near/126020256):
and just wrote down some kind of standard maths functory thing about evaluating the universal object at a map

#### [Kevin Buzzard (May 03 2018 at 01:50)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/Church%20Numeral%20Puzzles/near/126020304):
but, like induction, you might think about universal objects in a different way to us

#### [Kevin Buzzard (May 03 2018 at 01:50)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/Church%20Numeral%20Puzzles/near/126020312):
I think I see what I'm missing

#### [Kevin Buzzard (May 03 2018 at 01:51)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/Church%20Numeral%20Puzzles/near/126020322):
In my world, a would be a map in the category

#### [Kevin Buzzard (May 03 2018 at 01:51)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/Church%20Numeral%20Puzzles/near/126020323):
and I would be assuming m was a functor

#### [Kevin Buzzard (May 03 2018 at 01:51)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/Church%20Numeral%20Puzzles/near/126020325):
and trying to represent it

#### [Kevin Buzzard (May 03 2018 at 01:51)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/Church%20Numeral%20Puzzles/near/126020332):
but m being a functor is an extra condition which I have forgotten about because in the examples I know it is always there

#### [Kevin Buzzard (May 03 2018 at 03:12)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/Church%20Numeral%20Puzzles/near/126022755):
`example : equiv ℕ chℕfree := ⟨to_chfr,of_chfr,inv₁,inv₂⟩ `

#### [Kevin Buzzard (May 03 2018 at 03:17)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/Church%20Numeral%20Puzzles/near/126022901):
Mario's definition definitely works. I wonder if mine (which is implied by Mario's) is too weak.

#### [Kevin Buzzard (May 03 2018 at 03:23)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/Church%20Numeral%20Puzzles/near/126023071):
So I understand the category theory language much better than this DTT stuff.

#### [Kevin Buzzard (May 03 2018 at 03:23)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/Church%20Numeral%20Puzzles/near/126023076):
I want to say that Type is a category.

#### [Mario Carneiro (May 03 2018 at 03:23)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/Church%20Numeral%20Puzzles/near/126023077):
It is

#### [Kevin Buzzard (May 03 2018 at 03:23)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/Church%20Numeral%20Puzzles/near/126023078):
Then m wants to be a functor from Type to Type

#### [Kevin Buzzard (May 03 2018 at 03:23)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/Church%20Numeral%20Puzzles/near/126023080):
but Church's naive definition just demands a map on objects

#### [Mario Carneiro (May 03 2018 at 03:24)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/Church%20Numeral%20Puzzles/near/126023123):
In languages where the naive definition works, that's because of parametric polymorphism

#### [Mario Carneiro (May 03 2018 at 03:24)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/Church%20Numeral%20Puzzles/near/126023124):
i.e. everything is functorial

#### [Kevin Buzzard (May 03 2018 at 03:24)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/Church%20Numeral%20Puzzles/near/126023125):
I don't know what that means

#### [Mario Carneiro (May 03 2018 at 03:24)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/Church%20Numeral%20Puzzles/near/126023127):
HoTT is a lot like this

#### [Kevin Buzzard (May 03 2018 at 03:24)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/Church%20Numeral%20Puzzles/near/126023128):
Oh I see

#### [Mario Carneiro (May 03 2018 at 03:24)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/Church%20Numeral%20Puzzles/near/126023130):
the language is crafted such that you can't write badly behaved terms at all

#### [Mario Carneiro (May 03 2018 at 03:25)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/Church%20Numeral%20Puzzles/near/126023138):
everything is "fibrant"

#### [Mario Carneiro (May 03 2018 at 03:25)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/Church%20Numeral%20Puzzles/near/126023139):
whatever that means

#### [Kevin Buzzard (May 03 2018 at 03:25)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/Church%20Numeral%20Puzzles/near/126023140):
Let me modify Type

#### [Kevin Buzzard (May 03 2018 at 03:25)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/Church%20Numeral%20Puzzles/near/126023142):
so that its objects are still terms whose type is Type

#### [Mario Carneiro (May 03 2018 at 03:25)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/Church%20Numeral%20Puzzles/near/126023143):
but that's basically why univalence works

#### [Kevin Buzzard (May 03 2018 at 03:25)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/Church%20Numeral%20Puzzles/near/126023144):
but the morphisms are equivs

#### [Kevin Buzzard (May 03 2018 at 03:25)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/Church%20Numeral%20Puzzles/near/126023146):
Now m is a map on objects

#### [Kevin Buzzard (May 03 2018 at 03:26)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/Church%20Numeral%20Puzzles/near/126023186):
and the data of the equiv is exactly what m needs to be extendible to a map on morphisms I suspect

#### [Mario Carneiro (May 03 2018 at 03:26)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/Church%20Numeral%20Puzzles/near/126023187):
Check this out: http://www.cs.bham.ac.uk/~udr/papers/logical-relations-and-parametricity.pdf

#### [Kevin Buzzard (May 03 2018 at 03:27)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/Church%20Numeral%20Puzzles/near/126023193):
In fact I guess it's exactly when X and Y biject that I would even dream of identifying `(X->X) -> X -> X` and the analogous term for `Y`

#### [Mario Carneiro (May 03 2018 at 03:27)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/Church%20Numeral%20Puzzles/near/126023194):
It argues that naturality is the wrong idea and should be replaced by parametricity

#### [Mario Carneiro (May 03 2018 at 03:27)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/Church%20Numeral%20Puzzles/near/126023196):
I need to finish digesting it though, so don't quote me on that

#### [Mario Carneiro (May 03 2018 at 03:28)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/Church%20Numeral%20Puzzles/near/126023241):
Notice though that the condition I gave does not require that a is an equiv

#### [Mario Carneiro (May 03 2018 at 03:28)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/Church%20Numeral%20Puzzles/near/126023244):
I think that's going to be true in general

#### [Mario Carneiro (May 03 2018 at 03:28)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/Church%20Numeral%20Puzzles/near/126023245):
It really is a functoriality condition

#### [Kevin Buzzard (May 03 2018 at 03:29)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/Church%20Numeral%20Puzzles/near/126023249):
You have to be careful

#### [Kevin Buzzard (May 03 2018 at 03:29)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/Church%20Numeral%20Puzzles/near/126023254):
Given a map A to B

#### [Mario Carneiro (May 03 2018 at 03:29)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/Church%20Numeral%20Puzzles/near/126023255):
it's just this weird higher order functoriality thing

#### [Mario Carneiro (May 03 2018 at 03:29)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/Church%20Numeral%20Puzzles/near/126023256):
It seems like logical relations generate the condition well

#### [Kevin Buzzard (May 03 2018 at 03:29)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/Church%20Numeral%20Puzzles/near/126023258):
You don't get a map (A to A) to (B to B)

#### [Kevin Buzzard (May 03 2018 at 03:30)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/Church%20Numeral%20Puzzles/near/126023300):
So I don't know what you mean when you say functoriality is true "in general"

#### [Kevin Buzzard (May 03 2018 at 03:30)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/Church%20Numeral%20Puzzles/near/126023301):
I can only see a functor in the equiv category

#### [Kevin Buzzard (May 03 2018 at 03:31)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/Church%20Numeral%20Puzzles/near/126023308):
Maybe we mean different things by functorially

#### [Mario Carneiro (May 03 2018 at 03:31)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/Church%20Numeral%20Puzzles/near/126023309):
I mean that if you write down some more complicated thing than chN I can write down a more complicated parametricity constraint for it

#### [Mario Carneiro (May 03 2018 at 03:31)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/Church%20Numeral%20Puzzles/near/126023310):
and I can always do this

#### [Mario Carneiro (May 03 2018 at 03:31)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/Church%20Numeral%20Puzzles/near/126023311):
and it will involve a function a : X -> Y

#### [Mario Carneiro (May 03 2018 at 03:32)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/Church%20Numeral%20Puzzles/near/126023313):
and that function will usually not be required to be an equiv

#### [Kevin Buzzard (May 03 2018 at 03:33)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/Church%20Numeral%20Puzzles/near/126023363):
I can't make that concept into a functor

#### [Kevin Buzzard (May 03 2018 at 03:34)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/Church%20Numeral%20Puzzles/near/126023404):
For me, F (X -> Y) is a map F X -> F Y

#### [Mario Carneiro (May 03 2018 at 03:35)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/Church%20Numeral%20Puzzles/near/126023412):
Here's the setup: we define a collection of logical relations [R] : X -> Y -> Prop. The important one is for arrows: `[R -> S] : (X -> X') -> (Y -> Y') -> Prop` is defined by
```
f [R -> S] g <-> \forall x y, x [R] y -> f x [S] g y
```

#### [Mario Carneiro (May 03 2018 at 03:36)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/Church%20Numeral%20Puzzles/near/126023452):
At the base types we define `[R] : X -> Y -> Prop` by `x [R] y <-> a x = y`

#### [Mario Carneiro (May 03 2018 at 03:36)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/Church%20Numeral%20Puzzles/near/126023454):
where `a : X -> Y` is our fixed morphism to commute over

#### [Mario Carneiro (May 03 2018 at 03:37)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/Church%20Numeral%20Puzzles/near/126023460):
Applying this definition to `[(R -> R) -> R -> R]` gives exactly the condition I wrote down

#### [Kevin Buzzard (May 03 2018 at 03:37)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/Church%20Numeral%20Puzzles/near/126023463):
Oh so you're going to tell me that the function I'm looking for is actually a relation

#### [Mario Carneiro (May 03 2018 at 03:42)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/Church%20Numeral%20Puzzles/near/126023623):
And we can go further to even get the `a` part: we can define `[∀ X, R] : (∀ X:Type, P X) -> (∀ X:Type, Q X) -> Prop` by
```
F [∀ X, R] G <-> ∀ X Y : Type, ∀ (a : X -> Y), F X [R] G Y
```
(here if `X` appears in `R` it's referring to the relation for the function `a`)

#### [Mario Carneiro (May 03 2018 at 03:43)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/Church%20Numeral%20Puzzles/near/126023635):
Finally, a term is parametrically polymorphic if it is related to itself at its type, i.e. `m [∀ X, (X -> X) -> X -> X] m` for the case of `chN`

#### [Mario Carneiro (May 03 2018 at 03:44)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/Church%20Numeral%20Puzzles/near/126023674):
This is how logical relations work, and how the theorems for free statements are derived

#### [Kevin Buzzard (May 03 2018 at 17:34)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/Church%20Numeral%20Puzzles/near/126050623):
```quote
Check this out: http://www.cs.bham.ac.uk/~udr/papers/logical-relations-and-parametricity.pdf
```
That paper

