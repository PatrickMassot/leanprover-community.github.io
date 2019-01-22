---
layout: page
title: Lean Prover Zulip Chat Archive 
permalink: archive/113488general/68184sortingalgorithmsinlean.html
---

## [general](index.html)
### [sorting algorithms in lean](68184sortingalgorithmsinlean.html)

#### [Adam Kurkiewicz (Mar 30 2018 at 14:50)](https://leanprover.zulipchat.com/#narrow/stream/113488-general/topic/sorting%20algorithms%20in%20lean/near/124411849):
Hi guys,

A colleague at work (I'm working part-time in a tech company, Skyscanner) asked about dependent types & formal methods. After a bit of a chat he wanted to see an example implementation of some real-world algorithm with correctness guarantees, something like a selection sort would be great, but I would take anything "real enough but not too hard", e.g. binary search.

I've had a look at "programming in lean", but that's all I got:


> This chapter will have to assume some familiarity with Lean as a proof assistant. Give some natural examples, for example, proving properties of functions of lists, sorting routines, properties of the extended gcd. Discuss two styles: separating functions and properties, and combining them, using subtypes.

#### [Johannes Hölzl (Mar 30 2018 at 15:00)](https://leanprover.zulipchat.com/#narrow/stream/113488-general/topic/sorting%20algorithms%20in%20lean/near/124412107):
There are the sort functions in mathlib: https://github.com/leanprover/mathlib/blob/master/data/list/sort.lean
Is this what you are looking for?

#### [Adam Kurkiewicz (Mar 30 2018 at 15:31)](https://leanprover.zulipchat.com/#narrow/stream/113488-general/topic/sorting%20algorithms%20in%20lean/near/124413001):
Thanks, this looks useful. It's perhaps a little bit too general (for the purpose of exposition I'd probably want to restrict myself to lists of nats and natural order of nats), and some of the methods are a little bit advanced (tactics, etc.), so I might want to change things a little bit.

There's one thing I seem to be missing, this doesn't show that the sorted list contains the same elements? Or does it?:

```
theorem sorted_insertion_sort : ∀ l, sorted r (insertion_sort l)
| [] := sorted_nil
| (a :: l) := sorted_ordered_insert totr transr a _ (sorted_insertion_sort l)
```

#### [Adam Kurkiewicz (Mar 30 2018 at 15:36)](https://leanprover.zulipchat.com/#narrow/stream/113488-general/topic/sorting%20algorithms%20in%20lean/near/124413164):
Also, could we not have this directly in the type signature of insertion_sort? Something like
"insertion sort is a function which takes a list and returns another list, which is both sorted and has the same elements as the original list"

> l : list -> q : list \and sorted q \and same_elements_list l q

Put it this way, as a programmer I'd probably never care about these proofs, but maybe it would be nice to see them in the type signature?

#### [Adam Kurkiewicz (Mar 30 2018 at 15:41)](https://leanprover.zulipchat.com/#narrow/stream/113488-general/topic/sorting%20algorithms%20in%20lean/near/124413278):
Or maybe put it differently: let's say that I'd like to encode all the intended behaviour in the type signature and let a code monkey code the whole thing up, but for me to still have a guarantee that the monkey could never screw anything up (correctness-wise).

#### [Andrew Ashworth (Mar 30 2018 at 17:07)](https://leanprover.zulipchat.com/#narrow/stream/113488-general/topic/sorting%20algorithms%20in%20lean/near/124416003):
I don't follow, why would you want that in the type signature of insertion sort when you could prove those properties in separate lemmas. If you put it in the type signature it makes using `insertion_sort` cumbersome

#### [Andrew Ashworth (Mar 30 2018 at 17:08)](https://leanprover.zulipchat.com/#narrow/stream/113488-general/topic/sorting%20algorithms%20in%20lean/near/124416056):
as in if it was in the type signature whenever i call `insertion_sort` i have to remember it returns a tuple, and i only care about the first element (i.e. the sorted list it returns, if it had the type signature you propose)

#### [Mario Carneiro (Mar 30 2018 at 18:40)](https://leanprover.zulipchat.com/#narrow/stream/113488-general/topic/sorting%20algorithms%20in%20lean/near/124419195):
There is a second lemma that I think you missed: `perm_insertion_sort` says that the resulting list is a permutation of the original, meaning it has the same elements in the same multiplicity.

#### [Ching-Tsun Chou (Mar 30 2018 at 18:52)](https://leanprover.zulipchat.com/#narrow/stream/113488-general/topic/sorting%20algorithms%20in%20lean/near/124419610):
The whole volume 3 of Software Foundations is now devoted to such things: https://softwarefoundations.cis.upenn.edu/vfa-current/toc.html

#### [Mario Carneiro (Mar 30 2018 at 18:52)](https://leanprover.zulipchat.com/#narrow/stream/113488-general/topic/sorting%20algorithms%20in%20lean/near/124419619):
As Andrew says, it is possible to encode the proofs in the type. Here are some reasons this is less good:
* You have to prove the facts at the same time as constructing the function. Sometimes this is easy, sometimes you need a different kind of recursion for the proof.
* The set of properties your definition satisfies is open ended. Unlike other programming languages, the facts of a program are not limited to the things listed in the type.
* When writing a program for execution the primary focus is on clarity and speed or algorithmic complexity. Having proofs mixed up with that makes the program logic harder to follow, since you have to know the compiler well enough to know what to ignore and what is optimized away.

#### [Adam Kurkiewicz (Mar 30 2018 at 19:35)](https://leanprover.zulipchat.com/#narrow/stream/113488-general/topic/sorting%20algorithms%20in%20lean/near/124421218):
Fair enough guys, I find Mario's and Andrew's points entirely convincing, and of course I missed the lemma! I'll most likely still try to write a less generic implementation of one of those sorting algorithms. Good practice and hopefully something I'll be able to explain to my colleague.

#### [Mario Carneiro (Mar 30 2018 at 19:52)](https://leanprover.zulipchat.com/#narrow/stream/113488-general/topic/sorting%20algorithms%20in%20lean/near/124421994):
Another possibility for simpler verified programs is the functions in `list.basic`. There are lots of interesting examples of simple list functions and proofs that they have the expected properties. For example, `list.filter` has a two-line definition, and its proof of correctness is `list.mem_filter` (among others; that doesn't uniquely define the function).
