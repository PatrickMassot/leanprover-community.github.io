---
layout: page
title: Lean Prover Zulip Chat Archive 
permalink: archive/113488general/85762equationcompiler.html
---

## [general](index.html)
### [equation compiler](85762equationcompiler.html)

#### [Minchao Wu (Jul 24 2018 at 18:56)](https://leanprover.zulipchat.com/#narrow/stream/113488-general/topic/equation%20compiler/near/130222550):
Hi friends, is there a way to fill up this underscore?
```lean
def foo (n : nat) : nat :=
match n with
| 0     := 0
| k     := have k ≠ 0, from _, 
           0
end
```
Usually `n` is of some complicated inductive types, but I really just need to handle one specific constructor. For all the other constructors the proofs are long but exactly the same.  
I could use `rec` or `cases` or `if then else` but that would be awkward. So I am wondering how I can refer to the facts that the equation compiler knows but are not listed as hypotheses?

#### [Kenny Lau (Jul 24 2018 at 18:56)](https://leanprover.zulipchat.com/#narrow/stream/113488-general/topic/equation%20compiler/near/130222560):
use k+1 instead of k

#### [Minchao Wu (Jul 24 2018 at 18:57)](https://leanprover.zulipchat.com/#narrow/stream/113488-general/topic/equation%20compiler/near/130222573):
that works in the case of nat but not other complicated inductive types

#### [Kenny Lau (Jul 24 2018 at 18:57)](https://leanprover.zulipchat.com/#narrow/stream/113488-general/topic/equation%20compiler/near/130222582):
then you can't

#### [Minchao Wu (Jul 24 2018 at 18:59)](https://leanprover.zulipchat.com/#narrow/stream/113488-general/topic/equation%20compiler/near/130222696):
```lean
def bar : bool → ℕ 
| tt     := 0
| b     := have b ≠ tt, from _, 1
```
well maybe this one is a better toy example

#### [Kenny Lau (Jul 24 2018 at 19:00)](https://leanprover.zulipchat.com/#narrow/stream/113488-general/topic/equation%20compiler/near/130222747):
you can't.

#### [Minchao Wu (Jul 24 2018 at 19:00)](https://leanprover.zulipchat.com/#narrow/stream/113488-general/topic/equation%20compiler/near/130222758):
reason?

#### [Kenny Lau (Jul 24 2018 at 19:00)](https://leanprover.zulipchat.com/#narrow/stream/113488-general/topic/equation%20compiler/near/130222768):
in that environment you do not know that b is not tt

#### [Kenny Lau (Jul 24 2018 at 19:01)](https://leanprover.zulipchat.com/#narrow/stream/113488-general/topic/equation%20compiler/near/130222788):
also how do you use `rec` or `cases`?

#### [Minchao Wu (Jul 24 2018 at 19:01)](https://leanprover.zulipchat.com/#narrow/stream/113488-general/topic/equation%20compiler/near/130222792):
but the equation compiler knows that if it's tt then the thing is not exhaustive

#### [Kenny Lau (Jul 24 2018 at 19:01)](https://leanprover.zulipchat.com/#narrow/stream/113488-general/topic/equation%20compiler/near/130222798):
the `b` is a catch-all clause

#### [Kenny Lau (Jul 24 2018 at 19:01)](https://leanprover.zulipchat.com/#narrow/stream/113488-general/topic/equation%20compiler/near/130222801):
it is intended to match everything

#### [Minchao Wu (Jul 24 2018 at 19:01)](https://leanprover.zulipchat.com/#narrow/stream/113488-general/topic/equation%20compiler/near/130222804):
that's true

#### [Minchao Wu (Jul 24 2018 at 19:02)](https://leanprover.zulipchat.com/#narrow/stream/113488-general/topic/equation%20compiler/near/130222864):
I am saying that the compiler knows that tt will never be matched by b

#### [Kenny Lau (Jul 24 2018 at 19:02)](https://leanprover.zulipchat.com/#narrow/stream/113488-general/topic/equation%20compiler/near/130222869):
but that's already outside your environment

#### [Minchao Wu (Jul 24 2018 at 19:03)](https://leanprover.zulipchat.com/#narrow/stream/113488-general/topic/equation%20compiler/near/130222890):
perhaps, so I am asking if there is a clever hack

#### [Kenny Lau (Jul 24 2018 at 19:03)](https://leanprover.zulipchat.com/#narrow/stream/113488-general/topic/equation%20compiler/near/130222892):
what was your idea with `rec` and `cases`?

#### [Minchao Wu (Jul 24 2018 at 19:04)](https://leanprover.zulipchat.com/#narrow/stream/113488-general/topic/equation%20compiler/near/130222941):
> also how do you use `rec` or `cases`?

you just don't use `match`

#### [Kenny Lau (Jul 24 2018 at 19:04)](https://leanprover.zulipchat.com/#narrow/stream/113488-general/topic/equation%20compiler/near/130222950):
```quote
that works in the case of nat but not other complicated inductive types
```
does using `rec` solve this problem?

#### [Minchao Wu (Jul 24 2018 at 19:05)](https://leanprover.zulipchat.com/#narrow/stream/113488-general/topic/equation%20compiler/near/130222965):
it's the same as your suggestion of using `(k+1)`

