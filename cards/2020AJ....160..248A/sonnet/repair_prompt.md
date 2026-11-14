# Repair task for a Claude Code subagent

A methods card has evidence quotes that were not found verbatim in the paper. Below are the rules, the paper, and the failing items. Write ONE JSON object, nothing else, of the form {"repairs": [{"path": ..., "found": true|false, "loc": ..., "quote": ...}, ...]} with one entry per item (path unchanged) to:

    C:\Users\adama\alma-corpus\cards\2020AJ....160..248A\sonnet\repair_reply.txt

Use the Write tool for that file. Copy each quote character for character from the paper text below; a returned quote is checked mechanically and dropped if it is not in the paper. Do not read any other file, do not run commands, and do not change anything else. Reply with one line when done.

---

## Rules

You check evidence quotes for a methods card extracted from an astronomy paper. Some quotes could not be found verbatim in the paper text, and some stated values came without a quote. For each item: find the passage in the paper that supports the value and copy it VERBATIM (same words and order, at most 40 words; LaTeX markup may be dropped) with its loc (section heading, "abstract", "Table N" or "Figure N caption"). If the paper does not support the value, return found = false and leave quote and loc empty. Use only the paper text. Return one entry per item, with the item's path unchanged.

## Paper

<paper>
Draft version October 2, 2020
Typeset using L [A] TEX **twocolumn** style in AASTeX63


**An** **ALMA** **survey** **of** _λ_ **Orionis** **disks:** **from** **supernovae** **to** **planet** **formation**


