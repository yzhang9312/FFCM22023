---
layout: default
title: History of Kinetic Modeling
parent: Introduction
nav_order: 2
---

# History of Detailed Combustion Chemistry Modeling
{: .no_toc }
The history of detailed combustion chemistry reaction modeling dates back to 1960s.
{: .fs-6 .fw-300 }

## Table of contents
{: .no_toc .text-delta }

1. TOC
{:toc}

There is a long history of detailed combustion reaction modeling by the combustion chemistry community. Listed below are some milestones for the detailed chemistry modeling for combustion of small hydrocarbons that date back to 1960s.

## Milestones of detailed chemistry modeling for combustion of small hydrocarbons
- **Pioneering work**: In the 1960's, Dixon-Lewis published the pioneering work of modeling combustion chemistry using detailed reaction models[^D1967]$^{,}$[^D1970]. 

- **Early work**: From 1960's to 1990's, various reaction models were developed to reproduce a wide range of low-dimensional flame experiments, advancing the knowledge of fundamental reaction mechanisms and rate constants. The efforts explained both global combustion responses (laminar flame speed, heat release rate and ignition delay time) and detailed time-histories of certain species and combustion byproducts including nitrogen oxides (NOx), polycyclic aromatic hydrocarbons (PAHs) and soot. These inlcude the work of, among others, Jürgen Warnatz[^W1981]$^{,}$[^W1983], James A. Miller[^MMS1982]$^{,}$[^KME1989], Charles K. Westbrook[^WD1984]$^{,}$[^WP1984], Frederick L. Dryer[^WD1984]$^{,}$[^WD1981], Michael Frenklach[^FW1991]$^{,}$[^WF1997] and Hai Wang[^WF1997].

- **GRI Mech**: In the late 1990's, a reaction model for combustion of natural gas was developed, as the result of a decade-long collaboration among several institutions (known as the GRI Mech[^FWY1995]$^{,}$[^SGF1999] effort). The much-celebrated GRI Mech marks a unique advance in the development of reaction models, because it

  - involved the advanced experimentation of laser diagnostics, and reaction rate theories collaboratively in compiling the reaction pathways and evaluating the rate constant expressions;
  - applied a systematic, globally constrained optimization approach to derive the optimal rate constant assignment, within the physical limits of the parameters[^FWR1992].

  The combined approach ensures the physical soundness of the rate parameters based on the best kinetic knowledge at the time, and at the same time, the predictive capability of the reaction model against a wide set of combustion target data. As a result, the model has been the industry standard for the last two decades. 

- **Recent work**: Over the past two decades, much progress was made on reaction model development, due to the advance in
  - *experimental techniques*: the rate coefficients of some reactions can be measured using the shock tube/laser diagnostics techniques within an accuracy of ±20%[^LDH2013];
  - *reaction rate theories*: the advance in ab initio electronic structure calculations and reaction rate theories, along with the increased computing power, allows rate coefficients of many reactions to be calculated with chemical accuracy[^MPT2005]$^{,}$[^MK2006]$^{,}$[^FMK2006].

  Massive amounts of experimental data have been published in literature. Thus, many of the reaction rate coefficients must be updated and the reaction model must also be optimized, validated and tested against a significantly wider range of thermodynamic conditions. A list of the recent work includes
    * **H<sub>2</sub>/CO submodels**[^OCS2004]$^{,}$[^LZK2004]$^{,}$[^SW2006]$^{,}$[^SYJ2007]$^{,}$[^K2008] were updated and validated against a wide range of thermodynamic conditions;
    * **USC Mech II**, a high-temperature reaction model for combustion of H<sub>2</sub>/CO/C<sub>1-4</sub> compounds[^WYJ2007], was developed in 2007 and validated against experimental data for up to C<sub>3</sub> species; 
    * **Aramco Mech** were developed from 2013 to 2018 for the combustion of small hydrocarbons, including Aramco Mech Version 1.3[^MBA2013], Version 2.0[^ZLO2016] and Version 3.0[^ZLB2018]. Prof. [Henry Curran][Henry Curran] of National University of Ireland Galway led the effort.

