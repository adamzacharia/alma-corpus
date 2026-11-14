# Repair task for a Claude Code subagent

A methods card has evidence quotes that were not found verbatim in the paper. Below are the rules, the paper, and the failing items. Write ONE JSON object, nothing else, of the form {"repairs": [{"path": ..., "found": true|false, "loc": ..., "quote": ...}, ...]} with one entry per item (path unchanged) to:

    C:\Users\adama\alma-corpus\cards\2019MNRAS.483.4586F\sonnet\repair_reply.txt

Use the Write tool for that file. Copy each quote character for character from the paper text below; a returned quote is checked mechanically and dropped if it is not in the paper. Do not read any other file, do not run commands, and do not change anything else. Reply with one line when done.

---

## Rules

You check evidence quotes for a methods card extracted from an astronomy paper. Some quotes could not be found verbatim in the paper text, and some stated values came without a quote. For each item: find the passage in the paper that supports the value and copy it VERBATIM (same words and order, at most 40 words; LaTeX markup may be dropped) with its loc (section heading, "abstract", "Table N" or "Figure N caption"). If the paper does not support the value, return found = false and leave quote and loc empty. Use only the paper text. Return one entry per item, with the item's path unchanged.

## Paper

<paper>
MNRAS **000**, 1–26 (2018) Preprint 6 February 2019 Compiled using MNRAS L [A] TEX style file v3.0

## **Cold Molecular Outflows in the Local Universe and Their** **Feedback Effect on Galaxies**

### A. Fluetsch [1][,][2], R. Maiolino [1][,][2], S. Carniani [1][,][2], A. Marconi [3][,][4], C. Cicone [5], M. A. Bourne [2][,][6], T. Costa [7], A. C. Fabian [6], W. Ishibashi [6], G. Venturi [1][,][2][,][3][,][4]


