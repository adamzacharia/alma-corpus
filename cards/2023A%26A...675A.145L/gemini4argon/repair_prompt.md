# Repair task for a Claude Code subagent

A methods card has evidence quotes that were not found verbatim in the paper. Below are the rules, the paper, and the failing items. Write ONE JSON object, nothing else, of the form {"repairs": [{"path": ..., "found": true|false, "loc": ..., "quote": ...}, ...]} with one entry per item (path unchanged) to:

    C:\Users\adama\alma-corpus\cards\2023A%26A...675A.145L\gemini4argon\repair_reply.txt

Use the Write tool for that file. Copy each quote character for character from the paper text below; a returned quote is checked mechanically and dropped if it is not in the paper. Do not read any other file, do not run commands, and do not change anything else. Reply with one line when done.

---

## Rules

You check evidence quotes for a methods card extracted from an astronomy paper. Some quotes could not be found verbatim in the paper text, and some stated values came without a quote. For each item: find the passage in the paper that supports the value and copy it VERBATIM (same words and order, at most 40 words; LaTeX markup may be dropped) with its loc (section heading, "abstract", "Table N" or "Figure N caption"). If the paper does not support the value, return found = false and leave quote and loc empty. Use only the paper text. Return one entry per item, with the item's path unchanged.

## Paper

<paper>
Astronomy & Astrophysics manuscript no. HSL-PMonnier ©ESO 2023
June 19, 2023

## **The Dark Neutral Medium is (Mostly) Molecular Hydrogen**


H. Liszt [1] and M. Gerin [2]


1 National Radio Astronomy Observatory, 520 Edgemont Road, Charlottesville, VA, USA 22903 e-mail: hliszt@nrao.edu
2 LERMA, Observatoire de Paris, PSL Research University CNRS Sorbonne Université
e-mail: maryvonne.gerin@obspm.fr


received June 19, 2023


**ABSTRACT**


Context. More gas is sometimes inferred in molecular cloud complexes than is represented in HI or CO emission, and this is called
dark neutral medium (DNM).
Aims. Our aim is to extend a study of DNM along 13 directions in the outskirts of Chamaeleon by determining the atomic or molecular
character of the DNM along a larger sample of sightlines.
Methods. We acquired ALMA ground rotational state absorption profiles of HCO [+] and other molecules toward 33 compact extragalactic continuum background sources seen toward the Galactic anticenter, deriving N(H 2 ) = N(HCO [+] )/3 × 10 [−][9] as before. We
observed J=1-0 CO emission with the IRAM 30m telescope in directions where HCO [+] was newly detected.
Results. HCO [+] absorption was detected in 28 of 33 new directions and CO emission along 19 of those 28. The five sightlines lacking
detectable HCO [+] have three times lower <E B−V   - and <N(DNM)>. Binned in E B−V, N(H 2 ) and N(DNM) are strongly correlated and
vary by factors of 50-100 over the observed range E B−V ≈ 0.05 - 1 mag, while N(HI) varies by factors of only 2-3. On average N(DNM)
and N(H 2 ) are well matched, and detecting HCO [+] absorption adds little to no H 2 in excess of the previously inferred DNM. There
are five cases where 2N(H 2 ) < N(DNM)/2 indicates saturation of the HI emission profile. For sightlines with W CO ≥ 1 K-km s [−][1], the
CO-H 2 conversion factor N(H 2 )/W CO = 2 − 3 × 10 [20] cm [−][2] /(1 K-km s [−][1] ) is higher than is derived from studies of resolved clouds in

γ-rays.
Conclusions. Our work sampled primarily atomic gas with a mean H 2 fraction ≈ 1/3, but the DNM is almost entirely molecular. CO
fulfills its role as an H 2 tracer when its emission is strong, but large-scale CO surveys are not sensitive to H 2 columns associated with
typical values N(DNM) = 2 − 6 × 10 [20] cm [−][2] . Lower X CO values from γ-ray studies arise in part from different definitions and usage.
Sightlines with W CO ≥ 1 K-km s [−][1] represent 2/3 of the H 2 detected in HCO [+] and detecting 90% of the H 2 would require detecting CO
at levels W CO ≈ 0.2-0.3 K-km s [−][1] .



**Key words.** interstellar medium – abundances


**1.** **Introduction**


Between the atomic and molecular interstellar gases there is a
transition that is imperfectly traced in λ21cm HI and/or λ2.6mm
CO emission. Gas that is not well represented in one or both tracers is described as dark neutral medium (DNM) (Grenier et al.
2005; Planck Collaboration et al. 2015; Remy et al. 2017, 2018),
and the atomic or molecular character of the DNM can only be
decided by appealing to other information.
In the outskirts of Chamaeleon, we used millimeter-wave
HCO [+] absorption to show that the DNM was almost exclusively
molecular, even while the gas as a whole was mostly atomic
(Liszt et al. 2018). HCO [+] was detected along all 13 sampled
sightlines, of which 12 lacked detectable CO emission at a level
of 1.5 K-kms [−][1] . The amount of inferred H 2 was comparable to
that of the DNM (confirming the amount of the detected DNM),
and only for three sightlines did it seem likely that saturation
of the HI emission profile could account for much of the DNM.
Subsequent detections of CO absorption along six directions by
Liszt et al. (2019) showed that the lack of CO emission was due
to low CO column densities. The linewidth of CO absorption
was shown to be smaller than that of its parent molecule HCO [+],
illustrating the complex chemical nature of the CO formation
process in diffuse gas.


Send offprint requests to: H. S. Liszt



In this work we extend the analysis of the composition of
DNM to 33 sightlines in directions toward the Galactic anticenter (Remy et al. 2017, 2018) and consider the larger sample of 46
sightlines. The present study employs a relatively small number
of diffuse (A V ≤ 1 mag) and translucent (A V ≤ 3 mag) sightlines
where background sources are serendipitously available, and is
not a revision of the earlier study, whose derived DNM column
densities and other results are assumed here. Rather, we use the
newly derived H 2 abundances, independent of the presence of
CO emission, to consider such topics as the atomic or molecular
character of the DNM, the degree to which the Ł21 HI profile
represents N(HI) and the influence of the CO-H 2 conversion factor on the DNM determination.

Section 2 summarizes the observational material considered
here and Section 3 compares the prior results for DNM with
atomic hydrogen measured in the Ł21 emission and H 2 as sampled by its proxy 89 GHz absorption of HCO [+] . The role of CO
emission data is explored in Section 4 where the CO-H 2 conversion factor is derived. Section 5 presents a summary, with
conclusions and a discussion of later work.


**2.** **Observations and data reduction**


The methods of work were described in Liszt et al. (2018) and
are not repeated in full detail here. From the existing DNM


Article number, page 1 of 13

A&A proofs: manuscript no. HSL-PMonnier



analyses of Planck Collaboration et al. (2015) and Remy et al.
(2017, 2018) we take N(DNM) and Ł21 HI column densities
N(HI) and N(HI) cl representing respectively the line profile integral integrated over all velocities and the column density that
is associated with the cloud and/or kinematic features hosting
the neutral gas and DNM, as derived by a decomposition that
accounts for the compound nature of HI emission profiles from
individual clouds.

To the existing analyses we add ALMA observations of absorption from HCO [+] and profiles of λ2.6mm CO emission from
the IRAM 30m telescope, as described below.


2.1. Millimeter-wave absorption


The new absorption data discussed here are spectra of HCO [+] in
33 directions along Galactic anticenter sightlines toward ALMA
phase calibrators as given in the Tables here and projected on
sky maps in Figure 1. As before, the HCO [+] spectra were acquired with a spectral resolution of 0.205 km s [−][1] sampled at
0.102 km s [−][1] intervals without the so-called spectral averaging
that bins data. We also acquired spectra of HCN, C 2 H, HCO, and
several isotopologs. Counts of detections are shown in Figure 2,
but results for species other than HCO [+] will be discussed in detail in later work. Statistics of the HCO [+] detections are shown in
Figure A.1. Spectra in the 28 directions with detectable HCO [+]
absorption are shown in Figure B.1.


