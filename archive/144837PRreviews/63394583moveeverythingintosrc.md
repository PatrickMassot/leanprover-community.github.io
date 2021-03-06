---
layout: page
title: Lean Prover Zulip Chat Archive 
permalink: archive/144837PRreviews/63394583moveeverythingintosrc.html
---

## [PR reviews](index.html)
### [#583 move everything into `src`](63394583moveeverythingintosrc.html)

#### [Patrick Massot (Jan 15 2019 at 09:15)](https://leanprover.zulipchat.com/#narrow/stream/144837-PR%20reviews/topic/%23583%20move%20everything%20into%20%60src%60/near/155153163):
What is the status of this PR? I think we should bite the bullet and make it happen. I'm waiting for it before implementing the topology part of https://github.com/leanprover/mathlib/issues/586 I'm willing to update the PR, but then it needs to be merged right away, otherwise it will have conflict at every single future commit

#### [Patrick Massot (Jan 15 2019 at 09:15)](https://leanprover.zulipchat.com/#narrow/stream/144837-PR%20reviews/topic/%23583%20move%20everything%20into%20%60src%60/near/155153170):
@**Johannes Hölzl**

#### [Reid Barton (Jan 15 2019 at 09:41)](https://leanprover.zulipchat.com/#narrow/stream/144837-PR%20reviews/topic/%23583%20move%20everything%20into%20%60src%60/near/155154177):
I agree we should do this now, and then follow up with the reorganization at the level of whole files, which we now have an outline for and should be straightforward. I don't think we need to wait for the details of how to reorganize individual files like `topological_space.lean`.

#### [Kevin Buzzard (Jan 15 2019 at 09:42)](https://leanprover.zulipchat.com/#narrow/stream/144837-PR%20reviews/topic/%23583%20move%20everything%20into%20%60src%60/near/155154237):
I vote for pain today as opposed to more pain tomorrow.

#### [Reid Barton (Jan 15 2019 at 13:37)](https://leanprover.zulipchat.com/#narrow/stream/144837-PR%20reviews/topic/%23583%20move%20everything%20into%20%60src%60/near/155165674):
@**Mario Carneiro**

#### [Mario Carneiro (Jan 15 2019 at 13:38)](https://leanprover.zulipchat.com/#narrow/stream/144837-PR%20reviews/topic/%23583%20move%20everything%20into%20%60src%60/near/155165734):
ok, it has to be redone though of course

#### [Patrick Massot (Jan 15 2019 at 15:31)](https://leanprover.zulipchat.com/#narrow/stream/144837-PR%20reviews/topic/%23583%20move%20everything%20into%20%60src%60/near/155172935):
@**Mario Carneiro** what do you mean here? Do you mean: if someone redoes it then I'll merge right away?

#### [Mario Carneiro (Jan 15 2019 at 15:31)](https://leanprover.zulipchat.com/#narrow/stream/144837-PR%20reviews/topic/%23583%20move%20everything%20into%20%60src%60/near/155172952):
yes

#### [Mario Carneiro (Jan 15 2019 at 15:33)](https://leanprover.zulipchat.com/#narrow/stream/144837-PR%20reviews/topic/%23583%20move%20everything%20into%20%60src%60/near/155173107):
are we ready for the reorganization though? I guess both should be done around the same time

#### [Patrick Massot (Jan 15 2019 at 15:36)](https://leanprover.zulipchat.com/#narrow/stream/144837-PR%20reviews/topic/%23583%20move%20everything%20into%20%60src%60/near/155173342):
Ok, it's rebased

#### [Patrick Massot (Jan 15 2019 at 15:37)](https://leanprover.zulipchat.com/#narrow/stream/144837-PR%20reviews/topic/%23583%20move%20everything%20into%20%60src%60/near/155173376):
I'm ready to move analysis files around. I don't know about the stuff in `basic`

#### [Mario Carneiro (Jan 15 2019 at 15:41)](https://leanprover.zulipchat.com/#narrow/stream/144837-PR%20reviews/topic/%23583%20move%20everything%20into%20%60src%60/near/155173697):
ok, so the first reorg PR can be moving files around with no splitting, and we can split files in later PRs

