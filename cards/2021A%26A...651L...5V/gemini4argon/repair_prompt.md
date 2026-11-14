# Repair task for a Claude Code subagent

A methods card has evidence quotes that were not found verbatim in the paper. Below are the rules, the paper, and the failing items. Write ONE JSON object, nothing else, of the form {"repairs": [{"path": ..., "found": true|false, "loc": ..., "quote": ...}, ...]} with one entry per item (path unchanged) to:

    C:\Users\adama\alma-corpus\cards\2021A%26A...651L...5V\gemini4argon\repair_reply.txt

Use the Write tool for that file. Copy each quote character for character from the paper text below; a returned quote is checked mechanically and dropped if it is not in the paper. Do not read any other file, do not run commands, and do not change anything else. Reply with one line when done.

---

## Rules

You check evidence quotes for a methods card extracted from an astronomy paper. Some quotes could not be found verbatim in the paper text, and some stated values came without a quote. For each item: find the passage in the paper that supports the value and copy it VERBATIM (same words and order, at most 40 words; LaTeX markup may be dropped) with its loc (section heading, "abstract", "Table N" or "Figure N caption"). If the paper does not support the value, return found = false and leave quote and loc empty. Use only the paper text. Return one entry per item, with the item's path unchanged.

## Paper

<paper>
_Astronomy & Astrophysics_ manuscript no. Paper_final ©ESO 2021
June 11, 2021


Letter to the Editor

## **A major asymmetric ice trap in a planet-forming disk:** **I. Formaldehyde and methanol**


Nienke van der Marel [1][,][ 2], Alice S. Booth [3], Margot Leemker [3], Ewine F. van Dishoeck [3][,][ 4], and Satoshi Ohashi [5]


1 Physics & Astronomy Department, University of Victoria, 3800 Finnerty Road, Victoria, BC, V8P 5C2, Canada
2 Banting Research fellow
3 Leiden Observatory, Leiden University, 2300 RA Leiden, the Netherlands
4 Max-Plank-Institut fur Extraterrestrische Physik, Giessenbachstraße 1, D-85748 Garching, Germany
5 RIKEN Cluster for Pioneering Research, 2-1, Hirosawa, Wako-shi, Saitama 351-0198, Japan


Received April, 2021; accepted June, 2021


**ABSTRACT**


_Context._ The chemistry of planet-forming disks sets the exoplanet atmosphere composition and the prebiotic molecular content. Dust
traps are of particular importance as pebble growth and transport are crucial for setting the chemistry where giant planets are forming.
_Aims._ The asymmetric Oph IRS 48 dust trap located at 60 au radius provides a unique laboratory for studying chemistry in pebbleconcentrated environments in warm Herbig disks with low gas-to-dust ratios down to 0.01.
_Methods._ We use deep ALMA Band 7 line observations to search the IRS 48 disk for H 2 CO and CH 3 OH line emission, the first steps
of complex organic chemistry.
_Results._ We report the detection of 7 H 2 CO and 6 CH 3 OH lines with energy levels between 17 and 260 K. The line emission shows
a crescent morphology, similar to the dust continuum, suggesting that the icy pebbles play an important role in the delivery of these
molecules. Rotational diagrams and line ratios indicate that both molecules originate from warm molecular regions in the disk with
temperatures >100 K and column densities ∼ 10 [14] cm [−][2] or a fractional abundance of ∼ 10 [−][8] and with H 2 CO/CH 3 OH∼0.2, indicative
of ice chemistry. Based on arguments from a physical-chemical model with low gas-to-dust ratios, we propose a scenario where the
dust trap provides a huge icy grain reservoir in the disk midplane or an ‘ice trap’, which can result in high gas-phase abundances of
warm COMs through efficient vertical mixing.
_Conclusions._ This is the first time that complex organic molecules have been clearly linked to the presence of a dust trap. These results
demonstrate the importance of including dust evolution and vertical transport in chemical disk models, as icy dust concentrations
provide important reservoirs for complex organic chemistry in disks.



**Key words.** Astrochemistry – Protoplanetary disks


**1.** **Introduction**


Protoplanetary disks around young stars are the birth cradles of
planets, and the chemical composition in these disks sets the
exoplanet atmospheric composition and the formation of prebiotic molecules on their surfaces (Ehrenfreund & Charnley 2000;
Öberg & Bergin 2021). So far, mostly simple molecules have
been detected in disks (e.g. Dutrey et al. 1997; Thi et al. 2004;
Öberg et al. 2010, 2015; Walsh et al. 2016), and their abundances
are set by photodissociation in the surface layers and freeze-out
in the midplane (Bergin et al. 2007). Complex organic molecules
(COMs) may be present but are expected to be mostly locked up
in ices. CO ice chemistry is crucial for the formation of complex
organic molecules which can be thermally released into the gasphase (Herbst & van Dishoeck 2009). For Herbig disks, COMs
cannot form in situ since they are warm and lack a large COice reservoir (Agúndez et al. 2018). Surprisingly, CH 3 OH was
recently detected in the Herbig disk HD100546 (Booth et al.
2021). This detection can be understood when CH 3 OH ice is inherited from earlier stages, followed by radial transport and sublimation at its iceline. Pebble growth and transport are known
to play an important role in the chemical composition of disks
and resulting exoplanet atmospheres (Cridland et al. 2017; Krijt
et al. 2020). The connection between pebbles and ice chemistry



can be studied directly in so-called dust traps (concentrations of
dust grains), possibly revealing a much richer chemistry as dust
rings are colder in the midplane (Alarcón et al. 2020) while exposed dust cavity walls can reveal sublimated midplane products
(Cleeves et al. 2011; Mulders et al. 2011).
Dust traps are thought to be the main explanation for the
observed narrow dust rings and asymmetries in high-resolution
ALMA observations revealing also a segregation between gas
and dust (e.g. van der Marel et al. 2013; Pérez et al. 2014; Andrews et al. 2018). Pressure bumps at gap edges trap larger dust
grains due to drag forces between gas and dust (Weidenschilling
1977), which can explain the appearance of dust rings in protoplanetary disks as the dust is prevented from drifting inwards
(Pinilla et al. 2012a). In some cases, the pressure bump can become susceptible to the Rossby Wave Instability and form longlived vortices (Barge & Sommeria 1995), which trap the dust in
the azimuthal direction. The Herbig disk Oph IRS 48 is a textbook example of such a dust trap showing an asymmetric dust
concentration south of the star (van der Marel et al. 2013, 2015),
and thus an ideal target for studying complex organic chemistry
in a pebble-concentrated environment.
The presence of warm H 2 CO in the IRS 48 disk was discovered by van der Marel et al. (2014). H 2 CO is a precursor of more
complex organic molecules such as CH 3 OH through CO ice hy

Article number, page 1 of 16

_A&A proofs:_ manuscript no. Paper_final


**Table 1.** Detected molecular lines, line properties and disk integrated fluxes


Molecule Transition Rest frequency _E_ _u_ _g_ _u_ log _A_ _ul_ _F_ _int_
(GHz) (K) (mJy km s [−][1] )
o-H 2 CO 5 1,5 -4 1,4 351.768648 62 33 -2.92013 836
o-H 2 CO 5 3,3 -4 3,2 364.275141 158 33 -3.05097 391
o-H 2 CO 5 3,2 -4 3,1 364.288914 158 33 -3.05065 574
p-H 2 CO 5 0,5 -4 0,4 362.736024 52 11 -2.86264 577
p-H 2 CO 5 2,4 -4 2,3 363.945876 100 11 -2.93377 377
p-H 2 CO 5 4,2 -4 4,1 /5 4,1 -4 4,0 _[a]_ 364.103257 241 11 -3.30139 99
a-CH 3 OH 14 1,13 -14 0,14 349.106997 260 116 -3.35603 198
a-CH 3 OH 1 1,1 -0 0,0 350.905100 17 12 -3.47949 89
e-CH 3 OH 4 0,4 -3 −1,3 350.687651 36 36 -4.06195 215
e-CH 3 OH 7 −2,6 -6 −1,5 363.739868 87 60 -3.76767 141
e-CH 3 OH 8 1,7 -7 2,5 361.852195 105 68 -4.11248 125
e-CH 3 OH 11 0,11 -10 1,9 360.848946 166 92 -3.91831 155
_a_ Lines are blended.
Rest frequencies and other properties are taken from CDMS: _E_ _u_ is the upper energy level,
_g_ _u_ the degeneracy and _A_ _ul_ the Einstein _A_ -coefficient.



