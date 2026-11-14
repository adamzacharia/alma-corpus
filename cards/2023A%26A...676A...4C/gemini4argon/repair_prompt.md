# Repair task for a Claude Code subagent

A methods card has evidence quotes that were not found verbatim in the paper. Below are the rules, the paper, and the failing items. Write ONE JSON object, nothing else, of the form {"repairs": [{"path": ..., "found": true|false, "loc": ..., "quote": ...}, ...]} with one entry per item (path unchanged) to:

    C:\Users\adama\alma-corpus\cards\2023A%26A...676A...4C\gemini4argon\repair_reply.txt

Use the Write tool for that file. Copy each quote character for character from the paper text below; a returned quote is checked mechanically and dropped if it is not in the paper. Do not read any other file, do not run commands, and do not change anything else. Reply with one line when done.

---

## Rules

You check evidence quotes for a methods card extracted from an astronomy paper. Some quotes could not be found verbatim in the paper text, and some stated values came without a quote. For each item: find the passage in the paper that supports the value and copy it VERBATIM (same words and order, at most 40 words; LaTeX markup may be dropped) with its loc (section heading, "abstract", "Table N" or "Figure N caption"). If the paper does not support the value, return found = false and leave quote and loc empty. Use only the paper text. Return one entry per item, with the item's path unchanged.

## Paper

<paper>
# FAUST IX. Multiband, multiscale dust study of L1527 IRS

# Introduction

Circumstellar disks orbiting class II young stellar objects (YSOs) are also commonly referred to as protoplanetary disks even though a large fraction of them already display structures thought to be shaped by embedded planets (cite: Andrews2018). Rings, gaps, and spirals have also been observed in younger (\<1Myr) disks ((cite: AlmaPartenership2015), (cite: Sheehan2018), (cite: Seguracox2020), (cite: Nakatani2020)). Several mechanisms have been proposed to explain the formation of structures during the early stages of the disk lifetime, including gravitational instabilities (cite: Takahashi2014), disk winds ((cite: Johansen2009), (cite: Takahashi2018)), and the evolution of dust (cite: Okuzumi2016). Along with these possibilities, the early formation of large planetesimals that gravitationally interact with the disk remains a viable explanation for the observations.

