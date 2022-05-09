---
title: "Op-Ed Research Summary"
subtitle: "Water Conservation Through Reducing Greywater"
author: Thomas Knudson
papersize: a4
geometry: margin=2cm
bibliography: OpEdSources.bib
header-includes: |
    \usepackage{fancyhdr}
    \pagestyle{fancy}
    \fancyhead[RO,RE]{GEOG 300, S2022}
    \fancyhead[CO,CE]{Op-Ed Research Summary}
    \fancyhead[LO,LE]{Knudson}
    \usepackage{setspace}
---

\onehalfspacing

## OSU's Potable Water Use as a Case Study

- STARS reports that OSU used $202,819,452$ Gallons of potable water during the period of July 1 2019 to June 30 2020, which amounts to $555,670$ Gallons (of potable water) per day [@stars].
- As a baseline (first reported measurements to STARS), OSU used $267,228,984$ gallons of potable water from July 1 2004 to June 30 2005 [@stars].
- OSU has reduced its water consumption by $39.56\%$ (comparing 2019-2020 to 2004-2005) [@stars].
- OSU reports that rainwater collected on campus is filtered and stored inside a 16,500 gallon cistern located in the Kelley Engineering building for flushing the toilets and urinals [@stars]. 
  - Only used for Kelley [@osu].
- OSU is supplied water from Oak Creek, distributed by the City of Corvallis, for use on campus [@osu].
- "In fiscal year 2010, OSU used over 230 million gallons of treated water.  Expenses related to water (both supply and sewer) totaled nearly $1.5 million during that period." [@osu]

## How Can We Do Better? 

### Dual-flush Toilets 

- "Due to the high water consumption for toilet flushing (pointed by studies on water end-uses quoted herein), it was considered that dual-flush toilets are the devices with the greatest potential for potable water savings." [@ReducingPotable]
- "According to SABESP (2008), dual-flush toilets reduce water consumption by 50–75%, compared with conventional toilet flushing devices." [@ReducingPotable]
- @DualFlush find a $20\%$ reduction in water usage for homes either initially or retroactively fitted with low-flow toilets.
- Higher efficiency water devices don't necessarily lead to less consumption and is difficult to measure statistically [@PotableSavings, p. 2].
  - Showers, washing machines, etc.
- "The coefficient on the dual-flush/efficient toilet dummy variable is -0.249 which is negative and statistically significant at the 1% level. This indicates that the presence of a water efficient toilet reduces household water consumption by about 25%. By contrast, neither efficient shower heads nor rainwater tanks have a statistically significant effect on household water consumption" [@PotableSavings, p. 8]

### Reducing Potable Water Consumption

- In @ReducingPotable, suggests three alternatives to reduce potable water consumption: adoption of dual-flush toilets, reuse of greywater (for flushing), and rainwater collection (for flushing). 
- The authors note a preference for the first two options, as the use of rainwater for flushing does not reduce the overall amount of greywater generated (but does reduce the demand for potable water) [@ReducingPotable].
- Market-based approaches (increased cost to discourage water use) is not equitable. Public goods, such as water, either should not or are reasonably prevented by policy from disproportionately impacting low-income households [@DualFlush, p. 13].
- Policy doesn't always have the desired effect: "Renwick and Archibald (1998) found that low-income households in two Southern California communities were more price-responsive than high-income households, reflecting water expenditures’ larger share of the household budget. Thus, if water demand management occurs solely through price increases, low-income households will contribute a greater fraction of the cities’ aggregate water savings than high income households." [@DualFlush, p.14]

## Estimating the Impact of Overhauling OSU's Toilets

- Current designs use between $3$ and $9$ liters of water per flush, whereas vacuum toilets use between $0.8$ and $1.5$ liters [@PracticalPerformance, p. 1].
- Vacuum dual-flush toilets use $0.7$ liters for a regular flush and $0.4$ liters for the reduced flush [@PracticalPerformance, p. 3].
- Using the STARS report of $202,819,452$ Gallons for the 2019-2020 [@stars], we can convert this to best and worst case scenarios of potable water being used per flush, using @PracticalPerformance 's data.
  - $7.678 \times 10^8$ Liters
  - Do some calculations in Excel to compare how many gallons (or liters) of water could be saved by examining a variety of cases (best and worst for each assumed amount of total usage was for toilets in increments of $10\%$ of total). 

# References

$$\ $$

\bibliography{OpEdSources}
