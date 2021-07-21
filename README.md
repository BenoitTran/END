## Entropic approximation of the Nested Distance

Computes on an interactive example the Nested Distance and the Entropic Nested Distance between two scenario trees of depth $T$.

The Nested Distance between stochastic processes is a refinement of the Wasserstein distance to account for proximity in filtrations. We compute the Nested Distance via the backward recursive algorithm introduced in [Kovacevic and Pichler, 2015](https://www-user.tu-chemnitz.de/~alopi/publications/ScenarioTreesKovacevicPichler2015.pdf), which amounts to solve an exponential number (in $T$) number of Linear optimization problems corresponding to the computation of an Optimal Transport problem between conditional probabilities, see [Pichler and Schlotter, 2019](https://arxiv.org/abs/1802.03639).

We regularize the computation of each Optimal Transport problem by adding an entropic term in its objective. The resulting Entropic regularization of the Nested Distance (END) preserves its main feature: under some assumptions, it is Lipschitz-continuous w.r.t. the value function of Multistage Stochastic optimization Problems, see [Pflug and Pichler, 2012](https://doi.org/10.1137/110825054).

The computation of an Optimal Transport problem is done by Linear Programming. Solving its regularized counterpart is done by an alternative maximization scheme called Sinkhorn's algorithm, introduced in Optimal Transport by [Cuturi, 2013](https://arxiv.org/abs/1306.0895). See [Peyré and Cuturi, 2019](https://arxiv.org/abs/1803.00567) for a complete presentation of Sinkhorn's algorithm.

This notebook aims to highlight the computational efficency of the Entropic Nested Distance compared to the Nested Distance, while remaining its main feature with small over estimation.
