---
layout: default
title: Yoneda 引理 (Yoneda Lemma)
---

Yoneda 引理 (Yoneda Lemma)
===

当我们思考一些数学对象时，比如群 (groups)、序 (orders) 或范畴 (categories)，我们经常感到有必要回到它们的本源。我们开始问自己，什么是“群性”或“序性”？就像是，给定一些（或任意）对象集，如何构造出这些对象的最终群——一个包含所有其他群的群？所有其他群只是它的特殊情况。或者说，什么是最终的序？最终的范畴？

同态函子 (Homomorphism Functors)
---

给定任意范畴，我们可以生成一个集合，它包含了所有相对于某个给定对象具有特定类型签名的态射集 (set of morphisms)。这称为*同态集* (Homomorphism set)，记为 $Hom(B, - )$，其中 $B$ 是你选取的对象（例如，我们选取棕色的球）。

![同态集](hom_set.svg)

这个集构成一个范畴，在其中，态射集是对象（再次强调，态射集是*对象*），而态射与原始范畴中的相同。在这两个范畴之间（原始范畴和基于态射的奇特范畴）存在一个函子，称为同态函子 (homomorphism functor)。

![同态函子](hom_functor.svg)

**问题：** 我们应该选取哪个对象，使得原始范畴和同态范畴同构？

通过同态函子，我们可以在集合范畴 (category of sets) 中*表示*任何范畴。这就是为什么同态函子和与之同构的所有函子称为*可表函子* (representable functors)。

