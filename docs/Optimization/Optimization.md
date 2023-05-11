---
layout: default
title: Optimization and Uncertainty Minimization
nav_order: 6
permalink: /docs/Optimization
---

# Optimization and Uncertainty Minimization
{: .no_toc }

Mathematical framework for FFCM-2 optimization and uncertainty minimization
{: .fs-6 .fw-300 }

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}
The Method of Uncertainty Minimization by Polynomial Chaos Expansion (MUM-PCE) was developed in earlier work for reaction
model optimization and uncertainty minimization[^SW2011]$^{,}$[^WS2015]. FFCM-1 was developed using the MUM-PCE framework. The 
optimal rate parameters were obtained by minimizing the objective function, and the covariance matrix that describes the 
correlation between each pair of rate parameters was updated using the Bayesian theorem[^STW2016]. The current NN-MUM-PCE
approach builds on the MUM-PCE framework with some adaptation. In this page, we explain the procedures and mathematical 
formulas for NN-MUM-PCE, and highlight the a few unique features.

## Objective function
Similar to MUM-PCE, the NN-MUM-PCE finds the optimal rate parameter assignments $\mathbf x^*$ by solving a
nonlinear least-squares optimization problem 

$$
\begin{align}
    \min_{\mathbf x} &\quad \Phi ({\mathbf x}) \\
    \text{subject to } &\quad \mathbf{x} \in [\mathbf{-1}, \mathbf{1}]
\end{align}
$$

where the objective function $\Phi(\mathbf{x})$ is given as

$$
\begin{equation}
\Phi(\mathbf{x}) = \min_{\mathbf x} \left\{\sum_{m=1}^M \left(\frac{y_m(\mathbf x) - y_{m,obs}}{\sigma_{m,obs}}\right)^2 + \sum_{k=1}^N (\lambda x_k)^2 \right\}
\end{equation}
$$ 

where $M$ is the number of targets considered, $y_m (\mathbf{x})$ and $y_{m,obs}$ are 
the model prediction and the experimental value of the $m^{th}$ target, respectively. $\sigma_{m,obs}$ represents the data uncertainty. 

For the objective function $\Phi(\mathbf{x})$, 
- **the first term** measures the deviation between the model prediction $y_{m}(\mathbf{x})$ and the experimental value $y_{m,obs}$, inversely weighted by the sqaure of the data uncertainty $\sigma_{m,obs}$; 
- **the second term** is the Euclidean norm of the normalized rate parameter $\mathbf{x}$, representing the distances of the optimized rate parameters $$\mathbf{x}^*$$ from the trial assignments $$\mathbf{x} = \mathbf{0}$$.
- $\lambda$ is a regularization coefficient, governing the weight applied to the reaction kinetics relative to combustion property data.

In FFCM-1, an unconstrained optimization problem was solved. Unique to the FFCM-2 work is that the constraints of rate parameters are explicitly applied to the optimization to ensure the physical soundness and interpretability of the optimized rate parameters. 


## Optimization algorithm
In the MUM-PCE approach, the optimization was solved using the Levenberg-Marquardt (LM) algorithm, which works well for low-dimensional, unbounded problems. Also, the constraints on the rate parameters $\mathbf{x}$ was not explicitly imposed. FFCM-2, however, is an exceptionally higher-dimensional, sparse problem. We leveraged the trust region reflective (TRF) algorithm from the SciPy nonlinear least squares optimizer `scipy.optimize.leastsquares`. The TRF algorithm is a robust method that is particularly suitable for large sparse problems with bounds, and it explicitly applies the parameter bounds so that the physical soundness of the optimized rate parameters are ensured. The TRF algorithm requires as input the gradient of $y$ with respect to the optimization variables $\mathbf{x}$, which is available analytically, as discussed before.

## Inconsistent targets
MUM-PCE allows us to evaluates the consistency of reaction model with respect to the experimental data by calculating the $F$ score of a target $m$ as

$$
\begin{equation}
    F_m = \frac{y_{m,obs} - y_{m,opt}}{2\sigma_{m,obs}}
\end{equation}
$$

where $y_{m,opt}$ is the optimized model prediction. A target $m$ is regarded as inconsistent when $\|F_m\| > 1$. That is, the optimized model cannot reconcile the target within its experimental uncertainty by adjusting the rate parameters within the uncertainty limits. The inconsistent targets are removed from the target list and the model is re-optimized. This process is carried out iteratively until all remaining targets are consistent. The inconsistent targets are usually further examined to understand the source of inconsistency. Analysing the inconsistent targets shed light on the refinement of the reation models (e.g., missing reactions, inappropriate rate constant assignments) and the uncertainty/noise in the combustion property data.

## Uncertainty Minimization
The uncertainty minimization is achieved by deriving the posterior covariance matrix using the Bayesian theorem, assuming the trial rate parameters follow a multivariate log-normal distribution. If we linearize the response surface at the optimal point and express $\mathbf{x^*}$ as 

$$
\begin{equation}
    \mathbf{x^*} = \mathbf{x^{(0)*}} + \mathbf{x^{(1)*}} \xi,
\end{equation}
$$

where $\xi \sim \mathcal{N}(0,1)$ is a standard normal random variable; the optimized rate parameters is represented by the mean $\mathbf{x}^{(0)\*}$. The posterior covariance matrix $\Sigma^*$ is obtained by

$$
\begin{equation}
    \Sigma^*= \mathbf{x^{(1)*}} \mathbf{x^{(1)*{T}}} = \Big( \sum_{m=1}^M \frac{\mathbf{J_m}^T \mathbf{J_m}}{\sigma_{m,obs}^2} + \lambda^2 \mathbf{I}\Big)^{-1},
