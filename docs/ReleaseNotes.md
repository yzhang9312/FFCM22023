---
layout: default
title: Release Notes
nav_order: 9
bibliography: 
---

# Release Notes
{: .no_toc }
Release notes of the FFCM-2 developement
{: .fs-6 .fw-300 }

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

## HCO prompt dissociation
An earlier version of trial model underpredicts the laminar flame speeds of fuel-rich acetylene and oxygen-diluted trioxane, and the preliminary optimization was not able to reconcile the data within the experimental uncertainties by adjusting the rate parameters within the physical limits. The discrepancy is likely due to the missing reactions of prompt dissociation of formyl radicals (HCO), as discussed by Labbe et al.[^LSG2016] The prompt dissociation indicates the weekly bound radicals with low dissociation energy barrier can decompose into a stable molecule and a radical during the vibrational-rotational relaxation process, at temperatures relevant to combustion of hydrocarbons. 

For example, the HCO prompt dissociation expands reaction

$$
\begin{align}
    & \text{CH}_2\text{O} + \text{R} \rightleftharpoons \text{HCO} + \text{RH}
\end{align}
$$

into two reactions

$$
\begin{align}
    \text{CH}_2\text{O} + \text{R} &\rightleftharpoons \text{HCO} + \text{RH}, \\
    \text{CH}_2\text{O} + \text{R} &\rightarrow \text{H + CO} + \text{RH}, 
\end{align}
$$

The rate constant for prompt dissociation reaction (Reaction 3) is obtained by multiplying a dissociation probability with the original rate constant (Reaction 1), where the dissociation probability is calculated by Labbe et al.[^LSG2016]. The rate constant of Reaction 2 is updated by subtracting the rate of Reaction 3 from the original Reaction 1. 

In the current work, we found the HCO prompt dissociation of Reaction 1 where $\text{R} = \text{H}, \text{O}$ and $\text{OH}$ is sufficient. With the updated trial model, the calculated laminar flame speeds are increased by around 12%, and is consistent with the experimental data within uncertainties.

## High pressure methane ignition
In recent years, the increasing interest in using methane/natural gas for high pressure turbine requires a reaction model that can accurately predict high-pressure methane combustion, especially under high oxygen concentration. Although FFCM-1 was validated and tested against a wide range of combustion property targets for methane, it could not predict methane combustion under high pressure, high oxygen concentration conditions, as methyl-proxy (CH<sub>3</sub>O<sub>2</sub>) chemistry was not included. Recently, Shao et al.[^SCD2019] and Karimi et al.[^KOL2019] measured ignition delay times of high-pressure methane in highly diluted CO<sub>2</sub> and Ar using shock tubes. They showed that adding CH<sub>3</sub>O<sub>2</sub> chemistry to FFCM-1 could reproduce experiments of highly diluted mixtures for pressures up to 150 atm. The modified FFCM-1 overpredicts the ignition delay for mixtures with high oxygen concentration and pressures higher than 150 atm. The preliminary FFCM-2 optimization could not reconcile the data and it was found that the reaction of CH<sub>3</sub>O<sub>2</sub> with O<sub>2</sub> is critical under such conditions.

Lakshmanan et al.[^LHS2021] studied the reaction pathways of CH<sub>3</sub>O<sub>2</sub> and O<sub>2</sub> using quantum chemical calculations and dynamic simulations. They found the reaction proceeds via a concerted mechanism: the H-atom shifts to the peroxy radical site and at the same time, O<sub>2</sub> is added to the C-H radical site. Two reaction pathways were proposed with rate constant expressions computed using transition state theory and master equation calculation,

$$
\begin{equation}
    \text{CH}_3\text{O}_2 + \text{O}_2 \rightarrow \text{CH}_2\text{O} + \text{OH + O}_2
\end{equation}
$$

with rate constant expression $k = 4.2 \times 10^{13} \exp(-8676/T)$ cm$^3$ mol$^{-1}$s$^{-1}$, and