2.2. IRAM 30m CO emission


We took frequency-switched CO emission profiles at the IRAM
30m telescope in August 2019 toward the 28 anticenter sightlines with detected HCO [+] absorption. The CO spectra are shown
in Figure B.1. These CO data were taken as five-point maps toward the target and displaced by 2 HPBW (2x22 [′′] ) in the four
cardinal directions, using a pointing pattern that was designed
to detect HCO [+] and HCN emission in the presence of spectral
line absorption in the target direction. For the HCO [+] emission
that will be discussed in subsequent work, the HCO [+] emission
profile is formed by averaging spectra along the four outlying
directions. For CO the present results use the average of all five
pointings because contamination by absorption is not measurable given the strength of the emission and/or the continuum.
The results are presented on the main beam antenna temperature
scale that is native to the 30m telescope.


2.3. Conversion from integrated HCO [+] absorption to N(H 2 )


The suitability of HCO [+] as a proxy for H 2 in diffuse molecular
gas was explored extensively in Liszt & Gerin (2023) (hereafter
Paper 1). As in our earlier work, we use N(H 2 ) = N(HCO [+] )/3 ×
10 [−][9] and N(HCO [+] ) = 1.10 × 10 [12] Υ HCO + where Υ HCO + is the integrated HCO [+] optical depth expressed in km s [−][1] .


2.4. Reddening and dust optical depth


The 6 [′] resolution dust-emission maps scaled to optical reddening
E B−V by Schlegel et al. (1998) are cited here. Those reddening
values can be converted to Planck 353 GHz dust optical depth
using the relationship established by Planck Collaboration et al.
(2014) between the 353 GHz dust optical depth and the E B−V
values of Schlegel et al. (1998), E B−V /τ 353 = (1.49 ± 0.03) × 10 [4]

mag.


Article number, page 2 of 13



2.5. Conventions


Velocities presented with the spectra are taken with respect to
the kinematic definition of the Local Standard of Rest. N(H) is
the column density of H nuclei detected in neutral atomic and
molecular form, N(H) = N(HI)+2N(H 2 ), and the molecular hydrogen and DNM fractions 2N(H 2 )/N(H) and N(DNM)/N(H) are
respectively represented by f H 2 and f DNM . The integrated absorption of the HCO [+] profile in units of km s [−][1] is denoted by Υ HCO+
and similarly for other species. The integrated emission of the
J=1-0 CO line is denoted by W CO with units of K-km s [−][1] and the
CO-H 2 conversion factor N(H 2 )/W CO is denoted by X CO . Where
reference is made to a typical Galactic or standard CO-H 2 conversion factor, the value N(H 2 )/W CO = 2 × 10 [20] cm [−][2] /(1 Kkm s [−][1] ) should be understood, as summarized in Table E.1 of
Remy et al. (2017).


2.6. Overview


Observational results of importance to this work are given in Table 1 and Table 2, and summaries of mean properties of various
subsamples are presented in Table 3. Some statistics of the continuum targets and noise in the detections of HCO [+] absorption
are discussed in Appendix A and the CO emission and HCO [+]
absorption line profiles are shown in Figure B.1 and discussed in
Appendix B.


**3.** **HI, DNM, and H** 2 **sampled in HCO** [+] **absorption**


Figure 1 shows the new Galactic anticenter sightlines projected
on maps of E B−V and N(DNM). The region at b < −30 [o] is described by Remy et al. (2017) as Cetus, and that at b - −22 [o] as
Taurus-Main. California lies to the north around b = −10 [o] and
Perseus is near (l,b) = 160 [o],-20 [o] . Taurus-North overlays most of
the map region. The individual subregions are not discussed here
owing to the sparse sampling.
Counts of sources and detected molecular tracers binned in
0.05 mag intervals of reddening are shown in Figure 2. HCO [+] is
the molecular tracer detected most commonly (28 of 33 anticenter sightlines and 41 of 46 overall), followed by C 2 H (26 total)
and HCN (21 total) . The properties of molecular absorption line
tracers other than HCO [+] will be discussed in later work.
The Chamaeleon and Galactic anticenter subsamples have
the same mode at E B−V = 0.25 - 0.3 mag in Figure 2, but the anticenter subsample has a high-reddening tail at E B−V - 0.5 mag
that is absent in Chamaeleon. The Galactic anticenter sample has
higher mean extinction and molecular fraction. Overall (see Table 3) the anticenter sources have the following characteristics:


– 33% higher <E B−V - = 0.36 vs 0.27 mag;
– Same <N(HI)> = 1.3 × 10 [21] cm [−][2] and f DNM = 0.12;
– 80% higher <N(HI) cl - = 1.12 vs 0.62 ×10 [21] cm [−][2] ;
– 2 times higher <2N(H 2 )> = 0.80 vs 0.39 ×10 [20] cm [−][2] ;
– 65% higher f H 2 = 0.38 vs 0.23;

–
Higher fraction of detected CO, 9/33 (18/33 in the new work)
vs 1/13;
– Higher incidence of nondetection of HCO [+], 5/33 vs 0/13, in
some cases due to low flux, see Figure A.1.


The DNM fraction is nearly the same in the two samples
(0.12-0.13) and much smaller (0.06) in both subsamples when
CO emission was detected at the level of 1 K-kms [−][1] . The DNM
fraction is also noticeably smaller when molecular gas sampled
in HCO [+] absorption is absent, and similarly at E B−V < 0.2 mag.
The strongest variations in f DNM in Table 3 arise in selections

L&G: DNM, dark and molecular gas



**-10**


**-20**


**-30**


**-40**


**-50**



~~**1**~~


~~**0.02**~~
**190** **180** **170** **160** **150** **140**

**Galactic Longitude [degrees]**



**-10**


**-20**


**-30**


**-40**


**-50**



~~**4E21**~~


~~**1E20**~~
**190** **180** **170** **160** **150** **140**

**Galactic Longitude [degrees]**



Fig. 1. Sky maps of the observed sightlines. Left: Positions of the background sources observed here are projected against a map of E B−V from
the work of Schlegel et al. (1998). The sightlines lacking detected HCO [+] absorption (largely due to weak continuum) are indicated with smaller
symbols. Right: Same as left, but shown against a map of N(DNM) from Remy et al. (2017, 2018).



based on the strength of CO emission and are discussed in Section 4.


3.1. Quantitative summary results


Figure 3 shows an overview of trends in means of N(HI),
N(DNM), and N(H 2 ) using data binned in 0.05 mag intervals of
reddening as in Figure 2, plotted horizontally at the mean E B−V
in every bin. The counts in each bin are shown and the bins at
E B−V - 0.5 mag are occupied by only one or two sightlines. The
association of DNM with molecular gas is unmistakable.
The mean HI column density varies by only a factor of 3
over a wider range E B−V = 0.09 - 1 mag. By contrast, means of
N(NDM) and N(H 2 ) vary by factors of 50-100. The values of
<N(DNM)> and <N(H 2 )> are comparable and increase steadily
for E B−V ∼ [<] 0.7 mag, beyond which <N(DNM)> either fails to
increase or falls: the CO emission tracer used to derive N(DNM)
was used effectively to account for H nuclei in H 2 . The cloudassociated mean N(HI) cl declines at E B−V ≥ 0.7 mag as H 2 sequesters H nuclei. The value of <N(H 2 )> increases up to the bins
at highest E B−V where <N(H 2 )> ≈ <N(HI>) ≈ 2 − 3 <N(HI) cl and whole sightlines are dominated by molecular gas.
The correlation between DNM and H 2 is remarkable considering the vastly different scales on which E B−V, N(HI), and
N(NDM) are measured (6-20 [′] ), as contrasted with N(H 2 ) ∝
Υ HCO + that is derived on submilliarcsecond scales from absorption against scatter-broadened compact millimeter-wave ALMA
calibrator continuum sources. The same kind of correlation of
tracers observed on different angular scales occurs in the correlation of integrated λ21cm HI optical depth with E B−V (Liszt
2021).
When HCO [+] is not detected (5/46 directions) the following
characteristics are found compared to sightlines with detected
HCO [+] :


