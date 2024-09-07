---
layout: default
title: Monoids 
---
Monoids 等等 (Monoids etc)
===

既然我们已经讲完了范畴 (categories)，现在让我们看看一些同样有趣的结构——幺半群 (monoids)。与范畴一样，幺半群/群 (monoids/groups) 也是由元素集合及操作组成的抽象系统，用于操作这些元素。然而，这些操作与我们在范畴中使用的操作有所不同。让我们来看看。

什么是幺半群 (What are monoids)
===

幺半群比范畴简单得多。幺半群由一组元素 (称为幺半群的*基础集合* (underlying set)) 和一个*幺半群操作* (monoid operation) 定义——这是一个组合两个元素并产生同类第三个元素的规则。

让我们用我们熟悉的彩色球来说明。

![Balls](../03_monoid/balls.svg)

我们可以通过定义一个“组合”两个球为一个的操作来基于这个集合定义一个幺半群。例如，这样的操作可以是将球的颜色混合，就像混合颜料一样。

![An operation for combining balls](../03_monoid/balls_operation.svg)

你可能会想到定义类似操作的其他方法。这将帮助你意识到，可以从给定的元素集合中创建许多种不同的幺半群，也就是说，幺半群不仅仅是集合，它是集合*与操作的结合*。

结合律 (Associativity)
---

幺半群的操作应该像函数组合一样具有*结合性* (associative)，即以不同顺序应用它对相同数量的元素不应产生不同的结果。

![Associativity in the color mixing operation](../03_monoid/balls_associativity.svg)

当一个操作具有结合性时，这意味着我们可以对任何序列的项应用各种代数操作（或者换句话说，应用等式推理），例如我们可以用它由多个元素组成的集合替换任何一个元素，或者添加一个在等式两边都存在的项，并保持现有项的相等性。

![Associativity in the color mixing operation](../03_monoid/balls_arithmetic.svg)

单位元 (The identity element)
---

实际上，并非任何（结合的）组合元素的操作都能使球组成一个幺半群（它们可能组成*半群* (semigroup)，这也是一个主题，但我们暂且不谈）。要构成幺半群，一个集合必须有一个给定操作的*单位元* (identity element)，这是你在集合论和范畴论中已经熟悉的概念——它是与任何其他元素组合时，返回该元素的元素（不是单位元，而是另一个元素）。简单来说，$x • i = x$ 和 $i • x = x$ 对于任何 $x$ 都成立。

在我们的颜色混合幺半群中，白球（或者如果有的话，透明球）就是单位元。

![The identity element of the color-mixing monoid](../03_monoid/balls_identity.svg)

正如你可能还记得的，上章中函数组合也是结合的，并且也有一个单位元，所以你可能开始怀疑它以某种方式也构成了一个幺半群。确实如此，但这里有一个需要我们稍后讨论的细节。

基础幺半群 (Basic monoids)
===

为了保留悬念，在讨论幺半群与范畴之间的关系之前，我们先来看看一些简单的幺半群示例。

从数构成的幺半群 (Monoids from numbers)
---

数学不仅仅与数字有关，但数字确实会在大多数数学领域中出现，幺半群也不例外。当自然数集 $\mathbb{N}$ 与我们熟悉的加法操作组合时，它构成了一个幺半群（传统上称为“在加法下” (under addition)）。这个幺半群记作 $\left< \mathbb{N},+ \right>$ （通常，所有群体都用角括号括起集合和操作来表示）。

![The monoid of numbers under addition](../03_monoid/numbers_addition.svg)

如果你在课本中看到“$1 + 1 = 2$”，你要么在阅读非常高级的内容，要么在阅读非常简单的内容，不过我不太确定这里到底属于哪种情况。

无论如何，自然数在乘法下也构成了一个幺半群。

![The monoid of numbers under multiplication](../03_monoid/numbers_multiplication.svg)

**问题 (Question):** 这些幺半群的单位元是什么？

**任务 (Task):** 研究其他数学运算，并验证它们是否为幺半群。

布尔代数中的幺半群 (Monoids from boolean algebra)
---

思考我们所讨论的运算时，你可能会想起布尔运算中的*与* ($\land$) 和*或* ($\lor$)。这两者都形成幺半群，其作用于仅包含两个值的集合 $\{ True, False \}$。

**任务 (Task):** 通过展开公式 $(A \land B) \land C = A \land (B \land C)$ 的所有可能值，证明 $\land$ 是结合的。同样对*或*运算进行验证。

**问题 (Question):** “与”和“或”运算的单位元是什么？

