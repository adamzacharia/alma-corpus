# Repair task for a Claude Code subagent

A methods card has evidence quotes that were not found verbatim in the paper. Below are the rules, the paper, and the failing items. Write ONE JSON object, nothing else, of the form {"repairs": [{"path": ..., "found": true|false, "loc": ..., "quote": ...}, ...]} with one entry per item (path unchanged) to:

    C:\Users\adama\alma-corpus\cards\2025A%26A...699A..17L\gemini4argon\repair_reply.txt

Use the Write tool for that file. Copy each quote character for character from the paper text below; a returned quote is checked mechanically and dropped if it is not in the paper. Do not read any other file, do not run commands, and do not change anything else. Reply with one line when done.

---

## Rules

You check evidence quotes for a methods card extracted from an astronomy paper. Some quotes could not be found verbatim in the paper text, and some stated values came without a quote. For each item: find the passage in the paper that supports the value and copy it VERBATIM (same words and order, at most 40 words; LaTeX markup may be dropped) with its loc (section heading, "abstract", "Table N" or "Figure N caption"). If the paper does not support the value, return found = false and leave quote and loc empty. Use only the paper text. Return one entry per item, with the item's path unchanged.

## Paper

<paper>
Astronomy & Astrophysics manuscript no. aa53182-24corr © ESO 2025
June 17, 2025

## CO, CS, HCO, HCO [+], C 2 H, and HCN in the diffuse interstellar **medium**


H. Liszt [1] and M. Gerin [2]


1 National Radio Astronomy Observatory, 520 Edgemont Road, Charlottesville, VA, USA 22903 e-mail: hliszt@nrao.edu
2 LERMA, Observatoire de Paris, PSL Research University CNRS Sorbonne Universit´e
e-mail: maryvonne.gerin@observatoiredeparis.psl.eu


received June 17, 2025


**ABSTRACT**


Context. Radio frequency molecular absorption lines appear along sight lines with A V well below 1 mag, revealing the presence of H 2 in
diffuse gas even when λ2.6mm CO emission is absent.
Aims. We discuss absorption lines of HCO [+], C 2 H, HCN, CS, and HCO in a larger sample (88 sight lines) than was available before.
Methods. We observed millimeter-wave absorption at the Institut de radioastronomie millimetrique (IRAM) and Atacama Large
Millimeter/submillimeter (ALMA) interferometers over the past 30 years and gathered the results for to compare with observations of
HCO [+] and CO emission taken at the Arizona Radio Observatory (ARO) KP12m and IRAM 30m telescopes.
Results. We detected HCO [+] along 72 of 86 sight lines where it was observed, C 2 H along 53 of 76 sight lines, and HCN along 38 of 57 sight
lines. C 2 H is ubiquitous, and N(C 2 H)/N(HCO [+] ) increases at smaller E B−V and smaller N(HCO [+] ), but C 2 H absorption is intrinsically weaker,
which lowers the number of sight lines with a low column density along which it was detected. The dense-gas tracer HCN was uniformly
detected down to N(H 2 ) = 10 [20] cm [−][2], with little change in the relative abundance of N(HCN)/N(HCO [+] ) ≈ 1.25. HCO was detected along
only 4 of 46 sight lines that were newly observed at ALMA because its lines are intrinsically weak, but HCO is ubiquitous in the interstellar
medium with N(HCO)/N(HCO [+] ) = 1/3 or N(HCO)/N(H 2 ) = 10 [−][9] . CS was not seen in the 13 directions where it was newly observed, which
are all in Chamaeleon. The line widths of HCN features are (like those of CO) narrower than those of matching features observed in HCO [+],
and those of C 2 H are broader. HCO [+] emission is commonly observed at (log) levels −2 ± 0.3 dex with respect to CO emission. The comparison
of HCO [+] emission and absorption along 7 sight lines yielded a typical HCO [+] excitation temperature of 2.76 K and total neutral hydrogen
number densities n(H) of ≈ 50 − 200 cm [−][3] .


**Key** **words.** Astrochemistry; Galaxy: disk; ISM: abundances; ISM: atoms; ISM: clouds; ISM: dust, extinction; ISM: molecules; Line: profiles;Molecular processes



**1.** **Introduction**


In several recent papers (Liszt et al., 2018, 2019; Liszt & Gerin,
2023b), we used the Atacama Large Millimeter/Submillimeter
Array (ALMA) observations of millimeter-wave HCO [+] and
CO absorption to demonstrate the molecular character of the
dark neutral medium (DNM) that is present at the HI-H 2 transition in diffuse or translucent interstellar gas (Grenier et al.,
2005; Planck Collaboration et al., et al. 2015; Remy et al.,
2017, 2018). Gas in the DNM is inferred to be present from
far-infrared (FIR) dust emission and γ-ray emission but is imperfectly traced and largely invisible in λ21cm HI and λ2.6mm
CO emission. In our work, sight lines with a low CO column
density that lack detectable CO emission showed HCO [+] absorption when the reddening exceeded the known threshold


Send offprint requests to: H. S. Liszt
Correspondence to: hliszt@nrao.edu



E B−V ∼ [>] 0.08 mag (Savage et al., 1977; Liszt & Gerin, 2023a)
for observing H 2 fractions f H 2 = 2N(H 2 )/(N(HI)+2N(H 2 )) =
2N(H 2 )/N(H)∼ [>] 0.1. With a few exceptions that imply a possible saturation of the λ21cm HI profile, the newly inferred H 2
column densities N(H 2 ) = N(HCO [+] )/3 × 10 [−][9] closely matched
the amount of DNM.


In the course of these observations along 13 sight lines in
Chamaeleon and 33 sight lines in the Galactic anticenter, we
also used the prodigious data-gathering abilities of ALMA to
observe absorption from other species that were previously detected in diffuse gas, C 2 H (Lucas & Liszt, 2000; Liszt et al.,
2012), HCN (Liszt & Lucas, 2001), CS (Lucas & Liszt, 2002),
HCO (Liszt et al., 2014), and H 2 CO (Nash, 1990; Lucas &
Liszt, 1996; Liszt et al., 2006). We discuss these associated observations here. In combination with ALMA observations of 4

sight lines at low latitude in the inner Galaxy (Gerin & Liszt,
2017; Liszt & Gerin, 2018) and the previously published ab

2 L&G: DNM, dark and molecular gas



sorption data from the IRAM 30m telescope and Plateau de
Bure Interferometer (PdBI), we discuss observations along 86
sight lines in the most commonly observed species HCO [+], 76
in C 2 H and 57 in HCN. HCO is a ubiquitous species with weak
absorption (Liszt et al., 2014) that was detected along all 4 of
the 46 sight lines at which it was expected based on the ac
achieved rms noise levels.


Far fewer (25) sight lines were observed in total in CS after
our failure to detect CS absorption along the 13 sight lines in
Chamaeleon within the integration times that sufficed to detect
HCO [+] and C 2 H. No new detections of CS are presented here,
and, as discussed below, the new upper limits on CS are not
significant because the molecular hydrogen column densities
that characterize the observed sight lines are low. A comparison of absorption line observations of CS and H 2 CO toward
B0355+508 recently showed that the relative abundance of CS
increases in presumably denser gas with a smaller electron fraction, where a substantial fraction of ionized carbon has recombined to neutral atomic carbon (Gerin et al., 2024). This suggests a role of neutral carbon in the formation of CS along with
recombination of HCS [+] that was also inferred (Lucas & Liszt,
2002). CS J=2-1 emission from diffuse gas is bimodal with respect to HCO [+] emission and abruptly increases in brightness
when the integrated brightness of CO exceeds 10 K-kms [−][1]

(Liszt, 2020).


Section 2 summarizes the observational material we con
sidered. Section 3 discusses the properties of the sample in the
broader Galactic context and summarizes the abundance relations among HCO [+], C 2 H, HCN, CS, and HCO. Section 4 compares the line widths of Gaussian kinematic components fit to
HCO [+], C 2 H and HCN. In Section 5 we use the HCO [+] and CO
emission to derive HCO [+] excitation temperatures and hydrogen number densities in the host gas and to relate the H 2 sampled in HCO [+] absorption to the CO emission brightness, the
12 CO/ 13 CO brightness ratio, and the CO-H 2 conversion factor.
These quantities are commonly used to characterize the gas.
Section 6 presents our summary.


**2.** **Observations and data sources**


The dataset we discuss here is a combination of older and

newer observations, as noted in Table A.1. The older absorption
line work is from the IRAM PdBI and NOEMA interferome
ters, and the older CO and HCO [+] emission line profiles were
taken at the previous-generation ARO 12m telescope on Kitt
Peak. The newer observations of the absorption line were taken
at ALMA, and the newer CO and HCO [+] emission profiles were
taken at the IRAM 30m telescope. The older data and some of
the newer data have been described in earlier work cited here.

The portions of the current dataset that have not been published
previously are the 87-98 GHz ALMA absorption profiles of
HCO, HCN, C 2 H and CS, and the profiles of [13] CO and HCO [+]

emission that were taken in the course of our recent work to

characterize the DNM, as noted in the Introduction.



2.1. Absorption line spectra


As in our earlier work, the new ALMA absorption line profiles
were taken from the continuum-peak pixels of the spectral line
datacubes from the standard pipeline product for the various
species, and they were normalized by the continuum flux in the
appropriate continuum map of the spectral window. The channel spacing and approximate spectral resolution of the ALMA
data were 30.5 and 61.0 kHz, or 0.102 and 0.205 km s [−][1] respectively, at the HCO [+] rest frequency 89.1885 GHz. All directions in the Galactic anticenter were observed for the same

time, which resulted in strongly varying rms line/continuum
sensitivities.


We newly observed the F=2-1 and F=1-0 hyperfine components of the N=1-0, J=3/2-1/2 transition of C 2 H whose
strongest hyperfine component (F=2-1) is at 87.317 GHz. The
observed components included 5/8 of the total integrated line
strength of the N=1-0 J=3/2-1/2 transition. We define the total
as Υ CCH . N(C 2 H) = 2.71 × 10 [13] cm [−][2] Υ CCH as in our earlier survey of C 2 H absorption (Lucas & Liszt, 2000), where all hyperfine components were observed. The spectra of C 2 H are shown
in Figure C.1.


As in earlier work (Liszt & Lucas, 2001), we observed the
J=1-0 transition of HCN, whose strongest hyperfine component is at 88.632 GHz, and we derived N(HCN) = 1.89 ×
10 [12] cm [−][2] Υ HCN where Υ HCN is the integrated optical depth
summed over all three hyperfine components. The spectra of
HCN are shown in Figure D.1.


The line-of-sight properties and measured absorption line
quantities are given in Table B.1 for HCO [+], HCN, and C 2 H.
The fluxes in this table are averages of the almost equal fluxes
in the three spectral windows. Upper limits are the 3σ values measured over the span of the HCO [+] line, when given.
In the five cases when HCO [+] was not observed or not detected, they are given over an arbitrary 3 km s [−][1] interval. No
absorption from CS was reliably detected in our observations of
Chamaeleon. We therefore did not observe CS in the Galactic

anticenter.


2.2. Emission line spectra


The IRAM 30m emission profiles have a channel spacing and
approximate spectral resolution of 48.8 and 97.7 kHz, or 0.164
and 0.33 km s [−][1] at the HCO [+] rest frequency.


The HCO [+] profiles we show are averages of spectra displaced by 1.2 HPBW = 30 [′′] from the continuum source in
each of the four cardinal directions, as discussed in Section F.
This was necessary because the emitted and absorbed fluxes are
comparable, and no pure emission spectrum was obtained toward the continuum at the 30m telescope. This is not a concern
for much brighter CO lines.


