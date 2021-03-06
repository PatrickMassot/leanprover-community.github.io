---
layout: page
title: Lean Prover Zulip Chat Archive 
permalink: archive/116395maths/55685realpowers.html
---

## [maths](index.html)
### [real powers](55685realpowers.html)

#### [Chris Hughes (Nov 04 2018 at 16:27)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/real%20powers/near/137159650):
If we did `has_pow real real`, what would `(-1)^(1/3)` be?

#### [Kevin Buzzard (Nov 04 2018 at 16:28)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/real%20powers/near/137159654):
nonono

#### [Kevin Buzzard (Nov 04 2018 at 16:28)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/real%20powers/near/137159696):
real^real is surely not a good idea

#### [Kevin Buzzard (Nov 04 2018 at 16:28)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/real%20powers/near/137159699):
what would (-1)^(1/4) be?

#### [Kevin Buzzard (Nov 04 2018 at 16:29)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/real%20powers/near/137159702):
If you want real^real then I would suggest setting $$a^b=0$$ if $$a\leq 0$$

#### [Kevin Buzzard (Nov 04 2018 at 16:29)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/real%20powers/near/137159729):
You can make sense of $$a^b$$ for $$a$$ a positive real and $$b$$ any complex number, it should be $$\exp(b\log(a))$$

#### [Johan Commelin (Nov 04 2018 at 16:30)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/real%20powers/near/137159778):
```quote
If you want real^real then I would suggest setting $$a^b=0$$ if $$a\leq 0$$
```
I am quite sure you made a typo. That should have been $$a^b = 37$$.

#### [Kevin Buzzard (Nov 04 2018 at 16:30)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/real%20powers/near/137159779):
you can make sense of $$a^b$$ for $$a$$ any non-zero complex number and $$b$$ any integer

#### [Kevin Buzzard (Nov 04 2018 at 16:30)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/real%20powers/near/137159784):
I would have put 37 but maybe $$0^{37}$$ should be 0...

#### [Johannes Hölzl (Nov 04 2018 at 17:19)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/real%20powers/near/137161598):
@**Chris Hughes**  the usual thing: we totalize it. I think for `log` we can force it to by symmetric. either a long the $$y$$-axis, or through the origin. For power on $$\mathbb{R}$$ you might want to have $$a^b = |a|^b$$ or similar, and of course $$0^a = 0$$.

#### [Chris Hughes (Nov 04 2018 at 17:21)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/real%20powers/near/137161689):
Don't we want $$0^0 = 1$$?

#### [Kevin Buzzard (Nov 04 2018 at 17:22)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/real%20powers/near/137161736):
I think you want 0^0 = undefined if both those 0's are real numbers

#### [Johannes Hölzl (Nov 04 2018 at 17:22)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/real%20powers/near/137161738):
I don't think there is a natural choice to totalize it. Theorems about `log` and `pow` will always assume that the argument is non-negative.

#### [Kevin Buzzard (Nov 04 2018 at 17:22)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/real%20powers/near/137161741):
and undefined := 0 in Lean

#### [Johannes Hölzl (Nov 04 2018 at 17:22)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/real%20powers/near/137161742):
Undefined means we are free to choose a value

#### [Johannes Hölzl (Nov 04 2018 at 17:22)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/real%20powers/near/137161748):
and maybe for `pow`, $$0^0 = 1$$ makes more sense. I don't know.

#### [Kevin Buzzard (Nov 04 2018 at 17:22)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/real%20powers/near/137161749):
There's certainly a case for (0 : real) ^ (0 : nat) = 1

#### [Johannes Hölzl (Nov 04 2018 at 17:23)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/real%20powers/near/137161766):
Yes: $$a^{n : \mathbb{R}}= a^n$$ should hold

#### [Johannes Hölzl (Nov 04 2018 at 17:24)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/real%20powers/near/137161813):
so 'real'-power should extend 'int'-power should extend 'nat'-power

