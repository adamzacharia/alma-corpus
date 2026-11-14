# Repair task for a Claude Code subagent

A methods card has evidence quotes that were not found verbatim in the paper. Below are the rules, the paper, and the failing items. Write ONE JSON object, nothing else, of the form {"repairs": [{"path": ..., "found": true|false, "loc": ..., "quote": ...}, ...]} with one entry per item (path unchanged) to:

    C:\Users\adama\alma-corpus\cards\2020A%26A...639A..87V\sonnet\repair_reply.txt

Use the Write tool for that file. Copy each quote character for character from the paper text below; a returned quote is checked mechanically and dropped if it is not in the paper. Do not read any other file, do not run commands, and do not change anything else. Reply with one line when done.

---

## Rules

You check evidence quotes for a methods card extracted from an astronomy paper. Some quotes could not be found verbatim in the paper text, and some stated values came without a quote. For each item: find the passage in the paper that supports the value and copy it VERBATIM (same words and order, at most 40 words; LaTeX markup may be dropped) with its loc (section heading, "abstract", "Table N" or "Figure N caption"). If the paper does not support the value, return found = false and leave quote and loc empty. Use only the paper text. Return one entry per item, with the item's path unchanged.

## Paper

<paper>
_Astronomy & Astrophysics_ manuscript no. COM_paper ⃝c ESO 2020
May 15, 2020

## **Complex organic molecules in low-mass protostars on solar** **system scales**

### **I. Oxygen-bearing species**


M. L. van Gelder [1], B. Tabone [1], Ł. Tychoniec [1], E. F. van Dishoeck [1][,][ 2], H. Beuther [3], A. C. A. Boogert [4], A. Caratti o
Garatti [5], P. D. Klaassen [6], H. Linnartz [7], H. S. P. Müller [8], and V. Taquet [9]


1 Leiden Observatory, Leiden University, PO Box 9513, 2300RA Leiden, The Netherlands
e-mail: `vgelder@strw.leidenuniv.nl`
2 Max Planck Institut für Extraterrestrische Physik (MPE), Giessenbachstrasse 1, 85748 Garching, Germany
3 Max Planck Institute for Astronomy, Königstuhl 17, 69117 Heidelberg, Germany
4 Institute for Astronomy, University of Hawaii at Manoa, 2680 Woodlawn Drive, Honolulu, HI 96822, USA
5 Dublin Institute for Advanced Studies, School of Cosmic Physics, Astronomy and Astrophysics Section, 31 Fitzwilliam Place,
D04C932 Dublin 2, Ireland
6 UK Astronomy Technology Centre, Royal Observatory Edinburgh, Blackford Hill, Edinburgh EH9 3HJ, UK
7 Laboratory for Astrophysics, Leiden Observatory, Leiden University, PO Box 9531, 2300RA Leiden, The Netherlands
8 I. Physikalisches Institut, Universität zu Köln, Zülpicher Str. 77, 50937 Köln, Germany
9 INAF, Osservatorio Astrofisico di Arcetri, Largo E. Fermi 5, 50125 Firenze, Italy


Received XXX; accepted XXX


**ABSTRACT**


_Context._ Complex organic molecules (COMs) are thought to form on icy dust grains in the earliest phase of star formation. The
evolution of these COMs from the youngest Class 0/I protostellar phases toward the more evolved Class II phase is still not fully
understood. Since planet formation seems to start early, and mature disks are too cold for characteristic COM emission lines, studying
the inventory of COMs on solar system scales in the Class 0/I stage is relevant.
_Aims._ The aim is to determine the abundance ratios of oxygen-bearing COMs in Class 0 protostellar systems on scales of ∼100 AU
radius. These abundances will be inter-compared, and contrasted to other low-mass protostars such as IRAS16293-2422B and HH 212.
Additionally, using both cold and hot COM lines, the gas-phase abundances can be tracked from a cold to a hot component, and
ultimately be compared with those in ices to be measured with the _James Webb Space Telescope_ (JWST). The abundance of deuterated
methanol allows us to probe the ambient temperature during the formation of this species.
_Methods._ ALMA Band 3 (3 mm) and Band 6 (1 mm) observations are obtained of seven Class 0 protostars in the Perseus and Serpens
star-forming regions. By modeling the inner protostellar region using ’LTE’ models, the excitation temperature and column densities
are determined for several O-bearing COMs including methanol (CH 3 OH), acetaldehyde (CH 3 CHO), methyl formate (CH 3 OCHO),
and dimethyl ether (CH 3 OCH 3 ). Abundance ratios are taken with respect to CH 3 OH.
_Results._ B1-c and B1-bS (both Perseus) and Serpens S68N (Serpens) show COM emission, i.e., three out of the seven of the observed
sources. No clear correlation seems to exist between the occurrence of COMs and source luminosity. The abundances of several COMs
such as CH 3 OCHO, CH 3 OCH 3, acetone (CH 3 COCH 3 ), and ethylene glycol ((CH 2 OH) 2 ) are remarkably similar for the three COMrich sources, and to IRAS 16238-2422B and HH 212, even though these sources originate from four different star-forming regions
(i.e., Perseus, Serpens, Ophiuchus, Orion). For other COMs like CH 3 CHO, ethanol (CH 3 CH 2 OH), and glycolaldehyde (CH 2 OHCHO),
the abundances differ by up to an order of magnitude, indicating that local source conditions are case determining. B1-c hosts a cold
( _T_ ex ≈ 60 K), more extended component of COM emission with a column density of typically a few % of the warm/hot ( _T_ ex ∼ 200 K),
central component. A D/H ratio of 1–3 % is derived for B1-c, S68N, and B1-bS based on the CH 2 DOH/CH 3 OH ratio (taking into
account statistical weighting) suggesting a temperature of ∼15 K during the formation of methanol. This ratio is consistent with other
low-mass protostars, but lower than for high-mass star-forming regions.
_Conclusions._ The abundance ratios of most O-bearing COMs are roughly fixed between different star-forming regions, and are
presumably set at an earlier cold prestellar phase. For several COMs, local source properties become important. Future mid-infrared
facilities such as JWST/MIRI will be essential to directly observe COM ices. Combining this with a larger sample of COM-rich
sources with ALMA will allow for directly linking ice and gas-phase abundances in order to constrain the routes that produce and
maintain chemical complexity during the star formation process.


**Key words.** Astrochemistry – stars: formation – stars: protostars – stars: low-mass – ISM: abundances – techniques: interferometric



**1.** **Introduction**


Complex organic molecules (COMs) are molecules with six or
more atoms of which at least one atom is carbon (see review by
Herbst & van Dishoeck 2009). They have been observed toward



high-mass and low-mass star-forming regions, both in young
protostars (e.g., Caselli & Ceccarelli 2012; Jørgensen et al. 2016;
McGuire 2018; Bøgelund et al. 2019), and in protostellar outflows (e.g., Arce et al. 2008; Öberg et al. 2010). As a protostellar


Article number, page 1 of 44

_A&A proofs:_ manuscript no. COM_paper



system develops from the embedded Class 0/I phase toward the
more evolved Class II phase, the COMs may eventually either
be destroyed or become incorporated in the ice mantles of dust
grains or planetesimals in disks (Visser et al. 2009, 2011; Drozdovskaya et al. 2016). Since planet formation may start already
in the embedded Class 0/I phase (e.g., Harsono et al. 2018; Manara et al. 2018), studying the inventory and abundances of COMs
on solar system scales in the earliest stages of star formation is
essential to probe the initial conditions of planet formation. With
the launch of the _James_ _Webb_ _Space_ _Telescope_ (JWST) in the
near future, the ice abundances of COMs can be directly linked
to their gaseous counterpart.
In cold prestellar envelopes, formation of COMs happens
on the ice mantles of dust grains through hydrogenation of
smaller molecules such as CO (Charnley et al. 1992; Watanabe
& Kouchi 2002; Fuchs et al. 2009). This leads to the formation of
methanol (CH 3 OH), but these COMs may even get as complex
as, for example, glycolaldehyde (CH 2 OHCHO), ethylene glycol ((CH 2 OH) 2 ), and glycerol (HOCH 2 CH(OH)CH 2 OH) (Öberg
et al. 2009; Chuang et al. 2016, 2017; Fedoseev et al. 2017).
When the dust grains move inwards toward protostars, the ultraviolet (UV) radiation field increases (e.g., Visser et al. 2009;
Drozdovskaya et al. 2016), leading to the dissociation of some
COMs into smaller radicals (Gerakines et al. 1996; Öberg 2016).
These radicals react with other COMs in the ice mantles to form
larger species (Garrod & Herbst 2006; Garrod et al. 2008; Öberg
et al. 2009), and at higher temperatures perhaps through thermal
induced chemistry (Theulé et al. 2013). When the temperature
of the dust grains reaches _T_ ≈ 100 − 300 K, all COMs desorb
from the grains into the gas phase where they can be transformed
by high temperature gas-phase chemistry and UV radiation (e.g.,
Charnley et al. 1992; Balucani et al. 2015; Skouteris et al. 2018).
A fraction of the COMs may be incorporated into larger bodies
in the cold mid-plane of an accretion disk.
Another reason for studying COMs in the earliest (Class 0)
phase of star formation is that gaseous COM lines are hard to
detect in the Class I phase (e.g., Artur de la Villarmois et al.
2019). An exception is when a (more evolved) source undergoes an accretion burst; the sudden increase in luminosity can
release frozen COMs from the grains (van ’t Hoff et al. 2018; Lee
et al. 2019b). In the ice phase, they are difficult to observe, with
only well constrained abundances for CH 3 OH and some limits
or tentative detections for formic acid (HCOOH), acetaldehyde
(CH 3 CHO), and ethanol (CH 3 CH 2 OH) (see review by Boogert
et al. 2015; Terwisscha van Scheltinga et al. 2018).
Most studies of gaseous COMs have been carried out on
high-mass hot cores in massive star-forming regions such as
Sagittarius B2 and Orion KL, where COMs are typically present
in high abundances (e.g., Belloche et al. 2013; Neill et al. 2014;
Crockett et al. 2014; Pagani et al. 2017). In low-mass young stellar objects, single-dish observations with beams of a few thousand AU show that the abundances of oxygen-bearing COMs
with respect to CH 3 OH seem to be narrowly distributed (Bottinelli et al. 2004; Jørgensen et al. 2005; Bergner et al. 2017;
Belloche et al. 2020).
With the Atacama Large Millimeter/submillimeter Array
(ALMA), it is now possible to spatially resolve individual protostellar systems on scales of ∼50 AU. Additionally, the spectral coverage and sensitivity of ALMA allow a large variety of
COMs and corresponding isotopologues to be observed in optically thin lines, resulting in more accurate abundance determinations. Gaseous COMs have been studied mostly in the Class 0
IRAS 16293-2422 binary system (hereafter IRAS 16293) as part
of the ALMA PILS survey (Jørgensen et al. 2016). This led


Article number, page 2 of 44



to many detections of new species in the interstellar medium
(ISM) such as HONO (Coutens et al. 2019), CH 3 Cl (Fayolle
et al. 2017), and CHD 2 OCHO (Manigand et al. 2019). Furthermore, IRAS 16293 has been studied extensively for both oxygen and nitrogen-bearing COMs (Jørgensen et al. 2018; Calcutt
et al. 2018; Ligterink et al. 2018a,b; Manigand et al. 2020). Other
low-mass sources studied interferometrically on ∼ 50 − 150 AU
scales include HH 212 (Lee et al. 2019a), NGC 1333-IRAS 2A
and IRAS 4A (hereafter IRAS 2A and IRAS 4A; Taquet et al.
2015, 2019), L483 (Jacobsen et al. 2019), and three sources in
the Serpens Main star forming region (Bergner et al. 2019).


Single dish observations show hints of a cold, more extended
component of COM emission in Class 0 protostars where the
excitation temperature may drop below 20–60 K. This component is present additional to the ’typical’ warm/hot, more compact COM emission with _T_ ≳ 100 − 300 K (Bisschop et al.
2007; Isokoski et al. 2013; Marcelino et al. 2018). Currently, the
chemical relationship between the cold COMs on large scales
and warm/hot COMs on small scales is still unknown. The evolution of COMs from a cold extended component to a hot central component can be traced by observing COMs in multiple
frequency bands.


The Perseus and Serpens star-forming regions are known to
host many embedded protostars (e.g., Enoch et al. 2009; Tobin et al. 2016; Karska et al. 2018). In this paper, four protostellar regions with strong ice features in infrared observations (Boogert et al. 2008) are targeted with ALMA in Band 3
and Band 6. These targets are also part part of the JWST/MIRI
guaranteed time observations (GTO) program (project ID 1290).
JWST/MIRI will, for instance, observe the 7.2 µm and 7.4 µm
features for which CH 3 CH 2 OH and CH 3 CHO, respectively,
are strong candidates based on laboratory spectroscopy (e.g.,
Schutte et al. 1999; Terwisscha van Scheltinga et al. 2018).
Ultimately, this will allow for directly comparing gaseous and
icy COMs. Some additional nearby sources falling within the
ALMA field of view are also included here, leading to a total of seven sources: B1-b, B1-bS, B1-bN and B1-c in the
Perseus Barnard 1 cloud, and Serpens S68N (hereafter S68N),
Ser-emb 8 (N), and Serpens SMM3 (hereafter SMM3) in the
Serpens Main region.


B1-b (sometimes also referred to as B1-bW) is a bright infrared source with strong ice features in CH 3 OH and (potentially) CH 3 CHO (Öberg et al. 2011). B1-bN is a suggested first
hydrostatic core candidate (e.g., Pezzuto et al. 2012; Hirano &
Liu 2014; Gerin et al. 2017), and B1-bS is proposed as a hot
corino (Marcelino et al. 2018). B1-c is a young Class 0 object showing both strong CH 3 OH ice and gas COM features in
the hot corino (Boogert et al. 2008; Bergner et al. 2017), and
a high velocity outflow (Jørgensen et al. 2006; Hatchell et al.
2007). Moreover, all Barnard 1 objects have been extensively
studied in the VLA Nascent Disk and Multiplicity (VANDAM)
survey (Tobin et al. 2016; Tychoniec et al. 2018b), showing
compact disk-like structures at scales of several tens of AU. In
Serpens, S68N and SMM3 are both Class 0 sources studied in
detail by Kristensen et al. (2010). Hull et al. (2017) and Tychoniec et al. (2018a, 2019) observed several protostars in Serpens with ALMA, focusing on outflows. Interestingly, whereas
Ser-emb 8 (N) hosts a high velocity outflow, S68N only has
a slow velocity outflow. The characteristics of our targets are
shown in Table 1. We focus here on the O-bearing COMs in the
data; the N-bearing species will be part of a future paper.

M. L. van Gelder et al.: Complex organic molecules in low-mass protostars on solar system scales


**Table 1.** List of protostars discussed in this paper as well as their main astronomical properties.


Object Cloud RA (J2000) Dec (J2000) _d_ _L_ bol _T_ bol _M_ env CH 3 OH/H 2 O ice COMs detected?
(hh:mm:ss.ss) (dd:mm:ss.s) pc L ⊙ K M ⊙ (%) Band 3 Band 6
B1-b Perseus 03:33:20.34 31:07:21.3 320 _[1]_ 0.32 _[2]_ 151 _[2]_ 1.5 _[2]_ 11.2 _[3]_ n n
_B1-bN_ Perseus 03:33:21.21 31:07:43.6 320 _[1]_ 0.28 _[4]_ 17 _[4]_ 0.4 _[4]_ – n –
_B1-bS_ Perseus 03:33:21.36 31:07:26.3 320 _[1]_ 0.57 _[4]_ 22 _[4]_ 0.4 _[4]_ – y y
B1-c Perseus 03:33:17.88 31:09:31.8 320 _[1]_ 5.9 _[5]_ 46 _[5]_ 3.8 _[2]_ <7.1 _[3]_ y y
S68N Serpens 18:29:48.09 01:16:43.3 436 _[6]_ 5.4 _[7]_ 58 _[6]_ 9.4 _[7]_ – y y
_Ser-emb 8 (N)_ Serpens 18:29:48.73 01:16:55.6 436 _[6]_ – – – – n y _[8]_

SMM3 Serpens 18:29:57.75 01:14:06.7 436 _[6]_ 27.5 _[5]_ 37 _[5]_ – – n n _[9]_


**Notes.** The objects in italic additionally fell within the field of view of the ALMA observations. In the last 2 columns, yes (y) indicates that COMs
were detected in this work, no (n) indicates that the spectra lacked any COM detections, and – indicates that the Band was not observed for the
corresponding target.
( _1_ ) Ortiz-León et al. (2018). ( _2_ ) Enoch et al. (2009). ( _3_ ) Boogert et al. (2008). ( _4_ ) Hirano & Liu (2014). ( _5_ ) Karska et al. (2018). ( _6_ ) Ortiz-León et al.
(2017). [(] _[7]_ [)] Enoch et al. (2011). [(] _[8]_ [)] Only CH 3 OH emission related to the outflow detected. [(] _[9]_ [)] Based on data from ALMA program 2017.1.01350.S



**2.** **Observations**


ALMA Cycle 5 observations (project 2017.1.01174.S; PI: E.F.
van Dishoeck) were taken in Band 3 (3 mm) and Band 6 (1 mm).
The key targeted COMs were CH 3 OH, HCOOH, CH 3 CHO,
CH 3 OCHO, CH 3 CH 2 OH, and NH 2 CHO. We list the main technical properties of our ALMA images in Table E.1. For B1-bN
and SMM3, we lack Band 6 observations in our program. All
data were taken using the 12m array, with a synthesized beam of

∼ ∼
1.5–2.5" ( 500-1000 AU at the distances of our sources; C43-2
& C43-3 configuration) and ∼0.45" (∼100-200 AU; C43-4 configuration) for Band 3 and Band 6, respectively. The largest recoverable scales (LAS) were ∼20" (∼6000–9000 AU) and ∼6"
(∼2000-3000 AU) for Band 3 and Band 6, respectively. The
spectral resolution was ∼0.2 km s [−][1] for most spectral windows,
with a few windows in Band 3 having ∼0.3–0.4 km s [−][1] . At this
resolution, all lines are spectrally resolved. The line sensitivity
is ∼0.1 K. The absolute uncertainty on the flux calibration is
≤15% for all observations. For SMM3, we use archival Band 6
data (project 2017.1.01350.S; PI: Ł. Tychoniec) at similar spatial