The early formation of planetary embryos is also suggested by the dust mass budget of evolved disks when compared to their younger progenitors ((cite: Testi2014), (cite: Ansdell2016)). (cite: Manara2018) estimated that the solid (dust) mass observed in evolved class II disks of the Ophiuchus (cite: Sanchis2020) and Lupus star-forming-region is 1 or 2 orders of magnitude lower than the mass of the expected exoplanet population. Conversely, the class 0/Is disks of Perseus contain roughly the same mass in solids as the known exoplanets ((cite: Williams2019), (cite: Tychoniec2020). One possible explanation is that the missing mass in the class II disks is the early conversion of class 0/I solids into planetesimals (e.g. (cite: Testi2022), (cite: Bernabo2022), (cite: Xu2023)). In a separate study, (cite: Mulders2021) suggest that the solid masses in class II disks and in exoplanets might be of the same order of magnitude. Nevertheless, an unrealistic planet formation efficiency of 100% would be required to place the beginning of planet formation during the class II stage.

Direct observational evidence for early-formed, kilometer-sized planetesimals is out of reach for any radio interferometer and thus this problem remains open. Furthermore, observational constraints on the initial properties of the dust population are needed for simulations to reconstruct the pathways that lead to planetesimal formation, starting from submicron-sized interstellar medium (ISM) dust particle interactions in a core accretion paradigm (e.g., (cite: Safronov1969), (cite: Goldreich1973),

(cite: Ormel2009), (cite: Birnstiel2016), (cite: Draz2022)). Even more importantly in this context, in an effort to investigate planetesimal formation at early stages, (cite: Cridland2022) find that differential gas and dust replenishment of a protoplanetary disk from its surrounding envelope sets favorable conditions for planetesimal formation. However, grains that are moderately coupled to the gas ($>$30 $\mu$m) are required to meet the streaming instability conditions that lead to the birth of these planetary embryos (cite: Youdin2005). Moreover, constraining grain sizes during the protostellar collapse phase has proven to be important for understanding the role of magnetic breaking during the early stages of disk formation. Since small grains are the main charge carriers, their distribution is paramount for the coupling of the infalling material with magnetic fields. In turn, such a coupling seems to regulate disk masses and sizes ((cite: Zhao2016), (cite: Lebreuilly2020)).

An additional reason to investigate the properties of dust grains in these extended envelopes is to constrain the role that dust grains play as sites - and catalysts - of molecular reactions in diffuse environments. The most commonly accepted pathways to produce complex organic molecules all rely on the presence of icy mantles on dust grains to capture the building blocks of these complex molecules and facilitate reactions among them (e.g., (cite: Tielens1982)).

|                                |                             |     |     |
|:-------------------------------|:---------------------------:|:---:|:---:|
|                                |                             |     |     |
| Alternative ID                 |       IRAS 04368+2557       |     |     |
|                                |                             |     |     |
| RA                             |       04h 39m 53.88s        |     |     |
|                                |                             |     |     |
| Dec                            | +26$^{\circ}$ 03’09.56$''$  |     |     |
|                                |                             |     |     |
| Age \[yr\]                     | \< 3 $\cdot$ $10^5$$^{[1]}$ |     |     |
|                                |                             |     |     |
| $M_{*} [M_{\odot}]$            | 0.2$^{[1]}$-0.45$^{[1,2]}$  |     |     |
|                                |                             |     |     |
| $L_{bol} [L_{\odot}]$          |         1.6$^{[3]}$         |     |     |
|                                |                             |     |     |
| $M_{4200au}^{env} [M_{\odot}]$ |         0.8$^{[4]}$         |     |     |
|                                |                             |     |     |

: Main properties of our target, L1527 IRS. The age of the object has been roughly estimated by \[1\] (cite: Tobin2012) based on the mass loss rate of the source. The mass of the protostar has been estimated by means of kinematical analysis by \[1\] and \[2\] (cite: Aso2017). The bolometric luminosity was reported by \[3\] (cite: Karska2018) and might suffer up to a factor two uncertainty due to the high inclination of the disk (e.g., (cite: Whitney2003)).The envelope mass was derived in \[4\] (cite: Motte2001) based on the IRAM 30 m telescope and MPIfR bolometer arrays’ 1.3 millimeter maps.

One way to probe dust grain properties in protostellar environments relies on estimates of their spectral index ($\alpha$), the slope of the spectral energy distribution (SED) across (sub)millimeter wavelengths. Specifically, if dust opacity scales as $\kappa \propto \nu^{\beta}$ and if the Rayleigh-Jeans (RJ) approximation holds, $\beta = \alpha - 2$ in the optically thin regime (e.g., (cite: BeckwithSargent1991), (cite: MiyakeNakagawa1993), (cite: Natta2007)). Typical spectral indices for the ISM - $\beta \sim 1.7$ - correspond to grain sizes in the range 100 Å – 0.3 $\mu$m (cite: Weingartner2001). On the other hand, $\beta < 1$ has been observed in class II objects, suggesting the presence of larger grains ($a \geq 1$ mm) in more evolved disks ((cite: BeckwithSargent1991) ,(cite: Testi2003), (cite: Ricci2010), (cite: Testi2014), (cite: Tazzari2021)).

In the recent past, several works have attempted to measure the dust emissivity index $\beta$ at the large scales of class 0/I protostellar envelopes to constrain whether dust growth might be significant at these very early stages of star and planet formation. Many have found surprisingly low $\beta$ values ($\leq 1$) and interpreted this result as evidence for early dust growth ((cite: Kwon09), (cite: Shirley2011), (cite: Chiang2012), (cite: Miotello2014), (cite: LG2019), (cite: Valdivia2019)). Following similar methods, other works have not found hints of such growth (cite: AG2019). And, in their sample study of ten CALYPSO (cite: Maury2019) class 0/I sources, (cite: Galametz2019) found examples of both relatively low and large $\beta$ values.

The hypothesis of early grain growth in the envelopes of class 0/Is has been considered to be challenging from a theoretical perspective: growth to millimeter-sized particles seems to require environments characterized by higher density and/or longer timescales than the average class 0/I envelope (e.g., (cite: Ormel2009), (cite: Guillet2020), (cite: Lebreuilly2023), (cite: Bate2022) and (cite: Silsbee2022)). Using both analytical models and numerical simulations, these authors find that dust particles cannot grow larger than $\sim 2 \mu$m in collapsing envelopes. It will be crucial for next simulations to incorporate generally disregarded effects, like the dust back-reaction on the turbulence through gas-dust friction and dust-magnetic-field interaction. Early growth is not the only possible explanation for the mentioned observations. (cite: Lebreuilly2020) proposed a scenario in which the differential collapse of dust grains of different mass through the prestellar core leads to a stratification of the dust sizes since larger grains collapse faster. Finally, another possibility could be an uplifting of grown disk grains to the inner envelope by the protostellar outflows and/or jets ((cite: Wong2016), (cite: Tsukamoto2021)).

It is thus imperative to characterize dust properties and evolution in the very early stage of star and planet formation.

| Project Code | P.I. | Date | Integration (s) | Resolution | Frequency (GHz) | Rescale Factor | CASA version |
|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|
|  |  |  | Band 3 |  |  |  |  |
| 2015.1.00261.S | Ceccarelli, C. | 01/03/2016 | 3113 | 2$\ensuremath{''}$ | 85-87 | 0.93 | 4.5.2 |
|  |  | 02/03/2016 |  | 2.4$''$ | 90-92 | 0.92 | 4.5.2 |
| 2016.1.01245.S | Cox, E. | 04/01/2017 | 907 | 2.1$''$ | 99-114 | 1.06 | 4.7.0-1 |
| 2016.1.01541.S | Harsono, D. | 21/12/2016 | 635 | 1.8$''$ | 92-105 | 1.14 | 4.7.0 |
| 2017.1.00509.S | Sakai, N. | 14/11/2017 | 6150 | 0.09$''$ | 85-99 | 1.000 | 5.1.1-5 |
|  |  | 14/11/2017 |  | 0.09$''$ | 85-99 | 1.04 | 5.1.1-5 |
|  |  | 14/11/2017 |  | 0.09$''$ | 85-99 | 1.04 | 5.1.1-5 |
| 2018.1.01205.L | Yamamoto, S. | 4/01/2017 | 1783 | 1.1$''$ | 93-108 | \- | 5.6.1-8 |
|  |  |  | Band 4 |  |  |  |  |
| 2016.1.01203.S | Oya, Y. | 19/11/2016 | 4697 | 0.8$''$ | 138-150 | 0.96 | 5.1.1 |
|  |  | 03/09/2017 |  | 0.1$''$ | 138-150 | 0.92 | 5.1.1 |
| 2016.1.01541.S | Harsono, D. | 10/03/2017 | 241 | 2.1$''$ | 144-154 | 0.97 | 4.7.0 |
|  |  | 31/03/2017 |  | 2.1$''$ | 144-154 | 1.000 | 4.7.0 |
|  |  |  | Band 6 |  |  |  |  |
| 2012.1.00647.S | Ohashi, N. | 20/07/2014 | 2117 | 0.4$''$ | 218-233 | 1.000 | 4.2.1 |
|  |  | 20/07/2014 |  | 0.4$''$ | 218-233 | 1.01 | 4.2.1 |
| 2013.1.01086.S | Koyamatsu, S. | 24/05.2015 | 2902 | 0.6$''$ | 219-234 | 0.85 | 4.5.0 |
|  |  | 20/09/2015 |  | 0.2$''$ | 219-234 | 0.99 | 4.5.0 |
| 2013.1.00858.S | Sakai, N. | 18/07/2015 | 2388 | 0.2$''$ | 245-263 | 0.96 | 4.4.0 |
| 2012.1.00193.S | Tobin, J. | 11/08/2015 | 7348 | 0.2$''$ | 244-260 | 0.94 | 4.3.1 |
|  |  | 02/09/2015 |  | 0.2$''$ | 244-260 | 1.05 | 4.3.1 |
| 2017.1.01413.S | van ’t Hoff, M. | 10/09/2018 | 968 | 0.3$''$ | 226-240 | 1.05 | 5.4.0 |
|  |  | 28/09/2018 |  | 0.3$''$ | 226-240 | 1.07 | 5.4.0 |
| 2011.0.00604.S | Sakai, N. | 10/08/2012 | 4838 | 0.6$''$ | 245-262 | 1.14 | 4.2.1 |
|  |  | 26/08/2014 |  | 0.6$''$ | 245-262 | 1.09 | 4.2.1 |
| 2011.0.00210.S | Ohashi, N. | 26/08/2012 | 1663 | 0.7$''$ | 219-231 | 1.05 | 4.2.1 |
| 2013.1.01331.S | Sakai, N. | 02/02/2015 | 1209.6 | 1.2$''$ | 216-235 | 0.97 | 4.3.0 |
| 2018.1.01205.L | Yamamoto, S. | 26/10/2018 | 1360.8 | 0.3$''$ | 244-262 | 1.10 | 5.6.1-8 |
|  |  | 17/03/2019 | 362.0 | 1.1$''$ | 244-262 | 1.10 | 5.6.1-8 |
|  |  | 15/12/2019 |  | 1.1$''$ | 244-262 | 1.11 | 5.6.1-8 |
|  |  | 26/10/2018 | 2358 | 0.3$''$ | 244-262 | 1.01 | 5.6.1-8 |
|  |  | 07/03/2019 | 635.0 | 1.1$''$ | 244-262 | 1.004 | 5.6.1-8 |
|  |  |  | Band 7 |  |  |  |  |
| 2012.1.00346.S | Evans, N. | 14/06/2014 | 635 | 0.3$''$ | 343-357 | 1.11 | 4.2.1 |
| 2015.1.01549.S | Ohashi, N. | 26/07/2016 | 847 | 0.2$''$ | 329-341 | 1.000 | 4.5.3 |
| 2016.A.00011.S | Sakai, N. | 29/07/2017 | 3592 | 0.075$''$ | 339-352 | 0.95 | 4.7.2 |
|  |  | 05/09/2017 |  | 0.075$''$ | 339-352 | 1.01 | 4.7.2 |
| 2011.0.00604.S | Sakai, N. | 29/08/2012 | 4233 | 0.5$''$ | 338-352 | 1.12 | 4.2.1 |

In this paper we focus on a single source in Taurus, L1527 IRS, (140 pc, e.g., (cite: Torres2007), (cite: Zucker2019)), hereafter L1527, to benchmark a dust continuum study across multiple frequencies and physical scales. Due to its distance and brightness, L1527 is one of the best studied class 0/I YSOs. The presence of an edge-on circumstellar disk was first suggested by (cite: Bontemps1996) and (cite: Ohashi1997) based on observations of the orientation of the bipolar outflow. It has been later confirmed by means of Spitzer and Gemini-North scattered light observations as an edge-on dark lane obscuring the central protostar ((cite: Tobin2008) and (cite: Tobin2010a), respectively) as well as high-resolution Submillimeter Array (SMA) and Combined Array for Research in Millimeter Astronomy (CARMA) interferometric observations of its continuum emission (cite: Tobin2013). The Atacama Large Millimeter/submillimeter Array (ALMA) C$^{18}$O kinematic detection of the disk was reported by (cite: Ohashi2014) and (cite: Aso2017). Furthermore, this edge-on, warped disk presents asymmetries at $\sim 20$ au that are consistent with spiral structures, the physical origin of which has been proposed to be gravitational instability ((cite: Sakai2019), (cite: Nakatani2020), (cite: Ohashi2022), (cite: Sheehan2022)). Observations of L1527 also display a bipolar jets and outflows extending to $20000$ au perpendicular to the disk plane, and carving a cavity in the collapsing envelope ((cite: Bontemps1996), (cite: Ohashi1997), (cite: Hogerheijde1998), (cite: Tobin2010a), (cite: Oya2015)). Being this object in a late stage of accretion, its molecular jet and outflow are not very energetic (cite: Podio2021). Table [1](#tab:l1527) summarizes the main properties of this young source.

We aim to study the dust continuum emission of L1527 using the Atacama Large millimeter/submillimeter Array (ALMA) and the Atacama Compact Array (ACA) to probe the outer ($10^3$ au) and inner ($10^2$ au) envelope, as well as the disk (10 au). We consider observations of our target in four different ALMA Bands (3, 4, 6, 7). Section 2 presents the ALMA and ACA observations that we have used throughout the analysis and the data reduction process. In Section 3, we justify the uv-plane geometrical modeling used for the source. In Section 4, we analyze the spectral and dust emissivity indices of L1527 at different scales. We discuss our results in Section 5, and wrap up our conclusions in Section 6.

| Project Code | P.I. | Date | Integration (s) | Resolution | Frequency (GHz) | Rescaling Factor | CASA version |
|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|
|  |  |  | Band 3 |  |  |  |  |
| 2016.1.01541.S | Harsono, D. | 30/01/2018 | 907 | 13.0$''$ | 92-105 | 1.06 | 4.7.0 |
| 2018.1.00799.S | Pineda, J. | 05/10/2018 | 5235 | 12.0$''$ | 92-107 | 1.06 | 5.4.0 |
|  |  | 05/10/2020 |  | 12.0$''$ | 92-107 | 1.07 | 5.4.0 |
|  |  | 06/10/2018 |  | 12.0$''$ | 92-107 | 1.05 | 5.4.0 |
|  |  | 06/10/2018 |  | 12.0$''$ | 92-107 | 1.08 | 5.4.0 |
|  |  | 06/10/2020 |  | 12.0$''$ | 92-107 | 1.06 | 5.4.0 |
|  |  |  | Band 4 |  |  |  |  |
| 2016.1.01541.S | Harsono, D. | 27/10/2016 | 302 | 9.1$''$ | 144-154 | 1.07 | 4.7.0 |
| 2016.2.00171.S | Harsono, D. | 24/08/2017 | 6168 | 7.8$''$ | 144-154 | 1.03 | 4.7.2 |
|  |  | 03/09/2017 |  | 7.8$''$ | 144-154 | 1.01 | 4.7.2 |
|  |  | 04/09/2017 |  | 7.8$''$ | 144-154 | 0.93 | 4.7.2 |
|  |  | 12/09/2017 |  | 7.8$''$ | 144-154 | 0.99 | 4.7.2 |
|  |  |  | Band 6 |  |  |  |  |
| 2016.2.00117.S | Yoshida, K. | 31/08/2017 | 26943 | 4.3$''$ | 230-245 | 1.12 | 4.7.2 |
|  |  | 01/09/2017 |  | 4.3$''$ | 230-245 | 1.09 | 4.7.2 |
|  |  | 15/09/2017 |  | 4.3$''$ | 225-245 | 1.11 | 4.7.2 |
|  |  | 16/09/2017 |  | 4.3$''$ | 225-245 | 1.10 | 4.7.2 |
|  |  | 16/09/2017 |  | 4.3$''$ | 225-245 | 1.02 | 4.7.2 |
|  |  | 16/09/2017 |  | 4.3$''$ | 225-245 | 1.10 | 4.7.2 |
|  |  | 17/09/2017 |  | 4.3$''$ | 225-245 | 1.03 | 4.7.2 |
|  |  | 17/09/2017 |  | 4.3$''$ | 225-245 | 0.99 | 4.7.2 |
|  |  | 17/09/2017 |  | 4.3$''$ | 225-245 | 0.95 | 4.7.2 |
| 2018.1.01205.L | Yamamoto, S. | 24/10/2018 | 4474 | 5.9$''$ | 216-235 | 0.98 | 5.6.1-8 |
|  |  | 20/10/2018 |  | 4.8$''$ | 245-262 | 1.07 | 5.6.1-8 |
|  |  |  | Band 7 |  |  |  |  |
| 2016.2.00117.S | Yoshida, K. | 15/09/2018 | 2782 | 3.1$''$ | 352-363 | 1.15 | 4.7.2 |

# ALMA observations

We here summarize the details of the observations used throughout this work. This source has been extensively studied with both the extended and compact arrays of ALMA. Archival data include high-resolution observations designed to detect disk substructure as well as lower-resolution, high-sensitivity observations of the extended envelope. We collect every available ALMA and ACA dataset suitable for our study of L1527, aiming to combine them in the deepest continuum analysis of the envelope so far. A summary of the datasets used in this work can be found in what follows and in Tables [\[table:1\]](#table:1) and [\[table:2\]](#table:2).

## ALMA FAUST B3 and B6

Here, we present new B6 and B3 data from the ALMA Large Program Fifty AU Study of the chemistry in the disk/envelope system of Solar-like protostars (FAUST, PI: Yamamoto, S.). The main goal of FAUST is to investigate the gas chemical composition of the environments surrounding young, Sun-like protostars including their embedding envelopes, their outflows, and disks (see (cite: Codella2021) for further details).

The observations aimed at L1527 were centered at right ascension $\alpha$(2000) $=$ 04h39m53.878s and declination $\delta$(2000) $= +$26$^{\circ}$03$'$09.56$''$. B3 observations were run on December 14, 2018 and August 25, 2019 with the 12m array in ALMA configurations C43-3 and C43-6, respectively. The baselines of these observations thus ranged 15-2500 meters. ALMA observed L1527 in the 93-95 and 104-108 GHz ranges. The source was observed for approximately 35 minutes in B3, for a continuum sensitivity of 0.025mJy. B6 observations were performed between October 20th, 2018 and December 15, 2019 with both the 7m and 12m arrays. The baselines of the 7m array ranged from 8.9 to 48.9 meters. The 12m array observations were taken in configurations C43-2 and C43-5, with baselines ranging from to 15-314 meters and 15-1400 meters, respectively. ALMA observed in the 244-247 and 258-262 GHz ranges with a spectral resolution of approximately 62.5 MHz. The source was observed for approximately 75 minutes in B6, for a continuum sensitivity of 0.026mJy.

The FAUST data were calibrated using a modified version of ALMA pipeline version 42866, using the Common Astronomical Software Applications (CASA, (cite: McMullin2007)), version 5.6.1-8. This included a correction for errors introduced by the per-channel normalization of data by the ALMA correlator[^1]. Line-free Local Standard of Rest Kinematic (LSRK) frequency ranges were identified by visual inspection and averaged per spectral window, and initial continuum images were produced for each separate ALMA configuration. These were then used as initial models for subsequent per-configuration phase-only self-calibration, followed by amplitude and phase self-calibration. Great care was taken to ensure that the models were as complete as possible to avoid changing the overall flux density scale of the data when doing amplitude self-calibration. L1527 is sufficiently strong that per-integration phase-only self-calibration was possible, while for amplitude self-calibration per-scan self-cal was used. The per-configuration datasets were then aligned across configurations in both phase and amplitude, again using a self-calibration technique. Corrections to the amplitude scale of up to 10% were found to be needed for some datasets. Improvements in the dynamic range (peak/RMS away from emission) of more than an order of magnitude for the final images were achieved using this technique for setup 1 and 2. The improvement for setup 3 was $\sim35\%$. Finally, we imaged the visibilities with the CASA *tclean* function, using the hogbom deconvolver, a "briggs" weighting scheme with robust parameter set to 0.5. The resulting beam in B3 is 0.44$''$x0.27$''$ wide with PA=-29$^{\circ}$; while the synthesized beam in B6 is 0.42$''$x0.28$''$, PA=19$^{\circ}$. We present the new continuum maps in Fig. [1](#fig:faustb3) and Fig. [2](#fig:faustb6).

## ALMA Band 3

We gathered ALMA Band 3 (B3) observations of L1527 spanning from 2017 to 2020. Given the different scientific aims of the projects, the data collected with the 12-m array has a resolution between 0.09$''$ (project 2017.1.00509.S, PI: Sakai, N.) and 2.4$''$ (project 2015.1.00261.S, PI: Ceccarelli, C.). The sensitivity of the 12-m array observations that have been used in this work ranges from 0.03 to 0.06 mJy and the total time on source is $\sim$210 minutes. The frequency of the side bands ranges from 85 to 115 GHz.\
The 7-m array has been pointed at L1527 in B3 for a total $\sim$102 minutes (projects: 2016.1.01541.S and 2018.1.00799.S; PIs: Harsono, D. and Pineda, J.). The observations have resolutions 12.0$''$ - 13.2$''$ and have been carried out in a range of frequencies from 92 to 105 GHz with sensitivities of 0.3-0.6 mJy.

## ALMA Band 4

L1527 has been observed in Band 4 (B4) throughout several months in 2016 and 2018. The data collected with the 12-m array has a resolution between 0.1$''$ (project 2016.1.01203.S, PI: Oya, Y.) and 2.1$''$ (project 2016.1.01541.S, PI: Harsono, D.). The sensitivity of the 12-m array data that have been used in this work ranges from 0.03 to 0.3 mJy and the total time on source is $\sim$82 minutes. The frequency of the side bands ranges from 138 to 154 GHz.\
The 7-m array observed L1527 in B4 for a total $\sim$107 minutes (projects: 2016.1.01541.S and 2016.2.00171.S; PI: Harsono, D.). The observations have resolutions 7.8$''$ - 9.1$''$ and have been carried out in a range of frequencies from 144 to 154 GHz with sensitivities of 0.2-0.4 mJy.

## ALMA Band 6

ALMA Band 6 (B6) observations of L1527 span from 2013 and 2020. The data collected with the 12-m array has a resolution between 0.2$''$ (projects 2012.1.00193.S, 2013.1.00858.S and 2013.1.01086.S; PIs: Tobin, J.; Sakai, N. and Koyamatsu, S.) and 1.1$''$ (project 2018.1.01205.L; PI: Yamamoto, S.). The sensitivity of the 12-m array observations that have been used in this work ranges from 0.03 to 0.09 mJy and the total time on source is $\sim$403 minutes. The frequency of the side bands ranges from 218 to 263 GHz.\
The 7-m array observed L1527 in B6 for a total $\sim$85 minutes. The observations have resolutions spanning 4.3$''$ - 5.9$''$ (projects: 2016.2.00117.S and 2018.1.01205.L; PIs: Yoshida, K. and Yamamoto, S.) and have been carried out in a range of frequencies from 216 to 262 GHz with sensitivities of 0.4-1.0 mJy.

![](images/b3_fausst_mds.png)

## ALMA Band 7

L1527 has been observed in Band 7 (B7) from 2014 and 2018. The data collected with the 12-m array has a resolution between 0.075$''$ (project: 2016.A.00011.S, PI: Sakai, N.) and 0.5$''$ (project 2011.0.00604.S; PI: Sakai, N.). The sensitivity of the 12-m array observations that have been used in this work ranges from 0.06 to 0.2 mJy and the total time on source is $\sim$155 minutes. The frequency of the side bands ranges from 218 to 263 GHz.\
The 7-m array observed L1527 in B6 for a total $\sim$46 minutes during project 2016.2.00117.S (PI: Yoshida, K.). The observations have resolutions 3.1$''$ and have been carried out in a range of frequencies from 352 to 363 GHz with sensitivity of 1.44 mJy.

## Data reduction and self-calibration

Since we work with data taken at several frequencies, we avoid frequency smearing by splitting datasets with a relatively large frequency offset. This is especially important in B3. Thus, we split its datasets into two groups. This way, after calibration, we work with five final frequencies: 88, 100, 141, 249, and 348 GHz. These frequencies roughly correspond to 3.4, 3.0, 2.1, 1.2 and 0.88 mm wavelengths.

The first round of calibrations was performed using the standard CASA pipeline methods provided by the ALMA Regional Centers (ARC). Considering the data were acquired over a period of several years, different versions of CASA were used for these calibrations. The version used for each dataset is listed in Table [\[table:1\]](#table:1). This first round includes system temperature, phase, amplitude, and bandpass calibration, along with corrections to account for atmospheric water vapor.

We carried out further data reduction and calibration steps using CASA version 6.2.1.7. First, the ALMA cubes for each execution block were inspected and additional flagging was applied when necessary, that is to mask out spectral lines. We are only interested in the continuum emission, thus, to speed up further operations, we channel-averaged the spectral windows of every execution block. We used a common width to level out the S/N among spectral windows and we were careful to avoid bandwidth smearing effects by limiting the averaging based on the maximum baselines and spectral window bandwidth (cite: Bridle1999). Before combining the datasets for the analysis, we performed several additional operations. First, we ran the *statwt* CASA routine in order to fix the visibility weights. This is especially important for datasets from old ALMA Cycles that have been reduced with CASA 4.2.1 or earlier versions[^2]. We then imaged the averaged-channel visibilities with the *tclean* task and fitted a Gaussian with *imfit* to pinpoint the maximum of the emission. Next, we used the *fixvis* function to shift the phase center to the position of the peak of L1527 at the epoch of every observation.

![](images/b6_faust_mds.png)

![](images_ref_report/L1527_tot_emission_cfrPdBI_ref_report.png)

Since the target coordinates were slighlty different across datasets, we also set the source sky position (in the metadata) to a common center across execution blocks using *fixplanets*. Once the coordinates of each dataset were phase-centered and aligned following this procedure, we rescaled the fluxes following the procedure of (cite: Andrews2018): for every frequency, selected a range of uv-distances where the uv coverage of two datasets overlaps, binned the visibilities in that range, and compared them to obtain a rescaling factor where the visibilities overlapped. The rescaling factors were in a 1-15% range for all execution blocks. The rescaling correction was then computed using the task *gencal* and the rescaling itself was achieved by applying the correction factors with *applycal*. We report the rescaling factors in Tables [\[table:1\]](#table:1) and [\[table:2\]](#table:2).

Based on this model, we then computed the phase corrections on each execution block using *gaincal* and applied them with *applycal*. This step aimed to correct phase errors between executions and between spectral windows. We repeated this procedure three times. In the first round, we set the solution interval of *gaincal* to *inf*, combined the scans within each execution block and set gaintype $=$ "G", that is the gains were determined for each polarization and spectral window. In the second and third rounds, we combined the spectral windows of each block, shortened the solution intervals to 60 and 10 seconds, respectively, and set gaintype $=$ "T", to obtain one solution for both polarizations. The self-calibration yielded peak S/N improvements in the range 10-500 % when evaluated on the images obtained with the combined datasets. We did not find any appreciable improvement in the noise and signal-to-noise properties for phase-only self-calibration steps with even smaller time intervals. At this point, we combined the corrected datasets using the *concat* CASA task.

Since we analyze extended emission, we estimated the effect of the antennas primary beam (PB) correction on the recovered flux. In B7, the ALMA 7m and 12m antennas PB full width at half maximum is 33.0$''$ and 19.0$''$, respectively. This results in a loss of about 10% of flux at 20 k$\lambda$ (1000 au scales), for the 12m antennas. This only marginally affects the recovered spectral index we are interested in, increasing it by a factor of $<$5% even at the largest scales.

## L1527 as seen in the visibility space

The final binned visibility amplitudes obtained with our data reduction and self-calibration are illustrated in Fig. [3](#fig:our_data). We also show that the associated spectral index lies in the range $1.5 < \alpha_{0.88-3.4mm} < 2.4$. This low $\alpha$ is not surprising as the disk emission contribution dominates at every uv-distance (see Section [3](#sec:model)), thus the total spectral index is strongly influenced by the optically thick disk (cfr. Section [4](#section:spindx)).

Among other class 0/Is of the CALYPSO survey, the continuum emission of the envelope infalling on L1527 has been studied in (cite: Galametz2019), hereafter G19, who used PdBI observations at 1.3 and 3.2 millimeter. The data they used spans a range in uv-distances from 20 to 200 k$\lambda$ at both frequencies. Fig. [3](#fig:our_data) shows a comparison between the ALMA observations we used and G19’s PdBI fluxes (white points).

We cut the ALMA datasets at the shortest common baseline, set by B7 at 9.8 k$\lambda$, hence a Maximum Recoverable Scale (MRS) of roughly 26.0$''$, or 3500 au at the distance of the source. We aim to more robustly determine the spectral and dust-emissivity indices of the source by extending the frequency range, that dominates the error on $\alpha$ (see Section [4](#section:spindx)). Furthermore, a denser sampling of frequencies is critical to understand the optical depth of the source across wavelengths, which is vital to constrain where the spectral index is a good proxy for dust grain sizes.

On top of enriching the studied frequency range, we used a combination of ALMA and ACA data to study the dust continuum emission with high S/N at scales 2 times larger than G19, toward both shorter and longer baselines. In fact, although our primary attentions are devoted to the envelope, long-baseline visibilities are of great importance if we want to properly model the compact emission. G19 subtracted a constant amplitude (F$_{200 k\lambda}$) from each visibility at the two frequencies, assuming an unresolved disk that would contribute a constant flux at baselines shorter than 200 k$\lambda$ ($\sim$1.0$''$, or 140 au).

Considering the wider uv-coverage of the data we used (9.8-1000 k$\lambda$), we can more precisely model and subtract the compact emission by fitting a Gaussian component within a model that separately accounts for envelope and disk (see Section [3](#sec:model)). This procedure also makes a significant difference when computing the errors on $\alpha$ and $\beta$, which in turn depend on the relative errors of the amplitudes. Since the PdBI amplitudes in G19 were roughly constant and only slightly above F$_{200 k\lambda}$, the relative error on the fluxes after the subtraction of F$_{200 k\lambda}$ became large already at a uv-distance of $\sim$ 100 k$\lambda$. Given the high S/N of our combined datasets, the relative flux uncertainty remains relatively contained after disk subtraction (see Fig. [6](#fig:mean_alpha)). In the upcoming Section, we lay out the methods we followed to model the full visibilities and subtract the disk component to obtain an envelope-only spectral index.

# Disentangling disk and envelope emission

To investigate dust properties in the envelope of L1527, we worked in the visibility ($u, v$) plane. This approach has the main advantage of keeping the analysis clear of the artifacts and non-linearity from which image reconstruction algorithms suffer.

The visibility amplitudes are the combined flux of disk and envelope at all $uv$ distances. Since we are mainly interested in studying the spectral index of the envelope, we have to disentangle the compact emission flux from the extended one. Hence, we need to fit the data with a model appropriate for a compact disk that, at the same time, self-consistently accounts for excess emission at the shortest baselines (largest physical scales).

Brightness profiles of protostellar envelopes of diverse class 0/I YSOs have been found to be well fit by broken power laws with exponents in the (-2.5,-1) range ((cite: Plummer1911), (cite: Motte2001), (cite: shirley2002), (cite: Maury2019)). Thus, we consider a geometrical model in which a Gaussian, that will trace the compact emission, is summed to a power law (Plummer profile):

$$\begin{equation}
    I_{TOT}(R) = rI_0 \cdot e^{-\frac{R^2}{2\sigma^2}}  + \frac{(1-r) I_0}{\Bigg(1 + \Big(\frac{R'}{R_i}\Big)^2 \Bigg)^{\frac{p-1}{2}}} .
    \label{eq:total_profile}
\end{equation}$$

![](images/uvplot_Band3_85ghz_logscale_G+P_noincl_50walker_3000_7000steps.png)

The Gaussian is defined by a peak $f_0' = rI_0$, a width $\sigma$, an inclination $inc$ and position angle PA. The envelope power law has peak flux $f_0'' = (1-r)I_0$ and three free parameters: $R_i$, $R_{out}$, $p$. These are such that the envelope emission is constant within a radius $R_i$, it follows Eq. [\[eq:total_profile\]](#eq:total_profile) between $R_i$ and $R_{out}$ and it is null beyond $R_{out}$. The peak fluxes of the extended and compact emission are modulated by the free parameter $0 < r < 1$. We have performed the fitting with `galario`, a library that exploits the power of modern graphical processing units (GPUs) to accelerate the analysis of observations from radio interferometers (cite: Tazzari2018). In our framework, `galario` would compute a model image given our total profile, then it would Fourier-transform it into synthetic visibilities and sample them at the uv-points covered by the antenna configurations with which the observations were performed. Then, it would run a minimum-$\chi^2$ fit between the data and the model visibilities. The 10 fit parameters were the flux amplitude $I_0$ and the $r$ factor; the width $\sigma$, the inclination (inc) and position angle (PA) of the Gaussian; the inner and outer envelope radii, $R_{in}$ and $R_{out}$, and the power law exponent $p$. Finally two parameters, dRA and dDec, fit the offset of the peak from the phase center. For each fit, 80 walkers were set to run for 3,000 burn-in steps and 7,000 more steps after the burn-in stage. The best fit results are summarized in Table [\[tab:fits_results\]](#tab:fits_results). We show, as an example, the single best-fit model for the B3 88 GHz data, decomposed in its power law and Gaussian components (Fig. [4](#fig:fitband3)). We report the rest of the fits in Figures [18](#fig:B3fit), [19](#fig:B4fit), [20](#fig:B6fit), [21](#fig:B7fit), along with the best fit parameters summary (Table [\[tab:fits_results\]](#tab:fits_results)) in Appendix [9](#sec:appendix2). In particular, we find that the compact emission has a deprojected width of $0.15\ensuremath{''} < \sigma_{fit} < 0.28\ensuremath{''}$ on the sky, depending on the Band. If we define the radius of the disk to be the $2\sigma$ contour of the Gaussian component, then $R_{disk} \sim 75$ au in B7, consistent with what was found in the kinematical analysis of (cite: Aso2017). In addition, the Gaussian component contributes to a minimum of 75% in B4, up to 98% in B3 (see Appendix [9](#sec:appendix2) for the detail). The derived disk fluxes are listed in Table [2](#tab:disk_tab). This fitting procedure allows us to disentangle disk and envelope emission and study the spectral energy distribution of the disk and envelope separately in the next section.

![](images_ref_report/L1527_disc_alpha_mywork+melis_B3-88-99-B4-B6-B7_ref_report.png)

# Spectral and dust emissivity indices

In this Section, we first derive the spectral indices of the observed emission at both disk and envelope scales, then we discuss to what extent these can be used to evaluate dust grain properties.

![](images_ref_report/L1527_disc-subtracted_emission_mean_alpha_last_ref_report.png)

## The circumstellar disk

To study possible early dust grain growth in the envelope of L1527, we made use of long baseline data to properly model the compact emission to be subtracted from the short baseline amplitudes. In doing so, we obtained estimates of the flux of the compact ($0.15" < \sigma_{fit} < 0.27"$) emission of L1527 in four ALMA bands. We here show the spectral energy distribution of the disk we obtained by combining and modeling all suitable ALMA archival data for L1527 (Figure [5](#fig:disk_sed), Tab. [2](#tab:disk_tab)). To offer a more comprehensive view to the reader, we extended the range of wavelengths by including literature Very Large Array (VLA) measurements from (cite: Melis2011), up to 6 cm.

Fitting the SED in the 0.88 to 7-millimeter range using our measurements along with the values of (cite: Melis2011), we find an optically thick disk with $\alpha = 2.1 \pm 0.1$. This is not surprising: the disk orbiting L1527 is very inclined ($i \sim 80^{\circ}$), almost edge-on to the sky: this geometric factor contributes to increase its optical depth along our line of sight. Furthermore, (cite: Ohashi2022) used high-resolution, multiple frequency observations of the disk and found that the brightness temperature toward the mid-plane of the disk obtained by converting the flux at 0.88 mm (42 K) is much lower than that found at 2 and 3 mm (60 K and 90 K, respectively). This progressive increase in brightness temperature with wavelength means that the disk is at least partially optically thick at 0.88 and 2 mm.

The high optical depth of the circumstellar disk of L1527 prevents us from concluding anything about its dust grain properties based on the spectral index alone. Finally, the 3.5 and 6 cm fluxes can be used to estimate the free-free emission that affects the measurements at the shorter studied wavelengths.

|             |                |                    |                   |
|:------------|:--------------:|:------------------:|:-----------------:|
| $\nu$ (GHz) | $\lambda$ (mm) | Flux density (mJy) |     Reference     |
|             |                |                    |                   |
| 348         |      0.86      |    324 $\pm$ 29    |     this work     |
| 249         |      1.2       |    132 $\pm$ 9     |     this work     |
| 141         |      2.1       |     52 $\pm$ 3     |     this work     |
| 101         |      3.0       |    28 $\pm$ 0.6    |     this work     |
| 88          |      3.4       |    21 $\pm$ 0.5    |     this work     |
| 43.5        |      7.0       |   4.4 $\pm$ 0.6    | (cite: Melis2011) |
| 22.5        |      13.3      |   1.4 $\pm$ 0.1    | (cite: Melis2011) |
| 8.5         |      35.2      |  0.81 $\pm$ 0.03   | (cite: Melis2011) |
| 5           |       60       |  0.68 $\pm$ 0.04   | (cite: Melis2011) |

: L1527 disk SED built with ALMA (this work) and VLA (cite: Melis2011) observations.

The slope at these longer wavelengths is $\alpha_{35-60} = 0.33 \pm 0.17$, as reported in Fig. [5](#fig:disk_sed) and is compatible with what is expected for free-free emission (cite: Panagia1975). However, it is worth noting that (cite: Melis2011) showed how the 3.5 cm flux of L1527 is highly variable in time. Indeed, they listed eight measurements (references therein) at this wavelength taken between 1996 and 2010 where the 3.5 cm flux shows significant variations between 0.55 and 0.81 mJy, with errors of 1-5%. In Fig. [5](#fig:disk_sed), we show (cite: Melis2011) points taken at roughly simultaneous epochs (2010 July 30th). The contribution of the free-free emission is lower than 10% in B3 and lower than 1% in B7.

## The envelope

We investigate changes in the spectral index throughout the spatial scales of the envelope in the visibility plane. Starting from the common shortest baseline of $\sim$ 9 k$\lambda$, we log-uniformly bin the visibilities across the available uv-distances and then measure the spectral index in each bin. Since we are interested in studying the spectral index of the envelope, we have subtracted the galario best-fit Gaussian component of our model (see Section [3](#sec:model)) from the data. This way, the remaining flux is the contribution of the extended emission only (Fig. [6](#fig:mean_alpha)).

Here, the amplitude and related error bars account for both statistical and calibration uncertainties. We set the latter to 10% for B7 and 5% for bands 3, 4 and 6, following the prescriptions of the ALMA Handbook and on-sky analysis (cite: Remijan2019; francis20). While the error on $\alpha$ is dominated by flux calibration errors on the observed amplitudes (see Fig. [3](#fig:our_data)), the relative amplitude error becomes important after the subtraction of the disk model. Not only is the relative error overall larger, it also visibly increases with uv-distance. This effect is clear in Fig. [6](#fig:mean_alpha). Using almost every archival dataset for this source, we made an effort to maximize the S/N of the faint envelope of L1527 in what is its deepest continuum analysis.

To make the best use of our multiwavelength data, we fitted a line to the fluxes along all wavelengths in each uv-distance bin and we more robustly determined the spectral index. Since we combined a number of datasets for each band, the frequency of each flux point in each bin is taken to be the weighted average of the frequencies in that bin. The uncertainty on the spectral index obtained by fitting all bands is the error on the slope obtained with the weighted linear regression. Figure [6](#fig:mean_alpha) shows that the fitted spectral index of the envelope of L1527 appears roughly flat in the studied range that spans from $\sim 2000$ down to 50 au, $\alpha \sim 3$. For completeness, we show the spectral indices computed between adjacent bands in Appendix [8](#sec:appendix1). These are flat as well, although they show systematic differences in their average value, which clearly shows the need for a multifrequency (\>2) approach.

Finally, we measured the spectral index in different angle bins on the sky, after removal of the compact component. We divided the uv-plane into three different regions: the envelope ($-20^\circ< PA <20^\circ$), the outflow ($70^\circ< PA <110^\circ$) and the cavity walls (the remaining zones). We do not observe any significant difference among the three spectral indices at scales larger than 200 au (Fig. [7](#fig:spindx_angles)).

## Dust emissivity index

The simple link between the exponent of the dust opacity power law and the spectral index, $\beta = \alpha + 2$, only holds for optically thin emission when the RJ approximation is valid. Thus, before interpreting the values of the envelope’s spectral index in terms of dust properties, we check whether these necessary conditions are met at the wavelengths we probe. First, we evaluate the optical thickness of the emission. The specific intensity $I_{\lambda}$, or flux per unit solid angle that we receive from the source ($F_{\lambda}/\Omega$) can be generally expressed as an absorbed black body: $$\begin{equation}
    I_{\lambda} = \frac{F_{\lambda}}{\Omega} = \big(1 - e^{-\tau_{\lambda}}\big) \cdot B(T_{dust})
\end{equation}$$ where the optical depth $\tau_{\lambda}$ modulates the difference between the observed flux and the optically thick black body emission. If $\tau_{\lambda} \ll 1$, then $F_{\lambda}/\Omega \sim \tau_{\lambda} B(T_{dust})$, while if $\tau_{\lambda} \gg 1$, then the observed emission tends to a black body spectrum.

To evaluate the optical thickness, we consider a typical dust temperature prescription for a centrally illuminated protostellar envelope ((cite: Shu1977), (cite: Butner1990), (cite: Terebey1993), (cite: Motte2001)): $$\begin{equation}
    T(R) = 38 L^{0.2} \Bigg(\frac{R}{100 au}\Bigg)^{-0.4}.
    \label{eq:temp}
\end{equation}$$ Considering this relation and the range of scales that we probe, the temperature gets as low as 10 K in the outermost radii of the envelope ($\sim 2000$ au). We find that, even at the shortest of our wavelengths, the envelope emission is optically thin at all scales as $F_{0.88mm}/\Omega < B(T_{dust})$ by a factor of 10 (Fig. [8](#fig:opt_thin)). The optically thin regime is naturally satisfied at longer wavelengths.

Secondly, we check if the RJ approximation is valid. Based on the same temperature profile for the dust, in the cold outskirts of the envelope ($\sim$ 20 K at 500 au), $h\nu / k_BT \sim 0.8$ at our mean B7 frequency of 348 GHz. This violates the RJ condition $h\nu / k_BT \ll 1$. Thus, while the envelope of L1527 is in the optically thin emission regime, it does not satisfy the RJ approximation and $\beta \neq \alpha - 2$.

Thus, using the same profile, we can obtain a temperature-corrected $\beta$ profile as: $$\begin{equation}
    \log_{10} \Bigg[\frac{F_{\nu}}{B_{\nu}(T)}\Bigg] = \beta \cdot \log_{10}({\nu}) + A ,
    \label{eq:beta}
\end{equation}$$ where $A$ is a constant (similarly to what done in G19, but for multiple frequencies). Figure [9](#fig:beta) shows how the dust emissivity index is nearly $\alpha-2$ for the smaller spatial scales, where T(R) is large enough, while it starts to show diskrepancies after 200 au (where T$\sim$ 25 K). We also investigated the effects on $\beta$ of changing the temperature profile’s radial power law exponent. We found that exponents in the interval \[-0.3,-0.6\] do not affect our conclusions. We exclude steeper profiles as they lead to unreasonably low values of the temperature at the studied scales. The error on the dust emissivity index has been considered to be the same one that affects the spectral index since we are assuming an exact temperature profile, thus $\Delta\alpha = \Delta\beta$.

In Figure [9](#fig:beta), we report the measured $\beta$ as a function of uv-distance, and we overplot a linear fit to the points. We have run the fit by means of the Bayesian method described in (cite: Kelly2007) and implemented in linmix[^3]. The priors were uniformly distributed. We plot some single chain results in Fig. [9](#fig:beta), along with the best fit model. We find evidence for an outward increasing $\beta$, rising from 0.8 to 1.6 between 50 and 2000 au radial scales: $$\begin{equation}
    \beta(R_{au}) = 0.37^{+0.17}_{-0.16} \cdot \log_{10}( R_{au}) - 0.23^{+0.45}_{-0.46}.
    \label{eq:beta_grad}
\end{equation}$$ In turn, Eq. [\[eq:beta_grad\]](#eq:beta_grad) yields: $$\begin{equation}
    \beta(R=300 au) = 1.15 \pm 0.08.
\end{equation}$$ These measurements represent tentative evidence for dust optical properties variations throughout the envelope of L1527. Furthermore, low $\beta$ at scales lower than $\sim$ 300 au are consistent with the presence of submillimeter sized grains in the inner envelope.

## Literature comparison

G19 studied the envelope continuum emission of a few class 0/I sources, including L1527. Here, we briefly compare our findings to theirs. First, the wide uv-distance range of the datasets we used allowed us to model the disk emission spatial profile, while only a constant amplitude was subtracted in the amplitudes in G19, who assumed an unresolved compact disk. This spatial modeling is important to properly subtract the compact emission from the total amplitudes and work out the rest of the analysis on the flux of the envelope alone.

G19 reported a slope of $\beta$ of 0.18 $\pm$ 0.39. Noticeably, this flat $\beta$ profile of G19 is consistent with what we observe across the same region they studied, 70-700 au radii. Extending the studied scale by a factor 2, we are able to explore the outer envelope and determine the positive outward gradient of Eq. [\[eq:beta_grad\]](#eq:beta_grad). At the outer probed radii ($\sim$ 2000 au), the derived values for $\beta$ are consistent with typical ISM measurements. Secondly, G19 reported a fitted $\beta_{500 au} = 1.41 \pm 0.16$ while we find $\beta_{500 au} = 1.15 \pm 0.08$ based on Eq.[\[eq:beta\]](#eq:beta). These improvements have been obtained thanks to higher sensitivity data as well as the extension of the studied frequency ranges.

![](images_ref_report/L1527_emission_angles_ref_report.png)

# Discussion

We here discuss our results in further detail, how they compare with existing theoretical and observational literature, and the caveats relevant to our analysis.

## Dust growth in envelopes is challenging

The low $\beta$ value we measured at scales of a few hundred au from L1527 is a tentative evidence for grown dust grains in the inner envelope of the class 0/I YSOs L1527. If solids indeed grew in the envelope, this would represent a shift in the usually assumed initial conditions for planet formation, which only include $< 0.25 \mu$m grains at such scales. However, a challenge to our measurements rises when trying to link these low $\beta$ with the in situ formation of relatively large dust grains in the envelope environment. Indeed, theoretical studies of grain agglomeration have not been able to reproduce such growth in envelope-like environments. The numerical simulations of (cite: Ormel2009), (cite: Lebreuilly2023) and (cite: Bate2022) have shown that it is very unlikely that solid dust grains could grow larger than about 1 $\mu$m at the typical densities and timescales of envelopes such as the one infalling on L1527 and its young disk. These works included a thorough treatment of grain-grain collision energetics, accounting for relative grain velocities due to turbulence, Brownian motions, ambipolar diffusion and hydro-dynamical drift.

![](images_ref_report/opt_thin_b7_ref_report.png)

Additionally, (cite: Silsbee2022) proposed a simpler, analytical model to place strict upper bounds on the maximum grain size that can be reached in extended protostellar envelopes. They considered a coagulation model for the growth of spherical, yet fractal grains whose relative motions are driven by turbulence and the fragmentation of which happens for velocities above a quite generous threshold of v$_{rel}$ = 10 m/s. Considering that the optical properties of dust grains depended on the product of their radius (a) with a filling factor (or porosity) $\phi$, they find that it is not possible to grow grains with an optical radius $a_{opt} = a\phi$ of 1 millimeter, in typical protostellar envelope conditions. They find that, in the $10^5$ yr lifetime of a typical class 0 source whose volume density is approximately $10^7$ cm$^{-3}$, grains grow up to only about 2.5 $\mu$m.

![](images_ref_report/betas_mine_B3-88-99-B4-B6-B7_ref_report.png)

## Grain size, composition and temperature effects on $\beta$

While these theoretical works strongly disfavor the in situ growth of (sub)millimeter dust grains in the envelopes of young objects, the observational evidence of the low dust emissivity indices found therein ((cite: Kwon09), (cite: Miotello2014), (cite: Galametz2019)) remains largely uncontested.

First, an objection to the link between low $\beta$ and large grains might arise from the dependency of the dust-emissivity index on other dust properties. In fact, the dust emissivity index is sensitive to changes in dust composition, porosity and the presence (or absence) of an icy mantle (e.g., (cite: BeckwithSargent1991), (cite: Testi2014)). Although variations in $\beta$ are evident and well-characterized across different grain properties, $\beta < 1$ remains a strong evidence for the presence of (sub)millimeter grains in the studied distribution ( (cite: Natta2004ASPC), (cite: draine2006), (cite: Natta2007), (cite: Testi2014) and (cite: Kholer2015), (cite: Ysard2019)). Thus, although further laboratory studies will be necessary to more precisely interpret $\beta$ in terms of both grain sizes and compositions, dust particles significantly larger than what expected for the typical ISM grains (0.2-2 $\mu$m) remain a robust explanation for our observations.

Secondly, if the compact emission contribution is not properly subtracted from the visibilities, a bias can be introduced when determining the slope of the SED. Previous studies (e.g., (cite: Miotello2014) and G19) have subtracted the compact emission assuming unresolved disks that would only contribute an offset at all uv-distances. They determined this value by fitting a constant to the visibilities amplitudes after some arbitrary long baseline and subtracted it from the visibilities at shorter uv-distances. Here, we have tried to more properly model and subtract the disk emission as explained in Section [3](#sec:model).

Finally, perhaps the temperature correction discussed in Section [4.3](#sec:beta_section) could be revisited. If the emission is optically thin, Equation [\[eq:beta\]](#eq:beta) reduces to: $$\begin{equation}
    \beta = \alpha - \frac{d \log(B_{\nu}(T))}{d \log(\nu)},
    \label{eq:corr_beta}
\end{equation}$$ where the second term is two in case the RJ approximation is satisfied. The temperature power law we consider (cfr. Eq.[\[eq:temp\]](#eq:temp)) yields temperatures of about 25 K at 200 au, where we find $\beta \lesssim 1$. Here, the correction term of Eq.[\[eq:corr_beta\]](#eq:corr_beta) amounts to 1.85. If the true temperature of the medium at 300 au were lower than what is predicted with our simple power law, then the real $\beta$ would be higher. However, to produce $\beta \sim$ 1.7, the temperature of the envelope at 300 au would need to be lower than 5 K, which is far below a reasonable value for a protostellar envelope.

## Alternatives: differential collapse or outflow transport

Although simulations predict so far that large grains cannot grow in situ, observations strongly hint to their presence in the inner few hundreds au of these protostellar envelopes. Different mechanisms that can justify their presence might be at play.

First, (cite: Lebreuilly2020) investigated how the distribution of dust grains of a prestellar core evolves during the early phases of the protostellar collapse and how this evolution depends on the initial conditions of the cloud and the dust distribution. They found a significant decoupling between gas and dust for grains of a few 10 $\mu$m. Moreover, observations of scattered light from molecular cloud cores in the 3-5 $\mu$m range ("coreshine") have provided evidences for the presence of grains larger than usually expected ISM ones: up to 10 $\mu$m compared to about 0.25 $\mu$m ((cite: Steinacker2010), (cite: Steinacker2014), (cite: Steinacker2015)). These larger grains would tend to settle more efficiently in the first-core, leading to a radial stratification of dust properties that could reproduce a gradient of $\beta$ as we observe here, but hardly explain the low $\beta$ values at the inner envelope scales. Further refinement of this kind of model will require deeper knowledge of prestellar core dust properties.

A second scenario to explain large grains in the envelopes of class 0/I YSO was studied by (cite: Wong2016), who proposed that such grains might be transported to the envelope after the growth has happened in the disk in the very early stages of the system. Their model suggested that a typical protostellar outflow (T$\sim$ 10 K, v $\sim$ 10 km/s) could lift grains as large as 1 mm in the first $10^4$ yr of the protostellar lifetime if the mass loss rate of the protostar was high enough ($\sim10^{-6} \dot M_{\odot}$/yr). Among others, (cite: Brauer2008), (cite: Kawasaki2022), (cite: Bate2022), (cite: Lebreuilly2023) all find that growth up to cm-sized pebbles is extremely fast (a few $\sim 10^3$ yr) at the high density of the disk environment, thus producing the large grains that the outflow would entrain in the first place. Based on three-dimensional magneto-hydro-dynamical simulations, (cite: Lebreuilly2020) and (cite: Tsukamoto2021) found that the large dust grains grown in the inner region of a disk can be entrained by an outflow up to the envelope scales (up to 100 $\mu$m according to the first work, and even $>$1 mm for the second). These grains then decouple from the gas and are ejected from the outflow into the envelope itself, enriching its dust population before falling back to the disk.

(cite: chen16) found evidence for low $\beta$ correlated with protostellar outflow locations in Perseus. More recently, G19 observed a correlation between $\beta$ and the envelope mass of the CALYPSO sources, which might be in turn caused by a correlation between envelope mass and CO outflows fluxes (cite: Bontemps1996).

This two relationships together might support the scenario of disk dust transport into class 0/I protostellar envelopes.

While a more thorough treatment of this link for L1527 is outside of the scope of this work, we note that L1527 indeed hosts a large scale outflow structure in the east-west direction, perpendicular to the edge-on disk. (cite: Hogerheijde1998) observed the source with the James Clerk Maxwell Telescope and detected in $^{12}$CO ($J$=3–2) line emission an outflow extending over about 20000 au. Moreover, (cite: Tobin2010a) imaged this source with the Gemini North telescope (in its L’ band) and with the Infrared Array Camera (IRAC) on the Spitzer Space Telescope (2.15-8.0 $\mu$m), detecting the outflow cavity out to roughly 10000 au in both cases. Future investigations should consider whether the L1527 outflow can transport (sub)millimeter grains from the inner disk and lift them in the envelope. Such research is vital to our understanding the origin and consequences of relatively large grains at envelope scales, and may even shed light on this evolutionary stage of disk-based planet formation models.

## Caveats

Although we aim to present a more robust way of measuring the spectral index of the faint extended emission from the envelope of class 0/I YSOs, our analysis is not free of caveats. Additional work remains to further improve the reliability of our claims.

First, while we present a study of the spectral- and dust emissivity indices as a function of uv-distance and physical source scales, we have to keep in mind that a particular baseline does not only probe an annular region at some distance from the center, rather it probes any physical structure within a scale given by $\theta \sim \lambda/B$. It is for this reason that we have to model and subtract the disk from the visibility amplitudes before evaluating the spectral index for the envelope and, for the same reason, the $\alpha$ and $\beta$ we compute for the envelope at different scales represent a flux-weighted average over the relevant envelope spatial scales. If the inner envelope is much brighter than the outer one, as expected, the flux at even the shorter baselines will be dominated by the inner envelope. Thus, the spectral index value at these scales would still be mainly describing the inner region.

Second, in Section [4](#section:spindx) we have calculated the dust emissivity index $\beta$ of the envelope taking into account diskrepancies from the RJ approximation, hence accounting for a temperature profile, T $\propto$ R$^{-0.4}$. This power-law was derived for a dusty envelope illuminated by a central protostar (e.g., (cite: Terebey1993)). While the values we obtain using this proportionality are reasonable, as they do not reach values lower than typical cores temperatures at typical cores scales (10 K at 2000 au; e.g., (cite: Ferriere2001)), a more thorough treatment that accounts for the temperature structure and its associated uncertainties can be achieved by post-processing 3D envelope models with radiative transfer in order to.

# Conclusions

We aim to characterize the maximum grain size of the dust distribution in the envelope of a class 0/I YSO: L1527 IRS, or L1527 for short. Given its vicinity (140 pc), this source has been extensively studied over decades with different types of data and methodologies to investigate its star, extended envelope, and circumstellar disk both in the dust continuum and line emission. In this context, we exploit the richness of data from the Atacama Large (sub)millimeter Array to greatly enhance the S/N of the extended emission in the continuum and determine the peak of the dust grain population in the envelope that surrounds and infalls onto the young circumstellar disk of L1527.

We find that:

- The spectral index of the compact disk, i.e. within a radius of $\sim$ 75 au, is $\alpha_{0.88-3.4mm} = 2$, consistent with the expected high optical depth of its edge-on geometry. No dust grain properties information can be extracted in such a condition without thorough radiative transfer modelling, outside of the scope of this work.

- After subtraction of the inner disk emission and correction for the RJ approximation, we find tentative evidence for a positive outward gradient of the dust emissivity index of the envelope of L1527 ($\beta(R) \sim 0.37 \log$(R$_{au}$), which can be interpreted as variations of dust properties from ISM-like particles ($\beta \sim$ 1.6) at 2000 au down to grown grains below 300 au ($\beta \leq$1).

- The implications of physical and chemical properties of dust grains on the values of $\beta$ as well as the possible impact of the temperature profile used to calculate the correction for departure from the RJ approximation in computing the dust emissivity index (cfr Section [5.1](#section:beta_discuss)) is carefully discussed. None of these possibilities alone are able to justify $\beta$ values as low as 1 at hundreds of au, thus strengthening the hypothesis of submillimeter grains at these scales. While in situ formation seems disfavored by most theoretical studies, differential core dust collapse or outflow dust transport from the disk could explain our observations.

- We argue that a multiscale ($10^1-10^3$ au), multifrequency (n\>2), and high-sensitivity study is necessary to tightly constrain the spectral- and dust emissivity index profiles of faint class 0/I YSO envelopes. Using ALMA B3, B4, B6 and B7 effectively halves the error bars of measurements made in previous studies that made use of two wavelengths only.

ALMA has provided us with the necessary capabilities in terms of resolution, recoverable scales, sensitivity, and frequency ranges that are critical to the study of the continuum emission of faint, extended envelopes such as the one infalling onto the young protostar L1527. It is now the time to exploit this infrastructure to conduct sample studies of these objects with state-of-the-art data sets to finally pinpoint the initial conditions of grain growth and planet formation in both space and time.

# Acknowledgements

This work was partly supported by the Italian Ministero dell’Istruzione, Università e Ricerca through the grant Progetti Premiali 2012-iALMA (CUP C52I13000140001), by the Deutsche Forschungsgemeinschaft (DFG, German Research Foundation) - Ref no. 325594231 FOR 2634/2 TE 1024/2-1, by the DFG Cluster of Excellence Origins (www.origins-cluster.de). This project has received funding from the European Union’s Horizon 2020 research and innovation program under the Marie Sklodowska- Curie grant agreement No 823823 (DUSTBUSTERS) and from the European Research Council (ERC) via the ERC Synergy Grant ECOGAL (grant 855130). This research has received funding from the European Research Council (ERC) under the European Union’s Horizon 2020 research and innovation programme (MagneticYSOS project, Grant Agreement No 679937). D.J. is supported by NRC Canada and by an NSERC discovery Grant. We thank the entire ALMA team for their dedication to provide us with the data we used for this work. This paper makes use of the following ALMA data: ADS/JAO.ALMA#2015.1.00261.S, ADS/JAO.ALMA#2016.1.01245.S, ADS/JAO.ALMA#2016.1.01541.S, ADS/JAO.ALMA#2017.1.00509.S, ADS/JAO.ALMA#2018.1.01205.L, ADS/JAO.ALMA#2016.1.01203.S, ADS/JAO.ALMA#2012.1.00647.S, ADS/JAO.ALMA#2013.1.01086.S, ADS/JAO.ALMA#2012.1.00193.S, ADS/JAO.ALMA#2017.1.01413.S, ADS/JAO.ALMA#2011.0.00604.S, ADS/JAO.ALMA#2011.0.00210.S, ADS/JAO.ALMA#2013.1.01331.S, ADS/JAO.ALMA#2012.1.00346.S, ADS/JAO.ALMA#2015.1.01549.S, ADS/JAO.ALMA#2016.A.00011.S, ADS/JAO.ALMA#2018.1.00799.S, ADS/JAO.ALMA#2016.2.00171.S, ADS/JAO.ALMA#2016.2.00117.S. ALMA is a partnership of ESO (representing its member states), NSF (USA) and NINS (Japan), together with NRC (Canada), MOST and ASIAA (Taiwan), and KASI (Republic of Korea), in cooperation with the Republic of Chile. The Joint ALMA Observatory is operated by ESO, AUI/NRAO and NAOJ. We thank M. Troisi for his sharp comments, which supported LC during this work. We thank the referee for their comments, which helped to improve the quality of this work.

95 natexlab

(ref: AG2019) Agurto-Gangas, C., Pineda, J. E., Szűcs, L., et al. 2019, A&A, 623, A147

(ref: AlmaPartenership2015) ALMA Partnership, Brogan, C. L., Pérez, L. M., et al. 2015, ApJL, 808, L3

(ref: Andrews2018) Andrews, S. M., Huang, J., Pérez, L. M., et al. 2018, ApJL, 869, L41

(ref: Ansdell2016) Ansdell, M., Williams, J. P., van der Marel, N., et al. 2016, ApJ, 828, 46

(ref: Aso2017) Aso, Y., Ohashi, N., Aikawa, Y., et al. 2017, ApJ, 849, 56

(ref: Bate2022) Bate, M. R. 2022, MNRAS, 514, 2145

(ref: BeckwithSargent1991) Beckwith, S. V. W. & Sargent, A. I. 1991, ApJ, 381, 250

(ref: Bernabo2022) Bernabò, L. M., Turrini, D., Testi, L., Marzari, F., & Polychroni, D. 2022, ApJL, 927, L22

(ref: Birnstiel2016) Birnstiel, T., Fang, M., & Johansen, A. 2016, Space Sci. Rev., 205, 41

(ref: Bontemps1996) Bontemps, S., Andre, P., Terebey, S., & Cabrit, S. 1996, A&A, 311, 858

(ref: Brauer2008) Brauer, F., Dullemond, C. P., & Henning, T. 2008, A&A, 480, 859

(ref: Bridle1999) Bridle, A. H. & Schwab, F. R. 1999, in Astronomical Society of the Pacific Conference Series, Vol. 180, Synthesis Imaging in Radio Astronomy II, ed. G. B. Taylor, C. L. Carilli, & R. A. Perley, 371

(ref: Butner1990) Butner, H. M., Evans, Neal J., I., Harvey, P. M., et al. 1990, ApJ, 364, 164

(ref: chen16) Chen, M. C.-Y., Di Francesco, J., Johnstone, D., et al. 2016, ApJ, 826, 95

(ref: Chiang2012) Chiang, H.-F., Looney, L. W., & Tobin, J. J. 2012, ApJ, 756, 168

(ref: Codella2021) Codella, C., Ceccarelli, C., Chandler, C., et al. 2021, Frontiers in Astronomy and Space Sciences, 8, 227

(ref: Cridland2022) Cridland, A. J., Rosotti, G. P., Tabone, B., et al. 2022, A&A, 662, A90

(ref: draine2006) Draine, B. T. 2006, ApJ, 636, 1114

(ref: Draz2022) Drazkowska, J., Bitsch, B., Lambrechts, M., et al. 2022, arXiv e-prints, arXiv:2203.09759

(ref: Ferriere2001) Ferrière, K. M. 2001, Reviews of Modern Physics, 73, 1031

(ref: francis20) Francis, L., Johnstone, D., Herczeg, G., Hunter, T. R., & Harsono, D. 2020, AJ, 160, 270

(ref: Galametz2019) Galametz, M., Maury, A. J., Valdivia, V., et al. 2019, A&A, 632, A5

(ref: Goldreich1973) Goldreich, P. & Ward, W. R. 1973, ApJ, 183, 1051

(ref: Guillet2020) Guillet, V., Hennebelle, P., Pineau des Forêts, G., et al. 2020, A&A, 643, A17

(ref: Hogerheijde1998) Hogerheijde, M. R., van Dishoeck, E. F., Blake, G. A., & van Langevelde, H. J. 1998, ApJ, 502, 315

(ref: Johansen2009) Johansen, A., Youdin, A., & Klahr, H. 2009, ApJ, 697, 1269

(ref: Karska2018) Karska, A., Kaufman, M. J., Kristensen, L. E., et al. 2018, ApJS, 235, 30

(ref: Kawasaki2022) Kawasaki, Y., Koga, S., & Machida, M. N. 2022, MNRAS, 515, 2072

(ref: Kelly2007) Kelly, B. C. 2007, ApJ, 665, 1489

(ref: Kholer2015) Köhler, M., Ysard, N., & Jones, A. P. 2015, A&A, 579, A15

(ref: Kwon09) Kwon, W., Looney, L. W., Mundy, L. G., Chiang, H.-F., & Kemball, A. J. 2009, ApJ, 696, 841

(ref: Ladd1991) Ladd, E. F., Adams, F. C., Casey, S., et al. 1991, ApJ, 382, 555

(ref: LG2019) Le Gouellec, V. J. M., Hull, C. L. H., Maury, A. J., et al. 2019, ApJ, 885, 106

(ref: Lebreuilly2020) Lebreuilly, U., Commerçon, B., & Laibe, G. 2020, A&A, 641, A112

(ref: Lebreuilly2023) Lebreuilly, U., Vallucci-Goy, V., Guillet, V., Lombart, M., & Marchand, P. 2023, MNRAS, 518, 3326

(ref: Manara2018) Manara, C. F., Morbidelli, A., & Guillot, T. 2018, A&A, 618, L3

(ref: Maury2019) Maury, A. J., André, P., Testi, L., et al. 2019, A&A, 621, A76

(ref: McMullin2007) McMullin, J. P., Waters, B., Schiebel, D., Young, W., & Golap, K. 2007, in Astronomical Society of the Pacific Conference Series, Vol. 376, Astronomical Data Analysis Software and Systems XVI, ed. R. A. Shaw, F. Hill, & D. J. Bell, 127

(ref: Melis2011) Melis, C., Duchêne, G., Chomiuk, L., et al. 2011, ApJL, 739, L7

(ref: Miotello2014) Miotello, A., Testi, L., Lodato, G., et al. 2014, A&A, 567, A32

(ref: MiyakeNakagawa1993) Miyake, K. & Nakagawa, Y. 1993, Icarus, 106, 20

(ref: Motte2001) Motte, F. & André, P. 2001, A&A, 365, 440

(ref: Mulders2021) Mulders, G. D., Pascucci, I., Ciesla, F. J., & Fernandes, R. B. 2021, ApJ, 920, 66

(ref: Nakatani2020) Nakatani, R., Liu, H. B., Ohashi, S., et al. 2020, ApJL, 895, L2

(ref: Natta2004ASPC) Natta, A. & Testi, L. 2004, in Astronomical Society of the Pacific Conference Series, Vol. 323, Star Formation in the Interstellar Medium: In Honor of David Hollenbach, ed. D. Johnstone, F. C. Adams, D. N. C. Lin, D. A. Neufeeld, & E. C. Ostriker, 279

(ref: Natta2007) Natta, A., Testi, L., Calvet, N., et al. 2007, in Protostars and Planets V, ed. B. Reipurth, D. Jewitt, & K. Keil, 767

(ref: Ohashi1997) Ohashi, N., Hayashi, M., Ho, P. T. P., & Momose, M. 1997, ApJ, 475, 211

(ref: Ohashi2014) Ohashi, N., Saigo, K., Aso, Y., et al. 2014, ApJ, 796, 131

(ref: Ohashi2022) Ohashi, S., Nakatani, R., Liu, H. B., et al. 2022, ApJ, 934, 163

(ref: Okuzumi2016) Okuzumi, S., Momose, M., Sirono, S.-i., Kobayashi, H., & Tanaka, H. 2016, ApJ, 821, 82

(ref: Ormel2009) Ormel, C. W., Paszun, D., Dominik, C., & Tielens, A. G. G. M. 2009, A&A, 502, 845

(ref: Oya2015) Oya, Y., Sakai, N., Lefloch, B., et al. 2015, ApJ, 812, 59

(ref: Panagia1975) Panagia, N. & Felli, M. 1975, A&A, 39, 1

(ref: Plummer1911) Plummer, H. C. 1911, MNRAS, 71, 460

(ref: Podio2021) Podio, L., Tabone, B., Codella, C., et al. 2021, A&A, 648, A45

(ref: Remijan2019) Remjian, A., Biggs, A., Cortes, P. A., et al. 2019, ALMA Technical Handbook,ALMA Doc. 7.3, ver. 1.1, 2019, ALMA Technical Handbook,ALMA Doc. 7.3, ver. 1.1ISBN 978-3-923524-66-2

(ref: Ricci2010) Ricci, L., Testi, L., Natta, A., & Brooks, K. J. 2010, A&A, 521, A66

(ref: Safronov1969) Safronov, V. S. & Zvjagina, E. V. 1969, Icarus, 10, 109

(ref: Sakai2019) Sakai, N., Hanawa, T., Zhang, Y., et al. 2019, Nature, 565, 206

(ref: Sanchis2020) Sanchis, E., Testi, L., Natta, A., et al. 2020, A&A, 633, A114

(ref: Seguracox2020) Segura-Cox, D. M., Schmiedeke, A., Pineda, J. E., et al. 2020, Nature, 586, 228

(ref: Sheehan2018) Sheehan, P. D. & Eisner, J. A. 2018, ApJ, 857, 18

(ref: Sheehan2022) Sheehan, P. D., Tobin, J. J., Li, Z.-Y., et al. 2022, ApJ, 934, 95

(ref: shirley2002) Shirley, Y. L., Evans, Neal J., I., & Rawlings, J. M. C. 2002, ApJ, 575, 337

(ref: Shirley2011) Shirley, Y. L., Mason, B. S., Mangum, J. G., et al. 2011, AJ, 141, 39

(ref: Shu1977) Shu, F. H. 1977, ApJ, 214, 488

(ref: Silsbee2022) Silsbee, K., Akimkin, V., Ivlev, A. V., et al. 2022, arXiv e-prints, arXiv:2210.01832

(ref: Steinacker2015) Steinacker, J., Andersen, M., Thi, W. F., et al. 2015, A&A, 582, A70

(ref: Steinacker2014) Steinacker, J., Ormel, C. W., Andersen, M., & Bacmann, A. 2014, A&A, 564, A96

(ref: Steinacker2010) Steinacker, J., Pagani, L., Bacmann, A., & Guieu, S. 2010, A&A, 511, A9

(ref: Takahashi2014) Takahashi, S. Z. & Inutsuka, S.-i. 2014, ApJ, 794, 55

(ref: Takahashi2018) Takahashi, S. Z. & Muto, T. 2018, ApJ, 865, 102

(ref: Tazzari2018) Tazzari, M., Beaujean, F., & Testi, L. 2018, MNRAS, 476, 4527

(ref: Tazzari2021) Tazzari, M., Clarke, C. J., Testi, L., et al. 2021, MNRAS, 506, 2804

(ref: Testi2014) Testi, L., Birnstiel, T., Ricci, L., et al. 2014, in Protostars and Planets VI, ed. H. Beuther, R. S. Klessen, C. P. Dullemond, & T. Henning, 339

(ref: Testi2022) Testi, L., Natta, A., Manara, C. F., et al. 2022, A&A, 663, A98

(ref: Testi2003) Testi, L., Natta, A., Shepherd, D. S., & Wilner, D. J. 2003, A&A, 403, 323

(ref: Tielens1982) Tielens, A. G. G. M. & Hagen, W. 1982, A&A, 114, 245

(ref: Tobin2008) Tobin, J. J., Hartmann, L., Calvet, N., & D’Alessio, P. 2008, ApJ, 679, 1364

(ref: Tobin2012) Tobin, J. J., Hartmann, L., Chiang, H.-F., et al. 2012, Nature, 492, 83

(ref: Tobin2013) Tobin, J. J., Hartmann, L., Chiang, H.-F., et al. 2013, ApJ, 771, 48

(ref: Tobin2010a) Tobin, J. J., Hartmann, L., & Loinard, L. 2010, ApJL, 722, L12

(ref: Torres2007) Torres, R. M., Loinard, L., Mioduszewski, A. J., & Rodrı́guez, L. F. 2007, ApJ, 671, 1813

(ref: Tsukamoto2021) Tsukamoto, Y., Machida, M. N., & Inutsuka, S.-i. 2021, ApJL, 920, L35

(ref: Tychoniec2020) Tychoniec, Ł., Manara, C. F., Rosotti, G. P., et al. 2020, A&A, 640, A19

(ref: Valdivia2019) Valdivia, V., Maury, A., Brauer, R., et al. 2019, MNRAS, 488, 4897

(ref: Weingartner2001) Weingartner, J. C. & Draine, B. T. 2001, ApJ, 548, 296

(ref: Whitney2003) Whitney, B. A., Wood, K., Bjorkman, J. E., & Cohen, M. 2003, ApJ, 598, 1079

(ref: Williams2019) Williams, J. P., Cieza, L., Hales, A., et al. 2019, ApJL, 875, L9

(ref: Wong2016) Wong, Y. H. V., Hirashita, H., & Li, Z.-Y. 2016, PASJ, 68, 67

(ref: Xu2023) Xu, W. & Armitage, P. J. 2023, arXiv e-prints, arXiv:2302.04711

(ref: Youdin2005) Youdin, A. N. & Goodman, J. 2005, ApJ, 620, 459

(ref: Ysard2019) Ysard, N., Koehler, M., Jimenez-Serra, I., Jones, A. P., & Verstraete, L. 2019, A&A, 631, A88

(ref: Zhao2016) Zhao, B., Caselli, P., Li, Z.-Y., et al. 2016, MNRAS, 460, 2050

(ref: Zucker2019) Zucker, C., Speagle, J. S., Schlafly, E. F., et al. 2019, ApJ, 879, 125

# Continuum maps

While we have not conducted our analysis on the continuum maps, we have produced a set of images for each band during self-calibration, separately for the compact and extended array (see Section [2](#sec:data_red)). We here report both large-scale (ACA 7m-array) and higher resolution (ALMA 12m-array) continuum maps of L1527 for the bands we used in this work.

![](images_ref_report/ALMA_B3_image.png)

![](images_ref_report/ALMA_B4_image.png)

![](images_ref_report/ALMA_B6_image.png)

![](images_ref_report/ALMA_B7_image.png)

# Adjacent bands spectral index

In this study, we have used multiple wavelengths to study the continuum emission of the envelope of L1527. This is critical to damp the possible systematic errors that occur when only using fluxes at two wavelengths. We show the importance of this approach in what follows. We computed $\alpha$ between pair of bands as follows: $$\begin{equation}
    \alpha = \frac{log_{10}{F(\nu_2)}-log_{10}{F(\nu_1)}}{log_{10}{\nu_2}-log_{10}{\nu_1}}.
    \label{eq:alpha}
\end{equation}$$ To evaluate the uncertainties on the spectral index between two wavelengths, we propagate the errors of Eq.[\[eq:alpha\]](#eq:alpha): $$\begin{equation}
    \Delta\alpha^2 = \Bigg(\frac{1}{ln{\nu_2}-ln{\nu_1}}\Bigg)^2 \Bigg(\frac{\sigma_1^2}{F_{\nu_1}^2} + \frac{\sigma_2^2}{F_{\nu_2}^2}  \Bigg),
\end{equation}$$

![](images_ref_report/L1527_disc-subtracted_emission_only_B3-B4_ref_report.png)

![](images_ref_report/L1527_disc-subtracted_emission_only_B4-B6_ref_report.png)

![](images_ref_report/L1527_disc-subtracted_emission_only_B6-B7_ref_report.png)

![](images_ref_report/L1527_disc-subtracted_emission_only_B3-B6_ref_report.png)

where $\sigma_1$ and $\sigma_2$ are the uncertainties on the amplitudes in each uv-distance bin: $$\begin{equation}
    \sigma_i = \sqrt{ \Bigg(\frac{\partial F_i}{\partial Re_i} \Bigg)^2  dRe_i^2 +\Bigg(\frac{\partial F_i}{\partial Im_i} \Bigg)^2 dIm_i^2 + \Bigg(F_i \cdot dC \Bigg)^2}.
    \label{eq:amp_err}
\end{equation}$$ Here, ${Re}$ and ${Im}$ are the real and imaginary parts of the interferometric visibilities that make the amplitude as $F = \sqrt(Re^2 + Im^2)$, and $dC$ is the flux calibration error. We set the latter to 10% for B7 and 5% for B3, B4 and B6, following the prescriptions of the ALMA Handbook ((cite: Remijan2019), (cite: francis20)). We here show the spectral index of the envelope of L1527 as computed between adjacent bands, plus the one between B3 and B6. Figures [14](#fig:B34), [15](#fig:B46), [16](#fig:B67), [17](#fig:B36) show how, given the statistical errors and the proximity of the adjacent bands, the error on $\alpha$ can be large at the longest baselines. Moreover, the spectral index $\alpha$ shows systematic differences among different combination of adjacent bands. Only using multiple bands (\>2), one can robustly constrain the spectral index, damping the uncertainties that arise using only two frequencies (see Section [4](#section:spindx)).

# Fit results

As explained in Section [3](#sec:model), we fit a composite model to the visibilities. The model consists of a Gaussian component to trace the compact emission and a power law to better describe the extended emission. The disk radius, defined as the $2\sigma$ level of the Gaussian component is approximately 75 au, consistent with what was found kinematically by (cite: Aso2017). The disk contributes to the flux up to a maximum of 98% in B3, highlighting the necessity to combine as many ALMA datasets as possible and selfcalibrate them in order to enhance the faint extended continuum emission.

The disk results edge-on ($inc \sim 80^{\circ}$), consistently with several results throughout the literature with a position angle $PA \sim 2^{\circ}$, in a westward convention. The inner radius of the envelope is constrained to be in the range 0.01-0.15 arcseconds while the outer one is in the range 8-12 arcseconds, both depending on the band. Having phase-centered the datasets during the data calibration procedure, we find both dRA and dDec phase offsets consistent with zero. Finally, the power law exponent of the Plummer profile ($p$) is found to be in the range 2.6-3.1, roughly consistent with what was found by (cite: Ladd1991). We list the results of the fitting, that was carried out with galario, in Tab.[\[tab:fits_results\]](#tab:fits_results) and show the final model in Figures [4](#fig:fitband3), [18](#fig:B3fit), [19](#fig:B4fit), [20](#fig:B6fit), [21](#fig:B7fit).

![](images/uvplot_Band3_115ghz_logscale_G+P_noincl_60walker_2000_5000steps.png)

![](images/uvplot_Band4_logscale_G+P_noincl_50walker_2000_5000steps.png)

![](images_ref_report/uvplot_Band6_logscale_G+P_noincl_60walker_3000_7000steps.png)

![](images_ref_report/uvplot_Band7_logscale_G+P_noincl_50walker_3000_7000steps_ref_report.png)

| Parameter | Band 3 (88 GHz) | Band 3 (100 GHz) | Band 4 | Band 6 | Band 7 |
|:--:|:--:|:--:|:--:|:--:|:--:|
| $f_0$ (Jy/sr) | $10.47 \pm 0.02$ | $10.53 \pm 0.01$ | $10.79 \pm 0.03$ | $11.12 \pm 0.01$ | $11.51 \pm 0.01$ |
| $r$ | $0.90 \pm 0.01$ | $0.98 \pm 0.01$ | $0.74 \pm 0.01$ | $0.72 \pm 0.01$ | $0.38 \pm 0.01$ |
| $\sigma$ (") | $0.147 \pm 0.007$ | $0.151 \pm 0.001$ | $0.208 \pm 0.004$ | $0.270 \pm 0.001$ | $0.330 \pm 0.001$ |
| inc (deg) | $78 \pm 1$ | $80 \pm 1$ | $80 \pm 1$ | $82\pm1$ | $78 \pm 1$ |
| PA (deg) | $2.08\pm0.6$ | $2.27 \pm 0.02$ | $3.09 \pm 0.05$ | $2.3\pm0.01$ | $1.942 \pm 0.007$ |
| $R_{in}$ (") | $0.03\pm0.01$ | $0.14 \pm 0.01$ | $0.04 \pm 0.01$ | $0.08 \pm 0.02$ | $0.03\pm 0.01$ |
| $R_{out}$ (") | $9.9\pm0.1$ | $9.9 \pm 0.1$ | $12.8 \pm 0.1$ | $4.4 \pm 0.2$ | $1.35 \pm 0.1$ |
| $p$ | $2.62\pm0.01$ | $2.76 \pm 0.03$ | $2.75 \pm 0.01$ | $3.37 \pm 0.01$ | $2.54 \pm 0.02$ |
| dRA (") | $0.029\pm0.001$ | $0.029 \pm 0.001$ | $0.007 \pm 0.001$ | $0.001 \pm 0.001$ | $0.005 \pm 0.001$ |
| dDec (") | $-0.017\pm0.002$ | $-0.018 \pm 0.001$ | $-0.011 \pm 0.001$ | $0.008 \pm 0.005$ | $0.005 \pm 0.003$ |

[^1]: https://help.almascience.org/kb/articles/what-errors-could-originate-from-the-correlator-spectral-normalization-and-tsys-calibration

[^2]: https://casaguides.nrao.edu/index.php/DataWeightsAndCombination

[^3]: https://github.com/jmeyers314/linmix

</paper>

## Items to check

```json
[
 {
  "path": "analysis_steps[1].assumptions[0].evidence[0]",
  "value": "Envelope emission is constant within R_i, follows Plummer power law between R_i and R_out, and is zero beyond R_out; compact disk is represented by a 2D Gaussian",
  "failed_quote": "These are such that the envelope emission is constant within a radius $R_i$, it follows Eq. [eq:total_profile] between $R_i$ and $R_{out}$ and it is null beyond $R_{out}$."
 },
 {
  "path": "results_numeric[14].evidence[1]",
  "value": "Dust emissivity index at R = 300 au (and reported at 500 au) = 1.15 dimensionless",
  "failed_quote": "Secondly, G19 reported a fitted $\\beta_{500 au} = 1.41 \\pm 0.16$ while we find $\\beta_{500 au} = 1.15 \\pm 0.08$ based on Eq.[eq:beta]."
 }
]
```
