# getting started

## following ...

https://jump.dev/JuMP.jl/stable/tutorials/getting_started/getting_started_with_JuMP/

### an example

```julia
using JuMP
import HiGHS

model = Model(HiGHS.Optimizer)

@variable(model, x >= 0)
@variable(model, 0 <= y <= 3)
@objective(model, Min, 12x + 20y)
@constraint(model, c1, 6x + 8y >= 100)
@constraint(model, c2, 7x + 12y >= 120)

optimize!(model)

is_solved_and_feasible(model)

termination_status(model)
primal_status(model)
dual_status(model)

objective_value(model)
value(x)
value(y)

shadow_price(c1)
shadow_price(c2)
```

### arrays

```julia
@variable(model, a[1:2, 1:2])
```

```julia
a[1, 1]
a[:, 2]
```

```julia
n = 10
l = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]
u = [10, 11, 12, 13, 14, 15, 16, 17, 18, 19]
@variable(model, l[i] <= x[i=1:n] <= u[i])
```

```julia
@variable(model, y[i=1:2, j=1:2] >= 2i + j)
@variable(model, w[1:5, ["red", "blue"]] <= 1)
```

### integrality

```julia
@variable(model, integer_x, Int)
@variable(model, binary_x, Bin)
```

### constraints

```julia
@constraint(model, [i = 1:2, j = 1:2; i != j], i * x <= j + 1)

@variable(model, z[1:10])
@constraint(model, c_sum, sum(z[i] for i in 1:10) <= 1)
```

### vectors

Consider an LP in standard form,

    min{c^T x | Ax = b, x >= 0}


```julia
vector_model = Model(HiGHS.Optimizer)
A = [1 1 9 5; 3 5 0 8; 2 0 6 13]
b = [7, 3, 5]
c = [1, 3, 5, 2]
@variable(vector_model, x[1:4] >= 0)
@constraint(vector_model, A * x .== b)
@objective(vector_model, Min, c' * x)

optimize!(vector_model)

is_solved_and_feasible(vector_model)
```

### end