drogenation (e.g. Watanabe & Kouchi 2002; Fuchs et al. 2009).
The morphology appeared to be cospatial with the dust crescent,
but the detection was tentative. CH 3 OH was not detected in this
work, but upper limits were derived. The H 2 CO/CH 3 OH abundance ratio can be used as tracer for the formation mechanism
(Garrod et al. 2006), since CH 3 OH can only be formed efficiently through ice chemistry, whereas H 2 CO has both an iceand gas-phase route (e.g. Walsh et al. 2014). Gas-phase dominated H 2 CO formation implies a ratio>1 and ice-phase a ratio<1.
However, the derived H 2 CO/CH 3 OH ratio from van der Marel
et al. (2014) of ≳0.3 was inconclusive about the formation mechanism.

Whereas H 2 CO has been routinely detected in a range of
protoplanetary disks (e.g. Pegues et al. 2020), CH 3 OH has only
been detected in the TW Hya disk (Walsh et al. 2016), the young
IRAS04302 disk (Podio et al. 2020) and outburst disk V883 Ori
(van ’t Hoff et al. 2018; Lee et al. 2019) and recently in the Herbig disk HD100546 (Booth et al. 2021).
In this work, we present the detection of multiple CH 3 OH
and H 2 CO transitions in the IRS 48 system, only the second Herbig disk with observed COMs and the first disk where the COM
production can be linked directly to the dust trap.


**2.** **Observations**


Oph IRS 48 is an A0 star located in the Ophiuchus cloud at a
distance of 135 pc (Gaia Collaboration et al. 2018). This disk,
inclined at 50 [◦], shows an asymmetric millimeter-dust concentration at 60 au, in contrast with a full ring in gas and small
dust grains (van der Marel et al. 2013) and has an estimated
gas disk mass of only 0.6 _M_ Jup (van der Marel et al. 2016).
IRS 48 has been observed using the Atacama Large Millimeter/submillimeter Array (ALMA) in Band 7 in polarization mode
in Cycle 5 in August 2018 (2017.1.00834.S, PI:Adriana Pohl).
The continuum polarization data are presented by Ohashi et al.
(2020), and the main calibration and reduction process is described in detail in that work. The total on-source integration
time is 89 minutes. The continuum is subtracted in the uv-plane
using the CASA task `uvcontsub` with a first order polynomial. The spectral setup contains four spectral windows at 349.7,
351.5, 361.6 and 363.5 GHz, with a bandwidth of 1875 GHz in
each window and a channel width of 1953 kHz or ∼1.6 km s [−][1] .


Article number, page 2 of 16



Seven H 2 CO and six CH 3 OH transitions were identified
using the matched-filter-technique (Loomis et al. 2018), listed
in Table 1, for _E_ _u_ levels between 17 and 260 K. H 2 CO transitions are identified as ortho (o-) and para (p-) transitions,
respectively. Each line was imaged using the `tclean` task
at the channel resolution, using natural weighting. The final
channel cubes have a beam size of 0.63×0.50" and a rms
noise of σ rms ∼1.2 mJy beam [−][1] channel [−][1] . The brightest lines
(H 2 CO 5 0,5 − 4 0,4 and CH 3 OH 4 0,4 − 3 1,3 ) are also imaged using Briggs weighting with a robust of 0.5 for a resolution of
0.55×0.44".

Spectra are extracted from the naturally weighted cubes using Keplerian masking (using _d_ =135 pc, _i_ =50 [◦] and _M_ ∗ =2.0 _M_ ⊙ )
and presented in Figure A.1. All cubes show a clear Keplerian
pattern along the southern part of the disk. Some lines are located adjacent to other lines, i.e. the H 2 CO 5 3,3 -4 3,2 and 5 3,2 -4 3,1
transitions, so their line wings overlap in 2 channels.
The disk-integrated spectra are resolved even at our low
spectral resolution, ranging from -2 to 12 km s [−][1] with
_v_ source =4.55 km s [−][1] . The CH 3 OH lines appear to have somewhat
more prominent line wings (corresponding to an inner 30 au radius) than the H 2 CO lines. The spectra are integrated over the
entire individual profiles (avoiding overlap with adjacent features) and the disk integrated fluxes are reported in Table 1.
The H 2 CO 5 4,2 -4 4,1 and 5 4,1 -4 4,0 fluxes are computed by dividing
their shared flux by 2. The integrated fluxes are detected with a
range between 5 and 42σ int, with σ int ∼20 mJy km s [−][1], whereas
the calibration uncertainty is 10%.
Zero-moment maps are created using Keplerian masking
and presented in Figure A.2. The central position is set at
J2000 16h27m37.180s, -24 [◦] 30’35.48", based on Gaia DR2
(Gaia Collaboration et al. 2018). Spectra and moment maps of
the two brightest lines are presented in Figure 1.


**3.** **Results**


Both H 2 CO and CH 3 OH lines are firmly detected. IRS 48 is the
second known Herbig disk with a detection of CH 3 OH, following HD 100546 (Booth et al. 2021). It is immediately clear that
both molecules follow the dust trap morphology (Figure 1), in
contrast with [13] CO which shows a full disk ring, just like the
small grains (van der Marel et al. 2013). This confirms the find

Nienke van der Marel et al.: A major asymmetric ice trap in a planet-forming disk: I. Formaldehyde and methanol







































v (km s 1 )















v (km s 1 )













v (km s 1 )



**Fig. 1.** Overview of the brightest H 2 CO and CH 3 OH lines using Briggs weighting, the 336 GHz continuum and the [13] CO 6-5 map with a similar
beam size for comparison. The top row shows the zero-moment maps, the middle row the continuum and the first moment maps and the bottom
row the disk integrated spectra. The µm-sized grain distribution as traced by 19 µm VISIR data (Geers et al. 2007) is indicated in the continuum
image. The source velocity is indicated by a vertical dotted line. The grey shades indicate the noise levels in the spectra.



ings of van der Marel et al. (2014) of their suggested location of
the H 2 CO emission.

Figure 1 presents the data for the two brightest line transitions: the H 2 CO 5 1,5 − 4 1,4 and the CH 3 OH 4 0,4 − 3 0,3 lines. The
maps are compared with the 355 GHz continuum from the same
dataset and with the [13] CO 6–5 intensity maps. The [13] CO data
are taken from van der Marel et al. (2016) and imaged using uvtapering for a similar beam size as the Band 7 data presented
here. The first-moment maps of the H 2 CO and CH 3 OH emission
are consistent with Keplerian motion along the southern half of
the disk.

A comparison between the images in both the radial and azimuthal directions is presented in Figure 2. The profiles are extracted by deprojecting the zero-moment maps assuming a position angle of 100 [◦] and an inclination of 50 [◦] (Bruderer et al.
2014). The azimuthal profile is extracted at the dust peak radius
of 62 au with a radial width of 60 au and the radial profile at the
peak φ of 192 [◦] East-of-North with an azimuthal width of 100 [◦] .
For [13] CO, the data are extracted around the peak radius of 35 au
and the peak φ of 269 [◦] .
The azimuthal profiles show that H 2 CO is azimuthally more
extended than CH 3 OH and is trailing the dust trap, whereas



