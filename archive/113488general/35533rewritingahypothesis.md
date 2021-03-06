---
layout: page
title: Lean Prover Zulip Chat Archive 
permalink: archive/113488general/35533rewritingahypothesis.html
---

## [general](index.html)
### [rewriting a hypothesis](35533rewritingahypothesis.html)

#### [Johan Commelin (Apr 24 2018 at 09:40)](https://leanprover.zulipchat.com/#narrow/stream/113488-general/topic/rewriting%20a%20hypothesis/near/125608657):
This belongs in its own topic.
(Originally https://leanprover.zulipchat.com/#narrow/stream/113488-general/subject/statement.20of.20the.20five.20lemma/near/125607928)
```quote
Can I easily rewrite the hypothesis `(com₁ : m ∘ f = r ∘ l)` into `com₁' : \fo x, (m (f x) = r (l x))` ?
```

#### [Sean Leather (Apr 24 2018 at 09:41)](https://leanprover.zulipchat.com/#narrow/stream/113488-general/topic/rewriting%20a%20hypothesis/near/125608662):
Did you try `unfold function.comp`?

#### [Moses Schönfinkel (Apr 24 2018 at 09:42)](https://leanprover.zulipchat.com/#narrow/stream/113488-general/topic/rewriting%20a%20hypothesis/near/125608722):
Wouldn't you need extensionality for it first?

#### [Sean Leather (Apr 24 2018 at 09:47)](https://leanprover.zulipchat.com/#narrow/stream/113488-general/topic/rewriting%20a%20hypothesis/near/125608842):
```lean
example {A B C D : Type} (f₁ f₂ : A → B) (g₁ g₂ : B → C) : g₁ ∘ f₁ = g₂ ∘ f₂ :=
  by unfold function.comp; funext x
```

```lean
A B C D : Type,
f₁ f₂ : A → B,
g₁ g₂ : B → C,
x : A
⊢ g₁ (f₁ x) = g₂ (f₂ x)
```

#### [Moses Schönfinkel (Apr 24 2018 at 09:47)](https://leanprover.zulipchat.com/#narrow/stream/113488-general/topic/rewriting%20a%20hypothesis/near/125608848):
Right, I am a moron :).

#### [Sean Leather (Apr 24 2018 at 09:48)](https://leanprover.zulipchat.com/#narrow/stream/113488-general/topic/rewriting%20a%20hypothesis/near/125608893):
Or you read from right to left. :upside_down_face:

#### [Moses Schönfinkel (Apr 24 2018 at 09:48)](https://leanprover.zulipchat.com/#narrow/stream/113488-general/topic/rewriting%20a%20hypothesis/near/125608900):
I think my fingers typed before my brain got involved.

#### [Sean Leather (Apr 24 2018 at 09:49)](https://leanprover.zulipchat.com/#narrow/stream/113488-general/topic/rewriting%20a%20hypothesis/near/125608909):
Actually, in my current version of Lean (dated to February, I think), `unfold` isn't necessary.

#### [Sean Leather (Apr 24 2018 at 09:49)](https://leanprover.zulipchat.com/#narrow/stream/113488-general/topic/rewriting%20a%20hypothesis/near/125608912):
```lean
A B C D : Type,
f₁ f₂ : A → B,
g₁ g₂ : B → C,
x : A
⊢ (g₁ ∘ f₁) x = (g₂ ∘ f₂) x
```

#### [Sean Leather (Apr 24 2018 at 09:50)](https://leanprover.zulipchat.com/#narrow/stream/113488-general/topic/rewriting%20a%20hypothesis/near/125608959):
Okay, but that's not what you want. So I revoke my statement.

#### [Sean Leather (Apr 24 2018 at 09:51)](https://leanprover.zulipchat.com/#narrow/stream/113488-general/topic/rewriting%20a%20hypothesis/near/125608982):
And to alleviate @**Moses Schönfinkel**'s concerns, you can do it the other way around:

```lean
example {A B C D : Type} (f₁ f₂ : A → B) (g₁ g₂ : B → C) : g₁ ∘ f₁ = g₂ ∘ f₂ :=
  by funext x; unfold function.comp
```

```lean
A B C D : Type,
f₁ f₂ : A → B,
g₁ g₂ : B → C,
x : A
⊢ g₁ (f₁ x) = g₂ (f₂ x)
```

#### [Sean Leather (Apr 24 2018 at 09:51)](https://leanprover.zulipchat.com/#narrow/stream/113488-general/topic/rewriting%20a%20hypothesis/near/125608989):
@**Moses Schönfinkel** So you're not a moron after all.

#### [Moses Schönfinkel (Apr 24 2018 at 09:54)](https://leanprover.zulipchat.com/#narrow/stream/113488-general/topic/rewriting%20a%20hypothesis/near/125609106):
I am at least a partial moron because I thought extensionality needs to come before unfolding :). For some definition of "thought" which is just "don't think and fetch a pattern you'd encountered before".

#### [Johan Commelin (Apr 24 2018 at 10:07)](https://leanprover.zulipchat.com/#narrow/stream/113488-general/topic/rewriting%20a%20hypothesis/near/125609543):
Ok, so I unfolded that hypothesis. Now how do I apply it? Part of my (50-line) context is like this:
```
com₃ : (λ (x : C₁), m (h₁ x)) = λ (x : C₁), h₂ (l x),
x : C₁,
this : h₂ (l x) = 1
⊢ m (h₁ x) = 1
```

#### [Johan Commelin (Apr 24 2018 at 10:13)](https://leanprover.zulipchat.com/#narrow/stream/113488-general/topic/rewriting%20a%20hypothesis/near/125609747):
Why can't `cc` solve this one?

#### [Kevin Buzzard (Apr 24 2018 at 10:14)](https://leanprover.zulipchat.com/#narrow/stream/113488-general/topic/rewriting%20a%20hypothesis/near/125609789):
I don't know anything about cc

#### [Johan Commelin (Apr 24 2018 at 10:14)](https://leanprover.zulipchat.com/#narrow/stream/113488-general/topic/rewriting%20a%20hypothesis/near/125609790):
Somehow it needs a slightly rewritten version of `com₃`, I guess

#### [Kevin Buzzard (Apr 24 2018 at 10:14)](https://leanprover.zulipchat.com/#narrow/stream/113488-general/topic/rewriting%20a%20hypothesis/near/125609793):
but are you having trouble proving this in general?

#### [Johan Commelin (Apr 24 2018 at 10:14)](https://leanprover.zulipchat.com/#narrow/stream/113488-general/topic/rewriting%20a%20hypothesis/near/125609794):
Yup

#### [Kevin Buzzard (Apr 24 2018 at 10:15)](https://leanprover.zulipchat.com/#narrow/stream/113488-general/topic/rewriting%20a%20hypothesis/near/125609816):
com3 says "two functions are equal"

#### [Johan Commelin (Apr 24 2018 at 10:15)](https://leanprover.zulipchat.com/#narrow/stream/113488-general/topic/rewriting%20a%20hypothesis/near/125609818):
AFAIK, `cc` follows it's nose, deducing equalities and occasionally applying some functions.

#### [Johan Commelin (Apr 24 2018 at 10:15)](https://leanprover.zulipchat.com/#narrow/stream/113488-general/topic/rewriting%20a%20hypothesis/near/125609823):
But that is simplistic

#### [Kevin Buzzard (Apr 24 2018 at 10:15)](https://leanprover.zulipchat.com/#narrow/stream/113488-general/topic/rewriting%20a%20hypothesis/near/125609826):
I would be tempted to really use the functions themselves

#### [Johan Commelin (Apr 24 2018 at 10:15)](https://leanprover.zulipchat.com/#narrow/stream/113488-general/topic/rewriting%20a%20hypothesis/near/125609827):
@**Kevin Buzzard** Right, so I need to do some funext

#### [Kevin Buzzard (Apr 24 2018 at 10:15)](https://leanprover.zulipchat.com/#narrow/stream/113488-general/topic/rewriting%20a%20hypothesis/near/125609833):
I am sure I can give a hands-on proof

#### [Johan Commelin (Apr 24 2018 at 10:15)](https://leanprover.zulipchat.com/#narrow/stream/113488-general/topic/rewriting%20a%20hypothesis/near/125609834):
Or what

#### [Kevin Buzzard (Apr 24 2018 at 10:16)](https://leanprover.zulipchat.com/#narrow/stream/113488-general/topic/rewriting%20a%20hypothesis/near/125609879):
You can write "show (m circ h1) x = 1" probably

#### [Kevin Buzzard (Apr 24 2018 at 10:16)](https://leanprover.zulipchat.com/#narrow/stream/113488-general/topic/rewriting%20a%20hypothesis/near/125609881):
this will rewrite the goal

#### [Kevin Buzzard (Apr 24 2018 at 10:16)](https://leanprover.zulipchat.com/#narrow/stream/113488-general/topic/rewriting%20a%20hypothesis/near/125609886):
because `show` will change a goal to something definitionally equivalent

#### [Kevin Buzzard (Apr 24 2018 at 10:16)](https://leanprover.zulipchat.com/#narrow/stream/113488-general/topic/rewriting%20a%20hypothesis/near/125609887):
Do you know about definitional equivalence?

#### [Johan Commelin (Apr 24 2018 at 10:16)](https://leanprover.zulipchat.com/#narrow/stream/113488-general/topic/rewriting%20a%20hypothesis/near/125609888):
yes

#### [Kevin Buzzard (Apr 24 2018 at 10:17)](https://leanprover.zulipchat.com/#narrow/stream/113488-general/topic/rewriting%20a%20hypothesis/near/125609897):
and you can use "change" to rewrite hypotheses to definitionally equivalent things too

#### [Sean Leather (Apr 24 2018 at 10:17)](https://leanprover.zulipchat.com/#narrow/stream/113488-general/topic/rewriting%20a%20hypothesis/near/125609902):
As well as `refine`.

#### [Johan Commelin (Apr 24 2018 at 10:17)](https://leanprover.zulipchat.com/#narrow/stream/113488-general/topic/rewriting%20a%20hypothesis/near/125609906):
Hmmz, ok

#### [Johan Commelin (Apr 24 2018 at 10:17)](https://leanprover.zulipchat.com/#narrow/stream/113488-general/topic/rewriting%20a%20hypothesis/near/125609907):
Let's see if I can find a proof

#### [Kevin Buzzard (Apr 24 2018 at 10:18)](https://leanprover.zulipchat.com/#narrow/stream/113488-general/topic/rewriting%20a%20hypothesis/near/125609910):
Let me just get your context into some MWE

#### [Kenny Lau (Apr 24 2018 at 10:18)](https://leanprover.zulipchat.com/#narrow/stream/113488-general/topic/rewriting%20a%20hypothesis/near/125609947):
@**Johan Commelin** `exaxt (congr_fun com\3 _).trans this`

#### [Kevin Buzzard (Apr 24 2018 at 10:21)](https://leanprover.zulipchat.com/#narrow/stream/113488-general/topic/rewriting%20a%20hypothesis/near/125610023):
```lean
example (W X Y Z : Type) (f : W → X) (g : X → Z) (h : W → Y) (j : Y → Z) (w : W) (one : Z)
(Hcom : (λ t, g (f t)) = (λ t, j (h t))) (Hthis : j (h w) = one) : g (f w) = one := sorry
```

#### [Kevin Buzzard (Apr 24 2018 at 10:21)](https://leanprover.zulipchat.com/#narrow/stream/113488-general/topic/rewriting%20a%20hypothesis/near/125610026):
@**Johan Commelin** if you write your question like this (i.e. make it easily cut-and-pasteable)

#### [Kevin Buzzard (Apr 24 2018 at 10:21)](https://leanprover.zulipchat.com/#narrow/stream/113488-general/topic/rewriting%20a%20hypothesis/near/125610029):
then when Kenny goes into proof mode

#### [Kevin Buzzard (Apr 24 2018 at 10:22)](https://leanprover.zulipchat.com/#narrow/stream/113488-general/topic/rewriting%20a%20hypothesis/near/125610066):
he's more likely to print out more proofs

#### [Johan Commelin (Apr 24 2018 at 10:22)](https://leanprover.zulipchat.com/#narrow/stream/113488-general/topic/rewriting%20a%20hypothesis/near/125610069):
Ok, I see

#### [Kevin Buzzard (Apr 24 2018 at 10:24)](https://leanprover.zulipchat.com/#narrow/stream/113488-general/topic/rewriting%20a%20hypothesis/near/125610140):
```lean
example (W X Y Z : Type) (f : W → X) (g : X → Z) (h : W → Y) (j : Y → Z) (w : W) (one : Z)
(Hcom : (λ t, g (f t)) = (λ t, j (h t))) (Hthis : j (h w) = one) : g (f w) = one := 
begin
change (g ∘ f) w = one,
change (j ∘ h) w = one at Hthis,
change (g ∘ f) = (j ∘ h) at Hcom,
rwa Hcom
end
```

#### [Kevin Buzzard (Apr 24 2018 at 10:25)](https://leanprover.zulipchat.com/#narrow/stream/113488-general/topic/rewriting%20a%20hypothesis/near/125610146):
If you're not ready for Kenny's gobble-de-gook then there is how I would think about it

#### [Kevin Buzzard (Apr 24 2018 at 10:25)](https://leanprover.zulipchat.com/#narrow/stream/113488-general/topic/rewriting%20a%20hypothesis/near/125610154):
`rwa` means `rewrite, and then note that the goal is an assumption so close it`

#### [Kevin Buzzard (Apr 24 2018 at 10:26)](https://leanprover.zulipchat.com/#narrow/stream/113488-general/topic/rewriting%20a%20hypothesis/near/125610206):
and `change` lets you change things to definitionally equivalent things

#### [Kevin Buzzard (Apr 24 2018 at 10:26)](https://leanprover.zulipchat.com/#narrow/stream/113488-general/topic/rewriting%20a%20hypothesis/near/125610211):
The problem with rewrite is that it will not change stuff to definitionally equivalent stuff

#### [Kevin Buzzard (Apr 24 2018 at 10:27)](https://leanprover.zulipchat.com/#narrow/stream/113488-general/topic/rewriting%20a%20hypothesis/near/125610214):
it has to already be exactly right

#### [Johan Commelin (Apr 24 2018 at 10:29)](https://leanprover.zulipchat.com/#narrow/stream/113488-general/topic/rewriting%20a%20hypothesis/near/125610290):
Ok, got that. Thanks!

#### [Kevin Buzzard (Apr 24 2018 at 10:29)](https://leanprover.zulipchat.com/#narrow/stream/113488-general/topic/rewriting%20a%20hypothesis/near/125610296):
Here's Kenny's proof:

#### [Kevin Buzzard (Apr 24 2018 at 10:30)](https://leanprover.zulipchat.com/#narrow/stream/113488-general/topic/rewriting%20a%20hypothesis/near/125610339):
```lean
example (W X Y Z : Type) (f : W → X) (g : X → Z) (h : W → Y) (j : Y → Z) (w : W) (one : Z)
(Hcom : (λ t, g (f t)) = (λ t, j (h t))) (Hthis : j (h w) = one) : g (f w) = one := 
((congr_fun Hcom) _).trans Hthis
```

#### [Patrick Massot (Apr 24 2018 at 10:30)](https://leanprover.zulipchat.com/#narrow/stream/113488-general/topic/rewriting%20a%20hypothesis/near/125610340):
That's a nice example. I'm sure we can have a 23rd PR about simp vs rw vs change

#### [Kevin Buzzard (Apr 24 2018 at 10:30)](https://leanprover.zulipchat.com/#narrow/stream/113488-general/topic/rewriting%20a%20hypothesis/near/125610341):
This really shows the power of term mode

#### [Patrick Massot (Apr 24 2018 at 10:30)](https://leanprover.zulipchat.com/#narrow/stream/113488-general/topic/rewriting%20a%20hypothesis/near/125610345):
Kevin, you forgot to switch browser

#### [Patrick Massot (Apr 24 2018 at 10:30)](https://leanprover.zulipchat.com/#narrow/stream/113488-general/topic/rewriting%20a%20hypothesis/near/125610350):
To the one where you are logged in as Kenny

#### [Kevin Buzzard (Apr 24 2018 at 10:31)](https://leanprover.zulipchat.com/#narrow/stream/113488-general/topic/rewriting%20a%20hypothesis/near/125610360):
darn, I'm getting forgetful in my old age

#### [Kevin Buzzard (Apr 24 2018 at 10:31)](https://leanprover.zulipchat.com/#narrow/stream/113488-general/topic/rewriting%20a%20hypothesis/near/125610367):
General mathlib style guide says "if it's trivially true, then the best proof is an incomprehensible one-liner"

#### [Kevin Buzzard (Apr 24 2018 at 10:32)](https://leanprover.zulipchat.com/#narrow/stream/113488-general/topic/rewriting%20a%20hypothesis/near/125610405):
because there's no point writing a four line tactic proof like mine, which makes it clear how you are doing something completely trivial

#### [Kevin Buzzard (Apr 24 2018 at 10:33)](https://leanprover.zulipchat.com/#narrow/stream/113488-general/topic/rewriting%20a%20hypothesis/near/125610426):
But I spent a long long time writing all proofs in tactic mode before I felt comfortable with these fancy one-line term mode proofs

#### [Johan Commelin (Apr 24 2018 at 10:33)](https://leanprover.zulipchat.com/#narrow/stream/113488-general/topic/rewriting%20a%20hypothesis/near/125610428):
Ok, so now I have proven that `h_1 x = 1`. So now I want to say `ker h_1 = im g_1` hence there is a `y : B_1` such that `g_1 y = x`.

#### [Kevin Buzzard (Apr 24 2018 at 10:33)](https://leanprover.zulipchat.com/#narrow/stream/113488-general/topic/rewriting%20a%20hypothesis/near/125610430):
How have you set things up: is ker h1 a set?

#### [Kevin Buzzard (Apr 24 2018 at 10:33)](https://leanprover.zulipchat.com/#narrow/stream/113488-general/topic/rewriting%20a%20hypothesis/near/125610431):
There are two ways of talking about what a mathematician would call a subset of a set

#### [Kevin Buzzard (Apr 24 2018 at 10:34)](https://leanprover.zulipchat.com/#narrow/stream/113488-general/topic/rewriting%20a%20hypothesis/near/125610471):
you can use sets or subtypes

#### [Kevin Buzzard (Apr 24 2018 at 10:34)](https://leanprover.zulipchat.com/#narrow/stream/113488-general/topic/rewriting%20a%20hypothesis/near/125610478):
they carry the same data, but packaged in different ways

#### [Kevin Buzzard (Apr 24 2018 at 10:34)](https://leanprover.zulipchat.com/#narrow/stream/113488-general/topic/rewriting%20a%20hypothesis/near/125610480):
One is a term, one is a type

#### [Johan Commelin (Apr 24 2018 at 10:34)](https://leanprover.zulipchat.com/#narrow/stream/113488-general/topic/rewriting%20a%20hypothesis/near/125610485):
https://gist.github.com/jcommelin/d097eb8f2587d34e5c337450bca543db

#### [Johan Commelin (Apr 24 2018 at 10:34)](https://leanprover.zulipchat.com/#narrow/stream/113488-general/topic/rewriting%20a%20hypothesis/near/125610486):
That's an update

#### [Johan Commelin (Apr 24 2018 at 10:35)](https://leanprover.zulipchat.com/#narrow/stream/113488-general/topic/rewriting%20a%20hypothesis/near/125610489):
With what I have so far

#### [Kevin Buzzard (Apr 24 2018 at 10:36)](https://leanprover.zulipchat.com/#narrow/stream/113488-general/topic/rewriting%20a%20hypothesis/near/125610554):
You're using sets

#### [Kevin Buzzard (Apr 24 2018 at 10:36)](https://leanprover.zulipchat.com/#narrow/stream/113488-general/topic/rewriting%20a%20hypothesis/near/125610555):
Oh wow, the message everyone was replying to has changed.

#### [Kevin Buzzard (Apr 24 2018 at 10:37)](https://leanprover.zulipchat.com/#narrow/stream/113488-general/topic/rewriting%20a%20hypothesis/near/125610568):
If you write `have := ...` in tactic mode

#### [Kevin Buzzard (Apr 24 2018 at 10:38)](https://leanprover.zulipchat.com/#narrow/stream/113488-general/topic/rewriting%20a%20hypothesis/near/125610607):
then Lean calls the thing you proved `this` by default

#### [Kevin Buzzard (Apr 24 2018 at 10:38)](https://leanprover.zulipchat.com/#narrow/stream/113488-general/topic/rewriting%20a%20hypothesis/near/125610611):
so you have about 20 hypotheses all called `this`

#### [Kevin Buzzard (Apr 24 2018 at 10:38)](https://leanprover.zulipchat.com/#narrow/stream/113488-general/topic/rewriting%20a%20hypothesis/near/125610614):
and you won't be able to use most of them

#### [Kevin Buzzard (Apr 24 2018 at 10:38)](https://leanprover.zulipchat.com/#narrow/stream/113488-general/topic/rewriting%20a%20hypothesis/near/125610616):
because `this` will only refer to one of them

#### [Kevin Buzzard (Apr 24 2018 at 10:38)](https://leanprover.zulipchat.com/#narrow/stream/113488-general/topic/rewriting%20a%20hypothesis/near/125610619):
and the rest will be inaccessible

#### [Johan Commelin (Apr 24 2018 at 10:40)](https://leanprover.zulipchat.com/#narrow/stream/113488-general/topic/rewriting%20a%20hypothesis/near/125610691):
```quote
Oh wow, the message everyone was replying to has changed.
```
Yes, still need to figure out how github behaves. Sorry...

#### [Patrick Massot (Apr 24 2018 at 10:41)](https://leanprover.zulipchat.com/#narrow/stream/113488-general/topic/rewriting%20a%20hypothesis/near/125610707):
For the record, the calc version of the previous question:
```lean
example (W X Y Z : Type) (f : W → X) (g : X → Z) (h : W → Y) (j : Y → Z) (w : W) (one : Z)
(Hcom : (λ t, g (f t)) = (λ t, j (h t))) (Hthis : j (h w) = one) : g (f w) = one :=
calc g (f w) = j (h w) : congr_fun Hcom w
         ... = _ : Hthis
```

#### [Johan Commelin (Apr 24 2018 at 10:41)](https://leanprover.zulipchat.com/#narrow/stream/113488-general/topic/rewriting%20a%20hypothesis/near/125610708):
About all the `this`es. My current strategy is to give them a name if I need to. But hopefully things like `rwa` and `apply_assumption` will just figure it out.

#### [Patrick Massot (Apr 24 2018 at 10:42)](https://leanprover.zulipchat.com/#narrow/stream/113488-general/topic/rewriting%20a%20hypothesis/near/125610767):
I guess Kevin/Kenny term proof is a rather direct translation of that calc proof

#### [Kevin Buzzard (Apr 24 2018 at 10:43)](https://leanprover.zulipchat.com/#narrow/stream/113488-general/topic/rewriting%20a%20hypothesis/near/125610778):
yes, `calc` is just some elaborate way of applying `trans`, as we see from the calc docs ;-)

#### [Patrick Massot (Apr 24 2018 at 10:45)](https://leanprover.zulipchat.com/#narrow/stream/113488-general/topic/rewriting%20a%20hypothesis/near/125610843):
I swear I didn't look at your term proof before writing this

#### [Patrick Massot (Apr 24 2018 at 10:45)](https://leanprover.zulipchat.com/#narrow/stream/113488-general/topic/rewriting%20a%20hypothesis/near/125610844):
Because this is what I do with term proof

#### [Patrick Massot (Apr 24 2018 at 10:45)](https://leanprover.zulipchat.com/#narrow/stream/113488-general/topic/rewriting%20a%20hypothesis/near/125610845):
My eyes refuse to stay on them

#### [Kevin Buzzard (Apr 24 2018 at 10:48)](https://leanprover.zulipchat.com/#narrow/stream/113488-general/topic/rewriting%20a%20hypothesis/near/125610944):
eew

#### [Kevin Buzzard (Apr 24 2018 at 10:48)](https://leanprover.zulipchat.com/#narrow/stream/113488-general/topic/rewriting%20a%20hypothesis/near/125610945):
the definition of kernel

#### [Kevin Buzzard (Apr 24 2018 at 10:48)](https://leanprover.zulipchat.com/#narrow/stream/113488-general/topic/rewriting%20a%20hypothesis/near/125610947):
is "the pre-image of the trivial subgroup"

#### [Kevin Buzzard (Apr 24 2018 at 10:48)](https://leanprover.zulipchat.com/#narrow/stream/113488-general/topic/rewriting%20a%20hypothesis/near/125610951):
Is that really better than "the things which map to the identity element"?

#### [Kenny Lau (Apr 24 2018 at 10:48)](https://leanprover.zulipchat.com/#narrow/stream/113488-general/topic/rewriting%20a%20hypothesis/near/125610954):
they don’t like fibres

#### [Kevin Buzzard (Apr 24 2018 at 10:49)](https://leanprover.zulipchat.com/#narrow/stream/113488-general/topic/rewriting%20a%20hypothesis/near/125610957):
`@[simp] lemma mem_trivial [group α] {g : α} : g ∈ trivial α ↔ g = 1`

#### [Kenny Lau (Apr 24 2018 at 10:49)](https://leanprover.zulipchat.com/#narrow/stream/113488-general/topic/rewriting%20a%20hypothesis/near/125610958):
search for fibre in zulip

#### [Kevin Buzzard (Apr 24 2018 at 10:50)](https://leanprover.zulipchat.com/#narrow/stream/113488-general/topic/rewriting%20a%20hypothesis/near/125611012):
I wonder if they have the lemma that h is in ker beta iff beta h = 1? ;-)

#### [Kevin Buzzard (Apr 24 2018 at 10:51)](https://leanprover.zulipchat.com/#narrow/stream/113488-general/topic/rewriting%20a%20hypothesis/near/125611034):
`lemma duh (f : A  → B) [is_group_hom f] (a : A) : a ∈ ker f ↔ f a = 1 := sorry`

#### [Kevin Buzzard (Apr 24 2018 at 10:51)](https://leanprover.zulipchat.com/#narrow/stream/113488-general/topic/rewriting%20a%20hypothesis/near/125611036):
That would definitely be a good start

#### [Johan Commelin (Apr 24 2018 at 10:53)](https://leanprover.zulipchat.com/#narrow/stream/113488-general/topic/rewriting%20a%20hypothesis/near/125611105):
Ok, I have the hypothesis that `m` is bijective. I want to apply the fact that `m` is injective. The definition of `bijective m` is `injective m \and surjective m`. Is there a general tactic that kills this?

#### [Kevin Buzzard (Apr 24 2018 at 10:54)](https://leanprover.zulipchat.com/#narrow/stream/113488-general/topic/rewriting%20a%20hypothesis/near/125611151):
If `H` is a proof of `P \and Q` then `H.1` is a proof of `P`

#### [Kenny Lau (Apr 24 2018 at 10:54)](https://leanprover.zulipchat.com/#narrow/stream/113488-general/topic/rewriting%20a%20hypothesis/near/125611158):
I was going to say that

#### [Kevin Buzzard (Apr 24 2018 at 10:54)](https://leanprover.zulipchat.com/#narrow/stream/113488-general/topic/rewriting%20a%20hypothesis/near/125611162):
Don't bait Patrick

#### [Johan Commelin (Apr 24 2018 at 10:55)](https://leanprover.zulipchat.com/#narrow/stream/113488-general/topic/rewriting%20a%20hypothesis/near/125611184):
Ok, thanks.

#### [Johan Commelin (Apr 24 2018 at 11:01)](https://leanprover.zulipchat.com/#narrow/stream/113488-general/topic/rewriting%20a%20hypothesis/near/125611388):
What is the best way of writing `have := y : B_1 "such that g_1 y = x"`?

#### [Johan Commelin (Apr 24 2018 at 11:01)](https://leanprover.zulipchat.com/#narrow/stream/113488-general/topic/rewriting%20a%20hypothesis/near/125611400):
Ok, that is pseudo-pseudo-Lean

#### [Kevin Buzzard (Apr 24 2018 at 11:02)](https://leanprover.zulipchat.com/#narrow/stream/113488-general/topic/rewriting%20a%20hypothesis/near/125611448):
Maybe you want to know about subtypes now

#### [Kevin Buzzard (Apr 24 2018 at 11:02)](https://leanprover.zulipchat.com/#narrow/stream/113488-general/topic/rewriting%20a%20hypothesis/near/125611450):
There's also `\ex`

#### [Kevin Buzzard (Apr 24 2018 at 11:02)](https://leanprover.zulipchat.com/#narrow/stream/113488-general/topic/rewriting%20a%20hypothesis/near/125611451):
exists

#### [Johan Commelin (Apr 24 2018 at 11:03)](https://leanprover.zulipchat.com/#narrow/stream/113488-general/topic/rewriting%20a%20hypothesis/near/125611461):
ok, maybe that is useful

#### [Kevin Buzzard (Apr 24 2018 at 11:03)](https://leanprover.zulipchat.com/#narrow/stream/113488-general/topic/rewriting%20a%20hypothesis/near/125611463):
`∃ y : B_1, g_1 y = x`

#### [Kevin Buzzard (Apr 24 2018 at 11:03)](https://leanprover.zulipchat.com/#narrow/stream/113488-general/topic/rewriting%20a%20hypothesis/near/125611465):
that's a Prop, so something of that type is a proof of that prop

#### [Kevin Buzzard (Apr 24 2018 at 11:03)](https://leanprover.zulipchat.com/#narrow/stream/113488-general/topic/rewriting%20a%20hypothesis/near/125611470):
and then you can uses `cases` on the proof in tactic mode to get to `y`

#### [Kevin Buzzard (Apr 24 2018 at 11:03)](https://leanprover.zulipchat.com/#narrow/stream/113488-general/topic/rewriting%20a%20hypothesis/near/125611474):
assuming you're in the middle of a proof.

#### [Johan Commelin (Apr 24 2018 at 11:04)](https://leanprover.zulipchat.com/#narrow/stream/113488-general/topic/rewriting%20a%20hypothesis/near/125611479):
ok, going to try that

#### [Kevin Buzzard (Apr 24 2018 at 11:04)](https://leanprover.zulipchat.com/#narrow/stream/113488-general/topic/rewriting%20a%20hypothesis/near/125611518):
If you're in the middle of a construction (i.e. defining something, not proving something) then you need to invoke the axiom of choice to get `y` out ;-)

#### [Kevin Buzzard (Apr 24 2018 at 11:04)](https://leanprover.zulipchat.com/#narrow/stream/113488-general/topic/rewriting%20a%20hypothesis/near/125611534):
The other thing you can do is to actually make a new type -- a subtype

#### [Kevin Buzzard (Apr 24 2018 at 11:05)](https://leanprover.zulipchat.com/#narrow/stream/113488-general/topic/rewriting%20a%20hypothesis/near/125611553):
`X := {y : B_1 // g_1 y = x}`

#### [Kevin Buzzard (Apr 24 2018 at 11:05)](https://leanprover.zulipchat.com/#narrow/stream/113488-general/topic/rewriting%20a%20hypothesis/near/125611564):
Now to build something of that type you need both an element y of B_1 and a proof that g_1 y = x

#### [Kevin Buzzard (Apr 24 2018 at 11:06)](https://leanprover.zulipchat.com/#narrow/stream/113488-general/topic/rewriting%20a%20hypothesis/near/125611610):
and then `⟨y,Hy⟩` has type X, where Hy is the proof

#### [Kevin Buzzard (Apr 24 2018 at 11:06)](https://leanprover.zulipchat.com/#narrow/stream/113488-general/topic/rewriting%20a%20hypothesis/near/125611621):
Or you can build the subset

#### [Kevin Buzzard (Apr 24 2018 at 11:06)](https://leanprover.zulipchat.com/#narrow/stream/113488-general/topic/rewriting%20a%20hypothesis/near/125611635):
`X : set B_1 := {y : B_1 | g_1 y = x}`

#### [Kevin Buzzard (Apr 24 2018 at 11:07)](https://leanprover.zulipchat.com/#narrow/stream/113488-general/topic/rewriting%20a%20hypothesis/near/125611639):
but now X isn't a type, so you can't have things of type X

#### [Kevin Buzzard (Apr 24 2018 at 11:07)](https://leanprover.zulipchat.com/#narrow/stream/113488-general/topic/rewriting%20a%20hypothesis/near/125611650):
X is just the function from B_1 to Prop sending z to the statement that g_1 z = x

#### [Kevin Buzzard (Apr 24 2018 at 11:08)](https://leanprover.zulipchat.com/#narrow/stream/113488-general/topic/rewriting%20a%20hypothesis/near/125611700):
so now the assertion that y has the property you want is literally just `X y`

#### [Kevin Buzzard (Apr 24 2018 at 11:08)](https://leanprover.zulipchat.com/#narrow/stream/113488-general/topic/rewriting%20a%20hypothesis/near/125611705):
but the notation `y ∈ X` also exists

#### [Kevin Buzzard (Apr 24 2018 at 11:08)](https://leanprover.zulipchat.com/#narrow/stream/113488-general/topic/rewriting%20a%20hypothesis/near/125611706):
`\in`

#### [Kevin Buzzard (Apr 24 2018 at 11:08)](https://leanprover.zulipchat.com/#narrow/stream/113488-general/topic/rewriting%20a%20hypothesis/near/125611711):
Which of these three answers you want might depend on what you're doing

#### [Kevin Buzzard (Apr 24 2018 at 11:09)](https://leanprover.zulipchat.com/#narrow/stream/113488-general/topic/rewriting%20a%20hypothesis/near/125611720):
and when I was learning Lean I found it very frustrating that there didn't seem to be a "right" answer for expressing something which in mathematics was unambiguous

#### [Kevin Buzzard (Apr 24 2018 at 11:09)](https://leanprover.zulipchat.com/#narrow/stream/113488-general/topic/rewriting%20a%20hypothesis/near/125611724):
but it's something I've now come to terms with

#### [Kevin Buzzard (Apr 24 2018 at 11:11)](https://leanprover.zulipchat.com/#narrow/stream/113488-general/topic/rewriting%20a%20hypothesis/near/125611796):
@**Kenny Lau** 
```lean
import group_theory.subgroup

open function

universes u

variables {A B : Type u} [group A] [group B]

definition ker (f : A  → B) [is_group_hom f] := is_group_hom.ker f

lemma duh (f : A  → B) [is_group_hom f] (a : A) : a ∈ ker f ↔ f a = 1 := sorry
```

#### [Kevin Buzzard (Apr 24 2018 at 11:11)](https://leanprover.zulipchat.com/#narrow/stream/113488-general/topic/rewriting%20a%20hypothesis/near/125611799):
Ok enough of this, I had better go to work

#### [Kevin Buzzard (Apr 24 2018 at 11:17)](https://leanprover.zulipchat.com/#narrow/stream/113488-general/topic/rewriting%20a%20hypothesis/near/125612020):
but I can't find this in subgroup.lean

#### [Kevin Buzzard (Apr 24 2018 at 11:17)](https://leanprover.zulipchat.com/#narrow/stream/113488-general/topic/rewriting%20a%20hypothesis/near/125612025):
I just found it

#### [Kevin Buzzard (Apr 24 2018 at 11:17)](https://leanprover.zulipchat.com/#narrow/stream/113488-general/topic/rewriting%20a%20hypothesis/near/125612029):
`mem_ker`

#### [Kevin Buzzard (Apr 24 2018 at 11:18)](https://leanprover.zulipchat.com/#narrow/stream/113488-general/topic/rewriting%20a%20hypothesis/near/125612084):
not a simp lemma, presumably because it relies on f

#### [Kevin Buzzard (Apr 24 2018 at 11:18)](https://leanprover.zulipchat.com/#narrow/stream/113488-general/topic/rewriting%20a%20hypothesis/near/125612087):
so is not part of the simp philosophy

#### [Kevin Buzzard (Apr 24 2018 at 11:19)](https://leanprover.zulipchat.com/#narrow/stream/113488-general/topic/rewriting%20a%20hypothesis/near/125612111):
@**Johan Commelin** I think you should open `is_group_hom`

#### [Kevin Buzzard (Apr 24 2018 at 11:20)](https://leanprover.zulipchat.com/#narrow/stream/113488-general/topic/rewriting%20a%20hypothesis/near/125612155):
not least because then you don't have to define `ker`, it is just there for you

#### [Johan Commelin (Apr 24 2018 at 11:20)](https://leanprover.zulipchat.com/#narrow/stream/113488-general/topic/rewriting%20a%20hypothesis/near/125612160):
yes

#### [Johan Commelin (Apr 24 2018 at 11:20)](https://leanprover.zulipchat.com/#narrow/stream/113488-general/topic/rewriting%20a%20hypothesis/near/125612162):
I did that 2 minutes ago

#### [Johan Commelin (Apr 24 2018 at 11:20)](https://leanprover.zulipchat.com/#narrow/stream/113488-general/topic/rewriting%20a%20hypothesis/near/125612166):
the proof is really stupid funny

#### [Johan Commelin (Apr 24 2018 at 11:21)](https://leanprover.zulipchat.com/#narrow/stream/113488-general/topic/rewriting%20a%20hypothesis/near/125612169):
it is almost only `apply_assumption` and `cc`

#### [Johan Commelin (Apr 24 2018 at 11:21)](https://leanprover.zulipchat.com/#narrow/stream/113488-general/topic/rewriting%20a%20hypothesis/near/125612179):
with a very rare `rwa` or `simp`

