Performance regression.

My workload:
```
mip version    runtime
1.8.2          7.6
1.9.0          9
1.9.1          8.6
1.9.2          8.9
1.10.0         9.25
1.11.0         9.5
```

Somewhere between 1.8.2 and 1.9.0 a change was made that introduced a performance
regression.
1.9.0 release notes:
```
- The conflict graph of a MIP, indicading conflicting assignments for binary variables, can now be queried
- Initial (optional) support for numpy tensors
- Compatibility fixes for the MacOS binaries
- Speedup for querying solutions in the callbacks
- Documentation improvements
```

Suspect commits?

- https://github.com/coin-or/python-mip/commit/e40444e865c4bc886d93fca7f43dd00083cad8c5
  - nah


# Python MIP (Mixed-Integer Linear Programming) Tools

Package website: **http://python-mip.com**

Python MIP is a collection of Python tools for the modeling and solution
of Mixed-Integer Linear programs (MIPs). MIP syntax was inspired by
[Pulp](https://github.com/coin-or/pulp). Just like
[CyLP](https://github.com/coin-or/CyLP) it also provides access to
advanced solver features like cut generation, lazy constraints, MIPstarts
and solution Pools. Porting Pulp and Gurobi models should be quite easy.

Some of the main features of MIP are:

* high level modeling: write your MIP models in Python as easily as in
  high level languages such as
  [MathProg](https://en.wikibooks.org/wiki/GLPK/GMPL_(MathProg)): 
  operator overloading makes it easy to write linear expressions in Python;

* full featured:
    - cut generators and lazy constraints: work with strong formulations with a
    large number of constraints by generating only the required inequalities
    during the branch and cut search;
    - solution pool: query the elite set of solutions found during the search;
    - MIPStart: use a problem dependent heuristic to generate initial feasible
    solutions for the MIP search.

* fast: the Python MIP package calls directly the native dynamic loadable
  library of the installed solver using the modern python
  [CFFI](https://cffi.readthedocs.io) module; models
  are efficiently stored and optimized by the solver and MIP transparently
  handles all communication with your Python code; it is also compatible
  with the [Pypy](https://pypy.org/) just in time compiler, meaning that
  you can have a much better performance, up to 25 times faster for the 
  creation of large MIPs, than the official Gurobi python interface 
  which only runs on CPython;

* multi solver: Python MIP was written to be deeply integrated with the
  C libraries of the open-source COIN-OR Branch-&-Cut
  [CBC](https://projects.coin-or.org/Cbc) solver and the commercial solver
  [Gurobi](http://www.gurobi.com/); all details of communicating with 
  different solvers are handled by Python-MIP and you write only one
  solver independent code;

* written in modern [typed](https://docs.python.org/3/library/typing.html) Python 3 (requires Python 3.5 or newer).

## Examples

Many Python-MIP examples are documented at https://docs.python-mip.com/en/latest/examples.html 

The code of these examples and additional ones (published in tutorials) can be downloaded at https://github.com/coin-or/python-mip/tree/master/examples

## Documentation
 
The full Python-MIP documentation is available at
https://docs.python-mip.com/en/latest/

A PDF version is also available:
https://python-mip.readthedocs.io/_/downloads/en/latest/pdf/

## Mailing list

Questions, suggestions and development news can be posted at the [Python-MIP
google group](https://groups.google.com/forum/#!forum/python-mip).
 
## Build status

[![Github Actions Status](https://github.com/coin-or/python-mip/workflows/CI/badge.svg?branch=master)](https://github.com/coin-or/python-mip/actions)
[![Current version](https://badge.fury.io/gh/coin-or%2Fpython-mip.svg)](https://github.com/coin-or/python-mip/releases)
[![Current total of lines](https://tokei.rs/b1/github/coin-or/python-mip?category=lines)](https://github.com/coin-or/python-mip)
[![License](https://img.shields.io/badge/license-EPL-blue.svg)](https://github.com/coin-or/python-mip/blob/master/LICENSE)

