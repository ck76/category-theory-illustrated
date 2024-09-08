---
layout: default
title: Functors
---

函子 (Functors)
===

从本章开始，我们将稍微改变策略（因为我相信你已经厌倦了在不同主题之间跳跃），我们将全速深入范畴的世界，使用迄今为止看到的结构作为背景。这将使我们能够推广这些结构中研究过的一些概念，从而使它们对所有范畴都适用。

我们迄今看到的范畴 (Categories we saw so far)
===

到目前为止，我们看到了许多不同的范畴和范畴类型。让我们再回顾一下：

### 集合范畴 (The category of sets)
我们首先审视了所有范畴之母——*集合范畴*。

![集合范畴](../10_functors/category_sets.svg)

我们还看到了它包含许多其他范畴，例如编程语言中的类型范畴。

### 特殊类型的范畴 (Special types of categories)
我们还学习了其他代数对象，它们实际上只是*特殊类型的范畴*，例如只包含一个*对象*的范畴（如单子、群）和在任意两个对象之间只有一个*态射*的范畴（如预序、偏序）。

![范畴类型](../10_functors/category_types.svg)

### 其他范畴 (Other categories)
我们还定义了许多基于不同概念的*范畴*，例如基于逻辑或编程语言的范畴，也有一些“没那么严肃的范畴”，例如颜色混合的偏序范畴。

![颜色混合范畴](../10_functors/category_color_mixing.svg)

### 有限范畴 (Finite categories)
最重要的是，我们看到了*完全是虚构的*范畴，例如我的足球运动员层级。这些正式被称为*有限范畴*。

![有限范畴](../10_functors/finite_categories.svg)

尽管它们本身可能没什么用，但背后的想法很重要——我们可以画出任何点和箭头的组合并称其为一个范畴，就像我们可以用任何物体的组合构造一个集合一样。

### 审视一些有限范畴 (Examining some finite categories)
---

为将来参考，让我们看看一些重要的有限范畴。

最简单的范畴是 $0$（享受一下这个简约的图表）。

![有限范畴 0](../10_functors/finite_zero.svg)

接下来是最简单的范畴 $1$——它由一个对象组成，除了其恒等态射之外没有其他态射（我们不绘制恒等态射，按照惯例）。

![有限范畴 1](../10_functors/finite_one.svg)

如果我们将对象的数量增加到两个，我们会看到几个更有趣的范畴，例如包含两个对象和一个态射的范畴 $2$。

![有限范畴 2](../10_functors/finite_two.svg)

**任务：** 还有另外两个只包含 2 个对象且两个对象之间至多有一个态射的范畴，画出它们。

最后，范畴 $3$ 包含 3 个对象以及 3 个态射（其中一个是其他两个的复合态射）。

![有限范畴 3](../10_functors/finite_three.svg)

范畴同构 (Categorical isomorphisms)
===

我们所看到的许多范畴彼此非常相似，例如，颜色混合偏序和表示逻辑的范畴都有一个*最大*和*最小*对象。为了指出这些相似性并理解它们的意义，能够使用正式的方式将范畴相互连接是很有用的。最简单的一种连接方式就是老朋友*同构*。

### 集合同构 (Set isomorphisms)
在第1章中，我们讨论了*集合同构*，它在两个集合之间建立了等价关系。如果你忘记了，集合同构是集合之间的*双向函数*。

![集合同构](../10_functors/set_isomorphism.svg)

它也可以被视为两个“互为逆”的函数，组合后等于恒等函数。

### 序同构 (Order isomorphisms)
在第4章中，我们遇到了*序同构*，并且看到它们类似于集合同构，但多了一个条件——除了保持对象之间的映射外，定义同构的函数还必须保持对象的顺序，例如一个序中的最大对象应该与另一个序中的最大对象连接，最小对象应该与最小对象连接，所有中间的对象也应如此。

![序同构](../10_functors/order_isomorphism.svg)

更正式地说，对于任何 $a$ 和 $b$，如果我们有 $a ≤ b$，那么我们也应该有 $F(a) ≤ F(b)$（反之亦然）。

### 范畴同构 (Categorical isomorphisms)
现在，我们将推广序同构的定义，使其适用于所有其他范畴（即适用于可能在两个对象之间有多个态射的范畴）：