As before, the emission results are presented on the mainbeam antenna temperature scale that is native to the 30m tele
scope.

L&G: DNM, dark and molecular gas 3



**10**


**1**


**0.1**


**0.01**


**10** **[22]**


**10** **[21]**


**10** **[20]**



1 [o] 2 [o] 5 [o] 10 [o] 15 [o] 30 [o] 60 [o]



1 [o] 2 [o] 5 [o] 10 [o] 15 [o] 30 [o] 60 [o]



sightlines with upper limits on HCO [+]

Galactic average



sightlines with upper limits on HCO [+]

Galactic average



3σ upper limit on HCO [+]
N(H2)=N(HCO [+] )/3x10 [-9]


**0.01** **0.1** **1**

**sin(|b|)**



**10** **[22]**


**10** **[21]**


**10** **[20]**


**10**


**1**


**0.1**



3σ upper limit on WCO


**0.01** **0.1** **1**

**sin(|b|)**



Fig. 1. Galactic-scale properties of the sample. We plot against sin(|b|) E B−V (top left), N(HI) (top right), N(H 2 ) = N(HCO [+] )/3 × 10 [−][9] (bottom
left), and W CO, the line profile integral of the CO J=1-0 emission. The sight lines that were not detected in HCO [+] absorption are shown as
smaller green symbols in the upper two panels. The smaller green symbols in the lower panels are the 3σ upper limits on the plotted quantity.
The solid line in each panel is a regression line: A plane-parallel vertically stratified Galactic gas layer would exhibit a power-law slope of -1.
We also show averages at intervals of 0.01 in sin(|b|) in blue at the top. A legend marking the values of the Galactic latitude is inset near the top
of the upper two panels. The values for the statistical parameters and the regression fits are given in Table 1.



2.3. Atomic and molecular hydrogen column densities


The λ21cm HI column densities were derived from the Leiden,
Argentine, and Bonn (LAB) All-Sky HI survey Kalberla et al.
(et al. 2005) in the optically thin limit as N(HI) = 1.823 ×
10 [18] cm [−][2] W HI, where W HI is the λ21cm HI emission line profile integral in units of K-km s [−][1] .
As is common practice (see Gerin et al. (et al. 2019)), we
derived the H 2 column densities as N(H 2 ) = N(HCO [+] )/3 × 10 [−][9]

and N(HCO [+] ) = 1.10 × 10 [12] cm [−][2] Υ HCO+ where Υ HCO+ is the
integrated optical depth of the J=1-0 HCO [+] absorption line,
which corresponds to a permanent dipole moment of µ = 3.89
Debye for HCO [+] . Much of our earlier work (eg Lucas & Liszt
(1996)) employed a higher permanent dipole moment of µ =



4.07 Debye and derived ≈ 10% lower N(HCO [+] ) for a given
Υ HCO+ .


2.4. Conventions


The velocities we presen with the spectra were taken with
respect to the kinematic definition of the local standard of
rest. We defined N(H) as the column density of H nuclei
detected in their neutral atomic and molecular form, N(H)
= N(HI)+2N(H 2 ). The molecular hydrogen fraction f H 2 =
2N(H 2 )/N(H). The integrated absorption of the HCO [+] profile
in units of km s [−][1] is denoted by Υ HCO+ and similarly for other
species. The integrated emission of the J=1-0 CO line is de

4 L&G: DNM, dark and molecular gas



noted by W CO in units of K-kms [−][1], and the CO-H 2 conversion
factor N(H 2 )/W CO is denoted by X CO .
Where reference is made to a typical Galactic or standard CO-H 2 conversion factor, the value N(H 2 )/W CO = 2 ×
10 [20] cm [−][2] /(1 K-kms [−][1] ) should be understood, as summarized
in Table E.1 of Remy et al. (2017). Where we refer to optical reddening, the values cited were taken from the work of
Schlegel et al. (1998).

Where the contributions of individual datasets are noted in

the figures, the rubric PdBI denotes results taken from the earlier surveys of HCO [+] (Lucas & Liszt, 1996), C 2 H (Lucas &
Liszt, 2000), HCN Liszt & Lucas (2001), and CS (Lucas &
Liszt, 2002). The rubric Chamaeleon refers to new data taken
incidental to the DNM studies of Liszt et al. (2018, 2019), and
Inner Galaxy refers to the data of Gerin & Liszt (2017) and
Liszt & Gerin (2018). New results incidental to DNM studies
in the Galactic anticenter (Liszt & Gerin, 2023b) use the rubric
Outer Galaxy.


2.5. Distances and velocity assignments


Approximate cloud distances derived from the GAIA stellar
reddening surveys are available for sight lines in or near wellknown cloud complexes that have been specifically targeted,
for instance, 180 - 200 pc in Chamaeleon (Voirin et al., 2018;
Yan et al., et al. 2019; Zucker et al., et al. 2019) and 140 pc in
Taurus (Yan et al., et al. 2019; Zucker et al., et al. 2019). There
are two isolated sight lines (Liszt & Pety, 2012; Liszt, 2020)
in the general vicinity of the high-latitude cloud MBM 53 at
250 pc (Sun et al., 2021), and the gas toward BL Lac is a few
degrees away from the Lacerta region identified at 500 pc by
Yan et al. (et al. 2019); Zucker et al. (et al. 2019).
The 3D extinction maps of Lallement et al. (2022) show the
run of extinction with distance along our specific sight lines.
The relatively large jumps in extinction associated with molecular gas uniquely associate dust structures with the absorption
line velocity in the simpler cases, even in the absence of CO
emission. Conversely, structure in the run of extinction with
distance may help us to understand kinematic substructure in
the absorption line profiles. This subject will be discussed in a
future contribution.


**3.** **The sample**


The sample is an amalgamation of datasets that were taken over
the course of nearly 30 years for various purposes, at instruments that overlap only partially in their sky coverage. The
PdBI surveys of HCO [+] (Lucas & Liszt, 1996) and C 2 H (Lucas
& Liszt, 2000) contained flux-limited samples that were augmented with a few sources of particular interest, as viewed from
the perspective of the Northern Hemisphere, and the PdBI data
for HCN and CS were much more limited. The ALMA data

in Chamaeleon were complete in flux over a very particular
sky region. The newer ALMA data in the outer Galaxy were
derived from a serendipitous sample of sight lines that were
previously studied to derive their DNM content. The properties
and biases of the sample are discussed in this section.



3.1. Galactic-scale properties


Figure 1 shows the galactic-scale properties of our sample. The
gas and dust column densities are plotted against sin(|b|), which
is proportional to the nominal path length through a planeparallel stratified Galactic disk. The numerical values derived
from these plots are given in Table 1. In the top left corner
in Figure 1, the reddening E B−V along individual sight lines
(Schlegel et al., 1998) is plotted, together with the all-sky average at each latitude calculated at increments of ∆ sin(|b|) =
0.01. The regression line for the sample has a power-law slope
of −1.00 ± 0.08, which is appropriate for a plane-parallel stratified medium, but the Galaxy per se progressively departs from
this geometry for |b| ∼ [>] 20 [◦] . The sample values of E B−V lie
above the Galactic average at all latitudes and do not show the
same steep decline until |b| ∼ [>] 44 [o] . Thus, the sample is noticeably rich in dust and gas. We also mark the sight lines without
HCO [+] detections. These sight lines track the Galactic average
more closely and mostly lie below the regression line.


Figure 1 in the top right corner shows a similar plot for
the HI profile integral converted into column density N(HI), as
described in Section 2.3. In this plot, the sample mean N(HI)
follows the Galactic average for |b| ∼ [<] 15 [◦] and departs less from
the Galactic average up to about 30 [◦] than E B−V . When the departure of the sample from the Galactic average is smaller in
N(HI) than in E B−V, the sample is likely to be rich in molecular gas. In contrast to the behavior of E B−V, the sample sight
lines without a detection of HCO [+] have typical sample values
of N(HI) up to very high latitudes, where the sample values of
E B−V decrease. It is tempting to identify the missing E B−V with
the absent H 2 .


Figure 1 shows the Galactic-scale distribution of two quantities measured in this study in the bottom panel, N(H 2 ) =
N(HCO [+] )/3 × 10 [−][9] at the left (where the upper limits on HCO [+]

were included in the calculation of the regression line at their
displayed values), and W CO at the right. The HCO [+] column
density and CO emission brightness show more scatter owing
to the sensitivity of the H 2 and CO formation to local gas properties. The sight lines without a HCO [+] detections fall well below the regression line at the left, but are well mixed in the general data population. In any case, HCO [+] was not detected along
any sight line above 44 [◦], corresponding to sin(44 [◦] ) = 0.7.


Figure 1 shows in the bottom right panel the data for the
line profile integral of CO emission W CO . In this plot, the upper limits on CO emission fall far below the weakest detections.
This differs from the plot in the bottom left panel, where the upper limits on the HCO [+] absorption are at levels at which HCO [+]

is commonly detected. We generally failed to observe any CO
emission at levels W CO ∼ [<] 0.2 K-kms [−][1] . No CO emission was
detected along sight lines without a detection of HCO [+] . The
sight lines without CO emission when HCO [+] absorption is detected are possibly more interesting.


The results in Figure 1 indirectly show that the molecular
fraction of the diffuse gas is substantial (1/4-1/3),the applicable
CO-H 2 conversion factor is near the standard Galactic value
(Section 2.4), and even very low levels of CO emission can
imply significant molecular fractions in the ISM.

L&G: DNM, dark and molecular gas 5



The HI column through the Galactic disk vertically at the
solar radius is usually quoted as N(HI) ≈ 3 × 10 [20] cm [−][2], which
is slightly below the 90 [o] intercept of the regression line for
N(HI) in the upper right panel in Figure 1, ≈ 4 × 10 [20] cm [−][2] . By
comparison, the 90 [o] intercept of the regression line for N(H 2 )
in the lower left panel is N(H 2 ) ≈ 0.6 × 10 [20] cm [−][2], implying f H 2
= 2N(H 2 )/(N(HI)+2N(H 2 )) ≈ 1/4-1/3.


The vertical intercept of the regression line in the lower left
panel is at W CO = 0.245 K-km s [−][1], compared to W CO = 0.235
K-kms [−][1] derived from the smaller sample of older data cited
here (Liszt et al., 2010). In comparison with the result in the
lower left panel for H 2, the implied CO-H 2 conversion factor
is 0.63 × 10 [20] cm [−][2] /(0.245K-kms [−][1] ) = 2.57 × 10 [20] cm [−][2] /(Kkm s [−][1] ).


If we were to look at the Milky Way vertically from outside the solar circle, the CO brightness would be 2×0.245 Kkm s [−][1] = 0.49 K-km s [−][1] . This is small compared to the brightness of disks in external galaxies such as M51 (Bigiel et al., et
al. 2016), but it is about half of the face-on brightness of the
Milky Way at the solar circle, 0.8 K-kms [−][1] (Liszt et al., 2010).
The diffuse molecular gas causes about half of the molecular
hydrogen in the ISM near the Sun. An integrated brightness of
1 K-km s [−][1] is equivalent to a H 2 mass of 4.1M ⊙ pc [−][2] using the
CO-H 2 conversion factor derived above.


3.2. Molecules mixed in the Galactic gas and dust