\end{equation}
$$

where $\textbf{I}$ is the identity matrix, and $\mathbf{J_m}$ is the Jacobian matrix evaluated at $\mathbf{x} = \mathbf{x^{(0)*}}$,

$$
\begin{equation}
    \mathbf{J_m} = \frac{\partial y_m}{\partial \mathbf{x}} \Big|_{\mathbf{x} = \mathbf{x^{(0)*}}}
\end{equation}
$$

The prediction uncertainty of the trial or optimized model $\sigma_m^{*}$ can then be calculated using polynomial chaos expansions, 

$$
\begin{equation}
    \sigma_{m}^* = \|\mathbf{J_m}^T \mathbf{L}\|_2^2 + \frac{1}{2} \|\mathbf{L}^T \mathbf{H_m} \mathbf{L}\|_F^2,
\end{equation}
$$

where $\mathbf{J_m}$ and $\mathbf{H_m}$ are the Jacobian and Hessian matrix at the optimal point, and $\mathbf{L}$ is the Cholesky decomposition of the covariance matrix. For the trial model, the covariance matrix is a diagonal matrix given by $\lambda^{-2}\textbf{I}$. For the optimized model, the posterior covariance matrix $\Sigma^*$ is given by equation above.


## Parameter Freezing
Unique to NN-MUM-PCE framework is to freeze unncessary parameters after optimization. The current NN-RS allows to all rate parameters to be optimized. Despite we used massive sets of targets, not all rate parameters can be optimized and constrained, due to the effect sparsity of the combustion chemistry models. Thus, we found it useful to freeze unnecessary parameters after optimization. It helps to suppress noises and interpret the optimization results (especially the perturbed rate constants). 

### Unnecessary parameters
The $i^{th}$ rate parameter $x_i$ is regarded as unnecessary and should be frozen (not optimized) when,

- $\|A_{i,opt}/A_{i,0} - 1\| < \chi_A$
- $\sigma_{i,opt} > \chi_{2\sigma}$

where $A_{i,opt}$, $A_{i,0}$ are the $A$-factor of the $i^{th}$ rate parameter for the optimized and trial models, respectively. ${\sigma_{i, opt}}$ represents the posterior uncertainty factor of the $i^{th}$ rate parameter. 

$\chi_A$, $\chi_{2\sigma}$ set the threshold for the multiplier $A_{i,opt}/A_{i,0}$ and the posterior uncertainty. A small multiplier after optimization means the parameter does not make significant contribution to improving the model prediction; A large posterior parameter uncertainty means the parameter cannot be constrained by the given target set and thus does not contribute to minimizing the
model prediction uncertainties. From this analysis, we divide the parameters $\mathbf{x}$ to two sets of rate parameters, the optimized set $\mathbf{x_a}$ and the unoptimized set $\mathbf{x_f}$. 

### Conditional normal distribution
The conditional normal distribution is applied to freeze the unoptimized set $\mathbf{x_f}$ back to the trial values $\mathbf{x_f} = \mathbf{0}$. The distribution for the optimized set $\mathbf{x_a}$ are derived analytically, 


$$
\begin{align}
    \mathbf{x} \sim \mathcal{N}(\mathbf{\mu}, \mathbf{\Sigma}) = \mathcal{N}(\begin{bmatrix}
    \mathbf{\mu_a} \\
    \mathbf{\mu_f} 
  \end{bmatrix}, \begin{bmatrix}
    \mathbf{\Sigma_{aa}} & \mathbf{\Sigma_{af}}\\
    \mathbf{\Sigma_{fa}} & \mathbf{\Sigma_{ff}}
  \end{bmatrix}),
\end{align}
$$

where

$$
\begin{equation}
    \mathbf{\mu_a}|_{\mathbf{x_f} = \mu_f} = \mathbf{\mu_a + \Sigma_{aa} \Sigma_{ff}^{-1} (x_f - \mu_f)},
\end{equation}
$$

$$
\begin{equation}
    \mathbf{\Sigma_{a}|_{\mathbf{x_f} = \mu_f} = \Sigma_{aa} - \Sigma_{af} \Sigma_{ff}^{-1} \Sigma_{fa}}.
\end{equation}
$$

The choice of $\chi_A$, $\chi_{2\sigma}$ are determined based on the specific problem settings. A parametric study is provided on the summary results page.

## References
[^ZDV2023a]: Zhang, Y., Dong, W., Vandewalle, L. A., Xu, R., Smith, G. P., & Wang, H. (2023). Neural network approach to response surface development for reaction model optimization and uncertainty minimization. Combustion and Flame, 251, 112679.

[^SW2011]: Sheen, D. A., & Wang, H. (2011). The method of uncertainty quantification and minimization using polynomial chaos expansions. Combustion and Flame, 158(12), 2358-2374.

[^STW2016]: G.P. Smith, Y. Tao, and H. Wang, Foundational Fuel Chemistry Model Version 1.0 (FFCM-1), http://nanoenergy.stanford.edu/ffcm1, 2016.

[^WS2015]: Wang, H., & Sheen, D. A. (2015). Combustion kinetic model uncertainty quantification, propagation and minimization. Progress in Energy and Combustion Science, 47, 1-31.

[^TW2019]: Tao, Y., & Wang, H. (2019). Joint probability distribution of Arrhenius parameters in reaction model optimization and uncertainty minimization. Proceedings of the Combustion Institute, 37(1), 817-824.