– 3 times lower <E B−V - = 0.13 mag;
– 1.3 times higher <N(H)>/<E B−V - = 8 × 10 [21] cm [−][2] mag [−][1] ;
– 3.5 times lower <N(DNM)> = 8 × 10 [19] cm [−][2] ;



**0.0** **0.2** **0.4** **0.6** **0.8** **1.0**

**E(B-V) [mag]**


Fig. 2. Counts of sightlines and detected tracers binned in 0.05 intervals
of reddening, E B−V . The histogram of all sources is overlaid (dashed
red) in the other panels.


– 2 times lower <f DNM - = 0.07;
– no DNM in 3/5 cases vs. 15/46 overall.


Instead, using 3σ upper limits for N(H 2 ) we find:


Article number, page 3 of 13



**10**

**8**
**6**
**4**
**2**


**10**

**8**
**6**
**4**
**2**


**10**

**8**
**6**
**4**
**2**


**10**

**8**
**6**
**4**
**2**


**10**

**8**
**6**
**4**
**2**


**10**

**8**
**6**
**4**
**2**



**Sources w/CO emission (19)**


**Sources w/HCN (21)**


**Sources w/C2H (26)**


**Sources w/HCO** **[+]** **(41)**


**All sources (46)**


**Chamaeleon sources (13)**

A&A proofs: manuscript no. HSL-PMonnier



– >5 times lower <2N(H 2 )>≤ 1.5 × 10 [20] cm [−][2] and
– >2.5 times lower <f H 2 >≤ 0.14


The ensemble of sightlines with N(DNM) < 5 × 10 [19] cm [−][2]
does not differ by more than 10-20% from other sightlines in
any mean property not involving N(DNM). The variations in
N(DNM) and N(H 2 ) stand in great contrast with N(HI) that increases only by a factor of 3 across the figure. The rise in N(H 2 )
accounts for the failure of N(HI) to increase at high E B−V, but
this could in principle also be explained by increasing saturation of the HI emission. As noted in Planck Collaboration et al.
(2015) and further refined by Remy et al. (2018), the global
DNM analysis finds the best fit with the optically thin estimate
of N(HI), implicitly leaving a bigger overall role for molecular
gas than for saturation of the HI profile.


3.2. DNM and HI


Shown in Figure 4 is the variation of <N(DNM)> with <N(HI)>
and <N(HI) cl >. Chamaeleon differs from the Galactic anticenter
in having more extraneous atomic gas along the line of sight and
smaller values of cloud-associated gas. The cloud-associated HI
in Chamaeleon is clustered at the low end of the range, even
though the samples are evenly matched in the span of their total
HI column density and have the same mean N(HI) in Table 3.
Sightlines lacking DNM are present at all N(HI), but
N(DNM) is uniformly small along sightlines at the highest
column densities N(HI) ∼ [>] 2.3 × 10 [21] cm [−][2] where CO emission is more commonly observed. The sources with N(DNM)
- 6 × 10 [20] cm [−][2] and high N(DNM)/N(HI) ratios are perhaps
the most obvious candidates for hosting significant quantities of
DNM in atomic form as the result of saturation of the HI profile, but only two of these actually have small contributions from
N(H 2 ). Assessing the DNM contribution arising from possible
saturation of the HI profile is discussed in Section 3.3 where
it is seen that the strongest cases of atomic DNM actually have
more modest N(DNM).


3.3. DNM, E B−V, and N(H 2 )


As with HI, sightlines lacking DNM are present over the full
range of E B−V in Figure 5, top, but they are predominant at
smaller N(H 2 ). Sightlines with 2N(H 2 ) ∼ [<] 10 [20] cm [−][2] lack DNM.
Along sightlines with column densities too low to host molecular gas, the atomic gas is well represented by the optically thin
estimates of N(HI) used in the DNM analysis.
Care must be taken in interpreting the relationship of DNM
and N(H 2 ) in Figure 5 because the DNM in part represents material that is missing in the CO emission tracer while some of the
H 2 traced by HCO [+] is actually visible in CO emission. To minimize this cross-contamination,Figure 6 shows a plot of N(DNM)
vs. N(H 2 ) for sightlines lacking a detection of CO, using the
more sensitive IRAM data for the Galactic anticenter subsample.
Included are all but one (12/13) of the Chamaeleon sightlines and
60% of those toward the anticenter.
Sightlines lacking DNM in the absence of CO emission in
Figure 6 are almost entirely confined at 2N(H 2 ) ∼ [<] 2 × 10 [20] cm [−][2],
so the detections of HCO [+] absorption do not imply much additional gas along sightlines where DNM was not found. Missing
from Figure 6 are sightlines with 2N(H 2 ) ∼ [>] 10 [21] cm [−][2] corresponding to W CO = 2.5 K-km s [−][1] for the Galactic CO-H 2 conversion factor.
There are two or three cases in each subsample where
N(DNM)/2N(H 2 ) ∼ [>] 2 and saturation of the Ł21 emission pro

Article number, page 4 of 13



file may be important. Most of these sightlines have modest values N(DNM) ≈ 4 − 5 × 10 [20] cm [−][2] and are not the sightlines with
high N(DNM) that were singled out for discussion in Section 3.2
when comparing N(DNM) and N(HI).
There are also two or three sightlines at N(H 2 )  - 6 ×
10 [20] cm [−][2] where N(DNM)/2N(H 2 ) ∼ [<] 2. Overall <2N(H 2 )> =
1.3<N(DNM)> for sources lacking CO emission, so H 2 accounts
for DNM without adding extra “dark” gas, and the DNM is
mostly molecular. As before in Chamaeleon, the DNM is largely
molecular, even if the medium overall is predominantly atomic.


**4.** **The role of CO emission**


The CO emission that was detected in previous studies used to
determine N(DNM) along our sightlines was well above 1 Kkm s [−][1] in every case (Table 2), with <W CO - = 4.9K-kms [−][1] (Table 3). This is very nearly the same mean as for the sample of
sightlines with W CO ≥ 1K-kms [−][1] observed at the IRAM 30m,
5.5 K-km s [−][1] (see Table 2). Compared to the overall average, the
sightlines with <W CO - ≥ 1K-kms [−][1] have the following characteristics:


– 50-100% higher <E B−V - = 0.5 − 0.7 mag;
– 3-4 times higher <2N(H 2 )> = 2 − 3 × 10 [21] cm [−][2] ;
– 2 times higher < fH 2 - = 0.6;
– 2 times lower <f DNM - = 0.06.


The 50% smaller DNM fractions <f DNM  - = 0.06 along samples of sightlines with <W CO - ≥ 1K-kms [−][1] indicate that CO
emission is doing a good job of tracing H 2 in gas where the
molecular fraction is high (Liszt 2017), CO emission is strong,
and the cloud-associated HI fraction declines (Figure 2). However, CO emission in general represents a small portion of the
total molecular gas present along the sightlines in this work. For
instance, <2N(H 2 )> = 7 × 10 [20] cm [−][2] along 46 sightlines, while
<W CO - ≈ 5 K-km s [−][1] along the 6-10 sightlines where <W CO ≥ 1K-kms [−][1] (Table 3). For a typical Galactic CO-H 2 conversion factor, the summed molecular gas column represented in
HCO [+] is three to four times that inferred from the summed CO
emission. Most of the molecular gas in our sample was hidden
in the DNM prior to our work and is still only revealed by the
HCO [+] absorption, even with more sensitve CO observations.
The IRAM 30m detections with <W CO - below 1K-kms [−][1] comprise less than 20% of the total amount of CO emission.


4.1. The CO-H 2 conversion factor


