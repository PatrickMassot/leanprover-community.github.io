---
layout: page
title: Lean Prover Zulip Chat Archive 
permalink: archive/116395maths/66414groupactingongroup.html
---

## [maths](index.html)
### [group acting on group](66414groupactingongroup.html)

#### [Kenny Lau (Apr 09 2018 at 15:05)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/group%20acting%20on%20group/near/124835829):
Do we have a name for a group acting on another group that is compatible with the group structure?

#### [jmc (Apr 09 2018 at 15:19)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/group%20acting%20on%20group/near/124836222):
There is this thing called G-module

#### [jmc (Apr 09 2018 at 15:19)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/group%20acting%20on%20group/near/124836230):
But then you act on abelian groups

#### [Kenny Lau (Apr 09 2018 at 15:19)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/group%20acting%20on%20group/near/124836231):
but a group is not a module

#### [Kenny Lau (Apr 09 2018 at 15:19)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/group%20acting%20on%20group/near/124836232):
right

#### [jmc (Apr 09 2018 at 15:21)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/group%20acting%20on%20group/near/124836300):
Where does this show up?

#### [Kenny Lau (Apr 09 2018 at 15:21)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/group%20acting%20on%20group/near/124836303):
in my brain

#### [Kenny Lau (Apr 09 2018 at 15:21)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/group%20acting%20on%20group/near/124836304):
i'm just making this up

#### [Kenny Lau (Apr 09 2018 at 15:22)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/group%20acting%20on%20group/near/124836308):
oh wait, this does show up in group theory

#### [Kenny Lau (Apr 09 2018 at 15:22)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/group%20acting%20on%20group/near/124836348):
a group acts on a normal subgroup by conjugation

#### [jmc (Apr 09 2018 at 15:22)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/group%20acting%20on%20group/near/124836349):
Ok, G-modules show up a lot in group cohomology

#### [jmc (Apr 09 2018 at 15:22)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/group%20acting%20on%20group/near/124836351):
Aah, ok, sure

#### [Kenny Lau (Apr 09 2018 at 15:22)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/group%20acting%20on%20group/near/124836352):
right, i'm learning group cohomology right now

#### [Kenny Lau (Apr 09 2018 at 15:22)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/group%20acting%20on%20group/near/124836355):
and then an action of G on N is just a homomorphism G -> Aut(N)

#### [jmc (Apr 09 2018 at 15:23)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/group%20acting%20on%20group/near/124836366):
Sure, but if G acts on G', it is also just a homom G -> Aut(G')

#### [jmc (Apr 09 2018 at 15:23)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/group%20acting%20on%20group/near/124836370):
if the action is compatible with the group structure

#### [Kevin Buzzard (Apr 09 2018 at 15:27)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/group%20acting%20on%20group/near/124836498):
If the group M you're acting on is abelian, then this is just called a G-module usually (G the group doing the acting)

#### [Kevin Buzzard (Apr 09 2018 at 15:28)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/group%20acting%20on%20group/near/124836539):
If M is not abelian then this is sometimes called a "non-abelian G-module" and the theory very quickly gets technical

#### [Kevin Buzzard (Apr 09 2018 at 15:28)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/group%20acting%20on%20group/near/124836549):
H^1 is no longer a group, but just a pointed set

#### [Kevin Buzzard (Apr 09 2018 at 15:28)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/group%20acting%20on%20group/near/124836557):
and for higher cohomology groups one has to use fancy stuff like gerbes

#### [Kevin Buzzard (Apr 09 2018 at 15:29)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/group%20acting%20on%20group/near/124836577):
See Serre's book on Galois cohomology (some appendix) for a brief and clear introduction.

