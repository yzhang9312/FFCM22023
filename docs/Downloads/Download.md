---
layout: default
title: Downloads
nav_order: 10
permalink: /docs/Downloads
---

# Downloads
The current page provides access to the optimized FFCM-2 along with the covariance matrix, in both Cantera format and Chemkin format. To obtain the trial FFCM-2, please contact Prof. Hai Wang. 

## Download FFCM-2 (Cantera format)
[CTI format](/assets/data/models/FFCM2_model.cti){: .btn .btn-primary .fs-5 .mb-4 .mb-md-0 .mr-2 }
[YAML format](/assets/data/models/FFCM2_model.cti){: .btn .btn-primary .fs-5 .mb-4 .mb-md-0 .mr-2 }

## Download FFCM-2 (Chemkin format)
[Reactions](/assets/data/models/FFCM2_reactions.inp){: .btn .btn-primary .fs-5 .mb-4 .mb-md-0 .mr-2 }
[Thermochemical Data](/assets/data/models/FFCM2_thermo.dat){: .btn .btn-primary .fs-5 .mb-4 .mb-md-0 .mr-2 }
[Transport Data](/assets/data/models/FFCM2_transport.dat){: .btn .btn-primary .fs-5 .mb-4 .mb-md-0 .mr-2 }

## Download FFCM-2 Covariance Matrix
[Covariance matrix](/assets/data/models/Covariance_matrix.csv){: .btn .btn-primary .fs-5 .mb-4 .mb-md-0 .mr-2 }
[Readme](/assets/data/models/README_covariance.csv){: .btn .btn-primary .fs-5 .mb-4 .mb-md-0 .mr-2 }

{: .note }
The covariance matrix $\mathbf{\Sigma_{aa}} \in \mathbb{R}^{258 \times 258}$ describes the correlation between the normalized rate parameters $\mathbf{x_a} \in \mathbb{R}^{258}$ that remain active after parameter freezing. It can be used to sample the optimized model in the posterior parametric space, using multivariate normal distribution centered at $\mathbf{\mu_a} = \mathbf{0}$. The readme file specifies the rate parameter that corresponds to each dimension of the matrix, along with the uncertainty factor $f$. Given the $k^{th}$ sample $\mathbf{x_k}\sim \mathcal{N}(\mathbf{0}, \mathbf{\Sigma_{aa}})$, the multiplier is calculated by $f^{\mathbf{x_{k}}}$. The sampled rate parameters $A_{k}$ is obtained by multiplying the optimized nominal rate parameter $A_{\*}$ by the multiplier $A_{k} = A_{\*} \times f^{\mathbf{x_{k}}}$.