#### [Minchao Wu (Jul 24 2018 at 19:05)](https://leanprover.zulipchat.com/#narrow/stream/113488-general/topic/equation%20compiler/near/130222983):
namely explicitly writing down all the constructors

#### [Simon Hudon (Jul 24 2018 at 19:28)](https://leanprover.zulipchat.com/#narrow/stream/113488-general/topic/equation%20compiler/near/130224157):
What you could do is:

```
begin
  cases n,
  case 0 : 
  { /- proof -/ },
  all_goals { /- proof -/ },
end

#### [Kenny Lau (Jul 24 2018 at 19:28)](https://leanprover.zulipchat.com/#narrow/stream/113488-general/topic/equation%20compiler/near/130224169):
but how are you going to prove n != 0?

#### [Johan Commelin (Jul 24 2018 at 19:31)](https://leanprover.zulipchat.com/#narrow/stream/113488-general/topic/equation%20compiler/near/130224343):
I think that you don't have to.

#### [Johan Commelin (Jul 24 2018 at 19:31)](https://leanprover.zulipchat.com/#narrow/stream/113488-general/topic/equation%20compiler/near/130224351):
That is Simon's trick.

#### [Johan Commelin (Jul 24 2018 at 19:32)](https://leanprover.zulipchat.com/#narrow/stream/113488-general/topic/equation%20compiler/near/130224422):
You just prove it case by case, for all cases. But then, you prove all but one case with a single proof.

#### [Minchao Wu (Jul 24 2018 at 19:33)](https://leanprover.zulipchat.com/#narrow/stream/113488-general/topic/equation%20compiler/near/130224489):
I forgot to mention that foll all the other cases I need the fact that n!=0

#### [Minchao Wu (Jul 24 2018 at 19:34)](https://leanprover.zulipchat.com/#narrow/stream/113488-general/topic/equation%20compiler/near/130224536):
but this trick might work

#### [Johan Commelin (Jul 24 2018 at 19:35)](https://leanprover.zulipchat.com/#narrow/stream/113488-general/topic/equation%20compiler/near/130224585):
Right, so now you somehow need to know that fact, but now it should be even true in your environment (I hope).

#### [Simon Hudon (Jul 24 2018 at 19:35)](https://leanprover.zulipchat.com/#narrow/stream/113488-general/topic/equation%20compiler/near/130224590):
 Off the top of my head, `cases h : n` will preserve the variable n and you can do your proof with `subst n` and `contradiction`

#### [Simon Hudon (Jul 24 2018 at 19:44)](https://leanprover.zulipchat.com/#narrow/stream/113488-general/topic/equation%20compiler/near/130225161):
concretely, here is how I do it:

```lean
def foo (n : nat) : nat :=
begin
  cases h : n,
  case nat.zero : 
  { exact 0 },
  all_goals
  { have : n ≠ 0,
    { subst n, contradiction },
    exact n },
end
```

#### [Simon Hudon (Jul 24 2018 at 19:45)](https://leanprover.zulipchat.com/#narrow/stream/113488-general/topic/equation%20compiler/near/130225220):
(deleted)

#### [Minchao Wu (Jul 24 2018 at 19:47)](https://leanprover.zulipchat.com/#narrow/stream/113488-general/topic/equation%20compiler/near/130225363):
when you use `cases 0:` to handle the specific constructor, how do you supply the arguments to that constructor?

#### [Minchao Wu (Jul 24 2018 at 19:47)](https://leanprover.zulipchat.com/#narrow/stream/113488-general/topic/equation%20compiler/near/130225389):
in the case of nat there is no parameters

#### [Simon Hudon (Jul 24 2018 at 19:48)](https://leanprover.zulipchat.com/#narrow/stream/113488-general/topic/equation%20compiler/near/130225432):
(note that it's `case nat.zero :`, no s, and full constructor name)

#### [Simon Hudon (Jul 24 2018 at 19:48)](https://leanprover.zulipchat.com/#narrow/stream/113488-general/topic/equation%20compiler/near/130225455):
if we were looking at a list for instance, it would be `case list.cons : x xs { /- my proof -/ }`

#### [Minchao Wu (Jul 24 2018 at 19:59)](https://leanprover.zulipchat.com/#narrow/stream/113488-general/topic/equation%20compiler/near/130226138):
Very cool, it worked

#### [Minchao Wu (Jul 24 2018 at 19:59)](https://leanprover.zulipchat.com/#narrow/stream/113488-general/topic/equation%20compiler/near/130226143):
Thanks!

#### [Minchao Wu (Jul 24 2018 at 20:00)](https://leanprover.zulipchat.com/#narrow/stream/113488-general/topic/equation%20compiler/near/130226210):
I wasn't aware of the `case` tatic

#### [Simon Hudon (Jul 24 2018 at 20:00)](https://leanprover.zulipchat.com/#narrow/stream/113488-general/topic/equation%20compiler/near/130226238):
The more you know :wink:

#### [Minchao Wu (Jul 24 2018 at 20:00)](https://leanprover.zulipchat.com/#narrow/stream/113488-general/topic/equation%20compiler/near/130226248):
I'm going to embrace it from now on :)

#### [Nicholas Scheel (Jul 25 2018 at 01:14)](https://leanprover.zulipchat.com/#narrow/stream/113488-general/topic/equation%20compiler/near/130244135):
(deleted)

