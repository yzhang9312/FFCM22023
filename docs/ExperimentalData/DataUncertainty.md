---
layout: default
title: Data Uncertainty
parent: Experimental Data
nav_order: 2
---

# Data Uncertainty
All fundamental combustion experimental data have uncertainties. The data uncertainties must be evaluated before using them in reaction model optimization or validation. The source of data uncertainties comes from statistical consistency, experimental techniques, post-processing of the data, among many other sources. In this section, we introduce a systematic framework to quantify the uncertainties for typical combustion experimental data.

## Statistical consistency
One source of uncertainty is the statistical consistency. Over the past decades, the combustion properties of certain thermodynamic conditions have been measured multiple times, by various research groups using different experimental techniques. To this end, we carry out a statistical analysis a using empirical function analysis and nonlinear least square procedure[^LWE2015]. The statistical scatter can be calculated by the prediction confidence interval using 

$$
\begin{equation}
    \delta(\alpha) = t(1 - \frac{\alpha}{2}, n_{df}) \Big\{ \Big[\frac{\sum_{j=1}^n (y_{data, j} - \hat y_{fit,j})^2}{n_{df}} \Big] \Big[1 + \frac{1}{n} + \frac{(x - x_{mean})^2}{\sum_{j=1}^n (x - x_{mean})^2} \Big] \Big\}^{1/2}
\end{equation}
$$

The equation above calculates the $\alpha$ confidence interval, where $t$ is the Student-t distribution; $y_{fit}$ represents the prediction by the empirical functions; $y_{data}$ represents the laminar flame speed measurement $S_u^o$ or the normalized ignition delay measurement $\tau_{ign}[\text{Fuel}]^{-\lambda} [\text{O}_2]^{-\nu} [\text{Diluent}]^{-\gamma}$. The total number of data points is n and the degree of freedom is n<sub>df</sub>. $x$ represents the normalized equivalence ratio $\bar \phi$ or the normalized post-shock temperature $1000 \text{ K} /  T_5$. 


### Laminar Flame Speed
For laminar flame speed, the rational function is used to express the variation of flame speed as a function of the normalized equivalence ratios $\bar \phi$. 

$$
\begin{equation}
    S_{u, calc}^o (\bar \phi) = \frac{P(\bar \phi)}{Q(\bar \phi)} = \frac{\sum_{i=0}^{n_p} p_{i} \bar \phi^{i}}{1 + \sum_{i=1}^{n_q} q_{i} \bar \phi^{i}}
\end{equation}
$$

where $P$, $Q$ are polynomials and $p_i$, $q_i$ are the associated coefficients. The orders of the polynomials $n_p$, $n_q$ are hyper-parameters to be determined through a convergence test on the fit. The normalized equivalence ratio $\bar \phi$ removes the asymmetric variation of flame speed with equivalence ratio $\phi$ between the fuel lean region ($\phi \in [0,1]$) and the fuel rich region ($\phi \in [1, \infty]$)[^LWE2015].


$$
\begin{equation}
    \bar \phi = \frac{\phi}{1 + \phi}
\end{equation}
$$

Herein, we demonstrate the analysis with the laminar flame speed of $i$-C<sub>4</sub>H<sub>8</sub>/air mixtures at unburnt gas temperature $T_u = 298$ K and pressure $p = 1$ atm. The given condition has been measured by 7 research groups from 1998 to 2016. Davis and Law[^DL1998] conducted experiments for equivalence ratios $\phi=0.7-1.7$ using the counterflow twin-flame configuration and the stretch effect of the flame speed measurements was corrected using a linear extrapolation. Kelly[^K2011] and Zhao et al.[^ZYS2015] measured the flame speeds for equivalence ratios $\phi = 0.7-1.8$ using the outwardly propagating spherical flames in a double-chamber constant-pressure combustion bomb and applied a nonlinear regression approach to correct for the stretch effects. Park et al.[^PVS2016] used the counterflow twin-flame techniques for the experiments and obtained the stretch-free data using a computationally-assisted nonlinear extrapolation approach. In a multi-university collaboration work, Zhou et al.[^ZLO2016] provided data from three universities. Princeton University (PU) and Texas A&M University (TAMU) took the measurements using the spherical bombs, wheras CNRS-Université de Lorraine (CNRS) employed the heat flux method. TAMU data were obtained in a high-temperature, high-pressure, constant-volume bomb with nonlinear extrapolation. Princeton data were obtained in a cylindrical chamber with a concentric release chamber, followed by a linear extrapolation to zero stretch. 

Figure 1 plots all data discussed above. The red solid line represents the nominal fit of the data using the rational function. The two blue dash dot lines are the 95% confidence intervals, which gives a quantitative evaluation of the statistical scatter of the data. The data in blue symbols (Davis and Law[^DL1998]) lie outside of the confidence interval for the fuel rich conditions. This is attributed to the linear extrapolation. For this reason, this set of data is removed and the fitting is conducted iteratively until no outliers are observed or outliers cannot be explained by limitations in experimental techniques. This analyses helps to direct the future experiments. For the flame speed of $i$-C<sub>4</sub>H<sub>8</sub>/air mixture, the fuel rich conditions exhibit smaller data scatter than the fuel lean conditions. The large scatter in fuel lean conditions are dictated by two sets of data from Princeton and TAMU: they differ for about $5-7$ cm/s and the reason was unclear according to the original paper[^ZLO2016]. To further reduce the experimental uncertainty, more data at the fuel lean conditions are needed.

