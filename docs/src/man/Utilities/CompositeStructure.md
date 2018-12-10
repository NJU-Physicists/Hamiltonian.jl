```@meta
CurrentModule=Hamiltonian.Utilities.CompositeStructure
```

# Composite structure

In principle, Julia is not an object-oriented programming language. For example, only abstract types can be inherited so that subtype cannot inherit fields from their parents. Therefore, Julia prefers composition over inheritance. However, to make a new concrete type behaves much alike another one, tedious reputitions of redifining the generic interfaces are usually not avoidable, especially for the basic types in Julia base. In this module, we implement two such composited types, [`CompositeVector`](@ref) and [`CompositeDict`](@ref), for the sake of future usages.

## Composite vector

A composite vector is a vector that is implemented by including an ordinary `Vector` as one of its attributes with the name `:contents`.

To take full advantages of the Julia base, the following interfaces are redined:
* inquiry of info: `size`, `length`
* comparison between objects: `==`, `isequal`
* obtainment of old elements: `getindex`
* modification of old elements: `setindex!`
* addition of new elements: `push!`, `pushfirst!`, `insert!`, `append!`, `prepend!`
* removal of old elements: `splice!`, `deleteat!`, `pop!`, `popfirst!`, `empty!`
* construction of new objects: `empty`, `reverse`, `similar`
* iteration: `iterate`, `keys`, `values`, `pairs`

Composite vectors are suited for the situations where other attributes are not affected by the modification of the elements. Note that arithmatic operations and logical operations excluding `==` and `isequal` are not supported.

## Composite dict

A composite dict is a dict that is implemented by including an ordinary `Dict` as one of its attributes with the name `:contents`.

To take full advantages of the Julia base, the following interfaces are redined:
* inquiry of info: `isempty`, `length`, `haskey`, `in`, `hash`
* comparison between objects: `==`, `isequal`
* obtainment of old elements: `get`, `getkey`, `getindex`
* modification and addition of elements: `push!`, `get!`, `setindex!`
* removal of old elements: `pop!`, `delete!`, `empty!`
* construction of new objects: `merge`, `empty`
* iteration: `iterate`, `keys`, `values`, `pairs`

As is similar to composite vectors, composite dicts are suited for the situations where other attributes are not affected by the modification of the elements.

## Manul

```@autodocs
Modules=[CompositeStructure]
Order=  [:module,:constant,:type,:macro,:function]
```