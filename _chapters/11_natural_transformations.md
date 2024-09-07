---
layout: default
title: 自然变换 (Natural Transformations)
---

自然变换 (Natural Transformations)
===

> 我发明范畴不是为了研究函子，而是为了研究自然变换。—— 桑德斯·麦克兰 (Saunders Mac Lane)

在本章中，我们将介绍函子 (functors) 之间的态射 (morphisms) 概念，或者说 *自然变换 (natural transformations)*。理解自然变换将使我们能够定义范畴的等价性以及其他一些高级概念。

自然变换实际上是范畴论的核心——事实上，范畴论是为了研究自然变换而发明的。然而，自然变换的重要性一开始并不明显，因此在介绍它们之前，我喜欢谈谈这一核心所维持的知识体系（我在比喻方面还是不错的……原则上如此）。

范畴的方法论——对象被高估了 (The Categorical Way AKA Objects Are Overrated)
===

> 世界是事实的集合，而不是事物的集合。——路德维希·维特根斯坦 (Ludwig Wittgenstein)

大约2500年前，哲学家巴门尼德 (Parmenides) 提出宇宙的本质是永恒不变的，而我们看到的变化只是表象。虽然这一观点远非显而易见，但却容易理解——对象充斥在我们周围，无论是在现实生活中还是在数学中，都可以被视为对象。因此，我们可能倾向于认为，理解世界的关键在于理解 *什么是对象*。这就是集合论 (set theory) 从一个角度所做的（经典逻辑也是如此）——集合论中的主要（甚至可以说唯一的）基本概念就是集合的概念。当数学家说“万物皆集合”时，他们的意思是 *所有对象都可以用集合来表示*。

然而，还有另一种看待事物的方式。当一个对象独立存在时，它是什么？我们能否孤立地研究一个对象，并且一旦它脱离其环境后，是否还有什么值得研究的？正如忒修斯 (Theseus) 曾经问的，如果一个对象经过某种过程使其所有部分被替换，它还是同一个对象吗？

问这些问题可能会让我们怀疑，虽然当我们观察世界时看到的是对象，但理解世界的真正关键在于过程或 *函数 (functions)*。例如，当我们认真思考日常对象时，我们意识到每个对象都有一个特定的 *功能* 或功能，离开了这个功能，它将不再是它本身。比如，一盏不发光的灯还是灯吗？不可食用的食物还是食物吗？这在数学对象中更为明显——如果没有它们之间的函数，这些对象根本不能称之为对象。例如，在逻辑中，我们通过存在量词 (existential quantifiers) 来指定对象，即我们说存在一个对象，使得如此这般。因此，取而代之的是，我们可能会采取相反的观点，即 *对象之所以有趣，只是因为它们是态射的来源和目标*。

虽然这种观点由来已久（可以追溯到巴门尼德的对手赫拉克利特 (Heraclitus)），但无论在哲学领域还是在数学领域，它都很少得到探讨。然而，它在范畴论中却根深蒂固。例如，当我们说某个属性定义了一个对象 *直至唯一同构 (up to a unique isomorphism)* 时，我们的意思正是如此——如果有两个或多个对象是同构的，并且在范畴中从/到所有其他对象的态射完全相同（在范畴中有相同的 *函数*），那么这些对象在所有意图和目的上是等价的。而理解这一点的关键就是自然变换。

那么，你准备好听自然变换了吗？实际上，我认为你还没准备好，所以我想继续谈谈别的事情。让我们重新问一下在上一章开头思考的问题——什么意味着两个范畴相等。

同构与等价 (Isomorphisms and Equivalence)
===

在上一章中，我们讨论了同构 (isomorphisms) 有多么重要，它们在范畴论中如何定义相等性，但同时我们也说 *范畴同构* 并不能捕捉范畴的相等性概念。

![同构范畴 (Isomorphic Categories)](isomorphic_categories.svg)

这只是因为（尽管看起来可能有些矛盾）*同构对象和态射在范畴同构中不被视为相等*，即仅因某些附加同构对象不同的范畴不一定是同构的。

![同构范畴 (Equal Categories)](equal_categories.svg)

然而，这些范畴是等价的。

**巴门尼德：** 这个范畴显然不能等同于另一个——它有不同数量的对象！

**赫拉克利特：** 谁在乎呢兄弟，它们是同构的。

为了更好地理解等价范畴，让我们回到一个从地图到所代表区域的函子。为了使这个函子是可逆的（并且范畴是同构的），地图应该完全表示区域，即每条道路应该都有箭头，每个小地方应该都有点。

![同构范畴 (Isomorphic Map)](isomorphic_map.svg)

