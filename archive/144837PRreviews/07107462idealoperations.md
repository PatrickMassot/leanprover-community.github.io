---
layout: page
title: Lean Prover Zulip Chat Archive 
permalink: archive/144837PRreviews/07107462idealoperations.html
---

## [PR reviews](index.html)
### [#462 ideal operations](07107462idealoperations.html)

#### [Kenny Lau (Nov 07 2018 at 13:29)](https://leanprover.zulipchat.com/#narrow/stream/144837-PR%20reviews/topic/%23462%20ideal%20operations/near/146936148):
@**Kevin Buzzard** @**Mario Carneiro** `pow` comes for free after I've proved semiring! :D

#### [Kenny Lau (Nov 07 2018 at 13:30)](https://leanprover.zulipchat.com/#narrow/stream/144837-PR%20reviews/topic/%23462%20ideal%20operations/near/146936223):
and about `map`: I don't really see how useful it would be @**Johan Commelin**

#### [Kenny Lau (Nov 07 2018 at 13:40)](https://leanprover.zulipchat.com/#narrow/stream/144837-PR%20reviews/topic/%23462%20ideal%20operations/near/146936726):
@**Mario Carneiro** why don't we prove that `submodule.map` and `submodule.comap` form a galois connection?

#### [Mario Carneiro (Nov 07 2018 at 13:41)](https://leanprover.zulipchat.com/#narrow/stream/144837-PR%20reviews/topic/%23462%20ideal%20operations/near/146936749):
sure, it's one line

#### [Kenny Lau (Nov 07 2018 at 13:41)](https://leanprover.zulipchat.com/#narrow/stream/144837-PR%20reviews/topic/%23462%20ideal%20operations/near/146936755):
I mean, why didn't we?

#### [Kenny Lau (Nov 07 2018 at 13:41)](https://leanprover.zulipchat.com/#narrow/stream/144837-PR%20reviews/topic/%23462%20ideal%20operations/near/146936763):
you could derive some other theorems from this galois connection, right?

#### [Johan Commelin (Nov 07 2018 at 13:52)](https://leanprover.zulipchat.com/#narrow/stream/144837-PR%20reviews/topic/%23462%20ideal%20operations/near/146937375):
@**Kenny Lau** I think `map` will be very useful. If `I : ideal R` and `f : R → S` you see mathematicians writing `I.S` all the time for the ideal generated by `I` in `S`.

#### [Kevin Buzzard (Nov 07 2018 at 13:53)](https://leanprover.zulipchat.com/#narrow/stream/144837-PR%20reviews/topic/%23462%20ideal%20operations/near/146937400):
`comap` is used to show that `Spec` is a functor.

#### [Johan Commelin (Nov 07 2018 at 13:53)](https://leanprover.zulipchat.com/#narrow/stream/144837-PR%20reviews/topic/%23462%20ideal%20operations/near/146937405):
And implicitly we are using all the time that it behaves well in certain ways. Which are exactly the little lemmas in the beginning of A–MD.

#### [Kenny Lau (Nov 07 2018 at 14:40)](https://leanprover.zulipchat.com/#narrow/stream/144837-PR%20reviews/topic/%23462%20ideal%20operations/near/146940064):
@**Kevin Buzzard** @**Johan Commelin** added `map`. this might be the only time I use `ge` instead of `le`.

#### [Kenny Lau (Nov 07 2018 at 14:46)](https://leanprover.zulipchat.com/#narrow/stream/144837-PR%20reviews/topic/%23462%20ideal%20operations/near/146940426):
my laptop now has 27% battery

#### [Patrick Massot (Nov 07 2018 at 14:47)](https://leanprover.zulipchat.com/#narrow/stream/144837-PR%20reviews/topic/%23462%20ideal%20operations/near/146940454):
why did you use `ge`?

#### [Kenny Lau (Nov 07 2018 at 14:55)](https://leanprover.zulipchat.com/#narrow/stream/144837-PR%20reviews/topic/%23462%20ideal%20operations/near/146940909):
because the right hand side was simpler

#### [Kenny Lau (Nov 07 2018 at 15:19)](https://leanprover.zulipchat.com/#narrow/stream/144837-PR%20reviews/topic/%23462%20ideal%20operations/near/146942312):
I guess I’ll switch it back

