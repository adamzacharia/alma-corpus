# Repair task for a Claude Code subagent

A methods card has evidence quotes that were not found verbatim in the paper. Below are the rules, the paper, and the failing items. Write ONE JSON object, nothing else, of the form {"repairs": [{"path": ..., "found": true|false, "loc": ..., "quote": ...}, ...]} with one entry per item (path unchanged) to:

    C:\Users\adama\alma-corpus\cards\2021A%26A...653A..84P\gemini4argon\repair_reply.txt

Use the Write tool for that file. Copy each quote character for character from the paper text below; a returned quote is checked mechanically and dropped if it is not in the paper. Do not read any other file, do not run commands, and do not change anything else. Reply with one line when done.

---

## Rules

You check evidence quotes for a methods card extracted from an astronomy paper. Some quotes could not be found verbatim in the paper text, and some stated values came without a quote. For each item: find the passage in the paper that supports the value and copy it VERBATIM (same words and order, at most 40 words; LaTeX markup may be dropped) with its loc (section heading, "abstract", "Table N" or "Figure N caption"). If the paper does not support the value, return found = false and leave quote and loc empty. Use only the paper text. Return one entry per item, with the item's path unchanged.

## Paper

<paper>
_Astronomy & Astrophysics_ manuscript no. pozzi ©ESO 2021
June 1, 2021

## **The ALPINE-ALMA [CII] survey: Dust mass budget in the early** **Universe**


F. Pozzi [1][,][ 2], F. Calura [2], Y. Fudamoto [3], M. Dessauges-Zavadsky [3], C. Gruppioni [2], M. Talia [1], G. Zamorani [2], M.
Bethermin [4], A. Cimatti [1][,][ 5], A. Enia [1], Y. Khusanova [4], R. Decarli [2], O. Le Fèvre [4], P. Capak [6], P. Cassata [7], A.L. Faisst [6], L.
Yan [8], D. Schaerer [3], J. Silverman [9], S. Bardelli [2], M. Boquien [10], A. Enia [1], D.Narayanan [11], M. Ginolfi [12], N.P. Hathi [13],
G.C. Jones [14][,][ 15], A.M. Koekemoer [13], B.C. Lemaux [16], F. Loiacono [1], R. Maiolino [14][,][ 15][,][ 17], D.A. Riechers [18], G.
Rodighiero [6], M. Romano [7][,][ 19], L. Vallini [20], D. Vergani [2], E. Zucca [2]


1 Dipartimento di Fisica e Astronomia, Università of Bologna, via Gobetti 93/2, 40129, Bologna, Italy
2 INAF – Osservatorio di Astrofisica e Scienza dello Spazio di Bologna, via Gobetti 93/3, 40129, Bologna, Italy
3 Department of Astronomy, University of Geneva, 51 Ch. des Maillettes, 1290 Versoix, Switzerland
4 Aix Marseille Univ. CNRS, LAM, Laboratoire d’Astrophysique de Marseille, Marseille, France
5 INAF – Osservatorio astrofisico di Arcetri, Largo E. Fermi 5, I-50125, Firenze, Italy
6 Infrared Processing and Analysis Center, California Institute of Technology, Pasadena, CA 91125, USA
7 Dipartimento di Fisica e Astronomia, Università di Padova, vicolo Osservatorio 3, 35122 Padova, Italy
8 The Caltech Optical Observatories, California Institute of Technology, Pasadena, CA 91125, USA
9 Kavli Institute for the Physics and Mathematics of the Universe, The University of Tokyo, 5-1-5 Kashiwanoha, Kashiwa-shi,
Chiba, 277-8583 Japan
10 Centro de Astronomia (CITEVA), Universidad de Antofagasta, Avenida Angamos 601, Antofagasta, Chile
11 Department of Astronomy, University of Florida, 211 Bryant Space Sciences Center, Gainesville, FL 32611 USA
12 European Southern Observatory, Karl-Schwarzschild-Straße 2, 85748 Garching, Germany
13 Space Telescope Science Institute, 3700 San Martin Drive, Baltimore, MD 21218, USA
14 Cavendish Laboratory, University of Cambridge, 19 J. J. Thomson Ave., Cambridge CB3 0HE, UK
15 16 Kavli Institute for Cosmology, University of Cambridge, Madingley Road, Cambridge CB3 0HA, UK
16 Department of Physics, University of California, Davis, One Shields Ave., Davis, CA 95616, USA
17 Department of Physics and Astronomy, University College London, UK
18 Department of Astronomy, Cornell University, Space Sciences Buildin, Ithaca, NY 14853, USA
19 INAF – Osservatorio Astronomico di Padova, Vicolo dell’Osservatorio 5, I-35122, Padova, Italy
20 Scuola Normale Superiore, Piazza dei Cavalieri 7, I-56126 Pisa, Italy


Accepted May 26, 2021


**ABSTRACT**


_Aims._ The dust content of normal galaxies and the dust mass density (DMD) at high- _z_ ( _z_   - 4) are unconstrained given the source
confusion and the sensitivity limitations of previous observations. The ALMA Large Program to INvestigate [CII] at Early Times
(ALPINE), which targeted 118 UV-selected star-forming galaxies at 4.4<z<5.9, provides a new opportunity to tackle this issue for
the first time with a statistically robust dataset.
_Methods._ We have exploited the rest-frame far-infrared (FIR) fluxes of the 23 continuum individually detected galaxies and stacks
of continuum images to measure the dust content of the 118 UV-selected ALPINE galaxies. We have focused on the dust scaling
relations and, by comparing them with predictions from chemical evolution models, we have probed the evolutionary stage of UVselected galaxies at high- _z_ . By using the observed correlation between the UV-luminosity and the dust mass, we have estimated the
DMD of UV-selected galaxies at _z_ ∼5, weighting the galaxies by means of the UV-luminosity function (UVLF). The derived DMD
has been compared with the value we have estimated from the 10 ALPINE far-IR continuum blindly detected galaxies at the redshift
of the ALPINE targets.
_Results._ Our ALMA survey allows the exploration for the first time of the dust content in normal star-forming galaxies at _z_    - 4 in a
statistically robust sample of sources. The comparison of the observed dust scaling relations with chemical evolution models suggests
that ALPINE galaxies are not likely progenitors of disc galaxies, but of intermediate and low mass proto-spheroids, resulting in
present-day bulges of spiral or elliptical galaxies. Interestingly, this conclusion is in line with the independent morphological analysis,
that shows that the majority (∼70%) of the dust-continuum detected galaxies have a disturbed morphology. The DMD obtained at _z_ ∼5
from UV-selected sources is ∼30 % of the value obtained from blind far-IR selected sources, showing that the UV-selection misses
the most dust-rich, UV-obscured galaxies.
_Conclusions._


**Key words.** galaxies: high-redshift — galaxies: ISM — ISM: dust


**1.** **Introduction**


Cosmic dust accounts for an almost negligible contribution of

∼
the baryon mass in the Universe ( 0.1 % in the local Universe,

Article number, page 1 of 14

_A&A proofs:_ manuscript no. pozzi



see Shull et al. 2012). Nevertheless, it plays a crucial role in
many astrophysical and astrochemical aspects. First among others, it strongly affects the spectral energy distribution of galaxies, being a source of attenuation for UV/optical photons and an
emission source in the infrared domain. Therefore, it is of primary importance to recover the galaxy dust properties to achieve
a self-consistent understanding of the physics and evolution of
galaxies across the cosmic time.
Before the advent of the Atacama Large Millimeter Array
(ALMA), dust emission of normal star-forming galaxies was
detected mainly thanks to the Herschel surveys up to _z_ < 4
( _z_ ∼2, e.g., Rodighiero et al. 2011; Gruppioni et al. 2013; Magnelli et al. 2013; Lemaux et al. 2014) or extreme dusty (usually
strongly lensed) galaxies up to high- _z_ ( _z_ - 4, e.g., Combes et al.
2012, Rowan-Robinson et al. 2016, Negrello et al. 2017).
Nowadays, ALMA is revolutionising this field of research
thanks to its superb sensitivity and high-spatial resolution that
avoids the problem of source confusion, allowing continuum detection at _z_ - 4 also for normal star-forming galaxies (i.e. with
star-formation rate from a few up to tens of solar masses/year).
Given its relatively small field of view (∼30 arcsec at
1.2 mm), ALMA started the exploration of the high- _z_ Universe
by targeting individual galaxies (e.g Hodge et al. 2013; Riechers et al. 2014, Capak et al. 2015, Watson et al. 2015; Laporte
et al. 2017). The number of normal/large programs over the last
years has been steadily increasing and different continuum surveys have been performed, from the deepest observations over
small areas (<5 arcmin [2], e.g., Dunlop et al. 2017, GonzálezLópez et al. 2020) to the wider (few tens of arcmin [2] ) and shallower surveys (e.g., Franco et al. 2018).