CH 3 OH is similar in width as the continuum emission. In contrast, the [13] CO emission is present along the entire ring, with a
dip around the continuum peak due to continuum oversubtraction (the Band 9 continuum peak is azimuthally shifted w.r.t.
to the Band 7 continuum due to different grain sizes traced).
The Band 7 line data presented here are only moderately affected by continuum oversubtraction. Radially, the H 2 CO profile
is cospatial with the continuum emission, although the emission
remains radially unresolved. In contrast, the CH 3 OH profile appears somewhat further extended outwards and based on the line
wings, also inwards. The [13] CO emission peaks radially inside
the dust continuum peak.


**4.** **Analysis**


With multiple line transitions it is possible to derive the column
density and excitation temperature for both molecules under the
assumption of LTE and optically thin emission (or a correction
for optical depth). The optical depth is determined first using the
expected emission from the emitting area. As the zero-moment
maps of H 2 CO and CH 3 OH are marginally resolved, the emitting area cannot be reliably determined from these images. In

Article number, page 3 of 16

_A&A proofs:_ manuscript no. Paper_final





1.0


0.8


0.6


0.4


0.2


0.0


1.0


0.8


0.6


0.4


0.2


0.0


|Col1|Radial profiles|Col3|Col4|Col5|Col6|Col7|Col8|
|---|---|---|---|---|---|---|---|
||Continuum<br>13CO 6-5<br>H2CO 51, 5<br>41, 4<br>CH3OH 40, 4<br>3<br>1, 3<br>beam|Continuum<br>13CO 6-5<br>H2CO 51, 5<br>41, 4<br>CH3OH 40, 4<br>3<br>1, 3<br>beam|Continuum<br>13CO 6-5<br>H2CO 51, 5<br>41, 4<br>CH3OH 40, 4<br>3<br>1, 3<br>beam|Continuum<br>13CO 6-5<br>H2CO 51, 5<br>41, 4<br>CH3OH 40, 4<br>3<br>1, 3<br>beam|Continuum<br>13CO 6-5<br>H2CO 51, 5<br>41, 4<br>CH3OH 40, 4<br>3<br>1, 3<br>beam|Continuum<br>13CO 6-5<br>H2CO 51, 5<br>41, 4<br>CH3OH 40, 4<br>3<br>1, 3<br>beam|Continuum<br>13CO 6-5<br>H2CO 51, 5<br>41, 4<br>CH3OH 40, 4<br>3<br>1, 3<br>beam|
|||||||||
|||||||||
|||||||||
|||||||||
|||||||||
|||||||||














|Col1|0 50 100 150 200 250 r (au) H2CO 51, 5 41, 4 beam Azimuthal profiles|Col3|Col4|Col5|Col6|Col7|Col8|Col9|Col10|
|---|---|---|---|---|---|---|---|---|---|
||beam<br>Continuum<br>13CO 6-5<br>H2CO 51, 5<br>41, 4<br>CH3OH 40, 4-<br>3<br>1, 3|beam<br>Continuum<br>13CO 6-5<br>H2CO 51, 5<br>41, 4<br>CH3OH 40, 4-<br>3<br>1, 3|beam<br>Continuum<br>13CO 6-5<br>H2CO 51, 5<br>41, 4<br>CH3OH 40, 4-<br>3<br>1, 3|beam<br>Continuum<br>13CO 6-5<br>H2CO 51, 5<br>41, 4<br>CH3OH 40, 4-<br>3<br>1, 3|beam<br>Continuum<br>13CO 6-5<br>H2CO 51, 5<br>41, 4<br>CH3OH 40, 4-<br>3<br>1, 3|beam<br>Continuum<br>13CO 6-5<br>H2CO 51, 5<br>41, 4<br>CH3OH 40, 4-<br>3<br>1, 3|beam<br>Continuum<br>13CO 6-5<br>H2CO 51, 5<br>41, 4<br>CH3OH 40, 4-<br>3<br>1, 3|beam<br>Continuum<br>13CO 6-5<br>H2CO 51, 5<br>41, 4<br>CH3OH 40, 4-<br>3<br>1, 3|beam<br>Continuum<br>13CO 6-5<br>H2CO 51, 5<br>41, 4<br>CH3OH 40, 4-<br>3<br>1, 3|
|||||||||||
|||||||||||
|||||||||||
|||||||||||
|||||||||||
|||||||||||



0 50 100 150 200 250 300 350

( )


**Fig.** **2.** Radially and azimuthally averaged profiles of the brightest
H 2 CO and CH 3 OH lines from the Briggs weighted images, combined
with the profiles from [13] CO 6-5 and the 355 GHz continuum imaged at
the same beam size of 0.55×0.44".


stead, the emitting area is determined using the high resolution
(0.18×0.14") Band 7 continuum image (Francis & van der Marel
2020, and Figure A.3), with the underlying assumption that the
H 2 CO and CH 3 OH emission follow the morphology of the dust
crescent. Although the H 2 CO emission is azimuthally more extended than the continuum, the difference is marginal (∼20% in
the convolved images) and can be ignored. The emitting area of
the high-resolution continuum is 1.4·10 [−][11] sr with a 5σ threshold.

Using this emitting area, the optical depth τ and the column
densities of individual levels _N_ _u_ are estimated following the excitation equations in Loomis et al. (2018). All lines are optically
thin with τ < 0.1 for _T_ >100 K. The ortho-to-para ratio of H 2 CO
in the degeneracies and partition functions is taken as 3, and the


Article number, page 4 of 16



A/E ratio of CH 3 OH as 1. The column density _N_ _T_ and temperature _T_ rot are estimated by fitting the rotational diagrams using the
`emcee` package to compute the posterior distributions (ForemanMackey et al. 2013), assuming optically thin emission. Our bestfit results are shown in Figure 3 and indicate an average column density of 7.7±0.5 - 10 [13] cm [−][2] and 4.9±0.2 - 10 [14] cm [−][2],
and a rotational temperature of 173 [+] − [11] 9 [and] [103] [+] − [6] 5 [K] [for] [H] [2] [CO]
and CH 3 OH, respectively (see Figure B.1). This implies that the
temperature of H 2 CO is higher than CH 3 OH and the abundance
ratio H 2 CO/CH 3 OH is 0.16±0.01, much lower than found for
other disks (Booth et al. 2021), and suggestive of ice-dominated
chemistry. However, it is possible that the transitions trace multiple regimes with different temperatures in the disk. Furthermore,
the ortho-to-para ratio obtained by fitting the ortho and para lines
separately is <3, which is potentially pointing to an ice formation route as well (Terwisscha van Scheltinga et al. 2021), but
could also be caused by optical depth (see Appendix B). The
gas surface density derived by van der Marel et al. (2016) at 60
au radius corresponds to _N_ H 2 ∼ 1.6 · 10 [22] cm [−][2], so the relative
abundances of H 2 CO and CH 3 OH are ∼ 10 [−][8] w.r.t. H 2, consistent with previous estimates by van der Marel et al. (2014).
The excitation temperature (rotational temperature) is equal
to the kinetic temperature under the assumption of LTE at high
densities. H 2 CO lines are particularly good diagnostics of kinetic
temperature, since radiative transitions are not allowed between
the different _K_ _p_ ladders. The relative populations of those ladders
are therefore dominated by collisions only (Mangum & Wootten
1993; van Dishoeck et al. 1993). The LTE assumption and corresponding kinetic temperature can be tested using a calculation of
the balance between excitation and de-excitation using RADEX
(van der Tak et al. 2007). Collisional rate coefficients are taken
from the LAMDA database for the individual molecules (Rabli
& Flower 2010; Wiesenfeld & Faure 2013) as summarized in
Schöier et al. (2005). We compute line ratios for a range of temperatures and H 2 densities and a molecular column density of
10 [14] cm [−][2] shown in Figure C.3 following van Dishoeck et al.
(1995).
The H 2 densities in the midplane and molecular layers of
IRS 48 are ∼ 10 [6][−][8] cm [−][3] (Bruderer et al. 2014). In this regime,
the line ratios are only sensitive to temperature, with typical inferred values of 200±50 K for H 2 CO and 100±20 K for CH 3 OH,
confirming that the H 2 CO emission originates from a warmer
layer (Fig. C.3).


