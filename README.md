# Metaheuristics

A Julia package for metaheuristic optimization algorithms. Evolutionary are considered.

[![Build Status](https://travis-ci.org/jmejia8/Metaheuristics.jl.svg?branch=master)](https://travis-ci.org/jmejia8/Metaheuristics.jl)
[![Coverage Status](https://coveralls.io/repos/github/jmejia8/Metaheuristics.jl/badge.svg?branch=master)](https://coveralls.io/github/jmejia8/Metaheuristics.jl?branch=master)
[![Doc](https://img.shields.io/badge/docs-dev-blue.svg)](https://jmejia8.github.io/Metaheuristics.jl/dev/)

## Installation

Open the Julia (Julia 0.7 or Later) REPL and press `]` to open the Pkg prompt. To add this package, use the add command:

```
pkg> add https://github.com/jmejia8/Metaheuristics.jl.git
```

## Algorithms

- Evolutionary Centers Algorithm
- Differential Evolution
- Particle Swarm Optimization
- Artificial Bee Colony
- MOEA/D-DE
- Gravitational Search Algorithm
- Simulated Annealing
- Whale Optimization Algorithm
- NSGA-II

## Quick Start

Assume you want to solve the following minimization problem.

![Rastrigin Surface](https://raw.githubusercontent.com/jmejia8/Metaheuristics.jl/master/docs/src/figs/rastrigin.png)

Minimize:

![Eq](https://latex.codecogs.com/gif.latex?f(x) = 10D + \sum_{i=1}^{D}  x_i^2 - 10\cos(2\pi x_i))

where ![Eq](https://latex.codecogs.com/gif.latex?x\in[-5, 5]^{D}), i.e., ![Eq](https://latex.codecogs.com/gif.latex?-5 \leq x_i \leq 5) for ![Eq](https://latex.codecogs.com/gif.latex?i=1,\ldots,D). D is the
dimension number, assume D=10.

### Solution

Firstly, import the Metaheuristics package:

```julia
using Metaheuristics
```

Code the objective function:
```julia
f(x) = 10length(x) + sum( x.^2 - 10cos.(2π*x)  )
```

Instantiate the bounds, note that `bounds` should be a $2\times 10$ `Matrix` where
the first row corresponds to the lower bounds whilst the second row corresponds to the
upper bounds.

```julia
D = 10
bounds = [-5ones(D) 5ones(D)]'
```

Approximate the optimum using the function `optimize`.

```julia
result = optimize(f, bounds)
```

Optimize returns a `State` datatype which contains some information about the approximation.
For instance, you may use mainly two functions to obtain such approximation.

```julia
@show minimum(result)
@show minimizer(result)
```


## Contributing


Please, be free to send me your PR, issue or any comment about this package for Julia.