#### [Chris Hughes (Nov 04 2018 at 17:24)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/real%20powers/near/137161815):
But that doesn't work if $$a^n = \mid a\mid^n$$

#### [Mario Carneiro (Nov 04 2018 at 17:28)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/real%20powers/near/137161933):
0^a = 0 unless a = 0, otherwise 1

#### [Johannes Hölzl (Nov 04 2018 at 17:28)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/real%20powers/near/137161973):
right it doesn't extend `int`-power. And I don't see a sensible default where it would. we could check if `floor` or `ceil` of the argument is odd/even, but this feels too forced

#### [Mario Carneiro (Nov 04 2018 at 17:28)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/real%20powers/near/137161979):
I have this in the metamath definition, with the if and everything

#### [Mario Carneiro (Nov 04 2018 at 17:29)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/real%20powers/near/137161985):
for negative powers I used complexes, because there was only one definition complex ^ complex, of course that's not an option here

#### [Chris Hughes (Nov 04 2018 at 17:29)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/real%20powers/near/137161999):
In metamath is $$(-1)^{1/3} = -1$$

#### [Mario Carneiro (Nov 04 2018 at 17:29)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/real%20powers/near/137162004):
no, it's e^2pi i/3

#### [Kevin Buzzard (Nov 04 2018 at 17:30)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/real%20powers/near/137162052):
that ain't no real

#### [Mario Carneiro (Nov 04 2018 at 17:30)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/real%20powers/near/137162057):
like I said, complex

#### [Mario Carneiro (Nov 04 2018 at 17:30)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/real%20powers/near/137162065):
I don't think we should try for the rational extension, it's crazy and not at all complete

#### [Johannes Hölzl (Nov 04 2018 at 17:30)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/real%20powers/near/137162066):
okay, what about using `a^b = Re (a ^ b)`?

#### [Kevin Buzzard (Nov 04 2018 at 17:30)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/real%20powers/near/137162072):
You want to define the Riemann Zeta function for complex s with Re(s)>1 as the infinite sum of n^{-s}

#### [Johannes Hölzl (Nov 04 2018 at 17:31)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/real%20powers/near/137162080):
where the left one is on reals and right of the equality is the complex power?

#### [Mario Carneiro (Nov 04 2018 at 17:31)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/real%20powers/near/137162087):
that could work...

#### [Johannes Hölzl (Nov 04 2018 at 17:31)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/real%20powers/near/137162091):
AFAIU it is an extension of `int`-power  and it is continuous

#### [Mario Carneiro (Nov 04 2018 at 17:32)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/real%20powers/near/137162136):
except of course where it isn't

#### [Mario Carneiro (Nov 04 2018 at 17:32)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/real%20powers/near/137162167):
I think the power function is discontinuous at 0,0 no matter what you do

#### [Johannes Hölzl (Nov 04 2018 at 17:32)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/real%20powers/near/137162175):
argh, yes

#### [Kevin Buzzard (Nov 04 2018 at 17:32)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/real%20powers/near/137162176):
not if you restrict the power to be in nat

#### [Mario Carneiro (Nov 04 2018 at 17:33)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/real%20powers/near/137162187):
and there is probably a branch cut somewhere that will survive in the real version

#### [Kevin Buzzard (Nov 04 2018 at 17:33)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/real%20powers/near/137162188):
for example, when evaluating a polynomial, it's essential that x^0 gets sent to 1

#### [Kevin Buzzard (Nov 04 2018 at 17:33)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/real%20powers/near/137162190):
but that 0 is 0:nat

#### [Mario Carneiro (Nov 04 2018 at 17:33)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/real%20powers/near/137162193):
right, I am 100% of the view that 0^0 = 1

#### [Kevin Buzzard (Nov 04 2018 at 17:33)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/real%20powers/near/137162199):
but my point is that this makes things continuous in this domain of real x nat -> real

