# triple -- JuMP

## version and project setup

```sh
julia -version
```
=>
    julia version 1.12.0


```julia/pkg
activate triple
```
=>
    Activating new project at `~/b/julia/triple/triple`

## install JuMP

Following https://jump.dev/JuMP.jl/stable/installation/,

```julia/pkg
add JuMP
```
=>
    [snip]
    Precompiling packages finished.
      13 dependencies successfully precompiled in 55 seconds. 127 already precompiled.


## install HiGHS

```julia/pkg
add HiGHS
```
=>
    [snip]
    Precompiling packages finished.
      4 dependencies successfully precompiled in 8 seconds. 140 already precompiled.


## using ...

```julia
using JuMP
using HiGHS
model = Model(HiGHS.Optimizer)
set_attribute(model, "output_flag", false)
set_attribute(model, "primal_feasibility_tolerance", 1e-8)
```

All seems fine.

## next ...

see `getting-started.md`

## resources

https://jump.dev/


### end
