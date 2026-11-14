# Repair task for a Claude Code subagent

A methods card has evidence quotes that were not found verbatim in the paper. Below are the rules, the paper, and the failing items. Write ONE JSON object, nothing else, of the form {"repairs": [{"path": ..., "found": true|false, "loc": ..., "quote": ...}, ...]} with one entry per item (path unchanged) to:

    C:\Users\adama\alma-corpus\cards\2024MNRAS.530..597B\gemini4argon\repair_reply.txt

Use the Write tool for that file. Copy each quote character for character from the paper text below; a returned quote is checked mechanically and dropped if it is not in the paper. Do not read any other file, do not run commands, and do not change anything else. Reply with one line when done.

---

## Rules

You check evidence quotes for a methods card extracted from an astronomy paper. Some quotes could not be found verbatim in the paper text, and some stated values came without a quote. For each item: find the passage in the paper that supports the value and copy it VERBATIM (same words and order, at most 40 words; LaTeX markup may be dropped) with its loc (section heading, "abstract", "Table N" or "Figure N caption"). If the paper does not support the value, return found = false and leave quote and loc empty. Use only the paper text. Return one entry per item, with the item's path unchanged.

## Paper

<paper>
MNRAS **000**, 1–14 (2024) Preprint 9 April 2024 Compiled using MNRAS L [A] TEX style file v3.0

## **Cloud-Scale Molecular Gas Properties of the Antennae Merger: A** **Comparative Study with PHANGS-ALMA Galaxies and NGC 3256**


Nathan Brunetti, [1] Christine D. Wilson, [1] _[★]_ Hao He, [1] Jiayi Sun, [1] _[,]_ [2] Adam K. Leroy, [3] Erik Rosolowsky, [4]

Ashley Bemis, [5] Frank Bigiel, [6] Brent Groves, [7] Toshiki Saito, [8] and Eva Schinnerer [9]

1 _Department of Physics and Astronomy, McMaster University, Hamilton, ON L8S 4M1, Canada_
2 _Canadian Institute for Theoretical Astrophysics (CITA), University of Toronto, 60 St George Street, Toronto, ON M5S 3H8, Canada_
3 _Department of Astronomy, The Ohio State University, 140 West 18th Avenue, Columbus, OH 43210, USA;_
_Center for Cosmology and Astroparticle Physics (CCAPP), 191 West Woodruff Avenue, Columbus, OH 43210, USA_
4 _Department of Physics, University of Alberta, Edmonton, AB T6G 2E1, Canada_
5 _Leiden Observatory, Leiden University, PO Box 9513, 2300 RA Leiden, The Netherlands_
6 _Argelander-Institut für Astronomie, Universität Bonn, Auf dem Hügel 71, D-53121 Bonn, Germany_
7 _International Centre for Radio Astronomy Research, University of Western Australia, 35 Stirling Highway, Crawley, WA 6009, Australia_
8 _National Astronomical Observatory of Japan, 2-21-1 Osawa, Mitaka, Tokyo, 181-8588, Japan_
9 _Max-Planck-Institut für Astronomie, Königstuhl 17, D-69117, Heidelberg, Germany_


Accepted XXX. Received YYY; in original form ZZZ


**ABSTRACT**

We present observations of the central 9 kpc of the Antennae merger (NGC 4038/9) at 55 pc resolution in the CO (2–1) line
obtained with the Atacama Large Millimeter/submillimeter Array (ALMA). We use a pixel-based analysis to compare the
gas properties in the Antennae to those in 70 nearby spiral galaxies from the PHANGS-ALMA survey, as well as the merger
and nearest luminous infrared galaxy NGC 3256. Compared to PHANGS-ALMA galaxies at matched spatial resolution, the
molecular gas in the Antennae exhibits some of the highest surface densities, velocity dispersions, peak brightness temperatures,
and turbulent pressures. However, the virial parameters in the Antennae are consistent with many of the PHANGS-ALMA
galaxies. NGC 3256 has similar gas surface densities but higher nuclear velocity dispersions than the Antennae, as well as higher
system-wide peak brightness temperatures and virial parameters. NGC 3256 is at a later stage in the merging process than the
Antennae, which may result in more intense merger-driven gas flows that could drive up the turbulence in the gas. The high virial
parameters in NGC 3256 may indicate that this increased turbulence is suppressing future star formation as NGC 3256 moves
out of the starburst phase. In comparison, the relatively normal virial parameters in the Antennae may imply that it is about to
undergo a new burst of star formation.



**Key words:** ISM: kinematics and dynamics – galaxies: interactions
– galaxies: ISM – galaxies: nuclei – galaxies: star formation – submillimetre: ISM.


**1** **INTRODUCTION**


From the spatial correlation of molecular gas and recent star formation seen in galaxies throughout the universe, we know that stars
form from molecular gas. The efficiency with which molecular gas
is converted into stars has been observed to be fairly similar at subkiloparsec scales across many nearby spiral galaxies (Leroy et al.
2008). However, the global star formation efficiency (SFE) (calculated from the star formation rate (SFR) and molecular gas mass
(M mol ) via SFE = SFR/M mol ) for the most actively star-forming
galaxies deviates from what is observed in more normal spiral galaxies (e.g. Kennicutt & de los Reyes 2021). Observations of these
different star-forming regimes, done at comparable angular resolutions and sensitivities and using the same tracer, will allow us to
understand what causes this difference in star formation efficiency.
Both global and kiloparsec-scale observations of spiral galaxies
and starbursts have revealed the difference in SFEs but not the cause

(e.g. de los Reyes & Kennicutt 2019; Wilson et al. 2019; Kennicutt &
de los Reyes 2021), so observations of the molecular gas at smaller


© 2024 The Authors



scales are the natural next step. Many nearby spiral galaxies have been
observed in molecular gas at scales around 100 pc and even smaller
(e.g. Schinnerer et al. 2013; Leroy et al. 2021b), but the relative
rarity of and distance to starbursting galaxies have precluded similar
observations. Brunetti et al. (2021) and Brunetti & Wilson (2022)
presented the highest spatial-resolution observations (∼100 pc) of
molecular gas in NGC 3256, a luminous infrared galaxy (LIRG) and
actively star-forming merger. Comparisons to the Physics at High Angular resolution in Nearby GalaxieS with ALMA (PHANGS-ALMA)
homogeneous survey of 70 nearby spiral galaxies (Sun et al. 2020;
Leroy et al. 2021b) at matched resolution revealed that the molecular
gas in the merger reaches some of the highest mass surface densities,
velocity dispersions, peak brightness temperatures, virial parameters, and internal turbulent pressures seen in the sample. However,
a single merger that happens to be the nearest LIRG cannot be expected to be representative of all merging and starbursting systems.
To extend the sample of mergers, we have observed NGC 4038/9
(Arp 244, “the Antennae”) at ∼100 pc spatial resolution to add it to
these comparisons of molecular gas properties.


At a distance of 22 Mpc (Schweizer et al. 2008), NGC 4038/9 is
the nearest gas-rich major merger (Stanford et al. 1990; Wilson et al.
2000; Gao et al. 2001a; Wilson et al. 2003; Brandl et al. 2009; Ueda
et al. 2012; Schirm et al. 2014; Bigiel et al. 2015) with ∼2 × 10 [10] M⊙

2 _N. Brunetti et al._


of molecular gas in the central region. Based on a significant body
of numerical work on reproducing the morphology and kinematics
of the interaction, the system is currently either just before or just
after the second pericentre passage (e.g. Toomre & Toomre 1972;
Barnes 1988; Mihos et al. 1993; Karl et al. 2010; Teyssier et al.
2010; Privon et al. 2013; Renaud et al. 2015). Its central region
hosts two progenitor nuclei separated by about 7 kpc. Given these
orbital details, NGC 4038/9 is likely at an earlier merger stage than
NGC 3256, and so offers a chance to probe how the molecular gas
properties depend on the phase of the merger.
The total SFR of the Antennae is between 11 M⊙ yr [−] [1] (separately
estimated from far-ultraviolet probing ∼1 to 100 Myr and 24 µm
probing ∼1 to 400 Myr) and 20 M⊙ yr [−] [1] (from H _𝛼_ probing ∼1 to
10 Myr; Chandar et al. 2017). Although not technically a LIRG from
its infrared luminosity, the higher of these SFR estimates would give
the Antennae a similar SFR to LIRGs. Separated from the nuclei is
the starbursting “overlap region” which alone exhibits a SFR of about
4 M⊙ yr [−] [1] over the last ≲100 Myr estimated from mid- through farinfrared observations (Brandl et al. 2009; Klaas et al. 2010; Bemis
& Wilson 2019). The remainder of the central part of the merger
has an infrared-estimated SFR totaling about 2.6 M⊙ yr [−] [1] (Bemis
& Wilson 2019).
NGC 4038/9 hosts an estimated population of at least 10 [4] young
massive star clusters, with masses in some cases exceeding 10 [6] M⊙
(Whitmore et al. 2010; Chandar et al. 2015; Mok et al. 2020). Several stellar populations of different ages have also been identified
throughout the system with a young starburst population in the overlap region (∼3 to 10 Myr; Mengel et al. 2001, 2005; Whitmore et al.
2010) and older post-starburst populations in the nuclei (∼65 Myr;
Mengel et al. 2001). Exploring the molecular-gas properties of this
system will provide the details on what conditions are necessary to
form the most massive star clusters (e.g. He et al. 2022). Our understanding of nearby mergers like NGC 4038/9 should also fill in the
small-scale information on how star and cluster formation occurred at

high redshift, where mergers were much more common (e.g. Romano
et al. 2021) and when the progenitors of globular clusters formed.
In this paper we present Atacama Large Millimeter/Submillimeter
Array (ALMA) observations of the central ∼9 kpc of NGC 4038/9
in the carbon monoxide (CO) _𝐽_ =2–1 line at linear scales of 55 pc,
corresponding to giant molecular cloud (GMC)-scales, and use them
to probe the molecular gas properties across the diverse interstellar
medium (ISM) of NGC 4038/9. These observations have comparable
sensitivity and resolution but are a significant improvement in area
coverage (see Figure 1), and image fidelity (covering the full range
of spatial scales) over earlier ALMA observations of the Antennae
(Whitmore et al. 2014; Sun et al. 2018). Section 2 describes the new
observations, along with our calibration and imaging procedure for
the CO (2–1) data. In Section 3 we describe the pixel-based method
used to measure the molecular gas properties in NGC 4038/9 at a
range of spatial resolutions. In Section 4, we compare NGC 4038/9
to the PHANGS-ALMA results presented by Sun et al. (2018, 2020)
and the LIRG NGC 3256 presented in Brunetti et al. (2021), and
we discuss the implications in Section 5. Finally, in Section 6 we
summarize the results and conclusions of this work.


**2** **DATA**


**2.1** **Observations**


Mosaicked ALMA observations of the central ∼9 kpc of NGC 4038/9
covering the entire disks of the two merging galaxies were obtained


MNRAS **000**, 1–14 (2024)