Magnelli et al. (2020) carried out the first study of the dust
mass density (DMD) from _z_ ∼0.5 up to _z_ ∼5, taking advantage of
the deepest (9.5 µJy/beam) ALMA 1.2mm continuum map of
∼4 arcmin [2] in the Hubble Ultra Deep Field (HUDF) of the survey ASPECS (Walter et al. 2016, Decarli et al. 2019, GonzálezLópez et al. 2020). Their results confirm the presence of a peak
around _z_ ∼1-3 and a decrease of the DMD from _z_ ∼1 down to the
local Universe already found by Herschel (Dunne et al. 2011;
Driver et al. 2018, Pozzi et al. 2020), the latter result being
in contrast with cosmological simulations (e.g., Popping et al.
2017, Aoyama et al. 2018, Li et al. 2019).
In order to improve our understanding of the DMD at high_z_ (>4), in this work we take advantage of our recently completed ALMA Large program to INvestigate [CII] at Early times
(ALPINE, PI: Le Fèvre, see Le Fèvre et al. 2020, Béthermin
et al. 2020, Faisst et al. 2020b). The goal of the ALPINE survey
was to observe the prominent [CII] 158 µm emission line for 118
UV-selected normal star-forming galaxies at _z_ ∼4.4 − 5.8. From
118 targets, 75 galaxies were detected in [CII] and 23 in continuum. Besides the main targets, also a blind search for continuum
and line emitters in an ∼25 arcmin [2] area has been performed in
the ALPINE pointings (Béthermin et al. 2020, Loiacono et al.
2020).
Over the last year, many works based on the ALPINE survey
have been presented, describing the Interstellar Medium (ISM)
properties of ‘normal’ star-forming galaxies at _z_ ∼5 (the [CII]SFR relation: Schaerer et al. 2020; the [CII] outflows: Ginolfi
et al. 2020b; the [CII] spatial scales: Fujimoto et al. 2020; the
Lyα-[CII] velocity offset: Cassata et al. 2020; the IRX-β relation:
Fudamoto et al. 2020; the gas content: Dessauges-Zavadsky et al.
2020, detailed studies on individual sources (Jones et al. 2020;
Romano et al. 2020; Ginolfi et al. 2020a) or presenting statistical studies at _z_ ∼5, including the [CII] luminosity function for
ultra-violet (UV) and serendipitous detected line emitters (Yan


Article number, page 2 of 14



et al. 2020, Loiacono et al. 2020), the infrared (IR) luminosity
function (Gruppioni et al. 2020) and the cosmic star formation
rate density (SFRD, Khusanova et al. 2020a).
In the present work, we measure the dust content of UVselected ‘normal’ (main-sequence) galaxies and IR continuum
serendipitously detected sources. In Sect. 2 and 3 the ALPINE
sample and the measurements of the dust masses are presented, respectively. In Sect. 4, the derived ISM properties of
the ALPINE targets (dust masses from the present work and
gas masses from Dessauges-Zavadsky et al. 2020) are combined
with the well characterised stellar masses and SFRs (Faisst et al.
2020b), to discuss the dust scaling relation for the UV-population
at _z_ ∼5. In Sect. 5 the DMD for the UV-selected and for the IRselected populations are presented. Finally, in Sect. 6 we present
our conclusions.
Throughout the paper, we assume a ΛCDM cosmology with
Ω _m_ = 0.3, Ω λ = 0.7 and _H_ 0 =70 km s [−][1] Mpc [−][3] .


**2.** **Observations**


In the following section we describe in detail the ALPINE continuum detected sample that we use in our study. For a more
complete description of the overall survey, of the data reduction, and of the ancillary data we refer to Le Fèvre et al. (2020),
Béthermin et al. (2020) and Faisst et al. (2020b), respectively.
The 118 galaxies from the ALPINE survey (Le Fèvre et al.
2020) are rest-frame UV-selected galaxies at redshift _z_ ∼4.4−5.9.
These galaxies originated in two fields, namely the ‘COSMOS
Evolution Survey’ field (COSMOS, Scoville et al. 2007) and the
‘Extended Chandra Deep Field South’ field (ECDFS, Giacconi
et al. 2002). They all have spectroscopic redshifts from different campaigns (see Faisst et al. 2020b for details). They were
selected to be representative of star-forming Main-Sequence
Galaxies at redshift _z_ ∼5 (i.e. Speagle et al. 2014). They have stellar masses in the range M ⋆ = 10 [8][.][4] − 10 [11] M ⊙ and star-formation
rate in the range SFR=3-270 M ⊙ yr [−][1] . The stellar masses are
derived from SED-fitting using broadband and medium (intermediate) band rest-frame UV/optical photometry (see Faisst
et al. 2020b for details). The SFRs reported are derived from
Schaerer et al. (2020), using the ALPINE far-IR data, to properly account for dust-obscured SFR. They have been computed
as SFR(UV)+SFR(IR) in case of IR continuum detection, and
are derived in the other cases from the observed UV slope and
luminosity using the ALPINE IRX-beta relation (obtained from
stacking, see Fudamoto et al. 2020). These SFRs are globally
consistent with the SFR derived from UV/optical SED-fitting
(median(SFR(UV+IR)/SFR(SED))∼1.2). Anyway, since there
are few outliers for which SFR(UV+IR) results to be a factor up to ∼5 higher than SFR(SED), we prefer to consider the
SFR(UV+IR) in the present analysis to properly account for
dust-obscured SFR.
The ALPINE targets were observed during Cycle 5 and
Cycle 6 in Band 7 (275-373 GHz) which covers the [CII] line
from _z_ = 4.1 − 5.9. To avoid atmospheric absorption, no targets
were included in the redshift range _z_ = 4.6 − 5.1. Each target was
observed between 15 and 45 minutes. The data were reduced
and calibrated with standard routines using the ‘Common
Astronomy Software Application’ (CASA) software (McMullin
et al. 2007). We refer to Béthermin et al. (2020) for all the details
of the data reduction processes and the catalogue construction.
The continuum maps - that are of interest for this work - were
produced using line free channels, reaching an angular resolution between 0.7 [′′] and 1.6 [′′] and mean sensitivities (RMS of 50
µJy/beam and 28 µJy/beam in the 4.3< _z_ < 4.6 and 5.1< _z_ < 5.9

F. Pozzi, F. Calura, Y. Fudamoto et al.: The ALPINE-ALMA survey: Dust mass budget in the early Universe



ranges, respectively. Some sources were marginally resolved at
the angular resolution reached by the observations and different
methods were implemented and compared to measure the fluxes.
The simulations performed (see Sect. 3.2 and 3.9 in Béthermin
et al. 2020) showed that the 2D-fit photometry is the most accurate one, even though other methods are consistent within the
error bars. The final continuum catalogue consists of 23 sources
detected at signal-to-noise ratio SNR> 3.5 (see Table B.1 in
Béthermin et al. 2020). In case of multi-components objects
( _DEIMOS_ _ _COS MOS_ _881725, _vuds_ _ _cosmos_ _5101209780
and _vuds_ _ _e fdcs_ _530029038) we use the sum of the components for _DEIMOS_ _ _COS MOS_ _881725, while we use the
fluxes of the central targets for _vuds_ _ _cosmos_ _5101209780 and
_vuds_ _ _e fdcs_ _530029038 since the companions are likely separated objects (see Appendix D.2 and Table D.1 in Béthermin
et al. 2020 and Ginolfi et al. 2020a).
We anticipate here that in Sec. 5.1 we will perform a stacking
analysis on the rest-frame 157 µm ALMA continuum images,
including both the 23 individual continuum detected sources and
the non-detections. This will be essential to recover the average
properties of the ALPINE population.
In the ALPINE survey, 57 sources were also serendipitously detected at 860-1000 µm (ALMA band-7) and we refer
to Béthermin et al. (2020) for the description of the detection
procedure and the delivery of the non-targets catalogue. In this
case, given the absence of a prior, a conservative threshold of
S/N>5 has been applied. We refer to Gruppioni et al. (2020) for
the detailed characterisation of the sources, done by searching
for counterparts of the serendipitous targets in all the available
multi-band and photo-z catalogues, and also performing new
photometry. The resulting blind sources are distributed in the
wide photometric redshift range (0.5-6) computed including UV,
optical and IR data (for only 4 sources it was not possible to assign a redshift, see Sect. 3.2.2 in Gruppioni et al. 2020). For the
aims of the present work (see Sec. 5.3) we will consider the subsample of 10 galaxies in the redshift range corresponding to the
ALPINE targets (4.1 < _z_ < 5.9). All the 10 sources are detected
in the COSMOS field.


**3.** **Dust mass estimates**


We derive the dust masses using a single Modified Black Body
(MBB) curve, under the approximation of an optically thin
regime (see Bianchi 2013),


_D_ [2]
_L_ _[S]_ [ ν] _[obs]_
_M_ _dust_ = (1)
(1 + _z_ ) _k_ ν _B_ ν ( _T_ )


where ν and ν _obs_ are the rest-frame and observed frequencies
(ν = ν _obs_ (1 + _z_ )), _B_ ν ( _T_ ) is the Planck function, _D_ _L_ the luminosity
distance, _k_ ν the grain absorption cross section per unit mass and
_S_ ν _obs_ is the observed flux corresponding to a rest-frame frequency
at which the dust can be considered optically thin.
We assume a power-law for _k_ ν, _k_ ν = _k_ ν 0 ( ν [ν] 0 [)] [β] [cm] [2] [g] [−][1] [.] [We]

adopt _k_ ν 0 = 4 cm [2] g [−][1] with ν 0 =1.2 THz (see Bianchi 2013) and
β = 1.8, i.e. the Galactic value from the Planck data (Planck
Collaboration et al. 2011).
For the temperature of the dust, we assume T= 25 K. Considering the rest-frame frequency assumed to compute _S_ ν _obs_, we
have considered 1.2 THz, corresponding to λ _rest_ = 250 µm
(see Gilli et al. 2014). At this wavelength our galaxies are expected to be optically thin based on the recent results obtained
by Faisst et al. (2020a) from the SEDs of 4 main-sequence _z_ ∼5.5



**Fig. 1.** Dust masses of the ALPINE continuum-detected galaxies (filled
circles) plotted as a function of _z_ and computed assuming a MBB spectrum with T=25 K and β = 1.8 (see Sec. 3). The empty circles correspond to T=35 K. Blue and red points show detections at 4< _z_ <5 and
5< _z_ <6, respectively. For comparison, we show other compilations of
dust masses at high- _z_ (green triangles: Mancini et al. 2015; dark-green
squares: Le´sniewska & Michałowski 2019).


galaxies (2 contained in the ALPINE dataset), observed with
ALMA in 3 different bands and for which constraints on the
Rayleigh-Jeans part of their spectra were obtained. Our assumption is valid considering also the wavelengths at which more
dusty/extreme sources than the ALPINE ones become optically
thick as SMGs (λ _rest_ <∼ [200][ µ][m,][ Conley et al. 2011][,][ Riechers et al.]
2013; λ _rest_ <∼ [100][ µ][m,][ Simpson et al. 2017][).]

Below we discuss our choice of a single cold component. Morever, we discuss the uncertainties on the derived dust
masses related to three (non-independent) factors: the ‘bandconversion’, linked to the extrapolation of the 250 µm flux from
higher frequencies (i.e. 157 µm), the emissivity β and the temperature T.
In galaxies, dust is located primarily in two components, a
warm one (20<T<60 K) associated to the Photo-Dissociation
Regions (PDRs) and a cold one associated to the diffuse ISM
medium (T< 30 K, see Draine & Li 2007). The adopted method
relies on the assumption that the diffuse cold dust component accounts for the bulk of the dust budget. This has been shown to
be true in the local Universe (see Orellana et al. 2017), where,
given the high-quality photometric data, a sophisticated fit has
been performed showing how the contribution of the warm component accounts for a low fraction of the total dust budget (∼1 %
and reaching the highest value of 4% for starburst galaxies). At
higher redshift, up to _z_ ∼2, the validity of this approximation has
been advocated by Scoville et al. (2014) (see also Scoville et al.
2016, Scoville et al. 2017) in support to the correlation between
the gas masses derived from the sub-millimeter fluxes (directly
linked to the dust masses under the optically thin approximation) and the gas masses derived from CO observations, under
the assumption of a dust-to-gas ratio (see also the recent work of
Kaasinen et al. 2019).

At the redshift of the ALPINE sources, _z_ ∼5, there is no
systematic study that compares the molecular gas masses derived from the sub-millimeter fluxes and the CO measurements,
because the CO line is hard to get even with the most up-todate interferometers (so far in normal main sequence galaxies


Article number, page 3 of 14

_A&A proofs:_ manuscript no. pozzi



there are only two detections, D’Odorico et al. 2018, Pavesi
et al. 2019). Moreover, the CO-based ALMA gas mass estimates rely on strong assumptions about the CO excitation mechanism to extrapolate from the high-J CO levels accessible with
ALMA the CO(1-0) fundamental line. To overcome this issue,
in Dessauges-Zavadsky et al. (2020) the [CII] line has been used
as tracer of the molecular gas masses for the ALPINE galaxies.
By using the relation from Zanella et al. (2018), the molecular
gas masses have been derived from the [CII] luminosities and
compared with masses inferred from dynamical masses and submm fluxes under the approximation of a unique dust component
at T= 25 K and β=1.8. The good correlation shown by the three
tracers (see Sect. 3 and Figs. 3 and 4 in Dessauges-Zavadsky
et al. 2020) supports our assumptions. A cold dust component,
dominating the dust budget, has been recently considered up to
very high- _z_ also by Magnelli et al. (2020), taking advantage of
the ALMA LP survey at 1.2mm (ASPECS, Walter et al. 2016,
Decarli et al. 2019, González-López et al. 2020), where the cold
component approximation has been applied up to _z_ ∼4.5 for detected sources and up to _z_ ∼5.5 for stacked data (see also the
recent review from Hodge & da Cunha (2020) and references
within).


We underline that our assumed dust temperatures are ‘massweighted’ mean temperatures which should not be confused
with the ‘luminosity-weighted’ mean temperatures, more related
to the global SED shape (see Liang et al. 2019 for a detailed
discussion on the different dust temperature definitions). This
means that our temperatures are not comparable with the warmer
temperatures obtained by Béthermin et al. (2020) by fitting the
λ _rest_ - 40µm far-IR ALPINE stacked SED (T= 43 ± 5 _K_, see
Sect. 4 in Béthermin et al. 2020 paper) or with the dust peak
temperature range (30-43 K) as found by Faisst et al. (2020a).
Similar considerations are valid also when comparing the cold
‘mass-weighted’ temperature with predictions from theoretical
models. In Sommovigo et al. (2020) (but see also Narayanan
et al. 2018, Liang et al. 2019) the authors show with an analytical
and physically motivated model that the dust located in high- _z_
(>5) Giant Molecular Clouds (GMCs) is warmer (T∼60 K) than
locally, since theyh are characterized by a more compact structure than their local analogues. The warm dust located near starforming regions has a strong radiative efficiency, therefore it determines the shape of the SED but it does not represent the bulk
of the dust mass, expected to be at lower temperature (T∼20-30
K, Sommovigo et al. 2020).


Considering the uncertainties related to the band conversion,
we rely on the simulations performed by Privon et al. (2018). In
Privon et al. (2018), the 850 µm luminosities of simulated SEDs
are compared with the ones that would have been estimated assuming a MBB approximation with β=1.8 and T=25K (as in the
present analysis), under different observational set-ups. In particular, the scenario of observing only with ALMA Band 7, as in
our case, has been considered (see Fig. 5 in Privon et al. 2018).
The inferred luminosities are always greater than the "real" ones,
with differences of the order of ∼20% at z∼5 (and up to 30%
for the most extreme halos). These mis-matches are due to the
choice of the parameters (β and T) used to infer the 850 µm
flux from data at higher frequencies and from the fact that real
SEDs are not single-temperature blackbodies. We stress that the
results of Privon et al. (2018) are obtained at 850 µm (and not at
250 µm), but are valid also in the present case. In fact, we have
tested that our dust masses do not change if one considers 250
or 850 µm and if the flux _S_ ν _obs_ in Eq. 1 is derived by means of an
extrapolation at higher frequencies.


Article number, page 4 of 14



Considering the emissivity parameter β and the temperature
T, we test how the dust masses would change by changing
individually these parameters, by freezing the others. For the
emissivity β, as stated before, we assume β=1.8, i.e. the Galactic
value from the Planck data (Planck Collaboration et al. 2011),
again in agreement with Faisst et al. (2020a). Theoretical models
predict a wider range for β (i.e. Draine 2011) and therefore
we test how extreme values of β=1.5 (β=2) would affect our
dust mass estimates finding an increase (decrease) of the dust
masses by a negligible factor of less than ∼15% for β=1.5 (β=2)
(see also Magnelli et al. 2020). For the temperarure of the cold
dust, we explore a range of values, from T=20 K up to T=35
K. We do not consider temperatures lower than T=20 K, given
the floor imposed by the cosmic microwave background (at
z=5-6, T _CMB_ =16-19 K, respectively, see da Cunha et al. 2013).
A temperature of T=20 K would increase the dust masses
by a factor within the uncertainties considered (20%), while
assuming T=35 K would produce a decrease of the order of
60%. The dust masses derived at T=25 K are our fiducial ones,
but we will discuss also the consequences of a 10 K warmer dust.


In Table A.1 the dust masses for the 23 continuum-detected
sources are reported. We calculate the error bars on the dust
masses by summing in quadrature the relative uncertainties on
the 157 µm continuum flux (∼25%), the systematic uncertainties
due to the β emissivity (∼15%) and to the band conversion emis
∼
sivity ( 30%). The combined errors give a typical uncertainty of
0.2-0.3 dex, expressed in logM _dust_ .
The dust masses of the galaxies of the ALPINE sample are
shown as a function of redshift in Fig. 1 (red and blue filled
circles). For most of our galaxies we find dust masses in the
range log(M _dust_ / _M_ ⊙ )=7.8-8.4, with the exception of two systems showing significantly higher values (log(Mdust=M)=8.8
and log(Mdust=M)=8.9 for _DEIMOS_ _ _COS MOS_ _818760
and _DEIMOS_ _ _COS MOS_ _873756, respectively). These two
sources are the only targets presenting an ALMA continuum
flux - 1 mJy (see Table B.1. in Béthermin et al. 2020). The
empty circles in Fig. 1 correspond to the estimates obtained assuming for the dust a warmer temperature of T=35 K. In Fig. 1
we also report two collections of high-z ( _z_ ∼6−7) dust mass measurements compiled in Mancini et al. (2015) and Le´sniewska &
Michałowski (2019). Altogether, the values from these works,
which include both detections and upper limits, show a ∼ 3 dex
scatter, hence much larger than the one obtained for our galaxies.


**4.** **Scaling relation of ALPINE continuum detected**

**sources**


In this section we combine the dust masses estimates with other
physical information obtained for the ALPINE targets, and we
compare the observed dust scaling relations with predictions
from chemical evolution models in order to understand the nature and to probe the evolution of MS-selected galaxies at z∼4-5.
In the following section we present first a brief description of the
chemical models and then the comparison of the observed dust
scaling relations with the model predictions.


_4.1._ _Chemical evolution models_


The chemical evolution models considered here describe galaxies with different star formation histories, namely protospheroidals (PSPH) and spirals. The models including evolution
of interstellar dust grains were presented in Calura et al. (2008)

F. Pozzi, F. Calura, Y. Fudamoto et al.: The ALPINE-ALMA survey: Dust mass budget in the early Universe


**Fig. 2.** Top panels: M _dust_ versus age (panel a) and M _gas_ versus age (b). Middle panels: SFR versus age (c) and M _dust_ versus M ⋆ (d). Bottom panels:
M _dust_ versus SFR (e) and M _dust_ versus M _gas_ (f). M _dust_ has been computed by means of a MBB fit and assuming T=25 _K_ and β = 1.8. Blue and red
points show detections at 4 < _z_ < 5 and 5 < _z_ < 6, respectively. In panel a) the triangles around the points indicate galaxies classified as mergers
or dispersion-dominated objects (Le Fèvre et al. 2020), whereas the black vertical dashed lines indicate the age of the Universe at redshift 4.5 and
z=5.5 (corresponding to an age of the Universe of 1.35 Gyr and 1.05 Gyr, respectively). The empty squares in panel c) represent the ALPINE
galaxies non-detected in continuum. The curves represent the chemical evolution models described in Sect. 4.1. The yellow, orange and red solid
lines represent proto-spheroid models of baryonic mass 3×10 [10], 10 [11] and 10 [12] M ⊙, respectively, computed with a standard Salpeter IMF (Salpeter
1955). The light green, green and dark green dot-dashed lines are for three PSPHs with the same baryonic masses as above but characterised by
a top-heavy IMF (Larson 1998). The light cyan, cyan and blue solid lines represent models for a dwarf spiral, an intermediate-mass spiral and an
M101-like spiral, respectively (Calura et al. 2017). The stars and squares plotted along each curve and with the same colour mark the evolutionary
times of 0.1 and 0.5 Gyr, respectively.


Article number, page 5 of 14

_A&A proofs:_ manuscript no. pozzi