幺半群运算的集合论定义 (Monoid operations in terms of set theory)
===

现在我们已经知道了什么是幺半群运算，甚至还看到了几个简单的例子。然而，我们还没有正式地定义幺半群规则/运算，即使用我们为其他内容定义时所用的集合论语言。我们能做到这一点吗？当然可以——一切都可以用集合来定义。

我们说过，幺半群由两个东西组成：一个集合（我们称之为 $A$）和作用于该集合的幺半群操作。由于 $A$ 已经在集合论中定义（因为它只是一个集合），我们只需定义幺半群操作。

定义这个操作并不难。实际上，我们已经为加法操作 $+$ 做过类似的定义——在第2章中，我们说过“加法”可以用集合论表示为一个接受两个数的乘积并返回一个数的函数（形式上为 $+: \mathbb{Z} \times \mathbb{Z} \to \mathbb{Z}$）。

![The plus operation as a function](../03_monoid/plus_operation.svg)

其他任何幺半群操作也可以以相同的方式表示——作为一个函数，该函数从幺半群的集合中取一对元素并返回另一个幺半群元素。

![The color-mixing operation as a function](../03_monoid/color_mixing_operation.svg)

形式上，我们可以从任何集合 $A$ 定义一个幺半群，通过定义一个具有类型签名 $A \times A \to A$ 的（结合的）函数。就是这样。准确来说，这是定义幺半群操作的*一种方法*。还有另一种方法，我们将在接下来看到。在那之前，让我们再研究一些范畴。

类似幺半群的其他对象 (Other monoid-like objects)
===

幺半群运算遵守两条定律——它们是*结合的* (associative)，并且存在一个*单位元* (identity element)。在某些情况下，我们会遇到一些遵循其他定律的运算，这些定律也同样有趣。向结合元素的方式施加更多（或更少）的规则，会导致定义类似幺半群的结构。

交换幺半群 (Commutative (abelian) monoids)
---

查看幺半群定律和我们给出的示例时，我们会发现所有这些例子都遵循一个我们没有明确说明的规则——应用操作的顺序对最终结果没有影响。

![Commutative monoid operation](../03_monoid/monoid_commutative.svg)

这样的操作（对任何给定的元素集合进行组合，无论先应用哪一个，结果都是相同的）称为*交换的* (commutative) 操作。具有交换操作的幺半群称为*交换幺半群* (commutative monoids)。

正如我们所说，加法是交换的——无论我是先给你1个苹果然后再给你2个，还是先给你2个再给你1个，结果都是相同的。

![Commutative monoid operation](../03_monoid/addition_commutative.svg)

到目前为止，我们研究的所有幺半群都是*交换的*。稍后我们会看到一些非交换的例子。

群 (Groups)
---

群是这样一种幺半群，其中对于每个元素，都存在一个所谓的“逆元” (inverse element)，当两个相继应用时，它们会相互抵消。用平白的语言定义这些概念让你更能理解数学公式的优势——形式上我们说，对于所有元素 $x$，必须存在 $x'$ 使得 $x • x' = i$ （其中 $i$ 是单位元）。

如果我们将*幺半群*视为建模一组（结合的）动作效果的手段，我们则使用*群*来建模这些动作也是*可逆的*。

我们讨论过的一个既是幺半群又是群的例子是自然数集在加法下的集合。每个数的逆元是其相反数（正数的逆元是负数，反之亦然）。上面的公式变成 $x + (-x) = 0$。

群的研究是一个比幺半群理论大得多的领域（甚至可能比范畴论本身还大）。其中一个最大的分支是“对称群” (symmetry groups) 的研究，我们将在接下来讨论。

总结 (Summary)
---

但是在此之前，先做一个简单的总结——这些代数结构可以根据定义它们的定律汇总在以下表格中。

| | 半群 (Semigroups) | 幺半群 (Monoids) | 群 (Groups) |
|---| ---             | ---        |
|结合律 (Associativity)| X | X | X |
|单位元 (Identity)| | X | X |
|可逆性 (Invertibility) | |  | X |

现在，让我们来看一下对称群 (symmetry groups)。

对称群及群分类 (Symmetry groups and group classifications)
===

几何图形的*对称性* (symmetries) 群是一类有趣的幺半群/群。给定一个几何图形，对称性指的是一种动作，执行这种动作后图形不会发生位移（例如，它可以完美地适应在应用动作之前所适应的模具）。

这次我们不会再使用球了，因为在对称性方面，球只有一个位置，因此只有一个动作——即恒等动作 (identity action)（顺便说一下，它是自己的逆元）。所以让我们使用这个三角形，就我们的目的而言，它和其他三角形没有区别（我们对三角形本身不感兴趣，而是对它的旋转感兴趣）。

