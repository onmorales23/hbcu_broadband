---
title: Measuring Students' Access to Broadband at Historically Black Colleges and Universities (HBCUs)
subtitle: Proposal for AEFP 2024
author: Olivia Morales and Benjamin Skinner
date: 2023-10-07
bibliography: hbcu_broadband.bib
header-includes:
  - \usepackage[backend=biber, style=apa]{biblatex}
  - \usepackage{amsmath}
  - \usepackage{txfonts}
geometry: margin=1in
---

### Background ###

The economic, educational and social opportunities broadband access
brings to communities are indisputable [@tomer_etal_2020]. However, a
significant portion of the U.S. population still lacks stable access
to broadband internet in their home. In the higher education context,
broadband serves a vital role in sustaining the academic and
social mechanisms of a college/university. Simply put, reliable
broadband connections are nonnegotiable necessities for supporting the
work of students, staff and faculty at HEIs across the country.

The principal question then becomes, what does broadband access look
like in the U.S. and how should it be measured? In @skinner_2019,
multiple data sources were utilized to develop informed measures of
broadband at open-access institutions across the United States. These
different sources measure broadband access uniquely, through counts of
individuals with broadband in the home, upload/download speeds,
etc. Averaging and weighting these points (by distance/population)
resulted in a more comprehensive measure of broadband access for each
HEI featured in the analytic sample. This measure served as the
independent variable in the multiple Bayesian regression models
defined to estimate the relationship between broadband access and
students taking online courses at public, open-access institutions.

We hope to expand on the work done in @skinner_2019 by gauging
broadband access (via similar population/distance-weighted processes)
across a specific subset of institutions in the U.S.: HBCUs. Recent
spotlight on the inaccessibility of broadband at HBCUs across the
country warrants deeper empirical investigation. The McKinsey
Institute for Black Economic Mobility sounds the alarm on this issue
clearly; in their 2021 report, researchers found that 82% of HBCUs are
located in broadband deserts [@bevinsetal_2021]. Broadband deserts, as
defined by @mathewsali_2023, "lack readily available and affordable
access to high-performance broadband, with residents unable to
experience digital inclusion, digital equity and, ultimately, digital
dignity" (p.730). The dire broadband needs at HBCUs has even
prompted a comprehensive federal response with the
creation of the Office of Minority Broadband Initiatives under the
National Telecommunications and Information Administration (NTIA)
[@federalregister_2021]. Programs under this newly created office will
specifically address issues of broadband access in "vulnerable
communities", naming HBCUs as important stakeholders in accomplishing
this goal.

This focus on historically underserved and underfunded institutions
will shed light on large-scale inequities in access to broadband for
the most vulnerable student populations in the country. Previous
research highlights broadband disparities geographically [@larose_etal_2007;
@westkarsten_2016], but recent scholarship by @skinner_etal_2021 has
challenged this narrow view of broadband access by underscoring
inequities across racial/ethnic & socioeconomic subpopulations,
connecting this heterogeneity to historical redlining practices
determined by 20th century federal housing policy. Our project
supports the broader movement towards exploring nuance in the
broadband landscape, examining access through the intersections of
geography, institution type and student demographics.

### Research Questions ###

1. Does broadband access vary across student populations at HBCUs?
2. Does geography exacerbate broadband access inequities across HBCUs?

### Data ###

This paper will draw from three unique sources of data: the
Integrated Postsecondary Education Data System (IPEDS), ACS and the
FCC.

From IPEDS, we will be pulling unit identification numbers and
locations for institutions (via coordinates of latitude/longitude),
filtering institutions by HBCU status. ACS summary files will be
pulled to identify counts of individuals with broadband access in the
home at the block group level. FCC data contribute the final pieces to
the dataset, providing details of unique Internet Service Providers
(ISPs) and maximum/minimum download speeds at the block group level.

These multiple data sources will be utilized to eventually calculate
population- and distance-based weights via matrices. Combining these
weights will allow us to assign a more informative measure of
broadband access at HBCUs across the United States. These measures
will provide a descriptive picture of access to broadband at HBCUs,
with the ability to disaggregate measures by geography,
race/ethnicity, etc.

### Methods ###

The institution-level data from IPEDS will be pulled first, as that
contains the most basic information to properly locate each HBCU
available as reported by the National Center for Education Statistics
(NCES).

Next, we will pull block group-level information from ACS summary
files to identify block group centroids and counts of broadband access
in the home. The centroids, along with the coordinate information from
the institutions, will be used to construct an $N \times K$ distance
matrix (N representing the institutions, K representing each block
group). This matrix contains values that calculate the distance $d$
between each institution $i$ and all the block group centroids $c$ in
the U.S., $d_{ic}$.

To ensure that download speed information from block groups nearest
the institution is valued more in the final measure calculation,
inverse distances will be created using the following equation:

$$id_{ic} = \frac{1}{(d_{ic})^r}$$

where $id_{ic}$ represents inverse distance and $r$ represents a decay
function to prevent skewing of averages due to differences in
population densities.

Distance weights will then be calculated by dividing each inverse
distance by the sum of the distances for each institution:

$$idw_{ic} = \frac{id_{ic}}{\Sigma^C_{c=1}id_{ic}}$$

Since this weighted broadband measure will be assigned to each
institution (and not at the student level), population weights will
need to be calculated to account for institutional averages that might
be pulled to more densely populated areas:

$$pw_{c} = \frac{pop_{c}}{\sum_{c=1}^{C}{pop_c}}$$

where $pw_c$ is the population weight for each school and $pop_c$ is
the population measure for each block group.

The two weights achieved through these calculations will be
consolidated to form one concrete, weighted average measure of
broadband for each HBCU in our analytic sample:

$$w_{sc} = idw_{ic} \times pw_{c}$$

$$weightedbroadband_{i} = \sum_{c=1}^{C} \frac{w_{sc} \cdot
broadband_c}{\sum_{c=1}^{C}{w_{ic}}}$$


The broadband measure $broadband_{c}$ represents average broadband 
speeds (upload/download) and available ISPs for the block group. 


### Forthcoming Findings ###

\pagebreak

### References ###