(see also Schurer et al. 2009, Pipino et al. 2011, Calura et al.
2014). Chemical evolution models calculate the evolution of the
abundances of various chemical elements and dust in the interstellar medium, generally starting from simple prescriptions to
describe basic processes regulating galaxy evolution. In the past,
these models have been extensively tested and used to interpret
observational, dust-related scaling relations in local and distant
galaxies (see also Calura et al. 2017).
In the models used here, PSPH represent the precursors of
local elliptical galaxies. PSPH form from the rapid collapse of a
gas cloud of primordial composition, which triggers an intense
starburst. The collapse is described by an exponential infall law,
with a characteristic e-folding time which depends on the mass
of the galaxy (Calura et al. 2014) and with typical values in the
range ∼ 0.2 − 0.5 Gyr (Palla et al. 2020). The starburst continues
until the thermal energy of the interstellar medium, computed as
the cumulative energy deposited in the ISM by type II and type
Ia SNe, equals the binding energy of the gas, computed taking
into account the gravitational contribution of the gas, of the stars
and of the dark matter halo, assumed ten times more massive
than the initial gas mass (Matteucci 1994). When this occurs, star
formation is immediately interrupted, and the galaxy is assumed
to instantaneously eject all the residual gas. The models describe
three PSPH of final baryonic mass 3 × 10 [10] _M_ ⊙, 10 [11] _M_ ⊙ and
10 [12] _M_ ⊙ .
In this work, we also consider a set of chemical evolution
models for spiral galaxies. Each model consists of several independent rings, 2 kpc wide, each of them representing a separate region of a disc. Also in spiral galaxies the formation of
the disc is described by an exponential infall, but with much
longer, radius-dependent timescales, ranging from ∼ 1 Gyr in
the innermost parts up to ∼ 10 Gyr in the outskirts, according to
the ’inside-out’ scenario (Matteucci & Francois 1989). The final
stellar masses of the spirals range from 2 × 10 [9] _M_ ⊙ to 10 [11] _M_ ⊙ .
In all our models, star formation is modelled by means of
a Schmidt (1959) law, with a higher efficiency in more massive
objects, a behaviour known as galactic downsizing (e.g., Cowie
et al. 1996; Matteucci 1994, Spitoni et al. 2020).
The stellar initial mass function (IMF) assumed for spirals
is the one of Scalo (1986), a two-slope power-law characterised
by a steeper slope (α = −1.7) with respect to the Salpeter (α =
−1.35) at stellar mass values > 2 _M_ ⊙ .
For the IMF of PSPH we test two different forms, i.e. the
Salpeter (1955) IMF and the one of Larson (1998), a topheavy IMF (THIMF). The Larson IMF has the form φ( _m_ ) ∝
_m_ [−][1][.][35] _exp_ (− _m_ _c_ / _m_ ), and assuming a characteristic mass value
_m_ _c_ = 1.2 _M_ ⊙, it is top-heavy, i.e. richer in massive stars, with
respect to the Salpeter IMF (see Calura et al. 2014). In all cases,
the IMF is assumed to be constant in time.
The use of a steeper IMF in discs is motivated by the results
by Weidner & Kroupa (2005), who have shown that, since the
disc stellar population is mostly made by dissolving open stellar clusters, the disc IMF must be significantly steeper than the
’canonical’ cluster IMF (with φ( _m_ ) ∝ _m_ [−][1][.][35] for stellar masses
above ∼ 1 _M_ ⊙ ) as the former results from a folding of the latter
with the star cluster mass function, which in general is a single
slope power law (e. g., Lada & Lada 2003).
The choice of a different IMF in different models is also motivated by the requirements of reproducing the local constraints,
including the abundance pattern observed in the Milky Way disc
for spirals (e. g., Spitoni et al. 2019) and the abundance ratios and
metal budget in local ellipticals (e. g. Calura & Matteucci 2004;
De Masi et al. 2019). For the stellar mass and SFR, the conversion between a standard IMF such as the one of Chabrier (2003)


Article number, page 6 of 14



and the one of (Salpeter 1955) amounts to ∼0.2-0.25 dex. The
same is true also when a Scalo (1986) is considered. Therefore,
the adoption of different IMFs produces variations which are in
general much smaller than the range shown by the ALPINE sample. Overall, this implies that the impact of the choice of the IMF
on the results of Fig. 2 is marginal.
The models include dust production in stars, occurring in
core-collapse SNe and intermediate-mass stars, restoring significant amounts of dust grains during the asymptotic giant branch
(AGB) phase. The set of metallicity-independent dust condensation efficiencies considered here are from Dwek (1998). Also
dust destruction in supernovae shocks and dust growth in the
ISM are taken into account. The prescriptions for these processes
are described in Calura et al. (2008) (see also Dwek 1998).


_4.2._ _Dust scaling relations_


In Fig. 2 the dust masses are reported along with other physical
quantities of the ALPINE continuum detected sources: the stellar mass (M _stars_ ), the star-formation rate (SFR), the age, and the
gas mass (M _gas_ ). The stellar mass, the SFR and the age values
have been computed by Faisst et al. (2020b) adopting a Chabrier
(2003) IMF and using the LePhare SED-fitting code (Arnouts
et al. 1999, Ilbert et al. 2006). We are aware that the age is one
of the most uncertain parameters of the SED-fitting analysis (i.e.,
Thomas et al. 2017). However, as we will discuss later, the exact
values found for this parameter do not influence significantly our
results.
For consistency with the models, we rescale M _stars_ and SFR
to a Salpeter (1955) IMF by multiplying the quantities by a factor
of 1.7 (see Speagle et al. 2014). Regarding M _gas_, we adopt the
values from Dessauges-Zavadsky et al. (2020), obtained from the

[CII] luminosities using the Zanella et al. (2018) relation, with a
typical uncertainty of ∼0.3 dex. In Fig. 2 we compare estimates
derived for the galaxies of our sample with results obtained with
the chemical evolution models presented in Sect. 4.1. The solid
circles represent the inferred quantities (red and blue for galaxies
at _z_ ∼4.5 and _z_ ∼5.5, respectively), while the curves represent the
PSPH and spiral models (see caption of Fig.2 for further details).
The evolution of the dust mass as a function of age (a) panel)
shows that the inferred M _dust_ values are in good agreement with
those obtained with PSPH models at epochs comparable to the
ages of the detected systems.
Typical dust mass values of ∼ 10 [8] _M_ ⊙ as derived in the
ALPINE sample of continuum detected sources are achievable
already at early times (typically ∼ 0.1−0.5 Gyr) in PSPH. On the
other hand, in the case of spirals only the most massive model
reaches comparable values after several Gyr of evolution (blue
line in the top-left panel), whereas the other models show much
lower M _dust_ values at any epoch. As already said, this result is
robust against the exact value of the ages of the ALPINE galaxies. In fact, in the extreme and unlikely case that the ages are all
systematically underestimated, they can not be larger than the
age of the Universe at the redshift of our sample (vertical dashed
lines in Fig.2, panel a)).
This seems that the PSPH models are the only ones that can
cover the region occupy by the observed galaxies. The other
models need > 1 Gyr to produce the M _dust_ that are observed. This
finding is due to an overall much faster, stronger evolution shown
by PSPH with respect to spirals, confirmed also by their star formation history (panel (c) in Fig.2). The SFR vs age plot shows
that most of the SFRs measured in ALPINE galaxies are consistent with the values shown by the intermediate- and low-mass
PSPH models (orange and yellow lines), with very few of them

F. Pozzi, F. Calura, Y. Fudamoto et al.: The ALPINE-ALMA survey: Dust mass budget in the early Universe



similar to the values shown by the most massive spiral models.
This plot also shows a limited time interval in which the SFR
values of the low-mass PSPH are very similar to those shown by
the massive spirals at early times (< 1 Gyr), but in other plots
these two models show a rather distinct behaviour, such as in
the M _dust_ −Age and M _dust_ −M _stars_ relations. A couple of galaxies
with particularly high M _dust_ are reproduced by the PSPH models
with a THIMF (green dashed-dotted lines). On this topic, a particularly high dust yield (defined as amount of dust per unit stellar mass, or specific dust mass) in star-forming galaxies at high
redshift was found also in other works (Calura et al. 2017 and
references therein), and several other reasons were proposed, including, beside the adoption of a THIMF (Gall et al. 2011), also
an enhanced dust accretion rate (Pipino et al. 2011; Valiante et al.
2011).
Another explanation for this result invokes a substantial revision of our current knowledge of both dust production and accretion mechanisms, which might be needed in the case that neither
destruction in SNe shocks nor accretion plays a significant role
in regulating the dust mass budget in galaxies. In a recent analysis of the dust mass budget in local and distant star-forming
galaxies, Gall & Hjorth 2018 showed that the observed dust
masses can be accounted for if the majority of the dust is formed
by SNe on short timescales, i.e. during the most recent star formation episodes. This does not exclude that other processes,
such as grain growth and destruction, may be at play in regulating the dust budget but, if their effects are non-negligible, they
need to balance each other and occur on comparable timescales.
If this is the case, several parameters related to the gas microphysics and sometimes different local thermal conditions have
to be tuned to yield comparable destruction and growth rates. A
most direct interpretation of this results is that stardust production is dominant with respect to other processes. In such case, a
high dust yield can be accommodated assuming a THIMF.
Also the analysis of the cold gas budget, as traced by the
molecular gas content and indicated by the M _gas_ vs age, supports
the result that ALPINE galaxies show properties mostly similar
to PSPH.

A further indication supporting our conclusion, is the galaxy
classification of the ALPINE targets, performed by Le Fèvre
et al. (2020), from a preliminary visual inspection analysis of the

[CII] data cubes together with the large wealth of ancillary data
(mainly HST F814W images, see Koekemoer et al. 2007, Koekemoer et al. 2011). The majority of the ALPINE [CII]-detected
galaxies have a disturbed morphology (60% including mergers or extended and dispersion dominated systems) while only
13.3% show a rotating disc (the remaining 10.7% and 16% being compact or too faint to be classified). The fraction of galaxies
with disturbed morphology become even larger (∼70%) when
considering only the continuum-detected sources. This does not
exclude that the ALPINE galaxies might be compatible with progenitors of MW-like galaxies, whose earliest assembly and starformation activity is expected to occur mostly in their spheroidal
components.
Moreover, our conclusion is fairly robust against the fact that
is based on only 23 ALPINE continuum detected galaxies. In
Fig. 2 (panel c)), we report the SFR as a function of the age
also for the ALPINE galaxies not detected in continuum (empty
squares). These sources, as expected, are less extreme, characterised by a lower SFR in comparison to the continuum detected
ones (<SFR>∼56 M ⊙ yr [−][1] and <SFR>∼180 M ⊙ yr [−][1], respectively). Nevertheless, they still occupy a parameter space between the evolutionary tracks of the PSPH and the most massive
spiral model.



**Fig.** **3.** 6 [′′] ×6 [′′] cutouts of L _UV_ binned stacks of ALMA continuum images used to derive the stacked dust masses. The upper and lower panels show stacks of galaxies at _z_ ∼4.5 and _z_ ∼5.5, respectively. Black solid
contours show 2,3,4,5 σ. While in the _z_ ∼4.5 bins all stacks have a clear
detection at - 4σ, in the _z_ ∼5.5 bins the stacks have a clear detection
only at the highest L _UV_ bin. In Table 1 the results of the stacking analysis are summarised, including the number of sources stacked in each
bin of L _UV_ .


In conclusion, our study of the scaling relations and our comparison with chemical evolution models indicates that ALPINE
galaxies mostly show dust masses and SFR values expected in
young, star-forming PSPH. In most cases, a Salpeter IMF is sufficient to account for the observed dust masses, i.e. in general
there is no particular need to invoke mechanisms such as a topheavy IMF to enhance dust production, as seen e. g. in a sample of starbursts observed by Herschel (Calura et al. 2017). Our
models for disc galaxies show a slower buildup of the dust mass
and, at these epochs, fail to account for the observed dust masses.
Our study strongly outlines the need for statistical samples
of galaxies at high- _z_ with the SED properly sampled in the farIR/sub-mm part of the spectrum, in order to better derive the dust
properties (mainly the temperature and the mass). This will be
achieved by exploiting the synergies between sub-mm/mm (i.e.
ALMA, NOEMA) and far-IR facilities, with features similar to
the SPace Infrared telescope for Cosmology and Astrophysics
(SPICA [1], Roelfsema et al. 2018) or to the Origins Space Telescope (OST [2] ) which, altogether, will enable a full characterisation of the spectrum from the Wien (FIR) up to the RayleighJeans regimes (sub-mm/mm).
This will allow us to improve our understanding of early dust
production and to increase the current samples of galaxies with
measured dust masses at high-redshift. In the forthcoming future, the James Webb Space Telescope (JWST, Gardner et al.
2009), working in the near-IR and mid-IR regimes, will allow us
to better constrain the stellar masses, ages, metallicities and star
formation histories of galaxies at very high-redshift.


**5.** **Dust mass density at** _**z**_ ∼ **5**


In the following section, we derive an estimate of the dust mass
density (DMD) in the redshift range of the ALPINE survey
(4.3 < _z_ < 4.6 and 5.1 < _z_ < 5.9). Taking into account that
the ALPINE is a targeted survey of pre-selected galaxies, we divide the derivation of the DMD in two steps: first, we estimate


1 http://spica-missions.org
2 http://origins.ipac.caltech.edu


Article number, page 7 of 14

_A&A proofs:_ manuscript no. pozzi



**Fig.** **4.** M _dust_ versus L _UV_ for the ALPINE targets. Blue and red points
show individual FIR continuum detections at 4 < _z_ < 5 and 5 < _z_ < 6,
respectively. Open downward triangles show 3σ upper limits of individual IR non-detections. Stacks with detections at _z_ < 5 and _z_ - 5, are
shown as blue and red squares, respectively. The non-detection of stacks
are indicated by a downward arrows. M _dust_ from the stacked ALMA
continuum fluxes have been estimated using the same expression as for
the targets (Eq. 1). The Bayesian linear fit of all the stacked values (detections and upper limits) is shown by the black line/light-blue lines,
which also illustrate the probability distribution of the fit at 1σ confidence level. The resulting best-fit is _log_ ( _M_ _dust_ ) = (1.16 [0] − [.] 0 [68] .57 [)(] _[log]_ [(] _[L]_ _[UV]_ [)][ −]
11.) + (−0.11 [0] − [.] 0 [10] .15 [)][ +][ 7][.][76] [(dispersion] [σ] [ <] ∼ [0][.][2] [dex,] [Pearson] [rank] [coe][ffi][-]
cient of 0.76 and p-value 0.08, with the Pearson coefficient computed
considering all data as detections)

.


the contribution of the UV-selected galaxies (ρ _dust_, _UV_ ), which
sets a lower limit to the DMD; second, we consider the continuum serendipitously detected sources in the redshift bin of the
ALPINE targets, trying to evaluate the total DMD (ρ _dust_, _IR_ ).


_5.1._ _Contribution to the DMD from UV-selected galaxies_


The ALPINE targets are UV-selected sources, with UVmagnitude L _UV_ - 0.5 _L_ [⋆] (see Sect. 2). Among the 118 ALPINE

∼
targets, 23 sources ( 20% of the sample) are far-IR continuum
detected and, as a consequence, for deriving the average properties of the parent UV-selected population, we need to take into
account also the contribution of the non-detected galaxies. To
this aim, we performed a stacking analysis on the ALMA maps.
We perform stacking using the λ 158µ _m_ rest-frame continuum
images centered on the UV counterpart positions, including both
individual detections and non-detection in order to avoid biases. The procedure used has been extensively described in the
ALPINE paper of Khusanova et al. (2020a) (see also Fudamoto
et al. 2020). Here we briefly summarise the main points. We use
median stacking on the UV counterpart positions of both detected and non detected objects. As for the detections, we adopt a
3.5σ threshold. In case of non detection, we use the conservative
3σ upper limits by adding three times the background RMS to
the local maximum (see Béthermin et al. 2020.) We performed
the stacking in two redshift bins, at _z_ < 5 and z> 5, and we
further split the sample in bins of UV luminosity. The bins have
been chosen to have an almost equal number of sources in each
interval (∼ 20). In Table 1 the results of our stacking analysis are
summarised, while in Fig. 3 the stacked images are shown. From


