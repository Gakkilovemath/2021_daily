
a['a_b'] = a['a'].astype("str") + "_" + a['b'].astype("str")
a['a_b_category'] = a['a_b'].astype("category")
a.groupby(['a_b_category'])['c'].cumsum()
It comes a lot that we often summarize a continuous distribution (often, posterior distribution of parameter estimation or of predictions) by a point mass (or a sharpe spike) for (1) computation or memory cost, (2) easier communication, (3) part of a larger computation approximation, such as EM or in dropout, or a combination of all of these.

How do we justify the choice of point summary? Here is a few list:

The mean of posterior density minimizes the 
L
2
 risk.
The mode of the posterior density minimizes the KL divergence to it. Well, this needs more explanation. Assuming 
p
(
θ
)
 is some continuous density on real line with respect to the Lebesgue measure 
μ
(
θ
)
—but a point mass 
δ
(
θ
0
)
 is defined with repect to counting measure 
μ
c
(
θ
)
—but to define KL divergence does requires the same measurable space. To overvome this ambiguity we can either (a) equip the real line with the summed measure 
μ
c
(
θ
)
+
μ
(
θ
)
 and the KL divergence reads 
C
−
log
p
(
θ
0
)
 which is minimized at the mode, or (b) view 
δ
(
θ
0
)
≈
n
o
r
m
a
l
(
θ
0
,
τ
)
 for a very small but fixed 
τ
, then KL divergence is also approximately 
C
(
τ
)
+
log
p
(
θ
0
)
, which again minimized at the mode. Put it in another way, the MAP is always the spiky variational inference approximation to the exact posterior density.
The Wasserstein metric is different. It is legit to consider the Wasserstein metric between point mass and continuous densities. The posterior median minimizes the Wasserstein metric for order 1 and he posterior mean minimizes the Wasserstein metric for order 2. Likewise we can argue the posterior median/mean is the variational inference approximation to the exact posterior density under Wasserstein metric.


