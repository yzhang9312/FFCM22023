---
layout: default
title: Foundational Fuels
parent: Introduction
nav_order: 1
---

# Foundational Fuels and Foundational Fuel Chemistry Model
{: .no_toc }
Introduction of foundational fuels and foundational fuel chemistry model
{: .fs-6 .fw-300 }

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

## Foundational Fuels and Foundational Fuel Chemistry Model
Reliable combustion simulation depends on an accurate and uncertainty-minimized combustion chemistry reaction model. Owing to the hierarchical nature of combustion chemistry, the reaction kinetics of hydrogen, carbon monoxide and small hydrocarbons C<sub>1-4</sub> is the foundation to combustion chemistry modeling of all hydrocarbon compounds. These smaller hydrocarbons species are referred to as **foundational fuels** and the corresponding reaction model is termed as **foundational fuel chemistry model**.

### Relevance to HyChem modeling
The development of foundational fuel chemistry model is not only critical to smaller hydrocarbons, but relevant to the modeling of real, multicomponent fuel combustion. 

Recently, a physics-based hybrid chemistry (HyChem) modeling approach was developed for modeling reaction chemistry of large hydrocarbons and real, distillate fuels[^WXW2018]$^{,}$[^XWB2018]$^{,}$[^TXW2018]$^{,}$[^WXP2018]$^{,}$[^SWX2020]$^{,}$[^XSL2020]$^{,}$[^XW2021]. The HyChem approach decouples the high-temperature combustion of large hydrocarbons and real, liquid fuels into two stages that are separable in temporal and spatial scales: the fuel first undergoes a rapid decomposition to produce a mixture of smaller intermediate species; these fragments, consisting primarily of foundational fuels, are oxidized to the final combustion products. The fuel decomposition is a fast process, and can be modeled with a few global, lumped reactions. The stoichiometric coefficients and rate constants of the lumped reactions can be determined by solving an inverse problem, using as targets the speciation data of thermal and oxidative pyrolysis experiments conducted in shock tube and flow reactor. The rate limiting step in the oxidation of the fragments, which must be treated with a detailed, foundational fuel chemistry model. 

The HyChem approach models the real fuel as one single species, resolving the challenge to determine the chemical compositions of the real, multi-component fuels that are difficult to be precisely defined. Also, the decoupling of the lumped fuel decomposition reactions and foundational fuel chemistry avoids compiling a great many reaction pathways and rate constants that cannot be studied by first-principle or experiments. The number of chemical species and reactions are significantly reduced to the level of foundational fuel chemistry. The HyChem approach has been successfully applied to modeling a series of conventional jet fuels[^WXW2018]$^{,}$[^XWB2018], synthetic jet fuels[^TXW2018], rocket fuels[^XWB2018], gasoline fuels[^XSL2020], sustainable aviation fuels[^WXP2018] and formation of NOx from the Jet A fuel[^SWX2020]. The model could be reduced to $40 - 50$ species and are applicable to CFD simulations.

An issue identified in the earlier HyChem work is that the uncertainties of HyChem models remain large, due to the uncertainties in the foundational fuel chemistry[^XWB2018]$^{,}$[^WXP2018]. Thus, an accurate and uncertainty-minimized foundational C<sub>0−4</sub> combustion chemistry model is critical to accurately modeling large hydrocarbons and real, distillate fuels.

### List of Foundational Fuels
The key foundational fuels are listed below. The **primary species** (shown in bold) are those found in the decomposition of the large hydrocarbons and real fuels, whereas the *secondary species* (shown in italics) are common fuels themselves. The current optimization, validation and test are focused on the listed fuels.