Article number, page 8 of 14



the stacks at _z_ < 5, we detected significant continuum emission from all the L _UV_ bins (Fig. 3, upper panels), while from
the stacks at _z_ - 5, we detected continuum emission only in the
highest L _UV_ bin (Fig. 3, lower panels).
In Fig. 4 the dust masses as a function of their UV-luminosity
have been reported for the continuum detected sources (23 objects), for the non-detections and from the stacked images. For
the non-detections and for the stacked images, the same procedure adopted for the detected sources has been used to estimate
the dust masses, considering the 3σ flux upper limits and the
stacked results as rest-frame 158 µm continuum fluxes, respectively. The black line represents the linear log(M _dust_ )-log(L _UV_ )
relation obtained using the stacked values. We performed the fit
using the method described in Feldmann (2019), for evaluating
the likelihood in presence of censored data. This method is a
generalization of the statistical approach of Kelly (2007) and is
implemented in the _LeoPy_ python package. The evaluation of
the likelihood has been combined with a Bayesian tool to realize
Monte Carlo Markov Chain for parameter space exploration, implemented in the _emcee_ python package (Foreman-Mackey et al.
2013). The fit results with a poor significance level with the coefficient constrained at 1-2σ (Pearson rank coefficient of 0.76 and
p-value of 0.08, estimated considering all data as detections).
Regardless of the poor significance of the fit, we are confident
about the L _UV_ -M _dust_ correlation, as a secondary effect of the relation between SFR and M _dust_, in galaxies where L _UV_ captures
most of the SFR (as expected for the ALPINE targets, characterized generally by low extinction values, < ( _E_ − _V_ ) > ∼0.08, see
Faisst et al. 2020b).
The obtained relation allows us to derive the DMD for the
UV-selected sources. In particular, since the ALPINE sample is
not a volume-limited sample, to derive the comoving density of
our physical property (M _dust_ ), we use L _UV_ as proxy of M _dust_, following the same approach described in a companion ALPINE
paper (Khusanova et al. 2020a) where the authors derived the
Star Formation Rate Density (SFRD) starting from the continuum detected ALPINE UV-selected sources.
Following Khusanova et al. (2020a) (see also Fontana et al.
2004, Pozzi et al. 2020), we estimate the comoving density of
our physical property by convolving the volume density of the
proxy with the mean M _dust_ -L _UV_ relation as:


ρ _dust_, _UV_ = < _M_ _dust_ - ( _x_ )φ( _x_ ) _dx_ (2)
�


where _x_ is the L _UV_ and φ( _x_ ) is the UV-luminosity function
(UVLF). In this operation we have converted the mean relation
found in log space (see Fig. 4) to the mean relation in linear

space as:



_LUVdust_ [>][+] [2][.][3][×] 2 [σ][2]



_Mdust_
< _M_ _dust_ / _L_ _UV_ >= 10 [(][<][log] _LUV_



2 [σ] ) (3)



where σ is the dispersion of the data in log space as obtained by
the Bayesian fit (σ∼0.2 dex, see Fig. 4).
Two main caveats could affect our method and should be
mentioned: first, we consider the ALPINE targets as a fair representative sample of the UV-sources; second, we extrapolate to
a broader L _UV_ range, the log(M _dust_ )-log(L _UV_ ) relation found for
10.4 <log( _L_ _UV_ ) < 11.5. Considering the first issue, we rely on
Faisst et al. (2020b) (their Fig. 17), where it has been shown
how the ALPINE sources occupy the same region of the parent
sample in COSMOS (rest-frame UV/optical selected at _z_ ∼5) in
the M _star_ −SFR plane, leading the authors to conclude that the

F. Pozzi, F. Calura, Y. Fudamoto et al.: The ALPINE-ALMA survey: Dust mass budget in the early Universe


ALPINE sources are a fair representation of UV-selected starforming _z_ - 4 galaxies. This is not to be intended that the
ALPINE galaxies are a representation of all the star-forming
galaxies since we are aware that the UV-selection does not take
into account ultra-dusty galaxies. We discuss this point in Sec.
5.3. Considering the second issue, we estimate two quantities:
the dust mass density derived by integrating the UV-luminosity
only over the ALPINE UV-luminosity range and the dust mass
density obtained by extrapolating the relation down to fainter UV
luminosity not sampled by the ALPINE targets, and integrating
over the commonly used 0.03 _L_ [⋆] − 100 _L_ [⋆] range (ρ _dust_, _UV_ ).
Given the procedure described above, we have estimated the
uncertainty on ρ _dust_, _UV_ combining the uncertainties affecting the
UVLF determination and the log(M _dust_ )-log(L _UV_ ) relation. At
_z_ ∼5, the UVLF is quite well constrained, the main uncertainty
being the faint-end slope α (i.e. Bouwens et al. 2015, Ono et al.
2018, Khusanova et al. 2020b). We use the derivation from Ono
et al. (2018) and we estimate the associated uncertainty by varying each of the UVLF parameters (α, L ⋆ and Φ ⋆ ) within 1-σ (see
Table 7 in Ono et al. 2018). We find an uncertainty of ∼0.2 dex
in ρ _dust_, _UV_, of the same order of the uncertainties derived from
the 1σ dispersion of the log(M _dust_ )-log(L _UV_ ) relation.
The results are shown in Fig. 6 and reported in Table 2.


_5.2._ _Contribution to the DMD from FIR blind detected_
_galaxies_



In the previous section, by integrating the UVLF over the wide
0.03 _L_ [⋆] − 100 _L_ [⋆] range, we have estimated the value of the
DMD of the population of rest-frame UV-selected galaxies. In
the present section, we estimate the DMD from the population
of rest-frame FIR selected galaxies. To this aim, we consider
the blind continuum non-target detections in the ALPINE survey in the redshift range corresponding to the ALPINE targets
(4.1 < _z_ < 5.9) (see Sec 2). For these sources we estimated
the dust masses as done for the ALPINE targets. We consider
now L _IR_ as proxy of M _dust_ and as luminosity function of the
proxy the recent determination from Gruppioni et al. (2020). Of
the 10 sources blindy detected, 5 sources were found to have
a spectroscopic redshift (from the detection of the [CII] emission line) very close to the ALPINE central targets (see Sect.
3.2 in Gruppioni et al. 2020). Since these sources are possibly
related to an overdensity (see also Lemaux et al. 2018, Loiacono et al. 2020 on this issue), we consider the conservative
IRLF determination from Gruppioni et al. (2020), where these
sources have been removed. For L _IR_ we consider the values measured with the SED obtained from stacking the photometric datapoints of the ALPINE analogs galaxies in the COSMOS field
from λ _rest_ - 40µm. In Fig. 5 (Top) the values of M _dust_ as a function of L _IR_ are reported together with the best-fitting relation.
The fit results with a high-level of significance (Pearson rank
coefficient 0.97 and p-value of 10 [−][5] ).
As for the DMD obtained for the UV-galaxy population,
we estimate the comoving density of our physical parameter
(ρ _dust_, _IR_, where now the subscript _IR_ stands for derived from IRselected sources) by convolving the volume density of the proxy
(L _IR_ ) with the M _dust_ -L _IR_ relation as:


ρ _dust_, _IR_ = < _M_ _dust_ - φ( _x_ ) _dx_ (4)
�


where now _x_ is L _IR_ and φ( _x_ ) is the IR-luminosity function
(IRLF). As done for L _UV_, for converting the mean relation from



**Fig.** **5.** Top: M _dust_ versus L _IR_ for the non-target serendipitously detected sources in the ALPINE redshift range (4.1< _z_ < 5.9). The
corresponding M _dust_ have been calculated using the same expression
as for the ALPINE targets (Eq. 1). The Bayesian linear fit is shown
by the black line/light-blue lines, which also illustrate the probability
distribution of the fit at 1σ confidence level. The resulting best-fit is
_log_ ( _M_ _dust_ ) = (1.01 [0] − [.] 0 [11] .11 [)(] _[log]_ [(] _[L]_ _[IR]_ [)][ −] [12][.][2)][ +][ (][−][0][.][0] − [0][.] 0 [05] .05 [)][ +][ 8][.][8 (dispersion]
σ [<] ∼ [0][.][05 dex, Pearson rank coe][ffi][cient of 0.97 and p-value 10] [−][5] [)]
. Bottom: Distribution of the L _IR_ for the target continuum detected (blue histogram, <log(L _IR_ ) >= 11.6 [+] − [0] 0 [.] . [1] 2 [)] [and] [for] [the]
serendipitously detected (red histogram, <log(L _IR_ ) >= 12.1 − [+] 0 [0] . [.] 3 [9]
) ALPINE sources. L _IR_ have been estimated using the stacked
SED from ALPINE analogues in the COSMOS field from
Béthermin et al. (2020).


log space to linear space we have taken into account the dispersion, although given the small dispersion ( [<] ∼ [0][.][05 dex), the second]
term in Eq. 3 is negligible.
As for the ρ _dust_, _UV_, also for ρ _dust_, _IR_ we consider two quantities: a lower limit obtained integrating the IRLF only in the
IR luminosity range sampled by the data (11.7 <log(L _IR_ )< 13),
and the value (ρ _dust_, _IR_ ) obtained integrating the IRLF in the commonly used IR range (ρ _dust_, _IR_ ; 9 <log( _L_ _IR_ ) < 14, see Gruppioni
et al. 2020).

The uncertainty on ρ _dust_, _IR_ depends on the uncertainties
affecting the IRLF and on the uncertainties affecting the
log(M _dust_ )-log(L _IR_ ) relation. The former has been computed
considering the 1σ uncertainty derived through the MCMC anal

Article number, page 9 of 14

_A&A proofs:_ manuscript no. pozzi



|redshift|N|logL<br>UV<br>[L ]<br>⊙|logM<br>dust<br>[M ]<br>⊙|
|---|---|---|---|
|4.4 <_ z_ < 4.6|23 (2)<br>23 (8)<br>21(5)|10.4 - 10.9<br>10.9 - 11.1<br>11.1 - 11.6|7.53+0.15<br>−0.17<br>7.83+0.13<br>−0.14<br>7.83+0.11<br>−0.14|
|5.1 <_ z_ < 5.9|25 (0)<br>10 (1)<br>15(7)|10.4 - 10.9<br>10.9 - 11.1<br>11.1 - 11.6|<7.5<br><7.6<br>7.72+0.2<br>−0.2|


**Table** **1.** Results of the stacking analysis. Median M _dust_ are reported,
derived from the median stacked fluxes obtained as described in Sect.
5.1 and using equation 1 as for the targets. The upper limits are at 3σ.
The number of sources stacked in each bin and indivially detected are
also reported.


ysis of the IRLF estimated by Gruppioni et al. (2020) (see their
Table 4). This term accounts for a 1σ dispersion of ∼0.3-0.5 dex
in ρ _dust_, _IR_, significantly higher than that derived from the dispersion of the log(M _dust_ )-log(L _IR_ ) relation ( [<] ∼ [0][.][05 dex).]
The results are shown in Fig. 6 and reported in Table 2.


_5.3._ _Discussion on the DMD derivation_


In Fig. 6 we report the evolution of the comoving DMD as
a function of the look-back time from our analysis together
with determinations from other observational works and with
model predictions. The ALPINE derivations are reported at 12 <
_t_ _lookback_ < 12.5 Gyrs, corresponding to the redshift range of
the ALPINE sources (in case of the derivation from the UVpopulations a slightly wider range is considered for graphic convenience). The values obtained from the UV-selected population (IR-selected population), obtained by integrating the UVLF
(IRLF) in the extended UV (IR) luminosity range are represented
by a blue (red) point. The boxes around the points represent the
1σ associated uncertainties, with the large dispersion of ρ _dust_, _UV_
reflecting the large dispersion in the log(M _dust_ )-log(L _UV_ ) relation
(see Fig. 4, Top).
The value of ρ _dust_, _UV_ is ∼30 % of ρ _dust_, _IR_ (although consistent within 1σ), and this is not surprising, since the UV-selected
population is not representative, by construction, of the most
dusty obscured galaxies which are present in the blind IR selection. This is supported by the comparison of the L _IR_ distribution of the ALPINE targets and of the serendipitously detected
sources. The serendipitous sources show <log(L _IR_ )>= 12.1 [+] − [0] 0 [.] . [9] 3 [,]
hence they are generally brighter than the ALPINE targets, with
<log(L _IR_ ) >= 11.6 − [+] 0 [0] . [.][1] 2 [(see Fig.][ 5][, Botton). While this di][ff][erence]
alone cannot be conclusive since it could be partially caused
by different S/N cuts (S/N=3.5 and 5, for our targets and the
serendipitously sources, respectively, see Béthermin et al. 2020),
beside their different IR luminosity distribution, also the fact that
only half of the serendipitous sources (see Gruppioni et al. 2020)
are detected in the UV at magnitudes _z_ ∼25.9 (Laigle et al. 2016)
further supports our hypothesis.
Our result is also in line with the one found recently by Gruppioni et al. (2020) which concerns the star-formation rate density
(SFRD). By deriving the SFRD from IR sources serendipitously
detected in ALPINE, the authors found that the difference with
literature UV results increases with redshift, reaching a factor
∼10 at _z_ ∼6.
In Fig. 6 we also show previous determinations of ρ _dust_ (see
references in the figure legend and caption). In the redshift range
sampled by the ALPINE survey, recent determinations were derived by Péroux & Howk (2020) and Magnelli et al. (2020).


Article number, page 10 of 14



Péroux & Howk (2020) (salmon filled squares in Fig. 6) estimated the DMD indirectly, by convolving the mass density of
neutral gas with the dust-to-gas (DTG) ratio. The density of neutral gas was derived from an extensive literature collection of
different measurements, mainly based on high- _z_ quasar spectra
absorbing features, whereas the DTG was estimated from the
depletions of different heavy elements into the solid phase. The
determinations from Péroux & Howk (2020) are consistent with
our ρ _dust_ value obtained from UV-selected galaxies, whereas it is
lower than our ‘fiducial value’ derived from IR selected galaxies.
However, Péroux & Howk (2020) cautioned the reader against a
potential selection bias affecting their estimate (see their Sec.
3.2.3), as extremely dusty systems might be missing from their
optically-selected quasar sample. The large uncertainty (up to
50%) affecting our determination of ρ _dust_ for IR selected galaxies
reflects the small sample used to estimate the IRLF. This stresses
further the need for future investigations and for future space IR
high-sensitivity instruments suitable for tracing the dust content
of high-redshift galaxies.

