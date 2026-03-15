---
layout: project
title: 'National Paediatric Diabetes Audit (NPDA)'
repository: '[NPDA](https://github.com/rcpch/national-paediatric-diabetes-audit)'
issues: '[Issues](https://github.com/rcpch/national-paediatric-diabetes-audit/issues)'
app_url: '[Epilepsy12](https://e12.rcpch.ac.uk/account/login/?next=/)'
docs: 'https://e12.rcpch.ac.uk/docs/'
status: 'live'
---
## Background

NPDA followed hot on the heels of Epilepsy12. Pleased with the success of E12 RCPCH looked to repeat the same with NPDA - again a national audit which RCPCH oversaw, but where bringing it inhouse would improve oversight of data collection. 

## Django

By now the [RCPCH Incubator](https://playbook.rcpch.tech/) were familiar with Django, and the team had grown. We now had a real developer, [Michael Barton](https://github.com/orgs/rcpch/people/mbarton) who took over the leadership of the team, bringing with him extensive knowledge and experience of software from industry.

## Children's Diabetes

I had a particular interest in this project as had worked as a diabetes doctor for children for many years and submitted data to the NPDA myself. Standards of care in children's diabetes had seen huge changes since 2010 as consequence of national investment in hospital services. This saw introduction of national networks for centres providing diabetes care for children, peer reviews of all centres and introduction of the NPDA to measure outcomes. In parallel though the medicine itself had changed and so the investment was made because of the recognition in adults that more intensive treatment led to better outcome. Intensification of treatment though meant diabetes services could nolonger be just delivered by a doctor and a nurse - dose adjustment, carbohydrate counting (and in time, technology), psychological support all needed a bigger team and this led to new ways of working as well as more scrutiny. The effect, over the next 15 years, was a huge improvement in outcomes in children's diabetes.

## The National Paediatric Diabetes Audit

The NPDA was in a more mature state than Epilepsy12 had been. It had been running for longer, and services were familiar already with the measures. Whereas Epilepsy12 audited the first year of care of children presenting for the first time with epilepsy, NPDA sought to be a registry of all children under 18 y with all types of diabetes, and set and measure standards of care for them. The dataset was already quite detailed and implementation for this reason was much quicker - partly because we had done it before, partly because NPDA had been running for longer.

![npda]({{ '../assets/img/npda.png' | relative_url }})

A complexity of NPDA is that users enter data not just through an online form but mostly through csv uploads. This meant an API that would parse CSVs, extract fields and populate tables.

## Why not an API

A lesson for me has been that technical solutions to problems have to be pragmatic. Although we are asking clinicians to enter data when they are already busy and possibly entering the same data already into a clinical records, the reality is that they have existing workflows that generate csvs. It is not that easy to change that. Also, although the data is entered twice (in the EHR and into the CSV), creating an API to pull data directly from the EHR is also not practical (although I have implemented this). The data required for the NPDA is often not stored in a structured way in the EHR, and there are so many different EHRs that it is not practical to expect many to use an API directly.

## Reporting

So while we built an API, no one has used it, but instead there is a web form that accepts the same data as can be uploaded as csv. A nice extra is that by accepting postcodes for children we can map where children are in a locality, so clinicians can calculate distance to clinic, index of multiple deprivation and so on.

## Methodology

In the same way as Epilepsy12 and the Growth Charts before it, there was a process of having a development board who did the work, overseen by the Project board, diabetes experts that would sign off the quality and execution.

## Outcomes

NPDA is just now entering its second year and the data from year one are in but not yet analysed.