in Cycle 6 (see Table A1 for details of the observations). The main
12 m-array was used in both a compact and extended configuration.
The Morita Atacama Compact Array (ACA) was included for sensitivity to larger-scale emission, and the total power (TP) array was
also included to capture the largest-scale emission. Band 3 and 6
observations were carried out with spectral setups designed to cover
the _𝐽_ =1–0 and _𝐽_ =2–1 rotational transitions of [12] CO, the _𝐽_ =1–0 transitions of C [17] O and the cyanide radical (CN), and the _𝐽_ =2–1 transitions of [13] CO and C [18] O. Sufficient bandwidth was covered to also

allow detection of continuum emission in both bands. The spectral
resolution of the [12] CO (2–1) spectral window is 1.953 MHz, or approximately 2.54 km s [−] [1] . The native beam size is 0.51 [′′] (55 pc) and
the rms noise at this resolution is 0.24 K. The calibration accuracy
of ALMA at these frequencies is 5%.This paper focuses on the [12] CO
_𝐽_ =2–1 line; the continuum data products have been presented in He
et al. (2022). The remaining CO spectral lines are presented in He et
al. 2024 (submitted).


**2.2** **Calibration and imaging**


Calibration of all interferometric data was carried out by observatory
staff as part of data quality assurance using the ALMA pipeline for
Common Astronomy Software Applications (casa) (McMullin et al.
2007); casa and pipeline versions used for calibration are summarized in Table A1. After downloading the raw data from the archive,
we used the same versions to reapply the calibration prior to our
imaging. We inspected the diagnostic plots in the observatory weblogs to search for problematic data that were not properly calibrated
or left unflagged by the ALMA pipeline. Nothing was identified that
was serious enough to warrant changes to the calibration or additional
flagging.
Given the complex morphology of molecular line emission expected in the Antennae at the resolution of our observations, and the
number of lines to be imaged, we requested access to an early version of the PHANGS-ALMA imaging pipeline [1] for casa (Leroy et al.
2021a). Starting from the version-one code (at commit 5ef53d3), we
made modifications for imaging the additional array combinations
and spectral lines included in our observations of NGC 4038/9 [2] .
These modifications include implementation of different angular
sizes of the model components during multi-scale cleaning, for which
we use point sources, 0.5, 1, 2.5, 5, and 10 arcsec. All spectral-line
cleaning was carried out using the newest casa version available at
the time (5.6.1-8) to run the PHANGS-ALMA imaging pipeline. The
observations from the two 12 m-array configurations and the ACA
were all imaged and cleaned together. Cleaned cubes were also visually inspected for artefacts related to calibration and cleaning errors
before combining with the TP data.
TP data processing was carried out with the PHANGS-ALMA
TP calibration and imaging pipeline for casa in casa version 4.7.2
(see Table A1 for more details). This version of casa was the newest
version that the TP pipeline had been tested with at the time. Herrera et al. (2020) describe the full details of the pipeline procedure.
We used a modified version that does not perform any spectral bin

1 The procedure followed by the imaging pipeline has not changed dramatically between version one and the version described in detail by Leroy et al.
(2021a).
2 Details of these modifications are given in Appendix A. Our modified
version of the imaging pipeline will be shared on reasonable request to the
corresponding author, with a fully annotated Git change history.

_Molecular cloud properties of the Antennae_ 3


**Figure 1.** CO (2–1) moment maps of NGC 4038/9 at 55 pc resolution. Top left: integrated intensity (moment 0); top right: velocity field (moment 1); bottom:
velocity dispersion (moment 2). Pixels are half of the beam FWHM on a side. The squares in the bottom right corner of each panel contain a circle with diameter
equal to the beam FWHM (0.51 [′′] ). A scale bar indicating 1 kpc at the distance of NGC 4038/9 is also shown in the bottom right corner of each panel.


MNRAS **000**, 1–14 (2024)

4 _N. Brunetti et al._


ning and all continuum subtraction was carried out using order-one
polynomial (linear) fits to the continuum levels.
The interferometric and TP cubes were combined using the
PHANGS-ALMA imaging pipeline to produce the complete measurements of the spectral line emission in NGC 4038/9 (again using
casa version 5.6.1-8). Interferometric cubes corrected for the primary beam response were first made by dividing by the primary
beam cubes, and the corrected cubes were convolved to have circular synthesized beams. The interferometric cubes were padded with
masked pixels to cover at least the entire TP field of view (FoV), and
the TP cubes were regridded on to the same astrometric and spectral
grid as the interferometric cubes. Using the _feather_ task in casa,
the TP cubes were combined with both main array configurations
plus the ACA. The feathered cubes still contain the primary beam response applied to the interferometric data (and the inherent response
in the TP data), so another copy of the cubes was made which was
multiplied by the interferometric primary beam response to produce
flat-noise cubes for future use in identifying individual clouds using
algorithms such as pycprops (Rosolowsky et al. 2021).
Several versions of the interferometric cube were made when the

synthesized beam was made circular, with FWHM physical sizes
of 55, 80, 90, 120, and 150 pc. These beam sizes facilitate direct
comparisons to the analyses at 55, 80, and 120 pc by Sun et al.
(2018) and Brunetti et al. (2021), as well as at 90 and 150 pc by
Sun et al. (2020) and Brunetti & Wilson (2022). The cube with
55 pc resolution (0.51 arcsec) has an rms noise of approximately
0.25 K. Following Sun et al. (2018) and Brunetti et al. (2021), after
feathering the TP data with the convolved interferometric cubes,
each cube was spatially regridded such that the pixels were half the
synthesized beam FWHM on a side to roughly Nyquist sample the
beams. Moment maps calculated from the CO (2–1) data cube as
described in Brunetti et al. (2021) are shown in Figure 1.


**3** **ANALYSIS**


**3.1** **Measuring molecular gas properties**


Maps of total molecular gas mass surface density (Σ mol ), velocity dispersion ( _𝜎_ _𝑣_ ), and peak brightness temperature ( _𝑇_ B _,_ max ) were
calculated in the same way as in Brunetti et al. (2021). The only
difference was that we adopted a single Milky-Way like conversion
factor of _𝛼_ CO(2−1) = 4 _._ 35/0 _._ 70 = 6 _._ 25 M⊙ pc [−][2] (K km s [−][1] ) [−][1] for
all measurements from NGC 4038/9, following Sun et al. (2018),
where 0.70 is the commonly used value for the [12] CO _𝐽_ =2–1 / _𝐽_ =1–0
line ratio (cf. Leroy et al. 2022). Using the same conversion factor
as Sun et al. (2018) means any differences in the estimated mass
surface densities originate from different integrated intensities. The
conversion factor in NGC 4038/9 is not yet well constrained (see
Section 5 for further discussion) but previous investigation has estimated it may be similar to the typical Milky Way value (Wilson et al.
2003). This conversion factor includes a contribution from helium
and other heavy elements.
From our measurements of Σ mol and _𝜎_ _𝑣_ we also estimate the virial
parameter and internal turbulent pressure in each pixel, following Sun
et al. (2020), with



−1

(1)
�



Σ mol
_𝛼_ vir ≈ 3 _._ 1
� 10 [2] M⊙ pc [−][2]


and



−1 2
_𝜎_ _𝑣_ _𝐷_ beam
� � 10 km s [−][1] � � 150 pc



(2)


where _𝐷_ beam is the FWHM of the synthesized beam. These are
equivalent to equations 13 and 15 from Sun et al. (2018) that were
used by Brunetti et al. (2021). As described in Sun et al. (2018), these
equations assume that a single cloud roughly fills each synthesized
beam along with the equation for the virial parameter assuming a
cloud density profile that goes as _𝜌_ ( _𝑟_ ) ∝ _𝑟_ [−][1] . Maps of molecular gas
properties at 55 pc resolution are shown in Figure 2; maps at 150 pc
resolution are shown in Figure A1. We provide the binned data used
in this paper for both NGC 4038/9 and NGC 3256 as two separate
machine-readable tables (see Table B1 and B2 for format). Note that
we use square pixels, following Sun et al. (2018) and Brunetti et al.
(2021), but Sun et al. (2020) resample their maps to have hexagonal
pixels that match the beam size before measuring the gas properties.


**3.2** **Separating measurements by region**


To examine the impact that the location within NGC 4038/9 has
on the molecular gas properties, we separate our measurements into
sub-samples that are close to the nuclei and farther away. Following
Sun et al. (2018) and Brunetti et al. (2021), all pixels that are less
than 1 kpc from either nucleus (shown as gray circles with radii
of 1 kpc in Figures 2 and A1) are included in the nuclear pixel
sample, and the remaining pixels make up the non-nuclear sample.
Since the CO (3–2) observations of NGC 4038/9 from Whitmore
et al. (2014) analysed by Sun et al. (2018) only covered the overlap
region, we also separate pixels in our CO (2–1) data into another
sub-sample that lies in the same on-sky footprint as the CO (3–2)
observations for direct comparisons between the two datasets (gray
polygons in Figures 2 and A1). Note that Sun et al. (2020) separate
their aperture measurements into central and disc regions within each
galaxy based on distinct structures identified in near-infrared images
(the full description of this methodology is given by Querejeta et al.
2021) rather than by a 1 kpc radius as we do in this work [3] .


**3.3** **Morphology of the CO emission at 55 pc resolution**


The CO emission of the Antennae shown in Figure 1 has a very
complex structure. As seen in earlier work (Stanford et al. 1990; Wilson et al. 2000; Ueda et al. 2012), the regions of highest integrated
intensity in the moment 0 map are found in the northern nucleus
(NGC 4038), the southern nucleus (NGC 4039), and the overlap
region. These regions with high integrated intensities also typically
show large line widths in the moment 2 map and high brightness temperatures and pressures (Figure 2). Both nuclei show rather distorted
morphologies, especially NGC 4039, with filaments at different pitch
angles emerging from each nucleus.
The velocity field shown in the moment 1 map is particularly
striking in appearance, with sudden shifts in velocity on the scale
of a few resolutions elements visible in many parts of the map. The
western arm (to the west of NGC 4038) shows a consistent velocity
gradient reminiscent of the velocity field of a rotating disk, but this
interpretation is hard to reconcile with the quite redshifted emission
from the nucleus of NGC 4038 itself. The emission in the central

40 arcsec of NGC 4039 also suggests large-scale rotation, but this
organized structure breaks up in the central 5-10 arcsec, where several
shifts from red- to blue-shifted emission are seen.


3 Table of measurements from Sun et al. (2020) was retrieved from the
journal website on 2021 September 6.



−1

_._
�



_𝑃_ turb Σ mol

≈ 3 _._ 3×10 [5] K cm [−][3]
_𝑘_ B � 10 [2] M⊙ pc [−][2]



turb Σ mol

≈ 3 _._ 3×10 [5] K cm [−][3]
_𝑘_ B � 10 [2] M⊙ pc [−][2]



_𝜎_ _𝑣_
�� 10 km s [−][1]



2
_𝐷_ beam
� � 150 pc



MNRAS **000**, 1–14 (2024)

_Molecular cloud properties of the Antennae_ 5



(M pc 2 )

250 1500 3800 7100 12000



v [ (km s] 1 )
10 30 55 85 120



T B, max (K)
1 4 8 14 20



-18°51'30"


52'00"


30"


53'00"


30"