$$
\begin{equation}
    \text{CH}_3\text{O}_2 + \text{O}_2 \rightarrow \text{HO}_2 + \text{CO + H}_2\text{O}
\end{equation}
$$

with rate constant expression $k = 467 T^{2.9} \exp(-20870/T)$ cm$^3$ mol$^{-1}$s$^{-1}$. 

The dominating products were found to be CH<sub>2</sub>O + O<sub>2</sub> + OH. With the two additional pathways, the trial model underpredicts the ignition delay, but optimization was able to adjust the rate constant within uncertainty limit to reconcile the data.

## Abstraction reaction by oxygen at the allylic site
The ignition delay times for C<sub>3</sub>H<sub>6</sub>/air or *i*-C<sub>4</sub>H<sub>8</sub>/air mixtures at elevated pressure and high oxygen concentrations are sensitive to the allylic-site hydrogen abstraction reaction by molecular oxygen. The earlier trial model under-predicts ignition delay times under such conditions, indicating the rates assigned for the following reactions were too slow.

$$
\begin{align}
    i\text{-C}_4\text{H}_8 + \text{O}_2 &\rightleftharpoons i\text{-C}_4\text{H}_7 + \text{HO}_2 \\
    \text{C}_3\text{H}_6 + \text{O}_2 &\rightleftharpoons a\text{-}\text{C}_3\text{H}_5 + \text{HO}_2
\end{align}
$$

In an earlier trial model, the rate constant expressions were adapated from Stothard et al.[^SW1991] and Ingham et al.[^IWW1994] for propene and iso-butene, respectively. In their work, the rate constants were fitted to the low-temperature measurements and extrapolated to high-temperature region using a linear Arrhenius expression (no $T^n$ factor). For the *i*-C<sub>4</sub>H<sub>8</sub> reaction, Yasunaga et al.[^YKI2009] conducted shock tube ignition delay and species time-history measurements and the extrapolated high-temperature rate constants were too slow. Zhou et al. [^ZSS2017] and Chen et al.[^CB2000] performed transition state theory analyses and the results are consistent with the fit by Yasunaga et al.[^YKI2009] at elevated temperatures. Recently, Lokachari et al.[^LPK2020] fitted a new expression, considering theories and fits at high temperatures and experiments at lower temperatures. Their rate parameter was adopted in the trial model for iso-butene. For propene, we considered a refit of high-temperature data fit by Burke et al.[^BMH2014] and low-temperature measurements by Stothard et al.[^SW1991].


## High temperature ethylene ignition
The earlier version of trial model over-predicts the ignition delay times of C<sub>2</sub>H<sub>4</sub>/air mixtures at elevated temperatures, and the optimization cannot reconcile the data by adjusting the rate parameters within the physical limits. Sensitivity analysis shows that the kinetics of C<sub>2</sub>H<sub>4</sub> + O is important under these conditions. In the earlier trial model, the rate parameters of C<sub>2</sub>H<sub>4</sub> + O system was adapted from the recommendation by Baulch et al.[^BBC2005]. Based on a series of low-temperature measurements, Baulch et al. assigned the rate parameters with product branching ratios as 60% CH<sub>3</sub> + HCO, 35% CH<sub>2</sub>CHO + H, and 5% CH<sub>2</sub>CO + H<sub>2</sub> at temperature T = 298 K and pressure p < 1 bar. At elevated temperatures, Baulch et al.'s rate constants also predict ~60% products as CH<sub>3</sub> + HCO, which inhibits C<sub>2</sub>H<sub>4</sub> ignition. Recently, Li et al.[^LJZ2017] investigated the kinetics of C<sub>2</sub>H<sub>4</sub> + O system using an ab initio transition state theory based master equation (AITSTME) approach. They also included an a priori description of the intersystem crossing (ISC). At room temperature, their calculated branching ratios are consistent with those of Baulch et al. At high temperatures, however, Li et al.'s theory predicts CH<sub>2</sub>CHO + H and CH<sub>2</sub> + CH<sub>2</sub>O as the major products. Clearly, these channels provide H radicals and promotes the reactivity. Directly applying Li et al.[^LJZ2017]'s rate constants could lead to underprediction of ignition delay times for certain mixtures that are highly diluted. The discrepancy is further addressed by optimization.

