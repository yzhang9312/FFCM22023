---
layout: default
title: Reactions and Rate Constants
parent: Trial Model
nav_order: 1
---

The table lists all reaction pathways, the rate parameters and the uncertainties for the trial FFCM-2.

- In the column of **Rate Constants**
  - $A$: pre-exponential factor ($A$-factor) with unit cm$^3 \cdot$ mol $\cdot$ s;
  - $n$: temperature dependency;
  - $E$: activation energy with unit J $\cdot$ mol$^{-1}$.
- $f$ represents the uncertainty of the pre-exponential factor
- 

<link href="https://cdn.jsdelivr.net/npm/bootstrap@5.1.3/dist/css/bootstrap.min.css" rel="stylesheet" integrity="sha384-1BmE4kWBq78iYhFldvKuhfTAU6auU8tT94WrHftjDbrCEXSU1oBoqyl2QvZ6jIW3" crossorigin="anonymous">
<link rel="stylesheet" href="https://cdn.jsdelivr.net/npm/bootstrap-icons@1.7.2/font/bootstrap-icons.css">
<link rel="stylesheet" href="https://unpkg.com/bootstrap-table@1.21.2/dist/bootstrap-table.min.css">
<!-- <link rel="stylesheet" type="text/css" href="extensions/filter-control/bootstrap-table-filter-control.css"> -->

<div class="table-responsive">
    <table
        id="table"
        data-toggle="table"
        data-show-toggle="true"
        data-search="true"
        data-height="900"
        data-width="100"
        data-strict-search="true"
        data-page-list="[25, 50, 100, all]"
        data-pagination="true"
        data-cookie="true"
        data-advanced-search="true"
        data-id-table="advancedTable"
        data-cookie-id-table="saveId"
        data-filter-control="true"
        data-filter-show-clear="true"
        data-show-search-clear-button="true"
        data-show-columns="true"
        data-show-columns-search="true"
        data-search-highlight="true"
        data-click-to-select="true"
        data-toolbar="#toolbar"
        data-page-size="30"
        data-escape="false"
        data-search-on-enter-key="false"
        data-show-filter-control-switch="true"
        data-url="/assets/data/trial_table.json">
        <thead>
            <tr>
            <th data-field="Index" data-halign="center" data-align="center">ID</th>
            <th data-field="Reaction" data-halign="center" data-align="center">Reaction</th>
            <th data-field="ReactionClass" data-halign="center" data-align="center">Species</th>
            <th data-field="Type" data-halign="center" data-align="center">Type</th>
            <th data-field="Species" data-halign="center" data-align="center">Keywords</th>
            <th data-field="Rates" data-halign="center" data-align="center">Rate Constants</th>
            <th data-field="Uncertainty" data-halign="center" data-align="center">$f$</th>
            <th data-field="Source" data-halign="center" data-align="center">Sources</th>
            <th data-field="Comments" data-halign="center" data-visible="false">Comments</th>
            </tr>
        </thead>
    </table>
</div>    

<script>
    $(function() {
      $('#table').bootstrapTable();
    })
</script>

<script src="https://cdn.jsdelivr.net/npm/jquery/dist/jquery.min.js"></script>
<script src="https://cdn.jsdelivr.net/npm/bootstrap@5.1.3/dist/js/bootstrap.bundle.min.js" integrity="sha384-ka7Sk0Gln4gmtz2MlQnikT1wXgYsOg+OMhuP+IlRH9sENBO0LRn5q+8nbTov4+1p" crossorigin="anonymous"></script>
<script src="https://unpkg.com/bootstrap-table@1.21.2/dist/bootstrap-table.min.js"></script>
<script src="https://unpkg.com/bootstrap-table@1.21.2/dist/extensions/filter-control/bootstrap-table-filter-control.min.js"></script>
<script src="https://unpkg.com/bootstrap-table@1.21.2/dist/extensions/toolbar/bootstrap-table-toolbar.min.js"></script>
<script src="https://unpkg.com/bootstrap-table@1.21.2/dist/extensions/cookie/bootstrap-table-cookie.min.js"></script>