1 _University_ _of_ _Cambridge,_ _Cavendish_ _Laboratory,_ _Cambridge_ _CB3_ _0HE,_ _UK_
2 _University_ _of_ _Cambridge,_ _Kavli_ _Institute_ _for_ _Cosmology,_ _Cambridge_ _CB3_ _0HE,_ _UK_
3 _Dipartimento_ _di_ _Fisica_ _e_ _Astronomia,_ _Universit`a_ _degli_ _Studi_ _di_ _Firenze,_ _Firenze,_ _Italy_
4 _INAF_ _Osservatorio_ _Astrofisico_ _di_ _Arcetri,_ _Firenze,_ _Italy_
5 _INAF_ _Osservatorio_ _Astronomico_ _di_ _Brera,_ _Via_ _Brera_ _28,_ _I-20121,_ _Milano,_ _Italy_
6 _Institute_ _of_ _Astronomy,_ _Madingley_ _Road,_ _Cambridge_ _CB3_ _0HA,_ _UK_
7 _Leiden_ _Observatory,_ _Leiden_ _University,_ _PO_ _Box_ _9513,_ _NL-2300_ _RA_ _Leiden,_ _the_ _Netherlands_


Accepted XXX. Received YYY; in original form ZZZ


**ABSTRACT**
We study molecular outflows in a sample of 45 local galaxies, both star forming and
AGN, primarily by using CO data from the ALMA archive and from the literature.
For a subsample we also compare the molecular outflow with the ionized and neutral
atomic phases. We infer an empirical analytical function relating the outflow rate
simultaneously to the SFR, _L_ AGN, and galaxy stellar mass; this relation is much tighter
than the relations with the individual quantities. The outflow kinetic power shows a
larger scatter than in previous, more biased studies, spanning from 0.1 to 5 per cent
of _L_ AGN, while the momentum rate ranges from 1 to 30 times _L_ AGN / _c_, indicating
that these outflows can be both energy-driven, but with a broad range of coupling
efficiencies with the ISM, and radiation pressure-driven. For about 10 per cent of the
objects the outflow energetics significantly exceed the maximum theoretical values;
we interpret these as “fossil outflows” resulting from activity of a past strong AGN,
which has now faded. We estimate that, in the stellar mass range probed here (>
10 [10] M ⊙ ), less than 5 per cent of the outflowing gas escapes the galaxy. The molecular
gas depletion time associated with the outflow can be as short as a few million years
in powerful AGN, however, the total gas (H 2 +HI) depletion times are much longer.
Altogether, our findings suggest that even AGN-driven outflows might be relatively
ineffective in clearing galaxies of their entire gas content, although they are likely
capable of clearing and quenching the central region.


**Key** **words:** galaxies: active — galaxies: evolution — quasars: general — galaxies:
ISM — galaxies: star formation



**1** **INTRODUCTION**


Galactic outflows driven either by active galactic nuclei
(AGN) or starbursts may be capable of expelling ionized,
atomic neutral and molecular gas from galaxies and thereby
regulate or even shut down star formation. As a consequence,
outflows may provide the (negative) feedback effect that is
invoked to explain several key observable properties of galaxies. For instance, star formation suppression from AGNdriven outflows is thought to play a key role in accounting for
the the local population of massive passive galaxies and the
lack of over-massive galaxies (e.g. Scannapieco & Oh 2004;


© 2018 The Authors



Springel et al. 2005; Sijacki et al. 2007; Puchwein & Springel
2013; Vogelsberger et al. 2014; Beckmann et al. 2017). Furthermore, this process may offer an explanation for the tight
correlations between the masses of the central supermassive
black holes (SMBHs) and the stellar masses or velocity dispersions of their host galaxy bulges (e.g Fabian 2012; King
& Pounds 2015). On the other hand, starburst-driven outflows are thought to play a key role in self-regulating star
formation in low-mass galaxies and also to be responsible
for the chemical enrichment of the circumgalactic medium
(e.g. Erb 2015; Chisholm et al. 2017).


In the last few years, extensive observing programmes

2 _A_ _Fluetsch_ _et_ _al._


have been dedicated to the detection and characterisation

of galactic outflows, especially powerful outflows that are
driven by AGN. Several studies have investigated the warm
ionized phase of outflows, finding velocities up to several
1000 km s [−][1] and radii up to several kpc (e.g. Westmoquette
et al. 2012; Harrison et al. 2014; Arribas et al. 2014; Rupke
et al. 2017). In high- _z_ quasars (QSOs) such ionized outflows
are seen to spatially anti-correlate with star formation in the
host galaxy, which has been regarded as direct evidence for
quasar-driven outflows quenching star formation in galaxies
(Cano-Diaz et al. 2012; Carniani et al. 2016, 2017). Numerous studies have confirmed the presence of prominent neutral atomic outflows in local galaxies (Morganti et al. 2005;
Rupke et al. 2005a; Cazzoli et al. 2016; Morganti et al. 2016;
Rupke et al. 2017). However, among all the gas phases involved in galactic outflows, the molecular phase is of particular interest, because it is found to dominate the outflow
mass (Feruglio et al. 2010; Rupke & Veilleux 2013; Cicone
et al. 2014; Garc´ıa-Burillo et al. 2015; Carniani et al. 2015;
Fiore et al. 2017). Furthermore, molecular gas is the phase
out of which stars form, hence molecular outflows directly
affect star formation.
Molecular outflows have been detected through P-Cygni
profiles of FIR OH transitions (Fischer et al. 2010; Sturm
2011; Veilleux et al. 2013; Spoon et al. 2013; Stone et al.
2016; Gonz´alez-Alfonso et al. 2017) and through broad wings
seen in interferometric observations of molecular transitions
such as low- _J_ CO lines (Feruglio et al. 2010; Cicone et al.
2012; Combes et al. 2013; Sakamoto et al. 2014; Garc´ıaBurillo et al. 2015) as well as higher density tracers such
as HCN (Aalto et al. 2012, 2015; Walter et al. 2017).
Using CO line mapping, Cicone et al. (2014) found that
starburst _M_ � outf (H 2 )/SFR)galaxiesof have1-4, butoutflowthe mass-loadingpresence of anfactorsAGN (dra-η =
matically increases η. Depletion time-scales due to the outflow, i.e. τ dep,outf (H 2 ) ≡ _M_ (H 2 )/ _M_ [�] outf (H 2 ), were found to anticorrelate with _L_ AGN, which further indicates that AGN boost
galactic outflows. In a study of AGN wind scaling relations
including molecular and ionized winds, Fiore et al. (2017)
observed that molecular� outflow mass rates correlate with
AGN luminosity as _M_ outf ( _H_ 2 ) ∝ _L_ AGN [0][.][76] [,] [while] [the] [ionized]
outflow� mass rates has a steeper dependence of the form
_M_ outf (ion) ∝ _L_ AGN [1][.][29] [,] [suggesting] [that] [at] [high] [luminosities] [the]
ionized phase may contribute significantly to the mass-loss
rate. However, it should be noted that these results were
achieved by comparing outflow phases observed in different
samples of galaxies, hence these results are potentially subject to (differential) selection effects among samples selected
to investigate different phases.
The purpose of this work is not to provide a census of
molecular outflows in galaxies (which would require high
sensitivity millimetre data for a large, volume–limited or
mass–limited sample of galaxies), but it is to explore the
scaling relations between molecular outflows and galaxy
properties. This will shed light on the driving mechanisms of
outflows and their effect on the host galaxies. We improve
relative to previous studies by significantly increasing the
statistics with a sample size of nearly 50 galaxies ( which is
more than twice that of previous molecular outflow studies
using CO data) and by tackling some of the biases and selection effects. We use interferometric CO measurements that
allow us to determine the velocity and spatial extent of the



outflows. We specifically investigate the relations between
outflow and galaxy properties such as star formation rate,
stellar mass and AGN luminosity. Furthermore, we include
data from the ionized and atomic phase of the outflow for
those galaxies in our sample that have this information available, and we investigate their relationship with the molecular
phase. This is crucial since galactic outflows are multiphase
and by focussing only on one phase the total impact of galactic winds on the ISM might be underestimated (e.g. Cicone
et al. 2018a).
Throughout this work, a _H_ 0 = 70 km s [−][1] Mpc [−][1], Ω M
= 0.27 and Ω Λ = 0.73 cosmology is adopted.


**2** **SAMPLE** **AND** **DATA** **ANALYSIS**


**2.1** **Sample** **Selection**


We have characterised molecular outflows both by collecting
data from the literature and from an extensive analysis of
ALMA archival data. We set an upper limit of _z_ <0.2 on the
redshifts of the targets, since beyond this redshift the angular resolution of most ALMA archival observations (>0.3 [′′] )
probes scales too coarse (>1 kpc) to enable a proper characterisation of outflows. We search the ALMA archive for
low- _J_ transitions (i.e. CO(1-0), CO(2-1) and CO(3-2)) of all
local galaxies observed in these transitions and with publicly available data in the archive as of April, 1st, 2018. As a
result we have analysed about 100 galaxies from the ALMA
archive. However, most of these data have turned out to have
sensitivities too low to enable the detection of putative faint
broad CO transitions associated with outflows. However, we
have detected outflow signatures in seven of these galaxies,
according to the procedure described in Sect. 2.2.
We generally do not use the ALMA observations for
which there is no outflow detection to set upper limits on
the outflow properties (e.g. outflow rate, kinetic power, momentum rate) since these would need knowledge of both outflow size and velocity, which is not known a priori. Yet, we
can infer tentative upper limits in three cases for which the
outflow is detected in other phases (in particular the ionized
phase) by assuming that the (undetected) molecular outflow
has the same size and velocity as those observed in the detected outflow phases. As a consequence, from the ALMA
archive we have obtained molecular outflow information for
a total of 10 galaxies (7 detections and 3 upper limits).
For what concerns the literature sample, we have
searched for published molecular outflows at _z_ _<_ 0.2 obtained through the analysis of the CO(1-0) and CO(2-1)
emission lines. We have compiled a total of 31 galaxies with
published molecular outflows (five of which are upper limits).
We also include four ULIRGs from Gonz´alez-Alfonso
et al. (2017) in our sample. In these cases the molecular outflow properties have been determined based on the
far-infrared transitions of OH observed through the Herschel/PACS spectrometer. Their outflow mass rates are calculated assuming a single expulsion of gas, which is analogous to what we assume in this paper (as it will be described in Sect. 2.3). For an additional four galaxies of the
Gonz´alez-Alfonso et al. (2017) sample the molecular outflow
rates inferred from OH have been measured also through CO


MNRAS **000**, 1–26 (2018)

_Cold_ _Molecular_ _Outflows_ _in_ _the_ _Local_ _Universe_ 3



observation and in these cases they are in reasonable agreement (typically within a factor of two).
The total sample used in this work consists of 45 galaxies whose properties, such as redshift, luminosity distance,
optical classification, star formation rate, AGN luminosity, AGN contribution to the bolometric luminosity (α bol =
_L_ AGN / _L_ bol ), molecular and atomic gas content and radio parameter _q_ IR are listed in Table 1. This sample is homogenised
as described in Sections 2.3 and 2.4, i.e. the properties of the
host galaxy and the outflow are calculated in a consistent
way across the entire sample. We stress that even though we
have not used any other selection criteria, our sample is still
heavily biased, as most of the ALMA observing programmes
(as well as results from the literature) have primarily targeted samples with enhanced star formation (ULIRGs or,
more generally, starbursts) or with a known AGN. Nevertheless, we have significantly enlarged the sample relative to
previous CO outflow studies by more than doubling its size
and by including galaxies that are more representative of
the massive star forming galaxy population, as they feature
also lower velocity outflows and much less extreme objects
than in previous studies. In particular, we have included
targets from the ALMA archive culled from observing programmes that were not aimed at extreme classes of galaxies
(starbursts or AGN), and this has resulted in a less biased
sample than in previous studies.
However, we emphasize, once more, that the goal of
this paper is not to provide an unbiased census of the occurrence of molecular outflows in galaxies. The primary goal
of this paper is to explore the relations between molecular
outflows and galactic properties by sampling the broadest
possible range of galactic properties, such as star formation
rate, mass, activity type, AGN luminosity.
To illustrate the range of SFRs and galaxy stellar
masses Fig. 1 shows the galaxies in our sample in the stellar mass - star formation rate plane. We also over-plot the
contours of the distribution of galaxies from the SDSS DR7
release, which shows the obvious biases affecting our sample.
The grey points indicate galaxies from a previous study on
molecular outflows by Cicone et al. (2014), the blue points
show the new, additional galaxies added in this work. Different symbols indicate different optical spectral classification,
as discussed more in detail later on. The sample spans about
two orders of magnitude in stellar mass and nearly four orders of magnitude in SFR. Clearly the galaxies in our sample
are not distributed uniformly over these ranges and do not
even follow the distribution traced by SDSS galaxies. As a
consequence of the selection biases our sample is skewed towards massive galaxies and mainly sampling galaxies above
the main sequence, hence (probably merger-driven) ‘starbursts’. However, our sample also probes the main sequence
and a few galaxies located in the green valley. Unfortunately,
quiescent galaxies are not included by our sample.
In addition, the fraction of AGN in our sample (≈ 50 per
cent) is higher than in other local complete surveys, where
about 10–20 per cent are unambiguously AGN (although
the actual number might be anything up to 40 per cent, depending on the AGN luminosity threshold and the selection
band) (Maiolino & Rieke 1995; Miller et al. 2003). However, this enables us to properly probe different level and
types of AGN activity. The AGN in our sample probe a
wide range of bolometric AGN luminosities, from very weak


MNRAS **000**, 1–26 (2018)









|3<br>2<br>1<br>0<br>/yr)<br>1<br>log(SFR)(M<br>2<br>3<br>2<br>1<br>0<br>1<br>2|Sy<br>LINER<br>HII|
|---|---|
|2<br>1<br>0<br>1<br>2<br>3<br>2<br>1<br>0<br>1<br>2<br>3<br>log(SFR) (M /yr)|Sy<br>LINER<br>HII|


9.0 9.5 10.0 10.5 11.0 11.5 12.0
M star (M )


**Figure** **1.** Distribution of our sample in the stellar mass-SFR
diagram, compared to the SDSS galaxies (contours). The grey
points show the galaxies in the sample of Cicone et al. (2014),
the blue galaxies represent the additional galaxies added to that
sample. The SDSS contours show the levels 100, 300, 500, 1000
galaxies. The red dot in the upper panel marks galaxies with
measurements of ionized outflows, the yellow dot in the lower
panel galaxies with observed neutral outflows.


AGN ( 10 [40] erg s [−][1] ), to powerful AGN in the quasar regime
( 10 [46] erg s [−][1] ).


**2.2** **Identification** **of** **Outflows**


The ALMA archival data have been calibrated and imaged
using the CASA software version 4.7 (McMullin et al. 2007).
We have ensured that the data cubes have a spectral window broad enough to find possible wings (covering at least
1500km s [−][1] ). We analyse the ALMA CO data initially by
searching for outflow signatures by fitting a single or a double Gaussian profile to the CO emission integrated over the
whole galaxy. Whether only one or two Gaussians are required, is determined by comparing the reduced chi-square
( χ red [2] [)] [value] [of] [their] [respective] [fits.] [If] [two] [Gaussians] [lead]
to a decrease in χ red [2] [of] [10] [per] [cent] [or] [more,] [then] [we] [con-]
sider this as an initial clue for the possible presence of an
outflow. In these cases we also visually verify whether we
can clearly distinguish a narrow (σ narrow ≲ 100 km s [−][1] ) and
a broad component (σ broad ranging from ∼100 km s [−][1] to
several 100 km s [−][1], depending on the galaxy). In these candidate cases we tentatively identify the broad component as
emission from an outflow as a first clue.
We then verify the presence of outflows by inspecting
the position-velocity (pv) diagram and producing a map of

4 _A_ _Fluetsch_ _et_ _al._


the line wings. Position-velocity diagrams are generated by
extracting a 2D spectrum along a pseudo-slit (with a typical
width of about 0.6 arcsec) placed along the major and minor
axes of the galaxy and plotting the velocity as a function
of the position along the pseudo-slit. Rotation-dominated
galaxies show a characteristic S-shape in the pv diagram
(along the major axis), whereas outflows are identified by
an excess of high-velocity gas on top of rotation. Line wings
maps are also produced by integrating over the spectral
range where the broad component (i.e. outflow component)
is dominant. We determine the root mean square (RMS) of
the line maps and identify the wings as significant when they
are detected at a significance level of - 5σ. The line wings
are identified as due to outflows if they have velocities in
excess of two times the width of the narrow component and
are not located in the direction of rotation. In the Appendix
A, we show for each galaxy the spectrum integrated over
the whole galaxy including the narrow and the broad component, the pv diagrams along the major and minor axes
and the line maps of the wings.


**2.3** **Outflow** **Properties**


We calculate the outflow mass based on the flux of the broad
line component, which can be converted into _L_ CO [′] [,] [defined]
as (Solomon & Vanden Bout 2005):


_L_ CO [′] [= 3][.][25][ ×][ 10] [7] _[S]_ [CO] [∆][v][ν] obs [−][2] _[D]_ L [2] [(1 +] _[ z]_ [)] [−][3] (1)


where _S_ CO ∆v is the integrated flux in Jy km s [−][1], ν obs is the
observed frequency of the CO transition (in GHz), _D_ L the
luminosity distance (in Mpc) and _z_ the redshift. _L_ CO(1 [′] −0)
can in turn be converted into molecular mass of the outflow ( _M_ outf (H 2 )) via _M_ outf (H 2 ) = α CO _L_ CO [′] [,] [where] [α] [CO] [is] [the]
CO-to-H 2 conversion factor. For outflows we conservatively
assume a CO-to-H 2 conversion factor of 0.8 M ⊙ /(K km s [−][1]

pc [2] ) to for consistency with previous work. This is the value
typically adopted for the molecular ISM of ULIRGs (Bolatto et al. 2013). The excitation in the wings and the core
in Mrk 231, a ULIRG hosting the closest QSO and a well
studied outflow, were found to be very similar and hence
the conversion factor in the non-outflowing and outflowing
components are likely to be similar (Cicone et al. 2012). In
some outflows the conversion factor has been studied in detail (see e.g. Weiß et al. 2005; Cicone et al. 2018b) yielding
values closer to α CO ≈ 2 M ⊙ /(K km s [−][1] pc [2] ).
For outflows observed in higher- _J_ transitions we assume
that the CO emission is thermalised and optically thick,
hence _L_ CO(3 [′] −2) [=] _[L]_ CO(2 [′] −1) [=] _[L]_ CO(1 [′] −0) [.] [This] [is] [consistent,]
within the errors, with what was found in Mrk 231 (Feruglio et al. 2015). The double component fitting allows us to
directly estimate the outflow velocity (v outf ) using the prescription of Rupke et al. (2005a): v outf = FWHM broad /2 +
_|_ v broad - v narrow _|_, where FWHM broad is the full width at half
maximum of the broad component and v broad and v narrow
are the velocity centroids of the broad and narrow components, respectively. The spatial extent of the outflow is calculated based on the line maps of the broad wings. We fit
a 2D-Gaussian profile to the wing map and use the beamdeconvolved major axis (FWHM) divided by two as the radius of the outflow.
The mass outflow rate, _M_ [�] outf (H 2 ), is calculated assuming



time-averaged thin expelled shells or clumps (Rupke et al.
2005b):


_M_ � outf (H 2 ) = _[v]_ [outf] [(][H] [2] [)] _[M]_ [outf] [(][H] [2] [)] . (2)
_r_ outf (H 2 )


where v outf (H 2 ), _r_ outf (H 2 ) and _M_ outf (H 2 ) are the velocity, radius and molecular gas mass of the outflow, respectively.
This description allows us a better comparison with models and is more realistic than the assumption of spherical
(or multi-conical) volume with uniform filling factor (Cicone et al. 2015; Pereira-Santaella et al. 2016; Veilleux et al.
2017). It can be shown that between the two scenarios there
is a difference of a factor of three in the estimates of the outflow rate (and derived quantities such as kinetic power and
momentum rate), which does not alter our conclusions significantly. Projection effects certainly plague the estimation
of the outflow radius and velocity. However, as discussed
in Cicone et al. (2015), since the orientations of outflows
are distributed randomly, it can be shown that the resulting average correction factor is unity, hence statistically the
(unknown) projection correction factors cancel out on average, though they certainly introduce scatter. By combining
all sources of uncertainty, we infer that the average uncertainty on the mass outflow rate is about 0.3 dex. The errors
on the associated outflow properties (kinetic power, momentum rate) is estimated to be as large as 0.5 dex.


**2.4** **Ancillary** **information**


In this section we provide ancillary information on the host
galaxy, which are summarized in Table 1.


_2.4.1_ _Optical_ _classification_


In terms of activity classifications, we refer to galaxies as
‘star forming’, ‘Seyfert’ and ‘LINER’ based on their optical spectroscopic classification, and in particular through
the BPT-[SII] diagram (Kewley et al. 2006). The nature
of galaxies classified as ‘LINER’ is not always clear, and
this classification appears to include a mixed population. It
has been shown that the ‘LINER’ emission can extend on

kpc-scales across a large fraction of passive and green valley
galaxies (hence renaming this class as ‘LIER’, i.e. dropping
the ‘N’ which stands for ‘Nuclear’ in the original acronym)
and correlates with the old stellar population, and this can
be explained in terms of excitation by the hard radiation
field produced by evolved post-AGB stars (e.g. Sarzi et al.
2010; Belfiore et al. 2016). However, in the nuclear regions,
LI(N)ER-like emission can also be associated with excitation
by weak, radiatively inefficient AGN (e.g. Ho et al. 1993).
Yet, in LIRGs, ULIRGs, and other galaxies characterised
by prominent outflows, which are most of the LINER-like
galaxies in our sample, LI(N)ER-like diagnostics are likely
associated which shock excitation (e.g. Monreal-Ibero et al.
2006). Many authors broadly group Seyfert and LI(N)ERlike diagnostics into a generic ‘AGN’ category. As discussed
above, this rough classification can be misleading as in many
galaxies the LINER classification is not associated with an
AGN at all; however, in the case of our sample it is true
that many LINER-like galaxies do host an AGN based on
the X-ray or mid-IR properties; therefore in a few instances


MNRAS **000**, 1–26 (2018)

in the paper (e.g. Sect. 3.2) we will adopt this classification
as well. Regardless of the optical classification, the role of
the AGN, if present, will be clarified by the AGN fractional
contribution to the bolometric luminosity, as discussed in
the following.


_2.4.2_ _AGN_ _luminosity_


AGN bolometric luminosities were derived from the hard Xray flux (2-10 keV) by using the relation given in Marconi
et al. (2004): log[ _L_ AGN / _L_ (2-10 keV)] = 1.54 + 0.25L +
0.012L [2] - 0.0015L [3], where L = (log _L_ AGN -12) and _L_ AGN
is the AGN bolometric luminosity in units of _L_ ⊙ . Typically,
X-ray-based AGN luminosities have a scatter of ∼ 0.1 dex
(Marconi et al. 2004). In a few cases where no X-ray data
are available, or the source is Compton-thick, we used the

[OIII]λ5007 luminosity. In this case the AGN luminosity is
inferred from the relation _L_ AGN ∼ 3500 _L_ [OIII] (Heckman
et al. 2004). In some cases for which [OIII]λ5007 is not available, or which are heavily obscured in the optical, we estimated the AGN luminosity by using the AGN contribution
to the bolometric luminosity α bol as inferred from various
mid-IR diagnostics in the literature (Veilleux et al. 2009;
Nardini et al. 2009, 2010). Nardini et al. (2009) and Nardini
et al. (2010) use spectral features in the wavelength range
5-8 µm that allow them to disentangle AGN and starburst
contribution. Veilleux et al. (2009) use six different IR-based
methods, as for instance the equivalent width of the PAH
feature at 7.7 µm and the continuum ratio of _f_ 30 / _f_ 15, and
average them to calculate the AGN contribution. Using the
AGN fraction, we can then calculate the AGN luminosity via
_L_ AGN = α bol _L_ bol, where in most cases _L_ bol ≈ _L_ IR (although
for ULIRGs _L_ bol ∼ 1.15 _L_ IR (Veilleux et al. 2009)). In the rest
of the paper α bol = _L_ AGN / _L_ bol refers to the AGN contribution to the total IR luminosity, which generally dominates
in most of our galaxies, although in a few more quiescent
galaxies the stellar optical/NIR light may contribute significantly. The uncertainty of the IR luminosity consists of the
contribution from uncertainties on the IR fluxes at 12, 25,
60 and 100 µm, which are generally below 10 per cent and
the scatter in the calculation of the total IR luminosity, _L_ IR,
based on these IRAS fluxes, which is about 10-20 per cent
(Takeuchi et al. 2005). In total, we therefore conservatively
assume 30 per cent uncertainty on _L_ IR .


_2.4.3_ _Star_ _Formation_ _Rate_


To compute the total star formation, we use the _L_ IR -SFR
relation given in Kennicutt & Evans (2012), which assumes
a Chabrier IMF and the total infrared luminosity from 8 to
1000 µm, corrected for the AGN contribution through the
α bol factor. The uncertainty in star formation rates stems
from uncertainties on _L_ IR (which is discussed above and
amounts to ∼ 30 per cent) and on α bol . α bol has similarly values using various techniques and they usually agree within
10-15 per cent (Veilleux et al. 2009). We assume this as the
typical error. The conversion of infrared luminosity to SFR
comes with a 30 per cent calibration uncertainty (Kennicutt
1998). For star formation rate estimates, we therefore infer
conservatively a typical uncertainty of 0.3 dex.


MNRAS **000**, 1–26 (2018)



_Cold_ _Molecular_ _Outflows_ _in_ _the_ _Local_ _Universe_ 5


_2.4.4_ _Gas_ _content_


The molecular gas mass in the host galaxy is inferred from
the CO(1-0) (narrow) line luminosity _L_ CO [′] [,] [as] [discussed]
above. The CO-to-H 2 conversion factor is one of the major
uncertainties in the calculation of the molecular gas mass
and depends heavily on the metallicity and physical state
of the molecular ISM (Bolatto et al. 2013). We adopt three
different CO-to-H 2 conversion factors depending on the type
of galaxy. For ULIRGs, we adopt α CO = 0.8 M ⊙ /(K km s [−][1]

pc [2] ), for LIRGs we use α CO = 1.2 M ⊙ /(K km s [−][1] pc [2] ) and
for all other galaxies we use a Milky Way-type conversion
factor of 4.4 M ⊙ /(K km s [−][1] pc [2] ) (Bolatto et al. 2013).
For about half of the galaxies 21cm HI, single dish, observations are also available which provide the atomic gas
mass in the host galaxy.


_2.4.5_ _Stellar_ _mass_


Stellar masses are calculated for all galaxies in this sample
by using the _K_ -band magnitude and a colour correction (e.g.
_B_   - _V_ ) (Bell et al. 2003). _K_ -band magnitudes are taken from
the extended source catalogue of 2MASS (Skrutskie et al.
2006).
However, the presence of an AGN can potentially contaminate the observed fluxes. For Seyfert 2 galaxies, the direct continuum radiation from the accretion disc is obscured

along our line of sight, but the hot dust heated by the AGN
can still contribute significantly to the light observed in the
_K_ -band. Therefore, in the case of Seyfert 2 galaxies, in order to avoid the latter issue, we use _J_ -band magnitudes,
that are not affected by AGN-heated circumnuclear dust
emission, and estimate the _K_ -band magnitude by assuming
_J_ – _K_ =0.75, which is the average colour (with little scatter)
found by Mannucci et al. (2002).
For Seyfert 1 galaxies in our sample a contamination
by the AGN might be very high also in the _J_ -band and optical bands (because the radiation from the accretion disc
is directly observable) and, therefore, we need to use a different approach. For Mrk 231 and IRAS F11119+3257, the
contribution of the AGN to the total magnitudes has been
estimated in Veilleux et al. (2002) and we simply subtract
this nuclear contribution to estimate the stellar masses in

these two galaxies. For the other three Seyfert 1 galaxies, we
compute the stellar mass by using the _H_ -band magnitude of
the host (which does not include nuclear contribution by the
AGN) inferred by Zhang et al. (2016) and the mass-to-light
correction given in their paper.
For non-type 1 AGN, the colours for the mass-to-light
ratio correction are obtained from the literature. We com
bine different colours, _u_   - _g_ for galaxies with SDSS photometry, _B_   - _V_ from VERONCAT, the Veron Catalogue of
Quasars and AGN (V´eron-Cetty & V´eron 2010), or from
the GALEX survey (Gil de Paz et al. 2007) and _B_   - _R_ from
the APM catalogue [1] . In a few cases where no information
about colours is available, we assume an average logarithmic mass-to-light correction of -0.08 (Bell et al. 2003; Zhang
et al. 2016). Our final errors on the stellar mass comprises


1 ∼
http://www.ast.cam.ac.uk/ mike/apmcat/

6 _A_ _Fluetsch_ _et_ _al._


errors on the photometry of the host galaxy ( _H_, _J_ or _K_ band) and the uncertainty of the _M_ ⋆ / _L_ ratio. The _K_ -band
magnitude are estimated to have an 0.1 mag uncertainty
based on comparison between different samples (Bell et al.
2003). In the _J_ and _H_ -band, the typical uncertainty is 0.2
mag (Zhang et al. 2016). Our estimates of _M_ ⋆ / _L_ ratios have
a typical systematic error of about 25 per cent which stems
from uncertainties in galaxy age, dust extinction and the impact of SF bursts on the star formation history (Bell et al.
2003). Furthermore, for AGN host galaxies, additional uncertainties might be introduced by the corrections applied
here. Therefore, we conservatively obtain an average error
of ±0.2 dex on the stellar masses. Although the use of different colours for some of the galaxies may potentially be a
matter of concern, Bell & de Jong (2001) and Taylor et al.
(2011) have shown that there is no systematic uncertainties
on the inferred stellar masses when different colours and different (infrared/red) bands are used.


_2.4.6_ _Radio_ _emission_


In order to investigate the potential link between outflows
and radio jets, we have also collected data about the radio
power in galaxies at 1.4 GHz, mostly by using the database
provided by NED. Since in normal star forming galaxies the
radio luminosity simply scales with the SFR as traced by the
infrared luminosity (e.g. Yun et al. 2001; Ivison et al. 2010),
the contribution from a radio jet can be inferred in terms of
excess relative to the radio-to-infrared ratio observed in nor
mal star forming galaxies. Therefore, in Table 1 we provide
the quantity _q_ IR which is the ratio between the rest frame
8-to-1000 µm flux and the 1.4 GHz monochromatic radio
flux (Ivison et al. 2010).


**2.5** **Ionized** **Outflows**


We complement our results on molecular outflows with data
on the ionized outflow phase. For each galaxy, we search
whether a reliable estimate of the ionized outflow mass is
provided in the literature. 16 of our sources, i.e. about 1/3 of
the sample have measurements of the ionized outflow mass,
velocity and radius. Rupke & Veilleux (2013) provide ionized gas masses for four galaxies (IRAS F08572+3915, IRAS
F10565+2448, Mrk 273 and Mrk 231) based on the H α emission. Greene et al. (2012) estimate the ionized outflow mass
for SDSS J1356+1026 using H β. The other sources with
ionized outflow rates are taken from Arribas et al. (2014)
and are based on integral field spectroscopy (IFS) of H α.
We carefully homogenise the calculations of the ionized outflow properties. Outflow velocities are calculated
in the same way as for molecular outflow, i.e. v outf (ion) =
FWHM broad (ion)/2 + _|_ v broad (ion)-v narrow (ion) _|_ (Rupke et al.
2005a). For the calculation of the outflow mass, _M_ outf (ion),
we assume an electron density of _n_ e = 315 cm [−][3] as found in
Arribas et al. (2014). This value is also close to the electron
density values found in other works (e.g. Perna et al. 2015;
Bischetti et al. 2017). We calculate the ionized outflow mass
rate as follows:


_M_ � outf (ion) = _[v]_ [outf] [(][ion][)] _[M]_ [outf] [(][ion][)], (3)
_R_ outf (ion)



where _R_ outf (ion) is the radius of the outflow.
For the outflow extent, we generally assume the same value
given in the corresponding paper. However, in Arribas et al.
(2014), an average fixed radius of 700 pc is assumed. Instead
of using this fixed radius, we use the value inferred from Bellocchi et al. (2013) using the broad H α maps obtained with
VIMOS at the Very Large Telescope (VLT) and assuming a
spherical geometry.
We note that the spatial extent of ionized outflow can
be severely affected by beam smearing effects, because the
observed spatial distribution is luminosity weighted, hence
the central, compact regions dominate the outflow size measurement, even if the outflow is much more extended. This
results in an overestimation of the outflow rate. Indeed, the
uncertainty on the outflow extent (limited by the typical
seeing of about 1 [′′] ), often resulting into an error of 50% on
the outflow radius, dominates the uncertainty on the outflow
rate shown in the various figures.
Measurements of the ionized outflow are available for only
1/3 of the sample. Galaxies in our sample with ionized outflow measurement are indicated with a red dot in the top
panel of Fig. 1. Unfortunately, the part of the sample with
available ionized outflow information is restricted to the
mass range 10.4 < log ( _M_ ∗ / _M_ ⊙ ) < 11.6, hence limiting our
capability to properly explore the full mass range probed
by the molecular outflow sample. However, within this mass
range, the galaxies with ionized outflows sample the full SFR

range.


**2.6** **Neutral** **Outflows** **from** **Na** **I** **D**


We also include data on neutral atomic outflows in the
same way as for the ionized outflows. We crossmatch our
sample with Rupke & Veilleux (2013) and Cazzoli et al.
(2016), where the properties of the neutral outflow are inferred from the blue-shifted neutral sodium absorption doublet lines (Na I D) at 5890 [˚] A and 5896 [˚] A. The Na I D
absorption method can only trace outflows towards those
lines of sights that have enough stellar continuum light in
the background; this often limits the use of this diagnostic
to the central regions of galaxy disks. Additional issues affecting this diagnostics is that it has to be disentangled from
the Na I D stellar absorption, from possible Na I D emission
and from the nearby He I nebular emission.
With these caveats in mind we have taken the outflow
rate inferred in the original papers. We have also attempted
to re-determine the outflow rate by taking the outflow mass
given in the original papers and re-calculating the outflow by
using our approach, based on size and outflow velocity, although in this case the method is not fully applicable as the
covering factor is another parameter that should be taken
into account. In most cases we obtain values close to those re
ported in the original papers, however, for a couple of galaxies the difference is as high as a factor of three. We will use
both the atomic outflow rate reported in the original papers
and those recalculated by us.


**2.7** **Neutral** **outflows** **from** **[CII]**


The fine-structure transition of C [+], [CII], is another tracer of
cold neutral gas, which has been increasingly used to search


MNRAS **000**, 1–26 (2018)

outflows, especially at high redshift (Janssen et al. 2016;
Maiolino et al. 2012; Cicone et al. 2015; Gallerani et al.
2018). The majority of [CII] emission is believed to stem
from photon dominated regions (PDRs), where the bulk
of the gas is in the neutral atomic phase. However about
20 per cent is generally coming from CO-dark molecular gas
and about 30 per cent can come from the partly ionized
phase (Pineda et al. 2014). We have collected data on the

[CII]-outflow for our sample from Janssen et al. (2016), who
provide the atomic mass in the outflow based on the [CII]
broad/narrow components decomposition, assuming a temperature of 100 K and density of 10 [5] cm [−][3], which should
be typical of the ULIRGs in their sample. The outflow rate
is then calculated by taking the radius estimated from the
CO observations and consistently with the method used for
molecular outflows, as described above.
As we will see in the next section a few targets have measurements of atomic neutral outflows both from Na I D and [CII].
In some of these cases the agreement between the measured
mass-loss rates is within a factor of two, which is remarkable
given all assumption, potential systematics and issues discussed above. However, for one ULIRG hosting a powerful
AGN (Mrk 273) the difference is as large as an order of magnitude, hinting at the fact that for some extreme targets the
uncertainties in the estimation of the atomic neutral outflow
can be very large.
Combining the measurements of atomic neutral outflows from Na I D and [CII] measurements (also taking
into account galaxies which have both measurements) only
12 galaxies have this information (about one fourth of the
full sample). These are indicated with a yellow dot in the
bottom panel of Fig. 1. They span the limited mass range
10.6 < log ( _M_ ∗ / _M_ ⊙ ) < 11.6, and only probe galaxies with
high SFR (generally higher than the main sequence), implying that the atomic neutral outflows in our sample are
hardly representative of the broader population of galaxies (in terms of mass and SFR), probed by the full sample
with molecular outflow information. The extrapolation of
the atomic neutral information to the full sample should be
considered with great care, and possibly expanded in the
future.


**3** **RESULTS**


In this section we report the main results obtained through
our sample of molecular outflows, in combination with the
ancillary data. A more extensive analysis of the results and
of their interpretation is given in Section 4.


**3.1** **Atomic** **neutral** **and** **ionized** **outflows** **in**
**comparison** **with** **molecular** **outflows**


We start by investigating the relation between molecular
outflow rate and atomic neutral and ionized outflow rates
for those galaxies in our sample that have additional multiwavelength data suited for such a study.
In Figure 2, we plot the molecular outflow rate as a
function of ionized outflow mass rate of the same object, for
those galaxies that have information on _both_ outflow phases
available. Star forming galaxies have comparable ionized and


MNRAS **000**, 1–26 (2018)



_Cold_ _Molecular_ _Outflows_ _in_ _the_ _Local_ _Universe_ 7


1







0.8


0.6


0.4


0.2


0



log(M OUTF (H 2 )) (M /yr)


**Figure** **2.** Molecular outflow mass rate (M [�] outf (H 2 )) compared to
the ionized outflow mass rate (M [�] outf (ion)). The dashed line shows
the 1:1 relation. Circles indicate Seyfert host galaxies, LINERs are
plotted as triangles and purely star forming galaxies as stars. The
data points are colour-coded according to their AGN contribution
(L AGN /L bol ), as given in the colour bar on the right. The data
points with black edges are molecular outflows inferred from OH
measurements by Gonz´alez-Alfonso et al. (2017). The symbols
with a central white dot are the candidate ‘fossil’ outflows (see
sect.4.3).



4


3





2


1



0



1

40 42 44 46
log(L AGN ) (erg/s)



1


0.8


0.6


0.4


0.2


0



**Figure** **3.** Molecular to ionized mass outflow rate as a function
of AGN luminosity. Colour-coding and symbols are as in Fig. 5.


molecular outflow rates. As we will see, the molecular outflow loading factor for star forming galaxies is close to one,
implying that also the ionized outflow loading factor is close
to unity, in agreement with independent studies focussed
specifically on ionized outflows (Heckman et al. 2015).
In contrast, AGN host galaxies have much higher molecular outflow rates than ionized ones. This is in agreement with previous studies (Rupke & Veilleux 2013; Garc´ıaBurillo et al. 2015; Carniani et al. 2015; Fiore et al. 2017),
which observed that molecular outflow rates are 2-3 magnitudes higher than ionized outflow rates. Rupke et al. (2017)
also investigate the multi-phase outflow in a few quasars;
only two objects in their sample have measurements in the
molecular phase, and in these two cases the molecular phase
dominate the outflow mass relative to the atomic phase.
At higher AGN luminosities (above 10 [46] erg s [−][1] ), it has

8 _A_ _Fluetsch_ _et_ _al._







1


0.8


0.6


0.4





0.2


0



**Figure** **4.** Neutral atomic outflow rates inferred from the [CII]
line or the Na I D absorption (outlined using black squares) as
a function of the molecular outflow rates. Measurements of the
same galaxy obtained with two different methods ([CII] or Na I D)
are connected with a dashed black line. The diagonal dashed line
gives the 1:1 relation. Colour-coding and symbols are as in Fig.

2.


been suggested that the ionized winds have similar mass
outflow rates to molecular winds (Fiore et al. 2017); however, these previous studies were mostly based on the comparison of galaxy samples which were observed in different
gas phases. It is difficult to directly investigate the relation between molecular and ionized gas in luminous, distant quasars, as it generally very challenging to detect their
molecular outflows through their weak CO wings, which
are in most cases still below the detection limits, even for
ALMA observations, for most high- _z_ QSOs. The few deep
ALMA/NOEMA observations and studies reported so far
on some individual quasars are not conclusive yet. Brusa
et al. (2018) have reported the detection of a molecular (CO)
outflow rate comparable with the ionized outflow rate in a
quasar at _z_ ∼1.5, while Toba et al. (2017) have reported the
lack of molecular (CO) outflow in an AGN at _z_ ∼0.5. However, in both cases the sensitivity of the millimetre observation is still far from what would be required to match the
optical/near-IR observations, hence a significant amount of
outflowing molecular gas may still be missed in these observations. Carniani et al. (2017) have reported the detection of
a molecular outflow in a quasar at _z_ ∼2.3, having an outflow
rate much larger than the ionized outflow rate. Feruglio et al.
(2017) have reported the detection of a fast and massive
molecular outflow ( _M_ [�] outf (H 2 ) = 3-7×10 [3] M ⊙ yr [−][1] ) in a lensed
quasar at _z_ ∼4, but unfortunately in this case the ionized outflow rate is not available for comparison. Although, it is not
yet possible to make a direct, statistically sound comparison
of the ionized and molecular outflow rates at very high luminosities, we can at least investigate the relationship and
trend within the luminosity range probed by our sample.
Fig. 3 shows the dependence of the ratio between molecular
and ionized outflow rate as a function of the bolometric luminosity of the AGN. The ratio _M_ [�] outf (H 2 )/ _M_ [�] outf (ion) clearly
increases with AGN luminosity, which is the opposite trend
of that obtained in the past based on disjoint samples of
ionized and molecular outflows (Fiore et al. 2017). However,
our sample is still small and does not reach up to very high



AGN luminosities ( _>_ 10 [46] erg s [−][1] ). Yet, overall our data
confirm the results of Fiore et al. (2017) and Carniani et al.
(2015) that, in our luminosity range ( _L_ AGN < 10 [46] erg s [−][1] ),
molecular outflows have outflow rates about two order of
magnitude larger than ionized outflow rates.
Neutral atomic gas can be measured through the Na I D
absorption, but it is subject to significant uncertainties due
to the fact that it can be probed only where there is enough
background stellar light. Moreover, disentangling the Na I D
absorption outflow feature from the Na I D stellar absorption and from the ISM absorption in the host galaxies, as
well as from the He I an Na I D nebular emission, further
increases the uncertainties. An alternative way to probe the
atomic neutral outflow is to exploit the fine-structure line of
C [+], [CII]λ157.74 µm, which, as discussed in Sect. 2.7, traces
primarily atomic gas. Janssen et al. (2016) measured the outflowing mass of atomic gas in a sample of ULIRGs/LIRGs
some of which are in our sample, and for which we have
inferred the atomic outflow rate as discussed in Sect. 2.7.
In Fig. 4 we compare the atomic outflow mass rate inferred
from both [CII] and Na I D (surrounded by a black square)
with the molecular outflow rate from this work for galaxies with measurements of both tracers. The sample size is
small so far. Despite this, the inferred atomic outflow rates of
AGN host galaxies seem to be very similar to the molecular
outflow rates suggesting that outflows have similar contribution of atomic neutral and molecular gas. For star-forming
galaxies the outflow masses are comparable in the atomic
and molecular phase, but any possible trend is likely washed
out by the above mentioned uncertainties. The discrepancy
between the Na I D and the carbon measurements can be ex
plained in the uncertainties associated with Na I D discussed
above, though more observations are needed to investigate
these issues.

With the limited statistics available for the sub-samples
with multiple outflow phases, it is not possible to provide accurate relationships among the various phases, also because
there is significant dispersion. However, it is useful to provide some indication on the rough relationship between the
molecular outflow and other two phases, which can provide
some guidance on how to obtain the _total_ outflow rate (and
other derived quantities) to correct the molecular outflow
rate by roughly accounting for the additional phases. Based
on the results above we can roughly state that in starburstdriven outflows the ionized and neutral atomic phases contribute, each of them, to the outflow rate at the same level
as the molecular outflow rate. In AGN-driven outflows the
atomic neutral outflow rate is similar to the molecular outflow rate, while the ionized outflow rate is negligible. We
will adopt these simple recipes, when attempting to infer
the global properties of outflows in the following sections.


**3.2** **Mass** **outflow** **rate** **scaling** **relations**


In this section we start investigating the scaling relations
between the molecular outflow rate and galaxy properties,
with the goal of obtaining a first indication of the driving
mechanism in different regimes.


MNRAS **000**, 1–26 (2018)

**Figure** **5.** Mass outflow rate as a function of star formation rate.
The black dashed line� shows the relation for a outflow massloading factor η = M outf (H 2 )/SFR = 1. The black dashed line is
the 1:1 relation between outflow rate and SFR, i.e. η = 1. The red
and blue dashed lines represent the best fits to AGN hosts and
star forming/starburst galaxies, respectively. The vertical black
and grey arrows indicate the average correction of the outflow
rate, for AGN and star forming galaxies, respectively, once the
atomic (ionized and neutral) phases average contributions to the
of the outflow rate (as inferred in Sect. 3.1) are included. Colourcoding and symbols are as in Fig. 2.



3


2


1


0


1



0.00 0.25 0.50 0.75 1.00



1


0.8


0.6


0.4


0.2


0



bol [= L] AGN [/L] Bol


�
**Figure** **6.** Mass loading factor η = M outf (H 2 )/SFR as a function of AGN fractional contribution to the bolometric luminosity,
L AGN /L bol . The black dashed line shows the relation for an outflow mass-loading factor η = 1. Colour-coding and symbols are
as in Fig. 2.


_3.2.1_ _Dependence_ _on_ _SFR_ _and_ _L_ AGN


Figure 5 shows the molecular mass outflow rate _M_ � outf (H 2 )
as a function of the SFR, colour-coded by AGN contribution to the bolometric luminosity. Similar to what was found
in smaller samples in previous works (Cicone et al. 2014;
Garc´ıa-Burillo et al. 2015), the star forming/starburst galaxies have a mass-loading factor η = _M_ [�] outf (H 2 )/SFR consistent
with unity or slightly lower. As we have discussed in the previous section, in star forming galaxies the contribution to the
total mass-loss rate is similar for different gas phases (ionized/neutral atomic and molecular). By including all the gas
phases, the total mass-loss rate increases roughly by 0.5 dex,
which is indicated by the grey arrow, and which brings the


MNRAS **000**, 1–26 (2018)



_Cold_ _Molecular_ _Outflows_ _in_ _the_ _Local_ _Universe_ 9


total loading factor closer to (or exceeding) unity for star
forming galaxies. However, for the moment we focus on the
molecular outflow rate. The best-fit of the relation between
molecular outflow rate and SFR for SF galaxies (shown as
a dashed blue line in Fig. 5) is log( _M_ [�] outf (H 2 )/(M ⊙ yr [−][1] ))
= 1.19 [+0] −0 [.] . [16] 16 [log(SFR/(M] [⊙] [yr] [−][1] [))] [–] [0.59] [+0] −0 [.] . [28] 28 [.] [This] [and] [the]
following fits are performed by using linmix (Kelly 2007),
considering the error bars both in x and y and including
upper limits.

The AGN host galaxies have a mass-loading factor larger than unity, especially those that are AGNdominated, and η ranges from a factor of a few up to
a hundred. The best-fit relation for AGN host galaxies is
log( _M_ [�] outf (H 2 )/(M ⊙ yr [−][1] )) = 0.76 − [+0] 0 [.] . [11] 11 [log(SFR/(M] [⊙] [yr] [−][1] [)) +]
0.85 [+0] −0 [.] . [18] 18 [and] [is] [shown] [with] [a] [red] [dashed] [line] [in] [Fig.] [5][.] [As]
we have discussed in the previous subsection, in AGN host
galaxies the atomic phase makes, on average, a comparable contribution to the outflow rate as the molecular phase,
while the ionized phase is generally negligible, at least in the
luminosity range probed by us. The effect of including the
atomic component of the outflow for AGN is shown with a
black arrow.

The outflow properties inferred in star forming galaxies are in good agreement with models predicting a massloading factor η close to 1 (e.g. Finlator & Dav´e 2008; Dav´e
et al. 2011; Heckman et al. 2015), where feedback from supernovae is the main outflow driver and required to properly
regulate star formation in galaxies.

Galaxies containing an AGN have loading factors larger
than 1 indicating that gas is removed at a faster rate than
stars are formed. In particular, the presence of a strong AGN
in the galaxy increases the (molecular) outflow mass loadingfactor substantially. In particular, the higher the AGN contribution (α bol, see colour-coding in Fig. 5), the higher their
mass-loading factor η. This is illustrated even more clearly
in Fig. 6, where the relation between the outflow loading factor, i.e. η = _M_ [�] outf (H 2 )/SFR and α bol = _L_ AGN / _L_ bol is shown.
However, a correlation is only seen at _L_ AGN / _L_ bol _>_ 0.7, while
at 0.1 _<_ _L_ AGN / _L_ bol _<_ 0.7, the loading factor η simply scatters between 1 and 10 for AGN. As we will discuss further
later on, this is probably due to two effects: 1) additional
contribution from star formation to the outflow rate (which,
however, is expected to contribute only with η ∼ 1); 2) the
fact that the outflow has much longer time-scale ( _>_ 10 [6] yr)
than the AGN accretion variability (∼ 10 -10 [5] yr) (Gilli et al.
2000; Schawinski et al. 2015), hence the outflow is expected
to generally outlast an AGN which has recently switched off,
or decreased in luminosity.

Figure 7 shows the correlation between the mass outflow rate and _L_ AGN . The dashed line shows the best-fit to
the AGN host galaxies (LINERs, Seyfert 1 and Seyfert 2),
excluding purely star forming galaxies (optically classified
as star forming/starburst), which gives the following relation: log( _M_ [�] outf /(M ⊙ yr [−][1] )) = 0.68 [+0] −0 [.] . [10] 10 [log(] _[L]_ [AGN] [/(erg] [s] [−][1] [))]
    - 28.5 [+4][.][6] [Comparing] [with] [the] [predictions] [from] [chemo-]
4.6 [.]
hydrodynamic simulations (Richings & Faucher-Gigu`ere
2018), the observed values are about 1 dex higher at _L_ AGN
= 10 [44] erg s [−][1], but are consistent with simulations at _L_ AGN
≈ 10 [46] erg s [−][1] within the errors. Although Seyfert galaxies
show a correlation between AGN luminosity and molecular
outflow mass rate, suggesting that these outflows are AGN

