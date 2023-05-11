---
layout: default
title: Home
nav_order: 0
permalink: /
usemathjax: true
---

# Foundational Fuel Chemistry Model Version 2.0 (FFCM-2)
{: .fs-8.5 }
Foundational Fuel Chemistry Model Version 2.0 (FFCM-2) is an uncertainty-minimized reaction model for the combustion of hydrogen, carbon monoxide and small, foundational hydrocarbon fuels (up to C<sub>4</sub>). The model was optimized and validated against legacy combustion targets that cover a wide range of thermodynamic conditions.
{: .fs-6 .fw-300 }

[Download model](/docs/Downloads){: .btn .btn-primary .fs-5 .mb-4 .mb-md-0 .mr-2 }
[Citation](#how-to-cite){: .btn .btn-primary .fs-5 .mb-4 .mb-md-0 .mr-2 }
[Performance](/docs/Results){: .btn .btn-primary .fs-5 .mb-4 .mb-md-0 .mr-2 }
[Release notes](/docs/ReleaseNotes){: .btn .btn-primary .fs-5 .mb-4 .mb-md-0 .mr-2 }

---

{: .note }
The combustion reaction chemistry community commonly uses the wording **reaction mechanism** to describe the fundamental combustion chemistry. We prefer the use **reaction model**. A mechanism describes how nature works; a model tries to describe and mimic that nature.

## The FFCM project
The Foundational Fuel Chemistry Model (FFCM) project is the result of a long-term research collaboration between Prof. [Hai Wang][Hai Wang]’s research group at Stanford University and Dr. [Gregory Smith][Gregory Smith] of the [SRI International][SRI International]; Its primary objective is to advance an accurate, uncertainty-minimized reaction model for combustion of small hydrocarbon fuels by assimilating large sets of legacy fundamental combustion property data into the state of knowledge of elementary reaction kinetics. The current FFCM Version 2 [(FFCM-2)][FFCM-2] extends from the previous FFCM Version 1 [(FFCM-1)][FFCM-1] effort to cover a wider range of relevant C<sub>0</sub>-C<sub>4</sub> fuels.

### The current FFCM-2 release
- consists of 96 C<sub>0</sub>-C<sub>4</sub> species and 1054 reactions.
- is optimized against 1192 sets of fundamental combustion data that span a wide range of thermodynamic conditions, including laminar flame speeds, shock tube ignition delay time and speciation profiles in shock tube or flow reactor for foundational fuels up to C<sub>4</sub> species.

## The FFCM research team
### Current members
<style>
* {
  box-sizing: border-box;
}
/* Create four equal columns that floats next to each other */
.column {
  float: left;
  width: 25%;
  padding: 20px;
}
/* Clear floats after the columns */
.row:after {
  content: "";
  display: table;
  clear: both;
}
</style>
<div class="row">
  <ul>
  {% for member in site.data.members %}
    {% if member.status == "current" %}
    <div class="column">
      <li>
      <div style="text-align:center">
        <a href="{{ member.website }}">
          <img class="staffer-image" src="{{ page.baseurl }}{{ member.photo }}" alt="">
        </a>
        <h3 class="staffer-name">
          <a href="{{ member.website }}">{{ member.name }}</a>
        </h3>
        {{ member.affiliation }}
        {{ member.email }}
      </div>
      </li>
    </div>
    {% endif %}
  {% endfor %}
  </ul>
</div>

### Previous members
<style>
.column {
  float: left;
  width: 25%;
  padding: 5px;
}
</style>
<div class="row">
  <ul>
  {% for member in site.data.members %}
    {% if member.status == "previous" %}
    <div class="column">
      <li>
      <div style="text-align:center">
        <a href="{{ member.website }}">
          <img class="staffer-image" src="{{ page.baseurl }}{{ member.photo }}" alt="">
        </a>
        <h3 class="staffer-name">
          <a href="{{ member.website }}">{{ member.name }}</a>
        </h3>
        {{ member.affiliation }}
        {{ member.email }}
      </div>
      </li>
    </div>
    {% endif %}
  {% endfor %}
  </ul>
</div>


## How to cite
### Citation in APA format
```
Y. Zhang, W. Dong, L. Vandewalle, R. Xu, G.P. Smith and H. Wang, Foundational Fuel Chemistry Model Version 2.0 (FFCM-2), https://web.stanford.edu/group/haiwanglab/FFCM2/pages/FFCM2.html, 2023.
```
### Citation in Bibtex format
```bibtex
@Article{ZDV2023,
  author  = {Zhang, Yue and Dong, Wendi and Vandewalle, Laurien and Xu, Rui and Smith, Gregory and Wang, Hai},
  title   = {Foundational {Fuel} {Chemistry} {Model} {Version} 2.0 ({FFCM}-2)},
  journal = {https://web.stanford.edu/group/haiwanglab/FFCM2/pages/FFCM2.html},
  year    = {2023},
```

## Acknowledgements
The FFCM effort started in 2011 as a part of the work of the [DOE Combustion Energy Frontier Research Center (CEFRC)][CEFRC]. The work continued with support from the [Air Force Office of Scientific Research (AFOSR)][AFOSR] since 2012, and more recently the [Office of Naval Research (ONR)][ONR]. During the process, many researchers have contributed to the outcome of the model, notably

- Dr. [Enoch Dames][Enoch Dames] contributed to the original version of the FFCM-1 trial model through a critical review of some of the rate coefficient assignments.

- Dr. [Elke Goos][Elke Goos] of [DLR-Institute of Combustion Technology][DLR] and Dr. [Branko Ruscic][Branko Ruscic] of [Argonne National Laboratory][Argonne National Laboratory] provided the thermochemical data for FFCM-1.

- Prof. [Ronald K. Hanson][Ronald K. Hanson] and Dr. [David F. Davidson][David F. Davidson] of [Stanford University][Stanford University] measured some of the key reaction rate coefficients for FFCM-1.

- Prof. [Fokion N. Egolfopoulos][Fokion N. Egolfopoulos] of [University of Southern California][University of Southern California] provided useful discussion of the laminar flame speed data.

[Hai Wang]: https://nanoenergy.stanford.edu
[Gregory Smith]: https://www.sri.com/about/people/gregory-smith
[Ronald K. Hanson]: https://profiles.stanford.edu/ronald-hanson
[David F. Davidson]: https://profiles.stanford.edu/david-davidson
[Fokion N. Egolfopoulos]: http://ame-www.usc.edu/personnel/egolfopoulos
[Elke Goos]: http://www.dlr.de/vt/en/desktopdefault.aspx/tabid-7603/12862_read-32396
[Branko Ruscic]: http://atct.anl.gov/~ruscic/
[Enoch Dames]: https://www.linkedin.com/in/enochdames/
[Stanford University]: http://www.stanford.edu
[CEFRC]: https://www.princeton.edu/cefrc/
[AFOSR]: http://www.wpafb.af.mil/afrl/afosr/
[ONR]: https://www.nre.navy.mil/
[Argonne National Laboratory]: http://www.anl.gov
[SRI International]: http://www.sri.com
[University of Southern California]: http://www.usc.edu
[DLR]: http://www.dlr.de/vt/en/DesktopDefault.aspx/18902_read-43899/
[FFCM-1]: https://web.stanford.edu/group/haiwanglab/FFCM1/pages/FFCM1.html
[FFCM-2]: /