#### [Kenny Lau (Nov 07 2018 at 15:19)](https://leanprover.zulipchat.com/#narrow/stream/144837-PR%20reviews/topic/%23462%20ideal%20operations/near/146942314):
I guess I’ll switch it back

#### [Kenny Lau (Nov 07 2018 at 16:15)](https://leanprover.zulipchat.com/#narrow/stream/144837-PR%20reviews/topic/%23462%20ideal%20operations/near/146964872):
@**Johan Commelin** @**Kevin Buzzard** do you have any other requests?

#### [Kenny Lau (Nov 07 2018 at 16:16)](https://leanprover.zulipchat.com/#narrow/stream/144837-PR%20reviews/topic/%23462%20ideal%20operations/near/146964942):
i have 2 hours of train

#### [Kevin Buzzard (Nov 07 2018 at 16:16)](https://leanprover.zulipchat.com/#narrow/stream/144837-PR%20reviews/topic/%23462%20ideal%20operations/near/146964974):
Nullstellensatz?

#### [Kevin Buzzard (Nov 07 2018 at 16:17)](https://leanprover.zulipchat.com/#narrow/stream/144837-PR%20reviews/topic/%23462%20ideal%20operations/near/146964983):
Not that I ever use it

#### [Kevin Buzzard (Nov 07 2018 at 16:17)](https://leanprover.zulipchat.com/#narrow/stream/144837-PR%20reviews/topic/%23462%20ideal%20operations/near/146965009):
Completion of a ring WRT an ideal

#### [Patrick Massot (Nov 07 2018 at 16:17)](https://leanprover.zulipchat.com/#narrow/stream/144837-PR%20reviews/topic/%23462%20ideal%20operations/near/146965014):
Integral elements!

#### [Kevin Buzzard (Nov 07 2018 at 16:17)](https://leanprover.zulipchat.com/#narrow/stream/144837-PR%20reviews/topic/%23462%20ideal%20operations/near/146965017):
oh wait Patrick might have done that

#### [Kevin Buzzard (Nov 07 2018 at 16:17)](https://leanprover.zulipchat.com/#narrow/stream/144837-PR%20reviews/topic/%23462%20ideal%20operations/near/146965034):
Integral elements , as Patrick says

#### [Johan Commelin (Nov 07 2018 at 16:18)](https://leanprover.zulipchat.com/#narrow/stream/144837-PR%20reviews/topic/%23462%20ideal%20operations/near/146965101):
Right, I think integral closure would be a reasonable next step.

#### [Kenny Lau (Nov 07 2018 at 16:21)](https://leanprover.zulipchat.com/#narrow/stream/144837-PR%20reviews/topic/%23462%20ideal%20operations/near/146965271):
I mean, regarding this PR

#### [Kenny Lau (Nov 07 2018 at 16:21)](https://leanprover.zulipchat.com/#narrow/stream/144837-PR%20reviews/topic/%23462%20ideal%20operations/near/146965276):
also, how should I call (M:N)?

#### [Johan Commelin (Nov 07 2018 at 16:21)](https://leanprover.zulipchat.com/#narrow/stream/144837-PR%20reviews/topic/%23462%20ideal%20operations/near/146965296):
What is it?

#### [Kenny Lau (Nov 07 2018 at 16:21)](https://leanprover.zulipchat.com/#narrow/stream/144837-PR%20reviews/topic/%23462%20ideal%20operations/near/146965303):
x such that xN <= M

#### [Johan Commelin (Nov 07 2018 at 16:22)](https://leanprover.zulipchat.com/#narrow/stream/144837-PR%20reviews/topic/%23462%20ideal%20operations/near/146965365):
Ok, so it is not some sort of index of a submodule.

#### [Kenny Lau (Nov 07 2018 at 16:22)](https://leanprover.zulipchat.com/#narrow/stream/144837-PR%20reviews/topic/%23462%20ideal%20operations/near/146965377):
that would be []

#### [Johan Commelin (Nov 07 2018 at 16:22)](https://leanprover.zulipchat.com/#narrow/stream/144837-PR%20reviews/topic/%23462%20ideal%20operations/near/146965384):
Aah, of course.