Megan [Ansdell,](http://orcid.org/0000-0003-4142-9842) [1, 2] Thomas J. Haworth, [3] Jonathan P. Williams, [4] Stefano Facchini, [5] Andrew Winter, [6]

Carlo F. Manara, [5] Alvaro Hacar, [7] Eugene Chiang, [8] Sierk van Terwisga, [9] Nienke van der Marel, [10] and
Ewine F. van Dishoeck [7]


1 _Flatiron_ _Institute,_ _Simons_ _Foundation,_ _162_ _Fifth_ _Ave,_ _New_ _York,_ _NY_ _10010,_ _USA_
2 _NASA_ _Headquarters,_ _300_ _E_ _Street_ _SW,_ _Washington,_ _DC_ _20546,_ _USA_
3 _Astronomy_ _Unit,_ _School_ _of_ _Physics_ _and_ _Astronomy,_ _Queen_ _Mary_ _University_ _of_ _London,_ _London_ _E1_ _4NS,_ _United_ _Kingdom_
4 _Institute_ _for_ _Astronomy,_ _University_ _of_ _Hawai‘i_ _at_ _M¯anoa,_ _Honolulu,_ _HI,_ _USA_
5 _European_ _Southern_ _Observatory,_ _Karl-Schwarzschild-Str._ _2,_ _D-85748_ _Garching_ _bei_ _M¨unchen,_ _Germany_
6 _Astronomisches_ _Rechen-Institut,_ _Zentrum_ _f¨ur_ _Astronomie_ _der_ _Universit¨at_ _Heidelberg,_ _M¨onchhofstraße_ _12-14,_ _69120_ _Heidelberg,_ _Germany_
7 _Leiden_ _Observatory,_ _Leiden_ _University,_ _P.O._ _Box_ _9513,_ _2300-RA_ _Leiden,_ _The_ _Netherlands_
8 _Department_ _of_ _Astronomy,_ _University_ _of_ _California_ _at_ _Berkeley,_ _Berkeley,_ _CA_ _94720,_ _USA_
9 _Max-Planck-Institute_ _for_ _Astronomy,_ _K¨onigstuhl_ _17,_ _69117_ _Heidelberg,_ _Germany_
10 _Department_ _of_ _Physics_ _&_ _Astronomy,_ _University_ _of_ _Victoria,_ _Victoria,_ _BC,_ _V8P_ _1A1,_ _Canada_


(Accepted 18 Sept. 2020)


Submitted to AAS Journals


ABSTRACT


Protoplanetary disk surveys by the Atacama Large Millimeter/sub-millimeter Array (ALMA) are
now probing a range of environmental conditions, from low-mass star-forming regions like Lupus to
massive OB clusters like _σ_ Orionis. Here we conduct an ALMA survey of protoplanetary disks in
_λ_ Orionis, a _∼_ 5 Myr old OB cluster in Orion, with dust mass sensitivities comparable to the surveys
of nearby regions ( _∼_ 0.4 _M_ _⊕_ ). We assess how massive OB stars impact planet formation, in particular
from the supernova that may have occurred _∼_ 1 Myr ago in the core of _λ_ Orionis; studying these
effects is important as most planetary systems, including our Solar System, are likely born in cluster
environments. We find that the effects of massive stars, in the form of pre-supernova feedback and/or a
supernova itself, do not appear to significantly reduce the available planet-forming material otherwise
expected at the evolved age of _λ_ Orionis. We also compare a lingering massive “outlier” disk in _λ_ Orionis
to similar systems in other evolved regions, hypothesizing that these outliers host companions in their
inner disks that suppress disk dispersal to extend the lifetimes of their outer primordial disks. We
conclude with numerous avenues for future work, highlighting how _λ_ Orionis still has much to teach
us about perhaps one of the most common types of planet-forming environments in the Galaxy.


_Keywords:_ protoplanetary disks; planet formation; supernovae; OB stars; millimeter astronomy



1. INTRODUCTION


Thousands of diverse exoplanetary systems have now
been discovered (e.g., see review in Winn & Fabrycky
2015), yet how they all formed remains unclear due to
our still-incomplete understanding of the evolution of
the progenitor protoplanetary disks. These disks are


Corresponding author: Megan Ansdell;
� `[@megaparsec808](https://twitter.com/megaparsec808 )` ; � `[@mansdell](https://github.com/mansdell )`

[megan.c.ansdell@nasa.gov](mailto: megan.c.ansdell@nasa.gov)



traditionally thought to evolve through viscous accretion
(e.g., Lynden-Bell & Pringle 1974), where turbulence redistributes angular momentum and drives material onto
the central star. However other processes, both internal
and external to the disks, can also significantly influence
their evolution. In particular, the external influences of
massive OB stars on the disks of surrounding lower-mass
stars is important to study as many planetary systems,
including our Solar System, are likely born in cluster
environments (e.g., Adams 2010; Winter et al. 2020).

2 Ansdell et al.



In stellar clusters, the ultraviolet (UV) emission from
the OB stars induces thermal winds from nearby disks,
which effectively remove planet-forming material from
their outer regions in a process called “external photoevaporation” (e.g., Hollenbach et al. 1994). Theoretical work suggests that external photoevaporation can
severely shorten disk lifetimes and truncate outer disk
radii in cluster environments, whereas stellar encounters
play a relatively insignificant role in sculpting disk populations (e.g., Scally & Clarke 2001; Concha-Ram´ırez
et al. 2019), even in moderate UV environments (e.g.,
Facchini et al. 2016; Haworth et al. 2018; Winter et al.
2018). Moreover, external photoevaporation of the outer
disk is theorized to dominate over viscous spreading under realistic cluster conditions and dust grain growth
prescriptions (e.g., Clarke 2007; Facchini et al. 2016;
Winter et al. 2018). While direct detection of photoevaporative disk winds is observationally challenging, a
handful of cases exist (e.g., Henney & O’Dell 1999; Rigliaco et al. 2009). Meanwhile, indirect evidence of external photoevaporation from observations of its expected
impact on other disk properties is growing (e.g., Mann
et al. 2014; Kim et al. 2016; Guarcello et al. 2016; Ansdell et al. 2017; van Terwisga et al. 2019b).
Still, our understanding of how disk evolution is altered when one of these rapidly evolving OB stars inevitably goes supernova remains limited, due in part
to the lack of recent supernova events in nearby starforming regions (SFRs) available for study. This makes
the _λ_ Orionis cluster a key target, as a supernova is
thought to have occurred in the core of the region
_∼_ 1 Myr ago (e.g., Cunha & Smith 1996; Dolan & Mathieu 2001). At _∼_ 5 Myr of age (e.g., Hern´andez et al.
2009), _λ_ Orionis may therefore provide a rare snapshot
of an evolved SFR post-supernova, with the remaining
OB stars, lower-mass stellar population, and remnant
molecular cloud all still present. Supernovae are theorized to strip significant amounts of mass from disks
around nearby stars via ram pressure (e.g., Close & Pittard 2017) as well as expose them to enhanced cosmic
ray ionization rates that accelerate carbon processing
of CO into other molecules (e.g., Eistrup et al. 2016;
Schwarz et al. 2018a; Bosman et al. 2018), thereby providing predictions to test against observations.
A partial survey of the disk population in _λ_ Orionis was conducted at millimeter wavelengths by Ansdell et al. (2015) with JCMT/SCUBA-2. Observations
of disks at these longer wavelengths are particularly
useful because any optically thin continuum emission
can be related to the available planet-forming solids in
the disk (e.g., Hildebrand 1983; Andrews 2015), while
various molecular lines can probe gas content and/or



chemistry (e.g., Miotello et al. 2017; van Terwisga et al.
2019b; Miotello et al. 2019; Booth & Ilee 2020). How
_∼_
ever, due to the evolved age ( 5 Myr) and large distance
( _∼_ 400 pc) of _λ_ Orionis, combined with the limited sensitivity of JCMT/SCUBA-2, Ansdell et al. (2015) detected only one disk in their survey. Fortunately, the Atacama Large Millimeter/sub-millimeter Array (ALMA)
now provides the high sensitivity required to efficiently
survey the disk population in _λ_ Orionis to dust mass
sensitivities that are commonly achieved for the nearby
( _∼_ 150 pc) SFRs like Lupus (Ansdell et al. 2016, 2018),
Chamaeleon I (Pascucci et al. 2016), _ρ_ Ophiuchus (Cieza
et al. 2019), and Upper Sco (Barenfeld et al. 2016). This
paper presents the results of such an ALMA survey.
We begin in Section 2 by discussing the formation and
evolution of _λ_ Orionis, as the cluster’s history is central
to our analysis. In Section 3, we describe our sample of
protoplanetary disks and their host star properties. Our
ALMA survey of these disks and the key observational
results are presented in Section 4, while the basic disk
properties are derived in Section 5. We then examine the
implications for our understanding of how OB stars affect disk evolution in Section 6, which also discusses how
massive “outlier” disks in evolved regions like _λ_ Orionis
may improve our knowledge on the pathways of planet
formation and disk dispersal. We summarize our findings and provide avenues for future work in Section 7.


2. THE _λ_ ORIONIS CLUSTER


The formation, evolution, and current state of the
_λ_ Orionis cluster has been studied and debated in many
works (e.g., Maddalena & Morris 1987; Cunha & Smith
1996; Dolan & Mathieu 2001; Hern´andez et al. 2009;
Bayo et al. 2011; Mathieu 2015; Kounkel et al. 2018).
In this section, we briefly summarize the existing observations of the cluster, then assume a commonly adopted
but still-debated interpretation, which has implications
for our later analysis.
As illustrated in Figure 1, _λ_ Orionis currently consists
of several hundred low-mass members centered on a core

of OB stars. The most massive is the O8III star, _λ_ Ori,
the brightest in the head of the Orion constellation. Although _λ_ Ori is the only O-type star in the cluster, it has
a B0V companion at 1900 au projected separation, and
this binary system is accompanied by nine other B-type
stars (some close binaries themselves) in a dense _∼_ 2 pc
radius clump in the cluster center (Murdin & Penston
1977). The interstellar dust and molecular gas in the
region is largely confined to a _∼_ 30 pc radius ring (or
possibly shell; Lee et al. 2015), which is centered on the
clump of OB stars, encompasses the lower-mass population, and is rapidly expanding at _∼_ 14 km s _[−]_ [1] (e.g.,

ALMA Survey of _λ_ Orionis Disks 3




### 12° 10° 8°






### 5 [h] 48 [m] 42 [m] 36 [m] 30 [m] 24 [m]

## Right Ascension

**Figure** **1.** An IRAS 100- _µ_ m image of the _λ_ Orionis cluster. The white dashed box outlines the region surveyed for disks with
_Spitzer_ in Hern´andez et al. (2009, 2010), which we use as the basis of our ALMA survey sample selection (Section 3.1). The
inset zooms in on this region: the large circles are our ALMA detections color-coded by dust mass (Section 5.1), while the small
gray circles are the non-detections (Section 4.2); the dotted lines represent 1 pc and 3 pc radial distances from the _λ_ Ori system
at the center of the cluster. Gray arrows show the _Gaia_ DR2 proper motions of the cluster members identified by Kounkel et al.
(2018) in the LSR frame with the median cluster value subtracted; a reference vector of magnitude 1 mas yr _[−]_ [1] and a scale bar
of 5 pc are shown in the lower right corner. The small white stars are the locations of the B-type stars in the region, and the
larger white star is the location of the _λ_ Ori system, which contains the only O-type star in the region (Section 2).

4 Ansdell et al.



Maddalena & Morris 1987; Lang et al. 2000). As shown
in Figure 1, many of the _λ_ Orionis members also have
proper motions directed radially away from the cluster
center, with the more distant stars moving away the
fastest (Kounkel et al. 2018).
The age of the lower-mass stellar population in _λ_ Orionis is _∼_ 5 Myr (e.g., Dolan & Mathieu 2001; Hern´andez
et al. 2009). This is largely based on Str¨omgren photometry of the most massive OB stars, which suggests
their formation occurred _∼_ 6 Myr ago, combined with
photometric and spectroscopic surveys of the surrounding pre-main sequence stars, which indicate an epoch
of lower-mass star formation that began soon after but
was halted _∼_ 1–2 Myr ago (Dolan & Mathieu 1999,
2001). In this work we do _not_ consider the younger
dark Barnard 30 and Barnard 35 clouds, located along
the edge of the ring, as part of the _λ_ Orionis cluster.
We adopt the common interpretation in the literature
of these observations, which is that an O-type star exploded as a supernova _∼_ 1 Myr ago in the cluster core,
carving out the central cloud to create the molecular
ring/shell, while terminating star formation in the region (Cunha & Smith 1996; Dolan & Mathieu 1999,
2001; Mathieu 2008, 2015). However, we note that
pre-supernova feedback may also carve out central cavities in molecular clouds (e.g., Dale et al. 2014). Moreover, although the radial motions of the _λ_ Orionis members have been attributed to a “single-trigger” expansion caused by the supernova (Kounkel et al. 2018),
such kinematics can result from any mechanism that
removes the interstellar gas and its gravitational potential (Winter et al. 2019), and outward acceleration may
even be aided by gravitational feedback of the dispersed
gas (Zamora-Avil´es et al. 2019). While these and other
caveats are discussed further in Section 6.1, the massive
stars in _λ_ Orionis, whether through pre-supernova feedback and/or a supernova event itself, have played a key
role in shaping the region.


3. SAMPLE


3.1. _Disk_ _Sample_ _Selection_


Like most SFRs, the disk census in _λ_ Orionis is based
on targeted _Spitzer_ observations, which can identify
stars exhibiting excess emission above the stellar photosphere at near-infrared (IRAC 3.6, 4.5, 5.8, and 8.0 _µ_ m;
Fazio et al. 2004) and/or mid-infrared (MIPS 24 _µ_ m;
Rieke et al. 2004) wavelengths where dust emits efficiently. Hern´andez et al. (2009) used _Spitzer_ data to
study the intermediate-mass population in _λ_ Orionis,
finding 29 members earlier than F5 but only 10 bearing disks; they classified the nine sources with moderate infrared excess as debris disks and the one source



with large infrared excess as an optically thick disk.
Hern´andez et al. (2010) then studied the lower-mass
population in _λ_ Orionis, finding 436 members down to
the substellar limit but only 49 with disks; they grouped
the disks according to their spectral energy distributions
(SEDs)—optically thick disks had the largest excesses,
evolved disks had smaller excesses, and (pre-)transition
disks exhibited signs of inner disk clearings. We exclude from our sample the nine debris disks, as these
are likely second-generation dust disks (Wyatt 2008),
resulting in an initial sample of 50 primordial (or protoplanetary) disks. We use the same naming conventions
as Hern´andez et al. (2009, 2010) in this work.
As shown in Figure 1, the region surveyed by _Spitzer_
(white box) only covers _∼_ 3 pc from the cluster center. Recent kinematic studies of the Orion Complex
using astrometric data from _Gaia_ (Gaia Collaboration
et al. 2016) Data Release 2 (DR2; Gaia Collaboration
et al. 2018) combined with spectroscopic data from the
Apache Point Observatory Galactic Evolution Experiment (APOGEE; Majewski et al. 2017) revealed a population of radially expanding _λ_ Orionis members that
extend well beyond this area (Kounkel et al. 2018). Surveys for disks in these outer regions have not yet been
conducted, making it possible that our ALMA sample
based solely on _Spitzer_ data is incomplete. Nevertheless, the low protoplanetary disk fraction in _λ_ Orionis
inferred from the _Spitzer_ data is consistent with the
_∼_ 5 Myr age of the cluster, as it follows the well-known
exponential decline in disk frequency with age (e.g., see
Figure 14 in Hern´andez et al. 2007). Moreover, the issue of a potentially incomplete disk census when using
targeted _Spitzer_ observations for the sample selection is
a general (albeit moderate) problem facing the ALMA
disk demographic literature, as _Gaia_ continues to reveal
missed or interloping stellar populations in young SFRs
(e.g., Manara et al. 2018b; Galli et al. 2020; Luhman &
Esplin 2020). We also note that the radially expanding
population missed by _Spitzer_ is unlikely to represent a
younger population formed as a consequence of the supernova and/or feedback from the massive OB stars, as
Dolan & Mathieu (1999, 2001) found no evidence for
triggered or sequential star formation in the region.
We identify interlopers in the _Spitzer_ sample by using distances from _Gaia_ DR2 to find contaminant background sources—a method that has been previously applied to refine membership in the Lupus clouds (Manara et al. 2018b). While the individual _Gaia_ DR2 parallaxes of _λ_ Orionis members remain imprecise due to
the cluster’s distance, they are sufficient for identifying clear interlopers. We therefore remove five sources
(LO 1310, 2357, 2404, 5042, and 7517) from our sample,

ALMA Survey of _λ_ Orionis Disks 5


**Table** **1.** Source Properties


Source 2MASS ID R.A. Decl. SpT _M_ _⋆_ _v_ LSR Ref. _[†]_ _µ_ _α_ _µ_ _δ_


( _M_ _⊙_ ) (km s _[−]_ [1] ) (mas yr _[−]_ [1] ) (mas yr _[−]_ [1] )


LO 65 J05331515+0950301 05:33:15.15 +09:50:30.05 M4 0.19 11.5 _±_ 0.2 2,4 -0.64 _±_ 0.28 -1.00 _±_ 0.23

LO 1079 J05334791+1001396 05:33:47.91 +10:01:39.69 M5.5 0.07 ... 1 2.11 _±_ 0.49 -2.68 _±_ 0.41

LO 1152 J05334992+0950367 05:33:49.93 +09:50:36.79 M3.0 0.29 7.5 _±_ 0.1 1,4 2.65 _±_ 0.10 -3.31 _±_ 0.08

LO 1359 J05335661+1006149 05:33:56.61 +10:06:14.91 M5.25 0.08 ... 1 -0.68 _±_ 1.16 -1.90 _±_ 0.83

LO 1589 J05340393+0952122 05:34:03.94 +09:52:12.30 M2.5 0.35 8.2 _±_ 0.3 1,4 2.82 _±_ 0.12 -3.25 _±_ 0.09

LO 1624 J05340495+0957038 05:34:04.96 +09:57:03.76 M3 0.29 12.0 _±_ 0.1 2,4 0.27 _±_ 0.07 -2.14 _±_ 0.06

LO 1840 J05341141+0942079 05:34:11.41 +09:42:07.94 M6.0 0.09 ... 1 1.24 _±_ 0.25 -2.91 _±_ 0.21

LO 2088 J05341927+0948275 05:34:19.27 +09:48:27.51 M7.0 0.04 12.1 _±_ 0.5 1,5 -2.06 _±_ 1.52 -1.03 _±_ 1.32

LO 7957 ... 05:34:36.28 +09:55:32.20 M8.0 ... ... 1 ... ...

LO 2712 J05343836+0958116 05:34:38.36 +09:58:11.63 M7 0.04 ... 2 2.85 _±_ 2.18 -5.91 _±_ 1.85

LO 2989 J05344621+0955376 05:34:46.21 +09:55:37.65 M5.5 0.07 12.7 _±_ 0.4 1,5 -0.63 _±_ 1.01 -1.62 _±_ 0.85

LO 2993 J05344631+1002318 05:34:46.32 +10:02:31.87 M5.0 0.08 ... 1 -1.79 _±_ 0.69 -3.57 _±_ 0.60

LO 3360 J05345639+0955045 05:34:56.40 +09:55:04.46 M4.0 0.19 10.7 _±_ 0.1 1,4 0.84 _±_ 0.33 -2.65 _±_ 0.25

LO 3506 J05350015+0952408 05:35:00.16 +09:52:40.88 M8 0.03 13.3 _±_ 0.7 2,5 5.26 _±_ 3.29 0.12 _±_ 2.76

LO 3597 J05350274+0956475 05:35:02.74 +09:56:47.58 M4.0 0.19 12.3 _±_ 0.2 1,4 0.57 _±_ 0.12 -2.00 _±_ 0.10

LO 3746 J05350707+0954014 05:35:07.07 +09:54:01.48 M6 0.06 12.7 _±_ 0.4 2,5 0.56 _±_ 0.62 -1.84 _±_ 0.49

LO 7951 ... 05:35:07.95 +10:00:06.26 M6.0 ... ... 1 ... ...

LO 3785 J05350833+0942537 05:35:08.34 +09:42:53.79 K4 1.04 14.5 _±_ 0.3 2,4 1.59 _±_ 0.07 -1.96 _±_ 0.06

HD 245185 J05350960+1001515 05:35:09.60 +10:01:51.43 A0 2.26 ... 3 0.34 _±_ 0.14 -1.93 _±_ 0.10

LO 3887 J05351112+0957195 05:35:11.13 +09:57:19.58 M5.0 0.09 12.8 _±_ 0.4 1,5 0.58 _±_ 0.37 -2.19 _±_ 0.33

LO 3942 J05351255+0953111 05:35:12.56 +09:53:11.14 M3.0 0.30 11.2 _±_ 0.3 1,4 1.44 _±_ 0.60 -2.96 _±_ 0.46

LO 4021 J05351533+0948369 05:35:15.33 +09:48:36.96 M3.0 0.33 11.6 _±_ 0.3 1,5 0.65 _±_ 0.21 -1.96 _±_ 0.16

LO 4111 J05351792+0956571 05:35:17.92 +09:56:57.20 M4 0.19 12.0 _±_ 0.3 2,5 1.13 _±_ 0.23 -1.94 _±_ 0.17

LO 4126 J05351818+0952241 05:35:18.18 +09:52:24.17 M2.0 0.44 11.7 _±_ 0.4 1,5 0.50 _±_ 0.21 -1.70 _±_ 0.16

LO 4155 J05351904+0954550 05:35:19.05 +09:54:55.74 K2 1.40 12.9 _±_ 0.5 1,4 0.93 _±_ 0.08 -2.19 _±_ 0.06

LO 4163 J05351913+0954424 05:35:19.14 +09:54:42.38 M4.0 0.19 11.2 _±_ 0.4 1,5 0.21 _±_ 0.20 -2.03 _±_ 0.16

LO 4187 J05351991+1002364 05:35:19.92 +10:02:36.51 M1.0 0.50 9.2 _±_ 0.3 1,6 2.66 _±_ 0.09 -2.76 _±_ 0.07

LO 4255 J05352151+0953291 05:35:21.52 +09:53:29.21 M5 0.10 12.1 _±_ 0.3 2,5 0.12 _±_ 0.36 -1.47 _±_ 0.35

LO 4363 J05352440+0953519 05:35:24.41 +09:53:51.94 M5.5 0.07 12.3 _±_ 0.4 1,5 0.35 _±_ 0.64 -0.18 _±_ 0.50

LO 4407 J05352536+1008383 05:35:25.36 +10:08:38.25 M3 0.29 11.2 _±_ 0.2 2,4 1.71 _±_ 0.54 -4.05 _±_ 0.43

LO 4520 J05352846+1002275 05:35:28.46 +10:02:27.44 M3.5 0.25 ... 1 0.62 _±_ 0.16 -1.56 _±_ 0.12

LO 4531 J05352877+0954101 05:35:28.78 +09:54:10.08 M5.5 0.07 11.9 _±_ 0.3 1,5 1.51 _±_ 0.71 -2.74 _±_ 0.62

LO 4817 J05353722+0956517 05:35:37.23 +09:56:51.72 M4 0.20 ... 2 0.82 _±_ 0.20 -2.28 _±_ 0.16

LO 4916 J05353984+0953240 05:35:39.85 +09:53:24.06 M6.5 0.05 11.8 _±_ 0.7 1,5 ... ...

LO 5267 J05355094+0938567 05:35:50.95 +09:38:56.69 M4 0.19 ... 1 0.87 _±_ 0.28 -1.77 _±_ 0.21

LO 5447 J05355585+0956217 05:35:55.86 +09:56:21.75 M1.5 0.24 10.8 _±_ 0.2 1,4 0.98 _±_ 0.13 -1.87 _±_ 0.10

LO 5679 J05360288+0942074 05:36:02.88 +09:42:07.50 M1 0.47 11.4 _±_ 0.1 2,4 2.16 _±_ 0.09 -2.28 _±_ 0.06

LO 5916 J05360981+0942370 05:36:09.81 +09:42:37.02 M6.0 0.05 11.8 _±_ 0.5 1,5 0.58 _±_ 1.07 -2.09 _±_ 0.98

LO 6191 J05361810+0952254 05:36:18.11 +09:52:25.41 M6.0 0.06 11.9 _±_ 0.5 1,5 1.39 _±_ 0.82 -3.26 _±_ 0.61

LO 6866 J05363804+0940509 05:36:38.07 +09:40:50.18 K7 0.67 11.9 _±_ 0.2 2,4 0.60 _±_ 0.12 -1.79 _±_ 0.11

LO 6886 J05363861+0935052 05:36:38.61 +09:35:05.22 M3 0.29 11.5 _±_ 0.2 2,4 0.83 _±_ 0.44 -2.14 _±_ 0.36

LO 7402 J05365309+0941556 05:36:53.09 +09:41:55.67 K4 1.05 13.6 _±_ 0.1 2,4 1.96 _±_ 0.06 -1.97 _±_ 0.05

LO 7490 J05365533+0946479 05:36:55.34 +09:46:47.94 M3 0.33 ... 1 1.15 _±_ 0.18 -2.54 _±_ 0.17

LO 7528 J05365617+0931227 05:36:56.17 +09:31:22.70 M1.5 0.42 9.5 _±_ 0.2 1,4 ... ...


_†_ References for stellar spectral types (SpT) and radial velocities ( _v_ LSR ): (1) Bayo et al. (2011), (2) Hern´andez et al. (2010), (3)
Hern´andez et al. (2009), (4) Kounkel et al. (2018), (5) Maxted et al. (2008), (6) Sacco et al. (2008).

6 Ansdell et al.



as the lower bounds of their estimated _Gaia_ DR2 distances from Bailer-Jones et al. (2018) are _>_ 480 pc, making them likely background sources. Indeed, LO 1310
and LO 2357 have radial velocities in the local standard of rest (LSR) reference frame of _v_ LSR = 1 _._ 3 and
_−_ 35 km s _[−]_ [1], respectively, which differ significantly from
the average cluster value of 12 km s _[−]_ [1] (Kounkel et al.
2018); LO 2404, 5042, and 7517 do not have known radial velocities. We also remove LO 3710, found to be a
non-member by Bayo et al. (2011) due to a discrepant
surface gravity. Of these interlopers, only LO 7517
is detected by our ALMA survey at marginal (3.4 _σ_ )
significance; given its estimated _Gaia_ DR2 distance of
3744 [+405] _−_ 336 [pc,] [it] [is] [likely] [a] [background] [galaxy.]
Table 1 gives our final sample of the 44 protoplanetary
disks analyzed in the remainder of this work.


3.2. _Host_ _Star_ _Properties_


The available host star properties for our disk sample
are provided in Table 1. Stellar spectral types (SpT)
were mostly determined by Bayo et al. (2011) from
moderate-resolution optical and near-infrared spectra.
However, 14 stars have only photometric spectral types
from Hern´andez et al. (2010), who interpolated _R−J_ colors onto the spectral type sequence using the standard
_R−J_ colors from Kenyon & Hartmann (1995). Although
the _R −_ _J_ colors were not corrected for reddening, the
reddening toward _λ_ Orionis is low at _E_ ( _B −_ _V_ ) _≈_ 0 _._ 12
(Diplas & Savage 1994) and these photometric spectral types match well (typically _±_ 1 spectral sub-type)
to the spectroscopically determined values from Bayo
et al. (2011) when the samples overlap.
The host star proper motions in right ascension ( _µ_ _RA_ )
and declination ( _µ_ _Dec_ ) are from _Gaia_ DR2. Radial velocities are also provided and taken from various literature sources, translated into the LSR reference frame
( _v_ LSR ) using the source coordinates. The source coordinates in right ascension (R.A.) and declination (Decl.)
are the fitted positions for our ALMA detections (Section 4.2) or the Two Micron All-Sky Survey (2MASS;
Skrutskie et al. 2006) positions for the non-detections.
As previously mentioned, the _λ_ Orionis cluster is
too distant for reliable individual _Gaia_ DR2 parallaxes.
This is further complicated for young, disk-hosting stars
whose variability from disk scattered light and/or surrounding nebulosity can result in poor fits to the _Gaia_
DR2 single-star astrometric model, leading to higher astrometric noise. Thus we do not provide distance estimates for each source in our sample, but rather rely on
the average distance of the non-disk-bearing members
in _λ_ Orionis from _Gaia_ DR2, which is well-constrained
to 404 _±_ 4 pc (Kounkel et al. 2018) and consistent with



earlier estimates of 450 _±_ 50 pc based on main-sequence
fitting to the massive OB stars (Dolan & Mathieu 2001;
Mathieu 2015). We therefore adopt a distance of 400 pc
for _λ_ Orionis in the remainder of this work.
We estimate stellar masses ( _M_ _⋆_ ) from these SpT values and 2MASS _J_ -band magnitudes, following the methods of Ansdell et al. (2017). Each target is placed on
the HertzsprungRussel (HR) diagram by converting SpT
to stellar effective temperature and _J_ -band magnitude
to stellar luminosity using the relations from Herczeg
& Hillenbrand (2015) and a distance of 400 pc. Estimates of _M_ _⋆_ are then found by comparing the positions on the HR diagram to the evolutionary models
of Baraffe et al. (2015). For the one intermediate-mass
star, HD 245185, we instead use the evolutionary models
of Siess et al. (2000). We do not provide _M_ _⋆_ estimates
for the two sources without 2MASS data (LO 7957 and
LO 7951). The typical _M_ _⋆_ uncertainties, propagated
from the uncertainties on SpT and _J_ -band magnitude,
are 0.1–0.2 _M_ _⊙_ .


4. ALMA OBSERVATIONS & RESULTS


4.1. _ALMA_ _Observations_


The ALMA observations used in this work were taken
in Cycle 5 under program 2017.1.00466.S (PI: Ansdell).
The program allowed for a range of array configurations to maximize the probability of survey completion,
and the observations were conducted over 13 execution
blocks (see Appendix A for information on the array
configuration and weather conditions for each execution
block). All sources in our sample were observed during
each execution block, thus the sensitivities and synthesized beams are uniform across the sample.
The spectral setup was identical for each execution
block: four spectral windows were centered on 247.96,
245.46, 232.97, and 230.51 GHz, each with usable bandwidths of 1.88 GHz, for a bandwidth-weighted mean
continuum frequency of 239.36 GHz (1.25 mm). The
last spectral window covered the [12] CO _J_ = 2 _−_ 1 transition at moderate ( _∼_ 1 km s _[−]_ [1] ) spectral resolution to
preserve the maximum possible continuum bandwidth
while allowing for the possibility of detecting molecular
gas emission.
On-source integration times were _∼_ 6 min per source,
chosen so the 3 _σ_ dust mass constraints would be comparable to the limits reached in the ALMA surveys of more
nearby SFRs (e.g., Barenfeld et al. 2016; Ansdell et al.
2016; Pascucci et al. 2016), assuming a linear relation
between millimeter flux and dust mass (e.g., Hildebrand
1983). Data were pipeline calibrated by NRAO staff
using the Common Astronomy Software Applications
( `CASA` ) package (McMullin et al. 2007) version 5.4.0.

ALMA Survey of _λ_ Orionis Disks 7

|HD245185|LO4187|LO1624|LO4407|LO4155|LO6866|LO4163|
|---|---|---|---|---|---|---|
|LO 4531|LO 4520|LO 5267|LO 3360|LO 1152|LO 65|LO 4255|



**Figure** **2.** ALMA 1.25 mm continuum images of the 14 detected disks in our _λ_ Orionis sample, ordered by decreasing flux
density (as reported in Table 2). The 2 _[′′]_ _×_ 2 _[′′]_ images are centered on the source, scaled to their maximum value, and clipped
below 1.5 _σ_ for clarity. The typical beam size of _∼_ 0.3 _[′′]_ is shown in the first panel by the white ellipse.



The pipeline included flux, bandpass, and gain calibrations (see Appendix A for a list of the calibrators). We
assume an absolute flux calibration uncertainty of 10%,
similar to other ALMA disk surveys (e.g., Barenfeld
et al. 2016; Ansdell et al. 2016; Cazzoletti et al. 2019).


4.2. _ALMA_ _Continuum_ _Results_


We create continuum images from the calibrated visibilities by averaging over the continuum channels using
the `split` task in `CASA`, then cleaning with a Briggs
robust weighting parameter of +0 _._ 5 using the `tclean`
task. This results in a median continuum rms of 34 _µ_ Jy
and beam size of 0 _._ 31 _[′′]_ _×_ 0.29 _[′′]_ . We do not perform selfcalibration as the detected sources are faint, with a median signal-to-noise ratio of 15 (see Table 2).
In most cases, we measure continuum flux densities by
fitting point source models to the visibility data with the
`uvmodelfit` task in `CASA` . The point source model has
three free parameters: integrated flux density ( _F_ 1 _._ 25mm ),
right ascension offset from the phase center (∆ _α_ ), and
declination offset from the phase center (∆ _δ_ ). For the
non-detections, we fix ∆ _α_ and ∆ _δ_ to zero when running
`uvmodelfit` to avoid spurious detections (the phase offsets are typically only 0.05 _[′′]_ for the detections, much
smaller than the beam size). In three cases, the sources
are resolved, therefore we use an elliptical Gaussian
model instead, which has three additional parameters:
full-width-half-max along the major axis ( _a_ ), aspect ratio of the axes ( _r_ ), and position angle (P _._ A _._ ). With the
underlying assumption that these models describe the
data appropriately, we multiply the uncertainties on all
the fitted parameters by the factor needed to produce a
reduced _χ_ [2] of 1 (typically a factor of two).
Table 2 reports the _F_ 1 _._ 25mm values for all sources,
along with their statistical uncertainties (i.e., not includ


ing the 10% flux calibration error), while Figure 2 shows
the continuum images for the _≥_ 3 _σ_ detections. Only 14
of the 44 sources are detected at _≥_ 3 _σ_ significance and
only 3 of the detections are marginally resolved. We
conservatively identify resolved sources as those where
the ratio of _a_ to its uncertainty is greater than five. The
resolved sources are HD 245185, LO 4187, and LO 4407
with the following fitted elliptical Gaussian parameters, respectively: _a_ = 0 _._ 203 _[′′]_ _±_ 0.002 _[′′]_, 0.113 _[′′]_ _±_ 0.015 _[′′]_,
and 0.123 _[′′]_ _±_ 0.022 _[′′]_ ; _r_ = 0 _._ 807 _±_ 0.006, 0.710 _±_ 0.196, and
0.508 _±_ 0.380; P _._ A _._ = 70 _._ 1 _[◦]_ _±_ 0.9 _[◦]_, _−_ 1 _._ 3 _[◦]_ _±_ 19.5 _[◦]_, and

85.5 _[◦]_ _±_ 18.7 _[◦]_ .

We stack the images of the 30 non-detections to
constrain the average continuum flux for the individually undetected sources, finding a tentative detection
of 0 _._ 019 _±_ 0 _._ 006 mJy (3.2 _σ_ ) in the stacked image. We
verify this result by calculating the mean continuum
flux density and standard error on the mean for the 30
non-detections using the values in Table 2, which gives
0 _._ 020 _±_ 0 _._ 005 mJy (4.0 _σ_ ).


4.3. _ALMA_ _CO_ _Results_


We extract [12] CO channel maps from the calibrated
visibilities by first subtracting the continuum using the
`uvcontsub` task in `CASA` . To search for [12] CO emission,
we follow the general procedure of Ansdell et al. (2017).
In short, we extract an initial spectrum for each source
to identify candidate detections with emission exceeding 3 _×_ the channel rms near the expected _v_ LSR of the
cluster (12 km s _[−]_ [1] ; Kounkel et al. 2018). These candidates are visually inspected and any emission is cleaned
with a Briggs robust weighting parameter of +0 _._ 5 using
`tclean` . Zero-moment maps are then created by summing the channels _±_ 3 km s _[−]_ [1] from the systemic velocity unless clear emission was seen beyond these limits.

8 Ansdell et al.



**Table** **2.** ALMA Disk Fluxes


Source _F_ 1 _._ 25mm _F_ 12CO


(mJy) (mJy km s _[−]_ [1] )


LO 65 0.117 _±_ 0.030 _<_ 25


LO 1079 0.033 _±_ 0.030 _<_ 24


LO 1152 0.159 _±_ 0.028 _<_ 24


LO 1359 0.053 _±_ 0.028 _<_ 23


LO 1589 0.053 _±_ 0.028 _<_ 24


LO 1624 1.179 _±_ 0.028 _<_ 24


LO 1840 -0.008 _±_ 0.030 _<_ 24


LO 2088 -0.005 _±_ 0.028 _<_ 24


LO 7957 0.075 _±_ 0.028 _<_ 24


LO 2712 -0.033 _±_ 0.028 _<_ 25


LO 2989 0.076 _±_ 0.028 _<_ 23


LO 2993 0.008 _±_ 0.030 _<_ 24


LO 3360 0.234 _±_ 0.028 _<_ 24


LO 3506 0.016 _±_ 0.030 _<_ 25


LO 3597 -0.063 _±_ 0.030 _<_ 25


LO 3746 0.047 _±_ 0.030 _<_ 24


LO 7951 0.038 _±_ 0.028 _<_ 25


LO 3785 0.035 _±_ 0.034 _<_ 28


HD 245185 33.955 _±_ 0.056 1915 _±_ 51


LO 3887 0.024 _±_ 0.028 _<_ 23


LO 3942 -0.001 _±_ 0.028 _<_ 24


LO 4021 0.032 _±_ 0.028 _<_ 24


LO 4111 -0.012 _±_ 0.028 _<_ 24


LO 4126 0.004 _±_ 0.028 _<_ 23


LO 4155 0.927 _±_ 0.030 27 _±_ 8


LO 4163 0.481 _±_ 0.028 _<_ 24


LO 4187 1.846 _±_ 0.037 113 _±_ 21


LO 4255 0.099 _±_ 0.028 _<_ 24


LO 4363 0.032 _±_ 0.028 _<_ 23


LO 4407 1.067 _±_ 0.037 29 _±_ 8


LO 4520 0.340 _±_ 0.028 _<_ 25


LO 4531 0.375 _±_ 0.028 _<_ 22


LO 4817 0.023 _±_ 0.028 _<_ 24


LO 4916 0.017 _±_ 0.028 _<_ 24


LO 5267 0.257 _±_ 0.028 _<_ 24


LO 5447 -0.002 _±_ 0.028 _<_ 23


LO 5679 0.054 _±_ 0.028 _<_ 24


LO 5916 0.011 _±_ 0.028 _<_ 23


LO 6191 0.009 _±_ 0.028 _<_ 24


LO 6866 0.623 _±_ 0.028 80 _±_ 14


LO 6886 0.006 _±_ 0.028 _<_ 23


LO 7402 0.017 _±_ 0.030 _<_ 23


LO 7490 0.030 _±_ 0.028 _<_ 25


LO 7528 0.031 _±_ 0.028 _<_ 25



The integrated [12] CO line fluxes ( _F_ 12CO ) are measured
using a curve-of-growth aperture photometry method,
with errors ( _E_ 12CO ) estimated by taking the standard
deviation of fluxes measured within the same-sized aperture placed randomly within the field of view but away
from the source.
Only five sources (HD 245185, LO 4155, LO 4187,
LO 4407, LO 6866) are detected with _F_ 12CO _≥_ 3 _×_
_E_ 12CO, though two of these (LO 4155, LO 4407) are
marginal (3–4 _σ_ ) detections. One other source, LO 1624,
shows emission at _∼_ 5 _×_ the rms in the single channel at
its known _v_ LSR, but is undetected in its zero-moment
map as summing over several channels dilutes the emission. For the non-detections, we construct zero-moment
maps by integrating _±_ 3 km s _[−]_ [1] from their known _v_ LSR
when available (Table 1), else from the average _v_ LSR of
the cluster (12 km s _[−]_ [1] ; Kounkel et al. 2018). Table 2
gives the _F_ 12CO values for the detections and upper limits of 3 _×_ the rms in the zero-moment maps for the nondetections. Figure 3 shows the zero-moment and firstmoment maps for the five detections, while Appendix B
presents the [12] CO spectra for all sources in our sample.
Figure 4 then shows ALMA Band 6 [12] CO emission as
a function of the Band 6 continuum for the continuumdetected disks in the evolved _λ_ Orionis cluster (this
work), the young Lupus clouds (Ansdell et al. 2018),
and the middle-aged _σ_ Orionis cluster (Ansdell et al.
2017; Ansdell et al., in prep), all scaled to 150 pc. We
do not show other notable ALMA disk surveys, as they
were conducted in Band 7 (e.g., Barenfeld et al. 2016;
Pascucci et al. 2016) or do not have published Band 6
12 CO fluxes (e.g., Cieza et al. 2019). Interestingly, the
roughly linear correlation between continuum and [12] CO
flux holds over the first _∼_ 5 Myr of disk evolution, implying that the lack of gas detections in our _λ_ Orionis
survey can be explained by the low continuum emission.
This roughly linear correlation between the (somewhat) optically thin millimeter continuum flux and the
optically thick [12] CO flux is potentially due to more massive dust disks having more extended gas disks (e.g.,
Barenfeld et al. 2016). Moreover, since there is an observed linear relationship between the millimeter continuum luminosity ( _L_ mm ) and emitting surface area ( _R_ mm [2] [)]
of protoplanetary disks (Tripathi et al. 2017; Andrews
et al. 2018a), and Figure 4 implies that the [12] CO luminosity ( _L_ CO ) is proportional to _L_ mm, while we also
expect _L_ CO to be proportional to the [12] CO emitting
surface area ( _R_ CO [2] [) if it is optically thick, we can predict]
that _R_ CO _∝_ _R_ mm, which is indeed seen in observations
(Ansdell et al. 2018; Trapman et al. 2020).

ALMA Survey of _λ_ Orionis Disks 9



1.25 mm 12 CO (0th) 12 CO (1st)

15.0


14.0


13.0


12.0


11.0


11.0


10.0


9.0


8.0


13.0


12.0


11.0


10.0


9.0


11.4


11.0


10.6


14.5


14.0


13.5


13.0


**Figure** **3.** Our ALMA Band 6 observations of the five [12] CO
detections in our sample (Section 4.3). The first column
shows the 1.25 mm continuum maps with 4 _σ_, 20 _σ_, and 150 _σ_
contours. The middle column shows the [12] CO zero-moment

maps, scaled to their maximum value and clipped below 2 _σ_
for clarity. The final column shows the [12] CO first-moment
maps within the 3 _σ_ contours of the zero-moment maps. Images are 2 _[′′]_ _×_ 2 _[′′]_ and the typical beam size is given in the first
panel by the dashed ellipse.


5. DISK PROPERTIES


5.1. _Dust_ _Masses_


Under the simplified assumption that dust emission
from a protoplanetary disk at millimeter wavelengths is
optically thin and isothermal, the observed continuum
flux density at a given frequency ( _F_ _ν_ ) can be directly
related to the mass of the emitting dust ( _M_ dust ), as established in Hildebrand (1983):



10




|L|upus(2Myr)<br>Orionis(3Myr)<br>Orionis(5Myr)|Col3|
|---|---|---|
||||
||||
||||



_F_ _ν_ _d_ [2]
_M_ dust = (1)

_κ_ _ν_ _B_ _ν_ ( _T_ dust ) _[≈]_ [4] _[.]_ [1] _[ ×][ F]_ [1] _[.]_ [25mm] _[,]_



1


0.1


0.1 1 10 100


ALMA Band 6 Continuum Flux (mJy)


**Figure** **4.** 12 CO flux as a function of continuum flux in
ALMA Band 6 for the continuum-detected disks in Lupus
(Ansdell et al. 2018), _σ_ Orionis (Ansdell et al. 2017, Ansdell
et al., in prep), and _λ_ Orionis (this work). Fluxes are normalized to 150 pc and downward-facing triangles are 3 _σ_ upper
limits on [12] CO flux. Approximate ages of each region are
provided for reference. The four _λ_ Orionis [12] CO detections
follow the roughly linear correlation seen in younger regions,
and the lingering bright disk in _λ_ Orionis is HD 245185.


for Taurus disks (Andrews & Williams 2005). We take
the dust grain opacity, _κ_ _ν_, as 2.3 cm [2] g _[−]_ [1] at 230 GHz
and use an opacity power-law index of _β_ d = 1 _._ 0 (Beckwith et al. 1990); these are the same assumptions as in
Ansdell et al. (2016, 2017, 2018) and Cieza et al. (2019)
but differ slightly from some previous ALMA disk surveys (Pascucci et al. 2016; Barenfeld et al. 2016), which
use _β_ = 0 _._ 4. For the distance, _d_, we use the cluster’s average _Gaia_ DR2 value of 400 pc (Section 3.2), and take
the _F_ 1 _._ 25mm measurements from Table 2.
With this approach, the median _M_ dust of the continuum detections in our _λ_ Orionis survey is only _∼_ 2 _M_ _⊕_ .
These dust masses may be underestimated, however,
if the observed millimeter continuum emission is (partially) optically thick (e.g., Andrews & Williams 2005;
Zhu et al. 2019) and/or if the temperature of the dust in
the outer disk (where we assume most of the disk mass
is located) is lower than 20 K. Nevertheless, employing
this simplified relation with these caveats in mind provides the most practical approach given the faint and
unresolved emission from the disks in our observations.

Figure 5 shows the _M_ dust estimates for the continuum
detections in our survey in increasing order. It also includes the median 3 _σ_ upper limit of _∼_ 0.4 _M_ _⊕_ for the
individual non-detections in our survey, as well as the
mean detection of _∼_ 0.08 _M_ _⊕_ found when stacking these
non-detections (Section 4.2).



where _M_ dust is in Earth masses and _F_ 1 _._ 25mm is in mJy.
Here we use _B_ _ν_ ( _T_ dust ) as the Planck function for a characteristic dust temperature of _T_ dust = 20 K, the median

10 Ansdell et al.


100


10


1


0.1





|Col1|Col2|Col3|Col4|Col5|Col6|
|---|---|---|---|---|---|
|||||||
||||||OMC-2 (1 Myr)<br>Lupus (2 Myr)<br> Orionis (3 Myr)<br>|
||||||Upper Sco (5 Myr)<br> Orionis (5 Myr)|
|||||||


**Figure** **5.** Dust masses of the 14 continuum-detected disks in our _λ_ Orionis survey (white circles) in increasing order (source
names are given on the _x_ axis). The white downward triangle is the median 3 _σ_ upper limit for individual non-detections (ND),
while the white star shows their detected average dust mass from our stacking analysis (Section 5.1). Comparable disk dust
mass populations (see Section 5.2) from OMC-2 (purple crosses), Lupus (blue diamonds), _σ_ Orionis (orange x’s), and Upper
Sco (green squares) are also shown, illustrating the smooth distribution in the younger regions in contrast with the steep rise
toward the high-mass outlier disks in the older populations (see Sections 5.2 and 6.3). The colored solid lines are polynomial
fits to guide the eye for each region; approximate ages of each region are also provided for reference.



5.2. _Comparisons_ _to_ _Other_ _Regions_


At _∼_ 5 Myr old, _λ_ Orionis provides an important point
of comparison to the several younger disk populations,
as well as the similarly aged Upper Sco disk population,
that have been previously surveyed by ALMA. Figure 6
compares the _M_ dust cumulative distribution for _λ_ Orionis (this work) to that of OMC-2 (van Terwisga et al.
2019a), Lupus (Ansdell et al. 2018), _σ_ Orionis (Ansdell et al. 2017), and Upper Sco (Barenfeld et al. 2016).
The _M_ dust values are uniformly calculated using Equation 1 with the reported wavelengths of the surveys and
typical _Gaia_ DR2 distances of _∼_ 150 pc for Lupus and
Upper Sco and _∼_ 400 pc for _σ_ Orionis and OMC-2. For
the approximate ages of the regions, we adopt the values
used in the ALMA surveys or reported in more recent
analyses of the protoplanetary disk populations (e.g.,
Andrews 2020). The cumulative distributions are constructed using the Kaplan-Meier Estimator (with the
Python `lifelines` package; Davidson-Pilon et al. 2020)
to account for upper limits, as in previous works (e.g.,
Barenfeld et al. 2016; Ansdell et al. 2017; Cieza et al.
2019; van Terwisga et al. 2019b; Cazzoletti et al. 2019).



Figure 6 illustrates that _λ_ Orionis follows the general
decay in the overall disk dust mass population with age
that has been previously reported (e.g., Ansdell et al.
2016; Barenfeld et al. 2016; Pascucci et al. 2016; Cieza
et al. 2019; van Terwisga et al. 2019b). Moreover, the
_M_ dust distribution in _λ_ Orionis is statistically indistinguishable from that of the similarly aged Upper Sco association. Both of these findings suggest that, if a supernova did occur relatively recently in _λ_ Orionis, it did not
have a significant impact on disk dust mass evolution in
the region. We discuss this further in Section 6.1.
A reliable comparison of the _M_ dust distributions in
Figure 6 requires confirming that the regions have similar _M_ _⋆_ populations, due to the known correlation between disk dust mass and stellar mass (e.g., Andrews
et al. 2013; Ansdell et al. 2016; Barenfeld et al. 2016;
Pascucci et al. 2016). Two-sample tests have previously
demonstrated that the stellar mass populations in Lupus, _σ_ Orionis, and Upper Sco are likely drawn from the
same parent population (Barenfeld et al. 2016; Ansdell
et al. 2016, 2017). To confirm that the _M_ dust populations in _λ_ Orionis and Upper Sco are indeed statistically
indistinguishable, we again use two-sample tests to com

ALMA Survey of _λ_ Orionis Disks 11



1.0


0.8


0.6


0.4


0.2







0.1 1 10 100

M dust [M ]


**Figure** **6.** The disk dust mass ( _M_ dust ) cumulative distribution for _λ_ Orionis compared to several other regions surveyed
by ALMA, calculated with the Kaplan-Meier Estimator to
account for upper limits (see Section 5.2). Approximate ages
for each region are provided for reference.



pare their stellar mass populations. Using the _M_ _⋆_ values from Table 1 for _λ_ Orionis and those from Barenfeld
et al. (2016) for Upper Sco, we find _p_ -values of 0.77 and
0.11 for the T-test and Wilcoxon rank-sum test, respectively (calculated with `scipy.stats` in Python). Thus
the _M_ _⋆_ populations are likely drawn from the same parent population and so the _M_ dust distributions can be
reliably compared.
Figure 5 also illustrates the decline in _M_ dust distributions with age, but highlights differences at the highmass end, which are not readily apparent from the cumulative distributions in Figure 6. In Figure 5, the
_λ_ Orionis detections are plotted against the upper 32%
of the _M_ dust populations in the comparison regions (32%
was chosen to match the detection rate in _λ_ Orionis).
Interestingly, the highest-mass disks in all the regions
appear to converge around _∼_ 100 M _⊕_ regardless of age
or environment. Although the number of disks at such
high masses falls steeply after a few Myr, one or more
“outlier” disks appear to persist even at _∼_ 5 Myr of age.
We discuss these lingering massive disks in Section 6.3.
One caveat is that the ages assumed in this work are
just the typical median values of the regions reported in
the literature. They do not reflect the possibility of distributed age populations, and have been calculated using different methods, any of which are likely imprecise
and/or inaccurate due to biases in both the observations
and the stellar evolution models (e.g., Bell et al. 2013).
However, the relative ages should be generally reliable
and sufficient for the purposes of this work.



5.3. _HD_ _245185_


HD 245185 hosts a clear outlier disk in _λ_ Orionis, having over an order of magnitude higher millimeter continuum and [12] CO flux than the rest of the sample (Figure 4). HD 245185 is a well-studied Herbig Ae/Be star in
the literature and is the only early-type (A0) star in our
sample (Table 1) with a mass of _∼_ 2.5 _M_ _⊙_ (e.g., Folsom
et al. 2012). Figure 3 shows the 1.25 mm continuum map
and the [12] CO zero-moment and first-moment maps from
our ALMA observations. We note that the proper motions ( _µ_ _α_ = 0 _._ 34, _µ_ _δ_ = _−_ 1 _._ 93) and distance (427 _−_ [+21] 19 [pc)]
from _Gaia_ DR2, as well as the systemic velocity derived
from our ALMA [12] CO observations ( _v_ LSR _≈_ 13 km s _[−]_ [1] ),
are all consistent with cluster membership.
Equation 1 yields _M_ dust _≈_ 140 _M_ _⊕_, an order of magnitude higher than the next most massive disk in _λ_ Orionis
(Figure 5). One concern is that this is due to HD 245185
being the only hot star in our sample, given that the simplified relation in Equation 1 assumes _T_ dust = 20 K for
all disks. However, only some of the difference (a factor
of _∼_ 3) may be accounted for if, rather than assuming
an isothermal disk, we scale the dust temperature with
stellar luminosity using _T_ dust = 25 K _×_ ( _L_ _⋆_ _/L_ _⊙_ ) [0] _[.]_ [25] as
suggested by the radiative transfer model grid of Andrews et al. (2013). We do not use this scaling, however,
as it remains uncertain whether such a clear relationship
holds in the real disk population. For example, Tazzari
et al. (2017) found no relation between _T_ dust and stellar properties when modeling the ALMA visibilities of
resolved Lupus disks.
Another reason why a massive disk around HD 245185
is unusual at the evolved age of _λ_ Orionis is that disks
around intermediate-mass stars typically dissipate twice
as fast as those around late-type stars (at least based
on infrared emission, which traces the warm inner disk;
e.g., Ribas et al. 2015). It is unlikely that HD 245185 is
much younger than the average disk in the cluster: several authors have estimated the age of HD 245185, e.g.,
6 _._ 9 _±_ 2 _._ 5 Myr (Alecian et al. 2013) and 5 _._ 5 _±_ 2 _._ 0 Myr
(Folsom et al. 2012), suggesting we cannot use delayed
star formation relative to the rest of _λ_ Orionis to rec
oncile this system. We discuss possible explanations for
such long-lived primordial disks in Section 6.3.


6. DISCUSSION


6.1. _Do_ _Supernovae_ _Impact_ _Planet_ _Formation?_


_λ_ Orionis may provide a rare snapshot of an evolved
SFR that is _∼_ 1 Myr post-supernova with the remaining
OB stars, lower-mass stellar population, and remnant
molecular cloud all still present (Section 2). Comparing
the disk population in _λ_ Orionis to those in other SFRs

12 Ansdell et al.



may therefore provide an opportunity to study how supernovae affect planet formation.
Supernovae are theorized to strip significant amounts
of mass from disks around nearby pre-main sequence
stars. Close & Pittard (2017) ran three-dimensional hydrodynamic simulations of protoplanetary disks, with a
range of masses and inclinations, subject to a supernova occurring 0.3 pc away. They reported an “instantaneous stripping” phase with mass-loss rates of
10 _[−]_ [5] _M_ _⊙_ yr _[−]_ [1] lasting 10–100 years, followed by more
moderate but extended ablation with mass-loss rates of
10 _[−]_ [6] to 10 _[−]_ [7] _M_ _⊙_ yr _[−]_ [1] . For the low-mass (0.1 _M_ Jup )
and moderate-mass (1.0 _M_ Jup ) disks in their simulations, up to 90% and 30% of the disk mass, respectively, was removed during the instantaneous stripping
phase; these disk masses are typical in _σ_ Orionis, a possible example of a pre-supernova OB cluster. High-mass
(10 _M_ Jup ) disks, however—similar to the outlier around
HD 245185 in _λ_ Orionis (Section 5.3)—were largely unaffected. Since the peak ram pressure in the simulations
of Close & Pittard (2017) strongly depends on distance
from the supernova (dropping off as _d_ _[−]_ [3] ), we would expect most disks within 0.3 pc to be significantly depleted
in mass, with those further out relatively unaffected.
Indeed, as shown in Figure 7, we observe but do not
detect four disks with projected separations _<_ 0 _._ 3 pc
from the cluster core, the presumed supernova location (Section 2). Several disks are detected just beyond
0.3 pc, but have disk masses similar to the rest of the
population. Due to the natural course of cluster expansion, these projected distances are likely overestimates of
the source locations when the supernova occurred. Still,
our finding that the overall disk population in _λ_ Orionis
appears to follow the general decline in disk dust mass
with age seen in other SFRs, and is statistically indistinguishable from that of the similarly aged Upper Sco
association (Figure 6; Section 5.2), implies that a supernova occurring several Myr into disk evolution does
not significantly reduce the amount of planet-forming
solid material that would otherwise be available at this

age, except potentially for disks that were within a small
fraction of a parsec from the supernova event.
Additionally, pre-supernova feedback may mute the
effects of the actual supernova event on the surrounding
environment. Recent simulations that combine stellar
winds and photoionization with supernova events (Lucas
et al. 2020) found that pre-supernova feedback sculpts
low-density channels in the gas, through which supernova energy can more freely escape into the wider interstellar medium. As a result, supernova explosions may
have only moderate, though more widespread, effects
on the surrounding natal molecular clouds and their



100


10


1


0.1


0.1 1 10

Projected Separation from Ori [pc]


**Figure** **7.** Disk mass ( _M_ disk ), assuming a gas-to-dust ratio
of 100, as a function of projected separation from the central
OB star ( _λ_ Ori) in _λ_ Orionis. Circles are ALMA Band 6
continuum detections and downward-facing triangles are 3 _σ_
upper limits; stars indicate [12] CO detections. The vertical
dotted line denotes the 0.3 pc distance of the supernova in
the simulations of Close & Pittard (2017) (see Section 6.1).


star/disk populations. When occurring late in disk evolution, it is possible that these moderate effects from supernovae are simply negligible when compared to other
disk evolutionary processes.
One caveat to this interpretation, however, is that
we cannot rule out that a supernova also occurred in
the SFRs against which we are comparing the _λ_ Orionis disk population. In particular, a supernova may
have also occurred _∼_ 1 Myr ago in Upper Sco; this is
based on the kinematics of an expanding HI shell in the
region (de Geus 1992) as well as the kinematic traceback of the runaway O-type star _ζ_ Oph and pulsar
PSR 1932+11059, which may have once been close binaries in Upper Sco before the pulsar progenitor exploded
as a supernova (Hoogerwerf et al. 2000, 2001). However,
the large uncertainties on the present-day kinematics of
the runaway objects, including an unknown radial velocity for the pulsar, make the location of the presumed
supernova, and thus its potential impact on the Upper
Sco disk population, unclear.
Another caveat is that our ALMA sample is selected
from targeted _Spitzer_ observations (Section 3), thus only
includes disks that are currently within _∼_ 3 pc of the
cluster core (see white dashed box in Figure 1). Because the recently identified _λ_ Orionis members outside
the _Spitzer_ survey region are radially expanding outward
(Figure 1; Kounkel et al. 2018), the concern is that our
ALMA survey missed some disks that were once much
closer to the cluster core and thus potentially most affected by the supernova. However, the faster-moving

ALMA Survey of _λ_ Orionis Disks 13



stars in this radially expanding population only have
typical proper motions of _∼_ 1 mas yr _[−]_ [1] (relative to the
cluster median), which translates to _∼_ 2 pc over 1 Myr
at 400 pc. Because these stars also have typical projected separations of ≳10 pc from the cluster core, it is
unlikely that they were particularly close to the supernova when it occurred, especially if the outward acceleration was aided by gravitational feedback of the dispersed gas (Zamora-Avil´es et al. 2019). Moreover, although Kounkel et al. (2018) explain the observed radial
motions as due to the “single-trigger expansion” caused
by the supernova, alternative explanations staged presupernova are also viable: such kinematics can be a consequence of any mechanism that disperses the intracluster gas (e.g., stellar winds or radiation; see Winter et al.
2019), and pre-supernova feedback may preclude the actual supernova event as the main mechanism driving the
removal of the gas potential (e.g., Lucas et al. 2020).
Indeed, an alternative explanation is that a supernova has not yet actually occurred in _λ_ Orionis, and
that the observed features described in Section 2 originate from other aspects of the cluster history, such as
pre-supernova feedback. In fact, the expected chemical
effects from a supernova are not readily apparent in our
current ALMA data. Supernovae are production sites
of cosmic rays (see review in Grenier et al. 2015), thus
the cosmic ray ionization rate of H 2 ( _ζ_ CR ) should be enhanced in _λ_ Orionis. Typical ionization rates in molecular clouds are _ζ_ CR _∼_ 10 _[−]_ [17] s _[−]_ [1] and may be even lower
in disk midplanes (Cleeves et al. 2014), however after a
supernova the levels can be enhanced to _ζ_ CR _∼_ 10 _[−]_ [15] or
10 _[−]_ [14] s _[−]_ [1] (e.g., Indriolo et al. 2010; Le Petit et al. 2016).
At these levels, the transformation of CO into methanol
and hydrocarbons proceeds much faster in the ice and
gas, on scales of _<_ 1 Myr rather than 5–10 Myr (Bosman
et al. 2018; Schwarz et al. 2018b). Yet we still detect CO
in some _λ_ Orionis disks, and at levels expected from their
millimeter continuum emission (Figure 4). However, the
sample size of gas detections is small; deeper observations and additional molecular lines will help determine
if our current CO non-detections are due to dispersal of
the gas or chemical transformation of the CO.
Nevertheless, the massive stars in _λ_ Orionis, through
pre-supernova feedback and/or a recent supernova event
itself, appear to have sculpted many of the observational
features of the region, yet have not significantly reduced
the available planet-forming material in the overall disk
population beyond what is expected at this evolved age.


6.2. _External_ _Photoevaporation_ _in_ _λ_ _Orionis_


OB stars can also impact the disk population through
external photoevaporation (e.g., Johnstone et al. 1998;



St¨orzer & Hollenbach 1999), a process that is now
thought to be one of the main environmental factors depleting disk material (e.g., Scally & Clarke 2001; Sellek
et al. 2020), even in typical galactic UV environments
(e.g., Facchini et al. 2016; Haworth et al. 2016; Winter et al. 2018). While direct detection of externally
driven photoevaporative winds is observationally challenging (Henney & O’Dell 1999; Rigliaco et al. 2009;
Haworth & Owen 2020), indirect evidence based on the
expected impacts on more easily observable disk properties is growing (e.g., Fang et al. 2012; Mann et al. 2014;
Kim et al. 2016; Guarcello et al. 2016; Haworth et al.
2017; van Terwisga et al. 2019b). In particular, using
ALMA to estimate disk masses, Ansdell et al. (2017)
found in _σ_ Orionis a dearth of massive (≳ 1 _M_ Jup ) disks
within _∼_ 0.5 pc of the central OB stars, followed by a
clear distant-dependent trend in disk mass out to the
cluster edge (see their Figure 6).
Although we do not see a similar distance-dependent
trend for the disk masses in _λ_ Orionis, there is a lack
of even low-mass (≳0.1 _M_ Jup ) disks within _∼_ 0.3 pc of
the central OB stars (Figure 7) that could be a tentative signature of external photoevaporation (and/or
ablation from the supernova; see Section 6.1). The
lack of a distance-dependent trend in disk mass beyond
0.3 pc may be explained by the older age of the cluster,
which has allowed for both more cluster expansion as
well as dust grain growth. In this scenario, the sources
in our sample were likely closer to the OB stars in the
past, experiencing more effective external photoevaporation that removed gas and any entrained small dust
grains in the outer disk. As the cluster dispersed with
age, the remaining dust grains in the disks would have
grown beyond 10–100 _µ_ m, at which point they are too
large to be affected by external photoevaporation and
instead experience rapid inward radial drift (Haworth
et al. 2018; Sellek et al. 2020). Thus any detectable
distance-dependent trend in disk mass may have been
washed out due to the dynamical evolution of the cluster and the evolution of the disk dust population probed
by ALMA for a couple Myr beyond the age of _σ_ Orionis.


6.3. _Outlier_ _Disks_ _in_ _Evolved_ _Regions_


The handful of relatively nearby SFRs (at ≲400 pc;
the distance of Orion or closer) with evolved ages ( _∼_ 5–
10 Myr old; the end of the disk lifetime) includes _λ_ Orionis, Upper Sco, and the TW Hya Association (TWA).
Each of these evolved regions contains at least one longlived primordial disk that remains much more massive
than the rest of the surviving disk population. Younger
regions, in contrast, exhibit a smooth distribution in
disk masses, regardless of whether they are in low-mass

14 Ansdell et al.



(e.g., Lupus) or high-mass (e.g., OMC-2) SFRs. This is
illustrated in Figure 5, which shows the upper 32% of the
disk dust mass distributions in different SFRs (32% was
chosen to match the detection rate in our _λ_ Orionis survey). In Figure 5, all of the SFRs exhibit similar slopes
until the highest-mass disks, at which point the distributions of the evolved Upper Sco and _λ_ Orionis regions rise
steeply due to their outlier disks (we do not show TWA
in Figure 5, as ALMA surveys of its disk population are
not yet published). Additionally, the most massive disks
in each SFR, regardless of age or environment, all have
_M_ dust _∼_ 100 _M_ _⊕_, which suggests that the outlier disks
in the evolved regions were _not_ distinct from birth, but
rather that some mechanism stopped the otherwise natural removal of disk material (e.g., by accretion onto the
star and/or winds) as the disks evolved.
A potential explanation is that one or more
(sub-)stellar companions formed in these disks, on orbits
that are inhibiting the dispersal of outer disk material
while also avoiding disk truncation/disruption, resulting in particularly long-lived primordial disks. A single,
massive super-Jupiter on an initially circular orbit may
excite its own eccentricity (e.g., D’Angelo et al. 2006),
enabling the clearing of a large inner cavity while preserving the outer disk; this has been demonstrated for
the _∼_ 5 Myr old PDS 70 system (Muley et al. 2019),
which hosts a super-Jupiter planet at 22 au, and could
potentially explain many other transition disks (van der
Marel et al. 2018; van der Marel et al., subm.). Chains of
gas giants (e.g., Zhu et al. 2011) and potentially superEarths (Fung & Chiang 2017; Rosenthal et al. 2020) may
also open inner disk cavities or large gaps. Although sufficiently inhibiting the accretion of gas-rich disk material
(onto either the star or planets) to prolong disk lifetimes remains a challenge in these scenarios, dust evolution models show that giant planets drive strong pressure bumps that effectively prevent millimeter dust from
drifting inward; these particle traps then result in prolonged lifetimes for the millimeter dust disks observed by
ALMA, especially for higher-mass disks around highermass stars (e.g., Pinilla et al. 2020). Stellar binaries can
exert torques on disks that similarly open central cavities, while also effectively inhibiting accretion of material onto the binary. Alexander (2012) showed that binaries on sufficiently close (≲1 au) orbits form cavities
smaller than the critical radius beyond which photoevaporative winds are efficient, resulting in circumbinary
disk lifetimes that are several times longer than those
of single-star disks. With these constraints in mind, we
discuss below how the outlier disks in _λ_ Orionis, Upper
Sco, and TWA show evidence of such companions that
could explain their extended primordial disk lifetimes.



For HD 245185 in _λ_ Orionis, Kama et al. (2015) placed
it in the population of Herbig Ae/Be stars whose stellar abundances are depleted in refractory elements while
hosting warm/flared transition disks, as opposed to the
population with solar abundances hosting cold/flat full
disks. They explained the chemical peculiarity of the
former population with giant planets filtering out dusty
material as it flows through the disk, resulting in the accretion of high gas-to-dust ratio material onto the star.
These massive planets would then also be responsible
for clearing out the large gap or cavity in the disk dust
structure that defines the transition disk classification
(Espaillat et al. 2014). Although our ALMA observations do not resolve any gaps or cavities in the disk
around HD 245185 (Figure 3), the resolution is poor
( _∼_ 60 au in radius). As the SED of HD 245185 exhibits
a mid-infrared dip (Ansdell et al. 2015), future ALMA
observations may still resolve structure in the disk.
For Upper Sco, one of the most massive disks is
around 2MASS J16042165-2130284 (also known simply
as J1604), a negligible accretor (Manara et al. 2020) of
K2 spectral type that hosts a face-on transition disk with
a large inner cavity seen in millimeter emission (Mathews et al. 2012; Ansdell et al. 2020). Evidence points
to one or more high-mass planetary companions clearing out the cavity as well as misaligning an unseen inner
disk component that casts variable shadows on the outer
disk detected in scattered light (e.g., Takami et al. 2014;
Pinilla et al. 2018). This misaligned inner disk is also
thought to cause the “dipper” variability observed in
space-based light curves (e.g., Cody & Hillenbrand 2018;
Ansdell et al. 2020). Another outlier disk in Upper Sco
is around the G-type star 2MASS J15583692-2257153
(or HD 143006), which also hosts a face-on transition
disk exhibiting “dipper” variability (Ansdell et al. 2020).
This disk has a large gap, several narrow rings/gaps,
and a bright asymmetry resolved by ALMA (Andrews
et al. 2018b) suggesting a warped inner disk driven by a
low-mass stellar or high-mass planetary companion, potentially orbiting at a few au (P´erez et al. 2018). Finally,
the most massive disk in Upper Sco is around 2MASS
J16113134-1838259 (or AS 205); this is not a transition
disk, but displays clear spirals arms detected by ALMA,
indicative of strong dynamical interactions induced by
a known external companion (Kurtovic et al. 2018) that
may be dominating its disk structure and evolution.
The outlier disk in TWA is around TW Hya itself.
It also has an inner disk warp, this time detected in the
gas kinematics (Rosenfeld et al. 2012), which could originate from a massive planetary companion orbiting this
K-type star (e.g., Facchini et al. 2014). Extremely highresolution ALMA observations have detected a gap at

ALMA Survey of _λ_ Orionis Disks 15



just 1 au, providing further evidence for interactions between the disk and a young planet (Andrews et al. 2016).
Moreover, scattered light images taken over nearly two
decades show that an azimuthal asymmetry in the outer
disk changes in position angle in a manner consistent
with shadowing by a precessing warped inner disk due
to perturbations by a roughly Jupiter-mass companion
orbiting at 1 au (Debes et al. 2017).
If some or all of these outlier disks are indeed due to

sub-stellar companions, they suggest that planet formation, given certain orbital parameters and mass ranges,
can change the course of disk evolution to extend the
lifetimes of primordial outer disks. More detailed analysis of these and other outlier disks—such as those
in the older Upper Cen and Lower Cen regions (e.g.,
HD 142527, HD 135344B, HD 100453, HD 100546)—
could therefore provide insight into the timing and nature of planet formation. For now, we can only make
some initial speculations. Early giant planet formation (occurring at ≲1 Myr) could help explain the outlier disks as well as the apparent discrepancy between
the amount of mass in protoplanetary disks compared
to mature exoplanet systems (Greaves & Rice 2010;
Williams 2012; Najita & Kenyon 2014; Manara et al.
2018a). We note that observing one or two outlier disks
within a given SFR, which typically hosts _∼_ 50–100 protoplanetary disks, is broadly consistent with the low
occurrence rate of giant planets (e.g., Cumming et al.
2008; Bowler 2016; Nielsen et al. 2019), given that particularly massive or multiple gas giants and/or certain
orbital parameters are likely required to create outlier
disks. If the outlier disks are instead associated with

the much more common compact multi-planet systems
(e.g., Winn & Fabrycky 2015), this could suggest that
such systems usually form in the outer disk and migrate
inward, during which they disperse the outer disk; only
in rarer cases do they form _in_ _situ_, preserving the outer
regions and resulting in an outlier disk.


7. SUMMARY


We present an ALMA Band 6 survey of the protoplanetary disk population in the _λ_ Orionis OB cluster.
This region is important for studying disk evolution and
planet formation due to its evolved age and the recent
supernova that may have occurred in its core. Our key
findings are as follows:


_•_ The millimeter emission from _λ_ Orionis disks is

weak, but not particularly unusual given the cluster’s evolved age of _∼_ 5 Myr. Only 14 of the 44
disks in our sample are detected in our observations of the 1.25 mm continuum (Figure 2), which
has a 34 _µ_ Jy median rms corresponding to 3 _σ_ dust



mass upper limits of _∼_ 0.4 _M_ _⊕_ . Stacking the 30
non-detections gives a 4 _σ_ mean signal of 20 _µ_ Jy
( _∼_ 0.08 _M_ _⊕_ ), indicating that deeper observations
should produce more detections. Only 5 disks are
also detected in the [12] CO line (Figure 3); however, the lack of gas detections is consistent with
the weak continuum emission, based on the correlation between millimeter continuum and [12] CO
emission seen in younger regions (Figure 4).


_•_ The effects of massive stars, in the form of presupernova feedback and/or a supernova event itself, do not appear to significantly reduce the overall planet-forming capacity of a population of protoplanetary disks that is already a few Myr into
evolution. This is based on comparing the disk
mass distribution in _λ_ Orionis to that of other

SFRs, in particular the similarly aged Upper Sco
association (Figures 5 and 6). One explanation
is that supernovae are only effective at stripping
mass from nearby disks that are within a small
fraction of a parsec. Additionally, pre-supernova
feedback may sculpt low-density channels in the
intercluster gas, through which energy can more
easily escape, significantly muting the impact of
supernovae events on the surrounding disk population. However, more work is needed to confirm
the occurrence of the supernova event in _λ_ Orionis
and/or determine whether a recent supernova also
occurred in Upper Sco.


_•_ Massive “outlier” disks lingering in evolved ( _∼_ 5–
10 Myr) regions like _λ_ Orionis, Upper Sco, and
TWA show evidence for one or more (sub-)stellar
companions. Because these massive disks would
not be considered outliers in younger ( _∼_ 1–2 Myr)
regions (Figure 5), their existence suggests that
companion formation, including planet formation
within certain orbital and mass constraints, can
change the course of disk evolution to extend the
lifetimes of primordial outer disks. Further study
of outlier disks as a population may therefore provide needed insight into the nature and timing of
certain types of planet formation.


Many avenues for future work exist. Deeper ALMA
observations of the disk population in _λ_ Orionis will
build up larger numbers of continuum and line detections to improve our constraints on population-level
statistics. Understanding the disk population of the
cluster members outside of the _Spitzer_ survey area will
also ensure that the ALMA survey is complete. Obtaining better constraints on the stellar and accretion

16 Ansdell et al.


properties of the disk-hosting stars in _λ_ Orionis with
wide-band and/or high-resolution spectra will allow us
to search for trends seen in other regions, as well as
any evidence for external photoevapoaration and viscous
evolution. Deeper observations with ALMA of multiple
molecular lines tracing the gas content and chemistry
will help determine whether our observations reflect disk
gas dispersal or the transformation of CO due to enhanced cosmic ray ionization from the supernova. Detailed theoretical studies may also provide insight into
the peculiar kinematics of _λ_ Orionis and its links to the
star-formation history of the region; similar studies in
Upper Sco are also important, in particular to assess the
possibility of a recent supernova having also occurred in
that region. Indeed, _λ_ Orionis still has much to teach us
about perhaps one of the most common types of planetforming environments in the nearby Galaxy.


ACKNOWLEDGMENTS


MA and EC acknowledge support from NASA grant
NNH18ZDA001N/EW. TJH is funded by a Royal Society Dorothy Hodgkin Fellowship. This project has
received funding from the European Union’s Horizon
2020 research and innovation programme under the
Marie Sklodowska-Curie grant agreement No 823823
(DUSTBUSTERS). This work was partly supported
by the Deutsche Forschungs-Gemeinschaft (DFG, German Research Foundation) - Ref no. FOR 2634/1
TE 1024/1-1. This work makes use of the following
ALMA data: ADS/JAO.ALMA#2017.1.00466.S and
#2016.1.00447.S. ALMA is a partnership of ESO (representing its member states), NSF (USA) and NINS
(Japan), together with NRC (Canada), MOST and
ASIAA (Taiwan), and KASI (Republic of Korea), in
cooperation with the Republic of Chile. The Joint
ALMA Observatory is operated by ESO, AUI/NRAO
and NAOJ. This work made use of data from the European Space Agency (ESA) mission Gaia [(https://www.](https://www.cosmos.esa.int/gaia)
[cosmos.esa.int/gaia),](https://www.cosmos.esa.int/gaia) processed by the Gaia Data Pro[cessing and Analysis Consortium (DPAC, https://www.](https://www.cosmos.esa.int/web/gaia/dpac/consortium)
[cosmos.esa.int/web/gaia/dpac/consortium).](https://www.cosmos.esa.int/web/gaia/dpac/consortium) Funding
for the DPAC has been provided by national institutions, in particular the institutions participating in the
Gaia Multilateral Agreement.


_Facilities:_ ALMA, _Gaia_


_Software:_ `astropy` (Astropy Collaboration et al.
2013, 2018), `ASURV` (Lavalley et al. 1992), `CASA` (McMullin et al. 2007), `matplotlib` (Hunter 2007)

ALMA Survey of _λ_ Orionis Disks 17


APPENDIX


A. ALMA OBSERVING LOG


Table 3 summarizes the 13 execution blocks that collected the ALMA observations of our _λ_ Orionis disk sample
(Section 4.1). It provides the date and time of the observations in Coordinated Universal Time (UTC Date), number of
antennae used ( _N_ ant ) and their baseline range ( _L_ base ), precipitable water vapor (PWV) at the time of the observations,
and names of the bandpass, flux, and gain calibrators applied in the pipeline calibration.


**Table** **3.** ALMA Observing Log


UTC Date _N_ ant _L_ base PWV Calibrators


(End Time) (m) (mm) (Bandpass/Flux, Phase)


2018-09-09 44 15–1213 2.1 J0423 _−_ 0120,
(13:39:36) J0532+0732

2018-09-09 46 15–1213 1.7 J0510+1800,
(10:58:12) J0532+0732

2018-09-08 43 15–784 1.3 J0510+1800,
(13:09:24) J0532+0732

2018-09-01 45 15–784 1.7 J0510+1800,
(12:28:28) J0532+0732

2018-08-30 46 15–784 0.8 J0510+1800,
(12:15:34) J0532+0732

2018-01-24 44 15–1398 1.4 J0510+1800,
(04:01:52) J0532+0732

2018-01-23 43 15–1398 0.9 J0510+1800,
(03:33:37) J0532+0732

2018-01-22 44 15–1398 0.7 J0510+1800,
(04:09:53) J0532+0732

2018-01-22 44 15–1398 1.0 J0510+1800,
(03:00:38) J0532+0732

2018-01-21 44 15–1398 1.1 J0510+1800,
(04:12:04) J0532+0732

2018-01-21 44 15–1398 1.5 J0510+1800,
(03:03:10) J0532+0732

2018-01-19 45 15–1398 2.4 J0510+1800,
(03:44:18) J0532+0732

2018-01-18 44 15–1398 1.7 J0510+1800,
(03:59:12) J0532+0732

18 Ansdell et al.


B. ALMA [12] CO SPECTRA


Figure 8 presents the ALMA Band 6 [12] CO spectra for all 44 sources in our _λ_ Orionis disk sample. Extraction of the
spectra is described in Sections 4.3.



0 5 10 15 20 25



LO 1152



LO 1359













0 5 10 15 20 25


LO 2088



0 5 10 15 20 25


LO 7957









0 5 10 15 20 25


LO 3360



0 5 10 15 20 25


LO 3506











0 5 10 15 20 25


LO 3785



0 5 10 15 20 25


HD 245185







LO 65


0 5 10 15 20 25


LO 1624


0 5 10 15 20 25


LO 2989


0 5 10 15 20 25


LO 3746


0 5 10 15 20 25


LO 3942


0 5 10 15 20 25


LO 4163


0 5 10 15 20 25


LO 4520


0 5 10 15 20 25


LO 5447


0 5 10 15 20 25


LO 6886


0 5 10 15 20 25

Velocity (km/s)











0 5 10 15 20 25


LO 4111



0 5 10 15 20 25


LO 4126







0 5 10 15 20 25


LO 4255



0 5 10 15 20 25


LO 4363









0 5 10 15 20 25


LO 4817



0 5 10 15 20 25


LO 4916



LO 1589


0 5 10 15 20 25


LO 2712


0 5 10 15 20 25


LO 3597


0 5 10 15 20 25


LO 3887


0 5 10 15 20 25


LO 4155


0 5 10 15 20 25


LO 4407


0 5 10 15 20 25


LO 5267


0 5 10 15 20 25


LO 6866


0 5 10 15 20 25









0 5 10 15 20 25


LO 5916



0 5 10 15 20 25


LO 6191







0 5 10 15 20 25


LO 7490



0 5 10 15 20 25


LO 7528







LO 1079


0 5 10 15 20 25


LO 1840


0 5 10 15 20 25


LO 2993


0 5 10 15 20 25


LO 7951


0 5 10 15 20 25


LO 4021


0 5 10 15 20 25


LO 4187


0 5 10 15 20 25


LO 4531


0 5 10 15 20 25


LO 5679


0 5 10 15 20 25


LO 7402


0 5 10 15 20 25







0 5 10 15 20 25



**Figure** **8.** ALMA Band 6 [12] CO spectra for _λ_ Orionis disks. Horizontal dashed red lines indicate 3 _×_ the median channel
rms, while horizontal dotted black lines indicate the zero flux level. Vertical dashed lines are the source _v_ LSR, when available
(Table 1). Clear detections ( _>_ 4 _σ_ ) are highlighted in purple, while marginal detections ( _∼_ 3–4 _σ_ ) are indicated with orange.

ALMA Survey of _λ_ Orionis Disks 19


REFERENCES



Adams, F. C. 2010, ARA&A, 48, 47,

doi: [10.1146/annurev-astro-081309-130830](http://doi.org/10.1146/annurev-astro-081309-130830)

Alecian, E., Wade, G. A., Catala, C., et al. 2013, MNRAS,

429, 1027, doi: [10.1093/mnras/sts384](http://doi.org/10.1093/mnras/sts384)

Alexander, R. 2012, ApJL, 757, L29,

doi: [10.1088/2041-8205/757/2/L29](http://doi.org/10.1088/2041-8205/757/2/L29)
Andrews, S. M. 2015, PASP, 127, 961, doi: [10.1086/683178](http://doi.org/10.1086/683178)

—. 2020, arXiv e-prints, arXiv:2001.05007.


[https://arxiv.org/abs/2001.05007](https://arxiv.org/abs/2001.05007)

Andrews, S. M., Rosenfeld, K. A., Kraus, A. L., & Wilner,

D. J. 2013, ApJ, 771, 129,

doi: [10.1088/0004-637X/771/2/129](http://doi.org/10.1088/0004-637X/771/2/129)

Andrews, S. M., Terrell, M., Tripathi, A., et al. 2018a, ApJ,

865, 157, doi: [10.3847/1538-4357/aadd9f](http://doi.org/10.3847/1538-4357/aadd9f)

Andrews, S. M., & Williams, J. P. 2005, ApJ, 631, 1134,

doi: [10.1086/432712](http://doi.org/10.1086/432712)

Andrews, S. M., Wilner, D. J., Zhu, Z., et al. 2016, ApJL,

820, L40, doi: [10.3847/2041-8205/820/2/L40](http://doi.org/10.3847/2041-8205/820/2/L40)

Andrews, S. M., Huang, J., P´erez, L. M., et al. 2018b,
ApJL, 869, L41, doi: [10.3847/2041-8213/aaf741](http://doi.org/10.3847/2041-8213/aaf741)

Ansdell, M., Williams, J. P., & Cieza, L. A. 2015, ApJ, 806,

221, doi: [10.1088/0004-637X/806/2/221](http://doi.org/10.1088/0004-637X/806/2/221)

Ansdell, M., Williams, J. P., Manara, C. F., et al. 2017, AJ,

153, 240, doi: [10.3847/1538-3881/aa69c0](http://doi.org/10.3847/1538-3881/aa69c0)

Ansdell, M., Williams, J. P., van der Marel, N., et al. 2016,

ApJ, 828, 46, doi: [10.3847/0004-637X/828/1/46](http://doi.org/10.3847/0004-637X/828/1/46)

Ansdell, M., Williams, J. P., Trapman, L., et al. 2018, ApJ,

859, 21, doi: [10.3847/1538-4357/aab890](http://doi.org/10.3847/1538-4357/aab890)

Ansdell, M., Gaidos, E., Hedges, C., et al. 2020, MNRAS,
492, 572, doi: [10.1093/mnras/stz3361](http://doi.org/10.1093/mnras/stz3361)

Astropy Collaboration, Robitaille, T. P., Tollerud, E. J.,

et al. 2013, A&A, 558, A33,

doi: [10.1051/0004-6361/201322068](http://doi.org/10.1051/0004-6361/201322068)

Astropy Collaboration, Price-Whelan, A. M., Sip˝ocz, B. M.,
et al. 2018, AJ, 156, 123, doi: [10.3847/1538-3881/aabc4f](http://doi.org/10.3847/1538-3881/aabc4f)

Bailer-Jones, C. A. L., Rybizki, J., Fouesneau, M.,

Mantelet, G., & Andrae, R. 2018, AJ, 156, 58,

doi: [10.3847/1538-3881/aacb21](http://doi.org/10.3847/1538-3881/aacb21)

Baraffe, I., Homeier, D., Allard, F., & Chabrier, G. 2015,

A&A, 577, A42, doi: [10.1051/0004-6361/201425481](http://doi.org/10.1051/0004-6361/201425481)

Barenfeld, S. A., Carpenter, J. M., Ricci, L., & Isella, A.

2016, ApJ, 827, 142, doi: [10.3847/0004-637X/827/2/142](http://doi.org/10.3847/0004-637X/827/2/142)

Bayo, A., Barrado, D., Stauffer, J., et al. 2011, A&A, 536,
A63, doi: [10.1051/0004-6361/201116617](http://doi.org/10.1051/0004-6361/201116617)

Beckwith, S. V. W., Sargent, A. I., Chini, R. S., & Guesten,
R. 1990, AJ, 99, 924, doi: [10.1086/115385](http://doi.org/10.1086/115385)

Bell, C. P. M., Naylor, T., Mayne, N. J., Jeffries, R. D., &

Littlefair, S. P. 2013, MNRAS, 434, 806,

doi: [10.1093/mnras/stt1075](http://doi.org/10.1093/mnras/stt1075)



Booth, A. S., & Ilee, J. D. 2020, MNRAS, 493, L108,

doi: [10.1093/mnrasl/slaa014](http://doi.org/10.1093/mnrasl/slaa014)

Bosman, A. D., Walsh, C., & van Dishoeck, E. F. 2018,

A&A, 618, A182, doi: [10.1051/0004-6361/201833497](http://doi.org/10.1051/0004-6361/201833497)

Bowler, B. P. 2016, PASP, 128, 102001,

doi: [10.1088/1538-3873/128/968/102001](http://doi.org/10.1088/1538-3873/128/968/102001)

Cazzoletti, P., Manara, C. F., Baobab Liu, H., et al. 2019,

A&A, 626, A11, doi: [10.1051/0004-6361/201935273](http://doi.org/10.1051/0004-6361/201935273)

Cieza, L. A., Ru´ız-Rodr´ıguez, D., Hales, A., et al. 2019,
MNRAS, 482, 698, doi: [10.1093/mnras/sty2653](http://doi.org/10.1093/mnras/sty2653)

Clarke, C. J. 2007, MNRAS, 376, 1350,

doi: [10.1111/j.1365-2966.2007.11547.x](http://doi.org/10.1111/j.1365-2966.2007.11547.x)

Cleeves, L. I., Bergin, E. A., & Adams, F. C. 2014, ApJ,
794, 123, doi: [10.1088/0004-637X/794/2/123](http://doi.org/10.1088/0004-637X/794/2/123)

Close, J. L., & Pittard, J. M. 2017, MNRAS, 469, 1117,

doi: [10.1093/mnras/stx897](http://doi.org/10.1093/mnras/stx897)

Cody, A. M., & Hillenbrand, L. A. 2018, AJ, 156, 71,
doi: [10.3847/1538-3881/aacead](http://doi.org/10.3847/1538-3881/aacead)

Concha-Ram´ırez, F., Wilhelm, M. J. C., Portegies Zwart,

S., & Haworth, T. J. 2019, MNRAS, 490, 5678,

doi: [10.1093/mnras/stz2973](http://doi.org/10.1093/mnras/stz2973)

Cumming, A., Butler, R. P., Marcy, G. W., et al. 2008,
PASP, 120, 531, doi: [10.1086/588487](http://doi.org/10.1086/588487)

Cunha, K., & Smith, V. V. 1996, A&A, 309, 892

Dale, J. E., Ngoumou, J., Ercolano, B., & Bonnell, I. A.
2014, MNRAS, 442, 694, doi: [10.1093/mnras/stu816](http://doi.org/10.1093/mnras/stu816)

D’Angelo, G., Lubow, S. H., & Bate, M. R. 2006, ApJ, 652,
1698, doi: [10.1086/508451](http://doi.org/10.1086/508451)

Davidson-Pilon, C., Kalderstam, J., Jacobson, N., et al.

2020, CamDavidsonPilon/lifelines: v0.24.15, v0.24.15,
Zenodo, doi: [10.5281/zenodo.3934629](http://doi.org/10.5281/zenodo.3934629)

de Geus, E. J. 1992, A&A, 262, 258

Debes, J. H., Poteet, C. A., Jang-Condell, H., et al. 2017,
ApJ, 835, 205, doi: [10.3847/1538-4357/835/2/205](http://doi.org/10.3847/1538-4357/835/2/205)

Diplas, A., & Savage, B. D. 1994, ApJS, 93, 211,
doi: [10.1086/192052](http://doi.org/10.1086/192052)

Dolan, C. J., & Mathieu, R. D. 1999, AJ, 118, 2409,

doi: [10.1086/301075](http://doi.org/10.1086/301075)
—. 2001, AJ, 121, 2124, doi: [10.1086/319946](http://doi.org/10.1086/319946)

Eistrup, C., Walsh, C., & van Dishoeck, E. F. 2016, A&A,

595, A83, doi: [10.1051/0004-6361/201628509](http://doi.org/10.1051/0004-6361/201628509)

Espaillat, C., Muzerolle, J., Najita, J., et al. 2014, in

Protostars and Planets VI, ed. H. Beuther, R. S. Klessen,

C. P. Dullemond, & T. Henning, 497,
doi: 10.2458/azu ~~u~~ apress ~~[9](http://doi.org/10.2458/azu_uapress_9780816531240-ch022)~~ 780816531240-ch022

Facchini, S., Clarke, C. J., & Bisbas, T. G. 2016, MNRAS,

457, 3593, doi: [10.1093/mnras/stw240](http://doi.org/10.1093/mnras/stw240)

Facchini, S., Ricci, L., & Lodato, G. 2014, MNRAS, 442,

3700, doi: [10.1093/mnras/stu1149](http://doi.org/10.1093/mnras/stu1149)

20 Ansdell et al.



Fang, M., van Boekel, R., King, R. R., et al. 2012, A&A,

539, A119, doi: [10.1051/0004-6361/201015914](http://doi.org/10.1051/0004-6361/201015914)


Fazio, G. G., Hora, J. L., Allen, L. E., et al. 2004, ApJS,

154, 10, doi: [10.1086/422843](http://doi.org/10.1086/422843)


Folsom, C. P., Bagnulo, S., Wade, G. A., et al. 2012,

MNRAS, 422, 2072,

doi: [10.1111/j.1365-2966.2012.20718.x](http://doi.org/10.1111/j.1365-2966.2012.20718.x)


Fung, J., & Chiang, E. 2017, ApJ, 839, 100,

doi: [10.3847/1538-4357/aa6934](http://doi.org/10.3847/1538-4357/aa6934)


Gaia Collaboration, Prusti, T., de Bruijne, J. H. J., et al.

2016, A&A, 595, A1, doi: [10.1051/0004-6361/201629272](http://doi.org/10.1051/0004-6361/201629272)


Gaia Collaboration, Brown, A. G. A., Vallenari, A., et al.

2018, A&A, 616, A1, doi: [10.1051/0004-6361/201833051](http://doi.org/10.1051/0004-6361/201833051)


Galli, P. A. B., Bouy, H., Olivares, J., et al. 2020, arXiv

e-prints, arXiv:2001.05190.

[https://arxiv.org/abs/2001.05190](https://arxiv.org/abs/2001.05190)


Greaves, J. S., & Rice, W. K. M. 2010, MNRAS, 407, 1981,

doi: [10.1111/j.1365-2966.2010.17043.x](http://doi.org/10.1111/j.1365-2966.2010.17043.x)


Grenier, I. A., Black, J. H., & Strong, A. W. 2015, ARA&A,

53, 199, doi: [10.1146/annurev-astro-082214-122457](http://doi.org/10.1146/annurev-astro-082214-122457)


Guarcello, M. G., Drake, J. J., Wright, N. J., et al. 2016,

arXiv e-prints, arXiv:1605.01773.

[https://arxiv.org/abs/1605.01773](https://arxiv.org/abs/1605.01773)


Haworth, T. J., Boubert, D., Facchini, S., Bisbas, T. G., &

Clarke, C. J. 2016, MNRAS, 463, 3616,

doi: [10.1093/mnras/stw2280](http://doi.org/10.1093/mnras/stw2280)


Haworth, T. J., Facchini, S., Clarke, C. J., & Cleeves, L. I.

2017, MNRAS, 468, L108, doi: [10.1093/mnrasl/slx037](http://doi.org/10.1093/mnrasl/slx037)


Haworth, T. J., Facchini, S., Clarke, C. J., & Mohanty, S.

2018, MNRAS, 475, 5460, doi: [10.1093/mnras/sty168](http://doi.org/10.1093/mnras/sty168)


Haworth, T. J., & Owen, J. E. 2020, MNRAS, 492, 5030,

doi: [10.1093/mnras/staa151](http://doi.org/10.1093/mnras/staa151)


Henney, W. J., & O’Dell, C. R. 1999, AJ, 118, 2350,

doi: [10.1086/301087](http://doi.org/10.1086/301087)


Herczeg, G. J., & Hillenbrand, L. A. 2015, ApJ, 808, 23,

doi: [10.1088/0004-637X/808/1/23](http://doi.org/10.1088/0004-637X/808/1/23)


Hern´andez, J., Calvet, N., Hartmann, L., et al. 2009, ApJ,

707, 705, doi: [10.1088/0004-637X/707/1/705](http://doi.org/10.1088/0004-637X/707/1/705)


Hern´andez, J., Morales-Calderon, M., Calvet, N., et al.

2010, ApJ, 722, 1226,

doi: [10.1088/0004-637X/722/2/1226](http://doi.org/10.1088/0004-637X/722/2/1226)


Hern´andez, J., Calvet, N., Brice˜no, C., et al. 2007, ApJ,

671, 1784, doi: [10.1086/522882](http://doi.org/10.1086/522882)


Hildebrand, R. H. 1983, QJRAS, 24, 267


Hollenbach, D., Johnstone, D., Lizano, S., & Shu, F. 1994,

ApJ, 428, 654, doi: [10.1086/174276](http://doi.org/10.1086/174276)


Hoogerwerf, R., de Bruijne, J. H. J., & de Zeeuw, P. T.

2000, ApJL, 544, L133, doi: [10.1086/317315](http://doi.org/10.1086/317315)


—. 2001, A&A, 365, 49, doi: [10.1051/0004-6361:20000014](http://doi.org/10.1051/0004-6361:20000014)



Hunter, J. D. 2007, Computing In Science & Engineering,

9, 90, doi: [10.1109/MCSE.2007.55](http://doi.org/10.1109/MCSE.2007.55)


Indriolo, N., Blake, G. A., Goto, M., et al. 2010, ApJ, 724,

1357, doi: [10.1088/0004-637X/724/2/1357](http://doi.org/10.1088/0004-637X/724/2/1357)


Johnstone, D., Hollenbach, D., & Bally, J. 1998, ApJ, 499,

758, doi: [10.1086/305658](http://doi.org/10.1086/305658)


Kama, M., Folsom, C. P., & Pinilla, P. 2015, A&A, 582,

L10, doi: [10.1051/0004-6361/201527094](http://doi.org/10.1051/0004-6361/201527094)


Kenyon, S. J., & Hartmann, L. 1995, ApJS, 101, 117,

doi: [10.1086/192235](http://doi.org/10.1086/192235)


Kim, J. S., Clarke, C. J., Fang, M., & Facchini, S. 2016,

ApJL, 826, L15, doi: [10.3847/2041-8205/826/1/L15](http://doi.org/10.3847/2041-8205/826/1/L15)


Kounkel, M., Covey, K., Su´arez, G., et al. 2018, AJ, 156,

84, doi: [10.3847/1538-3881/aad1f1](http://doi.org/10.3847/1538-3881/aad1f1)


Kurtovic, N. T., P´erez, L. M., Benisty, M., et al. 2018,

ApJL, 869, L44, doi: [10.3847/2041-8213/aaf746](http://doi.org/10.3847/2041-8213/aaf746)


Lang, W. J., Masheder, M. R. W., Dame, T. M., &

Thaddeus, P. 2000, A&A, 357, 1001


Lavalley, M., Isobe, T., & Feigelson, E. 1992, Astronomical

Society of the Pacific Conference Series, Vol. 25, ASURV:

Astronomy Survival Analysis Package, ed. D. M. Worrall,

C. Biemesderfer, & J. Barnes, 245


Le Petit, F., Ruaud, M., Bron, E., et al. 2016, A&A, 585,

A105, doi: [10.1051/0004-6361/201526658](http://doi.org/10.1051/0004-6361/201526658)


Lee, D., Seon, K.-I., & Jo, Y.-S. 2015, ApJ, 806, 274,

doi: [10.1088/0004-637X/806/2/274](http://doi.org/10.1088/0004-637X/806/2/274)


Lucas, W. E., Bonnell, I. A., & Dale, J. E. 2020, MNRAS,

493, 4700, doi: [10.1093/mnras/staa451](http://doi.org/10.1093/mnras/staa451)


Luhman, K. L., & Esplin, T. L. 2020, AJ, 160, 44,

doi: [10.3847/1538-3881/ab9599](http://doi.org/10.3847/1538-3881/ab9599)


Lynden-Bell, D., & Pringle, J. E. 1974, MNRAS, 168, 603,

doi: [10.1093/mnras/168.3.603](http://doi.org/10.1093/mnras/168.3.603)


Maddalena, R. J., & Morris, M. 1987, ApJ, 323, 179,

doi: [10.1086/165818](http://doi.org/10.1086/165818)


Majewski, S. R., Schiavon, R. P., Frinchaboy, P. M., et al.

2017, AJ, 154, 94, doi: [10.3847/1538-3881/aa784d](http://doi.org/10.3847/1538-3881/aa784d)


Manara, C. F., Morbidelli, A., & Guillot, T. 2018a, A&A,

618, L3, doi: [10.1051/0004-6361/201834076](http://doi.org/10.1051/0004-6361/201834076)


Manara, C. F., Prusti, T., Comeron, F., et al. 2018b, A&A,

615, L1, doi: [10.1051/0004-6361/201833383](http://doi.org/10.1051/0004-6361/201833383)


Manara, C. F., Natta, A., Rosotti, G. P., et al. 2020, arXiv

e-prints, arXiv:2004.14232.

[https://arxiv.org/abs/2004.14232](https://arxiv.org/abs/2004.14232)


Mann, R. K., Di Francesco, J., Johnstone, D., et al. 2014,

ApJ, 784, 82, doi: [10.1088/0004-637X/784/1/82](http://doi.org/10.1088/0004-637X/784/1/82)


Mathews, G. S., Williams, J. P., & M´enard, F. 2012, ApJ,

753, 59, doi: [10.1088/0004-637X/753/1/59](http://doi.org/10.1088/0004-637X/753/1/59)


Mathieu, R. 2015, _λ_ Ori: A Case Study in Star Formation,

147–163, doi: [10.1007/978-3-662-47290-3](http://doi.org/10.1007/978-3-662-47290-3_11) ~~1~~ 1

ALMA Survey of _λ_ Orionis Disks 21



Mathieu, R. D. 2008, The _λ_ Orionis Star Forming Region,

ed. B. Reipurth, Vol. 4, 757

Maxted, P. F. L., Jeffries, R. D., Oliveira, J. M., Naylor, T.,

& Jackson, R. J. 2008, MNRAS, 385, 2210,

doi: [10.1111/j.1365-2966.2008.13008.x](http://doi.org/10.1111/j.1365-2966.2008.13008.x)

McMullin, J. P., Waters, B., Schiebel, D., Young, W., &

Golap, K. 2007, Astronomical Society of the Pacific

Conference Series, Vol. 376, CASA Architecture and

Applications, ed. R. A. Shaw, F. Hill, & D. J. Bell, 127

Miotello, A., van Dishoeck, E. F., Williams, J. P., et al.

2017, A&A, 599, A113,

doi: [10.1051/0004-6361/201629556](http://doi.org/10.1051/0004-6361/201629556)

Miotello, A., Facchini, S., van Dishoeck, E. F., et al. 2019,

A&A, 631, A69, doi: [10.1051/0004-6361/201935441](http://doi.org/10.1051/0004-6361/201935441)

Muley, D., Fung, J., & van der Marel, N. 2019, ApJL, 879,
L2, doi: [10.3847/2041-8213/ab24d0](http://doi.org/10.3847/2041-8213/ab24d0)

Murdin, P., & Penston, M. V. 1977, MNRAS, 181, 657,

doi: [10.1093/mnras/181.4.657](http://doi.org/10.1093/mnras/181.4.657)

Najita, J. R., & Kenyon, S. J. 2014, MNRAS, 445, 3315,
doi: [10.1093/mnras/stu1994](http://doi.org/10.1093/mnras/stu1994)

Nielsen, E. L., De Rosa, R. J., Macintosh, B., et al. 2019,

AJ, 158, 13, doi: [10.3847/1538-3881/ab16e9](http://doi.org/10.3847/1538-3881/ab16e9)

Pascucci, I., Testi, L., Herczeg, G. J., et al. 2016, ApJ, 831,
125, doi: [10.3847/0004-637X/831/2/125](http://doi.org/10.3847/0004-637X/831/2/125)

P´erez, L. M., Benisty, M., Andrews, S. M., et al. 2018,
ApJL, 869, L50, doi: [10.3847/2041-8213/aaf745](http://doi.org/10.3847/2041-8213/aaf745)

Pinilla, P., Pascucci, I., & Marino, S. 2020, A&A, 635,

A105, doi: [10.1051/0004-6361/201937003](http://doi.org/10.1051/0004-6361/201937003)

Pinilla, P., Benisty, M., de Boer, J., et al. 2018, ApJ, 868,
85, doi: [10.3847/1538-4357/aae824](http://doi.org/10.3847/1538-4357/aae824)
Ribas, A., [´] Bouy, H., & Mer´ın, B. 2015, A&A, 576, A52,
doi: [10.1051/0004-6361/201424846](http://doi.org/10.1051/0004-6361/201424846)

Rieke, G. H., Young, E. T., Engelbracht, C. W., et al. 2004,
ApJS, 154, 25, doi: [10.1086/422717](http://doi.org/10.1086/422717)

Rigliaco, E., Natta, A., Randich, S., & Sacco, G. 2009,
A&A, 495, L13, doi: [10.1051/0004-6361/200811535](http://doi.org/10.1051/0004-6361/200811535)

Rosenfeld, K. A., Qi, C., Andrews, S. M., et al. 2012, ApJ,

757, 129, doi: [10.1088/0004-637X/757/2/129](http://doi.org/10.1088/0004-637X/757/2/129)

Rosenthal, M. M., Chiang, E. I., Ginzburg, S., &

Murray-Clay, R. A. 2020, MNRAS,
doi: [10.1093/mnras/staa1721](http://doi.org/10.1093/mnras/staa1721)

Sacco, G. G., Franciosini, E., Randich, S., & Pallavicini, R.

2008, A&A, 488, 167, doi: [10.1051/0004-6361:20079049](http://doi.org/10.1051/0004-6361:20079049)

Scally, A., & Clarke, C. 2001, MNRAS, 325, 449,
doi: [10.1046/j.1365-8711.2001.04274.x](http://doi.org/10.1046/j.1365-8711.2001.04274.x)

Schwarz, K. R., Bergin, E. A., Cleeves, L. I., et al. 2018a,
ApJ, 856, 85, doi: [10.3847/1538-4357/aaae08](http://doi.org/10.3847/1538-4357/aaae08)
—. 2018b, ApJ, 856, 85, doi: [10.3847/1538-4357/aaae08](http://doi.org/10.3847/1538-4357/aaae08)



Sellek, A. D., Booth, R. A., & Clarke, C. J. 2020, MNRAS,

492, 1279, doi: [10.1093/mnras/stz3528](http://doi.org/10.1093/mnras/stz3528)


Siess, L., Dufour, E., & Forestini, M. 2000, A&A, 358, 593.


[https://arxiv.org/abs/astro-ph/0003477](https://arxiv.org/abs/astro-ph/0003477)


Skrutskie, M. F., Cutri, R. M., Stiening, R., et al. 2006, AJ,

131, 1163, doi: [10.1086/498708](http://doi.org/10.1086/498708)


St¨orzer, H., & Hollenbach, D. 1999, ApJ, 515, 669,

doi: [10.1086/307055](http://doi.org/10.1086/307055)


Takami, M., Hasegawa, Y., Muto, T., et al. 2014, ApJ, 795,

71, doi: [10.1088/0004-637X/795/1/71](http://doi.org/10.1088/0004-637X/795/1/71)


Tazzari, M., Testi, L., Natta, A., et al. 2017, A&A, 606,

A88, doi: [10.1051/0004-6361/201730890](http://doi.org/10.1051/0004-6361/201730890)


Trapman, L., Ansdell, M., Hogerheijde, M. R., et al. 2020,

arXiv e-prints, arXiv:2004.07257.

[https://arxiv.org/abs/2004.07257](https://arxiv.org/abs/2004.07257)


Tripathi, A., Andrews, S. M., Birnstiel, T., & Wilner, D. J.

2017, ApJ, 845, 44, doi: [10.3847/1538-4357/aa7c62](http://doi.org/10.3847/1538-4357/aa7c62)


van der Marel, N., Williams, J. P., Ansdell, M., et al. 2018,

ApJ, 854, 177, doi: [10.3847/1538-4357/aaaa6b](http://doi.org/10.3847/1538-4357/aaaa6b)


van Terwisga, S. E., Hacar, A., & van Dishoeck, E. F.

2019a, A&A, 628, A85,

doi: [10.1051/0004-6361/201935378](http://doi.org/10.1051/0004-6361/201935378)


van Terwisga, S. E., van Dishoeck, E. F., Cazzoletti, P.,

et al. 2019b, A&A, 623, A150,

doi: [10.1051/0004-6361/201834257](http://doi.org/10.1051/0004-6361/201834257)


Williams, J. P. 2012, Meteoritics and Planetary Science, 47,

1915, doi: [10.1111/maps.12028](http://doi.org/10.1111/maps.12028)


Winn, J. N., & Fabrycky, D. C. 2015, ARA&A, 53, 409,

doi: [10.1146/annurev-astro-082214-122246](http://doi.org/10.1146/annurev-astro-082214-122246)


Winter, A. J., Clarke, C. J., Rosotti, G., et al. 2018,

MNRAS, 478, 2700, doi: [10.1093/mnras/sty984](http://doi.org/10.1093/mnras/sty984)


Winter, A. J., Clarke, C. J., & Rosotti, G. P. 2019,

MNRAS, 485, 1489, doi: [10.1093/mnras/stz473](http://doi.org/10.1093/mnras/stz473)


Winter, A. J., Kruijssen, J. M. D., Chevance, M., Keller,

B. W., & Longmore, S. N. 2020, MNRAS, 491, 903,

doi: [10.1093/mnras/stz2747](http://doi.org/10.1093/mnras/stz2747)


Wyatt, M. C. 2008, ARA&A, 46, 339,

doi: [10.1146/annurev.astro.45.051806.110525](http://doi.org/10.1146/annurev.astro.45.051806.110525)


Zamora-Avil´es, M., Ballesteros-Paredes, J., Hern´andez, J.,

et al. 2019, MNRAS, 488, 3406,

doi: [10.1093/mnras/stz1897](http://doi.org/10.1093/mnras/stz1897)


Zhu, Z., Nelson, R. P., Hartmann, L., Espaillat, C., &

Calvet, N. 2011, ApJ, 729, 47,

doi: [10.1088/0004-637X/729/1/47](http://doi.org/10.1088/0004-637X/729/1/47)


Zhu, Z., Zhang, S., Jiang, Y.-F., et al. 2019, ApJL, 877,

L18, doi: [10.3847/2041-8213/ab1f8c](http://doi.org/10.3847/2041-8213/ab1f8c)


</paper>

## Items to check

```json
[
 {
  "path": "software[0].used_for.evidence[0]",
  "value": "pipeline calibration, split, tclean, uvmodelfit, uvcontsub",
  "failed_quote": "using the uvmodelfit task in CASA"
 }
]
```
