---
layout: post
title:  "clinic calculator"
list_title: project
date:   2015-04-06 20:46:20 +0100
categories: jekyll update
---
Clinic calculator was the first project and although simple in scope, ended up being a deep dive into what a date means, and what age is.

## The clinical need

Accuracy about age in adult medicine is not hugely important, but age in paediatrics is. The younger you are, the more significant each day becomes, and therefore the more important accuracy is. In clinic, paediatricians count the days in the babies, the weeks and months in the infants, and then the years and the months pretty much up until you are 18y. 

You can always tell a medic who is not used to paediatrics because they struggle to age the patient. Unless they have spent a long time around children, they can't eyeball them and guess the age and round to months; what is more, the default phrase in adults - 'a 75y old man' or 'a 32 year old woman' which rolls off the tongue, makes it hard to retrain yourself into saying '18 month old child'. The doctors new to paediatrics in handover, already under pressure presenting something unfamiliar, stumble at the start with phrases like '14 month year old'. Convention is that we talk in days for the first 2-3 weeks of life, weeks and months for the first maybe 3 months and then months alone up until 2 years, with years and months after that. Of course not all do this, but it is a rule of thumb. If you are presenting a child who is 60 weeks old, you probably do not work routinely in paediatrics and are reading the age off the computer.

And who is it that writes the computer program? Well you can bet your mortgage it won't have been a medic, and in all likelihood details like this would not have made it as far as the medical advisor and would have been one of those many decisions developers make without consulting their users. And it is frustrating if you routinely rely on the computer calculated values if they are not expressed in units you routinely work with. A child who is 51 weeks old we would usually say is 11 months old or maybe a year. The child who is reported as being 64 days old would be more understood as being 2 months old.

So it is a detail, but when using software to run a clinic or a ward, it grates when the software you use to document your work doesn't even understand the information you need to do it.

## Extra complexity

Premature babies add even more complexity to the mix. A baby born before term is generally described in terms of their gestational age - that is how many completed weeks and days of a 40 week pregnancy. Parents might think of their baby as being born 14 weeks early, but their paediatrician would not - they would be mentally translating that into 26 weeks. Weeks of gestation have very specific meanings to paediatricians, because the medical problems accompanying the premature delivery of a baby at 23+5 weeks are very different to a baby born at 36+3. At 23+5, the registrar, SHO and possibly consultant would be present with the crash team and equipment. At 36 weeks, depending on the circumstances, only the SHO would be standing at the resuscitaire.

A typical ward round on the neonatal unit would begin with the SHO presenting the baby, starting with gestation at birth, days of life and corrected age.
>'This is James, born at 24+3, now D25, corrected age 28 weeks.'

In that short sentence everyone automatically knows what sort of issues would have been encountered over the last 3 weeks, and what the journey over the next 3 weeks is likely to look like.

This introduces the concept of 'corrected gestational age'. Clearly a 3 week old baby who was born at 24 weeks gestation, the threshold of 'viability', cannot be compared with a 3 week old born at term. So their **chronological** age is the same, but much more information can be gathered if their **corrected** age is also used. A baby who is 3 weeks old, correcting now to 27 weeks cannot be expected to hit the same developmental milestones as a term baby of the same age, for example. 

Few health care IT systems get this - they are generally built around adults, and the same prejudices that exist in medicine around children (that they are just scaled down adults) percolate through into software, which is usually built with the arrogance. The exception is [Badgernet](https://www.clevermed.com/badgernet/), a nationally-used service for neonatal medicine. Here the details have been carefully thought about. But not everyone has BadgerNet and many have to make do with whatever outmoded monolithic system was commissioned in the late 90s and will never be personalised to the needs of its users.

### Time of birth

In neonatal medicine, even the hours matter - to the extent that babies born after midday might be considered to be day 0 until midnight. Referring to them as D2 the following morning on the ward round might otherwise not make sense if they are less than 24 hours old at the time. Some medical problems, such as jaundice for example, take on a whole new meaning if onset is in the first 24 hours rather than beyond.

### Decimal age

This will be covered later when discussing growth charts, but a way of standardising time when plotting measurements against age is to convert the age to decimal. Years afterall are not the same length (there is a leap year ever 4th year) and months also vary. To over come this, decimal age is used in some areas of medicine, especially paediatric endocrinology, when small increments in height over time might mean the difference between normal height velocity and growth failure. To calculate the velocity, time elapsed is easier to calculate if you know the decimal age at which each measurement is captured.

## Age, Time and software

Like all measurements and units, the measurement of time is political. The Gregorian calendar was introduced by Pope Gregory XIII in 1582, and replace the Julian calendar. It standardised a year to 365 days, which was not quite a tropical year (time required for the earth to go round the sun). The inaccuracy accumulates over 4 years so this is reset by adding an extra day once every 4 years, the leap year. This kind of innaccuracy is hard to allow for in computers, particularly since time is such a critical metric for all the systems that sit on top this function. In computer time is stored as a single number, the number of milliseconds upto or since [Unix Epoch time](https://en.wikipedia.org/wiki/Unix_time), Thursday 1st January 1970.

Calculating someone's age therefore requires 2 dates and times which can then each be expressed in milliseconds since Epoch time and then it is easy to subtract one from the other, and then convert back to a date. Fortunately there are libraries for this.

Clinic calculator

Sitting in clinic once, faced with a 38 day old baby, born at 28+5 weeks, trying to work out if they should yet be smiling and when their first primary immunisations should start, made me realise how useless the electronic record I had in front of me was. It had no concept of prematurity or capacity to explain what 38 days was in months, let alone flag to me when immunisations might be due. So this frustration turned into my first journey into software, and android dev. This was much more accessible the iOS since I did not have a shiny mac and that was a prerequisite for working with Apple phones.

![clinic-calculator]({{ '../assets/img/cliniccalculator.png' | relative_url }})

Available for download [here](https://play.google.com/store/apps/details?id=com.eatyourpeas.cliniccalculator&hl=en&gl=US), it still works and still meets a need, sadly, although it has been on the store for a long time. 