<p align="center">
<img src="/assets/images/dataUQ/IC4H8_fls_analysis.png" alt="Employee data" width="500" height="500">
<br>
<i>Figure 1 The statistical consistency analysis for laminar flame speed of iso-butene / air mixture at 298 K and 1 atm</i>
</p>

For such conditions measured multiple times, the calculated $2\sigma$ uncertainty is treated as the fstatistical consistency factor; for conditions that are measured less than 3 times, we use 10% of the measured values to represent the statistical consistency. To factor in other generic effects, the flame speed uncertainty is lower bounded by 5% of the nominal values.

### Ignition Delay Time
For ignition delay measurements, the experimental data are fitted by the widely used Lifshitz function, where $A, n, B, \lambda, \nu, \gamma$ are coefficients and [Fuel], [O<sub>2</sub>] and [Diluent] represent the species concentration calculated by the ideal gas law.

$$
\begin{equation}
    \tau_{ign, calc} (T) = A T^n \exp(\frac{B}{T_5}) [\text{Fuel}]^{\lambda} [\text{O}_2]^{\nu} [\text{Diluent}]^{\gamma}
\end{equation}
$$

Figure 2 collects ignition delay measurements for ethylene/oxygen mixtures diluted in argon from 1967 to 2021. Similarly, the red solid line represents the nominal fit using Lifshitz function, while the two dash dot lines are the 95% confidence intervals. Outlier data are again evaluated based on the experimental techniques used.

<p align="center">
<img src="/assets/images/dataUQ/C2H4+AR_ign_analysis.png" alt="Employee data" width="600" height="600">
<br>
<i>Figure 2 The statistical consistency analysis for ignition delay time of ethylene/oxygen/argon mixture at various temperature, pressure and compositions.</i>
</p>

## Generic effects
In laminar flame speed measurements, many aspects could contribute to the uncertainties, including hydrodynamic instabilities of spherical flames at elevated pressures; inappropriate flame stretch corrections in spherical flames and counterflow measurements; heat-loss through the walls or radiation which challenges the adiabatic assumptions. Considering all these factors, the experimental uncertainties for adiabatic laminar flame speed measurements are at least 5%[^KMK2018]. In our evaluation of flame speed uncertainty, we use 5% of the measured value as the lower bound for $2\sigma$ data uncertainty.

For shock tube measurements, hydrogen radical impurity and temperature uncertainty contribute to data uncertainties. Computer experiments are used to quantify such effects,

- for the hydrogen radical impurity, the combustion property is calculated using the reported mixture composition with and without additional H radicals. The difference between the two calculated values are included in the uncertainty quantification. The amount of H radical is determined by a recent publication using a fitted Arrhenius expression[^UKD2014].

- for the temperature uncertainty, the given T<sub>5</sub> is perturbed by $\pm$1% in kinetic simulations, the difference was included in the uncertainty quantification.

The overall uncertainty factor of a target considers all the factors discussed above. 

## References
[^LWE2015]: Law, C. K., Wu, F., Egolfopoulos, F. N., Gururajan, V., & Wang, H. (2015). On the rational interpretation of data on laminar flame speeds and ignition delay times. Combustion Science and Technology, 187(1-2), 27-36.

[^DL1998]: Davis, S. G., & Law, C. K. (1998). Determination of and fuel structure effects on laminar flame speeds of C1 to C8 hydrocarbons. Combustion Science and Technology, 140(1-6), 427-449.

[^K2011]: Kelley, A. P. (2011). Dynamics of expanding flames (Doctoral dissertation, Princeton University).

[^ZYS2015]: Zhao, P., Yuan, W., Sun, H., Li, Y., Kelley, A. P., Zheng, X., & Law, C. K. (2015). Laminar flame speeds, counterflow ignition, and kinetic modeling of the butene isomers. Proceedings of the Combustion Institute, 35(1), 309-316.

[^PVS2016]: Park, O., Veloo, P. S., Sheen, D. A., Tao, Y., Egolfopoulos, F. N., & Wang, H. (2016). Chemical kinetic model uncertainty minimization through laminar flame speed measurements. Combustion and flame, 172, 136-152.

[^ZLO2016]: Zhou, C. W., Li, Y., O'connor, E., Somers, K. P., Thion, S., Keesee, C., ... & Curran, H. J. (2016). A comprehensive experimental and modeling study of isobutene oxidation. Combustion and Flame, 167, 353-379.

[^KMK2018]: Konnov, A. A., Mohammad, A., Kishore, V. R., Kim, N. I., Prathap, C., & Kumar, S. (2018). A comprehensive review of measurements and data analysis of laminar burning velocities for various fuel+ air mixtures. Progress in Energy and Combustion Science, 68, 197-267.

[^UKD2014]: Urzay, J., Kseib, N., Davidson, D. F., Iaccarino, G., & Hanson, R. K. (2014). Uncertainty-quantification analysis of the effects of residual impurities on hydrogen–oxygen ignition in shock tubes. Combustion and Flame, 161(1), 1-15.
