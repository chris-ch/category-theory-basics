# category-theory-basics
A few notes about category theory

## Preliminary definitions

A __category__ is a collection of __arrows__ between __objects__. Arrows are also called __morphisms__.
When arrows between two objects form a set the category is said to be __locally small__.

There is no limit to the number of arrows between two objects _A_ and _B_.

Coinciding arrows are necessarily composed, so that if we have _φ: A → B_ and _ψ: B → C_ 
we also necessarily have a morphism denoted _(ψ ○ φ): A → C_

Composition is associative : _(ω ○ ψ) ○ φ = ω ○ (ψ ○ φ)_

For any object *A* there is always an __identity arrow__ *id<sub>A</sub>: A → A* such that *id<sub>A</sub>* 
composed with any other composable arrow _φ_ is equivalent to _φ_ itself:

_φ ○ id<sub>A</sub> = φ_

In the case of the category __Set__ objects are sets and morphisms are functions.

An __initial object__ has a unique arrow pointing to every other object. In the category __Set__ the initial object is the empty set, 
because there is only one function from the empty set to any other set, the empty function corresponding to the set containing no relation.

A __terminal object__ has a unique arrow coming from every other object. In the category __Set__ the terminal object is any singleton set.
All singleton sets being isomorphic to each other they are all equivalent from a categorical perspective.

In general in category theory identity is up to isomorphism. Whatever may be inside objects are out of reach.
We only look at the quantity of information, not the information itself.

A __functor__ puts two categories in correspondence.

_F: C<sub>1</sub> → C<sub>2</sub>_

It does so by mapping both objects and morphisms and respecting the structure provided by morphisms.

A __natural transformation__ puts two functors un correspondence

_μ: F<sub>1</sub> → F<sub>2</sub>_

for _F<sub>1</sub>: C<sub>1</sub> → C<sub>2</sub>_ and _F<sub>2</sub>: C<sub>1</sub> → C<sub>2</sub>_

It does so for every object A in _C<sub>1</sub>_, so we have one __component__ for each object A in _C<sub>1</sub>_:

_μ<sub>A</sub>: F<sub>1</sub>(A) → F<sub>2</sub>(A)_ 
is said to be the component of the natural transformation _μ_ at _A_.

## Some example of functors

### Graphs
A graph _G_ is a functor from a category _Γ_ to _Set_.

The category _Γ_ contains 2 objects _e_ and _v_ (for edges and vertices) 
with 2 arrows _s_ and _t_ (for source and target) both flowing from _e_ to _v_.

### The Powerset is an endofunctor in _Set_
For any two categories C1 and C2 there is a category denoted _[C<sub>1</sub>, C<sub>2</sub>]_ whose objects are functors _C<sub>1</sub> → C<sub>2</sub>_ 
and whose arrows are natural transformations.

The set of morphisms between two objects _A_ and _B_ in a category _C_ are denoted _C(A, B)_.

### Hom-functors
Given any locally small category _C_ we automatically get an additional category for free 
called __hom-functor__ and denoted __Hom<sub>A</sub>__:

_Hom<sub>A</sub>: C → Set_

Parametrized by an object _A_ it maps
  - each object _X_ to the set of morphisms _Hom<sub>A</sub>(X)_ also denoted _X<sup>A</sup>_
  - each morphism _f: X → Y_ to a function _Hom<sub>A</sub>(f): Hom<sub>A</sub>(X) → Hom<sub>A</sub>(Y)_
    
Such a _Hom<sub>A</sub>(f)_ function exists because given a morphism _φ: A → X_ in the source category which corresponds to 
a function in _Hom<sub>A</sub>(X)_ and a morphism _f: X → Y_ 
their composition _ψ = (f ○ φ): A → Y_ exists and corresponds to an element in _Hom<sub>A</sub>(Y)_.

  - _Hom<sub>A</sub>( f )( φ ) = f ○ φ_, which is a morphism corresponding to a function in _Hom<sub>A</sub>(Y)_

Note that the expression *Hom<sub>A</sub>( f ) = f ○ \_* is somewhat similar to that of elements in dual vector spaces *Dual( u ) = u\* = < u, _>*

The set of natural transformations between the hom-functor *Hom<sub>A</sub> and a functor _F: C → Set_* 
is denoted _[C, Set](Hom<sub>A</sub>, F)_

### Representable functors
A functor _F_ naturally isomorphic to _Hom<sub>A</sub>_ is called a __representable functor__.
A representation of _F_ is therefore an object _A_ of _C_ together with a natural isomorphism 
_α: Hom<sub>A</sub> → F_.

#### Example
In programming, _List_ is typically **not** representable:

For _List_ to be representable by some type _r_ we would need to implement two functions:

  - _∀ a. φ :: Reader r a → [a]_
  - _∀ a. ψ :: [a] → Reader r a_

While there is always an implementation for the first function _φ_ (actually as many as there are lists of _r_ according
to the _yoneda lemma_), there is none for the second one _ψ_ because of the case when the empty list is provided:
in that case there is no way to find one single implementation  valid for all types _a_ (a function returning a constant
of some particular type would not work).

## Monoïds

The basic definition of a __monoïd__ is bound to a set equipped with a binary operation and a neutral element.
Typically _(ℕ, +)_ forms a monoïd with _1_ as its neutral element.

We can extend that definition to categories with a single object _M_ and arbitrary arrows flowing from _M_ to itself.

In doing so, _Hom<sub>M</sub>(M)_ is a set containing each of the arrows and any two arrows can be combined to form another one,
thereby providing a binary operation, with in particular _Id<sub>M</sub>_ as its neutral element.

Actually any monoïd (in the traditional sense for sets) is isomorphic to the hom-set of some single object category.

## Generalized elements

As mentioned above there is nothing such as elements within objects.
However when a terminal object _T_ is available in a category we have access to a __global element__ _ε_ of any object _X_:

- _ε: T → X_

In the case of _Set_, the morphism _ε_ is actually able to pick any element of a set object. A global element of _X_ is also called a __section element__ of _X_ or a __point__ of _X_.

We can actually see _T_ as a context and that can be generalized to any other object _A_:

- _ε<sub>A</sub>: A → X_

The morphism _ε<sub>A</sub> ∈ Hom<sub>A</sub>(X)_ is called a __generalized element__ of _X_ at __stage__ _A_,
or a __A-point__ of _X_.

![Handbook of Mathematics, Thierry de Vialar](/global-element.png)

## Yoneda lemma

The Yoneda lemma basicaly states that

- _[C, Set](Hom<sub>A</sub>, F) ≅ F A_

Given a functor _F: C → Set_ and the Hom-functor _Hom<sub>A</sub>_, there is a one-to-one correspondance between
the set of natural transformations from _Hom<sub>A</sub>_ to _F_ and the elements of _F A_.

## Yoneda embedding

Corollary:
- _Hom<sub>A</sub> ≅ Hom<sub>B</sub> ⇔ A ≅ B_

A hom-functor _Hom<sub>A</sub>_ is therefore related to a set of generalized elements.

In other words A≅B iff they have the same generalized elements, up to isomorphism.