![A triangle](../03_monoid/symmetry_group.svg)

旋转群 (Groups of rotations)
---

首先让我们回顾一下我们如何旋转三角形的方式的群，即它的*旋转群* (rotation group)。一个几何图形可以在不发生位移的情况下旋转的次数等于其边的数量，所以对于我们的三角形来说，有3个位置。

![The group of rotations in a triangle](../03_monoid/symmetry_rotation.svg)

将点（在这里是三角形）连接起来表明，从任何状态到另一个状态的可能旋转方式只有两种——*120度旋转* (120-degree rotation)（即翻转一次三角形）和*240度旋转* (240-degree rotation)（即翻转两次，或者等价地，沿相反方向翻转一次）。加上零度旋转（恒等动作），总共有3种旋转方式（对象）。

![The group of rotations in a triangle](../03_monoid/symmetry_rotation_actions.svg)

三角形的旋转构成了一个幺半群——*旋转是对象*（零度旋转是单位元），幺半群的操作是将两个旋转组合成一个，这就是先执行第一个旋转再执行第二个旋转的操作。

**注意 (NB):** 再次强调，群中的元素是*旋转*，而不是三角形本身，实际上这个群与三角形无关，正如我们稍后将看到的那样。

循环群/幺半群 (Cyclic groups/monoids)
---

更复杂的几何图形的旋转群的图表起初看起来相当杂乱。

![The group of rotations in a more complex figure](../03_monoid/symmetry_rotation_square.svg)

但如果我们注意到以下几点，它会变得更容易理解：尽管我们的群有许多旋转，并且对于更多边的图形（如果我没记错的话，旋转的次数等于边数）有更多的旋转，*所有这些旋转都可以归结为单一旋转的反复应用*（例如，三角形的120度旋转和八边形的45度旋转）。让我们为这个旋转做个符号。

![The group of rotations in a triangle](../03_monoid/symmetry_rotation_cyclic.svg)

具有这样“主要”旋转的对称群，以及一般的幺半群和群，拥有一个对象，通过反复应用它可以生成所有其他对象，称为*循环群* (cyclic groups)。这样的旋转称为群的*生成元* (generator)。

所有的旋转群都是循环群。另一个循环群的例子是自然数集在加法下的集合。这里我们可以使用 $+1$ 或 $-1$ 作为生成元。

![The group of numbers under addition](../03_monoid/numbers_cyclic.svg)

等等，既然没有循环，为什么这是循环群呢？因为整数是*无限的*循环群。

基于数的一个有限循环群的例子是*模运算* (modular arithmetic) 下的自然数集（有时称为“时钟算术” (clock arithmetic)）。模运算基于一个数，称为模数 (modulus)（我们以 $12$ 为例）。在其中，每个数都映射到该数与模数相加后取余数的结果。

例如：$1 \pmod{12} = 1$ （因为 $1/12 = 0$ 余 $1$）$2 \pmod{12} = 2$，等等。

但是 $13 \pmod{12} = 1$ （因为 $13/12 = 1$ 余 $1$），$14 \pmod{12} = 2$，$15 \pmod{12} = 3$ 等等。

实际上，数“绕圈”形成一个与模数相同数量的元素的群。例如，模数为 $3$ 的模运算的群表示有3个元素。

![The group of numbers under addition](../03_monoid/numbers_modular.svg)

所有具有相同数量元素的循环群（或者它们是*相同阶* (same order) 的）是同构的（细心的读者可能注意到我们还没有定义什么是群同构 (group isomorphisms)，更加细心的读者可能已经对它有了一个概念）。

例如，三角形的旋转群与模 $3$ 加法下的自然数集同构。

![The group of numbers under addition](../03_monoid/symmetry_modular.svg)

所有的循环群都是*交换的* (commutative)（也称为“阿贝尔” (abelian) 群）。

**任务 (Task):** 证明除了 $Z_3$ 之外，没有其他具有3个对象的群。

有些阿贝尔群不是循环的，但正如我们将在下文中看到的，循环群和阿贝尔群的概念是密切相关的。

群同构 (Group isomorphisms)
---

我们已经提到过群同构，但没有定义它们。现在让我们定义——两个群之间的同构是它们各自元素集合之间的同构 ($f$)，使得对于任何 $a$ 和 $b$，我们有 $f(a \circ b) = f(a) \circ f(b)$。直观上，同构群的图表具有相同的结构。

![Group isomorphism between different representations of S3](../03_monoid/group_isomorphism.svg)