Figure 2 plots the column densities of HCO [+], C 2 H, HCN, and
CS against reddening E B−V . HCO [+] is the most commonly detected molecule considered here, but neither it nor any other
molecules were found at E B−V < 0.07 mag where the molecular hydrogen fraction f H 2 is generally small in the ISM (Bohlin
et al., 1978). The precise E B−V locus of the onset of appreciable
values of f H 2 is somewhat uncertain (Liszt & Gerin, 2023a) .


Table 2 shows the fractions of detections of HCO [+], C 2 H,
HCN, CS, and HCO with E B−V (in decreasing order of the number of detections) and with the choice of a 2σ or 3σ confidence
level. E B−V = 0.0675 mag is the lowest reddening at which any
absorption was detected in HCO [+] . HCO [+] is detected two-thirds
of the time at E B−V ≤ 0.125 mag or A V ≤ 0.4 mag, and the
detection rates of HCO [+] are almost entirely unaffected by the
choice of confidence level. The ubiquity of HCO [+] absorption
enhances the ability of detecting other species by providing a
guide as to which sight lines harbor molecular gas and the velocity range over which molecular absorption or emission in
other species is expected.


C 2 H is the second most commonly detected molecule. Its
lower detection rate (compared to HCO [+] ) results more from a
lower sensitivity than from a narrower, less ubiquitous distribution in the Galactic gas. Overall, C 2 H was detected in twothirds of the directions in which it was observed.


The so-called high-density tracer HCN is detected at least
half the time when E B−V ∼ [>] 0.125 mag or A V ∼ [>] 0.4 mag and
it is detected along two-thirds of the sight lines where it was
observed. This is almost as frequently as C 2 H. CS, another
high-density tracer, was the least often detected species of the



four species shown in Figure 2 for reasons that are discussed in
Section 3.4.

The numerical values of statistical properties and powerlaw regression fits derived from the plots in Figure 2 are
given in Table 2. HCO [+] has a power-law slope versus E B−V
of 1.03 ± 0.11 in Figure 2, but the Galactic anticenter sample shows a very rapid increase in HCO [+] with E B−V within the
overall envelope of the data. The mixing of gas and dust over
long sight lines with high reddening near the Galactic plane in
the inner-Galaxy sample tends to drive the overall behavior toward the unit slope, while the abundances are more likely to be
dominated by localized cloud-level behavior when the E B−V is
modest.

HCN alone shows a power-law slope higher than one overall, 1.35 ± 0.10. The slope of the power-law fit to N(C 2 H),
0.83 ± 0.10, is noticeably shallower than that of HCO [+] . This
indicates an increase in N(C 2 H)/N(HCO [+] ) at smaller E B−V that
was reported earlier (Lucas & Liszt, 2000). The plot in the
lower right panel shows that CS is lower at E B−V ∼ [<] 0.6 mag
than in the regression line for the detected lines of sight.

The abundances are broadly consistent with earlier results,
but they are subject to several influences, including modern use
of a smaller permanent dipole moment for HCO [+], 3.89 versus
4.07 Debye. This leads to an increase of 9.4% in N(HCO [+] )
and to a smaller abundances relative to HCO [+] and H 2 for other
species. Where the abundances have a nonlinear relation, the
derived average relative abundances depend on the makeup of
the samples, as discussed in Section 3.4.


3.3. HCO


This work and the recent detection of HCO toward J1851+0035

by Narita et al. (et al. 2024) provided the first observations
of HCO in diffuse gas since the original detection by Liszt
et al. (2014). HCO is a widely distributed species whose lowest rotational transition is spread over four hyperfine components with LTE line strengths in a 4:2:2:1 ratio. The strongest
hyperfine component at 86670.76 MHz was observed to be
2% as strong as HCO [+] (Liszt et al., 2014), meaning that
HCO can only be detected at the 2σ level in directions where
HCO [+] is detected with a signal-to-noise ratio of 100 or more.
There were 4 directions like this among the 46 observations in
which HCO was observed in this work, and HCO was detected
above the 2σ level with a relative abundance N(HCO)/N(H 2 )
= 1.1 − 1.3 × 10 [−][9] along four sight lines, as detailed in Table 5.
As noted there, HCO was previously detected toward BL Lac at
E B−V = 0.32 mag with a relative abundance = 0.98±0.02×10 [−][9]

based on the detection of all four hyperfine components. HCO
is about one-third as abundant as HCO [+] and 25 times more

abundant than HOC [+] (Liszt et al., 2004; Gerin et al., et al.
2019).


3.4. Inter-relations in molecular species


Figure 3 plots the variation in C 2 H, HCN, and CS against
HCO [+] in the left panel and the variation in HCO [+], HCN, and
CS against C 2 Hin the right panel. The numerical values of sta

6 L&G: DNM, dark and molecular gas



tistical properties derived from these plots are given in Table 5.
The slopes of the regression lines in the plots versus N(C 2 H) in
the right panel are all steeper than those in the left panel, 1.01
versus 0.67, 1.40 versus 1.25, and 1.4 versus 1.1, from top to
bottom.

The slope of the regression line fit of N(C 2 H) versus
N(HCO [+] ) in the top left panel is 0.67, which confirms the
higher relative abundance ratio N(C 2 H)/N(HCO [+] ) at smaller
N(HCO [+] ) seen in a substantial but smaller and more homogeneous earlier survey of high-latitude northern targets
(Lucas & Liszt, 2000). This nonlinearity means that the mean
C 2 H/HCO [+] ratio varies with the composition of the sample,
and the current mean, <N(C 2 H)> / <N(HCO [+] )> = 10.6,
is slightly lower than the value <N(C 2 H)/N(HCO [+] )> = 14.5
quoted earlier.
HCN is detected down to N(HCO [+] ) ∼ [<] 4 × 10 [11] cm [−][2] with
a tight correlation (r = 0.95) and without a break in the powerlaw slope (1.25 ± 0.06) of the HCN-HCO [+] relation. Earlier,
sparser data (Figure 3 of Lucas & Liszt (2002)) seemed to
show an abrupt increase in N(HCN) at N(HCO [+] ) ≈ 10 [12] cm [−][2] .
The HCN/HCO [+] abundance ratio was quoted earlier as 0.7 2.5 (their Table 1). The current sample mean is <N(HCN)>
/ <N(HCO [+] )>= 1.25 ±0.06, and a comparison of the Gaussian
decomposition products gives a slightly higher number (Sect.
4), but the regression line in Fig. 3 is characterized by values
below unity for N(HCO [+] ) ∼ [<] 10 [13] cm [−][2] .
The upper limits on N(CS) in Chameleon and the values
derived earlier by Lucas & Liszt (2002) are statistically significant in showing a deficiency at E B−V ∼ [<] 0.5 mag relative to the
regression line for the detections at higher extinction in Fig. 2.
They are, however, too high to provide useful information for
the CS chemistry of the sight lines at E B−V ∼ [<] 0.5 mag given
the plot in the lower right panel in Fig. 3. The integration times
needed to study the other molecules were in general too brief
to provide much useful information on CS beyond that noted
in the Introduction.


**4.** **Component decomposition**


Figures 4 and 5 compare the results of a Gaussian decomposition of the new profiles of HCO [+], HCN, and C 2 H. For
each species, the decomposition simultaneously fit all kinematic components and hyperfine components by varying the
central optical depth, central velocity, and profile FWHM while
minimizing deviations from the observed line/continuum ratio exp(−τ). In this way, the quoted rms error estimates appropriately reflect the increased errors encountered when the
line/continuum ratios were fit at high optical depth in a spectrum with a fixed rms flux/continuum noise level, and the uncertainty introduced by multiple components.
We used the results for HCO [+] as an initial template for
HCN and C 2 H in decompositions that considered all observed
kinematic and hyperfine components. The hyperfine components of HCN and C 2 H were fit assuming optical depth ratios
proportional to their intrinsic line strengths. The associated numerical results are given in Tables 6 and 7.
The results considered matched and unmatched components. The matched components are those for which the sep


aration in central velocity is smaller than one-third of the
FWHM of the narrower of the possible pair of components.
Ambiguities are introduced in the case of weak broader components, and the component list was therefore ruthlessly purged
to achieve a minimum set of matched lines. As noted below,
the matched sets account for the vast majority of the aggregate
optical depth in every species, including HCO [+] whose profiles
accommodate a much larger number of fitted components.


4.1. Line widths


The Gaussian components fit to CO absorption were unambiguously found to be 10-15% narrower than those of HCO [+]

along six sight lines in Chamaeleon (Liszt et al., 2019). The
results for line width comparisons between HCO [+] and HCN
or C 2 H find small differences with a lower significance. In any
case, the new results did not deviate from a linear proportionality of the derived FWHM (Table 6 and Table 7).

The typical line widths of the matched components for all
species observed here are very similar, 1 km s [−][1] while the
matched HCN components are found to be 5% narrower on average than in HCO [+] (upper left panel in Figure 4 and Table 6).
As shown in Table 6, HCO [+] was decomposed into many more
components than HCN along the 28 sight lines decomposed in
HCO [+] and HCN (107 versus 55), but the 52 unmatched components in HCO [+] represent only 12% of the aggregate HCO [+]

absorption, and the four unmatched components of HCN represent 2% of the HCN absorption. The unmatched HCO [+] components are much weaker and somewhat broader than average,
as is the case for the unmatched HCN components.
Absorption from C 2 H is intrinsically weaker than in HCO [+]

or HCN, and somewhat different results were obtained when
we compared HCO [+] and C 2 H along 31 sight lines that were
decomposed in both species. For C 2 H, 73 of 119 HCO [+] components were matched with 73 of 81 components fit to C 2 H
(Figure 4 in the bottom panel and Table 7), and C 2 H is 12%
broader, with considerably more scatter than for the comparison of HCO [+] and HCN.

HCO [+] is more easily detected owing to its higher dipole
moment and lack of hyperfine structure, and the many weak
broad unmatched HCO [+] components result in a cumulative distribution function for HCO [+] that is shifted to higher line widths
in Figure 5 in the left panel, where all components that we fit to
each species were used to construct the cumulative distribution
function, not only the components that were matched in two
species.


4.2. Component column densities


The component column densities are shown in the bottom panel
in Figure 4 and are summarized quantitatively in Tables 6 and
7. The fits mimic the behavior seen in Figure 3 and Table 5,
with power-law slopes ≈ 1.2 and 0.7 for HCN and C 2 H, respectively. More HCO [+] components were matched in C 2 H than in
HCN (73 of 119 versus 55 of 107), with many matched components at N(HCO [+] ) < 10 [12] cm [−][2] . The mean HCO [+] column
density of components matched in HCN, 1.26 × 10 [12] cm [−][2], is

L&G: DNM, dark and molecular gas 7



larger by one-third than that for components matched in C 2 H
(0.92 × 10 [12] cm [−][2] ; Table 7). The relative abundance ratio of
the weakest matched components N(C 2 H)/N(HCO [+] ) ≈ 100 exceeds the overall mean <N(C 2 H)> / <N(HCO [+] )>≈ 25 by far.


**5.** **HCO** [+] **and CO in absorption and emission**


Seven of the Galactic anticenter sight lines were newly observed in [13] CO and HCO [+] emission, as shown in Figure 6. The
comparison of HCO [+] observed in emission and absorption can
be used to determine the excitation temperature of the J=1-0
transition of HCO [+] and the volume density of the host gas.
The comparisons of HCO [+], [12] CO and [13] CO in various combinations of emission and absorption reveal information on the
overall character of the gas as seen in CO: the CO brightness,
12 CO/ 13 CO ratio, and CO-H 2 conversion factor at which the
molecular gas is found.