> 给定两个范畴，它们之间的同构是对象集合之间的可逆映射，*以及*连接它们的态射之间的可逆映射，并且每个范畴的态射映射到另一个范畴中*具有相同签名*的态射。

![范畴同构](../10_functors/category_isomorphism.svg)

仔细检查这个定义后，我们会意识到，尽管它*听起来*更复杂（看起来*更凌乱*）一些，但实际上它与我们对序同构的定义是*相同的*。

只不过当两个对象之间只有一个态射时，所谓的“态射映射”是平凡的，所以我们可以忽略它们。

![序同构](../10_functors/category_order_isomorphism_2.svg)

**问题：** 序的态射函数是什么？

<!--
我们总是将源范畴的单一态射映射到目标范畴的单一态射（由于*保持序*的条件，该态射保证存在）
-->

然而，当两个对象之间可以有多个态射时，我们需要确保源范畴中的每个态射在目标范畴中都有对应的态射。因此，我们不仅需要对象之间的映射，还需要它们的态射之间的映射。

![范畴同构](../10_functors/category_order_isomorphism.svg)

顺便说一句，我们刚刚做的事情（将为更狭窄结构（序）定义的概念重新定义为更广泛的结构（范畴））称为*概念推广*。

### 范畴同构的问题 (The problem with categorical isomorphisms)
---

仔细研究后，我们意识到定义范畴同构并不难。然而，还有另一个问题，即它们*并没有捕捉到范畴相等的本质*。我想出一个非常好的直观解释，但这段空间太窄，无法容纳这个解释。因此，我们将在下一章中讨论一个更适合定义范畴之间*双向连接*的方法。

但首先，我们需要研究范畴之间的*单向连接*，即*函子*。

PS: 范畴同构在实践中也*非常罕见*——我能想到的唯一例子是上一章中的柯里–霍华德–兰贝克同构。这是因为如果两个范畴是同构的，那么完全没有理由将它们视为不同的范畴——它们实际上是同一个范畴。

<!--
漫画：
好的，我想我明白了——同构是当你有两个相似的图，然后把点连起来。
差不多是这样。
-->
什么是函子 (What are functors)
===

逻辑学家鲁道夫·卡纳普 (Rudolf Carnap) 首次提出了“函子”这个术语，作为他形式化自然语言（如英语）的项目的一部分，以创建一种精确的方式来讨论科学。最初，函子是指一个单词或短语，它的意义可以通过与数值结合来定制，比如“$x$ 点的温度”这个短语，其含义根据 $x$ 的值而变化。

换句话说，函子是一个*作为函数*的短语，但不是集合之间的函数，而是*语言概念*之间的函数（例如时间和温度）。

![卡纳普设想的函子](../10_functors/functor_carnap.svg)

后来，范畴论的发明者之一桑德斯·麦克莱恩 (Sanders Mac Lane) 借用了这个词，用来描述*在范畴之间充当函数的东西*，他将其定义如下：

> 两个范畴之间的函子（我们称它们为 $A$ 和 $B$）由两个映射组成——一个将 $A$ 中的每个*对象*映射到 $B$ 中的一个对象，另一个将 $A$ 中任意两个对象之间的每个*态射*映射到 $B$ 中的态射，这种映射方式*保持了范畴的结构*。

![函子](../10_functors/functor.svg)

现在让我们逐一解读这个定义的各个部分。

### 对象映射 (Object mapping)
---

在上面的定义中，我们使用“映射”一词来避免误用“函数”这个词，虽然它不是完全符合传统定义的函数。但在这种情况下，将映射称为函数几乎不算错——如果忽略态射，并将源范畴和目标范畴视为集合，对象映射实际上就是一个普通的函数。

![对象的函子](../10_functors/functor_objects.svg)

更正式的对象映射定义涉及到*范畴的底层集合*的概念：给定范畴 $A$，$A$ 的底层集合是一个集合，它的元素是 $A$ 的对象。利用这个概念，我们说两个范畴之间的对象映射是它们底层集合之间的*函数*。函数的定义仍然相同：

> 函数是两个集合之间的关系，将一个集合的每个元素（称为函数的*源集合*）与另一个集合中的一个元素匹配（称为函数的*目标集合*）。

### 态射映射 (Morphism mapping)
---

