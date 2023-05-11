---
layout: default
title: Approach
nav_order: 2
bibliography: 
---

# Approach
{: .no_toc }
An overview of the NN-MUM-PCE[^ZDV2023a] framework, the approach to FFCM-2 development.
{: .fs-6 .fw-300 }

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

In the previous work, the Method of Uncertainty Minimization using Polynomial Chaos Expansion[^SW2011]$^{,}$[^WS2015] (**MUM-PCE**) approach was proposed for combustion chemistry reaction model optimization and uncertainty minimization. The MUM-PCE approach was used to develop FFCM-1. In the current FFCM-2 study, we extended the MUM-PCE framework to **NN-MUM-PCE**[^ZDV2023a], using neural networks as response surfaces to handle the high dimensionality in FFCM-2 work.

<p align="center">
<img src="/assets/images/FFCMApproach.png" alt="NN-MUM-PCE approach" width="1000" height="1000">
<br>
<i>The overall workflow of the NN-MUM-PCE framework for FFCM-2 development</i>
</p>

### Trial Model
A trial reaction model is compiled along with its associated thermochemical and transport data. The evaluation of reaction rate constants relies on experimental measurements, ab initio theoretical calculations, or estimation based on analogous reactions. In addition to the nominal rate constant expression, the uncertainty factor of each reaction is also estimated from existing data. Therefore, the trial reaction model consists of thermochemical data, transport properties and a list of chemical reactions, their associated rate constant expressions, and the corresponding uncertainty factors.

### Experimental data collection and evaluation
Extensive literature review was carried out to compile the Stanford fundamental combustion property database for the target fuels/species. Currently the database contains 1192 sets of selected legacy combustion targets dating back to 1937. Relevant properties include the global combustion responses (laminar flame speeds and shock tube ignition delay measurements) and some detailed time-history profiles of key species in a fuel oxidation/pyrolysis process. For each optimization target, uncertainty analysis is performed, taking into consideration the statistical consistency and the generic uncertainties (e.g., uncertainty of temperature $T_5$, impurity of H radicals). Specific target conditions and target values are chosen to best represent the thermodynamic condition range of each data set. 

### Preliminary Test
The trial model is subject to extensive, pre-optimization tests against selected targets. Sensitivity analyses were performed to identify certain problems in the trial model. For example, after an initial screening test, it was determined that the model uncertainty for the laminar flame speed of H<sub>2</sub>/air mixtures can be significantly reduced if the uncertainty in the rate coefficient of the reaction

$$
\begin{equation}
    \text{H}_2 + \text{OH} \rightleftharpoons \text{H}_{2}\text{O} + \text{H}
\end{equation}    
$$

is reduced to the $\pm 20\%$ level. Prof. Han's group at Stanford subsequently made the measurement to reduce the $2\sigma$ rate uncertainty to $\pm 17\%$ [^LDH2013]. The measurement suggests that the higher end values within the uncertainty band of the measured H<sub>2</sub>/air laminar flame speed are probably more accurate than the lower values. Preliminary tests also include forward uncertainty quantification (**UQ**). The quality of the current kinetic rate knowledge is accessed in its predictive precision against the selected target. 

### Optimization and Uncertainty Minimization
The following steps are carried out for the globally constrained optimization and model uncertainty minimization (**UM**). 
- Develop neural network (NN) response surfaces for optimization targets.
- Minimize an objective function against the compiled and evaluated experimental targets using the NN response surfaces. 
- Obtain the posterior mean and covariance matrix of the optimization variables, using the Bayesian theorem with a Gaussian prior. The posterior covariance matrix describes the joint probability distribution function of the rate parameters. It helps reduce the parameter space and minimize the model prediction uncertainties.
- Identify the unnecessary active parameters that do not contribute to improving the models. The unnecessary parameters are frozen using the conditional multivariate Gaussian formula to suppress noises and produce optimization results that are easier to interpret. 

### Validation and Test
We distinguish model validation from model test [^WS2015]. Validation refers to tests against experimental data in which the model prediction uncertainty is also given; whereas a test involves only an "agree-disagree" comparison of a model prediction against its underlying data. A test serves the purpose of showing the model capture the essential physics and quantitatively, it shows that the model is not "wrong."  A validation test is more stringent as it not only compares the nominal prediction against its underlying data, it also provides a quantitative assessment of the model uncertainty against the experimental data uncertainty. In our study, the posterior model is **validated** against the set of experimental data from which the optimization targets are selected. Tests are made for a wider range of combustion data not considered in the target set.

### Further Analysis
Further analyses of the model and the target data are made to reveal key uncertainty in several aspects of the problems, including the rate coefficient and reaction pathways, and the combustion property data. Recommendations are made and documented on the basis of these analyses.

## References
[^ZDV2023a]: Zhang, Y., Dong, W., Vandewalle, L. A., Xu, R., Smith, G. P., & Wang, H. (2023). Neural network approach to response surface development for reaction model optimization and uncertainty minimization. Combustion and Flame, 251, 112679.

[^SW2011]: Sheen, D. A., & Wang, H. (2011). The method of uncertainty quantification and minimization using polynomial chaos expansions. Combustion and Flame, 158(12), 2358-2374.

[^LDH2013]: Lam, K. Y., Davidson, D. F., & Hanson, R. K. (2013). A shock tube study of H2+ OH -> H2O+ H using OH laser absorption. International Journal of Chemical Kinetics, 45(6), 363-373.

[^WS2015]: Wang, H., & Sheen, D. A. (2015). Combustion kinetic model uncertainty quantification, propagation and minimization. Progress in Energy and Combustion Science, 47, 1-31.