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

What are functors
===

The logician Rudolf Carnap coined the term "functor" as part of his project to formalize the syntax for the natural languages such as English in order to create a precise way for us to talk about science. Originally, a functor meant a word or phrase whose meaning can be customized by combining it with numerical value, such as the phrase "the temperature at $x$ o'clock", which has a different meaning depending on the value of $x$.

In other words, a functor is a phrase that *acts as a function*, only not a function between sets, but one between *linguistic concepts* (such as times and temperature).

![Functor, as envisioned by Rudolf Carnap.](../10_functors/functor_carnap.svg)

Later, one of the inventors of category theory Sanders Mac Lane borrowed the word, to describe a something that *acts as function between categories*, which he defined in the following way:

> A functor between two categories (let's call them $A$ and $B$) consists of two mappings --- a mapping that maps each *object* in $A$ to an object in $B$ and a mapping that maps each *morphism* between any objects in $A$ to a morphism between objects in $B$, in a way that *preserves the structure* of the category. 

![Functor](../10_functors/functor.svg)

Now let's unpack this definition by going through each of its components.

Object mapping
---

In the definition above, we use the word "mapping" to avoid misusing the word "function" for something that isn't exactly a function. But in this particular case, calling the mapping a function would barely be a misuse --- if we forget about morphisms and treat the source and target categories as sets, the object mapping is nothing but a regular old function.

![Functor for objects](../10_functors/functor_objects.svg)

A more formal definition of object mapping involves the concept of an *underlying set* of a category: Given a category $A$, the underlying set of $A$ is a set that has the objects of $A$ as elements. Utilizing this concept, we say that the object mapping of a functor between two categories is *a function between their underlying sets*. The definition of a function is still the same:

> A function is a relationship between two sets that matches each element of one set, called the *source set* of the function, with exactly one element from another set, called the *target set* of the function. 

Morphism mapping
---

The second mapping that forms the functor is a mapping between the categories' morphisms. This mapping resembles a function as well, but with the added requirement that each morphism in $A$ a given source and target must be mapped to a morphism with the corresponding source and target in $B$, as per the object mapping.

![Functor for morphisms](../10_functors/functor_morphisms.svg)

A more formal definition of a morphism mapping involves the concept of the *homomorphism set*: this is a set that contains all morphisms that go between given two objects in a given category. When utilizing this concept, we say that a mapping between the morphisms of two categories consists of a *set of functions between their respective homomorphism sets*.

![Functor for morphisms](../10_functors/functor_morphisms_formal.svg)

(Notice how the concepts of *homomorphism set* and of *underlying set* allowed us to "escape" to set theory when defining categorical concepts and define everything using functions.)

Functor laws
---

So these are the two mappings (one between objects and one between morphisms) that constitute a functor. But not every pair of such two mappings is a functor. As we said, in addition to existing, the mappings should *preserve the structure* of the source category into the target category. To see what that means, we revisit the definition of a category from chapter 2:

> A category is a collection of *objects* (we can think of them as points) and *morphisms* (arrows) that go from one object to another, where:
> 1. Each object has to have the identity morphism.
> 2. There should be a way to compose two morphisms with an appropriate type signature into a third one, in a way that is associative.

So this definition translates to the following two *functor laws*

1. Functions between morphisms should *preserve identities* i.e. all identity morphisms should be mapped to other identity morphisms.
 ![Functor](../10_functors/functor_laws_identity.svg)

2. Functors should also *preserve composition* i.e. for any two morphisms $f$ and $g$, the morphism that corresponds to their composition $F(g•f)$ in the source category should be mapped to the morphism that corresponds to the composition of their counterparts in the target directory, so $F(g•f) = F(g)•F(f)$.

 ![Functor](../10_functors/functor_laws_composition.svg)

And these laws conclude the definition of functors --- a simple but, as we will see shortly, very powerful concept. 

To see *why* is it so powerful, let's check some examples. 

Functors in everyday language
---

There is a common figure of speech (which is used  all the time in this book) which goes like this: 

> If $a$ is like $F a$, then $b$ is like $F b$.

Or "$a$ is related to $F a$, in the same way as $b$ is related to $F b$," e.g. "If schools are like corporations, then teachers are like bosses". 

This figure of speech is nothing but a way to describe a functor in our day-to-day language: what we mean by it is that there is a certain connection (or category-theory therms a "morphism") between schools and teachers, that is similar to the connection between corporations and bosses i.e. that there is some kind of structure-preserving map that connects the category of school-related things, to the category of work-related things which maps schools ($a$) to corporations ($F a$) and teacher ($b$) to bosses ($F b$), and which is such that the connections between schools and teachers ($a \to b$) are mapped to the connections between corporations and bosses ($F a \to F b$).

Diagrams are functors
---

> “A sign is something by knowing which we know something more.” — Charles Sanders Peirce

We will start with an example of a functor that is very *meta* --- the diagrams/illustrations in this book.

You might have noticed that diagrams play a special role in category theory --- while in other disciplines their function is merely complementary i.e. they only show what is already defined in another way, here *the diagrams themselves serve as definitions*. 

For example, in chapter 1 we presented the following definition of functional composition.

> The composition of two functions $f$ and $g$ is a third function $h$ defined in such a way that this diagram commutes.

![Functional composition - general definition](../10_functors/functions_compose_general.svg)

We all see the benefit of defining stuff by means of diagrams as opposed to writing lengthy definitions like

> "Suppose you have three objects $a$, $b$ and $c$ and two morphisms $f: b \to c$ and $g: a \to b$..."

However, it (defining stuff by means of diagrams) presents a problem --- definitions in mathematics are supposed to be formal, so if we want to use diagrams as definitions we must first *formalize the definition of a diagram itself*. 

So how can we do that? One key observation is that diagrams look as finite categories, as, for example, the above definition looks in the same way as the category $3$.

![the finite category 3](../10_functors/finite_three.svg)

However, this is only part of the story as finite categories are just structures, whereas diagrams are *signs*. They are "something by knowing which we know something more.", as Peirce famously put it (or "...which can be used in order to tell a lie", in the words of Umberto Eco). 

For this reason, aside from a finite category that encodes the diagram's structure, the definition of a diagram must also include a way for "interpreting" this category in some other context i.e. they must include *functors*.

![diagram as a functor](../10_functors/diagram_functor.svg)

This is how the concept of functors allows us to formalize the notion of diagrams: 

> A *diagram* is comprised of one finite category (called an *index category*) and a functor from it to some other category.

If you know about semiotics, you may view the source and target categories of the functor as *signifier* and *signified*.

And so, you can already see that the concept of a functor plays a very important role in category theory. Because of it, diagrams in category theory can be *specified formally* i.e. they are categorical objects *per se*. 

You might even say that they are categorical objects *par excellence* (TODO: remove that last joke).

<!--
(TODO: By the way, the fact that a diagram commutes means just that the morphism in the finite category are sometimes composites of one another).
-->

Maps are functors
---

> A map is not the territory it represents, but, if correct, it has a similar structure to the territory, which accounts for its usefulness. Alfred Korzybski

Functors are sometimes called "maps" for a good reason --- maps, like all other diagrams, are functors. If we consider some space, containing cities and roads that we travel by, as a category, in which the cities are objects and roads between them are morphisms, then a road map can be viewed as category that represent some region of that space, together with a functor that maps the objects in the map to real-world objects.

![A map and a preorder of city pathways](../10_functors/preorder_map_functor.svg)

In maps, morphisms that are a result of composition are often not displayed, but we use them all the time --- they are called *routes*. And the law of preserving composition tells us that every route that we create on a map corresponds to a real-world route. 

![A map and a preorder of city pathways](../10_functors/preorder_map_functor_route.svg)

Notice that in order to be a functor, a map does not have to list *all* roads that exist in real life, and *all* traveling options ("the map is not the territory"), the only requirement is that *the roads that it lists should be actual* --- this is a characteristic shared by all many-to-one relationships (i.e. functions).

<!--
Functors can also go from complex to simple
---

So far, we saw functors that go from a simple category, into a more complex one, which aim to *select* some objects from the target category*.

But functors can go the other way too --- from complex to simple --- those are the functors which *sort* the object of the source category into the categories that constitute the target.


Even more interestingly, we often encounter often special pairs of functors, consisting of one *selective* and one *sorting* functor that go between two categories, that kinda reverse each other. 

--> 

Human perception is functorial 
---

We saw that, aside from being a category-theoretic concept, functors are connected to many disciplines that study the human mind such as logic, linguistics, semiotics and the like. Why is it so? Recently, I wrote a [blog post about using logic to model real-life thinking](/logic-thought)) where I tackle the "unreasonable effectiveness" of functors (and "maps" in general), where I argue that human perception, human thinking, is functorial.

