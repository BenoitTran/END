# Entropic Nested Distance

A Julia 1.4 notebook to illustrate the speed and accuracy of the Entropic Nested Distance versus the Nested Distance. Computes on an interactive example the Nested Distance and the Entropic Nested Distance between two scenario trees of depth T.

### Introduction 

The Nested Distance between stochastic processes is a refinement of the Wasserstein distance to account for proximity in filtrations. We compute the Nested Distance via the backward recursive algorithm introduced in [Kovacevic and Pichler, 2015](https://www-user.tu-chemnitz.de/~alopi/publications/ScenarioTreesKovacevicPichler2015.pdf), which amounts to solve an exponential number (in T) number of Linear optimization problems.

Under additive costs, exploiting a decomposition of the Nested Distance as a finite sum of Wasserstein distance presented in [Pichler and Schlotter, 2019](https://arxiv.org/abs/1802.03639), we relax the computation of each Wasserstein distance  by adding an entropic term in the primal objective of the computation of each Wasserstein distance. Thus, the resulting Entropic Nested Distance is a relaxation of the Nested Distance and preserves its main feature: under some assumptions, it is Lipschitz-continuous w.r.t. the value function of Multistage Stochastic optimization Problems, see [Pflug and Pichler, 2012](https://doi.org/10.1137/110825054).

The computation of a Wasserstein distance is roughly O(n^3) with $n$ being the dimension of the ambiant space. By adding an entropic term to the primal of the optimal transport problem associated with the computation of a Wasserstein distance, an alternative maximization scheme in its dual yield Sinkhorn's algorithm, introduced in Optimal Transport in [Cuturi, 2013](https://arxiv.org/abs/1306.0895). By carefully selecting the entropic relaxation term, the complexity of Sinkhorn's algorithm is linear. See [Peyré and Cuturi, 2019](https://arxiv.org/abs/1803.00567) for a complete presentation of Sinkhorn's algorithm.

This notebook aims to highlight the computational efficency of the Entropic Nested Distance compared to the Nested Distance, while remaining its main feature with small over estimation.

### Packages

JuMP https://github.com/jump-dev/JuMP.jl, for modeling optimization problems,

ScenTrees https://github.com/kirui93/ScenTrees.jl for the introduced Tree julia structure and related functions,

Gurobi https://github.com/jump-dev/Gurobi.jl, interface for Gurobi's solver, using a free academic license, for solving LP.