Magnelli et al. (2020) estimate the DMD directly, thanks to
ALMA observations from the ASPECS LP survey (yellow filled
squared in figure). The ASPECS LP survey (González-López
et al. 2020) was obtained in Band 6 (1.2 mm), over an area of
∼4.2 arcmin [2] . The reported determinations from the ASPECS
survey from 0.3 < _z_ < 5.5 have been computed by stacking the
ALMA maps at the positions of _H_ -band selected galaxies above
a stellar mass of 10 [8] M ⋆ in distinct redshift bins. The points
corresponding to 3.2 < _z_ < 4.5 (4.5 < _z_ < 5.5), have been obtained by stacking 44 (9) galaxies, but, since the sample can not
be considered as stellar mass complete, these measurements can
only be considered lower limits (see Table 1 in Magnelli et al.
2020). Our values of ρ _dust_ obtained from the UV-selected and
the FIR-selected galaxies, at the redshift of the ALPINE survey (4.5< _z_ <5.9), are consistent with the lower limits from
the ASPECS survey obtained in the two highest redshift bins
(3.2 < _z_ < 4.5 and 4.5 < _z_ < 5.5).
The general DMD as a function of the cosmic time shows a
mild increase from _z_ ∼5 up to the cosmic noon (1 < _z_ < 3) (a
factor of ∼2.5 in our analysis), followed by a smooth decline (a
factor of ∼3) up to the local Universe (see also Driver et al. 2018,
Pozzi et al. 2020, Magnelli et al. 2020).
By comparing the DMD and the SFRD, as already stated by
Magnelli et al. (2020), at _z_ < 2 both quantities show a decline
toward the local Universe, but the decline of the DMD is less
pronounced than that observed for the SFRD (a factor ∼3-4 instead of ∼8). At _z_ - 3, the SFRD derived from IR data shows
an almost flat behaviour (Gruppioni et al. 2020 and references
within), while the DMD shows a mild decline (a factor ∼2.5). We
postpone the interpretation of these data to a theoretical work.
Nevertheless, we stress that the cosmic dust mass at _z_ ∼5 may not
have reached its maximum value yet, and this could be partially
explained considering the typical dust production timescales, i.e.
the time after which the dust mass reaches its maximum in galaxies, which ranges from a few 0.1 Gyr up to several Gys in spirals
and proto-spheroids, respectively (see panel a) in Fig. 2).
In Fig. 6 we also show the predictions from models. The
model from Gioannini et al. (2017) is the one that best reproduces the global trend shown by the DMD evolution from the
local Universe up to _z_ ∼5. This is not a cosmological model, but
a phenomenological one that combines the chemical evolution
of different galaxy types (Calura et al. 2008) with the evolution
of different galaxies as derived from Pozzi et al. (2015), based on
the IRLF from Gruppioni et al. (2013). The results of Popping
et al. (2017) and Vijayan et al. (2019) were obtained by means

F. Pozzi, F. Calura, Y. Fudamoto et al.: The ALPINE-ALMA survey: Dust mass budget in the early Universe



|log(ρdus ρ|st) z∼5 ρ|
|---|---|
|log(ρ_dust_,_UV_)<br>[M⊙Mpc−3]|_log_(ρ_dust_,_IR_)<br>[M⊙Mpc−3]|
|4.8+0.4<br>−1.0<br>> 4.3|5.3+0.5<br>−0.3<br>> 4.8|


**Table** **2.** Cosmic dust mass density derived from the ALPINE survey at _z_ ∼5. The left column reports the measurement derived from the
ALPINE UV-selected galaxies using L _UV_ as proxy for M _dust_ and integrating the UVLF in the typical 0.03 _L_ [⋆] −100 _L_ [⋆] range. The right column
reports the measurement derived from the serendipitous IR-detected
sources using L _IR_ as proxy for M _dust_ and integrating the IRLF in the
typical 9 < _log_ ( _L_ _IR_ ) < 14 range. We also report in the second row the
lower limits obtained by integrating the UVLF and IRLF only in the
range sampled by the detected sources (10.4 <log( _L_ _UV_ ) < 11.5 and
11.2 <log( _L_ _IR_ ) < 13, respectively).


of cosmological, semi-analytical galaxy formation models. They
both roughly account for the observed decrease of the DMD at
high-z ( _z_ - 3), but they fail to reproduce the decline at lower _z_
and they overestimate the dust mass budget detected locally in
resolved galaxies.
On the other hand, the models from Aoyama et al. (2018) and
Li et al. (2019) are based on cosmological hydrodynamic simulations. They are globally inconsistent with the data, severely
overestimating the DMD at _z_ < 1. At higher redshift, the model
from Aoyama et al. (2018) is in fair agreement with the observations, whereas the model from Li et al. (2019) underestimates
our ’fiducial’ DMD by up to a factor of ∼10.
Clearly, the DMD at high- _z_ needs further investigation from
both an observational and a theoretical point of view. From the
observational side, we stress that the DMD is estimated assuming our ’fiducial’ temperature of T=25 K, a choice made also in
several other studies (e. g. Scoville et al. 2014, Magnelli et al.
2020). As stated in Sec. 3, a warmer dust mass (T= 35 K) would
reduce the DMDs by a factor of 60%.
In order to shed more light on the trend of the DMD at z>2,
in particular in relation with the cosmic SFRD, a significant step
forward will be achieved from the synergy of far-IR and submm/mm facilities, allowing to consider at least two dust components, i.e. the warm and the cold one. This will be possible when
the ALMA data will be complemented by data from a future farIR satellite similar to SPICA, with a sensitivity more than an
order of magnitude better than Herschel (Roelfsema et al. 2018).


**6.** **Summary**


We use observations of the ALPINE survey to study the dust
mass content of normal star-forming galaxies at high- _z_ ( _z_ ∼5) and
to provide, for the first time, an estimate of the cosmic dust mass
density (DMD) at such high look-back time.
ALPINE is a targeted survey specifically designed to detect
the bright [CII] 158 µm line in 118 UV-selected galaxies in the
redshift range (4.4< _z_ <5.9). For the aims of the present analysis, we consider the rest-frame FIR continuum emission of the
ALPINE galaxies (individually detected or their stacks) and the
FIR continuum emission of the blind serendipitously detected
galaxies in the ALPINE area.
Dust masses are measured from the continuum emission at
250 µm (see Gilli et al. 2014), extrapolated from the 157 µm
ALMA data, assuming a mass-weighted temperature of 25 K and



a dust emissivity of β=1.8 Our main results can be summarized
as follows:


**–** We combine the dust masses of the 23 ALPINE continuum
detected sources with other robustly determined physical parameters derived from SED-fitting (i.e. Age, M ⋆, SFR) or
from the ALPINE observations themselves (i.e. M _gas_ ) to settle the evolutionary stage of normal star-forming galaxies at
_z_ ∼5. To this purpose, we compare the observed dust scaling relation with the evolutionary tracks predicted by chemical models for spiral galaxies and for precursors of local elliptical galaxies of different masses (called proto-spheroids,
PSPH). From the analysis of several scaling relations, we
conclude that our galaxies show dust masses and SFR values
typically consistent with intermediate- and low-mass PSPH
models. Our models indicate that galaxy discs, such as that
of the MW, show at early epochs SFR values < 10 _M_ ⊙ / _yr_
and dust masses much lower than the ones measured in
ALPINE galaxies. Our conclusion is confirmed also by the
non-detected galaxies, which, even if less extreme than the
actual detections, in the SFR-Age diagram generally show
SFR values compatible with the ones of the massive discs
which, in the galactic downsizing picture, at these epochs
are expected to be more intensely star-forming than low- and
intermediate- mass spirals. It is worth noting that our results
do not exclude that the ALPINE galaxies might be compatible with the progenitors of MW-like galaxies, whose earliest assembly and star-formation activity is expected to occur
mostly in their spheroidal components, i.e. in their bulges (e.
g., Calura et al. 2012; Roca-Fàbrega et al. 2016; Fragkoudi
et al. 2020).


**–** We estimate ρ _dust_ at _z_ ∼5 for UV-selected and FIR-selected
galaxies, using L _UV_ and L _IR_ as proxies for M _dust_, respectively. In the first case, we use the log(M _dust_ )-log(L _UV_ ) relation found for the ALPINE galaxies (considering both the
detected and the non-detected sources) and the convolution with the UVLF; in the second case, we consider the
log(M _dust_ )-log(L _IR_ ) relation found for the 10 blindly FIRdetected sources and the convolution with the IRLF. The
derived ρ _dust_, _UV_ is ∼30 % ρ _dust_, _IR_, although the two estimates are marginally consistent at 1σ. Our result supports
the conclusion that UV-selected galaxies miss the most obscured/dusty objects and we consider ρ _dust_, _IR_ as our fiducial
value.


**–** We compare our fiducial ρ _dust_ at _z_ ∼5 with the predictions
from models, taking into account also the ρ _dust_ determinations at lower _z_ from the literature. The phenomenological
model from Gioannini et al. (2017) is the model that best reproduces the observed evolution of ρ _dust_ . Since this model
is basically built upon the observed evolution of the cosmic
SFR, this result indicates that it can roughly account for the
expected timescales for dust production in galaxies. On the
other hand, the ab-initio cosmological, semi-analytical models of Popping et al. (2017) and Vijayan et al. (2019) and
and the cosmological simulations of Li et al. (2019) roughly
account for the observed evolution of ρ _dust_ dust at _z_  - 1,
but they overestimate the dust mass budget at lower redshift,
failing in reproducing the decreasing trend observed at _z_ < 1.
These results indicate that our physical understanding the
cosmic evolution of the dust mass needs to be improved.


Our study strongly outlines the need for statistical samples
of galaxies at high- _z_ with a full characterisation of the IR


Article number, page 11 of 14

_A&A proofs:_ manuscript no. pozzi



spectrum, from the Wien up to the Rayleigh-Jeans regimes.
This can be achieved by exploiting the synergies between
sub-mm/mm (i.e. ALMA, NOEMA) and far-IR facilities.


_Acknowledgements._ This paper is dedicated to the memory of Olivier Le Fèvre,
PI of the ALPINE survey. We are grateful to an anonymous referee for valuable suggestions that improved the paper. FP thanks Simone Bianchi for useful
discussion on the dust properties. We acknowledge support from grant PRIN
MIUR 2017- 20173ML3WW_001. FP also acknowledges support from the
INAF man-stream program ’Gas-DustPedia: A definitive view of the ISM in
the Local Universe’. FC also acknowledges support from the INAF main-stream
(1.05.01.86.31). D.R. acknowledges support from the National Science Foundation under grant numbers AST-1614213 and AST-1910107. D.R. also acknowledges support from the Alexander von Humboldt Foundation through a Humboldt Research Fellowship for Experienced Researchers. G.C.J and R.M acknowledge ERC advanced grant 695671 ’QUENCH’ and support by the Science
and Technology Facilities Council (STFC).


**References**


Aoyama, S., Hou, K.-C., Hirashita, H., Nagamine, K., & Shimizu, I. 2018, MNRAS, 478, 4905


Arnouts, S., Cristiani, S., Moscardini, L., et al. 1999, MNRAS, 310, 540


Beeston, R. A., Wright, A. H., Maddox, S., et al. 2018, MNRAS, 479, 1077


Béthermin, M., Fudamoto, Y., Ginolfi, M., et al. 2020, A&A, 643, A2


Bianchi, S. 2013, A&A, 552, A89


Bouwens, R. J., Illingworth, G. D., Oesch, P. A., et al. 2015, ApJ, 803, 34


Calura, F., Gibson, B. K., Michel-Dansac, L., et al. 2012, MNRAS, 427, 1401


Calura, F., Gilli, R., Vignali, C., et al. 2014, MNRAS, 438, 2765


Calura, F. & Matteucci, F. 2004, MNRAS, 350, 351


Calura, F., Pipino, A., & Matteucci, F. 2008, A&A, 479, 669 (CPM08)


Calura, F., Pozzi, F., Cresci, G., et al. 2017, MNRAS, 465, 54


Capak, P. L., Carilli, C., Jones, G., et al. 2015, Nature, 522, 455


Cassata, P., Morselli, L., Faisst, A., et al. 2020, A&A, 643, A6


Chabrier, G. 2003, ApJ, 586, L133


Combes, F., Rex, M., Rawle, T. D., et al. 2012, A&A, 538, L4


Conley, A., Cooray, A., Vieira, J. D., et al. 2011, ApJ, 732, L35


Cowie, L. L., Songaila, A., Hu, E. M., & Cohen, J. G. 1996, AJ, 112, 839


da Cunha, E., Groves, B., Walter, F., et al. 2013, ApJ, 766, 13


De Masi, C., Vincenzo, F., Matteucci, F., et al. 2019, MNRAS, 483, 2217


Decarli, R., Walter, F., Gónzalez-López, J., et al. 2019, ApJ, 882, 138


Dessauges-Zavadsky, M., Ginolfi, M., Pozzi, F., et al. 2020, A&A, 643, A5


D’Odorico, V., Feruglio, C., Ferrara, A., et al. 2018, ApJ, 863, L29


Draine, B. T. 2011, Physics of the Interstellar and Intergalactic Medium


Draine, B. T. & Li, A. 2007, ApJ, 657, 810


Driver, S. P., Andrews, S. K., da Cunha, E., et al. 2018, MNRAS, 475, 2891


Dudzeviˇci¯ut˙e, U., Smail, I., Swinbank, A. M., et al. 2020, arXiv e-prints,
arXiv:2010.06605


Dunlop, J. S., McLure, R. J., Biggs, A. D., et al. 2017, MNRAS, 466, 861


Dunne, L., Eales, S. A., & Edmunds, M. G. 2003, MNRAS, 341, 589


Dunne, L., Gomez, H. L., da Cunha, E., et al. 2011, MNRAS, 417, 1510


Article number, page 12 of 14



Dwek, E. 1998, ApJ, 501, 643


Faisst, A. L., Fudamoto, Y., Oesch, P. A., et al. 2020a, MNRAS, 498, 4192


Faisst, A. L., Schaerer, D., Lemaux, B. C., et al. 2020b, ApJS, 247, 61


Feldmann, R. 2019, Astronomy and Computing, 29, 100331


Fontana, A., Pozzetti, L., Donnarumma, I., et al. 2004, A&A, 424, 23


Foreman-Mackey, D., Hogg, D. W., Lang, D., & Goodman, J. 2013, PASP, 125,
306


Fragkoudi, F., Grand, R. J. J., Pakmor, R., et al. 2020, MNRAS, 494, 5936


Franco, M., Elbaz, D., Béthermin, M., et al. 2018, A&A, 620, A152


Fudamoto, Y., Oesch, P. A., Faisst, A., et al. 2020, arXiv e-prints,
arXiv:2004.10760


Fujimoto, S., Silverman, J. D., Bethermin, M., et al. 2020, arXiv e-prints,
arXiv:2003.00013


Gall, C. & Hjorth, J. 2018, ApJ, 868, 62


Gall, C., Hjorth, J., & Andersen, A. C. 2011, A&A Rev., 19, 43


Gardner, J. P., Mather, J. C., Clampin, M., et al. 2009, Astrophysics and Space
Science Proceedings, 10, 1


Giacconi, R., Zirm, A., Wang, J., et al. 2002, ApJS, 139, 369


Gilli, R., Norman, C., Vignali, C., et al. 2014, A&A, 562, A67


Ginolfi, M., Jones, G. C., Béthermin, M., et al. 2020a, A&A, 643, A7


Ginolfi, M., Jones, G. C., Béthermin, M., et al. 2020b, A&A, 633, A90


Gioannini, L., Matteucci, F., & Calura, F. 2017, MNRAS, 471, 4615


González-López, J., Novak, M., Decarli, R., et al. 2020, ApJ, 897, 91


Gruppioni, C., Béthermin, M., Loiacono, F., et al. 2020, A&A, 643, A8


Gruppioni, C., Pozzi, F., Rodighiero, G., et al. 2013, MNRAS, 432, 23 (GPR13)


Hodge, J. A. & da Cunha, E. 2020, arXiv e-prints, arXiv:2004.00934


Hodge, J. A., Karim, A., Smail, I., et al. 2013, ApJ, 768, 91


Ilbert, O., Arnouts, S., McCracken, H. J., et al. 2006, A&A, 457, 841