My thesis is that to perceive the world around us, we are going through a bunch of functors that go from more raw "low-level" mental models to more abstract "high-level" ones. 

We may say that perception starts with raw sensory data. From it, we go, (using a functor) to a category containing some basic model of how the world works (one that tells us where are we in space, how many objects are we seeing etc.). Then we are connecting this model to another, even more abstract model, which provides us with a higher-level view of the situation that we are in, and so on.

![Perception is functorial](../10_functors/chain.svg)

You can view this as a progression from simpler to more abstract from categories with less morphisms to categories with more morphisms --- we start with the category of pieces of sensory data that have no connections between one another, and proceed to another category where some of these pieces of data are connected. Then, we transfer this structure in another category with even more connections.

![Perception is functorial](../10_functors/logic_thought.svg)

All this is, of course, just a speculation, but we might convince yourself that there is some basis for it, especially after we see how significant functors are for the mathematical structures that we saw before.

Functors in monoids
===

So, after this slight detour, we will return to our usual modus operandi: 

Hey, do you know that in group theory, there is this cool thing called *group homomorphism* (or *monoid homomorphism* when we are talking about monoids) --- it is a function between the groups' underlying sets which preserves the group operation.

So, for example, If the time of the day right now is 00:00 o'clock (or 12 PM) then what would the time be after $n$ hours? The answer to this question can be expressed as a function with the set of integers as source and target.