#### [Patrick Massot (Nov 07 2018 at 16:23)](https://leanprover.zulipchat.com/#narrow/stream/144837-PR%20reviews/topic/%23462%20ideal%20operations/near/146965443):
Ok, Kenny. We need to be able to write the I^n\cdots D that is at the very bottom of Page 73  of https://www2.math.uni-paderborn.de/fileadmin/Mathematik/People/wedhorn/Lehre/AdicSpaces.pdf

#### [Johan Commelin (Nov 07 2018 at 16:24)](https://leanprover.zulipchat.com/#narrow/stream/144837-PR%20reviews/topic/%23462%20ideal%20operations/near/146965491):
So, this looks like the fractional quotient, but it isn't exactly that, right?

#### [Johan Commelin (Nov 07 2018 at 16:24)](https://leanprover.zulipchat.com/#narrow/stream/144837-PR%20reviews/topic/%23462%20ideal%20operations/near/146965543):
```quote
Ok, Kenny. We need to be able to write the I^n\cdots D that is at the very bottom of Page 73  of https://www2.math.uni-paderborn.de/fileadmin/Mathematik/People/wedhorn/Lehre/AdicSpaces.pdf
```
Hmmm, there quite a lot of abuse of notation going on there...

#### [Patrick Massot (Nov 07 2018 at 16:25)](https://leanprover.zulipchat.com/#narrow/stream/144837-PR%20reviews/topic/%23462%20ideal%20operations/near/146965564):
Yes, we want abuse of notations

#### [Kenny Lau (Nov 07 2018 at 16:25)](https://leanprover.zulipchat.com/#narrow/stream/144837-PR%20reviews/topic/%23462%20ideal%20operations/near/146965565):
@**Patrick Massot** I think we can already write that

#### [Patrick Massot (Nov 07 2018 at 16:25)](https://leanprover.zulipchat.com/#narrow/stream/144837-PR%20reviews/topic/%23462%20ideal%20operations/near/146965584):
I is an ideal and D is a subring (except that I is an ideal not in the same ring as D)

#### [Kenny Lau (Nov 07 2018 at 16:25)](https://leanprover.zulipchat.com/#narrow/stream/144837-PR%20reviews/topic/%23462%20ideal%20operations/near/146965587):
@**Johan Commelin** AM calls it quotient, but I don’t think we want this name in Lean

#### [Patrick Massot (Nov 07 2018 at 16:25)](https://leanprover.zulipchat.com/#narrow/stream/144837-PR%20reviews/topic/%23462%20ideal%20operations/near/146965603):
because D is in the localization

#### [Kenny Lau (Nov 07 2018 at 16:25)](https://leanprover.zulipchat.com/#narrow/stream/144837-PR%20reviews/topic/%23462%20ideal%20operations/near/146965604):
then what is I^n • D supposed to mean?

#### [Johan Commelin (Nov 07 2018 at 16:26)](https://leanprover.zulipchat.com/#narrow/stream/144837-PR%20reviews/topic/%23462%20ideal%20operations/near/146965631):
I don't think it is actually used.

#### [Johan Commelin (Nov 07 2018 at 16:26)](https://leanprover.zulipchat.com/#narrow/stream/144837-PR%20reviews/topic/%23462%20ideal%20operations/near/146965658):
Sorry, we are having to discussions interleaved...

#### [Patrick Massot (Nov 07 2018 at 16:26)](https://leanprover.zulipchat.com/#narrow/stream/144837-PR%20reviews/topic/%23462%20ideal%20operations/near/146965660):
Crap, I'm getting to Offenburg. I'll lose wifi

#### [Kenny Lau (Nov 07 2018 at 16:26)](https://leanprover.zulipchat.com/#narrow/stream/144837-PR%20reviews/topic/%23462%20ideal%20operations/near/146965669):
well the annihilator is used

#### [Patrick Massot (Nov 07 2018 at 16:26)](https://leanprover.zulipchat.com/#narrow/stream/144837-PR%20reviews/topic/%23462%20ideal%20operations/near/146965672):
I'll let Johan explain the abuse of notation

#### [Kenny Lau (Nov 07 2018 at 16:26)](https://leanprover.zulipchat.com/#narrow/stream/144837-PR%20reviews/topic/%23462%20ideal%20operations/near/146965675):
and this quotient is a generalisation