10 _A_ _Fluetsch_ _et_ _al._



10 11 12
M star (M )



1


0.8


0.6


0.4


0.2


0





4


3


2


1


0













**Figure** **7.** Mass outflow rate as a function of AGN (bolometric)
luminosity. The dashed line indicates the fit to the AGN host
galaxies (LINERs, Seyfert 1 and 2). Colour-coding and symbols
are as in Fig. 2.



4


3


2


1


0





10.0 10.5 11.0 11.5 12.0
M star (M )



1


0.8


0.6


0.4


0.2


0



**Figure** **8.** Molecular outflow mass rate as a function of galaxy
stellar mass. Colour-coding and symbols are as in Fig. 2.


driven, this correlation is looser and with larger scatter than
previously found in the literature (e.g. Cicone et al. 2014;
Fiore et al. 2017), probably as a consequence of our sample being less biased. Nevertheless, this is still supportive
of the scenario in which luminous AGN boost the outflow
rate by a large factor and nearly proportionally to the AGN
radiative power. It is interesting to note that Fig. 7 clearly
shows the presence of a significant fraction of galaxies (indicated by symbols with a central white dot) with high outflow
rates but little AGN contribution and, for those classified as
AGN, clearly not following the correlation observed for the
bulk of luminous AGN host galaxies. As discussed above,
this is partly due to contribution by star formation, but the
bulk of the effect may be due to ‘fossil’ AGN-driven outflows
as it will be clarified in the Section 4.


_3.2.2_ _Dependence_ _on_ _galaxy_ _stellar_ _mass_


Fig. 8 shows the outflow rate as a function of stellar mass.
This plot shows some correlation, which may be indirectly
linked to the correlation between outflow rate and SFR,



**Figure** **9.** Mass-loading factor as a function of stellar mass. The
red dashed line shows the best-fit to the data. Colour-coding and
symbols are as in Fig. 2.


through the stellar mass-SFR relation for galaxies on the
‘main sequence’. An important prediction of theoretical
models of feedback from star formation is that the outflow
loading factor should anti-correlate with the galaxy stellar
mass as η ∝ _M_ ⋆ [−][0][.][5], as a consequence of the deeper gravitational potential well in more massive galaxies (Mitra et al.
2015; Somerville & Dav´e 2015; Chisholm et al. 2017). Figure 9 shows the dependence of the mass loading factor η
on the stellar mass. Clearly, the observed relation between
outflow mass-loading factor and stellar mass is very scattered. A linear regression indicates that there is only a weak
anti-correlation of the form log(η) = -0.18 [+0] −0 [.] . [24] 24 [log(] _[M]_ [⋆] [/M] [⊙] [)]
+ 2.3 [+2] −2 [.] . [7] 6 [,] [i.e.] [only] [marginally] [consistent] [with] [theoretical]
predictions. However, before invoking any tension with theoretical models one should be aware of three main issues:
1) we include AGN-driven and star formation-driven outflows, whereas the models make predictions about outflows
driven by SNe and stellar radiation pressure, 2) the range
of stellar masses is probably too narrow to properly test the
theoretical predictions, especially given that the dependence
of the outflow rate on mass is weak (slope of –0.5 in log);
3) thirdly, the simple relation of outflow rate with stellar
mass is convolved with the dependence on SFR and with
the AGN contribution, which likely dominate the scatter of
any relation with _M_ ⋆ . We address the last issue in the following subsection.


_3.2.3_ _Disentangling_ _the_ _outflow_ _dependence_ _on_ _host_ _galaxy_
_parameters_