在范畴论中，群论中的同构群被认为是同一个群的实例。例如上图所示的群称为 $Z_3$。

有限群 (Finite groups)
---

与集合一样，群论中的同构概念允许我们识别常见的有限群。

最小的群就是仅有一个元素的平凡群 (trivial group) $Z_1$。

![The smallest group](../03_monoid/trivial_group.svg)

最小的非平凡群是 $Z_2$，它有两个元素。

![The smallest non-trivial group](../03_monoid/smallest_group.svg)

$Z_2$ 也被称为*布尔群* (boolean group)，因为它与 ${ True, False }$ 集在否定运算下同构。

像 $Z_3$ 一样，$Z_1$ 和 $Z_2$ 都是循环的。

群/幺半群的积 (Group/monoid products)
===

我们已经看到很多既是阿贝尔群也是循环群的例子，但我们还没有看到任何非循环的阿贝尔群。那么让我们看看它们的样子。这次，我们不再看单个例子，而是展示一种通过*群积* (group product) 将循环群组合成非循环阿贝尔群的一般方法。

给定任意两个群，我们可以将它们组合成第三个群，该群由两个群的所有可能元素对组成，并包含它们所有操作的和。

让我们看看积的样子。取以下两个群（由于它们只有两个元素和一个操作，它们都与 $Z2$ 同构）。为了更容易想象它们，我们可以将第一个群看作基于图形的垂直反射，而第二个群则是水平反射。

![Two trivial groups](../03_monoid/groups_product.svg)

通过取第一个群的元素集合与第二个群的元素集合的*笛卡尔积* (Cartesian product)，我们得到了新群的元素集合。

![Two trivial groups](../03_monoid/groups_product_four.svg)

而积群的*操作*由第一个群的操作与第二个群的操作组成，其中每个操作只作用于属于其对应群的元素，而另一个元素保持不变。

![Klein four](../03_monoid/klein_four_as_product.svg)

我们展示的两个群的积称为*克莱因四元群* (Klein four-group)，它是最简单的*非循环阿贝尔* (non-cyclic abelian) 群。

克莱因四元群的另一种表示方式是*非正方形矩形的对称群*。

![Klein four](../03_monoid/klein_four.svg)

**任务 (Task):** 证明这两种表示是同构的。

克莱因四元群是*非循环的*（因为它有两个生成元）——垂直旋转和水平旋转。然而，它仍然是*阿贝尔的*，因为操作顺序对最终结果没有影响。实际上，克莱因四元群是*最小的非循环群*。

循环积群 (Cyclic product groups)
---

当组成积的群的元素数量（即它们的*阶* (orders)）不是*互质* (relatively prime) 时，积群是*非循环的*。

如果两个群的阶不是互质的（例如 $2$ 和 $2$，它们都能被2整除，就像构成克莱因四元群的群一样），那么即使这两个群都是循环的，并且每个群只有一个生成元，它们的积也会有两个生成元。

如果你将两个阶是互质的群组合在一起（例如 $2$ 和 $3$），所得群将与同阶的循环群同构，因为 $Z_3$ 与 $Z_2$ 的积与 $Z_6$ 群同构 ($Z_3 \times Z_2 \cong Z_6$)。

![Chinese reminder theorem](../03_monoid/chinese_remainder_theorem.svg)

这是一个古老结果的推论，称为*中国剩余定理* (Chinese Remainder theorem)。

阿贝尔积群 (Abelian product groups)
---

当组成积的*群是阿贝尔的*时，积群也是*阿贝尔的*。我们可以通过注意到，虽然生成元不止一个，但每个生成元只作用于它自己群的部分，因此它们之间不会相互干扰，从而看到这一点。

有限阿贝尔群基本定理 (Fundamental theorem of Finite Abelian groups)
---

积提供了一种从循环群创建非循环阿贝尔群的方法——通过将两个或多个循环群相乘。有限阿贝尔群基本定理是一个结果，告诉我们*这是生成非循环阿贝尔群的唯一方法*，即

> 所有阿贝尔群要么是循环的，要么是循环群的积。

我们可以利用这一定律来直观理解阿贝尔群的本质，也可以用它来检验某个给定的群是否可以分解为更多基本群的积。

{% if site.distribution == 'print' %}

颜色混合幺半群作为积 (Color-mixing monoid as a product)
---

为了看看我们如何使用这个定理，让我们重温一下之前看到的颜色混合幺半群。

![color-mixing group](../03_monoid/balls_rule.svg)