这样的地图是必要的，如果你的目标是了解所有的 *地方*，然而，正如我们所说，当我们研究范畴论时，我们不那么关心 *地方*，而是关心 *连接它们的路径*，即我们关注的不是 *对象* 而是 *态射*。

例如，如果有交叉点以某种方式排列，使得从一个交叉点到另一个有路径并且反之亦然，那么地图可以将它们折叠成一个交叉点，但仍然显示所有存在的路径。

![等价范畴 (Equivalent Categories)](equivalent_map.svg)

我们看到，尽管这两个范畴 *不是同构的*，但从其中一个范畴到另一个再返回时，总是会得到 *同构的对象和态射*。

![等价范畴 (Equivalent Categories)](equivalent_map_equivalence.svg)

在这种情况下，我们称这些范畴是 *等价的 (equivalent)*。

订单的等价性 (Equivalence of Orders)
===

在正式定义订单等价性之前，我们需要回顾订单同构的定义。

在关于订单的章节中，我们给出了一个基于 *集合* 同构的订单同构定义。

> 订单同构 (Order Isomorphism) 本质上是两个订单的底层集合的同构 (invertible function)。然而，除了它们的底层集合之外，订单还有连接它们的箭头，因此还有一个条件：为了使一个可逆函数构成订单同构，它必须 *尊重这些箭头*，换句话说，它应该是 *保持订单的*。更具体地说，将这个函数（让我们称之为 $F$）应用于一个集合中的任意两个元素（$a$ 和 $b$）应该导致在另一个集合中具有相同对应顺序的两个元素（因此 $a ≤ b$ 当且仅当 $F(a) ≤ F(b)$）。

但既然我们知道了函子，我们将基于函子的定义重新表述：

> 给定两个订单 $A$ 和 $B$，订单同构包括两个函子 $F: A \to B$ 和 $G: B \to A$，它们的组合将我们带回到相同的对象。

> 更正式地说，对于 $A$ 的所有对象 $a$ 和 $B$ 的对象 $b$，我们应该有 $b = F(G(b))$ 和 $a = G(F(a))$（或者 $ ID_{B} = F \circ G$ 和 $ ID_{A} = G \circ F$）。

![同构订单 (Isomorphic Orders)](isomorphic_orders.svg)

**任务：** 证明这两个定义是等价的。

订单等价与等价类 (Order Equivalence and Equivalence Classes)
---

还记得我们在订单章节中介绍的 *等价类 (equivalence classes)* 概念吗？事实证明，这个概念与等价性有关。为了了解它的关联性，我们可以直观地展示两个等价订单的等价类。

![同构等价类的订单 (Orders with Isomorphic Equivalence Classes)](equivalent_order_classes.svg)

事实证明，两个订单是等价的，当且仅当由它们的等价类组成的订单是同构的。

**任务：** 证明这一点。

范畴的等价性 (Equivalence of Categories)
===

现在我们已经通过订单等价性热身了头脑，接下来我们准备处理更加复杂的 *范畴等价性*。这类似于我们从订单函子（单调映射）过渡到范畴函子，尽管定义看起来更复杂，但实际上只是订单定义的升级版本。

为什么我们需要升级定义？在范畴中，我们可以在任意两个对象之间有多个态射，因此即使通过两个函子组合得到的是同构对象，函数也可能不是同构的。例如，以下两个范畴 *不是* 等价的（左边的范畴只有一个态射，而右边的范畴有两个）。

![不等价的范畴 (Non-equivalent Categories)](unequal_categories.svg)

这看起来似乎与地图等于其所覆盖领土的想法相悖，因为在这种情况下，我们在两个范畴中都有从一个对象到另一个的路径。然而，路径不仅仅是从点 A 到点 B 的简单过程，正如将一个数字转换为布尔值的函数不仅仅是它的类型签名一样。这在订单上下文中很容易被忽略，因为订单中只允许两个对象之间有一条路径，但在范畴中这是必须考虑的。

因此，我们如何使定义变得更加广泛，以适应所有范畴呢？

自然变换 (Natural Transformations)
===

到目前为止，我们已经介绍了态射、函子和自然变换的进展，这可能会让你认为自然变换与态射和函子类似，但它们并不完全相同。更准确地说，自然变换不是递归的——普通态射和函子是对象之间的态射（或 *一态射 (1-morphisms)*），而自然变换是态射之间的态射（称为 *二态射 (2-morphisms)*）。

但是，少说空话，还是画一些图吧。

我们知道自然变换是函子之间的态射，因此我们先画出两个函子（为了简洁省略态射之间的箭头）。

![两个函子 (Two Functors)](natural_functors_objects.svg)

请注意，这两个函子具有相同的签名——它们的输入和输出范畴是相同的——这是它们之间可以通过自然变换连接的必要（但不充分）条件。