The results are presented in two formats. In one format,
ALMA and IRAM 30m profiles were interpolated onto common spectral grids for a channel-to-channel comparison of the
new results between species and tracers. In the other format,
the results integrated across whole profiles are shown for the
larger sample that includes older data.


5.1. HCO [+] compared in absorption and emission


The left panel of Figure 7 shows the brightness of the HCO [+]

emission plotted against the HCO [+] optical depth on a channelby-channel basis. Emission is detected in a statistical sense at
optical depths τ ∼ [>] 0.05. The emission toward J0502 is much
brighter than in any other source and accounts for almost 50%
of all emission. For most sources, the excitation temperature
inferred from the regression line passing through 0.015 K emission brightness at τ = 1 is 2.758 K. For J0502, the excitation
temperature corresponding to a brightness of 0.09 K at τ = 2 is
2.855 K.

The right panel of Figure 7 plots the integrated HCO [+] emission brightness and optical depth for the new and old results together with iso-density lines derived from the weak excitation
limit (including electrons) in the discussion of the detectability of millimeter-wave emission by Liszt & Pety (2016). When
the collisional excitation of a species is sufficiently far below
thermalization, all energy deposited in the rotation ladder by
collisions escapes the medium, regardless of the optical depth.
The emission line brightness is determined by the product of
the column density of the molecule, the mean hydrogen number density, and an effective excitation rate coefficient that includes all upward collisional excitations into whatever energy
levels. The rate coefficient is 30-100 times larger under diffuse
gas conditions where the ionization fraction exceeds 10 [−][4] compared to fully molecular gas, where CO dominates the carbon
budget and the ionization fraction is 10 [−][7] or smaller.
Almost all sources fall in the range n(H) = 50 − 200 cm [−][3],
with n(H) = 500 cm [−][3] toward J0502. Similar densities in diffuse molecular gas were inferred by Neufeld et al. (2024) from
a study of excitation in C 2 .



5.2. HCO [+] absorption and CO emission


Figure 8 relates the HCO [+] emission brightness to the [12] CO
emission. The typical brightness ratios for the new line profiles
on a channel-channel basis in the left panel are in the range
1/200-1/50, and half the aggregate HCO [+] emission occurs at
12 CO brightness W CO ≤ 2.3 K. The right panel in Figure 8
places the new results in a broader context by combining the
new results with integrated profile results reported away from
continuum background sources by Liszt (2020) that extend to
higher values of the brightnesses. There is a wide range of
HCO [+] brightness at W CO ∼ [>] 6K-kms [−][1], but it is within the
typical range 1/200 - 1/50.


5.3. Host of H 2


The optical depth is proportional to the column density per unit
velocity, and Figure 9 shows the HCO [+] optical depth scaled to
dN(H 2 )/dv and plotted against several quantities related to the
CO emission on a channel-by-channel basis. The [12] CO emission brightness (left), the CO-H 2 conversion factor (middle;
derivable from the left plot), and against the [13] CO/ [12] CO brightness ratio (left).
The middle panel of Figure 9 shows that most of the H 2
is found at CO-H 2 conversion factors in the range 1 − 4 ×
10 [20] H 2 cm [−][2] (K-kms [−][1] ) [−][1], but J0439 has only very weak
12 CO emission and a much higher ratio 9 × 10 20 H 2 cm −2 (Kkm s [−][1] ) [−][1] .
The right panel in Figure 9 shows that half the total amount
of H 2 occurs at [12] CO/ [13] CO brightness ratios at or above 20 and
80% above a ratio of 10, indicating the diffuse nature of the gas
and the general absence of saturation in [12] CO. The [12] CO/ [13] CO
ratio is expected to have been substantially diminished by fractionation resulting from C [+] exchange.


**6.** **Summary**


We joined recent ALMA observations (Table 1) with older absorption data taken at the IRAM Plateau de Bure Interferometer
(PdBI) and Northern Extended Millimeter Array (NOEMA)
telescopes to analyze a larger body of absorption spectra of
HCO [+], C 2 H, HCN, CS, and HCO arising in diffuse interstellar
gas seen toward compact extragalactic continuum sources. The
sight lines in the sample are slightly overabundanton average in
E B−V compared to the Galactic average (Figure 1, Section 3.1)
and richer in reddening than in the column density of atomic
hydrogen. This implies that the sample is not only rich in gas
and dust, but has a higher fraction of H 2 . The distribution of
E B−V with sin(|b|) has a higher scatter than that of N(HI), which
can be understood given the large scatter in the plots of N(H 2 )
and integrated CO emission W CO .
Figure 2 plots the column densities of HCO [+], C 2 H, HCN,
and CS against E B−V (see Section 3.2 and Table 2). Absorption
from HCO [+], the most ubiquitous species (72 of 86 sight lines;
Table 3), was uniformly detected at E B−V ∼ [>] 0.2 mag and was
detected more rarely down to E B−V = 0.07 mag, where H 2 first
becomes a substantial component of the ISM. C 2 H is ubiquitous, and N(C 2 H)/N(HCO [+] ) increases at smaller N(HCO [+] ), but

8 L&G: DNM, dark and molecular gas



**10** **[13]**


**10** **[12]**


**10** **[11]**


**10** **[13]**


**10** **[12]**


**10** **[11]**


**0.01** **0.1** **1**

**E(B-V) [mag]**



PdBi
Inner Galaxy
Chamaeleon
Outer Galaxy


PdBi
Inner Galaxy
Chamaeleon
Outer Galaxy



**10** **[14]**


**10** **[13]**


**10** **[12]**


**10** **[13]**


**10** **[12]**


**10** **[11]**


**0.01** **0.1** **1**

**E(B-V) [mag]**



PdBi
Inner Galaxy
Chamaeleon
Outer Galaxy


PdBi
Inner Galaxy
Chamaeleon



Fig. 2. Molecular column densities plotted against E B−V from Schlegel et al. (1998). The associated datasets are indicated (see Section 2.4). The
solid line in each panel is a regression line for the sight lines with detections of both plotted quantities. The values for the statistical parameters
and the regression fits are given in Table 2, and the statistical detection rates are given in Table 3.


Table 1. Statistical parameters and power-law fits for the data shown in Figure 1 [1]


x-species y-species n <x> <y> a b r
sin(|b|) E B−V 88 0.348(0.226) 0.560(0.899) mag 1.234(0.060) -0.999(0.083) 0.79
N(HI) 88 0.351(0.237) 2.137(2.878)×10 [21] cm [−][2] 20.592(0.033) -0.871(0.045) 0.90
N(H 2 ) 86 0.348(0.226) 6.002(12.42)×10 [20] cm [−][2] 19.801(0.093) -0.903(0.130) 0.60
W CO 54 0.320(0.197) 2.313(3.537) K-km s [−][1] -0.611(0.161) -0.817(0.226) 0.45

1
The quantities in parentheses are the standard deviation. a and b are fits to log (value of the y-species) =
a+b×log (value of the x-species), and r is the correlation coefficient.


Table 2. Statistical parameters and power-law fits for the data shown in Figure 2


x-species y-species n <x> <y> a b r
E B−V N(HCO [+] ) 73 0.656(0.948) mag 2.130(4.011)×10 [12] cm [−][2] 12.347(0.065) 1.025(0.113) 0.733
N(C 2 H) 53 0.650(1.040) mag 2.513(3.930)×10 [13] cm [−][2] 13.477(0.062) 0.828(0.105) 0.74
N(HCN) 38 0.754(1.176) mag 3.641(7.347)×10 [12] cm [−][2] 12.410(0.106) 1.355(0.197) 0.74
N(CS) 7 2.016(2.300) mag 6.591(5.265)×10 [12] cm [−][2] 12.538(0.143) 0.975(0.258) 0.860

1
The quantities in parentheses are the standard deviation. a and b are fits to log (value of the y-species) =
a+b×log (value of the x-species), and r is the correlation coefficient.

**10** **[14]**


**10** **[13]**


**10** **[12]**


**10** **[13]**


**10** **[12]**


**10** **[11]**


**10** **[13]**


**10** **[12]**


**10** **[11]**



PdBi
Inner Galaxy
Chamaeleon
Outer Galaxy


PdBi
Inner Galaxy
Chamaeleon
Outer Galaxy


PdBi
Inner Galaxy
Chamaeleon


**10** **[11]** **10** **[12]** **10** **[13]**

**N(HCO** **[+]** **) [cm** **[-2]** **]**



L&G: DNM, dark and molecular gas 9


**10** **[13]**


**10** **[12]**



PdBi
Inner Galaxy
Chamaeleon
Outer Galaxy


PdBi
Inner Galaxy
Chamaeleon
Outer Galaxy


PdBi
Inner Galaxy
Chamaeleon


**10** **[12]** **10** **[13]** **10** **[14]**

**N(C2H) [cm** **[-2]** **]**



**10** **[11]**


**10** **[13]**


**10** **[12]**


**10** **[11]**


**10** **[13]**


**10** **[12]**


**10** **[11]**



Fig. 3. Molecular column densities plotted against N(HCO [+] ; left) and N(C 2 H; right). The regression lines include only data for which both
molecules were detected. The values for the statistical parameters and the regression fits are given in Table 5.



C 2 H was detected slightly less frequently than HCO [+] (53 of
76 sight lines) because C 2 H absorption is intrinsically weaker
and harder to detect. The so-called dense-gas tracer HCN was
uniformly detected down to E B−V = 0.3 mag and occasionally
seen even below E B−V = 0.1 mag. It was uniformly detected at
N(H 2 ) ∼ [>] 10 [20] cm [−][2] with little change in the relative abundance
N(HCN)/N(HCO [+] ) ≈ 1.25 or N(HCN)/N(H 2 ) = 3.75 × 10 [−][9] .


We presented no new detections of CS, which we failed
to detect along all 13 sight lines we studied in the outskirts
of Chamaeleon (owing to a lack of sensitivity), and which we
subsequently did not observe in the Galactic anticenter. The
upper limits achieved in the Chamaeleon study show, however,
that the relative abundance of CS is lower at the low-E B−V end



of our sample at E B−V ∼ [<] 1 mag (Fig. 2) and perhaps (Fig. 3)
when N(HCO [+] ) [<] ∼ 2 × 10 [12] cm [−][2] .


HCO is ubiquitous in the diffuse ISM with
N(HCO)/N(HCO [+] ) = 1/3 or N(HCO)/N(H 2 ) = 1 × 10 [−][9]

, but the strongest hyperfine component of HCO is only about
2% as strong in absorption as HCO [+] and was only detected
along the four ALMA sight lines with a signal-to-noise ratio
of 100:1 or more in HCO [+] (Table 5).


Figure 3 (see Section 3.3 and Table 5) shows the interrelations among the column densities of HCO [+], C 2 H, HCN,
and CS. HCN is detected almost without exception down to
N(HCO [+] ) = 3 × 10 [11] cm [−][2] or N(H 2 ) = 10 [20] cm [−][2], in contrast
to earlier results that implied that N(HCN)/N(HCO [+] ) increased

10 L&G: DNM, dark and molecular gas



**2.5**


**2.0**


**1.5**


**1.0**


**0.5**



**2.5**


**2.0**


**1.5**


**1.0**


**0.5**



PdBi
Inner Galaxy
Chamaeleon
Outer Galaxy


**0.0** **0.5** **1.0** **1.5** **2.0** **2.5**

**FWHM HCO** **[+]** **[km s** **[-1]** **]**



PdBi
Inner Galaxy
Chamaeleon
Outer Galaxy


**0.0** **0.5** **1.0** **1.5** **2.0** **2.5**

