---
layout: page
title: Lean Prover Zulip Chat Archive 
permalink: archive/113488general/45872fsplitwithname.html
---

## [general](index.html)
### [fsplit with name](45872fsplitwithname.html)

#### [Reid Barton (Nov 27 2018 at 16:29)](https://leanprover.zulipchat.com/#narrow/stream/113488-general/topic/fsplit%20with%20name/near/148645058):
I want to construct an `Exists` value where both parts are Props in tactic mode. Is there a convenient way to use something like `fsplit` to produce two subgoals but also to have the result of the first subgoal available as a hypothesis in the second subgoal?

#### [Reid Barton (Nov 27 2018 at 16:31)](https://leanprover.zulipchat.com/#narrow/stream/113488-general/topic/fsplit%20with%20name/near/148645203):
Currently I have `have : P, { ... }, refine <this, _>, ...` but it's a little clunky and it means I have to write out `P`

#### [Reid Barton (Nov 27 2018 at 16:46)](https://leanprover.zulipchat.com/#narrow/stream/113488-general/topic/fsplit%20with%20name/near/148646115):
actually I turned out not to need `this`, but I'm still curious