构建对象映射的映射 (Building the Object Mapping Mapping)
---

一个函子由两个部分组成——对象映射 (object mapping) 和态射映射 (morphism mapping)，因此作为函子之间的态射，自然变换也应该考虑这两个映射。

首先，让我们连接两个函子的对象映射，创建我们称之为“对象映射的映射”。当我们意识到我们只需要连接函子 *目标范畴 (target category)* 中的对象时，它就比听起来要简单得多。在源范畴中的对象总是相同的，因为两个函子都将包含源范畴中的 *所有* 对象（因为这就是函数的作用，对吧？）

换句话说，映射两个函子的对象部分仅仅涉及指定目标范畴中的一些态射。

![自然变换 (Natural Transformation)](natural_transformation.svg)

注意，这些对象之间的映射并不总是具有函子的性质，因为并非所有对象都被映射到其他对象。

构建态射映射的映射 (Building the Morphism Mapping Mapping)
---

一旦对象映射之间的连接已经建立，态射映射的构建就只有一种方法——获取源范畴中的每个态射，并连接两个函子在目标范畴中生成的态射的图像。

![两个函子 (Two Functors)](natural_functors.svg)

形式定义 (Formal Definition)
---

在结束本章之前，我们来提炼出自然变换的严格定义：对于具有相同类型签名的两个函子 $F$ 和 $G$，其源范畴 $C$ 和目标范畴 $D$ 相同（即 $F : C \to D$ 和 $G : C \to D$），一个自然变换 $\alpha : F \Rightarrow G$ 是一组在 $D$ 中的态射，它将函子 $F$ 的所有目标对象（或称为 $F$ 在 $D$ 中的像）映射到函子 $G$ 的目标对象。

此外，映射必须满足，对于 $C$ 中任何具有签名 $X \to Y$ 的态射，$D$ 中对象 $F(X)$ 总是被映射到 $G(X)$，对象 $F(Y)$ 被映射到 $G(Y)$。

请注意，如果上述条件（有时称为“自然性条件 (naturality condition)”）成立，那么下图将是交换的。这反过来也成立——如果图是交换的，那么条件就成立，所以我们可以说 *这个图和定义是同构的*。因为这个图更简单，我们可以将其视为真正的定义。

![自然变换公式 (Natural Transformation Formula)](natural_transformation_formula.svg)

如果你仔细观察，你会发现这个图与我们的例子唯一的区别在于，这里的态射是垂直排列的，而在我们的例子中它们是水平的。

再次解释自然变换 (Natural Transformations Again)
===

现在我们已经看到了自然变换的定义，接下来我们将再次看到自然变换的定义（如果你觉得这本书的幽默质量有所下降，那只是因为 *事情变得严肃了*）。

我相信一旦你看到了一个自然变换的定义，你一定会觉得意犹未尽。所以让我们再看一个。让我们从我们的两个函子开始。

![两个函子 (Two Functors)](natural_functors.svg)

这个图可能会让我们认为自然变换是一种“二重函子 (double functors)”，每个对象都有两个箭头。这种概念当然无法定义（正如我们多次提到的，函数的全部意义在于每个对象只有一个箭头），但可以定义一个相关的概念，即 *乘积范畴 (product categories)*。

乘积范畴 (Product Categories)
---

我们已经看过 *群/幺半群的乘积 (products of groups/monoids)*，乘积范畴与之类似：取任意两个范畴（在实践中，最好有一个是有限的，但任何两个都可以）。

![乘积范畴的组成部分 (Product Category Components)](product_components.svg)

然后获取这些范畴的对象的所有可能对的集合。

![乘积范畴的对象 (Product Category Objects)](product_set.svg)

有没有办法从这个集合中创建一个范畴？当然，我们在群/幺半群乘积的章节中看到过类似的东西——我们只需取出两个范畴中所有的态射，并将它们复制到其类型签名中包含的所有对中。

![乘积范畴 (Product Category)](product_category.svg)

这就是两个范畴的 *乘积范畴*。

将自然变换视为乘积范畴的函子 (Natural Transformations as Functors of Product Categories)
---

当我们看最后一个图时，你可能会怀疑我们选择的这两个范畴用于演示乘积范畴的概念并非随机选择。你猜对了——我们可以在其中已经看到自然性方块 (naturality square)。

![乘积范畴目标范畴 (Product Category Target Category)](product_category_target_category.svg)

这是因为具有两个对象和一个态射的范畴（如果你还记得，它被称为 $2$）是构建等价于自然变换的函子的关键——因为它有两个对象，它生成源范畴的两个副本，并且因为这两个对象是连接的，这两个副本之间的连接方式与目标范畴中的两个“图像”之间的连接方式相同。所以剩下的就是画出这两个函子。