∼
resolution ( 0.3") but lower spectral resolution (0.7 km s [−][1] ).


The images were primary beam corrected, with factors of ∼1
for sources in the center of the images (i.e., B1-b, B1-c, S68N,
SMM3), and ∼3 and ∼4 for B1-bS and Ser-emb 8 (N) in Band 6,
respectively. In Band 3 the primary beam correction for B1-bS,
B1-bN, and Ser-emb 8 (N) was ∼1.2, ∼2, and ∼1.3, respectively.


Continuum images were made using line-free channels in
all spectral windows. For the line-dense sources (e.g., B1-c)
the line-free channels were carefully selected to exclude any
line emission from the continuum images. Using the continuum solutions, all line data were continuum subtracted. From
the pipeline product data, it was clear that all COM emission (except CH 3 OH) was unresolved and centrally peaked on
all sources. Therefore, line images were made using a mask
size of a few times the size of the synthesized beam with the
CASA 5.1.1 _tclean_ task using a Briggs weighting of 0.5. Figure 1 shows the continuum overlayed on the spatial distribution
of CH 3 OH 2 1,1 –1 0,1 and CH 3 OCHO 21 7,14 –20 7,13 emission in
Band 6 from B1-c, S68N, and B1-bS. Figure 2 shows the emission of CH 3 OCH 3 7 0,7 –6 1,6 in Band 3. Spectra were extracted
from the central beam of the sources.



**3.** **Spectral modeling and results**


In the Band 3 and Band 6 spectra of B1-b, B1-bN, Ser-emb 8 (N),
and SMM3, COM emission features are absent at our detection
sensitivity (see Table E.1), except for spatially extended CH 3 OH
emission in Ser-emb 8 (N) which is related to the outflow (Tychoniec et al. 2018a, 2019). These sources are therefore excluded
in the further analysis and labeled as COM-poor sources. The
other sources, B1-c, S68N, and B1-bS, are labeled as COM-rich
sources, and analyzed further below.


_3.1._ _Methodology_


The spectral analysis tool CASSIS [1] was used to determine column densities and excitation temperatures of detected species.
The line lists of each molecule were taken from the CDMS
(Müller et al. 2001, 2005; Endres et al. 2016) [2] and JPL (Pickett
et al. 1998) [3] catalogs. The laboratory spectroscopy of molecules
discussed in this paper is introduced in Appendix A and a full
list of lines can be found in Tables E.2 and E.3 for Band 3 and
Band 6, respectively. On average, the transition upper energies
of the spectral lines are lower in Band 3 compared to Band 6.
The Band 3 and Band 6 data are modeled separately. For a fixed
_V_ lsr, a grid of column densities, excitation temperatures, and full
width half maximum (FWHM) of the line was set with steps
of 0.05 on a logarithmic scale, and 10 K and 0.1 km s [−][1] on a
linear scale, respectively. The total parameter space probed is
10 [13] –10 [17] cm [−][2], 50–550 K, and 0.5–9.0 km s [−][1], respectively;
for CH 2 DOH the explored parameter space of the column density is 10 [14] –5 × 10 [17] cm [−][2] . For species with a small number of
transitions in Band 6, the excitation temperature was fixed to
_T_ ex = 200 K, and only the column density and FWHM were
varied. For most species in Band 3, we had to assume that _T_ ex
is equal to the Band 6 temperature because the signal-to-noise
ratio (S/N) is too low to detect multiple spectral lines. Since the
FWHM of the lines in B1-bS was close to the spectral resolution
limit, we fixed the FWHM to 1 km s [−][1] .


1 `[http://cassis.irap.omp.eu/](http://cassis.irap.omp.eu/)`
2 `[https://cdms.astro.uni-koeln.de/](https://cdms.astro.uni-koeln.de/)`
3 `[https://spec.jpl.nasa.gov/](https://spec.jpl.nasa.gov/)`


Article number, page 3 of 44

_A&A proofs:_ manuscript no. COM_paper


**Fig. 1.** ALMA Band 6 moment 0 images of the COM-rich sources analyzed in this study: B1-c (left), S68N (middle), and B1-bS (right). In color
the spatial distribution of CH 3 OH 2 1,1 –1 0,1 (top row, _E_ up = 28 K) and CH 3 OCHO 21 7,14 –20 7,13 emission (bottom row, _E_ up = 170 K) is shown,
with the color scale shown on top of each image. The images are integrated over [-10,10] km s [−][1] with respect to the _V_ lsr . In the colorbar, the 3σ line
level is indicated with the black bar, with σ line = 4.0, 4.9, and 4.4 mJy beam [−][1] km s [−][1] for B1-c, S68N, and B1-bS, respectively. The continuum
is shown with the black contours with increasingly [3,5,8,12,18,21,30] σ cont, where σ cont is 1.5, 0.8, and 1.0 mJy beam [−][1] km s [−][1] for B1-c, S68N,
and B1-bS, respectively. The size of the beam is shown in the lower right of each image, and in the lower left a scale bar is displayed. The image
of B1-bS has a lower S/N since the source is located on the edge of the primary beam.



A source size of 0.45" (equal to the Band 6 beam) is used for
all sources. Given the equation for beam dilution:


θ s [2]
Dilutionfactor [−][1] =, (1)
θ [2]
b [+][ θ] [2s]


with θ s the (assumed) angular source size of 0.45" and θ b the
beam size, the beam dilution factor is ∼20 and 2 for Band 3 and
Band 6, respectively. In reality, the size of the emitting region is
smaller than the assumed 0.45" and any derived column densities are thus lower limits. The effect of a smaller source size is
discussed in Section 4.2

Each species is modeled separately, and optically thick lines
and blended lines are excluded from the fitting procedure. Assuming that the populations of all levels can be described by
a single excitation temperature _T_ ex, the χ [2] is computed for each


Article number, page 4 of 44



grid point, after which the best fitting model is determined by the
minimum reduced χ [2] . This method is often called ’local thermodynamic equilibrium (LTE)’ as the high-density limit of molecular excitation in which the excitation temperature approaches the
kinetic temperature _T_ kin . Strictly speaking, thermodynamic equilibrium implies that not only the excitation but also the motions,
ionization balance and radiation field are in equilibrium at the
same temperature. The word ’local’ refers to a specific region in
an atmosphere with varying temperature and density, having its
origin in stellar astrophysics. In radio astronomy of the interstellar medium, however, the word LTE often just implies a single
excitation temperature to characterize the level populations of a
molecule, which we will refer to here as ’LTE’.


The 2σ uncertainty on the column density, excitation temperature, and FWHM is computed from the grid. The main con

M. L. van Gelder et al.: Complex organic molecules in low-mass protostars on solar system scales


**Fig. 2.** Same as Fig. 1, but now for CH 3 OCH 3 7 0,7 –6 1,6 ( _E_ up = 25 K) in Band 3. Here, σ line = 6.3, 5.5, and 5.2 mJy beam [−][1] km s [−][1] for B1-c, S68N,
and B1-bS, respectively. The continuum contours are [3,5,8,12,18,21,30] σ cont, where σ cont is 0.46, 0.54, and 0.71 mJy beam [−][1] km s [−][1] for B1-c,
S68N, and B1-bS, respectively.


B1-c


8


6


4


2


0


260 _._ 025 260 _._ 050 260 _._ 075 260 _._ 100 260 _._ 125 260 _._ 150 260 _._ 175 260 _._ 200
Frequency (GHz)


**Fig. 3.** Part of the Band 6 spectrum of B1-c shown in black with the best fitting model overplotted in red. The window is centered around a few
CH 3 CHO, CH 3 OCHO, and CH 3 CH 2 OH lines. The focus here is on the O-bearing COMs; for this reason several transitions clearly visible in the
data (i.e., CH 3 CH 2 CN) do not show up in the fitting model. Lines in italics were excluded during the fitting.



tributors to the uncertainty are the assumption of ’LTE’, the flux
calibration error of ALMA, and the assumption of Gaussian line
profiles. For sources with a high line density, such as B1-c, many
lines had to be excluded from the fit due to line blending, therefore increasing the uncertainty on the column densities and excitation temperatures.


_3.2._ _Column densities and excitation temperatures_


The column densities and excitation temperatures of all COMrich sources are presented in Appendix B. We consider a derived
column density an upper limit if the error is more than 80% of
the corresponding best fitting value. The number of lines used
for fitting each species is listed in Table B.2. Upper limits (3σ)
to the column density are provided if no unblended lines are detected. For B1-c in Band 6, unambiguous detections (i.e., - 5
unblended lines identified) are made for [13] CH 3 OH, CH [18] 3 [OH,]
CH 2 DOH, CH 3 CHO, CH 3 OCHO, CH 3 OCH 3, CH 3 COCH 3, and
aGg’(CH 2 OH) 2 . For S68N and B1-bS, line blending and sen


sitivity hampered unambiguous detections for several of these
COMs, but tentative detections can still be made for most
species. H 2 CCO and t-HCOOH show < 3 detected transitions, and their identifications are therefore considered tentative.
gGg’(CH 2 OH) 2 and CH 2 OHCHO are only detected toward B1-c
in Band 6; for all other sources (and B1-c Band 3) we put upper
limits on the column density for an excitation temperature of
200 K. Due to the absence of any optically thin CH 3 OH lines in
our data, the column density of CH 3 OH is determined by scaling it from [13] CH 3 OH for Band 3 and CH [18] 3 [OH] [for] [Band] [6] [(us-]
ing [12] C/ [13] C ∼ 70 and [16] O/ [18] O ∼ 560 for the local ISM; Milam
et al. 2005; Wilson & Rood 1994). In Fig. 3, part of the Band 6
spectrum of B1-c is shown with the best fitting model overlayed.
The full Band 6 spectra with best-fit model of all sources can
be found in Appendix C. The full Band 3 spectrum of B1-c is
presented in Appendix D.


B1-c is the most COM rich source of our sample. The measured column densities in Band 6 vary between 1.9 × 10 [18] cm [−][2]
for CH 3 OH and 7.0 × 10 [14] cm [−][2] for t-HCOOH in a ∼150 AU


Article number, page 5 of 44

_A&A proofs:_ manuscript no. COM_paper


**Table 2.** Column densities of CH 3 OH and abundance fractions (%) with respect to CH 3 OH for all COM rich sources.


B1-c S68N B1-bS
Species Name Band 3 Band 6 Band 3 Band 6 Band 3 Band 6
CH 3 OH Methanol 18 ± 4 19 ± 6 3.6 ± 0.8 14 ± 6 2.4 ± 0.7 5.0 ± 0.6
13 CH 3 OH ≡ 1.43 1.0 ± 0.3 ≡ 1.43 0.7 ± 0.3 ≡ 1.43 0.3 ± 0.1
CH [18] 3 [OH] < 1.0 ≡ 0.18 < 2.8 ≡ 0.18 < 4.2 ≡ 0.18
CH 2 DOH 5.7 ± 2.1 8.4 ± 2.8 < 13 4.3 ± 1.9 < 9.9 < 4.7
CH 3 CH 2 OH Ethanol 1.6 ± 0.9 0.8 ± 0.3 < 5.6 0.22 ± 0.09 < 8.3 < 0.6
CH 3 CHO Acetaldehyde 1.3 ± 0.5 0.2 ± 0.1 < 1.4 0.07 ± 0.03 < 2.1 0.13 ± 0.02
CH 3 OCHO Methyl formate 2.3 ± 1.0 1.0 ± 0.3 0.29 ± 0.07 1.1 ± 0.5 6.1 ± 1.8 0.75 ± 0.10
CH 3 OCH 3 Dimethyl ether 1.0 ± 0.2 1.3 ± 0.4 1.8 ± 0.4 0.9 ± 0.4 4.3 ± 1.2 1.3 ± 0.2
CH 3 COCH 3 Acetone < 2.8 0.4 ± 0.1 < 14 0.4 ± 0.2 < 21 0.10 ± 0.03
aGg’(CH 2 OH) 2 Ethylene glycol < 2.4 0.3 ± 0.1 < 12 0.16 ± 0.07 < 18 < 0.43
gGg’(CH 2 OH) 2 < 1.2 0.4 ± 0.1 < 6 < 0.81 < 8.9 < 0.43
CH 2 OHCHO Glycolaldehyde < 0.89 0.11 ± 0.04 < 2.2 < 0.06 < 3.3 < 0.064
H 2 CCO Ketene – 0.07 ± 0.02 – 0.07 ± 0.03 – 0.03 ± 0.01
t-HCOOH Formic acid 0.5 ± 0.1 0.04 ± 0.02 < 1.4 0.07 ± 0.03 < 4.2 < 0.1


**Notes.** The CH 3 OH entry is the column density in 10 [17] cm [−][2] in a 0.45" beam derived from [13] CH 3 OH for Band 3 and CH [18] 3 [OH for Band 6 using]
12 C/ 13 C = 70 and 16 O/ 18 O = 560, respectively. All other entries are abundances with respect to CH 3 OH (in %). The errors are derived from the
2σ (95%) uncertainties on the column densities. Abundance ratios which are set to their respective isotope ratio are indicated with a ≡ symbol.



diameter region. Our derived column density for CH 2 OHCHO
is 2.0 × 10 [15] cm [−][2] . Most COMs show column densities on the
order of ∼ 10 [15][−][16] cm [−][2] in both Band 3 and Band 6.


The column densities toward S68N are a factor ∼ 1.5 − 2
lower than toward B1-c. Similarly, the highest column density is derived for CH 3 OH (1.4 × 10 [18] cm [−][2] ), the lowest for
t-HCOOH (9.1 × 10 [14] cm [−][2] ) in Band 6, and ∼ 10 [15][−][16] cm [−][2] for
most COMs.


B1-bS has the lowest column densities measured in this sample, up to an order of magnitude lower than toward B1-c with
values of the order of ∼ 10 [14][−][17] cm [−][2] . It was located in the edge
of our ALMA field of view, resulting in a lower sensitivity and
an increased level of noise. Our derived column densities (for a
source size of 0.45") are up to a factor of a few lower than those
derived by Marcelino et al. (2018) for a 0.35" source size, which
is roughly the difference in beam dilution.


For molecules with multiple lines for which a _T_ ex is derived, the average excitation temperature in Band 3 is ∼ 30 K
lower than in Band 6. The average FWHM for B1-c and S68N in
Band 6 is 3.3±0.2 and 5.0±0.2 km s [−][1], respectively (the FWHM
for B1-bS was fixed to 1 km s [−][1] ). In Band 3 this is 3.1 ± 0.2 and
4.5 ± 0.5, respectively.The average FWHM in Band 3 is thus
slightly lower than in Band 6 for B1-c and S68N, but within the
uncertainties. This matches the expectation that the Band 3 observations trace the colder more extended regions and Band 6
being more sensitive to warmer compact regions since the transition upper energies in Band 3 are on average lower than in
Band 6 (see Tables E.2 and E.3) and because the beam size and
LAS are larger. When the Band 3 excitation temperature of all
species for which _T_ ex was fixed is decreased by 30 K, no significant changes in the column densities and abundances arise. In
Table B.3, the results of a fit with _T_ ex = 100 K to the Band 3 data
are presented. The derived column densities are typically about
a factor ∼ 2 lower than derived with _T_ ex as a free parameter or
fixed to 200 K.


Article number, page 6 of 44



_3.3._ _Relative abundances_


Clear isotopologue detections are only made for methanol. The
13 CH 3 OH/CH 183 [OH abundance ratio is][ <][ 6 for all targets, which]
is lower than the elemental value of ∼ 8. This hints at the possibility that even [13] CH 3 OH is optically thick for these sources.
The CH 2 DOH/CH 3 OH ratio is on the order of ∼ 1 − 10%. Hints
for features of isotopologues are seen for partially deuterated
ethanol (CH 2 DCH 2 OH) and methyl formate (CH 3 O [13] CHO), but
these lines are too weak to allow for an unambiguous confirmation and deriving physical properties.


In order to compare our derived column densities, we determine the abundance ratios of each species with respect to
CH 3 OH. Because the usual tracer of H 2, CO, comes from more
extended regions, CH 3 OH is chosen as the reference species.
In Table 2, the derived abundances are presented for the three
COM rich sources. The abundances between B1-c and S68N
vary within a factor 2-3. This may simply be an effect of the
source properties; the lines in S68N are, for example, a factor
∼ 1.5 broader (∼5.0 km s [−][1] and ∼3.3 km s [−][1] in Band 6, respectively) resulting in more blended lines. In S68N, our abundances
of CH 3 OCHO, CH 3 OCH 3, and H 2 CCO are an order of magnitude lower than those derived by Bergner et al. (2019). The
discrepancies are potentially due to different approaches to optical depth correction. Our observations of B1-bS have a low
S/N. Nevertheless our derived abundance ratios coincide within
a factor of a few with the hot (200 K) component modeled by
Marcelino et al. (2018).


The abundances in Band 3 for B1-c deviate within a factor of
∼2 from the abundances derived in Band 6. Only CH 3 CHO and
t-HCOOH are more abundant based on the Band 3 data. In S68N,
CH 3 OCHO is less abundant in Band 3 whereas CH 3 OCH 3 is
more abundant. In B1-bS, both CH 3 OCHO and CH 3 OCH 3 are
significantly more abundant in Band 3, possibly because the column density of CH 3 OH is underestimated.

M. L. van Gelder et al.: Complex organic molecules in low-mass protostars on solar system scales



**4.** **Discussion**


_4.1._ _Occurrence of COMs in young protostars_


The emission of COMs is assumed to originate from inside the
_T_ dust ∼ 100 − 300 K radius. Using the relation of Bisschop et al.
(2007) for the 100 K radius in hot cores:



to what is found here; see Fig. 4. Our range of source luminosities is significantly smaller (up to ∼ 20 L ⊙ compared to 10 [6] L ⊙ ;
Taquet et al. 2015), and a similar scatter of abundances can be
seen for their lower luminosities.


_4.2._ _Dependence on source size_


In modeling the COM emission, a source size equal to the beam
size (0.45") was assumed for all sources. However, since the
emission is spatially unresolved, the source size in reality will
be smaller. A smaller emitting region will increase the derived
column densities, and may result in spectral lines actually being optically thick. We can test this scenario by assuming the
100 K diameter as a source size. This gives an emitting region of
0.23", 0.16" and 0.07" for B1-c, S68N, and B1-bS, respectively.
Assuming the lines remain optically thin, the column densities
derived for a 0.45" source size can be scaled to a smaller size by
computing the difference in beam dilution (see Eq. (1)):


θ s [2] 1 θ s [2] 2
_N_ 1 = _N_ 2, (3)
θ [2] θ [2]
b [+][ θ] [2s] [1] b [+][ θ] [2s] [2]


where _N_ 1,2 are the column densities for respective source sizes
θ s 1,2, andFor B1-c and S68N, the resulting column densities still give θ b is the beam size.
optically thin (τ < 0.1) lines for all species except CH 3 OH.
However, the lines of CH 3 OH are already optically thick for a
0.45" source size and the column density is derived from the
13 C and 18 O isotopologues, whose lines remain optically thin.
This means that the abundances derived previously in this work
for these two sources remain the same. For B1-bS most lines do
become optically thick (i.e., τ > 0.1), indicating that the abundances derived above in Table 2 for B1-bS should be used with

care.


_4.3._ _From cold (Band 3) to hot (Band 6) COMs_


The temperature in the envelopes of Class 0 sources is expected
to have an onion shell layered structure, with increasing temperature when moving closer to the star (e.g., Jørgensen et al. 2002).
In warmer layers the COMs could be be further processed to
form more complex molecules (on the dust grains) and, more importantly, will all be released from the dust grains when the temperature reaches _T_ dust ≈ 100 − 300 K. With our multi-Band observations, we can check for hints of this onion-layered temperature structure by comparing the excitation temperature of COMs
in Band 3, which is more sensitive to extended emission, to the
COMs in Band 6, which is more sensitive to compact emission.
Indeed, the average excitation temperature for the few species for
which an excitation temperature could be derived in Band 3 (i.e.,
CH 3 CH 2 OH, CH 3 OCHO, and CH 3 OCH 3 ) is about 30 K lower
than in Band 6. However, as mentioned in Section 3.2, no significant changes in the column densities and abundances arise if the
Band 3 excitation temperature of all species for which _T_ ex was
fixed is decreased by 30 K. The outcome of the Band 6 model
does not change when all lines with a low _E_ up < 100 K are excluded.

Jørgensen et al. (2018) modeled the abundances of O-bearing
COMs in IRAS 16293B and found that they can be divided in
two classes with temperatures of ∼ 125 K (warm) and ∼ 300 K
(hot). Most COMs in our sample have excitation temperatures of
∼ 200 K, which falls in the middle between these two classes.
Only CH 3 OCH 3 consistently shows _T_ ex ∼ 100 K, both in the
Band 3 and Band 6 observations for all sources. This agrees


Article number, page 7 of 44



_R_ _T_ =100K ≈ 15.4



_L_
AU, (2)
� _L_ ⊙



with _L_ the source luminosity, implies an _R_ _T_ =100K of 37.4 AU,
35.8 AU, and 11.6 AU for B1-c, S68N, and B1-bS, respectively.
Our Band 6 beam size of ∼0.45" (corresponding to a radius of
∼ 72 AU and ∼ 98 AU for Perseus and Serpens, respectively)
is larger than this radius and thus agrees with all COM emission
being unresolved, except for any CH 3 OH emission related to an
outflow.
Previous studies have found that a higher luminosity implies
more emission of COMs (e.g., Jørgensen et al. 2002; Young &
Evans 2005; Visser et al. 2009). Following Eq. 2 we would indeed expect that the occurrence of COM emission is correlated
to the source luminosity. Here, three of the seven sources studied
show emission of COMs. However, our most luminous source,
SMM3, does not exhibit any COM emission. On the other end,
the two sources with the lowest luminosity, B1-bN and B1-b, do
not show any COM emission either. Interestingly, B1-bS also has
a rather low luminosity but does exhibit emission of COMs. This
suggests that, for the targets that we observed, no clear correlation exists between the occurrence of gaseous COMs and source
luminosity.
Not finding such a correlation is surprising. The relation for
_R_ _T_ =100K in Eq. (2), however, assumes a spherically symmetric
infalling envelope (Bisschop et al. 2007). In reality, our Class 0
sources may be surrounded by an accretion disk (e.g., Tobin
et al. 2012; Murillo et al. 2013). The presence of a disk or disklike structure may shift the _R_ _T_ =100K inwards as the temperature
in the mid-plane of a disk-like structure is lower than in the
surface layers (e.g., Jørgensen et al. 2005; Visser et al. 2009).
However, even for a fixed _R_ _T_ =100K, the amount of material with
_T_ dust - 100K (e.g., high enough to release the COMs from the
dust grains) can vary between different sources due to, for example, differences in the disk mass and radius (Persson et al. 2016).
The absence of COM emission can also originate from other
source properties. B1-bN has been suggested as a first hydrostatic core candidate (e.g., Pezzuto et al. 2012; Hirano & Liu
2014; Gerin et al. 2017); the temperature in the inner regions
may not have reached the threshold for ice COM sublimation.
B1-b has a high bolometric temperature, and could therefore be
more evolved than the other sources. Here only a weak continuum is detected, indicating that B1-b may have a cleared inner
region; all gaseous COMs have either already been destroyed or
are incorporated as ices in the cold outer part. The strong ice absorption observed toward this source might originate in a region
that is more extended than the inner B1-b envelope (Öberg et al.
2011). SMM3 shows strong continuum, which may imply that
increased dust opacity hides any COM emission.
Despite the absence of a clear correlation between the occurrence of COM emission and source luminosity, an increase in
luminosity should result in higher temperatures and an increased
UV radiation field (Visser et al. 2009; Drozdovskaya et al. 2016).
The abundance of COMs with respect to CH 3 OH may therefore be related to the source luminosity. However, Taquet et al.
(2015) and Belloche et al. (2020) have shown that for most COM
abundances no clear correlation exists with luminosity, similar

_A&A proofs:_ manuscript no. COM_paper


**Fig. 4.** Abundance of CH 2 DOH (top left), CH 3 CH 2 OH (top right), CH 3 OCHO (bottom left), and CH 3 OCH 3 (bottom right) with respect to CH 3 OH
as function of bolometric source luminosity. Both the abundances in Band 3 (blue) and Band 6 (red) are plotted, where the Band 3 data-points are
slightly shifted in luminosity for clarity. Arrows denote upper limits. In gray, the abundances of IRAS 2A and IRAS 4A (Taquet et al. 2015, 2019),
HH 212 (Lee et al. 2019a), IRAS 16293A (Manigand et al. 2020), and IRAS 16293B (Jørgensen et al. 2018) are presented.



with Jørgensen et al. (2018), who classified CH 3 OCH 3 as a warm
species. However, some ambiguity remains, since CH 3 OCH 3 is
also observed to have hot components in, for instance, higher
mass cores (Belloche et al. 2013; Isokoski et al. 2013).


4.3.1. Multi-component model


The emission of COMs can be a superposition of a warm/hot
inner component, and a second colder and more extended component. Earlier observational studies have shown that indeed a
cold ( _T_ < 100 K, i.e., below the desorption temperature), more
extended component may be present (e.g., Bisschop et al. 2007;
Isokoski et al. 2013; Fayolle et al. 2015; Marcelino et al. 2018).
Using our data, a possible cold component can be probed by fitting a multi-component model to the Band 3 data. This is only
done for B1-c and S68N since the S/N of B1-bS in Band 3 is
insufficient to carry out such analysis. H 2 CCO, CH 3 COCH 3,
(CH 2 OH) 2, and CH 2 OHCHO are excluded from this analysis
due to the lack of clear detections in our Band 3 data.


For the warm/hot component, the best-fit model of Band 6 is
adopted. This component is kept fixed. As a second component,
a colder model is introduced. Here, an excitation temperature
of 60 K was assumed and only the column density was fitted for.
The FWHM was initially set as a free parameter, but fixed to that
of the warm/hot component in the cases that the fit results were
unconstrained. A source size of 2.0" (equal to Band 3 beam) is


Article number, page 8 of 44



assumed for the cold component, compared with the source size
of the warm component of 0.45".
The results are presented in Table 3. In Fig. 5 part of the
Band 3 spectrum of B1-c centered around several CH 3 OCHO
lines is shown. The abundances of Table 3 are presented in a
bar plot in Fig. 6. In B1-c, a cold ( _T_ ex = 60 K) and more extended component is detected for most species. The column density of this cold component is typically a few % but can rise up to
10% of the warm/hot inner component. The abundances of more
complex species in the cold component are higher than those in
the warm/hot component, which contradicts the idea that COMs
are more effectively processed and released from icy grains in
warmer layers. However, one should also note that the column
density of [13] CH 3 OH, and therefore CH 3 OH, is likely underestimated.

Only for CH 3 CH 2 OH and CH 3 OCHO, a FWHM of 3.3 ± 0.8
could be derived for the cold component which agrees with the
average FWHM of the warm/hot component of 3.3 ± 0.2. The
line width of the cold component can be expected to be smaller
since the emitting material is located further out in the envelope.
However, Murillo et al. (2018) find that lower resolution data
can also result in a larger line width, especially if the molecule
is associated with the outflow or its cavity.
The presence of a cold component of COM emission indicates that some gas-phase formation routes are already efficient in the cold envelope as most COMs formed through grainsurface chemistry are still frozen out at these temperatures. Or

M. L. van Gelder et al.: Complex organic molecules in low-mass protostars on solar system scales


B1-c


110.875 110.880 110.885 110.890

Frequency (GHz)


**Fig. 5.** Part of the Band 3 spectrum of the warm/hot ( _T_ ex ∼ 100−300 K)
compact (red), cold ( _T_ ex = 60 K) extended (blue), and combined (green)
model overlayed on the data (black). The spectral features are from
CH 3 OCHO, with the upper energy indicated on top.


alternatively, that other mechanisms are capable of transferring
the COMs from the solid state to the gas phase. Possible mechanisms include photodesorption (Fayolle et al. 2011; Muñoz
Caro et al. 2016), desorption of fragments following photodissociation (Bertin et al. 2016), low temperature co-desorption
(Fayolle et al. 2013; Ligterink et al. 2018c), or reactive desorption via a thermal hot-spot (Minissale et al. 2016; Chuang et al.
2018). Only for CH 3 OCH 3 and the deuterated and [18] O isotopologues of CH 3 OH, an extended component seems to be absent.
Formic acid is very abundant in the cold, extended component. This disagrees with the hot identification in IRAS 16293B
(Jørgensen et al. 2018), but is more consistent with the cold
identification in high-mass star-forming regions (Bisschop et al.
2007; Belloche et al. 2013) and it likely being an abundant ice
species (Öberg et al. 2011; Boogert et al. 2015). However, both
in Band 3 and Band 6, only 1–3 lines could be fitted, hence the
identification of t-HCOOH should be considered rather tentative.
In S68N, a cold component is less evident. Only for
CH 3 OCHO a cold column density is derived; for all other species
only upper limits are found. These results suggest that a possible
cold component would have a column density of ≲ 1% of the
warm component.


_4.4._ _Comparison to other sources_


Our Band 6 abundances are compared to the ALMA Band 7
abundances of IRAS 16293B (Jørgensen et al. 2018) and HH 212
(Lee et al. 2019a), see Fig. 7. The abundances of several COMs
(i.e., CH 2 DOH, CH 3 OCHO, CH 3 OCH 3, and CH 3 COCH 3 ) from
this work are very similar to IRAS 16293B and HH 212; the distribution of abundances seems to span only a factor of a few. The
abundances are also within a factor 3 of IRAS 2A and IRAS 4A
(Taquet et al. 2015). This similarity in abundances is rather interesting given that the source properties (e.g., _L_ bol, _T_ bol, etc.)
are different for all sources. For example, IRAS 2A has a luminosity of 36 L ⊙, whereas the luminosity of B1-bS is two orders of magnitude lower (0.57 L ⊙ ). A similarly large range is
seen for the bolometric temperature and envelope mass. Moreover, these sources originate from four different star-forming
regions: Perseus (B1-bS, B1-c, IRAS 2A, IRAS 4A), Serpens
(S68N), Ophiuchus (IRAS 16293B), and Orion (HH 212). Apparently, despite the differences in source properties and local
environment, the internal distribution of these COM abundances


Article number, page 9 of 44

_A&A proofs:_ manuscript no. COM_paper


B1-c

10 [2]


10 [1]


10 [0]


10 _[−]_ [1]


10 _[−]_ [2]


10 [2]









10 [1]


10 [0]


10 _[−]_ [1]


10 _[−]_ [2]

|1<br>0<br>1<br>2<br>13CH3OH<br>Abundanceofsevera<br>d6modelwitha0<br>.<br>rrorsareshowninb<br>= 70 an d 16O/ 18O<br>o f 13C H 3OH<br>.|Col2|Col3|Col4|Col5|Col6|Col7|Col8|Col9|Col10|Col11|Col12|Cold Warm/hot|Col14|Col15|Col16|Col17|Col18|Col19|Col20|Col21|Col22|Col23|Col24|Col25|Col26|Col27|Col28|Col29|Col30|Col31|Col32|Col33|Col34|Col35|Col36|Col37|Col38|Col39|Col40|Col41|Col42|Col43|Col44|Col45|Col46|Col47|Col48|Col49|Col50|Col51|Col52|Col53|
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
|13CH3OH<br>2<br>1<br>0<br>1<br> Abundance of severa<br>d 6 model with a 0.<br> rrors are shown in b<br> = 70 and 16O/18O <br> of 13CH3OH.||||||||||||Cold<br>Warm/hot|Cold<br>Warm/hot|Cold<br>Warm/hot|Cold<br>Warm/hot|Cold<br>Warm/hot|||||||||||||||||||||||||||||||||||||
|13CH3OH<br>2<br>1<br>0<br>1<br> Abundance of severa<br>d 6 model with a 0.<br> rrors are shown in b<br> = 70 and 16O/18O <br> of 13CH3OH.||||||||||||Cold<br>Warm/hot|Cold<br>Warm/hot|Cold<br>Warm/hot|Cold<br>Warm/hot|Cold<br>Warm/hot|||||||||||||||||||||||||||||||||||||
|13CH3OH<br>2<br>1<br>0<br>1<br> Abundance of severa<br>d 6 model with a 0.<br> rrors are shown in b<br> = 70 and 16O/18O <br> of 13CH3OH.|||||||||||||||||||||||||||||||||||||||||||||||||||||
|13CH3OH<br>2<br>1<br>0<br>1<br> Abundance of severa<br>d 6 model with a 0.<br> rrors are shown in b<br> = 70 and 16O/18O <br> of 13CH3OH.|||||||||||||||||||||||||||||||||||||||||||||||||||||
|13CH3OH<br>2<br>1<br>0<br>1<br> Abundance of severa<br>d 6 model with a 0.<br> rrors are shown in b<br> = 70 and 16O/18O <br> of 13CH3OH.||13CH<br> ndance<br> model <br> s are s<br>70 and <br>3CH3O|13CH<br> ndance<br> model <br> s are s<br>70 and <br>3CH3O|13CH<br> ndance<br> model <br> s are s<br>70 and <br>3CH3O|13CH<br> ndance<br> model <br> s are s<br>70 and <br>3CH3O|3OH<br> of sev<br> with a<br>  hown i<br> 16O/18<br>H.|3OH<br> of sev<br> with a<br>  hown i<br> 16O/18<br>H.|3OH<br> of sev<br> with a<br>  hown i<br> 16O/18<br>H.|era<br> 0.<br>  n b<br>O|CH1<br>3 <br>  l speci<br>45" so<br>   lack, w<br> = 560,|CH1<br>3 <br>  l speci<br>45" so<br>   lack, w<br> = 560,|8<br> OH<br>  es wit<br>urce si<br>   ith arr<br> respe|8<br> OH<br>  es wit<br>urce si<br>   ith arr<br> respe|8<br> OH<br>  es wit<br>urce si<br>   ith arr<br> respe|8<br> OH<br>  es wit<br>urce si<br>   ith arr<br> respe|h re<br>ze, <br>    ow<br> ctiv|CH2<br>   spect t<br> wherea<br>    s denot<br> ely. Th|CH2<br>   spect t<br> wherea<br>    s denot<br> ely. Th|CH2<br>   spect t<br> wherea<br>    s denot<br> ely. Th|CH2<br>   spect t<br> wherea<br>    s denot<br> ely. Th|DOH<br>    o CH3 <br>s the c<br>    ing up<br> e high|DOH<br>    o CH3 <br>s the c<br>    ing up<br> e high|OH<br>old<br>     per<br>  er a|OH<br>old<br>     per<br>  er a|CH3C<br> for ou<br> (_T_ex <br>     limits<br>  bunda|CH3C<br> for ou<br> (_T_ex <br>     limits<br>  bunda|CH3C<br> for ou<br> (_T_ex <br>     limits<br>  bunda|H2OH<br> r mult<br>= 60 K<br>     . The C<br>  nces in|H2OH<br> r mult<br>= 60 K<br>     . The C<br>  nces in|i-co<br>) c<br>      H3<br>   th|i-co<br>) c<br>      H3<br>   th|CH3<br>  mpone<br>ompon<br>OH co<br>   e cold|CH3<br>  mpone<br>ompon<br>OH co<br>   e cold|CHO<br>  nt ana<br>ent is <br> lumn<br>    compo|CHO<br>  nt ana<br>ent is <br> lumn<br>    compo|CHO<br>  nt ana<br>ent is <br> lumn<br>    compo|lysi<br> ﬁtte<br> dens<br>    nen|CH3O<br>  s. The<br>d wit<br> ity is<br>    t are li|CH3O<br>  s. The<br>d wit<br> ity is<br>    t are li|CH3O<br>  s. The<br>d wit<br> ity is<br>    t are li|CHO<br>   warm<br>h a mo<br>  determ<br>     kely d|(_T_e<br>re e<br>  ine<br>      ue t<br>|CH3<br>x ∼20<br>xtende<br>  d by sc<br>      o an u<br>|CH3<br>x ∼20<br>xtende<br>  d by sc<br>      o an u<br>|OCH3<br>0 K) c<br>d 2.0"<br>   aling f<br>       nderes<br>|om<br> so<br>    rom<br>       tim<br>|om<br> so<br>    rom<br>       tim<br>|t-HC<br> ponent<br>urce si<br> 13CH<br>       ate of|OOH<br>  is ﬁxe<br>ze. Th<br>3OH u<br>        the col<br>|OOH<br>  is ﬁxe<br>ze. Th<br>3OH u<br>        the col<br>|OOH<br>  is ﬁxe<br>ze. Th<br>3OH u<br>        the col<br>|d<br>e 2<br> si<br>         um<br>|
|||||||||||||||||||||||||||||||||||||||||||B1<br>B1|-bS<br>-c|-bS<br>-c|S68N<br>IRAS|1629|1629|3B|HH21|HH21|HH21|2|
||||||||||||||||||||||||||||||||||||||||||||||||||||||
||||||||||||||||||||||||||||||||||||||||||||||||||||||
||||||||||||||||||||||||||||||||||||||||||||||||||||||

CH 2 DOH CH 3 CH 2 OH CH 3 CHO CH 3 OCHO CH 3 OCH 3 CH 3 COCH 3 aGg’(CH 2 OH) 2 gGg’(CH 2 OH) 2 CH 2 OHCHO H 2 CCO t-HCOOH


**Fig.** **7.** Bar plot comparing our derived Band 6 abundances to other sources. The IRAS 16293B abundances for all species except (CH 2 OH) 2,
CH 2 OHCHO, and CH 3 COCH 3 are from Jørgensen et al. (2018); the (CH 2 OH) 2 and CH 2 OHCHO abundances are from Jørgensen et al. (2016),
and the CH 3 COCH 3 abundances from Lykke et al. (2017). The HH 212 abundances are from Lee et al. (2019a). The 2σ (95%) errors are shown in
black, with arrows denoting upper limits. We note that the abundances of our targets are remarkably similar and show comparable values to those
derived for IRAS 16293B and HH 212.



is roughly similar. This indicates that their formation schemes
must follow a rather universal recipe, for instance following
the atom addition and abstraction reaction networks proposed
to govern the surface chemistry in cold interstellar clouds (e.g.,
Chuang et al. 2016). This implies that solid-state processes are
already enriching the complex organic inventory of the interstellar medium in the prestellar phase.

Interestingly, our sources are under-abundant up to more
than one order of magnitude in CH 3 CH 2 OH, CH 3 CHO, and
CH 2 OHCHO compared with IRAS 16293B, HH 212, IRAS 2A
and IRAS 4A. Our abundances of these COMs do fall within a
factor of a few with IRAS 16293A (Manigand et al. 2020). This
suggests that for some COMs local source conditions do become
important for the formation or the destruction. The column density ratio of CH 3 OCHO to CH 2 OHCHO of B1-c is consistent
with the lower part of the bimodal distribution found by El-Abd
et al. (2019). For H 2 CCO and t-HCOOH, our sources also have
lower abundances. The abundance of t-HCOOH in the cold component of the multi component analysis (see Section 4.3.1) is
consistent with IRAS 16293B and HH 212. However, the detections of these species are rather tentative since only < 3 clear
unblended lines (not taking into account (hyper)fine structured
lines) are detected.

In more massive star-forming regions, a larger scatter in
COM abundances seems to be present. AFGL 4176 has abundances very similar to ours for most COMs (Bøgelund et al.


Article number, page 10 of 44



2019), whereas those in Orion KL show deviations: the abundance of CH 3 CH 2 OH is similar (Tercero et al. 2018), but
CH 3 OCHO, CH 3 OCH 3 have lower abundances in our sources,
and CH 3 COCH 3 higher abundances (see Table 6 in Bøgelund
et al. 2019). Even larger deviations are found toward Sagittarius B2, where the abundances of all COMs are higher by up to
an order of magnitude (Belloche et al. 2016).
The abundances derived here are higher than those in chemical models of a collapsing cloud for most COMs (e.g., Garrod
2013). Especially for CH 3 COCH 3 and (CH 2 OH) 2, these models underestimate the abundances by up to an order of magnitude. This may be a direct result for a still not fully characterized
solid-state and gas-phase chemistry and underlying gas-grain interactions (see discussion by Bøgelund et al. 2019).


_4.5._ _Comparison with ices_


No clear COM ice features have (yet) been observed toward any
of our COM-rich sources. However, toward B1-b (from the same
cloud as B1-c) hints for CH 3 CHO, CH 3 CH 2 OH, and t-HCOOH
ice have been detected with an abundance of ∼ 10% with respect to CH 3 OH (Öberg et al. 2011; Boogert et al. 2015). These
are higher than those derived for the gaseous warm/hot component in this work (∼ 0.1 − 1%). A possible explanation for
this is that, besides from typical grain-surface chemistry, additional gas-phase chemistry in the cold envelope can contribute

M. L. van Gelder et al.: Complex organic molecules in low-mass protostars on solar system scales



in transforming CH 3 OH into more complex species such as
CH 3 CHO and CH 3 CH 2 OH and thus lowering the abundance
of these species with respect to CH 3 OH (e.g., Balucani et al.
2015). Another explanation is that other non-thermal desorption
mechanisms, such as desorption of fragments following photodissociation (Bertin et al. 2016), are active.
To better compare the abundances of COMs in the ice and
gas phase, it is essential to directly observe the ices. However,
the above mentioned detections are still very uncertain, with only
CH 3 OH being securely identified in interstellar ices. Measuring
the column densities of interstellar COM ices remains difficult
since current infrared telescopes lack the sensitivity or wavelength coverage, and because the spectral features originating
from ices are broad and depend on the ice composition. Moreover, the number of COMs for which extensive high resolution infrared laboratory spectra have become available is limited
(Hudson et al. 2018; Terwisscha van Scheltinga et al. 2018). Future mid-infrared facilities such as JWST/MIRI will allow for
directly observing COMs in the ice, which will be essential for
studying their formation and evolution from the cold envelope
toward the warm inner regions.


_4.6._ _Temperature dependence of deuterated methanol_


The deuteration fraction of methanol is an indication of the temperature during the solid-state formation of this species. At low
temperatures, deuterium is more efficient than regular hydrogen
in the hydrogenation process on interstellar dust grains (e.g.,
Nagaoka et al. 2005). This leads to a higher deuteration fraction than the elemental ratio (D/H ∼ 10 [−][5] ; Caselli & Ceccarelli 2012). Bøgelund et al. (2018) investigated the effect of temperature during the formation of methanol with the astrochemical GRAINOBLE model (Taquet et al. 2012). In order to compare our methanol D/H ratios to their model results, our gasphase CH 2 DOH abundances have to be corrected for statistical
weights; a D atom has a 3 times higher probability to stick into
the CH 3 group than into the OH group. In Band 3, this gives a
D/H ratio of 1.9±0.7%, < 4.3%, and < 3.3% for B1-c, S68N, and
B1-bS respectively. In Band 6, this is 2.7 ± 0.9%, 1.4 ± 0.6%, and
< 1.6%. These deuteration fractions correspond to a temperature
during the formation of methanol of ∼ 15 K, where a density of
_n_ H = 10 [5][−][6] cm [−][3] was assumed (cf. Fig. 8 of Bøgelund et al.
2018).
Our derived methanol D/H fractions agree well with other
well-studied low-mass protostars such as IRAS16293B (∼ 2%;
Jørgensen et al. 2018), IRAS 2A and IRAS 4A (∼ 2% and ∼ 1%,

∼
respectively; Taquet et al. 2019), and HH 212 ( 1% after taking
into account statistical weights; Bianchi et al. 2017; Taquet et al.
2019). Our fractions are up to an order of magnitude higher than
for high-mass star-forming regions such as NGC 6334I (∼ 0.1%
on average; Bøgelund et al. 2018), and Sagittarius B2 (0.04%
after statistical correction; Belloche et al. 2016). The lower D/H
ratios in more massive star-forming regions hint at a higher temperature (i.e., > 20 K) already during the earliest phase of highmass star formation.


**5.** **Summary**


In this paper, the content of oxygen bearing COMs is studied in
seven young protostellar systems. High resolution ALMA observations in both Band 3 and Band 6 were used to determine the
column densities and excitation temperatures. The main conclusions are as follows:



**–** Three out of the seven sources exhibit warm COM emission features with typical _T_ ex ∼ 200 K. There seems to be
no correlation between the bolometric luminosity (and temperature) and occurrence of COMs of these Class 0 sources.
Other effects, such as disk formation and clearing of an inner
region, may play a role as well.

**–**
A multi-component model was introduced to check whether
a cold ( _T_ ex = 60 K), more extended component of COM
emission is present. Only B1-c shows clear signs of such a
cold component, with typically a few % of the column density of the warm component. This indicates that in the cold
envelope already gas-phase formation may take place and
that this could be a direct consequence of the grain-gas transitions of COMs or (radical) COM fragments. t-HCOOH is
significantly more abundant in the cold component, hinting
at the cold origin of this species.
**–** The abundance of several COMs (i.e., CH 2 DOH,
CH 3 OCHO, CH 3 OCH 3, CH 3 COCH 3, and (CH 2 OH) 2 )
are remarkably similar in comparison to other young
Class 0 protostars in different star-forming regions such as
IRAS 16293-2422B and HH 212. This similarity suggests
that the distribution of these COM abundances is roughly
fixed at an early cold, i.e, prestellar stage. However, the
abundances of some COMs (i.e., CH 3 CH 2 OH, CH 3 CHO,
and CH 2 OHCHO) in our sources differ significantly compared to IRAS 16293B and HH 212, possibly because local
source conditions become important and affect formation
and destruction pathways in different ways. Astrochemical
modeling will be needed to extend on these findings.
**–** The D/H ratio of deuterated CH 3 OH is around a few % for
all COM-rich sources, suggesting a dust temperature of ∼
15 K during its solid-state formation. The derived formation
temperature is similar to other low-mass protostars, but lower
than in high-mass star-forming regions (> 20 K).


Our sample of COM-rich protostars studied on solar system
scales remains small. It is still unknown how much of the prestellar cloud material is reprocessed during the evolution toward
protostellar systems and more evolved sources. The abundance
of most COMs in the ice phase is still highly uncertain. Future
mid-infrared facilities, most notably the _James Webb Space Tele-_
_scope_, will provide vital information on COM ices. A larger sample of COM-rich sources with ALMA, both in the Class 0 phase
and in the more evolved Class I phase where most COM emission has already disappeared, would provide better constraints
on the chemical complexity during these earliest phases of star
formation. The present work already shows that such studies will
be valuable, given the rich distribution in COMs discussed here.


_Acknowledgements._ This paper makes use of the following ALMA data:
ADS/JAO.ALMA#2017.1.01174.S and ADS/JAO.ALMA#2017.1.01350.S.
ALMA is a partnership of ESO (representing its member states), NSF (USA)
and NINS (Japan), together with NRC (Canada), MOST and ASIAA (Taiwan),
and KASI (Republic of Korea), in cooperation with the Republic of Chile.
The Joint ALMA Observatory is operated by ESO, AUI/NRAO and NAOJ.
Astrochemistry in Leiden is supported by the Netherlands Research School for
Astronomy (NOVA). H.B. acknowledges support from the European Research
Council under the Horizon 2020 Framework Program via the ERC Consolidator
Grant CSF-648505. H.B. also acknowledges support from the Deutsche
Forschungsgemeinschaft (DFG) via Sonderforschungsbereich (SFB) 881 “The
Milky Way System” (sub-project B1).


**References**


Arce, H. G., Santiago-García, J., Jørgensen, J. K., Tafalla, M., & Bachiller, R.
2008, ApJ, 681, L21


Article number, page 11 of 44

_A&A proofs:_ manuscript no. COM_paper



Artur de la Villarmois, E., Jørgensen, J. K., Kristensen, L. E., et al. 2019, A&A,
626, A71
Balucani, N., Ceccarelli, C., & Taquet, V. 2015, MNRAS, 449, L16
Bellet, J., Samson, C., Steenbeckliers, G., & Wertheimer, R. 1971, Journal of
Molecular Structure, 9, 49
Belloche, A., Maury, A. J., Maret, S., et al. 2020, A&A, 635, A198
Belloche, A., Müller, H. S. P., Garrod, R. T., & Menten, K. M. 2016, A&A, 587,
A91
Belloche, A., Müller, H. S. P., Menten, K. M., Schilke, P., & Comito, C. 2013,
A&A, 559, A47
Bergner, J. B., Martín-Doménech, R., Öberg, K. I., et al. 2019, ACS Earth and
Space Chemistry, 3, 1564
Bergner, J. B., Öberg, K. I., Garrod, R. T., & Graninger, D. M. 2017, ApJ, 841,
120
Bertin, M., Romanzin, C., Doronin, M., et al. 2016, ApJ, 817, L12
Bianchi, E., Codella, C., Ceccarelli, C., et al. 2017, A&A, 606, L7
Bisschop, S. E., Jørgensen, J. K., van Dishoeck, E. F., & de Wachter, E. B. M.
2007, A&A, 465, 913
Bøgelund, E. G., Barr, A. G., Taquet, V., et al. 2019, A&A, 628, A2
Bøgelund, E. G., McGuire, B. A., Ligterink, N. F. W., et al. 2018, A&A, 615,
A88
Boogert, A. C. A., Gerakines, P. A., & Whittet, D. C. B. 2015, ARA&A, 53, 541
Boogert, A. C. A., Pontoppidan, K. M., Knez, C., et al. 2008, ApJ, 678, 985
Bottinelli, S., Ceccarelli, C., Lefloch, B., et al. 2004, ApJ, 615, 354
Brown, R. D., Crofts, J. G., Gardner, F. F., et al. 1975, ApJ, 197, L29
Brown, R. D., Godfrey, P. D., McNaughton, D., Pierlot, A. P., & Taylor, W. H.
1990, Journal of Molecular Spectroscopy, 140, 340
Butler, R. A. H., De Lucia, F. C., Petkie, D. T., et al. 2001, ApJS, 134, 319
Calcutt, H., Jørgensen, J. K., Müller, H. S. P., et al. 2018, A&A, 616, A90
Caselli, P. & Ceccarelli, C. 2012, A&A Rev., 20, 56
Charnley, S. B., Tielens, A. G. G. M., & Millar, T. J. 1992, ApJ, 399, L71
Christen, D., Coudert, L. H., Larsson, J. A., & Cremer, D. 2001, Journal of
Molecular Spectroscopy, 205, 185
Christen, D., Coudert, L. H., Suenram, R. D., & Lovas, F. J. 1995, Journal of
Molecular Spectroscopy, 172, 57
Christen, D. & Müller, H. S. P. 2003, Physical Chemistry Chemical Physics (Incorporating Faraday Transactions), 5, 3600
Chuang, K. J., Fedoseev, G., Ioppolo, S., van Dishoeck, E. F., & Linnartz, H.
2016, MNRAS, 455, 1702
Chuang, K. J., Fedoseev, G., Qasim, D., et al. 2017, MNRAS, 467, 2552
Chuang, K. J., Fedoseev, G., Qasim, D., et al. 2018, ApJ, 853, 102
Coutens, A., Ligterink, N. F. W., Loison, J. C., et al. 2019, A&A, 623, L13
Crockett, N. R., Bergin, E. A., Neill, J. L., et al. 2014, ApJ, 787, 112
Drozdovskaya, M. N., Walsh, C., van Dishoeck, E. F., et al. 2016, MNRAS, 462,
977
El-Abd, S. J., Brogan, C. L., Hunter, T. R., et al. 2019, ApJ, 883, 129
Endres, C. P., Drouin, B. J., Pearson, J. C., et al. 2009, A&A, 504, 635
Endres, C. P., Schlemmer, S., Schilke, P., Stutzki, J., & Müller, H. S. P. 2016,
Journal of Molecular Spectroscopy, 327, 95
Enoch, M. L., Corder, S., Duchêne, G., et al. 2011, ApJS, 195, 21
Enoch, M. L., Evans, Neal J., I., Sargent, A. I., & Glenn, J. 2009, ApJ, 692, 973
Fabricant, B., Krieger, D., & Muenter, J. S. 1977, J. Chem. Phys., 67, 1576
Fayolle, E. C., Bertin, M., Romanzin, C., et al. 2011, ApJ, 739, L36
Fayolle, E. C., Bertin, M., Romanzin, C., et al. 2013, A&A, 556, A122
Fayolle, E. C., Öberg, K. I., Garrod, R. T., van Dishoeck, E. F., & Bisschop, S. E.
2015, A&A, 576, A45
Fayolle, E. C., Öberg, K. I., Jørgensen, J. K., et al. 2017, Nature Astronomy, 1,
703
Fedoseev, G., Chuang, K. J., Ioppolo, S., et al. 2017, ApJ, 842, 52
Fisher, J., Paciga, G., Xu, L.-H., et al. 2007, Journal of Molecular Spectroscopy,
245, 7
Fuchs, G. W., Cuppen, H. M., Ioppolo, S., et al. 2009, A&A, 505, 629
Garrod, R. T. 2013, ApJ, 765, 60
Garrod, R. T. & Herbst, E. 2006, A&A, 457, 927
Garrod, R. T., Widicus Weaver, S. L., & Herbst, E. 2008, ApJ, 682, 283
Gerakines, P. A., Schutte, W. A., & Ehrenfreund, P. 1996, A&A, 312, 289
Gerin, M., Pety, J., Commerçon, B., et al. 2017, A&A, 606, A35
Groner, P., Albert, S., Herbst, E., et al. 2002, ApJS, 142, 145
Harsono, D., Bjerkeli, P., van der Wiel, M. H. D., et al. 2018, Nature Astronomy,
2, 646
Hatchell, J., Fuller, G. A., & Richer, J. S. 2007, A&A, 472, 187
Herbst, E. & van Dishoeck, E. F. 2009, ARA&A, 47, 427
Hirano, N. & Liu, F.-c. 2014, ApJ, 789, 50
Hudson, R. L., Gerakines, P. A., & Ferrante, R. F. 2018, Spectrochimica Acta
Part A: Molecular Spectroscopy, 193, 33
Hull, C. L. H., Girart, J. M., Tychoniec, Ł., et al. 2017, ApJ, 847, 92
Ilyushin, V., Kryvda, A., & Alekseev, E. 2009, Journal of Molecular Spectroscopy, 255, 32
Isokoski, K., Bottinelli, S., & van Dishoeck, E. F. 2013, A&A, 554, A100
Jacobsen, S. K., Jørgensen, J. K., Di Francesco, J., et al. 2019, A&A, 629, A29


Article number, page 12 of 44



Johnson, H. R. & Strandberg, M. W. P. 1952, J. Chem. Phys., 20, 687
Jørgensen, J. K., Bourke, T. L., Myers, P. C., et al. 2005, ApJ, 632, 973
Jørgensen, J. K., Harvey, P. M., Evans, Neal J., I., et al. 2006, ApJ, 645, 1246
Jørgensen, J. K., Müller, H. S. P., Calcutt, H., et al. 2018, A&A, 620, A170
Jørgensen, J. K., Schöier, F. L., & van Dishoeck, E. F. 2002, A&A, 389, 908
Jørgensen, J. K., van der Wiel, M. H. D., Coutens, A., et al. 2016, A&A, 595,
A117
Karska, A., Kaufman, M. J., Kristensen, L. E., et al. 2018, ApJS, 235, 30
Kleiner, I., Lovas, F. J., & Godefroid, M. 1996, Journal of Physical and Chemical
Reference Data, 25, 1113
Kristensen, L. E., van Dishoeck, E. F., van Kempen, T. A., et al. 2010, A&A,
516, A57
Lauvergnat, D., Coudert, L. H., Klee, S., & Smirnov, M. 2009, Journal of Molecular Spectroscopy, 256, 204
Lee, C.-F., Codella, C., Li, Z.-Y., & Liu, S.-Y. 2019a, ApJ, 876, 63
Lee, J.-E., Lee, S., Baek, G., et al. 2019b, Nature Astronomy, 3, 314
Ligterink, N. F. W., Calcutt, H., Coutens, A., et al. 2018a, A&A, 619, A28
Ligterink, N. F. W., Terwisscha van Scheltinga, J., Taquet, V., et al. 2018b, MNRAS, 480, 3628
Ligterink, N. F. W., Walsh, C., Bhuin, R. G., et al. 2018c, A&A, 612, A88
Lykke, J. M., Coutens, A., Jørgensen, J. K., et al. 2017, A&A, 597, A53
Manara, C. F., Morbidelli, A., & Guillot, T. 2018, A&A, 618, L3
Manigand, S., Calcutt, H., Jørgensen, J. K., et al. 2019, A&A, 623, A69
Manigand, S., Jørgensen, J. K., Calcutt, H., et al. 2020, A&A, 635, A48
Marcelino, N., Gerin, M., Cernicharo, J., et al. 2018, A&A, 620, A80
McGuire, B. A. 2018, ApJS, 239, 17
Milam, S. N., Savage, C., Brewster, M. A., Ziurys, L. M., & Wyckoff, S. 2005,
ApJ, 634, 1126
Minissale, M., Dulieu, F., Cazaux, S., & Hocuk, S. 2016, A&A, 585, A24
Muñoz Caro, G. M., Chen, Y. J., Aparicio, S., et al. 2016, A&A, 589, A19
Müller, H. S. P., Belloche, A., Xu, L.-H., et al. 2016, A&A, 587, A92
Müller, H. S. P. & Christen, D. 2004, Journal of Molecular Spectroscopy, 228,
298
Müller, H. S. P., Schlöder, F., Stutzki, J., & Winnewisser, G. 2005, Journal of
Molecular Structure, 742, 215
Müller, H. S. P., Thorwirth, S., Roth, D. A., & Winnewisser, G. 2001, A&A, 370,
L49
Murillo, N. M., Lai, S.-P., Bruderer, S., Harsono, D., & van Dishoeck, E. F. 2013,
A&A, 560, A103
Murillo, N. M., van Dishoeck, E. F., van der Wiel, M. H. D., et al. 2018, A&A,
617, A120
Nagaoka, A., Watanabe, N., & Kouchi, A. 2005, ApJ, 624, L29
Neill, J. L., Bergin, E. A., Lis, D. C., et al. 2014, ApJ, 789, 8
Öberg, K. I. 2016, Chemical Reviews, 116, 9631
Öberg, K. I., Boogert, A. C. A., Pontoppidan, K. M., et al. 2011, ApJ, 740, 109
Öberg, K. I., Bottinelli, S., Jørgensen, J. K., & van Dishoeck, E. F. 2010, ApJ,
716, 825
Öberg, K. I., Garrod, R. T., van Dishoeck, E. F., & Linnartz, H. 2009, A&A, 504,
891
Ordu, M. H., Zingsheim, O., Belloche, A., et al. 2019, A&A, 629, A72
Ortiz-León, G. N., Dzib, S. A., Kounkel, M. A., et al. 2017, ApJ, 834, 143
Ortiz-León, G. N., Loinard, L., Dzib, S. A., et al. 2018, ApJ, 865, 73
Pagani, L., Favre, C., Goldsmith, P. F., et al. 2017, A&A, 604, A32
Pearson, J. C., Brauer, C. S., & Drouin, B. J. 2008, Journal of Molecular Spectroscopy, 251, 394
Pearson, J. C., Yu, S., & Drouin, B. J. 2012, Journal of Molecular Spectroscopy,
280, 119
Persson, M. V., Harsono, D., Tobin, J. J., et al. 2016, A&A, 590, A33
Pezzuto, S., Elia, D., Schisano, E., et al. 2012, A&A, 547, A54
Pickett, H. M., Poynter, R. L., Cohen, E. A., et al. 1998,
J. Quant. Spectr. Rad. Transf., 60, 883
Schutte, W. A., Boogert, A. C. A., Tielens, A. G. G. M., et al. 1999, A&A, 343,
966
Skouteris, D., Balucani, N., Ceccarelli, C., et al. 2018, ApJ, 854, 135
Taquet, V., Bianchi, E., Codella, C., et al. 2019, A&A, 632, A19
Taquet, V., Ceccarelli, C., & Kahane, C. 2012, A&A, 538, A42
Taquet, V., López-Sepulcre, A., Ceccarelli, C., et al. 2015, ApJ, 804, 81
Tercero, B., Cuadrado, S., López, A., et al. 2018, A&A, 620, L6
Terwisscha van Scheltinga, J., Ligterink, N. F. W., Boogert, A. C. A., van
Dishoeck, E. F., & Linnartz, H. 2018, A&A, 611, A35
Theulé, P., Duvernay, F., Danger, G., et al. 2013, Advances in Space Research,
52, 1567
Tobin, J. J., Hartmann, L., Chiang, H.-F., et al. 2012, Nature, 492, 83
Tobin, J. J., Looney, L. W., Li, Z.-Y., et al. 2016, ApJ, 818, 73
Tychoniec, Ł., Hull, C. L. H., Kristensen, L. E., et al. 2019, A&A, 632, A101
Tychoniec, Ł., Hull, C. L. H., Tobin, J. J., & van Dishoeck, E. F. 2018a, in IAU
Symposium, Vol. 332, IAU Symposium, ed. M. Cunningham, T. Millar, &
Y. Aikawa, 249–253
Tychoniec, Ł., Tobin, J. J., Karska, A., et al. 2018b, ApJS, 238, 19
van ’t Hoff, M. L. R., Tobin, J. J., Trapman, L., et al. 2018, ApJ, 864, L23
Visser, R., Doty, S. D., & van Dishoeck, E. F. 2011, A&A, 534, A132
Visser, R., van Dishoeck, E. F., Doty, S. D., & Dullemond, C. P. 2009, A&A,
495, 881
Watanabe, N. & Kouchi, A. 2002, ApJ, 571, L173
Wilson, T. L. & Rood, R. 1994, ARA&A, 32, 191
Xu, L.-H., Fisher, J., Lees, R. M., et al. 2008, Journal of Molecular Spectroscopy,
251, 305
Xu, L.-H. & Lovas, F. J. 1997, Journal of Physical and Chemical Reference Data,
26, 17
Young, C. H. & Evans, Neal J., I. 2005, ApJ, 627, 293

M. L. van Gelder et al.: Complex organic molecules in low-mass protostars on solar system scales



**Appendix A:** **Laboratory spectroscopic data**


All laboratory spectroscopic data are acquired using the CDMS
(Müller et al. 2001, 2005; Endres et al. 2016) and JPL (Pickett
et al. 1998) catalogs. In some of the entries, vibrational or torsional states are not taken into account in the calculation of the
partition function. At low temperatures, the contribution of these
states are negligible. At higher temperatures (i.e., _T_ - 100 _K_ ),
however, a so-called vibrational correction factor must be applied if the torsional and vibrational states are not accounted for
in the partition functions. Below, we detail the laboratory spectroscopy of each individual species discussed in this paper and
indicate if a vibrational correction factor was applied.
The data of CH 3 OH are taken from the CDMS database and
are based on the work of Xu et al. (2008). The ground state and
first three torsional states are taken into account in the partition
function. The entry of the [13] C isotopologue takes the first two
torsional states into account (Xu & Lovas 1997). They assumed
that the dipole moment is the same as the main isotopologue
and calculated the partition function taking only the permanent
dipole moment into account. The CH [18] 3 [OH entry is based mostly]
on the data of Fisher et al. (2007). The spectroscopic data of
CH 2 DOH are taken from the JPL catalog, where the entry is
based on the work of Pearson et al. (2012). The vibrational correction factor at 200 K is calculated to be 1.181 by summing
up over torsional substates extrapolated from Lauvergnat et al.
(2009)
CH 3 CH 2 OH exists as two conformers: _trans_ and _gauche_,
which originates from the torsion in the OH group. The spectroscopic data are taken from the CDMS catalog, where the entry
is based on Pearson et al. (2008) and updated by Müller et al.
(2016), who noticed that the old catalog entry did not predict the
line intensities correctly around 3 mm in Sagittarius B2. This
applies also to other frequency regions, but not to all transitions.
Both conformers are included in the entry.
The data of CH 3 CHO are taken from the JPL catalog. It is
based on laboratory spectroscopy of Kleiner et al. (1996) and includes the first and second torsional state in its partition function.
The spectroscopic data of CH 3 OCHO are taken from the JPL
database. The entry is based on the work of Ilyushin et al. (2009)
and Brown et al. (1975). The partition function includes states up
to the first torsional state.
CH 3 OCH 3 data are taken from the CDMS entry, which includes mostly the work of Endres et al. (2009). The partition
function includes the ground vibrational state and excited states
up to 500 cm [−][1] . However, for the excitation temperatures derived in this work (∼100 K), the contribution of higher order
vibrational states to the partition function is negligible.
The CH 3 COCH 3 data are taken form the JPL catalog. The
rotational transitions were calculated by Groner et al. (2002) and
include only the ground state. Here, we use an updated version
of the entry. It is based on the study of Ordu et al. (2019) with
the majority of the lines from Groner et al. (2002).
The (CH 2 OH) 2 structure consists of 3 coupled rotors,
which give rise to ten different stable configurations (Christen
et al. 2001). Here, only the two lowest energy conformers of
(CH 2 OH) 2 are studied. The aGg’ state is the lowest energy state
whereas the gGg’ state lies about 290 K above that (Müller
& Christen 2004). The spectroscopic data are taken from the
CDMS entries, which are based on the work of Christen et al.
(1995) and Christen & Müller (2003) for the aGg’ conformer
and Christen et al. (2001) and Müller & Christen (2004) for
the gGg’ conformer. For gGg’(CH 2 OH) 2, the partition function
and line intensities were calculated assuming as if it is the low


est energy state conformer. Since for these calculations only the
ground state is considered, we approximate the effect of vibrational states by using a vibrational correction factor of 2.143 for
both conformers at 200 K.
The CH 2 OHCHO data are taken from the CDMS catalog.
The entry is based on the work of Butler et al. (2001) and only
includes data on the ground vibrational state. A vibrational correction factor of 1.5901 is calculated at 200 K in the harmonic
approximation.
The spectroscopic data of H 2 CCO are acquired from the
CDMS catalog. The entry is calculated mostly by Johnson &
Strandberg (1952), Fabricant et al. (1977), and Brown et al.
(1990). The contribution of vibrational states is assumed to be
negligible.
Formic acid, HCOOH, exists both in a _trans_ and _cis_
state, where the lowest energy state of c-HCOOH is about
2000 K higher than for t-HCOOH. In this study we only detect t-HCOOH, for which we use the entry of the JPL catalog.
This is based on the work of Bellet et al. (1971). The vibrational
correction is < 1.1 at 200 K and is therefore neglected.


Article number, page 13 of 44

_A&A proofs:_ manuscript no. COM_paper


**Appendix B:** **CASSIS modeling results**


**Table B.1.** Computed Band 3 and Band 6 column densities and excitation temperatures of our sources.


**B1-c**

Band 3 Band 6
Species Catalog _T_ ex (K) _N_ _[1]_ (cm [−][2] ) X/CH 3 OH (%) _T_ ex (K) _N_ _[1]_ (cm [−][2] ) X/CH 3 OH (%)
CH 3 OH CDMS – (1.8 ± 0.4) × 10 [18] ≡ 100 – (1.9 ± 0.6) × 10 [18] ≡ 100
13 CH 3 OH CDMS [190] (2.6 ± 0.6) × 10 [16] ≡ 1.43 190 ± 30 (1.8 ± 0.2) × 10 [16] 1.0 ± 0.3
CH [18] 3 [OH] CDMS [140] < 1.8 × 10 [16] < 1.0 140 ± 60 (3.4 ± 1.1) × 10 [15] ≡ 0.18
CH 2 DOH JPL 210 ± 60 (1.0 ± 0.3) × 10 [17] 5.7 ± 2.1 180 ± 20 (1.6 ± 0.1) × 10 [17] 8.4 ± 2.8
CH 3 CH 2 OH CDMS 160 ± 60 (2.9 ± 1.5) × 10 [16] 1.6 ± 0.9 250 ± 60 (1.5 ± 0.3) × 10 [16] 0.8 ± 0.3
CH 3 CHO JPL 260 ± 50 (2.4 ± 0.8) × 10 [16] 1.3 ± 0.5 260 ± 60 (4.6 ± 1.0) × 10 [15] 0.24 ± 0.10
CH 3 OCHO JPL 120 ± 40 (2.0 ± 0.8) × 10 [16] 1.1 ± 0.5 180 ± 20 (1.9 ± 0.1) × 10 [16] 1.0 ± 0.3
CH 3 OCH 3 CDMS 100 ± 10 (1.9 ± 0.1) × 10 [16] 1.0 ± 0.2 120 ± 10 (2.4 ± 0.1) × 10 [16] 1.3 ± 0.4
CH 3 COCH 3 JPL [200] < 5.0 × 10 [16] < 2.8 [200] (8.0 ± 0.9) × 10 [15] 0.4 ± 0.1
aGg’(CH 2 OH) 2 CDMS [180] < 4.2 × 10 [16] < 2.4 180 ± 100 (4.8 ± 0.6) × 10 [15] 0.3 ± 0.1
gGg’(CH 2 OH) 2 CDMS [200] < 2.2 × 10 [16] < 1.2 [200] (6.8 ± 0.8) × 10 [15] 0.4 ± 0.1
CH 2 OHCHO CDMS [200] < 1.6 × 10 [16] < 0.89 [200] (2.0 ± 0.2) × 10 [15] 0.11 ± 0.04
H 2 CCO CDMS – – – [200] (1.3 ± 0.1) × 10 [15] 0.07 ± 0.02
t-HCOOH JPL [200] (9.0 ± 1.0) × 10 [15] 0.5 ± 0.1 [200] (7.0 ± 2.0) × 10 [14] 0.04 ± 0.02


**S68N**

CH 3 OH CDMS – (3.6 ± 0.8) × 10 [17] ≡ 100 – (1.4 ± 0.6) × 10 [18] ≡ 100
13 CH 3 OH CDMS [160] (5.1 ± 1.2) × 10 [15] ≡ 1.43 160 ± 20 (1.0 ± 0.1) × 10 [16] 0.7 ± 0.3
CH [18] 3 [OH] CDMS [200] < 1.0 × 10 [16] < 2.8 200 ± 80 (2.5 ± 1.1) × 10 [15] ≡ 0.18
CH 2 DOH JPL [200] < 4.7 × 10 [16] < 13 [200] (6.0 ± 0.7) × 10 [16] 4.3 ± 1.9
CH 3 CH 2 OH CDMS [200] < 2.0 × 10 [16] < 5.6 [200] (3.0 ± 0.2) × 10 [15] 0.22 ± 0.09
CH 3 CHO JPL [200] < 5.0 × 10 [15] < 1.4 [200] (1.0 ± 0.1) × 10 [15] 0.07 ± 0.03
CH 3 OCHO JPL 220 ± 80 (1.6 ± 0.9) × 10 [16] 3.9 ± 2.5 290 ± 30 (1.6 ± 0.2) × 10 [16] 1.1 ± 0.5
CH 3 OCH 3 CDMS 110 ± 10 (6.4 ± 0.7) × 10 [15] 1.8 ± 0.4 90 ± 10 (1.2 ± 0.1) × 10 [16] 0.9 ± 0.4
CH 3 COCH 3 JPL [200] < 5.0 × 10 [16] < 14 [200] (5.3 ± 0.3) × 10 [15] 0.4 ± 0.2
aGg’(CH 2 OH) 2 CDMS [200] < 4.2 × 10 [16] < 12 [200] (2.3 ± 0.1) × 10 [15] 0.16 ± 0.07
gGg’(CH 2 OH) 2 CDMS [200] < 2.2 × 10 [16] < 6 [200] < 1.1 × 10 [16] < 0.81
CH 2 OHCHO CDMS [200] < 8.0 × 10 [15] < 2.2 [200] < 8.0 × 10 [14] < 0.06
H 2 CCO CDMS – – – [200] (1.0 ± 0.1) × 10 [15] 0.07 ± 0.03
t-HCOOH JPL [200] < 5.0 × 10 [15] < 1.4 [200] (9.1 ± 2.1) × 10 [14] 0.07 ± 0.03


**B1-bS**


CH 3 OH CDMS – (2.4 ± 0.7) × 10 [17] ≡ 100 – (5.0 ± 0.6) × 10 [17] ≡ 100
13 CH 3 OH CDMS [160] (3.5 ± 1.0) × 10 [15] ≡ 1.43 160 ± 40 (1.5 ± 0.5) × 10 [15] 0.3 ± 0.1
CH [18] 3 [OH] CDMS [200] < 1.0 × 10 [16] < 4.2 [200] (9.0 ± 1.0) × 10 [14] ≡ 0.18
CH 2 DOH JPL [200] < 2.4 × 10 [16] < 9.9 [200] < 2.4 × 10 [16] < 4.7
CH 3 CH 2 OH CDMS [200] < 2.0 × 10 [16] < 8.3 [200] < 3.0 × 10 [15] < 0.6
CH 3 CHO JPL [200] < 5.0 × 10 [15] < 2.1 [200] (6.4 ± 0.7) × 10 [14] 0.13 ± 0.02
CH 3 OCHO JPL [200] (1.5 ± 0.1) × 10 [16] 6.1 ± 1.8 [200] (3.8 ± 0.2) × 10 [15] 0.75 ± 0.10
CH 3 OCH 3 CDMS 90 ± 10 (1.1 ± 0.1) × 10 [16] 4.3 ± 1.2 110 ± 10 (6.7 ± 0.4) × 10 [15] 1.3 ± 0.2
CH 3 COCH 3 JPL [200] < 5.0 × 10 [16] < 21 [200] (5.1 ± 1.2) × 10 [14] 0.10 ± 0.03
aGg’(CH 2 OH) 2 CDMS [200] < 4.2 × 10 [16] < 18 [200] < 2.2 × 10 [15] < 0.43
gGg’(CH 2 OH) 2 CDMS [200] < 2.2 × 10 [16] < 8.9 [200] < 2.2 × 10 [15] < 0.43
CH 2 OHCHO CDMS [200] < 8.0 × 10 [15] < 3.3 [200] < 3.2 × 10 [14] < 0.064
H 2 CCO CDMS – – – [200] (1.3 ± 0.3) × 10 [14] 0.03 ± 0.01
t-HCOOH JPL [200] < 1.0 × 10 [16] < 4.2 [200] < 5.0 × 10 [14] < 0.1


**Notes.** The column density of CH 3 OH is determined by scaling [13] CH 3 OH for Band 3 and CH [18] 3 [OH for Band 6 using] [12] [C][/] [13] [C][ =][ 70 and] [16] [O][/] [18] [O][ =]
560, respectively. A value between squared brackets means the parameter was fixed to that value during the computation. Abundance ratio’s which
are set to their respective isotope ratio are indicated with a ≡ symbol.
( _1_ ) The presented column densities are derived for a 0.45" source size. However, in reality the source sizes will be smaller, and the presented
column densities thus represent lower limits.


Article number, page 14 of 44

M. L. van Gelder et al.: Complex organic molecules in low-mass protostars on solar system scales



**Table B.2.** Number of transitions and lines fitted for all sources.


**B1-c**

Band 3 Band 6

Species T L F T L F
CH 3 OH 1 1 0 3 3 0
13 CH 3 OH 2 1 1 8 7 4
CH [18] 3 [OH] 4 0 0 20 16 8
CH 2 DOH 5 2 2 16 9 6
CH 3 CH 2 OH 12 3 3 30 14 8
CH 3 CHO 17 2 2 27 6 5
CH 3 OCHO 34 16 13 111 12 7
CH 3 OCH 3 16 8 8 112 27 20
CH 3 COCH 3 59 0 0 128 6 5
aGg’(CH 2 OH) 2 25 0 0 105 18 8
gGg’(CH 2 OH) 2 43 0 0 115 4 2
CH 2 OHCHO 15 0 0 27 5 3
H 2 CCO 0 0 0 6 2 2

t-HCOOH 6 3 3 3 1 1


**S68N**

Band 3 Band 6

Species T L F T L F
CH 3 OH 1 1 0 3 3 0
13 CH 3 OH 2 1 1 8 5 5
CH [18] 3 [OH] 4 0 0 20 2 2
CH 2 DOH 5 0 0 16 2 2
CH 3 CH 2 OH 12 0 0 30 3 2
CH 3 CHO 17 0 0 27 2 2
CH 3 OCHO 34 7 7 111 10 7
CH 3 OCH 3 16 8 8 112 27 20
CH 3 COCH 3 59 0 0 128 2 1
aGg’(CH 2 OH) 2 25 0 0 105 1 1
gGg’(CH 2 OH) 2 43 0 0 115 0 0
CH 2 OHCHO 15 0 0 27 0 0
H 2 CCO 0 0 0 6 2 1

t-HCOOH 6 0 0 3 1 1


**B1-bS**

Band 3 Band 6

Species T L F T L F
CH 3 OH 1 1 0 3 3 0
13 CH 3 OH 2 1 1 8 4 3
CH [18] 3 [OH] 4 0 0 20 13 5
CH 2 DOH 3 0 0 16 0 0
CH 3 CH 2 OH 12 0 0 30 0 0
CH 3 CHO 17 2 2 27 3 2
CH 3 OCHO 34 8 8 111 10 7
CH 3 OCH 3 16 6 6 112 63 60
CH 3 COCH 3 59 0 0 128 1 1
aGg’(CH 2 OH) 2 25 0 0 0 0 0
gGg’(CH 2 OH) 2 43 0 0 0 0 0
CH 2 OHCHO 15 0 0 0 0 0
H 2 CCO 0 0 0 6 1 1

t-HCOOH 6 0 0 3 0 0


**Notes.** T is the number of transitions, L is the number of lines in the
model with a 3σ detection, and F is the number of unblended lines (i.e.,
no other line within one FWHM) that are included in the fit.



**Table B.3.** Computed column densities and abundance ratios in Band 3,
assuming _T_ ex = 100 K.


**B1-c**


Band 3
Species _T_ ex (K) _N_ (cm [−][2] ) X/CH 3 OH (%)
CH 3 OH – (6.7 ± 1.1) × 10 [17] ≡ 100
13 CH 3 OH [100] (9.6 ± 1.6) × 10 [15] ≡ 1.43
CH [18] 3 [OH] [100] < 2.2 × 10 [16] < 3.4
CH 2 DOH [100] (5.7 ± 0.7) × 10 [16] 8.4 ± 1.7
CH 3 CH 2 OH [100] (1.8 ± 0.2) × 10 [16] 2.7 ± 0.5
CH 3 CHO [100] (4.7 ± 1.6) × 10 [15] 0.7 ± 0.3
CH 3 OCHO [100] (1.6 ± 0.2) × 10 [16] 2.4 ± 0.5
CH 3 OCH 3 [100] (1.9 ± 0.1) × 10 [16] 2.8 ± 0.5
CH 3 COCH 3 [100] < 5.0 × 10 [16] < 7.5
aGg’(CH 2 OH) 2 [100] < 2.1 × 10 [16] < 3.2
gGg’(CH 2 OH) 2 [100] < 2.1 × 10 [16] < 3.2
CH 2 OHCHO [100] < 8.0 × 10 [15] < 1.2
t-HCOOH [100] (4.3 ± 0.7) × 10 [15] 0.6 ± 0.2


**S68N**


Band 3
Species _T_ ex (K) _N_ (cm [−][2] ) X/CH 3 OH (%)
CH 3 OH – (2.1 ± 0.7) × 10 [17] ≡ 100
13 CH 3 OH [100] (3.0 ± 1.0) × 10 [15] ≡ 1.43
CH [18] 3 [OH] [100] < 2.0 × 10 [16] < 9.8
CH 2 DOH [100] < 1.0 × 10 [17] < 49
CH 3 CH 2 OH [100] < 2.0 × 10 [16] < 9.8
CH 3 CHO [100] < 2.9 × 10 [14] < 0.14
CH 3 OCHO [100] (4.7 ± 0.3) × 10 [15] 2.3 ± 0.8
CH 3 OCH 3 [100] (6.0 ± 0.3) × 10 [15] 2.9 ± 1.0
CH 3 COCH 3 [100] < 5.0 × 10 [16] < 25
aGg’(CH 2 OH) 2 [100] < 4.3 × 10 [16] < 21
gGg’(CH 2 OH) 2 [100] < 4.3 × 10 [16] < 21
CH 2 OHCHO [100] < 1.6 × 10 [16] < 7.8
t-HCOOH [100] < 5.0 × 10 [15] < 2.5


**B1-bS**


Band 3
Species _T_ ex (K) _N_ (cm [−][2] ) X/CH 3 OH (%)
CH 3 OH – (1.1 ± 0.3) × 10 [17] ≡ 100
13 CH 3 OH [100] (1.6 ± 0.4) × 10 [15] ≡ 1.43
CH [18] 3 [OH] [100] < 1.0 × 10 [16] < 8.9
CH 2 DOH [100] < 2.0 × 10 [16] < 18
CH 3 CH 2 OH [100] < 2.0 × 10 [16] < 18
CH 3 CHO [100] (1.4 ± 0.2) × 10 [15] 1.2 ± 0.3
CH 3 OCHO [100] (5.7 ± 0.7) × 10 [15] 5.0 ± 1.3
CH 3 OCH 3 [100] (1.2 ± 0.1) × 10 [16] 11 ± 3
CH 3 COCH 3 [100] < 1.0 × 10 [16] < 8.9
aGg’(CH 2 OH) 2 [100] < 1.1 × 10 [16] < 9.6
gGg’(CH 2 OH) 2 [100] < 2.1 × 10 [16] < 19
CH 2 OHCHO [100] < 8.0 × 10 [15] < 7.2
t-HCOOH [100] < 1.0 × 10 [16] < 8.9


**Notes.** The column density of CH 3 OH is determined by scaling
13 CH 3 OH using 12 C/ 13 C = 70. A value between squared brackets
means the parameter was fixed to that value during the computation.
Abundance ratio’s which are set to their respective isotope ratio are indicated with a ≡ symbol.


Article number, page 15 of 44

_A&A proofs:_ manuscript no. COM_paper


**Appendix C:** **Full ALMA Band 6 spectra**


B1-c                      - Band 6                      - spw1


8


6


4


2


0


260 _._ 00 260 _._ 05 260 _._ 10 260 _._ 15 260 _._ 20





260 _._ 25 260 _._ 30 260 _._ 35 260 _._ 40
Frequency (GHz)





8


6


4


2


0


261 _._ 75 261 _._ 80 261 _._ 85 261 _._ 90


8


6


4


2


0


261 _._ 95 262 _._ 00 262 _._ 05 262 _._ 10 262 _._ 15
Frequency (GHz)


**Fig. C.1.** Full Band 6 spectrum of B1-c (black) with best fitting CASSIS model overplotted (red). We indicate the positions of species, where lines
in italic are excluded in the fitting. Lines annotated with an ’X’ are unidentified.


Article number, page 16 of 44

M. L. van Gelder et al.: Complex organic molecules in low-mass protostars on solar system scales


B1-c                     - Band 6                     - spw3


8


6


4


2


0


262 _._ 75 262 _._ 80 262 _._ 85 262 _._ 90 262 _._ 95


8


6


4


2


0


263 _._ 00 263 _._ 05 263 _._ 10 263 _._ 15
Frequency (GHz)


B1-c                     - Band 6                     - spw4


8


6


4


2


0


263 _._ 30 263 _._ 35 263 _._ 40 263 _._ 45 263 _._ 50


8


6


4


2


0


263 _._ 55 263 _._ 60 263 _._ 65 263 _._ 70 263 _._ 75
Frequency (GHz)


**Fig. C.2.** (Continued)


Article number, page 17 of 44

5



_A&A proofs:_ manuscript no. COM_paper


S68N    - Band 6    - spw1



4


3


2


1


0


_−_ 1


5


4


3


2


1


0


_−_ 1


260 _._ 25 260 _._ 30 260 _._ 35 260 _._ 40
Frequency (GHz)



5





4


3


2


1


0


_−_ 1

261 _._ 75 261 _._ 80 261 _._ 85 261 _._ 90


5


4


3


2


1


0


_−_ 1


261 _._ 95 262 _._ 00 262 _._ 05 262 _._ 10 262 _._ 15
Frequency (GHz)


**Fig. C.3.** Same as Fig. C.1 but now for S68N.


Article number, page 18 of 44

5



M. L. van Gelder et al.: Complex organic molecules in low-mass protostars on solar system scales


S68N           - Band 6           - spw3



4


3


2


1


0


_−_ 1

262 _._ 75 262 _._ 80 262 _._ 85 262 _._ 90 262 _._ 95


5


4


3


2


1


0


_−_ 1


263 _._ 00 263 _._ 05 263 _._ 10 263 _._ 15
Frequency (GHz)



5



S68N - Band 6 - spw4



4


3


2


1


0


_−_ 1

263 _._ 35 263 _._ 40 263 _._ 45 263 _._ 50


5


4


3


2


1


0


_−_ 1


263 _._ 55 263 _._ 60 263 _._ 65 263 _._ 70 263 _._ 75
Frequency (GHz)


**Fig. C.4.** (Continued)


Article number, page 19 of 44

_A&A proofs:_ manuscript no. COM_paper


B1-bS    - Band 6    - spw1









5


4


3


2


1


0





B1-bS - Band 6 - spw2



_−_ 1


5


4


3


2


1


0


_−_ 1





**Fig. C.5.** Same as Fig. C.1 but now for B1-bS.


Article number, page 20 of 44

M. L. van Gelder et al.: Complex organic molecules in low-mass protostars on solar system scales


B1-bS            - Band 6            - spw3





_−_ 1

262 _._ 75 262 _._ 80 262 _._ 85 262 _._ 90 262 _._ 95


5


4


3


2


1


0


_−_ 1


263 _._ 00 263 _._ 05 263 _._ 10 263 _._ 15
Frequency (GHz)



5



B1-bS - Band 6 - spw4



4


3


2


1


0


_−_ 1

263 _._ 30 263 _._ 35 263 _._ 40 263 _._ 45 263 _._ 50


5


4


3


2


1


0


_−_ 1


Frequency (GHz)


**Fig. C.6.** (Continued)


Article number, page 21 of 44

**Appendix D:** **B1-c Band 3 spectrum**


1 _._ 00


0 _._ 75


0 _._ 50


0 _._ 25


0 _._ 00



_A&A proofs:_ manuscript no. COM_paper


B1-c     - Band 3     - spw1



109 _._ 55 109 _._ 56 109 _._ 57 109 _._ 58 109 _._ 59 109 _._ 60
Frequency (GHz)





1 _._ 00


0 _._ 75


0 _._ 50


0 _._ 25


0 _._ 00


109 _._ 73 109 _._ 74 109 _._ 75 109 _._ 76 109 _._ 77 109 _._ 78
Frequency (GHz)


B1-c                       - Band 3                       - spw3


109 _._ 88 109 _._ 89 109 _._ 90 109 _._ 91 109 _._ 92 109 _._ 93
Frequency (GHz)


B1-c                       - Band 3                       - spw4


1 _._ 00


0 _._ 75


0 _._ 50


0 _._ 25


0 _._ 00


110 _._ 35 110 _._ 36 110 _._ 37 110 _._ 38 110 _._ 39 110 _._ 40
Frequency (GHz)


**Fig. D.1.** Full Band 3 spectrum of B1-c (black) with best fitting CASSIS model overplotted (red). We indicate the positions of species, where lines
in italic are excluded in the fitting.


Article number, page 22 of 44

M. L. van Gelder et al.: Complex organic molecules in low-mass protostars on solar system scales


B1-c                     - Band 3                     - spw5


1 _._ 00


0 _._ 75


0 _._ 50


0 _._ 25


0 _._ 00


110 _._ 76 110 _._ 77 110 _._ 78 110 _._ 79 110 _._ 80 110 _._ 81
Frequency (GHz)


B1-c                     - Band 3                     - spw6


110 _._ 86 110 _._ 87 110 _._ 88 110 _._ 89 110 _._ 90 110 _._ 91
Frequency (GHz)


B1-c                     - Band 3                     - spw7


1 _._ 00


0 _._ 75


0 _._ 50


0 _._ 25


0 _._ 00


111 _._ 15 111 _._ 16 111 _._ 17 111 _._ 18 111 _._ 19
Frequency (GHz)


B1-c                     - Band 3                     - spw8


111 _._ 65 111 _._ 66 111 _._ 67 111 _._ 68 111 _._ 69 111 _._ 70
Frequency (GHz)


**Fig. D.2.** (Continued)


Article number, page 23 of 44

_A&A proofs:_ manuscript no. COM_paper


B1-c                     - Band 3                     - spw9


1 _._ 00


0 _._ 75


0 _._ 50


0 _._ 25


0 _._ 00


111 _._ 74 111 _._ 75 111 _._ 76 111 _._ 77 111 _._ 78 111 _._ 79
Frequency (GHz)


B1-c                     - Band 3                     - spw10


112 _._ 12 112 _._ 13 112 _._ 14 112 _._ 15 112 _._ 16 112 _._ 17
Frequency (GHz)


B1-c                     - Band 3                     - spw11


112 _._ 23 112 _._ 24 112 _._ 25 112 _._ 26 112 _._ 27
Frequency (GHz)


B1-c                     - Band 3                     - spw12


1 _._ 00


0 _._ 75


0 _._ 50


0 _._ 25


0 _._ 00


112 _._ 26 112 _._ 27 112 _._ 28 112 _._ 29 112 _._ 30 112 _._ 31
Frequency (GHz)


**Fig. D.3.** (Continued)


Article number, page 24 of 44

1 _._ 00


0 _._ 75


0 _._ 50


0 _._ 25


0 _._ 00


1 _._ 00


0 _._ 75


0 _._ 50


0 _._ 25


0 _._ 00


1 _._ 00


0 _._ 75


0 _._ 50


0 _._ 25


0 _._ 00



M. L. van Gelder et al.: Complex organic molecules in low-mass protostars on solar system scales


B1-c               - Band 3               - spw13


112 _._ 40 112 _._ 42 112 _._ 44 112 _._ 46 112 _._ 48 112 _._ 50
Frequency (GHz)


B1-c               - Band 3               - spw14


112 _._ 76 112 _._ 78 112 _._ 80 112 _._ 82 112 _._ 84 112 _._ 86
Frequency (GHz)


B1-c               - Band 3               - spw15



Frequency (GHz)


B1-c                  - Band 3                  - spw16



1 _._ 00


0 _._ 75


0 _._ 50


0 _._ 25


0 _._ 00


**Fig. D.4.** (Continued)



Frequency (GHz)


Article number, page 25 of 44

_A&A proofs:_ manuscript no. COM_paper


**Appendix E:** **Additional tables**


**Table E.1.** List of ALMA image properties from program 2017.1.01774.S.


B1-b _[1]_ B1-c S68N _[2]_ SMM3

Band 3 Band 6 Band 3 Band 6 Band 3 Band 6 Band 3 Band 6

Configuration C43-3 C43-4 C43-3 C43-4 C43-2 C43-4 C43-2 –
Beam (") 2.1×1.4 0.58×0.39 2.1×1.4 0.58×0.39 2.8×1.8 0.46×0.42 2.8×1.8 –
LAS (") 16 6 16 6 22 6 22 –
∆V (km s [−][1] ) 0.2 / 0.4 0.14 0.2 / 0.4 0.14 0.17 / 0.32 0.14 0.17 / 0.32 –
Continuum rms (mJy) 8.5 5.4 14.4 24.4 14.6 9.2 5.1 –
Line rms (K) 0.05 0.16 0.06 0.14 0.04 0.15 0.06 –
Flux uncertainty (%) 3 12 3 12 5 9 5 –


**Notes.** [(] _[1]_ [)] Including B1-bN and B1-bS. [(] _[2]_ [)] Including Ser-emb 8 (N).


Article number, page 26 of 44

M. L. van Gelder et al.: Complex organic molecules in low-mass protostars on solar system scales


**Table E.2.** Lines per species used for fitting the Band 3 data.


Species Transition Frequency _A_ _i j_ _E_ up
(J K L M                    - J K L M) (GHz) (s [−][1] ) (K)
13 CH 3 OH 3 1 3 +0               - 4 0 4 +0 112.1435 7.1 × 10 [−][6] 28.0
17 -2 16 0                      - 17 1 16 0 112.3157 2.1 × 10 [−][6] 373.0
CH [18] 3 [OH] 21 3 18 4        - 20 2 18 4 110.9133 5.0 × 10 [−][6] 834.9
18 1 17 4                      - 19 2 17 4 111.6514 1.1 × 10 [−][6] 790.6
13 3 11 1                      - 14 2 13 1 112.3039 2.6 × 10 [−][6] 265.0
25 0 25 1                      - 25 1 25 1 113.0484 1.2 × 10 [−][6] 730.9
CH 2 DOH 28 0 28 2        - 28 1 28 1 109.7332 5.3 × 10 [−][6] 878.3
12 1 11 1                      - 12 0 12 1 113.0450 2.5 × 10 [−][6] 185.1
10 1 9 2                       - 10 0 10 2 113.1846 6.2 × 10 [−][6] 141.6
CH 3 CH 2 OH 20 3 17 0        - 19 4 15 1 109.7409 1.5 × 10 [−][6] 245.0
8 1 8 1                         - 8 0 8 0 110.3685 9.5 × 10 [−][6] 91.7
28 9 19 1                      - 27 10 17 0 110.7978 1.0 × 10 [−][6] 498.5
28 9 20 1                      - 27 10 18 0 110.7978 1.0 × 10 [−][6] 498.5
12 3 9 2                       - 12 2 10 2 112.1295 8.4 × 10 [−][6] 77.1
9 1 8 0                         - 8 0 8 1 112.2692 5.2 × 10 [−][6] 96.5
11 3 9 1                       - 10 4 7 0 112.7463 1.1 × 10 [−][6] 127.5
2 2 1 2                         - 1 1 0 2 112.8072 1.1 × 10 [−][5] 7.5
45 5 41 1                      - 45 4 41 0 112.8196 5.0 × 10 [−][6] 954.0
28 5 24 0                      - 27 6 22 1 113.0453 1.6 × 10 [−][6] 426.0
10 2 9 2                       - 10 1 10 2 113.0981 8.8 × 10 [−][6] 51.0
31 1 31 0                      - 30 2 29 1 113.1338 2.3 × 10 [−][6] 449.9
CH 3 CHO 17 4 13 6        - 18 3 16 6 109.5448 1.5 × 10 [−][6] 570.8
20 6 14 2                      - 21 5 16 2 109.7350 1.2 × 10 [−][6] 275.5
34 9 25 3                      - 35 8 28 3 109.7646 1.2 × 10 [−][6] 937.4
34 9 26 3                      - 35 8 27 3 109.7657 1.2 × 10 [−][6] 937.4
23 3 21 1                      - 22 4 18 2 110.9036 1.3 × 10 [−][6] 275.9
13 1 12 0                      - 13 0 13 0 111.1978 5.0 × 10 [−][6] 88.4
15 1 15 7                      - 14 1 13 8 111.7924 2.2 × 10 [−][6] 489.6
18 2 16 8                      - 18 2 17 7 112.1263 2.4 × 10 [−][6] 555.7
6 1 6 0                         - 5 1 5 0 112.2487 4.5 × 10 [−][5] 21.1
6 1 6 1                         - 5 1 5 1 112.2545 4.5 × 10 [−][5] 21.2
6 1 5 6                         - 6 0 6 6 112.3004 9.9 × 10 [−][6] 392.2
6 1 6 3                         - 5 1 5 3 112.3908 4.6 × 10 [−][5] 227.6
14 5 10 4                      - 15 4 11 5 112.3939 1.1 × 10 [−][6] 358.6
15 5 11 0                      - 16 4 12 0 112.4634 1.2 × 10 [−][6] 167.5
27 3 24 8                      - 27 3 25 7 112.8593 1.7 × 10 [−][6] 755.2
6 1 6 6                         - 5 1 5 6 113.0365 4.4 × 10 [−][5] 391.0
15 5 10 2                      - 16 4 13 1 113.1407 1.2 × 10 [−][6] 167.4
CH 3 OCHO 10 0 10 5        - 9 1 9 4 109.6030 2.7 × 10 [−][6] 217.2
9 6 3 3                         - 8 6 2 3 109.6085 1.1 × 10 [−][5] 238.2
9 6 4 3                         - 8 6 3 3 109.6085 1.1 × 10 [−][5] 238.2
9 3 7 3                         - 8 3 6 3 109.7637 1.7 × 10 [−][5] 220.2
9 5 5 3                         - 8 5 4 3 109.7710 1.3 × 10 [−][5] 230.8
9 5 4 3                         - 8 5 3 3 109.7788 1.3 × 10 [−][5] 230.8
15 4 12 3                      - 15 3 13 3 109.9070 1.9 × 10 [−][6] 269.0
28 6 22 5                      - 28 5 23 5 109.9082 2.7 × 10 [−][6] 455.2
9 5 4 5                         - 8 5 3 5 109.9122 1.3 × 10 [−][5] 230.6
9 7 3 4                         - 8 7 2 4 109.9248 7.7 × 10 [−][6] 246.1
9 4 5 5                         - 8 4 4 5 110.3645 1.6 × 10 [−][5] 224.6
9 1 8 3                         - 8 1 7 3 110.7765 1.9 × 10 [−][5] 215.7
10 1 10 1                      - 9 1 9 1 110.7887 2.0 × 10 [−][5] 30.3
10 1 10 0                      - 9 1 9 0 110.7905 2.0 × 10 [−][5] 30.3
15 4 12 4                      - 15 3 13 4 110.8612 1.8 × 10 [−][6] 268.6
9 5 4 2                         - 8 5 3 2 110.8740 1.4 × 10 [−][5] 43.2
9 3 7 1                         - 8 3 6 1 110.8798 1.8 × 10 [−][5] 32.6
9 5 5 0                         - 8 5 4 0 110.8804 1.4 × 10 [−][5] 43.2


Article number, page 27 of 44

**Table E.2.** continued.



_A&A proofs:_ manuscript no. COM_paper


Species Transition Frequency _A_ _i j_ _E_ up
(J K L M          - J K L M) (GHz) (s [−][1] ) (K)
9 5 5 1            - 8 5 4 1 110.8823 1.4 × 10 [−][5] 43.2
9 3 7 0            - 8 3 6 0 110.8871 1.8 × 10 [−][5] 32.6
9 5 4 0            - 8 5 3 0 110.8903 1.4 × 10 [−][5] 43.2
10 0 10 2          - 9 0 9 2 111.1699 2.0 × 10 [−][5] 30.2
10 0 10 0          - 9 0 9 0 111.1716 2.0 × 10 [−][5] 30.2
9 4 6 0            - 8 4 5 0 111.1960 1.6 × 10 [−][5] 37.2
9 1 8 2            - 8 1 7 2 111.6741 2.0 × 10 [−][5] 28.1
9 1 8 0            - 8 1 7 0 111.6822 2.0 × 10 [−][5] 28.1
23 6 17 3          - 23 5 18 3 111.7071 2.6 × 10 [−][6] 375.2
10 1 10 1          - 9 0 9 2 111.7340 3.0 × 10 [−][6] 30.3
10 1 10 0          - 9 0 9 0 111.7353 3.0 × 10 [−][6] 30.3
28 6 22 0          - 28 5 23 0 111.7501 2.8 × 10 [−][6] 269.8
25 5 20 2          - 25 4 21 2 112.2567 2.5 × 10 [−][6] 214.4
9 3 6 3            - 8 3 5 3 112.3069 1.8 × 10 [−][5] 220.5
25 5 20 0          - 25 4 21 0 112.3109 2.5 × 10 [−][6] 214.4
16 2 14 3          - 16 1 15 3 113.1815 1.5 × 10 [−][6] 272.4
CH 3 OCH 3 8 2 7 3 - 8 1 8 3 109.5714 5.4 × 10 [−][6] 38.3
8 2 7 5            - 8 1 8 5 109.5714 5.4 × 10 [−][6] 38.3
8 2 7 1            - 8 1 8 1 109.5741 5.4 × 10 [−][6] 38.3
8 2 7 0            - 8 1 8 0 109.5769 5.4 × 10 [−][6] 38.3
19 3 16 3          - 19 2 17 3 111.7416 1.1 × 10 [−][5] 187.5
19 3 16 5          - 19 2 17 5 111.7416 1.1 × 10 [−][5] 187.5
19 3 16 1          - 19 2 17 1 111.7430 1.1 × 10 [−][5] 187.5
19 3 16 0          - 19 2 17 0 111.7444 1.1 × 10 [−][5] 187.5
7 0 7 0            - 6 1 6 0 111.7826 7.4 × 10 [−][6] 25.2
7 0 7 1            - 6 1 6 1 111.7831 7.4 × 10 [−][6] 25.2
7 0 7 5            - 6 1 6 5 111.7836 7.4 × 10 [−][6] 25.3
7 0 7 3            - 6 1 6 3 111.7836 7.4 × 10 [−][6] 25.3
17 3 14 5          - 17 2 15 5 113.0576 1.1 × 10 [−][5] 153.1
17 3 14 3          - 17 2 15 3 113.0576 1.1 × 10 [−][5] 153.1
17 3 14 1          - 17 2 15 1 113.0594 1.1 × 10 [−][5] 153.1
17 3 14 0          - 17 2 15 0 113.0611 1.1 × 10 [−][5] 153.1
CH 3 COCH 3 32 23 10 1 - 32 22 11 1 109.6011 3.5 × 10 [−][5] 444.0
32 23 10 1          - 32 22 11 2 109.6030 3.4 × 10 [−][5] 444.0
9 6 3 1            - 8 7 2 2 109.9047 1.4 × 10 [−][6] 37.3
26 21 6 0          - 26 20 7 1 110.3754 2.6 × 10 [−][5] 306.6
29 22 7 0          - 29 21 8 1 110.3788 2.8 × 10 [−][5] 371.8
29 22 7 0          - 29 21 8 0 110.3828 3.1 × 10 [−][5] 371.8
26 21 5 0          - 26 20 6 1 110.3933 2.6 × 10 [−][5] 306.6
6 5 2 0            - 5 4 1 0 110.4013 3.4 × 10 [−][5] 18.2
8 4 5 0            - 7 3 4 1 110.4094 3.1 × 10 [−][5] 26.8
22 20 3 0          - 22 19 4 1 110.7627 1.6 × 10 [−][5] 232.1
42 25 17 0          - 42 24 18 1 110.7636 5.9 × 10 [−][5] 732.4
47 31 16 1          - 47 30 17 1 110.7727 4.4 × 10 [−][5] 928.6
38 25 14 0          - 38 24 15 1 110.8606 5.2 × 10 [−][5] 609.5
8 4 4 0            - 7 5 3 0 110.9171 1.6 × 10 [−][5] 28.4
8 4 4 1            - 7 5 3 2 111.1413 1.6 × 10 [−][5] 28.6
37 25 13 0          - 37 24 14 1 111.6404 4.9 × 10 [−][5] 581.8
37 25 13 1          - 37 24 14 2 111.6834 4.1 × 10 [−][5] 581.7
14 10 4 0          - 14 7 7 1 111.6931 1.8 × 10 [−][6] 88.0
24 11 13 1          - 24 10 14 1 111.7369 3.2 × 10 [−][5] 230.4
24 11 13 1          - 24 10 14 2 111.7372 3.2 × 10 [−][5] 230.4
14 10 4 0          - 14 7 7 0 111.7505 1.9 × 10 [−][6] 87.9
24 12 13 1          - 24 11 14 1 111.7591 3.2 × 10 [−][5] 230.4
24 12 13 1          - 24 11 14 2 111.7593 3.2 × 10 [−][5] 230.4
24 11 13 0          - 24 10 14 1 111.7973 3.2 × 10 [−][5] 230.4



Article number, page 28 of 44

**Table E.2.** continued.



M. L. van Gelder et al.: Complex organic molecules in low-mass protostars on solar system scales


Species Transition Frequency _A_ _i j_ _E_ up
(J K L M           - J K L M) (GHz) (s [−][1] ) (K)
37 25 13 1           - 37 24 14 1 111.7996 4.2 × 10 [−][5] 581.7
34 24 11 0           - 34 23 12 1 112.1478 4.1 × 10 [−][5] 497.9
31 18 14 0           - 31 17 15 0 112.1507 3.9 × 10 [−][5] 396.7
34 24 11 0           - 34 23 12 0 112.1546 3.9 × 10 [−][5] 497.9
31 18 14 0           - 31 17 15 1 112.1592 4.0 × 10 [−][5] 396.6
31 18 14 1           - 31 17 15 2 112.1677 3.9 × 10 [−][5] 396.6
31 18 14 1           - 31 17 15 1 112.1684 3.9 × 10 [−][5] 396.6
45 27 18 1           - 45 26 19 1 112.1796 4.6 × 10 [−][5] 840.2
21 20 1 0            - 21 19 2 1 112.2312 1.1 × 10 [−][5] 216.8
21 20 2 0            - 21 19 3 1 112.3046 1.2 × 10 [−][5] 216.7
45 30 15 0           - 45 29 16 0 112.4518 4.5 × 10 [−][5] 854.0
6 5 1 1              - 5 4 1 2 112.4951 1.4 × 10 [−][5] 18.5
38 24 15 0           - 38 23 16 0 112.5018 4.4 × 10 [−][5] 604.2
23 10 13 1           - 23 9 14 1 112.7549 3.1 × 10 [−][5] 209.3
23 10 13 1           - 23 9 14 2 112.7551 3.1 × 10 [−][5] 209.3
23 11 13 1           - 23 10 14 1 112.7621 3.1 × 10 [−][5] 209.3
23 11 13 1           - 23 10 14 2 112.7622 3.1 × 10 [−][5] 209.3
25 21 4 0            - 25 20 5 1 112.8283 2.4 × 10 [−][5] 288.2
23 10 13 0           - 23 9 14 1 112.8310 3.2 × 10 [−][5] 209.3
31 23 8 1            - 31 22 9 2 112.8320 2.7 × 10 [−][5] 421.0
23 11 13 0           - 23 10 14 1 112.8382 3.2 × 10 [−][5] 209.3
25 21 5 0            - 25 20 6 1 112.8397 2.4 × 10 [−][5] 288.2
31 23 8 0            - 31 22 9 1 112.8422 2.7 × 10 [−][5] 421.0
45 27 18 0           - 45 26 19 0 112.8627 4.7 × 10 [−][5] 840.3
31 23 8 0            - 31 22 9 0 112.8694 3.5 × 10 [−][5] 421.1
37 23 15 0           - 37 22 16 1 113.0468 5.3 × 10 [−][5] 571.2
25 21 4 0            - 25 20 5 0 113.0648 2.4 × 10 [−][5] 288.3
25 21 5 0            - 25 20 6 0 113.0707 2.4 × 10 [−][5] 288.3
39 25 15 0           - 39 24 16 0 113.0911 4.5 × 10 [−][5] 638.0
37 23 15 1           - 37 22 16 2 113.1143 4.4 × 10 [−][5] 571.2
37 23 15 1           - 37 22 16 1 113.1226 4.4 × 10 [−][5] 571.2
20 20 0 1            - 20 19 1 2 113.1584 6.2 × 10 [−][6] 202.2
45 30 15 0           - 45 29 16 1 113.2046 6.6 × 10 [−][5] 854.0
10 7 3 0             - 9 8 1 1 113.2057 1.2 × 10 [−][6] 45.9
31 23 9 1            - 31 22 10 2 113.2179 2.7 × 10 [−][5] 421.0
aGg’(CH 2 OH) 2 18 6 13 0  - 18 5 14 0 109.5468 3.6 × 10 [−][6] 102.0
45 9 36 1            - 45 8 37 1 109.7212 5.9 × 10 [−][6] 555.5
25 7 19 1            - 24 8 16 1 109.7295 1.0 × 10 [−][6] 184.8
27 7 20 1            - 27 6 21 1 109.7364 4.3 × 10 [−][6] 211.3
23 6 18 1            - 22 7 15 1 109.7545 1.2 × 10 [−][6] 154.4
10 1 9 1             - 9 1 8 0 109.7605 2.4 × 10 [−][5] 28.5
16 6 11 0            - 16 5 12 0 110.4055 3.5 × 10 [−][6] 84.7
15 6 10 1            - 15 5 11 1 110.8540 3.8 × 10 [−][6] 77.1
23 4 20 1            - 23 3 21 1 111.6959 2.7 × 10 [−][6] 144.1
11 6 5 1             - 11 5 6 1 112.1232 3.4 × 10 [−][6] 50.5
11 6 6 0             - 11 5 7 0 112.1340 3.1 × 10 [−][6] 50.1
11 6 6 1             - 11 5 7 1 112.1506 3.4 × 10 [−][6] 50.5
46 9 37 0            - 46 8 38 0 112.2790 6.0 × 10 [−][6] 578.7
10 6 4 0             - 10 5 5 0 112.3116 2.9 × 10 [−][6] 44.7
9 6 3 0              - 9 5 4 0 112.4602 2.7 × 10 [−][6] 39.8
9 6 4 0              - 9 5 5 0 112.4637 2.7 × 10 [−][6] 39.8
9 6 3 1              - 9 5 4 1 112.4783 2.9 × 10 [−][6] 40.1
9 6 4 1              - 9 5 5 1 112.4818 2.9 × 10 [−][6] 40.1
25 6 20 0            - 25 5 21 0 112.8157 4.5 × 10 [−][6] 178.4
10 2 9 1             - 9 1 8 1 112.8355 1.2 × 10 [−][6] 29.0
10 2 9 0             - 9 1 8 0 113.0314 1.1 × 10 [−][5] 28.7


Article number, page 29 of 44

**Table E.2.** continued.



_A&A proofs:_ manuscript no. COM_paper


Species Transition Frequency _A_ _i j_ _E_ up
(J K L M          - J K L M) (GHz) (s [−][1] ) (K)
27 7 21 1          - 27 6 21 0 113.0501 2.6 × 10 [−][6] 211.2
19 1 18 1          - 19 0 19 1 113.1029 1.3 × 10 [−][6] 92.8
42 9 33 1          - 42 8 34 1 113.1433 6.0 × 10 [−][6] 488.4
19 1 18 0          - 19 0 19 0 113.1609 1.3 × 10 [−][6] 92.4
gGg’(CH 2 OH) 2 46 9 37 0 - 46 8 38 0 109.5531 1.1 × 10 [−][5] 574.1
39 7 32 1          - 39 6 33 1 109.5776 9.8 × 10 [−][6] 412.0
46 9 37 1          - 46 8 38 1 109.6094 1.1 × 10 [−][5] 574.1
35 8 27 0          - 35 7 28 0 109.7473 9.8 × 10 [−][6] 341.1
24 6 19 0          - 24 5 20 0 109.7560 8.3 × 10 [−][6] 164.8
24 6 19 1          - 24 5 20 1 109.7601 8.0 × 10 [−][6] 164.8
27 8 20 1          - 26 9 18 0 109.8720 1.9 × 10 [−][6] 216.3
27 7 20 0          - 27 6 21 0 109.8996 8.2 × 10 [−][6] 209.4
15 6 10 1          - 15 5 10 0 110.3408 7.0 × 10 [−][6] 76.2
13 6 8 1           - 13 5 9 1 110.3980 6.9 × 10 [−][6] 62.0
25 7 18 1          - 24 8 17 1 110.4062 2.0 × 10 [−][6] 183.2
19 2 18 1          - 19 1 19 1 110.7957 2.4 × 10 [−][6] 92.0
19 2 18 0          - 19 1 19 0 110.7993 2.6 × 10 [−][6] 91.9
11 6 5 1           - 11 5 6 1 110.8835 6.5 × 10 [−][6] 49.8
11 6 5 0           - 11 5 6 0 110.8971 6.4 × 10 [−][6] 49.7
11 5 7 0           - 10 5 6 1 110.9012 9.7 × 10 [−][6] 44.4
11 6 6 1           - 11 5 7 1 110.9086 6.5 × 10 [−][6] 49.8
15 6 9 1           - 15 5 11 0 110.9138 5.7 × 10 [−][6] 76.2
11 5 6 0           - 10 5 5 1 110.9170 9.7 × 10 [−][6] 44.4
6 3 3 1            - 5 2 3 0 111.7594 6.9 × 10 [−][6] 14.7
11 6 6 1           - 11 5 6 0 112.1434 5.8 × 10 [−][6] 49.8
12 0 12 0          - 11 0 11 1 112.1530 9.4 × 10 [−][6] 36.1
40 9 32 0          - 40 8 32 1 112.1613 5.8 × 10 [−][6] 442.2
11 6 5 1           - 11 5 7 0 112.1696 5.8 × 10 [−][6] 49.8
20 4 17 1          - 19 5 15 0 112.2534 2.4 × 10 [−][6] 110.7
7 2 6 1            - 6 1 6 0 112.4572 5.4 × 10 [−][6] 15.6
9 6 4 1            - 9 5 4 0 112.5023 5.2 × 10 [−][6] 39.5
9 6 3 1            - 9 5 5 0 112.5055 5.2 × 10 [−][6] 39.5
6 6 1 1            - 6 5 1 0 112.7433 2.3 × 10 [−][6] 27.8
6 6 0 1            - 6 5 2 0 112.7434 2.3 × 10 [−][6] 27.8
18 4 14 1          - 17 5 13 1 112.7800 1.5 × 10 [−][6] 92.6
8 1 7 1            - 7 0 7 0 112.8301 5.7 × 10 [−][6] 18.7
11 8 3 1           - 10 8 2 0 113.0460 6.1 × 10 [−][6] 63.4
11 8 4 1           - 10 8 3 0 113.0460 6.1 × 10 [−][6] 63.4
23 6 17 0          - 22 7 16 0 113.0973 2.4 × 10 [−][6] 153.1
12 0 12 1          - 11 1 11 1 113.1070 9.2 × 10 [−][6] 36.2
23 6 17 1          - 22 7 16 1 113.1093 2.4 × 10 [−][6] 153.1
12 0 12 0          - 11 1 11 0 113.1156 1.6 × 10 [−][5] 36.1
11 7 4 1           - 10 7 3 0 113.1237 7.7 × 10 [−][6] 56.1
11 7 5 1           - 10 7 4 0 113.1237 7.7 × 10 [−][6] 56.1
26 6 21 0          - 26 5 22 0 113.1609 9.0 × 10 [−][6] 189.9
26 6 21 1          - 26 5 22 1 113.1851 8.9 × 10 [−][6] 190.0
47 9 38 0          - 47 8 39 0 113.2009 1.2 × 10 [−][5] 597.8
CH 2 OHCHO 4 3 1 - 3 2 2 109.8771 2.3 × 10 [−][5] 11.0
15 3 13           - 15 2 14 110.4025 1.6 × 10 [−][5] 71.8
45 26 19          - 46 25 22 110.4059 2.2 × 10 [−][6] 984.4
45 26 20          - 46 25 21 110.4059 2.2 × 10 [−][6] 984.4
49 18 32          - 48 19 29 111.6495 4.3 × 10 [−][6] 878.4
49 18 31          - 48 19 30 111.6495 4.3 × 10 [−][6] 878.4
10 5 5            - 10 4 6 111.7349 2.0 × 10 [−][5] 45.8
34 21 13          - 35 20 16 112.1106 2.0 × 10 [−][6] 597.9
34 21 14          - 35 20 15 112.1106 2.0 × 10 [−][6] 597.9



Article number, page 30 of 44

**Table E.2.** continued.



M. L. van Gelder et al.: Complex organic molecules in low-mass protostars on solar system scales


Species Transition Frequency _A_ _i j_ _E_ up
(J K L M           - J K L M) (GHz) (s [−][1] ) (K)
13 5 9             - 13 4 10 112.1777 2.3 × 10 [−][5] 65.9
20 6 14            - 20 5 15 112.2480 2.8 × 10 [−][5] 139.6
11 5 7             - 11 4 8 112.4443 2.2 × 10 [−][5] 51.9
14 5 10            - 14 4 11 112.4728 2.4 × 10 [−][5] 73.8
10 5 6             - 10 4 7 112.7734 2.1 × 10 [−][5] 45.8
9 5 5              - 9 4 6 113.1188 2.0 × 10 [−][5] 40.2

t-HCOOH 5 0 5  - 4 0 4 111.7468 1.4 × 10 [−][5] 16.1
5 2 4              - 4 2 3 112.2871 1.2 × 10 [−][5] 28.9
5 4 2              - 4 4 1 112.4323 5.3 × 10 [−][6] 67.1
5 4 1              - 4 4 0 112.4323 5.3 × 10 [−][6] 67.1
5 3 3              - 4 3 2 112.4596 9.4 × 10 [−][6] 44.8
5 3 2              - 4 3 1 112.4670 9.4 × 10 [−][6] 44.8


Article number, page 31 of 44

_A&A proofs:_ manuscript no. COM_paper


**Table E.3.** Lines per species used for fitting the Band 6 data.


Species Transition Frequency _A_ _i j_ _E_ up
(J K L M                    - J K L M) (GHz) (s [−][1] ) (K)
CH 3 OH 20 8 13 2        - 21 7 14 2 260.0643 2.1 × 10 [−][5] 808.2
20 3 18 0                      - 20 2 19 0 260.3815 9.1 × 10 [−][5] 536.9
2 1 1 1                         - 1 0 1 1 261.8057 5.6 × 10 [−][5] 28.0
13 CH 3 OH 2 1 1 0               - 1 0 1 0 259.9865 5.5 × 10 [−][5] 27.9
18 3 16 +0                    - 18 2 17 -0 260.0888 9.2 × 10 [−][5] 437.2
20 3 18 +0                    - 20 2 19 -0 262.7673 9.4 × 10 [−][5] 525.4
7 4 4 -0                         - 8 3 5 -0 262.9130 1.7 × 10 [−][5] 144.2
7 4 3 +0                      - 8 3 6 +0 262.9203 1.7 × 10 [−][5] 144.2
5 2 3 0                         - 4 1 3 0 263.1133 7.4 × 10 [−][5] 56.3
11 2 10 -0                      - 10 3 7 -0 263.3060 2.9 × 10 [−][5] 187.3
25 -7 18 0                      - 26 -6 20 0 263.5779 2.8 × 10 [−][5] 996.5
CH [18] 3 [OH] 12 2 10 4        - 13 3 10 4 260.0355 7.1 × 10 [−][5] 537.2
16 3 13 0                      - 16 2 14 0 260.3163 9.3 × 10 [−][5] 352.6
15 1 15 1                      - 14 2 13 1 260.4403 2.8 × 10 [−][5] 272.2
12 3 9 0                       - 12 2 10 0 261.8972 9.2 × 10 [−][5] 223.6
11 3 8 0                       - 11 2 9 0 262.1524 9.2 × 10 [−][5] 196.9
7 3 4 0                         - 7 2 5 0 262.7722 8.6 × 10 [−][5] 112.4
6 3 3 0                         - 6 2 4 0 262.8532 8.3 × 10 [−][5] 96.8
5 3 2 0                         - 5 2 3 0 262.9139 7.7 × 10 [−][5] 83.5
4 3 1 0                         - 4 2 2 0 262.9583 6.8 × 10 [−][5] 72.3
5 3 3 0                         - 5 2 4 0 262.9825 7.7 × 10 [−][5] 83.5
4 3 2 0                         - 4 2 3 0 262.9878 6.8 × 10 [−][5] 72.3
3 3 0 0                         - 3 2 1 0 262.9897 4.8 × 10 [−][5] 63.4
6 3 4 0                         - 6 2 5 0 262.9900 8.3 × 10 [−][5] 96.8
3 3 1 0                         - 3 2 2 0 262.9995 4.8 × 10 [−][5] 63.4
7 3 5 0                         - 7 2 6 0 263.0177 8.6 × 10 [−][5] 112.4
8 3 6 0                         - 8 2 7 0 263.0739 8.9 × 10 [−][5] 130.2
9 3 7 0                         - 9 2 8 0 263.1684 9.0 × 10 [−][5] 150.2
10 3 8 0                       - 10 2 9 0 263.3116 9.2 × 10 [−][5] 172.5
16 5 12 4                      - 17 6 12 4 263.4603 5.8 × 10 [−][5] 846.9
11 3 9 0                       - 11 2 10 0 263.5151 9.2 × 10 [−][5] 196.9
CH 2 DOH 25 5 20 2        - 24 6 19 2 260.0710 3.7 × 10 [−][6] 811.2
25 5 21 2                      - 24 6 18 2 260.0956 3.7 × 10 [−][6] 811.2
28 2 26 1                      - 28 1 27 1 260.1369 3.5 × 10 [−][5] 902.1
16 6 10 2                      - 17 5 12 1 260.1467 1.1 × 10 [−][5] 448.1
16 6 11 2                      - 17 5 13 1 260.1470 1.1 × 10 [−][5] 448.1
10 6 5 1                       - 11 5 7 2 260.2246 7.1 × 10 [−][6] 269.6
10 6 4 1                       - 11 5 6 2 260.2247 7.1 × 10 [−][6] 269.6
24 6 19 1                      - 23 7 16 0 260.4056 1.2 × 10 [−][5] 793.9
24 6 18 1                      - 23 7 17 0 260.4067 1.2 × 10 [−][5] 793.9
22 2 20 1                      - 22 0 22 2 261.7345 1.0 × 10 [−][6] 571.6
21 5 17 1                      - 20 6 14 0 261.8903 2.7 × 10 [−][5] 602.5
21 5 16 1                      - 20 6 15 0 261.8934 2.7 × 10 [−][5] 602.5
18 4 14 2                      - 17 5 12 1 261.9426 9.3 × 10 [−][6] 448.2
18 4 15 2                      - 17 5 13 1 261.9678 9.4 × 10 [−][6] 448.2
10 1 9 1                       - 9 2 8 1 262.1729 6.5 × 10 [−][6] 135.5
30 0 30 0                      - 29 2 28 2 262.7597 1.3 × 10 [−][6] 978.8
CH 3 CH 2 OH 36 7 29 2        - 35 8 28 2 259.9564 3.4 × 10 [−][5] 623.2
25 2 24 2                      - 25 1 25 2 260.0077 1.1 × 10 [−][4] 272.8
15 6 10 0                      - 14 6 9 0 260.0138 1.3 × 10 [−][4] 200.5
15 6 9 0                       - 14 6 8 0 260.0138 1.3 × 10 [−][4] 200.5
15 3 13 1                      - 14 3 12 1 260.0466 1.5 × 10 [−][4] 172.5
15 1 14 0                      - 14 1 13 0 260.0902 1.6 × 10 [−][4] 159.6
15 5 11 1                      - 14 5 10 1 260.1076 1.4 × 10 [−][4] 192.1
15 5 10 1                      - 14 5 9 1 260.1227 1.4 × 10 [−][4] 192.1
15 3 13 0                      - 14 3 12 0 260.1416 1.5 × 10 [−][4] 167.7


Article number, page 32 of 44

**Table E.3.** continued.



M. L. van Gelder et al.: Complex organic molecules in low-mass protostars on solar system scales


Species Transition Frequency _A_ _i j_ _E_ up
(J K L M           - J K L M) (GHz) (s [−][1] ) (K)
15 5 11 0            - 14 5 10 0 260.2498 1.4 × 10 [−][4] 187.2
15 5 10 0            - 14 5 9 0 260.2661 1.4 × 10 [−][4] 187.2
13 2 11 1            - 13 1 13 0 260.3086 6.2 × 10 [−][5] 143.3
7 1 6 1              - 6 0 6 0 260.4376 6.7 × 10 [−][5] 86.7
28 3 26 2            - 28 2 27 2 261.8160 1.1 × 10 [−][4] 351.0
34 4 31 2            - 33 5 28 2 261.9750 4.1 × 10 [−][5] 520.7
23 16 7 0            - 24 15 9 1 262.0787 4.1 × 10 [−][6] 599.0
23 16 8 0            - 24 15 10 1 262.0787 4.1 × 10 [−][6] 599.0
13 2 12 2            - 12 1 11 2 262.1543 6.7 × 10 [−][5] 81.0
43 5 38 2            - 43 4 39 2 262.8568 1.1 × 10 [−][4] 840.5
35 3 32 1            - 35 3 33 1 263.0739 2.4 × 10 [−][6] 604.2
22 2 20 0            - 22 1 22 1 263.1656 6.4 × 10 [−][5] 276.2
43 11 33 1           - 42 12 31 0 263.4075 1.7 × 10 [−][5] 996.0
43 11 32 1           - 42 12 30 0 263.4080 1.7 × 10 [−][5] 996.0
32 4 29 2            - 31 5 26 2 263.4372 4.1 × 10 [−][5] 464.7
15 3 12 1            - 14 3 11 1 263.4725 1.6 × 10 [−][4] 173.0
38 8 31 0            - 38 7 31 1 263.5386 6.2 × 10 [−][5] 752.0
30 16 14 2           - 31 15 17 2 263.6169 1.5 × 10 [−][5] 711.0
30 16 15 2           - 31 15 16 2 263.6169 1.5 × 10 [−][5] 711.0
13 3 11 0            - 12 2 11 1 263.6955 4.4 × 10 [−][5] 143.6
39 6 34 0            - 38 7 32 1 263.7078 2.2 × 10 [−][5] 751.8
CH 3 CHO 31 10 22 4  - 32 9 24 4 259.9788 1.4 × 10 [−][5] 886.7
44 6 39 0            - 43 7 36 0 260.0225 1.9 × 10 [−][5] 998.9
32 2 30 6            - 33 1 33 6 260.1158 1.8 × 10 [−][6] 887.2
6 1 5 8              - 5 1 5 7 260.1739 4.1 × 10 [−][5] 406.7
19 3 17 0            - 19 2 18 0 260.2834 5.7 × 10 [−][5] 196.4
13 1 13 1            - 12 0 12 2 260.4080 7.7 × 10 [−][5] 83.9
13 1 13 4            - 12 0 12 5 261.8892 7.6 × 10 [−][5] 288.3
14 5 10 6            - 13 5 9 6 261.9566 5.7 × 10 [−][4] 545.7
14 5 9 6             - 13 5 8 6 261.9567 5.7 × 10 [−][4] 545.7
17 0 17 8            - 16 1 16 7 261.9591 7.2 × 10 [−][5] 516.5
10 1 10 7            - 9 0 9 8 262.1191 5.3 × 10 [−][5] 431.0
9 2 7 6              - 9 1 8 6 262.7285 7.8 × 10 [−][5] 427.8
14 0 14 3            - 13 0 13 3 262.7300 6.3 × 10 [−][4] 302.3
14 1 14 6            - 13 1 13 6 262.8122 5.9 × 10 [−][4] 466.8
17 7 10 2            - 18 6 12 2 262.8291 1.2 × 10 [−][5] 252.0
14 9 5 8             - 13 9 4 8 262.8903 3.8 × 10 [−][4] 664.5
14 0 14 2            - 13 0 13 2 262.9601 6.2 × 10 [−][4] 95.8
7 5 3 3              - 8 4 4 3 262.9883 5.7 × 10 [−][6] 285.4
7 5 2 3              - 8 4 5 3 262.9893 5.7 × 10 [−][6] 285.4
14 0 14 0            - 13 0 13 0 263.0040 6.2 × 10 [−][4] 95.7
29 4 25 5            - 29 3 26 5 263.0099 7.5 × 10 [−][5] 645.8
10 1 10 6            - 9 0 9 6 263.1973 7.9 × 10 [−][5] 421.7
23 1 22 5            - 23 0 23 5 263.3144 3.5 × 10 [−][5] 466.0
6 2 5 1              - 5 1 5 1 263.4217 1.1 × 10 [−][5] 28.5
10 2 9 7             - 10 0 10 8 263.5180 2.4 × 10 [−][6] 440.1
15 2 13 5            - 15 1 15 4 263.7146 3.1 × 10 [−][6] 327.0
7 2 6 1              - 6 1 5 2 263.7366 3.4 × 10 [−][5] 34.9
CH 3 OCHO 35 8 27 3  - 34 9 26 3 260.0750 5.8 × 10 [−][6] 605.4
44 11 34 4           - 44 10 35 4 260.1058 2.5 × 10 [−][5] 853.7
46 8 38 3            - 46 7 39 3 260.1156 2.5 × 10 [−][5] 881.6
21 10 12 1           - 21 9 13 1 260.1286 2.1 × 10 [−][5] 202.8
21 10 11 2           - 21 9 12 2 260.1398 2.1 × 10 [−][5] 202.8
21 10 11 0           - 21 9 12 0 260.1626 2.1 × 10 [−][5] 202.8
21 10 12 0           - 21 9 13 0 260.1645 2.1 × 10 [−][5] 202.8
43 11 33 0           - 43 10 34 0 260.1757 2.8 × 10 [−][5] 644.0


Article number, page 33 of 44

**Table E.3.** continued.



_A&A proofs:_ manuscript no. COM_paper


Species Transition Frequency _A_ _i j_ _E_ up
(J K L M          - J K L M) (GHz) (s [−][1] ) (K)
44 11 34 0          - 44 10 35 0 260.1818 2.8 × 10 [−][5] 670.6
43 11 33 1          - 43 10 34 1 260.2286 2.8 × 10 [−][5] 644.0
44 9 36 4           - 44 8 37 4 260.2328 2.6 × 10 [−][5] 829.2
44 11 34 1          - 44 10 35 1 260.2341 2.8 × 10 [−][5] 670.5
13 4 10 4           - 12 3 10 4 260.2388 3.8 × 10 [−][6] 251.4
43 11 33 4          - 43 10 34 4 260.2415 2.4 × 10 [−][5] 827.3
21 3 18 2           - 20 3 17 2 260.2445 2.6 × 10 [−][4] 146.8
21 3 18 0           - 20 3 17 0 260.2551 2.6 × 10 [−][4] 146.8
25 10 15 3          - 25 9 16 3 260.2673 2.3 × 10 [−][5] 445.1
12 3 9 2           - 11 2 10 1 260.2897 4.5 × 10 [−][6] 53.2
25 10 16 3          - 25 9 17 3 260.2967 2.3 × 10 [−][5] 445.1
12 3 9 0           - 11 2 10 0 260.3608 4.5 × 10 [−][6] 53.2
21 8 13 2           - 20 8 12 2 260.3843 2.3 × 10 [−][4] 179.2
21 8 14 0           - 20 8 13 0 260.3927 2.3 × 10 [−][4] 179.2
21 8 14 1           - 20 8 13 1 260.4040 2.3 × 10 [−][4] 179.2
21 8 13 0           - 20 8 12 0 260.4153 2.3 × 10 [−][4] 179.2
38 11 28 4          - 38 10 28 5 260.4369 1.6 × 10 [−][6] 705.0
38 11 27 2          - 38 10 28 2 261.7075 2.7 × 10 [−][5] 520.6
21 7 14 2           - 20 7 13 2 261.7155 2.4 × 10 [−][4] 169.6
43 9 35 0           - 42 10 32 0 261.7196 3.6 × 10 [−][6] 619.6
21 6 15 5           - 20 6 14 5 261.7271 2.4 × 10 [−][4] 348.0
43 9 35 1           - 42 10 32 2 261.7273 3.6 × 10 [−][6] 619.6
21 7 14 0           - 20 7 13 0 261.7466 2.4 × 10 [−][4] 169.5
44 9 36 4           - 43 10 33 5 261.7591 3.4 × 10 [−][6] 829.2
21 6 15 3           - 20 6 14 3 261.7612 2.5 × 10 [−][4] 348.1
17 10 8 1           - 17 9 9 1 261.7731 1.8 × 10 [−][5] 156.6
17 10 7 2           - 17 9 8 2 261.7850 1.8 × 10 [−][5] 156.6
17 10 7 0           - 17 9 8 0 261.8223 1.8 × 10 [−][5] 156.6
17 10 8 0           - 17 9 9 0 261.8223 1.8 × 10 [−][5] 156.6
39 9 31 4           - 39 7 32 5 261.8334 6.1 × 10 [−][6] 703.9
42 10 33 4          - 41 11 31 4 261.8559 3.2 × 10 [−][6] 789.0
42 9 34 3           - 41 10 31 3 261.8562 4.4 × 10 [−][6] 777.0
24 10 14 5          - 24 9 15 5 261.9112 2.3 × 10 [−][5] 430.6
46 10 37 3          - 46 9 38 3 261.9118 2.8 × 10 [−][5] 895.3
38 9 30 0           - 38 7 31 0 261.9944 6.0 × 10 [−][6] 496.2
16 10 7 1           - 16 9 8 1 262.0360 1.7 × 10 [−][5] 146.6
16 10 6 2           - 16 9 7 2 262.0478 1.7 × 10 [−][5] 146.6
41 11 31 0          - 41 10 32 0 262.0580 2.8 × 10 [−][5] 592.7
38 9 30 1           - 38 7 31 2 262.0825 6.0 × 10 [−][6] 496.2
16 10 6 0           - 16 9 7 0 262.0882 1.7 × 10 [−][5] 146.6
16 10 7 0           - 16 9 8 0 262.0882 1.7 × 10 [−][5] 146.6
37 5 32 5           - 37 5 33 4 262.1035 8.9 × 10 [−][6] 625.0
41 11 31 1          - 41 10 32 1 262.1078 2.8 × 10 [−][5] 592.7
21 7 14 2           - 20 7 14 1 262.1113 4.6 × 10 [−][6] 169.6
19 4 16 4           - 18 3 15 5 262.1355 1.7 × 10 [−][5] 309.7
41 11 31 4          - 41 10 32 4 262.7105 2.4 × 10 [−][5] 776.5
43 9 35 0           - 43 7 36 0 262.7268 9.2 × 10 [−][6] 619.6
46 11 36 0          - 46 10 37 0 262.7278 2.9 × 10 [−][5] 725.6
23 10 13 5          - 23 9 14 5 262.7323 2.3 × 10 [−][5] 416.5
12 10 2 0           - 12 9 3 0 262.7462 1.1 × 10 [−][5] 112.4
12 10 3 0           - 12 9 4 0 262.7462 1.1 × 10 [−][5] 112.4
43 9 35 1           - 43 7 36 2 262.7498 9.2 × 10 [−][6] 619.6
11 10 2 1           - 11 9 3 1 262.7698 8.3 × 10 [−][6] 105.3
46 11 36 1          - 46 10 37 1 262.7761 2.9 × 10 [−][5] 725.5
11 10 1 2           - 11 9 2 2 262.7821 8.3 × 10 [−][6] 105.3
12 3 9 3           - 11 1 10 3 262.8302 2.4 × 10 [−][6] 240.5



Article number, page 34 of 44

**Table E.3.** continued.



M. L. van Gelder et al.: Complex organic molecules in low-mass protostars on solar system scales


Species Transition Frequency _A_ _i j_ _E_ up
(J K L M           - J K L M) (GHz) (s [−][1] ) (K)
10 10 1 1            - 10 9 2 1 262.8348 4.7 × 10 [−][6] 98.8
11 10 1 0            - 11 9 2 0 262.8348 8.3 × 10 [−][6] 105.3
11 10 2 0            - 11 9 3 0 262.8348 8.3 × 10 [−][6] 105.3
10 10 0 2            - 10 9 1 2 262.8472 4.7 × 10 [−][6] 98.8
32 7 25 3            - 31 8 24 3 262.8826 6.5 × 10 [−][6] 535.9
10 10 0 0            - 10 9 1 0 262.9019 4.7 × 10 [−][6] 98.8
10 10 1 0            - 10 9 2 0 262.9019 4.7 × 10 [−][6] 98.8
39 7 33 1            - 39 6 34 1 262.9162 2.2 × 10 [−][5] 497.3
39 7 33 0            - 39 6 34 0 262.9513 2.2 × 10 [−][5] 497.3
43 7 36 3            - 43 7 37 3 262.9776 9.4 × 10 [−][6] 790.0
51 14 38 1           - 50 15 35 2 262.9834 2.0 × 10 [−][6] 918.0
44 9 36 3            - 43 10 33 3 263.0190 3.6 × 10 [−][6] 828.7
42 10 33 1           - 41 11 30 2 263.0193 5.5 × 10 [−][6] 605.5
20 10 10 3           - 20 9 11 3 263.0300 2.1 × 10 [−][5] 377.5
20 10 11 3           - 20 9 12 3 263.0305 2.1 × 10 [−][5] 377.5
22 10 13 4           - 22 9 14 4 263.0364 2.2 × 10 [−][5] 402.5
29 1 28 3            - 29 1 29 3 263.0528 2.8 × 10 [−][6] 427.4
29 1 28 3            - 29 0 29 3 263.0529 5.2 × 10 [−][6] 427.4
29 2 28 3            - 29 1 29 3 263.0536 5.2 × 10 [−][6] 427.4
29 2 28 3            - 29 0 29 3 263.0536 2.8 × 10 [−][6] 427.4
42 10 33 0           - 41 11 30 0 263.0820 5.5 × 10 [−][6] 605.5
44 11 34 1           - 43 12 31 2 263.1054 5.5 × 10 [−][6] 670.5
44 11 34 0           - 43 12 31 0 263.1933 5.6 × 10 [−][6] 670.6
51 14 38 1           - 50 15 36 1 263.3156 3.5 × 10 [−][6] 918.0
43 9 35 4            - 42 10 32 5 263.3286 3.9 × 10 [−][6] 803.0
40 6 34 3            - 40 6 35 3 263.3459 9.2 × 10 [−][6] 704.3
19 10 10 3           - 19 9 11 3 263.3471 2.1 × 10 [−][5] 365.7
19 10 9 3            - 19 9 10 3 263.3471 2.1 × 10 [−][5] 365.7
49 9 40 2            - 49 8 41 2 263.3632 2.7 × 10 [−][5] 798.0
42 8 35 3            - 42 7 36 3 263.3690 2.5 × 10 [−][5] 765.2
39 7 33 1            - 39 5 34 2 263.3753 9.7 × 10 [−][6] 497.3
49 9 40 0            - 49 8 41 0 263.3938 2.7 × 10 [−][5] 798.0
39 7 33 0            - 39 5 34 0 263.4086 9.7 × 10 [−][6] 497.3
22 10 12 5           - 22 9 13 5 263.4524 2.2 × 10 [−][5] 403.0
9 6 4 4              - 8 5 4 4 263.4606 2.9 × 10 [−][5] 237.4
29 6 23 3            - 28 7 22 3 263.4713 7.7 × 10 [−][6] 472.9
47 12 35 5           - 47 11 36 5 263.5168 2.5 × 10 [−][5] 950.7
31 8 24 4            - 31 6 25 5 263.5309 3.7 × 10 [−][6] 523.5
51 10 42 0           - 50 11 39 0 263.5493 2.1 × 10 [−][6] 859.8
37 6 32 4            - 37 5 33 4 263.5905 2.0 × 10 [−][5] 625.0
51 10 42 1           - 50 11 39 2 263.5969 2.1 × 10 [−][6] 859.8
18 10 8 3            - 18 9 9 3 263.6061 2.0 × 10 [−][5] 354.6
18 10 9 3            - 18 9 10 3 263.6061 2.0 × 10 [−][5] 354.6
21 10 12 4           - 21 9 13 4 263.6491 2.2 × 10 [−][5] 389.6
40 11 30 0           - 40 10 31 0 263.6666 2.9 × 10 [−][5] 568.0
37 6 32 4            - 37 4 33 5 263.7116 9.1 × 10 [−][6] 625.0
40 11 30 1           - 40 10 31 1 263.7127 2.9 × 10 [−][5] 568.0
CH 3 OCH 3 20 5 16 3  - 20 4 17 3 259.9825 9.2 × 10 [−][5] 226.6
20 5 16 5            - 20 4 17 5 259.9826 9.2 × 10 [−][5] 226.6
20 5 16 1            - 20 4 17 1 259.9844 9.2 × 10 [−][5] 226.6
20 5 16 0            - 20 4 17 0 259.9863 9.2 × 10 [−][5] 226.6
24 5 20 3            - 24 4 21 3 260.0034 9.6 × 10 [−][5] 308.9
24 5 20 5            - 24 4 21 5 260.0034 9.6 × 10 [−][5] 308.9
24 5 20 1            - 24 4 21 1 260.0044 9.6 × 10 [−][5] 308.9
24 5 20 0            - 24 4 21 0 260.0054 9.6 × 10 [−][5] 308.9
19 5 15 3            - 19 4 16 3 260.3271 9.1 × 10 [−][5] 208.3


Article number, page 35 of 44

**Table E.3.** continued.



_A&A proofs:_ manuscript no. COM_paper


Species Transition Frequency _A_ _i j_ _E_ up
(J K L M          - J K L M) (GHz) (s [−][1] ) (K)
19 5 15 5           - 19 4 16 5 260.3272 9.1 × 10 [−][5] 208.3
19 5 15 1           - 19 4 16 1 260.3292 9.1 × 10 [−][5] 208.3
19 5 15 0           - 19 4 16 0 260.3313 9.1 × 10 [−][5] 208.3
16 5 11 5           - 16 4 12 5 260.4005 8.7 × 10 [−][5] 159.0
16 5 11 3           - 16 4 12 3 260.4011 8.6 × 10 [−][5] 159.0
16 5 11 1           - 16 4 12 1 260.4032 8.7 × 10 [−][5] 159.0
16 5 11 0           - 16 4 12 0 260.4056 8.7 × 10 [−][5] 159.0
28 4 25 0           - 27 5 22 0 261.8399 2.3 × 10 [−][5] 393.2
28 4 25 1           - 27 5 22 1 261.8402 2.3 × 10 [−][5] 393.2
28 4 25 3           - 27 5 22 3 261.8404 2.3 × 10 [−][5] 393.2
28 4 25 5           - 27 5 22 5 261.8404 2.3 × 10 [−][5] 393.2
14 5 10 3           - 14 4 10 3 261.8785 1.1 × 10 [−][5] 130.8
14 5 10 1           - 14 4 10 1 261.8832 3.9 × 10 [−][6] 130.8
14 5 9 5           - 14 4 10 5 261.8941 8.6 × 10 [−][5] 130.8
14 5 9 3           - 14 4 10 3 261.8965 7.5 × 10 [−][5] 130.8
14 5 9 1           - 14 4 10 1 261.8976 8.2 × 10 [−][5] 130.8
14 5 9 0           - 14 4 10 0 261.8998 8.6 × 10 [−][5] 130.8
15 5 11 3           - 15 4 12 3 261.9530 8.4 × 10 [−][5] 144.4
15 5 11 5           - 15 4 12 5 261.9543 8.7 × 10 [−][5] 144.4
15 5 11 1           - 15 4 12 1 261.9566 8.6 × 10 [−][5] 144.4
15 5 11 0           - 15 4 12 0 261.9596 8.7 × 10 [−][5] 144.4
15 5 10 3           - 15 4 12 3 261.9814 3.7 × 10 [−][6] 144.4
15 5 10 1           - 15 4 12 1 261.9830 1.0 × 10 [−][6] 144.4
12 5 7 3           - 12 4 8 3 262.7548 2.8 × 10 [−][5] 106.2
12 5 8 1           - 12 4 8 1 262.7616 2.3 × 10 [−][5] 106.2
12 5 7 5           - 12 4 8 5 262.7637 8.2 × 10 [−][5] 106.2
12 5 8 3           - 12 4 8 3 262.7688 5.4 × 10 [−][5] 106.2
12 5 7 1           - 12 4 8 1 262.7690 5.9 × 10 [−][5] 106.2
12 5 7 0           - 12 4 8 0 262.7699 8.2 × 10 [−][5] 106.2
8 2 6 5            - 7 1 7 5 262.7712 3.3 × 10 [−][5] 38.6
8 2 6 3            - 7 1 7 3 262.7712 3.3 × 10 [−][5] 38.6
8 2 6 1            - 7 1 7 1 262.7740 3.3 × 10 [−][5] 38.6
8 2 6 0            - 7 1 7 0 262.7769 3.3 × 10 [−][5] 38.6
12 5 7 3           - 12 4 9 3 262.8843 5.5 × 10 [−][5] 106.2
12 5 8 5           - 12 4 9 5 262.8893 8.2 × 10 [−][5] 106.2
12 5 8 1           - 12 4 9 1 262.8902 5.9 × 10 [−][5] 106.2
12 5 8 0           - 12 4 9 0 262.8954 8.2 × 10 [−][5] 106.2
12 5 7 1           - 12 4 9 1 262.8976 2.3 × 10 [−][5] 106.2
12 5 8 3           - 12 4 9 3 262.8982 2.8 × 10 [−][5] 106.2
27 5 23 3           - 27 4 24 3 262.9642 1.0 × 10 [−][4] 380.2
27 5 23 5           - 27 4 24 5 262.9642 1.0 × 10 [−][4] 380.2
27 5 23 1           - 27 4 24 1 262.9645 1.0 × 10 [−][4] 380.2
27 5 23 0           - 27 4 24 0 262.9649 1.0 × 10 [−][4] 380.2
11 5 6 3           - 11 4 7 3 263.0353 2.6 × 10 [−][5] 95.2
11 5 7 1           - 11 4 7 1 263.0428 2.8 × 10 [−][5] 95.2
11 5 6 5           - 11 4 7 5 263.0441 8.0 × 10 [−][5] 95.2
11 5 7 3           - 11 4 7 3 263.0494 5.3 × 10 [−][5] 95.2
11 5 6 1           - 11 4 7 1 263.0500 5.1 × 10 [−][5] 95.2
11 5 6 0           - 11 4 7 0 263.0504 8.0 × 10 [−][5] 95.2
11 5 6 3           - 11 4 8 3 263.1021 5.3 × 10 [−][5] 95.2
11 5 7 5           - 11 4 8 5 263.1075 8.0 × 10 [−][5] 95.2
11 5 7 1           - 11 4 8 1 263.1079 5.1 × 10 [−][5] 95.2
11 5 7 0           - 11 4 8 0 263.1138 8.0 × 10 [−][5] 95.2
11 5 6 1           - 11 4 8 1 263.1151 2.8 × 10 [−][5] 95.2
11 5 7 3           - 11 4 8 3 263.1163 2.6 × 10 [−][5] 95.2
9 5 4 3            - 9 4 6 3 263.3887 6.4 × 10 [−][6] 76.1



Article number, page 36 of 44

**Table E.3.** continued.



M. L. van Gelder et al.: Complex organic molecules in low-mass protostars on solar system scales


Species Transition Frequency _A_ _i j_ _E_ up
(J K L M           - J K L M) (GHz) (s [−][1] ) (K)
9 5 5 1              - 9 4 5 1 263.3991 1.5 × 10 [−][5] 76.1
9 5 4 5              - 9 4 5 5 263.4011 7.3 × 10 [−][5] 76.1
9 5 5 3              - 9 4 6 3 263.4037 6.6 × 10 [−][5] 76.1
9 5 4 1              - 9 4 5 1 263.4066 5.8 × 10 [−][5] 76.1
9 5 4 0              - 9 4 5 0 263.4078 7.3 × 10 [−][5] 76.1
9 5 4 3              - 9 4 5 3 263.4114 6.6 × 10 [−][5] 76.1
9 5 5 5              - 9 4 6 5 263.4140 7.3 × 10 [−][5] 76.1
9 5 5 1              - 9 4 6 1 263.4151 5.8 × 10 [−][5] 76.1
9 5 5 0              - 9 4 6 0 263.4206 7.3 × 10 [−][5] 76.1
9 5 4 1              - 9 4 6 1 263.4226 1.5 × 10 [−][5] 76.1
9 5 5 3              - 9 4 5 3 263.4263 6.4 × 10 [−][6] 76.1
8 5 3 3              - 8 4 5 3 263.4921 1.1 × 10 [−][6] 67.9
8 5 4 1              - 8 4 4 1 263.5038 3.8 × 10 [−][6] 67.9
8 5 3 5              - 8 4 4 5 263.5071 6.7 × 10 [−][5] 67.9
8 5 4 3              - 8 4 5 3 263.5074 6.6 × 10 [−][5] 67.9
8 5 3 1              - 8 4 4 1 263.5115 6.3 × 10 [−][5] 67.9
8 5 3 3              - 8 4 4 3 263.5118 6.6 × 10 [−][5] 67.9
8 5 4 5              - 8 4 5 5 263.5121 6.7 × 10 [−][5] 67.9
8 5 3 0              - 8 4 4 0 263.5140 6.7 × 10 [−][5] 67.9
8 5 4 1              - 8 4 5 1 263.5146 6.3 × 10 [−][5] 67.9
8 5 4 0              - 8 4 5 0 263.5189 6.7 × 10 [−][5] 67.9
8 5 3 1              - 8 4 5 1 263.5222 3.8 × 10 [−][6] 67.9
8 5 4 3              - 8 4 4 3 263.5271 1.1 × 10 [−][6] 67.9
7 5 3 3              - 7 4 4 3 263.5784 6.0 × 10 [−][5] 60.6
7 5 2 5              - 7 4 3 5 263.5795 6.0 × 10 [−][5] 60.6
7 5 3 5              - 7 4 4 5 263.5812 6.0 × 10 [−][5] 60.6
7 5 2 3              - 7 4 3 3 263.5822 6.0 × 10 [−][5] 60.6
7 5 2 1              - 7 4 3 1 263.5828 5.9 × 10 [−][5] 60.6
7 5 3 1              - 7 4 4 1 263.5848 5.9 × 10 [−][5] 60.6
7 5 2 0              - 7 4 3 0 263.5865 6.0 × 10 [−][5] 60.6
7 5 3 0              - 7 4 4 0 263.5881 6.0 × 10 [−][5] 60.6
6 5 2 3              - 6 4 3 3 263.6249 4.9 × 10 [−][5] 54.3
6 5 1 5              - 6 4 2 5 263.6266 4.9 × 10 [−][5] 54.3
6 5 2 5              - 6 4 3 5 263.6271 4.9 × 10 [−][5] 54.3
6 5 1 3              - 6 4 2 3 263.6288 4.9 × 10 [−][5] 54.3
6 5 1 1              - 6 4 2 1 263.6294 4.8 × 10 [−][5] 54.3
6 5 2 1              - 6 4 3 1 263.6313 4.8 × 10 [−][5] 54.3
6 5 1 0              - 6 4 2 0 263.6337 4.9 × 10 [−][5] 54.3
6 5 2 0              - 6 4 3 0 263.6342 4.9 × 10 [−][5] 54.3
5 5 1 3              - 5 4 2 3 263.6534 3.1 × 10 [−][5] 48.8
5 5 0 5              - 5 4 1 5 263.6553 3.1 × 10 [−][5] 48.8
5 5 1 5              - 5 4 2 5 263.6553 3.1 × 10 [−][5] 48.8
5 5 0 3              - 5 4 1 3 263.6573 3.1 × 10 [−][5] 48.8
5 5 0 1              - 5 4 1 1 263.6579 3.1 × 10 [−][5] 48.8
5 5 1 1              - 5 4 2 1 263.6599 3.1 × 10 [−][5] 48.8
5 5 0 0              - 5 4 1 0 263.6625 3.1 × 10 [−][5] 48.8
5 5 1 0              - 5 4 2 0 263.6625 3.1 × 10 [−][5] 48.8
CH 3 COCH 3 38 26 12 0  - 38 23 15 0 260.0197 2.3 × 10 [−][5] 615.2
10 9 2 1             - 9 6 3 1 260.0832 4.7 × 10 [−][6] 49.8
25 19 7 0            - 25 16 10 1 260.0881 2.4 × 10 [−][6] 277.8
29 27 2 0            - 28 28 1 0 260.1037 1.0 × 10 [−][6] 404.6
29 27 3 0            - 28 28 0 0 260.1037 1.0 × 10 [−][6] 404.6
23 16 8 1            - 22 17 5 1 260.1095 3.5 × 10 [−][5] 229.8
28 25 4 0            - 27 26 2 1 260.1376 3.3 × 10 [−][6] 370.0
27 23 5 0            - 26 24 2 0 260.1771 7.1 × 10 [−][6] 337.4
27 23 4 0            - 26 24 3 0 260.1771 7.1 × 10 [−][6] 337.4


Article number, page 37 of 44

**Table E.3.** continued.



_A&A proofs:_ manuscript no. COM_paper


Species Transition Frequency _A_ _i j_ _E_ up
(J K L M          - J K L M) (GHz) (s [−][1] ) (K)
25 19 7 1           - 25 16 10 1 260.1828 4.4 × 10 [−][6] 277.8
28 17 11 0          - 28 14 14 0 260.1892 7.0 × 10 [−][6] 330.6
34 24 11 1          - 34 21 13 2 260.1953 1.7 × 10 [−][6] 497.8
9 9 0 0            - 8 6 3 0 260.2293 1.2 × 10 [−][6] 42.7
44 14 30 0          - 44 13 31 0 260.2497 3.0 × 10 [−][4] 690.3
44 15 30 0          - 44 14 31 0 260.2497 3.0 × 10 [−][4] 690.3
44 14 30 0          - 44 13 31 1 260.2689 3.4 × 10 [−][5] 690.3
44 14 30 0          - 44 14 31 1 260.2689 3.4 × 10 [−][5] 690.3
44 15 30 0          - 44 13 31 1 260.2689 3.9 × 10 [−][4] 690.3
44 15 30 0          - 44 14 31 1 260.2689 3.9 × 10 [−][4] 690.3
29 27 3 0           - 28 28 0 1 260.2727 1.0 × 10 [−][6] 404.5
28 17 11 0          - 28 14 14 1 260.2796 7.0 × 10 [−][6] 330.6
44 14 30 1          - 44 14 31 2 260.2881 3.0 × 10 [−][4] 690.2
44 15 30 1          - 44 13 31 2 260.2881 3.0 × 10 [−][4] 690.2
44 14 30 1          - 44 14 31 1 260.2881 3.0 × 10 [−][4] 690.2
44 15 30 1          - 44 13 31 1 260.2881 3.0 × 10 [−][4] 690.2
27 19 9 1           - 27 16 12 2 260.3305 6.5 × 10 [−][6] 315.8
28 25 3 0           - 27 26 1 1 260.3326 3.3 × 10 [−][6] 370.0
36 25 11 0          - 36 22 14 1 260.3392 2.0 × 10 [−][5] 555.0
28 17 11 1          - 28 14 14 1 260.3691 6.9 × 10 [−][6] 330.5
28 17 11 1          - 28 14 14 2 260.3772 6.9 × 10 [−][6] 330.5
28 25 4 1           - 27 26 2 2 260.4195 3.3 × 10 [−][6] 369.9
29 27 3 1           - 28 28 0 2 260.4414 1.0 × 10 [−][6] 404.4
38 26 12 1          - 38 23 15 2 261.7077 2.0 × 10 [−][5] 615.2
18 9 9 0           - 18 6 12 0 261.7099 1.0 × 10 [−][6] 134.3
26 21 6 0           - 25 22 4 1 261.7369 1.3 × 10 [−][5] 306.6
30 22 8 1           - 30 19 11 2 261.7414 4.8 × 10 [−][6] 393.3
41 11 30 1          - 41 11 31 2 261.7560 2.6 × 10 [−][4] 576.3
41 12 30 1          - 41 10 31 2 261.7560 2.6 × 10 [−][4] 576.3
41 11 30 1          - 41 10 31 1 261.7561 2.6 × 10 [−][4] 576.3
41 12 30 1          - 41 11 31 1 261.7561 2.6 × 10 [−][4] 576.3
30 22 8 0           - 30 19 11 1 261.7703 5.6 × 10 [−][6] 393.3
41 11 30 0          - 41 10 31 1 261.7955 1.5 × 10 [−][4] 576.4
41 11 30 0          - 41 11 31 1 261.7955 1.5 × 10 [−][4] 576.4
41 12 30 0          - 41 10 31 1 261.7955 2.0 × 10 [−][4] 576.4
41 12 30 0          - 41 11 31 1 261.7955 2.0 × 10 [−][4] 576.4
10 9 1 0           - 9 6 3 1 261.7975 2.4 × 10 [−][6] 49.8
20 7 13 1           - 19 8 12 2 261.8181 4.9 × 10 [−][4] 151.2
20 7 13 1           - 19 8 12 1 261.8182 4.9 × 10 [−][4] 151.2
20 8 13 1           - 19 7 12 2 261.8191 4.9 × 10 [−][4] 151.2
20 8 13 1           - 19 7 12 1 261.8192 4.9 × 10 [−][4] 151.2
41 11 30 0          - 41 10 31 0 261.8347 2.6 × 10 [−][4] 576.4
41 12 30 0          - 41 11 31 0 261.8347 2.6 × 10 [−][4] 576.4
30 22 8 0           - 30 19 11 0 261.8621 7.7 × 10 [−][6] 393.3
20 7 13 0           - 19 8 12 1 261.9017 4.9 × 10 [−][4] 151.1
20 8 13 0           - 19 7 12 1 261.9027 4.9 × 10 [−][4] 151.1
40 27 13 0          - 40 24 16 0 261.9051 2.9 × 10 [−][5] 678.6
21 18 3 1           - 21 15 6 1 261.9131 1.1 × 10 [−][6] 206.3
20 7 13 0           - 19 8 12 0 261.9852 4.9 × 10 [−][4] 151.1
20 8 13 0           - 19 7 12 0 261.9862 4.9 × 10 [−][4] 151.1
26 21 5 1           - 25 22 3 2 261.9892 1.3 × 10 [−][5] 306.6
26 21 6 1           - 25 22 3 1 262.0656 1.3 × 10 [−][5] 306.5
26 21 5 1           - 25 22 4 1 262.0681 1.3 × 10 [−][5] 306.5
26 21 6 1           - 25 22 4 2 262.1439 1.3 × 10 [−][5] 306.5
10 9 1 1           - 9 6 3 2 262.1591 2.6 × 10 [−][6] 49.9
40 10 30 1          - 40 10 31 2 262.1740 2.4 × 10 [−][4] 540.1



Article number, page 38 of 44

**Table E.3.** continued.



M. L. van Gelder et al.: Complex organic molecules in low-mass protostars on solar system scales


Species Transition Frequency _A_ _i j_ _E_ up
(J K L M           - J K L M) (GHz) (s [−][1] ) (K)
40 11 30 1           - 40 9 31 2 262.1740 2.4 × 10 [−][4] 540.1
40 10 30 1           - 40 10 31 1 262.1741 2.4 × 10 [−][4] 540.1
40 11 30 1           - 40 9 31 1 262.1741 2.4 × 10 [−][4] 540.1
50 23 28 1           - 49 24 25 1 262.7522 2.6 × 10 [−][6] 964.3
39 10 30 0           - 39 9 31 0 262.7529 2.3 × 10 [−][4] 504.8
39 9 30 0            - 39 8 31 0 262.7529 2.3 × 10 [−][4] 504.8
50 22 28 0           - 49 25 25 1 262.7640 4.1 × 10 [−][6] 964.3
50 23 28 0           - 49 24 25 1 262.7644 4.1 × 10 [−][6] 964.3
21 6 15 1            - 20 7 14 2 262.7689 5.7 × 10 [−][4] 158.3
21 7 15 1            - 20 6 14 2 262.7689 5.7 × 10 [−][4] 158.3
21 6 15 1            - 20 7 14 1 262.7689 5.7 × 10 [−][4] 158.3
21 7 15 1            - 20 6 14 1 262.7689 5.7 × 10 [−][4] 158.3
50 22 28 0           - 49 25 25 0 262.7764 2.5 × 10 [−][6] 964.4
50 23 28 0           - 49 24 25 0 262.7767 2.6 × 10 [−][6] 964.4
40 27 13 0           - 40 24 16 1 262.8043 3.7 × 10 [−][5] 678.6
21 6 15 0            - 20 7 14 1 262.8419 5.7 × 10 [−][4] 158.2
21 7 15 0            - 20 6 14 1 262.8419 5.7 × 10 [−][4] 158.2
30 17 13 1           - 29 20 10 1 262.8726 6.8 × 10 [−][6] 374.2
30 17 13 0           - 29 20 10 1 262.9092 6.8 × 10 [−][6] 374.3
38 8 30 1            - 38 8 31 2 262.9134 2.1 × 10 [−][4] 470.2
38 9 30 1            - 38 7 31 2 262.9134 2.1 × 10 [−][4] 470.2
38 8 30 1            - 38 8 31 1 262.9135 2.1 × 10 [−][4] 470.2
38 9 30 1            - 38 7 31 1 262.9135 2.1 × 10 [−][4] 470.2
21 6 15 0            - 20 7 14 0 262.9147 5.7 × 10 [−][4] 158.2
21 7 15 0            - 20 6 14 0 262.9147 5.7 × 10 [−][4] 158.2
30 17 13 0           - 29 20 10 0 262.9170 6.8 × 10 [−][6] 374.3
30 17 13 1           - 29 20 10 2 262.9385 6.7 × 10 [−][6] 374.2
23 16 7 1            - 22 17 5 2 262.9661 2.7 × 10 [−][5] 230.0
14 11 4 0            - 13 10 3 0 262.9821 4.6 × 10 [−][4] 90.4
21 18 3 1            - 21 15 6 2 262.9920 1.0 × 10 [−][6] 206.4
38 8 30 0            - 38 7 31 1 263.0452 2.3 × 10 [−][5] 470.3
38 8 30 0            - 38 8 31 1 263.0452 3.9 × 10 [−][5] 470.3
38 9 30 0            - 38 7 31 1 263.0452 2.2 × 10 [−][4] 470.3
38 9 30 0            - 38 8 31 1 263.0452 2.4 × 10 [−][4] 470.3
21 18 4 1            - 21 15 7 2 263.1102 1.0 × 10 [−][6] 206.2
38 8 30 0            - 38 7 31 0 263.1764 2.1 × 10 [−][4] 470.3
38 9 30 0            - 38 8 31 0 263.1764 2.1 × 10 [−][4] 470.3
14 11 4 1            - 13 10 4 2 263.3286 4.4 × 10 [−][4] 90.4
14 11 3 1            - 13 10 3 2 263.3983 4.4 × 10 [−][4] 90.6
37 7 30 0            - 37 6 31 1 263.4085 5.1 × 10 [−][6] 436.6
37 7 30 0            - 37 7 31 1 263.4085 5.1 × 10 [−][6] 436.6
37 8 30 0            - 37 6 31 1 263.4085 2.2 × 10 [−][4] 436.6
37 8 30 0            - 37 7 31 1 263.4085 2.2 × 10 [−][4] 436.6
18 10 9 0            - 17 9 8 1 263.4583 3.2 × 10 [−][4] 134.4
21 18 3 0            - 21 15 6 0 263.5077 1.1 × 10 [−][6] 206.4
14 11 3 0            - 13 10 3 1 263.5148 4.0 × 10 [−][4] 90.5
40 27 13 1           - 40 24 16 1 263.5282 2.9 × 10 [−][5] 678.6
36 6 30 1            - 36 5 31 2 263.5343 1.7 × 10 [−][4] 403.8
36 7 30 1            - 36 6 31 2 263.5343 1.7 × 10 [−][4] 403.8
36 6 30 1            - 36 6 31 1 263.5344 1.7 × 10 [−][4] 403.8
36 7 30 1            - 36 5 31 1 263.5344 1.7 × 10 [−][4] 403.8
37 7 30 0            - 37 7 31 0 263.5783 1.9 × 10 [−][4] 436.6
37 8 30 0            - 37 6 31 0 263.5783 1.9 × 10 [−][4] 436.6
18 10 9 0            - 17 9 8 0 263.6265 3.2 × 10 [−][4] 134.4
23 16 7 0            - 22 17 6 0 263.6422 3.6 × 10 [−][5] 230.0
14 11 4 0            - 13 10 4 1 263.6745 3.9 × 10 [−][4] 90.4
14 10 4 1            - 13 9 5 1 263.6827 3.0 × 10 [−][4] 88.0


Article number, page 39 of 44

**Table E.3.** continued.



_A&A proofs:_ manuscript no. COM_paper


Species Transition Frequency _A_ _i j_ _E_ up
(J K L M          - J K L M) (GHz) (s [−][1] ) (K)
10 8 3 1           - 9 5 5 2 263.7026 2.1 × 10 [−][6] 47.5
25 19 7 0           - 24 20 4 0 263.7264 2.2 × 10 [−][5] 277.8
36 6 30 0           - 36 5 31 1 263.7477 4.5 × 10 [−][5] 403.8
36 6 30 0           - 36 6 31 1 263.7477 4.5 × 10 [−][5] 403.8
36 7 30 0           - 36 5 31 1 263.7477 1.5 × 10 [−][4] 403.8
36 7 30 0           - 36 6 31 1 263.7477 1.5 × 10 [−][4] 403.8
aGg’(CH 2 OH) 2 46 11 35 1 - 45 12 34 1 259.9713 1.3 × 10 [−][5] 593.8
47 3 44 0           - 47 3 45 1 259.9736 8.1 × 10 [−][6] 546.3
47 4 44 0           - 47 2 45 1 259.9737 8.1 × 10 [−][6] 546.3
55 14 41 1          - 55 13 43 0 260.0722 1.2 × 10 [−][5] 855.4
26 12 14 0          - 25 12 13 1 260.1167 3.4 × 10 [−][4] 243.3
26 12 15 0          - 25 12 14 1 260.1167 3.4 × 10 [−][4] 243.3
17 5 13 0           - 16 4 13 1 260.1561 2.1 × 10 [−][5] 87.8
30 13 18 1          - 30 12 18 0 260.2226 8.7 × 10 [−][6] 311.9
30 13 17 1          - 30 12 19 0 260.2226 8.7 × 10 [−][6] 311.9
47 14 34 0          - 47 13 34 1 260.2259 9.0 × 10 [−][6] 651.5
47 14 33 0          - 47 13 35 1 260.2706 8.8 × 10 [−][6] 651.5
29 5 24 1           - 28 6 23 1 260.2757 3.6 × 10 [−][5] 231.5
26 11 16 0          - 25 11 15 1 260.3799 3.5 × 10 [−][4] 232.1
26 11 15 0          - 25 11 14 1 260.3799 3.5 × 10 [−][4] 232.1
46 6 41 1           - 45 7 39 0 260.4379 2.3 × 10 [−][6] 547.7
23 5 18 0           - 22 5 18 0 261.7385 2.2 × 10 [−][6] 149.9
24 13 11 1          - 24 12 13 0 261.7715 8.0 × 10 [−][6] 230.7
24 13 12 1          - 24 12 12 0 261.7715 8.0 × 10 [−][6] 230.7
24 5 19 1           - 23 5 18 0 261.8151 4.2 × 10 [−][4] 162.5
53 14 40 0          - 52 15 37 0 261.8547 1.0 × 10 [−][5] 801.3
53 14 40 1          - 52 15 37 1 261.8655 1.4 × 10 [−][5] 801.5
59 9 51 1           - 59 8 52 1 261.8778 4.0 × 10 [−][5] 914.0
18 4 15 0           - 17 3 15 1 261.8919 9.2 × 10 [−][6] 92.3
26 8 19 0           - 25 8 18 1 261.9036 4.0 × 10 [−][4] 204.5
53 14 39 0          - 52 15 38 0 261.9265 1.0 × 10 [−][5] 801.3
59 9 51 0           - 59 8 52 0 261.9386 4.6 × 10 [−][5] 913.6
53 14 39 1          - 52 15 38 1 261.9416 1.4 × 10 [−][5] 801.5
23 13 10 1          - 23 12 12 0 261.9447 7.8 × 10 [−][6] 218.9
23 13 11 1          - 23 12 11 0 261.9447 7.8 × 10 [−][6] 218.9
60 8 52 0           - 60 8 53 1 261.9497 1.7 × 10 [−][5] 942.7
26 8 18 0           - 25 8 17 1 261.9712 4.0 × 10 [−][4] 204.5
34 9 26 0           - 34 7 27 1 262.0007 2.2 × 10 [−][6] 333.6
50 14 36 1          - 50 13 37 1 262.0294 5.5 × 10 [−][5] 724.4
23 5 18 1           - 22 5 18 1 262.0416 3.6 × 10 [−][6] 150.3
25 3 22 1           - 24 3 21 0 262.0459 4.7 × 10 [−][4] 167.7
45 14 32 0          - 45 13 32 1 262.0479 9.2 × 10 [−][6] 605.6
45 14 31 0          - 45 13 33 1 262.0631 9.1 × 10 [−][6] 605.6
50 14 36 0          - 50 13 37 0 262.0948 5.4 × 10 [−][5] 724.1
22 13 10 1          - 22 12 10 0 262.0986 7.5 × 10 [−][6] 207.6
22 13 9 1           - 22 12 11 0 262.0986 7.5 × 10 [−][6] 207.6
14 6 8 1           - 13 5 8 0 262.1074 1.2 × 10 [−][5] 69.7
34 5 29 1           - 33 6 27 0 262.1490 2.4 × 10 [−][6] 311.8
58 12 47 1          - 58 10 48 0 262.1613 8.3 × 10 [−][6] 917.2
12 7 5 1           - 11 6 5 0 262.7122 1.4 × 10 [−][5] 62.7
12 7 6 1           - 11 6 6 0 262.7128 1.4 × 10 [−][5] 62.7
26 7 20 0           - 25 7 19 1 262.7212 4.0 × 10 [−][4] 197.4
18 5 14 0           - 17 4 13 0 262.7275 2.6 × 10 [−][5] 96.7
25 18 7 1           - 24 18 6 0 262.7483 2.1 × 10 [−][4] 319.0
25 18 8 1           - 24 18 7 0 262.7483 2.1 × 10 [−][4] 319.0
15 13 2 1           - 15 12 4 0 262.7550 3.9 × 10 [−][6] 142.3



Article number, page 40 of 44

**Table E.3.** continued.



M. L. van Gelder et al.: Complex organic molecules in low-mass protostars on solar system scales


Species Transition Frequency _A_ _i j_ _E_ up
(J K L M           - J K L M) (GHz) (s [−][1] ) (K)
15 13 3 1            - 15 12 3 0 262.7550 3.9 × 10 [−][6] 142.3
25 13 12 1           - 24 13 11 0 262.7564 3.2 × 10 [−][4] 243.0
25 13 13 1           - 24 13 12 0 262.7564 3.2 × 10 [−][4] 243.0
51 5 46 1            - 51 4 47 1 262.7644 3.1 × 10 [−][5] 664.3
51 6 46 1            - 51 5 47 1 262.7705 3.1 × 10 [−][5] 664.3
14 13 1 1            - 14 12 3 0 262.8042 2.9 × 10 [−][6] 134.9
14 13 2 1            - 14 12 2 0 262.8042 2.9 × 10 [−][6] 134.9
25 19 6 1            - 24 19 5 0 262.8144 1.9 × 10 [−][4] 337.2
25 19 7 1            - 24 19 6 0 262.8144 1.9 × 10 [−][4] 337.2
26 3 24 1            - 25 3 23 0 262.8239 4.3 × 10 [−][4] 174.2
44 14 31 0           - 44 13 31 1 262.8422 9.2 × 10 [−][6] 583.4
13 13 1 1            - 13 12 1 0 262.8455 1.6 × 10 [−][6] 128.1
44 14 30 0           - 44 13 32 1 262.8508 9.2 × 10 [−][6] 583.4
18 5 14 1            - 17 4 13 1 262.8516 1.6 × 10 [−][5] 97.0
25 12 13 1           - 24 12 12 0 262.8661 3.4 × 10 [−][4] 230.8
25 12 14 1           - 24 12 13 0 262.8661 3.4 × 10 [−][4] 230.8
10 8 2 1             - 9 7 2 0 262.8770 1.7 × 10 [−][5] 58.8
10 8 3 1             - 9 7 3 0 262.8770 1.7 × 10 [−][5] 58.8
51 5 46 0            - 51 4 47 0 262.8941 3.2 × 10 [−][5] 664.0
25 20 5 1            - 24 20 4 0 262.8963 1.6 × 10 [−][4] 356.3
25 20 6 1            - 24 20 5 0 262.8963 1.6 × 10 [−][4] 356.3
51 6 46 0            - 51 5 47 0 262.9008 3.2 × 10 [−][5] 664.0
26 2 24 1            - 25 2 23 0 262.9441 4.4 × 10 [−][4] 174.2
24 8 17 0            - 24 6 18 1 262.9878 1.3 × 10 [−][6] 179.2
25 21 4 1            - 24 21 3 0 262.9924 1.3 × 10 [−][4] 376.4
25 21 5 1            - 24 21 4 0 262.9924 1.3 × 10 [−][4] 376.4
25 11 15 1           - 24 11 14 0 263.0395 3.6 × 10 [−][4] 219.6
25 11 14 1           - 24 11 13 0 263.0395 3.6 × 10 [−][4] 219.6
50 5 45 1            - 50 5 46 0 263.0857 1.2 × 10 [−][5] 640.1
50 6 45 1            - 50 4 46 0 263.0967 1.2 × 10 [−][5] 640.1
25 22 3 1            - 24 22 2 0 263.1018 1.0 × 10 [−][4] 397.4
25 22 4 1            - 24 22 3 0 263.1018 1.0 × 10 [−][4] 397.4
25 10 16 1           - 24 10 15 0 263.3025 3.7 × 10 [−][4] 209.3
25 10 15 1           - 24 10 14 0 263.3026 3.7 × 10 [−][4] 209.3
49 14 35 1           - 49 13 36 1 263.3298 5.6 × 10 [−][5] 699.7
25 24 1 1            - 24 24 0 0 263.3565 3.5 × 10 [−][5] 442.4
25 24 2 1            - 24 24 1 0 263.3565 3.5 × 10 [−][5] 442.4
49 14 35 0           - 49 13 36 0 263.3831 5.4 × 10 [−][5] 699.5
29 1 29 0            - 28 1 28 1 263.3921 4.5 × 10 [−][4] 196.9
29 0 29 0            - 28 0 28 1 263.3921 4.5 × 10 [−][4] 196.9
27 7 20 0            - 27 4 23 0 263.3926 1.4 × 10 [−][6] 211.0
26 7 19 0            - 25 7 18 1 263.4155 4.1 × 10 [−][4] 197.5
49 14 36 1           - 49 13 37 1 263.4359 5.6 × 10 [−][5] 699.7
26 6 21 0            - 25 6 20 1 263.4496 3.8 × 10 [−][4] 191.4
27 6 21 0            - 27 3 24 0 263.4667 1.7 × 10 [−][6] 205.7
25 5 21 1            - 24 5 20 0 263.4812 4.4 × 10 [−][4] 173.3
49 14 36 0           - 49 13 37 0 263.4838 5.3 × 10 [−][5] 699.4
42 9 34 1            - 41 10 32 0 263.4896 5.6 × 10 [−][6] 487.2
43 14 30 0           - 43 13 30 1 263.5672 9.3 × 10 [−][6] 561.7
43 14 29 0           - 43 13 31 1 263.5721 9.3 × 10 [−][6] 561.7
44 10 35 1           - 43 11 33 0 263.6747 9.7 × 10 [−][6] 539.0
47 11 37 0           - 46 12 35 1 263.6974 6.4 × 10 [−][6] 616.8
25 9 17 1            - 24 9 16 0 263.6982 3.9 × 10 [−][4] 200.1
25 9 16 1            - 24 9 15 0 263.7007 3.9 × 10 [−][4] 200.1
36 5 31 1            - 35 6 29 0 263.7327 1.8 × 10 [−][6] 347.0
gGg’(CH 2 OH) 2 60 8 52 0  - 60 8 53 1 259.9804 2.7 × 10 [−][5] 936.2


Article number, page 41 of 44

**Table E.3.** continued.



_A&A proofs:_ manuscript no. COM_paper


Species Transition Frequency _A_ _i j_ _E_ up
(J K L M          - J K L M) (GHz) (s [−][1] ) (K)
50 14 37 1          - 50 13 38 1 260.0226 1.2 × 10 [−][4] 718.7
50 14 37 0          - 50 13 38 0 260.0388 9.8 × 10 [−][5] 718.6
47 6 42 0           - 46 6 40 0 260.0511 5.8 × 10 [−][6] 566.1
57 4 53 0           - 56 5 51 1 260.0513 1.7 × 10 [−][5] 799.2
57 5 53 0           - 56 6 51 1 260.0516 1.7 × 10 [−][5] 799.2
30 7 24 0           - 30 4 26 1 260.0601 8.1 × 10 [−][6] 252.2
28 0 28 1           - 27 1 27 1 260.1916 1.7 × 10 [−][4] 183.2
28 1 28 1           - 27 0 27 1 260.1917 1.7 × 10 [−][4] 183.2
28 0 28 0           - 27 1 27 0 260.1931 1.7 × 10 [−][4] 183.1
28 1 28 0           - 27 0 27 0 260.1932 1.7 × 10 [−][4] 183.1
48 6 43 0           - 47 7 41 1 260.2289 2.0 × 10 [−][5] 588.9
54 6 48 1           - 54 6 49 0 260.2348 5.6 × 10 [−][6] 747.1
54 7 48 1           - 54 5 49 0 260.2368 8.1 × 10 [−][6] 747.1
53 14 40 0          - 52 15 37 0 260.2665 2.2 × 10 [−][5] 795.2
53 14 40 1          - 52 15 37 1 260.2737 2.5 × 10 [−][5] 795.2
49 5 45 1           - 49 3 46 0 260.2761 5.1 × 10 [−][6] 600.5
49 4 45 1           - 49 4 46 0 260.2762 5.0 × 10 [−][6] 600.5
53 14 39 0          - 52 15 38 0 260.3312 2.5 × 10 [−][5] 795.2
53 14 39 1          - 52 15 38 1 260.3391 2.3 × 10 [−][5] 795.2
18 2 16 1           - 17 2 16 1 260.4196 4.2 × 10 [−][6] 87.3
35 7 28 1           - 34 8 27 1 261.7538 2.8 × 10 [−][5] 335.9
48 5 43 0           - 47 7 41 0 261.7594 3.6 × 10 [−][6] 588.9
15 6 9 0           - 14 5 9 1 261.7612 1.0 × 10 [−][4] 76.2
49 14 35 1          - 49 13 37 0 261.7776 8.8 × 10 [−][5] 694.2
45 3 43 1           - 45 2 44 1 261.7792 2.8 × 10 [−][5] 488.4
45 2 43 1           - 45 1 44 1 261.7792 2.8 × 10 [−][5] 488.4
51 13 39 0          - 50 14 37 1 261.7989 3.4 × 10 [−][5] 731.2
45 3 43 0           - 45 2 44 0 261.8089 2.8 × 10 [−][5] 488.3
45 2 43 0           - 45 1 44 0 261.8089 2.8 × 10 [−][5] 488.3
30 7 24 1           - 30 4 26 0 261.8350 8.3 × 10 [−][6] 252.3
57 8 50 1           - 57 6 51 0 261.9016 1.4 × 10 [−][5] 839.2
26 7 19 1           - 26 4 22 1 261.9779 4.5 × 10 [−][6] 196.1
41 8 34 1           - 40 9 32 0 261.9959 3.7 × 10 [−][5] 454.8
15 6 10 0           - 14 5 10 1 262.0159 1.1 × 10 [−][4] 76.1
43 2 42 1           - 43 1 43 1 262.0203 1.5 × 10 [−][5] 435.8
43 1 42 1           - 43 0 43 1 262.0203 1.5 × 10 [−][5] 435.8
48 6 43 0           - 47 6 41 0 262.0213 4.4 × 10 [−][6] 588.9
51 13 38 0          - 50 14 36 1 262.0401 2.2 × 10 [−][5] 731.2
43 1 42 0           - 43 0 43 0 262.0499 1.5 × 10 [−][5] 435.7
43 2 42 0           - 43 1 43 0 262.0499 1.5 × 10 [−][5] 435.7
26 7 19 0           - 26 4 22 0 262.0555 3.2 × 10 [−][6] 196.0
47 4 44 1           - 47 2 45 0 262.0701 4.1 × 10 [−][6] 543.3
47 3 44 1           - 47 3 45 0 262.0702 4.1 × 10 [−][6] 543.3
12 4 9 0           - 11 1 10 0 262.1539 2.6 × 10 [−][6] 45.9
52 6 47 1           - 52 5 48 1 262.7561 6.2 × 10 [−][5] 684.3
52 5 47 1           - 52 4 48 1 262.7563 6.2 × 10 [−][5] 684.3
48 14 35 1          - 48 13 35 0 262.7790 8.2 × 10 [−][5] 670.1
58 4 54 0           - 57 5 52 1 262.7833 1.7 × 10 [−][5] 826.0
58 5 54 0           - 57 6 52 1 262.7835 1.8 × 10 [−][5] 826.0
52 6 47 0           - 52 5 48 0 262.7850 6.2 × 10 [−][5] 684.3
52 5 47 0           - 52 4 48 0 262.7851 6.2 × 10 [−][5] 684.3
49 5 44 0           - 48 6 42 1 262.7944 2.3 × 10 [−][5] 612.1
56 11 45 1          - 56 10 47 0 262.8056 3.1 × 10 [−][5] 846.1
54 10 44 1          - 53 10 43 0 262.8323 7.1 × 10 [−][6] 769.2
48 14 34 1          - 48 13 36 0 262.8480 8.7 × 10 [−][5] 670.1
15 6 10 1           - 14 5 9 1 262.9243 8.5 × 10 [−][5] 76.2



Article number, page 42 of 44

**Table E.3.** continued.



M. L. van Gelder et al.: Complex organic molecules in low-mass protostars on solar system scales


Species Transition Frequency _A_ _i j_ _E_ up
(J K L M           - J K L M) (GHz) (s [−][1] ) (K)
48 6 43 1            - 47 7 41 0 262.9262 2.2 × 10 [−][5] 588.9
15 6 10 0            - 14 5 9 0 262.9573 7.7 × 10 [−][5] 76.1
51 13 39 1           - 50 14 37 0 262.9728 2.3 × 10 [−][5] 731.3
25 4 21 1            - 24 4 20 0 263.0163 1.6 × 10 [−][4] 170.5
45 3 43 1            - 45 1 44 0 263.0586 2.9 × 10 [−][6] 488.4
45 2 43 1            - 45 2 44 0 263.0586 2.9 × 10 [−][6] 488.4
26 3 23 1            - 25 3 22 0 263.0676 9.8 × 10 [−][5] 178.9
25 5 20 0            - 24 5 19 1 263.0725 1.6 × 10 [−][4] 173.6
25 7 19 0            - 25 4 21 1 263.0877 3.3 × 10 [−][6] 183.1
17 5 13 0            - 16 4 13 1 263.1057 9.6 × 10 [−][5] 87.1
30 6 25 0            - 30 3 27 1 263.1423 3.9 × 10 [−][6] 246.1
48 5 43 1            - 47 6 41 0 263.1708 2.1 × 10 [−][5] 588.9
32 5 27 0            - 32 4 29 1 263.1942 6.3 × 10 [−][6] 276.0
43 2 42 1            - 43 0 43 0 263.3325 1.6 × 10 [−][6] 435.8
44 10 34 0           - 43 11 32 1 263.4029 3.7 × 10 [−][5] 535.1
46 14 33 0           - 46 13 33 1 263.5562 8.7 × 10 [−][5] 623.6
26 18 8 0            - 25 18 7 1 263.5570 8.8 × 10 [−][5] 328.6
26 18 9 0            - 25 18 8 1 263.5570 8.8 × 10 [−][5] 328.6
26 17 10 0           - 25 17 9 1 263.5577 9.7 × 10 [−][5] 311.6
26 17 9 0            - 25 17 8 1 263.5577 9.7 × 10 [−][5] 311.6
26 19 7 0            - 25 19 6 1 263.5670 7.8 × 10 [−][5] 346.5
26 19 8 0            - 25 19 7 1 263.5670 7.8 × 10 [−][5] 346.5
26 16 10 0           - 25 16 9 1 263.5730 1.1 × 10 [−][4] 295.6
26 16 11 0           - 25 16 10 1 263.5730 1.1 × 10 [−][4] 295.6
46 14 32 0           - 46 13 34 1 263.5813 8.6 × 10 [−][5] 623.6
26 20 6 0            - 25 20 5 1 263.5846 6.9 × 10 [−][5] 365.4
26 20 7 0            - 25 20 6 1 263.5846 6.9 × 10 [−][5] 365.4
9 9 0 1              - 8 8 1 1 263.5918 1.9 × 10 [−][4] 61.4
9 9 1 1              - 8 8 0 1 263.5918 1.9 × 10 [−][4] 61.4
26 21 5 0            - 25 21 4 1 263.6069 5.8 × 10 [−][5] 385.3
26 21 6 0            - 25 21 5 1 263.6069 5.8 × 10 [−][5] 385.3
26 15 11 0           - 25 15 10 1 263.6074 1.1 × 10 [−][4] 280.6
26 15 12 0           - 25 15 11 1 263.6074 1.1 × 10 [−][4] 280.6
13 7 7 1             - 12 6 6 1 263.6167 1.1 × 10 [−][4] 68.3
13 7 6 1             - 12 6 7 1 263.6186 1.1 × 10 [−][4] 68.3
9 9 0 0              - 8 8 1 0 263.6196 1.9 × 10 [−][4] 61.3
9 9 1 0              - 8 8 0 0 263.6196 1.9 × 10 [−][4] 61.3
26 22 4 0            - 25 22 3 1 263.6311 4.8 × 10 [−][5] 406.1
26 22 5 0            - 25 22 4 1 263.6311 4.8 × 10 [−][5] 406.1
13 7 7 0             - 12 6 6 0 263.6457 1.1 × 10 [−][4] 68.2
13 7 6 0             - 12 6 7 0 263.6476 1.1 × 10 [−][4] 68.2
27 2 25 1            - 26 3 24 1 263.6485 8.9 × 10 [−][5] 185.6
26 23 3 0            - 25 23 2 1 263.6545 3.6 × 10 [−][5] 427.8
26 23 4 0            - 25 23 3 1 263.6545 3.6 × 10 [−][5] 427.8
27 2 25 0            - 26 3 24 0 263.6585 1.6 × 10 [−][4] 185.5
11 8 4 1             - 10 7 3 1 263.6667 1.4 × 10 [−][4] 63.4
11 8 3 1             - 10 7 4 1 263.6667 1.4 × 10 [−][4] 63.4
26 14 12 0           - 25 14 11 1 263.6670 1.2 × 10 [−][4] 266.5
26 14 13 0           - 25 14 12 1 263.6670 1.2 × 10 [−][4] 266.5
26 24 2 0            - 25 24 1 1 263.6744 2.5 × 10 [−][5] 450.6
26 24 3 0            - 25 24 2 1 263.6744 2.5 × 10 [−][5] 450.6
26 25 1 0            - 25 25 0 1 263.6877 1.3 × 10 [−][5] 474.3
26 25 2 0            - 25 25 1 1 263.6877 1.3 × 10 [−][5] 474.3
11 8 4 0             - 10 7 3 0 263.6951 1.4 × 10 [−][4] 63.3
11 8 3 0             - 10 7 4 0 263.6951 1.4 × 10 [−][4] 63.3
26 13 13 0           - 25 13 12 1 263.7599 1.3 × 10 [−][4] 253.4


Article number, page 43 of 44

**Table E.3.** continued.



_A&A proofs:_ manuscript no. COM_paper


Species Transition Frequency _A_ _i j_ _E_ up
(J K L M          - J K L M) (GHz) (s [−][1] ) (K)
26 13 14 0          - 25 13 13 1 263.7599 1.3 × 10 [−][4] 253.4
43 9 35 1           - 42 10 32 1 263.7620 2.4 × 10 [−][5] 504.6
CH 2 OHCHO 27 11 16 - 27 10 17 260.1657 2.8 × 10 [−][4] 283.9
27 11 17          - 27 10 18 260.1817 2.8 × 10 [−][4] 283.9
45 9 37           - 45 8 38 261.7386 3.0 × 10 [−][4] 632.0
25 11 14          - 25 10 15 261.7955 2.7 × 10 [−][4] 254.2
25 11 15          - 25 10 16 261.7990 2.7 × 10 [−][4] 254.2
41 12 29          - 41 11 30 261.8305 3.3 × 10 [−][4] 569.0
25 1 24           - 24 2 23 262.0482 4.6 × 10 [−][4] 170.8
25 2 24           - 24 2 23 262.0513 6.9 × 10 [−][6] 170.8
25 1 24           - 24 1 23 262.0537 6.9 × 10 [−][6] 170.8
25 2 24           - 24 1 23 262.0568 4.6 × 10 [−][4] 170.8
43 7 36           - 43 6 37 262.7212 2.7 × 10 [−][4] 570.1
26 0 26           - 25 1 25 262.7943 5.3 × 10 [−][4] 173.0
26 1 26           - 25 1 25 262.7943 7.1 × 10 [−][6] 173.0
26 0 26           - 25 0 25 262.7943 7.1 × 10 [−][6] 173.0
26 1 26           - 25 0 25 262.7943 5.3 × 10 [−][4] 173.0
43 10 34          - 42 11 31 262.7994 6.2 × 10 [−][5] 593.1
51 14 37          - 50 15 36 262.9430 6.9 × 10 [−][5] 861.3
23 11 12          - 23 10 13 263.0488 2.6 × 10 [−][4] 226.9
23 11 13          - 23 10 14 263.0495 2.6 × 10 [−][4] 226.9
38 5 33           - 38 4 34 263.3786 2.2 × 10 [−][4] 433.8
30 1 29           - 30 0 30 263.4168 5.6 × 10 [−][5] 240.8
30 2 29           - 30 1 30 263.4168 5.6 × 10 [−][5] 240.8
22 11 11          - 22 10 12 263.5580 2.5 × 10 [−][4] 214.1
22 11 12          - 22 10 13 263.5582 2.5 × 10 [−][4] 214.1
46 8 38           - 46 7 39 263.5591 3.0 × 10 [−][4] 657.2
22 6 16           - 21 6 15 263.7526 6.6 × 10 [−][6] 164.3
38 6 33           - 38 5 34 263.7558 2.2 × 10 [−][4] 433.8
H 2 CCO 13 1 13 - 12 1 12 260.1920 2.0 × 10 [−][4] 100.5
13 8 5            - 12 8 4 261.8202 1.3 × 10 [−][4] 918.9
13 8 6            - 12 8 5 261.8202 1.3 × 10 [−][4] 918.9
13 7 6            - 12 7 5 262.0435 1.5 × 10 [−][4] 725.0
13 7 7            - 12 7 6 262.0435 1.5 × 10 [−][4] 725.0
13 2 11           - 12 2 10 262.7609 2.0 × 10 [−][4] 140.5
t-HCOOH 12 0 12 - 11 0 11 262.1036 1.9 × 10 [−][4] 82.8
20 3 17           - 20 2 18 263.0581 5.1 × 10 [−][6] 257.2
3 2 2             - 2 1 1 263.7624 3.4 × 10 [−][6] 19.2



Article number, page 44 of 44


</paper>

## Items to check

```json
[
 {
  "path": "data.external_data_from_literature[1].what.evidence[0]",
  "value": "Local ISM isotope ratios 12C/13C~70, 16O/18O~560",
  "failed_quote": "using 12 C/ 13 C ∼ 70 and 16 O/ 18 O ∼ 560 for the local ISM; Milam et al. 2005; Wilson & Rood 1994"
 },
 {
  "path": "software[1].used_for.evidence[0]",
  "value": "LTE modelling of column densities and Tex",
  "failed_quote": "The spectral analysis tool CASSIS was used to determine column densities and excitation temperatures of detected species."
 }
]
```