**5.** **Discussion and conclusions**


The strong detection of CH 3 OH and its precursor H 2 CO in
IRS 48 challenge current chemical disk models, which predict
that Herbig disks cannot form COMs in situ due to their warmer
midplane (Agúndez et al. 2018). IRS 48 is the second mature Herbig disk with a CH 3 OH detection, following HD100546
(Booth et al. 2021). The derived H 2 CO/CH 3 OH abundance ratio of ∼0.2 in IRS 48 indicates that ice chemistry must be the
primary formation mechanism. The warm excitation temperatures >100 K indicates that the emission does not originate from
the disk midplane which has a temperature of ∼70 K at 60 au
(Bruderer et al. 2014). The continuum brightness temperature
at 355 GHz is 27 K, providing a lower limit. H 2 CO may originate from slightly higher layers than CH 3 OH considering its rotational temperature.
An important clue for the origin of the COM chemistry in
IRS 48 is the striking crescent morphology of the emission,
which is following the shape of the dust continuum. The asymmetric dust continuum has been interpreted as a dust trap, based

Nienke van der Marel et al.: A major asymmetric ice trap in a planet-forming disk: I. Formaldehyde and methanol



26


25


24


23


22


26


25


24


23


22






|Col1|H2CO|Col3|Col4|Col5|Col6|Col7|
|---|---|---|---|---|---|---|
||NT = 7.7 ± 0.5 1013 cm<br>2<br>Trot = 173+11<br>9  K<br>ortho<br>para|NT = 7.7 ± 0.5 1013 cm<br>2<br>Trot = 173+11<br>9  K<br>ortho<br>para|NT = 7.7 ± 0.5 1013 cm<br>2<br>Trot = 173+11<br>9  K<br>ortho<br>para|NT = 7.7 ± 0.5 1013 cm<br>2<br>Trot = 173+11<br>9  K<br>ortho<br>para|NT = 7.7 ± 0.5 1013 cm<br>2<br>Trot = 173+11<br>9  K<br>ortho<br>para|NT = 7.7 ± 0.5 1013 cm<br>2<br>Trot = 173+11<br>9  K<br>ortho<br>para|
||||||||
||||||||
||||||||
||||||||
||||||||
||||||||


|Col1|CH3OH|Col3|Col4|Col5|Col6|Col7|
|---|---|---|---|---|---|---|
||NT = 4.9 ± 0.2 1014 cm<br>2<br>Trot = 103+6<br>5 K|NT = 4.9 ± 0.2 1014 cm<br>2<br>Trot = 103+6<br>5 K|NT = 4.9 ± 0.2 1014 cm<br>2<br>Trot = 103+6<br>5 K|NT = 4.9 ± 0.2 1014 cm<br>2<br>Trot = 103+6<br>5 K|NT = 4.9 ± 0.2 1014 cm<br>2<br>Trot = 103+6<br>5 K|NT = 4.9 ± 0.2 1014 cm<br>2<br>Trot = 103+6<br>5 K|
||||||||
||||||||
||||||||
||||||||
||||||||
||||||||



0 50 100 150 200 250 300

E u (K)


**Fig. 3.** Rotational diagrams of H 2 CO and CH 3 OH using the integrated
fluxes from this study, assuming optically thin emission. The integrated
flux of the H 2 CO 9 1,8 -8 1,7 transition from van der Marel et al. (2014) is
included as a lower limit. The red line provides the best fit through the
data points and the grey lines are draws from the posterior distribution
from the fitting (Figure B.1).


on the comparison between large grains, small grains and gas
(van der Marel et al. 2013). The high degree of chemical complexity may thus be related to special physical conditions there.
Large grains concentrate in a dust trap and grow efficiently to
larger sizes due to the higher dust concentration and lower destructive collision efficiency (Weidenschilling 1977; Brauer et al.
2008; Pinilla et al. 2012b). Small grains are still continuously
produced by fragmentation. The dust trap thus provides a large
reservoir of icy dust grains, and if these have been either radially transported from the outer part of the disk or inherited from
the early, colder stages they might be rich in ices (Krijt et al.
2020; Booth et al. 2021). The dust trap thus acts as an ‘ice trap’
of large icy dust grains, as previously suggested for TW Hya
(Walsh et al. 2016). Considering typical interstellar ice abundances of CH 3 OH of 3 · 10 [−][6] (Boogert et al. 2015) and model



COM ice abundances in the disk midplane of ≥10 [−][6] (Walsh et al.
2014), only a fraction of the ice content is sublimated.
The dust density distribution in the dust trap plays a crucial
role here, as dust grains limit the UV field penetration in the disk,
lowering the dust and gas temperature (Bruderer et al. 2012).
Ohashi et al. (2020) derived a dust surface density as high as 28 g cm [−][2] at the dust trap radius based on polarization continuum
measurements and constraints from the centimeter emission in
IRS 48. This is well above the gas surface density of 0.07 g cm [−][2]
derived from CO isotopologues and DALI modelling by van der
Marel et al. (2016), implying a dust-to-gas ratio ≫1. Using a
series of physical-chemical models with different dust surface
densities, we estimate the temperature in the disk at the location
of the dust trap. Two sets of models are run: first, only the dust
density of the large grains in the midplane is increased (settled
models) and second, the dust density is increased throughout the
column (full models). The details of the vertical and radial structure of gas and dust of the models are described in Appendix
C.
Figure 4 shows the midplane temperature profiles and the
vertical gas temperature profiles at 65 au (away from the edge),
based on the model output (Figure C.1-C.2). The gas temperature is coupled to the dust temperature in the midplane, up to
_z_ / _r_ ≲ 0.15. Figure 4 demonstrates that the midplane temperature may get as low as 40 K in the dust trap, well below the
H 2 CO sublimation temperature of 66 K (Penteado et al. 2017).
The temperature is unlikely to be below the CO freezeout temperature of 22 K, so continuous formation of H 2 CO and CH 3 OH
through CO ice hydrogenation is not possible. However, the dust
trap contains a very large reservoir of icy grains. In order to
sublimate, icy grains containing H 2 CO and CH 3 OH need to be
vertically transported to the higher, warmer layers in the disk.
The right panel in Figure 4 shows that the temperature reaches
>100 K at a height of _z_ / _r_ ∼0.2 for the settled models, in the
emitting layer of H 2 CO and CH 3 OH. The full models reach temperature of only 80 K, not high enough to explain the observed
excitation temperatures, suggesting that the high dust concentration of large dust grains must be settled to the midplane. We note
that the gas temperature in the warm molecular layer in IRS48 is
estimated as 250-350 K from mid-J rotational CO lines (Fedele
et al. 2016), and also that the brightness temperature of the [13] CO
6–5 line is as high as ∼200 K (van der Marel et al. 2016).
This distribution of icy dust grains and molecules requires
efficient vertical transport in the disk which can be achieved by
turbulent mixing (Semenov & Wiebe 2011). In addition, the dynamics of the vortex itself may play a role, as both the vertical shear instability (Flock et al. 2020) and meridional flows
(Meheut et al. 2010) in vortices increase the vertical mixing. The
full scenario of the ice reservoir, mixing and sublimation is summarized in the bottom panels of Figure 4.
The morphology of the COM emission suggests that the
combination of a concentration of icy dust pebbles and the irradiation of the cavity wall (resulting in a thin layer of thermal sublimation as proposed by Cleeves et al. 2011) increase the chemical complexity in IRS 48. It is also important to point out that
the COM emission is unlikely to trace an actual azimuthal gas
overdensity in the disk: considering the high SNR, the azimuthal
contrast would have to be more than a factor of 10, and such a
contrast was not detected in the C [18] O 6-5 isotopologue emission
(van der Marel et al. 2016), which is optically thin considering
the ratio of 4.3±1.4 with the C [17] O flux measured by Bruderer
et al. (2014).
The difference in azimuthal extent between H 2 CO and
CH 3 OH could be explained by the lower desorption tempera