Comparison of the scaled HCO [+] absorption and IRAM 30 emission measurements provides the most direct determination of the
actual CO-H 2 conversion factor along the lines of sight studied
in this work. Figure 7 shows the trends in <N(H 2 )>, <W CO >,
and <N(H 2 )>/<W CO - binned in 0.05 mag increments of E B−V
as in Figure 3. Included are the 28 Galactic anticenter sightlines
where HCO [+] was detected, with W CO taken at the 3σ upper
limit for sightlines where CO emission was not detected with
greater significance. Also included is the sightline toward J1733
in Chamaeleon where CO emission was detected. The 3σ upper
limits W CO ≤ 1.5 K-kms [−][1] in Chamaeleon are not useful.
Figure 7 illustrates the behavior of the CO-H 2 conversion
factor that is tabulated for different samples in Table 3. The values of <N(H 2 )> and <W CO - both increase steadily with E B−V
in Figure 7, but at different rates so that their ratio declines by
a factor ≈ 7 to <N(H 2 )>/<W CO - = 2.5 − 3 × 10 [20] H 2 cm [−][2] (Kkm s [−][1] ) [−][1] for E B−V ∼ [>] 0.5 mag. Variations of similar magnitude in

L&G: DNM, dark and molecular gas



**10** **[21]**


**10** **[20]**



3 7 3 4 11 4 2 3 3 1 1 1 1 2


N(H2)
N(DNM)
N(HI)


**0.1** **1**

**E(B-V) [mag]**



3 7 3 4 11 4 2 3 3 1 1 1 1 2


N(H2)
N(DNM)
N(HI)cl


**0.1** **1**
**E(B-V) [mag]**



Fig. 3. Trends in mean N(HI), N(H 2 ), and N(DNM). The results are binned in 0.05 mag intervals of E B−V . Left: N(HI) is calculated over the whole
line profile. Right: N(HI) = N(HI) cl the HI column density associated with the clouds studied here. The number of sightlines in each bin is shown
in both panels.



**1.2E21**


**1.0E21**


**8.0E20**


**6.0E20**


**4.0E20**


**2.0E20**


**0**


**1.2E21**


**1.0E21**


**8.0E20**


**6.0E20**


**4.0E20**


**2.0E20**



Chamaeleon
Anticenter


**5.0E20** **1.0E21** **1.5E21** **2.0E21** **2.5E21**

**N(HI)cl [cm** **[-2]** **]**


Chamaeleon
Anticenter



**0**


**5.0E20** **1.0E21** **1.5E21** **2.0E21** **2.5E21**

**N(HI) [cm** **[-2]** **]**


Fig. 4. N(DNM) plotted against total sightline N(HI) (bottom) and
cloud-associated atomic hydrogen N(Hi) cl (top).


individual diffuse and/or translucent MBM clouds were reported
by Magnani et al. (1998) and Cotten & Magnani (2013).
Mean values of N(H 2 )/W CO are 2 − 2.5 × 10 [20] H 2 cm [−][2] (Kkm s [−][1] ) [−][1] for the old and new samples with <W CO - ≥ 1 Kkm s [−][1], increasing by factors of 2-3 for the samples with IRAM
30m detections below 1K-kms [−][1] and upper limits. Also see the
inset in Figure 7 on this point..
The values of the CO-H 2 conversion factor derived are comparable to those derived in extant Galactic-scale γ-ray analyses
(Table E.1 in Remy et al. 2017) when W CO ∼ [>] 1 K-kms [−][1], but
are uniformly larger than those derived in cloud-level studies
like the DNM analysis whose results are summarized in Table
2 of Remy et al. (2017). Those results ranged from 1 − 1.6 ×
10 [20] H 2 cm [−][2] (K-kms [−][1] ) [−][1] for determinations based on dust and



from 0.44 − 1.00 × 10 [20] H 2 cm [−][2] (K-kms [−][1] ) [−][1] for determinations
based on gamma rays.
There is no contradiction with the larger values found in
this work whose method of studying widely separated, semirandomly placed sightlines is similar to the larger scale studies.
The strongly CO-emitting (W CO - 10 K-kms [−][1] ) regions encountered in the cloud-level studies that have generally small values
of X CO (see Figure 13 in Remy et al. 2018) were not sampled
here.
There may also be a difference arising from the operational
definition of the conversion factor. The conversion factors in Table 2 in Remy et al. (2017) are those that optimize the fit of the γray or dust emissivity to a total hydrogen column density that is
represented schematically as N(H) = N(HI)+N(DNM)+2N(H 2 )
= N(HI)+N(DNM)+2X CO W CO . After the analysis, there remains
a DNM constituent whose molecular fraction is undetermined
and not explicitly considered in the definition of the multiplier
X CO ; we showed that the DNM is largely molecular. By contrast, the present analysis determines N(H 2 ) independent of CO
emission and defines X CO = N(H 2 )/W CO . This N(H 2 ) includes
the molecular component of the DNM that we took pains to consider separately in the discussion of Figure 6.


4.2. Achievable limits and detection thresholds for CO, DNM,
and H 2


Sightlines in our study often had rms CO emission noise ∆W CO
>∼ 1/3 − 1/2 K-kms [−][1] in the prior DNM analysis (Table 2). For
a typical Galactic conversion 2N(H 2 )/W CO = 4 × 10 [20] cm [−][2] (Kkms) [−][1], the equivalent 3σ threshold detection limits on the hydrogen column are 2N(H 2 ) = 4 − 6 × 10 [20] cm [−][2], above the actual
values of N(DNM) along most of the sightlines we observed. By
contrast, the median 3σ detection threshold from HCO [+] in our
work is 2N(H 2 ) > 1.1 × 10 [20] cm [−][2] and typical N(DNM) values
are N(DNM) ∼ [>] 2 × 10 [20] cm [−][2] (Figure 6).
The effectiveness of reducing the detection threshold of CO
emission below 1 K-km s [−][1] can be assessed by examining the
distribution of CO detections and upper limits in the IRAM 30m
CO observations. The subsamples of IRAM CO observations


Article number, page 5 of 13

H2=DNM/2


H2=DNM


H2=2*DNM


Chamaeleon
Anticenter



**1.2E21**


**1.0E21**


**8.0E20**


**6.0E20**


**4.0E20**


**2.0E20**


**0**



A&A proofs: manuscript no. HSL-PMonnier


**1.2E21**


**1E21**


**8E20**


**6E20**


**4E20**


**2E20**



Chamaeleon
Anticenter



**0**



**0.0** **0.2** **0.4** **0.6** **0.8** **1.0**

**E(B-V) [mag]**



**10** **[20]** **10** **[21]**

**2N(H2) [cm** **[-2]** **]**


Fig. 6. N(DNM) plotted against N(H 2 ) for sightlines lacking detected
CO emission in the analysis of Remy et al. (2018). Shown are loci at
which the number of H nuclei in H 2 is 50, 100, and 200% of that in
DNM.



**1.2E21**


**1.0E21**


**8.0E20**


**6.0E20**


**4.0E20**


**2.0E20**


**0**



Chamaeleon
Anticenter



**10**


**1**


**0.1**



**10** **[20]** **10** **[21]**

**2N(H2) [cm** **[-2]** **]**


Fig. 5. N(DNM) plotted against E B−V (top) and 2N(H 2 ) (bottom). Larger
symbols represent sightlines where W CO ∼ [>] 1 K-km s [−][1] .


summarized in Table 3 show 6 detections with W CO - 1 Kkm s [−][1], 12 detections with W CO < 1 K-kms [−][1], and ten upper
limits at levels W CO < 0.1 − 0.2 K-km s [−][1] (see Table 1 for values
of upper limits and Figure 3 for a graphical representation of the
data). HCO [+] was detected along all of these sightlines, and the
three subsamples respectively represent fractions 0.66, 0.26, and
0.08 of the total amount of H 2 .


Thus, a survey with a detection limit of 1 K-kms [−][1] would
detect approximately two-thirds of the molecular gas along these
diffuse and/or translucent lines of sight, and a much increased effort to reduce the detection limit to 0.2 K-kms [−][1] might find another one-fourth of the H 2 . Comparable reductions in the fraction
of undetected H 2 with increasing CO sensitivity down to rms levels ∆W CO ≈ 0.1 K-kms [−][1] were achieved by Donate & Magnani
(2017). Missing one-third of the H 2 at the 1 K-km s [−][1] threshold
is consistent with the dark gas fraction derived by Wolfire et al.
(2010) and Gong et al. (2018).


Article number, page 6 of 13



**10** **[21]**


**10** **[20]**


**10** **[19]**