构成函子的第二个映射是范畴态射之间的映射。这个映射也类似于函数，但附加了一个要求，即 $A$ 中具有特定源和目标的态射必须映射到 $B$ 中具有相应源和目标的态射，符合对象映射的定义。

![态射的函子](../10_functors/functor_morphisms.svg)

更正式的态射映射定义涉及到*同态集* (homomorphism set) 的概念：它是一个包含在给定范畴中两个对象之间的所有态射的集合。利用这个概念，我们说两个范畴的态射映射由它们各自的同态集之间的*一组函数*构成。

![态射的函子](../10_functors/functor_morphisms_formal.svg)

（注意，我们使用*同态集*和*底层集合*的概念，从集合论“逃逸”到范畴论中，并使用函数来定义一切。）

### 函子定律 (Functor laws)
---

到目前为止，我们看到了构成函子的两个映射（一个是对象之间的映射，另一个是态射之间的映射）。但并不是每一对这样的映射都构成函子。正如我们所说，除了存在映射之外，这些映射还必须*保持源范畴的结构*到目标范畴。为了理解这意味着什么，我们回顾第2章对范畴的定义：

> 范畴是*对象*（可以看作点）和*态射*（箭头）组成的集合，其中态射从一个对象到另一个对象，并满足：
> 1. 每个对象必须具有恒等态射。
> 2. 必须有一种方式将两个具有适当类型签名的态射组合成第三个态射，并且这种组合是结合律的。

因此，这一定义转化为以下两条*函子定律*：

1. 态射之间的函数应*保持恒等性*，即所有恒等态射应映射到其他恒等态射。
   ![函子定律 - 恒等性](../10_functors/functor_laws_identity.svg)

2. 函子还应*保持复合*，即对于任意两个态射 $f$ 和 $g$，在源范畴中对应于它们复合的态射 $F(g•f)$ 应该被映射到目标范畴中对应的复合态射 $F(g)•F(f)$ 上，即 $F(g•f) = F(g)•F(f)$。

![函子定律 - 复合性](../10_functors/functor_laws_composition.svg)

这两条定律完成了对函子的定义——这是一个简单但非常强大的概念，我们接下来会看到它的强大之处。

### 日常语言中的函子 (Functors in everyday language)
---

在日常生活中有一个常见的说法（本书中也经常使用这种说法），如下所示：

> 如果 $a$ 类似于 $F a$，那么 $b$ 也类似于 $F b$。

或者说“$a$ 与 $F a$ 之间有某种关系，类似于 $b$ 与 $F b$ 之间的关系”，例如“如果学校像公司，那么老师就像老板”。

这种说法实际上是用日常语言描述函子的一种方式：我们的意思是，在学校和老师之间有某种联系（用范畴论的术语来说是“态射”），类似于公司和老板之间的联系，即存在某种保持结构的映射，将与学校相关的事物范畴映射到与工作相关的事物范畴，将学校（$a$）映射到公司（$F a$），将老师（$b$）映射到老板（$F b$），并且学校与老师之间的关系（$a \to b$）被映射为公司与老板之间的关系（$F a \to F b$）。

### 图表是函子 (Diagrams are functors)
---

> “符号是一种通过了解它，我们可以了解更多东西的存在。”—— 查尔斯·桑德斯·皮尔斯 (Charles Sanders Peirce)

我们将从一个非常*元*的函子例子开始——本书中的图表/插图。

你可能已经注意到，图表在范畴论中扮演了特殊的角色——在其他学科中，图表的功能仅仅是辅助性的，即它们只是展示已经通过其他方式定义的内容，而在这里，*图表本身就是定义*。

例如，在第1章中我们给出了以下函数复合的定义。

> 两个函数 $f$ 和 $g$ 的复合是一个第三个函数 $h$，其定义方式使得该图表可交换。

![函数复合 - 通用定义](../10_functors/functions_compose_general.svg)

我们都看到了通过图表定义事物的好处，而不是写下冗长的定义，比如：

> “假设你有三个对象 $a$、$b$ 和 $c$，以及两个态射 $f: b \to c$ 和 $g: a \to b$……”

然而，用图表定义事物会带来一个问题——数学中的定义应该是正式的，所以如果我们想使用图表作为定义，我们必须首先*形式化图表本身的定义*。