#### [Patrick Massot (Jan 15 2019 at 15:42)](https://leanprover.zulipchat.com/#narrow/stream/144837-PR%20reviews/topic/%23583%20move%20everything%20into%20%60src%60/near/155173773):
Yes, that's the plan

#### [Mario Carneiro (Jan 15 2019 at 16:52)](https://leanprover.zulipchat.com/#narrow/stream/144837-PR%20reviews/topic/%23583%20move%20everything%20into%20%60src%60/near/155180006):
@**Patrick Massot** I merged, but it looks a bit incomplete. Could you follow up moving the rest of the files?

#### [Patrick Massot (Jan 15 2019 at 16:52)](https://leanprover.zulipchat.com/#narrow/stream/144837-PR%20reviews/topic/%23583%20move%20everything%20into%20%60src%60/near/155180043):
So weird... I guess I trusted Simon too much

#### [Mario Carneiro (Jan 15 2019 at 16:53)](https://leanprover.zulipchat.com/#narrow/stream/144837-PR%20reviews/topic/%23583%20move%20everything%20into%20%60src%60/near/155180095):
you should redone it instead of rebase, I think

#### [Mario Carneiro (Jan 15 2019 at 16:53)](https://leanprover.zulipchat.com/#narrow/stream/144837-PR%20reviews/topic/%23583%20move%20everything%20into%20%60src%60/near/155180119):
the files that were left behind are new since simon's version

#### [Patrick Massot (Jan 15 2019 at 16:54)](https://leanprover.zulipchat.com/#narrow/stream/144837-PR%20reviews/topic/%23583%20move%20everything%20into%20%60src%60/near/155180172):
Ok, it's probably my fault then

#### [Patrick Massot (Jan 15 2019 at 16:58)](https://leanprover.zulipchat.com/#narrow/stream/144837-PR%20reviews/topic/%23583%20move%20everything%20into%20%60src%60/near/155180604):
https://github.com/leanprover/mathlib/pull/597

#### [Patrick Massot (Jan 15 2019 at 16:59)](https://leanprover.zulipchat.com/#narrow/stream/144837-PR%20reviews/topic/%23583%20move%20everything%20into%20%60src%60/near/155180612):
sorry about the inconvenience

#### [Johan Commelin (Jan 16 2019 at 18:55)](https://leanprover.zulipchat.com/#narrow/stream/144837-PR%20reviews/topic/%23583%20move%20everything%20into%20%60src%60/near/155273357):
I'm a git noob. I just did `git pull upstream master` to get the latest version from https://github.com/leanprover/mathlib
So now I have a directory `src/` with all of mathlib in it. But all the old directories are also still there. So everything is duplicated. Is it easy to fix this? (Otherwise I'll just reclone.)

#### [Johannes Hölzl (Jan 16 2019 at 18:57)](https://leanprover.zulipchat.com/#narrow/stream/144837-PR%20reviews/topic/%23583%20move%20everything%20into%20%60src%60/near/155273485):
the old directories are not deleted, usually there are still the `olean` files in them. One option is to clean your repository using `git clean -xfd`, but be careful to not have any uncommited stuff in your repo

#### [Johan Commelin (Jan 16 2019 at 18:59)](https://leanprover.zulipchat.com/#narrow/stream/144837-PR%20reviews/topic/%23583%20move%20everything%20into%20%60src%60/near/155273603):
Ok, now the old directories are empty, but they are still there...

#### [Johannes Hölzl (Jan 16 2019 at 19:07)](https://leanprover.zulipchat.com/#narrow/stream/144837-PR%20reviews/topic/%23583%20move%20everything%20into%20%60src%60/near/155274121):
hm the `-d` should have removed them

#### [Johan Commelin (Jan 16 2019 at 19:29)](https://leanprover.zulipchat.com/#narrow/stream/144837-PR%20reviews/topic/%23583%20move%20everything%20into%20%60src%60/near/155275903):
Aah, `git clean -fd` worked