- **FFCM-1**: In 2016, FFCM-1[^STW2016] was released from an earlier work of the group. FFCM-1 consists of 38 species and 291 reactions for combustion of C<sub>0-2</sub> species and was optimized against combustion targets of H<sub>2</sub>, syngas, carbon monoxide, CH<sub>2</sub>O, CH<sub>4</sub>, and a limited set of C<sub>2</sub>H<sub>6</sub> data. The effort is unique in its approaches, objectives, and scopes from other studies in several aspects, because FFCM-1

  - provides the covariance matrix that derived from assimilating a set of fundamental combustion targets over a wide range of thermodynamic conditions and phenomena into the state of knowledge in reaction kinetics, using the Bayes theorem;
  - was the pioneering combustion reaction model that quantifies and minimizes the model prediction uncertainties. The model not only makes the nominal predictions for the combustion property, but yields uncertainty bands using the posterior covariance matrix;
  - was exploited to discern he remaining uncertainty and unresolved issues in the reaction rate coefficients and fundamental combustion data, which helped to direct future research in the reaction model community.

## References

[^D1967]: Dixon-Lewis, G. N. (1967). Flame structure and flame reaction kinetics-I. Solution of conservation equations and application to rich hydrogen-oxygen flames. Proceedings of the Royal Society of London. Series A. Mathematical and Physical Sciences, 298(1455), 495-513.

[^D1970]: Dixon-Lewis, G. (1970). Flame structure and flame reaction kinetics-V. Investigation of reaction mechanism in a rich hydrogen+ nitrogen+ oxygen flame by solution of conservation equations. Proceedings of the Royal Society of London. A. Mathematical and Physical Sciences, 317(1529), 235-263.

[^W1981]: Warnatz, J. (1981, January). The structure of laminar alkane-, alkene-, and acetylene flames. In Symposium (International) on Combustion (Vol. 18, No. 1, pp. 369-384). Elsevier.

[^W1983]: Warnatz, J. (1983). The mechanism of high temperature combustion of propane and butane. Combustion Science and Technology, 34(1-6), 177-200.

[^MMS1982]: Miller JA, Mitchell RE, Smooke MD, Kee RJ. Toward a comprehensive chemical kinetic mechanism for the oxidation of acetylene: comparison of model predictions with results from flame and shock tube experiments. Symp (Int) Combust. 1982;19:181-96.

[^KME1989]: Kee RJ, Miller JA, Evans GH, Dixon-Lewis G. A computational model of the structure and extinction of strained, opposed flow, premixed methane-air flames. Symp (Int) Combust. 1989;22:1479-94.

[^WD1984]: Westbrook CK, Dryer FL. Chemical kinetic modeling of hydrocarbon combustion. Prog Energy Combust Sci. 1984;10:1-57.

[^WP1984]: Westbrook CK, PITZ WJ. A comprehensive chemical kinetic reaction mechanism for oxidation and pyrolysis of propane and propene. Combust Sci Technol. 1984;37:117-52.

[^WD1981]: Westbrook CK, Dryer FL. Chemical kinetics and modeling of combustion processes. Symp (Int) Combust. 1981;18:749-67.

[^MB1989]: Miller JA, Bowman CT. Mechanism and modeling of nitrogen chemistry in combustion. Prog Energy Combust Sci. 1989;15:287-338.

[^WF1997]: Wang H, Frenklach M. A detailed kinetic modeling study of aromatics formation in laminar premixed acetylene and ethylene flames. Combust Flame. 1997;110:173-221.

[^FW1991]: Frenklach M, Wang H. Detailed modeling of soot particle nucleation and growth. Symp (Int) Combust. 1991;23:1559-66.

[^FWY1995]: Frenklach M, Wang H, Yu C, Goldenberg M, Bowman C, Hanson R, Davidson D, Chang E, Smith G, Golden D. GRI-Mech-1.2, An Optimized Detailed Chemical Reaction Mechanism for Methane Combustion. Gas Research Institute. 1995.