那么我们该如何做呢？一个关键的观察是，图表看起来像有限范畴，例如，上述定义与范畴 $3$ 看起来相似。

![有限范畴 3](../10_functors/finite_three.svg)

然而，这只是故事的一部分，因为有限范畴只是结构，而图表是*符号*。它们是“通过了解它，我们可以了解更多东西”，正如皮尔斯著名的说法（或者用翁贝托·艾柯 (Umberto Eco) 的话来说，“……可以用来撒谎的东西”）。

因此，除了编码图表结构的有限范畴外，图表的定义还必须包括一种在其他上下文中“解释”这个范畴的方式，即它们必须包括*函子*。

![图表作为函子](../10_functors/diagram_functor.svg)

这就是函子概念让我们形式化图表概念的方式：

> 一个*图表*由

一个有限范畴（称为*索引范畴*）和从它到其他范畴的函子组成。

如果你了解符号学，您可以将函子的源范畴和目标范畴视为*能指*和*所指*。

由此你可以看出，函子在范畴论中扮演着非常重要的角色。正因为如此，范畴论中的图表可以*形式化指定*，即它们本身就是范畴对象。

你甚至可以说它们是范畴对象的*卓越代表*（TODO: 删除最后这个笑话）。

### 地图是函子 (Maps are functors)
---

> “地图不是它所代表的领土，但如果是正确的，它具有与领土相似的结构，这使它具有实用性。”—— 阿尔弗雷德·科日布斯基 (Alfred Korzybski)

函子有时被称为“映射”是有原因的——地图，就像其他所有图表一样，实际上是函子。如果我们将包含城市和连接城市的道路的空间视为一个范畴，其中城市是对象，道路是态射，那么一张路线图可以被视为代表该空间某一区域的范畴，以及将该地图中的对象映射到现实世界对象的函子。

![城市路径的预序与地图](../10_functors/preorder_map_functor.svg)

在地图中，通常不会显示复合得到的态射，但我们经常使用它们——它们被称为*路线*。保持复合性的定律告诉我们，我们在地图上创建的每条路线都对应现实世界中的一条路线。

![城市路径的预序与地图 - 路线](../10_functors/preorder_map_functor_route.svg)

注意，为了成为一个函子，地图不必列出*所有*现实中存在的道路和*所有*旅行选项（“地图不是领土”），唯一的要求是*它列出的道路必须是真实存在的*——这是所有多对一关系（即函数）共有的特性。

### 人类感知具有函子性质 (Human perception is functorial)
---

我们看到，除了是一个范畴论概念之外，函子还与许多研究人类心智的学科相关，如逻辑、语言学、符号学等。为什么会这样呢？我最近写了一篇[关于使用逻辑建模现实生活思维的博客文章](/logic-thought)，其中探讨了函子（以及“映射”）的“非凡有效性”，我认为人类的感知和思维是具有函子性质的。

我的观点是，为了感知我们周围的世界，我们通过一系列函子，从更原始的“低层次”心理模型转向更抽象的“高层次”模型。

我们可以说，感知始于原始的感官数据。然后，通过一个函子，我们转向一个包含基本世界模型的范畴（告诉我们我们在空间中的位置、我们看到的物体数量等）。接着，我们将这个模型与另一个更抽象的模型连接起来，该模型为我们提供了所处情况的更高层次视图，依此类推。

![感知具有函子性质](../10_functors/chain.svg)

你可以将这视为从简单到抽象的进程，从具有较少态射的范畴进展到具有更多态射的范畴——我们从没有任何联系的感官数据组成的范畴开始，接着进入另一个范畴，其中一些数据片段之间有了联系。然后，我们将这种结构转移到具有更多联系的另一个范畴。

![感知具有函子性质](../10_functors/logic_thought.svg)

当然，这只是一个猜想，但当我们看到函子对于我们之前讨论的数学结构有多重要时，或许可以证明它有一定的依据。

### 单子中的函子 (Functors in monoids)
---

在这个小插曲之后，让我们回到我们通常的操作方式：

嘿，你知道在群论中有一个很酷的东西叫做*群同态*（当我们谈论单子时，它被称为*单子同态*）——它是一个在群的底层集合之间保持群运算的函数。

例如，如果现在是 00:00（或中午 12 点），那么 $n$ 小时后会是什么时间？这个问题的答案可以通过一个以整数集为源和目标的函数来表达。