#### [Kevin Buzzard (Nov 04 2018 at 17:34)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/real%20powers/near/137162239):
oh

#### [Mario Carneiro (Nov 04 2018 at 17:34)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/real%20powers/near/137162240):
a lot of crazy mathematicians use "everything is continuous" ism to justify claiming that it is undefined there

#### [Johannes Hölzl (Nov 04 2018 at 17:34)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/real%20powers/near/137162244):
in this case one wants to use `pow : nat -> real -> real` anyway. I think the case we are discussing now is how to define `pow : real -> real -> real`

#### [Kevin Buzzard (Nov 04 2018 at 17:34)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/real%20powers/near/137162248):
but one issue is whether it should extend the nat version

#### [Mario Carneiro (Nov 04 2018 at 17:34)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/real%20powers/near/137162251):
of course, that should be easy

#### [Johannes Hölzl (Nov 04 2018 at 17:35)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/real%20powers/near/137162261):
I agree, it should extend the `nat`-version. and it would be nice if we could extend the `int` version in a sensible way

#### [Mario Carneiro (Nov 04 2018 at 17:35)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/real%20powers/near/137162262):
extending int should also be possible

#### [Kevin Buzzard (Nov 04 2018 at 17:35)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/real%20powers/near/137162266):
I know a lot of crazy computer scientists use "everything must extend what we already have in every case even if answers are junk"ism...

#### [Mario Carneiro (Nov 04 2018 at 17:35)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/real%20powers/near/137162273):
extending to rat is possible but a bad idea in my view

#### [Kevin Buzzard (Nov 04 2018 at 17:35)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/real%20powers/near/137162274):
I think (0 : real) ^ (0 : real) is junk so should be 0

#### [Mario Carneiro (Nov 04 2018 at 17:35)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/real%20powers/near/137162278):
lolno

#### [Kevin Buzzard (Nov 04 2018 at 17:36)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/real%20powers/near/137162315):
but (0 : real) ^ (0 : nat) is not junk so should be 1

#### [Chris Hughes (Nov 04 2018 at 17:36)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/real%20powers/near/137162322):
Noooo

#### [Kevin Buzzard (Nov 04 2018 at 17:36)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/real%20powers/near/137162329):
:-)

#### [Johannes Hölzl (Nov 04 2018 at 17:36)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/real%20powers/near/137162331):
we don't extend everything. In Isabelle the logarithm of a negative argument is undefined in the sense of a fixed but unknown value

#### [Chris Hughes (Nov 04 2018 at 17:36)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/real%20powers/near/137162335):
But then `cast_pow` requires proving things are non zero.

#### [Mario Carneiro (Nov 04 2018 at 17:36)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/real%20powers/near/137162343):
I was not sure about log of negatives either

#### [Mario Carneiro (Nov 04 2018 at 17:37)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/real%20powers/near/137162348):
log of 0 is even worse

#### [Kevin Buzzard (Nov 04 2018 at 17:37)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/real%20powers/near/137162349):
junk!

#### [Kevin Buzzard (Nov 04 2018 at 17:37)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/real%20powers/near/137162352):
37

#### [Mario Carneiro (Nov 04 2018 at 17:37)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/real%20powers/near/137162359):
log x = log |x| makes some calculus stuff very slightly slicker

#### [Mario Carneiro (Nov 04 2018 at 17:38)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/real%20powers/near/137162408):
but I don't think it will come up much anyway

#### [Johannes Hölzl (Nov 04 2018 at 17:38)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/real%20powers/near/137162409):
What about `sgn x * log |x|`?  I think both have their advantages/disadvantages.

#### [Mario Carneiro (Nov 04 2018 at 17:38)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/real%20powers/near/137162412):
whoa

#### [Mario Carneiro (Nov 04 2018 at 17:38)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/real%20powers/near/137162415):
what is that for?

