---
layout: default
title: Stanford Fundamental Combustion Property Database
parent: Experimental Data
nav-order: 1
---

# Stanford Fundamental Combustion Property Database

## What's new and unique about SFCPD?

### Broad coverage
The Stanford Fundamental Combustion Property Database consolidates legacy data that date back to 1937. A total of 342 research articles and all listed databases were evaluated. The database covers all relevant C<sub>0-4</sub> foundational fuels and relevant property includes
- Laminar flame speed
- High-temperature shock tube ignition delay times
- Shock tube species time-history measurements

and selected

- Low-pressure burner stablized flames
- Flow reactor species time-history measurements


In the current work, the shock tube ignition delay measurements for temperature T<sub>5</sub> below 1000 K and rapid compression machine (RCM) data are not considered. 

### Flexible formats for both human and machines
- The current database is hosted using the Python Data Analysis Library ([pandas][pandas]), which provides flexible and useful tools for data analysis and manipulation. The library is written in Python and can be readily interfaced with other Python-based softwares to automate the pipeline for kinetic model development, including Cantera for kinetic modeling, PyTorch for neural network training and Numpy/Scipy for optimization and uncertainty minimization. 

- To facilitate the human interaction with the database, we developed tools that converts the pandas database to and from the SpreadSheet, which is more human readeable to allow experimentalists to share their data more easily. 

### Target selection
A number of 1192 targets are selected for optimization. They span a wide range of thermodynamic conditions and fuels, including

- Laminar flame speed: 380
- Ignition delay time: 792
- Flow reactor species time-history: 4
- Shock tube species time-history: 12
- Burner stabilized flames: 4

The conditions can be found at the validation page. 

In general, we only consider data for neat fuels as targets. The fuel blend data, including natural gas, are used for additional test. Also, the target list only contains shock tube measurements with argon as bath gas. The nitrogen diluted mixtures are used for additional test.  

[pandas]: https://pandas.pydata.org