2 5 2 4 7 3 1 1 3 1 1 1 1 2

1 2 1

N(H2)/WCO
WCO

N(H2)


**0.1** **1**

**E(B-V) [mag]**


Fig. 7. Trends in mean N(H 2 ) (black squares), W CO (pink diamonds),
and N(H 2 )/W CO (blue triangles). The results are binned in 0.05 mag
intervals of E B−V, as in Figure 3. Bins in which all sightlines have only
upper limits on W CO are indicated by upper and lower limits. The scales
for N(H 2 ) cm [−][2] and N(H 2 )/W CO ( cm [−][2] (K-km s [−][1] ) [−] 1) are read on the
left vertical axis and that for W CO (K-km s [−][1] ) on the right. The number
of sightlines in each bin is shown as in Figure 3 and the count is carried
separately for W CO at low E B−V . The light gray dashed line is a powerlaw fit N(H 2 ) = 10 [21][.][0973] E B−V [1][.][335] .


4.3. The wider view


In Section 4.2 we note that two-thirds of the H 2 was found along
the sightlines with W CO - 1 K-kms [−][1] and that a deeper survey
with a detection limit of 0.2 K-kms [−][1] would have found another
25% of the H 2 . At this point we can ask how the results of this
sparse sampling are reflected in the region as a whole. We drew
a hull around the observed anticenter sightlines, as shown in Fig

L&G: DNM, dark and molecular gas



ure C.1 and derived the pixel-by-pixel statistics for the contained
area, the amount of material (taken proportional to E B−V ), and
the amount of H 2 . For H 2 we used the N(H 2 )-E B−V relationship

[1]
N(H 2 ) = 10 [21][.][0973] E B−V [1][.][335] and the fact that W CO ∼ [>] 1 K-km s [−][1]
at E B−V ∼ [>] 0.4 mag or N(H 2 ) [>] ∼ 4 × 10 [20] cm [−][2] in Figure 7 (see
also Figure 5 of Paper 1).
Figure 8 shows the probability densities (at left) and cumulative distributions for the derived quantities. Reading values off
the cumulative probability distributions at right in Figure 8, conditions with E B−V ≥ 0.4 mag, N(H 2 ) ∼ [>] 4 × 10 [20] cm [−][2] occur
over one-fourth of the total area containing one-half of the total
projected gas column and two-thirds of the H 2 . Apparently, the
sampled sightlines were representative of the region as a whole
regarding the H 2 distribution.
Sampling 90% of the H 2 would require detecting CO emission at E B−V ∼ [>] 0.2 mag where N(H 2 ) ≈ 2 × 10 [20] cm [−][2] . The
sampling here is too sparse to derive an equivalent value of W CO
in Figure 7, but the broader sample in Paper 1 suggests W CO ∼ [>]
0.3 K-km s [−][1] would be appropriate. Sightlines with E B−V < 0.32
mag or A V < 1 mag comprise two-thirds of the area, one-third
of the mass, and one-fourth of the H 2 .


4.4. Comparison with predictions and models


For models, the critical factors in predicting the amount of dark
gas are the threshold where W CO reaches the 1 K-km s [−][1] brightness level and the amount of material above the threshold. In the
regime of diffuse molecular gas the integrated brightness of the
J=1-0 line is determined almost exclusively by the CO column
density, with W CO (K-kms [−][1] ) = N(CO)/10 [15] cm [−][2] for hydrogen number densities n(H) = 64 − 500 cm [−][3] (Liszt 2007, 2017;
Hu et al. 2021) and kinetic temperatures appropriate to the local
thermal pressure. This simple proportionality between column
density and brightness persists well beyond the CO column density where the J=1-0 transition becomes optically thick, owing
to the strongly subthermal excitation (Goldreich & Kwan 1974).
Thus, the CO chemistry dominates the CO brightness, and
the sky map of CO emission is a map of the chemistry. The
observations can be reproduced by an ad hoc CO formation chemistry in which a fixed relative abundance of HCO [+]
N(HCO [+] )/N(H 2 ) = 3 × 10 [−][9] thermally recombines to CO if
the H 2 formation and shielding of H 2 and CO are treated selfconsistently along with the heating and cooling Liszt (2017).
However, networks of chemical reactions in quiescent gas may
fail to form the observed quantity of HCO [+] and produce too little
CO. This causes the CO brightness to reach 1 K-kms [−][1] at overly
large values of E B−V and N(H 2 ) where shielding of CO by dust
and H 2 make up for the deficit in the CO formation rate (e.g.,
Gong et al. 2018 Figure 7; Hu et al. 2021 Figure 9).
Models with a weak CO formation chemistry have an innate
tendency to overestimate the amount of CO-dark gas, but the actual amount of CO-dark gas depends on the distribution of material. In practice the DNM fraction seen by Remy et al. (2018)
varied from 0 to 0.3 (their Figure 8) and the sightlines sampled
here had <f DNM - = 0.13.


**5.** **Summary**


We took 89.2 GHz ALMA HCO [+] absorption spectra toward 33
compact millimeter-wave extragalactic continuum sources seen
against the Galactic anticenter (Figure 1 and the tables above).


1 f H 2 = 2N(H 2 )/N(H) = 0.4-0.5 at E B−V = 2 mag if N(H)/E B−V = 6 −
8 × 10 [21] mag [−][1]



We also observed J=1-0 CO emission at the IRAM 30m telescope in the 28 anticenter directions where HCO [+] was detected.
Inferring N(H 2 ) from N(HCO [+] ) using the ratio N(HCO [+] )/N(H 2 )
= 3×10 [−][9], we combined these results with those from our earlier
study of 13 directions where HCO [+] absorption was detected in
the outskirts of Chamaeleon. We compared the inferred N(H 2 )
with prior determinations of the column densities of the dark
neutral medium, the neutral gas of uncertain (atomic or molecular) character that had been found to be missing in HI and/or CO
emission when compared with the submillimeter dust and γ-ray
emissivities of large-scale molecular cloud complexes.

