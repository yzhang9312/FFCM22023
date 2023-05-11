---
layout: default
title: History of Kinetic Database
parent: Experimental Data
nav-order: 4
---

# History of Combustion Property Database Development
A brief history of the development of combustion property database for kinetic modeling
{: .fs-6 .fw-300 }

Researchers started to publish fundamental combustion property data many decades ago[^S1937], yet the efforts for developing comprehensive and standardized combustion kinetic experimental databases have not been made until recent years[^F2007]$^{,}$[^DH2005]$^{,}$[^PSF2019]$^{,}$[^OZP2014]$^{,}$[^WN2018]. To facilitate kinetic model optimization and validation, the legacy combustion property data need to be consolidated with data uncertainty evaluated and the format of database needs to be designed for easy access by both human and computer codes. Herein, we highlight the key features of some existing efforts.

- **Review papers:** Every other year, a few review papers were published to consolidate the laminar flame speed data. In 2012, Ranzi et al.[^RFG2012] consolidated and reviewed selected laminar flame speed measurements for hydrocarbon and oxygenated fuels between 1990 and 2011. The review was conducted in a hierarchical sequence, including selected foundational C<sub>0-4</sub> species, large hydrocarbons (primary reference fuels, cyclo-alkanes, heavy normal-alkanes and aromatics) to alcohols and oxygenated species and fuel blends. Key reactions for modeling laminar flame speeds were also discussed. In 2018, Konnov et al. [^KMK2018] reviewed the advances in experimental techniques in determining flame speed. Data were collected and reviewed for selected single component fuel/air mixtures (e.g., H<sub>2</sub>, CH<sub>4</sub>, higher alkanes, DME, liquid alkanes and alchohols) from literature in the past three decades. For both papers, the reviewed data are publicly available in the format of Spreadsheet.

- **PrIMe:** In 2006, Frenklach and coworkers[^F2007] released Process Informatics Model (PrIMe), which was the pioneering work for designing a kinetic database. PrIMe used the format of eXtensible Markup Language (XML) to incorporate fundamental combustion experimental data, along with reaction models and simulation results. It was web-based and the objective was to spread the idea of collecting kinetic data and transform data into kinetic knowledge. 

- **CloudFlame:** Started in 2013, the CloudFlame open database was organized by the Clean Combustion Research Center at King Abdullah University of Science and Technology (KAUST). Data published in a few literature were digitized and stored in the format of Comma-Separated Values (CSV) file. 

- **ReSpecTh:** Started in 2014, Turanyi and coworkers[^OZP2014] developed the ReSpecTh database. The latest version includes literature data for H<sub>2</sub>, syngas, CH<sub>3</sub>OH, C<sub>2</sub>H<sub>5</sub>OH and CH<sub>4</sub> up to 2019. Similar to the PrIMe work, ReSpecTh also used the XML format to facilitate the data access by computer codes. In ReSpecTh, selected metadata of experiments are added to the database.

- **ChemKED:** In 2018, Weber and Niemeyer [^WN2018] initiated the ChemKED effort to standardize the data format that are both human- and machine-readable. They leveraged the format of yet another markup language (YAML). Compared to the XML format, the YAML format makes it easier for researchers to collaborate on the database files. At the current stage, the experimental data stored in this format is limited. 

- **FKDUSTM:** Since 2005, Prof. Hanson and coworkers of Stanford University summarize the ignition delay times, species time-histories, and reaction rate measured in the Stanford shock tube lab and released the Fundamental Kinetic Database Utilizing Shock Tube Measurements[^DH2005]. The database has been updated from time to time and so far it covers the data from 1974 to 2019 inclusively. The data are stored mainly in word documents or Portable Document Format (PDF). The format is more human-readable than XML, but difficult for the interaction with computer codes.

In summary, each database partially covers some legacy data of foundational fuels, but none of the existing efforts incorporate all targets needed for FFCM-2 development (laminar flame speeds, shock tube ignition delay and species time-history profile for all C<sub>0-4</sub> foundational fuels). It motivates us to develop the Stanford Fundamental Combustion Property Database.

## References
[^S1937]: Smith, F. A. (1937). Problems of Stationary Flames. Chemical Reviews, 21(3), 389-412.

[^DH2005]: Davidson, D. F., & Hanson, R. K. (2005). Fundamental kinetics database utilizing shock tube measurements. Mechanical Engineering Department, Stanford University, Stanford CA.

[^PSF2019]: Pelucchi, M., Stagni, A., & Faravelli, T. (2019). Addressing the complexity of combustion kinetics: Data management and automatic model validation. In Computer Aided Chemical Engineering (Vol. 45, pp. 763-798). Elsevier.

[^F2007]: Frenklach, M. (2007). Transforming data into knowledge—process informatics for combustion chemistry. Proceedings of the combustion Institute, 31(1), 125-140.

[^OZP2014]: Olm, C., Zsély, I. G., Pálvölgyi, R., Varga, T., Nagy, T., Curran, H. J., & Turányi, T. (2014). Comparison of the performance of several recent hydrogen combustion mechanisms. Combustion and Flame, 161(9), 2219-2234.

[^P2019]: Pelucchi, M., Stagni, A., & Faravelli, T. (2019). Addressing the complexity of combustion kinetics: Data management and automatic model validation. In Computer Aided Chemical Engineering (Vol. 45, pp. 763-798). Elsevier.

[^WN2018]: Weber, B. W., & Niemeyer, K. E. (2018). ChemKED: A Human‐and Machine‐Readable Data Standard for Chemical Kinetics Experiments. International Journal of Chemical Kinetics, 50(3), 135-148.

[^RFG2012]: Ranzi, E. L. I. S. E. O., Frassoldati, A., Grana, R., Cuoci, A., Faravelli, T., Kelley, A. P., & Law, C. K. (2012). Hierarchical and comparative kinetic modeling of laminar flame speeds of hydrocarbon and oxygenated fuels. Progress in Energy and Combustion Science, 38(4), 468-501.

[^KMK2018]: Konnov, A. A., Mohammad, A., Kishore, V. R., Kim, N. I., Prathap, C., & Kumar, S. (2018). A comprehensive review of measurements and data analysis of laminar burning velocities for various fuel+ air mixtures. Progress in Energy and Combustion Science, 68, 197-267.