![群同态作为函数](../10_functors/group_homomorphism_function.svg)

这个函数很有趣——它保持（模）加法运算：如果 13 小时后是 1 点，而 14 小时后是 2 点，那么（13 + 14）小时后是（1 + 2）点。

![群同态](../10_functors/group_homomorphism.svg)

或者正式地说，如果我们称这个函数为 $F$，那么我们有以下等式：$F(a + b) = F(a) + F(b)$（其中右边的 $+$ 表示模加法）。由于这个等式成立，$F$ 函数是一个*群同态*，它将整数加法群映射到模 11 加法群（你可以将 11 替换为任何其他数）。

群不必如此相似才能在它们之间存在同态。举个例子，将任何数 $n$ 映射为 2 的*指数* $n \to 2ⁿ$，这个函数给出了整数加法群和整数乘法群之间的群同态，即 $F(a + b) = F(a) \times F(b)$。

![不同群之间的群同态](../10_functors/group_homomorphism_addition_multiplication.svg)

哦对了，我们在讨论什么来着？对，群同态是函子。要理解为什么，我们切换到范畴论视角，并重新审视我们第一个例子（为了简化图表，我们使用模 2 代替模 11）。

![群同态作为函子](../10_functors/group_homomorphism_functor.svg)

看来，当我们将群/单子视为单对象范畴时，群/单子同态实际上就是这些范畴之间的函子。让我们看看是不是这样。

**对象映射 (Object mapping)**
---

当群/单子被视为范畴时，它们只有一个对象，所以在任何两个群/单子之间只有一个可能的对象映射——将源群的唯一对象映射到目标群的对象（图中未绘制）。

**态射映射 (Morphism mapping)**
---

因此，对于群同态来说，态射映射是唯一相关的组成部分。在范畴论视角中，群的对象（如 $1$、$2$、$3$ 等）对应于态射（如 $+1$、$+2$、$+3$ 等），因此态射映射就是群对象之间的映射，如图所示。

### 函子定律 (Functor laws)
---

第一个函子定律是平凡的，它只是说源群的唯一恒等对象（对应于其唯一对象的恒等态射）应该映射到目标群的唯一恒等对象。

如果我们记住，群的结合运算（组合两个对象）对应于将群视为范畴时的*函数复合*，那么我们会意识到群同态方程 $F(a + b) = F(a) \times F(b)$ 只是第二个函子定律 $F(g•f) = F(g)•F(f)$ 的一种表述。

许多代数运算都满足这个方程，例如群同态的函子定律 $n \to 2ⁿ$ 就是著名的代数规则 $gᵃ gᵇ= gᵃ⁺ᵇ$。

**任务：** 尽管很简单，但我们没有证明第一个函子定律（关于保持恒等性的定律）总是成立。有趣的是，对于群/单子来说，它实际上是从第二个定律推导出来的。试着证明这一点。首先从恒等函数的定义开始。

### 序中的函子 (Functors in orders)
---

现在让我们谈论一个与函子完全无关的概念，开个玩笑（嘿，冷笑话总比没有笑话好，对吧？）。在序的理论中，我们有序之间的函数（这并不奇怪，因为序就像单子/群一样，基于集合），其中一个非常有趣的函数类型，具有在微积分和分析中的应用，就是*单调函数*（也叫做*单调映射*）。这是两个序之间的一个函数，它*保持源序对象的顺序*，在目标序中也保持对象的顺序。所以当对于源序中的每一个 $a$ 和 $b$，如果 $a ≤ b$，那么 $F(a) ≤ F(b)$，此时函数 $F$ 是单调的。

例如，将当前时间映射到某物体行驶距离的函数是单

调的，因为行驶距离随着时间增加（或保持不变）而增加。

![单调函数](../10_functors/monotone_map.svg)

如果我们在折线图上绘制这个或任何其他单调函数，我们会看到它的趋势只有一个方向（即只向上或只向下）。

![单调函数，折线图表示](../10_functors/monotone_map_plot.svg)

现在我们要证明单调函数也是函子，准备好了吗？

**对象映射 (Object mapping)**
---

像在范畴中一样，序的对象映射是其底层集合之间的函数。

**态射映射 (Morphism mapping)**
---