由于不存在一个可以通过与自身混合生成所有其他颜色的颜色，颜色混合幺半群是*非循环的*。然而，颜色混合幺半群*是阿贝尔的*。因此，根据有限阿贝尔群定理（该定理对幺半群同样适用），颜色混合幺半群必须（同构于）一个积。

而且，找到组成它的幺半群并不难——虽然没有一种颜色可以生成所有其他颜色，但有三种颜色可以做到——即三原色。这一观察使我们得出结论，颜色混合幺半群可以表示为三个幺半群的积，对应于三种原色。

![color-mixing group as a product](../03_monoid/color_mixing_product.svg)

你可以将每个颜色幺半群视为一个布尔幺半群，只有两种状态（有颜色和无颜色）。

![Cyclic groups, forming the color-mixing group](../03_monoid/color_mixing_cyclic.svg)

或者，替代地，你可以将其视为具有多个状态，表示不同的着色层次。

![Color-shading cyclic group](../03_monoid/cyclic_shading.svg)

在这两种情况下，幺半群都是循环的。

{%endif%}

二面体群 (Dihedral groups)
===

现在，我们终于要研究一个非交换群 (non-commutative group)——一个几何图形的*旋转和反射* (rotations and reflections) 的群。与上一个群类似，但这里除了我们已经看到的旋转操作（及其复合操作）之外，还有一个操作是垂直翻转图形，这个操作会使图形变为其镜像：

![Reflection of a triangle](../03_monoid/reflection.svg)

这两个操作及其复合结果形成一个称为 $Dih3$ 的群，它是非阿贝尔的（而且是*最小的*非阿贝尔群）。

![The group of rotations and reflections in a triangle](../03_monoid/symmetry_reflection.svg)

**任务 (Task):** 证明该群确实是非阿贝尔的。

**问题 (Question):** 除了有两个主要操作外，是什么决定了该群及其他任何群为非阿贝尔的？

表示任何二维形状的旋转和反射集的群称为*二面体群* (dihedral groups)。

<!--
TODO: FSM as monoids
https://faculty.uml.edu/klevasseur/ads/s-monoid-of-fsm.html
-->


幺半群/群的范畴化视角 (Groups/monoids categorically)
===

我们首先定义了幺半群 (monoid) 为一组可组合的*元素*。然后我们看到对于某些群 (groups)，如对称群 (groups of symmetries) 和旋转群 (rotations)，这些元素可以视为*动作*。事实上，这对于其他所有群也同样适用。例如，我们颜色混合幺半群 (color-blending monoid) 中的*红球*可以看作是*将红色加入混合物*的动作，数字 $2$ 在加法幺半群中可以看作是操作 $+2$ 等等。这一观察引出了幺半群和群的范畴化视角。

柯里化 (Currying)
---

当我们定义幺半群时，看到它们的操作是双参数函数。我们使用集合论 (set theory) 引入了一种表示这些函数的方法——通过使用积将两个参数合并。也就是说，我们展示了一个接受两个参数的函数（比如 $A$ 和 $B$）并将它们映射到某个结果（$C$），可以视为从这两个参数集合的积映射到结果。所以 $A\times B\to C$。

然而，这并不是集合论表示多参数函数的唯一方式——还有另一种同样有趣的方式，它不依赖于任何数据结构，而只依赖于函数：这种方式是有一个函数，它将第一个参数（即 $A$）映射到*另一个函数*，该函数将第二个参数映射到最终结果（即 $B \to C$）。所以 $A\to B \to C$。

将一个接受一对对象的函数转换为一个接受一个对象并返回一个接受另一个对象的函数的过程称为*柯里化* (currying)。它通过高阶函数来实现。下面是这种函数的实现方式。

```
const curry = <A, B, C> (f:(a:A, b:B) => C) => (a:A) => (b:B) => f(a, b)
```

同样重要的是反向函数，它将柯里化的函数映射为多参数函数，称为*反柯里化* (uncurry)。

```
const uncurry = <A, B, C> (f:(a:A) => (b:B) => C) => (a:A, b:B ) => f(a)(b)
```

关于这两个函数还有很多可以说的，首先是它们的存在引发了范畴论中*积* (product) 和*态射* (morphism) 概念之间的一种有趣关系，称为*伴随* (adjunction)。但我们将在后面讨论这一点。目前，我们关心的是这两种函数表示是同构的，形式上为 $A\times B\to C\cong A\to B \to C$。

顺便说一下，这种同构也可以用编程来表示。它等价于以下函数对于任何参数总是返回 `true` 的声明：

```
(...args) => uncurry(curry(f(...args)) === f(...args)
```

