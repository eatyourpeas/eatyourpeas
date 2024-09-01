---
layout: page
title:  "children's growth charts"
---

Over the years I have had several goes at growth charts. There are implementations in node.js, sqlserver and visual basic. In 2019/2020, the [Royal College of Paediatrics](https://www.rcpch.ac.uk) were looking to digitize the charts that they had developed in the 1980s and published on paper.

[Marcus Baw](https://github.com/pacharanero) and I teamed up to build them.

## Complexity

The are a handful of implementations of children's growth charts, and all of these are based on a statistical technique to chart biological data known as the LMS method, developed by [Professor Tim Cole](https://github.com/statist7). This compresses the reference data into 3 values for each age interval, and these can be used to calculate a centile and SDS for any measurement against an age, sex and gestation at birth.

Rather than bundle the complicated calculations into the charts and publish as a standalone application, RCPCH took the unique step of separating the calculation logic from the charting and publishing the caclulation as an API. 

This is the first proper production level project I had been involved in, and as a small agile team, Marcus and I put the project together inside of 18 months, together with a full suite of tests, continuous integration, [documentation and a demo site](https://growth.rcpch.ac.uk).