![Group homomorphism as a function](../10_functors/group_homomorphism_function.svg)

This function is interesting --- it preserves the operation of (modular) addition: if, 13 hours from now the time will be 1 o'clock and if 14 hours from now it will be 2 o'clock, then the time after (13 + 14) hours will be (1 + 2) o'clock. 

![Group homomorphism](../10_functors/group_homomorphism.svg)

Or to put it formally, if we call it (the function) $F$, then we have the following equation: $F(a + b) = F(a) + F(b)$ (where $+$ in the right-hand side of the equation means modular addition). Because this equation holds, the $F$ function is a *group homomorphism* between the group of integers under addition and the group of modulo arithmetic with base 11 under modular addition (where you can replace 11 with any other number).


The groups don't have to be so similar for there to be a homomorphism between them. Take, for example, the function that maps any number $n$ to 2 to the *power of $n$,* so  $n \to 2ⁿ$ (here, again, you can replace 2 with any other number). This function gives a rise to a group homomorphism between the group of integers under addition and the integers under multiplication, or $F(a + b) = F(a) \times F(b)$.

![Group homomorphism between different groups](../10_functors/group_homomorphism_addition_multiplication.svg)

Wait, what were we talking about, again? Oh yeah --- group homomorphisms are functors. To see why, we switch to the category-theoretic representation of groups and revisit our first example and (to make the diagram simpler, we use $mod2$ instead of $mod11$).

![Group homomorphism as a functor](../10_functors/group_homomorphism_functor.svg)

It seems that when we view groups/monoid as one-object categories, a group/monoid homomorphism is just a functor between these categories. Let's see if that is the case.

Object mapping
---

Groups/monoids have just one object when viewed as categories, so there is also only one possible object mapping between any couple of groups/monoids --- one that maps the (one and only) object of the source group to the object of the target group (not depicted in the diagram).

Morphism mapping
---

Because of the above, the morphism mapping is the only relevant component of the group homomorphism. In the category-theoretic perspective, group objects (like $1$ and $2$ $3$ etc.) correspond to morphisms (like $+1$, $+2$ $+3$ etc.) and so the morphism mapping is just mapping between the group's objects, as we can see in the diagram.


Functor laws
---

The first functor law trivial, it just says that the one and only identity object of the source group (which corresponds to the identity morphism of its one and only object) should be mapped to the one and only identity object of the target group. 

And if we remember that the group operation of combining two objects corresponds to *functional composition* if we view groups as categories, we realize that the group homomorphism equation $F(a + b) = F(a) \times F(b)$ is just a formulation of the second functor law: $F(g•f) = F(g)•F(f)$.

And many algebraic operations satisfy this equation, for example the functor law for the group homomorphism between $n \to 2ⁿ$ is just the famous algebraic rule, stating that $gᵃ gᵇ= gᵃ⁺ᵇ$.

**Task:** Although it's trivial, we didn't prove that the first functor law (the one about the preservation of identities always holds. Interestingly enough, for groups/monoids it actually follows from the second law. Try to prove that. Start with the definition of the identity function.

Functors in orders
===

And now let's talk about a concept that is completely unrelated to functors, nudge-nudge (hey, bad jokes are better than no jokes at all, right?) In the theory of orders, we have the concept of functions between orders (which is unsurprising, given that orders, like monoids/groups, are based on sets) and one very interesting type of such function, which has applications in calculus and analysis, is a *monotonic function* (also called *monotone map*). This is a function between two orders that *preserves the order of the objects in the source order, in the target order. So a function $F$ is monotonic  when for every $a$ and $b$ in the source order, if $a ≤ b$ then $F(a) ≤ F(b)$.

For example, the function that maps the current time to the distance traveled by some object is monotonic because the distance traveled increases (or stays the same) as time increases.

![A monotonic function](../10_functors/monotone_map.svg)

If we plot this or any other monotonic function on a line graph, we see that it goes just one direction (i.e. just up or just down).

![A monotonic function, represented as a line-graph](../10_functors/monotone_map_plot.svg)

Now we are about to prove that monotonic functions are functors too, ready?

Object mapping
---

Like with categories, the object mapping of an order is represented by a function between the orders' underlying sets. 

Morphism mapping
---

With monoids, the object mapping component of functors was trivial. Here is the reverse: the morphism mapping is trivial - given a morphism between two objects from the source order, we map that morphism to the morphism between their corresponding objects in the target order. The fact that the monotonic function respects the order of the elements, ensures that the latter morphism exists.

Functor laws
---

It is not hard to see that monotone maps obey the first functor law as identities are the only morphisms that go between a given object and itself. 

And the second law ($F(g•f) = F(g)•F(f)$) also follows trivially: both morphisms $F(g•f)$ and $F(g)•F(f)$ have the same type signature. But because in orders there can be just one morphism with a given type signature, these two morphisms must be equal to one another.

**Task:** Expand the proof.

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