#### [Mario Carneiro (Nov 04 2018 at 17:39)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/real%20powers/near/137162430):
it looks cool on the graph paper in my head...

#### [Johannes Hölzl (Nov 04 2018 at 17:40)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/real%20powers/near/137162481):
I think there were some cases where it could have been helpful. But I don't remember the exact statements where it would save some non-negativity assumption. But yes the graph looks nice :-)

#### [Johannes Hölzl (Nov 04 2018 at 17:43)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/real%20powers/near/137162601):
But `x /= 0 -> y /= 0 -> log (x * y) = log x + log y` only works for the `log x = log |x|` case

#### [Kevin Buzzard (Nov 04 2018 at 17:43)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/real%20powers/near/137162613):
that's a junk theorem!

#### [Kevin Buzzard (Nov 04 2018 at 17:44)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/real%20powers/near/137162668):
This islike you trying to figure out what the square root of anegative number should be so that sqrt(ab)=sqrt(a)sqrt(b) always works. Nobody who wants to apply that theorem will have a,b<0

#### [Mario Carneiro (Nov 04 2018 at 17:45)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/real%20powers/near/137162682):
sometimes a,b>0 but it's a hassle to prove

#### [Kevin Buzzard (Nov 04 2018 at 17:45)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/real%20powers/near/137162687):
you can't say "x != 0" is any better than "x > 0". It's still a precondition, so tehe user has to supply something

#### [Johannes Hölzl (Nov 04 2018 at 17:45)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/real%20powers/near/137162700):
but sometimes `x !=0` is easier to proof than `x > 0`.

#### [Kevin Buzzard (Nov 04 2018 at 17:45)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/real%20powers/near/137162712):
*boggle*

#### [Mario Carneiro (Nov 04 2018 at 17:46)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/real%20powers/near/137162752):
I mean it is literally a weaker hypothesis

#### [Kevin Buzzard (Nov 04 2018 at 17:46)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/real%20powers/near/137162753):
if you're in a situation where you're taking logs and you don't have x>0 as a hypothesis then something is seriously wrong with your local context anyway

#### [Chris Hughes (Nov 04 2018 at 17:46)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/real%20powers/near/137162756):
Proving things are $$>0$$ is cheap on paper but expensive in lean. Keeping track of which theorems are randomly true for some non-intuitive definition is cheap in Lean but expensive on paper.

#### [Mario Carneiro (Nov 04 2018 at 17:46)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/real%20powers/near/137162764):
you had it in your context once, then you did 5 rewrites and it's not obviously true any more

#### [Kevin Buzzard (Nov 04 2018 at 17:47)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/real%20powers/near/137162781):
I did see that in a 1st year's code recently -- "let H2 := H,..." and I thought "wooah what is this fool doing?" and then I understood that they wanted to rewrite H but keep track of it anyway

#### [Mario Carneiro (Nov 04 2018 at 17:49)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/real%20powers/near/137162834):
those could be some combination of rewrites to the log(s) and rewrites to the hypothesis too

#### [Mario Carneiro (Nov 04 2018 at 17:49)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/real%20powers/near/137162843):
What are the preconditions to `log (log (log x + 1)) < 3`?

#### [Kevin Buzzard (Nov 04 2018 at 17:50)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/real%20powers/near/137162849):
x>>0

#### [Mario Carneiro (Nov 04 2018 at 17:50)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/real%20powers/near/137162897):
but not too >> or else it won't be `< 3` :)

#### [Kevin Buzzard (Nov 04 2018 at 17:50)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/real%20powers/near/137162907):
If it's too >> then it's false. If it's not >> enough then it makes no sense

#### [Kevin Buzzard (Nov 04 2018 at 17:51)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/real%20powers/near/137162919):
it's NaN

#### [Mario Carneiro (Nov 04 2018 at 17:51)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/real%20powers/near/137162921):
unfortunately (or fortunately), `real` has no NaN