Note that although the C<sub>2</sub>H<sub>4</sub> + O kinetics affect the ignition delay times of C<sub>2</sub>H<sub>4</sub>/air mixtures, it has no sensitivity in modeling the real fuel chemistry (e.g., Jet A fuel) using the HyChem approach. In the HyChem modeling, the O radicals react with other pyrolytic products (e.g., H<sub>2</sub>) before reacting with C<sub>2</sub>H<sub>4</sub>.

## Isomerization of butene isomers
In high-temperature combustion, the major decomposition products of many bio-derived sustainable aviation fuels, including the alcohol-to-jet (ATJ) fuel, is iso-butene. This is attributed to the highly-branched molecular structure of the fuels. Thus, an accurate iso-butene reaction kinetic model is critical to modeling these fuels. Recently, the importance of butene isomerization reactions in modeling iso-butene pyrolysis is acknowledged. Nagaraja et al.[^NKP2020] measured the species distribution of *i*-C<sub>4</sub>H<sub>8</sub> pyrolysis in single-pulse shock tube at pressure 2 atm and temperature 1000-1800 K. They found that the reaction model was not able to reproduce the 1-C<sub>4</sub>H<sub>8</sub> and 2-C<sub>4</sub>H<sub>8</sub> yields in experiments due to missing isomerization reactions.

$$
\begin{align}
    &i\text{-C}_4\text{H}_8 \rightleftharpoons 1\text{-C}_4\text{H}_8, \\
    &i\text{-C}_4\text{H}_8 \rightleftharpoons 2\text{-C}_4\text{H}_8, \\
    &1\text{-C}_4\text{H}_8 \rightleftharpoons 2\text{-C}_4\text{H}_8
\end{align}
$$

In the current work, the butene isomerization reactions were included in trial model and their rate constants were determined via an approach that combines reaction rate theories and a constrained optimization against experimental data. The assigned trial rate constants are accomplished through a methylcyclopropane (MCP) intermediate. This is based on the experimental observations of Kalra et al.[^KCL1999] for methylcyclopropane shock tube isomerization to the butene isomers. Quantum calculations on cyclopropane ring opening to propene[^DL1998a] provide guidance for transition state parameters to this concerted hydrogen shift – ring opening process. We conducted master equation calculations (temperature $T = 1000-2000$ K, pressure $p = 1-10$ atm) with the Multiwell code to produce approximate trial model rate parameters for the isomerization reactions, thought to be peripheral at the time, adjusting the transition state parameters and barriers to mimic the MCP experimental results. Note for brevity our model uses a thermal average of the *cis-* and *trans-*2-butene and omits cyclic isomers. Optimization will refine these rates, which merit further study.


## References

[^LSG2016]: Labbe, N. J., Sivaramakrishnan, R., Goldsmith, C. F., Georgievskii, Y., Miller, J. A., & Klippenstein, S. J. (2016). Weakly bound free radicals in combustion:“Prompt” dissociation of formyl radicals and its effect on laminar flame speeds. The journal of physical chemistry letters, 7(1), 85-89.

[^LHS2021]: Lakshmanan, S., Hase, W. L., & Smith, G. P. (2021). Mechanism and kinetics for the reaction of methyl peroxy radical with O 2. Physical Chemistry Chemical Physics, 23(41), 23508-23516.

[^NKP2020]: Nagaraja, S. S., Kukkadapu, G., Panigrahy, S., Liang, J., Lu, H., Pitz, W. J., & Curran, H. J. (2020). A pyrolysis study of allylic hydrocarbon fuels. International Journal of Chemical Kinetics, 52(12), 964-978.