![乘积范畴中的自然变换 (Natural Transformation in Product Category)](product_category_natural_transformation.svg)

形式定义 (Formal Definition)
---

让我们正式说明我们在这些图中看到的内容。如你所记得的，我们称两个函子为 $F$ 和 $G$，它们的范畴分别为 $C$ 和 $D$（因此 $F : C \to D$ 和 $G : C \to D$）。

此外，我们称具有两个连接对象的范畴为 $2$，其中的态射是 $0$ 和 $1$。

在这种情况下，我们的自然变换 $\alpha : F \Rightarrow G$ 只是从 $2$ 的乘积范畴到 $C$ 的函子，即 $2 \times C \to G$，如此一来，如果我们取出 $C$ 的子范畴，该子范畴仅包含具有 $0$ 对象的那些对象及其态射，那么该函子等价于 $F$，如果我们考虑包含 $1$ 的子范畴，那么该函子等价于 $G$（我们写作 $\alpha(-,0)=F$ 和 $\alpha(-,1)=G$）。 Voilà!

**任务：** 查看这两个定义是如何等价的。

---

自然变换的其他定义
---

自然变换从主函子 (representable functors) 到其他函子的转换就是常规函子的转换。

极限与余极限 (Limits and Colimits)
===

自然性解释的插曲 (Interlude: Naturality Explained)
---

构造同构并不难——给定两个包含三个对象的集合，有三种同构连接它们，而这个数字呈指数增长。

但大多数这些同构只是随机的。在我们的研究中，我们只对 *有意义的* 结构感兴趣。在范畴论中，“有意义”的抽象概念通过自然性条件 (naturality condition) 来捕捉。

---

极限 (Limits)
===

乘积是范畴论中称为 *极限 (limits)* 的一个例子。极限是一个总结了由其他对象和态射组成的结构（也称为图 (diagram)）的对象，它允许我们以后检索其中的一部分。

极限还必须是唯一的，因为对于相同的结构，不能有两个极限对象。

极限的概念与交换图 (commuting diagrams) 的概念密切相关。当我们研究乘积时，这一点并不明显，因为乘积的图没有几条通往同一点的路径。

尽管我们不会在此深入讨论，但极限可以像我们研究的其他内容一样被正式定义。

---

乘积是极限 (Products Are Limits)
===

好了，我们说极限总结了一个结构。乘积总结的是什么结构？它是由两个没有连接的对象（集合）组成的结构。

![外部图 (External Diagram)](product_part_external.svg)

为什么乘积在表示这两个对象时是唯一的？因为任何其他也表示它们的对象都通过一个态射连接到乘积（这被称为极限的 *泛属性 (universal property)*）。

---

自然变换与结合律 (Natural Transformations and Associativity)
===

自然变换的定义只说明了 $(ab)c = a(bc)$。

---

自由对象 (Free Objects)
===

[什么是自由对象？ (What are Free Objects?)](https://math.stackexchange.com/questions/131389/what-are-free-objects)

---

Monad 单子
===

---

可表函子 (Representable Functors)
===

一个 Hom-函子可以始终转换为任何取值为集合的函子（Yoneda 引理），但反之则不然。

---

Yoneda 引理 (Yoneda Lemma)
===

---

[Applied Category Theory Course](https://www.azimuthproject.org/azimuth/show/Applied+Category+Theory+Course#Course)

---

[Herding Cats](https://eed3si9n.com/herding-cats/day1.html)

---

[Topology: MIT Press](https://topology.mitpress.mit.edu/)

---

[What Is a Natural Transformation?](https://www.math3ma.com/blog/what-is-a-natural-transformation)

---

[Makelele 和线性代数](https://graphicallinearalgebra.net/2015/04/23/makelele-and-linear-algebra/)

---

[什么是范畴论？](https://www.math3ma.com/blog/what-is-category-theory-anyway)

---

[数学工具箱 (Mathematical Toolkit)](https://www.youtube.com/watch?v=8j9AF2cfmFo&list=PLk-BCMYCWSzW-nPNnw19Y6oQJnvaAcp1I)


https://www.azimuthproject.org/azimuth/show/Applied+Category+Theory+Course#Course


https://eed3si9n.com/herding-cats/day1.html


https://topology.mitpress.mit.edu/


https://www.math3ma.com/blog/what-is-a-natural-transformation

https://graphicallinearalgebra.net/2015/04/23/makelele-and-linear-algebra/

https://www.math.toronto.edu/gscott/WhatVS.pdf

https://www.youtube.com/playlist?list=PLk-BCMYCWSzW-nPNnw19Y6oQJnvaAcp1I

https://brilliant.org/courses/linear-algebra/linear-equations-5/
 https://www.math3ma.com/blog/what-is-category-theory-anyway

*/
