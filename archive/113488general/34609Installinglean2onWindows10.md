---
layout: page
title: Lean Prover Zulip Chat Archive 
permalink: archive/113488general/34609Installinglean2onWindows10.html
---

## [general](index.html)
### [Installing lean2 on Windows 10](34609Installinglean2onWindows10.html)

#### [Thomas Eckl (Aug 23 2018 at 19:24)](https://leanprover.zulipchat.com/#narrow/stream/113488-general/topic/Installing%20lean2%20on%20Windows%2010/near/132650105):
I would like to work with the HoTT library of Lean2, so I tried to install lean2 on Windows 10 machines (a laptop and a Surface Pro3) following the instructions at [https://github.com/leanprover/lean2/blob/master/doc/make/msys2.md](https://github.com/leanprover/lean2/blob/master/doc/make/msys2.md), and I failed several times at the same stage when running the ninja command. Below I copied just the last log-message of several very similar ones.  Any idea what to do?

[7/223] Building CXX object util/lp/CMakeFiles/lp.dir/lar_core_solver_instances.cpp.obj
FAILED: util/lp/CMakeFiles/lp.dir/lar_core_solver_instances.cpp.obj 
C:\msys64\mingw64\bin\g++.exe   -IC:/msys64/mingw64/include -IC:/lean2/src -I. -Wall -Wextra -std=c++11  -D LEAN_WINDOWS -D LEAN_WIN_STACK_SIZE=104857600 -D_GLIBCXX_USE_CXX11_ABI=0 -D LEAN_MULTI_THREAD -D LEAN_AUTO_THREAD_FINALIZATION -DLEAN_BUILD_TYPE="Release" -D LEAN_TRACK_MEMORY -O3 -DNDEBUG -MD -MT util/lp/CMakeFiles/lp.dir/lar_core_solver_instances.cpp.obj -MF util\lp\CMakeFiles\lp.dir\lar_core_solver_instances.cpp.obj.d -o util/lp/CMakeFiles/lp.dir/lar_core_solver_instances.cpp.obj -c C:/lean2/src/util/lp/lar_core_solver_instances.cpp
In file included from C:/lean2/src/util/lp/static_matrix.h:15,,
                 from C:/lean2/src/util/lp/lp_core_solver_base.h:14,
				 from C:/lean2/src/util/lp/lar_core_solver.h:11,
				 from C:/lean2/src/util/lp/lar_core_solver.cpp:15,
				 from C:/lean2/src/util/lp/lar_core_solver_instances.cpp:12:
C:/lean2/src/util/lp/permutation_matrix.h: 
In member function 'unsigned int* lean::permutation_matrix<T, X>::values() const':
C:/lean2/src/util/lp/permutation_matrix.h:126:44: error: cannot convert 'const std::vector<unsigned int, std::allocator<unsigned int> >' to 'unsigned int*' in return unsigned * values() const { return m_permutation; }
										  ^~~~~~~~~~~~~
ninja: build stopped: subcommand failed.

#### [Thomas Eckl (Aug 29 2018 at 23:11)](https://leanprover.zulipchat.com/#narrow/stream/113488-general/topic/Installing%20lean2%20on%20Windows%2010/near/133022349):
Digging out my c++ -knowledge (probably not a bad idea when using lean) I realized that the problem in the file permutation.h was that a pointer to m_permutation and not m_permutation itself should be returned. Since m_permutation is a vector, changing m_permutation to m_permutation.data()  in the incriminated line will do.

#### [Andrew Ashworth (Aug 30 2018 at 01:32)](https://leanprover.zulipchat.com/#narrow/stream/113488-general/topic/Installing%20lean2%20on%20Windows%2010/near/133028541):
I'm glad you were able to solve this problem. I'm afraid your topic didn't get much attention because very few people in this chat are interested in Lean 2 and HoTT. Even more so now that Lean 4 is on the horizon. You might be interested in https://github.com/gebner/hott3.

#### [Floris van Doorn (Aug 30 2018 at 10:28)](https://leanprover.zulipchat.com/#narrow/stream/113488-general/topic/Installing%20lean2%20on%20Windows%2010/near/133046441):
I'm not active on Zulip, so I didn't see this message earlier, but if you make a pull request for Lean 2 with the fix, I'm happy to merge it.