[^BBC2005]: Baulch, D. L., Bowman, C. T., Cobos, C. J., Cox, R. A., Just, T., Kerr, J. A., ... & Warnatz, J. (2005). Evaluated kinetic data for combustion modeling: supplement II. Journal of physical and chemical reference data, 34(3), 757-1397.

[^LJZ2017]: Li, X., Jasper, A. W., Zádor, J., Miller, J. A., & Klippenstein, S. J. (2017). Theoretical kinetics of O+ C2H4. Proceedings of the Combustion Institute, 36(1), 219-227.

[^SCD2019]: Shao, J., Choudhary, R., Davidson, D. F., Hanson, R. K., Barak, S., & Vasu, S. (2019). Ignition delay times of methane and hydrogen highly diluted in carbon dioxide at high pressures up to 300 atm. Proceedings of the combustion institute, 37(4), 4555-4562.

[^KOL2019]: Karimi, M., Ochs, B., Liu, Z., Ranjan, D., & Sun, W. (2019). Measurement of methane autoignition delays in carbon dioxide and argon diluents at high pressure conditions. Combustion and Flame, 204, 304-319.

[^IWW1994]: Ingham, T., Walker, R. W., & Woolford, R. E. (1994, January). Kinetic parameters for the initiation reaction RH+ O2→ R+ HO2. In Symposium (International) on Combustion (Vol. 25, No. 1, pp. 767-774). Elsevier.

[^ZLO2016]: Zhou, C. W., Li, Y., O'connor, E., Somers, K. P., Thion, S., Keesee, C., ... & Curran, H. J. (2016). A comprehensive experimental and modeling study of isobutene oxidation. Combustion and Flame, 167, 353-379.

[^YKI2009]: Yasunaga, K., Kuraguchi, Y., Ikeuchi, R., Masaoka, H., Takahashi, O., Koike, T., & Hidaka, Y. (2009). Shock tube and modeling study of isobutene pyrolysis and oxidation. Proceedings of the Combustion Institute, 32(1), 453-460.

[^CB2000]: Chen, C. J., & Bozzelli, J. W. (2000). Thermochemical property, pathway and kinetic analysis on the reactions of allylic isobutenyl radical with O2: an elementary reaction mechanism for isobutene oxidation. The Journal of Physical Chemistry A, 104(43), 9715-9732.

[^ZSS2017]: Zhou, C. W., Simmie, J. M., Somers, K. P., Goldsmith, C. F., & Curran, H. J. (2017). Chemical kinetics of hydrogen atom abstraction from allylic sites by 3O2; implications for combustion modeling and simulation. The Journal of Physical Chemistry A, 121(9), 1890-1899.

[^LPK2020]: Lokachari, N., Panigrahy, S., Kukkadapu, G., Kim, G., Vasu, S. S., Pitz, W. J., & Curran, H. J. (2020). The influence of iso-butene kinetics on the reactivity of di-isobutylene and iso-octane. Combustion and Flame, 222, 186-195.

[^SW1991]: Stothard, N. D., & Walker, R. W. (1991). Determination of the arrhenius parameters for the initiation reaction C3H6+O2=CH2CHCH2+HO2. Journal of the Chemical Society, Faraday Transactions, 87(2), 241-247.

[^BMH2014]: Burke, S. M., Metcalfe, W., Herbinet, O., Battin-Leclerc, F., Haas, F. M., Santner, J., ... & Curran, H. J. (2014). An experimental and modeling study of propene oxidation. Part 1: Speciation measurements in jet-stirred and flow reactors. Combustion and Flame, 161(11), 2765-2784.

[^KCL1999]: Kalra, B. L., Cho, J. Y., & Lewis, D. K. (1999). Kinetics of the thermal isomerization of methylcyclopropane. The Journal of Physical Chemistry A, 103(3), 362-364.

[^DL1998a]: Dubnikova, F., & Lifshitz, A. (1998). Structural and geometrical isomerizations of cyclopropane. quantum chemical and RRKM calculations. The Journal of Physical Chemistry A, 102(19), 3299-3306.