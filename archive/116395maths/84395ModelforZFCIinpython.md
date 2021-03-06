---
layout: page
title: Lean Prover Zulip Chat Archive 
permalink: archive/116395maths/84395ModelforZFCIinpython.html
---

## [maths](index.html)
### [Model for ZFC-I in python](84395ModelforZFCIinpython.html)

#### [Kenny Lau (Jun 08 2018 at 21:23)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/Model%20for%20ZFC-I%20in%20python/near/127788909):
I built a quite straightforward model for ZFC *sans* infinity in python: [here](https://tio.run/##dVNNb6MwED3Hv2KaartYYdOQrLorVA75A3tJb1UUucE0XsEYGdOmavvbs2OTAGHTC4w9H@/5zUz5ZncaF4fM6AKyGrdW67wCVZTaWDAyrbeSHU@6lEZYbQ7XYHcStjqVoDNvy1wWEm3lzgIqaVkqs/Y2QB6zkcIUEpixkZEVGRQUcDZ63alcApJ/pDLAmygm1Goq0jSgBO6uKW@SQEQmwu1tAnNXwtYGXSRj1/QrySIkYZXGjoO7J6RcFE@pgFUM4/fxZByOp3@1wsB5iRlk2gCCwo7uivPJ@HPsSou9ImGootxbiRWVF7myb6AqEAiiqqRxmGehpVBG4TNz/x58@BBDEN3frzh8eOOBn6XV6Ar5b5e1jI9NCE7qTzcbbTabsGW75OHsvFKpX6VxApyMMxH@r1fUORV8JEqOFjp@0UVZ1mF0jmTkc50L4xR5RG0lxEdNgtVVMuNr1gvocyCYglrQV3xQt8zF1jtZz@6rmX2pjHtI9lVn10OxtjuttnJIf/ltnvgHHN39hrxjDGfskV/CWvJPB1TRKOTSUmtbayjFysW9aPzxR9aFQKqBtFwUfVovFDTuIq/8Vr1gs0/NGtE@OeiNgzYCn2Xj9N6PxFV3SzJYmEIWTzQYO1UyMjs6@5AI7QeKuQS/40VJXXTTFJS5FJWEVON3SwI6WFCWsyaESB1aORpOdzwuaSdsgKFfO/8G6vlRbTpGHJKkEyvwpS5EnEZ6GOD3Jpg3QXftdRt@9CwWP@eL379afzefPuIG5hFcJc1bOWs4NyMQRLNZB0ey9e8fcR1eHDifdPgH)

#### [Kenny Lau (Jun 08 2018 at 21:23)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/Model%20for%20ZFC-I%20in%20python/near/127788914):
it's called the hereditarily finite sets

#### [Mario Carneiro (Jun 09 2018 at 00:35)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/Model%20for%20ZFC-I%20in%20python/near/127796997):
Why in Python? This could be done in lean computably

#### [Kenny Lau (Jun 09 2018 at 00:36)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/Model%20for%20ZFC-I%20in%20python/near/127797041):
sure

#### [Mario Carneiro (Jun 09 2018 at 00:36)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/Model%20for%20ZFC-I%20in%20python/near/127797046):
I don't even know what "construct a model in Python" means

#### [Mario Carneiro (Jun 09 2018 at 00:37)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/Model%20for%20ZFC-I%20in%20python/near/127797049):
since it doesn't have a proof theory

#### [Kenny Lau (Jun 09 2018 at 00:37)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/Model%20for%20ZFC-I%20in%20python/near/127797056):
well, the natural numbers is the model, I just provided the relevant functions

#### [Mario Carneiro (Jun 09 2018 at 00:37)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/Model%20for%20ZFC-I%20in%20python/near/127797064):
what is the encoding?

#### [Mario Carneiro (Jun 09 2018 at 00:39)](https://leanprover.zulipchat.com/#narrow/stream/116395-maths/topic/Model%20for%20ZFC-I%20in%20python/near/127797124):
actually, there is an instance of `denumerable (finset N)` that you could use for the elementhood predicate in lean

