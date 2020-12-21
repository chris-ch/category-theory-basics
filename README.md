# category-theory-basics
A few notes about category theory

## Preliminary definitions

A __category__ is a collection of __arrows__ between __objects__. Arrows are also called __morphisms__.

There is no limit to the number of arrows between two objects _A_ and _B_.

Coinciding arrows are necessarily composed, so that if we have _φ: A → B_ and _ψ: B → C_ we also necessarily have _(ψ ○ φ): A → C_

Composition is associative : _(ω ○ ψ) ○ φ = ω ○ (ψ ○ φ)_

For any object *A* there is always an __identity arrow__ *id<sub>A</sub>: A → A* such that *id<sub>A</sub>* 
composed with any other composable arrow _φ_ is equivalent to _φ_ itself:

_φ ○ id<sub>A</sub> = φ_

In the case of the category __Set__ objects are sets and morphisms are functions.

An __initial object__ has a unique arrow pointing to every other object. In the category __Set__ the initial object is the empty set, 
because there is only one function from the empty set to any other set, the empty function corresponding to the set containing no relation.

A __terminal object__ has a unique arrow coming from every other object. In the category __Set__ the terminal object is any singleton set.
All singleton sets being isomorphic to each other they are all good candidates.

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

## Generalized elements

As mentioned above there is nothing such as elements within objects.
However when an initial object _I_ is available in a category we have access to a __global element__ _ε_ of any object _X_:

_ε: I → X_

In the case of _Set_, the morphism _ε_ is actually able to pick any element of a set object. A global element of _X_ is also called a __section element__ of _X_ or a __point__ of _X_.

We can actually see _I_ as a context and that can be generalized to any other object _A_:

_ε<sub>A</sub>: A → X_

The morphism _ε<sub>A</sub>_ is a __generalized element__ of _X_ at __stage__ _A_.

![Handbook of Mathematics, Thierry de Vialar](/global-element.png)