Article number, page 5 of 16

_A&A proofs:_ manuscript no. Paper_final



140



140


120


100


80


60


40


20


0



|Midplane temperature<br>Dust<br>trap<br>T<br>H2CO freeze<br>,<br>T<br>CO freeze<br>,|Col2|Col3|lane te|Col5|mperature|Col7|
|---|---|---|---|---|---|---|
|~~T~~CO, freeze<br>TH2CO, freeze<br>Dust<br> trap<br>Midplane temperature|~~T~~CO, freeze<br>TH2CO, freeze<br>Dust<br> trap|~~T~~CO, freeze<br>TH2CO, freeze<br>Dust<br> trap|~~T~~CO, freeze<br>TH2CO, freeze<br>Dust<br> trap|~~T~~CO, freeze<br>TH2CO, freeze<br>Dust<br> trap|~~T~~CO, freeze<br>TH2CO, freeze<br>Dust<br> trap|~~T~~CO, freeze<br>TH2CO, freeze<br>Dust<br> trap|
||||||||
||||||||
||||||||
||||||||
||||||||
||||||||
||||||||
||||||||


0 25 50 75 100 125

R (au)



120


100


80


60


40


20


0








|Col1|Col2|
|---|---|
|d=0.005 g cm<br>2 (sett)<br>d=0.05 g cm<br>2 (sett)<br>d=0.5 g cm<br>2 (sett)<br>d=5.0 g cm<br>2 (sett)<br>d=0.005 g c<br>d=0.05 g cm<br>d=0.5 g cm<br>d=5.0 g cm|m<br>2 (vdM16)<br> <br>2 (full)<br>2 (full)<br>2 (full)|


|ertical gas temperature at R=65 au<br>Emitting<br>layer<br>T<br>ex<br>d=0 .005 g cm 2 (sett) d=0 .005 g cm 2 (vdM16)<br>d=0 .05 g cm 2 (sett) d=0 .05 g cm 2 (full)<br>d=0 .5 g cm 2 (sett) d=0 .5 g cm 2 (full)<br>d=5 .0 g cm 2 (sett) d=5 .0 g cm 2 (full)|Col2|Col3|Col4|
|---|---|---|---|
|Tex<br>Emitting<br> layer<br>ertical gas temperature at R=65 au<br>d=0.005 g cm<br>2 (sett)<br>d=0.05 g cm<br>2 (sett)<br>d=0.5 g cm<br>2 (sett)<br>d=5.0 g cm<br>2 (sett)<br>d=0.005 g cm<br>2 (vdM16)<br>d=0.05 g cm<br>2 (full)<br>d=0.5 g cm<br>2 (full)<br>d=5.0 g cm<br>2 (full)|Tex<br>Emitting<br> layer<br>d=0.005 g cm<br>2 (sett)<br>d=0.05 g cm<br>2 (sett)<br>d=0.5 g cm<br>2 (sett)<br>d=5.0 g cm<br>2 (sett)<br>d=0.005 g c<br>d=0.05 g cm<br>d=0.5 g cm<br>d=5.0 g cm|Tex<br>Emitting<br> layer<br>d=0.005 g cm<br>2 (sett)<br>d=0.05 g cm<br>2 (sett)<br>d=0.5 g cm<br>2 (sett)<br>d=5.0 g cm<br>2 (sett)<br>d=0.005 g c<br>d=0.05 g cm<br>d=0.5 g cm<br>d=5.0 g cm|Tex<br>Emitting<br> layer<br>d=0.005 g cm<br>2 (sett)<br>d=0.05 g cm<br>2 (sett)<br>d=0.5 g cm<br>2 (sett)<br>d=5.0 g cm<br>2 (sett)<br>d=0.005 g c<br>d=0.05 g cm<br>d=0.5 g cm<br>d=5.0 g cm|
|||||
|||||
|||||
|||||
|||||
|||||
|||||
|||||



0.0 0.1 0.2 0.3

z/r



**Fig. 4. Top left:** Radial dust temperature profiles of the midplane. **Top right:** Vertical gas temperature profiles at 65 au, just inside the dust trap.
Both temperature profiles are based on our physical-chemical DALI models with different dust surface densities (Figure C.1,C.2). In the midplane,
the gas temperature is equal to the dust temperature. The plots demonstrate that the dust trap provides sufficiently low temperatures for a COM ice
reservoir in the settled midplane, whereas the temperatures in the emitting layer are sufficiently high to explain the derived excitation temperatures.
**Bottom:** Sketch of the proposed scenario for the complex organic chemistry in a dust trap based on this work. The blue-orange gradient indicates
the predicted temperature structure in the disk the large arrows the vertical and radial transport of the icy pebbles, and the small arrow the thermal
desorption at the inner edge of the dust trap

.



ture of H 2 CO compared to CH 3 OH. This discrepancy cannot
be explained by additional gas phase chemistry production, as
this would result in H 2 CO emission along the entire ring. Formation by gas phase chemistry is not excluded but due to the
extreme dust trapping the ice sublimation dominates the observable chemistry.


It is unclear whether the high dust-to-gas ratio environment
and high COM abundances are unique for IRS 48. Pegues et al.
(2020) and Facchini et al. (2021) derive H 2 CO column densi

Article number, page 6 of 16



ties of ∼10 [12] cm [−][2] and low excitation temperatures of 20-30 K
for a number of T Tauri disks, whereas for HD100546, the rotational temperature in the inner 50 au was derived as 50-100
K (Booth et al. 2021). All these T Tauri disks have radial dust
traps, which also lead to dust concentrations smaller than the
beam size of the COM observations. Interestingly, Pegues et al.
(2020) find a higher column density of ∼ 10 [13] cm [−][2] for J16042130, the only disk in their sample for which the H 2 CO emission
is more resolved radially, revealing the ring structure also seen

Nienke van der Marel et al.: A major asymmetric ice trap in a planet-forming disk: I. Formaldehyde and methanol


in the continuum. As the inferred column densities rely on the
assumed emitting area, the column densities in these works are
lower limits and may be as high as in IRS 48. However, the high
excitation temperatures of the COMs in IRS 48 require more efficient vertical transport, which may be due to the unique vortex
properties.
IRS 48 is the first protoplanetary disk with a clear link between the morphology of the COM emission and the continuum.
These results show the importance of taking into account dust
traps in chemical disk models in the production of complex organic chemistry, and in spatially resolving COMs in disks for
comparison with the dust substructure.


_Acknowledgements._ We thank the referee for their thoughtful report, which has
improved the clarity of the manuscript. We would also like to thank Wlad Lyra
and Sebastiaan Krijt for useful discussions and Akimasa Kataoka for his help
with the reduction of the data. N.M. acknowledges support from the Banting
Postdoctoral Fellowships program, administered by the Government of Canada.
ALMA is a partnership of ESO (representing its member states), NSF (USA) and
NINS (Japan), together with NRC (Canada) and NSC and ASIAA (Taiwan) and
KASI (Republic of Korea), in cooperation with the Republic of Chile. The Joint
ALMA Observatory is operated by ESO, AUI/ NRAO and NAOJ. This paper
makes use of the following ALMA data: 2017.1.00834.S.


Article number, page 7 of 16

_A&A proofs:_ manuscript no. Paper_final