|1kpc 1kpc|Col2|Col3|Col4|Col5|Col6|Col7|Col8|Col9|Col10|Col11|Col12|Col13|Col14|Col15|Col16|Col17|Col18|Col19|Col20|Col21|Col22|Col23|Col24|Col25|
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
|1 kpc<br>1 kpc|||||||||||||||||||||||||
|1 kpc<br>1 kpc|||||||||||||||||||||||||
|1 kpc<br>1 kpc|1 kpc|1 kpc|1 kpc|1 kpc|1 kpc|1 kpc|1 kpc|1 kpc|1 kpc|1 kpc|1 kpc|1 kpc|1 kpc|1 kpc|1 kpc|1 kpc|1 kpc|1 kpc|1 kpc|1 kpc|1 kpc|1 kpc|1 kpc|1 kpc|
|1 kpc<br>1 kpc|1 kpc||||||||||||||||||||||||



RA (J2000)



vir
0.0 2.5 5.0 7.5 10.0


-18°51'30"


52'00"


30"


53'00"



P turb /k B (10 [6] K cm 3 ) 12
1 20 200 1000 4000



12 [h] 01 [m] 56 [s] 54 [s] 52 [s] 50 [s]







30"



12 [h] 01 [m] 56 [s] 54 [s] 52 [s] 5012 [s] [h] 01 [m] 56 [s] 54 [s] 52 [s] 50 [s]



RA (J2000)



RA (J2000)



**Figure 2.** Maps of molecular-gas properties in NGC 4038/9 at 55 pc resolution, calculated from CO (2–1) moment maps. The top row shows, from left to right,
mass surface density, velocity dispersion, and peak brightness temperature. The bottom row shows the virial parameter on the left and the internal turbulent
pressure on the right. Pixels are half of the beam FWHM on a side. Given the range of measured virial parameters, we chose a relatively low upper clipping
value of _𝛼_ vir = 10 to show pixels that are likely unbound (yellow) while still showing some of the structure for pixels that may be bound by external material
(orange) and pixels that are likely marginally bound (black/blue). The gray circles indicate the regions within 1 kpc radii of the nuclei, denoting the nuclear and
non-nuclear regions discussed in later sections. The gray polygons in the lower left indicate the overlap-region FoV observed in CO (3–2) by Whitmore et al.
(2014) and analysed by Sun et al. (2018). Pixels in these polygons make up our overlap region sub-sample. The squares in the bottom right corner of each panel
contain a circle with diameter equal to the beam FWHM (0.51 [′′] ). A scale bar indicating 1 kpc at the distance of NGC 4038/9 is also shown in the bottom right
corner of each panel. A CO-to-H 2 conversion factor of 6.25 M⊙ pc [−] [2] (K km s [−] [1] ) [−][1] was used to convert integrated intensities to mass surface densities, which
also affects the estimates of the virial parameter and internal turbulent pressure (see Equations 1 and 2).



There are a variety of filamentary structures visible in the integrated intensity map, including the long filament to the east of
NGC 4039 highlighted in Espada et al. (2012), and also a variety of
other similar structures particularly to the south of the NGC 4038
nucleus. While these structures typically exhibit narrow line widths



in the moment 2 map, some of them show a nearly constant radial
velocity in the moment 1 map while others shows signs of a gradient
in radial velocity along their length.


MNRAS **000**, 1–14 (2024)

6 _N. Brunetti et al._


**4** **RESULTS**


In this section, we compare the molecular gas properties of
NGC 4038/9 with spiral galaxies from the PHANGS-ALMA survey as well as with the merger and nearest LIRG NGC 3256. In
Section 4.1 we present the mean values for gas mass surface density,
velocity dispersion, and peak brightness temperature along with two
derived quantities, the virial parameter and the turbulent pressure.
In this analysis, we distinguish between the central nuclear regions
and the rest of the disk. In Section 4.2, we examine the correlations
between velocity dispersion and mass surface density in the various
galaxies and regions.


**4.1** **Distribution of cloud-scale molecular gas properties**


Qualitative comparisons between NGC 4038/9, NGC 3256, and the
PHANGS-ALMA galaxies presented by Sun et al. (2018) at 120 pc
resolution are shown as mass-weighted medians (symbols) and inner 68 [th] percentiles (errorbars) in Figure 3. Galaxies are split between nuclear (triangles) and non-nuclear (circles) sub-samples, with
the Whitmore et al. (2014) overlap region FoV also included for
NGC 4038/9 (stars). Figure 4 shows the mass-weighted distributions of the various sub-samples from NGC 4038/9 and NGC 3256
smoothed with Gaussian kernel density estimators (KDEs, e.g. Sun
et al. 2018) [4] .
There is considerable overlap in all cloud-scale properties between the nuclear and non-nuclear sub-samples from NGC 4038/9.
NGC 4038/9 exhibits higher mass surface densities measured in CO
(2–1) relative to all the PHANGS-ALMA galaxies [5] in Figure 3. The
nuclear and non-nuclear surface density samples from NGC 4038/9
and NGC 3256 are similar. Mass surface density distributions from
the central regions of PHANGS-ALMA galaxies overlap the most
with NGC 4038/9, but the disc region distributions from several
galaxies also overlap with NGC 4038/9. However when comparing nuclei to nuclei and non-nuclei to non-nuclei, the samples from
NGC 4038/9 are wider, have slightly higher medians, and extend to
higher surface densities at all resolutions. The greater sample spread
and maximum surface densities stand out especially in Figure 4.
The results of comparing NGC 4038/9 to the PHANGS-ALMA
galaxies in velocity dispersion, peak brightness temperature, and internal turbulent pressure are similar to those seen in mass surface
density, with the central regions of the PHANGS-ALMA galaxies
overlapping the most with NGC 4038/9. NGC 4038/9 exhibits some
of the highest values, although the centres of NGC 3256 and sometimes NGC 3627 often reach significantly higher values. NGC 4038/9
appears most consistent with the PHANGS-ALMA galaxies in virial
parameter, with the relatively low median and very large sample
width meaning it overlaps at least partially with all PHANGS-ALMA
galaxies. The higher mass surface densities and slightly lower velocity dispersions measured in CO (3–2) in NGC 4038/9 lead to virial
parameter samples from the CO (3–2) measurements that are much
lower than in CO (2–1) via Equation 1. However, Equation 2 results
in the CO (3–2) sample of internal turbulent pressures being only


4 Measurements at 120 pc resolution are shown but comparisons at 80 pc and
55 pc resolution were also made with generally the same results as seen in
Figures 3 and 4.
5 We note that the surface density values derived from the CO (3–2) measurements for NGC 4038/9 from Sun et al. (2018) exceed the CO (2–1) values.
This difference is likely due to the assumed value for the CO _𝐽_ =3–2 / _𝐽_ =1–0
line ratio being smaller than the value observed in He et al. 2024 (submitted).


MNRAS **000**, 1–14 (2024)



10 [4]





10 [3]


10 [2]


10 [1]


10 [2]


10 [1]


10 [1]


10 [0]


10 _[−]_ [1]


10 [1]


10 [0]


10 [8]


10 [6]


10 [4]

|Centre Disc Overlap|Col2|Col3|Col4|Col5|
|---|---|---|---|---|
||||||
||||||
||||||
||||||
||||||
||||||
||||||



**Figure 3.** Comparisons of mass-weighted pixel sample percentiles at 120 pc
resolution from NGC 4038/9, NGC 3256, and Sun et al. (2018) for mass
surface density, velocity dispersion, peak brightness temperature, virial parameter, and internal turbulent pressure. Medians are shown as symbols and
the inner 68 [th] percentiles as error bars. Samples are split between centre (triangle) and non-centre/disc (circle) pixels. NGC 4038/9 also has pixel samples
from the Whitmore et al. (2014) overlap region FoV, shown as stars. Percentiles from our CO (2–1) observations of NGC 4038/9 are in orange, from
the CO (3–2) observations in blue, NGC 3256 is in black, and the remainder
of the galaxies analysed by Sun et al. (2018) are in brown. Galaxies from Sun
et al. (2018) are ordered along the _𝑥_ axis with stellar mass increasing from
left to right. Stellar masses are from Sun et al. (2020), where available, and
from Sun et al. (2018) otherwise (i.e. M 31, M 33, and M 51).

0 _._ 5


0 _._ 0




|NGC 4038/9<br>NGC 3256|Col2|Col3|
|---|---|---|
|NGC 4038/9<br>NGC 3256|||



10 [1] 10 [2] 10 [3] 10 [4]


Σ (M _⊙_ pc _[−]_ [2] )



1


0





10 [0] 10 [1] 10 [2]


_σ_ _v_ (km s _[−]_ [1] )




