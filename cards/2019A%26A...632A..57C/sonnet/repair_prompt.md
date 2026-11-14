# Repair task for a Claude Code subagent

A methods card has evidence quotes that were not found verbatim in the paper. Below are the rules, the paper, and the failing items. Write ONE JSON object, nothing else, of the form {"repairs": [{"path": ..., "found": true|false, "loc": ..., "quote": ...}, ...]} with one entry per item (path unchanged) to:

    C:\Users\adama\alma-corpus\cards\2019A%26A...632A..57C\sonnet\repair_reply.txt

Use the Write tool for that file. Copy each quote character for character from the paper text below; a returned quote is checked mechanically and dropped if it is not in the paper. Do not read any other file, do not run commands, and do not change anything else. Reply with one line when done.

---

## Rules

You check evidence quotes for a methods card extracted from an astronomy paper. Some quotes could not be found verbatim in the paper text, and some stated values came without a quote. For each item: find the passage in the paper that supports the value and copy it VERBATIM (same words and order, at most 40 words; LaTeX markup may be dropped) with its loc (section heading, "abstract", "Table N" or "Figure N caption"). If the paper does not support the value, return found = false and leave quote and loc empty. Use only the paper text. Return one entry per item, with the item's path unchanged.

## Paper

<paper>
A&A 632, A57 (2019)
[https://doi.org/10.1051/0004-6361/201935226](https://doi.org/10.1051/0004-6361/201935226)
© T. Csengeri et al. 2019


# **Astronom** **y**
### &
# **Astrophysics**


## **Search for high-mass protostars with ALMA revealed up to** **kilo-parsec scales (SPARKS)**

#### **II. Complex organic molecules and heavy water in shocks around a young** high-mass protostar [⋆]

T. Csengeri [1,2], A. Belloche [1], S. Bontemps [2], F. Wyrowski [1], K. M. Menten [1], and L. Bouscasse [1]


1 Max Planck Institute for Radioastronomy, Auf dem Hügel 69, 53121 Bonn, Germany
e-mail: `[csengeri@mpifr-bonn.mpg.de](mailto:csengeri@mpifr-bonn.mpg.de)`
2 Laboratoire d’astrophysique de Bordeaux, Univ. Bordeaux, CNRS, B18N, allée Geoffroy Saint-Hilaire, 33615 Pessac, France


Received 7 February 2019 / Accepted 25 September 2019


**ABSTRACT**


_Context._ Classical hot cores are rich in molecular emission, and they show a high abundance of complex organic molecules (COMs).
The emergence of molecular complexity that is represented by COMs, in particular, is poorly constrained in the early evolution of hot

cores.
_Aims._ We put observational constraints on the physical location of COMs in a resolved high-mass protostellar envelope associated
with the G328.2551−0.5321 clump. The protostar is single down to ∼400 au scales and we resolved the envelope structure down to this
scale.
_Methods._ High angular resolution observations using the Atacama Large Millimeter Array allowed us to resolve the structure of
the inner envelope and pin down the emission region of COMs. We use local thermodynamic equilibrium modelling of the available 7.5 GHz bandwidth around ∼345 GHz to identify the COMs towards two accretion shocks and a selected position representing
the bulk emission of the inner envelope. We quantitatively discuss the derived molecular column densities and abundances towards
these positions, and use our line identification to qualitatively compare this to the emission of COMs seen towards the central position,
corresponding to the protostar and its accretion disk.
_Results._ We detect emission from 10 COMs, and identify a line of deuterated water (HDO). In addition to methanol (CH 3 OH), methyl
formate (CH 3 OCHO) and formamide (HC(O)NH 2 ) have the most extended emission. Together with HDO, these molecules are found to
be associated with both the accretion shocks and the inner envelope, which has a moderate temperature of _T_ kin ∼ 110 K. We find a significant difference in the distribution of COMs. O-bearing COMs, such as ethanol, acetone, and ethylene glycol are almost exclusively
found and show a higher abundance towards the accretion shocks with _T_ kin ∼ 180 K. Whereas N-bearing COMs with a CN group, such
as vinyl and ethyl cyanide peak on the central position, thus the protostar and the accretion disk. The molecular composition is similar
towards the two shock positions, while it is significantly different towards the inner envelope, suggesting an increase in abundance of
O-bearing COMs towards the accretion shocks.
_Conclusions._ We present the first observational evidence for a large column density of COMs seen towards accretion shocks at the
centrifugal barrier at the inner envelope. The overall molecular emission shows increased molecular abundances of COMs towards
the accretion shocks compared to the inner envelope. The bulk of the gas from the inner envelope is still at a moderate temperature
of _T_ kin ∼ 110 K, and we find that the radiatively heated inner region is very compact (<1000 au). Since the molecular composition is
dominated by that of the accretion shocks and the radiatively heated hot inner region is very compact, we propose this source to be
a precursor to a classical, radiatively heated hot core. By imaging the physical location of HDO, we find that it is consistent with an
origin within the moderately heated inner envelope, suggesting that it originates from sublimation of ice from the grain surface and its
destruction in the vicinity of the heating source has not been efficient yet.


**Key words.** astrochemistry – stars: massive – stars: formation – submillimeter: ISM – ISM: molecules



**1. Introduction**


The origin of complex organic molecules (COMs) that emerge
during the process of star and planet formation is a key question in understanding our astrochemical origins. Historically,
COMs in the interstellar medium have been identified towards so
called hot cores associated with sites of high-mass star formation
(Blake et al. 1987; Garay & Lizano 1999; Kurtz et al. 2000). In


⋆ A copy of the reduced datacubes is available at the CDS via anonymous ftp to `[cdsarc.u-strasbg.fr](http://cdsarc.u-strasbg.fr)` ( `[130.79.128.5](ftp://130.79.128.5)` ) or via `[http://](http://cdsarc.u-strasbg.fr/viz-bin/cat/J/A+A/632/A57)`
```
cdsarc.u-strasbg.fr/viz-bin/cat/J/A+A/632/A57

```


these objects, radiative heating from the central protostar leads
to an increase in temperature that can reach _T_ ≳100−200 K over
an extent of 0.05−0.1 pc, leading to a boost of chemical complexity due to thermal desorption of heavier molecules from the
ice mantles and grain surfaces, and subsequent gas-phase reactions. As a result, classical hot cores exhibit a high abundance of
COMs (e.g. Bisschop et al. 2007; Mookerjea et al. 2007; Beltrán
et al. 2009; Widicus Weaver et al. 2017).
The formation of COMs was first modelled by invoking
gas-phase chemical reactions (e.g. Millar et al. 1991; Charnley
et al. 1992; Caselli et al. 1993); recent chemical models assign,


A57, page 1 of 16



[Open Access article, published by EDP Sciences, under the terms of the Creative Commons Attribution License (](http://www.edpsciences.org) `[http://creativecommons.org/licenses/by/4.0](http://creativecommons.org/licenses/by/4.0)` ),
which permits unrestricted use, distribution, and reproduction in any medium, provided the original work is properly cited.

A&A 632, A57 (2019)



however, an important role to reactions on the grain-surface
(Charnley 2001; Garrod & Herbst 2006; Garrod & Widicus
Weaver 2013, see however Balucani et al. 2015). According
to these models, COMs are thought to form in the ice mantles of interstellar dust grains (Herbst & van Dishoeck 2009).
First, through the hydrogenation of atoms and small molecules,
the “zeroth-generation” species of small saturated COMs, such
as CH 3 OH, form. The diffusion and recombination of these
small molecules and radicals lead to the emergence of “firstgeneration” COMs, which becomes efficient at ≳30 K (Garrod &
Herbst 2006). When the radiative feedback from the emerging
protostar heats up its environment to ≳100 K, molecules sublimate from the grains and the “second-generation” COMs form
through gas-phase reactions.
This relatively simple picture of hot core formation and
chemistry seems to be, however, more complicated because
while all hot cores are rich in molecular emission, they exhibit a
significant diversity in their chemical composition (Walmsley &
Schilke 1993; Kurtz et al. 2000; Churchwell 2002; Bisschop et al.
2007; Calcutt et al. 2014; Widicus Weaver et al. 2017; Bonfand
et al. 2017; Sánchez-Monge et al. 2017; Allen et al. 2018). The
origin of this diversity is not fully understood. To understand
the key processes leading to the formation of COMs, first the
physical conditions, in which these molecules appear, need to be
constrained. In practice this means determining in which component of the envelope they reside, allowing us to pinpoint whether
they originate from the cold or the heated parts of the envelope, or are associated with slow or fast shocks. Constraining the
chemical differentiation of the inner envelope observationally
is therefore particularly important because resolving the physical location of COMs reveals the physical conditions of the gas,
which can help to constrain their chemical formation pathways.
This can be used as a tool to investigate both the physical and
chemical processes related to star formation and the emergence
of molecular complexity (Garrod & Widicus Weaver 2013; Sakai
et al. 2014).
Measured with single dish telescopes, incapable of resolving
individual massive envelopes, the origin of chemical differentiation is, however, challenging to identify. Reaching the scales
of a few hundred au resolution (<0. [′′] 1 at distances of several
kpc) is necessary to resolve the spatial distribution of COMs
within high-mass protostellar envelopes. While this information
would provide valuable input to constrain chemical models, this
is a largely unexplored territory for the precursors of high-mass
stars. In the past, due to angular resolution and sensitivity limitations, typically only the brightest hot cores have been studied
(e.g. Palau et al. 2011, 2017; Jiménez-Serra et al. 2012; Widicus
Weaver & Friedel 2012; Friedel & Widicus Weaver 2012; Öberg
et al. 2013; Allen et al. 2017). These are frequently found in
regions in which confusion due to the clustered nature of (highmass) star formation limits the possibility to reveal the spatial
location of COMs within single envelopes.
High angular resolution and high sensitivity observations
with the Atacama Large Millimeter Array (ALMA) provide now
an increasingly rich insight into the close vicinity of forming
O-type stars. An emerging number of observational studies
show in unprecedented detail the resolved structure of highmass clusters and protostellar envelopes (Sánchez-Monge et al.
2013; Maud et al. 2017; Ginsburg et al. 2017; Csengeri et al.
2018, hereafter Paper I). Some show an increasing complexity towards smaller scales in terms of clustering, while rare
examples of single high-mass protostellar envelopes have been
identified (Paper I). Here we study the molecular composition


A57, page 2 of 16



**[Fig.](http://dexter.edpsciences.org/applet.php?DOI=10.1051/0004-6361/201935226&pdf_id=0)** **1.** Line-free continuum emission map at 345 GHz combining
ALMA 12 m and 7 m arrays from Paper I imaged with robust parameter
of −2 giving a beam size with a geometric mean of 0. [′′] 16. The colour
scale is linear between −3σ and 120σ, where 1σ is 1.3 mJy beam [−][1],
contours start at 7σ and increase on a logarithmic scale up to 120σ by
a factor of 1.37. The red and blue dashed lines show the direction of
the CO outflow. The dotted line indicates the direction perpendicular to
the outflow, and the white ellipse shows the position of the accretion
disk from Paper I. The HPBW of the synthesised beam is shown in the
lower left corner; the filled ellipse corresponds to that of the continuum
image, the dotted ellipse to the molecular line data of this paper. Black
triangles mark the positions where the spectra have been extracted for
this work, and the white dotted circle shows the area with a radius of
0. [′′] 5 where the spectra have been averaged.


of the gas in the immediate vicinity of G328.2551-0.5321, a hot
core precursor, on few hundred au scales. This source is the only
massive object embedded in the MSXDC G328.25-00.51 dark
cloud that is located at a distance of 2.5 [+] − [1] 0 [.] . [7] 5 [kpc.] [It] [was] [identi-]
fied by Csengeri et al. (2017) based on the APEX Telescope
Large Area Survey of the Galaxy (ATLASGAL) (Schuller et al.
2009; Csengeri et al. 2014, 2017) at 870 µm, and was observed
in the frame of the SPARKS project (Search for High-mass Protostars with ALMA revealed up to kilo-parsec scales, Csengeri
et al., in prep.). In Paper I we show that the physical structure of this source is dominated by a single collapsing envelope
down to ∼400 au scales (Fig. 1), which makes it an ideal laboratory to study the emergence of hot cores. We estimate the
protostellar mass to be between ∼11 and 16 _M_ ⊙ with an envelope
mass ∼120 _M_ ⊙ (Paper I). For the first time, we find indication
for shocked gas in the 300–800 au vicinity of the protostar that
has been identified using a rotational transition of CH 3 OH from
within its first torsionally excited state, and is interpreted to outline accretion shocks (Fig. 1, _A_ and _B_ positions, Paper I). This
phenomenon has been observed towards nearby low-mass protostars (Sakai et al. 2014; Oya et al. 2017), and is expected to arise
due to the infall from the envelope onto a compact, rotationally
supported accretion disk. Here we focus on the molecular composition of the observed accretion shocks and reveal spatially
resolved emission from several COMs as new tracers pinpointing
these shocks.
The paper is organised as follows: in Sect. 2 we present the
observations and the data reduction; in Sect. 3 we show the spectra towards the selected positions and analyse their molecular
composition. In Sect. 4 we discuss the results, and finally in
Sect. 5 we present our conclusions.

T. Csengeri et al.: Search for high-mass protostars with ALMA revealed up to kilo-parsec scales (SPARKS). II.



**2. Observations and data reduction**


The observations have been carried out with ALMA in Cycle 2
using 35 of the 12 m antennas on 2015 May 3, and 2015
September 1. The phase centre was (α, δ) J2000 = (15 [h] 58 [m] 00.05 [s],
−53 [◦] 57 [′] 57. [′′] 8) and the baseline range is 15 m (17 kλ) to 1574 m
(1809 kλ). The total time on source was 7.4 min, and the
_T_ sys varies between 120 and 200 K. The calibrators have been
J1517−2422 (bandpass), J1617−5848 (phase) and the absolute
flux scale has been calibrated based on observations of Titan
and Ceres. The atmospheric conditions have been stable over
both measurement sets with a precipitable water vapour of ∼0.8
and ∼1.1 mm for the more extended and the compact configuration, respectively. We estimate an absolute flux uncertainty
around ∼10% by comparing the measured and catalogue fluxes
for the two measurement sets for the bandpass and phase calibrators. The bandpass calibrator was measured less frequently and
shows on average larger flux variations over the timescale of the
two measurement sets compared to the phase calibrator, which
does not show strong flux variations over this period. Here we
measure a maximum discrepancy between the catalogue and the
measured value up to 12%. We used four basebands in Band 7
centred on 347.331, 345.796, 337.061, and 333.900 GHz, respectively. This gives a 4 × 1.75 GHz effective bandwidth with a
spectral resolution of 0.977 MHz corresponding to ∼0.9 km s [−][1]
velocity resolution.
The data have been calibrated in CASA 4.3.1 with the
pipeline (version 34 044). We imaged and cleaned the data using
Briggs weighting and used the CLEAN algorithm for deconvolution. In this work we used a robust parameter of 0.5 for the
imaging [1] to favour sensitivity.
We first created a cube of the entire bandwidth with a
synthesised half-power beam width (HPBW) of 0. [′′] 30 × 0. [′′] 17
and a position angle of 88.37 degrees. The geometric mean
of the major and minor axes corresponds to a beam size of
0. [′′] 23 (∼575 au). We then extracted spectra of the entire frequency coverage towards representative positions corresponding
to the two accretion shock spots, and a position representing
the inner envelope (Fig. 1). The spectra were then exported to
GILDAS/CLASS [2] for further processing. We subtracted the continuum emission from these spectra by selecting line emission
free channels, and using a zero order baseline. To convert the
spectra from Jy beam [−][1] to Kelvin units we used a factor of 198
based on the geometric mean of the synthesized HPBW.
We also show here images of molecular line emission, where
we imaged a narrow velocity range around the selected line. In an
iterative process, we first created the image, then identified the
emission free channels towards the continuum peak and close
to the selected line emission. We then subtracted the continuum
emission in the _uv_ -data, performed the gridding and the deconvolution procedure, as described above, to obtain continuum free
data cubes around a list of selected lines.
We only focus here on molecular emission that originates
from scales typically smaller than the largest angular scales of
∼7 [′′], beyond which the sensitivity of our 12 m array observations
drops. We have therefore not used information from the more
compact 7 m array. We measure a 1σ rms noise level of ∼3 K
in brightness temperature ( _T_ b ) scales in a spectral resolution of


1 For the line-free continuum maps presented in Paper I we used a
robust parameter of −2 to give more weight to the longer baselines
yielding a better angular resolution of 0. [′′] 16 corresponding to ∼400 au
physical scales.
2 `[https://www.iram.fr/IRAMFR/GILDAS/](https://www.iram.fr/IRAMFR/GILDAS/)`



0.977 MHz. The spectral setup and data reduction for our target
is described in more details in Paper I.


**3. Results and analysis**


We investigate here the physical properties of the gas and aim
to explore its molecular composition with a particular focus on
COMs within this high-mass protostellar envelope. In Fig. 2, we
show the spectrum towards the central position averaged within
a radius of 0. [′′] 5 (Fig. 1), and as a comparison the spectrum
extracted towards the accretion shock position labelled as _B_, and
the central position corresponding to the protostar and its accretion disk. It is clear that the gas is rich in molecular emission, and
we identify and list the brightest transitions of simple molecules
in Table 1.
We present a quantitative analysis towards three positions
corresponding to the two locations of accretion shocks (one of
them shown in Fig. 2), and the bulk of the inner envelope represented by a position offset from both the accretion shocks and
the outflow impacted gas (Fig. 1). The severe blending due to the
larger line-widths and the significant uncertainty of dust temperature and opacity hinders us from a quantitative analysis of the
spectrum towards the central position, nevertheless, we show and
qualitatively discuss its molecular emission corresponding to the
protostar and its accretion disk. We show the extracted spectrum
towards the _B_ -shock position with the brightest emission lines,
and hence the richest spectrum in detail in Fig. 3 covering a
7.5 GHz bandwidth where we also label unblended transitions
of the identified COMs. The same figure for the other positions,
corresponding to the _A_ -shock position and the position representing the bulk emission of the inner envelope, are shown in
Appendix A.


_3.1. Line fitting and LTE modelling_


Since the volume density in the inner envelope is expected to
be high (¯ _n_ ≳ 10 [7] cm [−][3], Paper I), we model the spectra assuming
that local thermodynamic equilibrium (LTE) conditions apply.
We used the Weeds package (Maret et al. 2011), and fitted the
spectra in an iterative process. Corrections for the torsionally and
vibrationally excited states’ contribution to the rotational partition function, and thus to the column density, were derived for
the main isotopologue of the listed species.
The steps of the fitting are the following. We first determined
the molecular column density ( _N_ ) and the kinetic temperature
( _T_ kin ) of CH 3 OH. For this the input parameters are _N_ (CH 3 OH),
_T_ kin, source size, rest velocity (� lsr ) and linewidth (∆�). We fixed
the source size to 0. [′′] 4 which is larger than the beam. While
emission for the modelled transitions may have different source
sizes, as long as they are spatially resolved, the actual source size
does not significantly influence the result. Later, from Fig. 4, it
is clear that this assumption holds, although emission from the
_B_ -shock position seems to be more compact compared to the
other positions. Overestimating the source size would lead to
an underestimation of the molecular column densities. The � lsr
and ∆� are measured using a Gaussian fit to the CH 3 OH lines
and these values are reported in Paper I. We also considered
the continuum emission in our models that we have directly
extracted from the fitted baseline of the spectra. These parameters, together with the position, the measured continuum flux
density, and the results of the two free parameters, _N_ (CH 3 OH)
and _T_ kin are summarised in Table 2.
To constrain _N_ (CH 3 OH) and _T_ kin, we created a grid of models exploring a parameter range of _N_ (CH 3 OH) = 10 [17] –10 [20] cm [−][2]


A57, page 3 of 16

A&A 632, A57 (2019)


**[Fig.](http://dexter.edpsciences.org/applet.php?DOI=10.1051/0004-6361/201935226&pdf_id=0)** **2.** Grey filled histograms show spectra converted to brightness temperature ( _T_ b ) scale: spectrum extracted towards the central position, the
_B_ -shock position, and an average within a radius of 0. [′′] 5 around the peak of the dust continuum emission, which is multiplied by a factor of 4 for
a better visibility. The blue labels show the species listed in Table 1, pink labels show transitions of CH 3 OH (and its isotopologue) discussed in
Paper I. The spectra have been shifted along the y-axis for a better visibility.



and _T_ kin = 50−300 K. To select the best fit, we computed the
residuals of each fit, and visually inspected the results with a
particular emphasis on the optically thin lines and the unblended
transitions of CH 3 OH listed in Table 1. The resulting _T_ kin was
then used to estimate _N_ H 2 based on the dust continuum emission assuming that the gas and the dust are thermalised at these
high densities, hence _T_ d = _T_ kin . For this we used _N_ (H 2 ) =
_B_ ν ( _T_ _d_ ) Ω _F_ ν κ _R_ ν µ H2 _m_ H [[cm] [−][2] [],] [where] _[F]_ [ν] [is] [the] [beam] [averaged] [flux] [den-]
sity towards the selected positions, _B_ ν ( _T_ ) is the Planck function,
Ω is the solid angle of the beam calculated by Ω= 1.13 × Θ [2],
where Θ is the geometric mean of the beam major and minor
axes; κ ν = 0.0185 cm [2] g [−][1] from Ossenkopf & Henning (1994) at
345 GHz including the gas-to-dust ratio, _R_, of 100; µ H 2 is the
mean molecular weight per hydrogen molecule and is equal to
2.8; and _m_ H is the mass of a hydrogen atom.
We find that the derived parameters are similar for the
two shock positions, the CH 3 OH column density reaches up to
2 × 10 [19] cm [−][2], and the kinetic temperature is around 180 K. As
pointed out in Paper I, temperatures above ∼200 K are not consistent with the observations because other CH 3 OH lines would
appear brighter than the emission seen at the corresponding frequencies. Towards the position of the inner envelope, our models
suggest a factor of 5 lower CH 3 OH column density, and a considerably lower kinetic temperature of 110 K. In Table 2 we give
the range of values that are consistent with the data within 3σ,
and mark in bold the best fit value adopted for the following
modelling.
After fitting the CH 3 OH transitions, we created the models for other molecules using the same parameters (v lsr, ∆�, _T_ kin
and source size) as for CH 3 OH using the CDMS (Müller et al.
2005; Endres et al. 2016) and JPL (Pickett et al. 1998) molecular databases. Varying the molecular column density (relative
to methanol) we fitted the brightest unblended transitions of
each species and visually inspected the result. As shown later
in Fig. 4, the adopted source size corresponding to spatially


A57, page 4 of 16



resolved emission holds for most of the molecules, however,
some of the highest energy transitions seem to originate from a
more compact region which we do not account for in our model.
As a consequence, the column densities for these molecules may
be underestimated. As our composite final model shows, these
parameters give a good agreement with the spectra. The linewidth of vinyl and ethyl cyanide are, however, larger than that
of methanol with line-widths up to 8 km s [−][1] . Such a larger value
would lead to molecular column densities up to 50% higher than
the value given by our model.
We obtained the final model in an iterative process, by first
fitting the brightest emission of a new species independently,
and then visually inspected the full model including all identified species and checked whether the overall fit result remains
reasonably good. This is necessary due to the large fraction of
blended transitions. Subsequently, once a molecule was identified, we included its isotopologue in the model, and searched for
rotational transitions of their lowest energy vibrationally excited
states. However, except for CH 3 OH � t = 1 and HC 3 N � 7 = 1, we
have no clear detection of emission from such higher energy,
vibrationally excited states.
Altogether we could identify emission from 10 COMs in the
spectra. We list the results of the fit, such as their relative fraction
compared to CH 3 OH, molecular column density, and abundance
in Table 4 for the three positions. We show the spectrum for the
_B_ -shock position and the best-fit model in Fig. 3, where we label
the least blended lines of each molecule.


_3.2. Detection of COMs_


While the available, non continuous 7.5 GHz bandwidth offers
limited spectral coverage to perform a complete analysis of all
the molecules that have lines in the spectra, we are able to identify several transitions from ten COMs (Table 3). This frequency
range covers transitions over a broad range of upper energy levels

T. Csengeri et al.: Search for high-mass protostars with ALMA revealed up to kilo-parsec scales (SPARKS). II.



**Table 1.** Summary of detected simple molecules and their transitions.


Molecule Transition Frequency _E_ up / _k_ Database

[GHz] [K]


34 SO 7 8 –6 7 333.901 80 CDMS

SO 2 8 2,6 –7 1,7 334.673 43 CDMS
H [13] CCCN 38–37 334.930 314 CDMS

HC [13] CCN [(?)] 37–36 335.093 305 CDMS
HDCO [(?)] 5 1,4 –4 1,3 335.097 56 CDMS
HDO 3 3,1 –4 2,2 335.396 335 JPL
SO 2 29 5,25 –30 2,28 335.773 463 CDMS
SO 2 23 3,21 –23 2,22 336.089 276 CDMS

HC 3 N 37–36 336.521 307 CDMS

SO 10 11 –10 10 336.554 143 CDMS

SO 2 16 7,9 –17 6,12 336.670 245 CDMS
C [17] O 3–2 337.061 [(] _[a]_ [)] 32 CDMS

SO 2 13 2,12 –12 1,11 345.339 93 CDMS
H [13] CN 4–3 345.340 41 CDMS
34 SO 2 6 4,2 –6 3,3 345.553 57 CDMS

HC 3 N 38–37 345.609 324 CDMS
34 SO 2 5 4,2 –5 3,3 345.651 51 CDMS

CO 3–2 345.796 33 CDMS

NS Ω = 1/2, _l_ = _e_ 15/2–13/2 345.823 [(] _[b]_ [)] 70 CDMS
NS Ω = 1/2, _l_ = _f_ 15/2–13/2 346.221 [(] _[c]_ [)] 70 CDMS

HC 3 N, � 7 = 1, _l_ = 1 _e_ 38–37 346.456 645 CDMS

SO 2 16 4,12 –16 3,13 346.524 165 CDMS

SO 9 8 – 8 7 346.529 79 CDMS

SO 2 19 1,19 –18 0,18 346.652 168 CDMS

HC 3 N, � 7 = 1, _l_ = 1 _f_ 38–37 346.949 646 CDMS
H [13] CO [+] 4–3 346.998 42 CDMS

SiO 8–7 347.331 75 CDMS

HN [13] C 4–3 348.340 42 CDMS

SO 2 24 2,22 –23 3,21 348.388 292 CDMS
NS Ω = 3/2 15/2–13/2 348.516 [(] _[c]_ [)] 390 CDMS

H 2 CS 10 1,9 –9 1,8 348.534 105 CDMS
CH 3 CN 19–18, K = 8 [(] _[d]_ [)] 349.025 624 CDMS


CH 3 OH− _A_ � t = 0 2 −2 –3 −1 335.134 45 CDMS

CH 3 OH− _A_ � t = 0 7 1 –6 1 335.582 79 CDMS

CH 3 OH− _A_ � t = 0 14 7 –15 6 336.438 488 CDMS

CH 3 OH− _A_ � t = 0 12 −1 –12 0 336.865 197 CDMS

CH 3 OH− _E_ � t = 0 3 3 –4 2 337.136 62 CDMS

CH 3 OH− _E_ � t = 1 3 0 –2 1 334.427 315 CDMS

CH 3 OH− _A_ � t = 2 7 1 –6 1 336.606 747 JPL
13 CH 3 OH− _A_ � t = 0 12 −1 –12 0 335.560 193 CDMS
13 CH 3 OH− _A_ � t = 0 14 −1 –14 0 347.188 254 CDMS


**Notes.** [(] _[a]_ [)] The frequency corresponds to the _F_ = 1/2–3/2 transition.
( _b_ ) The frequency corresponds to the _F_ = 17/2–15/2 transition. ( _c_ ) The
frequency corresponds to the _F_ = 15/2–13/2 and _F_ = 13/2–11/2 transitions. [(] _[d]_ [)] The K = 9 transition at 348.911 GHz is likely to be detected,
although it is blended with a CH 3 OCHO line. [(?)] The “?” mark indicates
uncertain line identification due to blending.


( _E_ up / _k_ ) with a spontaneous decay rate (Einstein A-coefficient)
above 10 [−][4] s [−][1] for all species. The range of upper energy levels is, however, much narrower for the detected transitions and
covers a range typically around 150–400 K. Many of these transitions are, however strongly blended in the spectra. The smallest
energy range covered is for methyl formate and formamide.



In addition to several methanol (and isotopologue) lines,
we detect emission from various O-bearing COMs, such as
methyl formate (CH 3 OCHO � = 0), ethanol (C 2 H 5 OH � = 0),
acetone (CH 3 COCH 3 � = 0), ethylene glycol ( _a_ (CH 2 OH) 2 ), and
acetaldehyde (CH 3 CHO, � = 0). Comparing this list of Obearing COMs with the typical molecules identified towards hot
cores, a notable non detection is dimethyl ether (CH 3 OCH 3 )
which is often found to be co-existing and spatially correlated
with methyl formate (e.g. Brouillet et al. 2013; Jaber et al. 2014)
suggesting that they are chemically related (Garrod et al. 2008).
The upper limit on its molecular column density suggests, however, that a significant amount of dimethyl ether could remain
undetected in this frequency range (see Sect. 4.2).
Among the detected species except methanol, methyl formate has the largest column density up to _N_ (CH 3 OCHO) =
1.0 × 10 [18] cm [−][2] corresponding to a relative fraction of 0.05 compared to CH 3 OH. The largest number of transitions falling in
this band are from acetone, ethylene glycol and acetaldehyde
which produce a weed-like spread of spectral lines. Therefore,
due to blending and uncertainties in the spectroscopic parameters at such relatively high energy and frequency (Ordu et al.
2019), the identification of these molecules is less robust. As a
consequence, and also considering their large fraction of blended
transitions, the estimated column density is less robust compared
to the other species. In particular, blending seems to be more
prevalent for acetone, ethanol and acetaldehyde transitions in the
higher frequency spectral windows between 345 and 349 GHz.
We also likely detect formic acid, _t_ −HCOOH, however, there
are only two detectable lines of this molecule falling in our
frequency coverage and only one of them is unblended [3] . Our
modelling suggests that _t_ −HCOOH is among the lowest abundance O-bearing COMs, with typically more than two orders of
magnitude lower abundance compared to that of CH 3 OH.
We also identify N-bearing COMs, such as vinyl cyanide
(C 2 H 3 CN), and ethyl cyanide, (C 2 H 5 CN), methyl isocyanate
(CH 3 NCO) as well as formamide (HC(O)NH 2 ). The identification of formamide is, however, less robust since it has practically
only one detectable transition that is not blended with other lines
in the observed frequency range. Since the unblended formamide
line is strong, in order to increase the number of its detectable
transitions, we searched for its [13] C isotopologue both in the spectra extracted towards the shock spots and the brightest central
position. The brightest isotopologue line ( _J_ = 16 2,15 –15 2,14 ) is,
however, blended at the frequency of 335.405 GHz, and has a
predicted peak line temperature close to the noise level assuming
an isotopic ratio of 60 and optically thin emission.
Comparing the molecular abundances between O- and
N-bearing COMs, we find more than one order of magnitude lower column densities for the N-bearing COMs, such as
vinyl and ethyl cyanide, as well as formamide compared to the
O-bearing COMs. O-bearing COMs originating from a colder
gas component have been seen on similar scales towards the
Orion Hot Core and the Compact Ridge (Caselli et al. 1993),
and on somewhat larger scales towards classical hot cores (Qin
et al. 2010; Widicus Weaver et al. 2017). However, our analysis in
Sect. 3.3 suggests that our initial assumption that all COMs originate from gas with the same physical conditions (i.e. _T_ kin ), may
not hold, in particular for the central position where COMs with
a CN group seem to be more compact with a different spatial origin. In this case our estimation of the column density, especially
for C 2 H 3 CN and C 2 H 5 CN may not be accurate.


3 The 13 C isotopologue of formic acid has an expected peak line
temperature comparable to the noise level.


A57, page 5 of 16

A&A 632, A57 (2019)


**[Fig. 3.](http://dexter.edpsciences.org/applet.php?DOI=10.1051/0004-6361/201935226&pdf_id=0)** Spectrum extracted towards the _B_ -shock position from Paper I. Grey filled histogram shows the observed spectrum converted to brightness
temperature ( _T_ b ) scale, green line shows the composite LTE model including the species listed in Table 3. Coloured labels indicate the least blended
transitions of the modelled COMs, as well as other species identified in the spectrum (Table 1). Each colour represents a different molecule and
includes its isotopologues as well.


A57, page 6 of 16

T. Csengeri et al.: Search for high-mass protostars with ALMA revealed up to kilo-parsec scales (SPARKS). II.


**[Fig.](http://dexter.edpsciences.org/applet.php?DOI=10.1051/0004-6361/201935226&pdf_id=0)** **4.** Zeroth moment maps of some simple molecules, and selected transitions of COMs. All contours correspond to significant emission and
start at 20% of the maximum value and increase by 15% of the maximum value. Yellow star marks the position of the dust continuum peak
corresponding to the central protostar. The beam is shown in the lower left corner. Labels indicate the shown molecular species. One figure shows
the continuum as a reference, where the scale and contours are the same as in Fig. 1.


**Table 2.** Positions, their observed 345 GHz continuum emission and modelled methanol parameters.


Position Offset [(] _[a]_ [)] _F_ ν [(] _[b]_ [)] _T_ cont [(] _[c]_ [)] _N_ (CH 3 OH) [(][†][)] _T_ kin [(] _[d]_ [)][,][ (][†][)] _N_ H 2

[mJy/beam] [K] [cm [−][2] ] [K] [cm [−][2] ]


Shock _A_ [−1. [′′] 96;−2. [′′] 85] 156 30.9 1.2 × 10 [19] − **1** . **6** × **10** **[19]** 170–190 ( **180** ) 2.04 × 10 [24]

Shock _B_ [−2. [′′] 50;−2. [′′] 88] 144 28.5 1.6 × 10 [19] − 2.4 × 10 [19] ( **2** × **10** **[19]** ) 170–200 ( **180** ) 1.89 × 10 [24]

Inner envelope [−2. [′′] 43;−2. [′′] 47] 86 17.0 **4** . **1** × **10** **[18]** − 8.1 × 10 [18] 90–110 1.90 × 10 [24]

Protostar + disk [−2. [′′] 17;−2. [′′] 76] 239 47.3 200 − 500 1.1 − 2.8 × 10 [24 (] _[e]_ [)]


**Notes.** [(][†][)] Bold face shows the values from the best fit models. [(] _[a]_ [)] The position of the dust continuum peak is at [−2. [′′] 17;−2. [′′] 76] relative to the phase
centre position given in Sect. 2. [(] _[b]_ [)] Measured in the synthesized beam of 0. [′′] 3×0. [′′] 17. [(] _[c]_ [)] Brightness temperature of the continuum emission on the
Rayleigh-Jeans scale. [(] _[d]_ [)] _T_ kin corresponds to the gas temperature estimated from the CH 3 OH lines (Sect. 3.1). [(] _[e]_ [)] Neglecting the effect of optical
depth.



_3.3. Spatial distribution of various molecules_

Investigating the spatial distribution of the identified molecules,
we find a strong chemical differentiation within this high-mass
envelope. We show zeroth moment maps calculated over a
velocity range of −55 to −35 km s [−][1] for some unblended
transitions of COMs in Fig. 4, and for comparison, we also show
some of the brightest emission from other molecules, such as
HN [13] C ( _J_ = 4–3, _E_ up / _k_ = 42 K), H 2 CS ( _J_ = 10 − 1, 9 − 9 1,8,
_E_ up / _k_ = 105 K), SO 2 ( _J_ = 24 2,22 − 23 3,21, _E_ up / _k_ = 293 K),



NS ( _J_ = 8 1,8,7 − 7 −1,7,6, _J_ = 8 1,8,8 − 7 −1,7,7, _E_ up / _k_ = 70 K), as
well as the _K_ = 8–8 line of the _J_ = 19–18 transition of CH 3 CN
( _E_ up / _k_ = 624 K). All these transitions of simple molecules show
the brightest emission towards the peak position of the dust
continuum, and show considerably more extended emission
towards the inner envelope than the majority of the COMs. Only
the shown CH 3 CN line appears relatively compact highlighting the potentially warmer regions in the immediate vicinity
of the protostellar embryo.


A57, page 7 of 16

A&A 632, A57 (2019)


**Table 3.** Summary of the detected interstellar COMs towards the selected positions.


Molecule _E_ up / _k_ [(] _[a]_ [)] Detected _E_ up / _k_ Database Component [(] _[b]_ [)]
(K) (K)


CH 3 OH Methanol 45–1677 45–488 JPL e,s
CH 3 OCHO Methyl formate 80–352 80–352 JPL e,s
C 2 H 5 OH Ethanol 88–3294 90–407 CDMS s
CH 3 COCH 3 [(] _[c]_ [)] Acetone 98–2241 98–304 JPL s
a(CH 2 OH) 2 Ethylene glycol 98–1729 266–455 CDMS s
CH 3 CHO Acetaldehyde 153–807 153–383 JPL s
CH 3 NCO Methyl isocyanate 323–465 365–460 CDMS s
C 2 H 3 CN Vinyl cyanide 300–2531 308–326 CDMS c
C 2 H 5 CN Ethyl cyanide 60–2032 72–351 CDMS c
HC(O)NH 2 [(] _[d]_ [)] Formamide 136–152 136–152 CDMS e,s,c


_t_ -HCOOH [(] _[d]_ [)][,][(] _[e]_ [)] Formic acid 136–645 145 CDMS e


**Notes.** [(] _[a]_ [)] Range of upper energy levels of all transitions in our frequency coverage with an _A_ ij above 10 [−][4] s [−][1], except for methanol and methyl
formate, where the lowest energy transition detected has an _A_ ij of 9.87 × 10 [−][5] s [−][1] and 2.68 × 10 [−][5] s [−][1], respectively. [(] _[b]_ [)] The label e corresponds to
the inner envelope, s to the accretion shocks, and c to the innermost central regions that could have contribution from both the outflow and the
accretion disk. [(] _[c]_ [)] Spectroscopic parameters are more uncertain at this frequency range (Ordu et al. 2019). [(] _[d]_ [)] The identification is based on only one
to two unblended transitions. [(] _[e]_ [)] Formic acid contains less than 6 atoms, it is, however, the simplest organic acid and thus will be discussed together
with the listed interstellar COMs.



The emission from COMs is rather compact, but typically
spatially resolved. Methyl formate shows the most extended
morphology coinciding with the highest column density dust
emission, however, formamide is also considerably extended.
Using a 2D Gaussian fit to the 0th moment map shown in Fig. 4,
we measure the beam convolved full-width at half-maximum
(FWHM) extent of methyl formate to be 0. [′′] 95 × 0. [′′] 58, corresponding to a beam deconvolved geometric mean of 0. [′′] 70.
Following the formulation in Paper I, we estimate a radius ( _R_ 90% )
of 0. [′′] 58 corresponding to a size of 1450 au. For formamide, we
measure a beam convolved FWHM of 0. [′′] 62 × 0. [′′] 61, corresponding to a beam deconvolved geometric mean of 0. [′′] 57. Similarly as
above, this corresponds to a radius of 0. [′′] 47 that is 1175 au.
Qualitatively comparing the emission from the central position towards that of the envelope, it is apparent that the O- versus
N-bearing COMs show a striking difference in their morphology; while O-bearing COMs peak offset from the central protostar, N-bearing COMs with a CN group are the brightest
towards the central position, thus the protostar and the disk, and
show an elongation in the direction of the outflow axis. The
most striking example of this dichotomy is seen in ethanol, acetone, acetaldehyde and ethylene glycol versus vinyl and ethyl
cyanides. The similar upper energy levels ( _E_ up / _k_ = 150−300 K)
of these transitions (Fig. 4) suggests that the spatial morphology corresponds to genuine chemical differentiation rather than
temperature gradients and excitation effects. Similarly as above,
using a 2D Gaussian fit, we measure a beam convolved FWHM
of the most compact emission of the 348.991 GHz C 2 H 3 CN line
of 0. [′′] 63 × 0. [′′] 51, corresponding to a beam deconvolved size of
0. [′′] 55 × 0. [′′] 47. The most compact component of this emission
corresponds to an _R_ 90% radius of ∼900 au.
The other striking feature is that, all the other typical
O-bearing COMs, such as ethanol, acetone, ethylene glycol peak
on and only show emission towards the shock positions. The
lack of detection of these molecules towards the inner envelope may be, however, due to observational limitation, because
the unblended transitions in our frequency coverage are typically above _E_ up / _k_ - 200 K, hence a combination of sensitivity,


A57, page 8 of 16



blending and excitation effects may make it difficult to detect
these molecules in the relatively colder gas component with
_T_ kin ≲ 100 K.


_3.4. Detection and distribution of HDO_


The LTE modelling allows us to identify the _J_ = 3 3,1 − 4 2,2 transition of HDO at 335.396 GHz ( _E_ up / _k_ = 335 K), and requires a
high column density of 2.1–4.0 × 10 [17] cm [−][2] to fit the observed
line intensity. Our models suggest that this transition is blended
with a line of ethylene glycol at 335.397 GHz. In addition, shifted
by a few km s [−][1] at 335.403 GHz, there is also a methyl formate
line which may also show a small contribution to the observed
emission at the frequency of the HDO line. However, there is no
model that could reproduce the observed spectrum using only
ethylene glycol and methyl formate. Our best fit model towards
all three position requires including a significant amount of HDO
to reproduce the observed line intensity. The spatial extent of
the HDO line is comparable to that of methyl formate and formamide, while ethylene glycol for example has a considerably
more compact morphology peaking on the accretion shocks.
The modelled lines do not contribute to more than 15–21% of
the velocity integrated line intensity on the selected positions,
therefore we assign the observed emission to the HDO line.
The distribution of the HDO emission together with its
velocity field is shown in Fig. 5. It shows an increased intensity towards one of the shock positions, however, its emission is dominated by the inner envelope component showing
an extended morphology. The estimated HDO abundance is
between 1.1 × 10 [−][7] and 2.1 × 10 [−][7] for all three positions, and is
therefore similar towards the shock positions and the inner envelope. Using a 2D Gaussian fit we measure its beam convolved
FWHM to be ∼0. [′′] 86 × 0. [′′] 54 with a deconvolved geometric
mean of 0. [′′] 64 corresponding to an _R_ 90% radius of 0. [′′] 53 that is
∼1325 au. As seen in Fig. 4, this shows that the emission from
HDO (and thus likely of that of H 2 O in the gas phase) is comparable to that of the inner envelope, as well as that of methanol
and methyl formate. Also formamide shows a similar, although

T. Csengeri et al.: Search for high-mass protostars with ALMA revealed up to kilo-parsec scales (SPARKS). II.


**Table 4.** Summary of the model results for the detected COMs.


Position Molecule _C_ vib [(] _[a]_ [)] _N_ / _N_ (CH 3 OH) _N_ _X_ [(] _[b]_ [)] _T_ rot v off [(] _[c]_ [)]

[cm [−][2] ] [K] [km s [−][1] ]


Shock–A CH 3 OH 1 1 1.6 × 10 [19] 7.8 × 10 [−][6] 180 −4.2
CH 3 OCHO 1 0.04 6.4 × 10 [17] 3.1 × 10 [−][7] 180 −4.2
C 2 H 5 OH 1.44 0.048 7.7 × 10 [17] 3.8 × 10 [−][7] 180 −4.2
CH 3 COCH 3 1 0.025 4.0 × 10 [17] 2.0 × 10 [−][7] 180 −4.2
a(CH 2 OH) 2 1 0.005 8.0 × 10 [16] 3.9 × 10 [−][8] 180 −4.2
_t_ -HCOOH [(] _[b]_ [)] 1 0.004 6.4 × 10 [16] 3.1 × 10 [−][8] 180 −4.2
CH 3 CHO 1 0.002 3.2 × 10 [16] 1.6 × 10 [−][8] 180 −4.2
CH 3 NCO 1.03 0.0041 6.6 × 10 [16] 3.2 × 10 [−][8] 180 −4.2
C 2 H 3 CN 1 0.0017 2.7 × 10 [16] 1.3 × 10 [−][8] 180 −4.2
C 2 H 5 CN 1.7 0.0057 9.1 × 10 [16] 4.4 × 10 [−][8] 180 −4.2
HC(O)NH 2 [(] _[b]_ [)] 1.16 0.0058 9.3 × 10 [16] 4.6 × 10 [−][8] 180 −4.2
CH 3 OCH 3 1 <0.1 <1.6 × 10 [18] <7.8 × 10 [−][7] 180 −4.2
HDO 1 0.02 3.2 × 10 [17] 1.6 × 10 [−][7] 180 −4.2


Shock–B CH 3 OH 1 1 2.0 × 10 [19] 1.1 × 10 [−][5] 180 +4.55
CH 3 OCHO 1 0.05 1.0 × 10 [18] 5.3 × 10 [−][7] 180 +4.55
C 2 H 5 OH 1.44 0.048 9.6 × 10 [17] 5.1 × 10 [−][7] 180 +4.55
CH 3 COCH 3 1 0.025 5.0 × 10 [17] 2.6 × 10 [−][7] 180 +4.55
a(CH 2 OH) 2 1 0.005 1.0 × 10 [17] 5.3 × 10 [−][8] 180 +4.55
_t_ -HCOOH [(] _[b]_ [)] 1 0.005 1.0 × 10 [17] 5.3 × 10 [−][8] 180 +4.55
CH 3 CHO 1 0.002 4.0 × 10 [16] 2.1 × 10 [−][8] 180 +4.55
CH 3 NCO 1.03 0.0041 8.2 × 10 [16] 4.4 × 10 [−][8] 180 +4.55
C 2 H 3 CN 1 0.0017 3.3 × 10 [16] 1.8 × 10 [−][8] 180 +4.55
C 2 H 5 CN 1.7 0.0049 9.7 × 10 [16] 5.1 × 10 [−][8] 180 +4.55
HC(O)NH 2 [(] _[b]_ [)] 1.16 0.0077 1.6 × 10 [17] 8.2 × 10 [−][8] 180 +4.55
CH 3 OCH 3 1 <0.1 <2.0 × 10 [18] <1.1 × 10 [−][6] 180 +4.55
HDO 1 0.02 4.0 × 10 [17] 2.1 × 10 [−][7] 180 +4.55


Envelope CH 3 OH 1 1 4.1 × 10 [18] 2.2 × 10 [−][6] 110 +3.5
CH 3 OCHO 1 0.025 1.03 × 10 [17] 5.4 × 10 [−][8] 110 +3.5
C 2 H 5 OH 1.1 0.022 9.0 × 10 [16] 4.7 × 10 [−][8] 110 +3.5
CH 3 COCH 3 1 0.01 4.1 × 10 [16] 2.2 × 10 [−][8] 110 +3.5
a(CH 2 OH) 2 1 0.01 4.1 × 10 [16] 2.2 × 10 [−][8] 110 +3.5
_t_ -HCOOH [(] _[b]_ [)] 1 0.0033 1.367 × 10 [16] 7.2 × 10 [−][9] 110 +3.5
CH 3 CHO 1 0.00167 6.83 × 10 [15] 3.6 × 10 [−][9] 110 +3.5
CH 3 NCO 1.0 0.004 1.64 × 10 [16] 8.6 × 10 [−][9] 110 +3.5
C 2 H 3 CN 1 0.005 2.05 × 10 [16] 1.1 × 10 [−][8] 110 +3.5
C 2 H 5 CN 1.18 0.0118 4.8 × 10 [16] 2.6 × 10 [−][8] 110 +3.5
HC(O)NH 2 [(] _[b]_ [)] 1.03 0.01 4.2 × 10 [16] 2.2 × 10 [−][8] 110 +3.5
CH 3 OCH 3 1 <0.5 <2.1 × 10 [18] <1.1 × 10 [−][6] 110 +3.5
HDO 1 0.05 2.1 × 10 [17] 1.1 × 10 [−][7] 110 +3.5


**Notes.** ( _a_ ) Correction factor to the molecular column density to account for the contribution of torsionally or vibrationally excited states to the
partition function. All parameters are calculated for the given _T_ kin . [(] _[b]_ [)] The molecular abundance ( _X_ ) is calculated by _X_ = _N_ / _N_ (H 2 ). The values used
for _N_ (H 2 ) are given in Table 2. [(] _[c]_ [)] Velocity offset compared to the � lsr of −43.5 km s [−][1] .



marginally smaller extent. Similarly to CH 3 OH and other
O-bearing COMs, its peak is offset compared to the position of
the protostar, suggesting that it has a higher abundance at the
shock positions. This is confirmed by our modelling which measures the highest column density of HDO towards the _B_ -shock
position. In Fig. 5 we show the first moment map revealing the
kinematics of the HDO emitting gas. The velocity pattern of
HDO traced by its 1st moment map is very similar to that of
CH 3 OH (Paper I), and is consistent with rotational motions with
a velocity gradient roughly perpendicular to the outflow. This
confirms that the bulk of observed HDO emission originates
from the inner envelope.



**4. Discussion**


_4.1. Shock chemistry instead of a radiatively heated_
_envelope: precursor of a hot core_


In Paper I we investigate the physical properties of the collapsing core and the protostellar envelope of G328.2551-0.5321, and
estimate the current protostellar mass to be around 16 _M_ ⊙ with
an envelope mass of _M_ env ∼ 120 _M_ ⊙ . Therefore, the protostar is
very likely to form an O4-O5 type star with a final stellar mass of
∼50 _M_ ⊙ . While the bulk of the CH 3 OH emission is extended over
the inner envelope, at the close vicinity of the protostar, between


A57, page 9 of 16

A&A 632, A57 (2019)



**[Fig. 5.](http://dexter.edpsciences.org/applet.php?DOI=10.1051/0004-6361/201935226&pdf_id=0)** Zeroth ( _left_ ) and first ( _right_ ) moment map of the HDO ( _J_ = 3 3,1 −
4 2,2 ) line calculated between −55 and −35 km s [−][1] . The yellow star marks
the position of the dust continuum peak, and the black line shows the
v lsr at −43.5 km s [−][1] . The red and blue arrows show the orientation of
the outflow. The crosses mark the positions where the spectra were
extracted for this study. The beam is shown in the lower left corner.


a projected distance of 300 and 800 au, a rotational transition
from the vibrationally excited state of CH 3 OH at 334.436 GHz
is interpreted as tracing shocks due to accretion. The accretion
shocks imply the presence of an accretion disk, with a measured
orientation perpendicular within 10 [◦] to the axis of the outflow.
Since the accretion shocks on both the A and B positions are
extended, we study here the molecular composition of positions
that are the brightest in molecular emission along the extent of
the accretion shocks (Fig. 1).
Our results on the overall molecular composition of the gas
suggest a similar molecular richness compared to other highmass star forming regions hosting classical, radiatively heated
hot cores (Hatchell et al. 1998; Bisschop et al. 2007; Allen et al.
2017; Widicus Weaver et al. 2017). The COMs typical of hot
cores are detected towards G328.2551-0.5321, however, several
species are found to peak at the proposed accretion shocks rather
than the radiatively heated core towards the protostar and the
accretion disk. Inferred from CH 3 OH transitions, the bulk of
the gas in the inner envelope is at a temperature of _T_ kin = 110 K
with a relatively small extent, a radius of ∼1175 au, and 1450 au
for the most extended molecules, such as formamide and methyl
formate, respectively (Sect. 3.3). This extent is comparable to
the highest column density dust continuum emission detected
with a 1500 au radius. Considering a spherically symmetric centrally illuminated core, the expected dust temperature is between
83 and 157 K at a radius of 1000 au for the protostellar luminosity of 1.3 × 10 [4] _L_ ⊙ (Paper I) assuming radiative equilibrium
(Goldreich & Kwan 1974; Wolfire & Cassinelli 1986; Wilner
et al. 1995). This is broadly consistent with the temperature
estimate from the molecular line emission for the bulk of the
inner envelope. However, instead of a gradual warming up of
the gas due to the radiative heating of the protostar, we identify
localised spots of heated gas towards the accretion shocks with
_T_ kin = 180 K.
Since the source hosts a deeply embedded protostar, a radiatively heated inner core is expected towards the central position.
The most compact emission peaking on the protostar is traced
by vinyl and ethyl cyanides and has a radius of 900 au along
its minor axis. Assuming that molecules with a CN group outline the largest potential extent of a radiatively heated inner core
implies that this region must be very compact. Massive protostars or YSOs observed towards well studied high-mass star
forming regions exhibit a considerably more extended heated
inner region. For example Ginsburg et al. (2017) resolve the
region with high gas temperatures of _T_ - 100 K out to 5000 au
towards the hot cores of the W51 Main star forming region, and


A57, page 10 of 16



Bonfand et al. (2017) measure an extent of ∼3000 au towards
compact hot cores in the SgrB2 star forming region. Other hot
cores typically have an even larger extent of warm gas up to
0.1 pc (Hatchell et al. 1998; Kurtz et al. 2000; Cesaroni 2005).
In this context the current state of G328.2551-0.5321 is likely to
represent an earlier evolutionary stage compared to classical hot
cores, and where localised spots of heated gas due to accretion
shocks, hence a different heating mechanism leaves an observable imprint on the physical and chemical properties of the gas,
since the highest column densities of COMs originate from the
accretion shocks.
In the case of G328.2551-0.5321, based on the radiative equilibrium model, a ∼15× higher protostellar luminosity would
be required to heat the dust to _T_ - 100 K at a 5000 au radius.
Given the large expected final stellar mass of _M_ ⋆ ∼ 50 _M_ ⊙ of the
protostar in G328.2551-0.5321, it is very likely that the radiatively heated region is going to expand, turning this object into
a classical radiatively heated hot core with a comparably large
extent of heated gas as other known objects.
In addition to these physical arguments, the molecular composition could also be used to obtain an age estimate of the gas
(e.g. Viti et al. 2004; Caselli et al. 1993; Garrod et al. 2008;
Allen et al. 2018). Overall, we detect several molecules that
are suggested to be “first generation” COMs originating from
grain surface chemistry, based on the observational study of
Bisschop et al. (2007), such as CH 3 OH, C 2 H 5 OH, CH 3 OCHO,
HC(O)NH 2, CH 3 CN, and C 2 H 5 CN, although the spatial distribution of these molecules is resolved and shows significant
differences (see Sect. 4.3). Chemical age estimates for hot
cores have been based on molecular richness (Calcutt et al.
2014), ratios of chemically related species such as C 2 H 3 CN
and C 2 H 5 CN (e.g. Fontani et al. 2007; Zeng et al. 2018; Allen
et al. 2018), and dedicated physico-chemical modelling of hot
cores (Bonfand et al. 2019). The observed ratio of C 2 H 3 CN
and C 2 H 5 CN towards G328.2551-0.5321 is consistent with a
source that is still chemically young according to the chemical models by Caselli et al. (1993), although Charnley et al.
(1992) and Rodgers & Charnley (2001) suggest that additional
C 2 H 3 CN may form in gas phase reactions compared to those
models. In this context the overall chemical composition of
G328.2551-0.5321 resembles that of a young hot core with an
age <10 [5] yr, and is different from sources where chemistry is
driven by low velocity shocks and a high cosmic ray flux (Zeng
et al. 2018). Recent models by Allen et al. (2018), for example,
reproduce the observed abundances of cyanides using a short
warm-up phase, however, including a higher cosmic ionisation
rate towards one hot core in their sample was necessary. Therefore, it remains unclear how reliable such age estimates can
be, missing gas-phase reactions for the production of cyanides
as well as variations in physical conditions may impact age
estimates.


_4.2. Chemical differentiation at the innermost 1500 au scales_
_of the protostar: the O/N dichotomy_


One of the most striking results of our analysis is the observed
spatial dichotomy between O- and N-bearing COMs on scales
smaller than ∼1000 au observed towards the inner envelope.
While the O-bearing COMs are associated with the inner envelope and the shock spots, the N-bearing COMs are located in
the immediate vicinity of the protostar and the accretion disk
and show an extension in the direction of the outflow. Only formamide shows a more extended distribution, similar to that of
methyl formate.

T. Csengeri et al.: Search for high-mass protostars with ALMA revealed up to kilo-parsec scales (SPARKS). II.



Chemical differentiation, a.o., the O/N dichotomy, has been
first observed on larger scales towards Orion-KL (Caselli et al.
1993) as well as W3(OH) and W3(H 2 O) (Wyrowski et al. 1999)
originating from different physical components within these
star forming regions. On scales smaller than 3000 au this has
been further confirmed towards Orion-KL (Blake et al. 1996;
Wright et al. 1996; Widicus Weaver & Friedel 2012; Friedel &
Widicus Weaver 2012; Feng et al. 2015), as well as other high
−
mass star forming cores, such as G10.61 0.23 (Qin et al. 2010)
followed by several other examples, like AFGL2591 (JiménezSerra et al. 2012), NGC7538IRS9 (Öberg et al. 2013), G35.20,
G35.03 (Allen et al. 2017), and other sources like more evolved
MYSOs (Fayolle et al. 2015). G328.2551-0.5321 is, however, the
first example where we can study such a chemical differentiation
in a single, well resolved collapsing envelope, and associate the
observed molecules to their physical origin within the envelope.
This makes this source a favourable target to study the origin of
chemical differentiation as well as the emergence, and chemical
evolution of hot cores.
From the O-bearing COMs except methanol, methyl formate
has the largest column density, and its distribution resembles
that of the low-excitation CH 3 OH lines shown in more detail
in Paper I. This is, however, not surprising, since methyl formate is chemically related to methanol (Garrod & Herbst 2006).
The observed spatial distribution and its presence in a moderately warm gas phase may suggest grain surface production
and subsequent sublimation to the gas phase. Dimethyl ether,
a chemically related molecule to methyl formate remains, however, undetected up to a relative fraction of 10–50% compared
to methanol towards both the shock and the envelope positions,
despite having transitions in a range of upper energy levels similar to that of methyl formate. The models of Garrod & Herbst
(2006) predict a ratio between the gas phase fractional abundances of methyl formate and dimethyl ether between 0.24 and
17 at different times of their models, while observations suggest a molecular abundance of the same order of magnitude for
both species (Garrod & Herbst 2006; Cazaux et al. 2003; Taquet
et al. 2015). Our sensitivity is, however, not sufficient to detect
dimethyl ether at a similar column density compared to methyl
formate.
While methyl formate is abundant over the entire extent of
the inner envelope, the lowest column density O-bearing COMs,
such as ethanol and ethylene glycol are only detected towards
the accretion shocks first recognised by the torsionally excited
state CH 3 OH line in Paper I. The distribution of these primarily
O-bearing COMs is rather similar to the high excitation
methanol emission showing two peaks offset from the dust continuum and thus the central protostar (Fig. 4). Similarly to the
high excitation methanol lines, their velocity pattern shows the
two velocity components offset by ∼±4.5 km s [−][1] with respect to
the v lsr of the source. This allows us to conclude that due to the
change of physical conditions at the accretion shocks, heavier
O-bearing COMs outline well the existence of these shocks.
The N-bearing COMs, especially vinyl and ethyl cyanides,
are located towards the immediate vicinity of the protostar and
the accretion disk and show an extension in the direction of
the outflow. This suggests that they are also associated with the
innermost region of the outflow cavity, and potentially the accretion disk as also suggested for the vibrationally excited, � 7 = 1
state HC 3 N transition at 346.456 GHz in Paper I. Our results
provide the first direct evidence that, in contrast to O-bearing
COMs, molecules with a CN group peak on the innermost
few hundred au vicinity of the protostar likely associated with
regions of hot gas, which explains why some studies may find



them at elevated temperatures relative to the O-bearing COMs
(Qin et al. 2010; Widicus Weaver et al. 2017).
In fact models of photodissociation regions (PDRs) show
that the CN emission is sensitive to the UV radiation (e.g. Jansen
et al. 1995; Sternberg & Dalgarno 1995; van Zadelhoff et al.
2003; Walsh et al. 2010), which could explain the enhancement
of molecules with a CN group towards the central position associated with the accretion disk. For example, towards low-mass
embedded protostars CN has been proposed to trace the outflow cavity walls (Jørgensen 2004), while CN is also one of the
brightest tracers of protoplanetary disks (Guilloteau et al. 2014;
Cazzoletti et al. 2018), where it has been proposed to trace the
UV impacted upper warm molecular layers.
As for hot cores, complex cyanides have been modelled
by Allen et al. (2018), who suggest that a longer warm up
time together with a higher cosmic ray ionisation rate is necessary to reproduce the observed high abundance of vinyl and
ethyl cyanides. The chemical differentiation between O- and
N-bearing COMs observed toward the Orion Hot Core and Compact Ridge could also be explained with a different thermal
evaporation history (Caselli et al. 1993).
The case of formamide is somewhat in between these two
components, as this molecule shows strong emission towards the
dust peak while it is also present in the inner envelope, and shows
brighter emission towards at least one of the shock positions.
The observed difference compared to the other N-bearing COMs
may be explained by a different chemical formation pathway due
to its amide bond (−N−C( = O)−), which is also suggested by
the fact that it has been detected in various environments, such
as low-mass protostars (López-Sepulcre et al. 2015), also showing a ring around the central object (Coutens et al. 2016); hot
cores (Bisschop et al. 2007); and shocks (Mendoza et al. 2014).
Although we find a spatial correlation between methanol, methyl
formate and formamide, this does not provide enough constraints
on the chemical formation routes, that is a grain surface production and sublimation versus gas-phase formation scenario.
Therefore, the formation pathway of formamide remains unclear
(cf. Mendoza et al. 2014), in addition to the gas-phase reactions,
its grain surface production could be efficient (Garrod et al.
2008).


_4.3. Change of molecular composition at the accretion_
_shocks_


Based on the molecular emission and the kinetic temperatures
( _T_ kin ) derived from our LTE modelling, towards G328.25510.5321 we identify three distinct physical components hosting emission of COMs: (1) the inner envelope showing
extended emission of methyl formate, HDO and formamide with
_T_ kin = 110 K and an extent of ∼1000–1500 au _FWHM_ ; (2) the
shock spots with a higher kinetic temperature of _T_ kin = 160–
190 K together with an enhanced column density of O-bearing
COMs. Ethanol, acetone, and ethylene glycol show, for example, the highest column density and abundance towards the shock
positions. The kinematics of these species further confirms their
association with the accretion shocks as they show prominently
the two velocity components with ∼±4.5 km s [−][1] offset from
the source v lsr, similarly as the CH 3 OH � t = 1 line reported in
Paper I; (3) the closest vicinity of the protostar and its accretion
disk characterised by N-bearing COMs with a CN group, such
as vinyl and ethyl cyanide.
Since blending and dust opacity hinders us from a quantitative analysis of the molecular composition towards the central
position, here we compare the molecular abundances between


A57, page 11 of 16

A&A 632, A57 (2019)



10 [19]





10 [18]


10 [17]


10 [16]


**[Fig. 6.](http://dexter.edpsciences.org/applet.php?DOI=10.1051/0004-6361/201935226&pdf_id=0)** Molecular column densities obtained from the Weeds LTE modelling of COMs and HDO. The three positions (shock- _A_, - _B_ and the
position toward the inner envelope) are labelled in different colours.


the accretion shocks and the inner envelope. Towards the shock
positions we estimate a beam averaged H 2 column density,
_N_ (H 2 ), of 1.89–2.04 × 10 [24] cm [−][2] assuming a dust temperature,
_T_ d = _T_ kin of 180 K. In contrast, towards the inner envelope we
measure a somewhat lower kinetic temperature of 110 K and
_N_ (H 2 ) = 1.9 × 10 [24] cm [−][2] . This suggests that considering the
temperature variations, the H 2 column densities at the three positions are practically identical. Our modelling shows that the
abundance of CH 3 OH reaches up to 7.8 × 10 [−][6] −1.1 × 10 [−][5]
towards the accretion shocks, it is, however, up to a factor of
five lower towards the inner envelope with an abundance of
2.2 × 10 [−][6] . The other O-bearing COMs have a molecular abundance relative to H 2 between 1.6 × 10 [−][8] and 5.3 × 10 [−][7] towards
the shock positions, and an order of magnitude lower abundance range, between 3.6 × 10 [−][9] and 5.4 × 10 [−][8] towards the
position representing the bulk of the inner envelope. Compared
to the most abundant O-bearing COMs, such as methyl formate, the N-bearing COMs like vinyl and ethyl cyanide have
up to an order of magnitude lower abundance range, between
1.3 × 10 [−][8] and 5.1 × 10 [−][8] towards the shock positions. The
estimated abundances are also lower towards the inner envelope, and range between 8.6 × 10 [−][9] and 2.6 × 10 [−][8] for all the
N-bearing COMs. The molecular abundances of formamide are
of the order of 10 [−][8], at least one order of magnitude higher
than observed towards hot corino objects (López-Sepulcre et al.
2015), although our estimations are only based on practically one
transition and may not be robust for this molecule. The estimated
molecular abundances are listed in Table 4.
We compare the molecular composition towards the shock
positions and the inner envelope in Fig. 6. In general, we find that
the molecular composition of the two shock spots are broadly
consistent with each other, and show very similar molecular
abundances for most species. However, the observed molecular abundance of COMs with respect to H 2 towards the inner
envelope is found to be several factors lower compared to the


A57, page 12 of 16



0.02


0.01


0.00


−0.01


−0.02


−0.03


Molecule


**[Fig.](http://dexter.edpsciences.org/applet.php?DOI=10.1051/0004-6361/201935226&pdf_id=0)** **7.** Relative molecular abundances with respect to that of the
_B_ -shock position. Positive means a relative decrease of certain species
compared to the same molecular abundance derived at the _B_ -shock
position.


shock spots. After methanol, methyl formate is the second most
abundant molecule both in the shock spots and in the envelope.
Towards the position of the inner envelope, it shows, however, a
much higher relative abundance relative to CH 3 OH.
The change of molecular abundances normalised to CH 3 OH
with respect to the _B_ shock position is shown in Fig. 7. This further suggests that the relative change of molecular composition
between the _A_ and _B_ shock spots is small, thus their molecular composition is similar. The molecular composition towards
the inner envelope is, however, considerably different, in particular the relative fraction to CH 3 OH from methyl formate,
ethanol and acetone is smaller in the inner envelope than at the
B shock position, suggesting that the gas becomes enriched in
these O-bearing COMs in the shocks.
HDO has a similar abundance towards the inner envelope
and the accretion shocks, suggesting that not only the accretion
shocks but also the inner envelope has a significant contribution
to the overall amount of HDO. Its relative fraction compared to
methanol changes, however, significantly and becomes considerably higher towards the inner envelope. This is simply because
the methanol abundance is lower towards the inner envelope
compared to the accretion shocks.
In contrast, the cyanides show a relatively moderate change
of abundance ratio between the envelope and the accretion
shocks. The C 2 H 5 CN/C 2 H 3 CN abundance ratio is 2.4−3.4
towards all positions, suggesting that saturated nitriles are in general more abundant than unsaturated ones, which is expected
for hot cores. Saturated molecules are chemically more stable
which may explain their observed higher abundance. Chemical models predict that (e.g. Caselli et al. 1993) C 2 H 3 CN forms
from C 2 H 5 CN through ion-molecule reactions in the gas phase,
therefore their ratio has been suggested as a tracer for the chemical age of hot cores. For example Fontani et al. (2007) find
C 2 H 5 CN/C 2 H 3 CN abundance ratios around 2.0−3.3 towards
six classical hot cores and conclude that their age is less

T. Csengeri et al.: Search for high-mass protostars with ALMA revealed up to kilo-parsec scales (SPARKS). II.



than 10 [5] yr. Such a ratio is also consistent with that found
towards Orion-KL and SgrB2(N) (Zeng et al. 2018), however
towards SgrB2(N) high angular resolution measurements resolving the individual hot cores suggest very different ratios and find
C 2 H 5 CN/C 2 H 3 CN = 5−17. The evolutionary sequence towards
SgrB2(N) based on the C 2 H 5 CN/C 2 H 3 CN ratio is, however, contradicting the results of dedicated physico-chemical modelling
(Bonfand et al. 2019) suggesting that either the chemical network
lacks some reactions or that other physical parameters such as
the stellar mass and ionisation rate may have a stronger impact
on the chemical evolution than the age.
Altogether this quantitatively demonstrates a change in the
molecular composition of COMs between the envelope and the
accretion shocks, while Fig. 4 shows that also the central position
is likely to have an even more drastic change of molecular composition. The origin of this different chemistry observed towards
the central position, the accretion shocks and the inner envelope needs to be understood. As discussed earlier, the chemistry
of N-bearing COMs with a CN group may be influenced by a
strong change of physical conditions in the immediate vicinity
of the protostar, such as UV radiation as well as the gas being
exposed to a heating source for a longer time-scale compared
to the gas within the cold envelope. A different thermal history of the gas, together with different initial conditions for the
chemistry in the envelope due to thermal or non-thermal desorption processes could be responsible for the observed spatial
segregation of molecules.


_4.4. Distribution of deuterated water_


HDO from cold and hot gas has been detected towards classical
hot cores both at low and high angular resolution (e.g. Jacq et al.
1990; van der Tak et al. 2006; Liu et al. 2013). Here we resolve for
the first time HDO emission towards the inner regions of a highmass protostellar envelope and find that it is associated with the
inner envelope. Its velocity field is axisymmetric roughly perpendicular to the outflow direction consistent with a rotational
pattern also observed in several CH 3 OH transitions. A similar
rotational pattern has also been observed towards AFGL 2591,
where, based on its correlation with the continuum structure, it
has been proposed to trace a circumstellar disk (van der Tak et al.
2006). In addition, HDO shows an enhanced molecular column
density towards at least one of the shock positions, and similarly
to the O-bearing COMs, its emission does not show a prominent
peak on the position of the protostar.
Since we only have one observed transition, the estimated
parameters of HDO rely on the assumption that the emitting
gas has the same rotational temperature as CH 3 OH, which is
180 K for the shock position and 110 K on the position of the
inner envelope. This gives an estimate of the HDO column
density of 2.1 and 4.0 × 10 [17] cm [−][2] towards the inner envelope
and the shock position, respectively. The HDO column density is relatively similar towards the shock spots and the inner
envelope, however its relative fraction compared to CH 3 OH is
higher in the envelope than in the accretion shocks by a factor of 2. As a comparison, towards G34.26+0.15, one of the
classical hot cores, Coutens et al. (2014) estimate an HDO column density of ∼1.6 × 10 [16] cm [−][2] with an excitation temperature
of ∼79 K towards the inner regions of the hot core. Our estimates give an HDO abundance of _X_ (HDO) = 1.1–2.1 × 10 [−][7]
relative to H 2, which is of the same order of magnitude as Liu
et al. (2011) find for the _T_ - 100 K regime for G34.26+0.15, and
what Kulczak-Jastrze¸bska (2017) estimates for the inner region
of other classical hot cores.



The kinetic temperature of the inner envelope is mainly estimated based on methanol and methyl formate, and because HDO
shows a similar spatial distribution to these species, it is reasonable to assume that it is also associated with gas close to,
or just above the ice sublimation temperature, _T_ = 90–190 K.
This would suggest that the observed HDO emission likely originates from the evaporation of the grain surfaces, expected at
≳100 K, (Fraser et al. 2001). This is also consistent with the
abundance jump assumed by modelling of single dish (low resolution) observations for classical hot cores, as well as low- to
intermediate mass Class 0 protostars (Comito et al. 2003; Parise
et al. 2005; Liu et al. 2013).
Our detection of HDO from the inner envelope is intriguing,
because chemical models predict a decrease in the abundance
of water, and therefore HDO towards the inner 1000 au of hot
cores (Coutens et al. 2014), with the destruction of HDO being
even more efficient than the destruction of H 2 O. In comparison
to our results, both the location and the relatively high abundance
of HDO suggest that H 2 O, and HDO destruction has not been
efficient in this source yet, providing further evidence that the
source is chemically young.


**5. Conclusions**


Using high angular-resolution observations with ALMA, we
investigate the physical and chemical structure of the massive
envelope of a high-mass protostar, G328.2551-0.5321. We identify emission from 10 COMs using LTE modelling of a 7.5 GHz
non continuous spectral coverage around 345 GHz, and find
that its overall molecular composition shows a similar richness
compared to other high-mass star forming regions.
Comparing to recent observations of hot cores, the radiatively heated inner region is the most compact observed to date
with a radius ( _R_ 90% ) of <900 au estimated from vinyl and ethyl
cyanides. Inferred from CH 3 OH transitions, the bulk of the gas
in the inner envelope is at a temperature of _T_ kin = 110 K, allowing us to witness the emergence of accretion shocks suggesting
a different heating mechanism compared to the classical, radiatively heated hot cores. However, given the ∼50 _M_ ⊙ expected
final stellar mass, G328.2551-0.5321 is likely to represent an
earlier evolutionary stage compared to classical hot cores.
For the first time, we spatially resolve on <1000 au scales
within a single collapsing envelope the chemical differentiation
of O-bearing COMs versus N-bearing COMs, in particular those
with a CN group. The O-bearing COMs, such as ethanol, acetone, ethylene glycol and acetaldehyde have an increased abundance towards the two localised positions of accretion shocks
with _T_ kin = 180 K. These transitions show the same velocity pattern as the CH 3 OH � _t_ = 1 emission at 334.436 GHz reported
in Paper I, representing the accretion shocks. Emission from
other COMs, such as methanol, methyl formate, and formamide
is found towards an extended region with a radius ( _R_ 90% ) of
1175−1450 au and _T_ kin = 110 K.
We image and spatially resolve emission from the HDO
( _J_ = 3 3,1 –4 2,2 ) line. It is extended over the inner envelope and
its velocity pattern is consistent with a velocity gradient roughly
perpendicular to the outflow, likely corresponding to the rotational pattern of the inner envelope. Its extent is comparable
to that of methyl formate with _T_ kin = 110 K. The high HDO
column density suggests that the destruction of water has not
been efficient towards this source since HDO is expected to be
destroyed in the inner regions of classical hot cores.
We identify three physical components within the envelope, a
compact inner region representing the immediate vicinity of the


A57, page 13 of 16

A&A 632, A57 (2019)



protostar and its accretion disk, the inner envelope, and the accretion shocks within the envelope. We quantitatively show that
the molecular composition of COMs towards the two accretion
shocks is similar, while there is a change of molecular composition among COMs compared to the inner envelope. In addition,
we qualitatively show that the central regions are particularly
apparent in N-bearing COMs with a CN group, such as vinyl and
ethyl cyanide that could explain the typically observed higher
temperatures found with these molecules towards classical hot

cores.


_Acknowledgements._ This paper makes use of the ALMA data: ADS/JAO.ALMA
2013.1.00960.S. ALMA is a partnership of ESO (representing its member states),
NSF (USA), and NINS (Japan), together with NRC (Canada), NSC and ASIAA
(Taiwan), and KASI (Republic of Korea), in cooperation with the Republic of
Chile. The Joint ALMA Observatory is operated by ESO, AUI/NRAO, and
NAOJ. T.Cs. acknowledges support from the Deutsche Forschungsgemeinschaft,
DFG via the SPP (priority programme) 1573 “Physics of the ISM”.


**References**


Allen, V., van der Tak, F. F. S., Sánchez-Monge, Á., Cesaroni, R., & Beltrán,
[M. T. 2017, A&A, 603, A133](http://linker.aanda.org/10.1051/0004-6361/201935226/1)
[Allen, V., van der Tak, F. F. S., & Walsh, C. 2018, A&A, 616, A67](http://linker.aanda.org/10.1051/0004-6361/201935226/2)
[Balucani, N., Ceccarelli, C., & Taquet, V. 2015, MNRAS, 449, L16](http://linker.aanda.org/10.1051/0004-6361/201935226/3)
Beltrán, M. T., Codella, C., Viti, S., Neri, R., & Cesaroni, R. 2009, ApJ, 690,
[L93](http://linker.aanda.org/10.1051/0004-6361/201935226/4)
Bisschop, S. E., Jørgensen, J. K., van Dishoeck, E. F., & de Wachter, E. B. M.
[2007, A&A, 465, 913](http://linker.aanda.org/10.1051/0004-6361/201935226/5)
[Blake, G. A., Sutton, E. C., Masson, C. R., & Phillips, T. G. 1987, ApJ, 315, 621](http://linker.aanda.org/10.1051/0004-6361/201935226/6)
[Blake, G. A., Mundy, L. G., Carlstrom, J. E., et al. 1996, ApJ, 472, L49](http://linker.aanda.org/10.1051/0004-6361/201935226/7)
Bonfand, M., Belloche, A., Menten, K. M., Garrod, R. T., & Müller, H. S. P.
[2017, A&A, 604, A60](http://linker.aanda.org/10.1051/0004-6361/201935226/8)
[Bonfand, M., Belloche, A., Garrod, R. T., et al. 2019, A&A, 628, A27](http://linker.aanda.org/10.1051/0004-6361/201935226/9)
[Brouillet, N., Despois, D., Baudry, A., et al. 2013, A&A, 550, A46](http://linker.aanda.org/10.1051/0004-6361/201935226/10)
[Calcutt, H., Viti, S., Codella, C., et al. 2014, MNRAS, 443, 3157](http://linker.aanda.org/10.1051/0004-6361/201935226/11)
[Caselli, P., Hasegawa, T. I., & Herbst, E. 1993, ApJ, 408, 548](http://linker.aanda.org/10.1051/0004-6361/201935226/12)
[Cazaux, S., Tielens, A. G. G. M., Ceccarelli, C., et al. 2003, ApJ, 593, L51](http://linker.aanda.org/10.1051/0004-6361/201935226/13)
Cazzoletti, P., van Dishoeck, E. F., Visser, R., Facchini, S., & Bruderer, S. 2018,

[A&A, 609, A93](http://linker.aanda.org/10.1051/0004-6361/201935226/14)
[Cesaroni, R. 2005, Ap&SS, 295, 5](http://linker.aanda.org/10.1051/0004-6361/201935226/15)
[Charnley, S. B. 2001, ApJ, 562, L99](http://linker.aanda.org/10.1051/0004-6361/201935226/16)
[Charnley, S. B., Tielens, A. G. G. M., & Millar, T. J. 1992, ApJ, 399, L71](http://linker.aanda.org/10.1051/0004-6361/201935226/17)
[Churchwell, E. 2002, ARA&A, 40, 27](http://linker.aanda.org/10.1051/0004-6361/201935226/18)
[Comito, C., Schilke, P., Gerin, M., et al. 2003, A&A, 402, 635](http://linker.aanda.org/10.1051/0004-6361/201935226/19)
[Coutens, A., Vastel, C., Hincelin, U., et al. 2014, MNRAS, 445, 1299](http://linker.aanda.org/10.1051/0004-6361/201935226/20)
[Coutens, A., Jørgensen, J. K., van der Wiel, M. H. D., et al. 2016, A&A, 590, L6](http://linker.aanda.org/10.1051/0004-6361/201935226/21)
[Csengeri, T., Urquhart, J. S., Schuller, F., et al. 2014, A&A, 565, A75](http://linker.aanda.org/10.1051/0004-6361/201935226/22)
[Csengeri, T., Bontemps, S., Wyrowski, F., et al. 2017, A&A, 601, A60](http://linker.aanda.org/10.1051/0004-6361/201935226/23)
[Csengeri, T., Bontemps, S., Wyrowski, F., et al. 2018, A&A, 617, A89](http://linker.aanda.org/10.1051/0004-6361/201935226/24)
[Endres, C. P., Schlemmer, S., Schilke, P., Stutzki, J., & Müller, H. S. P. 2016, J.](http://linker.aanda.org/10.1051/0004-6361/201935226/25)
[Mol. Spectr., 327, 95](http://linker.aanda.org/10.1051/0004-6361/201935226/25)
Fayolle, E. C., Öberg, K. I., Garrod, R. T., van Dishoeck, E. F., & Bisschop, S. E.
[2015, A&A, 576, A45](http://linker.aanda.org/10.1051/0004-6361/201935226/26)
[Feng, S., Beuther, H., Henning, T., et al. 2015, A&A, 581, A71](http://linker.aanda.org/10.1051/0004-6361/201935226/27)
[Fontani, F., Pascucci, I., Caselli, P., et al. 2007, A&A, 470, 639](http://linker.aanda.org/10.1051/0004-6361/201935226/28)
Fraser, H. J., Collings, M. P., McCoustra, M. R. S., & Williams, D. A. 2001,

[MNRAS, 327, 1165](http://linker.aanda.org/10.1051/0004-6361/201935226/29)
[Friedel, D. N., & Widicus Weaver, S. L. 2012, ApJS, 201, 17](http://linker.aanda.org/10.1051/0004-6361/201935226/30)
[Garay, G., & Lizano, S. 1999, PASP, 111, 1049](http://linker.aanda.org/10.1051/0004-6361/201935226/31)
[Garrod, R. T., & Herbst, E. 2006, A&A, 457, 927](http://linker.aanda.org/10.1051/0004-6361/201935226/32)


A57, page 14 of 16



[Garrod, R. T., & Widicus Weaver, S. L. 2013, Chem. Rev., 113, 8939](http://linker.aanda.org/10.1051/0004-6361/201935226/33)
[Garrod, R. T., Widicus Weaver, S. L., & Herbst, E. 2008, ApJ, 682, 283](http://linker.aanda.org/10.1051/0004-6361/201935226/34)
[Ginsburg, A., Goddi, C., Kruijssen, J. M. D., et al. 2017, ApJ, 842, 92](http://linker.aanda.org/10.1051/0004-6361/201935226/35)
[Goldreich, P., & Kwan, J. 1974, ApJ, 189, 441](http://linker.aanda.org/10.1051/0004-6361/201935226/36)
[Guilloteau, S., Simon, M., Piétu, V., et al. 2014, A&A, 567, A117](http://linker.aanda.org/10.1051/0004-6361/201935226/37)
[Hatchell, J., Thompson, M. A., Millar, T. J., & MacDonald, G. H. 1998, A&AS,](http://linker.aanda.org/10.1051/0004-6361/201935226/38)
[133, 29](http://linker.aanda.org/10.1051/0004-6361/201935226/38)
[Herbst, E., & van Dishoeck, E. F. 2009, ARA&A, 47, 427](http://linker.aanda.org/10.1051/0004-6361/201935226/39)
[Jaber, A. A., Ceccarelli, C., Kahane, C., & Caux, E. 2014, ApJ, 791, 29](http://linker.aanda.org/10.1051/0004-6361/201935226/40)
[Jacq, T., Walmsley, C. M., Henkel, C., et al. 1990, A&A, 228, 447](http://linker.aanda.org/10.1051/0004-6361/201935226/41)
[Jansen, D. J., Spaans, M., Hogerheijde, M. R., & van Dishoeck, E. F. 1995, A&A,](http://linker.aanda.org/10.1051/0004-6361/201935226/42)
[303, 541](http://linker.aanda.org/10.1051/0004-6361/201935226/42)
Jiménez-Serra, I., Zhang, Q., Viti, S., Martín-Pintado, J., & de Wit, W.-J. 2012,

[ApJ, 753, 34](http://linker.aanda.org/10.1051/0004-6361/201935226/43)
[Jørgensen, J. K. 2004, A&A, 424, 589](http://linker.aanda.org/10.1051/0004-6361/201935226/44)
[Kulczak-Jastrze¸bska, M. 2017, ApJ, 835, 121](http://linker.aanda.org/10.1051/0004-6361/201935226/45)
Kurtz, S., Cesaroni, R., Churchwell, E., Hofner, P., & Walmsley, C. M. 2000,

[Protostars and Planets IV (Tucson, AZ: University of Arizona Press), 299](http://linker.aanda.org/10.1051/0004-6361/201935226/46)
[Liu, F.-C., Parise, B., Kristensen, L., et al. 2011, A&A, 527, A19](http://linker.aanda.org/10.1051/0004-6361/201935226/47)
[Liu, F.-C., Parise, B., Wyrowski, F., Zhang, Q., & Güsten, R. 2013, A&A, 550,](http://linker.aanda.org/10.1051/0004-6361/201935226/48)
[A37](http://linker.aanda.org/10.1051/0004-6361/201935226/48)
[López-Sepulcre, A., Jaber, A. A., Mendoza, E., et al. 2015, MNRAS, 449, 2438](http://linker.aanda.org/10.1051/0004-6361/201935226/49)
Maret, S., Hily-Blant, P., Pety, J., Bardeau, S., & Reynier, E. 2011, [A&A,](http://linker.aanda.org/10.1051/0004-6361/201935226/50) 526,
[A47](http://linker.aanda.org/10.1051/0004-6361/201935226/50)

[Maud, L. T., Hoare, M. G., Galván-Madrid, R., et al. 2017, MNRAS, 467, L120](http://linker.aanda.org/10.1051/0004-6361/201935226/51)
[Mendoza, E., Lefloch, B., López-Sepulcre, A., et al. 2014, MNRAS, 445, 151](http://linker.aanda.org/10.1051/0004-6361/201935226/52)
[Millar, T. J., Herbst, E., & Charnley, S. B. 1991, ApJ, 369, 147](http://linker.aanda.org/10.1051/0004-6361/201935226/53)
[Mookerjea, B., Casper, E., Mundy, L. G., & Looney, L. W. 2007, ApJ, 659, 447](http://linker.aanda.org/10.1051/0004-6361/201935226/54)
[Müller, H. S. P., Schlöder, F., Stutzki, J., & Winnewisser, G. 2005, J. Mol. Struct.,](http://linker.aanda.org/10.1051/0004-6361/201935226/55)
[742, 215](http://linker.aanda.org/10.1051/0004-6361/201935226/55)
[Öberg, K. I., Boamah, M. D., Fayolle, E. C., et al. 2013, ApJ, 771, 95](http://linker.aanda.org/10.1051/0004-6361/201935226/56)
[Ordu, M. H., Zingsheim, O., Belloche, A., et al. 2019, A&A, 629, A72](http://linker.aanda.org/10.1051/0004-6361/201935226/57)
[Ossenkopf, V., & Henning, T. 1994, A&A, 291, 943](http://linker.aanda.org/10.1051/0004-6361/201935226/58)
[Oya, Y., Sakai, N., Watanabe, Y., et al. 2017, ApJ, 837, 174](http://linker.aanda.org/10.1051/0004-6361/201935226/59)
[Palau, A., Fuente, A., Girart, J. M., et al. 2011, ApJ, 743, L32](http://linker.aanda.org/10.1051/0004-6361/201935226/60)
[Palau, A., Walsh, C., Sánchez-Monge, Á., et al. 2017, MNRAS, 467, 2723](http://linker.aanda.org/10.1051/0004-6361/201935226/61)
[Parise, B., Caux, E., Castets, A., et al. 2005, A&A, 431, 547](http://linker.aanda.org/10.1051/0004-6361/201935226/62)
Pickett, H. M., Poynter, R. L., Cohen, E. A., et al. 1998, J. Quant. [Spectr.](http://linker.aanda.org/10.1051/0004-6361/201935226/63) Rad.
[Transf., 60, 883](http://linker.aanda.org/10.1051/0004-6361/201935226/63)
[Qin, S.-L., Wu, Y., Huang, M., et al. 2010, ApJ, 711, 399](http://linker.aanda.org/10.1051/0004-6361/201935226/64)
[Rodgers, S. D., & Charnley, S. B. 2001, ApJ, 546, 324](http://linker.aanda.org/10.1051/0004-6361/201935226/65)
[Sakai, N., Sakai, T., Hirota, T., et al. 2014, Nature, 507, 78](http://linker.aanda.org/10.1051/0004-6361/201935226/66)
[Sánchez-Monge, Á., Cesaroni, R., Beltrán, M. T., et al. 2013, A&A, 552, L10](http://linker.aanda.org/10.1051/0004-6361/201935226/67)
[Sánchez-Monge, Á., Schilke, P., Schmiedeke, A., et al. 2017, A&A, 604, A6](http://linker.aanda.org/10.1051/0004-6361/201935226/68)
[Schuller, F., Menten, K. M., Contreras, Y., et al. 2009, A&A, 504, 415](http://linker.aanda.org/10.1051/0004-6361/201935226/69)
[Sternberg, A., & Dalgarno, A. 1995, ApJS, 99, 565](http://linker.aanda.org/10.1051/0004-6361/201935226/70)
[Taquet, V., López-Sepulcre, A., Ceccarelli, C., et al. 2015, ApJ, 804, 81](http://linker.aanda.org/10.1051/0004-6361/201935226/71)
[van der Tak, F. F. S., Walmsley, C. M., Herpin, F., & Ceccarelli, C. 2006, A&A,](http://linker.aanda.org/10.1051/0004-6361/201935226/72)
[447, 1011](http://linker.aanda.org/10.1051/0004-6361/201935226/72)
van Zadelhoff, G.-J., Aikawa, Y., Hogerheijde, M. R., & van Dishoeck, E. F.
[2003, A&A, 397, 789](http://linker.aanda.org/10.1051/0004-6361/201935226/73)
Viti, S., Collings, M. P., Dever, J. W., McCoustra, M. R. S., & Williams, D. A.
[2004, MNRAS, 354, 1141](http://linker.aanda.org/10.1051/0004-6361/201935226/74)
Walmsley, C. M., & Schilke, P. 1993, Dust and [Chemistry](http://linker.aanda.org/10.1051/0004-6361/201935226/75) in Astronomy, eds.
T. J. Millar, & D. A. Williams (Boca Raton: CRC Press), 37
[Walsh, C., Millar, T. J., & Nomura, H. 2010, ApJ, 722, 1607](http://linker.aanda.org/10.1051/0004-6361/201935226/76)
[Widicus Weaver, S. L., & Friedel, D. N. 2012, ApJS, 201, 16](http://linker.aanda.org/10.1051/0004-6361/201935226/77)
[Widicus Weaver, S. L., Laas, J. C., Zou, L., et al. 2017, ApJS, 232, 3](http://linker.aanda.org/10.1051/0004-6361/201935226/78)
[Wilner, D. J., Welch, W. J., & Forster, J. R. 1995, ApJ, 449, L73](http://linker.aanda.org/10.1051/0004-6361/201935226/79)
[Wolfire, M. G., & Cassinelli, J. P. 1986, ApJ, 310, 207](http://linker.aanda.org/10.1051/0004-6361/201935226/80)
[Wright, M. C. H., Plambeck, R. L., & Wilner, D. J. 1996, ApJ, 469, 216](http://linker.aanda.org/10.1051/0004-6361/201935226/81)
Wyrowski, F., Schilke, P., Walmsley, C. M., & Menten, K. M. 1999, ApJ, 514,
[L43](http://linker.aanda.org/10.1051/0004-6361/201935226/82)
[Zeng, S., Jiménez-Serra, I., Rivilla, V. M., et al. 2018, MNRAS, 478, 2962](http://linker.aanda.org/10.1051/0004-6361/201935226/83)

T. Csengeri et al.: Search for high-mass protostars with ALMA revealed up to kilo-parsec scales (SPARKS). II.


**Appendix A:** **Spectra obtained towards the** _**A**_ **-shock position, and the inner envelope**


**[Fig. A.1.](http://dexter.edpsciences.org/applet.php?DOI=10.1051/0004-6361/201935226&pdf_id=0)** Same as Fig. 3 extracted towards the _A_ -shock position.


A57, page 15 of 16

A&A 632, A57 (2019)


**[Fig. A.2.](http://dexter.edpsciences.org/applet.php?DOI=10.1051/0004-6361/201935226&pdf_id=0)** Same as Fig. 3 extracted towards a position of the inner envelope.


A57, page 16 of 16


</paper>

## Items to check

```json
[
 {
  "path": "science.targets[0].coordinates.evidence[0]",
  "value": "phase centre (J2000) 15h58m00.05s, −53°57′57.8″",
  "failed_quote": "located at a distance of 2.5 +0.7/−0.5 kpc"
 },
 {
  "path": "science.targets[0].coordinates.evidence[1]",
  "value": "phase centre (J2000) 15h58m00.05s, −53°57′57.8″",
  "failed_quote": "The phase centre was (α, δ) J2000 = (15h58m00.05s, −53°57′57.″8)"
 },
 {
  "path": "science.targets[0].redshift_or_distance.evidence[0]",
  "value": "2.5 (+0.7/-0.5) kpc",
  "failed_quote": "located at a distance of 2.5 +0.7/−0.5 kpc"
 },
 {
  "path": "science.targets[0].redshift_or_distance.evidence[1]",
  "value": "2.5 (+0.7/-0.5) kpc",
  "failed_quote": "The phase centre was (α, δ) J2000 = (15h58m00.05s, −53°57′57.″8)"
 },
 {
  "path": "data.other_facilities[0].provided.evidence[0]",
  "value": "870 µm survey that identified the source",
  "failed_quote": "It was identified by Csengeri et al. (2017) based on the APEX Telescope Large Area Survey of the Galaxy (ATLASGAL)"
 },
 {
  "path": "software[1].used_for.evidence[0]",
  "value": "spectra processing and continuum subtraction",
  "failed_quote": "The spectra were then exported to GILDAS/CLASS for further processing."
 },
 {
  "path": "analysis_steps[3].fitting.evidence[0]",
  "value": "manual iterative fitting",
  "failed_quote": "(no quote given)"
 },
 {
  "path": "analysis_steps[4].fitting.evidence[0]",
  "value": "2D Gaussian",
  "failed_quote": "(no quote given)"
 }
]
```
