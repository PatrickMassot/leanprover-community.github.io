---
layout: page
title: Lean Prover Zulip Chat Archive 
permalink: archive/113488general/09099leanpkgupgrade.html
---

## [general](index.html)
### [leanpkg upgrade](09099leanpkgupgrade.html)

#### [Patrick Massot (Sep 13 2018 at 21:04)](https://leanprover.zulipchat.com/#narrow/stream/113488-general/topic/leanpkg%20upgrade/near/133906249):
It seems `leanpkg upgrade` doesn't want to upgrade mathlib past 120635628368ec261e031cefc6d30e0304088b03 Is someone else seeing this?

#### [Kevin Buzzard (Sep 13 2018 at 21:04)](https://leanprover.zulipchat.com/#narrow/stream/113488-general/topic/leanpkg%20upgrade/near/133906305):
Is your Lean 3.4.1?

#### [Patrick Massot (Sep 13 2018 at 21:04)](https://leanprover.zulipchat.com/#narrow/stream/113488-general/topic/leanpkg%20upgrade/near/133906317):
yes

#### [Kevin Buzzard (Sep 13 2018 at 21:04)](https://leanprover.zulipchat.com/#narrow/stream/113488-general/topic/leanpkg%20upgrade/near/133906323):
then I think it upgrades to mathlib branch 3.4.1

#### [Patrick Massot (Sep 13 2018 at 21:05)](https://leanprover.zulipchat.com/#narrow/stream/113488-general/topic/leanpkg%20upgrade/near/133906338):
no

#### [Patrick Massot (Sep 13 2018 at 21:05)](https://leanprover.zulipchat.com/#narrow/stream/113488-general/topic/leanpkg%20upgrade/near/133906339):
things would be much worse then

#### [Reid Barton (Sep 13 2018 at 21:05)](https://leanprover.zulipchat.com/#narrow/stream/113488-general/topic/leanpkg%20upgrade/near/133906352):
maybe your upstream is leanprover-community, that one is still at the commit you mention

#### [Patrick Massot (Sep 13 2018 at 21:06)](https://leanprover.zulipchat.com/#narrow/stream/113488-general/topic/leanpkg%20upgrade/near/133906406):
Indeed

#### [Patrick Massot (Sep 13 2018 at 21:06)](https://leanprover.zulipchat.com/#narrow/stream/113488-general/topic/leanpkg%20upgrade/near/133906412):
That's silly

#### [Patrick Massot (Sep 13 2018 at 21:06)](https://leanprover.zulipchat.com/#narrow/stream/113488-general/topic/leanpkg%20upgrade/near/133906421):
Someone messed up

#### [Patrick Massot (Sep 13 2018 at 21:07)](https://leanprover.zulipchat.com/#narrow/stream/113488-general/topic/leanpkg%20upgrade/near/133906467):
I took the opportunity to update community mathlib