**References**


Agúndez, M., Roueff, E., Le Petit, F., & Le Bourlot, J. 2018, A&A, 616, A19
Alarcón, F., Teague, R., Zhang, K., Bergin, E. A., & Barraza-Alfaro, M. 2020,
ApJ, 905, 68
Andrews, S. M., Huang, J., Pérez, L. M., et al. 2018, ApJ, 869, L41
Andrews, S. M., Wilner, D. J., Espaillat, C., et al. 2011, ApJ, 732, 42
Barge, P. & Sommeria, J. 1995, A&A, 295, L1
Bergin, E. A., Aikawa, Y., Blake, G. A., & van Dishoeck, E. F. 2007, Protostars
and Planets V, 751
Boogert, A. C. A., Gerakines, P. A., & Whittet, D. C. B. 2015, ARA&A, 53, 541
Booth, A. S., Walsh, C., Terwisscha van Scheltinga, J., et al. 2021, Nature Astronomy [ `arXiv:2104.08348` ]
Brauer, F., Dullemond, C. P., & Henning, T. 2008, A&A, 480, 859
Bruderer, S. 2013, A&A, 559, A46
Bruderer, S., van der Marel, N., van Dishoeck, E. F., & van Kempen, T. A. 2014,
A&A, 562, A26
Bruderer, S., van Dishoeck, E. F., Doty, S. D., & Herczeg, G. J. 2012, A&A, 541,
A91
Cleeves, L. I., Bergin, E. A., Bethell, T. J., et al. 2011, ApJ, 743, L2
Cridland, A. J., Pudritz, R. E., & Birnstiel, T. 2017, MNRAS, 465, 3865
Dutrey, A., Guilloteau, S., & Guelin, M. 1997, A&A, 317, L55
Ehrenfreund, P. & Charnley, S. B. 2000, ARA&A, 38, 427
[Facchini, S., Teague, R., Bae, J., et al. 2021, arXiv e-prints, arXiv:2101.08369](http://arxiv.org/abs/2101.08369)
Fedele, D., van Dishoeck, E. F., Kama, M., Bruderer, S., & Hogerheijde, M. R.
2016, A&A, 591, A95
Flock, M., Turner, N. J., Nelson, R. P., et al. 2020, ApJ, 897, 155
Foreman-Mackey, D., Hogg, D. W., Lang, D., & Goodman, J. 2013, PASP, 125,
306
Francis, L. & van der Marel, N. 2020, ApJ, 892, 111
Fuchs, G. W., Cuppen, H. M., Ioppolo, S., et al. 2009, A&A, 505, 629
Gaia Collaboration, Brown, A. G. A., Vallenari, A., et al. 2018, A&A, 616, A1
Garrod, R., Park, I. H., Caselli, P., & Herbst, E. 2006, Faraday Discussions, 133,
51
Geers, V. C., Pontoppidan, K. M., van Dishoeck, E. F., et al. 2007, A&A, 469,
L35
Hama, T., Kouchi, A., & Watanabe, N. 2018, ApJ, 857, L13
Herbst, E. & van Dishoeck, E. F. 2009, ARA&A, 47, 427
Kahane, C., Frerking, M. A., Langer, W. D., Encrenas, P., & Lucas, R. 1984,
A&A, 137, 211
Krijt, S., Bosman, A. D., Zhang, K., et al. 2020, ApJ, 899, 134
Lee, J.-E., Lee, S., Baek, G., et al. 2019, Nature Astronomy, 3, 314
Loomis, R. A., Öberg, K. I., Andrews, S. M., et al. 2018, AJ, 155, 182
Mangum, J. G. & Wootten, A. 1993, ApJS, 89, 123
Meheut, H., Casse, F., Varniere, P., & Tagger, M. 2010, A&A, 516, A31
Mulders, G. D., Waters, L. B. F. M., Dominik, C., et al. 2011, A&A, 531, A93
Öberg, K. I. & Bergin, E. A. 2021, Phys. Rep., 893, 1
Öberg, K. I., Guzmán, V. V., Furuya, K., et al. 2015, Nature, 520, 198
Öberg, K. I., Qi, C., Fogel, J. K. J., et al. 2010, ApJ, 720, 480
Ohashi, S., Kataoka, A., van der Marel, N., et al. 2020, ApJ, 900, 81
Pegues, J., Öberg, K. I., Bergner, J. B., et al. 2020, ApJ, 890, 142
Penteado, E. M., Walsh, C., & Cuppen, H. M. 2017, ApJ, 844, 71
Pérez, L. M., Isella, A., Carpenter, J. M., & Chandler, C. J. 2014, ApJ, 783, L13
Pinilla, P., Benisty, M., & Birnstiel, T. 2012a, A&A, 545, A81
Pinilla, P., Birnstiel, T., Ricci, L., et al. 2012b, A&A, 538, A114
Podio, L., Garufi, A., Codella, C., et al. 2020, A&A, 642, L7
Rabli, D. & Flower, D. R. 2010, MNRAS, 406, 95
Schöier, F. L., van der Tak, F. F. S., van Dishoeck, E. F., & Black, J. H. 2005,
A&A, 432, 369
Semenov, D. & Wiebe, D. 2011, ApJS, 196, 25
Terwisscha van Scheltinga, J., Hogerheijde, M. R., Cleeves, L. I., et al. 2021,
ApJ, 906, 111
Thi, W.-F., van Zadelhoff, G.-J., & van Dishoeck, E. F. 2004, A&A, 425, 955
van der Marel, N., Pinilla, P., Tobin, J., et al. 2015, ApJ, 810, L7
van der Marel, N., van Dishoeck, E. F., Bruderer, S., et al. 2016, A&A, 585, A58
van der Marel, N., van Dishoeck, E. F., Bruderer, S., et al. 2013, Science, 340,
1199
van der Marel, N., van Dishoeck, E. F., Bruderer, S., & van Kempen, T. A. 2014,
A&A, 563, A113
van der Tak, F. F. S., Black, J. H., Schöier, F. L., Jansen, D. J., & van Dishoeck,
E. F. 2007, A&A, 468, 627
van Dishoeck, E. F., Blake, G. A., Draine, B. T., & Lunine, J. I. 1993, in Protostars and Planets III, ed. E. H. Levy & J. I. Lunine, 163
van Dishoeck, E. F., Blake, G. A., Jansen, D. J., & Groesbeck, T. D. 1995, ApJ,
447, 760
van ’t Hoff, M. L. R., Tobin, J. J., Trapman, L., et al. 2018, ApJ, 864, L23
Walsh, C., Juhász, A., Meeus, G., et al. 2016, ApJ, 831, 200
Walsh, C., Millar, T. J., Nomura, H., et al. 2014, A&A, 563, A33
Watanabe, N. & Kouchi, A. 2002, ApJ, 571, L173
Weidenschilling, S. J. 1977, MNRAS, 180, 57
Wiesenfeld, L. & Faure, A. 2013, MNRAS, 432, 2573


Article number, page 8 of 16

Nienke van der Marel et al.: A major asymmetric ice trap in a planet-forming disk: I. Formaldehyde and methanol


**Appendix A:** **Spectra and intensity maps**


This section contains additional figures of the data.







CH 3 OH 4 0, 4 -3 1, 3 CH 3 OH 7 2, 6 [-6] 1, 5







H 2 CO 5 0, 5 -4 0, 4 H 2 CO 5 1, 5 -4 1, 4



120



100


80


60



40


20


0


20


120


100


80


60


40


20


0


20


|H2CO 52, 4-42, 3|Col2|H2CO 53, 3-43, 2|CH3OH|H 81, 7-72, 5|Col6|CH3OH 110, 11-101, 9|Col8|
|---|---|---|---|---|---|---|---|
||||10<br>20<br>30|||||
||||10<br>0|||||



|H2CO 53, 2-43, 1|Col2|H2CO 54, 2-44, 1|CH3OH 1|141, 13-140, 14|Col6|CH3OH 11, 1-00, 0|
|---|---|---|---|---|---|---|
||||0<br>10<br>20<br>30||||
||||10<br>||||


0 10


v (km s 1 )





0 10


v (km s 1 )





0 10


v (km s 1 )



0 10


v (km s 1 )



**Fig.** **A.1.** H 2 CO and CH 3 OH spectra, integrated over the central area of the dust trap using Keplerian masking (blue) and extracted from a
rectangular box (grey). The grey shades indicate the noise levels in the spectra. The spectra are ordered by increasing _E_ _u_, following the values
reported in Table 1.


Article number, page 9 of 16

_A&A proofs:_ manuscript no. Paper_final











































































Article number, page 10 of 16

Nienke van der Marel et al.: A major asymmetric ice trap in a planet-forming disk: I. Formaldehyde and methanol












|Col1|13CO 6 5<br>--<br>mm-dust|
|---|---|
|||
|||
|||
|||
|||



**Fig. A.3.** High resolution image of the [13] CO 6–5 zero moment map (blue) and the 366 GHz continuum (red) at the original 0.18×0.14" resolution.
The contours of the [13] CO show the 20,40,60,80% of the peak while the contours of the continuum indicate the 5σ level. This image demonstrates
that the gas traces a full disk ring whereas the mm-dust grains are concentrated in the southern part of the disk.


**Appendix B:** **Rotational diagram analysis**


This section contains more details on the analysis of the rotational diagram from Figure 3. Figure B.1 shows the corner plots showing
the posterior distributions and covariances of the fit containing all line transitions, confirming the fit has converged. The covariance
is similar to previous studies of rotational diagrams of COMs in protoplanetary disks (e.g. Loomis et al. 2018).


**Fig. B.1.** Posterior distributions of the column density and rotational temperature based on our optically thin line intensities of H 2 CO (left) and
CH 3 OH (right). The best fit is shown in Figure 3.


Second, we estimate the ortho-to-para ratio of H 2 CO by fitting the ortho and para lines separately, without the ortho-to-para
correction of 3 in the degeneracies as used in Figure 3. The new rotational diagram with best fits and the posteriors are shown in
Figure B.2. The ortho lines have a best fit _T_ rot of 193 [+] − [18] 15 [K and] _[ N]_ _[T]_ [=][ 7][.][2][ ±][ 0][.][7][ ·][ 10] [13] [cm] [−][2] [and the para lines a] _[ T]_ [rot] [of 257] [+] − [57] 39 [K and]
_N_ _T_ = 5.9 ± 1.7 · 10 [13] cm [−][2] . This implies an ortho-to-para ratio of 1.2±0.4, which is well below the default value of 3. The lower
value could indicate an ice formation rather than gas formation route (e.g Terwisscha van Scheltinga et al. 2021), which is consistent
with our proposed scenario. However, if the optical depth of the ortho lines is underestimated (if the emitting area is smaller than
assumed) this could also explain the lower value. Furthermore, for H 2 O it has been shown that the ortho-to-para ratio is reset after
desorption from the ices (Hama et al. 2018) and if the same is true for H 2 CO, the ortho-to-para ratio does not provide information


Article number, page 11 of 16

_A&A proofs:_ manuscript no. Paper_final


about the formation origin. Regardless of the precise scenario, a low ortho-to-para ratio would imply a very cold formation location
of only ∼10 K (Kahane et al. 1984), much lower than the current dust trap conditions.



26





25


24


23


22

|Col1|H2CO|Col3|Col4|Col5|Col6|Col7|
|---|---|---|---|---|---|---|
||ortho<br>para (uncorrected)|ortho<br>para (uncorrected)|ortho<br>para (uncorrected)|ortho<br>para (uncorrected)|ortho<br>para (uncorrected)|ortho<br>para (uncorrected)|
||||||||
||||||||
||||||||
||||||||
||||||||
||||||||



0 50 100 150 200 250 300

E u (K)


**Fig. B.2.** Rotational diagram of H 2 CO, similar to Figure 3, but without the default ortho-to-para correction of 3 for the para lines, with separate
fits to the ortho and para lines. The bottom panels show the posterior distributions of the best fits as in Figure B.1.


**Appendix C:** **Temperature structure**


This section describes our analysis of the temperature structure and line ratios of IRS 48. We set up a series of physical-chemical
models using DALI (Bruderer et al. 2012; Bruderer 2013) to compute the gas and dust temperature structure from the heatingcooling balance of gas and dust, following the parametrized model of the gas and dust surface density from van der Marel et al.
(2016) that is consistent with the CO 6–5 isotopologue data presented in that work. The dust surface density was not explicitly fit
in that model, and with a gas-to-dust ratio of 20 used in that work the dust surface density at 60 au is Σ _d_ ∼0.005 g cm [−][2] . As Ohashi
et al. (2020) derived a much higher dust surface density of Σ _d_ ∼2-8 g cm [−][2], we explore the effect of the dust surface density on the
radial and vertical temperature structure, using Σ _d_ ∼0.05, 0.5 and 5.0 g cm [−][2] between 60 and 80 au. Two sets of models are run: one
with an increase of the large grains in the midplane with a larger degree of settling (settled models) and second with an increase of
all grains throughout the full dust column (full models). The vertical density structure in DALI is fixed to a Gaussian profile with
different scale heights for the large and small grains to represent the settling, following Andrews et al. (2011):


Article number, page 12 of 16

Nienke van der Marel et al.: A major asymmetric ice trap in a planet-forming disk: I. Formaldehyde and methanol



2 []

(C.1)
� 



Σ _l_
ρ _l_ = exp
~~√~~ 2π _r_ χ _h_



1
− 2




π/2 − θ
� χ _h_



2 []

(C.2)
� 



Σ _s_
ρ _s_ = exp
~~√~~ 2π _rh_



1
− 2




π/2 − θ
� _h_



with ρ _l_ and ρ _s_ the dust density of large and small grains, respectively, _h_ = _h_ _c_ ( _r_ / _r_ _c_ ) [ψ] the scale height, χ the settling parameter and
θ the vertical latitude coordinate measured from the pole. The large grain population contains dust grains from 0.005 µm to 1 mm
and the small grain population contains dust grains from 0.005 - 1 µm by convention. In the full disk model, the settling degree χ
is set to the default value of 0.2, while in the settled model χ is set to 0.1. The radial structure inside 60 au contains the inner dust
disk (between _r_ sub and _r_ gap ), the gas cavity _r_ cavgas and dust cavity _r_ cavdust, which are the same as in van der Marel et al. (2016) and
we refer for more details to that work. All model parameter values are listed in Table C.1 and the results are shown in Figure C.1
and C.2.


**Table C.1.** Model parameters of gas and dust surface density

|Property Parameter|Settledmodels|Fullmodels|
|---|---|---|
|Surface density<br>Σ60au,gas (g cm−2)<br>Σ60au,dust (g cm−2)<br>Dust settling<br>χ|0.25<br>0.005,0.05,0.5,5.0<br>(large grains only)<br>0.1|0.25<br>0.005,0.05,0.5,5.0<br>(all grains)<br>0.2|
|Vertical structure<br>_hc_<br>ψ|0.14<br>0.22|0.14<br>0.22|
|Radial structure<br>_rc_ (au)<br>_r_sub (au)<br>_r_gap (au)<br>_r_cavgas (au)<br>_r_cavdust (au)<br>_r_out (au)|60<br>0.4<br>1<br>25<br>60<br>90|60<br>0.4<br>1<br>25<br>60<br>90|



Second, we estimate the expected flux ratios for both optically thick and optically thin emission of the H 2 CO and CH 3 OH lines
studied in this work. This is parametrized by setting an abundance of 10 [−][7] and 10 [−][9] (optically thick and thin, respectively) for both
molecules in the regions in the disk where the extinction _A_ _V_ >1 (shielding for photodissociation), radius _r_ >60 au (in the dust trap)
and the dust temperature _T_ dust - _T_ subl, with _T_ subl =66 K for H 2 CO and 100 K for CH 3 OH. These thresholds set the region where
the molecule is expected to be in the gas phase. These regions are well above the regime where the majority of the large grains are
located due to the settling. In the rest of the disk, these molecular abundances are set to 10 [−][12] . This leads to specific emitting layers
in the disk where H 2 CO and CH 3 OH are located, which are used to raytrace the lines to compute line ratios which can be compared
with the data. The absolute fluxes are less relevant as the real molecular layers are likely much more complex. Also, as DALI is an
axisymmetric model, the azimuthal structure is not constrained in this model.
The models show that the dust and gas temperature drop when the dust density is increased due to the stronger suppression of the
UV field. This drop remains limited to the midplane when the dust density is only increased in that region compared to an increase
throughout the full column. This is illustrated directly in Figure 4. The models show that the emitting layer shifts upward in the disk
for higher dust densities when the dust is distributed throughout the disk (’full’) due to the sublimation temperature requirement.
On the upper end, the emitting layer is constrained by the extinction requirement, which means that the layer becomes thinner in
the high dust density models. In the most extreme case of Σ _d_ =5 g cm [−][2] an additional emitting layer appears in the midplane as the
dust becomes fully optically thick at the dust edge, leading to a strong vertical increase in temperature.
The raytraced line fluxes reproduce the H 2 CO fluxes reasonably well for the settled models for the 10 [−][7] abundance, the CH 3 OH
fluxes are at least a factor 10 too low. The models with 10 [−][9] abundance and high dust density full models underestimate all fluxes by
1 to 3 orders of magnitude. The line ratios are derived and compared with the line ratios in the RADEX plot in Figure C.3. The line
ratios for H 2 CO for 10 [−][7] abundance are closer to the data values, suggesting that the H 2 CO emission is potentially optically thick
(i.e. the emitting area is at least a factor 5 smaller than our estimate). The ratios shift to slightly lower values for the higher dust
density models, consistent with lower temperatures. For CH 3 OH the ratios are essentially the same for the two abundances and in
similar temperature regime as the data, suggesting the emission remains optically thin for both. The ratios shift to higher values for
the high dust density full models, consistent with higher temperatures, which is the result of the strong upward shift in the emitting
layers. However, the column density and flux drop significantly in that case, implying that this is not a realistic scenario. Overall,
the spread in temperatures for the different ratios implies that the various lines trace different temperature regions in the disk with
potentially different abundances. A more detailed analysis is saved for future work.


Article number, page 13 of 16

_A&A proofs:_ manuscript no. Paper_final

















































50 60 70 80 90

r (au)


H 2 CO abundance


50 60 70 80 90

r (au)


CH 3 OH abundance


50 60 70 80 90

r (au)





0


30



0


30



10 7



0


30



0


30



25


20


15



25


20



25


20



25


20


15



10 8


10 9



10 10


10 11


10 7



10


5


0


30


25


20


15


10


5


0



15


10


5


0


30



25


20


15


10


5


0



50 60 70 80 90

r (au)


H 2 CO abundance


50 60 70 80 90

r (au)


CH 3 OH abundance


50 60 70 80 90

r (au)



15


10


5


0


30



25


20


15


10


5


0



50 60 70 80 90

r (au)


H 2 CO abundance


50 60 70 80 90

r (au)


CH 3 OH abundance


50 60 70 80 90

r (au)



10


5


0


30


25


20


15


10


5


0



50 60 70 80 90

r (au)


H 2 CO abundance


50 60 70 80 90

r (au)


CH 3 OH abundance


50 60 70 80 90

r (au)



10 8


10 9


10 10


10 11



**Fig. C.1.** Temperature structure of the IRS 48 disk as computed by DALI, using the gas and dust density profile derived by van der Marel et al.
(2016) for the settled models (dust density increase of the large grains in the midplane)
. The columns show the influence of the assumed dust surface density (or dust-to-gas ratio, as the gas surface density is set
constant) on the UV field and gas temperature. The white contours in the temperature plots indicate steps of 20 K.


Article number, page 14 of 16

Nienke van der Marel et al.: A major asymmetric ice trap in a planet-forming disk: I. Formaldehyde and methanol





















































50 60 70 80 90

r (au)


H 2 CO abundance


50 60 70 80 90

r (au)


CH 3 OH abundance


50 60 70 80 90

r (au)



0


30



0


30



0


30



0


30



10 7


10 8


10 9


10 10


10 11


10 7


10 8


10 9


10 10


10 11



25


20



25


20



25


20


15



15


10


5


0


30



15


10


5


0


30



25


20


15



50 60 70 80 90

r (au)


H 2 CO abundance


50 60 70 80 90

r (au)


CH 3 OH abundance


50 60 70 80 90

r (au)



10


5


0


30


25


20


15


10


5


0



50 60 70 80 90

r (au)


H 2 CO abundance


50 60 70 80 90

r (au)


CH 3 OH abundance


50 60 70 80 90

r (au)



25


20


15


10


5


0



50 60 70 80 90

r (au)


H 2 CO abundance


50 60 70 80 90

r (au)


CH 3 OH abundance


50 60 70 80 90

r (au)



25


20


15


10


5


0



10


5


0


30


25


20


15


10


5


0



**Fig. C.2.** Temperature structure of the IRS 48 disk as computed by DALI, using the gas and dust density profile derived by van der Marel et al.
(2016) for the full models (dust increase across the column). The columns show the influence of the assumed dust surface density (or dust-to-gas
ratio, as the gas surface density is set constant) on the UV field and gas temperature. The white contours in the temperature plots indicate steps of
20 K.


Article number, page 15 of 16

_A&A proofs:_ manuscript no. Paper_final


**Fig.** **C.3.** Expected line ratios as computed by RADEX for H 2 CO (top) and CH 3 OH (bottom) for a column density of 10 [14] cm [−][2] . The white
contours indicate the observed values and the dashed lines the uncertainty. The coloured lines indicate the ratios as computed for our DALI models
of the settled model for fixed abundances 10 [−][7] and 10 [−][9] in specific emitting layers as described in the text.


Article number, page 16 of 16


</paper>

## Items to check

```json
[
 {
  "path": "data.external_data_from_literature[1].what.evidence[0]",
  "value": "High resolution (0.18x0.14\") Band 7 continuum image used to determine emitting area",
  "failed_quote": "Instead, the emitting area is determined using the high resolution (0.18×0.14\") Band 7 continuum image (Francis & van der Marel 2020, and Figure A.3), with the underlying assumption that the H 2 CO and CH 3 OH emission follow the morphology of the dust crescent."
 },
 {
  "path": "analysis_steps[3].assumptions[1].evidence[0]",
  "value": "H2CO and CH3OH emission follow the morphology of the dust crescent",
  "failed_quote": "Instead, the emitting area is determined using the high resolution (0.18×0.14\") Band 7 continuum image (Francis & van der Marel 2020, and Figure A.3), with the underlying assumption that the H 2 CO and CH 3 OH emission follow the morphology of the dust crescent."
 },
 {
  "path": "reasoning.limitations_admitted[2].evidence[1]",
  "value": "The low H2CO ortho-to-para ratio (<3) could be an artifact of underestimated optical depth of the ortho lines if the true emitting area is smaller than assumed, or could be reset after ice desorption.",
  "failed_quote": "Furthermore, for H 2 O it has been shown that the ortho-to-para ratio is reset after desorption from the ices (Hama et al. 2018) and if the same is true for H 2 CO, the ortho-to-para ratio does not provide information about the formation origin."
 }
]
```