与单子不同，函子的对象映射部分是平凡的。这里正好相反：态射映射是平凡的——给定源序中的两个对象之间的态射，我们将该态射映射到目标序中对应的态射。单调函数尊重元素的顺序，确保后者态射的存在。

### 函子定律 (Functor laws)
---

不难看出，单调映射遵循第一个函子定律，因为恒等态射是唯一的，存在于每个对象与自身之间。

第二条定律 ($F(g•f) = F(g)•F(f)$) 也显然成立：$F(g•f)$ 和 $F(g)•F(f)$ 两个态射具有相同的类型签名。而在序中，具有给定类型签名的态射只能有一个，因此这两个态射必然是相等的。

**任务：** 扩展证明。

<!--
And the second law ($F(g•f) = F(g)•F(f)) also follows from the fact that there is only one morphism with a given signature. 

Suppose that in the source order we have two morphisms with the following type signature:

$f :: a \to b$ and $g :: b \to c$. 

Then, if we compose those two morphisms in the target order ($F(g)•F(f)$), we get a morphism from object $F(a)$ to object $F(c)$ ($F(g)•F(f) :: F(a) \to F(c)$).

If we compose the two morphisms in the source order, and we use the functor to get the corresponding morphism in the target order ($F(g•f)$) we get another morphism from object $F(a)$ to object $F(c)$ ($F(g•f) :: F(a) \to F(c)$)

But because in orders there can be just one morphism between $F(a)$ and $F(c)$ so these two morphisms must be equal to one another.
 
-->

Linear functions
===

OK, enough with this abstract nonsense, let's talk about "normal" functions --- ones between numbers. 

In calculus, there is this concept of *linear functions* (also called "degree one polynomials") that are sometimes defined as functions of the form $f(x) = xa$ i.e. ones that contain no operations other than multiplying the argument by some constant (designated as $a$ in the example). 

But if we start plotting some such functions we will realize that there is another way to describe them --- their graphs are always comprised of straight lines.

![Linear functions](../10_functors/linear_functions.svg)

**Question:** Why is that?

Another interesting property of these functions is that most of them *preserve* addition, that is for any $x$ and $y$, you have $f(x) + f(y) = f(x + y)$. We already know that this equation is equivalent to the second functor law. So linear functions are just *functors between the group of natural numbers under addition and itself.* As we will see later, they are example of functors in the *category of vector spaces*.

![Linear functions](../10_functors/linear_function_functor.svg)

**Question:** Are the two formulas we presented to define linear functions completely equivalent?

<!--
Let 
$f(x) = ax $

and 

$f(y) = ay $

Then

$f(x) + f(y) = ax + ay $

This means that

$f(x) + f(y) = a(x + y)$

but $f(x) = ax$, so 

$f(x) + f(y) = f(x + y)$
-->

And if we view that natural numbers as an order, linear functions are also functors as well, as all functions that are plotted with straight lines are obviously monotonic.

Note, however, that not all functions that are plotted straight lines preserve addition --- functions of the form $f(x) = x * a + b$ in which $b$ is non-zero, are also straight lines (and are also called linear) but they don't preserve addition.

![Linear functions](../10_functors/linear_function_non_functor.svg)

For those, the above formula looks like this: $f(x) + b + f(y) + b = f(x + y) + b$.

<!--

The category of topological spaces
---
The smoothness of the mapping means that paths may stretch or collapse but not break. 
-->


Functors in programming. The list functor
===

Types in programming language form a category, associated to that category are some functors that programmers use every day, such as the list functor, that we will use as an example. The list functor is an example of a functor that maps from the realm of simple (primitive) types and functions to the realm of more complex (generic) types and functions. 

![A functor in programming](../10_functors/functor_programming.svg)

But let's start with the basics: defining the concept of a functor in programming context is as simple as changing the terms we use, according to the table in chapter 2 (the one that compares category theory with programming languages), and (perhaps more importantly) changing the font we use in our formulas from "modern" to "monospaced".