#### [Mario Carneiro (Nov 04 2018 at 17:51)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/real%20powers/near/137162928):
just ask anyone who has dealt with IEEE floats, NaN is a mess

#### [Kevin Buzzard (Nov 04 2018 at 17:51)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/real%20powers/near/137162929):
If you say to a mathematician "this is true for x=20" they will assume you mean that the LHS evaluates to something meaningful in maths

#### [Mario Carneiro (Nov 04 2018 at 17:52)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/real%20powers/near/137162970):
right, and that's one of the more expensive in lean things to do

#### [Mario Carneiro (Nov 04 2018 at 17:53)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/real%20powers/near/137162980):
you might think "we could just have preconditions on `log` and then it would all make sense" but that would just make the problem worse

#### [Kevin Buzzard (Nov 04 2018 at 17:53)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/real%20powers/near/137162987):
I think we need a `with_NaN` structure

#### [Mario Carneiro (Nov 04 2018 at 17:54)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/real%20powers/near/137163030):
`with_bot`?

#### [Kevin Buzzard (Nov 04 2018 at 17:54)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/real%20powers/near/137163033):
but it might not be a bottom

#### [Mario Carneiro (Nov 04 2018 at 17:54)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/real%20powers/near/137163035):
or equal to itself..

#### [Kevin Buzzard (Nov 04 2018 at 17:54)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/real%20powers/near/137163043):
well obviously we'd have to modify eq

#### [Mario Carneiro (Nov 04 2018 at 17:54)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/real%20powers/near/137163045):
obviously

#### [Kevin Buzzard (Nov 04 2018 at 17:55)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/real%20powers/near/137163057):
we need not_a_Type

#### [Kevin Buzzard (Nov 04 2018 at 17:55)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/real%20powers/near/137163064):
or not_a_term or something

#### [Mario Carneiro (Nov 04 2018 at 17:56)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/real%20powers/near/137163122):
it was silly of us to assume that all types have a reflexive relation... we should generalize to semitypes

#### [Kevin Buzzard (Nov 04 2018 at 17:56)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/real%20powers/near/137163129):
rofl that's clearly what these guys have been missing for the last 100 years

#### [Kevin Buzzard (Nov 04 2018 at 17:56)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/real%20powers/near/137163140):
we realised we needed semimodules

#### [Kevin Buzzard (Nov 04 2018 at 17:56)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/real%20powers/near/137163145):
it was only a matter of time before we had the real breakthrough

#### [Mario Carneiro (Nov 04 2018 at 17:57)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/real%20powers/near/137163172):
I joke, but PERs (partial equivalence relations) as types are a thing

#### [Mario Carneiro (Nov 04 2018 at 17:57)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/real%20powers/near/137163177):
nuprl uses it

#### [Kevin Buzzard (Nov 04 2018 at 17:57)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/real%20powers/near/137163181):
is that where you drop reflexivity?

#### [Mario Carneiro (Nov 04 2018 at 17:57)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/real%20powers/near/137163183):
yeah

#### [Kevin Buzzard (Nov 04 2018 at 17:58)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/real%20powers/near/137163222):
so you get equivalence classes and then some wasteland

#### [Kevin Buzzard (Nov 04 2018 at 17:58)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/real%20powers/near/137163229):
of terms which are related to nothing

#### [Mario Carneiro (Nov 04 2018 at 17:58)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/real%20powers/near/137163236):
it's just an equivalence relation on a subtype

#### [Kevin Buzzard (Nov 04 2018 at 17:58)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/real%20powers/near/137163238):
right

#### [Mario Carneiro (Nov 04 2018 at 17:58)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/real%20powers/near/137163245):
In type theory it has the purpose of rolling subtyping and quotients into one construct

#### [Mario Carneiro (Nov 04 2018 at 17:59)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/real%20powers/near/137163259):
so you get some nice categorical structure