**FWHM HCO** **[+]** **[km s** **[-1]** **]**



**10** **[13]**


**10** **[12]**


**10** **[11]**



PdBi
Inner Galaxy
Chamaeleon
Outer Galaxy



PdBi
Inner Galaxy
Chamaeleon
Outer Galaxy



**10** **[14]**


**10** **[13]**


**10** **[12]**



**10** **[10]** **10** **[11]** **10** **[12]** **10** **[13]**

**N(HCO** **[+]** **) [cm** **[-2]** **]**



**10** **[10]** **10** **[11]** **10** **[12]** **10** **[13]**

**N(HCO** **[+]** **) [cm** **[-2]** **]**



Fig. 4. Results of the Gaussian component fitting. Top: FWHM of the Gaussian components fit to spectra of HCN and C 2 H compared with
those fit to HCO [+] . The solid black line shows the regression fit in each case, and the dashed light gray line shows the locus of the equal FWHM.
The numerical quantities derived from the fitting are given in Tables 6 and 7. Bottom: Column densities.


Table 3. Detection rates as they vary with E B−V [1] and confidence level


2σ limits


E B−V
Species All 0.0..0.067 0.067..0.125 0.125..0.250 0.250..0.5 0.5..1.0 1.0..2.0 2.0..7.345
HCO [+] 72/86 0/4 8/12 10/16 24/24 17/17 6/6 7/7
C 2 H 53/76 0/4 6/11 8/17 17/21 14/15 4/4 4/4
HCN 38/57 4/7 4/10 12/21 12/13 2/2 4/4
CS 7/24 1/3 0/2 1/9 1/4 1/2 3/4
HCO 4/46 0/6 1/10 1/20 2/10

3σ limits


E B−V
Species All 0.0..0.067 0.067..0.125 0.125..0.250 0.250..0.5 0.5..1.0 1.0..2.0 2.0..7.345
HCO [+] 71/86 0/4 8/12 9/16 24/24 17/17 6/6 7/7
C 2 H 45/76 0/4 2/11 6/17 15/21 14/15 4/4 4/4
HCN 32/57 1/7 4/10 10/21 11/13 2/2 4/4
CS 7/24 1/3 0/2 1/9 1/4 1/2 3/4
HCO 2/46 0/6 1/10 0/20 1/10
1 Entries are #sight lines where detected/#sight lines observed

L&G: DNM, dark and molecular gas 11



**100**


**80**


**60**


**40**


**20**



C2H
HCN
HCO [+]


**0** **2** **4**

**FWHM [km s** **[-1]** **]**



C2H
HCO [+]


**0** **2** **4**
**FWHM [km s** **[-1]** **]**



HCN
HCO [+]



**25**


**20**


**15**


**10**


**5**


**0**



**0** **2** **4**

**FWHM [km s** **[-1]** **]**



Fig. 5. line width probability distributions for all components fit to each species. Left: Cumulative distributions for HCO [+], HCN, and C 2 H.
Middle: Fractional distributions of individual HCO [+] and HCN line widths. Right: Fractional distributions of HCO [+] and C 2 H line widths.



**12CO**



**12CO/2**



**J0431+2037**

**12CO**


**13COx10**


**HCO** **[+]**


**0** **5** **10** **15**


**J0439+3045**


**12CO/2**


**13CO*3**


**HCO** **[+]** **x15**


HCO [+]


**0** **10**

**VLSR (KM S** **[-1]** **)**



**1**


**0**


**2**


**1**


**0**



**J0356+2903**


**13COx5**



**J0426+2327**


**13COx5**



**J0502+1338**



**0.5**


**0.0**


**-0.5**


**1**


**0**



**1**


**0**



**HCO** **[+]** **x10**


**HCO** **[+]**


**0** **10**



**HCO** **[+]** **x10**


**HCO** **[+]**


**0** **10**



**12CO/2**


**HCO** **[+]** **x5**


**HCO** **[+]**


**0** **10**

**VLSR (KM S** **[-1]** **)**



**J0437+2940**


**13CO**



**12CO/3**



**J0438+3004**


**13CO**



**12CO**



**HCO** **[+]** **x10**


**HCO** **[+]**


**0** **10**

**VLSR (KM S** **[-1]** **)**



**1**


**0**


**2**


**1**


**0**



**HCO** **[+]** **x15**


**HCO** **[+]**


**0** **10**

**VLSR (KM S** **[-1]** **)**



Fig. 6. Emission profiles of [12] CO(black), [13] CO(gray and gray shaded), HCO [+] (green), and HCO [+] absorption (red). The emission profiles were
normalized as shown. The CO emission profiles were folded in frequency, resulting in negative artifacts at velocities not associated with other
material.



abruptly at N(HCO [+] ) = 10 [12] cm [−][2] . The bottom panel in Figure
3 shows that the lack of detections of CS at E B−V < 0.5 mag
might result from a lack of sensitivity, because the observed
upper limits on N(CS) are higher than the values expected from
extrapolating the detections at higher N(HCO [+] ) and N(C 2 H).


In Section 4 we discussed the Gaussian decomposition of
ALMA profiles of HCO [+], C 2 H, and HCN by comparing the
numbers and line widths of kinematic components in Figures 45 and Tables 6 and 7. The typical line widths for all species are
1 km s [−][1] . HCO [+] is the most widely detected species as a result
of its high dipole moment and lack of hyperfine structure, and
its spectra are richer and decomposed into more components



than in C 2 H or HCN. For HCN (Table 7), 55 of 59 HCN components seen along 28 sight lines were matched against 55 of
107 components in HCO [+], and the matched HCN components
were found to be 5% narrower on average (0.975 versus 1.032
km s [−][1] ). The unmatched components are weaker and broader
than average and constitute small fractions of the total absorption in either species. For C 2 H (Figures 4-5 and Table 7) 73
of 81 components were matched against 73 of 119 HCO [+] components along 31 sight lines, and the matched C 2 H components
are 12% broader, 1.12 versus 1.03 km s [−][1] . The unmatched components constitute a small fraction of the total absorption.

12 L&G: DNM, dark and molecular gas



**0.10**


**0.08**


**0.06**


**0.04**


**0.02**


**0**

|J0502<br>J0439<br>J0438<br>J0437<br>J0426<br>J0356|Col2|
|---|---|
|||



**0.01** **0.1** **1**

τ **(HCO** **[+]** **)**



**1.0**


**0.8**


**0.6**


**0.4**



**0** **2** **4** **6** **8** **10** **12**

Υ **HCO+ [km s** **[-1]** **]**







**0.12**


**0.10**


**0.08**


**0.06**


**0.04**


**0.02**


**0**





**0.2**


**0**



Fig. 7. HCO [+] emission plotted against absorption. Left: Channel values of emission brightness and absorption for the new data shown in
Figure 6. The excitation temperature corresponding to the regression line is 2.758 K. Right: Integrated emission brightness against integrated
absorption Υ HCO+ for the new and old data. Superposed at the right are the locii of constant number density n(H) for diffuse purely molecular
gas using results for the weak excitation limit (including electrons) described by Liszt & Pety (2016) (see Section 5.1 for an explanation of the
underlying physics).



**0.10**


**0.08**


**0.06**



**0.25**


**0.20**


**0.15**


**0.10**


**0.05**


**0**













**1.0**


**0.8**


**0.6**


**0.4**


**0.2**


**0**



**0.04**


**0.02**


**0**





**0** **2** **4** **6**

**T(** **[12]** **CO) [Kelvin]**



**0** **5** **10** **15** **20**

**WCO [K-km s** **[-1]** **]**



Fig. 8. Comparison of emission brightness for HCO [+] and [12] CO. Left: Channel-channel comparison for the six new anticenter sources with
W CO - 1 K-km s [−][1] . Right: Integrated HCO [+] emission plotted against W CO with new data from this work overlaid on earlier observations taken
around and well removed from continuum background sources. This was previously shown as Figure 8 in Liszt (2020).



In Section 5 we discussed new observations of HCO [+] and

CO emission along seven outer Galaxy sight lines (Figure 6).
A channel-by-channel comparison of the HCO [+] emission and
absorption showed (Figure 7, left) that HCO [+] emission is detected in a statistical sense at HCO [+] optical depths as low as
0 .05, and the great majority of channels imply a typical excitation temperature of 2.76 K up to τ = 2. Stronger emission
with an excitation temperature 2.86 K was seen on the the sight
line to J0502. Deriving N(HCO [+] ) in the limit of no collisional
excitation is a good approximation.


The comparison of the integrated HCO [+] emission and absorption (Figure 7, right) showed that the mean hydrogen vol


ume density falls in the range n(H) = 50 − 200 cm [−][3] on six
of the seven sight lines, with n(H) = 500 cm [−][3] toward J0502,
where the HCO [+] emission is brighter.

The brightness ratio of the HCO [+] emission to that of CO is
generally within a factor of two of 1% for gas seen near the continuum background targets (Figure 8, left). Most of the HCO [+]

emission arises in channels in which the CO brightness is 2 K
or lower.

In Section 5.1 (Figure 9) we related the H 2 content to the
nature of the host gas as characterized by different aspects of
the CO emission. Nearly half of the total amount of H 2 arises in
line channels with a CO brightness of ∼ [<] 2 K (Figure 9, left) and

**1E21**


**8E20**


**6E20**


**4E20**


**2E20**


**0**







L&G: DNM, dark and molecular gas 13


**1.0**


**0.8**


**0.6**


**0.4**



**0.2**


**0.0**







**0** **2** **4** **6**

**T(** **[12]** **CO) [Kelvin]**



**0** **5E20** **1E21** **1.5E21** **2E21** **2.5E21** **3E21**
**XCO [H2 cm** **[-2]** **/(K-km s** **[-1]** **)]**



**0.00** **0.05** **0.10** **0.15** **0.20**
**T(** **[13]** **CO) /T(** **[12]** **CO)**



Fig. 9. Channel-by-channel comparison with values of the HCO [+] absorption scaled to H 2 . The fat red curve in each panel is the fractional
cumulative distribution, which is to be read against the red scale at the right.



Table 4. Relative abundances of HCO


Source E B−V N(H 2 ) N(HCO) X(HCO) [1]

mag 10 [21] cm [−][2] 10 [12] cm [−][2] 10 [−][9]

J0325+2224 0.21 0.371 0.40(0.13) 1.08(0.34)
J0433+0521 0.30 0.127 0.17(0.06) 1.33(0.49)
J0438+3004 0.95 2.293 2.82(0.25) 1.23(0.11)
J0439+3045 0.87 1.850 2.16(0.82) 1.17(0.44)
BL Lac [2] 0.32 0.867 0.85(0.02) 0.98(0.02)
1 X(HCO)=N(HCO)/N(H 2 )
2 Data from Liszt et al. (2014)


about 80% with CO-H 2 conversion factors N(H 2 )/W CO = 1 −
5 × 10 [20] H 2 (K-kms [−][1] ) [−][1] and [12] CO/ [13] CO emission brightness
ratios above 10.


Acknowledgements. The National Radio Astronomy Observatory is a
facility of the National Science Foundation, operated by Associated
Universities, Inc.

This work was supported by the French program “Physique
et Chimie du Milieu Interstellaire” (PCMI) funded by the Conseil
National de la Recherche Scientifique (CNRS) and Centre National
d’Etudes Spatiales (CNES).

This work is based in part on observations carried out under
project number 003-19 with the IRAM 30m telescope]. IRAM is supported by INSU/CNRS (France), MPG (Germany) and IGN (Spain).

This paper makes use of the following ALMA data


