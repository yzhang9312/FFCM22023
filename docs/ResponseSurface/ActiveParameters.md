---
layout: default
title: Active Parameters
parent: Response Surface
nav_order: 1
---
# Active Parameters
{: .no_toc }
Normalized rate parameters and active parameters
{: .fs-6 .fw-300 }

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

## Active Parameters
The response surface generation starts from the selection of active rate parameters (optimization variables). For a combustion chemistry reaction model, active parameters could be reaction rate constants, thermochemical data or transport data. The current work focuses only on the reaction rate constants. 

### Normalized rate parameters
The rate constants are described by the nonlinear Arrhenius expression

$$
\begin{equation}
    k = A T^{n} e^{-E/RT},
\end{equation}
$$

where $A$ is the pre-exponential factor ($A$-factor), $n$ is the temperature dependency and $E$ is the activation energy. The rate constant of the $i^{th}$ reaction is denoted as $k_i$. If $k_i$ has nominal value $k_{i,0}$ and the associated uncertainty factor $f_i$, the physical bounds of $k_i$ is defined as

$$
\begin{equation}
    k_i \in [k_{i,0} / f_i, k_{i,0} \times f_i]
\end{equation}
$$

The normalized rate parameter $x_i$ for $k_i$ is expressed as[^FWR1992]

$$
\begin{equation}
    x_i = \frac{\ln( k_i / k_{i,0} )}{ \ln f_i} \in [-1, 1],
\end{equation}
$$

The two limits $x_i = \pm 1$ corresponds to the physical limits defined by its uncertainty factor $f_i$. The subscript "0" represents the nominal rate parameter value in the trial model (trial value). 

In the current work, we did not observe signals from targets to constrain the temperature dependencies $n$ and activation energies $E$. Thus, only $A$-factors are considered as optimization variables. Thus, $x_i$ is simplified as

$$
\begin{equation}
    x_i = \frac{\ln(A_i/A_{i,0})}{\ln f_i} \in (-1, 1),
\end{equation}
$$

The preliminary test indicates certain targets are sensitive to selected Chaperon efficiencies and they need to be considered in the optimization. Thus, we define the normalized Chaperon efficiencies as

$$
\begin{equation} 
    x_l = \frac{\log (\beta_{m,i}/\beta_{m,i,0})}{\log f_{m,i}},
\end{equation}
$$

where $\beta_{m,i}$ is the $m^{th}$ three-body efficiency of the $i^{th}$ reaction, and $\beta_{m,i,0}$ and $f_{m,i}$ are its nominal value and uncertainty factor, respectively. The full list of active parameters is of dimension $K = K_A + K_M$, including all of the active $A$-factors $x_i$ ($i = 1, 2, ..., K_A$) and the Chaperon efficiencies considered in an optimization study $x_l$, where $l = K_A + 1, ..., K_A + K_M$.

### Active parameter selection
In the FFCM-2 optimization, $K_A = 1029$, where all of the $A$-factors are active except the last 25 chemicalluminesence reactions. In addition, 23 three-body Chaperon efficiencies which exhibit sensitivity to targets are active ($K_M = 23$). Thus, the number of active parameters in FFCM-2 optimization is $K = K_A + K_M = 1,052$.

For pressure-dependent unimolecular reactions, the $A$-factors of the high- and low-pressure limit rate coefficients were perturbed by the same factor to keep pressure fall-off in the rate coefficient unchanged. Independent perturbation of the low-pressure limit rate coefficient and hence the fall-off is carried out through the perturbation of the selected Chaperon efficiencies for the same reaction. We used a modified, in-house Cantera code to allow perturbation of Chaperon efficiencies. For PLOG reactions, all specified rate expressions are perturbed with the same factor.

### Selected active Chaperon efficiencies
The 23 active three-body Chaperon efficiencies in the current optimization is listed below, along with their trial values and associated uncertainties. For the H+O<sub>2</sub>(+M)=HO<sub>2</sub>(+M) reaction, the ranges of relative three-body efficiencies are Ar: $\pm 0.2$; H<sub>2</sub>O: $\pm 7$; CO<sub>2</sub>: $\pm 1.4$. For other reactions, generic relative efficiencies are used, and the ranges are: Ar, He: $\pm 0.3$; H<sub>2</sub>O: $\pm 3$; CO<sub>2</sub>: $\pm 1$. Uncertainty factors of three-body efficiencies are obtained by averaging the upper and lower bounds mentioned above. All enhancement factors listed here are relative to N<sub>2</sub>.

|   Index | Reaction             | Three-body (M) | Trial values ($\beta_{m,0}$) |   Uncertainty |
|:-------:|:--------------------:|:-----------:|:-------:|:-------------:|
|      13 | H2O+M=H+OH+M         | M = AR      |    1    |          1.43 |
|      13 | H2O+M=H+OH+M         | M = CO2     |    3.8  |          1.36 |
|      13 | H2O+M=H+OH+M         | M = H2      |    3    |          1.5  |
|      13 | H2O+M=H+OH+M         | M = HE      |    1.1  |          1.38 |
|      15 | H+O2(+M)=HO2(+M)     | M = AR      |    0.67 |          1.43 |
|      15 | H+O2(+M)=HO2(+M)     | M = CO2     |    2.88 |          1.95 |
|      15 | H+O2(+M)=HO2(+M)     | M = H2O     |   14    |          2    |
|      24 | H2O2(+M)=2OH(+M)     | M = AR      |    1    |          1.43 |
|      35 | HCO+M=CO+H+M         | M = AR      |    1    |          1.43 |
|      35 | HCO+M=CO+H+M         | M = CO2     |    2    |          2    |
|      35 | HCO+M=CO+H+M         | M = H2O     |   12    |          1.33 |
|      35 | HCO+M=CO+H+M         | M = HE      |    1    |          1.43 |
|      86 | H+HCO(+M)=CH2O(+M)   | M = AR      |    0.7  |          1.75 |
|      86 | H+HCO(+M)=CH2O(+M)   | M = CO2     |    2    |          2    |
|     101 | CH3+H(+M)=CH4(+M)    | M = AR      |    0.7  |          1.75 |
|     101 | CH3+H(+M)=CH4(+M)    | M = CO2     |    2    |          2    |
|     101 | CH3+H(+M)=CH4(+M)    | M = H2O     |    6    |          2    |
|     116 | 2CH3(+M)=C2H6(+M)    | M = AR      |    0.7  |          1.75 |
|     116 | 2CH3(+M)=C2H6(+M)    | M = H2O     |    6    |          2    |
|     288 | C2H4(+M)=H2+H2CC(+M) | M = AR      |    0.7  |          1.75 |
|     288 | C2H4(+M)=H2+H2CC(+M) | M = H2O     |    6    |          2    |
|     336 | C2H4+H(+M)=C2H5(+M)  | M = AR      |    0.7  |          1.75 |
|     336 | C2H4+H(+M)=C2H5(+M)  | M = H2O     |    6    |          2    |

## References

[^FWR1992]: Frenklach M, Wang H, Rabinowitz MJ. Optimization and analysis of large chemical kinetic mechanisms using the solution mapping method—combustion of methane. Prog Energy Combust Sci. 1992;18:47-73.