> A functor between two categories (let's call them `A` and `B`) consists of a mapping that maps each ~~object~~ *type* in `A` to a type in `B` and a mapping that maps each ~~morphism~~ *function* between types in `A` to a function between types in `B`, in a way that preserves the structure of the category.

Comparing these definitions makes us realize that mathematicians and programmers are two very different communities, that are united by the fact that they both use functors (and by their appreciation of peculiar typefaces).

Type mapping
---

The first component of a functor is a mapping that converts one type (let's call it `A`) to another type (`B`). So it is *like a function, but between types*. Such constructions are supported by almost all programming languages that have static type checking in the first place --- they go by the name of *generic types*. A generic type is nothing but a function that maps one (concrete) type to another (this is why generic types are sometimes called *type-level functions*). 

![A functor in programming - type mapping](../10_functors/functor_programming_objects.svg)

Note that although the diagrams they look similar, a *type-level* function is completely different from a *value-level* function. A value-level function from `String`, to `List<String>` (or in mathy Haskell/ML-inspired notation $string \to List\ string$ is) converts a *value* of type `String` (such as `"foo"`) and to a value of type `List<String>`. You even have (as we will see later) a value-level functions with signature $a \to List\ a$ that can convert any value to a list of elements containing that value, but this is different from the *type-level* function `List<A>` as that one converts a *type* $a$ to a *type* $List\ a$ (e.g. the type `string` to the type $List\ string$, $number$ to $List\ number$ etc.).

Function mapping
---

So the type mapping of a functor is simply a generic type in a programming language (we can also have functors between two generic types, but we will review those later). So what is the *function mapping* --- this is a mapping that convert any function operating on simple types, like $string \to number$ to a function between their more complex counterparts e.g. $List\ string \to List\ number$.

![A functor in programming - function mapping](../10_functors/functor_programming_morphisms.svg)

In programming languages, this mapping is represented by a higher-order function called `map` with a signature (using Haskell notation), $(a \to b) \to (Fa \to Fb)$, where $F$ represents the generic type.

Note that although any possible function that has this type signature (that that obeys the functor laws) gives rise to a functor, *not all such functors are useful*. Usually, there is only one of them that makes sense for a given generic type and that's why we talk about *the* list functor, and see `map` is defined directly in the in the generic datatype, as a method.

In the case of lists and similar structures, the *useful* implementation of `map` is the one that applies the original (simple) function to all elements of the list. 

```
class Array<A> {
  map (f: A ➞ B): Array<B> {
    let result = [];
    for (obj of this) {
      result.push(f(obj));
    }
    return result;
  }
}
```

Functor laws
---

Aside from facilitating code reuse by bringing in all standard functions of simple types in a more complex context, `map` allows us to work in a way that is predictable, courtesy of the functor laws, which in programming context look like this.

Identity law:
```
a.map(a => a) == a
```
Composition law:
```
a.map(f).map(g) == a.map((a) => g(f(a)))
```

**Task:** Use examples to verify that the laws are followed.

What are functors for
===

Now, that we have seen so many examples of functors, we finally can attempt to answer the million-dollar question, namely what are functors for and why are they useful? (often formulated also as "Why are you wasting your/my time with this (abstract) nonsense?") 

Well, we saw that *maps are functors* and we know that *maps are useful*, so let's start from there. 

So, why is a map useful? Well, it obviously has to do with the fact that the points and arrows of the map corresponds to the cities and the roads in the place you are visiting in i.e. due to the very fact that it is a functor, but there is a second aspect as well - maps (or at least those of them that are useful) are *simpler to work with* than the actual things they represent. For example, road maps are useful, because they are *smaller* than the territory they represent, so it is much easier to go look up the routes between two given places by following a map, than to actually travel through all them in real life. 

And functors in programming are used for similar reason - functions that involve simple types like `string`, `number`, `boolean` etc. are ... simple, and least when compared with functions that work with lists and other generic types. Using the `map` function allows us to operate on such types without having to think about them and to derive functions that transform them, from functions that transform simple values. In other words, functors are means of *abstraction*.

Of course, not all routes on the map and no functions that between generic datatypes can be derived just by functions between the types they contain. This is generally true for many "useful" functors: because their source categories are "simpler" than the target, some of the morphisms in the target have no equivalents in the source i.e. making the model simpler inevitably results in losing some of its capabilities. This is a consequence of "the map is not the territory" principle (or in programming context, "every abstraction is a leaky abstraction", as Joel Spolsky put it): 

Pointed functors
===

Now, before we close it off, we will review one more functor-related concept that is particularly useful in programming - *pointed endofunctors.*

Endofunctors
---

To understand what pointed endofunctors are, we have to first understand what are *endofunctors*, and we already saw some examples of those in the last section. Let me explain: from the way the diagrams there looked like, we might get the impression that different type families belong to different categories.

![A functor in programming](../10_functors/functor_programming.svg)

But that is not the case - all type families from a given programming language are actually part of one and the same category - the category of *types*.

![A functor in programming](../10_functors/functor_programming_endo.svg)

Wait, so this is permitted? Yes, these are exactly what we call *endofunctors* i.e. ones that have one and the same category as source and target.

The identity functor
---

So, what are some examples of endofunctors? I want to focus on one that will probably look familiar to you - it is the *identity functor* of each category, the one that maps each object and morphism to itself.

![Identity  functor](../10_functors/identity_functor.svg)

And it might be familiar, because an identity functor is similar to an identity morphism - it allow us to talk about value-related stuff without actually involving values. 

Pointed functors
---

Finally, the identity functor, together with all other functors to which the identity functor can be *naturally transformed* are called *pointed functors* (i.e. a functor is pointed if there exist a morphism from the identity functor to it). As we will see shortly, the list functor is a pointed functor.

![Pointed functor](../10_functors/pointed_functor.svg)

We still haven't discussed what does it mean for one functor to be naturally transformed to another one (although the commuting diagram above can give you some idea). This is a complex concept and we have a whole chapter about it (the next one). 

However if we concentrate solely on the category of types in programming languages, then *a natural transformation is just a function* that translates each value of what we called the "simple types" to a value of the functor's generic type i.e. $a \to F\ a$), in a way that this diagram commutes.

![Pointed functor in Set](../10_functors/pointed_functor_set.svg)

What does it take for this diagram to commute? It means that when you have two equivalent routes for reaching from the top-left diagonal to the bottom-right diagonal i.e. that applying any function between any two types ($a \to b$), followed by the lifting function ($b \to F\ b$), is equivalent to applying the lifting function first ($a \to F\ a$), and then the mapped version of the original function second ($F\ a \to F\ b$).

The list functor is pointed, because such a function exist for the list functor - it is the function $a \to [\ a\ ]$ that puts every value in a "singleton" list. So, for every function between simple types, such as the function $length:\ string \to number$ we have a square like this one.

![Pointed functor in Set](../10_functors/pointed_functor_set_internal.svg)

And the fact that the square commutes is expressed by the following equality:

```
[a].map(f) = [f(a)]
```
By the way, it may not look like it right now, but this commuting square might be the one of the most-important diagram that exist in category theory, second to only the triangle of functional composition.

The category of small categories
===

Ha, I got you this time (or at least I *hope* I did) - you probably thought that I won't introduce another category in this chapter, but this is exactly what I am going to do now. And (surprise again) the new category won't be the category of functors (don't worry, we will introduce that in the next chapter). Instead, we will examine the category of (small) categories, that has all the categories that we saw so far as objects and functors as its morphisms, like $Set$ - the category of sets, $Mon$, the category of monoids, $Ord$, the category of orders etc.

![The category of categories](../10_functors/category_of_categories.svg)

We haven't yet mentioned the fact that functors compose (and in an associative way at that), but since a functor is just a bunch of functions, it is no wonder that it does.

**Task:** Go through the functor definition and see how do they compose. 

**Question:** What are the initial and terminal object of the category of small categories.

Categories all the way down
---

The recursive nature of category theory might sometimes leave us confused: we started by saying that categories are *composed of objects and morphisms*, but now we are saying that there are *morphisms between categories* (functors). And on top of that, there is a category where *the objects are categories themselves*. Does that mean that categories are an example of... categories? Sounds a bit weird on intuitive level (as for example biscuits don't contain other biscuits and houses don't use houses as building material), but it is actually the case. Like, for example, every monoid is a category with one just object, but at the same time, monoids can be seen as belonging to one category - the category of monoids, where they are connected by monoid homomorphisms. We also have the category of groups, for example, which contains the category of monoids as a subcategory, as all monoids are groups etc.

Category theory does *categorize* everything, so, from a category-theoretic standpoint, all of maths is *categories all the way down*. Whether you would threat a given category as a universe or as a point depends solemnly on the context. Category theory is an *abstract* theory. That is, it does not seek to represent an actual state of affairs, but to provide a language that you can use to express many different ideas.