[^SGF1999]: Smith GP, Golden DM, Frenklach M, Moriarty NW, Eiteneer B, Goldenberg M, Bowman CT, Hanson RK, Song S, Gardiner Jr WC. GRI-Mech 3.0. http://www.me.berkeley.edu/gri_mech. 1999.

[^FWR1992]: Frenklach M, Wang H, Rabinowitz MJ. Optimization and analysis of large chemical kinetic mechanisms using the solution mapping method—combustion of methane. Prog Energy Combust Sci. 1992;18:47-73.

[^MPT2005]: Miller JA, Pilling MJ, Troe J. Unravelling combustion mechanisms through a quantitative understanding of elementary reactions. Proc Combust Inst. 2005;30:43-88.

[^FMK2006]: Fernández-Ramos A, Miller JA, Klippenstein SJ, Truhlar DG. Modeling the kinetics of bimolecular reactions. Chem Rev. 2006;106:4518-84.

[^MK2006]: Miller JA, Klippenstein SJ. Master equation methods in gas phase chemical kinetics. J Phys Chem A. 2006;110:10528-44.

[^K2008]: Konnov AA. Remaining uncertainties in the kinetic mechanism of hydrogen combustion. Combust Flame. 2008;152:507-28.

[^LZK2004]: Li J, Zhao Z, Kazakov A, Dryer FL. An updated comprehensive kinetic model of hydrogen combustion. Int J Chem Kinet. 2004;36:566-75.

[^SW2006]: Saxena P, Williams FA. Testing a small detailed chemical-kinetic mechanism for the combustion of hydrogen and carbon monoxide. Combust Flame. 2006;145:316-23.

[^SYJ2007]: Sun H, Yang S, Jomaas G, Law C. High-pressure laminar flame speeds and kinetic modeling of carbon monoxide/hydrogen combustion. Proc Combust Inst. 2007;31:439-46.

[^OCS2004]: Ó Conaire M, Curran HJ, Simmie JM, Pitz WJ, Westbrook CK. A comprehensive modeling study of hydrogen oxidation. Int J Chem Kinet. 2004;36:603-22.

[^DJW2005]: Davis SG, Joshi AV, Wang H, Egolfopoulos F. An optimized kinetic model of H2/CO combustion. Proc Combust Inst. 2005;30:1283-92.

[^WYJ2007]: Wang, H., You, X., Joshi, A. V., Davis, S. G., Laskin, A., Egolfopoulos, F., & Law, C. K. (2007). USC Mech Version II. High-temperature combustion reaction model of H2/CO/C1-C4 compounds. URL: http://ignis.usc.edu/USC_Mech_II.htm.

[^MBA2013]: Metcalfe, W. K., Burke, S. M., Ahmed, S. S., & Curran, H. J. (2013). A hierarchical and comparative kinetic modeling study of C1− C2 hydrocarbon and oxygenated fuels. International Journal of Chemical Kinetics, 45(10), 638-675.

[^ZLO2016]: Zhou, C. W., Li, Y., O'connor, E., Somers, K. P., Thion, S., Keesee, C., ... & Curran, H. J. (2016). A comprehensive experimental and modeling study of isobutene oxidation. Combustion and Flame, 167, 353-379.

[^ZLB2018]: Zhou, C. W., Li, Y., Burke, U., Banyon, C., Somers, K. P., Ding, S., ... & Curran, H. J. (2018). An experimental and chemical kinetic modeling study of 1, 3-butadiene combustion: Ignition delay time and laminar flame speed measurements. Combustion and Flame, 197, 423-438.

[^STW2016]: G.P. Smith, Y. Tao, and H. Wang, Foundational Fuel Chemistry Model Version 1.0 (FFCM-1), http://nanoenergy.stanford.edu/ffcm1, 2016.

[^LDH2013]: Lam, K. Y., Davidson, D. F., & Hanson, R. K. (2013). A shock tube study of H2+ OH -> H2O+ H using OH laser absorption. International Journal of Chemical Kinetics, 45(6), 363-373.

[Henry Curran]: https://www.nuigalway.ie/our-research/people/chemistry/henrycurran