| $\text{C}_{0-1}$ species | $\text{C}_{2}$ species | $\text{C}_{3}$ species | $\text{C}_{4}$ species | Aromatics |
|:-------------:|:------------------:|:------:|:---:|:---:|
| $$\text{H}_2$$ **(hydrogen)** | $$\text{C}_2\text{H}_2$$ **(acetylene)** | $$p\text{-C}_3\text{H}_4$$ **(propyne)** | $$1,3\text{-C}_4\text{H}_6$$ **(1,3-butadiene)** | $$\text{C}_6\text{H}_6$$ **(benzene)** |
| $$\text{CO}$$ **(carbon monoxide)** | $$\text{C}_2\text{H}_4$$ **(ethylene)** | $$a\text{-C}_3\text{H}_4$$ **(allene)** | $$1\text{-C}_4\text{H}_8$$ **(1-butene)** | $$\text{C}_7\text{H}_8$$ **(toluene)** |
| $$\text{C}\text{H}_2\text{O}$$ **(formaldehyde)** | $$\text{C}_2\text{H}_6$$ **(ethane)** | $$\text{C}_3\text{H}_6$$ **(propene)** | $$2\text{-C}_4\text{H}_8$$ **(2-butene)** ||
| $$\text{CH}_4$$ **(methane)** | | | $$i\text{-C}_4\text{H}_8$$ **(iso-butene)** ||
|||||
| $$\text{H}_2\text{O}_2$$ (*hydrogen peroxide*) | $$\text{CH}_3\text{CHO}$$ (*acetaldehyde*) | $$\text{C}_3\text{H}_8$$ (*propane*) | $$n\text{-C}_4\text{H}_{10}$$ (*n-butane*) |
| $$\text{CH}_3\text{OH}$$ (*methanol*) | $$\text{C}_2\text{H}_5\text{OH}$$ (*ethanol*) | $$\text{CH}_3\text{COCH}_3$$ (*acetone*) | $$i\text{-C}_4\text{H}_{10}$$ (*iso-butane*) |
| | | | $$\text{C}_4\text{H}_{4}$$ (*vinyl acetylene*) | |
| | | | $$\text{C}_4\text{H}_{2}$$ (*diacetylene*) | |

{: .note }
FFCM-1 was developed only for combustion of H<sub>2</sub>, CO, CH<sub>2</sub>O and CH<sub>4</sub>; FFCM-2 extends the coverage to all C<sub>0-4</sub> foundational fuels. The current release does not include species and reactions for aromatics (C<sub>6</sub>H<sub>6</sub>, C<sub>7</sub>H<sub>8</sub>). 

## References
[^WXW2018]: Wang, H., Xu, R., Wang, K., Bowman, C. T., Hanson, R. K., Davidson, D. F., ... & Egolfopoulos, F. N. (2018). A physics-based approach to modeling real-fuel combustion chemistry-I. Evidence from experiments, and thermodynamic, chemical kinetic and statistical considerations. Combustion and Flame, 193, 502-519.

[^XWB2018]: Xu, R., Wang, K., Banerjee, S., Shao, J., Parise, T., Zhu, Y., ... & Wang, H. (2018). A physics-based approach to modeling real-fuel combustion chemistry–II. Reaction kinetic models of jet and rocket fuels. Combustion and Flame, 193, 520-537.

[^TXW2018]: Tao, Y., Xu, R., Wang, K., Shao, J., Johnson, S. E., Movaghar, A., ... & Wang, H. (2018). A Physics-based approach to modeling real-fuel combustion chemistry–III. Reaction kinetic model of JP10. Combustion and Flame, 198, 466-476.

[^WXP2018]: Wang, K., Xu, R., Parise, T., Shao, J., Movaghar, A., Lee, D. J., ... & Wang, H. (2018). A physics-based approach to modeling real-fuel combustion chemistry–IV. HyChem modeling of combustion kinetics of a bio-derived jet fuel and its blends with a conventional Jet A. Combustion and Flame, 198, 477-489.

[^SWX2020]: Saggese, C., Wan, K., Xu, R., Tao, Y., Bowman, C. T., Park, J. W., ... & Wang, H. (2020). A physics-based approach to modeling real-fuel combustion chemistry–V. NOx formation from a typical Jet A. Combustion and Flame, 212, 270-278.

[^XSL2020]: Xu, R., Saggese, C., Lawson, R., Movaghar, A., Parise, T., Shao, J., ... & Wang, H. (2020). A physics-based approach to modeling real-fuel combustion chemistry–VI. Predictive kinetic models of gasoline fuels. Combustion and Flame, 220, 475-487.

[^XW2021]: Xu, R., & Wang, H. (2021). A physics-based approach to modeling real-fuel combustion chemistry–VII. Relationship between speciation measurement and reaction model accuracy. Combustion and Flame, 224, 126-135.