|1)|Col2|Col3|Col4|Col5|
|---|---|---|---|---|
|0<br>1<br>ass frac. (dex_−_|_._5<br>_._0||||
|0<br>1<br>ass frac. (dex_−_|_._0||||



10 [0] 10 [1]


_T_ B _,_ max (K)

|1)|Col2|Col3|Col4|
|---|---|---|---|
|0_._5<br>1_._0<br>ass frac. (dex_−_1||||
|0_._0<br>||||



10 [0] 10 [1] 10 [2]


_α_ vir





10 [5] 10 [7] 10 [9]


_P_ turb _/k_ B (K cm _[−]_ [3] )


**Figure** **4.** Mass-weighted Gaussian KDEs of the 120 pc resolution measurements from the entire FoVs of NGC 4038/9 and NGC 3256 in the solid

orange and black lines, respectively. The samples from NGC 4038/9 are also
separated into regions near the nuclei (dotted), farther than 1 kpc from the
nuclei (dashed), and within the Whitmore et al. (2014) overlap region FoV
(dash-dotted). The blue-shaded regions show where the whole-FoV sample
from NGC 4038/9 is above the sample from NGC 3256. Gaussian KDE
bandwidths for the whole FoV samples were automatically chosen using the
scipy implementation of Scott’s Rule (Scott 1992), and the other regions from
NGC 4038/9 use the same bandwidth as that of the whole FoV.



_Molecular cloud properties of the Antennae_ 7


slightly higher than in CO (2–1). Peak brightness temperatures are
also similar between the two spectral line samples.
In properties other than mass surface density, the medians from
NGC 4038/9 are often lower than those measured in NGC 3256.

The two mergers appear most consistent in their non-nuclear samples of velocity dispersion and pressure, though the sample from
NGC 4038/9 is wider, extending both above and below the sample
from NGC 3256. The comparison of virial parameters in NGC 4038/9
and NGC 3256 is quite different from the other gas properties. The
median virial parameter in NGC 4038/9 is less than half that in
NGC 3256. The nuclear median from NGC 4038/9 also appears lower
than that of the non-nuclear pixels, contrary to NGC 3256 but similar to what is seen in the centres and discs of the PHANGS-ALMA

galaxies. However, the spread of the samples from both NGC 4038/9
and NGC 3256 does result in considerable overlap in the virial parameter between the two mergers.
The same comparisons of physical properties are made in Figure 5 but the samples from NGC 4038/9 are now shown with the full
PHANGS-ALMA sample analysed by Sun et al. (2020) at 150 pc resolution [6] . Note that we made the separation of pixels into regions in the
PHANGS-ALMA galaxies in the same manner as for NGC 4038/9,
not using the centre and disc designations from Sun et al. (2020).
We chose this approach to reduce variability in the comparison with
NGC 4038/9 potentially brought on by differences in how pixels are
assigned to the different regions. Using the simple 1 kpc radius also
has the benefit of often increasing the number of pixels within the
centres of galaxies, resulting in less stochastic inner 68 [th] percentiles
for the less massive and/or more distant galaxies. However, given the
size-stellar mass relation of galaxies, the fraction of a galaxy included
in the central region will increase as stellar mass decreases. For example, across the stellar mass range (1.2 × 10 [9] to 8.3 × 10 [10] M⊙) of
the PHANGS-ALMA galaxies shown in Figure 5, a range of stellar
radii of about 6 to 30 kpc is expected (Trujillo et al. 2020; Sánchez
Almeida 2020). This effect will likely result in the percentiles from
the centres of low stellar mass galaxies being underestimated since
contaminating disc pixels will make up a larger fraction of pixels in
their central 1 kpc.
Trends in the medians and inner 68 [th] percentiles with resolution
are not very strong in NGC 4038/9 so the GMC measurements for
the Antennae in Figure 5 do not appear very different compared to
Figure 3. The general trends between NGC 4038/9 and PHANGSALMA disc galaxies observed in Figure 3 appear in the comparisons
in Figure 5 as well. The centres of PHANGS-ALMA galaxies are
the most similar to NGC 4038/9, regardless of spatial scale, with
greater similarities at higher stellar masses. NGC 4038/9 exhibits
some of the highest mass surface densities, velocity dispersions,
peak brightness temperatures, and internal turbulent pressures compared to the PHANGS-ALMA galaxies. Virial parameters measured
in NGC 4038/9 are much more similar to typical values measured
in PHANGS-ALMA galaxies. Finally, for each property shown in
Figure 5, there are usually at least a few PHANGS-ALMA galaxies
that are more extreme in one or more aspects than NGC 4038/9.


**4.2** **Correlations between velocity dispersion and mass surface**
**density**


Figures 6 and 7 show mass-weighted probability density functions
(PDFs) of the velocity dispersion versus mass surface density. All


6 We found very little difference between using measurements made at 90 pc
and 150 pc resolution.


MNRAS **000**, 1–14 (2024)

8 _N. Brunetti et al._



Centres



10 [3]


10 [2]


10 [1]


10 [1]


10 [1]


10 [0]


10 _[−]_ [1]


10 [1]


10 [0]


10 [8]


10 [6]


10 [4]



NGC 4038/9

PHANGS



10 [9] 10 [10] 10 [11]


_M_ _⋆_ (M _⊙_ )



Discs


10 [9] 10 [10] 10 [11]


_M_ _⋆_ (M _⊙_ )



**Figure 5.** Mass-weighted pixel-sample percentiles vs. stellar mass for the five quantities from Fig. 3 from NGC 4038/9 (orange) and Sun et al. (2020) (brown)
measured at 150 pc resolution. The left column shows PHANGS-ALMA samples from galaxy centres (triangles) and the right column shows samples from
outside the centres (circles; based on being within a 1 kpc radius of the centre, not the centre and disc designations from Sun et al. 2020). NGC 4038/9 samples
from the nuclei, outside the nuclei (including the overlap region), and just the overlap region (stars) are shown in both columns. Note that the position of
NGC 4038/9 along the _𝑥_ axis is arbitrary.


MNRAS **000**, 1–14 (2024)

_Molecular cloud properties of the Antennae_ 9



PDFs are made from Gaussian KDEs, with bandwidths automatically
chosen using the scipy implementation of Scott’s Rule (Scott 1992).
Figure 6 shows velocity dispersion vs. mass surface density PDFs
of all significant pixels from NGC 4038/9, NGC 3256, and apertures
from all galaxies presented by Sun et al. (2020). KDEs show measurements made at 150 pc resolution in NGC 4038/9 and PHANGSALMA and 120 pc resolution in NGC 3256 [7] . The shift of most of
the mass to both higher surface densities and velocity dispersions in
NGC 4038/9 and NGC 3256 is visible, but the lower values from the
merger samples overlap with the higher values from the PHANGSALMA galaxies. The apertures from the centres of (primarily barred)
PHANGS-ALMA galaxies populate a very similar part of the parameter space to NGC 4038/9 and NGC 3256 (see Figure 2 from Sun
et al. 2020 for the separation of PHANGS-ALMA samples by region
and whether a galaxy contains a bar). These central values make
a dispersion-surface density trend that is slightly offset to higher
velocity dispersion for a given surface density from the rest of the
PHANGS-ALMA sample. The dispersion-surface density trends in
the merger samples are more consistent with this offset PHANGSALMA trend. There may also be evidence for the merger sample
trends broadening at high surface densities, extending to higher velocity dispersions at a given surface density than the PHANGSALMA sample. This broadening in velocity dispersion would also
produce a larger range of virial parameter at high surface densities
(see Equation 1). However, the sensitivity limit in this parameter
space roughly follows the upper-left edge of the contours (see Figure 1 from Sun et al. 2020), so that we do not have enough sensitivity
to detect low surface density regions with large velocity dispersions.
This effect is likely truncating the extent of the scatter in velocity
dispersion seen along the trends for NGC 4038/9 and NGC 3256 at
lower surface densities. To explore if the trends in the mergers truly
broaden only at high surface densities or are possibly broader than
the PHANGS-ALMA trend at all surface densities would require observations with a sensitivity a factor of two to four times better than
the current dataset.

Figure 7 shows the same contoursfor NGC 3256 andthe PHANGSALMA galaxies, but now the sample from NGC 4038/9 is split
into pixels within 1 kpc of either nucleus and those beyond. As already seen in Figures 3 and 5, pixels near the nuclei of NGC 4038/9
exhibit higher surface densities and velocity dispersions. The twodimensional view also emphasizes the split between regions is not
perfect as there is considerable overlap between the two sub-samples
in NGC 4038/9. The nuclear regions of NGC 4038/9 are generally
most consistent with the centres of (mostly barred) PHANGS-ALMA
galaxies, while the non-nuclear region extends over nearly the complete range limits of the full PHANGS-ALMA sample (both discs
and centres), likely due to the presence of the high surface density overlap region within the non-nuclear region of NGC 4038/9.
A similar separation of samples by nuclear and non-nuclear regions
is seen in NGC 3256 (see figure 7 from Brunetti et al. 2021). We
also note that the trend of velocity dispersion with surface density
appears stronger in the non-nuclear sample from NGC 4038/9 than
the nuclear sample, such that a majority of the mass in the nuclear
sample actually appears with nearly constant velocity dispersion with
surface density. This feature may indicate our choice of CO-to-H 2
conversion factor is not appropriate for regions near the nuclei of
NGC 4038/9, and we discuss this possibility further in Section 5.


7 Again, there are very few qualitative differences between different resolution versions of these figures.



Σ (M _⊙_ pc _[−]_ [2] )


**Figure** **6.** Mass-weighted Gaussian KDEs of velocity dispersion vs. mass
surface density measured in all significant pixels or hexagonal apertures from
NGC 4038/9 (orange filled contours), NGC 3256 (black dotted contours),
and all PHANGS-ALMA galaxies presented by Sun et al. (2020) (brown
contours). Contours enclose 99.5, 90, 50, and 20 per cent of the mass fromeach
data set. Measurements shown are made at 150 pc resolution in NGC 4038/9
and PHANGS-ALMA and 120 pc resolution in NGC 3256. Note that the mass
weighting used in this figure results in a different distribution of contours
compared to those presented in Sun et al. (2018, 2020), which did not use
mass weighting.


**5** **DISCUSSION**


**5.1** **Comparison of the two mergers**


NGC 4038/9 and NGC 3256 are in different merger stages and the
two systems also show significant differences in their molecular gas
conditions. Such differences are indeed predicted by merger simulations. Previous numerical work on replicating the morphology and
kinematics of NGC 4038/9 seems to point towards it being sometime
around second pericentre passage (Toomre & Toomre 1972; Barnes
1988; Mihos et al. 1993; Karl et al. 2010; Privon et al. 2013; Renaud
et al. 2015), with the large gas content suggesting that it may eventually enter the ULIRG phase (e.g., Gao et al. 2001b). NGC 3256 is a
late-stage merger, likely entering the point of coalescence, due to its
disturbed morphology and closely separated nuclei that share a common envelope (Stierwalt et al. 2013). In their simulations of galaxy
mergers, Moreno et al. (2019) show that after first pericentre passage,
the SFR of the merging galaxy relative to an isolated control galaxy
increases by a factor of about five for about 25 Myr before settling
to a more moderate enhancement of a factor of about two. After sec
ond pericentre passage and during coalescence, a second dramatic
enhancement, with the SFR ∼10 to 30 times higher than the control
galaxy, persists for about 500 Myr before more gradually decreasing.
A comparison of the SFR estimate of NGC 4038/9 (ranging from
11 to 20 M⊙ yr [−] [1] ) and NGC 3256 (50 M⊙ yr [−] [1] ) to the simulated
SFR enhancements fits their inferred merger stages. He et al. (2023)
used these same simulations to investigate how the properties of the
molecular clouds evolve during the merger. They find that clouds
in the merger have higher virial parameters than in simulations of


MNRAS **000**, 1–14 (2024)



10 [2]


10 [1]





10 [0]

10 [0] 10 [1] 10 [2] 10 [3] 10 [4]

10 _N. Brunetti et al._



10 [2]


10 [1]


10 [0]


10 [2]


10 [1]





10 [0]

10 [0] 10 [1] 10 [2] 10 [3] 10 [4]



Σ (M _⊙_ pc _[−]_ [2] )


**Figure 7.** Same as Figure 6 but now the sample from NGC 4038/9 is separated
into pixels within 1 kpc of the nuclei (red) and those beyond (blue). Contours
from NGC 3256 and PHANGS-ALMA are the same as in Figure 6 and are
identical in the top and bottom panels of this figure.


isolated galaxies and that the increase in virial parameter coincides
with the increase in the global star formation rate.
Our observations of higher molecular gas surface densities in
NGC 4038/9 than NGC 3256 (see e.g. Figure 4) but lower SFR
may also fit into the evolution of dense gas in the simulations presented by Moreno et al. (2019) and investigated further in He et al.
(2023). After the first pericentre passage and until just after the second passage, the mass of cold dense gas ( _𝑛>_ 10 cm [−][3], _𝑇<_ 300 K)
in their fiducial merger simulation is enhanced to almost twice that in
their isolated galaxy control (their figure 7). The dense gas mass then
becomes depleted relative to the isolated galaxy before rebounding
to about the same mass just before coalescence, and then slowly depleting to below the mass in the isolated galaxy. We may be catching
NGC 4038/9 close enough to its second encounter that the molecular
gas mass is still maximally enhanced whereas NGC 3256 is showing
signs of the subsequent reduction of molecular gas.


MNRAS **000**, 1–14 (2024)



To explain the higher SFR in NGC 3256 compared to NGC 4038/9
despite their comparable ranges of molecular gas surface density
we turn to the behaviour of the densest gas in the simulations.
While Moreno et al. (2019) found the total mass of molecular gas
decreased after second passage, the mass in cold ultra-dense gas
( _𝑛>_ 1000 cm [−][3], _𝑇<_ 300 K) increased by a factor of about 100 [8] .
The fraction of cold dense gas in the ultra-dense regime increased
from about 0.1 per cent to around 30 per cent, leading to the dramatic
increase in the SFR after second passage. Thus, it could be that the
total mass of very dense gas is significantly higher in NGC 3256 than
in NGC 4038/9, which could lead to an increase in the overall star

formation rate.

While the velocity dispersions in the non-nuclear regions of
NGC 4038/9 and NGC 3256 are quite similar, the nuclear velocity
dispersions in NGC 3256 are significantly higher than in NGC 4038/9
(Figure 3). Higher velocity dispersions near the nuclei of NGC 3256
may also be driven by the different merger stages and possibly influenced by the presence of outflows (Sakamoto et al. 2013). Star
formation is predicted to produce at most about 10 km s [−] [1] of turbulent velocity dispersion (Shetty & Ostriker 2012; Krumholz et al.
2018), with gas flows required to power larger velocity dispersions
(Krumholz et al. 2018). The later merger stage of NGC 3256, resulting in more morphological disruption and likely more significant
tidal flows of gas towards the nuclei, could result in the larger velocity
dispersions compared to NGC 4038/9.
Combining higher surface densities with similar velocity dispersions (in the non-nuclear regions) in NGC 4038/9 as compared to
NGC 3256 results in lower virial parameters for some of the gas in
NGC 4038/9. While we might expect the higher SFR in NGC 3256
to imply lower virial parameters than in NGC 4038/9, we may be
seeing the combination of enhanced turbulence and ultra-dense gas
in NGC 3256 making the gas appear unbound at the scales probed.
Perhaps in the more violent coalescence stages only the densest (and
therefore smaller volume) portions of the molecular gas in NGC 3256
will even approach being gravitationally bound. In contrast, weaker
tidal flows in NGC 4038/9 (cf. Ueda et al. 2017) may not have transformed its ISM away from appearing largely near virial equilibrium
or collapse like many of the PHANGS-ALMA galaxies. The ISM in
NGC 4038/9 still being in a transitional stage may explain the wide
range of virial parameters compared to PHANGS-ALMA and the
non-nuclear regions of NGC 3256.
It could also be that the methods to measure SFR observation
ally (which measure the average SFR over 10-100 Myr, Kennicutt &
Evans 2012) lag behind the properties of the molecular gas (which
are measured "instantaneously"). The dynamical state of the molecular gas in NGC 3256 may now be unfavorable for widespread star
formation but our SFR indicators rely on a currently existing population of stars that are the result of past gas conditions. We must
also caution that the virial parameters shown in Figures 3 through 5
do not account for pressure confinement contributing to binding the
observed molecular gas. Brunetti et al. (2021) roughly estimate that
stellar surface densities and cloud-cloud collisions between GMCs

could provide enough external pressure to balance the internal pressure for some of the gas in NGC 3256.
If the CO emission is optically thick in both NGC 4038/9 and
NGC 3256 then the peak brightness temperature would be roughly
equal to the kinetic temperature of the molecular gas. The higher


8 We note that this simulated "ultra-dense gas" is on average somewhat denser
(by a factor of ∼ 10) than the "bulk molecular gas" traced by CO observations
of galaxies.

peak brightness temperatures we measure in NGC 3256 would then
indicate that the kinetic temperature of the gas is also higher than in
NGC 4038/9. Given the higher SFR in NGC 3256 is producing more
stars to heat the molecular gas, it is not surprising that the molecular gas appears hotter in NGC 3256 than NGC 4038/9. A radiative
transfer analysis of NGC 3256 spanning several CO transitions as
well as optically thin and thick isotopologues would be necessary to
further investigate differences in the temperatures and densities of
the molecular gas in the two mergers at GMC scales.
As mentioned in Section 4.1, the changes in the median molecular
gas properties with resolution in NGC 4038/9 are typically small relative to PHANGS-ALMA measured by Sun et al. (2018, 2020). Even
weaker trends in median molecular gas properties were measured in
NGC 3256 by Brunetti et al. (2021). Starting with a beam that is
roughly the size of a typical GMC and then increasing the beam size,
the measured surface density and peak brightness temperature would
tend to decrease as a result of beam dilution. Conversely, if the starting
beam is smaller than the typical GMC size, then increasing the beam
size would likely not result in very much change in the measured surface density. The cloud-finding analysis by Brunetti & Wilson (2022)
resulted in cloud radii slightly larger in NGC 3256 than PHANGSALMA galaxies, pointing towards NGC 3256 being in the second
scenario described. The weak trends measured in NGC 4038/9 im
ply it is also in the second scenario and that the typical size of
GMCs may again be larger than those in PHANGS-ALMA galaxies.
The clouds in NGC 4038/9 may not be as large as in NGC 3256
since we measured slightly stronger trends in NGC 4038/9. An interesting investigation would be to calculate the “clumping factor”
defined by Leroy et al. (2013) for NGC 4038/9 and NGC 3256 and
compare to those calculated by Sun et al. (2022) for the PHANGSALMA galaxies. If the mergers exhibit lower clumping factors than
the PHANGS-ALMA galaxies, then a shortcut for estimating the
clumping and typical GMC size could be to calculate the changes
in molecular gas property medians over a fairly modest change in
resolution.


**5.2** **CO-to-H** 2 **conversion factor considerations**


Since the CO-to-H 2 conversion factor influences many of the molecular gas properties presented here, we now discuss the appropriateness
of our choice to use a single value (the Milky Way value) throughout NGC 4038/9. A single conversion factor has the benefit that
changes to the factor result in shifting the sample of quantities all
together. However, it is likely an oversimplification to assume all
regions within NGC 4038/9 truly have the same conversion factor.
For example, in their merger simulations, Renaud et al. (2019a) find
that the CO-to-H 2 conversion factor has a significant time variation.
They conclude that the conversion factor fluctuations are produced
by both feedback energy and velocity dispersion. In their analysis of
a simulation of an Antennae-like merger, Renaud et al. (2019b) find
that the conversion factor has strong spatial variations as well.
There may be a signature in our data of the conversion factor in
NGC 4038/9 changing in the gas closer to the nuclei. While a trend
between the velocity dispersion and surface density in NGC 4038/9
is obvious up to about 10 [3] M⊙ pc [−] [2], for surface densities above this
value there is a flattening of the trend that is most easily seen in the
nuclei in Figure 7 (top panel). Since this flattening is strongest in
the nuclear sub-sample from NGC 4038/9, and is not seen in any
of the sub-samples from Sun et al. (2020) (who adopt a radially
variable conversion factor), our choice of a single conversion factor



_Molecular cloud properties of the Antennae_ 11


for NGC 4038/9 may be the cause [9] . Larger velocity dispersions and
hotter gas, like the medians from NGC 4038/9 in Figure 3 imply,
can drive the conversion factor down (Bolatto et al. 2013). If the

conversion factor does decrease towards the nuclei in NGC 4038/9

then the nuclear surface densities would need to be shifted to the left

in Figure 7. An interesting consequence of this interpretation is that
for pixels with surface densities roughly below about 10 [3] M⊙ pc [−] [2],
the conversion factor may not vary as much as it will in the nuclear
regions.
As for the choice of the Milky Way value itself, this choice helps
in simplifying comparisons with other work like Sun et al. (2018)
and Galactic studies. For example, a single conversion factor across
NGC 4038/9 and the PHANGS-ALMA galaxies from Sun et al.
(2018) means that Figure 3 indicates that the surface brightness of
CO emission is systematically higher in NGC 4038/9. However, there
is evidence that the Milky Way conversion factor may not be far off
for the bulk of the CO emission in NGC 4038/9, even given the
typical differences between spiral galaxies and starbursts/mergers
(Narayanan et al. 2011, 2012; Renaud et al. 2019a,b). Wilson
et al. (2003) estimated _𝛼_ CO(1−0) ≈6 _._ 5 M⊙ pc [−][2] (K km s [−][1] ) [−][1] in
NGC 4038/9 from virial mass estimates of resolved super giant
molecular complexes, or a factor of ≈1.5 larger than the Milky Way
value we use here. Schirm et al. (2014) performed non-local thermodynamic equilibrium radiative transfer modeling of NGC 4038/9
with the radex code on eight transitions of CO and two transitions
of [CI]. To make their mass estimate consistent with that of Brandl
et al. (2009) they had to assume a starburst-like CO abundance and arrived at a conversion factor of _𝛼_ CO(1−0) ≈7 M⊙ pc [−][2] (K km s [−][1] ) [−][1],
consistent with Wilson et al. (2003). Scaling this conversion factor to CO (2–1), with the same _𝑅_ 21 we adopted, gives a value of
_𝛼_ CO(2−1) ≈ 10 M⊙ pc [−][2] (K km s [−][1] ) [−][1] . Given the observed spread
in the conversion factor within starbursts of factors of ∼3 to 4 (Bolatto et al. 2013), we have opted to simplify comparisons to previous
works by simply using the Milky Way value. We will address the
question of what conversion factor is appropriate for NGC 4038/9 by
combining all CO data in the present observations with additional
ALMA observations of several transitions of optically thin and thick
CO isotopologues, at similar spatial resolution to the observations
presented here (He et al. 2024, submitted).


**6** **CONCLUSIONS**


We have presented GMC-scale observations of the central 9 kpc of
NGC 4038/9 in CO (2–1). Maps of molecular gas mass surface density, velocity dispersion, peak brightness temperature, virial parameter, and internal turbulent pressure have been derived from these
data at a range of spatial resolutions from 55 to 150 pc. Comparisons of the pixel-by-pixel distributions of these gas properties from
NGC 4038/9 have been made at matched spatial resolution to the
PHANGS-ALMA sample of 70 nearby spiral galaxies (Sun et al.
2018, 2020), the overlap region of NGC 4038/9 observed in CO (3–
2) (Whitmore et al. 2014; Sun et al. 2018), and the merger and nearest
luminous infrared galaxy NGC 3256 (Brunetti et al. 2021).
Relative to the PHANGS-ALMA galaxies, NGC 4038/9 has some
of the highest molecular gas surface densities, velocity dispersions,
peak brightness temperatures, and turbulent pressures. These gas
properties measured in the discs of the PHANGS-ALMA galaxies


9 An alternative interpretation is that the gas in the nuclei is far from selfgravitating, in which case no correlation between velocity dispersion and
surface density would be expected.


MNRAS **000**, 1–14 (2024)

12 _N. Brunetti et al._


are often significantly lower than those measured in NGC 4038/9.
The centres of the PHANGS-ALMA galaxies with the highest stellar
masses do show some overlap with the gas properties in NGC 4038/9.
Virial parameters measured in NGC 4038/9, while spanning a large
range, are much more similar to the PHANGS-ALMA galaxies than
any other gas property. Differences by region within NGC 4038/9
(nuclei vs. non-nuclear) are similar to those seen within PHANGSALMA galaxies, with the most extreme gas properties near the nuclei.


Gas surface densities are similar between NGC 4038/9 and

NGC 3256, though the highest values are measured in NGC 4038/9.
On the other hand, velocity dispersions near the nuclei of NGC 3256
and peak brightness temperatures throughout the system are significantly higher than in NGC 4038/9. Higher peak brightness temperatures may be indicative of higher kinetic temperatures caused by the
higher star formation rate in NGC 3256. Some of the higher velocity
dispersions in the nuclei of NGC 3256 may be due to contamination from the jet in the southern nucleus and/or the outflow in the
northern nucleus (Sakamoto et al. 2013; Brunetti et al. 2021). However, the later merger stage of NGC 3256 compared to NGC 4038/9
may also be producing more intense merger-driven flows into the
nucleus of NGC 3256 that could produce more turbulence and result
in larger line widths. The wider but systematically lower range of
virial parameters in NGC 4038/9 compared to NGC 3256 could also
be a consequence of the differing merger stages. NGC 3256 may be
leaving the starburst phase as coalescence of the progenitor galaxies increases the turbulence and suppresses further star formation,
but NGC 4038/9 may be caught in the transition between bursts of
enhanced star formation.


Next steps will focus on comparisons of several CO isotopologues
and transitions across the entire region observed in this work (He et
al. 2024, submitted). _𝐽_ =2–1 transitions of [13] CO and C [18] O as well
as the _𝐽_ =1–0 transition of [12] CO were also observed in this project
and will allow for exact matching of _𝑢𝑣_ coverage as well as spatial
and spectral resolutions. Additional observations have been obtained
with ALMA, mapping the same field of view with the same array
combinations in [12] CO (3–2) and [13] CO (1–0), extending the area
probed by these transitions at cloud scales. With three transitions
of [12] CO and two transitions of [13] CO a radiative transfer analysis
can constrain the densities and temperatures of the molecular gas in
NGC 4038/9, and help to estimate the CO-to-H 2 conversion factor at
cloud scales (He et al. 2024, submitted).


In summary, these two nearby galaxy mergers show significantly
higher molecular gas surface densities, velocity dispersions, peak
brightness temperatures, and turbulent pressures on giant molecular
cloud scales compared to spiral galaxies from the PHANGS-ALMA
survey. However, there are also significant differences between the
two mergers that may be linked to the phase of the merger. For
example, the larger velocity dispersion and higher gas temperature of
NGC 3256 may be linked to enhanced feedback from star formation
in its more advanced merger phase compared to NGC 4038/9. In
contrast, there may be a current up-tick in the star formation rate in
NGC 4038/9, highlighting time variability as an important factor in
understanding galaxy mergers observationally as well as theoretically
(Moreno et al. 2019; He et al. 2023). Additional studies on molecular
cloud scales of nearby starburst mergers as well as the pre- and postmerger stages will be important for placing these results in a wider
context and ultimately informing our understanding of the high star
formation rates seen in galaxies at high redshift.


MNRAS **000**, 1–14 (2024)



**ACKNOWLEDGEMENTS**


We thank the referee for comments that improved the presentation
and discussion of the paper. The research of NB and HH is partially
supported by grants from the Natural Sciences and Engineering Research Council of Canada through the New Technologies for Canadian Observatories program. The research of CDW and ER is supported by grants from the Natural Sciences and Engineering Research
Council of Canada (NSERC), and also for CDW by the Canada Research Chairs program. JS acknowledges support by NSERC through
a Canadian Institute for Theoretical Astrophysics (CITA) National
Fellowship. FB acknowledges funding from the European Research
Council (ERC) under the European Unions Horizon 2020 research
and innovation program (grant agreement No.726384/Empire). ES
acknowledges funding from the ERC under the European Unions
Horizon 2020 research and innovation program (grant agreement
No. 694343).
We acknowledge the use of the ARCADE (ALMA Reduction in
the CANFAR Data Environment) science platform. ARCADE is a
ALMA Cycle 7 development study with support from the National
Radio Astronomy Observatory, the North American ALMA Science
Centre, and the National Research Centre of Canada.
This research made use of Astropy, a community-developed core
Python package for Astronomy ( `[http://www.astropy.org](http://www.astropy.org)`, Astropy Collaboration et al. 2013, 2018). This research also made use of
the SciPy (Virtanen et al. 2020), Matplotlib (Hunter 2007), NumPy
(van der Walt et al. 2011), pandas (McKinney 2010), Jupyter Notebook (Kluyver et al. 2016), and spectral-cube (Ginsburg et al.
2019) Python packages. This research has made use of the R programming language (R Core Team 2019). This research has made
use of the Cube Analysis and Rendering Tool for Astronomy (carta)
(Comrie et al. 2021). This research has made use of NASA’s Astrophysics Data System. This research has made use of the VizieR
catalogue access tool (Ochsenbein et al. 2000). This research has
made use of the NASA/IPAC Extragalactic Database (NED), which
is funded by the National Aeronautics and Space Administration and
operated by the California Institute of Technology. This research has
made use of the SIMBAD database, operated at CDS, Strasbourg,
France (Wenger et al. 2000).


**DATA AVAILABILITY**


This paper makes use of the following ALMA data:
ADS/JAO.ALMA#2018.1.00272.S (accessed from the ALMA Science portal at `almascience.org` ). ALMA is a partnership of ESO
(representing its member states), NSF (USA) and NINS (Japan), together with NRC (Canada), MOST and ASIAA (Taiwan), and KASI
(Republic of Korea), in cooperation with the Republic of Chile.
The Joint ALMA Observatory is operated by ESO, AUI/NRAO and
NAOJ. The National Radio Astronomy Observatory is a facility of the
National Science Foundation operated under cooperative agreement
by Associated Universities, Inc.
The primary-beam cube from project
ADS/JAO.ALMA#2011.0.00876.S was retrieved from the JVO

portal ( `[http://jvo.nao.ac.jp/portal](http://jvo.nao.ac.jp/portal)` ) operated by the NAOJ.
The derived data generated in this research will be shared on
reasonable request to the corresponding author.


**REFERENCES**


[Astropy Collaboration et al., 2013, A&A, 558, A33](http://dx.doi.org/10.1051/0004-6361/201322068)

[Astropy Collaboration et al., 2018, AJ, 156, 123](http://dx.doi.org/10.3847/1538-3881/aabc4f)
[Barnes J. E., 1988, ApJ, 331, 699](http://dx.doi.org/10.1086/166593)
[Bemis A., Wilson C. D., 2019, AJ, 157, 131](http://dx.doi.org/10.3847/1538-3881/ab041d)
Bigiel F., Leroy A. K., Blitz L., Bolatto A. D., da Cunha E., Rosolowsky E.,
[Sandstrom K., Usero A., 2015, ApJ, 815, 103](http://dx.doi.org/10.1088/0004-637X/815/2/103)
[Bolatto A. D., Wolfire M., Leroy A. K., 2013, ARA&A, 51, 207](http://dx.doi.org/10.1146/annurev-astro-082812-140944)
[Brandl B. R., et al., 2009, ApJ, 699, 1982](http://dx.doi.org/10.1088/0004-637X/699/2/1982)
[Brunetti N., Wilson C. D., 2022, MNRAS, 515, 2928](http://dx.doi.org/10.1093/mnras/stac1975)

Brunetti N., Wilson C. D., Sliwa K., Schinnerer E., Aalto S., Peck A. B.,

[2021, MNRAS, 500, 4730](http://dx.doi.org/10.1093/mnras/staa3425)
[Chandar R., Fall S. M., Whitmore B. C., 2015, ApJ, 810, 1](http://dx.doi.org/10.1088/0004-637X/810/1/1)
[Chandar R., Fall S. M., Whitmore B. C., Mulia A. J., 2017, ApJ, 849, 128](http://dx.doi.org/10.3847/1538-4357/aa92ce)
Comrie A., et al., 2021, CARTA: The Cube Analysis and Rendering Tool for
[Astronomy, doi:10.5281/zenodo.4905459](http://dx.doi.org/10.5281/zenodo.4905459)
[Espada D., et al., 2012, ApJ, 760, L25](http://dx.doi.org/10.1088/2041-8205/760/2/L25)
[Gao Y., Lo K. Y., Lee S. W., Lee T. H., 2001a, ApJ, 548, 172](http://dx.doi.org/10.1086/318682)
[Gao Y., Lo K. Y., Lee S. W., Lee T. H., 2001b, ApJ, 548, 172](http://dx.doi.org/10.1086/318682)
Ginsburg A., et al., 2019, radio-astro-tools/spectral-cube: Release v0.4.5,

[doi:10.5281/zenodo.3558614](http://dx.doi.org/10.5281/zenodo.3558614)

He H., Wilson C., Brunetti N., Finn M., Bemis A., Johnson K., 2022, [ApJ,](http://dx.doi.org/10.3847/1538-4357/ac5628)

[928, 57](https://ui.adsabs.harvard.edu/abs/2022ApJ...928...57H)
He H., Bottrell C., Wilson C., Moreno J., Burkhart B., Hayward C. C.,
[Hernquist L., Twum A., 2023, ApJ, 950, 56](http://dx.doi.org/10.3847/1538-4357/acca76)
[Herrera C. N., et al., 2020, A&A, 634, A121](http://dx.doi.org/10.1051/0004-6361/201936060)
[Hunter J. D., 2007, Computing in Science & Engineering, 9, 90](http://dx.doi.org/10.1109/MCSE.2007.55)
Karl S. J., Naab T., Johansson P. H., Kotarba H., Boily C. M., Renaud F.,
[Theis C., 2010, ApJ, 715, L88](http://dx.doi.org/10.1088/2041-8205/715/2/L88)
[Kennicutt R. C., Evans N. J., 2012, ARA&A, 50, 531](http://dx.doi.org/10.1146/annurev-astro-081811-125610)
[Kennicutt R. C., de los Reyes M. A. C., 2021, ApJ, 908, 61](http://dx.doi.org/10.3847/1538-4357/abd3a2)
[Klaas U., Nielbock M., Haas M., Krause O., Schreiber J., 2010, A&A, 518,](http://dx.doi.org/10.1051/0004-6361/201014670)

[L44](https://ui.adsabs.harvard.edu/abs/2010A&A...518L..44K)
Kluyver T., et al., 2016, in Loizides F., Scmidt B., eds, 20 [th] International
Conference on Electronic Publishing. Positioning and Power in Academic
Publishing: Players, Agents and Agendas. IOS Press, Netherlands, p. 87
[Krumholz M. R., Burkhart B., Forbes J. C., Crocker R. M., 2018, MNRAS,](http://dx.doi.org/10.1093/mnras/sty852)


[477, 2716](https://ui.adsabs.harvard.edu/abs/2018MNRAS.477.2716K)
Leroy A. K., Walter F., Brinks E., Bigiel F., de Blok W. J. G., Madore B.,
[Thornley M. D., 2008, AJ, 136, 2782](http://dx.doi.org/10.1088/0004-6256/136/6/2782)
[Leroy A. K., et al., 2013, ApJ, 769, L12](http://dx.doi.org/10.1088/2041-8205/769/1/L12)
[Leroy A. K., et al., 2021a, ApJS, 255, 19](http://dx.doi.org/10.3847/1538-4365/abec80)
[Leroy A. K., et al., 2021b, ApJS, 257, 43](http://dx.doi.org/10.3847/1538-4365/ac17f3)
[Leroy A. K., et al., 2022, ApJ, 927, 149](http://dx.doi.org/10.3847/1538-4357/ac3490)
McKinney W., 2010, in Stéfan van der Walt Jarrod Millman eds, Python
in Science Conf. Ser.. Available at: `[http://conference.scipy.org/](http://conference.scipy.org/proceedings/scipy2010/)`
`[proceedings/scipy2010/](http://conference.scipy.org/proceedings/scipy2010/)`, p. 56
McMullin J. P., Waters B., Schiebel D., Young W., Golap K., 2007, in Shaw
R. A., Hill F., Bell D. J., eds, ASP Conf. Ser. Vol. 376, Astronomical Data
Analysis Software and Systems XVI. Astron. Soc. Pac., San Francisco,
p. 127
Mengel S., Lehnert M. D., Thatte N., Tacconi-Garman L. E., Genzel R., 2001,

[ApJ, 550, 280](http://dx.doi.org/10.1086/319704)
[Mengel S., Lehnert M. D., Thatte N., Genzel R., 2005, A&A, 443, 41](http://dx.doi.org/10.1051/0004-6361:20052908)
[Mihos J. C., Bothun G. D., Richstone D. O., 1993, ApJ, 418, 82](http://dx.doi.org/10.1086/173373)
[Mok A., Chandar R., Fall S. M., 2020, ApJ, 893, 135](http://dx.doi.org/10.3847/1538-4357/ab7a14)
[Moreno J., et al., 2019, MNRAS, 485, 1320](http://dx.doi.org/10.1093/mnras/stz417)
Narayanan D., Krumholz M., Ostriker E. C., Hernquist L., 2011, [MNRAS,](http://dx.doi.org/10.1111/j.1365-2966.2011.19516.x)

[418, 664](https://ui.adsabs.harvard.edu/abs/2011MNRAS.418..664N)
[Narayanan D., Krumholz M. R., Ostriker E. C., Hernquist L., 2012, MNRAS,](http://dx.doi.org/10.1111/j.1365-2966.2012.20536.x)

[421, 3127](https://ui.adsabs.harvard.edu/abs/2012MNRAS.421.3127N)

[Ochsenbein F., Bauer P., Marcout J., 2000, A&AS, 143, 23](http://dx.doi.org/10.1051/aas:2000169)

Privon G. C., Barnes J. E., Evans A. S., Hibbard J. E., Yun M. S., Mazzarella
[J. M., Armus L., Surace J., 2013, ApJ, 771, 120](http://dx.doi.org/10.1088/0004-637X/771/2/120)
[Querejeta M., et al., 2021, A&A, 656, A133](http://dx.doi.org/10.1051/0004-6361/202140695)
R Core Team 2019, R: A Language and Environment for Statistical Computing. R Foundation for Statistical Computing, Vienna, Austria, `[https:](https://www.R-project.org/)`
```
  //www.R-project.org/
```

[Renaud F., Bournaud F., Duc P.-A., 2015, MNRAS, 446, 2038](http://dx.doi.org/10.1093/mnras/stu2208)

[Renaud F., Bournaud F., Daddi E., Weiß A., 2019a, A&A, 621, A104](http://dx.doi.org/10.1051/0004-6361/201834397)



_Molecular cloud properties of the Antennae_ 13


Renaud F., Bournaud F., Agertz O., Kraljic K., Schinnerer E., Bolatto A.,
[Daddi E., Hughes A., 2019b, A&A, 625, A65](http://dx.doi.org/10.1051/0004-6361/201935222)
[de los Reyes M. A. C., Kennicutt R. C., 2019, ApJ, 872, 16](http://dx.doi.org/10.3847/1538-4357/aafa82)
[Romano M., et al., 2021, A&A, 653, A111](http://dx.doi.org/10.1051/0004-6361/202141306)
[Rosolowsky E., et al., 2021, MNRAS, 502, 1218](http://dx.doi.org/10.1093/mnras/stab085)
Sakamoto K., Aalto S., Costagliola F., Martín S., Ohyama Y., Wiedner M. C.,
[Wilner D. J., 2013, ApJ, 764, 42](http://dx.doi.org/10.1088/0004-637X/764/1/42)
[Sánchez Almeida J., 2020, MNRAS, 495, 78](http://dx.doi.org/10.1093/mnras/staa1108)
[Schinnerer E., et al., 2013, ApJ, 779, 42](http://dx.doi.org/10.1088/0004-637X/779/1/42)
[Schirm M. R. P., et al., 2014, ApJ, 781, 101](http://dx.doi.org/10.1088/0004-637X/781/2/101)
[Schweizer F., et al., 2008, AJ, 136, 1482](http://dx.doi.org/10.1088/0004-6256/136/4/1482)
Scott D. W., 1992, Multivariate Density Estimation: Theory, Practice, and
Visualization. Wiley Series in Probability and Statistics, John Wiley &
Sons, New York
[Shetty R., Ostriker E. C., 2012, ApJ, 754, 2](http://dx.doi.org/10.1088/0004-637X/754/1/2)
[Stanford S. A., Sargent A. I., Sanders D. B., Scoville N. Z., 1990, ApJ, 349,](http://dx.doi.org/10.1086/168334)

[492](https://ui.adsabs.harvard.edu/abs/1990ApJ...349..492S)

[Stierwalt S., et al., 2013, ApJS, 206, 1](http://dx.doi.org/10.1088/0067-0049/206/1/1)
[Sun J., et al., 2018, ApJ, 860, 172](http://dx.doi.org/10.3847/1538-4357/aac326)
[Sun J., et al., 2020, ApJ, 901, L8](http://dx.doi.org/10.3847/2041-8213/abb3be)
[Sun J., et al., 2022, AJ, 164, 43](http://dx.doi.org/10.3847/1538-3881/ac74bd)
[Teyssier R., Chapon D., Bournaud F., 2010, ApJ, 720, L149](http://dx.doi.org/10.1088/2041-8205/720/2/L149)
[Toomre A., Toomre J., 1972, ApJ, 178, 623](http://dx.doi.org/10.1086/151823)
[Trujillo I., Chamba N., Knapen J. H., 2020, MNRAS, 493, 87](http://dx.doi.org/10.1093/mnras/staa236)
[Ueda J., et al., 2012, ApJ, 745, 65](http://dx.doi.org/10.1088/0004-637X/745/1/65)
[Ueda J., et al., 2017, PASJ, 69, 6](http://dx.doi.org/10.1093/pasj/psw110)

[Virtanen P., et al., 2020, Nature Methods, 17, 261](http://dx.doi.org/10.1038/s41592-019-0686-2)
van der Walt S., Colbert S. C., Varoquaux G., 2011, Comput. Sci. Eng., 13,

22

[Wenger M., et al., 2000, A&AS, 143, 9](http://dx.doi.org/10.1051/aas:2000332)
[Whitmore B. C., et al., 2010, AJ, 140, 75](http://dx.doi.org/10.1088/0004-6256/140/1/75)
[Whitmore B. C., et al., 2014, ApJ, 795, 156](http://dx.doi.org/10.1088/0004-637X/795/2/156)
[Wilson C. D., Scoville N., Madden S. C., Charmandaris V., 2000, ApJ, 542,](http://dx.doi.org/10.1086/309504)

[120](https://ui.adsabs.harvard.edu/abs/2000ApJ...542..120W)

[Wilson C. D., Scoville N., Madden S. C., Charmandaris V., 2003, ApJ, 599,](http://dx.doi.org/10.1086/379344)

[1049](https://ui.adsabs.harvard.edu/abs/2003ApJ...599.1049W)

[Wilson C. D., Elmegreen B. G., Bemis A., Brunetti N., 2019, ApJ, 882, 5](http://dx.doi.org/10.3847/1538-4357/ab31f3)


**APPENDIX A:** **MODIFICATIONS TO THE PHANGS-ALMA**

**INTERFEROMETRIC IMAGING PIPELINE**


Starting from commit 5ef53d3, we made modifications to the
PHANGS-ALMA imaging pipeline to handle the additional array
configurations and spectral lines present in the NGC 4038/9 observations compared to the bulk of the PHANGS-ALMA observations
and to address some code bugs. The first change was to automate
the continuum subtraction step based on the user-defined spectral
line centre and width parameters. Since the PHANGS-ALMA observations consisted of only one main array configuration combined
with the ACA and TP, the ability to combine two main array configurations had to be added. This modification also included adding
angular scales to use in Band 6 multi-scale cleaning of our extended
main array configuration data. Additionally, PHANGS-ALMA data
consisted of only Band 6 observations, primarily focused on [12] CO
( _𝐽_ =2–1). Steps like channel binning had to be made to handle additional lines in the NGC 4038/9 observations, e.g. [12] CO (1–0), [13] CO
(2–1), CN (1–0), etc. This modification also included the addition of
angular scale specifications for the Band 3 multi-scale cleaning. Coding bugs were fixed that prevented clean masks from being used in
the single-scale clean step and from manually specifying image and
pixel sizes. At this stage we also added the ability to manually specify
the “robust,” “nchan,” “start,” “uvrange,” and “uvtaper” arguments
to _tclean_ .

Given the volume of data and computing resources available, we


MNRAS **000**, 1–14 (2024)

14 _N. Brunetti et al._


had to switch to setting “chanchunks” to −1 in _tclean_ since our highest resolution cubes could not fit in memory all at once. To further
improve memory management and processing speed, we removed
additional image padding in right ascension and declination during
imaging and instead added padding of the interferometric cubes before feathering to ensure the angular coverage was at least as large as
the TP cubes. The final change related to the cube size was adding
a check during writing masks to disk that would do the writing in
batches of channels to avoid memory issues for our largest cubes that
were about 16 GB in size. Since the pre-imaging regridding would
not guarantee exactly the same spectral channels would be filled with
data across all arrays, we added a call to the _split_ task to remove
one channel at each end of the imaging spectral windows (SPWs) to
avoid blank channels being included in the cube for cleaning. Finally,
substantial effort was also spent on properly capturing all casa logging output and redirecting it to output files. This message capturing
was missing in version one and made it difficult to ensure each step
was performed correctly as well as verifying adjustments to the code
for the Antennae observations.

Table A1 gives a summary of the observations and the calibration method used for each individual observation. Figure A1 show
the resulting maps processed at 150 pc resolution for comparison to
Figure 2 at 55 pc resolution.


**APPENDIX B:** **DATA TABLES**


We provide the binned data used in this paper for both NGC 4038/9
and NGC 3256 as two separate machine-readable tables (see Table B1 and B2 for format). In these tables, each row reports our
measurements for one pixel in one galaxy; pixel values at different
physical resolutions are reported sequentially. The contents of the
rows are as follows:


(i) The resolution (beam FWHM) of the dataset in parsecs.
(ii) the right ascension and declination of the pixel in degrees.
(iii) The logarithmic value of the molecular gas surface density,
Σ mol in M ⊙ pc [2] ; the velocity dispersion, _𝜎_ v in km s [−][1] ; the peak
brightness temperature, _𝑇_ B in K; the virial parameter, _𝛼_ vir ; and the
logarithmic value of the turbulent pressure, _𝑃_ turb, in K km s [−][1] .

(iv) The projected distances of the pixel from each of the two
nuclei, in kpc.


Table B1 also indicates whether or not a pixel lies in the overlap
region. Table B2 indicates whether or not a pixel lies in the north or
south portion of the jet or the west exclusion zone; see Brunetti et al.
(2021) for details.


This paper has been typeset from a TEX/L [A] TEX file prepared by the author.


MNRAS **000**, 1–14 (2024)

_Molecular cloud properties of the Antennae_ 15


**Table A1.** Summary of observations and calibration methods.


Array Band Observation Repeats Minimum Maximum casa Pipeline
date baseline [a] baseline [a] version version

(m) (m)


12 m 3 2018 Oct 30 1 15 1400 5.4.0-68 42030M [b]

12 m 3 2018 Nov 1 1 15 1400 5.4.0-68 42030M [b]

12 m 3 2018 Nov 3 1 15 1400 5.4.0-68 42030M [b]

12 m 3 2018 Nov 4 2 15 1400 5.4.0-68 42030M [b]

12 m 3 2018 Nov 6 2 15 1400 5.4.0-68 42030M [b]

12 m 3 2018 Nov 8 1 15 1400 5.4.0-68 42030M [b]

12 m 3 2018 Nov 14 1 15 1400 5.4.0-68 42030M [b]

12 m 3 2018 Nov 17 1 15 1400 5.4.0-68 42030M [b]

12 m 6 2018 Nov 11 2 15 1400 5.4.0-70 42254M [b]

12 m 6 2019 Apr 16 2 15 741 5.4.0-70 42254M [b]

12 m 3 2019 Jan 1 2 15 500 5.4.0-70 42254M [b]

12 m 3 2019 Jan 5 1 15 500 5.4.0-70 42254M [b]

12 m 6 2019 Jan 11 1 15 314 5.4.0-70 42254M [b]

7 m 3 2018 Oct 23 1 9 45 5.4.0-68 42030M [b]

7 m 3 2018 Nov 6 2 9 49 5.4.0-68 42030M [b]

7 m 3 2018 Dec 4 1 9 49 5.4.0-68 42030M [b]

7 m 3 2018 Dec 9 1 10 49 5.4.0-68 42030M [b]

7 m 3 2018 Dec 11 1 9 49 5.4.0-68 42030M [b]

7 m 3 2018 Dec 15 1 9 49 5.4.0-68 42030M [b]

7 m 3 2018 Dec 16 2 9 49 5.4.0-68 42030M [b]

7 m 3 2018 Dec 17 1 9 49 5.4.0-68 42030M [b]

7 m 6 2018 Oct 16 4 9 49 5.4.0-68 42030M [b]

7 m 6 2018 Oct 20 2 9 49 5.4.0-68 42030M [b]


TP 3 2018 Oct 23 1 . . . . . . 4.7.2 ca9f82c [c]


TP 3 2018 Nov 12 1 . . . . . . 4.7.2 ca9f82c [c]


TP 3 2018 Nov 25 1 . . . . . . 4.7.2 ca9f82c [c]


TP 3 2018 Nov 27 2 . . . . . . 4.7.2 ca9f82c [c]


TP 3 2018 Nov 29 1 . . . . . . 4.7.2 ca9f82c [c]


TP 3 2018 Dec 3 2 . . . . . . 4.7.2 ca9f82c [c]


TP 3 2018 Dec 4 1 . . . . . . 4.7.2 ca9f82c [c]


TP 3 2018 Dec 5 1 . . . . . . 4.7.2 ca9f82c [c]


TP 3 2018 Dec 6 1 . . . . . . 4.7.2 ca9f82c [c]


TP 3 2018 Dec 8 2 . . . . . . 4.7.2 ca9f82c [c]


TP 3 2018 Dec 9 3 . . . . . . 4.7.2 ca9f82c [c]


TP 6 2018 Oct 24 1 . . . . . . 4.7.2 ca9f82c [c]


TP 6 2018 Oct 30 1 . . . . . . 4.7.2 ca9f82c [c]


TP 6 2018 Oct 31 2 . . . . . . 4.7.2 ca9f82c [c]


_Notes._ All interferometric observations were multiple-pointing mosaics covering an area
approximately 2 _._ 8 × 1 _._ 9 arcmin, centred on (12 [h] 01 [m] 53 [s], −18°52 [′] 30 [′′], J2000).
a Projected for source position on the sky.
b ALMA observatory pipeline. All observatory pipeline versions were followed by “(PipelineCASA54-P1-B).”
c PHANGS-ALMA TP pipeline obtained from `[https://github.com/PhangsTeam/TP_](https://github.com/PhangsTeam/TP_ALMA_data_reduction)`
`[ALMA_data_reduction](https://github.com/PhangsTeam/TP_ALMA_data_reduction)` . Version hash is the Git commit at which we obtained the pipeline.


**Table B1.** Binned data for NGC 4038/9 used in this paper


Beam R.A. Decl. log Σ mol _𝜎_ v T B _𝛼_ vir log P turb NGC4908 NGC4039 overlap
FWHM [1] distance distance region?

55.0 180.470384 -18.892159 1.684 3.3 0.91 1.91 4.677 9.587 2.518 False

80.0 180.470997 -18.892576 1.646 3.5 0.82 1.60 4.524 9.746 2.599 False

90.0 180.470997 -18.892589 1.6450 3.6 0.73 1.61 4.464 9.751 2.604 False

120.0 180.471988 -18.892628 1.528 4.1 0.50 1.98 4.378 9.775 2.546 False

150.0 180.471988 -18.892589 1.420 3.4 0.49 1.36 4.003 9.760 2.531 False
1 This table is available in its entirety in machine-readable form.


MNRAS **000**, 1–14 (2024)

16 _N. Brunetti et al._


Σ (M _⊙_ pc _[−]_ [2] )
250 1500 3800 7100 12000


_−_ 18 _[◦]_ 51 _[′]_ 30 _[′′]_


52 _[′]_ 00 _[′′]_


30 _[′′]_


53 _[′]_ 00 _[′′]_



_σ_ _v_ (km s _[−]_ [1] )
10 30 55 85 120



_T_ B _,_ max (K)
1 4 8 14 20







30 _[′′]_


_−_ 18 _[◦]_ 51 _[′]_ 30 _[′′]_


52 _[′]_ 00 _[′′]_


30 _[′′]_


53 _[′]_ 00 _[′′]_


30 _[′′]_



12 [h] 01 [m] 56 [s] 54 [s] 52 [s] 50 [s]



_α_ vir
2 4 6 8 10



_P_ turb _/k_ B (10 [6] K cm _[−]_ [3] )
1 20 200 1000 4000



RA (J2000)







12 [h] 01 [m] 56 [s] 54 [s] 52 [s] 50 [s]


RA (J2000)



12 [h] 01 [m] 56 [s] 54 [s] 52 [s] 50 [s]


RA (J2000)



**Figure A1.** The same as Figure 2 but showing the molecular gas properties at 150 pc resolution. See the Figure 2 caption for more details.


**Table B2.** Binned data for NGC 3256 from Brunetti et al. (2021) used in this paper


Beam R.A. Decl. log Σ mol _𝜎_ v T B _𝛼_ vir log P turb N nucleus S nucleus north south west
FWHM [1] distance distance jet? jet? region?

55.0 156.958656 -43.908402 1.459 8.1 1.09 19.13 5.226 23.257 92.168 False False True

80.0 156.958290 -43.908435 1.398 7.8 0.79 14.07 4.971 24.641 95.893 False False True

120.0 156.959157 -43.909034 1.348 7.1 0.69 8.77 4.665 26.925 131.593 False False True
1 This table is available in its entirety in machine-readable form.


MNRAS **000**, 1–14 (2024)


</paper>

## Items to check

```json
[
 {
  "path": "processing.imaging.continuum_subtraction.evidence[0]",
  "value": "Automated continuum subtraction based on user-defined spectral line centre and width for interferometric data; order-one polynomial (linear) fits for TP data",
  "failed_quote": "We used a modified version that does not perform any spectral binning and all continuum subtraction was carried out using order-one polynomial (linear) fits to the continuum levels."
 },
 {
  "path": "processing.imaging.smoothing.evidence[0]",
  "value": "Convolved to circular synthesized beams with FWHM physical sizes of 55, 80, 90, 120, and 150 pc; no spectral binning on TP data",
  "failed_quote": "We used a modified version that does not perform any spectral binning and all continuum subtraction was carried out using order-one polynomial (linear) fits to the continuum levels."
 },
 {
  "path": "processing.inherited[1].what.evidence[0]",
  "value": "Total Power (TP) data calibration and imaging procedure",
  "failed_quote": "TP data processing was carried out with the PHANGS-ALMA TP calibration and imaging pipeline for casa in casa version 4.7.2 (see Table A1 for more details). Herrera et al. (2020) describe the full details of the pipeline procedure."
 },
 {
  "path": "analysis_steps[0].key_parameters[2].evidence[0]",
  "value": "TP continuum subtraction: order-one polynomial (linear)",
  "failed_quote": "We used a modified version that does not perform any spectral binning and all continuum subtraction was carried out using order-one polynomial (linear) fits to the continuum levels."
 },
 {
  "path": "analysis_steps[0].fitting.evidence[0]",
  "value": "Order-one polynomial (linear) fits for TP continuum subtraction",
  "failed_quote": "We used a modified version that does not perform any spectral binning and all continuum subtraction was carried out using order-one polynomial (linear) fits to the continuum levels."
 },
 {
  "path": "analysis_steps[2].method.evidence[2]",
  "value": "Divide pixels into nuclear (< 1 kpc from either nucleus), non-nuclear (> 1 kpc), and Whitmore et al. (2014) CO (3-2) overlap region FoV sub-samples. Apply the same 1 kpc nuclear separation to PHANGS-ALMA galaxies. Compute mass-weighted medians, inner 68th percentiles, and 1D/2D Gaussian kernel density estimators (KDEs) to compare NGC 4038/9 with NGC 3256 and 70 PHANGS-ALMA galaxies.",
  "failed_quote": "All PDFs are made from Gaussian KDEs, with bandwidths automatically chosen using the scipy implementation of Scott’s Rule (Scott 1992)."
 },
 {
  "path": "analysis_steps[2].key_parameters[1].evidence[0]",
  "value": "Gaussian KDE bandwidth selection: Scott's Rule",
  "failed_quote": "All PDFs are made from Gaussian KDEs, with bandwidths automatically chosen using the scipy implementation of Scott’s Rule (Scott 1992)."
 },
 {
  "path": "analysis_steps[2].fitting.evidence[0]",
  "value": "Gaussian kernel density estimation using Scott's Rule for bandwidth selection",
  "failed_quote": "All PDFs are made from Gaussian KDEs, with bandwidths automatically chosen using the scipy implementation of Scott’s Rule (Scott 1992)."
 },
 {
  "path": "software[4].used_for.evidence[0]",
  "value": "Astronomy Python package used in data analysis",
  "failed_quote": "This research made use of Astropy, a community-developed core Python package for Astronomy (http://www.astropy.org, Astropy Collaboration et al. 2013, 2018)."
 }
]
```