Jones, G. C., Béthermin, M., Fudamoto, Y., et al. 2020, MNRAS, 491, L18


Kaasinen, M., Scoville, N., Walter, F., et al. 2019, ApJ, 880, 15


Kelly, B. C. 2007, ApJ, 665, 1489


Khusanova, Y., Béthermin, M., Le Fèvre, O., et al. 2020a, arXiv e-prints,
arXiv:2007.08384


Khusanova, Y., Le Fèvre, O., Cassata, P., et al. 2020b, A&A, 634, A97


Koekemoer, A. M., Aussel, H., Calzetti, D., et al. 2007, ApJS, 172, 196


Koekemoer, A. M., Faber, S. M., Ferguson, H. C., et al. 2011, ApJS, 197, 36


Lada, C. J. & Lada, E. A. 2003, ARA&A, 41, 57


Laigle, C., McCracken, H. J., Ilbert, O., et al. 2016, ApJS, 224, 24


Laporte, N., Ellis, R. S., Boone, F., et al. 2017, ApJ, 837, L21


Larson, R. B. 1998, MNRAS, 301, 569


Le Fèvre, O., Béthermin, M., Faisst, A., et al. 2020, A&A, 643, A1


Lemaux, B. C., Le Fèvre, O., Cucciati, O., et al. 2018, A&A, 615, A77


Lemaux, B. C., Le Floc’h, E., Le Fèvre, O., et al. 2014, A&A, 572, A90


Le´sniewska, A. & Michałowski, M. J. 2019, A&A, 624, L13


Li, Q., Narayanan, D., & Davé, R. 2019, MNRAS, 490, 1425

F. Pozzi, F. Calura, Y. Fudamoto et al.: The ALPINE-ALMA survey: Dust mass budget in the early Universe


**Fig. 6.** Evolution of the comoving dust mass density (ρ _dust_ ) as a function of the look-back time. Our determinations are shown at _t_ _lookback_ ∼12.3 Gyrs,
obtained from the ALMA continuum detection of the UV-selected (blue circle) and serendipitously detected sources (red circle), respectively. The
blue/red boxes represent the 1σ uncertainties. For comparison, estimates from other surveys are shown (ALMA: Magnelli et al. 2020; Herschel:
Dunne et al. 2011, Driver et al. 2018, Beeston et al. 2018, Pozzi et al. 2020; SCUBA: Dunne et al. (2003), Vlahakis et al. 2005, Dudzeviˇci¯ut˙e
et al. 2020; IRAM: Magnelli et al. 2019; absorbers in the optical spectra of quasars: Ménard & Fukugita 2012, Péroux & Howk 2020). The lines
represent different models: the cosmological hydrodynamic models from Aoyama et al. (2018) and Li et al. (2019) as water-green and light blue
lines, respectively; the semi-analytical models from Popping et al. (2017) and Vijayan et al. (2019) as pink and dashed-magenta lines, respectively;
the chemical evolution model from Gioannini et al. (2017) as dark-green dashed line.



Liang, L., Feldmann, R., Kereš, D., et al. 2019, MNRAS, 489, 1397


Loiacono, F., Decarli, R., Gruppioni, C., et al. 2020, arXiv e-prints,
arXiv:2006.04837


Magnelli, B., Boogaard, L., Decarli, R., et al. 2020, ApJ, 892, 66


Magnelli, B., Karim, A., Staguhn, J., et al. 2019, ApJ, 877, 45


Magnelli, B., Popesso, P., Berta, S., et al. 2013, A&A, 553, A132


Mancini, M., Schneider, R., Graziani, L., et al. 2015, MNRAS, 451, L70


Matteucci, F. 1994, A&A, 288, 57


Matteucci, F. & Francois, P. 1989, MNRAS, 239, 885


Mattsson, L. 2015, arXiv e-prints, arXiv:1505.04758


McMullin, J. P., Waters, B., Schiebel, D., Young, W., & Golap, K. 2007, Astronomical Society of the Pacific Conference Series, Vol. 376, CASA Architecture and Applications, ed. R. A. Shaw, F. Hill, & D. J. Bell, 127


Ménard, B. & Fukugita, M. 2012, ApJ, 754, 116


Narayanan, D., Davé, R., Johnson, B. D., et al. 2018, MNRAS, 474, 1718


Negrello, M., Amber, S., Amvrosiadis, A., et al. 2017, MNRAS, 465, 3558


Ono, Y., Ouchi, M., Harikane, Y., et al. 2018, PASJ, 70, S10


Orellana, G., Nagar, N. M., Elbaz, D., et al. 2017, A&A, 602, A68



Palla, M., Calura, F., Matteucci, F., et al. 2020, MNRAS, 494, 2355


Pavesi, R., Riechers, D. A., Faisst, A. L., Stacey, G. J., & Capak, P. L. 2019, ApJ,
882, 168


Pavesi, R., Sharon, C. E., Riechers, D. A., et al. 2018, ApJ, 864, 49


Péroux, C. & Howk, J. C. 2020, ARA&A, 58, 363


Pipino, A., Fan, X. L., Matteucci, F., et al. 2011, A&A, 525, A61


Planck Collaboration, Abergel, A., Ade, P. A. R., et al. 2011, A&A, 536, A25


Popping, G., Somerville, R. S., & Galametz, M. 2017, MNRAS, 471, 3152


Pozzi, F., Calura, F., Gruppioni, C., et al. 2015, ApJ, 803, 35


Pozzi, F., Calura, F., Zamorani, G., et al. 2020, MNRAS, 491, 5073


Privon, G. C., Narayanan, D., & Davé, R. 2018, ApJ, 867, 102


Riechers, D. A., Bradford, C. M., Clements, D. L., et al. 2013, Nature, 496, 329


Riechers, D. A., Carilli, C. L., Capak, P. L., et al. 2014, ApJ, 796, 84


Riechers, D. A., Pavesi, R., Sharon, C. E., et al. 2019, ApJ, 872, 7


Roca-Fàbrega, S., Valenzuela, O., Colín, P., et al. 2016, ApJ, 824, 94


Rodighiero, G., Daddi, E., Baronchelli, I., et al. 2011, ApJ, 739, L40


Roelfsema, P. R., Shibai, H., Armus, L., et al. 2018, PASA, 35, e030


Article number, page 13 of 14

_A&A proofs:_ manuscript no. pozzi


Romano, M., Cassata, P., Morselli, L., et al. 2020, MNRAS, 496, 875


Rowan-Robinson, M., Oliver, S., Wang, L., et al. 2016, MNRAS, 461, 1100


Salpeter, E. E. 1955, Vistas in Astronomy, 1, 283


Scalo, J. M. 1986, Fund. Cosmic Phys., 11, 1


Schaerer, D., Ginolfi, M., Bethermin, M., et al. 2020, arXiv e-prints,
arXiv:2002.00979


Schmidt, M. 1959, ApJ, 129, 243


Schurer, A., Calura, F., Silva, L., et al. 2009, MNRAS, 394, 2001


Scoville, N., Aussel, H., Brusa, M., et al. 2007, ApJS, 172, 1


Scoville, N., Aussel, H., Sheth, K., et al. 2014, ApJ, 783, 84


Scoville, N., Lee, N., Vanden Bout, P., et al. 2017, ApJ, 837, 150


Scoville, N., Sheth, K., Aussel, H., et al. 2016, ApJ, 820, 83


Shull, J. M., Smith, B. D., & Danforth, C. W. 2012, ApJ, 759, 23


Simpson, J. M., Smail, I., Swinbank, A. M., et al. 2017, ApJ, 839, 58


Sommovigo, L., Ferrara, A., Pallottini, A., et al. 2020, MNRAS, 497, 956


Speagle, J. S., Steinhardt, C. L., Capak, P. L., & Silverman, J. D. 2014, ApJS,
214, 15


Spitoni, E., Calura, F., Mignoli, M., et al. 2020, A&A, 642, A113


Spitoni, E., Silva Aguirre, V., Matteucci, F., Calura, F., & Grisoni, V. 2019, A&A,
623, A60


Thomas, R., Le Fèvre, O., Scodeggio, M., et al. 2017, A&A, 602, A35


Valiante, R., Schneider, R., Salvadori, S., & Bianchi, S. 2011, MNRAS, 416,
1916


Vijayan, A. P., Clay, S. J., Thomas, P. A., et al. 2019, MNRAS, 489, 4072


Vlahakis, C., Dunne, L., & Eales, S. 2005, MNRAS, 364, 1253


Walter, F., Decarli, R., Aravena, M., et al. 2016, ApJ, 833, 67


Watson, D., Christensen, L., Knudsen, K. K., et al. 2015, Nature, 519, 327


Weidner, C. & Kroupa, P. 2005, ApJ, 625, 754


Yan, L., Sajina, A., Loiacono, F., et al. 2020, arXiv e-prints, arXiv:2006.04835


Zanella, A., Daddi, E., Magdis, G., et al. 2018, MNRAS, 481, 1976


Article number, page 14 of 14

F. Pozzi, F. Calura, Y. Fudamoto et al.: The ALPINE-ALMA survey: Dust mass budget in the early Universe


**Appendix A:** **Dust mass estimates** **Table** **A.1.** M _dust_ estimates for the 23 ALPINE continuum detected
sources. The dust masses have estimated using a Modified Black
Body spectrum (MBB), under the approximation of thin emission, assuming T _dust_ =25 K and the spectral index β = 1.8 (see Sec. 3). _[a]_
Multi-component objects (see Appendix D.2 and Table D.1 in Béthermin et al. 2020). For DEIMOS_COSMOS_881725 the sum of the
components have been considered; for vuds_cosmos_51012097 and
vuds_efdcs_530029038 only the fluxes of the central targets since the
companions are likely separated objects (see Sec. 2).



.



|TargetName|log M<br>dust<br>[log10(M/M ⊙)]|
|---|---|
|CANDELS_GOODSS_19<br>CANDELS_GOODSS_32<br>DEIMOS_COSMOS_396844<br>DEIMOS_COSMOS_417567<br>DEIMOS_COSMOS_422677<br>DEIMOS_COSMOS_460378<br>DEIMOS_COSMOS_488399<br>DEIMOS_COSMOS_493583<br>DEIMOS_COSMOS_494057<br>DEIMOS_COSMOS_539609<br>DEIMOS_COSMOS_552206<br>DEIMOS_COSMOS_683613<br>DEIMOS_COSMOS_818760<br>DEIMOS_COSMOS_848185<br>DEIMOS_COSMOS_873756<br>DEIMOS_COSMOS_881725<br>vuds_cosmos_5100822662<br>vuds_cosmos_5100969402<br>vuds_cosmos_5100994794<br>vuds_cosmos_5101209780<br>vuds_cosmos_5101218326<br>vuds_cosmos_5180966608<br>vuds_efdcs_530029038|8.21±0.19<br>8.12± 0.21<br>8.31± 0.19<br>8.22± 0.21<br>8.33± 0.22<br>7.95± 0.21<br>8.32 ± 0.18<br>8.14 ± 0.22<br>8.16 ± 0.18<br>8.13 ± 0.21<br>8.35 ± 0.20<br>8.29± 0.19<br>8.81± 0.17<br>8.38± 0.18<br>8.91± 0.17<br>8.32±0.25_a_<br>8.09± 0.18<br>8.29± 0.21<br>7.85± 0.21<br>8.27± 0.23_a_<br>8.44± 0.18<br>8.39± 0.19<br>7.85± 0.26_a_|


Article number, page 15 of 14


</paper>

## Items to check