Binning the HI, H 2, and DNM column densities in reddening, we showed in Figure 3 that the mean DNM and molecular
gas column densities were comparable and varied compatibly by
factors of 50-100 over the observed range E B−V = 0.09 - 1 mag,
while N(H(I) varied by only factors of 2-3. The means of N(H 2 )
and N(DNM) are small at low mean reddening, and increase in
similar fashion up to E B−V = 0.5 mag where molecular gas begins to dominate and CO emission is strong. N(H 2 ) continues
to increase with higher reddening, but N(DNM) and the column
density of cloud-associated HI fall where H 2 dominates (sequestering hydrogen) and CO emission is stronger and more closely
representative of N(H 2 ).

We made detailed individual sightline-level comparisons of
N(DNM) with E B−V, N(HI), and N(H 2 ) in Figures 4-6. Sightlines
with appreciable DNM appear at all N(HI) (Figure 4); the overall
mean DNM fraction f DNM = N(DNM)/(N(HI)+2N(H 2 )) = 0.12
is modest. Sightlines with appreciable DNM are lacking when
E B−V ∼ [<] 0.15 mag (Figure 5) and when 2N(H 2 ) ∼ [<] 10 [20] cm [−][2]
or 2N(H 2 ) ∼ [>] 10 [21] cm [−][2] (Figure 6). In Figure 6 we compared
N(DNM) and N(H 2 ) in directions lacking detected CO emission
in order to eliminate the case that H 2 was already represented
by CO emission in the DNM analysis. This figure showed that
there were 2-3 sightlines in each subsample (Chamaeleon and
anticenter) or 5-6/46 overall where 2N(H 2 ) <≤ N(DNM)/2 and
H 2 accounted for the minority of the DNM. There are also a few
directions at 2N(H 2 ) ≈ 10 [21] cm [−][2] where 2N(H 2 ) - 2N(DNM).
Overall, the amounts of DNM and H 2 are similar <2N(H 2 )> =
1.3 <N(DNM)> for the unambiguous cases lacking CO emission. The form of the DNM is overwhelmingly molecular hydrogen.
Directions with <W CO  - >1 K-km s [−][1] have two times smaller
mean DNM fractions <f DNM - = 0.06, while sightlines with
<W CO - < 1 K-km s [−][1] have three times higher f DNM ∼ [>] 0.17-0.19
(Table 3). The relatively few sightlines with W CO ≥ 1 K-kms [−][1]
contain two-thirds of the H 2 detected in HCO [+], and detecting
90% of the H 2 would require detecting CO at levels W CO ≈ 0.20.3 K-km s [−][1] .

The CO-H 2 conversion factor falls steadily with increasing
E B−V or W CO in Figure 7. Because the H 2 is concentrated in
the sightlines with W CO ≥ 1 K-km s [−][1], the overall mean COH 2 conversion factors in our work are <N(H 2 )>/<W CO - = 2 −
3 × 10 [20] H 2 cm [−][2] for samples of sightlines with detectable CO
emission. These values are comparable to previously determined
large-scale Galactic averages, and are substantially higher than
the global values determined by the cloud-level analyses quoted
here to derive N(DNM). We ascribed these differences in part to
the present sampling of widely scattered sightlines (i.e., that we
did not do a cloud-level analysis) and perhaps to differences in
the operational definition of the conversion factor, as discussed
in Section 4.1.

Subsequent papers derived from the observations discussed
here will focus on the physics and chemistry of the molecules


Article number, page 7 of 13

**1.0**


**0.5**


**0.0**



A&A proofs: manuscript no. HSL-PMonnier


**1.0**









**0.5**


**0.0**



**0.0** **1.0** **2.0**

**E(B-V) [mag]**



**0.0** **1.0** **2.0**

**E(B-V) [mag]**



Fig. 8. Probability distributions of area, amount of material, and molecular hydrogen with respect to E B−V . Left: Counts (probability density)
scaled to the same area. Right: Cumulative distribution function. N(H 2 ) is calculated using the mean power-law fit N(H 2 ) = 10 [21][.][0973] E B−V [1][.][335]
derived as shown in Figure 7.


Table 1. Line-of-sight properties and new results for HCO [+] and CO



Source RA(J2000) Dec(J2000) l b E B−V [1] 89 GHz flux Υ HCO+ [2] σΥ HCO+ [3] W CO [4] σW CO [5]

hh.mmsss dd.mmsss degrees degrees mag Jy km s [−][1] km s [−][1] K-km s [−][1] K-km s [−][1]



J0203+1134 2.03464 11.34492 149.6826 -47.4992 0.144 0.126 ≤0.263 0.088
J0209+1352 2.09357 13.52045 150.1800 -44.8290 0.094 0.223 0.20 0.050 ≤0.071 0.024

J0211+1051 2.11132 10.51348 152.5781 -47.3674 0.145 0.462 0.76 0.029 0.36 0.025

J0213+1820 2.13105 18.20255 148.7289 -40.4014 0.130 0.093 ≤0.345 0.115
J0231+1322 2.31459 13.22547 157.0917 -42.7380 0.121 0.430 0.14 0.025 ≤0.064 0.021
J0242+1742 2.42243 17.42589 157.0180 -37.7033 0.077 0.227 ≤0.151 0.050
J0252+1718 2.52077 17.18427 159.7420 -36.7885 0.220 0.172 0.25 0.077 ≤0.096 0.032

J0325+2224 3.25368 22.24004 163.6700 -28.0213 0.213 1.162 1.01 0.017 0.94 0.051

J0329+3510 3.29154 35.10060 155.9152 -17.4042 0.267 0.570 0.51 0.032 ≤0.143 0.048
J0329+2756 3.29577 27.56155 160.7030 -23.0743 0.198 0.158 ≤0.193 0.064
J0334+0800 3.34533 8.00144 177.2396 -37.0871 0.391 0.150 0.44 0.088 ≤0.162 0.054
J0336+3218 3.36301 32.18293 158.9998 -18.7650 0.733 1.689 0.16 0.009 ≤0.219 0.073

J0356+2903 3.56085 29.03423 164.6120 -18.4927 0.212 0.139 1.50 0.090 1.62 0.042

J0357+2319 3.57216 23.19538 169.0302 -22.4661 0.185 0.224 0.28 0.027 ≤0.192 0.064
J0400+0550 4.00117 5.50431 184.2710 -33.7266 0.266 0.159 0.25 0.063 ≤0.172 0.057

J0401+0413 4.01199 4.13344 186.0261 -34.4947 0.341 0.405 0.49 0.021 0.19 0.048

J0403+2600 4.03056 26.00015 168.0260 -19.6483 0.201 0.331 0.60 0.029 0.62 0.067

J0406+0637 4.06343 6.37150 184.7075 -32.0009 0.283 0.264 0.54 0.051 0.63 0.040

J0407+0742 4.07291 7.42075 183.8723 -31.1558 0.265 0.387 0.53 0.031 0.19 0.042

J0426+0518 4.26366 5.18199 189.3631 -28.7705 0.291 0.516 0.12 0.020 ≤0.170 0.057

J0426+2327 4.26557 23.27396 173.8881 -17.4457 0.539 0.304 2.57 0.057 4.84 0.045

J0427+0457 4.27476 4.57083 189.8857 -28.7306 0.335 0.414 0.62 0.024 0.39 0.045

J0437+2037 4.31038 20.37343 176.8096 -18.5565 0.532 0.217 1.54 0.073 0.67 0.026

J0431+1731 4.31574 17.31358 179.4942 -20.3579 0.464 0.104 1.01 0.110 0.70 0.049

J0433+0521 4.33111 5.21156 190.3730 -27.3967 0.298 4.911 0.35 0.003 ≤0.109 0.036

J0437+2940 4.37044 29.40138 170.5818 -11.6609 0.979 0.059 5.92 1.138 10.42 0.027

J0438+3004 4.38049 30.04455 170.4116 -11.2283 0.952 0.689 6.25 0.038 7.11 0.026

J0439+3045 4.39178 30.45076 170.0655 -10.5913 0.867 0.195 5.05 0.082 6.69 0.027

J0440+1437 4.40211 14.37570 183.2538 -20.5438 0.681 0.337 1.21 0.031 0.83 0.029

J0445+0715 4.45014 7.15539 190.4535 -23.8898 0.121 0.275 ≤0.083 0.028

J0449+1121 4.49077 11.21286 187.4274 -20.7365 0.504 0.521 0.65 0.022 0.23 0.033

J0502+1338 5.02332 13.38110 187.4143 -16.7456 0.564 0.271 1.81 0.059 2.46 0.031

J0510+1800 5.10024 18.00416 184.7304 -12.7895 0.328 2.411 0.13 0.005 0.17 0.036
1 From Schlegel et al. (1998)
2 −1
Integrated optical depth or 3σ upper limit over a 3 km s interval
3 −1
Integrated emission from our results or 3σ upper limit over a 3 km s interval
4 rms of detected emission or rms over a 3km s −1 interval


Article number, page 8 of 13

L&G: DNM, dark and molecular gas


Table 2. Line-of-sight properties and derived quantities


Source E(B-V) N(HI) [1] N(HI) cl [1] 2N(H 2 ) [2] W CO [3] N(DNM) [1] 2N(H 2 )/N(HI) N(DNM)/N(HI) X CO [4]

mag 10 [21] cm [−][2] 10 [21] cm [−][2] 10 [21] cm [−][2] K-km s [−][1] 10 [21] cm [−][2]

J0203+1134 0.144 0.664 0.646 ≤0.193 0.201 ≤0.290 0.303

J0209+1352 0.094 0.696 0.686 0.144 0.00 0.206 0.00

J0211+1051 0.145 0.618 0.617 0.561 0.240 0.908 0.388

J0213+1820 0.130 0.933 0.911 ≤0.253 0.177 ≤0.271 0.190

J0231+1322 0.121 0.926 0.852 0.103 0.00 0.111 0.00

J0242+1742 0.077 0.820 0.819 ≤0.111 0.00 ≤0.135 0.00

J0252+1718 0.220 1.142 1.139 0.184 0.299 0.161 0.262

J0325+2224 0.213 0.999 0.926 0.742 2.82 0.180 0.743 0.180 1.314

J0329+3510 0.267 1.418 1.131 0.372 0.150 0.263 0.106

J0329+2756 0.198 1.129 1.002 ≤0.142 ≤ 1.97 0.00 ≤0.126 0.00

J0334+0800 0.391 1.893 1.855 0.322 0.223 0.170 0.118

J0336+3218 0.733 1.435 1.165 0.119 ≤2.60 0.606 0.082 0.423

J0356+2903 0.212 0.666 0.520 1.099 1.40 0.178 1.650 0.267 3.931

J0357+2319 0.185 1.022 0.944 0.205 ≤0.79 0.00 0.200 0.00

J0400+0550 0.266 1.266 1.210 0.182 0.238 0.144 0.188

J0401+0413 0.341 1.209 1.202 0.357 0.426 0.296 0.352

J0403+2600 0.201 0.830 0.667 0.438 1.99 0.00 0.528 0.00 1.101

J0406+0637 0.283 1.182 1.143 0.397 0.266 0.335 0.225

J0407+0742 0.265 1.033 1.006 0.387 0.258 0.374 0.250

J0426+0518 0.291 1.305 1.141 0.091 ≤1.40 0.414 0.070 0.317

J0426+2327 0.539 1.586 1.331 1.887 5.78 0.00 1.190 0.00 1.632

J0427+0457 0.335 1.361 1.192 0.457 2.49 0.590 0.336 0.433 0.918

J0437+2037 0.532 2.324 1.992 1.130 ≤1.61 0.00 0.486 0.00

J0431+1731 0.464 1.714 1.457 0.739 3.09 0.00 0.431 0.00 1.198

J0433+0521 0.298 1.159 0.950 0.255 ≤1.48 0.795 0.220 0.686

J0437+2940 0.979 1.320 0.936 4.345 11.98 0.126 3.292 0.095 1.814

J0438+3004 0.952 2.019 1.002 4.586 7.70 0.771 2.271 0.382 2.979

J0439+3045 0.867 2.361 0.745 3.701 9.42 0.00 1.567 0.00 1.964

J0440+1437 0.681 1.659 1.524 0.888 ≤1.97 1.230 0.535 0.741
J0445+0715 0.121 1.044 0.915 ≤0.061 0.00 ≤0.058 0.00

J0449+1121 0.504 1.416 1.347 0.476 0.791 0.336 0.558

J0502+1338 0.564 2.188 1.957 1.324 ≤1.90 0.672 0.605 0.307
J0510+1800 0.328 2.347 1.986 0.092 ≤2.00 0.00 0.039 0.00

J0942-7731 0.336 1.000 0.617 0.837 ≤1.50 0.382 0.838 0.382

J1058-8003 0.152 0.651 0.470 0.147 “ 0.371 0.226 0.570

J1136-6827 0.460 2.407 0.915 0.910 “ 0.172 0.378 0.071

J1145-6954 0.387 1.925 0.998 0.638 “ 0.223 0.331 0.116

J1147-7935 0.300 2.506 0.773 0.040 “ 0.00 0.016 0.00

J1152-8344 0.283 1.088 0.505 0.176 “ 0.515 0.162 0.473

J1224-8313 0.257 0.962 0.563 0.693 “ 0.335 0.720 0.348

J1254-7138 0.282 1.902 0.660 0.102 “ 0.00 0.053 0.00

J1312-7724 0.476 1.257 0.671 0.199 “ 0.396 0.158 0.315

J1550-8258 0.107 0.679 0.416 0.177 “ 0.027 0.261 0.039

J1617-7717 0.091 0.659 0.431 0.043 “ 0.045 0.065 0.068

J1723-7713 0.255 0.834 0.500 1.105 2.40 0.195 1.325 0.234 2.302

J1733-7935 0.139 0.792 0.525 0.041 ≤ 1.50 0.00 0.052 0.00
1 HI and DNM column densities are from Planck Collaboration et al. (2015) and Remy et al. (2017, 2018)
2 + −9
N(H 2 ) = N(HCO )/3 × 10

3 Integrated J=1-0 CO emission used by Planck Collaboration et al. (2015) and Remy et al. (2017, 2018)
4 X CO = N(H 2 )/W CO



observed in the course of this work, chiefly HCO [+], C 2 H, and
HCN.


Acknowledgements. The National Radio Astronomy Observatory (NRAO) is a
facility of the National Science Foundation, operated by Associated Universities, Inc. This work was supported by the French program “Physique et Chimie
du Milieu Interstellaire” (PCMI) funded by the Conseil National de la Recherche
Scientifique (CNRS) and Centre National d’Etudes Spatiales (CNES). This work
is based in part on observations carried out under project number 003-19 with
the IRAM 30m telescope]. IRAM is supported by INSU/CNRS (France), MPG
(Germany) and IGN (Spain). This paper makes use of the following ALMA data
– ADS/JAO.ALMA#2016.1.00714.S


