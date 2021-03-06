---
layout: page
title: Lean Prover Zulip Chat Archive 
permalink: archive/113488general/28762failedtostartchildprocess.html
---

## [general](index.html)
### [failed to start child process](28762failedtostartchildprocess.html)

#### [Scott Morrison (Jul 25 2018 at 08:07)](https://leanprover.zulipchat.com/#narrow/stream/113488-general/topic/failed%20to%20start%20child%20process/near/130257139):
I have a student who can't run leanpkg on Windows: `leanpkg.bat new test` says: "failed to start child process", and doesn't create a new directory.

#### [Scott Morrison (Jul 25 2018 at 08:07)](https://leanprover.zulipchat.com/#narrow/stream/113488-general/topic/failed%20to%20start%20child%20process/near/130257148):
Has anyone experienced this, and knows the fix?

#### [Scott Morrison (Jul 25 2018 at 08:07)](https://leanprover.zulipchat.com/#narrow/stream/113488-general/topic/failed%20to%20start%20child%20process/near/130257151):
I know nothing about Windows anymore.

#### [Johan Commelin (Jul 25 2018 at 08:27)](https://leanprover.zulipchat.com/#narrow/stream/113488-general/topic/failed%20to%20start%20child%20process/near/130257829):
```quote
Has anyone experienced this, and knows the fix?
```
The fix would obviously be to wipe Windows and install a proper OS.

#### [Minchao Wu (Jul 25 2018 at 09:53)](https://leanprover.zulipchat.com/#narrow/stream/113488-general/topic/failed%20to%20start%20child%20process/near/130260741):
@**Scott Morrison** one of my colleagues has experienced this. The simplest solution would be using Git Bash if Git is installed.

#### [Kevin Buzzard (Jul 25 2018 at 11:09)](https://leanprover.zulipchat.com/#narrow/stream/113488-general/topic/failed%20to%20start%20child%20process/near/130263893):
I've had several problems with git on Windows. There appears to be more than one canonical installation of git.

#### [Chris Hughes (Jul 25 2018 at 11:45)](https://leanprover.zulipchat.com/#narrow/stream/113488-general/topic/failed%20to%20start%20child%20process/near/130265519):
I always get that error if I use the windows command line instead of Msys.

#### [Kevin Buzzard (Jul 25 2018 at 11:52)](https://leanprover.zulipchat.com/#narrow/stream/113488-general/topic/failed%20to%20start%20child%20process/near/130265849):
The mantra I tell Windows users is msys2, git, lean binary, set msys2 path variable so it can see git and leanpkg, then follow instructions in reference manual

#### [Kevin Buzzard (Jul 25 2018 at 11:53)](https://leanprover.zulipchat.com/#narrow/stream/113488-general/topic/failed%20to%20start%20child%20process/near/130265881):
Oh -- and don't put lean in a directory whose full name has a space in

#### [Scott Morrison (Jul 25 2018 at 12:13)](https://leanprover.zulipchat.com/#narrow/stream/113488-general/topic/failed%20to%20start%20child%20process/near/130266683):
We found yet another solution: activate the "Linux Subsystem for Windows", install the "Ubuntu" app, and use `elan` there. It was incredibly painless and fast (15 minutes?)

#### [Mario Carneiro (Jul 25 2018 at 12:22)](https://leanprover.zulipchat.com/#narrow/stream/113488-general/topic/failed%20to%20start%20child%20process/near/130267031):
really? I've never had much success with WSL

#### [Olli (Sep 12 2018 at 18:53)](https://leanprover.zulipchat.com/#narrow/stream/113488-general/topic/failed%20to%20start%20child%20process/near/133811905):
Any ideas what the "failed to start child process" might be due to? I am on Windows 10 and I get it when trying to use `leanpkg` for basically anything. I see that it originates in the C++ code base of Lean itself.

I saw some mentions of this issue in the mailing list, where it was mentioned that it occasionally happens, but for me I'm unable to do almost anything with `leanpkg`, which means I can't use `mathlib` as far as I can tell.

I might give using WSL a try, although I'm afraid that configuring VSCode might become a pain in that case.

#### [Olli (Sep 12 2018 at 18:57)](https://leanprover.zulipchat.com/#narrow/stream/113488-general/topic/failed%20to%20start%20child%20process/near/133812101):
I suppose another thing I could try is compiling Lean from source and hoping that that fixes the issue.