– ADS/JAO.ALMA#2016.1.00132.S

– ADS/JAO.ALMA#2016.1.00714.S

– ADS/JAO.ALMA#2018.1.00115.S

– ADS/JAO.ALMA#2019.1.00120.S


ALMA is a partnership of ESO (representing its member states),
NSF (USA) and NINS (Japan), together with NRC (Canada), NSC
and ASIAA (Taiwan), and KASI (Republic of Korea), in cooperation
with the Republic of Chile. The Joint ALMA Observatory is operated
by ESO, AUI/NRAO and NAOJ.

We thank the referee for a close reading that resulted in a significantly improved presentation.



**References**


Bigiel, F., Leroy, A. K., & Jim´enez-Donaire, M. J. et al. 2016,
ApJ, 822, L26
Bohlin, R. C., Savage, B. D., & Drake, J. F. 1978, ApJ, 224,
132

Gerin, M. & Liszt, H. 2017, A&A, 600, A48
Gerin, M., Liszt, H., & Neufeld, D. et al. 2019, A&A, 622, A26
Gerin, M., Liszt, H., Pety, J., & Faure, A. 2024, A&A, 686,
A49

Grenier, I. A., Casandjian, J.-M., & Terrier, R. 2005, Science,
307, 1292
Kalberla, P. M. W., Burton, W. B., & Hartmann, D. et al. 2005,
A&A, 440, 775
Lallement, R., Vergely, J. L., Babusiaux, C., & Cox, N. L. J.
2022, A&A, 661, A147
Liszt, H. & Gerin, M. 2018, A&A, 610, A49
—. 2023a, ApJ, 943, 172
—. 2023b, A&A, 675, A145
Liszt, H., Gerin, M., & Grenier, I. 2018, A&A, 617, A54
—. 2019, A&A, 627, A95
Liszt, H. & Lucas, R. 2001, A&A, 370, 576
Liszt, H., Lucas, R., & Black, J. H. 2004, A&A, 428, 117
Liszt, H., Lucas, R., & Pety, J. 2006, A&A, 448, 253
Liszt, H., Sonnentrucker, P., Cordiner, M., & Gerin, M. 2012,
ApJ, 753, L28
Liszt, H. S. 2020, ApJ, 897, 104
Liszt, H. S. & Pety, J. 2012, A&A, 541, A58
—. 2016, ApJ, 823, 124
Liszt, H. S., Pety, J., Gerin, M., & Lucas, R. 2014, A&A, 564,
A64

Liszt, H. S., Pety, J., & Lucas, R. 2010, A&A, 518, A45+
Lucas, R. & Liszt, H. S. 1996, A&A, 307, 237
—. 2000, A&A, 358, 1069
—. 2002, A&A, 384, 1054
Narita, K., Sakamoto, S., & Koda, J. et al. 2024, ApJ, 969, 102
Nash, A. G. 1990, ApJS, 72, 303
Neufeld, D. A., Welty, D. E., Ivlev, A. V., Caselli, P.,
Edenhofer, G., Indriolo, N., Obolentseva, M., Silsbee, K.,
Sonnentrucker, P., & Wolfire, M. G. 2024, ApJ, 973, 143

14 L&G: DNM, dark and molecular gas


Table 5. Statistical parameters and power-law fits for the data shown in Figure 3


x-species y-species n <x> <y> a b r
N(HCO [+] ) N(C 2 H) 51 2.469(0.456)×10 [12] cm [−][2] 2.619(4.018)×10 [13] cm [−][2] 5.138(0.799) 0.667(0.066) 0.82
N(HCN) 39 2.987(5.093)×10 [12] cm [−][2] 3.732(7.419)×10 [12] cm [−][2] -3.152(0.726) 1.248(0.060) 0.96
N(CS) 7 8.657(9.323)×10 [12] cm [−][2] 6.179(5.610)×10 [12] cm [−][2] -1.806(2.344) 1.126(0.185) 0.94
N(C 2 H) N(HCO [+] ) 51 2.619(4.018)×10 [13] cm [−][2] 2.469(0.456)×10 [12] cm [−][2] -1.250(1.321) 1.008(0.100) 0.82
N(HCN) 35 3.275(4.643)×10 [13] cm [−][2] 4.097(7.746)×10 [12] cm [−][2] -6.494(1.857) 1.395(0.140) 0.87
N(CS) 7 7.826(8.128)×10 [13] cm [−][2] 6.179(5.610)×10 [12] cm [−][2] -7.101(3.274) 1.429(0.239) 0.94

1
The quantities in parentheses are the standard deviation. a and b are fits to log (value of the y-species) =
a+b×log (value of the x-species), and r is the correlation coefficient.


Table 6. Mean line widths and column densities of the Gaussian components on 28 sight lines decomposed in HCO [+] and HCN


Molecule HCO [+] HCN Slope
Sample Total Matched Unmatched Total Matched Unmatched Matched
#components 107 55 52 59 55 4 55
<FWHM> km s [−][1] 1.25(0.64) 1.03(0.37) 1.47(0.57) 1.03(0.52) 0.98(0.41) 1.51(1.19) 0.99(0.07)
<N> 10 [12] cm [−][2] 0.73(1.06) 1.26(1.25) 0.18(0.20) [1] 1.78(2.67) 1.88(2.74) 0.41(0.22) [2] 1.13(0.08)
1 The unmatched components of HCO + comprise 12% of the total HCO + column density.
2 The unmatched components of HCN comprise 2% of the total HCN column density.


Table 7. Mean line widths and column densities for the Gaussian components on 31 sight lines decomposed in HCO [+] and C 2 H


Molecule HCO [+] C 2 H
Sample Total Matched Unmatched Total Matched Unmatched Slope
#components 119 73 46 81 73 8 73
<FWHM> km s [−][1] 1.26(0.73) 1.03(0.37) 1.66(0.90) 1.20(0.56) 1.15(0.49) 1.48(0.82) 0.98(0.09)
<N> 10 [12] cm [−][2] 0.71(1.00) 0.92(1.17) 0.20(0.51) [1] 9.29(8.28) 9.76(0.81) 5.00(3.10) [2] 0.56(0.06)
1 The unmatched components of HCO + comprise 11% of the total HCO + column density.
2
The unmatched components of C 2 H comprise 5% of the total C 2 H column density.



Planck Collaboration, Fermi Collaboration, & Ade, P. A. R. et
al. 2015, A&A, 582, A31
Remy, Q., Grenier, I. A., Marshall, D. J., & Casandjian, J. M.
2017, A&A, 601, A78
—. 2018, A&A, 611, A51
Savage, B. D., Drake, J. F., Budich, W., & Bohlin, R. C. 1977,
ApJ, 216, 291
Schlegel, D. J., Finkbeiner, D. P., & Davis, M. 1998, ApJ, 500,
525

Sun, M., Jiang, B., Zhao, H., & Ren, Y. 2021, ApJS, 256, 46
Voirin, J., Manara, C. F., & Prusti, T. 2018, A&A, 610, A64
Yan, Q.-Z., Zhang, B., & Xu, Y. et al. 2019, A&A, 624, A6
Zucker, C., Speagle, J. S., & Schlafly, E. F. et al. 2019, ApJ,
879, 125


**Appendix A:** **Data sources**


The new and old data sources are described in Section 2.1 and

Table A.1.


**Appendix B:** **Line of sight properties:** HCO [+] **, HCN**
**and C** 2 **H**


New results for HCO [+], HCN and C 2 H are summarized in Table

B.1.



Table A.1. Data sources


Observation old new

Absorption PdBI, Noema ALMA
Emission ARO 12m IRAM 30m


**Appendix C:** **Spectra of C** 2 **H**


Recent ALMA absorption spectra of C 2 H are shown in Figure
C.1.


**Appendix D:** **Spectra of HCN**


Recent ALMA absorption spectra of HCN are shown in Figure
D.1.


**Appendix E:** **Spectra of HCO**


Recent ALMA absorption spectra of HCO are shown in Figure
E.1 for the sight lines noted in Table 5.


**Appendix F:** **Forming emission spectra in the**
**presence of a continuum background.**


In Section 5 we discussed the excitation of HCO [+] based on

comparison of emission and absorption spectra of HCO [+] and

L&G: DNM, dark and molecular gas 15


Table B.1. Line of sight properties, HCO [+] column densities and new results for HCN and C 2 H


Source RA(J2000) Dec(J2000) l b E B−V flux N(HCO [+] ) N(HCN) N(C 2 H)
hh.mmsss dd.mmsss degrees degrees mag Jy 10 [12] cm [−][2] 10 [12] cm [−][2] 10 [13] cm [−][2]

J0203+1134 2.03464 11.34492 149.6826 -47.4992 0.144 0.128 ≤0.289 ≤0.455 ≤1.635

J0209+1352 2.09357 13.52045 150.1800 -44.8290 0.094 0.225 0.215(0.055) ≤0.263 ≤0.908
J0211+1051 2.11132 10.51348 152.5781 -47.3674 0.145 0.465 0.841(0.032) 0.713(0.053) 1.971(0.201)
J0213+1820 2.13105 18.20255 148.7289 -40.4014 0.130 0.094 ≤0.379 ≤0.688 ≤2.278

J0231+1322 2.31459 13.22547 157.0917 -42.7380 0.121 0.431 0.154(0.028) ≤0.148 ≤0.445
J0242+1742 2.42243 17.42589 157.0180 -37.7033 0.077 0.227 ≤0.166 ≤0.271 ≤0.967

J0252+1718 2.52077 17.18427 159.7420 -36.7885 0.220 0.205 0.276(0.084) ≤0.312 ≤1.139
J0325+2224 3.25368 22.24004 163.6700 -28.0213 0.213 1.171 1.114(0.019) 0.620(0.031) 1.293(0.058)
J0329+3510 3.29154 35.10060 155.9152 -17.4042 0.267 0.582 0.559(0.035) ≤0.146 0.606(0.169)
J0329+2756 3.29577 27.56155 160.7030 -23.0743 0.198 0.161 ≤0.213 ≤0.345 ≤1.240

J0334+0800 3.34533 8.00144 177.2396 -37.0871 0.391 0.151 0.483(0.097) ≤0.492 ≤1.627
J0336+3218 3.36301 32.18293 158.9998 -18.7650 0.733 1.674 0.178(0.010) ≤0.049 0.534(0.049)
J0356+2903 3.56085 29.03423 164.6120 -18.4927 0.212 0.140 1.648(0.099) 1.415(0.145) ≤1.279
J0357+2319 3.57216 23.19538 169.0302 -22.4661 0.185 0.227 0.307(0.030) ≤0.171 ≤0.612
J0400+0550 4.00117 5.50431 184.2710 -33.7266 0.266 0.161 0.273(0.070) ≤0.352 ≤1.224
J0401+0413 4.01199 4.13344 186.0261 -34.4947 0.341 0.409 0.536(0.023) 0.272(0.051) 1.853(0.126)
J0403+2600 4.03056 26.00015 168.0260 -19.6483 0.201 0.335 0.657(0.032) 0.431(0.058) 0.322(0.047)
J0406+0637 4.06343 6.37150 184.7075 -32.0009 0.283 0.267 0.595(0.057) 0.302(0.089) 1.503(0.235)
J0407+0742 4.07291 7.42075 183.8723 -31.1558 0.265 0.390 0.580(0.034) 0.394(0.057) 1.207(0.214)
J0426+0518 4.26366 5.18199 189.3631 -28.7705 0.291 0.518 0.137(0.022) ≤0.108 0.708(0.131)
J0426+2327 4.26557 23.27396 173.8881 -17.4457 0.539 0.309 2.831(0.063) 3.780(0.086) 2.434(0.249)
J0427+0457 4.27476 4.57083 189.8857 -28.7306 0.335 0.413 0.686(0.026) 0.474(0.052) 2.583(0.164)
J0437+2037 4.31038 20.37343 176.8096 -18.5565 0.532 0.221 1.696(0.081) 0.769(0.121) 2.260(0.399)
J0431+1731 4.31574 17.31358 179.4942 -20.3579 0.464 0.106 1.109(0.121) ≤0.553 ≤1.939
J0433+0521 4.33111 5.21156 190.3730 -27.3967 0.298 4.931 0.382(0.003) 0.118(0.006) 1.099(0.019)
J0437+2940 4.37044 29.40138 170.5818 -11.6609 0.979 0.060 6.517(1.252) 10.987(0.753) 8.980(1.016)
J0438+3004 4.38049 30.04455 170.4116 -11.2283 0.952 0.692 6.878(0.042) 8.815(0.049) 6.154(0.134)
J0439+3045 4.39178 30.45076 170.0655 -10.5913 0.867 0.196 5.551(0.090) 6.438(0.110) 2.734(0.292)
J0440+1437 4.40211 14.37570 183.2538 -20.5438 0.681 0.339 1.333(0.034) 0.621(0.060) 2.956(0.202)
J0445+0715 4.45014 7.15539 190.4535 -23.8898 0.121 0.277 ≤0.091 ≤0.208 ≤0.526