```json
[
 {
  "path": "science.targets[1].redshift_or_distance.evidence[0]",
  "value": "4.1 < z < 5.9",
  "failed_quote": "In the ALPINE survey, 57 sources were also serendipitously detected at 860-1000 um (ALMA band-7)"
 },
 {
  "path": "science.targets[1].distance_source.evidence[0]",
  "value": "Gruppioni et al. 2020",
  "failed_quote": "In the ALPINE survey, 57 sources were also serendipitously detected at 860-1000 um (ALMA band-7)"
 },
 {
  "path": "science.targets[2].redshift_or_distance.evidence[0]",
  "value": "4.4 < z < 5.9",
  "failed_quote": "CANDELS_GOODSS_19 8.21+-0.19"
 },
 {
  "path": "science.targets[2].distance_source.evidence[0]",
  "value": "Faisst et al. 2020b",
  "failed_quote": "CANDELS_GOODSS_19 8.21+-0.19"
 },
 {
  "path": "science.targets[3].redshift_or_distance.evidence[0]",
  "value": "4.4 < z < 5.9",
  "failed_quote": "CANDELS_GOODSS_32 8.12+- 0.21"
 },
 {
  "path": "science.targets[3].distance_source.evidence[0]",
  "value": "Faisst et al. 2020b",
  "failed_quote": "CANDELS_GOODSS_32 8.12+- 0.21"
 },
 {
  "path": "science.targets[4].redshift_or_distance.evidence[0]",
  "value": "4.4 < z < 5.9",
  "failed_quote": "DEIMOS_COSMOS_396844 8.31+- 0.19"
 },
 {
  "path": "science.targets[4].distance_source.evidence[0]",
  "value": "Faisst et al. 2020b",
  "failed_quote": "DEIMOS_COSMOS_396844 8.31+- 0.19"
 },
 {
  "path": "science.targets[5].redshift_or_distance.evidence[0]",
  "value": "4.4 < z < 5.9",
  "failed_quote": "DEIMOS_COSMOS_417567 8.22+- 0.21"
 },
 {
  "path": "science.targets[5].distance_source.evidence[0]",
  "value": "Faisst et al. 2020b",
  "failed_quote": "DEIMOS_COSMOS_417567 8.22+- 0.21"
 },
 {
  "path": "science.targets[6].redshift_or_distance.evidence[0]",
  "value": "4.4 < z < 5.9",
  "failed_quote": "DEIMOS_COSMOS_422677 8.33+- 0.22"
 },
 {
  "path": "science.targets[6].distance_source.evidence[0]",
  "value": "Faisst et al. 2020b",
  "failed_quote": "DEIMOS_COSMOS_422677 8.33+- 0.22"
 },
 {
  "path": "science.targets[7].redshift_or_distance.evidence[0]",
  "value": "4.4 < z < 5.9",
  "failed_quote": "DEIMOS_COSMOS_460378 7.95+- 0.21"
 },
 {
  "path": "science.targets[7].distance_source.evidence[0]",
  "value": "Faisst et al. 2020b",
  "failed_quote": "DEIMOS_COSMOS_460378 7.95+- 0.21"
 },
 {
  "path": "science.targets[8].redshift_or_distance.evidence[0]",
  "value": "4.4 < z < 5.9",
  "failed_quote": "DEIMOS_COSMOS_488399 8.32 +- 0.18"
 },
 {
  "path": "science.targets[8].distance_source.evidence[0]",
  "value": "Faisst et al. 2020b",
  "failed_quote": "DEIMOS_COSMOS_488399 8.32 +- 0.18"
 },
 {
  "path": "science.targets[9].redshift_or_distance.evidence[0]",
  "value": "4.4 < z < 5.9",
  "failed_quote": "DEIMOS_COSMOS_493583 8.14 +- 0.22"
 },
 {
  "path": "science.targets[9].distance_source.evidence[0]",
  "value": "Faisst et al. 2020b",
  "failed_quote": "DEIMOS_COSMOS_493583 8.14 +- 0.22"
 },
 {
  "path": "science.targets[10].redshift_or_distance.evidence[0]",
  "value": "4.4 < z < 5.9",
  "failed_quote": "DEIMOS_COSMOS_494057 8.16 +- 0.18"
 },
 {
  "path": "science.targets[10].distance_source.evidence[0]",
  "value": "Faisst et al. 2020b",
  "failed_quote": "DEIMOS_COSMOS_494057 8.16 +- 0.18"
 },
 {
  "path": "science.targets[11].redshift_or_distance.evidence[0]",
  "value": "4.4 < z < 5.9",
  "failed_quote": "DEIMOS_COSMOS_539609 8.13 +- 0.21"
 },
 {
  "path": "science.targets[11].distance_source.evidence[0]",
  "value": "Faisst et al. 2020b",
  "failed_quote": "DEIMOS_COSMOS_539609 8.13 +- 0.21"
 },
 {
  "path": "science.targets[12].redshift_or_distance.evidence[0]",
  "value": "4.4 < z < 5.9",
  "failed_quote": "DEIMOS_COSMOS_552206 8.35 +- 0.20"
 },
 {
  "path": "science.targets[12].distance_source.evidence[0]",
  "value": "Faisst et al. 2020b",
  "failed_quote": "DEIMOS_COSMOS_552206 8.35 +- 0.20"
 },
 {
  "path": "science.targets[13].redshift_or_distance.evidence[0]",
  "value": "4.4 < z < 5.9",
  "failed_quote": "DEIMOS_COSMOS_683613 8.29+- 0.19"
 },
 {
  "path": "science.targets[13].distance_source.evidence[0]",
  "value": "Faisst et al. 2020b",
  "failed_quote": "DEIMOS_COSMOS_683613 8.29+- 0.19"
 },
 {
  "path": "science.targets[14].redshift_or_distance.evidence[0]",
  "value": "4.4 < z < 5.9",
  "failed_quote": "DEIMOS_COSMOS_818760 8.81+- 0.17"
 },
 {
  "path": "science.targets[14].distance_source.evidence[0]",
  "value": "Faisst et al. 2020b",
  "failed_quote": "DEIMOS_COSMOS_818760 8.81+- 0.17"
 },
 {
  "path": "science.targets[15].redshift_or_distance.evidence[0]",
  "value": "4.4 < z < 5.9",
  "failed_quote": "DEIMOS_COSMOS_848185 8.38+- 0.18"
 },
 {
  "path": "science.targets[15].distance_source.evidence[0]",
  "value": "Faisst et al. 2020b",
  "failed_quote": "DEIMOS_COSMOS_848185 8.38+- 0.18"
 },
 {
  "path": "science.targets[16].redshift_or_distance.evidence[0]",
  "value": "4.4 < z < 5.9",
  "failed_quote": "DEIMOS_COSMOS_873756 8.91+- 0.17"
 },
 {
  "path": "science.targets[16].distance_source.evidence[0]",
  "value": "Faisst et al. 2020b",
  "failed_quote": "DEIMOS_COSMOS_873756 8.91+- 0.17"
 },
 {
  "path": "science.targets[17].redshift_or_distance.evidence[0]",
  "value": "4.4 < z < 5.9",
  "failed_quote": "DEIMOS_COSMOS_881725 8.32+-0.25a"
 },
 {
  "path": "science.targets[17].distance_source.evidence[0]",
  "value": "Faisst et al. 2020b",
  "failed_quote": "DEIMOS_COSMOS_881725 8.32+-0.25a"
 },
 {
  "path": "science.targets[18].redshift_or_distance.evidence[0]",
  "value": "4.4 < z < 5.9",
  "failed_quote": "vuds_cosmos_5100822662 8.09+- 0.18"
 },
 {
  "path": "science.targets[18].distance_source.evidence[0]",
  "value": "Faisst et al. 2020b",
  "failed_quote": "vuds_cosmos_5100822662 8.09+- 0.18"
 },
 {
  "path": "science.targets[19].redshift_or_distance.evidence[0]",
  "value": "4.4 < z < 5.9",
  "failed_quote": "vuds_cosmos_5100969402 8.29+- 0.21"
 },
 {
  "path": "science.targets[19].distance_source.evidence[0]",
  "value": "Faisst et al. 2020b",
  "failed_quote": "vuds_cosmos_5100969402 8.29+- 0.21"
 },
 {
  "path": "science.targets[20].redshift_or_distance.evidence[0]",
  "value": "4.4 < z < 5.9",
  "failed_quote": "vuds_cosmos_5100994794 7.85+- 0.21"
 },
 {
  "path": "science.targets[20].distance_source.evidence[0]",
  "value": "Faisst et al. 2020b",
  "failed_quote": "vuds_cosmos_5100994794 7.85+- 0.21"
 },
 {
  "path": "science.targets[21].redshift_or_distance.evidence[0]",
  "value": "4.4 < z < 5.9",
  "failed_quote": "vuds_cosmos_5101209780 8.27+- 0.23a"
 },
 {
  "path": "science.targets[21].distance_source.evidence[0]",
  "value": "Faisst et al. 2020b",
  "failed_quote": "vuds_cosmos_5101209780 8.27+- 0.23a"
 },
 {
  "path": "science.targets[22].redshift_or_distance.evidence[0]",
  "value": "4.4 < z < 5.9",
  "failed_quote": "vuds_cosmos_5101218326 8.44+- 0.18"
 },
 {
  "path": "science.targets[22].distance_source.evidence[0]",
  "value": "Faisst et al. 2020b",
  "failed_quote": "vuds_cosmos_5101218326 8.44+- 0.18"
 },
 {
  "path": "science.targets[23].redshift_or_distance.evidence[0]",
  "value": "4.4 < z < 5.9",
  "failed_quote": "vuds_cosmos_5180966608 8.39+- 0.19"
 },
 {
  "path": "science.targets[23].distance_source.evidence[0]",
  "value": "Faisst et al. 2020b",
  "failed_quote": "vuds_cosmos_5180966608 8.39+- 0.19"
 },
 {
  "path": "science.targets[24].redshift_or_distance.evidence[0]",
  "value": "4.4 < z < 5.9",
  "failed_quote": "vuds_efdcs_530029038 7.85+- 0.26a"
 },
 {
  "path": "science.targets[24].distance_source.evidence[0]",
  "value": "Faisst et al. 2020b",
  "failed_quote": "vuds_efdcs_530029038 7.85+- 0.26a"
 },
 {
  "path": "data.bands.evidence[1]",
  "value": "Band 7 (275-373 GHz, 860-1000 um)",
  "failed_quote": "In the ALPINE survey, 57 sources were also serendipitously detected at 860-1000 um (ALMA band-7)"
 },
 {
  "path": "data.frequencies_and_spectral_setup.evidence[1]",
  "value": "275-373 GHz covering [CII] 158 um and rest-frame ~157-158 um continuum",
  "failed_quote": "We anticipate here that in Sec. 5.1 we will perform a stacking analysis on the rest-frame 157 um ALMA continuum images, including both the 23 individual continuum detected sources and the non-detections."
 },
 {
  "path": "data.lines_targeted[0].evidence[0]",
  "value": "[CII]",
  "failed_quote": "The goal of the ALPINE survey was to observe the prominent [CII] 158 um emission line for 118 UV-selected normal star-forming galaxies at z ~ 4.4 - 5.8."
 },
 {
  "path": "data.sensitivity.evidence[0]",
  "value": "mean RMS 50 uJy/beam (4.3 < z < 4.6) and 28 uJy/beam (5.1 < z < 5.9)",
  "failed_quote": "and mean sensitivities (RMS of 50 uJy/beam and 28 uJy/beam in the 4.3< z < 4.6 and 5.1< z < 5.9 ranges, respectively."
 },
 {
  "path": "data.external_data_from_literature[0].what.evidence[1]",
  "value": "ALMA Band 7 continuum fluxes and catalogues for 23 target detections and 57 serendipitous detections",
  "failed_quote": "In the ALPINE survey, 57 sources were also serendipitously detected at 860-1000 um (ALMA band-7) and we refer to Béthermin et al. (2020) for the description of the detection procedure and the delivery of the non-targets catalogue."
 },
 {
  "path": "data.external_data_from_literature[5].what.evidence[0]",
  "value": "UV luminosity function (UVLF) at z ~ 5",
  "failed_quote": "We use the derivation from Ono et al. (2018) and we estimate the associated uncertainty by varying each of the UVLF parameters (alpha, L_* and Phi_*) within 1-sigma (see Table 7 in Ono et al. 2018)."
 },
 {
  "path": "data.simulations_or_models_as_data[0].evidence[0]",
  "value": "Chemical evolution models for proto-spheroidal (PSPH) and spiral galaxies (Calura et al. 2008, 2014, 2017)",
  "failed_quote": "The chemical evolution models considered here describe galaxies with different star formation histories, namely proto-spheroidals (PSPH) and spirals. The models including evolution of interstellar dust grains were presented in Calura et al. (2008)"
 },
 {
  "path": "data.simulations_or_models_as_data[1].evidence[1]",
  "value": "Cosmological hydrodynamic, semi-analytical, and phenomenological models for cosmic dust mass density evolution (Gioannini et al. 2017; Popping et al. 2017; Vijayan et al. 2019; Aoyama et al. 2018; Li et al. 2019)",
  "failed_quote": "The results of Popping et al. (2017) and Vijayan et al. (2019) were obtained by means of cosmological, semi-analytical galaxy formation models."
 },
 {
  "path": "processing.imaging.final_rms.evidence[0]",
  "value": "50 uJy/beam (4.3 < z < 4.6) and 28 uJy/beam (5.1 < z < 5.9)",
  "failed_quote": "and mean sensitivities (RMS of 50 uJy/beam and 28 uJy/beam in the 4.3< z < 4.6 and 5.1< z < 5.9 ranges, respectively."
 },
 {
  "path": "analysis_steps[0].method.evidence[1]",
  "value": "Single Modified Black Body (MBB) in optically thin regime evaluated at rest-frame 250 um (1.2 THz), extrapolated from observed Band 7 (rest-frame ~157 um) continuum flux",
  "failed_quote": "Dust masses are measured from the continuum emission at 250 um (see Gilli et al. 2014), extrapolated from the 157 um ALMA data, assuming a mass-weighted temperature of 25 K and a dust emissivity of beta=1.8"
 },
 {
  "path": "analysis_steps[0].key_parameters[1].evidence[0]",
  "value": "k_nu0 = 4 cm^2 g^-1 at nu0 = 1.2 THz (lambda_rest = 250 um), beta = 1.8",
  "failed_quote": "We adopt k_nu0 = 4 cm^2 g^-1 with nu0 =1.2 THz (see Bianchi 2013) and beta = 1.8, i.e. the Galactic value from the Planck data (Planck Collaboration et al. 2011)."
 },
 {
  "path": "analysis_steps[0].assumptions[0].evidence[0]",
  "value": "Optically thin dust emission at rest-frame 250 um",
  "failed_quote": "Considering the rest-frame frequency assumed to compute S_nu_obs, we have considered 1.2 THz, corresponding to lambda_rest = 250 um (see Gilli et al. 2014). At this wavelength our galaxies are expected to be optically thin"
 },
 {
  "path": "analysis_steps[0].assumptions[2].evidence[0]",
  "value": "LambdaCDM cosmology with Omega_m = 0.3, Omega_lambda = 0.7, H_0 = 70 km s^-1 Mpc^-3",
  "failed_quote": "Throughout the paper, we assume a LambdaCDM cosmology with Omega_m = 0.3, Omega_lambda = 0.7 and H_0 =70 km s^-1 Mpc^-3."
 },
 {
  "path": "analysis_steps[0].fitting.evidence[0]",
  "value": "Analytical evaluation of single MBB equation; error bars computed by summing in quadrature relative uncertainties on 157 um flux (~25%), beta (~15%), and band conversion (~30%)",
  "failed_quote": "We calculate the error bars on the dust masses by summing in quadrature the relative uncertainties on the 157 um continuum flux (~25%), the systematic uncertainties due to the beta emissivity (~15%) and to the band conversion emissivity (~30%)."
 },
 {
  "path": "analysis_steps[0].validation.evidence[2]",
  "value": "Tested sensitivity to beta (1.5 to 2.0 changes mass by <15%), temperature (T=20 K changes by 20%, T=35 K decreases by 60%), and rest-frame reference wavelength (250 um vs 850 um gives unchanged masses)",
  "failed_quote": "In fact, we have tested that our dust masses do not change if one considers 250 or 850 um and if the flux S_nu_obs in Eq. 1 is derived by means of an extrapolation at higher frequencies."
 },
 {
  "path": "analysis_steps[1].key_parameters[0].evidence[0]",
  "value": "PSPH final baryonic masses of 3e10, 1e11, and 1e12 M_sun; spiral final stellar masses from 2e9 to 1e11 M_sun",
  "failed_quote": "The models describe three PSPH of final baryonic mass 3 x 10^10 M_sun, 10^11 M_sun and 10^12 M_sun."
 },
 {
  "path": "analysis_steps[1].key_parameters[0].evidence[1]",
  "value": "PSPH final baryonic masses of 3e10, 1e11, and 1e12 M_sun; spiral final stellar masses from 2e9 to 1e11 M_sun",
  "failed_quote": "The final stellar masses of the spirals range from 2 x 10^9 M_sun to 10^11 M_sun."
 },
 {
  "path": "analysis_steps[2].method.evidence[0]",
  "value": "Median stacking of rest-frame 158 um continuum images centered on UV counterpart positions, including both detections and non-detections, split into two redshift bins (z < 5 and z > 5) and three L_UV bins (~20 sources per bin)",
  "failed_quote": "We perform stacking using the lambda_158um rest-frame continuum images centered on the UV counterpart positions, including both individual detections and non-detection in order to avoid biases."
 },
 {
  "path": "analysis_steps[2].key_parameters[0].evidence[0]",
  "value": "Detection threshold 3.5 sigma; 3 sigma upper limits for non-detections (3 * background RMS + local maximum); L_UV bins: 10.4-10.9, 10.9-11.1, 11.1-11.6 log(L_sun)",
  "failed_quote": "As for the detections, we adopt a 3.5sigma threshold. In case of non detection, we use the conservative 3sigma upper limits by adding three times the background RMS to the local maximum (see Béthermin et al. 2020.)"
 },
 {
  "path": "analysis_steps[2].assumptions[0].evidence[0]",
  "value": "Same MBB parameters (T = 25 K, beta = 1.8) applied to stacked fluxes and 3 sigma upper limits to derive M_dust",
  "failed_quote": "For the non-detections and for the stacked images, the same procedure adopted for the detected sources has been used to estimate the dust masses, considering the 3sigma flux upper limits and the stacked results as rest-frame 158 um continuum fluxes, respectively."
 },
 {
  "path": "analysis_steps[3].method.evidence[1]",
  "value": "Bayesian linear regression of log(M_dust) vs log(L_UV) (on stacked data including upper limits) and log(M_dust) vs log(L_IR) (on 10 serendipitous sources), followed by convolution of the linear-space mean relation with the UVLF (Ono et al. 2018) and IRLF (Gruppioni et al. 2020)",
  "failed_quote": "As for the DMD obtained for the UV-galaxy population, we estimate the comoving density of our physical parameter (rho_dust,IR, where now the subscript IR stands for derived from IR-selected sources) by convolving the volume density of the proxy (L_IR) with the M_dust-L_IR relation"
 },
 {
  "path": "analysis_steps[3].key_parameters[0].evidence[0]",
  "value": "UVLF integration ranges: 10.4 < log(L_UV) < 11.5 (sampled lower limit) and 0.03 L* to 100 L* (full); IRLF integration ranges: 11.2 < log(L_IR) < 13 (sampled lower limit) and 9 < log(L_IR) < 14 (full)",
  "failed_quote": "we estimate two quantities: the dust mass density derived by integrating the UV-luminosity only over the ALPINE UV-luminosity range and the dust mass density obtained by extrapolating the relation down to fainter UV luminosity not sampled by the ALPINE targets, and integrating over the commonly used 0.03L* - 100L* range (rho_dust,UV)."
 },
 {
  "path": "analysis_steps[3].assumptions[1].evidence[0]",
  "value": "Log-normal scatter correction exp(0.5 * (ln(10) * sigma)^2) applied when converting mean relation from log space to linear space",
  "failed_quote": "In this operation we have converted the mean relation found in log space (see Fig. 4) to the mean relation in linear space as: < M_dust/L_UV >= 10^(<log M_dust/L_UV >+ 2.3xsigma^2/2)"
 },
 {
  "path": "analysis_steps[3].validation.evidence[0]",
  "value": "Pearson rank correlation coefficient and p-value computed for linear fits; uncertainties propagated by varying UVLF parameters within 1 sigma and using MCMC posteriors of IRLF",
  "failed_quote": "(dispersion sigma <~ 0.2 dex, Pearson rank coefficient of 0.76 and p-value 0.08, with the Pearson coefficient computed considering all data as detections)"
 },
 {
  "path": "analysis_steps[3].validation.evidence[1]",
  "value": "Pearson rank correlation coefficient and p-value computed for linear fits; uncertainties propagated by varying UVLF parameters within 1 sigma and using MCMC posteriors of IRLF",
  "failed_quote": "We use the derivation from Ono et al. (2018) and we estimate the associated uncertainty by varying each of the UVLF parameters (alpha, L_* and Phi_*) within 1-sigma (see Table 7 in Ono et al. 2018)."
 },
 {
  "path": "analysis_steps[3].validation.evidence[2]",
  "value": "Pearson rank correlation coefficient and p-value computed for linear fits; uncertainties propagated by varying UVLF parameters within 1 sigma and using MCMC posteriors of IRLF",
  "failed_quote": "The former has been computed considering the 1sigma uncertainty derived through the MCMC analysis of the IRLF estimated by Gruppioni et al. (2020) (see their Table 4)."
 },
 {
  "path": "results_numeric[0].evidence[1]",
  "value": "Dust mass range for most ALPINE continuum-detected galaxies (log M_dust) = 7.8-8.4 log10(M_sun)",
  "failed_quote": "For most of our galaxies we find dust masses in the range log(M_dust/M_sun)=7.8-8.4"
 },
 {
  "path": "results_numeric[1].evidence[0]",
  "value": "Dust mass of CANDELS_GOODSS_19 (log M_dust) = 8.21 log10(M/M_sun)",
  "failed_quote": "CANDELS_GOODSS_19 8.21+-0.19"
 },
 {
  "path": "results_numeric[2].evidence[0]",
  "value": "Dust mass of CANDELS_GOODSS_32 (log M_dust) = 8.12 log10(M/M_sun)",
  "failed_quote": "CANDELS_GOODSS_32 8.12+- 0.21"
 },
 {
  "path": "results_numeric[3].evidence[0]",
  "value": "Dust mass of DEIMOS_COSMOS_396844 (log M_dust) = 8.31 log10(M/M_sun)",
  "failed_quote": "DEIMOS_COSMOS_396844 8.31+- 0.19"
 },
 {
  "path": "results_numeric[4].evidence[0]",
  "value": "Dust mass of DEIMOS_COSMOS_417567 (log M_dust) = 8.22 log10(M/M_sun)",
  "failed_quote": "DEIMOS_COSMOS_417567 8.22+- 0.21"
 },
 {
  "path": "results_numeric[5].evidence[0]",
  "value": "Dust mass of DEIMOS_COSMOS_422677 (log M_dust) = 8.33 log10(M/M_sun)",
  "failed_quote": "DEIMOS_COSMOS_422677 8.33+- 0.22"
 },
 {
  "path": "results_numeric[6].evidence[0]",
  "value": "Dust mass of DEIMOS_COSMOS_460378 (log M_dust) = 7.95 log10(M/M_sun)",
  "failed_quote": "DEIMOS_COSMOS_460378 7.95+- 0.21"
 },
 {
  "path": "results_numeric[7].evidence[0]",
  "value": "Dust mass of DEIMOS_COSMOS_488399 (log M_dust) = 8.32 log10(M/M_sun)",
  "failed_quote": "DEIMOS_COSMOS_488399 8.32 +- 0.18"
 },
 {
  "path": "results_numeric[8].evidence[0]",
  "value": "Dust mass of DEIMOS_COSMOS_493583 (log M_dust) = 8.14 log10(M/M_sun)",
  "failed_quote": "DEIMOS_COSMOS_493583 8.14 +- 0.22"
 },
 {
  "path": "results_numeric[9].evidence[0]",
  "value": "Dust mass of DEIMOS_COSMOS_494057 (log M_dust) = 8.16 log10(M/M_sun)",
  "failed_quote": "DEIMOS_COSMOS_494057 8.16 +- 0.18"
 },
 {
  "path": "results_numeric[10].evidence[0]",
  "value": "Dust mass of DEIMOS_COSMOS_539609 (log M_dust) = 8.13 log10(M/M_sun)",
  "failed_quote": "DEIMOS_COSMOS_539609 8.13 +- 0.21"
 },
 {
  "path": "results_numeric[11].evidence[0]",
  "value": "Dust mass of DEIMOS_COSMOS_552206 (log M_dust) = 8.35 log10(M/M_sun)",
  "failed_quote": "DEIMOS_COSMOS_552206 8.35 +- 0.20"
 },
 {
  "path": "results_numeric[12].evidence[0]",
  "value": "Dust mass of DEIMOS_COSMOS_683613 (log M_dust) = 8.29 log10(M/M_sun)",
  "failed_quote": "DEIMOS_COSMOS_683613 8.29+- 0.19"
 },
 {
  "path": "results_numeric[13].evidence[0]",
  "value": "Dust mass of DEIMOS_COSMOS_818760 (log M_dust) = 8.81 log10(M/M_sun)",
  "failed_quote": "DEIMOS_COSMOS_818760 8.81+- 0.17"
 },
 {
  "path": "results_numeric[14].evidence[0]",
  "value": "Dust mass of DEIMOS_COSMOS_848185 (log M_dust) = 8.38 log10(M/M_sun)",
  "failed_quote": "DEIMOS_COSMOS_848185 8.38+- 0.18"
 },
 {
  "path": "results_numeric[15].evidence[0]",
  "value": "Dust mass of DEIMOS_COSMOS_873756 (log M_dust) = 8.91 log10(M/M_sun)",
  "failed_quote": "DEIMOS_COSMOS_873756 8.91+- 0.17"
 },
 {
  "path": "results_numeric[16].evidence[0]",
  "value": "Dust mass of DEIMOS_COSMOS_881725 (log M_dust) = 8.32 log10(M/M_sun)",
  "failed_quote": "DEIMOS_COSMOS_881725 8.32+-0.25a"
 },
 {
  "path": "results_numeric[17].evidence[0]",
  "value": "Dust mass of vuds_cosmos_5100822662 (log M_dust) = 8.09 log10(M/M_sun)",
  "failed_quote": "vuds_cosmos_5100822662 8.09+- 0.18"
 },
 {
  "path": "results_numeric[18].evidence[0]",
  "value": "Dust mass of vuds_cosmos_5100969402 (log M_dust) = 8.29 log10(M/M_sun)",
  "failed_quote": "vuds_cosmos_5100969402 8.29+- 0.21"
 },
 {
  "path": "results_numeric[19].evidence[0]",
  "value": "Dust mass of vuds_cosmos_5100994794 (log M_dust) = 7.85 log10(M/M_sun)",
  "failed_quote": "vuds_cosmos_5100994794 7.85+- 0.21"
 },
 {
  "path": "results_numeric[20].evidence[0]",
  "value": "Dust mass of vuds_cosmos_5101209780 (log M_dust) = 8.27 log10(M/M_sun)",
  "failed_quote": "vuds_cosmos_5101209780 8.27+- 0.23a"
 },
 {
  "path": "results_numeric[21].evidence[0]",
  "value": "Dust mass of vuds_cosmos_5101218326 (log M_dust) = 8.44 log10(M/M_sun)",
  "failed_quote": "vuds_cosmos_5101218326 8.44+- 0.18"
 },
 {
  "path": "results_numeric[22].evidence[0]",
  "value": "Dust mass of vuds_cosmos_5180966608 (log M_dust) = 8.39 log10(M/M_sun)",
  "failed_quote": "vuds_cosmos_5180966608 8.39+- 0.19"
 },
 {
  "path": "results_numeric[23].evidence[0]",
  "value": "Dust mass of vuds_efdcs_530029038 (log M_dust) = 7.85 log10(M/M_sun)",
  "failed_quote": "vuds_efdcs_530029038 7.85+- 0.26a"
 },
 {
  "path": "results_numeric[30].evidence[0]",
  "value": "Slope of log(M_dust) vs log(L_UV) relation = 1.16 dimensionless",
  "failed_quote": "The resulting best-fit is log(M_dust) = (1.16+0.68-0.57)(log(L_UV) - 11.) + (-0.11+0.10-0.15) + 7.76"
 },
 {
  "path": "results_numeric[31].evidence[0]",
  "value": "Slope of log(M_dust) vs log(L_IR) relation = 1.01 dimensionless",
  "failed_quote": "The resulting best-fit is log(M_dust) = (1.01+0.11-0.11)(log(L_IR) - 12.2) + (-0.0+0.05-0.05) + 8.8"
 },
 {
  "path": "results_numeric[32].evidence[0]",
  "value": "Cosmic dust mass density from UV-selected galaxies at z ~ 5, log(rho_dust,UV) = 4.8 log10(M_sun Mpc^-3)",
  "failed_quote": "log(rho_dust,UV) [M_sun Mpc^-3] 4.8+0.4-1.0"
 },
 {
  "path": "results_numeric[33].evidence[0]",
  "value": "Cosmic dust mass density lower limit from UV-selected galaxies (sampled L_UV range), log(rho_dust,UV) = >4.3 log10(M_sun Mpc^-3)",
  "failed_quote": "log(rho_dust,UV) [M_sun Mpc^-3] 4.8+0.4-1.0 > 4.3"
 },
 {
  "path": "results_numeric[34].evidence[0]",
  "value": "Cosmic dust mass density from IR-selected galaxies at z ~ 5, log(rho_dust,IR) = 5.3 log10(M_sun Mpc^-3)",
  "failed_quote": "log(rho_dust,IR) [M_sun Mpc^-3] 5.3+0.5-0.3"
 },
 {
  "path": "results_numeric[35].evidence[0]",
  "value": "Cosmic dust mass density lower limit from IR-selected galaxies (sampled L_IR range), log(rho_dust,IR) = >4.8 log10(M_sun Mpc^-3)",
  "failed_quote": "log(rho_dust,IR) [M_sun Mpc^-3] 5.3+0.5-0.3 > 4.8"
 },
 {
  "path": "findings_qualitative[1].evidence[1]",
  "value": "A standard Salpeter IMF is generally sufficient to explain the dust masses of ALPINE galaxies in proto-spheroid models without requiring a top-heavy IMF, except for a couple of the most dust-massive galaxies.",
  "failed_quote": "In most cases, a Salpeter IMF is sufficient to account for the observed dust masses, i.e. in general there is no particular need to invoke mechanisms such as a top-heavy IMF to enhance dust production"
 },
 {
  "path": "findings_qualitative[3].evidence[0]",
  "value": "The phenomenological model of Gioannini et al. (2017) best reproduces the cosmic evolution of the dust mass density from z ~ 5 to the local Universe, whereas cosmological semi-analytical and hydrodynamic models overestimate the low-redshift (z < 1) dust mass density.",
  "failed_quote": "The phenomenological model from Gioannini et al. (2017) is the model that best reproduces the observed evolution of rho_dust."
 },
 {
  "path": "findings_qualitative[3].evidence[1]",
  "value": "The phenomenological model of Gioannini et al. (2017) best reproduces the cosmic evolution of the dust mass density from z ~ 5 to the local Universe, whereas cosmological semi-analytical and hydrodynamic models overestimate the low-redshift (z < 1) dust mass density.",
  "failed_quote": "On the other hand, the ab-initio cosmological, semi-analytical models of Popping et al. (2017) and Vijayan et al. (2019) and and the cosmological simulations of Li et al. (2019) roughly account for the observed evolution of rho_dust dust at z > 1, but they overestimate the dust mass budget at lower redshift, failing in reproducing the decreasing trend observed at z < 1."
 },
 {
  "path": "claims[0].evidence[1]",
  "value": "ALPINE galaxies are likely progenitors of intermediate- and low-mass proto-spheroids (present-day bulges or ellipticals) rather than galaxy discs.",
  "failed_quote": "Typical dust mass values of ~ 10^8 M_sun as derived in the ALPINE sample of continuum detected sources are achievable already at early times (typically ~ 0.1-0.5 Gyr) in PSPH."
 },
 {
  "path": "claims[1].evidence[1]",
  "value": "UV selection misses the most dust-rich, UV-obscured galaxies at z ~ 5, making the blind IR-derived DMD the more complete fiducial estimate.",
  "failed_quote": "The derived rho_dust,UV is ~30 % rho_dust,IR, although the two estimates are marginally consistent at 1sigma. Our result supports the conclusion that UV-selected galaxies miss the most obscured/dusty objects and we consider rho_dust,IR as our fiducial value."
 },
 {
  "path": "reasoning.limitations_admitted[0].evidence[0]",
  "value": "Single band observation (ALMA Band 7, rest-frame ~157 um) requires assuming a fixed dust temperature (T = 25 K) and emissivity (beta = 1.8) and extrapolating to 250 um; if cold dust is at T = 35 K, dust masses and DMDs decrease by 60%.",
  "failed_quote": "Morever, we discuss the uncertainties on the derived dust masses related to three (non-independent) factors: the 'band-conversion', linked to the extrapolation of the 250 um flux from higher frequencies (i.e. 157 um), the emissivity beta and the temperature T."
 },
 {
  "path": "reasoning.limitations_admitted[2].evidence[0]",
  "value": "The linear fit of log(M_dust) vs log(L_UV) from stacked images has poor statistical significance (constrained at 1-2 sigma, p-value = 0.08) and must be extrapolated to fainter UV luminosities not sampled by ALPINE.",
  "failed_quote": "The fit results with a poor significance level with the coefficient constrained at 1-2sigma (Pearson rank coefficient of 0.76 and p-value of 0.08, estimated considering all data as detections)."
 },
 {
  "path": "reasoning.limitations_admitted[3].evidence[0]",
  "value": "The IR-selected DMD determination has large uncertainty (~0.3-0.5 dex, up to 50%) due to the small sample (10 sources, 5 after removing overdensity candidates) used to constrain the IRLF.",
  "failed_quote": "The large uncertainty (up to 50%) affecting our determination of rho_dust for IR selected galaxies reflects the small sample used to estimate the IRLF."
 }
]
```