这是同构的一部分，另一部分是柯里化函数的等价函数。

**任务 (Task):** 编写同构的另一部分。

幺半群元素作为函数/置换 (Monoid elements as functions/permutations)
---

让我们回头看看我们到目前为止讨论的幺半群/群，结合我们学到的知识。我们一开始将群操作表示为一个对的函数。例如，对称群的操作（以 $Z_3$ 为例）是将两个旋转转换为另一个旋转的动作。

![The group of rotations in a triangle - group notation](../03_monoid/symmetry_rotation_actions.svg)

通过柯里化，我们可以将一个给定群/幺半群的元素表示为函数，并将群操作本身表示为函数的组合。例如，$Z_3$ 的三个元素可以看作是从一个包含三个元素的集合到自身的三个双射函数（在群论背景下，这种函数称为*置换* (permutations)）。

![The group of rotations in a triangle - set notation](../03_monoid/symmetry_rotation_functions.svg)

我们也可以对加法幺半群进行同样的操作——数字可以不被视为*数量*（例如两个苹果、两个橙子等），而是*操作*（例如作为将一个给定数量加上2的动作）。

形式上，加法幺半群的操作可以有如下类型签名：

$+: \mathbb{Z} \times \mathbb{Z} \to \mathbb{Z}$

由于我们上面展示的同构关系，这个函数等价于如下函数：

$+: \mathbb{Z} \to (\mathbb{Z} \to \mathbb{Z})$

当我们将幺半群的一个元素（例如 $2$）应用于该函数时，结果是将 2 加到一个给定数上的函数 $+2$。

$+2: \mathbb{Z} \to \mathbb{Z}$

由于幺半群操作在上下文中是给定的，因此我们可以将元素 $2$ 和函数 $+2$ 在幺半群的上下文中视为等价。

$2 \cong +2$

换句话说，除了将幺半群的元素表示为*对象*，我们也可以将它们表示为*函数*。

幺半群操作作为函数组合 (Monoid operations as functional composition)
---

表示幺半群元素的函数具有相同的源和目标，或者如我们所说的相同的类型签名（形式上，它们属于类型 $A \to A$，其中 $A$ 为某个集合）。因此，它们可以通过*函数组合* (functional composition) 相互组合，生成*同样类型签名*的函数。

![The group of rotations in a triangle - set notation](../03_monoid/symmetry_rotation_cayley.svg)

同样，这也适用于加法幺半群——数字函数可以通过函数组合进行组合。

$+2 \circ +3 \cong +5$

因此，表示幺半群元素的函数也构成了一个幺半群，在函数组合操作下（表示群元素的函数在函数组合下也构成了一个群）。

**问题 (Question):** 哪些是函数群的单位元？

**任务 (Task):** 证明表示逆群元素的函数也是逆函数。