#### [Johan Commelin (Nov 07 2018 at 16:27)](https://leanprover.zulipchat.com/#narrow/stream/144837-PR%20reviews/topic/%23462%20ideal%20operations/near/146965701):
Sure, annihilators are used.

#### [Johan Commelin (Nov 07 2018 at 16:28)](https://leanprover.zulipchat.com/#narrow/stream/144837-PR%20reviews/topic/%23462%20ideal%20operations/near/146965776):
Speaking of localisations: @**Kenny Lau** we couldn't find the fact that `s : S` becomes a unit in the localisation.

#### [Kevin Buzzard (Nov 07 2018 at 16:28)](https://leanprover.zulipchat.com/#narrow/stream/144837-PR%20reviews/topic/%23462%20ideal%20operations/near/146965798):
Maybe localisation was written before units

#### [Kenny Lau (Nov 07 2018 at 16:28)](https://leanprover.zulipchat.com/#narrow/stream/144837-PR%20reviews/topic/%23462%20ideal%20operations/near/146965804):
so how should I name (M:N)?

#### [Johan Commelin (Nov 07 2018 at 16:33)](https://leanprover.zulipchat.com/#narrow/stream/144837-PR%20reviews/topic/%23462%20ideal%20operations/near/146966120):
I don't have a good idea...

#### [Reid Barton (Nov 07 2018 at 16:33)](https://leanprover.zulipchat.com/#narrow/stream/144837-PR%20reviews/topic/%23462%20ideal%20operations/near/146966129):
If no one has a better idea, I suggest `colon`

#### [Reid Barton (Nov 07 2018 at 16:33)](https://leanprover.zulipchat.com/#narrow/stream/144837-PR%20reviews/topic/%23462%20ideal%20operations/near/146966140):
`M.colon N`

#### [Kenny Lau (Nov 07 2018 at 16:33)](https://leanprover.zulipchat.com/#narrow/stream/144837-PR%20reviews/topic/%23462%20ideal%20operations/near/146966142):
and what is I^n • D?

#### [Johan Commelin (Nov 07 2018 at 16:35)](https://leanprover.zulipchat.com/#narrow/stream/144837-PR%20reviews/topic/%23462%20ideal%20operations/near/146966302):
`I` is an ideal in a subring `A₀` of a ring `A`. We localise at an element `s : A` so we get `A → A_s`. Inside this, we look at `D` which is the subring generated by the image of `A₀` and some elements we don't care about.

#### [Kevin Buzzard (Nov 07 2018 at 16:35)](https://leanprover.zulipchat.com/#narrow/stream/144837-PR%20reviews/topic/%23462%20ideal%20operations/near/146966331):
```quote
@**Johan Commelin** @**Kevin Buzzard** do you have any other requests?
```
I just looked through it all and you have got everything I can think of (including comap of prime is prime).

#### [Johan Commelin (Nov 07 2018 at 16:36)](https://leanprover.zulipchat.com/#narrow/stream/144837-PR%20reviews/topic/%23462%20ideal%20operations/near/146966374):
With this information, the reader is supposed to figure out what `I^n • D` is. I would be surprised if Lean could do so as well.

#### [Kenny Lau (Nov 07 2018 at 20:43)](https://leanprover.zulipchat.com/#narrow/stream/144837-PR%20reviews/topic/%23462%20ideal%20operations/near/147249919):
oh no, (analysis) limit stuffs use ideals

#### [Kenny Lau (Nov 07 2018 at 20:43)](https://leanprover.zulipchat.com/#narrow/stream/144837-PR%20reviews/topic/%23462%20ideal%20operations/near/147249925):
so all those need to be compiled

#### [Kenny Lau (Nov 07 2018 at 23:51)](https://leanprover.zulipchat.com/#narrow/stream/144837-PR%20reviews/topic/%23462%20ideal%20operations/near/147262554):
Should we have a notation for `r • linear_map.id`?

#### [Kenny Lau (Nov 08 2018 at 00:38)](https://leanprover.zulipchat.com/#narrow/stream/144837-PR%20reviews/topic/%23462%20ideal%20operations/near/147264938):
```lean
def annihilator (N : submodule R M) : ideal R :=
(linear_map.lsmul R N).ker

def colon (N P : submodule R M) : ideal R :=
annihilator (P.map N.mkq)
```