In the previous subsections we have shown how the outflow
rate depends on galaxy properties (for which sensitive CO
observations are available, such as stellar mass, star formation rate and the luminosity of the AGN. However, it is
difficult to isolate the role played by each of these quantities, especially given that they are correlated. In this section,
we attempt to disentangle the contribution of these different
factors.

For this purpose, we performed a regression as follows:


log( _M_ [�] outf ) = x log(αSFR+β _L_ AGN ) + y log _M_ ⋆, (4)


MNRAS **000**, 1–26 (2018)

_Cold_ _Molecular_ _Outflows_ _in_ _the_ _Local_ _Universe_ 11



1


0.8


0.6









0.4


0.2





0



1.14log(0.52 M [SFR] /yr [+ 0.51] 10 [43] L AGN erg/s [)] 0.41log( 10M [11] star M [)]


**Figure** **10.** Simultaneous multiple linear regression fit of the
molecular outflow rate as a function of star formation rate, stellar
mass and AGN luminosity, as given in equation 5. Colour-coding
and symbols are as in Fig. 2.


1



being ∆(x,α,β,y) = (0.12,0.19,0.25,0.25). The resulting relation is shown in Fig. 10. Clearly the large dispersion seen
in the previous plots (outflow rate vs _L_ AGN, vs SFR and vs
_M_ ⋆ separately) is greatly reduced in this relation, indicating that we are simultaneously capturing the contribution
of these three factors to the outflow rate. Very interestingly,
this relation enables us to disentangle (at least partly) the
contribution of the three factors to the outflow rate. The
dependence on stellar mass is now seen more clearly: the dependence has a power law index of –0.41, which is very close
to the value expected by theory of –0.5 for outflows driven by
star formation. As our sample also includes AGN-driven outflows, it is likely that these have mass-loading factors which
decrease with stellar mass, too. We cannot disentangle in
this kind of analysis the power-law index of the dependence
on AGN luminosity and SFR separately. With the functional
form adopted by us the combined dependence has a power
law index of 1.1, i.e. a nearly linear relation, as expected in
many models at least for the SFR.
However, this relation only accounts for the molecular
phase of the outflow. As discussed in Sect. 3.1, including the
atomic-neutral and ionized phases is difficult because we do
not have enough statistics in terms of galaxies which have
all three outflow phases measured. However, as mentioned
in Sect. 3.1, we can roughly account for these two phases
by including a factor of three for star forming galaxies (as
they have an ionized and atomic outflow rates that are similar to the molecular outflow rate) and a factor of two for
AGN-dominated galaxies (as they have an atomic outflow
rate similar to the molecular outflow rate and a negligible
contribution from the ionized outflow rate, at least in our
luminosity range). In this case the resulting best fit for the
_total_ outflow rate is given by









0.8


0.6


0.4


0.2


0



1.13log(1.29 M [SFR] /yr [+ 0.81] 10 [43] L AGN erg/s [)] 0.37log( 10M [11] star M [)]


**Figure** **11.** Simultaneous multiple linear regression fit of the _total_
outflow rate as a function of star formation rate, stellar mass
and AGN luminosity, as given in equation 6. Colour-coding and
symbols are as in Fig. 2.


and finding the values of the parameters that minimize the
dispersion around this relation. The reason for using this
expression, is that for starburst galaxies we only have an
upper limit on the AGN luminosity. Combining the SFR and
AGN in the term in parenthesis ensures that this term never
diverges to very negative values in log, i.e. it ensures that
when we investigate galaxies with outflow there is always a
driving mechanism, either SF or AGN. We have excluded our
candidate fossil outflows as they are expected not to follow
a relation with AGN or SFR, although AGN variability will
still be a source of scatter.

The resulting best fit is:



SFR
log( _M_ [�] outf (tot)/(M ⊙ yr [−][1] )) = 1.13 log 1.29
� M ⊙ yr [−][1]



_L_ AGN
+0.81
10 [43] erg s [−][1]



− 0.37 log _M_ ⋆
� � 10 [11] M ⊙



,
�



(6)



SFR
log( _M_ [�] outf (H 2 )/(M ⊙ yr [−][1] )) = 1.14 log 0.52
� M ⊙ yr [−][1]



with one standard deviation errors on the four parameters
being ∆(x,α,β,y) = (0.55,0.45,0.12,0.24). The resulting fit is
shown in Fig. 11, which has a scatter even smaller than in
Fig. 10.
These _global_ relations can be used to infer the expected
outflow rate in any kind of galaxies, and provide an appropriate comparison for the theoretical models and simulations.


_3.2.4_ _Dependence_ _on_ _L_ AGN _/L_ Edd


In the previous subsections we have investigated the dependence on nuclear activity in terms of AGN absolute luminosity. However, both in energy-driven outflows and radiation pressure-driven outflows (the two main mechanisms
proposed for AGN outflows) the most fundamental quantity is the AGN luminosity relative to the Eddington limit,
_L_ AGN / _L_ Edd . This quantity is more difficult to determine as
it requires an estimate of the black hole mass. The latter
has been inferred only for about half of the galaxies in our
sample with a variety of methods (primarily through virial
estimators) and subject to large uncertainties. The major
contribution to this uncertainty stems from the virial coefficient _f_, which shows a scatter of 0.44 (Woo et al. 2010). Fig.



_L_ AGN
+0.51
10 [43] erg s [−][1]



− 0.41 log _M_ ⋆
� � 10 [11] M ⊙



,
�



(5)



with one standard deviation errors on the four parameters


MNRAS **000**, 1–26 (2018)

12 _A_ _Fluetsch_ _et_ _al._



4


3


2


1


0













1


0.8


0.6


0.4


0.2


0


|Sy|Col2|Col3|
|---|---|---|
|add. outf. phases<br><br>LINER<br>HII|||



(b)



1


0.8


0.6


0.4


0.2


0



(a)



log(L AGN /L Edd )



6 7 8 9
log(M BH ) (M )



**Figure** **12.** Outflow rate as a function of Eddington ratio, i.e. L AGN /L Edd . Outflow rate a s function of black hole mass. Colour-coding
and symbols are as in Fig. 2.



12a shows the outflow rate as a function of Eddington ratio.
If one excludes SF-dominated galaxies, which are driven by
a different mechanism (see also discussion in the next sections), the plot shows some correlation between outflow rate
and Eddington ratio, although with a few points subject to
large scatter. Such a scatter could partly be accounted for
by the uncertainties in the black hole masses. Additional
discussion on this dependence will be given in Sect. 4.


_3.2.5_ _Dependence_ _on_ _black_ _hole_ _mass_


In Fig. 12b we also show the outflow rate as a function of
black hole mass. In principle one should not expect any correlation of the outflow rate with the black hole mass, but the
plot clearly shows a significant correlation. Such a correlation was already identified by Rupke et al. (2017), although
with lower statistics. One interpretation is that this correlation is simply a consequence of the correlation between outflow rate and stellar mass (Sect. 3.2.2), through the black
hole–galaxy mass relation. However, another possibility is
that the correlation between outflow rate and black hole
mass traces the average driving effect that the black hole
has during its intermitted accretion phases. Indeed, if one
assumes that the black hole accretes at a given Eddington
fraction _L_ AGN / _L_ Edd (e.g. at the average Eddington fraction
of the AGN population) and with an average duty cycle,
then the black hole mass may be a tracer of the average
AGN activity over the past ∼ 10 [6] − 10 [8] yr, i.e. on time-scales
closer to the outflow dynamical time-scale, hence resulting in
the observed correlation. We discuss the effects of the AGN
flickering further in the next sections.


_3.2.6_ _Dependence_ _on_ _radio_ _power_


Galactic outflows are seen to also be linked with the presence of radio jets. The connection appears to be common
for what concerns the ionized phase of outflows (Mullaney
et al. 2013). Furthermore, clear indications that some molecular and atomic outflows are associated with radio jets has
been found (e.g. Morganti et al. 2013, 2015; Dasyra et al.
2015, 2016). However, it is not yet clear how common this
association is among molecular outflows.



We have explored this connection in our sample by investigating the correlation of the outflow rate with the excess of radio power relative to the value expected from the
radio–SFR correlation, which is traced by the parameter
_q_ IR, defined as the ratio between the far-IR flux and the
monochromatic flux at 1.4 GHz (Sect. 2.4.6). Fig. 13 shows
the molecular outflow rate as a function of the parameter
_q_ IR . The vertical dashed line indicates the average value for
star forming galaxies, while the solid vertical line indicates
the limit below which galaxies are considered to have a significant radio excess associated with a radio jet (Ivison et al.
2010; Harrison et al. 2014).
Most galaxies in our sample are consistent with the radio luminosity being associated with star formation. Actually it seems that, on average, _q_ IR in our sample is even
higher than typically observed in normal galaxies, possibly
reflecting the bias towards star-bursting systems, or the contribution of powerful AGN to the infrared emission in some
of the galaxies of our sample.
The Fig. 13 shows that two of the three galaxies with radio excess ( _q_ IR _<_ 1.8) do have strong outflows. However, the
plot shows no clear correlation between molecular outflow
rate and excess of radio emission relative to the SFR-radio

relation. This finding suggests that, statistically, the presence of radio jets does not seem to be a primary driving
mechanism of the majority of galactic molecular outflows in
our sample. However, this does not imply that strong radio
jets cannot cause outflows. In fact, as already discussed at
the beginning of this section, radio jets have been seen as
the origin of powerful outflows in a few specific galaxies.


**3.3** **Depletion** **time**


In the following we estimate the outflow depletion timescale, defined as τ depl,outf = _M_ gas / _M_ [�] outf, i.e. the time required
to remove all gas from the galaxy with the current mass outflow rate assuming no fresh supply of additional gas is delivered to the galaxy. We first focus on the depletion time of
the molecular gas, i.e. τ depl,outf (H 2 ) = _M_ (H 2 )/ _M_ [�] outf (H 2 ), as we
have this information for all galaxies in the sample and we
will then discuss the total gas depletion time for galaxies that
have information on their HI content. In Fig. 14, we show the


MNRAS **000**, 1–26 (2018)

_Cold_ _Molecular_ _Outflows_ _in_ _the_ _Local_ _Universe_ 13





1


0.8


0.6


0.4


0.2


0



3


2


1


0



0 1 2 3 4













1


0.8


0.6


0.4


0.2


0



S IR
q IR log( S 1.4GHz [)]


**Figure** **13.** Molecular outflow rate as a function of the parameter
q IR defined as the ratio between the far-IR flux and the radio
monochromatic flux at 1.4 GHz (Sect. 2.4.6). The vertical dashed
line indicates the average value for star forming galaxies, while
the solid vertical line indicates the limit below which galaxies are
considered to have a significant radio excess associated with a
radio jet (Ivison et al. 2010; Harrison et al. 2014). Colour-coding
and symbols are as in Fig. 2.


1



11


10


9


8


7





**Figure** **15.** Molecular gas depletion time-scale due to outflows
vs depletion time-scale due to star formation. Colour-coding and
symbols are as in Fig. 2.



40 42 44 46
log(L AGN ) (erg/s)



1


0.8


0.6


0.4


0.2


0



9


8


7


6



40 42 44 46
log(L AGN ) (erg/s)



0.8


0.6


0.4


0.2


0



**Figure** **14.** Molecular gas depletion time-scale due to outflows as
a function of AGN luminosity. Colour-coding and symbols are as
in Fig. 2.


relation between molecular depletion time-scales and AGN
luminosity. While we do observe an anti-correlation between
depletion time-scales and AGN luminosity, and with AGN
contribution to the bolometric luminosity, the trend is much
more scattered than in previous studies (Sturm 2011; Cicone
et al. 2014). The depletion time-scale of molecular gas for the
most powerful AGN is between a few times 10 [6] and 10 [8] yr.
Fig. 15 shows the depletion time due to outflows compared to the depletion time-scale due to star formation. For
star-forming galaxies, the depletion time due to star formation is similar or shorter than the depletion time due to
outflowing gas. For AGN hosts, the depletion is dominated
by outflows rather than by gas consumption due to star formation, implying that AGN-driven outflows play a key role
in regulating star formation in galaxies.
For about half of the galaxies we also have information


MNRAS **000**, 1–26 (2018)



**Figure** **16.** Total gas (HI+H 2 ) depletion time-scale as a function
of AGN luminosity. Colour-coding and symbols are as in Fig. 2.


on the atomic gas content, hence we can estimate the total depletion time: τ depl (tot) = _M_ (H 2 + HI)/ _M_ [�] outf ( _H_ 2 ). This is
shown in Fig. 16, which illustrates that the total depletion
time-scale is much longer, and generally exceeding 10 [8] yr
even in most AGN (even if the other gas phases are included,
as shown by the black arrow), implying that the AGN is unlikely to clear the galaxy of its total gas content.
The combination of these various results indicates that

AGN-driven outflows are capable of clearing the central
parts of galaxies, where the gas content is dominated by
the molecular phase, but the AGN is unlikely to clear the
entire galaxy of its gas content.


**3.4** **Kinetic** **power**


It is important to investigate the properties of outflows such
as their kinetic power and momentum rate, as different models make different predictions for these quantities. In this
section we briefly discuss the observational results for what
concerns the kinetic power, in the next section we will discuss the momentum rate, while a detailed analysis of impli

14 _A_ _Fluetsch_ _et_ _al._













1


0.8



37


36


35


34


33





0.6


0.4


0.2



1


0.8


0.6


0.4


0.2


0







0



flow assuming a coupling efficiency of 100 per cent between the
outflow and the ISM. The prediction for momentum-driven outflows and some radiation pressure-driven outflows is shown as a
shaded region. The red dashed line shows the predicted relation
for the radiation pressure-driven outflow presented in Ishibashi
et al. (2018). Colour-coding and symbols are as in Fig. 2.



















41 42 43 44 45
log(P K, SF ) (erg/s)





**Figure** **18.** Kinetic power of the outflow as a function of the
kinetic power generated by supernovae, as inferred from the SFR.
The black dashed lines indicate coupling efficiencies of 1, 10 and
100 per cent. Colour-coding and symbols are as in Fig. 2.


cations and comparison with models will be given in Sect.

4.2.
Fig. 17 shows the kinetic power of the outflow (=0.5
_v_ [2] _M_ [�] outf ) as a function of the radiative power of the AGN.
Clearly, for AGN host galaxies the kinetic power correlates
with the AGN luminosity, although the correlation appears
to be superlinear. Moreover, our more extended, and less
biased sample, with respect to previous studies, reveals a
large scatter.
Star forming galaxies follow different relations compared to AGN, as expected since in these sources the observed outflows cannot have originated from a currently active AGN episode. To test whether star formation can explain why these galaxies are outliers, in Fig. 18 we compare



**Figure** **19.** Relation between outflow momentum rate
(v outf M [�] outf (H 2 )) and AGN radiative momentum rate (L AGN /c).
The theoretical predictions (v outf M [�] outf )/(L AGN /c) ∼ 20:1 (energydriven) and 1:1 (momentum-driven) are shown as a dashed
lines, respectively. Radiation pressure-driven outflows can reach
(v outf M [�] outf )/(L AGN /c) ∼ 5:1. Colour-coding and symbols are as in
Fig. 2.


the kinetic power of the outflow with the power expected to
be generated by supernovae ( _P_ K,SF = 7×10 [41] SFR (M ⊙ yr [−][1] )
(Veilleux et al. 2005). In star forming galaxies, especially
those with low values of _P_ K,SF, the kinetic power of the outflow can be explained by supernovae by assuming a coupling
efficiency of only 0.5% (except for a few SF galaxies with extreme outflows discussed further below). However, accounting for the contribution of the ionized and atomic phases
increases the kinetic power of SB-dominated outflows by a
factor of about three (Sect. 3.1), as indicated by the grey arrow, suggesting a coupling efficiency of supernova ejecta with
the ISM higher than 1%. Conversely, in AGN host galaxies a
coupling of ∼ 10 per cent or much more is needed; as this is
significantly larger than expected by models of SN outflows
(especially if accounting for the other outflow phases, as indicated with the black arrow), this indicates, as expected,
that SNe are not powerful enough to drive the outflow in
these objects and that the outflow must be mostly driven
by the AGN.
Fig. 17 and 18 also clearly indicate that there are a few
galaxies for which the kinetic power greatly exceeds what
expected from the AGN energy-driven scenario and also in
excess of what is expected by the SNe-driven scenario, as
a coupling efficiency higher than 10 per cent would be required. In these cases (objects marked by white dot in their
centre) the outflow is likely due to a past, more active phase
of the AGN. This will be discussed further in Sect. 4.3.



**3.5** **Momentum** **rate**


The outflow momentum rate is plotted as a function of the
AGN radiative momentum rate _L_ AGN / _c_ in Fig. 19, illustrating a good correlation of these two quantities for AGN host
galaxies, further indicating that AGN play a significant role
in driving galactic outflows. However, also in this case it is
clear that the scatter is significantly larger than in previous
studies.

Galaxies classified as star forming are all outliers in this


MNRAS **000**, 1–26 (2018)

_Cold_ _Molecular_ _Outflows_ _in_ _the_ _Local_ _Universe_ 15























**Figure** **20.** Dependence of the outflow momentum rate
(v outf M [�] outf ) on the total photon momentum output of the galaxy
(i.e. from AGN _and_ star formation). The top dashed line indicates
the 1:1 relation between momentum rate and bolometric luminos
ity, while lower dashed lines indicate lower ratios. Colour-coding
and symbols are as in Fig. 2.


relation since they are powered by a different mechanism (i.e.
SNe feedback and/or radiation pressure from the stellar UV
radiation field). In Fig. 20, we analyse the dependence of
outflow momentum rate on _total_ photon momentum rate
of the galaxy, _L_ bol / _c_ . For strong AGN hosts, _L_ bol ≈ _L_ AGN,
but for AGN with lower AGN contribution and star forming
galaxies, _L_ bol is much larger than _L_ AGN . In this plot it is
interesting to note that for some star forming galaxies, especially at high luminosities (i.e. high SFR) the momentum
rate is close to ∼ 0.5 _L_ bol / _c_, suggesting that radiation pressure on dusty clouds by the radiation field of young stars
can be an additional significant contributor to the driving
mechanism of outflow in starburst galaxies, as predicted by
some models (Thompson et al. 2015), although a coupling
efficiency of at least 50% would be required.
In some star forming galaxies the momentum rate of the
outflow is close or exceeding _L_ bol / _c_ (which would imply an
unrealistic coupling efficiency of 100% or higher), indicating
that other mechanisms or other phenomena may be at work.
This is also seen in some AGN: A few AGN hosts have out
flows which, when compared with _L_ AGN / _c_, are characterised
by momentum boosts well in excess of what expected by any
theory (see Fig. 19). As we will discuss later on, most of these
outflows with extreme momentum rates can be explained in
terms of fossil outflows resulting from a much stronger past
AGN activity.


**4** **DISCUSSION**


**4.1** **Driving** **mechanisms** **in** **AGN**


Three different mechanisms have been proposed for powering AGN-driven outflow: an energy conserving blast wave
(so-called energy-driven), a momentum conserving blast
wave (so-called momentum-driven), and direct radiation
pressure on to the dusty clouds of the galactic ISM (so-called
radiation pressure-driven). These are discussed in greater detail in the following.


MNRAS **000**, 1–26 (2018)



Many theoretical models expect that the most effective feedback process is obtained through AGN-driven outflows that are energy conserving (energy-driven), in which
a hot bubble composed of a thermalised nuclear wind has a
cooling time-scale much longer than the outflow expansion
time-scale. The outflow is accelerated due to the adiabatic
expansion of the hot bubble. In this scenario, the outflow kinetic energy is expected to be about 5 per cent of the AGN
radiative power, if the AGN is accreting close to the Eddington limit and if a 100 per cent thermal-to-kinetic conversion
efficiency and high gas covering fractions are assumed (i.e.
100% coupling between the blast wave and the ISM in the
host galaxy) (King 2010; Faucher-Giguere & Quataert 2012;
Zubovas & King 2012; Costa et al. 2014; King & Pounds
2015; Richings & Faucher-Gigu`ere 2018). Yet, more detailed
3D, non-spherically symmetric simulations have suggested
that the coupling can be significantly lower than 100 per
cent, with dense clumps of the ISM remaining unaffected
and the outflow escaping along the directions of least resistance (Bourne et al. 2014; Gabor & Bournaud 2014; Costa
et al. 2015; Bourne et al. 2015; Roos et al. 2015).
Momentum-driven outflows (in which the energy of the
shocked wind is quickly dissipated on small scales via radiation losses) are generally expected to be much less effective
in driving outflows and in this case the outflow kinetic energy is expected to be of the order of 0.1 per cent of the
AGN radiative luminosity, or less (King & Pounds 2015).
Momentum-driven outflows are also expected to be confined
within the central few 100 pc as most of their energy is
quickly dissipated.
An additional class of models suggests that direct radiation pressure of the UV, optical and IR photons on the
dusty clouds of the ISM can be effective enough to drive massive outflows (Fabian 2012; Thompson et al. 2015; Ishibashi
et al. 2017; Bieri et al. 2017; Costa et al. 2017; Ishibashi et al.
2018; Costa et al. 2018). In this case there is a broad range
of expected outflow properties. If the central dusty region in
which acceleration takes place is optically thick to IR radiation, then the kinetic power of the outflows can be as high as
∼ 1 per cent of the AGN luminosity (this applies also when
the source of radiation is a compact starburst); however, in
less extreme cases the outflow kinetic power is expected to be
lower than this value. Recently, Ishibashi et al. (2018) developed the model of radiation pressure-driven outflows further.
The predict a super-linear relation between outflow kinetic
power and AGN luminosity in the form _P_ K,outf ∝ _L_ AGN [3][/][2] [.]
By looking at the results reported in Sect. 3.4 and Fig.
17, where the prediction of different models are also shown,
it is clear that outflows in AGN host galaxies span a broad
range of properties. Although AGN ‘flickering’ can account
for some of the scatter, as discussed in the next section,
the very broad range of _P_ K,outf / _L_ AGN suggests that these
outflows are driven by a combination of different driving
mechanisms and/or a broad range of coupling efficiencies
with the ISM. Some AGN are consistent with the energydriven scenario, and full coupling of the outflow with the
ISM. However, the majority of AGN are significantly below
the _P_ K = 0.05 _L_ AGN relation (which assumes all thermal energy of the putative expanding hot bubble is converted into
kinetic energy of the outflow) and so the respective outflows
are more consistent with a momentum-driven or radiation

pressure-driven mechanism; alternatively they are energy

16 _A_ _Fluetsch_ _et_ _al._


driven, but poorly coupled with the galaxy ISM. However,
the momentum-driven scenario can probably be excluded
as the observed outflows are mostly on kpc-scales, while
momentum-driven outflows should be confined within the
central few 100 pc (King & Pounds 2015).
As shown in Fig. 17, at high AGN luminosities, galaxies
lie closer to the expected value for the energy-driven mode
though still mostly below the value expected from energydriven outflows. This seems to indicate that different driving
mechanisms may be at work at different luminosities. Specifically, at high luminosities energy-driven outflows (though
with poor coupling) may dominate, while at low luminosities
radiation pressure may be the dominant mechanism driving
outflows.
The super-linear relation between outflow kinetic power
and AGN luminosity in the form _P_ K,outf ∝ _L_ AGN [3][/][2] [expected]
by the radiation pressure model of Ishibashi et al. (2018)
(dashed orange line in Fig.17) is consistent with the observed relation in terms of slope. Therefore, this model can
potentially account also for the high _P_ K,outf / _L_ AGN values
(∼1 per cent) observed at the highest luminosities, and the
decreasing values of this ratio at lower luminosities. However, the �model also expects the outflow rate to follow a
relation _M_ outf ∝ _L_ AGN [1][/][2] [,] [which] [is] [somewhat] [shallower] [than]
what we observe for molecular gas (see Fig. 7).
In terms of momentum rate, in the energy-driven case
models expect that the momentum rate is boosted to about
15-20 _L_ AGN / _c_ (Faucher-Giguere & Quataert 2012; Zubovas
& King 2012). Momentum-driven winds are expected to result in momentum rates of ∼ _L_ AGN / _c_ (King 2010). Direct
acceleration of the ISM through the action of radiation pressure on dusty clouds generates momentum rates ranging
from ∼ 1 up to 5 _L_ AGN / _c_, the latter in the case that the
medium that is being accelerated is optically thick to infrared radiation, resulting in multiple scattering that boosts
the momentum rate (Ishibashi & Fabian 2015; Thompson
et al. 2015; Bieri et al. 2017; Costa et al. 2018; Ishibashi
et al. 2018).
In Fig. 19 the upper dashed line represents the theoretical prediction for the energy-driven model (with 100 per cent
coupling), while the lower dashed lines indicate the values
expected for the momentum-driven and radiation pressuredriven models. Some of the galaxies with an AGN do follow
the theoretical prediction for energy-driven outflows within
the errors, but most galaxies hosting an AGN have momentum rates scattered between the energy-driven case and the
momentum/radiation pressure-driven cases, further suggesting the contribution of different driving mechanisms and/or
energy-driven outflows with poor coupling.
An additional route to study the driving mechanism is
to investigate the relation between outflow rate, AGN luminosity and gas column density of the circumnuclear gas.
Indeed, in the context of radiation pressure-driven outflows,
the effective Eddington luminosity is dominated by radiation pressure on dust, which drastically reduces the Eddington limit. Fabian et al. (2008) and Ricci et al. (2017) have
pointed out that the effective Eddington limit ( _L_ Edd,eff ) is
higher at higher gas column densities as larger amounts of
material need to be pushed out. Hence, these authors expect a region in the _L_ AGN / _L_ Edd vs _N_ H plane where radiation pressure on dust dominates over gravity and where this
kind of outflows should be most effective. This is explored


|Sy<br>LINER<br>HII|Col2|
|---|---|
|||



**Figure** **21.** Gaseous column density along our line of sight, as inferred from X-ray spectra, versus L AGN /L Edd, with symbols colourcoded by outflow rate (right hand-side colour bar). The solid line
delimitates the area (non-shaded) where radiation pressure on
dust is expected to overcome gravity (i.e. where the effective Eddington luminosity for a dusty medium is exceeded) hence producing powerful outflows. Symbols are as in Fig. 2.


in Fig. 21, where the column density (as inferred from Xray observations) is shown as a function of the Eddington
ratio, _L_ AGN / _L_ Edd, and colour coding is according to the outflow rate. The region on the right hand-side of the plot,
delimited by the solid line, is where the effective Eddington
luminosity for a dusty medium is exceeded, and therefore
where we expect powerful outflows that are driven by radiation pressure on dust. As pointed out by Fabian et al.
(2008) and Ricci et al. (2017), this region is underpopulated,
indeed empirically confirming that the effective Eddington
ratio is exceeded in this region. The few galaxies of our sample located in this region do indeed show among the highest
outflow rates, suggesting that indeed these extreme outflows
may be driven by radiation pressure on dust. We note that
in the scenario discussed by Fabian et al. (2008) and Ricci
et al. (2017) AGN with _N_ H < 10 [22] _cm_ [−][2] are not considered,
as these low column densities are thought to be associated
with dust lanes in the host galaxy and not directly linked
with the AGN process; however, our analysis shows that
the three objects in this region are characterized by strong
outflows, suggesting that also in these cases the outflow is
driven by radiation pressure on dust. For the other galaxies,
located on the left-side of the solid line (shaded are) there is
not much correlation between the outflow rate and their location on the diagram, in particular there are galaxies with
high outflow rates also below the boundary expected by the
model. These outflows could be driven by a different mech
anism.

To summarise, our results indicate that AGN-driven
outflows are either consistent with predictions from direct
radiation pressure models or with the energy-conserving
blast-wave scenario, but with a coupling with the ISM of
the host galaxy that varies from galaxy to galaxy and generally is lower than 100%.


MNRAS **000**, 1–26 (2018)



26


25


24


23


22


21


20



4 2 0
log(L AGN /L Edd )



2.5


2.0


1.5


1.0


0.5


0.0

_Cold_ _Molecular_ _Outflows_ _in_ _the_ _Local_ _Universe_ 17



**4.2** **Driving** **mechanisms** **in** **star** **forming** **galaxies**


As discussed in Sect. 3.4 only about ∼1–2 per cent of the
kinetic power released by SNe appear to be converted into
outflow kinetic power. A low coupling efficiency of the kinetic
energy between supernova ejecta and ISM is expected by
the fact that most of the energy is radiated away in the
dense interstellar medium in which most SNe are expected
to explode. Yet, models and simulations expect still higher
coupling efficiencies, of the order of 5 per cent (Walch &
Naab 2015). Although, there is some tension this is actually
within the errors; however, if confirmed with more accurate
data it may indicate that radiation losses during the SN-ISM
interaction are higher than expected (possibly because the
ISM is denser than assumed in the simulations).
However, in addition to the kinetic power injected by
SNe, outflows in star forming galaxies can also be driven by
radiation pressure onto the dusty clouds (Thompson et al.
2005, 2015). The correlation in Fig. 20 between outflow momentum rate and radiative momentum from the bolometric

luminosity of star forming galaxies suggests indeed that radiation pressure may play a role. However, one should also
be aware that such a correlation is also degenerate with the
kinetic power injected by SNe, since the SN rate is linked
to the SFR which is in turn related to the bolometric lu
minosity. Moreover, it is important to note that most star
forming galaxies have a ratio between momentum rate and
radiation momentum is between 0.5 and 0.1 (Fig. 20), implying that, if this driving process is at work, the coupling
efficiency must be less than 50 per cent.


**4.3** **Fossil** **Outflows**


There are a few galaxies with outflows that are characterised
by anomalously high kinetic power and momentum rates
compared to their AGN luminosity and SFR, which are difficult to explain with any driving mechanism. More specifically, Fig. 17 and 18 indicate that for some galaxies (marked
with a white dot in these and other figures) the kinetic power
is greatly in excess of what is expected even from the AGN
energy-driven scenario, even assuming 100 per cent coupling,
and is also in excess of what is expected by the SNe-driven
scenario, unless assuming an unrealistically high coupling
efficiency of the SNe (larger than 10 per cent, especially if
accounting for all outflow phases). In Fig. 19 it is clear that
these objects have also very high momentum rate, even in
excess of what expected in the case of energy-driven outflows and 100 per cent coupling. It is unlikely that in these
objects the SFR or AGN power are not estimated properly,
as the observational constraints are quite good. It is also
unlikely that these outflows are driven by a radio-jet, as
these objects do not show any radio excess in Fig. 13. In
these cases, as already hinted in the previous sections, the
most likely explanation is that we are observing ‘fossil’ outflows that outlast a past powerful AGN activity, which has
recently faded. This interpretation is further supported by
the low Eddington ratios (log( _L_ AGN / _L_ Edd ) ≲ -3) seen in the
three fossil outflow objects for which a black hole estimate
is available.

Fossil outflows are expected from theory in large numbers. It has been shown that outflows can remain visible for
a time about 10 times longer than the driving phases and


MNRAS **000**, 1–26 (2018)



up to 10 [8] yr (King et al. 2011). Theoretical considerations
have suggested that in M82 a powerful AGN might have
been present until about 17 Myr ago and may have been responsible for driving the outflow currently observed (Zubovas 2015). Even more simply, without invoking detailed and
extensive theoretical simulations, the dynamical time-scales
of the outflows ( _t_ dyn ∼ _R_ /v) are in the range of 10 [6] -10 [8] yr,
while we know that AGN have a ‘flickering’ time-scale ranging from a few years (e.g. Gilli et al. 2000) up to 10 [5] yr
(Schawinski et al. 2015; King & Nixon 2015). Therefore, a
large number of fossil AGN is naturally expected. The outliers we see here are possible manifestations of this scenario
and are likely the tip of the iceberg of a much larger population of fossil outflows. If this is true, then one should
be careful when comparing observational outflow properties
with theoretical models as possibly a large fraction of galaxies (in our sample 10 - 20 per cent) display fossil outflows.
The reason why in the past such fossil outflows had
not been identified is likely because previous observations
had targeted primarily known, strong AGN hence biasing
the sample towards outflows that are in the phase of being
powered. Instead, in our study we have collected data of
galaxies from the ALMA archive, many of which had been
observed independently of their activity, hence reducing such
biases.

Table 3 gives the list of fossil outflows identified by us.
Their properties have no peculiarities relative to other galaxies in the sample.


**4.4** **Do** **Outflows** **Escape** **the** **Galaxy** **and** **the** **Halo?**


If outflow velocities are high enough to escape the potential of the galaxy (and possibly even the halo), then these
outflows can effectively clear the galaxy of its gas content.
It also depends on how much gas the outflows sweep up as
they move out of the galaxy and on whether they collide
with inflowing material. We ignore the latter effects here,
because, as it turns out, most outflowing material should
not escape the galactic halo purely due to its insufficient
velocity. Mass-loading and a potential interaction with gas
infall would only strengthen our conclusions.
In principle one should use the velocity rotation curve
of galaxies to infer the mass distribution radial profile of the
associated gravitational potential. Unfortunately, at the moment, this information is not available for the vast majority
of the galaxies in our sample. Information on the rotation
curve is available only for very few galaxies, primarily from
the CO interferometric data, and only in the central region
of the galaxy. As a consequence, we have to rely on some
simple assumptions and use scaling relations with the stellar mass.

We consider the stellar mass as determined in Sect. 2.4.
We use the relation by McIntosh et al. (2005) at _z_ = 0 to
relate the stellar mass to the half-light radius _r_ 50 :


log(¯ _r_ 50 /h [−][1] kpc) = 0.56 log ( _M_ ⋆ h [2] /M ⊙ ) − 5.52. (7)


We approximate the stellar mass distribution adopting a
Hernquist profile (Hernquist 1990) for the density


_a_ 1

ρ( _r_ ) = _[M]_ (8)

2π _r_ ( _r_ + _a_ ) [3]

18 _A_ _Fluetsch_ _et_ _al._


where _a_ is related to the effective radius _r_ eff via _r_ eff ≈ 1.8135 _a_ .
We can now compute the escape velocity for galaxies in our
sample. The escape velocity is given by





10 [0]


10 1


10 2



v esc = ~~�~~ 2|Φ( _r_ )| =



2 _GM_

(9)

~~�~~ _r_ + _a_ [.]



The escape fraction is then defined as the fraction of the
outflow that has a velocity higher than the escape velocity.
Unfortunately this calculation can be done only for those
outflows for which we have the data in electronic form, as it
requires estimating the integral of the fraction of the broad
wings with velocity higher than the escape velocity (i.e. this
calculation cannot be done for the data in the literature for
which an electronic version of the spectrum is not available).
This part of the outflow will eventually leave the galaxy. In
Fig. 22, the escape fraction is shown for the galaxies as a
function of the AGN luminosity. Only in IRAS 20100-4156,
and maybe in 4C 12.50, 10 per cent or more of the gas in the
outflow will escape the galaxy using these simple assumptions. For all other galaxies, the escape fraction is smaller
or negligible and there is no clear dependence on AGN luminosity. We should note, however, that the equations here
only hold if we consider ballistic motions. If the outflows are
still driven and therefore further accelerated, they are more
likely to escape the galaxy potential. The error in the escape
fraction is as large as 50 per cent as inferred by running a
Monte Carlo simulation, taking into account errors in fitting
the line profile, stellar mass and outflow radius.
Therefore, despite galactic outflows being very massive
and energetic, especially those driven by AGN, most of the
expelled gas will quickly re-accrete onto the galaxy and be
available again for star formation. Hence, the ejection of gas,
at least in this molecular phase, does not really contribute
to the global quenching of star formation in galaxies. However, these outflows can still have a dramatic effect in the
central region of galaxies (especially in the bulge region),
where they can locally suppress or even quench star formation. Moreover, even if the ejective aspect of outflows does
not directly contribute to the global quenching of galaxies
on large galactic scales, this does not mean that outflows do
not play a role at all on the global evolution of galaxies on
large scales. By injecting energy, outflows can keep the halo
gas hot and prevent it from cooling onto the galaxy, hence
effectively resulting into a delayed quenching of star formation in the galaxy as a consequence of starvation (e.g. Gilli
et al. 2017; Costa et al. 2017). The escape fractions inferred
above are for molecular outflows. Ionized outflows, although
generally contributing much less to the outflow rate, are expected to have higher escape fractions (Costa et al. 2015).
This can be investigated for several galaxies whose outflow
has been mapped in the ionized phase, but we defer this
kind of analysis to a later paper.
We note that the escape fraction discussed above refers
to the escape velocity from the galaxy. The escape fraction
from the galaxy dark matter halo are even smaller, but also
more difficult to compute. We can attempt to estimate the
velocities needed to escape the halo by making a few approximations in the following.
We use the Navarro-Frenk-White (NFW) profile
(Navarro et al. 1995) to describe the density in the halo



This allows us to compute the escape fractions of gas out
of the halo. As expected, we generally obtain escape fractions from the halo even much smaller than the escape fractions from the galaxy, typically much smaller than 1 per
cent, further indicating that the bulk of the outflowing gas
will remain in the gravitational potential of the system and
will eventually re-accrete onto the galaxy. We note, however, that our sample does not include low mass galaxies
( _M_ ⋆ < 10 [10] _M_ ⊙ ), for which models expect a large fraction of
the outflowing gas to leave the galaxy and its halo, hence enriching the IGM. Detailed observations targeting this class
of galaxies are needed in order to test these expectations.


**4.5** **Effectiveness** **of** **AGN** **driven** **outflows** **in**
**quenching** **star** **formation**


AGN-driven outflows have been claimed to be one of the
primary candidates for cleaning galaxies of their gas content
hence quenching star formation and transforming them into
passive systems. The “blast-wave” energy-conserving mode,
with 100 per cent coupling with the ISM, has generally been
regarded as the most effective mode to remove galaxies of
their gas content (Zubovas & King 2012). We have, however,
obtained various results indicating that such“ejective”mode


MNRAS **000**, 1–26 (2018)



10 3

40 42 44 46
log(L AGN ) (erg/s)



1


0.8


0.6


0.4


0.2


0



**Figure** **22.** Fraction of the molecular outflow that escapes the
galaxy as a function of AGN luminosity. The two data points
with a black contour are taken from the literature and use slightly
different definitions of escape velocity.


of the galaxy:


ρ crit δ c
ρ( _r_ ) = (10)
_r_ / _r_ s (1 + _r_ / _r_ s ) [2]


where ρ crit = 3 _H_ [2] /8πG is the critical density and _r_ s = _r_ 200 /c
is the characteristic radius (c being the concentration parameter). The mass of the halo ( _M_ 200 ) can be inferred from
the stellar mass using a stellar mass-halo mass relation from
abundance matching (Moster et al. 2013). To find the mass
concentration from the halo mass, we use the relation by
Duffy et al. (2008) at _z_ = 0:


log _c_ 200 = 0.76 − 0.1 log _M_ 200 . (11)


As in Sect. 4.4, the escape velocity is:



v esc = �2|Φ( _r_ )| =



2 _M_ 200 _G_ (12)
� _r_ (ln(1 + c) − c/(1 + c) [ln(1 +] _[ r]_ [/] _[r]_ [s] [))]

_Cold_ _Molecular_ _Outflows_ _in_ _the_ _Local_ _Universe_ 19



is probably not effective in clearing the whole galaxy of its
gas content, even at high luminosities. Indeed, most observational properties of the AGN-driven outflows are below
the expectations from energy-conserving mode, suggesting
either poor coupling efficiency (as suggested by some models and numerical simulations, e.g. Gabor & Bournaud 2014;
Costa et al. 2015; Richings & Faucher-Gig`uere 2017) or that
other driving mechanisms, such as direct radiation pressure
onto the ISM dusty clouds, are also at work (Thompson
et al. 2015; Costa et al. 2017; Ishibashi et al. 2018). We have
shown that the outflow depletion time-scales for the total
gas mass are very long, beyond the typical lifetime of AGN,
hence these outflows are unlikely to expel the whole amount
of gas in the galaxy. Finally, as illustrated in the previous
section, only a small fraction of the outflowing gas actually
escapes the galaxy (and even less the halo), hence most of
the expelled gas re-accretes on the galaxy to fuel star for
mation.

Although, the AGN “ejective” mode does not seem capable of quenching the entire galaxy, it can likely clean and
quench the central region. Indeed, the outflow depletion time
associated with the (mostly centrally concentrated) molecular gas is much shorter (∼ 10 [7] yr), especially in luminous
AGN. Therefore, the ejective AGN mode (especially when
occurring at high redshift) may actually be a important
route for quenching star formation in the bulge region.
The AGN driven outflow may also have an additional
indirect effect on larger scales. Although the ejective mode
is likely confined to the central regions, the energy injected
by the outflow into the halo can contribute to keep it hot,
hence preventing further gas accretion onto the galaxy and
therefore resulting in a “delayed” quenching, by starvation,
once star formation has used up the gas available in the disc
(Costa et al. 2015, 2017). This “preventive”, delayed mode
is supported by various statistical properties of the local
population of galaxies (Peng et al. 2015; Woo et al. 2017;
Cresci & Maiolino 2018).


**5** **CONCLUSIONS**


In this work, we have quantified the energetics of molecular outflows in a sample of 45 local ( _z_ _<_ 0.2) galaxies including AGN host galaxies as well as star forming/starburst
galaxies. The sample spans a range in AGN luminosity from
log( _L_ AGN ) ∼ 41 up to ∼ 46 erg s [−][1] and in star formation rate
from ∼ 0.1 up to several 100 M ⊙ yr [−][1] . Molecular outflow
properties are inferred from interferometric observations of
low- _J_ CO lines (apart from four galaxies, for which OH absorption from Herschel is used). We collect data of molecular
outflows from the literature and recalculate outflow and host
galaxy properties in a consistent manner. Furthermore, we
also analyse all public ALMA archival data of low- _J_ (1-0,
2-1 and 3-2) CO lines in local galaxies and look for signatures of outflowing gas. This is the largest sample to date
for which molecular outflows in CO have been investigated,
and includes also less powerful outflows than previous studies. Our sample improves with respect to previous studies
not only in terms of statistics but also by reducing the bias
favouring very active galaxies which have been preferentially
targeted in the past.
Our main findings can be summarised as follows:


MNRAS **000**, 1–26 (2018)




 - For about 30 per cent of the galaxies we could also obtain information on the ionized outflow, while for 18 per cent
of the sample we have also information on the neutral outflow. We find that in starburst galaxies the ionized outflow
is about as massive as the molecular outflow. In AGN the
ionized outflows is generally negligible comparable to the
molecular outflow and we find that the molecular-to-ionized
outflow rate increases with AGN luminosity. The amount of
gas in the atomic neutral phase has a large scatter, but in
general is comparable to the molecular phase.

 - The molecular mass-loading factor (η = _M_ [�] outf (H 2 )/SFR)
for star forming galaxies is consistent with unity, as expected
by models of star formation feedback.

 - The molecular mass-loading factor is higher in AGN
host galaxies compared to star forming galaxies, although a
significant boost (with η _>_ 10) is only seen in galaxies in
which the AGN luminosity is high relative to the bolometric
luminosity ( _L_ AGN / _L_ bol _>_ 0.7).

 - In AGN the outflow rate correlates with the AGN luminosity and with the Eddington ratio, _L_ AGN / _L_ Edd, although
with large scatter, further indicating that the AGN plays a
role in driving outflows. We also observe a correlation with
the black hole mass, which can be seen as tracing a link
between the outflow (which has a dynamical time-scale of
10 [6] − 10 [8] yr, much longer than the AGN flickering timescale) with the integrated, average past activity of the black
hole.


 - We highlight that the dependence of the outflow properties on AGN luminosity, star formation rate and galaxy
stellar mass, makes it difficult to isolate the individual dependences, as each these properties are can be mutually correlated in galaxies. Therefore, we have derived a relation of
the outflow rate simultaneously fitting the dependence of
AGN luminosity, SFR and stellar mass. The resulting fit is
much tighter than the individual relations and enables us to
disentangle, at least partially, the individual dependences.
In particular, we obtain a scaling of the outflow rate on stellar mass as ∝ _M_ ⋆ [−][0][.][41], which is very close to the dependence
expected by models of outflows driven by SNe and stellar
winds. We also suggest that the inferred empirical (fourdimensional) relation between outflow rate, _L_ AGN, SFR and
_M_ ⋆ can be very efficiently used to predict the strength of
outflows in a variety of galaxies and for comparison with
models.


 - We find that the majority of the molecular outflows
studied here show no excess of radio emission relative to the

SFR-radio relation. In addition, there is no correlation between molecular outflow rate and infrared-to-radio luminosity ratio, indicating that the majority of molecular outflows
are not driven by radio jets, at least within the luminosity
range probed by us. However, this does not exclude that
radio jet may have an important role in driving molecular
outflows in a few specific galaxies, as indeed observed.

 - The depletion time-scale associated with outflow (i.e.
τ depl = _M_ gas / _M_ [�] outf ) anti-correlates with AGN luminosity, i.e.
is shorter in more luminous AGN. The depletion time-scale
for molecular gas (τ depl,outf (H 2 )= _M_ (H 2 )/ _M_ [�] outf (H 2 )) can be as
short as a few, or a few tens million years, much shorter than
the depletion time-scale associated with star formation only.
However, when considering also the atomic component, the
depletion time-scale for the total gas content (τ depl,outf (tot)=
_M_ (H 2 + HI)/ _M_ [�] outf (H 2 )) is typically of the order, or longer

20 _A_ _Fluetsch_ _et_ _al._


than 10 [8] yr, i.e. longer than the typical AGN lifetime. This
indicates that the AGN-driven outflow is generally capable
of quickly removing the gas from the central regions (which
are dominated by the molecular phase), but unlikely to clean
the entire galaxy from its gas content.


 - For AGN host galaxies the outflow kinetic power
_P_ K,outf (H 2 ) shows a much larger scatter than in previous
studies and spans from 0.1 to 5 per cent of _L_ AGN . The ratio
_P_ K,outf (H 2 )/ _L_ AGN increases with luminosity. The momentum
rate spans from 1 to 30 times _L_ AGN / _c_ . These results suggest
that the AGN driven outflows can be both energy-driven
(with a broad range of coupling efficiencies with the ISM)
and radiation pressure-driven.


 - We estimate that the fraction of outflowing gas with
a high enough velocity to escape the galaxy and the dark
matter halo is less than 5 per cent, indicating that, although
outflows can remove gas from the central region, most of the
gas re-accretes onto the galaxy.


 - The results on the kinetic power, on the momentum
rate, on the depletion time-scale and on the fraction of escaping case, considered all together, indicate that the AGN
“ejective mode” is unlikely to be effective in cleaning the
galaxy of its gas content, at least in the mass range probed
by us (> 10 [10] M ⊙ ). However, AGN outflows are likely capable of cleaning the gas content, hence quench star formation, in the central (bulge) region. Moreover, AGN-driven
outflows can inject energy into the halo hence keeping it hot
and preventing further gas accretion, therefore resulting in
a delayed feedback that quenches the galaxy through starvation (Peng et al. 2015; Woo et al. 2017).


 - In star forming galaxies the kinetic power is only 1–
2 per cent of the kinetic power generated by supernovae,
indicating very fast cooling of supernova ejecta in the dense
ISM in which they explode, hence poor efficiency in driving outflows, as expected by some models. In star forming
galaxies the momentum rate of outflows correlates with the
bolometric luminosity, and it is about 0.3 _L_ bol / _c_, suggesting
that radiation pressure can also contribute to drive outflows
in star forming galaxies.


 - We also identify about 10 per cent of the galaxies whose
outflow significantly exceeds the maximum theoretical values of kinetic power and momentum rate expected for both
AGN and SB-driven cases. Our proposed explanation is that
these are ‘fossil outflows’ resulting from activity of a past
strong AGN, which has now faded. Theoretical models expects such fossil outflows to be present in large numbers,
also simply based on the fact that the outflows dynamical
time-scales is of the order of 10 [6] − 10 [8] yr while the AGN
has a much shorter variability (1 − 10 [6] yr). Previous outflow
surveys have not identified such fossil outflows because they
may have been biased towards powerful AGN and powerful
starburst galaxies in order to maximise the probability of detecting outflows. Our sample is less biased in this sense (as it
includes galaxies that were not selected specifically with the
goal of detecting outflows), which has enabled us to detect
this phenomenon. However, our sample is still biased, hence
the fraction of fossil outflow found by us is probably still the
tip of the iceberg of a larger population.



**ACKNOWLEDGEMENTS**


We thank Fabrizio Fiore and Kastytis Zubovas for their
detailed comments on the draft.

RM and SC acknowledge support by the Science and
Technology Facilities Council (STFC). RM and AF acknowledge ERC Advanced Grant 695671 ”QUENCH”. CC
acknowledges funding from the European Union’s Horizon
2020 research and innovation programme under the Marie
Sklodowska-Curie grant agreement No 664931. ACF and
WI acknowledge ERC Advanced Grant 3409442 ”FEEDBACK”. MAB acknowledges support by the ERC starting
grant 638707 ”BHs and their host galaxies: co-evolution
across cosmic time”. This paper makes use of the following ALMA data: ADS/JAO.ALMA#2013.1.00659.S,
ADS/JAO.ALMA#2012.1.00377.S,
ADS/JAO.ALMA#2012.1. 00611,
ADS/JAO.ALMA#2015.1.00102.S, ADS/JAO.ALMA#
2015.1.00263.S, ADS/JAO.ALMA#2013.1.00379.S,
ADS/JAO. ALMA# 2012.1.00539, ADS/JAO. ALMA#
2016.1.01279.S.
This research has made use of the NASA/ IPAC Infrared
Science Archive, which is operated by the Jet Propulsion
Laboratory, California Institute of Technology, under
contract with the National Aeronautics and Space Administration. This publication makes use of data products
from the Two Micron All Sky Survey, which is a joint
project of the University of Massachusetts and the Infrared
Processing and Analysis Center/California Institute of
Technology, funded by the National Aeronautics and Space
Administration and the National Science Foundation.


**REFERENCES**


Aalto S., Muller S., Sakamoto K., Gallagher J., Mart´ın S.,
Costagliola F., 2012, A [&](http://dx.doi.org/10.1051/0004-6361/201118052) A, 546, A68
Aalto S., et al., 2015, A [&](http://dx.doi.org/10.1051/0004-6361/201423987) A, 574, A85
Alonso-Herrero A., Engelbracht C. W., Rieke M. J., Rieke G. H.,
Quillen A. C., 2001, [ApJ,](http://dx.doi.org/10.1086/318282) 546, 952
Armus L., et al., 2004, [ApJS,](http://dx.doi.org/10.1086/422915) 154, 178
Arribas S., Colina L., Bellocchi E., Maiolino R., Villar-Mart´ın M.,
2014, A [&](http://dx.doi.org/10.1051/0004-6361/201323324) A, 568, A14
Baan W. a., Salzer J. J., LeWinter R. D., 1998, [ApJ,](http://dx.doi.org/10.1086/306504) 509, 633
Beckmann R. S., et al., 2017, [MNRAS,](http://dx.doi.org/10.1093/mnras/stx1831) 472, 949
Belfiore F., et al., 2016, [MNRAS,](http://dx.doi.org/10.1093/mnras/stw1234) 461, 3111
Bell E. F., de Jong R. S., 2001, [ApJ,](http://dx.doi.org/10.1086/319728) 550, 212
[Bell E. F., McIntosh D. H., Katz N., Weinberg M. D., 2003, ApJS,](http://dx.doi.org/10.1086/378847)
149, 289
Bellocchi E., Arribas S., Colina L., Miralles-Caballero D., 2013,

A [&](http://dx.doi.org/10.1051/0004-6361/201221019) A, 557, A59
Best P. N., Kauffmann G., Heckman T. M., Ivezi´c Z., [ˇ] 2005, [MN-](http://dx.doi.org/10.1111/j.1365-2966.2005.09283.x)
[RAS,](http://dx.doi.org/10.1111/j.1365-2966.2005.09283.x) 362, 9
Bieri R., Dubois Y., Rosdahl J., Wagner A., Silk J., Mamon G. A.,
2017, [MNRAS,](http://dx.doi.org/10.1093/mnras/stw2380) 464, 1854
Bischetti M., et al., 2017, A [&](http://dx.doi.org/10.1051/0004-6361/201629301) A, 598, A122
Bolatto A. D., Wolfire M., Leroy A. K., 2013, [ARA&A,](http://dx.doi.org/10.1146/annurev-astro-082812-140944) 51, 207
Bourne M. A., Nayakshin S., Hobbs A., 2014, [MNRAS,](http://dx.doi.org/10.1093/mnras/stu747) 441, 3055
Bourne M. A., Zubovas K., Nayakshin S., 2015, [MNRAS,](http://dx.doi.org/10.1093/mnras/stv1730) 453,

1829

Brightman M., Nandra K., 2011, [MNRAS,](http://dx.doi.org/10.1111/j.1365-2966.2011.18612.x) 414, 3084
Brusa M., et al., 2018, A [&](http://dx.doi.org/10.1051/0004-6361/201731641) A, 612, A29
Cano-Diaz M., et al., 2012, A [&](http://dx.doi.org/10.1051/0004-6361/201118358) A, 537, L8
Carniani S., et al., 2015, A [&](http://dx.doi.org/10.1051/0004-6361/201526557) A, 580, A102
Carniani S., et al., 2016, A [&](http://dx.doi.org/10.1051/0004-6361/201528037) A, 591, A28


MNRAS **000**, 1–26 (2018)

_Cold_ _Molecular_ _Outflows_ _in_ _the_ _Local_ _Universe_ 21



Carniani S., et al., 2017, A [&](http://dx.doi.org/10.1051/0004-6361/201730672) A, 605, A105
Cazzoli S., Arribas S., Maiolino R., Colina L., 2016, A [&](http://dx.doi.org/10.1051/0004-6361/201526788) A, 590,
A125

Chisholm J., Tremonti C. A., Leitherer C., Chen Y., 2017, [MN-](http://dx.doi.org/10.1093/mnras/stx1164)
[RAS,](http://dx.doi.org/10.1093/mnras/stx1164) 469, 4831
Cicone C., Feruglio C., Maiolino R., Fiore F., Piconcelli E., Menci
N., Aussel H., Sturm E., 2012, A [&](http://dx.doi.org/10.1051/0004-6361/201218793) A, 543, A99
Cicone C., et al., 2014, A [&](http://dx.doi.org/10.1051/0004-6361/201322464) A, 562, A21
Cicone C., et al., 2015, A [&](http://dx.doi.org/10.1051/0004-6361/201424980) A, 574, A14
Cicone C., Brusa M., Ramos Almeida C., Cresci G., Husemann
B., Mainieri V., 2018a, Nat. [Astron.,](http://dx.doi.org/10.1038/s41550-018-0406-3) 2, 176
Cicone C., et al., 2018b, [ApJ,](http://dx.doi.org/10.3847/1538-4357/aad32a) 863, 143
Combes F., et al., 2013, A [&](http://dx.doi.org/10.1051/0004-6361/201322288) A, 558, A124
Costa T., Sijacki D., Haehnelt M. G., 2014, [MNRAS,](http://dx.doi.org/10.1093/mnras/stu1632) 444, 2355
Costa T., Sijacki D., Haehnelt M. G., 2015, [MNRAS](http://dx.doi.org/10.1093/mnrasl/slu193) Lett., 448,

L30

Costa T., Rosdahl J., Sijacki D., Haehnelt M., 2017, preprint
( `[arXiv:1709.08638](http://arxiv.org/abs/1709.08638)` )
Costa T., Rosdahl J., Sijacki D., Haehnelt M. G., 2018, [MNRAS,](http://dx.doi.org/10.1093/mnras/stx2598)
473, 4197
Cresci G., Maiolino R., 2018, Nat. [Astron.,](http://dx.doi.org/10.1038/s41550-018-0404-5) 2, 179
Cresci G., et al., 2015, A [&](http://dx.doi.org/10.1051/0004-6361/201526581) A, 582, A63
Dasyra K. M., Combes F., Novak G. S., Bremer M., Spinoglio L.,
Pereira Santaella M., Salom´e P., Falgarone E., 2014, A [&](http://dx.doi.org/10.1051/0004-6361/201323070) A,
565, A46
Dasyra K. M., Bostrom A. C., Combes F., Vlahakis N., 2015,

[ApJ,](http://dx.doi.org/10.1088/0004-637X/815/1/34) 815
Dasyra K. M., Combes F., Oosterloo T., Oonk J. B. R., Morganti
R., Salom´e P., Vlahakis N., 2016, A [&](http://dx.doi.org/10.1051/0004-6361/201629689) A, 595, L7
Dav´e R., Oppenheimer B. D., Finlator K., 2011, [MNRAS,](http://dx.doi.org/10.1111/j.1365-2966.2011.18680.x) 415,

11

Duc P.-A., Mirabel I. F., Maza J., 1997, [A&AS,](http://dx.doi.org/10.1051/aas:1997205) 124, 533
Duffy A. R., Schaye J., Kay S. T., Vecchia C. D., 2008, [MNRAS](http://dx.doi.org/10.1111/j.1745-3933.2008.00537.x)
[Lett.,](http://dx.doi.org/10.1111/j.1745-3933.2008.00537.x) 390, 1
Erb D. K., 2015, [Nature,](http://dx.doi.org/10.1038/nature14454) 523, 169
Fabian A., 2012, [ARA&A,](http://dx.doi.org/10.1146/annurev-astro-081811-125521) 50, 455
Fabian A. C., Vasudevan R. V., Gandhi P., 2008, [MNRAS](http://dx.doi.org/10.1111/j.1745-3933.2008.00430.x) Lett.,

385

Faucher-Giguere C. A., Quataert E., 2012, [MNRAS,](http://dx.doi.org/10.1111/j.1365-2966.2012.21512.x) 425, 605
Feruglio C., Maiolino R., Piconcelli E., Menci N., Aussel H.,
Lamastra A., Fiore F., 2010, Astron. [Astrophys.,](http://dx.doi.org/10.1051/0004-6361/201015164) 518, L155
Feruglio C., et al., 2015, A [&](http://dx.doi.org/10.1051/0004-6361/201526020) A, 583, A99
Feruglio C., et al., 2017, A [&](http://dx.doi.org/10.1051/0004-6361/201731387) A, 608, A30
Finlator K., Dav´e R., 2008, [MNRAS,](http://dx.doi.org/10.1111/j.1365-2966.2008.12991.x) 385, 2181
Fiore F., et al., 2017, A [&](http://dx.doi.org/10.1051/0004-6361/201629478) A, 601, A143
Fischer J., et al., 2010, Astron. [Astrophys.,](http://dx.doi.org/10.1051/0004-6361/201014676) 518, L41
Franceschini A., et al., 2003, [MNRAS,](http://dx.doi.org/10.1046/j.1365-8711.2003.06744.x) 343, 1181
Gabor J. M., Bournaud F., 2014, [MNRAS,](http://dx.doi.org/10.1093/mnras/stu677) 441, 1615
Gallerani S., Pallottini A., Feruglio C., Ferrara A., Maiolino R.,
[Vallini L., Riechers D. A., Pavesi R., 2018, MNRAS, 473, 1909](http://dx.doi.org/10.1093/mnras/stx2458)
Garc´ıa-Burillo S., et al., 2015, A [&](http://dx.doi.org/10.1051/0004-6361/201526133) A, 580, A35
Gil de Paz A., et al., 2007, [ApJS,](http://dx.doi.org/10.1086/516636) 173, 185
Gilli R., Maiolino R., Marconi A., Risaliti G., Dadina M., Weaver
K. A., Colbert E. J. M., 2000, Astron. Astrophys., 355, 485
Gilli R., Calura F., D’Ercole A., Norman C., 2017, A [&](http://dx.doi.org/10.1051/0004-6361/201730457) A, 603,
A69

Gonz´alez-Alfonso E., et al., 2017, [ApJ,](http://dx.doi.org/10.3847/1538-4357/836/1/11) 836, 11
Gonz´alez-Mart´ın O., Masegosa J., M´arquez I., Guainazzi M.,
Jim´enez-Bail´on E., 2009, A [&](http://dx.doi.org/10.1051/0004-6361/200912288) A, 506, 1107
Greene J. E., Zakamska N. L., Smith P. S., 2012, [ApJ,](http://dx.doi.org/10.1088/0004-637X/746/1/86) 746, 86
Harrison C. M., Alexander D. M., Mullaney J. R., Swinbank
A. M., 2014, [MNRAS,](http://dx.doi.org/10.1093/mnras/stu515) 441, 3306
Heckman T. M., Kauffmann G., Brinchmann J., Tremonti C.,
White S. D. M., Charlot S., Tremonti C., White S. D. M.,
2004, [ApJ,](http://dx.doi.org/10.1086/422872) 613, 109
Heckman T. M., Alexandroff R. M., Borthakur S., Overzier R.,
Leitherer C., 2015, [ApJ,](http://dx.doi.org/10.1088/0004-637X/809/2/147) 809
Hernquist L., 1990, [ApJ,](http://dx.doi.org/10.1086/168845) 356, 359


MNRAS **000**, 1–26 (2018)



Ho L., Filippenko A., Sargent W., 1993, [ApJ,](http://dx.doi.org/10.1086/173291) 417, 63
Ho L. C., Filippenko A. V., Sargent W. L. W., 1997, [ApJS,](http://dx.doi.org/10.1086/313041) 112,

315

Ishibashi W., Fabian A. C., 2015, [MNRAS,](http://dx.doi.org/10.1093/mnras/stv944) 451, 93
Ishibashi W., Banerji M., Fabian A. C., 2017, [MNRAS,](http://dx.doi.org/10.1093/mnras/stx921) 469, 1496
[Ishibashi W., Fabian A. C., Maiolino R., 2018, MNRAS, p. sty236](http://dx.doi.org/10.1093/mnras/sty236)
Ivison R. J., et al., 2010, [MNRAS,](http://dx.doi.org/10.1111/j.1365-2966.2009.15918.x) 402, 245
Janssen A., et al., 2016, [ApJ,](http://dx.doi.org/10.3847/0004-637X/822/1/43) 822, 43
Kelly B. C., 2007, [ApJ,](http://dx.doi.org/10.1086/519947) 665, 1489
Kennicutt R. C., 1998, [ApJ,](http://dx.doi.org/10.1086/305588) 498, 541
Kennicutt R. C., Evans N. J., 2012, [ARA&A,](http://dx.doi.org/10.1146/annurev-astro-081811-125610) 50, 531
Kewley L. J., Groves B., Kauffmann G., Heckman T., 2006, [MN-](http://dx.doi.org/10.1111/j.1365-2966.2006.10859.x)
[RAS,](http://dx.doi.org/10.1111/j.1365-2966.2006.10859.x) 372, 961
King A. R., 2010, [MNRAS,](http://dx.doi.org/10.1111/j.1365-2966.2009.16013.x) 402, 1516
King A., Nixon C., 2015, [MNRAS](http://dx.doi.org/10.1093/mnrasl/slv098) Lett., 453, L46
King A., Pounds K., 2015, [ARA&A,](http://dx.doi.org/10.1146/annurev-astro-082214-122316) 53, 115
King A. R., Zubovas K., Power C., 2011, [MNRAS](http://dx.doi.org/10.1111/j.1745-3933.2011.01067.x) Lett., 415
LaMassa S. M., Heckman T. M., Ptak A., Martins L., Wild V.,
Sonnentrucker P., Hornschemeier A., 2011, [ApJ,](http://dx.doi.org/10.1088/0004-637X/729/1/52) 729, 52
Lena D., et al., 2015, [ApJ,](http://dx.doi.org/10.1088/0004-637X/806/1/84) 806, 84
Leroy A. K., Walter F., Decarli R., Bolatto A., Zschaechner L.,
Weiss A., 2015, [ApJ,](http://dx.doi.org/10.1088/0004-637X/811/1/15) 811, 15
Lutz D., Maiolino R., Spoon H. W. W., Moorwood A. F. M.,
2004, Astron. [Astrophys.,](http://dx.doi.org/10.1051/0004-6361:20035838) 418, 465
Maiolino R., Rieke G., 1995, [ApJ,](http://dx.doi.org/10.1086/176468) 454, 95
Maiolino R., et al., 2012, [MNRAS](http://dx.doi.org/10.1111/j.1745-3933.2012.01303.x) Lett., 425
Mannucci F., Pozzetti L., Thompson D., Oliva E., Baffa C., Comoretto G., Gennari S., Lisi F., 2002, [MNRAS,](http://dx.doi.org/10.1046/j.1365-8711.2002.05108.x) 329, 57
Marconi A., Risaliti G., Gilli R., Hunt L. K., Maiolino R., Salvati
M., 2004, [MNRAS,](http://dx.doi.org/10.1111/j.1365-2966.2004.07765.x) 351, 169
McIntosh D. H., et al., 2005, [ApJ,](http://dx.doi.org/10.1086/432786) 632, 191
McMullin J. P., Waters B., Schiebel D., Young W., Golap K.,
2007, Astron. Data Anal. Softw. Syst. XVI, 376, 127
Miller C. J., Nichol R. C., Gomez P. L., Hopkins A. M., Bernardi
M., 2003, [ApJ,](http://dx.doi.org/10.1086/378383) 597, 142
Mitra S., Dav´e R., Finlator K., 2015, [MNRAS,](http://dx.doi.org/10.1093/mnras/stv1387) 452, 1184
Monreal-Ibero A., Arribas S., Colina L., 2006, [ApJ,](http://dx.doi.org/10.1086/498257) 637, 138
Morganti R., Tadhunter C. N., Oosterloo T. A., 2005, [Astron.](http://dx.doi.org/10.1051/0004-6361:200500197)
[Astrophys.,](http://dx.doi.org/10.1051/0004-6361:200500197) 444, L9
Morganti R., Fogasy J., Paragi Z., Oosterloo T., Orienti M., 2013,

Science (80-. )., 341, 1082
Morganti R., Oosterloo T., Raymond Oonk J. B., Frieswijk W.,
Tadhunter C., 2015, A [&](http://dx.doi.org/10.1051/0004-6361/201525860) A, 580, A1
Morganti R., Veilleux S., Oosterloo T., Teng S. H., Rupke D.,
2016, A [&](http://dx.doi.org/10.1051/0004-6361/201628978) A, 593, A30
Moster B. P., Naab T., White S. D. M., 2013, [MNRAS,](http://dx.doi.org/10.1093/mnras/sts261) 428, 3121
Mullaney J. R., Alexander D. M., Fine S., Goulding A. D., Harrison C. M., Hickox R. C., 2013, [MNRAS,](http://dx.doi.org/10.1093/mnras/stt751) 433, 622
Nardini E., Risaliti G., Salvati M., Sani E., Imanishi M., Marconi
A., Maiolino R., 2008, [MNRAS](http://dx.doi.org/10.1111/j.1745-3933.2008.00450.x) Lett., 385, L130
Nardini E., Risaliti G., Salvati M., Sani E., Watabe Y., Marconi
A., Maiolino R., 2009, [MNRAS,](http://dx.doi.org/10.1111/j.1365-2966.2009.15357.x) 399, 1373
Nardini E., Risaliti G., Watabe Y., Salvati M., Sani E., 2010,

[MNRAS,](http://dx.doi.org/10.1111/j.1365-2966.2010.16618.x) 405, 2505
Navarro J. F., Frenk C. S., White S. D. M., 1995, [ApJ,](http://dx.doi.org/10.1086/177173) 462, 563
Neff S., Hutchings J., Standord S., Unger S., 1990, [Astron.](http://dx.doi.org/10.1086/115398) J., 99,

1088

Peng Y., Maiolino R., Cochrane R., 2015, [Nature,](http://dx.doi.org/10.1038/nature14439) 521, 192
Pereira-Santaella M., et al., 2011, A [&](http://dx.doi.org/10.1051/0004-6361/201117420) A, 535, 93
Pereira-Santaella M., et al., 2016, A [&](http://dx.doi.org/10.1051/0004-6361/201628875) A, 594, A81
Perna M., et al., 2015, A [&](http://dx.doi.org/10.1051/0004-6361/201425035) A, 574, A82
Piconcelli E., Jimenez-Bailon E., Guainazzi M., Schartel N.,
Rodriguez-Pascual P. M., Santos-Lleo M., 2005, [Astron.](http://dx.doi.org/10.1051/0004-6361:20041621) As[trophys.,](http://dx.doi.org/10.1051/0004-6361:20041621) 432, 15
Pineda J. L., Langer W. D., Goldsmith P. F., 2014, A [&](http://dx.doi.org/10.1051/0004-6361/201424054) A, 570,
A121

Prieto M. A., Reunanen J., Tristram K. R. W., Neumayer N.,

22 _A_ _Fluetsch_ _et_ _al._


Fernandez-Ontiveros J. A., Orienti M., Meisenheimer K.,
2010, [MNRAS,](http://dx.doi.org/10.1111/j.1365-2966.2009.15897.x) 402, 724
Puchwein E., Springel V., 2013, [MNRAS,](http://dx.doi.org/10.1093/mnras/sts243) 428, 2966
Querejeta M., et al., 2016, A [&](http://dx.doi.org/10.1051/0004-6361/201628674) A, 593, A118
Ricci C., et al., 2017, Nature, 549, 488
Richings A. J., Faucher-Gig`uere C.-A., 2017, MNRAS, 000, 1
Richings A. J., Faucher-Gigu`ere C. A., 2018, [MNRAS,](http://dx.doi.org/10.1093/mnras/stx3014) 474, 3673
Risaliti G., Maiolino R., Salvati M., 1999, [ApJ,](http://dx.doi.org/10.1086/307623) 522, 157
Roos O., Juneau S., Bournaud F., Gabor J. M., 2015, [ApJ,](http://dx.doi.org/10.1088/0004-637X/800/1/19) 800
Rupke D. S., Veilleux S., 2013, [ApJ,](http://dx.doi.org/10.1088/0004-637X/768/1/75) 768
Rupke D. S., Veilleux S., Sanders D. B., 2005a, [ApJ](http://dx.doi.org/10.1086/444451)
Rupke D. S., Veilleux S., Sanders D. B., 2005b, [ApJS,](http://dx.doi.org/10.1086/432889) 160, 115
Rupke D. S. N., G¨ultekin K., Veilleux S., 2017, [ApJ,](http://dx.doi.org/10.3847/1538-4357/aa94d1) 850, 40
[Sakamoto K., Aalto S., Combes F., Evans A., Peck A., 2014, ApJ,](http://dx.doi.org/10.1017/S1743921314010357)
797, 90
Salak D., Nakai N., Hatakeyama T., Miyamoto Y., 2016, [ApJ,](http://dx.doi.org/10.3847/0004-637X/823/1/68)
823, 68
Sarzi M., et al., 2010, [MNRAS,](http://dx.doi.org/10.1111/j.1365-2966.2009.16039.x) 402, 2187
Scannapieco E., Oh S. P., 2004, [ApJ,](http://dx.doi.org/10.1086/386542) 608, 62
Schawinski K., Koss M., Berney S., Sartori L. F., 2015, [MNRAS,](http://dx.doi.org/10.1093/mnras/stv1136)
451, 2517
Severgnini P., Maiolino R., Salvati M., 2000, A & A
Sijacki D., Springel V., Di Matteo T., Hernquist L., 2007, [MN-](http://dx.doi.org/10.1111/j.1365-2966.2007.12153.x)
[RAS,](http://dx.doi.org/10.1111/j.1365-2966.2007.12153.x) 380, 877
Skrutskie M. F., et al., 2006, [Astron.](http://dx.doi.org/10.1086/498708) J., 131, 1163
Solomon P., Vanden Bout P., 2005, [ARA&A,](http://dx.doi.org/10.1146/annurev.astro.43.051804.102221) 43, 677
Somerville R. S., Dav´e R., 2015, [ARA&A,](http://dx.doi.org/10.1146/annurev-astro-082812-140951) 53, 51
Spoon H. W. W., et al., 2013, [ApJ,](http://dx.doi.org/10.1088/0004-637X/775/2/127) 775, 127
Springel V., di Matteo T., Hernquist L., 2005, [MNRAS,](http://dx.doi.org/10.1111/j.1365-2966.2005.09238.x) 361, 776
Stone M., Veilleux S., Mel´endez M., Sturm E., Graci´a-Carpio J.,
Gonz´alez-Alfonso E., 2016, [ApJ,](http://dx.doi.org/10.3847/0004-637X/826/2/111) 826, 111
Strickland D. K., 2007, [MNRAS,](http://dx.doi.org/10.1111/j.1365-2966.2007.11478.x) 376, 523
Sturm E., 2011, [ApJ,](http://dx.doi.org/10.1088/2041-8205/733/1/L16) 733, L16
Sun A.-L., Greene J. E., Zakamska N. L., Nesvadba N. P. H.,
2014, [ApJ,](http://dx.doi.org/10.1088/0004-637X/790/2/160) 790, 160
Takeuchi T. T., Buat V., Iglesias-P´aramo J., Boselli A., Burgarella D., 2005, A [&](http://dx.doi.org/10.1051/0004-6361:20042189) A, 432, 423
Taylor E. N., et al., 2011, [MNRAS,](http://dx.doi.org/10.1111/j.1365-2966.2011.19536.x) 418, 1587
Teng S. H., et al., 2009, [ApJ,](http://dx.doi.org/10.1088/0004-637X/701/2/2035) 701, 2035
Teng S. H., et al., 2015, [ApJ,](http://dx.doi.org/10.1088/0004-637X/814/1/56) 814, 56
Thompson T. A., Quataert E., Murray N., 2005, [ApJ,](http://dx.doi.org/10.1086/431923) 630, 167
Thompson T. A., Fabian A. C., Quataert E., Murray N., 2015,

[MNRAS,](http://dx.doi.org/10.1093/mnras/stv246) 449, 147
Toba Y., Komugi S., Nagao T., Yamashita T., Wang W.-H., Imanishi M., Sun A.-L., 2017, [ApJ,](http://dx.doi.org/10.3847/1538-4357/aa9d17) 851, 98
Tombesi F., Mel´endez M., Veilleux S., Reeves J. N., Gonz´alezAlfonso E., Reynolds C. S., 2015, [Nature,](http://dx.doi.org/10.1038/nature14261) 519, 436
Veilleux S., Kim D.-C., Sanders D. B., Mazzarella J. M., Soifer
B. T., 1995, [ApJS,](http://dx.doi.org/10.1086/192158) 98, 171
Veilleux S., Kim D., Sanders D. B., 2002, [ApJS,](http://dx.doi.org/10.1086/343844) 143, 315
Veilleux S., Cecil G., Bland-Hawthorn J., 2005, [ARA&A,](http://dx.doi.org/10.1146/annurev.astro.43.072103.150610) 43, 769
Veilleux S., et al., 2009, [ApJS,](http://dx.doi.org/10.1088/0067-0049/182/2/628) 182, 628
Veilleux S., et al., 2013, [ApJ,](http://dx.doi.org/10.1088/0004-637X/776/1/27) 776, 27
Veilleux S., Bolatto A., Tombesi F., Mel´endez M., Sturm E.,
Gonz´alez-Alfonso E., Fischer J., Rupke D. S. N., 2017, [ApJ,](http://dx.doi.org/10.3847/1538-4357/aa767d)
843, 18
V´eron-Cetty M.-P., V´eron P., 2010, Astron. [Astrophys.,](http://dx.doi.org/10.1051/0004-6361/201014188) 518, A10
Vogelsberger M., et al., 2014, [MNRAS,](http://dx.doi.org/10.1093/mnras/stu1536) pp 1518–1547
Walch S., Naab T., 2015, [MNRAS,](http://dx.doi.org/10.1093/mnras/stv1155) 451, 2757
Walter F., et al., 2017, [ApJ,](http://dx.doi.org/10.3847/1538-4357/835/2/265) 835, 265
Weiß A., Walter F., Scoville N. Z., 2005, Astron. [Astrophys.,](http://dx.doi.org/10.1051/0004-6361:20052667) 438,

533

Westmoquette M. S., Clements D. L., Bendo G. J., Khan S. A.,
2012, [MNRAS,](http://dx.doi.org/10.1111/j.1365-2966.2012.21214.x) 424, 416
Woo J.-H., et al., 2010, [ApJ,](http://dx.doi.org/10.1088/0004-637X/716/1/269) 716, 269
Woo J.-H., Son D., Bae H.-J., 2017, [ApJ,](http://dx.doi.org/10.3847/1538-4357/aa6894) 839, 120
Yuan T.-T., Kewley L. J., Sanders D. B., 2010, [ApJ,](http://dx.doi.org/10.1088/0004-637X/709/2/884) 709, 884
Yun M. S., Reddy N. A., Condon J. J., 2001, [ApJ,](http://dx.doi.org/10.1086/323145) 554, 803



Zhang Z., Shi Y., Rieke G. H., Xia X., Wang Y., Sun B., Wan L.,
2016, [Astrophys.](http://dx.doi.org/10.3847/2041-8205/819/2/L27) J. Lett., 819, 0
Zschaechner L. K., et al., 2016, [ApJ,](http://dx.doi.org/10.3847/0004-637X/832/2/142) 832, 142
Zubovas K., 2015, [MNRAS,](http://dx.doi.org/10.1093/mnras/stv1173) 451, 3627
Zubovas K., King A., 2012, [ApJ,](http://dx.doi.org/10.1088/2041-8205/745/2/L34) 745, L34


MNRAS **000**, 1–26 (2018)

_Cold_ _Molecular_ _Outflows_ _in_ _the_ _Local_ _Universe_ 23


**Table** **1.** List of galaxies in the sample analysed in this paper, together with some of their basic properties


Galaxy type _z_ _D_ L SFR log(L AGN ) log(M ⋆ ) α bol log(M(H 2 )) log(M(HI)) q IR Ref.

[Mpc] [M ⊙ yr [−][1] ] [erg s [−][1] ] [M ⊙ ] [M ⊙ ] [M ⊙ ]
(1) (2) (3) (4) (5) (6) (7) (8) (9) (10) (11) (12)

**CO** **Literature** **data**

IRAS F08572+3915 Sy2 0.05821 265 20 45.72 10.79 0.86 9.18 3.57 α, A, a
IRAS F10565+2448 Sy2 0.04311 196 95 44.81 10.66 0.170 9.90 2.64 α, A, a
IRAS 23365+3604 LINER 0.06438 285 137 44.67 11.23 0.072 9.93 2.73 α, A, a
Mrk 273 Sy2 0.03777 169 139 44.16 11.10 0.080 9.70 10.21 2.49 α, A, a
IRAS F23060+0505 Sy2 0.17300 831 75 46.06 11.75 0.780 10.39 2.79 α, A, a
Mrk 876 Sy1 0.12900 607 6.5 45.84 11.64 0.930 9.84 2.63 α, A, a
I Zw 1 Sy1 0.06114 259 36 45.37 11.30 0.520 9.56 10.27 3.04 α, A, a
Mrk 231 Sy1 0.04217 189 234 45.72 11.53 0.340 9.73 2.44 α, A, a
NGC 1266 LINER 0.00719 28.6 1.6 43.31 10.30 0.250 9.23 2.36 α, A, a
M82 HII 0.00068 4.03 10 ≤41.54 10.66 ≤0.0009 8.64 9.04 2.62 α, A, a
NGC 1377 LINER 0.00578 23.9 0.9 42.93 10.06 0.200 8.44 9.89 α, A, a
NGC 6240 Sy2 0.02448 107 16 45.38 11.53 0.780 9.86 10.05 2.10 α, A, a
NGC 3256 HII 0.00926 44.6 36 ≤41.97 11.23 ≤0.0007 9.68 9.89 2.37 α, A, a
NGC 3628 HII 0.00280 17.1 1.8 ≤40.79 11.30 ≤0.0009 9.53 10.31 2.00 α, A, a
NGC 253 HII 0.00081 2.77 3 ≤40.66 10.65 ≤0.0004 8.15 9.27 3.01 α, A, a
NGC 6764 LINER 0.00807 32.6 2.6 42.23 10.48 0.017 8.90 9.64 2.25 α, A, a
NGC 1068 Sy2 0.00379 13.1 18 43.94 11.23 0.097 9.11 9.12 2.32 α, A, a
IC 5063 Sy2 0.01100 47.2 0.6 44.30 11.02 0.9 8.85 10.75 1.11 α, A, a
NGC 2146 HII 0.00298 12.5 12 ≤41.09 10.58 ≤0.0003 8.94 9.41 2.83 α, A, a
IRAS 17208-0014 HII 0.0428 189 200 ≤43.67 11.33 ≤0.24 10.03 2.79 β, B, b
NGC 1614 HII 0.0159 68.3 45 ≤42.07 11.07 ≤0.0006 9.51 2.77 β,γ, C, b
Circinus Galaxy Sy2 0.0014 8.34 0.6 43.57 10.95 0.59 9.32 10.27 2.07 δ, D, b
SDSS J1356+1026 Sy2 0.1230 579 20 46 11.36 0.43 8.91 2.32 ϵ, E, b
ESO 320-G030 HII 0.0108 51.1 20 ≤41.09 11.03 ≤0.0001 9.08 2.77 ζ, F, b
NGC 1808 HII 0.0033 10.8 5.1 ≤40.98 10.64 ≤0.0005 9.28 7.70 β, C, b
NGC 1433 Sy2 0.0036 14.5 0.23 42.24 10.67 0.20 8.63 9.22 η, G, b
M51 Sy2 0.0020 11.1 2.6 43.79 11.06 0.61 10.12 9.80 2.11 θ, H, b
4C 12.50 Sy2 0.1217 573 84 45.70 11.66 0.60 10.02 0.002 β,I,b,c
IRAS 05081+7936 HII 0.0537 239 98 ≤42.37 11.51 ≤0.0006 10.03 2.54 ι, J, d
IRAS 10035+4852 HII 0.0648 294 100 ≤45.11 11.19 ≤0.33 9.79 2.54 ι, J, d
IRAS F11119+3257 Sy1 0.189 929 144 46.2 12.20 0.689 9.94 1.62 κ, K, c

**CO** **ALMA** **archival** **data**

IRAS 20100-4156 HII 0.129583 605 330 ≤42.93 11.10 ≤ 0.0007 9.95 2.93 σ, O, b
PG 0157+001 Sy1 0.16311 777 209 45.29 11.71 0.18 9.38 2.13 τ, P, b
IRAS 15115+0208 HII 0.095482 441 50.9 ≤43.49 11.96 ≤0.1 9.72 υ, J, b
IRAS 05189-2524 Sy2 0.042563 189 146 44.47 11.06 0.05 8.99 3.08 χ, Q, b
NGC 4418 Sy2 0.007268 36.4 14.5 43.81 10.22 ≤0.0005 8.59 8.66 3.35 η, S, b
IRAS 13120-5453 Sy2 0.030761 138 157 44.35 11.14 0.173 9.59 η, N, c, f
IRAS 22491-1808 HII 0.077760 348 145 ≤41.64 11.07 ≤0.06 10.22 3.26 ψ, Q, h
NGC 1386 Sy2 0.002895 11.1 0.27 40.19 10.03 0.0015 8.28 2.69 λ, L, b
NGC 6810 HII 0.006775 28 5.0 40.70 10.93 0.0003 8.86 µ, C, b
NGC 5643 Sy2 0.003999 20.1 3.6 42.91 10.90 0.0029 8.99 9.42 ν, H, b
**OH** **outflows** **(Gonz´alez-Alfonso** **et** **al.** **2017)**
IRAS F03158+4227 Sy2 0.13459 632 220 45.94 11.70 0.55 ξ, o, C, e
IRAS F14348-1447 LINER 0.08257 382 169 44.59 11.46 0.17 10.17 o, M, e
IRAS F14378-3651 LINER 0.067637 308 112 45.12 11.15 0.21 9.46 2.56 o, π, N, e
IRAS F20551-4250 LINER 0.04295 187 43 44.75 11.15 0.13 9.67 2.89 β, C, e


**Columns:** (1) Galaxy name, (2) optical classification, (3) redshift, (4) luminosity distance, (5) star formation rate, (6): AGN
luminosity, (7) stellar mass, (8) fraction of the bolometric luminosity associated with the AGN (α bol = L AGN /L bol ), (9) molecular gas
mass, (10) HI gas mass, (11) radio excess parameter q IR, galaxies with q ≤ 1.8 have a radio excess, (12) references.
**References:** optical classification: α: Cicone et al. (2014), β: Yuan et al. (2010), γ: Alonso-Herrero et al. (2001), δ: Neff et al. (1990),
ϵ : Sun et al. (2014) and references therein, ζ : Pereira-Santaella et al. (2011), η: V´eron-Cetty & V´eron (2010), θ: Ho et al. (1997), ι:
Leroy et al. (2015) and references therein, κ: Veilleux et al. (2002), λ: Lena et al. (2015), µ: Strickland (2007), ν: Cresci et al. (2015)
and references therein, ξ: Nardini et al. (2010), o: Gonz´alez-Alfonso et al. (2017) and references therein, π: Teng et al. (2015), σ: Duc
et al. (1997), τ: Armus et al. (2004), υ: Best et al. (2005), φ: Baan et al. (1998), χ: Veilleux et al. (1995), ψ: Nardini et al. (2008)
AGN luminosity/X-ray luminosity: A: Cicone et al. (2014) and references therein, B: Garc´ıa-Burillo et al. (2015), C: Brightman &
Nandra (2011), D: Prieto et al. (2010), E: Sun et al. (2014), inferred from [OIII] line, F: Pereira-Santaella et al. (2011), G:,Risaliti
et al. (1999), inferred from [OIII] line, H: Lutz et al. (2004), I: Teng et al. (2009), J: estimated upper limit from 6 µm flux according
to Lutz et al. (2004), K: Tombesi et al. (2015), L: LaMassa et al. (2011), M: Gonz´alez-Mart´ın et al. (2009), N: Teng et al. (2015), O:
Franceschini et al. (2003), P: Piconcelli et al. (2005), Q: Severgnini et al. (2000)
AGN contribution: a: Cicone et al. (2014) and references therein, b: calculated in this work, see Sect. 2.4, c: Veilleux et al. (2009), d:
Leroy et al. (2015), e: Gonz´alez-Alfonso et al. (2017), f: Teng et al. (2015), g: Nardini et al. (2010), h: Nardini et al. (2008)


MNRAS **000**, 1–26 (2018)

24 _A_ _Fluetsch_ _et_ _al._


**Table** **2.** Outflow properties of the sample



Galaxy log M outf (H 2 ) R outf v outf M� outf (H 2 ) log τ depl,outf (H 2 ) P K L,outf (H 2 )



M� outf (H 2 ) _v_



Galaxy log M outf (H 2 ) R outf v outf M� outf (H 2 ) log τ depl,outf (H 2 ) K L,outfAGN 2 L outfAGN / 2 c _v_ M� outf (ion) M� outf (HI) NaID M� outf (HI) [CII] ef. Ref. Trans.

[M ⊙ ] [pc] [kms [−][1] ] [M ⊙ yr [−][1] ] [yr] [M ⊙ yr [−][1] ] [M ⊙ yr [−][1] ] [M ⊙ yr [−][1] ] [%]
(1) (2) (3) (4) (5) (6) (7) (8) (9) (10) (11) (12) (13) (14)

**Literature** **data**

IRAS F08572+3915 8.61 820 800 403 6.57 0.016 11 0.32 25 130 (a) 1-0
IRAS F10565+2448 8.37 1100 450 100 7.90 0.0010 13 0.54 65 180 (a) 1-0
IRAS 23365+3604 8.17 1230 450 57 8.18 0.008 10 (a) 1-0
Mrk 273 8.24 550 620 200 7.40 0.17 160 0.66 7.9 110 (a) 1-0
IRAS F23060+0505 ≤9.56 ≤4050 (550) ≤500 ≥7.69 ≤0.004 ≤4.5 (a) 1-0
Mrk 876 ≤9.48 ≤3550 (700) ≤610 ≥7.05 ≤0.014 ≤12 (a) 1-0
I Zw 1 ≤7.67 ≤500 (500) ≤47 ≥7.90 ≤0.0016 ≤1.9 (a) 1-0
Mrk 231 8.47 600 700 350 7.19 0.01 8.8 0.05 180 250 4.6 (a) 1-0
NGC 1266 7.93 450 177 11 8.19 0.005 18 2* (a) 1-0
M82 8.08 800 100 4 8.04 ≥0.036 ≥218 (a) 1-0
NGC 1377 7.29 200 110 5 7.77 0.0021 11 <1 (a) 2-1
NGC 6240 8.61 650 400 267 7.43 0.006 8.4 ≤1300 (a) 1-0
NGC 3256 7.34 500 250 4 9.12 ≥0.08 ≥190 3.6 26 (a) 2-1
NGC 3628 7.36 400 50 1.5 9.35 ≥0.019 ≥230 (a) 1-0
NGC 253 6.32 200 50 1.4 8.00 ≥0.024 ≥290 0.60 (a) 2-1
NGC 6764 6.52 600 170 1 8.89 0.006 20 (a) 1-0
NGC 1068 7.26 100 150 28 7.66 0.0023 9.1 (a) 2-1
IC 5063 7.37 500 300 8 7.97 0.0011 2.2 0.21 (a) 2-1
NGC 2146 7.68 1550 150 5 8.27 ≥0.27 ≥1100 (a) 1-0
IRAS 17208-0014 7.66 160 600 176 7.78 ≥0.43 ≥430 46 34 (b) 2-1
NGC 1614 7.51 560 360 21 8.19 ≥0.74 ≥1200 13 22 (b) 1-0
Circinus Galaxy 6.48 450 150 1 9.31 0.0002 0.78 0.07 (c) 1-0
SDSS J1356+1026 7.84 300 500 118 6.84 0.0009 1.1 2.7 (d) 3-2
ESO 320-G030 6.81 2500 455 1.2 9.00 ≥0.63 ≥840 1.6 24 (e) 2-1
NGC 1808 7.48 1000 98 3 8.80 ≥0.094 ≥580 (f) 1-0
NGC 1433 5.81 100 100 0.7 8.82 0.0012 7.1 0.07 (g) 3-2
M51 6.61 37 100 11 9.07 0.0006 3.5 (h) 1-0
4C 12.50 7.72 150 640 227 7.66 0.006 5.5 <30* (i) 3-2
IRAS 05081+7936 ≤8.01 ≤500 (400) ≤95 ≥8.05 (j) 1-0
IRAS 10035+4852 ≤8.15 ≤500 (400) ≤117 ≥7.72 (j) 1-0
IRAS F11119+3257 9.14 7000 1000 203 7.63 0.0046 2.7 5.7 (k) 1-0

**ALMA** **archival** **data**

IRAS 20100-4156 9.31 663 456 1457 6.78 ≥11 ≥15000 2.5 9.3 (l) 1-0
PG 0157+001 8.39 729 268 93 7.41 0.001 2.4 0.94 (l) 3-2
IRAS 15115+0208 8.82 1174 103 59 7.95 ≥0.006 ≥38 <1 (l) 1-0
IRAS 05189-2524 8.87 189 491 219 6.64 0.060 69 7.0 480 7.6 (l) 3-2
NGC 4418 7.90 569 134 19 7.31 0.0017 7.6 <1 (l) 2-1
IRAS 13120-5453 8.55 179 549 1115 6.54 0.47 520 680 0.82 (l) 3-2
IRAS 22491-1808 8.73 202 241 654 7.40 ≥27 ≥68000 0.29 (l) 2-1
NGC 1386 ≤6.23 80 500 ≤17 ≥7.24 ≤56 ≤68000 (l) 1-0
NGC 6810 ≤7.20 120 500 ≤64 ≥7.03 ≤107 ≤130000 (l) 1-0
NGC 5643 ≤6.92 60 500 ≤85 ≥7.14 ≤0.68 ≤820 (l) 1-0
**OH** **outflows** **(Gonz´alez-Alfonso** **et** **al.** **2017)**
IRAS F03158+4227 8.70 335 1000 1500 6.62 0.055 33 (m)
IRAS F14348-1447 8.62 355 450 420 7.54 0.07 95 ≤1500 (m)
IRAS F14378-3651 8.07 255 425 180 7.20 0.008 11 (m)
IRAS F20551-4250 8.00 175 450 200 7.37 0.023 31 0.40 (m)



L AGN



Outflow properties: (1) galaxy name, (2) outflow mass, (3) outflow radius, (4) outflow velocity (following the prescription in Rupke
et al. (2005a)), (5) outflow mass rate, (6) depletion time due to outflows, (7) kinetic power divided by AGN luminosity, (8) momentum
rate boost, (9) ionised outflow mass rate, (10) neutral outflow rate using Na I D absorption, (11) neutral outflow rate using [CII], (12)
fraction of the outflowing gas escaping the galaxy (*these values are taken from the literature and their definition of outflow velocity
is slightly different from the one used here), (13): references: (a) Cicone et al. (2014), (b) Garc´ıa-Burillo et al. (2015), (c) Zschaechner
et al. (2016), (d) Sun et al. (2014), (e) Pereira-Santaella et al. (2016), (f) Salak et al. (2016), (g) Combes et al. (2013), (h) Querejeta
et al. (2016), (i) Dasyra et al. (2014), (j) Leroy et al. (2015), (k) Veilleux et al. (2017), (l) this work, includes information about which
CO transition is used (m): Gonz´alez-Alfonso et al. (2017), (14) CO transition used for calculation of outflow properties.


MNRAS **000**, 1–26 (2018)

_Cold_ _Molecular_ _Outflows_ _in_ _the_ _Local_ _Universe_ 25


**Table** **3.** Fossil Outflow candidates


Galaxy P K,outf (H 2 )/L AGN (M [�] outf (H 2 )v)/(L AGN /c) P K,outf (H 2 )/P K,SF (H 2 )

[%]

Mrk 273 0.17 160 27

IRAS 17208-0014 ≥0.43 ≥430 14

IRAS 20100-4156 ≥11 ≥15000 18

IRAS 13120-5453 0.47 520 97

IRAS 22491-1808 ≥27 ≥68000 12


Outflow properties: (1): galaxy name, (2): ratio of kinetic power of the outflow and the bolometric luminosity of the AGN, (3):
momentum boost factor, (4): kinetic energy outflow compare to kinetic energy due to supernovae.


MNRAS **000**, 1–26 (2018)

26 _A_ _Fluetsch_ _et_ _al._


**APPENDIX** **A:** **ALMA** **ARCHIVAL** **DATA**


In Figs. A2–A7 of this appendix we show the ALMA archival
data of galaxies in which we have found evidence for outflows. Each figure shows on the top panels the integrated
spectrum along with a zoom in the Y-axis, and where the
blue dashed line shows the narrow component and the red
dashed line the broad component tracing the outflow. The
central panel shows the position-velocity diagram along the
major axis (left) and along the minor axis (right). The bottom panels show the map of the broad wings, i.e. the flux
integrated in the velocity ranges where the broad component is stronger than the narrow component (specific velocity ranges are indicated on top of each panel).



MNRAS **000**, 1–26 (2018)

_Cold_ _Molecular_ _Outflows_ _in_ _the_ _Local_ _Universe_ 27























































**Figure** **A1.** IRAS 20100-4156: The top panels show the CO line emission and the fit to the line, where the blue dashed line represents
the narrow emission and the red dashed line is the broad component. The two middle panels show the position-velocity diagrams along
the major (left) and minor (right) axis with (1,2,3,4,5,10,30,50,70)σ contours as white lines. In the bottom panel, the linemaps of the
wings are depicted (produced by integrating over the spectral range where the broad component, i.e. outflow component, is dominant).
The black cross indicates the peak of the narrow emission. Positive contours are shown as white lines (1,2,3,4,5,10)σ and negative contour
are represented by white dashed lines (-1,-2,-3)σ.


This paper has been typeset from a TEX/L [A] TEX file prepared by the author.


MNRAS **000**, 1–26 (2018)

28 _A_ _Fluetsch_ _et_ _al._

































































**Figure** **A2.** IRAS 05189-2524: see caption of Fig. A1, but contours in pv diagrams (middle panel) are (2,3,5,10,30,50,70)σ.


MNRAS **000**, 1–26 (2018)

_Cold_ _Molecular_ _Outflows_ _in_ _the_ _Local_ _Universe_ 29

























































**Figure** **A3.** PG 0157+001: see caption of Fig. A1



MNRAS **000**, 1–26 (2018)

30 _A_ _Fluetsch_ _et_ _al._


3.0


2.5


2.0


1.5


1.0


0.5


0.0


1000 750 500 250 0 250 500 750 1000



0.25


0.20


0.15


0.10


0.05


0.00


1000 750 500 250 0 250 500 750 1000





























**Figure** **A4.** IRAS13120-5453: see caption of Fig. A1, but contours in pv diagrams (middle panel) are (3,5,10,30,50,70)σ.


MNRAS **000**, 1–26 (2018)

_Cold_ _Molecular_ _Outflows_ _in_ _the_ _Local_ _Universe_ 31


0.6


0.5


0.4


0.3


0.2


0.1


0.0


0.1


400


200


200


400



































**Figure** **A5.** NGC4418: see caption of Fig. A1



MNRAS **000**, 1–26 (2018)

32 _A_ _Fluetsch_ _et_ _al._

































































**Figure** **A6.** IRAS15515+0208: see caption of Fig. A1



MNRAS **000**, 1–26 (2018)

_Cold_ _Molecular_ _Outflows_ _in_ _the_ _Local_ _Universe_ 33



























































**Figure** **A7.** IRAS 22491-1808: see caption of Fig. A1



MNRAS **000**, 1–26 (2018)


</paper>

## Items to check

```json
[
 {
  "path": "analysis_steps[0].method.evidence[0]",
  "value": "Fit single vs double Gaussian; two Gaussians preferred if reduced chi2 drops by >=10 per cent, plus visual check of narrow/broad components",
  "failed_quote": "If two Gaussians lead to a decrease in χ red [2] of 10 per cent or more, then we consider this as an initial clue for the possible presence of an outflow."
 },
 {
  "path": "analysis_steps[1].method.evidence[0]",
  "value": "Broad-component flux to L'CO then M = alpha_CO L'CO; v_outf = FWHM_broad/2 + |v_broad - v_narrow|; radius = deconvolved major-axis FWHM/2 of 2D Gaussian fit to wing map; Mdot = v M / r",
  "failed_quote": "We fit a 2D-Gaussian profile to the wing map and use the beam-deconvolved major axis (FWHM) divided by two as the radius of the outflow."
 }
]
```