J0449+1121 4.49077 11.21286 187.4274 -20.7365 0.504 0.526 0.714(0.024) 0.484(0.037) 3.001(0.118)
J0502+1338 5.02332 13.38110 187.4143 -16.7456 0.564 0.273 1.986(0.065) 1.626(0.075) 1.694(0.239)
J0510+1800 5.10024 18.00416 184.7304 -12.7895 0.328 2.442 0.139(0.006) 0.031(0.010) 0.209(0.029)
J0942-7731 9.42427 -77.31116 293.3194 -18.3299 0.336 0.204 1.256(0.074) ≤0.170 1.653(0.284)
J1058-8003 10.58433 -80.03542 298.0095 -18.2881 0.152 1.188 0.221(0.010) ≤0.052 ≤0.223
J1136-6827 11.36021 -68.27061 296.0710 -6.5902 0.460 0.470 1.365(0.039) 0.554(0.015) 1.376(0.158)
J1145-6954 11.45536 -69.54018 297.3172 -7.7465 0.387 0.541 0.957(0.034) 0.203(0.039) 0.724(0.147)
J1147-7935 11.47334 -67.53418 296.9588 -5.7671 0.300 1.563 0.060(0.006) ≤3.969 0.200(0.043)
J1152-8344 11.52532 -83.44094 301.2388 -21.0576 0.283 0.114 0.264(0.077) ≤0.544 ≤1.804
J1224-8313 12.24544 -83.13101 302.0983 -20.3907 0.257 0.301 1.040(0.048) 0.652(0.076) 0.988(0.179)
J1254-7138 12.54598 -71.38184 303.2156 -8.7687 0.282 0.383 0.153(0.030) ≤0.143 ≤0.000
J1312-7724 13.12387 -77.24131 304.1251 -14.5810 0.476 0.209 0.298(0.040) ≤0.294 ≤0.777
J1550-8258 15.50592 -82.58065 308.2800 -22.0469 0.107 0.357 0.266(0.044) ≤0.188 ≤0.629
J1617-7717 16.17493 -77.17185 313.4306 -18.8538 0.091 2.478 0.065(0.008) ≤0.029 ≤0.100
J1723-7713 17.23509 -77.13502 315.6923 -21.7985 0.255 0.312 1.658(0.057) 1.799(0.057) ≤0.901
J1733-7935 17.33407 -79.35554 313.6117 -23.2669 0.139 0.606 0.066(0.020) ≤0.093 0.409(0.104)



CO. Because the emitted and absorbed fluxes of HCO [+] lines
are by coincidence comparable at most millimeter-wave telescopes, pure emission profiles cannot be obtained directly toward the continuum Lucas & Liszt (1996). Instead we observed
at positions displaced from the continuum by 1.2 HPBW = 30 [′′]

in each of the four cardinal directions, similar to Lucas & Liszt
(1996). Spectra around J0426+2327 are shown in Figure A.4.
The individual HCO [+] spectra at right are noisy but see the average in Figure 6.



Mixing of emission and absorption is not an issue for the
much stronger CO emission lines that are shown at left in
Figure F.1. The spectra toward and displaced 1 HPBW = 22 [′′]

from the continuum differ little so we averaged all five positions to form the [12] CO and [13] CO spectra shown in Figure 6.
Although the averaged CO and HCO [+] spectra discussed in
Section 5 were derived over slightly regions they (as earlier)
seem to present a coherent picture of the HCO [+] excitation.

16 L&G: DNM, dark and molecular gas



**0.1**


**0.0**


**-0.1**


**-0.2**


**0.1**


**0.0**


**-0.1**


**-0.2**


**0.1**


**0.0**


**-0.1**


**-0.2**


**0.1**


**0.0**


**-0.1**


**-0.2**


**0.1**


**0.0**


**-0.1**


**-0.2**


**0.1**


**0.0**


**-0.1**


**-0.2**



**J1224-8313**


**-20** **0** **20**



**J0209+1352** **J0211+1051** **J0231+1322** **J0242+1742** **J0252+1718** **J0325+2224** **J0329+3510**


**J0334+0800** **J0336+3218** **J0356+2903** **J0357+2319** **J0400+0550** **J0401+0413** **J0403+2600**


**J0406+0637** **J0407+0742** **J0426+0518** **J0426+2327** **J0427+0457** **J0431+2037** **J0431+1731**


**J0433+0521** **J0437+2940** **J0438+3004** **J0439+3045** **J0440+1437** **J0445+0715** **J0449+1121**


**J0502+1338** **J0510+1800** **J0942-7731** **J1058-8003** **J1136-6827** **J1145-6954** **J1152-8344**



**J1254-7138**


**-20** **0** **20**



**J1312-7724**


**-20** **0** **20**



**J1550-8258**


**-20** **0** **20**



**J1617-7717**


**-20** **0** **20**



**J1723-7713**


**-20** **0** **20**



**J1733-7935**


**-20** **0** **20**



**VLSR [km s** **[-1]** **]**


Fig. C.1. Spectra of C 2 H absorption. Spectra along 4 sight lines lacking apparent detections are not shown. See Table 1 for quantitative results
and Table 4 for the statistics of detection rates.

**0.1**


**0.0**


**-0.1**


**-0.2**


**0.1**


**0.0**


**-0.1**


**-0.2**


**0.1**


**0.0**


**-0.1**


**-0.2**


**0.1**


**0.0**


**-0.1**


**-0.2**


**0.1**


**0.0**


**-0.1**


**-0.2**



L&G: DNM, dark and molecular gas 17


**J0211+1051** **J0325+2224** **J0356+2903/3** **J0403+2600**


**J0406+0637** **J0407+0742** **J0426+2327/3** **J0431+2037**


**J0433+0521*9** **J0437+2940/3** **J0438+3004/3** **J0439+3045/3**


**J0440+1437** **J0449+1121** **J0502+1338** **J1058-8003*3**



**J1136-6827**


**-20** **0** **20**



**J1145-6954**


**-20** **0** **20**



**J1224-8313**


**-20** **0** **20**



**J1723-7713**


**-20** **0** **20**



**VLSR [km s** **[-1]** **]**


Fig. D.1. ALMA spectra of HCN absorption including all statistically significant detections. Some spectra have been scaled as indicated in
those panels. See Table 1 for quantitative results and Table 4 for the statistics of detection rates.

18 L&G: DNM, dark and molecular gas



**0.00**


**-0.01**


**-0.02**


**-0.03**


**0.01**


**0.00**


**-0.01**


**-0.02**


**-0.03**


**-0.04**


**-0.05**















**-10** **0** **10** **20**

**VLSR [km s** **[-1]** **]**



**0.00**


**-0.01**


**-0.02**


**-0.03**


**0.00**


**-0.05**



**-10** **0** **10** **20**

**VLSR [km s** **[-1]** **]**







**-10** **0** **10** **20**

**VLSR [km s** **[-1]** **]**



**-10** **0** **10** **20**

**VLSR [km s** **[-1]** **]**



Fig. E.1. ALMA spectra of HCO absorption shown as red histograms superposed on scaled profiles of HCO [+] absorption shown as gray
histograms.

L&G: DNM, dark and molecular gas 19


Fig. F.1. Individual spectra used to form the average spectra toward J0426+2327 as discussed in Section 5 and shown in Figure 7. [12] CO (black)
and [13] CO spectra shown in red and scaled upward by factor 5 are shown at left and HCO [+] spectra are shown at right.


</paper>

## Items to check

