---
layout: project
title: 'CheckTick'
repository: '[ChecTick](https://github.com/eatyourpeas-ltd/checktick)'
issues: '[Issues](https://github.com/eatyourpeas-ltd/checktick/issues)'
app_url: '[CheckTIck](https://checktick.uk/home)'
docs: 'https://checktick.uk/docs'
status: 'live'
---

## Background

This is the first big project for Eatyourpeas, and is heavily supported with the advent of LLMs and agents which became increasingly popular in the second half of 2025. 

There is a big need for good quality, secure, survey platforms in health care, but actually there really aren't any. There are some but they are tend to be hosted by universities if they are to have the protections and security required by the NHS, and even then they are not really optimised for healthcare.

## Why is Healthcare special?

### Security

Hosting patient data can only be in the UK and has to meet all the requirements of the [Data Protection Security Toolkit](https://www.dsptoolkit.nhs.uk/). Then there is [GDPR](https://gdpr-info.eu/), as well as research governance requirements. To meet all of these CheckTick encrypts all data end to end, has been fully pen tested and has cyberessentials accreditation.

### Datasets

Medical surveys are different to regular surveys. The datasets that populate the dropdowns are often standardised (think lists of hospital trusts, or blood groups) - some are published by the [NHS Data Dictionary](https://digital.nhs.uk/data-and-information/data-tools-and-services/data-services/hospital-episode-statistics/hospital-episode-statistics-data-dictionary) but there are other datasets which are all collected by CheckTick.

It is common to survey clinicians and want to know where they work, which NHS region and so on. CheckTick has custom question groups for collecting standard information about clinicians or patients.

### Standardised Questionnaires

In research it is quite common to require standardised questions as part of a broader questionnaire - for example the PHQ-9 psychological health questions or the SDQ (Strengths and Difficulties). CheckTick hosts these and offers users the option to share question groups for others to use.

### Tools

Postcodes are usually collected because researchers or clinicians want to collect index of multiple deprivation. Or they might want to know what local authority or local health board they live in. Calculations like these are handled within CheckTick.

### Survey Types

Survey builders typically offer different question types - multiple choice, lickert scales, dropdowns and so on. CheckTick supports these, but also entering data to build a survey in this way is time-consuming. Mostly when designing a survey, often with colleagues, a word document is shared where questions and answer types are circulated. CheckTick supports a special markdown format where questions can be imported directly from text - much quicker that dragging and dropping. There is even an option to outsource the creation of a survey to an LLM that generates the syntax automatically.

### Languages

In Health Care it is common to run surveys across communities of patients from different cultural backgrounds. CheckTick uses an LLM to generate translations of surveys (which ideally should be checked by a native speaker) so that the same survey can be run in multiple languages at the same time. 

### Accessibility

In Health Care, similarly, patient surveys are held to a higher standard as patients may have disabilities so surveys need to be able to meet accessibility standards. The WCAG 2.1 AA standards are the requirement for health care applications and CheckTick meets all of these.

## Open Source

CheckTick is published in the open under the AGPL license on GitHub and can used for free with exhaustive documentation to support this.