– ADS/JAO.ALMA#2018.1.00115.S ALMA is a partnership of ESO (repre

senting its member states), NSF (USA) and NINS (Japan), together with NRC
(Canada), NSC and ASIAA (Taiwan), and KASI (Republic of Korea), in coop


eration with the Republic of Chile. The Joint ALMA Observatory is operated
by ESO, AUI/NRAO and NAOJ. We thank Isabelle Grenier for providing results of the DNM analysis and we thank the anonymous referee for many helpful
remarks. HSL is grateful for the hospitality of the ITU-R and the Hotel de la
Cigogne in Geneva during the completion of this manuscript.


**References**


Cotten, D. L. & Magnani, L. 2013, MN, 436, 1152
Donate, E. & Magnani, L. 2017, MNRAS, 436, 1152
Goldreich, P. & Kwan, J. 1974, ApJ, 189, 441
Gong, M., Ostriker, E. C., & Kim, C.-G. 2018, ApJ, 858, 16
Grenier, I. A., Casandjian, J.-M., & Terrier, R. 2005, Science, 307, 1292
Hu, C.-Y., Sternberg, A., & van Dishoeck, E. F. 2021, ApJ, 920, 44


Article number, page 9 of 13

A&A proofs: manuscript no. HSL-PMonnier


Table 3. Mean line-of-sight properties and derived quantities


Sample E(B-V) N(HI) N(HI) cl 2N(H 2 ) W CO N(DNM) f H 2 f DNM X CO
mag 10 [21] cm [−][2] 10 [21] cm [−][2] 10 [21] cm [−][2] K-km s [−][1] 10 [21] cm [−][2]

Galactic anticenter 0.362 1.324 1.119 0.798 5.185 0.268 0.38 0.13 1.93

# 33 33 33 33 9 33 33 33 9

Chamaeleon 0.271 1.282 0.619 0.393 2.400 0.205 0.23 0.12 2.30

# 13 13 13 13 1 13 13 13 1

All LOS 0.336 1.312 0.977 0.684 4.906 0.250 0.34 0.13 1.95

# 46 46 46 46 10 46 46 46 10

E B−V ≤ 0.2mag 0.131 0.818 0.710 0.168 0.082 0.18 0.08
# 13 13 13 13 13 13 13
Lacking HCO [+][1] 0.134 0.918 0.859 ≤0.152 0.076 ≤0.14 ≥0.08
# 5 5 5 5 5 5 5
DNM ≤ 10 [20] cm [−][2] 0.273 1.373 0.953 0.539 5.070 0.004 0.28 0.00 1.67

# 17 17 17 17 4 17 17 17 4
CO detected earlier [2] 0.502 1.369 0.928 1.910 4.906 0.204 0.58 0.06 1.95

# 10 10 10 10 10 10 10 10 10

30m CO detected 0.467 1.491 1.197 1.312 2.170 0.318 0.47 0.11 3.02

# 18 18 18 18 18 18 18 18 18
30m W CO >1K-km s [−][1] 0.685 1.690 1.082 2.824 5.522 0.291 0.63 0.06 2.56
# 6 6 6 6 6 6 6 6 6
30m W CO ≤1K-km s [−][1] 0.358 1.391 1.255 0.555 0.494 0.332 0.29 0.17 5.62
# 12 12 12 12 12 12 12 12 12
30m UL ≤1K-km s [−][1] 0.287 1.226 1.107 0.198 <0.140 0.273 0.14 0.19 >7.07