```json
[
 {
  "path": "data.lines_targeted[0].evidence[1]",
  "value": "HCO+",
  "failed_quote": "where Y_HCO+ is the integrated optical depth of the J=1-0 HCO+ absorption line"
 },
 {
  "path": "data.lines_targeted[5].evidence[0]",
  "value": "12CO",
  "failed_quote": "The integrated emission of the J=1-0 CO line is denoted by W_CO in units of K-kms^-1"
 },
 {
  "path": "data.external_data_from_literature[0].what.evidence[0]",
  "value": "21cm HI emission line profile integrals from the Leiden, Argentine, and Bonn (LAB) All-Sky HI survey",
  "failed_quote": "The lambda21cm HI column densities were derived from the Leiden, Argentine, and Bonn (LAB) All-Sky HI survey Kalberla et al. (et al. 2005)"
 },
 {
  "path": "data.external_data_from_literature[5].what.evidence[0]",
  "value": "HCO abundance toward BL Lac",
  "failed_quote": "BL Lac^2 0.32 0.867 0.85(0.02) 0.98(0.02) ... ^2 Data from Liszt et al. (2014)"
 },
 {
  "path": "processing.inherited[1].what.evidence[0]",
  "value": "C2H column density conversion factor N(C2H) = 2.71 x 10^13 cm^-2 Y_CCH",
  "failed_quote": "N(C2H) = 2.71 x 10^13 cm^-2 Y_CCH as in our earlier survey of C2H absorption (Lucas & Liszt, 2000)"
 },
 {
  "path": "processing.inherited[2].what.evidence[0]",
  "value": "HCN column density conversion factor N(HCN) = 1.89 x 10^12 cm^-2 Y_HCN",
  "failed_quote": "As in earlier work (Liszt & Lucas, 2001), we observed the J=1-0 transition of HCN, whose strongest hyperfine component is at 88.632 GHz, and we derived N(HCN) = 1.89 x 10^12 cm^-2 Y_HCN"
 },
 {
  "path": "processing.inherited[3].what.evidence[0]",
  "value": "Deriving H2 column density as N(H2) = N(HCO+)/3 x 10^-9 and N(HCO+) = 1.10 x 10^12 cm^-2 Y_HCO+ using dipole moment mu = 3.89 Debye",
  "failed_quote": "As is common practice (see Gerin et al. (et al. 2019)), we derived the H2 column densities as N(H2) = N(HCO+)/3 x 10^-9 and N(HCO+) = 1.10 x 10^12 cm^-2 Y_HCO+"
 },
 {
  "path": "processing.inherited[4].what.evidence[0]",
  "value": "Standard Galactic CO-H2 conversion factor N(H2)/W_CO = 2 x 10^20 cm^-2 /(1 K-km s^-1)",
  "failed_quote": "Where reference is made to a typical Galactic or standard CO-H2 conversion factor, the value N(H2)/W_CO = 2 x 10^20 cm^-2 /(1 K-kms^-1) should be understood, as summarized in Table E.1 of Remy et al. (2017)."
 },
 {
  "path": "analysis_steps[0].method.evidence[1]",
  "value": "Extract spectral line profiles from the continuum-peak pixels of standard pipeline datacubes, normalize by the continuum flux in the respective spectral window continuum map, integrate optical depth over the HCO+ line span (or 3 km/s for non-detections), and apply linear conversion factors to derive column densities.",
  "failed_quote": "Upper limits are the 3sigma values measured over the span of the HCO+ line, when given. In the five cases when HCO+ was not observed or not detected, they are given over an arbitrary 3 km s^-1 interval."
 },
 {
  "path": "analysis_steps[0].key_parameters[0].evidence[0]",
  "value": "N(C2H) = 2.71 x 10^13 cm^-2 Y_CCH (with observed F=2-1 and F=1-0 components having 5/8 of total line strength)",
  "failed_quote": "The observed components included 5/8 of the total integrated line strength of the N=1-0 J=3/2-1/2 transition. We define the total as Y_CCH . N(C2H) = 2.71 x 10^13 cm^-2 Y_CCH"
 },
 {
  "path": "analysis_steps[0].key_parameters[1].evidence[0]",
  "value": "N(HCN) = 1.89 x 10^12 cm^-2 Y_HCN",
  "failed_quote": "and we derived N(HCN) = 1.89 x 10^12 cm^-2 Y_HCN where Y_HCN is the integrated optical depth summed over all three hyperfine components."
 },
 {
  "path": "analysis_steps[0].key_parameters[2].evidence[0]",
  "value": "N(HCO+) = 1.10 x 10^12 cm^-2 Y_HCO+ and N(H2) = N(HCO+)/3 x 10^-9",
  "failed_quote": "we derived the H2 column densities as N(H2) = N(HCO+)/3 x 10^-9 and N(HCO+) = 1.10 x 10^12 cm^-2 Y_HCO+"
 },
 {
  "path": "analysis_steps[0].validation.evidence[0]",
  "value": "Confirmed in Section 5.1 that HCO+ excitation temperature is ~2.76 K, validating the limit of no collisional excitation.",
  "failed_quote": "the great majority of channels imply a typical excitation temperature of 2.76 K up to tau = 2. ... Deriving N(HCO+) in the limit of no collisional excitation is a good approximation."
 },
 {
  "path": "analysis_steps[2].method.evidence[1]",
  "value": "Perform power-law linear regressions in log-log space of E_B-V, N(HI), N(H2), and W_CO against sin(|b|), and of molecular column densities against E_B-V, N(HCO+), and N(C2H).",
  "failed_quote": "a and b are fits to log (value of the y-species) = a+bxlog (value of the x-species), and r is the correlation coefficient."
 },
 {
  "path": "analysis_steps[2].key_parameters[0].evidence[0]",
  "value": "N(HI) = 1.823 x 10^18 cm^-2 W_HI",
  "failed_quote": "The lambda21cm HI column densities were derived from the Leiden, Argentine, and Bonn (LAB) All-Sky HI survey Kalberla et al. (et al. 2005) in the optically thin limit as N(HI) = 1.823 x 10^18 cm^-2 W_HI"
 },
 {
  "path": "analysis_steps[2].assumptions[0].evidence[0]",
  "value": "Optically thin 21cm HI emission",
  "failed_quote": "in the optically thin limit as N(HI) = 1.823 x 10^18 cm^-2 W_HI"
 },
 {
  "path": "analysis_steps[2].fitting.evidence[0]",
  "value": "Linear regression of log(y) = a + b log(x)",
  "failed_quote": "a and b are fits to log (value of the y-species) = a+bxlog (value of the x-species), and r is the correlation coefficient."
 },
 {
  "path": "results_numeric[4].evidence[0]",
  "value": "Power-law slope of N(HCO+) vs E_B-V = 1.025 dimensionless",
  "failed_quote": "E_B-V N(HCO+) 73 0.656(0.948) mag 2.130(4.011)x10^12 cm^-2 12.347(0.065) 1.025(0.113) 0.733"
 },
 {
  "path": "results_numeric[5].evidence[0]",
  "value": "Power-law slope of N(C2H) vs E_B-V = 0.828 dimensionless",
  "failed_quote": "N(C2H) 53 0.650(1.040) mag 2.513(3.930)x10^13 cm^-2 13.477(0.062) 0.828(0.105) 0.74"
 },
 {
  "path": "results_numeric[6].evidence[0]",
  "value": "Power-law slope of N(HCN) vs E_B-V = 1.355 dimensionless",
  "failed_quote": "N(HCN) 38 0.754(1.176) mag 3.641(7.347)x10^12 cm^-2 12.410(0.106) 1.355(0.197) 0.74"
 },
 {
  "path": "results_numeric[7].evidence[0]",
  "value": "Power-law slope of N(C2H) vs N(HCO+) = 0.667 dimensionless",
  "failed_quote": "N(HCO+) N(C2H) 51 2.469(0.456)x10^12 cm^-2 2.619(4.018)x10^13 cm^-2 5.138(0.799) 0.667(0.066) 0.82"
 },
 {
  "path": "results_numeric[8].evidence[0]",
  "value": "Power-law slope of N(HCN) vs N(HCO+) = 1.248 dimensionless",
  "failed_quote": "N(HCN) 39 2.987(5.093)x10^12 cm^-2 3.732(7.419)x10^12 cm^-2 -3.152(0.726) 1.248(0.060) 0.96"
 },
 {
  "path": "results_numeric[9].evidence[0]",
  "value": "Mean relative abundance <N(HCN)>/<N(HCO+)> = 1.25 dimensionless",
  "failed_quote": "The current sample mean is <N(HCN)> / <N(HCO+)>= 1.25 +-0.06"
 },
 {
  "path": "results_numeric[19].evidence[0]",
  "value": "Total neutral hydrogen number density n(H) in host gas = 50-200 cm^-3",
  "failed_quote": "The comparison of HCO+ emission and absorption along 7 sight lines yielded a typical HCO+ excitation temperature of 2.76 K and total neutral hydrogen number densities n(H) of approx 50 - 200 cm^-3."
 },
 {
  "path": "findings_qualitative[2].evidence[0]",
  "value": "HCN is uniformly detected down to N(HCO+) ~ 3 x 10^11 cm^-2 (N(H2) = 10^20 cm^-2) without an abrupt break in the HCN-HCO+ power-law slope.",
  "failed_quote": "HCN is detected down to N(HCO+) <= 4 x 10^11 cm^-2 with a tight correlation (r = 0.95) and without a break in the power-law slope (1.25 +- 0.06) of the HCN-HCO+ relation."
 },
 {
  "path": "findings_qualitative[2].evidence[1]",
  "value": "HCN is uniformly detected down to N(HCO+) ~ 3 x 10^11 cm^-2 (N(H2) = 10^20 cm^-2) without an abrupt break in the HCN-HCO+ power-law slope.",
  "failed_quote": "HCN is detected almost without exception down to N(HCO+) = 3 x 10^11 cm^-2 or N(H2) = 10^20 cm^-2, in contrast to earlier results that implied that N(HCN)/N(HCO+) increased abruptly at N(HCO+) = 10^12 cm^-2."
 },
 {
  "path": "findings_qualitative[3].evidence[1]",
  "value": "Nearly half of the total H2 traced by HCO+ occurs in channels with 12CO brightness <= 2 K and 12CO/13CO brightness ratios >= 20, indicating diffuse, unsaturated CO gas.",
  "failed_quote": "Nearly half of the total amount of H2 arises in line channels with a CO brightness of <= 2 K (Figure 9, left)"
 },
 {
  "path": "claims[0].evidence[0]",
  "value": "Confirmed that C2H is ubiquitous and N(C2H)/N(HCO+) increases significantly at smaller E_B-V and smaller N(HCO+).",
  "failed_quote": "The slope of the power-law fit to N(C2H), 0.83 +- 0.10, is noticeably shallower than that of HCO+ . This indicates an increase in N(C2H)/N(HCO+) at smaller E_B-V that was reported earlier (Lucas & Liszt, 2000)."
 },
 {
  "path": "claims[1].evidence[0]",
  "value": "Refuted the abrupt jump; HCN is uniformly present down to N(H2) = 10^20 cm^-2 without a break in the power-law relation.",
  "failed_quote": "HCN is detected down to N(HCO+) <= 4 x 10^11 cm^-2 with a tight correlation (r = 0.95) and without a break in the power-law slope (1.25 +- 0.06) of the HCN-HCO+ relation. Earlier, sparser data (Figure 3 of Lucas & Liszt (2002)) seemed to show an abrupt increase in N(HCN) at N(HCO+) approx 10^12 cm^-2."
 },
 {
  "path": "claims[2].evidence[1]",
  "value": "HCO is ubiquitous in the diffuse ISM with N(HCO)/N(HCO+) = 1/3, and was detected wherever sensitivity was sufficient.",
  "failed_quote": "There were 4 directions like this among the 46 observations in which HCO was observed in this work, and HCO was detected above the 2sigma level with a relative abundance N(HCO)/N(H2) = 1.1 - 1.3 x 10^-9 along four sight lines"
 },
 {
  "path": "claims[3].evidence[1]",
  "value": "HCN line widths are slightly narrower than matching HCO+ features (similar to CO), whereas C2H features are broader.",
  "failed_quote": "the matched HCN components were found to be 5% narrower on average (0.975 versus 1.032 km s^-1). ... and the matched C2H components are 12% broader, 1.12 versus 1.03 km s^-1."
 },
 {
  "path": "claims[4].evidence[0]",
  "value": "Collisional excitation of HCO+ is very weak, validating the assumption of no collisional excitation when deriving N(HCO+) from absorption, and placing the host gas at n(H) ~ 50-200 cm^-3.",
  "failed_quote": "The comparison of HCO+ emission and absorption along 7 sight lines yielded a typical HCO+ excitation temperature of 2.76 K and total neutral hydrogen number densities n(H) of approx 50 - 200 cm^-3."
 },
 {
  "path": "claims[4].evidence[1]",
  "value": "Collisional excitation of HCO+ is very weak, validating the assumption of no collisional excitation when deriving N(HCO+) from absorption, and placing the host gas at n(H) ~ 50-200 cm^-3.",
  "failed_quote": "the great majority of channels imply a typical excitation temperature of 2.76 K up to tau = 2. ... Deriving N(HCO+) in the limit of no collisional excitation is a good approximation."
 },
 {
  "path": "reasoning.limitations_admitted[1].evidence[1]",
  "value": "The sample is an inhomogeneous amalgamation of datasets taken over 30 years with different selection criteria and is biased toward higher reddening and molecular gas content than the Galactic average.",
  "failed_quote": "The sample values of E_B-V lie above the Galactic average at all latitudes and do not show the same steep decline until |b| >= 44^o . Thus, the sample is noticeably rich in dust and gas."
 },
 {
  "path": "reasoning.limitations_admitted[2].evidence[0]",
  "value": "Integration times were too short to provide useful upper limits on CS chemistry at E_B-V <= 0.5 mag.",
  "failed_quote": "They are, however, too high to provide useful information for the CS chemistry of the sight lines at E_B-V <= 0.5 mag given the plot in the lower right panel in Fig. 3."
 }
]
```
