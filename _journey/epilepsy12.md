---
layout: project
title: 'epilepsy12'
repository: 'N/A'
issues: 'N/A'
app_url: '[Epilepsy12](https://e12.rcpch.ac.uk/account/login/?next=/)'
docs: 'https://e12.rcpch.ac.uk/docs/'
status: 'live'
---
The [Epilepsy12 National Audit](https://www.rcpch.ac.uk/work-we-do/clinical-audits/epilepsy12) is a national project, funded by [HQIP](https://www.hqip.org.uk/a-z-of-nca/national-epilepsy-12-audit/) and delivered by the Royal College of Paediatrics and Child Health. This was the first big project the [RCPCH Incubator](https://playbook.rcpch.tech/) undertook after the success of the [Growth Charts]({% link _journey/growth-charts.md %}).

RCPCH had previously subcontracted Epilepsy12 to a supplier but now sought greater control over the content, as it already had an audit department and a committee of clinicians that decided on the audit questions and data analysis. It made sense that they would want to build the platform in house to have greater control over how data was collected and reported.

## Python

Given the previous project had been in python, we chose to use python for this. Resolutely open source, we wanted to encourage clinicians and others to be involved in the build and be able to feed back quickly to speed up the development cycle. This was before LLMs were on the scene and being agile was not always easy with multiple stakeholders. Python is taught in schools and if clinicians have done coding before, they are likely to have learned python, so this was a major reason for using it. And python and the large community that support it is built on open source principles which was important to us. 

We therefore chose Django - it is well respected, has a large community supporting it, plenty of plugins and libraries and is secure and well-maintained. Django was a good fit.

## Audit Platforms

Audits are powerful levers of change in clinical medicine - they are part of the governance strategy that allows government to standardise care across the country, to measure what centres are doing and make sure that people are meeting a minimum standard. Results of audits are analysed and if a centre is an 'outlier' this is reported to the lead clinician and the hospital chief executive so that changes, and if necessary extra investment, can be made to improve things. National audits measure standards of care which are agreed and include clinical outcomes and patient feedback.

But this means clinicians have to find time to fill out the audit, and as clinicians ourselves, we were keen to ensure the platform was nice to use, as intuitive as possible, and importantly reported back in real time results to clinicians so that they could have insights from their data that would allow them to local patterns that might allow them to improve things before the reports were published. 

## Design

Filling out audits as a busy clinician is a time pressure that for most is not covered in the job plans. In some centres extra resource in the form of admin is provided, but mostly it falls to the lead clinician and maybe the nursing teams. It was a key requirement therefore that the screens were reactive and while the layout was chronological or reflected care processes, we all knew that in real life things do not always happen in a linear fashion. The scan might be booked but the result takes time to come back so the platform had to be able to save as you went, leave gaps for when things were missing and signpost to clinicians which things were missing.

![epilepsy12-dashboard]({{ '../assets/img/e12-dashboard.png' | relative_url }})
![epilepsy12-submissions]({{ '../assets/img/e12-submissions.png' | relative_url }})
{: .figure-pair}

In the process of a child's first year of care therefore we broke the questions into sections. had question counters with dials and progress bars and flags to show that questions were answered or yet to answer, and if answered had they passed the measure or not. 

## Methodology

Following on from our approach as a small team working on the growth charts we reused the same workflow. There was a project board of engaged experts that oversaw quality and standards, and a smaller development board that met more often and worked in an agile way to set goals, raise issues and close them. We met (and continue to meet) regularly to go through the issues of github and set tasks for the next sprint. 

## Outcomes

Epilepsy12 is now in it's 2 year and engagement with the audit is up over 90%. In 2025 there were record numbers of returns and generally feedback is positive.