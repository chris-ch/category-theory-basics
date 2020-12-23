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

A __functor__ puts two categories in correspondance

_F: C<sub>1</sub> → C<sub>2</sub>_

It does so by mapping both objects and morphisms and respecting the structure provided by morphisms.

A __natural transformation__ puts two functors un correspondance

_μ: F<sub>1</sub> → F<sub>2</sub>_

for _F<sub>1</sub>: C<sub>1</sub> → C<sub>2</sub>_ and _F<sub>2</sub>: C<sub>1</sub> → C<sub>2</sub>_

It does so for every object A in _C<sub>1</sub>_, so we have one __component__ for each object A in _C<sub>1</sub>_:

_μ<sub>A</sub>: F<sub>1</sub>(A) → F<sub>2</sub>(A)_ 
is said to be the component of the natural trasnformation _μ_ at _A_.


## Hom-functors
Given any locally small category _C_ we automatically get a second category for free 
called __Hom-functor__ and denoted __Hom<sub>C</sub>(A , \_)__:

_Hom<sub>C</sub>(A, \_): C → Set_

Given an object _A_ it maps
  - each object _X_ to the set of morphisms _Hom<sub>C</sub>(A, X)_ also denoted _X<sup>A</sup>_
  - each morphism _f: X → Y_ to a function _Hom<sub>C</sub>(A, f): Hom<sub>C</sub>(A, X) → Hom<sub>C</sub>(A, Y)_
    
Such a _Hom<sub>C</sub>(A, f)_ function exists because given a morphism _φ: A → X_ in the source category which corresponds to 
a function in _Hom<sub>C</sub>(A, X)_ and a morphism _f: X → Y_ 
their composition _ψ = (f ○ φ): A → Y_ exists and corresponds to an element in _Hom<sub>C</sub>(A, Y)_.

  - _Hom<sub>C</sub>(A, f)( φ ) = f ○ φ_, which is a morphism corresponding to a function in _Hom<sub>C</sub>(A, Y)_

The notation *Hom<sub>C</sub>(A, f) = f ○ \_* is somewhat similar to that of elements in dual vector spaces *Dual(u) = u\* = < u, _>*

A functor naturally isomorphic to _Hom<sub>C</sub>(A , \_)_ is called a __representable functor__.

## Generalized elements

As mentioned above there is nothing such as elements within objects.
However when a terminal object _T_ is available in a category we have access to a __global element__ _ε_ of any object _X_:

- _ε: T → X_

In the case of _Set_, the morphism _ε_ is actually able to pick any element of a set object. A global element of _X_ is also called a __section element__ of _X_ or a __point__ of _X_.

We can actually see _T_ as a context and that can be generalized to any other object _A_:

- _ε<sub>A</sub>: A → X_

The morphism _ε<sub>A</sub> ∈ Hom<sub>C</sub>(A, X)_ is called a __generalized element__ of _X_ at __stage__ _A_,
or a __A-point__ of _X_.

![Handbook of Mathematics, Thierry de Vialar](/global-element.png)


## Yoneda lemma

Given a functor _F: C → Set_ and the Hom-functor _Hom<sub>C</sub>(A , \_)_, there is a one-to-one correspondance between
the set of natural transformations from _Hom<sub>C</sub>(A , \_)_ to _F_ and the elements of _F A_.

A hom-functor _Hom<sub>C</sub>(A , \_)_ is therefore related to a set of generalized elements.

The Yoneda lemma basicaly says that

- _Hom(A, \_) ≅ Hom(B, \_) ⇔ A ≅ B_
    
In other words A≅B iff they have the same generalized elements, up to isomorphism.


