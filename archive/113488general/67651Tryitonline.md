---
layout: page
title: Lean Prover Zulip Chat Archive 
permalink: archive/113488general/67651Tryitonline.html
---

## [general](index.html)
### [Try it online!](67651Tryitonline.html)

#### [Kenny Lau (Mar 31 2018 at 07:43)](https://leanprover.zulipchat.com/#narrow/stream/113488-general/topic/Try%20it%20online%21/near/124444027):
[Lean is now available at tio.run](https://tio.run/##y0lNzPv/PzO3IL@oRCExLzGnsjizWK8oNTGHSzk5IzU5WyEvsUQvMSUlPjk/NxcmpmGkYKUAUqT5/z8A)

#### [Kenny Lau (Mar 31 2018 at 07:44)](https://leanprover.zulipchat.com/#narrow/stream/113488-general/topic/Try%20it%20online%21/near/124444036):
It’s a website hosted by a guy named Dennis mainly for the purpose of code-golfing competitions held in codegolf.SE

#### [Kenny Lau (Mar 31 2018 at 07:44)](https://leanprover.zulipchat.com/#narrow/stream/113488-general/topic/Try%20it%20online%21/near/124444076):
of which I have been a regular for 3 years

#### [Kenny Lau (Mar 31 2018 at 07:45)](https://leanprover.zulipchat.com/#narrow/stream/113488-general/topic/Try%20it%20online%21/near/124444084):
it was added shortly after I [answered a challenge in Lean for the first time](https://codegolf.stackexchange.com/a/160919/48934)

#### [Mario Carneiro (Mar 31 2018 at 07:58)](https://leanprover.zulipchat.com/#narrow/stream/113488-general/topic/Try%20it%20online%21/near/124444387):
Re your golf:
```
def f:_->nat|(n+2):=f(n+1)+f n|x:=x
```

#### [Kenny Lau (Mar 31 2018 at 08:00)](https://leanprover.zulipchat.com/#narrow/stream/113488-general/topic/Try%20it%20online%21/near/124444436):
nice... how does that _ work?

#### [Mario Carneiro (Mar 31 2018 at 08:01)](https://leanprover.zulipchat.com/#narrow/stream/113488-general/topic/Try%20it%20online%21/near/124444445):
It figures out the type from `(n+2)`

#### [Kenny Lau (Mar 31 2018 at 08:01)](https://leanprover.zulipchat.com/#narrow/stream/113488-general/topic/Try%20it%20online%21/near/124444447):
you seriously should joins us! 😛

#### [Mario Carneiro (Mar 31 2018 at 08:01)](https://leanprover.zulipchat.com/#narrow/stream/113488-general/topic/Try%20it%20online%21/near/124444448):
I watch a lot

#### [Kenny Lau (Mar 31 2018 at 08:04)](https://leanprover.zulipchat.com/#narrow/stream/113488-general/topic/Try%20it%20online%21/near/124444535):
i could even prove its correctness at the end of my answer 😛

#### [Mario Carneiro (Mar 31 2018 at 08:06)](https://leanprover.zulipchat.com/#narrow/stream/113488-general/topic/Try%20it%20online%21/near/124444586):
Heh, my only answer on PPCG is a program that creates optimal golfs in another language

#### [Kenny Lau (Mar 31 2018 at 17:26)](https://leanprover.zulipchat.com/#narrow/stream/113488-general/topic/Try%20it%20online%21/near/124457803):
@**Kevin Buzzard**

#### [Kenny Lau (Mar 31 2018 at 17:26)](https://leanprover.zulipchat.com/#narrow/stream/113488-general/topic/Try%20it%20online%21/near/124457805):
Dennis got his thing to automatically build the latest version of mathlib once it got OK'ed by travis

#### [Chris Hughes (Mar 31 2018 at 20:52)](https://leanprover.zulipchat.com/#narrow/stream/113488-general/topic/Try%20it%20online%21/near/124462918):
Impressively fast. Is there a way to change the layout?

#### [Kenny Lau (Mar 31 2018 at 20:52)](https://leanprover.zulipchat.com/#narrow/stream/113488-general/topic/Try%20it%20online%21/near/124462920):
what kind of layout?

#### [Chris Hughes (Mar 31 2018 at 21:13)](https://leanprover.zulipchat.com/#narrow/stream/113488-general/topic/Try%20it%20online%21/near/124463425):
So it's like VScode, with goals on the right.

#### [Kenny Lau (Mar 31 2018 at 21:14)](https://leanprover.zulipchat.com/#narrow/stream/113488-general/topic/Try%20it%20online%21/near/124463465):
I'm afraid that isn't possible, since every other language on the site uses the same layout

#### [Kenny Lau (Mar 31 2018 at 21:14)](https://leanprover.zulipchat.com/#narrow/stream/113488-general/topic/Try%20it%20online%21/near/124463467):
you can still see the goals if you leave them blank, it will be displayed as an error

#### [Kenny Lau (Apr 05 2018 at 16:13)](https://leanprover.zulipchat.com/#narrow/stream/113488-general/topic/Try%20it%20online%21/near/124672274):
[Lean@TIO](https://tio.run/##y0lNzPv/PzO3IL@oRCExLzGnsjizWK8oNTGHSzk5IzU5WyEvsUQvMSUlPjk/NxcmpmGkYKUAUqT5/z8A) has updated to mathlib ` 22e671 ` on lean ` 96c932a `

#### [Kenny Lau (Apr 24 2018 at 05:16)](https://leanprover.zulipchat.com/#narrow/stream/113488-general/topic/Try%20it%20online%21/near/125600886):
https://codegolf.stackexchange.com/a/163239/48934

#### [Andrew Ashworth (Apr 24 2018 at 06:38)](https://leanprover.zulipchat.com/#narrow/stream/113488-general/topic/Try%20it%20online%21/near/125603271):
I see the top answer is very awesome, `ṗṬML`. Dear god what am I reading

#### [Kevin Buzzard (Apr 24 2018 at 10:58)](https://leanprover.zulipchat.com/#narrow/stream/113488-general/topic/Try%20it%20online%21/near/125611300):
I quit Lean. I'm moving over to Jelly.

#### [Kevin Buzzard (Apr 24 2018 at 10:58)](https://leanprover.zulipchat.com/#narrow/stream/113488-general/topic/Try%20it%20online%21/near/125611305):
[that's what we call Jello in the UK]

#### [Sean Leather (Apr 24 2018 at 11:45)](https://leanprover.zulipchat.com/#narrow/stream/113488-general/topic/Try%20it%20online%21/near/125613031):
@**Kenny Lau** Why not `ℕ` instead of `nat`?

#### [Kenny Lau (Apr 24 2018 at 11:45)](https://leanprover.zulipchat.com/#narrow/stream/113488-general/topic/Try%20it%20online%21/near/125613033):
not sure how many bytes the former is

#### [Sean Leather (Apr 24 2018 at 11:46)](https://leanprover.zulipchat.com/#narrow/stream/113488-general/topic/Try%20it%20online%21/near/125613089):
Hmm, 3 bytes according to https://mothereff.in/byte-counter .

#### [Kenny Lau (Apr 24 2018 at 11:46)](https://leanprover.zulipchat.com/#narrow/stream/113488-general/topic/Try%20it%20online%21/near/125613094):
then it saves no bytes :P

#### [Sean Leather (Apr 24 2018 at 11:46)](https://leanprover.zulipchat.com/#narrow/stream/113488-general/topic/Try%20it%20online%21/near/125613097):
Indeed.

#### [Kenny Lau (Nov 16 2018 at 22:14)](https://leanprover.zulipchat.com/#narrow/stream/113488-general/topic/Try%20it%20online%21/near/147846641):
https://codegolf.stackexchange.com/a/176122/48934

#### [Scott Morrison (Nov 16 2018 at 22:48)](https://leanprover.zulipchat.com/#narrow/stream/113488-general/topic/Try%20it%20online%21/near/147848525):
Quick, a PR!

#### [Chris Hughes (Nov 16 2018 at 23:03)](https://leanprover.zulipchat.com/#narrow/stream/113488-general/topic/Try%20it%20online%21/near/147849345):
you could `import data.rat` and save one character

#### [Chris Hughes (Nov 16 2018 at 23:04)](https://leanprover.zulipchat.com/#narrow/stream/113488-general/topic/Try%20it%20online%21/near/147849432):
I would have commented on stackexchange but I needed 50 reputation.

#### [Kevin Buzzard (Nov 16 2018 at 23:04)](https://leanprover.zulipchat.com/#narrow/stream/113488-general/topic/Try%20it%20online%21/near/147849439):
Are you allowed to use "the standard library"?

#### [Mario Carneiro (Nov 16 2018 at 23:07)](https://leanprover.zulipchat.com/#narrow/stream/113488-general/topic/Try%20it%20online%21/near/147849595):
yes, as long as you don't update the standard library after the challenge

#### [Mario Carneiro (Nov 16 2018 at 23:08)](https://leanprover.zulipchat.com/#narrow/stream/113488-general/topic/Try%20it%20online%21/near/147849650):
you will notice the mathematica answer is a cheeky `DirichletConvolve`

#### [Mario Carneiro (Nov 16 2018 at 23:09)](https://leanprover.zulipchat.com/#narrow/stream/113488-general/topic/Try%20it%20online%21/near/147849669):
(so in particular scott's strategy is disallowed by the rules)

#### [Mario Carneiro (Nov 16 2018 at 23:11)](https://leanprover.zulipchat.com/#narrow/stream/113488-general/topic/Try%20it%20online%21/near/147849792):
wait, kenny's last post on this thread is a codegolf for the number of surjections, plus a proof of correctness. Why doesn't mathlib have that?

#### [Kenny Lau (Nov 16 2018 at 23:12)](https://leanprover.zulipchat.com/#narrow/stream/113488-general/topic/Try%20it%20online%21/near/147849855):
does it?

#### [Mario Carneiro (Nov 16 2018 at 23:13)](https://leanprover.zulipchat.com/#narrow/stream/113488-general/topic/Try%20it%20online%21/near/147849864):
https://codegolf.stackexchange.com/a/163239/11143

#### [Kenny Lau (Nov 16 2018 at 23:14)](https://leanprover.zulipchat.com/#narrow/stream/113488-general/topic/Try%20it%20online%21/near/147849969):
I mean, does mathlib have that?

#### [Kevin Buzzard (Nov 16 2018 at 23:15)](https://leanprover.zulipchat.com/#narrow/stream/113488-general/topic/Try%20it%20online%21/near/147850001):
We could just start working on getting all of OEIS in, right?

#### [Mario Carneiro (Nov 16 2018 at 23:34)](https://leanprover.zulipchat.com/#narrow/stream/113488-general/topic/Try%20it%20online%21/near/147850991):
it doesn't, that's my point

#### [Mario Carneiro (Nov 16 2018 at 23:35)](https://leanprover.zulipchat.com/#narrow/stream/113488-general/topic/Try%20it%20online%21/near/147851047):
I don't see any reason we shouldn't have the stirling numbers defined, especially if you have a nice thing to prove about them

#### [Mario Carneiro (Nov 16 2018 at 23:36)](https://leanprover.zulipchat.com/#narrow/stream/113488-general/topic/Try%20it%20online%21/near/147851151):
I'm not saying we should all go out and formalize OEIS, but if someone has already gone to the trouble of formalizing some of it, I'd like to get in on that