凯莱定理 (Cayley's theorem)
---

一旦我们学会如何通过柯里化将任何幺半群的元素表示为置换，它们也形成了一个幺半群，这样就不奇怪了，这个构造的置换幺半群与原始幺半群同构（即从其构造的幺半群——这是一个称为凯莱定理的结果：

> 任何群都同构于一个置换群。

形式上，如果我们用 $Perm$ 表示置换群，则对于任何集合 $A$，有 $Perm(A) \cong A$。

![The group of rotations in a triangle --- set notation and normal notation](../03_monoid/symmetry_rotation_comparison.svg)

换句话说，将一个群的元素表示为置换实际上产生了该幺半群的一个表示（有时称为其*标准表示* (standard representation)）。

凯莱定理也许看起来并不那么令人印象深刻，但这恰恰说明了它作为一个结果有多么具有影响力。

{% if site.distribution == 'print' %}

插曲：对称群 (Symmetric groups)
---

首先需要知道的是，对称群*不等同于*对称性群体 (symmetry groups)。当我们明确了这一点后，我们可以理解它们实际是什么：给定一个自然数 $n$，$n$ 的对称群，记作 $\mathrm{S}_n$（$n$ 度的对称群），是一个集合所有可能的置换组成的群。这样的群的元素数等于 $1\times 2\times 3...\times n$ 或 $n!$（即 $n$ 的阶乘）。

例如，$\mathrm{S}_1$ 表示一元素集的置换群只有一个元素（因为一元素集除了恒等函数之外没有其他函数）。

![The S1 symmetric group](../03_monoid/s1.svg)

$\mathrm{S}_2$ 有 $1 \times 2 = 2$ 个元素（顺便说一下，颜色用于直观表示为什么 $n$ 元素集的置换数为 $n!$）。

![The S2 symmetric group](../03_monoid/s2.svg)

到了 $\mathrm{S}_3$，我们已经感受到了指数增长（甚至比指数增长更快！）的力量——它有 $1\times 2\times 3=6$ 个元素。

![The S3 symmetric group](../03_monoid/s3.svg)

每个对

称群 $\mathrm{S}_n$ 都包含所有 $n$ 阶的群——这是因为（如我们在上一节所见）每个具有 $n$ 个元素的群都同构于 $n$ 元素集上的一个置换集，而 $\mathrm{S}_n$ 包含了*所有此类*存在的置换。

以下是一些例子：
- $\mathrm{S}_1$ 同构于 $Z_1$，即*平凡群* (trivial group)，而 $\mathrm{S}_2$ 同构于 $Z_2$，即*布尔群* (boolean group)（但其他对称群不与循环群同构）。
- $\mathrm{S}_3$ 的前三个置换同构于 $Z_3$。

![The S3 symmetric group](../03_monoid/s3_z3.svg)

- $\mathrm{S}_3$ 也同构于 $Dih3$（但其他对称群不与二面体群同构）。

基于这一见解，我们可以这样表述凯莱定理：

> 所有群都同构于对称群的子群。

**任务 (Task):** 证明两者是如何等价的。

有趣的事实：群论研究实际上始于对称群的研究，因此该定理实际上是我们现在所知并热爱的群的标准定义出现的先决条件（好吧，至少*我*喜欢它）——它提供了证明，该定义所描述的概念与对称群已有的概念是等价的。

{% endif %}

幺半群作为范畴 (Monoids as categories)
---

我们看到，将幺半群的元素转换为动作/函数，可以在集合和函数的上下文中准确地表示幺半群。

![The group of rotations in a triangle - set notation and normal notation](../03_monoid/symmetry_rotation_set.svg)

然而，似乎这种表示中的集合部分有点多余——你到处都有相同的集合——所以，如果我们能简化它，那就好了。而我们可以通过将其描绘为一个外部（范畴的）图来做到这一点。

![The group of rotations in a triangle - categorical notation](../03_monoid/symmetry_rotation_external.svg)

但是等一下，如果幺半群的*集合*对应于范畴论中的*对象*，那么对应的范畴将只有一个对象。因此，正确的表示将仅涉及一个点，从中发出的箭头和回到该点的箭头。

![The group of rotations in a triangle - categorical notation](../03_monoid/symmetry_rotation_category.svg)

不同幺半群之间的唯一区别是它们拥有的态射数量及其之间的关系。

从范畴论的角度看，这种表示的直觉由幺半群和群的*封闭性* (closure) 定律所体现，而范畴没有该定律——它规定无论如何组合两个对象，结果总是相同的对象。例如，不管你如何旋转一个三角形，你仍然得到一个三角形。

| | 范畴 (Categories) | 幺半群 (Monoids) | 群 (Groups)
|---| ---             | ---        |
|结合性 (Associativity)| X | X | X |
|单位元 (Identity)| X | X | X |
|可逆性 (Invertibility) | |  | X |
|封闭性 (Closure)  | | X | X |

当我们将幺半群视为范畴时，这条定律表明该范畴中的所有态射都应该来自同一个对象并指向同一个对象——一个幺半群，无论是什么幺半群，都可以看作是*具有一个对象的范畴*。反之亦然：任何具有一个对象的范畴都可以看作是一个幺半群。

让我们通过回顾第2章中的范畴定义来详细说明这一想法。

> 范畴是*对象*（我们可以将其视为点）和*态射*（箭头）的集合，态射从一个对象指向另一个对象，其中：
> 1. 每个对象必须有一个恒等态射。
> 2. 必须有一种方法将两个具有适当类型签名的态射组合成一个第三个态射，并且这种组合是结合的。

除了*幺半群的对象在范畴中是态射*这一有些令人困惑的事实外，这正是幺半群的描述。

范畴对于每个对象都有一个恒等态射，因此对于只有一个对象的范畴，也应该有一个唯一的恒等态射。而幺半群确实有一个恒等对象，从范畴论的角度来看，它对应于那个恒等态射。

范畴提供了一种将两个具有适当类型签名的态射组合在一起的方法，对于只有一个对象的范畴，这意味着*所有态射都应该可以组合*。而幺半群操作正是这样做的——给定任意两个对象（或者说，两个态射，如果我们使用范畴术语），它会生成第三个态射。

哲学上，将幺半群定义为一个单对象范畴意味着它对应于这样一种观点，即幺半群是对一组（结合的）动作如何在给定对象上执行并改变其状态的建模。假设对象的状态仅由执行的动作决定，我们可以将其排除在外，专注于动作如何组合。通常情况下，这些动作（和元素）可以是任何东西，从混合颜色、给定数量的事物增加等。

群/幺半群的表示 (Group/monoid presentations)
---

当我们将循环群/幺半群视为范畴时，我们会看到它们对应于具有*一个对象*和*一个态射*（如我们所说的*生成元*）的范畴，以及生成元与其自身组合时生成的态射。事实上，无限循环幺半群（同构于自然数），可以通过这个简单定义完全描述。

![Presentation of an infinite cyclic monoid](../03_monoid/infinite_cyclic_presentation.svg)

这是因为生成元一次又一次的应用会产生无限循环群的所有元素。具体来说，如果我们将生成元视为操作 $+1$，则我们得到自然数。

![Presentation of an infinite cyclic monoid](../03_monoid/infinite_cyclic_presentation_elements.svg)

有限循环群/幺半群也是如此，只是它们的定义包含一条附加规则，规定一旦你将生成元与其自身组合了 $n$ 次，就会得到恒等态射。对于循环群 $Z_3$（可以看作是三角形旋转群），该规则规定生成元与其自身组合三次后得到恒等态射。

![Presentation of a finite cyclic monoid](../03_monoid/finite_cyclic_presentation.svg)

将群生成元与其自身组合，然后应用该规则，得到 $Z_3$ 的三个态射。

![Presentation of a finite cyclic monoid](../03_monoid/finite_cyclic_presentation_elements.svg)

我们也可以用这种方式表示积群。让我们以克莱因四元群为例，克莱因四元群有两个生成元，它继承自组成它的群（我们视为非正方形矩形的垂直和水平旋转），每个生成元都有一个规则。

![Presentation of Klein four](../03_monoid/klein_four_presentation.svg)

为了使表示完整，我们添加了组合这两个生成元的规则。

![Presentation of Klein four - third law](../03_monoid/klein_four_presentation_third_law.svg)

然后，如果我们开始应用这两个生成元并遵循这些规则，我们就得到了四个元素。

![The elements of Klein four](../03_monoid/klein_four_presentation_elements.svg)

定义给定群的生成元和规则集合称为群的*表示* (presentation of a group)。每个群都有一个表示。

{% if site.distribution == 'print' %}

插曲：自由幺半群 (Free monoids)
---

我们看到，选择不同的规则集合会产生不同类型的幺半群。那么如果我们不选择任何规则呢？这些幺半群（我们根据选择的集合得到不同的幺半群）称为*自由幺半群* (free monoids)（“自由”一词在这里的意思是，一旦你有了集合，你可以“免费”将其升级为幺半群，即无需定义其他任何内容）。

如果你重温前一节，你会注意到我们已经看到过一个这样的幺半群。具有一个生成元的自由幺半群与整数幺半群同构。

![The free monoid with one generator](../03_monoid/infinite_cyclic_presentation_elements.svg)

我们可以从一组彩色球中构造一个自由幺半群——该幺半群的元素将是所有可能的球的组合序列。

![The free monoid with the set of balls as a generators](../03_monoid/balls_free.svg)

自由

幺半群是特殊的——在给定集合上的自由幺半群的每个元素都可以通过应用幺半群的规则，转换为任何其他使用相同生成元的幺半群的相应元素。例如，如果我们将上述元素应用于颜色混合幺半群的规则，得到如下结果。

![Converting the elements of the free monoid to the elements of the color-mixing monoid](../03_monoid/balls_free_color_mixing.svg)

**任务 (Task):** 写出颜色混合幺半群的规则。

如果我们戴上程序员的帽子，会发现集合 $T$ 上的自由幺半群类型（我们可以记作 `FreeMonoid<T>`）与类型 `List<T>`（如果你更喜欢的话，可以用 `Array<T>`）是同构的，并且我们上面描述的特殊性质的直觉实际上非常简单：将对象保存在列表中可以让你将它们转换为任何其他结构，即当我们想要对一堆对象进行某些操作，但我们不知道具体是什么操作时，我们只是将这些对象保存在列表中，直到执行操作的时机到来。

虽然自由幺半群的直觉似乎足够简单，但它的正式定义目前还不是我们可以处理的内容... 因为我们还需要覆盖更多内容。

我们知道，作为给定生成集合中最一般的幺半群，自由幺半群可以转换为所有其他幺半群。即存在一个函数将自由幺半群映射到其他幺半群。但这个函数是什么呢？请继续关注接下来的章节。

{%endif%}