# 10 10 10 10 10 10 10 10 10
Sample E(B-V) N(HI) N(HI) cl 2N(H 2 ) W CO N(DNM) f H 2 f DNM X CO
mag 10 [21] cm [−][2] 10 [21] cm [−][2] 10 [21] cm [−][2] 10 [21] cm [−][2]


1
Limits in this table use 3σ upper limits on undetected quantities
2 All sightlines detected earlier in CO had W CO >1K-km s −1


Liszt, H. 1997, A&ASS, 124, 183
—. 2021, ApJ, 908, 127
Liszt, H. & Gerin, M. 2023, ApJ, 943, 172
Liszt, H., Gerin, M., & Grenier, I. 2018, A&A, 617, A54
—. 2019, A&A, 627, A95
Liszt, H. S. 2007, A&A, 476, 291
—. 2017, ApJ, 835, 138
Magnani, L., Onello, J. S., Adams, N. G., Hartmann, D., & Thaddeus, P. 1998,
ApJ, 504, 290
Planck Collaboration, Abergel, A., Ade, P. A. R., Aghanim, N., Alves,
M. I. R., Aniano, G., Armitage-Caplan, C., Arnaud, M., Ashdown, M., AtrioBarandela, F., & et al. 2014, A&A, 571, A11
Planck Collaboration, Fermi Collaboration, Ade, P. A. R., Aghanim, N., Aniano,
G., Arnaud, M., & Ashdown, M. 2015, A&A, 582, A31
Remy, Q., Grenier, I. A., Marshall, D. J., & Casandjian, J. M. 2017, A&A, 601,
A78

—. 2018, A&A, 611, A51
Schlegel, D. J., Finkbeiner, D. P., & Davis, M. 1998, ApJ, 500, 525
Wolfire, M. G., Hollenbach, D., & McKee, C. F. 2010, ApJ, 716, 1191


Article number, page 10 of 13

L&G: DNM, dark and molecular gas



**6**





**4**


**2**


**0**


**0.00** **0.02** **0.04** **0.06** **0.08** **0.10** **0.12**

∆Υ **HCO+ [km s** **[-1]** **]**


Fig. A.1. Integrated HCO [+] optical depth Υ HCO + plotted against its rms
error. The upper limits along five sightlines not detected in HCO [+] are
3σ.


**Appendix A:** **Statistics of HCO** [+] **detections**


HCO [+] absorption was not detected in five directions, all in the
Galactic anticenter sample. Figure A.1 shows Υ HCO [+] plotted
against its rms error ∆Υ HCO +, in essence against the strength
of the continuum background since all sightlines were observed
for the same length of time. The plot shows that even the noisiest sightlines miss relatively small amounts of molecular gas.
The bias in the plot, whereby <Υ HCO + - increases with ∆Υ HCO +,
was to some extent built into the observing to increase the yield.
That is, the source selection began with flux-limited samples that
would achieve a minimum signal-to-noise ratio on the weakest
source, and added 50% additional targets at lower flux S ν and
higher E B−V /S ν that could be serendipitously observed without a
proportionate increase in the required observing time.


**Appendix B:** **Spectra of HCO** [+] **and CO**


Spectra of HCO [+] absorption and CO emission in the 28 directions with detected HCO [+] absorption are shown in Figure B.1.
The HCO [+] absorption is the negative-going signal shown in red.
The black histogram shows the CO emission. The frequencyswitched IRAM 30m CO spectra were delivered only after folding in frequency, preventing a separation of the phases of the
frequency-switching cycle using the methods of Liszt (1997).
Negative-going features in the CO spectrum are artifacts; only
the positive-going CO signal coincident with HCO [+] absorption
is interstellar.


**Appendix C:** **Area used to derive large-scale**
**statistics**


To derive the statistical distributions shown in Figure 8 and discussed in Section 4.4, we drew a hull around the observed sightlines as illustrated in Figure C.1 and summed over the interior
pixels.



Article number, page 11 of 13

A&A proofs: manuscript no. HSL-PMonnier



**2**


**1**


**0**


**-1**


**2**


**1**


**0**


**-1**


**2**


**1**


**0**


**-1**


**2**


**1**


**0**


**-1**


**2**


**1**


**0**


**-1**


**2**


**1**


**0**


**-1**


**2**


**1**


**0**


**-1**



**J0209+1352**


**-20** **0**


**J0325+2224**


**-20** **0**


**J0356+2903**


**-20** **0**


**J0403+2600**


**-20** **0**


**J0426+2327**


**-20** **0**


**J0433+0521**


**-20** **0**


**J0440+1437**


**-20** **0**



**J0211+1051**


**-20** **0**


**J0329+3510**


**-20** **0**


**J0357+2319**


**-20** **0**


**J0406+0637**


**-20** **0**


**J0427+0457**


**-20** **0**


**J0437+2940**


**-20** **0**


**J0449+1121**


**-20** **0**



**J0231+1322**


**-20** **0**


**J0334+0800**


**-20** **0**


**J0400+0550**


**-20** **0**


**J0407+0742**


**-20** **0**


**J0431+2037**


**-20** **0**


**J0438+3004**


**-20** **0**


**J0502+1338**


**-20** **0**



**J0252+1718**


**-20** **0**


**J0336+3218**


**-20** **0**


**J0401+0413**


**-20** **0**


**J0426+0518**


**-20** **0**


**J0431+1731**


**-20** **0**


**J0439+3045**


**-20** **0**


**J0510+1800**


**-20** **0**



**Vlsr [km s** **[-1]** **]**


Fig. B.1. Spectra of HCO [+] absorption (red) and CO emission (black) from the Galactic anticenter sample. For an explanation of the appearance of
the frequency-switched IRAM 30m emission spectra, see Appendix B.


Article number, page 12 of 13

L&G: DNM, dark and molecular gas


~~**1**~~


**-10**


**-20**


**-30**


**-40**


**-50**

~~**0**~~
**190** **180** **170** **160** **150** **140**

**GALACTIC LONGITUDE [degrees]**


Fig. C.1. As in Figure 1, left, but showing the outlines of an area containing the observed sightlines used to derive large-scale properties of
the anticenter region (see Section 4.3).



Article number, page 13 of 13


</paper>

## Items to check

```json
[
 {
  "path": "data.external_data_from_literature[0].what.evidence[0]",
  "value": "N(DNM), 21cm HI column densities N(HI) and N(HI)_cl, and prior J=1-0 CO emission W_CO",
  "failed_quote": "From the existing DNM analyses of Planck Collaboration et al. (2015) and Remy et al. (2017, 2018) we take N(DNM) and Ł21 HI column densities N(HI) and N(HI) cl"
 },
 {
  "path": "analysis_steps[3].method.evidence[1]",
  "value": "Combine the 33 anticenter sightlines with 13 Chamaeleon sightlines, bin quantities in 0.05 mag intervals of E_B-V, fit power-law N(H2)-E_B-V relation, and compute pixel-by-pixel cumulative distributions inside a regional hull",
  "failed_quote": "We drew a hull around the observed anticenter sightlines, as shown in Figure C.1 and derived the pixel-by-pixel statistics for the contained area, the amount of material (taken proportional to E B−V ), and the amount of H 2 . For H 2 we used the N(H 2 )-E B−V relationship N(H 2 ) = 10 [21][.][0973] E B−V [1][.][335]"
 },
 {
  "path": "analysis_steps[3].assumptions[0].evidence[0]",
  "value": "Amount of material proportional to E_B-V and N(H2) = 10^21.0973 * E_B-V^1.335",
  "failed_quote": "We drew a hull around the observed anticenter sightlines, as shown in Figure C.1 and derived the pixel-by-pixel statistics for the contained area, the amount of material (taken proportional to E B−V ), and the amount of H 2 . For H 2 we used the N(H 2 )-E B−V relationship N(H 2 ) = 10 [21][.][0973] E B−V [1][.][335]"
 }
]
```
